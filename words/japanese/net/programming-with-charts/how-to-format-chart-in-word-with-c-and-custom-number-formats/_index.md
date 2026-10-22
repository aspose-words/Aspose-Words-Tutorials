---
category: general
date: 2026-10-13
description: C# を使用して Word のチャートの軸に通貨などのカスタム数値書式を適用し、チャートをフォーマットする方法。ステップバイステップのコード例を含む。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format chart
- apply custom number format
- custom number format word
- how to set chart
- change chart axis format
language: ja
lastmod: 2026-10-13
og_description: C# を使用して Word のグラフをフォーマットする方法では、グラフ軸にカスタム数値書式を適用でき、値を通貨やパーセンテージ、または必要な任意のパターンで表示させることができます。ステップバイステップのガイドに従ってください。
og_image_alt: Word chart showing axis values formatted as currency after applying
  custom number format
og_title: C#でWordのチャートをフォーマットする方法 – カスタム数値形式
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to format chart in Word with C# by applying a custom number format,
    such as currency, to chart axes. Step‑by‑step code example included.
  headline: How to format chart in Word with C# and custom number formats
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart formatting
title: C# とカスタム数値書式で Word のチャートをフォーマットする方法
url: /ja/net/programming-with-charts/how-to-format-chart-in-word-with-c-and-custom-number-formats/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# とカスタム数値書式で Word のチャートをフォーマットする方法

C# で Word のチャートをフォーマットすることは、データをプロフェッショナルに提示する必要があるときに一般的な要件です。このガイドでは、**Aspose.Words for .NET** を使用してチャートの軸にカスタム数値書式を適用し、値が期待通りに表示される方法を示します。

DOCX ファイルの読み込み、最初のチャートの取得、現在の書式の読み取り、そして通貨のように小数点以下 2 桁の新しいパターンを設定する方法を学びます。また、追加の系列に対してチャート軸の書式を変更する方法や、必要に応じて書式をリセットする方法もカバーしています。

## 前提条件

* .NET 6.0 以降がインストールされていること  
* Visual Studio 2022（または .NET をサポートする任意の IDE）プロジェクト  
* **Aspose.Words for .NET** NuGet パッケージ (`Aspose.Words`)  
* 少なくとも 1 つのチャートが含まれる Word ドキュメント（`input.docx`）

以下のコマンドでパッケージを追加できます:

```bash
dotnet add package Aspose.Words
```

## Aspose.Words を使用して Word のチャートをフォーマットする方法

以下の完全なプログラムは、**チャート** の軸値をフォーマットするために必要なすべての手順を示しています。ファイルを `Program.cs` として保存し、コマンドラインまたは IDE から実行してください。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Load the Word document that contains the chart
        Document doc = new Document("input.docx");

        // Step 2: Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Step 3: Access the X‑value collection of the first data series
        ChartXValueCollection xValues = chart.ChartData.Series[0].XValues;

        // Optional: Show the current number format code
        Console.WriteLine($"Current format code: {xValues.FormatCode}");

        // Step 4: Apply a custom number format (currency with two decimals)
        // The format string follows Excel/Word conventions.
        xValues.FormatCode = "\"$\"#,##0.00";

        // Step 5: Save the modified document
        doc.Save("output_formatted.docx");
        Console.WriteLine("Chart axis format applied and document saved as output_formatted.docx");
    }
}
```

### 各ステップの説明

| ステップ | なぜ重要か | キーコード |
|------|----------------|----------|
| **ドキュメントの読み込み** | Word ファイルを操作するには `Document` オブジェクトが必要です。 | `new Document("input.docx")` |
| **チャートの取得** | `Chart` オブジェクトは `Shape` ノードとして格納されており、キャストすることでチャート固有の API を使用できます。 | `(Chart)doc.GetChild(NodeType.Shape, 0, true)` |
| **X 値へのアクセス** | 軸の書式設定はデータ系列の値コレクションに適用されます。 | `chart.ChartData.Series[0].XValues` |
| **現在の書式の読み取り** | 既存の `FormatCode` を把握することで、置換するか拡張するかを判断できます。 | `xValues.FormatCode` |
| **カスタム書式の設定** | `FormatCode` プロパティは任意の Excel 互換パターンを受け入れ、通貨、パーセンテージ、日付などを設定できます。 | `xValues.FormatCode = "\"$\"#,##0.00"` |
| **ドキュメントの保存** | 変更を永続化すると、新しい軸書式が DOCX ファイルに書き込まれます。 | `doc.Save("output_formatted.docx")` |

プログラムを実行すると `output_formatted.docx` が生成されます。Word で開くと、チャートの X 軸の値が単なる数値ではなく **$1,234.00**、**$2,345.00**、… のように表示されます。

## カスタム数値書式をチャート軸に適用する

Y 軸や追加の系列に **カスタム数値書式を適用** する必要がある場合、手順は同じです—対象となるコレクションを変更するだけです：

```csharp
// Apply format to Y‑values of the second series
ChartYValueCollection yValues = chart.ChartData.Series[1].YValues;
yValues.FormatCode = "0%"; // percentage format
```

> **プロのコツ:** 書式文字列内でリテラル文字を埋め込むには二重引用符を使用します（例: 通貨の場合は `"$"`）。上記のように引用符をエスケープしてください。

## カスタム数値書式と Word のロケールの扱い

Word は数値書式を解釈する際にドキュメントのロケールを尊重します。ドキュメントが米国以外のロケールを使用している場合、書式文字列を調整する必要があるかもしれません：

```csharp
// German locale – uses comma as decimal separator
xValues.FormatCode = "\"€\" #.##0,00";
```

ドイツ語設定のドキュメントで書式をテストすると、値が **€ 1.234,00** のように表示されることが確認できます。

## プログラムでチャートのプロパティを設定する方法

軸の書式設定に加えて、**チャート** のタイトル、凡例、データ ラベルを設定したくなることがよくあります。以下は、軸をフォーマットした後にチャートタイトルを設定する簡単なコードスニペットです。

```csharp
chart.Title.Text = "Sales by Quarter";
chart.Title.IsVisible = true;
```

これをカスタム数値書式と組み合わせることで、レポート作成に適した完全に仕上げられたチャートが得られます。

## ユーザー入力に基づいてチャート軸の書式を動的に変更する

実際のアプリケーションでは、ユーザーが実行時に書式を選択できるようにすることがあります。以下のメソッドは書式設定ロジックをカプセル化しています：

```csharp
static void SetAxisFormat(Chart chart, int seriesIndex, string formatCode)
{
    var xVals = chart.ChartData.Series[seriesIndex].XValues;
    xVals.FormatCode = formatCode;
}
```

`SetAxisFormat(chart, 0, "\"$\"#,##0.00")` を通貨用に、`SetAxisFormat(chart, 0, "0%")` をパーセンテージ用に呼び出すことができます。このアプローチにより、メインコードをすっきり保ち、将来的な拡張をサポートします。

## エッジケースと一般的な落とし穴

| 状況 | 注意点 | 推奨される対策 |
|-----------|-------------------|---------------|
| ドキュメントに **チャートが含まれていない** | `GetChild` が `null` を返し、キャスト例外が発生します。 | `null` かどうかを確認してからキャストしてください（例参照）。 |
| 同一ドキュメントに複数のチャートがある場合 | コードは常に最初のチャート（インデックス 0）を取得します。 | `doc.GetChildNodes(NodeType.Shape, true)` をループし、`ShapeType.Chart` でフィルタリングしてください。 |
| 系列に **X 値がない**（例: 円グラフ） | `XValues` にアクセスすると `ArgumentOutOfRangeException` がスローされる可能性があります。 | 書式設定前に `Series[i].XValues` が空でないことを確認してください。 |
| ロケールの不一致 | 通貨記号が正しく表示されない可能性があります。 | 適切なロケール記号を使用して `xValues.FormatCode` を明示的に設定してください。 |

## 期待される出力

サンプルプログラムを実行した後、**output_formatted.docx** を開きます。チャートの X 軸は選択したカスタム書式で数値を表示するはずです。通貨の例では、軸ラベルは次のようになります:

```
$1,000.00
$2,000.00
$3,000.00
```

Y 値にパーセンテージ書式を適用した場合、Y 軸のラベルは次のようになります:

```
10%
20%
30%
```

## 結論

このチュートリアルでは、C# を使用して Word のチャートを **フォーマット** し、軸の値に **カスタム数値書式を適用** する方法を示しました。これにより、通貨、パーセンテージ、その他任意の数値パターンを設定する再利用可能なパターンが得られ、ロケールの扱い、複数系列、動的なユーザー入力への対応方法も理解できました。

次に、`ChartRenderer` を使用して **チャート** のタイトルやデータ ラベルを設定したり、チャートを画像としてエクスポートしたりする方法を探求するとよいでしょう。これらのトピックは本稿で扱った概念に直接基づいており、完全に自動化されたレポート ソリューションの作成に役立ちます。

---

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法に基づく密接に関連したトピックをカバーしています。各リソースには、ステップバイステップの解説付きの完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [チャートの軸の数値書式](/words/english/net/programming-with-charts/number-format-for-axis/)
- [チャートのデータ ラベルの数値書式設定](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Aspose.Words for .NET を使用した Word ラインチャートの副 X 軸の書式設定と表示単位を千単位に設定](/words/english/net/programming-with-charts/format-secondary-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}