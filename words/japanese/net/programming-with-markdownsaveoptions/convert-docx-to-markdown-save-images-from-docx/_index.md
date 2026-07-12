---
category: general
date: 2026-06-27
description: Aspose.Words を使用して docx を markdown に変換し、画像を保存します。Word ファイルから画像を抽出し、Word
  文書を markdown としてエクスポートする方法を学びましょう。
draft: false
keywords:
- convert docx to markdown
- save images from docx
- extract images from word file
- export word document as markdown
language: ja
og_description: docx を markdown に変換し、画像を保存します。このガイドでは、Word ファイルから画像を抽出し、Word 文書を markdown
  としてエクスポートする方法を示します。
og_title: docx を markdown に変換し、docx から画像を保存
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Convert docx to markdown and save images from docx using Aspose.Words.
    Learn how to extract images from Word file and export Word document as markdown.
  headline: Convert docx to markdown & save images from docx
  type: TechArticle
- description: Convert docx to markdown and save images from docx using Aspose.Words.
    Learn how to extract images from Word file and export Word document as markdown.
  name: Convert docx to markdown & save images from docx
  steps:
  - name: How the code works
    text: '- **Loading the document** (`new Document(inputPath)`) gives us an in‑memory
      representation of the Word file, complete with all its parts—paragraphs, tables,
      and **images**. - **`MarkdownSaveOptions`** is where the magic happens. By attaching
      a `ResourceSavingCallback`, we gain full control over eve'
  - name: Quick sanity check
    text: '- Does the Markdown file open without errors in VS Code’s preview pane?
      ✅ - Are all pictures displayed when you view the file on GitHub? ✅ - Did the
      `Images` directory contain one file per picture from the original `.docx`? ✅'
  - name: What’s next?
    text: '- **Style the Markdown** – add a front‑matter block for Jekyll or Hugo.
      - **Automate the pipeline** – embed this code in an Azure DevOps or GitHub Action
      step. - **Handle tables and footnotes** – explore other `MarkdownSaveOptions`
      flags like `ExportTableBorderStyles`.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Markdown
- Word
title: docx を markdown に変換し、docx から画像を保存する
url: /ja/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-save-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# docx を markdown に変換し、docx から画像を保存する

Word ファイルに埋め込まれた画像を失わずに **docx を markdown に変換** する方法を考えたことはありませんか？ あなた一人ではありません—開発者はレポートのクリーンな Markdown バージョンが必要なことが多く、すべての図、ロゴ、スクリーンショットをそのまま保持したいと考えています。

このチュートリアルでは、**.docx を Markdown に変換**し、**docx から画像を任意のフォルダーに保存**し、強力な Aspose.Words ライブラリを使用して **Word ファイルから画像を抽出** する完全な実行可能サンプルを順を追って解説します。最後には、**Word ドキュメントを markdown にエクスポート** するコードを 1 行で書く方法もマスターできます。

## 必要なもの

- .NET 6+（または .NET Framework 4.7.2+）がマシンにインストールされていること  
- `Aspose.Words` への NuGet 参照（無料トライアルで問題なし）  
- 少なくとも 1 枚の画像を含むサンプル `input.docx`  
- お好みの IDE（Visual Studio、Rider、あるいは VS Code でも可）  

追加のサードパーティーツールは不要ですし、面倒なコマンドライン操作も不要です。純粋に C# コードだけです。

## docx を markdown に変換 – 概要

基本的な考え方はシンプルです：

1. ソースの Word ドキュメントを読み込む。  
2. 画像などの外部リソースの取り扱い方法を Aspose.Words に指示する。  
3. ライブラリに任せて Markdown として保存する。

以下が **完全に実行可能なプログラム** です。新しいコンソールプロジェクトにコピー＆ペーストして `Ctrl+F5` を押すだけで動作します。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // Step 1: Load the source document that contains images
        // -----------------------------------------------------------------
        string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");
        Document doc = new Document(inputPath);

        // -----------------------------------------------------------------
        // Step 2: Configure Markdown save options with a custom callback
        // -----------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // This callback runs for each external resource (images, CSS, etc.)
            ResourceSavingCallback = (sender, args) =>
            {
                // ---------------------------------------------------------
                // Step 3a: Save images to a custom folder using a unique name
                // ---------------------------------------------------------
                if (args.ResourceType == ResourceType.Image)
                {
                    string imageFolder = Path.Combine("YOUR_DIRECTORY", "Images");
                    Directory.CreateDirectory(imageFolder); // ensures folder exists

                    // Use a GUID so we never clash with existing files
                    string uniqueName = Guid.NewGuid().ToString() + args.Extension;
                    args.SavePath = Path.Combine(imageFolder, uniqueName);
                }

                // ---------------------------------------------------------
                // Step 3b: Skip CSS files – they aren't needed for plain Markdown
                // ---------------------------------------------------------
                if (args.ResourceType == ResourceType.CssStyleSheet)
                    args.Cancel = true;
            }
        };

        // -----------------------------------------------------------------
        // Step 4: Export the document to Markdown, applying the options
        // -----------------------------------------------------------------
        string outputPath = Path.Combine("YOUR_DIRECTORY", "output.md");
        doc.Save(outputPath, mdOptions);

        Console.WriteLine("Conversion complete! Markdown saved to " + outputPath);
        Console.WriteLine("Images extracted to " + Path.Combine("YOUR_DIRECTORY", "Images"));
    }
}
```

### コードの仕組み

- **Loading the document** (`new Document(inputPath)`) は、Word ファイルのすべてのパーツ（段落、テーブル、そして **images**）を含むインメモリ表現を提供します。  
- **`MarkdownSaveOptions`** が魔法の場所です。`ResourceSavingCallback` を設定することで、Aspose.Words が書き出そうとするすべての外部リソースを完全に制御できます。  
- コールバック内では `args.ResourceType == ResourceType.Image` をチェックすることで **Word ファイルから画像を抽出** します。コールバックは画像バイト列、元の拡張子、そして動的に作成したフォルダーへの `SavePath` プロパティを受け取ります。`Guid.NewGuid()` を使用すれば一意のファイル名が保証され、以前の実行結果を上書きしてしまう心配がありません。  
- **CSS をスキップ**（`ResourceType.CssStyleSheet`）します。プレーンな Markdown にはスタイルシートは不要なので、出力がすっきりします。  
- 最後に `doc.Save(outputPath, mdOptions)` が Markdown ファイルを書き出し、Word の構造を Markdown の等価表現に変換します（見出しは `#`、テーブルはパイプ区切りの行に変換など）。

## docx から画像を保存 – カスタムフォルダー戦略

カスタムフォルダーを使う理由は何でしょうか？ CI パイプライン用のドキュメントを生成するときに、Markdown ファイルとその資産をクリーンで再現性のあるレイアウトで隣り合わせに置きたいときに便利です。

```csharp
string imageFolder = Path.Combine("YOUR_DIRECTORY", "Images");
Directory.CreateDirectory(imageFolder);
```

**プロのコツ**：

- フォルダー パスはプロジェクト ルートからの **相対パス** にしておきましょう。こうすれば Markdown ファイルは相対リンク（`![Alt text](Images/abc123.png)`）で画像を参照でき、GitHub、GitLab、あるいは任意の静的サイトジェネレーターでも正しく表示されます。  
- **決定的な名前が必要** な場合（例：同じ画像は常に同じファイル名になるべき場合）は、GUID の代わりに画像バイト列のハッシュを使用します：`MD5.Create().ComputeHash(args.Data)`。小さな調整ですが、キャッシュに便利です。

## Word ファイルから画像を抽出 – エッジケース

1. **複数の画像形式** – Aspose.Words は PNG、JPEG、GIF、BMP、さらには SVG もサポートしています。`args.Extension` プロパティには正しい拡張子がすでに入っているので、拡張子を推測する必要はありません。  
2. **非常に大きな画像** – ソース文書に高解像度の写真が含まれている場合、生成されるファイルはかなりのサイズになることがあります。コールバック後に `System.Drawing` や `ImageSharp` を使って圧縮ステップを追加することを検討してください。  
3. **非表示画像** – Word はヘッダー/フッターやテキストボックス内にも画像を格納できます。コールバックはそれらすべてを検出するため、**表示されている画像だけでなくすべての画像** が抽出されます。本文の画像だけが欲しい場合は、`args.ImageIndex` でフィルタリングするか、`args.ImageType` を調べて条件分岐してください。

## Word ドキュメントを markdown にエクスポート – 結果の検証

プログラムを実行したら、任意の Markdown ビューアで `output.md` を開きます。以下のような内容が表示されるはずです：

```markdown
# My Report

Here is an introductory paragraph.

![Image1](Images/3f9c2d1e-7a5b-4c9e-9f6a-2b4e5d6f7a8b.png)

More text follows...
```

画像リンクが **Images** フォルダーを指していることに注目してください。これが **Word ドキュメントを markdown にエクスポート** に成功したことを示すサインです。

### 簡易チェック

- Markdown ファイルは VS Code のプレビューウィンドウでエラーなく開けますか？ ✅  
- GitHub 上でファイルを表示したときにすべての画像が正しく表示されますか？ ✅  
- `Images` ディレクトリには元の `.docx` に含まれる画像が 1 ファイルずつ入っていますか？ ✅  

これらのチェックのいずれかが失敗した場合は、`ResourceSavingCallback` のロジックと `YOUR_DIRECTORY` プレースホルダーが書き込み可能な場所を指しているかを再確認してください。

## よくある落とし穴と回避策

| Pitfall | Why it happens | Fix |
|---------|----------------|-----|
| **Images not appearing** | Callback never fired because `ResourceSavingCallback` wasn’t assigned. | Assign the callback **before** calling `doc.Save`. |
| **Empty Images folder** | `args.Cancel = true` was set for all resources inadvertently. | Only cancel CSS (`ResourceType.CssStyleSheet`), leave images untouched. |
| **File‑path too long on Windows** | Using deep nested folders plus GUIDs can exceed 260 characters. | Keep the folder shallow, or enable long‑path support in Windows 10+. |
| **Duplicate image names** | Using `DateTime.Now.Ticks` instead of GUID can collide on fast loops. | Stick with `Guid.NewGuid()` for uniqueness. |

## まとめ

私たちは **docx を markdown に変換**し、**docx から画像を保存**し、**Word ファイルから画像を抽出**しながら **Word ドキュメントを markdown にエクスポート** する方法を、クリーンで再現性のある手順で実演しました。すべては Aspose.Words の `ResourceSavingCallback` に依存しており、外部アセットを細かく制御できます。

### 次にやることは？

- **Markdown をスタイリング** – Jekyll や Hugo 用にフロントマターを追加。  
- **パイプラインを自動化** – このコードを Azure DevOps や GitHub Action のステップに組み込む。  
- **テーブルや脚注を処理** – `MarkdownSaveOptions` の他のフラグ（例：`ExportTableBorderStyles`）を調査。  

フォルダー構成を調整したり、画像圧縮を追加したり、`MarkdownSaveOptions` を `HtmlSaveOptions` に置き換えて出力形式を HTML に変更したりしても構いません。**convert docx to markdown** のしっかりした土台があれば、可能性は無限です。

Happy coding, and may your documentation always stay both beautiful **and** machine‑readable!

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、API の追加機能をマスターしたり、別の実装アプローチを自分のプロジェクトに取り入れたりするのに役立ちます。

- [Save Word Images – Convert Word to Markdown with Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [Convert Word to Markdown – Embed Images as Base64](/words/english/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/)
- [How to Rename Images When Converting DOCX to Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}