---
category: general
date: 2026-07-16
description: Aspose.Words を使用して Java でグループ シェイプを挿入する方法 – 長方形シェイプを追加し、シェイプのサイズを設定し、色付きの長方形と円を作成する。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert group
- add rectangle shape
- set shape dimensions
- create colored rectangle
- create colored circle
language: ja
lastmod: 2026-07-16
og_description: Javaでグループシェイプを挿入する方法：矩形シェイプの追加、シェイプのサイズ設定、そして Aspose.Words を使用してカラー矩形と円を作成するハンズオンガイド
og_image_alt: Screenshot showing a grouped blue rectangle and red circle in a Java‑generated
  Word document
og_title: Javaでグループシェイプを挿入 – 完全な Aspose.Words チュートリアル
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  headline: how to insert group shape in Java – Complete Guide
  type: TechArticle
- description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  name: how to insert group shape in Java – Complete Guide
  steps:
  - name: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
    text: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
  - name: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
    text: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
  - name: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
    text: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
  - name: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
    text: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
  - name: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
    text: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shapes
- Document Automation
- Group Shapes
title: Javaでグループシェイプを挿入する方法 – 完全ガイド
url: /ja/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Javaでグループシェイプを挿入する方法 – 完全ガイド

Ever wondered **グループシェイプを挿入する方法** in a Word document using Java? You're not the only one. Whether you're building a report generator or a dynamic flyer creator, grouping shapes keeps your layout tidy and your code manageable.

In this tutorial we’ll walk through the exact steps to **矩形シェイプを追加**, **シェイプのサイズを設定**, and **カラー矩形を作成** and **カラーサークルを作成** using the Aspose.Words library. By the end you’ll have a runnable program that produces a .docx file with a blue rectangle and a red circle neatly wrapped inside a group.

## 前提条件

- Java 17（または最新のJDK）がインストールされ、設定されていること。
- 依存関係管理のためのMavenまたはGradle。
- Aspose.Words for Java 23.9以降 – Maven Centralから取得できます。
- Java構文の基本的な理解 – 特別な知識は不要です。

If you’re missing any of these, grab the JDK from Oracle’s site and add the Aspose.Words dependency to your `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Now that the groundwork is set, let’s get our hands dirty.

## グループシェイプを挿入する方法 – 概要

The core idea is simple: create a `Document`, open a `DocumentBuilder`, insert a **グループシェイプ**, then drop individual shapes (a rectangle and a circle) into that group. The group acts like a container, so moving it later will shift everything inside – ideal for complex layouts.

Below is the full, ready‑to‑run code. Feel free to copy‑paste it into a new Java class called `InsertGroupShapeDemo`.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to insert a group shape, add a rectangle and a circle,
 * set their dimensions, and apply colors using Aspose.Words for Java.
 */
public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape that will contain other shapes.
        Shape group = builder.insertGroupShape();

        // Step 3: Create a blue rectangle, set its size and position, and add it to the group.
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);          // set shape dimensions – width
        rectangle.setHeight(50.0);          // set shape dimensions – height
        rectangle.setLeft(20.0);            // X‑coordinate inside the group
        rectangle.setTop(20.0);             // Y‑coordinate inside the group
        rectangle.getFill().setForeColor(Color.BLUE); // create colored rectangle
        group.appendChild(rectangle);       // add rectangle shape to the group

        // Step 4: Create a red circle, set its size and position, and add it to the same group.
        Shape circle = new Shape(doc, ShapeType.ELLIPSE);
        circle.setWidth(60.0);              // set shape dimensions – width (diameter)
        circle.setHeight(60.0);             // set shape dimensions – height (diameter)
        circle.setLeft(150.0);              // X‑coordinate inside the group
        circle.setTop(20.0);                // Y‑coordinate inside the group
        circle.getFill().setForeColor(Color.RED); // create colored circle
        group.appendChild(circle);          // add circle shape to the group

        // Step 5: Save the document with the grouped shapes.
        doc.save("GroupShapeDemo.docx");
        System.out.println("Document saved successfully.");
    }
}
```

> **プロのコツ:** `setLeft` と `setTop` の値はページではなくグループの原点に対して相対的です。これにより、後でグループ全体の位置を変更するのが非常に簡単になります。

### 何が起こったのか？

1. **Document & Builder** – 空のWordファイルと、コンテンツ挿入を可能にする`DocumentBuilder`を作成します。
2. **Group Shape** – `builder.insertGroupShape()`はコンテナを作成します。描画オブジェクト用のフォルダーと考えてください。
3. **Blue Rectangle** – `RECTANGLE`タイプの`Shape`をインスタンス化し、サイズと位置を設定し、青で塗りつぶします。これが**カラー矩形を作成**するステップです。
4. **Red Circle** – 同様の手順で、完璧な円を作るために`ELLIPSE`を使用し、赤で塗りつぶします。これが**カラーサークルを作成**する部分です。
5. **Saving** – 最後にすべてを`GroupShapeDemo.docx`に保存します。

Run the program (`mvn compile exec:java -Dexec.mainClass=InsertGroupShapeDemo`) and open the resulting file. You should see a blue rectangle on the left and a red circle on the right, both locked inside a single group box.

## 矩形シェイプの追加

If you only need a rectangle without grouping, you can skip the `insertGroupShape()` call and append the rectangle directly to the document’s body. However, grouping gives you the flexibility to move, rotate, or delete multiple shapes in one go.

```java
Shape rect = new Shape(doc, ShapeType.RECTANGLE);
rect.setWidth(120);
rect.setHeight(70);
rect.getFill().setForeColor(Color.GREEN);
builder.insertNode(rect);
```

Notice how we used **矩形シェイプを追加** logic here. The rectangle appears on the page as an independent object. In most real‑world scenarios you’ll want the group, though, because it preserves relative positioning.

## シェイプのサイズ設定

When you see methods like `setWidth` and `setHeight`, remember they accept **points** (1/72 inch). If you prefer millimeters, convert first:

```java
double mmToPoints = 72.0 / 25.4;
double widthInMm = 50; // 50 mm
rectangle.setWidth(widthInMm * mmToPoints);
rectangle.setHeight(30 * mmToPoints);
```

This snippet demonstrates **シェイプのサイズ設定** with a unit conversion – handy when your design specs come from a UI mockup that uses metric units.

## カラー矩形の作成

Coloring a shape is as simple as calling `getFill().setForeColor()`. You can pass any `java.awt.Color`. Want a gradient? Use `setForeColor` for the start color and `setBackColor` for the end.

```java
rectangle.getFill().setForeColor(Color.MAGENTA);
rectangle.getFill().setBackColor(Color.YELLOW);
rectangle.getFill().setFillType(FillType.GRADIENT);
```

That’s a quick way to **カラー矩形を作成** with a gradient fill instead of a solid hue.

## カラーサークルの作成

Circles are just ellipses with equal width and height. The same color logic applies:

```java
circle.getFill().setForeColor(new Color(255, 165, 0)); // orange
```

If you need a transparent fill, set the alpha channel:

```java
circle.getFill().setForeColor(new Color(0, 0, 255, 128)); // semi‑transparent blue
```

Now you’ve mastered the **カラーサークルを作成** technique.

## ドキュメントの保存

Aspose.Words lets you output to many formats: DOCX, PDF, HTML, PNG, you name it. For this demo we stick with DOCX because it preserves the vector shapes perfectly.

```java
doc.save("GroupShapeDemo.pdf", SaveFormat.PDF);
```

Switching the `SaveFormat` is all it takes to generate a PDF version of the same grouped artwork.

## よくある落とし穴と回避策

- **シェイプをグループに追加し忘れた？** シェイプはページに表示されますが、グループと一緒に移動しません。必ず `group.appendChild(yourShape)` を呼び出してください。

## 次に学ぶべきことは？

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [JavaでWord文書を作成 – 影効果付き矩形シェイプの追加](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words for JavaでDocumentBuilderを使用してフォームフィールドを作成しコンテンツを追加する方法](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.WordsでWordに矩形シェイプを作成 – ステップバイステップガイド](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}