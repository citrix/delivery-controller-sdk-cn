## SDK 入门

要创建脚本，请执行以下步骤：

  1. 使用 Citrix Studio 执行要编写脚本的操作，例如，创建一组 Machine Creation Services 计算机的目录。

  2. 收集 Studio 为执行任务所做的 SDK 操作的日志。

  3. 查看脚本以了解各部分的作用。 这将有助于您自定义自己的脚本。 有关详细信息，请参阅示例用例，其中详细解释了脚本的作用。

  4. 转换并修改 Studio 脚本段，将其转变成更适用的脚本。为此，需要：
    
    - 使用变量。 一些 cmdlet 带有参数，如 TaskId。 但是，由于 Studio 使用早期 cmdlet 的结果对象的值，可能无法清楚了解这些参数中使用的值来自何处。
    
    - 删除任何不需要的命令。
    
    - 将一些步骤添加到循环中，以方便进行控制。例如，将计算机创建过程添加到一个循环中，这样便可以控制要创建的计算机数。

**示例**

**注意：**创建脚本时，为确保始终获得最新的增强功能和修复程序，Citrix 建议您按照上文所述的过程进行操作，而不是复制并粘贴示例脚本。

| 示例                                                      |                       说明                       |
| ------------------------------------------------------- |:----------------------------------------------:|
| [示例：创建目录](./creating-a-catalog.md)                      | 脚本：创建一组 Machine Creation Services (MCS) 计算机的目录 |
| [示例：创建和配置主机](./creating-and-configuring-a-host.md)      |                   脚本：创建和配置主机                   |
| [示例：创建 PvD 桌面](./creating-a-pvd-desktop.md)             |      脚本：创建包含 Personal vDisk (PvD) 桌面的交付组       |
| [示例：获取负载平衡信息 ](./getting-load-balancing-information.md) |               显示服务器操作系统计算机的负载指数值               |