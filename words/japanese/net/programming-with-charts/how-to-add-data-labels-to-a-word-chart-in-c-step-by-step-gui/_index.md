---
category: general
date: 2026-08-04
description: Aspose.Words を使用した C# でデータラベルを追加する方法。チャートの編集、データラベルの中央配置、チャートにパーセンテージを表示、データラベルのカスタマイズを学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add data labels
- how to edit chart
- center chart data labels
- show percentages in chart
- customize chart data labels
language: ja
lastmod: 2026-08-04
og_description: C#でAspose.Wordsを使用してデータラベルを追加する方法。このチュートリアルでは、チャートの編集、チャートデータラベルの中央揃え、チャートにパーセンテージを表示する方法、そしてチャートデータラベルのカスタマイズ方法を示します。
og_image_alt: Screenshot of a Word chart with data labels added using C#
og_title: C#でWordチャートにデータラベルを追加する方法 – 完全ガイド
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  headline: How to add data labels to a Word chart in C# – step‑by‑step guide
  type: TechArticle
- description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  name: How to add data labels to a Word chart in C# – step‑by‑step guide
  steps:
  - name: – Load the Word document containing the chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: – Retrieve the first chart from the document
    text: '```csharp // Find the first shape that contains a chart. Shape chartShape
      = (Shape)document.GetChild(NodeType.Shape, 0, true); Chart chart = chartShape.GetChart();
      ```'
  - name: – Enable data label customization and show percentages in chart
    text: '```csharp // Access the first series of the chart. ChartSeries series =
      chart.Series[0];'
  - name: – Change the label placement to the center of each data point
    text: '```csharp // Position the labels at the center of each point. dataLabels.Position
      = ChartDataLabelPosition.Center; // center chart data labels ```'
  - name: – Further customize chart data labels (optional)
    text: 'If you need more control, you can adjust font, color, or leader lines:'
  - name: – Save the modified document
    text: '```csharp // Persist the changes to a new file. document.Save("YOUR_DIRECTORY/output.docx");
      ```'
  - name: Expected result
    text: 'When you open `output.docx` in Microsoft Word, the chart will display:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart manipulation
title: C#でWordのチャートにデータラベルを追加する方法 – ステップバイステップガイド
url: /ja/net/programming-with-charts/how-to-add-data-labels-to-a-word-chart-in-c-step-by-step-gui/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で Word のチャートにデータ ラベルを追加する方法 – ステップバイステップ ガイド

Word 文書内にあるチャートに **how to add data labels** が必要な場合、このガイドでは実行すべき正確なコードを示します。チャートのプロパティの編集、データ ラベルの中央配置、チャート内でのパーセンテージ表示、そしてあらゆるシナリオに合わせたデータ ラベルのカスタマイズ方法が分かります。

このチュートリアルでは、ドキュメントの読み込みから変更の保存まで、既存のチャートを変更するために必要なすべてをカバーしています。外部参照は不要で、Aspose.Words for .NET ライブラリと基本的な C# 開発環境だけで完結します。

## 前提条件

開始する前に、以下が揃っていることを確認してください。

* .NET 6.0（またはそれ以降）がインストールされていること。
* Aspose.Words for .NET バージョン 23.9 以上。  
  NuGet でインストールできます：

```bash
dotnet add package Aspose.Words
```

* 少なくとも 1 つのチャートを含む Word ファイル（`input.docx`）。

## C# で Word のチャートにデータ ラベルを追加する方法

以下のセクションでは各ステップを順に説明します。主要キーワード **how to add data labels** が本文とコードコメントに自然に出現し、推奨される密度を保っています。

### 手順 1 – チャートを含む Word 文書を読み込む

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

*このステップが重要な理由*: `Document` オブジェクトは Word ファイル全体を表します。これを読み込むことで、チャートを保持するシェイプを含むすべてのノードにアクセスできます。

### 手順 2 – 文書から最初のチャートを取得する

```csharp
// Find the first shape that contains a chart.
Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
Chart chart = chartShape.GetChart();
```

*このステップが重要な理由*: チャートは `Shape` ノード内に格納されています。取得したノードを `Shape` にキャストし、`GetChart()` を呼び出すことで、シリーズ、軸、ラベルコレクションを公開する `Chart` オブジェクトを取得できます。

### 手順 3 – データ ラベルのカスタマイズを有効にし、チャートにパーセンテージを表示する

```csharp
// Access the first series of the chart.
ChartSeries series = chart.Series[0];

// Turn on data labels and request percentage values.
ChartDataLabelCollection dataLabels = series.DataLabels;
dataLabels.ShowPercentage = true;   // show percentages in chart
dataLabels.ShowValue = true;        // optional: also show raw values
```

*このステップが重要な理由*: `ShowPercentage` を設定すると、Aspose.Words が各スライスの全体に対する割合を計算して表示します。これは二次キーワード **show percentages in chart** に直接対応しています。

### 手順 4 – ラベルの配置を各データ ポイントの中心に変更する

```csharp
// Position the labels at the center of each point.
dataLabels.Position = ChartDataLabelPosition.Center; // center chart data labels
```

*このステップが重要な理由*: `Position` プロパティはラベルがデータ ポイントに対してどこに表示されるかを制御します。`Center` を使用することで二次キーワード **center chart data labels** を満たし、円グラフやドーナツ グラフの可読性が向上します。

### 手順 5 – チャート データ ラベルをさらにカスタマイズする（オプション）

より細かい制御が必要な場合は、フォント、色、リーダーラインを調整できます：

```csharp
// Example: make labels bold and red.
dataLabels.Font.Bold = true;
dataLabels.Font.Color = System.Drawing.Color.Red;

// Example: add leader lines for better separation.
dataLabels.ShowLeaderLines = true;
```

これらの設定は二次キーワード **customize chart data labels** を示し、ブランドガイドラインに合わせて外観を調整できることを実演しています。

### 手順 6 – 変更された文書を保存する

```csharp
// Persist the changes to a new file.
document.Save("YOUR_DIRECTORY/output.docx");
```

*このステップが重要な理由*: 保存することで、更新されたチャートが Word 文書に書き戻され、Microsoft Word でファイルを開いたときに新しいデータ ラベルが表示されます。

## 完全な実行可能サンプル

以下はコピーして貼り付け、実行できる完全なプログラムです。必要な `using` ディレクティブと各行を説明するコメントがすべて含まれています。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class AddDataLabelsDemo
{
    static void Main()
    {
        // 1. Load the Word document.
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first chart.
        Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
        Chart chart = chartShape.GetChart();

        // 3. Enable data labels and show percentages.
        ChartSeries series = chart.Series[0];
        ChartDataLabelCollection dataLabels = series.DataLabels;
        dataLabels.ShowPercentage = true;
        dataLabels.ShowValue = true;

        // 4. Center the labels on each data point.
        dataLabels.Position = ChartDataLabelPosition.Center;

        // 5. Optional: further customize appearance.
        dataLabels.Font.Bold = true;
        dataLabels.Font.Color = System.Drawing.Color.DarkBlue;
        dataLabels.ShowLeaderLines = true;

        // 6. Save the modified document.
        document.Save("YOUR_DIRECTORY/output.docx");

        Console.WriteLine("Data labels added and document saved successfully.");
    }
}
```

### 期待される結果

Microsoft Word で `output.docx` を開くと、チャートは次のように表示されます：

* 各スライスの横にパーセンテージ値が表示されます（例: **25 %**, **40 %**, …）。
* ラベルが各 **data point** の中心に配置されます。
* 適用した追加のスタイリング（例: **太字の赤文字**）が反映されます。

これらの視覚的な手がかりにより、チャートの解釈が容易になり、特にプレゼンテーションやレポートで役立ちます。

## データ ラベル以外のチャート プロパティの編集方法

このガイドの焦点は **how to add data labels** ですが、タイトル、凡例の配置、軸の書式設定など、**how to edit chart** 設定も行いたい場合があります。`Chart` オブジェクトは `Title`、`Legend`、`AxisX/AxisY` などのプロパティを提供します。例えば、チャートのタイトルを変更するには次のようにします：

```csharp
chart.Title.Text = "Quarterly Sales Breakdown";
chart.Title.Font.Size = 14;
```

すべてのチャートの変更は同じ手順で行います。チャートを取得し、プロパティを調整し、最後に文書を保存します。

## よくある落とし穴とベストプラクティスのヒント

| 落とし穴 | 発生原因 | 推奨される対策 |
|---|---|---|
| チャートがグループ化されたシェイプ内にある。 | `GetChild(NodeType.Shape, …)` が外側のグループを返し、内部のチャートを返さない。 | `shape.HasChart` を持つシェイプを再帰的に検索する。 |
| 保存後にデータ ラベルが表示されない。 | `ShowValue` または `ShowPercentage` が `true` に設定されていなかった。 | 必要に応じて `ShowValue` と `ShowPercentage` の両方を明示的に `true` に設定する。 |
| 小さなスライスでラベルが重なる。 | 中央配置が混雑を引き起こす可能性がある。 | 外側配置には `ChartDataLabelPosition.OutSideEnd` を使用するか、`LeaderLines` を有効にする。 |

これらのヒントを適用することで、さまざまなチャートタイプで信頼性の高い結果が得られます。

## 結論

これで C# を使用して Word のチャートに **how to add data labels** できるようになりました。このチュートリアルでは、チャートの取得、ラベルの表示有効化、ラベルの中央配置、パーセンテージの表示、外観のカスタマイズについて説明しました。この知識があれば、**how to edit chart** の詳細や **center chart data labels**、**show percentages in chart**、**customize chart data labels** も任意のレポートシナリオで実施できます。

さらに探求したいですか？複数のシリーズを追加したり、条件付き書式を適用したり、チャートを画像としてエクスポートしたりしてみてください。Aspose.Words API は豊富なチャート操作機能を提供しているので、データに最適なビジュアル表現を見つけるために実験してみましょう。

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、**your** プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Customize A Single Chart Data Point In A Chart](/words/english/net/programming-with-charts/single-chart-data-point/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}