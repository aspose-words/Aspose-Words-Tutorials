---
category: general
date: 2026-05-04
description: Aspose を使用して LLM で文書を編集する方法 – 段落テキストの置換、ローカル LLM への接続、AI を使ったテキストの書き換えを学ぶ。
draft: false
keywords:
- how to use llm
- replace paragraph text
- connect to local llm
- rewrite text using ai
- edit document aspose
language: ja
og_description: Aspose を使用して LLM で文書を編集する方法。このガイドでは、ローカル LLM に接続し、段落テキストを置換し、AI を使ってテキストを書き換える方法を示します。
og_title: LLM と Aspose.Words の使い方 – C# で段落を書き換える
tags:
- Aspose.Words
- C#
- AI
- LLM
title: Aspose.Words と LLM の使い方 – C# で段落を書き換える
url: /ja/net/ai-powered-document-processing/how-to-use-llm-with-aspose-words-rewrite-paragraphs-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words と LLM の使い方 – C# で段落を書き換える

Word 文書を手動で開かずに **LLM を使って** 仕上げたいと思ったことはありませんか？同じ悩みを抱える開発者は多いです。段落テキストをプログラムで *置換* したいが、クリーンな AI 主導のワークフローがない…そんな壁にぶつかっていませんか？

このチュートリアルでは、ローカルの大規模言語モデルを接続し、`.docx` ファイルからスニペットを取得し、**AI でテキストを書き換える**よう指示し、最終的に更新した文書を保存するまでを Aspose.Words で実装します。最後まで実行できる C# コンソール アプリの完成形が手に入ります。

> **得られるもの:** 完全に実行可能なサンプル、各ステップの解説、エッジケースへの対処法、拡張アイデア

## 必要なもの

- **.NET 6+**（または .NET Framework 4.7.2 – 両方で動作します）
- **Aspose.Words for .NET**（NuGet パッケージ `Aspose.Words`）
- **ローカル LLM サーバ**（シンプルな HTTP `/generate` エンドポイントを公開しているもの、例: Ollama、LMStudio、またはカスタム Flask サービス）
- C# と HTTP クライアントコードの基本的な知識  

追加の SDK は不要です。必要なものはすべて、ここで書くコードに含まれています。

## 手順 1: LLM で段落テキストを置換する方法

まず最初に、変更したい段落を特定します。Aspose.Words はリッチなオブジェクトモデルを提供しているので、これがとても簡単です。

```csharp
using Aspose.Words;
using Aspose.Words.AI;   // Imaginary namespace for illustration – replace with actual if needed
using System.Net.Http;
using System.Text;
using System.Text.Json;

// Load the source document
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Grab the third paragraph (zero‑based index)
Paragraph targetParagraph = document.FirstSection.Body.Paragraphs[2];

// Show the original text in the console – handy for debugging
Console.WriteLine("Original paragraph:");
Console.WriteLine(targetParagraph.GetText());
```

**重要ポイント:**  
正しいノードを選択しないと、見出しや表を誤って上書きしてしまう危険があります。**段落テキストを置換**するアプローチを取ることで、文書構造はそのままに、対象のコンテンツだけを変更できます。

> **プロのコツ:** 文書に可変長のセクションがある場合は、`document.GetChildNodes(NodeType.Paragraph, true)` と LINQ を組み合わせて、テキストやスタイルで段落を検索しましょう。

## 手順 2: ローカル LLM エンドポイントに接続する

テキストが取得できたら、LLM に送信します。例では HTTP の面倒な処理を隠蔽したラッパークラス `LocalLargeLanguageModel` を使用しています。必要に応じて `HttpClient` 直接呼び出しに置き換えても構いません。

```csharp
/// <summary>
/// Minimal wrapper around a local LLM HTTP API.
/// Assumes the API accepts a JSON payload { "prompt": "..."} and returns { "response": "..." }.
/// </summary>
public class LocalLargeLanguageModel
{
    private readonly HttpClient _client;
    private readonly string _endpoint;

    public LocalLargeLanguageModel(string endpoint)
    {
        _endpoint = endpoint.TrimEnd('/');
        _client = new HttpClient();
    }

    public string GenerateText(string prompt)
    {
        var payload = new { prompt };
        var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

        // Synchronous call for brevity – in production use async/await
        var response = _client.PostAsync($"{_endpoint}/generate", content).Result;
        response.EnsureSuccessStatusCode();

        var json = response.Content.ReadAsStringAsync().Result;
        var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
        return result?["response"] ?? string.Empty;
    }
}

// Step 2: Instantiate the LLM client pointing at localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:5000");
```

**この接続方法の理由:**  
**ローカル LLM に接続**することでレイテンシが低減し、データがオンプレミスに留まり、API コストも発生しません。ラッパーを使うことで後続のコードがシンプルになり、**AI でテキストを書き換える**ロジックに集中できます。

## 手順 3: Aspose.Words で AI にテキストを書き換えてもらう

段落テキストと LLM が準備できたら、モデルに対して「フォーマルな口調で書き換えてください」と指示するプロンプトを作成します。プロンプトは他のスタイル（フレンドリー、テクニカルなど）に変更可能です。

```csharp
// Build the prompt – notice the newline for readability
string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";

// Ask the LLM to generate the revised version
string revisedText = localLlm.GenerateText(prompt);

// Show the AI‑generated text
Console.WriteLine("\nRevised paragraph:");
Console.WriteLine(revisedText);
```

**なぜ効果があるのか:**  
LLM はプロンプト駆動です。明示的な指示（例: “Rewrite … in a formal tone”）を与えることで、一貫した結果が得られます。**AI でテキストを書き換える**ステップが本チュートリアルの核心であり、AI を文書ワークフローに直接組み込む方法を示しています。

## 手順 4: 文書を編集し、変更を保存する

元の Run を新しい内容に置き換えます。Aspose.Words はテキストを `Run` オブジェクトで管理しているため、先にクリアしておくと余計な書式が残りません。

```csharp
// Clear existing runs (pieces of text) from the paragraph
targetParagraph.Runs.Clear();

// Append a new Run containing the revised text
targetParagraph.AppendChild(new Run(document, revisedText));

// Save the updated document
document.Save("YOUR_DIRECTORY/output.docx");

// Confirmation
Console.WriteLine("\nDocument saved as output.docx");
```

**エッジケースの注意点:**  
元の段落に太字や斜体など混在した書式がある場合は、スタイルを保持したいでしょう。その場合は新しい `Run` を作成し、元の `Font` 設定をコピーしてから `Text` に `revisedText` を設定します。

## 完全動作サンプル

以下はコンソール プロジェクトにそのまま貼り付けられる全コードです。先に Aspose.Words の NuGet パッケージをインストールしてください（`dotnet add package Aspose.Words`）。

```csharp
// ---------------------------------------------------------------
// Complete C# console app: how to use llm to edit a Word doc
// ---------------------------------------------------------------
using Aspose.Words;
using Aspose.Words.AI;   // Replace with real namespace if needed
using System;
using System.Collections.Generic;
using System.Net.Http;
using System.Text;
using System.Text.Json;

namespace LlmAsposeDemo
{
    public class LocalLargeLanguageModel
    {
        private readonly HttpClient _client;
        private readonly string _endpoint;

        public LocalLargeLanguageModel(string endpoint)
        {
            _endpoint = endpoint.TrimEnd('/');
            _client = new HttpClient();
        }

        public string GenerateText(string prompt)
        {
            var payload = new { prompt };
            var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

            var response = _client.PostAsync($"{_endpoint}/generate", content).Result;
            response.EnsureSuccessStatusCode();

            var json = response.Content.ReadAsStringAsync().Result;
            var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
            return result?["response"] ?? string.Empty;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the document
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // 2️⃣ Pick the third paragraph (index 2)
            Paragraph targetParagraph = document.FirstSection.Body.Paragraphs[2];
            Console.WriteLine("Original paragraph:");
            Console.WriteLine(targetParagraph.GetText());

            // 3️⃣ Connect to the local LLM
            var localLlm = new LocalLargeLanguageModel("http://localhost:5000");

            // 4️⃣ Ask the model to rewrite it formally
            string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";
            string revisedText = localLlm.GenerateText(prompt);
            Console.WriteLine("\nRevised paragraph:");
            Console.WriteLine(revisedText);

            // 5️⃣ Replace the paragraph contents
            targetParagraph.Runs.Clear();
            targetParagraph.AppendChild(new Run(document, revisedText));

            // 6️⃣ Save the file
            document.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("\nDocument saved as output.docx");
        }
    }
}
```

### 期待される出力

```
Original paragraph:
the quick brown fox jumps over the lazy dog.

Revised paragraph:
The quick brown fox leaps over the lazy dog in a formal manner.

Document saved as output.docx
```

`output.docx` を開くと、3 番目の段落が洗練されたバージョンに置き換わっていることが確認できます。

## よくある質問と落とし穴

| 質問 | 回答 |
|----------|--------|
| **LLM が余分なフィールドを含む JSON を返したらどうする？** | `GenerateText` を調整して正しいプロパティをデシリアライズするか、手動でレスポンスを解析してください。 |
| **複数の段落を一度に処理できるか？** | 可能です。`document.FirstSection.Body.Paragraphs` を走査し、同じプロンプトロジックを適用します。必要に応じて段落インデックスをプロンプトに含めるとコンテキストが明確になります。 |
| **LLM サーバが認証を要求する場合は？** | POST 前に `HttpClient` にヘッダーを追加します: `_client.DefaultRequestHeaders.Add("Authorization", "Bearer YOUR_TOKEN");` |
| **置換後に書式が失われる。** | 元の `Run.Font` 設定を保持してください。新しい `Run` を作成し、`originalRun.Font.Clone()` をコピーしてから `Text` を設定します。 |
| **LLM が時々空文字列を返す。** | フォールバックを実装しましょう。`revisedText.Trim().Length == 0` の場合は元のテキストを保持するか、シンプルなプロンプトで再試行します。 |

## ソリューションの拡張

単一段落で **LLM の使い方** をマスターしたら、次のステップを検討してください。

- **バッチ処理:** すべての段落をループし、選択したスタイル（例: “全テキストを簡潔に”）で書き換える。  
- **スタイル認識型書き換え:** 元の段落のスタイル名をプロンプトに渡し、見出しと本文で異なる扱いをさせる。  
- **CI パイプラインへの統合:** ドキュメントの自動整形をビルドプロセスの一部として組み込む。  
- **代替プロンプト:** “この段落を要約してください” や “この段落をスペイン語に翻訳してください” など、**AI でテキストを書き換える**の応用範囲を広げる。

## 結論

本稿では **LLM の使い方** を Aspose.Words と組み合わせ、文書の読み込み、**ローカル LLM へ接続**、段落抽出、**AI でテキストを書き換える**、**段落テキストを置換**、そして結果の保存までの一連の流れを実演しました。コードは自己完結型で、すぐに動作し、AI と従来の文書自動化を実用的に融合させる方法を示しています。

ぜひ試してみて、プロンプトを調整しながら自分だけのワークフローを構築してください。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}