---
title: How to Set LoadOptions in Aspose.Words for Java
linktitle: Using Load Options
second_title: Aspose.Words Java Document Processing API
description: Learn how to set LoadOptions in Aspose.Words for Java, including how to specify temp folder, set word version, convert metafiles to PNG, and convert shape to math for flexible document processing.
weight: 11
url: /java/document-loading-and-saving/using-load-options/
date: 2025-12-27
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# How to Set LoadOptions in Aspose.Words for Java

In this tutorial we’ll walk through **how to set LoadOptions** for a variety of real‑world scenarios when working with Aspose.Words for Java. LoadOptions give you fine‑grained control over the way a document is opened—whether you need to update dirty fields, work with encrypted files, convert shapes to Office Math, or tell the library where to store temporary data. By the end you’ll be able to customize loading behavior to match your application’s exact requirements.

## Quick Answers
- **What is LoadOptions?** A configuration object that influences how Aspose.Words loads a document.  
- **Can I update fields while loading?** Yes—set `setUpdateDirtyFields(true)`.  
- **How do I open a password‑protected file?** Pass the password to the `LoadOptions` constructor.  
- **Is it possible to change the temporary folder?** Use `setTempFolder("path")`.  
- **Which method converts shapes to Office Math?** `setConvertShapeToOfficeMath(true)`.

## Why Use LoadOptions?
LoadOptions let you avoid post‑load processing steps, reduce memory usage, and ensure the document is interpreted exactly as you need. For example, converting metafiles to PNG during load prevents later rasterization issues, and specifying the MS Word version helps maintain layout fidelity when dealing with legacy files.

## Prerequisites
- Java 17 or later  
- Aspose.Words for Java (latest version)  
- A valid Aspose license for production use  

## Step‑by‑Step Guide

### Update Dirty Fields

When a document contains fields that have been edited but not refreshed, you can tell Aspose.Words to automatically update them during load.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

*The `setUpdateDirtyFields(true)` call ensures that any dirty fields are recalculated as soon as the document is opened.*

### Load Encrypted Document

If your source file is password‑protected, provide the password when creating the `LoadOptions` instance. You can also set a new password when saving to a different format.

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

### Convert Shape to Office Math

Some legacy documents store equations as drawing shapes. Enabling this option converts those shapes into native Office Math objects, which are easier to edit later.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

### Set MS Word Version

Specifying the target Word version helps the library choose the correct rendering rules, especially when dealing with older file formats.

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

### Use Temporary Folder

Large documents may generate temporary files (e.g., when extracting images). You can direct these files to a folder of your choosing, which is useful for sandboxed environments.

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

### Warning Callback

During loading, Aspose.Words may raise warnings (e.g., unsupported features). Implementing a callback lets you log or react to these events.

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Handle warnings as they arise during document loading.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

### Convert Metafiles to PNG

Metafiles such as WMF can be rasterized to PNG during load, ensuring consistent rendering across platforms.

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

## Complete Source Code For Working with Load Options in Aspose.Words for Java

```java
public void updateDirtyFields() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setUpdateDirtyFields(true);
	}
	Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
}
@Test
public void loadEncryptedDocument() throws Exception {
	Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
@Test
public void convertShapeToOfficeMath() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertShapeToOfficeMath(true);
	}
	Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
}
@Test
public void setMsWordVersion() throws Exception {
	// Create a new LoadOptions object, which will load documents according to MS Word 2019 specification by default
	// and change the loading version to Microsoft Word 2010.
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setMswVersion(MsWordVersion.WORD_2010);
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
@Test
public void useTempFolder() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setTempFolder("Your Directory Path");
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
@Test
public void warningCallback() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
public static class DocumentLoadingWarningCallback implements IWarningCallback {
	public void warning(WarningInfo info) {
		// Prints warnings and their details as they arise during document loading.
		System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
		System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
	}
}
@Test
public void convertMetafilesToPng() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertMetafilesToPng(true);
	}
	Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
@Test
public void loadChm() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setEncoding(Charset.forName("windows-1251"));
	}
	Document doc = new Document("Your Directory Path" + "HTML help.chm", loadOptions);
}
```

## Common Use Cases & Tips

- **Batch conversion pipelines** – Combine `setTempFolder` with a scheduled job to process hundreds of files without filling the system temp directory.  
- **Legacy document migration** – Use `setMswVersion` together with `setConvertShapeToOfficeMath` to bring old engineering documents into a modern format while preserving equations.  
- **Secure document handling** – Pair `loadEncryptedDocument` with `OdtSaveOptions` to re‑encrypt files with a new password in a different format.  

## Frequently Asked Questions

**Q: How can I handle warnings during document loading?**  
A: Implement a custom `IWarningCallback` (as shown in the *Warning Callback* example) and register it via `loadOptions.setWarningCallback(...)`. This lets you log, ignore, or abort based on warning severity.

**Q: Can I convert shapes to Office Math objects when loading a document?**  
A: Yes—call `loadOptions.setConvertShapeToOfficeMath(true)` before constructing the `Document`. The library will automatically replace compatible shapes with native Office Math objects.

**Q: How do I specify the MS Word version for document loading?**  
A: Use `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` (or any other enum value) to tell Aspose.Words which Word version’s rendering rules to apply.

**Q: What is the purpose of the `setTempFolder` method in LoadOptions?**  
A: It directs all temporary files generated during loading (such as extracted images) to a folder you control, which is essential for environments with restricted system temp directories.

**Q: Is it possible to convert metafiles like WMF to PNG during load?**  
A: Absolutely—enable it with `loadOptions.setConvertMetafilesToPng(true)`. This ensures raster images are stored as PNG, improving compatibility with modern viewers.

## Conclusion

We’ve covered the essential techniques for **how to set LoadOptions** in Aspose.Words for Java, from updating dirty fields to handling encrypted files, converting shapes, specifying the Word version, directing temporary storage, and more. By leveraging these options you can build robust, high‑performance document processing pipelines that adapt to a wide range of input scenarios.

---

**Last Updated:** 2025-12-27  
**Tested With:** Aspose.Words for Java 24.11  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}