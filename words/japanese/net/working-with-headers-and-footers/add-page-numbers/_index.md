---
title: Aspose.Words for .NET を使用して Word 文書のフッターにページ番号を追加する
weight: 210
limit:
description: Aspose.Words for .NET を使用して、Word 文書のプライマリフッターに自動更新されるページ番号を追加します。
keywords: [Aspose.Words for .NET, add page numbers, word document footer, documentbuilder page numbers, automatic page numbering, c# aspose.words]
url: /net/working-with-headers-and-footers/add-page-numbers/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Aspose.Words for .NET を使用して、Word 文書のプライマリフッターに自動更新されるページ番号を追加します。
  headline: Aspose.Words for .NET を使用して Word 文書のフッターにページ番号を追加する
  type: TechArticle
- description: Aspose.Words for .NET を使用して、Word 文書のプライマリフッターに自動更新されるページ番号を追加します。
  name: Aspose.Words for .NET を使用して Word 文書のフッターにページ番号を追加する
  steps:
  - name: 新しい Document オブジェクトを作成し、それに紐付く DocumentBuilder を作成します。
    text: 新しい Document オブジェクトを作成し、それに紐付く DocumentBuilder を作成します。
  - name: builder のカーソルを最初のセクションのプライマリフッターへ移動します。
    text: builder のカーソルを最初のセクションのプライマリフッターへ移動します。
  - name: 段落の配置を中央に設定し、フッターテキストをセンタリングします。
    text: 段落の配置を中央に設定し、フッターテキストをセンタリングします。
  - name: ラベル "Page " を書き込み、現在のページ番号を表示する PAGE フィールドを挿入します。
    text: ラベル "Page " を書き込み、現在のページ番号を表示する PAGE フィールドを挿入します。
  - name: '" of " を書き込み、総ページ数を示す NUMPAGES フィールドを挿入します。'
    text: '" of " を書き込み、総ページ数を示す NUMPAGES フィールドを挿入します。'
  - name: 文書を .docx ファイルとして保存します。
    text: 文書を .docx ファイルとして保存します。
  type: HowTo
- questions:
  - answer: いいえ。`MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` は builder を *最初*
      のセクションのプライマリフッターだけに移動させるため、フィールドはそこにのみ挿入されます。
    question: 文書に複数のセクションがある場合、このコードはすべてのセクションのフッターにページ番号を追加しますか？
  - answer: 'フィールドを書き込む前に、`builder.ParagraphFormat.Alignment` を別の `ParagraphAlignment`
      値（例: `ParagraphAlignment.Right`）に設定します。'
    question: フッター内のページ番号段落の配置を変更するにはどうすればよいですか？
  - answer: '`InsertField` はフィールドコードとオプションのフィールド結果を受け取ります。`null` を渡すことで、Aspose.Words
      に実行時に Word が結果を計算させるよう指示します。'
    question: '`InsertField("PAGE", null)` の `null` 引数は何を表していますか？'
  - answer: はい。フィールドを挿入する前に `HeaderFooterType.FooterPrimary` を `HeaderFooterType.HeaderPrimary`（または別のヘッダータイプ）に置き換えます。
    question: 同じ "Page X of Y" フィールドをフッターではなくヘッダーに配置できますか？
  type: FAQPage
images:
- /net/working-with-headers-and-footers/add-page-numbers/og-image.png
og_title: Word フッターに自動ページ番号を挿入する
og_description: Aspose.Words for .NET を使用して、Word フッターにリアルタイムのページ番号を追加するステップバイステップのコードです。
og_image_alt: Aspose.Words for .NET を使用して、Word 文書のフッターに自動ページ番号を追加する方法を示すガイド
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET を使用して Word 文書のフッターにページ番号を追加する
このチュートリアルでは、Aspose.Words の Document と DocumentBuilder を使用して、Word 文書のプライマリフッターに自動更新されるページ番号を挿入する方法を示します。ページ番号をプログラムで追加することで、手動で編集することなくファイル全体で一貫したページ付けを実現できます。サンプルコードは .NET 環境で実行できる状態になっています。

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/add-page-numbers" >}}


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
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: 文書に複数のセクションがある場合、このコードはすべてのセクションのフッターにページ番号を追加しますか？**  
A: いいえ。`MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` は builder を *最初* のセクションのプライマリフッターだけに移動させるため、フィールドはそこにのみ挿入されます。

**Q: フッター内のページ番号段落の配置を変更するにはどうすればよいですか？**  
A: フィールドを書き込む前に、`builder.ParagraphFormat.Alignment` を別の `ParagraphAlignment` 値（例: `ParagraphAlignment.Right`）に設定します。

**Q: `InsertField("PAGE", null)` の `null` 引数は何を表していますか？**  
A: `InsertField` はフィールドコードとオプションのフィールド結果を受け取ります。`null` を渡すことで、Aspose.Words に実行時に Word が結果を計算させるよう指示します。

**Q: 同じ "Page X of Y" フィールドをフッターではなくヘッダーに配置できますか？**  
A: はい。フィールドを挿入する前に `HeaderFooterType.FooterPrimary` を `HeaderFooterType.HeaderPrimary`（または別のヘッダータイプ）に置き換えます。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}