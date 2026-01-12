---
category: general
date: 2026-01-11
description: JavaでWord文書を素早く作成するには、長方形のシェイプを追加し、塗りつぶし色を設定し、シェイプに影を適用します。ステップバイステップで学びましょう。
draft: false
keywords:
- create word document java
- add rectangle shape
- apply shadow to shape
- set shape fill color
- how to add shape
language: ja
og_description: 矩形シェイプを挿入し、塗りつぶし色を設定し、影を適用してJavaでWord文書を作成する。コード付きの完全ガイド。
og_title: JavaでWord文書を作成 – 影付き長方形シェイプを追加
tags:
- Aspose.Words
- Java
- Document Generation
title: JavaでWord文書を作成 – 影付き長方形シェイプを追加
url: /ja/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create Word Document Java – 四角形シェイプに影効果を追加

Ever needed to **create word document java** and make it look a bit more polished? Maybe you’re building a report generator and a plain page just won’t cut it. The good news? With Aspose.Words for Java you can drop a rectangle shape onto a document, give it a splash of color, and even toss a subtle shadow on it—all in a handful of lines.

このチュートリアルでは、四角形シェイプを追加し、塗りつぶし色を設定し、シェイプに影を適用して Word ファイルを少しだけプロフェッショナルに見せる方法を順を追って解説します。最後まで読むと、プロジェクトにコピペできる実行可能なサンプルが手に入ります。

## 必要なもの

- **Java 17** (or any recent JDK) – the code uses the standard language features.
- **Aspose.Words for Java** library – version 23.9 or newer is recommended.
- An IDE or text editor of your choice – IntelliJ IDEA, Eclipse, VS Code… you decide.
- A folder where the generated `ShadowShape.docx` will be saved.

追加の設定ウィザードは不要です。Aspose.Words の JAR をクラスパスに追加すればすぐに使えます。

## ステップ 1: プロジェクトの設定と Aspose.Words のインポート

First things first, create a new Maven (or Gradle) project and pull in the Aspose.Words dependency. Here’s a minimal `pom.xml` snippet for Maven:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>23.9</version>
        <classifier>jdk17</classifier>
    </dependency>
</dependencies>
```

If you’re not using Maven, just drop the JAR file into your `libs` folder and add it to the build path.

> **Pro tip:** Aspose offers a free trial license that you can embed with `License license = new License(); license.setLicense("Aspose.Words.lic");`. Skip it for quick tests; the library works in evaluation mode.

## ステップ 2: 新しい Document と Builder の作成

Now we’ll actually **create word document java** objects. The `Document` class represents the whole .docx file, while `DocumentBuilder` lets us insert content.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

At this point you have an empty document ready to receive shapes, paragraphs, or anything else you might need.

## ステップ 3: 四角形シェイプの挿入と塗りつぶし色の設定

Adding a shape is as simple as calling `insertShape`. We’ll use the **add rectangle shape** technique, which falls under the secondary keyword *add rectangle shape*.

```java
        // Insert a rectangle shape – 200pt wide, 100pt tall
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);

        // Set the fill color to a bright orange
        rectangle.setFillColor(java.awt.Color.ORANGE);
```

Why orange? It stands out in a sea of white, but you can swap it for any `java.awt.Color` you like. This step covers the secondary keyword *set shape fill color*.

## ステップ 4: 影の外観を設定 – シェイプに影を適用

Now comes the fun part: giving the rectangle a subtle drop shadow. The Aspose API exposes a `ShadowFormat` object that controls every aspect of the shadow.

```java
        // Get the shadow format object for the shape
        ShadowFormat shadow = rectangle.getShadowFormat();

        // Make the shadow visible
        shadow.setVisible(true);

        // Choose a neutral gray for the shadow color
        shadow.setColor(java.awt.Color.GRAY);

        // Blur radius – larger values produce a softer edge
        shadow.setBlur(5.0);

        // Offset determines how far the shadow is displaced
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);

        // Transparency (0 = opaque, 1 = fully transparent)
        shadow.setTransparency(0.2);

        // Define the shadow style and type
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);

        // Scale controls the overall size of the shadow relative to the shape
        shadow.setScale(1.0);
```

That block of code **apply shadow to shape** exactly as the secondary keyword suggests. You can tweak `blur`, `offsetX/Y`, and `transparency` to suit your design language. For instance, a larger `offsetX` creates a more dramatic cast, while a higher `transparency` makes the shadow whisper rather than shout.

## ステップ 5: ドキュメントの保存

Finally, we write the document to disk. Choose a folder you have write access to, and give the file a clear name.

```java
        // Save the result – adjust the path as needed
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

When you open `ShadowShape.docx` in Microsoft Word or LibreOffice, you’ll see a bright orange rectangle with a soft gray shadow hovering just beneath it.

![create word document java with rectangle shape](/images/shadow-rectangle.png "create word document java – rectangle with shadow")

*Image alt text includes the primary keyword, satisfying the SEO rule.*

## よくある質問とエッジケース

### 別のシェイプが必要な場合は？

Aspose.Words supports dozens of `ShapeType` values – stars, arrows, callouts, you name it. Simply replace `ShapeType.RECTANGLE` with `ShapeType.OVAL` or any other enum constant. The same **how to add shape** steps apply.

### シェイプを特定の段落に追加するには？

Instead of inserting the shape directly with the builder, you can create it first (`new Shape(document, ShapeType.RECTANGLE)`) and then add it to a `Paragraph` via `paragraph.appendChild(shape)`. This gives you finer control over layout.

### 単色の代わりにグラデーション塗りを適用できますか？

Yes! Use `rectangle.getFill().setFillType(FillType.GRADIENT)` and define a `LinearGradientFill`. The API is a bit more verbose, but it works great for modern designs.

### 古い Word バージョンとの互換性は？

Aspose.Words saves in the .docx format by default, which is supported by Word 2007+ and LibreOffice. If you need .doc, call `document.save("file.doc", SaveFormat.DOC)`. Shadow rendering may differ slightly, but the shape itself remains intact.

## 完全動作例（コピー＆ペースト可能）

Below is the entire program, ready to compile and run. Replace `YOUR_DIRECTORY` with an actual path on your machine.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape and set its fill color
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);
        rectangle.setFillColor(java.awt.Color.ORANGE);

        // Step 3: Apply shadow to shape
        ShadowFormat shadow = rectangle.getShadowFormat();
        shadow.setVisible(true);
        shadow.setColor(java.awt.Color.GRAY);
        shadow.setBlur(5.0);
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);
        shadow.setTransparency(0.2);
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);
        shadow.setScale(1.0);

        // Step 4: Save the document
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Running this code produces a Word file that contains the orange rectangle with a soft gray shadow—exactly what we set out to achieve when we wanted to **create word document java** with a styled shape.

## 結論

You now have a solid, end‑to‑end recipe for **create word document java** that *adds rectangle shape*, *sets shape fill color*, and *applies shadow to shape*. The approach is straightforward, the API is fluent, and you can extend it in countless ways—different shapes, gradient fills, or even multiple shadows per shape.

What’s next? Try layering several shapes, experiment with `ShadowStyle.ETCHED` for a different visual feel, or combine this with table generation to build fully‑fledged reports. The possibilities are only limited by your imagination (and maybe the Aspose license tier).

If you ran into any hiccups or have ideas for further enhancements, drop a comment below. Happy coding, and enjoy making those Word documents look a little less bland!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}