---
category: general
date: 2026-10-07
description: Aspose.Words for C# を使用して Word 文書を作成し、円グラフを挿入する方法を学びます。このガイドでは、カスタム チャート
  ラベルを使用して Word ファイルを生成する方法も示しています。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- generate word file
- customize pie chart
- how to add pie chart
language: ja
lastmod: 2026-10-07
og_description: C#でWord文書を作成し、円グラフを挿入します。このステップバイステップガイドに従って、完全にカスタマイズされたチャートラベル付きのWordファイルを生成しましょう。
og_image_alt: Screenshot of a Word document that contains a customized pie chart created
  with C#
og_title: C#でカスタマイズされた円グラフを含むWord文書を作成する
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to create word document and insert pie chart using Aspose.Words
    in C#. The guide also shows how to generate word file with custom chart labels.
  headline: How to create word document with a customized pie chart in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart
title: C#でカスタマイズされた円グラフを含むWord文書の作成方法
url: /ja/net/programming-with-charts/how-to-create-word-document-with-a-customized-pie-chart-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# でカスタマイズした円グラフを含む Word 文書を作成する方法

プログラムで **Word 文書を作成** したい場合、このチュートリアルでは Aspose.Words for .NET を使用して **円グラフを挿入** し、データ ラベルをカスタマイズする方法を示します。また、完全にスタイルが適用されたグラフを含む **Word ファイルを生成** する手順も学べます。プロジェクトのセットアップから最終文書の保存まで、外部ツールは Aspose.Words ライブラリ以外不要で、完全なサンプルコードも提供されているのでそのままコピーして実行できます。

## 前提条件

開始する前に、以下が揃っていることを確認してください。

* .NET 6.0 SDK 以降がインストール済み  
* 有効な Aspose.Words for .NET ライセンス（または無料評価キー）  
* Visual Studio 2022 や Visual Studio Code などの IDE  

プロジェクトに次の NuGet パッケージを追加する必要があります。

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.Drawing.Charts
```

これらのパッケージは、以下のサンプルで使用する `Document`、`DocumentBuilder`、およびチャート関連クラスを提供します。

## Word 文書を作成し、チャートを追加する

最初のステップは **Word 文書を作成** し、コンテンツを挿入できる `DocumentBuilder` を取得することです。ビルダーは文書内のカーソルのように機能します。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` オブジェクトは Word ファイル全体を表し、`DocumentBuilder` は `InsertChart` などのメソッドでオブジェクトを文書フローに直接配置できます。

## 文書に円グラフを挿入する

ビルダーの準備ができたら、特定のサイズで **円グラフを挿入** できます。チャートはビルダーの現在位置に追加されます。

```csharp
        // Step 3: Insert a pie chart with the desired size (400x300 points)
        Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

        // Populate the chart with sample data
        pieChart.Series.Clear();
        ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                                new[] { 25.0, 35.0, 20.0, 20.0 });
```

`InsertChart` は操作可能な `Chart` オブジェクトを返します。サンプル データは四半期ごとの売上を表す 4 つのスライスを作成します。

## 円グラフのデータ ラベルをカスタマイズする

チャートを見やすくするために、**円グラフのラベル** をカスタマイズする必要があります。ラベルをスライスの外側に配置し、リーダー ラインを表示します。ここで `ChartDataLabelCollection` が活躍します。

```csharp
        // Step 4: Get the data label collection of the first series
        ChartDataLabelCollection dataLabels = pieChart.Series[0].DataLabels;

        // Step 5: Position the data labels outside each slice
        dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Step 6: Enable leader lines for clearer label connections
        dataLabels.ShowLeaderLines = true;

        // Optional: Show the actual value and percentage
        dataLabels.ShowValue = true;
        dataLabels.ShowPercentage = true;
```

`Position` を `OutsideEnd` に設定すると、各ラベルがスライスの端の外側に移動し、`ShowLeaderLines` を有効にするとラベルとスライスを結ぶ線が描画されます。オプションのフラグ `ShowValue` と `ShowPercentage` を使用すれば、数値とパーセンテージの両方を表示できます。

**プロのコツ:** ラベルのフォントを変更したい場合は `dataLabels.Font` でサイズ、色、スタイルを設定してください。これにより、チャートが企業のブランディングに合わせて統一されます。

## Word ファイルを保存・生成する

チャートの設定が完了したら、`Document` インスタンスをディスクに保存して **Word ファイルを生成** します。最新の Word バージョンとの互換性を最大限に保つため、`.docx` 形式を選択してください。

```csharp
        // Step 7: Save the document with the customized chart
        string outputPath = @"C:\Temp\CustomPieChart.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

`CustomPieChart.docx` を開くと、4 つのスライスが外側にラベル付けされ、リーダー ラインで接続され、値とパーセンテージの両方が表示された円グラフが確認できます。

![C# で作成したカスタマイズ円グラフを含む Word 文書のスクリーンショット](image-placeholder.png)

*この画像は **Word 文書を作成** チュートリアルの最終結果を示しています。*

## よくあるバリエーションとエッジケース

| シナリオ | コードの適用方法 |
|----------|----------------------|
| **複数系列** | `pieChart.Series` に追加の `ChartSeries` オブジェクトを追加します。各系列は独自の `DataLabels` コレクションを持ち、個別にスタイル設定できます。 |
| **異なるチャートサイズ** | `InsertChart(width, height)` の幅と高さのパラメータを変更します。単位はポイント (1 pt ≈ 1/72 in) です。 |
| **チャートタイトル** | `pieChart.Title.Text = "Quarterly Sales"` のように設定して説明的なタイトルを追加します。 |
| **PDF へのエクスポート** | チャート作成後に `document.Save("Report.pdf", SaveFormat.Pdf);` を呼び出します。 |
| **ライセンスの取り扱い** | ライセンス ファイル (`Aspose.Words.lic`) をアプリケーション フォルダーに配置し、`new License().SetLicense("Aspose.Words.lic");` を文書作成前に実行します。 |

これらのバリエーションにより、**円グラフを追加する方法** をシンプルなレポートから複雑なダッシュボードまで、さまざまな実務シーンで実現できます。

## 結論

Aspose.Words for .NET を使用して **Word 文書を作成**、**円グラフを挿入**、そして **円グラフのラベルをカスタマイズ** する方法が分かりました。完全なサンプルは、文書の初期化、チャートの追加、データ ラベル位置の調整、リーダー ラインの有効化、そして最終的に **Word ファイルを生成** するというクリーンなワークフローを示しています。

異なるチャート種別 (`ChartType.Column`, `ChartType.Line`) を試したり、ブランドに合わせたカスタム カラーパレットを適用したりして、チュートリアルを拡張してみてください。問題が発生した場合は Aspose.Words のドキュメントを参照するか、複数系列や動的データ ソースを使用した「円グラフを追加する方法」などの関連トピックを調べてみましょう。

Happy coding, and feel free to share your results or ask follow‑up questions in the comments!

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには完全な動作コード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、プロジェクトで代替実装アプローチを探求したりするのに役立ちます。

- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insert Area Chart Into A Word Document](/words/english/net/programming-with-charts/insert-area-chart/)
- [Insert Scatter Chart in Word Document](/words/english/net/programming-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}