---
category: general
date: 2026-08-04
description: C# のチャートにおけるカスタム データ ラベル配置は、チャートのスライス上にラベルを中央に配置できます。Aspose.Words のチャート
  API を使用したステップバイステップ ガイドに従ってください。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Custom Data‑Label Placement for Charts
- chart data label positioning
- Aspose.Words chart API
- C# chart manipulation
- Word document chart automation
language: ja
lastmod: 2026-08-04
og_description: C#でのチャートのカスタム データ ラベル配置では、Word チャートの各スライスのデータ ラベルをすべて中央に配置する方法を示します。Aspose.Words
  でチャートのデータ ラベル配置をマスターしましょう。
og_image_alt: Screenshot of a Word chart with centered data labels after applying
  C# code
og_title: C#でチャートのデータラベル配置をカスタマイズする – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Custom Data‑Label Placement for Charts in C# lets you center labels
    on chart slices. Follow this step‑by‑step guide using Aspose.Words chart API.
  headline: Custom Data‑Label Placement for Charts in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart
- Data Labels
title: C#でのチャート用カスタムデータラベル配置
url: /ja/net/programming-with-charts/custom-data-label-placement-for-charts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# におけるチャートのカスタム データ ラベル配置

**Custom Data‑Label Placement for Charts** は、Word 文書内のチャート上で各ラベルの表示位置を正確に制御できるようにします。このチュートリアルでは、C# と Aspose.Words のチャート API を使用して、各スライスのデータ ラベルをすべて中央に配置する方法を学びます。

完全な実行可能サンプルが提供されます。サンプルは `.docx` ファイルを読み込み、最初のチャート シェイプにアクセスし、すべてのラベルの `Position` を `Center` に変更し、更新されたドキュメントを保存します。外部参照は不要で、Aspose.Words for .NET ライブラリと基本的な C# 開発環境だけで実行できます。

**学べること**

* チャートを含む Word 文書の読み込み方法  
* Aspose.Words のチャート API を使用してチャート シェイプを取得する方法  
* チャート内のすべての系列に対して **チャート データ ラベルの配置** を適用する方法  
* ラベルが中央に配置された状態で Word に保存する方法  

**前提条件**

* .NET 6.0（またはそれ以降）をインストール済み  
* Visual Studio 2022（または任意の C# IDE）  
* `Aspose.Words` NuGet パッケージへの参照  
* 少なくとも 1 つのチャートを含む Word ファイル（`Chart.docx`）  

---

## Custom Data‑Label Placement for Charts – 手順 1: ドキュメントの読み込み

最初の操作は、チャートが格納されている Word ファイルを開くことです。`Document` は Aspose.Words でのすべての操作のエントリーポイントです。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the source Word document.
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

// Verify that the document actually contains a chart.
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
if (shapes.Count == 0)
{
    throw new InvalidOperationException("The document does not contain any shapes.");
}
```

*Why this step matters*: ドキュメントを読み込まなければチャート オブジェクトに到達できません。バリデーションにより、ファイルにチャートが含まれていない場合は明確なエラーが返され、後続の null 参照を防止します。

---

## Aspose.Words のチャート API を使用してチャート シェイプにアクセスする

Aspose.Words はチャートを `Shape` 内にネストされた `Chart` オブジェクトとして扱います。適切な子ノードをキャストして取得します。

```csharp
// Get the first shape that is a chart.
Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (!chartShape.HasChart)
{
    throw new InvalidOperationException("The first shape is not a chart.");
}

// Extract the Chart instance.
Chart chart = chartShape.GetChart();
```

*Why this step matters*: `Chart` に直接アクセスすることで、系列、データ ポイント、ラベル プロパティをフルコントロールできます。シェイプがチャートでない場合、コードは情報提供的なメッセージとともに早期に中止します。

---

## C# でチャート データ ラベルの配置を設定する

次に、すべての系列とすべてのデータ ラベルを走査し、`Position` を `Center` に設定します。これが **Custom Data‑Label Placement for Charts** の核心です。

```csharp
// Center all data labels on each slice of the chart.
foreach (Series series in chart.Series)
{
    foreach (ChartDataLabel label in series.DataLabels)
    {
        // Position enum values: Center, InsideEnd, OutsideEnd, etc.
        label.Position = ChartDataLabelPosition.Center;
    }
}
```

**Pro tip**: 別の配置が必要な場合（例: 列チャートの `InsideEnd`）は、列挙値を適宜変更してください。`ChartDataLabelPosition` 列挙体は、Word がサポートするすべての標準位置を網羅しています。

*Why this step matters*: `label.Position` を変更すると、基になる OOXML 表現が更新されるため、Microsoft Word でドキュメントを開いたときにラベルが中央に表示されます。

---

## 更新されたラベルで Word 文書を保存する

チャートの変更が完了したら、変更をファイルに永続化します。元のファイルを上書きすることも、新しいコピーを作成することも可能です。

```csharp
// Save the modified document with centered labels.
doc.Save(@"YOUR_DIRECTORY\ChartLabelsCentered.docx");
```

*Why this step matters*: 保存により、更新された OOXML がディスクに書き込まれます。`ChartLabelsCentered.docx` を Word で開くと、すべてのスライス ラベルが中央に配置されていることが確認でき、**Custom Data‑Label Placement for Charts** が正常に完了したことが分かります。

---

## エッジケースとバリエーション

| 状況 | 対処方法 |
|-----------|---------------|
| **Multiple charts** in the same document | `doc.GetChildNodes(NodeType.Shape, true)` をループし、各シェイプの `shape.HasChart` をチェックします。 |
| **Different chart types** (pie, doughnut, bar) | `ChartDataLabelPosition.Center` は円グラフ系で機能します。棒・列チャートの場合は `InsideEnd` や `OutsideEnd` が好まれることがあります。 |
| **Label text needs formatting** | `label.TextProperties` にアクセスしてフォントサイズ、色、太字などを設定します。 |
| **Running on .NET Core** | .NET Standard バージョンの Aspose.Words を参照してください。API は同一です。 |

---

## 完全な動作例

以下はコンソール アプリケーションにコピーペーストできるフル プログラムです。必要な `using` ディレクティブとエラーハンドリングをすべて含んでいます。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Path to the source and destination files.
        const string sourcePath = @"YOUR_DIRECTORY\Chart.docx";
        const string destPath   = @"YOUR_DIRECTORY\ChartLabelsCentered.docx";

        // Load the document.
        Document doc = new Document(sourcePath);

        // Find the first chart shape.
        Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (chartShape == null || !chartShape.HasChart)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Get the Chart object.
        Chart chart = chartShape.GetChart();

        // Center all data labels.
        foreach (Series series in chart.Series)
        {
            foreach (ChartDataLabel label in series.DataLabels)
            {
                label.Position = ChartDataLabelPosition.Center;
            }
        }

        // Save the updated document.
        doc.Save(destPath);
        Console.WriteLine($"Document saved with centered labels to: {destPath}");
    }
}
```

**Expected result**: Microsoft Word で `ChartLabelsCentered.docx` を開くと、チャートの各スライスにデータ ラベルがスライスの中心に直接表示され、視覚的にすっきりした外観になります。

---

## 結論

これで C# における **Custom Data‑Label Placement for Charts** ソリューションが完成しました。ドキュメントを読み込み、Aspose.Words のチャート API を介してチャートにアクセスし、すべてのラベルに `ChartDataLabelPosition.Center` を設定し、ファイルを保存することで、任意の Word ベースのチャートのラベル配置を自動化できます。

次のステップとして、`InsideEnd` や `OutsideEnd` といった他の **chart data label positioning** オプションを試したり、**C# chart manipulation** を活用して色の変更、凡例の追加、ゼロからのチャート生成に挑戦してみてください。これらの拡張は本稿で紹介した手法を直接応用でき、Word 文書のチャート自動化スキルをさらに広げてくれます。Happy coding!

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを基にした、密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説と完全なコード例が含まれており、API の追加機能をマスターしたり、独自の実装アプローチを探求したりするのに役立ちます。

- [チャート データ ラベルのカスタマイズ](/words/english/net/programming-with-charts/chart-data-label/)
- [チャート内データ ラベルの数値書式設定](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Chart Data Label](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}