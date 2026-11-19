---
category: general
date: 2026-11-18
description: 空白のWord文書を作成し、C#でActiveXボタンを挿入します。コントロールの追加方法、ボタンのキャプション設定、ファイルの保存方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- how to add control
- insert activex button
- set button caption
language: ja
lastmod: 2026-11-18
og_description: C# を使用して空白の Word 文書を作成し、ActiveX ボタンを挿入します。この完全なチュートリアルに従ってコントロールを追加し、ボタンのキャプションを設定し、結果を保存してください。
og_image_alt: Screenshot of a Word document showing an inserted ActiveX button with
  the caption “Press”
og_title: 空白のWord文書を作成し、ActiveXボタンを挿入する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  headline: Create a blank Word document and insert an ActiveX button
  type: TechArticle
- description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  name: Create a blank Word document and insert an ActiveX button
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET installed (`Install-Package Aspose.Words`). * Basic familiarity with
      C# and Visual Studio or any .NET‑compatible IDE.'
  - name: Tip
    text: 'If you need the button to appear on a specific page, move the builder’s
      cursor first:'
  - name: Expected result
    text: Opening `with_button.docx` in Word shows a blank page with a rectangular
      button labeled **Press**. Clicking the button does nothing by default because
      no VBA macro is attached, but the control is fully functional and can be wired
      to code later.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: 空白のWord文書を作成し、ActiveXボタンを挿入する
url: /ja/net/working-with-oleobjects-and-activex/create-a-blank-word-document-and-insert-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 空白の Word ドキュメントを作成し、ActiveX ボタンを挿入する

**空白の Word ドキュメントを作成**し、その中にインタラクティブな ActiveX ボタンを配置する必要がある場合、このガイドでは Aspose.Words for .NET を使用して正確にその方法を示します。完全なコードを確認し、各行がなぜ重要かを理解し、**ボタンのキャプションを設定**してコントロールがユーザー操作の準備ができているように見せる方法を学びます。

主目的に加えて、**ActiveX の挿入方法**、Word ファイルへの **コントロールの追加方法** の手順、そしてカスタムキャプション付き **ActiveX ボタンの挿入** の微妙な点についても取り上げます。最後まで読むと、埋め込み UI 要素が必要なあらゆるドキュメント自動化シナリオで再利用できるパターンが手に入ります。

## 学べること

* プログラムで **空白の Word ドキュメントを作成**する方法。  
* **ActiveX ボタンを挿入**し、そのプロパティを設定するために必要な正確な API 呼び出し。  
* コントロールが目的のテキストを表示するように **ボタンのキャプションを設定**する方法。  
* ファイルを任意の場所に保存する際のヒントと一般的な落とし穴への対処法。

### 前提条件

* .NET 6.0 以降（コードは .NET Framework 4.6+ でも動作します）。  
* Aspose.Words for .NET がインストールされていること（`Install-Package Aspose.Words`）。  
* C# と Visual Studio、または任意の .NET 対応 IDE の基本的な知識。

---

## Aspose.Words を使用して空白の Word ドキュメントを作成する

最初のステップは空の `Document` オブジェクトをインスタンス化することです。このオブジェクトは、何も追加するまでコンテンツを含まない Word ファイルを表します。

```csharp
// Step 1: Create a new blank document
Document document = new Document();
```

*Why this matters*: 空の `Document` はクリーンなキャンバスを提供します。後で段落、表、またはコントロールを追加しても、既存の書式設定を気にする必要がありません。

---

## ドキュメント操作用に DocumentBuilder を初期化する

`DocumentBuilder` は、現在のカーソル位置にコンテンツを挿入できるヘルパークラスです。ドキュメント内の位置を自動的に追跡します。

```csharp
// Step 2: Initialise a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this matters*: `DocumentBuilder` がなければ、低レベルのノードツリーを手動で操作する必要があります。ビルダーはテキスト、画像、ActiveX コントロールの挿入を簡素化します。

---

## ActiveX ボタンの挿入方法（insert activex button）

ここでは `InsertForms2OleControl` を使用して ActiveX コントロールを埋め込みます。このメソッドは 3 つの引数が必要です：

1. コントロールのタイプ（`OleControlType.CommandButton`）。  
2. コントロールの内部名（VBA やマクロコードで使用）。  
3. ページ上の位置とサイズを定義する `RectangleF`。

```csharp
// Step 3: Insert a CommandButton ActiveX control at the current cursor position
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,          // type of control
    "ClickMe",                             // internal name (identifier)
    new System.Drawing.RectangleF(0, 0, 100, 30)); // x, y, width, height
```

*Why this matters*: これは Word ドキュメントに **ActiveX を挿入する方法** の核心です。矩形の座標はポイント単位で表されます（1 ポイント = 1/72 インチ）。ボタンを必要な位置に配置できるように調整してください。

### ヒント

ボタンを特定のページに表示させたい場合は、まずビルダーのカーソルを移動させます：

```csharp
builder.MoveToSection(0);  // moves to the first (and only) section
builder.InsertParagraph(); // ensures there is a paragraph to host the control
```

---

## ボタンのキャプションを設定する方法（set button caption）

コントロールを配置した後、そのプロパティを変更できます。最も目立つプロパティは `Caption` で、ボタンに表示されるテキストを決定します。

```csharp
// Step 4: Set the visible caption of the button
commandButton.Caption = "Press";
```

*Why this matters*: ユーザーが見るのは内部名ではなくキャプションです。これを変更することで、最終的なドキュメントでボタンが意味を持つようになります。

---

## ボタンを含むドキュメントを保存する

最後に、ドキュメントをディスクに書き込みます。サポートされている任意の形式（`.docx`、`.pdf` など）を選択できます。ここでは Word ドキュメントとして保存します。

```csharp
// Step 5: Save the document with the ActiveX button
string outputPath = @"C:\Temp\with_button.docx";
document.Save(outputPath);
```

*Why this matters*: ファイルを永続化することで、Microsoft Word で開いてボタンをテストできます。ドキュメントを開くと、ボタンは “Press” というキャプションで表示されます。

### 期待される結果

`with_button.docx` を Word で開くと、四角形のボタンに **Press** とラベル付けされた空白ページが表示されます。デフォルトでは VBA マクロが付いていないためクリックしても何も起こりませんが、コントロールは完全に機能しており、後でコードに接続できます。

---

## 特定の段落にコントロールを追加する方法（how to add control）

場合によっては、特定の段落内にボタンを配置したいことがあります。たとえば、指示テキストの後などです。`MoveTo` を使用してコントロールを挿入する前にビルダーの位置を設定します。

```csharp
// Example: add a paragraph, then insert the button after it
builder.Writeln("Click the button below to continue:");
builder.InsertParagraph(); // creates a new empty paragraph
builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    "ContinueBtn",
    new System.Drawing.RectangleF(0, 0, 120, 35));
```

*Why this matters*: このパターンはコンテキスト内で **コントロールを追加する方法** を示し、ドキュメントのレイアウトが論理的に保たれることを保証します。

---

## 一般的な落とし穴と回避方法

| 問題 | 発生原因 | 対策 |
|-------|----------------|-----|
| ボタンがページ外に表示される | 矩形座標がページ余白の外にある | `builder.PageSetup` を使用してページサイズを取得し、安全な `RectangleF` を計算します。 |
| キャプションが表示されない | `Caption` がコントロールの完全な初期化前に設定されている | Step 4 のように `InsertForms2OleControl` 呼び出し **後** に `Caption` を設定します。 |
| ドキュメントにボタンが保存されない | 挿入後にビルダーのカーソルが移動され、変更がコミットされていない | ビルダーを同じページに保つか、保存前に `builder.Document.UpdatePageLayout()` を呼び出します。 |

---

## 完全な実行可能サンプル

以下はコピーして貼り付け、実行できる完全なプログラムです。空白の Word ファイルを作成し、ActiveX ボタンを挿入し、キャプションを設定し、結果を保存します。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Initialise DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(document);

        // Optional: add some explanatory text
        builder.Writeln("Below is an ActiveX button created programmatically:");
        builder.InsertParagraph();

        // 3️⃣ Insert the ActiveX CommandButton
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "MyButton",
            new RectangleF(0, 0, 100, 30));

        // 4️⃣ Set the button caption
        commandButton.Caption = "Press";

        // 5️⃣ Save the document
        string outputPath = @"C:\Temp\with_button.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Output**: プログラムを実行した後、Microsoft Word で `C:\Temp\with_button.docx` を開きます。単一ページに「Below is an ActiveX button created programmatically:」というテキストと、**Press** とラベル付けされたボタンが表示されます。

---

## 結論

これで **空白の Word ドキュメントを作成**し、**ActiveX ボタンを挿入**し、**ボタンのキャプションを設定**し、Aspose.Words for .NET を使用して結果を **保存**する方法が分かりました。同じパターンは `OleControlType` を変更することで、他の ActiveX コントロール（チェックボックス、リストボックスなど）にも拡張できます。  

次に、VBA を使用した **ActiveX ボタンのイベント挿入方法** や、既にコンテンツが含まれる既存ドキュメントへの **コントロールの追加方法** を検討するとよいでしょう。これらのトピックはすべて、本稿で取り上げた概念に直接基づいています。

コーディングを楽しんでください。また、アプリケーションの UI 要件に合わせて、さまざまなサイズ、位置、キャプションを自由に試してみてください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックをカバーしています。各リソースには、ステップバイステップの解説付きの完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [ActiveX コマンドボタン付き Word ドキュメントを C# で作成する方法](/words/english/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/)
- [Aspose.Words を使用して Word ドキュメントに ActiveX ボタンを追加する方法](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}