---
category: general
date: 2026-08-14
description: Aspose.Words を使用して Java で Word の図形をグループ化します。矩形の図形の作成方法、図形のサイズ設定方法、そして空白の
  Word 文書で複数の図形をグループ化する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create rectangle shape
- set shape dimensions
- group multiple shapes
- build blank word document
language: ja
lastmod: 2026-08-14
og_description: Aspose.Words for Java を使用して Word で図形をグループ化します。空白の Word 文書を作成し、長方形の図形を作成、サイズを設定し、数分で複数の図形をグループ化します。
og_image_alt: Screenshot showing grouped rectangle shapes in a Word document created
  with Java
og_title: Wordで図形をグループ化 – 開発者向けJava例
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to create
    rectangle shape, set shape dimensions, and group multiple shapes in a blank Word
    document.
  headline: Group shapes in Word – complete programming guide
  type: TechArticle
- questions:
  - answer: Overlap is allowed; Word will render them in the order they were added.
      Use `setZOrder` if you need explicit stacking.
    question: What if the shapes overlap?
  - answer: No. A `GroupShape` is confined to a single page because its coordinate
      system is page‑relative.
    question: Can I group shapes across different pages?
  - answer: Each child keeps its own formatting (fill color, line style). To apply
      a uniform style, iterate over `groupShape.getChildNodes()` and set properties
      programmatically.
    question: Do grouped shapes inherit formatting?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Wordで図形をグループ化 – 完全プログラミングガイド
url: /ja/java/images-shapes/group-shapes-in-word-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word でシェイプをグループ化する – 完全プログラミングガイド

Wordでシェイプをグループ化する必要がある場合、このチュートリアルではJavaとAspose.Wordsを使用した全プロセスを解説します。**空のWord文書を作成する**、**長方形シェイプを作成する**、**シェイプのサイズを設定する**、そして最終的に**複数のシェイプをグループ化して**単一オブジェクトとして動作させる方法を学びます。

Wordファイル内でシェイプを扱うことは、絵筆のないキャンバスに描くような感覚です。このガイドの最後までに、レポート、請求書、カスタムテンプレートの生成など、あらゆるJavaプロジェクトに組み込める再利用可能なコードスニペットが手に入ります。

## 必要なもの

- Java 8 以上
- Aspose.Words for Java（最新バージョン、例: 24.9）
- IntelliJ IDEA や Eclipse などの IDE
- オブジェクト指向プログラミングの基本的な知識

これらの前提条件はすべて無料でインストールでき、以下のコードは単一のMaven依存関係でコンパイルできます。

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## 手順 1: 空のWord文書を作成し、ビルダーを初期化する

最初に行うべきことは**空のWord文書を作成する**ことです。これにより、後でシェイプを挿入できるクリーンなキャンバスが得られます。

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder lets you add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` は *.docx* ファイル全体を表し、`DocumentBuilder` は段落、表、シェイプを挿入するヘルパーです。両オブジェクトの初期化は、すべてのWord自動化タスクの基礎となります。

## 手順 2: グループシェイプ コンテナを挿入する

**グループシェイプ** は他のシェイプを保持できるフォルダーのように機能します。まず、サイズ 400 pt × 200 pt の固定コンテナを作成します。

```java
        // Insert a group shape that will hold other shapes (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);
```

`insertGroupShape` メソッドは `GroupShape` オブジェクトを返します。単一ユニットとして扱いたいすべてのシェイプは、このオブジェクトに追加する必要があります。

## 手順 3: 長方形シェイプを作成し、シェイプのサイズを設定する

ここでは**長方形シェイプ** オブジェクトを作成し、サイズを設定し、グループ内に配置します。この手順では**シェイプのサイズを正確に設定する**方法も示します。

```java
        // ---- First rectangle -------------------------------------------------
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);   // set shape dimensions: width = 150 pt
        rectangle1.setHeight(100);  // set shape dimensions: height = 100 pt
        rectangle1.setTop(20);      // vertical offset inside the group
        rectangle1.setLeft(20);     // horizontal offset inside the group
        groupShape.appendChild(rectangle1); // add to the group

        // ---- Second rectangle ------------------------------------------------
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);    // place it beside the first rectangle
        groupShape.appendChild(rectangle2);
```

両方の長方形は同じサイズを共有していますが、`left` プロパティが異なるため横に並んで表示されます。必要に応じて `setTop` と `setLeft` を変更して任意のレイアウトを構成できます。

## 手順 4: グループ化された長方形を含む文書を保存する

シェイプをグループ内に配置したら、単に `Document` を保存します。生成されたファイルでは、選択時に一緒に移動する2つの長方形が表示されます。

```java
        // Save the document to disk
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

プログラムを実行すると、作業ディレクトリに `GroupShape.docx` が作成されます。Microsoft Wordで開き、1つの長方形を選択すると、グループ全体がユニットとして移動することが確認できます—これが **Word のシェイプをグループ化** の本来の動作です。

![Group shapes in Word example](group-shapes.png){alt="Group shapes in Word example"}

*図: Word文書内で一緒にグループ化された2つの長方形シェイプ。*

## プロのコツ: 同じグループシェイプを再利用する

後でさらにシェイプ（例: 円、テキストボックス）を追加する必要がある場合は、`groupShape` の参照を保持し、`appendChild` の呼び出しを続けます。これによりコンテナの再作成を防ぎ、すべてのメンバーが同期されたままになります。

```java
        // Example: add a third shape later
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(120);
        ellipse.setHeight(80);
        ellipse.setTop(130);
        ellipse.setLeft(140);
        groupShape.appendChild(ellipse);
```

## エッジケースとよくある質問

- **シェイプが重なった場合はどうなりますか？** 重なりは許可されており、Wordは追加された順序で描画します。明示的なスタック順が必要な場合は `setZOrder` を使用してください。
- **異なるページ間でシェイプをグループ化できますか？** できません。`GroupShape` は座標系がページ相対であるため、単一ページに限定されます。
- **グループ化されたシェイプは書式設定を継承しますか？** 各子シェイプは独自の書式設定（塗りつぶし色、線のスタイル）を保持します。統一したスタイルを適用するには、`groupShape.getChildNodes()` を反復処理し、プログラムでプロパティを設定します。

## 参考用フルソースコード

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // 1. Build blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert group shape container (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);

        // 3. Create first rectangle and set shape dimensions
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);
        rectangle1.setHeight(100);
        rectangle1.setTop(20);
        rectangle1.setLeft(20);
        groupShape.appendChild(rectangle1);

        // 4. Create second rectangle and set shape dimensions
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);
        groupShape.appendChild(rectangle2);

        // 5. Save the document containing the grouped rectangles
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

プログラムを実行すると、2つの長方形が**グループ化**されたDOCXファイルが生成されます。任意の長方形を選択すると両方が移動し、**複数のシェイプをグループ化**に成功したことが確認できます。

## 結論

これで、Javaを使用して **Wordでシェイプをグループ化**する方法が分かりました。**空のWord文書を作成**し、**長方形シェイプを作成**、**シェイプのサイズを設定**し、最終的に**複数のシェイプを単一の可動オブジェクトにグループ化**する手順です。このパターンは任意の数のシェイプに拡張でき、テキスト、画像、チャートと組み合わせてリッチなプログラム生成ドキュメントを構築できます。

### 次は何をすべきか？

- 異なるタイプ（楕円、矢印、テキストボックス）で **複数のシェイプをグループ化** することを探求してください。
- `shape.getFillColor()` と `shape.getLine().setColor()` を呼び出して、塗りつぶし色や枠線を適用します。
- 構造化レポートのために、テーブルセルにグループ化されたシェイプを挿入します。
- この手法とメールマージを組み合わせ、ブランドロゴを含む個別契約書を生成します。

自由に実験し、サイズを調整したり、追加コンテンツを埋め込んだりしてください。グループ化をマスターすれば、Word自動化スクリプトははるかに柔軟で保守しやすくなります。コーディングを楽しんでください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、完全な動作コード例とステップバイステップの解説が含まれており、追加のAPI機能を習得し、プロジェクトで代替実装アプローチを探求するのに役立ちます。

- [Java 用 Aspose.Words でドキュメントシェイプを使用する](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Word 文書を Java で作成 – 影効果付き長方形シェイプの追加](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [.NET 用 Aspose.Words で Word 文書にグループシェイプを作成する](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}