---
date: '2026-07-21'
description: 了解如何使用 Aspose.Words for Java 添加、打印、删除评论并将其标记为已完成，以及在 Word 文档中检索 UTC 时间戳。
keywords:
- how to use aspose
- add comment java
- print word comments
- Aspose.Words Java
- comment management
lastmod: '2026-07-21'
og_description: 探索如何使用 Aspose.Words Java 添加、打印、删除评论并将其标记为已完成，以及在 Word 文档中检索 UTC 时间戳。
og_image_alt: 'Developer guide: Manage Word comments with Aspose.Words Java'
og_title: 如何使用 Aspose.Words Java 进行评论管理
schemas:
- author: Aspose
  dateModified: '2026-07-21'
  description: Learn how to use Aspose.Words for Java to add, print, remove, and mark
    comments as done, plus retrieve UTC timestamps in Word documents.
  headline: How to Use Aspose.Words Java for Comment Management
  type: TechArticle
- questions:
  - answer: Aspose.Words for Java is a library that enables developers to create,
      edit, convert, and render Word documents programmatically without requiring
      Microsoft Word.
    question: What is Aspose.Words for Java?
  - answer: A temporary license or free trial works for development and testing; a
      full license is required for production deployments.
    question: Do I need a license to run the examples?
  - answer: Yes—load the document with the appropriate password, then use the same
      comment APIs once the file is opened.
    question: Can I add comments to password‑protected documents?
  - answer: The library handles comments in all Word formats (DOC, DOCX, DOCM, DOT,
      DOTX, DOTM) and preserves them when converting to PDF, HTML, or images.
    question: How many comment formats does Aspose.Words support?
  - answer: Practically, you can manage thousands of comments; performance depends
      on document size and available memory.
    question: Is there a limit to the number of comments I can process?
  type: FAQPage
tags:
- comment management
- Aspose.Words
- Java document processing
- add comment java
- print word comments
title: 如何使用 Aspose.Words Java 进行评论管理
url: /zh/java/annotations-comments/aspose-words-java-comment-management-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words Java 进行评论管理

以编程方式管理 Word 文档中的评论可能像在迷宫中穿行，尤其是当你需要添加回复、解决问题或追踪反馈留下的时间时。**How to use Aspose** 让这变得简单：Aspose.Words for Java 库提供了简洁的 API，能够添加、打印、删除评论并将其标记为完成，还能获取精确的 UTC 时间戳。在本指南中，我们将逐步演示每项功能，帮助你在 Java 应用程序中嵌入强大的评论处理。

## 快速答案
- **什么库在 Java 中处理 Word 评论？** Aspose.Words for Java.
- **我可以为评论添加回复吗？** 是的 – 使用 `Comment.getReplies().add(...)`。
- **如何打印所有评论？** 遍历 `doc.getComments()` 并输出每条评论的文本。
- **是否可以将评论标记为已完成？** 设置 `Comment.setDone(true)`。
- **如何获取评论的 UTC 时间戳？** 调用 `Comment.getDateTime().toInstant()`。

## 什么是 “how to use aspose”？
**“how to use aspose”** 指的是开发者在代码库中集成 Aspose 库（如 Aspose.Words for Java）以完成文档操作任务的实际步骤。通过下面的示例，你将看到如何利用 API 进行评论管理。

## 为什么在评论处理时使用 Aspose.Words？
Aspose.Words 支持 **35+** 种输入和输出格式——包括 DOCX、PDF、HTML 和 ODT，并且能够在普通服务器硬件上在 **3 秒** 内处理 **500 页** 文档，且无需 Microsoft Word。这种性能加上丰富的评论 API，消除了手动 XML 解析或第三方工具的需求。

## 前置条件
- 已安装 Java Development Kit (JDK 8 或更高)。
- 使用 IntelliJ IDEA 或 Eclipse 等 IDE。
- 使用 Maven 或 Gradle 进行依赖管理。
- 有效的 Aspose.Words 许可证（提供免费试用）。

### 设置 Aspose.Words for Java
在项目中引入库：

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
Aspose.Words 是商业产品，但你可以先使用免费试用或申请临时许可证以获得全部功能。访问 [purchase page](https://purchase.aspose.com/buy) 了解授权选项。

## 如何使用 Aspose.Words for Java 添加带回复的评论？
要插入评论及其后续回复，首先加载或创建一个 `Document`，然后使用 `DocumentBuilder` 将光标定位到需要添加评论的位置。创建包含作者信息和文本的 `Comment` 对象，将其加入文档，最后将 `Comment` 回复附加到原始评论上。此顺序确保反馈以层级结构存储在文件中。

`Document` 类表示内存中加载的 Word 文档。  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
```  

## 如何在 Word 文档中打印所有评论及其回复？
要显示每条评论及其嵌套回复，加载目标文档并遍历其 `CommentCollection`。对于每个顶层评论，输出作者、文本和创建日期，然后遍历其 `Replies` 集合打印每条回复的详细信息。此方法可完整、可读地呈现文件中所有反馈。

`Document` 类表示内存中加载的 Word 文档。  
```java
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/Comments.docx");
```  

## 如何在 Aspose.Words for Java 中删除评论回复？
要删除评论回复，首先从文档的评论集合中获取父 `Comment` 对象。你可以清空整个 `Replies` 列表以删除所有嵌套反馈，或通过索引定位特定回复并调用 `remove` 方法。此清理有助于在审阅后保持文档简洁。

`Document` 类表示内存中加载的 Word 文档。  
```java
Document document = new Document();
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
comment.addReply("Joe Bloggs", "J.B.", new Date(), "Another reply");
```  

## 如何在 Word 文档中将评论标记为已完成？
将评论标记为已完成表示该问题已得到处理。从文档中获取目标 `Comment`，然后调用其 `setDone(true)` 方法。标记后，支持的查看器会以可视指示显示已解决的评论，帮助审阅者快速识别已处理项。

`Document` 类表示内存中加载的 Word 文档。  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
documentBuilder.writeln("Hello world!");
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("Fix the spelling error!");
```  

## 如何获取评论的 UTC 日期和时间？
每条评论都会存储其创建的确切时刻。加载文档后，访问 `Comment` 对象并调用 `getDateTime()` 方法，返回 `DateTime` 值。使用 `toInstant()` 将该值转换为 UTC，以获得适用于日志或审计的时区无关时间戳。

`Document` 类表示内存中加载的 Word 文档。  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
Date dateTime = new Date();
Comment comment = new Comment(document, "John Doe", "J.D.", dateTime);
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```  

## 实际应用
了解并使用这些评论管理功能可以显著提升文档工作流：

- **协作编辑：** 团队可以在 Word 文件内留下线程式反馈，无需离开文档。
- **文档审阅自动化：** 将评论导出为 CSV 或与问题追踪系统集成。
- **审计与合规：** UTC 时间戳提供了不可篡改的反馈记录。

这些功能可平滑集成到内容管理平台、自动化报告管道或自定义审阅工具中。

## 性能考虑
处理大型 Word 文件（数百页）时请注意以下技巧：

- 将评论分批处理，而不是一次性加载完整的评论树。
- 对多个操作复用同一个 `Document` 实例，以降低内存开销。
- 升级到最新的 Aspose.Words 版本，以获得性能优化和错误修复。

## 结论
现在你已经了解 **如何使用 Aspose.Words Java** 来添加、打印、删除、解决以及为 Word 文档中的评论打上时间戳。将这些模式整合到你的应用程序中，可简化协作并保持清晰的审计轨迹。

**下一步：**  
- 试验按作者或日期过滤评论。  
- 将评论处理与文档保护功能相结合，实现安全的审阅周期。  

准备好将这些技术投入生产了吗？立即开始编码，观看你的文档审阅过程变得更加高效。

## 常见问题

**Q: 什么是 Aspose.Words for Java？**  
A: Aspose.Words for Java 是一个库，允许开发者在不依赖 Microsoft Word 的情况下，以编程方式创建、编辑、转换和渲染 Word 文档。

**Q: 运行示例是否需要许可证？**  
A: 开发和测试阶段可使用临时许可证或免费试用；生产部署则需要正式许可证。

**Q: 我可以向受密码保护的文档添加评论吗？**  
A: 可以——使用相应的密码加载文档后，即可使用相同的评论 API。

**Q: Aspose.Words 支持多少种评论格式？**  
A: 该库在所有 Word 格式（DOC、DOCX、DOCM、DOT、DOTX、DOTM）中处理评论，并在转换为 PDF、HTML 或图像时保留它们。

**Q: 处理评论的数量有没有限制？**  
A: 实际上可以管理成千上万条评论；性能取决于文档大小和可用内存。

---

**最后更新：** 2026-07-21  
**测试环境：** Aspose.Words for Java 24.12  
**作者：** Aspose

```java
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```

```java
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentWithReply.docx");
```

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

```java
comment.removeReply(comment.getReplies().get(0)); // Remove one reply
comment.removeAllReplies(); // Remove all remaining replies
```

```java
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
document.getFirstSection().getBody().getFirstParagraph().getRuns().get(0).setText("Hello world!");
comment.setDone(true);
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentDone.docx");
```

```java
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Comment currentComment = (Comment) doc.getChild(NodeType.COMMENT, 0, true);
assert currentComment.getDateTimeUtc().toString() == dateTime.toString();
```

## 相关教程

- [掌握 Aspose.Words for Java：在 Word 文档中插入和管理书签](/words/java/content-management/aspose-words-java-manage-bookmarks/)
- [使用 Aspose.Words Java 跟踪 Word 文档更改：文档修订完整指南](/words/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)
- [Aspose.Words Java：Word 文档处理全面指南](/words/java/document-operations/aspose-words-java-master-word-processing/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}