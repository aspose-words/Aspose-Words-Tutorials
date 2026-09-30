---
category: general
date: 2026-03-04
description: Aspose.Words AI を使用して Word 文書を要約します。OpenAI の要約生成方法を学び、C# で OpenAI と Gemini
  の結果を比較します。
draft: false
keywords:
- summarize word document
- ai summary of word
- generate openai summary
- compare openai gemini
- create gemini summary
language: ja
og_description: Aspose.Words AI を使用して Word 文書を要約します。OpenAI の要約生成方法を学び、C# で OpenAI
  と Gemini の結果を比較します。
og_title: AIでWord文書を要約 – OpenAI vs Gemini
tags:
- Aspose.Words
- C#
- AI‑summarization
title: AIでWord文書を要約 – OpenAI vs Gemini
url: /ja/net/ai-powered-document-processing/summarize-word-document-with-ai-openai-vs-gemini/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# AIでWord文書を要約する – 完全なC#ガイド  

Word文書を**自動で要約**したいけど、どのAIモデルを信頼すればいいか分からないことはありませんか？ 多くのプロジェクト—法務ブリーフ、研究論文、週次レポートなど—で、Wordファイルの簡潔なAI要約を得られれば、手作業で読む時間を何時間も節約できます。  

このチュートリアルでは、**実行可能な完全なサンプル**を通して、Aspose.Wordsで*.docx*を読み込み、**OpenAIの要約**を生成し、続いて**Geminiの要約**を作成し、最後に**OpenAIとGeminiの結果を横並びで比較**する方法を解説します。最後まで読めば、C#で**OpenAI要約を生成**し、**Gemini要約を作成**する手順が正確に分かり、一般的な落とし穴を回避する実用的なヒントも得られます。  

## 必要なもの  

- **Aspose.Words for .NET**（v24.10以降）— Wordファイルを理解できるライブラリ。  
- **OpenAI APIキー** と **Google AI Studioキー** — 小さなドキュメントであれば無料プランで十分です。  
- .NET 6 SDK（またはそれ以降）とお好みのIDE（Visual Studio、VS Code、Rider など）。  

`Aspose.Words` と同梱のAIモデルラッパー以外に追加のNuGetパッケージは不要です。  

## 手順 1: プロジェクトのセットアップと名前空間のインポート  

まずコンソールアプリを作成し、必要な `using` ディレクティブを追加します。以下のコードブロックは **完全なプログラム骨格** です。`Program.cs` にそのまま貼り付けてください。

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.AI;          // Provides OpenAiModel and GoogleModel extensions

namespace WordSummarizer
{
    class Program
    {
        static void Main(string[] args)
        {
            // We'll fill in the steps later.
        }
    }
}
```

*ポイント*: `Aspose.Words.AI` をインポートすると、内部でOpenAIとGeminiに通信する `Summarize` 拡張メソッドが利用可能になります。これが無いと自前でHTTP呼び出しを実装しなければならず、かなりのボイラープレートが必要です。

## 手順 2: ソースドキュメントの読み込み  

**要約対象のWord文書**は、メモリ上にロードされて初めて処理を開始できます。Aspose.Words は *.docx*、*.doc*、*.rtf* など多数の形式をサポートしているので、変換を気にする必要はありません。

```csharp
// Inside Main()
string inputPath = @"YOUR_DIRECTORY\input.docx";

if (!System.IO.File.Exists(inputPath))
{
    Console.WriteLine($"❌ File not found: {inputPath}");
    return;
}

// Load the document – this is where the magic begins.
Document document = new Document(inputPath);
Console.WriteLine("✅ Document loaded successfully.");
```

**プロのコツ**: 大容量ファイルを扱う場合は、`LoadOptions` を使ってメモリ使用量を抑えることを検討してください。  

## 手順 3: OpenAI 要約の生成  

ここでは OpenAI の **gpt‑4o‑mini** モデルにコンテンツの要約を依頼します。`OpenAiModel` クラスはモデル名を受け取り、環境変数 `OPENAI_API_KEY` を自動的に取得します。

```csharp
// Inside Main()
string openAiSummary = document.Summarize(
    new OpenAiModel("gpt-4o-mini")   // <-- generate openai summary
);

Console.WriteLine("\n--- OpenAI Summary ---");
Console.WriteLine(openAiSummary);
```

### なぜ OpenAI を要約に使うのか？

- **速度** – gpt‑4o‑mini は典型的な5ページ文書で1秒未満に結果を返します。  
- **品質** – 多くのルールベース手法よりも微妙なニュアンスを捉えることができます。  

APIキーが設定されていない場合、ライブラリは分かりやすい例外をスローし、コンソールに有益なエラーメッセージが表示されるのでデバッグが容易です。

## 手順 4: Gemini 要約の生成  

Google の **Gemini‑1.5‑pro** モデルは、より短く箇条書きスタイルの出力を生成することが多いです。切り替えはたった1行です。

```csharp
// Inside Main()
string geminiSummary = document.Summarize(
    new GoogleModel("gemini-1.5-pro")   // <-- create gemini summary
);

Console.WriteLine("\n--- Gemini Summary ---");
Console.WriteLine(geminiSummary);
```

### Gemini が適しているケースは？

- スライド資料用に**簡潔な箇条書き**が必要なとき。  
- 組織がコンプライアンス上、Google Cloud を好むとき。  

こちらも APIキーは環境変数 `GOOGLE_API_KEY` から取得され、ソースコードに認証情報が残りません。

## 手順 5: OpenAI と Gemini の出力を比較  

2つの要約が得られたら、**OpenAI と Gemini を横並びで比較**し、どちらが自分のワークフローに合うか判断します。以下はシンプルな diff 風ビューを出力するヘルパーメソッドです。

```csharp
static void CompareSummaries(string openAi, string gemini)
{
    Console.WriteLine("\n=== Comparison Table ===");
    Console.WriteLine("{0,-30} | {1}", "OpenAI Summary", "Gemini Summary");
    Console.WriteLine(new string('-', 70));

    // Split by lines for a rough line‑by‑line view.
    var openLines = openAi.Split('\n');
    var gemLines = gemini.Split('\n');
    int max = Math.Max(openLines.Length, gemLines.Length);

    for (int i = 0; i < max; i++)
    {
        string o = i < openLines.Length ? openLines[i] : "";
        string g = i < gemLines.Length ? gemLines[i] : "";
        Console.WriteLine("{0,-30} | {1}", o.Trim(), g.Trim());
    }
}
```

両要約を生成した直後に呼び出します:

```csharp
// Inside Main()
CompareSummaries(openAiSummary, geminiSummary);
```

テーブル形式で瞬時に視覚的比較が可能です。OpenAI のナラティブスタイルが有用か、Gemini の簡潔な箇条書きが適切かをすぐに判断できます。  

## 手順 6: 完全版 – 動作するサンプルコード  

すべてをまとめた **完全プログラム** を以下に示します（プレースホルダーのパスを差し替え、環境変数を設定すればすぐに実行可能です）。

```csharp
// Program.cs – Full runnable example
using System;
using Aspose.Words;
using Aspose.Words.AI;

namespace WordSummarizer
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the document
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            if (!System.IO.File.Exists(inputPath))
            {
                Console.WriteLine($"❌ File not found: {inputPath}");
                return;
            }
            Document document = new Document(inputPath);
            Console.WriteLine("✅ Document loaded successfully.");

            // 2️⃣ Generate OpenAI summary
            string openAiSummary = document.Summarize(
                new OpenAiModel("gpt-4o-mini")   // generate openai summary
            );
            Console.WriteLine("\n--- OpenAI Summary ---");
            Console.WriteLine(openAiSummary);

            // 3️⃣ Generate Gemini summary
            string geminiSummary = document.Summarize(
                new GoogleModel("gemini-1.5-pro")   // create gemini summary
            );
            Console.WriteLine("\n--- Gemini Summary ---");
            Console.WriteLine(geminiSummary);

            // 4️⃣ Compare the two
            CompareSummaries(openAiSummary, geminiSummary);
        }

        // Helper to display a side‑by‑side comparison
        static void CompareSummaries(string openAi, string gemini)
        {
            Console.WriteLine("\n=== Comparison Table ===");
            Console.WriteLine("{0,-30} | {1}", "OpenAI Summary", "Gemini Summary");
            Console.WriteLine(new string('-', 70));

            var openLines = openAi.Split('\n');
            var gemLines = gemini.Split('\n');
            int max = Math.Max(openLines.Length, gemLines.Length);

            for (int i = 0; i < max; i++)
            {
                string o = i < openLines.Length ? openLines[i] : "";
                string g = i < gemLines.Length ? gemLines[i] : "";
                Console.WriteLine("{0,-30} | {1}", o.Trim(), g.Trim());
            }
        }
    }
}
```

### 期待される出力  

```
✅ Document loaded successfully.

--- OpenAI Summary ---
[Longer, narrative paragraph summarizing the input.docx content]

--- Gemini Summary ---
• Bullet point 1
• Bullet point 2
• Bullet point 3

=== Comparison Table ===
OpenAI Summary                 | Gemini Summary
----------------------------------------------------------------------
[First sentence from OpenAI]   | • Bullet point 1
[Second sentence]              | • Bullet point 2
...                            | • Bullet point 3
```

右側に箇条書き、左側に段落が表示されれば正常に動作しています。  

## よくある落とし穴と回避策  

| 問題 | 発生理由 | 対策 |
|------|----------|------|
| **APIキーが見つからない** | 環境変数が未設定またはタイプミス | Windows なら `setx OPENAI_API_KEY "sk-..."`、Bash なら `export OPENAI_API_KEY=...` を実行 |
| **ドキュメントが大きすぎる** | Aspose がファイル全体をメモリにロードするため | `LoadOptions` に `LoadFormat.Docx` と `LoadFormat.MemoryOptimized` を指定して読み込み |
| **レートリミットエラー** | 無料プランの呼び出し回数上限に達した | 指数バックオフ付きのリトライロジック（例: `Thread.Sleep`）を追加 |
| **文字化け** | .docx 内の非UTF‑8文字 | ソースファイルをUnicodeで保存。Aspose はほとんどの場合自動で正しく処理します |

## チュートリアルの拡張例  

- **バッチ処理** – フォルダ内の *.docx* をループで走査し、各要約を *.txt* に書き出す。  
- **カスタムプロンプト** – 特定のトーンが必要な場合は `Prompt` オブジェクトを `Summarize` に渡す（例: “3つの箇条書きで要約してください”）。  
- **ハイブリッド要約** – OpenAI の段落と Gemini の箇条書きを結合し、“ベスト・オブ・両方”レポートを作成する。  

## 結論  

これで **OpenAI と Gemini の両方を使ってWord文書を要約** し、**結果を比較** できる **即実行可能なC#ソリューション** が手に入りました。ドキュメントレビューのパイプライン構築、社内ナレッジベースの整備、あるいは単なる実験に至るまで、さまざまなシーンで活用してください。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}