# Azure RM Windows Spirent TestCenter Application Terraform

## Description

Run a Windows Server instance and install the Windows Spirent TestCenter application.
After the instance has been started connect using Remote Desktop to use Spirent TestCenter.

[Spirent TestCenter Virtual](https://github.com/Spirent-terraform-Modules/terraform-azurerm-stcv)
traffic generator instances can be created via Terraform.

## Prerequisites

- Obtain a copy of the Windows Spirent TestCenter Application from http://support.spirent.com.
Be sure to update the `stc_installer` variable to point to this file.

## Connect to Windows Server

After the Windows Server instance is running, you can connect to it over Remote Desktop (RDP).

1. Find the Windows Server instance you provisioned in the Azure dashboard.
2. Select the instance and click _Connect_, _RDP_.
3. Select the _RDP_ tab and click _Download RDP File_.
4. Locate and launch the RDP file you downloaded in step 3.
5. Click _Connect_ and provide the user and password you set in variables `admin_username` and `stc_windows_pw`.
6. You may receive a security warning about an insecure certificate due to the instance using a self-signed certificate.  Click _Yes_ to continue.
7. You should now see the Windows desktop with a shortcut to the Spirent TestCenter Application.
8. Launch the Spirent TestCenter Application.


<!-- BEGINNING OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
## Requirements

| Name | Version |
|------|---------|
| terraform | >= 0.13.0 |
| azurerm | >=2.37.0 |
| azurerm | >=2.37.0 |

## Providers

| Name | Version |
|------|---------|
| azurerm | >=2.37.0 >=2.37.0 |
| null | n/a |
| template | n/a |

## Modules

No Modules.

## Resources

| Name |
|------|
| [azurerm_network_interface](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/network_interface) |
| [azurerm_network_interface_security_group_association](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/network_interface_security_group_association) |
| [azurerm_network_security_group](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/network_security_group) |
| [azurerm_public_ip](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/public_ip) |
| [azurerm_virtual_machine_extension](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/virtual_machine_extension) |
| [azurerm_windows_virtual_machine](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/windows_virtual_machine) |
| [null_resource](https://registry.terraform.io/providers/hashicorp/null/latest/docs/resources/resource) |
| [template_file](https://registry.terraform.io/providers/hashicorp/template/latest/docs/data-sources/file) |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| admin\_username | Local administrator user name. | `string` | `"adminuser"` | no |
| dest\_dir | Destination directory on the instance where files will be copied. | `string` | `"c:/users/adminuser/downloads"` | no |
| enable\_provisioner | Enable provisioning. | `bool` | `true` | no |
| ingress\_cidr\_blocks | List of management interface ingress IPv4/IPv6 CIDR ranges. | `list(string)` | n/a | yes |
| instance\_count | Number of instances to create. | `number` | `1` | no |
| instance\_name | Name assigned to the Windows STC GUI instance.  An instance number will be appended to the name. | `string` | `"stcgui"` | no |
| instance\_size | The Azure Virtual Machine SKU. | `string` | `"Standard_DS1_v2"` | no |
| marketplace\_version | Version of the Windows server image. | `string` | `"latest"` | no |
| mgmt\_plane\_subnet\_id | Management public Azure subnet ID. | `string` | `""` | no |
| resource\_group\_location | Resource group location in Azure. | `string` | `"West US 2"` | no |
| resource\_group\_name | Resource group name in Azure. | `string` | n/a | yes |
| stc\_installer | File path to 'Spirent TestCenter Application x64.exe' or 'Spirent TestCenter Application.exe' installer. | `string` | n/a | yes |
| stc\_windows\_pw | Specify the windows password with a TF\_VAR\_stc\_windows\_pw environment variable | `string` | n/a | yes |

## Outputs

| Name | Description |
|------|-------------|
| instance\_ids | List of instance IDs |
| instance\_private\_ips | List of private IP addresses assigned to the instances, if applicable |
| instance\_public\_ips | List of public IP addresses assigned to the instances, if applicable |
<!-- END OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
