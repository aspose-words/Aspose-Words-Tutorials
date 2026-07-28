---
category: general
date: 2026-01-03
description: Word を Markdown に変換し、画像を base64 で埋め込むを一度で行う。Word を Markdown として保存する方法、Word
  から Markdown を生成する方法、そして base64 画像データ URI の使用方法を学びましょう。
draft: false
keywords:
- convert word to markdown
- embed images as base64
- save word as markdown
- base64 image data uri
- generate markdown from word
language: ja
og_description: Word を Markdown に変換し、画像を base64 データ URI として埋め込む。このステップバイステップのチュートリアルでは、Word
  を Markdown として保存し、Word から Markdown を生成する方法を示します。
og_title: Word を Markdown に変換 – Base64 画像埋め込みガイド
tags:
- Aspose.Words
- C#
- Markdown
title: Word を Markdown に変換 – 画像を Base64 で埋め込む
url: /ja/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word を Markdown に変換 – 画像を Base64 で埋め込む

## 必要なもの

- **.NET 6.0 以降**（NuGet パッケージを参照できるものなら何でも可）
- **Aspose.Words for .NET**（無料トライアルでテストは十分に可能です）
- いくつかの画像が入ったシンプルな `.docx` ファイル（ここでは `input.docx` と呼びます）
- お好みの IDE（Visual Studio、Rider、VS Code など好きなもの）

すでに揃っているなら、すばらしいです—さっそく始めましょう。まだの場合は、NuGet パッケージのインストールは 1 行で済みます。

```bash
dotnet add package Aspose.Words
```

## ステップ 1: Word ドキュメントを読み込む — **convert word to markdown** の開始点

まず `.docx` をメモリに読み込む必要があります。ここから変換の魔法が始まります。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word file that contains the images.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

> **なぜ重要か:**  
> ドキュメントを読み込むことで、Aspose はテキスト、スタイル、すべての埋め込みリソースに完全にアクセスできるようになります。このステップがなければ、変換できるものが何もありません。

## ステップ 2: MarkdownSaveOptions を設定し、Resource‑Saving コールバックを用意する

Aspose は、通常はディスクに書き込まれるすべてのリソース（画像など）をインターセプトできます。カスタム `IResourceSavingCallback` を提供することで、デフォルトのファイルベースの保存を **base64 image data uri** に置き換えることができます。

```csharp
// Configure Markdown save options so that images become Base64 URIs.
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceHandler()
};
```

### カスタムハンドラ – 画像を Base64 に変換する

以下が完全な実装です。`args.ResourceType == ResourceType.Image` をチェックし、次のように処理していることに注目してください。

1. 画像を `MemoryStream` に書き込む。  
2. バイト配列を Base64 文字列に変換する。  
3. `data:image/jpeg;base64,` URI を作成し、`args.Uri` に設定する。

```csharp
// Custom handler that converts each image resource to a Base64 data URI.
class MyResourceHandler : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Only process images – leave other resources untouched.
        if (args.ResourceType == ResourceType.Image)
        {
            // Prepare an in‑memory stream for the image.
            using (MemoryStream ms = new MemoryStream())
            {
                // Save the image using default JPEG options.
                args.ResourceData.Save(ms, ImageSaveOptions.DefaultJpeg);
                // Build the Base64 data URI.
                string base64 = Convert.ToBase64String(ms.ToArray());
                args.Uri = $"data:image/jpeg;base64,{base64}";
                // No need to keep the stream open after we set the URI.
                args.KeepResourceStreamOpen = false;
            }
        }
    }
}
```

> **プロのコツ:** ソースの Word が PNG を使用している場合は、`ImageSaveOptions.DefaultJpeg` を `ImageSaveOptions.DefaultPng` に置き換え、MIME タイプも（`image/png`）に変更してください。

## ステップ 3: ドキュメントを Markdown として保存 – 最終的な **save word as markdown** 手順

コールバックの準備ができたので、実際の保存はワンライナーです。

```csharp
// Save the document to a Markdown file. Images are already embedded.
document.Save("YOUR_DIRECTORY/output.md", markdownSaveOptions);
```

`output.md` を任意の Markdown ビューア（VS Code のプレビュー、GitHub など）で開くと、元の Word ファイルと同じテキストが表示され、画像は別ファイルなしでインラインに表示されます。

## 期待される出力

```markdown
# Sample Title

Here’s a paragraph that originally lived in Word.

![Embedded Image](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBxISEhU...
```

`![Embedded Image]` 行は **base64 image data uri** です—画像全体がその場でエンコードされています。余分なフォルダーも、壊れたリンクもありません。

## エッジケースと対処方法

| Situation | What to Do |
|-----------|------------|
| **大きな画像** – Base64 にするとサイズが約 33% 増加します | 変換前にリサイズを検討してください: `args.ResourceData.Save(ms, new ImageSaveOptions { ImageResolution = 72 })`。 |
| **非 JPEG 画像**（PNG、GIF） | `args.ResourceData.ImageType` で元のフォーマットを検出し、正しい MIME タイプ（`image/png`、`image/gif`）を設定してください。 |
| **非常に長いドキュメント**（数百枚の画像） | メモリ使用量に注意してください。RAM が不足した場合は、各画像を一時的にディスクへストリームすることもできます。 |
| **別個の画像ファイルが必要**（例: 静的サイト用） | ファイルとして残したい画像に対してコールバックから `false` を返し、Aspose にフォルダーへ書き出させてください。 |

## よくある質問（先に回答）

- **この方法は .doc ファイルでも動作しますか？** はい—Aspose.Words はレガシーな `.doc` ファイルも `.docx` と同様にロードできます。`new Document("myfile.doc")` を指定するだけです。
- **テーブルや脚注はどうなりますか？** Markdown エクスポーターで完全にサポートされています。テーブルは markdown テーブルに、脚注はインライン参照に変換されます。
- **markdown の方言を変更できますか？** `MarkdownSaveOptions` には `MarkdownVersion` プロパティ（CommonMark、GitHub など）があり、必要な構文がある場合は保存前に設定してください。

## 完全な、すぐに実行できるサンプル

以下はコンソールアプリにコピペできる完全なプログラムです。すべての using 文、ハンドラクラス、エラーハンドリングが含まれています。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToMarkdownDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            try
            {
                // 1️⃣ Load the source Word document.
                Document doc = new Document("YOUR_DIRECTORY/input.docx");

                // 2️⃣ Prepare Markdown options with our custom image handler.
                MarkdownSaveOptions options = new MarkdownSaveOptions
                {
                    ResourceSavingCallback = new MyResourceHandler()
                };

                // 3️⃣ Save as Markdown – images become Base64 URIs.
                string outputPath = "YOUR_DIRECTORY/output.md";
                doc.Save(outputPath, options);

                Console.WriteLine($"✅ Success! Markdown saved to {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Conversion failed: {ex.Message}");
            }
        }
    }

    // Custom callback that embeds images as Base64 data URIs.
    class MyResourceHandler : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            if (args.ResourceType == ResourceType.Image)
            {
                using (MemoryStream ms = new MemoryStream())
                {
                    // Preserve original format if you prefer PNG/GIF.
                    args.ResourceData.Save(ms, ImageSaveOptions.DefaultJpeg);
                    string base64 = Convert.ToBase64String(ms.ToArray());
                    args.Uri = $"data:image/jpeg;base64,{base64}";
                    args.KeepResourceStreamOpen = false;
                }
            }
        }
    }
}
```

プログラムを実行し、生成された `output.md` を開くと、Word ファイルの完璧な markdown レプリカが確認できます—**convert word to markdown** がこれまでになく簡単です。

## まとめ

私たちは、画像をインラインに保ちながら **convert word to markdown** するという課題から始めました。ドキュメントを読み込み、`MarkdownSaveOptions` のコールバックを設定し、ファイルを保存することで、**save word as markdown** のクリーンな解決策を実現し、**base64 image data uri** 文字列を生成しました。これで **embed images as base64** の方法やエッジケースの対処、画像タイプごとの調整方法もわかります。

## 次にやること

- **markdown の代わりに HTML を生成** – `MarkdownSaveOptions` を `HtmlSaveOptions` に置き換え、同じコールバックを再利用します。  
- **複数ファイルをバッチ変換** – フォルダー上の `foreach` ループでロジックをラップします。  
- **CI パイプラインに統合** – 静的サイト向けにドキュメント生成を自動化します。

自由に実験し、画像品質を調整したり、独自のリソース処理（例: 画像を CDN にアップロードして URL を挿入）を追加したりしてください。Aspose.Words と少しの C# の工夫を組み合わせれば、可能性は無限です。

コーディングを楽しんで、あなたの markdown が常に完璧に表示されますように！

![convert word to markdown フロー図 – 画像を Base64 で埋め込む](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNjAwIiBoZWlnaHQ9IjQwMCIgdmlld0JveD0iMCAwIDYwMCA0MDAiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+PHJlY3Qgd2lkdGg9IjYwMCIgaGVpZ2h0PSI0MDAiIGZpbGw9IiNmZmYiIHN0cm9rZT0iI2NjYyIgLz48dGV4dCB4PSI1MCIgeT0iMjAwIiBmb250LXNpemU9IjM2IiBmaWxsPSIjMDAwIj5JbWFnZSBJbWFnZSBJbWFnZSBJbWFnZTwvdGV4dD48L3N2Zz4= "convert word to markdown フローダイアグラム")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}