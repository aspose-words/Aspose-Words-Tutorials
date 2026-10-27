---
category: general
date: 2026-10-13
description: C#で円グラフをカスタマイズし、スライスを分離、最初のスライスの角度を変更、パーセンテージラベルを表示した後、変更したドキュメントを保存する。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save modified document
- show percentage labels
- explode pie chart slices
- display percentages pie
- change first slice
language: ja
lastmod: 2026-10-13
og_description: C#で円グラフをカスタマイズした後、変更したドキュメントを保存します。円グラフのスライスを分離する方法、最初のスライスの角度を変更する方法、パーセンテージラベルを表示する方法を学びましょう。
og_image_alt: Screenshot of a Word document where the pie chart slices are exploded
  and percentage labels are displayed after saving the modified document
og_title: 分割された円グラフスライスを含む変更ドキュメントを保存 – C# ガイド
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 'Save modified document after customizing a pie chart: explode slices,
    change first slice angle, and show percentage labels in C#.'
  headline: Save modified document with exploded pie chart slices in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word chart
- pie chart
- document manipulation
title: C#で、分割された円グラフスライスを含む変更済みドキュメントを保存する
url: /ja/net/programming-with-charts/save-modified-document-with-exploded-pie-chart-slices-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で円グラフのスライスを分離した状態で文書を保存する

Word の円グラフを調整した後に **save modified document** が必要な場合、このガイドで正確な手順を示します。円グラフのスライスを分離し、最初のスライスの角度を変更し、パーセンテージラベルを表示する方法を、数行の C# コードで学びます。

チャートのカスタマイズは、レポート、請求書、ダッシュボードをプログラムで生成する際に一般的な要件です。このチュートリアルの最後までに、DOCX ファイルを読み込み、チャートの外観を変更し、配布可能な **save modified document** を作成できるようになります。

## Prerequisites

- .NET 6.0 以降（コードは .NET Framework 4.6+ でも動作します）
- Aspose.Words for .NET 23.10 以降（無料トライアルまたはライセンス版）
- 単一の円グラフを含む Word ファイル（`input.docx`）
- Visual Studio 2022 または任意の C# IDE

> **Tip:** Aspose.Words の NuGet パッケージは `dotnet add package Aspose.Words` で追加します。

## Step 1: Load the Word document that contains the chart

最初のステップは、対象の DOCX ファイルを開くことです。`Document` クラスはメモリ上の Word ファイル全体を表します。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

ドキュメントを読み込むことで、チャートを保持するシェイプを含むすべてのノードにフルアクセスできます。

## Step 2: Retrieve the first chart shape from the document

チャートは `Shape` ノード内に格納されています。`GetChild` を使って最初のチャートを取得できます。

```csharp
        // Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
```

ドキュメントに複数のチャートがある場合はインデックス（`0`）を調整するか、コレクションをループしてください。この行は、変更対象となる `Chart` オブジェクトへの参照を確保します。

## Step 3: Explode pie chart slices

スライスを分離すると、円全体からそのスライスが離れ、読みやすくなります。`Explode` プロパティはシリーズ全体に適用されます。

```csharp
        // Enable slice explosion so each slice is separated from the pie
        chart.PieChart.Explode = true;
```

`Explode` を `true` に設定すると、**explodes pie chart slices** がシリーズ全体に適用され、すべてのスライスを目立たせるのに便利です。

## Step 4: Change the first slice angle

デザインガイドラインに合わせるなど、最初のスライスをカスタム角度で開始したい場合があります。

```csharp
        // Set a custom start angle for the first slice (30 degrees)
        chart.PieChart.FirstSliceAngle = 30;
```

`FirstSliceAngle` プロパティは **changes first slice** の向きを変更し、円全体を回転させて最初のスライスが 30 度から始まるようにします。

## Step 5: Show percentage labels on the pie slices

各スライスの数値的貢献度を表示することはレポートでよく求められます。`DataLabel.ShowPercentage` フラグを有効にするとパーセンテージが表示されます。

```csharp
        // Display percentage values on the data labels of the pie slices
        chart.PieChart.DataLabel.ShowPercentage = true;
```

この手順で **show percentage labels** がチャート上に直接表示され、**display percentages pie** の要件も満たします。

## Step 6: Save the modified document

すべてのカスタマイズが完了したら、変更を新しいファイルに永続化します。`Save` メソッドは更新された DOCX をディスクに書き込みます。

```csharp
        // Save the modified document
        doc.Save(@"YOUR_DIRECTORY\output.docx");
    }
}
```

これで **save modified document** が完成し、分離された円グラフ、回転した最初のスライス、そしてパーセンテージラベルが含まれます。

![保存された文書に表示された分離された円グラフ](/images/pie-chart-exploded.png "保存された文書に分離された円グラフのスライスとパーセンテージラベル")

*このスクリーンショットは、文書を保存した後の最終出力を示しています。*

## Full, runnable example

以下に、コンソールプロジェクトにコピー＆ペーストできる完全なプログラムを示します。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace PieChartCustomizer
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source DOCX
            Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

            // 2️⃣ Get the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Explode all slices
            chart.PieChart.Explode = true;

            // 4️⃣ Rotate the first slice to 30°
            chart.PieChart.FirstSliceAngle = 30;

            // 5️⃣ Show percentages on each slice
            chart.PieChart.DataLabel.ShowPercentage = true;

            // 6️⃣ Persist the changes
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Expected result

`output.docx` を開くと、円グラフは次のように表示されます。

- すべてのスライスが少し分離されています（**exploded pie chart slices**）
- 最初のスライスが 30 度のオフセットで開始します（**change first slice**）
- 各スライスがパーセンテージで貢献度を示します（**show percentage labels**, **display percentages pie**）
- 元のファイルを変更せずに **save modified document** が行われています。

## Common questions and edge cases

| Question | Answer |
|----------|--------|
| **What if the document has no chart?** | コードは `GetChild` 後に `null` をチェックします。チャートが存在しない場合は、プログラムで追加するか、明確なメッセージで中止できます。 |
| **Can I explode only a single slice?** | はい。`chart.PieChart.Series[0].DataPoints[i].Explosion = true;` のように、`i` をスライスのインデックスに置き換えて使用します。 |
| **How do I change the label format (e.g., show value + %)?** | `chart.PieChart.DataLabel.ShowValue = true;` と、必要に応じて `chart.PieChart.DataLabel.ShowPercentage = true;` を設定して両方を組み合わせます。 |
| **Is the chart style preserved after saving?** | Aspose.Words は **save modified document** 時に、色やフォントを含むすべてのスタイリングを保持します。 |
| **Can I process multiple charts in the same file?** | `NodeType.Shape` のすべての `Shape` ノードをループし、`shape.HasChart` でフィルタリングします。各チャートに同じ手順を適用してください。 |

## Conclusion

これで Word の円グラフをプログラムでカスタマイズした後に **save modified document** する方法が分かりました。本ガイドでは、円グラフのスライスを分離し、最初のスライス角度を変更し、パーセンテージラベルを表示する手順を解説し、**show percentage labels**, **explode pie chart slices**, **display percentages pie**, **change first slice** の要件を満たしました。

次に検討すべきこと：

- データ系列を動的に追加する (`chart.Series.Add(...)`)  
- 凡例の配置やチャートタイトルのカスタマイズ  
- チャートのスタイルを保持したまま DOCX を PDF に変換  

さまざまな角度、分離設定、ラベル形式を試して、レポート要件に合わせてください。Happy coding!

## What Should You Learn Next?

以下のチュートリアルは、本ガイドで示した手法を基にした、密接に関連するトピックを扱っています。各リソースには、完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを探求するのに役立ちます。

- [C# で Aspose.Words を使用して編集済み文書を保存する方法 – ステップバイステップガイド](/words/english/net/programming-with-docsaveoptions/how-to-save-edited-document-in-c-with-aspose-words-step-by-s/)
- [Aspose.Words for .NET を使用して Word 文書内のチャート系列データを更新する](/words/english/net/programming-with-charts/modify-chart-series/)
- [Word 文書に縦棒グラフを挿入する](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}