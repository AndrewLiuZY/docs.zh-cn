---
title: 通过 Visual Studio for Mac 开始使用 .NET Core
description: 本主题将指导你使用 Visual Studio for Mac 和 .NET Core 来构建简单的控制台应用程序。
ms.date: 12/19/2019
ms.openlocfilehash: 4cd7e311411bce62698e291e763227496877ea39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "75740492"
---
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a>通过 Visual Studio for Mac 开始在 macOS 上使用 .NET Core

Visual Studio for Mac 提供用于开发 .NET Core 应用程序的功能全面的集成开发环境 (IDE)。 本文将指导你使用 Visual Studio for Mac 和 .NET Core 来构建简单的控制台应用程序。

> [!NOTE]
> 你的反馈非常有价值。 有两种方法可以向开发团队提供有关 Visual Studio for Mac 的反馈：
>
> * 在 Visual Studio for Mac 中，从菜单中选择“帮助”   > “报告问题”  ，或从欢迎屏幕中选择“报告问题”  ，将打开一个窗口，以供填写 bug 报告。 可在[开发人员社区](https://developercommunity.visualstudio.com/spaces/8/index.html)门户中跟踪自己的反馈。
> * 若要提出建议，从菜单中选择“帮助”   > “提供建议”  ，或从欢迎屏幕中选择“提供建议”  ，转到 [Visual Studio for Mac 开发人员社区网页](https://developercommunity.visualstudio.com/content/idea/post.html?space=41)。

## <a name="prerequisites"></a>系统必备

请参阅 [.NET Core 依赖项和要求](../install/dependencies.md?pivots=os-macos)一文。

请查看 [.NET Core 支持](/visualstudio/mac/net-core-support)一文，确保使用的是受支持的 .NET Core 版本。

## <a name="get-started"></a>入门

如果已安装先决条件和 Visual Studio for Mac，请跳过此部分，并继续[创建项目](#creating-a-project)。 请按照以下步骤安装先决条件和 Visual Studio for Mac：

下载 [Visual Studio for Mac 安装程序](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)。 运行安装程序。 阅读并同意许可协议。 在安装过程中，选择用于安装 .NET Core 的选项。 你有机会安装 Xamarin，这是一项跨平台移动应用开发技术。 安装 Xamarin 及其相关组件对于 .NET Core 开发而言是可选项。 有关 Visual Studio for Mac 安装过程的分步介绍，请参阅 [Visual Studio for Mac 文档](/visualstudio/mac/)。 安装完成后，启动 Visual Studio for Mac IDE。

## <a name="creating-a-project"></a>创建项目

1. 在“开始”窗口上，选择“新建”  。

   ![Visual Studio for Mac 开始屏幕上的“新建”按钮](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. 在“新建项目”对话框中，选择“.NET Core”节点下的“应用”。 单击“下一步”，然后选择“控制台应用程序”模板。

   ![新项目模板列表](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. 如果安装了多个版本的 .NET Core，请选择项目的目标框架。

1. 为“项目名称”  键入“HelloWorld”。 选择“创建”  。

   ![配置新的控制台应用程序对话框](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. 等待还原项目的依赖项。 该项目包含一个 C# 文件 *Program.cs*，其中包含具有 `Main` 方法的 `Program` 类。 运行应用时，`Console.WriteLine` 语句将“Hello World!” 输出至控制台。

   ![打开 Program.cs 文件的主窗口](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a>运行此应用程序

使用 ⌘ ↵（command + enter 键）在调试模式下运行应用，或者使用 ⌥ ⌘ ↵（option + command + enter 键）在发布模式下运行应用。

![应用程序输出窗格显示 Hello World!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a>下一步

[使用 Visual Studio for Mac 在 macOS 上构建完整的 .NET Core 解决方案](using-on-mac-vs-full-solution.md)主题为你演示如何构建包含可重用的库和单元测试的完整的 .NET Core 解决方案。
