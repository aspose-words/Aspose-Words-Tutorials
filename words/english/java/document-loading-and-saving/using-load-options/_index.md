---
title: Using Load Options in Aspose.Words for Java
linktitle: Using Load Options
second_title: Aspose.Words Java Document Processing API
description: Mastering Load Options in Aspose.Words for Java. Customize document loading, handle encryption, convert shapes, set Word versions, and more for efficient Java document processing.
weight: 11
url: /java/document-loading-and-saving/using-load-options/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Using Load Options in Aspose.Words for Java


## Introduction to Working with Load Options in Aspose.Words for Java

In this tutorial, we will explore how to work with Load Options in Aspose.Words for Java. Load Options allow you to customize how documents are loaded and processed. We will cover various scenarios, including updating dirty fields, loading encrypted documents, converting shapes to Office Math, setting the MS Word version, specifying a temporary folder, handling warnings, and converting metafiles to PNG. Let's dive in step by step.

## Update Dirty Fields

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

This code snippet demonstrates how to update dirty fields in a document. The `setUpdateDirtyFields(true)` method is used to ensure that dirty fields are updated during document loading.

## Load Encrypted Document

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

Here, we load an encrypted document using a password. The `LoadOptions` constructor accepts the document password, and you can also specify a new password when saving the document using `OdtSaveOptions`.

## Convert Shape to Office Math

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

This code demonstrates how to convert shapes to Office Math objects during document loading. The `setConvertShapeToOfficeMath(true)` method enables this conversion.

## Set MS Word Version

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

You can specify the MS Word version for document loading. In this example, we set the version to Microsoft Word 2010 using `setMswVersion`.

## Use Temporary Folder

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

By setting the temporary folder using `setTempFolder`, you can control where temporary files are stored during document processing.

## Warning Callback

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

This code demonstrates how to set up a warning callback to handle warnings during document loading. You can customize the behavior of your application when warnings occur.

## Convert Metafiles to PNG

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

To convert metafiles (e.g., WMF) to PNG images during document loading, you can use the `setConvertMetafilesToPng(true)` method.

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

## Conclusion

In this tutorial, we have delved into various aspects of working with Load Options in Aspose.Words for Java. Load Options play a crucial role in customizing how documents are loaded and processed, allowing you to tailor your document processing to your specific needs. Let's recap the key points covered in this guide:

## FAQ's

### How can I handle warnings during document loading?

You can set up a warning callback as shown in the `warningCallback()` method above. Customize the `DocumentLoadingWarningCallback` class to handle warnings according to your application's requirements.

### Can I convert shapes to Office Math objects when loading a document?

Yes, you can convert shapes to Office Math objects by using `loadOptions.setConvertShapeToOfficeMath(true)`.

### How do I specify the MS Word version for document loading?

Use `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` to specify the MS Word version for document loading.

### What is the purpose of the `setTempFolder` method in Load Options?

The `setTempFolder` method allows you to specify the folder where temporary files are stored during document processing.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
