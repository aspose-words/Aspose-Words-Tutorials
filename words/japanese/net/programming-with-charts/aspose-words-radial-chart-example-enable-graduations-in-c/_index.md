---
category: general
date: 2026-10-13
description: C# と Aspose.Words 24.9+ を使用して、放射状チャートで目盛りを有効にする方法を示す Aspose.Words の放射状チャート例。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words radial chart example
- Aspose.Words chart API
- C# radial chart
- graduations visibility
- Aspose.Words version 24.9
- chart manipulation in .NET
language: ja
lastmod: 2026-10-13
og_description: C# と最新の 24.9+ ライブラリを使用して、放射状チャートで目盛りを有効にする方法を示す Aspose.Words の放射状チャート例。
og_image_alt: Aspose.Words radial chart example displaying graduations
og_title: Aspose.Words ラジアルチャートの例 – C#で目盛りを有効にする
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  headline: 'Aspose.Words radial chart example: enable graduations in C#'
  type: TechArticle
- description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  name: 'Aspose.Words radial chart example: enable graduations in C#'
  steps:
  - name: Load the document that contains a radial chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: Retrieve the first chart shape from the document
    text: '```csharp // NodeType.Shape selects shapes; the third argument (true) searches
      the whole tree. Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
      if (chart == null) { throw new InvalidOperationException("No chart shape found
      in the document."); } ```'
  - name: Enable graduations on the radial chart
    text: '```csharp // This property is available starting with Aspose.Words 24.9.
      chart.RadialChart.IsGraduationsVisible = true; ```'
  - name: Save the modified document
    text: '```csharp string outputPath = Path.Combine(Environment.CurrentDirectory,
      "RadialChart_Graduations.docx"); doc.Save(outputPath); Console.WriteLine($"Document
      saved to {outputPath}"); ```'
  - name: Expected output
    text: When you open `RadialChart_Graduations.docx` in Word, the radial chart will
      display tick marks (graduations) around the circular axis, similar to the screenshot
      shown earlier. The rest of the chart (data series, legend, title) remains unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Charts
title: 'Aspose.Words ラジアルチャートの例: C#で目盛りを有効にする'
url: /ja/net/programming-with-charts/aspose-words-radial-chart-example-enable-graduations-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ラジアルチャート例: C# で目盛りを有効にする

**aspose.words radial chart example** をお探しなら、ここが正しい場所です。このチュートリアルでは、Aspose.Words for .NET API を使用してラジアルチャートの目盛り (graduations) を有効にする手順を詳しく解説します。

ラジアルチャートは、時間帯別のメトリクスや季節的なトレンドなど、循環データの可視化に便利です。デフォルトでは円形軸周囲の目盛りが非表示になっているため、チャートが読みづらくなることがあります。目盛りを有効にするのはワンラインの変更ですが、正しいオブジェクトモデルと機能をサポートするバージョンを把握している必要があります。

このガイドで学べること：

* 既にラジアルチャートが含まれている Word 文書を読み込む方法  
* Aspose.Words のチャート API を介してチャート シェイプにアクセスする方法  
* **目盛りの表示** をオンにする方法（**Aspose.Words バージョン 24.9** 以降で利用可能）  
* 変更後の文書を保存し、結果を確認する方法  

完全な実行可能コードが含まれているので、コピーして新しいコンソール プロジェクトに貼り付ければすぐに効果を確認できます。

![Aspose.Words ラジアルチャート例（目盛りあり）](https://example.com/images/radial-chart-graduations.png "Aspose.Words ラジアルチャート例（目盛りが有効化された状態）")

## 前提条件

開始する前に、以下を確認してください。

| 要件 | 重要な理由 |
|------|------------|
| .NET 6.0 以降 | Aspose.Words for .NET 24.9+ は .NET Standard 2.0 を対象とし、.NET 6+ で動作します。 |
| Aspose.Words for .NET **24.9** 以上 | `IsGraduationsVisible` プロパティはバージョン 24.9 で導入されました。古いリリースでは `MissingMemberException` がスローされます。 |
| ラジアルチャートを含む Word 文書（`RadialChart.docx`） | 本例は既存のチャートを操作します。ゼロから作成する方法は別トピックです。 |
| C# IDE（Visual Studio、Rider、VS Code） | .NET プロジェクトをコンパイルできる任意の IDE で構いません。 |
| NuGet パッケージ `Aspose.Words` | `dotnet add package Aspose.Words --version 24.9.0`（またはそれ以降）でインストールします。 |

> **プロのコツ:** 24.9 にアップグレードできない場合でも、他のチャート プロパティは変更可能ですが、目盛りは非表示のままです。これは API がそのフラグを公開していないためです。

## Aspose.Words ラジアルチャート例 – ステップバイステップ ガイド

以下のセクションでは、プロセスを個別のステップに分割して解説します。各ステップには必要なコードと、*なぜ* そのステップが必要かの簡単な説明が含まれています。

### ステップ 1: ラジアルチャートを含む文書を読み込む

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// The file path can be absolute or relative to the executable directory.
string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");

// Load the Word document. Aspose.Words parses the entire file into a DOM tree.
Document doc = new Document(sourcePath);
```

**重要な理由:**  
`Document` は **Aspose.Words チャート API** のエントリーポイントです。DOCX ファイルをメモリにロードし、段落・テーブル・チャート シェイプなどすべてのノードにアクセスできるようにします。ファイルが見つからない場合、`Document` は `FileNotFoundException` をスローするため、実運用コードでは例外処理が必要です。

### ステップ 2: 文書から最初のチャート シェイプを取得する

```csharp
// NodeType.Shape selects shapes; the third argument (true) searches the whole tree.
Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    throw new InvalidOperationException("No chart shape found in the document.");
}
```

**重要な理由:**  
チャートは `Shape` ノードとして格納されています。`GetChild` メソッドに `NodeType.Shape` を指定すると DOM を走査し、最初に一致したシェイプを返します。`Chart` へキャストすることで `RadialChart` などチャート固有のプロパティにアクセスできます。null チェックは、テンプレート再利用時に文書にチャートが含まれていないという一般的なエッジケースに対する明確なエラーメッセージを提供します。

### ステップ 3: ラジアルチャートの目盛りを有効にする

```csharp
// This property is available starting with Aspose.Words 24.9.
chart.RadialChart.IsGraduationsVisible = true;
```

**重要な理由:**  
`IsGraduationsVisible` は円形軸周囲の目盛りを制御します。`true` に設定すると目盛りが描画され、数値を正確に把握したい閲覧者にとって可読性が向上します。このプロパティは `RadialChart` の下にあり、`Chart` のサブタイプです。バー チャートなど非ラジアルチャートに対して使用すると `RadialChart` プロパティは `null` になるため、複雑なシナリオではチャート種別の確認が必要です。

#### 非ラジアルチャートの取り扱い（オプション）

```csharp
if (chart.ChartType == ChartType.Radial)
{
    chart.RadialChart.IsGraduationsVisible = true;
}
else
{
    Console.WriteLine("The chart is not radial; graduations are not applicable.");
}
```

このガードを入れることで、ソース文書に異なるチャート種別が混在している場合でもコードが堅牢になります。

### ステップ 4: 変更後の文書を保存する

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**重要な理由:**  
`Save` を呼び出すことで、メモリ上の DOM が .docx ファイルに書き出され、チャートへの変更が永続化されます。出力ファイルは Microsoft Word、LibreOffice、または DOCX をサポートする任意のビューアで開くことができ、目盛りが表示されたラジアルチャートが確認できます。

## 完全な実行可能サンプル

以下は .NET コンソール プロジェクトの `Program.cs` に貼り付けて使用できる、全コードです。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1. Load the source document that contains a radial chart.
        // -----------------------------------------------------------------
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");
        Document doc = new Document(sourcePath);

        // -----------------------------------------------------------------
        // 2. Locate the first chart shape in the document.
        // -----------------------------------------------------------------
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // -----------------------------------------------------------------
        // 3. Enable graduations (tick marks) on the radial chart.
        // -----------------------------------------------------------------
        // Ensure the chart is radial before accessing RadialChart.
        if (chart.ChartType == ChartType.Radial && chart.RadialChart != null)
        {
            chart.RadialChart.IsGraduationsVisible = true;
        }
        else
        {
            Console.WriteLine("The chart is not a radial chart; cannot set graduations.");
            return;
        }

        // -----------------------------------------------------------------
        // 4. Save the updated document.
        // -----------------------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Radial chart with graduations saved to: {outputPath}");
    }
}
```

### 期待される結果

`RadialChart_Graduations.docx` を Word で開くと、円形軸周囲に目盛り（graduations）が表示されたラジアルチャートが確認でき、先ほどのスクリーンショットと同様の外観になります。データ系列、凡例、タイトルなど他の要素は変更されません。

## 一般的なバリエーションとエッジケース

| 状況 | 解決策 |
|------|--------|
| **古い Aspose.Words バージョン (< 24.9)** | 最新の NuGet パッケージにアップグレードしてください。`IsGraduationsVisible` プロパティは以前のリリースには存在しません。 |
| **同一文書に複数のチャートがある** | `doc.GetChild(NodeType.Shape, index, true)` で適切な `index` を指定するか、`doc.GetChildNodes(NodeType.Shape, true)` を列挙し `ChartType.Radial` でフィルタリングします。 |
| **プログラムでチャートを作成する場合** | `DocumentBuilder` を使用してチャートを挿入し、その後 `RadialChart.IsGraduationsVisible` を設定します。 |

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、独自プロジェクトで代替実装を検討したりする際に役立ちます。

- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Remove a Chart Series from a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/remove-chart-series/)
- [Hide Plot Area Border in a Column Chart with Aspose.Words for .NET](/words/english/net/programming-with-charts/hide-plot-border/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}