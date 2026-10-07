---
category: general
date: 2026-09-27
description: JavaでWord文書に円グラフを挿入し、Wordで円グラフを作成、円グラフにパーセンテージを表示してデータを明確に把握する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- create pie chart in word
- show percentages on pie chart
- add chart to word document
- how to add leader lines
language: ja
lastmod: 2026-09-27
og_description: JavaでWord文書に円グラフを挿入する方法。このガイドでは、Wordで円グラフを作成し、円グラフにパーセンテージを表示し、リーダーラインを追加する手順を示します。
og_image_alt: Screenshot of a formatted pie chart inserted into a Word document
og_title: Javaを使用してWord文書に円グラフを挿入する方法
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  headline: How to insert a pie chart into a Word document using Java
  type: TechArticle
- description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  name: How to insert a pie chart into a Word document using Java
  steps:
  - name: Expected output
    text: '![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image
      alt="Formatted pie chart inserted into a Word document"}'
  - name: Changing slice values
    text: 'If you need custom data, replace the default series values:'
  - name: Multiple series (donut chart)
    text: While a simple pie chart has one series, Aspose.Words also supports donut
      charts with multiple series. Switch `ChartType.PIE` to `ChartType.DONUT` and
      repeat the series‑configuration steps.
  - name: Exporting to PDF
    text: If your downstream workflow requires PDF, call `doc.save("output/PieFormatted.pdf");`
      after the chart is built. The visual layout remains identical.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word automation
- Chart
title: Java を使用して Word 文書に円グラフを挿入する方法
url: /ja/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java を使用して Word 文書に円グラフを挿入する方法

Word ファイルに **円グラフを挿入する方法** が必要な場合、このガイドでは全工程を順を追って説明します。**Word で円グラフを作成する方法** を確認し、各スライスにパーセンテージを表示し、リーダーラインを追加して洗練された外観にする方法が分かります。

Word の自動化はしばしば重く感じられますが、Aspose.Words for Java を使用すれば、プログラムで完全にフォーマットされた文書を生成できます。このチュートリアルの最後までに、スタイルが適用された円グラフを含む Word 文書を生成する実行可能な Java スニペットが手に入ります。

## 前提条件

- Java 17 以降がインストールされていること
- 依存関係管理に Maven または Gradle を使用できること
- Aspose.Words for Java（バージョン 23.11 以上）をプロジェクトに追加していること
- Java 構文の基本的な知識があること

チャート API の事前経験は不要です。以下の手順ですべて、プロジェクトのセットアップから最終出力までカバーしています。

## 手順 1: Maven 依存関係の設定

`pom.xml` に Aspose.Words ライブラリを追加します。この単一の依存関係で `Document`、`DocumentBuilder`、およびチャートクラスにアクセスできます。

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.11</version>
</dependency>
```

Gradle を使用する場合、同等の設定は次のとおりです：

```groovy
implementation 'com.aspose:aspose-words:23.11'
```

> **プロのコツ:** バグ修正や新しいチャート機能の恩恵を受けるため、最新の安定版を使用してください。

## 手順 2: 新しいドキュメントとビルダーを作成する

`Document` オブジェクトは Word ファイルを表し、`DocumentBuilder` はコンテンツの挿入を可能にします。これは **Word 文書にチャートを追加する** 基礎となります。

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

ビルダーは現在、ドキュメント内の任意の場所にオブジェクトを配置できる状態です。

## 手順 3: 円グラフを挿入する

Aspose.Words は複数のチャートタイプをサポートしています。ここでは `ChartType.PIE` を選択します。サイズはポイントで指定します（1 ポイント = 1/72 インチ）。

```java
        // Step 3: Insert a pie chart with a size of 400x300 points
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

この段階では、チャートはプレースホルダー値を持つデフォルトのデータ系列を含んでいます。必要に応じて後でこれらの値を置き換えることができます。

## 手順 4: チャート系列にアクセスする

円グラフはスライスの値を保持する単一の系列を持ちます。書式設定を適用するためにそれを取得します。

```java
        // Step 4: Get the first (and only) series
        ChartSeries series = chart.getSeries().get(0);
```

## 手順 5: 最初のスライスを分離する

スライスを分離（エクスプロード）すると、特定のデータポイントに注目が集まります。重要な指標を強調したいときの一般的なビジュアル手法です。

```java
        // Step 5: Explode the first slice
        series.setExploded(true);
```

## 手順 6: 各スライスにパーセンテージを表示する

チャート上に直接パーセンテージを表示すると、データの洞察が向上します。これは **円グラフにパーセンテージを表示する** 要件を満たします。

```java
        // Step 6: Show percentages on each slice
        series.setShowPercentage(true);
```

## 手順 7: ラベルを明確にするためにリーダーラインを追加する

リーダーラインはスライスラベルと対応するセクションを結び、曖昧さを排除します。これは **リーダーラインの追加方法** を実現します。

```java
        // Step 7: Add leader lines so labels are clearly connected
        series.setShowLeaderLines(true);
```

## 手順 8: 文書を保存する

最後に、文書をディスクに書き込みます。書き込み権限のある任意のフォルダーを選択できます。

```java
        // Step 8: Save the document with the formatted pie chart
        doc.save("output/PieFormatted.docx");
    }
}
```

プログラムを実行すると `output/PieFormatted.docx` が作成されます。Microsoft Word でファイルを開くと、次のような円グラフが表示されます：

- 最初のスライスが分離されています。
- 各スライスにパーセンテージ値が表示されています。
- リーダーラインがパーセンテージから対応するスライスへ指しています。

### 期待される出力

![Word のフォーマット済み円グラフ](/images/pie-formatted.png){: .center-image alt="Word 文書に挿入されたフォーマット済み円グラフ"}

スクリーンショット（alt テキストは主要キーワードを使用）は最終的な外観を示しています。レポート、提案書、ダッシュボード向けの、クリーンでデータ駆動型の円グラフです。

## 一般的なバリエーションとエッジケース

### スライス値の変更

カスタムデータが必要な場合は、デフォルトの系列値を置き換えます：

```java
double[] values = {30, 45, 25};
String[] categories = {"Apples", "Bananas", "Cherries"};
series.getDataLabelCollection().clear(); // remove placeholder labels

for (int i = 0; i < values.length; i++) {
    series.getData().add(values[i]);
    series.getCategory().add(categories[i]);
}
```

### 複数系列（ドーナツチャート）

シンプルな円グラフは 1 系列ですが、Aspose.Words は複数系列のドーナツチャートもサポートしています。`ChartType.PIE` を `ChartType.DONUT` に変更し、系列設定の手順を繰り返します。

### PDF へのエクスポート

下流のワークフローで PDF が必要な場合は、チャート作成後に `doc.save("output/PieFormatted.pdf");` を呼び出します。ビジュアルレイアウトは同一です。

## 完全なソースリスト

以下は、IDE にコピー＆ペーストできる完全な単一ファイルの Java コードです。

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300‑point pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Access the single series in the pie chart
        ChartSeries series = chart.getSeries().get(0);

        // Explode the first slice for emphasis
        series.setExploded(true);

        // Show percentages on each slice
        series.setShowPercentage(true);

        // Add leader lines for clear label connections
        series.setShowLeaderLines(true);

        // Save the document
        doc.save("output/PieFormatted.docx");
    }
}
```

`mvn compile exec:java -Dexec.mainClass=PieChartExample`（または同等の Gradle コマンド）でプログラムをコンパイル・実行します。生成された Word ファイルには完全にフォーマットされた円グラフが含まれます。

## 結論

これで、Java を使用して Word 文書に **円グラフを挿入する方法**、**Word で円グラフを作成する方法**、**円グラフにパーセンテージを表示する方法**、そしてリーダーライン付きで **Word 文書にチャートを追加する方法** が分かりました。完全な例は各ステップを実演し、コードがそのように書かれている理由を説明し、カスタマイズのヒントを提供します。

次に、以下を検討してみてください：

- カスタムフォントでデータラベルを追加する（**円グラフにパーセンテージを表示する** のバリエーション）
- 1 つの文書に複数のチャートを組み合わせる（**Word 文書にチャートを追加する** のユースケース）
- テーブルとチャートを組み合わせたレポート自動生成

色やスライスの順序、PDF へのエクスポートなどを自由に試してみてください。コーディングを楽しんで！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Aspose.Words for Java を使用して縦棒グラフを作成する方法](/words/english/java/document-conversion-and-export/using-charts/)
- [Word 文書でチャート軸を非表示にする方法](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Aspose.Words for .NET を使用して Word に折れ線グラフを作成する方法](/words/english/net/working-with-charts/create-chart-using-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}