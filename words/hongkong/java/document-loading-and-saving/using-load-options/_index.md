---
title: 在 Aspose.Words for Java 中使用載入選項
linktitle: 使用載入選項
second_title: Aspose.Words Java 文件處理 API
description: 掌握 Aspose.Words for Java 中的載入選項。自訂文件載入、處理加密、轉換形狀、設定 Word 版本等，以實現高效的 Java 文件處理。
weight: 11
url: /zh-hant/java/document-loading-and-saving/using-load-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中使用載入選項


## 在 Aspose.Words for Java 中使用載入選項簡介

在本教程中，我們將探討如何在 Aspose.Words for Java 中使用載入選項。載入選項可讓您自訂文件的載入和處理方式。我們將介紹各種場景，包括更新髒字段、載入加密文件、將形狀轉換為 Office Math、設定 MS Word 版本、指定臨時資料夾、處理警告以及將圖元文件轉換為 PNG。讓我們一步步深入。

## 更新髒字段

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

此程式碼片段示範如何更新文件中的髒欄位。這`setUpdateDirtyFields(true)`方法用於確保在文件載入期間更新髒字段。

## 載入加密文檔

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

在這裡，我們使用密碼載入加密文件。這`LoadOptions`建構函數接受文檔密碼，也可以在儲存文件時指定新密碼，使用`OdtSaveOptions`.

## 將造型轉換為 Office Math

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

此程式碼示範如何在文件載入期間將形狀轉換為 Office Math 物件。這`setConvertShapeToOfficeMath(true)`方法啟用此轉換。

## 設定 MS Word 版本

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

您可以指定用於文件載入的 MS Word 版本。在此範例中，我們使用以下命令將版本設定為 Microsoft Word 2010`setMswVersion`.

## 使用臨時資料夾

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

透過使用設定臨時資料夾`setTempFolder`，您可以控製文件處理過程中暫存文件的儲存位置。

## 警告回調

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        //處理文檔載入過程中出現的警告。
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

此程式碼示範如何設定警告回呼來處理文件載入期間的警告。您可以自訂發生警告時應用程式的行為。

## 將圖元檔轉換為 PNG

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

要在文件載入期間將圖元檔案（例如 WMF）轉換為 PNG 映像，您可以使用`setConvertMetafilesToPng(true)`方法。

## 在 Aspose.Words for Java 中使用載入選項的完整原始碼

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
	//建立一個新的LoadOptions對象，預設會根據MS Word 2019規格載入文檔
	//並將載入版本變更為Microsoft Word 2010。
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
		//列印文件載入過程中出現的警告及其詳細資訊。
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

## 結論

在本教程中，我們深入研究了在 Aspose.Words for Java 中使用載入選項的各個方面。載入選項在自訂文件載入和處理方式方面發揮著至關重要的作用，使您可以根據自己的特定需求自訂文件處理。讓我們回顧一下本指南中涵蓋的要點：

## 常見問題解答

### 如何處理文檔載入過程中的警告？

您可以設定警告回調，如下所示`warningCallback()`方法同上。客製化`DocumentLoadingWarningCallback`類別來根據應用程式的要求處理警告。

### 載入文件時可以將形狀轉換為 Office Math 物件嗎？

是的，您可以使用以下方法將形狀轉換為 Office Math 對象`loadOptions.setConvertShapeToOfficeMath(true)`.

### 如何指定載入文件的 MS Word 版本？

使用`loadOptions.setMswVersion(MsWordVersion.WORD_2010)`指定用於文件載入的 MS Word 版本。

### 目的是什麼`setTempFolder` method in Load Options?

這`setTempFolder`方法可讓您指定在文件處理過程中儲存臨時檔案的資料夾。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
