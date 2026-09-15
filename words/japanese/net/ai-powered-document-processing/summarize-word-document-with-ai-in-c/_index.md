---
category: general
date: 2026-09-14
description: C#でAIを使ってWord文書を要約する – OpenAIやGoogleのプロバイダーで簡潔な要約を生成する方法を学び、数行でAIによるテキスト要約を体験しよう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- summarize word document
- summarize text with ai
- document summarization google
language: ja
lastmod: 2026-09-14
og_description: C#でAIを使用してWord文書を要約する。このチュートリアルでは、OpenAIまたはGoogleの要約プロバイダーを呼び出し、簡潔な結果を得る方法を示します。
og_image_alt: Console window displaying a short AI‑generated summary of a Word document
og_title: AIでWord文書を要約する – クイックC#ガイド
schemas:
- author: GroupDocs
  dateModified: '2026-09-14'
  description: Summarize Word document using AI in C# – learn to generate concise
    summaries with OpenAI or Google providers and see how to summarize text with AI
    in just a few lines.
  headline: Summarize Word document with AI in C#
  type: TechArticle
- description: Summarize Word document using AI in C# – learn to generate concise
    summaries with OpenAI or Google providers and see how to summarize text with AI
    in just a few lines.
  name: Summarize Word document with AI in C#
  steps:
  - name: Load the source `.docx` file.
    text: Load the source `.docx` file.
  - name: Define summarization options (provider and sentence limit).
    text: Define summarization options (provider and sentence limit).
  - name: Call the summarizer to produce a short text.
    text: Call the summarizer to produce a short text.
  - name: Write the result to the console.
    text: Write the result to the console.
  type: HowTo
tags:
- AI summarization
- C#
- Word processing
title: C#でAIを使ってWord文書を要約する
url: /ja/net/ai-powered-document-processing/summarize-word-document-with-ai-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で AI を使用して Word ドキュメントを要約する

Word ドキュメントの内容を自動的に **要約** する必要がある場合、このガイドでは完全で実行可能なソリューションを示します。`.docx` ファイルの読み込み方法、要約リクエストの設定方法、OpenAI または Google のいずれかを AI プロバイダーとして使用して簡潔な要約を取得する方法が分かります。

この例は人気のある `GroupDocs.Summarization` ライブラリで動作しますが、`DocumentSummarizer` API を提供する任意のライブラリにも同様のパターンが適用できます。このチュートリアルの最後までに、数行の C# コードで **AI を使用してテキストを要約** できるようになります。

## 学習できること

- 必要な NuGet パッケージをインストールする。
- Word ドキュメント（`.docx`）をメモリにロードする。
- 要約プロバイダー（OpenAI または Google）を選択し、文の上限を設定する。
- 要約を生成し、コンソールに表示する。
- ファイルが見つからない、またはサポートされていないプロバイダーなどの一般的なエラーを処理する。

> **前提条件:** .NET 6 以降、基本的な C# の知識、そして選択したプロバイダー（OpenAI または Google）の API キー。

## 要約ライブラリのインストール

まず、プロジェクトに `GroupDocs.Summarization` パッケージを追加します：

```bash
dotnet add package GroupDocs.Summarization
```

このパッケージには、後のコードで使用する `Document`、`SummarizerOptions`、`DocumentSummarizer` の各型が含まれています。

## Word ドキュメントの要約 – 概要

コアワークフローは4つのステップで構成されています。

1. ソースの `.docx` ファイルをロードする。
2. 要約オプション（プロバイダーと文の上限）を定義する。
3. 要約器を呼び出して短いテキストを生成する。
4. 結果をコンソールに出力する。

各ステップは以下で詳しく説明します。

## ステップ 1: ソースドキュメントのロード

```csharp
using System;
using GroupDocs.Summarization;
using GroupDocs.Summarization.Options;

class Program
{
    static void Main()
    {
        // Replace with the actual path to your .docx file
        const string inputPath = @"C:\Docs\input.docx";

        // Verify that the file exists before attempting to load it
        if (!System.IO.File.Exists(inputPath))
        {
            Console.Error.WriteLine($"Error: The file \"{inputPath}\" was not found.");
            return;
        }

        // Load the Word document into a Document object
        Document doc = new Document(inputPath);
        Console.WriteLine("Document loaded successfully.");
```

**なぜ重要か:** ファイルを `Document` オブジェクトにロードすることで、基盤となる Word フォーマットが抽象化され、テーブル、画像、脚注に関係なくプレーンテキストとして要約器が処理できるようになります。

## ステップ 2: 要約オプションの定義（プロバイダー選択と文数制限）

```csharp
        // Configure summarization settings
        SummarizerOptions options = new SummarizerOptions
        {
            // Switch between OpenAI and Google providers as needed
            Provider = SummarizerProvider.OpenAI,   // or SummarizerProvider.Google
            MaxSentences = 5                        // Desired number of sentences in the summary
        };

        Console.WriteLine($"Summarization will use {options.Provider} and return up to {options.MaxSentences} sentences.");
```

**なぜ重要か:**  
- **プロバイダー選択** は、テキストを処理する AI サービスを決定します。OpenAI と Google のモデルは同じ入力を受け取りますが、価格、レイテンシ、言語カバレッジが異なります。  
- **`MaxSentences`** は出力の長さを制御でき、完全な要約ではなく簡易プレビューが必要な場合に重要です。

## ステップ 3: 選択した AI プロバイダーを使用して要約を生成する

```csharp
        try
        {
            // The static Summarize method contacts the chosen AI service and returns a concise summary
            string summary = DocumentSummarizer.Summarize(doc, options);
            Console.WriteLine("\nSummary:");
            Console.WriteLine(summary);
        }
        catch (Exception ex)
        {
            // Provide a clear error message for common failure points
            Console.Error.WriteLine($"Summarization failed: {ex.Message}");
        }
    }
}
```

**なぜ重要か:** `Summarize` 呼び出しは、トークン化、モデル推論、ポストプロセッシングといった重い処理をすべて行うため、カスタムプロンプトを書いたり HTTP リクエストを自分で管理したりする必要がありません。`try/catch` ブロックにより、ネットワークエラー、認証問題、またはサポートされていないドキュメント機能が明確に報告されます。

## ステップ 4: 生成された要約をコンソールに出力する

前のステップの `Console.WriteLine` 文ですでに結果は表示されていますが、後で分析できるように要約をファイルに書き出すこともできます：

```csharp
        // Optional: save the summary to a .txt file
        const string outputPath = @"C:\Docs\summary.txt";
        System.IO.File.WriteAllText(outputPath, summary);
        Console.WriteLine($"\nSummary saved to \"{outputPath}\".");
```

**なぜ重要か:** 要約を永続化することで、数十件のドキュメントの要約を生成し、元ファイルと一緒に保存するバッチ処理パイプラインが可能になります。

## OpenAI を使用して AI でテキストを要約する方法

OpenAI の GPT‑4 モデルを使用したい場合は、プロバイダーを明示的に設定します：

```csharp
options.Provider = SummarizerProvider.OpenAI;
```

`OPENAI_API_KEY` 環境変数が定義されていることを確認するか、プログラムでキーを設定してください：

```csharp
SummarizerOptions.ApiKey = "sk-YourOpenAIKey";
```

OpenAI は一般的により流暢な文章を生成し、マーケティングコピーやエグゼクティブ向けブリーフに役立ちます。

## Google を使用したドキュメント要約 – Google プロバイダーの利用

Google Cloud にすでに投資している組織は、Google プロバイダーに切り替えてください：

```csharp
options.Provider = SummarizerProvider.Google;
```

Google の API キーを設定します：

```csharp
SummarizerOptions.ApiKey = "AIzaYourGoogleKey";
```

Google の PaLM モデルは多言語要約に優れており、大量のワークロードに対してコスト効果が高い場合があります。

## エッジケースとベストプラクティスのヒント

| Situation | Recommended handling |
|-----------|----------------------|
| **大きなドキュメント（>10 MB）** | `MaxSentences` を増やすか、ドキュメントをセクションに分割し、各セクションを個別に要約してトークン制限を回避します。 |
| **API キーがない** | ライブラリは `AuthenticationException` をスローします。`Summarize` を呼び出す前にキーを検証してください。 |
| **サポートされていないファイル形式** | `Document` は `.docx`、`.pdf`、プレーンテキストのみをサポートします。他の形式（例: `.doc`）は、まず変換ライブラリを使用して `.docx` に変換してください。 |
| **ネットワーク遅延** | アプリケーションが応答性を保つ必要がある場合は、呼び出しを非同期バージョン（`SummarizeAsync`）でラップしてください。 |

**プロのコツ:** 変更頻度の低いドキュメントの要約はキャッシュしてください。ファイル内容のハッシュを保存し、キャッシュ結果を再利用することで不要な API 呼び出しを防げます。

## 完全な実行可能サンプル

以下は、NuGet パッケージをインストールし API キーを設定した後に、新しいコンソールプロジェクト（`dotnet new console`）にコピー＆ペーストして実行できる完全なプログラムです。

```csharp
using System;
using GroupDocs.Summarization;
using GroupDocs.Summarization.Options;

namespace WordSummarizer
{
    class Program
    {
        static void Main()
        {
            const string inputPath = @"C:\Docs\input.docx";
            const string outputPath = @"C:\Docs\summary.txt";

            if (!System.IO.File.Exists(inputPath))
            {
                Console.Error.WriteLine($"Error: The file \"{inputPath}\" was not found.");
                return;
            }

            Document doc = new Document(inputPath);
            Console.WriteLine("Document loaded successfully.");

            SummarizerOptions options = new SummarizerOptions
            {
                Provider = SummarizerProvider.OpenAI, // change to Google if preferred
                MaxSentences = 5
            };

            // Set your API key (environment variable or direct assignment)
            // SummarizerOptions.ApiKey = "YOUR_API_KEY";

            try
            {
                string summary = DocumentSummarizer.Summarize(doc, options);
                Console.WriteLine("\nSummary:");
                Console.WriteLine(summary);

                System.IO.File.WriteAllText(outputPath, summary);
                Console.WriteLine($"\nSummary saved to \"{outputPath}\".");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Summarization failed: {ex.Message}");
            }
        }
    }
}
```

**期待される出力（例）:**

```
Document loaded successfully.
Summarization will use OpenAI and return up to 5 sentences.

Summary:
The report outlines Q3 revenue growth of 12% driven by new product launches. Customer churn decreased to 3%, the lowest in two years. Marketing spend rose by 8% to support brand awareness. The executive team recommends expanding into the APAC market. Risks include supply‑chain delays and regulatory changes.
```

## 結論

これで、C# で AI を使用して **Word ドキュメント** の内容を要約する、完全で本番環境対応の手法が手に入りました。`SummarizerProvider.OpenAI` を `SummarizerProvider.Google` に置き換えるだけで、他のコードを変更せずに **Google スタイルのドキュメント要約** を実行できます。`MaxSentences` の値を変えたり、バッチ処理を試したり、要約をメール通知やナレッジベースの更新といった大規模なワークフローに統合したりしてみてください。

**次のステップ**  
- 高スループットシナリオ向けに非同期 API（`SummarizeAsync`）を検討する。  
- 要約とキーワード抽出を組み合わせて検索可能なインデックスを構築する。  
- 同様のパターンを使って、プレーンな `.txt` ファイルやウェブページから **AI を使用してテキストを要約** する。

コーディングを楽しんでください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説付きの完全な動作コード例が含まれており、追加の API 機能を習得したり、独自プロジェクトで代替実装アプローチを検討したりするのに役立ちます。

- [Aspose.Words API を使用した C# での Word ドキュメント要約 – 完全 AI 駆動ガイド](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-complete-ai-powered-guide/)
- [Word ドキュメント - テキストの検索と置換](/words/english/net/find-and-replace-text/)
- [Ranges - Word ドキュメントからテキスト取得](/words/english/net/programming-with-ranges/ranges-get-text/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}