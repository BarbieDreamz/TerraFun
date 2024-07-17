This user data script is a work in progress and currently lacks error handling and idempotency. It was originally created and written to resolve an issue with a corrupt file system on EC2 where snapshots did not exist. This was manually ran via EC2 Serial Console where it failed and then injected as user data on boot.

Its primary goal is to create a new filesystem on /dev/xvda, mount it as /home, and add it to the fstab. It was revised and tested in Terraform.

Variables will be introduced to make the script more flexible and adaptable. Future improvements will include error handling and idempotency checks such as checking if /home exists. 

Removal of sleep since this isn't a good practice outside of live troubleshooting (they truly only exist because you need to allow time for the instance to launch and each command to complete)

I also might change this entirely and just use cloud-init. 
