---
date: 2026-01-09
description: 學習如何在使用 Aspose.Words for Java 時，以密碼加密 docx 並在保存為 OOXML 格式的文件時更改壓縮等級。
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: 使用密碼加密 docx – 以 Aspose.Words Java 保存 OOXML
url: /zh-hant/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用密碼加密 docx – 使用 Aspose.Words Java 以 OOXML 保存

## 在 Aspose.Words for Java 中將文件保存為 OOXML 格式的介紹

在本指南中，您將學習如何 **encrypt docx with password** 並使用 Aspose.Words for Java 以 OOXML 格式保存文件。OOXML（Office Open XML）是 Microsoft Word 以及許多其他辦公應用程式使用的現代檔案格式。我們將逐一說明最常用的選項──密碼保護、相容性等級、屬性更新、舊版字元處理，以及 **how to change compression level**──讓您能依需求自訂輸出。

## 快速解答
- **How can I protect a Word file?** 使用 `OoxmlSaveOptions.setPassword("yourPassword")` 於保存前設定。  
- **What OOXML compliance level should I choose?** ISO 29500 2008 Strict，提供與現代 Office 版本的最高相容性。  
- **Can I keep legacy control characters?** 可以，啟用 `setKeepLegacyControlChars(true)`。  
- **How do I change the compression level?** 設定 `setCompressionLevel(CompressionLevel.SUPER_FAST)` 或 `MAXIMUM` 以符合需求。  
- **Do these options affect file size?** 壓縮等級與舊版字元處理會顯著影響最終 .docx 檔案大小。

## 什麼是 “encrypt docx with password”？
對 DOCX 檔案進行加密即是以 AES‑256 加密方式保存文件，必須輸入密碼才能在 Word 或任何相容的檢視器中開啟。當檔案透過電郵、雲端儲存或內部網路門戶分享時，這對保護機密資訊至關重要。

## 為什麼要使用 OOXML 保存選項？
- **Security:** 密碼保護可防止未經授權的存取。  
- **Compatibility:** 相容性設定確保檔案在不同 Word 版本間皆可正常使用。  
- **Performance:** 調整壓縮可加快保存速度或減少檔案大小。  
- **Preservation:** 保留舊版控制字元可在轉換舊文件時維持原始忠實度。

## 前置條件
- 已在專案中加入 Aspose.Words for Java 程式庫（Maven/Gradle 或手動 JAR）。  
- Java 8 或以上。  
- 欲處理的來源文件（`.docx` 或 `.doc`）。

## 使用密碼加密保存文件

您可以在以 OOXML 格式保存時使用密碼加密文件。以下是操作步驟：

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

> **Pro tip:** 請選擇強度高的密碼並妥善保存；密碼無法從加密檔案中復原。

## 設定 OOXML 相容性

保存文件時可指定 OOXML 相容性等級。例如，可將其設定為 ISO 29500:2008（Strict）。操作如下：

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

保存時可選擇更新文件的「Last Saved Time」屬性。操作如下：

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

若文件包含舊版控制字元，您可以在保存時選擇保留它們。操作如下：

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

## 如何在保存 OOXML 時變更壓縮等級

保存文件時可調整壓縮等級。例如，可將其設定為 `SUPER_FAST` 以最小壓縮，或 `MAXIMUM` 以取得最小檔案大小。操作如下：

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

以上是使用 Aspose.Words for Java 以 OOXML 格式保存文件時可使用的主要選項與設定。歡迎探索更多選項，並依需求自訂文件保存流程。

## 完整範例程式碼：在 Aspose.Words for Java 中以 OOXML 格式保存文件

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

在本完整指南中，我們探討了如何 **encrypt docx with password** 並使用 Aspose.Words for Java 以 OOXML 格式保存文件。無論您需要保護檔案、確保嚴格的 OOXML 相容性、更新文件屬性、保留舊版控制字元，或是 **change compression level**，Aspose.Words 都提供多功能工具以滿足您的需求。

## 常見問答

**Q: 如何移除受密碼保護的文件的密碼保護？**  
A: 使用正確的密碼開啟文件，然後在 `OoxmlSaveOptions` 中不設定密碼再保存，即可產生未受保護的副本。

**Q: 在以 OOXML 格式保存文件時，我可以設定自訂屬性嗎？**  
A: 可以。於呼叫 `save()` 前，於 `Document` 物件上使用 `BuiltInDocumentProperties` 與 `CustomDocumentProperties`。

**Q: 以 OOXML 格式保存文件時的預設壓縮等級是什麼？**  
A: 預設為 `CompressionLevel.NORMAL`。您可切換至 `SUPER_FAST` 以提升速度，或 `MAXIMUM` 以取得最小檔案大小。

**Q: 啟用 `keepLegacyControlChars` 會影響與現代 Word 版本的相容性嗎？**  
A: 現代 Word 能開啟含有舊版控制字元的檔案，但某些舊功能可能會呈現不同。僅在需要保留原始內容時才使用此選項。

**Q: 是否可以在一次呼叫中結合多個保存選項（例如密碼 + 壓縮）？**  
A: 當然可以。在傳遞給 `doc.save()` 前，於單一 `OoxmlSaveOptions` 實例上設定所有需要的屬性。

---

**最後更新：** 2026-01-09  
**測試環境：** Aspose.Words for Java 24.12  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}