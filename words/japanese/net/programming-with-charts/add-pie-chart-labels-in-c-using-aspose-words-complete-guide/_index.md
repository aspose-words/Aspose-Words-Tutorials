---
category: general
date: 2026-07-20
description: Aspose.Words for .NET を使用して円グラフのラベルを追加します。円グラフのラベルの変更方法、パーセンテージラベルの表示方法、チャート系列ラベルの迅速な更新方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart labels
- change pie chart labels
- update chart series labels
- show percentage labels
- display pie chart percentages
language: ja
lastmod: 2026-07-20
og_description: C# と Aspose.Words で円グラフのラベルを追加します。数ステップで円グラフのラベル変更、パーセンテージラベルの表示、チャート系列ラベルの更新をマスターできます。
og_image_alt: Word document screenshot displaying a pie chart with custom percentage
  labels
og_title: C#で円グラフのラベルを追加 – Aspose.Words 完全チュートリアル
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Add pie chart labels with Aspose.Words for .NET. Learn how to change
    pie chart labels, show percentage labels, and update chart series labels quickly.
  headline: Add pie chart labels in C# using Aspose.Words – Complete Guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Aspose.Words を使用した C# での円グラフラベルの追加 – 完全ガイド
url: /ja/net/programming-with-charts/add-pie-chart-labels-in-c-using-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# と Aspose.Words で円グラフラベルを追加する – 完全ガイド

Word 文書に **円グラフラベル** を追加したいですか？ Aspose.Words を使えば、**円グラフラベルの変更** や **円グラフのパーセンテージ表示** をファイル内で手軽に行えます—Word で手動調整する必要はありません。  

このチュートリアルでは、**パーセンテージラベルの表示**、位置の変更、さらには **動的データ用にチャート系列ラベルを更新** する手順を詳しく解説します。最後まで読めば、任意の .NET プロジェクトにすぐ組み込める再利用可能なスニペットが手に入ります。

> **クイックプレビュー:** 本ガイドに従って保存した `.docx` を開くと、各スライスにパーセンテージが表示された円グラフが見え、ラベルはスライスの外側に配置されているので読みやすさが最大化されています。

---

## 必要なもの

- **Aspose.Words for .NET**（2026 年時点の最新バージョン）。NuGet から取得できます: `Install-Package Aspose.Words`。
- すでに円グラフまたはドーナツグラフが埋め込まれている **Word 文書**（ここでは `Chart.docx` と呼びます）。
- **C#** と Visual Studio（またはお好みの IDE）に関する基本的な知識。

以上です—余計なライブラリや COM 相互運用は不要で、純粋なマネージドコードだけで完結します。

---

## 円グラフラベルの追加 – 完全実装

以下は **完全に実行可能な** C# コンソールプログラムです。文書を読み込み、最初の円グラフを変更し、結果を保存します。各行にコメントが付いているので、**何を** しているかだけでなく **なぜ** それを行うのかも理解できます。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartLabelDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the Word document that already contains a pie chart.
            //    Change the path to where your Chart.docx lives.
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart node in the document.
            //    The GetChild method walks the document tree and returns the first Node of type Chart.
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label collection of the first series.
            //    In a pie chart each series represents the whole pie; the collection holds the labels for each slice.
            ChartDataLabelCollection dataLabels = chart.Series[0].DataLabelCollection;

            // 4️⃣ Position the data labels **outside** the slices.
            //    This is the most readable layout for pie/doughnut charts.
            dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

            // 5️⃣ Turn on the percentage display.
            //    ShowPercentage automatically calculates and shows each slice’s contribution.
            dataLabels.ShowPercentage = true;

            // 6️⃣ (Optional) If you also want the actual values, enable ShowValue.
            //    dataLabels.ShowValue = true; // uncomment to display raw numbers.

            // 7️⃣ Save the modified document.
            //    The new file will contain the pie chart with custom labels.
            doc.Save(@"YOUR_DIRECTORY\ChartWithCustomLabels.docx");

            Console.WriteLine("Pie chart labels added successfully!");
        }
    }
}
```

### 期待される結果

`ChartWithCustomLabels.docx` を Microsoft Word で開きます。円グラフに **各スライスの外側にパーセンテージラベルが配置された状態** が表示されます。ラベルは「35 %」「20 %」といった形で、チャートが瞬時に把握できるようになります。

---

## 円グラフラベルの変更：位置と書式設定

パーセンテージを表示せずに **円グラフラベルだけを変更** したい場合は、`Position` プロパティを以下のいずれかに設定します。

| Position 列挙体 | 視覚効果 |
|------------------|----------|
| `InsideEnd`      | ラベルがスライス内部、端に配置されます。 |
| `Center`         | ラベルがスライスの中央に表示されます（小さな円グラフに適しています）。 |
| `OutsideEnd`     | ラベルがスライスの外側に配置され、リーダーラインで接続されます（デフォルト設定）。 |

```csharp
dataLabels.Position = ChartDataLabelPosition.Center; // example switch
```

**プロのコツ:** スライスが多数ある場合は `OutsideEnd` が最適です。テキストの重なりを防げます。

---

## 円グラフにパーセンテージラベルを表示する

`ShowPercentage` プロパティは **ブールフラグ** です。`true` に設定すると、Aspose.Words が基になるデータソースに基づいて各スライスの割合を計算し、ラベルに表示します。

```csharp
dataLabels.ShowPercentage = true; // Turns on the % display
```

生の数値 **と** パーセンテージの両方が必要な場合は、`ShowValue` と組み合わせて使用できます。

```csharp
dataLabels.ShowValue = true; // Shows the actual cell value next to the %
```

両方のフラグが有効なとき、ラベルは「45 % (120)」のように表示されます。

---

## 動的データ向けにチャート系列ラベルを更新する

月次売上やアンケート結果など、チャートを動的に生成するケースが多いでしょう。**チャート系列ラベルをプログラムで更新** するには、データラベルに手を加える前に `Series` コレクションを変更します。

```csharp
// Assume you have a second series you want to rename
chart.Series[1].Name = "Projected Growth";

// Refresh the data label collection after changes
ChartDataLabelCollection secondSeriesLabels = chart.Series[1].DataLabelCollection;
secondSeriesLabels.ShowPercentage = true;
secondSeriesLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

このスニペットは、最初の系列だけでなく **任意の系列** のラベルを更新する方法を示しています。実績と予測を組み合わせたレポートを作成する際に便利です。

---

## エッジケースとよくある落とし穴

| 状況 | 注意点 | 対策 |
|------|--------|------|
| **チャートが円グラフ/ドーナツグラフでない** | `Position` が視覚的に影響しないことがあります。 | `chart.Type` が `ChartType.Pie` または `ChartType.Doughnut` であることを確認してください。 |
| **チャートが見つからない** | `GetChild` が `null` を返す可能性があります。 | ガード句を追加（コード参照）し、適切なメッセージをログに出力します。 |
| **古い Word バージョン** | 一部のラベル機能が無視されることがあります。 | 完全サポートを保証するため、`.docx`（最新形式）で保存してください。 |
| **スライス数が多い** | `OutsideEnd` でもラベルが重なることがあります。 | スライス数を減らすか、チャートサイズを拡大してください。 |

---

## 完全動作サンプル（コピー＆ペースト）

以下は **そのままコピー** して新しいコンソールプロジェクトに貼り付けられる **全プログラム** です。`YOUR_DIRECTORY` を `Chart.docx` が格納されているフォルダーに置き換えるだけです。



## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには、ステップバイステップの解説と完全なコード例が含まれているので、API の追加機能をマスターしたり、独自プロジェクトで代替実装を検討したりする際に役立ちます。

- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Customize Single Chart Series In A Chart](/words/english/net/programming-with-charts/single-chart-series/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}