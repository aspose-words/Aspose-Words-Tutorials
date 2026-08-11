---
category: general
date: 2026-08-10
description: Aspose.Words を使用して円グラフの Word ドキュメントを作成します。チャートの挿入方法、円グラフの色のカスタマイズ、C#
  で円のスライスの色を変更する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- customize pie chart colors
- how to style pie
- how to insert chart
- change pie slice color
language: ja
lastmod: 2026-08-10
og_description: Aspose.Words を使用して円グラフの Word 文書を作成します。このガイドでは、チャートの挿入方法、円グラフの色のカスタマイズ、C#
  アプリケーションで円のスライスの色を変更する方法を説明します。
og_image_alt: Screenshot of a Word document containing a styled pie chart generated
  by Aspose.Words
og_title: 円グラフを作成するWord文書 – Aspose.Words ガイド
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create pie chart Word document using Aspose.Words. Learn how to insert
    chart, customize pie chart colors, and change pie slice color in C#.
  headline: Create pie chart Word document with Aspose.Words
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, .NET
      6, and later. Just reference the same NuGet package.
    question: Does this work with .NET Core?
  - answer: Replace `ChartType.Pie` with `ChartType.Doughnut`. The same styling APIs
      (`Explosion`, `ForeColor`) apply.
    question: What if I need a donut chart instead of a pie?
  - answer: Open the existing file with `new Document("Existing.docx")`, create a
      `DocumentBuilder` for that document, and call `InsertChart` at the desired cursor
      position.
    question: Can I insert the chart into an existing document?
  - answer: 'Pie charts are best for a limited number of categories (typically < 10).
      For many categories, consider a bar or column chart instead. ## Full source
      code recap Below is the complete program in one block for easy copy‑paste: ```csharp
      using System; using System.Drawing; using Aspose.Words; using Aspo'
    question: How do I handle large datasets?
  type: FAQPage
tags:
- Aspose.Words
- C#
- pie chart
title: Aspose.Words を使用して円グラフの Word 文書を作成する
url: /ja/net/programming-with-charts/create-pie-chart-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words で円グラフの Word 文書を作成する

プログラムで **円グラフの Word 文書を作成** したい場合は、このチュートリアルが手順をすべて示します。チャートの挿入、**円グラフの色のカスタマイズ**、そして **円のスライスの色変更** を Aspose.Words for .NET を使って解説します。

完全に実行可能なサンプルが掲載されているので、Visual Studio にコピーして実行し、生成された *.docx* をすぐに開いてスタイルが適用された円グラフを確認できます。外部ドキュメントは不要です――必要な情報はすべてこのガイドに含まれています。

## 前提条件

開始する前に、以下が揃っていることを確認してください。

* .NET 6.0 SDK 以降がインストール済み  
* 有効な Aspose.Words for .NET ライセンス（または一時評価キー）  
* Visual Studio 2022（または任意の C# IDE）  

コードは `Aspose.Words` と `Aspose.Words.Drawing.Charts` 名前空間のみを使用するため、Aspose.Words ライブラリ以外の NuGet パッケージは不要です。

## 円グラフの Word 文書を作成 – 完全サンプル

以下の C# プログラムは新しい Word 文書を作成し、円グラフを挿入して最初の 2 つのスライスにスタイルを適用し、ファイルを保存します。各ステップについて詳しく説明します。

```csharp
using System;
using System.Drawing;                // For Color
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Initialize a blank document and a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a pie chart of size 400x300 points.
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            // Step 3: Populate the chart with sample data (optional but makes the chart visible).
            // Aspose.Words creates an empty series by default; we add a series with three values.
            chart.Series.Clear(); // Remove the default empty series.
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30); // Slice 1
            series.DataPoints.Add(45); // Slice 2
            series.DataPoints.Add(25); // Slice 3

            // Step 4: Explode the first slice to emphasize it.
            series.Points[0].Explosion = 20; // 20% explosion makes the slice pop out.

            // Step 5: **Customize pie chart colors** – set the first two slices.
            series.Points[0].Format.Fill.ForeColor = Color.Orange; // Slice 1 color
            series.Points[1].Format.Fill.ForeColor = Color.Green;  // Slice 2 color

            // Step 6: **Change pie slice color** for any additional slices if needed.
            // Example: set the third slice to a custom blue.
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            // Step 7: Save the document containing the styled pie chart.
            string outputPath = @"PieChartStyled.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### 各ステップの説明

| 手順 | 内容 | 意味 |
|------|------|------|
| **1** | 新しい `Document` と `DocumentBuilder` を作成します。 | `DocumentBuilder` はチャートなどのコンテンツを Word ファイルに挿入するための流暢なメソッドを提供します。 |
| **2** | `ChartType.Pie` と固定サイズで `InsertChart` を呼び出します。 | `InsertChart` は **チャートを挿入する方法** で、幅・高さを指定することでページ上にきれいに収まります。 |
| **3** | 3 つのカテゴリと数値を持つデータ系列を追加します。 | データがない円グラフは表示されません。データを設定することでスタイリング手順を示せます。 |
| **4** | 最初のポイントに `Explosion` を設定します。 | スライスを飛び出させることで特定のセグメントに注目させられ、重要データのハイライトに便利です。 |
| **5** | 最初の 2 つのポイントに `ForeColor` を設定します。 | これが **円グラフの色をカスタマイズ** する核心部分で、任意の `System.Drawing.Color` を使用できます。 |
| **6** | 追加のスライスに対して **円のスライスの色変更** 方法を示します。 | スタイルは最初の 2 スライスに限定されず、各スライスを個別に色付けできることを実演しています。 |
| **7** | 文書を `PieChartStyled.docx` として保存します。 | 最終出力は Microsoft Word、Google Docs、または互換ビューアで開くことができます。 |

#### 期待される出力

`PieChartStyled.docx` を開くと、1 ページに 400 × 300 pt の円グラフが表示されます。

* スライス 1（オレンジ）は外側に飛び出しています。  
* スライス 2（緑）は飛び出したスライスの隣に配置されています。  
* スライス 3（スチールブルー）が残りの領域を埋めます。

チャートはデータ値（30, 45, 25）と、ここで定義したカスタムカラーを反映しています。

## 円グラフのスタイル設定 – 追加ヒント

* **テーマカラーを使用** – `Color.Orange` をハードコーディングする代わりに、文書テーマから色を取得できます:  
  ```csharp
  chart.Series[0].Points[0].Format.Fill.ForeColor = doc.Theme.ColorScheme.Accent1;
  ```
* **データ ラベルを追加** – パーセンテージを表示したい場合:  
  ```csharp
  chart.HasDataLabel = true;
  chart.DataLabel.NumberFormat = "#%";
  ```
* **動的にサイズ変更** – ページ余白に基づいてチャートサイズを計算します:  
  ```csharp
  double width = doc.PageSetup.PageWidth - doc.PageSetup.LeftMargin - doc.PageSetup.RightMargin;
  double height = width * 0.75; // 4:3 aspect ratio
  builder.InsertChart(ChartType.Pie, width, height);
  ```

これらのバリエーションは、基本例を超えて **円グラフのスタイル設定方法** の柔軟性を示しています。

## よくある質問

**Q: .NET Core でも動作しますか？**  
A: はい。Aspose.Words for .NET は .NET Core、.NET 5、.NET 6 以降と互換性があります。同じ NuGet パッケージを参照してください。

**Q: 円グラフではなくドーナツ グラフが必要な場合は？**  
A: `ChartType.Pie` を `ChartType.Doughnut` に置き換えます。`Explosion`、`ForeColor` などの同じスタイリング API が適用されます。

**Q: 既存の文書にチャートを挿入できますか？**  
A: `new Document("Existing.docx")` で既存ファイルを開き、その文書用に `DocumentBuilder` を作成し、目的のカーソル位置で `InsertChart` を呼び出します。

**Q: 大量データを扱う場合は？**  
A: 円グラフはカテゴリ数が限られた（通常 < 10）場合に適しています。カテゴリが多い場合は棒グラフや縦棒グラフの使用を検討してください。

## 完全なソースコードまとめ

以下に、コピー＆ペーストしやすいように 1 つのブロックにまとめた完全プログラムを示します。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            chart.Series.Clear();
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30);
            series.DataPoints.Add(45);
            series.DataPoints.Add(25);

            series.Points[0].Explosion = 20;
            series.Points[0].Format.Fill.ForeColor = Color.Orange;
            series.Points[1].Format.Fill.ForeColor = Color.Green;
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            doc.Save("PieChartStyled.docx");
            Console.WriteLine("Document saved as PieChartStyled.docx");
        }
    }
}
```

このコードを実行すると、前述のスタイルが適用された円グラフの Word 文書が生成されます。

## 結論

これで Aspose.Words を使用して **円グラフの Word 文書を作成** し、**円グラフの色をカスタマイズ**、さらに **円のスライスの色を変更** する方法が分かりました。ガイドでは、チャートの挿入、データの設定、スライスの飛び出し、カスタムカラーの適用、そして結果の保存までをカバーしました。

ここからは、**円グラフ以外のチャートの挿入方法**、凡例の追加、複数ページにわたるレポートの作成など、関連トピックを探求できます。さまざまな配色やデータセットで実験し、レポート作成のニーズに合わせてカスタマイズしてください。

Happy coding!

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれているので、API の追加機能を習得したり、独自プロジェクトで代替実装を試したりするのに役立ちます。

- [Wordで列チャートを挿入する Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Word文書にエリアチャートを挿入する Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Wordで散布図チャートを作成する Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}