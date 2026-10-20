---
category: general
date: 2026-10-20
description: 以程式方式建立空白 DOCX，並使用 Java 嵌入指令按鈕。學習完整的建立 Word 文件程式碼，以儲存含按鈕的 Word 檔案，並設定指令按鈕的說明文字。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank docx programmatically
- create word document code
- save word with button
- add command button word
- set command button caption
language: zh-hant
lastmod: 2026-10-20
og_description: 以程式方式建立空白 DOCX 並嵌入指令按鈕。遵循此一步一步的 Java 教學，將 Word 儲存為含按鈕的檔案，並設定指令按鈕的標題。
og_image_alt: Screenshot of a blank DOCX file with an inserted command button created
  programmatically
og_title: 以程式方式建立空白 DOCX – 加入指令按鈕
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  headline: Create a blank DOCX programmatically and add a command button
  type: TechArticle
- description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  name: Create a blank DOCX programmatically and add a command button
  steps:
  - name: Initialize a new blank document
    text: A blank document is the canvas on which you’ll place the command button.
      Aspose.Words provides the `Document` class for this purpose.
  - name: Set up a `DocumentBuilder`
    text: '`DocumentBuilder` is a helper that lets you insert content, including OLE
      controls, without dealing with low‑level node manipulation.'
  - name: Insert an OLE command button
    text: Word treats interactive controls as OLE (Object Linking and Embedding) objects.
      Aspose.Words exposes `Forms2OleControl` for this.
  - name: Configure the button – type, caption, and location
    text: You must define the control’s type (`COMMANDBUTTON`), set a user‑visible
      caption, and place it on the page.
  - name: Save the document with the embedded button
    text: Finally, write the file to disk. The resulting file can be opened in Microsoft
      Word, where the button will be fully functional.
  - name: Expected result
    text: 'When you open `CommandButton.docx` in Microsoft Word:'
  type: HowTo
tags:
- Java
- DOCX
- Aspose.Words
- Command button
- Automation
title: 以程式方式建立空白 DOCX 並加入指令按鈕
url: /zh-hant/java/document-manipulation/create-a-blank-docx-programmatically-and-add-a-command-butto/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 以程式方式建立空白 DOCX 並加入指令按鈕

如果您需要 **以程式方式建立空白 DOCX**，本教學將示範如何直接在檔案中嵌入指令按鈕。您將取得完整的 *create word document code*，可儲存含按鈕的 Word 文件、讓您 **set command button caption**，且相容最新的 Aspose.Words for Java 函式庫。

在 DOCX 檔案中嵌入互動式控制項非常有用，尤其在您想要發佈會觸發巨集、啟動外部程式，或僅以可點擊的「Click Me」按鈕引導使用者時。以下步驟涵蓋從初始化空白文件到將最終檔案寫入磁碟的全部過程。

## 前置條件

* 已安裝 Java 17 或更新版本。  
* Maven（或您偏好的建置工具）以管理相依性。  
* Aspose.Words for Java 23.9 或更新版本。將相依性加入您的 `pom.xml`：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

* 任何支援 Java 的 IDE，例如 IntelliJ IDEA 或 VS Code。

## 以程式方式建立空白 DOCX – 步驟說明

以下各節將流程拆解為清晰的編號步驟。每一步皆說明 **為何** 需要此步驟，而不僅是 **要輸入什麼**。

### 步驟 1：初始化新的空白文件

空白文件是您放置指令按鈕的畫布。Aspose.Words 提供 `Document` 類別以完成此目的。

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

*Why this matters*：從空的 `Document` 開始，可確保沒有隱藏的格式或既有控制項會干擾您之後加入的按鈕。

### 步驟 2：設定 `DocumentBuilder`

`DocumentBuilder` 是協助您插入內容（包括 OLE 控制項）的工具，無需處理低階節點操作。

```java
        // Step 2: Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this matters*：建構器會維持目前的游標位置，因而可將按鈕精確放置在您指定的位置。

### 步驟 3：插入 OLE 指令按鈕

Word 將互動控制項視為 OLE（Object Linking and Embedding）物件。Aspose.Words 以 `Forms2OleControl` 來呈現此功能。

```java
        // Step 3: Insert an OLE command button into the document
        com.aspose.words.forms.Forms2OleControl commandButton = builder.insertForms2OleControl();
```

*Why this matters*：插入控制項會產生佔位元，之後您可以設定其類型、標題與位置。

### 步驟 4：設定按鈕 – 類型、標題與位置

您必須定義控制項的類型（`COMMANDBUTTON`）、設定使用者可見的標題，並將其放置於頁面上。

```java
        // Step 4: Configure the command button's type, caption, and position
        commandButton.setOleControlType(com.aspose.words.forms.OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");               // set command button caption
        commandButton.setLeft(100);                         // distance from the left margin (points)
        commandButton.setTop(200);                          // distance from the top margin (points)
```

*Why this matters*：  
* **Type** 告訴 Word 此控制項的行為類似可點擊的按鈕。  
* **Caption** 是使用者看到的文字；變更它即是 **set command button caption** 的方式。  
* **Left** 與 **Top** 控制精確的放置位置，這在您 **add command button word** 需要精確版面的文件時尤為重要。

### 步驟 5：儲存含嵌入按鈕的文件

最後，將檔案寫入磁碟。產生的檔案可於 Microsoft Word 開啟，且按鈕將完整運作。

```java
        // Step 5: Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

*Why this matters*：此步驟 **saves Word with button**，讓控制項在不同機器間仍能保留。該檔案可作為範本分發，或用於自動化報表產生流程。

## 完整範例

將下方完整類別複製到名為 `CommandButtonDemo.java` 的檔案中，將 `YOUR_DIRECTORY` 調整為實際路徑，然後以 `mvn compile exec:java` 執行。

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.OleControlType;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an OLE command button into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the command button
        commandButton.setOleControlType(OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");   // set command button caption
        commandButton.setLeft(100);             // points from left margin
        commandButton.setTop(200);              // points from top margin

        // Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

### 預期結果

當您在 Microsoft Word 開啟 `CommandButton.docx` 時：

* 文件除了標有 **Click Me** 的按鈕外，完全是空白。  
* 點擊該按鈕會顯示 Word 的預設行為（除非附加巨集，否則不會執行任何操作），以此證明 OLE 控制項已正確嵌入。

## 常見問題與特殊情況

| Question | Answer |
|----------|--------|
| **我可以變更按鈕大小嗎？** | 是的。使用 `commandButton.setWidth(double)` 與 `commandButton.setHeight(double)` 以點為單位調整尺寸。 |
| **如果需要在按鈕上附加巨集該怎麼辦？** | 按鈕本身僅是 OLE 控制項。您必須手動或透過 Aspose.Words `Document` API 的 `addMacro` 工具將 VBA 巨集加入文件。 |
| **按鈕能在 LibreOffice 中運作嗎？** | LibreOffice 只支援有限的 OLE 控制項。按鈕會顯示，但其點擊行為可能不同。 |
| **如何加入多個按鈕？** | 重複步驟 3‑4，使用新的 `Forms2OleControl` 實例。為每個按鈕調整 `setLeft`/`setTop` 以避免重疊。 |
| **此程式碼能相容 .NET 嗎？** | 原理相同，但您需要使用 .NET 版的 `Aspose.Words` 類別（`Document`、`DocumentBuilder`、`Forms2OleControl`）。 |

## 現場小技巧

* **Pro tip:** 在插入按鈕前使用 `builder.moveToDocumentEnd()`，可將按鈕放在文件最末端，無論先前內容為何。  
* **Watch out for:** 設定過小的 `Left`/`Top` 可能會把按鈕放到可列印區域之外，導致在 Word 版面檢視中看不到。  
* **Performance note:** 插入大量 OLE 控制項會增加檔案大小。若僅需視覺提示，建議改用普通的 `Shape` 並加上超連結。

## 結論

您現在已了解如何 **以程式方式建立空白 DOCX**，並使用 Java 嵌入完整功能的指令按鈕。本教學涵蓋了整個 *create word document code* 工作流程，示範了如何 **save Word with button**，展示了正確的 **add command button word** 元素使用方式，並說明了如何 **set command button caption**。

接下來您可以：

* 加入更多 OLE 控制項（核取方塊、下拉式清單）以打造更豐富的表單。  
* 附加 VBA 巨集，使按鈕執行自訂動作。  
* 結合此技巧與文件合併列印（mail‑merge），製作動態、互動式範本。

歡迎自行嘗試不同的按鈕樣式、位置與其他控制項，以符合您的業務需求。祝開發愉快

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，進一步延伸所示技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索其他實作方式。

- [以指令按鈕建立空白 Word 文件 – 步驟指南](/words/english/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/)
- [如何在 Word 中插入 ActiveX 按鈕 – 設定按鈕標題](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)
- [以 Java 建立空白 Word 文件 – 完整 Aspose.Words 指南](/words/english/java/document-loading-and-saving/create-blank-word-document-with-java-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}