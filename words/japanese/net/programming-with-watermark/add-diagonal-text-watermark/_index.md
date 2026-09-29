---
title: Aspose.Words for .NET を使用して、Word ドキュメントにカスタムフォントの斜めテキスト透かしを作成する
weight: 210
limit:
description: Aspose.Words for .NET を使用して、カスタムフォントの斜めテキスト透かしを Word .docx に追加するステップバイステップのコード。
keywords: [Aspose.Words for .NET, diagonal text watermark, custom font watermark, Word document watermark, Document.Watermark.SetText, C# watermark API]
url: /net/programming-with-watermark/add-diagonal-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Aspose.Words for .NET を使用して、カスタムフォントの斜めテキスト透かしを Word .docx に追加するステップバイステップのコード。
  headline: Aspose.Words for .NET を使用して、Word ドキュメントにカスタムフォントの斜めテキスト透かしを作成する
  type: TechArticle
- description: Aspose.Words for .NET を使用して、カスタムフォントの斜めテキスト透かしを Word .docx に追加するステップバイステップのコード。
  name: Aspose.Words for .NET を使用して、Word ドキュメントにカスタムフォントの斜めテキスト透かしを作成する
  steps:
  - name: '`document` という名前の新しい空の Word ドキュメント インスタンスを作成します。'
    text: '`document` という名前の新しい空の Word ドキュメント インスタンスを作成します。'
  - name: '`watermarkSettings` を Arial の 48pt グレー フォント、斜めレイアウト、不透明レンダリングで設定します。'
    text: '`watermarkSettings` を Arial の 48pt グレー フォント、斜めレイアウト、不透明レンダリングで設定します。'
  - name: 前述の設定を使用して、テキスト透かし「Private」を `document` に適用します。
    text: 前述の設定を使用して、テキスト透かし「Private」を `document` に適用します。
  - name: 透かしが付いたドキュメントを保存するファイルパスを定義します。
    text: 透かしが付いたドキュメントを保存するファイルパスを定義します。
  - name: 変更された `document` を指定されたパスに .docx ファイルとして保存します。
    text: 変更された `document` を指定されたパスに .docx ファイルとして保存します。
  type: HowTo
- questions:
  - answer: '`IsSemitrasparent` は透かしが部分的な不透明度で描画されるかどうかを決定します。`false` に設定すると透かしは完全に不透明になり、`true`
      にするとデフォルトの半透明効果が適用されます。'
    question: '`TextWatermarkOptions` の **IsSemitrasparent** フラグは何を制御しますか？'
  - answer: はい — `document.Watermark.SetText` を呼び出す前に、`Layout` プロパティを `WatermarkLayout.Horizontal`（または他の列挙値）に設定してください。
    question: 透かしの向きを斜めではなく水平に変更できますか？
  - answer: Word は透かし用にデフォルトフォントにフォールバックするため、テキストは表示されますが、意図したスタイルとは異なる見た目になる可能性があります。
    question: '指定した `FontFamily`（例: "Arial"）が対象マシンにインストールされていない場合はどうなりますか？'
  - answer: '`Document document = new Document("Existing.docx");` で既存ファイルをロードし、`TextWatermarkOptions`
      を構成して、示されたように `document.Watermark.SetText` を呼び出します。'
    question: 新規作成ではなく、既存の `.docx` ファイルに透かしを追加することは可能ですか？
  type: FAQPage
images:
- /net/programming-with-watermark/add-diagonal-text-watermark/og-image.png
og_title: カスタムフォントの斜めテキスト透かしを追加する
og_description: 数分で自分のフォントを使用した斜めテキスト透かしを Word ファイルに埋め込む方法を学びます。
og_image_alt: Aspose.Words for .NET を使用して、カスタムフォントの斜めテキスト透かしを Word ドキュメントに追加する方法を示すガイド
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET を使用して、Word ドキュメントにカスタムフォントの斜めテキスト透かしを作成する
このチュートリアルでは、新しい Word ドキュメントを作成し、選択したフォント設定で斜めテキスト透かしを構成し、Document.Watermark.SetText API を介して適用し、結果を .docx ファイルとして保存する手順を案内します。最後には、ブランドや所有権を示すプロフェッショナルな透かしが付いたドキュメントが手に入り、ステップバイステップのコードは任意の .NET プロジェクトにコピーできる状態です。

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-diagonal-text-watermark" >}}


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

**Q: `TextWatermarkOptions` の **IsSemitrasparent** フラグは何を制御しますか？**  
A: `IsSemitrasparent` は透かしが部分的な不透明度で描画されるかどうかを決定します。`false` に設定すると透かしは完全に不透明になり、`true` にするとデフォルトの半透明効果が適用されます。

**Q: 透かしの向きを斜めではなく水平に変更できますか？**  
A: はい — `document.Watermark.SetText` を呼び出す前に、`Layout` プロパティを `WatermarkLayout.Horizontal`（または他の列挙値）に設定してください。

**Q: 指定した `FontFamily`（例: "Arial"）が対象マシンにインストールされていない場合はどうなりますか？**  
A: Word は透かし用にデフォルトフォントにフォールバックするため、テキストは表示されますが、意図したスタイルとは異なる見た目になる可能性があります。

**Q: 新規作成ではなく、既存の `.docx` ファイルに透かしを追加することは可能ですか？**  
A: `Document document = new Document("Existing.docx");` で既存ファイルをロードし、`TextWatermarkOptions` を構成して、示されたように `document.Watermark.SetText` を呼び出します。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}