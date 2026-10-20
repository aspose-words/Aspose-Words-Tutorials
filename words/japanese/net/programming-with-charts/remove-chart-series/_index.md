---
title: Aspose.Words for .NET を使用して Word ドキュメントからチャート系列を削除する
weight: 510
limit:
description: Aspose.Words for .NET を使用して、Word ドキュメント内の縦棒グラフから特定のデータ系列を削除する方法を学びます。
keywords: [Aspose.Words for .NET, remove chart series, ChartSeriesCollection.RemoveAt, column chart manipulation, Word document chart editing, C# chart series removal]
url: /net/programming-with-charts/remove-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET を使用して、Word ドキュメント内の縦棒グラフから特定のデータ系列を削除する方法を学びます。
  headline: Aspose.Words for .NET を使用して Word ドキュメントからチャート系列を削除する
  type: TechArticle
- description: Aspose.Words for .NET を使用して、Word ドキュメント内の縦棒グラフから特定のデータ系列を削除する方法を学びます。
  name: Aspose.Words for .NET を使用して Word ドキュメントからチャート系列を削除する
  steps:
  - name: 新しい Word Document を作成し、それにリンクした DocumentBuilder を作成します。
    text: 新しい Word Document を作成し、それにリンクした DocumentBuilder を作成します。
  - name: サイズ 432×252 ポイントの縦棒グラフを挿入し、さらに操作できるように Chart オブジェクトを取得します。
    text: サイズ 432×252 ポイントの縦棒グラフを挿入し、さらに操作できるように Chart オブジェクトを取得します。
  - name: 削除すべき系列のゼロベースインデックス（2 番目の系列）を定義します。
    text: 削除すべき系列のゼロベースインデックス（2 番目の系列）を定義します。
  - name: インデックスが有効な場合、チャートの Series コレクションに対して RemoveAt を呼び出してその系列を削除します。
    text: インデックスが有効な場合、チャートの Series コレクションに対して RemoveAt を呼び出してその系列を削除します。
  - name: 更新されたドキュメントを .docx ファイルとして保存します。
    text: 更新されたドキュメントを .docx ファイルとして保存します。
  type: HowTo
- questions:
  - answer: '`if` 条件（`targetSeriesIdx < columnChart.Series.Count`）が失敗するため、`RemoveAt`
      は呼び出されず、チャートは変更されません。'
    question: チャートの系列数と同じインデックスを渡した場合、どうなりますか？
  - answer: はい、`columnChart.Series.RemoveAt` の後、凡例は残っている系列を反映するように再生成されるため、削除された項目は凡例から消えます。
    question: 系列を削除すると、チャートの凡例は自動的に更新されますか？
  - answer: このコードは `Series` コレクションをサポートするすべてのチャートタイプで機能します。チャートを挿入する際に `ChartType.Column`
      を目的のタイプに変更すればよいだけです。
    question: 同じコードを使用して、折れ線グラフや円グラフから系列を削除できますか？
  - answer: 系列がゼロのチャートでも有効な `Shape` として保存されますが、生成されたドキュメントでは空のチャートとして表示されます。
    question: チャートの唯一の系列を削除した場合、チャートは正しく保存されますか？
  type: FAQPage
images:
- /net/programming-with-charts/remove-chart-series/og-image.png
og_title: Word ドキュメント内のチャート系列を削除する
og_description: Aspose.Words for .NET を使用して、Word のチャートからデータ系列を削除するステップバイステップガイド。
og_image_alt: Aspose.Words for .NET を使用して、Word ドキュメント内の縦棒グラフから特定のデータ系列を削除する方法を示すガイド
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET を使用して Word ドキュメントからチャート系列を削除する
このチュートリアルでは、Word ドキュメントを作成し、DocumentBuilder で縦棒グラフを追加し、ChartSeriesCollection.RemoveAt メソッドを使用してそのグラフから特定のデータ系列を削除する方法を示します。最後には、不要な系列が削除された状態で保存されたドキュメントが得られ、.NET コードから直接チャートの内容を正確に制御できます。

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/remove-chart-series" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: チャートの系列数と同じインデックスを渡した場合、どうなりますか？**  
A: `if` 条件（`targetSeriesIdx < columnChart.Series.Count`）が失敗するため、`RemoveAt` は呼び出されず、チャートは変更されません。

**Q: 系列を削除すると、チャートの凡例は自動的に更新されますか？**  
A: はい、`columnChart.Series.RemoveAt` の後、凡例は残っている系列を反映するように再生成されるため、削除された項目は凡例から消えます。

**Q: 同じコードを使用して、折れ線グラフや円グラフから系列を削除できますか？**  
A: このコードは `Series` コレクションをサポートするすべてのチャートタイプで機能します。チャートを挿入する際に `ChartType.Column` を目的のタイプに変更すればよいだけです。

**Q: チャートの唯一の系列を削除した場合、チャートは正しく保存されますか？**  
A: 系列がゼロのチャートでも有効な `Shape` として保存されますが、生成されたドキュメントでは空のチャートとして表示されます。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}