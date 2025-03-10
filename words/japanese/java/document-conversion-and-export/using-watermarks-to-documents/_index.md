---
title: Aspose.Words for Java でドキュメントに透かしを使用する
linktitle: 文書に透かしを使用する
second_title: Aspose.Words Java ドキュメント処理 API
description: Aspose.Words for Java でドキュメントに透かしを追加する方法を学びます。テキストと画像の透かしをカスタマイズして、プロフェッショナルな外観のドキュメントを作成します。
weight: 15
url: /ja/java/document-conversion-and-export/using-watermarks-to-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でドキュメントに透かしを使用する


## Aspose.Words for Java でドキュメントに透かしを追加する方法の紹介

このチュートリアルでは、Aspose.Words for Java API を使用してドキュメントに透かしを追加する方法について説明します。透かしは、ドキュメントにテキストやグラフィックのラベルを付けて、そのステータス、機密性、その他の関連情報を示す便利な方法です。このガイドでは、テキスト透かしとイメージ透かしの両方について説明します。

## Aspose.Words for Java の設定

ドキュメントに透かしを追加する前に、Aspose.Words for Java を設定する必要があります。開始するには、次の手順に従ってください。

1.  Aspose.Words for Javaをダウンロード[ここ](https://releases.aspose.com/words/java/).
2. Aspose.Words for Java ライブラリを Java プロジェクトに追加します。
3. Java コードに必要なクラスをインポートします。

ライブラリの設定が完了したので、透かしの追加に進みましょう。

## テキスト透かしの追加

テキスト透かしは、ドキュメントにテキスト情報を追加するときによく使用されます。Aspose.Words for Java を使用してテキスト透かしを追加する方法は次のとおりです。

```java
//ドキュメントインスタンスを作成する
Document doc = new Document("Document.docx");

//TextWatermarkOptions を定義する
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

//透かしのテキストとオプションを設定する
doc.getWatermark().setText("Test", options);

//透かし付きで文書を保存する
doc.save("DocumentWithWatermark.docx");
```

## 画像に透かしを追加する

テキストの透かしに加えて、画像の透かしをドキュメントに追加することもできます。画像の透かしを追加する方法は次のとおりです。

```java
//ドキュメントインスタンスを作成する
Document doc = new Document("Document.docx");

//透かしの画像を読み込む
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

//透かしのサイズと位置を設定する
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

//文書に透かしを追加する
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

//透かし付きで文書を保存する
doc.save("DocumentWithImageWatermark.docx");
```

## 透かしのカスタマイズ

透かしの外観と位置を調整してカスタマイズできます。テキスト透かしの場合は、フォント、サイズ、色、レイアウトを変更できます。画像透かしの場合は、前の例で示したように、サイズと位置を変更できます。

## 透かしの削除

ドキュメントから透かしを削除するには、次のコードを使用できます。

```java
//ドキュメントインスタンスを作成する
Document doc = new Document("DocumentWithWatermark.docx");

//透かしを削除する
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

//透かしなしで文書を保存する
doc.save("DocumentWithoutWatermark.docx");
```


## 結論

このチュートリアルでは、Aspose.Words for Java を使用してドキュメントに透かしを追加する方法を学習しました。テキストまたは画像の透かしを追加する必要がある場合、Aspose.Words にはそれらを効率的にカスタマイズおよび管理するためのツールが用意されています。また、不要になった透かしを削除して、ドキュメントをクリーンかつプロフェッショナルなものにすることもできます。

## よくある質問

### テキスト透かしのフォントを変更するにはどうすればよいですか?

テキスト透かしのフォントを変更するには、`setFontFamily`の財産`TextWatermarkOptions`。 例えば：

```java
options.setFontFamily("Times New Roman");
```

### 1 つのドキュメントに複数の透かしを追加できますか?

はい、複数の透かしを作成することで、ドキュメントに複数の透かしを追加できます。`Shape`異なる設定のオブジェクトを作成してドキュメントに追加します。

### 透かしを回転させることも可能ですか?

はい、設定することで透かしを回転させることができます。`setRotation`の財産`Shape`オブジェクト。正の値は透かしを時計回りに回転し、負の値は反時計回りに回転します。

### 透かしを半透明にするにはどうすればいいですか?

透かしを半透明にするには、`setSemitransparent`財産に`true`の`TextWatermarkOptions`.

### ドキュメントの特定のセクションに透かしを追加できますか?

はい、セクションを反復処理し、目的のセクションに透かしを追加することで、ドキュメントの特定のセクションに透かしを追加できます。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
