---
category: general
date: 2026-06-02
description: 学习如何在 C# 中使用可变字重字体，并以编程方式设置字体粗细，同时更改字体伸展代码以实现动态排版。
draft: false
keywords:
- use variable weight font
- set font weight programmatically
- change font stretch code
- variable font Aspose.Words
- dynamic typography C#
language: zh
og_description: 在 C# 中使用可变粗细字体，以编程方式设置字体粗细并更改字体伸展代码，从而在文档中实现动态排版。
og_title: 在 C# 中使用可变粗细字体 – 完整指南
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  headline: Use Variable Weight Font in C# – Complete Programming Guide
  type: TechArticle
- description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  name: Use Variable Weight Font in C# – Complete Programming Guide
  steps:
  - name: What if the font doesn’t appear at all?
    text: '- **Missing FontSettings**: Double‑check that `doc.FontSettings = fontSettings;`
      is executed **before** any text is added. - **Incorrect family name**: Use `fontSettings.GetFonts()`
      to list all discovered families; copy the exact string. - **Unsupported weight/stretch**:
      Some variable fonts only sup'
  - name: Can I change the weight after the document is saved?
    text: Yes. The `Run` object is mutable, so you can adjust `FontWeight` or `FontStretch`
      at any point before the final `Save`. If you need to toggle weights dynamically
      (e.g., based on user interaction), consider generating separate runs for each
      state.
  - name: Does this work with DOCX output?
    text: Absolutely. The variable‑weight metadata is stored in the underlying OpenXML,
      and modern versions of Word can interpret it. However, older Word versions may
      ignore the stretch setting.
  type: HowTo
tags:
- C#
- Aspose.Words
- Variable Fonts
title: 在 C# 中使用可变字重字体 – 完整编程指南
url: /zh/net/enable-opentype-features/use-variable-weight-font-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中使用可变粗细字体 – 完整编程指南

是否曾经需要在 .NET 项目中 **使用可变粗细字体**，但不确定如何让粗细和伸展度响应用户输入？你并不孤单。在许多 UI 或报表场景中，你希望文本能够自适应——比如一个在悬停时变为粗体的轻量标题，或一个为强调而加宽的段落。好消息是，使用 Aspose.Words 你可以 **以编程方式设置字体粗细**，甚至 **实时更改字体伸展代码**。

在本教程中，我们将通过一个动手示例，完整演示如何加载可变粗细字体、应用自定义粗细，并调节伸展设置——所有代码均为可直接复制粘贴的 C# 示例。完成后，你将拥有一个可运行的控制台应用，生成展示效果的 PDF。

---

## 你需要准备的内容

- **Aspose.Words for .NET**（v23.12 或更高）。该库完整支持可变粗细字体。
- 包含至少一个可变粗细字体文件的文件夹，例如 *RobotoFlex‑Variable.ttf*。可从 Google Fonts 下载。
- .NET 6 SDK（或任意近期 .NET 版本）以及你喜欢的 IDE。
- 基础的 C# 知识——不需要高级技巧，只需几行代码。

就这些。除 Aspose.Words 外无需额外的 NuGet 包，也不需要奇怪的配置文件。

---

![使用可变粗细字体示例](https://example.com/variable-weight-sample.png "使用可变粗细字体演示")

*Alt text: 展示在生成的 PDF 文档中使用可变粗细字体的截图。*

---

## 第 1 步：设置 FontSettings 并指向你的字体文件夹  

首先，Aspose.Words 必须知道你的可变粗细字体所在位置。通过创建 `FontSettings` 对象并附加 `FolderFontSource` 来实现。`true` 标志表示引擎还会搜索子文件夹，这在你将多个字体族放在同一目录时非常方便。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create FontSettings and point to the folder containing variable‑weight fonts
var fontSettings = new FontSettings();
fontSettings.SetFontSources(new FontSourceBase[]
{
    new FolderFontSource(@"C:\MyProject\Fonts\", true) // Adjust path to your own directory
});
```

**为什么这一步很重要：**如果不注册文件夹，Aspose.Words 会回退到系统字体，忽略自定义字体文件中嵌入的可变粗细数据。这一步是后续所有操作的基础。

---

## 第 2 步：将 FontSettings 附加到 Document  

接下来创建一个新的 `Document`（或加载已有文档），并告诉它使用我们刚才准备好的 `FontSettings`。这种绑定使得后续添加的每个 `Run` 都能访问可变粗细数据。

```csharp
// Step 2: Attach the FontSettings to the document
var doc = new Document();          // Starts with a blank document
doc.FontSettings = fontSettings;   // Connects our custom fonts
```

如果你已经有模板——比如带占位符的 Word 文件——可以将 `new Document()` 替换为 `new Document("Template.docx")`。同样的 `FontSettings` 将会生效。

---

## 第 3 步：添加将使用可变粗细字体的 Run  

`Run` 是 Aspose.Words 中最小的文本格式单元。我们将创建一个 Run，将其插入新段落，随后再修改其字体属性。

```csharp
// Step 3: Add a run of text that will use the variable‑weight font
var paragraph = new Paragraph(doc);
doc.FirstSection.Body.AppendChild(paragraph);

var run = new Run(doc, "Variable‑weight text demo");
paragraph.AppendChild(run);
```

此时文本会使用默认字体（通常是 Times New Roman）渲染。真正的魔法将在我们为其指定可变粗细族后出现。

---

## 第 4 步：选择可变粗细字体族  

这里才是真正 **使用可变粗细字体** 的地方。将 `Font.Name` 设置为可变字体文件内部定义的精确族名。对于 Roboto Flex，族名为 `"Roboto Flex"`。

```csharp
// Step 4: Choose the variable‑weight font family
run.Font.Name = "Roboto Flex";
```

如果不确定族名，可在字体查看器中打开 `.ttf` 文件，或使用 `fontSettings.GetFonts()` 方法枚举可用族。

---

## 第 5 步：以编程方式设置字体粗细和伸展  

现在进入教程核心：我们 **以编程方式设置字体粗细** 并 **更改字体伸展代码**。这两个属性均接受整数值，映射到 OpenType 规范。

```csharp
// Step 5: Specify the desired weight and stretch for the run
run.Font.FontWeight = 300;   // Light weight (300)
run.Font.FontStretch = 125; // Expanded stretch (125% of normal width)
```

- **FontWeight**：100（Thin）→ 900（Black）。选择任意可变字体支持的数值。
- **FontStretch**：50（Ultra‑Condensed）→ 200（Ultra‑Expanded）。默认值为 100（Normal）。

> **专业提示：**并非所有可变字体都公开完整范围。如果设置了不受支持的值，引擎会自动夹取到最近的可用粗细或伸展。

---

## 第 6 步：保存文档并验证结果  

最后，将文档保存为 PDF（或 DOCX），打开查看效果。PDF 是视觉验证的理想格式，因为其渲染在各平台上保持一致。

```csharp
// Step 6: Save the document as PDF
doc.Save(@"C:\MyProject\Output\VariableWeightDemo.pdf", SaveFormat.Pdf);
```

打开 *VariableWeightDemo.pdf* 后，你应该能看到短语 “Variable‑weight text demo” 以轻量、略微展开的 Roboto Flex 渲染。将 `FontWeight` 改为 `700`、`FontStretch` 改为 `80` 并重新运行——即可看到文本变粗且更紧凑。

---

## 常见问题与边缘情况  

### 如果字体根本没有显示怎么办？

- **缺少 FontSettings**：确保在添加任何文本之前执行 `doc.FontSettings = fontSettings;`。
- **族名错误**：使用 `fontSettings.GetFonts()` 列出所有发现的族名，复制完整字符串。
- **不支持的粗细/伸展**：部分可变字体仅支持 100‑900 粗细范围的子集。可使用 `run.Font.FontWeight = 400;` 作为安全回退。

### 能在文档保存后再更改粗细吗？

可以。`Run` 对象是可变的，你可以在最终 `Save` 之前随时调整 `FontWeight` 或 `FontStretch`。如果需要根据用户交互动态切换粗细，考虑为每种状态生成独立的 Run。

### 这在 DOCX 输出时也有效吗？

完全有效。可变粗细元数据会存储在底层 OpenXML 中，现代版本的 Word 能够解释它。不过，较旧的 Word 版本可能会忽略伸展设置。

---

## 完整可运行示例  

下面是一段完整的控制台程序，你可以立即编译运行。它包含所有必要的 `using` 指令、错误处理以及注释。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace VariableWeightDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure FontSettings
            var fontSettings = new FontSettings();
            fontSettings.SetFontSources(new FontSourceBase[]
            {
                // 👉 Point to your local folder containing the variable‑weight font files
                new FolderFontSource(@"C:\MyProject\Fonts\", true)
            });

            // 2️⃣ Create the document and attach FontSettings
            var doc = new Document();
            doc.FontSettings = fontSettings;

            // 3️⃣ Build a paragraph with a run of text
            var paragraph = new Paragraph(doc);
            doc.FirstSection.Body.AppendChild(paragraph);
            var run = new Run(doc, "Variable‑weight text demo");
            paragraph.AppendChild(run);

            // 4️⃣ Apply the variable‑weight font family
            run.Font.Name = "Roboto Flex";

            // 5️⃣ Set weight (300 = Light) and stretch (125 = Expanded)
            run.Font.FontWeight = 300;   // set font weight programmatically
            run.Font.FontStretch = 125; // change font stretch code

            // 6️⃣ Save as PDF to verify the rendering
            string outputPath = @"C:\MyProject\Output\VariableWeightDemo.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}");
            Console.WriteLine("Open the PDF to see the light, expanded Roboto Flex text.");
        }
    }
}
```

**预期输出：**控制台打印保存路径，生成的 PDF 显示轻量、展开样式的文本——正是我们配置的效果。

---

## 小结  

我们已经学习了如何在 C# 中 **使用可变粗细字体**，演示了 **以编程方式设置字体粗细**，并展示了实现 **更改字体伸展代码** 的完整步骤。步骤简洁明了：配置 `FontSettings`、将其附加到 `Document`、创建 `Run`、选择可变粗细族，最后调节 `FontWeight` 与 `FontStretch`。

---

## 接下来可以做什么？

- **动态 UI 集成**：将相同逻辑嵌入 WinForms 或 WPF 应用，让用户通过滑块选择粗细/伸展。
- **多个 Run**：在同一段落中组合不同粗细的多个 Run，实现丰富的排版层次。
- **高级轴**：部分可变字体提供额外轴（如倾斜、光学尺寸）。可使用 `run.Font.FontStyle` 或探索 `FontVariationSettings` 实现更细致的控制。
- **性能技巧**：在处理大量文档时缓存 `FontSettings` 实例，避免重复扫描文件夹。

尽情实验——将 *Roboto Flex* 换成 *Inter Variable* 或其他 OpenType 可变字体，感受文档视觉灵活性的提升。祝编码愉快！


## 接下来你应该学习什么？

以下教程与本指南紧密相关，帮助你进一步掌握 API 功能并探索在项目中的替代实现方式，每篇都包含完整的可运行代码示例和逐步说明。

- [使用目标机器上的字体](/words/english/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [使用目标机器上的字体](/words/german/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [使用目标机器上的字体](/words/french/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}