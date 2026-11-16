---
category: general
date: 2026-11-15
description: JavaでWordに長方形の図形を作成し、Wordに図形を追加する方法、図形のサイズを設定する方法、そしてWord文書を効率的に保存する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add shapes to word
- save word document
- set shape dimensions
- define shape size
language: ja
lastmod: 2026-11-15
og_description: Java を使用して Word 文書に長方形の図形を作成します。Word に図形を追加し、図形のサイズを設定し、数分で Word 文書を保存する方法を学びましょう。
og_image_alt: Screenshot showing a rectangle shape inside a group shape in a Word
  document
og_title: JavaでWordに長方形の図形を作成する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  headline: Create rectangle shape in a Word document using Java
  type: TechArticle
- description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  name: Create rectangle shape in a Word document using Java
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well). * Aspose.Words
      for Java 23.10 or newer – you can obtain it from Maven Central. * A basic understanding
      of Java syntax and object‑oriented concepts.'
  - name: Expected output
    text: '* A Word file named `RectangleShapeDemo.docx`. * Inside the first paragraph,
      a group shape containing a 100 pt × 50 pt rectangle. * No text is added, so
      the rectangle appears on a blank page.'
  - name: What’s next?
    text: '* Explore **add shapes to Word** by inserting circles, arrows, or text
      boxes. * Combine multiple shapes into a single `GroupShape` and apply transformations
      (rotate, flip). * Generate reports that embed charts as shapes, then **save
      Word document** as PDF for sharing.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Javaを使ってWord文書に矩形シェイプを作成する
url: /ja/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java を使用して Word ドキュメントに矩形シェイプを作成

Word ファイル内に **矩形シェイプを作成** する必要がある場合、このガイドでは Java を使ってその手順を正確に示します。**Word にシェイプを追加** する方法、**シェイプのサイズを設定** する方法、そして IDE を離れることなく **Word ドキュメントを保存** する方法が分かります。

以下のセクションでは、完全な実行可能サンプル、各行の説明、サイズ問題やドキュメント互換性などの一般的な落とし穴への対策を提供します。外部参照は不要で、Aspose.Words for Java ライブラリだけで完結します。

## 学べること

* `Document` と `DocumentBuilder` の初期化方法。
* **グループシェイプ** を挿入し、その中に矩形を配置する方法。
* `setWidth` と `setHeight` を使用して **シェイプのサイズを定義** する方法。
* `.docx` 形式で **Word ドキュメントを保存** する方法。
* 異なるページサイズや DPI 設定に対するエッジケースの処理方法。

### 前提条件

* Java 17 以降（コードは Java 8 でもコンパイル可能）。
* Aspose.Words for Java 23.10 以降 – Maven Central から入手可能。
* Java の構文とオブジェクト指向の基本的な理解。

> **プロのコツ:** 後で円やテキストボックスなどのシェイプを追加する予定がある場合は、同じ `GroupShape` の中に入れておきましょう。これにより、コレクション全体の移動、回転、書式設定が格段に楽になります。

## 手順 1: ドキュメントとビルダーの初期化

最初のステップは、空の Word ファイルとコンテンツを書き込むための `DocumentBuilder` を作成することです。  

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this matters:* `Document` はファイル全体を表し、`DocumentBuilder` はテキスト、テーブル、**シェイプ** の挿入用の高レベルメソッドを提供します。ビルダーがなければ、低レベルノードを手動で操作する必要があります。

## 手順 2: 複数のシェイプを保持するグループシェイプを挿入

**グループシェイプ** はコンテナのように機能し、複数のシェイプを追加して後で 1 つのオブジェクトとして扱うことができます（例: 一緒に移動や回転）。

```java
        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();
```

*Why use a group shape?* 後で矢印や円、ラベルを矩形の周りに追加したい場合、グループがすべてを整列させたままにしてくれます。また、**Word にシェイプを追加** するワークフローが簡素化され、各新しいシェイプに対して `appendChild` を 1 回呼び出すだけで済みます。

## 手順 3: 矩形シェイプを作成

次に、グループ内に配置する実際の矩形を作成します。`Shape` コンストラクタには所有する `Document` とシェイプの種類が必要です。

```java
        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
```

*Why a rectangle?* `ShapeType.RECTANGLE` は、セクションのハイライト、プレースホルダー作成、または Word 内でシンプルな UI モックアップを描く際に最も一般的に使用されるプリミティブです。

## 手順 4: 矩形のサイズを定義

サイズを設定することが **シェイプのサイズを設定** する重要なポイントです。Aspose.Words がサポートする任意の測定単位を使用できます。デフォルトはポイント (1 pt = 1/72 inch) です。

```java
        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

> **注意:** ミリメートル単位で指定したい場合は、`rectangle.setWidth(ConversionUtil.inchesToPoints(1.39));` のように呼び出します（`1.39 in ≈ 35 mm`）。これにより **シェイプのサイズを定義** する柔軟性が示されます。

## 手順 5: 矩形をグループシェイプに追加

作成した矩形を先に作ったグループに追加すると、ドキュメント内に表示されます。

```java
        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);
```

この時点で矩形はグループの左上隅に配置されています。必要に応じて `rectangle.setLeft(...)` や `rectangle.setTop(...)` で正確な位置に移動できます。

## 手順 6: （オプション）ドキュメントを保存して結果を確認

最後に、ドキュメントをディスクに書き出します。これが **Word ドキュメントを保存** するステップで、`.docx` ファイルが生成され、Microsoft Word、LibreOffice、Google Docs で開くことができます。

```java
        // Step 6: Save the document (optional but recommended for verification)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

プログラムを実行すると `RectangleShapeDemo.docx` が作成され、グループシェイプ内に 1 つの矩形が含まれます。ファイルを開くと、定義したサイズ通りの白い矩形が表示されます。

### 期待される出力

* `RectangleShapeDemo.docx` という名前の Word ファイル。
* 最初の段落内に、100 pt × 50 pt の矩形を含むグループシェイプが配置されている。
* テキストは追加されていないため、矩形は白紙のページ上に表示される。

## 一般的なバリエーションとエッジケース

| 状況 | コードの適応方法 |
|-----------|-----------------------|
| **異なるページサイズ**（例: A4） | シェイプを挿入する前に `document.getFirstSection().getPageSetup().setPaperSize(PaperSize.A4);` を呼び出す。 |
| **印刷用の高 DPI** | 幅・高さに目的の DPI 倍率を掛ける。例: `rectangle.setWidth(200 * 2);` で解像度を 2 倍にする。 |
| **矩形内にテキストラベルを追加** | `TEXT_BOX` タイプの `Shape` を作成し、`setWidth`/`setHeight` を矩形に合わせて設定し、同じ `GroupShape` に追加する。 |
| **矩形を回転** | `rectangle.setRotationAngle(45);` を使用して時計回りに 45 度回転させる。 |
| **DOCX ではなく PDF として保存** | `document.save("output.docx");` を `document.save("output.pdf");` に置き換える。同じ API が PDF でも機能し、矩形が保持される。 |

## 堅牢な実装のためのプロのコツ

1. **ビルダーを再利用** – グループシェイプを挿入した後も、新しいビルダーインスタンスを作らずに段落やテーブルを追加し続けられます。  
2. **リソースを解放** – Java のガベージコレクタがほとんどのオブジェクトを処理しますが、ストリームを使用する場合は `document.close();` を明示的に呼び出すことでファイルハンドル漏れを防げます。  
3. **サイズを検証** – `setWidth`/`setHeight` を呼び出す前に、値が正の数であることを確認してください。負の値は `IllegalArgumentException` をスローします。  
4. **バージョン互換性** – 本コードは Aspose.Words 23.x 以降で動作します。古いバージョンでは `Shape.setSize(width, height)` を使用する必要がある場合があります。

## 完全な実行可能サンプル

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();

        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);

        // Optional: set a light gray fill to make it visible in Word
        rectangle.getFillColor() .setRGB(200, 200, 200);

        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);

        // Step 6: Save the document (you can also save as PDF)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

> **結果の検証:** `output/RectangleShapeDemo.docx` を Microsoft Word で開きます。指定したサイズの矩形がページ上部中央に表示されているはずです。矩形が小さすぎる場合は、`setWidth` と `setHeight` に渡す値を調整してください。

## 結論

これで Java を使用して Word ファイルに **矩形シェイプを作成** し、`GroupShape` を介して **Word にシェイプを追加**、**シェイプのサイズを設定** し、最終的に **Word ドキュメントを保存** する方法が分かりました。同じパターンを他のシェイプタイプにも適用でき、プログラムで複雑な図を構築できます。

### 次にやることは？

* **Word にシェイプを追加** して円や矢印、テキストボックスを挿入してみましょう。  
* 複数のシェイプを 1 つの `GroupShape` にまとめ、回転や反転などの変形を適用します。  
* チャートをシェイプとして埋め込んだレポートを生成し、**Word ドキュメントを PDF として保存** して共有します。

次のシナリオに合わせて、サイズ、色、位置を自由に調整してみてください。ハッピーコーディング！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示したテクニックを基に、さらに関連するトピックを深く掘り下げたものです。各リソースには、完全な動作コード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、独自の実装アプローチを探求したりするのに役立ちます。

- [Word ドキュメント Java 作成 – 影効果付き矩形シェイプの追加](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Java Word ドキュメントで矩形シェイプを作成 – 完全ステップバイステップガイド](/words/english/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/)
- [Word ドキュメント Java 作成 – シェイプを非表示にして塗りつぶし色を設定](/words/english/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}