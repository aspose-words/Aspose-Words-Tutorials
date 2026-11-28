---
category: general
date: 2026-06-02
description: C# を使用して Word 文書にチャートの凡例を表示します。凡例の追加方法、プリセットのチャートスタイルの適用方法、そして数分で Word
  のチャートのビジュアルをカスタマイズする方法を学びましょう。
draft: false
keywords:
- show chart legend
- how to add legend
- add legend word chart
- apply preset chart style
- apply chart style word
language: ja
og_description: Word文書にチャートの凡例をすぐに表示します。このガイドでは、凡例の追加、プリセットのチャートスタイルの適用、そしてエッジケースの処理方法を順に解説します。
og_title: Wordでチャートの凡例を表示する – 完全C#チュートリアル
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  headline: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  name: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  steps:
  - name: How to add legend to a specific chart (not the first one)?
    text: 'Replace the `0` index in `GetChild(NodeType.Chart, 0, true)` with the zero‑based
      position of your target chart, or loop through all chart nodes:'
  - name: Can I place the legend at the bottom instead of the right?
    text: 'Absolutely. Just change the `LegendPosition` enum:'
  - name: What if the chart already has a legend but I want to hide it?
    text: 'Set `HasLegend` to `false`:'
  - name: Does this work with Word 2010, 2016, and later?
    text: Yes. Aspose.Words abstracts the underlying Word version, so the same code
      works across all modern .docx files.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word chart
- Legend customization
title: C#でWordのチャート凡例を表示する – 完全ステップバイステップガイド
url: /ja/net/programming-with-charts/show-chart-legend-in-word-with-c-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# WordでC#を使用してチャートの凡例を表示する – 完全ステップバイステップガイド

Ever wondered **how to add legend** to a chart that lives inside a Word document? You're not the only one. In many reports, a missing legend makes the data look cryptic, and fixing it shouldn't be a headache.  

Word文書内にあるチャートに**凡例を追加する方法**を考えたことはありませんか？ あなただけではありません。多くのレポートで、凡例が欠けているとデータが分かりにくくなりますが、修正は面倒であるべきではありません。  

In this tutorial we’ll **show chart legend** in a Word file using Aspose.Words for .NET, apply a preset chart style, and make sure the legend appears exactly where you need it. By the end you’ll have a ready‑to‑run sample that you can drop into any C# project.  

このチュートリアルでは、Aspose.Words for .NET を使用して Word ファイル内に**チャートの凡例を表示**し、プリセットのチャートスタイルを適用し、凡例が必要な場所に正確に表示されるようにします。最後まで実行可能なサンプルが得られ、任意の C# プロジェクトに組み込むことができます。  

## 本ガイドでカバーする内容

We'll walk through the entire workflow:

1. Load an existing *.docx* that already contains a chart.  
2. Retrieve the first chart (or any chart you target).  
3. **Apply preset chart style** to give the visual a professional look.  
4. **Show chart legend**, position it on the right, and handle special cases like Waterfall charts.  
5. Save the modified document.

1. 既にチャートが含まれている既存の *.docx* を読み込みます。  
2. 最初のチャート（または対象とする任意のチャート）を取得します。  
3. **プリセットのチャートスタイルを適用**し、視覚的にプロフェッショナルな外観にします。  
4. **チャートの凡例を表示**し、右側に配置し、ウォーターフォールチャートなどの特殊ケースに対応します。  
5. 変更されたドキュメントを保存します。  

No external tools, no manual fiddling with the UI—just pure code. The only prerequisite is a reference to the Aspose.Words NuGet package (version 23.10 or later) and a basic understanding of C#.  

外部ツールは不要で、UIを手動でいじる必要もありません—純粋にコードだけです。必要条件は Aspose.Words NuGet パッケージ（バージョン 23.10 以降）への参照と、C# の基本的な理解だけです。  

## 前提条件

- .NET 6.0 以降（サンプルは .NET Framework 4.7.2 でも動作します）。  
- Aspose.Words for .NET ライブラリがインストール済み（`Install-Package Aspose.Words`）。  
- 既に少なくとも 1 つのチャートが含まれている Word ファイル（`input.docx`）。  
- Visual Studio、Rider、またはお好みの IDE。  

## 手順 1: プロジェクトのセットアップとドキュメントの読み込み

First, create a console app (or integrate the code into an existing project). Add the `using` directives and load the `.docx` file.  

まず、コンソール アプリを作成します（既存プロジェクトにコードを統合しても構いません）。`using` ディレクティブを追加し、`.docx` ファイルを読み込みます。  

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        
        // Continue with the next steps...
```

> **なぜ重要か:** ドキュメントの読み込みは基礎です。`Document` インスタンスがなければ、Aspose.Words が提供するチャートオブジェクトにアクセスできません。  

## 手順 2: 対象チャートの取得

Charts are stored as nodes inside the document tree. The `GetChild` method performs a deep search, letting us fetch the first chart regardless of where it sits (header, body, footer, etc.).  

チャートはドキュメントツリー内のノードとして格納されています。`GetChild` メソッドは深い検索を行い、ヘッダー、本文、フッターなどに関係なく最初のチャートを取得できます。  

```csharp
        // Retrieve the first chart in the document (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }
```

> **ヒント:** 複数のチャートがある場合は、インデックス `0` を `1`、`2` … に変更するか、`doc.GetChildNodes(NodeType.Chart, true)` を使って反復処理してください。  

## 手順 3: プリセットのビジュアルスタイルを適用

A good-looking chart often starts with a style. Aspose.Words ships with dozens of built‑in styles; `ChartStyle.Style12` is a clean, modern option.  

見栄えの良いチャートは、スタイルから始まります。Aspose.Words には数十種類の組み込みスタイルがあり、`ChartStyle.Style12` はシンプルでモダンなオプションです。  

```csharp
        // Apply a preset visual style to the chart
        chart.Style = ChartStyle.Style12;
```

> **動作概要:** `Style` プロパティは UI で確認できる組み込みの Word チャートスタイルに対応しています。プリセットを選択することで、色やフォント、マーカーを手動で設定する手間が省けます。  

## 手順 4: 凡例を有効化し位置を設定

Now for the star of the show—**show chart legend**. We turn the legend on, then dock it to the right side of the chart.  

さあ、本題の**チャート凡例の表示**です。凡例を有効にし、チャートの右側に配置します。  

```csharp
        // Enable the legend and place it on the right side
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;
```

> **なぜ右側か？** 凡例を右側に配置するとデータ領域が広く保たれ、棒グラフや縦棒グラフに特に有効です。  

## 手順 5: ウォーターフォールチャートの処理（特殊ケース）

Waterfall charts behave a bit differently; the legend can be hidden by default. The following guard clause ensures the legend is visible when the chart type is Waterfall.  

ウォーターフォールチャートは少し挙動が異なり、デフォルトで凡例が非表示になることがあります。以下のガード句は、チャートタイプがウォーターフォールの場合に凡例が表示されるようにします。  

```csharp
        // For Waterfall charts, ensure the legend is visible
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }
```

> **エッジケースの注意:** 古いバージョンの Word ではウォーターフォールチャートの `HasLegend` が無視されることがあるため、`Legend.Show` を明示的に設定することで表示が保証されます。  

## 手順 6: 変更されたドキュメントの保存

Finally, write the changes back to disk. You can overwrite the original file or create a new one.  

最後に、変更をディスクに書き戻します。元のファイルを上書きすることも、新しいファイルを作成することも可能です。  

```csharp
        // Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

Running the program will produce `output.docx` with a visible legend on the right, styled with `Style12`. Open the file in Word to verify the result.  

プログラムを実行すると、右側に凡例が表示され、`Style12` が適用された `output.docx` が生成されます。Word でファイルを開き、結果を確認してください。  

## 完全動作例（全手順を統合）

Below is the complete, ready‑to‑run code. Copy‑paste it into `Program.cs` (or any C# file) and adjust the file paths.  

以下は完全な実行可能コードです。`Program.cs`（または任意の C# ファイル）にコピー＆ペーストし、ファイルパスを調整してください。  

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Retrieve the first chart (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // 3️⃣ Apply a preset visual style (show chart legend with a nice look)
        chart.Style = ChartStyle.Style12;

        // 4️⃣ Enable the legend and dock it to the right
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;

        // 5️⃣ Special handling for Waterfall charts
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }

        // 6️⃣ Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

**Expected output:** Opening `output.docx` shows the original chart with a right‑aligned legend, styled with the modern `Style12`. All data series are clearly labeled, making the chart instantly understandable.  

**期待される出力:** `output.docx` を開くと、元のチャートに右揃えの凡例が表示され、モダンな `Style12` が適用されています。すべてのデータ系列にラベルが付いているため、チャートがすぐに理解できます。  

## よくある質問 (FAQ)

### 特定のチャート（最初のものではない）に凡例を追加する方法は？

Replace the `0` index in `GetChild(NodeType.Chart, 0, true)` with the zero‑based position of your target chart, or loop through all chart nodes:  

`GetChild(NodeType.Chart, 0, true)` の `0` インデックスを、対象チャートのゼロベース位置に置き換えるか、すべてのチャートノードをループしてください。  

```csharp
NodeCollection charts = doc.GetChildNodes(NodeType.Chart, true);
foreach (Chart c in charts)
{
    // Apply the same steps to each chart
}
```

### 凡例を右側ではなく下部に配置できますか？

Absolutely. Just change the `LegendPosition` enum:  

もちろんです。`LegendPosition` 列挙体を変更するだけです。  

```csharp
chart.Legend.Position = LegendPosition.Bottom;
```

### 既に凡例があるチャートで、凡例を非表示にしたい場合は？

Set `HasLegend` to `false`:  

`HasLegend` を `false` に設定します。  

```csharp
chart.HasLegend = false;
```

### Word 2010、2016、以降でも動作しますか？

Yes. Aspose.Words abstracts the underlying Word version, so the same code works across all modern .docx files.  

はい。Aspose.Words は基盤となる Word バージョンを抽象化しているため、同じコードがすべての最新 .docx ファイルで動作します。  

## プロのコツと一般的な落とし穴

- **プロのコツ:** スタイル適用後でも、`Chart.Series` コレクションを通じて個々の要素（色、データラベル）を調整できます。スタイルは堅実なベースラインを提供します。  
- **注意点:** チャートがテーブルセル内にある場合、凡例が狭く表示されることがあります。凡例を配置する前に、チャートサイズ（`chart.Width`、`chart.Height`）を拡大することを検討してください。  
- **パフォーマンスに関する注意:** 大容量のドキュメント（数百 MB）を読み込むとメモリ使用量が増大します。チャート操作だけが必要な場合は、`LoadOptions` に `LoadFormat.Docx` を指定してオーバーヘッドを削減しましょう。  

## 次のステップ

Now that you know **how to add legend** and **apply preset chart style** in Word, you might explore:  

Word で **凡例の追加** と **プリセットチャートスタイルの適用** ができるようになったので、次のことを検討できます：  

- **カスタムチャートカラー** (`chart.Series[i].Format.Fill.ForeColor`)。  
- **データラベルの書式設定** (`chart.Series[i].HasDataLabel = true`)。  
- **チャートを画像としてエクスポート** (`chart.ToImage()`)、他の場所に埋め込む際に便利です。  

Each of these topics builds on the same object model, so you’ll find the learning curve gentle.  

これらのトピックはすべて同じオブジェクトモデルに基づいているため、学習曲線は緩やかです。  

## 結論

We’ve just demonstrated a clean, end‑to‑end solution for **show chart legend** in a Word document using C#. By loading the document, retrieving the chart, applying a preset style, enabling the legend, and handling Waterfall quirks, you get a polished chart ready for any business report.  

私たちは C# を使用して Word 文書内に **チャート凡例を表示** する、クリーンでエンドツーエンドのソリューションを実演しました。ドキュメントの読み込み、チャートの取得、プリセットスタイルの適用、凡例の有効化、そしてウォーターフォールの特殊処理を行うことで、ビジネスレポートにすぐ使える洗練されたチャートが得られます。  

Feel free to experiment with other `ChartStyle` values or legend positions—your data visualizations deserve the best presentation. If you hit any snags, drop a comment below; happy coding!  

他の `ChartStyle` の値や凡例の位置を試してみてください—データ可視化は最高のプレゼンテーションに値します。問題があれば下にコメントを残してください。コーディングを楽しんで！  

## 次に学ぶべきことは？

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.  

以下のチュートリアルは、本ガイドで示した手法を基にした、密接に関連するトピックをカバーしています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。  

- [Word ドキュメントに列グラフを挿入する](/words/english/net/programming-with-charts/insert-column-chart/)  
- [Word ドキュメントでチャート軸を非表示にする](/words/english/net/programming-with-charts/hide-chart-axis/)  
- [Word チャート API の使用](/words/english/net/programming-with-charts/)  

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}