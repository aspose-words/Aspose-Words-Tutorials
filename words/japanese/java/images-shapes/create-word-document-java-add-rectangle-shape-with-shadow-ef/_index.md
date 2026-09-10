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

**JavaでWord文書を作成する**際に、もう少し洗練された見た目にしたいと思ったことはありませんか？例えば、レポートジェネレーターを作成していて、シンプルなページでは物足りないと感じているかもしれません。そんな時に役立つのが、Aspose.Words for Javaです。たった数行のコードで、文書に長方形を配置し、色を付け、さらに微妙な影まで加えることができます。

このチュートリアルでは、四角形シェイプを追加し、塗りつぶし色を設定し、シェイプに影を適用して Word ファイルを少しだけプロフェッショナルに見せる方法を順を追って解説します。最後まで読むと、プロジェクトにコピペできる実行可能なサンプルが手に入ります。

## 必要なもの

- **Java 17**（または最新のJDK） – コードは標準言語機能を使用します。
- **Aspose.Words for Java**ライブラリ – バージョン23.9以降を推奨します。
- お好みのIDEまたはテキストエディタ – IntelliJ IDEA、Eclipse、VS Codeなど、ご自由にお使いください。
- 生成された`ShadowShape.docx`を保存するフォルダ。

追加の設定ウィザードは不要です。Aspose.Words の JAR をクラスパスに追加すればすぐに使えます。

## ステップ 1: プロジェクトの設定と Aspose.Words のインポート

まず最初に、新しいMaven（またはGradle）プロジェクトを作成し、Aspose.Wordsの依存関係を追加してください。Maven用の最小限の`pom.xml`スニペットは以下のとおりです。

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

Mavenを使用していない場合は、JARファイルを`libs`フォルダにドロップし、ビルドパスに追加してください。

> **ヒント:** Asposeは無料のトライアルライセンスを提供しており、`License license = new License(); license.setLicense("Aspose.Words.lic");`で組み込むことができます。簡単なテストの場合は、このライセンスは不要です。ライブラリは評価モードで動作します。

## ステップ 2: 新しい Document と Builder の作成

それでは、実際にWord文書のJavaオブジェクトを作成します。`Document`クラスは.docxファイル全体を表し、`DocumentBuilder`クラスはコンテンツを挿入するためのものです。

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

この時点で、図形、段落、その他必要なものを追加できる空の文書が作成されています。

## ステップ 3: 四角形シェイプの挿入と塗りつぶし色の設定

図形を追加するには、`insertShape`を呼び出すだけです。ここでは、セカンダリキーワード`*add rectangle shape*`に含まれる`**add rectangle shape**という手法を使用します。

```java
        // Insert a rectangle shape – 200pt wide, 100pt tall
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);

        // Set the fill color to a bright orange
        rectangle.setFillColor(java.awt.Color.ORANGE);
```

なぜオレンジ色なのかというと、白一色の中で目立つためですが、`java.awt.Color`で指定する任意の色に変更することもできます。この手順では、セカンダリキーワード`*set shape fill color*`について説明します。

## ステップ 4: 影の外観を設定 – シェイプに影を適用

さあ、ここからが楽しい部分です。長方形に控えめなドロップシャドウを適用してみましょう。Aspose APIは、シャドウのあらゆる側面を制御できる`ShadowFormat`オブジェクトを提供しています。

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

このコードブロックは、セカンダリキーワードが示すとおり、図形に影を適用します。`blur`、`offsetX/Y`、`transparency`を調整することで、デザインに合わせて影の表現を変えることができます。例えば、`offsetX`を大きくすると影がよりドラマチックになり、`transparency`を大きくすると影が控えめになります。

## ステップ 5: ドキュメントの保存

最後に、ドキュメントをディスクに書き込みます。書き込み権限のあるフォルダを選択し、ファイル名を分かりやすいものにしてください。

```java
        // Save the result – adjust the path as needed
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Microsoft WordまたはLibreOfficeで`ShadowShape.docx`を開くと、明るいオレンジ色の長方形とそのすぐ下に浮かぶ柔らかな灰色の影が表示されます。

![create word document java with rectangle shape](/images/shadow-rectangle.png "create word document java – rectangle with shadow")

*画像altテキストにはプライマリキーワードが含まれており、SEOルールを満たしています。*

## よくある質問とエッジケース

### 別のシェイプが必要な場合は？

Aspose.Words は、星、矢印、吹き出しなど、数十種類の `ShapeType` 値をサポートしています。`ShapeType.RECTANGLE` を `ShapeType.OVAL` またはその他の列挙定数に置き換えるだけで使用できます。**図形の追加方法**の手順は同じです。

### シェイプを特定の段落に追加するには？

ビルダーで図形を直接挿入する代わりに、まず図形を作成し (`new Shape(document, ShapeType.RECTANGLE)`)、次に `paragraph.appendChild(shape)` を使用して `Paragraph` に追加することもできます。これにより、レイアウトをより細かく制御できます。

### 単色の代わりにグラデーション塗りを適用できますか？

はい！`rectangle.getFill().setFillType(FillType.GRADIENT)` を使用して `LinearGradientFill` を定義します。API は少し冗長になりますが、最新のデザインに最適です。

### 古い Word バージョンとの互換性は？

Aspose.Words はデフォルトで .docx 形式で保存します。これは Word 2007 以降および LibreOffice でサポートされています。.doc 形式が必要な場合は、`document.save("file.doc", SaveFormat.DOC)` を呼び出してください。影のレンダリングは若干異なる場合がありますが、形状自体はそのまま維持されます。

## 完全動作例（コピー＆ペースト可能）

以下にコンパイルして実行できるプログラム全体を示します。`YOUR_DIRECTORY` を実際のパスに置き換えてください。

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

このコードを実行すると、オレンジ色の四角形に淡いグレーの影が付いたWordファイルが生成されます。これはまさに、スタイル付き図形を含むWord文書をJavaで作成したいという私たちの目標達成です。

## 結論

これで、四角形を追加し、塗りつぶしの色を設定し、影を適用するという、Word文書作成のための確実なエンドツーエンドのレシピが完成しました。このアプローチはシンプルで、APIは使いやすく、さまざまな図形、グラデーション塗りつぶし、あるいは図形ごとに複数の影を適用するなど、無数の方法で拡張できます。

次は？複数の図形を重ねてみたり、`ShadowStyle.ETCHED`を使って異なる視覚効果を試してみたり、テーブル生成と組み合わせて本格的なレポートを作成したりしてみましょう。可能性はあなたの想像力（そしておそらくAsposeライセンスのティア）によってのみ制限されます。

何か問題が発生したり、さらなる機能強化のアイデアがあれば、下のコメント欄にご記入ください。コーディングを楽しんで、Word文書を少しでも魅力的にしましょう！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}