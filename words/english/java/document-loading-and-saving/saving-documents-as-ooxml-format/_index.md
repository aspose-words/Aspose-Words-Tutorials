---
title: Saving Documents as OOXML Format in Aspose.Words for Java
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
description: Learn how to save documents in OOXML format with Aspose.Words for Java. Secure, optimize, and customize your files effortlessly. 
weight: 20
url: /java/document-loading-and-saving/saving-documents-as-ooxml-format/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Saving Documents as OOXML Format in Aspose.Words for Java


## Introduction to Saving Documents as OOXML Format in Aspose.Words for Java

In this guide, we will explore how to save documents in OOXML format using Aspose.Words for Java. OOXML (Office Open XML) is a file format used by Microsoft Word and other office applications. We'll cover various options and settings for saving documents in OOXML format.

## Prerequisites

Before we begin, make sure you have the Aspose.Words for Java library set up in your project.

## Saving a Document with Password Encryption

You can encrypt your document with a password while saving it in OOXML format. Here's how you can do it:

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

## Setting OOXML Compliance

You can specify the OOXML compliance level when saving the document. For example, you can set it to ISO 29500:2008 (Strict). Here's how:

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

## Updating Last Saved Time Property

You can choose to update the "Last Saved Time" property of the document when saving it. Here's how:

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

## Keeping Legacy Control Characters

If your document contains legacy control characters, you can choose to keep them while saving. Here's how:

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

## Setting Compression Level

You can adjust the compression level when saving the document. For example, you can set it to SUPER_FAST for minimal compression. Here's how:

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

These are some of the key options and settings you can use when saving documents in OOXML format using Aspose.Words for Java. Feel free to explore more options and customize your document-saving process as needed.

## Complete Source Code For Saving Documents as OOXML Format in Aspose.Words for Java

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

## Conclusion

In this comprehensive guide, we've explored how to save documents in OOXML format using Aspose.Words for Java. Whether you need to encrypt your documents with passwords, ensure compliance with specific OOXML standards, update document properties, preserve legacy control characters, or adjust compression levels, Aspose.Words provides a versatile set of tools to meet your requirements.

## FAQ's

### How do I remove password protection from a password-protected document?

To remove password protection from a password-protected document, you can open the document with the correct password and then save it without specifying a password in the save options. This will save the document without password protection.

### Can I set custom properties when saving a document in OOXML format?

Yes, you can set custom properties for a document before saving it in OOXML format. Use the `BuiltInDocumentProperties` and `CustomDocumentProperties` classes to set various properties such as author, title, keywords, and custom properties.

### What is the default compression level when saving a document in OOXML format?

The default compression level when saving a document in OOXML format using Aspose.Words for Java is `NORMAL`. You can change the compression level to `SUPER_FAST` or `MAXIMUM` as needed.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
