---
category: general
date: 2026-03-19
description: 学习如何在 Aspose.Words for Java 中捕获警告并检测缺失的字体。本分步指南还展示了如何优雅地处理缺失的字体。
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to detect missing fonts
- handle missing fonts
language: zh
og_description: 如何在 Aspose.Words for Java 中捕获警告，检测缺失字体，并使用完整代码示例处理缺失字体。
og_title: 如何捕获警告 – 检测 Aspose.Words 中缺失的字体
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: 如何捕获警告 – 检测 Aspose.Words 中缺失的字体
url: /zh/java/document-rendering/how-to-capture-warnings-detect-missing-fonts-in-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何捕获警告 – 检测 Aspose.Words 中缺失的字体

是否曾想过在 Word 文档加载时某些字体在机器上不可用时**如何捕获警告**？你并不孤单。在许多实际项目中，缺失的字体会导致静默的布局偏移，而唯一了解发生了什么的方法是监听 Aspose.Words 发出的警告流。  

在本教程中，我们将演示一个完整的、可直接运行的示例，**检测缺失的字体**，向您展示**如何以编程方式检测缺失的字体**，并提供一个关于**处理缺失字体**的快速技巧，以确保输出保持可预测。

> **快速提示：** 代码适用于 Aspose.Words 23.9（或更高版本），并且需要 Java 8+。

---

## 您需要的条件

- **Aspose.Words for Java**（Maven/Gradle 依赖或类路径上的 JAR）  
- 一个引用了系统未安装字体的 Word 文件（`input.docx`），例如 “Comic Sans MS”  
- 一个 Java IDE 或者简单的 `javac`/`java` 命令行环境  

不需要其他库——其余所有内容都包含在 Aspose.Words 包中。

---

## 步骤 1 – 设置 LoadOptions 以捕获警告  

要开始监听警告，必须创建一个 `LoadOptions` 实例。该对象告诉加载器跟踪它遇到的任何问题，例如缺失的字体。

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions that will store warning information
        LoadOptions loadOptions = new LoadOptions();

        // ... the rest of the code follows
```

**为什么这很重要：** 如果没有 `LoadOptions`，加载器会静默地将缺失的字体替换为默认系统字体，而您永远不会知道发生了替换。启用警告可以让您完全可见。

---

## 步骤 2 – 使用 LoadOptions 加载文档  

现在我们实际加载文档。我们刚创建的 `LoadOptions` 被传递给构造函数，因此在解析期间产生的任何警告都会被捕获。

```java
        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**专业提示：** 如果您批量处理许多文件，请复用同一个 `LoadOptions` 实例，以避免不必要的对象创建。

---

## 步骤 3 – 遍历捕获的警告  

Aspose.Words 将每个警告存储为 `WarningInfo` 对象。我们只关心与字体相关的警告，因此我们过滤 `FontSubstitutionWarningInfo`。

```java
        // Step 3: Loop through all warnings generated while loading
        for (WarningInfo warning : document.getWarnings()) {
            // Step 3a: Keep only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // Step 4: Output the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());
            }
        }
    }
}
```

**解释：**  
- `document.getWarnings()` 返回加载期间出现的所有警告的列表。  
- `FontSubstitutionWarningInfo` 包含两个关键数据：**请求的字体**（DOCX 所要求的字体）和 Aspose.Words 回退使用的**实际字体**。  
- 通过打印这两个信息，您可以立即看到哪些字体缺失以及进行了何种替换。

---

## 步骤 4 – （可选）以编程方式处理缺失的字体  

捕获警告只是故事的一半。一旦知道某个字体缺失，您可能希望通过提供自定义替代或记录问题以供后续审查来**处理缺失的字体**。

```java
                // Optional: Replace the missing font with a known fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
```

**为什么要这样做？**  
- 确保在不同机器上的渲染一致。  
- 防止后续生成的 PDF 或图像出现意外的布局变化。  

您还可以将警告详情存入数据库，发送电子邮件给内容团队，或在关键字体缺失时中止处理。

---

## 完整可运行示例  

下面是完整的可运行程序。只需将 `YOUR_DIRECTORY/input.docx` 替换为您的测试文件路径，将 Aspose.Words JAR 添加到类路径，然后运行即可。

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // 3️⃣ Iterate through all warnings
        for (WarningInfo warning : document.getWarnings()) {
            // 3a️⃣ Filter only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // 4️⃣ Display the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());

                // 5️⃣ (Optional) Provide a custom fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
            }
        }

        // 6️⃣ Save the document if you need to see the result with the fallback applied
        document.save("output.docx");
    }
}
```

**预期输出**（当缺少 “Comic Sans MS” 时）：

```
Requested: Comic Sans MS → Substituted: Arial
```

在可选的回退代码运行后，保存的 `output.docx` 将在原本引用 “Comic Sans MS” 的位置使用 **Arial** 渲染。

---

## 常见问题与边缘情况  

| Question | Answer |
|----------|--------|
| *如果文档有多个缺失的字体怎么办？* | 循环会为每个缺失的字体发出警告。您可以将它们收集到 `Map<String, String>` 中进行批处理。 |
| *这对从文档生成的 PDF 有效吗？* | 当然有效。字体替代发生在加载阶段，因此后续的导出（PDF、HTML、图像）都会使用已解析的字体。 |
| *我可以抑制警告而不是捕获它们吗？* | 可以——将 `loadOptions.setWarningCallback(null);` 设置为 null，但您将失去对缺失字体的可见性。 |
| *保存后警告列表会被清除吗？* | 警告集合属于 `Document` 实例。调用 `document.save()` 后，列表保持不变，除非创建新的 `Document`。 |
| *DOCX 中嵌入的自定义字体怎么办？* | 嵌入的字体被视为可用；即使主机系统未安装，Aspose.Words 也会使用它们。 |

---

## 生产环境的专业提示  

- **缓存 FontSettings：** 如果处理数百个文件，请创建一个带有首选回退的 `FontSettings` 实例并复用，以避免开销。  
- **记录结构化数据：** 与其使用普通的 `System.out`，不如将警告写入 JSON 日志——这使得下游分析（例如“最常缺失的字体”）变得轻而易举。  
- **提前验证：** 在进行繁重处理之前，使用 `LoadOptions` 进行快速的“干加载”；如果关键字体缺失则提前中止。  
- **线程安全：** `Document` 对象不是线程安全的。将每个文件的处理放在独立线程中，或使用线程局部的 `LoadOptions`。  

---

## 结论  

您现在已经了解了在 Aspose.Words for Java 中**如何捕获警告**、**检测缺失的字体**以及使用干净的回退策略**处理缺失的字体**。通过利用 `LoadOptions` 并遍历 `document.getWarnings()`，您可以全面了解字体替代事件，确保生成的文档在所有环境中都能如预期般呈现。

准备好下一步了吗？尝试将此模式扩展到**检测缺失的图像**、**跟踪不受支持的特性**，甚至**自动嵌入缺失的字体**到输出文件中。相同的警告捕获方法适用于许多其他文档处理场景，使您的代码更加健壮且具备前瞻性。

祝编码愉快，愿您的文档始终美观呈现！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}