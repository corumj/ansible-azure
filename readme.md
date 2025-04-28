# Azure Demo and Testing 

## Demos
1) Create an virtual machine and all the supporting cloud resources like a VPC, Subnet, public IP, and security group 
    - ansible-test-rhel-vm.yml
    - ansible-test-windows-vm.yml
2) Create and prepare Azure Flexible Postgresql server for use with AAP (could be customized for other db needs)
    - create_database.yml 
3) Prepare a VM and create an Azure Image gallery image 
    - ansible-test-rhel-vm.yml or ansible-test-windows-vm.yml to create an instance we can turn into an image
    - update_all_packages.yml or windows-update-all.yml
    - azure-generalizeVMCreateImage.yml - needs to be customized for windows or rhel
    - image_to_instance.yml (hard coded to create instance from image)
4) Control vm power state, for scheduling downtime 
    - vm-power-state.yml 
5) Stand up an AKS cluster and work with it 
    - aks.yml
    - aks_k8s_info.yml 
6) Terraform with Ansible - with AAP provider and without
    - tf.main.check.yml - spins up 2 instances, one with and one without the tf AAP provider to push new resources into AAP's inventory









## Backup Testing 
1. Run either `ansible-test-rhel-vm.yml` to create a RHEL system we can backup 
2. Run `backup-create-policy.yml` to create a backup vault and backup policy
3. Run `backup-on-demand.yml` to backup ansible-test-rhel-vm, this will take over 30 minutes
4. Create a file or two on the server, something for the system to backup  
5. Attempt to run `restore_point_recovery.yml` currently untested to restore to a new VM.  
