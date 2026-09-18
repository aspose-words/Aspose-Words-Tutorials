---
category: general
date: 2026-09-18
description: Aspose.Words を使用して空白のドキュメントを作成し、Word に図形を挿入する – 三角形の図形の追加方法やその他の操作を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- add shapes to word
- how to insert triangle
- add triangle shape
- create word document
language: ja
lastmod: 2026-09-18
og_description: Aspose.Words を使用して Word で空白の文書を作成し、三角形の図形や図形のグループ化、その他のグラフィックの挿入方法を学びましょう。この完全ガイドに従ってください。
og_image_alt: Screenshot of a Word document showing a grouped shape with a triangle
  inside
og_title: 空白の文書を作成し、Wordに図形を追加する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document and insert shapes to Word with Aspose.Words –
    learn how to add a triangle shape and more.
  headline: How to create blank document and add shapes to Word
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Wordで空白の文書を作成し、図形を追加する方法
url: /ja/java/images-shapes/how-to-create-blank-document-and-add-shapes-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wordで空白文書を作成し、図形を追加する方法

If you need to **create blank document** and then enrich it with graphics, this guide shows you exactly how. We'll walk through creating a Word file from scratch and **add shapes to Word**, including **how to insert triangle** shape, using Aspose.Words for Java.

You’ll finish the tutorial with a ready‑to‑use *.docx* file that contains a grouped shape holding a triangle. The steps cover everything from project setup to saving the final **create word document**. No external tools are required beyond Aspose.Words.

## 前提条件

* Java 17 以降がインストールされていること  
* 依存関係管理のための Maven または Gradle  
* Aspose.Words for Java のライセンス（無料評価版でもこのデモは動作します）  

別のビルドシステムを使用したい場合は、依存関係の構文を適宜調整してください。コードは Java をサポートする任意のプラットフォームで動作します。

## Aspose.Words で空白文書を作成する

The first operation is to **create blank document** in memory. Aspose.Words provides a `Document` class that represents a Word file without any content.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank document
```

`new Document()` コンストラクタは空の *.docx* 構造を作成し、後で段落、表、またはグラフィックで内容を埋めることができます。文書が空白であるため、追加するすべての要素を完全にコントロールできます。

## Word に図形を追加する – グループ図形の挿入

A group shape lets you treat several graphics as a single unit. This is useful when you want to move or resize multiple shapes together.

```java
        // Step 2: Initialize a DocumentBuilder to construct content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a group shape of size 300 × 300 points
        GroupShape group = builder.insertGroupShape(300.0, 300.0);
```

`DocumentBuilder` はコンテンツ追加の主要 API です。`insertGroupShape` 呼び出しは、300 × 300 ポイント（約 4 × 4 インチ）のコンテナを作成します。この呼び出しの後、カーソルはグループの *内部* に配置され、追加の図形を挿入できる状態になります。

### なぜグループ図形を使用するのか？

Grouping keeps related graphics aligned and makes it easier to apply uniform formatting. If you later decide to move the triangle, the whole group moves together, preserving layout.

## グループ内に三角形図形を挿入する方法

Now we address **how to insert triangle** shape. The triangle is one of the built‑in `ShapeType` values.

```java
        // Step 4: Move the cursor into the group's first paragraph
        builder.moveTo(group.getFirstParagraph());

        // Step 5: Insert a triangle shape of size 60 × 60 points inside the group
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);
```

`moveTo` 呼び出しにより、ビルダーの挿入位置がグループの最初の段落になることが保証されます。その後 `insertShape` が 60 × 60 ポイントの三角形を追加します。カーソルがグループ内にあるため、三角形はグループ図形の子要素となります。

**Add triangle shape** のヒント:

* サイズはポイントで測定されます。72 ポイントが 1 インチに相当します。レイアウトに合わせて寸法を調整してください。  
* 別の向きが必要な場合は、`builder.getCurrentParagraph().getParagraphFormat().setAlignment()` を使用してグループ内で図形の配置を設定します。  
* 三角形はグループの塗りと線のスタイルを継承しますが、`shape.getFillColor()` または `shape.getStrokeColor()` で上書きできます。

## 文書を保存する – create word document

After constructing the graphics, you save the file. This step finalizes the **create word document** operation.

```java
        // Step 6: Save the document with the extended group shape
        doc.save("ExtendedGroup.docx");               // create word document
    }
}
```

`doc.save` はメモリ上の表現をディスクに標準的な Word 文書として書き込みます。`ExtendedGroup.docx` は Microsoft Word、LibreOffice、または OOXML 形式をサポートする任意のビューアで開くことができます。このファイルは、コードで作成された通り、三角形を含むグループ化された図形を表示します。

## 完全な実行可能サンプル

Putting all pieces together, here is the complete program you can copy, compile, and run:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Prepare a builder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a group shape (300 × 300 points)
        GroupShape group = builder.insertGroupShape(300.0, 300.0);

        // 4. Position the cursor inside the group
        builder.moveTo(group.getFirstParagraph());

        // 5. Insert a triangle shape (60 × 60 points)
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);

        // 6. Save the file – this creates the final Word document
        doc.save("ExtendedGroup.docx");
    }
}
```

### 期待される結果

When you open `ExtendedGroup.docx`, you will see a single group shape occupying the center of the page. Inside that group, a small triangle appears at the default position. The triangle can be selected and moved as part of the group, confirming that **add shapes to word** worked as intended.

## よくある質問とエッジケース

| Question | Answer |
|----------|--------|
| *グループ内に複数の図形を追加できますか？* | はい。三角形を挿入した後、カーソルをグループ内に保ったまま、別の `ShapeType` を指定して `builder.insertShape` を再度呼び出してください。 |
| *三角形を赤にしたい場合はどうすればいいですか？* | `insertShape` が返す `Shape` を取得し、`shape.getFillColor().setColor(Color.RED)` を呼び出します。 |
| *古い .doc ファイルでも動作しますか？* | Aspose.Words は指定した形式で保存します。レガシーな Word 文書を作成するには `doc.save("file.doc", SaveFormat.DOC)` を使用してください。 |
| *グループの枠線を変更するには？* | 枠線をカスタマイズするには、`group.getStrokeColor().setColor(Color.BLUE)` と `group.setLineWeight(2.0)` を使用します。 |
| *三角形を回転させる方法はありますか？* | 角度（度）を設定するには `shape.getRotation()` を呼び出します。 |

## プロのコツ

* **Reuse the builder** – 各図形ごとに新しい `DocumentBuilder` を作成するとオーバーヘッドが増えます。文書ごとにビルダーを1つだけ保持してください。  
* **Unit conversion** – ミリメートルで作業する場合は、ポイントに変換します（`points = mm * 2.83465`）。  
* **Performance** – 大規模な文書では、すべての図形を追加した後に `doc.updatePageLayout()` を一度だけ呼び出してください。

## 結論

これで、Aspose.Words for Java を使用して **create blank document**、**add shapes to Word**、そして特に **how to insert triangle** 図形を行う方法が分かりました。完全なサンプルは、空のファイルからグループ化された三角形を含む **create word document** を保存するまでの全工程を示しています。

ここからは、追加の `ShapeType` 値を調査したり、カスタムスタイルを適用したり、複数のグループを組み合わせて複雑な図を作成したりできます。さまざまなサイズ、色、位置で実験し、Java における Word の自動化を習得してください。

---

*次のレポートを自動化する準備はできましたか？サンプルをクローンし、サイズを調整して、コードを自分のアプリケーションに組み込んでください。*

## 次に学ぶべきことは？

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Aspose.Words for .NET を使用して Word 文書にグループ図形を作成する](/words/english/net/working-with-shapes/add-group-shape/)
- [影付き長方形図形付きの空白 Word 文書を作成する – ステップバイステップガイド](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words を使用して Word に長方形図形を作成する – ステップバイステップガイド](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}