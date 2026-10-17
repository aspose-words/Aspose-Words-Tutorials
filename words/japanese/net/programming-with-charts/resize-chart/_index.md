---
title: Aspose.Words for .NET を使用して Word のページサイズを変更する際に、チャートを比例的にリサイズする
weight: 210
limit:
description: Aspose.Words for .NET を使用して、文書を A4 に変更したときに Word の縦棒グラフを自動リサイズする方法を学びます。
keywords: [chart resizing, Aspose.Words for .NET, Word column chart, automatic chart scaling, A4 page size, resize chart in Word]
url: /net/programming-with-charts/resize-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET を使用して、文書を A4 に変更したときに Word の縦棒グラフを自動リサイズする方法を学びます。
  headline: Aspose.Words for .NET を使用して Word のページサイズを変更する際に、チャートを比例的にリサイズする
  type: TechArticle
- description: Aspose.Words for .NET を使用して、文書を A4 に変更したときに Word の縦棒グラフを自動リサイズする方法を学びます。
  name: Aspose.Words for .NET を使用して Word のページサイズを変更する際に、チャートを比例的にリサイズする
  steps:
  - name: 新しい Document オブジェクトと、それを編集するための DocumentBuilder を作成します。
    text: 新しい Document オブジェクトと、それを編集するための DocumentBuilder を作成します。
  - name: サイズ 432×252 ポイントの縦棒グラフを挿入し、その Chart オブジェクトを取得します。
    text: サイズ 432×252 ポイントの縦棒グラフを挿入し、その Chart オブジェクトを取得します。
  - name: チャートのタイトルテキストを "Quarterly Revenue" に設定し、表示させます。
    text: チャートのタイトルテキストを "Quarterly Revenue" に設定し、表示させます。
  - name: 元のチャートサイズのまま、ドキュメントをファイルに保存します。
    text: 元のチャートサイズのまま、ドキュメントをファイルに保存します。
  - name: 文書の用紙サイズを A4 に変更し、レイアウトを更新します。
    text: 文書の用紙サイズを A4 に変更し、レイアウトを更新します。
  - name: 元のアスペクト比を保ちつつ、ページ幅の 80 % に相当する新しいチャート幅を計算します。
    text: 元のアスペクト比を保ちつつ、ページ幅の 80 % に相当する新しいチャート幅を計算します。
  - name: シェイプにチャートが含まれている場合、計算した幅と高さを適用してサイズ変更します。
    text: シェイプにチャートが含まれている場合、計算した幅と高さを適用してサイズ変更します。
  - name: チャートが新しいページサイズに合わせてリサイズされた後、ドキュメントを保存します。
    text: チャートが新しいページサイズに合わせてリサイズされた後、ドキュメントを保存します。
  type: HowTo
- questions:
  - answer: はい。`docBuilder.PageSetup.PaperSize` を変更しても既存のシェイプは自動的に調整されないため、示したように
      `chartContainer.Width` と `Height` を自分で再計算して割り当てる必要があります。
    question: 文書の用紙サイズを変更した後、チャートを手動でリサイズする必要がありますか？
  - answer: '`originalAspectRatio = chartContainer.Height / chartContainer.Width`
      として比率を保持し、新しい幅が決まった後に `newChartHeight = newChartWidth * originalAspectRatio`
      を計算しています。'
    question: コードはリサイズ時にチャートの元の幅と高さの比率（アスペクト比）をどのように保っていますか？
  - answer: '`UpdatePageLayout()` はレイアウトエンジンにページ寸法を再評価させ、チャートサイズを再計算する前に `docBuilder.PageSetup.PageWidth`
      が新しい A4 の幅を反映するようにします。'
    question: 用紙サイズを A4 に設定した後に `myDoc.UpdatePageLayout()` を呼び出すのはなぜですか？
  - answer: '`if (chartContainer.HasChart)` のガードにより、チャートが存在しない場合に `Width` と `Height`
      の代入が行われず、実行時例外を回避します。'
    question: 挿入したシェイプに実際にチャートが含まれていない場合はどうなりますか？
  - answer: もちろんです。`0.8` の乗数を任意の比率に置き換えれば、残りのリサイズロジックは元のアスペクト比を引き続き保持します。
    question: 80 % のスケーリング係数を別の値に変更できますか？
  type: FAQPage
images:
- /net/programming-with-charts/resize-chart/og-image.png
og_title: A4 に切り替えるときの Word チャートのリサイズ
og_description: 文書を A4 に変更した後、チャートを自動リサイズして比例を保ちます。
og_image_alt: Aspose.Words for .NET を使用して、A4 サイズの Word 文書に合わせて自動的にリサイズされた縦棒グラフを示すスクリーンショット
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET を使用して Word のページサイズを変更する際に、チャートを比例的にリサイズする
このチュートリアルでは、Word 文書に縦棒グラフを挿入し、文書のページサイズを A4 に切り替え、チャートが新しいページ幅に対して比例したまま自動的にリサイズされる方法を示します。手順に従うことで、手動でスケーリングせずにチャートのサイズが調整され、さまざまなページ形式でも一貫したレイアウトが保たれることが確認できます。

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/resize-chart" >}}


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

**Q: 文書の用紙サイズを変更した後、チャートを手動でリサイズする必要がありますか？**  
A: はい。`docBuilder.PageSetup.PaperSize` を変更しても既存のシェイプは自動的に調整されないため、示したように `chartContainer.Width` と `Height` を自分で再計算して割り当てる必要があります。

**Q: コードはリサイズ時にチャートの元の幅と高さの比率（アスペクト比）をどのように保っていますか？**  
A: `originalAspectRatio = chartContainer.Height / chartContainer.Width` として比率を保持し、新しい幅が決まった後に `newChartHeight = newChartWidth * originalAspectRatio` を計算しています。

**Q: 用紙サイズを A4 に設定した後に `myDoc.UpdatePageLayout()` を呼び出すのはなぜですか？**  
A: `UpdatePageLayout()` はレイアウトエンジンにページ寸法を再評価させ、チャートサイズを再計算する前に `docBuilder.PageSetup.PageWidth` が新しい A4 の幅を反映するようにします。

**Q: 挿入したシェイプに実際にチャートが含まれていない場合はどうなりますか？**  
A: `if (chartContainer.HasChart)` のガードにより、チャートが存在しない場合に `Width` と `Height` の代入が行われず、実行時例外を回避します。

**Q: 80 % のスケーリング係数を別の値に変更できますか？**  
A: もちろんです。`0.8` の乗数を任意の比率に置き換えれば、残りのリサイズロジックは元のアスペクト比を引き続き保持します。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}