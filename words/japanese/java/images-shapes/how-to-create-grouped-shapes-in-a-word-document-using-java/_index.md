---
category: general
date: 2026-10-13
description: Java を使用して Word でグループ化された図形の作成方法を学びましょう。このガイドでは、グループ図形の挿入方法、グループに線を追加する方法、そして文書全体で複数の図形をグループ化する方法を示します。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create grouped shapes
- add line to group
- group multiple shapes word
- insert group shape
language: ja
lastmod: 2026-10-13
og_description: JavaでWordにグループ化された図形を作成します。この完全なチュートリアルに従って、グループ図形の挿入、グループへの線の追加、複数の図形のグループ化をWord文書で行いましょう。
og_image_alt: Screenshot of a Word document showing created grouped shapes
og_title: JavaでWordのグループ化されたシェイプを作成する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to create grouped shapes in Word with Java. This guide shows
    you how to insert group shape, add line to group, and group multiple shapes word‑wide.
  headline: How to create grouped shapes in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Java を使用して Word 文書でグループ化された図形を作成する方法
url: /ja/java/images-shapes/how-to-create-grouped-shapes-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java を使用して Word 文書でグループ化されたシェイプを作成する方法

If you need to **create grouped shapes** in a Microsoft Word file from Java, this tutorial walks you through the entire process. You’ll see how to **insert group shape**, place a rectangle and a line inside the same container, and finally save the document with the grouped graphics.

Grouping shapes makes it easy to move, resize, or style several drawing objects as a single unit—perfect for diagrams, flowcharts, or custom page decorations. By the end of this guide you’ll be able to **add line to group**, **group multiple shapes word** documents, and reuse the same technique for any number of shapes.

## 前提条件

- Java 17 以降が開発マシンにインストールされていること。  
- Aspose.Words for Java のライセンス（または無料評価版）。  
- Aspose.Words の依存関係を追加できる Maven または Gradle プロジェクト：

```xml
<!-- Maven example -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

追加のライブラリは必要ありません。

## 手順 1: グループ シェイプ コンテナを挿入する

最初のステップは、ドキュメントに **insert group shape** を挿入することです。このコンテナは以降のすべてのシェイプを保持します。

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // The rest of the code will add shapes to this group
```

`builder.insertGroupShape()` は、タイプ `GROUPSHAPE` の空の `Shape` オブジェクトを作成します。これは、他の描画オブジェクトを含めることができる透明なキャンバスと考えてください。

## 手順 2: グループに矩形を追加する

矩形は、シェイプのグループの視覚的背景としてよく使用されます。

```java
        // Create a rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        rectangleShape.setLeft(0);      // X‑coordinate inside the group
        rectangleShape.setTop(0);       // Y‑coordinate inside the group

        // Append the rectangle to the group container
        groupShape.appendChild(rectangleShape);
```

`Left` と `Top` を `0` に設定すると、矩形がグループの左上隅に配置されます。これらの値を変更して、グループ内でシェイプのオフセットを調整できます。

## 手順 3: **Add line to group** – 線シェイプを作成する

ここで **add line to group** を行います。線は矩形の下に表示されます。

```java
        // Create a line shape
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);   // length of the line
        lineShape.setTop(60);      // vertical position (60 points down)

        // Append the line to the same group
        groupShape.appendChild(lineShape);
```

`Top` プロパティは、線を矩形の下に 60 ポイント移動させ、シンプルなスタックレイアウトを作成します。水平オフセットが必要な場合は `Left` を設定することもできます。

## 手順 4: グループ化されたシェイプを含む文書を保存する

```java
        // Save the document to a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

Microsoft Word で `GroupShapeDemo.docx` を開くと、矩形と線の両方を含む単一のグループが表示されます。グループを選択すると、両方のシェイプを一緒に移動でき、**group multiple shapes word** に成功したことが示されます。

## 完全な実行可能サンプル

以下は、すべてのインポートとエラーハンドリングを含む完全なプログラムです。IDE にコピーし、`YOUR_DIRECTORY` を既存のフォルダー パスに置き換えて実行してください。

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // Step 3: Add a rectangle to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);
        rectangleShape.setHeight(50);
        rectangleShape.setLeft(0);
        rectangleShape.setTop(0);
        groupShape.appendChild(rectangleShape);

        // Step 4: Add a line to the group
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);
        lineShape.setTop(60);
        groupShape.appendChild(lineShape);

        // Step 5: Save the document
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

### 期待される出力

- `GroupShapeDemo.docx` という名前のファイルがターゲット フォルダーに作成されます。  
- Word でファイルを開くと、上部に矩形、下部に線が含まれる単一のグループ化オブジェクトが表示されます。  
- グループをドラッグすると両方のシェイプが一緒に移動し、**created grouped shapes** に成功したことが確認できます。

## ヒントと一般的な落とし穴

- **Pro tip:** グループ内の個々のシェイプを回転またはスタイル設定する必要がある場合、グループに追加する前にそれぞれのセッター（`setRotation`、`getFill().setForeColor` など）を呼び出してください。グループはこれらのビジュアルプロパティを保持します。  
- **Watch out for:** 線の `Top` プロパティを設定し忘れると、矩形と重なり、グループがごちゃごちゃに見えることがあります。  
- **Edge case:** 2 つ以上のシェイプを追加する場合、各子の座標はグループの原点 (0,0) に対して相対的であることを覚えておいてください。レイアウトをそれに合わせて計画しましょう。  
- **Performance note:** 多数（数百）のシェイプをグループ化すると、ファイルサイズが若干増加する可能性がありますが、Word での後続編集が簡素化されます。

## プログラムで **group multiple shapes word** 文書を作成する方法

上記のパターン—グループ コンテナを作成し、各子シェイプを設定して追加する—は、円、画像、テキスト ボックスなど、任意の数のシェイプに対して機能します。`doc.save()` を呼び出す前に「シェイプ作成 → プロパティ設定 → 追加」の手順を繰り返すだけです。

グループに既に他のシェイプが含まれている状態で **add line to group** が必要な場合、既存のグループを次のように取得できます：

```java
Shape existingGroup = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                                 .stream()
                                 .filter(s -> ((Shape) s).getShapeType() == ShapeType.GROUPSHAPE)
                                 .findFirst()
                                 .orElseThrow(() -> new IllegalStateException("No group found"));
existingGroup.appendChild(lineShape);
```

これにより、文書のライフサイクルの任意の時点でグループを変更できることが示されます。

## 結論

これで、Java と Aspose.Words を使用して Word 文書に **create grouped shapes** する方法が分かりました。**inserting group shape**、**adding line to group**、**group multiple shapes word** を行うことで、単一オブジェクトとして動作する複雑な図形を作成でき、図表、テンプレート、レポート自動生成に最適です。

次に、以下の関連トピックを確認してください：

- **Applying styles to grouped shapes** – すべての子に対して一括で塗りつぶし色、枠線、エフェクトを設定する方法を学びます。  
- **Exporting grouped shapes to PDF** – ドキュメントを変換した際に同じグループが保持される様子を確認できます。  
- **Animating shapes with VBA** – Java で生成したグループと Word マクロを組み合わせ、インタラクティブな文書を作成します。

さまざまなシェイプの種類、サイズ、位置を自由に試してみてください。グループ化により、多数のオブジェクトを一つとして扱える柔軟性が得られ、コードとユーザー操作の両方がシンプルになります。ハッピーコーディング！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれ、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}