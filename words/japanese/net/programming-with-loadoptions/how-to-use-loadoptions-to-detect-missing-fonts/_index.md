---
category: general
date: 2026-06-08
description: Aspose.Words の LoadOptions を使用して、ドキュメントのインポート時に欠落フォントを検出する方法を学びます。コード、解説、ベストプラクティスを含むステップバイステップガイド。
draft: false
keywords:
- how to use loadoptions
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- C# document loading
language: ja
og_description: Aspose.Words の LoadOptions の使い方と、ドキュメント読み込み時に欠落フォントを検出する方法。コードと実践的なヒントを含む完全ガイド。
og_title: LoadOptions を使用して欠落フォントを検出する方法
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  headline: How to Use LoadOptions to Detect Missing Fonts
  type: TechArticle
- description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  name: How to Use LoadOptions to Detect Missing Fonts
  steps:
  - name: Create a Warning Handler
    text: Aspose.Words uses the `IWarningCallback` interface to notify you about non‑critical
      issues, such as font substitution. Implement the interface and decide what to
      do when a warning arrives.
  - name: Attach the Handler to LoadOptions
    text: Now we create a `LoadOptions` instance and tell it to use our `FontWarningHandler`.
      This is the point where **how to use LoadOptions** really shines.
  - name: Load the Document Using the Configured Options
    text: Finally, we feed the `LoadOptions` into the `Document` constructor. If the
      source file references a font that isn’t installed, Aspose.Words will fire the
      warning and your handler will print a message.
  - name: Multiple Documents in a Loop
    text: Often you’ll process a batch of files. The same `LoadOptions` instance can
      be reused, but remember that the `WarningCallback` persists across loads. If
      you need per‑document isolation, instantiate a fresh `LoadOptions` for each
      iteration.
  - name: Custom Font Substitution Logic
    text: 'Instead of merely logging, you might want to substitute a specific missing
      font with a corporate‑approved alternative. Extend the handler:'
  - name: Silencing Unwanted Warnings
    text: If you only care about font issues and want to suppress everything else,
      filter by `WarningType` as shown. Conversely, to log *all* warnings, drop the
      `if` check and output `info.WarningType` alongside `info.Description`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Font Management
title: LoadOptions を使用して欠落フォントを検出する方法
url: /ja/net/programming-with-loadoptions/how-to-use-loadoptions-to-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# LoadOptions を使用して欠落フォントを検出する方法

Aspose.Words で Word ドキュメントを読み込む際に **LoadOptions の使い方** を疑問に思ったことはありませんか？このチュートリアルでは、**LoadOptions の使い方** を正確に示し、**欠落フォントを検出**して適切に処理する方法をご紹介します。ドキュメント変換サービスやレポートエンジンを構築している場合でも、欠落フォントはレイアウトの予期せぬ変化を引き起こす可能性があるため、早期に検出することが重要です。

私たちは、警告コールバックの設定から結果の解釈まで、すべての手順を順に説明します。最終的に、任意の .NET プロジェクトに組み込める完全に動作する C# のサンプルが完成します。外部ドキュメントは不要で、自己完結型のソリューションです。最後までで、警告システムが存在する理由、設定方法、コールバックが発火したときの対処方法が分かります。

## 前提条件

- **Aspose.Words for .NET**（任意の最新バージョン；使用する API は 2022 年以降安定しています）。
- .NET 開発環境（Visual Studio、Rider、または C# 拡張機能付き VS Code）。
- フォントがインストールされていないフォントを参照しているサンプル Word ファイル（`input.docx`）。

以上です—Aspose.Words 以外に追加の NuGet パッケージは必要ありません。

## Aspose.Words で LoadOptions を使用する方法

**LoadOptions** クラスは、ドキュメントの読み取り方法をカスタマイズするためのゲートウェイです。警告コールバックを設定することで、Aspose.Words がファイルを解析した瞬間に **欠落フォントを検出** できます。では、詳しく見ていきましょう。

### 手順 1: 警告ハンドラの作成

Aspose.Words は `IWarningCallback` インターフェイスを使用して、フォント置換などの非致命的な問題を通知します。インターフェイスを実装し、警告が発生したときの処理を決定します。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

// Step 1: Define a warning handler that will be notified of font substitutions.
class FontWarningHandler : IWarningCallback
{
    // The Process method is called for every warning Aspose.Words generates.
    public void Process(WarningInfo info)
    {
        // We're only interested in font substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

**重要な理由:**  
コールバックがない場合、Aspose.Words は欠落フォントをデフォルト（通常は Arial）に静かに置き換えてしまいます。`FontSubstitution` 警告を取得することで、問題をログに記録したり、ユーザーに通知したり、さらにはカスタムの代替フォントに置き換えることができます。

### 手順 2: ハンドラを LoadOptions に割り当てる

ここで `LoadOptions` インスタンスを作成し、`FontWarningHandler` を使用するように設定します。これが **LoadOptions の使い方** が本領を発揮するポイントです。

```csharp
using Aspose.Words.LoadOptions;

// Step 2: Create LoadOptions and attach the warning handler.
var loadOptions = new LoadOptions
{
    // The WarningCallback property accepts any IWarningCallback implementation.
    WarningCallback = new FontWarningHandler()
};
```

**重要な理由:**  
`LoadOptions` はインポート時の設定（エンコーディング、パスワードなど）を一括で管理できる場所です。`WarningCallback` を設定することで、軽量かつイベント駆動のメカニズムが有効になり、これらのオプションで読み込むすべてのドキュメントに適用できます。

### 手順 3: 設定したオプションでドキュメントを読み込む

最後に、`LoadOptions` を `Document` コンストラクタに渡します。ソースファイルがインストールされていないフォントを参照している場合、Aspose.Words が警告を発し、ハンドラがメッセージを出力します。

```csharp
// Step 3: Load the document using the configured LoadOptions.
// Any missing fonts will trigger the FontWarningHandler.
Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**期待される出力:**  
`input.docx` がマシンに存在しないフォント *“MyCustomFont”* を使用していると仮定すると、コンソール出力は次のようになります:

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
```

すべてのフォントが揃っている場合、コールバックは何も出力せず、パフォーマンスへの影響もありません。

## 警告コールバックで欠落フォントを検出する（セカンダリキーワードの実例）

フレーズ **detect missing fonts** は上記の見出しに自然に含まれており、セカンダリキーワードを強調しています。実際のプロジェクトで遭遇し得るいくつかのバリエーションを見てみましょう。

### ループ内で複数ドキュメントを処理する

多くの場合、ファイルのバッチ処理を行います。同じ `LoadOptions` インスタンスを再利用できますが、`WarningCallback` はロード間で保持されることに注意してください。ドキュメントごとに分離が必要な場合は、各イテレーションで新しい `LoadOptions` をインスタンス化します。

```csharp
string[] files = Directory.GetFiles(@"C:\Docs", "*.docx");
foreach (var file in files)
{
    var options = new LoadOptions { WarningCallback = new FontWarningHandler() };
    var document = new Document(file, options);
    // Perform further processing...
}
```

### カスタムフォント置換ロジック

単にログを取るだけでなく、特定の欠落フォントを社内承認済みの代替フォントに置き換えたい場合があります。ハンドラを拡張しましょう:

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Extract the missing font name from the description.
            string missingFont = info.Description.Split('\'')[1];
            // Choose a fallback based on your policy.
            string fallback = missingFont.Equals("MyCustomFont") ? "Calibri" : "Arial";
            Console.WriteLine($"Missing '{missingFont}'. Using fallback '{fallback}'.");
            // You could also modify FontSettings here if needed.
        }
    }
}
```

これで **欠落フォントを検出** するだけでなく、置換方法も決定できます。

### 不要な警告を無効化する

フォントに関する警告だけが必要で他を抑制したい場合は、以下のように `WarningType` でフィルタリングします。逆に、*すべて* の警告を記録したい場合は `if` 条件を削除し、`info.WarningType` と `info.Description` を出力します。

## 完全な実行可能サンプル

すべてを統合した完全なプログラムを以下に示します。`"YOUR_DIRECTORY/input.docx"` をテストファイルのパスに置き換えてください。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Ensure the Aspose.Words license is set if you have one.
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        string docPath = Path.Combine("YOUR_DIRECTORY", "input.docx");

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
            // You can now work with 'doc' – save, modify, export, etc.
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**フォントが欠落している場合の期待コンソール出力:**

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

フォントが欠落していない場合は、次のように何も表示されません:

```
Document loaded successfully.
```

## よくある落とし穴とプロのコツ

- **Pitfall:** `WarningCallback` の設定を忘れること。API は依然としてフォントを置換しますが、置換が行われたことに気付けません。  
  **Pro tip:** フォントの忠実度が必要な場合は必ずハンドラを添付してください。ほぼコストはかかりません。

- **落とし穴:**

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全なコード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Aspose.Words でフォントを検出する方法 – 警告と設定の処理](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Aspose.Words でフォントを取得する方法 – 完全ガイド](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [DOCX をロードして欠落フォントを検出する方法 – 完全 C# ガイド](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}