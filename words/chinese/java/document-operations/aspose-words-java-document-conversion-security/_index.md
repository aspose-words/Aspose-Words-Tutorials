---
"date": "2025-03-28"
"description": "学习如何使用 Aspose.Words for Java 掌握文档转换和安全。轻松转换为 ODT、确保架构合规性并加密文档。"
"title": "Aspose.Words Java&#58; ODT 文件的文档转换和安全性"
"url": "/zh/java/document-operations/aspose-words-java-document-conversion-security/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# 使用 Aspose.Words Java 掌握文档转换和安全

## 介绍

在文档管理领域，高效地转换和保护文档对开发者和企业至关重要。无论是确保与旧版本架构的兼容性，还是通过加密保护敏感信息，如果没有合适的工具，这些任务都可能令人望而生畏。本教程重点介绍如何使用 **Aspose.Words for Java** 简化将文档导出为开放文档文本 (ODT) 格式的过程，同时保持模式合规性并实施强大的安全措施。

在本指南中，您将学习如何：
- 导出符合 ODT 1.1 规范的文档。
- 在 ODT 文档中使用不同的测量单位。
- 使用 Aspose.Words for Java 通过密码加密 ODT/OTT 文件。

让我们开始吧！

## 先决条件

在开始之前，请确保您已进行以下设置：

### 所需库
你需要 **Aspose.Words for Java** 版本 25.3 或更高版本。以下是如何通过 Maven 或 Gradle 将其添加到项目中：

#### Maven：
```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

#### Gradle：
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### 环境设置
确保您的机器上安装了 Java，并且配置了用于 Java 开发的 IDE 或文本编辑器。

### 知识前提
建议对 Java 编程有基本的了解，以便有效地遵循本教程。

## 设置 Aspose.Words

要开始使用 Aspose.Words，首先确保它已正确集成到您的项目中。步骤如下：

1. **获取许可证**：您可以从 [Aspose](https://purchase.aspose.com/temporary-license/) 不受限制地测试所有功能。
   
2. **基本初始化**：
   ```java
   import com.aspose.words.Document;

   public class AsposeSetup {
       public static void main(String[] args) throws Exception {
           // 从磁盘加载文档
           Document doc = new Document("path/to/your/document.docx");
           
           // 将其保存为 ODT 格式作为示例用法
           doc.save("output/path/OdtSaveOptions.odt", com.aspose.words.SaveFormat.ODT);
       }
   }
   ```

## 实施指南

### 将文档导出为 ODT Schema 1.1

此功能允许您确保导出的文档符合 ODT 1.1 模式，这对于与某些应用程序的兼容性至关重要。

#### 概述
代码片段演示了如何在设置特定的模式要求和测量单位的同时导出文档。

#### 逐步实施

**3.1 配置导出选项**
```java
import com.aspose.words.Document;
import com.aspose.words.OdtSaveOptions;

// 加载源 Word 文档
Document document = new Document("YOUR_DOCUMENT_DIRECTORY/Rendering.docx");

// 初始化 ODT 保存选项并配置架构合规性
OdtSaveOptions saveOptions = new OdtSaveOptions();
saveOptions.setMeasureUnit(OdtSaveMeasureUnit.CENTIMETERS);
saveOptions.isStrictSchema11(true); // 设置为 true 以符合 ODT 1.1

// 使用这些设置保存文档
document.save("YOUR_OUTPUT_DIRECTORY/OdtSaveOptions.Odt11Schema.odt", saveOptions);
```

**3.2 验证导出设置**
保存后，请确保文档的设置正确：
```java
import com.aspose.words.MeasurementUnits;

Document loadedDoc = new Document("YOUR_OUTPUT_DIRECTORY/OdtSaveOptions.Odt11Schema.odt");
MeasurementUnits mu = loadedDoc.getLayoutOptions().getRevisionOptions().getMeasurementUnit();

assert mu == MeasurementUnits.CENTIMETERS;
```

### 使用不同的测量单位
在某些情况下，您可能需要出于风格或地区原因导出具有不同测量单位的文档。

#### 概述
此功能支持在 ODT 文档中指定测量单位，从而允许公制和英制系统之间的灵活性。

**3.3 设置测量单位**
```java
OdtSaveOptions saveOptions = new OdtSaveOptions();
// 选择您想要的单位：厘米或英寸
saveOptions.setMeasureUnit(OdtSaveMeasureUnit.CENTIMETERS);

document.save("YOUR_OUTPUT_DIRECTORY/OdtSaveOptions.Measurements.odt", saveOptions);
```

**3.4 验证样式中的测量单位**
为了确保应用正确的测量，请检查styles.xml内容：
```java
if (saveOptions.getMeasureUnit() == OdtSaveMeasureUnit.CENTIMETERS) {
    assert TestUtil.docPackageFileContainsString(
        "<style:paragraph-properties fo:orphans=\"2\" fo:widows=\"2\" style:tab-stop-distance=\"1.27cm\" />",
        "YOUR_OUTPUT_DIRECTORY/OdtSaveOptions.Measurements.odt", "styles.xml");
}
```

### 加密 ODT/OTT 文档
处理敏感文档时，安全性至关重要。此功能演示如何使用 Aspose.Words 加密文档。

#### 概述
使用密码加密您的文档，确保只有授权用户才能访问其内容。

**3.5 加密文档**
```java
import com.aspose.words.Document;
import com.aspose.words.OdtSaveOptions;

Document doc = new Document();
doc.getRange().appendText("Hello world!");

OdtSaveOptions saveOptions = new OdtSaveOptions(com.aspose.words.SaveFormat.ODT);
saveOptions.setPassword("@sposeEncrypted_1145");

// 加密保存文档
doc.save("YOUR_OUTPUT_DIRECTORY/OdtSaveOptions.Encrypt.odt", saveOptions);
```

**3.6 验证加密**
确保您的文档已加密：
```java
import com.aspose.words.FileFormatUtil;
import com.aspose.words.LoadOptions;

FileFormatInfo docInfo = FileFormatUtil.detectFileFormat("YOUR_OUTPUT_DIRECTORY/OdtSaveOptions.Encrypt.odt");
assert docInfo.isEncrypted();

// 使用正确的密码加载文档
Document loadedDoc = new Document(
    "YOUR_OUTPUT_DIRECTORY/OdtSaveOptions.Encrypt.odt",
    new LoadOptions("@sposeEncrypted_1145")
);

assert loadedDoc.getText().trim() == "Hello world!";
```

## 实际应用
以下是这些功能的一些实际用例：
1. **商业合规**：将文档导出到 ODT 1.1 可确保与各个行业的遗留系统兼容。
2. **国际化**：使用不同的测量单位可以实现跨测量标准不同的地区之间的无缝文档共享。
3. **数据保护**：加密敏感报告或合同可防止未经授权的访问，这对法律和金融部门至关重要。

## 性能考虑
为了优化使用 Aspose.Words 时的性能：
- 尽量减少文档中高分辨率图像的使用。
- 保持文档结构简单以减少处理时间。
- 定期更新到最新版本的 Aspose.Words for Java 以获得性能改进。

## 结论
在本教程中，您学习了如何使用 **Aspose.Words for Java**这些技术确保与各种架构版本的兼容性，并通过加密增强文档安全性。为了进一步探索 Aspose 的功能，您可以深入研究其丰富的文档并尝试其他功能。

准备好在你的项目中实施这些解决方案了吗？前往 [Aspose.Words 文档](https://reference.aspose.com/words/java/) 了解更多见解！

## 常见问题解答部分
**问：如何确保与旧版 ODT 兼容？**
答：使用 `OdtSaveOptions.isStrictSchema11(true)` 符合 ODT 1.1 规范。

**问：我可以轻松地在公制和英制单位之间切换吗？**
答：是的，将测量单位设置为 `OdtSaveOptions.setMeasureUnit()` 要么 `CENTIMETERS` 或者 `INCHES`。

**问：如果我的文档没有按预期加密怎么办？**
答：确保您已使用 `saveOptions.setPassword()`使用以下方式验证加密 `FileFormatUtil。detectFileFormat()`.

**问：如何解决加密文档的加载问题？**
答：请确保加载文档时使用正确的密码。

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}