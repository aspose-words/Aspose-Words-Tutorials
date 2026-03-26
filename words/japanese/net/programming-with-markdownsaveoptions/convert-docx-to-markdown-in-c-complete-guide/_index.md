---
category: general
date: 2026-03-25
description: Aspose.Words を使用して Word から画像を抽出しながら、DOCX を Markdown に素早く変換します。フルコードでステップバイステップ学べます。
draft: false
keywords:
- convert docx to markdown
- extract images from word
language: ja
og_description: Aspose.Words を使用して DOCX を Markdown に変換し、Word から画像を抽出します。すぐに実行できるソリューションの完全なチュートリアルをご覧ください。
og_title: C#でDOCXをMarkdownに変換する – ステップバイステップガイド
tags:
- Aspose.Words
- C#
- Markdown
title: C#でDOCXをMarkdownに変換する – 完全ガイド
url: /ja/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.WordsでDOCXをMarkdownに変換する

Word の埋め込み画像を保持したまま **DOCX を Markdown に変換** したいことはありませんか？同じ問題に直面した開発者は多く、Word のコンテンツを静的サイトジェネレータやドキュメントリポジトリに移行しようとするときに壁にぶつかります。  
良いニュースは、Aspose.Words for .NET がその重い作業を代行してくれ、さらに小さなコールバックを使えば **Word ファイルから画像を抽出** することもできるということです。

このチュートリアルでは、`.docx` を読み込み、Markdown ファイルとして保存し、すべての画像を専用フォルダーに書き出す実践的な例を順を追って解説します。最後まで読めば、任意の .NET プロジェクトに組み込めるコンソールアプリが完成します。

> **プロのコツ:** 画像が不要でテキストだけが欲しい場合は、`ResourceSavingCallback` を省略しても構いません。コードは依然としてクリーンな Markdown を生成します。

## 必要なもの

- **Aspose.Words for .NET**（最新バージョン、例: 24.12）。NuGet から取得できます: `Install-Package Aspose.Words`。
- **.NET 6.0** 以上（API は .NET Framework でも動作しますが、.NET 6 が最もパフォーマンスが高いです）。
- 任意のコンソールプロジェクトまたは C# ホスト環境。
- 画像が少なくとも1つ含まれる入力 Word ファイル（`input.docx`）―画像抽出の動作を確認するためです。

以上だけです。余計なライブラリや面倒なコマンドラインツールは不要です。さっそく始めましょう。

![convert docx to markdown example](images/convert-docx-to-markdown.png)

*Image alt text: convert docx to markdown example*

## Step 1 – プロジェクトを作成して Aspose.Words を追加

整理しやすいように、新しいコンソールアプリを作成します。

```bash
dotnet new console -n DocxToMarkdownDemo
cd DocxToMarkdownDemo
dotnet add package Aspose.Words
```

`Program.cs` を開き、自動生成されたコードをすべて削除します。後で完全なソリューションを貼り付けますが、まずはプロジェクトがビルドできることだけ確認してください。

## Step 2 – ソース DOCX を読み込む

最初に行うのは、Aspose.Words に Word ファイルを読み込ませることです。この操作は **高速** で、Word 本体を起動せずにドキュメント構造を解析します。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Path to your source document
string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");

// Load the DOCX into a Document object
Document doc = new Document(inputPath);
```

なぜ `Path.Combine` でパスを組み立てるのか？ これにより、Windows、macOS、Linux いずれの環境でもコードがポータブルになります。CI パイプラインに移行したときに便利です。

## Step 3 – リソースコールバック付き Markdown 保存オプションを設定

Aspose.Words に Markdown で保存させると、デフォルトでは画像が Base64 文字列として埋め込まれます。小さなアイコン程度なら問題ありませんが、写真など大きな画像になるとファイルサイズが膨れ上がります。そこで **リソース保存コールバック** を設定し、画像をディスクに書き出して Markdown のリンクを更新します。

```csharp
// Define where the Markdown and resources will live
string outputDir = Path.Combine("YOUR_DIRECTORY", "Output");
string resourcesDir = Path.Combine(outputDir, "Resources");

// Ensure directories exist
Directory.CreateDirectory(outputDir);
Directory.CreateDirectory(resourcesDir);

// Create Markdown options and plug in the callback
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceSaver(resourcesDir)
};
```

`resourcesDir` をコールバックのコンストラクタに渡している点に注目してください。これによりパスロジックがコールバック本体から切り離され、クラスの再利用性が向上します。

## Step 4 – リソース保存コールバックを実装

このコールバックは `IResourceSavingCallback` を実装します。Aspose.Words が画像を書き出すたびに `ResourceSavingArgs` オブジェクトが渡されます。ここで **保存先** と **一意なファイル名** を決め、エンジンにデフォルトの保存動作をスキップさせます。

```csharp
class MyResourceSaver : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyResourceSaver(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build a unique, deterministic file name
        string ext = Path.GetExtension(args.FileName);          // e.g., ".png"
        string fileName = $"img_{args.Index}{ext}";            // img_0.png, img_1.jpg, …

        // Full path on disk
        string filePath = Path.Combine(_resourcesFolder, fileName);

        // Write the image bytes
        using (FileStream fs = new FileStream(filePath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Update the Markdown URI so it points to the saved image
        args.Uri = $"Resources/{fileName}";

        // Tell Aspose.Words we handled the saving
        args.Cancel = true;
    }
}
```

**重要ポイント:** `args.Uri` を設定することで、生成された `.md` ファイル内で画像がどのように参照されるかを完全にコントロールできます。相対パス `Resources/img_0.png` は、VS Code、GitHub、静的サイトジェネレータのいずれでも正しく機能します。

## Step 5 – ドキュメントを Markdown として保存

最後に、Aspose.Words に Markdown ファイルを書き出すよう指示します。先ほど設定したコールバックが画像ごとに自動的に呼び出されます。

```csharp
// Destination Markdown file
string markdownPath = Path.Combine(outputDir, "output.md");

// Perform the conversion
doc.Save(markdownPath, mdOptions);
```

この行が完了すると、次のものが生成されます。

- `output.md` – 元の Word コンテンツをクリーンに変換した Markdown。
- `Resources/` フォルダー – DOCX から抽出されたすべての画像が格納されます。

## 完全動作サンプル

以下は **そのままコピペできる** 完全版プログラムです。`YOUR_DIRECTORY` を `input.docx` が置かれている絶対パスまたは相対パスに置き換えてください。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

class Program
{
    static void Main()
    {
        // ------------------------------------------------------------
        // 1️⃣  Define paths
        // ------------------------------------------------------------
        string baseDir = Path.Combine(Environment.CurrentDirectory, "DemoFiles");
        string inputPath = Path.Combine(baseDir, "input.docx");
        string outputDir = Path.Combine(baseDir, "Output");
        string resourcesDir = Path.Combine(outputDir, "Resources");

        // Create folders if they don't exist
        Directory.CreateDirectory(outputDir);
        Directory.CreateDirectory(resourcesDir);

        // ------------------------------------------------------------
        // 2️⃣  Load the DOCX
        // ------------------------------------------------------------
        Document doc = new Document(inputPath);

        // ------------------------------------------------------------
        // 3️⃣  Prepare Markdown options with a resource callback
        // ------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new MyResourceSaver(resourcesDir)
        };

        // ------------------------------------------------------------
        // 4️⃣  Save as Markdown
        // ------------------------------------------------------------
        string markdownPath = Path.Combine(outputDir, "output.md");
        doc.Save(markdownPath, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown file: {markdownPath}");
        Console.WriteLine($"Images folder: {resourcesDir}");
    }
}

// -----------------------------------------------------------------
// Callback that writes each image to the Resources folder
// -----------------------------------------------------------------
class MyResourceSaver : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyResourceSaver(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Create a deterministic file name like img_0.png
        string extension = Path.GetExtension(args.FileName);
        string fileName = $"img_{args.Index}{extension}";
        string filePath = Path.Combine(_resourcesFolder, fileName);

        // Persist the image bytes
        using (FileStream fs = new FileStream(filePath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Update the Markdown link to point to the saved image
        args.Uri = $"Resources/{fileName}";

        // Cancel default saving because we already wrote the file
        args.Cancel = true;
    }
}
```

### 期待される出力

任意の Markdown ビューアで `Output/output.md` を開くと、次のような内容が表示されます。

```markdown
# My Sample Document

Here is a paragraph that came from Word.

![Image 1](Resources/img_0.png)

Another paragraph with **bold** text.
```

`Resources` フォルダーには `img_0.png`、`img_1.jpg` など、元の `input.docx` に埋め込まれていた画像がそのまま保存されています。

## Frequently Asked Questions (FAQ)

**この方法は .doc ファイルでも使えますか？**  
はい。Aspose.Words は `.doc`、`.docx`、`.rtf` など多数のフォーマットを読み込めます。`inputPath` の拡張子を変更するだけで対応可能です。

**画像の URL を絶対パスにしたい場合は？**  
`args.Uri = $"Resources/{fileName}";` を例えば `args.Uri = $"https://mycdn.com/docs/{fileName}";` のように書き換えます。Markdown はリモートの場所を参照するようになります。

**画像の品質や形式を制御できますか？**  
コールバックは元の画像ストリームを受け取ります。PNG を JPEG に変換したい場合は、`System.Drawing.Image` でストリームを読み込み、再エンコードしたバイト列を書き出した後に `args.Uri` を設定すれば実現できます。

**`ResourceSavingCallback` はスレッドセーフですか？**  
Aspose.Words は各リソースに対してコールバックを**順次**呼び出すため、基本的にスレッドセーフです。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}