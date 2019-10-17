# building-a-windows-dc-terraform
Building a Windows 2016 Domain Controller using Ansible + Terrraform on AWS

## Running

1. `git clone https://github.com/d1vious/building-a-windows-dc-terraform && cd building-a-windows-dc-terraform` clone project and cd into the project dir
2. Customize any environment parameters necessary under `variables.tf`
3. Setup your variables for your environment under `terraform.tfvars`, set your own password, and public IP in the whitelist
4. Run `terraform init` and then `terraform apply`

**make sure that you [configure](#configure) terraform first**

## Configure 

1. `brew install terraform` install terraform CLI on OSX [other platforms](https://www.terraform.io/downloads.html)
2. `brew install awscli`  install aws CLI on OSX otherwise see: [guide](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html)
3. Get AWS API token `aws configure` 
4. Set terraform variables under [terraform/terraform.tfvars](https://github.com/splunk/attack_range/blob/develop/terraform/terraform.tfvars.example)

**if on OSX please first set the following env variable:** `export OBJC_DISABLE_INITIALIZE_FORK_SAFETY=YES` otherwise you will see the following errors when running Ansible:

```
aws_instance.windows_2016_dc (local-exec): TASK [Gathering Facts] *********************************************************
aws_instance.windows_2016_dc (local-exec): objc[7843]: +[__NSCFConstantString initialize] may have been in progress in another thread when fork() was called.
aws_instance.windows_2016_dc (local-exec): objc[7843]: +[__NSCFConstantString initialize] may have been in progress in another thread when fork() was called. We cannot safely call it or ignore it in the fork() child process. Crashing instead. Set a breakpoint on objc_initializeAfterForkError to debug.
aws_instance.windows_2016_dc: Still creating
```