---
category: general
date: 2026-02-18
description: 学习如何将 DOCX 转换为 PDF，并在保存 Word 为 PDF 时保留浮动形状。本指南展示了如何正确导出形状。
draft: false
keywords:
- convert docx to pdf
- save word as pdf
- how to export shapes
language: zh
og_description: 将 DOCX 转换为 PDF 并学习如何导出形状。遵循本完整教程，将 Word 保存为带有正确标记的 PDF。
og_title: 将 DOCX 转换为 PDF – 内联形状导出指南
tags:
- Aspose.Words
- Java
- PDF conversion
title: 将 DOCX 转换为 PDF 并导出内联形状 – 步骤指南
url: /zh/java/document-conversion-and-export/convert-docx-to-pdf-with-inline-shape-export-step-by-step-gu/
---

Let's write the full translation.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 将 DOCX 转换为 PDF – 内联形状导出指南

是否曾经需要**将 DOCX 转换为 PDF**，但担心浮动的图片或文本框会消失或位移？你并不孤单。在许多项目中——比如自动化报告生成器或批处理流水线——保持 Word 文档的精确布局是不可妥协的。

好消息是？只需几行代码，你就可以**将 Word 保存为 PDF**，并控制这些浮动形状是导出为内联标签还是保持块级元素。下面将完整展示**如何按需导出形状**，并提供一些避免常见陷阱的技巧。

---

## 你将学到

* 从磁盘加载 `.docx` 文件。  
* 配置 `PdfSaveOptions` 使浮动形状导出为内联标签。  
* 将生成的 PDF 写入你指定的文件夹。  
* 理解 `setExportFloatingShapesAsInlineTag` 标志的意义以及何时需要切换它。  

无需外部服务，也不需要神奇的“点击下载” UI——仅仅是可以直接放入任何 Maven 或 Gradle 项目的纯 Java 代码。

---

## 前置条件

| 需求 | 原因 |
|-------------|----------------|
| **Aspose.Words for Java** (v23.12 或更高) | 提供示例中使用的 `Document` 和 `PdfSaveOptions` 类。 |
| **JDK 8+** | 该库编译于 Java 8 及以上版本；旧版运行时会抛出 `UnsupportedClassVersionError`。 |
| **一个包含至少一个浮动形状（图片、文本框、WordArt）的 DOCX 文件** | 为了看到形状导出选项的效果，需要文档中实际存在浮动对象。 |

如果这些都已经准备好，太好了——我们直接开始。

---

## 第一步 – 加载源文档  

首先创建一个指向要转换的 `.docx` 的 `Document` 实例。构造函数会将文件读取到内存，解析 OpenXML 包，并准备内部对象模型。

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

// Adjust the path to your environment
String inputPath = "YOUR_DIRECTORY/input.docx";

Document doc = new Document(inputPath);
```

> **专业提示：** 如果在循环中处理大量文件，请在调用 `doc.close()`（或让垃圾回收器处理）后再复用同一个 `Document` 对象。这可以防止 Windows 上出现文件句柄泄漏。

---

## 第二步 – 配置 PDF 保存选项以导出形状  

教程的核心就在这里。`PdfSaveOptions` 让你决定转换的行为。将 `setExportFloatingShapesAsInlineTag(true)` 设置为 `true`，会强制所有浮动形状在 PDF 的标签结构中被视为*内联*元素。这意味着屏幕阅读器会按照与周围文本相同的顺序读取形状，通常是可访问性合规的要求。

```java
import com.aspose.words.PdfSaveOptions;

PdfSaveOptions pdfOptions = new PdfSaveOptions();
// true → inline tagging (shape behaves like a character)
// false → block‑level tagging (shape sits in its own block)
pdfOptions.setExportFloatingShapesAsInlineTag(true);
```

**什么时候会把它设为 `false`？**  
如果你的 PDF 只用于打印分发，并且希望形状保持原始定位而不影响逻辑阅读顺序，则可以选择块级标签。默认值是 `false`，因此本教程中我们显式启用了内联行为。

---

## 第三步 – 将文档保存为 PDF  

选项准备好后，使用目标文件名和选项对象调用 `save`。库会处理繁重的工作：布局引擎、字体嵌入以及标签生成。

```java
String outputPath = "YOUR_DIRECTORY/shapes.pdf";
doc.save(outputPath, pdfOptions);
```

调用完成后，你会在指定文件夹中看到 `shapes.pdf`。在 Adobe Acrobat 或任何能够显示标签的 PDF 阅读器中打开（通常在 **文件 → 属性 → 标签**），你会发现浮动形状已作为内联标签出现。

---

## 完整、可运行的示例  

把所有代码整合在一起，这里提供一个自包含的 Java 类，你可以直接编译运行。确保 Aspose.Words JAR 已加入类路径。

```java
import com.aspose.words.*;

public class DocxToPdfWithShapes {
    public static void main(String[] args) {
        try {
            // 1️⃣ Load the source DOCX
            String inputPath = "YOUR_DIRECTORY/input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Configure PDF options – export floating shapes as inline tags
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → inline tagging

            // 3️⃣ Save as PDF
            String outputPath = "YOUR_DIRECTORY/shapes.pdf";
            doc.save(outputPath, pdfOptions);

            System.out.println("✅ Conversion complete! PDF saved to: " + outputPath);
        } catch (Exception e) {
            System.err.println("❌ Something went wrong: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**预期结果：**  
- PDF 文件包含与原始 DOCX 相同的文本内容。  
- 所有浮动图片或文本框现在被标记为*内联*，即它们出现在阅读顺序中，而不是作为独立块。  
- 打开 PDF 的**标签**面板时，你会看到一个 `<Figure>` 元素嵌套在 `<Paragraph>` 中——这正是 `setExportFloatingShapesAsInlineTag(true)` 所保证的。

---

## 常见问题与边缘情况  

### 1️⃣ 这能处理受密码保护的 DOCX 文件吗？  
可以——在加载之前提供密码即可：

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("mySecret");
Document doc = new Document(inputPath, loadOptions);
```

### 2️⃣ Word 文件中的 SVG 或 EMF 图像怎么办？  
Aspose.Words 在保存为 PDF 时会自动将矢量图形栅格化。如果需要保持矢量形式，请设置：

```java
pdfOptions.setRasterizeTransformedElements(false);
```

### 3️⃣ 转换时如何保留超链接？  
默认情况下会保留链接。不过，如果在没有选项的情况下使用 `pdfOptions.setSaveFormat(SaveFormat.PDF)`，可能会失去逻辑结构。保留 `PdfSaveOptions` 对象即可同时保留标签和链接。

### 4️⃣ 能批量处理一个文件夹中的 DOCX 吗？  
完全可以。将 `DocxToPdfWithShapes` 逻辑放入遍历 `Files.list(Paths.get("YOUR_DIRECTORY"))` 的循环中。记得对每个文件单独捕获异常，防止单个错误导致整个批处理中止。

---

## 实战技巧  

* **注意缺失的字体。** 如果源 DOCX 使用了服务器上未安装的自定义字体，PDF 会使用回退字体，可能导致布局错乱。使用 `pdfOptions.setFontEmbeddingMode(FontEmbeddingMode.EMBED_ALL)` 强制嵌入所有字体。  
* **可访问性测试。** 转换后运行 Acrobat 的 **可访问性检查器**。内联标签通常能提升分数，但仍可能需要手动为图片添加替代文本。  
* **性能技巧：** 对于大型文档（100+ 页），启用 `pdfOptions.setMemoryOptimization(true)` 可以降低堆内存占用。

---

## 可视化确认  

下面是一张在 Adobe Acrobat 中打开的 PDF 截图，展示了 **标签** 面板中内联标记的形状。

![Convert DOCX to PDF example output](image.png)

*Alt text: convert docx to pdf example output showing inline shape tags.*

---

## 总结  

现在你已经掌握了**如何在转换 DOCX 为 PDF 时控制浮动对象的导出方式**。通过切换 `setExportFloatingShapesAsInlineTag`，你可以决定形状是成为阅读顺序的一部分，还是保持独立块——这对可访问性和视觉保真度都至关重要。

接下来你可以：

* **批量将 Word 保存为 PDF** 以便归档。  
* 尝试其他 `PdfSaveOptions`，例如 `setCompliance(PdfCompliance.PDF_A_1B)`，实现长期保存。  
* 通过阅读完整的 Aspose.Words 文档或尝试 `setExportDocumentStructure(true)` 标志，进一步探索**如何导出形状**的细节。

动手试一试，调整选项，让你的 PDF 完全符合需求。祝编码愉快！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}