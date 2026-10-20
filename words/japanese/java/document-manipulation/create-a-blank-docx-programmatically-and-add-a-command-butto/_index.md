---
category: general
date: 2026-10-20
description: Java を使用してプログラムで空の DOCX を作成し、コマンドボタンを埋め込みます。ボタン付きの Word を保存し、コマンドボタンのキャプションを設定する完全な
  Word 文書作成コードを学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank docx programmatically
- create word document code
- save word with button
- add command button word
- set command button caption
language: ja
lastmod: 2026-10-20
og_description: プログラムで空白のDOCXを作成し、コマンドボタンを埋め込みます。このステップバイステップのJavaガイドに従って、ボタン付きのWordを保存し、コマンドボタンのキャプションを設定してください。
og_image_alt: Screenshot of a blank DOCX file with an inserted command button created
  programmatically
og_title: プログラムで空白のDOCXを作成 – コマンドボタンを追加
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
title: プログラムで空白のDOCXを作成し、コマンドボタンを追加する
url: /ja/java/document-manipulation/create-a-blank-docx-programmatically-and-add-a-command-butto/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# プログラムで空のDOCXを作成し、コマンドボタンを追加する

If you need to **空のDOCXをプログラムで作成**, this tutorial shows you how to embed a command button directly into the file. You’ll get the complete *Word文書作成コード* that saves a Word document with a button, lets you **コマンドボタンのキャプションを設定**, and works with the latest Aspose.Words for Java library.

Embedding interactive controls in a DOCX file is useful when you want to distribute templates that trigger macros, launch external programs, or simply guide users with a clickable “Click Me” button. The steps below cover everything from initializing a blank document to persisting the final file on disk.

## 前提条件

* Java 17 or newer installed.
* Maven (or your preferred build tool) to manage dependencies.
* Aspose.Words for Java 23.9 or later. Add the dependency to your `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

* An IDE such as IntelliJ IDEA or VS Code (any editor that supports Java works).

## プログラムで空のDOCXを作成する – 手順ごとに

The following sections break the process into clear, numbered steps. Each step explains **why** it’s needed, not just **what** to type.

### 手順 1: 新しい空のドキュメントを初期化

A blank document is the canvas on which you’ll place the command button. Aspose.Words provides the `Document` class for this purpose.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

*この重要性*: Starting with an empty `Document` ensures no hidden formatting or existing controls interfere with the button you’ll add later.

### 手順 2: `DocumentBuilder` を設定

`DocumentBuilder` is a helper that lets you insert content, including OLE controls, without dealing with low‑level node manipulation.

```java
        // Step 2: Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*この重要性*: The builder maintains the current cursor position, so the button will be placed exactly where you specify.

### 手順 3: OLE コマンドボタンを挿入

Word treats interactive controls as OLE (Object Linking and Embedding) objects. Aspose.Words exposes `Forms2OleControl` for this.

```java
        // Step 3: Insert an OLE command button into the document
        com.aspose.words.forms.Forms2OleControl commandButton = builder.insertForms2OleControl();
```

*この重要性*: Inserting the control creates a placeholder that you can later configure (type, caption, position).

### 手順 4: ボタンを構成 – タイプ、キャプション、位置

You must define the control’s type (`COMMANDBUTTON`), set a user‑visible caption, and place it on the page.

```java
        // Step 4: Configure the command button's type, caption, and position
        commandButton.setOleControlType(com.aspose.words.forms.OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");               // set command button caption
        commandButton.setLeft(100);                         // distance from the left margin (points)
        commandButton.setTop(200);                          // distance from the top margin (points)
```

*この重要性*:  
* **Type** tells Word the control behaves like a clickable button.  
* **Caption** is the text the user sees; changing it is how you **コマンドボタンのキャプションを設定**.  
* **Left** and **Top** control the exact placement, which is essential when you **コマンドボタンをWordに追加** documents that need precise layout.

### 手順 5: 埋め込まれたボタン付きでドキュメントを保存

Finally, write the file to disk. The resulting file can be opened in Microsoft Word, where the button will be fully functional.

```java
        // Step 5: Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

*この重要性*: This step **ボタン付きのWordを保存** so the control persists across machines. The file can be distributed as a template or used in automated report generation pipelines.

## 完全な動作例

Copy the entire class below into a file named `CommandButtonDemo.java`, adjust `YOUR_DIRECTORY` to a real path, and run it with `mvn compile exec:java`.

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

### 期待される結果

When you open `CommandButton.docx` in Microsoft Word:

* The document is completely blank except for a button labeled **Click Me**.
* Clicking the button will display the default Word behavior (it does nothing unless a macro is attached), confirming that the OLE control was correctly embedded.

## よくある質問とエッジケース

| Question | Answer |
|----------|--------|
| **Can I change the button size?** | Yes. Use `commandButton.setWidth(double)` and `commandButton.setHeight(double)` to adjust dimensions in points. |
| **What if I need a macro attached to the button?** | The button itself is just an OLE control. You must add a VBA macro to the document manually or via the Aspose.Words `Document` API’s `addMacro` utilities. |
| **Will the button work in LibreOffice?** | LibreOffice supports limited OLE controls. The button appears, but its click behavior may differ. |
| **How to add multiple buttons?** | Repeat Steps 3‑4 with a new `Forms2OleControl` instance. Adjust `setLeft`/`setTop` for each button to avoid overlap. |
| **Is the code compatible with .NET?** | The same logic applies, but you’d use `Aspose.Words` for .NET classes (`Document`, `DocumentBuilder`, `Forms2OleControl`). |

## 現場からのヒント

* **Pro tip:** Use `builder.moveToDocumentEnd()` before inserting the button if you want it at the very end of the document, regardless of prior content.
* **Watch out for:** Very small `Left`/`Top` values can place the button outside the printable area, making it invisible in Word’s layout view.
* **Performance note:** Inserting many OLE controls can increase file size. If you only need a visual cue, consider using a plain `Shape` with a hyperlink instead.

## 結論

You now know how to **空のDOCXをプログラムで作成** and embed a fully functional command button using Java. The tutorial covered the entire *Word文書作成コード* workflow, demonstrated how to **ボタン付きのWordを保存**, showed the correct way to **コマンドボタンをWordに追加** elements, and explained how to **コマンドボタンのキャプションを設定**. 

From here you can:

* Add more OLE controls (checkboxes, combo boxes) for richer forms.
* Attach VBA macros to make the button perform custom actions.
* Combine this technique with document mail‑merge for dynamic, interactive templates.

Feel free to experiment with button styles, positions, and additional controls to match your specific business requirements. Happy coding

## 次に学ぶべきことは？

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create blank word document with a command button – step‑by‑step guide](/words/english/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/)
- [How to Insert ActiveX Button in Word – Set Button Caption](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)
- [Create Blank Word Document with Java – Full Aspose.Words Guide](/words/english/java/document-loading-and-saving/create-blank-word-document-with-java-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}