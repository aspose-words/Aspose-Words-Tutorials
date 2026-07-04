---
category: general
date: 2026-05-04
description: 如何设置 Word 导出 Markdown 的分辨率。了解 Markdown 图像分辨率、如何导出公式，以及在 Java 中将 Word
  保存为 Markdown。
draft: false
keywords:
- how to set resolution
- markdown image resolution
- how to use markdown
- how to export equations
- save word as markdown
language: zh
og_description: 如何设置从 Word 导出 Markdown 的分辨率。本指南展示了 Markdown 图像分辨率、导出公式以及将 Word 保存为
  Markdown。
og_title: 在将 Word 保存为 Markdown 时如何设置分辨率
tags:
- Aspose.Words
- Java
- Markdown
- Document Export
title: 在将 Word 保存为 Markdown 时如何设置分辨率
url: /zh/java/document-conversion-and-export/how-to-set-resolution-when-saving-word-as-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在将 Word 保存为 Markdown 时设置分辨率

是否曾经想过 **如何为从 Word 文档生成的 Markdown 文件中的图片设置分辨率**？你并不是唯一的遇到此问题的人。许多开发者在默认的光栅化数学图片在高 DPI 屏幕上显得模糊时都会卡住。

在本教程中，我们将逐步演示如何控制 *markdown 图像分辨率*，同时展示 **如何将公式导出为 LaTeX**，最后说明 **如何使用 Aspose.Words for Java 将 Word 保存为 markdown**。完成后，你将拥有一份清晰、可投入生产的 Markdown 文件，公式渲染清晰，图像质量符合需求。

## 前置条件

- Java 17（或任何近期的 JDK）  
- Aspose.Words for Java 23.6 或更高版本 – 可从 Maven Central 获取  
- 包含 OfficeMath 对象（公式）以及可能的光栅图像的 Word 文档（`.docx`）  
- 对 Maven/Gradle 和 IDE（IntelliJ IDEA、Eclipse、VS Code 等）有基本了解  

无需额外的库，其他所有功能均由 Aspose.Words 处理。

---

## 如何设置 Markdown 导出的分辨率

> **专业提示：** 你选择的分辨率直接影响生成图片的文件大小。**300 dpi** 对大多数基于网页的 Markdown 查看器来说是一个不错的平衡。

```java
// Step 1: Load the source Word document containing equations
Document doc = new Document("YOUR_DIRECTORY/Math.docx");

// Step 2: Create Markdown save options to control the export behavior
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();

// Step 3: Export OfficeMath objects as LaTeX expressions
saveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

// Step 4 (optional): Set image resolution for any rasterized Math images
saveOptions.setImageResolution(300);   // <-- this is where we set the resolution

// Step 5: Save the document as a Markdown file using the configured options
doc.save("YOUR_DIRECTORY/MathExport.md", saveOptions);
```

`setImageResolution(int dpi)` 调用是 **如何设置分辨率** 的核心。它告诉 Aspose.Words 在指定的每英寸点数下光栅化任何回退图像（例如，当公式无法以纯 LaTeX 表示时）。如果省略此行，库会回退到默认的 220 dpi，在视网膜显示屏上可能会显得模糊。

### 为什么要使用 LaTeX 表示公式？

当你以 LaTeX 导出公式 (`OfficeMathExportMode.LATEX`) 时，生成的 Markdown 包含用 `$…$` 或 `$$…$$` 包裹的原始 LaTeX 代码。大多数现代 Markdown 渲染器（GitHub、GitLab、使用 MathJax 的 MkDocs）会将其渲染为清晰、可缩放的矢量图形——无需担心分辨率。分辨率设置仅在 **markdown 图像分辨率** 对于任何光栅回退图像（如嵌入的图表或不被 Markdown 原生支持的图片）时才起作用。

---

## 如何有效使用 Markdown 图像分辨率

如果你需要在 Word 文件中嵌入普通图片（例如截图），它们会被 Aspose.Words 转换为 PNG。相同的 `setImageResolution` 方法同样适用，确保这些 PNG 继承你指定的 DPI。下面是一份快速检查清单：

1. **选择与目标平台匹配的 DPI** – 传统网页使用 72 dpi，标准显示器使用 150 dpi，打印质量 PDF 使用 300 dpi。  
2. **测试输出** – 在你喜欢的查看器中打开生成的 `.md` 文件并放大，验证清晰度。  
3. **考虑文件大小** – 更高的 DPI 会产生更大的 PNG；如果带宽是顾虑，可尝试 200 dpi 并进行对比。

---

## 如何将公式导出为 LaTeX

`saveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);` 这行代码告诉 Aspose.Words 将每个 OfficeMath 对象转换为 LaTeX。这是推荐的做法，因为：

- **可伸缩性** – LaTeX 在任何尺寸下渲染都不会失真。  
- **可编辑性** – 以后可以直接在 Markdown 文件中修改 LaTeX。  
- **兼容性** – 大多数静态站点生成器和文档工具已经支持 LaTeX 渲染。

如果你需要旧的基于图片的回退，只需切换为 `OfficeMathExportMode.IMAGE`。此时，你设置的分辨率就显得尤为关键。

---

## 将 Word 保存为 Markdown – 完整端到端示例

下面是一个完整的、可运行的 Maven 项目片段，演示了从依赖声明到执行的整个流程。

```xml
<!-- pom.xml -->
<project xmlns="http://maven.apache.org/POM/4.0.0" ...>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>markdown-export</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.6</version>
        </dependency>
    </dependencies>
</project>
```

```java
// src/main/java/com/example/MarkdownMathExport.java
package com.example;

import com.aspose.words.*;

public class MarkdownMathExport {
    public static void main(String[] args) throws Exception {
        // Load the source Word document containing equations and images
        Document doc = new Document("src/main/resources/Math.docx");

        // Configure Markdown export options
        MarkdownSaveOptions options = new MarkdownSaveOptions();
        options.setOfficeMathExportMode(OfficeMathExportMode.LATEX); // export equations as LaTeX
        options.setImageResolution(300); // set resolution for rasterized images

        // Save as Markdown
        doc.save("output/MathExport.md", options);

        System.out.println("✅ Markdown export complete! Check output/MathExport.md");
    }
}
```

**预期结果：** `MathExport.md` 将为每个公式包含 LaTeX 块，任何嵌入的图片都会以 DPI 为 300 的 PNG 链接形式出现。使用支持 MathJax 的 Markdown 查看器（例如带有 Markdown Preview Enhanced 插件的 VS Code）打开文件，你将看到方程和图像都异常清晰。

---

## 常见问题与边缘情况

### 如果只想为某一张图片设置不同的 DPI，该怎么办？

Aspose.Words 通过 `setImageResolution` 全局设置 DPI。若需对单张图片使用不同 DPI，需要在生成的 Markdown 后处理：用更高分辨率的 PNG 替换对应文件，并手动调整图片链接。虽然不是理想方案，但对少量特殊情况仍可行。

### 这在 Linux/macOS 上能工作吗？

完全可以。该库是纯 Java 实现，代码可在任何装有 JDK 的平台上运行。只需确保文件路径使用正斜杠或 `Paths.get(...)` 进行平台无关的处理。

### 那 SVG 输出呢？

如果你更倾向于使用矢量图表，可以设置 `saveOptions.setExportImagesAsSvg(true);`。SVG 不受 DPI 影响，**markdown 图像分辨率** 的问题随之消失。不过，并非所有 Markdown 渲染器都能良好处理 SVG，使用前请先在目标平台上测试。

### 能把生成的 Markdown 嵌入到静态站点生成器吗？

可以。输出的是普通的 `.md` 文件，使用标准 Markdown 语法并带有 LaTeX 分隔符。大多数生成器（Jekyll、Hugo、MkDocs）都能直接使用。只需在站点配置中启用 MathJax 或 KaTeX 即可。

---

## 结论

我们已经介绍了 **如何在将 Word 保存为 markdown 时设置图像分辨率**，探讨了 **markdown 图像分辨率** 的细节，演示了 **如何将公式导出为 LaTeX**，并提供了完整的 Java 实现。通过调节 `setImageResolution` 并选择合适的 `OfficeMathExportMode`，你可以精准控制视觉保真度和文件大小。

准备好下一步了吗？尝试将此方法与 Aspose.PDF 结合，将同一 Word 源直接转换为 PDF，或实验 `setExportImagesAsSvg(true)` 以获得基于矢量的图形。这里学到的技巧是任何自动化文档流水线的基石。

如果你觉得本指南有帮助，请在 GitHub 上给它加星，分享给同事，或在下方留下你的使用技巧。祝编码愉快！  

![如何设置分辨率示例](resolution.png "将 Word 保存为 Markdown 时的分辨率设置")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}