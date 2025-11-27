---
date: '2025-11-27'
description: 学习如何使用 Aspose.Words for Java 跟踪 Word 文档中的更改并管理修订。通过本综合指南，掌握文档比较、内联修订处理等技巧。
keywords:
- track changes
- document revisions
- inline revision handling
language: zh
title: 使用 Aspose.Words Java 跟踪 Word 文档更改：文档修订完整指南
url: /java/document-comparison-tracking/aspose-words-java-track-changes-revisions/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words Java 在 Word 文档中跟踪更改：文档修订完整指南

## 介绍

在多个贡献者共同编辑重要文档时，协作可能会变得困难，尤其是当你需要 **在 Word 文档中跟踪更改** 时。借助 Aspose.Words for Java，你可以将“跟踪更改”功能无缝嵌入到应用程序中，获得对修订的细粒度控制。本教程将带你完成库的设置、处理内联修订以及掌握完整的更改跟踪功能。

**你将学到的内容：**
- 如何使用 Maven 或 Gradle 设置 Aspose.Words
- 实现各种类型的修订（插入、格式、移动、删除）
- 理解并利用关键特性来管理文档更改

### 快速回答
- **哪个库可以实现 Word 文档的更改跟踪？** Aspose.Words for Java  
- **推荐使用哪种依赖管理器？** Maven 或 Gradle（均受支持）  
- **开发阶段需要许可证吗？** 免费试用可用于评估；生产环境需购买许可证  
- **能高效处理大文档吗？** 可以——使用分段处理和批量操作  
- **是否有编程方式启动跟踪？** `document.startTrackRevisions()` 可启动跟踪会话  

让我们先设置环境，以便你能够掌握这些功能。

## 前置条件

在开始之前，请确保你具备以下条件：
- **Java Development Kit (JDK)：** 已安装 8 版或更高版本。
- **集成开发环境 (IDE)：** 如 IntelliJ IDEA、Eclipse 或 NetBeans。
- **Maven 或 Gradle：** 用于管理依赖并构建项目。

同时，需要具备基本的 Java 编程知识，以便跟随代码示例。

## 设置 Aspose.Words

要将 Aspose.Words 集成到项目中，请使用 Maven 或 Gradle 进行依赖管理。

### Maven 设置

在 `pom.xml` 文件中添加以下依赖：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

### Gradle 设置

在 `build.gradle` 文件中加入此行：

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### 许可证获取

Aspose 提供免费试用以测试其功能，帮助你评估是否满足需求。获取方式如下：
1. **免费试用：** 从 [Aspose Downloads](https://releases.aspose.com/words/java/) 下载库，使用时受评估限制。
2. **临时许可证：** 访问 [Temporary License](https://purchase.aspose.com/temporary-license/) 获取可延长使用且无评估限制的临时许可证。
3. **购买许可证：** 如需完整功能，请按照其购买页面的说明进行购买。

#### 基本初始化

初始化时，创建 `Document` 实例并开始使用：

```java
import com.aspose.words.Document;

public class Main {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("input.docx");
        // Further processing here
    }
}
```

## 使用 Aspose.Words Java 跟踪 Word 文档更改

本节回答 **如何在 Java 中跟踪更改**，开发者可以使用 Aspose.Words 实现修订处理。了解不同的修订类型以及如何查询它们，对构建稳健的协作功能至关重要。

## 实现指南

本节将探讨如何使用 Aspose.Words Java 处理不同类型的修订。

### 处理内联修订

#### 概述

在文档中进行更改跟踪时，理解并管理内联修订至关重要。这些修订可能包括插入、删除、格式更改或文本移动。

#### 代码实现

以下是使用 Aspose.Words Java 判断内联节点修订类型的分步指南：

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

#### 说明
- **Insert Revision（插入修订）：** 在跟踪更改时添加文本时产生。
- **Format Revision（格式修订）：** 对文本进行格式修改时触发。
- **Move From/To Revisions（移动修订）：** 表示文档内部的文本移动，成对出现。
- **Delete Revision（删除修订）：** 标记已删除的文本，等待接受或拒绝。

### 实际应用

以下是管理修订的真实场景示例：
1. **协同编辑：** 团队可在最终定稿前高效审阅并批准更改。
2. **法律文档审查：** 律师可跟踪合同的修改，确保各方对最终版本达成一致。
3. **软件文档：** 开发者可管理技术文档的更新，保持内容清晰准确。

### 性能考量

在处理大量修订的大文档时优化性能：
- 通过顺序处理文档章节来最小化内存占用。
- 利用 Aspose.Words 内置的批量操作方法以降低开销。

## 结论

现在，你已经学会如何使用 Aspose.Words Java 通过内联修订管理实现 **在 Word 文档中跟踪更改**。掌握这些技术后，你可以提升协作效率，并在应用程序中对文档修改保持精确控制。

**后续步骤：**
- 试验不同类型的修订。
- 将 Aspose.Words 集成到更大的项目中，以实现全面的文档处理解决方案。

## 常见问题

1. **Aspose.Words 中的内联节点是什么？**
   - 内联节点表示段落中的文本元素，如运行（run）或字符格式。
2. **如何在 Aspose.Words Java 中启动修订跟踪？**
   - 对 `Document` 实例调用 `startTrackRevisions` 方法即可开始跟踪更改。
3. **我可以自动接受或拒绝文档中的修订吗？**
   - 可以，使用 `acceptAllRevisions` 或 `rejectAllRevisions` 等方法可编程地接受或拒绝所有修订。
4. **Aspose.Words 支持哪些文档类型？**
   - 支持 DOCX、PDF、HTML 等多种流行格式，实现灵活的文档转换。
5. **如何高效处理大文档？**
   - 采用增量处理章节的方式，结合批量操作以保持性能。

## 资源

- [Aspose.Words Java 文档](https://reference.aspose.com/words/java/)
- [下载 Aspose.Words for Java](https://releases.aspose.com/words/java/)
- [购买许可证](https://purchase.aspose.com/buy)
- [免费试用](https://releases.aspose.com/words/java/)
- [临时许可证](https://purchase.aspose.com/temporary-license/)
- [Aspose 支持论坛](https://forum.aspose.com/c/words/10)

立即开启你的 Aspose.Words Java 之旅，充分发挥文档处理在应用中的潜力！

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**最后更新：** 2025-11-27  
**测试版本：** Aspose.Words 25.3 for Java  
**作者：** Aspose