# Get-BrokerCatalog

Gets catalogs configured for this site.

## 语法

    Get-BrokerCatalog [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerCatalog [[-Name] <String>] [-AllocationType <AllocationType>] [-AppDnaAnalysisState <AppDnaAnalysisState>] [-AssignedCount <Int32>] [-AvailableAssignedCount <Int32>] [-AvailableCount <Int32>] [-AvailableUnassignedCount <Int32>] [-Description <String>] [-HypervisorConnectionUid <Int32>] [-IsRemotePC <Boolean>] [-MachinesArePhysical <Boolean>] [-Metadata <String>] [-MinimumFunctionalLevel <FunctionalLevel>] [-PersistUserChanges <PersistUserChanges>] [-ProvisioningSchemeId <Guid>] [-ProvisioningType <ProvisioningType>] [-PvsAddress <String>] [-PvsDomain <String>] [-RemotePCDesktopGroupPriority <Int32>] [-RemotePCDesktopGroupUid <Int32>] [-RemotePCHypervisorConnectionUid <Int32>] [-ScopeId <Guid>] [-ScopeName <String>] [-SessionSupport <SessionSupport>] [-TenantId <Guid>] [-UnassignedCount <Int32>] [-UsedCount <Int32>] [-UUID <Guid>] [-ZoneName <String>] [-ZoneUid <Guid>] [-MachineUid <Int32>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Retrieves catalogs matching the specified criteria. If no parameters are specified this cmdlet enumerates all catalogs.

See about_Broker_Filtering for information about advanced filtering options.

\---\---\---\---\---\---\---\----- BrokerCatalog Object The catalog object returned represents a group of related physical or virtual machines that have been configured in the site.

See about_Broker_Machines for more information.

    -- AllocationType (Citrix.Broker.Admin.SDK.AllocationType)
       Denotes how the the machines in the catalog are allocated to a user.
       Possible values are:
       o Static: Machines get assigned to a user either by the admin or on first use. This relationship is static and changes only if an admin explicitly changes the assignments. o Random: Machines are allocated to users randomly from a pool of available machines.
    
    -- AppDnaAnalysisState (Citrix.Broker.Admin.SDK.AppDnaAnalysisState?)
       The AppDNA Analysis State of the catalog
    
    -- AssignedCount (System.Int32)
       The number of assigned machines (machines that have been assigned to a user/users or a client name/address).
    
    -- AvailableAssignedCount (System.Int32)
       The number of available machines (not in a desktop group), that are also assigned to users.
    
    -- AvailableCount (System.Int32)
       The number of available machines (those not in any desktop group).
    
    -- AvailableUnassignedCount (System.Int32)
       The number of available machines (those not in any desktop group) that are not assigned to users.
    
    -- Description (System.String)
       Description of the catalog.
    
    -- HypervisorConnectionUid (System.Int32?)
       The Uid of the hypervisor connection that is associated with the machines in the catalog. This property only applies to MCS provisioned catalogs. For other provisioning types machines can be from one or more different hypervisor connections.
    
    -- IsRemotePC (System.Boolean)
       Specifies whether or not the catalog is a RemotePC catalog. Remote PC catalogs automatically configure appropriate machines without the need for manual configuration. See about_Broker_RemotePC for more information.
    
    -- MachinesArePhysical (System.Boolean)
       Specifies whether or not the machines in the catalog can be power-managed by the broker.
    
    -- MetadataMap (System.Collections.Generic.Dictionary<string, string>)
       Holds any metadata associated with the catalog.
    
    -- MinimumFunctionalLevel (Citrix.Broker.Admin.SDK.FunctionalLevel)
       The expected minimal functional level of the machines in the catalog.
    
    -- Name (System.String)
       Name of the catalog.
    
    -- PersistUserChanges (Citrix.Broker.Admin.SDK.PersistUserChanges)
       Specifies how user changes are persisted on machines in the catalog. Possible values are:
       o OnLocal: User changes are stored on the machine's local storage.
       o Discard: User changes are discarded.
       o OnPvd: User changes are stored on the user's personal vDisk.
    
    -- ProvisioningSchemeId (System.Guid?)
       The GUID of the provisioning scheme (if any) associated with the catalog. This only applies if the provisioning type is MCS.
    
    -- ProvisioningType (Citrix.Broker.Admin.SDK.ProvisioningType)
       Specifies how the machines are provisioned in the catalog. Possible values are:
       o Manual: No provisioning.
       o PVS: Machine provisioned by PVS (machine may be physical, blade, VM...)
       o MCS: Machine provisioned by MCS (machine must be a VM).
    
    -- PvsAddress (System.String)
       IP address of the PVS server to be used in a catalog with a PVS ProvisioningType.
    
    -- PvsDomain (System.String)
       The domain of the PVS server to be used in a catalog with a PVS ProvisioningType.
    
    -- RemotePCDesktopGroupPriorities (System.Int32[])
       Remote PC desktop groups' association priorities.
    
    -- RemotePCDesktopGroupUids (System.Int32[])
       UIDs of the Remote PC desktop groups associated with this catalog.
    
    -- RemotePCHypervisorConnectionUid (System.Int32?)
       UID of the hypervisor connection used for powering on RemotePC machines in this catalog (only for catalogs with IsRemotePC set to true).
    
    -- Scopes (Citrix.Broker.Admin.SDK.ScopeReference[])
       The list of the delegated admin scopes to which the catalog belongs.
    
    -- SessionSupport (Citrix.Broker.Admin.SDK.SessionSupport)
       Specifies the session support of the machines in the catalog. Valid values are:
       SingleSession, MultiSession.
    
    -- TenantId (System.Guid?)
       Identity of tenant associated with catalog. Not applicable (always blank) in non-multitenant sites.
    
    -- Uid (System.Int32)
       Uid of the catalog.
    
    -- UnassignedCount (System.Int32)
       The number of unassigned machines (machines not assigned to users).
    
    -- UsedCount (System.Int32)
       The number of machines in the catalog that are in a desktop group.
    
    -- UUID (System.Guid)
       The global ID of the catalog.
    
    -- ZoneName (System.String)
       Name of the Zone associated with this catalog.
    
    -- ZoneUid (System.Guid)
       Uid of the Zone associated with this catalog.
    

## 相关命令

- [New-BrokerCatalog](New-BrokerCatalog.html)
- [Remove-BrokerCatalog](Remove-BrokerCatalog.html)
- [Rename-BrokerCatalog](Rename-BrokerCatalog.html)
- [Set-BrokerCatalog](Set-BrokerCatalog.html)

## 参数

| 名称                              | 说明                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| UID                             | Get catalogs with the specified UID.                                                                                                                                                                                                                                                                                                                                                                                                                                                               | true  | false |                                                                                        |
| 名称                              | Gets catalogs with the specified name.                                                                                                                                                                                                                                                                                                                                                                                                                                                             | false | false |                                                                                        |
| AllocationType                  | Gets catalogs that are of the specified allocation type. Values can be:  
o Static - Machines in a catalog of this type are permanently assigned to a user.  
o Permanent - equivalent to 'Static'.  
o Random - Machines in a catalog of this type are picked at random and temporarily assigned to a user.                                                                                                                                                                                       | false | false |                                                                                        |
| AppDnaAnalysisState             | Gets catalogs that have of the specified AppDNA Analysis State. Values can be:  
o None - No AppDNA analysis has not been preformed.  
o Capturing - AppDNA analysis is running and capturing infomation from a catalog machine.  
o Canceled - The AppDNA analysis process was cancelled.  
o Ready - The AppDNA analysis process has finished correctly.  
o Failed - The AppDNA analysis process failed.  
o Importing - AppDNA analysis is running and uploading results to the AppDNA server. | false | false |                                                                                        |
| AssignedCount                   | Gets catalogs containing a specified number of assigned machines (machines that have been assigned to users).  
This property is typically used with advanced filtering; see about_Broker_Filtering.                                                                                                                                                                                                                                                                                             | false | false |                                                                                        |
| AvailableAssignedCount          | Gets catalogs containing a specified number of available machines (those not in any desktop group) that are also assigned to users.  
This property is typically used with advanced filtering; see about_Broker_Filtering.                                                                                                                                                                                                                                                                       | false | false |                                                                                        |
| AvailableCount                  | Gets catalogs containing a specified number of available machines (those not in any desktop group).  
This property is typically used with advanced filtering; see about_Broker_Filtering.                                                                                                                                                                                                                                                                                                       | false | false |                                                                                        |
| AvailableUnassignedCount        | Gets catalogs containing a specified number of available machines (those not in any desktop group) that are not assigned to users.  
This property is typically used with advanced filtering; see about_Broker_Filtering.                                                                                                                                                                                                                                                                        | false | false |                                                                                        |
| 说明                              | Gets catalogs with the specified description.                                                                                                                                                                                                                                                                                                                                                                                                                                                      | false | false |                                                                                        |
| HypervisorConnectionUid         | Gets catalogs associated with the specified hypervisor connection.                                                                                                                                                                                                                                                                                                                                                                                                                                 | false | false |                                                                                        |
| IsRemotePC                      | Gets catalogs with the specified IsRemotePC value.                                                                                                                                                                                                                                                                                                                                                                                                                                                 | false | false |                                                                                        |
| MachinesArePhysical             | Specifies whether machines in the catalog can be power-managed by the Citrix Broker Service. Where the Citrix Broker Service cannot control the power state of the machine specify $true, otherwise $false. Can only be specified together with a provisioning type of Pvs or Manual, or if used with the legacy CatalogKind parameter only with Pvs or PvsPvd catalog kinds.                                                                                                                      | false | false |                                                                                        |
| 元数据                             | 获取具有匹配的元数据条目的记录。  
比较的值由键名、冒号和值组成。 例如：-Metadata "abc:x*" 匹配具有键名为“abc”且值以字母“x”开头的元数据条目的记录。                                                                                                                                                                                                                                                                                                                                                                                                          | false | false |                                                                                        |
| MinimumFunctionalLevel          | Gets catalogs with a specific MinimumFunctionalLevel.  
Valid values are L5, L7, L7_6                                                                                                                                                                                                                                                                                                                                                                                                              | false | false |                                                                                        |
| PersistUserChanges              | Gets catalogs with the specified behavior when persisting changes made by the end user. Possible values are:  
o OnLocal - User changes are stored on the machine's local storage.  
o Discard - User changes are discarded.  
o OnPvd - User changes are stored on the user's personal vDisk.                                                                                                                                                                                                     | false | false |                                                                                        |
| ProvisioningSchemeId            | Gets catalogs associated with the specified provisioning scheme.                                                                                                                                                                                                                                                                                                                                                                                                                                   | false | false |                                                                                        |
| ProvisioningType                | Specifies the provisioning type for the catalog. Values can be:  
o Manual - No provisioning.  
o PVS - Machine provisioned by PVS (machine may be physical, blade, VM,...).  
o MCS - Machine provisioned by MCS (machine must be VM).                                                                                                                                                                                                                                                            | false | false |                                                                                        |
| PvsAddress                      | Gets catalogs containing machines provided by the Provisioning Services server with the specified address.                                                                                                                                                                                                                                                                                                                                                                                         | false | false |                                                                                        |
| PvsDomain                       | Gets catalogs containing machines provided by the Provisioning Services server in the specified domain.                                                                                                                                                                                                                                                                                                                                                                                            | false | false |                                                                                        |
| RemotePCDesktopGroupPriority    | Gets Remote PC catalogs with a Remote PC desktop group association with the specified priority.                                                                                                                                                                                                                                                                                                                                                                                                    | false | false |                                                                                        |
| RemotePCDesktopGroupUid         | Gets Remote PC catalogs associated with the specified Remote PC desktop group.                                                                                                                                                                                                                                                                                                                                                                                                                     | false | false |                                                                                        |
| RemotePCHypervisorConnectionUid | Gets Remote PC catalogs associated with the specified Remote PC hypervisor connection.                                                                                                                                                                                                                                                                                                                                                                                                             | false | false |                                                                                        |
| ScopeId                         | Gets catalogs that are associated with the given scope identifier.                                                                                                                                                                                                                                                                                                                                                                                                                                 | false | false |                                                                                        |
| ScopeName                       | Gets catalogs that are associated with the given scope name.                                                                                                                                                                                                                                                                                                                                                                                                                                       | false | false |                                                                                        |
| SessionSupport                  | Gets catalogs that have the specified session capability. Values can be:  
o SingleSession - Single-session only machine.  
o MultiSession - Multi-session capable machine.                                                                                                                                                                                                                                                                                                                        | false | false |                                                                                        |
| TenantId                        | Gets catalogs associated with the specified tenant identity.                                                                                                                                                                                                                                                                                                                                                                                                                                       | false | false |                                                                                        |
| UnassignedCount                 | Gets catalogs containing a specified number of unassigned machines (machines not assigned to users).  
This property is typically used with advanced filtering; see about_Broker_Filtering.                                                                                                                                                                                                                                                                                                      | false | false |                                                                                        |
| UsedCount                       | Gets catalogs containing a specified number of machines used in a desktop group.  
This property is typically used with advanced filtering; see about_Broker_Filtering.                                                                                                                                                                                                                                                                                                                          | false | false |                                                                                        |
| UUID                            | Get catalogs with the specified global ID.                                                                                                                                                                                                                                                                                                                                                                                                                                                         | false | false |                                                                                        |
| ZoneName                        | Gets catalogs located in the zone with the specified name.                                                                                                                                                                                                                                                                                                                                                                                                                                         | false | false |                                                                                        |
| ZoneUid                         | Gets machines located in the zone with the specified UID.                                                                                                                                                                                                                                                                                                                                                                                                                                          | false | false |                                                                                        |
| MachineUid                      | Gets the catalog containing the machine referenced by the specified unique identifier (UID).                                                                                                                                                                                                                                                                                                                                                                                                       | false | false |                                                                                        |
| ReturnTotalRecordCount          | When specified, this causes the cmdlet to output an error record containing the number of records available. 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Broker_Filtering for details.                                                                                                                                                                                                                                                                                                                   | false | false | False                                                                                  |
| MaxRecordCount                  | 指定要返回的最大记录数。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | false | false | 250                                                                                    |
| 跳过                              | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                                                                                                                                                                                                                                                                                                                                                                                                              | false | false |                                                                                        |
| SortBy                          | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。                                                                                                                                                                                                                                                                                                                                                                                                           | false | false | 默认排序顺序是按名称或唯一标识符。                                                                      |
| 过滤器                             | Gets records that match a PowerShell style filter expression. See about_Broker_Filtering for details.                                                                                                                                                                                                                                                                                                                                                                                            | false | false |                                                                                        |
| 属性                              | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                                                                                                                                                                                                                                                                                                                                                                                                             | false | false |                                                                                        |
| AdminAddress                    | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                                                                                                                                                                                                                                                                                                 | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

## 返回值

### Citrix.Broker.Admin.SDK.Catalog

Get-BrokerCatalog returns an object for each matching catalog.

## 示例

### 示例 1

    C:\PS> Get-BrokerCatalog -AllocationType Random
    C:\PS> Get-BrokerCatalog -Filter { AllocationType  -eq 'Random'}
    

Description  
\---\---\-----  
These commands return all catalogs containing machines that are randomly assigned to users. The second form uses advanced filtering (see about_Broker_Filtering).

### 示例 2

    C:\PS> Get-BrokerCatalog -Filter { AvailableCount  -gt 10}
    

Description  
\---\---\-----  
This command returns catalogs with more than 10 unused machines that are available for assignment to users.

### 示例 3

    C:\PS> Get-BrokerCatalog -MaxRecordCount 1 -ProvisioningType Manual -SortBy '-AvailableCount'
    

Description  
\---\---\-----  
This command returns the unmanaged catalog with the highest number of available machines.