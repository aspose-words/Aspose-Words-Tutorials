---
category: general
date: 2026-09-21
description: DocumentBuilder を使用してプログラムで Word 文書を作成し、Word 文書を保存するボタン、コマンド ボタン（Word）を挿入する方法、およびコマンド
  ボタンのキャプションを設定する方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- save word document button
- insert command button word
- set command button caption
- how to use documentbuilder
language: ja
lastmod: 2026-09-21
og_description: Aspose.Words を使用してプログラムで Word 文書を作成します。Word 文書を保存するボタンの作成方法、コマンドボタンの挿入方法、コマンドボタンのキャプション設定方法、そしてインタラクティブ
  フォーム用に DocumentBuilder を使用する方法を学びましょう。
og_image_alt: Screenshot of a Word file that contains an inserted CommandButton created
  programmatically
og_title: プログラムでWord文書を作成し、ボタンを追加する
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically and learn how to save word document
    button, insert command button word, and set command button caption using DocumentBuilder.
  headline: Create word document programmatically and insert a button
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: プログラムでWord文書を作成し、ボタンを挿入する
url: /ja/java/using-document-elements/create-word-document-programmatically-and-insert-a-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# プログラムで Word 文書を作成し、ボタンを挿入する

If you need to **create word document programmatically**, Aspose.Words provides a fluent API that lets you add interactive controls such as a CommandButton. This tutorial also explains **how to use DocumentBuilder**, how to **save word document button**, and how to **set command button caption** so the button appears exactly as you expect inside the .docx file.

プログラムで **Word 文書を作成** する必要がある場合、Aspose.Words は CommandButton などのインタラクティブ コントロールを追加できる流暢な API を提供します。このチュートリアルでは **DocumentBuilder の使用方法**、**Word 文書のボタンを保存する方法**、そして **コマンドボタンのキャプションを設定する方法** についても説明し、.docx ファイル内でボタンが期待通りに表示されるようにします。

You will learn how to:

* Initialize a blank document with `Document`. => `Document` を使用して空の文書を初期化する。
* Work with `DocumentBuilder` to edit the document. => `DocumentBuilder` を使用して文書を編集する。
* Insert a **CommandButton** (`insert command button word`). => **CommandButton** を挿入する（`insert command button word`）。
* Set the button’s name and visible caption (`set command button caption`). => ボタンの名前と表示キャプションを設定する（`set command button caption`）。
* Persist the result to disk (`save word document button`). => 結果をディスクに保存する（`save word document button`）。

The steps are written for .NET developers using C# and the latest Aspose.Words for .NET (v24.10). No additional NuGet packages are required beyond Aspose.Words.

手順は C# を使用する .NET 開発者向けに、最新の Aspose.Words for .NET（v24.10）を前提としています。Aspose.Words 以外に追加の NuGet パッケージは必要ありません。

---

## 開始前に必要なもの

| 前提条件 | 理由 |
|--------------|--------|
| Visual Studio 2022（または任意の C# IDE） | サンプルコードをコンパイルして実行するためです。 |
| .NET 6.0 SDK 以降 | サンプルの実行環境を提供します。 |
| Aspose.Words for .NET（v24.10 以降） | プログラムで Word 文書を作成し、フォームコントロールを操作できるライブラリです。 |
| C# と OOP の基本的な知識 | コードの流れを理解するために必要です。 |

You can install Aspose.Words via NuGet:

```bash
dotnet add package Aspose.Words
```

---

## プログラムで Word 文書を作成する

The first step is to instantiate an empty `Document`. This object represents the entire Word file in memory.

最初のステップは空の `Document` をインスタンス化することです。このオブジェクトはメモリ上の Word ファイル全体を表します。

```csharp
// Step 1: Create a new blank document
Document doc = new Document();
```

Creating the document programmatically gives you a clean canvas on which you can add paragraphs, tables, or interactive controls.  

プログラムで文書を作成すると、段落やテーブル、インタラクティブ コントロールを追加できるクリーンなキャンバスが得られます。  

---

## DocumentBuilder の使い方

`DocumentBuilder` is the primary class for editing a `Document`. It provides methods to insert text, images, and form fields. In this tutorial we use it to place a CommandButton.

`DocumentBuilder` は `Document` を編集するための主要クラスです。テキスト、画像、フォームフィールドを挿入するメソッドを提供します。このチュートリアルでは CommandButton を配置するために使用します。

```csharp
// Step 2: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

The builder maintains an internal cursor that points to the current insertion location. By default it starts at the beginning of the first section, which is ideal for our example.

ビルダーは現在の挿入位置を指す内部カーソルを保持しています。デフォルトでは最初のセクションの先頭から開始するため、今回の例に最適です。

---

## コマンドボタン（Word）を挿入する

Aspose.Words treats a CommandButton as an ActiveX control. The `InsertForms2OleControl` method creates a generic OLE control that we then configure as a button.

Aspose.Words は CommandButton を ActiveX コントロールとして扱います。`InsertForms2OleControl` メソッドは汎用 OLE コントロールを作成し、これをボタンとして構成します。

```csharp
// Step 3: Insert an ActiveX Forms2OleControl (a CommandButton)
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

At this point the control exists in the document but has no visual representation until we define its type.

この時点でコントロールは文書内に存在しますが、タイプを定義するまで視覚的な表現はありません。

---

## コマンドボタンのキャプションを設定する

Now we tell the OLE control that it should behave like a CommandButton and give it a friendly label.

ここで OLE コントロールに CommandButton として動作させ、わかりやすいラベルを付けます。

```csharp
// Step 4: Define the control as a CommandButton
commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

// Step 5: Set a unique name for the button (used for identification)
commandButton.SetName("btnSubmit");

// Step 6: Set the visible caption that appears on the button
commandButton.SetCaption("Submit");
```

Setting the **command button caption** is essential because Word displays this text on the button surface. If you omit `SetCaption`, the button will appear with a generic label.

**コマンドボタンのキャプション** を設定することは重要です。Word はこのテキストをボタンの表面に表示します。`SetCaption` を省略すると、ボタンは汎用ラベルで表示されます。

---

## Word 文書のボタンを保存する

Finally, persist the document to disk. The `Save` method writes the entire Word package, including the newly inserted button, to a .docx file.

最後に、文書をディスクに永続化します。`Save` メソッドは新しく挿入したボタンを含む Word パッケージ全体を .docx ファイルに書き込みます。

```csharp
// Step 7: Save the document containing the CommandButton
doc.Save("YOUR_DIRECTORY/CommandButton.docx");
```

The file `CommandButton.docx` now contains a fully functional button labeled **Submit**. When the user opens the file in Microsoft Word and clicks the button, the default action (which you can later bind via VBA) will be triggered.

`CommandButton.docx` ファイルには **Submit** とラベル付けされた完全に機能するボタンが含まれます。ユーザーが Microsoft Word でファイルを開きボタンをクリックすると、デフォルトのアクション（後で VBA でバインド可能）が実行されます。

---

## 完全な動作例

Below is the complete program that you can copy, paste, and run. It demonstrates the entire workflow from document creation to saving the button.

以下はコピーして貼り付け、実行できる完全なプログラムです。文書作成からボタン保存までの全工程を示しています。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder (how to use DocumentBuilder)
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a CommandButton (insert command button word)
        Forms2OleControl commandButton = builder.InsertForms2OleControl();

        // 4. Define the control type as CommandButton
        commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

        // 5. Give the button a unique name (optional but useful)
        commandButton.SetName("btnSubmit");

        // 6. Set the visible caption (set command button caption)
        commandButton.SetCaption("Submit");

        // 7. Save the document (save word document button)
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**期待される結果**

* 指定したパスに `CommandButton.docx` という名前のファイルが作成されます。
* Microsoft Word でファイルを開くと、1 ページ目に **Submit** ボタンが 1 つ表示されます。
* ボタンは選択、サイズ変更、または Word の **Developer** タブからマクロにリンクできます。

---

## よくある質問とエッジケースの対処

| 質問 | 回答 |
|----------|--------|
| *複数のボタンが必要な場合はどうすればよいですか？* | ステップ 3〜6 を異なる名前とキャプションで繰り返します。各ボタンは一意の `SetName` 値を持つ必要があります。 |
| *ボタンのサイズを設定できますか？* | はい。コントロールを挿入した後、`OleFormat` オブジェクトを介して `Width` と `Height` プロパティを変更できます。 |
| *すべての Word バージョンでボタンは動作しますか？* | ActiveX コントロールは Windows のデスクトップ版 Word でサポートされています。Word Online や macOS では表示されません。 |
| *クリックハンドラを追加するには？* | ボタンの名前（`btnSubmit`）を参照する VBA コードを書く必要があります。VBA マクロは `doc.VbaProject` を使用して埋め込めます。 |
| *テーブルセル内にボタンを挿入するにはどうすればよいですか？* | `InsertForms2OleControl` を呼び出す前に、ビルダーのカーソルを目的のセル（`builder.MoveTo(cell.FirstParagraph)`）に移動します。 |

---

## プロのコツ

* **プロのコツ:** 常に `SetName` で意味のある名前を設定してください。VBA の自動化が簡素化され、デバッグが容易になります。
* **注意点:** `SetControlType` の呼び出しを忘れないでください。この呼び出しがないと OLE オブジェクトはクリック可能なボタンではなく、汎用のプレースホルダーとして表示されます。
* **パフォーマンスのコツ:** ループで多数の文書を生成する場合、単一の `DocumentBuilder` インスタンスを再利用し、各挿入前に `builder.MoveToDocumentEnd()` を呼び出して不要なカーソルリセットを防ぎます。

---

## 次のステップ

Now that you know how to **create word document programmatically**, **insert command button word**, **set command button caption**, and **save word document button**, you can explore more advanced scenarios:

これで **プログラムで Word 文書を作成**、**コマンドボタン（Word）を挿入**、**コマンドボタンのキャプションを設定**、そして **Word 文書のボタンを保存** する方法が分かりましたので、より高度なシナリオを検討できます:

* ユーザー入力用に **TextFormField** コントロールを追加する。
* ボタンと **MacroButton** フィールドを組み合わせて VBA を直接実行する。
* **DocumentBuilder.InsertImage** を使用してボタン上にアイコンを配置する。
* ASP.NET と統合して Word フォームを生成する

## 次に学ぶべきことは？

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

以下のチュートリアルは本ガイドで示した手法を基にした、密接に関連するトピックを取り上げています。各リソースには完全な動作コード例とステップバイステップの解説が含まれ、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [新規 Word 文書の作成](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Aspose.Words for .NET を使用した Word 文書の作成](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Aspose.Words を使用した Word 文書へのインライン画像挿入](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}