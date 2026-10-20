---
category: general
date: 2026-07-16
description: Aspose.Words for Java を使用して、Word ドキュメント内のボタンサイズをプログラムで設定します。ActiveX ボタンの挿入方法、ボタンの位置設定などを学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size
- insert activex button
- programmatically add button
- set button location
- create word document button
language: ja
lastmod: 2026-07-16
og_description: JavaでWord文書のボタンサイズを設定する。ステップバイステップのガイドで、ActiveXボタンの挿入、ボタン位置の設定、プログラムによるボタンの追加方法を示します。
og_image_alt: Screenshot of a Word document where the button size has been set using
  Aspose.Words for Java
og_title: JavaでWordのボタンサイズを設定する – 完全なAspose.Wordsチュートリアル
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  headline: Set Button Size in Word with Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  name: Set Button Size in Word with Java – Complete Aspose.Words Guide
  steps:
  - name: Expected Output Screenshot
    text: '![Word document showing the inserted button with the set button size](https://example.com/images/set-button-size.png
      "Screenshot of a Word file where the button size has been set using Aspose.Words
      for Java")'
  - name: “Can I set the button size using centimeters instead of points?”
    text: Word’s API only accepts points, but you can convert centimeters to points
      (`points = cm * 28.3465`). Write a small helper method if you prefer metric
      units.
  - name: “What if I need the button to appear on a specific page?”
    text: After inserting the button, you can move the cursor to a particular page
      using `builder.moveToPage(pageNumber)`. Insert the control right after the move,
      then set its location as shown above.
  - name: “Does this work with .doc (Word 97‑2003) files?”
    text: Yes—Aspose.Words automatically handles older formats. Just change the file
      extension in `doc.save("Demo.doc")`.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: JavaでWordのボタンサイズを設定する – 完全なAspose.Wordsガイド
url: /ja/java/using-document-elements/set-button-size-in-word-with-java-complete-aspose-words-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# JavaでWordのボタンサイズを設定 – 完全な Aspose.Words ガイド

Word ファイルを UI を開かずに **set button size** したいと思ったことはありませんか？ あなただけではありません。たとえば「Submit」ボタン付きのオンボーディングパケットをその場で生成する必要があるとき、プログラムで行うことで手作業の時間を大幅に削減できます。

このチュートリアルでは、**insert ActiveX button** の手順、サイズと位置の調整、そして最終的な保存までを詳しく解説します。最後まで読めば、Aspose.Words for Java を使って任意の Word 文書に **programmatically add button** コントロールを追加できるようになります。

## Prerequisites – What You Need Before You Start

- **Java Development Kit (JDK) 8+** – どの最近の JDK でも動作します。  
- **Aspose.Words for Java** ライブラリ（公式サイトから最新の JAR をダウンロード）。  
- お好みの **IDE** – IntelliJ IDEA、Eclipse、あるいはシンプルなテキストエディタでも構いません。  
- Java の基本的な文法に慣れていること；Word 自動化の深い知識は不要です。

> *Pro tip:* Aspose.Words の JAR をプロジェクトのクラスパスに入れておかないと、`com.aspose.words.*` をインポートした瞬間に `ClassNotFoundException` が発生します。

## Step 1: Create a New Word Document

最初に空のドキュメントと `DocumentBuilder` を作成します。ビルダーはファイル内に何でも描くことができるペンのようなものです。

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document.
        Document doc = new Document();

        // DocumentBuilder gives us a fluent API to add content.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Why this matters:** `Document` オブジェクトは .docx 全体を表し、`DocumentBuilder` は段落や表、そして **ActiveX** コントロールを挿入できる作業の中心です。

## Step 2: Insert ActiveX Button – The “Insert ActiveX Button” Moment

ここで実際に **insert activex button** を文書に挿入します。Aspose.Words は便利なメソッド `insertForms2OleControl` を提供しており、`Forms2OleControl` オブジェクトを返します。

```java
        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");   // Programmatic name.
        commandButton.setCaption("Submit");   // Text shown on the button.
```

> *What’s happening under the hood?* `Forms2OleControlType.COMMAND_BUTTON` は Word に対して、UI の開発者タブからドロップできる従来の CommandButton を要求していることを示します。

## Step 3: Set Button Size and Location – The Core “Set Button Size” Logic

ここがキーワードの本領発揮です。**set button size** と **set button location** を行い、コントロールがページ上の正確な位置に表示されるようにします。

```java
        // Position the button (distance from the left/top edges in points).
        commandButton.setLeft(100);   // 100 points from the left margin.
        commandButton.setTop(150);    // 150 points from the top margin.

        // Set the button's dimensions.
        commandButton.setWidth(80);   // Width = 80 points.
        commandButton.setHeight(30);  // Height = 30 points.
```

> **Why you should care:** ポイントは Word のネイティブ測定単位です（1 ポイント = 1/72 インチ）。`setLeft`、`setTop`、`setWidth`、`setHeight` を調整することで、ピクセル単位の正確な配置が可能になり、画面上では見えても印刷時にずれるといった問題が解消します。  
> 
> *Common pitfall:* 幅または高さのいずれかを設定し忘れると、デフォルトサイズのままになりクリックしにくくなることがあります。必ず両方を指定してください。

## Step 4: Save the Document – “Create Word Document Button” Completed

最後にファイルをディスクに書き出します。ここでは **create a Word document button** を .docx 内に作成したことになります。

```java
        // Persist the document to the file system.
        doc.save("CommandButtonDemo.docx");
    }
}
```

`CommandButtonDemo.docx` を Microsoft Word で開くと、左端から 100 pt、上端から 150 pt の位置に **Submit** ボタンが配置され、サイズは 80 × 30 pt になっているのが確認できます。UI でクリックするとデフォルトの ActiveX 動作がトリガーされます（必要に応じて VBA で後から処理を割り当てることも可能です）。

### Expected Output Screenshot

![Word document showing the inserted button with the set button size](https://example.com/images/set-button-size.png "Screenshot of a Word file where the button size has been set using Aspose.Words for Java")

*Alt text:* set button size in a Word document using Java

## Step 5 (Optional): Add More Controls or Style the Button

**programmatically add button** コントロールを 1 つ以上追加したい場合は、名前とキャプションを変えて挿入ブロックを繰り返すだけです。フォントや背景色の変更、さらには後で VBA マクロをバインドすることも可能です。

```java
        // Example: Adding a Cancel button next to Submit.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);   // Position it 90 points to the right of Submit.
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);
```

> *Tip:* プロフェッショナルな外観を保つために、すべてのボタンサイズは一定にしておきましょう。幅・高さを定数として保持すると簡単です。

## Common Questions & Edge Cases

### “Can I set the button size using centimeters instead of points?”
Word の API はポイントしか受け付けませんが、センチメートルをポイントに変換することは可能です（`points = cm * 28.3465`）。メトリック単位が好みの場合は小さなヘルパーメソッドを作成してください。

### “What if I need the button to appear on a specific page?”
ボタンを挿入した後、`builder.moveToPage(pageNumber)` でカーソルを目的のページに移動できます。その直後にコントロールを挿入し、上記と同様に位置を設定してください。

### “Does this work with .doc (Word 97‑2003) files?”
はい。Aspose.Words は古い形式も自動的に処理します。`doc.save("Demo.doc")` のように拡張子を変更すれば OK です。

## Full, Runnable Example

以下は、Aspose.Words の JAR がクラスパスにあることを前提に、すぐにコピー＆ペーストして実行できる完全なプログラムです。

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first ActiveX CommandButton.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");

        // 3️⃣ Set button location and size – the core set button size logic.
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // 4️⃣ (Optional) Add a second button for illustration.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);

        // 5️⃣ Save the document – you’ve now created a Word document button.
        doc.save("CommandButtonDemo.docx");
    }
}
```

プログラムを実行し、生成された `CommandButtonDemo.docx` を開くと、サイズが整った 2 つのボタンが表示されます。

## Conclusion – You’ve Mastered Setting Button Size in Word

このガイドでは **set button size** と **set button location** を Aspose.Words for Java で実装する手順を、最初から最後まで網羅しました。これらの手順に従えば、**insert activex button**、**programmatically add button** コントロール、そして **create word document button** 要素を自由に作成できるようになります。

次は何をしますか？ ボタンをテーブルセル内に埋め込んだり、送信前にフォームフィールドを検証する VBA マクロを添付したりしてみましょう。同様のパターンはチェックボックスやコンボボックスなど他の ActiveX コントロールにも適用でき、`Forms2OleControlType.COMMAND_BUTTON` を適切な列挙値に置き換えるだけです。

質問や問題があれば、下のコメント欄にご投稿ください。コーディングを楽しみながら、Word 文書自動生成の力を存分に活用してください！

## What Should You Learn Next?

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれているので、API の追加機能を習得したり、独自の実装方法を探求したりするのに役立ちます。

- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [How to remove footers from Word documents using Aspose.Words for Java](/words/english/java/document-manipulation/removing-content-from-documents/)
- [Aspose.Words Java&#58; Comprehensive Guide to Word Document Processing](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}