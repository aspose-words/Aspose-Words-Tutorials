---
date: 2025-12-13
description: Aspose.Words for Java を使用して、縦棒グラフの作成方法とグラフのデータ ラベルの書式設定方法を学びます。複数の系列の追加、軸タイプの変更、軸の非表示についても探ります。
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java を使用して柱状グラフを作成する方法
url: /ja/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java を使用して縦棒グラフを作成する方法

このチュートリアルでは、Aspose.Words for Java を使用して Word 文書内に **縦棒グラフ** を直接作成します。さまざまなグラフタイプの作成、複数シリーズの追加、グラフデータラベルの書式設定、軸タイプの変更、さらにはクリーンな外観が必要なときに軸を非表示にする方法まで順を追って解説します。最後まで読めば、ドキュメントにリッチなグラフを埋め込むための堅牢で本番環境向けのアプローチが身につきます。

## クイック回答
- **チャートを作成するための主要クラスは何ですか？** `DocumentBuilder` と `insertChart`。
- **新しいシリーズを追加するメソッドはどれですか？** `chart.getSeries().add(...)`。
- **チャートのデータラベルをフォーマットするには？** `getDataLabels().get(...).getNumberFormat().setFormatCode(...)` を使用します。
- **軸を非表示にできますか？** はい、軸オブジェクトで `setHidden(true)` を呼び出します。
- **Aspose.Words のライセンスは必要ですか？** 本番環境で使用するにはライセンスが必要です。無料トライアルも利用可能です。

## 縦棒グラフとは何か、なぜ使用するのか

縦棒グラフはカテゴリデータを垂直の棒で表現し、グループ間の値比較（地域別売上、月次費用など）に最適です。Java アプリケーションで Aspose.Words を使用して縦棒グラフを生成すれば、Excel や外部ツールを使わずに Word / DOCX ファイルに直接ビジュアルを埋め込むことができます。

## 縦棒グラフの作成方法

以下はシンプルな縦棒グラフを作成する基本例です。コードは元のスニペットと同一で、理解しやすいように説明コメントを追加しています。

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

### 複数シリーズの追加

`chart.getSeries().add(...)` を繰り返し呼び出すことで **複数シリーズ** を縦棒グラフに追加できます。各シリーズは独自のカテゴリと値のセットを持ち、複数のデータセットを横並びで比較できます。

## カスタムデータラベル付き折れ線グラフの作成方法

縦棒グラフの代わりに折れ線グラフが必要な場合も、同様の手順で作成できます。この例では **異なる数値形式でデータラベルをフォーマット** する方法も示しています。

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

### データラベルの追加

`series1.hasDataLabels(true)` はシリーズに **データラベルを追加** し、`setShowValue(true)` によって実際の数値をグラフ上に表示します。

## 軸タイプの変更と軸プロパティのカスタマイズ方法

軸タイプ（例：日付軸からカテゴリ軸への変更）を変更すると、データポイントのプロット方法を制御できます。このスニペットでは、ミニマリストデザインを好む場合に **軸を非表示** にする方法も示しています。

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

// Example of hiding the Y axis.
yAxis.setHidden(true);

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### 軸タイプの変更

`xAxis.setCategoryType(AxisCategoryType.CATEGORY)` は **軸タイプ** を日付ベースからカテゴリベースに変更し、ラベル配置を自由にコントロールできるようにします。

## チャートデータラベルのフォーマット（数値形式）

数値書式は軸やデータラベルに直接適用できます。この例では Y 軸の数値に千位区切りを付けています。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## 追加のチャートカスタマイズ

基本に加えて、表示範囲の調整、ラベル間の間隔設定、特定軸の非表示など、さまざまなカスタマイズが可能です。詳細は Aspose.Words for Java API ドキュメントをご参照ください。

## よくある質問

**Q: チャートに複数のシリーズを追加するにはどうすればよいですか？**  
A: 表示したい各シリーズに対して `chart.getSeries().add()` を使用します。各呼び出しで固有の名前、カテゴリ配列、値配列を指定できます。

**Q: カスタム数値形式でチャートのデータラベルをフォーマットするには？**  
A: シリーズの `DataLabels` オブジェクトにアクセスし、`getNumberFormat().setFormatCode("your format")` を呼び出します。`isLinkedToSource(true)` を使用して元セルの書式にリンクさせることも可能です。

**Q: チャートの軸を非表示にするには？**  
A: 非表示にしたい `ChartAxis`（例：`chart.getAxisY()`）で `setHidden(true)` を呼び出します。

**Q: 軸タイプを変更する最適な方法は？**  
A: カテゴリ軸には `setCategoryType(AxisCategoryType.CATEGORY)`、日付軸には `AxisCategoryType.DATE` を使用します。

**Q: シリーズにデータラベルを追加するには？**  
A: `series.hasDataLabels(true)` で有効化し、`series.getDataLabels().setShowValue(true)` で表示設定を行います。

## 結論

Aspose.Words for Java を使用した **縦棒グラフ** の作成方法を網羅しました。基本的なグラフの挿入、複数シリーズの追加、データラベルの書式設定、軸タイプの変更、そしてクリーンな外観のための軸非表示まで、レポートや文書生成パイプラインにこれらのテクニックを組み込むことで、プロフェッショナルでデータ駆動型の Word 文書を提供できます。

---

**Last Updated:** 2025-12-13  
**Tested With:** Aspose.Words for Java 24.12 (latest)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}