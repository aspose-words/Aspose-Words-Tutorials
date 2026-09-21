---
category: general
date: 2026-09-21
description: C# を使用してドキュメントテンプレートを生成し、Word テンプレートにデータを入力し、DOCX ファイル内のプレースホルダーを置換する方法をステップバイステップで学ぶガイド。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- generate document template
- populate word template
- how to replace placeholder
- fill docx template
- replace text docx
language: ja
lastmod: 2026-09-21
og_description: C#でWordテンプレートにデータを埋め込み、プレースホルダーを置換し、完成したDOCXファイルを保存して文書テンプレートを生成します。この完全ガイドに従ってください。
og_image_alt: Screenshot of a C# program generating and filling a DOCX template
og_title: C#でドキュメントテンプレートを生成 – DOCXファイルにデータを埋め込む
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to generate document template, populate word template and
    replace placeholders in a DOCX file using C# – step‑by‑step guide.
  headline: How to generate document template and fill it with data in C#
  type: TechArticle
tags:
- C#
- DOCX
- template processing
title: C#でドキュメントテンプレートを生成し、データで埋める方法
url: /ja/net/find-and-replace-text/how-to-generate-document-template-and-fill-it-with-data-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# でドキュメントテンプレートを生成し、データで埋める方法

If you need to **generate document template** files that can be reused for invoices, contracts, or reports, this guide shows you exactly how. You’ll learn to **populate word template** placeholders, replace them with real values, and finally **fill docx template** files programmatically.

再利用可能な **document template** ファイルを請求書、契約書、レポートなどで生成する必要がある場合、このガイドで具体的な手順を示します。**populate word template** のプレースホルダーを学び、実際の値に置き換え、最終的に **fill docx template** ファイルをプログラムで作成する方法を学びます。

Creating a reusable template eliminates manual copy‑pasting and ensures consistency across all generated documents. The steps below work with any `.docx` file that contains simple placeholder tokens such as `{{Name}}`.

再利用可能なテンプレートを作成することで、手動でのコピー＆ペーストを排除し、生成されるすべてのドキュメントで一貫性を保つことができます。以下の手順は、`{{Name}}` のようなシンプルなプレースホルダートークンを含む任意の `.docx` ファイルで機能します。

## 前提条件

* .NET 6.0 SDK 以降がインストールされていること  
* Visual Studio 2022（またはお好みの IDE）  
* **Aspose.Words for .NET** NuGet パッケージ – 例で使用されている `Document` クラスを提供します  

以下のコマンドでパッケージを追加できます：

```bash
dotnet add package Aspose.Words
```

## 手順 1: Word テンプレートの準備

Create a Word document (`Template.docx`) that contains placeholders where dynamic data should appear. A common convention is double‑curly braces:

動的データが入る場所にプレースホルダーを含む Word ドキュメント（`Template.docx`）を作成します。一般的な慣例として二重波かっこが使用されます：

```
Dear {{Name}},

Your order #{{OrderId}} has been shipped on {{ShipDate}}.
```

Save the file in a folder you can reference from code, for example `C:\Docs\Template.docx`.

コードから参照できるフォルダーにファイルを保存します。例: `C:\Docs\Template.docx`。

## 手順 2: テンプレートドキュメントの読み込み

The first programmatic action is to load the template into memory. The `Document` constructor reads the file and builds an object model you can manipulate.

最初のプログラム上の操作はテンプレートをメモリに読み込むことです。`Document` コンストラクタはファイルを読み取り、操作可能なオブジェクトモデルを構築します。

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        // Load the template document from disk
        string templatePath = @"C:\Docs\Template.docx";
        Document doc = new Document(templatePath);
```

**Why this matters:** Loading the file creates a clean copy each time, so the original template remains untouched for future runs.

**Why this matters:** ファイルを読み込むたびにクリーンなコピーが作成されるため、元のテンプレートは将来の実行でも変更されません。

## 手順 3: プレースホルダーを実際のデータに置き換える

Aspose.Words provides a simple `Range.Replace` method that scans the document for a specific string and substitutes it. Wrap the call in a helper method to keep the main flow tidy.

Aspose.Words は、特定の文字列をスキャンして置換するシンプルな `Range.Replace` メソッドを提供します。呼び出しをヘルパーメソッドでラップして、メインフローをすっきり保ちます。

```csharp
        // Helper to replace a single placeholder
        void ReplacePlaceholder(string placeholder, string value)
        {
            // The placeholder includes the curly braces exactly as they appear in the template
            doc.Range.Replace(placeholder, value, new FindReplaceOptions());
        }

        // Populate the template with real values
        ReplacePlaceholder("{{Name}}", "John Doe");
        ReplacePlaceholder("{{OrderId}}", "A12345");
        ReplacePlaceholder("{{ShipDate}}", DateTime.Today.ToString("MMMM d, yyyy"));
```

**How it works:** `Range.Replace` walks through every paragraph, table cell, header, and footer, ensuring that all occurrences of the token are updated. This is the most reliable way to **how to replace placeholder** text in a DOCX file.

**How it works:** `Range.Replace` はすべての段落、テーブルセル、ヘッダー、フッターを走査し、トークンのすべての出現箇所が更新されることを保証します。これは DOCX ファイル内の **how to replace placeholder** テキストを置換する最も信頼できる方法です。

### 複数出現とトークン欠如の処理

* プレースホルダーが複数回出現する場合、`Replace` はすべてのインスタンスを自動的に更新します。  
* プレースホルダーが存在しない場合、メソッドは何もしません—例外はスローされません。  
* 大規模なドキュメントでは、すべての置換が完了するまで `doc.UpdateFields()` を無効にすることでパフォーマンスを向上させることができます。

## 手順 4: 埋め込まれたドキュメントの保存

Once all placeholders are replaced, write the result to a new file. Keeping the output separate preserves the original template for future runs.

すべてのプレースホルダーが置換されたら、結果を新しいファイルに書き出します。出力を別に保つことで、元のテンプレートは将来の実行でも保持されます。

```csharp
        // Save the filled document to a new file
        string outputPath = @"C:\Docs\FilledTemplate.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Result:** `FilledTemplate.docx` now contains the personalized content:

**Result:** `FilledTemplate.docx` にはパーソナライズされたコンテンツが含まれます：

```
Dear John Doe,

Your order #A12345 has been shipped on September 21, 2026.
```

## 手順 5: 出力の検証（オプション）

If you want to programmatically confirm that the replacements succeeded, you can read the saved file back and search for the expected values:

置換が成功したことをプログラム上で確認したい場合、保存したファイルを再度読み込み、期待する値を検索できます：

```csharp
        Document verifyDoc = new Document(outputPath);
        bool nameReplaced = verifyDoc.Range.Text.Contains("John Doe");
        Console.WriteLine($"Name replacement successful: {nameReplaced}");
```

Running the verification step prints `true` when the placeholder was correctly replaced.

検証ステップを実行すると、プレースホルダーが正しく置換された場合に `true` が出力されます。

## よくある落とし穴とベストプラクティスのヒント

| Issue | Why it happens | Recommended fix |
|-------|----------------|-----------------|
| **プレースホルダーに余分なスペースが含まれる** | `"{{ Name }}"` は `"{{Name}}"` と一致しません。 | プレースホルダーのトークンから空白を除くか、置換前に両側をトリムしてください。 |
| **Word が隠し書式を追加する** | Word はプレースホルダーを複数のランに分割して保存することがあり、`Replace` が検出できなくなることがあります。 | `Document.Range.Replace` を使用し、`FindReplaceOptions` の `MatchCase = false` と `FindWholeWordsOnly = false` を設定してください。 |
| **大きなドキュメントで遅延が発生する** | トークンを1つずつ置換すると、毎回全文書スキャンが実行されます。 | 保存前に各トークンに対して `Range.Replace` を呼び出し、1回のパスでまとめて置換してください。 |
| **読み取り専用フォルダーへの保存** | `doc.Save` が `UnauthorizedAccessException` をスローします。 | 対象ディレクトリに書き込み権限があることを確認するか、ユーザーが書き込み可能なパス（例: `%TEMP%`）を選択してください。 |

## 完全な動作例

Below is the complete, self‑contained program that you can copy, paste, and run.

以下は、コピーして貼り付け、実行できる完全な自己完結型プログラムです。

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        // Paths – adjust to your environment
        string templatePath = @"C:\Docs\Template.docx";
        string outputPath   = @"C:\Docs\FilledTemplate.docx";

        // 1️⃣ Load the template document
        Document doc = new Document(templatePath);

        // 2️⃣ Replace placeholders
        void Replace(string placeholder, string value) =>
            doc.Range.Replace(placeholder, value, new FindReplaceOptions());

        Replace("{{Name}}", "John Doe");
        Replace("{{OrderId}}", "A12345");
        Replace("{{ShipDate}}", DateTime.Today.ToString("MMMM d, yyyy"));

        // 3️⃣ Save the filled document
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");

        // 4️⃣ (Optional) Verify replacement
        Document verify = new Document(outputPath);
        Console.WriteLine($"Verification – name found: {verify.Range.Text.Contains("John Doe")}");
    }
}
```

**期待されるコンソール出力**

```
Document saved to C:\Docs\FilledTemplate.docx
Verification – name found: True
```

Open `FilledTemplate.docx` in Microsoft Word to see the personalized text.

Microsoft Word で `FilledTemplate.docx` を開くと、パーソナライズされたテキストが表示されます。

## 結論

You now know how to **generate document template**, **populate word template**, and **fill docx template** files by **how to replace placeholder** tokens with real data. The approach works for any number of placeholders and scales to large documents when you follow the best‑practice tips.

これで、**document template** を **generate** し、**word template** に **populate** し、**docx template** ファイルを **how to replace placeholder** トークンで実データに置換して **fill** する方法が分かりました。このアプローチはプレースホルダーの数に関係なく機能し、ベストプラクティスのヒントに従えば大規模なドキュメントにもスケールします。

### 次は何をすべきか？

* **Dynamic tables:** コレクションに基づいて行を挿入するには `DocumentBuilder` を使用します。  
* **Conditional sections:** `IF` フィールドでテンプレートの一部を非表示または表示します。  
* **PDF export:** `doc.Save("output.pdf")` を呼び出して、埋め込まれたドキュメントの PDF バージョンを作成します。  

Experiment with these variations to build a full‑featured document generation engine for invoices, contracts, or any repeatable report.

これらのバリエーションを試して、請求書、契約書、または任意の繰り返しレポート用のフル機能のドキュメント生成エンジンを構築してください。

---

## 次に学ぶべきことは？

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step‑by‑step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Word ドキュメント - テキストの検索と置換](/words/english/net/find-and-replace-text/)
- [Word ドキュメントの生成](/words/english/java/word-processing/generate-word-document/)
- [破損した DOCX の復元 – Word ドキュメントのオープンとロード](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}