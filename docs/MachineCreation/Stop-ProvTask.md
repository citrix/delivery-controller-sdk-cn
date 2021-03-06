# Stop-ProvTask

Stops currently running MachineCreation Service tasks.

## 语法

    Stop-ProvTask [-TaskId] <Guid> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Enables tasks currently running in the MachineCreation Service to be stopped. Once stopped, tasks cannot be restarted.

## 相关命令

- [Get-ProvTask](Get-ProvTask.html)
- [Remove-ProvTask](Remove-ProvTask.html)
- [Switch-ProvTask](Switch-ProvTask.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| TaskId       | Specifies the identifier for the task to be stopped.                                                                                                                   | true  | true (ByPropertyName) |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### System.Management.Automation.PSObject

Objects containing the TaskId parameter can be piped to the Stop-ProvTask command.

## 返回值

### 

## Notes If the command fails, the following errors can result.  
Error Codes  
\---\---\-----  
InvalidWorkflow  
The specified task could not be found.  
InvalidWorkflowHost  
The specified task is executing on a different server.  
DatabaseError  
An error occurred in the service while attempting a database operation.  
DatabaseNotConfigured  
The operation could not be completed because the database for the service is not configured.  
DataStoreException  
An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.  
PermissionDenied  
You do not have permission to execute this command.  
AuthorizationError  
There was a problem communicating with the Citrix Delegated Administration Service.  
ConfigurationLoggingError  
The operation could not be performed because of a configuration logging error.  
CommunicationError  
There was a problem communicating with the remote service.  
DatabaseError  
There was a problem communicating with the database.  
ExceptionThrown  
An unexpected error occurred. 有关更多详细信息，请参阅控制器上的 Windows 事件日志或 XenDesktop 日志。

## 示例

### 示例 1

    c:\PS>Get-ProvTask -active $true | Stop-ProvTask
    Success
    

Description  
\---\---\-----  
Terminate all tasks currently executing on the MachineCreation Service.

### 示例 2

    c:\PS>Stop-ProvTask -TaskId bd52e688-e40d-4790-83de-9f7633481454
    Success
    

Description  
\---\---\-----  
Terminate the named task executing on the MachineCreation Service.