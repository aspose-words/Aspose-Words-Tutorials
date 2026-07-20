---
category: general
date: 2026-07-20
description: Javaで円グラフを挿入するステップバイステップガイド。スライスを分離する方法、円グラフを回転させる方法、スライスをハイライトする方法、円グラフのスライスをカスタマイズする方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to explode slice
- how to rotate pie chart
- highlight pie chart slice
- customize pie chart slice
language: ja
lastmod: 2026-07-20
og_description: Javaで円グラフを挿入し、スライスを分離する方法、円グラフを回転させる方法、スライスをハイライトする方法、そして円グラフのスライスをカスタマイズして洗練されたビジュアルレポートを作成する方法をマスターしましょう。
og_image_alt: Screenshot showing an inserted pie chart with an exploded and rotated
  slice
og_title: Javaで円グラフを挿入 – 分割表示、回転、ハイライト
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Insert pie chart in Java with a step‑by‑step guide. Learn how to explode
    slice, how to rotate pie chart, highlight pie chart slice and customize pie chart
    slice.
  headline: Insert Pie Chart in Java – Explode, Rotate & Highlight Slices
  type: TechArticle
tags:
- Java
- charting
- visualization
title: Javaで円グラフを挿入 – スライスを分離、回転、ハイライト
url: /ja/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Javaで円グラフを挿入 – スライスの爆発、回転、ハイライト

Ever needed to **insert pie chart** in a Java report but weren’t sure how to make a single slice pop out? You’re not the only one. Whether you’re building a dashboard, generating an invoice, or just visualizing survey results, a well‑styled pie chart can turn raw numbers into instantly understandable insight.

このチュートリアルでは、完全な実行可能サンプルを通じて、円グラフの挿入方法、**how to explode slice**、**how to rotate pie chart**、さらにはカスタムカラーで **highlight pie chart slice** する方法を示します。最後まで読むと、人気の *JFreeChart* ライブラリ（または類似の API）を使用する任意の Java プロジェクトに組み込める再利用可能なスニペットが手に入ります。

## 前提条件

- Java 17 以降（コードは古いバージョンでもコンパイルできますが、簡潔さのためにモダンな `var` 構文を使用します）。
- Maven または Gradle を使用して `org.jfree:jfreechart` 依存関係を取得します。
- Java クラスとチャートビルダーの概念に関する基本的な理解。

Maven プロジェクトにライブラリを追加したことがない場合は、以下を `pom.xml` に貼り付けるだけです：

```xml
<dependency>
    <groupId>org.jfree</groupId>
    <artifactId>jfreechart</artifactId>
    <version>1.5.4</version>
</dependency>
```

これだけです—追加の設定は不要です。

## ステップ 1: Insert Pie Chart – ビルダーとチャートオブジェクトの作成

まず最初に、チャートを生成する *ビルダー*（工場のようなもの）が必要です。JFreeChart では `ChartFactory` がその重い作業を担います。

```java
import org.jfree.chart.ChartFactory;
import org.jfree.chart.JFreeChart;
import org.jfree.data.general.DefaultPieDataset;

public class PieChartDemo {

    public static JFreeChart createPieChart() {
        // Prepare the data set
        var dataset = new DefaultPieDataset();
        dataset.setValue("Apples", 40);
        dataset.setValue("Bananas", 30);
        dataset.setValue("Cherries", 20);
        dataset.setValue("Dates", 10);

        // Insert pie chart with a width of 400 and height of 300
        JFreeChart chart = ChartFactory.createPieChart(
                "Fruit Distribution", // chart title
                dataset,              // data
                true,                 // include legend
                true,                 // tooltips
                false                 // URLs
        );
        return chart;
    }
}
```

なぜデータセットから始めるかというと、チャート自体は数値を視覚的にラップしたものに過ぎないからです。ここで **inserting pie chart** を行うことで、すでに 400 × 300 のキャンバスが用意されます（サイズは画像にレンダリングする際に適用されます）。

## ステップ 2: How to Explode Slice – 最初のセグメントを強調

チャートが作成されたので、最初のスライスを目立たせましょう。スライスを爆発させる（explode）ことで、円から少し離れた位置に描画され、読者の目を引きます。

```java
import org.jfree.chart.plot.PiePlot;
import org.jfree.chart.plot.PiePlotState;

public static void explodeFirstSlice(JFreeChart chart) {
    // Grab the plot from the chart – this is where we tweak appearance
    PiePlot plot = (PiePlot) chart.getPlot();

    // Explode the first slice (index 0) to highlight it
    // The key "Apples" corresponds to the first entry we added
    plot.setExplodePercent("Apples", 0.15); // 15% outward
}
```

メソッド名に **how to explode slice** フレーズを使用していることに注目してください。これにより意図が明確になります。`setExplodePercent` メソッドはキー（スライスのラベル）とパーセンテージを受け取り、必要に応じて「ポップアウト」距離を調整できます。

## ステップ 3: How to Rotate Pie Chart – 開始角度の変更

デフォルトの円グラフは 12 時の位置から開始します。場合によっては、最初のスライスを別の位置から始めたいことがあります—デザインモックアップに合わせるためや、別のチャートと揃えるためなどです。

```java
public static void rotateChart(JFreeChart chart, double startAngle) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Rotate the chart so the first slice starts at the given angle (degrees)
    plot.setStartAngle(startAngle);
}
```

`rotateChart(chart, 45)` を呼び出すと、全体の円が回転し、“Apples” スライスが 45 度の角度から開始します。これは **how to rotate pie chart** の要件通りです。

## ステップ 4: Highlight Pie Chart Slice – カスタムカラーとラベル

スライスを爆発させるだけでなく、スライスに固有の色や太字ラベルを付けて、**highlight pie chart slice** を実現したい場合もあります。

```java
import java.awt.Color;
import org.jfree.chart.labels.StandardPieSectionLabelGenerator;

public static void customizeSlice(JFreeChart chart) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Set a vivid color for the "Apples" slice
    plot.setSectionPaint("Apples", new Color(0xFF5722)); // deep orange

    // Make the label display both key and value in bold
    plot.setLabelGenerator(new StandardPieSectionLabelGenerator(
            "{0}: {1} ({2})")); // key: value (percent)
    plot.setLabelFont(plot.getLabelFont().deriveFont(java.awt.Font.BOLD));
}
```

ここでは塗りとラベルスタイルを変更することで **customize pie chart slice** を行っています。ブランドの配色やフォントに合わせて色やフォントを自由に変更してください。

## ステップ 5: Render the Chart to an Image（オプションだが便利）

実際のアプリケーションの多くは、チャートを PNG、JPEG、あるいは PDF として出力する必要があります。以下はチャートをファイルに書き出す簡単な方法です。

```java
import java.io.File;
import org.jfree.chart.ChartUtils;

public static void saveChart(JFreeChart chart, String filename) throws Exception {
    int width = 400;
    int height = 300;
    File outFile = new File(filename);
    ChartUtils.saveChartAsPNG(outFile, chart, width, height);
}
```

フロー全体を実行すると、以下のような 400 × 300 の PNG が生成されます：

![Insert pie chart example](image.png){: alt="爆発および回転したスライスを示す円グラフ挿入例"}

## 完全な動作例

すべてを組み合わせた、`main` メソッドの完全なコードを以下に示します。新しい Java クラスにコピー＆ペーストして実行できます：

```java
public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Insert the pie chart
        JFreeChart chart = createPieChart();

        // 2️⃣ Explode the first slice
        explodeFirstSlice(chart);

        // 3️⃣ Rotate the chart 45° so the first slice starts at 45 degrees
        rotateChart(chart, 45);

        // 4️⃣ Highlight and customize the exploded slice
        customizeSlice(chart);

        // 5️⃣ Save to disk (optional)
        saveChart(chart, "fruit-pie.png");

        System.out.println("Pie chart generated: fruit-pie.png");
    }

    // ... (include the helper methods from steps 1‑4 here) ...
}
```

### 期待される出力

プログラムを実行すると **fruit-pie.png** というファイルが作成されます。開くと以下が確認できます：

- タイトルが “Fruit Distribution” の 400 × 300 の円グラフ。
- “Apples” スライスが 15 % 爆発（外側へ）しています。
- 全体のチャートが回転し、“Apples” が 45 度の位置から開始しています。
- 爆発した

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした、密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Aspose.Words for Java を使用したカラムチャートの作成方法](/words/english/java/document-conversion-and-export/using-charts/)
- [散布図の挿入](/words/hindi/net/programming-with-charts/insert-scatter-chart/)
- [エリアチャートの挿入](/words/hindi/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}