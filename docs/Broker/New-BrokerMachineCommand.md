# New-BrokerMachineCommand

Creates a new command to deliver to a desktop.

## 语法

    New-BrokerMachineCommand -User <String> -Category <String> -CommandName <String> [-DesktopGroups <DesktopGroup[]>] [-SendTrigger <MachineCommandTrigger>] [-SendDeadline <TimeSpan>] [-CommandData <Byte[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    New-BrokerMachineCommand -MachineUid <Int32> -Category <String> -CommandName <String> [-SendTrigger <MachineCommandTrigger>] [-SendDeadline <TimeSpan>] [-CommandData <Byte[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    New-BrokerMachineCommand -SessionUid <Int64> -Category <String> -CommandName <String> [-SendTrigger <MachineCommandTrigger>] [-SendDeadline <TimeSpan>] [-CommandData <Byte[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    New-BrokerMachineCommand -Synchronous -MachineUid <Int32> -Category <String> -CommandName <String> [-CommandData <Byte[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Create a new command queued for delivery to a desktop. Commands are sent to a specific handler installed on the desktop using the Category parameter. Each handler has its own list of commands identified by the CommandName parameter. Optional command data can be provided using the CommandData parameter in a format specified by the handler.

Commands are targeted at a specific user, session or machine. Commands targeted at a user can be further be restricted to one or more desktop groups.

The SendTrigger is used to restrict the command to a specific event related to the target. For example, when the target machine registers or when the target user reconnects to a session. The command will be sent to the machine when the SendTrigger occurs for the target.

If the Synchronous switch is provided, the target must be a machine and no SendTrigger can be specified. The command is sent immediately to the machine if it is currently registered and fails if the machine is not registered.

Note that the combined length of the Category and CommandName is limited to 64 characters. The Category and CommandName must both be entirely alphanumeric and not include any white space.

## 相关命令

- [Get-BrokerMachineCommand](Get-BrokerMachineCommand.html)
- [Remove-BrokerMachineCommand](Remove-BrokerMachineCommand.html)

## 参数

| 名称            | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                                   |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ----------------------------------------------------------------------------------------------------- |
| 类别            | The service on the desktop to send the command to.                                                                                                                              | true  | true (ByPropertyName) |                                                                                                       |
| CommandName   | The name of the command to send (as defined by the service).                                                                                                                    | true  | true (ByPropertyName) |                                                                                                       |
| 用户            | User whose desktop or session should receive the command.                                                                                                                       | true  | true (ByPropertyName) | Any user.                                                                                             |
| MachineUid    | Specific machine that should receive the command.                                                                                                                               | true  | true (ByPropertyName) |                                                                                                       |
| SessionUid    | Currently logged on user session that should receive the command.                                                                                                               | true  | true (ByPropertyName) | Any session.                                                                                          |
| Synchronous   | Send the command immediately and block while waiting for the reply.                                                                                                             | true  | false                 | false                                                                                                 |
| CommandData   | Optional additional data to include with the command.                                                                                                                           | false | true (ByPropertyName) | 无                                                                                                     |
| LoggingId     | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                                       |
| AdminAddress  | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default.                |
| DesktopGroups | Further restrict the command targeted at a user to machines in these desktop groups.                                                                                            | false | true (ByPropertyName) | No restriction by desktop group.                                                                      |
| SendTrigger   | Queue command for delivery until this particular event occurs. Valid values are NextContact, Broker, LogOn, Logoff, Disconnect and Reconnect.                                   | false | true (ByPropertyName) | Default value is 'NextContact' so the command is sent during the next communication with the desktop. |
| SendDeadline  | Automatically cancel the command if it not delivered before the specified time span passes.                                                                                     | false | true (ByPropertyName) | Command expires after 24 hours.                                                                       |

## 输入类型

### 无

No parameter is accepted from the input pipeline.

## 返回值

### Citrix.Broker.Admin.SDK.MachineCommand

New command that was added to the command queue.### Citrix.Broker.Admin.SDK.MachineSynchronousCommandResponse When the Synchronous option is used, the command is immediately sent to the specified machine and processed. The SDK object returned describes the command and the result of this command processing.## Notes Commands are subject to delegated administration restrictions based on the desktop group, category and command name.

## 示例

### 示例 1

    New-BrokerMachineCommand -Category UserProfileManager -CommandName "ResetUpmProfile" -DesktopGroups 1 -CommandData $byteArray -SendTrigger logon -user domain1\user1
    

Description  
\---\---\-----  
Instruct the User Profile Manager service to execute the "ResetUpmProfile" command using the encoded $byteArray command data when user domain1\user1 logs on to any machine in desktop group 1

### 示例 2

    New-BrokerMachineCommand -Synchronous -Category "MonitorService" -CommandName "EnableLogging" -MachineUid 13
    

Description  
\---\---\-----  
Instruct the monitor service to immediately execute the "EnableLogging" command on the machine having Uid 13.