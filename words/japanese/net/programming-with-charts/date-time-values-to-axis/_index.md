---
"description": "この包括的なステップバイステップ ガイドでは、Aspose.Words for .NET を使用してグラフの軸に日付と時刻の値を追加する方法を学習します。"
"linktitle": "グラフの軸に日付と時刻の値を追加する"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "グラフの軸に日付と時刻の値を追加する"
"url": "/ja/net/programming-with-charts/date-time-values-to-axis/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# グラフの軸に日付と時刻の値を追加する

## 導入

ドキュメントにグラフを作成することは、データを視覚化する強力な手段となります。時系列データを扱う場合、グラフの軸に日付と時刻の値を追加することは、データの明瞭性を保つ上で非常に重要です。このチュートリアルでは、Aspose.Words for .NET を使用して、グラフの軸に日付と時刻の値を追加する手順を詳しく説明します。このステップバイステップガイドは、環境の設定、コードの記述、そしてプロセスの各段階を理解するのに役立ちます。さあ、始めましょう！

## 前提条件

始める前に、次の前提条件が満たされていることを確認してください。

1. Visual Studio または任意の .NET IDE: .NET コードを記述して実行するには開発環境が必要です。
2. Aspose.Words for .NET: Aspose.Words for .NETライブラリがインストールされている必要があります。ダウンロードはこちらから。 [ここ](https://releases。aspose.com/words/net/).
3. C# の基本知識: このチュートリアルでは、C# プログラミングの基本を理解していることを前提としています。
4. 有効なAsposeライセンス：一時ライセンスは以下から取得できます。 [ここ](https://purchase。aspose.com/temporary-license/).

## 名前空間のインポート

まず、プロジェクトに必要な名前空間がインポートされていることを確認してください。この手順は、Aspose.Words のクラスとメソッドにアクセスするために不可欠です。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## ステップ1: ドキュメントディレクトリを設定する

まず、ドキュメントを保存するディレクトリを定義する必要があります。これは、ファイルを整理し、コードが正しく実行されるようにするために重要です。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## ステップ2: 新しいドキュメントとドキュメントビルダーを作成する

次に、 `Document` クラスと `DocumentBuilder` オブジェクト。これらのオブジェクトは、ドキュメントの作成と操作に役立ちます。

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ステップ3: ドキュメントにグラフを挿入する

次に、 `DocumentBuilder` オブジェクト。この例では縦棒グラフを使用していますが、他の種類も選択できます。

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## ステップ4: 既存のシリーズをクリアする

グラフ内の既存の系列をすべてクリアして、白紙の状態から始めるようにしてください。この手順はカスタムデータの場合に必須です。

```csharp
chart.Series.Clear();
```

## ステップ5: 系列に日付と時刻の値を追加する

日付と時刻の値をチャート系列に追加します。この手順では、日付と対応する値の配列を作成します。

```csharp
chart.Series.Add("Aspose Series 1",
    new[]
    {
        new DateTime(2017, 11, 06), new DateTime(2017, 11, 09), new DateTime(2017, 11, 15),
        new DateTime(2017, 11, 21), new DateTime(2017, 11, 25), new DateTime(2017, 11, 29)
    },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2, 5.3 });
```

## ステップ6: X軸を構成する

X軸のスケールと目盛りを設定します。これにより、日付が適切な間隔で正しく表示されます。

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.Scaling.Minimum = new AxisBound(new DateTime(2017, 11, 05).ToOADate());
xAxis.Scaling.Maximum = new AxisBound(new DateTime(2017, 12, 03).ToOADate());
xAxis.MajorUnit = 7;
xAxis.MinorUnit = 1;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
```

## ステップ7: ドキュメントを保存する

最後に、ドキュメントを指定のディレクトリに保存します。これでプロセスは完了です。ドキュメントには、X軸に日付と時刻の値を含むグラフが作成されます。

```csharp
doc.Save(dataDir + "WorkingWithCharts.DateTimeValuesToAxis.docx");
```

## 結論

Aspose.Words for .NET を使えば、ドキュメント内のグラフの軸に日付と時刻の値を追加するのが簡単です。このチュートリアルで説明する手順に従うだけで、時系列データを効果的に視覚化する、明快で情報量の多いグラフを作成できます。レポート、プレゼンテーション、あるいは詳細なデータ表現を必要とするあらゆるドキュメントを作成する場合でも、Aspose.Words は成功に必要なツールを提供します。

## よくある質問

### Aspose.Words for .NET で他の種類のグラフを使用できますか?

はい、Aspose.Words は、折れ線グラフ、棒グラフ、円グラフなど、さまざまな種類のグラフをサポートしています。

### チャートの外観をカスタマイズするにはどうすればよいですか?

グラフのプロパティにアクセスし、スタイルや色などを設定することで、外観をカスタマイズできます。

### チャートに複数のシリーズを追加することは可能ですか?

もちろんです！複数のシリーズをチャートに追加するには、 `Series.Add` 異なるデータを使用してメソッドを複数回実行します。

### チャートデータを動的に更新する必要がある場合はどうすればよいですか?

要件に応じてシリーズと軸のプロパティをプログラムで操作することにより、グラフ データを動的に更新できます。

### Aspose.Words for .NET の詳細なドキュメントはどこで入手できますか?

より詳細なドキュメントは以下をご覧ください [ここ](https://reference。aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}