---
title: power shell和cmd的区别
date: 2022-01-09 10:30:54
tags:
- 其他
---

<center>**缘起**</center>
起因是使用Anaconda3的时候，有两个命令行工具：Anaconda Powershell Prompt 和Anaconda Prompt，让我再一次想起win10系统里面留给我的一个疑惑，power shell和cmd的区别是什么？

<center>**区别**</center>
有一篇[经验](https://jingyan.baidu.com/article/9f7e7ec094938f6f281554e4.html)分析了几点，并且我逐一验证了

- 资源占用：cmd 0.7MB，powershell <20MB
- 界面显示：cmd 统一颜色，powershell 有语法高亮
- 命令排版：cmd 排版随窗口大小变化，美观；powershell 跟随执行命令前的窗口大小
- 命令支持：cmd仅支持传统windows命令，powershell 增加支持.net命令，引入cmdlet工具

综上所述：powershell支持更多命令。内存根本不差这点，界面高亮舒服，排版执行前调整好窗口大小即可，最重要的是命令的支持。

也有一篇微软官方的问答回复了这个问题：[power shell和cmd有什么区别？](https://answers.microsoft.com/zh-hans/windows/forum/windows_7-performance/power/16a7f1bc-b19f-4d5d-b398-2ee6a1dd826f)

<div>
<details>
<summary>微软回答</summary>
<style>
 p {text-indent:2em;} 
</style>
<p>cmd是和powershell都可以做命令行交互，批处理和powershell脚本功能也相当。
<p>Windows PowerShell 是专为系统管理员设计的新 Windows 命令行 shell。Windows PowerShell 包括交互式提示和脚本环境，两者既可以独立使用也可以组合使用。
<p>与接受和返回文本的大多数 shell 不同，Windows PowerShell 是在 .NET Framework 公共语言运行时 (CLR) 和 .NET Framework 的基础上构建的，它接受和返回 .NET Framework 对象。环境中的这一根本更改带来了管理和配置 Windows 的全新工具和方法。
<p>Windows PowerShell 引入了 cmdlet（读作“command-let”）的概念，这是内置到 shell 中的一个简单的单一功能命令行工具。可以分别使用每个 cmdlet，但是组合使用这些简单的工具执行复杂任务时才发挥其作用。Windows PowerShell 包括一百多个基本的核心 cmdlet，您可以编写自己的 cmdlet 并与其他用户共享它们。
<p>与许多 shell 一样，Windows PowerShell 为您提供了对计算机上文件系统的访问。此外，使用 Windows PowerShell 提供程序还可以访问其他数据存储，如注册表和数字签名证书存储，就像访问文件系统一样容易。
</details>
</div>

最终呢，Anaconda里面的两种命令行的区别，也是同上。

扩展：[Using Cmdlets](https://docs.microsoft.com/en-us/previous-versions//bb648607(v=vs.85)?redirectedfrom=MSDN)