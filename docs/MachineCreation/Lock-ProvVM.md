# Lock-ProvVM

Locks a VM.

## 语法

    Lock-ProvVM [-VMID] <String[]> -ProvisioningSchemeName <String> [-Tag <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Lock-ProvVM [-VMID] <String[]> -ProvisioningSchemeUid <Guid> [-Tag <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Provides the ability to 'lock' a virtual machine with a tag string. This stops other commands from being able to remove the virtual machine without unlocking the VM first. This is to enable consumers of the virtual machines to indicate that the VM is being used.

## 相关命令

- [UnLock-ProvVM](UnLock-ProvVM.html)
- [Get-ProvVM](Get-ProvVM.html)
- [Remove-ProvVM](Remove-ProvVM.html)

## 参数

| 名称                     | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| VMID                   | The virtual machine Id (hypervisor context).                                                                                                                           | true  | true (ByPropertyName) |                                       |
| ProvisioningSchemeName | The name of the provisioning scheme.                                                                                                                                   | true  | true (ByPropertyName) |                                       |
| ProvisioningSchemeUid  | The unique identifier of the provisioning scheme.                                                                                                                      | true  | false                 |                                       |
| 标记                     | The string to be held against the VM being locked.                                                                                                                     | false | false                 |                                       |
| LoggingId              | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress           | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                              | false | false                 | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### Citrix.MachineCreation.Sdk.ProvisionedVirtualMachine  
You can pipe an object containing a parameter called 'VMId' and 'ProvisioningSchemeName' to Lock-ProvVM

## 返回值

### 

## Notes In the case of failure, the following errors can result.  
Error Codes  
\---\---\-----  
VMDoesNotExist  
The specified VM cannot be located.  
VMAlreadyLocked  
The VM is already unlocked.  
VMDoesNotExistForProvisioningScheme  
The specified VM does exist in the hypervisor, but is not part of the specified provisioning scheme.  
PermissionDenied  
The user is not authorized to perform this operation  
ConfigurationLoggingError  
The operation could not be performed because of a configuration logging error  
DatabaseError  
An error occurred in the service while attempting a database operation.  
DatabaseNotConfigured  
The operation could not be completed because the database for the service is not configured.  
ServiceStatusInvalidDb  
An error occurred in the service while attempting a database operation - communication with the database failed for  
for various reasons.  
CommunicationError  
An error occurred while communicating with the service.  
PermissionDenied  
The user does not have administrative rights to perform this operation.  
ExceptionThrown  
An unexpected error occurred. 要查找更多详细信息，请参阅使用的控制器上的 Windows 事件日志，或检查 XenDesktop 日志。

## 示例

### 示例 1

    C:\PS>Lock-ProvVM -provisioningSchemeName MyScheme -VMId  bc79802c-ba6e-8de8-99e9-4c35d7ad24b4 -Tag LockedString
    

Description  
\---\---\-----  
Locks the VM with the Id 'bc79802c-ba6e-8de8-99e9-4c35d7ad24b4' in the provisioning scheme 'MyScheme' with the tag 'LockedString'.

### 示例 2

    C:\PS>Get-ProvVM -provisioningSchemeName MyScheme | Lock-ProvVM -Tag LockedString
    

Description  
\---\---\-----  
Locks all the VMs in the provisioning scheme 'MyScheme' with the tag 'LockedString'.