---
"date": "2025-03-28"
"description": "了解如何使用 Aspose.Words for Java 掌握清單偵測、文字處理等。本指南涵蓋偵測由空格分隔的清單、修剪空格、確定文件方向、停用自動編號偵測和管理超連結。"
"title": "使用 Aspose.Words 在 Java 中進行主清單偵測和文字處理完整指南"
"url": "/zh-hant/java/tables-lists/java-aspose-words-list-detection-text-handling/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# 使用 Aspose.Words 在 Java 中進行主清單偵測和文字處理：完整指南

## 介紹

由於分隔符號不一致和格式問題，處理純文字文件通常會為識別清單等結構化資料帶來挑戰。 Aspose.Words for Java 函式庫提供了強大的功能來解決這些問題，包括偵測帶有空格的編號、修剪空格、確定文件方向、停用自動編號偵測以及管理文字文件中的超連結。本教學將幫助您使用 Aspose.Words 有效地處理文字資料。

**您將學到什麼：**
- 檢測空格分隔清單的技術
- 從文件內容中修剪不需要的空格的方法
- 確定文字檔案讀取方向的方法
- 禁用自動編號偵測的方法
- 偵測和管理純文字文件中的超連結的策略

讓我們回顧一下實現這些功能之前所需的先決條件。

## 先決條件

在開始之前，請確保您具備以下條件：

### 所需庫：
- **Aspose.Words for Java**：版本 25.3 或更高版本。

### 環境設定：
- 確保您的開發環境支援 Maven 或 Gradle，因為它們需要管理相依性。

### 知識前提：
- 對 Java 程式設計有基本的了解
- 熟悉 Maven 或 Gradle 建置系統

## 設定 Aspose.Words

要開始在專案中使用 Aspose.Words for Java，您需要包含必要的依賴項。方法如下：

**Maven：**
```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

**Gradle：**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### 許可證獲取

為了充分利用 Aspose.Words，請考慮取得授權：
- **免費試用**：可用於測試功能。
- **臨時執照**：僅用於評估目的，不受限制。
- **購買**：持續使用的完整許可證。

獲得許可證後，請在應用程式中初始化它以解鎖庫的所有功能。

## 實施指南

讓我們分解每個功能並了解如何使用 Aspose.Words for Java 實作它們。

### 檢測帶有空格的數字

**概述：** 此功能可讓您識別使用空格作為分隔符號的純文字文件中的清單。

#### 步驟 1：載入文檔
```java
import com.aspose.words.*;

final String TEXT_DOC = "Full stop delimiters:\n" +
    // …
    "3 Fourth list item 3";

TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setDetectNumberingWithWhitespaces(true);
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
```

#### 步驟 2：驗證清單檢測
```java
List<Paragraph> paragraphList = Arrays.stream(doc.getFirstSection().getBody().getParagraphs().toArray())
        .filter(Paragraph.class::isInstance)
        .map(Paragraph.class::cast)
        .collect(Collectors.toList());

boolean detectNumberingWithWhitespaces = true;
if (detectNumberingWithWhitespaces) {
    assert doc.getLists().getCount() == 4 : "Expected four lists.";
    boolean foundFourthList = paragraphList.stream()
        .anyMatch(p -> p.getText().contains("Fourth list") && p.isListItem());
    assert foundFourthList : "Expected to find a fourth list item detected as numbered.";
}
```

*參數和方法：*
- `setDetectNumberingWithWhitespaces(true)`：配置解析器以識別帶有空格分隔符號的清單。
- `doc.getLists().getCount()`：檢索文件中偵測到的清單的數量。

### 修剪前導和尾隨空格

**概述：** 此功能可修剪純文字文件中行首或行尾不必要的空格，確保文字格式清晰。

#### 步驟 1：配置載入選項
```java
import java.nio.charset.StandardCharsets;
import java.io.ByteArrayInputStream;

String textDoc = "      Line 1 \n" +
    // …
    " Line 3       ";

TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);

Document doc = new Document(new ByteArrayInputStream(textDoc.getBytes(StandardCharsets.US_ASCII)), loadOptions);
```

#### 步驟 2：驗證修剪
```java
ParagraphCollection paragraphs = doc.getFirstSection().getBody().getParagraphs();
for (int i = 0; i < paragraphs.getCount(); i++) {
    Paragraph paragraph = paragraphs.get(i);
    String text = paragraph.getText();
    assert !text.startsWith(" ") : "Expected no leading spaces.";
    assert !text.endsWith(" ") : "Expected no trailing spaces.";
}
```

*關鍵配置：*
- `setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM)`：修剪行首的空格。
- `setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM)`：刪除行尾的空格。

### 偵測文檔方向

**概述：** 確定文件是否應從右到左 (RTL) 閱讀，例如希伯來語或阿拉伯語文本。

#### 步驟 1：設定自動偵測
```java
TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setDocumentDirection(DocumentDirection.AUTO);
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Hebrew text.txt", loadOptions);

boolean isBidi = doc.getFirstSection().getBody().getFirstParagraph().getParagraphFormat().isBidi();
assert isBidi : "Expected Hebrew text to be right-to-left.";
```

### 停用自動編號偵測

**概述：** 防止庫自動偵測和格式化清單項目。

#### 步驟 1：配置載入選項
```java
TxtLoadOptions options = new TxtLoadOptions();
options.setAutoNumberingDetection(false);
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Number detection.txt", options);

int listItemsCount = 0;
for (Paragraph paragraph : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true)) {
    if (paragraph.isListItem())
        listItemsCount++;
}
assert listItemsCount == 0 : "Expected no detected list items.";
```

### 檢測文字中的超連結

**概述：** 識別和管理純文字文件中的超連結。

#### 步驟 1：設定偵測選項
```java
import java.nio.charset.StandardCharsets;
import java.io.ByteArrayInputStream;

final String INPUT_TEXT = "Some links in TXT:\n" +
    // …
    "https://docs.aspose.com/words/net/”；

try (ByteArrayInputStream stream = new ByteArrayInputStream(INPUT_TEXT.getBytes(StandardCharsets.US_ASCII))) {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    loadOptions.setDetectHyperlinks(true);
    Document doc = new Document(stream, loadOptions);

    String[] expectedLinks = {"https://www.aspose.com/", "https://docs.aspose.com/words/net/"};
    for (int i = 0; i < doc.getRange().getFields().getCount(); i++) {
        String result = doc.getRange().getFields().get(i).getResult().trim();
        assert result.equals(expectedLinks[i]) : "Expected hyperlink does not match.";
    }
}
```

## 實際應用

1. **內容管理系統（CMS）：** 自動將使用者產生的內容格式化為結構化清單。
2. **資料擷取工具：** 使用列表檢測來組織非結構化資料以進行分析。
3. **文字處理管道：** 透過修剪空格和偵測文字方向來增強文件預處理。

## 性能考慮

為了優化性能：
- 以最少的操作載入文檔，專注於必要的功能。
- 在可行的情況下，透過分塊處理大型文件來管理記憶體使用量。

## 結論

透過利用 Aspose.Words for Java，您可以有效地管理純文字文件中的文字資料。從檢測空格分隔的清單到處理文字方向和超鏈接，這些強大的工具可以實現強大的文件操作。如需進一步了解，請參閱 [Aspose.Words 文檔](https://reference.aspose.com/words/java/) 或嘗試免費試用。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}