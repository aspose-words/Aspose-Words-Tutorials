---
category: general
date: 2026-04-28
description: Word を Markdown に変換する際に画像の相対パスを設定する方法、Word から画像を抽出する方法、エクスポートされた画像用のリソースフォルダーを作成する方法を学びましょう。
draft: false
keywords:
- markdown image relative path
- convert word to markdown
- extract images from word
- create resources folder
- export images from docx
language: ja
og_description: Word を Markdown に変換する際に、画像の相対パスを設定し、Word から画像を抽出して、エクスポートされた画像用の resources
  フォルダーを作成します。
og_title: Markdown画像の相対パス – WordをMarkdownに変換
tags:
- Aspose.Words
- C#
- Markdown
- Image Export
title: Markdown画像の相対パス – WordをMarkdownに変換
url: /ja/net/programming-with-markdownsaveoptions/markdown-image-relative-path-convert-word-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# markdown image relative path – Word を Markdown に変換

Word を markdown に変換する際に **markdown image relative path** が必要になったことはありませんか？ あなただけではありません。生成された Markdown がフラットなフォルダー内の画像を指してしまい、静的サイトや GitHub リポジトリで期待する相対リンク構造が壊れるという問題に多くの開発者が直面しています。

このチュートリアルでは、**Word から画像を抽出し**、**リソースフォルダーを作成**し、画像参照を書き換えてクリーンな *markdown image relative path* を使用する、完全なエンドツーエンドのソリューションを順を追って解説します。最後まで読むと、公開準備が整った `.md` ファイルと、元の `.docx` から抽出したすべての画像が整理された `Resources` ディレクトリが手に入ります。

> **得られるもの:** 単一の C# プログラム（外部スクリプト不要）、各パーツが重要な理由の明確な説明、そして自分のプロジェクトにコピーペーストできる実用的なヒント集です。

---

## 前提条件

- **.NET 6.0** 以降がインストールされていること（.NET Framework 4.7+ をターゲットにすることも可能ですが、新規プロジェクトには .NET 6 が最適です）。
- **Aspose.Words for .NET**（執筆時点での最新 NuGet パッケージ、バージョン 23.12）。以下でインストールします:
  ```bash
  dotnet add package Aspose.Words
  ```
- 画像を含む Word ドキュメント（例: `WithImages.docx`）を用意します。
- 出力する markdown と画像を保存したいフォルダー、例: `C:\Projects\MarkdownExport`。

追加のライブラリは不要です。その他はすべて Aspose.Words が処理します。

---

## Step 1: ソース Word ドキュメントをロードする（Word を markdown に変換する出発点）

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Adjust the path to point at your own .docx file.
        string sourcePath = @"C:\Projects\MarkdownExport\WithImages.docx";

        // Load the document – this is where Aspose.Words parses the Word file.
        Document doc = new Document(sourcePath);
        
        // The rest of the workflow follows…
    }
}
```

*Why this matters:* ドキュメントをロードすると内部ノードツリーにアクセスでき、後で **export images from docx** が必要になる画像パーツが含まれています。ロードに失敗すると以降の手順がすべて実行されないため、パスとファイル権限を再確認してください。

---

## Step 2: カスタムコールバックで `MarkdownSaveOptions` を設定する（リソースフォルダー作成の核心）

`ResourceSavingCallback` を使用すると、Aspose.Words が画像ファイルを書き込むたびに介入できます。コールバック内で **Resources サブフォルダーを作成**し、参照を調整して生成された markdown が *markdown image relative path* を使用するようにします。

```csharp
// Inside Main(), after loading the document:
string outputFolder = @"C:\Projects\MarkdownExport";
string resourcesFolder = Path.Combine(outputFolder, "Resources");

// Make sure the folder exists before we start saving anything.
Directory.CreateDirectory(resourcesFolder);

// Set up the Markdown save options.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Hook that runs for every image resource.
    ResourceSavingCallback = new MyMarkdownResourceCallback(resourcesFolder)
};

// Save the document as Markdown.
string markdownPath = Path.Combine(outputFolder, "Doc.md");
doc.Save(markdownPath, mdOptions);
```

`resourcesFolder` をコールバックのコンストラクタに渡していることに注目してください。これによりフォルダー パスが柔軟になり、コード全体で文字列をハードコーディングすることを防げます。

---

## Step 3: **リソースフォルダーを作成**しパスを書き換えるコールバックを実装する

```csharp
/// <summary>
/// Handles image extraction and path rewriting for markdown export.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyMarkdownResourceCallback(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Build the full file system path where the image will be stored.
        string targetPath = Path.Combine(_resourcesFolder, args.ResourceFileName);
        
        // 2️⃣ Ensure the directory exists (in case Aspose creates sub‑folders).
        Directory.CreateDirectory(Path.GetDirectoryName(targetPath));

        // 3️⃣ Write the image stream to disk.
        using (FileStream fileStream = File.Create(targetPath))
        {
            args.Stream.CopyTo(fileStream);
        }

        // 4️⃣ Update the markdown reference to use a relative path.
        // This is the crucial line that gives us the markdown image relative path.
        args.ResourceFileName = Path.Combine("Resources", args.ResourceFileName);
    }
}
```

*Why this works:* `args.Stream` には生の画像バイトが含まれています。これを `Resources` フォルダー内のファイルにコピーすることで **export images from docx** を安全に行います。その後、`args.ResourceFileName` を相対 URL（`Resources/image.png`）に置き換えます。後で Aspose.Words が markdown を書き出す際にその文字列がそのまま挿入され、目的の *markdown image relative path* が得られます。

---

## Step 4: 生成された Markdown を確認する（最終出力のイメージ）

`Doc.md` を任意のテキストエディタで開きます。以下のような内容が表示されるはずです:

```markdown
# Sample Heading

Here is an inline picture:

![Image 0](Resources/Image_0.png)

And a picture inside a table:

![Image 1](Resources/Image_1.jpg)
```

重要なのは、各画像参照が `Resources/...` を指していることです。これが求めていた **markdown image relative path** です。

![markdown image relative path example](example.png "markdown image relative path example")

*Tip:* 相対リンクを解釈するビューア（VS Code のプレビュー、GitHub、または静的サイトジェネレータ）で markdown を開くと、追加設定なしで画像が正しく表示されます。

---

## Step 5: よくある落とし穴とプロのコツ

| Issue | Why it happens | How to fix it |
|-------|----------------|---------------|
| 画像が `Resources` ではなくルートフォルダーに保存される | コールバックが設定されていない、または `args.ResourceFileName` が上書きされていないためです。 | `ResourceSavingCallback` が `doc.Save` を呼び出す **前に** 設定されているか再確認してください。 |
| ファイル名に不正な文字が含まれる | Word は画像にスペースや Unicode 記号を含む名前を付けることがあります。 | コールバック内で `Path.GetInvalidFileNameChars()` を使用して `args.ResourceFileName` をサニタイズしてください。 |
| 大きなドキュメントの処理に時間がかかる | 各画像が同期的に書き込まれているためです。 | .NET 6 以降でパフォーマンスが必要な場合は、非同期 I/O（`await args.Stream.CopyToAsync(fileStream)`）に切り替えてください。 |
| markdown を移動すると相対パスが壊れる | パスが markdown ファイルの位置に対して相対的であるためです。 | `Doc.md` と `Resources` フォルダーを同じ場所に保つか、コールバックで別の相対プレフィックス（例: `../assets`）を使用するよう調整してください。 |

---

## Step 6: ソリューションの拡張（さらに制御が必要な場合）

- **Multiple output formats:** `MarkdownSaveOptions` を `HtmlSaveOptions` や `PdfSaveOptions` に置き換えても同じコールバックを使用できます。Aspose.Words はフォーマットに関係なくすべての画像でコールバックを呼び出します。
- **Custom image naming:** 画像をリネームしたい場合（例: `figure-01.png`）、ファイルを書き込む前にコールバック内で `args.ResourceFileName` を変更してください。
- **Embedding images as Base64:** `args.ResourceFileName` をデータ URI（`data:image/png;base64,...`）に設定し、ファイル書き込みを省略します。単一ファイルの markdown エクスポートに便利です。

---

## 結論

これで、**Word を markdown に変換**し、**word から画像を抽出**し、**リソースフォルダーを作成**し、すべての画像に対してクリーンな **markdown image relative path** を保証する完全に機能する C# プログラムが手に入りました。コードは自己完結型で、最新の Aspose.Words バージョンで動作し、最小限の手間で任意の .NET プロジェクトに組み込むことができます。

次のステップは？ 生成された markdown を Hugo や Jekyll などの静的サイトジェネレータに流し込んでみるか、コールバックを試して画像を直接 Base64 文字列として埋め込んでみてください。SVG 画像や異常に大きなファイルなどのエッジケースに直面した場合は、上記の「よくある落とし穴」表を参照してください。小さな調整で問題は解決できることが多いです。

コーディングを楽しんで、markdown が常に正しいフォルダーを指すように！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}