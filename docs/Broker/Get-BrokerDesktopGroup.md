# Get-BrokerDesktopGroup

Gets broker desktop groups configured for this site.

## 语法

    Get-BrokerDesktopGroup [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerDesktopGroup [[-Name] <String>] [-AppDisk <Guid>] [-AppDnaAnalysisState <AppDnaAnalysisState>] [-AppDnaCompatibility <AppDnaCompatibility>] [-AutomaticPowerOnForAssigned <Boolean>] [-AutomaticPowerOnForAssignedDuringPeak <Boolean>] [-ColorDepth <ColorDepth>] [-DeliveryType <DeliveryType>] [-Description <String>] [-DesktopKind <DesktopKind>] [-Enabled <Boolean>] [-InMaintenanceMode <Boolean>] [-IsRemotePC <Boolean>] [-Metadata <String>] [-MinimumFunctionalLevel <FunctionalLevel>] [-OffPeakBufferSizePercent <Int32>] [-OffPeakDisconnectAction <SessionChangeHostingAction>] [-OffPeakDisconnectTimeout <Int32>] [-OffPeakExtendedDisconnectAction <SessionChangeHostingAction>] [-OffPeakExtendedDisconnectTimeout <Int32>] [-OffPeakLogOffAction <SessionChangeHostingAction>] [-OffPeakLogOffTimeout <Int32>] [-PeakBufferSizePercent <Int32>] [-PeakDisconnectAction <SessionChangeHostingAction>] [-PeakDisconnectTimeout <Int32>] [-PeakExtendedDisconnectAction <SessionChangeHostingAction>] [-PeakExtendedDisconnectTimeout <Int32>] [-PeakLogOffAction <SessionChangeHostingAction>] [-PeakLogOffTimeout <Int32>] [-PublishedName <String>] [-ScopeId <Guid>] [-ScopeName <String>] [-SecureIcaRequired <Boolean>] [-SessionSupport <SessionSupport>] [-SettlementPeriodBeforeAutoShutdown <TimeSpan>] [-SettlementPeriodBeforeUse <TimeSpan>] [-ShutdownDesktopsAfterUse <Boolean>] [-Tag <String>] [-TenantId <Guid>] [-TimeZone <String>] [-TotalApplicationGroups <Int32>] [-TotalApplications <Int32>] [-TurnOnAddedMachine <Boolean>] [-UUID <Guid>] [-ZonePreference <ZonePreference>] [-ApplicationGroupUid <Int32>] [-ApplicationUid <Int32>] [-TagUid <Int32>] [-PowerTimeSchemeUid <Int32>] [-MachineConfigurationUid <Int32>] [-RemotePCCatalogUid <Int32>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Retrieve desktop groups matching the specified criteria. If no parameters are specified this cmdlet enumerates all desktop groups.

Desktop groups represent groups of desktops that are managed together for brokering purposes.

\---\---\---\---\---\---\---\----- BrokerDesktopGroup Object A desktop group object represents a collection of machines that are fully configured in a site that is able to run either a Microsoft Windows desktop environment, individual applications, or both.

    -- AppDisks (System.Guid[])
       The Application Disks used by machines in the desktop group.
    
    -- AppDnaAnalysisState (Citrix.Broker.Admin.SDK.AppDnaAnalysisState?)
       Specifies the current state of AppDNA Analysis on the desktop group
    
    -- AppDnaCompatibility (Citrix.Broker.Admin.SDK.AppDnaCompatibility?)
       The compatibility with the application disks attached to the desktop group
    
    -- AutomaticPowerOnForAssigned (System.Boolean)
       Specifies whether assigned desktops in the desktop group are automatically started at the start of peak time periods. Only relevant for groups whose DesktopKind is Private.
    
    -- AutomaticPowerOnForAssignedDuringPeak (System.Boolean)
       Specifies whether assigned desktops in the desktop are automatically started throughout peak time periods. Only relevant for groups whose DesktopKind is Private and which have AutomaticPowerOnForAssigned set to true.
    
    -- ColorDepth (Citrix.Broker.Admin.SDK.ColorDepth)
       Default color depth of sessions started with machines in the desktop group. Possible values are:
       FourBit, EightBit, SixteenBit, TwentyFourBit.
    
    -- ConfigurationSlotUids (System.Int32[])
       Uids of any configuration slots which hold machine configurations associated with the desktop group. The order of slot UIDs in this list correspond with the order of items in the associated MachineConfigurationNames and MachineConfigurationUids list properties, and so the same slot UID can appear more than once.
    
    -- DeliveryType (Citrix.Broker.Admin.SDK.DeliveryType)
       The type of resources being published. Possible values are:
       DesktopsOnly, AppsOnly, DesktopsAndApps.
    
    -- Description (System.String)
       Description of the desktop group.
    
    -- DesktopKind (Citrix.Broker.Admin.SDK.DesktopKind)
       The kind of the desktops being published, possible values are:
       Private and Shared.
    
    -- DesktopsAvailable (System.Int32)
       The number of machines in the desktop group in state Available; this is the number of machines with no sessions present.
    
    -- DesktopsDisconnected (System.Int32)
       The number of disconnected sessions present on machines in the desktop group.
    
    -- DesktopsFaulted (System.Int32)
       The number of machines in the desktop group whose FaultState is not None.
    
    -- DesktopsInUse (System.Int32)
       The number of machines in the desktop group in state InUse; this is the number of machines with at least one session present.
    
    -- DesktopsNeverRegistered (System.Int32)
       The number of machines in the desktop group that have never registered with the current site.
    
    -- DesktopsPreparing (System.Int32)
       The number of machines in the desktop group whose PvD disk image is being prepared.
    
    -- DesktopsUnregistered (System.Int32)
       The number of machines in the desktop group that are currently unregistered.
    
    -- Enabled (System.Boolean)
       Specifies whether the desktop group is enabled or not; disabled desktop groups do not appear to users.
    
    -- IconUid (System.Int32)
       The Uid of the icon to be used as a default for desktops in the desktop group. Individual desktop objects can override this default by setting the IconUid parameter on the desktop object.
    
    -- InMaintenanceMode (System.Boolean)
       Specifies whether the machines in the desktop group are in maintenance mode or not.
    
    -- IsRemotePC (System.Boolean)
       Specifies whether the desktop group is a Remote PC desktop group.
    
    -- MachineConfigurationNames (System.String[])
       The MachineConfiguration names associated with the desktop group.
    
    -- MachineConfigurationUids (System.Int32[])
       The MachineConfiguration uids associated with the desktop group.
    
    -- MetadataMap (System.Collections.Generic.Dictionary<string, string>)
       Metadata associated with the desktop group.
    
    -- MinimumFunctionalLevel (Citrix.Broker.Admin.SDK.FunctionalLevel)
       The minimum FunctionalLevel required for the machines in the desktop group to be able to register with the Citrix Broker Service.
    
    -- Name (System.String)
       Name of the desktop group.
    
    -- OffPeakBufferSizePercent (System.Int32)
       The percentage of machines that are kept available in an idle state outside peak hours.
    
    -- OffPeakDisconnectAction (Citrix.Broker.Admin.SDK.SessionChangeHostingAction)
       The action that is performed after a configurable period of a user session disconnecting outside peak hours. Possible values are Nothing, Suspend or Shutdown.
    
    -- OffPeakDisconnectTimeout (System.Int32)
       The number of minutes before the configured action is performed after a user session disconnects outside peak hours.
    
    -- OffPeakExtendedDisconnectAction (Citrix.Broker.Admin.SDK.SessionChangeHostingAction)
       The action performed after a second configurable period of a user session disconnecting outside peak hours. Possible values are Nothing, Suspend, or Shutdown.
    
    -- OffPeakExtendedDisconnectTimeout (System.Int32)
       The number of minutes before the second configured action is performed after a user session disconnects outside peak hours.
    
    -- OffPeakLogOffAction (Citrix.Broker.Admin.SDK.SessionChangeHostingAction)
       The action performed after a configurable period of a user session ending outside peak hours. Possible values are Nothing, Suspend, or Shutdown.
    
    -- OffPeakLogOffTimeout (System.Int32)
       The number of minutes before the configured action is performed after a user session ends outside peak hours.
    
    -- PeakBufferSizePercent (System.Int32)
       The percentage of machines in the desktop group that are kept available in an idle state in peak hours.
    
    -- PeakDisconnectAction (Citrix.Broker.Admin.SDK.SessionChangeHostingAction)
       The action performed after a configurable period of a user session disconnecting in peak hours. Possible values are Nothing, Suspend, or Shutdown.
    
    -- PeakDisconnectTimeout (System.Int32)
       The number of minutes before the configured action is performed after a user session disconnects in peak hours.
    
    -- PeakExtendedDisconnectAction (Citrix.Broker.Admin.SDK.SessionChangeHostingAction)
       The action performed after a second configurable period of a user session disconnecting in peak hours. Possible values are Nothing, Suspend, or Shutdown.
    
    -- PeakExtendedDisconnectTimeout (System.Int32)
       The number of minutes before the second configured action is performed after a user session disconnects in peak hours.
    
    -- PeakLogOffAction (Citrix.Broker.Admin.SDK.SessionChangeHostingAction)
       The action performed after a configurable period of a user session ending in peak hours. Possible values are Nothing, Suspend, or Shutdown.
    
    -- PeakLogOffTimeout (System.Int32)
       The number of minutes before the configured action is performed after a user session ends in peak hours.
    
    -- ProtocolPriority (System.String[])
       A list of protocol names in the order in which they are attempted for use during connection.
    
    -- PublishedName (System.String)
       The name of the desktop group as it is to appear to the user in StoreFront.
    
    -- Scopes (Citrix.Broker.Admin.SDK.ScopeReference[])
       The list of the delegated admin scopes to which the desktop group belongs.
    
    -- SecureIcaRequired (System.Boolean)
       Flag that specifies if the SecureICA encryption of the HDX protocol is required for sessions of desktops in the desktop group.
    
    -- Sessions (System.Int32)
       The total number of user sessions currently running on all of the machines in the desktop group.
    
    -- SessionSupport (Citrix.Broker.Admin.SDK.SessionSupport)
       Specifies the session support (single/multi) of the machines in the desktop group. Machines with the incorrect session support for the desktop group will be unable to register with the Citrix Broker Service.
    
    -- SettlementPeriodBeforeAutoShutdown (System.TimeSpan)
       Time after a session ends during which automatic shutdown requests (for example, shutdown after use, idle pool management) are deferred. Any outstanding shutdown request takes effect after the settlement period expires. This is typically used to configure time to allow logoff scripts to complete.
    
    -- SettlementPeriodBeforeUse (System.TimeSpan)
       Idle period before a machine can be selected to host a new session after registration or the end of a previous session. This is typically used to allow a machine to become idle following processing associated with start-up or logoff actions. A machine may still be selected during the idle period if no other machine is available for immediate use.
    
    -- ShutdownDesktopsAfterUse (System.Boolean)
       Specifies if the desktops will shut down after they have been used and there are no sessions running on the machine. The machines will not shut down if they are placed into maintenance mode, even if this flag is set to $true. The machines, however, will shutdown after the machine is taken out of maintenance mode if the flag is still set.
    
    -- Tags (System.String[])
       Tags associated with the desktop group.
    
    -- TenantId (System.Guid?)
       Identity of tenant associated with desktop group. Not applicable (always blank) in non-multitenant sites.
    
    -- TimeZone (System.String)
       The timezone that desktops in the desktop group are in (for power policy purposes).
    
    -- TotalApplicationGroups (System.Int32)
       Total number of application groups associated with the desktop group.
    
    -- TotalApplications (System.Int32)
       Total number of applications associated with the desktop group.
    
    -- TotalDesktops (System.Int32)
       Total number of machines in the desktop group.
    
    -- TurnOnAddedMachine (System.Boolean)
       Specifies whether the broker should attempt to turn on power-managed machines when they are added to the desktop group.
    
    -- Uid (System.Int32)
       Uid of the desktop group.
    
    -- UUID (System.Guid)
       UUID of the desktop group.
    
    -- ZonePreferences (Citrix.Broker.Admin.SDK.ZonePreference[])
       Ordered list of zone preferences taken into account when launching resources from this desktop group. Possible values for each preference are UserLocation, UserHome, UserHomeOnly and ApplilcationHome.
    

## 相关命令

- [New-BrokerDesktopGroup](New-BrokerDesktopGroup.html)
- [Set-BrokerDesktopGroup](Set-BrokerDesktopGroup.html)
- [Rename-BrokerDesktopGroup](Rename-BrokerDesktopGroup.html)
- [Remove-BrokerDesktopGroup](Remove-BrokerDesktopGroup.html)
- [Add-BrokerUser](Add-BrokerUser.html)
- [Add-BrokerTag](Add-BrokerTag.html)

## 参数

| 名称                                    | 说明                                                                                                                                                                                | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| UID                                   | Gets desktop groups with the specified value of Uid.                                                                                                                              | true  | false |                                                                                        |
| 名称                                    | Gets desktop groups whose name matches the supplied pattern.                                                                                                                      | false | false |                                                                                        |
| AppDisk                               | Gets only desktop groups using the specified application disk.                                                                                                                    | false | false |                                                                                        |
| AppDnaAnalysisState                   | Gets only desktop groups with specified value of AppDnaAnalysisState                                                                                                              | false | false |                                                                                        |
| AppDnaCompatibility                   | Gets only desktop groups with specified value of AppDnaCompatibility                                                                                                              | false | false |                                                                                        |
| AutomaticPowerOnForAssigned           | Gets only desktop groups with the specified value of AutomaticPowerOnForAssigned.                                                                                                 | false | false |                                                                                        |
| AutomaticPowerOnForAssignedDuringPeak | Gets only desktop groups with the specified value of AutomaticPowerOnForAssignedDuringPeak.                                                                                       | false | false |                                                                                        |
| ColorDepth                            | Gets only desktop groups with the specified color depth.  
Valid values are FourBit, EightBit, SixteenBit, and TwentyFourBit.                                                     | false | false |                                                                                        |
| DeliveryType                          | Gets desktop groups according to their delivery type.  
Valid values are DesktopsOnly, AppsOnly and DesktopsAndApps.                                                              | false | false |                                                                                        |
| 说明                                    | Gets desktop groups whose description matches the supplied pattern.                                                                                                               | false | false |                                                                                        |
| DesktopKind                           | Gets desktops of a particular kind.  
Valid values are Private and Shared.                                                                                                        | false | false |                                                                                        |
| 已启用                                   | Gets desktop groups with the specified value of Enabled.                                                                                                                          | false | false |                                                                                        |
| 处于维护模式                                | Gets desktop groups with the specified value of InMaintenanceMode.                                                                                                                | false | false |                                                                                        |
| IsRemotePC                            | Gets desktop groups with the specified IsRemotePC value.                                                                                                                          | false | false |                                                                                        |
| 元数据                                   | 获取具有匹配的元数据条目的记录。  
比较的值由键名、冒号和值组成。 例如：-Metadata "abc:x*" 匹配具有键名为“abc”且值以字母“x”开头的元数据条目的记录。                                                                                         | false | false |                                                                                        |
| MinimumFunctionalLevel                | Gets desktop groups with a specific MinimumFunctionalLevel.  
Valid values are L5, L7, L7_6                                                                                       | false | false |                                                                                        |
| OffPeakBufferSizePercent              | Gets desktop groups with the specified value of OffPeakBufferSizePercent.                                                                                                         | false | false |                                                                                        |
| OffPeakDisconnectAction               | Gets desktop groups with the specified value of OffPeakDisconnectAction.                                                                                                          | false | false |                                                                                        |
| OffPeakDisconnectTimeout              | Gets desktop groups with the specified value of OffPeakDisconnectTimeout.                                                                                                         | false | false |                                                                                        |
| OffPeakExtendedDisconnectAction       | Gets desktop groups with the specified value of OffPeakExtendedDisconnectAction.                                                                                                  | false | false |                                                                                        |
| OffPeakExtendedDisconnectTimeout      | Gets desktop groups with the specified value of OffPeakExtendedDisconnectTimeout.                                                                                                 | false | false |                                                                                        |
| OffPeakLogOffAction                   | Gets desktop groups with the specified value of OffPeakLogOffAction.                                                                                                              | false | false |                                                                                        |
| OffPeakLogOffTimeout                  | Gets desktop groups with the specified value of OffPeakLogOffTimeout.                                                                                                             | false | false |                                                                                        |
| PeakBufferSizePercent                 | Gets desktop groups with the specified value of PeakBufferSizePercent.                                                                                                            | false | false |                                                                                        |
| PeakDisconnectAction                  | Gets desktop groups with the specified value of PeakDisconnectAction.                                                                                                             | false | false |                                                                                        |
| PeakDisconnectTimeout                 | Gets desktop groups with the specified value of PeakDisconnectTimeout.                                                                                                            | false | false |                                                                                        |
| PeakExtendedDisconnectAction          | Gets desktop groups with the specified value of PeakExtendedDisconnectAction.                                                                                                     | false | false |                                                                                        |
| PeakExtendedDisconnectTimeout         | Gets desktop groups with the specified value of PeakExtendedDisconnectTimeout.                                                                                                    | false | false |                                                                                        |
| PeakLogOffAction                      | Gets desktop groups with the specified value of PeakLogOffAction.                                                                                                                 | false | false |                                                                                        |
| PeakLogOffTimeout                     | Gets desktop groups with the specified value of PeakLogOffTimeout.                                                                                                                | false | false |                                                                                        |
| PublishedName                         | Gets desktop groups whose published name matches the supplied pattern.                                                                                                            | false | false |                                                                                        |
| ScopeId                               | Gets desktop groups that are associated with the given scope identifier.                                                                                                          | false | false |                                                                                        |
| ScopeName                             | Gets desktop groups that are associated with the given scope name.                                                                                                                | false | false |                                                                                        |
| SecureIcaRequired                     | Gets desktop groups with the specified value of SecureIcaRequired.                                                                                                                | false | false |                                                                                        |
| SessionSupport                        | Gets desktop groups that have the specified session capability. Values can be:  
o SingleSession - Single-session only machine.  
o MultiSession - Multi-session capable machine. | false | false |                                                                                        |
| SettlementPeriodBeforeAutoShutdown    | Gets desktop groups with the specified value of SettlementPeriodBeforeAutoShutdown.                                                                                               | false | false |                                                                                        |
| SettlementPeriodBeforeUse             | Gets desktop groups with the specified value of SettlementPeriodBeforeUse.                                                                                                        | false | false |                                                                                        |
| ShutdownDesktopsAfterUse              | Gets desktop groups with the specified value of ShutdownDesktopsAfterUse.                                                                                                         | false | false |                                                                                        |
| 标记                                    | Gets desktop groups tagged with the specified tag.                                                                                                                                | false | false |                                                                                        |
| TenantId                              | Gets desktop groups associated with the specified tenant identity.                                                                                                                | false | false |                                                                                        |
| TimeZone                              | Gets desktop groups with the specified value of TimeZone.                                                                                                                         | false | false |                                                                                        |
| TotalApplicationGroups                | Gets desktop groups that are acting as delivery groups for the specified number of application groups.                                                                            | false | false |                                                                                        |
| TotalApplications                     | Gets desktop groups that are acting as delivery groups for the specified number of applications.                                                                                  | false | false |                                                                                        |
| TurnOnAddedMachine                    | Gets desktop groups with the specified value of TurnOnAddedMachine value.                                                                                                         | false | false |                                                                                        |
| UUID                                  | Gets desktop groups with the specified value of UUID.                                                                                                                             | false | false |                                                                                        |
| ZonePreference                        | Gets desktop groups with a zone preference list containing the specified zone preference.                                                                                         | false | false |                                                                                        |
| ApplicationGroupUid                   | Gets only desktop groups with which the specified application group has been associated.                                                                                          | false | false |                                                                                        |
| ApplicationUid                        | Gets desktop groups that publish the specified application (identified by Uid)                                                                                                    | false | false |                                                                                        |
| TagUid                                | Gets desktop groups to which the specified tag (identified by its Uid) has been added to help identify it - see Add-BrokerTag for more information.                               | false | false |                                                                                        |
| PowerTimeSchemeUid                    | Gets desktop groups associated with the specified power time scheme (identified by its Uid).                                                                                      | false | false |                                                                                        |
| MachineConfigurationUid               | Gets desktop groups with the specified value of MachineConfiguration.                                                                                                             | false | false |                                                                                        |
| RemotePCCatalogUid                    | Gets Remote PC desktop groups associated with the specified catalog.                                                                                                              | false | false |                                                                                        |
| ReturnTotalRecordCount                | When specified, this causes the cmdlet to output an error record containing the number of records available. 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Broker_Filtering for details.  | false | false | False                                                                                  |
| MaxRecordCount                        | 指定要返回的最大记录数。                                                                                                                                                                      | false | false | 250                                                                                    |
| 跳过                                    | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                                                                                             | false | false |                                                                                        |
| SortBy                                | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。                                                                                          | false | false | 默认排序顺序是按名称或唯一标识符。                                                                      |
| 过滤器                                   | Gets records that match a PowerShell style filter expression. See about_Broker_Filtering for details.                                                                           | false | false |                                                                                        |
| 属性                                    | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                                                                                            | false | false |                                                                                        |
| AdminAddress                          | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.Broker.Admin.SDK.DesktopGroup

Get-BrokerDesktopGroup returns an object for each matching desktop group.## Notes To perform greater-than or less-than comparisons, use -Filter. For more information, see about_Broker_Filtering and the examples.

## 示例

### 示例 1

    C:\PS> Get-BrokerDesktopGroup -PublishedName EMEA*
    

Description  
\---\---\-----  
Finds all desktop groups with published names starting with "EMEA".

### 示例 2

    C:\PS> Get-BrokerDesktopGroup -InMaintenanceMode $true
    

Description  
\---\---\-----  
Finds all desktop groups in maintenance mode.