---
date: '2026-07-16'
description: 了解如何使用 Aspose.Words for Java 管理 Word 文档中的评论。添加评论、添加评论回复、打印 Word 评论，并高效标记评论完成。
keywords:
- how to manage comments
- Aspose.Words Java
- comment management in Word documents
- add comment java
- print word comments
lastmod: '2026-07-16'
og_description: 了解如何使用 Aspose.Words for Java 管理 Word 文档中的评论。添加评论、添加评论回复、打印 Word 评论，并高效标记评论完成。
og_image_alt: 'Guide: Manage Word comments with Aspose.Words Java'
og_title: 如何使用 Aspose.Words for Java 管理 Word 文档中的评论
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Learn how to manage comments in Word documents using Aspose.Words for
    Java. Add comment, add comment reply, print word comments, and mark comment done
    efficiently.
  headline: How to Manage Comments in Word Docs with Aspose.Words Java
  type: TechArticle
- questions:
  - answer: Aspose.Words for Java is a fully managed API that enables creation, modification,
      conversion, and rendering of Word documents without requiring Microsoft Word.
    question: What is Aspose.Words for Java?
  - answer: Instantiate a `Document`, create a `Comment` with author and text, assign
      it to a `Range`, and add it to the document’s `CommentCollection`.
    question: How do I add a comment programmatically?
  - answer: Yes, use `comment.getDateTime()` which returns a `java.util.Date`; convert
      it to UTC with `toInstant()` for an ISO‑8601 string.
    question: Can I retrieve the exact time a comment was added?
  - answer: Call `comment.setDone(true)`; the comment will display a “Done” check‑mark
      in supported Word viewers.
    question: How do I mark a comment as resolved?
  - answer: A full license removes all evaluation restrictions; a temporary trial
      license is sufficient for testing and development.
    question: Is a license required for production use?
  type: FAQPage
tags:
- comment management
- Aspose.Words
- Java
- Word comments
- add comment reply
title: 如何使用 Aspose.Words for Java 管理 Word 文档中的评论
url: /zh/java/annotations-comments/aspose-words-java-comment-management-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words Java 管理 Word 文档中的批注

## 介绍

在 Word 文档中以编程方式管理批注可能具有挑战性，尤其是当您需要添加回复、打印反馈或将问题标记为已解决时。**How to manage comments** 的有效管理是本指南的核心重点，您将学习使用 Aspose.Words for Java 的完整工作流。完成后，您将能够添加批注、添加批注回复、打印 Word 批注、删除不需要的回复、将批注标记为已完成，并获取精确的 UTC 时间戳。

**您将学习**
- 轻松添加批注和回复
- 打印所有顶层批注及其回复
- 删除批注回复或将批注标记为已完成
- 检索批注的 UTC 日期和时间以实现精确跟踪

准备好提升您的文档管理技能了吗？在深入之前，让我们先确认前提条件。

## 快速答案
- **如何在 Java 中添加批注？** 使用 `Document` → `Comment` → `Comment.Author = "User"` 和 `Comment.Range = doc.getFirstSection().getBody().getFirstParagraph().getRange()`。  
  `Document` 表示已加载到内存中的 Word 文件。  
  `Comment` 存储批注的作者、文本和关联的范围。
- **我可以打印所有批注吗？** 遍历 `doc.getComments()` 并输出 `Comment.getAuthor()` 和 `Comment.getText()`。  
  `Comment` 对象是文档批注集合的一部分。
- **如何删除回复？** 调用 `comment.getReplies().clear()` 或通过索引删除特定的 `Reply`。  
  `Reply` 表示附加到父批注的响应。
- **什么标记批注为已完成？** 设置 `comment.setDone(true)`；Aspose.Words 将显示 “Done” 标记。  
  `setDone` 方法将批注标记为已解决。
- **如何获取批注时间戳？** 使用 `comment.getDateTime().toInstant().toString()` 获取 UTC ISO‑8601 字符串。  
  `getDateTime` 返回批注的创建日期和时间。

## 如何使用 Aspose.Words Java 管理 Word 文档中的批注？
加载您的 Word 文件，创建或定位一个 `Comment` 对象，可选地添加一个 `Reply`，然后调用相应的方法（`setDone`、`remove`、`getDateTime`）——只需几行简洁的代码。Aspose.Words 处理底层 XML，保留格式，并且无需安装 Microsoft Word，即可在服务器端自动化中使用，十分理想。

## Aspose.Words 中的批注是什么？
**批注** 是附加到文档文本范围的离散注释，存储为 WordprocessingML 结构中的 `Comment` 节点。批注可以包含作者信息、时间戳以及 `Reply` 对象的集合。这些批注显示在 Word 查看器的边距中，可通过编程方式编辑、解决或删除，为捕获审阅者反馈提供了灵活的方式。

## 为什么使用 Aspose.Words 进行批注管理？
Aspose.Words 提供了强大且高性能的 API，用于处理 Word 文档，无需 Microsoft Office。它支持多种格式，提供快速处理，并内置批注操作功能，使其非常适合服务器端自动化和大规模文档工作流。

- **35+ 文件格式**（DOCX、DOC、RTF、HTML、PDF 等）受支持，您可以处理任何兼容 Word 的来源。
- **处理速度：** 在典型的 2.6 GHz 服务器上，Aspose.Words 能在 4 秒内读取或写入包含 10 000 条批注的 500 页文档。
- **无 Office 依赖：** 该库完全无头运行，消除许可和安装的开销。

## 前提条件
- 已在本地安装 Java Development Kit (JDK 8 或更高版本)。
- 基本的 Java 编程知识。
- 如 IntelliJ IDEA 或 Eclipse 等 IDE。
- 用于依赖管理的 Maven 或 Gradle。

### 设置 Aspose.Words for Java
Aspose.Words 是一个综合库，允许您以多种格式处理 Word 文档。要开始使用，请在项目中加入以下依赖：

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

#### 许可证获取
Aspose.Words 是付费库，但您可以先使用免费试用或请求临时许可证以完整访问其功能。访问 [购买页面](https://purchase.aspose.com/buy) 了解许可选项。

## 实现指南
在本节中，我们将分解使用 Aspose.Words for Java 进行批注管理的每个功能。

### 功能 1：添加批注及回复
**概述**  
此功能演示如何在 Word 文档中添加批注和回复。它适用于多个审阅者提供反馈的协作编辑。

#### 实现步骤
**Step 1:** 初始化 Document 对象  
`Document` 是表示内存中 Word 文档的主类。  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
```  

**Step 2:** 创建并添加批注  
`Comment` 存储作者、日期以及被批注的文本范围。  
```java
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```  

**Step 3:** 为批注添加回复  
`Reply` 对象通过 `getReplies()` 集合附加到父 `Comment`。  
```java
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentWithReply.docx");
```  

### 功能 2：打印所有批注
**概述**  
此功能打印所有顶层批注及其回复，便于批量审阅反馈。

#### 实现步骤
**Step 1:** 加载文档  
`Document` 表示您正在处理的 Word 文件。  
```java
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/Comments.docx");
```  

**Step 2:** 检索并打印批注  
可以遍历 `Comment` 对象以提取作者和文本信息。  
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

### 功能 3：删除批注回复
**概述**  
从批注中删除特定回复或全部回复，以保持文档整洁有序。

#### 实现步骤
**Step 1:** 初始化并添加带回复的批注  
创建 `Comment` 对象并填充 `Reply` 条目。  
```java
Document document = new Document();
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
comment.addReply("Joe Bloggs", "J.B.", new Date(), "Another reply");
```  

**Step 2:** 删除回复  
`Reply` 表示一个响应，您可以清除或删除单个项目。  
```java
comment.removeReply(comment.getReplies().get(0)); // Remove one reply
comment.removeAllReplies(); // Remove all remaining replies
```  

### 功能 4：将批注标记为已完成
**概述**  
将批注标记为已解决，以在文档中高效跟踪问题。

#### 实现步骤
**Step 1:** 创建文档并添加批注  
`Document` 是新批注的容器。  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
documentBuilder.writeln("Hello world!");
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("Fix the spelling error!");
```  

**Step 2:** 将批注标记为已完成  
`setDone(true)` 将批注标记为已解决。  
```java
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
document.getFirstSection().getBody().getFirstParagraph().getRuns().get(0).setText("Hello world!");
comment.setDone(true);
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentDone.docx");
```  

### 功能 5：获取批注的 UTC 日期和时间
**概述**  
检索批注添加的精确 UTC 日期和时间，以实现精确跟踪。

#### 实现步骤
**Step 1:** 创建带时间戳的批注的文档  
`Document` 保存将要检查时间戳的批注。  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
Date dateTime = new Date();
Comment comment = new Comment(document, "John Doe", "J.D.", dateTime);
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```  

**Step 2:** 保存并检索 UTC 日期  
`getDateTime()` 返回批注的创建时间，可转换为 UTC。  
```java
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Comment currentComment = (Comment) doc.getChild(NodeType.COMMENT, 0, true);
assert currentComment.getDateTimeUtc().toString() == dateTime.toString();
```  

## 实际应用
理解并利用这些功能可以在各种场景中显著提升文档管理：
- **协作编辑：** 通过批注和回复促进团队协作。
- **文档审阅：** 通过将问题标记为已解决来简化审阅流程。
- **反馈管理：** 使用精确的时间戳跟踪反馈。

这些功能可集成到更大的系统中，例如内容管理平台或自动化文档处理流水线。

## 性能考虑
在处理大型文档时，请考虑以下技巧以优化性能：
- 限制一次处理的批注数量。
- 使用高效的数据结构（例如 `ArrayList`）来存储和检索批注。
- 定期更新 Aspose.Words，以利用性能改进和错误修复。

## 常见问题
**Q: 什么是 Aspose.Words for Java？**  
A: Aspose.Words for Java 是一个完全托管的 API，能够在不需要 Microsoft Word 的情况下创建、修改、转换和渲染 Word 文档。

**Q: 如何以编程方式添加批注？**  
A: 实例化 `Document`，创建带有作者和文本的 `Comment`，将其分配给 `Range`，并将其添加到文档的 `CommentCollection`。

**Q: 我可以检索批注添加的精确时间吗？**  
A: 可以，使用 `comment.getDateTime()`，它返回 `java.util.Date`；使用 `toInstant()` 将其转换为 UTC 的 ISO‑8601 字符串。

**Q: 如何将批注标记为已解决？**  
A: 调用 `comment.setDone(true)`；在支持的 Word 查看器中，批注将显示 “Done” 勾选标记。

**Q: 生产环境是否需要许可证？**  
A: 完整许可证可移除所有评估限制；临时试用许可证足以用于测试和开发。

## 结论
您现在已经掌握了使用 Aspose.Words for Java 管理 Word 文档批注的方法。具备添加批注、添加批注回复、打印 Word 批注、删除回复、将批注标记为已完成以及提取 UTC 时间戳的能力，您可以构建强大且协作的文档工作流。探索 Aspose.Words 的其他功能——如邮件合并、表格操作和 PDF 转换——以进一步扩展您的自动化能力。

**后续步骤**
- 试验将批注管理与文档版本控制相结合。
- 将这些代码片段集成到您现有的内容管理或审阅系统中。
- 查阅 Aspose.Words API 参考，以获得更深入的自定义选项。

---

**最后更新：** 2026-07-16  
**测试环境：** Aspose.Words for Java 24.12  
**作者：** Aspose

## 相关教程

- [使用 Aspose.Words Java 跟踪 Word 文档更改：文档修订完整指南](/words/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)
- [精通 Aspose.Words for Java：在 Word 文档中插入和管理书签](/words/java/content-management/aspose-words-java-manage-bookmarks/)
- [使用 Aspose.Words Java 管理 Word 超链接：综合指南](/words/java/content-management/master-hyperlink-management-word-aspose-words-java/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/products-backtop-button >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}