---
category: general
date: 2026-09-05
description: C# を使用して Word にレーダーチャートを作成します。空白の Word 文書を生成し、レーダーチャートを追加し、チャートのサイズを設定し、目盛りをすばやく有効にする方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radar chart
- add chart to word
- add radar chart
- generate blank word document
- set chart size word
language: ja
lastmod: 2026-09-05
og_description: C# を使用して Word にレーダーチャートを作成する。このガイドでは、空白の Word 文書を生成し、レーダーチャートを追加し、チャートのサイズを設定し、目盛りを有効にする方法を数分で紹介します。
og_image_alt: Screenshot of a Word document with a created radar chart
og_title: Wordでレーダーチャートを作成する – ステップバイステップ C# ガイド
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create radar chart in Word using C#. Learn to generate a blank Word
    document, add a radar chart, set chart size, and enable tick marks quickly.
  headline: How to create radar chart and add chart to Word with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Chart
- Word automation
title: C#でレーダーチャートを作成し、Wordにチャートを追加する方法
url: /ja/net/programming-with-charts/how-to-create-radar-chart-and-add-chart-to-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#でレーダーチャートを作成し、Wordにチャートを追加する方法

Word ファイル内に **レーダーチャートを作成** したい場合は、このガイドが全工程を案内します。**空白の Word ドキュメントを生成**し、レーダーチャートを挿入し、**チャートのサイズを Word で設定**し、軸の目盛りを有効化する方法を数行の C# コードで学びます。

レポートに視覚的データを追加するのは一般的な要件であり、Aspose.Words を使用すれば簡単に実現できます。以下の手順では **Word にチャートを追加** する方法もカバーしているので、ダッシュボードや財務サマリー、その他データ駆動型コンテンツを自動化できます。

## 前提条件

開始する前に以下を確認してください。

* .NET 6.0 以降がインストール済み  
* Aspose.Words for .NET のライセンス（または無料トライアル） – 本チュートリアルで使用する `Document`、`DocumentBuilder`、チャート API が含まれます  
* Visual Studio 2022（または任意の C# IDE）  

> **プロのコツ:** テスト時は Aspose.Words の DLL をプロジェクトの `bin` フォルダーに配置し、NuGet (`Install-Package Aspose.Words`) で参照してください。

## Word ドキュメントでレーダーチャートを作成する方法

最初のステップは **空白の Word ドキュメントを生成** し、チャートのホストとなるキャンバスを用意することです。これにより、コンテンツを追加する前にドキュメントのメタデータを制御できます。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// 1️⃣ Create an empty Word document
Document document = new Document();   // this is a blank .docx file
```

*Why this matters:* 空の `Document` オブジェクトは、隠れたスタイルやセクションがチャートのレイアウトに干渉しないことを保証します。また、後で必要に応じてドキュメントプロパティ（author、title など）を設定できる利点もあります。

## Aspose.Words を使用して Word にチャートを追加する方法

次に `DocumentBuilder` を作成します。ビルダーはテキスト、画像、チャートをドキュメントに挿入できる中心的なオブジェクトです。

```csharp
// 2️⃣ Initialize a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

これでカーソル位置に直接 **レーダーチャートを追加** できます。`InsertChart` メソッドは `ChartType` 列挙体、幅、そして高さ（ポイント単位）を受け取ります。

```csharp
// 3️⃣ Insert a radar (radial) chart with a specific size
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

*Why 400 × 300?* このサイズは標準的な A4 ページ上で見やすいチャートを提供します。レイアウトに合わせて別のアスペクト比が必要な場合は、後述の **チャートのサイズを Word で設定** 手順で調整できます。

## Word でチャートのサイズを設定する

挿入後にサイズを微調整したい場合は、チャートの `Width` と `Height` プロパティを変更します。周囲のテキストやページ余白に合わせて視覚的バランスを取る際に便利です。

```csharp
// 4️⃣ Adjust chart dimensions (optional)
// radarChart.Width = 500;   // width in points
// radarChart.Height = 350;  // height in points
```

> **Note:** `InsertChart` のオーバーロードですでにサイズが設定されているため、上記コードは任意であり、完全性のために示しています。

## 放射軸に目盛りを有効化する

レーダーチャートは、放射軸に明確な目盛りが表示されていると最も有用です。以下の設定で目盛りをオンにし、間隔を 30 度に設定します。これは一般的なコンパス式レーダー表示に合わせたものです。

```csharp
// 5️⃣ Turn on graduations (tick marks) and set interval
radarChart.AxisX.HasGraduations = true;      // show tick marks
radarChart.AxisX.GraduationInterval = 30;   // every 30 degrees
```

*Why this matters:* 目盛りがあることで、各角度での値を読者が把握しやすくなり、データに不慣れなステークホルダーに対しても可読性が向上します。

## チャートを含むドキュメントを保存する

最後に、ドキュメントをディスクに書き出します。好きなフォルダーを指定してください。ただし、パスが存在することを確認してください。

```csharp
// 6️⃣ Save the Word file
document.Save(@"C:\Temp\RadialChart.docx");
```

`RadialChart.docx` を Microsoft Word で開くと、ページ中央に指定サイズで描画されたレーダーチャートが表示され、30 度ごとに目盛りが付いていることが確認できます。

### 期待される出力

* **RadialChart.docx** という名前の `.docx` ファイル  
* 1 ページ目にサイズ 400 × 300 ポイントのレーダーチャートが配置  
* X 軸（放射軸）に 0°、30°、60°、…、330° の目盛りが表示  

この後、`radarChart.Series` にアクセスしてプレースホルダーのデータ系列を独自の値に置き換えることができますが、これは基本的な **add radar chart** チュートリアルの範囲外です。

## よくあるバリエーションとエッジケース

| シナリオ | 調整 |
|----------|------|
| **別のチャートタイプ** | `ChartType.Radar` を `ChartType.Column`、`ChartType.Pie` などに置き換える |
| **複数チャート** | `InsertChart` を繰り返し呼び出す。各呼び出しは前のチャートの後に新しいチャートを配置 |
| **大量データ** | `radarChart.Series[0].DataPoints.AddDataPointForBarSeries(value)` を使用して多数のデータポイントを追加 |
| **PDF として保存** | チャート追加後に `document.Save("RadialChart.pdf", SaveFormat.Pdf);` を呼び出す |
| **.NET Core 上で実行** | `Aspose.Words.NETCore` パッケージを参照。API の使用方法は同一 |

## 完全な実行可能サンプル

以下はコンソール アプリケーションにコピーペーストできる完全プログラムです。すべての手順、オプションのサイズ調整、コメントが含まれています。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace RadarChartDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Generate a blank Word document
            Document document = new Document();

            // 2️⃣ Create a builder to work with the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3️⃣ Insert a radar chart (400 × 300 points)
            Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

            // 4️⃣ (Optional) Change chart size if needed
            // radarChart.Width = 500;
            // radarChart.Height = 350;

            // 5️⃣ Enable tick marks on the radial axis
            radarChart.AxisX.HasGraduations = true;          // show tick marks
            radarChart.AxisX.GraduationInterval = 30;       // every 30 degrees

            // 6️⃣ Populate the chart with sample data (optional)
            radarChart.Series[0].DataPoints.Clear();
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(10);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(20);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(30);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(40);

            // 7️⃣ Save the document
            string outputPath = @"C:\Temp\RadialChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

プログラムを実行し、生成されたファイルを開くと、説明通りのレーダーチャートが確認できます。

## 結論

これで C# を使って **レーダーチャートを作成** し、**Word にチャートを追加** する方法が分かりました。チュートリアルでは **空白の Word ドキュメントを生成**、レーダーチャートの挿入、**チャートのサイズを Word で設定**、軸の目盛り有効化を取り上げました。この基礎をもとに、複数チャートやカスタムデータ系列、PDF へのエクスポートなどへ拡張できます。

### 次のステップ

* `ChartType`（例: `Bar`、`Line`）を使った他のチャートタイプを探索 – **add radar chart** キーワードに関連する例を参照  

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、独自プロジェクトで代替実装アプローチを検討したりするのに役立ちます。

- [Insert Scatter Chart in Word Document](/words/english/net/programming-with-charts/insert-scatter-chart/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}