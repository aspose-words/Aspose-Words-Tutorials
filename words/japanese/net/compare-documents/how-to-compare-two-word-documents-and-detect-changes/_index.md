---
category: general
date: 2026-09-21
description: C#で2つのWord文書（docxファイル）を比較し、Wordの変更点を検出して、比較結果を新しい文書として保存する。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- compare two word documents
- compare docx files
- compare word document versions
- save comparison result
- detect changes in word
language: ja
lastmod: 2026-09-21
og_description: Aspose.Words for .NET を使用して Word 文書を迅速に比較し、docx ファイルの比較方法を学び、Word
  の変更を検出し、比較結果を保存します。
og_image_alt: C# code snippet that compares two Word documents and saves the comparison
  result
og_title: C#で2つのWord文書を比較する – 完全ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: compare two Word documents in C# to compare docx files, detect changes
    in Word and save comparison result as a new document.
  headline: How to compare two Word documents and detect changes
  type: TechArticle
- description: compare two Word documents in C# to compare docx files, detect changes
    in Word and save comparison result as a new document.
  name: How to compare two Word documents and detect changes
  steps:
  - name: Why this step matters
    text: Aspose.Words implements a sophisticated diff algorithm that understands
      Word’s formatting, tables, footnotes, and even tracked changes. Using the library
      ensures accurate detection of modifications when you **compare word document
      versions**.
  - name: Customizing the comparison (optional)
    text: 'If you need to fine‑tune the behavior—e.g., ignore header/footer changes
      or treat case‑insensitive text as equal—you can supply a `CompareOptions` object:'
  - name: Verifying the output
    text: 'Open `ComparisonResult.docx` in Microsoft Word. You should see:'
  type: HowTo
tags:
- Word
- C#
- Aspose.Words
- Document comparison
title: 2つのWord文書を比較して変更を検出する方法
url: /ja/net/compare-documents/how-to-compare-two-word-documents-and-detect-changes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 2つのWord文書を比較して変更を検出する方法

プログラムで **2つのWord文書を比較** する必要がある場合、このガイドではC#での完全なソリューションを示します。**docxファイルを比較** し、**Wordでの変更を検出** し、**比較結果を保存** して差分をハイライトする新しいファイルを作成する方法を学びます。改訂履歴の追跡や文書レビューのワークフロー構築など、以下の手順ですべてカバーしています。

このチュートリアルでは、**Word文書バージョンを並べて比較** する方法、比較動作のカスタマイズ、ページレイアウトの違いや非表示テキストなどの一般的なエッジケースの処理方法も紹介します。最後には、明確な差分文書を生成する実行可能なプロジェクトが手に入ります。

## 前提条件

- .NET 6.0 SDK 以降（コードは .NET Core と .NET Framework でも動作します）
- Visual Studio 2022（または C# をサポートする任意の IDE）
- **Aspose.Words for .NET** NuGet パッケージ（`Document`、`Comparer`、`ComparisonResult` クラスを提供するライブラリ）
- 比較したい2つの Word ファイル、例: `Version1.docx` と `Version2.docx`

> **プロのコツ:** Aspose.Words は商用ライブラリですが、フル機能の無料トライアルが提供されています。オープンソースの代替を希望する場合は **DocX** や **Open XML SDK** を検討できますが、比較 API の機能は限定的です。

## 手順 1: Aspose.Words for .NET をインストール

ターミナルでプロジェクトフォルダーを開き、次のコマンドを実行します:

```bash
dotnet add package Aspose.Words
```

このコマンドは最新の Aspose.Words アセンブリをプロジェクトに追加し、**docx ファイルを効率的に比較** できる比較エンジンへのアクセスを提供します。

### この手順が重要な理由
Aspose.Words は Word の書式設定、表、脚注、さらには変更履歴まで理解できる高度な差分アルゴリズムを実装しています。ライブラリを使用することで、**Word文書バージョンを比較** する際に変更の正確な検出が保証されます。

## 手順 2: 最初の Word 文書をロード

```csharp
using Aspose.Words;

// Load the first version of the document
Document docVersion1 = new Document(@"C:\Docs\Version1.docx");
```

**説明:**  
`Document` は Word ファイルを表す主要オブジェクトです。`Version1.docx` をロードすることで、比較器が読み取れるメモリ内表現が作成されます。パスは絶対でも相対でも構いませんが、ファイルが存在することを確認してください。存在しない場合は `FileNotFoundException` がスローされます。

## 手順 3: 2番目の Word 文書をロード

```csharp
// Load the second version of the document
Document docVersion2 = new Document(@"C:\Docs\Version2.docx");
```

**説明:**  
`docVersion1` と `docVersion2` の両方がメモリ上にあることで、比較エンジンは各ノード（段落、表、画像など）を走査し、差分を検出できます。この手順は **2つのWord文書を比較** ワークフローに不可欠です。

## 手順 4: 文書を比較して変更を検出

```csharp
// Perform the comparison
ComparisonResult comparison = Comparer.Compare(docVersion1, docVersion2);
```

**なぜこれが機能するのか:**  
`Comparer.Compare` は `ComparisonResult` オブジェクトを返し、挿入は緑、削除は赤でマークされた新しい `Document` を含みます（デフォルトのビジュアルスタイル）。このメソッドは、追加されたテキスト、削除された段落、スタイル変更など、**Word の変更を検出** します。

### 比較のカスタマイズ（オプション）

動作を細かく調整したい場合（例: ヘッダー/フッターの変更を無視する、大小文字を区別しないテキストを同等とみなす）には、`CompareOptions` オブジェクトを渡すことができます:

```csharp
var options = new CompareOptions
{
    IgnoreFormatting = true,
    IgnoreCaseChanges = true,
    IgnoreHeadersAndFooters = false
};

ComparisonResult comparison = Comparer.Compare(docVersion1, docVersion2, options);
```

これらのオプションは、外観の書式だけが異なる **Word文書バージョンを比較** する際に便利です。

## 手順 5: 比較結果を保存

```csharp
// Save the diff document
comparison.Save(@"C:\Docs\ComparisonResult.docx");
```

**何が起こるか:**  
`Save` メソッドは生成された差分をディスクに書き込みます。出力ファイル `ComparisonResult.docx` には元の内容にインラインの改訂マークが付加され、レビューアはテキストが追加、削除、変更された正確な位置を確認できます。これにより **比較結果の保存** 要件が満たされます。

### 出力の検証

Microsoft Word で `ComparisonResult.docx` を開きます。以下が表示されるはずです:

- 挿入されたテキストは左側に挿入バーが付き、緑色でハイライトされます。
- 削除されたテキストは赤色で取り消し線が付いて表示されます。
- （有効にしている場合）すべての変更を要約する改訂ペインが表示されます。

ハイライトが表示されない場合は、2つの元文書が実際に異なるか、`CompareOptions` で改訂追跡が無効になっていないかを再確認してください。

## 一般的なエッジケースの処理

| 状況 | 推奨アプローチ |
|-----------|----------------------|
| **大容量文書（>50 MB）** | `Comparer.Compare` を `CompareOptions.DisableRevisions` と共に使用して軽量な差分を生成し、必要に応じて手動で改訂マークを追加します。 |
| **パスワード保護されたファイル** | `LoadOptions` でパスワードを指定して文書をロードします: `new Document(path, new LoadOptions { Password = "pwd" })`。 |
| **ロケールが異なる場合（例: en‑US と en‑GB）** | `CompareOptions` で `IgnoreCaseChanges` と `IgnoreLocaleDifferences` を有効にします。 |
| **画像は変わっているがテキストは変わっていない** | 画像の変更を検出するために `CompareOptions.IgnoreImages = false` を設定します。 |

これらのシナリオに対処することで、実務プロジェクトでも **2つのWord文書を比較** ソリューションが信頼性を保ちます。

## 完全な実行可能サンプル

以下は、すべての手順を組み合わせた完全なコンソールアプリケーションです。コードを新しい `.csproj` にコピーして実行してください。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Comparing;

namespace WordComparisonDemo
{
    class Program
    {
        static void Main()
        {
            // Paths to the documents you want to compare
            string path1 = @"C:\Docs\Version1.docx";
            string path2 = @"C:\Docs\Version2.docx";
            string outputPath = @"C:\Docs\ComparisonResult.docx";

            // Load both documents
            Document docVersion1 = new Document(path1);
            Document docVersion2 = new Document(path2);

            // Optional: customize comparison behavior
            var options = new CompareOptions
            {
                IgnoreFormatting = false,
                IgnoreCaseChanges = false,
                IgnoreHeadersAndFooters = false,
                IgnoreComments = true,
                IgnoreFootnotes = true
            };

            // Perform the comparison
            ComparisonResult comparison = Comparer.Compare(docVersion1, docVersion2, options);

            // Save the result
            comparison.Save(outputPath);

            Console.WriteLine($"Comparison complete. Result saved to: {outputPath}");
        }
    }
}
```

**コンソールでの期待出力:**

```
Comparison complete. Result saved to: C:\Docs\ComparisonResult.docx
```

生成された `ComparisonResult.docx` を開くと、2つの元ファイル間のすべての変更がハイライトされたビジュアル差分が表示されます。

## 次のステップと関連トピック

- **PDF へのエクスポート:** `save comparison result` を DOCX として保存した後、`doc.Save("result.pdf", SaveFormat.Pdf)` を使用して PDF に変換できます。
- **Web API での自動化:** 比較ロジックを ASP.NET Core コントローラにラップし、ユーザーが2つのファイルをアップロードして即座に差分文書を受け取れるようにします。
- **バッチ処理:** 文書ペアのフォルダーをループして、一括で比較レポートを生成します。
- **SharePoint や OneDrive との統合:** 元のバージョンと差分文書をクラウドライブラリに保存し、共同レビューを可能にします。

これらの拡張により、単純な **compare docx files** ユーティリティを超える、フル機能の文書レビューソリューションを構築できます。

---

**まとめ**

これで、Aspose.Words を使用して **2つのWord文書を比較** し、**Word の変更を検出** し、**比較結果を保存** して挿入と削除を明確にマークした新しいファイルを作成する方法が分かりました。上記の手順に従うことで、信頼性のある **Word文書バージョンの比較** が可能になり、差分をニーズに合わせてカスタマイズし、プロセスを大規模なアプリケーションに統合できます。コーディングを楽しんでください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Compare Options In Word Document](/words/english/net/compare-documents/compare-options/)
- [Compare For Equal In Word Document](/words/english/net/compare-documents/compare-for-equal/)
- [How to Load Word Documents Using Aspose.Words LoadOptions](/words/english/net/programming-with-loadoptions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}