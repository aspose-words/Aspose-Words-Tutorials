---
category: general
date: 2026-05-26
description: JavaのWord文書で長方形の図形を作成し、影効果を適用します。図形に影を追加し、影の距離を設定し、ファイルを保存する方法を学びましょう。
draft: false
keywords:
- create rectangle shape
- apply shadow effect
- create word document java
- add shape shadow
- set shadow distance
language: ja
og_description: Java の Word ドキュメントで長方形の図形を作成し、影効果を適用し、図形の影を追加し、Aspose.Words で影の距離を設定します。
og_title: JavaのWord文書で矩形シェイプを作成する – 完全ガイド
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create rectangle shape in a Java Word document and apply shadow effect.
    Learn how to add shape shadow, set shadow distance, and save the file.
  headline: Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in a Java Word document and apply shadow effect.
    Learn how to add shape shadow, set shadow distance, and save the file.
  name: Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide
  steps:
  - name: “Can I use a different shape?”
    text: Absolutely. Replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`, `ShapeType.LINE`,
      or any other supported enum. The rest of the shadow code stays the same.
  - name: “What if I need multiple shadows?”
    text: Aspose.Words only supports a single shadow per shape. To simulate multiple
      shadows, duplicate the shape, offset each copy, and adjust the transparency.
  - name: “Is the shadow visible in LibreOffice?”
    text: Yes—Aspose.Words writes standard OOXML, which LibreOffice interprets correctly.
      The shadow may look slightly different due to rendering engines, but the effect
      persists.
  - name: “How do I change the shadow color to match my brand?”
    text: Just swap `java.awt.Color.GRAY` with any `java.awt.Color` you prefer, such
      as `new java.awt.Color(0, 120, 215)` for a corporate blue.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word Automation
title: JavaのWord文書で長方形シェイプを作成する – 完全ステップバイステップガイド
url: /ja/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java Word ドキュメントで矩形シェイプを作成 – 完全ステップバイステップガイド

Java Word ドキュメントで **create rectangle shape** を作成したいと思ったことはありますか？しかし、どこから始めればよいか分からないことも多いでしょう。プログラムでレポートや請求書を生成する際、多くの開発者がこの壁にぶつかります。このチュートリアルでは、**create rectangle shape** の作成方法、洗練された影の適用方法、そして影の距離を微調整してプロフェッショナルな仕上がりにする手順を詳しく解説します。

Aspose.Words for Java を使用します。この堅牢なライブラリを使えば、Microsoft Office をインストールせずに Word ファイルを操作できます。本ガイドの最後までに、**create word document java** プロジェクトで **add shape shadow**、**apply shadow effect**、**set shadow distance** を数行のコードで実装できるようになります。

---

## 作成するもの

- シアンの矩形を含む新しい `.docx` ファイル。
- ぼかしがかかり、角度が付いており、部分的に透明なリアルなドロップシャドウ。
- シェイプから影までの距離を完全に制御。
- Maven または Gradle プロジェクトにそのまま組み込める、すぐに実行可能な Java クラス。

外部ツール不要、手動の UI 操作も不要—純粋にコードだけです。

## 前提条件

- Java 8 以上（コードは Java 11、Java 17 でも動作します）。
- Aspose.Words for Java ライブラリ（Maven Central から入手可能）。
- お好みの IDE またはテキストエディタ（IntelliJ IDEA、Eclipse、VS Code など）。
- Java 構文の基本的な知識。

Maven の依存関係を追加したことがない場合は、以下の簡単なスニペットをご覧ください：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

それでは、始めましょう。

## ステップ 1: Word ドキュメントで矩形シェイプを作成

最初に必要なのは空のドキュメントと `DocumentBuilder` です。builder はドキュメントに書き込むペンのようなものです。これが用意できたら、単一のメソッド呼び出しで **create rectangle shape** が可能です。

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape of 150x80 points.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        // Make the shape visible by filling it with cyan.
        rectangleShape.setFillColor(java.awt.Color.CYAN);
```

> **重要な理由:** `insertShape` メソッドはジオメトリを作成するだけでなく、シェイプをドキュメントの内部コレクションに追加するため、すぐにスタイリングを開始できます。

## ステップ 2: シェイプに影効果を適用

矩形がページ上に配置されたので、**apply shadow effect** を行います。影は奥行きを与え、シェイプがページから浮き上がっているように見せ、レポートの可読性を向上させる微妙な UI 改善です。

```java
        // Retrieve the shadow format object.
        ShadowFormat shadowFormat = rectangleShape.getShadowFormat();

        // Enable the shadow and configure its appearance.
        shadowFormat.setVisible(true);          // Turn the shadow on.
        shadowFormat.setBlur(5.0);              // Soft blur radius.
        shadowFormat.setAngle(45.0);            // Direction of the shadow.
        shadowFormat.setColor(java.awt.Color.GRAY); // Shadow color.
        shadowFormat.setTransparency(0.3);     // 30% transparent.
```

> **プロのコツ:** `5.0` のぼかしは画面表示のドキュメントで自然に見えます。印刷する場合は、ぼやけた外観を防ぐためにやや低めの値にすると良いでしょう。

## ステップ 3: 影の距離を設定 – 配置の微調整

影はぼかしだけでなく、適切なオフセットも必要です。ここで **set shadow distance** を行います。`7.0` ポイントの距離は、目立ちすぎず、しかし確実に見えるほどの控えめなオフセットを作ります。

```java
        // Define how far the shadow sits from the shape.
        shadowFormat.setDistance(7.0); // Distance in points.
```

> **もっと大きなオフセットが必要な場合は？** 値を上げ、よりタイトにしたい場合は下げます。距離は角度と組み合わせて影を正しく配置することを忘れないでください。

## ステップ 4: ドキュメントを保存 – 作業を永続化

最後に、ドキュメントをディスクに書き込みます。ファイルの保存先は好きなパスに変更してください。

```java
        // Save the document with the rectangle and its shadow.
        doc.save("YOUR_DIRECTORY/shadow.docx");
    }
}
```

クラスを実行すると `shadow.docx` ファイルが作成され、Microsoft Word や LibreOffice で開くと、45° の角度で 7 ポイントオフセットされたソフトなグレーの影付きシアン矩形が表示されます。

## 完全な動作例

以下に、コピー＆ペースト可能な完全なコードを示します。すべてのインポート、コメント、最終的な `save` 呼び出しが含まれています。

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape of the desired size.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        // Step 3: Apply a fill color to make the shape visible.
        rectangleShape.setFillColor(java.awt.Color.CYAN);

        // Step 4: Configure the shape's shadow effect.
        ShadowFormat shadowFormat = rectangleShape.getShadowFormat();
        shadowFormat.setVisible(true);          // Enable the shadow.
        shadowFormat.setBlur(5.0);              // Set the blur radius.
        shadowFormat.setDistance(7.0);          // Define how far the shadow is from the shape.
        shadowFormat.setAngle(45.0);            // Set the direction of the shadow.
        shadowFormat.setColor(java.awt.Color.GRAY); // Choose the shadow color.
        shadowFormat.setTransparency(0.3);      // Make the shadow partially transparent.

        // Step 5: Save the document with the shaped shadow.
        doc.save("YOUR_DIRECTORY/shadow.docx");
    }
}
```

**期待される出力:** `shadow.docx` を開くと、1 ページ目の中央にシアンの矩形が表示され、右下にわずかにオフセットされた微妙なグレーの影が落ちます。影のぼかしと透明度により、自然光のように見えます。

## よくある質問とエッジケース

### 「別のシェイプを使用できますか？」

もちろんです。`ShapeType.RECTANGLE` を `ShapeType.OVAL`、`ShapeType.LINE`、または他のサポートされている enum に置き換えてください。影のコードはそのままです。

### 「複数の影が必要な場合は？」

Aspose.Words はシェイプごとに単一の影しかサポートしていません。複数の影をシミュレートするには、シェイプを複製し、各コピーをオフセットし、透明度を調整します。

### 「LibreOffice でも影は表示されますか？」

はい。Aspose.Words は標準的な OOXML を出力するため、LibreOffice でも正しく解釈されます。レンダリングエンジンの違いにより若干見え方が変わることがありますが、効果は維持されます。

### 「ブランドに合わせて影の色を変更するには？」

`java.awt.Color.GRAY` を任意の `java.awt.Color` に置き換えるだけです。例えば、企業のブルーにしたい場合は `new java.awt.Color(0, 120, 215)` を使用します。

## 画像イラスト

![create rectangle shape in Java Word document](https://example.com/images/rectangle-shadow.png)

*Alt text:* **create rectangle shape** のイラストで、Word ドキュメント内にシアンの矩形とグレーのドロップシャドウが表示されています。

## まとめと次のステップ

ここでは、Aspose.Words for Java を使用して **create rectangle shape**、**apply shadow effect**、**add shape shadow**、**set shadow distance** を行う方法を解説しました。コードは自己完結型で、最新の JDK で動作し、配布可能な洗練された `.docx` ファイルを生成します。

さらに進めたいですか？以下を試してみてください：

- `builder.moveTo(rectangleShape.getAbsolutePosition())` を使用して矩形内にテキストを追加する。
- シェイプのテーブルを作成して図を構築する。
- ドキュメントを PDF にエクスポートする（`doc.save("output.pdf", SaveFormat.PDF);`）。

これらはすべて、先ほど学んだ基本に基づいているため、例を拡張するのが容易に感じられるでしょう。

## 最後に

**create word document java** のようなシェイプや影付けのタスクをマスターすれば、レポート、契約書、マーケティング資料の自動化で大きな優位性を得られます。ここで示したアプローチはクリーンで保守性が高く、何よりも必要なビジュアルスタイルに合わせて簡単に調整できます。

コードを実行し、ぼかし、角度、距離を調整して、ドキュメントが平凡から洗練されたものへと変化する様子をご覧ください。問題が発生したら下にコメントを残してください。喜んでお手伝いします。

コーディングを楽しんで！

## 関連チュートリアル

- [Create Word Document Java – 影効果付き矩形シェイプの追加](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words for Java の DocumentBuilder を使用してフォームフィールドを作成しコンテンツを追加する方法](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words for Java でバーコード生成付き Word から PDF を作成](/words/english/java/document-conversion-and-export/using-barcode-generation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}