---
category: general
date: 2026-04-05
description: C#でDOCXをMarkdownに変換し、DOCXから画像を抽出する方法を学びましょう。フルコードとヒント付きのステップバイステップガイドです。
draft: false
keywords:
- convert docx to markdown
- extract images from docx
- Aspose.Words markdown conversion
- C# document processing
- image extraction C#
language: ja
og_description: Aspose.Words を使用して DOCX を Markdown に変換し、DOCX から画像を抽出します。コード、解説、ベストプラクティスのヒントを含む完全な
  C# チュートリアル。
og_title: DOCX を Markdown に変換 – C# で DOCX から画像を抽出
tags:
- Aspose.Words
- C#
- Markdown
- DOCX
- Image extraction
title: DOCX を Markdown に変換 – Aspose.Words で DOCX から画像を抽出
url: /ja/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-extract-images-from-docx-with-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX を Markdown に変換 – C# で DOCX から画像を抽出

DOCX を **Markdown に変換** したいが、出力で画像が消えてしまうことに悩んだことはありませんか？ あなただけではありません。多くのプロジェクトで Markdown バージョンはバージョン管理や静的サイトジェネレータに最適ですが、画像が残らず、リッチな文書が無味乾燥なテキストファイルになってしまいます。  

良いニュースです。数行の C# と Aspose.Words を使えば、**DOCX を Markdown に変換** しながら **DOCX から画像を自動的に抽出** できます。このガイドでは、全工程を順を追って解説し、各要素がなぜ重要かを説明し、画像フォルダーを整理する方法まで示します。

## 本チュートリアルで学べること

- 画像を含む DOCX の読み込み方法  
- 画像の保存先を決定するカスタム `IResourceSavingCallback` の定義方法  
- 抽出した画像を正しく参照できるように `MarkdownSaveOptions` を設定する方法  
- 重複画像名や PNG 以外の形式といったエッジケースへの対処法  
- 今日からすぐに実行できる、コピー＆ペースト可能な完全サンプルコード  

### 前提条件

- .NET 6.0 以上（API は .NET Core、.NET Framework、.NET 5+ でも動作）  
- **Aspose.Words for .NET** のライセンス（無料トライアルでもテスト可能）  
- C# と Visual Studio（またはお好みの IDE）に関する基本的な知識  

これらが揃っていれば、さっそく始めましょう。

---

## Step 1: Set Up the Project and Install Aspose.Words

まず、新しいコンソール アプリを作成します（既存のソリューションに統合しても構いません）。

```bash
dotnet new console -n DocxToMarkdownDemo
cd DocxToMarkdownDemo
dotnet add package Aspose.Words
```

> **Pro tip:** 最新の NuGet バージョン（2026年4月時点で 24.12）を使用すると、最新の Markdown エクスポート機能が利用できます。

---

## Step 2: Create a Callback to Save Images Where You Want Them

Aspose.Words は Markdown エクスポート中に書き出されるすべてのリソース（画像、SVG など）をフックできます。`IResourceSavingCallback` を実装することで、以下が可能になります。

1. Markdown ファイルの隣に配置するフォルダーを選択  
2. ユニークなファイル名を生成（既存画像を上書きしないように）  
3. 形式を決定（ここでは一貫性のため PNG に統一）

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Saves each image extracted from the DOCX into a dedicated folder
/// with a GUID‑based filename. The markdown file will reference the
/// new filename via <c>args.ResourceFileName</c>.
/// </summary>
class ImageResourceSaver : IResourceSavingCallback
{
    private readonly string _targetFolder;

    public ImageResourceSaver(string targetFolder)
    {
        _targetFolder = targetFolder;
        // Ensure the folder exists before we start writing files.
        Directory.CreateDirectory(_targetFolder);
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Generate a unique name to avoid collisions.
        string newFileName = $"img_{Guid.NewGuid():N}.png";

        // Full physical path where the image will be written.
        string fullPath = Path.Combine(_targetFolder, newFileName);

        // Tell the markdown exporter what name to use in the .md file.
        args.ResourceFileName = newFileName;

        // Provide a stream that writes to the desired location.
        args.Stream = new FileStream(fullPath, FileMode.Create);
    }
}
```

### なぜ GUID ベースの名前にするのか？

元の DOCX に同名の画像が複数含まれている場合、単純にコピー＆ペーストするとどちらかが上書きされてしまいます。`Guid.NewGuid()` を使用すれば一意性が保証されるため、特に自動化パイプラインで何度も変換を実行する際に便利です。

---

## Step 3: Load the DOCX and Wire Up the Markdown Options

次に、ドキュメントをメモリに読み込み、先ほど作成したコールバックを設定します。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------------
        // 1️⃣  Define paths – adjust these to match your environment.
        // --------------------------------------------------------------------
        string sourceDocx = @"C:\Docs\WithImages.docx";
        string outputMarkdown = @"C:\Docs\DocWithImages.md";
        string imagesFolder = @"C:\Docs\MarkdownResources";

        // --------------------------------------------------------------------
        // 2️⃣  Load the Word document.
        // --------------------------------------------------------------------
        Document doc = new Document(sourceDocx);

        // --------------------------------------------------------------------
        // 3️⃣  Configure MarkdownSaveOptions with our custom saver.
        // --------------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // This tells Aspose.Words to call ImageResourceSaver for each image.
            ResourceSavingCallback = new ImageResourceSaver(imagesFolder)
        };

        // --------------------------------------------------------------------
        // 4️⃣  Perform the conversion.
        // --------------------------------------------------------------------
        doc.Save(outputMarkdown, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown saved to: {outputMarkdown}");
        Console.WriteLine($"Images saved to:   {imagesFolder}");
    }
}
```

### コードの流れをステップごとに解説

| Step | Purpose |
|------|---------|
| **Define paths** | プロジェクトの柔軟性を保ち、再コンパイルせずに任意のフォルダーを指せるようにします。 |
| **Load the DOCX** | `Document` が Word ファイルを解析し、段落・表・画像などすべての要素にアクセスできるようにします。 |
| **Configure `MarkdownSaveOptions`** | `ResourceSavingCallback` が画像抽出のフックになります。これが無いと、Aspose.Words は画像を Base64 文字列として埋め込むか、設定次第で完全に除外してしまいます。 |
| **Save** | `doc.Save` が Markdown ファイルを書き出し、画像ごとにコールバックを呼び出します。 |

---

## Step 4: Verify the Output – What Should You See?

プログラムを実行したら `DocWithImages.md` を開きます。以下のような Markdown 画像リンクが生成されているはずです。

```markdown
![img_1a2b3c4d5e6f7g8h9i0j.png](MarkdownResources/img_1a2b3c4d5e6f7g8h9i0j.png)
```

そして `C:\Docs\MarkdownResources` フォルダー内に、GUID 名の PNG ファイルが多数作成されます。任意のファイルを開くと、元の DOCX に埋め込まれていた画像と同一であることが確認できます。

相対パスを尊重するビューア（例: VS Code のプレビュー、GitHub、静的サイトジェネレータ）で Markdown を開くと、画像は Word と同様に正しく表示されます。

### よくある落とし穴と回避策

| Symptom | Likely Cause | Fix |
|---------|--------------|-----|
| 画像が壊れたリンクとして表示される | `ResourceFileName` が設定されていないため、Markdown が存在しないファイルを指している | コールバック内で `args.ResourceFileName = newFileName;` を確実に設定 |
| PNG ファイルが巨大になる | 元画像が JPEG や BMP で、PNG へ変換したためサイズが増加 | `args.ResourceContentType` で元形式を検出し、拡張子を保持: `args.ResourceFileName = $"{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";` |
| 重複画像がまだ残る | 静的なファイル名を使用したため GUID が使われていない | GUID ロジックに戻すか、画像タイプごとにカウンタを追加 |
| `FileNotFoundException` がスローされる | DOCX のパスが間違っている、またはフォルダーに読み取り権限がない | パスを確認し、適切なファイルシステム権限を付与 |

---

## Step 5: Advanced Tweaks (Optional)

### 5.1 Preserve Original Image Formats

出力画像の拡張子を元のままにしたい場合は、コールバックを次のように変更します。

```csharp
public void ResourceSaving(ResourceSavingArgs args)
{
    string ext = Path.GetExtension(args.ResourceFileName).ToLowerInvariant();
    // Default to .png if Aspose couldn't determine an extension.
    if (string.IsNullOrEmpty(ext)) ext = ".png";

    string newFileName = $"img_{Guid.NewGuid():N}{ext}";
    string fullPath = Path.Combine(_targetFolder, newFileName);
    args.ResourceFileName = newFileName;
    args.Stream = new FileStream(fullPath, FileMode.Create);
}
```

### 5.2 Embed Images as Base64 (When You *Don’t* Want Separate Files)

単一ファイルの Markdown が欲しいケース（例: メール送信時）では、以下のオプションに変更します。

```csharp
mdOptions.ImagesFolder = string.Empty; // disables external folder
mdOptions.ExportImagesAsBase64 = true;
```

ただし、**extract images from DOCX** がほとんどの静的サイトワークフローの主目的であるため、フォルダー方式が一般的に推奨されます。

---

## Full Working Example (Copy‑Paste Ready)

以下は 1 ファイルにまとめた完全なプログラムです。パスを自分の環境に合わせて置き換え、実行してください。

```csharp
// ---------------------------------------------------------------
// Convert DOCX to Markdown – Extract Images from DOCX
// ---------------------------------------------------------------
// NuGet: Aspose.Words (>= 24.12)
// ---------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class ImageResourceSaver : IResourceSavingCallback
{
    private readonly string _targetFolder;
    public ImageResourceSaver(string targetFolder) => Directory.CreateDirectory(_targetFolder = targetFolder);

    public void ResourceSaving(ResourceSavingArgs args)
    {
        string ext = Path.GetExtension(args.ResourceFileName).ToLowerInvariant();
        if (string.IsNullOrEmpty(ext)) ext = ".png";
        string newFileName = $"img_{Guid.NewGuid():N}{ext}";
        string fullPath = Path.Combine(_targetFolder, newFileName);
        args.ResourceFileName = newFileName;
        args.Stream = new FileStream(fullPath, FileMode.Create);
    }
}

class Program
{
    static void Main()
    {
        // 👉 Adjust these paths:
        string sourceDocx = @"C:\Docs\WithImages.docx";
        string outputMd  = @"C:\Docs\DocWithImages.md";
        string imgFolder = @"C:\Docs\MarkdownResources";

        // Load the DOCX.
        Document doc = new Document(sourceDocx);

        // Set up markdown options with our image saver.
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageResourceSaver(imgFolder)
        };

        // Perform conversion.
        doc.Save(outputMd, mdOptions);

        Console.WriteLine("✅ DOCX successfully converted to Markdown.");
        Console.WriteLine($"📄 Markdown: {outputMd}");
        Console.WriteLine($"🖼️ Images folder: {imgFolder}");
    }
}
```

`dotnet run` で実行します。コンソールに ✅ が表示されたら、Markdown ファイルを開き、画像が正しく表示されていることを確認してください。

---

## Conclusion

これで **DOCX を Markdown に変換し、C# で DOCX から画像を抽出する** 完全な本番環境向けソリューションが手に入りました。ガイド全体で主要キーワードが繰り返し登場するため、検索エンジンや AI アシスタントに対する関連性も高まります。  

コードは次の 4 ステップで完結します。

1. Word 文書をロード  
2. `IResourceSavingCallback` で全画像をフック  
3. ユニークな名前で予測可能なフォルダーに保存  
4. 画像を参照する Markdown を生成  

ここからは、例えば

- Plug

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}