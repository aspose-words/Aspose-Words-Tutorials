---
category: general
date: 2026-03-17
description: C#でWordをMarkdownに変換し、DOCXから画像を抽出します。画像の抽出方法、コールバックの設定方法、そしてアセットフォルダにMarkdownを保存する方法を学びましょう。
draft: false
keywords:
- convert word to markdown
- extract images from docx
- how to extract images
- how to convert docx
language: ja
og_description: C#でWordをMarkdownに変換し、DOCXから画像を抽出する方法を学びましょう。ステップバイステップのコード、解説、スムーズな変換のためのヒントをご紹介します。
og_title: Word を Markdown に変換し、DOCX から画像を抽出する (C#) – 完全ガイド
tags:
- Aspose.Words
- C#
- Markdown
- Document Conversion
title: Word を Markdown に変換し、DOCX から画像を抽出する (C#)
url: /ja/net/programming-with-markdownsaveoptions/convert-word-to-markdown-extract-images-from-docx-c/
---

Now produce final content with translations.

Make sure to keep all shortcodes exactly as original.

Let's construct final output.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word を Markdown に変換し、DOCX から画像を抽出する (C#)

Ever needed to **Word を Markdown に変換** but got stuck on the images that magically disappear? You're not the only one. In many real‑world projects—think static site generators, documentation pipelines, or headless CMSes—you need the markdown text **と** the original pictures, neatly tucked away in an *assets* folder.  

In this tutorial you’ll see exactly **docx を変換する方法** to markdown **画像を抽出しながら** using Aspose.Words for .NET. We'll walk through setting up a resource‑saving callback, handling edge cases like duplicate filenames, and ending up with a clean folder structure ready for your static site builder.  

## 学べること

- `.docx` ファイルを読み込み、変換の準備を行う。  
- `IResourceSavingCallback` を実装して **DOCX から画像を抽出**。  
- `MarkdownSaveOptions` を設定し、Markdown が assets を正しく参照するようにする。  
- コードを実行し、`.md` ファイルと画像フォルダーの両方が期待通りに生成されることを確認する。  

**Prerequisites** – 必要条件は .NET 6+（または .NET Framework 4.7.2+）と Aspose.Words のライセンス（無料トライアルでこのデモは動作します）です。C# とファイル I/O の基本的な理解があるとスムーズですが、ガイドは自己完結型です。

![Convert Word to Markdown folder layout](https://example.com/convert-word-to-markdown.png "Convert Word to Markdown folder layout")

*変換後のフォルダー構成 – Markdown ファイルは、抽出されたすべての画像を格納する `assets` フォルダーの隣に配置されます。*

---

## ステップ 1: ソースドキュメントを読み込む (Word を Markdown に変換)

The first thing we do is read the `.docx` you want to turn into markdown. Aspose.Words abstracts away the low‑level OPC format, so a single line gets the job done.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

// Adjust these paths to match your environment.
string inputPath  = Path.Combine("YOUR_DIRECTORY", "input.docx");
string outputDir  = Path.Combine("YOUR_DIRECTORY", "output");

// Ensure the output folder exists.
Directory.CreateDirectory(outputDir);

// Load the DOCX file.
Document document = new Document(inputPath);
```

*Why this matters:* Loading the document early gives us a `Document` object that holds both the textual content **と** the embedded resources (images, charts, etc.). Without this step you can't **画像を抽出する方法** later on.

---

## ステップ 2: DOCX から **画像を抽出する方法** のコールバックを作成する

Aspose.Words calls your `IResourceSavingCallback` every time it needs to write a resource (like an image). By providing our own implementation we decide **どこに** the file lands and **どのように** the markdown will reference it.

```csharp
/// <summary>
/// Saves each extracted resource (image, video, etc.) into an "assets" sub‑folder
/// and rewrites the markdown reference to point at that relative path.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _outputDirectory;

    public MyMarkdownResourceCallback(string outputDirectory)
    {
        _outputDirectory = outputDirectory;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Build the assets folder path.
        string assetsFolder = Path.Combine(_outputDirectory, "assets");
        Directory.CreateDirectory(assetsFolder);

        // 2️⃣ Resolve potential filename collisions.
        string safeFileName = GetUniqueFileName(assetsFolder, args.ResourceFileName);

        // 3️⃣ Write the resource stream to disk.
        string assetPath = Path.Combine(assetsFolder, safeFileName);
        using (FileStream fs = new FileStream(assetPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // 4️⃣ Tell the markdown writer the *relative* path it should embed.
        args.ResourceFileName = Path.Combine("assets", safeFileName);
        args.KeepResourceStreamOpen = false; // we already closed it
    }

    // Helper: ensure we don't overwrite an existing file.
    private string GetUniqueFileName(string folder, string originalName)
    {
        string filePath = Path.Combine(folder, originalName);
        if (!File.Exists(filePath))
            return originalName;

        string nameWithoutExt = Path.GetFileNameWithoutExtension(originalName);
        string ext = Path.GetExtension(originalName);
        int counter = 1;

        while (File.Exists(filePath))
        {
            string candidate = $"{nameWithoutExt}_{counter}{ext}";
            filePath = Path.Combine(folder, candidate);
            counter++;
        }

        return Path.GetFileName(filePath);
    }
}
```

**重要ポイント**  

- **なぜ assets サブフォルダーが必要か？** 画像を `.md` ファイルから分離して保持することで、ほとんどの静的サイトジェネレータが期待するレイアウトを再現します。  
- **衝突処理** は、同じ画像が複数回出現したときに発生する「ファイルは既に存在します」例外を防ぎます。  
- `args.KeepResourceStreamOpen = false` を設定すると、ストリームを処理したことを Aspose に通知し、メモリリークを防止します。

---

## ステップ 3: コールバックを **MarkdownSaveOptions** に接続する

Now we tell Aspose.Words to use our callback whenever it writes a resource. This is the core of **docx を変換する方法** while preserving its media.

```csharp
// Instantiate the callback with the output directory.
var resourceCallback = new MyMarkdownResourceCallback(outputDir);

// Configure markdown options.
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // The callback does the heavy lifting for image extraction.
    ResourceSavingCallback = resourceCallback,

    // Optional: make the markdown more GitHub‑friendly.
    ExportImagesAsBase64 = false, // we want separate files, not embedded data URIs.
    ExportHeadersFooters = true,
    ExportDocumentProperties = false
};
```

*Why we set `ExportImagesAsBase64 = false`*: Base64‑encoded images bloat the markdown file and defeat the purpose of having a clean `assets` folder. By disabling it, the markdown will contain a simple `![](assets/image.png)` reference.

---

## ステップ 4: ドキュメントを Markdown として保存する

With everything prepared, the final step is a one‑liner that produces both the `.md` file and the images.

```csharp
string markdownPath = Path.Combine(outputDir, "output.md");

// Save the document.
document.Save(markdownPath, markdownOptions);
Console.WriteLine($"✅ Conversion complete! Markdown saved to: {markdownPath}");
Console.WriteLine($"📁 Extracted images are in: {Path.Combine(outputDir, "assets")}");
```

**期待される結果**  

- `output.md` は、各画像タグが `assets/<image_name>` を指す Markdown テキストを含みます。  
- `assets` フォルダーには、元々 `input.docx` に埋め込まれていた PNG、JPEG、または GIF ファイルが格納されます。  

`output.md` を任意の Markdown ビューア（VS Code、GitHub、MkDocs など）で開くと、画像が Word 文書に表示された通りにレンダリングされます。

---

## 一般的な落とし穴の対処 (FAQ)

### DOCX に重複した画像名が含まれる場合は？

Our `GetUniqueFileName` helper appends an incremental suffix (`image_1.png`, `image_2.png`, …) so no file gets overwritten.

### Aspose.Words のライセンスは必要ですか？

A trial works fine for experimentation, but for production you should purchase a license to remove the evaluation watermark and get full performance.

### 複数の Word ファイルをバッチで変換できますか？

Absolutely. Wrap the loading and saving code in a `foreach (var file in Directory.GetFiles(sourceFolder, "*.docx"))` loop, reusing the same `MyMarkdownResourceCallback` instance (or create a new one per file if you want isolated asset folders).

### 画像以外のリソース（例: 埋め込み PDF）はどうですか？

The callback receives **任意の** resource type. You can inspect `args.ResourceType` and decide whether to keep, ignore, or rename them.

### このアプローチは .NET Core と互換性がありますか？

Yes. The code above targets .NET 6, but you can downgrade to .NET Framework 4.7.2 by adjusting the project file. Aspose.Words supports both runtimes.

---

## プロのコツとベストプラクティス

- **assets フォルダーを整理整頓する** – バッチ変換後、空のプレースホルダーによって作成された可能性のある 0 バイトファイルを削除する簡易スクリプトを実行します。  
- **意味のあるファイル名を使用する** – 人が読める画像名が必要な場合は、`args.ResourceFileName` から元の `AltText`（存在する場合）を抽出し、ファイル名に組み込みます。  
- **バージョン管理** – リポジトリには Markdown のみを保存し、assets フォルダーは CI パイプラインの一部として生成できるようにして、リポジトリを軽量に保ちます。  
- **パフォーマンス** – 大規模なドキュメントの場合、`markdownOptions.SaveFormat = SaveFormat.Markdown;` を設定して出力をストリーミングし、まず `MemoryStream` に書き込むことを検討してください。

---

## 完全な動作例（コピー＆ペースト可能）

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

/// <summary>
/// Demonstrates converting a DOCX to Markdown while extracting images into an assets folder.
/// </summary>
class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1️⃣ Paths – adjust these to your environment.
        // -----------------------------------------------------------------
        string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");
        string outputDir = Path.Combine("YOUR_DIRECTORY", "output");
        Directory.CreateDirectory(outputDir);

        // -----------------------------------------------------------------
        // 2️⃣ Load the source document.
        // -----------------------------------------------------------------
        Document doc = new Document(inputPath);

        // -----------------------------------------------------------------
        // 3️⃣ Set up the resource‑saving callback.
        // -----------------------------------------------------------------
        var callback = new MyMarkdownResourceCallback(outputDir);

        // -----------------------------------------------------------------
        // 4️⃣ Configure Markdown options.
        // -----------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = callback,
            ExportImagesAsBase64 = false,
            ExportHeadersFooters = true,
            ExportDocumentProperties = false
        };

        // -----------------------------------------------------------------
        // 5️⃣ Save as Markdown.
        // -----------------------------------------------------------------
        string markdownFile = Path

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}