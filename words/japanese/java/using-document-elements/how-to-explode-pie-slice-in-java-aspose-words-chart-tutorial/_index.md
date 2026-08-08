---
category: general
date: 2026-08-07
description: Aspose.Words を使用した Java でのパイチャートのスライスの分割方法。パイにリーダーラインを追加し、Word チャートを作成し、パイチャートのスライスをカスタマイズする方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode pie slice
- add leader lines to pie
- java create word chart
- customize pie chart slices
language: ja
lastmod: 2026-08-07
og_description: Java と Aspose.Words を使用して円グラフのスライスを分離表示する方法。このガイドでは、円グラフにリーダーラインを追加し、Word
  のチャートを作成し、円グラフのスライスをカスタマイズして視覚的インパクトを高める方法を紹介します。
og_image_alt: Screenshot of a Word document with an exploded pie chart created using
  Java Aspose.Words
og_title: Javaで円グラフのスライスを分離する方法 – Aspose.Words ガイド
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to explode pie slice in Java using Aspose.Words. Learn to add leader
    lines to pie, create Word chart, and customize pie chart slices.
  headline: How to explode pie slice in Java – Aspose.Words chart tutorial
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Pie Chart
title: Javaで円グラフのスライスを引き離す方法 – Aspose.Words チャートチュートリアル
url: /ja/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to explode pie slice in Java – Aspose.Words chart tutorial

Java で Word 文書内の **円グラフのスライスを分離（explode）** する方法を知りたい方のためのチュートリアルです。また、**円グラフにリーダーラインを追加** する方法、**java create word chart** オブジェクトの作成方法、そして **円グラフのスライスをカスタマイズ** して洗練された結果を得る方法も紹介します。このガイドの最後まで読むと、任意の Java プロジェクトに組み込める完全な実行可能サンプルが手に入ります。

![How to explode pie slice in Java – Aspose.Words chart](/images/pie-chart-exploded.png)

## Prerequisites

開始する前に、以下を用意してください。

* Java Development Kit (JDK) 8 以上
* 依存関係管理のための Maven または Gradle
* Aspose.Words for Java のライセンス（学習目的であれば無料評価版でも可）
* Java の構文とオブジェクト指向の基本的な知識

> **Pro tip:** Aspose.Words は無料トライアルを提供していますが、ライセンスを購入すると生成された文書から評価版の透かしが除去されます。

## What this tutorial covers

* 新規 Word 文書の作成  
* `DocumentBuilder` を使用した **円グラフ** の挿入  
* データポイントを強調するための **円グラフスライスの分離（explode）**  
* ラベルを見やすくするための **円グラフへのリーダーライン追加**  
* スライスの外観カスタマイズ（色や枠線など）  
* 文書をディスクに保存し、結果を確認する方法

---

## How to explode pie slice with Aspose.Words in Java

最初のステップはチャートオブジェクトを設定し、目的のスライスを分離することです。Aspose.Words は `Shape` クラスを通じてチャートを公開し、各スライスは `ChartPoint` として表されます。`Explosion` プロパティを設定することで、スライスを中心からどれだけ離すかを制御できます。

```java
// Step 1: Create a blank document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a pie chart (400x300 points)
Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
Chart chart = pieChart.getChart();

// Step 3: Explode the first slice (index 0) by 20 points
chart.getSeries().get(0).getPoints().get(0).setExplosion(20);
```

**Why it works:**  
`setExplosion(20)` はチャートエンジンに対し、スライスをチャートの中心から 20 ポイントだけオフセットするよう指示します。この値は相対的で、数値が大きいほど効果が顕著になります。インデックス（`get(1)`, `get(2)`, …）を変更すれば、任意のスライスを分離できます。

## Add leader lines to pie for clearer labels

リーダーラインはスライスのラベルとエッジを結びつけ、特にスライスが分離されている場合や多数の小さなセクションがある場合に有用です。`setLeaderLines(true)` 呼び出しで、シリーズ全体に対してこの機能を有効にします。

```java
// Step 4: Enable leader lines for the series
chart.getSeries().get(0).setLeaderLines(true);
```

**Why you need leader lines:**  
スライスが分離されると、デフォルトのラベルが他の要素と重なることがあります。リーダーラインはスライスからテキストボックスまで短い線を描画し、ラベルの可読性を保ちます。

## Java create Word chart – inserting data series

データのないチャートはほとんど役に立ちません。シリーズにカテゴリと値を設定する必要があります。以下では、市場シェアを表す 3 つのカテゴリを追加します。

```java
// Step 5: Populate the chart with data
ChartSeries series = chart.getSeries().get(0);
series.getDataLabel().setShowCategoryName(true); // show labels
series.getDataLabel().setShowPercentage(true);   // show percentages

// Add categories and values
series.getCategories().add("Product A");
series.getCategories().add("Product B");
series.getCategories().add("Product C");

series.getValues().add(45); // Product A = 45%
series.getValues().add(30); // Product B = 30%
series.getValues().add(25); // Product C = 25%
```

**Explanation:**  
`ChartSeries` はカテゴリ（スライス名）と数値データの両方を保持します。`ShowCategoryName` と `ShowPercentage` を有効にすると、チャートが自己説明的になり、先ほど追加したリーダーラインと相性が良くなります。

## Customize pie chart slices beyond explosion

スライスを分離するだけでなく、色や枠線の調整、さらにはスライス自体を非表示にすることもよくあります。以下のスニペットは、3 つの一般的なカスタマイズ例を示しています。

```java
// Step 6: Change slice colors and borders
ChartPoint pointA = series.getPoints().get(0); // Product A
ChartPoint pointB = series.getPoints().get(1); // Product B
ChartPoint pointC = series.getPoints().get(2); // Product C

// Set custom fill colors
pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50")); // green
pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3")); // blue
pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800")); // orange

// Add a thin border to each slice
for (ChartPoint pt : series.getPoints()) {
    pt.getFormat().getLine().setWeight(0.5);
    pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
}

// Optional: hide a slice (e.g., Product C) without removing data
pointC.setIsHidden(true);
```

**Why customize slices:**  
カスタムカラーは企業のブランディングに合わせるのに役立ち、枠線は印刷物での可読性を向上させます。スライスを非表示にすると、データモデルはそのままに視覚的な出力から特定のカテゴリを一時的に除外できます。

## Save the document and verify the result

最後に、文書をディスクに書き込みます。生成された `.docx` は Microsoft Word、LibreOffice、または対応ビューアで開くことができます。

```java
// Step 7: Save the document
String outputPath = "output/PieChartDemo.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

**Expected output:**  
`PieChartDemo.docx` を開くと、最初のスライス（Product A）が外側に分離され、各スライスからラベルへリーダーラインが伸び、スライスはカスタムの緑、青、オレンジ色で表示されます。非表示にしたスライス（Product C）は見えませんが、パーセンテージは合計で 100 % になるので、データはチャートのシリーズに残っています。

---

## Full, runnable example

以下は、Aspose.Words の依存関係をプロジェクトに追加した後にコピー＆ペーストして実行できる完全なプログラムです。

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a pie chart (400x300 points)
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = pieChart.getChart();

        // Explode the first slice to highlight it
        chart.getSeries().get(0).getPoints().get(0).setExplosion(20);

        // Enable leader lines for clearer labeling
        chart.getSeries().get(0).setLeaderLines(true);

        // Populate the chart with data
        ChartSeries series = chart.getSeries().get(0);
        series.getDataLabel().setShowCategoryName(true);
        series.getDataLabel().setShowPercentage(true);

        series.getCategories().add("Product A");
        series.getCategories().add("Product B");
        series.getCategories().add("Product C");

        series.getValues().add(45);
        series.getValues().add(30);
        series.getValues().add(25);

        // Customize slice colors and borders
        ChartPoint pointA = series.getPoints().get(0);
        ChartPoint pointB = series.getPoints().get(1);
        ChartPoint pointC = series.getPoints().get(2);

        pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50"));
        pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3"));
        pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800"));

        for (ChartPoint pt : series.getPoints()) {
            pt.getFormat().getLine().setWeight(0.5);
            pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
        }

        // Hide the third slice (optional)
        pointC.setIsHidden(true);

        // Save the document
        document.save("output/PieChartDemo.docx");
        System.out.println("Pie chart Word document created successfully.");
    }
}
```

**Dependency (Maven)**  

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Use the latest stable version -->
</dependency>
```


## What Should You Learn Next?

以下のチュートリアルは、本ガイドで示したテクニックを基にした、密接に関連するトピックをカバーしています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得したり、独自プロジェクトで代替実装アプローチを探求したりするのに役立ちます。

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to Load Word Documents with Aspose.Words Java: Comprehensive Guide](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}