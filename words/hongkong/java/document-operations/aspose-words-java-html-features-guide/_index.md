---
"date": "2025-03-28"
"description": "了解如何利用 Aspose.Words for Java 掌握文件處理，包括 VML 支援、加密、HTML 導入選項等。"
"title": "Aspose.Words for Java&#58;全面的 HTML 功能和文件處理指南"
"url": "/zh-hant/java/document-operations/aspose-words-java-html-features-guide/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# Aspose.Words for Java 的全面 HTML 功能：開發人員指南

## 介紹

瀏覽複雜的文件處理世界可能會令人望而生畏，尤其是在處理各種 HTML 功能時。無論您處理的是向量標記語言 (VML) 支援、加密文件還是特定的 HTML 導入行為， **Aspose.Words for Java** 提供了一個強大的解決方案。在本指南中，我們將探討如何使用 Aspose.Words 無縫實現這些功能，增強您的文件處理能力。

**您將學到什麼：**
- 如何載入具有 VML 支援的 HTML 文件。
- 處理固定頁面 HTML 和警告的技術。
- 加密和載入受密碼保護的 HTML 文件的方法。
- 在 HTML 載入選項中使用基本 URI。
- 將 HTML 輸入元素匯入為結構化文件標籤或表單欄位。
- 忽略 `<noscript>` HTML 載入期間的元素。
- 配置區塊導入模式來控制HTML結構保存。
- 支援 `@font-face` 自訂字體的規則。

有了這些見解，您將能夠很好地處理各種 HTML 處理任務。讓我們先深入了解先決條件和設定！

## 先決條件

在我們開始使用 Aspose.Words for Java 實作各種 HTML 功能之前，請確保您的環境已正確設定：

- **所需庫：** 您需要 Aspose.Words 函式庫版本 25.3 或更高版本。
- **開發環境：** 本指南假設您使用 Maven 或 Gradle 進行依賴管理。
- **知識庫：** 對 Java 有基本的了解並熟悉 HTML 文件將會很有幫助。

## 設定 Aspose.Words

要開始使用 Aspose.Words，首先需要將其包含在您的專案中。以下是使用 Maven 和 Gradle 設定庫的步驟：

### Maven

將以下相依性新增至您的 `pom.xml` 文件：

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle

將其包含在您的 `build.gradle` 文件：

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### 許可證獲取

Aspose.Words 需要許可證才能使用全部功能。您可以獲得免費試用、申請臨時許可證或購買永久許可證。訪問 [購買頁面](https://purchase.aspose.com/buy) 了解更多詳情。

若要在 Java 專案中初始化 Aspose.Words，請確保已正確設定許可：

```java
import com.aspose.words.License;

public class InitializeAspose {
    public static void main(String[] args) throws Exception {
        License license = new License();
        license.setLicense("path/to/your/license/file.lic");
        
        System.out.println("Aspose.Words is ready to use!");
    }
}
```

## 實施指南

我們將根據想要實現的功能將實作分為幾個部分。

### 在 HTML 文件中支援 VML

**概述：**
載入具有或不具有 VML 支援的 HTML 文件可以實現向量圖形的多種渲染。在處理包含圖表和形狀等圖形元素的文件時，此功能至關重要。

#### 逐步實施：

1. **設定載入選項**
   
   ```java
   import com.aspose.words.Document;
   import com.aspose.words.HtmlLoadOptions;

   HtmlLoadOptions loadOptions = new HtmlLoadOptions();
   loadOptions.setSupportVml(true); // 啟用 VML 支持
   ```

2. **載入文檔**
   
   ```java
   Document doc = new Document("path/to/VML conditional.htm", loadOptions);
   ```

3. **驗證影像類型**
   
   確保圖像類型符合您的期望：
   
   ```java
   import com.aspose.words.NodeType;
   import com.aspose.words.Shape;

   Shape imageShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
   String expectedImageType = "JPG"; // 根據實際邏輯調整

   if (!imageShape.getImageData().getImageType().toString().equals(expectedImageType)) {
       throw new AssertionError("Unexpected image type loaded.");
   }
   ```

### 載入 HTML 修復並處理警告

**概述：**
載入固定頁面 HTML 文件可能會產生警告，需要進行管理才能準確處理。

#### 逐步實施：

1. **定義警告回調**
   
   ```java
   import com.aspose.words.IWarningCallback;
   import com.aspose.words.WarningInfo;
   import java.util.ArrayList;

   private static class ListDocumentWarnings implements IWarningCallback {
       private final ArrayList<WarningInfo> mWarnings = new ArrayList<>();

       public void warning(WarningInfo info) { 
           mWarnings.add(info); 
       }

       public ArrayList<WarningInfo> warnings() { return mWarnings; }
   }
   ```

2. **配置載入選項**
   
   ```java
   HtmlLoadOptions loadOptions = new HtmlLoadOptions();
   ListDocumentWarnings warningCallback = new ListDocumentWarnings();
   loadOptions.setWarningCallback(warningCallback);
   ```

3. **載入文件並檢查警告**
   
   ```java
   Document doc = new Document("path/to/HtmlFixed.html", loadOptions);

   if (warningCallback.warnings().size() != 1) {
       throw new AssertionError("Unexpected number of warnings.");
   }
   ```

### 加密 HTML 文件

**概述：**
使用密碼加密 HTML 文件可確保安全訪問，這對於敏感資訊至關重要。

#### 逐步實施：

1. **準備數位簽章選項**
   
   ```java
   import com.aspose.words.CertificateHolder;
   import com.aspose.words.DigitalSignatureUtil;
   import com.aspose.words.SignOptions;

   CertificateHolder certificateHolder = CertificateHolder.create("path/to/morzal.pfx", "aw");
   SignOptions signOptions = new SignOptions();
   signOptions.setComments("Comment");
   signOptions.setSignTime(new Date());
   signOptions.setDecryptionPassword("docPassword");
   ```

2. **簽署並加密文檔**
   
   ```java
   String inputFileName = "path/to/Encrypted.docx";
   String outputFileName = "path/to/output/directory/HtmlLoadOptions.EncryptedHtml.html";

   DigitalSignatureUtil.sign(inputFileName, outputFileName, certificateHolder, signOptions);
   ```

3. **載入加密文檔**
   
   ```java
   import com.aspose.words.Document;

   HtmlLoadOptions loadOptions = new HtmlLoadOptions("docPassword");
   Document doc = new Document(outputFileName, loadOptions);

   if (!doc.getText().trim().equals("Test encrypted document.")) {
       throw new AssertionError("Unexpected document text.");
   }
   ```

### HTML 載入選項的基本 URI

**概述：**
指定基本 URI 有助於解析相對 URI，尤其是在處理映像或其他連結資源時。

#### 逐步實施：

1. **使用基本 URI 配置載入選項**
   
   ```java
   HtmlLoadOptions loadOptions = new HtmlLoadOptions(LoadFormat.HTML, "", "path/to/imageDir");
   ```

2. **載入文件並驗證圖像**
   
   ```java
   import com.aspose.words.Document;
   import com.aspose.words.NodeType;

   Document doc = new Document("path/to/Missing image.html", loadOptions);
   Shape imageShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);

   if (!imageShape.isImage()) {
       throw new AssertionError("Expected an image shape.");
   }
   ```

### 導入 HTML 選擇為結構化文件標籤

**概述：**
輸入 `<select>` 元素作為結構化文件標籤允許在 Word 文件中更好地控制和格式化。

#### 逐步實施：

1. **設定首選控制類型**
   
   ```java
   import com.aspose.words.HtmlLoadOptions;
   import com.aspose.words.ControlType;

   HtmlLoadOptions loadOptions = new HtmlLoadOptions();
   loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag);
   ```

2. **載入文檔並驗證結構**
   
   ```java
   import com.aspose.words.Document;
   import com.aspose.words.NodeType;
   import com.aspose.words.StructuredDocumentTag;

   Document doc = new Document("path/to/Input HTML with select element.html", loadOptions);
   StructuredDocumentTag sdt = (StructuredDocumentTag)doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

   if (!sdt.getTagName().equals("Select")) {
       throw new AssertionError("Expected a Structured Document Tag with tag name 'Select'.");
   }
   ```

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}