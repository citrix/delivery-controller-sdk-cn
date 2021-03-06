# Remove-BrokerConfiguredFTA

Deletes one or more configured file type associations.

## 语法

    Remove-BrokerConfiguredFTA [-InputObject] <ConfiguredFTA[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Deletes one or more file type associations configured for a published application. At least one configured file type association object must be specified.

## 相关命令

- [Get-BrokerConfiguredFTA](Get-BrokerConfiguredFTA.html)
- [New-BrokerConfiguredFTA](New-BrokerConfiguredFTA.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入           | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Specifies the ConfiguredFTA objects to delete.                                                                                                                                  | true  | true (ByValue) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.ConfiguredFTA[]

One or more ConfiguredFTA objects can be supplied as input.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> $ftas = Get-BrokerConfiguredFTA -ExtensionName ".txt"
    C:\PS> Remove-BrokerConfiguredFTA $ftas
    

Description  
\---\---\-----  
Deletes all configured file type associations with an extension name of ".txt".