---
category: general
date: 2026-11-18
description: Google AI翻訳を使ってdocxをフランス語に翻訳し、文書全体を翻訳し、翻訳された文書をたった3つのステップで保存する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate docx to french
- google ai translation
- translate entire document
- save translated document
- how to translate docx
language: ja
lastmod: 2026-11-18
og_description: Google AI翻訳を使用して、docxをフランス語に即座に翻訳します。このガイドに従って、ドキュメント全体を翻訳し、翻訳済みドキュメントを簡単に保存しましょう。
og_image_alt: Screenshot showing a DOCX file translated to French using Google AI
og_title: Google AIでdocxをフランス語に翻訳する – クイックガイド
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Learn how to translate docx to French with Google AI translation, translate
    entire document, and save translated document in just three steps.
  headline: How to translate docx to French using Google AI
  type: TechArticle
- description: Learn how to translate docx to French with Google AI translation, translate
    entire document, and save translated document in just three steps.
  name: How to translate docx to French using Google AI
  steps:
  - name: 'Create a new console project:'
    text: 'Create a new console project:'
  - name: 'Add the NuGet packages that the tutorial relies on:'
    text: 'Add the NuGet packages that the tutorial relies on:'
  - name: '(Optional) If you prefer a higher‑level wrapper, you can also install `GroupDocs.Translator`:'
    text: '(Optional) If you prefer a higher‑level wrapper, you can also install `GroupDocs.Translator`:'
  type: HowTo
tags:
- C#
- Google AI
- Document translation
- Localization
title: Google AI を使用して docx をフランス語に翻訳する方法
url: /ja/net/ai-powered-document-processing/how-to-translate-docx-to-french-using-google-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Google AI を使用して docx をフランス語に翻訳する方法

docx をフランス語に翻訳する必要がある場合、Google AI 翻訳を使用すると、C# の数行のコードだけでドキュメント全体を翻訳できます。このチュートリアルでは、DOCX ファイルの翻訳方法、ドキュメント全体のコンテンツの翻訳方法、そして翻訳されたドキュメントを確実に保存する方法を正確に示します。

Google Cloud Translation クライアントの設定方法、Word ファイルの読み込み方法、各段落を翻訳するために API を呼び出す方法、そして最終的に **save translated document** 手順を書く方法を学びます。外部スクリプトや手動でのコピー＆ペーストは不要で、すべて .NET アプリケーション内で実行されます。

## 必要なもの

* .NET 6.0 SDK またはそれ以降がインストールされていること  
* **Cloud Translation API** が有効化された Google Cloud プロジェクト  
* サービス アカウントの JSON キーファイル（Google Cloud コンソールからダウンロード）  
* Visual Studio 2022（またはお好みの C# IDE）  

これらの前提条件により、**google ai translation** の呼び出しが成功し、Open XML SDK を使用して DOCX ファイルの読み書きが可能になります。

## プロジェクトの設定と必要な SDK のインストール

1. 新しいコンソール プロジェクトを作成する:

   ```bash
   dotnet new console -n DocxFrenchTranslator
   cd DocxFrenchTranslator
   ```

2. チュートリアルが依存する NuGet パッケージを追加する:

   ```bash
   dotnet add package Google.Cloud.Translate.V3
   dotnet add package DocumentFormat.OpenXml
   ```

   *`Google.Cloud.Translate.V3`* は **google ai translation** クライアントを提供し、*`DocumentFormat.OpenXml`* は Microsoft Office をインストールせずに DOCX ファイルを操作できるようにします。

3. （オプション）より高レベルのラッパーを好む場合は、`GroupDocs.Translator` もインストールできます:

   ```bash
   dotnet add package GroupDocs.Translator
   ```

   以下のコード例はどちらのアプローチでも動作します。透明性のために Open XML バージョンを完全に示しています。

## ソース DOCX ファイルの読み込み

最初の実装ステップは、翻訳したい Word ドキュメントを読み込むことです。Open XML SDK を使用すると、各段落のテキストをリストに抽出できます。

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using DocumentFormat.OpenXml.Packaging;
using DocumentFormat.OpenXml.Wordprocessing;

namespace DocxFrenchTranslator
{
    /// <summary>
    /// Reads all paragraph texts from a DOCX file.
    /// </summary>
    public static class DocxReader
    {
        public static List<string> GetParagraphs(string path)
        {
            var paragraphs = new List<string>();

            using (WordprocessingDocument wordDoc = WordprocessingDocument.Open(path, false))
            {
                Body body = wordDoc.MainDocumentPart.Document.Body;
                foreach (Paragraph para in body.Elements<Paragraph>())
                {
                    paragraphs.Add(para.InnerText);
                }
            }

            return paragraphs;
        }
    }
}
```

**この重要性:** ファイルを一度だけ読み込み、テキストをメモリに保持することで、段落ごとに単一の API 呼び出しで **translate entire document** コンテンツを翻訳でき、繰り返しのファイル I/O を回避できます。

## Google AI 翻訳の実行

元の段落が取得できたら、Translation API を呼び出して各文字列を英語（または任意のソース言語）からフランス語に変換します。`null` を渡すと、クライアントが自動的にソース言語を検出します。

```csharp
using Google.Cloud.Translate.V3;
using System.Collections.Generic;
using System.Threading.Tasks;

namespace DocxFrenchTranslator
{
    /// <summary>
    /// Handles translation using Google Cloud Translation (v3).
    /// </summary>
    public static class Translator
    {
        private static readonly TranslationServiceClient client;

        static Translator()
        {
            // The GOOGLE_APPLICATION_CREDENTIALS environment variable should point to your JSON key.
            client = TranslationServiceClient.Create();
        }

        /// <summary>
        /// Translates a list of strings to French.
        /// </summary>
        public static async Task<List<string>> TranslateToFrenchAsync(List<string> texts)
        {
            var request = new TranslateTextRequest
            {
                Parent = $"projects/{client.ProjectId}/locations/global",
                TargetLanguageCode = "fr",
                // SourceLanguageCode can be omitted for auto‑detection.
            };

            // Add all texts to the request.
            request.Contents.AddRange(texts);

            // Execute the translation.
            TranslateTextResponse response = await client.TranslateTextAsync(request);

            var translated = new List<string>();
            foreach (Translation translation in response.Translations)
            {
                translated.Add(translation.TranslatedText);
            }

            return translated;
        }
    }
}
```

**この重要性:** バッチリクエストで **google ai translation** を使用すると、段落ごとの単一呼び出しループに比べてレイテンシとコストが削減されます。このメソッドは、プログラムで **how to translate docx** を実演しています。

## 翻訳されたテキストで新しい DOCX を作成する

フランス語の文字列を受け取ったら、それらを新しい DOCX ファイルに書き戻します。以下のヘルパークラスは、翻訳された段落から新しいドキュメントを構築します。

```csharp
using DocumentFormat.OpenXml.Packaging;
using DocumentFormat.OpenXml.Wordprocessing;

namespace DocxFrenchTranslator
{
    /// <summary>
    /// Writes a list of paragraphs to a new DOCX file.
    /// </summary>
    public static class DocxWriter
    {
        public static void Write(string outputPath, List<string> frenchParagraphs)
        {
            // Ensure the directory exists.
            Directory.CreateDirectory(Path.GetDirectoryName(outputPath)!);

            // Create a new document.
            using (WordprocessingDocument wordDoc = WordprocessingDocument.Create(outputPath, DocumentFormat.OpenXml.WordprocessingDocumentType.Document))
            {
                MainDocumentPart mainPart = wordDoc.AddMainDocumentPart();
                mainPart.Document = new Document();
                Body body = mainPart.Document.AppendChild(new Body());

                foreach (string paraText in frenchParagraphs)
                {
                    Paragraph para = new Paragraph(new Run(new Text(paraText)));
                    body.AppendChild(para);
                }

                mainPart.Document.Save();
            }
        }
    }
}
```

## すべてを組み合わせる – 完全なプログラム

以下は、前述のスニペットを結び付けた完全で実行可能なコンソール アプリケーションです。**translate docx to french** を実演し、**google ai translation** を実行し、最後に **save translated document** を行います。

```csharp
using System;
using System.IO;
using System.Threading.Tasks;

namespace DocxFrenchTranslator
{
    class Program
    {
        static async Task Main(string[] args)
        {
            // ------------------------------------------------------------------
            // 1️⃣ Load the source document
            // ------------------------------------------------------------------
            string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
            if (!File.Exists(inputPath))
            {
                Console.WriteLine($"Input file not found: {inputPath}");
                return;
            }

            var originalParagraphs = DocxReader.GetParagraphs(inputPath);
            Console.WriteLine($"Loaded {originalParagraphs.Count} paragraphs from input.docx.");

            // ------------------------------------------------------------------
            // 2️⃣ Translate the entire document to French using Google AI
            // ------------------------------------------------------------------
            var frenchParagraphs = await Translator.TranslateToFrenchAsync(originalParagraphs);
            Console.WriteLine("Translation completed – document is now in French.");

            // ------------------------------------------------------------------
            // 3️⃣ Save the translated document
            // ------------------------------------------------------------------
            string outputPath = Path.Combine(Environment.CurrentDirectory, "output_fr.docx");
            DocxWriter.Write(outputPath, frenchParagraphs);
            Console.WriteLine($"Saved translated document to: {outputPath}");
        }
    }
}
```

### 期待される出力

プログラムを実行すると（`dotnet run`）、コンソールに以下のような出力が表示されます:

```
Loaded 12 paragraphs from input.docx.
Translation completed – document is now in French.
Saved translated document to: C:\Path\To\Your\Project\output_fr.docx
```

`output_fr.docx` を Word、LibreOffice、または任意のビューアで開くと、元の英語コンテンツがフランス語の翻訳に置き換わっていることが確認できます。

## docx をフランス語に翻訳する – ステップバイステップ概要

### 1. Google 資格情報を安全に設定する

* サービス アカウントの JSON ファイルを安全な場所に配置する（例:）

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説とともに完全な動作コード例が含まれており、追加の API 機能を習得し、独自のプロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Google AI を使用した C# で翻訳された Word ドキュメントの保存方法](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)
- [DOCX をフランス語に翻訳し、ドキュメント翻訳を自動化する方法](/words/english/net/ai-powered-document-processing/how-to-translate-docx-to-french-and-automate-document-transl/)
- [Aspose.Words と Google API を使用して docx をフランス語に翻訳する方法](/words/english/net/ai-powered-document-processing/translate-docx-to-french-with-aspose-words-and-google-api/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}