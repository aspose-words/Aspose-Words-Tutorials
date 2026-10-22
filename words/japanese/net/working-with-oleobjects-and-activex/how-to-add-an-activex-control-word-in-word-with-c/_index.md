---
category: general
date: 2026-09-30
description: C# を使用して Word 文書に ActiveX コントロールを追加します。ActiveX ボタンの挿入方法、コマンド ボタンの追加方法、そしてクリック可能にする方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- activex control word
- how to insert activex
- how to add command button
- insert activex button
- add clickable button word
language: ja
lastmod: 2026-09-30
og_description: C#でWord文書にActiveXコントロールを追加する。ActiveXボタンを挿入し、コマンドボタンを追加してクリックできるようにする完全ガイド。
og_image_alt: Word document displaying an inserted ActiveX command button
og_title: Word文書にActiveXコントロールを追加する – ステップバイステップC#ガイド
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Add an ActiveX control word to a Word document using C#. Learn how
    to insert an ActiveX button, add a command button, and make it clickable.
  headline: How to add an ActiveX control word in Word with C#
  type: TechArticle
tags:
- ActiveX
- Aspose.Words
- C#
- Word automation
title: C#でWordにActiveXコントロールを追加する方法
url: /ja/net/working-with-oleobjects-and-activex/how-to-add-an-activex-control-word-in-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で Word に ActiveX コントロール ワードを追加する方法

Microsoft Word ファイルに **ActiveX コントロール ワード** を埋め込む必要がある場合、このガイドではその手順を詳しく解説します。クリック可能なボタンを挿入し、ドキュメントを保存し、最新の Aspose.Words for .NET で動作する完全な実行可能サンプルをご覧いただけます。

ActiveX コントロール ワードを追加すると、インタラクティブなフォームやカスタム ダイアログ、ネイティブ Word コントロールのように動作するシンプルな UI 要素を作成できます。ユーザー操作が必要な契約テンプレートや「実行」ボタンが必要なレポートなど、以下の手順ですべてカバーしています。

## 前提条件

開始する前に以下を用意してください。

* .NET 6.0 SDK 以降（コードは .NET Framework 4.8 でも動作します）
* Visual Studio 2022（または C# をサポートする任意の IDE）
* Aspose.Words for .NET がインストール済み（`dotnet add package Aspose.Words`）
* C# と Word 文書構造の基本的な理解

> **プロのコツ:** `InsertForms2OleControl` メソッドはレガシーな「Forms 2.0」コントロール、すなわち Word がフォーム フィールドで使用する ActiveX コントロールにのみ対応しています。新しい Office バージョンを対象にしても、デスクトップ クライアントでは正しく表示されます。

## 手順 1: プロジェクトの設定と名前空間のインポート

新しいコンソール プロジェクトを作成し、必要な `using` 文を追加します。これによりコンパイラが `Document`、`DocumentBuilder`、`OleControlType` クラスを認識できるようになります。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

`Aspose.Words` 名前空間は Word 処理用のハイレベル API を提供し、`Aspose.Words.Drawing` には ActiveX コントロールの種類を指定するための `OleControlType` 列挙体が含まれています。

## 手順 2: ソースの Word 文書を読み込む

変更したい Word ファイルから開始します。以下のコードは、指定したフォルダーにある `input.docx` を読み込みます。

```csharp
// Step 2: Load the Word document you want to modify
string inputPath = @"C:\Docs\input.docx";
Document doc = new Document(inputPath);
```

ファイルが存在しない場合、Aspose.Words は `FileNotFoundException` をスローします。エラーハンドリングが必要な場合は `try/catch` ブロックでラップしてください。

## 手順 3: DocumentBuilder を作成して文書を編集

`DocumentBuilder` はテキスト、画像、コントロールの挿入を担当する主要クラスです。次に挿入する要素の位置を指すカーソルを保持します。

```csharp
// Step 3: Create a DocumentBuilder to work with the document's content
DocumentBuilder builder = new DocumentBuilder(doc);
```

デフォルトでは、ビルダーのカーソルは最初のセクションの先頭に配置されています。`MoveToDocumentEnd()` や `MoveToParagraph(index)` などのメソッドで、ボタンを別の場所に配置することも可能です。

## 手順 4: ActiveX CommandButton コントロールを挿入

チュートリアルの核心部分です。**ActiveX コントロール ワード** をクリック可能なボタンとして挿入します。`InsertForms2OleControl` メソッドは、コントロールの種類とキャプション（または名前）の 2 つの引数を受け取ります。

```csharp
// Step 4: Insert an ActiveX CommandButton control with the caption "ClickMe"
builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");
```

* **なぜ `OleControlType.CommandButton` を使用するのか？**  
  Word にクラシックな Forms 2.0 コマンド ボタンを作成させ、キャプションを表示し、後でマクロや VBA スクリプトに接続できるようにします。

* **キャプションは何をするのか？**  
  文字列 `"ClickMe"` がボタンに表示されるテキストになります。UI に合わせて任意の文字列に変更できます。

### 特定の位置にボタンを挿入する

特定の段落の後にボタンが必要な場合は、まずビルダーを移動させます。

```csharp
builder.MoveToParagraph(2); // moves to the third paragraph (zero‑based index)
builder.InsertParagraph(); // optional: add a blank line before the button
builder.InsertForms2OleControl(OleControlType.CommandButton, "Submit");
```

## 手順 5: 変更後の文書を保存

コントロールを挿入したら、変更を新しいファイル（または元のファイルを上書き）に保存します。

```csharp
// Step 5: Save the modified document
string outputPath = @"C:\Docs\output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

デスクトップ版 Word で `output.docx` を開くと、**ClickMe**（または使用したキャプションに応じて **Submit**）というラベルの付いたボタンが表示されます。デザイン モードでボタンをクリックしてもデフォルトでは何も起こりません。後で Word の「開発」タブからマクロを割り当てることができます。

## 完全な実行可能サンプル

以下は、ワークフロー全体を示す自己完結型プログラムです。新しいコンソール アプリの `Program.cs` に貼り付けて実行してください。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXControlWordDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\Docs\input.docx";
            string outputPath = @"C:\Docs\output.docx";

            // 1️⃣ Load the source document
            Document doc = new Document(inputPath);

            // 2️⃣ Create a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Optional: move to the end of the document
            builder.MoveToDocumentEnd();
            builder.Writeln(); // add a blank line before the button

            // 3️⃣ Insert the ActiveX CommandButton (the core of the activex control word)
            builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");

            // 4️⃣ Save the result
            doc.Save(outputPath);
            Console.WriteLine($"Successfully saved the document with an ActiveX button to: {outputPath}");
        }
    }
}
```

### 期待される出力

* コンソールに成功メッセージと出力パスが表示されます。
* `output.docx` を開くと、ビルダーが挿入した位置に **ClickMe** ボタンが表示されます。
* ボタンは選択、サイズ変更、または Word の **Developer → Design Mode** からマクロを割り当てることが可能です。

## よくある質問とエッジケースの対処

| 質問 | 回答 |
|----------|--------|
| **ヘッダー/フッターに ActiveX ボタンを挿入するには？** | `builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` でヘッダー/フッターに移動してから `InsertForms2OleControl` を呼び出します。 |
| **ボタンではなくチェックボックスが必要な場合は？** | `OleControlType.CheckBox` を使用し、キャプションに `"Agree"` などを指定します。 |
| **Word Online でもボタンは動作しますか？** | いいえ。Word Online はレガシーな Forms 2.0 ActiveX コントロールをサポートしていません。デスクトップ クライアントでのみ表示されます。 |
| **プログラムからボタンのサイズを設定できますか？** | 挿入後に `builder.CurrentParagraph.Runs[0].GetShape()` で取得した `Shape` オブジェクトの `Width`／`Height` を調整します。 |
| **コードからマクロを割り当てる方法はありますか？** | Aspose.Words ではマクロ編集機能は提供されていません。Word で手動でマクロを付与するか、Office Interop API を使用してください。 |

## 本番環境での使用時のポイント

* **ハードコーディングされたパスは避ける** – `Path.Combine` と設定ファイルを活用してください。
* **`Document` の破棄** – 大きなファイルを扱う場合は `using` ステートメントでラップし、メモリを速やかに解放します。
* **出力の検証** – `doc.GetChildNodes(NodeType.Shape, true)` を走査し、`OleControl` タイプのシェイプが存在するかプログラムで確認します。
* **セキュリティに関する注意** – ActiveX コントロールはクライアント側でコードを実行できるため、信頼できるユーザーにのみ配布し、デジタル署名の導入も検討してください。

## 結論

C# を使用して Word 文書に **ActiveX コントロール ワード** を追加する方法が理解できたはずです。文書を読み込み、`DocumentBuilder` を作成し、`InsertForms2OleControl` でコマンド ボタンを挿入し、ファイルを保存することで、インタラクティブな Word フォームの自動生成が可能になります。`OleControlType` の他の値を試したり、ヘッダーやテーブルにコントロールを配置したり、マクロと組み合わせてリッチなユーザー体験を実現してください。

---

*次のステップ*: 他のタイプの **ActiveX** コントロールの挿入方法を探求し、VBA で **コマンド ボタン** のイベント ハンドラを追加する方法を学び、クロスプラットフォーム互換性のための **ActiveX ボタン** のベスト プラクティスを確認しましょう。


## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を応用した関連トピックを扱っています。各リソースには、ステップバイステップの解説と完全なコード例が含まれており、API の追加機能を習得したり、プロジェクトで代替実装を検討したりするのに役立ちます。

- [Embedding OLE Objects and ActiveX Controls in Word Documents](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}