---
category: general
date: 2026-03-19
description: ローカルLLMを使用してWordで文法チェックを行い、モデルを登録し、修正された文書を保存する方法を、C#の単一チュートリアルで学びましょう。
draft: false
keywords:
- how to check grammar
- set up local llm
- check grammar in word
- how to register llm
- how to save corrected
language: ja
og_description: ローカルLLMを使用してWordで文法をチェックし、モデルを登録し、修正された文書を保存する方法―ステップバイステップガイド。
og_title: C#でローカルLLMを使って文法をチェックする方法
tags:
- Aspose.Words
- AI
- C#
title: C#でローカルLLMを使って文法をチェックする方法
url: /ja/net/ai-powered-document-processing/how-to-check-grammar-with-a-local-llm-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# でローカル LLM を使用して文法をチェックする方法

テキストをクラウドに送信せずに Word 文書の **文法をチェックする方法** を考えたことはありませんか？ あなたは一人ではありません。多くの開発者が、自己ホスト型モデルのプライバシーを保ちつつ、AI による提案を得たいと考えています。このガイドでは、カスタム LLM の登録、Aspose.Words の設定方法、そして最終的に **修正されたファイルの保存方法** を、純粋な C# で解説します。

また、**ローカル LLM のセットアップ** の詳細、**LLM のエンドポイント登録方法**、そして **Word 文書の文法チェック** 手順を具体的に示します。最後まで読むと、任意の .NET プロジェクトに組み込める実行可能サンプルが手に入ります。

## 前提条件

- .NET 6+ SDK（コードは .NET Core と .NET Framework でも動作します）
- Visual Studio 2022 または C# 拡張機能付き VS Code
- Aspose.Words for .NET（v24.12 以降） – NuGet から取得できます
- OpenAI 互換 API を提供するローカルで動作する LLM（例: ポート 11434 の Ollama）

> **プロのコツ:** Ollama を使用している場合、コマンド `ollama serve` がエンドポイント `http://localhost:11434/api/generate` を自動的に起動します。

## ステップ 1 – llm の登録方法: カスタムモデルを Aspose.Words に追加する

最初に行うべきことは、Aspose.Words に **ローカル llm** を知らせることです。これはアプリケーションの起動時に一度だけ実行します。

```csharp
using Aspose.Words;
using Aspose.Words.AI;

// Register a custom LLM endpoint – no API key required for local servers
AiEngine.RegisterModel(
    modelName: "local-llm",                         // identifier we’ll reference later
    endpoint: new Uri("http://localhost:11434/api/generate"),
    apiKey: null,                                   // local server doesn’t need a key
    provider: AiProvider.Custom);
```

**なぜ重要か:** モデルを登録することで、Aspose.Words に名前付きハンドル（`"local-llm"`）を付与します。後で `CheckGrammar` を呼び出すと、ライブラリはどのエンドポイントにアクセスすべきか正確に把握します。この手順を省略すると、ライブラリは組み込みのクラウドサービスにフォールバックし、プライベート LLM の目的が失われます。

## ステップ 2 – 分析したい Word 文書を読み込む

ここでファイルをメモリに読み込みます。`.docx`、`.doc`、あるいは `.rtf` ファイルを指定できます。

```csharp
// Replace YOUR_DIRECTORY with the actual folder path on your machine
Document sourceDocument = new Document("YOUR_DIRECTORY/input.docx");

// Quick sanity check – print the number of paragraphs we just loaded
Console.WriteLine($"Loaded document with {sourceDocument.GetChildNodes(NodeType.Paragraph, true).Count} paragraphs.");
```

**何が起きているか:** `Document` は Aspose.Words のコアオブジェクトモデルです。ファイルを解析し、ノード（段落、表、画像など）のツリーを構築します。これにより AI エンジンは文法解析のために特定のテキスト範囲を対象にできます。

## ステップ 3 – 文法チェックオプションの設定（ローカル llm のセットアップ）

ここでは、先に登録したモデルを文法チェック操作に結び付けます。

```csharp
AiGrammarCheckOptions grammarOptions = new AiGrammarCheckOptions
{
    Model = "local-llm",               // references the name we used in RegisterModel
    // Optional: you can tweak temperature, maxTokens, etc. if your LLM supports them
    // Temperature = 0.7,
    // MaxTokens = 512
};
```

**これらのオプションを公開する理由:** LLM によって挙動が異なります。`Model` を公開することで、Aspose.Words はローカルモデルとクラウドベースのモデルをコードを変更せずに切り替えられます。この柔軟性は、コンプライアンスやオフラインシナリオ向けに **ローカル llm をセットアップ** する際に不可欠です。

## ステップ 4 – AI 駆動の文法チェックを実行する（Word の文法チェック）

すべてが設定されたら、実際の文法チェックはワンラインで実行できます。

```csharp
// This mutates sourceDocument in place, inserting suggestions and corrections
sourceDocument.CheckGrammar(grammarOptions);
Console.WriteLine("Grammar check completed.");
```

**内部処理:** Aspose.Words は各文を抽出し、LLM エンドポイントに送信し、提案された編集を含む JSON ペイロードを受け取ります。その後、編集内容を文書ツリーに適用します。ここではシンプルさのため同期的に実行していますが、ノンブロッキング I/O を好む場合は非同期オーバーロード `CheckGrammarAsync` を呼び出すこともできます。

## ステップ 5 – 修正された文書の保存方法

AI が処理を終えたら、変更を永続化したくなるでしょう。

```csharp
// Save the corrected file – you can change the format to PDF, HTML, etc.
sourceDocument.Save("YOUR_DIRECTORY/checked.docx");
Console.WriteLine("Corrected document saved as checked.docx");
```

**期待される結果:** Word で `checked.docx` を開くと、文法問題がハイライトされます（`AiGrammarCheckOptions` の設定により自動修正される場合もあります）。トラッキングを有効にしていれば、変更履歴も表示されます。

## 完全な動作例

すべてを組み合わせた、すぐに実行できるコンソールアプリがこちらです:

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.AI;

class Program
{
    static void Main()
    {
        // 1️⃣ Register the local LLM
        AiEngine.RegisterModel(
            modelName: "local-llm",
            endpoint: new Uri("http://localhost:11434/api/generate"),
            apiKey: null,
            provider: AiProvider.Custom);

        // 2️⃣ Load the source document
        string inputPath = "YOUR_DIRECTORY/input.docx";
        Document sourceDocument = new Document(inputPath);
        Console.WriteLine($"Loaded: {inputPath}");

        // 3️⃣ Set up grammar‑check options (using the local model)
        AiGrammarCheckOptions grammarOptions = new AiGrammarCheckOptions
        {
            Model = "local-llm"
        };

        // 4️⃣ Perform the AI‑driven grammar check
        sourceDocument.CheckGrammar(grammarOptions);
        Console.WriteLine("Grammar analysis finished.");

        // 5️⃣ Save the corrected document
        string outputPath = "YOUR_DIRECTORY/checked.docx";
        sourceDocument.Save(outputPath);
        Console.WriteLine($"Corrected file saved to: {outputPath}");
    }
}
```

**コンソールに期待される出力:**

```
Loaded: YOUR_DIRECTORY/input.docx
Grammar analysis finished.
Corrected file saved to: YOUR_DIRECTORY/checked.docx
```

`checked.docx` を開くと、文法の改善が自動的に適用されているのが確認できるはずです。

## よくある質問とエッジケース

| Question | Answer |
|----------|--------|
| *LLM が API キーを必要とする場合はどうすればよいですか？* | `RegisterModel` の `apiKey` にキーを渡します。同じコードはキーあり・キーなしのサービスの両方で動作します。 |
| *別のファイル形式を使用できますか？* | もちろんです。`Document.Save` は `.pdf`、`.html`、`.txt` などを受け付けます。拡張子を変更するだけです。 |
| *LLM がエラーを返した場合はどうすればよいですか？* | `CheckGrammar` を try/catch で囲み、詳細は `AiException` を確認します。多くの場合はタイムアウトなので、`grammarOptions.Timeout` の増加を検討してください。 |
| *この操作はスレッドセーフですか？* | 登録手順はグローバルで、起動時に一度だけ実行すべきです。その後の `CheckGrammar` 呼び出しは、各々が独自の `Document` インスタンスを使用していれば並列実行しても安全です。 |

## 次のステップ

**ローカル llm** を使って **文法をチェックする方法** が分かったので、以下を検討してみてください:

- **バッチ処理**: フォルダー内の文書をループし、同じパイプラインを実行する。
- **カスタムプロンプト**: `grammarOptions.PromptTemplate` を設定して、スタイル別チェック用にリクエストペイロードを調整する。
- **ASP.NET Core との統合**: アップロードされた `.docx` ファイルを受け取り、文法チェックを実行し、修正済みファイルを返す API エンドポイントを公開する。

これらの拡張により、社内に留まったままでフル機能の “文法 as a Service” プラットフォームを構築できます。

---

*コーディングを楽しんでください！ 問題があれば下にコメントを残してください—設定の微調整を喜んでお手伝いします。*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}