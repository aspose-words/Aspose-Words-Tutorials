---
category: general
date: 2026-07-26
description: Aspose.Words を使用して Word 文書に ActiveX ボタンを挿入する方法 – 数行でボタンのキャプション、位置、サイズを設定する方法を学べます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert activex
- set button caption
language: ja
lastmod: 2026-07-26
og_description: Aspose.Words を使用して Word 文書に ActiveX ボタンを挿入する方法。ボタンのキャプション、位置、サイズを設定するステップバイステップのチュートリアルをご覧ください。
og_image_alt: Screenshot of a Word document showing an inserted ActiveX CommandButton
  with a custom caption
og_title: WordでActiveXボタンを挿入する方法 – クイックガイド
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: How to insert ActiveX button in a Word document using Aspose.Words
    – learn to set button caption, position, and size in just a few lines.
  headline: How to Insert ActiveX Button in Word – Set Button Caption
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- Document generation
title: WordにActiveXボタンを挿入する方法 – ボタンのキャプションを設定する
url: /ja/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word に ActiveX ボタンを挿入する方法 – ボタンのキャプションを設定する

UI を開かずに **ActiveX** コントロールを Word ファイルに挿入する方法を考えたことはありますか？ あなただけではありません。多くのエンタープライズ アプリでは、マクロを実行するクリック可能なボタンが必要で、プログラムで行うことで何時間も節約できます。このガイドでは、Aspose.Words for Java を使用して **ActiveX** CommandButton を挿入する方法、そしてユーザーが何をクリックすべきか分かるように **ボタンのキャプションを設定する** 方法を詳しく解説します。

ライブラリの設定、ドキュメントの作成、ボタンの配置、サイズと位置の調整、キャプションの設定、そして最終的な保存までの全工程を順に説明します。最後には、Word で開くと完全に機能する ActiveX ボタンが配置された `.docx` が生成され、マクロを発火させる準備が整います。

---

## 学べること

- Java プロジェクトに Aspose.Words をインストールして参照する方法  
- 新しい `Document` と `DocumentBuilder` を作成する方法  
- **ActiveX** CommandButton コントロールをワンライナーで挿入する方法  
- **ボタンのキャプション** を設定し、位置とサイズを調整する方法  
- ドキュメントを保存し、Word で結果を確認する方法  

ActiveX の事前知識は不要です。基本的な Java の知識と Aspose.Words のコピーさえあれば始められます。

---

## 前提条件

- Java 8 以上がインストールされていること  
- 依存関係管理に Maven または Gradle を使用（Maven の例を示します）  
- **Aspose.Words for Java** のライセンス版または評価版（無料トライアルでデモは実行可能）  
- 生成されたファイルをテストするための Microsoft Word（最新バージョン可）

---

## 手順 1: Aspose.Words をプロジェクトに設定する

まずは Aspose.Words の依存関係を追加します。Maven を使用している場合は、`pom.xml` に以下を追加してください。

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for the latest version -->
</dependency>
```

Gradle を使用する場合は次のように追加します。

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

`mvn clean install`（または `gradle build`）を実行すればライブラリがクラスパスに追加され、コーディングの準備が整います。

---

## 手順 2: 新しいドキュメントとビルダーを作成する

`Document` は Word ファイル全体を表し、`DocumentBuilder` はその内容を編集するためのツールです。ビルダーは新しいキャンバスに描くペンのようなものです。

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();                 // creates an empty .docx
        DocumentBuilder builder = new DocumentBuilder(doc);
```

なぜ空のドキュメントから始めるのか？ それにより追加するすべての要素を完全にコントロールでき、後から予期せぬ書式が混入する心配がなくなります。

---

## 手順 3: ActiveX CommandButton コントロールを挿入する

本題です。Aspose.Words の `insertForms2OleControl` メソッドを使うと、任意の ActiveX コントロールを配置できます。ここでは **CommandButton** を指定します。

```java
        // Step 3: Insert a CommandButton ActiveX control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

このメソッドは `Forms2OleControl` オブジェクトを返し、ボタンのプロパティにプログラムからアクセスできます。これが **how to insert activex** がワンライナーになるポイントです。低レベルの COM API をいじる必要はありません。

---

## 手順 4: 位置・サイズを設定し、ボタンのキャプションを設定する

ページ中央に浮かんでいるだけのボタンは実用的ではありません。ユーザーが期待する位置に配置し、適切なサイズにし、そして最も重要な **ボタンのキャプション** を設定して何をするボタンかを明示します。

```java
        // Step 4a: Position the button (coordinates are in points)
        commandBtn.setLeft(100);   // distance from the left margin
        commandBtn.setTop(150);    // distance from the top margin

        // Step 4b: Define width and height
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Step 4c: Set the button caption (the text that appears on the button)
        commandBtn.setCaption("Click Me");
```

**なぜこの数値か？** Word はポイント単位（1 pt ≈ 1/72 インチ）を使用します。`100 pt` は左端から約 1.4 インチ、`150 pt` は上端から約 2.1 インチで、標準的な A4 用紙のほぼ中央に相当します。レイアウトに合わせて調整してください。

キャプションの設定は必須です。設定しなければボタンは空白の矩形に見えてしまいます。`setCaption` メソッドは任意の文字列を受け取るので、必要に応じて後からローカライズも可能です。

---

## 手順 5: ドキュメントを保存する

最後にドキュメントをディスクに書き出します。保存先フォルダーは任意ですが、パスが存在することを確認してください。

```java
        // Step 5: Save the document to a .docx file
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

`ActiveXButton.docx` を Word で開くと、**「Click Me」** とラベル付けされたボタンが適切に配置されているはずです。ダブルクリックすると、Word はマクロの有効化を促します（ActiveX コントロールはマクロ有効と見なされます）。その後、VBA の `Click` イベントにマクロを割り当てることができます。

---

## 見落としがちなケースとヒント

- **マクロ有効形式**: 標準の `.docx` では ActiveX コントロールは無効化されます。ボタンをすぐに使用できるようにしたい場合は、`doc.save(outputPath, SaveFormat.DOCM);` を使って `.docm`（マクロ有効）として保存してください。  
- **互換性**: Word 2007 以前のバージョンはバイナリ形式の `.doc` を使用します。Aspose.Words はこの形式でも保存可能ですが、コントロールのプロパティが若干異なる場合があります。  
- **セキュリティ設定**: 一部の企業環境では ActiveX がロックダウンされています。ボタンが表示されない場合は、Word の「信頼センター」→「ActiveX 設定」を確認してください。  
- **複数ボタン**: 複数設置したい場合は `insertForms2OleControl` 呼び出しを繰り返し、各ボタンの `Left`/`Top` 値を調整します。返されたオブジェクトを保持しておけば、個別にキャプションを設定できます。  
- **キャプションのスタイリング**: キャプションはデフォルトフォントを継承します。フォントやスタイルを変更したい場合は、内部 XML を編集するか、挿入後に Word スタイルを適用する必要があります（`ParagraphFormat` API を使用）。このガイドの範囲を超えますが、Aspose.Words でも実現可能です。

---

## 完全動作サンプル

以下はそのまま実行可能な Java クラスです。IDE に貼り付け、出力パスを調整して **Run** をクリックしてください。

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Position the button (points from the left/top margins)
        commandBtn.setLeft(100);
        commandBtn.setTop(150);

        // Set size (width × height in points)
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Set the button caption – this is the visible text
        commandBtn.setCaption("Click Me");

        // Save the document; you may also use SaveFormat.DOCM for macro‑enabled files
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

**期待される出力**: 実行後、コンソールに保存先が表示されます。生成されたファイルを Word で開くと、ページ中央付近に「Click Me」と表示されたボタンが配置されています。クリックすると標準の ActiveX クリックイベントが発火します（実際に動作させるには VBA マクロを割り当てる必要があります）。

---

## まとめ

これで **ActiveX** CommandButton コントロールを Aspose.Words を使ってプログラム的に Word 文書に挿入し、**ボタンのキャプション** を設定、位置やサイズを調整する方法が習得できました。この手法により手作業の UI 作業が不要になり、レポート自動生成プロセスにシームレスに組み込めます。

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれているので、API の追加機能をマスターしたり、別の実装アプローチを自分のプロジェクトに取り入れたりする際に役立ちます。

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Insert an Image into Word Document Header | Aspose.Words for .NET](/words/english/net/header-footer-formatting/insert-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}