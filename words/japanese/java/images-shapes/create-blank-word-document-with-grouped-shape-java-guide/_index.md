---
category: general
date: 2026-07-20
description: Aspose.Words を使用して Java で空白の Word ドキュメントを作成します。グループの作成方法、長方形シェイプの挿入方法、シェイプへの画像埋め込み方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create group
- add image word document
- insert rectangle shape
- embed image in shape
language: ja
lastmod: 2026-07-20
og_description: Java と Aspose.Words を使用して空白の Word ドキュメントを作成します。このガイドでは、グループの作成、長方形シェイプの挿入、シェイプへの画像埋め込み方法を示し、動的な
  Word ファイルを作成します。
og_image_alt: Screenshot of a blank Word document containing a grouped shape with
  a rectangle and an embedded image
og_title: グループ化されたシェイプで空白のWord文書を作成 – Javaガイド
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  headline: Create blank word document with grouped shape – Java guide
  type: TechArticle
- description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  name: Create blank word document with grouped shape – Java guide
  steps:
  - name: '`output.docx` appears in the project folder.'
    text: '`output.docx` appears in the project folder.'
  - name: Opening the file shows a single page with a grouped shape.
    text: Opening the file shows a single page with a grouped shape.
  - name: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
    text: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
  - name: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
    text: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: グループ化されたシェイプを持つ空白のWord文書を作成 – Javaガイド
url: /ja/java/images-shapes/create-blank-word-document-with-grouped-shape-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# グループ化されたシェイプを持つ空白のWordドキュメントを作成 – Javaガイド

すでにきれいにグループ化されたシェイプが含まれる **create blank word document** を作成する方法を考えたことはありますか？レポートテンプレートを作成しているか、ロゴとキャプションのプレースホルダーが必要なのかもしれません。どちらにせよ、共通の課題があります：空のファイルから始め、グループを追加し、内部に矩形を配置し、最後に画像を埋め込む—すべてプログラムで行います。

このチュートリアルでは、まさにそれを実現する完全な、すぐに実行できるJava例を順を追って解説します。**how to create group**、**insert rectangle shape**、そして **add image word document** を同じグループ内に追加する方法を学びます。最後には、さらなるカスタマイズが可能な洗練されたテンプレートのようなWordファイルが手に入ります。

> **What you’ll get:** 完全に機能するJavaクラス、ステップバイステップの解説、ファイルパス処理のヒント、そして期待される出力のプレビューが得られます。外部ドキュメントは不要です—必要なものはすべてここにあります。

---

## 空白のWordドキュメントを作成 – 手順概要

最初に必要なのは、完全に空白のWordファイルです。Aspose.Words を使えばこれが簡単にできます：`Document` クラスをデフォルトコンストラクタでインスタンス化するだけです。これにより、Word を開いて **New → Blank document** をクリックしたのと同じクリーンなキャンバスが得られます。

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Why start with a blank document?**  
> 空白のドキュメントを使用することで、後で追加するシェイプに影響を与える隠れたスタイルやセクションが存在しないことが保証されます。また、ファイルサイズを最小限に抑えることができ、バッチジョブで多数のファイルを生成する際に便利です。

---

## グループを作成しシェイプを追加する方法

**group shape** は本質的に複数の子シェイプを保持できるコンテナで、描画オブジェクト用のフォルダーと考えてください。グループ化することで、単一のコマンドで全体を移動、サイズ変更、回転させることができます。

```java
        // 2️⃣ Insert a group shape 200x200 points
        GroupShape group = builder.insertGroupShape(200.0, 200.0);
```

`insertGroupShape` メソッドは `GroupShape` オブジェクトを返し、矩形と画像の親として使用します。サイズはポイントで表され（1ポイント = 1/72インチ）、200ポイントは約 2.78 × 2.78 インチのボックスになります。

> **Pro tip:** グループを透明にしたい場合は、作成後に `group.setFillColor(Color.getWhite());` を設定してください。

グループが作成されたので、次のシェイプを配置する場所をビルダーに指示する必要があります。ビルダーのカーソルはグループの最初の段落内に位置している必要があります。

```java
        // Move the cursor to the first paragraph of the group
        builder.moveTo(group.getFirstParagraph());
```

---

## グループ内に矩形シェイプを挿入する

矩形はテキストのプレースホルダーや視覚的なヒントとしてよく使用されます。**first child** としてグループに追加することで、後続の画像の背後に配置されます。

```java
        // 3️⃣ Insert a rectangle (100x50 points) as the first child
        builder.insertShape(ShapeType.RECTANGLE, 100.0, 50.0);
```

矩形はグループの座標系を継承するため、デフォルトで 100 × 50 ポイントのサイズが中央に配置されます。返された `Shape` オブジェクトにアクセスして、境界線を追加したり、塗りつぶし色を変更したり、影を適用したりしてさらにスタイルを設定できます。

```java
        // Optional styling (commented out for brevity)
        // Shape rect = builder.getCurrentShape();
        // rect.setFillColor(Color.getLightGray());
        // rect.setStrokeColor(Color.getBlack());
```

---

## 画像をWordドキュメントに追加 – シェイプに画像を埋め込む

さあ、楽しいパートです：**embed image in shape**。同じグループの第二子として JPEG 画像を挿入します。カーソルがまだグループ内にあるため、画像は自動的に子ノードになります。

```java
        // 4️⃣ Insert an image (make sure the path is correct)
        builder.insertImage("sample.jpg");   // <-- replace with your image path
```

画像ファイルが見つからない場合、Aspose.Words は `FileNotFoundException` をスローします。回避するには、`sample.jpg` をプロジェクトの作業ディレクトリに置くか、絶対パスを使用してください。

> **What if you need a different image format?**  
> Aspose.Words は PNG、BMP、GIF、TIFF、さらには SVG もサポートしています。ファイル拡張子を変更すれば、ライブラリが自動的に変換を行います。

---

## ドキュメントを保存して結果を確認する

最後に、メモリ上のドキュメントをディスクに保存します。生成された `.docx` には、矩形と画像の両方を保持するグループ化されたシェイプが1ページに含まれます。

```java
        // 5️⃣ Save the document to verify the output
        doc.save("output.docx");
    }
}
```

`output.docx` を Microsoft Word で開くと、左上隅に 200 × 200 ポイントのグループが表示されます。グループ内には、上部に薄いグレーの矩形があり、そのすぐ下に指定した画像が完璧に揃って表示されます。

![Grouped shape example](grouped-shape.png){:alt="矩形と埋め込み画像を含むグループ化シェイプがある空白のWordドキュメントのスクリーンショット"}

---

## 一般的なバリエーションとエッジケースの処理

| シナリオ | 変更点 | 重要な理由 |
|----------|----------------|----------------|
| **Different group size** | `insertGroupShape(width, height)` のパラメータを調整する | 大きなグループは、より複雑なレイアウトを収容できます。 |
| **Multiple images** | 毎回グループの段落に移動した後、`builder.insertImage()` を繰り返し呼び出す | 呼び出すたびに新しい子が追加され、`Shape.setLeft()` / `setTop()` で位置を調整できます。 |
| **Dynamic image paths** | `String.format("images/%s.jpg", imageName)` を使用する | バッチ処理でコードを再利用しやすくなります。 |
| **Saving as PDF** | `doc.save("output.pdf")` に置き換える | Aspose.Words はリアルタイムで変換でき、直接PDFを生成できます。 |
| **Rotating the group** | `group.setRotation(45);` を使用する | 装飾的な透かしやスタイリッシュなヘッダーに便利です。 |

---

## 期待される出力と検証

クラスを実行した後：

1. `output.docx` がプロジェクトフォルダーに作成されます。  
2. ファイルを開くと、グループ化されたシェイプがある単一ページが表示されます。  
3. グループ内では、矩形が左上に配置され、画像がそのすぐ下に表示されます。  
4. Word でグループを選択すると、両方の子オブジェクトがハイライトされ、正しくグループ化されていることが確認できます。

これらの手順のいずれかが失敗した場合は、画像パスを再確認し、Aspose.Words の JAR がクラスパスに含まれていることを確認してください。

---

## 結論

これで **how to create blank word document** を作成し、矩形と埋め込み画像を含むグループ化シェイプで強化する方法が分かりました。**how to create group**、**insert rectangle shape**、そして **add image word document** を習得すれば、コードだけで高度なWordテンプレートを構築でき、手動での調整は不要です。

次のチャレンジに挑みますか？同じグループ内にテキストボックスを追加したり、企業のブランディングに合わせてさまざまなシェイプスタイルを試したりしてみてください。さらに、このレイアウトで始まるドキュメントを多数生成し、レポートライブラリ全体を作成することも可能です。

コーディングを楽しんでください。そして、以下のコメント欄であなたのバリエーションをぜひ共有してください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説付きの完全な動作コード例が含まれており、追加のAPI機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [JavaでWordドキュメントを作成 – 影効果付き矩形シェイプの追加](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words for JavaでDocumentBuilderを使用してフォームフィールドを作成しコンテンツを追加する方法](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words for JavaでPDFドキュメントを作成する方法 | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}