---
category: general
date: 2026-11-22
description: Aspose.Words for Java を使用して Word に図形を追加する方法を学びましょう – 四角形を挿入し、プログラムで非表示にします。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shape to word
- how to insert shape
- how to hide shape
- hide shape in word
language: ja
lastmod: 2026-11-22
og_description: Aspose.Words for Java を使用して Word に図形を追加します。このチュートリアルでは、長方形を挿入し、図形を非表示にし、ドキュメントを保存する方法を示します。
og_image_alt: Screenshot of Java code that adds and hides a shape in a Word document
og_title: Aspose.Words を使用して Word に図形を追加する – Java ガイド
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  headline: How to add shape to Word documents with Aspose.Words for Java
  type: TechArticle
- description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  name: How to add shape to Word documents with Aspose.Words for Java
  steps:
  - name: Expected output
    text: '* The file `output.docx` opens without any visible shapes. * If you inspect
      the document with Aspose.Words (e.g., `doc.getChildNodes(NodeType.SHAPE, true).size()`),
      the shape count will be **1**, confirming that the shape exists but is hidden.'
  - name: 1. Creating a shape in a fresh document
    text: 'If you start from scratch, replace the load line with:'
  - name: 2. Positioning the shape precisely
    text: 'By default, `insertShape` places the shape at the current cursor location.
      To position it absolutely:'
  - name: 3. Controlling visibility per output format
    text: 'If you need the shape visible in the Word UI but hidden when exporting
      to PDF, use `Shape.setWrapType(WrapType.NONE)` together with `Hidden`:'
  - name: 4. Adding text inside the shape
    text: 'A rectangle can contain a text frame:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: Aspose.Words for Java を使用して Word 文書に図形を追加する方法
url: /ja/java/images-shapes/how-to-add-shape-to-word-documents-with-aspose-words-for-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java を使用して Word ドキュメントにシェイプを追加する方法

プログラムで **Word にシェイプを追加** する必要がある場合、Aspose.Words for Java を使えば簡単です。このガイドでは **シェイプの挿入方法**、可視性の制御、そして **シェイプの非表示方法** を学び、最終的なファイルが期待通りになるようにします。

既存の `.docx` を読み込み、長方形を挿入し、非表示にして結果を保存する、完全な実行可能サンプルを順に確認できます。外部スクリプトや手動ステップは不要で、チュートリアルでは新規ドキュメントの作成や印刷時のみシェイプを非表示にするなどの一般的なバリエーションも取り上げています。

## Prerequisites

開始する前に、以下が揃っていることを確認してください。

* Java 17（またはそれ以降） – 以前のバージョンでも動作しますが、最新の LTS がパフォーマンス面で優れています。  
* Maven 3.8+ – 依存関係管理に使用します。  
* 有効な Aspose.Words for Java ライセンス（学習目的であれば無料評価版で可）。  
* お好みの IDE またはテキストエディタ（例：IntelliJ IDEA、VS Code）。

## Step 1: Add Aspose.Words to your Maven project

`pom.xml` に以下の依存関係を追加します。これにより（2026年11月時点の）最新安定版が取得されます。

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

> **プロのヒント:** JAR を独自のライセンスロジックと共に配布する場合は、`<scope>provided</scope>` を使用してください。

## Add shape to Word – initializing the document

最初の実装ステップは `Document` オブジェクトを取得することです。既存ファイルを読み込むか、新規に作成できます。

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document (or create a new one)
        Document doc = new Document("input.docx");   // <-- replace with your path
        // If you prefer a blank document, use:
        // Document doc = new Document();
```

*Why this matters*: `Document` クラスはすべての Word 操作のエントリーポイントです。既存ファイルを読み込むとスタイルやヘッダー・フッターが保持され、新規ドキュメントはクリーンな状態から開始できます。

## How to insert shape in a Word document

次に `DocumentBuilder` を作成し、ドキュメントのコンテンツを変更します。ビルダーはテキスト、テーブル、そして **シェイプ** の挿入メソッドを提供します。

```java
        // Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape with a width of 100 points and height of 50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
```

`insertShape` 呼び出しは `Shape` オブジェクトを返し、色・枠線・テキストなどをさらに設定できます。サイズはポイント単位で指定します（1 pt = 1/72 in）。

*Why you might use a rectangle*: 長方形は注釈、透かし、プレースホルダーの最も一般的なコンテナです。`ShapeType.RECTANGLE` を `ShapeType.ELLIPSE`、`ShapeType.LINE` などに置き換えて、さまざまなビジュアル要件に対応できます。

## How to hide shape in Word

レイアウト計算のためにシェイプは必要だが、最終的な表示には出したくない場合があります。Aspose.Words では `setHidden(true)` メソッドでこれを実現できます。

```java
        // Hide the shape so it does not appear when the document is opened
        rectangle.setHidden(true);
```

非表示フラグは Microsoft Word の **Hidden** 書式オプションと同様に機能し、シェイプはビジュアルレイアウトから除外されますが、ドキュメントのオブジェクトモデルには残ります。以下のようなケースで便利です。

* 後でアプリケーションが読み取るメタデータやマーカーを保存する。  
* 公開直前に削除するプレースホルダーを作成する。  
* 出力形式ごとに可視性を制御する（例：HTML では非表示、PDF では表示）。

> **注意:** デフォルトでは非表示シェイプも PDF にエクスポートされます。PDF からも除外したい場合は `rectangle.getWrapType() = WrapType.NONE` を設定し、`Hidden` プロパティを適切に調整してください。

## Step 4: Save the modified document

変更を新しいファイルに保存します。

```java
        // Save the document with the hidden rectangle
        doc.save("output.docx");   // <-- replace with your desired output path
    }
}
```

`output.docx` を Microsoft Word で開くと、長方形は表示されませんが、ドキュメントツリーの一部として残っています。`Shape.isHidden()` を確認すれば、プログラム上でも存在を検証できます。

### Expected output

* ファイル `output.docx` を開いても、目に見えるシェイプはありません。  
* Aspose.Words で `doc.getChildNodes(NodeType.SHAPE, true).size()` を実行するとシェイプ数は **1** となり、シェイプが存在するが非表示であることが確認できます。

## Advanced variations and edge cases

### 1. Creating a shape in a fresh document

最初から作成する場合は、ロード行を次のように置き換えます。

```java
Document doc = new Document();          // creates an empty Word file
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Report Title");        // add a title before the shape
```

### 2. Positioning the shape precisely

デフォルトでは `insertShape` が現在のカーソル位置にシェイプを配置します。絶対位置に設定するには次を使用します。

```java
rectangle.setLeft(72);   // 1 inch from the left margin
rectangle.setTop(144);   // 2 inches from the top of the page
rectangle.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangle.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
```

### 3. Controlling visibility per output format

Word UI ではシェイプを表示しつつ、PDF へエクスポートする際に非表示にしたい場合は、`Shape.setWrapType(WrapType.NONE)` と `Hidden` を組み合わせます。

```java
rectangle.setHidden(false);                 // visible in Word
rectangle.getParagraph().getParagraphFormat()
        .setPageBreakBefore(true);          // ensure it stays on its own line
// When converting to PDF, hide it programmatically:
if (exportingToPdf) {
    rectangle.setHidden(true);
}
```

### 4. Adding text inside the shape

長方形はテキストフレームを含めることができます。

```java
Shape textBox = builder.insertShape(ShapeType.TEXT_BOX, 200, 50);
textBox.getTextBox().setInternalMarginLeft(5);
textBox.getTextBox().setInternalMarginTop(5);
builder.moveTo(textBox.getFirstParagraph());
builder.write("Confidential");
```

同じ `setHidden(true)` 呼び出しでテキストボックス全体を非表示にできます。

## Common pitfalls and how to avoid them

| 症状 | 原因 | 対策 |
|------|------|------|
| `setHidden(true)` を設定した後でもシェイプが表示される | シェイプの非表示フラグを設定する前にドキュメントが保存されました | `setHidden(true)` を **doc.save()** の **前に** 呼び出すことを確認してください |
| シェイプのサイズが歪んで見える | 高 DPI 画面でポイントとピクセルが混同されている | プラットフォーム間で一貫したサイズにするため、ポイント (72 pt = 1 in) を使用してください |
| 非表示シェイプが印刷されてしまう | 一部のプリンターは非表示フラグを無視します | `Shape.setWrapType(WrapType.NONE)` を設定し、さらに `Shape.getParagraph().getParagraphFormat().setPageBreakBefore(false)` をクリアしてください |

## Conclusion

これで **Word にシェイプを追加** し、**シェイプを挿入** し、**シェイプを非表示** にしてエンドユーザーからは見えないがドキュメント構造には残る方法が分かりました。上記の完全なサンプルはファイルを読み込み、長方形を挿入し、非表示にして保存する流れを示し、典型的なユースケースといくつかのエッジケースを網羅しています。

ここからは、カスタム塗りつぶし色でシェイプを挿入する方法や、条件付き印刷のためにシェイプを非表示にする方法、Aspose.Words を使った大量ドキュメントの自動処理など、関連トピックを探求できます。`ShapeType` の値や位置指定オプション、可視性フラグを組み合わせて、あなたのワークフローに最適な実装を試してみてください。

Happy coding, and enjoy the flexibility that programmatic Word manipulation brings to your Java applications!

## What Should You Learn Next?

以下のチュートリアルは、本ガイドで示したテクニックを基にした、密接に関連するトピックを扱っています。各リソースには完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得したり、独自プロジェクトで代替実装アプローチを検討したりするのに役立ちます。

- [Aspose.Words を使用して Java でプログラム的に Word ドキュメントを作成し、シェイプを追加・非表示にする](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [Java を使用して Word ドキュメントでシェイプを非表示にする方法](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [空白の .docx Word ドキュメントを作成し、Aspose.Words で非表示の長方形シェイプを追加する](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}