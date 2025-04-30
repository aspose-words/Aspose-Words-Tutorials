---
"description": "Aspose.Words for Java でドキュメントに透かしを追加する方法を学びましょう。テキストや画像の透かしをカスタマイズして、プロフェッショナルなドキュメントを作成できます。"
"linktitle": "文書への透かしの使用"
"second_title": "Aspose.Words Java ドキュメント処理 API"
"title": "Aspose.Words for Java でドキュメントに透かしを追加する"
"url": "/ja/java/document-conversion-and-export/using-watermarks-to-documents/"
"weight": 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でドキュメントに透かしを追加する


## Aspose.Words for Java でドキュメントに透かしを追加する方法の紹介

このチュートリアルでは、Aspose.Words for Java API を使用してドキュメントに透かしを追加する方法を説明します。透かしは、ドキュメントのステータス、機密性、その他の関連情報をテキストやグラフィックでラベル付けする便利な方法です。このガイドでは、テキストと画像の両方の透かしについて説明します。

## Aspose.Words for Java の設定

ドキュメントに透かしを追加する前に、Aspose.Words for Java をセットアップする必要があります。以下の手順に従ってください。

1. Aspose.Words for Javaをダウンロード [ここ](https://releases。aspose.com/words/java/).
2. Aspose.Words for Java ライブラリを Java プロジェクトに追加します。
3. Java コードに必要なクラスをインポートします。

ライブラリの設定が完了したので、透かしの追加に進みます。

## テキスト透かしの追加

テキスト透かしは、ドキュメントにテキスト情報を追加したい場合によく使用されます。Aspose.Words for Java を使用してテキスト透かしを追加する方法は次のとおりです。

```java
// ドキュメントインスタンスを作成する
Document doc = new Document("Document.docx");

// TextWatermarkOptionsを定義する
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// 透かしのテキストとオプションを設定する
doc.getWatermark().setText("Test", options);

// 透かし入りの文書を保存する
doc.save("DocumentWithWatermark.docx");
```

## 画像透かしの追加

テキスト透かしに加えて、画像透かしもドキュメントに追加できます。画像透かしを追加する方法は次のとおりです。

```java
// ドキュメントインスタンスを作成する
Document doc = new Document("Document.docx");

// 透かしの画像を読み込む
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// 透かしのサイズと位置を設定する
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// 文書に透かしを追加する
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// 透かし入りの文書を保存する
doc.save("DocumentWithImageWatermark.docx");
```

## 透かしのカスタマイズ

透かしの外観と位置を調整することでカスタマイズできます。テキスト透かしの場合は、フォント、サイズ、色、レイアウトを変更できます。画像透かしの場合は、前の例で示したように、サイズと位置を変更できます。

## 透かしの削除

ドキュメントから透かしを削除するには、次のコードを使用できます。

```java
// ドキュメントインスタンスを作成する
Document doc = new Document("DocumentWithWatermark.docx");

// 透かしを削除する
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// 透かしなしで文書を保存する
doc.save("DocumentWithoutWatermark.docx");
```


## 結論

このチュートリアルでは、Aspose.Words for Java を使用してドキュメントに透かしを追加する方法を学習しました。テキストまたは画像の透かしを追加する必要がある場合でも、Aspose.Words はそれらを効率的にカスタマイズおよび管理するためのツールを提供します。また、不要になった透かしを削除することで、ドキュメントをすっきりとプロフェッショナルな仕上がりにすることができます。

## よくある質問

### テキスト透かしのフォントを変更するにはどうすればよいですか?

テキスト透かしのフォントを変更するには、 `setFontFamily` の財産 `TextWatermarkOptions`。 例えば：

```java
options.setFontFamily("Times New Roman");
```

### つのドキュメントに複数の透かしを追加できますか?

はい、複数の透かしを作成することで、ドキュメントに複数の透かしを追加できます。 `Shape` 異なる設定のオブジェクトを作成してドキュメントに追加します。

### 透かしを回転させることってできますか？

はい、設定することで透かしを回転させることができます。 `setRotation` の財産 `Shape` オブジェクト。正の値は透かしを時計回りに回転し、負の値は反時計回りに回転します。

### 透かしを半透明にするにはどうすればいいでしょうか?

透かしを半透明にするには、 `setSemitransparent` 財産に `true` の中で `TextWatermarkOptions`。

### ドキュメントの特定のセクションに透かしを追加できますか?

はい、セクションを反復処理し、目的のセクションに透かしを追加することで、ドキュメントの特定のセクションに透かしを追加できます。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}