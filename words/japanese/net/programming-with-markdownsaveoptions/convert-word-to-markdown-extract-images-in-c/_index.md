---
category: general
date: 2026-02-18
description: Aspose.Words を使用して Word を Markdown に変換し、docx から画像を抽出します。完全な C# の例で、Word
  から Markdown を生成する方法を学びましょう。
draft: false
keywords:
- convert word to markdown
- extract images from docx
- how to extract images
- generate markdown from word
- how to convert docx to markdown
language: ja
og_description: Aspose.Words を使用して Word を Markdown に変換し、docx から画像を抽出します。このガイドでは、Word
  から Markdown をステップバイステップで生成する方法を示します。
og_title: Word を Markdown に変換 – C# で画像を抽出
tags:
- C#
- Aspose.Words
- Markdown
- Document Conversion
title: Word を Markdown に変換 – C# で画像を抽出する
url: /ja/net/programming-with-markdownsaveoptions/convert-word-to-markdown-extract-images-in-c/
---

unchanged.

Let's produce final content.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Convert Word to Markdown – Extract Images in C#

Word を **Markdown に変換** しながら、`.docx` ファイルからすべての画像を抽出したいと思ったことはありませんか？ あなたは一人ではありません。契約書やブログ記事、技術仕様書など、元が Word で書かれたものをクリーンな Markdown にしたい開発者は多くいます。朗報です！ Aspose.Words for .NET を使えば、数行のコードで実現でき、Markdown ファイル *と* 元画像が入ったフォルダーが生成されます。

このチュートリアルでは、**Word から Markdown を生成**し、docx から画像を抽出し、すべてをディスクに保存する、実行可能な C# プログラムを順を追って解説します。最後まで読めば、**docx を markdown に変換**する方法、**docx から画像を抽出**する方法、そして自分のプロジェクトに合わせてプロセスを調整する方法がわかります。

## What You’ll Need

- **Aspose.Words for .NET**（v23.10 以降）。`Install-Package Aspose.Words` で無料トライアルの NuGet パッケージを取得できます。
- .NET 6+ SDK（最近のバージョンならどれでも可）。
- 少なくとも 1 枚の画像が含まれるサンプル `input.docx`。
- Markdown と画像資産を保存したいフォルダー。

他のサードパーティライブラリは不要です。以下のコードには必要な `using` ディレクティブがすべて含まれているので、コンソールアプリにコピペして **F5** で実行できます。

![Convert Word to Markdown example](/images/convert-word-to-markdown.png "convert word to markdown")

*画像代替テキスト: Word ファイルが画像付きの Markdown ファイルに変換される様子のイラスト。*

---

## Step 1: Load the Source Word Document

最初に Aspose.Words に変換したいファイルを指示します。`Document` は `.docx` 内のテキスト、表、画像などすべてへのゲートウェイです。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 👉 Step 1: Load the Word document that contains images.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document document = new Document(inputPath);
```

> **Why this matters:** Loading the document once keeps memory usage low and lets the library inspect the internal package structure, which is essential for later extracting images.

---

## Step 2: Tell Aspose.Words How to Save as Markdown

Aspose.Words には `MarkdownSaveOptions` クラスが用意されています。改行コードから外部リソース（画像など）の保存先フォルダーまで、すべてを制御できます。

```csharp
        // 👉 Step 2: Configure Markdown save options with a resource‑saving callback.
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
        {
            // The callback fires for each external resource (e.g., an image) that needs a file.
            ResourceSavingCallback = new ResourceSavingCallback(args =>
            {
                // 👉 Step 3 inside the callback: decide where and how to store each image.
                string resourceFolder = @"YOUR_DIRECTORY\markdown-resources";
                Directory.CreateDirectory(resourceFolder); // creates if it doesn’t exist

                // Give each image a unique name to avoid collisions.
                string uniqueFileName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.FileName)}";
                args.FileName = Path.Combine(resourceFolder, uniqueFileName);

                // Optional: you could compress PNGs here by manipulating args.Stream.
            })
        };
```

> **Why a callback?** The `ResourceSavingCallback` gives you full control over the file name and location of each extracted image. Without it, Aspose would dump everything into the same folder with generic names, which can be messy for larger projects.

---

## Step 3: Save the Document as Markdown

オプション設定が完了したら、保存はワンライナーです。ライブラリが段落、見出し、リスト、表を変換し、コールバックのおかげで各画像を指定フォルダーに書き出します。

```csharp
        // 👉 Step 4: Save the document as a Markdown file.
        string outputPath = @"YOUR_DIRECTORY\output.md";
        document.Save(outputPath, markdownOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown saved to: {outputPath}");
        Console.WriteLine($"Images extracted to: {Path.GetDirectoryName(outputPath)}\\markdown-resources");
    }
}
```

### Expected Result

- `output.md` には Markdown 構文が含まれます（例: `![Image](markdown-resources/img_1234.png)`）。
- `markdown-resources` フォルダーには元の Word ファイルから抽出されたすべての画像が一意の名前で格納されます。

任意の Markdown ビューア（VS Code、GitHub、静的サイトジェネレータなど）で `output.md` を開くと、元の Word のレイアウトと同じテキストと画像が軽量でウェブフレンドリーな形式で表示されます。

---

## Step 4: Common Variations & Edge Cases

### 4.1 Handling Existing Resource Folders

変換を複数回実行すると、古い画像が残ることがあります。実行前にフォルダーをクリアするガード句を入れると便利です。

```csharp
if (Directory.Exists(resourceFolder))
{
    foreach (var file in Directory.GetFiles(resourceFolder))
        File.Delete(file);
}
else
{
    Directory.CreateDirectory(resourceFolder);
}
```

### 4.2 Changing Image Formats

Web 最適化のためにすべての画像を JPEG にしたい場合、コールバック内でストリームを再エンコードできます。

```csharp
using (var img = System.Drawing.Image.FromStream(args.Stream))
{
    var jpegStream = new MemoryStream();
    img.Save(jpegStream, System.Drawing.Imaging.ImageFormat.Jpeg);
    jpegStream.Position = 0;
    args.Stream = jpegStream;
    args.FileName = Path.ChangeExtension(args.FileName, ".jpg");
}
```

> **Pro tip:** `System.Drawing.Common` works on Windows; on Linux/macOS you might prefer `ImageSharp` for cross‑platform safety.

### 4.3 Preserving Table Styles

Word 文書でテーブルの書式設定が重要な場合、`MarkdownSaveOptions` を調整できます。

```csharp
markdownOptions.ExportTableColumnWidths = true;   // keeps column widths
markdownOptions.ExportTableBorders = true;       // adds markdown border syntax
```

### 4.4 Using a Different Output Directory

`Save` メソッドは任意の絶対パスまたは相対パスを受け取ります。CI パイプラインでは一時的なビルドフォルダーを指定すると便利です。

```csharp
document.Save(Path.Combine(Path.GetTempPath(), "doc.md"), markdownOptions);
```

---

## Frequently Asked Questions

**Q: Does this work with `.doc` (binary) files?**  
A: Yes. `new Document("file.doc")` automatically detects the format, so the same code handles both `.doc` and `.docx`.

**Q: What if the Word file contains embedded SVG images?**  
A: Aspose.Words extracts them as their original format. If you need raster versions, you’ll have to convert the SVG stream inside the callback (e.g., using `Svg.Skia`).

**Q: Can I skip the image extraction altogether?**  
A: Set `markdownOptions.ExportImagesAsBase64 = true;` to embed images directly in the markdown using data URIs—useful for single‑file README generation.

---

## Recap & Next Steps

We’ve just covered the full **convert word to markdown** workflow:

1. Load the `.docx`.
2. Configure `MarkdownSaveOptions` with a `ResourceSavingCallback`.
3. Save the document, letting the callback write each picture to a dedicated folder.

That’s the entire solution in under 50 lines of C#.  

If you’re ready to take it further, consider:

- **Generating a static site**: Feed the markdown into a generator like Hugo or Jekyll.
- **Batch processing**: Wrap the code in a `foreach` loop to handle dozens of files automatically.
- **Advanced image handling**: Resize, watermark, or convert images on the fly using the callback.

Feel free to experiment—swap out the callback logic, tweak save options, or integrate this into a larger document‑pipeline. The sky’s the limit, and now you have a solid foundation for any **generate markdown from word** project.

Happy coding, and may your markdown always be clean and your images always found!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}