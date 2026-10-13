---
title: Aspose.Words for .NET を使用して Word のチャートで二次 Y 軸を通貨形式に設定する
weight: 710
limit:
description: Aspose.Words for .NET を使用して、Word の折れ線グラフに二次 Y 軸を追加し、通貨形式に設定する方法を学びます。
keywords: [Aspose.Words for .NET, format secondary axis, currency axis formatting, Word line chart secondary series, secondary Y axis .NET, chart axis number format]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET を使用して、Word の折れ線グラフに二次 Y 軸を追加し、通貨形式に設定する方法を学びます。
  headline: Aspose.Words for .NET を使用して Word のチャートで二次 Y 軸を通貨形式に設定する
  type: TechArticle
- description: Aspose.Words for .NET を使用して、Word の折れ線グラフに二次 Y 軸を追加し、通貨形式に設定する方法を学びます。
  name: Aspose.Words for .NET を使用して Word のチャートで二次 Y 軸を通貨形式に設定する
  steps:
  - name: 空の新しい Word ドキュメントと、編集用の DocumentBuilder を作成します。
    text: 空の新しい Word ドキュメントと、編集用の DocumentBuilder を作成します。
  - name: サイズ 450×250 ポイントの折れ線グラフをドキュメントに挿入し、その Chart オブジェクトを取得します。
    text: サイズ 450×250 ポイントの折れ線グラフをドキュメントに挿入し、その Chart オブジェクトを取得します。
  - name: Aspose が新しいチャートに追加するデフォルトのプレースホルダー系列を削除します。
    text: Aspose が新しいチャートに追加するデフォルトのプレースホルダー系列を削除します。
  - name: 四半期ラベルを定義し、サンプル値を持つ一次データ系列をチャートに追加します。
    text: 四半期ラベルを定義し、サンプル値を持つ一次データ系列をチャートに追加します。
  - name: Line タイプの二次系列グループを作成し、二次軸グループに割り当てます。
    text: Line タイプの二次系列グループを作成し、二次軸グループに割り当てます。
  - name: 二次 X 軸を非表示にし、二次 Y 軸だけが表示されるようにします。
    text: 二次 X 軸を非表示にし、二次 Y 軸だけが表示されるようにします。
  - name: 二次 Y 軸のタイトルを表示し、そのテキストを \"Sales (USD)\" に設定します。
    text: 二次 Y 軸のタイトルを表示し、そのテキストを \"Sales (USD)\" に設定します。
  - name: 二次 Y 軸の数値形式を小数点以下2桁の通貨パターンに設定し、ソースの書式設定からリンクを解除します。
    text: 二次 Y 軸の数値形式を小数点以下2桁の通貨パターンに設定し、ソースの書式設定からリンクを解除します。
  - name: 二次グループに補助系列を追加し、二次 Y 軸に対してプロットされるデータを提供します。
    text: 二次グループに補助系列を追加し、二次 Y 軸に対してプロットされるデータを提供します。
  - name: 完成したドキュメントを、現在のディレクトリにある ProfitChart.docx という名前のファイルに保存します。
    text: 完成したドキュメントを、現在のディレクトリにある ProfitChart.docx という名前のファイルに保存します。
  type: HowTo
- questions:
  - answer: チャートは Aspose.Words が挿入するデフォルトのプレースホルダー系列を保持するため、カスタムの \"Main Series\"
      が不要なデータポイントと一緒に表示されます。
    question: '`lineChart.Series.Clear()` 呼び出しを省略するとどうなりますか？'
  - answer: '`secondarySeriesGroup.AxisX.Hidden = false;` を設定します（または `true` に設定している行を削除するだけでも構いません）。'
    question: 二次 X 軸を非表示にせずに表示するにはどうすればよいですか？
  - answer: はい。書式文字列を変更します。例えばユーロの場合は `secondarySeriesGroup.AxisY.NumberFormat.FormatCode
      = \"€\"#,##0.00\";` のようにし、ロケールに合わせてパターンを調整してください。
    question: 二次 Y 軸に別の通貨記号や書式を使用できますか？
  - answer: '`IsLinkedToSource` が true の場合、軸は基になるデータソースから数値書式を継承し、カスタムの `FormatCode`
      が上書きされます。false に設定すると、指定した書式が強制的に使用されます。'
    question: カスタム数値書式を適用する際に `IsLinkedToSource = false` を設定する必要があるのはなぜですか？
  - answer: はい。`secondarySeriesGroup.AxisY.Position = AxisPosition.Left;` を割り当てれば（デフォルトは
      `Right`）軸が描画される側を制御できます。
    question: 二次 Y 軸をチャートの左側に移動することは可能ですか？
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: チャートの二次軸を通貨形式に設定する
og_description: Word の折れ線グラフに二次 Y 軸を追加し、小数点以下2桁の通貨形式でスタイル設定する方法を学びます。
og_image_alt: Aspose.Words for .NET を使用して二次 Y 軸が通貨形式に設定された Word の折れ線グラフを示すスクリーンショット
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET を使用して Word のチャートで二次 Y 軸を通貨形式に設定する
このチュートリアルでは、Word ドキュメントを作成し、折れ線グラフを挿入し、二次 Y 軸を追加し、その軸を小数点以下2桁の通貨形式に設定し、Aspose.Words for .NET を使用して二次データ系列をバインドする方法を示します。二次軸を通貨形式にすることで、一次系列と並んで財務データを明確に提示できます。ステップバイステップのコードに従って、生成されたドキュメント内に直接チャートが描画される様子をご確認ください。

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/format-secondary-axis" >}}


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

**Q: `lineChart.Series.Clear()` 呼び出しを省略するとどうなりますか？**  
A: チャートは Aspose.Words が挿入するデフォルトのプレースホルダー系列を保持するため、カスタムの \"Main Series\" が不要なデータポイントと一緒に表示されます。

**Q: 二次 X 軸を非表示にせずに表示するにはどうすればよいですか？**  
A: `secondarySeriesGroup.AxisX.Hidden = false;` を設定します（または `true` に設定している行を削除するだけでも構いません）。

**Q: 二次 Y 軸に別の通貨記号や書式を使用できますか？**  
A: はい。書式文字列を変更します。例えばユーロの場合は `secondarySeriesGroup.AxisY.NumberFormat.FormatCode = \"€\"#,##0.00\";` のようにし、ロケールに合わせてパターンを調整してください。

**Q: カスタム数値書式を適用する際に `IsLinkedToSource = false` を設定する必要があるのはなぜですか？**  
A: `IsLinkedToSource` が true の場合、軸は基になるデータソースから数値書式を継承し、カスタムの `FormatCode` が上書きされます。false に設定すると、指定した書式が強制的に使用されます。

**Q: 二次 Y 軸をチャートの左側に移動することは可能ですか？**  
A: はい。`secondarySeriesGroup.AxisY.Position = AxisPosition.Left;` を割り当てれば（デフォルトは `Right`）軸が描画される側を制御できます。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}