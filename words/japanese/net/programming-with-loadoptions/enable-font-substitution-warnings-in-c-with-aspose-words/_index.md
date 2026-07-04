---
category: general
date: 2026-06-20
description: Aspose.Words を使用して C# でフォント置換警告を有効にします。LoadOptions の設定方法、警告の取得方法、欠落フォントの効率的な処理方法を学びましょう。
draft: false
keywords:
- enable font substitution warnings
- Aspose.Words LoadOptions
- C# font substitution warnings
- document warning handling
- font substitution messages
language: ja
og_description: C# と Aspose.Words でフォント置換の警告を有効にします。このガイドでは、LoadOptions の設定方法、WarningInfo
  の読み取り方法、そして欠落フォント メッセージの表示方法を示します。
og_title: C#でフォント置換警告を有効にする – 完全ガイド
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Enable font substitution warnings in C# using Aspose.Words. Learn how
    to configure LoadOptions, capture warnings, and handle missing fonts efficiently.
  headline: Enable Font Substitution Warnings in C# with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Font Substitution
- Warnings
title: Aspose.Words を使用した C# でフォント置換警告を有効にする
url: /ja/net/programming-with-loadoptions/enable-font-substitution-warnings-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# と Aspose.Words でフォント置換警告を有効にする

サーバーにインストールされていないフォントが Word 文書で参照されているときに、**フォント置換警告を有効にする**方法を考えたことはありませんか？ あなただけではありません。フォントが欠如すると、生成された PDF や画像のレイアウトが静かに壊れることがあり、早期に検出する唯一の方法は Aspose.Words が出す警告を監視することです。

このチュートリアルでは、警告を有効にして `WarningInfo` コレクションから取得し、コンソールに意味のあるメッセージを出力するハンズオン例を順に解説します。最後まで読むと、**Aspose.Words LoadOptions** の設定方法、**C# のフォント置換警告** の処理方法、そしてドキュメント処理パイプラインを堅牢に保つコツが分かります。

また、警告を抑制した場合や、出力をコンソールではなくログに記録したい場合など、いくつかのエッジケースにも触れ、最新の Aspose.Words for .NET（バージョン 24.10 時点）で動作する、コピー＆ペースト可能な完全サンプルコードも提供します。

## 必要なもの

- .NET 6.0 以降（コードは .NET Framework 4.7+ でも動作します）
- `Aspose.Words` への NuGet 参照（`dotnet add package Aspose.Words` でインストール）
- フォントが **インストールされていない** 状態で参照されている Word ファイル（例: `DocumentWithMissingFont.docx`）
- 使いやすい IDE（Visual Studio、Rider、または VS Code）

以上です—余計なサービスやプロプライエタリツールは不要です。準備はできましたか？さっそく始めましょう。

## Step 1: フォント置換警告を有効にする

最初に行うべきことは、Aspose.Words に対してフォントが置換されたときに通知を受け取りたい旨を伝えることです。これは `LoadOptions` オブジェクトの `FontSettings` プロパティを通じて行います。デフォルトでは警告は **無効** に設定されており API が静かになるようになっているため、自分でスイッチを入れる必要があります。

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

// Create LoadOptions and enable detailed font‑substitution warnings.
LoadOptions loadOpts = new LoadOptions
{
    // FontSettings is the gateway for all font‑related behavior.
    FontSettings = new FontSettings()
    // No extra code needed here; simply having a FontSettings instance
    // makes Aspose.Words collect font‑substitution warnings.
};
```

> **Why this works:** `FontSettings` が `null` でない場合、ライブラリはドキュメントの読み込み中に遭遇したすべての `WarningType.FontSubstitution` エントリを自動的に `Document.WarningInfo` に追加します。フォント用の「デバッグモード」をオンにしたようなものです。

## Step 2: 設定済みオプションでドキュメントを読み込む

警告コレクションが有効になったので、先ほど作成した `LoadOptions` を使ってドキュメントを読み込みます。ドキュメントに欠損フォントが含まれていれば、Aspose.Words は代替フォントに置換し、`WarningInfo` リストに警告をプッシュします。

```csharp
// Path to a DOCX that references a font not present on the machine.
string docPath = @"C:\Samples\DocumentWithMissingFont.docx";

// Load the document while respecting the LoadOptions we set up.
Document doc = new Document(docPath, loadOpts);
```

> **Pro tip:** ループで多数のファイルを処理する場合は、同じ `LoadOptions` インスタンスを再利用しましょう。一度だけ作成すれば、イテレーションごとに数ミリ秒のオーバーヘッドを削減できます。

## Step 3: WarningInfo を走査してフォント置換メッセージを表示する

ドキュメントの読み込みが完了すると、`WarningInfo` コレクションにロード中に発生したすべての警告が格納されます。ここでは `WarningType.FontSubstitution` のみが対象なので、適切にフィルタリングします。

```csharp
foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"Substituted: {warning.Description}");
}
```

上記スニペットを、欠損フォント「Papyrus」を参照している文書に対して実行すると、次のような出力が得られることがあります。

```
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Comic Sans MS' is not installed. Substituted with 'Times New Roman'.
```

これが **フォント置換メッセージ** です。明確で実行可能な情報となっており、ログに記録したりアラートシステムに送信したりできます。

## 完全動作サンプル

以下はすべてをひとつにまとめたコンソールアプリの例です。`.csproj` に貼り付けて **Run** をクリックしてください。

```csharp
// ---------------------------------------------------------------
// Enable Font Substitution Warnings – Complete Example
// ---------------------------------------------------------------

using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions to capture font‑substitution warnings.
        LoadOptions loadOpts = new LoadOptions
        {
            FontSettings = new FontSettings()   // Enabling warning collection.
        };

        // 2️⃣ Load the target document (adjust the path to match your environment).
        string docPath = @"C:\Samples\DocumentWithMissingFont.docx";
        Document doc = new Document(docPath, loadOpts);

        // 3️⃣ Process the warning collection.
        Console.WriteLine("=== Font Substitution Warnings ===");
        bool anyWarnings = false;

        foreach (WarningInfo warning in doc.WarningInfo)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                anyWarnings = true;
                Console.WriteLine($"Substituted: {warning.Description}");
            }
        }

        if (!anyWarnings)
            Console.WriteLine("No font substitution warnings were generated.");

        // Optional: keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

### 期待される出力

フォントがインストールされていない場合、次のような出力が表示されます。

```
=== Font Substitution Warnings ===
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Courier New' is not installed. Substituted with 'Times New Roman'.
Press any key to exit...
```

すべてのフォントがマシンに存在すれば、プログラムは単に以下を出力します。

```
=== Font Substitution Warnings ===
No font substitution warnings were generated.
Press any key to exit...
```

## よくある落とし穴 & プロのコツ

| Issue | Why It Happens | How to Fix / Avoid |
|-------|----------------|--------------------|
| **Warnings disappear** | `FontSettings` をクリアした、または `FontSettings` を設定しない `LoadOptions` を使用した。 | プロパティを変更しなくても、必ず `FontSettings` をインスタンス化してください。 |
| **Too many warnings** | 文書が多数のマイナーなフォントを使用している。 | `SetFontsFolder` でカスタムフォントフォルダーを `FontSettings` に追加し、置換回数を減らすことを検討してください。 |
| **Performance hit in a tight loop** | 各イテレーションで `LoadOptions` を再生成している。 | すべてのドキュメントで単一の `LoadOptions` インスタンスを再利用しましょう。 |
| **Missing console output** | GUI アプリ内で実行しており `Console.WriteLine` が無視されている。 | 警告をロガー (`ILogger`) にリダイレクトするか、ファイルに書き出してください。 |

### 実サービスでの警告処理

Web API ではコンソールへの書き込みは望ましくありません。その代わりに警告を構造化ログへ流し込みます。

```csharp
var logger = LoggerFactory.Create(builder => builder.AddConsole()).CreateLogger<Program>();

foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        logger.LogWarning("Font substitution: {Description}", warning.Description);
}
```

このようにすれば、**ドキュメント警告のハンドリング** を保ちつつ、サービスをクリーンに保てます。

## サンプルの拡張例

- **他の警告タイプを取得**（例: `WarningType.UnknownFileFormat`）するには `if` フィルタを削除します。  
- **すべての警告を JSON に保存**し、下流の分析に利用します。  
- **特定のフォールバックフォントを強制**するには `FontSettings.SubstitutionSettings.DefaultFontName` を設定します。

これらはすべて、**フォント置換警告を有効にする**ことをマスターした後に自然に拡張できる機能です。

## 結論

本稿では、Aspose.Words を使用して C# で **フォント置換警告を有効にする**方法を、`LoadOptions` の設定から `WarningInfo` の走査、フレンドリーなメッセージのコンソール出力まで実演しました。上記手順に従うことで、欠損フォントによるレイアウト変更が静かに起こるリスクからドキュメント処理パイプラインを守れます。

次はカスタムフォントフォルダーを追加したり、警告をファイルに記録したり、監視ダッシュボードへ送信したりしてみてください。同じパターンは PDF 変換、画像レンダリング、メールマージなど、あらゆる **ドキュメント警告のハンドリング** シナリオで有効です。

**C# のフォント置換警告** について質問がある方や、巧妙な回避策を共有したい方はぜひコメントを残してください—ハッピーコーディング！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示した手法に密接に関連するトピックを扱っています。各リソースには完全な動作コード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、プロジェクトで代替実装アプローチを探求したりするのに役立ちます。

- [Aspose.Words でフォント置換警告を有効にする – 完全ガイド](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Aspose.Words でフォントを検出する – 警告と設定の処理](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Java で Aspose.Words を使用したフォント置換警告の取得 – 完全ガイド](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}