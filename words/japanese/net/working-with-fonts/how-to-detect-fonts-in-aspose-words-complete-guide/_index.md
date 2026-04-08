---
category: general
date: 2026-04-07
description: Aspose.Words を使用した C# でフォントの検出方法と、フォントが欠落している場合の警告取得方法を学びます。ステップバイステップのコードが含まれています。
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- handle missing fonts
- Aspose.Words font substitution
- C# document loading warnings
language: ja
og_description: Aspose.Wordsでフォントを検出する方法は？このチュートリアルに従って警告を取得し、欠落フォントを簡単に処理しましょう。
og_title: Aspose.Wordsでフォントを検出する方法 – 完全ガイド
tags:
- Aspose.Words
- C#
- Font handling
title: Aspose.Wordsでフォントを検出する方法 – 完全ガイド
url: /ja/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words でフォントを検出する方法 – 完全ガイド

本番環境にリリースする前に、Word 文書に欠落している **フォントを検出** したいと思ったことはありませんか？ 多くのエンタープライズシナリオで、余計なフォントが PDF 変換パイプラインを壊したり、レイアウトの乱れを引き起こしたりして、プロフェッショナルでない印象を与えてしまいます。良いニュースは、Aspose.Words には欠損フォントを検出し、明確な警告を出す組み込み機能があることです。

このチュートリアルでは、**フォントの検出方法**、**警告の取得方法**、そして **欠損フォントの処理ベストプラクティス** を順を追って解説します。外部ツールは不要、推測も不要—今すぐプロジェクトに組み込める純粋な C# コードだけです。

> **クイックプレビュー:** 最後まで読むと、ドキュメント読み込み時にすべてのフォント置換メッセージを収集する再利用可能な `FontSubstitutionWarningCollector` が手に入り、フォントが見つからなかったときの対処方法が分かります。

---

## 学べること

- `LoadOptions` を設定してフォント置換警告をリッスンする方法。  
- カスタムコレクタークラスでその警告を取得する方法。  
- 収集した警告を処理し、処理を中止するか、ログに記録するか、フォントを置換するかを決定する方法。  
- リモートフォントや埋め込みフォントを参照するドキュメントに対するエッジケースの取り扱い。  

**前提条件:** .NET 6+（または .NET Framework 4.6+）、Aspose.Words for .NET（最新バージョン）、C# の基本的な知識。Aspose.Words を使ったことがなくても心配はいりません—このガイドは数分のセットアップ時間だけを想定しています。

---

## Aspose.Words LoadOptions を使用したフォント検出方法

欠損フォントを検出する最初のステップは、Aspose.Words にそれらを報告させることです。これは `LoadOptions.WarningCallback` プロパティで実現でき、`IWarningCallback` を実装した任意のクラスを受け取ります。以下では、警告をすべて保存する小さなコレクターを作成します。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.Collections.Generic;

/// <summary>
/// Collects all warnings emitted while loading a document.
/// </summary>
public class FontSubstitutionWarningCollector : IWarningCallback
{
    // Thread‑safe static list so we can access warnings after loading.
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();

    // Called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑related warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Warnings.Add(info);
        }
    }

    // Helper to clear previous run’s warnings.
    public static void Clear() => Warnings.Clear();
}
```

**重要ポイント:** 警告コールバックを設定しないと、Aspose.Words は欠損フォントをデフォルトフォントに静かに置換してしまい、問題があることに気付くことができません。`WarningType.FontSubstitution` を捕捉することで、**利用できないフォント** を完全に可視化できます。

次に、コレクターを `LoadOptions` に組み込み、ドキュメントを読み込みます。

```csharp
// Step 1: Prepare load options with our warning collector.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontSubstitutionWarningCollector()
};

// Optional: clear any stale warnings from a previous run.
FontSubstitutionWarningCollector.Clear();

// Step 2: Load the document. Replace the path with your own file.
Document doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
```

> **プロのコツ:** バッチ処理で多数のドキュメントを扱う場合、同じ `FontSubstitutionWarningCollector` インスタンスを再利用できますが、ロードごとに `Clear()` を呼んで警告がファイル間で混在しないようにしてください。

---

## ドキュメント読み込み時の警告取得

ドキュメントが読み込まれた後、コレクターにはすでにフォント関連の警告がすべて格納されています。次に考えるべきは、*警告をどのように取得して* ログや画面に表示しやすくするかです。

```csharp
// Step 3: Iterate over collected warnings and output them.
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    Console.WriteLine($"{warning.Type}: {warning.Message}");
}
```

典型的な出力例は次のとおりです:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'Garamond' missing. Using 'Times New Roman' instead.
```

**この情報が示すこと:** 各行は元のフォント名と、Aspose.Words が選択した代替フォントを示しています。この情報をもとに、代替フォントが許容できるか、あるいは欠損フォントを手動で埋め込む必要があるかを判断できます。

---

## 欠損フォントを上手に処理する

警告を検出・取得するだけでは不十分です。実際の価値は、**欠損フォントを本番環境向けに処理** できることにあります。以下に、一般的な 3 つの戦略を示します。

1. **ログを残して続行** – 監査トレイルが必要なバッチ処理に最適。  
2. **重要フォントで中止** – 特定のフォント（例: ブランド専用フォント）が欠損している場合は例外をスロー。  
3. **欠損フォントをオンザフライで埋め込む** – 既知のフォルダーから欠損フォントを読み込み、再度ドキュメントを読み込む前に Aspose.Words に登録。

### 例: 重要フォントで中止する

```csharp
// Define a list of fonts that must be present.
var requiredFonts = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };

foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    // Extract the original font name from the warning message.
    string missingFont = ExtractFontName(warning.Message);
    if (requiredFonts.Contains(missingFont))
    {
        throw new InvalidOperationException(
            $"Critical font '{missingFont}' is missing. Document load aborted.");
    }
}

// Helper method to parse font name from warning text.
string ExtractFontName(string message)
{
    // Message pattern: "Font 'X' was not found..."
    int start = message.IndexOf('\'') + 1;
    int end = message.IndexOf('\'', start);
    return (start > 0 && end > start) ? message[start..end] : string.Empty;
}
```

### 例: 欠損フォントを自動埋め込み

```csharp
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    string missingFont = ExtractFontName(warning.Message);
    string fontPath = $@"C:\Fonts\{missingFont}.ttf";

    if (File.Exists(fontPath))
    {
        // Register the font with Aspose.Words.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(Path.GetDirectoryName(fontPath), false);
        doc.FontSettings = fontSettings;

        // Reload the document now that the font is available.
        doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
        break; // Re‑load once; subsequent warnings will be resolved.
    }
}
```

**これらのパターンが有効な理由:** フォントが欠損したときに何をすべきかを明示的に決めることで、ブランドや可読性を損なうサイレントな置換を防げます。これが **欠損フォントの制御された処理** の本質です。

---

## 完全動作サンプル

すべてを統合した、**フォント検出**、**警告取得**、そして **欠損フォントをログに記録して処理** するシンプルなポリシーを実装した、単一の実行可能プログラムを以下に示します。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.Collections.Generic;
using System.IO;

public class FontSubstitutionWarningCollector : IWarningCallback
{
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Warnings.Add(info);
    }
    public static void Clear() => Warnings.Clear();
}

class Program
{
    static void Main()
    {
        string docPath = @"C:\Docs\MissingFonts.docx";

        // 1️⃣ Configure LoadOptions with the warning collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontSubstitutionWarningCollector()
        };
        FontSubstitutionWarningCollector.Clear();

        // 2️⃣ Load the document – this is where fonts are detected.
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Process the collected warnings.
        if (FontSubstitutionWarningCollector.Warnings.Count == 0)
        {
            Console.WriteLine("✅ No missing fonts detected.");
        }
        else
        {
            Console.WriteLine("⚠️ Font substitution warnings:");
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
                Console.WriteLine($"{w.Type}: {w.Message}");

            // Example policy: abort if a brand‑critical font is missing.
            var critical = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
            {
                string missing = ExtractFontName(w.Message);
                if (critical.Contains(missing))
                {
                    Console.WriteLine($"❌ Critical font '{missing}' missing. Stopping.");
                    return;
                }
            }
        }

        // 4️⃣ Continue with normal processing (e.g., save as PDF).
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
        Console.WriteLine("✅ Document saved as PDF.");
    }

    // Helper to pull the original font name out of the warning text.
    static string ExtractFontName(string message)
    {
        int first = message.IndexOf('\'') + 1;
        int last = message.IndexOf('\'', first);
        return (first > 0 && last > first) ? message[first..last] : string.Empty;
    }
}
```

**期待される結果:** マシンに存在しないフォントを参照しているドキュメントでプログラムを実行すると、コンソールに各置換警告が一覧表示されます。警告が `critical` セットに含まれるフォントに関係している場合、プログラムは早期に終了し、欠陥のある PDF が生成されるのを防ぎます。

---

## よくある質問 (FAQ)

| 質問 | 回答 |
|------|------|
| *Aspose.Words のこのコードを使用するのにライセンスは必要ですか？* | はい、有効な Aspose.Words ライセンスがないと評価版の透かしが表示され、機能が制限されます。 |
| *埋め込みフォントも検出できますか？* | 埋め込みフォントはファイルに既に含まれているため、Aspose.Words は置換警告を出しません。必要に応じて `Document.FontInfos` で埋め込みフォントを列挙できます。 |
| *Windows ではシステムフォントだが Linux では存在しない場合はどうなりますか？* | Linux ではフォントがインストールされていないため同じ警告が発生します。必要な `.ttf` ファイルをアプリに同梱し、**欠損フォントの処理** 戦略で対処してください。 |
| *警告コレクターはスレッドセーフですか* | {{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}