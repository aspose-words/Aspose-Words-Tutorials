---
category: general
date: 2026-10-13
description: C# を使用して Word 文書内のチャートラベルをプログラムで調整する方法を学びましょう。このガイドでは Aspose.Words のチャート操作とラベルの配置について解説します。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically adjust chart labels
- Aspose.Words chart manipulation
- C# chart data label
- Word document chart example
- modify chart label position
- set data label alignment
language: ja
lastmod: 2026-10-13
og_description: C# を使用して Word 文書内のチャートラベルをプログラムで調整します。この完全なチュートリアルに従って、ラベルの配置や整列、その他の設定を変更しましょう。
og_image_alt: Screenshot showing programmatically adjust chart labels in a Word document
og_title: Wordでチャートラベルをプログラム的に調整する – C#ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to programmatically adjust chart labels in a Word document
    using C#. This guide covers Aspose.Words chart manipulation and label alignment.
  headline: Programmatically adjust chart labels in a Word document with C#
  type: TechArticle
tags:
- chart labels
- C#
- Aspose.Words
title: C# を使用して Word 文書内のチャートラベルをプログラムで調整する
url: /ja/net/programming-with-charts/programmatically-adjust-chart-labels-in-a-word-document-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# を使用して Word 文書のチャート ラベルをプログラムで調整する

Word 文書内の **programmatically adjust chart labels** が必要な場合、本ガイドでは C# での具体的な手順を示します。レポートの生成、ダッシュボードの自動化、テンプレートのカスタマイズなど、.docx ファイル内のチャートのラベル位置と配置を変更する完全な実行可能サンプルをご覧いただけます。

また、**Aspose.Words chart manipulation** の手法や、複数シリーズの扱い方、**C# chart data label** オブジェクトを使用する際の一般的な落とし穴の回避方法も学べます。

## Prerequisites

開始する前に、以下がインストールされていることを確認してください。

* .NET 6.0（またはそれ以降）  
* Visual Studio 2022（または任意の C# IDE）  
* **Aspose.Words for .NET** NuGet パッケージ（`Install-Package Aspose.Words`）  
* 少なくとも 1 つのチャートが含まれる Word 文書（`input.docx`）  

これらは、**Word document chart example** を変更するために必要な項目です。

## Step 1: Set up the project and import namespaces

新しいコンソール プロジェクトを作成し、必要な `using` ディレクティブを追加します。これにより **programmatically adjust chart labels** の環境が整います。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source and destination files
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the document that contains a chart
            Document doc = new Document(inputPath);
```

*Why this step?*  
ドキュメントを読み込むことで、内部の **Word document chart example** ツリーにアクセスでき、チャートがシェイプ ノードとして格納されていることが分かります。

## Step 2: Locate the first chart shape

チャートは `Shape` ノードとして格納されています。以下のコードは、ドキュメント内の最初のチャートを取得し、ラベル調整の対象とします。

```csharp
            // Retrieve the first chart shape in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }
```

*Why this step?*  
`GetChild` メソッドは再帰的に検索（`true`）し、`Shape` 型の最初のノードを返します。`Chart` にキャストすることで、チャート固有の API を使用できるようになります。

## Step 3: Access the data label you want to modify

チャートの各シリーズにはデータ ラベルのコレクションがあります。シンプルなチャートでは、最初のラベルだけで十分なことが多いです。以下のコードでそのラベルにアクセスする方法を示します。

```csharp
            // Access the first series' first data label
            ChartSeries series = chart.Series[0];
            ChartDataLabel dataLabel = series.DataLabelCollection[0];
```

*Why this step?*  
`ChartSeries` はポイントのシリーズを表します。`DataLabelCollection` はそのシリーズのラベルを保持し、配置や配置の細かな制御が可能です。

## Step 4: Change label placement and alignment

ここで **programmatically adjust chart labels** を行い、位置、水平配置、垂直配置を設定します。これらのプロパティは Word の UI にあるオプションに対応しています。

```csharp
            // Set the label's position relative to the data point
            dataLabel.Position = DataLabelPosition.OutsideEnd; // Options: OutsideEnd, InsideEnd, etc.

            // Align the label horizontally and vertically
            dataLabel.HorizontalAlignment = HorizontalAlignment.Center;
            dataLabel.VerticalAlignment = VerticalAlignment.Top;
```

*Why these settings?*  

* `OutsideEnd` はラベルを各棒または列の端のすぐ外側に配置し、可読性を向上させます。  
* `HorizontalAlignment.Center` はテキストをポイントの上で中央揃えにし、`VerticalAlignment.Top` はラベルの上端をデータポイントに合わせて配置するため、他の要素との重なりを防ぎます。

### Pro tip
チャートに複数のシリーズがある場合は、`chart.Series` をループし、各 `DataLabelCollection` に同じ設定を適用してください。これにより、チャート全体で一貫した外観が保たれます。

```csharp
            // Example: adjust all series in the chart
            foreach (ChartSeries s in chart.Series)
            {
                foreach (ChartDataLabel lbl in s.DataLabelCollection)
                {
                    lbl.Position = DataLabelPosition.OutsideEnd;
                    lbl.HorizontalAlignment = HorizontalAlignment.Center;
                    lbl.VerticalAlignment = VerticalAlignment.Top;
                }
            }
```

## Step 5: Save the modified document

ラベル調整が完了したら、変更を新しいファイルに保存します。これで **modify chart label position** のプロセスは完了です。

```csharp
            // Save the updated document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

`output.docx` を開くと、すべてのチャート ラベルがデータポイントの外側端に移動し、水平に中央揃え、垂直に上揃えになっていることが確認できます。

## Edge cases and variations

| Situation | What to watch for | Recommended approach |
|-----------|-------------------|----------------------|
| **Multiple charts** in the same document | `GetChild` only returns the first chart. | Use `doc.GetChildNodes(NodeType.Shape, true)` to iterate over all chart shapes. |
| **Series without data labels** | `DataLabelCollection` may be empty. | Check `series.HasDataLabels` before accessing the collection. |
| **Different chart types** (pie, line, scatter) | Not all `DataLabelPosition` values are valid. | Use `DataLabelPosition.Auto` for charts that decide the best placement automatically. |
| **Localization** | Alignment constants are language‑agnostic, but the rendered text may need right‑to‑left support. | Set `dataLabel.TextDirection` if you need RTL languages. |

## Complete, runnable example

以下に、コピーして貼り付けて実行できる完全なプログラムを示します。`YOUR_DIRECTORY` を実際のフォルダー パスに置き換えてください。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the Word document that contains a chart
            Document doc = new Document(inputPath);

            // Retrieve the first chart shape from the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Loop through all series and adjust each data label
            foreach (ChartSeries series in chart.Series)
            {
                foreach (ChartDataLabel label in series.DataLabelCollection)
                {
                    label.Position = DataLabelPosition.OutsideEnd;
                    label.HorizontalAlignment = HorizontalAlignment.Center;
                    label.VerticalAlignment = VerticalAlignment.Top;
                }
            }

            // Save the modified document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Expected result:** Opening `output.docx` shows each chart label positioned outside the data point, centered horizontally, and aligned to the top—exactly the effect of **programmatically adjust chart labels** you scripted.

## Conclusion

これで C# を使用して Word 文書の **programmatically adjust chart labels** 方法が分かりました。本チュートリアルでは以下をカバーしました。

* **Aspose.Words chart manipulation** を用いたドキュメントの読み込み  
* **C# chart data label** の取得  
* **modify chart label position** と配置の変更  
* ファイルの保存と一般的なエッジケースの処理  

ここからは、ラベルフォントのカスタマイズ、条件付き書式の追加、バッチ処理での複数チャートの更新など、より高度なシナリオに挑戦できます。さまざまな `DataLabelPosition` オプションを試して、レポートに最適なスタイルを見つけてください。

---

*自動レポート パイプラインをさらに強化したいですか？ラベルにカスタム数値書式を追加したり、チャートを画像としてエクスポートして PDF に使用したりしてみましょう。*

## What Should You Learn Next?

以下のチュートリアルは、本ガイドで示した手法を基にした関連トピックを扱っています。各リソースには、完全な動作コード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、独自プロジェクトで代替実装アプローチを検討したりするのに役立ちます。

- [Set Uniform Data Labels in a Column Chart Using Aspose.Words for .NET](/words/english/net/programming-with-charts/uniform-data-labels/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}