---
category: general
date: 2026-09-27
description: Javaで空白のWord文書を作成し、Aspose.Wordsを使用して図形をグループ化します。図形のサイズ設定、塗りつぶし色の設定、子要素をグループに追加する方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- set shape size
- set shape fill color
- append child to group
language: ja
lastmod: 2026-09-27
og_description: JavaでAspose.Wordsを使用して空白のWord文書を作成します。このチュートリアルでは、Wordで図形をグループ化する方法、図形のサイズを設定する方法、図形の塗りつぶし色を設定する方法、そして子要素をグループに追加する方法を示します。
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: 空白のWord文書を作成し、Javaで図形をグループ化する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create a blank Word document in Java and group shapes using Aspose.Words.
    Learn to set shape size, set shape fill color, and append child to group.
  headline: How to create blank word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Javaで空白のWord文書を作成し、図形をグループ化する方法
url: /ja/java/images-shapes/how-to-create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Javaで空白のWord文書を作成し、シェイプをグループ化する方法

プログラムで **create blank word document** を作成する必要がある場合、このガイドでは Aspose.Words for Java を使用して正確に行う方法を示します。また、**group shapes in word**、各シェイプのサイズ設定、塗りつぶし色の適用、そして **append child to group** によってオブジェクトを単一のユニットとして動作させる方法も学べます。

コードからWordファイルを操作することで、手動での書式設定を省き、レポート、契約書、マーケティングパンフレットなどを自動的に生成できます。このチュートリアルの最後までに、青い長方形と画像を含む `.docx` ファイルを生成し、両方がグループ化された実行可能なJavaプログラムが完成します。

## 前提条件

- Java 17（または最新のJDK）がインストールされていること。
- 依存関係管理のための Maven または Gradle。
- Aspose.Words for Java のライセンス（無料評価版でもテストは可能）。
- サンプル画像ファイル（例：`sample.jpg`）をコードから参照できるフォルダーに配置すること。

> **Pro tip:** 画像ファイルは `resources` ディレクトリに保存し、`ClassLoader.getResourceAsStream` で読み込むことでハードコーディングされた絶対パスを回避できます。

## 手順 1: 空白のWord文書を作成し、GroupShape を追加する

最初のステップは、空のWordファイルを表す新しい `Document` オブジェクトをインスタンス化し、続いて `GroupShape` を挿入することです。このグループは、後で追加するすべてのシェイプのコンテナとして機能します。

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();                     // create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape();     // group shapes in word
```

*Why this matters:* `GroupShape` を使用すると、複数のシェイプをまとめて移動、回転、書式設定でき、図や透かしなどの複雑なレイアウトに不可欠です。

## 手順 2: 長方形を挿入し、**set shape size** を設定する

次に、長方形を作成し、寸法を定義してグループに追加します。これにより **set shape size** 操作が実演されます。

```java
        // Step 2: Create a rectangle shape, configure its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);                         // set shape size – width 100 points
        rectangle.setHeight(50.0);                         // set shape size – height 50 points
        rectangle.setFillColor(java.awt.Color.BLUE);      // set shape fill color to blue
        group.appendChild(rectangle);                     // append child to group
```

*Explanation:* `setWidth` と `setHeight` はシェイプの正確なサイズをポイント単位で制御します（1ポイント = 1/72 インチ）。レイアウト要件に合わせてこれらの値を調整してください。

## 手順 3: 長方形に対して **Set shape fill color** を設定する

長方形の背景は `setFillColor` を使用して青に設定されます。任意の `java.awt.Color` 定数やカスタム RGB カラーを使用できます。

```java
        // The fill color was already applied in the previous step.
        // If you need a different color later, just call setFillColor again:
        // rectangle.setFillColor(new java.awt.Color(255, 165, 0)); // orange
```

*Why it’s useful:* 塗りつぶし色はオブジェクトを視覚的に区別するのに役立ち、特に文書を PDF にエクスポートしたり印刷したりする際に有用です。

## 手順 4: 画像を挿入し、**append child to group** を実行する

同じ `GroupShape` に画像を追加します。画像は `DocumentBuilder.insertImage` で挿入され、その後グループに追加されるため、長方形と一緒に移動します。

```java
        // Step 4: Insert an image and add it to the same group
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        group.appendChild(picture);                       // append child to group
```

*Edge case:* 画像パスが間違っていると、Aspose.Words は `FileNotFoundException` をスローします。相対パスを使用するか、リソースから画像をロードしてこの問題を回避してください。

## 手順 5: **Save the document with the grouped shapes**

最後に、ドキュメントをディスクに書き込みます。生成されたファイルには長方形と画像がグループ化された状態で含まれます。

```java
        // Step 5: Save the document with the grouped shapes
        doc.save("YOUR_DIRECTORY/GroupShape.docx");       // creates the blank word document with grouped shapes
    }
}
```

### 期待される出力

- 指定ディレクトリに `GroupShape.docx` という名前のファイルが作成されます。
- Microsoft Word でファイルを開くと、青い長方形と選択した画像が単一のオブジェクトとして選択された状態の空白ページが表示されます（それらを一緒に移動またはサイズ変更できます）。

![create blank word document with grouped shapes](/images/grouped-shapes.png "create blank word document with grouped shapes")

*上のスクリーンショットは、新しく作成された Word 文書内の最終的なグループ化シェイプを示しています。*

## よくあるバリエーションと追加のヒント

| シチュエーション | 対処方法 |
|-----------|-----------------|
| **Multiple images** | 各画像を `builder.insertImage` で挿入し、各画像に対して `group.appendChild(picture)` を呼び出します。 |
| **Different shape types** | `Shape` オブジェクトを作成する際に、`ShapeType.OVAL`、`ShapeType.LINE` などを使用します。 |
| **Changing group position** | すべての子要素を追加した後、`group.setLeft(x)` と `group.setTop(y)` を設定してグループ全体を移動します。 |
| **Export to PDF** | グループ化後に `doc.save("output.pdf")` を呼び出します。PDF はグループ化を保持します。 |
| **License enforcement** | 評価版を実行すると透かしが表示されます。有効なライセンスをインストールして透かしを削除してください。 |

## 結論

これで、Aspose.Words for Java を使用して **create blank word document**、**GroupShape** の挿入、**set shape size**、**set shape fill color**、そして **append child to group** の方法が分かりました。このパターンにより、後で Word で編集したり他の形式にエクスポートしたりできる、複雑なプログラム的レイアウトを構築できます。

次に、テキストボックスを使用した **group shapes in word** の方法や、シェイプにハイパーリンクを追加する方法、またはマルチページレポートの自動生成を検討してください。同じ原則が適用されます—追加のシェイプを作成し、プロパティを設定し、同じグループに追加するだけです。

コーディングを楽しんでください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説付きの完全なコード例が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}