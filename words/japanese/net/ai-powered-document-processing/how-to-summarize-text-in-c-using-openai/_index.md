---
category: general
date: 2026-09-11
description: APIキーを読み取り、OpenAIを呼び出し、Word文書の簡潔な要約を生成することで、C#でテキストを要約する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to summarize text
- summarize word document
- read api key
- how to create summary
- how to call openai
language: ja
lastmod: 2026-09-11
og_description: C#でテキストを要約するには？このチュートリアルでは、APIキーの取得方法、OpenAIの呼び出し方、そしてWord文書の要約作成方法を解説します。
og_image_alt: Diagram showing C# code flow that reads an API key, calls OpenAI, and
  outputs a document summary
og_title: OpenAI を使って C# でテキストを要約する方法 – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to summarize text in C# by reading the API key, calling OpenAI,
    and generating a concise summary of a Word document.
  headline: How to summarize text in C# using OpenAI
  type: TechArticle
- description: Learn how to summarize text in C# by reading the API key, calling OpenAI,
    and generating a concise summary of a Word document.
  name: How to summarize text in C# using OpenAI
  steps:
  - name: '**Cache the API key** – reading from the environment each call adds negligible
      overhead, but you can store it in a static readonly field if you call the summarizer
      many times in one process.'
    text: '**Cache the API key** – reading from the environment each call adds negligible
      overhead, but you can store it in a static readonly field if you call the summarizer
      many times in one process.'
  - name: '**Rate‑limit requests** – OpenAI enforces request limits; implement exponential
      back‑off if you hit `429 Too Many Requests`.'
    text: '**Rate‑limit requests** – OpenAI enforces request limits; implement exponential
      back‑off if you hit `429 Too Many Requests`.'
  - name: '**Sanitize input** – remove personally identifiable information before
      sending text to an external AI service.'
    text: '**Sanitize input** – remove personally identifiable information before
      sending text to an external AI service.'
  - name: '**Unit test the extraction logic** – mock `WordprocessingDocument` to verify
      `ExtractTextFromDocx` works with different document structures.'
    text: '**Unit test the extraction logic** – mock `WordprocessingDocument` to verify
      `ExtractTextFromDocx` works with different document structures.'
  type: HowTo
tags:
- C#
- OpenAI
- Document processing
- AI summarization
title: OpenAI を使用して C# でテキストを要約する方法
url: /ja/net/ai-powered-document-processing/how-to-summarize-text-in-c-using-openai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で OpenAI を使用してテキストを要約する方法

If you need to **how to summarize text** in a .docx file, this guide shows you a complete, ready‑to‑run solution. You’ll learn how to read the API key from your environment, how to call OpenAI (or Google) from C#, and how to create a concise summary of a Word document.

`.docx` ファイルで **how to summarize text** を行う必要がある場合、このガイドでは完全で実行可能なソリューションを示します。環境変数から API キーを読み取る方法、C# から OpenAI（または Google）を呼び出す方法、Word ドキュメントの簡潔な要約を作成する方法を学びます。

Summarizing a Word document is a common requirement for report generation, email digests, or knowledge‑base extraction. By the end of this tutorial you will have a command‑line program that prints a five‑sentence summary of any `.docx` file you provide.

Word ドキュメントの要約は、レポート作成、メール要約、ナレッジベース抽出などで一般的な要件です。このチュートリアルの最後までに、提供した任意の `.docx` ファイルの 5 文の要約を出力するコマンドラインプログラムが作成できます。

## 前提条件

- .NET 6.0 SDK またはそれ以降（[dotnet.microsoft.com](https://dotnet.microsoft.com/download) からダウンロード）
- `OPENAI_API_KEY` という名前の環境変数に保存された有効な OpenAI API キー（**read api key** が実行されるのが確認できます）
- `.docx` ファイルを読み取るための `DocumentFormat.OpenXml` NuGet パッケージ
- `OpenAI` NuGet パッケージ（Google プロバイダーを使用したい場合は `Google.AI`）

## Step 1: プロジェクトのセットアップと依存関係のインストール

Create a new console project and add the required packages:

```bash
dotnet new console -n SummarizerDemo
cd SummarizerDemo
dotnet add package DocumentFormat.OpenXml
dotnet add package OpenAI
# Optional: dotnet add package Google.AI
```

> **Pro tip:** 後で依存関係を追加する場合は、関連パッケージを `<ItemGroup>` 内にまとめて `csproj` を整理してください。

## Step 2: API キーを安全に読み取る

Hard‑coding secrets is unsafe. The tutorial demonstrates the proper way to **read api key** from environment variables.

シークレットをハードコーディングするのは安全ではありません。このチュートリアルでは環境変数から **read api key** を取得する正しい方法を示します。

```csharp
using System;

/// <summary>
/// Retrieves the OpenAI API key from the environment.
/// Throws an exception if the variable is missing.
/// </summary>
static string GetOpenAIApiKey()
{
    var key = Environment.GetEnvironmentVariable("OPENAI_API_KEY");
    if (string.IsNullOrWhiteSpace(key))
    {
        throw new InvalidOperationException(
            "OPENAI_API_KEY environment variable not set. " +
            "Set it before running the program.");
    }
    return key;
}
```

## Step 3: 要約したい Word ドキュメントを読み込む

The code below shows **how to summarize word document** content by extracting plain text from the OpenXML structure.

以下のコードは OpenXML 構造からプレーンテキストを抽出し、**how to summarize word document** コンテンツを要約する方法を示しています。

```csharp
using DocumentFormat.OpenXml.Packaging;
using DocumentFormat.OpenXml.Wordprocessing;

/// <summary>
/// Extracts raw text from a .docx file.
/// </summary>
static string ExtractTextFromDocx(string path)
{
    using var wordDoc = WordprocessingDocument.Open(path, false);
    var body = wordDoc.MainDocumentPart.Document.Body;
    return body.InnerText;
}
```

## Step 4: 再利用可能なサマライザークラスを作成する

This class encapsulates **how to call openai** (or Google) and implements **how to create summary** logic. It also lets you switch providers with a single enum value.

このクラスは **how to call openai**（または Google）をカプセル化し、**how to create summary** ロジックを実装します。また、単一の enum 値でプロバイダーを切り替えることができます。

```csharp
using System.Threading.Tasks;
using OpenAI;
using OpenAI.Chat;

/// <summary>
/// Supported AI providers for summarization.
/// </summary>
enum SummarizerProvider { OpenAI, Google }

/// <summary>
/// Provides a method to summarize a document using the selected provider.
/// </summary>
static class DocumentSummarizer
{
    public static async Task<string> SummarizeAsync(
        string text,
        SummarizerProvider provider,
        int maxSentences = 5)
    {
        return provider switch
        {
            SummarizerProvider.OpenAI => await SummarizeWithOpenAIAsync(text, maxSentences),
            SummarizerProvider.Google => await SummarizeWithGoogleAsync(text, maxSentences),
            _ => throw new NotSupportedException($"Provider {provider} is not supported.")
        };
    }

    // ---------- OpenAI implementation ----------
    private static async Task<string> SummarizeWithOpenAIAsync(string text, int maxSentences)
    {
        var apiKey = GetOpenAIApiKey(); // re‑use the method from Step 2
        var client = new OpenAIClient(new OpenAIAuthentication(apiKey));

        var prompt = $"Summarize the following text in no more than {maxSentences} sentences:\n\n{text}";
        var chatRequest = new ChatRequest(new[] { new ChatMessage(ChatMessageRole.System, prompt) });

        var response = await client.ChatEndpoint.GetCompletionAsync(chatRequest);
        return response.FirstChoice.Message.Content.Trim();
    }

    // ---------- Google implementation (optional) ----------
    private static async Task<string> SummarizeWithGoogleAsync(string text, int maxSentences)
    {
        // Placeholder for Google AI call.
        // Replace with actual Google client code if you have the package.
        await Task.Yield();
        return "Google summarization not implemented in this demo.";
    }
}
```

### この構造が重要な理由

- **Separation of concerns:** ドキュメントの読み込み、API キーの取得、AI サービスの呼び出しがそれぞれ独立したメソッドに分離されています。これによりコードのテストや拡張が容易になります。
- **Provider flexibility:** enum を使用することで、呼び出しコードを変更せずに OpenAI と Google を切り替えられ、**how to call openai** と **how to create summary** に再利用可能に直接対応します。
- **Error handling:** API キーが見つからない場合は明確な例外がスローされ、サイレント失敗を防ぎます。

## Step 5: `Program.cs` にすべてを統合する

```csharp
using System;
using System.Threading.Tasks;

class Program
{
    static async Task Main(string[] args)
    {
        if (args.Length != 1)
        {
            Console.WriteLine("Usage: SummarizerDemo <path-to-docx>");
            return;
        }

        string docPath = args[0];

        // 1️⃣ Load the source document
        string rawText = ExtractTextFromDocx(docPath);

        // 2️⃣ Summarize the document using OpenAI (you can switch to Google)
        string summary = await DocumentSummarizer.SummarizeAsync(
            rawText,
            SummarizerProvider.OpenAI, // change to SummarizerProvider.Google if needed
            maxSentences: 5);

        // 3️⃣ Output the generated summary
        Console.WriteLine("Summary:");
        Console.WriteLine(summary);
    }

    // Include the helper methods from Steps 2‑4 here
    // (GetOpenAIApiKey, ExtractTextFromDocx, DocumentSummarizer, etc.)
}
```

### 期待される出力

Running the program with a sample document:

```bash
dotnet run -- "sample/input.docx"
```

might produce:

```
Summary:
The report outlines quarterly sales growth, highlighting a 12% increase in the North American market. 
Key challenges include supply‑chain delays and rising material costs. 
Customer feedback indicates higher satisfaction with the new product line. 
Recommendations focus on expanding the digital sales channel and optimizing inventory levels. 
Overall, the company is positioned for continued growth in the next fiscal year.
```

## Step 6: 一般的なバリエーションとエッジケース

| 状況 | 推奨される調整 |
|-----------|------------------------|
| **大きなドキュメント** ( > 10 KB ) | テキストをチャンクに分割し、各チャンクを要約してから結果を結合します。 |
| **非英語コンテンツ** | プロンプトに言語ヒントを渡す、例: “Summarize the following French text …”。 |
| **Google プロバイダー** | `SummarizeWithOpenAIAsync` 呼び出しを適切な Google API クライアントに置き換え、同じ enum インターフェースを保持します。 |
| **カスタム要約長** | `SummarizeAsync` を呼び出す際の `maxSentences` 引数を変更します。 |
| **API キーが欠如** | `GetOpenAIApiKey` メソッドはすでに明確な例外をスローします。よりフレンドリーなメッセージが必要な場合は `Main` で捕捉してください。 |

## 本番環境でのプロのヒント

1. **Cache the API key** – 各呼び出しで環境から読み取るオーバーヘッドは無視できる程度ですが、同一プロセスでサマライザーを多数呼び出す場合は static readonly フィールドに保存できます。
2. **Rate‑limit requests** – OpenAI はリクエスト制限を課しています。`429 Too Many Requests` が返された場合は指数バックオフを実装してください。
3. **Sanitize input** – テキストを外部 AI サービスに送信する前に、個人を特定できる情報を除去してください。
4. **Unit test the extraction logic** – `WordprocessingDocument` をモックして、`ExtractTextFromDocx` がさまざまなドキュメント構造で機能することを検証します。

## 結論

これで、API キーを安全に読み取り、OpenAI を呼び出し、Word ドキュメントの簡潔な要約を生成することで、C# で **how to summarize text** ができるようになりました。同じパターンを使えば、他のプロバイダーでも **how to call openai** が可能になり、さまざまなコンテンツタイプ向けに **how to create summary** ロジックを実装し、環境から **read api key** 値を安全に取得できます。より長いドキュメントや別のプロバイダー、カスタムプロンプトで実験し、特定のドメインに合わせた要約を調整してください。

---

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [C# と Aspose.Words API を使用した Word ドキュメントの要約 – 完全 AI 駆動ガイド](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-complete-ai-powered-guide/)
- [Word から PDF を作成する方法 – 完全 C# ガイド](/words/english/net/basic-conversions/how-to-create-pdf-from-word-complete-c-guide/)
- [Word ドキュメント - コンテンツの削除方法](/words/english/net/remove-content/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}