---
date: 2026-02-16
description: Aspose.Words for Java を使用して、テキストボックスの作成、透かし文字の追加、複数の図形のグループ化、図形のアスペクト比の設定、テーブルセルへの図形の配置方法を学びます。
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Javaでテキストボックスを作成し、ドキュメントシェイプを使用する方法
url: /ja/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Javaでドキュメントシェイプを使用する

## Aspose.Words for Javaでドキュメントシェイプを使用する概要

この包括的なガイドでは、Aspose.Words for Javaを使用して **テキストボックスを作成** オブジェクトやその他の強力なシェイプの作成方法を学びます。シェイプを使用すると、Word ドキュメントに吹き出し、ボタン、透かし、SmartArt などを追加でき、視覚的に魅力的でインタラクティブになります。単純なテキストボックスの挿入から複数シェイプのグループ化、アスペクト比の設定、テーブルセル内へのシェイプ配置まで、実践的な例を順に解説します。

## クイック回答
- **テキストボックスを追加する主な方法は何ですか？** `DocumentBuilder.insertShape(ShapeType.TEXT_BOX, …)` を使用します。
- **シェイプをグループ化できますか？** はい – `GroupShape` を作成し、子シェイプを追加します。
- **シェイプのアスペクト比をロックまたはロック解除するには？** `shape.setAspectRatioLocked(true/false)` を呼び出します。
- **シェイプで透かしを追加できますか？** もちろんです – `TEXT_PLAIN_TEXT` を持つ `Shape` を挿入し、塗りつぶし/線を設定します。
- **SmartArt ダイアグラムは Aspose.Words で使用できますか？** はい – `shape.hasSmartArt()` で検出し、`shape.updateSmartArtDrawing()` で更新します。

## テキストボックスとは何か、そしてテキストボックスシェイプを作成する理由

テキストボックスは、書式設定されたテキスト、画像、またはその他のシェイプを保持できるコンテナです。自動化で **テキストボックスを作成** を使用すると、ページ上の任意の場所にフローティングコンテンツを配置でき、注釈、吹き出し、装飾要素などをメインの文書フローを変更せずに追加できます。

## シェイプの追加方法

コードに入る前に、プロジェクトで Aspose.Words for Java が参照されていることを確認してください。まだ追加していない場合は、公式サイトからライブラリをダウンロードしてください：

[Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### ドキュメントへのシェイプの追加

## 複数シェイプのグループ化方法

`GroupShape` を使用すると、複数の個別シェイプを単一ユニットとして扱うことができ、まとめて移動や回転させるのに便利です。

### GroupShape の挿入

以下は、グループを作成し、2 つの異なるシェイプを追加して、ドキュメントに挿入する完全な例です。

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

## テキストボックスの作成方法（create text box）

### テキストボックスシェイプの挿入

`insertShape` メソッドを使用すると、テキストボックスの追加が簡単になります。以下の例では、テキストボックスの位置設定と回転の 2 つの方法を示しています。

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

## シェイプのアスペクト比の設定方法

### アスペクト比の管理

シェイプを元の比例を保たずに伸ばす必要がある場合があります。以下のスニペットは、画像シェイプのアスペクト比ロックを解除する方法を示しています。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## シェイプをテーブルセルに配置する方法

### テーブルセル内へのシェイプ配置

以下は、テーブルを作成し、ページに対して相対的に配置される透かしシェイプを挿入する例です。このシェイプはセル内にも配置可能です。

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
watermark.isLayoutInCell(true); // Display the shape outside of the table cell if it will be placed into a cell.
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

## SmartArt シェイプの操作

### SmartArt シェイプの検出

`hasSmartArt()` メソッドを使用して、プログラムからドキュメント内の SmartArt オブジェクトを検出できます。

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### SmartArt 描画の更新

SmartArt シェイプを見つけたら、`updateSmartArtDrawing()` を使用して内部描画データを更新できます。

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## 結論

このガイドでは、Aspose.Words for Java を使用して **テキストボックスを作成** オブジェクト、複数シェイプのグループ化、アスペクト比の調整、テーブルセル内へのシェイプ埋め込み、透かしの追加、SmartArt ダイアグラムの操作方法を取り上げました。これらのテクニックにより、プログラムでリッチな書式設定とインタラクティブな Word ドキュメントを構築できるようになります。

## FAQ

### Aspose.Words for Java とは何ですか？

Aspose.Words for Java は、開発者がプログラムで Word ドキュメントを作成、変更、変換できる Java ライブラリです。さまざまな形式のドキュメントを操作するための豊富な機能とツールを提供します。

### Aspose.Words for Java はどこからダウンロードできますか？

以下のリンクから Aspose のウェブサイトで Aspose.Words for Java をダウンロードできます: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### ドキュメントシェイプを使用するメリットは何ですか？

ドキュメントシェイプは視覚的要素とインタラクティブ性を追加し、ドキュメントをより魅力的で情報豊かにします。シェイプを使って吹き出し、ボタン、画像、透かしなどを作成でき、全体的なユーザー体験が向上します。

### シェイプの外観をカスタマイズできますか？

はい、サイズ、位置、回転、塗りつぶし色などのプロパティを調整することでシェイプの外観をカスタマイズできます。Aspose.Words for Java はシェイプカスタマイズのための豊富なオプションを提供します。

### Aspose.Words for Java は SmartArt と互換性がありますか？

はい、Aspose.Words for Java は SmartArt シェイプをサポートしており、ドキュメント内で複雑な図やグラフィックを扱うことができます。

## よくある質問

**Q: 同じシェイプ内でテキストボックスと画像を組み合わせられますか？**  
A: はい。シェイプを作成した後、`builder.insertImage()` を使用してテキストボックスシェイプに画像を挿入し、必要に応じてレイアウトを調整します。

**Q: 透かしを文書のすべてのコンテンツの背後に表示させるには？**  
A: シェイプの `WrapType` を `NONE` に設定し、`RelativeHorizontalPosition` と `RelativeVerticalPosition` を `PAGE` に調整します。これにより透かしがメインフローの背後に配置されます。

**Q: Word でグループ化されたシェイプにアニメーションを付けられますか？**  
A: Aspose.Words はシェイプの作成とグループ化は可能ですが、アニメーション機能は Word の UI 機能に依存するためサポートされていません。

**Q: SmartArt のサポートに必要な Aspose.Words のバージョンは？**  
A: SmartArt の検出と更新は、Java 用 Aspose.Words 20.9 以降で利用可能です。

**Q: 多数のシェイプを含む大規模ドキュメントを効率的に処理できますか？**  
A: はい。`doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010)` 以上を使用して、多数のシェイプを含むドキュメントのパフォーマンスを向上させます。

---

**最終更新日:** 2026-02-16  
**テスト環境:** Aspose.Words for Java 24.12  
**作者:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}