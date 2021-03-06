# Get-AppLibScopedObject

Gets the details of the scoped objects for the AppLibrary Service.

## 语法

    Get-AppLibScopedObject [-ScopeId <Guid>] [-ScopeName <String>] [-ObjectType <ScopedObjectType>] [-ObjectId <String>] [-ObjectName <String>] [-Description <String>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

返回直接限定了作用域的对象列表，包括作用域和对象的名称和标识符以及对象描述，以用于显示目的。

每个直接限定了作用域的对象至少一个结果。对象与多个作用域关联时，输出中每个作用域一个结果，因而出现重复的对象详细信息。

对于 All 作用域，不会返回记录，尽管如果对象不在任何作用域中，将返回 ScopeId 和 ScopeName 为空的结果。

## 相关命令

## 参数

| 名称                     | 说明                                                                                            | 是否必需？ | 管道输入                  | 默认值                                   |
| ---------------------- | --------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| ScopeId                | 按给定作用域标识符获取作用域对象条目。                                                                           | false | true (ByPropertyName) |                                       |
| ScopeName              | 按给定作用域名称获取作用域对象条目。                                                                            | false | true (ByPropertyName) |                                       |
| ObjectType             | 获取给定类型对象的作用域对象条目。                                                                             | false | true (ByPropertyName) |                                       |
| ObjectId               | 获取具有指定对象标识符的对象的作用域对象条目。                                                                       | false | true (ByPropertyName) |                                       |
| ObjectName             | 获取具有指定对象标识符的对象的作用域对象条目。                                                                       | false | true (ByPropertyName) |                                       |
| 说明                     | 获取具有指定说明的对象的作用域对象条目。                                                                          | false | false                 |                                       |
| 属性                     | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                        | false | false                 |                                       |
| ReturnTotalRecordCount | 如果指定此项，cmdlet 将输出包含可用记录数的错误记录。 此错误记录是附加信息，并不影响写入输出管道的对象。 请参阅 about_AppLib_Filtering 了解详细信息。 | false | false                 | False                                 |
| MaxRecordCount         | 指定要返回的最大记录数。                                                                                  | false | false                 | 250                                   |
| 跳过                     | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                         | false | false                 |                                       |
| SortBy                 | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。      | false | false                 | 默认排序顺序是按名称或唯一标识符。                     |
| 过滤器                    | 获取与 PowerShell 样式过滤表达式匹配的记录。请参阅 about_AppLib_Filtering 了解详细信息。                              | false | false                 |                                       |
| AdminAddress           | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                    | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.AppLibrary.Sdk.ScopedObject

The Get-AppLibScopedObject command returns an object containing the following properties:  
ScopeId <Guid?>  
指定作用域的唯一标识符。  
ScopeName <string>  
指定作用域的显示名称。  
ObjectType <scopedobjecttype>  
此条目相关的对象的类型。  
ObjectId <string>  
对象的唯一标识符。  
ObjectName <string>  
对象的显示名称  
说明 <string>  
对象的说明（如果对象类型没有说明，可能为 $null）。## 注意 如果命令失败，会返回以下错误。  
错误代码  
\---\---\-----  
UnknownObject  
未找到其中一个指定的对象。  
PartialData  
只返回了一部分可用数据。  
InvalidFilter  
无法为此 cmdlet 解释提供的过滤表达式。  
CouldNotQueryDatabase  
未定义获取数据库所需的查询。  
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
CommunicationError  
与远程服务通信时出现问题。  
ExceptionThrown  
发生意外错误。有关更多详细信息，请参阅控制器上的 Windows 事件日志或 XenDesktop 日志。

## 示例

### 示例 1

    c:\PS>Get-AppLibScopedObject -ObjectType Scheme
    
    ScopeId     : eff6f464-f1ee-4442-add3-99982e0cec01
    ScopeName   : Sales
    ObjectType  : Scheme
    ObjectId    : cd4174ee-9e4b-4e57-b126-9dbf757fe493
    ObjectName  : MyExampleScheme
    Description : Test scheme
    
    ScopeId     : 304e0fa7-d390-47f0-a94f-7e956a324c41
    ScopeName   : Finance
    ObjectType  : Scheme
    ObjectId    : cd4174ee-9e4b-4e57-b126-9dbf757fe493
    ObjectName  : MyExampleScheme
    Description : Test scheme
    
    ScopeId     :
    ScopeName   :
    ObjectType  : Scheme
    ObjectId    : 5062e46b-71bc-4ac9-901a-30fe6797e2f6
    ObjectName  : AnotherScheme
    Description : Another scheme in no scopes
    

说明  
\---\---\-----  
获取类型为 Scheme 的所有作用域对象。 示例输出中显示 Sales 和 Finance 两个作用域中的 scheme 对象 (MyExampleScheme) 以及不在任何作用域中的另一个 scheme (AnotherScheme)。 在最后一个记录中，返回的 ScopeId 值和 ScopeName 值为空。