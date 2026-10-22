---
category: general
date: 2026-09-27
description: 使用 Aspose.Words 在 Java 中创建包含 ActiveX 的 docx。一步步学习插入 ActiveX 命令按钮。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx containing activex
- insert activex command button
- Aspose.Words Java
- ActiveX control in Word
- generate Word document programmatically
language: zh
lastmod: 2026-09-27
og_description: 使用 Aspose.Words 在 Java 中创建包含 ActiveX 的 docx。请按照本指南插入 ActiveX 命令按钮并保存文档。
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
og_title: 使用 Java 创建包含 ActiveX 的 docx – 完整指南
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  headline: How to create docx containing ActiveX with Java and Aspose.Words
  type: TechArticle
- description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  name: How to create docx containing ActiveX with Java and Aspose.Words
  steps:
  - name: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
    text: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
  - name: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
    text: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
  - name: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
    text: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
  type: HowTo
tags:
- docx
- activex
- java
- aspose-words
title: 如何使用 Java 和 Aspose.Words 创建包含 ActiveX 的 docx
url: /zh/java/using-document-elements/how-to-create-docx-containing-activex-with-java-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Java 和 Aspose.Words 创建包含 ActiveX 的 docx

如果您需要 **创建包含 ActiveX 的 docx**，本指南提供完整的解决方案。您将学习如何使用 Aspose.Words for Java **向 Word 文件插入 ActiveX 命令按钮**，然后将结果保存为可在 Microsoft Word 中打开的 .docx。

以编程方式生成 Word 文档可以避免手动编辑，并确保报告、合同或表单模板的一致性。以下步骤涵盖从项目设置到处理常见陷阱的全部内容，帮助您将此技术集成到任何 Java 应用程序中。

## 前置条件

在开始之前，请确保您具备以下条件：

* 已安装 Java Development Kit (JDK) 8 或更高版本。
* 已安装 Maven 3.6+（或您偏好的其他构建工具）。
* 拥有 Aspose.Words for Java 授权文件（免费评估版可用于测试）。
* 若要直观验证 ActiveX 控件，请在目标机器上安装 Microsoft Word。

这些项目是必需的，因为 Aspose.Words 提供创建文档的 API，而 Word 则用于渲染 ActiveX 控件。

## 第 1 步：设置 Maven 项目

创建一个新的 Maven 项目，或在现有的 `pom.xml` 中添加 Aspose.Words 依赖：

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-docx-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.10</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **专业提示：** 将 Aspose.Words 版本与官方发布说明保持同步，以便获得错误修复和新的 ActiveX 功能。

## 第 2 步：编写创建文档的 Java 代码

创建一个名为 `ActiveXDocxCreator` 的类。下面的代码包含所有必需的导入、`main` 方法以及解释每一步操作的详细注释。

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

/**
 * Demonstrates how to create a DOCX file that contains an ActiveX command button.
 * The resulting file can be opened in Microsoft Word where the button appears
 * on the first page.
 */
public class ActiveXDocxCreator {

    public static void main(String[] args) {
        // 1. Initialize a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX Forms2OleControl at the current cursor position.
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // 3. Configure the control to be a CommandButton and set its caption.
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");

        // 4. Position the button on the page.
        //    The coordinates are measured in points (1 point = 1/72 inch).
        commandButton.setLeft(100); // 100 points from the left margin
        commandButton.setTop(150);  // 150 points from the top margin

        // 5. (Optional) Set the size of the button for better visibility.
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // 6. Save the document to the desired location.
        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            // Ensure the output directory exists.
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

### 为什么每行代码都很重要

* `Document` 是所有 Word 内容的容器。创建一个新的实例即可获得干净的画布。
* `DocumentBuilder` 提供流式 API 用于插入元素；它会自动跟踪插入点。
* `insertForms2OleControl()` 创建一个通用的 OLE 控件占位符。Aspose.Words 将其视为 ActiveX 容器。
* `setControlType(Forms2OleControlType.COMMANDBUTTON)` 告诉 Word 将占位符渲染为 CommandButton。
* `setCaption("Click Me")` 定义按钮上显示的文字。
* `setLeft` 和 `setTop` 将按钮相对于页面边距定位。根据您的布局调整这些数值。
* `setWidth` 和 `setHeight` 为可选项，但可改善按钮外观，尤其是在默认尺寸过小的情况下。
* `doc.save` 将内存中的结构写入物理的 .docx 文件，Word 可以直接打开。

## 第 3 步：验证生成的文档

在 Microsoft Word 中打开 `output/ActiveXCommandButton.docx`：

1. 文档应显示单页，左上角附近有一个标注为 **Click Me** 的按钮。
2. 若按钮未出现，请检查 Word 的信任中心中是否 **启用了 ActiveX 控件**（文件 → 选项 → 信任中心 → 信任中心设置 → ActiveX 设置）。
3. 该按钮仅在支持 ActiveX 的 Windows 版 Word 上可用。macOS 或基于 Web 的 Word 会将控件显示为静态图像。

## 第 4 步：处理常见边缘情况

| 情况 | 原因 | 推荐操作 |
|-----------|--------|--------------------|
| 打开文件后按钮缺失 | Word 的安全设置阻止了 ActiveX | 为受信任位置启用 “在受信任的文档中运行所有控件” |
| 生成的 .docx 无法打开 | Aspose.Words 版本不兼容 | 升级至最新的 Aspose.Words 发行版；旧版本可能未正确嵌入所需的 OLE 部分 |
| 需要按钮执行宏 | 单独的 ActiveX 不包含宏代码 | 将 ActiveX 控件与处理 `Click` 事件的 VBA 宏结合使用。使用 `DocumentBuilder.insertOleObject` 方法嵌入启用宏的模板 |
| 在不同页面尺寸上布局错位 | 坐标为绝对点数 | 在定位控件前使用 `builder.getPageSetup().setPageWidth` 和 `setPageHeight` 统一页面尺寸 |

## 第 5 步：扩展解决方案

通过更改 `ControlType` 枚举，您可以插入其他 ActiveX 控件：

```java
commandButton.setControlType(Forms2OleControlType.CHECKBOX); // inserts a checkbox
```

Aspose.Words 还支持插入 **ActiveX 文本框**、**列表框** 和 **组合框**。相同的定位方法（`setLeft`、`setTop`、`setWidth`、`setHeight`）同样适用。

如果需要放置多个控件，只需重复调用 `builder.insertForms2OleControl()` 并相应调整每个控件的坐标。

## 完整源码文件

以下是完整的 `ActiveXDocxCreator.java` 文件，可直接复制粘贴使用：

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

public class ActiveXDocxCreator {
    public static void main(String[] args) {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

运行此程序即可生成 **包含 ActiveX 的 docx**，可分发给需要交互式表单的终端用户。

## 结论

现在，您已经掌握了使用 Java 和 Aspose.Words **创建包含 ActiveX 的 docx**，以及如何以编程方式 **插入 ActiveX 命令按钮**。本教程涵盖了项目设置、完整源码、验证步骤以及处理常见问题的策略。

接下来您可以探索：

* 为按钮点击添加 VBA 宏响应。
* 嵌入复选框、组合框等其他 ActiveX 控件。
* 使用动态数据自动生成多页表单。

尝试不同的坐标、尺寸和控件类型，以适配您的特定文档布局。祝编码愉快！

## 接下来您应该学习什么？

以下教程与本指南紧密相关，帮助您进一步掌握 API 功能并在项目中探索替代实现方式：

- [Using OLE Objects and ActiveX Controls in Aspose.Words for Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}