---
category: general
date: 2026-02-13
description: C#でWordをMarkdownとして保存し、docxから画像を抽出する。docxをMarkdownに変換し、画像を保存し、リソースを整理する方法を学びましょう。
draft: false
keywords:
- save word as markdown
- convert docx to markdown
- how to extract images
- save images from docx
language: ja
og_description: 完全なC#サンプルでWordをMarkdownとして保存し、docxから画像を抽出します。docxをMarkdownに変換し、画像を保存し、すべてを整然と保ちます。
og_title: Word を Markdown に保存 – docx から画像を抽出
tags:
- Aspose.Words
- C#
- Markdown conversion
title: Word を Markdown として保存 – docx から画像を抽出
url: /ja/net/programming-with-markdownsaveoptions/save-word-as-markdown-extract-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word を markdown として保存 – docx から画像を抽出

元の *.docx* 内にあるすべての画像も保持しながら **save word as markdown** が必要になったことはありませんか？ 静的サイトジェネレータを構築しているか、あるいはレガシーな Word レポートを Git フレンドリーな形式に移行したいだけかもしれません。どちらにせよ、問題点は同じです：変換時に画像が失われるか、壊れたリンクの山ができてしまいます。

実は、カスタムパーサを書いたり *.docx* の ZIP 構造を手作業で探したりする必要はありません。Aspose.Words を使えば **convert docx to markdown** ができ、さらに **save images from docx** を任意のフォルダーに保存できます。このガイドでは、まさにそれを実行する完全な C# プログラムをステップバイステップで解説します。

このチュートリアルを終えると、以下が手に入ります：

* 元の Word のレイアウトをそのまま再現した markdown ファイル。
* 抽出されたすべての画像を含む “MarkdownResources” フォルダー（元の名前そのまま）。
* PDF、HTML、または Aspose がサポートする他のフォーマットにも適用できる再利用可能なコールバックパターン。

> **Prerequisites** – .NET 6+（または .NET Framework 4.7+）、有効な Aspose.Words ライセンス（または無料トライアル）、そして Visual Studio または VS Code が必要です。他の NuGet パッケージは不要です。

---

## チュートリアルでカバーする内容

解決策を論理的なステップに分解します：

1. **Load the source document** – 変換したい *.docx* を開きます。  
2. **Create a resource‑saving callback** – 画像を保存する場所を Aspose に指示します。  
3. **Configure `MarkdownSaveOptions`** – コールバックを markdown エクスポーターに設定します。  
4. **Save the markdown file** – たった一行で処理を実行します。  

途中で各要素が *why* 重要かを説明し、一般的な落とし穴（フォルダー権限がないなど）を指摘し、PNG のみ抽出やカスタム画像命名といったエッジケースに合わせてコードを調整する方法を示します。

## Step 1 – Load the source document

まず最初に、Word ファイルを指す `Document` インスタンスが必要です。Aspose は *.docx* の ZIP 形式を抽象化しているので、他のドキュメントオブジェクトと同様に扱えます。

```csharp
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Adjust the path to where your .docx lives.
const string inputPath = @"YOUR_DIRECTORY\input.docx";

Document doc = new Document(inputPath);
```

*Why this matters*: ファイルパスが間違っていると、Aspose は `FileNotFoundException` をスローし、パイプライン全体が停止します。定数（あるいは設定値）を使用すれば、コアロジックを変更せずにファイルを差し替えることが容易になります。

> **Pro tip** – ファイルがユーザー提供の場合は、ロード処理を try/catch でラップしてください。そうすればスタックトレースではなく、分かりやすいエラーメッセージを表示できます。

## Step 2 – Define a callback that decides where each image is saved

Aspose は `IResourceSavingCallback` を介して保存プロセスにフックできるようにしています。コールバックは外部リソース（画像、CSS など）ごとに `ResourceSavingArgs` オブジェクトを受け取ります。これを利用して、各画像を専用フォルダーに振り分け、元のファイル名を保持します。

```csharp
// Step 2: Define a callback that decides where each image is saved.
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build a path like: YOUR_DIRECTORY\MarkdownResources\image001.png
        string resourcesFolder = Path.Combine("YOUR_DIRECTORY", "MarkdownResources");
        Directory.CreateDirectory(resourcesFolder); // ensures the folder exists

        string imagePath = Path.Combine(resourcesFolder, args.ResourceFileName);

        // Tell Aspose where to write the file.
        args.ResourceFilePath = imagePath;
        args.Stream = new FileStream(imagePath, FileMode.Create, FileAccess.Write);
    }
}
```

*Why this matters*: コールバックがないと、Aspose は画像を markdown ファイルと同じフォルダーに配置し、汎用的な名前を付けます。パスを制御することでプロジェクトを整理し、名前衝突を防げます。

**Edge case** – 一部の Word ファイルでは同じ画像が複数回埋め込まれます。`args.ResourceFileName` には既にユニークなハッシュが含まれるため、上書きは起きません。連番の命名方式が好みなら、コールバック内で静的カウンタを保持すると良いでしょう。

## Step 3 – Configure Markdown save options to use the custom callback

ここでコールバックを markdown エクスポーターに結び付けます。`MarkdownSaveOptions` では見出しレベルやコードブロックのフェンス、画像を Base64 で埋め込むかどうか（今回は *not*）なども調整できます。

```csharp
// Step 3: Configure Markdown save options to use the custom callback.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Attach our resource‑saving logic.
    ResourceSavingCallback = new MyMarkdownResourceCallback(),

    // Optional: keep original line breaks for better diff‑friendliness.
    ExportHeadersFooters = false,
    ExportImagesAsBase64 = false
};
```

*Why this matters*: `ResourceSavingCallback` プロパティはドキュメントモデルとファイルシステムをつなぐ橋です。これを設定し忘れると画像が失われ、markdown は存在しないファイルを参照することになります。

## Step 4 – Save the document as Markdown, invoking the callback for each resource

最後に、Aspose に markdown ファイルを書き出すよう指示します。ライブラリは画像ごとにコールバックを呼び出し、画像ファイルを書き込み、markdown には相対リンクを挿入します。

```csharp
// Step 4: Save the document as Markdown, invoking the callback for each resource.
const string outputPath = @"YOUR_DIRECTORY\output.md";

doc.Save(outputPath, mdOptions);
```

コードが完了すると、ディスク上に以下の2つが作成されます：

1. **output.md** – 元の Word コンテンツを Markdown で表現したもの。  
2. **MarkdownResources/** – 抽出されたすべての画像を格納するフォルダー（例: `image001.png`, `image002.jpg`）。

**Verification** – 任意の markdown ビューアで `output.md` を開きます。`![image001.png](MarkdownResources/image001.png)` のような画像タグが表示されます。画像が正しく表示されれば成功です。

## 一般的なバリエーションと想定シナリオ

### 1. 画像を Base64 で埋め込みたいですか？

`MarkdownSaveOptions` の `ExportImagesAsBase64 = true` を設定します。これによりインラインのデータ URI を含む単一の markdown ファイルが生成されます—単一ファイルのドキュメントには便利ですが、ファイルサイズが大きくなります。

### 2. PNG 画像だけが必要ですか？

コールバックを拡張子でフィルタリングするように変更します：

```csharp
if (Path.GetExtension(args.ResourceFileName).Equals(".png", StringComparison.OrdinalIgnoreCase))
{
    // Save as before.
}
else
{
    // Skip non‑PNG resources.
    args.Cancel = true;
}
```

### 3. 実行時に出力フォルダーを変更する

フォルダー パスをコマンドライン引数または設定ファイルで受け取り、`resourcesFolder` を構築する際にその変数を使用します。これによりツールをプロジェクト間で再利用可能になります。

### 4. 大規模ドキュメントの処理

非常に大きな Word ファイルの場合、出力をストリーミングしてメモリへの全体ロードを回避することを検討してください。Aspose の `Document` クラスはすでに低メモリフットプリントで動作しますが、`LoadOptions` の `MemoryOptimization = MemoryOptimization.MemoryOptimized` を設定することもできます。

## 完全な実行可能サンプル

以下は新しいコンソールアプリ（`dotnet new console`）にコピー＆ペーストできる完全なプログラムです。`YOUR_DIRECTORY` を実際のパスに置き換え、Aspose.Words NuGet パッケージ（`dotnet add package Aspose.Words`）を追加することを忘れずに。

```csharp
// Program.cs
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace DocxToMarkdown
{
    // Step 2: Callback that saves each image into a dedicated folder.
    class MyMarkdownResourceCallback : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            string resourcesFolder = Path.Combine("YOUR_DIRECTORY", "MarkdownResources");
            Directory.CreateDirectory(resourcesFolder);

            string imagePath = Path.Combine(resourcesFolder, args.ResourceFileName);
            args.ResourceFilePath = imagePath;
            args.Stream = new FileStream(imagePath, FileMode.Create, FileAccess.Write);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 1: Load the source document.
            const string inputPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(inputPath);

            // Step 3: Configure the markdown options.
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new MyMarkdownResourceCallback(),
                ExportImagesAsBase64 = false,
                ExportHeadersFooters = false
            };

            // Step 4: Save as markdown.
            const string outputPath = @"YOUR_DIRECTORY\output.md";
            doc.Save(outputPath, mdOptions);

            Console.WriteLine("Conversion complete!");
            Console.WriteLine($"Markdown file: {outputPath}");
            Console.WriteLine($"Images folder: {Path.Combine("YOUR_DIRECTORY", "MarkdownResources")}");
        }
    }
}
```

**期待される出力**（コンソール）：

```
Conversion complete!
Markdown file: C:\Projects\MyDocs\output.md
Images folder: C:\Projects\MyDocs\MarkdownResources
```

`output.md` を開くと、`MarkdownResources` フォルダーを指す画像参照付きの markdown 構文が表示されます。すべての画像は元のファイル名を保持しているので、必要に応じて元の Word ファイルに遡って確認できます。

## 結論

ここでは Aspose.Words を使用して **save word as markdown** と同時に **extract images from docx** を行う方法を示しました。重要なポイントは `IResourceSavingCallback` です—これにより各リソースの保存先を完全に制御でき、markdown を整然と保ち、画像を整理できます。

単一の自己完結型プログラムで以下が可能です：

* 任意の *.docx* をクリーンな markdown に変換する（`convert docx to markdown`）。  
* すべての画像を保持する（`save images from docx`）。  
* 下流パイプライン向けに出力レイアウトをカスタマイズする。

次のステップは？同じコールバックパターンで HTML や PDF への変換を試すか、CI ジョブに組み込んで Word レポートを自動的に静的サイトリポジトリへ同期させてみてください。可能性は無限で、これで堅実な基盤が手に入りました。

質問や便利なカスタマイズを見つけたら、下のコメント欄にどうぞ—ハッピーコーディング！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}