---
category: general
date: 2026-10-04
description: 使用 Java 建立包含純文字內容控制項與佔位符的 Word 文件。了解如何將佔位符加入標籤以及如何插入 SDT。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- plain text content control
- docx with placeholder
- add placeholder to tag
- how to insert sdt
language: zh-hant
lastmod: 2026-10-04
og_description: 建立含有純文字內容控制項與佔位符的 Word 文件。本教學示範如何將佔位符加入標籤，以及如何使用 Aspose.Words for
  Java 插入 sdt。
og_image_alt: Screenshot of a generated DOCX showing a plain text content control
  with placeholder
og_title: 建立含內容控制的 Word 文件 – 步驟指南
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Create word document using Java that includes a plain text content
    control and a placeholder. Learn how to add placeholder to tag and how to insert
    sdt.
  headline: Create word document with a plain text content control
  type: TechArticle
- description: Create word document using Java that includes a plain text content
    control and a placeholder. Learn how to add placeholder to tag and how to insert
    sdt.
  name: Create word document with a plain text content control
  steps:
  - name: Initialise the document and builder
    text: '```java import com.aspose.words.*;'
  - name: Insert a plain‑text Structured Document Tag (SDT)
    text: '```java private static void insertPlainTextControl(DocumentBuilder builder)
      throws Exception { // Step 2 – create a plain text content control (SDT) with
      a unique tag name StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
      StructuredDocumentTagType.PLAIN_TEXT, "MyTag");'
  - name: Add regular content after the SDT
    text: '```java private static void addTrailingContent(DocumentBuilder builder)
      throws Exception { // Step 3 – write a line after the SDT to prove the control
      is correctly positioned builder.writeln("After SDT"); } ```'
  - name: Save the resulting file
    text: '```java private static void saveDocument(Document doc) throws Exception
      { // Step 4 – persist the document as a DOCX with placeholder String outPath
      = "SdtDemo.docx"; doc.save(outPath); System.out.println("Document saved to "
      + outPath); } ```'
  - name: Expected output
    text: 'Running the program creates `SdtDemo.docx`. Opening the file in Word shows:'
  - name: Next steps
    text: '* Explore **how to insert sdt** inside tables for form‑like layouts. *
      Combine this technique with **docx with placeholder** merging to build automated
      report generators. * Experiment with other control types (`RICH_TEXT`, `CHECKBOX`)
      to create richer Word forms.'
  type: HowTo
tags:
- Word
- Java
- Aspose.Words
title: 建立含純文字內容控制項的 Word 文件
url: /zh-hant/java/document-manipulation/create-word-document-with-a-plain-text-content-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立含純文字內容控制項的 Word 文件

如果您需要 **建立 Word 文件** 且其中包含使用者可編輯的區域，純文字內容控制項是最可靠的做法。本教學會完整說明如何插入 Structured Document Tag（SDT）、設定 placeholder，並將結果儲存為 **docx with placeholder**。您將看到一個完整、可執行的 Java 範例，適用於 Aspose.Words for Java 23.8。

本指南涵蓋所有前置條件，說明每個 API 呼叫的意義，並提供處理多語系 placeholder 或巢狀標籤等邊緣案例的技巧。完成後，您即可產生一個在文件內直接提示使用者「Enter text…」的 Word 檔案。

## 前置條件

在開始之前，請確保您已具備：

* 已安裝 Java 17（或更新版本）並在 PATH 中設定。  
* Maven 3.8+ 用於管理相依性。  
* Aspose.Words for Java 授權（評估版可用於測試）。  
* 開發 IDE（IntelliJ IDEA、Eclipse 或 VS Code）。

將 Aspose.Words 加入您的 `pom.xml`：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.8</version>
</dependency>
```

## 建立含純文字內容控制項的 Word 文件

核心工作流程包含四個邏輯步驟。每個步驟皆以具說明性的 method 包裝，方便在較大型的專案中重複使用。

### 步驟 1：初始化文件與 Builder

```java
import com.aspose.words.*;

public class SdtDemo {
    public static void main(String[] args) throws Exception {
        // Step 1 – create an empty Document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        insertPlainTextControl(builder);
        addTrailingContent(builder);
        saveDocument(doc);
    }
}
```

**為何重要**：`Document` 代表記憶體中的 Word 檔案。`DocumentBuilder` 是流暢的 API，可讓您插入段落、表格與 SDT。從空白文件開始可確保 placeholder 出現在最前端，這對範本相當有用。

### 步驟 2：插入純文字 Structured Document Tag（SDT）

```java
private static void insertPlainTextControl(DocumentBuilder builder) throws Exception {
    // Step 2 – create a plain text content control (SDT) with a unique tag name
    StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
            StructuredDocumentTagType.PLAIN_TEXT, "MyTag");

    // Step 2.1 – add a placeholder that appears when the tag is empty
    sdt.setPlaceholderName("Enter text…");   // add placeholder to tag
}
```

**為何重要**：`StructuredDocumentTagType.PLAIN_TEXT` 會建立僅接受純文字的內容控制項，避免意外的格式化。`setPlaceholderName` 呼叫會填入使用者在輸入前看到的灰色提示文字——這即是 **add placeholder to tag** 的操作，使文件呈現表單般的感受。

### 步驟 3：在 SDT 後加入一般內容

```java
private static void addTrailingContent(DocumentBuilder builder) throws Exception {
    // Step 3 – write a line after the SDT to prove the control is correctly positioned
    builder.writeln("After SDT");
}
```

**為何重要**：在控制項之後加入內容可驗證 SDT 不會佔用整個文件流程。此範例亦示範如何將結構化標籤與普通段落混合，這在建立範本時是常見需求。

### 步驟 4：儲存產生的檔案

```java
private static void saveDocument(Document doc) throws Exception {
    // Step 4 – persist the document as a DOCX with placeholder
    String outPath = "SdtDemo.docx";
    doc.save(outPath);
    System.out.println("Document saved to " + outPath);
}
```

**為何重要**：`save` 方法會將記憶體模型寫入實體 **docx with placeholder** 檔案。產生的檔案可於 Microsoft Word、LibreOffice，或任何支援 OpenXML 格式的函式庫中開啟。

## 完整原始碼

將上述片段組合起來，即可得到一個可自行編譯與執行的完整程式：

```java
import com.aspose.words.*;

public class SdtDemo {
    public static void main(String[] args) throws Exception {
        // Initialise document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert plain‑text content control and set placeholder
        StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
                StructuredDocumentTagType.PLAIN_TEXT, "MyTag");
        sdt.setPlaceholderName("Enter text…");   // add placeholder to tag

        // Add normal text after the control
        builder.writeln("After SDT");

        // Save the file
        String outPath = "SdtDemo.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### 預期輸出

執行程式會產生 `SdtDemo.docx`。在 Word 中開啟該檔案會顯示：

* 一個灰色 placeholder “Enter text…” 位於標記為 **MyTag** 的純文字內容控制項內。  
* 控制項下方緊接著顯示 **After SDT** 這一行。

使用者一開始輸入文字後，placeholder 會立即消失，且保留原始格式。

## 常見變形與邊緣案例

| 情境 | 建議變更 |
|----------|--------------------|
| **多語系 placeholder** | 使用 Unicode 字元於 `setPlaceholderName`，例如 `sdt.setPlaceholderName("Введите текст…");`。 |
| **巢狀內容控制項** | 在第二次 `insertStructuredDocumentTag` 前，呼叫 `builder.moveTo(sdt.getParagraph());` 以在第一個 SDT 內插入第二個。 |
| **唯讀控制項** | 呼叫 `sdt.setLockContentControl(true);` 以防止使用者刪除標籤。 |
| **Rich‑text 取代純文字** | 將 `StructuredDocumentTagType.PLAIN_TEXT` 換成 `StructuredDocumentTagType.RICH_TEXT`。 |
| **儲存至串流** | 當需要透過 HTTP 傳送檔案時，使用 `doc.save(OutputStream, SaveFormat.DOCX);`。 |

## 專業提示

* **Reuse tag IDs** – 若從相同範本產生大量文件，請保持標籤名稱（`"MyTag"`）一致，以便後續處理（例如 mail‑merge）能可靠定位。  
* **Performance** – 對於大型範本，請僅建立一次 `DocumentBuilder` 並重複使用；在迴圈中插入多個 SDT 比每次重新建立 Builder 更快。  
* **Testing** – 產生 DOCX 後，可透過程式碼使用 `doc.getRange().getStructuredDocumentTags().getCount()` 來驗證 placeholder 是否存在。  

## 結論

現在您已了解如何 **create word document**，其中包含帶有自訂 placeholder 的 **plain text content control**，從而產生可供使用者輸入的 **docx with placeholder**。此範例示範了從初始化文件、**how to insert sdt**、**add placeholder to tag**、加入一般內容，到最後儲存檔案的完整流程。

### 後續步驟

* 探索 **how to insert sdt** 在表格內的使用，以建立類表單的版面。  
* 結合此技巧與 **docx with placeholder** 合併，打造自動化報表產生器。  
* 嘗試其他控制項類型（`RICH_TEXT`、`CHECKBOX`），以建立更豐富的 Word 表單。  

歡迎將程式碼套用於您自己的模板引擎，並在留言區分享您的成果！

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，並以此為基礎。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索其他實作方式。

- [如何使用 DocumentBuilder 在 Aspose.Words for Java 中建立表單欄位並加入內容](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create Word Document Java – 新增帶陰影效果的矩形形狀](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [如何使用 Aspose.Words for Java 建立 PDF 文件 | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}