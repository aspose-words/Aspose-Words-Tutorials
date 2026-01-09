---
date: 2026-01-09
description: 了解如何使用 Aspose.Words for Java 在保存为 OOXML 格式的文档时，对 docx 加密并设置密码以及更改压缩级别。
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: 使用密码加密 docx – 使用 Aspose.Words Java 保存 OOXML
url: /zh/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words Java 对 docx 加密并使用密码 – OOXML 保存

## 在 Aspose.Words for Java 中将文档保存为 OOXML 格式的简介

在本指南中，您将学习如何 **encrypt docx with password** 并使用 Aspose.Words for Java 将文档保存为 OOXML 格式。OOXML（Office Open XML）是 Microsoft Word 以及许多其他办公应用程序使用的现代文件格式。我们将逐步演示最常用的选项——密码保护、合规级别、属性更新、遗留字符处理以及 **如何更改压缩级别**——帮助您根据实际需求定制输出。

## 快速答疑
- **如何保护 Word 文件？** 在保存前使用 `OoxmlSaveOptions.setPassword("yourPassword")`。  
- **应该选择哪种 OOXML 合规级别？** ISO 29500 2008 Strict 可实现与现代 Office 版本的最高兼容性。  
- **可以保留遗留控制字符吗？** 可以，启用 `setKeepLegacyControlChars(true)`。  
- **如何更改压缩级别？** 根据需要设置 `setCompressionLevel(CompressionLevel.SUPER_FAST)` 或 `MAXIMUM`。  
- **这些选项会影响文件大小吗？** 压缩级别和遗留字符处理会显著改变最终 .docx 的大小。

## 什么是 “encrypt docx with password”？
对 DOCX 文件进行加密意味着文档以 AES‑256 加密方式保存，打开时需要密码，无论是在 Word 还是任何兼容的查看器中。这对于通过电子邮件、云存储或内部门户共享文件时保护机密信息至关重要。

## 为什么使用 OOXML 保存选项？
- **安全性：** 密码保护可防止未授权访问。  
- **兼容性：** 合规设置确保文件在不同版本的 Word 中均能正常工作。  
- **性能：** 调整压缩可加快保存速度或减小文件体积。  
- **保真度：** 保留遗留控制字符可在转换旧文档时保持原始内容的完整性。

## 前置条件
- 已在项目中添加 Aspose.Words for Java 库（Maven/Gradle 或手动 JAR）。  
- Java 8 或更高版本。  
- 需要处理的源文档（`.docx` 或 `.doc`）。

## 使用密码加密保存文档

您可以在以 OOXML 格式保存文档的同时为其设置密码加密。操作方法如下：

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

> **专业提示：** 请选择强密码并妥善保管；密码无法从加密文件中恢复。

## 设置 OOXML 合规级别

保存文档时可以指定 OOXML 合规级别。例如，可将其设置为 ISO 29500:2008（Strict）。实现方式如下：

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

## 更新“最后保存时间”属性

保存文档时可以选择更新文档的 “Last Saved Time” 属性。实现方式如下：

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

## 保留遗留控制字符

如果文档中包含遗留控制字符，您可以在保存时选择保留它们。实现方式如下：

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

## 更改保存 OOXML 时的压缩级别

保存文档时可以调整压缩级别。例如，可将其设为 `SUPER_FAST` 以实现最小压缩，或设为 `MAXIMUM` 以获得最小文件体积。实现方式如下：

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

以上是使用 Aspose.Words for Java 将文档保存为 OOXML 格式时可用的一些关键选项和设置。欢迎进一步探索更多功能，并根据需要自定义文档保存流程。

## 完整源码：在 Aspose.Words for Java 中以 OOXML 格式保存文档

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

在本完整指南中，我们探讨了如何 **encrypt docx with password** 并使用 Aspose.Words for Java 将文档保存为 OOXML 格式。无论是需要保护文件、确保严格的 OOXML 合规、更新文档属性、保留遗留控制字符，还是 **更改压缩级别**，Aspose.Words 都提供了一套灵活的工具来满足您的需求。

## 常见问答

**问：如何移除受密码保护的文档的密码？**  
答：使用正确的密码打开文档后，在 `OoxmlSaveOptions` 中不再指定密码即可保存，这将生成一个未受保护的副本。

**问：在以 OOXML 格式保存文档时可以设置自定义属性吗？**  
答：可以。在调用 `save()` 之前，使用 `Document` 对象的 `BuiltInDocumentProperties` 和 `CustomDocumentProperties` 进行设置。

**问：以 OOXML 格式保存文档时默认的压缩级别是什么？**  
答：默认是 `CompressionLevel.NORMAL`。您可以切换到 `SUPER_FAST` 以提升速度，或 `MAXIMUM` 以获得最小文件体积。

**问：启用 `keepLegacyControlChars` 会影响与现代 Word 版本的兼容性吗？**  
答：现代 Word 能打开包含遗留控制字符的文件，但某些旧功能的呈现可能会有所不同。仅在需要保留原始内容的情况下使用此选项。

**问：是否可以在一次调用中组合多个保存选项（例如密码 + 压缩）？**  
答：完全可以。在将 `OoxmlSaveOptions` 实例传递给 `doc.save()` 之前，先配置所有所需属性即可。

---

**最后更新：** 2026-01-09  
**测试环境：** Aspose.Words for Java 24.12  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}