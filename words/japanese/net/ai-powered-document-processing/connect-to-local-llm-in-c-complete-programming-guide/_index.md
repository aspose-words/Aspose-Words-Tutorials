---
category: general
date: 2026-04-28
description: C# からローカル LLM に接続し、大規模言語モデルに Word 文書の読み込みを指示し、ローカル LLM を呼び出してテキストを自動的に書き換える。ステップバイステップのコードが含まれています。
draft: false
keywords:
- connect to local llm
- prompt large language model
- load word document
- call local llm
- rewrite text automatically
language: ja
og_description: C#からローカルLLMに接続し、大規模言語モデルへのプロンプト方法、Word文書の読み込み、ローカルLLMの呼び出し、そして数分でテキストを自動的に書き換える方法を確認できます。
og_title: C#でローカルLLMに接続する – 完全プログラミングガイド
tags:
- Aspose.Words
- C#
- LLM
- AI Automation
title: C#でローカルLLMに接続する – 完全プログラミングガイド
url: /ja/net/ai-powered-document-processing/connect-to-local-llm-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#でローカルLLMに接続 – 完全プログラミングガイド

.NET アプリから **connect to local llm** して、Word ファイルとやり取りさせたいことはありませんか？ あなたは一人ではありません。このガイドでは、ローカルLLM に接続し、**prompt large language model**、Word 文書をロードし、**call local llm**、そして最終的に **rewrite text automatically** する全プロセスを解説します。最後まで実行可能なサンプルができ、任意の段落をフォーマルな口調に変換でき、外部 API キーは一切不要です。

## このチュートリアルでカバーする内容

必要な NuGet パッケージをインストールし、シンプルなローカル LLM エンドポイント（例: ポート 11434 の Ollama）を起動します。その後、Aspose.Words を使って `.docx` ファイルを読み込み、段落を LLM に送信し、書き換えたバージョンを受け取って同じ文書に書き戻します。さらに、null 段落、非同期破棄、エンコーディングの問題といった一般的な落とし穴への対処方法も紹介するので、コードはデモだけでなく本番環境でも動作します。

### 前提条件

- .NET 6.0 SDK 以上（.NET 8 でも可）
- Visual Studio 2022 または C# 拡張機能付き VS Code
- **Aspose.Words for .NET**（無料トライアルで問題ありません）
- `/api/generate` 契約に対応したローカルホストの LLM（例: Ollama、LMStudio）
- C# の async/await の基本的な知識

> **Pro tip:** まだ Ollama をインストールしていない場合は `ollama serve` を実行し、`ollama pull llama3` でモデルを取得してください。デフォルトの HTTP エンドポイントは `http://localhost:11434/api/generate` です。

## ステップ1: 必要なパッケージをインストール

まず、プロジェクトに Aspose.Words と Aspose.Words.AI の NuGet パッケージを追加します。

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

これらのライブラリは **load word document** 機能と、HTTP リクエストを手作業で作成せずに **call local llm** できる薄いラッパーを提供します。

## ステップ2: ローカルLLMエンドポイントに接続

ローカルでホストされたモデルへの接続は、`LocalLargeLanguageModel` をインスタンス化するだけで完了します。コンストラクタには生成エンドポイントの完全な URL を渡します。

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System.Threading.Tasks;

// Create a client that talks to the LLM running on localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");
```

なぜエンドポイントをクラスでラップするのか？ `LocalLargeLanguageModel` は JSON シリアライズ、リトライ、ストリーミング応答を自動で処理してくれるため、`HttpClient` をいじる代わりにプロンプトロジックに集中できます。

## ステップ3: ソースWord文書をロード

次に、文書をメモリに取り込みます。Aspose.Words は事実上すべての Word フォーマットに対応しているので、`Document` は Office がインストールされていなくても `input.docx` を解析できます。

```csharp
// Path to the source file – adjust as needed
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document; throws if the file is missing or corrupted
Document sourceDocument = new Document(inputPath);
```

ストリーム（例: ASP.NET でアップロードされたファイル）で処理したい場合は、ファイルパスを `MemoryStream` に置き換えて `Document` コンストラクタに渡すだけです。

## ステップ4: 現在の段落テキストを抽出

`DocumentBuilder` を使って文書を操作します。この例では **the first paragraph** を書き換えますが、`sourceDocument.GetChildNodes(NodeType.Paragraph, true)` をループすれば多数の段落を処理できます。

```csharp
// Builder gives us a cursor inside the document
DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);

// Grab the text of the paragraph where the builder is currently positioned
string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

// Safety check – avoid sending empty strings to the LLM
if (string.IsNullOrWhiteSpace(originalParagraph))
{
    Console.WriteLine("No paragraph found at the current cursor position.");
    return;
}
```

`?.` 演算子は、文書が空の場合に `NullReferenceException` が発生するのを防ぎます。これは初心者がつまずきやすい **edge cases** の一つです。

## ステップ5: LLMに段落を書き換えるようプロンプト

いよいよ **prompt large language model** を実行します。プロンプトはプレーンな英語で、ラッパーが JSON に変換してローカルエンドポイントに送ります。

```csharp
// Build a friendly instruction for the model
string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";

// Await the model's response – this is an async call
string rewrittenParagraph = await localLlm.PromptAsync(prompt);
```

なぜこのようにリクエストを構成するのか？ LLM は明確で単一タスクの指示に最もよく応答します。コロンの後に改行を入れることで指示とコンテンツを分離し、モデルがプロンプトをそのままエコーしてしまう可能性を減らします。

**期待される出力** – `originalParagraph` が `"Hey, what's up?"` の場合、LLM は次のように返すかもしれません:

> “Good day, how may I assist you?”

結果は次のように出力して確認できます:

```csharp
Console.WriteLine("Original:  " + originalParagraph);
Console.WriteLine("Rewritten: " + rewrittenParagraph);
```

## ステップ6: 書き換えたテキストを文書に挿入

新しいテキストが手に入ったら、古い段落を置き換えます。`DocumentBuilder.Writeln` は改行を書き込みカーソルを前進させるので、追記に最適です。*replace* したい場合は、書き込む前に `docBuilder.CurrentParagraph.RemoveAllChildren()` を使用してください。

```csharp
// Option A – Append a new paragraph (keeps the original)
docBuilder.Writeln(rewrittenParagraph);

// Option B – Replace the existing paragraph (uncomment to use)
// docBuilder.CurrentParagraph.RemoveAllChildren();
// docBuilder.CurrentParagraph.AppendChild(new Run(docBuilder.Document, rewrittenParagraph));
```

両方のアプローチを示しているので、ワークフローに合う方を選んでください。

## ステップ7: 更新された文書を保存

最後に、変更を新しいファイルに永続化します。Aspose.Words は拡張子に基づいて自動的にフォーマットを選択します。

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
sourceDocument.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Word で `output.docx` を開くと、段落がフォーマルな口調に変わっていることが確認できます。

## 完全な動作例

以下は **complete, self‑contained program** です。コンソールプロジェクトにコピペし、NuGet パッケージを復元して実行してください。ローカル LLM が起動している以外は追加設定は不要です。

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System;
using System.IO;
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        // -------------------------------------------------
        // Step 1: Connect to the locally hosted LLM endpoint
        // -------------------------------------------------
        var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");

        // -------------------------------------------------
        // Step 2: Load the source Word document
        // -------------------------------------------------
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        Document sourceDocument = new Document(inputPath);

        // -------------------------------------------------
        // Step 3: Retrieve the text of the current paragraph
        // -------------------------------------------------
        DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);
        string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

        if (string.IsNullOrWhiteSpace(originalParagraph))
        {
            Console.WriteLine("No paragraph found at the current cursor position.");
            return;
        }

        // -------------------------------------------------
        // Step 4: Ask the LLM to rewrite the paragraph in a formal tone
        // -------------------------------------------------
        string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";
        string rewrittenParagraph = await localLlm.PromptAsync(prompt);

        // -------------------------------------------------
        // Step 5: Insert the rewritten text back into the document
        // -------------------------------------------------
        docBuilder.Writeln(rewrittenParagraph);

        // -------------------------------------------------
        // Step 6: Save the updated document
        // -------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        sourceDocument.Save(outputPath);

        Console.WriteLine("Original paragraph:");
        Console.WriteLine(originalParagraph);
        Console.WriteLine("\nRewritten paragraph:");
        Console.WriteLine(rewrittenParagraph);
        Console.WriteLine($"\nDocument saved to {outputPath}");
    }
}
```

### 実行時の期待結果

1. コンソールに元の段落と書き換え後の段落が表示されます。  
2. `output.docx` が `input.docx` の隣に生成されます。  
3. ファイルを開くと、新しいフォーマルな段落が元の段落の後に挿入（または代替コードに切り替えた場合は置き換え）されていることが確認できます。

## 一般的なエッジケースの対処

| Situation | Solution |
|-----------|----------|
| **Empty or whitespace‑only paragraph** | `string.IsNullOrWhiteSpace` をチェックしてからプロンプトを送信します（Step 3 参照）。 |
| **LLM returns an error or empty string** | `PromptAsync` を `try/catch` でラップし、失敗時は元のテキストにフォールバックします。 |
| **Multiple paragraphs need rewriting** | `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` をループし、同じプロンプトロジックを適用します。 |
| **Large documents cause latency** | 段落をバッチ化して 1 回のリクエストで送信します（1 回の呼び出しで最大 4 KB のプロンプトが目安）。 |
| **Non‑ASCII characters get garbled** | LLM エンドポイントが UTF‑8 を使用していることを確認します（ほとんどの最新モデルは対応）。 |

## 次のステップと関連トピック

- **Prompt large language model** にスタイルガイドや長さ制限など、よりリッチな指示を付与する。  
- **call local llm** を Web API で利用し、文書自動化をサービスとして公開する。  
- 高スループットシナリオ向けに **load word document** を並列ストリームで処理する方法を探る。  
- この手法と **rewrite text automatically** を組み合わせて、メール大量生成やレポート標準化に活用する。  

さらに深掘りしたい場合は、Aspose の **document merging** に関するドキュメントと、カスタムサンプリングパラメータ用の Ollama API リファレンスをご覧ください。

## 結論

今回、C# から **connect to local llm** し、**prompt large language model**、**load word document**、**call local llm**、そして **rewrite text automatically** する方法を、単一の実行可能コンソールアプリで示しました。このパターンはスケール可能で、プロンプトを差し替えたり段落をループ処理したり、ASP.NET エンドポイントとして公開したりと応用が利きます。重要なポイントは、ローカル AI モデルを従来の文書処理ライブラリと緊密に統合でき、信頼できるオンプレミス環境を離れることなく強力な自動化が実現できるということです。

スレッドに関する質問があれば、

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}