---
"description": "了解如何使用 Aspose.Words for Java 以 OOXML 格式儲存文件。輕鬆保護、優化和自訂您的文件。"
"linktitle": "將文件儲存為 OOXML 格式"
"second_title": "Aspose.Words Java文件處理API"
"title": "在 Aspose.Words for Java 中將文件儲存為 OOXML 格式"
"url": "/zh-hant/java/document-loading-and-saving/saving-documents-as-ooxml-format/"
"weight": 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中將文件儲存為 OOXML 格式


## 在 Aspose.Words for Java 中將文件儲存為 OOXML 格式的簡介

在本指南中，我們將探討如何使用 Aspose.Words for Java 以 OOXML 格式儲存文件。 OOXML（Office Open XML）是Microsoft Word和其他辦公室應用程式所使用的檔案格式。我們將介紹以 OOXML 格式儲存文件的各種選項和設定。

## 先決條件

在開始之前，請確保您的專案中已設定了 Aspose.Words for Java 程式庫。

## 使用密碼加密儲存文檔

您可以使用密碼加密您的文檔，同時將其儲存為 OOXML 格式。您可以按照以下步驟操作：

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// 載入文檔
Document doc = new Document("Document.docx");

// 建立OoxmlSaveOptions並設定密碼
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// 加密保存文檔
doc.save("EncryptedDoc.docx", saveOptions);
```

## 設定 OOXML 合規性

您可以在儲存文件時指定 OOXML 合規等級。例如，您可以將其設定為 ISO 29500:2008（嚴格）。方法如下：

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// 載入文檔
Document doc = new Document("Document.docx");

// 針對 Word 2016 進行最佳化
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// 建立 OoxmlSaveOptions 並設定合規級別
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// 使用合規性設定儲存文檔
doc.save("ComplianceDoc.docx", saveOptions);
```

## 更新上次儲存時間屬性

您可以選擇在儲存文件時更新其「上次儲存時間」屬性。方法如下：

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// 載入文檔
Document doc = new Document("Document.docx");

// 建立 OoxmlSaveOptions 並啟用更新上次儲存時間屬性
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// 使用更新後的屬性儲存文檔
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## 保留舊版控製字符

如果您的文件包含舊式控製字符，您可以選擇在儲存時保留它們。方法如下：

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// 載入具有舊式控製字元的文檔
Document doc = new Document("LegacyControlChars.doc");

// 使用 FLAT_OPC 格式建立 OoxmlSaveOptions 並啟用保留舊式控製字符
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// 使用舊式控製字元儲存文檔
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## 設定壓縮等級

您可以在儲存文件時調整壓縮等級。例如，您可以將其設為 SUPER_FAST 以實現最小壓縮。方法如下：

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// 載入文檔
Document doc = new Document("Document.docx");

// 建立OoxmlSaveOptions並設定壓縮級別
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// 使用指定的壓縮等級儲存文檔
doc.save("FastCompressionDoc.docx", saveOptions);
```

這些是使用 Aspose.Words for Java 以 OOXML 格式儲存文件時可以使用的一些關鍵選項和設定。請隨意探索更多選項並根據需要自訂文件儲存流程。

## 在 Aspose.Words for Java 中將文件儲存為 OOXML 格式的完整原始碼

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

## 結論

在本綜合指南中，我們探討如何使用 Aspose.Words for Java 以 OOXML 格式儲存文件。無論您需要使用密碼加密文件、確保符合特定的 OOXML 標準、更新文件屬性、保留舊式控製字元或調整壓縮級別，Aspose.Words 都提供了一套多功能工具來滿足您的要求。

## 常見問題解答

### 如何從受密碼保護的文件中刪除密碼保護？

若要從受密碼保護的文檔中刪除密碼保護，您可以使用正確的密碼開啟該文檔，然後儲存它，而無需在儲存選項中指定密碼。這將保存沒有密碼保護的文件。

### 以 OOXML 格式儲存文件時可以設定自訂屬性嗎？

是的，您可以在將文件儲存為 OOXML 格式之前為其設定自訂屬性。使用 `BuiltInDocumentProperties` 和 `CustomDocumentProperties` 類別來設定各種屬性，例如作者、標題、關鍵字和自訂屬性。

### 以 OOXML 格式儲存文件時的預設壓縮等級是多少？

使用 Aspose.Words for Java 以 OOXML 格式儲存文件時的預設壓縮等級是 `NORMAL`。您可以將壓縮等級變更為 `SUPER_FAST` 或者 `MAXIMUM` 根據需要。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}