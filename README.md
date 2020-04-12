# Bootstrap JupyterHub on AWS

This repo lays the foundation for a jupyterhub instance on AWS.

It uses terraform for the initial setup of an ec2 instance and `jupyterhub-deploy-teaching` ansible playbooks to
configure a jupyterhub instance that can be used for hosting a number of users.

The desire for hosting a jupyterhub instance was created after wanting to collaborate with friends on the
[Neureka-Challenge](https://neureka-challenge.com/), setup by: [Novela Neurotech](https://www.novelaneuro.com/) and [NeuroTechX](https://neurotechx.com/).

I have downloaded the data from [Temple University Hospital](https://www.isip.piconepress.com/projects/tuh_eeg/) into an EBS volume that is mounted to this jupyterhub instance on [notebooks.dendritictech.com](https://notebooks.dendritictech.com).

This will allow for users to be able to start playing with the data and building out initial processing pipelines. The
current resources for this instance are not enough to do advanced modelling, which requires GPU-resources.

## Installation

**Requires**

- [terraform](https://www.terraform.io/downloads.html)
- SSH key + client
- AWS profile with the following policies: AmazonEC2FullAccess, AmazonVPCFullAccess, AmazonRoute53FullAccess
- Domain Name already in [Route53](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/domain-register.html)

### Terraform

The usual Terraform commands should get you a running EC2 Instance

`terraform init`

`terraform plan`

`terraform apply`


Then go into the `jupyterhub-deploy-teaching` directory update the `deploy.yml` and `host_vars` files and run the ansible-playbook:

`ansible-playbook -i hosts deploy.yml`

