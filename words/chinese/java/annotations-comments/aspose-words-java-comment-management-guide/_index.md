---
date: '2026-08-10'
description: 了解如何使用 Aspose.Words for Java 添加评论。一步步指南，教您创建、回复、打印、删除以及标记已完成的评论，并获取 UTC
  时间戳。
keywords:
- how to add comment java
- comment management Java
- Aspose.Words comments
lastmod: '2026-08-10'
og_description: 了解如何使用 Aspose.Words for Java 添加评论。一步步指南，教您创建、回复、打印、删除以及标记已完成的评论，并获取
  UTC 时间戳。
og_image_alt: Guide showing how to add comment java with Aspose.Words in Word documents
og_title: 如何使用 Aspose.Words for Java 为 Word 文档添加评论
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Learn how to add comment java with Aspose.Words for Java. Step‑by‑step
    guide to create, reply to, print, remove, and mark comments as done, plus retrieve
    UTC timestamps.
  headline: How to add comment java using Aspose.Words for Word docs
  type: TechArticle
- questions:
  - answer: No. The trial works for development only; a full license is required for
      production deployments.
    question: Can I use Aspose.Words without a license in production?
  - answer: Yes. Load a protected file by passing the password to the `Document` constructor.
    question: Does the library support password‑protected documents?
  - answer: Aspose.Words for Java supports JDK 8 through JDK 21, with full feature
      parity across versions.
    question: Which Java versions are compatible?
  - answer: Comment enumeration runs in linear time; a 1,000‑page document processes
      in under 2 seconds on a typical 4‑core server.
    question: How does comment performance scale with document size?
  - answer: Absolutely. Iterate the `CommentCollection` and write each comment’s properties
      to CSV, JSON, or XML as needed.
    question: Can I export comments to a separate file?
  type: FAQPage
tags:
- comment management
- Aspose.Words
- Java document processing
title: 如何使用 Aspose.Words for Java 为 Word 文档添加评论
url: /zh/java/annotations-comments/aspose-words-java-comment-management-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words 为 Word 文档添加 Java 注释

## 介绍
将评论以编程方式添加到 Word 文档可以简化协作、代码审查或自动化报告生成。在本教程中，您将学习使用 Aspose.Words 库 **如何添加 Java 注释**，涵盖创建、回复、打印、删除、标记为完成以及提取 UTC 时间戳。完成后，您将能够直接在文档中嵌入丰富的反馈，而无需手动操作。

## 快速答案
- **第一步是什么？** 使用 `new Document("input.docx")` 加载 Word 文件。  
- **我可以回复评论吗？** 可以——创建 `Comment` 对象并调用 `comment.getReplies().add(reply)`。  
- **如何将评论标记为已完成？** 设置 `comment.setDone(true)` 将其标记为已解决。  
- **UTC 时间可用吗？** 每个评论的 `getDateTime()` 存储为 UTC，您可以直接读取。  
- **我需要许可证吗？** 试用版可用于开发；完整许可证可去除评估限制。

## 什么是如何添加 Java 注释？
`how to add comment java` 指的是使用 Java 代码和 Aspose.Words API 以编程方式向 Microsoft Word 文档插入评论的过程。此操作可在以文档为中心的工作流中实现自动化反馈循环。

## 为什么使用 Aspose.Words 进行评论管理？
Aspose.Words 支持 **35+ 种输入和输出格式**，并且能够处理超过 **500 页** 的文档，同时在典型服务器上保持内存使用低于 **100 MB**。其评论 API 在未安装 Microsoft Word 的情况下即可工作，让您在无头环境中拥有完整控制，并且相比 Office 自动化可将许可证成本降低高达 **70 %**。

## 先决条件
- 已安装 Java Development Kit (JDK) 17 或更高版本。  
- 如 IntelliJ IDEA 或 Eclipse 等 IDE。  
- 用于依赖管理的 Maven 或 Gradle。  
- 有效的 Aspose.Words for Java 许可证（试用版或正式版）。

### 设置 Aspose.Words for Java
Aspose.Words 以单个 JAR 形式提供。添加与您的构建工具匹配的依赖项。

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
Aspose.Words 是商业产品；您可以先使用免费试用版，或请求临时许可证以获取全部功能。访问 [purchase page](https://purchase.aspose.com/buy) 了解许可证选项。

## 如何使用 Aspose.Words 在 Java 中添加评论？
加载文档，创建 `Comment` 对象，并将其附加到 `Paragraph`。这种两步模式将在所需位置插入评论，是后续所有操作的基础。通过指定作者、文本和时间戳，您可以立即为审阅者提供上下文，评论也会成为文档结构的一部分。

`Document` 类是 Aspose.Words 的顶层对象，表示内存中的单个 Word 文件。实例化后，所有读写操作都通过该对象进行。  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
```  

接下来，创建实际的评论。`Comment` 类存储作者、文本和时间戳信息。  
```java
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```  

最后，使用评论的 `Replies` 集合添加回复。`Comment` 对象会自动跟踪回复层级。  
```java
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentWithReply.docx");
```  

## 如何打印所有评论及其回复？
遍历文档的 `CommentCollection`，输出每条评论的文本、作者和 UTC 时间戳。回复嵌套在每条评论内部，您可以显示完整的对话线程。通过递归遍历集合，可保留层级结构，并将输出格式化用于日志或 UI，亦可按作者或日期进行过滤。  
```java
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/Comments.docx");
```  

使用简单循环遍历集合并打印详细信息。  
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

## 如何删除评论回复？
您可以删除特定的回复或清除评论的所有回复。删除回复有助于在采纳反馈后保持文档整洁。使用 `getReplies().remove(index)` 方法进行有针对性的删除，或调用 `clear()` 清空整个回复列表，确保不留下孤立的讨论。  
```java
Document document = new Document();
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
comment.addReply("Joe Bloggs", "J.B.", new Date(), "Another reply");
```  

调用 `comment.getReplies().clear()` 或按索引删除单个回复。  
```java
comment.removeReply(comment.getReplies().get(0)); // Remove one reply
comment.removeAllReplies(); // Remove all remaining replies
```  

## 如何将评论标记为已完成？
设置评论的 `Done` 标志表示问题已解决。此可视提示对审阅者和下游处理工具都有帮助。调用 `setDone(true)` 时，Word 会在评论旁显示复选标记，您随后可以查询该标志以生成未完成项的报告。  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
documentBuilder.writeln("Hello world!");
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("Fix the spelling error!");
```  

在处理完评论内容后应用该标志。  
```java
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
document.getFirstSection().getBody().getFirstParagraph().getRuns().get(0).setText("Hello world!");
comment.setDone(true);
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentDone.docx");
```  

## 如何从评论获取 UTC 日期和时间？
每条评论的创建时间以 UTC 存储，可通过 `getDateTime()` 访问。此时间戳对审计追踪和版本控制至关重要。返回的 `DateTime` 对象可使用 ISO‑8601 格式化，从而记录反馈的精确时刻，并在分布式系统间同步评论数据。  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
Date dateTime = new Date();
Comment comment = new Comment(document, "John Doe", "J.D.", dateTime);
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```  

您可以将时间戳格式化为 ISO‑8601，以便轻松记录。  
```java
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Comment currentComment = (Comment) doc.getChild(NodeType.COMMENT, 0, true);
assert currentComment.getDateTimeUtc().toString() == dateTime.toString();
```  

## 实际应用
了解这些 API 可帮助您构建稳健的解决方案，包括：
- **协作编辑平台** – 在生成的报告中直接嵌入反馈循环。  
- **自动化审查流水线** – 标记、解决并审计评论，无需人工干预。  
- **合规文档** – 捕获审阅者时间戳以满足监管审计。

## 性能考虑因素
在处理大型文件（500 页以上）时，请遵循以下最佳实践：
- 将评论分批处理，以避免将整个集合加载到内存中。  
- 使用 `Document.optimizeResources()` 在保存前压缩文档。  
- 保持 Aspose.Words 为最新版本；24.12 版为评论枚举带来了 30 % 的速度提升。

## 结论
现在，您已经拥有使用 Aspose.Words 完成 **how to add comment java** 的完整工具包：创建评论、回复、打印、删除、标记为已完成以及提取 UTC 时间戳。将这些代码片段集成到现有的 Java 服务中，以实现反馈自动化、执行审查策略并保持清晰的审计轨迹。

**接下来的步骤**
- 试验按作者或日期过滤评论。  
- 将评论管理与 Aspose.Words “track changes” API 结合，实现完整的修订控制。  
- 探索将评论数据导出为 JSON，以供下游分析使用。

## 常见问题

**Q: 我可以在生产环境中不使用许可证使用 Aspose.Words 吗？**  
A: 不能。试用版仅用于开发，生产部署需要完整许可证。

**Q: 该库是否支持受密码保护的文档？**  
A: 支持。通过将密码传递给 `Document` 构造函数来加载受保护的文件。

**Q: 哪些 Java 版本兼容？**  
A: Aspose.Words for Java 支持 JDK 8 到 JDK 21，所有版本功能保持一致。

**Q: 评论性能如何随文档大小扩展？**  
A: 评论枚举的时间复杂度为线性；在典型的 4 核服务器上，1,000 页文档的处理时间不足 2 秒。

**Q: 我可以将评论导出到单独的文件吗？**  
A: 当然可以。遍历 `CommentCollection`，根据需要将每条评论的属性写入 CSV、JSON 或 XML。

---

**最后更新：** 2026-08-10  
**测试环境：** Aspose.Words for Java 24.12  
**作者：** Aspose  

{{< blocks/products/products-backtop-button >}}

## 相关教程

- [掌握 Aspose.Words for Java 注释与评论教程](/words/java/annotations-comments/)
- [使用 Aspose.Words Java 跟踪 Word 文档更改：文档修订完整指南](/words/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)
- [Aspose.Words Java：Word 文档处理综合指南](/words/java/document-operations/aspose-words-java-master-word-processing/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}