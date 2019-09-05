# Getting started with Ansible for OCI cloud

### One possible scenario to get started with Ansible and OCI modules.

#### Background
Ansible is implemented on top of Python.

Python ecosystem is unfortunately a bit notorious when it comes to managing programming libraries, program packages and their versions, etc. There are a good bunch of different package managers, installers and other tools meant to ease up these kind of pains but so far there is probably not an ultimate solution yet.

Instead, it is quite common/easy to mess up with e.g. your own machince's Python environment with some set of additional Python tooling installations.

#### Virtualenv to the rescue
In order to provide some isolation against a library dependency hell situation, this document builds upon a tooling called "virtualenv".

Virtualenv is probably not the only way to isolate your python stuff, but at least for Oracle OCI Ansible modules etc it seems to provide quite good protection with respect to the other python stuff there may already exist on your computer.

## Prerequisites
This "tutorial" builds on the following assumptions:

#### 1. Python installed
Your machine should come with Python installation. Moreover, we assume you have *Python 3* installed.

E.g. on a Linux you should be able to check this for example:

    $ which python3
    /usr/bin/python3

    $ python3 --version
    Python 3.5.2

The exact Python version number does not need to match the example but the major "3" is assumed further.

#### 2. You can install additional software "easily"
You should have a way to somewhat easily install additional software for you machine. No matter whether that is ```yum``` or ```apt-get``` or similar general software package manager for a Linux system. Or ```brew``` for a Mac system.

It is possible to install everything out of sources, probably, but later on in this tutorial we use a apt-get as an example. This is just for convenience, so feel free to adapt to your own system.

## Install Virtualenv

If you can find "virtualenv" package from your system's package management, that may be good enough.

For example like this (Note, this is from a Ubuntu Linux, and Warning, yes you *may* mess up your existing python installation):

    $ apt-cache search virtualenv
    ...
    virtualenv - Python virtual environment creator
    ...

    $ sudo apt-get install virtualenv

    $ which virtualenv
    /usr/bin/virtualenv

## Create isolated virtualenv

    $ virtualenv ansible-oci-env --no-site-packages --python=$(which python3)
    Already using interpreter /usr/bin/python3
    Using base prefix '/usr'
    New python executable in ansible-oci-env/bin/python3
    Also creating executable in ansible-oci-env/bin/python
    Installing setuptools, pkg_resources, pip, wheel...done.  

In that command:
  - "ansible-oci-env" was just a name for the new environment, feel free to come up your own better name
  - "--no-site-packages" should provide additional isolation to NOT link to the other python libraries and packages that may exist (note, this option may be default/unnecessary on newer virtualenv's)
  - "--python" option directs to use Python 3 in case older ones exist on you system.


    $ cd ansible-oci-env

    ansible-oci-env$ ls
    bin  include  lib  pip-selfcheck.json  share

## "activate" the new virtual python environment

    ansible-oci-env$ cd bin

    ansible-oci-env/bin$ source activate
    (ansible-oci-env) bin$

Sometimes later you can run command *deactivate* within the *bin* directory. The "(environment-name)" should then disappear. Note, deactivate does not need the "source" in front of it.

## Install PythonSDK into the virtual environment

    (ansible-oci-env) ansible-oci-env/bin$ pip install oci

    ...
    Downloading https://files.pythonhosted.org/packages/83/97/33c11a4314f4e7d35040fe44e24f3e9ee571cbe5f0091faac9197c1bb980/oci-2.3.3-py2.py3-none-any.whl (2.5MB)
    |████████████████████████████████| 2.5MB 1.5MB/s
    Collecting pytz>=2016.10 (from oci)
    Using cached ...
    ...

## Verify openSSl version -> should be at least 1.0.1

    (ansible-oci-env) ansible-oci-env/bin$ python -c "import ssl; print(ssl.OPENSSL_VERSION)"
    OpenSSL 1.0.2g  1 Mar 2016

## Install Ansible

    (ansible-oci-env) ansible-oci-env/bin$ pip install ansible
    ...
    Installing collected packages: MarkupSafe, jinja2, PyYAML, ansible
    Successfully installed MarkupSafe-1.1.1 PyYAML-5.1.2 ansible-2.8.4 jinja2-2.10.1

#### Sidestep: generate SSH keypair (if nececessary)

If you have not generated a SSH keypair yet, refer to:
  - [Ansible Documentation - Getting Started](https://docs.ansible.com/ansible/latest/user_guide/intro_getting_started.html)

## Create ~/.oci/config file to authenticate

OCI Ansible modules build on top of Oracle OCI Tools. For authentication to work against OCI Cloud we need to hand-craft a special config file.

(Note, FIXME, we may have a dedicated practice for setting up on such file?)

The file's exact contents is pretty long explanation, but for starters please refer to:

- [Oci Config file Documentation](https://docs.cloud.oracle.com/iaas/Content/API/Concepts/sdkconfig.htm)
