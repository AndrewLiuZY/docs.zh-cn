---
title: 在 Visual Studio 中使用 .NET Core 测试 .NET Standard 类库
description: 为 .NET Core 类库创建单元测试项目。 验证 .NET Core 类库能否正确地进行单元测试。
ms.date: 12/24/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: 307261088f5c7c69c0e69fbd6b99940c04842eec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156616"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio"></a>在 Visual Studio 中使用 .NET Core 测试 .NET Standard 库

在[在 Visual Studio 中生成 .NET Standard 库](library-with-visual-studio.md)中，创建了一个简单的类库，用于向 <xref:System.String> 类添加扩展方法。 现在，将创建一个单元测试，用于确保此类库能够按预期运行。 向在上一篇文章中创建的解决方案添加单元测试项目。

## <a name="create-a-unit-test-project"></a>创建单元测试项目

若要创建单元测试项目，请执行以下操作：

1. 打开在[在 Visual Studio 中生成 .NET Standard 库](library-with-visual-studio.md)一文中创建的 `ClassLibraryProjects` 解决方案。

1. 将名为“StringLibraryTest”的新单元测试项目添加到解决方案。

   1. 在“解决方案资源管理器”  中右键单击解决方案并选择“添加”   > “新建项目”  。

   1. 在“添加新项目”  页面，在搜索框中输入“mstest”  。 从“语言”列表中选择“C#”  或“Visual Basic”  ，然后从“平台”列表中选择“所有平台”  。 选择“MsTest 测试项目(.NET Core)”  模板，然后选择“下一步”  。

   1. 在“配置新项目”页面，在“项目名称”框中输入“StringLibraryTest”。 然后选择“创建”  。

   > [!NOTE]
   > 除了 MSTest 之外，还可以在 Visual Studio 中为 .NET Core 创建 xUnit 和 nUnit 测试项目。

1. 此时，Visual Studio 会创建项目，并在具有以下代码的代码窗口中打开类文件：

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;

    namespace StringLibraryTest
    {
        [TestClass]
        public class UnitTest1
        {
            [TestMethod]
            public void TestMethod1()
            {
            }
        }
    }
    ```

    ```vb
    Imports Microsoft.VisualStudio.TestTools.UnitTesting

    Namespace StringLibraryTest
        <TestClass>
        Public Class UnitTest1
            <TestMethod>
            Sub TestSub()

            End Sub
        End Class
    End Namespace
    ```

   单元测试模板创建的源代码负责执行以下操作：

   - 它会导入 <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> 命名空间，其中包含用于单元测试的类型。

   - 向 `UnitTest1` 类应用 [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) 特性。 测试类中标记有 [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) 属性的所有测试方法都会在单元测试运行时自动执行。

   - 它应用 [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) 属性，将 C# 中的 `TestMethod1` 或将 Visual Basic 中的 `TestSub` 定义为在单元测试运行时自动执行的测试方法。

1. 在“解决方案资源管理器”中，右键单击“StringLibraryTest”项目的“依赖项”节点，并从上下文菜单中选择“添加引用”。

   > [!div class="mx-imgBorder"]
   > ![StringLibraryTest 依赖项的上下文菜单](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. 在“引用管理器”  对话框中，展开“项目”  节点，并选中“StringLibrary”  旁边的框。 添加对 `StringLibrary` 程序集的引用后，编译器可以查找 StringLibrary  方法。 选择“确定”  按钮。 这会添加对类库项目 `StringLibrary` 的引用。

   ![Visual Studio 中的“引用管理器”对话框](./media/testing-library-with-visual-studio/project-reference-manager.png)

## <a name="add-and-run-unit-test-methods"></a>添加并运行单元测试方法

运行单元测试时，Visual Studio 执行单元测试类（对其应用了 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 特性的类）中标记有 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 特性的所有方法。 当第一次遇到测试不通过或测试方法中的所有测试均已成功通过时，测试方法终止。

最常见的测试调用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 类的成员。 许多断言方法至少包含两个参数，其中一个是预期的测试结果，另一个是实际的测试结果。 下表显示了 `Assert` 类最常调用的一些方法：

| 断言方法     | 函数 |
| ------------------ | -------- |
| `Assert.AreEqual`  | 验证两个值或对象是否相等。 如果值或对象不相等，则断言失败。 |
| `Assert.AreSame`   | 验证两个对象变量引用的是否是同一个对象。 如果这些变量引用不同的对象，则断言失败。 |
| `Assert.IsFalse`   | 验证条件是否为 `false`。 如果条件为 `true`，则断言失败。 |
| `Assert.IsNotNull` | 验证对象是否不为 `null`。 如果对象为 `null`，则断言失败。 |

还可以在测试方法中使用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> 方法来指示它应引发的异常的类型。 如果未引发指定异常，则测试不通过。

测试 `StringLibrary.StartsWithUpper` 方法时，需要提供许多以大写字符开头的字符串。 在这种情况下，此方法应返回 `true`，以便可以调用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> 方法。 同样，需要提供许多以非大写字符开头的字符串。 在这种情况下，此方法应返回 `false`，以便可以调用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> 方法。

由于库方法处理的是字符串，因此还需要确保它能够成功处理[空字符串 (`String.Empty`)](xref:System.String.Empty)（不含字符且 <xref:System.String.Length> 为 0 的有效字符串）和 `null` 字符串（尚未初始化的字符串）。 如果对 <xref:System.String> 实例调用 `StartsWithUpper` 作为扩展方法，无法向其传递 `null` 字符串。 不过，还可以直接将其作为静态方法进行调用，并向其传递一个 <xref:System.String> 自变量。

将定义三个方法，每个方法都会对字符串数组中的各个元素反复调用它的 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 方法。 由于测试方法在第一次遇到测试不通过时会立即失败，因此将调用方法重载，以便传递字符串来指明方法调用中使用的字符串值。

创建测试方法：

1. 将 UnitTest1.cs  或 UnitTest1.vb  代码窗口中的代码替换为以下代码：

   [!code-csharp[Test#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]
   [!code-vb[Test#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   `TestStartsWithUpper` 方法中的大写字符的测试包括希腊文大写字母 alpha (U+0391) 和西里尔文大写字母 EM (U+041C)。 `TestDoesNotStartWithUpper` 方法中的小写字符的测试包括希腊文小写字母 alpha (U+03B1) 和西里尔文小写字母 Ghe (U+0433)。

1. 在菜单栏上，选择“文件”   > “将 UnitTest1.cs 另存为”  或“文件”   > “将 UnitTest1.vb 另存为”  。 在“文件另存为”  对话框中，选择“保存”  按钮旁边的箭头，然后选择“保存时使用编码”  。

   > [!div class="mx-imgBorder"]
   > ![Visual Studio“文件另存为”对话框](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

1. 在“确认另存为”  对话框中，选择“是”  按钮，保存文件。

1. 在“高级保存选项”对话框的“编码”下拉列表中，选择“Unicode (UTF-8 带签名) - 代码页 65001”，然后选择“确定”。

   > [!div class="mx-imgBorder"]
   > ![Visual Studio“高级保存选项”对话框](./media/testing-library-with-visual-studio/advanced-save-options.png)

   如果无法将源代码保存为 UTF8 编码文件，Visual Studio 可能会将其另存为 ASCII 文件。 在这种情况下，运行时将无法准确解码 ASCII 范围以外的 UTF8 字符，且测试结果也会不正确。

1. 在菜单栏上，选择“测试”   > “运行”   > “所有测试”  。 此时，“测试资源管理器”  窗口打开并显示测试已成功运行。 “通过的测试”  部分列出了三个测试，“摘要”  部分报告了测试运行结果。

   > [!div class="mx-imgBorder"]
   > ![通过测试的“测试资源管理器”窗口](./media/testing-library-with-visual-studio/test-explorer-window.png)

## <a name="handle-test-failures"></a>处理测试失败

由于运行的测试均通过，因此需进行少量改动，以使其中一个测试方法失败：

1. 通过修改 `TestDoesNotStartWithUpper` 方法中的 `words` 数组来包含字符串“Error”。 由于 Visual Studio 将在生成运行测试的解决方案时自动保存打开的文件，因此无需手动保存。

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. 从菜单栏中选择“测试”   > “运行”   > “所有测试”  ，运行测试。 “测试资源管理器”  窗口指示有两个测试成功，还有一个失败。

   > [!div class="mx-imgBorder"]
   > ![未通过测试的“测试资源管理器”窗口](./media/testing-library-with-visual-studio/failed-test-window.png)

1. 选择失败的测试，`TestDoesNotStartWith`。 “测试资源管理器”  窗口显示断言生成的消息：“Assert.IsFalse 失败。 ‘Error’ 应返回 false; 实际返回 True”。 由于此次失败，数组中“Error”之后的所有字符串都未进行测试。

   > [!div class="mx-imgBorder"]
   > ![显示 IsFalse 断言失败的“测试资源管理器”窗口](./media/testing-library-with-visual-studio/failed-test-detail.png)

1. 撤消在步骤 1 中执行的修改并删除字符串“Error”。 重新运行测试，测试将通过。

## <a name="test-the-release-version-of-the-library"></a>测试库的发行版本

现已测试库的调试版本。 至此，测试已全部通过，且已充分测试库，应对库的发布版本再运行一次这些测试。 许多因素（包括编译器优化）有时可能会导致调试版本和发行版本出现行为差异。

若要测试发行版本，请执行以下操作：

1. 在 Visual Studio 工具栏中，将生成配置从 **“调试”** 更改为 **“发行”** 。

   > [!div class="mx-imgBorder"]
   > ![突出显示发布版本的 Visual Studio 工具栏](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)

1. 在“解决方案资源管理器”  中，右键单击“StringLibrary”  项目，从上下文菜单中选择“生成”  ，重新编译库。

   > [!div class="mx-imgBorder"]
   > ![带有生成命令的 StringLibrary 上下文菜单](./media/testing-library-with-visual-studio/build-library-context-menu.png)

1. 从菜单栏中选择“测试”   > “运行”   > “所有测试”  ，运行单元测试。 测试通过。

至此，已完成对库的测试，下一步就是使其可供调用方使用。 可以将类库与一个或多个应用程序捆绑在一起，也可以 NuGet 包的形式分发类库。 有关详细信息，请参阅[使用 .NET Standard 类库](consuming-library-with-visual-studio.md)。

## <a name="see-also"></a>另请参阅

- [单元测试基础知识 - Visual Studio](/visualstudio/test/unit-test-basics)
