# IaC and DevOps Workshop
Oracle Cloud DevOps workshop content and links

<b>0. Register for Oracle Cloud Trial special promotion (500 $ / 30 days)</b>
  - https://myservices.us.oraclecloud.com/mycloud/signup?language=en&sourceType=_ref_coc-asset-opcHome
  - By entering email address system will recognise whitelisted users and guide you through the rest of the process. You should not be required to enter credit card information, or be required for SMS validation. Please let me know immediately if this is the case and we'll sort it out.
  - Once you have logged in, create a service user to be used in the excercises and assign it to the administrators group
  - Self-paced examples and excercises:https://github.com/oracle/learning-library/tree/master/oci-library

<b>1. Pre-requisites for connectivity and version control</b>
  - We will be using key based authentication. Follow the setup instructions at: https://docs.cloud.oracle.com/iaas/Content/GSG/Tasks/creatingkeys.htm
  - Each participant needs a Github account for which they can register freely at https://github.com/
  - Git workflow: https://www.atlassian.com/git/tutorials/comparing-workflows
  - Exercise on Git basics: https://guides.github.com/activities/hello-world/
  - Exercise on working with local and remote repositories: https://help.github.com/en/articles/adding-an-existing-project-to-github-using-the-command-line
  - Git branching and merging: https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging

<b>2. Deploy Oracle Linux Developer Image</b>
  - We will use cloud compute instance as a jump-box/bastion host so we are not required to setup tooling on participant laptops
  - https://blogs.oracle.com/linux/announcing-the-oracle-cloud-developer-image-for-oracle-cloud-infrastructure
  - Tutorial to create the same using Terraform with OCI Resource Manager: https://docs.cloud.oracle.com/iaas/Content/ResourceManager/Concepts/samplecomputeinstance.htm

<b>3. Setup and update OCI CLI and tools</b>
  - Run YUM update for tooling https://access.redhat.com/documentation/en-us/red_hat_network_satellite/5.5/html/reference_guide/sect-reference_guide-package_updater-updating_packages_from_the_command_line_with_yum
  - Configure authentication https://docs.cloud.oracle.com/iaas/Content/API/Concepts/apisigningkey.htm
  - Setup OCI CLI https://docs.cloud.oracle.com/iaas/Content/API/SDKDocs/cliinstall.htm
  - Excercise: test CLI setup https://oracle.github.io/learning-library/oci-library/DevOps/OCI_CLI/OCI_CLI_HOL.html#overview
  
<b>4. Terraform</b>
  - Terraform configuration language, structure and syntax: https://www.terraform.io/docs/configuration/index.html
  - Introduction to Terraform on OCI: https://docs.cloud.oracle.com/iaas/Content/API/SDKDocs/terraformgetstarted.htm
  - Terraform Provider for OCI: https://docs.cloud.oracle.com/iaas/Content/API/SDKDocs/terraformgetstarted.htm
  - Documentation: https://www.terraform.io/docs/providers/oci/index.html
  - Terraform examples for Oracle: https://github.com/oracle/terraform-examples
  - Recap excercise for creating a compute instance with Resource Manager: https://docs.cloud.oracle.com/iaas/Content/ResourceManager/Concepts/samplecomputeinstance.htm
  
<b>5. Ansible</b>
  - Ansible architecture: https://docs.ansible.com/ansible/latest/dev_guide/overview_architecture.html
  - Ansible on OCI: https://oracle-cloud-infrastructure-ansible-modules.readthedocs.io/en/latest/index.html
  - OCI Ansible modules and samples repository: https://github.com/oracle/oci-ansible-modules
  - Getting started with Ansible on Oracle Cloud: https://docs.cloud.oracle.com/iaas/Content/API/SDKDocs/ansiblegetstarted.htm
  - Running ad hoc commands exercise: https://docs.ansible.com/ansible/latest/user_guide/intro_getting_started.html
  - Ansible Dynamic Inventories on OCI: https://docs.cloud.oracle.com/iaas/Content/API/SDKDocs/ansibleinventoryscript.htm
  - Ansible Playbooks sample excercises: https://docs.cloud.oracle.com/iaas/Content/API/SDKDocs/ansiblesamples.htm
  
<b>6. CI/CD</b>
  - GitLab by example
  - Wercker by example
  - GitOps, Containers and Cloud Native CI/CD with Jenkins-X excercise: https://github.com/ev-orcl/cloudnativeci/blob/master/README.md
  
