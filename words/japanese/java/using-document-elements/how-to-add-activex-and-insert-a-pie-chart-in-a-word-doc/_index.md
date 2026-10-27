---
category: general
date: 2026-08-17
description: Aspose.Words を使用して Word 文書に ActiveX コントロールを追加し、円グラフを挿入する方法。スライスを分割して
  DOCX として保存する手順を数ステップで解説。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert pie chart
- save as docx
- how to insert chart
- explode pie slice
language: ja
lastmod: 2026-08-17
og_description: ActiveX コントロールの追加、円グラフの挿入、スライスの分割、そして Aspose.Words を使用して DOCX に保存する方法
  – 完全ステップバイステップガイド
og_image_alt: Screenshot of a Word document showing an ActiveX button and a pie chart
  with an exploded slice
og_title: Word文書にActiveXを追加し、円グラフを挿入する方法
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to add ActiveX controls and insert a pie chart in a Word doc using
    Aspose.Words. Explode a slice and save as DOCX in a few steps.
  headline: How to add ActiveX and insert a pie chart in a Word doc
  type: TechArticle
tags:
- Aspose.Words
- ActiveX
- Chart
- DOCX
title: Word文書にActiveXを追加し、円グラフを挿入する方法
url: /ja/java/using-document-elements/how-to-add-activex-and-insert-a-pie-chart-in-a-word-doc/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 文書に ActiveX を追加し、円グラフを挿入する方法

Word 文書に **ActiveX を追加する方法** のコントロールとチャートを埋め込む必要がある場合、このチュートリアルでは完全な実行可能ソリューションを示します。Aspose.Words を使用すると、ActiveX CommandButton を配置し、円グラフを作成し、強調のためにスライスを飛び出させ、最後に **DOCX として保存** を数行の C# で行うことができます。

以下のセクションでは、必要なインポートすべて、完全なコードリスト、および各手順が重要である理由の説明を示します。最後まで読むと、プログラムで生成した任意の .docx ファイルに対して、インタラクティブなコントロールと視覚的データを統合できるようになります。

## 前提条件

開始する前に、以下が揃っていることを確認してください。

* .NET 6.0 以降（コードは .NET Framework 4.7+ でも動作します）
* Aspose.Words for .NET パッケージ（NuGet 経由で入手可能）
* Visual Studio 2022 や VS Code などの開発環境
* C# と Word オブジェクトモデルの基本的な知識

追加のサードパーティ製チャートライブラリは不要です — Aspose.Words が組み込みのチャート作成機能を提供します。

## Aspose.Words を使用した ActiveX コントロールの追加方法

ActiveX コントロールを使用すると、Word ファイルにインタラクティブな UI 要素を直接埋め込むことができます。このガイドでは、後で VBA コードに接続できる **CommandButton** を追加します。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a group shape to hold the ActiveX control
GroupShape groupShape = builder.InsertGroupShape();

// Step 3: Insert a rectangle shape, hide it, and attach it to the group
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
groupShape.AppendChild(rectangleShape);
rectangleShape.SetHidden(true);

// Step 4: Insert a plain‑text StructuredDocumentTag (optional placeholder)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");

// Step 5: Insert the CommandButton ActiveX control
Forms2OleControl commandButton = builder.InsertForms2OleControl();
commandButton.SetActiveXControlType(Forms2OleControlType.CommandButton);
commandButton.SetCaption("Click Me");

// The CommandButton now appears in the document and can be used in VBA macros.
```

**Why this works:**  
`InsertForms2OleControl` は OLE コンテナを作成し、Word UI が ActiveX コントロールとして認識します。コントロールタイプを `CommandButton` に設定し、キャプションを付与すると、ユーザーが Word でファイルを開いたときに標準的なボタンとして動作します。

## 円グラフの挿入とスライスの飛び出し

チャートは、文書を離れることなくデータを視覚化するのに便利です。以下の手順では、**チャートの挿入方法** を示し、特に最初のスライスが飛び出した **円グラフ** を作成します。

```csharp
// Step 6: Insert a pie chart (400 × 300 points)
Chart pieChart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);

// Populate the chart with sample data
pieChart.Series.Clear();
ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                          new[] { 12000, 15000, 9000, 13000 });

// Step 7: Explode the first slice for emphasis
series.SetExplode(0, true);

// Optional: Customize colors or labels here if needed
```

**Why explode the slice:**  
`SetExplode(0, true)` を呼び出すと、Aspose.Words は最初のデータポイントをオフセットし、閲覧者の目をそのセグメントに引きつけます。これはプレゼンテーションで重要な値を強調する一般的なテクニックです。

## DOCX として保存

ActiveX ボタンとチャートを追加した後、ドキュメントをディスクに永続化します。この手順では、標準メソッドを使用した **DOCX として保存** を示します。

```csharp
// Step 8: Save the document in DOCX format
document.Save("Output.docx", SaveFormat.Docx);
```

`Output.docx` ファイルには、インタラクティブなボタンと飛び出したスライスを持つ円グラフが含まれ、追加プラグインなしで Microsoft Word で開くことができます。

## 完全な実行可能サンプル

すべてをまとめると、以下はコンソールアプリケーションにコピーしてすぐに実行できる自己完結型プログラムです。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert group shape and hidden rectangle (required for ActiveX positioning)
        GroupShape group = builder.InsertGroupShape();
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        group.AppendChild(rect);
        rect.SetHidden(true);

        // Optional placeholder tag
        builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");

        // Insert CommandButton ActiveX control
        Forms2OleControl button = builder.InsertForms2OleControl();
        button.SetActiveXControlType(Forms2OleControlType.CommandButton);
        button.SetCaption("Click Me");

        // Insert pie chart and explode first slice
        Chart chart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);
        chart.Series.Clear();
        ChartSeries series = chart.Series.Add("Revenue", new[] { "Jan", "Feb", "Mar" },
                                               new[] { 5000, 7000, 3000 });
        series.SetExplode(0, true); // explode pie slice

        // Save the document
        doc.Save("Output.docx", SaveFormat.Docx);

        Console.WriteLine("Document created successfully: Output.docx");
    }
}
```

**Expected result:**  
`Output.docx` を Word で開くと、*Click Me* とラベル付けされたボタンと、最初のスライス（January）が他の部分からオフセットされた円グラフが表示されます。ボタンは VBA イベントハンドリングの準備ができており、チャートは Word の組み込みチャートツールで編集可能です。

## よくある質問とエッジケース

* **Can I add other ActiveX types?**  
  はい。`Forms2OleControlType.CommandButton` を `Forms2OleControlType` 列挙体の任意の値（例: `CheckBox`、`OptionButton`）に置き換えるだけで同じ挿入パターンが適用されます。

* **What if I need a different chart type?**  
  `InsertChart` 呼び出しで `ChartType.Bar`、`ChartType.Line` などを使用します。**チャートの挿入方法** の手順は同一で、列挙体の値だけが変わります。

* **How to control the size of the exploded slice?**  
  現在 Aspose.Words は二値の飛び出しフラグ（true/false）のみをサポートしています。より細かい制御（例: オフセット距離）を行うには、保存後に基になる OOXML を編集する必要があります。

* **Is the document compatible with older Word versions?**  
  DOCX として保存すれば Word 2007 以降と互換性があります。Word 2003 用に `SaveFormat.Doc` に変更することは可能ですが、その形式では ActiveX のサポートが制限されます。

* **Do I need to reference `System.Drawing`?**  
  いいえ。描画オブジェクトはすべて Aspose.Words が提供するため、必要な NuGet パッケージは `Aspose.Words` だけです。

## 結論

これで **ActiveX を追加する方法**、**円グラフの挿入**、**円スライスの飛び出し**、そして **DOCX として保存** を Aspose.Words for .NET を使って実現できるようになりました。完全なサンプルは、ドキュメント作成から最終保存までのすべての手順を網羅し、各 API 呼び出しの背後にある考え方を解説しています。

次に取り組むと良いテーマ:

* CommandButton のクリックに応答する VBA マクロの追加（**チャートの挿入方法** とデータ自動更新）
* 企業ブランディングに合わせたチャートの外観カスタマイズ（色、データ ラベルなど）
* **ComboBox** や **ListBox** など、リッチなフォームを実現する追加の ActiveX コントロールの埋め込み

コードを自由に試し、サンプルデータを置き換え、独自のドキュメント生成パイプラインに統合してください。コーディングを楽しんでください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックをカバーしています。各リソースには、完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Aspose.Words for .NET を使用して Word に列グラフを挿入する](/words/english/net/working-with-charts/insert-column-chart/)
- [Aspose.Words for .NET を使用して Word にシンプルな列グラフを挿入する](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Aspose.Words for .NET を使用して Word にバブルチャートを挿入する](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}