---
date: '2026-11-02'
description: 了解如何使用 Aspose.Words for Java 跟踪 Word 文档中的更改，涵盖文档比较、内联修订处理、授权以及性能技巧。
keywords:
- how to track changes
- track formatting changes
- document comparison aspose
- aspose.words license java
lastmod: '2026-11-02'
og_description: 了解如何使用 Aspose.Words for Java 跟踪 Word 文档中的更改，包括文档比较、内联修订处理和授权细节。
og_image_alt: Guide showing how to track changes in Word documents with Aspose.Words
  Java
og_title: 如何使用 Aspose.Words Java 跟踪 Word 文档中的更改
schemas:
- author: Aspose
  dateModified: '2026-11-02'
  description: Learn how to track changes in Word docs using Aspose.Words for Java,
    covering document comparison, inline revision handling, licensing, and performance
    tips.
  headline: How to track changes in Word docs with Aspose.Words Java
  type: TechArticle
- description: Learn how to track changes in Word docs using Aspose.Words for Java,
    covering document comparison, inline revision handling, licensing, and performance
    tips.
  name: How to track changes in Word docs with Aspose.Words Java
  steps:
  - name: '**Free trial:** Download the library from [Aspose Downloads](https://releases.aspose.com/words/java/)
      and use it with evaluation limitations.'
    text: '**Free trial:** Download the library from [Aspose Downloads](https://releases.aspose.com/words/java/)
      and use it with evaluation limitations.'
  - name: '**Temporary license:** Obtain a temporary license for extended usage without
      evaluation restrictions by visiting [Temporary License](https://purchase.aspose.com/temporary-license/).'
    text: '**Temporary license:** Obtain a temporary license for extended usage without
      evaluation restrictions by visiting [Temporary License](https://purchase.aspose.com/temporary-license/).'
  - name: '**Purchase license:** Consider purchasing if you need full access to Aspose.Words
      features by following the instructions on their purchase page.'
    text: '**Purchase license:** Consider purchasing if you need full access to Aspose.Words
      features by following the instructions on their purchase page.'
  - name: '**Collaborative editing:** Teams can review and approve changes before
      publishing a final contract.'
    text: '**Collaborative editing:** Teams can review and approve changes before
      publishing a final contract.'
  - name: '**Legal document review:** Lawyers track amendments to clauses, ensuring
      every change is auditable.'
    text: '**Legal document review:** Lawyers track amendments to clauses, ensuring
      every change is auditable.'
  - name: '**Software documentation:** Technical writers manage updates to API references
      while preserving version history.'
    text: '**Software documentation:** Technical writers manage updates to API references
      while preserving version history.'
  type: HowTo
- questions:
  - answer: An inline node represents a run of text or a character‑level element inside
      a paragraph, such as a `Run` or a `Field`.
    question: What is an inline node in Aspose.Words?
  - answer: Call `document.startTrackRevisions()` on your `Document` instance before
      making any edits.
    question: How do I start tracking revisions with Aspose.Words Java?
  - answer: Yes, use `document.acceptAllRevisions()` or `document.rejectAllRevisions()`
      to apply the changes programmatically.
    question: Can I automate accepting or rejecting revisions in a document?
  - answer: It supports DOCX, PDF, HTML, ODT, RTF, EPUB, and more than 35 formats
      for both import and export.
    question: What types of documents does Aspose.Words support?
  - answer: Process the file section by section, use low‑memory load options, and
      leverage batch revision methods to keep CPU and RAM usage optimal.
    question: How do I handle large documents efficiently with Aspose.Words?
  type: FAQPage
tags:
- track changes
- Aspose.Words Java
- document revisions
- inline revisions
- Java document processing
title: 如何使用 Aspose.Words Java 跟踪 Word 文档中的更改
url: /zh/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words Java 跟踪 Word 文档中的更改

在重要文档上协作通常意味着您需要**跟踪 Word 文档中的更改**，以便每一次编辑都可见且可控制。Aspose.Words for Java 为您提供一个无需 Microsoft Word 即可运行的编程式“Track Changes”引擎，让您可以直接在代码中启动、查询、接受或拒绝修订。在本指南中，您将设置库，探索内联修订的处理，并发现针对大文件的性能友好技术。

## 快速答案
- **哪个库可以实现 Word 文档的更改跟踪？** Aspose.Words for Java  
- **推荐使用哪种依赖管理器？** Maven 或 Gradle（均受支持）  
- **开发是否需要许可证？** 免费试用可用于评估；生产使用需要许可证  
- **我可以高效处理大文档吗？** 可以——使用分段处理和批量操作  
- **是否有方法以编程方式开始跟踪？** `document.startTrackRevisions()` 启动跟踪会话  

## 什么是跟踪更改？
`how to track changes` 指的是以编程方式启用 Word 内置修订跟踪功能的过程。启用后，每一次插入、删除、格式编辑或移动都会记录为一个独立的修订对象。这些对象随后可以被枚举、审阅，并可以接受以使更改永久生效，或拒绝以丢弃更改，从而提供文档编辑的完整可审计性。

## 为什么在更改跟踪中使用 Aspose.Words？
Aspose.Words 支持**35+ 输入和输出格式**——包括 DOCX、PDF、HTML 和 ODT——并且能够在标准服务器硬件上在 **3 秒以内处理 500 页文档**，无需 Microsoft Word。该 API 可在 Windows、Linux 和 macOS 上运行，非常适合需要可靠修订管理的云端或本地解决方案。

## 先决条件

- **Java Development Kit (JDK)：** 8 版或更高。  
- **IDE：** IntelliJ IDEA、Eclipse 或 NetBeans。  
- **构建工具：** 用于依赖管理的 Maven 或 Gradle。  
- 基本的 Java 知识，以便理解代码片段。

## 设置 Aspose.Words

### Maven 设置

在您的 `pom.xml` 文件中添加以下依赖：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

### Gradle 设置

在您的 `build.gradle` 文件中加入此行：

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### 许可证获取

Aspose 提供免费试用以测试其功能，让您评估是否满足需求。开始步骤如下：

1. **免费试用：** 从 [Aspose Downloads](https://releases.aspose.com/words/java/) 下载库，并在评估限制下使用。  
2. **临时许可证：** 访问 [Temporary License](https://purchase.aspose.com/temporary-license/) 获取临时许可证，以在没有评估限制的情况下延长使用。  
3. **购买许可证：** 如果需要完整访问 Aspose.Words 功能，请按照其购买页面上的说明进行购买。

#### 基本初始化

`Document` 是 Aspose.Words 中表示内存中 Word 文件的主要对象。要初始化，只需创建 `Document` 实例并开始使用它：

```java
import com.aspose.words.Document;

public class Main {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("input.docx");
        // Further processing here
    }
}
```

## 如何使用 Aspose.Words Java 跟踪 Word 文档中的更改
`document.startTrackRevisions()` 在文档上启动修订跟踪会话。加载 Word 文件，调用 `startTrackRevisions()` 开始跟踪会话，进行所需编辑，最后保存文档。API 将每一次编辑记录为修订对象，您随后可以枚举、接受或拒绝。此两步模式——开始跟踪，执行编辑——涵盖插入、删除、格式更改和移动。

## 实现指南

在本节中，我们将探讨如何使用 Aspose.Words Java 处理不同类型的修订。

### 处理内联修订

#### 概述

在进行更改跟踪时，内联修订会以 run 的形式出现在段落内部。它们可以是插入、删除、格式更改或移动操作。了解每种类型有助于构建对用户友好的审阅工具。

#### 代码实现

以下代码片段演示了如何检查内联节点的修订类型：

```java
import com.aspose.words.Document;
import com.aspose.words.Paragraph;
import com.aspose.words.Run;
import com.aspose.words.Revision;
import org.testng.Assert;

public class RevisionHandler {
    public void handleRevisions() throws Exception {
        Document doc = new Document("Revision runs.docx");

        // Check the number of revisions
        Assert.assertEquals(6, doc.getRevisions().getCount());

        // Accessing a specific revision's parent node
        Run run = (Run) doc.getRevisions().get(0).getParentNode();

        Paragraph paragraph = run.getParentParagraph();
        com.aspose.words.RunCollection runs = paragraph.getRuns();

        Assert.assertEquals(runs.getCount(), 6);

        // Identifying different types of revisions
        Assert.assertTrue(runs.get(2).isInsertRevision());  // Insert revision
        Assert.assertTrue(runs.get(2).isFormatRevision());  // Format revision
        Assert.assertTrue(runs.get(4).isMoveFromRevision()); // Move from revision
        Assert.assertTrue(runs.get(1).isMoveToRevision());   // Move to revision
        Assert.assertTrue(runs.get(5).isDeleteRevision());   // Delete revision
    }
}
```

`RevisionType` 是一个枚举，用于分类更改类型——Insert、Delete、Format、MoveFrom 或 MoveTo。通过检查此属性，您可以决定是否向用户显示更改或应用自动接受规则。

#### 说明
- **Insert 修订：** 在跟踪激活期间添加的文本。  
- **Format 修订：** 对已有文本的字体、颜色或样式的更改。  
- **Move from / to 修订：** 表示文档内部的文本移动；它们始终成对出现。  
- **Delete 修订：** 被删除的文本，但在接受或拒绝之前仍保留。

### 实际应用

修订处理发挥作用的真实场景：

1. **协作编辑：** 团队可在发布最终合同前审阅并批准更改。  
2. **法律文档审查：** 律师跟踪条款的修订，确保每项更改可审计。  
3. **软件文档：** 技术作者在维护 API 参考更新的同时保留版本历史。

### 性能考虑

`LoadOptions` 配置文档的加载方式，包括内存使用设置。处理大型、修订密集的文档可能会占用大量内存。请遵循以下最佳实践：

- **按章节处理：** 一次加载并处理一个章节，以保持低内存使用。  
- **批量操作：** 在可能的情况下，对整个章节使用 `Document.acceptAllRevisions()` 或 `Document.rejectAllRevisions()`，而不是对单个节点。  
- **流式 API：** 对于大于 1 GB 的文件，使用 `LoadOptions` 的流模式，以避免将整个文件加载到内存中。

## 常见陷阱和故障排除

`document.startTrackRevisions()` 在给定的 Document 实例上启动修订跟踪。

- **编辑后缺少修订：** 确保在进行任何更改之前调用 `document.startTrackRevisions()`；在编辑后才开始跟踪将无法捕获之前的修改。  
- **意外的格式更改：** 某些样式更改会报告为 `RevisionType.Format`。如果您只关心文本内容，请在枚举逻辑中过滤掉格式修订。  
- **大型文档变慢：** 启用 `LoadOptions.memoryUsage = LoadOptions.MemoryUsageMode.LowMemory` 以降低峰值内存消耗。

## 常见问题

`Document.acceptAllRevisions()` 应用所有待处理的修订，使所有更改永久生效。`Document.rejectAllRevisions()` 丢弃所有待处理的修订，将文档恢复到原始状态。

**Q: 什么是 Aspose.Words 中的内联节点？**  
A: 内联节点表示段落内部的文本运行或字符级元素，例如 `Run` 或 `Field`。

**Q: 如何使用 Aspose.Words Java 开始跟踪修订？**  
A: 在进行任何编辑之前，对您的 `Document` 实例调用 `document.startTrackRevisions()`。

**Q: 我可以自动接受或拒绝文档中的修订吗？**  
A: 可以，使用 `document.acceptAllRevisions()` 或 `document.rejectAllRevisions()` 以编程方式应用更改。

**Q: Aspose.Words 支持哪些类型的文档？**  
A: 支持 DOCX、PDF、HTML、ODT、RTF、EPUB 等超过 35 种格式的导入和导出。

**Q: 如何使用 Aspose.Words 高效处理大文档？**  
A: 按章节处理文件，使用低内存加载选项，并利用批量修订方法以保持 CPU 和 RAM 使用的最佳状态。

## 资源

- [Aspose.Words Java 文档](https://reference.aspose.com/words/java/)  
- [下载 Aspose.Words for Java](https://releases.aspose.com/words/java/)  
- [购买许可证](https://purchase.aspose.com/buy)  
- [免费试用](https://releases.aspose.com/words/java/)  
- [临时许可证](https://purchase.aspose.com/temporary-license/)  
- [Aspose 支持论坛](https://forum.aspose.com/c/words/10)

立即使用 Aspose.Words Java 开启您的旅程，充分发挥文档处理在应用中的全部潜力！

---

**最后更新：** 2026-11-02  
**测试版本：** Aspose.Words 25.3 for Java  
**作者：** Aspose

## 相关教程

- [在 Aspose.Words for Java 中实现更改跟踪](/words/java/document-comparison-tracking/)
- [使用 Aspose.Words for Java 文档转换 API 将 Word 转换为 PDF](/words/java/document-converting/)
- [Aspose Words Loadoptions 在 Java 中恢复损坏的 Word 文档](/words/java/document-loading-and-saving/aspose-words-loadoptions-recover-corrupted-word-docs-in-java/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}