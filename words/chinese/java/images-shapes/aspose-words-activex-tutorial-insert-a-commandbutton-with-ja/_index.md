---
category: general
date: 2026-08-07
description: Aspose.Words ActiveX 教程展示了如何使用 Java 向 Word 文档中添加 CommandButton 控件。了解完整的代码、配置和保存步骤。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose words activex tutorial
- aspose.words java
- activeX control java
- documentbuilder insert control
- forms2olecontrol usage
language: zh
lastmod: 2026-08-07
og_description: Aspose.Words ActiveX 教程解释如何使用 Java 将 CommandButton ActiveX 控件嵌入 Word
  文档。请按照完整示例创建、配置并保存文档。
og_image_alt: Screenshot of a Word document with a CommandButton added via Aspose.Words
  ActiveX tutorial
og_title: Aspose.Words ActiveX 教程 – Java 步骤指南
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  headline: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  type: TechArticle
- description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  name: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  steps:
  - name: Initialize a `Document` and `DocumentBuilder`.
    text: Initialize a `Document` and `DocumentBuilder`.
  - name: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
    text: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
  - name: Set the button’s name, caption, size, and position.
    text: Set the button’s name, caption, size, and position.
  - name: Save the document as a .docx file that contains the ActiveX control.
    text: Save the document as a .docx file that contains the ActiveX control.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
title: Aspose.Words ActiveX 教程——使用 Java 插入 CommandButton
url: /zh/java/images-shapes/aspose-words-activex-tutorial-insert-a-commandbutton-with-ja/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ActiveX 教程 – 使用 Java 插入 CommandButton

如果您需要在 Word 文件中嵌入 ActiveX 控件，本 **Aspose.Words ActiveX 教程** 将手把手带您完成整个过程。您将看到如何创建空白文档、插入 CommandButton、设置其属性并保存结果——全部使用纯 Java 代码。

示例使用 Aspose.Words for Java API，无需在构建服务器上安装 Microsoft Office。完成本指南后，您即可生成包含完整功能 CommandButton 控件的 .docx 文件，能够在 Windows 环境中使用。

## 前置条件

开始之前，请确保您已具备：

- 已安装 Java Development Kit (JDK) 8 或更高版本。
- Maven 或其他构建工具，用于管理依赖。
- Aspose.Words for Java 许可证（或临时评估密钥），以避免评估水印。
- 对 Java 语法和面向对象编程有基本了解。

> **专业提示：** 将 Aspose.Words Maven 依赖添加到 `pom.xml`，让 IDE 自动解析类：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version -->
</dependency>
```

## 步骤 1：创建一个新的空白文档和 `DocumentBuilder`

`Document` 类在内存中表示 Word 文件，而 `DocumentBuilder` 提供流式 API 用于编辑文档。初始化这两个对象即可为后续修改做好准备。

```java
import com.aspose.words.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty Word document
        Document document = new Document();

        // DocumentBuilder lets you add text, tables, and controls
        DocumentBuilder builder = new DocumentBuilder(document);
```

**为什么重要：**  
`DocumentBuilder` 会跟踪当前光标位置，因此任何后续的插入操作——例如添加控件——都会出现在您期望的位置。

## 步骤 2：插入 CommandButton ActiveX 控件

Aspose.Words 为 ActiveX 对象提供 `Forms2OleControl`。`insertForms2OleControl` 方法需要控件类型，您通过 `Forms2OleControlType` 枚举来指定。

```java
        // Insert a CommandButton ActiveX control at the current cursor location
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**说明：**  
插入的控件是基于 COM 的对象，Word 在 Windows 环境中打开文档时会将其呈现为可点击的按钮。

## 步骤 3：配置按钮的属性

插入后，您可以调整按钮的名称、标题、大小和位置。这些属性决定了控件在 Word 中的外观和行为。

```java
        // Set the logical name used by VBA or external scripts
        commandButton.setName("cmdSubmit");

        // Text displayed on the button face
        commandButton.setCaption("Submit");

        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);
        commandButton.setTop(150);

        // Define the button’s dimensions (width × height) in points
        commandButton.setWidth(80);
        commandButton.setHeight(30);
```

**这些设置为何重要：**

- **Name** – 使 VBA 宏能够引用该控件（`ActiveDocument.Forms("cmdSubmit")`）。
- **Caption** – 确定用户点击的可见标签。
- **Left / Top** – 控制相对于页面边距的放置位置。
- **Width / Height** – 确保在不同屏幕分辨率下保持一致的视觉尺寸。

## 步骤 4：保存文档

调用 `save` 将内存中的表示写入物理文件。您可以选择任意受支持的格式（`.docx`、`.doc`、`.pdf` 等）。本教程中我们保留原生 Word 格式。

```java
        // Persist the document with the embedded ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

**结果：**  
在 Microsoft Word 中打开 `ActiveXDemo.docx` 时，会显示一个标有 **Submit** 的 CommandButton，位于指定坐标。点击按钮会触发默认行为（默认未附加 VBA 代码）。

## 完整源代码

将上述代码块组合起来，完整且可运行的程序如下：

```java
import com.aspose.words.*;
import com.aspose.words.forms.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button's properties
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // Step 4: Save the document with the ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

### 预期输出

- 在 `output` 文件夹中生成名为 **ActiveXDemo.docx** 的文件。
- 在 Windows 上的 Microsoft Word 中打开时，文档会显示位于定义位置的可点击 **Submit** 按钮。
- 该按钮可通过 Word UI（开发工具 → 属性）进行选中、移动或关联 VBA 代码。

## 常见变体处理

| 场景 | 调整 |
|----------|------------|
| **保存为 .doc**（旧版格式） | `document.save("ActiveXDemo.doc", SaveFormat.DOC);` |
| **添加事件处理程序** | Word 通过 Aspose.Words 不暴露 ActiveX 事件。您必须在生成文档后手动添加 VBA 代码。 |
| **多个控件** | 对不同的 `setName` 和 `setCaption` 值重复插入/配置块。 |
| **不同控件类型（例如 CheckBox）** | 在 `insertForms2OleControl` 调用中使用 `Forms2OleControlType.CHECKBOX`。 |
| **非 Windows 平台** | ActiveX 控件仅在 Windows Word 中渲染。跨平台方案请考虑内容控件（`StructuredDocumentTag`）。 |

## 最佳实践与常见坑点

- **尽早授权** – 在创建 `Document` 之前注册 Aspose.Words 许可证，以避免出现评估提示。
- **坐标系统** – 位置以点为单位（1 pt = 1/72 in）。如果 UI 设计使用像素或厘米，请进行相应转换。
- **文件路径** – 使用绝对路径或 Java 的 `Paths` API，防止输出目录不存在导致 `FileNotFoundException`。
- **线程安全** – `Document` 与 `DocumentBuilder` 不是线程安全的。若并行生成文档，请为每个线程创建独立实例。
- **测试** – 在目标 Word 版本（如 Word 2016、Word 365）上验证生成的文档，因为旧版本可能以不同方式显示 ActiveX 控件。

## 结论

本 **Aspose.Words ActiveX 教程** 演示了如何使用 Java 编程方式向 Word 文档中添加 CommandButton 控件。您已经学会：

1. 初始化 `Document` 与 `DocumentBuilder`。
2. 插入类型为 `COMMAND_BUTTON` 的 `Forms2OleControl`。
3. 设置按钮的名称、标题、尺寸和位置。
4. 将文档保存为包含 ActiveX 控件的 .docx 文件。

接下来，您可以探索其他控件类型、自动化 VBA 宏注入，或将 ActiveX 控件与 Aspose.Words 的其他功能（如邮件合并和内容控件）结合使用。尝试不同布局，并将生成的文档集成到更大的基于 Java 的报表流水线中。

---


## 接下来您应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并探索项目中的替代实现方式。每个资源都提供完整的可运行代码示例和逐步解释。

- [Using OLE Objects and ActiveX Controls in Aspose.Words for Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Convert Word to RTF with Aspose.Words for Java Tutorial](/words/english/java/document-loading-and-saving/saving-documents-as-rtf-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}