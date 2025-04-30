---
"date": "2025-03-28"
"description": "了解如何利用 Aspose.Words for Java 掌握文档处理，包括 VML 支持、加密、HTML 导入选项等。"
"title": "Aspose.Words for Java™ 综合 HTML 功能和文档处理指南"
"url": "/zh/java/document-operations/aspose-words-java-html-features-guide/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# Aspose.Words for Java 的全面 HTML 功能：开发人员指南

## 介绍

驾驭复杂的文档处理世界可能令人望而生畏，尤其是在处理各种 HTML 功能时。无论您处理的是矢量标记语言 (VML) 支持、加密文档，还是特定的 HTML 导入行为， **Aspose.Words for Java** 提供强大的解决方案。在本指南中，我们将探索如何使用 Aspose.Words 无缝实现这些功能，从而增强您的文档处理能力。

**您将学到什么：**
- 如何加载具有 VML 支持的 HTML 文档。
- 处理固定页面 HTML 和警告的技术。
- 加密和加载受密码保护的 HTML 文档的方法。
- 在 HTML 加载选项中使用基本 URI。
- 将 HTML 输入元素导入为结构化文档标签或表单字段。
- 忽略 `<noscript>` HTML 加载期间的元素。
- 配置块导入模式来控制HTML结构保存。
- 支持 `@font-face` 自定义字体的规则。

有了这些见解，您将能够胜任各种 HTML 处理任务。让我们先深入了解先决条件和设置！

## 先决条件

在我们开始使用 Aspose.Words for Java 实现各种 HTML 功能之前，请确保您的环境已正确设置：

- **所需库：** 您需要 Aspose.Words 库版本 25.3 或更高版本。
- **开发环境：** 本指南假设您使用 Maven 或 Gradle 进行依赖管理。
- **知识库：** 对 Java 有基本的了解并熟悉 HTML 文档将会很有帮助。

## 设置 Aspose.Words

要开始使用 Aspose.Words，首先需要将其添加到您的项目中。以下是使用 Maven 和 Gradle 设置库的步骤：

### Maven

将以下依赖项添加到您的 `pom.xml` 文件：

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle

将其包含在您的 `build.gradle` 文件：

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### 许可证获取

Aspose.Words 需要许可证才能使用完整功能。您可以获取免费试用版、申请临时许可证或购买永久许可证。请访问 [购买页面](https://purchase.aspose.com/buy) 了解更多详情。

要在 Java 项目中初始化 Aspose.Words，请确保已正确设置许可：

```java
import com.aspose.words.License;

public class InitializeAspose {
    public static void main(String[] args) throws Exception {
        License license = new License();
        license.setLicense("path/to/your/license/file.lic");
        
        System.out.println("Aspose.Words is ready to use!");
    }
}
```

## 实施指南

我们将根据想要实现的功能将实现分为几个部分。

### 在 HTML 文档中支持 VML

**概述：**
无论是否支持 VML，加载 HTML 文档都能实现矢量图形的多样化渲染。此功能在处理包含图表和形状等图形元素的文档时至关重要。

#### 逐步实施：

1. **设置加载选项**
   
   ```java
   import com.aspose.words.Document;
   import com.aspose.words.HtmlLoadOptions;

   HtmlLoadOptions loadOptions = new HtmlLoadOptions();
   loadOptions.setSupportVml(true); // 启用 VML 支持
   ```

2. **加载文档**
   
   ```java
   Document doc = new Document("path/to/VML conditional.htm", loadOptions);
   ```

3. **验证图像类型**
   
   确保图像类型符合您的期望：
   
   ```java
   import com.aspose.words.NodeType;
   import com.aspose.words.Shape;

   Shape imageShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
   String expectedImageType = "JPG"; // 根据实际逻辑调整

   if (!imageShape.getImageData().getImageType().toString().equals(expectedImageType)) {
       throw new AssertionError("Unexpected image type loaded.");
   }
   ```

### 加载 HTML 修复并处理警告

**概述：**
加载固定页面 HTML 文档可能会产生警告，需要进行管理才能准确处理。

#### 逐步实施：

1. **定义警告回调**
   
   ```java
   import com.aspose.words.IWarningCallback;
   import com.aspose.words.WarningInfo;
   import java.util.ArrayList;

   private static class ListDocumentWarnings implements IWarningCallback {
       private final ArrayList<WarningInfo> mWarnings = new ArrayList<>();

       public void warning(WarningInfo info) { 
           mWarnings.add(info); 
       }

       public ArrayList<WarningInfo> warnings() { return mWarnings; }
   }
   ```

2. **配置加载选项**
   
   ```java
   HtmlLoadOptions loadOptions = new HtmlLoadOptions();
   ListDocumentWarnings warningCallback = new ListDocumentWarnings();
   loadOptions.setWarningCallback(warningCallback);
   ```

3. **加载文档并检查警告**
   
   ```java
   Document doc = new Document("path/to/HtmlFixed.html", loadOptions);

   if (warningCallback.warnings().size() != 1) {
       throw new AssertionError("Unexpected number of warnings.");
   }
   ```

### 加密 HTML 文档

**概述：**
使用密码加密 HTML 文档可确保安全访问，这对于敏感信息至关重要。

#### 逐步实施：

1. **准备数字签名选项**
   
   ```java
   import com.aspose.words.CertificateHolder;
   import com.aspose.words.DigitalSignatureUtil;
   import com.aspose.words.SignOptions;

   CertificateHolder certificateHolder = CertificateHolder.create("path/to/morzal.pfx", "aw");
   SignOptions signOptions = new SignOptions();
   signOptions.setComments("Comment");
   signOptions.setSignTime(new Date());
   signOptions.setDecryptionPassword("docPassword");
   ```

2. **签名并加密文档**
   
   ```java
   String inputFileName = "path/to/Encrypted.docx";
   String outputFileName = "path/to/output/directory/HtmlLoadOptions.EncryptedHtml.html";

   DigitalSignatureUtil.sign(inputFileName, outputFileName, certificateHolder, signOptions);
   ```

3. **加载加密文档**
   
   ```java
   import com.aspose.words.Document;

   HtmlLoadOptions loadOptions = new HtmlLoadOptions("docPassword");
   Document doc = new Document(outputFileName, loadOptions);

   if (!doc.getText().trim().equals("Test encrypted document.")) {
       throw new AssertionError("Unexpected document text.");
   }
   ```

### HTML 加载选项的基本 URI

**概述：**
指定基本 URI 有助于解析相对 URI，尤其是在处理图像或其他链接资源时。

#### 逐步实施：

1. **使用基本 URI 配置加载选项**
   
   ```java
   HtmlLoadOptions loadOptions = new HtmlLoadOptions(LoadFormat.HTML, "", "path/to/imageDir");
   ```

2. **加载文档并验证图像**
   
   ```java
   import com.aspose.words.Document;
   import com.aspose.words.NodeType;

   Document doc = new Document("path/to/Missing image.html", loadOptions);
   Shape imageShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);

   if (!imageShape.isImage()) {
       throw new AssertionError("Expected an image shape.");
   }
   ```

### 导入 HTML 选择为结构化文档标签

**概述：**
输入 `<select>` 元素作为结构化文档标签允许在 Word 文档中更好地控制和格式化。

#### 逐步实施：

1. **设置首选控制类型**
   
   ```java
   import com.aspose.words.HtmlLoadOptions;
   import com.aspose.words.ControlType;

   HtmlLoadOptions loadOptions = new HtmlLoadOptions();
   loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag);
   ```

2. **加载文档并验证结构**
   
   ```java
   import com.aspose.words.Document;
   import com.aspose.words.NodeType;
   import com.aspose.words.StructuredDocumentTag;

   Document doc = new Document("path/to/Input HTML with select element.html", loadOptions);
   StructuredDocumentTag sdt = (StructuredDocumentTag)doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

   if (!sdt.getTagName().equals("Select")) {
       throw new AssertionError("Expected a Structured Document Tag with tag name 'Select'.");
   }
   ```

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}