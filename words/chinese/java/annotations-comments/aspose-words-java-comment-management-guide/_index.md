---
date: '2026-06-12'
description: 了解如何使用 Aspose.Words for Java 在 Word 中创建批注，以及如何轻松地添加批注、打印、删除、标记为已完成并跟踪时间戳。
keywords:
- create comment in word
- how to add comment
- how to delete comment
- add reply to comment
- mark comment as done
schemas:
- author: Aspose
  dateModified: '2026-06-12'
  description: Learn how to create comment in Word using Aspose.Words for Java, and
    how to add comment, print, remove, mark as done, and track timestamps effortlessly.
  headline: 'Aspose.Words Java: Create Comment in Word Docs – Full Guide'
  type: TechArticle
- description: Learn how to create comment in Word using Aspose.Words for Java, and
    how to add comment, print, remove, mark as done, and track timestamps effortlessly.
  name: 'Aspose.Words Java: Create Comment in Word Docs – Full Guide'
  steps:
  - name: Initialize the Document Object
    text: The `Document` class is Aspose.Words' top‑level object that represents a
      single Word file in memory. After you create a `Document` instance, all further
      operations—such as adding comments—are performed through this object.
  - name: Create and Add a Comment
    text: '`Comment` represents a single user remark attached to a specific location
      in the document. You set properties like `Author`, `Text`, and optionally `DateTime`
      before adding it to the document’s comment collection.'
  - name: Add a Reply to the Comment
    text: A reply is also a `Comment` object, but its `ParentComment` property points
      to the original comment’s ID, establishing a hierarchical thread.
  type: HowTo
- questions:
  - answer: Yes, a valid commercial license is required for production use; a free
      trial is available for evaluation.
    question: Can I use Aspose.Words for comment management in a commercial application?
  - answer: Absolutely. Load the document with `LoadOptions.setPassword("yourPassword")`
      and comment APIs work unchanged.
    question: Does the library support password‑protected Word files?
  - answer: Aspose.Words for Java supports JDK 8 through JDK 21, covering both legacy
      and modern environments.
    question: Which Java versions are compatible with Aspose.Words?
  - answer: Comments are independent of revision tracking; you can retrieve or modify
      them without affecting change history.
    question: How do I handle comments in a DOCX that contains tracked changes?
  - answer: Practically no—Aspose.Words can manage thousands of comments, limited
      only by available memory.
    question: Is there a limit to the number of comments a document can contain?
  type: FAQPage
title: 'Aspose.Words Java: 在 Word 文档中创建批注 – 完整指南'
url: /zh/java/annotations-comments/aspose-words-java-comment-management-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java：在 Word 文档中创建批注 – 完整指南

## 简介
如果您需要以编程方式**在 Word 中创建批注**文档，Aspose.Words for Java 为您提供一个干净、高性能的 API，且无需安装 Microsoft Word。在本教程中，您将学习如何添加批注、附加回复、打印批注线程、删除不需要的回复、将批注标记为已解决，以及获取精确的 UTC 时间戳以实现审计就绪的跟踪。完成后，您将能够将完整的批注管理工作流直接嵌入到您的 Java 应用程序中。

**您将掌握的内容：**
- 如何轻松添加批注和回复  
- 如何打印所有顶层批注及其回复  
- 如何删除批注回复或将批注标记为已完成  
- 如何获取批注创建的 UTC 日期和时间  

准备好提升您的文档自动化能力了吗？让我们先确保您的开发环境已准备就绪。

## 快速答疑
- **如何使用 Java 在 Word 中创建批注？** 使用 `Document` → `Comment` → `Comment.Author` 并调用 `Document.getComments().add(comment)`。  
- **我可以向现有批注添加回复吗？** 是的，创建一个新的 `Comment`，并将原始批注的 `Id` 设为其 `ParentComment`。  
- **如何删除批注回复？** 通过 `Comment.getReplies()` 获取回复，然后调用 `Comment.remove()`。  
- **有没有办法将批注标记为已解决？** 设置 `Comment.setDone(true)`，并可选择更改其颜色。  
- **如何获取批注的精确 UTC 时间戳？** 访问 `Comment.getDateTime()`，它返回 UTC 的 `java.util.Date`。  

## 什么是“在 Word 中创建批注”？
*“Create comment in word”* 指的是使用诸如 Aspose.Words 的 API，以编程方式向 Word 文档的批注集合中插入批注对象。这使得能够实现自动化的审阅周期、审计追踪和协作反馈，而无需手动用户交互。它允许开发者在文档生成期间直接嵌入批注，消除后期手动编辑的需求。

## 为什么使用 Aspose.Words 进行批注管理？
Aspose.Words 支持 **35+** 种输入和输出格式——包括 DOCX、DOC、ODT、PDF、HTML 和 EPUB，并且能够在典型服务器上在 **3 秒** 内处理 **500‑页** 文档。其批注 API 完全离线工作，消除了对 Microsoft Word 的需求，并保证在 Windows、Linux 和 macOS 环境下结果一致。

## 先决条件
- 已安装 Java Development Kit (JDK) 17 或更高版本。  
- 使用 IntelliJ IDEA 或 Eclipse 等 IDE（任意一种均可）。  
- 具备 Java 对象和集合的基本了解。  
- 拥有 Aspose.Words for Java 许可证（免费试用可用于评估）。  

### 设置 Aspose.Words for Java
Aspose.Words 以单个 JAR 包的形式提供，您可以在构建工具中引用它。

**Maven：**  
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```  

**Gradle：**  
```gradle
implementation 'com.aspose:aspose-words:25.3'
```  

#### 获取许可证
Aspose.Words 是商业库，但您可以先使用免费试用或请求临时许可证以获得完整功能访问。访问[购买页面](https://purchase.aspose.com/buy)了解许可选项。

## 如何在 Word 中创建批注？  
加载文档，实例化一个 `Comment` 对象，设置作者和文本，然后将其添加到文档的批注集合——整个流程可以通过三行简洁的 Java 代码实现。API 会自动分配唯一 ID，跟踪插入位置，并以 UTC 存储创建时间戳。

### 步骤 1：初始化 Document 对象  
`Document` 类是 Aspose.Words 的顶层对象，表示内存中的单个 Word 文件。创建 `Document` 实例后，所有后续操作——例如添加批注——都通过该对象执行。  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
```  

### 步骤 2：创建并添加批注  
`Comment` 表示附加在文档特定位置的单个用户备注。您可以在将其添加到文档的批注集合之前设置 `Author`、`Text` 等属性，亦可选地设置 `DateTime`。  
```java
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```  

### 步骤 3：为批注添加回复  
回复也是一个 `Comment` 对象，但其 `ParentComment` 属性指向原始批注的 ID，从而建立层级线程。  
```java
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentWithReply.docx");
```  

## 如何打印 Word 文档中的所有批注？  
`CommentCollection` 是保存文档中所有批注的容器。检索文档的 `CommentCollection`，遍历每个顶层批注，并为每个批注打印其作者、文本和创建日期；随后遍历其 `Replies` 集合以显示嵌套反馈。此方法可在一次遍历中提供所有审阅注释的完整、可读快照。

### 步骤 1：加载文档  
```java
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/Comments.docx");
```  

### 步骤 2：检索并打印批注  
```java
NodeCollection<Comment> comments = doc.getChildNodes(NodeType.COMMENT, true);
for (Comment comment : (Iterable<Comment>) comments) {
    if (comment.getAncestor() == null) {
        System.out.println("Top-level comment:");
        System.out.println("\t" + comment.getText().trim() + ", by " + comment.getAuthor());
        for (Comment reply : comment.getReplies()) {
            System.out.println("\t" + reply.getText().trim() + ", by " + reply.getAuthor());
        }
    }
}
```  

## 如何删除批注回复？  
通过父批注的 `Replies` 列表中的索引确定要删除的回复，然后在该回复对象上调用 `remove()`。如果需要清除所有回复，只需清空 `Replies` 集合。您还可以在删除前按作者或日期过滤回复，以保持审计完整性。

### 步骤 1：初始化并添加带回复的批注  
```java
Document document = new Document();
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
comment.addReply("Joe Bloggs", "J.B.", new Date(), "Another reply");
```  

### 步骤 2：删除回复  
```java
comment.removeReply(comment.getReplies().get(0)); // Remove one reply
comment.removeAllReplies(); // Remove all remaining replies
```  

## 如何将批注标记为已完成？  
`Done` 是一个布尔属性，指示批注是否已解决。将 `Comment` 实例的 `Done` 标志设为 `true`；当文档在 Word 中打开时，Aspose.Words 会以可视的“已解决”样式（通常为绿色对勾）呈现该批注。此状态可在后续程序中检查，以生成未解决反馈的报告。

### 步骤 1：创建文档并添加批注  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
documentBuilder.writeln("Hello world!");
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("Fix the spelling error!");
```  

### 步骤 2：将批注标记为已完成  
```java
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
document.getFirstSection().getBody().getFirstParagraph().getRuns().get(0).setText("Hello world!");
comment.setDone(true);
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentDone.docx");
```  

## 如何从批注获取 UTC 日期和时间？  
`Comment.getDateTime()` 返回批注的 UTC 创建时间戳。创建批注时，Aspose.Words 会自动以 UTC 存储创建时间。通过 `Comment.getDateTime()` 访问它，并根据日志或合规报告的需要进行格式化。您可以将返回的 `java.util.Date` 转换为 ISO‑8601 字符串或 `java.time.Instant`，以实现跨系统的一致处理。

### 步骤 1：创建带时间戳的批注文档  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
Date dateTime = new Date();
Comment comment = new Comment(document, "John Doe", "J.D.", dateTime);
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```  

### 步骤 2：保存并检索 UTC 日期  
```java
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Comment currentComment = (Comment) doc.getChild(NodeType.COMMENT, 0, true);
assert currentComment.getDateTimeUtc().toString() == dateTime.toString();
```  

## 实际应用
了解并使用这些批注管理功能可以显著提升许多实际场景中的文档工作流：

- **协作编辑：** 团队可以在文件内部直接留下线程化反馈，自动化流程可以提取或解决批注，无需人工干预。  
- **文档审阅流水线：** 法务或编辑部门可以以编程方式标记未解决的批注，生成审阅报告，并强制执行合规截止日期。  
- **审计追踪：** 通过导出 UTC 时间戳，组织能够满足可追溯性和版本控制的监管要求。  

这些功能可平滑集成到内容管理系统、CI/CD 流水线或自定义文档生成服务中。

## 性能考虑因素
处理大量 Word 文件时，请牢记以下最佳实践：

- **批量处理：** 将批注加载并处理在 ≤ 200 份文档的批次中，以避免过度的内存消耗。  
- **惰性加载：** 仅在确实需要批注数据时，使用 `Document.load(..., LoadOptions)` 并将 `LoadOptions.setLoadComments(true)` 设置为 true。  
- **资源清理：** 显式调用 `document.dispose()`（或依赖 try‑with‑resources）及时释放本机资源。  

遵循这些提示可确保即使是 **1,000‑页** 文档也能在普通服务器硬件上高效处理。

## 常见问题及解决方案
| 问题 | 原因 | 解决方案 |
|-------|-------|----------|
| **访问 `Comment.getReplies()` 时的 NullPointerException** | 文档加载时禁用了批注。 | 通过 `LoadOptions.setLoadComments(true)` 启用批注加载。 |
| **时间戳不正确（本地时间而非 UTC）** | 手动使用本地 `Date` 调用 `Comment.setDateTime()`。 | 使用 `new Date()`，Aspose.Words 会将其存储为 UTC，或使用 `Instant.now()` 进行转换。 |
| **在 Microsoft Word 中未显示回复** | 缺少父批注 ID 的关联。 | 在添加回复之前，确保调用 `reply.setParentCommentId(parent.getId())`。 |

## 常见问题

**Q: 我可以在商业应用中使用 Aspose.Words 进行批注管理吗？**  
A: 是的，生产使用需要有效的商业许可证；免费试用可用于评估。

**Q: 该库是否支持受密码保护的 Word 文件？**  
A: 当然支持。使用 `LoadOptions.setPassword("yourPassword")` 加载文档，批注 API 正常工作。

**Q: 哪些 Java 版本与 Aspose.Words 兼容？**  
A: Aspose.Words for Java 支持 JDK 8 到 JDK 21，覆盖传统和现代环境。

**Q: 如何处理包含修订痕迹的 DOCX 中的批注？**  
A: 批注与修订跟踪相互独立；您可以检索或修改批注而不影响更改历史。

**Q: 文档中可以包含的批注数量是否有限制？**  
A: 实际上没有——Aspose.Words 能管理成千上万的批注，唯一限制是可用内存。

---

**最后更新：** 2026-06-12  
**测试环境：** Aspose.Words for Java 24.12  
**作者：** Aspose  

{{< blocks/products/products-backtop-button >}}

## 相关教程

- [使用 Aspose.Words Java 跟踪 Word 文档中的更改：文档修订完整指南](/words/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)
- [精通 Aspose.Words for Java：如何在 Word 文档中插入和管理书签](/words/java/content-management/aspose-words-java-manage-bookmarks/)
- [Aspose.Words Java：Word 文档处理综合指南](/words/java/document-operations/aspose-words-java-master-word-processing/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}