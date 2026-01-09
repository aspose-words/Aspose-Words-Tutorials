---
title: "Encrypt docx with password – OOXML save with Aspose.Words Java"
linktitle: "Saving Documents as OOXML Format"
second_title: "Aspose.Words Java Document Processing API"
description: "Learn how to encrypt docx with password and change compression level while saving documents in OOXML format using Aspose.Words for Java."
weight: 20
date: 2026-01-09
url: /java/document-loading-and-saving/saving-documents-as-ooxml-format/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Encrypt docx with password – OOXML save with Aspose.Words Java

## Introduction to Saving Documents as OOXML Format in Aspose.Words for Java

In this guide, you'll learn how to **encrypt docx with password** and save documents in OOXML format using Aspose.Words for Java. OOXML (Office Open XML) is the modern file format used by Microsoft Word and many other office applications. We'll walk through the most common options—password protection, compliance levels, property updates, legacy character handling, and **how to change compression level**—so you can tailor the output to your exact needs.

## Quick Answers
- **How can I protect a Word file?** Use `OoxmlSaveOptions.setPassword("yourPassword")` before saving.  
- **What OOXML compliance level should I choose?** ISO 29500 2008 Strict for maximum compatibility with modern Office versions.  
- **Can I keep legacy control characters?** Yes, enable `setKeepLegacyControlChars(true)`.  
- **How do I change the compression level?** Set `setCompressionLevel(CompressionLevel.SUPER_FAST)` or `MAXIMUM` as required.  
- **Do these options affect file size?** Compression level and legacy character handling can noticeably change the final .docx size.

## What is “encrypt docx with password”?
Encrypting a DOCX file means the document is saved with AES‑256 encryption, requiring a password to open it in Word or any compatible viewer. This is essential for protecting confidential information when files are shared via email, cloud storage, or intranet portals.

## Why use OOXML saving options?
- **Security:** Password protection prevents unauthorized access.  
- **Compatibility:** Compliance settings ensure the file works across different Word versions.  
- **Performance:** Adjusting compression can speed up saving or reduce file size.  
- **Preservation:** Keeping legacy control characters maintains fidelity when converting older documents.

## Prerequisites
- Aspose.Words for Java library added to your project (Maven/Gradle or manual JAR).  
- Java 8 or higher.  
- A source document (`.docx` or `.doc`) you want to process.

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

> **Pro tip:** Choose a strong password and store it securely; the password cannot be recovered from the encrypted file.

## Setting OOXML Compliance

You can specify the OOXML compliance level when saving the document. For example, you can set it to ISO 29500:2008 (Strict). Here's how:

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

## How to Change Compression Level When Saving OOXML

You can adjust the compression level when saving the document. For example, you can set it to `SUPER_FAST` for minimal compression or `MAXIMUM` for the smallest file size. Here's how:

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

These are some of the key options and settings you can use when saving documents in OOXML format using Aspose.Words for Java. Feel free to explore more options and customize your document‑saving process as needed.

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

In this comprehensive guide, we've explored how to **encrypt docx with password** and save documents in OOXML format using Aspose.Words for Java. Whether you need to protect your files, ensure strict OOXML compliance, update document properties, preserve legacy control characters, or **change compression level**, Aspose.Words provides a versatile set of tools to meet your requirements.

## Frequently Asked Questions

**Q: How do I remove password protection from a password‑protected document?**  
A: Open the document with the correct password, then save it without specifying a password in `OoxmlSaveOptions`. This creates an unprotected copy.

**Q: Can I set custom properties when saving a document in OOXML format?**  
A: Yes. Use `BuiltInDocumentProperties` and `CustomDocumentProperties` on the `Document` object before calling `save()`.

**Q: What is the default compression level when saving a document in OOXML format?**  
A: The default is `CompressionLevel.NORMAL`. You can switch to `SUPER_FAST` for speed or `MAXIMUM` for the smallest file size.

**Q: Will enabling `keepLegacyControlChars` affect compatibility with modern Word versions?**  
A: Modern Word can open files with legacy control characters, but some older features may render differently. Use this option only when you need to preserve exact original content.

**Q: Is it possible to combine multiple save options (e.g., password + compression) in a single call?**  
A: Absolutely. Configure all desired properties on a single `OoxmlSaveOptions` instance before passing it to `doc.save()`.

---

**Last Updated:** 2026-01-09  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}