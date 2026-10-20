---
category: general
date: 2026-10-20
description: C# を使用して Word 文書にプレースホルダー テキストを設定します。Aspose.Words for .NET を使って、コントロールの追加とプレースホルダーの設定をすばやく行う方法をご紹介します。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- how to add control
- how to set placeholder
- generate word c#
language: ja
lastmod: 2026-10-20
og_description: C#でWord文書にプレースホルダー文字列を設定する。このチュートリアルでは、コントロールの追加、プレースホルダーの設定、そしてWordファイルをプログラムで生成する方法を示します。
og_image_alt: Screenshot of a Word document showing placeholder text created with
  C# code
og_title: C#でWord文書にプレースホルダー文字列を設定する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Set placeholder text in a Word document using C#. Learn how to add
    control and set placeholder quickly with Aspose.Words for .NET.
  headline: Set placeholder text in a Word document using C#
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, and .NET
      6+. The same code runs unchanged.
    question: Does this work with .NET Core?
  - answer: Use `sdt.SetText("Default value")` after creating the SDT. The placeholder
      disappears once a value is set.
    question: Can I set a default value in addition to the placeholder?
  - answer: 'Load the document, locate the SDT by its `Title` (`doc.GetChildNodes(NodeType.StructuredDocumentTag,
      true)`) and read `sdt.GetText()`. ## Conclusion You now know how to **set placeholder
      text** in a Word document using C#. By creating a plain‑text `StructuredDocumentTag`,
      assigning a title and place'
    question: What if I need to retrieve the entered value later?
  type: FAQPage
tags:
- C#
- Aspose.Words
- Word automation
- Content control
title: C# を使用して Word 文書にプレースホルダー テキストを設定する
url: /ja/net/programming-with-sdt/set-placeholder-text-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# を使用して Word ドキュメントにプレースホルダー テキストを設定する

C# で生成する Microsoft Word ファイルに **プレースホルダー テキストを設定** する必要がある場合、このガイドで正確な手順をご紹介します。コンテンツ コントロールを追加し、プレースホルダーを定義し、ドキュメントを保存する、Aspose.Words for .NET を使用した簡潔なエンドツーエンド ソリューションをご覧いただけます。

多くの開発者は、Word ドキュメントに **コントロールを追加する方法** や、Word を手動で開かずに **プレースホルダーを設定する方法** を疑問に思っています。このチュートリアルではそれらの質問に答えるとともに、ユーザー入力の準備ができた **Word C# を生成** するクリーンな方法も示します。

## 本チュートリアルで達成できること

* プログラムで空の Word ドキュメントを作成する。
* プレーンテキストの Structured Document Tag (SDT) を挿入する。これはコンテンツ コントロールの技術的名称です。
* SDT に意味のあるタイトルとプレースホルダー テキストを割り当てる。
* 生成された `.docx` ファイルをディスクに保存する。

追加のツールは、Aspose.Words ライブラリと .NET 6（またはそれ以降）の開発環境があれば不要です。

## 前提条件

* .NET 6 SDK 以上がインストールされていること。  
* Visual Studio 2022（または .NET をサポートする任意の IDE）。  
* Aspose.Words for .NET NuGet パッケージ（`Install-Package Aspose.Words`）。  

> **プロのコツ:** テストだけの場合は Aspose.Words の無料評価版を使用してください。透かしが追加されますが、ライセンス版と同様に動作します。

## 手順 1: プロジェクトの設定と名前空間のインポート

新しいコンソール プロジェクトを作成し、必要な `using` ディレクティブを追加します。これにより、コアの Aspose.Words クラスとマークアップ名前空間がスコープに入ります。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // The complete solution starts here.
        }
    }
}
```

*この手順が重要な理由:* `Aspose.Words.Markup` をインポートすると、`StructuredDocumentTag`、`SdtType`、`MarkupLevel` にアクセスでき、**コントロールを追加** し、**プレースホルダーを設定** するために必要なオブジェクトが利用可能になります。

## 手順 2: 空のドキュメントと DocumentBuilder の作成

`Document` は Word ファイル全体を表し、`DocumentBuilder` は要素を挿入するための便利なカーソルを提供します。

```csharp
// Step 2: Initialize a new empty document.
Document doc = new Document();

// DocumentBuilder starts at the beginning of the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*この手順が重要な理由:* クリーンなドキュメントから開始することで、設定したプレースホルダーが意図した場所に正確に表示され、既存のコンテンツに干渉しません。

## 手順 3: コンテンツ コントロール（Structured Document Tag）の作成

ここではプレーンテキストの SDT を作成し、タイトルを付け、コントロールが空のときにユーザーに表示されるプレースホルダー テキストを設定します。

```csharp
// Step 3: Build a plain‑text Structured Document Tag (SDT).
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,                     // Parent document
    SdtType.PlainText,       // Control type – plain text box
    MarkupLevel.Inline);     // Inline placement (behaves like a word)

sdt.Title = "CustomerName";                 // Logical name for the control
sdt.PlaceholderName = "Enter name here";    // Text shown when empty
```

*この手順が重要な理由:* `Title` プロパティにより、後でコントロールを参照できます（例: データ バインディング用）。`PlaceholderName` は、エンド ユーザーを案内するために表示したい **プレースホルダー テキストを設定** するものです。

## 手順 4: 現在のカーソル位置にコントロールを挿入

`DocumentBuilder` を使用して、ビルダーが現在位置している場所に SDT をドキュメントへ挿入します。

```csharp
// Step 4: Insert the SDT into the document.
builder.InsertNode(sdt);
```

*この手順が重要な理由:* ノードを挿入すると、コントロールがドキュメントの DOM に結び付けられます。複数のプレースホルダーを追加する必要がある場合は、ビルダーのカーソルを移動してこの手順を繰り返すことができます。

## 手順 5: ドキュメントの保存

最後に、ドキュメントをディスクに書き込みます。`YOUR_DIRECTORY` を実際のパスに置き換えてください。

```csharp
// Step 5: Save the .docx file.
string outputPath = @"C:\Temp\SDT.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

`SDT.docx` を Microsoft Word で開くと、**Enter name here** と表示された灰色のインライン テキスト ボックスが見えます。ボックス内をクリックするとプレースホルダーが消え、ユーザーは顧客名を入力できるようになります。

### 期待される出力

| ファイルの場所 | コンテンツ プレビュー |
|---------------|-----------------|
| `C:\Temp\SDT.docx` | プレーンテキスト コンテンツ コントロール（タイトルは *CustomerName*）内のインライン プレースホルダー **Enter name here**。 |

## エッジケースとバリエーション

| 状況 | 推奨される調整 |
|-----------|------------------------|
| **複数のプレースホルダー** | `Title` と `PlaceholderName` の異なる `StructuredDocumentTag` オブジェクトを追加で作成し、必要な場所にそれぞれ挿入します。 |
| **リッチテキスト プレースホルダー** | プレースホルダー内で書式設定を可能にするため、`PlainText` の代わりに `SdtType.RichText` を使用します。 |
| **ブロックレベル コントロール** | `MarkupLevel.Inline` を `MarkupLevel.Block` に変更すると、コントロールが段落全体のように動作します。 |
| **プレースホルダーが表示されない** | Word のドキュメント表示設定でコンテンツ コントロールが非表示になっていないことを確認してください（`File → Options → Advanced → Show content controls`）。 |
| **ストリームへの保存** | ディスクに書き込む代わりに HTTP 経由でファイルを送信する必要がある場合は、`doc.Save(stream, SaveFormat.Docx)` を呼び出します。 |

## 完全な実行可能サンプル

以下は、コピーして貼り付け、実行できる完全なプログラムです。上記のすべての手順が単一の `Main` メソッドに含まれています。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Position a builder at the start of the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Define a plain‑text content control (SDT) with placeholder text.
            StructuredDocumentTag sdt = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Inline);

            sdt.Title = "CustomerName";                 // Logical identifier
            sdt.PlaceholderName = "Enter name here";    // The placeholder you see in Word

            // 4️⃣ Insert the SDT into the document.
            builder.InsertNode(sdt);

            // 5️⃣ Save the document to disk.
            string outputPath = @"C:\Temp\SDT.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document successfully saved to {outputPath}");
        }
    }
}
```

プログラムを実行し、生成されたファイルを開くと、ユーザー入力の準備ができたプレースホルダー テキストが表示されます。

## よくある質問と回答

**Q: .NET Core でも動作しますか？**  
A: はい。Aspose.Words for .NET は .NET Core、.NET 5、.NET 6+ と互換性があり、同じコードがそのまま動作します。

**Q: プレースホルダーに加えてデフォルト値を設定できますか？**  
A: SDT を作成した後に `sdt.SetText("Default value")` を使用します。値が設定されるとプレースホルダーは消えます。

**Q: 後で入力された値を取得するにはどうすればよいですか？**  
A: ドキュメントをロードし、`Title` で SDT を特定（`doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`）して、`sdt.GetText()` を読み取ります。

## 結論

C# を使用して Word ドキュメントに **プレースホルダー テキストを設定** する方法が分かりました。プレーンテキストの `StructuredDocumentTag` を作成し、タイトルとプレースホルダーを割り当て、`DocumentBuilder` で挿入し、ファイルを保存することで、**コントロールを追加** し、**Word C# を生成** することができます。  

ここからは以下を検討できます:

* リッチテキストやドロップダウン リスト コントロールの追加（`SdtType.RichText`、`SdtType.DropDownList`）。  
* データベースから複数のプレースホルダーを埋め込む。  
* 生成した `.docx` を Aspose.Words で PDF に変換する。

アプリケーションの要件に合わせて、さまざまなコントロールタイプやプレースホルダーのスタイルを試してみてください。コーディングを楽しんでください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Set Placeholder Text in Aspose.Words – Complete C# Guide](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [Create word document programmatically – add content control and placeholder](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [How to Add Content Control and Create Word Document with Aspose – Complete](/words/english/net/programming-with-sdt/how-to-add-content-control-and-create-word-document-with-asp/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}