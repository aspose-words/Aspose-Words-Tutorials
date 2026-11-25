---
category: general
date: 2026-11-25
description: Java を使用して Word で図形をグループ化する方法と、Aspose.Words で DOCX ファイルの図形サイズを設定する方法。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- how to set shape dimensions
- set shape size word
language: ja
lastmod: 2026-11-25
og_description: Aspose.Words Java API を使用して Word で図形をグループ化し、図形のサイズをすばやく設定する方法。完全なステップバイステップのソリューションをご覧ください。
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Wordで図形をグループ化し、サイズを設定する方法 – Javaガイド
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  headline: How to group shapes in Word and set their dimensions programmatically
  type: TechArticle
- description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  name: How to group shapes in Word and set their dimensions programmatically
  steps:
  - name: Expected output
    text: '* A Word document (`GroupShape.docx`) with one page. * A `GroupShape` containing
      a 100 × 50 pt rectangle and an 80 × 80 pt ellipse. * Selecting either shape
      selects the whole group.'
  - name: How to change the position of the grouped shapes?
    text: 'After creating the `GroupShape`, you can set its `left` and `top` properties:'
  - name: What if I need to add more than two shapes?
    text: '`GroupShape` works like any other container node. Call `groupShape.appendChild(yourShape)`
      for each additional shape. The API does not limit the number of children.'
  - name: Can I apply style (fill color, line weight) to individual shapes?
    text: 'Yes. Each `Shape` object exposes formatting properties:'
  - name: Does the code work with older Aspose.Words versions?
    text: The `insertGroupShape` method was introduced in version 24.9. If you are
      on an earlier version, you’ll need to create a `GroupShape` manually via the
      node tree, which is more involved. Upgrading is the recommended path.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- shapes
title: Wordで図形をグループ化し、プログラムでサイズを設定する方法
url: /ja/java/images-shapes/how-to-group-shapes-in-word-and-set-their-dimensions-program/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wordで図形をグループ化し、プログラムでサイズを設定する方法

Wordで図形を**グループ化する方法**と正確なサイズを制御する必要がある場合、このガイドでは完全な実行可能なソリューションを示します。Aspose.Words for Java を使用すると、長方形と楕円を作成し、それらを `GroupShape` に追加し、幅や高さなどの**図形のサイズを設定する方法**を単一の DOCX ファイルで行うことができます。

以下を学びます:

* 新しい Word 文書をゼロから作成する方法。  
* `GroupShape` を挿入する方法（バージョン 24.9 の新 API）。  
* 長方形と楕円をグループに追加する方法。  
* `setWidth` と `setHeight` を使用して**Word の図形サイズを正確に設定**する方法。  
* 文書をディスクに保存する方法。

外部ツールは不要です — Java 17+、Maven、そして Aspose.Words for Java ライブラリだけで完結します。

## Prerequisites

* Java Development Kit 17 以上。  
* 依存関係管理のための Maven（または Gradle）。  
* Aspose.Words for Java 24.9 以上（`GroupShape` API は 24.9 で導入）。  
* Java の構文とオブジェクト指向の基本的な知識。

まだプロジェクトに Aspose.Words を追加していない場合は、以下の Maven 依存関係を含めてください:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Step 1: Create a new document and a DocumentBuilder

`Document` クラスは Word ファイル全体を表し、`DocumentBuilder` はコンテンツ追加の便利な手段を提供します。

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this step?*  
新しい `Document` を作成するとクリーンなキャンバスが得られます。`DocumentBuilder` は段落や表、そして本ケースでは図形を挿入できる高レベルのヘルパーです。

## Step 2: Insert a GroupShape (new API in version 24.9)

`GroupShape` はコンテナのように機能し、追加した図形はすべて同じビジュアルグループの一部になります。

```java
        // Step 2: Insert a GroupShape (new API in version 24.9)
        GroupShape groupShape = builder.insertGroupShape();
```

*Why use `GroupShape`?*  
図形をグループ化すると、複数のオブジェクトを一度に移動、回転、または書式設定でき、作業が簡素化されます。この API は 24.9 で追加されたため、古いバージョンではこの行はコンパイルできません。

## Step 3: Create a rectangle, set its size, and add it to the group

ここでは長方形に対して**図形のサイズを設定する方法**を実演します。

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);   // height in points
        groupShape.appendChild(rectangle);
```

*Why set width and height explicitly?*  
Word は図形サイズをポイント単位で保持します。`setWidth` と `setHeight` を呼び出すことで、正確な視覚的占有領域を制御でき、レイアウトの精密さや PDF へのエクスポートが必要なシナリオで重要になります。

## Step 4: Create an ellipse, set its size, and add it to the same group

同じ**図形サイズ設定**テクニックは任意の図形タイプで機能します。

```java
        // Step 4: Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(document, ShapeType.ELLIPSE);
        ellipse.setWidth(80.0);
        ellipse.setHeight(80.0);
        groupShape.appendChild(ellipse);
```

*Why add the ellipse to the same `GroupShape`?*  
両方の図形がユニットとして一緒に移動します。アイコン、ロゴ、または整列が必要な複雑な図表を作成する際に便利です。

## Step 5: Save the document with the grouped shapes

最後に DOCX ファイルをディスクに永続化します。

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShape.docx");
    }
}
```

このプログラムを実行すると、**GroupShape.docx** という名前のファイルが生成され、長方形と楕円がグループ化された状態で保存されます。Microsoft Word で開くと、2 つの図形が単一オブジェクトとして扱われ、ドラッグ、サイズ変更、回転を同時に行えます。

### Expected output

* 1 ページの Word 文書（`GroupShape.docx`）。  
* 100 × 50 pt の長方形と 80 × 80 pt の楕円を含む `GroupShape`。  
* 任意の図形を選択すると、グループ全体が選択されます。

## Common questions and edge cases

### How to change the position of the grouped shapes?

`GroupShape` を作成した後、`left` と `top` プロパティを設定できます:

```java
groupShape.setLeft(150.0);
groupShape.setTop(200.0);
```

これらの座標もポイント単位で測定されます。

### What if I need to add more than two shapes?

`GroupShape` は他のコンテナノードと同様に機能します。追加したい図形ごとに `groupShape.appendChild(yourShape)` を呼び出してください。子要素数に制限はありません。

### Can I apply style (fill color, line weight) to individual shapes?

可能です。各 `Shape` オブジェクトは書式設定プロパティを公開しています:

```java
rectangle.getFillColor().setColor(Color.BLUE);
ellipse.getStroke().setWeight(2.0);
```

### Does the code work with older Aspose.Words versions?

`insertGroupShape` メソッドはバージョン 24.9 で導入されました。以前のバージョンを使用している場合は、ノードツリーを介して手動で `GroupShape` を作成する必要があり、手間がかかります。アップグレードが推奨されます。

## Pro tips

* **ポイント単位を使用して一貫性を保つ** – Word の内部単位はポイント (1/72 インチ) です。ピクセルやセンチメートルから変換すると予期しないサイズになることがあります。  
* **配置前にグループ化** – 子要素をすべて追加した後で `GroupShape` の位置を設定してください。そうしないとオフセットの再計算が必要になることがあります。  
* **DocumentBuilder を再利用** – `builder.moveTo` でカーソルを移動させ、各 `insertGroupShape` 呼び出しの前に位置を調整すれば、同一文書に複数のグループを挿入できます。

## Conclusion

これで **Word で図形をグループ化する方法** と **Aspose.Words for Java を使用して図形のサイズを設定する方法** の完全なエンドツーエンド例が手に入りました。チュートリアルでは、文書の作成、`GroupShape` の挿入、長方形と楕円の追加、正確なサイズ設定、そして結果の保存までをカバーしました。

ここからさらに進められること:

* 同じグループにテキストボックスや画像を追加する。  
* API 経由で Word のスマートアート機能を使い、グループ化した図形にアニメーションを付与する。  
* グループ化した図形を PDF や SVG にエクスポートしてウェブで利用する。

さまざまな図形タイプ、サイズ、位置で実験してみてください。グループ化は Word 文書内の複雑なレイアウトを強力にコントロールする手段です。

## What Should You Learn Next?

以下のチュートリアルは、本ガイドで示したテクニックを基にした関連トピックを扱っています。各リソースには、ステップバイステップの解説と完全なコード例が含まれており、API の追加機能を習得したり、別の実装アプローチを探求したりするのに役立ちます。

- [How to create a blank Word document and group shapes in Java](/words/english/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/)
- [How to group shapes in Word with Java – complete guide](/words/english/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}