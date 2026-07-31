---
category: general
date: 2026-07-29
description: Word文書でグラフを編集する方法—グラフラベルの位置を変更し、棒グラフのラベルを調整し、データラベルを修正し、ラベルのフォントを変更する方法を学ぶ。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- change chart label position
- adjust bar chart labels
- modify chart data labels
- change chart label font
language: ja
lastmod: 2026-07-29
og_description: Wordでチャートを素早く編集する方法。チャートラベルの位置変更、棒グラフのラベル調整、データラベルの修正、ラベルフォントの変更をマスターしましょう。
og_image_alt: Screenshot of a Word bar chart with custom label positions and larger
  font size
og_title: Wordでチャートを編集する方法 – ラベルとフォントを変更
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  headline: 'How to Edit Chart in Word: Change Label Position, Font & More'
  type: TechArticle
- description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  name: 'How to Edit Chart in Word: Change Label Position, Font & More'
  steps:
  - name: What if the document contains multiple charts?
    text: 'The code above grabs the *first* chart (`GetChild(NodeType.Shape, 0, true)`).
      To edit all charts, replace the single retrieval with a loop:'
  - name: How to **change chart label font** for a specific series only?
    text: 'Each `ChartSeries` has its own `DataLabelCollection`. Target a series by
      index:'
  - name: Does this work with pie or line charts?
    text: Yes—`ChartDataLabelPosition` supports values like `InsideEnd`, `OutsideEnd`,
      and `BestFit`. For a pie chart you might prefer `OutsideEnd` to keep labels
      readable.
  - name: What about localization (e.g., different decimal separators)?
    text: Aspose.Words respects the document’s locale settings. If you need to enforce
      a specific format, adjust `label.NumberFormat` before saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: Wordでチャートを編集する方法：ラベル位置、フォントなどを変更
url: /ja/net/working-with-charts/how-to-edit-chart-in-word-change-label-position-font-more/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word でチャートを編集する方法: ラベル位置、フォントなどを変更

Word 文書内のチャートを編集する必要は、レポートを洗練された見た目にしたいときに頻繁に出てきます。**チャート ラベルの位置を変更**したり、メニューを何度も辿らずにラベルを読みやすくしたりするのに苦労したことはありませんか？あなたは一人ではありません—レポート自動生成を行う多くの開発者が同じ壁にぶつかります。このガイドでは、C# と Aspose.Words ライブラリを使用して **棒グラフ ラベルを調整**、**チャート データ ラベルを変更**、そして **チャート ラベルのフォントを変更** する完全な実行可能サンプルをステップバイステップで解説します。

## 学習できること

- 既に棒グラフが含まれている .docx ファイルを読み込む。  
- 最初のチャート シェイプを取得し、そのデータ ラベル コレクションにアクセスする。  
- **チャート ラベルの位置を変更**して、棒がすっきり見えるようにする。  
- **棒グラフ ラベル** のフォントサイズを調整して可読性を向上させる。  
- 変更した文書をディスクに保存する。  

外部ツール不要、手動 UI 操作も不要—.NET プロジェクトにそのまま貼り付けられる純粋なコードだけです。最後まで読めば、何十もの文書で再利用できる自己完結型ソリューションが手に入ります。

> **前提条件**  
> - .NET 6.0 以降（コードは .NET Framework 4.7+ でも動作します）。  
> - Aspose.Words for .NET（NuGet で入手可能）。  
> - 既に棒グラフが含まれている Word ファイル（`BarChart.docx`）。  

これらが揃っていない場合は、最新の Aspose.Words パッケージを今すぐ取得してください：

```bash
dotnet add package Aspose.Words
```

---

## チャートの編集方法: Word 文書からチャートを取得する

**チャートの編集** オブジェクトへの最初のステップは、文書を読み込みチャート シェイプを見つけることです。Aspose.Words はチャートを `Shape` ノードとして扱うため、`GetChild` と `NodeType.Shape` を使って最初に見つかったチャートを取得できます。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the Word document that contains a chart
Document document = new Document(@"C:\Temp\BarChart.docx");

// Retrieve the first chart shape from the document
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
```

> **重要ポイント:**  
> `Chart` オブジェクトに直接アクセスすることで、Word でファイルを開いて手動でラベルを調整する手間が省けます。これは **チャート データ ラベルを変更** 自動化の基礎となります。

## 棒グラフ ラベルの調整: チャート ラベル位置の変更

`Chart` インスタンスが手に入ったので、`DataLabelCollection` を走査します。目的は **チャート ラベルの位置を変更** し、各ラベルが棒の基部内部にきれいに収まるようにすることです（上に浮かんでいるのではなく）。

```csharp
// Loop through each data label in the chart
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Place label inside the base of the bar
    dataLabel.Position = ChartDataLabelPosition.InsideBase;
}
```

> **プロのコツ:**  
> `InsideBase` は縦棒グラフでうまく機能します。横棒グラフの場合は `InsideEnd` を試してみてください。位置の調整はコードを再実行して保存された文書を開くだけで簡単に確認できます。

## チャート ラベル フォントの変更: 可読性のためにフォントサイズを調整

小さすぎるフォントはレポートの可読性を静かに蝕みます。**チャート ラベルのフォントを変更** するには、各 `ChartDataLabel` の `Font.Size` プロパティを設定するだけです。ここでは 9 pt に設定します。多くの印刷レポートでバランスの取れたサイズです。

```csharp
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Set a readable font size (9 points)
    dataLabel.Font.Size = 9;
}
```

> **この操作の理由:**  
> フォントサイズの調整は **チャート データ ラベルを変更** のベストプラクティスの一部です。大きめのフォントはアクセシビリティを向上させ、手動での後処理を減らします。

## 更新された文書を保存

位置とフォントを調整したら、**チャートの編集** の最終ステップは変更を永続化することです。Aspose.Words ならワンライナーで完了します。

```csharp
// Save the modified document with new label settings
document.Save(@"C:\Temp\BarChartCustomLabels.docx");
```

`BarChartCustomLabels.docx` を Word で開くと、ラベルが棒の内部にぴったり収まり、はっきりとした 9 pt フォントで表示されます。小さな数字に目を細める必要はもうありません。

---

## 完全動作サンプル（すべての手順を 1 ファイルにまとめた例）

以下は、文書の読み込みから更新版の保存までの全フローを示す、すぐに実行できるコンソール プログラムです。新しい .NET コンソール プロジェクトに貼り付けて **F5** を押すだけです。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source document (must contain a bar chart)
            string sourcePath = @"C:\Temp\BarChart.docx";

            // Path where the edited document will be saved
            string destPath = @"C:\Temp\BarChartCustomLabels.docx";

            // Load the Word document
            Document doc = new Document(sourcePath);

            // Retrieve the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Iterate over each data label
            foreach (ChartDataLabel label in chart.DataLabelCollection)
            {
                // Change chart label position
                label.Position = ChartDataLabelPosition.InsideBase;

                // Change chart label font size
                label.Font.Size = 9;
            }

            // Save the updated document
            doc.Save(destPath);
            Console.WriteLine($"Chart labels updated and saved to: {destPath}");
        }
    }
}
```

**プログラム実行時の期待出力:**

```
Chart labels updated and saved to: C:\Temp\BarChartCustomLabels.docx
```

生成されたファイルを開くと、**棒グラフ ラベルの調整** が棒の内部に配置され、快適なフォントサイズで表示されていることが確認できます。

---

## よくある質問とエッジケース

### 文書に複数のチャートが含まれている場合は？

上記コードは *最初の* チャート（`GetChild(NodeType.Shape, 0, true)`）を取得します。すべてのチャートを編集したい場合は、単一取得をループに置き換えてください：

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape shape in shapes)
{
    if (shape.HasChart)
    {
        Chart chart = shape.GetChart();
        // Apply label changes as shown earlier
    }
}
```

### 特定の系列だけ **チャート ラベルのフォントを変更** したい場合は？

各 `ChartSeries` には独自の `DataLabelCollection` が存在します。インデックスで系列を指定して対象にします：

```csharp
ChartSeries series = chart.Series[1]; // second series (zero‑based)
foreach (ChartDataLabel label in series.DataLabelCollection)
{
    label.Font.Size = 10; // larger for this series only
}
```

### 円グラフや折れ線グラフでも動作しますか？

はい。`ChartDataLabelPosition` は `InsideEnd`、`OutsideEnd`、`BestFit` などの値をサポートしています。円グラフの場合は、ラベルの可読性を保つために `OutsideEnd` が好まれることが多いです。

### ローカライズ（例: 小数点区切り文字の違い）はどう扱う？

Aspose.Words は文書のロケール設定を尊重します。特定の書式を強制したい場合は、保存前に `label.NumberFormat` を調整してください。

---

## まとめと次のステップ

**チャートの編集** オブジェクトを Word 文書で最初から最後まで扱う方法を網羅しました：ファイルの読み込み、チャートの取得、**チャート ラベルの位置を変更**、**棒グラフ ラベルの調整**、**チャート データ ラベルの変更**、そして最終的に **チャート ラベルのフォントを変更** して保存するまで。完全なサンプルは本番環境でも使えるレベルで、任意の自動化パイプラインに組み込めます。

次のステップとして、以下のアイデアを検討してみてください：

- **データ ラベルの色を設定**（`dataLabel.Font.Color = Color.Blue;`）。  
- **値をパーセンテージで表示**（`dataLabel.NumberFormat = "0%";`）。  
- **既存のチャートを読み込むのではなく、プログラムからチャートを作成**。  

これらはすべて本日使用した API と同じ領域に基づいているので、違和感なく取り組めるはずです。

問題が発生した場合はコメントを残すか、Aspose.Words のドキュメントでより深いチャート カスタマイズ方法を確認してください。コーディングを楽しみ、美しくラベル付けされたチャートを活用しましょう！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示した手法を応用した関連トピックを扱っています。各リソースには完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得したり、プロジェクトで代替実装アプローチを探求したりするのに役立ちます。

- [チャート データ ラベルのカスタマイズ](/words/english/net/programming-with-charts/chart-data-label/)
- [チャート内データ ラベルの数値書式設定](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [チャート データ ラベル](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}