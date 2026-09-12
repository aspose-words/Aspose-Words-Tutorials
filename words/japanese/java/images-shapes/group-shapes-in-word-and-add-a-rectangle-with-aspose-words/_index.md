---
category: general
date: 2026-09-11
description: Aspose.Words for Java を使用して Word で図形をグループ化し、長方形の図形を追加します。図形のサイズ設定、オブジェクトのグループ化、ドキュメントの保存方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- how to group shapes
- how to add rectangle
language: ja
lastmod: 2026-09-11
og_description: Wordで図形をグループ化し、Aspose.Words for Javaを使用して長方形の図形を追加します。このチュートリアルでは、図形のサイズ設定、図形のグループ化、そしてドキュメントのエクスポート方法を示します。
og_image_alt: Screenshot showing grouped shapes in a Word document
og_title: Wordでシェイプをグループ化 – Aspose.Wordsで矩形を追加
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  headline: Group shapes in Word and add a rectangle with Aspose.Words
  type: TechArticle
- description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  name: Group shapes in Word and add a rectangle with Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17 or later installed. * Maven or Gradle to manage dependencies.
      * A valid Aspose.Words for Java license (or a free evaluation key). * An image
      file (`sample.png`) placed in a known directory (replace `YOUR_DIRECTORY` with
      your actual path).'
  - name: Add a group shape
    text: A group shape is a container that can hold other shapes. Think of it as
      a folder for drawing objects.
  - name: How to add rectangle
    text: The code above demonstrates **how to add rectangle** by creating a `Shape`
      instance with `ShapeType.RECTANGLE` and then appending it to the `GroupShape`.
      This pattern works for any other shape type (e.g., `ELLIPSE`, `POLYLINE`).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Wordで図形をグループ化し、Aspose.Wordsで矩形を追加する
url: /ja/java/images-shapes/group-shapes-in-word-and-add-a-rectangle-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word でシェイプをグループ化し、Aspose.Words で矩形を追加する

Word で **シェイプをグループ化** しながらプログラムで矩形を追加したい場合、このガイドは完全に実行可能なソリューションを提供します。グループシェイプの挿入方法、矩形シェイプの追加方法、シェイプサイズの設定方法、そしてドキュメントを保存してすぐに結果を確認する手順をすべて解説します。

Word 文書を扱う際は、画像、チャート、シンプルな幾何シェイプなど複数のオブジェクトを 1 つの論理単位にまとめることがよくあります。オブジェクトをグループ化すると、まとめて移動、回転、スタイル設定が容易になります。このチュートリアルでは **矩形シェイプの追加** と **シェイプサイズの設定** についても取り上げ、レイアウトを正確にコントロールできるようにします。

## 学べること

* Aspose.Words for Java を使って新しい Word 文書を作成する方法。  
* **シェイプをグループ化** して単一オブジェクトとして扱う方法。  
* グループに **矩形シェイプを追加** し、同じグループに画像を挿入する方法。  
* 矩形と画像の **シェイプサイズを設定** する方法。  
* 文書を保存し、Microsoft Word で結果を確認する手順。

### 前提条件

* Java 17 以降がインストールされていること。  
* Maven または Gradle で依存関係を管理できること。  
* 有効な Aspose.Words for Java ライセンス（または無料評価キー）。  
* 既知のディレクトリに配置した画像ファイル（`sample.png`）（`YOUR_DIRECTORY` を実際のパスに置き換えてください）。

---

## Aspose.Words を使用して Word でシェイプをグループ化する方法

最初のステップは `Document` と `DocumentBuilder` を作成することです。`DocumentBuilder` はシェイプやテキスト、その他の要素を挿入するための便利な API を提供します。

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Initialize the document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **ポイント:** `DocumentBuilder` は基になる `Document` オブジェクトと直接連携し、低レベルのノードコレクションを手動で扱うことなくシェイプを挿入できます。

### グループシェイプを追加

グループシェイプは他のシェイプを保持できるコンテナです。描画オブジェクト用のフォルダーと考えてください。

```java
        // Insert an empty group shape – this will hold the rectangle and the picture
        GroupShape group = builder.insertGroupShape();
```

`insertGroupShape()` メソッドは `GroupShape` ノードを作成し、後で子シェイプを追加できるように返します。  

---

## グループに矩形シェイプを追加

ここでは、先ほど作成したグループに **矩形シェイプを追加** します。矩形は画像の背景または枠として機能します。

```java
        // Create a rectangle shape with a specific size
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points
        rectangle.setHeight(50.0);   // height in points
        rectangle.setFillColor(java.awt.Color.LIGHT_GRAY);
        rectangle.setStrokeColor(java.awt.Color.DARK_GRAY);
        rectangle.setStrokeWeight(1.0);
        // Append the rectangle to the group
        group.appendChild(rectangle);
```

> **ヒント:** `FillColor` と `StrokeColor` を設定すると、最終文書で矩形が見えるようになります。これらのプロパティを省略するとシェイプが透明になる可能性があります。

### 矩形の追加方法

上記コードは、`ShapeType.RECTANGLE` を指定して `Shape` インスタンスを作成し、`GroupShape` に追加することで **矩形を追加** する方法を示しています。このパターンは `ELLIPSE` や `POLYLINE` など、他のシェイプタイプでも同様に機能します。

---

## 矩形と画像のシェイプサイズを設定

適切なサイズ設定により、矩形と画像が正しく整列します。ここでは、次に挿入する画像の **シェイプサイズも設定** します。

```java
        // Insert an image and set its size
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.png");
        picture.setWidth(100.0);   // match rectangle width
        picture.setHeight(50.0);   // match rectangle height
        // Append the picture to the same group
        group.appendChild(picture);
```

矩形も画像も同じ寸法（100 × 50 ポイント）になりました。同じグループに属しているため、グループ全体を移動または回転させると、両方のシェイプが同時に変化します。

> **サイズを合わせる理由:** 寸法を揃えることで、画像が矩形の内部にきれいに収まり、整った「フレーム付き画像」効果が得られます。

---

## 文書を保存して結果を確認

最後に、文書をディスクに書き出します。Microsoft Word でファイルを開くと、グループ化されたシェイプが単一の選択可能オブジェクトとして表示されます。

```java
        // Save the document – the group will appear as one object in Word
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

`output.docx` を開くと、画像が内部に入った矩形が表示されます。シェイプをクリックすると、矩形と画像の両方が **グループ化** されているため同時に選択されます。

![group shapes in word example](https://example.com/images/group-shapes-word.png "group shapes in word example")

*画像代替テキスト:* *group shapes in word example* – グループ化された矩形と画像を示す Word 文書の例。

---

## よくある質問とエッジケースの対処

| 質問 | 回答 |
|----------|--------|
| **画像のサイズを別にしたい場合は？** | 挿入後に `picture.setWidth()` と `picture.setHeight()` を調整します。矩形は元のサイズのままにするか、同様にリサイズできます。 |
| **同じグループにさらにシェイプを追加できますか？** | はい。追加したい `Shape` オブジェクトに対して `group.appendChild(newShape)` を呼び出します。 |
| **グループ全体を回転させるには？** | `group.setRotationAngle(double angleInRadians)` を使用します。回転はすべての子シェイプに適用されます。 |
| **画像ファイルが見つからない場合は？** | `insertImage` は `FileNotFoundException` をスローします。try‑catch で囲み、代替のプレースホルダーシェイプを提供してください。 |
| **後でグループ化を解除できますか？** | `group.removeAllChildren()` で子要素を分離し、個別に文書へ再挿入できます。 |

---

## 結論

これで **Word でシェイプをグループ化** し、**矩形シェイプを追加**、**シェイプサイズを設定**、そして Aspose.Words for Java を使って文書を **保存** する完全な実行例が完成しました。矩形と画像をグループ化することで、1 つの単位として移動、リサイズ、回転が可能になり、多くの文書自動化シナリオで求められる操作が実現できます。

次に試すべきこと:

* 同じグループにテキストボックスを追加（`how to add rectangle` スタイルのテキスト）。  
* 異なる塗りつぶしパターンやグラデーションを適用（`set shape size` とスタイリングの組み合わせ）。  
* 同様の手法でチャート、テーブル、SmartArt をグループ化（他のオブジェクトタイプで `how to group shapes` を活用）。  

他のシェイプタイプや色、レイアウトオプションでも自由に実験してください。コーディングを楽しんでください！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、独自プロジェクトで代替実装を検討したりするのに役立ちます。

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}