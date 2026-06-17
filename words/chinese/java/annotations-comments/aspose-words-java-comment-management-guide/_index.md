---
date: '2026-06-17'
description: 了解如何使用 Aspose.Words 在 Java 中添加批注，并在高效打印 Word 文档批注的同时管理回复、删除和时间戳。
keywords:
- how to add comment java
- print word document comments
- Aspose.Words comment management
- Java Word API
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Learn how to add comment java with Aspose.Words, and print word document
    comments efficiently while managing replies, removal, and timestamps.
  headline: 'How to Add Comment Java: Aspose.Words Comment Management Guide'
  type: TechArticle
- description: Learn how to add comment java with Aspose.Words, and print word document
    comments efficiently while managing replies, removal, and timestamps.
  name: 'How to Add Comment Java: Aspose.Words Comment Management Guide'
  steps:
  - name: Initialize the Document Object
    text: The `Document` class is Aspose.Words' top‑level object that represents a
      single Word file in memory.
  - name: Create and Add a Comment
    text: '`Comment` represents a single comment node attached to a run of text.'
  - name: Add a Reply to the Comment
    text: '`Comment.getReplies()` returns a collection that you can populate with
      additional `Comment` objects.'
  - name: Load the Document
    text: The `Document` class loads the file and parses its comment tree.
  - name: Retrieve and Print Comments
    text: '`CommentCollection` provides indexed access to each top‑level comment.'
  - name: Initialize and Add Comments with Replies
    text: '`DocumentBuilder` helps you insert comments and replies in a single pass.'
  - name: Remove Replies
    text: '`Comment.getReplies().clear()` removes every reply attached to the comment.'
  - name: Create a Document and Add a Comment
    text: '`DocumentBuilder` inserts the initial comment that we will later resolve.'
  - name: Mark the Comment as Done
    text: '`comment.setDone(true)` updates the comment’s status to resolved.'
  - name: Create a Document with a Timestamped Comment
    text: When you add a comment, Aspose.Words automatically records the UTC timestamp.
  type: HowTo
- questions:
  - answer: Aspose.Words for Java is a fully managed API that lets you create, edit,
      convert, and render Word documents without Microsoft Word installed.
    question: What is Aspose.Words for Java?
  - answer: Add the Maven or Gradle dependency shown in the “Setting Up Aspose.Words
      for Java” section, then refresh your project.
    question: How do I install Aspose.Words for my project?
  - answer: Yes, a temporary trial license works for evaluation, but it adds evaluation
      watermarks and limits some features.
    question: Can I use Aspose.Words without a license?
  - answer: Forgetting to call `document.save()` after modifications, or attempting
      to access a comment that has been removed, can cause `NullPointerException`s.
    question: What are common pitfalls when managing comments?
  - answer: Use the `Revision` API together with comment timestamps to build a change‑log
      that spans many files.
    question: How do I track changes across multiple documents?
  type: FAQPage
title: 如何在 Java 中添加批注：Aspose.Words 批注管理指南
url: /zh/java/annotations-comments/aspose-words-java-comment-management-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Java 中添加评论：Aspose.Words 评论管理指南

## 介绍
在 Word 文档中以编程方式管理评论可能具有挑战性，尤其是在协作环境中需要 **how to add comment java** 时。本教程将逐步演示如何添加、打印、删除以及标记评论为已完成，并获取 UTC 时间戳以进行精确跟踪。完成后，您将能够熟练处理 Aspose.Words for Java 中的所有常见评论相关场景。

**您将学习：**
- 轻松添加评论和回复
- 打印所有顶层评论及其回复
- 删除评论回复或将评论标记为已完成
- 检索评论的 UTC 日期和时间以进行精确跟踪

准备好提升文档自动化工作流了吗？让我们先确认前置条件。

## 快速答案
- **在 Java 中如何添加评论？** 使用 `DocumentBuilder` 插入 `Comment` 对象，然后调用 `Comment.getReplies().add(...)` 添加回复。  
- **我可以打印所有评论吗？** 遍历 `doc.getComments()` 并输出每条评论的文本和作者。  
- **有没有办法将评论标记为已解决？** 设置 `Comment.setDone(true)` 将其标记为已完成。  
- **如何获取评论的时间戳？** 访问 `Comment.getDateTime()`，它返回 UTC 的 `java.util.Date`。  
- **这些功能需要许可证吗？** 是的，有效的 Aspose.Words 许可证可解锁完整的评论管理功能。

## 什么是 how to add comment java？
**how to add comment java** 指的是使用 Aspose.Words API for Java 以编程方式向 Word 文档插入评论的过程。此功能实现了无需手动编辑的自动化审阅工作流。通过使用该 API，您可以在代码中创建、回复和管理评论，从而实现与文档处理流水线和版本控制系统的无缝集成。

## 为什么使用 Aspose.Words 进行评论管理？
Aspose.Words 支持 **35+** 种输入和输出格式——包括 DOCX、PDF、HTML 和 ODT，并且能够在普通服务器硬件上在 **3 秒** 内处理 **500 页** 的文档。其评论 API 完全在内存中运行，无需安装 Microsoft Word。

## 前置条件
- 已安装 Java Development Kit (JDK) 8 或更高版本
- 熟悉 Java 语法和面向对象概念
- 使用 IntelliJ IDEA 或 Eclipse 等 IDE
- 拥有 Aspose.Words for Java 许可证（试用版可用于评估）

### 设置 Aspose.Words for Java
Aspose.Words 通过 Maven Central 和 NuGet 分发。请在项目中加入与您的构建系统匹配的依赖。

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
Aspose.Words 是商业库，但您可以使用免费试用或申请临时许可证以获取全部功能。访问 [purchase page](https://purchase.aspose.com/buy) 了解授权选项。

## 实施指南
本节将对每个评论管理功能进行分解，并提供清晰、可操作的步骤。

### 如何添加评论 java？
`Document` 类表示加载到内存中的 Word 文件。  
`DocumentBuilder` 类提供用于导航和编辑文档内容的方法。  
`Comment` 类表示附加到 Word 文档文本范围的评论节点。

**直接答案：**  
实例化一个 `Document` 对象，使用 `DocumentBuilder` 定位光标，调用 `builder.insertComment("Author", "Initial comment")`，然后使用 `comment.getReplies().add(new Comment("Reply author", "Reply text"))` 添加回复。这样即可在几行代码内创建完整的评论线程。

#### 步骤 1：初始化 Document 对象
`Document` 类是 Aspose.Words 的顶层对象，表示内存中的单个 Word 文件。  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
```

#### 步骤 2：创建并添加评论
`Comment` 表示附加到一段文本的单个评论节点。  
```java
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```

#### 步骤 3：为评论添加回复
`Comment.getReplies()` 返回一个集合，您可以向其中填充额外的 `Comment` 对象。  
```java
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentWithReply.docx");
```

### 如何打印 Word 文档评论？
`Document` 类保存 Word 文件的内容和结构，包括其评论。  
`CommentCollection` 类提供对文档中每个顶层评论的索引访问。

**直接答案：**  
遍历 `doc.getComments()`，输出每条评论的作者、文本和时间戳，然后循环 `comment.getReplies()` 显示回复详情。这样即可获得文档中所有反馈的完整、可读快照。

#### 步骤 1：加载文档
`Document` 类加载文件并解析其评论树。  
```java
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/Comments.docx");
```

#### 步骤 2：检索并打印评论
`CommentCollection` 提供对每个顶层评论的索引访问。  
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

### 如何删除评论回复？
`Comment` 类表示评论及其关联的回复。

**直接答案：**  
调用 `comment.getReplies().clear()` 删除所有回复，或使用 `comment.getReplies().removeAt(index)` 删除特定回复。修改后，保存文档以持久化更改。

#### 步骤 1：初始化并添加带回复的评论
`DocumentBuilder` 帮助您一次性插入评论和回复。  
```java
Document document = new Document();
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
comment.addReply("Joe Bloggs", "J.B.", new Date(), "Another reply");
```

#### 步骤 2：删除回复
`Comment.getReplies().clear()` 删除附加到该评论的所有回复。  
```java
comment.removeReply(comment.getReplies().get(0)); // Remove one reply
comment.removeAllReplies(); // Remove all remaining replies
```

### 如何将评论标记为已完成？
`Comment` 类包含 `setDone` 方法，用于将评论标记为已解决。

**直接答案：**  
对目标 `Comment` 对象调用 `comment.setDone(true)`。此标记会存储在 Word 文件中，并在 Microsoft Word 中显示为“已完成”复选标记。

#### 步骤 1：创建文档并添加评论
`DocumentBuilder` 插入我们稍后将解决的初始评论。  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
documentBuilder.writeln("Hello world!");
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("Fix the spelling error!");
```

#### 步骤 2：将评论标记为已完成
`comment.setDone(true)` 更新评论的状态为已解决。  
```java
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
document.getFirstSection().getBody().getFirstParagraph().getRuns().get(0).setText("Hello world!");
comment.setDone(true);
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentDone.docx");
```

### 如何获取评论的 UTC 日期和时间？
`Comment.getDateTime()` 方法返回一个 `java.util.Date` 对象，表示评论的 UTC 创建时间。

**直接答案：**  
访问 `comment.getDateTime()`，它返回 UTC 的 `java.util.Date`。您可以使用 `SimpleDateFormat` 并设置 `UTC` 时区进行显示或记录。

#### 步骤 1：创建带时间戳的评论文档
添加评论时，Aspose.Words 会自动记录 UTC 时间戳。  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
Date dateTime = new Date();
Comment comment = new Comment(document, "John Doe", "J.D.", dateTime);
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```

#### 步骤 2：保存并检索 UTC 日期
`comment.getDateTime()` 提供评论创建的确切时刻。  
```java
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Comment currentComment = (Comment) doc.getChild(NodeType.COMMENT, 0, true);
assert currentComment.getDateTimeUtc().toString() == dateTime.toString();
```

## 实际应用
理解并运用这些功能可以显著提升各种场景下的文档管理：

- **协作编辑：** 团队可以直接在文档中留下结构化反馈，您的自动化程序可以以编程方式汇总或解决评论。  
- **文档审阅流水线：** 自动化 QA 过程可以在发布前标记未解决的评论。  
- **审计追踪：** UTC 时间戳为合规性要求高的行业提供可靠的审计日志。

这些功能可平滑集成到内容管理系统、CI/CD 流水线或自定义审阅工具中。

## 性能考虑
在处理包含大量评论的大型 Word 文件（数百页）时，请注意以下技巧：

- 将评论分批处理，以避免一次性将整个评论树加载到内存。  
- 如需在保留原始文件的同时进行操作，可使用 `Document.clone()` 创建副本。  
- 升级到最新的 Aspose.Words 版本，以获得内存优化和多线程处理的增强功能。

## 结论
您现在拥有了完整的 **how to add comment java** 工具箱，可使用 Aspose.Words 管理评论的完整生命周期。掌握这些 API 后，您可以自动化审阅周期、强化合规性，并构建更智能的文档处理解决方案。

**后续步骤**
- 尝试按作者或日期过滤评论。  
- 将评论管理与 Aspose.Words 的其他功能（如邮件合并或文档转换）结合使用。  
- 查阅 Aspose.Words API 参考，了解自定义评论样式等高级场景。

## 常见问题

**问：什么是 Aspose.Words for Java？**  
答：Aspose.Words for Java 是一个完全托管的 API，允许您在未安装 Microsoft Word 的情况下创建、编辑、转换和呈现 Word 文档。

**问：如何为我的项目安装 Aspose.Words？**  
答：在 “设置 Aspose.Words for Java” 部分添加示例的 Maven 或 Gradle 依赖，然后刷新项目。

**问：可以在没有许可证的情况下使用 Aspose.Words 吗？**  
答：可以，临时试用许可证可用于评估，但会添加评估水印并限制某些功能。

**问：管理评论时常见的陷阱有哪些？**  
答：修改后忘记调用 `document.save()`，或尝试访问已被删除的评论，可能导致 `NullPointerException`。

**问：如何跨多个文档跟踪更改？**  
答：结合 `Revision` API 与评论时间戳，构建跨文件的更改日志。

---

**Last Updated:** 2026-06-17  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< blocks/products/products-backtop-button >}}

## Related Tutorials

- [Hyperlink Management in Word Using Aspose.Words Java: A Comprehensive Guide](/words/java/content-management/master-hyperlink-management-word-aspose-words-java/)
- [Track Changes in Word Documents Using Aspose.Words Java: A Complete Guide to Document Revisions](/words/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)
- [Aspose.Words Java: Comprehensive Guide to Word Document Processing](/words/java/document-operations/aspose-words-java-master-word-processing/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}