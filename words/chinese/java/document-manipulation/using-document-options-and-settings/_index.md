---
date: 2026-01-16
description: 了解如何使用 Aspose.Words for Java 在 Word 中突出显示拼写错误，并学习如何设置每行字符数、定制视图选项以及清理样式。
linktitle: Using Document Options and Settings
second_title: Aspose.Words Java Document Processing API
title: 使用 Aspose.Words Java 在 Word 中突出显示拼写错误
url: /zh/java/document-manipulation/using-document-options-and-settings/
weight: 31
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中使用文档选项和设置

## Aspose.Words for Java 中文档选项和设置的简介

在本综合指南中，您将学习 **如何在 Word 中突出显示拼写错误**，并掌握诸如查看选项、页面布局和样式清理等相关设置。无论您是经验丰富的开发者还是刚入门，新手，下面的示例都能帮助您创建健壮、能够感知错误的文档，并在各种 Word 版本中正常工作。

## 快速答疑
- **如何在 Word 中突出显示拼写错误？** 在 `Document` 对象上使用 `setShowSpellingErrors(true)`。  
- **还能显示语法错误吗？** 可以——调用 `setShowGrammaticalErrors(true)`。  
- **哪个方法设置每行字符数？** `getPageSetup().setCharactersPerLine(int)`。  
- **哪个 API 用于针对特定 Word 版本进行优化？** `doc.getCompatibilityOptions().optimizeFor(MsWordVersion)`。  
- **有没有办法清理未使用的样式？** 使用 `CleanupOptions` 并调用 `setUnusedStyles(true)`，随后执行 `doc.cleanup(options)`。

## 如何在 Word 中突出显示拼写错误？

Aspose.Words 使打开拼写错误突出显示变得非常简单。当文档在 Microsoft Word 中打开时，拼写错误的单词会出现熟悉的红色下划线，帮助最终用户即时发现问题。

## 如何设置每行字符数

控制每行字符数对于固定宽度布局（例如代码清单或传统表单）至关重要。`PageSetup` 类提供 `setCharactersPerLine(int)`，可让您精确定义该值。

## 如何显示语法错误

除了拼写错误，您还可以启用语法错误显示。这对于必须遵循风格指南的内容起草或构建校对工具非常有用。

## 为兼容性优化文档

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.OptimizeForMsWord.docx");
```

文档管理的一个关键方面是确保与不同版本的 Microsoft Word 兼容。Aspose.Words for Java 提供了一种直接的方法，可针对特定的 Word 版本对文档进行优化。在上面的示例中，我们将文档优化为 Word 2016，以确保无缝兼容。

## 识别语法和拼写错误

```java
@Test
public void showGrammaticalAndSpellingErrors() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    doc.setShowGrammaticalErrors(true);
    doc.setShowSpellingErrors(true);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ShowGrammaticalAndSpellingErrors.docx");
}
```

在处理文档时，准确性至关重要。Aspose.Words for Java 使您能够在文档中突出显示语法和拼写错误，从而提高校对和编辑效率。

## 清理未使用的样式和列表

```java
@Test
public void cleanupUnusedStylesAndLists() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Unused styles.docx");
    // Define cleanup options
    CleanupOptions cleanupOptions = new CleanupOptions();
    cleanupOptions.setUnusedLists(false);
    cleanupOptions.setUnusedStyles(true);
    doc.cleanup(cleanupOptions);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupUnusedStylesAndLists.docx");
}
```

高效管理文档样式和列表对于保持文档一致性至关重要。Aspose.Words for Java 允许您清理未使用的样式和列表，确保文档结构简洁有序。

## 删除重复样式

```java
@Test
public void cleanupDuplicateStyle() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Clean duplicate styles
    CleanupOptions options = new CleanupOptions();
    options.setDuplicateStyle(true);
    doc.cleanup(options);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupDuplicateStyle.docx");
}
```

重复的样式会导致文档混乱和不一致。使用 Aspose.Words for Java，您可以轻松删除重复样式，保持文档的清晰和连贯。

## 自定义文档查看选项

```java
@Test
public void viewOptions() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Customize viewing options
    doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
    doc.getViewOptions().setZoomPercent(50);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ViewOptions.docx");
}
```

定制文档的查看体验至关重要。Aspose.Words for Java 允许您设置多种查看选项，如页面布局和缩放比例，以提升文档可读性。

## 配置文档页面设置

```java
@Test
public void documentPageSetup() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Configure page setup options
    doc.getFirstSection().getPageSetup().setLayoutMode(SectionLayoutMode.GRID);
    doc.getFirstSection().getPageSetup().setCharactersPerLine(30);
    doc.getFirstSection().getPageSetup().setLinesPerPage(10);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.DocumentPageSetup.docx");
}
```

精确的页面设置对文档排版至关重要。Aspose.Words for Java 使您能够设置布局模式、**每行字符数**以及每页行数，确保文档在视觉上更具吸引力。

## 设置编辑语言

```java
@Test
public void addJapaneseAsEditingLanguages() throws Exception
{
    LoadOptions loadOptions = new LoadOptions();
    // Set language preferences for editing
    loadOptions.getLanguagePreferences().addEditingLanguage(EditingLanguage.JAPANESE);
    Document doc = new Document("Your Directory Path" + "No default editing language.docx", loadOptions);
    // Check the overridden editing language
    int localeIdFarEast = doc.getStyles().getDefaultFont().getLocaleIdFarEast();
    System.out.println(localeIdFarEast == (int) EditingLanguage.JAPANESE
            ? "The document either has no any FarEast language set in defaults or it was set to Japanese originally."
            : "The document default FarEast language was set to another than Japanese language originally, so it is not overridden.");
}
```

编辑语言在文档处理过程中发挥重要作用。使用 Aspose.Words for Java，您可以设置并自定义编辑语言，以满足文档的语言需求。

## 结论

在本指南中，我们深入探讨了 Aspose.Words for Java 中的各种文档选项和设置。从兼容性优化、错误显示到样式清理和查看选项，这个强大的库为管理和自定义文档提供了广泛的功能。

## 常见问答

### 如何针对特定的 Word 版本优化文档？

要针对特定的 Word 版本进行优化，请使用 `optimizeFor` 方法并指定所需的版本。例如，针对 Word 2016 进行优化：

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "OptimizedForWord2016.docx");
```

### 如何在文档中突出显示语法和拼写错误？

您可以使用以下代码在文档中启用语法和拼写错误的显示：

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.setShowGrammaticalErrors(true);
doc.setShowSpellingErrors(true);
doc.save("Your Directory Path" + "ShowErrors.docx");
```

### 清理未使用的样式和列表的目的是什么？

清理未使用的样式和列表有助于保持文档结构的整洁有序。它会移除不必要的杂乱，提高文档的可读性和一致性。

### 如何从文档中删除重复的样式？

要删除文档中的重复样式，请使用 `cleanup` 方法并将 `duplicateStyle` 选项设为 `true`。示例代码如下：

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
CleanupOptions options = new CleanupOptions();
options.setDuplicateStyle(true);
doc.cleanup(options);
doc.save("Your Directory Path" + "CleanedDocument.docx");
```

### 如何自定义文档的查看选项？

您可以使用 `ViewOptions` 类来自定义文档的查看选项。例如，将视图类型设置为页面布局并将缩放比例设为 50%：

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
doc.getViewOptions().setZoomPercent(50);
doc.save("Your Directory Path" + "CustomView.docx");
```

## 其他提示与常见陷阱

- **在需要全面校对时同时启用拼写和语法检查**。忘记设置其中一个标志（`setShowGrammaticalErrors` 或 `setShowSpellingErrors`）可能导致错误被忽略。  
- **设置每行字符数时**，请记住该值会受到所选字体和页面边距的影响。务必在实际文档布局中进行测试，以避免意外的换行。  
- **清理操作在原始文件上是不可逆的**。请始终在副本上操作或使用版本控制来保留原始样式。  
- **编辑语言偏好**会影响拼写检查行为。如果面向多语言文档，请将所有相关语言添加到 `LanguagePreferences` 中。

---

**最后更新：** 2026-01-16  
**测试环境：** Aspose.Words for Java 24.12  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}