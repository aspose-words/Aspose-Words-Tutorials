---
date: '2026-01-27'
description: 学习如何使用 Aspose.Words for Java 在 Word 文档中添加 Java 注释以及添加/删除 Word 注释。轻松实现注释的管理、打印、删除和时间戳。
keywords:
- Aspose.Words Java
- comment management in Word documents
- managing comments with Aspose.Words
title: 使用 Aspose.Words 在 Java 中添加批注 – 批注管理大师
url: /zh/java/annotations-comments/aspose-words-java-comment-management-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java：精通 Word 文档中的评论管理

## Introduction
如果您需要以编程方式 **add comment java** 并对评论的整个生命周期保持完全控制，您来对地方了。无论是构建协作审阅工具还是自动化文档工作流，管理评论——添加、回复、删除以及跟踪时间戳——都可能成为痛点。在本教程中，我们将使用 Aspose.Words for Java 逐步演示所有关键操作，让您能够自信地 **add remove word comments**、打印评论、将其标记为完成，并提取 UTC 时间戳。

**What You’ll Learn**
- 如何仅用一行代码添加评论和回复  
- 如何打印所有顶层评论及其嵌套回复  
- 如何删除评论回复或完整清除评论线程  
- 如何将评论标记为完成（已解决）  
- 如何获取评论创建的精确 UTC 日期和时间  

准备好了吗？在深入代码之前，请先确保您的环境已正确设置。

## Prerequisites
在开始之前，请确保具备以下条件：

- 已安装 Java Development Kit (JDK) 8 或更高版本  
- 具备 Java 语法和面向对象编程的基础知识  
- 使用 IntelliJ IDEA 或 Eclipse 等 IDE 便于项目管理  

### Setting Up Aspose.Words for Java
Aspose.Words 是一个强大的库，可让您以多种格式操作 Word 文档。根据您的构建系统添加相应的依赖：

**Maven**  
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle**  
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### License Acquisition
Aspose.Words 是商业产品，但您可以先使用免费试用版，或申请临时许可证以获得全部功能。访问 [purchase page](https://purchase.aspose.com/buy) 了解授权选项。

## Quick Answers
- **Can I add comment java without a license?** Yes, a trial works but adds evaluation watermarks.  
- **Which method adds a reply?** `comment.addReply(author, initials, date, text)`.  
- **How do I mark a comment as done?** Call `comment.setDone(true)`.  
- **Is UTC timestamp available?** Use `comment.getDateTimeUtc()`.  
- **What version is tested?** Aspose.Words 25.3 (Java).

## Implementation Guide
下面的章节将逐步拆解每个功能，并提供上下文和实用技巧。

### Feature 1: Add Comment with Reply
#### Overview
添加评论及其回复是协作编辑的基础。您将看到如何创建评论、将其附加到段落，然后添加嵌套回复。

#### Implementation Steps
**Step 1:** Initialize the Document Object  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
```

**Step 2:** Create and Add a Comment  
```java
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```

**Step 3:** Add a Reply to the Comment  
```java
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentWithReply.docx");
```

### Feature 2: Print All Comments
#### Overview
在审阅大型文档时，打印每个顶层评论及其回复可以节省时间。此代码片段演示如何加载文档并遍历评论层级。

#### Implementation Steps
**Step 1:** Load the Document  
```java
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/Comments.docx");
```

**Step 2:** Retrieve and Print Comments  
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

### Feature 3: Remove Comment Replies
#### Overview
有时评论线程会变得嘈杂。此示例展示如何删除单个回复或清空整个回复列表。

#### Implementation Steps
**Step 1:** Initialize and Add Comments with Replies  
```java
Document document = new Document();
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
comment.addReply("Joe Bloggs", "J.B.", new Date(), "Another reply");
```

**Step 2:** Remove Replies  
```java
comment.removeReply(comment.getReplies().get(0)); // Remove one reply
comment.removeAllReplies(); // Remove all remaining replies
```

### Feature 4: Mark Comment as Done
#### Overview
将评论标记为 “done” 表示问题已解决。此标记可在 UI 层用于过滤已完成的反馈。

#### Implementation Steps
**Step 1:** Create a Document and Add a Comment  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
documentBuilder.writeln("Hello world!");
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("Fix the spelling error!");
```

**Step 2:** Mark the Comment as Done  
```java
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
document.getFirstSection().getBody().getFirstParagraph().getRuns().get(0).setText("Hello world!");
comment.setDone(true);
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentDone.docx");
```

### Feature 5: Get UTC Date and Time from Comment
#### Overview
精确的时间戳对于审计追踪至关重要。Aspose.Words 将创建时间存储为 UTC，您可以检索并进行比较。

#### Implementation Steps
**Step 1:** Create a Document with a Timestamped Comment  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
Date dateTime = new Date();
Comment comment = new Comment(document, "John Doe", "J.D.", dateTime);
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```

**Step 2:** Save and Retrieve the UTC Date  
```java
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Comment currentComment = (Comment) doc.getChild(NodeType.COMMENT, 0, true);
assert currentComment.getDateTimeUtc().toString() == dateTime.toString();
```

## Practical Applications
掌握这些 API 可以显著提升基于文档的解决方案：

- **Collaborative Editing:** 让多位审阅者直接在文件中留下反馈、回复并解决问题。  
- **Document Review Pipelines:** 自动提取评论用于报告或合规检查。  
- **Audit Trails:** 为法律或监管目的存储 UTC 时间戳。  

这些代码片段可嵌入更大的系统，如内容管理平台、自动化报告生成器或自定义 Word 处理工具。

## Performance Considerations
处理大型 Word 文件（数百页、数千条评论）时，请注意以下要点：

- 将评论分批处理，而不是一次性全部加载到内存。  
- 在执行多项操作时复用同一个 `Document` 实例。  
- 升级到最新的 Aspose.Words 版本，以获得性能优化和错误修复。

## Common Issues and Solutions
| Issue | Why It Happens | Fix |
|-------|----------------|-----|
| **`NullPointerException` when accessing replies** | The comment has no replies (`getReplies()` returns empty). | Always check `comment.getReplies().getCount() > 0` before accessing an element. |
| **Comments not appearing after saving** | Document was saved to a different folder or overwritten. | Verify `YOUR_DOCUMENT_DIRECTORY` points to the intended location and that you have write permissions. |
| **UTC timestamp differs from local time** | `Date` uses system locale; `getDateTimeUtc()` converts to UTC. | Use `new Date()` for creation and rely on `getDateTimeUtc()` for consistent storage. |

## FAQ Section
1. **What is Aspose.Words for Java?**  
   - It's a library that allows manipulation of Word documents in various formats programmatically.  

2. **How do I install Aspose.Words for my project?**  
   - Add the Maven or Gradle dependency shown earlier to your project file.  

3. **Can I use Aspose.Words without a license?**  
   - Yes, with limitations (evaluation watermarks and feature restrictions).  

4. **What are some common issues when managing comments?**  
   - Ensure proper document loading, handle null references for replies, and verify comment hierarchy.  

5. **How do I track changes across multiple documents?**  
   - Implement version‑control logic in your application or use Aspose.Words’ built‑in revision tracking features.  

---

**Last Updated:** 2026-01-27  
**Tested With:** Aspose.Words 25.3 for Java  
**Author:** Aspose  

{{< blocks/products/products-backtop-button >}}

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}