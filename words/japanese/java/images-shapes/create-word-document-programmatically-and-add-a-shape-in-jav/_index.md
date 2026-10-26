---
category: general
date: 2026-10-26
description: Aspose.Words for Java を使用して、Word ドキュメントをプログラムで作成し、図形を追加し、オブジェクトを非表示にする方法を学ぶ
  – ステップバイステップガイド。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to hide shape
- how to add shape
- hide object in word
language: ja
lastmod: 2026-10-26
og_description: プログラムでWord文書を作成し、Aspose.Words for Java を使用してWordに図形を追加しオブジェクトを非表示にする方法を学びます。完全な実行可能サンプルです。
og_image_alt: Screenshot of a Word document created programmatically with a hidden
  ellipse shape
og_title: Wordドキュメントをプログラムで作成 – Javaでシェイプを追加・非表示にする
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document programmatically, add a shape, and
    hide object in Word using Aspose.Words for Java – step‑by‑step guide.
  headline: Create Word document programmatically and add a shape in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Javaでプログラム的にWord文書を作成し、図形を追加する
url: /ja/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# JavaでWord文書をプログラム的に作成し、シェイプを追加する

Word文書をプログラム的に作成する必要がある場合、このチュートリアルではその手順、シェイプの追加、そしてWordでオブジェクトを非表示にする方法を正確に示します。レポートジェネレータや自動契約システムを構築している場合でも、数分で完全に実行可能なソリューションが手に入ります。

以下を学びます：

* Aspose.Words for Java を使用して Word 文書を初期化する。  
* **how to add shape** テクニックを使用して楕円（または他のシェイプ）を挿入する。  
* **how to hide shape** の質問に答える形で、そのシェイプを非表示にする。  

Aspose.Words ライブラリ以外に外部ツールは必要なく、コードは Java 17 以降で動作します。

## 前提条件

開始する前に、以下が揃っていることを確認してください：

* Java Development Kit (JDK) 17 以上がインストールされていること。  
* 依存関係管理のための Maven または Gradle（例では Maven を使用）。  
* 有効な Aspose.Words for Java ライセンス（無料評価版でもテストは可能）。  

Aspose.Words が初めての場合は公式の Getting Started ガイドを参照してください。ただし、このチュートリアルを進めるために読む必要はありません。

## Maven 依存関係

次の依存関係を `pom.xml` に追加してください：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

> **プロのコツ:** バージョン番号は常に最新に保ってください。新しいリリースにはシェイプ処理のバグ修正が含まれています。

## Step 1: Word文書をプログラム的に作成 – ドキュメントの初期化

Word文書をプログラム的に作成する際に最初に行うことは、`Document` オブジェクトをインスタンス化することです。このオブジェクトはメモリ内の .docx ファイル全体を表します。

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document doc = new Document();

        // Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*このステップが重要な理由*: `Document` クラスはすべての Word 処理操作のエントリーポイントです。これがなければページや段落、シェイプを追加できません。

## Step 2: シェイプの追加 – 楕円の挿入

ここではチュートリアルの **how to add shape** 部分に取り組みます。Aspose.Words は多数のシェイプタイプ（Ellipse、Rectangle、TextBox など）をサポートしています。以下では幅と高さが 50 ポイントの楕円を挿入します。

```java
        // Insert an ellipse shape of size 50x50 points
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);

        // Position the shape (optional)
        ellipse.setLeft(100);
        ellipse.setTop(100);
```

`insertShape` メソッドは `Shape` オブジェクトを返し、色、線のスタイル、回転などをさらにカスタマイズできます。座標はポイント（1/72 インチ）で測定されます。

*シェイプを追加したい理由*: シェイプは透かし、装飾要素、または後で非表示や置換するプレースホルダーとして便利です。

## Step 3: シェイプの非表示 – Word でオブジェクトを見えなくする

**how to hide shape** の質問に答えるには、シェイプの `Hidden` プロパティを `true` に設定するだけです。これにより Word はシェイプを非表示オブジェクトとして扱い、文書ビューや印刷時に表示されません。

```java
        // Hide the shape so it does not appear in the rendered document
        ellipse.setHidden(true);
```

特定のユーザーや条件に対して **hide object in Word** が必要な場合は、ビジネスロジックに基づいて実行時にこのプロパティを切り替えることができます。

> **注:** 非表示のシェイプは文書の XML 構造の一部として残ります。後で `setHidden(false)` を設定すれば再表示できます。

## Step 4: 文書の保存

シェイプを追加し非表示にしたら、文書をディスクに書き込みます。

```java
        // Save the document as a .docx file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

Microsoft Word で `HiddenShapeDemo.docx` を開くと、楕円が非表示のため空白ページが表示されます。文書は他の普通の Word ファイルと同様に動作します。

## 完全な動作例

すべての要素を組み合わせた、完全で実行可能なプログラムは以下の通りです：

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a document programmatically
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: How to add shape – insert an ellipse (50x50 points)
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);
        ellipse.setLeft(100);
        ellipse.setTop(100);

        // Step 3: How to hide shape – hide the ellipse so it never appears
        ellipse.setHidden(true);

        // Step 4: Save the file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

**Expected output**

```
Document created successfully.
```

`HiddenShapeDemo.docx` を開くと空白ページが表示され、非表示の楕円は描画されません。これにより **hide object in Word** 操作が成功したことが確認できます。

## エッジケースとバリエーション

| 状況 | 変更点 | 理由 |
|-----------|----------------|-----|
| 楕円の代わりに長方形を非表示にする | `insertShape` で `ShapeType.RECTANGLE` を使用する | 異なるビジュアルプレースホルダー |
| 複数のシェイプを一度に非表示にする | `doc.getChildNodes(NodeType.SHAPE, true)` をループし、`setHidden(true)` を設定する | バルク処理に便利 |
| シェイプを印刷ビューでのみ表示する | `shape.setVisible(false)` と `shape.setPrint(true)` を設定する | Word は画面表示と印刷表示を区別するため |
| 別の測定単位を使用する | `builder.getDocument().getCompatibilityOptions().setMeasureUnit(MeasureUnit.INCHES)` を呼び出す | レイアウト要件に合わせる |

## よくある落とし穴

* **`setHidden(true)` の呼び出しを忘れる** – シェイプが通常通り表示されます。  
* **シェイプを非表示にする前に文書を保存する** – 順序が重要です。先に非表示にし、次に保存します。  
* **古い Aspose.Words バージョンを使用する** – 古いリリースでは `setHidden` API が存在しない場合があります。  

生成されたファイルは対象となる Microsoft Word のバージョンで必ずテストし、非表示状態が期待通りに動作することを確認してください。

## 結論

このガイドでは Aspose.Words for Java を使用して **Word文書をプログラム的に作成**、**シェイプの追加**、そして **Word でオブジェクトを非表示** にする方法を学びました。完全な例は、ドキュメントの初期化からシェイプが決して表示されないファイルの保存までの正確な手順を示しています。

ここからは以下を試せます：

* `ShapeType.LINE`、`ShapeType.TEXT_BOX` など他のシェイプタイプを試す。  
* 非表示シェイプとブックマークを組み合わせて動的テンプレートを作成する。  
* `setVisible` と `setPrint` プロパティを調査し、オブジェクトの可視性をより細かく制御する。

コーディングを楽しみ、Word 文書の自動化を満喫してください！

## 次に学ぶべきことは？

以下のチュートリアルは本ガイドで示した手法を基にした、密接に関連するトピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれ、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Aspose.Words for Java を使用して空白の Word 文書を作成する方法](/words/english/java/document-manipulation/how-to-create-blank-word-document-with-aspose-words-for-java/)
- [Java を使用して Word 文書でシェイプを非表示にする方法](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Java で Word 文書を作成 – 影効果付き長方形シェイプの追加](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}