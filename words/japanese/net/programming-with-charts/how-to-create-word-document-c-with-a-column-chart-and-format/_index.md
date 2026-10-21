---
category: general
date: 2026-09-21
description: Aspose.Words を使用したステップバイステップガイドで、C# で Word 文書を作成し、縦棒グラフを挿入し、ラベル位置を設定し、値を表示する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to insert chart
- how to set label
- how to display values
- insert column chart word
language: ja
lastmod: 2026-09-21
og_description: Aspose.Words を使用して C# で Word 文書を作成します。このチュートリアルでは、縦棒グラフの挿入方法、ラベル位置の設定、値の表示方法を示します。
og_image_alt: Screenshot of a Word document created with C# that contains a column
  chart and data labels
og_title: C#でWord文書を作成 – 列グラフを挿入、ラベルを設定、値を表示
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  headline: How to create Word document C# with a column chart and formatted labels
  type: TechArticle
- description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  name: How to create Word document C# with a column chart and formatted labels
  steps:
  - name: Expected result
    text: When you open `output.docx`, you should see a single column chart similar
      to the image below. Each column has a numeric label at its top, inside the column,
      displaying the series value.
  - name: Adding custom data to the chart
    text: 'If you need to replace the placeholder data, you can modify the chart’s
      `Series` collection:'
  - name: Changing label font and color
    text: 'You can further customize the label appearance:'
  - name: Inserting multiple charts
    text: The `DocumentBuilder` can insert as many charts as you need. Just call `InsertChart`
      again after moving the cursor with `builder.Writeln()` or `builder.InsertParagraph()`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Charts
title: C#で列チャートと書式設定されたラベルを含むWord文書の作成方法
url: /ja/net/programming-with-charts/how-to-create-word-document-c-with-a-column-chart-and-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で列グラフと書式設定されたラベルを持つ Word 文書を作成する方法

**C# で Word 文書を作成**し、グラフを含めたい場合は、このガイドで手順をすべて解説します。列グラフの挿入方法、データラベルの位置設定、ラベルの値表示を Aspose.Words for .NET を使って行う方法を学べます。

以前は、グラフ付きの Word ファイルを作成するには Microsoft Word で手作業が必要でした。この **how to insert chart** 手順に従えば、コードだけでプロセス全体を自動化でき、レポート生成が高速かつ再現可能になります。チュートリアルでは **how to set label** のプロパティ設定や **how to display values** の方法もカバーしており、エンドユーザー向けにすぐ使えるグラフが作れます。

この記事を読み終えると、列ごとにデータラベルが内部に表示され、数値も示された `.docx` ファイルを生成する完全な C# プログラムが手に入ります。

## 前提条件

開始する前に以下を用意してください。

* .NET 6.0 SDK 以降がインストール済み  
* **Aspose.Words for .NET** のライセンス版（テスト用に無料トライアルでも可）  
* Visual Studio 2022 または Visual Studio Code などの IDE  

`Aspose.Words` 以外に追加で必要な NuGet パッケージはありません。

## 手順 1: プロジェクトの作成と Aspose.Words の追加

新しいコンソールプロジェクトを作成し、Aspose.Words パッケージを追加します。

```bash
dotnet new console -n WordChartDemo
cd WordChartDemo
dotnet add package Aspose.Words
```

`dotnet add package` コマンドは、**Aspose.Words** の最新安定版を取得します。このパッケージに **insert column chart word** サンプルで使用するチャート API が含まれています。

## 手順 2: 空の Word 文書を作成

最初のコードは空の文書と、コンテンツ挿入用の `DocumentBuilder` を作成します。これが **create word document C#** の土台です。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 2: Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` は `.docx` 全体を表し、`DocumentBuilder` は `InsertParagraph`、`InsertImage`、そして本チュートリアルの要となる `InsertChart` などのメソッドを提供します。

## 手順 3: 列グラフを挿入 (how to insert chart)

次に **column chart** を挿入します。`InsertChart` メソッドは、チャートの種類、幅、高さ（ポイント単位）を受け取ります。

```csharp
        // Step 3: Insert a column chart with a width of 400 pt and height of 300 pt.
        Chart chart = builder.InsertChart(ChartType.Column, 400, 300);
```

この時点でチャートにはプレースホルダー値が入ったデフォルトのデータ系列が作成されます。カスタム数値に置き換えることも可能ですが、**how to set label** と **how to display values** を示すだけならデフォルトで十分です。

## 手順 4: データラベルを各列の内部に配置 (how to set label)

データラベルは各列に表示されるテキストです。読みやすさ向上のため、ラベルを列の内部に移動し、数値を表示させます。

```csharp
        // Step 4: Access the first data label of the first series.
        ChartDataLabel label = chart.DataLabels[0];

        // Position the label at the inside end of the column.
        label.Position = ChartDataLabelPosition.InsideEnd;

        // Show the numeric value of each data point.
        label.ShowValue = true;
```

`ChartDataLabelPosition.InsideEnd` はラベルを列の上端に配置しますが、形状の内部に留まります。これはレポートでよく使われるビジュアルスタイルです。`ShowValue` を `true` に設定することで **how to display values** の要件を満たします。

## 手順 5: 文書を保存

最後に文書をディスクに書き出します。生成されたファイルは Microsoft Word、LibreOffice、または Open XML 形式に対応した任意のビューアで開くことができます。

```csharp
        // Step 5: Save the document to the output folder.
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

プログラムを実行すると、`output.docx` が作成され、列内部にデータラベルが配置され、数値が表示された列グラフが含まれます。

### 期待される結果

`output.docx` を開くと、以下の画像のような単一の列グラフが表示されます。各列の上部（列内部）に数値ラベルがあり、系列の値が示されています。

![Chart in a Word document created with C#](/images/word-chart-example.png "Chart in a Word document created with C# – create word document C#")

*Alt text:* *C# で作成した Word 文書内のチャートで、列グラフの挿入と値表示を示しています。*

## よくあるバリエーションとエッジケース

### カスタムデータをチャートに追加

プレースホルダー データを置き換える必要がある場合は、チャートの `Series` コレクションを操作します。

```csharp
// Replace the default series with custom values.
chart.Series.Clear();
ChartSeries series = chart.Series.Add(ChartType.Column);
series.Name = "Sales Q1";
series.AddCategory("Jan", 120);
series.AddCategory("Feb", 150);
series.AddCategory("Mar", 180);
```

### ラベルのフォントと色を変更

ラベルの外観をさらにカスタマイズできます。

```csharp
label.Font.Name = "Arial";
label.Font.Size = 10;
label.Font.Color = System.Drawing.Color.DarkBlue;
```

### 複数のチャートを挿入

`DocumentBuilder` は必要なだけチャートを挿入できます。`builder.Writeln()` や `builder.InsertParagraph()` でカーソルを移動した後、再度 `InsertChart` を呼び出すだけです。

## プロのコツ

* **Pro tip:** `chart.HasTitle = true` と `chart.Title.Text` を設定して、チャートに説明的なタイトルを付けましょう。スクリーンリーダーのアクセシビリティが向上します。  
* **Watch out for:** ネットワーク共有に保存する場合、アプリケーションに書き込み権限があることを確認してください。権限がないと `doc.Save` が `UnauthorizedAccessException` をスローします。  
* **Performance tip:** 複数の挿入を行う場合は、`DocumentBuilder` のインスタンスを再利用しましょう。毎回新しいビルダーを作成すると不要なオーバーヘッドが発生します。

## 結論

これで **create Word document C#** の方法、**insert chart** の要素、**set label** の位置設定、そして各列内部への **display values** の実装がマスターできました。上記の完全なコード例はすぐに実行可能で、カスタムデータやスタイリング、追加チャートなどに拡張できます。

次は **how to insert picture**、**how to generate tables**、**how to apply document themes** などの関連トピックを探求し、レポートをさらにリッチに自動化しましょう。コーディングを楽しんでください！

## 次に学ぶべきこと

このガイドで示したテクニックを応用できる、密接に関連したチュートリアルを以下にまとめました。各リソースは完全な動作コードとステップバイステップの解説を含んでおり、API の追加機能習得や独自実装の検討に役立ちます。

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}