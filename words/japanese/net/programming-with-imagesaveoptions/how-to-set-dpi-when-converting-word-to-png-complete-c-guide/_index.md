---
category: general
date: 2025-12-29
description: Aspose.Words を使用して Word を PNG に変換する際の DPI 設定方法を学びましょう。このステップバイステップのチュートリアルでは、高解像度
  PNG のエクスポートと画像解像度設定についても解説しています。
draft: false
keywords:
- how to set dpi
- convert word to png
- save word as png
- high resolution png export
- set image resolution png
language: ja
og_description: Aspose.Words を使用して Word を PNG に変換する際の DPI 設定方法。このガイドに従って高解像度 PNG のエクスポートと画像解像度の制御を行いましょう。
og_title: Word を PNG に変換する際の DPI 設定方法 – 完全 C# ガイド
tags:
- Aspose.Words
- C#
- Image Export
title: Word を PNG に変換するときに DPI を設定する方法 – 完全 C# ガイド
url: /ja/net/programming-with-imagesaveoptions/how-to-set-dpi-when-converting-word-to-png-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word を PNG に変換する際の DPI 設定方法 – 完全 C# ガイド

Word 文書を PNG に変換するときに **DPI を設定する方法** を考えたことはありますか？ プレゼンテーション用に鮮明なスクリーンショットが必要だったり、300 dpi の高解像度で印刷できる資産を生成したりする場合に役立ちます。どちらにしても、ここが正解です。このチュートリアルでは、Aspose.Words を使用してマルチページの `.docx` を高解像度 PNG 画像に変換し、画像解像度を設定してぼやけない出力を得る方法をステップバイステップで解説します。

**convert word to png**、**save word as png**、そして **high resolution png export** を簡単に実現するコツもご紹介します。外部ドキュメントは不要で、Visual Studio にコピペできる自己完結型の実行例です。

---

## 必要なもの

- **Aspose.Words for .NET**（最新バージョン、例: 24.9）  
- .NET 6+（または .NET Framework 4.7.2+） – 最近のランタイムであればどれでも可  
- PNG に変換したい Word ファイル（`MultiPage.docx`）  
- 開発環境 – Visual Studio、Rider、または VS Code で OK  

以上です。Aspose.Words 以外の NuGet パッケージは不要です。

---

## 手順 1: Word 文書を読み込む

まず最初に、Word ファイルのインメモリ表現が必要です。`Document` クラスがそれを担います。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the multi‑page document from disk
Document multiPageDoc = new Document("YOUR_DIRECTORY/MultiPage.docx");
```

> **ポイント:** 文書を読み込むことで `PageCount` にアクセスでき、後で Aspose に **すべてのページ** を PNG としてエクスポートさせる際に必要になります。

---

## 手順 2: DPI 設定付き ImageSaveOptions を構成する

次に、Aspose に PNG 出力を指示し、DPI を指定します。`ImageHorizontalResolution` と `ImageVerticalResolution` がその鍵です。

```csharp
// Create PNG save options and set the DPI to 300
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    // Export every page (0‑based index to PageCount‑1)
    PageSet = new PageSet(0, multiPageDoc.PageCount - 1),

    // Set image resolution – this is the “how to set dpi” part
    ImageHorizontalResolution = 300, // 300 DPI horizontally
    ImageVerticalResolution   = 300, // 300 DPI vertically

    // Give each page a friendly file name
    PageSavingCallback = (sender, args) =>
    {
        args.ImageFileName = $"Page_{args.PageIndex + 1}.png";
    }
};
```

> **プロのコツ:** 300 dpi は印刷向けグラフィックの事実上の標準です。画面表示だけで良い場合は 96 dpi にすればファイルサイズが大幅に削減できます。

---

## 手順 3: すべてのページを単一のタイル PNG（または個別ファイル）として保存する

Aspose では、すべてのページを 1 枚の巨大タイル PNG にまとめるか、ページごとに別ファイルとして書き出すかを選べます。以下の例は **単一タイル** アプローチですが、`ExportImagesAsSeparateFiles` フラグを切り替えるだけで、`PageSavingCallback` が個別ファイルを生成します。

```csharp
// Save the whole document as a tiled PNG file
multiPageDoc.Save("YOUR_DIRECTORY/Pages.png", imageSaveOptions);
```

ページごとに 1 ファイルが欲しい場合は、次のように設定してください。

```csharp
imageSaveOptions.ExportImagesAsSeparateFiles = true;
```

これでコールバックが `Page_#.png` という名前で各ページを保存します。

---

## 手順 4: 出力を確認する

コードを実行したら、`Pages.png`（または生成された `Page_#.png`）を任意の画像ビューアで開きます。元の Word ページと同じレイアウトの、鮮明で高解像度の画像が表示されるはずです。

- **解像度の確認:** 右クリック → プロパティ → 詳細 → 水平 DPI / 垂直 DPI → **300** と表示されていること  
- **サイズの確認:** 300 dpi では、一般的な A4 用紙 (8.27 in × 11.69 in) が約 2481 × 3508 ピクセルになるので、印刷に最適です

---

## よくある落とし穴と回避策

| 問題 | 発生理由 | 解決策 |
|------|----------|--------|
| **ぼやけた出力** | DPI がデフォルト (96) のまま | `ImageHorizontalResolution` **と** `ImageVerticalResolution` を明示的に設定 |
| **ページが抜ける** | `PageSet` が一部だけを対象にしている | `new PageSet(0, multiPageDoc.PageCount - 1)` を使用して全ページを含める |
| **ファイル名が衝突** | コールバックが未設定 | ユニークな名前を生成する `PageSavingCallback` を提供 |
| **ファイルサイズが大きすぎる** | 必要以上に 600 dpi 以上を指定 | 品質要件を満たす最低限の DPI を選択 |
| **巨大ドキュメントでメモリ不足** | 大きなタイル PNG をエクスポート | `ExportImagesAsSeparateFiles = true` に切り替えてページごとに書き出す |

---

## 上級編: PNG のバリエーション別エクスポート

**透過背景**や**色深度の変更**が必要なこともあります。Aspose.Words では `ImageSaveOptions` 内の `PngOptions` でこれらを調整できます。

```csharp
imageSaveOptions.PngOptions = new PngOptions
{
    // Enable transparency
    Transparency = true,

    // 8‑bit color depth (smaller file) or 24‑bit for full color
    BitDepth = 24
};
```

上記の DPI 設定と組み合わせれば、Web 用でも印刷用でも使える **high resolution png export** が実現します。

---

## 完全動作サンプル

以下はそのままコピペできる完成プログラムです。`YOUR_DIRECTORY` を実際のパスに置き換えてください。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/MultiPage.docx");

        // 2️⃣ Configure PNG export with 300 DPI
        ImageSaveOptions options = new ImageSaveOptions(SaveFormat.Png)
        {
            PageSet = new PageSet(0, doc.PageCount - 1),
            ImageHorizontalResolution = 300,
            ImageVerticalResolution = 300,
            // Optional: separate files per page
            // ExportImagesAsSeparateFiles = true,

            // 3️⃣ Friendly file names for each page
            PageSavingCallback = (sender, args) =>
            {
                args.ImageFileName = $"Page_{args.PageIndex + 1}.png";
            },

            // 4️⃣ High‑resolution PNG tweaks (transparent background, 24‑bit)
            PngOptions = new PngOptions
            {
                Transparency = true,
                BitDepth = 24
            }
        };

        // 5️⃣ Save – either a tiled PNG or separate files
        doc.Save("YOUR_DIRECTORY/Pages.png", options);

        Console.WriteLine("Conversion complete! Check YOUR_DIRECTORY for the PNG files.");
    }
}
```

実行すれば、**high resolution PNG export** が各ページごとに、設定した DPI で出力されます。

---

## FAQ（よくある質問）

**Q: 古い `.doc` ファイルでも動作しますか？**  
A: はい。Aspose.Words はフォーマットを抽象化しているので、`.doc`、`.docx`、`.rtf`、さらには `.odt` でも同じコードが使えます。

**Q: PNG ではなく JPEG で出力したい場合は？**  
A: `SaveFormat.Png` を `SaveFormat.Jpeg` に変更し、必要に応じて `JpegOptions` を調整すれば OKです。

**Q: 大判ポスター用に 600 dpi が必要な場合は？**  
A: `ImageHorizontalResolution = 600` と `ImageVerticalResolution = 600` を設定してください。ただし DPI が高いとピクセル数が急増し、メモリ使用量が増える点に注意。

**Q: 複数の Word ファイルを一括処理したい場合は？**  
A: 上記ロジックを `foreach (var file in Directory.GetFiles(folder, "*.docx"))` ループで回します。各 `Document` インスタンスは必ず破棄するか、`ImageSaveOptions` を再利用して効率化しましょう。

---

## まとめ

Aspose.Words を使って **Word を PNG に変換する際の DPI 設定方法** を解説し、**高解像度 PNG エクスポート** のコツと、**save word as png** を正確な画像解像度で実現するサンプルコードを提供しました。`ImageHorizontalResolution`、`ImageVerticalResolution`、そして必要に応じた `PngOptions` を調整すれば、印刷向けの高品質グラフィックから軽量な Web 用画像まで自在に生成できます。

次のステップとして、さまざまな DPI 値を試したり、個別ファイル出力に切り替えたり、PDF‑to‑PNG パイプラインと組み合わせてみてください。**set image resolution png** の考え方は他のフォーマットでも応用できるので、幅広い画像エクスポートシナリオに対応できるようになりました。

Happy coding, and may your PNGs always be razor‑sharp! 

![Word を PNG に変換する際の DPI 設定方法 – 例出力](/images/how-to-set-dpi-word-to-png.png "how to set dpi")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}