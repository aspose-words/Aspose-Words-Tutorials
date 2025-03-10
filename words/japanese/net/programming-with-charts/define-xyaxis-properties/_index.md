---
title: グラフの XY 軸プロパティを定義する
linktitle: グラフの XY 軸プロパティを定義する
second_title: Aspose.Words ドキュメント処理 API
description: このステップバイステップ ガイドでは、Aspose.Words for .NET を使用してグラフの XY 軸プロパティを定義する方法を学習します。.NET 開発者に最適です。
weight: 10
url: /ja/net/programming-with-charts/define-xyaxis-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# グラフの XY 軸プロパティを定義する

## 導入

グラフは、データを視覚化するための強力なツールです。動的なグラフを使用してプロフェッショナルなドキュメントを作成する必要がある場合、Aspose.Words for .NET は非常に役立つライブラリです。この記事では、Aspose.Words for .NET を使用してグラフの XY 軸プロパティを定義するプロセスを、各ステップをわかりやすく簡単に説明しながら説明します。

## 前提条件

コーディングに取り掛かる前に、いくつかの前提条件を満たす必要があります。

1. Aspose.Words for .NET: Aspose.Words for .NETライブラリがあることを確認してください。[ここからダウンロード](https://releases.aspose.com/words/net/).
2. 開発環境: Visual Studio のような統合開発環境 (IDE) が必要です。
3. .NET Framework: 開発環境が .NET 開発用に設定されていることを確認します。
4. C# の基本知識: このガイドでは、C# プログラミングの基本を理解していることを前提としています。

## 名前空間のインポート

まず、プロジェクトに必要な名前空間をインポートする必要があります。これにより、ドキュメントやグラフの作成と操作に必要なすべてのクラスとメソッドにアクセスできるようになります。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

このプロセスを簡単なステップに分解し、各ステップではグラフの XY 軸のプロパティを定義する特定の部分に焦点を当てます。

## ステップ 1: ドキュメントと DocumentBuilder を初期化する

まず、新しいドキュメントを初期化し、`DocumentBuilder`オブジェクト。`DocumentBuilder`ドキュメントにコンテンツを挿入するのに役立ちます。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ステップ2: グラフを挿入する

次に、ドキュメントにグラフを挿入します。この例では、面グラフを使用します。必要に応じてグラフのサイズをカスタマイズできます。

```csharp
//グラフを挿入
Shape shape = builder.InsertChart(ChartType.Area, 432, 252);
Chart chart = shape.Chart;
```

## ステップ3: デフォルトのシリーズをクリアしてカスタムデータを追加する

デフォルトでは、チャートにはいくつかの定義済みシリーズがあります。これらをクリアし、カスタム データ シリーズを追加します。

```csharp
chart.Series.Clear();
chart.Series.Add("Aspose Series 1",
	new DateTime[]
	{
		new DateTime(2002, 01, 01), new DateTime(2002, 06, 01), new DateTime(2002, 07, 01),
		new DateTime(2002, 08, 01), new DateTime(2002, 09, 01)
	},
	new double[] { 640, 320, 280, 120, 150 });
```

## ステップ4: X軸のプロパティを定義する

ここで、X 軸のプロパティを定義します。これには、カテゴリの種類の設定、軸の交差のカスタマイズ、目盛りとラベルの調整が含まれます。

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.CategoryType = AxisCategoryType.Category;
xAxis.Crosses = AxisCrosses.Custom;
xAxis.CrossesAt = 3; // 軸の表示単位 (百) で測定されます。
xAxis.ReverseOrder = true;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
xAxis.TickLabelOffset = 200;
```

## ステップ5: Y軸のプロパティを定義する

同様に、Y 軸のプロパティを設定します。これには、目盛りラベルの位置、主単位と副単位、表示単位、スケーリングの設定が含まれます。

```csharp
ChartAxis yAxis = chart.AxisY;
yAxis.TickLabelPosition = AxisTickLabelPosition.High;
yAxis.MajorUnit = 100;
yAxis.MinorUnit = 50;
yAxis.DisplayUnit.Unit = AxisBuiltInUnit.Hundreds;
yAxis.Scaling.Minimum = new AxisBound(100);
yAxis.Scaling.Maximum = new AxisBound(700);
```

## ステップ6: ドキュメントを保存する

最後に、指定したディレクトリにドキュメントを保存します。これにより、カスタマイズされたチャートを含む Word ドキュメントが生成されます。

```csharp
doc.Save(dataDir + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

## 結論

Aspose.Words for .NET を使用して Word 文書にグラフを作成およびカスタマイズするのは、必要な手順を理解すれば簡単です。このガイドでは、ドキュメントの初期化から最終製品の保存まで、グラフの XY 軸プロパティを定義するプロセスを順を追って説明しました。これらのスキルがあれば、詳細でプロフェッショナルなグラフを作成して、文書の質を高めることができます。

## よくある質問

### Aspose.Words for .NET ではどのような種類のグラフを作成できますか?
面グラフ、棒グラフ、折れ線グラフ、円グラフなど、さまざまな種類のグラフを作成できます。

### Aspose.Words for .NET をインストールするにはどうすればよいですか?
 Aspose.Words for .NETは以下からダウンロードできます。[ここ](https://releases.aspose.com/words/net/)提供されているインストール手順に従ってください。

### グラフの外観をカスタマイズできますか?
はい、Aspose.Words for .NET では、色、フォント、軸のプロパティなど、グラフを広範囲にカスタマイズできます。

### Aspose.Words for .NET の無料試用版はありますか?
はい、無料トライアルをご利用いただけます[ここ](https://releases.aspose.com/).

### その他のチュートリアルやドキュメントはどこで見つかりますか?
詳細なチュートリアルやドキュメントは、[Aspose.Words for .NET ドキュメント ページ](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
