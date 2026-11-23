---
category: general
date: 2026-11-22
description: Javaで円グラフを作成し、チャートサイズの設定、データラベルの追加、パーセンテージの表示、そして視覚的インパクトを高めるために最初のスライスを回転させる方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- set chart size
- show percentages pie chart
- add data labels pie chart
- rotate pie chart slice
language: ja
lastmod: 2026-11-22
og_description: Javaで円グラフを作成し、チャートサイズを設定し、データラベルにパーセンテージを表示し、最初のスライスを回転させる—すべて単一の実行可能な例で。
og_image_alt: Screenshot of a created pie chart showing custom size, percentage labels,
  and a rotated first slice
og_title: Javaでカスタムサイズ、ラベル、回転を設定した円グラフを作成する
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  headline: Create pie chart with custom size, data labels, and rotation in Java
  type: TechArticle
- description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  name: Create pie chart with custom size, data labels, and rotation in Java
  steps:
  - name: Why each step matters
    text: '| Step | Purpose | How it relates to the keywords | |------|---------|--------------------------------|
      | **Insert chart** | **Create pie chart** – the core object that will render
      the visual. | Directly satisfies the *create pie chart* requirement. | | **Set
      dimensions** | The `addChart(..., 400, 3'
  - name: 1. Insert a pie chart and set chart size
    text: '```java IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50,
      400, 300); ```'
  - name: 2. Populate the chart with data
    text: The demo adds three categories and a single series. Replace the hard‑coded
      numbers with data from a database, CSV, or user input as needed.
  - name: 3. Show percentages on each slice
    text: '```java series.getDataLabelFormat().setShowPercentage(true); ```'
  - name: 4. Add detailed data labels
    text: '```java series.getDataLabelFormat().setShowCategoryName(false); series.getDataLabelFormat().setShowLeaderLines(false);
      ```'
  - name: 5. Rotate the first slice
    text: '```java chart.setFirstSliceAngle(45); ```'
  - name: 6. Save and view the result
    text: 'Running the program produces `output/PieChartDemo.pptx`. Open it in PowerPoint
      or any compatible viewer to see the final pie chart:'
  - name: What’s next?
    text: '* Explore other chart types (Bar, Line, Area) using the same `ChartType`
      enum. * Combine multiple charts on a single slide for dashboards. * Export charts
      to PNG or SVG for use in web applications.'
  type: HowTo
tags:
- Java
- charts
- Aspose.Slides
- data‑visualization
title: Javaでカスタムサイズ、データラベル、回転を設定した円グラフを作成する
url: /ja/java/getting-started/create-pie-chart-with-custom-size-data-labels-and-rotation-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Javaでカスタムサイズ、データラベル、回転を持つ円グラフを作成する

Javaで **create pie chart** が必要な場合、このガイドでは全工程を案内します。**set chart size** の方法、**show percentages pie chart** の有効化、**data labels pie chart** の追加、そして **rotate pie chart slice** により最初のスライスが45度の角度から開始する方法を学びます。

この例では、PowerPointファイルの操作に広く使用されている **Aspose.Slides for Java** を使用しています。同じ概念は他のチャートライブラリにも適用でき、API 呼び出しをツールキットの同等のものに置き換えるだけです。

## 前提条件

* Java 17 以降がインストールされていること  
* 依存関係管理のための Maven 3.8+（または Gradle）  
* Java 構文の基本的な理解  
* Aspose.Slides for Java のバイナリへのアクセス（公式サイトから無料トライアルを取得可能）

`pom.xml` に依存関係を追加します:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-slides</artifactId>
    <version>24.9</version> <!-- latest version as of November 2026 -->
</dependency>
```

## 円グラフの作成 – 完全な例

以下のプログラムは、カスタムサイズ、パーセンテージデータラベル、回転した最初のスライスを持つ円グラフを含む PowerPoint スライドを作成します。

```java
package com.example.piechart;

import com.aspose.slides.*;
import com.aspose.slides.charts.*;

public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a presentation
        Presentation pres = new Presentation();

        // 2️⃣ Add a blank slide
        ISlide slide = pres.getSlides().addEmptySlide(pres.getLayoutSlides().get_Item(0));

        // 3️⃣ Insert a pie chart (create pie chart)
        IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
        // The dimensions above also demonstrate set chart size

        // 4️⃣ Populate the chart with sample data
        IChartDataWorkbook workbook = chart.getChartData().getChartDataWorkbook();

        // Clear the default series & categories
        chart.getChartData().getSeries().clear();
        chart.getChartData().getCategories().clear();

        // Add categories (slices)
        chart.getChartData().getCategories().add(workbook.getCell(0, "A1", "Category A"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A2", "Category B"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A3", "Category C"));

        // Add a series and assign values
        IChartSeries series = chart.getChartData().getSeries().add(
                workbook.getCell(0, "B1", "Series 1"),
                chart.getType());

        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B1", 30));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B2", 45));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B3", 25));

        // 5️⃣ Enable percentage display on data labels (show percentages pie chart)
        series.getDataLabelFormat().setShowPercentage(true);
        series.getDataLabelFormat().setShowCategoryName(false);
        series.getDataLabelFormat().setShowLegendKey(false);
        series.getDataLabelFormat().setShowSeriesName(false);
        series.getDataLabelFormat().setShowValue(false);
        series.getDataLabelFormat().setShowLeaderLines(false);

        // 6️⃣ Rotate the chart so the first slice starts at 45 degrees (rotate pie chart slice)
        chart.setFirstSliceAngle(45);

        // 7️⃣ Save the presentation
        String outPath = "output/PieChartDemo.pptx";
        pres.save(outPath, SaveFormat.Pptx);
        System.out.println("Presentation saved to " + outPath);
    }
}
```

### 各ステップの重要性

| ステップ | 目的 | キーワードとの関係 |
|------|---------|--------------------------------|
| **Insert chart** | **Create pie chart** – ビジュアルを描画するコアオブジェクトです。 | *create pie chart* の要件を直接満たします。 |
| **Set dimensions** | `addChart(..., 400, 300)` 呼び出しは **set chart size** を示しています。 | 幅 (400 px) と高さ (300 px) を制御します。 |
| **Show percentages** | `setShowPercentage(true)` は各スライスで **show percentages pie chart** を表示します。 | ユーザーは生の値ではなくパーセンテージを必要とすることが多いです。 |
| **Add data labels** | `DataLabelFormat` の設定により、望ましい可視性で **data labels pie chart** が追加されます。 | ラベルは可読性を向上させ、カスタマイズ可能です。 |
| **Rotate slice** | `setFirstSliceAngle(45)` により、最初のスライスが45度の角度から開始するようにチャートが回転し、**rotate pie chart slice** を実現します。 | 特定のスライスの視覚的強調が向上します。 |

## ステップバイステップの内訳

### 1. 円グラフを挿入し、チャートサイズを設定する

```java
IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
```

`addChart` メソッドはチャートを作成し、同時に **set chart size** を 400 × 300 ポイントに設定します。  
別のサイズが必要な場合は、最後の2つの引数を調整してください。

### 2. データでチャートを埋める

デモでは3つのカテゴリと1つの系列を追加しています。必要に応じてハードコードされた数値をデータベース、CSV、またはユーザー入力からのデータに置き換えてください。

### 3. 各スライスでパーセンテージを表示する

```java
series.getDataLabelFormat().setShowPercentage(true);
```

`setShowPercentage(true)` を有効にすると、チャートは **show percentages pie chart** を自動的に計算し、各スライスの全体に対する割合を表示します。

### 4. 詳細なデータラベルを追加する

```java
series.getDataLabelFormat().setShowCategoryName(false);
series.getDataLabelFormat().setShowLeaderLines(false);
```

他のラベルオプション（`setShowValue`、`setShowSeriesName` など）を切り替えて、**add data labels pie chart** の体験を調整できます。

### 5. 最初のスライスを回転させる

```java
chart.setFirstSliceAngle(45);
```

`setFirstSliceAngle(45)` を呼び出すことで **rotate pie chart slice** が実行され、最初のセグメントが45度の角度で開始し、目立たせます。

### 6. 結果を保存して表示する

プログラムを実行すると `output/PieChartDemo.pptx` が生成されます。PowerPoint または互換性のあるビューアで開き、最終的な円グラフを確認してください：

![Create pie chart example](images/pie_chart_example.png){.align-center alt="カスタムサイズ、パーセンテージラベル、回転した最初のスライスを持つ作成された円グラフのスクリーンショット"}

上の画像は **create pie chart** の結果を示しており、サイズ、ラベル、パーセンテージ、回転が正しく適用されていることを確認できます。

## よくあるバリエーションとエッジケース

| 状況 | 調整 |
|-----------|------------|
| **異なるチャート寸法** | `addChart` の幅/高さパラメータを変更します。 |
| **複数系列** | 追加の `IChartSeries` オブジェクトを追加します。各系列は独自のラベル設定を持つことができます。 |
| **カスタムラベル形式** | `series.getDataLabelFormat().setNumberFormat("0.0%")` を使用して小数点以下の桁数を制御します。 |
| **別の角度への回転** | `setFirstSliceAngle` に 0‑360 の任意の整数を渡します。 |
| **画像としてエクスポート** | 保存後、ラスタ版として `chart.writeAsSvg(outPath)` または `chart.writeAsPng(outPath)` を呼び出します。 |

> **Pro tip:** ループで多数のチャートを生成する予定がある場合、同じ `Presentation` オブジェクトを再利用し、チャートデータだけを置き換えてください。これによりメモリオーバーヘッドが削減され、処理速度が向上します。

## 結論

これで Java で **create pie chart** を作成し、**set chart size** を設定し、**show percentages pie chart** を有効にし、**add data labels pie chart** を追加し、**rotate pie chart slice** により視覚的な強調を高める方法が分かりました。完全で実行可能な例は、初期化から最終的な PowerPoint ファイルの保存までのすべてのステップを示しています。

### 次は何を学ぶべきか？

* 同じ `ChartType` 列挙型を使用して、他のチャートタイプ（棒グラフ、折れ線グラフ、エリアグラフ）を探索してください。  
* ダッシュボード用に単一スライド上で複数のチャートを組み合わせます。  
* チャートを PNG または SVG にエクスポートしてウェブアプリケーションで使用します。  

色、凡例、アニメーション効果を自由に試してみてください—データ可視化は想像力だけが制限です。チャート作成を楽しんでください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Word に円グラフを挿入する方法 – データラベルパーセンテージの追加](/words/english/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/)
- [Java で円グラフのスライスを分離する方法 – Aspose.Words チャートチュートリアル](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Java で円グラフを挿入 – 分離、回転、ハイライトスライス](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}