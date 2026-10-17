---
title: Aspose.Words for .NET を使用して、Word ドキュメントの特定の段落に Comment を挿入する
weight: 210
limit:
description: Aspose.Words for .NET を使用して、Word ドキュメントの選択した段落に著者コメントを追加し、DOCX として保存するステップバイステップガイド。
keywords: [add comment Aspose.Words for .NET, insert comment Word document, comment author Aspose.Words, c# add comment to Word, save DOCX with comment]
url: /net/working-with-comments/add-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET を使用して、Word ドキュメントの選択した段落に著者コメントを追加し、DOCX として保存するステップバイステップガイド。
  headline: Aspose.Words for .NET を使用して、Word ドキュメントの特定の段落に Comment を挿入する
  type: TechArticle
- description: Aspose.Words for .NET を使用して、Word ドキュメントの選択した段落に著者コメントを追加し、DOCX として保存するステップバイステップガイド。
  name: Aspose.Words for .NET を使用して、Word ドキュメントの特定の段落に Comment を挿入する
  steps:
  - name: 新しい Document と DocumentBuilder をインスタンス化して、Word ファイルの作成を開始します。
    text: 新しい Document と DocumentBuilder をインスタンス化して、Word ファイルの作成を開始します。
  - name: DocumentBuilder.Writeln を使用して、文書に 3 つの個別の段落テキストを追加します。
    text: DocumentBuilder.Writeln を使用して、文書に 3 つの個別の段落テキストを追加します。
  - name: 文書に段落が 2 つ未満の場合は最初の段落にフォールバックし、2 番目の段落を安全に取得します。
    text: 文書に段落が 2 つ未満の場合は最初の段落にフォールバックし、2 番目の段落を安全に取得します。
  - name: 著者情報を含む Comment を作成し、テキストを設定して、選択した段落に添付します。
    text: 著者情報を含む Comment を作成し、テキストを設定して、選択した段落に添付します。
  - name: 変更されたドキュメントを現在のフォルダーにある 'sample.docx' という名前の DOCX ファイルとして保存します。
    text: 変更されたドキュメントを現在のフォルダーにある 'sample.docx' という名前の DOCX ファイルとして保存します。
  type: HowTo
- questions:
  - answer: '`if` ブロックは `paraList.Count` が 2 未満の場合、最初の段落（`paraList[0]`）にフォールバックするため、コメントは存在しない
      2 番目の段落ではなく、その単一の段落に添付されます。'
    question: ドキュメントに段落が 1 つしかない場合、コードはどう動作しますか？
  - answer: それらは `Comment` コンストラクタの第2引数と第3引数として渡されます – `new Comment(wordDoc, "Jordan",
      "JH", DateTime.Now)` – ここで "Jordan" が著者名、"JH" がイニシャルです。
    question: この例では、コメントの著者名とイニシャルはどのように設定されていますか？
  - answer: このスニペットでは、コメントは `AppendChild` によって `Paragraph` 全体にリンクされていますが、テキスト範囲にコメントを付けるには、対象の
      `Run` ノードの前後に `CommentRangeStart` と `CommentRangeEnd` を作成し、その間に `Comment` ノードを追加する必要があります。
    question: 段落全体ではなく、特定のテキスト部分にコメントを付けることはできますか？
  - answer: '`AppendChild` は `Comment` ノードを段落の子コレクションに追加し、Aspose.Words はドキュメント保存時に必要なコメント開始/終了マーカーを自動的に生成します。'
    question: コメントマーカーを手動で挿入する必要がありますか、それとも `AppendChild` が処理してくれますか？
  type: FAQPage
images:
- /net/working-with-comments/add-comment/og-image.png
og_title: Word の段落にコメントを挿入する
og_description: 特定の段落に著者コメントを追加し、Aspose.Words でファイルを DOCX としてエクスポートする。
og_image_alt: Aspose.Words for .NET を使用して、Word ドキュメントの段落にコメントを追加する方法を示すガイド。
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET を使用して、Word ドキュメントの特定の段落に Comment を挿入する
Aspose.Words for .NET を使用すると、プログラムから Word ファイルにコメントを追加できます。このチュートリアルでは、新しいドキュメントの作成、3 つの段落の挿入、2 番目の段落の検索、著者と日付情報を含むコメントの添付手順を解説します。最後に、コメントを保持したまま DOCX ファイルとしてドキュメントを保存します。

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-comment" >}}


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

**Q: ドキュメントに段落が 1 つしかない場合、コードはどう動作しますか？**  
A: `if` ブロックは `paraList.Count` が 2 未満の場合、最初の段落（`paraList[0]`）にフォールバックするため、コメントは存在しない 2 番目の段落ではなく、その単一の段落に添付されます。

**Q: この例では、コメントの著者名とイニシャルはどのように設定されていますか？**  
A: それらは `Comment` コンストラクタの第2引数と第3引数として渡されます – `new Comment(wordDoc, "Jordan", "JH", DateTime.Now)` – ここで "Jordan" が著者名、"JH" がイニシャルです。

**Q: 段落全体ではなく、特定のテキスト部分にコメントを付けることはできますか？**  
A: このスニペットでは、コメントは `AppendChild` によって `Paragraph` 全体にリンクされていますが、テキスト範囲にコメントを付けるには、対象の `Run` ノードの前後に `CommentRangeStart` と `CommentRangeEnd` を作成し、その間に `Comment` ノードを追加する必要があります。

**Q: コメントマーカーを手動で挿入する必要がありますか、それとも `AppendChild` が処理してくれますか？**  
A: `AppendChild` は `Comment` ノードを段落の子コレクションに追加し、Aspose.Words はドキュメント保存時に必要なコメント開始/終了マーカーを自動的に生成します。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}