---
category: general
date: 2026-03-17
description: Aspose.Words と警告コールバックを使用して C# でフォントを検出する方法。ドキュメントの読み込み時に欠落フォントの置換を取得するためのコールバックの使い方を学びます。
draft: false
keywords:
- how to detect fonts
- how to use callback
- Aspose.Words font detection
- C# missing font warning
- warning callback example
language: ja
og_description: Aspose.Words を使用して C# でフォントを検出する方法。このガイドでは、ドキュメントの読み込み中に欠落フォントの警告を取得するためにコールバックを使用する方法を示します。
og_title: C#でフォントを検出する方法 – Aspose.Wordsでコールバックを使用
tags:
- Aspose.Words
- C#
- Document Processing
title: C#でフォントを検出する方法 – Aspose.Wordsでコールバックを使用
url: /ja/net/working-with-fonts/how-to-detect-fonts-in-c-use-callback-with-aspose-words/
---

Now produce final answer.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#でフォントを検出する方法 – Aspose.Words のコールバックを使用

Word 文書内のフォントをプログラムで **検出する方法** が必要で、変換後に文字が変に見えることに悩んだことはありませんか？ 同じ悩みを抱える方は多いです。請求書ジェネレータ、レポートエクスポーター、バッチ処理パイプラインなど、実務の多くのプロジェクトでフォントが欠如していると、デバッグが困難なレイアウトの不具合が静かに発生します。  

朗報です！ Aspose.Words では、警告コールバックを使ってこれらの問題を明確に把握できるクリーンな方法が提供されています。このチュートリアルでは、ドキュメントの読み込み時に Aspose が実行するすべてのフォント置換をキャプチャする **コールバックの使用方法** を紹介し、欠落フォントのレポートを出力する実行可能なサンプルを手に入れられます。

取り上げる内容:

* 最小限の前提条件（.NET プロジェクトと Aspose.Words NuGet パッケージ）。  
* `IWarningCallback` を実装して `WarningType.FontSubstitution` を監視する方法。  
* コールバックを `LoadOptions` に組み込み、ドキュメントを読み込む手順。  
* 出力例と、実運用コード向けの実用的なヒント。

このチュートリアルを終える頃には、任意の DOCX、DOC、RTF ファイルに対して自動的に **フォントを検出** し、欠落フォント情報に基づいてログ記録、ユーザー通知、フォールバックフォントへの置換などの処理ができるようになります。

---

![Word 文書でフォントを検出する方法 – Aspose.Words の警告コールバック](https://example.com/images/detect-fonts.png "Word 文書でフォントを検出する方法")

## 必要な環境

* **.NET 6.0** 以上（例は .NET Framework 4.6+ でもコンパイル可能）。  
* **Aspose.Words for .NET** – NuGet でインストール: `Install-Package Aspose.Words`。  
* 故意にインストールされていないフォントを参照しているサンプル Word ファイル（例: `MissingFont.docx`）。  

追加のライブラリは不要です。すべて Aspose 名前空間内に収まっています。

---

## 警告コールバックでフォントを検出する手順

### 手順 1: 警告コールバック クラスを作成

このコールバックは `IWarningCallback` を実装します。Aspose.Words が見つからないフォントに遭遇すると、`WarningInfo` として `WarningType.FontSubstitution` が発生します。クラスはコンソールに分かりやすい行を出力するだけです。

```csharp
using System;
using Aspose.Words.Warnings;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about missing‑font warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Example output: [Font substitution] Missing: "Comic Sans MS"
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
        }
    }
}
```

**重要ポイント:** `WarningType.FontSubstitution` のみをフィルタリングすることで、非推奨機能などの騒がしい警告を除外し、**フォントが存在しないことの検出** に焦点を当てたログを実現できます。

---

### 手順 2: `LoadOptions` にコールバックを組み込む

`LoadOptions` はドキュメントの解析方法をカスタマイズできます。`WarningCallback` プロパティに先ほどの `FontWarningCollector` を設定すると、欠落フォントが検出されるたびにコールバックが呼び出されます。

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Configure load options with our custom warning handler.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**ヒント:** ここで `LoadOptions.FontSettings` を設定すれば、プログラム上でフォールバックフォントを指定できます。高度なシナリオは後述します。

---

### 手順 3: ドキュメントを読み込み、出力を確認

実際にファイルを読み込みます。Aspose がドキュメントを解析すると、見つからないフォントがあれば即座にコールバックがトリガーされます。

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\MissingFont.docx";

try
{
    Document doc = new Document(docPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
}
```

**期待されるコンソール出力**（例として *Comic Sans MS* がインストールされていない場合）:

```
[Font substitution] Missing: "Comic Sans MS"
Document loaded successfully.
```

複数の欠落フォントがある場合は、フォントごとに 1 行ずつ表示されます。これが **フォント検出** に必要な情報です。

---

## コールバックを使った応用シナリオ

### コンソールではなくファイルへログ出力

本番環境では永続的なログが必要になることが多いです。`Console.WriteLine` を `StreamWriter` に置き換えてください。

```csharp
class FontWarningCollector : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            File.AppendAllText(_logPath,
                $"[Font substitution] Missing: {info.Description}{Environment.NewLine}");
        }
    }
}
```

### 後で分析できるように警告を収集

ドキュメント読み込み後に欠落フォント一覧を取得したい場合があります。`List<string>` に警告を格納し、外部から参照できるようにします。

```csharp
class FontWarningCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}

// Usage
var collector = new FontWarningCollector();
LoadOptions opts = new LoadOptions { WarningCallback = collector };
Document doc = new Document(docPath, opts);

if (collector.MissingFonts.Any())
{
    Console.WriteLine("Missing fonts detected:");
    collector.MissingFonts.ForEach(f => Console.WriteLine($"- {f}"));
}
```

### プログラム上でフォールバックフォントを提供

社内で統一したフォントを強制したい場合は、読み込み前に `FontSettings` にフォントを追加します。

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";

LoadOptions opts = new LoadOptions
{
    WarningCallback = new FontWarningCollector(),
    FontSettings = fontSettings
};

Document doc = new Document(docPath, opts);
```

これにより、Aspose は欠落フォントを *Arial Unicode MS* に置換しつつ、コールバックで置換情報を報告します。**コールバックの使用** で検出と自動修正の両方を実現できる便利な手法です。

---

## よくある落とし穴とプロのコツ

| 落とし穴 | 発生理由 | 回避策 |
|--------|----------|--------|
| **`Aspose.Words.Warnings` の参照忘れ** | `IWarningCallback` インターフェイスはこの名前空間にあります。 | ファイル冒頭に `using Aspose.Words.Warnings;` を追加。 |
| **`LoadOptions` を使わずにドキュメントを読み込む** | デフォルトローダーは警告なしでフォントを置換します。 | 必ず `LoadOptions` インスタンスを作成し、コールバックを設定。 |
| **権限が制限されたサーバーで実行** | ログファイルへの書き込みで `UnauthorizedAccessException` が発生する可能性。 | 書き込み可能なフォルダー（例: アプリのデータディレクトリ）を使用するか、メモリ内コレクションに留める。 |
| **複数スレッドで同じコレクタを共有** | `FontWarningCollector` はデフォルトでスレッドセーフではありません。 | スレッドごとに別々のコレクタを作成するか、リストにロックを掛ける。 |
| **埋め込みフォントでもコールバックが発火すると想定** | 埋め込みフォントはドキュメントに既に含まれているため警告は出ません。 | 埋め込みフォントの整合性を確認したい場合は、`FontSettings` 経由で `FontInfo` を調べます。 |

---

## 完全動作サンプル（コピー＆ペーストで使用可能）

```csharp
// ------------------------------------------------------------
// Detect missing fonts in a Word document using Aspose.Words
// ------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningCollector : IWarningCallback
{
    // Store warnings for later use (optional)
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Print to console
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
            // Keep a copy in memory
            MissingFonts.Add(info.Description);
        }
    }
}

class Program
{
    static void Main()
    {
        // Path to the document you want to inspect
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

        // 1️⃣ Create the callback collector
        var collector = new FontWarningCollector();

        // 2️⃣ Set up LoadOptions with the callback
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = collector
        };

        // 3️⃣ Load the document – warnings will fire automatically
        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");

            // Optional: act on the collected data
            if (collector.MissingFonts.Count > 0)
            {
                Console.WriteLine("\nSummary of missing fonts:");
                foreach (var font in collector.MissingFonts)
                    Console.WriteLine($"- {font}");
            }
            else
            {
                Console.WriteLine("\nNo missing fonts detected.");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**期待される出力例**（欠落フォントが 2 つある場合）:

```
[Font substitution] Missing: "Comic Sans MS"
[Font substitution] Missing: "Papyrus"
Document loaded successfully.

Summary of missing fonts:
- Comic Sans MS
- Papyrus
```

インストール済みフォントしか使用していない場合、コンソールには次のように表示されます:

```
Document loaded successfully.

No missing fonts detected.
```

---

## まとめ

本稿では、Aspose.Words にカスタム警告コールバックを組み込むことで **Word 文書内のフォントを検出** する方法を解説しました。この手法は軽量で、以下の要件を満たします

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}