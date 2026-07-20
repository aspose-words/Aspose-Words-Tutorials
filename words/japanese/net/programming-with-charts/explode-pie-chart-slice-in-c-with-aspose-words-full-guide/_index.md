---
category: general
date: 2026-07-19
description: Aspose.Words for C# を使用して円グラフのスライスを分離します。円スライスの分離方法、ドーナツ穴のサイズ調整、チャートのデータポイントの変更をすばやく学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- explode pie chart slice
- how to explode pie slice
- adjust doughnut hole size
- change chart data points
language: ja
lastmod: 2026-07-19
og_description: Aspose.Words for C# を使用して円グラフのスライスを分離します。このガイドでは、円グラフのスライスを分離する方法、ドーナツチャートの穴のサイズを調整する方法、そしてチャートのデータポイントを効率的に変更する方法を示します。
og_image_alt: Screenshot showing an exploded pie chart slice created with Aspose.Words
  in C#
og_title: C#で円グラフのスライスを分離する – Aspose.Wordsチュートリアル
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  headline: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  type: TechArticle
- description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  name: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  steps:
  - name: Install and Reference Aspose.Words
    text: 'First things first, add the Aspose.Words package to your project. In the
      Package Manager Console:'
  - name: Load the Word Document Containing the Chart
    text: We need a `Document` object that points at the `.docx` with the chart you
      want to modify.
  - name: Retrieve the First Chart Node
    text: Most examples assume a single chart, so we’ll grab the first one. If you
      have multiple charts, adjust the index accordingly.
  - name: Explode the First Slice of a Pie Chart
    text: Now the star of the show—**how to explode pie slice**. We’ll set the `Exploded`
      property of the first data point.
  - name: Adjust Doughnut Hole Size (If It’s a Doughnut Chart)
    text: If your chart happens to be a doughnut, you might want to **adjust doughnut
      hole size**. The hole size is a percentage of the chart’s radius.
  - name: Change Chart Data Points (Optional)
    text: Sometimes you need to **change chart data points**—maybe you’ve updated
      the underlying numbers and want the visual to reflect that.
  - name: Save the Modified Document
    text: Finally, write the changes back to disk. You can overwrite the original
      or create a new file—up to you.
  - name: What’s Next?
    text: '- **Style the exploded slice** (change fill color, border, or add a data
      label). Search for “Aspose.Words chart formatting”. - **Automate batch processing**
      of multiple documents—loop through a folder, explode slices, and save new versions.
      - **Combine with Aspose.Slides** if you need the same chart'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: C# と Aspose.Words で円グラフのスライスを分離する完全ガイド
url: /ja/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# と Aspose.Words で円グラフのスライスを分離する – 完全ガイド

C# を使って Word 文書内の **explode pie chart slice** を実現する方法を考えたことはありませんか？ あなただけではありません。営業資料を作成する場合でも、アンケート結果を可視化する場合でも、スライスを分離すると目を引く場所に注意を集められます。このチュートリアルでは、ドキュメントの読み込み、チャートの取得、最初のスライスの分離、ドーナツの穴の調整、さらにはチャートのデータポイントの変更まで、全工程を順に解説します。

また、**how to explode pie slice**、**adjust doughnut hole size**、**change chart data points** といった二次的な概念も紹介します。余計な説明は省き、すぐにコピペできる完全なソリューションをご提供します。

## 必要なもの

- **Aspose.Words for .NET**（2026‑07‑19 時点の最新バージョン）。NuGet から `Install-Package Aspose.Words` で取得できます。
- **.NET 6+** プロジェクト（レガシー環境の場合は .NET Framework 4.7.2+）。
- すでに円グラフまたはドーナツグラフが含まれている Word ファイル（`Chart.docx`）。まだない場合は、Word で簡単にチャートを作成して保存してください。

以上です—余分なライブラリや COM インターロップは不要で、純粋なマネージドコードだけです。

## Explode Pie Chart Slice – 手順別実装

以下ではタスクを小さなステップに分割します。各セクションには明確な見出し、コードスニペット、そして *なぜ* それを行うのかという簡潔な説明が含まれます。

### 手順 1: Aspose.Words のインストールと参照設定

まずは Aspose.Words パッケージをプロジェクトに追加します。Package Manager Console で以下を実行してください。

```powershell
Install-Package Aspose.Words
```

> **プロのコツ:** Visual Studio の組み込み NuGet UI を使用している場合は “Aspose.Words” を検索し、[Install] をクリックしてください。これにより最新のバグ修正が適用され、チャート操作機能がすぐに利用可能になります。

### 手順 2: チャートが含まれる Word 文書を読み込む

変更したいチャートが含まれる `.docx` を指す `Document` オブジェクトが必要です。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document
Document doc = new Document(@"C:\Charts\Chart.docx");

// Verify that the document actually contains a chart
if (doc.GetChildNodes(NodeType.Chart, true).Count == 0)
{
    throw new InvalidOperationException("No chart found in the specified document.");
}
```

> **なぜ重要か:** `Document` は Aspose.Words のすべての操作のエントリーポイントです。事前にチャートの有無を確認することで、スライスを分離しようとした際の null 参照エラーを防げます。

### 手順 3: 最初の Chart ノードを取得する

多くの例は単一のチャートを前提としているため、最初のものを取得します。複数のチャートがある場合はインデックスを調整してください。

```csharp
// Grab the first chart in the document (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

> **注:** チャートが存在することを確認した後の `Chart` へのキャストは安全です。このオブジェクトを通じてシリーズやデータポイント、チャート種別固有の設定にアクセスできます。

### 手順 4: 円グラフの最初のスライスを分離する

ここが本題—**how to explode pie slice**。最初のデータポイントの `Exploded` プロパティを設定します。

```csharp
// Ensure the chart is a Pie (or Pie3D) before exploding
if (chart.ChartType == ChartType.Pie || chart.ChartType == ChartType.Pie3D)
{
    // Explode the first slice (index 0)
    chart.PieChartData.Series[0].DataPoints[0].Exploded = true;
}
else
{
    Console.WriteLine("The chart is not a pie chart; skipping explode operation.");
}
```

> **なぜ機能するか:** `Exploded` は Word に対し、そのスライスを中心から離すよう指示し、典型的な「分離された円グラフ」効果を作り出します。このプロパティはブール型で、`true` に設定すれば完了です。

### 手順 5: ドーナツチャートの場合は穴のサイズを調整する

チャートがドーナツの場合は、**adjust doughnut hole size** したくなるでしょう。穴のサイズはチャート半径に対するパーセンテージで指定します。

```csharp
// Check for Doughnut chart type and modify the hole size
if (chart.ChartType == ChartType.Doughnut)
{
    // Set the hole size to 30% (range: 0–100)
    chart.DoughnutChartData.HoleSize = 30;
}
```

> **数値の意味:** `30` を指定すると、内側の円が全半径の 30 % を占め、外側のリングがより太くなります。

### 手順 6: チャートのデータポイントを変更する（オプション）

場合によっては **change chart data points** が必要になることがあります—基になる数値が更新され、ビジュアルに反映させたいときです。

```csharp
// Example: Update the second data point's value to 75
if (chart.PieChartData?.Series?.Count > 0 && chart.PieChartData.Series[0].DataPoints.Count > 1)
{
    chart.PieChartData.Series[0].DataPoints[1].Value = 75;
}
```

> **なぜ行うか:** データポイントの値を変更すると、スライスの割合が自動的に再計算され、Word で手動編集することなくチャートが正確に保たれます。

### 手順 7: 変更したドキュメントを保存する

最後に、変更をディスクに書き戻します。元のファイルを上書きしても、新しいファイルを作成しても構いません。

```csharp
// Save the document with the exploded slice and adjusted doughnut hole
doc.Save(@"C:\Charts\FormattedChart.docx");

// Quick confirmation
Console.WriteLine("Document saved successfully with exploded pie chart slice.");
```

> **ヒント:** 明示的に指定したい場合は `SaveFormat.Docx` を使用しますが、`Save(string)` はファイル拡張子から自動的に形式を判別します。

## 期待される結果

Microsoft Word で `FormattedChart.docx` を開くと、以下が確認できるはずです。

- 円グラフの最初のスライスが外側へ **exploded** しています。
- チャートがドーナツの場合、中心の穴が半径の **30 %** を占めています。
- 変更したデータポイントは設定した新しい値を反映しています。

以下は、分離されたスライスのイメージ例です（イラストのみ）。

![Aspose.Words を使用して C# で作成した分離された円グラフのスライス](exploded-pie-slice.png)

*Alt text:* **exploded pie chart slice** は、Word 文書内で分離されたセグメントを示しています。

## よくある質問とエッジケース

**チャートが円グラフやドーナツでない場合は？**  
コードは `ChartType` を確認してから `Exploded` や `HoleSize` を適用します。棒グラフ、折れ線グラフ、エリアチャートなどではこれらのプロパティは存在しないため、ロジックは安全にスキップします。

**複数のスライスを分離できますか？**  
もちろん可能です。`chart.PieChartData.Series[0].DataPoints` をループし、任意のインデックスで `Exploded = true` を設定してください。

**ロケール固有の数値形式を気にする必要がありますか？**  
Aspose.Words は数値を double として保存するため、ロケールに依存せず、コンマとピリオドの違いによる問題は発生しません。

**ヘッダーやフッターに埋め込まれたチャートはどうですか？**  
`doc.GetChildNodes(NodeType.Chart, true)` を使用してすべてのチャートを取得し、各ノードの `ParentNode` を調べて配置場所を確認します。同じ分離ロジックが適用できます。

## 結論

これで、Aspose.Words を使用して C# で **explode pie chart slice** を実現するための、すぐにコピペできる確実なソリューションが手に入りました。ドキュメントの読み込み、チャートの取得、スライスの分離、**adjust doughnut hole size**、**change chart data points**、そしてファイルの保存まで、全工程を網羅しました。

ぜひ色々試してみてください。別のスライスを分離したり、穴のサイズを 45 % に調整したり、複数のデータポイントを同時に更新したりできます。Aspose.Words API はこれらの調整を簡単に行えるようにし、Word ファイルを開いた瞬間に変更が反映されます。

### 次にやることは？

- **分離されたスライスのスタイル設定**（塗りつぶし色、枠線の変更、データラベルの追加など）。“Aspose.Words chart formatting” を検索してください。
- 複数文書の **バッチ処理を自動化**—フォルダーをループし、スライスを分離して新しいバージョンとして保存します。
- PowerPoint デッキでも同じチャートが必要な場合は **Aspose.Slides と組み合わせ** てください。

チャート操作に関する質問や、他のチャートタイプについてさらに深掘りしたい場合は、下にコメントを残してください。コーディングを楽しんで！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を応用した、密接に関連するトピックを取り上げています。各リソースには、完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装方法を検討するのに役立ちます。

- [Aspose.Words for .NET を使用して Word に縦棒グラフを挿入する](/words/english/net/working-with-charts/insert-column-chart/)
- [Aspose.Words for .NET を使用して Word にシンプルな縦棒グラフを挿入する](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Aspose.Words for .NET で Word 文書にエリアチャートを挿入する](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}