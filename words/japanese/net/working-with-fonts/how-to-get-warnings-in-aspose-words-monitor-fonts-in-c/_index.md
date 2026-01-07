---
category: general
date: 2026-01-06
description: Aspose.Words を使用してドキュメントを読み込む際の警告取得方法とフォントの監視方法を学びます。このガイドでは、警告コールバックとフォント置換の追跡について説明します。
draft: false
keywords:
- how to get warnings
- how to monitor fonts
- Aspose.Words warning callback
- font substitution detection
- document load options
language: ja
og_description: Aspose.Wordsで警告を取得する方法は？ステップバイステップのチュートリアルに従って、フォントを監視し、ドキュメントを読み込む際の置換メッセージを取得してください。
og_title: Aspose.Wordsで警告を取得する方法 – フォントを監視
tags:
- Aspose.Words
- C#
- Font Monitoring
title: Aspose.Wordsで警告を取得する方法 – C#でフォントを監視する
url: /ja/net/working-with-fonts/how-to-get-warnings-in-aspose-words-monitor-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Wordsで警告を取得する方法 – C#でフォントを監視する

Word文書にインストールされていないフォントが含まれているときに **警告を取得する方法** を考えたことはありますか？これは一般的な問題で、アプリは欠損フォントを静かに置き換えてしまい、何が変わったか分かりません。良いニュースは、Aspose.Wordsの警告システムにフックして、リアルタイムで **フォントを監視** できることです。

このチュートリアルでは、フォント置換警告を正確にキャプチャする方法、その重要性、取得した情報をどう活用するかを示します。外部ドキュメントは不要で、今すぐ Visual Studio に貼り付けて実行できる完全なサンプルコードを提供します。

> **Pro tip:** ドキュメント変換パイプラインを構築している場合、欠損フォントを早期にログに記録することで、後続のレイアウト崩れを防げます。

---

## 必要なもの

- **Aspose.Words for .NET**（最新バージョン；API は v23.10 以降変更なし）
- .NET 開発環境（Visual Studio、Rider、または C# 拡張機能付き VS Code）
- インストールされていないフォントを参照するサンプル `.docx`（例：**“NonExistentFont”**）

以上です—Aspose.Words 以外の NuGet パッケージは不要です。

---

## Step 1 – 警告コレクタの設定 (Primary Keyword in Header)

まず最初に、警告が発生したときに保存しておく場所が必要です。Aspose.Words はこの目的のために `LoadOptions` の `WarningCallback` プロパティを提供しています。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

// Create a collection that will receive every warning emitted during load.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Attach the collector to LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = warningCollector
};
```

**Why this matters:**  
ライブラリが欠損フォントに遭遇したとき、例外はスローせずに `WarningInfo` オブジェクトを発行します。コレクタを設定することで、すべての置換イベントを完全に可視化でき、**フォントを監視**しながらコンソールを無関係なメッセージで汚染しません。

---

## Step 2 – 警告有効オプションでドキュメントを読み込む

次に実際にファイルを読み込みます。前ステップで用意した `LoadOptions` により、フォント関連の警告がすべてキャプチャされます。

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\unknownFont.docx";

Document doc = new Document(docPath, loadOptions);
```

**What’s happening under the hood?**  
Aspose.Words は Word ファイルを解析し、フォントを解決します。要求されたフォントが見つからない場合は代替フォント（通常は Arial）にフォールバックします。このフォールバックが `WarningType.FontSubstitution` 警告をトリガーし、`warningCollector` に格納されます。

---

## Step 3 – 収集した警告を検査する (Primary Keyword Appears Again)

ドキュメントの読み込みが完了したら、`warningCollector` を走査してフォント置換メッセージを出力します。

```csharp
foreach (WarningInfo warning in warningCollector)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        // The Description contains a readable message like:
        // "Font 'NonExistentFont' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warning.Description}");
    }
}
```

**Expected output** (欠損フォントが *“FancyScript”* であると仮定):

```
Substituted font: Font 'FancyScript' was not found. Substituted with 'Arial'.
```

ドキュメントに複数の不明フォントが含まれている場合、置換ごとに 1 行が出力されます—ログやアラートに最適です。

---

## Step 4 – 任意: 警告情報をログまたは永続化する

本番環境では `Console.WriteLine` だけでは不十分なことが多いです。以下は警告を JSON ファイルに書き出す簡易例です。

```csharp
using System.IO;
using System.Text.Json;

// Build a simple DTO.
var warnings = warningCollector
    .Where(w => w.WarningType == WarningType.FontSubstitution)
    .Select(w => new { FontMessage = w.Description })
    .ToList();

string json = JsonSerializer.Serialize(warnings, new JsonSerializerOptions { WriteIndented = true });
File.WriteAllText(@"C:\Logs\font-warnings.json", json);

Console.WriteLine("Font warnings saved to font-warnings.json");
```

これで、監視ダッシュボードに投入したり、欠損フォントファイルの自動取得をトリガーしたりできる永続的な記録が得られます。

---

## Step 5 – 結果を検証しクリーンアップする

プログラムを実行します。置換メッセージが表示されれば **警告を取得** でき、**フォントを監視** していることになります。何も表示されない場合は、テストドキュメントが本当に未インストールのフォントを参照しているか確認してください。

```csharp
// Quick sanity check – print the total number of warnings captured.
Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
```

カウントがゼロになるのは通常、次のいずれかです：

1. すべてのフォントが解決された（フォントがローカルにインストールされている可能性）。
2. ドキュメントに置換が必要なフォント参照が含まれていなかった。

---

## よくある落とし穴と回避策

| Pitfall | Why It Happens | Fix |
|---------|----------------|-----|
| **No warnings appear** | フォントが実際にシステムに存在するか、ドキュメントが組み込みフォントのみ使用している。 | ソースファイル内のフォント名を不可能なもの（例：`XYZ123`）に変更して再試行。 |
| **Too many warnings (noise)** | ループで多数のドキュメントを読み込む際にコレクタをクリアしていない。 | 各ドキュメントごとに `WarningInfoCollection` を再生成するか、処理後に `warningCollector.Clear()` を呼び出す。 |
| **Performance impact** | ディスクへの過剰なロギングがバッチ処理を遅くする。 | 警告をメモリにバッファし、一括書き込みするか、非同期 I/O を使用する。 |
| **Missing `using Aspose.Words.Loading;`** | `LoadOptions` クラスはこの名前空間にある。 | Step 1 に示したように不足している `using` ディレクティブを追加する。 |

---

## ソリューションの拡張 – 他の警告タイプの監視

フォント置換以外にも、Aspose.Words は次のような警告を出すことがあります：

- **Deprecated features** (`WarningType.Deprecated`),
- **Potential data loss** (`WarningType.DataLoss`),
- **Unsupported file formats** (`WarningType.UnsupportedFileFormat`)。

Step 3 のフィルタを拡張すれば、これらも取得できます：

```csharp
if (warning.WarningType != WarningType.None)
{
    Console.WriteLine($"{warning.WarningType}: {warning.Description}");
}
```

これにより、**フォントを監視** だけでなく、アプリケーションが遭遇し得るあらゆるシナリオの **警告を取得** できるようになります。

---

## 完全動作サンプル (コピー＆ペースト可能)

```csharp
using System;
using System.IO;
using System.Linq;
using System.Text.Json;
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1 – Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();
        LoadOptions loadOptions = new LoadOptions { WarningCallback = warningCollector };

        // Step 2 – Load the document (adjust the path to your file).
        string docPath = @"C:\Docs\unknownFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Step 3 – Output font substitution warnings.
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Substituted font: {warning.Description}");
            }
        }

        // Optional Step 4 – Persist warnings to JSON.
        var fontWarnings = warningCollector
            .Where(w => w.WarningType == WarningType.FontSubstitution)
            .Select(w => new { Message = w.Description })
            .ToList();

        string json = JsonSerializer.Serialize(fontWarnings, new JsonSerializerOptions { WriteIndented = true });
        File.WriteAllText(@"C:\Logs\font-warnings.json", json);
        Console.WriteLine("Font warnings saved to font-warnings.json");

        // Step 5 – Quick sanity check.
        Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
    }
}
```

**Run it:** プロジェクトをビルドして実行すると、警告がコンソールに表示され、JSON に保存されます。これが **警告を取得** し、**フォントを監視** するための Aspose.Words 完全解答です。

---

## 結論

これで、特にフォント置換シナリオにおける Aspose.Words の **警告を取得** 方法と、ドキュメント読み込みプロセス全体で **フォントを監視** する方法が分かりました。`WarningCallback` を設定し、収集した `WarningInfo` オブジェクトを列挙し、必要に応じてデータを永続化すれば、欠損フォントイベントを完全に可視化できます—ドキュメント処理パイプラインに不可欠な機能です。

次のステップは？ データ損失や非推奨機能の警告フィルタを拡張したり、JSON ログを Grafana などの監視ダッシュボードに統合したりしてみてください。同じパターンはすべての警告タイプに適用できるので、Aspose.Words が投げるあらゆる問題を確実に把握できるようになります。

Happy coding, and may your documents always render exactly as you expect! 

---

<img src="font-warnings.png" alt="Aspose.Wordsで警告を取得する方法" style="max-width:100%;">

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}