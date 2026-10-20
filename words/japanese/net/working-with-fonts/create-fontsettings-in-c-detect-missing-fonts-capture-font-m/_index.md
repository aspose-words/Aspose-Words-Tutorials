---
category: general
date: 2026-03-01
description: C#で FontSettings を作成し、欠落フォントを検出してフォントメッセージを取得し、Aspose.Words で欠落フォントを処理します。開発者向けのステップバイステップガイド。
draft: false
keywords:
- create fontsettings
- detect missing fonts
- capture font messages
- handle missing fonts
- Aspose.Words font handling
- C# document processing
language: ja
og_description: C#でFontSettingsを作成し、欠落フォントを検出、フォントメッセージを取得、Aspose.Wordsを使用して欠落フォントを処理します。コード付きの完全なチュートリアル。
og_title: C#でFontSettingsを作成 – 欠損フォントを検出し、フォントメッセージを取得
tags:
- Aspose.Words
- C#
- Font Management
title: C#でFontSettingsを作成 – 欠落フォントを検出し、フォントメッセージを取得
url: /ja/net/working-with-fonts/create-fontsettings-in-c-detect-missing-fonts-capture-font-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#でFontSettingsを作成 – 欠落フォントの検出とフォントメッセージの取得

.NETプロジェクトで **create FontSettings** が必要だったことはありますか、しかしターゲットマシンにインストールされていないフォントをどのように見つけるか分からなかったことはありませんか？ あなただけではありません。実際のアプリケーション—たとえば自動レポートジェネレータやドキュメントコンバータ—では、欠落フォントがレイアウトを静かに壊し、PDFが崩れるまで気付かないことがあります。  

もし **detect missing fonts**、**capture font messages**、そして **handle missing fonts** を、出力が崩れる前に実行できたらどうでしょうか？ 良いニュースは、Aspose.Words がこれを簡単にしてくれることです。このチュートリアルでは、`FontSettings` オブジェクトの設定から、どのグリフが置換されたか正確に教えてくれる警告コールバックの設定まで、全工程を順に解説します。

> **TL;DR:** 最終的に、すべてのフォント置換をログに記録する C# コンソールアプリが完成し、置換フォントを埋め込むかユーザーに警告するかを自由に選べます。

---

## 前提条件

- .NET 6 SDK（または最近の .NET バージョン）  
- Visual Studio 2022 または C# 拡張機能がインストールされた VS Code  
- Aspose.Words for .NET のライセンス（デモ用に無料トライアルで可）  
- インストールされていないフォントを参照しているサンプル DOCX（例：Linux 環境の *Comic Sans MS*）  

`Aspose.Words` 以外の特別な NuGet パッケージは必要ありません。

---

## Step 1 – Aspose.Words のインストールとプロジェクトの設定

まず最初に、新しいコンソールプロジェクトを作成し、Aspose.Words ライブラリを導入します。

```bash
dotnet new console -n FontSettingsDemo
cd FontSettingsDemo
dotnet add package Aspose.Words
```

> **Pro tip:** すでにソリューションがある場合は、NuGet パッケージマネージャ UI からパッケージを追加するだけで、バージョン管理が楽になります。

---

## Step 2 – FontSettings の作成（主要キーワードがここに表示されます）

**create FontSettings** のステップは、フォント関連ワークフローの基礎です。`FontSettings` は Aspose.Words に対してフォント検索場所、システムフォルダーの使用可否、欠落時のフォールバック方法を指示します。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a FontSettings object – this is where we’ll configure search paths.
FontSettings fontSettings = new FontSettings();

// Optional: add a custom folder that contains fallback fonts.
fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

なぜ重要かというと、適切に構成された `FontSettings` がないと、エンジンは欠落したグリフをデフォルトのシステムフォントで静かに置換してしまい、警告が一切表示されません。

---

## Step 3 – LoadOptions と FontSettings の接続

`LoadOptions` を使って `FontSettings` をドキュメントローダーに渡します。これにより、`Document` の構築フェーズで **detect missing fonts** が可能になります。

```csharp
// 2️⃣ Configure LoadOptions to use the FontSettings we just created.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

これで `loadOptions` を使用して DOCX をロードするたびに、先ほど設定した `FontSettings` が参照されます。

---

## Step 4 – **Capture Font Messages** のための Warning Callback の設定

Aspose.Words はさまざまな条件で警告を出します—フォント置換はその代表例です。`IWarningCallback` の実装を提供することで、**capture font messages** をリアルタイムで取得できます。

```csharp
// 3️⃣ Attach a warning handler that will print font‑substitution warnings.
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

### Warning ハンドラクラス

```csharp
/// <summary>
/// Handles font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Source == WarningSource.FontSubstitution)
        {
            Console.WriteLine($"[FontSubstitution] {info.Description}");
        }
    }
}
```

`info.Description` フィールドには、たとえば *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”* のような人間が読めるメッセージが入ります。これが **handle missing fonts** を上手く行うために必要な情報です。

---

## Step 5 – ドキュメントをロードしてコールバックに処理させる

すべてが接続されたら、ドキュメントのロードはシンプルです。ソースファイルがシステムに存在しないフォントを参照していれば、警告ハンドラが発火します。

```csharp
// 4️⃣ Load a document that may contain unknown fonts.
Document doc = new Document(@"C:\Docs\UnknownFont.docx", loadOptions);

// Optional: you can now save the document to PDF or any other format.
doc.Save(@"C:\Docs\Result.pdf");
```

プログラムを実行すると、次のようなコンソール出力が表示されます。

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
[FontSubstitution] Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

この出力が **capture font messages** の部分です。ハンドラを拡張してファイルにログを書き込んだり、テレメトリを送信したり、重要なフォントが欠落している場合は変換を中止したりできます。

---

## Step 6 – 完全動作サンプル（全体をまとめたコード）

以下はそのままコピー＆ペーストできる完全版プログラムです。`Program.cs` に貼り付け、ファイルパスを調整して `dotnet run` を実行してください。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 1: Create FontSettings -----
            FontSettings fontSettings = new FontSettings();
            // Add any custom folder with fallback fonts (optional)
            fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);

            // ----- Step 2: Configure LoadOptions -----
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontSubstitutionWarningHandler()
            };

            // ----- Step 3: Load the document -----
            string inputPath = @"C:\Docs\UnknownFont.docx";
            Document doc = new Document(inputPath, loadOptions);

            // ----- Step 4: Save the result (optional) -----
            string outputPath = @"C:\Docs\Result.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any font substitution warnings.");
        }
    }

    // ----- Warning handler that captures font messages -----
    class FontSubstitutionWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Source == WarningSource.FontSubstitution)
            {
                Console.WriteLine($"[FontSubstitution] {info.Description}");
            }
        }
    }
}
```

### 期待される出力

*Comic Sans MS* がインストールされていないマシンで実行すると、次のような出力が得られます。

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document processed. Check console for any font substitution warnings.
```

また、置換フォントを使用した `Result.pdf` が生成され、変換はクラッシュせずに完了します。

---

## よくある質問とエッジケース

| 質問 | 回答 |
|------|------|
| **変換を置換せずに失敗させたい場合は？** | `FontSubstitutionWarningHandler` 内で、`info.Description` に重要フォント名が含まれる場合に例外をスローします。 |
| **置換フォントを自動的に埋め込みたいですか？** | はい。欠落フォントを検出したら、既知のパスからフォールバック `FontInfo` をロードし、`fontSettings.SetFontsFolder` で `fontSettings` に追加できます。 |
| **Linux/macOS でも動作しますか？** | 完全に対応しています。`FontSettings` はクロスプラットフォームで機能しますので、フォールバックフォルダーに適切な `.ttf` または `.otf` ファイルを配置してください。 |
| **警告コールバックはスレッドセーフですか？** | コールバックはドキュメントをロードした同じスレッド上で実行されるため、コンソールへのログ出力に追加の同期は不要です。マルチスレッド環境では共有リソースを保護してください。 |
| **警告をファイルに記録するには？** | `Console.WriteLine` を `File.AppendAllText("font_warnings.log", ...)` に置き換えるか、Serilog や NLog といったロギングフレームワークを使用します。 |

---

## 本番環境向けフォント処理のプロTips

1. **Cache Font Lookups** – 複数のドキュメントをロードする際に同じ `FontSettings` インスタンスを再利用することで、ファイルシステムのスキャンを繰り返すのを防げます。  
2. **Whitelist Critical Fonts** – ブランドで特定のフォントが必須な場合、事前に存在を確認し、明確なエラーメッセージで中止します。  
3. **Use `SetFontFolder` Recursively** – `recursive: true` を設定するとサブフォルダーも走査され、フォントコレクション全体を配布する際に便利です。  
4. **Combine with `FontSubstitutionSettings`** – 置換ルールを細かく調整できます（例：同じファミリ名のフォントを優先）。

---

## 結論

私たちは **FontSettings を作成** し、`LoadOptions` に設定して **欠落フォントを検出**、警告コールバックで **フォントメッセージを取得**、そして **欠落フォントを適切に処理** する方法を実演しました。全体の流れは数十行の C# で収まり、任意の DOCX のフォント状況を完全に把握できるようになります。

次に試すべきこと：

- **Embedding fallback fonts** を出力 PDF に直接埋め込む (`PdfSaveOptions.FontEmbeddingMode`)。  
- 企業のブランディングルールに基づいてプログラムでフォントを置換する。  
- CI パイプラインと統合し、許可されていないフォントを使用したドキュメントを自動的にフラグする。

ぜひ試してみて、警告ハンドラを自分の要件に合わせて調整し、ドキュメントパイプラインを自信を持って運用してください。見えないフォントの入れ替えによる不思議なレイアウト不具合はもう起こりません。

コーディングを楽しんでください！ 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}