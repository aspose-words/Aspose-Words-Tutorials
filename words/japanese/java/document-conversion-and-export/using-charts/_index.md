---
title: Aspose.Words for Java でのチャートの使用
linktitle: チャートの使用
second_title: Aspose.Words Java ドキュメント処理 API
description: Aspose.Words for Java でグラフを作成し、カスタマイズする方法を学びます。データの視覚化のためのグラフの種類、書式設定、軸のプロパティを調べます。
weight: 12
url: /ja/java/document-conversion-and-export/using-charts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でのチャートの使用


## Aspose.Words for Java でのチャートの使用の概要

このチュートリアルでは、Aspose.Words for Java を使用してグラフを操作する方法について説明します。さまざまな種類のグラフの作成方法、軸のプロパティのカスタマイズ方法、データ ラベルの書式設定方法などを学習します。さあ、始めましょう!

## 折れ線グラフを作成する

折れ線グラフを作成するには、次のコードを使用します。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

//デフォルトで生成されたシリーズを削除します。
chart.getSeries().clear();

//データとデータ ラベルを含むシリーズを追加します。
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

//または、書式コードをソース セルにリンクします。
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

## その他の種類のグラフを作成する

同様の手法を使用して、縦棒グラフ、面グラフ、バブルグラフ、散布図など、さまざまな種類のグラフを作成できます。以下は、単純な縦棒グラフを挿入する例です。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

//デフォルトで生成されたシリーズを削除します。
chart.getSeries().clear();

//カテゴリを作成し、データを追加します。
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

## 軸プロパティのカスタマイズ

軸の種類の変更、目盛りの設定、ラベルの書式設定など、軸のプロパティをカスタマイズできます。XY 軸のプロパティを定義する例を次に示します。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

//デフォルトのシリーズをクリアしてデータを追加します。

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// X 軸を日付ではなくカテゴリに変更します。
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // 軸の表示単位 (百) で測定されます。
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

## データラベルの書式設定

データ ラベルをさまざまな数値形式でフォーマットできます。次に例を示します。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

//デフォルトのシリーズをクリアしてデータを追加します。

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## 追加のチャートカスタマイズ

境界、ラベル間の間隔単位を調整したり、グラフの軸を非表示にしたりすることで、グラフをさらにカスタマイズできます。これらのオプションの詳細については、提供されているコード スニペットを参照してください。

## 結論

このチュートリアルでは、Aspose.Words for Java を使用してグラフを操作する方法について説明しました。さまざまな種類のグラフの作成方法、軸のプロパティのカスタマイズ方法、データ ラベルの書式設定方法などを学習しました。Aspose.Words for Java には、ドキュメントにデータの視覚的表現を追加して、情報の表示方法を強化するための強力なツールが用意されています。

## よくある質問

### グラフに複数のシリーズを追加するにはどうすればよいですか?

チャートに複数のシリーズを追加するには、`chart.getSeries().add()`方法。シリーズ名、カテゴリ、データ値を必ず指定してください。

### カスタム数値形式でデータ ラベルをフォーマットするにはどうすればよいですか?

データラベルの書式設定は、`DataLabels`シリーズのプロパティと、希望する書式コードの設定`getNumberFormat().setFormatCode()`.

### グラフの軸プロパティをカスタマイズするにはどうすればよいですか?

軸の種類、目盛り、ラベルなどのプロパティをカスタマイズするには、`ChartAxis`次のような特性`setCategoryType()`, `setCrosses()` 、 そして`setMajorTickMark()`.

### 散布図や面グラフなどの他の種類のグラフを作成するにはどうすればいいですか?

適切な値を指定することで、さまざまなチャートタイプを作成できます。`ChartType`チャートを挿入するときに`builder.insertChart(ChartType.TYPE, width, height)`.

### グラフの軸を非表示にするにはどうすればいいですか?

チャートの軸を非表示にするには、`setHidden(true)`軸のプロパティ。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
