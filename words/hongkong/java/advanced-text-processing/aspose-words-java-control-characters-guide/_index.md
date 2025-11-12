---
date: '2025-11-12'
description: 學習如何在 Java 中使用 Aspose.Words 插入控制字元、管理回車符號，以及加入分頁或分欄斷行，以實現精確的文件格式設定。
keywords:
- Aspose.Words control characters
- Java document formatting with Aspose.Words
- inserting control characters in Java
- insert control characters java
- manage carriage returns
- add page break aspose
- insert non‑breaking space
- create multi‑column layout
language: zh-hant
title: 在 Java 中使用 Aspose.Words 插入控制字元
url: /java/advanced-text-processing/aspose-words-java-control-characters-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Java 中使用 Aspose.Words 插入控制字元
## 介紹
在產生發票、報表或電子報時，您是否需要對換行、製表符或分頁有像素級的精準控制？  
控制字元是讓您以程式方式塑造文件版面的隱形組件。  
本教學將教您如何 **插入**、**驗證** 與 **管理** 換行字元、非換行空格與欄位分隔等控制字元，並使用 Aspose.Words for Java API。

**您將達成的目標：**
1. 插入並驗證換行、換行符與分頁符。  
2. 新增空格、製表符、非換行空格與欄位分隔，以建立多欄版面。  
3. 套用大型文件自動化的效能最佳實踐技巧。

## 前置條件
在開始之前，請確保您已備妥以下項目：

| Requirement | Details |
|-------------|----------|
| **Aspose.Words for Java** | 版本 25.3 或更新（API 在之後的版本中保持穩定）。 |
| **JDK** | Java 8 以上（建議使用 Java 11 或 17）。 |
| **IDE** | IntelliJ IDEA、Eclipse，或任何支援 Java 的編輯器。 |
| **Build tool** | Maven **或** Gradle，用於相依性管理。 |
| **License** | 臨時或已購買的 Aspose.Words 授權檔案。 |

### 快速環境檢查清單
1. 已安裝 Maven **或** Gradle。  
2. 授權檔案可存取（例如 `src/main/resources/aspose.words.lic`）。  
3. 專案編譯無錯誤。

## 設定 Aspose.Words
我們將先將函式庫加入專案，然後載入授權。請依照您的工作流程選擇相應的建置系統。

### Maven 相依性
在 `pom.xml` 的 `<dependencies>` 區塊內加入以下程式碼：

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle 相依性
在 `build.gradle` 的 `dependencies` 區塊內插入此行：

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### 授權初始化（Java 程式碼）
```java
License license = new License();
license.setLicense("path/to/aspose.words.lic");
```

> **注意：** 請將 `"path/to/aspose.words.lic"` 替換為實際的授權檔案路徑。

## 功能 1：處理換行與分頁符
換行 (`ControlChar.CR`) 與分頁符 (`ControlChar.PAGE_BREAK`) 在需要讓輸出文字呈現文件視覺版面時相當重要。

### 步驟說明實作
1. **建立新的 Document 與 DocumentBuilder。**  
2. **寫入兩個段落。**  
3. **驗證產生的文字是否包含預期的控制字元。**  
4. **修剪文字並重新檢查結果。**

#### 1. 建立 Document
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

#### 2. 插入段落
```java
builder.writeln("Hello world!");
builder.writeln("Hello again!");
```

#### 3. 驗證控制字元
```java
String expectedTextWithCR = MessageFormat.format("Hello world!{0}", ControlChar.CR) +
        MessageFormat.format("Hello again!{0}", ControlChar.CR) +
        ControlChar.PAGE_BREAK;
assert doc.getText().equals(expectedTextWithCR) :
        "Text does not match expected value with control characters.";
```

#### 4. 修剪並檢查文字
```java
String expectedTrimmedText = MessageFormat.format("Hello world!{0}", ControlChar.CR) + "Hello again!";
assert doc.getText().trim().equals(expectedTrimmedText) :
        "Trimmed text does not match expected value.";
```

**結果：** `doc.getText()` 文字串現在包含明確的 CR 與分頁符號，確保下游系統（例如純文字匯出器）能保留版面配置。

## 功能 2：插入各種控制字元
除了換行外，Aspose.Words 亦提供空格、製表符、換行符、段落分隔與欄位分隔等常數。本節示範如何將每種字元嵌入文件。

### 步驟說明實作
1. **初始化全新的 DocumentBuilder。**  
2. **示範空格、非換行空格與製表符的寫入。**  
3. **加入換行、段落分隔與節分隔，並驗證節點數量。**  
4. **建立雙欄版面並插入欄位分隔。**

#### 1. 初始化 DocumentBuilder
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

#### 2. 插入空格相關字元
- **空格 (`ControlChar.SPACE_CHAR`)**
```java
builder.write("Before space." + ControlChar.SPACE_CHAR + "After space.");
```
- **非換行空格 (`ControlChar.NON_BREAKING_SPACE`)**
```java
builder.write("Before NBSP." + ControlChar.NON_BREAKING_SPACE + "After NBSP.");
```
- **製表符 (`ControlChar.TAB`)**
```java
builder.write("Before tab." + ControlChar.TAB + "After tab.");
```

#### 3. 換行、段落與節分隔
```java
// Verify initial paragraph count is 1
Assert.assertEquals(1, doc.getFirstSection().getBody()
        .getChildNodes(NodeType.PARAGRAPH, true).getCount());

// Insert a line feed (creates a new paragraph)
builder.write("Before line feed." + ControlChar.LINE_FEED + "After line feed.");
Assert.assertEquals(2, doc.getFirstSection().getBody()
        .getChildNodes(NodeType.PARAGRAPH, true).getCount());

// Insert a paragraph break
builder.write("Before paragraph break." + ControlChar.PARAGRAPH_BREAK + "After paragraph break.");
Assert.assertEquals(3, doc.getFirstSection().getBody()
        .getChildNodes(NodeType.PARAGRAPH, true).getCount());

// Insert a section break (still one Section object, but a break marker)
builder.write("Before section break." + ControlChar.SECTION_BREAK + "After section break.");
assert doc.getSections().getCount() == 1 :
        "Section count mismatch after section break.";
```

#### 4. 多欄版面的欄位分隔
```java
// Add a second section to host two columns
doc.appendChild(new Section(doc));
builder.moveToSection(1);
builder.getCurrentSection().getPageSetup().getTextColumns().setCount(2);

// Insert a column break between the two columns
builder.write("Text at end of column 1." + ControlChar.COLUMN_BREAK + "Text at beginning of column 2.");
```

**結果：** 文件現在包含一個雙欄頁面，文字會在 `COLUMN_BREAK` 後自動從第一欄流向第二欄。

## 實務應用
| Scenario | How Control Characters Help |
|----------|-----------------------------|
| **Invoice Generation** | 使用 `PAGE_BREAK` 為每批發票開啟新頁。 |
| **Financial Report** | 以 `TAB` 對齊數字，並使用 `NON_BREAKING_SPACE` 讓標題保持在同一行。 |
| **Newsletter Layout** | 在多欄節中使用 `COLUMN_BREAK` 產生並排文章。 |
| **CMS Content Export** | 透過 `LINE_FEED` 轉換富文字為純文字時保留換行結構。 |
| **Automated Templates** | 依使用者輸入動態插入 `PARAGRAPH_BREAK` 或 `SECTION_BREAK`。 |

## 效能考量
* **批次插入：** 將多個 `write` 呼叫合併為一次操作，以減少內部重排。  
* **避免頻繁節點遍歷：** 在需要多次計算段落數時，將 `NodeCollection` 結果快取起來。  
* **大型文件分析：** 使用 Java 效能分析工具（如 VisualVM）找出文字操作迴圈的瓶頸。

## 結論
您現在已掌握在 Java 文件中 **插入**、**驗證** 與 **最佳化** 控制字元的具體步驟，並可使用 Aspose.Words 產出專業等級的發票、報表與多欄出版物。

## 後續步驟
1. 嘗試其他 `ControlChar` 常數，如 `EM_SPACE` 或 `EN_SPACE`。  
2. 結合控制字元與郵件合併欄位，實現動態文件產生。  
3. 探索 Aspose.Words 的 **文件保護**、**浮水印**、**圖片插入** 等功能，進一步豐富輸出內容。

**立即試用：** 將上述程式碼片段加入您的下一個 Java 專案，體驗精準控制字元如何簡化文件工作流程！

## 常見問題
1. **什麼是控制字元？**  
   不會顯示為可見文字的符號（例如製表符、換行符），會影響文件版面配置。

2. **如何開始使用 Aspose.Words for Java？**  
   加入 Maven 或 Gradle 相依性、載入授權，然後依照本指南的程式碼範例操作即可。

3. **我可以在電子報中使用欄位分隔嗎？**  
   可以——`ControlChar.COLUMN_BREAK` 可與 `TextColumns` 屬性結合，將內容分割至多個欄位。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}