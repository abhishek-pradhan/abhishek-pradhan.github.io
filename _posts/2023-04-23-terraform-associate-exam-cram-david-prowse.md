---
title: Terraform Associate Exam Cram - David Prowse
date: 2023-04-23 13:30
categories: [Terraform]
tags: [terraform]
render_with_liquid: false
---

I recently attended [O'Reilly Live event by David Prowse on Terraform Associate Exam Cram](https://learning.oreilly.com/live-events/hashicorp-terraform-associate-exam-cram/0636920082746/0636920082745/) course and found it helpful to clear my Terraform certification - [HashiCorp Certified: Terraform Associate (002)](https://www.hashicorp.com/certification/terraform-associate-002). It was a live event spanning 2 days, with 4 hours daily & David covered lot of hands-on labs / practicals along with Exam tips. He also shared practice exam with 75 questions.

> You can find all the links / contacts / schedule and contents of the the class in the [References](#references) section at the end of this article.
{: .prompt-tip }

This article captures key points from the course into below 2 sections: [Exam Tips](#exam-tips) & [Hands-on Lab notes](#hands-on-lab-notes). 

> Please note that this article is not a replacement for the course, but more of accompanying notes. I would strongly recommend to attend David's course.
{: .prompt-info }

## Exam Tips

1. Terraform recommends using tab size of 2 space ident, set this in your favorite IDE like VS Code

2. Best practice for declarative tf script: have a blank line in between blocks/components

3. HashiCorp based provider plugins & community based provider plugins are automatically downloaded when we run $ terraform init

4. Terraform block naming convention:
    resource "aws_instance" "my_app_server" {
        ami = "ami-0x84f8d952e241ef73" 
        ...
    }
    - Block type Block label Block label name (also known as Terraform ID)
    - { arguments } 
        - Identifier = expression
    
    OR below is from Terraform site:
        resource "TYPE" "NAME" {
            [CONFIGURATION_KEY = CONFIGURATION_VALUE]
            ...
        }

5. Terraform is cross platform and can be installed on linux, Windows, macos

6. Refer Terraform help: 
    $ terraform -help
    $ terraform -h init

7. $ terraform apply cmd will make changes to infra in cloud / on premises, and to the state file

8. TF supports HCL & json, but not plaintext or js or xml files.

9. terraform.tfvars houses values only, whereas variables.tf can have variable declarations & values

10. The only files Terraform "auto-loads" are terraform.tfvars and *.auto.tfvars
    - Terraform auto loads .tfvars files, only when they are named terraform.tfvars or terraform.tfvars.json or *.auto.tfvars

11. Terraform Variables precedence: (first being highest):
    1. $ terraform apply -var="image_id=ami-abc123" or -var-file="dev.tfvars" (This includes variables set by a Terraform Cloud workspace)
    2. *.auto.tfvars
    3. terraform.tfvars
    4. environment variables (TF_VARS_image_id)
    Note: -var-file option is not supported in TFC! Instead use Environment / Terraform variables in TFC workspace.

12. Environment variables can be used to set the value of input variables. The environment variables must be in the format "TF_VAR"_<variablename>.
    variable "instructor_name" {
        type = string
    }
    $ export TF_VAR_instructor_name="bryan"
    $ terraform apply

13. Following are not allowed while Terraform state file is locked: apply, destroy or plan
    - The whole point of lock is so that other users cannot provision the same architecture at the same time!

14. Meta-arguments:
    1. count
    2. depends _on
    3. for_each
    4. Lifecycle
    5. Provider


## Hands-on Lab notes

- $ terraform fmt
    - Formats .tf /.tfvars files as per TF standards (like 2 ident spaces) and outputs files its formatted
        - For example: main.tf

- $ terraform fmt -recursive
    - Formats tf files within sub-dirs too

- $ terraform init
    - Initializating the backend... 
    - Initializing modules... (downloaded to .terraform/modules dir)
    - Initializating provider plugins (downloaded to .terraform/providers dir)
        - Default working directory is .terraform folder; if you want to change it set env variable:
        $ export TF_DATA_DIR=dir-name
    - Terraform has created lock file (.terraform.lock.hcl). It contains provider plugins & its corresponding hashes (per platform)
    - Terraform has successfully Initialized
    - Also validates syntax of terraform code!

- $ terraform init -upgrade
    - Will update any providers that were previously downloaded, but won't download any new ones

- $ terraform validate
    - Validates syntax of terraform code; also checks if variable is set or not set
    - Optional, since $ terraform init does it by default
    - However after init you have made any terraform code changes, then validate makes sense! 

- $ terraform plan
    - Dry run, doesn't create anything

- $ terraform plan -out=plan1
    - Saves plan to a file.
    - Binary file, we can't read it; but can extract information from it later

- $ terraform apply
    - First runs terraform plan & asks for confirmation to apply
- $ terraform apply -auto-approve
    - Creates resources
    - Creates terraform.tfstate file at root module (or aka main.tf)
    - Default 10 concurrent ops
        - Override concurrent ops by: $ terraform apply -parallelism=n
        - This concurrent ops is called walking the graph
    - Also creates / locks state file called terraform.tfstate.lock.info
        - This locks the state until run is completed
        - If for some reason terraform has not automatically unlocked state, use this cmd:
        $ terraform force-unlock LOCK_ID (where in you get LOCK_ID from terraform.tfstate.lock.info file) 

- $ terraform providers
    - Displays current providers used

- $ terraform output or
- $ terraform output ip_address or if you want to use it in shell scripting
- $(terraform output -raw ip_address) 
    - Shows all outputs or a specific output

- $ terraform show
    - Shows contents of state file in human readable format

- $ terraform state list
    - Shows all the resources created (as 1 line for each resource) 
- $ terraform state show aws_key
    - Shows a specific resource (in details), but in human readable format
    - $ terraform state show aws_instance | grep public_ip
- $ terraform state rm
    - step.1. Run  $ terraform state list to see a list of all Terraform-managed resources.
    - step.2. Run $ terraform state rm for each resource you want to keep, like the prod_db
        - For example: $ terraform state rm aws_instance.prod_db
    - step.3. Run $ terraform destroy to destroy all remaining resources. Terraform will not attempt to destroy the resource you preserved in step.2. because Terraform no longer manages it.

- $ terraform taint aws_instance.lab_05
    - Next time we run terraform apply, it will destroy the tainted resource & recreate it
- $ terraform untaint aws_instance.lab_05
- Since taint / untaint will soon be deprecated, better option is to do: $ terraform apply -replace aws_instance.lab_05

- Ways to destroy / clean up infrastructure:
    - $ terraform destroy or
    - $ terraform destroy -auto-approve
    - $ terraform destroy is an alias to terraform apply -destroy
    - terraform destroy --target aws_instance.demo_vm_1
        - To destroy a specific EC2 instance (demo_vm_1)
    - $ terraform plan -destroy
        - Speculative destroy plan

- Workspace related commands:
    - $ terraform workspace show
        - o/p: dev
    - $ terraform workspace new <uat>
    - $ terraform workspace list
        - o/p: dev*, uat
    - $ terraform workspace select <uat>
        - Select a specific workspace, in case of multiple workspaces
    - $ terraform workspace delete <dev>

- $ terraform console
    - Ensure $ terraform init is run first, cos it requires .tfstate file! Also, it locks the state file!
    - Provides playground for terraform functions!
        - > cidermask("172.16.0.0/12")
        - > max(1, 2,3)
        - > timestamp
        - > exit to exit from Console 
        - Approx. 100+ functions!

- Terraform Modules can be stored:
    a. Locally
    b. Publicly at TF registry
    c. Privately at TFC / TFE registry
    d. Git URLs, Mercurial URLs (i.e. VCS repos)
    e. Https urls (as .zip or .tar)
    f. Buckets (AWS S3)
- TF doesn't support Modules at:
    - BLOB storage
    - No DBs: Mysql or PostgreSQL 
    - ssh or ftp
- $ terraform get
    - Grab remote modules to local
    - Works without terraform init!
- Refer modules in tf config using module.resource.resource_label

- Terraform Logging:
    - Log immediately in terminal:
    $ TF_LOG=TRACE terraform apply
        - Log levels (from most verbose): Trace, Debug, Info, Warn, Error
        - Prepend LOG_TRACE to any terraform command, to enable logging
    - Log to file (logs are appended for each terraform command that we run):
    $ export TF_LOG_PATH=logs.txt
        - Note that even when TF_LOG_PATH is set, TF_LOG must be set in order for any logging to be enabled!
- Note: Turn on logging for entire terminal session:
    - $ export TF_LOG=TRACE
- $ export TF_LOG_CORE=TRACE
    - Logs things that happened inside terraform program
- $ export TF_LOG_PROVIDER=TRACE
    - Logs things that happened inside terraform provider plugins
- Disable logging: unset ENV variables by setting it to blank or exit terminal
- Note: if you set TF_LOG ENV variables, Logs will be displayed in stderr, meaning terminal; stderr is short for standard error and is used for diagnostic output. It is similar to stdout (standard output). Either way, results are displayed in terminal. 

- Check your configuration and state file and see if it matches existing infrastructure and if its different, it will update state file
    - $ terraform refresh
        - Outdated cmd now
    - Better to use:
    $ terraform apply -refresh-only

- You can specify multiple providers in terraform config
- You can also specify multiple AWS providers, say 1 for us-east-1 and other for us-west-1. In this case, 2nd AWS provider will be declared with alias and addressed via alias in resources or modules. If you don't specify provider, it defaults to first provider without alias!
    provider "aws" {
        region  = "us-east-1"
    }
    
    provider "aws" {
        region = "us-west-1"
        alias = "west"
    }
    
    resource "aws_instance" "foo" {
        provider = aws.west
        # ...
    }

- $ terraform import ADDR ID
    - Imports existing AWS resource created manually (i.e. resource created outside of Terraform), say EC2 into state file, but doesn't create terraform config file
    - Step.1. First create terraform config, say ec2 resource block with defaults
    - Step.2. $ terraform import aws_instance. myvm <aws instance ID>
        - $ terraform import module.vpc.aws_vpc.this <Aws vpc ID>
- The current implementation of Terraform import can only import resources into the state. It does not generate a configuration. Because of this, and before running terraform import, it is necessary to manually write a resource configuration block for the resource to which the imported object will be mapped.
    - First, add the resources to the configuration file:
        resource "aws_instance" "example" {
            # ...instance configuration...
        }
    - Then run the following command:
        $ terraform import aws_instance.example i-abcd1234
    - <https://developer.hashicorp.com/terraform/cli/commands/import>


## References
- [HashiCorp Certified: Terraform Associate (002)](https://www.hashicorp.com/certification/terraform-associate-002)
- [O'Reilly Live event by David Prowse on Terraform Associate Exam Cram](https://learning.oreilly.com/live-events/hashicorp-terraform-associate-exam-cram/0636920082746/0636920082745/)
- [Course material / code](https://github.com/daveprowse/tac-live)
- [Practice Exam David: 75 questions](https://learning.oreilly.com/certifications/9780138190408)
- [Contact David Prowse](https://prowse.tech)

