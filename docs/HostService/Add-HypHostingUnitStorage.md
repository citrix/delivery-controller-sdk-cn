# Add-HypHostingUnitStorage

Adds storage locations to a hosting unit.

## 语法

    Add-HypHostingUnitStorage [-LiteralPath] <String> [-StoragePath] <String> [-StorageType <StorageType>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Use this command to add storage locations for storing the hard disks required by the virtual machines created by the Citrix Machine Creation Service. You cannot use this command if the connection for the hosting unit is in maintenance mode.

## 相关命令

- [New-Item](New-Item.html)
- [Add-HypMetadata](Add-HypMetadata.html)
- [Remove-HypHostingUnitStorage](Remove-HypHostingUnitStorage.html)
- [Set-HypHostingUnitStorage](Set-HypHostingUnitStorage.html)

## 参数

| 名称           | 说明                                                                                                                                                                                                                                                                                                                                                                   | 是否必需？ | 管道输入           | 默认值                                  |
| ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | ------------------------------------ |
| LiteralPath  | Specifies the path to the hosting unit to which storage will be added. The path must be in one of the following formats: <drive>:\HostingUnits\<hostingunitname> 或者 <drive>:\HostingUnits\{<hostingunit uid>}                                                                                                                                                    | true  | false          |                                      |
| StoragePath  | Specifies the path to the storage that will be added. The path must be in one of the following formats: <drive>:\Connections\<connectionname>\MyStorage.storage or <drive>:\Connections\{<connection uid>}\MyStorage.storage or <drive>:\HostingUnits\<hostingunitname>\MyStorage.storage or <drive>:\HostingUnits\{<hostingunit uid>}\MyStorage.storage | true  | true (ByValue) |                                      |
| StorageType  | Specifies the type of storage in StoragePath. Supported storage types are: OSStorage PersonalvDiskStorage TemporaryStorage                                                                                                                                                                                                                                           | false | false          | OSStorage                            |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                                                               | false | false          |                                      |
| AdminAddress | Specifies the address of a XenDesktop controller to which the PowerShell snap-in connects. This can be a host name or an IP address.                                                                                                                                                                                                                                 | false | false          | LocalHost。有 cmdlet 提供了某个值后，此值将变为默认值。 |

## 输入类型

### System.string  
You can pipe a string that contains a path to Add-HypHostingUnitStorage (StoragePath parameter).

## 返回值

### Citrix.Host.Sdk.HostingUnit  
Add-HypHostingUnitStorage returns an object containing the new definition of the hosting unit.  
HostingUnitUid <guid>  
Specifies the unique identifier for the hosting unit.  
HostingUnitName <string>  
Specifies the name of the hosting unit.  
HypervisorConnection <Citrix.Host.Sdk.HypervisorConnection>  
Specifies the connection that the hosting unit uses to access a hypervisor.  
RootId <string>  
Identifies, to the hypervisor, the root of the hosting unit.  
RootPath <string>  
The hosting unit provider path that represents the root of the hosting unit.  
Storage <Citrix.Host.Sdk.Storage[]>  
The list of storage items that the hosting unit can use.  
PersonalvDiskStorage <Citrix.XDPowerShell.Storage[]>  
The list of storage items that the hosting unit can use for storing personal data.  
VMTaggingEnabled <boolean>  
Specifies whether or not the metadata in the hypervisor can be used to store information about the XenDesktop Machine Creation Service.  
NetworkId <string>  
The hypervisor's internal identifier that represents the network specified for the hosting unit.  
NetworkPath <string>  
The hosting unit provider path to the network specified for the hosting unit.  
AdditionalStorage  
The list of additional storage items that the hosting unit can use.  
Metadata <Citrix.Host.Sdk.Metadata[]>  
A list of key value pairs that can store additional information about the hosting unit.

## Notes The storage path must be valid for the hosting unit. The rules that are applied are as follows: XenServer (HypervisorConnection Type = XenServer)  
NA  
VMWare vSphere/ESX (HypervisorConnection Type = vCenter)  
The storage path must be directly contained in the root path item of the hosting unit.  
Microsoft SCVMM/Hyper-v (HypervisorConnection Type = SCVMM)  
Only one storage entry for these connection types is valid, and it must reference an SMB share. Additionally, if a Hyper-V failover cluster is used the SMB share must be the top-level mount point of the cluster shared volume on one of the servers in the cluster (i.e. C:\ClusterStorage).  
In the case of failure, the following errors can result.  
Error Codes  
\---\---\-----  
HostingUnitsPathInvalid  
The path provided is not to an item in a subdirectory of a hosting unit item.  
HostingUnitStoragePathInvalid  
The specified path is invalid.  
HostingUnitStoragePathInvalid  
The storage path cannot be found or is invalid. See notes above about validity.  
HostingUnitStorageDuplicateObjectExists  
The specified storage path is already part of the hosting unit.  
HypervisorInMaintenanceMode  
The hypervisor for the connection is in maintenance mode.  
DatabaseError  
An error occurred in the service while attempting a database operation.  
DatabaseNotConfigured  
The operation could not be completed because the database for the service is not configured.  
DataStoreException  
An error occurred in the service while attempting a database operation. Communication with the database failed for  
various reasons.  
CommunicationError  
An error occurred while communicating with the service.  
PermissionDenied  
The user does not have administrative rights to perform this operation.  
ExceptionThrown  
An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used, or examine the XenDesktop logs.

## Examples

### EXAMPLE 1

    c:\PS>Add-HypHostingUnitStorage -LiteralPath XDHyp:\HostingUnits\MyHostingUnit -StoragePath 'XDHyp:\HostingUnits\MyHostingUnits\newStorage.storage'
    
              HostingUnitUid       : bcd3d649-86d1-4aa8-8ec2-d322b6a2c457
              HostingUnitName      : MyHostingUnit
              HypervisorConnection : MyConnection
              RootPath             : /
              RootId               :
              NetworkPath          : /Network 0.network
              NetworkId            : ab47080b-ca15-771a-c8dc-6ad9650158f1
              Storage              : {/Local storage.storage, /newStorage.storage}
              PersonalvDiskStorage : {/newStorage.storage}
              VMTaggingEnabled     : True
              AdditionalStorage    : {TemporaryStorage}
              Metadata             : {}
    

Description  
\---\---\-----  
The command adds a new storage location called "newStorage.storage" to the hosting unit called "MyHostingUnit".

### EXAMPLE 2

    XDHyp:\HostingUnits\MyHostingUnit>Add-HypHostingUnitStorage -LiteralPath . -StoragePath 'XDHyp:\HostingUnits\MyHostingUnits\newStorage.storage' -StorageType OSStorage
    
              HostingUnitUid       : bcd3d649-86d1-4aa8-8ec2-d322b6a2c457
              HostingUnitName      : MyHostingUnit
              HypervisorConnection : MyConnection
              RootPath             : /
              RootId               :
              NetworkPath          : /Network 0.network
              NetworkId            : ab47080b-ca15-771a-c8dc-6ad9650158f1
              Storage              : {/Local storage.storage, /newStorage.storage}
              PersonalvDiskStorage : {/Local storage.storage}
              VMTaggingEnabled     : True
              AdditionalStorage    : {TemporaryStorage}
              Metadata             : {}
    

Description  
\---\---\-----  
The command adds a new storage location called "newStorage.storage" to the current directory. The dot (.) represents the current location (not its contents).

### EXAMPLE 3

    XDHyp:\HostingUnits\MyHostingUnit>dir *.storage | Add-HypHostingUnitStorage -LiteralPath XDHyp:\HostingUnits\MyHostingUnit
    

Description  
\---\---\-----  
The command adds all of the storage that is available in the hosting unit to the specified hosting unit.

### EXAMPLE 4

    c:\PS>Add-HypHostingUnitStorage -LiteralPath XDHyp:\HostingUnits\MyHostingUnit -StoragePath 'XDHyp:\HostingUnits\MyHostingUnits\newStorage.storage' -StorageType PersonalvDiskStorage
    
              HostingUnitUid       : bcd3d649-86d1-4aa8-8ec2-d322b6a2c457
              HostingUnitName      : MyHostingUnit
              HypervisorConnection : MyConnection
              RootPath             : /
              RootId               :
              NetworkPath          : /Network 0.network
              NetworkId            : ab47080b-ca15-771a-c8dc-6ad9650158f1
              Storage              : {/Local storage.storage}
              PersonalvDiskStorage : {/Local storage.storage, /newStorage.storage}
              VMTaggingEnabled     : True
              AdditionalStorage    : {TemporaryStorage}
              Metadata             : {}
    

Description  
\---\---\-----  
The command adds a new storage location called "newStorage.storage" to the hosting unit called "MyHostingUnit".