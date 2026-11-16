---
category: general
date: 2026-11-15
description: C#でGoogleを使ってテキストを翻訳する方法を学びましょう。このチュートリアルでは、Google翻訳の例を示し、複数言語の取り扱いとベストプラクティスを解説します。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to translate text
- translate text with google
- google translate example
- google translate tutorial
- translate multiple languages
language: ja
lastmod: 2026-11-15
og_description: C#でGoogleを使用してテキストを翻訳する方法（完全なGoogle翻訳の例を使用）。このチュートリアルに従って、複数の言語を安全に翻訳しましょう。
og_image_alt: Console output showing translated text from English to French using
  Google Translate API
og_title: C#でGoogle翻訳APIを使ってテキストを翻訳する方法 – クイックチュートリアル
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to translate text with Google in C#. This tutorial shows
    a Google Translate example, handling multiple languages and best practices.
  headline: How to translate text with Google Translate API in C# – step‑by‑step guide
  type: TechArticle
- description: Learn how to translate text with Google in C#. This tutorial shows
    a Google Translate example, handling multiple languages and best practices.
  name: How to translate text with Google Translate API in C# – step‑by‑step guide
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 SDK or later (the code compiles with .NET Core and .NET Framework).
      * A Google Cloud account with the **Cloud Translation API** enabled. * Basic
      familiarity with C# and console applications.'
  - name: Handling language detection
    text: 'If you need to know the source language, the response object contains `DetectedSourceLanguage`:'
  - name: Translating large documents
    text: The API supports up to 30 KB per request. For larger texts, split the content
      into chunks, translate each chunk, and then concatenate the results. Keep sentence
      boundaries intact to avoid awkward phrasing.
  - name: Rate‑limiting and quotas
    text: Google enforces per‑minute request limits. Implement a retry policy with
      exponential back‑off to respect quota limits and avoid `429 Too Many Requests`
      errors.
  type: HowTo
- questions:
  - answer: Yes. Use the `Format` parameter (`"text"` or `"html"`) when calling `TranslateText`.
      The SDK exposes this via the `TranslateText` overload that accepts a `TranslateTextRequest`.
    question: Can I translate a whole HTML page?
  - answer: The API returns an error. Validate language codes against the list returned
      by `client.ListSupportedLanguages()` before making a request.
    question: What if a language isn’t supported?
  - answer: 'Google bills per character translated. Estimate costs using the pricing
      page and consider caching frequent translations. --- ## Conclusion You now know
      **how to translate text** in C# using the official Google Translate API. The
      tutorial covered a **Google translate example**, demonstrated **transla'
    question: Does the API charge per character?
  type: FAQPage
tags:
- Google Cloud
- C#
- Translation API
title: C#でGoogle Translate APIを使用してテキストを翻訳する方法 – ステップバイステップガイド
url: /ja/net/ai-powered-document-processing/how-to-translate-text-with-google-translate-api-in-c-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#でGoogle Translate APIを使用してテキストを翻訳する方法 – ステップバイステップガイド

.NETアプリケーションで**how to translate text**が必要な場合、Google Cloud Translation APIは信頼性が高く、言語に依存しないソリューションを提供します。このチュートリアルでは、シンプルな文字列を翻訳する**Google Translate example**、**translate multiple languages**への拡張、そしてAPIキーとエラーハンドリングのベストプラクティスを紹介します。

実行可能なC#コンソールプログラムと、**translate text with Google**の明確な理解、そしてコードを大規模プロジェクトに適用する自信が得られます。

## このチュートリアルでカバーする内容

* Google Cloudプロジェクトの設定とAPIキーの取得。  
* `Google.Cloud.Translation.V2` NuGetパッケージのインストール。  
* 公式SDKを使用して**how to translate text**を行う、クリーンで再利用可能なコードの作成。  
* 単一呼び出しで**translate multiple languages**を行うようにソリューションを拡張。  
* 一般的な落とし穴と本番向け実装のためのヒント。

### 前提条件

* .NET 6.0 SDK以上（コードは.NET Coreおよび.NET Frameworkでもコンパイル可能）。  
* **Cloud Translation API**が有効化されたGoogle Cloudアカウント。  
* C#とコンソールアプリケーションの基本的な知識。  

---

## ステップ1: Google Cloud Translationクライアントライブラリのインストール

公式クライアントライブラリはHTTP呼び出しを抽象化し、認証を自動的に処理します。

```bash
dotnet add package Google.Cloud.Translation.V2
```

このコマンドを実行すると、プロジェクトに`Google.Cloud.Translation.V2`パッケージが追加され、本ガイド全体で使用される`TranslationClient`クラスにアクセスできるようになります。

> **このステップが重要な理由** – SDKを使用することで手動でのリクエスト構築を回避し、バグを減らし、Googleの最新APIバージョンに合わせることができます。

## ステップ2: 再利用可能な翻訳ヘルパーの作成

翻訳ロジックをstaticクラスにカプセル化することで、コードの再利用性が高まり、APIキーの取り扱いが分離されます。

```csharp
using Google.Cloud.Translation.V2;
using System;

namespace GoogleTranslateDemo
{
    /// <summary>
    /// Provides simple methods to translate text using the Google Cloud Translation API.
    /// </summary>
    public static class Translator
    {
        /// <summary>
        /// Translates a single string into the specified target language.
        /// </summary>
        /// <param name="sourceText">The text you want to translate.</param>
        /// <param name="targetLanguage">ISO‑639‑1 language code (e.g., "fr" for French).</param>
        /// <param name="apiKey">Your Google Cloud API key.</param>
        /// <returns>The translated text.</returns>
        public static string Translate(string sourceText, string targetLanguage, string apiKey)
        {
            // Initialise the client with the provided API key.
            var client = TranslationClient.CreateFromApiKey(apiKey);

            // Perform the translation. The API automatically detects the source language.
            var response = client.TranslateText(sourceText, targetLanguage);
            return response.TranslatedText;
        }

        /// <summary>
        /// Translates a collection of texts into several languages at once.
        /// </summary>
        /// <param name="sourceTexts">Array of strings to translate.</param>
        /// <param name="targetLanguages">Array of ISO‑639‑1 codes (e.g., "es", "de").</param>
        /// <param name="apiKey">Your Google Cloud API key.</param>
        /// <returns>A dictionary keyed by language code containing the translated results.</returns>
        public static Dictionary<string, string[]> TranslateMultiple(string[] sourceTexts,
                                                                    string[] targetLanguages,
                                                                    string apiKey)
        {
            var client = TranslationClient.CreateFromApiKey(apiKey);
            var result = new Dictionary<string, string[]>();

            foreach (var lang in targetLanguages)
            {
                var translations = client.TranslateTexts(sourceTexts, lang);
                result[lang] = translations.Select(t => t.TranslatedText).ToArray();
            }

            return result;
        }
    }
}
```

> **辞書を返す理由** – **translate multiple languages**が必要な場合、言語コードで結果を整理することで、後続の処理がシンプルになります。

## ステップ3: ヘルパーを使用するコンソールアプリケーションの構築

以下は、単一テキストの翻訳とバッチ翻訳の両方を示す完全な`Program.cs`です。

```csharp
using System;
using GoogleTranslateDemo; // Namespace from the helper class

class Program
{
    static void Main()
    {
        // ---- Single translation (Google Translate example) ----
        string sourceText = "Hello, world!";
        string targetLanguage = "fr"; // French
        string apiKey = "YOUR_GOOGLE_API_KEY"; // Replace with your actual key

        try
        {
            string translated = Translator.Translate(sourceText, targetLanguage, apiKey);
            Console.WriteLine($"[Single] English → French: {translated}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Translation failed: {ex.Message}");
        }

        // ---- Translate multiple languages (translate multiple languages) ----
        string[] texts = { "Good morning", "How are you?" };
        string[] languages = { "es", "de", "ja" }; // Spanish, German, Japanese

        try
        {
            var batchResult = Translator.TranslateMultiple(texts, languages, apiKey);
            foreach (var kvp in batchResult)
            {
                Console.WriteLine($"\n[Batch] Language: {kvp.Key}");
                for (int i = 0; i < texts.Length; i++)
                {
                    Console.WriteLine($"  {texts[i]} → {kvp.Value[i]}");
                }
            }
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Batch translation failed: {ex.Message}");
        }
    }
}
```

**期待されるコンソール出力**

```
[Single] English → French: Bonjour le monde!

[Batch] Language: es
  Good morning → Buenos días
  How are you? → ¿Cómo estás?

[Batch] Language: de
  Good morning → Guten Morgen
  How are you? → Wie geht es Ihnen?

[Batch] Language: ja
  Good morning → おはようございます
  How are you? → お元気ですか？
```

> **try/catchブロックの理由** – ネットワークエラー、クォータ制限、または無効なAPIキーが例外を発生させます。これらを適切に処理することでユーザー体験が向上し、アプリケーションの安定性が保たれます。

## ステップ4: APIキーの保護

上記のようにAPIキーをハードコーディングすることはデモとしては許容されますが、本番環境では適切ではありません。以下の実践を行ってください：

* 環境変数(`GOOGLE_API_KEY`)にキーを保存し、実行時に読み取る：  
  ```csharp
  string apiKey = Environment.GetEnvironmentVariable("GOOGLE_API_KEY");
  ```
* Google Cloud上（App Engine、Cloud Runなど）で実行する場合は、APIキーの代わりに**Google Application Default Credentials**を使用する。  
* Google CloudコンソールでキーをTranslation APIに限定し、使用を特定のIPアドレスやリファラに制限する。

## ステップ5: 実際のシナリオ向けにソリューションを拡張

### 言語検出の処理

元の言語を知りたい場合、レスポンスオブジェクトに`DetectedSourceLanguage`が含まれます：

```csharp
var response = client.TranslateText(sourceText, targetLanguage);
Console.WriteLine($"Detected source: {response.DetectedSourceLanguage}");
```

### 大規模ドキュメントの翻訳

APIは1リクエストあたり最大30KBまでサポートしています。より大きなテキストの場合、コンテンツをチャンクに分割し、各チャンクを翻訳してから結果を結合します。文の区切りを保つことで不自然な表現を防ぎます。

### レートリミットとクォータ

Googleは1分あたりのリクエスト上限を設定しています。クォータ制限を守り、`429 Too Many Requests`エラーを回避するために、指数バックオフを伴うリトライポリシーを実装してください。

```csharp
// Example using Polly (install Polly via NuGet)
var policy = Policy
    .Handle<Google.Api.Gax.Rpc.ResourceExhaustedException>()
    .WaitAndRetryAsync(3, attempt => TimeSpan.FromSeconds(Math.Pow(2, attempt)));

await policy.ExecuteAsync(() => client.TranslateTextAsync(...));
```

---

## よくある質問とエッジケース

**Q: HTML全体のページを翻訳できますか？**  
A: はい。`TranslateText`を呼び出す際に`Format`パラメータ（`"text"`または`"html"`）を使用します。SDKでは`TranslateTextRequest`を受け取る`TranslateText`のオーバーロードでこの機能が提供されています。

**Q: サポートされていない言語がある場合はどうなりますか？**  
A: APIはエラーを返します。リクエスト前に`client.ListSupportedLanguages()`で取得できる言語コードリストと照合して検証してください。

**Q: APIは文字数ごとに課金されますか？**  
A: Googleは翻訳された文字数ごとに課金します。料金ページでコストを見積もり、頻繁に使用する翻訳はキャッシュすることを検討してください。

---

## 結論

公式Google Translate APIを使用してC#で**how to translate text**する方法が分かりました。このチュートリアルでは**Google translate example**を取り上げ、**translate multiple languages**を実演し、APIキーのセキュリティやエラーハンドリングといった本番向けのベストプラクティスを強調しました。`Translator`ヘルパーを再利用することで、任意の.NETサービス、デスクトップアプリ、マイクロサービスに翻訳機能を組み込むことができます。

**次のステップ**

- **Google Translate tutorial**を探求し、用語集やカスタムモデルなどの高度な機能を学ぶ。  
- このコードをASP.NET Coreと組み合わせて多言語Web APIを作成する。  
- CSVファイルのバッチ翻訳を試し、ローカリゼーションパイプラインを自動化する。

コーディングを楽しんで、グローバルにアクセス可能なアプリケーション構築をお楽しみください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースは、ステップバイステップの解説と完全な動作コード例を含み、追加のAPI機能を習得し、プロジェクトで代替実装アプローチを探求するのに役立ちます。

- [translate docx to french with Aspose.Words and Google API](/words/english/net/ai-powered-document-processing/translate-docx-to-french-with-aspose-words-and-google-api/)
- [How to save translated Word document in C# with Google AI](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)
- [Translate string to Spanish in C# with Aspose.Words AI](/words/english/net/ai-powered-document-processing/translate-string-to-spanish-in-c-with-aspose-words-ai/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}