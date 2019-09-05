# Dynamic Inventory with Ansible - example for OCI Cloud

This scenario/tutorial builds on top of virtualenv'd OCI Ansible tutorial *Getting started with Ansible for OCI cloud*

Dynamic Inventory is an Ansible technique, which usually requires a third party inventory script's presence on the system.

For Oracle's OCI Cloud we can get one for example:

    (ansible-oci-env) ansible-oci-env/bin$ deactivate
    ansible-oci-env/bin$ cd ..
    ansible-oci-env$ mkdir oci-ansible-modules-src
    ansible-oci-env$ cd oci-ansible-modules-src/
    ansible-oci-env/oci-ansible-modules-src$ git clone https://github.com/oracle/oci-ansible-modules.git .
    Cloning into '.'...
    ...
    Checking connectivity... done.

Note related to the newly cloned source tree:

- Dynamic inventory scripts are located in oci-ansible-modules directory. Script creates inventory from compartment or tenancy.
- inventory-script/oci_inventory.ini
  - Ansible OCI external inventory script settings.
- inventory-script/oci_inventory.py
  - Creates the inventory cache file
- Test the inventory by run this command --> ```$ inventory-script/oci_inventory.py --list```
- Tip later use: Specify tags when launching instances. Instances will be named by tags in inventory (fortunately those tags can be added later, too).

### General command format for using Dynamic Inventory against OCI

- ```ansible-playbook -i /home/kayttaja/oci-ansible-modules/inventory-script/oci_inventory.py -b -u opc [playbook_name].yml```

 - "-i" = inventory
 - "-b" = become
 - "-u" = user

## Try running oci_inventory.py as a standalone script

    ansible-oci-env$ source bin/activate

    (ansible-oci-env) ansible-oci-env$ oci-ansible-modules-src/inventory-script/oci_inventory.py --list


## Try running oci_inventory as a part of Ansible playbook run

Let's assume we have written a playbook file like:

    ansible-oci-env$ cat connection_test.yml

    ---
    - name: Connection test
    hosts: a

    tasks:
    - name: Connection test
      debug:
        msg: "Toimii!"


We should probably enable SSH agent for key based authentication at this point, for example issuing something like this:

    (ansible-oci-env) ansible-oci-env$ eval $(ssh-agent)
    (ansible-oci-env) ansible-oci-env$ ssh-add <path-to-your-own-SSH-private-key>

    (ansible-oci-env) adep/ansible-oci-env$ ansible-playbook -i oci-ansible-modules-src/inventory-script/oci_inventory.py -b -u opc connection_test.yml
    ...
    PLAY [Connection test] *********************************************************
    TASK [Gathering Facts] *********************************************************
    ok: ...  => {
    "msg": "Toimii!"
    }
    ...

Success!?!


## Useful links
- [List of Oracle Cloud modules](https://oracle-cloud-infrastructure-ansible-modules.readthedocs.io/en/latest/modules/list_of_cloud_modules.html)
- [Oracle Cloud Infrastructure Guide](https://docs.ansible.com/ansible/latest/scenario_guides/guide_oracle.html)
