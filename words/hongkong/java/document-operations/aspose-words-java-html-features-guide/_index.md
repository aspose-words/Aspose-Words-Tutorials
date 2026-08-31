---
date: '2026-02-06'
description: 學習如何使用 Aspose.Words for Java 載入 HTML VML、加密 HTML Java 檔案、設定 HTML 基礎 URI，以及配置
  HTML 控制項選項。
keywords:
- Aspose.Words for Java
- HTML document processing
- document encryption
title: 使用 Aspose.Words for Java 載入 HTML VML – 完整指南
url: /zh-hant/java/document-operations/aspose-words-java-html-features-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for Java 的完整 HTML 功能：開發人員指南

## 簡介

在文件處理的複雜領域中航行可能令人望而卻步，尤其是處理各種 HTML 功能時。無論您是處理向量標記語言 (VML) 支援、加密文件，或是特定的 HTML 匯入行為，**Aspose.Words for Java** 都提供了強大的解決方案。  
在本指南中，您將學習如何**how to load html vml**（載入 HTML VML）以高效且安全的方式，同時涵蓋相關任務，如**encrypt html java**、**set html base uri**以及**configure html control**選項。

**您將學到：**
- 如何載入支援 VML 的 HTML 文件。
- 處理固定頁面 HTML 及警告的技巧。
- 加密及載入受密碼保護的 HTML 文件的方法。
- 在 HTML 載入選項中使用基礎 URI。
- 將 HTML 輸入元素匯入為結構化文件標記或表單欄位。
- 在載入 HTML 時忽略 `<noscript>` 元素。
- 設定區塊匯入模式以控制 HTML 結構的保留。
- 支援自訂字型的 `@font-face` 規則。

## 快速解答

- **在載入 HTML 時啟用 VML 的主要方法是什麼？** 設定 `loadOptions.setSupportVml(true)`。  
- **我可以載入受密碼保護的 HTML 檔案嗎？** 可以，將密碼傳遞給 `HtmlLoadOptions`。  
- **如何解析相對圖像路徑？** 使用 `loadOptions.setBaseUri("your/base/uri")`。  
- **是否可以將 `<select>` 匯入為表單欄位？** 設定 `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)`。  
- **哪個類別在載入期間捕獲警告？** 實作 `IWarningCallback` 並將其指派給 `loadOptions.setWarningCallback(...)`。

## 先決條件

在開始使用 Aspose.Words for Java 實作各種 HTML 功能之前，請確保您的環境已正確設定：

- **必要的函式庫：** 您需要 Aspose.Words 函式庫 25.3 版或更新版本。  
- **開發環境：** 本指南假設您使用 Maven 或 Gradle 進行相依管理。  
- **知識基礎：** 具備 Java 基礎知識並熟悉 HTML 文件將會有幫助。

## 設定 Aspose.Words

要開始使用 Aspose.Words，您首先需要將其加入專案中。以下是使用 Maven 與 Gradle 設定函式庫的步驟：

### Maven

在您的 `pom.xml` 檔案中加入以下相依性：

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle

在您的 `build.gradle` 檔案中加入以下內容：

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### 授權取得

Aspose.Words 需要授權才能完整使用全部功能。您可以取得免費試用、申請臨時授權，或購買永久授權。請前往 [購買頁面](https://purchase.aspose.com/buy) 了解更多資訊。

在 Java 專案中初始化 Aspose.Words 時，請確保已正確設定授權：

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

## 實作指南

我們將根據欲實作的功能，將實作內容分成多個章節說明。

### 如何使用 Aspose.Words 載入 html vml

**概述：**  
載入支援 VML 的 HTML 文件可靈活呈現圖表與形狀等向量圖形。這是主要關鍵字 **load html vml** 的核心步驟。

#### 逐步說明

1. **設定載入選項**

```java
import com.aspose.words.Document;
import com.aspose.words.HtmlLoadOptions;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setSupportVml(true); // Enable VML support
```

2. **載入文件**

```java
Document doc = new Document("path/to/VML conditional.htm", loadOptions);
```

3. **驗證圖像類型**

```java
import com.aspose.words.NodeType;
import com.aspose.words.Shape;

Shape imageShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
String expectedImageType = "JPG"; // Adjust based on actual logic

if (!imageShape.getImageData().getImageType().toString().equals(expectedImageType)) {
    throw new AssertionError("Unexpected image type loaded.");
}
```

### 載入固定頁面 HTML 並處理警告

**概述：**  
載入固定頁面 HTML 文件可能會產生需要處理的警告，以確保正確的處理。

#### 逐步說明

1. **定義警告回呼**

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

2. **設定載入選項**

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
使用密碼加密 HTML 文件可確保安全存取，對於敏感資訊尤為重要——此情境對應 **encrypt html java**。

#### 逐步說明

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

2. **簽署並加密文件**

```java
String inputFileName = "path/to/Encrypted.docx";
String outputFileName = "path/to/output/directory/HtmlLoadOptions.EncryptedHtml.html";

DigitalSignatureUtil.sign(inputFileName, outputFileName, certificateHolder, signOptions);
```

3. **載入加密文件**

```java
import com.aspose.words.Document;

HtmlLoadOptions loadOptions = new HtmlLoadOptions("docPassword");
Document doc = new Document(outputFileName, loadOptions);

if (!doc.getText().trim().equals("Test encrypted document.")) {
    throw new AssertionError("Unexpected document text.");
}
```

### HTML 載入選項的基礎 URI

**概述：**  
指定 **set html base uri** 可協助解析相對 URI，特別是在處理圖像或其他連結資源時。

#### 逐步說明

1. **使用基礎 URI 設定載入選項**

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

### 將 HTML Select 匯入為結構化文件標記

**概述：**  
若要 **configure html control** 行為，您可以將 `<select>` 元素匯入為結構化文件標記，從而更細緻地控制 Word 文件內的表單欄位。

#### 逐步說明

1. **設定首選控制類型**

```java
import com.aspose.words.HtmlLoadOptions;
import com.aspose.words.ControlType;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag);
```

2. **載入文件並驗證結構**

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

## 常見問題與解決方案

| 問題 | 原因 | 解決方法 |
|------|------|----------|
| VML 圖形未顯示 | `supportVml` 旗標保持預設值 (`false`) | 載入前請確保呼叫 `loadOptions.setSupportVml(true)`。 |
| 載入後圖像遺失 | 相對路徑無法解析 | 使用 **set html base uri** (`loadOptions.setBaseUri(...)`) 指向正確的資料夾。 |
| 受密碼保護的 HTML 拋出例外 | 未提供密碼 | 將密碼傳遞給 `new HtmlLoadOptions("yourPassword")`。 |
| 表單控制項顯示為純文字 | `HtmlControlType` 設定錯誤 | 依需求設定 `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` 或 `FormField`。 |
| 意外的警告 | 未處理的 HTML 元素 | 實作 `IWarningCallback` 以捕獲並檢視警告。 |

## 常見問與答

**Q: 我可以載入同時包含 VML 與現代 SVG 圖形的 HTML 檔案嗎？**  
A: 可以。使用 `setSupportVml(true)` 以啟用 VML；SVG 會由 Aspose.Words 自動處理。

**Q: 如何在不使用數位憑證的情況下加密 HTML 文件？**  
A: 使用接受密碼的 `HtmlLoadOptions` 建構子，並在設定密碼後以 `Document.save(..., SaveFormat.HTML)` 儲存文件。

**Q: 若基礎 URI 指向不存在的資料夾會發生什麼情況？**  
A: Aspose.Words 會拋出 `FileNotFoundException` 以表示資源遺失。載入前請先確認路徑是否正確。

**Q: 是否能變更所有 HTML 表單元素的預設控制類型？**  
A: 可以。使用 `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` 全域套用。

**Q: 警告回呼是執行緒安全的嗎？**  
A: 若您計畫同時載入多個文件，回呼實作應具備執行緒安全性。可使用同步集合或執行緒本地儲存。

---

**最後更新：** 2026-02-06  
**測試環境：** Aspose.Words for Java 25.3  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}