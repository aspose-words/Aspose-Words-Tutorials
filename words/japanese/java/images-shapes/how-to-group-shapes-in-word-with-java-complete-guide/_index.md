---
category: general
date: 2026-10-16
description: Java を使用して Word で図形をグループ化する方法を学びます。このチュートリアルでは、長方形の図形を追加し、図形のサイズと寸法を設定し、文書を保存する方法を示します。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- set shape dimensions
- rectangle shape code
language: ja
lastmod: 2026-10-16
og_description: Javaを使用してWordで図形をグループ化します。長方形の図形を追加し、サイズと寸法を設定し、プログラムでプロフェッショナルな文書を作成します。
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: JavaでWordの図形をグループ化する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  headline: How to group shapes in Word with Java – complete guide
  type: TechArticle
- description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  name: How to group shapes in Word with Java – complete guide
  steps:
  - name: Expected output
    text: '- A file named **GroupShapeDemo.docx** appears in the project folder. -
      Opening the file in Word shows two shapes (a rectangle and an ellipse) that
      are grouped together. - Dragging either shape moves the whole group, confirming
      that **group shapes in word** works as intended.'
  - name: Pro tip
    text: 'When you need to **set shape dimensions** based on dynamic data (e.g.,
      a barcode length), calculate the width/height in points first:'
  - name: What’s next?
    text: '- Explore **add rectangle shape** variations such as rounded corners (`ShapeType.RECTANGLE`
      with `setCornerRadius`). - Combine **group shapes in word** with tables or charts
      for richer documents. - Look into the Aspose.Words API for **text wrapping**
      (`shape.setWrapType(WrapType.SQUARE)`) to control'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: JavaでWordの図形をグループ化する方法 – 完全ガイド
url: /ja/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# JavaでWordの図形をグループ化する方法 – 完全ガイド

Word の図形をプログラムで **グループ化** したい場合、このチュートリアルで実行可能なソリューションを提供します。**矩形（rectangle）図形の追加**、サイズ調整、図形の寸法設定、そして最終的に矩形と楕円がグループ化された DOCX ファイルを保存する方法を確認できます。

Word で図形をグループ化すると、複雑なダイアグラムの作成、再利用可能なグラフィックコンポーネントの構築、または文書を後で編集する際に関連オブジェクトをまとめて保持するのに便利です。コードは Aspose.Words for Java ライブラリを使用しており、最新の JDK で動作し、Microsoft Word のインストールは不要です。

## 前提条件

開始する前に、以下を確認してください。

| 要件 | 理由 |
|------|------|
| Java 17（またはそれ以降） | ライブラリは最新の Java ランタイムを対象としています。 |
| Aspose.Words for Java（最新バージョン） | サンプルで使用する `Document`、`DocumentBuilder`、`GroupShape`、`Shape` クラスを提供します。 |
| IDE またはビルドツール（Maven/Gradle） | サンプルをコンパイルして実行するために必要です。 |
| Java の基本構文に関する知識 | コードの流れを理解するために必要です。 |

プロジェクトに Aspose.Words の依存関係を追加します。Maven の場合:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest version -->
</dependency>
```

Gradle の場合:

```gradle
implementation 'com.aspose:aspose-words:23.10'
```

## ソリューションの概要

このチュートリアルは **問題 → 解決策 → 説明** の流れで進めます。

1. **新しい Word 文書を作成** し、`DocumentBuilder` を取得。  
2. **`GroupShape` コンテナを挿入** して、複数の図形を保持。  
3. **矩形を追加**、幅・高さを設定（**set shape size** 手順）し、グループに添付。  
4. **楕円を追加**、同じグループ内に配置し、寸法も設定。  
5. **文書を保存** してディスクに書き出し。

各ステップではコードの **なぜ** を解説するので、API の動作と他シナリオへの適用方法が理解できます。

## 手順 1: 文書と DocumentBuilder の作成

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to work with it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**重要ポイント:** `Document` は DOCX 全体を表し、`DocumentBuilder` は低レベルのノード管理を意識せずにコンテンツを挿入できるヘルパーです。最初にこれらを作成することで、後続の図形操作のためのクリーンなキャンバスが得られます。

## 手順 2: GroupShape コンテナの挿入

```java
        // Step 2: Insert a GroupShape container that will hold multiple shapes
        GroupShape groupShape = builder.insertGroupShape();
```

`GroupShape` は描画オブジェクトの **フォルダー** のように機能します。グループを移動、回転、削除すると、子図形が自動的に追従します。これが **Word の図形グループ化** の核心です。

## 手順 3: 矩形図形の追加 – 矩形図形コード

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape width in points
        rectangleShape.setHeight(50);   // set shape height in points
        groupShape.appendChild(rectangleShape);
```

- **add rectangle shape** – `Shape` コンストラクタに `ShapeType.RECTANGLE` を渡すことで、Aspose.Words に矩形のアウトラインを描画させます。  
- **set shape size** – `setWidth` と `setHeight` で **shape dimensions** をポイント単位で指定します（1 pt = 1/72 in）。視覚的サイズを制御する最も一般的な方法です。  
- **Why we use `appendChild`** – 矩形を `GroupShape` に添付し、グループと一緒に移動できるようにします。

## 手順 4: 楕円の追加とグループ内での位置設定

```java
        // Step 4: Create an ellipse, set its size and position inside the group, then add it
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);      // set shape width
        ellipseShape.setHeight(80);     // set shape height (making it a circle)
        ellipseShape.setLeft(120);      // position relative to the group container
        groupShape.appendChild(ellipseShape);
```

楕円は **set shape dimensions** を矩形以外で示す例です。`setLeft` を呼び出すことで、グループ内の水平オフセットを制御でき、複数オブジェクトの配置に便利です。

## 手順 5: 文書の保存

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

*GroupShapeDemo.docx* を Microsoft Word で開くと、矩形と楕円が単一のグループとしてロックされていることが確認できます。どちらかの図形を選択するとグループ全体が選択され、**Word の図形グループ化** が期待通りに機能します。

## 完全な実行可能サンプル

すべてのパーツを組み合わせた完全なソースファイルは以下です。IDE にコピーして使用してください。

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will hold the rectangle and ellipse
        GroupShape groupShape = builder.insertGroupShape();

        // Add a rectangle (add rectangle shape) and define its size (set shape size)
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        groupShape.appendChild(rectangleShape);

        // Add an ellipse, set its dimensions, and position it inside the group
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);
        ellipseShape.setHeight(80);
        ellipseShape.setLeft(120);      // horizontal offset relative to the group
        groupShape.appendChild(ellipseShape);

        // Save the document to the local file system
        document.save("GroupShapeDemo.docx");
    }
}
```

### 期待される出力

- プロジェクトフォルダーに **GroupShapeDemo.docx** が作成されます。  
- Word でファイルを開くと、矩形と楕円の 2 つの図形がグループ化されて表示されます。  
- いずれかの図形をドラッグするとグループ全体が移動し、**Word の図形グループ化** が正しく機能していることが確認できます。

## よくあるバリエーションとエッジケース

| シナリオ | 変更点 | 理由 |
|----------|--------|------|
| **異なる図形タイプ**（例: 三角形） | `ShapeType.TRIANGLE` など、`Shape` 作成時に別の enum 値を使用 | より複雑なダイアグラムを構築できるようにするため |
| **塗りつぶし色の設定** | 図形作成後に `shape.getFillColor().setColor(Color.BLUE);` を呼び出す | グループ化に影響せず、見た目を向上させる |
| **グループの回転** | `groupShape.setRotationAngle(45);` | 子図形すべてを一括で回転でき、アイコンなどに便利 |
| **図形内にテキストを追加** | `shape.appendChild(new Paragraph(document));` の後に `Run` でテキストを追加 | ラベルやコールアウトとして図形を使用できる |
| **ストリームへの保存** | `ByteArrayOutputStream out = new ByteArrayOutputStream(); document.save(out, SaveFormat.DOCX);` | Web サービスで文書を直接返す場合に有用 |

### プロのコツ

動的データ（例: バーコードの長さ）に基づいて **set shape dimensions** を決める必要がある場合、まずポイント単位で幅・高さを計算します。

```java
double inches = 2.5;
int points = (int)(inches * 72); // 1 inch = 72 points
shape.setWidth(points);
```

ハードコーディングを避け、コードの汎用性を保てます。

## 結論

これで Java を使って **Word の図形をグループ化** し、**矩形図形の追加**、**shape size の設定**、**shape dimensions の設定** を行う方法が分かりました。上記手順に従えば、再利用可能なグラフィックグループを作成し、レポートに埋め込んだり、カスタムダイアグラムツールを構築したりできます。

### 次にやること

- 角丸（`ShapeType.RECTANGLE` と `setCornerRadius`）など、**add rectangle shape** のバリエーションを探求。  
- **group shapes in word** をテーブルやチャートと組み合わせて、よりリッチな文書を作成。  
- Aspose.Words API の **text wrapping**（`shape.setWrapType(WrapType.SQUARE)`）を調べ、周囲のテキストとの連携を制御。

ぜひ実験し、**rectangle shape code** をカスタマイズして結果を共有してください。

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれており、API の追加機能習得や代替実装アプローチの探求に役立ちます。

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}