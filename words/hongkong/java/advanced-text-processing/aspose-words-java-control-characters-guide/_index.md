---
date: '2025-11-12'
description: 學習一步步使用 Aspose.Words for Java 插入分頁符、定位點、非換行空格及多欄版面配置，立即提升文件自動化。
keywords:
- how to insert control characters
- add page break java
- manage carriage return aspose
- insert non breaking space
- create multi column layout
- Aspose.Words control characters
- Java document formatting
- text layout automation
- document generation Java
- Aspose.Words API
language: zh-hant
title: 使用 Aspose.Words for Java 插入控制字元
url: /java/advanced-text-processing/aspose-words-java-control-characters-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for Java 插入控制字元

## 為什麼控制字元在 Java 文件中很重要
在程式化產生發票、報表或電子報時，精確的文字排版是絕對不能妥協的。**分頁符**、**定位鍵**（Tab）以及**不換行空格**等控制字元讓您能在不需要手動編輯的情況下，精確決定內容出現的位置。本教學將示範如何使用 Aspose.Words for Java API 來管理這些字元，讓文件一次產出即具備專業外觀。

**本指南您將完成的目標**
1. 插入並驗證回車、換行與分頁符。  
2. 新增空格、定位鍵與不換行空格以對齊文字。  
3. 使用欄位分隔符建立多欄版面配置。  
4. 為大型文件套用最佳效能實務技巧。

## 前置條件
開始之前，請先確認您已具備以下項目：

| 必備項目 | 說明 |
|-------------|---------|
| **Aspose.Words for Java** | 版本 25.3 以上（API 向下相容）。 |
| **JDK** | 8 版或更新。 |
| **IDE** | IntelliJ IDEA、Eclipse，或您慣用的任何 Java IDE。 |
| **建置工具** | Maven **或** Gradle，用於相依性管理。 |
| **授權** | 暫時或正式購買的 Aspose.Words 授權檔 (`aspose.words.lic`)。 |

### 環境設定清單
1. 安裝 Maven **或** Gradle。  
2. 加入 Aspose.Words 相依性（請見下方說明）。  
3. 將授權檔放置於安全位置，並記下其路徑。

## 將 Aspose.Words 加入專案

### Maven
在 `pom.xml` 中插入以下片段：

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle
在 `build.gradle` 中加入此行：

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### 授權初始化
取得授權後，於應用程式啟動時進行初始化：

```java
License license = new License();
license.setLicense("path/to/aspose.words.lic");
```

> **注意：** 若未使用授權，函式庫會以評估模式執行，並會在文件中插入浮水印。

## 實作指南

本教學將說明兩個核心功能：**回車處理**與**插入各種控制字元**。每個功能皆以編號步驟呈現，且每段程式碼前都有簡短說明。

### 功能 1 – 回車與分頁符處理
`ControlChar.CR`（回車）與 `ControlChar.PAGE_BREAK`（分頁符）等控制字元定義了文件的邏輯流程。以下範例示範如何驗證這些字元是否正確插入。

#### 步驟說明

1. **建立新的 Document 與 DocumentBuilder**  
   `Document` 物件是所有內容的容器；`DocumentBuilder` 提供流暢的 API 以加入文字。

   ```java
   Document doc = new Document();
   DocumentBuilder builder = new DocumentBuilder(doc);
   ```

2. **插入兩個簡單段落**  
   每次呼叫 `writeln` 皆會自動附加段落分隔符。

   ```java
   builder.writeln("Hello world!");
   builder.writeln("Hello again!");
   ```

3. **使用控制字元建立預期字串**  
   我們利用 `MessageFormat` 將 `ControlChar.CR` 與 `ControlChar.PAGE_BREAK` 嵌入預期文字中。

   ```java
   String expectedTextWithCR = MessageFormat.format("Hello world!{0}", ControlChar.CR) +
           MessageFormat.format("Hello again!{0}", ControlChar.CR) +
           ControlChar.PAGE_BREAK;
   assert doc.getText().equals(expectedTextWithCR) :
           "Text does not match expected value with control characters.";
   ```

4. **修剪文件文字並重新驗證**  
   修剪會移除結尾的空白字元，同時保留有意的換行。

   ```java
   String expectedTrimmedText = MessageFormat.format("Hello world!{0}", ControlChar.CR) + "Hello again!";
   assert doc.getText().trim().equals(expectedTrimmedText) :
           "Trimmed text does not match expected value.";
   ```

> **結果：** 斷言確認文件的內部文字表示確實包含您預期的回車與分頁符。

### 功能 2 – 插入各種控制字元
接下來示範如何直接在文件中嵌入空格、定位鍵、換行、段落分隔符與欄位分隔符。

#### 步驟說明

1. **初始化全新的 DocumentBuilder**  
   從空白文件開始，可確保範例相互獨立。

   ```java
   Document doc = new Document();
   DocumentBuilder builder = new DocumentBuilder(doc);
   ```

2. **插入與空格相關的字元**  

   *空格字元 (`ControlChar.SPACE_CHAR`)*  
   ```java
   builder.write("Before space." + ControlChar.SPACE_CHAR + "After space.");
   ```

   *不換行空格 (`ControlChar.NON_BREAKING_SPACE`)*  
   ```java
   builder.write("Before NBSP." + ControlChar.NON_BREAKING_SPACE + "After NBSP.");
   ```

   *定位鍵 (`ControlChar.TAB`)*  
   ```java
   builder.write("Before tab." + ControlChar.TAB + "After tab.");
   ```

3. **加入換行與段落分隔符**  

   *換行字元在同一段落內建立新行。*  
   ```java
   // Verify that we start with a single paragraph
   Assert.assertEquals(1, doc.getFirstSection().getBody()
           .getChildNodes(NodeType.PARAGRAPH, true).getCount());

   builder.write("Before line feed." + ControlChar.LINE_FEED + "After line feed.");

   // After inserting a line feed, a second paragraph should appear
   Assert.assertEquals(2, doc.getFirstSection().getBody()
           .getChildNodes(NodeType.PARAGRAPH, true).getCount());
   ```

   *段落分隔符 (`ControlChar.PARAGRAPH_BREAK`)*  
   ```java
   builder.write("Before paragraph break." + ControlChar.PARAGRAPH_BREAK + "After paragraph break.");
   Assert.assertEquals(3, doc.getFirstSection().getBody()
           .getChildNodes(NodeType.PARAGRAPH, true).getCount());
   ```

   *分節分隔符 (`ControlChar.SECTION_BREAK`)*  
   ```java
   builder.write("Before section break." + ControlChar.SECTION_BREAK + "After section break.");
   assert doc.getSections().getCount() == 1 :
           "Section count mismatch after section break.";
   ```

4. **使用欄位分隔符建立多欄版面**  

   首先新增第二個節並啟用兩欄：

   ```java
   doc.appendChild(new Section(doc));
   builder.moveToSection(1);
   builder.getCurrentSection().getPageSetup().getTextColumns().setCount(2);
   ```

   然後插入欄位分隔符，將內容從第 1 欄移至第 2 欄：

   ```java
   builder.write("Text at end of column 1." + ControlChar.COLUMN_BREAK + "Text at beginning of column 2.");
   ```

> **結果：** 執行程式碼後，文件會正確呈現空格、定位鍵、換行、段落分隔符、分節分隔符以及兩欄版面——全部由 Aspose.Words 控制字元驅動。

## 真實案例
| 情境 | 控制字元的幫助 |
|----------|-----------------------------|
| **發票產生** | 在特定行數後強制分頁，確保合計金額位於新頁。 |
| **財務報表** | 使用定位鍵與不換行空格對齊欄位，保持數字格式一致。 |
| **電子報與手冊** | 透過欄位分隔符實現並排文章，免除手動排版。 |
| **CMS 產出文件** | 依使用者產生的內容動態插入換行與段落分隔符。 |
| **批次文件建立** | 大量插入控制字元以降低處理時間。 |

## 大型文件效能建議
- **批次插入：** 盡可能將多個 `write` 呼叫合併為一次。  
- **避免重複版面計算：** 在執行保存或匯出等重負載操作前，先一次性插入所有控制字元。  
- **使用 Java Flight Recorder 進行效能分析**，找出文字操作的瓶頸。

## 結論
您現在已掌握使用 Aspose.Words for Java 操作控制字元的完整步驟。透過程式化插入空格、定位鍵、換行、分頁與欄位分隔符，您可以一次產出格式完美的發票、報表與多欄出版物，無需手動調整。

**後續建議：**  
- 嘗試將控制字元與欄位代碼結合，實作動態內容。  
- 探索 Aspose.Words 的郵件合併、文件保護與 PDF 轉換等功能，擴充自動化流程。

**行動呼籲：** 將這些程式碼片段套用到您的下一個 Java 專案，體驗文件產出更乾淨、更可靠的效果！

## 常見問題

1. **什麼是控制字元？**  
   不是可見的符號（例如定位鍵、換行、分頁），會影響文字排版但不會顯示為字形。

2. **使用這些功能需要付費授權嗎？**  
   評估授權可供測試使用；正式授權會移除浮水印並解鎖全部 API 功能。

3. **在單欄文件中可以使用 `ControlChar.COLUMN_BREAK` 嗎？**  
   可以，但只有在透過 `PageSetup.getTextColumns().setCount()` 設定多欄後，欄位分隔符才會生效。

4. **有沒有方式列出所有可用的控制字元？**  
   所有常數皆定義於 `com.aspose.words.ControlChar` 類別，請參考官方 API 文件取得完整列舉。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}