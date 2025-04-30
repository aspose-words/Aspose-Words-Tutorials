---
"description": "Aspose.Words for Javaでグラフを作成およびカスタマイズする方法を学びます。グラフの種類、書式設定、軸のプロパティを活用して、データを視覚化します。"
"linktitle": "チャートの使用"
"second_title": "Aspose.Words Java ドキュメント処理 API"
"title": "Aspose.Words for Java でチャートを使用する"
"url": "/ja/java/document-conversion-and-export/using-charts/"
"weight": 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でチャートを使用する


## Aspose.Words for Java でのチャートの使い方入門

このチュートリアルでは、Aspose.Words for Java を使ってグラフを操作する方法を学びます。さまざまな種類のグラフの作成方法、軸プロパティのカスタマイズ方法、データラベルの書式設定方法などを学びます。さあ、始めましょう！

## 折れ線グラフを作成する

折れ線グラフを作成するには、次のコードを使用します。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// デフォルトで生成されたシリーズを削除します。
chart.getSeries().clear();

// データとデータ ラベルを含むシリーズを追加します。
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// または、書式コードをソース セルにリンクします。
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

## 他の種類のグラフを作成する

同様のテクニックを使って、縦棒グラフ、面グラフ、バブルグラフ、散布図など、さまざまな種類のグラフを作成できます。以下は、シンプルな縦棒グラフを挿入する例です。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// デフォルトで生成されたシリーズを削除します。
chart.getSeries().clear();

// カテゴリを作成し、データを追加します。
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

## 軸プロパティのカスタマイズ

軸の種類の変更、目盛りの設定、ラベルの書式設定など、軸のプロパティをカスタマイズできます。以下はXY軸のプロパティを定義する例です。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// デフォルトのシリーズをクリアしてデータを追加します。

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// X 軸を日付ではなくカテゴリに変更します。
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // Y 軸の表示単位 (百) で測定されます。
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

データラベルはさまざまな数値書式で書式設定できます。例を以下に示します。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// デフォルトのシリーズをクリアしてデータを追加します。

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## 追加のチャートカスタマイズ

境界線、ラベル間の間隔、グラフ軸の非表示などを調整することで、グラフをさらにカスタマイズできます。これらのオプションの詳細については、提供されているコードスニペットをご覧ください。

## 結論

このチュートリアルでは、Aspose.Words for Java を使ってグラフを操作する方法を解説しました。さまざまな種類のグラフの作成方法、軸プロパティのカスタマイズ方法、データラベルの書式設定方法などを学習しました。Aspose.Words for Java は、ドキュメントにデータの視覚的な表現を追加し、情報の提示方法を向上させる強力なツールを提供します。

## よくある質問

### グラフに複数のシリーズを追加するにはどうすればよいですか?

複数の系列をチャートに追加するには、 `chart.getSeries().add()` 方法。系列名、カテゴリ、データ値を必ず指定してください。

### カスタム数値形式でデータ ラベルをフォーマットするにはどうすればよいですか?

データラベルの書式設定は、 `DataLabels` シリーズのプロパティと、希望する書式コードの設定 `getNumberFormat()。setFormatCode()`.

### グラフの軸プロパティをカスタマイズするにはどうすればよいですか?

軸の種類、目盛り、ラベルなどの軸プロパティをカスタマイズするには、 `ChartAxis` 次のような特性 `setCategoryType()`、 `setCrosses()`、 そして `setMajorTickMark()`。

### 散布図や面グラフなどの他の種類のグラフを作成するにはどうすればよいですか?

適切な値を指定することで、さまざまなチャートタイプを作成できます。 `ChartType` チャートを挿入するときに `builder。insertChart(ChartType.TYPE, width, height)`.

### グラフの軸を非表示にするにはどうすればいいですか?

チャートの軸を非表示にするには、 `setHidden(true)` 軸のプロパティ。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}