---
title: Aspose.Words for .NET を使用して Word ドキュメントに赤い斜めテキスト透かしを追加する
weight: 110
limit:
description: Aspose.Words for .NET を使用して、バッチで生成されるすべての Word ファイルに赤い斜めテキスト透かしを自動的に適用します。
keywords: [Aspose.Words for .NET, text watermark, red diagonal watermark, batch document generation, DocumentBuilder watermark, automated report]
url: /net/programming-with-watermark/add-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Aspose.Words for .NET を使用して、バッチで生成されるすべての Word ファイルに赤い斜めテキスト透かしを自動的に適用します。
  headline: Aspose.Words for .NET を使用して Word ドキュメントに赤い斜めテキスト透かしを追加する
  type: TechArticle
- description: Aspose.Words for .NET を使用して、バッチで生成されるすべての Word ファイルに赤い斜めテキスト透かしを自動的に適用します。
  name: Aspose.Words for .NET を使用して Word ドキュメントに赤い斜めテキスト透かしを追加する
  steps:
  - name: 出力ファイルが保存される "GeneratedReports" フォルダーを作成します。
    text: 出力ファイルが保存される "GeneratedReports" フォルダーを作成します。
  - name: 3つの別々のドキュメントを生成するループを開始します。
    text: 3つの別々のドキュメントを生成するループを開始します。
  - name: 新しい空の Word ドキュメントオブジェクトを作成します。
    text: 新しい空の Word ドキュメントオブジェクトを作成します。
  - name: DocumentBuilder を使用して、タイトル行と説明をドキュメントに書き込みます。
    text: DocumentBuilder を使用して、タイトル行と説明をドキュメントに書き込みます。
  - name: フォント、サイズ、色、斜めレイアウトなど、透かしの外観を定義します。
    text: フォント、サイズ、色、斜めレイアウトなど、透かしの外観を定義します。
  - name: 設定した赤い斜め透かし（テキストは "PROTECTED"）をドキュメントに適用します。
    text: 設定した赤い斜め透かし（テキストは "PROTECTED"）をドキュメントに適用します。
  - name: 透かしを付けたドキュメントをユニークなファイル名で "GeneratedReports" フォルダーに保存します。
    text: 透かしを付けたドキュメントをユニークなファイル名で "GeneratedReports" フォルダーに保存します。
  - name: 現在のドキュメントの処理が完了したらループを終了します。
    text: 現在のドキュメントの処理が完了したらループを終了します。
  type: HowTo
- questions:
  - answer: IsSemitrasparent は透かしを部分的に不透明に描画するかどうかを決定します。**true** に設定するとテキストが半透明になり、下のコンテンツがより読みやすくなります。
    question: '**IsSemitrasparent** オプションは何を制御し、**true** に設定するとどのような効果がありますか？'
  - answer: はい。**document.Watermark.SetText** を呼び出す前に、**TextWatermarkOptions** の **Layout**
      プロパティを **WatermarkLayout.Horizontal** に設定します。
    question: 透かしの向きを斜めではなく水平に変更できますか？
  - answer: 'このスニペットは新しい **Document** インスタンスを作成しますが、既存のファイル（例: `new Document(\"Existing.docx\")`）を開き、**document.Watermark.SetText**
      を呼び出すことで同じ透かしを適用できます。'
    question: このコードは既存の Word ファイルに透かしを追加しますか、それとも新規作成したドキュメントにのみ追加しますか？
  - answer: '**TextWatermarkOptions** の **Color** プロパティに **Color.FromArgb(red, green,
      blue)** でカスタムカラーを割り当てます。例: 紫色の場合は `Color = Color.FromArgb(128, 0, 128)` とします。'
    question: 事前定義の **Color.Red** の代わりに、カスタム RGB 色を透かしに使用するにはどうすればよいですか？
  type: FAQPage
images:
- /net/programming-with-watermark/add-text-watermark/og-image.png
og_title: Word ドキュメントに赤い斜めテキスト透かしを追加する
og_description: Aspose.Words を使用して、バッチ内の各 Word ドキュメントに赤い斜め透かしを自動適用する方法をご覧ください。
og_image_alt: Aspose.Words for .NET を使用して Word ドキュメントに赤い斜めテキスト透かしを追加する方法を示すガイド
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET を使用して Word ドキュメントに赤い斜めテキスト透かしを追加する
このチュートリアルでは、バッチレポート生成中に作成される各 Word ドキュメントに赤い斜めテキスト透かしを自動的に埋め込む方法を示します。Aspose.Words for .NET の Document と DocumentBuilder クラスを使用し、ファイルが生成されるたびにプログラムで透かしを適用することで、手作業なしで全てのドキュメントに同じブランドや機密性の通知を付与できます。

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-text-watermark" >}}


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

**Q: **IsSemitrasparent** オプションは何を制御し、**true** に設定するとどのような効果がありますか？**  
A: IsSemitrasparent は透かしを部分的に不透明に描画するかどうかを決定します。**true** に設定するとテキストが半透明になり、下のコンテンツがより読みやすくなります。

**Q: 透かしの向きを斜めではなく水平に変更できますか？**  
A: はい。**document.Watermark.SetText** を呼び出す前に、**TextWatermarkOptions** の **Layout** プロパティを **WatermarkLayout.Horizontal** に設定します。

**Q: このコードは既存の Word ファイルに透かしを追加しますか、それとも新規作成したドキュメントにのみ追加しますか？**  
A: このスニペットは新しい **Document** インスタンスを作成しますが、既存のファイル（例: `new Document(\"Existing.docx\")`）を開き、**document.Watermark.SetText** を呼び出すことで同じ透かしを適用できます。

**Q: 事前定義の **Color.Red** の代わりに、カスタム RGB 色を透かしに使用するにはどうすればよいですか？**  
A: **TextWatermarkOptions** の **Color** プロパティに **Color.FromArgb(red, green, blue)** でカスタムカラーを割り当てます。例: 紫色の場合は `Color = Color.FromArgb(128, 0, 128)` とします。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}