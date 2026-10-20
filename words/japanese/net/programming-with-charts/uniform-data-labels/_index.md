---
title: Aspose.Words for .NET を使用して列チャートのデータ ラベルを均一に設定する
weight: 110
limit:
description: Aspose.Words for .NET を使用して Word の列チャートを作成し、すべての系列に均一なデータ ラベルのフォントサイズと色を適用する方法を学びます。
keywords: [Aspose.Words for .NET, uniform data labels, chart data label formatting, column chart Word SDK, default data label style, Word document chart customization]
url: /net/programming-with-charts/uniform-data-labels/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET を使用して Word の列チャートを作成し、すべての系列に均一なデータ ラベルのフォントサイズと色を適用する方法を学びます。
  headline: Aspose.Words for .NET を使用して列チャートのデータ ラベルを均一に設定する
  type: TechArticle
- description: Aspose.Words for .NET を使用して Word の列チャートを作成し、すべての系列に均一なデータ ラベルのフォントサイズと色を適用する方法を学びます。
  name: Aspose.Words for .NET を使用して列チャートのデータ ラベルを均一に設定する
  steps:
  - name: 新しい空の Word ドキュメントと、それを編集するための DocumentBuilder を作成します。
    text: 新しい空の Word ドキュメントと、それを編集するための DocumentBuilder を作成します。
  - name: ドキュメントに 500×300 の列チャートを挿入し、その Chart オブジェクトを取得します。
    text: ドキュメントに 500×300 の列チャートを挿入し、その Chart オブジェクトを取得します。
  - name: Aspose.Words が新しいチャートに追加するデフォルトのサンプル系列を削除します。
    text: Aspose.Words が新しいチャートに追加するデフォルトのサンプル系列を削除します。
  - name: カテゴリ ラベルを定義し、2 つのデータ系列（Item Alpha と Item Beta）とその値をチャートに追加します。
    text: カテゴリ ラベルを定義し、2 つのデータ系列（Item Alpha と Item Beta）とその値をチャートに追加します。
  - name: すべてのデータ ラベルに適用されるベースラインのフォントサイズと色を設定します。
    text: すべてのデータ ラベルに適用されるベースラインのフォントサイズと色を設定します。
  - name: 各系列のデータ ラベルを有効にし、数値を表示し、事前定義されたフォントサイズと色を適用します。
    text: 各系列のデータ ラベルを有効にし、数値を表示し、事前定義されたフォントサイズと色を適用します。
  - name: ドキュメントを .docx ファイルとして保存します。
    text: ドキュメントを .docx ファイルとして保存します。
  type: HowTo
- questions:
  - answer: '`InsertChart` はデフォルトのサンプル系列を持つチャートを作成します。これをクリアするとそのプレースホルダーが削除され、チャートには追加した系列（`Item
      Alpha` と `Item Beta`）だけが表示されます。'
    question: '`chart.Series.Clear()` を自分の系列を追加する前に呼び出す必要があるのはなぜですか？'
  - answer: '`Color.White` を任意の `System.Drawing.Color` 値（例: `Color.Black` や `Color.FromArgb(255,
      30, 144, 255)`）に置き換えます。新しい色はループ内で `series.DataLabels.Font.Color` を通じて適用されます。'
    question: データ ラベルの色を白以外に変更するにはどうすればよいですか？
  - answer: データ ラベルが非表示になるため、適用したフォント設定は見えなくなります。ラベル（およびそのスタイリング）を表示させるには、`HasDataLabels`
      を `true` のままにしておく必要があります。
    question: フォントサイズと色を設定した後に `series.HasDataLabels = false` を設定するとどうなりますか？
  - answer: はい。各 `ChartSeries` には独自の `DataLabels` オブジェクトがあるため、最初のループ後に追加された系列でも `HasDataLabels`、`ShowValue`、フォントプロパティを設定する必要があります。再度ループするか、スタイリングをヘルパーメソッドに抽出して適用してください。
    question: コードの後半で別の系列を追加した場合、再度系列をループする必要がありますか？
  type: FAQPage
images:
- /net/programming-with-charts/uniform-data-labels/og-image.png
og_title: Word チャートに均一なデータ ラベルを適用する
og_description: Aspose.Words for .NET を使って、すべてのチャート ラベルに同じフォントサイズと色をすぐに設定できます。
og_image_alt: Aspose.Words for .NET を使用して作成された、すべてのデータ ラベルが同じフォントサイズと色を共有する列チャートを含む Word ドキュメントのガイドです。
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET を使用して列チャートのデータ ラベルを均一に設定する
このチュートリアルでは、Aspose.Words for .NET を使用して Word ドキュメントを生成し、列チャートを挿入し、カスタム データ系列を追加する方法を示します。その後、デフォルトのデータ ラベルのフォントサイズと色を定義し、チャート内のすべての系列が同一のラベルを表示するようにします。単一のスタイルを適用することで、チャート全体の視覚的外観を一貫させることができます。

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/uniform-data-labels" >}}


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

**Q: `chart.Series.Clear()` を自分の系列を追加する前に呼び出す必要があるのはなぜですか？**  
A: `InsertChart` はデフォルトのサンプル系列を持つチャートを作成します。これをクリアするとそのプレースホルダーが削除され、チャートには追加した系列（`Item Alpha` と `Item Beta`）だけが表示されます。

**Q: データ ラベルの色を白以外に変更するにはどうすればよいですか？**  
A: `Color.White` を任意の `System.Drawing.Color` 値（例: `Color.Black` や `Color.FromArgb(255, 30, 144, 255)`）に置き換えます。新しい色はループ内で `series.DataLabels.Font.Color` を通じて適用されます。

**Q: フォントサイズと色を設定した後に `series.HasDataLabels = false` を設定するとどうなりますか？**  
A: データ ラベルが非表示になるため、適用したフォント設定は見えなくなります。ラベル（およびそのスタイリング）を表示させるには、`HasDataLabels` を `true` のままにしておく必要があります。

**Q: コードの後半で別の系列を追加した場合、再度系列をループする必要がありますか？**  
A: はい。各 `ChartSeries` には独自の `DataLabels` オブジェクトがあるため、最初のループ後に追加された系列でも `HasDataLabels`、`ShowValue`、フォントプロパティを設定する必要があります。再度ループするか、スタイリングをヘルパーメソッドに抽出して適用してください。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}