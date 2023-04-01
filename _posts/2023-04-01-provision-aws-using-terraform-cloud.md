---
title: Provision AWS using Terraform Cloud
date: 2023-04-01 11:00
categories: [Terraform, AWS]
tags: [terraform, aws]
render_with_liquid: false
---

This article gives you hands-on lab for creating AWS resources using Terraform cli & Terraform cloud.
  - Idea is to cover most of the commonly used Terraform blocks like module, resource, variable, output, locals, data
  - Terraform source code can be found at: <https://github.com/abhishek-pradhan/tfc-aws-demo>


## Pre-Requisites
1. AWS account with an IAM user having Console & Programmatic access. (You will need to create an AWS IAM user account with admin rights, an access key, and a secret key.)
2. Good to have: AWS CLI configured with #1's AWS access key id & secret access key
3. Terraform CLI setup'ed. Refer this [article](https://blog.abhishekpradhan.com/posts/getting-started-with-terraform-cli-terraform-cloud/) to setup Terraform CLI on either Windows 10/11 or Ubuntu or AWS Cloud9 IDE.
4. Terraform Cloud account (free)
5. Visual Studio Code as IDE to create / modify Terraform configs and Terraform extension from Hashicorp for syntax highlighting & intelli-sense.

> Assumption: You know basics about Terraform & AWS. 
{: .prompt-info }

## Let's provision AWS resources
- Login to Terraform Cloud <https://app.terraform.io/> and create an organization, let's say *tfc-aws-demo-org*

- Goto Organization Settings -> Variable sets -> Create variable set -> setup Variables set with 2 env variables: *AWS_ACCESS_KEY_ID* & *AWS_SECRET_ACCESS_KEY*. Values of these env variables is from Pre-Requisites #1 (see below screenshot for all the settings)

  > Notes from Terraform doc: 
    - Terraform uses [variables](https://developer.hashicorp.com/terraform/language/values/variables) for all plans and applies within a workspace. [Variable sets](https://developer.hashicorp.com/terraform/cloud-docs/workspaces/variables#scope) are a group of commonly used variables that you can apply to multiple workspaces in an organization.
    - We recommend creating a variable set for variables used in more than one workspace.
    - Note: I am using Variable set, since I will be using same AWS account across workspaces, with different AWS regions.
  {: .prompt-info }

  ![terraform cloud variable sets](/assets/img/posts/2023-04-01-provision-aws-using-terraform-cloud/terraform-cloud-variable-sets.png)
  *Screenshot: Terraform Cloud Variable sets*

- Now, we can start using this org to create multiple workspaces, as per our use-case. For instance, we can have dev, uat & prod workspaces.
  - Goto Terraform Cloud (TFC) -> Select our org -> Create a new Workspace -> CLI-driven workspace -> Workspace name = ws-dev -> Click 'Create workspace' button
- Clone my terraform configuration repo from github:
    ```terminal
    git clone git@github.com:abhishek-pradhan/tfc-aws-demo.git
    ```

  - Open up Visual studio code:
    ```terminal
  	$ cd tfc-aws-demo/ && code .
    ```

  - All you need to do is to change organization name in providers.tf to point to organization that you created above.
  - Also, check terraform.tfvars file to change aws region and aws resources, to avoid conflict
  
  > Note: In order to demo data block type, please ensure that aws s3 bucket named in data block type is present in your account or create one (manually or with aws cli) & update its name in ab_cdn_bucket OR comment out / remove data block from main.tf and its usage from outputs.tf file
  {: .prompt-info }

  - Create s3 bucket:
      ```terminal
      aws s3api create-bucket --bucket tfc-aws-demo-891223 --create-bucket-configuration LocationConstraint=ap-south-1
      ```

  - Tag s3 bucket: 
    ```terminal
    aws s3api put-bucket-tagging --bucket tfc-aws-demo-891223 --tagging "TagSet=[{Key=Terraform, Value=true}, {Key=Environment, Value=dev}]"
    ```

  - Delete s3 bucket (post you are done with this lab):
    ```terminal
    aws s3api delete-bucket --bucket tfc-aws-demo-891223
    ```

- Now we need terraform api token so that we can connect terraform cli to our terraform cloud account and start using tfc as our remote backend:
  ```terminal
  $ terraform login
  ```
    - this command takes you to browser & generates token when you click on 'Create API token' popup. Remember to copy & save token to terminal & your scratch pad
    - Now paste token in the terminal and we should be successfully connected to TFC! (see below screenshot)
      ![terraform login success](/assets/img/posts/2023-04-01-provision-aws-using-terraform-cloud/terraform-login-success.png)
      *Screenshot: Terraform login success*

- From here on, we will be using typical terraform cli (tf workflow) commands:
	```terminal
  terraform init
	```
  - Optional tf commands:
    ```terminal
    terraform validate
    terraform fmt
    ```

  ```terminal
  terraform plan
  ```

  ```terminal
  terraform apply -auto-approve
  ```
  - On successful run, we will see AWS resources in our AWS account via Console. Goto AWS Console -> Select our region (Mumbai) -> Search 'Resource Groups & Tag Editor' -> 'rg-tfc-aws-demo' Resource group -> Here you can check all the resources created by us (s3 bucket & kms key)
    ```terminal
    terraform output
    terraform output my-kms
    terraform output my-kms | grep key_id
    terraform show
    terraform state list
    terraform state show aws_resourcegroups_group.test
    ```

  - Workspace related commands (optional commands, since we used just 1 workspace, but good to know):
    ```terminal
    terraform workspace show
    terraform workspace new uat
    terraform workspace list
    
    # select a specific workspace, in case of multiple workspaces
    terraform workspace select uat
    ```

  - We are done with the lab, clean-up resources, so that we are not charged for un-used AWS resources
    ```terminal
    terraform destroy  -auto-approve
    ```

      - Delete s3 bucket (in-case you created it manually as mentioned above): 
      ```terminal
      aws s3api delete-bucket --bucket tfc-aws-demo-891223
      ```

> Note: since we are using TFC as remote backend, all our runs would be in TFC. Terraform cli will give you link to the runs in the terminal (screenshot below)
{: .prompt-info }

  ![terraform run success](/assets/img/posts/2023-04-01-provision-aws-using-terraform-cloud/terraform-run-success.png)
  *Screenshot: Terraform run success*

> Tip: Here I am using manual way to run Terraform cli commands to create AWS resources, however we can also setup CI/CD pipeline to automate this. Since we are using TFC, I don/t have to setup & create CI/CD pipeline using Jenkins. TFC provides us to do this out of the box!
{: .prompt-tip }
