---
category: general
date: 2026-08-10
description: C#でAspose.Wordsを使用して複数のWord文書を生成します。テンプレートから請求書を作成し、効率的にWordファイルをバッチ生成する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- generate multiple word documents
- create invoices from template
- batch generate word files
- Aspose.Words mail merge
- C# document automation
language: ja
lastmod: 2026-08-10
og_description: Aspose.Words を使用して複数の Word ドキュメントを生成します。このチュートリアルでは、テンプレートから請求書を作成し、C#
  で Word ファイルをバッチ生成する方法を示します。
og_image_alt: Screenshot of generate multiple word documents result
og_title: 複数のWord文書を生成する – Aspose.Words ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Generate multiple word documents with Aspose.Words in C#. Learn how
    to create invoices from template and batch generate word files efficiently.
  headline: Generate multiple word documents with Aspose.Words
  type: TechArticle
- description: Generate multiple word documents with Aspose.Words in C#. Learn how
    to create invoices from template and batch generate word files efficiently.
  name: Generate multiple word documents with Aspose.Words
  steps:
  - name: Prepare the data that will populate the merge fields
    text: The mail‑merge engine expects a collection of objects whose property names
      match the `MERGEFIELD` names in the template. In this example we use an anonymous
      type array, but you can replace it with a list of strongly‑typed DTOs.
  - name: Load the Word template that contains MERGEFIELD placeholders
    text: '```csharp // Step 2 – load template Document template = new Document("YOUR_DIRECTORY/InvoiceTemplate.docx");
      ```'
  - name: Merge the data into the template – one‑line call creates a single document
    text: '```csharp // Step 3 – perform the merge Document mergedDocument = MailMerger.Merge(template,
      invoiceData); ```'
  - name: Split the merged document into separate files and save each one
    text: '```csharp // Step 4 – split and save each invoice int invoiceNumber = 1;
      foreach (Document singleInvoice in mergedDocument.Split()) { string outputPath
      = $"YOUR_DIRECTORY/Invoice_{invoiceNumber++}.docx"; singleInvoice.Save(outputPath);
      } ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- MailMerge
- Document Automation
title: Aspose.Wordsで複数のWord文書を生成する
url: /ja/net/add-content-using-document-builder/generate-multiple-word-documents-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words を使用した複数の Word ドキュメントの生成

C# で **複数の Word ドキュメントを生成** する必要がある場合、Aspose.Words はファイル処理の定型コードを削減する簡潔な API を提供します。請求書システムを構築している場合や、個別のレターを作成する必要がある場合でも、このガイドでは **テンプレートから請求書を作成** し、**バッチで Word ファイルを生成** する方法を数行のコードで示します。

You will learn how to:

* メールマージ操作のためのデータを準備する。  
* `MERGEFIELD` プレースホルダーを含む Word テンプレートをロードする。  
* データを単一のドキュメントにマージし、個別のファイルに分割する。  
* 生成された各ファイルを一意の名前で保存する。

外部ツールは Aspose.Words for .NET ライブラリ以外必要なく、完全なコード例は .NET 6 以降で実行できます。

## 前提条件とセットアップ

開始する前に、以下が揃っていることを確認してください。

| 要件 | 理由 |
|-------------|--------|
| .NET 6 SDK (or newer) | コードは target‑typed `new` などの最新 C# 機能を使用しています。 |
| Aspose.Words for .NET NuGet package | `Document`、`MailMerger`、`Split` API を提供します。 |
| A Word template (`InvoiceTemplate.docx`) containing `MERGEFIELD` tags | **テンプレートから請求書を作成** のソースとして使用します。 |
| An IDE (Visual Studio, Rider, or VS Code) | プロジェクトのビルドとデバッグのために使用します。 |

以下のコマンドで NuGet パッケージをインストールします。

```bash
dotnet add package Aspose.Words
```

`InvoiceTemplate.docx` をコードから参照できるフォルダーに配置します。例: `YOUR_DIRECTORY`。

## メールマージで複数の Word ドキュメントを生成する方法

ソリューションの核心は 4 つの論理的ステップに分かれています。各ステップは明確なメソッド呼び出しでラップされており、コードが読みやすく保守しやすくなります。

### ステップ 1: マージフィールドに入力するデータを準備する

メールマージエンジンは、テンプレート内の `MERGEFIELD` 名とプロパティ名が一致するオブジェクトのコレクションを期待します。この例では匿名型配列を使用していますが、強く型付けされた DTO のリストに置き換えることも可能です。

```csharp
// Step 1 – data preparation
var invoiceData = new[]
{
    new { Name = "Alice", Amount = 123.45 },
    new { Name = "Bob",   Amount = 678.90 }
};
```

**なぜ重要か:**  
強く型付けされたデータソースを提供することで、各プレースホルダーが正しい値を受け取ることが保証され、多数の受取人向けに **バッチで Word ファイルを生成** する際に不可欠です。

### ステップ 2: MERGEFIELD プレースホルダーを含む Word テンプレートをロードする

```csharp
// Step 2 – load template
Document template = new Document("YOUR_DIRECTORY/InvoiceTemplate.docx");
```

**なぜ重要か:**  
`Document` クラスは Word ファイル全体をメモリ上に表します。テンプレートを一度ロードして再利用することで、後で **複数の Word ドキュメントを生成** する際の不要な I/O を回避できます。

### ステップ 3: データをテンプレートにマージ – ワンライン呼び出しで単一ドキュメントを作成

```csharp
// Step 3 – perform the merge
Document mergedDocument = MailMerger.Merge(template, invoiceData);
```

`MailMerger.Merge` はデータコレクションを反復処理し、各行ごとにテンプレートのコピーを挿入して `MERGEFIELD` の値を埋め込みます。その結果、すべての請求書が連続して含まれる単一の `Document` が生成されます。

### ステップ 4: マージされたドキュメントを個別のファイルに分割し、各ファイルを保存する

```csharp
// Step 4 – split and save each invoice
int invoiceNumber = 1;
foreach (Document singleInvoice in mergedDocument.Split())
{
    string outputPath = $"YOUR_DIRECTORY/Invoice_{invoiceNumber++}.docx";
    singleInvoice.Save(outputPath);
}
```

`Split()` 拡張メソッドはマージされたドキュメントを走査し、各データ行ごとに新しい `Document` インスタンスを返します。各 `singleInvoice` を保存することで個別のファイルが生成され、**バッチで Word ファイルを生成** ワークフローが完了します。

#### 完全に実行可能な例

以下は 4 つのステップを結びつけた完全なプログラムです。パスを調整した後、新しいコンソールプロジェクトにコピーして実行してください。

```csharp
using Aspose.Words;
using Aspose.Words.LowCode;

class Program
{
    static void Main()
    {
        // Step 1 – prepare data
        var invoiceData = new[]
        {
            new { Name = "Alice", Amount = 123.45 },
            new { Name = "Bob",   Amount = 678.90 }
        };

        // Step 2 – load the template
        Document template = new Document("YOUR_DIRECTORY/InvoiceTemplate.docx");

        // Step 3 – merge data into a single document
        Document mergedDocument = MailMerger.Merge(template, invoiceData);

        // Step 4 – split and save each invoice
        int invoiceNumber = 1;
        foreach (Document singleInvoice in mergedDocument.Split())
        {
            string outputPath = $"YOUR_DIRECTORY/Invoice_{invoiceNumber++}.docx";
            singleInvoice.Save(outputPath);
        }

        System.Console.WriteLine("Invoices generated successfully.");
    }
}
```

**期待される出力:**  
プログラムを実行すると、指定ディレクトリに `Invoice_1.docx`、`Invoice_2.docx`、… が作成されます。各ファイルには 1 人の顧客の請求書データが含まれ、マージフィールドは `invoiceData` の値に置き換えられます。

## テンプレートから請求書を作成 – よくある落とし穴の対処

**テンプレートから請求書を作成** する際に、いくつかの問題に直面することがあります。以下に回避策となる実用的なヒントを示します。

| 問題 | 解決策 |
|-------|----------|
| テンプレートのフィールド名がプロパティ名と一致しない | プロパティ名（`Name`、`Amount`）が Word ファイルの `MERGEFIELD` タグと完全に一致していることを確認してください。 |
| 大量データでメモリ使用量が高くなる | データをチャンクに分けて処理します：サブセットをマージし、分割、保存し、次のバッチの前に中間ドキュメントを破棄します。 |
| 特殊文字（例: “&”、 “<”）が文字化けする | Aspose.Words は XML 非安全文字を自動的にエスケープしますが、非 UTF‑8 ソースからロードする場合はテンプレートのエンコーディングを確認してください。 |
| カスタムファイル名が必要（例: 顧客名を含める） | `outputPath` 文字列を `$\"YOUR_DIRECTORY/Invoice_{singleInvoice.MailMergeData[\"Name\"]}.docx\"` に置き換え、分割ドキュメントからフィールド値を取得した後に使用します。 |

## バッチで Word ファイルを生成 – パフォーマンス上の考慮点

数千件のレコードに対して **バッチで Word ファイルを生成** する場合は、以下のガイドラインを念頭に置いてください：

1. **テンプレートオブジェクトを再利用する** – Step 2 で示したようにテンプレートを一度だけロードすることで、ディスク読み取りを繰り返すことを防ぎます。  
2. **中間ドキュメントを破棄する** – `foreach` ループは各 `singleInvoice.Save` 後に自動的にメモリを解放しますが、非常に大きなバッチの場合は `singleInvoice.Dispose()` を明示的に呼び出すこともできます。  
3. **保存ステップを並列化する** – 分割操作は独立した `Document` オブジェクトを生成するため、ストレージが並列 I/O に対応していれば `Parallel.ForEach` を使用してファイルを書き込むことができます。  

```csharp
using System.Threading.Tasks;

// ...

Parallel.ForEach(mergedDocument.Split(), (singleInvoice, state, index) =>
{
    string outputPath = $"YOUR_DIRECTORY/Invoice_{index + 1}.docx";
    singleInvoice.Save(outputPath);
});
```

**なぜ機能するか:**  
`Split()` は `IEnumerable<Document>` を返し、各 `Document` インスタンスが独自のメモリを所有しているため、並列に安全に列挙できます。

## 期待される結果と検証

プログラムが終了したら、生成された請求書を Microsoft Word で開きます。

* プレースホルダー `«Name»` は “Alice” または “Bob” に置き換えられます。  
* プレースホルダー `«Amount»` は、ドキュメントのデフォルト数値書式でフォーマットされた対応する数値を表示します。  
* 元のテンプレートのページレイアウト、ヘッダー、フッターは保持されます。

もしフィールドが未入力のまま残っている場合は、テンプレートの `MERGEFIELD` 名と `invoiceData` のプロパティ名を再度確認してください。

## 結論

これで Aspose.Words を使用して **複数の Word ドキュメントを生成** する方法、**テンプレートから請求書を作成** する方法、そして **バッチで Word ファイルを生成** する効率的な方法が分かりました。データの準備、テンプレートのロード、マージ、分割＆保存という 4 ステップのパターンは、最も一般的なドキュメント自動化シナリオを網羅しています。  

ここからは、テンプレートに画像、テーブル、条件ロジックを追加したり、請求書をオンデマンドで提供する Web API にワークフローを統合したりして、ソリューションを拡張できます。

---

![複数の Word ドキュメント生成のスクリーンショット](generate-multiple-word-documents.png){: .align-center alt="複数の Word ドキュメント生成結果のスクリーンショット"}

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Aspose.Words を使用した Word ドキュメントへのコンテンツの追加と前置](/words/english/net/document-sections/append-section-content/)
- [Aspose.Words for Java を使用した複数の Word ファイルの結合](/words/english/java/document-manipulation/cloning-and-combining-documents/)
- [Aspose.Words for .NET を使用した Word ドキュメントの行書式設定の適用](/words/english/net/working-with-table-styles-and-formatting/apply-row-formatting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}