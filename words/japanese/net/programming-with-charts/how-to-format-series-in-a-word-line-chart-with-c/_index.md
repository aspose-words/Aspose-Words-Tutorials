---
category: general
date: 2026-09-21
description: C# を使用して Word の折れ線グラフの系列をフォーマットする方法。Word 文書の作成、折れ線グラフの挿入、カスタム数値形式の適用を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format series
- create word document
- insert line chart
- add chart to word
- apply custom number format
language: ja
lastmod: 2026-09-21
og_description: C# を使用して Word の折れ線グラフの系列をフォーマットする方法。このチュートリアルでは、Word 文書の作成、折れ線グラフの挿入、カスタム数値形式の適用方法を示します。
og_image_alt: Screenshot of a Word document showing a line chart with percentage‑formatted
  Y‑axis values
og_title: C#でWordの折れ線グラフの系列をフォーマットする方法 – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to format series in a Word line chart using C#. Learn to create
    a Word document, insert a line chart, and apply a custom number format.
  headline: How to format series in a Word line chart with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart
- Word automation
title: C#でWordの折れ線グラフの系列をフォーマットする方法
url: /ja/net/programming-with-charts/how-to-format-series-in-a-word-line-chart-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# を使用した Word ラインチャートの系列の書式設定方法

Word ラインチャートで**系列の書式設定**が必要な場合、このガイドは完全な実行可能ソリューションを提供します。**Word ドキュメントの作成**、**ラインチャートの挿入**、そして Y 値への**カスタム数値書式の適用**を Aspose.Words for .NET を使って確認できます。

チャートオブジェクトモデルを理解すれば、Word の自動化はシンプルになります。このチュートリアルの最後までに、データ系列が小数点以下2桁のパーセンテージとして表示されるラインチャートを含む Word ファイルが作成できます。

## 本チュートリアルで達成できること

* プログラムで空の `.docx` ファイルを生成する。  
* サイズ 400 × 300 ポイントのラインチャートを追加する。  
* チャートの最初のデータ系列にアクセスする。  
* 書式コード `#,##0.00%` を適用し、Y 値をパーセンテージで表示させる。  

外部ツールは必要なく、Aspose.Words の NuGet パッケージだけで実行できます。

## 前提条件

* .NET 6.0 SDK 以降。  
* Visual Studio 2022（または任意の C# IDE）。  
* Aspose.Words for .NET 23.10 以上 – `dotnet add package Aspose.Words` でインストール。  

Aspose.Words はプラットフォームに依存しないため、コードは Windows、Linux、macOS で動作します。

## Aspose.Words を使用して Word ドキュメントを作成する

最初のステップは `Document` オブジェクトをインスタンス化することです。このオブジェクトはメモリ上の Word ファイル全体を表します。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document.
        Document doc = new Document();

        // The document currently has no content.
        // We will add a chart in the next step.
```

*重要ポイント*: `Document` はすべての Word 処理操作のエントリーポイントです。これがなければ段落や表、チャートを追加できません。

## ドキュメントにラインチャートを挿入する

`DocumentBuilder` は `Document` にコンテンツを書き込みます。`InsertChart` を呼び出すと、現在のページにチャートシェイプが作成されます。

```csharp
        // Step 2: Initialize a DocumentBuilder to construct the document content.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a line chart with the desired size (400 × 300 points).
        Chart chart = builder.InsertChart(ChartType.Line, 400, 300);
```

*重要ポイント*: `InsertChart` は `Chart` オブジェクトを返し、系列、軸、書式設定をフルコントロールできます。サイズパラメータはポイントで指定されます（1 ポイント = 1/72 インチ）。

## 最初のデータ系列にアクセスする

すべてのチャートは 1 つ以上の `ChartSeries` を持ちます。最初の系列はインデックス 0 です。

```csharp
        // Step 4: Access the first data series of the chart.
        ChartSeries series = chart.Series[0];
```

*重要ポイント*: `ChartSeries` オブジェクトはラインチャートの単一の線の Y 値、X 値、書式設定オプションを保持します。このオブジェクトを変更すると、データの視覚表現が変わります。

## 系列にカスタム数値書式を適用する

`FormatCode` プロパティは数値の表示方法を制御します。`#,##0.00%` を設定すると、Word は値を小数点以下2桁のパーセンテージとして扱います。

```csharp
        // Step 5: Apply a custom number format to the Y‑values.
        // This displays the numbers as percentages with two decimals.
        series.YValues.FormatCode = "#,##0.00%";

        // Optional: Populate the series with sample data.
        series.YValues.Add(0.15);
        series.YValues.Add(0.30);
        series.YValues.Add(0.45);
        series.YValues.Add(0.60);
```

*重要ポイント*: カスタム書式がないと、Word は生の小数（例: `0.15`）を表示します。書式コードはそれらを `15.00%` に変換し、これはビジネスレポートでよく求められる形式です。

## ドキュメントを保存し、結果を確認する

```csharp
        // Save the document to the file system.
        string outputPath = "FormattedSeriesLineChart.docx";
        doc.Save(outputPath);
        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

`FormattedSeriesLineChart.docx` を Microsoft Word で開くと、Y 軸ラベルが `15.00%`、`30.00%`、`45.00%`、`60.00%` と表示されたラインチャートが見えます。チャートのサイズは `InsertChart` で指定した寸法と一致します。

### 期待される出力のスクリーンショット

> *画像: パーセンテージ書式の Y 軸値を持つラインチャートが表示された Word 文書ページ。*  
> *(代替テキスト: パーセンテージ書式の Y 軸値を持つラインチャートが表示された Word 文書のスクリーンショット)*

## 一般的なバリエーションとエッジケース

| 状況 | 調整 |
|-----------|------------|
| **複数系列** | `chart.Series` をループし、各系列に `FormatCode` を設定する。 |
| **異なるチャートタイプ** | `ChartType.Line` を `ChartType.Column`、`ChartType.Pie` などに置き換える。 |
| **ロケール固有の区切り文字** | `CultureInfo` に対応した書式文字列を使用する。例: フランス語ロケールの場合 `"# ##0,00 %"`。 |
| **動的データソース** | 書式を適用する前に、データベースや CSV ファイルから `series.YValues` を設定する。 |

**プロ・チップ:** Y 値を追加した **後** に書式を適用してください。先に書式を変更してから値を追加しても動作しますが、後で適用することで最終データセットに確実に書式が適用されます。

## まとめ

これで C# を使用して Word ラインチャートの **系列の書式設定** 方法が分かりました。このチュートリアルで取り上げた内容は次のとおりです：

* Word ドキュメントの作成 (`create word document`)。  
* ラインチャートの挿入 (`insert line chart`, `add chart to word`)。  
* チャートの最初の系列へのアクセス。  
* パーセンテージ表示のためにカスタム数値書式を適用 (`apply custom number format`)。

## 次のステップ

* `ChartType` の異なる値を試して、他の可視化がどのように動作するか確認する。  
* `chart.Title`、`chart.AxisX.Title`、`chart.AxisY.Title` を使用してタイトル、軸ラベル、凡例を追加する。  
* チャートを画像としてエクスポートする（`chart.Save` と `SaveFormat.Png` を使用）ことで、Web レポートで利用できるようにする。  

このパターンを応用して、ダッシュボードや財務レポート、あるいはプログラムでチャートを生成する必要があるあらゆる文書を作成してください。コーディングを楽しんで！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Aspose.Words for .NET を使用して Word にラインチャートを作成する](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Word 文書に列チャートを挿入する](/words/english/net/programming-with-charts/insert-column-chart/)
- [Word 文書にエリアチャートを挿入する | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}