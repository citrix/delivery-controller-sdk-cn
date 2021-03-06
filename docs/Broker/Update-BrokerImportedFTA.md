# Update-BrokerImportedFTA

Imports or updates all of the file type associations for the specified worker.

## 语法

    Update-BrokerImportedFTA -DesktopUids <Int32[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Imports or updates the file type associations from a specified worker machine.

File type association associates a file extension (such as ".txt") with an application (such as Notepad). In a Citrix environment file type associations on a user device can be configured so that when an user clicks on a document it launches the appropriate published application. This is known as "content redirection".

Imported file type associations are different from configured file type associations. Imported file type associations are lists of known file type associations for a given desktop group. Configured file type associations are those that are actually associated with published applications for the purposes of content redirection.

Initially the system is not aware of any extensions, and they must be imported by the Citrix administrator. To import or update file type associations from a worker machine, two criteria must be met: o The worker machine must not be in use o The worker machine must be in maintenance mode

For more information about putting a worker machine in maintenance mode, see the Set-BrokerPrivateDesktop and Set-BrokerSharedDesktop cmdlets.

Imported file type associations are grouped together based on the desktop group of the machine from which they were imported. All file types for a desktop group are deleted. There is no mechanism for deleting a subset imported file type associations for a specific desktop group.

If file type associations are imported more than once for a desktop group, for example, if this cmdlet is run twice for two workers belonging to the same desktop group, all existing imported file type associations for that desktop group are deleted and imported again.

## 相关命令

- [Get-BrokerImportedFTA](Get-BrokerImportedFTA.html)
- [Remove-BrokerImportedFTA](Remove-BrokerImportedFTA.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| DesktopUids  | Imports or updates the file type associations from the specified desktop. The desktop must belong to a desktop group of the Private or Shared desktop kind.                     | true  | false |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Int32[]

An array of Uids for desktops can be supplied as input.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> $desktop = Get-BrokerSharedDesktop -MachineName "ACME\Worker1"
    C:\PS> Set-BrokerSharedDesktop $desktop -InMaintenanceMode $true
    C:\PS> Update-BrokerImportedFTA -DesktopUids $desktop.Uid
    C:\PS> Set-BrokerSharedDesktop $desktop -InMaintenanceMode $false
    

Description  
\---\---\-----  
Gets an object for the worker machine named "Worker1" in the "ACME" domain, and ensures no users can connect to it, before importing the file type associations from that desktop and re-enabling it.