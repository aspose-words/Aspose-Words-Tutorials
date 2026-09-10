---
date: 2025-12-14
description: Aspose.Words for Java を使用して画像シェイプの挿入方法を学びましょう。このガイドでは、シェイプの追加、テキストボックスシェイプの作成、テーブル内へのシェイプ配置、シェイプのアスペクト比の設定、そしてコールアウトシェイプの追加方法を示します。
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java におけるドキュメント シェイプの使用
url: /ja/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java で **insert image shape** を挿入する方法

## Quick Answers
- **シェイプを追加する主な方法は何ですか？** `DocumentBuilder.insertShape` を使用するか、`Shape` インスタンスを作成してドキュメントツリーに追加します。  
- **画像をシェイプとして挿入できますか？** はい – `builder.insertImage` を呼び出し、返された `Shape` を他のシェイプと同様に扱います。  
- **シェイプのアスペクト比を保持するには？** 必要に応じて `shape.setAspectRatioLocked(true)` または `false` を設定します。  
- **シェイプをグループ化できますか？** もちろんです – `GroupShape` でラップし、グループ全体を単一ノードとして挿入します。  
- **SmartArt 図は Aspose.Words で使用できますか？** はい、プログラムで SmartArt シェイプを検出し、更新できます。

## **insert image shape** とは何ですか？
*image shape* は、Word ドキュメント内にラスタまたはベクタ画像を保持する視覚要素です。Aspose.Words では、画像は `Shape` オブジェクトで表現され、サイズ、位置、回転、折り返しなどをフルコントロールできます。

## ドキュメントでシェイプを使用する理由
- **視覚的インパクト:** シェイプは重要情報に注意を引きます。  
- **インタラクティブ性:** ボタンやコールアウトは URL やブックマークにリンクできます。  
- **レイアウトの柔軟性:** 絶対座標または相対座標でグラフィックを正確に配置できます。  
- **自動化:** 手動編集なしで複雑なレイアウトを生成できます。

## 前提条件
- Java Development Kit (JDK 8 以上)  
- Aspose.Words for Java ライブラリ（公式サイトからダウンロード）  
- Java とオブジェクト指向プログラミングの基本知識  

ライブラリはここからダウンロードできます: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

## **add shape** の方法 – GroupShape の挿入
`GroupShape` を使用すると、複数のシェイプを 1 つの単位として扱えます。これにより、複数要素をまとめて移動や書式設定が可能です。

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

## **text box shape** の作成
テキストボックスは書式設定されたテキストを保持できるコンテナです。回転させて動的な外観にすることもできます。

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

## **shape aspect ratio** の設定
シェイプを自由に伸縮させる場合と、元の比率を保ちたい場合があります。アスペクト比の制御は簡単です。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## **shape in table** の配置
テーブルセル内にシェイプを埋め込むと、レポートレイアウトで便利です。以下の例はテーブルを作成し、ページ全体に跨る透かしスタイルのシェイプを挿入します。

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

## **callout shape** の追加
コールアウトシェイプはメモや警告を強調表示するのに最適です。上記コードは `ACCENT_BORDER_CALLOUT_1` を使用していますが、`ShapeType` を任意のコールアウトバリエーションに変更すればデザインに合わせられます。

## SmartArt シェイプの操作

### SmartArt シェイプの検出
SmartArt 図はプログラムで識別できるため、必要に応じて処理や置換が可能です。

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### SmartArt 描画の更新
検出後、データ変更に合わせて SmartArt グラフィックを更新できます。

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## よくある問題とヒント
- **シェイプが表示されない:** `builder.insertNode` を使用して対象ノードの後にシェイプを挿入しているか確認してください。  
- **予期しない回転:** 回転はシェイプの中心を基準に適用されます。必要に応じて `setLeft`/`setTop` を調整してください。  
- **アスペクト比がロックされている:** 多くのシェイプはデフォルトでアスペクト比をロックしています。自由に伸縮したい場合は `setAspectRatioLocked(false)` を呼び出してください。  
- **SmartArt の検出が失敗する:** 使用している Aspose.Words のバージョンが SmartArt をサポートしているか（v24 以降）確認してください。

## よくある質問

**Q: Aspose.Words for Java とは何ですか？**  
A: Aspose.Words for Java は、開発者がプログラムから Word ドキュメントを作成、変更、変換できる Java ライブラリです。さまざまな形式のドキュメント操作機能を提供します。

**Q: Aspose.Words for Java はどこからダウンロードできますか？**  
A: 以下のリンクからダウンロードできます: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

**Q: ドキュメントシェイプを使用するメリットは何ですか？**  
A: シェイプは視覚要素とインタラクティブ性をドキュメントに追加し、より魅力的で情報豊富な資料を作成できます。コールアウト、ボタン、画像、透かしなどを作成でき、ユーザー体験が向上します。

**Q: シェイプの外観はカスタマイズできますか？**  
A: はい、サイズ、位置、回転、塗りつぶし色などのプロパティを調整することでシェイプの外観を自由にカスタマイズできます。Aspose.Words for Java は豊富なカスタマイズオプションを提供します。

**Q: Aspose.Words for Java は SmartArt と互換性がありますか？**  
A: はい、Aspose.Words for Java は SmartArt シェイプをサポートしており、ドキュメント内の複雑な図やグラフィックを操作できます。

**最終更新日:** 2025-12-14  
**テスト環境:** Aspose.Words for Java 24.12 (latest)  
**作者:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}