---
category: general
date: 2026-10-10
description: 段落をフランス語に翻訳し、チャートのデータラベルの変更方法、データラベルのカスタマイズ方法、そして Aspose.Words AI を使用して編集した
  docx ファイルを保存する方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate paragraph to french
- how to change chart data label
- how to translate word document with ai
- customize chart data label
- how to save edited docx file
language: ja
lastmod: 2026-10-10
og_description: 段落をフランス語に翻訳し、Aspose.Words AI を使用してチャートのデータラベルを変更する方法、チャートのデータラベルをカスタマイズする方法、編集した
  docx ファイルを保存する方法を学びましょう。
og_image_alt: Screenshot of a Word document showing a French paragraph and a chart
  with a customized data label
og_title: 段落をフランス語に翻訳し、Wordでチャートラベルを変更する
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Translate paragraph to French and learn how to change chart data label,
    customize chart data label, and save edited docx file using Aspose.Words AI.
  headline: Translate paragraph to French and change chart label in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- AI translation
- chart customization
title: 段落をフランス語に翻訳し、Wordでチャートラベルを変更する
url: /ja/net/ai-powered-document-processing/translate-paragraph-to-french-and-change-chart-label-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 段落をフランス語に翻訳し、Word のチャート ラベルを変更する

同じ Word 文書内で **段落をフランス語に翻訳** しながらチャートを更新したい場合、本ガイドが手順をすべて示します。Aspose.Words AI を使用すればテキストを自動翻訳し、チャートのデータ ラベルを変更し、編集した `.docx` ファイルを保存するまでを数ステップで実行できます。

このチュートリアルでは、ソース ファイルの読み込みから変更の永続化までを網羅しています。最後まで実行すれば、任意の段落を翻訳し、チャート データ ラベルをカスタマイズした新しい Word ファイルを作成できるようになります。外部スクリプトは不要で、すべての処理が単一の C# プログラム内に収まります。

## 前提条件

- .NET 6.0 以降（.NET Framework 4.7+ でも動作します）
- Aspose.Words for .NET のライセンス（または無料評価キー）
- Google AI 翻訳器へのインターネット接続（`Translator` クラスは内部で Google の API を使用します）
- 少なくとも 1 つの段落と 1 つのチャートを含む Word 文書（`input.docx`）

## 手順 1: プロジェクトの設定と名前空間のインポート

新しいコンソール アプリケーションを作成し、Aspose.Words NuGet パッケージを追加します：

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

次に、`Program.cs` の先頭に必要な名前空間を追加します：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;          // AI translation helpers
using Aspose.Words.Drawing;    // Chart manipulation classes
using Aspose.Words.Tables;     // For accessing chart series and labels
```

これらのインポートにより、ドキュメントの読み込み、AI 翻訳、チャート編集機能が利用可能になります。

## 手順 2: ソースの Word 文書を読み込む

```csharp
// Path to the original file – adjust as needed
string inputPath = @"YOUR_DIRECTORY/input.docx";

// Load the document into memory
Document document = new Document(inputPath);
Console.WriteLine("Document loaded successfully.");
```

ファイルを読み込むと、ディスク上の元ファイルに手を加えることなく、メモリ上でクエリや変更ができる表現が生成されます。

## 手順 3: 最初の段落をフランス語に翻訳する

最初の段落はタイトルや導入文であることが多く、翻訳対象として最適です。`Translator` クラスは Google の AI モデルへの呼び出しを抽象化します。

```csharp
// Retrieve the first paragraph in the first section
Paragraph paragraph = document.FirstSection.Body.FirstParagraph;

// Extract the raw text (including trailing paragraph mark)
string originalText = paragraph.GetText();

// Translate the text to French
string translatedText = Translator.Translate(originalText, Language.French);
Console.WriteLine($"Original: {originalText.Trim()}");
Console.WriteLine($"Translated: {translatedText.Trim()}");

// Replace the paragraph's runs with the translated text
paragraph.Runs.Clear();                     // Remove existing runs
paragraph.AppendChild(new Run(document, translatedText)); // Insert new run
```

**なぜこれが機能するのか：**  
`paragraph.Runs.Clear()` は既存のテキスト ランをすべて削除し、新しい翻訳が古い内容と連結しないようにします。`new Run(document, translatedText)` は段落の書式設定を継承した新しいランを作成します。

## 手順 4: 最初のチャートを見つけてデータ ラベルをカスタマイズする

チャートは `NodeType.Shape` 型の `Shape` ノードとして格納されています。最初のチャートは `GetChild` で取得できます。

```csharp
// Find the first chart in the document (deep search)
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    Console.WriteLine("No chart found in the document.");
    return;
}

// Access the first series and its first data label
ChartSeries series = chart.Series[0];
ChartDataLabel dataLabel = series.DataLabels[0];

// Change the label's position and text
dataLabel.Position = ChartDataLabelPosition.OutsideEnd; // Move label outside the bar
dataLabel.Text = "Ventes T1"; // French for "Sales Q1"
Console.WriteLine("Chart data label customized.");
```

**重要な手順の説明：**

- `GetChild(NodeType.Shape, 0, true)` は深さ優先検索を行い、最初に見つかったシェイプ（この場合はチャート）を返します。  
- `ChartSeries` はデータ ポイントのコレクションを表し、最初のシリーズ (`Series[0]`) は通常、主要データセットに対応します。  
- `ChartDataLabelPosition.OutsideEnd` はラベルを棒の端の外側に配置し、可読性を向上させます。  
- `dataLabel.Text` にフランス語の文字列を設定することで、ラベルを翻訳された段落に合わせます。

## 手順 5: 翻訳された段落を含む文書を保存する

```csharp
string translatedDocPath = @"YOUR_DIRECTORY/translated.docx";
document.Save(translatedDocPath);
Console.WriteLine($"Translated document saved to {translatedDocPath}");
```

この時点で文書にはフランス語の段落が含まれますが、チャートの設定は元のままです。

## 手順 6: 更新されたチャートを含む文書を保存する

同じ `Document` インスタンスを再利用できます。チャートの変更はすでにメモリ上にあるため、再読み込みは不要です。

```csharp
string chartUpdatedPath = @"YOUR_DIRECTORY/chart-updated.docx";
document.Save(chartUpdatedPath);
Console.WriteLine($"Chart‑updated document saved to {chartUpdatedPath}");
```

両方のファイルが配布できる状態になりました：

- **`translated.docx`** – フランス語の段落が含まれています。  
- **`chart-updated.docx`** – フランス語の段落とカスタマイズされたチャート ラベルの両方が含まれています。

## 完全な実行可能サンプル

以下は `Program.cs` にそのまま貼り付けて使用できる完全プログラムです。`YOUR_DIRECTORY` を実際のフォルダー パスに置き換えれば、コンパイルと実行がそのまま行えます。



## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説と完全なコード例が含まれており、追加の API 機能を習得したり、プロジェクトで代替実装アプローチを検討したりするのに役立ちます。

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Chart Data Label](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}