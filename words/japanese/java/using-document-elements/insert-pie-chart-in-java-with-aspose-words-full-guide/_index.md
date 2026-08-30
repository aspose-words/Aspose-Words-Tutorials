---
category: general
date: 2026-07-29
description: Aspose.Words for Java を使用して円グラフを挿入し、ドーナツ グラフの作成方法、円グラフの書式設定、Word のチャート書式設定、チャートサイズのカスタマイズ方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- generate doughnut chart
- format pie chart
- format chart word
- customize chart size
language: ja
lastmod: 2026-07-29
og_description: Aspose.Words for Javaで円グラフを挿入し、ドーナツグラフの生成、円グラフの書式設定、Word のチャート書式設定、チャートサイズのカスタマイズをすばやく学び、プロフェッショナルな文書を作成します。
og_image_alt: Screenshot showing a Word document with an inserted pie chart created
  by Aspose.Words Java API
og_title: Javaで円グラフを挿入 – 完全なAspose.Wordsチュートリアル
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Insert pie chart using Aspose.Words for Java and learn how to generate
    doughnut chart, format pie chart, format chart Word, and customize chart size.
  headline: Insert pie chart in Java with Aspose.Words – Full Guide
  type: TechArticle
- questions:
  - answer: The evaluation version works fine for testing, but it adds a watermark.
      Drop your `aspose.words.lic` file in the classpath for a clean output.
    question: Do I need a license?
  - answer: 'Absolutely. Add the following dependency to your `pom.xml`:'
    question: Can I use this with Maven?
  - answer: Loop over `pieChart.getSeries()` and apply `setExplosion`, `setFillColor`,
      or other formatting per series. That’s the way to **format pie chart** for multi‑dimensional
      data.
    question: What if I have more than one series?
  - answer: Yes—once saved, you can open the document and manually adjust colors,
      fonts, or even convert the pie to a bar chart if you need to.
    question: Is the chart editable in Word after generation?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Chart
- Document Generation
- Word Automation
title: JavaでAspose.Wordsを使用して円グラフを挿入する – 完全ガイド
url: /ja/java/using-document-elements/insert-pie-chart-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insert pie chart in Java with Aspose.Words – Complete Guide

Java のコードから Word 文書に **円グラフを挿入** したいと思ったことはありませんか？ 同じ壁にぶつかる開発者は多いです。良いニュースは、Aspose.Words for Java を使えば数行のコードで実現でき、さらに **ドーナツ グラフの生成**、**円グラフの書式設定**、**Word のチャート書式設定**、**チャートサイズのカスタマイズ** も簡単に行えることです。

このチュートリアルでは、空の文書を作成し、円グラフを挿入し、いくつかのビジュアルプロパティを調整し、最終的にファイルを保存する実践的な例を順に解説します。最後まで読めば、チャート自動化が必要な任意の Java プロジェクトに貼り付け可能な再利用可能なスニペットが手に入ります。余計なライブラリや Office の相互運用は不要で、クリーンなコンパイル済み Java だけです。

## What You’ll Need

- **Java 17**（または最近の JDK；API は下位互換です）
- **Aspose.Words for Java** 22.12 以上 – Maven アーティファクトまたは Aspose サイトから .jar を取得してください。
- 手軽に `main` メソッドを実行できる IDE（IntelliJ IDEA、Eclipse、VS Code など）
- 任意：評価版の透かしを除去したい場合はライセンス ファイル

これらが揃ったら、すぐにコードに取り掛かれます。

## Step 1: Insert pie chart with Aspose.Words

最初に **円グラフを挿入** します。このステップが以降のすべての作業の土台となり、チャート オブジェクトから系列、データ ポイント、ビジュアル調整にアクセスできます。

```java
import com.aspose.words.*;

public class PieChartFormatting {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with a specific size (500x400 points)
        Chart pieChart = builder.insertChart(ChartType.PIE, 500, 400);
```

> **Why this matters:** `DocumentBuilder.insertChart` はチャートを作成するだけでなく、操作可能な `Chart` オブジェクトを返します。幅と高さの引数で **チャートサイズのカスタマイズ** が作成時に行えるため、後からリサイズする必要がありません。

## Step 2: Generate doughnut chart (optional)

デザイン上、真ん中に穴が必要な場合（典型的なドーナツ グラフ）も、Aspose ならワンライナーです。同じ `Chart` インスタンスを `ChartType.DONUT` に変更し、穴のサイズを設定するだけです。

```java
        // Optional: Turn the pie into a doughnut by setting the hole size (0‑100%)
        pieChart.getChartData().setHoleSize(30); // 30% hole makes it a doughnut chart
```

> **Tip:** 穴のサイズは `ChartType.DONUT` の場合にのみ有効です。`PIE` のままでは呼び出しは無視されますので、自由に試してみてください。

## Step 3: Format pie chart slices

視覚的に重要なスライスを強調したいことが多いです。ここでは **円グラフの書式設定** として、最初のスライスを 20 ポイント外側に「爆発」させます。これにより、最も重要なデータが目立ちます。

```java
        // Explode the first slice to emphasize it
        pieChart.getSeries().get(0).setExplosion(20);
```

> **Pro tip:** 複数系列がある場合は `pieChart.getSeries()` をループし、個別に色・枠線・データ ラベルを設定できます。これが **Word のチャート書式設定** をリッチに行うコツです。

## Step 4: Add data to the chart

データのないチャートは装飾的な図形に過ぎません。ここではシンプルなデータセット（例：四半期ごとの売上）を投入します。

```java
        // Populate the chart with sample data
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataLabels().setShowCategoryName(true);
        series.getDataLabels().setShowValue(true);

        // Clear any default points and add our own
        series.getPoints().clear();
        series.getPoints().add(new ChartPoint(30)); // Q1
        series.getPoints().add(new ChartPoint(45)); // Q2
        series.getPoints().add(new ChartPoint(15)); // Q3
        series.getPoints().add(new ChartPoint(10)); // Q4
```

> **Why we do this:** 明示的に `ChartPoint` オブジェクトを追加することで、ビジネスロジックが正確に反映されます。`setShowCategoryName` と `setShowValue` は **円グラフの書式設定** の一環で、ラベルと数値の両方を表示します。

## Step 5: Fine‑tune appearance (customize chart size & style)

初期サイズ以外にも、凡例、タイトル、データ ラベルのフォントなどを調整したい場合があります。これらすべてが **チャートサイズのカスタマイズ** と全体的な書式設定に含まれます。

```java
        // Set a title for the chart
        ChartTitle title = pieChart.getTitle();
        title.setText("Quarterly Sales Distribution");
        title.getFont().setSize(14);
        title.getFont().setBold(true);

        // Move the legend to the right side
        ChartLegend legend = pieChart.getLegend();
        legend.setPosition(LegendPosition.RIGHT);
        legend.getFont().setSize(10);

        // Adjust the overall chart size again if needed
        pieChart.setWidth(600);   // width in points
        pieChart.setHeight(450);  // height in points
```

> **Edge case:** 後で文書を PDF にエクスポートする場合、サイズがポイント単位で定義されているためベクターデータは鮮明なままです。これは **Word のチャート書式設定** と下流フォーマットの両方に有利です。

## Step 6: Save and view the document

最後のステップは `doc.save` を呼び出すだけです。これにより `.docx` ファイルが生成され、Microsoft Word、LibreOffice、または OpenXML をサポートする任意のビューアで開くことができます。

```java
        // Save the document containing the formatted chart
        doc.save("YOUR_DIRECTORY/PieChart.docx");
    }
}
```

> **Result:** `PieChart.docx` を開くと、適切なサイズの円（またはドーナツ）グラフが表示され、スライスが爆発し、タイトルと凡例が付いています。すべて UI に触れずに自動生成されています。

### Expected Output

| Element | What you’ll see |
|---------|-----------------|
| Chart type | 円グラフ（`holeSize` > 0 の場合はドーナツ） |
| Slice explosion | 最初のスライスが 20 pt だけオフセット |
| Legend | 右側に配置 |
| Title | 太字 14 pt の “Quarterly Sales Distribution” |
| Data labels | 各スライスにカテゴリ名と数値が表示 |
| Document | 共有可能な標準的な Word `.docx` ファイル |

## Common Questions & Gotchas

- **Do I need a license?**  
  評価版でもテストは可能ですが、透かしが入ります。クリーンな出力が必要な場合はクラスパスに `aspose.words.lic` を配置してください。

- **Can I use this with Maven?**  
  もちろんです。以下の依存関係を `pom.xml` に追加してください：

  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>22.12</version>
  </dependency>
  ```

- **What if I have more than one series?**  
  `pieChart.getSeries()` をループし、`setExplosion`、`setFillColor` などを系列ごとに適用します。これが **円グラフの書式設定** を多次元データに対応させる方法です。

- **Is the chart editable in Word after generation?**  
  はい。保存後に文書を開けば、色やフォントの手動調整、あるいは円を棒グラフに変換することも可能です。

## Wrap‑Up

Aspose.Words for Java を使って Word 文書に **円グラフを挿入** し、**ドーナツ グラフの生成**、**円グラフの書式設定**、**Word のチャート書式設定** のベストプラクティス、そして **チャートサイズのカスタマイズ** 方法を実演しました。上記の完全な実行可能サンプルを任意の Java プロジェクトに組み込めば、COM 相互運用や Office インストールの負荷なしに即座にチャート自動化が可能です。

次は何をしますか？ データ ソースをライブ データベースに置き換える、しきい値に応じた条件付きカラーを追加する、または同じ文書を PDF にエクスポートして印刷用レポートを作成する、などです。これらのステップは今回の基礎の上にスムーズに構築できます。

質問や改善アイデア（スタック バーや折れ線グラフなど）があれば、下のコメント欄にどうぞ。Happy charting!

## What Should You Learn Next?

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれており、API の追加機能をマスターしたり、独自プロジェクトで代替実装を試したりするのに役立ちます。

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Number Format For Axis In A Chart](/words/english/net/programming-with-charts/number-format-for-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}