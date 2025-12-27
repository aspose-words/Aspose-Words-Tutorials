---
date: 2025-12-27
description: 學習如何在 Aspose.Words for Java 中設定 LoadOptions，包括如何指定暫存資料夾、設定 Word 版本、將中繼檔轉換為
  PNG，以及將圖形轉換為數學式，以實現彈性文件處理。
linktitle: Using Load Options
second_title: Aspose.Words Java Document Processing API
title: 如何在 Aspose.Words for Java 中設定 LoadOptions
url: /zh-hant/java/document-loading-and-saving/using-load-options/
weight: 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Aspose.Words for Java 中設定 LoadOptions

在本教學中，我們將逐步說明 **如何設定 LoadOptions**，以應對在使用 Aspose.Words for Java 時的各種實務情境。LoadOptions 讓您能細緻控制文件的開啟方式——無論是需要更新未刷新欄位、處理加密檔案、將圖形轉換為 Office Math，或是告訴函式庫暫存資料的存放位置。完成後，您即可依照應用程式的精確需求自訂載入行為。

## 快速解答
- **什麼是 LoadOptions？** 影響 Aspose.Words 載入文件方式的設定物件。  
- **載入時可以更新欄位嗎？** 可以——設定 `setUpdateDirtyFields(true)`。  
- **如何開啟受密碼保護的檔案？** 在 `LoadOptions` 建構子中傳入密碼。  
- **可以變更暫存資料夾嗎？** 使用 `setTempFolder("path")`。  
- **哪個方法可將圖形轉換為 Office Math？** `setConvertShapeToOfficeMath(true)`。

## 為何使用 LoadOptions？
LoadOptions 可讓您避免載入後的處理步驟、降低記憶體使用量，並確保文件以您所需的方式被解讀。例如，在載入時將中繼檔轉換為 PNG 可防止之後的點陣化問題，且指定 MS Word 版本有助於在處理舊版檔案時維持版面配置的忠實度。

## 先決條件
- Java 17 或更新版本  
- Aspose.Words for Java（最新版本）  
- 用於正式環境的有效 Aspose 授權  

## 逐步指南

### 更新未刷新欄位

當文件中含有已編輯但未重新整理的欄位時，您可以指示 Aspose.Words 在載入時自動更新它們。

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

*`setUpdateDirtyFields(true)` 呼叫可確保任何未刷新欄位在文件開啟時即被重新計算。*

### 載入加密文件

如果來源檔案受密碼保護，請在建立 `LoadOptions` 實例時提供密碼。另存為其他格式時亦可設定新密碼。

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

### 將圖形轉換為 Office Math

某些舊版文件會將方程式以繪圖圖形儲存。啟用此選項可將這些圖形轉換為原生 Office Math 物件，之後編輯更為便利。

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

### 設定 MS Word 版本

指定目標 Word 版本可協助函式庫選擇正確的渲染規則，特別是在處理較舊檔案格式時。

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

### 使用暫存資料夾

大型文件在處理過程中可能產生暫存檔（例如擷取影像時）。您可以將這些檔案導向自行指定的資料夾，對於受限的沙盒環境相當有用。

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

### 警告回呼

載入過程中，Aspose.Words 可能拋出警告（例如不支援的功能）。實作回呼可讓您記錄或回應這些事件。

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

### 將中繼檔轉換為 PNG

如 WMF 等中繼檔可在載入時點陣化為 PNG，確保跨平台的渲染一致性。

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

## 完整範例程式碼：在 Aspose.Words for Java 中使用 Load Options

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

## 常見使用情境與技巧
- **批次轉換管線** – 結合 `setTempFolder` 與排程工作，可處理數百個檔案而不會填滿系統暫存目錄。  
- **舊版文件遷移** – 使用 `setMswVersion` 搭配 `setConvertShapeToOfficeMath`，將舊工程文件轉換為現代格式，同時保留方程式。  
- **安全文件處理** – 結合 `loadEncryptedDocument` 與 `OdtSaveOptions`，在不同格式中以新密碼重新加密檔案。  

## 常見問題

**Q: 如何在文件載入期間處理警告？**  
A: 實作自訂的 `IWarningCallback`（如 *警告回呼* 範例所示），並透過 `loadOptions.setWarningCallback(...)` 註冊。這讓您能依警告嚴重程度記錄、忽略或中止。

**Q: 載入文件時能將圖形轉換為 Office Math 物件嗎？**  
A: 可以——在建立 `Document` 之前呼叫 `loadOptions.setConvertShapeToOfficeMath(true)`。函式庫會自動將相容的圖形替換為原生 Office Math 物件。

**Q: 如何指定文件載入時的 MS Word 版本？**  
A: 使用 `loadOptions.setMswVersion(MsWordVersion.WORD_2010)`（或其他列舉值），告訴 Aspose.Words 套用哪個 Word 版本的渲染規則。

**Q: `setTempFolder` 方法在 LoadOptions 中的用途是什麼？**  
A: 它會將載入過程中產生的所有暫存檔（例如擷取的影像）導向您指定的資料夾，對於系統暫存目錄受限的環境尤為重要。

**Q: 是否可以在載入時將 WMF 等中繼檔轉換為 PNG？**  
A: 完全可以——使用 `loadOptions.setConvertMetafilesToPng(true)` 啟用。這可確保點陣圖以 PNG 形式儲存，提高與現代檢視器的相容性。

## 結論

我們已說明在 Aspose.Words for Java 中 **如何設定 LoadOptions** 的關鍵技巧，從更新未刷新欄位、處理加密檔案、轉換圖形、指定 Word 版本、導向暫存儲存等多項功能。善用這些選項，您即可構建穩健且高效能的文件處理管線，能因應各種輸入情境。

---

**最後更新：** 2025-12-27  
**測試環境：** Aspose.Words for Java 24.11  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}