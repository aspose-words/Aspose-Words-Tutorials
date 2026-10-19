---
category: general
date: 2026-02-21
description: DOCX を読み込み、テキストをローカル LLM に送信して文法をチェックし、修正されたバージョンを書き戻す方法。LLM の使い方と Word
  文書のテキストの読み取り方法を含む。
draft: false
keywords:
- how to check grammar
- how to use llm
- read word document text
- load docx in c#
language: ja
og_description: DOCX を読み込み、そのテキストをローカル LLM に送信し、修正されたバージョンを書き戻すことで C# で文法をチェックする方法。LLM
  の使い方と Word 文書のテキストの読み取り方を学びましょう。
og_title: ローカルLLMを使ってC#の文法をチェックする方法
tags:
- C#
- LLM
- Aspose.Words
title: ローカルLLMを使用してC#で文法をチェックする方法
url: /ja/net/ai-powered-document-processing/how-to-check-grammar-in-c-using-a-local-llm/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#でローカルLLMを使って文法をチェックする方法

C#プロジェクトを離れずにWord文書の**文法チェック**をしたことがありますか？ あなただけではありません—開発者は常に「チャットボットを動かすのと同じコードで校正を自動化できるか？」と尋ねます。短い答えは「はい」です。DOCXを読み込み、テキストを抽出し、ローカルでホストされた大規模言語モデル（LLM）に渡すことで、即座に文法修正が得られ、洗練された結果をそのままファイルに書き戻すことができます。

このチュートリアルでは、全工程を順に解説します：**load docx in c#**で`.docx`を読み込み、文法修正のために**how to use llm**を呼び出し、最後にクリーンアップしたドキュメントを保存します。最後までに、手動でコピー＆ペーストしたり外部APIを使ったりすることなく、純粋なC#とローカルLLMエンドポイントだけで動作するコンソールアプリが完成します。

> **必要なもの**
> - .NET 6.0 以降（コードは .NET Framework でも動作しますが、.NET 6 が最適です）
> - [Aspose.Words for .NET](https://products.aspose.com/words/net/) ライブラリ（無料トライアルでテスト可能）
> - `CheckGrammar(string)` エンドポイントを提供する LLM サーバー（例：Ollama、LM Studio、またはカスタム FastAPI ラッパー）
> - async/await の基本的な知識（任意ですが推奨）

**なぜこれが重要か**と疑問に思うなら、生成されたレポートの誤字を手作業で修正する時間を考えてみてください。このステップを自動化すれば、パイプラインが高速化するだけでなく、数十件の文書間で一貫性が保証されます。さあ、始めましょう。

## 文法チェックの概要

本格的に始める前に、簡単なロードマップをご紹介します：

1. **ローカルLLMエンドポイントと通信するクライアントを作成**します。  
2. Aspose.Words を使用して **Word文書を読み取ります**—これは C# で **read word document text** を行う古典的な方法です。  
3. **生テキストをLLMに送信**し、修正済みのバージョンを受け取ります。  
4. 文書内の **元のコンテンツを修正テキストに置き換え** ます。  
5. **保存**します（オプションですが、通常は必要です）。

各ステップは個別のメソッドにまとめられているので、後で再利用したり置き換えたりできます。完全なソースコードは記事の最後に掲載されています。

## ステップ1: LLMクライアントの設定 (How to Use LLM)

コードを整理するために、HTTP呼び出しを小さなラッパークラスにカプセル化します。このクラスは、LLMサービスが JSON ペイロード `{ "prompt": "..."}` を含む POST リクエストを受け取り、`{ "response": "..." }` を返すことを前提としています。サービスが異なる場合はシリアライズ方法を調整してください。

```csharp
using System.Net.Http;
using System.Text;
using System.Text.Json;
using System.Threading.Tasks;

/// <summary>
/// Minimal client for a local LLM that offers a grammar‑checking endpoint.
/// </summary>
public class LocalLargeLanguageModel
{
    private readonly HttpClient _http;
    private readonly string _baseUrl;

    public LocalLargeLanguageModel(string baseUrl)
    {
        _baseUrl = baseUrl.TrimEnd('/');
        _http = new HttpClient();
    }

    /// <summary>
    /// Sends the input text to the LLM and returns the corrected version.
    /// </summary>
    public async Task<string> CheckGrammarAsync(string input)
    {
        var payload = new { prompt = $"Correct the grammar and punctuation:\n\n{input}" };
        var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

        // The endpoint is assumed to be /grammar
        var response = await _http.PostAsync($"{_baseUrl}/grammar", content);
        response.EnsureSuccessStatusCode();

        var json = await response.Content.ReadAsStringAsync();
        var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
        return result != null && result.TryGetValue("response", out var corrected) ? corrected : input;
    }
}
```

**なぜ重要か:**  
- **Decoupling** – 後で Ollama から LM Studio に切り替える場合でも、URL またはペイロード形式を変更するだけで済みます。  
- **Async‑friendly** – ネットワーク I/O が UI やバックグラウンドワーカーをブロックしません。  
- **Error handling** – `EnsureSuccessStatusCode` は LLM がダウンした場合に明確な例外をスローし、後で捕捉します。

> **プロのコツ:** LLM が GPU 上で動作している場合、レイテンシスパイクを防ぐためにリクエストサイズを約4KB未満に抑えてください。

## ステップ2: DOCX の読み込みとテキスト抽出 (Read Word Document Text)

Aspose.Words を使えば Word ファイルの読み取りが非常に簡単です。`Document.GetText()` メソッドは改行を保持したまま、表示可能な全テキストを返します。テーブルや脚注などリッチなフォーマットが必要な場合はノードツリーを走査する必要がありますが、文法チェックだけならプレーンテキストで十分です。

```csharp
using Aspose.Words;

/// <summary>
/// Loads a .docx file and returns its raw textual content.
/// </summary>
public static string ReadDocumentText(string filePath)
{
    if (!File.Exists(filePath))
        throw new FileNotFoundException($"Document not found: {filePath}");

    var doc = new Document(filePath);
    return doc.GetText(); // Returns text with line breaks
}
```

**エッジケースの注意:**  
文書に英語以外の文字や特殊記号が含まれる場合、使用している LLM モデルが Unicode をサポートしていることを確認してください。ほとんどの最新モデルは対応していますが、古いモデルは文字が切り捨てられたり誤解されたりする可能性があります。

## ステップ3: 修正テキストでコンテンツを置き換える

Aspose.Words には「本文全体を置換」するワンライナーはありませんが、ノードツリーをクリアして単一の段落を挿入すればうまく動作します。これにより、トラッキング変更などの隠れたマークアップも除去されます。

```csharp
/// <summary>
/// Overwrites the document with the supplied corrected text.
/// </summary>
public static void WriteCorrectedText(string filePath, string correctedText)
{
    var doc = new Document(filePath);
    doc.RemoveAllChildren(); // Clears sections, paragraphs, tables, etc.

    var builder = new DocumentBuilder(doc);
    builder.Writeln(correctedText); // Writes as a single paragraph; you can split by "\n" if you want multiple paragraphs.

    doc.Save(filePath); // Overwrites the original file
}
```

**すべての子ノードを削除する理由:**  
- クリーンな状態を保証し、残存する書式が新しいコンテンツに干渉するのを防ぎます。  
- コードがシンプルになるため、特定のノードを探して置換する必要がなくなります。

元の見出しを保持したい場合は、元のノードツリーを解析し、`Run` ノードだけを置換することも可能ですが、これは本チュートリアルの範囲を超える複雑さが伴います。

## ステップ4: 全体を結合 – 完全動作例

以下に完全なコンソールプログラムを示します。**文法チェックの方法**を最初から最後まで実演し、基本的なエラーハンドリングとオプションのコマンドライン引数も含んでいます。

```csharp
using System;
using System.IO;
using System.Threading.Tasks;
using Aspose.Words;

// Ensure you have a license or are okay with the evaluation watermark.
class Program
{
    // Adjust these paths to match your environment.
    private const string InputPath = @"YOUR_DIRECTORY\input.docx";
    private const string OutputPath = @"YOUR_DIRECTORY\output.docx";
    private const string LlmEndpoint = "http://localhost:5000";

    static async Task Main(string[] args)
    {
        try
        {
            // 1️⃣ Create the LLM client.
            var llm = new LocalLargeLanguageModel(LlmEndpoint);

            // 2️⃣ Load the DOCX and read its text.
            Console.WriteLine("Reading document...");
            string originalText = ReadDocumentText(InputPath);

            // 3️⃣ Send text to the LLM for grammar correction.
            Console.WriteLine("Sending text to LLM for grammar check...");
            string correctedText = await llm.CheckGrammarAsync(originalText);

            // 4️⃣ Write the corrected text back into a new file.
            Console.WriteLine("Writing corrected text to new document...");
            // We copy the original file first so the original remains untouched.
            File.Copy(InputPath, OutputPath, overwrite: true);
            WriteCorrectedText(OutputPath, correctedText);

            Console.WriteLine($"✅ Grammar check complete! Updated file saved to: {OutputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ An error occurred: {ex.Message}");
            // For real‑world apps, consider logging the stack trace.
        }
    }

    // --- Helper methods from earlier steps ---
    public static string ReadDocumentText(string filePath)
    {
        if (!File.Exists(filePath))
            throw new FileNotFoundException($"Document not found: {filePath}");

        var doc = new Document(filePath);
        return doc.GetText();
    }

    public static void WriteCorrectedText(string filePath, string correctedText)
    {
        var doc = new Document(filePath);
        doc.RemoveAllChildren();

        var builder = new DocumentBuilder(doc);
        // Preserve line breaks by splitting and writing each line.
        foreach (var line in correctedText.Split(new[] { "\r\n", "\n" }, StringSplitOptions.None))
        {
            builder.Writeln(line);
        }

        doc.Save(filePath);
    }
}
```

### 期待される出力

プログラムを実行すると（`dotnet run`）、コンソールに以下のような出力が表示されます：

```
Reading document...
Sending text to LLM for grammar check...
Writing corrected text to new document...
✅ Grammar check complete! Updated file saved to: YOUR_DIRECTORY\output.docx
```

`output.docx` を Word で開くと、同じ内容ですが句読点や主語‑動詞の一致、明らかな誤字が LLM によって修正された状態になっています。

## よくある質問とエッジケース

### LLM が `null` または空文字列を返した場合は？

`CheckGrammarAsync` メソッドは、レスポンスペイロードに `response` フィールドがない場合、元の入力にフォールバックします。これにより、文書が誤って消去されることを防げます。

### リクエストがタイムアウトするまでに文書はどれくらいのサイズまで対応できるか？

ほとんどのローカル LLM サーバーは数千文字程度なら問題なく処理できます。より大きなファイル（例：100 KB 以上）の場合は、テキストを段落単位で分割し、各チャンクを個別に送信してから修正済みの部分を再構築することを検討してください。約2 KB のチャンクサイズが出発点として適切です。

### 画像、テーブル、脚注は保持されますか？

いいえ。すべての子ノードをクリアするため、テキスト以外の要素は失われます。これらを保持したい場合は、ノードツリーを走査し、`Run` ノード（テキスト断片）だけを置換し、他のノードはそのままにしておく必要があります。これはより高度なシナリオですので、`NodeCollection` 操作に関する Aspose.Words API をぜひ調べてみてください。

### ローカルではなくクラウド LLM を使用できますか？

もちろん可能です。`LocalLargeLanguageModel` のエンドポイント URL とペイロード形式を置き換えるだけです。クラウドサービスはレートリミットやコストが発生することが多いのに対し、ローカルモデルはオフラインで動作し、初期の GPU/CPU 設定以降は無料です。

## プロのコツとベストプラクティス

- **クライアントをキャッシュ**: 同じ `HttpClient` インスタンスを再利用することで、 

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}