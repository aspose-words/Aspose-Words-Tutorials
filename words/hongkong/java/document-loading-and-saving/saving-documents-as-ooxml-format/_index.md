---
date: 2025-12-29
description: 學習如何使用 Aspose.Words for Java 的儲存選項，以密碼加密 docx。輕鬆保護、優化及自訂您的 OOXML 檔案。
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: 如何使用 Aspose.Words for Java 為 DOCX 設定密碼加密
url: /zh-hant/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words for Java 為 DOCX 加密密碼

在本指南中，您將了解 **如何使用密碼加密 docx**，在以 OOXML 格式儲存文件時使用 Aspose.Words for Java。無論是保護機密報告或是確保合約草稿的安全，以下步驟將完整說明如何套用密碼保護以及微調其他 OOXML 儲存選項。

## 快速回答
- **我可以使用密碼加密 DOCX 檔案嗎？** 可以，在儲存前使用 `OoxmlSaveOptions.setPassword()`。  
- **哪個類別負責 OOXML 儲存設定？** `OoxmlSaveOptions`（屬於 Aspose.Words）。  
- **加密功能需要授權嗎？** 生產環境必須使用有效的 Aspose.Words 授權。  
- **我可以同時設定加密與合規性嗎？** 完全可以——在同一個 `OoxmlSaveOptions` 實例上同時呼叫 `setPassword` 與 `setCompliance`。  
- **有哪些壓縮等級可供選擇？** 透過 `CompressionLevel` 可設定 `NORMAL`、`SUPER_FAST` 與 `MAXIMUM`。

## 什麼是「encrypt docx with password」？
對 DOCX 檔案加密即是將檔案內容以加密形式儲存，只有在提供正確密碼後才能開啟。這可防止未授權的存取，同時在輸入密碼後仍能使用一般的 Word 工具開啟檔案。

## 為何使用 Aspose.Words 的儲存選項進行加密？
Aspose.Words 提供豐富的 **aspose words save options**，讓您不僅能控制加密，還能設定合規等級、壓縮方式與舊版字元處理，全部透過 Java 程式碼完成。省去手動後處理或第三方工具的需求。

## 前置條件
- Java Development Kit (JDK 8 或以上)  
- 已將 Aspose.Words for Java 套件加入專案（Maven/Gradle 或 JAR）  
- 生產環境的有效 Aspose.Words 授權（評估版可選）

## 使用密碼加密儲存文件

您可以在以 OOXML 格式儲存文件時，同時為文件設定密碼加密。操作方式如下：

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

## 設定 OOXML 合規性

儲存文件時可指定 OOXML 合規等級。例如，可將其設定為 ISO 29500:2008（Strict）。操作方式如下：

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

## 更新「最後儲存時間」屬性

儲存時可選擇是否更新文件的「最後儲存時間」屬性。操作方式如下：

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

## 保留舊版控制字元

若文件中包含舊版控制字元，您可以在儲存時選擇保留它們。操作方式如下：

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

## 設定壓縮等級

儲存文件時可調整壓縮等級。例如，可將其設定為 **SUPER_FAST** 以取得最小壓縮時間。操作方式如下：

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

以上即為使用 Aspose.Words for Java 以 OOXML 格式儲存文件時，可運用的主要選項與設定。歡迎探索更多功能，依需求自訂文件儲存流程。

## 完整範例程式碼：以 OOXML 格式儲存文件（Aspose.Words for Java）

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

在本完整指南中，我們探討了如何 **encrypt docx with password**，以及如何使用 Aspose.Words for Java 微調各種 OOXML 儲存選項。無論是保護機密內容、符合嚴格 ISO 標準、保留舊版字元，或是控制壓縮，皆可透過同一個 `OoxmlSaveOptions` API 取得細緻的控制。

## 常見問題

**Q: 如何移除已設定密碼的文件的保護？**  
A: 使用正確的密碼開啟文件後，再次儲存時不呼叫 `setPassword` 即可。新檔案將不再受保護。

**Q: 我可以在以 OOXML 格式儲存文件時設定自訂屬性嗎？**  
A: 可以。在呼叫 `save` 之前，於 `Document` 物件上使用 `BuiltInDocumentProperties` 或 `CustomDocumentProperties` 進行設定。

**Q: 以 OOXML 格式儲存文件的預設壓縮等級是什麼？**  
A: 預設為 `NORMAL`。若需更快速度可改為 `SUPER_FAST`，若需更小檔案則可改為 `MAXIMUM`。

**Q: aspose words save options 能否相容較舊的 Word 版本？**  
A: 能。透過調整 `MsWordVersion` 與合規設定，即可針對 Word 2007‑2019 進行相容性調整。

**Q: 是否可以在一次儲存操作中同時使用多項儲存選項？**  
A: 完全可以。建立一個 `OoxmlSaveOptions` 實例，設定所有需要的屬性（密碼、合規、壓縮等），再將其傳入 `doc.save()`。

---

**最後更新：** 2025-12-29  
**測試環境：** Aspose.Words for Java 24.12  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}