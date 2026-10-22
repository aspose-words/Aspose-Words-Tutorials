---
category: general
date: 2026-09-24
description: Javaで空白のWord文書を作成し、Aspose.Wordsを使用して矩形や線などの図形をグループ化する方法を学びます。ステップバイステップのコードが含まれています。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shapes
- add rectangle shape
- group shapes in word
- set shape size
language: ja
lastmod: 2026-09-24
og_description: Javaで空白のWord文書を作成し、Aspose.Wordsを使用して図形をグループ化し、長方形の図形を追加し、図形のサイズを設定する方法を学びます。
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: 空白のWord文書を作成し、Javaで図形をグループ化する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create a blank Word document in Java and group shapes
    like rectangles and lines using Aspose.Words. Includes step‑by‑step code.
  headline: How to create a blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Javaで空白のWord文書を作成し、図形をグループ化する方法
url: /ja/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Javaで空白のWord文書を作成し、図形をグループ化する方法

空白のWord文書を **作成** し、複数の描画オブジェクトを整理したい場合、このガイドで具体的な手順を示します。Aspose.Words for Java を使用すると、グループ形状を挿入し、矩形形状を追加し、線を描画し、各形状のサイズと位置を制御できます—すべて単一の実行可能プログラムで行えます。

ドキュメントの初期化から最終的な `.docx` の保存まで、すべての手順を順に説明します。最後までに、**図形のグループ化方法**、**矩形形状の追加**、そして **形状サイズの設定** を理解でき、Word ファイルを意図した通りに見せることができます。

## 前提条件

- Java 17 以降（コードは任意の最新 JDK でコンパイル可能）
- Aspose.Words for Java ライブラリ（[Aspose website](https://products.aspose.com/words/java) からダウンロード）
- IDE またはビルドツール（Maven/Gradle）で Aspose.Words JAR をクラスパスに追加できる環境
- Java 構文の基本知識

> **プロのコツ:** 依存関係管理には Maven を使用し、`com.aspose:aspose-words:23.12`（または最新バージョン）を `pom.xml` に追加してください。

## 手順 1: 空白の Word 文書を作成

最初のタスクは **空白の Word 文書を作成** することです。これにより、後で図形を挿入できるクリーンなキャンバスが得られます。

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document document = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(document);
```

*なぜ重要か:* `Document` オブジェクトは `.docx` ファイル全体を表します。空白の文書から開始することで、追加する図形に影響を与える隠れた書式設定がないことが保証されます。

## 手順 2: グループ形状を挿入 – �数オブジェクトのコンテナ

**グループ形状** は、複数の図形をまとめて移動、サイズ変更、回転できるコンテナとして機能します。これは Word における **図形のグループ化方法** の核心です。

```java
        // Insert a group shape of width 300 points and height 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

*説明:* `insertGroupShape` メソッドは `GroupShape` オブジェクトを作成し、現在のカーソル位置に配置します。このグループに対して `appendChild` で追加したすべての図形は、単一のユニットとして扱われます。

## 手順 3: 矩形形状を追加し、サイズを設定

ここで、グループに **矩形形状を追加** し、**形状サイズを正確に設定** します。

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);   // set shape width
        rectangle.setHeight(100.0);  // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Add the rectangle to the group
        group.appendChild(rectangle);
```

*なぜ形状サイズを設定する必要があるか:* 幅と高さは矩形がページ上にどのように表示されるかを制御します。`setLeft` と `setTop` メソッドは、矩形をグループの原点に対して位置付け、ピクセル単位のレイアウト制御を可能にします。

## 手順 4: 線形状を追加し、寸法を設定

線は別の一般的な描画オブジェクトです。線に対して **矩形形状と同様のロジック** を適用し、同じサイズ設定の原則が適用できることを示します。

```java
        // Create a line shape
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);   // line length
        line.setHeight(0.0);    // height is zero for a horizontal line
        line.setLeft(20.0);
        line.setTop(130.0);

        // Add the line to the same group
        group.appendChild(line);
```

*重要ポイント:* 線は高さを持ちませんが、長さを定義するために `setWidth` を使用します。位置指定（`setLeft`、`setTop`）は他の形状と同じ座標系に従います。

## 手順 5: グループ化された形状を含む文書を保存

最後に、文書を保存して変更を永続化します。これにより、Microsoft Word で結果を確認できる `.docx` ファイルが生成されます。

```java
        // Save the document to disk
        document.save("GroupShapeDemo.docx");
    }
}
```

**期待される出力:** `GroupShapeDemo.docx` を開くと、空白ページにグループ化された矩形と線が表示されます。どちらかの形状を選択するとグループ全体が選択され、一緒に移動できます。

## よくある質問とエッジケースの対処

| Question | Answer |
|----------|--------|
| *グループに2つ以上の形状を追加できますか？* | はい。追加の形状ごとに `group.appendChild(yourShape)` を呼び出します。 |
| *サイズの単位を別のもの（例: センチメートル）にしたい場合は？* | Aspose.Words はポイントを使用します（1 ポイント = 1/72 インチ）。`Points = centimeters * 28.3465` で変換してください。 |
| *別のマシンで文書を開いたときに、グループはレイアウトを保持しますか？* | はい。サイズと位置のデータはすべて `.docx` ファイルに保存されるため、レイアウトはポータブルです。 |
| *後で形状のグループ化を解除するには？* | `GroupShape` オブジェクトを取得し、`group.getChildNodes(NodeType.SHAPE, true)` を反復処理して各子要素をグループから取り出します。 |
| *グループ全体を回転させる必要がある場合は？* | 保存前に `group.setRotationAngle(double angleInDegrees)` を使用します。 |

## 完全な実行可能サンプル

以下は IDE にコピー＆ペーストできる完全なプログラムです。必要なインポートとコメントがすべて含まれています。

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape (container)
        GroupShape group = builder.insertGroupShape(300.0, 200.0);

        // Step 3: Add a rectangle shape and set its size
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);
        rectangle.setHeight(100.0);
        rectangle.setLeft(20.0);
        rectangle.setTop(20.0);
        group.appendChild(rectangle);

        // Step 4: Add a line shape and configure its dimensions
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);
        line.setHeight(0.0);
        line.setLeft(20.0);
        line.setTop(130.0);
        group.appendChild(line);

        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

プログラムを実行し、Microsoft Word で `GroupShapeDemo.docx` を開くと、説明どおりにグループ化された形状が表示されます。

## 結論

これで、Aspose.Words for Java を使用して **空白の Word 文書を作成**、**Word で図形をグループ化**、**矩形形状を追加**、そして **形状サイズを設定** する方法が分かりました。形状を `GroupShape` に入れることで、位置、拡大縮小、回転をまとめて完全に制御でき、図表やフローチャート、レポートに埋め込むカスタムグラフィックに最適です。

**次のステップ:**  
- 画像やテキストボックスなど、より複雑なオブジェクトで **図形のグループ化方法** を探求する。  
- `setRotationAngle` を試してグループ全体を回転させる。  
- この手法とメールマージを組み合わせ、ブランドロゴを含むパーソナライズド文書を生成する。

コードをご自身のプロジェクトに合わせて自由に調整し、結果をコメントで共有してください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [JavaでWordに矩形形状を作成 – 完全ガイド](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [JavaでWord文書を作成 – 影効果付き矩形形状を追加](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words for .NET を使用してWord文書にグループ形状を作成](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}