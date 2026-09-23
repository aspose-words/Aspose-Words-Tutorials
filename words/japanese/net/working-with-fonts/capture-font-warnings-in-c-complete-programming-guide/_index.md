---
category: general
date: 2026-02-18
description: Aspose.Words を使用して C# でフォント警告を取得し、欠落フォントを検出する方法を学びましょう。ステップバイステップのガイドに従って、欠落フォントを効率的に処理してください。
draft: false
keywords:
- capture font warnings
- detect missing fonts
- handle missing fonts
- list missing fonts
language: ja
og_description: C#でフォント警告を取得し、欠落フォントの検出・処理・一覧表示をフルコード例で学ぶ。
og_title: C#でフォント警告を取得する – 完全ガイド
tags:
- Aspose.Words
- C#
- Font Management
title: C#でフォント警告を取得する – 完全プログラミングガイド
url: /ja/net/working-with-fonts/capture-font-warnings-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# でフォント警告をキャプチャ – 完全プログラミングガイド

サーバーにインストールされていないフォントが文書で参照されたときに、**フォント警告をキャプチャ**する方法を考えたことはありますか？ あなただけではありません。多くのエンタープライズアプリでは、フォントが欠如するとレイアウトが乱れ、ライブラリが出す警告をリッスンすることが唯一確実な方法です。

このチュートリアルでは、**フォント警告をキャプチャ**するだけでなく、**欠損フォントを検出**し、**欠損フォントを処理**し、さらに **欠損フォントを一覧表示** できる、すぐに実行可能なソリューションをご紹介します。外部ドキュメントは不要です—コピーして貼り付け、実行するだけです。

## 学習内容

- `LoadOptions` を構成してフォント置換警告を有効にする方法。  
- DOCX を読み込み、すべての警告を取得するために必要な正確なコード。  
- 各ステップが重要な理由と、パフォーマンス上の考慮点。  
- 混在スクリプトフォントやカスタムフォントフォルダーを含む文書のエッジケース処理。  

**前提条件**: .NET 6+（または .NET Framework 4.6+）、**Aspose.Words** NuGet パッケージへの参照、C# の基本的な理解。Aspose.Words を使ったことがなくても心配無用です—このガイドはすべての細部を案内します。

![Diagram showing capture font warnings flow](image.png){alt="capture font warnings diagram"}

## フォント警告をキャプチャする重要性

Aspose.Words が文書を読み込むと、利用できないフォントは自動的にフォールバックに置き換えられます。この置き換えにより読み込みは成功しますが、視覚的な結果が大きくずれることがあります。**SubstitutionWarningLevel.All** フラグを有効にすると、ライブラリは欠損フォントごとに `WarningInfo` エントリを追加し、文書がレンダリングまたは保存される前に **欠損フォントを検出** できるようになります。

> **プロのコツ:** バッチジョブで数百ファイルを処理する場合、これらの警告を中央ストアにログとして保存しておくと、後の手動 QA にかかる時間を何時間も節約できます。

## Step 1: プロジェクトのセットアップ

1. お好みの IDE（Visual Studio、Rider、VS Code）を開く。  
2. 新しいコンソールプロジェクトを作成する：

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
```

3. Aspose.Words パッケージを追加する：

```bash
dotnet add package Aspose.Words
```

以上です—余計な DLL や COM インタープロは不要です。ライブラリは **欠損フォントを処理** するために必要なものをすべて含んでいます。

## Step 2: すべてのフォント置換警告をキャプチャするための LoadOptions の準備

エンジンに **フォント警告をキャプチャ** させるには、置換をすべて記録するよう指示する必要があります。以下のスニペットは `LoadOptions` インスタンスを作成し、警告レベルを有効にし、（任意で）カスタムフォントが格納されたフォルダーをエンジンに指示します。

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // Step 2.1 – Create LoadOptions and turn on font‑substitution warnings
            // -----------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions();

            // Initialise FontSettings if you need to add a custom font folder
            loadOptions.FontSettings = new FontSettings();

            // Capture *all* font substitution events (this is the key for capture font warnings)
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // Optional: add a folder that contains corporate fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);
```

**この設定が重要な理由:**  
- `SubstitutionWarningLevel.All` は **すべて** の欠損フォントイベントを記録し、最初の1件だけに留めません。  
- このフラグが無いと、Aspose.Words は静かにフォントを置き換え、問題があることに気付くことができません。

## Step 3: 設定したオプションで文書を読み込む

実際にファイルを開きます。`DocumentWithMissingFonts.docx` をテスト文書のパスに置き換えてください。

```csharp
            // -----------------------------------------------------------------
            // Step 2.2 – Load the document with the warning‑enabled options
            // -----------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";

            Document document = new Document(docPath, loadOptions);
```

ファイルに機械にインストールされていないフォント（またはオプションで指定したフォルダーにないフォント）の参照が含まれている場合、`document.WarningInfoCollection` が自動的に埋められます。

## Step 4: フォント置換警告を検索し表示する

チュートリアルの核心部分です。`WarningInfoCollection` を走査して **欠損フォントを一覧表示** します。`WarningType.FontSubstitution` でフィルタリングし、分かりやすいメッセージを出力します。

```csharp
            // -----------------------------------------------------------------
            // Step 2.3 – Enumerate and output font substitution warnings
            // -----------------------------------------------------------------
            var fontWarnings = document.WarningInfoCollection
                                         .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    // The Description property already contains a readable message
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // Keep console window open when debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### 期待される出力

```
⚠️ Missing fonts detected:
- Missing font: "Comic Sans MS"
- Missing font: "Calibri Light"
```

文書がインストール済みフォントだけを使用している場合は、`✅ No missing fonts detected` 行が表示されます。

## Step 5: 高度な – **欠損フォントをプログラムで処理** する方法

単にリストを出力するだけでも診断ツールとしては十分ですが、多くの本番システムでは **欠損フォントを自動的に処理** する必要があります。以下に一般的な2つの戦略を示します。

### 5.1 既知のフォールバックに置き換える

```csharp
loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution
{
    // Replace any missing font with Arial, which is universally available
    SubstituteFont = "Arial"
};
```

### 5.2 カスタムフォントをその場で埋め込む

企業フォントファイル（`MyBrand.ttf`）がある場合、欠損フォントが検出されたときに埋め込むことができます：

```csharp
foreach (WarningInfo warning in fontWarnings)
{
    string missingFontName = warning.Description.Split('"')[1]; // crude extraction
    // Load your custom font (ensure the path is correct)
    string customFontPath = $@"C:\MyCompany\Fonts\{missingFontName}.ttf";

    if (File.Exists(customFontPath))
    {
        loadOptions.FontSettings.SetFontsFolder(Path.GetDirectoryName(customFontPath), false);
        Console.WriteLine($"🔧 Embedded custom font for \"{missingFontName}\"");
    }
}
```

> **注意:** フォントを埋め込むと出力ファイルのサイズが増加するため、忠実度と帯域幅のトレードオフを検討してください。

## よくある落とし穴と回避策

| 症状 | 考えられる原因 | 対策 |
|------|----------------|------|
| 文書は見た目が崩れているのに警告が出ない | `SubstitutionWarningLevel` が `All` に設定されていない | 手順2でフラグが正しく設定されていることを確認 |
| 同じフォントが警告に複数回表示される | 文書内で同フォントが複数のスタイルで使用されている | ユニークなリストだけが必要なら `fontWarnings.Select(w => w.Description).Distinct()` で重複除去 |
| 大容量 DOCX ファイルでアプリがクラッシュする | デフォルトのメモリ設定で読み込んでいる | `LoadOptions.LoadFormat` を使用するか、ストリームで読み込んでメモリ負荷を軽減 |

## 完全動作サンプル（コピー＆ペーストで使用可能）

```csharp
using System;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ---------------------------------------------------------------
            // Configure LoadOptions to capture font warnings
            // ---------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // OPTIONAL: add a folder with custom fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);

            // ---------------------------------------------------------------
            // Load the document
            // ---------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // ---------------------------------------------------------------
            // Retrieve and display missing‑font warnings
            // ---------------------------------------------------------------
            var fontWarnings = doc.WarningInfoCollection
                                  .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // ---------------------------------------------------------------
            // OPTIONAL: automatic handling (fallback or embedding)
            // ---------------------------------------------------------------
            // Example: substitute everything with Arial
            // loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution { SubstituteFont = "Arial" };

            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

`dotnet run` でプログラムを実行してください。コンソールに欠損フォントの一覧が表示され、**フォント警告をキャプチャ** に成功したことが確認できます。

## 結論

これで、Aspose.Words を使用した C# アプリケーションにおいて **フォント警告をキャプチャ**、**欠損フォントを検出**、**欠損フォントを処理**、そして **欠損フォントを一覧表示** するための、完全な本番対応パターンが手に入りました。この手法は軽量で、数行のコードだけで実装でき、既存のパイプラインに簡単に組み込めます—以下のようなシナリオでも

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}