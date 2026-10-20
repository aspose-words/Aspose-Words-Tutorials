---
title: Aspose.Words for .NET を使用して Word でチャートタイトルを更新し、凡例の表示を切り替える
weight: 810
limit:
description: Aspose.Words for .NET を使用して、Word 文書内のチャートタイトルを変更し、凡例の表示を制御する方法を学びます。
keywords: [Aspose.Words for .NET, update chart title, toggle legend visibility, word chart manipulation, c# chart title, aspose words chart legend]
url: /net/programming-with-charts/update-chart-title/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET を使用して、Word 文書内のチャートタイトルを変更し、凡例の表示を制御する方法を学びます。
  headline: Aspose.Words for .NET を使用して Word でチャートタイトルを更新し、凡例の表示を切り替える
  type: TechArticle
- description: Aspose.Words for .NET を使用して、Word 文書内のチャートタイトルを変更し、凡例の表示を制御する方法を学びます。
  name: Aspose.Words for .NET を使用して Word でチャートタイトルを更新し、凡例の表示を切り替える
  steps:
  - name: ユーザーが指定したチャートタイトルと、凡例を表示するかどうかを定義します。
    text: ユーザーが指定したチャートタイトルと、凡例を表示するかどうかを定義します。
  - name: 新しい Word 文書と、コンテンツを追加するための DocumentBuilder を作成します。
    text: 新しい Word 文書と、コンテンツを追加するための DocumentBuilder を作成します。
  - name: 文書に 432 × 252 pt の縦棒グラフを挿入し、その Shape が実際にチャートを含んでいることを確認します。
    text: 文書に 432 × 252 pt の縦棒グラフを挿入し、その Shape が実際にチャートを含んでいることを確認します。
  - name: チャートオブジェクトを取得し、タイトルテキストをユーザーの値に設定し、タイトルが表示されるようにします。
    text: チャートオブジェクトを取得し、タイトルテキストをユーザーの値に設定し、タイトルが表示されるようにします。
  - name: 凡例を設定します：要求があれば右側に表示し、そうでなければ非表示にし、プロット領域にオーバーレイできるようにします。
    text: 凡例を設定します：要求があれば右側に表示し、そうでなければ非表示にし、プロット領域にオーバーレイできるようにします。
  - name: 変更した文書をディスクに CustomChart.docx として保存します。
    text: 変更した文書をディスクに CustomChart.docx として保存します。
  type: HowTo
- questions:
  - answer: '`displayLegend` が `true` の場合、コードは `chartLegend.Position` を `LegendPosition.Right`
      に設定し、凡例をプロット領域の右側に表示します。`Overlay` プロパティは `true` のままで、凡例がチャートと重なることでスペースを節約できます。'
    question: '`displayLegend` を `true` に設定すると、生成されたチャートで何が変わりますか？'
  - answer: '`chartTitle.Text` を設定した後で `chartTitle.Show = false`（または `Show` を `true`
      に設定しない）と、タイトルは Word 文書に描画されません。'
    question: ユーザーがタイトルを提供しなかった場合、チャートタイトルを非表示にするにはどうすればよいですか？
  - answer: はい。`InsertChart` はチャートを含むはずの `Shape` を返しますが、`HasChart` を確認することでその Shape
      が実際に `Chart` オブジェクトを保持していることを保証します。そうでない場合、コードは `InvalidOperationException`
      をスローします。
    question: '`InsertChart` を呼び出した後に `chartContainer.HasChart` を確認する必要がありますか？'
  - answer: 'もちろんです。`LegendPosition` 列挙体の任意の値（例: `LegendPosition.Top`、`LegendPosition.Bottom`、`LegendPosition.Left`）を
      `chartLegend.Position` に設定すれば、必要に応じて凡例の位置を変更できます。'
    question: 凡例を右側以外の場所に配置できますか？
  type: FAQPage
images:
- /net/programming-with-charts/update-chart-title/og-image.png
og_title: Word でチャートタイトルと凡例を変更する
og_description: Aspose.Words for .NET を使用して、Word 文書内でカスタムチャートタイトルを設定し、凡例の表示を制御する方法を学びます。
og_image_alt: Aspose.Words for .NET を使用して、Word 文書内のチャートタイトルを更新し、凡例を切り替えるコードを示すガイド
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET を使用して Word でチャートタイトルを更新し、凡例の表示を切り替える
このチュートリアルでは、Aspose.Words for .NET を使用して Word 文書内のチャートをプログラムで変更する方法を示します。縦棒グラフの挿入、ユーザーが提供したテキストでタイトルを置き換える方法、そしてユーザーの設定に基づいて凡例の表示とオーバーレイを制御する方法を学びます。これらの手順により、手動で編集することなくチャートの表示を動的にカスタマイズできます。

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/update-chart-title" >}}


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

**Q: `displayLegend` を `true` に設定すると、生成されたチャートで何が変わりますか？**  
A: `displayLegend` が `true` の場合、コードは `chartLegend.Position` を `LegendPosition.Right` に設定し、凡例をプロット領域の右側に表示します。`Overlay` プロパティは `true` のままで、凡例がチャートと重なることでスペースを節約できます。

**Q: ユーザーがタイトルを提供しなかった場合、チャートタイトルを非表示にするにはどうすればよいですか？**  
A: `chartTitle.Text` を設定した後で `chartTitle.Show = false`（または `Show` を `true` に設定しない）と、タイトルは Word 文書に描画されません。

**Q: `InsertChart` を呼び出した後に `chartContainer.HasChart` を確認する必要がありますか？**  
A: はい。`InsertChart` はチャートを含むはずの `Shape` を返しますが、`HasChart` を確認することでその Shape が実際に `Chart` オブジェクトを保持していることを保証します。そうでない場合、コードは `InvalidOperationException` をスローします。

**Q: 凡例を右側以外の場所に配置できますか？**  
A: もちろんです。`LegendPosition` 列挙体の任意の値（例: `LegendPosition.Top`、`LegendPosition.Bottom`、`LegendPosition.Left`）を `chartLegend.Position` に設定すれば、必要に応じて凡例の位置を変更できます。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}