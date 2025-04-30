---
"description": "Aspose.Words for Java のドキュメントシェイプのパワーを解き放ちましょう。ステップバイステップの例題を通して、視覚的に魅力的なドキュメントの作成方法を学びましょう。"
"linktitle": "ドキュメントシェイプの使用"
"second_title": "Aspose.Words Java ドキュメント処理 API"
"title": "Aspose.Words for Java でドキュメントシェイプを使用する"
"url": "/ja/java/document-conversion-and-export/using-document-shapes/"
"weight": 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でドキュメントシェイプを使用する


## Aspose.Words for Java でのドキュメント シェイプの使用の概要

この包括的なガイドでは、Aspose.Words for Java のドキュメントシェイプの世界を深く掘り下げていきます。シェイプは、視覚的に魅力的でインタラクティブなドキュメントを作成する上で不可欠な要素です。吹き出し、ボタン、画像、透かしなど、どんな要素を追加する必要がある場合でも、Aspose.Words for Java はそれらを効率的に行うためのツールを提供します。これらのシェイプの使い方を、ソースコードの例を使って段階的に見ていきましょう。

## ドキュメントシェイプの使い方

コードに進む前に、環境を設定しましょう。Aspose.Words for Javaがプロジェクトに統合されていることを確認してください。まだの場合は、Asposeのウェブサイトからダウンロードできます。 [Aspose.Words for Javaをダウンロード](https://releases.aspose.com/words/java/)

## ドキュメントに図形を追加する

### グループシェイプの挿入

あ `GroupShape` 複数の図形をグループ化することができます。グループ化の作成と挿入方法は次のとおりです。 `GroupShape`：

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

テキストボックス図形を挿入するには、 `insertShape` 以下の例に示す方法を使用します。

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

テーブルセル内に図形を配置する必要がある場合は、次のコードを使用してこれを実現できます。

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
watermark.isLayoutInCell(true); // 図形をセル内に配置した場合は、表のセルの外側に図形を表示します。
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

## SmartArt図形の操作

### SmartArt図形の検出

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

このガイドでは、Aspose.Words for Java のドキュメント図形の世界を探求しました。ドキュメントに様々な図形を追加し、そのプロパティを操作し、SmartArt 図形を操作する方法を学びました。これらの知識があれば、視覚的に魅力的でインタラクティブなドキュメントを簡単に作成できます。

## よくある質問

### Aspose.Words for Java とは何ですか?

Aspose.Words for Javaは、開発者がWord文書をプログラムで作成、変更、変換できるようにするJavaライブラリです。さまざまな形式の文書を扱うための幅広い機能とツールを提供します。

### Aspose.Words for Java をダウンロードするにはどうすればいいですか?

次のリンクから Aspose.Words for Java を Aspose Web サイトからダウンロードできます。 [Aspose.Words for Javaをダウンロード](https://releases.aspose.com/words/java/)

### ドキュメント シェイプを使用する利点は何ですか?

ドキュメントシェイプは、ドキュメントに視覚的な要素とインタラクティブ性を加え、より魅力的で情報豊かなドキュメントを実現します。シェイプを使えば、吹き出し、ボタン、画像、透かしなどを作成でき、ユーザーエクスペリエンス全体を向上させることができます。

### 図形の外観をカスタマイズできますか?

はい、サイズ、位置、回転、塗りつぶし色などのプロパティを調整することで、図形の外観をカスタマイズできます。Aspose.Words for Java には、図形をカスタマイズするための幅広いオプションが用意されています。

### Aspose.Words for Java は SmartArt と互換性がありますか?

はい、Aspose.Words for Java は SmartArt 図形をサポートしており、ドキュメント内で複雑な図やグラフィックを操作できます。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}