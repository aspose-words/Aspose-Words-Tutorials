---
title: Aspose.Words for Java でのドキュメント シェイプの使用
linktitle: ドキュメントシェイプの使用
second_title: Aspose.Words Java ドキュメント処理 API
description: Aspose.Words for Java のドキュメント シェイプのパワーを解き放ちます。ステップ バイ ステップの例を使用して、視覚的に魅力的なドキュメントを作成する方法を学びます。
weight: 14
url: /ja/java/document-conversion-and-export/using-document-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でのドキュメント シェイプの使用


## Aspose.Words for Java でのドキュメント シェイプの使用の概要

この包括的なガイドでは、Aspose.Words for Java のドキュメント シェイプの世界を詳しく見ていきます。視覚的に魅力的でインタラクティブなドキュメントを作成する場合、シェイプは不可欠な要素です。吹き出し、ボタン、画像、透かしなどを追加する必要がある場合、Aspose.Words for Java にはそれを効率的に行うためのツールが用意されています。ソース コードの例を使用して、これらのシェイプの使用方法を段階的に見ていきましょう。

## ドキュメントシェイプを使い始める

コードに進む前に、環境を設定しましょう。プロジェクトにAspose.Words for Javaが統合されていることを確認してください。まだ統合されていない場合は、AsposeのWebサイトからダウンロードできます。[Aspose.Words for Java をダウンロード](https://releases.aspose.com/words/java/)

## ドキュメントに図形を追加する

### グループシェイプの挿入

あ`GroupShape`複数の図形をグループ化することができます。ここでは、図形を作成して挿入する方法を説明します。`GroupShape`:

```java
Document doc = new Document();
doc.ensureMinimum();

GroupShape groupShape = new GroupShape(doc);
Shape accentBorderShape = new Shape(doc, ShapeType.ACCENT_BORDER_CALLOUT_1);
accentBorderShape.setWidth(100.0);
accentBorderShape.setHeight(100.0);

groupShape.appendChild(accentBorderShape);

Shape actionButtonShape = new Shape(doc, ShapeType.ACTION_BUTTON_BEGINNING);
actionButtonShape.setLeft(100.0);
actionButtonShape.setWidth(100.0);
actionButtonShape.setHeight(200.0);

groupShape.appendChild(actionButtonShape);

groupShape.setWidth(200.0);
groupShape.setHeight(200.0);
groupShape.setCoordSize(new Dimension(200, 200));

DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertNode(groupShape);

doc.save("Your Directory Path" + "WorkingWithShapes.AddGroupShape.docx");
```

### テキストボックス図形の挿入

テキストボックス図形を挿入するには、`insertShape`以下の例に示すように、メソッドを使用します。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertShape(ShapeType.TEXT_BOX, RelativeHorizontalPosition.PAGE, 100.0,
    RelativeVerticalPosition.PAGE, 100.0, 50.0, 50.0, WrapType.NONE);

shape.setRotation(30.0);
builder.writeln();

shape = builder.insertShape(ShapeType.TEXT_BOX, 50.0, 50.0);
shape.setRotation(30.0);

OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);

doc.save("Your Directory Path" + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## 図形のプロパティの操作

### アスペクト比の管理

図形のアスペクト比をロックするかどうかを制御できます。図形のアスペクト比をロック解除する方法は次のとおりです。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

### 表のセルに図形を配置する

テーブル セル内に図形を配置する必要がある場合は、次のコードを使用してこれを実現できます。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

builder.startTable();
builder.getRowFormat().setHeight(100.0);
builder.getRowFormat().setHeightRule(HeightRule.EXACTLY);

for (int i = 0; i < 31; i++) {
    if (i != 0 && i % 7 == 0)
        builder.endRow();

    builder.insertCell();
    builder.write("Cell contents");
}

builder.endTable();

Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.isLayoutInCell(true); //図形をセル内に配置した場合は、表のセルの外側に図形を表示します。
watermark.setWidth(300.0);
watermark.setHeight(70.0);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setRotation(-40);
watermark.setFillColor(Color.GRAY);
watermark.setStrokeColor(Color.GRAY);
watermark.getTextPath().setText("watermarkText");
watermark.getTextPath().setFontFamily("Arial");
watermark.setName("WaterMark_{Guid.NewGuid()}");
watermark.setWrapType(WrapType.NONE);

Run run = (Run) doc.getChildNodes(NodeType.RUN, true).get(doc.getChildNodes(NodeType.RUN, true).getCount() - 1);
builder.moveTo(run);
builder.insertNode(watermark);

doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010);
doc.save("Your Directory Path" + "WorkingWithShapes.LayoutInCell.docx");
```

## SmartArt 図形の操作

### SmartArt 図形の検出

次のコードを使用して、ドキュメント内の SmartArt 図形を検出できます。

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### SmartArt 描画の更新

ドキュメント内の SmartArt 描画を更新するには、次のコードを使用します。

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## 結論

このガイドでは、Aspose.Words for Java のドキュメント シェイプの世界について説明しました。ドキュメントにさまざまなシェイプを追加する方法、シェイプのプロパティを操作する方法、SmartArt シェイプを操作する方法を学習しました。この知識があれば、視覚的に魅力的でインタラクティブなドキュメントを簡単に作成できます。

## よくある質問

### Aspose.Words for Java とは何ですか?

Aspose.Words for Java は、開発者がプログラムで Word 文書を作成、変更、変換できるようにする Java ライブラリです。さまざまな形式の文書を操作するための幅広い機能とツールを提供します。

### Aspose.Words for Java をダウンロードするにはどうすればいいですか?

次のリンクから Aspose.Words for Java を Aspose Web サイトからダウンロードできます。[Aspose.Words for Java をダウンロード](https://releases.aspose.com/words/java/)

### ドキュメントシェイプを使用する利点は何ですか?

ドキュメント シェイプは、ドキュメントに視覚的な要素とインタラクティブ性を追加し、より魅力的で有益なドキュメントを作成します。シェイプを使用すると、吹き出し、ボタン、画像、透かしなどを作成して、全体的なユーザー エクスペリエンスを向上させることができます。

### 図形の外観をカスタマイズできますか?

はい、サイズ、位置、回転、塗りつぶし色などのプロパティを調整することで、図形の外観をカスタマイズできます。Aspose.Words for Java には、図形をカスタマイズするための幅広いオプションが用意されています。

### Aspose.Words for Java は SmartArt と互換性がありますか?

はい、Aspose.Words for Java は SmartArt 図形をサポートしており、ドキュメント内で複雑な図やグラフィックを操作できます。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
