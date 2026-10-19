---
title: Aspose.Words for .NET を使用してハイパーリンク付きコメントを追加し、PDF アノテーションとしてエクスポートする
weight: 110
limit:
description: Aspose.Words for .NET を使用して、Word ファイルにハイパーリンク付きコメントを追加し、PDF アノテーションとしてエクスポートする方法を学びます。
keywords: [Aspose.Words for .NET, add hyperlink comment, PDF annotation, export Word to PDF, comment with hyperlink, verify PDF output]
url: /net/working-with-comments/add-hyperlink-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET を使用して、Word ファイルにハイパーリンク付きコメントを追加し、PDF アノテーションとしてエクスポートする方法を学びます。
  headline: Aspose.Words for .NET を使用してハイパーリンク付きコメントを追加し、PDF アノテーションとしてエクスポートする
  type: TechArticle
- description: Aspose.Words for .NET を使用して、Word ファイルにハイパーリンク付きコメントを追加し、PDF アノテーションとしてエクスポートする方法を学びます。
  name: Aspose.Words for .NET を使用してハイパーリンク付きコメントを追加し、PDF アノテーションとしてエクスポートする
  steps:
  - name: 新しい空の Document オブジェクトと、それを操作するための DocumentBuilder を作成します。
    text: 新しい空の Document オブジェクトと、それを操作するための DocumentBuilder を作成します。
  - name: 今後追加するコメントのホストとなる、目に見えるテキスト行を書き込みます。
    text: 今後追加するコメントのホストとなる、目に見えるテキスト行を書き込みます。
  - name: Jane Doe が作成した Comment を作成し、ドキュメントの最初の段落に添付します。
    text: Jane Doe が作成した Comment を作成し、ドキュメントの最初の段落に添付します。
  - name: コメント内に段落を追加し、Aspose.Words Library のウェブサイトへの青色で下線付きのハイパーリンクを挿入します。
    text: コメント内に段落を追加し、Aspose.Words Library のウェブサイトへの青色で下線付きのハイパーリンクを挿入します。
  - name: ドキュメントがコメントを PDF アノテーションとしてレンダリングするように設定し、レイアウトを更新します。
    text: ドキュメントがコメントを PDF アノテーションとしてレンダリングするように設定し、レイアウトを更新します。
  - name: 生成された PDF を保存するために、現在のディレクトリに "Output" フォルダーを作成します。
    text: 生成された PDF を保存するために、現在のディレクトリに "Output" フォルダーを作成します。
  - name: PdfSaveOptions を使用して、準備したドキュメントを PDF ファイルとして保存します。
    text: PdfSaveOptions を使用して、準備したドキュメントを PDF ファイルとして保存します。
  - name: PDF ファイルが存在しデータが含まれていることを確認し、結果をコンソールに出力します。
    text: PDF ファイルが存在しデータが含まれていることを確認し、結果をコンソールに出力します。
  type: HowTo
- questions:
  - answer: '`InsertHyperlink` の第3パラメータは、リンクをフィールドとして扱うかどうかを指定します。`false` に設定すると、フィールドコードを必要とせず、PDF
      アノテーションで機能するプレーンなハイパーリンクが挿入されます。'
    question: '`InsertHyperlink` の第3引数（`false`）は何を制御しますか？'
  - answer: '`Save` を呼び出す前に `myDocument.LayoutOptions.CommentDisplayMode` を `CommentDisplayMode.ShowInBalloons`
      に設定します。これにより、PDF ではなく通常の Word コメントとしてバルーンが表示されます。'
    question: コメントを PDF アノテーションではなく、Word ドキュメント内でバルーンとして表示させるにはどうすればよいですか？
  - answer: はい。段落に追加する各 `Comment` はそれぞれ独自の `InsertHyperlink` 呼び出しを含めることができ、ドキュメントを保存するとすべてのハイパーリンクが個別の
      PDF アノテーションとして保持されます。
    question: 複数のコメントを追加した場合、各ハイパーリンクはエクスポートされた PDF で機能しますか？
  - answer: 生成された PDF を開き、コメントアノテーション（通常はメモアイコンで表示）を見つけてクリックし、コメントテキストを表示させた後、青色で下線付きのリンクをクリックします。リンク先の
      URL がウェブブラウザで開くはずです。
    question: PDF が生成された後、コメント内のハイパーリンクが実際に機能するかどうかを確認する方法は？
  type: FAQPage
images:
- /net/working-with-comments/add-hyperlink-comment/og-image.png
og_title: ハイパーリンクコメントの挿入と PDF へのエクスポート
og_description: Word のコメントにクリック可能なリンクを埋め込み、PDF アノテーションに変換する方法を学びます。
og_image_alt: Aspose.Words for .NET を使用して、Word ドキュメントにクリック可能なハイパーリンク付きコメントを追加し、PDF アノテーションとしてエクスポートする手順を示すガイド
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET を使用してハイパーリンク付きコメントを追加し、PDF アノテーションとしてエクスポートする
このチュートリアルでは、Word ドキュメントの作成、外部ウェブサイトへのクリック可能なハイパーリンクを含むコメントの挿入、コメントを PDF アノテーションとして表示する設定、ドキュメントの PDF へのエクスポート、そして生成された PDF ファイルの検証方法を紹介します。ステップバイステップのコードにより、リッチでリンク機能付きのコメントを追加し、PDF 変換時にそれらを保持できるため、読者とインタラクティブなメモを簡単に共有できます。

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-hyperlink-comment" >}}


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

**Q: `InsertHyperlink` の第3引数（`false`）は何を制御しますか？**  
A: `InsertHyperlink` の第3パラメータは、リンクをフィールドとして扱うかどうかを指定します。`false` に設定すると、フィールドコードを必要とせず、PDF アノテーションで機能するプレーンなハイパーリンクが挿入されます。

**Q: コメントを PDF アノテーションではなく、Word ドキュメント内でバルーンとして表示させるにはどうすればよいですか？**  
A: `Save` を呼び出す前に `myDocument.LayoutOptions.CommentDisplayMode` を `CommentDisplayMode.ShowInBalloons` に設定します。これにより、PDF ではなく通常の Word コメントとしてバルーンが表示されます。

**Q: 複数のコメントを追加した場合、各ハイパーリンクはエクスポートされた PDF で機能しますか？**  
A: はい。段落に追加する各 `Comment` はそれぞれ独自の `InsertHyperlink` 呼び出しを含めることができ、ドキュメントを保存するとすべてのハイパーリンクが個別の PDF アノテーションとして保持されます。

**Q: PDF が生成された後、コメント内のハイパーリンクが実際に機能するかどうかを確認する方法は？**  
A: 生成された PDF を開き、コメントアノテーション（通常はメモアイコンで表示）を見つけてクリックし、コメントテキストを表示させた後、青色で下線付きのリンクをクリックします。リンク先の URL がウェブブラウザで開くはずです。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}