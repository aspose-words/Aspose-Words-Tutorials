---
category: general
date: 2026-10-20
description: Aspose.Words を使用して Word 文書に円グラフを作成する – 色の設定、スライスの分離、Word 文書の保存方法を示すステップバイステップガイド.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save word document
- how to create chart
- how to explode slice
- how to set color
language: ja
lastmod: 2026-10-20
og_description: Aspose.Words を使用して Word 文書に円グラフを作成します。色の設定、スライスの分離、Word 文書の保存方法を、単一の実行可能なサンプルで学びましょう。
og_image_alt: Screenshot of a Word document containing a customized pie chart with
  an exploded red slice
og_title: Word文書に円グラフを作成する – 完全C#ガイド
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create pie chart in a Word document using Aspose.Words – step‑by‑step
    guide that shows how to set color, explode slice, and save Word document.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart automation
title: Aspose.Words を使用して Word 文書に円グラフを作成する方法
url: /ja/java/images-shapes/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words を使用して Word ドキュメントに円グラフを作成する方法

Word ファイル内に **create pie chart** を作成する必要がある場合、このガイドではその手順を正確に示します。カスタムカラーの設定、強調のためにスライスを分離する方法、そして最終的に **save Word document** してチャートを埋め込む方法が分かります。

チャートをプログラムで生成することで、Word を開いてチャートを挿入し、外観を調整するという手作業を省くことができます。このチュートリアルの最後までに、円グラフを作成しカスタマイズしてディスクに書き出す、完全な実行可能な C# コンソール アプリケーションが手に入ります。

## 前提条件

* .NET 6.0 SDK 以降がインストールされていること  
* 有効な Aspose.Words for .NET ライセンス（または無料評価キー）  
* Visual Studio 2022 や VS Code などの IDE  

`Aspose.Words` 以外に追加の NuGet パッケージは必要ありません。

## Word ドキュメントで円グラフを作成する方法

最初のステップは `Document` と `DocumentBuilder` をインスタンス化することです。`DocumentBuilder` を使用すると、チャートの挿入を含む高度な Word 機能にアクセスできます。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a blank document and a builder.
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Step 2: Insert a 400x300‑point pie chart.
            Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data.
            // Series 0, Category 0‑2 correspond to three slices.
            pieChart.Series[0].DataPoints.Clear();
            pieChart.Series[0].DataPoints.Add(30); // Slice A
            pieChart.Series[0].DataPoints.Add(45); // Slice B
            pieChart.Series[0].DataPoints.Add(25); // Slice C

            // The chart is now part of the document; further customization follows.
```

この時点でドキュメントには基本的な円グラフが含まれています。次のセクションでは **スライスを分離する方法**、**色を設定する方法**、そして **Word ドキュメントを保存する方法** を説明します。

## 強調のためにスライスを分離する方法

スライスを分離すると、円全体から切り離され、読者の目を引きます。Aspose.Words API では、ポイント単位で分離距離を指定できます。

```csharp
            // Step 3: Explode the first slice (index 0) by 20 points.
            // This moves the slice outward while keeping the rest of the chart intact.
            pieChart.Series[0].SetExplosion(0, 20);
```

なぜスライスを分離するのでしょうか？「ベストセラー商品」など特定のカテゴリを強調するレポートでは、視覚的な分離によりデータポイントが瞬時に認識されます。

## チャートのスライスに色を設定する方法

カスタムカラーはブランドの一貫性と可読性を向上させます。任意の `System.Drawing.Color` を特定のデータポイントに割り当てることができます。

```csharp
            // Step 4: Apply a red fill to the same slice we just exploded.
            // The Fill property controls the interior color of the slice.
            pieChart.Series[0].DataPoints[0].Fill.ForeColor = Color.Red;
```

事前定義されたカラーに限定されず、`Color.FromArgb` を使用して正確な色合いを作成できます。

## チャート付きの Word ドキュメントを保存する方法

チャートが希望通りになったら、ファイルの保存は簡単です。`Document.Save` メソッドは指定した形式でドキュメントを書き込みます。ここではデフォルトの `.docx` を使用します。

```csharp
            // Step 5: Save the document to the desired location.
            string outputPath = @"C:\Temp\PieChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

プログラムを実行すると `PieChart.docx` が作成されます。Microsoft Word でファイルを開くと、最初のスライスが分離され赤色で塗られた円グラフが表示され、コードどおりになっています。

### 期待される結果

* `C:\Temp` に **PieChart.docx** という名前の Word ファイルが作成されます。  
* ドキュメントには単一の円グラフが含まれ、サイズは 400 × 300 ポイントです。  
* スライス 0 は 20 ポイントオフセットされ赤色で塗られ、他のスライスはデフォルトの色のままです。  

Word でチャートを選択し、スライスのプロパティを確認することで、分離と色を検証できます。

## プロのコツと一般的な落とし穴

* **プロのコツ:** チャートのタイトルや凡例を変更する必要がある場合、保存前に `pieChart.Title.Text` と `pieChart.Legend` プロパティを使用します。  
* **注意点:** デフォルトのデータポイントをクリアし忘れると、余分な不要なスライスが生成されます。独自のデータを追加する前に必ず `Series[0].DataPoints.Clear()` を呼び出してください。  
* **パフォーマンスのコツ:** 大規模なドキュメントでは、複数のビルダーを作成する代わりに単一の `DocumentBuilder` インスタンスを再利用すると、メモリ使用量が削減されます。

## Aspose.Words を使用してチャートを作成する方法（追加コンテキスト）

`InsertChart` メソッドは円グラフ以外にも、棒グラフ、折れ線グラフ、エリア グラフなど多数のチャートタイプをサポートしています。別のタイプに切り替えるには、`ChartType.Pie` を目的の列挙値（例: `ChartType.Column`）に置き換えます。カスタマイズ手順（スライスの分離、色の設定）は同様のパターンで行えますが、すべてのチャートタイプが “explosion” プロパティを提供しているわけではありません。

## 他のチャートタイプでスライスを分離する方法

円グラフタイプのチャートだけが `SetExplosion` メソッドを提供します。棒グラフでこのメソッドを呼び出すと、API は `ArgumentException` をスローします。そのような場合は、データ ラベルやコールアウトを使用して特定の棒を強調することを検討してください。

## 単一スライスではなくシリーズ全体に色を設定する方法

シリーズ内のすべてのスライスに同じ色を適用したい場合は、データポイントをループ処理します：

```csharp
foreach (ChartDataPoint point in pieChart.Series[0].DataPoints)
{
    point.Fill.ForeColor = Color.Blue;
}
```

この方法は、複数のチャートで統一されたカラースキームが必要なときに便利です。

## Word ドキュメントを他の形式で保存する方法

Aspose.Words は PDF、HTML など多数の形式にエクスポートできます。`Save` 時にファイル拡張子を変更し、必要に応じて `SaveOptions` オブジェクトを渡します：

```csharp
document.Save(@"C:\Temp\PieChart.pdf", SaveFormat.Pdf);
```

チャート描画エンジンは、色や分離設定を保持したまま、チャートを対象の形式に自動的に変換します。

## 結論

これで、Word ドキュメントに **円グラフを作成** し、**スライスを分離** して **色を設定** することで外観をカスタマイズし、最終的に **Word ドキュメントを保存** してチャートを埋め込む方法が分かりました。このエンドツーエンドの例は、レポート生成やダッシュボード、プログラムで視覚データを挿入する必要があるあらゆるシナリオを自動化するための確固たる基盤を提供します。

### 次のステップ

* 他のチャートタイプ（`ChartType.Column`、`ChartType.Line`）を調査して、レポート作成ツールキットを拡充する。  
* 複数のチャートを単一のドキュメントに組み合わせ、包括的なダッシュボードを構築する。  
* `ChartDataLabel` を試して、スライス上にパーセンテージや値を直接表示する。

コードはご自身のデータ ソースに合わせて自由に適応してください。データベース、API、CSV ファイルのいずれから取得しても、同じ Aspose.Words のワークフローが適用できます。チャート作成をお楽しみください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [C# と Aspose.Words で円グラフのスライスを分離する – 完全ガイド](/words/english/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/)
- [Aspose.Words for .NET を使用して Word ドキュメントにカスタム列グラフを挿入](/words/english/net/programming-with-charts/insert-custom-chart/)
- [Aspose.Words for .NET を使用して Word ドキュメントのチャートシリーズ データを更新](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}