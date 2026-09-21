---
category: general
date: 2026-09-21
description: 空白のWord文書を作成し、DocumentBuilderを使用してWordファイルにレーダーチャートを挿入する方法をステップバイステップで学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert radar chart
- insert chart word file
- generate word document chart
- add radial chart word
language: ja
lastmod: 2026-09-21
og_description: Aspose.Words を使用して空白の Word ドキュメントを作成し、レーダーチャートを挿入します。このチュートリアルに従って、Word
  ドキュメントのチャートをすばやく生成しましょう。
og_image_alt: Screenshot showing a blank Word document with a radar chart inserted
og_title: 空白のWord文書を作成し、レーダーチャートを追加する – 完全なC#ガイド
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  headline: How to create a blank Word document and add a radar chart in C#
  type: TechArticle
- description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  name: How to create a blank Word document and add a radar chart in C#
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET (NuGet package `Aspose.Words` version 23.9 or newer). * Basic familiarity
      with C# and Visual Studio or your preferred IDE.'
  - name: Expected output
    text: '* A `RadialChartExample.docx` file on your desktop. * The first page contains
      a radar chart with five data points labeled “Series 1”. * No additional text
      appears because the document started blank.'
  - name: 1. Changing chart size after insertion
    text: 'If the initial dimensions don’t fit your layout, resize the chart like
      this:'
  - name: 2. Inserting the chart into a specific location
    text: You can move the builder’s cursor to a bookmark, table cell, or paragraph
      before calling `InsertChart`.
  - name: 3. Customizing chart appearance
    text: Aspose.Words exposes the full chart object model, allowing you to set titles,
      axis labels, and colors.
  - name: 4. Dealing with missing fonts
    text: 'If the target environment lacks a font used in the chart, Aspose.Words
      substitutes a default font. To guarantee consistency, embed the required fonts:'
  - name: 5. Exporting to other formats
    text: 'The same document can be saved as PDF, HTML, or PNG without extra code
      changes:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart generation
title: C#で空白のWord文書を作成し、レーダーチャートを追加する方法
url: /ja/java/using-document-elements/how-to-create-a-blank-word-document-and-add-a-radar-chart-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#で空白のWord文書を作成し、レーダーチャートを追加する方法

空白のWord文書を **作成** し、レーダー（ラジアル）チャートを埋め込む必要がある場合、このチュートリアルはすぐに実行できるソリューションを提供します。Aspose.Words .NET を使用してファイルを生成し、チャートを挿入し、結果を保存する手順を簡潔に解説します。

空白の文書は自動レポート作成シナリオに最適なキャンバスを提供し、レーダーチャートを追加することで多次元データを Word 内で直接可視化できます。このガイドを終える頃には、手動編集なしで Word 文書にチャートを生成できるようになります。

## 学べること

* C#で **空白のWord文書をプログラム的に作成** する方法。
* `DocumentBuilder` を使用した **レーダーチャートの挿入方法** の正確なコード。
* **チャートをWordファイルに挿入** し、サイズをカスタマイズする方法。
* **Word文書にチャートを生成** して出力を検証する手順。
* **ラジアルチャートをWordに追加** する際のヒントと一般的な落とし穴。

### 前提条件

* .NET 6.0 以降（コードは .NET Framework 4.6+ でも動作します）。
* Aspose.Words for .NET（NuGet パッケージ `Aspose.Words` バージョン 23.9 以上）。
* C# と Visual Studio（またはお好みの IDE）に関する基本的な知識。

## C#で空白のWord文書を作成する

最初のステップは空の `Document` オブジェクトをインスタンス化することです。このオブジェクトは完全に空白の `.docx` ファイルを表します。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Step 1: Create a new blank document
Document doc = new Document();
```

`Document` はファイル構造を作成しますが、まだセクションやページは含まれていません。Aspose.Words はコンテンツの追加を開始したときに自動的にデフォルトセクションを追加するため、次のステップは追加設定なしで機能します。

## Wordファイルにレーダーチャートを挿入する方法

レーダーチャート（ラジアルチャート）は、中心点から放射状に伸びる軸上にデータポイントを配置して可視化します。Aspose.Words はこの目的のために `DocumentBuilder.insertChart` を提供しています。

```csharp
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);

// Step 3: Insert a radar (radial) chart with the desired size (width: 400pt, height: 300pt)
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`InsertChart` は `Chart` オブジェクトを返し、さらに設定可能です。ビルダーはデフォルトで文書の先頭に位置しているため、チャートは空白文書の最初のページに表示されます。

## Wordファイルにチャートを挿入 – データ系列の追加

データがないチャートは表示されません。レーダーチャートに 1 つ以上の系列を追加して意味のあるものにします。

```csharp
// Step 4: Populate the chart with series data
ChartSeries series = radarChart.Series.Add("Series 1");

// Add data points (example values)
series.DataPoints.Add(4);
series.DataPoints.Add(7);
series.DataPoints.Add(3);
series.DataPoints.Add(6);
series.DataPoints.Add(5);
```

必要なだけ系列を追加できます。各系列は固有の名前を持ち、チャートの凡例に表示されます。データポイントは放射軸に対応し、追加した順序が円周上の位置を決定します。

## Word文書にチャートを生成 – ファイルの保存

チャートの構築が完了したら、文書をディスクに永続化します。書き込み権限のある場所を選択してください。

```csharp
// Step 5: Save the document containing the radar chart
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), 
                                 "RadialChartExample.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

生成された `.docx` ファイルを Microsoft Word で開くと、サイズ 400 × 300 ポイントのレーダーチャートがサンプルデータとともに空白ページに表示されます。

### 期待される出力

* デスクトップ上に `RadialChartExample.docx` ファイルが作成されます。
* 1 ページ目に「Series 1」とラベル付けされた 5 つのデータポイントを持つレーダーチャートが含まれます。
* 文書は空白から開始したため、追加のテキストは表示されません。

## ラジアルチャートをWordに追加 – 一般的なエッジケースの対処

### 1. 挿入後にチャートサイズを変更する

初期サイズがレイアウトに合わない場合、次のようにリサイズします。

```csharp
radarChart.Width = 500;   // width in points
radarChart.Height = 350;  // height in points
```

### 2. 特定の位置にチャートを挿入する

`InsertChart` を呼び出す前に、ビルダーのカーソルをブックマーク、テーブルセル、または段落に移動できます。

```csharp
builder.MoveToBookmark("ChartLocation");
Chart chartInTable = builder.InsertChart(ChartType.Radar, 350, 250);
```

### 3. チャートの外観をカスタマイズする

Aspose.Words は完全なチャートオブジェクトモデルを公開しており、タイトル、軸ラベル、色などを設定できます。

```csharp
radarChart.Title.Text = "Sales Performance";
radarChart.Series[0].FillFormat.ForeColor = System.Drawing.Color.Blue;
radarChart.AxisX.Title.Text = "Quarter";
radarChart.AxisY.Title.Text = "Revenue (M)";
```

### 4. フォントが見つからない場合の対処

対象環境にチャートで使用されているフォントが無い場合、Aspose.Words はデフォルトフォントに置き換えます。統一性を保つために必要なフォントを埋め込んでください。

```csharp
doc.FontSettings.SubstitutionSettings.DefaultFontName = "Arial";
```

### 5. 他の形式へのエクスポート

同じ文書を PDF、HTML、PNG などに保存でき、コードの変更は不要です。

```csharp
doc.Save("RadialChartExample.pdf");
```

## 完全な実行可能サンプル

すべてのパーツを組み合わせると、コピー＆ペーストしてすぐに実行できる単一プログラムが完成します。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class RadarChartDemo
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();

        // Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a radar chart (400pt x 300pt)
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

        // Add a data series with sample values
        ChartSeries series = radarChart.Series.Add("Quarterly Sales");
        series.DataPoints.Add(4);
        series.DataPoints.Add(7);
        series.DataPoints.Add(3);
        series.DataPoints.Add(6);
        series.DataPoints.Add(5);

        // Optional: customize appearance
        radarChart.Title.Text = "Quarterly Sales Radar";
        radarChart.AxisX.Title.Text = "Quarter";
        radarChart.AxisY.Title.Text = "Units Sold";

        // Save the document
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialChartExample.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

このプログラムを実行し、生成されたファイルを開くと、配布用に準備されたプロフェッショナルなレーダーチャートが表示されます。

## 結論

これで **空白のWord文書を作成** し、**レーダーチャートを挿入** し、**Word文書にチャートを生成** する方法が分かりました。上記の手順に従えば、**ラジアルチャートをWordに追加** するファイルを任意の自動レポートパイプラインに組み込み、サイズやスタイルをカスタマイズし、追加形式へエクスポートすることも可能です。

**次のステップ**

* 他のチャートタイプ（`ChartType.Column`、`ChartType.Pie` など）を試してレポート作成ツールキットを拡充する。
* `InsertChart` を複数回呼び出して、1 ページに複数のチャートを配置する。
* データベースや CSV ファイルからデータを取得し、系列を動的に設定する。
* 条件付きデータラベルやチャートテンプレートなど、詳細な書式設定オプションについては Aspose.Words のドキュメントを参照する。

コードを自由に試し、サイズを調整したり、サンプルデータを実際のビジネスメトリクスに置き換えてみてください。コーディングを楽しんでください！


## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法に基づく密接に関連したトピックをカバーしています。各リソースには、完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得したり、プロジェクトで代替実装アプローチを探求したりするのに役立ちます。

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}