---
category: general
date: 2026-09-18
description: C# を使用して空白の Word 文書を作成し、プレースホルダー テキストを設定してから docx として保存します。プレーンテキスト コントロールの挿入方法とプレースホルダー名の追加方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set placeholder text
- save document as docx
- insert plain text control
- add placeholder name
language: ja
lastmod: 2026-09-18
og_description: C# を使用して空白の Word 文書を作成し、プレースホルダー テキストを設定、プレーンテキスト コントロールを挿入、プレースホルダー名を追加して、docx
  として保存します。
og_image_alt: Screenshot of a Word document showing a plain‑text content control with
  placeholder text
og_title: プレースホルダー テキストで空白の Word 文書を作成 – C# ガイド
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  headline: Create blank Word document and insert a plain‑text control
  type: TechArticle
- description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  name: Create blank Word document and insert a plain‑text control
  steps:
  - name: An empty Word file (the **blank Word document** you created)
    text: An empty Word file (the **blank Word document** you created)
  - name: A plain‑text content control (the **insert plain text control** step)
    text: A plain‑text content control (the **insert plain text control** step)
  - name: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
    text: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
  - name: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
    text: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
  - name: A line of regular text after the control, demonstrating that normal content
      can follow
    text: A line of regular text after the control, demonstrating that normal content
      can follow
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 空白のWord文書を作成し、プレーンテキストコントロールを挿入する
url: /ja/java/using-document-elements/create-blank-word-document-and-insert-a-plain-text-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 空白のWord文書を作成し、プレーンテキストコントロールを挿入する

プログラムで **空白のWord文書を作成** する必要がある場合、このガイドではC#を使用してその方法を示します。**プレーンテキストコントロールの挿入**、**プレースホルダーテキストの設定**、**プレースホルダー名の追加**、そして最終的に **docxとして文書を保存** する方法を学びます。手順はすべて自己完結しているので、コードを任意の.NETプロジェクトにコピーしてすぐに実行できます。

Wordファイルを扱う際は、クリーンな開始点が必要になることが多く、ユーザーが入力するコントロールがすでに含まれた空の文書が求められます。このチュートリアルの最後までに、便利なプレースホルダー付きのプレーンテキストコンテンツコントロールを含み、その後に通常のコンテンツが続く `.docx` ファイルが作成されます。

## 前提条件

- .NET 6.0 以降（コードは .NET Framework 4.6+ でも動作します）
- **Aspose.Words for .NET** ライブラリへの参照（NuGet `Install-Package Aspose.Words` で入手可能）
- C# コンソールアプリケーションの基本的な知識
- `doc.save(...)` で指定する出力フォルダーへの書き込み権限

## 作成するもの

最終的な文書（`SDT.docx`）には以下が含まれます：

1. 空のWordファイル（作成した **blank Word document**）
2. プレーンテキストコンテンツコントロール（**insert plain text control** 手順）
3. ユーザーが入力するまでコントロール内に表示されるプレースホルダーテキスト（**set placeholder text** 手順）
4. 後でプログラムからアクセスできるプレースホルダー名（**add placeholder name** 手順）
5. コントロールの後に続く通常テキストの行で、通常のコンテンツが続くことを示します

## ステップ 1: 空白のWord文書を作成する

最初の操作は空の `Document` オブジェクトをインスタンス化することです。このオブジェクトはメモリ上の完全に新しい **blank Word document** を表します。

```csharp
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

// Step 1: Create a new blank document
Document doc = new Document();
```

*Why this matters:* 空の `Document` は追加するすべての要素を完全に制御でき、後で挿入するコンテンツコントロールに隠れたスタイルやセクションが干渉しないことを保証します。

## ステップ 2: DocumentBuilder を初期化する

`DocumentBuilder` は `Document` に書き込むためのヘルパークラスです。現在のカーソル位置を追跡し、さまざまなWordオブジェクトを挿入するメソッドを提供します。

```csharp
// Step 2: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this matters:* `DocumentBuilder` を使用すると、ビルダーが正確な挿入位置を把握しているため、**plain‑text control** の追加が簡素化されます。

## ステップ 3: プレーンテキストコントロールを挿入する

ここで **plain‑text content control**（構造化文書タグ、またはSDTとも呼ばれます）を追加します。コントロールタイプ `StructuredDocumentTagType.PLAIN_TEXT` は、Wordにコンテンツをリッチフォーマットではなくプレーンテキストとして扱うよう指示します。

```csharp
// Step 3: Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");
```

*Why this matters:* `InsertStructuredDocumentTag` メソッドはコントロールを作成し、参照（`sdt`）を返します。この参照を使ってプレースホルダーテキストやカスタム名を追加設定できます。

## ステップ 4: プレースホルダーテキストを設定し、プレースホルダー名を追加する

プレースホルダーテキストは、ユーザーに何を入力すべきか視覚的なヒントを提供します。**add placeholder name** 手順では、後で `doc.GetChildNodes` などの API で問い合わせ可能なプログラム上の識別子を割り当てます。

```csharp
// Step 4a: Set a placeholder text that appears when the SDT is empty
sdt.SetPlaceholderName("Enter text…");

// Step 4b: Add a placeholder name (tag ID) for later retrieval
sdt.Tag = "MyTag";
```

*Why this matters:* `SetPlaceholderName` はコンテンツコントロール内に表示されるグレーのヒントテキストを制御します。`Tag` を設定する（**add placeholder name** のアクション）ことで、ファイル全体を走査せずにドキュメントツリー内のコントロールを特定できます。

## ステップ 5: コントロールの後に通常のコンテンツを追加する

コントロールの後でも文書が通常通り続くことを示すため、シンプルなテキスト行を書き込みます。

```csharp
// Step 5: Add regular content after the SDT
builder.Writeln("After the tag.");
```

## ステップ 6: docxとして文書を保存する

最後に、メモリ上の文書をディスクに保存します。これが **save document as docx** 操作で、Microsoft Wordで開けるファイルを生成します。

```csharp
// Step 6: Save the document as a .docx file
string outputPath = @"YOUR_DIRECTORY/SDT.docx";
doc.Save(outputPath);
```

*Why this matters:* `.docx` 形式を使用することで、最新のWord、Google Docs、その他のOffice互換ツールとの最大互換性が確保されます。

## 完全な実行可能サンプル

以下はコンソールアプリプロジェクトにコピーできる完全なプログラムです。`YOUR_DIRECTORY` を実際のフォルダパスに置き換えてください。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

namespace WordSdtExample
{
    class Program
    {
        static void Main()
        {
            // Create a new blank Word document
            Document doc = new Document();

            // Initialize a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");

            // Set a placeholder text that appears when the SDT is empty
            sdt.SetPlaceholderName("Enter text…");

            // Add a placeholder name (tag) for later retrieval
            sdt.Tag = "MyTag";

            // Add regular content after the SDT
            builder.Writeln("After the tag.");

            // Save the document as a .docx file
            string outputPath = @"C:\Temp\SDT.docx"; // change to your folder
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### 期待される結果

- Wordで `SDT.docx` を開くと、内部に **Enter text…** というテキストが表示された空の灰色ボックスが表示されます。
- このボックスはプレーンテキストコンテンツコントロールで、直接入力できます。
- ボックスの下には **After the tag.** という行が通常の段落テキストとして表示されます。

プレースホルダーが表示されない場合は、Aspose.Words の最新バージョン（v23.1 以降）を使用しているか、コンテンツコントロールに対応した Word バージョン（Word 2007 以降）で文書を開いているか確認してください。

## 一般的なバリエーションとエッジケース

| Scenario | How to adapt the code |
|----------|-----------------------|
| **Multiple placeholders** | `InsertStructuredDocumentTag` を再度呼び出し、別のタグIDとプレースホルダー名を指定します。 |
| **Rich‑text control** | `PlainText` の代わりに `StructuredDocumentTagType.RichText` を使用します。 |
| **Setting default text** | 挿入後に `sdt.Text = "Default value";` を設定します。このテキストは文書読み込み時にプレースホルダーを置き換えます。 |
| **Saving to a stream** | `doc.Save(outputPath);` を `doc.Save(stream, SaveFormat.Docx);` に置き換えて、HTTPでファイルを送信します。 |
| **Changing placeholder color** | `sdt.PlaceholderTextColor = System.Drawing.Color.Gray;` を使用します（`using System.Drawing` が必要）。 |

## プロのコツ

- **Reuse the tag ID**: タグ（`MyTag`）を文書間で一貫させておくと、後で `doc.Range.Replace` や `StructuredDocumentTagCollection` を使ってデータの自動入力が可能になります。
- **Avoid hard‑coded paths**: ポータブルな出力先として `Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), "SDT.docx")` を使用します。
- **Performance**: 数千件の文書を生成する必要がある場合、SDT が既に含まれた単一の `Document` テンプレートを作成し、各イテレーションで `doc.Clone()` して複製します。

## 結論

これで、Aspose.Words for .NET を使用して **blank Word document** を作成し、**plain text control** を挿入し、**placeholder text** を設定し、**placeholder name** を追加し、**docxとして文書を保存** する方法が分かりました。このパターンは、フォーム入力済みのWordテンプレート、レポートの自動生成、またはユーザーが編集可能なプレースホルダーを必要とするあらゆるソリューションの基礎となります。

他のコントロールタイプを試したり、複数のプレースホルダーを組み合わせたり、このコードをWeb APIに組み込んで生成された `.docx` ファイルを直接呼び出し元に返すことも自由に行ってください。次のステップとして、**コンテンツコントロールにプログラムでデータを入力** する方法や、Aspose.Words の組み込み変換機能を使って **生成したWordファイルをPDFに変換** する方法を探ってみましょう。コーディングを楽しんでください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法に基づく密接に関連したトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加のAPI機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Word文書にテキスト入力フォームフィールドを挿入する](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Aspose.Words を使用して表付きの Word 文書を作成する](/words/english/net/add-content-using-document-builder/build-table/)
- [Aspose.Words を使用してヘッダーとフッター付きの Word 文書を作成する](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}