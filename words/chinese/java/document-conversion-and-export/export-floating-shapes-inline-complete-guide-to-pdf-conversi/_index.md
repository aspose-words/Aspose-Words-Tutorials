---
category: general
date: 2026-07-03
description: 在将 Word 转换为 PDF 时将浮动形状导出为内联。了解如何在 Java 中设置 PDF 选项以及将 Word 保存为 PDF 的选项。
draft: false
keywords:
- export floating shapes inline
- convert word to pdf inline
- how to set pdf options
- save word as pdf options
language: zh
og_description: 在将 Word 文档转换为 PDF 时，将浮动形状导出为内联。此教程展示了如何设置 PDF 选项以及保存 Word 为 PDF 的选项。
og_title: 导出内联浮动形状 – Java PDF 转换指南
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  headline: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  type: TechArticle
- description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  name: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  steps:
  - name: 1. “What if my document contains complex SmartArt?”
    text: SmartArt is treated as a drawing object. The inline flag works for most
      vector shapes, but very intricate SmartArt may still be rendered as an image.
      In those cases, consider flattening the SmartArt in Word before conversion,
      or use `pdfOptions.setExportSmartArtAsImage(true)` to force image export.
  - name: 2. “Can I combine inline and block exports in the same document?”
    text: Unfortunately the API applies the setting globally. If you need mixed behavior,
      split the document into sections, export each section separately with different
      options, then merge the PDFs using `PdfMerger`.
  - name: 3. “Does this affect font embedding?”
    text: No. Font embedding is controlled by `pdfOptions.setEmbedFullFonts(true)`
      (default). You can safely enable or disable it without touching the inline shape
      flag.
  - name: 4. “How do I verify that shapes are really `<span>`?”
    text: Open the resulting PDF in a tool like **PDF.js** or **Adobe Acrobat** →
      **Edit PDF** → **Object Inspector**. You’ll see the shape wrapped in a `<span>`
      element in the underlying XML. If you see `<div>`, the option wasn’t applied.
  type: HowTo
tags:
- Java
- PDF
- Aspose.Words
title: 导出内联浮动形状 – PDF 转换完整指南
url: /zh/java/document-conversion-and-export/export-floating-shapes-inline-complete-guide-to-pdf-conversi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 导出浮动形状内联 – PDF 转换完整指南

是否曾在将 Word 文档转换为 PDF 时需要 **导出浮动形状内联**？你并不孤单——许多开发者都会遇到图表或图标神秘地移到单独层的问题。好消息是，只需一个 PDF 选项即可让这些形状紧贴在 `<span>` 标签内，保持在 Word 中看到的布局。

在本教程中，我们将演示 **如何在 Java 中设置 PDF 选项**，展示 **保存 Word 为 PDF 选项** 的完整代码，并解释为何你可能想要 **将 Word 转换为 PDF 时内联导出**，而不是默认的块级导出。完成后，你将拥有一个可直接放入任意 Maven 或 Gradle 项目的可运行代码片段。

## 你将学到

- 浮动形状内联 `<span>` 与块级 `<div>` 导出的区别。  
- 如何配置 `PdfSaveOptions` 以强制内联渲染。  
- 逐步代码：加载 `.docx`、应用选项并写出 PDF。  
- 常见陷阱（缺失字体、不受支持的形状）以及规避方法。  
- 测试输出的技巧，并将此方法扩展到其他文档元素。

**先决条件** – 需要 Java 8 或更高版本、Aspose.Words for Java 库（或任何提供相同 `PdfSaveOptions` 类的 API），以及包含浮动形状的示例 Word 文件（本教程使用 `FloatingShapes.docx`）。不需要其他外部工具。

---

## 步骤 1：加载源 Word 文档

首先打开要转换的 `.docx`。这一步很直接，但请确保路径是绝对路径或能够正确从类路径解析。

```java
import com.aspose.words.Document;

// Step 1: Load the source Word document
Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");
```

*为什么这很重要：*  
如果文档未能正确加载，后续的 PDF 转换将抛出 `FileNotFoundException`。使用 `Document` 可以确保内部对象模型被完整填充，包括页面上所有的浮动形状。

---

## 步骤 2：创建 PDF 保存选项并将浮动形状设为内联

这里就是关键所在。默认情况下，Aspose.Words 会将浮动形状导出为块级 `<div>` 元素，这会破坏基于 HTML 的 PDF 的流式布局。调用 `setExportFloatingShapesAsInlineTag(true)` 可让引擎将每个形状包装在内联 `<span>` 中。

```java
import com.aspose.words.PdfSaveOptions;

// Step 2: Create PDF save options and set floating shapes to be exported as inline <span> elements
PdfSaveOptions pdfOptions = new PdfSaveOptions();
pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → <span>, false → <div>
```

*为什么这很重要：*  
- **布局保真度** – 内联标签使形状与周围文字对齐，避免出现不必要的空白。  
- **可搜索性** – 内联元素更容易被 PDF 阅读器正确索引。  
- **样式控制** – 若以后将 PDF 再转换为 HTML，可使用 CSS 定位 `<span>`。

> **专业提示：** 如果需要对特定文档使用旧的块级行为，只需传入 `false` 或直接省略此调用。

---

## 步骤 3：使用配置好的选项将文档保存为 PDF

现在将已加载的 `Document` 与 `PdfSaveOptions` 结合，并写出文件。这一行代码完成了大部分工作。

```java
// Step 3: Save the document as a PDF using the configured options
doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);
```

*为什么这很重要：*  
`save` 方法会遵循 `pdfOptions` 上设置的每一个标志。忘记传入选项将回退到默认的块级导出，失去 **导出浮动形状内联** 的意义。

---

## 完整工作示例

将上述内容整合在一起，下面是一个可以立即编译运行的紧凑程序。将 `YOUR_DIRECTORY` 替换为你机器上的实际路径。

```java
import com.aspose.words.*;

public class ExportFloatingShapesInlineDemo {
    public static void main(String[] args) {
        try {
            // Load the source Word document
            Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");

            // Configure PDF options to export floating shapes as inline <span>
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true);

            // Save as PDF with the above options
            doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);

            System.out.println("PDF created successfully with inline floating shapes.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**预期输出** – 运行程序后，打开 `FloatingShapes.pdf`。你应该看到形状与文本紧贴，没有额外的空白；如果检查 PDF 的内部结构，HTML 表现形式会在每个形状周围包含 `<span>` 标签。

![导出浮动形状内联示例](https://example.com/export-inline.png "显示浮动形状在 PDF 中内联渲染的截图")

*图片替代文字：* **导出浮动形状内联** 的 PDF 截图，展示内联形状。

---

## 常见问题与边缘情况

### 1. “如果我的文档包含复杂的 SmartArt 会怎样？”

SmartArt 被视为绘图对象。内联标志对大多数矢量形状有效，但极其复杂的 SmartArt 仍可能被渲染为图像。此时可在 Word 中先将 SmartArt 扁平化，或使用 `pdfOptions.setExportSmartArtAsImage(true)` 强制以图像方式导出。

### 2. “我能在同一文档中同时使用内联和块级导出吗？”

遗憾的是，该 API 的设置是全局生效的。如果需要混合行为，请将文档拆分为多个章节，分别使用不同的选项导出各章节，然后使用 `PdfMerger` 合并 PDF。

### 3. “这会影响字体嵌入吗？”

不会。字体嵌入由 `pdfOptions.setEmbedFullFonts(true)`（默认）控制。你可以安全地开启或关闭它，而无需触碰内联形状标志。

### 4. “我如何验证形状真的被包装成 `<span>` 了？”

在 **PDF.js** 或 **Adobe Acrobat** → **编辑 PDF** → **对象检查器** 中打开生成的 PDF。你会在底层 XML 中看到形状被 `<span>` 元素包裹。如果看到 `<div>`，说明选项未生效。

---

## 扩展方法 – 相关选项

既然已经了解了核心设置，下面这些 PDF 转换的调节项也值得一试：

| 选项 | 功能说明 | 常见使用场景 |
|--------|--------------|------------------|
| `setCompressImages(true)` | 减小图像体积 | 加快下载速度 |
| `setUseHighQualityRendering(true)` | 提升矢量渲染质量 | 打印级 PDF |
| `setExportDocumentStructure(true)` | 为可访问性添加结构标签 | WCAG 合规 |
| `setSaveFormat(SaveFormat.PDF)` | 明确指定保存格式（很少需要） | 多格式流水线 |

这些设置与 **将 Word 转换为 PDF 内联** 场景相辅相成，兼顾布局保真度与性能。

---

## 测试你的转换

1. **视觉检查** – 在 Chrome 和 Adobe Reader 两个阅读器中打开 PDF，确认形状对齐。  
2. **自动化对比** – 使用 `pdfbox` 等库提取 XML，断言存在 `<span>` 标签。  
3. **性能基准** – 对比开启和关闭 `setCompressImages` 时的耗时，观察权衡。

下面是一个简短的 JUnit 示例：

```java
@Test
public void testInlineExport() throws Exception {
    Document doc = new Document("src/test/resources/FloatingShapes.docx");
    PdfSaveOptions opts = new PdfSaveOptions();
    opts.setExportFloatingShapesAsInlineTag(true);
    ByteArrayOutputStream out = new ByteArrayOutputStream();
    doc.save(out, opts);
    String pdfXml = new String(out.toByteArray(), StandardCharsets.UTF_8);
    assertTrue(pdfXml.contains("<span"));
}
```

---

## 结论

现在，你已经掌握了在 **将 Word 转换为 PDF 时导出浮动形状内联** 的完整端到端方案。通过配置 `PdfSaveOptions`，你可以控制每个形状使用的 HTML 标签，使 PDF 更整洁、可搜索。记得测试输出、调整图像压缩等相关选项，并处理诸如复杂 SmartArt 等边缘情况。

准备好下一步了吗？尝试将同样的技巧应用于 **导出浮动表格内联**，或使用 Aspose 的 `HtmlSaveOptions` 实现 CSS 样式的 PDF。加载、配置、保存的模式几乎适用于所有文档‑到‑PDF 场景。

对 **如何设置 pdf 选项** 或在其他库中使用 **保存 Word 为 PDF 选项** 有更多疑问？欢迎留言，祝编码愉快！

## 接下来你可以学习什么？

以下教程与本指南的技术紧密相关，帮助你进一步掌握 API 功能并探索在项目中的替代实现方式。

- [Convert Word to PDF with Aspose.Words for Java](/words/english/java/document-converting/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Export Word Document Structure to PDF Document](/words/english/net/programming-with-pdfsaveoptions/export-document-structure/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}