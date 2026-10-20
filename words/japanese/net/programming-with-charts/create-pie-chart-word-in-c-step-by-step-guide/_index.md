---
category: general
date: 2026-08-07
description: C#で円グラフをすばやく作成する。円グラフの挿入方法、データラベルの追加、パーセンテージ表示、チャートデータラベルのカスタマイズを学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- show percentage chart
- add data labels pie
- insert pie chart
- customize chart data labels
language: ja
lastmod: 2026-08-07
og_description: Aspose.Words を使用して C# で円グラフを作成します。このチュートリアルでは、円グラフの挿入方法、データラベルの追加方法、パーセンテージ表示の方法を、チャートのデータラベルをカスタマイズしながら解説します。
og_image_alt: Word document displaying a pie chart with percentage labels outside
  each slice
og_title: C#で円グラフを作成する – 完全チュートリアル
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  headline: Create pie chart word in C# – step‑by‑step guide
  type: TechArticle
- description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  name: Create pie chart word in C# – step‑by‑step guide
  steps:
  - name: Call `chart.Series.Add()` for each additional series.
    text: Call `chart.Series.Add()` for each additional series.
  - name: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
    text: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
  - name: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
    text: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
  type: HowTo
tags:
- pie chart
- C#
- Aspose.Words
- chart customization
title: C#で円グラフを作成する – ステップバイステップガイド
url: /ja/net/programming-with-charts/create-pie-chart-word-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で円グラフ Word を作成 – ステップバイステップ ガイド

C# で **create pie chart word** ドキュメントを作成する必要がある場合、このガイドは完全な実行可能ソリューションを提供します。**insert pie chart**、**add data labels pie**、**show percentage chart** を行い、**customize chart data labels** で洗練された外観にする方法が分かります。

プログラムでチャートを生成すれば、手動での編集が不要になり、特にレポートやダッシュボードを自動的に作成する必要がある場合に便利です。以下のセクションでは、Aspose.Words for .NET を使用して、完全にラベル付けされた円グラフを Word ファイルに埋め込むために必要なすべてを学びます。

## 前提条件とセットアップ

開始する前に、以下がインストールされていることを確認してください。

* .NET 6.0 SDK 以降  
* 有効な Aspose.Words for .NET ライセンス（または一時的な評価キー）  
* Visual Studio 2022（または C# をサポートする任意の IDE）  

プロジェクトに Aspose.Words NuGet パッケージを追加します:

```bash
dotnet add package Aspose.Words
```

> **プロのコツ:** 多数のチャートを生成する場合は、パフォーマンス向上のために **Free‑Form Drawing** モード (`DocumentBuilder.UseFreeFormDrawing = true`) を有効にしてください。

## Aspose.Words で円グラフ Word を作成

最初の重要なステップは、空の Word ドキュメントと `DocumentBuilder` を作成することです。このオブジェクトが以降のすべての挿入操作を司ります。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new blank document and a DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*なぜ重要か*: `Document` は `.docx` ファイル全体を表し、`DocumentBuilder` は段落、テーブル、チャートを追加するための流暢な API を提供します。クリーンなドキュメントから始めることで、隠れた書式設定がチャートのレイアウトに干渉するのを防げます。

## ドキュメントに円グラフを挿入

次に、目的のサイズの円グラフを配置します。`InsertChart` メソッドは `Chart` オブジェクトを返し、さらに設定できます。

```csharp
// Step 2: Insert a pie chart of the desired size
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

*なぜ重要か*: `ChartType.Pie` フラグにより Aspose.Words は円形のチャートを生成します。幅 (`400`) と高さ (`300`) はポイント単位で指定され、視覚的な占有領域を正確にコントロールできます。

## データでチャートを埋める

円グラフには少なくとも 1 つの数値系列が必要です。ここでは「Apples」「Bananas」「Cherries」の 3 つのカテゴリを追加します。

```csharp
// Populate the first series with sample data
chart.Series[0].AddCategory("Apples", 40);
chart.Series[0].AddCategory("Bananas", 35);
chart.Series[0].AddCategory("Cherries", 25);
```

*なぜ重要か*: 各 `AddCategory` 呼び出しがスライスを作成します。数値はスライスの大きさを決定し、ラベルはデータ ラベルを有効にしたときに表示されるカテゴリ名になります。

## データ ラベルの追加とパーセンテージ表示

チャートを情報豊かにするため、データ ラベルを有効にし、スライスの外側に配置し、カテゴリ名とパーセンテージの両方を表示させます。

```csharp
// Step 3: Access the first series' data label collection
ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;

// Step 4: Position labels outside the slices and show useful information
labels.Position = ChartDataLabelPosition.OutsideEnd; // places label outside each slice
labels.ShowCategoryName = true;                     // displays "Apples", "Bananas", …
labels.ShowPercentage = true;                       // displays "40%" etc.
```

*なぜ重要か*: `Position` を `OutsideEnd` に設定すると、特にスライスが小さい場合の可読性が向上します。`ShowCategoryName` と `ShowPercentage` を有効にすることで **show percentage chart** の要件を満たし、**add data labels pie** の目的も達成します。

## チャート データ ラベルのさらにカスタマイズ（オプション）

フォントを変更したり、リーダーラインを追加したり、凡例を非表示にしたりしたい場合があります。以下のスニペットは一般的なカスタマイズ例です。

```csharp
// Optional: customize label font and leader lines
labels.Font.Size = 10;
labels.Font.Color = System.Drawing.Color.DarkBlue;
labels.ShowLeaderLines = true;

// Optional: hide the default legend because labels already contain the needed info
chart.HasLegend = false;
```

*なぜ重要か*: ラベルの外観をカスタマイズすることで、チャートがドキュメントのスタイルガイドに合致します。データ ラベルですでに情報が提供されている場合、凡例を削除すると視覚的な雑音が減ります。

## カスタマイズされたチャートでドキュメントを保存

最後に、ドキュメントをディスクに書き出します。書き込み権限のあるパスを選択してください。

```csharp
// Step 5: Save the document with the customized chart
doc.Save("YOUR_DIRECTORY/ChartWithCustomLabels.docx");
```

`ChartWithCustomLabels.docx` を Microsoft Word で開くと、各スライスがカテゴリ名とパーセンテージでラベル付けされ、スライスの外側に配置され、カスタムフォント設定が適用された円グラフが表示されます。

### 期待される出力

| スライス   | 値   | パーセンテージ | Word に表示されるラベル |
|-----------|------|----------------|--------------------------|
| Apples    | 40   | 40 %           | Apples – 40 %            |
| Bananas   | 35   | 35 %           | Bananas – 35 %           |
| Cherries  | 25   | 25 %           | Cherries – 25 %          |

チャートは以下のイラストに似た外観になります:

![各スライスの外側にパーセンテージ ラベルが表示された円グラフを含む Word ドキュメント](pie-chart-word.png "円グラフ Word 作成例")

*画像の alt テキストには SEO 用の主要キーワードが含まれています。*

## 複数シリーズとエッジケースの処理

基本例は単一シリーズを使用していますが、円グラフでも複数シリーズ（例: 2 年間の比較）を表示したい場合は、次の手順が必要です。

1. 追加のシリーズごとに `chart.Series.Add()` を呼び出す。  
2. 各シリーズが同じカテゴリを使用していることを確認する。異なる場合、Aspose.Words は `ArgumentException` をスローします。  
3. 必要に応じて `labels.ShowSeriesName = true` を設定し、スライスを区別できるようにする。

```csharp
// Adding a second series (e.g., sales in 2025)
chart.Series.Add("2025");
chart.Series[1].AddCategory("Apples", 45);
chart.Series[1].AddCategory("Bananas", 30);
chart.Series[1].AddCategory("Cherries", 25);
```

複数シリーズが存在すると、チャートは自動的に **clustered pie**（「pie of pies」）として描画されます。ラベルが読みやすいことを出力で確認してください。

## よくある落とし穴と回避方法

| 問題                         | 原因                                 | 対策 |
|------------------------------|--------------------------------------|------|
| ラベルがスライスと重なる     | チャート領域が小さい、カテゴリが多すぎる | `InsertChart(width, height)` でサイズを拡大、または `Position` を `InsideEnd` に変更 |
| パーセンテージの合計が 100 % にならない | データの丸め誤差                     | `labels.ShowPercentage = true` を使用（Aspose.Words が自動正規化） |
| Word でチャートが空白になる   | ライセンスが無い、または評価期限切れ   | ドキュメント作成前に有効な Aspose.Words ライセンスをロード |
| フォント色が Word のテーマと異なる | コード内でカスタムフォントを設定している | カスタムフォント設定を削除するか、Word のテーマ色 (`System.Drawing.Color.Black`) に合わせる |

## 完全なソースコード（実行可能）

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load license (optional for evaluation)
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a pie chart
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 3. Add data to the first series
        chart.Series[0].AddCategory("Apples", 40);
        chart.Series[0].AddCategory("Bananas", 35);
        chart.Series[0].AddCategory("Cherries", 25);

        // 4. Configure data labels
        ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;
        labels.Position = ChartDataLabelPosition.OutsideEnd;
        labels.ShowCategoryName = true;
        labels.ShowPercentage = true;

        // Optional: further customization
        labels.Font.Size = 10;
        labels.Font.Color = Color.DarkBlue;
        labels.ShowLeaderLines = true;
        chart.HasLegend = false;

        // 5. Save the document
        doc.Save("ChartWithCustomLabels.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

プログラムを実行すると `ChartWithCustomLabels.docx` が生成され、**create pie chart word** の要件をすべて満たす例が含まれます。

## 結論

これで、Aspose.Words を使用して C# で **create pie chart word** ドキュメントを作成する方法が分かりました。本ガイドでは円グラフの挿入、**add data labels pie**、**show percentage chart**、そして **customize chart data labels** を通じて、プロフェッショナルでデータ駆動型の Word ファイルを実現する手順をカバーしました。

ここからは、既存の段落に **insert pie chart** を埋め込む、**bar** や **line** チャートを生成する、またはデータセットが異なるレポートをバッチで自動作成するなど、関連トピックを探求できます。ラベル位置、フォントスタイル、複数シリーズ構成を試して、特定のレポート要件に合わせた出力を作りましょう。

Happy charting!

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示したテクニックを基にした密接に関連するトピックを扱っています。各リソースには、ステップバイステップの説明と完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを探るのに役立ちます。

- [チャート データ ラベルのカスタマイズ](/words/english/net/programming-with-charts/chart-data-label/)
- [チャート内データ ラベルのデフォルト オプション設定](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Word 文書に列グラフを挿入](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}