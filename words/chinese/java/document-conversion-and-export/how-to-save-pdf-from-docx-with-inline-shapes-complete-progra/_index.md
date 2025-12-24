---
category: general
date: 2025-12-23
description: 如何使用 Java 从 Word 文件保存 PDF。学习将 docx 转换为 PDF，导出形状，并在一步可靠的操作中将文档保存为 PDF。
draft: false
keywords:
- how to save pdf
- convert docx to pdf
- save document as pdf
- convert word to pdf
- how to export shapes
language: zh
og_description: 学习如何使用 Java 将包含内嵌形状的 DOCX 文件保存为 PDF。本指南涵盖将 DOCX 转换为 PDF、导出形状以及将文档保存为
  PDF。
og_title: 如何将 DOCX 保存为 PDF – 完整分步指南
tags:
- Java
- Aspose.Words
- PDF conversion
title: 如何将带内联形状的 DOCX 保存为 PDF – 完整编程指南
url: /zh/java/document-conversion-and-export/how-to-save-pdf-from-docx-with-inline-shapes-complete-progra/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何从带内联形状的 DOCX 保存为 PDF – 完整编程指南

如果你正在寻找 **如何从 Word 文档保存 pdf**，你来对地方了。无论是为了报告流水线需要 **将 docx 转换为 pdf**，还是仅仅想归档合同，本教程都会一步步展示确切的操作方法——无需猜测。

在接下来的几分钟里，你将了解如何在 **将 word 转换为 pdf** 时保留浮动形状，如何仅用一次方法调用 **将文档保存为 pdf**，以及 `setExportFloatingShapesAsInlineTag` 标志为何如此重要。无需外部工具，只需纯 Java 与 Aspose.Words for Java 库。

---

![如何保存 pdf 示例](image-placeholder.png "带内联形状的 pdf 保存示例")

## 使用 Aspose.Words for Java 保存 PDF

Aspose.Words 是一个成熟、功能完整的 API，允许你以编程方式操作 Word 文档。核心类是 `Document`，它在内存中表示整个 DOCX 文件。通过使用 `PdfSaveOptions`，你可以微调转换过程，包括令人头疼的浮动形状。

### 为什么要使用 `setExportFloatingShapesAsInlineTag`？

浮动图片、文本框和 SmartArt 在 DOCX 中作为独立的绘图对象存储。转换为 PDF 时，默认行为是将它们渲染为独立的层，这可能导致某些阅读器出现对齐问题。启用 **如何导出形状** 会强制库将这些对象直接嵌入 PDF 内容流，确保在 Word 中看到的内容与 PDF 中呈现的完全一致。

---

## 第 1 步：设置项目

在编写任何代码之前，确保已添加正确的依赖。

```xml
<!-- pom.xml snippet for Maven users -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest stable version -->
</dependency>
```

如果你使用 Gradle，等价写法是：

```groovy
implementation 'com.aspose:aspose-words:23.10'
```

> **小贴士：** Aspose.Words 是商业库，但 30 天免费试用足以用于学习和原型开发。

创建一个简单的 Java 项目（IDEA、Eclipse 或 VS Code），并添加上述依赖。这就是完成 **将 docx 转换为 pdf** 所需的全部配置。

---

## 第 2 步：加载源文档

下面的第一行代码加载你想要转换的 Word 文件。将 `YOUR_DIRECTORY` 替换为机器上的绝对或相对路径。

```java
import com.aspose.words.Document;

// Load the source DOCX
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **如果文件不存在怎么办？**  
> 构造函数会抛出 `java.io.FileNotFoundException`。请将调用包装在 `try/catch` 块中并记录友好的提示信息——这在将教程用于生产流水线时非常有帮助。

---

## 第 3 步：配置 PDF 保存选项（导出形状）

现在告诉 Aspose.Words 如何处理浮动对象。

```java
import com.aspose.words.PdfSaveOptions;

// Create PDF save options and enable inline tags for floating shapes
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
pdfSaveOptions.setExportFloatingShapesAsInlineTag(true);
```

将 `setExportFloatingShapesAsInlineTag(true)` 设置为 **如何导出形状** 的核心。若不启用此选项，形状在转换后可能会移动或消失，尤其是在目标 PDF 阅读器不支持复杂绘图层时。

---

## 第 4 步：将文档保存为 PDF

最后，将 PDF 写入磁盘。

```java
// Save the document as PDF using the configured options
doc.save("YOUR_DIRECTORY/inlineShapes.pdf", pdfSaveOptions);
```

当此行代码执行完毕后，你将得到一个名为 `inlineShapes.pdf` 的文件，其外观与 `input.docx` 完全相同，浮动图片也会保持原位。这标志着 **将文档保存为 pdf** 的工作流已完成。

---

## 完整可运行示例

将所有内容组合在一起，下面是一个可以直接复制粘贴到项目中的完整类。

```java
import com.aspose.words.Document;
import com.aspose.words.PdfSaveOptions;

public class DocxToPdfConverter {

    public static void main(String[] args) {
        // Adjust these paths before running
        String inputPath  = "YOUR_DIRECTORY/input.docx";
        String outputPath = "YOUR_DIRECTORY/inlineShapes.pdf";

        try {
            // Step 1: Load the DOCX file
            Document doc = new Document(inputPath);

            // Step 2: Prepare PDF options – this is where we answer how to export shapes
            PdfSaveOptions options = new PdfSaveOptions();
            options.setExportFloatingShapesAsInlineTag(true);

            // Step 3: Save as PDF – the core of how to save pdf
            doc.save(outputPath, options);

            System.out.println("Conversion successful! PDF created at: " + outputPath);
        } catch (Exception e) {
            System.err.println("Error during conversion: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**预期结果：** 在任意 PDF 阅读器中打开 `inlineShapes.pdf`。所有在原始 Word 文件中浮动的图片、文本框和 SmartArt 都应以内联方式出现，保持你设计的精确布局。

---

## 常见变体与边缘情况

| 场景 | 需要调整的内容 | 原因 |
|-----------|----------------|-----|
| **大型文档（>100 MB）** | 增加 JVM 堆内存 (`-Xmx2g`) | 防止转换过程中出现 `OutOfMemoryError` |
| **仅需要特定页面** | 使用 `PdfSaveOptions.setPageIndex()` 与 `setPageCount()` | 节省时间并减小文件体积 |
| **受密码保护的 DOCX** | 使用 `LoadOptions.setPassword()` 加载 | 在无需手动解锁的情况下完成转换 |
| **需要高分辨率图像** | 设置 `PdfSaveOptions.setImageResolution(300)` | 提升图像质量，但增大 PDF 大小 |
| **在无 GUI 的 Linux 上运行** | 无需额外步骤 – Aspose.Words 支持无头模式 | 非常适合 CI/CD 流水线 |

这些调整展示了对 **将 word 转换为 pdf** 场景的更深入理解，使本教程对初学者和有经验的开发者同样有价值。

---

## 如何验证输出

1. 在 Adobe Acrobat Reader 或任意现代浏览器中打开生成的 PDF。  
2. 将缩放比例设为 100 %，检查每个浮动形状是否与周围文字对齐。  
3. 使用 “属性” 对话框（通常是 `Ctrl+D`）确认 PDF 版本为 1.7 或更高——Aspose.Words 默认使用最新兼容版本。  

如果发现任何形状位置异常，请再次确认已调用 `setExportFloatingShapesAsInlineTag(true)`。这个小标志常常能解决最棘手的 **如何导出形状** 问题。

---

## 结论

我们已经完整演示了 **如何从 DOCX 保存 pdf** 并保留浮动图形的全过程，覆盖了 **将 docx 转换为 pdf** 的每一步，并解释了 `setExportFloatingShapesAsInlineTag` 选项为何是实现可靠 **如何导出形状** 的关键。完整、可运行的 Java 示例表明，你只需几行代码即可 **将文档保存为 pdf**。

接下来可以尝试以下实验：  
- 将 `PdfSaveOptions` 设置为嵌入字体 (`setEmbedFullFonts(true)`)。  
- 使用 `Document.appendDocument()` 将多个 DOCX 合并为单个 PDF。  
- 使用相同的 `save` 方法探索 XPS、HTML 等其他输出格式。

对 **将 word 转换为 pdf** 的细节有疑问或需要帮助解决特定边缘情况？欢迎在下方留言，祝编码愉快！

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}