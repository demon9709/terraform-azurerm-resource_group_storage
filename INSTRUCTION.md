# Instructions for Using the Azure Resource Group and Storage Account Module

## Prerequisites

1. Terraform >= 1.0 installed
2. Azure CLI installed and configured
3. Azure subscription with appropriate permissions

## Authentication

Configure Azure authentication using one of the following methods:

### Azure CLI
az login
az account set --subscription="SUBSCRIPTION_ID"

### Service Principal
export ARM_CLIENT_ID="your-client-id"
export ARM_CLIENT_SECRET="your-client-secret"
export ARM_SUBSCRIPTION_ID="your-subscription-id"
export ARM_TENANT_ID="your-tenant-id


## Installation

### From Terraform Registry

module "storage" {
source = "YOUR_USERNAME/resource_group_storage/azurerm"
version = "1.0.0"

Required variables
resource_group_name = "my-rg"
storage_account_name = "mystorageaccount"
}

### From GitHub (Development)

module "storage" {
source = "github.com/YOUR_USERNAME/terraform-azurerm-resource_group_storage"

resource_group_name = "my-rg"
storage_account_name = "mystorageaccount"
}


## Quick Start

1. Create a `main.tf` file:
terraform {
required_providers {
azurerm = {
source = "hashicorp/azurerm"
version = "~> 3.0"
}
}
}

provider "azurerm" {
features {}
}

module "storage" {
source = "YOUR_USERNAME/resource_group_storage/azurerm"
version = "1.0.0"

resource_group_name = "example-rg"
location = "West Europe"
storage_account_name = "examplestorageacc"

tags = {
Environment = "Development"
Project = "Example"
}
}

output "storage_account_name" {
value = module.storage.storage_account_name
}

2. Initialize Terraform:
terraform init

3. Review the plan:

terraform plan


4. Apply the configuration:

terraform apply

## Advanced Configuration

### Custom Storage Account Settings
module "storage" {
source = "YOUR_USERNAME/resource_group_storage/azurerm"
version = "1.0.0"

resource_group_name = "prod-rg"
location = "East US"
storage_account_name = "prodstorageacc"
account_tier = "Premium"
account_replication_type = "ZRS"
account_kind = "BlockBlobStorage"

tags = {
Environment = "Production"
CostCenter = "Engineering"
}
}

## Troubleshooting

### Storage Account Name Already Exists
- Storage account names must be globally unique across Azure
- Use a different name or check if you already own the account

### Invalid Storage Account Name
- Must be 3-24 characters
- Only lowercase letters and numbers
- No special characters or spaces

## Support

For issues and questions:
- GitHub Issues: https://github.com/YOUR_USERNAME/terraform-azurerm-resource_group_storage/issues
- Documentation: See README.md

## Version History

- v1.0.0 - Initial release
