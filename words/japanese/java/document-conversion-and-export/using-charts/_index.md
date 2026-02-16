---
date: 2026-02-16
description: Aspose.Words for Java でチャートに複数の系列を追加する方法、軸目盛りを変更する方法、カスタム数値書式を適用する方法、そして折れ線グラフと縦棒グラフを使用したチャート付き
  Word 文書の生成方法を学びましょう。
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Javaでチャートに複数の系列を追加する
url: /ja/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でチャートに複数シリーズを追加する

## Aspose.Words for Java のチャート使用の概要

このチュートリアルでは、Aspose.Words for Java を使用して **チャートに複数シリーズを追加する方法**、軸目盛りをカスタマイズして独自の数値書式を適用する重要性、そしてチャートが豊富な Word 文書を生成する手順を学びます。財務データの折れ線グラフや売上数字の縦棒グラフが必要な場合でも、以下の手順に従ってプログラムでチャートの作成、スタイリング、微調整が可能です。

## クイック回答
- **複数シリーズはどうやって追加しますか？** `chart.getSeries().add(...)` を各シリーズごとに呼び出します。  
- **軸目盛りは変更できますか？** はい – 軸オブジェクトの `setMajorTickMark()` と `setMinorTickMark()` を使用します。  
- **データラベルに適用できる書式は？** Excel 互換の任意の数値書式、例: `"$"#,##0.00` や `0.00%`。  
- **サポートされているチャートタイプは？** Line、Column、Area、Bubble、Scatter など多数、`ChartType` で指定可能です。  
- **本番環境でライセンスは必要ですか？** 完全な機能を利用するには有効な Aspose.Words for Java ライセンスが必要です。

## 「チャートに複数シリーズを追加する」とは？
複数シリーズを追加するとは、同一のチャート領域に 1 つ以上のデータセットを挿入し、異なるカテゴリや期間を横並びで比較できるようにすることです。各シリーズは独自の線、棒、またはマーカーとして表示され、読者によりリッチなビジュアルストーリーを提供します。

## なぜ Aspose.Words for Java でチャート付き Word 文書を生成するのか？
- **フルコントロール**：Word を手動で開かずにチャートタイプ、レイアウト、スタイルを完全に制御できます。  
- **プログラムによる生成**：自動レポートパイプラインに組み込みやすいです。  
- **クロスプラットフォーム**：任意の Java 対応環境で動作します。  
- **豊富な API**：軸、データラベル、数値書式のカスタマイズが可能です。

## 前提条件
- Java Development Kit (JDK) 8 以上。  
- プロジェクトに Aspose.Words for Java ライブラリを追加 (Maven/Gradle または JAR)。  
- 本番環境用の有効な Aspose ライセンス（評価版はオプション）。

## 手順ガイド

### 手順 1: 折れ線グラフを作成し **複数シリーズを追加**
以下は折れ線グラフを作成し、デフォルトのシリーズをクリアした後、カスタム データラベル付きの 3 つの異なるシリーズを追加するコアコードです。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Delete default generated series.
chart.getSeries().clear();

// Adding a series with data and data labels.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Or link format code to a source cell.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

> **プロのコツ:** `chart.getSeries().add(...)` を必要な回数だけ呼び出すことで **複数シリーズを追加** できます – 各呼び出しが同一チャート上に新しい線（または棒など）を生成します。

### 手順 2: **縦棒グラフを作成** (create column chart java)
次のスニペットは、カテゴリを横並びで比較するのに便利なシンプルな縦棒グラフの挿入方法を示しています。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Delete default generated series.
chart.getSeries().clear();

// Creating categories and adding data.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

### 手順 3: **軸目盛りを変更** (change axis tick marks)
X 軸と Y 軸の可読性を向上させます。以下のコードは目盛りの変更、順序の反転、カスタム交差点の設定方法を示しています。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Change the X axis to be a category instead of date.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // Measured in display units of the Y axis (hundreds).
xAxis.setReverseOrder(true);
xAxis.setMajorTickMark(AxisTickMark.CROSS);
xAxis.setMinorTickMark(AxisTickMark.OUTSIDE);
xAxis.setTickLabelOffset(200);

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### 手順 4: **カスタム数値書式を適用** (apply custom number format)
Excel がサポートする任意のパターンで軸の数値やデータラベルを書式設定できます。以下は Y 軸を千区切りパターンでフォーマットする簡潔な例です。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

### 手順 5: 最終的な Word 文書を生成 (generate chart word document)
シリーズ、軸、ラベルの設定が完了したら、上記スニペットのように `doc.save(...)` を呼び出すだけです。生成された `.docx` ファイルには、Microsoft Word で開いて編集可能な完全機能のチャートが含まれます。

## 一般的なユースケース
- **財務ダッシュボード** – 売上、費用、利益の複数シリーズを持つ折れ線グラフ。  
- **販売レポート** – 地域別四半期売上を比較する縦棒グラフ。  
- **プロジェクト追跡** – 時間経過に伴う進捗を可視化するエリアまたは散布図。

## 追加のチャートカスタマイズ
基本に加えて、範囲の調整、軸の非表示 (`axis.setHidden(true)`)、色の変更、凡例の追加などが可能です。詳細は Aspose.Words for Java API リファレンスをご参照ください。

## 結論
本ガイドでは、チャートに **複数シリーズを追加** する方法、折れ線グラフと縦棒グラフの作成、 **軸目盛りの変更**、 **カスタム数値書式の適用**、そして最終的に **チャートが豊富な Word 文書を生成** する手順を解説しました。Aspose.Words for Java を使えば、コードファーストでプロフェッショナルなデータ可視化を文書に直接埋め込む強力な手段が手に入ります。

## よくある質問

**Q: チャートに複数シリーズを追加するにはどうすればよいですか？**  
A: 表示したいシリーズごとに `chart.getSeries().add()` を呼び出します。各呼び出しが独自の線、棒、またはマーカー グループとして新しいデータセットを作成します。

**Q: カスタム数値書式でデータラベルをフォーマットするには？**  
A: シリーズの `DataLabels` オブジェクトにアクセスし、`getNumberFormat().setFormatCode("your pattern")` を使用します。`isLinkedToSource(true)` で元セルの書式にリンクさせることも可能です。

**Q: 軸目盛りを変更するには？**  
A: `ChartAxis` の `setMajorTickMark()` と `setMinorTickMark()` を使用します。オプションは `CROSS`, `INSIDE`, `OUTSIDE`, `NONE` などがあります。

**Q: 散布図やエリアチャートなど他のチャートタイプは作成できますか？**  
A: はい – `builder.insertChart(...)` 呼び出し時に目的の `ChartType`（例: `ChartType.SCATTER`, `ChartType.AREA`）を指定します。

**Q: 不要な軸を非表示にするには？**  
A: 非表示にしたい `ChartAxis` に対して `axis.setHidden(true)` を呼び出します。

---

**最終更新日:** 2026-02-16  
**テスト環境:** Aspose.Words for Java 24.11  
**作者:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}