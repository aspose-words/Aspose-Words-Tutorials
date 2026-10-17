---
category: general
date: 2026-02-18
description: ドキュメントからマークダウンを作成し、簡単な手順でドキュメントをマークダウンにエクスポートし、画像をサブフォルダーに保存します。C#でドキュメントをマークダウンとして保存する方法を学びましょう。
draft: false
keywords:
- create markdown from document
- export document to markdown
- save document as markdown
- save images to subfolder
language: ja
og_description: C#でドキュメントからMarkdownを作成し、画像をサブフォルダーに保存しながらドキュメントをMarkdownにエクスポートする方法を学びましょう。ステップバイステップのガイドに従ってください。
og_title: ドキュメントからマークダウンを作成 – 画像をエクスポートして保存
tags:
- C#
- Aspose.Words
- Markdown export
title: 文書からMarkdownを作成 – 画像をエクスポートして保存
url: /ja/java/document-conversion-and-export/create-markdown-from-document-export-and-save-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ドキュメントから Markdown を作成 – エクスポートと画像の保存

ドキュメントから **Markdown を作成** したいけれど、埋め込まれた画像をきれいに保つ方法が分からないことはありませんか？ あなただけではありません。多くのプロジェクトでレポート、マニュアル、ブログの下書きなどをプログラムで生成しますが、出力フォルダーに画像ファイルが散らばっているのは望ましいことではありません。

このチュートリアルでは、**ドキュメントを Markdown にエクスポート** し、すべての画像を専用の *md‑resources* サブフォルダーに保存し、最終的に **Aspose.Words for .NET API** を使用してドキュメントを Markdown として保存する、実行可能な完全なソリューションを順を追って解説します。最後まで読むと、任意の C# コードベースに組み込める単一メソッドと、エッジケースに対処するためのいくつかのヒントが手に入ります。

> **概要:**  
> • `MarkdownSaveOptions` の設定  
> • 画像をサブフォルダーにリダイレクトする `IResourceSavingCallback` の提供  
> • 設定したオプションで `Document.Save` を呼び出す  

コールバックを選択した理由が気になる方は、ステップバイステップでその根拠を説明しますので、ぜひ読み進めてください。

---

## 前提条件

- .NET 6.0 以降（コードは .NET Framework 4.7+ でも動作します）  
- Aspose.Words for .NET（NuGet パッケージ `Aspose.Words`）  
- ソースとなる `Document` オブジェクト（.docx、.pdf、.rtf など）  

追加のライブラリは不要です。コールバック API は Aspose.Words に組み込まれています。

---

## 手順 1: ドキュメントから Markdown を作成 – 保存オプションの設定

最初に行うのは `MarkdownSaveOptions` のインスタンス化です。このオブジェクトは、どの Markdown フレーバーを使用するか、画像を Base64 で埋め込むか、生成されたファイルをどこに配置するかといった変換の挙動を Aspose.Words に指示します。

```csharp
// Step 1: Initialize Markdown save options
var markdownSaveOptions = new Aspose.Words.Saving.MarkdownSaveOptions();
```

> **重要なポイント:**  
> `MarkdownSaveOptions` を明示的に作成しないと、ライブラリはデフォルト設定にフォールバックし、画像を Base64 文字列として Markdown ファイルに直接埋め込んでしまいます。これではファイルサイズが巨大になり、きれいな *images* フォルダーを持つという目的が失われます。

---

## 手順 2: ドキュメントを Markdown にエクスポートし、リソース処理を定義

次に、画像を **どこに保存するか** をセーバーに指示します。`IResourceSavingCallback` インターフェイスは、エクスポート中に検出されたすべてのリソース（画像、SVG など）に対してフックを提供します。コールバック内で行うことは次の通りです。

1. ターゲットフォルダー（`md-resources/`）が存在することを確認する。  
2. `OutputFileName` をフォルダー名と元のリソース名を結合したものに設定する。  

```csharp
// Step 2: Hook into the resource‑saving pipeline
markdownSaveOptions.ResourceSavingCallback = new Aspose.Words.Saving.IResourceSavingCallback(
    (args) =>
    {
        // All images will be placed in "md-resources" relative to the output .md file
        const string folder = "md-resources/";
        Directory.CreateDirectory(folder);          // Create folder if it doesn’t exist

        // Preserve the original file name (e.g., image001.png) but prepend the folder path
        args.OutputFileName = Path.Combine(folder, args.ResourceFileName);

        // Optional: you could also change the format here (e.g., convert BMP to PNG)
        // args.ResourceFileName = Path.ChangeExtension(args.ResourceFileName, ".png");
    });
```

> **よくある質問:** *画像を保存せずに埋め込みたい場合はどうすればいいですか？*  
> コールバックを省略するか、`args.OutputFileName = null;` と設定すれば、セーバーは自動的に画像を Base64 文字列として埋め込みます。

> **エッジケース:** 古いドキュメントに同名の画像が複数含まれていることがあります。上記のコールバックは既存ファイルを上書きしてしまいます。回避策として GUID を付加する方法があります。

```csharp
args.OutputFileName = Path.Combine(folder,
    $"{Path.GetFileNameWithoutExtension(args.ResourceFileName)}_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}");
```

---

## 手順 3: ドキュメントを Markdown として保存し、画像が正しく保存されたか確認

オプションの設定が完了したら、最終的な呼び出しは Markdown ファイルと関連画像をディスクに書き出すワンライナーです。

```csharp
// Step 3: Perform the actual export
string outputPath = @"C:\Exports\MyReport.md";
doc.Save(outputPath, markdownSaveOptions);
```

問題なく実行できれば、次のような出力が得られます。

- `MyReport.md` – ソースドキュメントの Markdown 表現。  
- `md-resources/` – `.md` ファイルと同じディレクトリに作成されるフォルダーで、抽出されたすべての画像が格納されます（例: `image001.png`, `image002.jpg`）。  

**サンプル Markdown スニペット**（Aspose.Words が自動生成）:

```markdown
# Sample Report

Here is an introductory paragraph.

![Sample image](md-resources/image001.png)

More text follows...
```

> **プロのコツ:** 生成された `.md` ファイルを VS Code や任意の Markdown プレビューアで開くと、相対パスがフォルダー構造と一致しているため画像が即座に表示されます。

---

## 完全な実行可能サンプル

以下は新規 .NET プロジェクトに貼り付けて実行できる、自己完結型コンソールプログラムです。簡単な Word ドキュメントを作成し、画像を追加したうえで **ドキュメントから Markdown を作成** し、画像をサブフォルダーに保存します。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a sample Word document with an image
        var doc = new Document();
        var builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, this is a test document.");
        builder.InsertImage("sample-image.png"); // Ensure this file exists next to exe

        // 2️⃣ Configure markdown export options (see Step 1 & 2 above)
        var markdownOptions = new MarkdownSaveOptions();
        markdownOptions.ResourceSavingCallback = new IResourceSavingCallback(
            (args) =>
            {
                const string folder = "md-resources/";
                Directory.CreateDirectory(folder);
                args.OutputFileName = Path.Combine(folder, args.ResourceFileName);
            });

        // 3️⃣ Save as markdown (Step 3)
        string outputFolder = Path.Combine(Environment.CurrentDirectory, "output");
        Directory.CreateDirectory(outputFolder);
        string markdownPath = Path.Combine(outputFolder, "ExportedDoc.md");
        doc.Save(markdownPath, markdownOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownPath}");
        Console.WriteLine("📂 Images saved in: md-resources/");
    }
}
```

**実行後に期待できる出力**:

```
✅ Markdown saved to: C:\MyProject\output\ExportedDoc.md
📂 Images saved in: md-resources/
```

`ExportedDoc.md` を開くと、画像参照が `md-resources/sample-image.png` を指しており、任意の Markdown ビューアで正しく表示されます。

---

## よくあるバリエーション

| シナリオ | コードの適用方法 |
|----------|----------------------|
| **画像のエクスポートをスキップ**（Base64 埋め込み） | `ResourceSavingCallback` を完全に省略するか、コールバック内で `args.OutputFileName = null;` を設定します。 |
| **画像形式を変更**（例: すべて PNG） | コールバック内で `args.ResourceFileName` を書き換え、必要に応じてストリームを変換して書き込みます。 |
| **カスタムフォルダー名** | `"md-resources/"` を任意の相対パスまたは絶対パスに置き換えます。 |
| **バッチで複数ドキュメントを処理** | `Document` オブジェクトのコレクションをループし、同じ `MarkdownSaveOptions` インスタンスを再利用します（ただしフォルダーはクリアするか、実行ごとに一意の名前にしてください）。 |

---

## 結論

本稿では **ドキュメントから Markdown を作成** し、**ドキュメントを Markdown にエクスポート**、さらに **画像をサブフォルダーに保存** する、クリーンなコールバック駆動アプローチを紹介しました。主なポイントは次の通りです。

- `MarkdownSaveOptions` を使用してエクスポートを細かく制御する。  
- `IResourceSavingCallback` を実装して画像を専用フォルダーに振り分け、Markdown をすっきり保つ。  
- 同様のパターンは SVG や音声など他のリソースタイプにも適用可能です（`args.ResourceType` を確認してください）。  

次のステップとして、**カスタム見出しスタイルで Markdown を保存** したり、`.md` ファイルとリソースを ZIP にまとめて返す ASP.NET Web API に組み込んだりすると良いでしょう。いずれにせよ、今やこの構成要素はあなたのツールボックスに加わりました。

質問や取り上げていないコーナーケースがあれば、下のコメント欄で教えてください。Happy coding!

---

![create markdown from document example](placeholder.png "create markdown from document example")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}