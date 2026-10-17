---
category: general
date: 2026-01-11
description: .NET ドキュメントで欠落フォントを検出するために、フォント置換警告を有効にします。Aspose.Words を使用して、欠落フォント名の取得方法と欠落フォントの一覧の取得方法を学びましょう。
draft: false
keywords:
- enable font substitution warnings
- detect missing fonts
- get missing font name
- list missing fonts
language: ja
og_description: Aspose.Wordsでフォント置換警告を有効にし、欠落フォントを検出し、欠落フォント名を取得し、文書内の欠落フォントを一覧表示します。
og_title: フォント置換警告を有効にする – ステップバイステップ C# チュートリアル
tags:
- Aspose.Words
- C#
- Document Processing
title: Aspose.Wordsでフォント置換警告を有効にする – 完全ガイド
url: /ja/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# フォント置換警告の有効化 – 完全ガイド

サーバーにロードした後、Word 文書の見た目が少しずつ変わっていると感じたことはありませんか？ おそらく、元の作者が使用したフォントがあなたのマシンに存在せず、Aspose.Words が黙って最も近いフォントに置き換えているからです。**フォント置換警告を有効にする**ことで、どのフォントが欠落しているか、何に置き換えられたか、そしてその情報をどう扱うかをすぐに把握できます。

このチュートリアルでは、実践的なエンドツーエンドの例を通じて、**欠落フォントを検出**し、**欠落フォント名を取得**し、さらに**欠落フォントの一覧**をレポート用に取得する方法を示します。余計な説明はなく、すぐに任意の .NET プロジェクトに組み込める明快なソリューションです。

---

## 学べること

- `LoadOptions` を構成して、Aspose.Words が詳細な警告を出すようにする方法。
- ドキュメントをロードし、フォント関連の警告を列挙するために必要な正確なコード。
- 欠落フォント名とその置換フォントを抽出し、整ったレポートとして出力する方法。
- 多数の欠落フォントやカスタムフォントフォルダーを含むドキュメントなど、エッジケースを扱うためのヒント。

### 前提条件

- .NET 6+（コードは .NET Framework 4.7+ でも動作します）
- Aspose.Words for .NET 23.10 以降（NuGet から取得できます）
- インストールされていないフォントを参照しているサンプル DOCX（ここでは `MissingFont.docx` と呼びます）

これらの前提が揃ったら、さっそく始めましょう。

## 手順 1: LoadOptions を設定してフォント置換警告を有効にする  

最初に行うべきことは、Aspose.Words に欠落フォントが重要であることを伝えることです。デフォルトではライブラリは内部的に警告を記録するだけです。`SubstitutionWarningLevel` を `Typical`（または最も詳細な出力を得るために `All`）に設定すると、スイッチがオンになります。

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Create a new LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Attach a FontSettings object so we can tweak font‑related behavior
loadOptions.FontSettings = new FontSettings();

// Enable warnings for typical font substitutions (covers most real‑world cases)
loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;
```

**なぜ重要か:**  
`SubstitutionWarningLevel` を設定すると、Aspose.Words が参照フォントを見つけられないたびに、`FontSubstitutionWarning` がドキュメントの `Warnings` コレクションに追加されます。このコレクションは、ドキュメントを手動で解析せずに **欠落フォントを検出** する唯一の信頼できる方法です。

> **プロのコツ:** 複数のドキュメントを処理し、すべての置換を確実に捕捉したい場合は `FontSubstitutionWarningLevel.All` を使用してください。多少ノイズは増えますが、警告が抜け落ちることはありません。

## 手順 2: 設定したオプションでドキュメントをロードする  

警告システムの準備ができたので、先ほど作成した `LoadOptions` を使って DOCX をロードします。パスは絶対でも相対でも構いませんが、ファイルが存在することを確認してください。

```csharp
// Path to the DOCX that references a font you don’t have
string docPath = @"C:\Docs\MissingFont.docx";

// Load the document while respecting our warning configuration
Document document = new Document(docPath, loadOptions);
```

**内部で何が起きているか:**  
Aspose.Words はドキュメントの XML を解析し、各 `<w:font>` 要素を解決し、システムのフォントカタログ（および `FontSettings` に追加したカスタムフォルダー）をチェックします。フォントが見つからない場合、警告を記録します—これが後で **欠落フォントの一覧** を取得するために必要な情報です。

## 手順 3: 警告を反復処理し、欠落フォントの詳細を抽出する  

ドキュメントがメモリ上にある状態で、`Warnings` コレクションにはすべての `FontSubstitutionWarning` が格納されています。これをループし、対象タイプでフィルタリングし、分かりやすいレポートを出力します。

```csharp
Console.WriteLine("=== Missing Font Report ===");
foreach (WarningInfo warning in document.Warnings)
{
    // Only interested in font substitution warnings
    if (warning is FontSubstitutionWarning fontWarning)
    {
        // The name of the font that was missing
        string missingFont = fontWarning.FontName;

        // The font Aspose.Words used instead
        string substitutedFont = fontWarning.SubstitutedFontName;

        Console.WriteLine($"Missing font: {missingFont}");
        Console.WriteLine($"Substituted with: {substitutedFont}");
        Console.WriteLine(new string('-', 30));
    }
}
```

**期待される出力**（ソース文書がインストールされていない `MyCustomFont` を参照していると仮定）

```
=== Missing Font Report ===
Missing font: MyCustomFont
Substituted with: Arial
------------------------------
Missing font: FancyScript
Substituted with: Times New Roman
------------------------------
```

各エントリが **欠落フォント名**（`MyCustomFont`）と代替フォント（`Arial`）の両方を提供していることに注目してください。これが、元のフォントを埋め込むか、作者に代替を依頼するか、あるいは置換を受け入れるかを判断するために必要な情報です。

## 手順 4: オプション – データをリストに収集してさらに処理する  

レポートを CSV にエクスポートしたり、API 経由で送信したり、後でメモリに保持したりしたい場合は、警告を強く型付けされたリストに格納できます。

```csharp
// Define a simple DTO to hold the warning details
public class MissingFontInfo
{
    public string MissingFont { get; set; }
    public string SubstitutedFont { get; set; }
}

// Build the list
List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();

foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fsw)
    {
        missingFonts.Add(new MissingFontInfo
        {
            MissingFont = fsw.FontName,
            SubstitutedFont = fsw.SubstitutedFontName
        });
    }
}

// Example: write to a CSV (requires System.IO)
var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);
```

これで **欠落フォントの一覧** が、下流システムが利用できる形式で取得できました。ダッシュボードに供給する場合でも、監査ログを生成する場合でも、データは準備完了です。

## 手順 5: エッジケースと一般的な落とし穴の対処  

### 単一実行での複数欠落フォント  

大企業のテンプレートはしばしば数十種類のカスタムフォントを参照します。警告コレクションは大きくなる可能性がありますが、上記の反復パターンは線形にスケールするため、パフォーマンスは問題になりません。出力を読みやすく保つことを忘れずに—ページやスタイルでグループ化すると、より詳細な分析に役立ちます。

### カスタムフォントフォルダー  

標準でないディレクトリ（例: 共有ネットワークフォルダー）にフォントを保存している場合は、Aspose.Words に検索場所を指示します。

```csharp
loadOptions.FontSettings.SetFontsFolder(@"\\fileserver\SharedFonts", recursive: true);
```

ドキュメントをロードする *前に* これを設定すると、ライブラリがフォントを見つける機会が得られ、警告が完全に解消されることがあります。

### 特定の警告を抑制する  

場合によっては、特定の置換が許容できることが分かっていることがあります（例: 装飾フォントで置換しても問題ない場合）。事後にそれらをフィルタリングできます。

```csharp
missingFonts = missingFonts
    .Where(f => f.MissingFont != "DecorativeFont")
    .ToList();
```

### バージョン互換性  

`FontSubstitutionWarningLevel` 列挙体は Aspose.Words 20.12 以降で安定しています。古いバージョンを使用している場合は、警告レベル機能にアクセスするためにアップグレードが必要になるかもしれません。

## 完全な動作例  

以下は、上記すべての手順を組み込んだ完全な実行可能プログラムです。新しいコンソールプロジェクトに貼り付け、Aspose.Words の NuGet パッケージを追加し、`docPath` を欠落フォントを参照するドキュメントに設定してください。

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    // DTO for storing missing font info
    public class MissingFontInfo
    {
        public string MissingFont { get; set; }
        public string SubstitutedFont { get; set; }
    }

    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure LoadOptions to enable font substitution warnings
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;

            // Optional: add a custom fonts folder
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

            // 2️⃣ Load the document with the above options
            string docPath = @"C:\Docs\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Gather warnings into a list
            List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();
            foreach (WarningInfo warning in doc.Warnings)
            {
                if (warning is FontSubstitutionWarning fsw)
                {
                    missingFonts.Add(new MissingFontInfo
                    {
                        MissingFont = fsw.FontName,
                        SubstitutedFont = fsw.SubstitutedFontName
                    });
                }
            }

            // 4️⃣ Output a human‑readable report
            Console.WriteLine("=== Missing Font Report ===");
            foreach (var info in missingFonts)
            {
                Console.WriteLine($"Missing font: {info.MissingFont}");
                Console.WriteLine($"Substituted with: {info.SubstitutedFont}");
                Console.WriteLine(new string('-', 30));
            }

            // 5️⃣ (Optional) Export to CSV for further analysis
            var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
            File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);

            Console.WriteLine("Report saved to C:\\Docs\\MissingFontsReport.csv");
        }
    }
}
```

このプログラムを実行すると、**フォント置換警告が有効化**され、**欠落フォントが検出**され、**欠落フォント名が取得**され、**欠落フォントの一覧**がコンソールと CSV ファイルの両方に出力されます。

## 結論  

ここまでで、Aspose.Words で **フォント置換警告を有効化** するために必要なすべて（初期設定から欠落フォントのクリーンな一覧取得まで）を網羅しました。上記の手順に従えば、ドキュメントの監査、視覚的忠実性の確保、サーバー上でのレンダリング時に不快なサプライズが起きるのを防げます。

次に試したいこと:

- **欠落フォントを埋め込む**：出力 PDF または DOCX に直接埋め込む（`FontSettings.EmbeddedFonts` を使用）。
- **レポートに基づくフォントインストールの自動化**：ビルドエージェント上でフォントを自動的にインストール。
- **CI パイプラインへの統合**：重要なフォントが欠如している場合にビルドを失敗させる。

ぜひ試してみてください。シンプルな警告システムが、フルスケールのフォント管理ワークフローへと変わります。

コーディングを楽しんで、すべてのフォントが見つかりますように！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}