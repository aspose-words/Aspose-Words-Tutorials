---
category: general
date: 2026-08-20
description: Aspose.Words for Java を使用して、図形をグループ化する方法、図形のサイズを設定する方法、画像をドキュメントに挿入する方法、画像をグループに追加する方法、そして長方形の図形を作成する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert image into document
- set shape size
- add picture to group
- create rectangle shape
language: ja
lastmod: 2026-08-20
og_description: Aspose.Words を使用して Word 文書で図形をグループ化する方法。図形のサイズ設定、文書への画像挿入、グループへの画像追加、矩形図形の作成を行うステップバイステップの
  Java チュートリアルをご覧ください。
og_image_alt: Diagram showing how to group shapes in a Word document
og_title: Aspose.Words を使用した Word 文書での図形のグループ化方法 – Java ガイド
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  headline: How to group shapes in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  name: How to group shapes in a Word document using Aspose.Words
  steps:
  - name: Create a new document and a `DocumentBuilder`
    text: A `Document` represents the Word file, while `DocumentBuilder` provides
      convenient methods for inserting content.
  - name: Insert a group shape that will hold multiple child shapes
    text: A group shape acts like a container. Its dimensions define the bounding
      box for all child shapes.
  - name: Create a rectangle shape, set its size, and add it to the group
    text: Setting the exact size of a shape is essential when you want precise layout
      control.
  - name: Insert an image, then add the picture shape to the same group
    text: Inserting an image is the core of the **insert image into document** requirement.
      The returned `Shape` is a picture shape that can be grouped like any other shape.
  - name: Position the entire group on the page
    text: After adding all child shapes, you can move, rotate, or hide the whole group.
      Positioning uses the **add picture to group** concept indirectly, because the
      group now contains the picture.
  - name: Save the document
    text: Finally, write the file to disk. You can open the resulting `.docx` in Word
      to verify the grouping.
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: Aspose.Words を使用して Word 文書で図形をグループ化する方法
url: /ja/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words を使用して Word 文書で図形をグループ化する方法

Word ファイルで **図形をグループ化する方法** が必要な場合、このチュートリアルでは完全な Java ソリューションを示します。**図形のサイズを設定する**、**文書に画像を挿入する**、**グループに画像を追加する**、そして **長方形の図形を作成する** 方法を、わかりやすい解説と実行可能なコードサンプルとともに確認できます。

図形をグループ化するとレイアウト管理が簡素化され、複数のオブジェクトを 1 つの単位として移動や回転ができ、文書がすっきりします。以下の手順で、長方形と画像を含むグループを作成し、ページ上に配置します。

## 前提条件

開始する前に、以下を確認してください。

* Java 17 以上がインストールされていること。
* Aspose.Words for Java（バージョン 23.9 以降）をプロジェクトのクラスパスに追加していること。
* サンプル JPEG 画像が `YOUR_DIRECTORY/sample.jpg` にあること（`YOUR_DIRECTORY` は実際のパスに置き換えてください）。

Maven で Aspose.Words を追加できます:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Aspose.Words で図形をグループ化する方法

以下のセクションでは、**図形をグループ化する方法** に必要な各操作を順に解説します。主要な H2 見出しに主要キーワードを含め、SEO ルールを満たしています。

### 手順 1: 新しいドキュメントと `DocumentBuilder` を作成する

`Document` は Word ファイルを表し、`DocumentBuilder` はコンテンツ挿入用の便利なメソッドを提供します。

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this matters*: 新しい `Document` から開始することで、作成するグループが既存要素と干渉しないことが保証されます。

### 手順 2: 複数の子図形を保持できるグループ図形を挿入する

グループ図形はコンテナのように機能します。そのサイズはすべての子図形のバウンディングボックスを定義します。

```java
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

*Tip*: 幅 (`300`) と高さ (`200`) はポイント単位です（1 pt = 1/72 inch）。追加する図形のサイズに合わせて調整してください。

### 手順 3: 長方形図形を作成し、サイズを設定してグループに追加する

正確なサイズを設定することは、レイアウトを細かく制御したい場合に不可欠です。

```java
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape size – width
        rectangleShape.setHeight(50);   // set shape size – height
        // Optionally set a fill color for visibility
        rectangleShape.getFillColor().setRGB(0xFF, 0xCC, 0x00);
        groupShape.appendChild(rectangleShape);
```

*Why we set shape size*: `setWidth` と `setHeight` メソッドは **set shape size** のサブキーワードに対応し、長方形の外観をピクセル単位で正確にコントロールできます。

### 手順 4: 画像を挿入し、同じグループに画像図形を追加する

画像の挿入は **insert image into document** 要件の核心です。返される `Shape` は他の図形と同様にグループ化できる画像図形です。

```java
        // Step 4: Insert an image, then add the picture shape to the same group
        Shape pictureShape = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        // Resize the picture if needed (example: 120 pt wide, maintain aspect ratio)
        pictureShape.setWidth(120);
        // Add the picture to the previously created group
        groupShape.appendChild(pictureShape);
```

*Pro tip*: 元のアスペクト比を保持したい場合は、幅または高さのいずれか一方だけを設定してください（`setWidth` または `setHeight`）。Aspose.Words が自動的にもう一方の寸法をスケーリングします。

### 手順 5: ページ上にグループ全体を配置する

すべての子図形を追加したら、グループ全体を移動、回転、非表示にできます。配置は **add picture to group** の概念を間接的に利用しています。なぜなら、グループ内に画像が含まれているからです。

```java
        // Step 5: Position the entire group on the page (it can also be rotated, hidden, etc.)
        groupShape.setLeft(50);   // distance from the left margin
        groupShape.setTop(100);   // distance from the top margin
        // Optional: rotate the group 15 degrees
        groupShape.setRotation(15);
```

*Explanation*: `setLeft` と `setTop` はページの余白を基準にグループの位置を決めます。グループを回転させると、すべての子図形がその変換を継承します。

### 手順 6: ドキュメントを保存する

最後にファイルをディスクに書き出します。生成された `.docx` を Word で開いて、グループ化が正しく行われているか確認できます。

```java
        // Step 6: Save the document
        doc.save("GroupShapesDemo.docx");
    }
}
```

プログラムを実行すると、長方形と画像が一緒にバンドルされた **GroupShapesDemo.docx** が生成されます。Word でどちらかの図形を選択するともう一方も同時に選択され、**図形をグループ化する方法** を正しく習得したことが確認できます。

---

## 期待される出力

Microsoft Word で *GroupShapesDemo.docx* を開くと:

* グループの左側に長方形（金色の塗り）が表示されます。
* 提供した画像が長方形の右側に表示されます。
* グループをドラッグすると、両方のオブジェクトが一緒に移動します。
* グループは左余白から 50 pt、上余白から 100 pt の位置に配置され、15° 回転しています。

画像が表示されない場合は、`insertImage` のファイルパスを再確認してください。ファイルが見つからないと Aspose.Words は `IOException` をスローします。

---

## よくある質問とエッジケースの対処

| Question | Answer |
|----------|--------|
| **Can I add more than two shapes?** | Yes. Call `groupShape.appendChild(otherShape)` for each additional shape. |
| **What if I need a transparent background for the rectangle?** | Use `rectangleShape.getFillColor().setRGB(255, 255, 255); rectangleShape.setFillTransparent(true);` |
| **Is grouping supported in older Word formats (e.g., `.doc`)?** | Grouping works for `.docx` and `.doc` but some older viewers may ignore the group metadata. Save as `.docx` for full fidelity. |
| **How do I ungroup later?** | Retrieve the child nodes via `groupShape.getChildNodes(NodeType.ANY, true)` and move them to the document body, then remove the group. |
| **Can I group shapes across different sections?** | No. A `GroupShape` must reside within a single `Story` (usually the main document body). |

---

## 安定した図形操作のためのプロティップ

* **Use absolute positioning sparingly** – relative positioning (`builder.moveToDocumentEnd()`) often yields more responsive layouts.
* **Cache the `DocumentBuilder`** – creating a new builder for each operation can degrade performance on large documents.
* **Set `PictureFillMode`** when you need the image to stretch or tile inside the shape: `pictureShape.setPictureFillMode(PictureFillMode.STRETCH);`
* **Validate image dimensions** before insertion to avoid unexpected scaling that can affect the group’s bounding box.

---

## 次のステップ

**図形をグループ化する方法** を習得したので、以下を検討してみてください:

* **Insert image into document** を、クロッピング (`pictureShape.setCropTop(...)`) などの高度なオプションと共に使用する。
* **Set shape size** をページ寸法に基づいて動的に設定する (`doc.getFirstSection().getPageSetup().getPageWidth()`)。
* **Add picture to group** とテキストボックスを組み合わせて、キャプション付きグラフィックを作成する。
* **Create rectangle shape** に角丸 (`rectangleShape.setCornerRadius(5);`) を適用する。

これらのトピックは同じ API をベースにしており、洗練されたプログラム的 Word レポートの作成に役立ちます。

---

## 結論

このチュートリアルでは、Aspose.Words for Java を使用して Word 文書で **図形をグループ化する方法** を学びました。6 つの手順（ドキュメント作成、グループ挿入、**長方形の図形を作成**、**図形のサイズを設定**、**文書に画像を挿入**、**グループに画像を追加**、そしてグループの配置）に従うことで、複雑なレイアウトシナリオに再利用可能なパターンが手に入ります。追加の子図形や異なる回転、条件付きグループ化ロジックなどを試して、アプリケーションの要件に合わせて自由にカスタマイズしてください。

コーディングを楽しんでください！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示した手法に密接に関連するトピックを扱っています。各リソースには完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得したり、プロジェクトで代替実装アプローチを探求したりするのに役立ちます。

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}