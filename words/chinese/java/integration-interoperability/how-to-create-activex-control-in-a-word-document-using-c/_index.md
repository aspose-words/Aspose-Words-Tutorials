---
category: general
date: 2026-08-20
description: 学习如何创建 ActiveX 控件，设置按钮大小，并使用完整的 C# 示例将按钮添加到 Word 中。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- set button size
- add button to word
- how to insert button
- create clickable button
language: zh
lastmod: 2026-08-20
og_description: 使用 C# 在 Word 文件中创建 ActiveX 控件。本教程展示如何设置按钮大小、将按钮添加到 Word 中以及制作可点击的按钮。
og_image_alt: Screenshot of a Word document showing a newly created ActiveX control
  button
og_title: 在 Word 中创建 ActiveX 控件 – 步骤详解 C# 指南
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  headline: How to create ActiveX control in a Word document using C#
  type: TechArticle
- description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  name: How to create ActiveX control in a Word document using C#
  steps:
  - name: Why this works
    text: '* `InsertForms2OleControl` tells Word to embed an OLE object of type **CommandButton**,
      which is the classic ActiveX button class. * The width and height arguments
      directly **set button size**; Word translates the values from points (1 pt ≈
      1/72 in). * Naming the control (`Name = "btnSubmit"`) makes'
  - name: Pro tip
    text: 'If you want a square button, set both dimensions to the same value:'
  - name: 1. What if the button does not appear after saving?
    text: '* Verify that the Aspose.Words version supports `InsertForms2OleControl`.
      Versions prior to 22.5 lack this feature. * Ensure the target file format is
      `.docx` or `.doc`. Older formats like `.rtf` cannot store ActiveX objects.'
  - name: 2. Can I insert the button at a specific bookmark?
    text: 'Yes. Move the builder to the bookmark before calling `InsertForms2OleControl`:'
  - name: 3. How to **set button size** dynamically based on text length?
    text: Calculate the required width using the `Graphics.MeasureString` method (from
      `System.Drawing`) and convert pixels to points (`points = pixels * 72 / DPI`).
      Then pass the computed width to `InsertForms2OleControl`.
  - name: 4. Is there a way to add multiple buttons in a loop?
    text: 'Absolutely. Wrap the insertion logic in a `for` loop and adjust the `Left`
      and `Top` properties for each iteration:'
  type: HowTo
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
title: 如何使用 C# 在 Word 文档中创建 ActiveX 控件
url: /zh/java/integration-interoperability/how-to-create-activex-control-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 C# 在 Word 文档中创建 ActiveX 控件

如果您需要在 Microsoft Word 文件中 **创建 ActiveX 控件**，本指南将准确展示如何操作。您将看到如何 **向 Word 添加按钮**、设置按钮尺寸以及使控件可点击——全部通过一个简短、独立的 C# 程序实现。

在本教程中，您将：

* 了解 ActiveX 控件为何对交互式 Word 文档有用。  
* 学习实现 **设置按钮大小** 并分配标题的完整代码。  
* 看到如何 **创建可点击按钮**，后续可将其绑定到宏或外部逻辑。  

该步骤适用于 Aspose.Words .NET 23.12 或更高版本，仅需 .NET 开发环境。

> **前置条件** – 您拥有有效的 Aspose.Words 许可证（或使用评估版），并且已安装 Visual Studio 2022 或任意 C# IDE。

---

## 在 Word 文档中创建 ActiveX 控件

第一步是实例化一个空的 `Document` 和一个 `DocumentBuilder`。Builder 提供了用于插入对象（如 ActiveX 控件）的高级 API。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document and obtain a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // The rest of the steps are explained in the following sections.
            InsertActiveXButton(builder);

            // Save the result so you can open it in Word.
            doc.Save("ActiveXButton.docx");
            Console.WriteLine("Document saved as ActiveXButton.docx");
        }
```

`InsertActiveXButton` 方法（下文定义）包含了 **如何插入按钮** 并进行配置的逻辑。

```csharp
        /// <summary>
        /// Inserts a CommandButton ActiveX control, sets its size, name, and caption.
        /// </summary>
        static void InsertActiveXButton(DocumentBuilder builder)
        {
            // Step 2: Insert a CommandButton ActiveX control with the desired size (width: 100, height: 30).
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                "CommandButton", 100, 30);

            // Step 3: Assign a name to the control for later reference.
            commandButton.Name = "btnSubmit";

            // Step 4: Set the caption that will be displayed on the button.
            commandButton.Caption = "Submit";

            // Optional: Position the button on the page (e.g., 100 points from the top left).
            commandButton.Left = 100;
            commandButton.Top = 150;
        }
    }
}
```

运行程序后会生成 **ActiveXButton.docx**。在 Word 中打开该文件会看到一个标记为 **Submit** 的按钮。该控件功能完整——点击后会触发标准的 `CommandButton_Click` 事件，您可以随后将其绑定到 VBA 宏。

### 为什么这样可行

* `InsertForms2OleControl` 告诉 Word 嵌入一种类型为 **CommandButton** 的 OLE 对象，这正是经典的 ActiveX 按钮类。  
* 宽度和高度参数直接 **设置按钮大小**；Word 会把数值从点（1 pt ≈ 1/72 in）转换为实际尺寸。  
* 为控件命名 (`Name = "btnSubmit"`) 可方便在 VBA 中定位（`ActiveDocument.InlineShapes("btnSubmit")`）。

---

## 设置按钮大小和标题

如果需要不同的外观，请调整 `InsertForms2OleControl` 调用中的数值参数。方法签名如下：

```csharp
Forms2OleControl InsertForms2OleControl(string progId, double width, double height);
```

* **progId** – ActiveX 类的程序标识符（标准按钮为 `"CommandButton"`）。  
* **width / height** – 以点为单位的尺寸。例如，要创建宽度为 2 cm 的按钮，可使用 `width = 56.7`（2 cm ≈ 56.7 pt）。

您也可以在插入后修改标题：

```csharp
commandButton.Caption = "Send Request";
```

更改标题不会影响尺寸，但会改变用户看到的视觉反馈。

### 小技巧

如果想要方形按钮，只需将两个维度设为相同的数值：

```csharp
Forms2OleControl squareBtn = builder.InsertForms2OleControl("CommandButton", 50, 50);
squareBtn.Caption = "OK";
```

---

## 向 Word 添加按钮并使其可点击

上述代码已经 **向 Word 添加按钮**。若要让按钮执行操作，需要编写一个处理 `Click` 事件的 VBA 宏。下面是一个可粘贴到 Word VBA 编辑器（`Alt+F11` → Insert → Module）中的最小宏示例：

```vba
Sub btnSubmit_Click()
    MsgBox "You clicked the Submit button!", vbInformation
End Sub
```

由于控件名为 `btnSubmit`，Word 会自动将 `Click` 事件映射到 `btnSubmit_Click`。这就是在不使用外部库的情况下实现 **创建可点击按钮** 功能的标准方式。

> **注意：** Word 的宏安全设置可能会阻止 ActiveX 控件。请确保文档的安全设置为 “Enable all macros” 或 “Enable VBA macros”，或对宏进行数字签名后再用于生产环境。

---

## 常见问题：如何插入按钮及故障排除

### 1. 保存后按钮未出现怎么办？

* 确认所使用的 Aspose.Words 版本支持 `InsertForms2OleControl`。22.5 之前的版本不具备此功能。  
* 确保目标文件格式为 `.docx` 或 `.doc`。旧格式如 `.rtf` 无法存储 ActiveX 对象。

### 2. 能否在特定书签处插入按钮？

可以。在调用 `InsertForms2OleControl` 之前，将 builder 移动到书签位置：

```csharp
builder.MoveToBookmark("InsertHere");
builder.InsertForms2OleControl("CommandButton", 100, 30);
```

### 3. 如何根据文本长度 **动态设置按钮大小**？

使用 `Graphics.MeasureString` 方法（来自 `System.Drawing`）计算所需宽度，并将像素转换为点（`points = pixels * 72 / DPI`），随后将计算得到的宽度传递给 `InsertForms2OleControl`。

### 4. 是否可以在循环中添加多个按钮？

完全可以。将插入逻辑放入 `for` 循环，并为每次迭代调整 `Left` 和 `Top` 属性：

```csharp
for (int i = 0; i < 3; i++)
{
    Forms2OleControl btn = builder.InsertForms2OleControl("CommandButton", 80, 25);
    btn.Name = $"btnOption{i + 1}";
    btn.Caption = $"Option {i + 1}";
    btn.Left = 50;
    btn.Top = 100 + i * 40; // stagger vertically
}
```

---

## 预期输出

运行程序并打开 **ActiveXButton.docx** 时：

* 第第一页左上角会出现一个 **Submit** 按钮。  
* 按钮尺寸与您提供的尺寸相匹配（`100 pt × 30 pt`）。  
* 若已添加 VBA 宏，点击按钮会弹出消息框：“You clicked the Submit button!”。

至此，您已成功 **创建 ActiveX 控件**、**设置按钮大小** 并 **向 Word 添加按钮**，同时学习了 **如何插入按钮** 与 **创建可点击按钮**，为后续自动化任务奠定基础。

---

## 结论

本教程教会您如何使用 C# 在 Word 文档中 **创建 ActiveX 控件**。按照步骤操作，您可以 **设置按钮大小**、为控件赋予有意义的名称，并 **向 Word 添加按钮**，使其成为绑定到 VBA 宏的 **可点击按钮**。

接下来您可以进一步探索：

* 将按钮绑定到 .NET COM 加载项，而非 VBA。  
* 使用其他 ActiveX 类，如 `CheckBox` 或 `ComboBox`。  
* 自动化创建包含多个控件的完整表单。

欢迎随意尝试不同的尺寸组合。

## 接下来该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并探索项目中的替代实现方案，每篇均提供完整可运行的代码示例和逐步说明。

- [在 .NET 中创建带浮动图片的 Word 文档](/words/english/net/add-content-using-document-builder/insert-floating-image/)
- [使用 Aspose.Words 在 Word 文档中创建页眉页脚](/words/english/net/header-footer-formatting/create-header-footer/)
- [从 Word 创建可访问的 PDF – 完整指南](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-from-word-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}