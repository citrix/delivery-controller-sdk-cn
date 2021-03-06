# New-AppLibAppDisk

Creates a new AppDisk.

## 语法

    New-AppLibAppDisk [-AppDiskName] <String> -HostingUnitName <String> -DiskSizeMB <Int32> -PreparationMachine <String> [-Scope <String[]>] [-AppDiskDescription <String>] [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    New-AppLibAppDisk [-AppDiskName] <String> -HostingUnitUid <Guid> -DiskSizeMB <Int32> -PreparationMachine <String> [-Scope <String[]>] [-AppDiskDescription <String>] [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    New-AppLibAppDisk [-AppDiskName] <String> -SourceAppDiskUid <Guid> -PreparationMachine <String> [-AppDiskDescription <String>] [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    New-AppLibAppDisk [-AppDiskName] <String> -SourceAppDiskName <String> -PreparationMachine <String> [-AppDiskDescription <String>] [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Lets you create a new AppDisk.

## 相关命令

- [Get-AppLibTask](Get-AppLibTask.html)
- [Get-AppLibAppDisk](Get-AppLibAppDisk.html)
- [Import-AppLibAppDisk](Import-AppLibAppDisk.html)
- [Test-AppLibAppDiskNameAvailable](Test-AppLibAppDiskNameAvailable.html)

## 参数

| 名称                 | 说明                                                                                                                                                                                                              | 是否必需？   | 管道输入  | 默认值                                   |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- | ----- | ------------------------------------- |
| AppDiskName        | The name of the AppDisk to be created. This must be a name that is not being used by an existing AppDisk, and it must not contain any of the following characters \/;:#.*?=<>                                  | []()""' | true  | false |                               |
| PreparationMachine | The SID of the machine to use as the preparation machine for this operation. The machine must be within a valid Machine Catalog.                                                                                | true    | false |                                       |
| HostingUnitName    | The name of the hosting unit used for the AppDisk.                                                                                                                                                              | true    | false |                                       |
| DiskSizeMB         | How large the AppDisk should be, in megabytes.                                                                                                                                                                  | true    | false |                                       |
| HostingUnitUid     | The identifier for the hosting unit used for the AppDisk.                                                                                                                                                       | true    | false |                                       |
| SourceAppDiskUid   | Identifies an AppDisk to be used as a basis for this one.                                                                                                                                                       | true    | false |                                       |
| SourceAppDiskName  | Identifies an AppDisk to be used as a basis for this one.                                                                                                                                                       | true    | false |                                       |
| AppDiskDescription | The description of the AppDisk.                                                                                                                                                                                 | false   | false |                                       |
| RunAsynchronously  | Indicates whether or not the command returns before it is complete. If specified, the command returns an identifier for the task that was created. This task can be monitored using the Get-AppLibTask command. | false   | false | false                                 |
| PurgeJobOnSuccess  | Indicates that the task history is removed from the database when the task has finished. This can only be specified for tasks that are not run asynchronously.                                                  | false   | false |                                       |
| LoggingId          | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                          | false   | false |                                       |
| AdminAddress       | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                                                                      | false   | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |
| 作用域                | The administration scopes to be applied to the new AppDisk.                                                                                                                                                     | false   | false |                                       |

## 输入类型

### 

## 返回值

### System.Guid

When the RunAsynchronously identifier is specified, this GUID is returned and provides the task identifier### System.Management.Automation.PSCustomObject System.Management.Automation.PSCustomObject This object provides details of the task that was run and contains the following information:  
TaskId <guid> The identifier for the task that was performed. Active <boolean> Indicates whether the task is still processing or is complete. Host <string> The name of the host on which the task is running or was run. DateStarted <datetime> The date and time that the task was initiated. LastUpdateTime <datetime> The date and time of the last task status update DateFinished <datetime> The date and time that the task finished execution Metadata <Metadata[]> Associated key-value data TaskState <string> Where in its lifecycle the task is CurrentOperation <string> Operation specific phase of the overall "Running" task state. TerminatingError < Citrix.Fma.Sdk.ServiceCore.CommonCmdlets.TaskterminatingError> Diagnostic information in the case of a complete task failure ActiveElapsedTime <int> How many seconds of active execution the task has taken Type <string> The type of task. For this cmdlet's tasks, this is always NewAppDisk. AppDiskName <string> The name of the AppDisk that the task was for. AppDiskUid <string> The identifier of the AppDisk that the task was for. Scopes <Citrix.Fma.Sdk.ServiceCoreScopeReference[]> The delegated administration scopes to which the AppDisk will belong. TaskStateInformation <string> Additional information about the current task state. TaskProgress <double> The progress of the task 0-100%. DiskSizeMB <int> The size of the AppDisk DiskLocalUid <guid> The identifier of the AppDisk lineage. DiskLocalVersion <guid> The identifier of the AppDisk within its lineage. RemoteTaskId <guid> The identifier of the associated disk management task on the Machine Creation Service HostingUnitName <string> The name of the associated hosting unit HostingUnitUid <guid> The indentifier of the associated hosting unit VirtualDiskId <guid> The identifier of the AppDisk stack ReservedMachineSid <string> Security identifier of the VM being used to perform the operation## Notes Only one long-running task for each AppDisk can be processed at a time.  
In case of failure, the following errors can result.  
错误代码  
\---\---\-----  
JobCreationFailed  
The requested task could not be started.  
DatabaseError  
尝试执行数据库操作时，服务发生错误。  
DatabaseNotConfigured  
由于未配置用于服务的数据库，无法完成操作。  
ServiceStatusInvalidDb  
An error occurred in the service while attempting a database operation. Communication with the database failed  
各种原因，无法与数据库通信。  
CommunicationError  
与服务通信时发生错误。  
InvalidParameterCombination  
Both PurgeJobOnSuccess and RunAsynchronously were specified. When running asynchronously, the cmdlet terminates before the job does, so it cannot clean up the completed job.  
PermissionDenied  
用户没有执行此操作的管理权限。  
ConfigurationLoggingError  
The operation could not be performed because of a configuration logging error.  
ScopeNotFound  
One or more of the scopes nominated for the new AppDisk do not exist.  
ExceptionThrown  
The cmdlet is associated with a task of type NewAppDisk, and while active will move through the following operations (CurrentOperation field)  
ValidatingInputs  
ConsolidatingMasterImage  
PreparingMasterImage  
ReplicatingMasterImage  
CommittingScheme

## 示例

### 示例 1

    C:\PS> New-AppLibAppDisk -AppDiskName MyAppDisk -HostingUnitName XenHu -DiskSizeMB 16384 -PreparationMachine S-1-5-21-2316621082-1546847349-2782505528-1165
    
              TaskId                              : 90e93b9d-a225-4701-ad50-fa1546af35ac
              AppDiskName                         : MyAppDisk
              AppDiskUid                          : d9ba6487-05f8-48ad-a178-1794605e2b8e
              Active                              : False
              DiskSizeMB                          : 16384
              DiskLocalUid                        : 7b4c01c4-72fa-4c80-913d-c6df785f4297
              DiskLocalVersion                    : 25118c6e-a737-4fb9-b4b3-121910a73160
              DateStarted                         : 17/11/2015 08:22:22
              LastUpdateTime                      : 17/11/2015 09:10:18
              DateFinished                        : 17/11/2015 09:10:18
              Type                                : NewAppDisk
              Metadata                            : {}
              TaskState                           : Finished
              TaskStateInformation                :
              TaskProgress                        : 100
              TerminatingError                    :
              RemoteTaskId                        : d2127904-a149-4dce-ae82-f9671a53f6fd
              HostingUnitName                     : XenHU
              HostingUnitUid                      : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501
              Host                                : MyHost
              VirtualDiskId                       : 7ce3c9a5-2888-45ba-8629-398f9e4eba7d
              CurrentOperation                    :
              ActiveElapsedTime                   : 2786
              ReservedMachineSid                  : S-1-5-21-2316621082-1546847349-2782505528-1165
    

Description  
\---\---\-----  
Creates a new 16Gb AppDisk with the name "MyAppDisk" using the hosting unit "XenHu", using the preparation machine "S-1-5-21-2316621082-1546847349-2782505528-1165".

### 示例 2

    C:\PS> New-AppLibAppDisk -AppDiskName MyUpdatedAppDisk -AppDiskDescription "Includes new applications" -SourceAppDisk MyAppDisk -PreparationMachine S-1-5-21-2316621082-1546847349-2782505528-1165 -RunAsynchronously
    
              Guid
              ----
              6dd85fec-96cf-46b1-9cd4-d8ba7d06e85b
    

说明  
\---\---\-----  
Asynchronously creates a new AppDisk "MyUpdatedAppDisk" from "MyAppDisk", using the preparation machine "S-1-5-21-2316621082-1546847349-2782505528-1165". To get the task details, use Get-AppLibTask -TaskID <task id>  
i.e.  
C:\PS>Get-AppLibTask -TaskID 6dd85fec-96cf-46b1-9cd4-d8ba7d06e85b  
TaskId : 6dd85fec-96cf-46b1-9cd4-d8ba7d06e85b AppDiskName : MyUpdatedAppDisk AppDiskUid : 3b9c6b62-be1e-467b-9cb4-025ad9cba916 Active : False DiskSizeMB : DiskLocalUid : 7b4c01c4-72fa-4c80-913d-c6df785f4297 DiskLocalVersion : a23f8bae-dedf-433f-8908-025144ff4f81 DateStarted : 23/11/2015 12:09:53 LastUpdateTime : 23/11/2015 13:01:26 DateFinished : 23/11/2015 13:01:26 Type : NewAppDisk Metadata : {} TaskState : Finished TaskStateInformation : TaskProgress : 100 TerminatingError : RemoteTaskId : 0ab9e8ed-1ded-4831-80c3-9cf84e752528 HostingUnitName : XenHU HostingUnitUid : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501 Host : MyHost VirtualDiskId : 4c245ff7-5cdd-4aac-a854-1e101e23d1f6 CurrentOperation : ActiveElapsedTime : 3079 ReservedMachineSid : S-1-5-21-2316621082-1546847349-2782505528-1165