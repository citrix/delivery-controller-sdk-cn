# Test-BrokerRemotePCAccountNameAvailable

Determine whether the proposed RemotePCAccount OU is available for use.

## 语法

    Test-BrokerRemotePCAccountNameAvailable [-OU] <String[]> [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

This cmdlet checks whether proposed RemotePCAccount OU is available for use. It returns a record for each OU indicating the availability of that OU, with $true indicating that the OU is unused and available for use, or $false if it is not available.

## 相关命令

- [Get-BrokerRemotePCAccount](Get-BrokerRemotePCAccount.html)
- [New-BrokerRemotePCAccount](New-BrokerRemotePCAccount.html)

## 参数

| 名称           | 说明                                                                                                                                                 | 是否必需？ | 管道输入                           | 默认值                                                                                    |
| ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ------------------------------ | -------------------------------------------------------------------------------------- |
| OU           | The RemotePCAccount OU to be tested.                                                                                                               | true  | true (ByValue, ByPropertyName) |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false                          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### System.String

You can pipe a string that contains the OU to test.

## 返回值

### Citrix.Broker.Admin.SDK.NameAvailability

The cmdlet returns a result for each OU specified. An availability of "True" indicates the OU is available for use, and "False" if it is not available.

## 示例

### 示例 1

    C:\PS> Test-BrokerRemotePCAccountNameAvailable -OU Test1
    

Description  
\---\---\-----  
Checks whether the OU "Test1" is available.

### 示例 2

    C:\PS> Test-BrokerRemotePCAccountNameAvailable @("Test1","Test2","Test3")
    

Description  
\---\---\-----  
Checks whether each of the specified names is available.