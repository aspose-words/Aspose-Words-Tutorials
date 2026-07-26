---
date: '2026-07-26'
description: 了解如何使用 Aspose.Words for Java 管理 Word 文档中的批注。提供添加、打印、删除以及标记批注为已完成的清晰代码示例。
keywords:
- Aspose.Words Java
- comment management in Word documents
- managing comments with Aspose.Words
lastmod: '2026-07-26'
og_description: 了解如何使用 Aspose.Words for Java 管理 Word 文档中的批注。提供添加、打印、删除以及标记批注为已完成的清晰代码示例。
og_image_alt: 'Developer guide: Managing Word comments with Aspose.Words Java'
og_title: 使用 Aspose.Words Java 管理 Word 文档批注的方法
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Learn how to manage comments in Word documents using Aspose.Words for
    Java. Add, print, delete, and mark comments as done with clear code examples.
  headline: How to Manage Comments in Word Docs with Aspose.Words Java
  type: TechArticle
- questions:
  - answer: A free trial works for evaluation, but a valid license is required for
      production to remove evaluation limits.
    question: Can I use Aspose.Words without a license in production?
  - answer: Yes—load the document with a `LoadOptions` object that includes the password.
    question: Does Aspose.Words support password‑protected Word files?
  - answer: The library can manage tens of thousands of comments; performance depends
      on available memory and document size.
    question: What is the maximum number of comments Aspose.Words can handle?
  - answer: By default, Aspose.Words records comment dates in UTC, ensuring consistent
      cross‑time‑zone reporting.
    question: Are comment timestamps always stored in UTC?
  - answer: Call `document.getComments().remove(comment)`; this removes the comment
      and all its replies in one operation.
    question: How do I delete an entire comment thread?
  type: FAQPage
tags:
- how to manage comments
- add comment java
- print word comments
- delete word comment
- java document comments
title: 使用 Aspose.Words Java 管理 Word 文档批注的方法
url: /zh/java/annotations-comments/aspose-words-java-comment-management-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/products-backtop-button >}}

# 如何使用 Aspose.Words Java 管理 Word 文档中的批注

以编程方式管理批注一直是依赖 Word 协作的团队的痛点。在本指南中，您将了解 **如何高效管理批注**，包括添加、打印、删除以及标记为已解决，全部无需打开 Word。本指南结束后，您将拥有一套完整的工具箱，用于自动化文档审阅流程。

## 快速答案
- **第一步是什么？** 将 Word 文件加载到 `Document` 对象中。  
- **我可以给批注添加回复吗？** 可以——使用 `Comment.getReplies().add()` 方法。  
- **如何列出所有批注？** 遍历 `Document.getComments()` 并打印每个批注的文本。  
- **可以将批注标记为完成吗？** 设置 `Comment.setDone(true)` 标志。  
- **如何获取批注的时间戳？** 调用 `Comment.getDateTime()`，它返回 UTC 的 `DateTime` 对象。

## 什么是 Word 文档中的批注管理？
批注管理是指在 Word 文件内部以编程方式创建、检索、修改和删除批注对象。它支持自动化审阅工作流、审计轨迹生成以及与问题跟踪系统的集成，免去在 Microsoft Word 中手动编辑的需求。

## 为什么使用 Aspose.Words for Java 来管理批注？
Aspose.Words 支持 **35+ 种文件格式**，可处理高达 **2,000 页** 的文档，同时内存占用保持在 150 MB 以下。其纯 Java 引擎可在任何平台运行，无需 Microsoft Word，提供确定性的性能，并可完全控制批注元数据，如作者、时间戳和解决状态。

## 前置条件
- 已安装 Java Development Kit (JDK) 17 或更高版本。  
- 使用 IntelliJ IDEA 或 Eclipse 等 IDE。  
- 使用 Maven 或 Gradle 进行依赖管理。  

### 设置 Aspose.Words for Java
Aspose.Words 以单个 JAR 包形式提供。将与您的构建系统匹配的依赖添加进去。

**Maven:**  
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```  

**Gradle:**  
```gradle
implementation 'com.aspose:aspose-words:25.3'
```  

#### 许可证获取
Aspose.Words 是商业产品，但您可以先使用免费试用版或临时许可证来获取完整功能。访问 [purchase page](https://purchase.aspose.com/buy) 了解授权选项。

## 如何添加带回复的批注？
Document 表示已加载到内存中的 Word 文件。  
Comment 是存储单个批注数据的对象。

**直接回答（40‑70 字）：**  
创建 `Document` 实例，调用 `document.getComments().add(author, initials, text, date)` 添加顶层批注，然后使用 `comment.getReplies().add(replyAuthor, replyInitials, replyText, replyDate)` 附加回复。API 会自动将回复关联到父批注，并在保存文档时一起持久化。

### 步骤 1：初始化 Document 对象
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
```  

### 步骤 2：创建并添加批注
```java
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```  

### 步骤 3：为批注添加回复
```java
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentWithReply.docx");
```  

## 如何打印所有批注及其回复？
Document 提供对 Word 文件中完整批注集合的访问。

**直接回答（40‑70 字）：**  
遍历 `document.getComments()`；对每个批注，打印作者、文本和时间戳。随后循环 `comment.getReplies()`，输出每条回复的详细信息。此嵌套遍历可在不加载额外文档部分的情况下，完整展示讨论层级。

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
`Comment.getReplies()` 返回可变的回复对象集合。

**直接回答（40‑70 字）：**  
定位目标批注，对特定回复调用 `comment.getReplies().remove(reply)`，或使用 `comment.getReplies().clear()` 删除全部回复。删除后保存文档，批注层级将相应更新。

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
Comment 表示单个批注节点，并包含 “done” 标志。

**直接回答（40‑70 字）：**  
对目标批注对象调用 `Comment.setDone(true)` 属性。保存后，Word 中的批注会显示 “Done” 勾选，表示问题已解决。以后可通过 `comment.isDone()` 查询已解决与未解决的批注。

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

## 如何获取批注的 UTC 日期和时间？
Comment 将创建日期存储为 UTC 时间戳。

**直接回答（40‑70 字）：**  
创建批注时，向构造函数传入 UTC 的 `java.util.Date`（或 `java.time.OffsetDateTime`）。随后使用 `comment.getDateTime()` 获取存储的 UTC 时间戳。该值可进行格式化或存入数据库，以实现精确的变更追踪。

### 步骤 1：创建带时间戳的批注文档
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
Date dateTime = new Date();
Comment comment = new Comment(document, "John Doe", "J.D.", dateTime);
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```  

### 步骤 2：保存并获取 UTC 日期
```java
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Comment currentComment = (Comment) doc.getChild(NodeType.COMMENT, 0, true);
assert currentComment.getDateTimeUtc().toString() == dateTime.toString();
```  

## 实际应用场景
掌握并运用这些批注管理功能可以显著提升工作流：

- **协同编辑：** 团队可自动插入审阅备注和回复，减少手动工作量。  
- **文档审阅自动化：** 为合规审计生成所有批注的汇总报告。  
- **反馈管理：** 将批注时间戳存入集中仓库，以跟踪响应时长。

## 性能考虑
在处理大型合同或手册时，请注意以下建议：

- 将批注分批处理，而不是一次性加载完整批注树到内存。  
- 对多个操作复用同一个 `Document` 实例，以降低 GC 压力。  
- 升级至最新的 Aspose.Words 版本，以获取内部内存优化补丁。

## 结论
现在，您已经了解 **如何使用 Aspose.Words for Java 管理 Word 文档中的批注**——包括添加、回复、打印、删除、标记为完成以及提取 UTC 时间戳。将这些模式应用于构建稳健的文档审阅流水线、与内容管理系统集成，或创建自定义审计工具。

**后续步骤：**  
- 试验条件批注过滤（例如，仅显示未解决的批注）。  
- 将批注数据与外部问题跟踪 API 结合，实现端到端工作流自动化。

## 常见问题

**问：可以在生产环境中不使用许可证使用 Aspose.Words 吗？**  
答：免费试用版仅用于评估，生产环境必须使用有效许可证以移除评估限制。

**问：Aspose.Words 是否支持受密码保护的 Word 文件？**  
答：是的——使用包含密码的 `LoadOptions` 对象加载文档即可。

**问：Aspose.Words 能处理的最大批注数量是多少？**  
答：库可以管理数万条批注；性能取决于可用内存和文档大小。

**问：批注时间戳是否始终以 UTC 存储？**  
答：默认情况下，Aspose.Words 会以 UTC 记录批注日期，确保跨时区报告的一致性。

**问：如何删除整个批注线程？**  
答：调用 `document.getComments().remove(comment)`；此操作会一次性删除该批注及其所有回复。

---

**最后更新：** 2026-07-26  
**测试环境：** Aspose.Words for Java 24.12  
**作者：** Aspose  

{{< blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

## 相关教程

- [Master Aspose.Words for Java&#58; How to Insert and Manage Bookmarks in Word Documents](/words/java/content-management/aspose-words-java-manage-bookmarks/)
- [Track Changes in Word Documents Using Aspose.Words Java&#58; A Complete Guide to Document Revisions](/words/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)
- [Hyperlink Management in Word Using Aspose.Words Java&#58; A Comprehensive Guide](/words/java/content-management/master-hyperlink-management-word-aspose-words-java/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-wrap-class >}}