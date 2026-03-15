---
category: general
date: 2026-03-14
description: Aspose.Words を使用して docx から画像を抽出しながら、Word を Markdown に素早く変換します。開発者向けのステップバイステップ
  C# サンプル。
draft: false
keywords:
- convert word to markdown
- extract images from docx
- Aspose.Words C#
- markdown conversion tutorial
- docx image handling
language: ja
og_description: Aspose.Words を使用して Word を Markdown に変換し、docx から画像を抽出します。手間のかからない変換のために、この詳細ガイドに従ってください。
og_title: Word を Markdown に変換 – 完全 C# チュートリアル
tags:
- C#
- Aspose.Words
- Markdown
- Document Conversion
title: Word を Markdown に変換 – 画像抽出付き完全ガイド
url: /ja/net/programming-with-markdownsaveoptions/convert-word-to-markdown-full-guide-with-image-extraction/
---

>}} keep.

Now produce final content with all translations.

Let's craft Japanese translations.

Be careful to keep markdown formatting exactly.

Proceed.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word を Markdown に変換 – 完全 C# チュートリアル

Word を **Markdown に変換** したいけれど、埋め込まれた画像をそのまま保持できるか不安だったことはありませんか？ あなたは一人ではありません。多くの開発者が、テキストは変換できても画像が消えてしまうという壁にぶつかります。朗報です！数行の C# と強力な Aspose.Words ライブラリさえあれば、**Word を Markdown に変換** しながら **docx から画像を抽出** することがスムーズに行えます。

このチュートリアルでは、NuGet パッケージのインストールから `.docx` ファイルの読み込み、Markdown セーバーの設定、画像をカスタムフォルダーに保存しリンクを書き換えるコールバックの実装まで、必要な手順をすべて解説します。最後には、使用可能な Markdown ファイルと、元の Word 文書から抽出されたすべての画像が入った整然とした `resources` ディレクトリが手に入ります。

## 学習内容

- C# プロジェクトに Aspose.Words for .NET を設定する方法。  
- 画像を保持しながら **Word を Markdown に変換** するために必要な正確なコード。  
- `ResourceSavingCallback` が **docx から画像を抽出** する際に不可欠な理由。  
- パス区切り文字や重複ファイル名などの一般的な落とし穴と回避策。  
- 生成された Markdown が正しくレンダリングされるかをすばやく確認する手順。

### 前提条件

| 要件 | 理由 |
|------|------|
| .NET 6.0 以降（または .NET Framework 4.7 以上） | Aspose.Words は両方をサポートしており、最新ランタイムの方がパフォーマンスが向上します。 |
| Visual Studio 2022（または任意の C# IDE） | デバッグやパッケージ管理が容易になります。 |
| NuGet 復元のためのインターネット接続 | ライブラリは公式フィードから取得されます。 |
| 画像 **と** テキストを含むサンプル `input.docx` | 画像抽出の動作を確認するために必要です。 |

追加のサードパーティツールは不要です—Aspose.Words がすべてを内部で処理します。

---

## 手順 1: NuGet で Aspose.Words をインストール

まず、プロジェクトに Aspose.Words パッケージを追加します。**Package Manager Console** を開き、以下を実行してください。

```powershell
Install-Package Aspose.Words
```

あるいは UI を使っても構いません：プロジェクトを右クリック → *Manage NuGet Packages* → “Aspose.Words” を検索 → **Install** をクリック。これでコア DLL と、後で必要になる `Saving` 名前空間がプロジェクトに追加されます。

> **プロのコツ:** バージョン（例: `22.12.0`）を固定しておくと、ライブラリが自動的に更新されて予期せぬ破壊的変更が起きるのを防げます。

---

## 手順 2: ソース Word ドキュメントを読み込む

ライブラリの準備ができたら、`.docx` ファイルを読み込みます。絶対パスでも相対パスでも、ソース文書を指すパスを指定してください。

```csharp
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word file. Replace the placeholder with your actual path.
Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

> **なぜ重要か:** `Document` は Word パッケージ全体を解析し、段落や表だけでなく、後で抽出する隠れた画像パーツにもアクセスできるようになります。

---

## 手順 3: Markdown 保存オプションを作成

Aspose.Words には `MarkdownSaveOptions` クラスが用意されており、変換の挙動を細かく調整できます。まずはインスタンスを作成し、後でコールバックを設定します。

```csharp
// Instantiate the options object.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
```

`ExportImagesAsBase64` を `false`（別ファイルとして画像を保存したいので）にしたり、必要に応じて `ExportHeadersFooters` を有効にしたりと、プロパティを調整できます。

---

## 手順 4: ResourceSavingCallback を設定 – DOCX から画像を抽出

本チュートリアルの核心です。`ResourceSavingCallback` は **各リソース**（画像、フォント等）を書き出す際に発火します。独自ハンドラを提供することで、画像の保存先と Markdown からの参照方法を自由に決められます。

```csharp
mdOptions.ResourceSavingCallback = new ResourceSavingCallback(
    (sender, args) =>
    {
        // 1️⃣ Define the folder where we’ll dump extracted pictures.
        string imageFolder = @"YOUR_DIRECTORY\resources\";

        // 2️⃣ Ensure the folder exists – create it on the fly.
        Directory.CreateDirectory(imageFolder);

        // 3️⃣ Preserve the original filename (e.g., Image1.png).
        string imageFileName = Path.GetFileName(args.FileName);
        string targetPath   = Path.Combine(imageFolder, imageFileName);

        // 4️⃣ Write the image stream to disk.
        using (FileStream fs = new FileStream(targetPath, FileMode.Create))
        {
            args.Stream.CopyTo(fs);
        }

        // 5️⃣ Tell the Markdown generator to use a relative path.
        //    This is the step that **extract images from docx** correctly.
        args.ResourceFileName = $"resources/{imageFileName}";
    });
```

### これが行うこと

1. `resources` サブフォルダーが存在しなければ作成します。  
2. 受け取った画像ストリームをそのフォルダーにコピーし、元のファイル名を保持して混乱を防ぎます。  
3. Markdown リンク（`![alt](resources/Image1.png)`）を更新し、レンダリング時に画像が正しく表示されるようにします。

> **エッジケース:** 画像名が重複すると、後に来た方が前のファイルを上書きします。回避策として、GUID をプレフィックスに付与したり、`Path.GetUniqueFileName`（カスタムヘルパー）を使用して保存前に名前を一意化できます。

---

## 手順 5: ドキュメントを Markdown として保存

コールバックを設定したら、最後は一行で Markdown ファイルを書き出します。

```csharp
// Choose the output path for the Markdown file.
string markdownPath = @"YOUR_DIRECTORY\output.md";

doc.Save(markdownPath, mdOptions);
```

この呼び出しが完了すると、以下が生成されます。

- `output.md` には Markdown テキストと `![Image1](resources/Image1.png)` のような画像参照が含まれます。  
- `resources` フォルダーには元の `.docx` から抽出されたすべての画像が格納されます。

---

## 手順 6: 結果を検証

`output.md` を任意の Markdown ビューア（VS Code、GitHub、Typora など）で開きます。元文書の見出し、リスト、**画像が正しくレンダリング**されているはずです。画像が欠けている場合は次を確認してください。

1. `resources` フォルダーに該当ファイルが存在するか。  
2. Markdown 内の相対パス（`resources/<filename>`）がフォルダー名と完全に一致しているか（Linux では大文字小文字を区別）。  
3. 画像ファイルが破損していないか—直接画像ビューアで開いて確認。

---

## 完全な動作例

以下はそのまま実行可能なサンプルプログラムです。`YOUR_DIRECTORY` を実際のフォルダー パスに置き換えてください。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class WordToMarkdown
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣ Load the source Word document.
        // -------------------------------------------------
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // -------------------------------------------------
        // 2️⃣ Prepare Markdown save options.
        // -------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // Export images as separate files, not Base64.
            ExportImagesAsBase64 = false
        };

        // -------------------------------------------------
        // 3️⃣ Set up the callback to **extract images from docx**.
        // -------------------------------------------------
        mdOptions.ResourceSavingCallback = new ResourceSavingCallback(
            (sender, args) =>
            {
                string imageFolder = @"YOUR_DIRECTORY\resources\";
                Directory.CreateDirectory(imageFolder);

                string imageFileName = Path.GetFileName(args.FileName);
                string targetPath = Path.Combine(imageFolder, imageFileName);

                using (FileStream fs = new FileStream(targetPath, FileMode.Create))
                {
                    args.Stream.CopyTo(fs);
                }

                // Update the reference used inside the Markdown file.
                args.ResourceFileName = $"resources/{imageFileName}";
            });

        // -------------------------------------------------
        // 4️⃣ Save as Markdown.
        // -------------------------------------------------
        string outputPath = @"YOUR_DIRECTORY\output.md";
        doc.Save(outputPath, mdOptions);

        Console.WriteLine("Conversion complete! Check output.md and the resources folder.");
    }
}
```

**期待される出力:** `output.md` を開くと次のようになります。

```markdown
# Sample Title

Here is some introductory text.

![Image1](resources/Image1.png)

More paragraphs…

![Diagram](resources/Diagram.jpg)
```

すべての画像がテキストと横並びで表示され、元の Word ファイルと同様のレイアウトになります。

---

## よくある質問と落とし穴

**Q: 抽出時に画像形式を変更できますか？**  
A: はい。コールバック内でストリームを再エンコード（例: PNG）してから書き出すことが可能です。`System.Drawing` や `ImageSharp` を使って `args.Stream` を操作してください。

**Q: Word 文書に SVG や EMF 画像が含まれている場合は？**  
A: Aspose.Words はほとんどのベクタ形式をデフォルトでラスタ PNG に変換します。元のベクタを保持したい場合は `mdOptions.ExportImageResolution` を設定し、ストリームを適切に処理してください。

**Q: .NET Core on Linux でも動作しますか？**  
A: 完全に動作します。`resources` パスはスラッシュ（`/`）または `Path.Combine` を使用してください。Linux のファイルシステムは大文字小文字を区別するため、フォルダー名の一貫性に注意しましょう。

**Q: フットノートやコメントを除外したい場合は？**  
A: 保存前に `mdOptions.ExportFootnotes` や `mdOptions.ExportComments` プロパティを調整すれば除外できます。

---

## 結論

ここまでで、**Word を Markdown に変換** しつつ **docx から画像を確実に抽出** する **完全なエンドツーエンド ソリューション** を学びました。Aspose.Words の `MarkdownSaveOptions` と `ResourceSavingCallback` を活用することで、テキスト変換と画像処理の両方を細かく制御できます。コードは自己完結型で、任意の .NET プラットフォームで動作し、既存のパイプラインに最小限の手間で組み込めます。

次のステップに進みませんか？ バルク変換の自動化、ASP.NET API への組み込み、または抽出した画像のサムネイル生成など、コア変換ロジックが確立すれば可能性は無限です。

---

![Word を Markdown に変換した例](convert-word-to-markdown.png "Word を Markdown に変換した例")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}