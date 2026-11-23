---
category: general
date: 2026-11-22
description: 使用 Java 在 Word 文件中建立巨集按鈕。學習插入指令按鈕、設定按鈕文字，並將巨集連結至按鈕，以製作互動文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create macro button
- insert command button
- set button text
- link macro to button
- add interactive button
language: zh-hant
lastmod: 2026-11-22
og_description: 使用 Java 在 Word 文件中建立巨集按鈕。本教學示範如何插入指令按鈕、設定按鈕文字，並將巨集連結至按鈕以實現完整互動。
og_image_alt: Screenshot of a Word document showing a macro button created with Java
  code
og_title: 使用 Java 在 Word 文件中建立宏按鈕 – 步驟指南
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  headline: How to create macro button in a Word document with Aspose.Words for Java
  type: TechArticle
- description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  name: How to create macro button in a Word document with Aspose.Words for Java
  steps:
  - name: Insert command button into the document
    text: '`DocumentBuilder.insertForms2OleControl` creates an OLE control of the
      specified type. The `Forms2OleControlType.COMMAND_BUTTON` constant tells Aspose.Words
      to generate a command button that can host a macro.'
  - name: Set button text (caption)
    text: The caption is the visible label on the button. Use `setCaption` to define
      what the user sees.
  - name: Link macro to button
    text: A macro is identified by its name, for example `MyMacro`. The `setOnClick`
      method stores this name in the button’s `OnClick` event handler.
  - name: Add interactive button to a Word document
    text: After configuring the OLE control, you may want to position it, resize it,
      or add surrounding text. The `DocumentBuilder` continues to operate on the document,
      so you can insert paragraphs before or after the button.
  - name: Expected output
    text: 'Running the program generates `MacroButtonDemo.docm`. Opening the file
      in Microsoft Word shows:'
  type: HowTo
tags:
- Aspose.Words
- Java
- OLE controls
- Automation
title: 如何在 Word 文件中使用 Aspose.Words for Java 建立巨集按鈕
url: /zh-hant/java/using-document-elements/how-to-create-macro-button-in-a-word-document-with-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文件中使用 Aspose.Words for Java 建立巨集按鈕

如果您需要在 Word 檔案中 **建立巨集按鈕**，本指南將逐步說明所需的確切步驟。您將學習如何 **插入指令按鈕**、**設定按鈕文字**，以及 **將巨集連結至按鈕**，使文件具備完整的互動性。

開發人員常會嵌入 OLE 控制項，以在文件內觸發 VBA 巨集。本教學涵蓋完整工作流程，從專案設定到可執行的 Java 範例，將 **互動按鈕** 新增至 .docx 檔案。無需外部腳本——所有操作皆在 Java 程序內執行。

## 前置條件

* 已安裝 JDK 17 或更新版本。
* Maven 3.8+（或 Gradle）用於相依性管理。
* Aspose.Words for Java 23.9 或更新版本 – 此函式庫提供 `DocumentBuilder` 與 OLE 控制項 API。
* 具備 Java 與 VBA 巨集的基本知識。

如果缺少上述任何項目，請先安裝；本教學的其餘部分假設這些項目皆已就緒。

## 如何使用 Aspose.Words for Java 建立巨集按鈕

解決方案的核心包含四個動作：

1. **Insert command button** OLE 控制項插入至文件中。
2. **Set button text**（標題）為使用者所見的文字。
3. **Link macro to button** 使點擊時執行指定的 VBA 程序。
4. **Save the document** 並保留嵌入的巨集。

以下將在各自的章節中說明每個動作。

### 步驟 1：在文件中插入指令按鈕

`DocumentBuilder.insertForms2OleControl` 會建立指定類型的 OLE 控制項。`Forms2OleControlType.COMMAND_BUTTON` 常數告訴 Aspose.Words 產生可容納巨集的指令按鈕。

```java
import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load a blank document or create a new one
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Why this matters:** OLE 控制項充當巨集的容器。若未插入，使用者將沒有可點擊的視覺元素。

### 步驟 2：設定按鈕文字（標題）

標題是按鈕上可見的標籤。使用 `setCaption` 來定義使用者所見的文字。

```java
        // Set the button's caption – this is the text displayed on the button
        commandButton.setCaption("Run Report");
```

**Why this matters:** 清晰的按鈕文字可提升可用性。`setCaption` 方法會更新 OLE 控制項的 `Caption` 屬性，Word 會將其呈現為按鈕標籤。

### 步驟 3：將巨集連結至按鈕

巨集以名稱識別，例如 `MyMacro`。`setOnClick` 方法會將此名稱儲存在按鈕的 `OnClick` 事件處理常式中。

```java
        // Assign a macro to run when the button is clicked
        commandButton.setOnClick("MyMacro");
```

**Why this matters:** 連結巨集即可產生互動行為。使用者在 Word 中點擊按鈕時，會執行對應的 VBA 程序。

### 步驟 4：將互動按鈕新增至 Word 文件

設定好 OLE 控制項後，您可能需要定位、調整大小或加入前後文字。`DocumentBuilder` 仍可對文件操作，您可以在按鈕前後插入段落。

```java
        // Add a descriptive paragraph before the button
        builder.moveToDocumentStart();
        builder.writeln("Click the button below to generate the report:");

        // Move the cursor back to the button location (optional)
        builder.moveTo(commandButton.getNode());

        // Optionally, resize the button (width and height in points)
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // Save the document with the macro-enabled format
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

**Why this matters:** 以 `.docm` 儲存可保留巨集程式碼。若儲存為 `.docx`，巨集參照將會遺失。

## 完整可執行範例

以下為完整的 Java 程式碼，包含匯入、例外處理與說明每一步的註解。將程式碼複製到具備 Aspose.Words 相依性的 Maven 專案中並執行。

```java
// Maven dependency (add to pom.xml):
// <dependency>
//   <groupId>com.aspose</groupId>
//   <artifactId>aspose-words</artifactId>
//   <version>23.9</version>
// </dependency>

import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new empty document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Write an introductory paragraph
        builder.writeln("Press the button to execute the macro:");

        // 4. Insert the command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 5. Set the visual caption of the button
        commandButton.setCaption("Run Report");

        // 6. Link the button to a VBA macro named MyMacro
        commandButton.setOnClick("MyMacro");

        // 7. Resize the button for better appearance
        commandButton.setWidth(120);   // points
        commandButton.setHeight(30);   // points

        // 8. Save the document as a macro‑enabled file
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

### 預期輸出

執行程式會產生 `MacroButtonDemo.docm`。在 Microsoft Word 中開啟該檔案會顯示：

* 一段文字為 *“Press the button to execute the macro:”*（按下按鈕以執行巨集）。
* 一個標示為 **Run Report** 的按鈕，直接位於該段落下方。
* 點擊按鈕時，Word 會嘗試執行巨集 `MyMacro`。（您必須手動或透過其他自動化步驟將實際的 VBA 程式碼加入文件中。）

若巨集不存在，Word 會顯示安全性警告，這是巨集啟用文件的標準行為。

## 常見變化與邊緣情況

| Scenario | How to adapt the code |
|----------|-----------------------|
| **不同的按鈕標題** | 將傳遞給 `setCaption` 的字串更改。 |
| **多個按鈕** | 重複呼叫 `insertForms2OleControl`，每次使用各自的 `setCaption` 與 `setOnClick`。 |
| **自訂巨集名稱** | 將 `"MyMacro"` 替換為任何有效的 VBA 程序名稱，例如 `"ExportToExcel"`。 |
| **按鈕尺寸限制** | 調整 `setWidth` 與 `setHeight` 的值；Word 會依照您提供的點數套用。 |
| **以程式方式嵌入巨集** | 使用 `Document.getBuiltInDocumentProperties().add("Macros", …)` 或其他 VBA 注入步驟；Aspose.Words 本身不會寫入 VBA 程式碼。 |

**Pro tip:** 開發時，請務必在將宏安全性設定為 *Enable all macros*（啟用所有巨集）的機器上測試產生的 `.docm`。在正式環境中，請使用受信任的憑證簽署巨集，以避免安全提示。

## 疑難排解清單

* **按鈕未顯示** – 確認文件已儲存為 `.docm`，且在支援 OLE 控制項的 Word 版本中開啟。
* **巨集未執行** – 確保巨集名稱完全相符（包括大小寫），且該巨集已存在於文件的 VBA 專案中。
* **按鈕標題被截斷** – 使用 `setWidth` 增加按鈕寬度，以容納較長的文字。
* **版面配置意外移位** – 使用 `builder.moveTo` 在插入控制項前精確定位游標。

## 結論

您現在已了解如何使用 Java 在 Word 文件中 **建立巨集按鈕**、**插入指令按鈕**、**設定按鈕文字**，以及 **將巨集連結至按鈕**，以實現完整的互動性。完整範例示範了所有必要的 API 呼叫，說明每一步的重要性，並提供常見變化的指引。

接下來，您可以探索：

* **將互動按鈕** 新增至現有範本，而非新文件。
* **以程式方式注入 VBA 程式碼**，使用 Open XML SDK 或其他自動化工具。
* **結合多個 OLE 控制項**（核取方塊、清單方塊）以建立豐富的表單。

嘗試不同的標題、巨集名稱與按鈕尺寸，以符合您的特定使用情境。祝開發愉快！

## 接下來您應該學習什麼？

以下教學涵蓋與本指南密切相關的主題，建立於本教學所示技術之上。每個資源皆包含完整可運作的程式碼範例與逐步說明，協助您精通其他 API 功能，並在自己的專案中探索替代實作方式。

- [如何使用 Java 在 Word 文件中插入指令按鈕](/words/english/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/)
- [如何使用 Java 設定 Word 文件中按鈕的位置](/words/english/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/)
- [如何在 Word 中插入 ActiveX 按鈕 – 設定按鈕標題](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}