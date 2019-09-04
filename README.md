# IaC and DevOps Workshop
Oracle Cloud DevOps workshop content and links

<b>0. Register for Oracle Cloud Trial special promotion (500 $ / 30 days)</b>
  - https://myservices.us.oraclecloud.com/mycloud/signup?language=en&sourceType=_ref_coc-asset-opcHome
  - By entering email address system will recognise whitelisted users and guide you through the rest of the process. You should not be required to enter credit card information, or be required for SMS validation. Please let me know immediately if this is the case and we'll sort it out.

<b>1. Setup pre-requisites</b>
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
  - Run YUM update for tooling
  - Configure authentication https://docs.cloud.oracle.com/iaas/Content/API/Concepts/apisigningkey.htm
  - Setup OCI CLI https://docs.cloud.oracle.com/iaas/Content/API/SDKDocs/cliinstall.htm
  
<b>4. Terraform</b>
  - Terraform configuration language, structure and syntax: https://www.terraform.io/docs/configuration/index.html
  - Introduction to Terraform on OCI: https://docs.cloud.oracle.com/iaas/Content/API/SDKDocs/terraformgetstarted.htm
  - Terraform Provider for OCI: https://docs.cloud.oracle.com/iaas/Content/API/SDKDocs/terraformgetstarted.htm
  - Documentation: https://www.terraform.io/docs/providers/oci/index.html
  - Terraform examples for Oracle: https://github.com/oracle/terraform-examples
  - Recap excercise for creating a compute instance with Resource Manager: https://docs.cloud.oracle.com/iaas/Content/ResourceManager/Concepts/samplecomputeinstance.htm
  
<b>5. Ansible</b>
  - 
