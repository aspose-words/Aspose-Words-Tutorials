---
"description": "掌握 Aspose.Words for Java 中的加载选项。自定义文档加载、处理加密、转换形状、设置 Word 版本等，以实现高效的 Java 文档处理。"
"linktitle": "使用加载选项"
"second_title": "Aspose.Words Java文档处理API"
"title": "在 Aspose.Words for Java 中使用加载选项"
"url": "/zh/java/document-loading-and-saving/using-load-options/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中使用加载选项


## Aspose.Words for Java 中加载选项的使用简介

在本教程中，我们将探索如何使用 Aspose.Words for Java 中的“加载选项”。加载选项允许您自定义文档的加载和处理方式。我们将涵盖各种场景，包括更新脏字段、加载加密文档、将形状转换为 Office Math、设置 MS Word 版本、指定临时文件夹、处理警告以及将图元文件转换为 PNG。让我们一步一步深入了解。

## 更新脏字段

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

此代码片段演示了如何更新文档中的脏字段。 `setUpdateDirtyFields(true)` 方法用于确保在文档加载过程中更新脏字段。

## 加载加密文档

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

在这里，我们使用密码加载加密文档。 `LoadOptions` 构造函数接受文档密码，您还可以在保存文档时使用 `OdtSaveOptions`。

## 将形状转换为 Office Math

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

此代码演示了如何在文档加载期间将形状转换为 Office Math 对象。 `setConvertShapeToOfficeMath(true)` 方法可以实现这种转换。

## 设置 MS Word 版本

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

您可以指定要加载文档的 MS Word 版本。在本例中，我们使用以下代码将版本设置为 Microsoft Word 2010： `setMswVersion`。

## 使用临时文件夹

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

通过使用设置临时文件夹 `setTempFolder`，您可以控制在文档处理过程中存储临时文件的位置。

## 警告回调

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // 处理文档加载过程中出现的警告。
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

此代码演示了如何设置警告回调来处理文档加载过程中出现的警告。您可以自定义应用在出现警告时的行为。

## 将图元文件转换为 PNG

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

要在文档加载期间将图元文件（例如 WMF）转换为 PNG 图像，您可以使用 `setConvertMetafilesToPng(true)` 方法。

## 在 Aspose.Words for Java 中使用加载选项的完整源代码

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
	// 创建一个新的 LoadOptions 对象，该对象将默认按照 MS Word 2019 规范加载文档
	// 并将加载版本更改为Microsoft Word 2010。
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
		// 打印文档加载过程中出现的警告及其详细信息。
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

## 结论

在本教程中，我们深入探讨了 Aspose.Words for Java 中加载选项的各个方面。加载选项在自定义文档的加载和处理方式中起着至关重要的作用，它允许您根据特定需求定制文档处理方式。让我们回顾一下本指南中涵盖的要点：

## 常见问题解答

### 如何处理文档加载期间的警告？

您可以设置警告回调，如下所示 `warningCallback()` 方法。自定义 `DocumentLoadingWarningCallback` 根据应用程序的要求处理警告。

### 加载文档时可以将形状转换为 Office Math 对象吗？

是的，您可以使用以下方法将形状转换为 Office Math 对象 `loadOptions。setConvertShapeToOfficeMath(true)`.

### 如何指定用于文档加载的 MS Word 版本？

使用 `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` 指定用于加载文档的 MS Word 版本。

### 的目的是什么 `setTempFolder` 加载选项中的方法？

这 `setTempFolder` 方法允许您指定在文档处理期间存储临时文件的文件夹。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}