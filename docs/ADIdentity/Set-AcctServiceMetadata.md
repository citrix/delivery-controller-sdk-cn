# Set-AcctServiceMetadata

在给定服务上添加或更新元数据。

## 语法

    Set-AcctServiceMetadata [-ServiceHostId] <Guid> -Name <String> -Value <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-AcctServiceMetadata [-ServiceHostId] <Guid> -Map <PSObject> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-AcctServiceMetadata [-InputObject] <Service[]> -Name <String> -Value <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-AcctServiceMetadata [-InputObject] <Service[]> -Map <PSObject> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

用于针对给定服务对象存储额外的自定义数据。

## 相关命令

- [Remove-AcctServiceMetadata](Remove-AcctServiceMetadata.html)

## 参数

| 名称            | 说明                                                                                                                                                                     | 是否必需？  | 管道输入                           | 默认值                                   |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------ | ------------------------------ | ------------------------------------- |
| ServiceHostId | 服务的 ID                                                                                                                                                                 | true   | true (ByValue, ByPropertyName) |                                       |
| InputObject   | 元数据要添加到的对象。                                                                                                                                                            | true   | true (ByValue)                 |                                       |
| Name          | 指定要添加的元数据的属性名称。对于指定的服务，该属性必须唯一。该属性不能包含以下任意字符：\/;:#.*?=<>                                                                                                              | []()"' | true                           | false |                               |
| Value         | 指定属性的值。                                                                                                                                                                | true   | false                          |                                       |
| Map           | 指定属性的（名称，值）对字典。 可以是哈希表（使用 @{"name1" = "val1"; "name2" = "val2"} 创建）或字符串字典（使用 new-object“System.Collections.Generic.Dictionary[String,String]”创建）。                      | true   | true (ByValue)                 |                                       |
| LoggingId     | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false  | false                          |                                       |
| AdminAddress  | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false  | false                          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### System.Collections.Generic.Dictionary[String,String]  
Set-AcctServiceMetadata 返回包含新（名称，值）对的字典。  
Key <string>  
指定属性的名称。  
Value <string>  
指定属性的值。

## 注意 如果命令失败，会返回以下错误。  
错误代码  
\---\---\-----  
InvalidParameterCombination  
cmdlet 参数不一致。  
UnknownObject  
未找到其中一个指定的对象。  
DatabaseError  
尝试执行数据库操作时，服务发生错误。  
DatabaseNotConfigured  
由于未配置用于服务的数据库，无法完成操作。  
DataStoreException  
尝试执行数据库操作时，服务发生错误 - 由于各种原因，无法与数据库通信。  
PermissionDenied  
您没有执行此命令的权限。  
AuthorizationError  
与 Citrix Delegated Administration Service 通信时出现问题。  
ConfigurationLoggingError  
由于配置日志记录错误，无法执行操作。  
CommunicationError  
与远程服务通信时出现问题。  
ExceptionThrown  
发生意外错误。 有关更多详细信息，请参阅控制器上的 Windows 事件日志或 XenDesktop 日志。

## 示例

### 示例 1

    c:\PS>Set-AcctServiceMetadata -ServiceHostId 4CECC26E-48E1-423F-A1F0-2A06DDD0805C -Name property -Value value
    
              Key                                       Value
              ---                                       -----
              property                                  value
    

说明  
\---\---\-----  
将名称为“property” 且值为“value”的元数据添加到标识符为“4CECC26E-48E1-423F-A1F0-2A06DDD0805C”的服务。