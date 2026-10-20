---
category: general
date: 2026-09-21
description: Java を使用してプログラムで Word 文書を作成します。Word で図形をグループ化する方法、長方形の図形を挿入する方法、図形のサイズを設定する方法、そして図形を
  Word 文書に追加する方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to group shapes in word
- how to insert rectangle shape
- add shapes to word document
- set shape size word
language: ja
lastmod: 2026-09-21
og_description: Javaでプログラム的にWord文書を作成する：このガイドでは、Wordで図形をグループ化する方法、長方形の図形を挿入する方法、図形のサイズを設定する方法、そして図形をWord文書に追加する方法を示します。
og_image_alt: Screenshot of a Java program creating a Word document with grouped shapes
og_title: Javaでプログラム的にWord文書を作成し、シェイプをグループ化する
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically using Java. Learn how to group
    shapes in Word, insert a rectangle shape, set shape size, and add shapes to a
    Word document.
  headline: Create word document programmatically, group shapes in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Word automation
- Shapes
title: Javaでプログラム的にWord文書を作成し、シェイプをグループ化する
url: /ja/java/images-shapes/create-word-document-programmatically-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Javaでプログラム的にWord文書を作成し、シェイプをグループ化する

プログラムでWord文書を**作成**する必要がある場合、このガイドでは完全なソリューションを順を追って説明します。**Wordでシェイプをグループ化**し、矩形を挿入し、サイズを設定し、他のシェイプを追加する方法を、Java と Aspose.Words for Java ライブラリを使用して学びます。

このチュートリアルは、プロジェクトのセットアップから最終的な .docx ファイルの保存までのすべての手順をカバーしています。最後まで実施すれば、矩形と画像が単一のグループにラップされた Word 文書を生成でき、両方を一緒に移動またはサイズ変更できるようになります。Aspose.Words API の事前知識は不要ですが、基本的な Java 開発環境は必要です。

## Prerequisites

* Java Development Kit (JDK) 8 以上  
* 依存関係管理のための Maven または Gradle  
* Aspose.Words for Java 23.9（または最新バージョン） – ライブラリは評価版として無料です  
* 既知のディレクトリに配置した画像ファイル（例: `sample.jpg`）  

これらの項目が揃っていれば、追加設定なしでコードを実行できます。

## Step 1: Set up the project and import Aspose.Words

Maven プロジェクトを作成するか、既存の `pom.xml` に依存関係を追加します。

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Gradle を使用する場合は、`build.gradle` に以下を追加してください。

```gradle
implementation 'com.aspose:aspose-words:23.9'
```

依存関係が解決したら、Java ソースファイルで必要なクラスをインポートします。

```java
import com.aspose.words.*;
import java.io.File;
```

## Step 2: Create the Word document programmatically

自動化シナリオの最初の操作は、`Document` オブジェクトと `DocumentBuilder` をインスタンス化することです。ビルダーを使用すると、テキスト、画像、シェイプの挿入が簡単になります。

```java
public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

この時点で文書はメモリ上にのみ存在します。ここからシェイプの追加を開始できます。

## Step 3: Insert a rectangle shape – how to insert rectangle shape

矩形は `ShapeType.RECTANGLE` を持つ基本的な `Shape` です。`setWidth`、`setHeight` でサイズを制御し、`setTop` と `setLeft` で位置を設定します。

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);
        rectangle.setTop(10.0);
        rectangle.setLeft(10.0);

        // Optional: give the rectangle a visible fill and line color
        rectangle.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
        rectangle.getStrokeColor().setColor(java.awt.Color.DARK_GRAY);
```

**Why this matters:** サイズと位置を明示的に設定する（`set shape size word`）ことで、文書のデフォルトレイアウトに関係なく、矩形が期待通りの場所に正確に表示されます。

## Step 4: Insert an image – add shapes to word document

`DocumentBuilder` はファイルパスから直接画像を挿入できます。挿入後は、他のシェイプと同様に画像の位置を再配置できます。

```java
        // Insert an image; replace the path with your own image location
        String imagePath = "YOUR_DIRECTORY/sample.jpg";
        if (!new File(imagePath).exists()) {
            throw new IllegalArgumentException("Image file not found: " + imagePath);
        }
        Shape picture = builder.insertImage(imagePath);
        picture.setTop(70.0);
        picture.setLeft(10.0);
```

矩形と画像は現在、文書内の独立したシェイプとして存在します。

## Step 5: Group the shapes – how to group shapes in word

シェイプをグループ化すると、単一ユニットとして移動やサイズ変更が可能になります。Aspose.Words はこの目的のために `GroupShape` コンテナを提供しています。

```java
        // Create a GroupShape that will contain the rectangle and the picture
        GroupShape group = builder.insertGroupShape();

        // Append the rectangle and picture to the group
        group.appendChild(rectangle);
        group.appendChild(picture);
```

グループが保存されると、Word は 2 つの子要素を 1 つの論理オブジェクトとして扱います。後でグループを選択してドラッグすれば、矩形と画像の両方が一緒に動きます。

## Step 6: Save the document

最後に、文書をディスクに書き出します。パスは Java プロセスから書き込み可能である必要があります。

```java
        // Save the document with the grouped shapes
        String outputPath = "YOUR_DIRECTORY/GroupShapeExample.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

`main` メソッドを実行すると **GroupShapeExample.docx** という名前のファイルが生成されます。Microsoft Word で開くと、矩形と画像がグループ内でロックされた状態で表示されます。グループを選択すると両オブジェクトが同時に移動でき、グループ化が成功したことが確認できます。

## Expected output

* 指定したディレクトリに作成される Word ファイル（`GroupShapeExample.docx`）  
* ファイル内では、矩形（ライトグレーの塗り）が左上隅に表示され、そのすぐ下に画像が配置されます。  
* 両オブジェクトは単一のグループに属しているため、どちらかをドラッグするともう一方も一緒に移動します。

## Common variations and edge cases

| Situation | Recommendation |
|-----------|----------------|
| **Different image formats** | Aspose.Words は PNG、BMP、GIF、TIFF をサポートしています。`insertImage` では適切なファイル拡張子を使用してください。 |
| **Negative dimensions** | API は `ArgumentException` をスローします。`setWidth` / `setHeight` を呼び出す前に必ず幅と高さを検証してください。 |
| **Large documents** | 多数のシェイプをグループ化するとファイルサイズが増加する可能性があります。パフォーマンスが重要な場合は、シェイプを単一の画像に結合することを検討してください。 |
| **Word version compatibility** | GroupShape は Word 2007（`.docx`）以降で動作します。古い `.doc` ファイルの場合、グループはフラット化されます。 |
| **Dynamic positioning** | ページサイズに基づく計算（`doc.getFirstSection().getPageSetup().getPageWidth()`）を使用すれば、適応的な配置が可能です。 |

**Pro tip:** グループ作成後、変更できます

## What Should You Learn Next?

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックをカバーしています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを探求するのに役立ちます。

- [Word ドキュメント作成 Java – 影効果付き矩形シェイプの追加](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Java で Word に矩形シェイプを作成 – 完全ガイド](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Aspose.Words for .NET を使用した Word 文書でのグループシェイプ作成](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}