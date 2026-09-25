---
category: general
date: 2026-02-28
description: C# を使用して Aspose.Words でフォント警告の処理方法と欠落フォントの検出方法を学びましょう。完全なコード付きのステップバイステップガイドです。
draft: false
keywords:
- handle font warnings
- detect missing fonts
language: ja
og_description: Aspose.Words でフォント警告を処理し、実行可能な C# のサンプルで欠落フォントを検出します。手順に従って出力をご確認ください。
og_title: Aspose.Words のフォント警告の対処 – 完全ガイド
tags:
- Aspose.Words
- C#
- Document Loading
title: Aspose.Wordsでフォント警告を処理する – 欠落フォントを検出
url: /ja/net/working-with-fonts/handle-font-warnings-in-aspose-words-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words のフォント警告の処理 – 欠落フォントの検出

Word ドキュメントを読み込むときに **フォント警告を処理** したことがありますか？ そして、なぜ一部のテキストが変に見えるのか疑問に思ったことはありませんか？ あなたは一人ではありません。欠落フォントは置換警告を発生させ、視覚的レイアウトを静かに壊すことがあります。 **欠落フォントを検出** しなければ、何が起こったかは分かりません。

このチュートリアルでは、Aspose.Words の `IWarningCallback` を使用して **フォント警告を処理** する実用的な方法を紹介します。ガイドの最後までに、すべてのフォント置換イベントを検出し、ログに記録し、ロードを中止するかどうかを判断できるようになります。外部ドキュメントは不要で、コピー＆ペーストだけで使える単一のサンプルです。

## 学習できること

- フォント置換アラートのみに反応するカスタム警告ハンドラを設定する。  
- ハンドラを `LoadOptions` に添付し、すべてのドキュメント読み込みで実行させる。  
- コンソール出力を確認し、各警告が何を意味するかを理解する。  

**Prerequisites**

- .NET 6.0 以降（コードは .NET Framework 4.6+ でも動作します）。  
- NuGet でインストールした Aspose.Words for .NET（`Install-Package Aspose.Words`）。  
- マシンにインストールされていないフォントを参照している Word ファイル（例：カスタム社内フォント）。  

これらが揃っていない場合は、まず入手してください。準備ができたら、さっそく始めましょう。

## Aspose.Words でフォント警告を処理する方法

以下は完全に実行可能なプログラムです。`using` 文から `Main` メソッドまで含まれているので、コンソール アプリに貼り付けて **F5** で実行できます。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

/// <summary>
/// Custom warning handler that reacts only to font‑substitution warnings.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font substitution events.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a clear message to the console – this is how we **detect missing fonts**.
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 1: Create LoadOptions and attach the custom warning callback.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // Step 2: Load the document. Any missing font will trigger our handler.
        // Replace the path with the actual location of your test document.
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        // Keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

> **期待されるコンソール出力**（ドキュメントがインストールされていないフォントを使用している場合）  
> ```
> ⚠️ Font substituted: Font 'MyCustomFont' was substituted with 'Arial'.
> ✅ Document loaded successfully.
> 
> Press any key to exit...
> ```

ドキュメントに **欠落フォントがない** 場合、警告行は表示されません。つまり、**欠落フォントを検出** したときだけ警告が出る仕組みです。

### なぜこれが機能するのか

Aspose.Words はファイルを解析中に遭遇したすべての非致命的問題について `WarningInfo` をスローします。`IWarningCallback` を実装することで、そのパイプラインにフックできます。`WarningType.FontSubstitution` フラグは、ライブラリが要求されたフォントをフォールバックに置き換えた正確なタイミングを示します。これはロード中に実行され、ドキュメント オブジェクト モデルに触れる前に動作するため、**フォント警告を処理** する最も信頼できる方法です。

## アプリを壊さずに欠落フォントを検出する

場合によっては、欠落フォントを致命的エラーとして扱いたいことがあります。たとえば、ブランド ガイドラインで置換を禁止している場合です。ハンドラを変更して、単にログに記録するだけでなく例外をスローさせることができます。

```csharp
public void Warning(WarningInfo info)
{
    if (info.WarningType == WarningType.FontSubstitution)
    {
        // Throwing stops the load process; you can catch it higher up.
        throw new InvalidOperationException($"Missing font detected: {info.Description}");
    }
}
```

これで `new Document(...)` を囲む `try…catch` ブロックが問題を捕捉し、ロードを中止するか、フォールバックするか、ユーザーに促すかを自由に決められます。

## ボーナス: UI アプリケーションで警告を可視化する

WinForms や WPF アプリを作成している場合は、`Console.WriteLine` を UI フレンドリーな呼び出しに置き換えてください。

```csharp
MessageBox.Show($"Font substituted: {info.Description}", "Font Warning",
                MessageBoxButtons.OK, MessageBoxIcon.Warning);
```

これによりエンドユーザーは警告をすぐに確認でき、すべてのプラットフォームで **フォント警告を処理** する一貫性が保たれます。

## よくある落とし穴 & プロのコツ

- **Pitfall:** `WarningCallback` を設定し忘れること。デフォルトの動作はフォント警告を無視するため、警告は一切表示されません。  
  **Pro tip:** 警告ハンドラだけが必要な場合でも、必ず `LoadOptions` インスタンスを作成してください。コストは低く、明示的です。  

- **Pitfall:** 非 Windows OS でパス区切り文字を間違えること。  
  **Pro tip:** `Path.Combine` を使用するか、文字列リテラルをそのまま書きます（Windows では `@"C:\Docs\MissingFont.docx"`、Linux では `"/home/user/docs/MissingFont.docx"`）。  

- **Pitfall:** 埋め込みフォントでも警告が発生すると想定すること。  
  **Pro tip:** 埋め込みフォントは「存在する」とみなされるため、置換警告は出ません。本当に *欠落* しているフォントでハンドラをテストしてください。  

- **Pitfall:** すべての警告タイプを過剰にログ出力すること。  
  **Pro tip:** 示したように `WarningType.FontSubstitution` でフィルタリングすれば、コンソールがすっきりし、**欠落フォントの検出** シナリオに集中できます。  

## 完全動作サンプルのまとめ

コメントを除いたクリーンなコードを好む方向けに、プログラム全体を再掲します。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
    }
}

class Program
{
    static void Main()
    {
        var loadOptions = new LoadOptions { WarningCallback = new FontWarningHandler() };
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

コピーして貼り付け、実行してください。コンソールが自動的に **フォント警告を処理** し、**欠落フォントを検出** します。

## 次のステップ

- **ファイルへのログ出力:** `Console.WriteLine` をロガー（例: NLog）に置き換えて、本番環境向けのトレースを実装。  
- **バッチ処理:** フォルダー内の複数ドキュメントをループし、すべてのフォント置換イベントを CSV レポートに集計。  
- **自動フォントインストール:** 警告ハンドラで企業リポジトリから欠落フォントをダウンロードし、ロードを続行できるようにフック。  

これらの拡張はすべて、**フォント警告を処理** するというコアアイデアをクリーンで再利用可能な形で活かすものです。

---

*Happy coding! If you run into any quirks while trying to **detect missing fonts**, drop a comment below. I’ll gladly help you troubleshoot.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}