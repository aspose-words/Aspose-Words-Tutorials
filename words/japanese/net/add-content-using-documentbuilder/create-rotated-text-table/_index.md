---
title: Aspose.Words for .NET を使用して Word 文書に回転テキストテーブルを作成する
weight: 110
limit:
description: Aspose.Words for .NET を使用して、固定列幅、回転テキスト、正確な行高さ、内容が入力されたセルを持つ Word テーブルの作り方を学びます。
keywords: [Aspose.Words for .NET, rotated text table, fixed column widths, vertical alignment Aspose.Words, set row height Word, populate table cells .NET]
url: /net/add-content-using-documentbuilder/create-rotated-text-table/
date: '2026-09-16'
lastmod: '2026-09-16'
schemas:
- author: Aspose
  dateModified: '2026-09-16'
  description: Aspose.Words for .NET を使用して、固定列幅、回転テキスト、正確な行高さ、内容が入力されたセルを持つ Word テーブルの作り方を学びます。
  headline: Aspose.Words for .NET を使用して Word 文書に回転テキストテーブルを作成する
  type: TechArticle
- description: Aspose.Words for .NET を使用して、固定列幅、回転テキスト、正確な行高さ、内容が入力されたセルを持つ Word テーブルの作り方を学びます。
  name: Aspose.Words for .NET を使用して Word 文書に回転テキストテーブルを作成する
  steps:
  - name: テーブルの構築に使用する新しい Document と DocumentBuilder をインスタンス化します。
    text: テーブルの構築に使用する新しい Document と DocumentBuilder をインスタンス化します。
  - name: 新しいテーブルを開始し、最初のセルを挿入し、列幅を固定して自動調整されないようにします。
    text: 新しいテーブルを開始し、最初のセルを挿入し、列幅を固定して自動調整されないようにします。
  - name: 現在のセル内のコンテンツを垂直方向に中央揃えにし、1 行目の最初のセルのテキストを書き込みます。
    text: 現在のセル内のコンテンツを垂直方向に中央揃えにし、1 行目の最初のセルのテキストを書き込みます。
  - name: 1 行目の2 番目のセルを挿入し、そのテキストを書き込みます。
    text: 1 行目の2 番目のセルを挿入し、そのテキストを書き込みます。
  - name: 1 行目を閉じて、レイアウトを確定します。
    text: 1 行目を閉じて、レイアウトを確定します。
  - name: 2 行目の最初のセルを開始し、行の高さを正確に 100 ポイントに設定し、テキストを上向きに回転させ、セルのテキストを書き込みます。
    text: 2 行目の最初のセルを開始し、行の高さを正確に 100 ポイントに設定し、テキストを上向きに回転させ、セルのテキストを書き込みます。
  - name: 2 行目の2 番目のセルを挿入し、テキストを下向きに回転させ、セルのテキストを書き込みます。
    text: 2 行目の2 番目のセルを挿入し、テキストを下向きに回転させ、セルのテキストを書き込みます。
  - name: 2 行目を閉じて、テーブルの2 行目を完成させます。
    text: 2 行目を閉じて、テーブルの2 行目を完成させます。
  - name: テーブルの構築を終了し、テーブル構造を確定します。
    text: テーブルの構築を終了し、テーブル構造を確定します。
  - name: 完成した文書を .docx ファイルとして保存します。
    text: 完成した文書を .docx ファイルとして保存します。
  type: HowTo
- questions:
  - answer: 列幅を固定した後、次のセルを挿入する前に `builder.CellFormat.Width = <valueInPoints>;` で各セルに幅を割り当てます。テーブルはその正確な幅を保持します。
    question: '`table.AutoFit(AutoFitBehavior.FixedColumnWidths)` を呼び出した後、特定の列幅を設定するにはどうすればよいですか？'
  - answer: '`builder.CellFormat.VerticalAlignment` はセル単位の設定なので、2 行目のセルに対しても（例：`builder.CellFormat.VerticalAlignment
      = CellVerticalAlignment.Center;`）コンテンツを書き込む前に再度設定する必要があります。'
    question: なぜ垂直方向の配置は最初の行には適用されるが、2 行目には適用されないのでしょうか？
  - answer: はい。各 `builder.EndRow();` 呼び出しの前に `builder.RowFormat.Height` と `builder.RowFormat.HeightRule
      = HeightRule.Exactly` を設定します。次の行は異なる高さの値を持たせることができます。
    question: 各行に異なる正確な高さを設定できますか？できる場合はその方法を教えてください。
  - answer: 次のセルに書き込む前に `builder.CellFormat.Orientation = TextOrientation.Horizontal;`
      を割り当てて、向きをリセットします。
    question: '`TextOrientation.Upward` または `Downward` を使用した後、テキストの向きをデフォルトに戻すにはどうすればよいですか？'
  type: FAQPage
images:
- /net/add-content-using-documentbuilder/create-rotated-text-table/og-image.png
og_title: Aspose.Words で Word に回転テキストテーブルを作成する
og_description: 垂直に回転したテキストと正確な行高さを持つ固定幅テーブルを構築するステップバイステップのコード。
og_image_alt: Aspose.Words for .NET を使用して作成された、固定列幅、セル内の回転テキスト、定義された行高さを持つテーブルが含まれる Word 文書のスクリーンショット。
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET を使用して Word 文書に回転テキストテーブルを作成する
このチュートリアルでは、Word 文書を生成し、列幅が固定され、行の高さが正確で、セルのテキストが垂直に回転するテーブルを追加する方法を示します。垂直方向の配置設定、テキストの向きの適用、各セルへのコンテンツ入力、そして最終的に文書を保存する方法を Aspose.Words for .NET で学びます。

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/create-rotated-text-table" >}}


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
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: `table.AutoFit(AutoFitBehavior.FixedColumnWidths)` を呼び出した後、特定の列幅を設定するにはどうすればよいですか？**  
A: 列幅を固定した後、次のセルを挿入する前に `builder.CellFormat.Width = <valueInPoints>;` で各セルに幅を割り当てます。テーブルはその正確な幅を保持します。

**Q: なぜ垂直方向の配置は最初の行には適用されるが、2 行目には適用されないのでしょうか？**  
A: `builder.CellFormat.VerticalAlignment` はセル単位の設定なので、2 行目のセルに対しても（例：`builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`）コンテンツを書き込む前に再度設定する必要があります。

**Q: 各行に異なる正確な高さを設定できますか？できる場合はその方法を教えてください。**  
A: はい。各 `builder.EndRow();` 呼び出しの前に `builder.RowFormat.Height` と `builder.RowFormat.HeightRule = HeightRule.Exactly` を設定します。次の行は異なる高さの値を持たせることができます。

**Q: `TextOrientation.Upward` または `Downward` を使用した後、テキストの向きをデフォルトに戻すにはどうすればよいですか？**  
A: 次のセルに書き込む前に `builder.CellFormat.Orientation = TextOrientation.Horizontal;` を割り当てて、向きをリセットします。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}