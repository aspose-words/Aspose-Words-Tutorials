---
category: general
date: 2026-07-16
description: C#でAIを使ってテキストを要約する。Wordから要約を生成し、C#でWord文書を読み込む方法を数ステップで学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- summarize text with ai
- generate summary from word
- load word document c#
- ai summarizer c#
- word document processing c#
- text summarization api
language: ja
lastmod: 2026-07-16
og_description: C#でAIを使ってテキストを要約しましょう。このガイドに従ってWordファイルから要約を生成し、C#でWord文書を素早く読み込む方法を学びましょう。
og_image_alt: Screenshot of C# code that loads a Word document and produces an AI‑generated
  summary
og_title: C#でAIを使ってテキストを要約する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Summarize text with AI using C#. Learn how to generate summary from
    Word and load Word document C# in just a few steps.
  headline: Summarize Text with AI in C# – Complete Programming Guide
  type: TechArticle
tags:
- C#
- AI
- Word
title: C#でAIを使ってテキストを要約する – 完全プログラミングガイド
url: /ja/net/ai-powered-document-processing/summarize-text-with-ai-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で AI によるテキスト要約 – 完全プログラミングガイド

IDE を離れずに **summarize text with AI** したいと思ったことはありませんか？たとえば *.docx* のレポートが山ほどあって、すぐにエグゼクティブ向けの要約が必要なときです。良いニュースは、C# だけで完結できることです。Word 文書を読み込み、AI 要約器を呼び出し、きれいな 5 文の概要を出力できます。

このチュートリアルでは、実際の例を通して **generate summary from Word** ファイルと **load Word document C#** のコードを紹介します。OpenAI と Google の両モデルに対応しています。最後には、任意の .NET プロジェクトに組み込める自己完結型コンソールアプリが手に入ります。

> **学べること**  
> • *.docx* ファイルを読み取る完全に実行可能な C# プログラム。  
> • AI サービスと通信する再利用可能な `Summarize` メソッド。  
> • ファイルが見つからない場合やモデル選択、トークン上限の扱い方に関するヒント。

---

## 前提条件 — 開始前に必要なもの

| 必要条件 | 理由 |
|-------------|----------------|
| .NET 6 以降 | 最新の言語機能と `async` サポートが利用可能。 |
| NuGet パッケージ: `Aspose.Words`（または `DocumentFormat.OpenXml`）、`System.Net.Http.Json` | `Aspose.Words` はコード例で使用する `Document` クラスを提供し、`HttpClient` が API 呼び出しを処理します。 |
| OpenAI または Google Vertex AI の API キー | 要約にはモデルエンドポイントが必要です。キーをコードに埋め込みます。 |
| フォルダー内にサンプル Word ファイル（`report.docx`） | チュートリアルでは `load word document c#` を使ってファイル I/O を実演します。 |

これらが揃っていない場合は、今すぐインストールしてください。手順はシンプルです。

---

## Step 1 – C# で Word 文書を読み込む  

最初に行うべきことは **load Word document C#** スタイルで文書を読み込むことです。Aspose.Words を使えば、ディスク上のファイルを指す `Document` インスタンスを作成するだけです。

```csharp
using Aspose.Words;
using System;
using System.IO;

// Ensure the file exists before we try to open it.
string filePath = Path.Combine(Environment.CurrentDirectory, "report.docx");
if (!File.Exists(filePath))
{
    Console.Error.WriteLine($"❌ File not found: {filePath}");
    return;
}

// Step 1: Load the source document
Document doc = new Document(filePath);
Console.WriteLine("✅ Document loaded successfully.");
```

**なぜ重要か:**  
* `Document` オブジェクトは *.docx* の XML を抽象化し、後でプレーンテキストとして扱えるようにします。  
* ファイルの存在チェックを行うことで、**load word document c#** 時に頻発する `FileNotFoundException` を防げます。

---

## Step 2 – 要約用にプレーンテキストを抽出  

AI モデルは Word の内部マークアップを理解できません。クリーンなテキストが必要です。Aspose は `Document.GetText()` を提供しており、文書全体を文字列として取得できます。

```csharp
// Extract raw text – this strips out tables, images, and formatting.
string rawText = doc.GetText();
if (string.IsNullOrWhiteSpace(rawText))
{
    Console.Error.WriteLine("⚠️ Document appears empty after extraction.");
    return;
}
Console.WriteLine($"📝 Extracted {rawText.Length:N0} characters of text.");
```

**Pro tip:** 見出しを保持したい場合は、`doc.GetChildNodes(NodeType.Paragraph, true)` を走査し、スタイルが “Heading” の段落だけを連結すると、要約が文書構造を尊重します。

---

## Step 3 – 要約オプションを定義  

ここからが本題、**summarize text with AI** です。モデル、最大文数、temperature などを調整できる小さな POCO にオプションをまとめます。

```csharp
public enum SummarizationModel
{
    OpenAI,
    Google
}

public class SummarizationOptions
{
    public int MaxSentences { get; set; } = 5;
    public SummarizationModel Model { get; set; } = SummarizationModel.OpenAI;
    public double Temperature { get; set; } = 0.7; // Controls creativity
}
```

これで AI に対して「何をしてほしいか」を明示できるオプションインスタンスを作成できます。

```csharp
// Step 2: Define summarization options (e.g., limit to 5 sentences, choose a model)
SummarizationOptions options = new SummarizationOptions
{
    MaxSentences = 5,
    Model = SummarizationModel.OpenAI   // switch to Google if you prefer
};
```

**設定を公開する理由:**  
* プロジェクトごとに要約の長さは異なります。2 文の TL;DR が必要なものもあれば、5 文のエグゼクティブブリーフが必要なものもあります。  
* `OpenAI` と `Google` のモデル切替は enum の値を一つ変えるだけで完了するため、A/B テストに最適です。

---

## Step 4 – `Summarize` メソッドを実装  

以下は **完全に実行可能** な実装例です。OpenAI の `chat/completions` エンドポイントまたは Google Vertex AI の `text-bison` モデルのどちらかにリクエストを送ります。`System.Net.Http.Json` を使ってコードを簡潔にしています。

```csharp
using System.Net.Http;
using System.Net.Http.Json;
using System.Threading.Tasks;

public static class AiSummarizer
{
    private static readonly HttpClient http = new HttpClient();

    public static async Task<string> SummarizeAsync(string text, SummarizationOptions opts)
    {
        // Choose endpoint and payload based on the selected model.
        if (opts.Model == SummarizationModel.OpenAI)
        {
            // OpenAI expects a messages array; we use a system prompt to enforce sentence limit.
            var request = new
            {
                model = "gpt-4o-mini",
                temperature = opts.Temperature,
                messages = new[]
                {
                    new { role = "system", content = $"Summarize the following text in no more than {opts.MaxSentences} sentences." },
                    new { role = "user", content = text }
                },
                max_tokens = 500
            };

            http.DefaultRequestHeaders.Authorization =
                new System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", Environment.GetEnvironmentVariable("OPENAI_API_KEY"));

            var response = await http.PostAsJsonAsync("https://api.openai.com/v1/chat/completions", request);
            response.EnsureSuccessStatusCode();

            var json = await response.Content.ReadFromJsonAsync<dynamic>();
            return (string)json.choices[0].message.content;
        }
        else // Google Vertex AI
        {
            var request = new
            {
                instances = new[] { new { content = text } },
                parameters = new
                {
                    temperature = opts.Temperature,
                    maxOutputTokens = 500,
                    topK = 40,
                    topP = 0.95,
                    // Vertex AI doesn’t have a built‑in sentence limit, so we post‑process later.
                }
            };

            http.DefaultRequestHeaders.Authorization =
                new System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", Environment.GetEnvironmentVariable("GOOGLE_API_KEY"));

            var response = await http.PostAsJsonAsync(
                "https://us-central1-aiplatform.googleapis.com/v1/projects/YOUR_PROJECT/locations/us-central1/publishers/google/models/text-bison-001:predict",
                request);
            response.EnsureSuccessStatusCode();

            var json = await response.Content.ReadFromJsonAsync<dynamic>();
            string raw = (string)json.predictions[0].content;
            // Simple post‑processing: keep only the first N sentences.
            return string.Join(' ', raw.Split('.').Take(opts.MaxSentences)).Trim() + ".";
        }
    }
}
```

**「なぜ」の説明**  
* **モデル非依存設計** – 同一メソッドで OpenAI と Google の両方を扱えるため、コードベースがすっきりします。  
* **キーは環境変数から取得** – API シークレットをハードコーディングするのはセキュリティリスクです。`Environment.GetEnvironmentVariable` を使うのがベストプラクティスです。  
* **文数制限の実装** – OpenAI はシステムプロンプトで直接指示できますが、Google は API が文数上限をサポートしていないため、取得後に簡易的に処理します。  

---

## Step 5 – 全体を結びつけて要約を出力  

ここまでの部品を組み合わせます。文書を読み込み、テキストを `SummarizeAsync` に渡し、結果をコンソールに表示します。

```csharp
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        // Load the document (Step 1)
        string filePath = Path.Combine(Environment.CurrentDirectory, "report.docx");
        if (!File.Exists(filePath))
        {
            Console.Error.WriteLine($"❌ Cannot find {filePath}");
            return;
        }
        Document doc = new Document(filePath);

        // Extract raw text (Step 2)
        string rawText = doc.GetText();

        // Define options (Step 3)
        SummarizationOptions options = new SummarizationOptions
        {
            MaxSentences = 5,
            Model = SummarizationModel.OpenAI   // Change to Google if you prefer
        };

        // Generate the summary (Step 4)
        string summary = await AiSummarizer.SummarizeAsync(rawText, options);

        // Step 5: Output the generated summary
        Console.WriteLine("\n=== AI‑Generated Summary ===\n");
        Console.WriteLine(summary);
    }
}
```

### 期待される出力

`report.docx` が 2 ページのビジネス分析レポートであると仮定すると、コンソールには次のように表示される可能性があります：

```
=== AI‑Generated Summary ===

The quarterly sales increased by 12% YoY, driven primarily by the new product line. Customer churn fell to 3%, the lowest in five years. Marketing spend rose 8% but delivered a 15% lift in brand awareness. Operational efficiencies saved $1.2M, mainly through supply‑chain automation. The outlook for Q3 remains positive, with projected growth of 10‑15%.
```

`options.Model` を `SummarizationModel.Google` に切り替えると、同様に簡潔な段落が出力されますが、表現スタイルが異なります。

---

## エッジケースとよくある落とし穴の対処  

| 状況 | 注意点 | 簡単な対策 |
|-----------|-------------------|-----------|
| **巨大文書 (>10 k トークン)** | API がリクエストを拒否したり、出力が切り捨てられる可能性があります。 | テキストを論理的なセクション（例: 見出しごと）に分割し、各チャンクを要約してから結合します。 |
| **API キーが未設定または無効** | 401 Unauthorized エラーが返ります。 | 環境変数 `OPENAI_API_KEY` / `GOOGLE_API_KEY` が設定されているか確認するか、ローカル開発時は `appsettings.json` に記載します。 |
| **非英語の Word ファイル** | Summar |

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示した手法を応用した関連トピックを扱っています。各リソースには、ステップバイステップの解説と完全なコード例が含まれており、API の追加機能習得や別実装アプローチの探索に役立ちます。

- [Word Document - Find And Replace Text](/words/english/net/find-and-replace-text/)
- [Ranges Get Text In Word Document](/words/english/net/programming-with-ranges/ranges-get-text/)
- [Copy Bookmarked Text In Word Document](/words/english/net/programming-with-bookmarks/copy-bookmarked-text/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}