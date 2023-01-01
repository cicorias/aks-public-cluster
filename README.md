# aks-public-cluster
Simple public AKS cluster with automatic authorized IP address configuration for demos.

<!-- BEGIN_TF_DOCS -->
## Requirements

| Name                                                                      | Version |
|---------------------------------------------------------------------------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | ~> 1.3  |
| <a name="requirement_azurerm"></a> [azurerm](#requirement\_azurerm)       | ~>3.24  |
| <a name="requirement_http"></a> [http](#requirement\_http)                | ~> 3.2  |

## Providers

| Name                                                          | Version |
|---------------------------------------------------------------|---------|
| <a name="provider_azurerm"></a> [azurerm](#provider\_azurerm) | ~>3.24  |
| <a name="provider_http"></a> [http](#provider\_http)          | ~> 3.2  |

## Modules

No modules.

## Resources

| Name                                                                                                                                         | Type        |
|----------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| [azurerm_kubernetes_cluster.main](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/kubernetes_cluster)        | resource    |
| [azurerm_subnet.main](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/subnet)                                | resource    |
| [azurerm_user_assigned_identity.aks](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/user_assigned_identity) | resource    |
| [azurerm_virtual_network.main](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/virtual_network)              | resource    |
| [azurerm_resource_group.main](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/data-sources/resource_group)             | data source |
| [http_http.myip](https://registry.terraform.io/providers/hashicorp/http/latest/docs/data-sources/http)                                       | data source |

## Inputs

| Name                                                                                                                                 | Description                                                    | Type     | Default                         | Required |
|--------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|----------|---------------------------------|:--------:|
| <a name="input_cluster_dns_prefix"></a> [cluster\_dns\_prefix](#input\_cluster\_dns\_prefix)                                         | DNS prefix for AKS cluster                                     | `string` | `"akspubliccluster"`            |    no    |
| <a name="input_cluster_dns_service_ip_address"></a> [cluster\_dns\_service\_ip\_address](#input\_cluster\_dns\_service\_ip\_address) | IP address for the cluster's DNS service                       | `string` | `"172.16.16.254"`               |    no    |
| <a name="input_cluster_docker_bridge_address"></a> [cluster\_docker\_bridge\_address](#input\_cluster\_docker\_bridge\_address)      | CIDR range for the docker bridge in the cluster                | `string` | `"172.17.0.1/16"`               |    no    |
| <a name="input_cluster_identity"></a> [cluster\_identity](#input\_cluster\_identity)                                                 | Name of the MSI (Managed Service Identity) for the AKS cluster | `string` | `"identity-public-aks-cluster"` |    no    |
| <a name="input_cluster_name"></a> [cluster\_name](#input\_cluster\_name)                                                             | Name for the public AKS cluster                                | `string` | `"aks-public-cluster"`          |    no    |
| <a name="input_cluster_service_ip_range"></a> [cluster\_service\_ip\_range](#input\_cluster\_service\_ip\_range)                     | CIDR range for the cluster's kube-system services              | `string` | `"172.16.16.0/24"`              |    no    |
| <a name="input_cluster_sku_tier"></a> [cluster\_sku\_tier](#input\_cluster\_sku\_tier)                                               | SKU tier selection between Free and Paid                       | `string` | `"Free"`                        |    no    |
| <a name="input_default_node_pool_vm_size"></a> [default\_node\_pool\_vm\_size](#input\_default\_node\_pool\_vm\_size)                | Size of nodes in the k8s cluster's default node pool           | `string` | `"Standard_D2s_v3"`             |    no    |
| <a name="input_resource_group_name"></a> [resource\_group\_name](#input\_resource\_group\_name)                                      | Name of the existing resource group to create the cluster in   | `string` | n/a                             |   yes    |
| <a name="input_subnet_cidr"></a> [subnet\_cidr](#input\_subnet\_cidr)                                                                | CIDR range for the cluster subnet                              | `string` | `"172.16.0.0/20"`               |    no    |
| <a name="input_subnet_name"></a> [subnet\_name](#input\_subnet\_name)                                                                | Name of the subnet where all resources will be                 | `string` | `"subnet-public-aks"`           |    no    |
| <a name="input_vnet_cidr"></a> [vnet\_cidr](#input\_vnet\_cidr)                                                                      | CIDR range for the virtual network                             | `string` | `"172.16.0.0/16"`               |    no    |
| <a name="input_vnet_name"></a> [vnet\_name](#input\_vnet\_name)                                                                      | Name of the virtual network where all resources will be        | `string` | `"vnet-public-aks"`             |    no    |

## Outputs

| Name                                                                                                                                      | Description                                                                           |
|-------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|
| <a name="output_api_server_authorized_ip_ranges"></a> [api\_server\_authorized\_ip\_ranges](#output\_api\_server\_authorized\_ip\_ranges) | CIDR range of IP addresses that can access the cluster's API server's public endpoint |
| <a name="output_credentials-command"></a> [credentials-command](#output\_credentials-command)                                             | Command to get the cluster's credentials with az cli                                  |
| <a name="output_id"></a> [id](#output\_id)                                                                                                | ID of the created kubernetes cluster                                                  |
| <a name="output_invoke-command"></a> [invoke-command](#output\_invoke-command)                                                            | Sample command to execute k8s commands on the cluster using az cli                    |
| <a name="output_name"></a> [name](#output\_name)                                                                                          | Name of the kubernetes cluster created by this module                                 |
| <a name="output_resource_group_name"></a> [resource\_group\_name](#output\_resource\_group\_name)                                         | Name of the resource group where the cluster was created                              |
<!-- END_TF_DOCS -->