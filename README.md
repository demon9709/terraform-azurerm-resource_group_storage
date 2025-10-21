# terraform-azurerm-resource_group_storage
# Azure Resource Group and Storage Account Terraform Module

This module creates an Azure Resource Group and Storage Account with configurable parameters.

## Features

- Creates Azure Resource Group
- Creates Azure Storage Account with customizable settings
- Supports various storage account types and replication options
- Tag support for resource management

## Usage
module "storage" {
source = "YOUR_USERNAME/resource_group_storage/azurerm"
version = "1.0.0"

resource_group_name = "my-rg"
location = "West Europe"
storage_account_name = "mystorageaccount"
account_tier = "Standard"
account_replication_type = "LRS"

tags = {
Environment = "Production"
ManagedBy = "Terraform"
}
}

## Requirements

| Name | Version |
|------|---------|
| terraform | >= 1.0 |
| azurerm | >= 3.0 |

## Providers

| Name | Version |
|------|---------|
| azurerm | >= 3.0 |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| resource_group_name | Name of the resource group | `string` | n/a | yes |
| location | Azure region | `string` | `"West Europe"` | no |
| storage_account_name | Storage account name | `string` | n/a | yes |
| account_tier | Storage account tier | `string` | `"Standard"` | no |
| account_replication_type | Replication type | `string` | `"LRS"` | no |
| account_kind | Storage account kind | `string` | `"StorageV2"` | no |
| tags | Resource tags | `map(string)` | `{}` | no |

## Outputs

| Name | Description |
|------|-------------|
| resource_group_id | ID of the resource group |
| resource_group_name | Name of the resource group |
| storage_account_id | ID of the storage account |
| storage_account_name | Name of the storage account |
| storage_account_primary_access_key | Primary access key (sensitive) |
| storage_account_primary_blob_endpoint | Primary blob endpoint |

## Examples

See the [examples](./examples) directory for working examples.

## License

MIT License - see LICENSE file for details.

