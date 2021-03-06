# New-BrokerSessionPreLaunch

Creates a new session pre-launch setting for a desktop group.

## 语法

    New-BrokerSessionPreLaunch [-DesktopGroupName] <String> [-Enabled <Boolean>] [-MaxAverageLoadThreshold <Int32>] [-MaxLoadPerMachineThreshold <Int32>] [-MaxTimeBeforeDisconnect <TimeSpan>] [-MaxTimeBeforeTerminate <TimeSpan>] [-UserFilterEnabled <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    New-BrokerSessionPreLaunch -DesktopGroupUid <Int32> [-Enabled <Boolean>] [-MaxAverageLoadThreshold <Int32>] [-MaxLoadPerMachineThreshold <Int32>] [-MaxTimeBeforeDisconnect <TimeSpan>] [-MaxTimeBeforeTerminate <TimeSpan>] [-UserFilterEnabled <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The New-BrokerSessionPreLaunch cmdlet is used to define a session pre-launch setting for a desktop group.

Note that each desktop group can only have a single session pre-launch setting. Session pre-launch only applies to application sessions.

## 相关命令

- [Get-BrokerSessionPreLaunch](Get-BrokerSessionPreLaunch.html)
- [Set-BrokerSessionPreLaunch](Set-BrokerSessionPreLaunch.html)
- [Remove-BrokerSessionPreLaunch](Remove-BrokerSessionPreLaunch.html)

## 参数

| 名称                         | 说明                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| -------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| DesktopGroupName           | The name of the desktop group that this pre-launch setting is applied to.                                                                                                                                                                                                                                                                                                                                                                                                   | true  | true (ByPropertyName) |                                                                                        |
| DesktopGroupUid            | The Uid of the desktop group that this pre-launch setting is applied to.                                                                                                                                                                                                                                                                                                                                                                                                    | true  | true (ByPropertyName) |                                                                                        |
| 已启用                        | Boolean that indicates if the new session pre-launch is enabled.                                                                                                                                                                                                                                                                                                                                                                                                            | false | true (ByPropertyName) | true                                                                                   |
| MaxAverageLoadThreshold    | Specifies the average load threshold across the desktop group. When the threshold hits, pre-launched sessions across the group be terminated to reduce load. Sessions that have been pre-launched the longest will be chosen first.                                                                                                                                                                                                                                         | false | true (ByPropertyName) |                                                                                        |
| MaxLoadPerMachineThreshold | Specifies the maximum load threshold per machine in the desktop group. When the threshold hits, pre-launched sessions on each loaded machine will be terminated to reduce load. Sessions that have been pre-launched the longest will be chosen first.                                                                                                                                                                                                                      | false | true (ByPropertyName) |                                                                                        |
| MaxTimeBeforeDisconnect    | Specifies the time by which a pre-launched session will be disconnected. The disconnect timer is optional, but when specified the terminate timer needs to be also set. The disconnect time cannot be greater than the terminate time. When the disconnect and terminate times are the same, the terminate timer takes precedence. The disconnect timer needs to be paired with a session termination condition like the terminate timer or one of load threshold settings. | false | true (ByPropertyName) | 15 分钟                                                                                  |
| MaxTimeBeforeTerminate     | Specifies the time by which a pre-launched session will be terminated. The terminate timer is not optional when timers are configured. When the disconnect and terminate times are the same, the terminate timer takes precedence.                                                                                                                                                                                                                                          | false | true (ByPropertyName) | 8 小时                                                                                   |
| UserFilterEnabled          | Specifies whether the session pre-launch's user filter is enabled or disabled. Where the user filter is enabled, pre-launch is enabled only to users who appear in the filter (either explicitly or by virtue of group membership).                                                                                                                                                                                                                                         | false | true (ByPropertyName) | false                                                                                  |
| LoggingId                  | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                                                                                                                                                             | false | false                 |                                                                                        |
| AdminAddress               | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                                                                                                                                                                                                                                                                          | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Depends on parameter

Parameters can be piped by property name.

## 返回值

### Citrix.Broker.Admin.SDK.SessionPreLaunch

New-BrokerSessionPreLaunch returns a session pre-launch object.

## 示例

### 示例 1

    C:\PS> New-BrokerSessionPreLaunch -DesktopGroupName test -Enabled $true -MaxTimeBeforeDisconnect 0:30 -MaxTimeBeforeTerminate 1:00
    

Description  
\---\---\-----  
Creates a new session pre-launch setting with a disconnect timer of 30 minutes and terminate timer of 1 hour.