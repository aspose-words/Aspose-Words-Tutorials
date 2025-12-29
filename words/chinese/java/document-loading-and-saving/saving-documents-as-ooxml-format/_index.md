---
date: 2025-12-29
description: 了解如何使用 Aspose.Words for Java 的保存选项为 docx 加密密码，轻松实现 OOXML 文件的安全、优化和自定义。
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: 如何使用 Aspose.Words for Java 对 DOCX 进行密码加密
url: /zh/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words for Java 对 DOCX 进行密码加密

在本指南中，您将了解 **如何使用密码加密 docx**，在以 OOXML 格式保存文档时使用 Aspose.Words for Java。无论是保护机密报告还是确保合同草稿的安全，下面的步骤都将向您展示如何应用密码保护并微调其他 OOXML 保存选项。

## 快速解答
- **我可以使用密码加密 DOCX 文件吗？** 可以，在保存之前使用 `OoxmlSaveOptions.setPassword()`。  
- **哪个类控制 OOXML 保存设置？** `OoxmlSaveOptions`（属于 Aspose.Words）。  
- **密码保护需要许可证吗？** 生产环境下需要有效的 Aspose.Words 许可证。  
- **我可以将加密与合规性设置结合使用吗？** 完全可以——在同一个 `OoxmlSaveOptions` 实例上同时调用 `setPassword` 和 `setCompliance`。  
- **有哪些压缩级别可供选择？** 通过 `CompressionLevel` 提供 `NORMAL`、`SUPER_FAST` 和 `MAXIMUM`。

## 什么是 “encrypt docx with password”？
对 DOCX 文件进行加密意味着文件内容以加密形式存储，只有在提供正确密码后才能打开。这可以防止未授权访问敏感信息，同时在提供密码后仍可使用标准的 Word 工具打开文件。

## 为什么使用 Aspose.Words 保存选项进行加密？
Aspose.Words 提供了一套丰富的 **aspose words save options**，让您不仅可以控制加密，还可以设置合规级别、压缩方式以及旧版字符处理——全部通过 Java 代码完成。这消除了手动后处理或使用第三方工具的需求。

## 前置条件
- Java Development Kit (JDK 8 或更高)  
- 已在项目中添加 Aspose.Words for Java 库（Maven/Gradle 或 JAR）  
- 生产环境下的有效 Aspose.Words 许可证（评估版可选）

## 使用密码加密保存文档

您可以在以 OOXML 格式保存文档时为其设置密码加密。操作方法如下：

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the password
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Save the document with encryption
doc.save("EncryptedDoc.docx", saveOptions);
```

## 设置 OOXML 合规性

保存文档时可以指定 OOXML 合规级别。例如，您可以将其设置为 ISO 29500:2008（Strict）。操作方法如下：

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Load the document
Document doc = new Document("Document.docx");

// Optimize for Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Create OoxmlSaveOptions and set the compliance level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Save the document with compliance setting
doc.save("ComplianceDoc.docx", saveOptions);
```

## 更新 “最后保存时间” 属性

保存文档时可以选择更新文档的 “Last Saved Time” 属性。操作方法如下：

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and enable updating the Last Saved Time property
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Save the document with the updated property
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## 保留旧版控制字符

如果文档中包含旧版控制字符，您可以在保存时选择保留它们。操作方法如下：

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// Load a document with legacy control characters
Document doc = new Document("LegacyControlChars.doc");

// Create OoxmlSaveOptions with the FLAT_OPC format and enable keeping legacy control characters
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Save the document with legacy control characters
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## 设置压缩级别

保存文档时可以调整压缩级别。例如，您可以将其设置为 **SUPER_FAST** 以实现最小压缩。操作方法如下：

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the compression level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Save the document with the specified compression level
doc.save("FastCompressionDoc.docx", saveOptions);
```

以上是使用 Aspose.Words for Java 将文档保存为 OOXML 格式时可用的一些关键选项和设置。欢迎探索更多选项并根据需要自定义文档保存过程。

## 完整源码：在 Aspose.Words for Java 中将文档保存为 OOXML 格式

```java
public void encryptDocxWithPassword() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setPassword("password"); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.EncryptDocxWithPassword.docx", saveOptions);
}
@Test
public void ooxmlComplianceIso29500_2008_Strict() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.OoxmlComplianceIso29500_2008_Strict.docx", saveOptions);
}
@Test
public void updateLastSavedTimeProperty() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setUpdateLastSavedTimeProperty(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
}
@Test
public void keepLegacyControlChars() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Legacy control character.doc");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setKeepLegacyControlChars(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
}
@Test
public void setCompressionLevel() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.SetCompressionLevel.docx", saveOptions);
}
```

## 结论

在本综合指南中，我们探讨了如何 **encrypt docx with password**，以及如何使用 Aspose.Words for Java 微调一系列 OOXML 保存选项。无论是需要保护机密内容、满足严格的 ISO 合规、保留旧版字符，还是控制压缩，库都通过同一个 `OoxmlSaveOptions` API 为您提供细粒度的控制。

## 常见问题

**问：如何移除受密码保护的文档的密码？**  
答：使用正确的密码打开文档后，再次保存时不要调用 `setPassword`。新文件将不再受保护。

**问：在以 OOXML 格式保存文档时可以设置自定义属性吗？**  
答：可以。在调用 `save` 之前，使用 `Document` 对象的 `BuiltInDocumentProperties` 或 `CustomDocumentProperties` 进行设置。

**问：以 OOXML 格式保存文档时默认的压缩级别是什么？**  
答：默认是 `NORMAL`。您可以切换到 `SUPER_FAST` 以提升速度，或 `MAXIMUM` 以获得更小的文件体积。

**问：aspose words save options 能兼容旧版 Word 吗？**  
答：能。通过调整 `MsWordVersion` 和合规性设置，您可以针对 Word 2007‑2019 进行兼容性处理。

**问：是否可以在一次操作中组合多个保存选项？**  
答：完全可以。创建一个 `OoxmlSaveOptions` 实例，设置所有需要的属性（密码、合规性、压缩等），然后将其传递给 `doc.save()`。

---

**最后更新：** 2025-12-29  
**测试环境：** Aspose.Words for Java 24.12  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}