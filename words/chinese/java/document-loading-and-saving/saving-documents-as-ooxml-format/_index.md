---
title: 在 Aspose.Words for Java 中将文档保存为 OOXML 格式
linktitle: 将文档保存为 OOXML 格式
second_title: Aspose.Words Java 文档处理 API
description: 了解如何使用 Aspose.Words for Java 将文档保存为 OOXML 格式。轻松保护、优化和自定义您的文件。
weight: 20
url: /zh/java/document-loading-and-saving/saving-documents-as-ooxml-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中将文档保存为 OOXML 格式


## 在 Aspose.Words for Java 中将文档保存为 OOXML 格式的简介

在本指南中，我们将探索如何使用 Aspose.Words for Java 将文档保存为 OOXML 格式。OOXML（Office Open XML）是 Microsoft Word 和其他办公应用程序使用的文件格式。我们将介绍将文档保存为 OOXML 格式的各种选项和设置。

## 先决条件

在开始之前，请确保您已在项目中设置了 Aspose.Words for Java 库。

## 使用密码加密保存文档

您可以在将文档保存为 OOXML 格式时使用密码加密文档。操作方法如下：

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

//加载文档
Document doc = new Document("Document.docx");

//创建OoxmlSaveOptions并设置密码
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

//加密保存文档
doc.save("EncryptedDoc.docx", saveOptions);
```

## 设置 OOXML 合规性

您可以在保存文档时指定 OOXML 合规级别。例如，您可以将其设置为 ISO 29500:2008（严格）。操作方法如下：

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

//加载文档
Document doc = new Document("Document.docx");

//针对 Word 2016 进行优化
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

//创建 OoxmlSaveOptions 并设置合规级别
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

//使用合规性设置保存文档
doc.save("ComplianceDoc.docx", saveOptions);
```

## 更新上次保存时间属性

您可以选择在保存文档时更新其“上次保存时间”属性。操作如下：

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

//加载文档
Document doc = new Document("Document.docx");

//创建 OoxmlSaveOptions 并启用更新上次保存时间属性
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

//使用更新后的属性保存文档
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## 保留旧版控制字符

如果您的文档包含旧版控制字符，您可以选择在保存时保留它们。操作方法如下：

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

//加载带有旧式控制字符的文档
Document doc = new Document("LegacyControlChars.doc");

//使用 FLAT_OPC 格式创建 OoxmlSaveOptions 并启用保留旧式控制字符
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

//使用旧式控制字符保存文档
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## 设置压缩级别

您可以在保存文档时调整压缩级别。例如，您可以将其设置为 SUPER_FAST 以获得最小压缩。操作方法如下：

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

//加载文档
Document doc = new Document("Document.docx");

//创建 OoxmlSaveOptions 并设置压缩级别
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

//使用指定的压缩级别保存文档
doc.save("FastCompressionDoc.docx", saveOptions);
```

这些是使用 Aspose.Words for Java 以 OOXML 格式保存文档时可以使用的一些关键选项和设置。您可以随意探索更多选项并根据需要自定义文档保存过程。

## 在 Aspose.Words for Java 中将文档保存为 OOXML 格式的完整源代码

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

在本综合指南中，我们探讨了如何使用 Aspose.Words for Java 将文档保存为 OOXML 格式。无论您需要使用密码加密文档、确保符合特定的 OOXML 标准、更新文档属性、保留旧控制字符还是调整压缩级别，Aspose.Words 都提供了一套多功能工具来满足您的需求。

## 常见问题解答

### 如何从受密码保护的文档中删除密码保护？

要从受密码保护的文档中删除密码保护，您可以使用正确的密码打开文档，然后保存它，而无需在保存选项中指定密码。这将保存没有密码保护的文档。

### 以 OOXML 格式保存文档时可以设置自定义属性吗？

是的，您可以在将文档保存为 OOXML 格式之前为其设置自定义属性。使用`BuiltInDocumentProperties`和`CustomDocumentProperties`类来设置各种属性，例如作者，标题，关键字和自定义属性。

### 以 OOXML 格式保存文档时的默认压缩级别是多少？

使用 Aspose.Words for Java 以 OOXML 格式保存文档时的默认压缩级别是`NORMAL`。您可以将压缩级别更改为`SUPER_FAST`或者`MAXIMUM`根据需要。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
