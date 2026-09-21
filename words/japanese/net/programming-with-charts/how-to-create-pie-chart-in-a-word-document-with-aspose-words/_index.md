---
category: general
date: 2026-09-21
description: Aspose.Words を使用して円グラフを作成し、Word に挿入する方法、円グラフにデータ ラベルを追加し、円グラフにパーセンテージを表示する方法を、数ステップで学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- insert chart into word
- add data labels to pie chart
- show percentages on pie chart
- how to display percentages in chart
language: ja
lastmod: 2026-09-21
og_description: Aspose.Words を使用して Word に円グラフを作成し、チャートを Word に挿入し、円グラフにデータ ラベルを追加し、円グラフにパーセンテージを表示します—すべて明確なコード例とともに。
og_image_alt: Screenshot of a Word document containing a pie chart with percentage
  data labels displayed outside each slice
og_title: Aspose.WordsでWordに円グラフを作成する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
- description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  name: How to create pie chart in a Word document with Aspose.Words
  steps:
  - name: Expected output
    text: 'When you open the generated document, you should see:'
  - name: Adding a title to the chart
    text: '```csharp chart.Title.Text = "Sales Distribution Q1"; chart.Title.Show
      = true; ```'
  - name: Changing slice colors
    text: '```csharp series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
      series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen; ```'
  - name: Handling an empty series
    text: 'If your data source might be empty, guard against `IndexOutOfRangeException`:'
  - name: Exporting to PDF instead of Word
    text: '```csharp doc.Save("PieChart.pdf", SaveFormat.Pdf); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- charting
- Word automation
title: Aspose.Words を使用して Word 文書に円グラフを作成する方法
url: /ja/net/programming-with-charts/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words で Word 文書に円グラフを作成する方法

プログラムで **円グラフを作成** したい場合、Aspose.Words を使えばシンプルに実現できます。このチュートリアルでは、**Word にチャートを挿入** し、シリーズを設定し、**円グラフにデータ ラベルを追加** し、最後に **円グラフにパーセンテージを表示** させる手順を解説します。最後まで実行すれば、任意の .NET プロジェクトに組み込める完全なサンプルが手に入ります。

本ガイドでは、必要な NuGet パッケージ、完全な C# ソース、各 API 呼び出しの意味、チャートのカスタマイズ方法まで網羅しています。外部ドキュメントは不要です—コピーして実行し、必要に応じて調整してください。

## 前提条件

開始する前に以下を確認してください。

* .NET 6.0 SDK 以降がインストールされていること。  
* Visual Studio 2022（または .NET に対応した任意の IDE）。  
* Aspose.Words for .NET のライセンス（無料トライアルでもテストは可能）。  
* C# と Word 文書構造の基本的な知識。

上記が揃っていれば、すぐにコードへ進めます。

## 手順 1: プロジェクトの作成と Aspose.Words のインポート

新しいコンソール プロジェクトを作成し、Aspose.Words の NuGet パッケージを追加します。

```bash
dotnet new console -n PieChartDemo
cd PieChartDemo
dotnet add package Aspose.Words
```

このパッケージには `Aspose.Words.Drawing.Charts` 名前空間が含まれ、`Chart` や `ChartSeries` クラスを利用できます。

> **プロのコツ:** ライセンス ファイル (`Aspose.Words.lic`) をプロジェクトのルートに配置し、起動時に読み込むことで評価版の透かしを回避できます。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: Apply your license
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");
```

## 手順 2: 空のドキュメントと DocumentBuilder の作成

`Document` は Word ファイルを表し、`DocumentBuilder` はコンテンツ挿入用のフルエント API を提供します。

```csharp
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder will let us add a chart
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**ポイント:** `DocumentBuilder` は現在の挿入位置を保持するため、チャートが文書の意図した場所に正確に配置されます。

## 手順 3: Word 文書に円グラフを挿入

ここで **Word にチャートを挿入** します。`InsertChart` メソッドはチャートの種類、幅、高さ（ポイント単位）を受け取ります。

```csharp
        // Insert a pie chart of size 400x300 points
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

この時点では、デフォルトのデータ系列がプレースホルダー値 (25, 25, 25, 25) で設定されています。必要に応じて後で置き換えられます。

## 手順 4: 最初の系列にアクセスし、データ ラベルをカスタマイズ

円グラフは通常 1 系列だけです。**円グラフにデータ ラベルを追加** するため、系列を取得しパーセンテージ表示を有効にします。

```csharp
        // Access the first (and only) series of the chart
        ChartSeries series = chart.Series[0];

        // Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // Position the labels outside the slices for readability
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

**`ShowPercentage` を設定する理由:** このフラグにより Aspose.Words が各スライスの割合を計算し、パーセンテージとして描画します。`Position` プロパティでラベルがスライスと重ならないように配置でき、特にスライスが小さい場合の可読性が向上します。

## 手順 5: (任意) プレースホルダー データの置き換え

特定の数値を使用したい場合は、デフォルトのポイントを置き換えます。

```csharp
        // Clear existing points
        series.Points.Clear();

        // Add custom data points
        series.Points.Add(new ChartPoint(40)); // 40%
        series.Points.Add(new ChartPoint(30)); // 30%
        series.Points.Add(new ChartPoint(20)); // 20%
        series.Points.Add(new ChartPoint(10)); // 10%
```

新しい値に応じてパーセンテージ ラベルは自動的に調整されます。

## 手順 6: ドキュメントの保存

最後にドキュメントをディスクに書き出します。拡張子がフォーマットを決定し、`.docx` は最新の Word ファイルを生成します。

```csharp
        // Save the document containing the pie chart
        doc.Save("PieChart.docx");
    }
}
```

プログラムを実行すると、出力フォルダーに **PieChart.docx** という名前のファイルが作成されます。Microsoft Word で開くと、各スライスにパーセンテージが外側に表示された円グラフが確認できます。

### 期待される出力

生成された文書を開くと、以下が表示されます。

* サイズ 400 × 300 pt の円グラフが 1 つ。  
* 4 つのスライス（追加したポイント数に応じて変化）。  
* 「40 %」「30 %」など、各スライスの外側に表示されたパーセンテージ ラベル。

ラベルがスライス内部に表示されている場合は、`ChartDataLabelPosition.OutsideEnd` が正しく設定されているか再確認してください。

## 手順 7: よくあるバリエーションとエッジケース

### チャートにタイトルを追加

```csharp
chart.Title.Text = "Sales Distribution Q1";
chart.Title.Show = true;
```

### スライスの色を変更

```csharp
series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen;
```

### 空の系列を扱う

データ ソースが空になる可能性がある場合は、`IndexOutOfRangeException` に備えてガードします。

```csharp
if (series.Points.Count == 0)
{
    // Provide a fallback to avoid runtime errors
    series.Points.Add(new ChartPoint(100));
}
```

### Word ではなく PDF にエクスポート

```csharp
doc.Save("PieChart.pdf", SaveFormat.Pdf);
```

チャート描画ロジックは同じで、Aspose.Words が自動的に Word レイアウトを PDF に変換します。

## 完全なソース一覧

以下は実行可能な完全プログラムです。`Program.cs` に貼り付けて `dotnet run` を実行してください。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: apply your license to remove evaluation watermarks
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Create a DocumentBuilder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a pie chart (400x300 points)
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 4. Access the first series
        ChartSeries series = chart.Series[0];

        // 5. Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // 6. Position data labels outside the slices
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Optional: replace placeholder data with custom values
        series.Points.Clear();
        series.Points.Add(new ChartPoint(40));
        series.Points.Add(new ChartPoint(30));
        series.Points.Add(new ChartPoint(20));
        series.Points.Add(new ChartPoint(10));

        // Optional: add a title
        chart.Title.Text = "Quarterly Sales Breakdown";
        chart.Title.Show = true;

        // 7. Save the document
        doc.Save("PieChart.docx"); // Change extension to .pdf for PDF output
    }
}
```

## まとめ

これで Aspose.Words を使って Word ファイルに **円グラフを作成** し、**Word にチャートを挿入**、**円グラフにデータ ラベルを追加**、そして **円グラフにパーセンテージを表示** する方法が分かりました。プロジェクトのセットアップから最終文書の生成までのフル ワークフローを示したサンプルなので、ダッシュボードやレポート、請求書の自動生成などに応用できます。

次は **チャートの凡例にパーセンテージを表示** する方法や、チャート色のカスタマイズ、Word 文書を PDF に変換して配布する手順などを学んでみましょう。同じ `InsertChart` メソッドを使って Bar や Line など他のチャートタイプにも挑戦すれば、Automation の幅がさらに広がります。

Happy charting!

## 次に学ぶべきこと

このガイドで示したテクニックを応用できる、関連チュートリアルを以下にまとめました。各リソースは完全なコード例とステップバイステップの解説が含まれているので、API の追加機能を習得したり、別の実装アプローチを自分のプロジェクトに取り入れたりするのに役立ちます。

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}