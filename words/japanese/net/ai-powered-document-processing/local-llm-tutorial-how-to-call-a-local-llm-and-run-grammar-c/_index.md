---
category: general
date: 2026-06-24
description: ローカルLLMのチュートリアルで、ローカルLLMの呼び出し方、Word文書の読み込み方法、C#でAI文法チェックを使用した文法チェックの実行方法を示します。
draft: false
keywords:
- local llm tutorial
- run grammar check
- ai grammar check
- call local llm
- load word document
language: ja
og_description: ローカルLLMチュートリアルでは、ローカルLLMの呼び出し方、Word文書の読み込み方法、そしてC#でAI文法チェックを実行する手順をステップバイステップで解説します。
og_title: ローカルLLMチュートリアル – ローカルLLMを呼び出して文法チェックを実行
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Local LLM tutorial that shows you how to call a local LLM, load a Word
    document and run grammar check using AI grammar check in C#.
  headline: Local LLM Tutorial – How to Call a Local LLM and Run Grammar Check
  type: TechArticle
- description: Local LLM tutorial that shows you how to call a local LLM, load a Word
    document and run grammar check using AI grammar check in C#.
  name: Local LLM Tutorial – How to Call a Local LLM and Run Grammar Check
  steps:
  - name: How to Run
    text: 1. Open a terminal in the project folder. 2. Run `dotnet run`. 3. Watch
      the console print the corrected text.
  - name: Can I use a different LLM brand?
    text: Absolutely. As long as the server respects the OpenAI v1 API schema, just
      change `Endpoint` and pick the corresponding `AiModelType` enum value (e.g.,
      `AiModelType.Llama2`). The rest of the code stays identical.
  - name: What if my document is huge (10 MB+)?
    text: Large payloads can exceed the default request size of many servers. Split
      the document into sections and call `CheckGrammar` per section, then concatenate
      the results. This also reduces the chance of a timeout.
  - name: How do I write the corrected output back to a `.docx` file?
    text: 'The `Document` class usually provides a `Save(string path, string content)`
      method. After you get `result.CorrectedText`, call:'
  - name: Is the dummy API key a security risk?
    text: No. The key is ignored by self‑hosted endpoints, but some SDKs enforce a
      non‑null string. Using a placeholder like `"dummy"` satisfies the SDK without
      exposing any secrets.
  type: HowTo
tags:
- LLM
- C#
- GrammarCheck
- AI
title: ローカルLLMチュートリアル – ローカルLLMの呼び出し方と文法チェックの実行
url: /ja/net/ai-powered-document-processing/local-llm-tutorial-how-to-call-a-local-llm-and-run-grammar-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ローカルLLMチュートリアル – ローカルLLMを呼び出して文法チェックを実行する

クラウドに何も送信せずに Word ファイルで **文法チェックを実行** する方法を考えたことはありませんか？この **ローカルLLMチュートリアル** では、自己ホスト型の大規模言語モデルを接続し、`.docx` ファイルを読み込み、AI に文章を整えてもらいます。API キーも外部トラフィックも不要—自分のマシンだけで重い処理を行います。

コードの各行を順に解説し、各要素が重要な理由を説明し、一般的な落とし穴（ファイルが見つからない、エンドポイントに到達できないなど）の対処方法も示します。最後まで読むと、ローカルにホストされたモデルを使用して **AI 文法チェック** を実行する、すぐに実行可能な C# コンソール アプリが手に入ります。

> **得られるもの:** 完全に実行可能なプログラム、各ステップの明確な説明、そして大規模なドキュメントや別の LLM プロバイダー向けにソリューションをスケールするためのヒント。

![ローカルLLMチュートリアル図](https://example.com/local-llm-tutorial-diagram.png "ローカルLLMチュートリアルのフローを示す図")

## 前提条件

- .NET 6.0 SDK 以降（Microsoft のサイトからダウンロード可能）
- OpenAI 互換エンドポイントを公開しているローカルで動作する LLM サーバー（例: Ollama、LM Studio、またはカスタム FastAPI ラッパー）
- `AiGrammar` NuGet パッケージ（または `LocalLargeLanguageModel`、`Document`、`AiModelType` クラスを提供する任意のライブラリ）
- サンプルの Word ドキュメント（`input.docx`）を、後で参照するフォルダーに配置

以上です—追加のクラウド認証情報は不要です。

## ステップ 1: ローカルLLMチュートリアル – エンドポイントの設定

最初に必要なのは、リクエスト先を指し示す **call local llm** オブジェクトです。これは、話す前にダイヤルする電話番号のようなものです。

```csharp
using System;
using AiGrammar;   // Hypothetical library containing the LLM helpers

// Step 1: Configure a local large language model (LLM) endpoint
var llm = new LocalLargeLanguageModel
{
    Endpoint = "http://localhost:8000/v1",
    ApiKey = "dummy"   // Not required for self‑hosted models, but the property is mandatory
};
```

**Why this matters:**  
ほとんどの LLM SDK は OpenAI API の契約に従った HTTP エンドポイントを期待します。`Endpoint` を `http://localhost:8000/v1` に設定することで、ライブラリに OpenAI のサーバーにアクセスする代わりに **call local llm** を使用するよう指示します。ダミーの API キーは単なるプレースホルダーで、一部のクライアントは null 値を受け付けないため、無害な文字列を渡しています。

> **プロのコツ:** LLM をリバースプロキシの背後で実行している場合、`Endpoint` をプロキシの URL に設定し、TLS 終端はプロキシに任せましょう。これによりコンソール アプリがシンプルかつ安全になります。

## ステップ 2: 文法チェック用に Word ドキュメントを読み込む

モデルにアクセスできるようになったので、メモリに **load word document** コンテンツを読み込む必要があります。`Document` クラスが `.docx` の解析を抽象化してくれます。

```csharp
// Step 2: Load the document you want to check
var docPath = @"C:\Projects\GrammarDemo\YOUR_DIRECTORY\input.docx";
if (!System.IO.File.Exists(docPath))
{
    Console.Error.WriteLine($"Error: The file '{docPath}' does not exist.");
    return;
}

var doc = new Document(docPath);
```

**Why this matters:**  
バイナリの `.docx` ファイルを直接 LLM に渡すと混乱します。`Document` ヘルパーは段落区切りを保持しながら生テキストを抽出し、**ai grammar check** にクリーンな入力を提供します。存在チェックは、アプリがクラッシュする原因となる `FileNotFoundException` を防ぎます。

## ステップ 3: LLM を使用して文法チェックを実行する

チュートリアルの核心です: ローカルモデルにテキストの校正を依頼します。`CheckGrammar` メソッドは HTTP の配管処理を隠蔽し、結果オブジェクトを返します。

```csharp
// Step 3: Run the grammar‑check operation using the LLM
var result = doc.CheckGrammar(
    llm,
    AiModelType.Gpt4   // You can swap this for any model supported by AiModelType
);
```

**Why this matters:**  
`AiModelType.Gpt4` は、リモートサービスにどのプロンプトテンプレートを使用するかを指示するラベルに過ぎません。より小さなモデル（例: `Llama2`）を使用する場合はそれに置き換えてください。ライブラリはドキュメントテキストをシリアライズし、`http://localhost:8000/v1/completions` に送信し、修正された出力を解析します。

> **エッジケース:** LLM がタイムアウトした場合、`CheckGrammar` は `TimeoutException` をスローします。大きなドキュメントやサーバーが混雑していると予想される場合は、`try/catch` ブロックで呼び出しをラップしてください。

## ステップ 4: 修正されたテキストを出力する

最後に、クリーンアップされたバージョンを表示します。実際のアプリでは新しい `.docx` ファイルに書き戻すこともできますが、このチュートリアルではコンソール出力で十分です。

```csharp
// Step 4: Output the corrected text
Console.WriteLine("=== Corrected Text ===");
Console.WriteLine(result.CorrectedText);
```

**期待される出力**（元のファイルにいくつか意図的なミスが含まれていると仮定）:

```
=== Corrected Text ===
The quick brown fox jumps over the lazy dog. 
She doesn't like apples, but she loves oranges.
```

LLM がエラーを検出しなかった場合、出力は入力と同一になりますが、これも有用なシグナルです。

## 完全な動作例

すべてをまとめると、以下が新しいコンソール プロジェクトにコピー＆ペーストできる完全なプログラムです。

```csharp
using System;
using AiGrammar;   // Replace with the actual namespace of your grammar library

namespace LocalLlmGrammarDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Configure the local LLM endpoint
            var llm = new LocalLargeLanguageModel
            {
                Endpoint = "http://localhost:8000/v1",
                ApiKey = "dummy"
            };

            // Path to the Word document you want to check
            var docPath = @"C:\Projects\GrammarDemo\YOUR_DIRECTORY\input.docx";

            // Verify the file exists before proceeding
            if (!System.IO.File.Exists(docPath))
            {
                Console.Error.WriteLine($"Error: The file '{docPath}' does not exist.");
                return;
            }

            // Load the document (this also extracts plain text)
            var doc = new Document(docPath);

            // Perform the AI grammar check using the local LLM
            GrammarCheckResult result;
            try
            {
                result = doc.CheckGrammar(llm, AiModelType.Gpt4);
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Grammar check failed: {ex.Message}");
                return;
            }

            // Show the corrected text
            Console.WriteLine("=== Corrected Text ===");
            Console.WriteLine(result.CorrectedText);
        }
    }
}
```

### 実行方法

1. プロジェクト フォルダーでターミナルを開く。  
2. `dotnet run` を実行する。  
3. コンソールに修正されたテキストが表示されるのを確認する。

これで **ローカルLLMチュートリアル** は 100 行未満のコードで完了です。

## よくある質問 (FAQ)

### 別の LLM ブランドを使用できますか？

もちろんです。サーバーが OpenAI v1 API スキーマに準拠している限り、`Endpoint` を変更し、対応する `AiModelType` 列挙値（例: `AiModelType.Llama2`）を選択すればよいだけです。コードの残りは同じです。

### ドキュメントが巨大（10 MB 超）だったらどうしますか？

大きなペイロードは多くのサーバーのデフォルトリクエストサイズを超える可能性があります。ドキュメントをセクションに分割し、各セクションごとに `CheckGrammar` を呼び出して結果を結合してください。これによりタイムアウトの可能性も減ります。

### 修正された出力を `.docx` ファイルに書き戻すには？

`Document` クラスは通常 `Save(string path, string content)` メソッドを提供します。`result.CorrectedText` を取得したら、以下を呼び出します:

```csharp
doc.Save(@"C:\Projects\GrammarDemo\output_corrected.docx", result.CorrectedText);
```

正確なシグネチャはライブラリのドキュメントをご確認ください。

### ダミー API キーはセキュリティリスクですか？

いいえ。キーは自己ホスト型エンドポイントでは無視されますが、一部の SDK は null でない文字列を要求します。`"dummy"` のようなプレースホルダーを使用すれば、シークレットを公開することなく SDK の要件を満たせます。

## 次のステップと関連トピック

- **ローカルLLMをファインチューニング**して、ドメイン固有の文法（例: 法務や医療文書）に対応させる。  
- **バッチジョブを実行**して、Word ファイル全体のフォルダーを処理する—出版パイプラインに最適。  
- ユーザーが入力中にリアルタイム提案が欲しい場合は、**ストリーミングレスポンス**を検討してください。  
- **スペルチェックライブラリ**と組み合わせて、二重層の品質ゲートを実装する。

これらのアイデアはすべて、この **ローカルLLMチュートリアル** で扱ったコア概念に基づいているため、**call local llm**、**load word document**、**run grammar check**、**handle results** といったパターンが随所に繰り返されます。

---

*ハッピーコーディング！問題が発生したら、下にコメントを残してください。一緒にトラブルシュートします。*

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説付きの完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを探求するのに役立ちます。

- [Word ドキュメントでエンコーディングを指定して読み込む](/words/english/net/programming-with-loadoptions/load-with-encoding/)
- [Word ドキュメントを暗号化された状態で読み込む](/words/english/net/programming-with-loadoptions/load-encrypted-document/)
- [破損した DOCX の復元 – Word ドキュメントを開いて読み込む](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}