---
category: general
date: 2026-09-21
description: OpenAIまたはGoogleのAPIを使用して、Wordファイルから要約を作成するC#のAI文書要約ツールの作り方を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- ai document summarizer
- ai powered summarization
- create summary from word
- summarize docx with ai
- summarize using google
language: ja
lastmod: 2026-09-21
og_description: C# の AI ドキュメント要約ツールは、Word ファイルから迅速に要約を作成できます。このガイドに従って、OpenAI または
  Google を使用した AI 駆動の要約を行いましょう。
og_image_alt: Diagram showing the workflow of an ai document summarizer processing
  a Word file
og_title: C#でAI文書要約ツールを作る – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to build an ai document summarizer in C# that creates summary
    from Word files using OpenAI or Google APIs.
  headline: How to use an ai document summarizer in C#
  type: TechArticle
- description: Learn how to build an ai document summarizer in C# that creates summary
    from Word files using OpenAI or Google APIs.
  name: How to use an ai document summarizer in C#
  steps:
  - name: Provider implementation details
    text: '```csharp static class DocumentSummarizer { public static string Summarize(string
      text, SummarizerProvider provider, int maxSentences = 5) { return provider switch
      { SummarizerProvider.OpenAI => SummarizeWithOpenAI(text, maxSentences), SummarizerProvider.Google
      => SummarizeWithGoogle(text, maxSenten'
  - name: Handling token limits and large documents
    text: If the source document exceeds the model’s token quota, split it into paragraphs
      and summarize each chunk separately, then combine the chunk summaries. This
      ensures you never hit the 8 k‑token limit for most models.
  - name: Expected output
    text: '``` Summary: The report highlights a 12% revenue increase driven by new
      product launches. Customer churn dropped to 3% after the recent support improvements.
      Marketing spend rose by 8% but delivered a 15% ROI. The upcoming quarter will
      focus on expanding into APAC markets. Overall, the company is on'
  type: HowTo
tags:
- AI
- C#
- Document Processing
title: C#でAI文書要約ツールを使用する方法
url: /ja/net/ai-powered-document-processing/how-to-use-an-ai-document-summarizer-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#でAI文書要約ツールを使用する方法

.ai document summarizer が .docx ファイル用に必要な場合、このガイドでは C# を使用して Word から要約を作成する方法を示します。OpenAI または Google のいずれかで動作する完全な実行可能サンプルが確認でき、数分で **ai powered summarization** ソリューションが手に入ります。

このチュートリアルでは、プロジェクトのセットアップからエッジケースの処理まで全てをカバーしているので、独自のアプリケーションで自信を持って **summarize docx with ai** ができます。外部スクリプトは不要で、NuGet パッケージを数個と短いコードスニペットだけで完了します。

## 必要なもの

- .NET 6.0 以降（コードは .NET Core 3.1+ でも動作します）
- OpenAI API キー **または** Google Cloud Vertex AI キー
- Word ファイルを読み込むための `DocX` NuGet パッケージ
- 選択したプロバイダー用の `OpenAI` または `Google.Cloud.AIPlatform.V1` NuGet パッケージ
- Visual Studio 2022 や VS Code などの開発環境

## 手順 1: ai document summarizer 環境のセットアップ

まず、新しいコンソールプロジェクトを作成し、必要なパッケージを追加します。

```bash
dotnet new console -n AiSummarizerDemo
cd AiSummarizerDemo
dotnet add package DocX --version 1.0.0
dotnet add package OpenAI --version 2.5.0   # for OpenAI
dotnet add package Google.Cloud.AIPlatform.V1 --version 2.6.0   # for Google
```

> **プロのコツ:** API キーはハードコーディングせず、環境変数 (`OPENAI_API_KEY`, `GOOGLE_APPLICATION_CREDENTIALS`) に保存してください。

## 手順 2: Word ドキュメントを読み込み **create summary from word** を実行

最初の実装行でソースの `.docx` ファイルを読み込みます。`DocX` を使用してプレーンテキストを抽出し、後で AI モデルが要約します。

```csharp
using System;
using System.IO;
using Xceed.Words.NET;   // DocX namespace

// Load the source document you want to summarize
Document document = Document.Load("input.docx");

// Extract raw text for the summarizer
string rawText = document.Text;
```

> **このステップが重要な理由:** AI モデルはクリーンで直線的なテキストで最も効果的に動作します。書式を除去することでトークン制限の予期せぬ問題を防ぎ、要約の関連性が向上します。

## 手順 3: **ai powered summarization** プロバイダーを選択

`SummarizerProvider` 列挙型を設定することで、OpenAI の GPT‑4 と Google の PaLM モデルを切り替えることができます。この列挙型はプロバイダー固有のロジックを抽象化します。

```csharp
enum SummarizerProvider
{
    OpenAI,
    Google
}

// Choose the provider (replace with your preference)
SummarizerProvider provider = SummarizerProvider.OpenAI; // or SummarizerProvider.Google
```

### プロバイダー実装の詳細

```csharp
static class DocumentSummarizer
{
    public static string Summarize(string text, SummarizerProvider provider, int maxSentences = 5)
    {
        return provider switch
        {
            SummarizerProvider.OpenAI => SummarizeWithOpenAI(text, maxSentences),
            SummarizerProvider.Google => SummarizeWithGoogle(text, maxSentences),
            _ => throw new NotSupportedException("Unsupported summarizer provider.")
        };
    }

    private static string SummarizeWithOpenAI(string text, int maxSentences)
    {
        var apiKey = Environment.GetEnvironmentVariable("OPENAI_API_KEY")
                     ?? throw new InvalidOperationException("OpenAI API key missing.");
        var client = new OpenAIClient(apiKey);
        var request = new ChatRequest
        {
            Model = "gpt-4o-mini",
            Messages =
            {
                new ChatMessage(ChatMessageRole.System,
                    "You are a helpful assistant that creates concise summaries."),
                new ChatMessage(ChatMessageRole.User,
                    $"Summarize the following text in no more than {maxSentences} sentences:\n\n{text}")
            }
        };
        var response = client.ChatEndpoint.GetCompletionAsync(request).Result;
        return response.FirstChoice.Message.Content.Trim();
    }

    private static string SummarizeWithGoogle(string text, int maxSentences)
    {
        var client = new PredictionServiceClientBuilder
        {
            // Google credentials are read from GOOGLE_APPLICATION_CREDENTIALS env var
        }.Build();

        var request = new PredictRequest
        {
            // The model name depends on your Vertex AI deployment
            Endpoint = "projects/YOUR_PROJECT/locations/us-central1/publishers/google/models/text-bison",
            Instances = { new Value { StringValue = $"Summarize in {maxSentences} sentences: {text}" } }
        };

        var response = client.Predict(request);
        return response.Predictions[0].StringValue.Trim();
    }
}
```

> **プロバイダーを抽象化する理由:** このパターンにより、呼び出しコードを変更せずに **summarize using google** または OpenAI を使用して要約でき、テストや後のプロバイダー切替に便利です。

## 手順 4: 簡潔な要約を生成 – **summarize docx with ai**

ヘルパーメソッドを呼び出し、出力を5文に制限します（`maxSentences` で調整可能）。

```csharp
// Generate a concise summary with a maximum of 5 sentences
string summary = DocumentSummarizer.Summarize(rawText, provider, maxSentences: 5);
```

### トークン制限と大規模文書の処理

ソース文書がモデルのトークン上限を超える場合、段落に分割し、各チャンクを個別に要約してからチャンク要約を結合します。これにより、ほとんどのモデルで 8 k トークンの上限に達することはありません。

```csharp
static string SummarizeLargeText(string fullText, SummarizerProvider provider, int maxSentences)
{
    const int chunkSize = 2000; // approximate token count
    var chunks = fullText
        .Split(new[] { "\n\n" }, StringSplitOptions.RemoveEmptyEntries)
        .Select(p => p.Trim())
        .Where(p => p.Length > 0)
        .ToList();

    var partialSummaries = new List<string>();
    var sb = new System.Text.StringBuilder();

    foreach (var paragraph in chunks)
    {
        sb.Append(paragraph);
        if (sb.Length > chunkSize)
        {
            partialSummaries.Add(Summarize(sb.ToString(), provider, maxSentences));
            sb.Clear();
        }
    }

    if (sb.Length > 0)
        partialSummaries.Add(Summarize(sb.ToString(), provider, maxSentences));

    // Final pass to merge chunk summaries
    return Summarize(string.Join(" ", partialSummaries), provider, maxSentences);
}
```

## 手順 5: 結果の要約を表示

最後に、要約をコンソールに出力するか、必要な場所に保存します。

```csharp
// Display the resulting summary
Console.WriteLine("Summary:\n" + summary);
```

### 期待される出力

```
Summary:
The report highlights a 12% revenue increase driven by new product launches. Customer churn dropped to 3% after the recent support improvements. Marketing spend rose by 8% but delivered a 15% ROI. The upcoming quarter will focus on expanding into APAC markets. Overall, the company is on track to exceed its annual targets.
```

正確な表現は AI プロバイダーにより異なりますが、構造（≤ 5 文）は一貫しています。

## 完全な実行可能プログラム

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Xceed.Words.NET;               // DocX
using OpenAI;                       // OpenAI SDK
using OpenAI.Chat;                  // Chat classes
using Google.Cloud.AIPlatform.V1;   // Google Vertex AI SDK
using Google.Protobuf;              // Value type

enum SummarizerProvider { OpenAI, Google }

static class DocumentSummarizer
{
    public static string Summarize(string text, SummarizerProvider provider, int maxSentences = 5)
        => provider switch
        {
            SummarizerProvider.OpenAI => SummarizeWithOpenAI(text, maxSentences),
            SummarizerProvider.Google => SummarizeWithGoogle(text, maxSentences),
            _ => throw new NotSupportedException("Unsupported provider.")
        };

    private static string SummarizeWithOpenAI(string text, int maxSentences)
    {
        var apiKey = Environment.GetEnvironmentVariable("OPENAI_API_KEY")
                     ?? throw new InvalidOperationException("OpenAI API key missing.");
        var client = new OpenAIClient(apiKey);
        var request = new ChatRequest
        {
            Model = "gpt-4o-mini",
            Messages =
            {
                new ChatMessage(ChatMessageRole.System,
                    "You are a helpful assistant that creates concise summaries."),
                new ChatMessage(ChatMessageRole.User,
                    $"Summarize the following text in no more than {maxSentences} sentences:\n\n{text}")
            }
        };
        var response = client.ChatEndpoint.GetCompletionAsync(request).Result;
        return response.FirstChoice.Message.Content.Trim();
    }

    private static string SummarizeWithGoogle(string text, int maxSentences)
    {
        var client = new PredictionServiceClientBuilder().Build();
        var request = new PredictRequest
        {
            Endpoint = "projects/YOUR_PROJECT/locations/us-central1/publishers/google/models/text-bison",
            Instances = { new Value { StringValue = $"Summarize in {maxSentences} sentences: {text}" } }
        };
        var response = client.Predict(request);
        return response.Predictions[0].StringValue.Trim();
    }
}

class Program
{
    static void Main()
    {
        // Step 1: Load the source document you want to summarize
        var doc = Document.Load("input.docx");
        string rawText = doc.Text;

        // Step 2: Choose the AI provider for summarization (OpenAI or Google)
        SummarizerProvider provider = SummarizerProvider.OpenAI; // or SummarizerProvider.Google

        // Step 3: Generate a concise summary with a maximum of 5 sentences
        string summary = DocumentSummarizer.Summarize(rawText, provider, maxSentences: 5);

        // Step 4: Display the resulting summary
        Console.WriteLine("Summary:\n" + summary);
    }
}
```

ファイルを `Program.cs` として保存し、` 

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを探求するのに役立ちます。

- [C# と Aspose.Words API で Word 文書を要約 – 完全な AI 搭載ガイド](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-complete-ai-powered-guide/)
- [新しい Word 文書を作成](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Aspose.Words for .NET で Word 文書を作成およびスタイル設定](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}