---
category: general
date: 2026-04-28
description: 使用 Aspose.Words for Java 创建 PDF UA 文档。学习如何在加载 docx 时进行恢复、将公式导出为 LaTeX、从
  Word 保存为 Markdown，以及检索缺失的字体。
draft: false
keywords:
- create PDF UA document
- retrieve missing fonts
- export equations to LaTeX
- save markdown from Word
- load docx with recovery
language: zh
og_description: 使用 Aspose.Words for Java 创建 PDF UA 文档。一步步指南，涵盖恢复加载、LaTeX 导出、Markdown
  保存以及缺失字体检索。
og_title: 创建 PDF UA 文档 – 完整的 Java 教程
tags:
- Aspose.Words
- Java
- PDF/UA
title: 使用 Aspose.Words 创建 PDF UA 文档 – 完整 Java 指南
url: /zh/java/document-conversion-and-export/create-pdf-ua-document-with-aspose-words-full-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 创建 PDF UA 文档 – 完整 Java 教程

需要 **从 Word 文件创建 PDF UA 文档** 并处理损坏的内容吗？在本教程中，我们将演示如何使用 Aspose.Words for Java 加载带恢复模式的 DOCX、将公式导出为 LaTeX、从 Word 保存 Markdown，以及获取缺失的字体——全部一步到位。  

如果你曾经面对一个损坏的 .docx 而苦恼为何生成的 PDF 无法无障碍访问，那么这里正是你的答案。完成后，你将拥有一个完全符合 PDF/UA 1 标准的文件、一个包含 LaTeX 公式的 Markdown 版本，以及一份加载过程中出现的字体替换清单。

## 你需要准备的东西

- **Aspose.Words for Java**（截至 2026 年的最新版本）——在 Maven/Gradle 中添加依赖或将 JAR 放入 classpath。  
- Java 17 或更高版本（API 使用流式处理，建议使用最新 JDK）。  
- 一个可能包含损坏段落、Office Math 公式和漂浮形状的示例 `input.docx`。  

无需额外库，所有功能都内置于 Aspose.Words。

---

## 第一步 – 使用恢复模式加载 DOCX  

当文档部分损坏时，默认加载器会抛出异常。启用恢复模式后，Aspose.Words 会继续处理并以警告的形式报告问题。

```java
import com.aspose.words.*;

public class LatestFeaturesDemo {

    public static void main(String[] args) throws Exception {

        // 1️⃣ Load the document with recovery to gracefully handle corruption
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

*为什么重要：* 恢复模式可以防止因为单个损坏段落导致整个流程中断。它还会填充 `doc.getWarnings()`，方便后续 **检索缺失字体** 等问题。

---

## 第二步 – 将公式导出为 LaTeX 并写入 Markdown 文件  

大多数开发者喜欢使用 Markdown 编写文档，但 Word 自带的公式复制起来非常麻烦。Aspose.Words 能直接把公式转换为 LaTeX。

```java
        // 2️⃣ Configure Markdown export with LaTeX for Office Math
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

        // Store images in a sub‑folder so the Markdown stays tidy
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });

        // Save the Markdown file
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);
```

*小技巧：* 回调函数会把每个提取的图片保存到 `imgs/` 目录下。这与 GitHub 渲染 Markdown 的方式保持一致——干净且可移植。

---

## 第三步 – 创建带正确标签的 PDF / UA 文档  

PDF/UA（通用可访问性）合规是许多公共部门项目的强制要求。下面的选项可以让 Aspose.Words 正确为漂浮形状打标签，并设置 PDF/UA 合规标志。

```java
        // 3️⃣ Prepare PDF/UA export options
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);          // Enforce PDF/UA‑1
        pdfOptions.setExportFloatingShapesAsInlineTag(true);      // Tag floating shapes

        // Save the accessible PDF
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);
```

*你会看到：* 在 Adobe Acrobat Pro 中打开 `output.pdf`，文档属性里会显示 “PDF/UA‑1 compliant”。所有漂浮形状（文本框、图片）都会拥有适用于屏幕阅读器的标签。

---

## 第四步 – 调整形状的阴影（可选样式）  

虽然对可访问性不是必需的，但对内部报告进行视觉微调会更专业。

```java
        // 4️⃣ Grab the first shape and modify its shadow
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(java.awt.Color.GRAY);
```

*为什么要这么做？* 如果 PDF 同时用于营销，细微的阴影可以提升布局的精致感，同时不影响合规性。

---

## 第五步 – 检索缺失的字体和其他警告  

在恢复加载期间，Aspose.Words 会记录所有字体替换。列出这些信息可以帮助你决定是嵌入正确的字体还是接受替代字体。

```java
        // 5️⃣ Enumerate font‑substitution warnings
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName() +
                                   " → substituted: " + fsw.getSubstitutedFontName());
            }
        }

        // You can also handle other warning types here (e.g., content loss)
    }
}
```

*典型输出*（你的控制台会显示类似如下内容）：

```
=== Font Substitution Report ===
Missing: Calibri → substituted: Arial
Missing: Times New Roman → substituted: Liberation Serif
```

如果看到关键字体缺失，建议在服务器上安装相应字体，或通过 `PdfSaveOptions.setEmbedFullFonts(true)` 将其嵌入。

---

## 完整可运行示例  

以下是完整的、可直接运行的 Java 类。复制到 IDE，修改路径后点击 **Run**。

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to:
 *  • load a DOCX with recovery,
 *  • export equations to LaTeX inside Markdown,
 *  • create a PDF/UA‑1 compliant PDF,
 *  • modify shape shadows,
 *  • and list any font‑substitution warnings.
 */
public class LatestFeaturesDemo {
    public static void main(String[] args) throws Exception {

        // ---- Step 1: Load DOCX with recovery ----
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // ---- Step 2: Export equations to LaTeX in Markdown ----
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);

        // ---- Step 3: Save as PDF/UA with proper tagging ----
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);

        // ---- Step 4: Optional – adjust the first shape’s shadow ----
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(Color.getGray());

        // ---- Step 5: List any missing‑font warnings ----
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName()
                                   + " → substituted: " + fsw.getSubstitutedFontName());
            }
        }
    }
}
```

**预期结果**

| 输出 | 描述 |
|------|------|
| `output.md` | Markdown 文件，所有 Office Math 公式均以 LaTeX（`$…$`）形式出现，图片保存于 `imgs/` 目录下。 |
| `output.pdf` | 符合 PDF/UA‑1 标准的文档；在 Acrobat 中打开可在 “文件 → 属性 → 标准” 中看到 “PDF/UA‑1”。 |
| 控制台 | 列出任何缺失的字体，例如 “Missing: Calibri → substituted: Arial”。 |

---

## 常见问题解答 (FAQ)

**问：这在旧版本的 Aspose.Words 上能工作吗？**  
答：`RecoveryMode`、`OfficeMathExportMode.LATEX` 和 `PdfCompliance.PDF_UA_1` 枚举是在 22.8 版本中引入的。如果使用更旧的版本，请升级——可访问性功能未向后兼容。

**问：如果我想嵌入原始字体而不是使用替代字体，该怎么办？**  
答：设置 `pdfOptions.setEmbedFullFonts(true)`，并确保字体文件在 JVM 的字体路径可被访问。

**问：能否导出到其他标记格式（例如 HTML）并保留 LaTeX 公式？**  
答：可以。使用 `HtmlSaveOptions` 并调用 `setOfficeMathExportMode(OfficeMathExportMode.LATEX)`——同一枚举在多种格式中通用。

**问：我的 DOCX 包含大量漂浮形状，所有形状都会被标记吗？**  
答：使用 `setExportFloatingShapesAsInlineTag(true)`，Aspose.Words 会为每个漂浮形状包装一个 `<Figure>` 标签，以满足大多数屏幕阅读器的检查。

---

## 小结  

我们已经演示了如何 **从 Word 源文件创建 PDF UA 文档**，同时 **使用恢复模式加载 docx**、**将公式导出为 LaTeX**、**从 Word 保存 markdown**，以及 **检索缺失字体**。代码完整自包含，可在任意 Java 17+ 环境下运行，生成的资产既适用于可访问性审计，也适合开发者使用。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}