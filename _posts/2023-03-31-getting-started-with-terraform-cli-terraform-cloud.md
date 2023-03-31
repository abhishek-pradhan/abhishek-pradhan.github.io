---
title: Getting started with Terraform CLI (OSS) and Terraform Cloud
date: 2023-03-31 12:15
categories: [Terraform, AWS]
tags: [terraform, aws]
render_with_liquid: false
---

This article will help you to setup Terraform CLI (OSS) and Terraform Cloud.

## Getting started with Terraform Cloud
1. Create free Terraform Cloud account: <a href="https://cloud.hashicorp.com/products/terraform">Terraform | HashiCorp Cloud Platform</a>
2. Setup Terraform CLI: <a href="https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli">Install Terraform | Terraform | HashiCorp Developer</a>
3. Download Terraform's Hello World (it's called getting-started example) terraform template from github: <a href="https://github.com/hashicorp/tfc-getting-started">GitHub - hashicorp/tfc-getting-started: An example Terraform configuration for Terraform Cloud</a>
4. Run setup.sh script & enjoy the show!

## Setup Terraform CLI
> Note: I have shown 3 ways / 3 platforms for installing Terraform CLI.
{: .prompt-info }

1. Install Terraform on Windows 10 / 11
2. Install Terraform on Linux Ubuntu or WSL Ubuntu
3. Install terraform on AWS Cloud9 IDE

### Install Terraform on Windows 10 / 11
> Pre-requisite:  Ensure that you have installed [GIT Bash](https://git-scm.com/download/win), since as part of Terraform's Hello World example, we will have to run shell script on Windows.
{: .prompt-tip }

- Download terraform CLI for [Windows](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli)
  - <https://developer.hashicorp.com/terraform/downloads> -> OS -> Windows -> Binary download for Windows -> Downloaded AMD64, since I am using 64-bit operating system, x64-based processor
  - Run below command to check if you are using 32 or 64 bit Windows:
    ```terminal
    wmic os get osarchitecture
    ```
- Unzip terraform_1.4.2_windows_amd64.zip to any folder and place terraform.exe in terraform folder, in my case I am using C:\terraform:
    ```terminal
    mkdir "C:\terraform"
    ```
- Open terminal and set Environment variable Path:
    ```terminal
    setx PATH "%PATH%;C:\terraform"
    ```

- Terraform cli setup is complete, now test terraform cli:
    ```terminal
    terraform -v
    ```

#### Setup Terraform cloud using Terraform cli
> Note: Use the Terraform account that you created as part of #1 in above Getting started section. 
{: .prompt-info }

- Run below login command and perform steps 1, 2:
  ```terminal
  terraform login
  ```
  
  1. Enter yes & then enter your Terraform cloud credentials in the default browser which was auto-opened for you
  2. On successful login, it generates token when you click on 'Create API token' popup. Remember to copy and paste token to terminal & to your notes / scratch pad. We should now be successfully connected to Terraform Cloud! (see below screenshot):
    ![successfull terraform cloud login](/assets/img/posts/2023-03-31-getting-started-with-terraform-cli-terraform-cloud/gitbash-terraform-cloud-login.png)
    *Screenshot: Successfull Terraform Cloud login*

  > Tip: Terraform will store the token in plain text for use by subsequent commands: C:\Users\abhi\AppData\Roaming\terraform.d\credentials.tfrc.json
  {: .prompt-tip }

- From here on, we will follow steps provided by Terraform (these are shown at the bottom in the above screenshot):
  - ```terminal
    git clone https://github.com/hashicorp/tfc-getting-started.git
    ```
  - Navigate to folder containing project:
    ```terminal
    cd tfc-getting-started
    ```
  - Open up this folder having Terraform config in VS code (or any of your favourite IDE) to view TF files
    > Tip: Ensure you have installed VS Code's Terraform extension by Hashicorp for support for .tf files
    {: .prompt-tip }
  - Now we need to execute shell script (.sh) on Windows. This is why we have been Git Bash terminal.
    > Note: Before you run shell file from Git bash, we need jq installed:
			curl -L -o /C/terraform/jq.exe https://github.com/stedolan/jq/releases/latest/download/jq-win64.exe
    {: .prompt-info }
    Run the setup script and follow the prompts to finish setup and perform your first Terraform Cloud run! 
    ```terminal
    ./scripts/setup.sh
    ```
    - It will create Terraform Cloud Organization, Workspace and finally infrastructure. You can view all of this in your Terraform Cloud account (screenshot below):
      ![successfull terraform cloud run](/assets/img/posts/2023-03-31-getting-started-with-terraform-cli-terraform-cloud/terraform-cloud-run.png)
      *Screenshot: Successfull Terraform Cloud run*

### Install Terraform on Linux Ubuntu or WSL Ubuntu
> Note: You can perform the exact below steps on WSL Ubuntu for Windows
{: .prompt-info }

- Download terraform CLI using Linux -> Ubuntu/Debian instructions: <a href="https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli">Install Terraform | Terraform | HashiCorp Developer</a>

- Ensure that your system is up to date, and you have the gnupg, software-properties-common, and curl packages installed. You will use these packages to verify HashiCorp's GPG signature, and install HashiCorp's Debian package repository:
  ```terminal
  sudo apt-get update && sudo apt-get install -y gnupg software-properties-common
  ```

- Install the HashiCorp GPG key:
  ```terminal
  wget -O- https://apt.releases.hashicorp.com/gpg | \
		    gpg --dearmor | \
		    sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg
  ```

- Verify the key's fingerprint:
  ```terminal
  gpg --no-default-keyring \
		    --keyring /usr/share/keyrings/hashicorp-archive-keyring.gpg \
    --fingerprint
    ```
  
- Add the official HashiCorp repository to your system. The lsb_release -cs command finds the distribution release codename for your current system, such as buster, groovy, or sid:
  ```terminal
  echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] \
		    https://apt.releases.hashicorp.com $(lsb_release -cs) main" | \
		    sudo tee /etc/apt/sources.list.d/hashicorp.list
  ```

- Download the package information from HashiCorp:
  ```terminal
  sudo apt update
  ```

- Install Terraform from the new repository:
  ```terminal
  sudo apt-get install terraform
  ```

- Terraform cli setup is complete, now test terraform cli:
    ```terminal
    terraform -v
    ```

#### Setup Terraform cloud using Terraform cli
> Note: Use the Terraform account that you created as part of #1 in above Getting started section. 
{: .prompt-info }

- Run below login command and perform steps 1, 2:
  ```terminal
  terraform login
  ```
  
  1. Enter yes & then enter your Terraform cloud credentials in the default browser which was auto-opened for you
  2. On successful login, it generates token when you click on 'Create API token' popup. Remember to copy and paste token to terminal & to your notes / scratch pad. We should now be successfully connected to Terraform Cloud! (see below screenshot):
    ![successfull terraform cloud login](/assets/img/posts/2023-03-31-getting-started-with-terraform-cli-terraform-cloud/terraform-cloud-login.png)
    *Screenshot: Successfull Terraform Cloud login*

  > Tip: Terraform will store the token in plain text for use by subsequent commands: /home/abhi/.terraform.d/credentials.tfrc.json
  {: .prompt-tip }

- From here on, we will follow steps provided by Terraform (these are shown at the bottom in the above screenshot):
  - ```terminal
    git clone https://github.com/hashicorp/tfc-getting-started.git
    ```
  - Navigate to folder containing project:
    ```terminal
    cd tfc-getting-started
    ```
  - Open up this folder having Terraform config in VS code (or any of your favourite IDE) to view TF files
    > Tip: Ensure you have installed VS Code's Terraform extension by Hashicorp for support for .tf files
    {: .prompt-tip }

    > Note: Before you run shell file, we need jq installed: sudo apt install jq
    {: .prompt-info }

    Run the setup script and follow the prompts to finish setup and perform your first Terraform Cloud run! 
    ```terminal
    ./scripts/setup.sh
    ```
    - It will create Terraform Cloud Organization, Workspace and finally infrastructure. You can view all of this in your Terraform Cloud account (screenshot below):
      ![successfull terraform cloud run](/assets/img/posts/2023-03-31-getting-started-with-terraform-cli-terraform-cloud/terraform-cloud-run.png)
      *Screenshot: Successfull Terraform Cloud run*

### Install terraform on AWS Cloud9 IDE
> Note: AWS Cloud9 IDE will incur you charges, ensure to clean-up / detroy Cloud9 environment once you are done with it.
{: .prompt-info }
- Create a cloud9 IDE from AWS console and you are ready to use terraform! No need to setup / install Terraform CLI, since it is already installed for us!
  - You get aws cli, git, terraform cli setup out of the box!

- When you create cloud9 IDE, all defaults were selected, with 2 key points:
  - Connection = AWS Systems Manager (SSM)
  - Platform = Amazon Linux 2
  - ![aws cloud9 settings](/assets/img/posts/2023-03-31-getting-started-with-terraform-cli-terraform-cloud/cloudnine-settings1.png)
  - ![aws cloud9 settings](/assets/img/posts/2023-03-31-getting-started-with-terraform-cli-terraform-cloud/cloudnine-settings2.png)

- Once Cloud9 IDE is created, launch it & fire away git, terraform commands!
  - terraform login
  - git clone https://github.com/hashicorp/tfc-getting-started.git
  - cd tfc-getting-started && ./scripts/setup.sh

		> Note: If you get jq error when running setup.sh, then install jq in Cloud9 IDE: "It looks like 'jq' is not installed; please install it and run this setup script again."
			sudo yum install jq  
			./scripts/setup.sh
    {: .prompt-info }

- Also, alternately you can upload your code to Cloud 9, make changes in Cloud9 IDE & download the code back, if you don't want to do it git way.

- Cloud9 IDE is the easiest way to get started with Terraform Cloud! (see below screenshot):
  ![aws cloud9 terraform success](/assets/img/posts/2023-03-31-getting-started-with-terraform-cli-terraform-cloud/cloudnine-terraform-success.png)
  *Screenshot: AWS Cloud9 Terraform Success*
  
- Successful Terraform run from Cloud9 IDE (screenshot below):
  ![successfull terraform cloud run](/assets/img/posts/2023-03-31-getting-started-with-terraform-cli-terraform-cloud/terraform-cloud-run.png)
  *Screenshot: Successfull Terraform Cloud run*
