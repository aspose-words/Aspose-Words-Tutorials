---
category: general
date: 2026-11-22
description: JavaでWord文書に長方形の図形を追加し、図形のサイズを設定し、複数の図形をグループ化し、効率的に図形をグループに追加する。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add rectangle shape
- set shape size
- group multiple shapes
- set shape dimensions
- append shape to group
language: ja
lastmod: 2026-11-22
og_description: Java を使用して Word 文書に長方形の図形を追加し、図形のサイズを設定し、複数の図形をグループ化し、単一のワークフローで図形をグループに追加します。
og_image_alt: Screenshot showing a rectangle shape added and grouped in a Word document
  using Java
og_title: Javaで長方形シェイプを追加し、シェイプをグループ化する – 完全ガイド
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  headline: Add rectangle shape and group shapes in Java
  type: TechArticle
- description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  name: Add rectangle shape and group shapes in Java
  steps:
  - name: Insert the rectangle shape
    text: The rectangle is the first visual element we want to place inside the document.
      By using the `Shape` constructor with `ShapeType.RECTANGLE`, you get a fully
      editable object.
  - name: Set shape size and dimensions
    text: Set shape size and dimensions
  - name: Create a group shape container
    text: '```java // Step 6: Create a group shape that will hold the rectangle and
      other shapes GroupShape groupShape = builder.insertGroupShape(); ```'
  - name: Append shape to group
    text: Append shape to group
  - name: Save the document
    text: '```java // Save the result to a new file doc.save("output.docx"); } } ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shape manipulation
title: Javaで長方形シェイプを追加し、シェイプをグループ化する
url: /ja/java/images-shapes/add-rectangle-shape-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java で矩形シェイプを追加し、シェイプをグループ化する

Java で Word 文書に **矩形シェイプを追加** したい場合、このガイドが正確な手順を案内します。**シェイプのサイズ設定**、**複数シェイプのグループ化**、そして **シェイプをグループに追加** する方法も学べます。IDE を離れることなく完了できます。

DOCX ファイル内でベクターグラフィックを扱うのは、別々の API を使い分けるように感じられます。このチュートリアルの最後には、矩形、楕円、そして必要に応じた追加シェイプを作成し、1 つのオブジェクトとしてまとめて移動できる、単一の自己完結型プログラムが完成します。必要なのは Aspose.Words for Java だけです。

## 前提条件

開始する前に、以下を確認してください。

* Java 17 以上がインストールされていること。
* Maven 3.8+（または Gradle）で依存関係を管理できること。
* 有効な Aspose.Words for Java ライセンス（評価版でもテストは可能）。
* IntelliJ IDEA や VS Code などの IDE（テキストエディタでも可）。

これらの要件があれば、コードは任意の最新開発環境でコンパイル・実行できます。

## 手順 1: Maven プロジェクトの設定

新規 Maven プロジェクトを作成するか、既存の `pom.xml` に Aspose.Words の依存関係を追加します。

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>shape‑demo</artifactId>
  <version>1.0.0</version>

  <dependencies>
    <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.12</version>
    </dependency>
  </dependencies>
</project>
```

この依存関係により、`Document`、`DocumentBuilder`、`Shape`、`GroupShape` など、文書操作に必要なすべてのクラスが取得されます。`mvn compile` を実行すると、Maven が自動的に JAR をダウンロードします。

## 手順 2: 文書をロードし DocumentBuilder を作成

`DocumentBuilder` はコンテンツ挿入用のフルエント API を提供します。既存の DOCX をロードするか、空の文書から開始します。

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document or create a new one
        Document doc = new Document("input.docx");          // replace with your path
        DocumentBuilder builder = new DocumentBuilder(doc);
```

ビルダーを早めに作成すると、文書の先頭にカーソルが配置され、シェイプ挿入の準備が整います。

## Word 文書に矩形シェイプを追加

### 手順 3: 矩形シェイプを挿入

矩形は文書内に配置したい最初のビジュアル要素です。`Shape` コンストラクタに `ShapeType.RECTANGLE` を指定すると、完全に編集可能なオブジェクトが取得できます。

```java
        // Step 3: Insert a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        // The shape is not yet sized; we will set its dimensions next.
```

この時点で矩形を追加しても、サイズが定義されてコンテナに追加されるまでレイアウトには影響しません。

### シェイプのサイズと寸法を設定

#### 手順 4: 幅と高さを定義

シェイプの寸法を設定すると、ページ上での表示が決まります。幅と高さの単位はポイント（1 pt = 1/72 in）です。

```java
        // Step 4: Set shape size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

デザイン要件に合わせて数値を調整してください。同じメソッドは任意の `Shape` インスタンスに適用できるため、円や矢印、カスタム描画にも再利用できます。

#### 手順 5: 矩形を文書に挿入

サイズが決まったら、ページ上に配置します。`DocumentBuilder` の `insertShape` メソッドは、現在のカーソル位置にシェイプを追加します。

```java
        // Insert the rectangle at the builder’s current position
        builder.insertShape(rectangle);
```

この段階では矩形がページに単独で表示されます。次の手順で他のシェイプと組み合わせます。

## 複数シェイプをグループ化

シェイプをグループ化すると、1 つの単位として移動、回転、サイズ変更が可能になります。複雑な図表作成に非常に便利です。

### 手順 6: グループシェイプコンテナを作成

```java
        // Step 6: Create a group shape that will hold the rectangle and other shapes
        GroupShape groupShape = builder.insertGroupShape();
```

`insertGroupShape` 呼び出しにより、文書に空のコンテナが追加されます。このコンテナに追加されたシェイプはすべてグループの一部となります。

### シェイプをグループに追加

#### 手順 7: 矩形をグループに追加

```java
        // Append the previously created rectangle to the group
        groupShape.appendChild(rectangle);
```

追加により、矩形は文書本体からグループの内部コレクションへ移動します。これで矩形はグループの変換（回転・移動など）に従います。

#### 手順 8: デモ用に楕円を追加

```java
        // Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(80);
        ellipse.setHeight(80);
        groupShape.appendChild(ellipse);
```

楕円は矩形と同じ座標空間を共有するため、必要に応じて `setLeft` や `setTop` プロパティで視覚的に整列させられます。

### 手順 9: 文書を保存

```java
        // Save the result to a new file
        doc.save("output.docx");
    }
}
```

プログラムを実行すると `output.docx` が生成されます。Microsoft Word や LibreOffice で開くと、矩形と楕円がグループ化された状態が確認できます。どちらかのシェイプを選択するとグループ全体がハイライトされ、**シェイプをグループに追加** が成功したことが分かります。

![Add rectangle shape example in Java](image.png){alt="Java で矩形シェイプを追加した例"}

*スクリーンショットは、単一のグループ内に矩形と楕円が配置され、共同操作できる状態を示しています。*

## このアプローチが重要な理由

* **単一の真実の情報源** – すべてのシェイププロパティをグループ作成前に設定することで、レイアウトの不具合を防止します。
* **再利用性** – 同じ `setWidth`/`setHeight` メソッドが任意のシェイプで機能するため、矢印や星、カスタム SVG へ簡単に拡張できます。
* **パフォーマンス** – グループ化により Word レンダラが処理する描画オブジェクト数が減少し、大規模文書の開封速度が向上します。
* **保守性** – シェイプ作成とグループ化ロジックを一箇所にまとめることで、将来の開発者が寸法変更や新シェイプ追加を容易に行えます。

## 一般的なバリエーションとエッジケース

| シナリオ | 調整 |
|----------|------------|
| **異なる単位** | `PointsToPixels` 変換を使用するか、インライン配置の場合は `Shape.setWrapType(WrapType.INLINE)` を設定します。 |
| **グループの回転** | `groupShape.setRotation(45);` と呼び出すと、子シェイプ全体が 45° 回転します。 |
| **シェイプへのテキスト追加** | サイズ設定後に `Shape.setText("Label");` を使用します。 |
| **動的サイズ設定** | `doc.getFirstSection().getPageSetup().getPageWidth()` でページ幅を取得し、比例的にシェイプサイズを計算します。 |

これらのバリエーションは、コアパターン **矩形シェイプを追加**、**シェイプサイズを設定**、**複数シェイプをグループ化**、**シェイプをグループに追加** がさまざまな実務要件に適応できることを示しています。

## 結論

Java を使用して Word 文書に **矩形シェイプを追加** し、**シェイプサイズを設定**、**複数シェイプをグループ化**、そして **シェイプをグループに追加** する方法を習得しました。完全なサンプルは単一の実行可能クラスとしてコンパイルでき、生成された DOCX ファイルで期待通りの結果が確認できます。

ここからさらに進められること:

* 各シェイプにテキストラベルやハイパーリンクを追加する。
* 階層的な図表を作るためにグループを入れ子にする。
* シェイプグループを保持したまま PDF へエクスポートする。

さまざまな寸法、色、追加シェイプタイプで実験してみてください。シェイプ操作の習熟は、レポート自動生成、動的図表、リッチな文書体験を Java コードだけで実現する扉を開きます。

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを基にした関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれており、API の追加機能習得や代替実装アプローチの探索に役立ちます。

- [Insert Rectangle Shape in Java – Group and Position Shapes](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [How to create and insert ellipse and rectangle shapes inside a group shape in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Create rectangle shape in a Word document using Java](/words/english/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}