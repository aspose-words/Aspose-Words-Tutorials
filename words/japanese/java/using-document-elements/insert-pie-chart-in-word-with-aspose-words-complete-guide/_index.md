---
category: general
date: 2026-07-26
description: Aspose.Words を使用して Word 文書に円グラフを挿入します。数ステップでグラフの追加、スライスの分割、パーセンテージの表示方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to add chart
- how to explode slice
- add chart to word
- how to show percentages
language: ja
lastmod: 2026-07-26
og_description: Aspose.Words を使用して Word ファイルに円グラフを挿入します。このガイドに従って、グラフの追加、スライスの分割、パーセンテージの表示をすばやく学びましょう。
og_image_alt: Screenshot illustrating insert pie chart in a Word document
og_title: Wordに円グラフを挿入 – ステップバイステップ Aspose.Words チュートリアル
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert pie chart into a Word document using Aspose.Words. Learn how
    to add chart, explode slice, and show percentages in just a few steps.
  headline: Insert Pie Chart in Word with Aspose.Words – Complete Guide
  type: TechArticle
- questions:
  - answer: Just add additional `ChartSeries` objects to `chart.Series`. Each series
      can have its own data set, colors, and explode settings.
    question: What if I need more than one series?
  - answer: Yes. Each `ChartPoint` has a `Format.Fill.ForeColor` property you can
      set to any `System.Drawing.Color`.
    question: Can I change the chart’s colors?
  - answer: The `ChartType` enum includes bar, line, doughnut, and many more. Swap
      `ChartType.Pie` for whichever visual you need.
    question: What about different chart types?
  - answer: Absolutely. Word treats the chart as a native Office chart, so users can
      double‑click it to open the built‑in chart editor.
    question: Is the chart editable in Word after insertion?
  type: FAQPage
tags:
- Aspose.Words
- Chart Automation
- .NET Development
title: Aspose.WordsでWordに円グラフを挿入する完全ガイド
url: /ja/java/using-document-elements/insert-pie-chart-in-word-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words を使用した Word への円グラフ挿入 – 完全ガイド

Word レポートに **円グラフを挿入** したいと思ったことはありませんか？ 方法が分からずに戸惑うことも多いでしょう。多くのビジネスアプリでは、円グラフの視覚的インパクトがデータを瞬時に分かりやすくし、Aspose.Words を使えば数行のコードでそれが実現できます。

このチュートリアルでは、**Word にチャートを追加** する正確な手順、強調のためにスライスを「爆発」させる方法、データラベルにパーセンテージを表示する方法を順に解説します。最後まで読むと、任意の .NET プロジェクトに組み込める実行可能なサンプルが手に入ります。

---

## 前提条件

- .NET 6.0 以降（コードは .NET Core と .NET Framework の両方で動作します）
- Aspose.Words for .NET の NuGet パッケージをインストール済み  
  ```bash
  dotnet add package Aspose.Words
  ```
- C# の基本的な構文理解—特別な知識は不要です
- お好みの IDE（Visual Studio、Rider、または VS Code）

以上です。さあ、手を動かしてみましょう。

---

## Word 文書への円グラフ挿入

最初に必要なのは新しい `Document` オブジェクトと `DocumentBuilder` です。Builder は Word のキャンバス上に直接書き込むペンのようなものと考えてください。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
using Aspose.Words.Charts;

// Step 1: Create a new document and a builder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **重要な理由:** `Document` は .docx ファイル全体を表し、`DocumentBuilder` はチャート、テーブル、テキストなどの要素を挿入する便利な API を提供します。これはすべての **how to add chart** 操作の基礎となります。

---

## Word にチャートを追加する方法

Builder が用意できたので、実際に **円グラフを挿入** できます。`insertChart` メソッドはチャートの種類とポイント単位のサイズ（1 ポイント = 1/72 インチ）を受け取ります。

```csharp
// Step 2: Insert a pie chart of size 400x300 points
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

> **ヒント:** 別のサイズが必要な場合は、幅と高さの値を調整するだけです。チャートはページ余白に合わせて自動的にスケーリングされます。

---

## 強調のためにスライスを爆発させる方法

一般的な視覚的調整として、スライスを「爆発」させて円から飛び出させます。これにより、読者の目が最も重要なセグメントに向けられます。

```csharp
// Step 3: Access the first series (the data set)
ChartSeries series = chart.Series[0];

// Step 4: Explode the first slice to emphasize it
series.Points[0].Exploded = true;
```

> **なぜスライスを爆発させるのか？** 特定のカテゴリ（例：財務レポートの「第1四半期売上」）を強調したいとき、スライスを爆発させるだけで余計なテキストなしにすぐ目立たせることができます。

---

## データラベルにパーセンテージを表示する方法

ほとんどの円グラフは、各スライスにパーセンテージが表示されている方が見栄えが良くなります。Aspose.Words では、1 つのプロパティでこれを有効にできます。

```csharp
// Step 5: Show percentages on the data labels of the first series
series.DataLabelFormat.ShowPercentage = true;
```

> **簡単な注意点:** `ShowPercentage` フラグはシリーズ内のすべてのポイントに適用されるため、スライスごとに設定する必要はありません。

---

## チャートを含む文書を保存する

最後に、文書をディスクに書き込みます。好きなフォルダーを選んでください。ただし、パスが存在していることを確認してください。

```csharp
// Step 6: Save the document containing the chart
doc.Save(@"C:\Temp\PieChart.docx");
```

`PieChart.docx` を Microsoft Word で開くと、最初のスライスが爆発し、パーセンテージが表示された完璧に描画された円グラフが確認できます—洗練されたビジネスレポートで期待される通りです。

---

## 完全な動作例

以下は、コピー＆ペーストでそのまま使用できる完全なプログラムです。コンソールアプリとして実行し、出力ファイルを確認してください。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a pie chart (400x300 points)
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data
            ChartSeries series = chart.Series[0];
            series.Name = "Sales Q1";
            series.Add(30); // Product A
            series.Add(45); // Product B
            series.Add(25); // Product C

            // Explode the first slice (Product A)
            series.Points[0].Exploded = true;

            // Show percentages on data labels
            series.DataLabelFormat.ShowPercentage = true;

            // Save the document
            string outputPath = @"C:\Temp\PieChart.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**期待結果:** 生成された `PieChart.docx` を開きます。タイトルが「Sales Q1」の 3 スライスの円グラフが表示され、最初のスライスが外側に引き出され、各スライスに「30 %」「45 %」「25 %」とラベル付けされています。ビジュアルは入力したデータと一致しています。

---

## よくある質問とエッジケース

- **シリーズが複数必要な場合は？**  
  追加の `ChartSeries` オブジェクトを `chart.Series` に追加するだけです。各シリーズは独自のデータセット、色、爆発設定を持てます。

- **チャートの色を変更できますか？**  
  はい。各 `ChartPoint` には `Format.Fill.ForeColor` プロパティがあり、任意の `System.Drawing.Color` に設定できます。

- **別のチャートタイプは？**  
  `ChartType` 列挙体には棒グラフ、折れ線、ドーナツなど多数が含まれます。必要なビジュアルに合わせて `ChartType.Pie` を置き換えてください。

- **挿入後に Word でチャートを編集できますか？**  
  もちろんです。Word はチャートをネイティブな Office チャートとして扱うため、ユーザーはダブルクリックで組み込みのチャートエディタを開くことができます。

---

## 結論

これで、Aspose.Words を使用して Word 文書に **円グラフを挿入** する方法、**Word にチャートを追加** する方法、**スライスを爆発させる** 方法、そしてデータラベルに **パーセンテージを表示** する方法が正確に分かりました。上記の完全な例はすぐに実行でき、カスタムデータやスタイリング、追加のシリーズなどで拡張可能です。

次のステップに進みませんか？ 円グラフをドーナツチャートに置き換えてみたり、異なるデータセットでレポートを自動生成したりしてみてください。他の可視化に興味がある場合は、棒グラフや折れ線グラフ向けの **how to add chart** ガイドをチェックするか、**add chart to word** API リファレンスでさらに詳しいカスタマイズ方法を探ってみてください。

コーディングを楽しんで、あなたの文書が完璧に切り分けられた円のように常に明瞭でありますように！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Aspose.Words for .NET を使用した Word への列グラフ挿入](/words/english/net/working-with-charts/insert-column-chart/)
- [Aspose.Words for .NET を使用した Word 文書へのエリアチャート挿入 | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Aspose.Words for .NET を使用した Word の散布図作成](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}