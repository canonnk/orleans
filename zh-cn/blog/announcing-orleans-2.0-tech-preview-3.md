# 宣布Orleans2.0技术预览版3

[朱利安·多明格斯(Julian Dominguez)](https://github.com/jdom)2017/9/13下午1:17:21

* * *

我们刚刚发布了Orleans2.0技术预览版火车的重大更新。新的二进制文件现在面向.NET Standard 2.0，因此它们与Orleans的.NET版本几乎完全相同。这意味着当前状态不仅对使用.NET Core编写新应用程序的人起作用，而且对于具有已在.NET Framework中运行的应用程序的人来说，也是一种升级途径。

## 我们完成了吗？

对于我们团队来说，这是一个激动人心的里程碑，因为它使2.0版本更加接近。在发布之前，我们还需要为此版本做一些剩余的事情，例如：

-   为.NET Core应用启用生成时代码生成器(.NET Core仍然仅支持运行时代码生成器)
-   迁移到[Microsoft.Extensions.Logging](https://www.nuget.org/packages/Microsoft.Extensions.Logging/)对于我们所有的日志记录
-   充实silos生成器API
-   通过仅扫描最终用户定义的程序集来改善启动
-   [重组](https://github.com/dotnet/orleans/issues/3353)我们的某些类型具有一个我们不经常版本化的Abstractions项目
-   拥有交易功能的初始版本
-   为通常序列化并持久存储的类型提供一定程度的向后兼容性
-   和其他一些小事

## 我该如何尝试？

我们刚刚将软件包发布到MyGet：<https://dotnet.myget.org/gallery/orleans-ci>

请按照链接获取有关如何配置NuGet以便从该供稿下载程序包的说明。

## 请帮助我们

我们计划开始更频繁地开始向MyGet提要发布更新的软件包，因此请尝试预览，如果有问题，请告知我们，以便我们可以对其进行修复并在不久后以您的方式发送更新。

## Orleans2.0 TP3的生产准备就绪了吗？

还没。大声明：我们在.NET中进行CI测试(因为我们的测试严重依赖AppDomains创建内存孤岛群集，而.NET Core不支持这些孤岛，但我们计划尽快解决)。我们已经在.NET Core(包括Windows和Linux)中进行了一些基本的手动测试，并且我们的一些贡献者正在使用它开发新的服务。获得反馈(和PR！)是此版本的主要目标之一，尚未在生产中使用。此外，即使对于已完全移植的功能，也无法保证此技术预览版与Orleans 1.5完全向后兼容。在接近稳定版本之后，我们将列出所有已知的重大更改，以防您有兴趣将应用程序从1.X升级到2.0。

## 笔记

如果您使用的是较早的技术预览，请注意程序集加载发生了一些变化，我们希望继续进行更改。同时，请注意，在.NET Core中，可能需要发布应用程序，以便所有要扫描的程序集都在同一文件夹中(您可以通过调用\`*dotnet发布*\`在您的silos主机上)。