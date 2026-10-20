---
category: general
date: 2026-03-25
description: Word ドキュメントを読み込み、欠落フォントを検出するための警告コールバックを作成します。Aspose.Words for .NET のフォント設定の構成方法を学びましょう。
draft: false
keywords:
- create warning callback
- load word document
- detect missing fonts
- configure font settings
language: ja
og_description: 欠落しているフォントを検出しながら Word ドキュメントを読み込むための警告コールバックを作成します。このガイドでは、Aspose.Words
  でフォント設定を構成する方法を示します。
og_title: 警告コールバックを作成 – Word文書を読み込み、欠落フォントを検出
tags:
- Aspose.Words
- C#
- Font handling
title: Word文書の読み込み時に警告コールバックを作成する – 完全ガイド
url: /ja/net/working-with-fonts/create-warning-callback-for-loading-word-documents-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 警告コールバックの作成 – Word 文書の読み込みと欠損フォントの検出

Word 文書を読み込む際に **警告コールバックを作成** したことがありますか？ なぜフォントが消えてしまうのか疑問に思ったことはありませんか？ あなただけではありません。多くのエンタープライズアプリでは、欠損フォントがレイアウトの災害を引き起こし、適切なコールバックがなければ問題に気付かないことがあります。  

良いニュースは？ Aspose.Words for .NET を使用すれば、**Word 文書の読み込み**、**欠損フォントの検出**、そして **フォント設定の構成** を数行のコードで実現できます。このチュートリアルでは、完全な実行可能サンプルを順に解説し、各要素がなぜ重要かを説明し、警告コールバックが正しく機能しているかを確認する方法を示します。

> **学べること**  
> * DOCX を読み込み、フォント置換を報告し、フォント検索パスをカスタマイズできる完全な C# プログラム。  
> * `FontSettings`、`LoadOptions`、`IWarningCallback` クラスの理解。  
> * 埋め込みフォントやシステム全体のフォントフォルダーなど、エッジケースの対処法。

---

## 前提条件

- .NET 6+（または .NET Framework 4.7.2+）と C# コンパイラ。  
- Aspose.Words for .NET NuGet パッケージ（`Install-Package Aspose.Words`）。  
- 少なくとも 1 つ、マシンにインストールされていないフォント（例：最小構成の Windows コンテナでの *Calibri Light*）を使用したサンプル Word ファイル（`input.docx`）。  
- C# コンソール アプリの基本的な知識。

追加のライブラリは不要です。すべて Aspose.Words 内に収められています。

---

## 手順 1: 欠損フォントを検出する警告コールバックを作成

このパズルの **主要** 要素は `IWarningCallback` を実装したクラスです。Aspose.Words は、警告が必要な状況（最も一般的なのはフォント置換）に遭遇したときにこのコールバックを呼び出します。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

/// <summary>
/// Handles warning events raised by Aspose.Words during document loading.
/// Specifically looks for FontSubstitution warnings and writes them to the console.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**この重要性** – コールバックがなければ、後からログをひっくり返すしかありません。リアルタイムで警告を処理すれば、ロードを中止するか、欠損フォントを代替フォントに置き換えるか、あるいは単に後でレビューできるようにログに残すかを即座に判断できます。

---

## 手順 2: カスタムフォント処理のために FontSettings を構成

実際に文書をロードする前に、システムに存在しないフォントをどこで探すか Aspose.Words に指示したい場合があります。ここで `FontSettings` が活躍します。

```csharp
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder (e.g., a shared network location) where your application stores its fonts.
fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);

// Optional: If you have a specific font to use as a universal fallback, set it here.
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

**この重要性** – 欠損フォントが格納されたフォルダーを Aspose.Words に指し示すことで、置換を回避できることが多くあります。どうしても不可能な場合は、*Arial* のような妥当なデフォルトを設定しておくと文書の可読性が保たれます。

---

## 手順 3: 設定した警告コールバックで Word 文書をロード

ここで全てを結びつけます。`LoadOptions` を作成し、`FontSettings` と `FontWarningHandler` を組み込み、最後に文書をロードします。

```csharp
// Prepare LoadOptions with both FontSettings and our warning handler.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontWarningHandler()
};

// Load the Word document. Replace the path with your actual file location.
Document document = new Document(@"C:\Docs\input.docx", loadOptions);

// At this point the warning handler has already printed any font‑substitution messages.
Console.WriteLine("✅ Document loaded successfully.");
```

**この重要性** – `LoadOptions` は文書の読み取り方法を構成する唯一の場所です。フォント設定と警告コールバックの両方を提供することで、欠損フォントが正しい場所で検索され **かつ** 直ちに報告されるようになります。

---

## 手順 4: 出力を検証 – 何が表示されるべきか？

コンソールからプログラムを実行します。`input.docx` がインストールされていないフォントを使用しており、かつ `C:\SharedFonts` にも存在しない場合、次のような出力が得られます。

```
⚠️ Font substitution detected: Font 'Roboto' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
```

すべてのフォントが利用可能な場合、警告行は一切表示されません。この即時フィードバックは、サイレントなフォント置換がブランドガイドライン違反につながる自動文書処理パイプラインにおいて非常に貴重です。

---

## 手順 5: よくある落とし穴とベストプラクティス

| 落とし穴 | 回避方法 |
|---------|----------|
| **`Aspose.Words.Fonts` の参照を忘れる** | ファイル冒頭に `using Aspose.Words.Fonts;` を必ず記述してください。これがないと型が見つからないエラーになります。 |
| **フォントフォルダーのパスが間違っている** | パスを再確認し、サブフォルダーがある場合は `recursive: true` を設定します。`Path.GetFullPath` を使ってデバッグすると便利です。 |
| **複数の警告コールバックを設定している** | Aspose.Words は最後に設定した `WarningCallback` だけを使用します。複雑なロジックが必要な場合は、単一のハンドラ内で委譲処理を行ってください。 |
| **UI のないサーバーで実行** | コンソール出力は問題ありませんが、Web アプリの場合は `Console.WriteLine` の代わりにファイルや監視システムへのログ出力を検討してください。 |
| **大容量文書でパフォーマンス低下** | 複数回ロードする場合は、`FontSettings` インスタンスを再利用してください。毎回作成するとコストがかかります。 |

**プロ tip:** 後で分析したい場合は、ハンドラ内で直接出力するのではなく `List<string>` に警告を蓄積しておきます。

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

その後、文書ロード後に `handler.Messages` を確認できます。

---

## 手順 6: ソリューションの拡張 – フォールバックフォントを埋め込むには？

欠損フォントを **PDF 出力時に埋め込む** ことで、下流のビューアが正確な外観を保持できるようにしたいケースがあります。文書をロードした後、埋め込みを強制できます。

```csharp
// Ensure the fallback font is embedded when saving to PDF.
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    EmbedStandardPdfFonts = false,
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};

document.Save(@"C:\Docs\output.pdf", pdfOptions);
Console.WriteLine("✅ PDF saved with embedded fonts.");
```

このスニペットは、**フォント設定の構成** アプローチをロード以外のシナリオにも拡張できることを示しています。

---

## 完全な実行可能サンプル

以下は新規コンソール アプリ プロジェクトにコピペできる、上記で説明したすべての要素を含む完全プログラムです。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    // Step 1 – Warning handler
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2 – Configure FontSettings
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);
            fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";

            // Step 3 – LoadOptions with warning callback
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontWarningHandler()
            };

            // Step 4 – Load the document
            string docPath = @"C:\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");

            // Optional: Save as PDF with embedded fonts
            var pdfOptions = new PdfSaveOptions
            {
                EmbedStandardPdfFonts = false,
                FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
            };
            doc.Save(@"C:\Docs\output.pdf", pdfOptions);
            Console.WriteLine("✅ PDF saved with embedded fonts.");
        }
    }
}
```

**期待される出力**（欠損フォントがある場合）:

```
⚠️ Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
✅ PDF saved with embedded fonts.
```

置換が発生しなければ、成功メッセージだけが表示されます。

---

## 結論

今回、Aspose.Words を使用して **Word 文書の読み込み時に欠損フォントを確実に検出する警告コールバック** を作成し、**フォント設定を構成** してライブラリがフォントを検索する場所とフォールバックを制御する方法を示しました。`FontSettings` と `LoadOptions` を組み合わせることで、フォント関連の問題を完全に可視化でき、サイレントなレイアウト不具合は過去のものとなります。

次のステップは？ `FontWarningHandler` をデータベース書き込みロガーに置き換える、あるいはブランド承認済みの代替フォントへマッピングする **フォント置換ルール** を試すなどです。また、コンテナ環境で動作する場合は **クラウドストレージから動的にフォントをロード** することも検討してください。

特定のエッジケース（OpenType 機能の取り扱いや暗号化された DOCX ファイルの処理など）について質問がありますか？ 下のコメント欄に書き込んでください。 happy coding!  

---

![Create warning callback diagram](https://example.com/images/create-warning-callback.png "Create warning callback diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}