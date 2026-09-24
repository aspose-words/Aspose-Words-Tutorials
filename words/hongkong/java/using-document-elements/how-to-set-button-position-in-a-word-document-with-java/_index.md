---
category: general
date: 2026-09-24
description: 使用 Java 與 Aspose.Words 設定 Word 文件中按鈕的位置。了解如何插入按鈕、加入 ActiveX 控制項，以及以 Java
  風格建立 Word 文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button position
- how to insert button
- add activex control
- add button to word
- create word document java
language: zh-hant
lastmod: 2026-09-24
og_description: 使用 Java 設定 Word 文件中的按鈕位置。本指南說明如何插入按鈕、加入 ActiveX 控制項，以及使用 Aspose.Words
  建立 Java 的 Word 文件。
og_image_alt: Screenshot of a Word document showing a CommandButton positioned at
  100 px left and 150 px top
og_title: 使用 Java 在 Word 文件中設定按鈕位置 – 完整指南
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  headline: How to set button position in a Word document with Java
  type: TechArticle
- description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  name: How to set button position in a Word document with Java
  steps:
  - name: Expected output
    text: '* A `.docx` file named **CommandButtonDemo.docx**. * Inside the document,
      a **CommandButton** labeled “Click Me” appears 100 px from the left margin and
      150 px from the top margin. * The button responds to clicks when the document
      is opened in Word (it will display a default ActiveX message unless y'
  - name: Adding multiple buttons
    text: If you need to **add button to Word** more than once, repeat steps 3‑5 with
      a new `Forms2OleControl` instance each time. Remember to adjust the `setTop`
      value so buttons don’t overlap.
  - name: Working without a license
    text: 'Aspose.Words adds a watermark when used without a license. For production
      code, purchase a license and apply it at the start of `main`:'
  - name: Compatibility with older Office versions
    text: 'ActiveX controls are supported in the `.doc` (Word 97‑2003) format. To
      create a legacy file, change the save format:'
  - name: Next steps
    text: '* Explore other `Forms2OleControl.ControlType` values (e.g., `CHECKBOX`,
      `TEXTBOX`) to build richer forms. * Combine the button with VBA macros for custom
      click handling. * Use Aspose.Words’ mail‑merge feature to generate personalized
      documents that already contain interactive controls.'
  type: HowTo
- questions:
  - answer: Yes. Aspose.Words is pure Java and runs on any JDK 8+ implementation,
      including OpenJDK.
    question: Does this work with OpenJDK?
  - answer: ActiveX button appearance is controlled by the host application (Word).
      You can attach VBA code to modify properties at runtime, but the static appearance
      is limited to the default style.
    question: Can I change the button’s font or color?
  - answer: 'Move the `DocumentBuilder` cursor into the cell before calling `insertForms2OleControl`.
      The control will inherit the cell’s layout, and you can still use `setLeft`/`setTop`
      for fine‑tuning. ## Conclusion You now know how to **set button position** in
      a Word document using Java, how to **how to inse'
    question: What if I need to place the button inside a table cell?
  type: FAQPage
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- CommandButton
title: 如何使用 Java 在 Word 文件中設定按鈕位置
url: /zh-hant/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文件中使用 Java 設定按鈕位置

如果您需要在 Word 檔案中 **設定按鈕位置**，本指南會提供完整且可執行的解決方案。無論您是建立需要使用者互動的範本，或是自動化表單，您都將學會如何使用 Aspose.Words for Java **插入按鈕** 並控制其放置位置。

本教學涵蓋了在 Word 文件中 **加入 ActiveX 控制項** 所需的全部內容，說明如何 **將按鈕加入 Word**，並示範完整的 **使用 Java 建立 Word 文件** 流程。無需任何外部參考——只要複製、執行並驗證結果即可。

## 前置條件

* 已安裝 Java 17（或任何 Java 8+ 執行環境）。
* Maven 或 Gradle 以管理相依性。
* Aspose.Words for Java 授權（免費試用版可用於評估）。
* 基本的 Java 語法概念。

> **專業提示：** 將 Aspose.Words 的 JAR 檔放在 `libs/` 資料夾，並將其加入專案的 classpath，以避免版本衝突。

## 步驟 1：設定 Maven 專案

建立一個簡易的 Maven 專案（或使用 Gradle），並加入 Aspose.Words 相依性：

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-button-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest at time of writing -->
        </dependency>
    </dependencies>
</project>
```

執行 `mvn clean compile` 會下載函式庫並準備建置路徑。

## 步驟 2：建立新的 Word 文件

第一個操作是以 **create Word document java** 方式建立文件。您需要實例化 `Document` 物件與 `DocumentBuilder`，以便編輯檔案。

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` 類別代表整個 .docx 檔案，而 `DocumentBuilder` 提供流暢的 API 以插入內容。

## 步驟 3：如何插入按鈕 – 加入 ActiveX 控制項

Aspose.Words 針對插入舊版 ActiveX 控制項（例如 CommandButton）提供 `Forms2OleControl` 類別。此步驟示範了 **how to insert button** 的確切做法。

```java
        // Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
```

`insertForms2OleControl` 方法會回傳可自行設定的 `Forms2OleControl` 實例。這是 **add ActiveX control** 流程的核心。

## 步驟 4：設定按鈕位置

現在我們實際 **設定按鈕位置**。控制項的 `setLeft` 與 `setTop` 方法接受點數值（1 pt = 1/72 in）。為了與一般螢幕座標對齊，您可以將像素轉換為點數（1 px ≈ 0.75 pt）。範例中，我們將按鈕放在距左邊緣 100 px、距上邊緣 150 px 的位置。

```java
        // Position the button on the page
        commandButton.setLeft(100 * 0.75);   // 75 pt ≈ 100 px
        commandButton.setTop(150 * 0.75);    // 112.5 pt ≈ 150 px
```

由於 **set button position** 的邏輯已封裝於此，您可以在需要移動控制項時重複使用這些程式碼。依需求調整數值即可符合版面需求。

## 步驟 5：定義大小與標題

沒有標籤的按鈕會讓人困惑。使用 `setWidth`、`setHeight` 與 `setCaption` 為其設定可見外觀。

```java
        // Define size and caption
        commandButton.setWidth(120 * 0.75);   // 90 pt width
        commandButton.setHeight(30 * 0.75);   // 22.5 pt height
        commandButton.setCaption("Click Me");
```

大小同樣以點數表示，為了保持一致性，我們會先將像素轉換為點數。

## 步驟 6：儲存文件 – 完成 **create Word document java** 流程

最後，將檔案寫入磁碟。路徑可以是絕對路徑或相對於專案根目錄。

```java
        // Save the document containing the CommandButton
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

執行程式後會在 `output` 資料夾產生 `CommandButtonDemo.docx`。在 Microsoft Word 中開啟該檔案，即可看到按鈕正確地出現在您設定的位置。

### 預期輸出

* 一個名為 **CommandButtonDemo.docx** 的 `.docx` 檔案。
* 文件內部會出現一個標示為「Click Me」的 **CommandButton**，其位置距左邊距 100 px、上邊距 150 px。
* 當文件在 Word 中開啟時，按鈕會回應點擊（除非您附加自訂 VBA 程式碼，否則會顯示預設的 ActiveX 訊息）。

## 步驟 7：常見變體與邊緣情況

### 新增多個按鈕

如果您需要 **add button to Word** 超過一次，請在每次使用新 `Forms2OleControl` 實例時重複步驟 3‑5。記得調整 `setTop` 的數值，以免按鈕重疊。

```java
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
        secondButton.setLeft(200 * 0.75);
        secondButton.setTop(250 * 0.75);
        secondButton.setWidth(120 * 0.75);
        secondButton.setHeight(30 * 0.75);
        secondButton.setCaption("Second");
```

### 未使用授權時的處理

Aspose.Words 在未授權的情況下會加入浮水印。正式環境建議購買授權，並在 `main` 方法開始時套用：

```java
        License license = new License();
        license.setLicense("Aspose.Words.lic");
```

### 與舊版 Office 相容性

ActiveX 控制項在 `.doc`（Word 97‑2003）格式中受支援。若要建立舊版檔案，只需變更儲存格式：

```java
        doc.save("CommandButtonDemo.doc", SaveFormat.DOC);
```

## 完整原始碼（可執行）

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Optional: apply a license if you have one
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control (how to insert button)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);

        // Step 3: Position the button on the page (set button position)
        commandButton.setLeft(100 * 0.75);   // distance from the left edge (points)
        commandButton.setTop(150 * 0.75);    // distance from the top edge (points)

        // Step 4: Define the button's size and caption
        commandButton.setWidth(120 * 0.75);   // width in points
        commandButton.setHeight(30 * 0.75);   // height in points
        commandButton.setCaption("Click Me");

        // Step 5: Save the document containing the CommandButton (create word document java)
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

將檔案儲存為 `src/main/java/CommandButtonDemo.java`，執行 `mvn exec:java -Dexec.mainClass=CommandButtonDemo`，然後開啟產生的文件即可看到結果。

## 常見問題

**Q: 這能在 OpenJDK 上運作嗎？**  
A: 可以。Aspose.Words 為純 Java，能在任何 JDK 8+ 實作上執行，包括 OpenJDK。

**Q: 我可以變更按鈕的字型或顏色嗎？**  
A: 按鈕的外觀由主機應用程式（Word）控制。您可以附加 VBA 程式碼於執行時修改屬性，但靜態外觀僅限於預設樣式。

**Q: 如果我要把按鈕放在表格儲存格內該怎麼做？**  
A: 在呼叫 `insertForms2OleControl` 前，先將 `DocumentBuilder` 游標移至該儲存格內。控制項會繼承儲存格的版面配置，且仍可使用 `setLeft`/`setTop` 進行微調。

## 結論

您現在已了解如何使用 Java 在 Word 文件中 **設定按鈕位置**、**插入按鈕**、**加入 ActiveX 控制項**，以及在 **create Word document java** 專案中遵循最佳實踐。完整範例示範了從專案設定到產生包含功能性 CommandButton 的 `.docx` 檔案的整個工作流程。

### 後續步驟

* 探索其他 `Forms2OleControl.ControlType` 值（例如 `CHECKBOX`、`TEXTBOX`），以建立更豐富的表單。
* 將按鈕與 VBA 巨集結合，以實作自訂點擊處理。
* 使用 Aspose.Words 的郵件合併功能，產生已包含互動控制項的個人化文件。

祝開發順利，盡情享受使用 Java 自動化 Word 文件的樂趣！

## 接下來該學什麼？

以下教學與本指南所示技術密切相關，能進一步延伸您的應用。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在自己的專案中探索其他實作方式。

- [如何使用 Aspose.Words for Java 的 DocumentBuilder 建立表單欄位並加入內容](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [在 Word 文件中使用 Aspose.Words for .NET 新增下拉式方塊表單欄位](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [如何使用 Aspose.Words Java 載入 Word 文件：完整指南](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}