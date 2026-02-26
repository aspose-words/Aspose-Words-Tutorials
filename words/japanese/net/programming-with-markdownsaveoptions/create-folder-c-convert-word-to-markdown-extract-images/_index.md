---
category: general
date: 2026-02-26
description: フォルダーC#チュートリアルを作成し、WordをMarkdownに変換し、docxから画像を抽出し、ストリームをファイルにコピーする方法をすべて一つの手順で示す。
draft: false
keywords:
- create folder c#
- convert word to markdown
- extract images from docx
- copy stream to file
language: ja
og_description: Create folder C# チュートリアルでは、Word を markdown に変換し、docx から画像を抽出し、ストリームをファイルにコピーする方法を、分かりやすいコード例とともに解説します。
og_title: フォルダー作成 C# – Word を Markdown に変換して画像を抽出
tags:
- C#
- Aspose.Words
- Markdown
- Image Extraction
title: C#でフォルダーを作成 – WordをMarkdownに変換＆画像を抽出
url: /ja/net/programming-with-markdownsaveoptions/create-folder-c-convert-word-to-markdown-extract-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# フォルダー作成 C# – Word を Markdown に変換し画像を抽出

Word 文書を Markdown に変換しながら、すべての画像を取り出すために **フォルダー作成 C#** が必要だったことはありませんか？ 同じ悩みを抱えている人は多いです。多くの自動化パイプラインでは、ファイルシステムの操作、フォーマット変換、バイナリデータの処理を同時に行う必要があります。

このガイドでは、以下を実現する完全な実行可能サンプルを順を追って解説します。  
- ターゲットディレクトリの作成  
- `.docx` を Markdown に変換  
- 埋め込まれた画像をすべて抽出  
- **copy stream to file** ロジックで画像を希望の場所に保存  

外部スクリプトや手動ステップは不要です。純粋に C# と Aspose.Words ライブラリだけで完結します。

> **得られるもの**  
> * Markdown とアセット用に整ったフォルダー構造  
> * 抽出した画像を正しく参照した Markdown ファイル  
> * 任意の .NET プロジェクトに貼り付け可能なフルソースコード  

始める前に以下を用意してください。

* .NET 6.0（またはそれ以降）SDK がインストール済み – コードは最新の言語機能を使用しています。  
* **Aspose.Words for .NET** のライセンス（無料トライアルでもテストは可能）。  
* Visual Studio 2022 またはお好みのエディタ。  

画像を埋め込むのではなく抽出したい理由を考えると、静的サイトジェネレータが相対パスの画像付き Markdown を好む点が挙げられます。資産を専用フォルダーにまとめておくと、整理しやすくキャッシュにも優しいです。

---

## フォルダー作成 C# と出力構造の準備

まず最初に、すべてのファイルが格納されるディスク上の場所を用意します。このステップが **フォルダー作成 C#** の本体で、`Directory.CreateDirectory` により驚くほどシンプルに実現できます。このメソッドは冪等で、フォルダーが既に存在しても例外を投げません。余計なチェックが不要になるので便利です。

```csharp
using System;
using System.IO;

// Define the base output directory (adjust as needed)
string baseOutput = Path.Combine(Environment.CurrentDirectory, "output");

// Subfolders for markdown and images
string markdownFolder = Path.Combine(baseOutput, "markdown");
string imagesFolder   = Path.Combine(baseOutput, "MyImages");

// Ensure the folders exist
Directory.CreateDirectory(markdownFolder);
Directory.CreateDirectory(imagesFolder);

Console.WriteLine($"Created folders:\n • {markdownFolder}\n • {imagesFolder}");
```

**重要なポイント:**  
フォルダーを事前に作成しておくことで、後続の保存処理が `DirectoryNotFoundException` で失敗することを防げます。また、レイアウトが予測可能になります。例: `.md` ファイルは `output/markdown`、抽出した画像は `output/MyImages` に配置されます。

> **プロのコツ:** プログラムを何度も実行する場合は、画像フォルダーを最初にクリアするとよいでしょう（`Directory.GetFiles(imagesFolder).ToList().ForEach(File.Delete);`）。これで古いファイルが残るのを防げます。

---

## Aspose.Words を使って Word を Markdown に変換

ディレクトリツリーが整ったら、Word 文書を Markdown に変換します。Aspose.Words が重い処理をすべて担ってくれるので、OpenXML やサードパーティのコンバータをいじる必要はありません。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source DOCX (replace with your actual path)
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
var doc = new Document(inputPath);

// Configure markdown options and attach the image callback (we’ll define it later)
var mdOptions = new MarkdownSaveOptions
{
    // The callback will redirect each extracted image to our custom folder
    ResourceSavingCallback = new ImageSavingCallback(imagesFolder)
};

// Save the markdown file into the previously created folder
string markdownPath = Path.Combine(markdownFolder, "output.md");
doc.Save(markdownPath, mdOptions);

Console.WriteLine($"Word document converted to markdown at: {markdownPath}");
```

**内部で何が起きているか:**  
`MarkdownSaveOptions` が Aspose に対して Markdown 構文で出力するよう指示します。デフォルトでは、ライブラリは画像を Markdown ファイルと同じフォルダーに自動生成された名前で保存します。ここで `ResourceSavingCallback` を提供することで、その挙動を横取りし、**copy stream to file** を任意の場所に実行できます。

---

## DOCX から画像を抽出して保存

コールバッククラスは `IResourceSavingCallback` を実装します。内部で受け取る `ResourceSavingArgs` オブジェクトには、元の画像ストリームと提案されたファイル名が含まれます。これをディスクに書き込み、必要に応じてファイル名を変更し、Aspose に「自分で処理した」ことを通知します。

```csharp
using Aspose.Words.Saving;
using System.IO;

/// <summary>
/// Handles image extraction during markdown conversion.
/// </summary>
public class ImageSavingCallback : IResourceSavingCallback
{
    private readonly string _targetFolder;

    public ImageSavingCallback(string targetFolder)
    {
        _targetFolder = targetFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Ensure the target folder exists (defensive, though we created it earlier)
        Directory.CreateDirectory(_targetFolder);

        // Build a new, friendly file name – you can customize the pattern
        string newFileName = $"img_{Path.GetFileName(args.ResourceFileName)}";
        string fullPath = Path.Combine(_targetFolder, newFileName);

        // **Copy stream to file** – the core of the image extraction
        using (FileStream fs = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Tell Aspose to use our new path in the markdown reference
        args.ResourceFileName = Path.Combine("MyImages", newFileName);
        args.Handled = true; // Prevent default saving logic
    }
}
```

### 生成される Markdown の例

変換後の `output.md` には次のような行が含まれます。

```markdown
![Image 1](MyImages/img_picture1.png)
```

`args.ResourceFileName` を相対パスに変更したおかげで、Markdown は作成したフォルダーを直接指すようになります。これは静的サイトジェネレータが期待する形式です。

**エッジケースの対処:**  
*文書に同名画像が複数ある場合*、プレフィックス `img_` と元の名前を組み合わせるだけで衝突は回避できます。さらに絶対的な一意性が必要なら `Guid.NewGuid()` を付与するとよいでしょう。

---

## Copy stream to file – 画像データの取り扱い

`File.WriteAllBytes` だけでは済まない理由は **ストリームの柔軟性** にあります。`args.Stream` はメモリストリーム、ネットワークストリーム、その他任意の実装になる可能性があります。`CopyTo` を使うことで、.NET にバッファサイズの最適化を任せつつ、実装に依存しないコードが書けます。

汎用ストリームを別の場所にコピーしたいときのコンパクトなユーティリティメソッドを示します。

```csharp
/// <summary>
/// Copies any readable stream to a file on disk.
/// </summary>
public static void CopyStreamToFile(Stream source, string destinationPath)
{
    using (var file = new FileStream(destinationPath, FileMode.Create, FileAccess.Write))
    {
        source.CopyTo(file);
    }
}
```

`ImageSavingCallback` 内のインラインコピーをこの `CopyStreamToFile` 呼び出しに置き換えれば、単一責任のアプローチに整理できます。

---

## 完全な実行可能サンプル

すべての部品を組み合わせると、コマンドラインから実行できる自己完結型プログラムが完成します。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the folder structure
        string baseOutput = Path.Combine(Environment.CurrentDirectory, "output");
        string markdownFolder = Path.Combine(baseOutput, "markdown");
        string imagesFolder   = Path.Combine(baseOutput, "MyImages");
        Directory.CreateDirectory(markdownFolder);
        Directory.CreateDirectory(imagesFolder);

        // 2️⃣ Load the DOCX
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        var doc = new Document(inputPath);

        // 3️⃣ Set up markdown options with our image callback
        var mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageSavingCallback(imagesFolder)
        };

        // 4️⃣ Save as markdown
        string markdownPath = Path.Combine(markdownFolder, "output.md");
        doc.Save(markdownPath, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown: {markdownPath}");
        Console.WriteLine($"Images folder: {imagesFolder}");
    }
}

// ---------- ImageSavingCallback (same as earlier) ----------
public class ImageSavingCallback : IResourceSavingCallback
{
    private readonly string _targetFolder;
    public ImageSavingCallback(string targetFolder) => _targetFolder = targetFolder;

    public void ResourceSaving(ResourceSavingArgs args)
    {
        Directory.CreateDirectory(_targetFolder);
        string newFileName = $"img_{Path.GetFileName(args.ResourceFileName)}";
        string fullPath = Path.Combine(_targetFolder, newFileName);
        using (FileStream fs = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }
        args.ResourceFileName = Path.Combine("MyImages", newFileName);
        args.Handled = true;
    }
}
```

**期待される結果**

* `output/markdown/output.md` – 画像参照が `![Alt text](MyImages/img_picture1.png)` のようになった Markdown ファイル。  
* `output/MyImages/` – 元の `input.docx` に埋め込まれていた画像が PNG/JPEG 形式で 1 ファイルずつ保存されます。  

任意の Markdown ビューア（VS Code、GitHub、または静的サイトジェネレータ）で開けば、元の Word ファイルと同じ位置に画像が正しく表示されます。

---

## よくある質問 & トラブルシューティング

| Question | Answer |
|----------|--------|
| **対象フォルダーにすでにファイルがある場合はどうしますか？** | `Directory.CreateDirectory` は上書きしません。クリーンな実行が必要な場合は、プログラム開始時に既存ファイルを削除するロジックを追加してください。 |
| **画像が抽出されない場合の対処法は？** | `ResourceSavingCallback` が正しく登録されているか確認し、`args.Stream` が null でないことをチェックしてください。また、Aspose.Words のライセンスが有効かどうかも確認しましょう。 |
| **Markdown の画像パスが間違っているようです** | `args.ResourceFileName` に設定した相対パスが、Markdown ファイルの保存先と一致しているか確認してください。パスの区切り文字は OS に合わせて `Path.Combine` を使用すると安全です。 |
| **大容量の DOCX を処理するとメモリが足りなくなる** | ストリームベースで処理しているため、`CopyTo` のバッファサイズを調整したり、`using` ブロックで適切に解放することでメモリ使用量を抑えられます。 |
| **Aspose.Words の無料トライアルで制限がありますか？** | トライアル版は機能に制限がありますが、基本的な変換と画像抽出は可能です。商用利用や高度なオプションが必要な場合は正式ライセンスをご購入ください。 |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}