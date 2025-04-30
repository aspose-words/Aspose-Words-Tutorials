---
"date": "2025-03-28"
"description": "了解如何使用 Aspose.Words for Java 掌握文件轉換和安全性。轉換為 ODT，確保符合模式，並輕鬆加密文件。"
"title": "Aspose.Words Java&#58; ODT 檔案的文件轉換與安全"
"url": "/zh-hant/java/document-operations/aspose-words-java-document-conversion-security/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# 使用 Aspose.Words Java 掌握文件轉換和安全

## 介紹

在文件管理領域，有效地轉換和保護文件對於開發人員和企業來說至關重要。無論是確保與舊模式版本的兼容性還是透過加密保護敏感訊息，如果沒有合適的工具，這些任務都可能令人望而生畏。本教學重點在於如何使用 **Aspose.Words for Java** 簡化將文件匯出為開放文件文字 (ODT) 格式的流程，同時保持模式合規性並實施強大的安全措施。

在本指南中，您將學習如何：
- 匯出符合 ODT 1.1 規範的文件。
- 在 ODT 文件中使用不同的測量單位。
- 使用 Aspose.Words for Java 透過密碼加密 ODT/OTT 檔案。

讓我們開始吧！

## 先決條件

在開始之前，請確保您已進行以下設定：

### 所需庫
你需要 **Aspose.Words for Java** 版本 25.3 或更高版本。以下是使用 Maven 或 Gradle 將其包含在專案中的方法：

#### Maven：
```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

#### Gradle：
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### 環境設定
確保您的機器上安裝了 Java，並且配置了用於 Java 開發的 IDE 或文字編輯器。

### 知識前提
建議對 Java 程式設計有基本的了解，以便有效遵循本教學。

## 設定 Aspose.Words

要開始使用 Aspose.Words，請先確保它已正確整合到您的專案中。步驟如下：

1. **取得許可證**：您可以從 [Aspose](https://purchase.aspose.com/temporary-license/) 不受限制地測試所有功能。
   
2. **基本初始化**：
   ```java
   import com.aspose.words.Document;

   public class AsposeSetup {
       public static void main(String[] args) throws Exception {
           // 從磁碟載入文檔
           Document doc = new Document("path/to/your/document.docx");
           
           // 將其儲存為 ODT 格式作為範例用法
           doc.save("output/path/OdtSaveOptions.odt", com.aspose.words.SaveFormat.ODT);
       }
   }
   ```

## 實施指南

### 將文件匯出為 ODT Schema 1.1

此功能可讓您確保匯出的文件符合 ODT 1.1 模式，這對於與某些應用程式的相容性至關重要。

#### 概述
程式碼片段示範如何在設定特定的模式要求和測量單位的同時匯出文件。

#### 逐步實施

**3.1 配置匯出選項**
```java
import com.aspose.words.Document;
import com.aspose.words.OdtSaveOptions;

// 載入來源 Word 文件
Document document = new Document("YOUR_DOCUMENT_DIRECTORY/Rendering.docx");

// 初始化 ODT 保存選項並配置架構合規性
OdtSaveOptions saveOptions = new OdtSaveOptions();
saveOptions.setMeasureUnit(OdtSaveMeasureUnit.CENTIMETERS);
saveOptions.isStrictSchema11(true); // 設定為 true 以符合 ODT 1.1

// 使用這些設定儲存文檔
document.save("YOUR_OUTPUT_DIRECTORY/OdtSaveOptions.Odt11Schema.odt", saveOptions);
```

**3.2 驗證導出設定**
儲存後，請確保文件的設定正確：
```java
import com.aspose.words.MeasurementUnits;

Document loadedDoc = new Document("YOUR_OUTPUT_DIRECTORY/OdtSaveOptions.Odt11Schema.odt");
MeasurementUnits mu = loadedDoc.getLayoutOptions().getRevisionOptions().getMeasurementUnit();

assert mu == MeasurementUnits.CENTIMETERS;
```

### 使用不同的測量單位
在某些情況下，您可能需要出於風格或地區原因匯出具有不同測量單位的文件。

#### 概述
此功能支援在 ODT 文件中指定測量單位，從而允許公制和英制系統之間的靈活性。

**3.3 設定測量單位**
```java
OdtSaveOptions saveOptions = new OdtSaveOptions();
// 選擇您想要的單位：厘米或英寸
saveOptions.setMeasureUnit(OdtSaveMeasureUnit.CENTIMETERS);

document.save("YOUR_OUTPUT_DIRECTORY/OdtSaveOptions.Measurements.odt", saveOptions);
```

**3.4 驗證樣式中的測量單位**
為了確保應用正確的測量，請檢查styles.xml內容：
```java
if (saveOptions.getMeasureUnit() == OdtSaveMeasureUnit.CENTIMETERS) {
    assert TestUtil.docPackageFileContainsString(
        "<style:paragraph-properties fo:orphans=\"2\" fo:widows=\"2\" style:tab-stop-distance=\"1.27cm\" />",
        "YOUR_OUTPUT_DIRECTORY/OdtSaveOptions.Measurements.odt", "styles.xml");
}
```

### 加密 ODT/OTT 文檔
處理敏感文件時，安全至關重要。此功能示範如何使用 Aspose.Words 加密文件。

#### 概述
使用密碼加密您的文檔，確保只有授權使用者才能存取其內容。

**3.5 加密文檔**
```java
import com.aspose.words.Document;
import com.aspose.words.OdtSaveOptions;

Document doc = new Document();
doc.getRange().appendText("Hello world!");

OdtSaveOptions saveOptions = new OdtSaveOptions(com.aspose.words.SaveFormat.ODT);
saveOptions.setPassword("@sposeEncrypted_1145");

// 加密保存文檔
doc.save("YOUR_OUTPUT_DIRECTORY/OdtSaveOptions.Encrypt.odt", saveOptions);
```

**3.6 驗證加密**
確保您的文件已加密：
```java
import com.aspose.words.FileFormatUtil;
import com.aspose.words.LoadOptions;

FileFormatInfo docInfo = FileFormatUtil.detectFileFormat("YOUR_OUTPUT_DIRECTORY/OdtSaveOptions.Encrypt.odt");
assert docInfo.isEncrypted();

// 使用正確的密碼載入文檔
Document loadedDoc = new Document(
    "YOUR_OUTPUT_DIRECTORY/OdtSaveOptions.Encrypt.odt",
    new LoadOptions("@sposeEncrypted_1145")
);

assert loadedDoc.getText().trim() == "Hello world!";
```

## 實際應用
以下是這些功能的一些實際用例：
1. **商業合規**：將文件匯出至 ODT 1.1 可確保與各行業的遺留系統相容。
2. **國際化**：使用不同的測量單位可以實現跨測量標準不同的地區之間的無縫文件共享。
3. **資料保護**：加密敏感報告或合約可防止未經授權的訪問，這對法律和金融部門至關重要。

## 性能考慮
為了優化使用 Aspose.Words 時的效能：
- 盡量減少在文件中使用高解析度影像。
- 保持文件結構簡單以減少處理時間。
- 定期更新至最新版本的 Aspose.Words for Java 以獲得效能改進。

## 結論
在本教程中，您學習如何使用 **Aspose.Words for Java**。這些技術確保與各種模式版本的兼容性，並透過加密增強文件安全性。為了進一步探索 Aspose 的功能，請考慮深入研究其廣泛的文件並嘗試其他功能。

準備好在您的專案中實施這些解決方案了嗎？前往 [Aspose.Words 文檔](https://reference.aspose.com/words/java/) 獲得更多見解！

## 常見問題部分
**Q：如何確保與舊版 ODT 相容？**
答：使用 `OdtSaveOptions.isStrictSchema11(true)` 符合 ODT 1.1 規範。

**Q：我可以輕鬆地在公制和英制單位之間切換嗎？**
答：是的，將測量單位設定為 `OdtSaveOptions.setMeasureUnit()` 要么 `CENTIMETERS` 或者 `INCHES`。

**Q：如果我的文件沒有如預期加密怎麼辦？**
答：確保您已使用 `saveOptions.setPassword()`。使用以下方式驗證加密 `FileFormatUtil。detectFileFormat()`.

**Q：如何解決加密文檔的載入問題？**
答：請確保在載入文件時使用正確的密碼。

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}