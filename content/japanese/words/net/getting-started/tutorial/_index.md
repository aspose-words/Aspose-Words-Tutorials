---
language: ja
url: /japanese/net/getting-started/tutorial/
---

{{< layout-start >}}

{{< layout-start >}}

```yaml
---
title: "Detect Missing Fonts in Aspose.Words Documents – Complete C# Guide"
description: "Detect missing fonts in your Aspose.Words documents using a warning callback. Learn how to log font substitutions with C# and keep your PDFs looking right."
date: 2025-12-08
draft: false
language: "en"
category: "general"
url: "PLACEHOLDER_URL"
keywords:
  - detect missing fonts
  - Aspose.Words warning callback
  - font substitution
  - LoadOptions C#
  - document loading C#
  - missing font detection
tags:
  - Aspose.Words
  - C#
  - Font Management
og_title: "Detect Missing Fonts in Aspose.Words – Step‑by‑Step C# Guide"
og_description: "Detect missing fonts in Aspose.Words documents instantly. Follow this guide to set up a warning callback and capture font substitution events in C#."
---
```

# Aspose.Words ドキュメントにおける欠損フォントの検出 – 完全 C# ガイド

Aspose.Words で Word ファイルを読み込むときに **欠損フォントを検出** する方法を考えたことはありますか？日常業務の中で、元のドキュメントがインストールされていないフォントを使用していたために、見た目が崩れた PDF に何度か遭遇しました。良いニュースは、Aspose.Words がフォントを置き換えるタイミングを正確に教えてくれ、シンプルな warning コールバックでその情報を取得できることです。

このチュートリアルでは、**完全で実行可能なサンプル**を通して、すべてのフォント置換をログに記録する方法、コールバックが重要な理由、そして堅牢な欠損フォント検出のためのいくつかの追加テクニックを紹介します。余計な説明は省き、今日すぐに動作させるために必要なコードと考え方だけを提供します。

---

## 学べること

- **Aspose.Words warning コールバック** を実装してフォント置換イベントを捕捉する方法。  
- **LoadOptions C#** を設定し、ドキュメント読み込み時にコールバックが呼び出されるようにする方法。  
- 欠損フォント検出が実際に機能したかを検証し、コンソール出力がどのようになるかを確認する方法。  
- 大量バッチやヘッドレス環境向けのオプション調整。

**Prerequisites** – 最近の Aspose.Words for .NET（コードは 23.12 でテスト）と .NET 6 以降、そして C# の基本的な知識が必要です。これらが揃っていればすぐに始められます。

---

## Warning コールバックで欠損フォントを検出する

このソリューションの核心は `IWarningCallback` の実装です。Aspose.Words はさまざまな状況で `WarningInfo` オブジェクトを発行しますが、ここでは `WarningType.FontSubstitution` のみを対象とします。実際にフックする方法を見てみましょう。

### Step 1: Font‑Warning コレクタの作成

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    // The Warning method is called automatically by the library.
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

*Why this matters*: `WarningType.FontSubstitution` でフィルタリングすることで、無関係な警告（例: 非推奨機能）によるノイズを防げます。`info.Description` には元のフォント名と使用された代替フォントがすでに含まれているため、明確な監査トレイルが得られます。

---

## コールバックを使用するように LoadOptions を設定する

ここで、Aspose.Words にファイル読み込み時にコレクタを使用するよう指示します。

### Step 2: LoadOptions の設定

```csharp
// Create a LoadOptions instance – this controls how the document is read.
LoadOptions loadOptions = new LoadOptions
{
    // Assign our custom warning callback.
    WarningCallback = new FontWarningCollector()
};
```

*Why this matters*: `LoadOptions` はコールバックや暗号化パスワード、その他の読み込み動作を設定できる唯一の場所です。`Document` コンストラクタから分離しておくことで、複数のファイルでコードを再利用しやすくなります。

---

## ドキュメントを読み込み、欠損フォントを取得する

コールバックが設定されたら、次は単にドキュメントを読み込むだけです。

### Step 3: DOCX（またはサポートされている任意の形式）を読み込む

```csharp
// Replace the path with the location of your test document.
string inputPath = @"C:\Docs\input.docx";

try
{
    // The warning callback fires automatically during this call.
    Document doc = new Document(inputPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    // Handle file‑not‑found, access‑denied, etc.
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

`Document` コンストラクタがファイルを解析すると、欠損フォントがある場合に `FontWarningCollector` が呼び出されます。コンソールには次のような行が表示されます。

```
Font substituted: Arial (substituted with Liberation Sans)
Document loaded successfully.
```

この行が **欠損フォントの検出** が機能したことを示す具体的な証拠です。

---

## 出力の確認 – 期待される結果

ターミナルまたは Visual Studio からプログラムを実行します。ソースドキュメントにインストールされていないフォントが含まれている場合、少なくとも1行の “Font substituted” が表示されます。ドキュメントがインストール済みフォントのみを使用している場合、コールバックは何も出力せず、 “Document loaded successfully.” メッセージだけが表示されます。

**Tip**: 再確認するには、Microsoft で該当の Word ファイルを開き、フォント一覧を確認します。*Home → Font* グループの *Replace Fonts* に表示されるフォントは、置き換えの対象となり得ます。

---

## 高度な使用法: バルクで欠損フォントを検出する

多数のファイルをスキャンする必要があることがよくあります。同じパターンはスケーラブルです。

```csharp
string[] files = Directory.GetFiles(@"C:\Docs\Batch", "*.docx");

foreach (var file in files)
{
    Console.WriteLine($"\nProcessing: {Path.GetFileName(file)}");
    Document doc = new Document(file, loadOptions);
}
```

`FontWarningCollector` は呼び出されるたびにコンソールへ書き込むため、追加の仕組みなしでファイルごとのレポートが得られます。実運用ではファイルやデータベースへのログ出力が必要になる場合があります。その際は `Console.WriteLine` を好みのロガーに置き換えるだけです。

---

## よくある落とし穴とプロのコツ

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| **警告が表示されない** | ドキュメントに実際にインストール済みフォントしか含まれていないためです。 | Word でファイルを開くか、システムからフォントを意図的に削除して確認してください。 |
| **コールバックが呼び出されない** | `LoadOptions.WarningCallback` が設定されていない、または後で新しい `LoadOptions` インスタンスが使用されたためです。 | 単一の `LoadOptions` オブジェクトを保持し、すべてのロードで再利用してください。 |
| **無関係な警告が多すぎる** | `WarningType.FontSubstitution` でフィルタリングしていないためです。 | 示したように `if (info.Type == WarningType.FontSubstitution)` ガードを追加してください。 |
| **大容量ファイルでのパフォーマンス低下** | コールバックがすべての警告で実行され、大きなドキュメントでは警告が多数発生するためです。 | `LoadOptions.WarningCallback` で他の警告タイプを無効化するか、既知の場合は `LoadOptions.LoadFormat` を特定の形式に設定してください。 |

---

## 完全動作例（コピー＆ペースト可能）

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 2 – configure LoadOptions with our warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCollector()
        };

        // Path to a single document or a folder for batch processing.
        string inputPath = @"C:\Docs\input.docx";

        try
        {
            // Step 3 – load the document; warnings are emitted automatically.
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**期待されるコンソール出力**（欠損フォントが検出された場合）:

```
Font substituted: Times New Roman (substituted with Liberation Serif)
Document loaded successfully.
```

置き換えが発生しなければ、成功行だけが表示されます。

---

## 結論

これで、Aspose.Words が処理するあらゆるドキュメントに対して **完全な、プロダクション対応の欠損フォント検出方法** を手に入れました。**Aspose.Words warning コールバック** を活用し、**LoadOptions C#** を設定することで、すべてのフォント置換をログに記録し、レイアウト問題をトラブルシュートし、PDF が意図した外観と感触を保つことができます。

単一ファイルから大量バッチまで、パターンは同じです。`IWarningCallback` を実装し、`LoadOptions` に組み込み、Aspose.Words に重い処理を任せましょう。

次のステップに進む準備はできましたか？この手法を **font embedding** や **fallback font families** と組み合わせて自動的に問題を解決したり、**DocumentVisitor** API を使ってより深いコンテンツ分析に挑戦したりしてみてください。コーディングを楽しみ、すべてのフォントが期待通りの場所にあることを願っています！

---

![Detect missing fonts in Aspose.Words – console output screenshot](https://example.com/images/detect-missing-fonts.png "detect missing fonts console output")

{{< layout-end >}}

{{< layout-end >}}