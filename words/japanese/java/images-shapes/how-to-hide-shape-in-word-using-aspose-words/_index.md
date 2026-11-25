---
category: general
date: 2026-11-25
description: Aspose.Words を使用して Word で図形を非表示にし、数行のコードで矩形の図形を挿入しながら Word 文書の作成方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- hide shape in word
- create word document aspose
- insert rectangle shape word
- Aspose.Words shape handling
- hide Word objects programmatically
language: ja
lastmod: 2026-11-25
og_description: Aspose.Words を使用して Word で図形を非表示にする。このチュートリアルでは、Aspose で Word 文書を作成し、長方形の図形を挿入してプログラムで非表示にする方法を示します。
og_image_alt: Screenshot of a hidden rectangle shape inside a Word document created
  with Aspose.Words
og_title: Aspose.WordsでWordのシェイプを非表示にする – クイックステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Hide shape in Word with Aspise.Words and learn to create Word document
    aspose while you insert rectangle shape word in just a few lines of code.
  headline: How to hide shape in Word using Aspose.Words
  type: TechArticle
- description: Hide shape in Word with Aspise.Words and learn to create Word document
    aspose while you insert rectangle shape word in just a few lines of code.
  name: How to hide shape in Word using Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17+ (or .NET 6+ if you prefer C#—the API calls are analogous). *
      Aspose.Words for Java 24.x (the latest version at the time of writing). * An
      IDE such as IntelliJ IDEA, Eclipse, or VS Code.'
  - name: Create a Word document aspose
    text: First, instantiate a blank `Document` and a `DocumentBuilder`. The builder
      provides a fluent API for adding content, including shapes.
  - name: Insert rectangle shape word
    text: Now we add a rectangle shape. The `insertShape` method requires the shape
      type and its dimensions in points (1 point = 1/72 inch).
  - name: Hide the shape so it does not appear in the layout
    text: Aspose.Words mirrors the Microsoft Word *Hidden* attribute. Setting it to
      `true` tells Word to omit the shape from rendering, while keeping the object
      in the document structure.
  - name: Save and verify the result
    text: Finally, write the document to disk. Open the file in Microsoft Word to
      confirm that the rectangle is not visible. You can also inspect the underlying
      XML to see the hidden flag.
  - name: (Optional) Unhide the shape later
    text: If you need to make the shape visible again, load the document, locate the
      shape, and set `hidden` to `false`.
  - name: What the output files contain
    text: '* **HideShapeResult.docx** – the rectangle is hidden; the page looks empty.
      * **UnhiddenShape.docx** – the same rectangle is visible, showing a red box
      with a black outline.'
  - name: Next steps
    text: '* Explore **conditional content** by combining hidden shapes with mail‑merge
      fields. * Learn how to **hide text runs** (`Run.setHidden(true)`) for more granular
      control. * Check the Aspose.Words documentation on **document protection** to
      prevent users from accidentally unhiding shapes.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape manipulation
title: Aspose.Words を使用して Word で図形を非表示にする方法
url: /ja/java/images-shapes/how-to-hide-shape-in-word-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words を使用して Word でシェイプを非表示にする方法

プログラムでドキュメントを生成する際に **hide shape in Word** が必要な場合、Aspose.Words を使えば簡単に実現できます。このガイドでは、Word document aspose の作成方法、rectangle shape word の挿入方法、そしてそのシェイプをレイアウトに表示されないように非表示にする手順を詳しく解説します。完全な実行可能サンプルが用意されているので、IDE にコピーペーストしてすぐに結果を確認できます。

このチュートリアルを終えると、隠し矩形が含まれた Word ファイルが作成されます。プレースホルダーや条件付きコンテンツ、読者に見せたくないメタデータなどに便利です。必要なのは Aspose.Words for Java（または .NET）ライブラリだけで、外部ツールは不要です。

## 学べること

* **create a Word document aspose** をゼロから作成する方法。  
* `DocumentBuilder` を使用して **insert rectangle shape word** を挿入する方法。  
* シェイプの `hidden` プロパティを設定し、最終レイアウトに描画されないようにする方法。  
* シェイプが非表示であることを確認し、必要に応じて再表示する方法。  

### 前提条件

* Java 17+（または C# が好みの場合は .NET 6+—API 呼び出しは同様です）。  
* Aspose.Words for Java 24.x（執筆時点での最新バージョン）。  
* IntelliJ IDEA、Eclipse、VS Code などの IDE。  

> **プロのコツ:** 商用ライセンスをまだお持ちでない場合は、Aspose の無料一時ライセンスを使用してください。評価目的であればライセンスなしでも動作しますが、ライセンスを適用すると評価用の透かしが除去されます。

## Aspose.Words で Word のシェイプを非表示にする

基本的な手順は次の通りです。

1. **新しい `Document` を作成する。**  
2. **`DocumentBuilder` を使って矩形シェイプを挿入する。**  
3. **シェイプを hidden とマークし、ファイルを開いたときに表示されないようにする。**  

以下で各ステップをコード例とともに解説します。

### Step 1: Create a Word document aspose

まず、空の `Document` と `DocumentBuilder` をインスタンス化します。ビルダーはコンテンツ追加用のフルエント API を提供し、シェイプを含むさまざまな要素を簡単に挿入できます。

```java
// Step 1: Create a new document and a DocumentBuilder to work with it
import com.aspose.words.*;

public class HideShapeExample {
    public static void main(String[] args) throws Exception {
        // Load a free evaluation license (optional for production)
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Create an empty Word document
        Document doc = new Document();

        // DocumentBuilder lets us add text, tables, shapes, etc.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**このポイントが重要な理由:**  
新しい `Document` を作成すると、クリーンなキャンバスが得られます。`DocumentBuilder` は現在の挿入位置を自動で管理し、セクションやページの処理も自動で行ってくれるため、ドキュメントの変更に最適です。

### Step 2: Insert rectangle shape word

次に矩形シェイプを追加します。`insertShape` メソッドはシェイプの種類とサイズ（ポイント単位、1 ポイント = 1/72 インチ）を指定します。

```java
        // Step 2: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

        // Optional: give the shape a visible fill and outline so you can see it before hiding
        rectangle.getFillColor().setRGB(255, 0, 0); // red fill
        rectangle.getStroke().setColor(java.awt.Color.BLACK);
        rectangle.getStroke().setWeight(1.0);
```

**このポイントが重要な理由:**  
`insertShape` はドキュメントの *drawing* パートに描画オブジェクトを作成します。サイズを指定することで、シェイプが可視の場合に占有する領域をコントロールできます。オプションのスタイリングを設定すれば、非表示にする前にシェイプを確認できます。

### Step 3: Hide the shape so it does not appear in the layout

Aspose.Words は Microsoft Word の *Hidden* 属性をサポートしています。`true` に設定すると、シェイプはレンダリングから除外されますが、ドキュメント構造内には残ります。

```java
        // Step 3: Hide the shape so it does not appear in the layout
        rectangle.setHidden(true);
```

**このポイントが重要な理由:**  
非表示シェイプはプログラムから引き続きアクセス可能で（例: 条件付き処理）、後からプロパティを切り替えて表示させることができます。**conditional placeholders** のように、特定の読者向けにのみ表示したい要素に最適です。

### Step 4: Save and verify the result

最後にドキュメントをディスクに保存します。Microsoft Word でファイルを開き、矩形が表示されていないことを確認してください。XML を直接確認すれば、hidden フラグが設定されていることが分かります。

```java
        // Save the document
        String outPath = "HideShapeResult.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

**期待される出力:**  
プログラム実行時に次のように出力されます。

```
Document saved to HideShapeResult.docx
```

Word で *HideShapeResult.docx* を開くと、ページは空（またはシェイプの前に追加した他のコンテンツ）に見えます。矩形はファイルの XML 内（`<w:hidden>` 属性）に存在しますが、描画はされません。

### Step 5: (Optional) Unhide the shape later

シェイプを再度表示したい場合は、ドキュメントを読み込み対象シェイプを取得し、`hidden` を `false` に設定します。

```java
        // Load the document again
        Document loadedDoc = new Document(outPath);
        Shape hiddenRect = (Shape) loadedDoc.getChild(NodeType.SHAPE, 0, true);
        hiddenRect.setHidden(false);
        loadedDoc.save("UnhiddenShape.docx");
```

**このポイントが重要な理由:**  
hidden フラグをトグルできることで、動的なドキュメント生成に柔軟性が生まれます。たとえば、すべてのオプション要素を非表示にしたマスタードキュメントを作成し、ユーザーの選好に応じて個別に表示させることが可能です。

## 完全な実行可能サンプル（create word document aspose, insert rectangle shape word, hide shape）

以下に、コンパイルしてすぐに実行できる完全プログラムを示します。

```java
// HideShapeExample.java
import com.aspose.words.*;

public class HideShapeExample {
    public static void main(String[] args) throws Exception {
        // ---- License (optional for evaluation) ----
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // ---- Step 1: Create a new document ----
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // ---- Step 2: Insert rectangle shape ----
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle.getFillColor().setRGB(255, 0, 0); // red fill for visual check
        rectangle.getStroke().setColor(java.awt.Color.BLACK);
        rectangle.getStroke().setWeight(1.0);

        // ---- Step 3: Hide the shape ----
        rectangle.setHidden(true);

        // ---- Step 4: Save the document ----
        String outPath = "HideShapeResult.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);

        // ---- Optional Step 5: Unhide and save a second file ----
        Document loadedDoc = new Document(outPath);
        Shape hiddenRect = (Shape) loadedDoc.getChild(NodeType.SHAPE, 0, true);
        hiddenRect.setHidden(false);
        loadedDoc.save("UnhiddenShape.docx");
        System.out.println("Unhidden document saved to UnhiddenShape.docx");
    }
}
```

**コードの実行方法**

```bash
javac -cp "aspose-words-24.10.jar" HideShapeExample.java
java -cp ".:aspose-words-24.10.jar" HideShapeExample
```

`aspose-words-24.10.jar` を、ダウンロードした実際のバージョンに置き換えてください。

### 出力ファイルの内容

* **HideShapeResult.docx** – 矩形が非表示になり、ページは空白に見えます。  
* **UnhiddenShape.docx** – 同じ矩形が表示され、赤いボックスと黒いアウトラインが確認できます。

## よくある質問とエッジケースの対処

| 質問 | 回答 |
|----------|--------|
| *非表示シェイプはページ割り付けに影響しますか？* | 影響しません。非表示オブジェクトはレイアウトエンジンに無視されるため、テキストが新しいページに押し出されることはありません。 |
| *画像や表など、他の Word オブジェクトも非表示にできますか？* | できます。`Shape`、`Paragraph`、`Run` など多くの `Node` サブクラスは `setHidden(boolean)` メソッドを提供しています。 |
| *既にシェイプが存在するドキュメントの場合は？* | `doc.getChildNodes(NodeType.SHAPE, true)` を使用してすべてのシェイプを列挙し、対象のシェイプだけを非表示にできます。 |
| *シェイプを非表示にするとファイルサイズは増えますか？* | わずかに増加しますが、シェイプの XML が残るだけなので、通常の文書では影響はほとんどありません。 |
| *PDF に変換したときに hidden フラグは保持されますか？* | PDF 変換時はデフォルトで非表示シェイプは除外されます。必要に応じて `PdfSaveOptions` で制御可能です。 |

## 非表示オブジェクトを扱う際のベストプラクティス

* `setName("MyPlaceholder")` でシェイプに名前を付けると、後から検索しやすくなります。  
* 複数の非表示要素を一括で切り替える必要がある場合は、`GroupShape` にまとめて管理します。  
* コメントや別ファイルの仕様書に、非表示要素の目的を明記しておくと、将来の保守担当者が理解しやすくなります。  
* 非表示オブジェクトの使いすぎは文書の複雑性を高め、XML を手動で確認するユーザーを混乱させる可能性があるため、適度に利用しましょう。  

## 結論

これで **hide shape in Word** を Aspose.Words で実装する方法、**create Word document aspose** の手順、そして **insert rectangle shape word** の後にシェイプを非表示にする方法が分かりました。サンプルは作成、挿入、非表示、保存、そして必要に応じた再表示というフルライフサイクルを示しています。動的レポートや条件付きテンプレート、見えないプレースホルダーが必要な自動化 Word ワークフローにぜひ活用してください。

### 次のステップ

* 隠しシェイプとメールマージ フィールドを組み合わせて **conditional content** を実装してみましょう。  
* より細かい制御が必要な場合は、テキストランの非表示（`Run.setHidden(true)`）も学んでみてください。  
* ユーザーが誤ってシェイプを表示しないようにするため、**document protection** に関する Aspose.Words のドキュメントも確認してみましょう。  

Happy coding, and let your generated Word files stay clean while still carrying the hidden data you need!

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれているので、API の追加機能を習得したり、別の実装アプローチを自分のプロジェクトに取り入れたりするのに役立ちます。

- [Create a Word document programmatically, add and hide a shape in Java using Aspose.Words](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [How to hide shape in a Word document using Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Create a blank .docx Word document and add a hidden rectangle shape with Aspose.Words](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}