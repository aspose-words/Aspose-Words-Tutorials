---
category: general
date: 2026-09-18
description: Javaで空白の文書を作成し、ActiveXボタンを追加します。コマンドボタンの挿入方法、インタラクティブなフォームの構築方法、Word文書の保存方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- create interactive form
- add activex button
- how to insert command button
- create word document
language: ja
lastmod: 2026-09-18
og_description: Javaで空白の文書を作成し、ActiveXコマンドボタンを埋め込みます。このステップバイステップガイドに従ってインタラクティブなフォームを作成し、Wordファイルを保存してください。
og_image_alt: Screenshot of a Word document showing a clickable ActiveX command button
og_title: Wordでインタラクティブなコマンドボタンを備えた空白文書を作成
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  headline: Create blank document with an interactive command button in Word using
    Java
  type: TechArticle
- description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  name: Create blank document with an interactive command button in Word using Java
  steps:
  - name: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
    text: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
  - name: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
    text: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
  - name: Insert the button as shown in Step 3.
    text: Insert the button as shown in Step 3.
  - name: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
    text: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Java を使って Word でインタラクティブなコマンドボタン付きの空白文書を作成する
url: /ja/java/document-manipulation/create-blank-document-with-an-interactive-command-button-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java を使用して Word にインタラクティブなコマンド ボタンを持つ空白ドキュメントを作成する

**空白ドキュメント**にクリック可能なボタンを埋め込みたい場合は、この記事で Aspose.Words for Java を使った手順をすべて解説します。インタラクティブなフォームの作成、ActiveX ボタンの追加、そして Word ファイルの保存まで、簡潔なステップで学べます。

コマンド ボタンを埋め込むことで、静的な .docx が Microsoft Word 内で直接操作できる機能的なフォームに変わります。本チュートリアルでは **コマンド ボタンの挿入方法**、一般的な落とし穴の対処、さらに複雑なフォームへの拡張方法もカバーしています。

## 前提条件

開始する前に、以下が揃っていることを確認してください。

* Java 17 以降（コードは JDK 17+ でコンパイル可能）
* Aspose.Words for Java 23.9 以上 – `Document`、`DocumentBuilder`、`Forms2OleControl` を提供
* Aspose.Words の依存関係を追加できる IDE またはビルドツール（Maven/Gradle）
* Java の基本構文と Word ドキュメントの概念に関する基礎知識

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## 手順 1: 空白ドキュメントを作成する

最初の操作は新しい `Document` オブジェクトをインスタンス化することです。このオブジェクトは、コンテンツを追加できる空の Word ファイルを表します。

```java
// Step 1: Create a new blank document
Document doc = new Document();
```

空白ドキュメントを作成すると、**プログラムで Word ドキュメントを作成**する際に、既存のテンプレートがなくてもクリーンなキャンバスが得られます。

## 手順 2: DocumentBuilder を初期化する

`DocumentBuilder` はテキスト、テーブル、フォーム コントロールを追加するための主要クラスです。先ほど作成した `Document` に対して動作します。

```java
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);
```

ビルダーは現在の挿入位置を保持するため、以降のコマンドはファイル内の正しい場所に影響を与えます。

## 手順 3: Forms2Ole コマンド ボタン コントロールを挿入する

Aspose.Words は ActiveX コントロール用に `Forms2OleControl` クラスを提供しています。**ActiveX ボタンを追加**するには、ビルダーから `COMMANDBUTTON` タイプを要求します。

```java
// Step 3: Insert a Forms2Ole command button control
Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);
```

`insertForms2OleControl` メソッドは、ビルダーの現在のカーソル位置にコントロールを挿入します。コントロールは ActiveX オブジェクトであるため、デスクトップ版 Microsoft Word でのみ動作し、Word Online では機能しません。

## 手順 4: ボタンの外観と位置を設定する

コントロールのセッターを使って、ボタンのキャプション、サイズ、位置を設定できます。位置はポイント単位で測定されます（1 ポイント = 1/72 インチ）。

```java
// Step 4: Configure the button's appearance and position
commandButton.setCaption("Click Me");   // Text shown on the button
commandButton.setTop(100);              // Distance from the top edge of the page (points)
commandButton.setLeft(100);             // Distance from the left edge of the page (points)
commandButton.setWidth(120);            // Optional: set button width
commandButton.setHeight(30);            // Optional: set button height
```

*なぜこれらのプロパティを設定するのか？* `Top` と `Left` を設定すると、ページ上の期待通りの位置にボタンが表示されます。`Caption` はユーザーに見えるラベルを定義します。幅・高さを省略すると、Word がデフォルトのサイズを割り当てますが、デザインと合わないことがあります。

### プロ・ティップ
複数のコントロールを追加する場合は、各挿入前に `builder.moveToDocumentEnd()` を呼び出して、オブジェクトが重ならないようにしてください。

## 手順 5: 埋め込みコマンド ボタン付きドキュメントを保存する

最後に、ドキュメントをディスクに書き出します。拡張子は `.docx`（古いバージョン向けは `.doc`）である必要があり、ActiveX コントロールが保持されます。

```java
// Step 5: Save the document with the embedded command button
String outputPath = "C:/temp/CommandButton.docx";
doc.save(outputPath);
System.out.println("Document saved to: " + outputPath);
```

Microsoft Word で `CommandButton.docx` を開くと、**Click Me** とラベル付けされたボタンが表示されます。クリックしてもデフォルトでは何も起こりませんが、後からマクロや VBA スクリプトを割り当ててカスタム動作を実装できます。

## 既存フォームにコマンド ボタンを挿入する方法（オプション）

すでにテキスト フィールドを持つフォームがあり、**インタラクティブなフォーム**にボタンを組み込みたい場合は、以下の手順を追加で実行します。

1. 既存ドキュメントを読み込む: `Document doc = new Document("ExistingForm.docx");`
2. ビルダーを目的の位置へ移動: `builder.moveToParagraph(5, 0); // 6 行目の最初のノード`
3. 手順 3 と同様にボタンを挿入
4. パラグラフのレイアウトに合わせてボタンの `Top`/`Left` を調整

この手順により、テンプレート全体を作り直すことなく、任意の既存 Word テンプレートに ActiveX ボタンを追加できます。

## エッジケースとトラブルシューティング

| 状況 | 確認すべきこと | 推奨される対処 |
|-----------|---------------|-----------------|
| ボタンが Word に表示されない | デスクトップ版 Word で開いているか確認（Word Online は ActiveX を除去） | Word 2016 以降のデスクトップ版で開く |
| キャプションが切れる | ボタン幅がテキストを収めるだけの大きさか確認 | `setWidth` を増やしてキャプションが収まるまで調整 |
| 保存時に `IOException` がスローされる | 出力ディレクトリが存在し、書き込み権限があるか確認 | ディレクトリを作成するか、管理者権限で実行 |
| 複数ボタンが重なる | 前回挿入後にビルダーのカーソルが移動していない可能性 | 各新しいコントロール挿入前に `builder.moveToDocumentEnd()` を呼び出す |

## 完全な実行可能サンプル

以下は、コピーしてコンパイル・実行できる完全な Java プログラムです。**空白ドキュメントの作成**、**ActiveX ボタンの追加**、**Word ドキュメントの保存**を一連の流れで示しています。

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) {
        try {
            // 1. Create a new blank document
            Document doc = new Document();

            // 2. Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Insert an ActiveX command button
            Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);

            // 4. Configure button properties
            commandButton.setCaption("Click Me");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(100);  // points from left
            commandButton.setWidth(120);
            commandButton.setHeight(30);

            // 5. Save the document
            String outPath = "CommandButton.docx";
            doc.save(outPath);
            System.out.println("Document created: " + outPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**期待される出力**

```
Document created: CommandButton.docx
```

`CommandButton.docx` を開くと、上端と左端からそれぞれ 100 pt の位置に **Click Me** とラベル付けされたボタンが 1 ページだけ表示されます。

## 結論

これで **空白ドキュメントを作成**し、**ActiveX ボタンを埋め込む**方法、そして単なる Word ファイルを **インタラクティブなフォーム**に変換する手順が身につきました。**コマンド ボタンの挿入方法**をマスターすれば、チェックボックスやコンボ ボックス、さらにはカスタム VBA ロジックまで拡張できます。

次に検討すべき関連トピック:

* **Create interactive form** with text fields (`builder.insertField`)  
* **Add activex button** that runs a VBA macro (`builder.insertOleObject`)  
* **Create word document** from a template using `Document(docTemplatePath)`  
* ボタンを保持したまま .docx を PDF に変換（PDF ではボタンは静的画像として表示されます）

ボタンのサイズ、位置、キャプションを自由に調整して UI デザインに合わせてみてください。ハッピーコーディング！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、別の実装アプローチを探求したりするのに役立ちます。

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create Vba Project in Word Document](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Create New Word Document](/words/english/net/add-content-using-documentbuilder/create-new-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}