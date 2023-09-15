# Step 1 - Configuring the Virtual Machine Scale Set manually

## Prereqs

- [Terraform installed](https://developer.hashicorp.com/terraform/downloads?product_intent=terraform)
- [Azure CLI installed](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli)

## Deployment

We have published [this Terraform module](https://registry.terraform.io/modules/amestofortytwo/selfhostedrunnervmss/azurerm) for simplified deployment. If you are not familiar with using Terraform, consider using the [manual method](./azuredevops-vmss-step1-manual.md) instead, but it should be fairly easy for most people. 

Start by creating an empty folder with a single file ```main.tf```, with the below content:

```hcl
provider "azurerm" {
  features {}
}

module "vmss" {
  source                         = "amestofortytwo/selfhostedrunnervmss/azurerm"
  operating_system               = "ubuntu"       # windows or ubuntu
  runner_platform                = "azure_devops" # azure_devops or github
}
```

Next, open a shell (cmd, terminal, powershell) and run the following:

```PowerShell
az login
az account set --subscription "<your subscription id>"
terraform init
terraform apply
```

[Continue to step 2 - Configuring the Azure DevOps Agent Pool](./step2.md)