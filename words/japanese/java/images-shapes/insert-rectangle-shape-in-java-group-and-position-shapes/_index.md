---
category: general
date: 2026-07-26
description: Aspose.Words を使用して Java で矩形シェイプを挿入します。シェイプのサイズ設定、位置設定、そして DOCX ファイル内でシェイプをグループ化する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- set shape size
- position shape
- how to group shapes
- how to add rectangle
language: ja
lastmod: 2026-07-26
og_description: Javaで長方形シェイプを挿入し、リッチなDOCXグラフィックを作成します。ステップバイステップのガイドに従って、シェイプのサイズ設定、位置決め、そしてシェイプのグループ化を簡単に行いましょう。
og_image_alt: Screenshot showing a rectangle shape inserted and grouped in a Java‑generated
  Word document
og_title: Javaで矩形形状を挿入 – グルーピングと配置をマスター
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert rectangle shape in Java using Aspose.Words. Learn how to set
    shape size, position shape, and how to group shapes in a DOCX file.
  headline: Insert Rectangle Shape in Java – Group and Position Shapes
  type: TechArticle
tags:
- Aspose.Words
- Java
- Shapes
- DOCX
title: Javaで矩形シェイプを挿入 – シェイプのグループ化と位置設定
url: /ja/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Javaで長方形シェイプを挿入 – シェイプのグループ化と位置設定

Ever needed to **insert rectangle shape** into a Word document while writing Java code? You’re not the only one—developers building reports, invoices, or custom templates hit this wall all the time. The good news is that with a few lines of Aspose.Words for Java you can **insert rectangle shape**, **set shape size**, **position shape**, and even **how to group shapes** so they move as a single unit.

このガイドでは、空のドキュメントを作成するところから、2つの長方形がきれいにグループ化された `.docx` を保存するまでの全プロセスを順に解説します。最後まで読むと、**長方形を追加する方法**、サイズの制御、正確な配置、そして再利用可能なグループへのまとめ方が分かります。Aspose.Words 以外の外部ライブラリは不要で、コードは Java 8 以降で動作します。

## 前提条件

- Java 8 以上がインストール済み（JDK 17 を使用していますが、Maven が動く環境ならどれでも可）
- Aspose.Words for Java 23.9 以降 – `pom.xml` に依存関係を追加するか JAR をダウンロード
- Java の基本構文が理解できること（`main` メソッドを書ければ OK）
- お好みの IDE またはテキストエディタ（IntelliJ IDEA、Eclipse、VS Code など）

> **Pro tip:** If you’re using Maven, the dependency looks like this:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Now that we’ve got the groundwork set, let’s dive into the code.

## 長方形シェイプを挿入してサイズを設定する

The first thing you’ll do is create a fresh `Document` and a `DocumentBuilder`. The builder is your “pen” that draws shapes onto the page. Below we **insert rectangle shape** and immediately **set shape size** to 100 × 80 points.

最初に行うのは、新しい `Document` と `DocumentBuilder` を作成することです。`DocumentBuilder` はページ上にシェイプを描く「ペン」の役割を果たします。以下のコードでは **長方形シェイプを挿入** し、すぐに **シェイプのサイズを 100 × 80 ポイントに設定** しています。

```java
import com.aspose.words.*;

public class GroupedRectanglesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder to add content
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape(400, 200);
        // The group itself is 400×200 points – adjust as needed

        // ---------- First rectangle ----------
        // Insert rectangle shape
        Shape rectangle1 = new Shape(document, ShapeType.RECTANGLE);
        // Set shape size
        rectangle1.setWidth(100);
        rectangle1.setHeight(80);
        // Position shape inside the group
        rectangle1.setLeft(20);   // 20 points from the left edge of the group
        rectangle1.setTop(30);    // 30 points from the top edge of the group
        // Add the rectangle to the group
        group.appendChild(rectangle1);
```

Notice how the `setWidth`/`setHeight` calls **set shape size** in points (1 pt ≈ 1/72 inch). You could also use `setSize` if you prefer a single method, but the explicit calls make the intent crystal clear.

## ページ上にシェイプを配置する

After we have the first rectangle, we need to **position shape** the second one so it doesn’t overlap the first. Positioning works the same way: you set the `Left` and `Top` properties relative to the group’s origin.

最初の長方形を作成したら、2つ目のシェイプを **位置指定** して最初のものと重ならないようにします。位置指定は同じ方法で行い、`Left` と `Top` プロパティをグループの原点に対して設定します。

```java
        // ---------- Second rectangle ----------
        Shape rectangle2 = new Shape(document, ShapeType.RECTANGLE);
        rectangle2.setWidth(120);
        rectangle2.setHeight(60);
        // Position this rectangle a bit farther to the right and lower down
        rectangle2.setLeft(150);
        rectangle2.setTop(50);
        group.appendChild(rectangle2);
```

If you’re wondering why we use `setLeft` instead of `setX`, it’s because Aspose.Words adopts the classic Windows GDI coordinate system—`Left` is the horizontal offset, `Top` is the vertical offset. Changing these values lets you fine‑tune the layout without fiddling with tables or paragraphs.

## シェイプをグループ化する方法

You might ask, “Why bother with a group at all?” Grouping makes sense when you want shapes to move together, rotate as a unit, or share a common style. In the snippet above we already created a `GroupShape` via `builder.insertGroupShape`. That object is essentially a container—think of it as a folder that holds other shape files.

> **Why this matters:** If you later decide to add a caption or rotate the whole diagram, you only need to modify the group, not each rectangle individually.

## グループに長方形を追加する方法

The act of **how to add rectangle** to the group is simply calling `group.appendChild(rectangle)`. Under the hood Aspose.Words updates the group’s internal collection and automatically recalculates the bounding box so the group still fits its declared width and height.

グループに **長方形を追加する方法** は、単に `group.appendChild(rectangle)` を呼び出すだけです。内部で Aspose.Words はグループのコレクションを更新し、バウンディングボックスを自動的に再計算して、宣言した幅と高さに収まるようにします。

```java
        // At this point the group already contains both rectangles.
        // You can also set the group’s border or fill if you like.
        group.getShapeStyle().setLineColor(Color.BLACK);
        group.getShapeStyle().setFillColor(Color.LIGHTGRAY);
```

You can experiment with other `ShapeType`s—`ShapeType.ELLIPSE`, `ShapeType.TRIANGLE`, etc.—and the same `appendChild` pattern works.

## ドキュメントを保存する

Finally, we persist the document to disk. The path can be absolute or relative; just make sure the folder exists.

最後に、ドキュメントをディスクに保存します。パスは絶対でも相対でも構いませんが、フォルダーが存在することを確認してください。

```java
        // Step 5: Save the document containing the grouped shapes
        String outPath = "output/GroupShape.docx";
        document.save(outPath);
        System.out.println("Document saved to: " + outPath);
    }
}
```

When you open `GroupShape.docx` in Microsoft Word, you’ll see two rectangles side‑by‑side, both locked inside a light‑gray box. Selecting the gray box will highlight both rectangles at once—proof that **how to group shapes** really works.

![Grouped rectangles in a Word document](placeholder-image.png){: .center-image alt="Javaで生成された DOCX ファイル内で 2 つの長方形がグループ化された例"}

*Image alt text (SEO):* **Javaで生成された DOCX ファイル内で 2 つの長方形がグループ化された例**.

## 期待される出力

- `output` フォルダーに配置された `GroupShape.docx` ファイル
- ドキュメント内には、幅 400 × 200 pt のグループに、サイズがそれぞれ 100 × 80 pt と 120 × 60 pt の長方形が (20, 30) と (150, 50) に配置されている
- グループは細い黒枠と薄いグレーの塗りつぶしが設定され、グループ化が視覚的に分かりやすくなっている

ファイルを開いてグレーのボックスをドラッグしてみてください。2 つの長方形が同時に動くはずです。動かない場合は、各シェイプに対して `group.appendChild` を呼び出したか再確認してください。

## よくある落とし穴とエッジケース

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| **Rectangles appear outside the page** | `Left`/`Top` values exceed the group’s dimensions | Increase the group size (`insertGroupShape(width, height)`) or reduce offsets |
| **Group disappears after saving** | The group’s `Width`/`Height` are set to 0 | Provide non‑zero dimensions when calling `insertGroupShape` |
| **Shape colors look wrong** | Default fill is transparent; Word may render it as white | Explicitly set `setFillColor` or use `ShapeStyle` |
| **Exception `ArgumentOutOfRangeException`** | Using negative coordinates | Keep `Left` and `Top` non‑negative |

Addressing these early saves you from the “why does my shape vanish?” headaches that many newcomers encounter.

## まとめと次のステップ

We’ve covered the full lifecycle of **insert rectangle shape** in Java: creating a document, **set shape size**, **position shape**, **how to group shapes**, and **how to add rectangle** to that group. The complete, runnable example lives in the code block above, and you can paste it straight into a Maven project to see the result.

What’s next? Consider experimenting with:

- Adding text inside each rectangle via

## 次に学ぶべきことは？

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}