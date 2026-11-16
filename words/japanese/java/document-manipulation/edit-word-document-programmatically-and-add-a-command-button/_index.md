---
category: general
date: 2026-11-15
description: Word文書をプログラムで編集してコマンドボタンを挿入します。ボタンの追加方法、コマンドボタンの名前設定、そして数分でWordのフォームボタンを作成する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit word document programmatically
- how to add button
- insert command button word
- create form button word
- set command button name
language: ja
lastmod: 2026-11-15
og_description: Word文書をプログラムで編集し、コマンドボタンを挿入します。このガイドでは、ボタンの追加方法、コマンドボタンの名前設定、そしてWordでフォームボタンをすばやく作成する方法を示します。
og_image_alt: Screenshot of a Word document edited programmatically with a command
  button
og_title: Word文書をプログラムで編集 – コマンドボタンを追加
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  headline: Edit Word document programmatically and add a command button
  type: TechArticle
- description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  name: Edit Word document programmatically and add a command button
  steps:
  - name: Expected output
    text: 'When you open the saved file:'
  - name: How to add button to a specific paragraph?
    text: '```java builder.moveToParagraph(2, true); // moves to third paragraph (0‑based
      index) Forms2OleControl btn = builder.insertForms2OleControl(); btn.setName("btnThirdParagraph");
      btn.setCaption("Click Me"); ```'
  - name: How to insert a button inside a table cell?
    text: '```java Table table = builder.startTable(); builder.insertCell(); builder.insertCell();
      builder.endTable();'
  - name: What if I need a larger button?
    text: '```java cmdBtn.setWidth(100); // width in points cmdBtn.setHeight(30);
      // height in points ```'
  - name: How to **insert command button word** using a different language (e.g.,
      C#)?
    text: 'The same logic applies; replace Java syntax with C# equivalents:'
  type: HowTo
tags:
- Word automation
- Aspose.Words
- Java
title: Word文書をプログラムで編集し、コマンドボタンを追加する
url: /ja/java/document-manipulation/edit-word-document-programmatically-and-add-a-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# プログラムでWord文書を編集し、コマンドボタンを追加する

プログラムで **Word 文書を編集** する必要がある場合、最速の方法は Aspose.Words API を使用することです。このチュートリアルでは、**ボタンを追加** する方法、キャプションの設定方法、そして **コマンドボタン名を設定** する方法を正確に示します。これにより、ドキュメントはシンプルなフォームとして機能します。最後には、機能するコマンドボタンを含む完全に編集可能な *.docx* が得られ、下流処理にすぐ使えるようになります。

Word を手動で開かずに、**コマンドボタンの文字列を挿入** する方法、**フォームボタンの文字列を作成** する方法、そしてボタンのプロパティを管理する方法を学びます。前提条件は、基本的な Java 開発環境と Aspose.Words for Java ライブラリだけです。

## 前提条件

- Java 17 以降（コードは Java 8+ でも動作します）
- Aspose.Words for Java（[Aspose.Words for Java](https://products.aspose.com/words/java/) からダウンロード）
- 変更したい既存の Word 文書（`input.docx`）
- Aspose.Words の依存関係を追加するための Maven または Gradle の知識

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## 手順 1: Word 文書をロードする

プログラムで **Word 文書を編集** する際の最初の操作は、ソースファイルを `Document` オブジェクトにロードすることです。このオブジェクトはメモリ上で Word ファイル全体を表し、内容を操作できるようにします。

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load the existing Word file
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Why this matters:** ドキュメントをロードすると、Aspose.Words が走査・変更できる DOM に似た構造が生成されます。このステップを省略すると、ボタン挿入の対象がなくなります。

## 手順 2: ドキュメントを編集するために `DocumentBuilder` を作成する

`DocumentBuilder` は Word ファイル内のカーソルのように機能します。現在の位置にテキスト、画像、フォームコントロールを挿入できます。

```java
        // Initialize a builder positioned at the start of the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Tip:** 特定の段落にボタンが必要な場合は、`builder.moveToParagraph(index, true);` でビルダーを先に移動させてください。

## 手順 3: Forms2OleControl（コマンドボタン）を挿入する

これで、Word ファイルに **ボタンを追加** するという中心的な質問に答えます。`insertForms2OleControl()` メソッドはレガシーな *Forms2.0* コマンドボタンを作成し、Word のバージョン間で最も互換性のあるコントロールです。

```java
        // Insert the command button at the builder's current cursor location
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();
```

> **Edge case:** Forms2.0 コントロールは Word の *Design Mode* でのみ表示されます。新しい ActiveX ボタンが必要な場合は `insertOleControl()` を検討してください。ただし、レガシーコントロールはほとんどの自動化シナリオで機能します。

## 手順 4: ボタンのプロパティを設定する

コントロールを挿入した後、**コマンドボタン名を設定** し、**コマンドボタンの文字列を挿入**（キャプション）して、ユーザーにとって使いやすくできます。

```java
        // Set the internal name used by automation scripts
        cmdBtn.setName("cmdSubmit");

        // Set the text that appears on the button
        cmdBtn.setCaption("Submit");
```

> **Why these properties?**  
> - `setName` はボタンに VBA や外部ツールが参照できる識別子を付与します。  
> - `setCaption` は表示ラベルで、実質的にエンドユーザーがクリックする **フォームボタンの文字列を作成** します。

サイズや位置を調整したり、基になる OLE オブジェクトにアクセスしてマクロを追加したりすることもできますが、これらはこの簡易ガイドの範囲外です。

## 手順 5: 変更されたドキュメントを保存する

最後に、変更を新しいファイルに保存します。このステップで出力ドキュメントに **フォームボタンの文字列が作成** されます。

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Result:** Microsoft Word で `output.docx` を開くと、“Submit” とラベル付けされたボタンが表示されます。Word を *Design Mode*（開発タブ → デザインモード）に切り替えると、ボタンをダブルクリックしてマクロを割り当てるか、単にフォームのプレースホルダーとして使用できます。

### 期待される出力

保存したファイルを開くと：

- カーソル挿入位置がボタンに置き換わります。
- ボタンはキャプション **Submit** を表示します。
- ボタンの内部名は **cmdSubmit** で、VBA や外部の自動化スクリプトから参照できます。

## よくある質問とバリエーション

### 特定の段落にボタンを追加する方法は？

```java
builder.moveToParagraph(2, true); // moves to third paragraph (0‑based index)
Forms2OleControl btn = builder.insertForms2OleControl();
btn.setName("btnThirdParagraph");
btn.setCaption("Click Me");
```

### テーブルセル内にボタンを挿入する方法は？

```java
Table table = builder.startTable();
builder.insertCell();
builder.insertCell();
builder.endTable();

builder.moveToCell(0, 0, 0, 0, true); // first row, first cell
Forms2OleControl cellBtn = builder.insertForms2OleControl();
cellBtn.setCaption("Cell Button");
```

### より大きなボタンが必要な場合は？

```java
cmdBtn.setWidth(100);   // width in points
cmdBtn.setHeight(30);   // height in points
```

### 別の言語（例: C#）で **コマンドボタンの文字列を挿入** する方法は？

同じロジックが適用されます。Java の構文を C# の同等コードに置き換えてください：

```csharp
Document doc = new Document("input.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
Forms2OleControl btn = builder.InsertForms2OleControl();
btn.Name = "cmdSubmit";
btn.Caption = "Submit";
doc.Save("output.docx");
```

## プロのコツと落とし穴

- **Pro tip:** ドキュメントの最後にボタンを挿入したい場合は、必ず `builder.moveToDocumentEnd()` を呼び出してください。  
- **Watch out for:** 開いたファイルと同じ場所に保存すると、例外が発生した際にドキュメントが破損する可能性があります。示したように別の出力パスを使用してください。  
- **Compatibility:** レガシーな Forms2.0 ボタンは Word 2007‑2021 で動作します。Web 版 Word ではコンテンツコントロールの使用を検討してください。  
- **Performance:** 非常に大きなドキュメント（>100 MB）をロードすると大量のメモリを消費する可能性があります。`Document.load(InputStream, LoadOptions)` と `LoadOptions.setLoadFormat(LoadFormat.DOCX)` を使用してリソース使用量を抑えてください。

## 完全な動作例

以下は完全な、すぐに実行できる Java プログラムです。`WordButtonDemo.java` というクラスにコピーし、ファイルパスを調整してから `mvn compile exec:java` を実行してください。

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Create a builder positioned at the start
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a command button (Forms2OleControl)
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();

        // 4. Set button properties – this is where we **set command button name**
        cmdBtn.setName("cmdSubmit");   // internal identifier
        cmdBtn.setCaption("Submit");   // visible text (creates form button word)

        // 5. Save the edited document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

プログラムを実行し、`output.docx` を開いてボタンが期待通りに表示されていることを確認してください。

## 結論

これで、Aspose.Words for Java を使用して **プログラムで Word 文書を編集** し、**コマンドボタンの文字列を挿入**、**フォームボタンの文字列を作成**、そして **コマンドボタン名を設定** する方法が分かりました。このアプローチにより手動編集が不要になり、フォームのバッチ処理が可能となり、自動化ワークフローとシームレスに統合できます。

次に検討できること：

- ボタンに VBA マクロを追加する（`cmdBtn.getOleFormat().setMacroName("MyMacro")`）  
- **コンテンツコントロール** を使用して、よりリッチなフォーム体験を提供する（`builder.insertCheckBox()` など）  
- ループを使って複数の文書に対して一括挿入を自動化する  

ボタンのサイズ、位置、イベント処理を自由に試して、シナリオに合わせて調整してください。ハッピーコーディング！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした、密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Word 文書にプログラムでコマンドボタンを追加する方法](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [プログラムで Word 文書を作成し、ActiveX ボタンを追加する](/words/english/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/)
- [Aspose.Words を使用した Word 文書へのコマンドボタン追加 – 完全ガイド](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}