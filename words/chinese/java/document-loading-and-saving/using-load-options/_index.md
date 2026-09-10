---
date: 2025-12-27
description: 了解如何在 Aspose.Words for Java 中设置 LoadOptions，包括如何指定临时文件夹、设置 Word 版本、将元文件转换为
  PNG，以及将形状转换为数学公式，以实现灵活的文档处理。
linktitle: Using Load Options
second_title: Aspose.Words Java Document Processing API
title: 如何在 Aspose.Words for Java 中设置 LoadOptions
url: /zh/java/document-loading-and-saving/using-load-options/
weight: 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Aspose.Words for Java 中设置 LoadOptions

在本教程中，我们将逐步演示 **如何为各种实际场景设置 LoadOptions**，以便在使用 Aspose.Words for Java 时使用。LoadOptions 让您能够细粒度地控制文档的打开方式——无论是需要更新脏字段、处理加密文件、将形状转换为 Office Math，还是指定库存放临时数据的位置。阅读完本教程后，您将能够根据应用程序的精确需求自定义加载行为。

## 快速回答
- **什么是 LoadOptions？** 用于影响 Aspose.Words 加载文档方式的配置对象。  
- **可以在加载时更新字段吗？** 可以——设置 `setUpdateDirtyFields(true)`。  
- **如何打开受密码保护的文件？** 将密码传递给 `LoadOptions` 构造函数。  
- **可以更改临时文件夹吗？** 使用 `setTempFolder("path")`。  
- **哪个方法可以将形状转换为 Office Math？** `setConvertShapeToOfficeMath(true)`。

## 为什么要使用 LoadOptions？
LoadOptions 可以帮助您避免加载后再进行处理的步骤，降低内存占用，并确保文档按照您的需求进行解释。例如，在加载时将元文件转换为 PNG 可以防止后续的光栅化问题，指定 MS Word 版本有助于在处理旧版文件时保持布局的忠实度。

## 前置条件
- Java 17 或更高版本  
- Aspose.Words for Java（最新版本）  
- 用于生产环境的有效 Aspose 许可证  

## 步骤指南

### 更新脏字段

当文档中包含已编辑但未刷新（脏）的字段时，您可以让 Aspose.Words 在加载期间自动更新它们。

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

*调用 `setUpdateDirtyFields(true)` 可确保在文档打开时立即重新计算所有脏字段。*

### 加载加密文档

如果源文件受密码保护，请在创建 `LoadOptions` 实例时提供密码。保存为其他格式时也可以设置新密码。

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

### 将形状转换为 Office Math

某些旧版文档将公式存储为绘图形状。启用此选项后，这些形状会被转换为原生 Office Math 对象，后续编辑更为方便。

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

### 设置 MS Word 版本

指定目标 Word 版本可帮助库选择正确的渲染规则，尤其是在处理旧文件格式时。

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

### 使用临时文件夹

大型文档在加载时可能会生成临时文件（例如提取图像时）。您可以将这些文件定向到自定义文件夹，这在受限的沙箱环境中尤为有用。

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

### 警告回调

加载过程中，Aspose.Words 可能会抛出警告（例如不受支持的特性）。实现回调可以让您记录或响应这些事件。

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

### 将元文件转换为 PNG

如 WMF 等元文件可以在加载时光栅化为 PNG，确保跨平台渲染的一致性。

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

## 完整示例代码：在 Aspose.Words for Java 中使用 LoadOptions

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

## 常见使用场景与技巧

- **批量转换流水线** – 将 `setTempFolder` 与计划任务结合，处理数百个文件而不占满系统临时目录。  
- **旧版文档迁移** – 使用 `setMswVersion` 配合 `setConvertShapeToOfficeMath` 将旧工程文档迁移到现代格式，同时保留公式。  
- **安全文档处理** – 将 `loadEncryptedDocument` 与 `OdtSaveOptions` 配合，在不同格式下使用新密码重新加密文件。  

## 常见问答

**问：如何在文档加载期间处理警告？**  
答：实现自定义的 `IWarningCallback`（如 *警告回调* 示例所示），并通过 `loadOptions.setWarningCallback(...)` 注册。这样您可以根据警告的严重程度记录、忽略或中止操作。

**问：加载文档时能将形状转换为 Office Math 对象吗？**  
答：可以——在构造 `Document` 之前调用 `loadOptions.setConvertShapeToOfficeMath(true)`。库会自动将兼容的形状替换为原生 Office Math 对象。

**问：如何指定文档加载时使用的 MS Word 版本？**  
答：使用 `loadOptions.setMswVersion(MsWordVersion.WORD_2010)`（或其他枚举值），告诉 Aspose.Words 应采用哪个 Word 版本的渲染规则。

**问：LoadOptions 中的 `setTempFolder` 方法有什么作用？**  
答：它将加载期间生成的所有临时文件（如提取的图像）定向到您指定的文件夹，这在系统临时目录受限的环境中尤为关键。

**问：是否可以在加载时将 WMF 等元文件转换为 PNG？**  
答：完全可以——通过 `loadOptions.setConvertMetafilesToPng(true)` 启用。这样光栅图像会以 PNG 形式保存，提高与现代查看器的兼容性。

## 结论

我们已经介绍了在 Aspose.Words for Java 中 **如何设置 LoadOptions** 的关键技术，从更新脏字段、处理加密文件、转换形状、指定 Word 版本、定向临时存储到更多高级选项。通过合理使用这些配置，您可以构建稳健、高性能的文档处理流水线，轻松应对各种输入场景。

---

**最后更新：** 2025-12-27  
**测试环境：** Aspose.Words for Java 24.11  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}