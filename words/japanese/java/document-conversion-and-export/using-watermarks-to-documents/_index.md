---
date: 2025-12-18
description: Aspose.Words for Java を使用して文書に透かしを追加する方法を学びます。画像透かしの例、透かしの色の変更、透かしの透明度の設定、透かしの削除が含まれます。
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java を使用してドキュメントに透かしを追加する方法
url: /ja/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java を使用してドキュメントに透かしを追加する方法

## Aspose.Words for Java におけるドキュメントへの透かし追加の概要

このチュートリアルでは、Aspose.Words for Java を使用して Word ドキュメントに **透かしを追加する方法** を学びます。透かしは、ファイルを機密、ドラフト、承認済みなどとラベル付けする簡単な手段で、テキストベースまたは画像ベースのものがあります。ライブラリの設定、テキストおよび画像透かしの作成、外観のカスタマイズ（透かしの色変更や透過度設定を含む）、そして不要になった透かしの削除までを順に解説します。

## 簡単な回答
- **透かしとは何ですか？** メインコンテンツの背後に表示される半透明のオーバーレイ（テキストまたは画像）です。  
- **複数の透かしを追加できますか？** はい – 複数の `Shape` オブジェクトを作成し、目的のセクションにそれぞれ追加します。  
- **透かしの色はどう変更しますか？** `TextWatermarkOptions` の `Color` プロパティを調整します。  
- **画像透かしの例はありますか？** 下記「画像透かしの追加」セクションをご覧ください。  
- **透かしを削除するのにライセンスは必要ですか？** 本番環境で使用する場合は有効な Aspose.Words ライセンスが必要です。

## Aspose.Words for Java の設定

ドキュメントに透かしを追加する前に、Aspose.Words for Java を設定する必要があります。以下の手順に従ってください。

1. Aspose.Words for Java を [こちら](https://releases.aspose.com/words/java/) からダウンロードします。  
2. ダウンロードした Aspose.Words for Java ライブラリを Java プロジェクトに追加します。  
3. Java コードで必要なクラスをインポートします。

ライブラリの設定が完了したら、実際の透かし作成に進みます。

## テキスト透かしの追加

テキスト透かしは、ドキュメントに文字情報を付加したいときの一般的な選択肢です。以下に Aspose.Words for Java を使用したテキスト透かしの追加方法を示します。

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Define TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Set the watermark text and options
doc.getWatermark().setText("Test", options);

// Save the document with the watermark
doc.save("DocumentWithWatermark.docx");
```

**重要ポイント:** `setFontFamily`、`setFontSize`、`setColor` を調整することで **透かしの色** をブランドに合わせて変更でき、`setSemitransparent(true)` を使用すると **透かしの透明度** を設定して控えめな効果を実現できます。

## 画像透かしの追加

テキスト透かしに加えて、画像透かしもドキュメントに追加できます。以下は PNG ロゴやスタンプを埋め込む **画像透かしの例** です。

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Load the image for the watermark
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Set the watermark size and position
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Add the watermark to the document
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Save the document with the watermark
doc.save("DocumentWithImageWatermark.docx");
```

このブロックを異なる画像や位置で繰り返すことで、1 ファイルに **複数の透かし** を追加できます。

## 透かしのカスタマイズ

透かしは外観や位置を調整してカスタマイズできます。テキスト透かしの場合はフォント、サイズ、色、レイアウトを変更し、画像透かしの場合はサイズ、回転、配置を前述の例のように変更します。

## 透かしの削除

**透かしドキュメント** の内容を削除する必要がある場合、以下のコードがすべてのシェイプを走査し、透かしとして識別されたものを削除します。

```java
// Create a Document instance
Document doc = new Document("DocumentWithWatermark.docx");

// Remove the watermark
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Save the document without the watermark
doc.save("DocumentWithoutWatermark.docx");
```

## 一般的な使用例とヒント

- **機密ドラフト:** 「CONFIDENTIAL」などの半透明テキスト透かしを適用します。  
- **ブランディング:** 会社ロゴを含む画像透かしを使用します。  
- **セクション別透かし:** `doc.getSections()` をループし、選択したセクションにのみ透かしを追加します。  
- **パフォーマンスのヒント:** 同じ透かしを多数のドキュメントに適用する場合は、`TextWatermarkOptions` インスタンスを再利用します。

## よくある質問

### テキスト透かしのフォントはどう変更しますか？

テキスト透かしのフォントを変更するには、`TextWatermarkOptions` の `setFontFamily` プロパティを変更します。例:

```java
options.setFontFamily("Times New Roman");
```

### 1 つのドキュメントに複数の透かしを追加できますか？

はい、異なる設定の `Shape` オブジェクトを複数作成し、ドキュメントに追加することで複数の透かしを設定できます。

### 透かしを回転させることは可能ですか？

はい、`Shape` オブジェクトの `setRotation` プロパティを設定することで透かしを回転させられます。正の値は時計回り、負の値は反時計回りに回転します。

### 透かしを半透明にするにはどうすればよいですか？

透かしを半透明にするには、`TextWatermarkOptions` の `setSemitransparent` プロパティを `true` に設定します。

### ドキュメントの特定セクションだけに透かしを追加できますか？

はい、セクションを走査し、目的のセクションにのみ透かしを追加することで実現できます。

---

**最終更新日:** 2025-12-18  
**テスト環境:** Aspose.Words for Java 24.12  
**作者:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}