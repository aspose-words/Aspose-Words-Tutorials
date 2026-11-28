---
category: general
date: 2026-08-23
description: Aspose.Words AI Translator と Google プロバイダーを使用して、C# で文字列をスペイン語に翻訳します。ステップバイステップのガイドに従って、C#
  で文字列を迅速に翻訳してください。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate string to spanish
- translate string in c#
language: ja
lastmod: 2026-08-23
og_description: Aspose.Words AI を使用して C# で文字列をスペイン語に翻訳します。このチュートリアルでは、Google プロバイダーの設定方法、文字列の翻訳方法、結果の表示方法を示します。
og_image_alt: Console screenshot showing translate string to spanish output in a C#
  application
og_title: C#で文字列をスペイン語に翻訳 – 完全なコード例
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Translate string to Spanish in C# using Aspose.Words AI Translator
    and Google provider. Follow the step‑by‑step guide to translate string in C# quickly.
  headline: Translate string to Spanish in C# with Aspose.Words AI
  type: TechArticle
- description: Translate string to Spanish in C# using Aspose.Words AI Translator
    and Google provider. Follow the step‑by‑step guide to translate string in C# quickly.
  name: Translate string to Spanish in C# with Aspose.Words AI
  steps:
  - name: '**Obtain an API key** from the Google Cloud Console → APIs & Services →
      Credentials.'
    text: '**Obtain an API key** from the Google Cloud Console → APIs & Services →
      Credentials.'
  - name: '**Enable the Cloud Translation API** for your project.'
    text: '**Enable the Cloud Translation API** for your project.'
  - name: Store the key securely (environment variable, secret manager, etc.). The
      example uses a literal for clarity, but production code should avoid hard‑coding
      secrets.
    text: Store the key securely (environment variable, secret manager, etc.). The
      example uses a literal for clarity, but production code should avoid hard‑coding
      secrets.
  - name: Open a terminal in the project folder.
    text: Open a terminal in the project folder.
  - name: Execute `dotnet run`.
    text: Execute `dotnet run`.
  - name: Confirm that the console displays the Spanish phrase.
    text: Confirm that the console displays the Spanish phrase.
  type: HowTo
tags:
- Aspose.Words
- C#
- Localization
title: Aspose.Words AI を使用して C# で文字列をスペイン語に翻訳する
url: /ja/net/ai-powered-document-processing/translate-string-to-spanish-in-c-with-aspose-words-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# と Aspose.Words AI を使用した文字列のスペイン語への翻訳

.NET アプリケーションで **文字列をスペイン語に翻訳** する必要がある場合、このガイドでは具体的な手順を示します。翻訳者を作成し、Google サービスを呼び出し、スペイン語のテキストを出力する完全な実行可能サンプルが確認できます。

このチュートリアルでは、Aspose.Words AI ライブラリを使用した **C# で文字列を翻訳** も取り上げており、外部スクリプトを使用せずにローカリゼーションをコードベースに直接統合できます。

## 必要なもの

- .NET 6.0 SDK またはそれ以降（コードは .NET Core および .NET Framework でもコンパイル可能）
- 有効な Google Cloud Translation API キー
- NuGet パッケージ `Aspose.Words.AI`（`dotnet add package Aspose.Words.AI` でインストール）
- Visual Studio 2022 などのコードエディタまたは IDE

これらの前提条件により、サンプルがすぐに実行できるようになります。

## Aspose.Words AI を使用した文字列のスペイン語への翻訳

このセクションでは、Google プロバイダー用に構成された `Translator` オブジェクトを作成します。プロバイダーは Google の翻訳エンドポイントへの HTTP リクエストを処理します。

```csharp
using System;
using Aspose.Words.AI;          // Namespace for Translator
using Aspose.Words.AI.Translator; // Contains TranslationProvider and Language enums

class Program
{
    static void Main()
    {
        // Step 1: Create a translator that uses Google as the provider
        var translator = new Translator(
            provider: TranslationProvider.Google,
            apiKey: "YOUR_GOOGLE_KEY");   // Replace with your real API key

        // Step 2: Translate the source text into Spanish
        string spanishText = translator.Translate(
            "Hello world",
            Language.Spanish);

        // Step 3: Use the translated text (display it in the console)
        Console.WriteLine(spanishText);
    }
}
```

**これが機能する理由:**  
- `Translator` は HTTP 呼び出しを抽象化し、提供した API キーで認証を処理します。  
- `TranslationProvider.Google` は SDK に対し、リクエストを Google Cloud Translation にルーティングするよう指示します。  
- `Language.Spanish` は対象言語コード（`es`）を選択します。  
- `Translate` メソッドは翻訳された文字列を返し、アプリケーション内の任意の場所で使用できます。

## Google 翻訳プロバイダーの設定

1. **API キーを取得**するには、Google Cloud Console の → APIs & Services → Credentials から取得します。  
2. **Cloud Translation API を有効化**します。  
3. キーを安全に保存します（環境変数、シークレットマネージャー等）。例では分かりやすさのためにリテラルを使用していますが、本番コードではシークレットをハードコーディングしないでください。

## C# で文字列を翻訳する – 手順ごとに

| Step | Action | Reason |
|------|--------|--------|
| 1 | `TranslationProvider.Google` を使用して `Translator` をインスタンス化 | SDK を Google サービスに接続 |
| 2 | `Translate(source, Language.Spanish)` を呼び出す | ソーステキストを送信し、スペイン語の結果を受け取る |
| 3 | `Console.WriteLine` で結果を出力 | 翻訳を検証し、使用例を示す |

Running the program prints:

```
¡Hola mundo!
```

> **注:** 正確な出力は Google の翻訳モデルにより若干異なる場合があります（例: “Hola mundo” と “¡Hola mundo!”）。どちらも有効なスペイン語の表現です。

## 実行と出力の確認

1. プロジェクトフォルダーでターミナルを開きます。  
2. `dotnet run` を実行します。  
3. コンソールにスペイン語のフレーズが表示されることを確認します。

コンソールに *“401 Unauthorized”* のようなエラーが表示された場合、API キーが正しいか、プロジェクトで Cloud Translation API が有効になっているかを再確認してください。

## よくある落とし穴とベストプラクティス

- **API クォータ制限** – Google は請求アカウントごとにリクエスト上限を課しています。予期しないスロットリングを防ぐため、Cloud Console で使用量を監視してください。  
- **ネットワーク遅延** – 翻訳呼び出しはリモートの HTTP リクエストです。遅延を減らすために、頻繁に翻訳する文字列をキャッシュすることを検討してください。  
- **エンコーディングの問題** – SDK は UTF‑8 文字列を扱います。特殊文字を保持するため、ソースファイルが UTF‑8 エンコードで保存されていることを確認してください。  
- **エラーハンドリング** – `Translate` 呼び出しを try‑catch ブロックでラップし、`ApiException` を処理してフォールバックテキストを提供します。

```csharp
try
{
    string spanishText = translator.Translate("Hello world", Language.Spanish);
    Console.WriteLine(spanishText);
}
catch (ApiException ex)
{
    Console.Error.WriteLine($"Translation failed: {ex.Message}");
    // Fallback to original text
    Console.WriteLine("Hello world");
}
```

## サンプルの拡張

- **他の言語への翻訳** – `Language.Spanish` を `Language.French`、`Language.German` などに置き換えます。  
- **バッチ翻訳** – 文字列リストを処理するために、ループ内で `Translate` を呼び出します。  
- **UI への統合** – 翻訳された文字列を ASP.NET Core Razor ページ、Windows Forms、または WPF アプリケーションで使用します。

## 結論

これで、Aspose.Words AI と Google 翻訳サービスを使用して C# で **文字列をスペイン語に翻訳** する方法が分かりました。完全なソリューションは、プロバイダーの設定、翻訳呼び出し、エラーハンドリング、出力の検証を網羅しています。

ここからは、他の言語を試したり、パフォーマンス向上のために結果をキャッシュしたり、翻訳機能を大規模なローカリゼーションパイプラインに統合したりしてください。

--- 

*さらにコンテンツをローカライズしたいですか？代替のクラウドプロバイダーとして **C# で Azure Cognitive Services を使用した文字列の翻訳** に関する次のチュートリアルをご覧ください。*

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説付きの完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [文字列で置換](/words/spanish/net/find-and-replace-text/replace-with-string/)
- [文字列で置換](/words/english/net/find-and-replace-text/replace-with-string/)
- [Aspose.Words で Word 文書を作成 – ステップバイステップガイド](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}