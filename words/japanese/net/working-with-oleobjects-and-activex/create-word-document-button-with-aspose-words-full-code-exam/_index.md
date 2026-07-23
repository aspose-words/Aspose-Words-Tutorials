---
category: general
date: 2026-07-23
description: Aspose.Words を使用して Word 文書にボタンを作成する – .docx ファイルに ActiveX CommandButton
  を挿入するステップバイステップガイド
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document button
- ActiveX CommandButton
- DocumentBuilder
- InsertForms2OleControl
- Aspose.Words
language: ja
lastmod: 2026-07-23
og_description: Aspose.WordsでWord文書にボタンを作成：数分でActiveX CommandButtonをWordファイルに埋め込む方法を学びましょう。
og_image_alt: Screenshot of a Word document showing an inserted CommandButton control
og_title: Word文書作成ボタン – Aspose.Words 完全ガイド
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  headline: create word document button with Aspose.Words – Full Code Example
  type: TechArticle
- description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  name: create word document button with Aspose.Words – Full Code Example
  steps:
  - name: '**Creates** an OLE object inside the Word file.'
    text: '**Creates** an OLE object inside the Word file.'
  - name: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
    text: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
  - name: '**Positions** it according to the rectangle we supplied.'
    text: '**Positions** it according to the rectangle we supplied.'
  - name: Launch Microsoft Word.
    text: Launch Microsoft Word.
  - name: Navigate to **File → Open** and select `CommandButton.docx`.
    text: Navigate to **File → Open** and select `CommandButton.docx`.
  - name: You should see a rectangular button labeled “CommandButton1”.
    text: You should see a rectangular button labeled “CommandButton1”.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
- CommandButton
title: Aspose.Words を使用した Word ドキュメント作成ボタン – 完全コード例
url: /ja/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words を使用した Word 文書ボタンの作成 – 完全プログラミングガイド

Ever needed to **create word document button** but weren’t sure which API to reach for? You’re not alone—most developers hit a wall when they try to embed interactive controls into a .docx file. The good news? With Aspose.Words for .NET you can drop a fully functional ActiveX CommandButton into a Word document in just a few lines of code.

**Word 文書ボタンを作成**したいと思ったことはありますか、しかしどの API を使用すべきか分からなかったことはありませんか？あなたは一人ではありません—ほとんどの開発者は .docx ファイルにインタラクティブなコントロールを埋め込もうとすると壁にぶつかります。良いニュースは、Aspose.Words for .NET を使用すれば、数行のコードで完全に機能する ActiveX CommandButton を Word 文書に埋め込むことができます。

このチュートリアルでは、プロジェクトの設定から `DocumentBuilder` の初期化、`InsertForms2OleControl` を使用したボタンの挿入、そして Word がコントロールを認識できるようにファイルを保存するまでの全工程を順に解説します。最後まで実行すれば、クリック可能なボタンを含む、すぐに使用できる Word ファイルが手に入ります—COM インターロップの複雑な作業は不要です。

## 必要なもの

- **.NET 6.0** 以上 (コードは .NET Framework 4.6+ でも動作します)。  
- **Aspose.Words for .NET** NuGet パッケージ (バージョン 23.9 以上)。  
- C# の基本的な理解 (構文は初心者向けに保ちます)。  
- Visual Studio 2022 またはお好みの IDE。  

以上です—余計な COM 参照も Office インターロップも不要で、純粋なマネージドコードだけです。

---

## Step 1: Aspose.Words を設定して **Word 文書ボタンを作成**

First things first, add the Aspose.Words package to your project:

```bash
dotnet add package Aspose.Words
```

Or, if you’re using the Visual Studio NuGet UI, search for “Aspose.Words” and hit **Install**. This single line gives you access to the `Document`, `DocumentBuilder`, and the `InsertForms2OleControl` method we’ll need later.

または、Visual Studio の NuGet UI を使用している場合は “Aspose.Words” を検索し、**Install** をクリックしてください。この一行で `Document`、`DocumentBuilder`、そして後で必要になる `InsertForms2OleControl` メソッドが利用可能になります。

> **プロのヒント:** NuGet パッケージは常に最新に保ちましょう。新しいリリースには ActiveX の取り扱いに関するバグ修正が含まれていることが多いです。

---

## Step 2: **ActiveX CommandButton** 用に **DocumentBuilder** を初期化

Now we create a fresh Word document and spin up a `DocumentBuilder`. Think of `DocumentBuilder` as the paintbrush that lets you draw content onto the canvas.

ここで新しい Word 文書を作成し、`DocumentBuilder` を起動します。`DocumentBuilder` はキャンバス上にコンテンツを描くためのペイントブラシのようなものです。

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 2.1: Create a new empty document
        Document document = new Document();

        // Step 2.2: Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

Notice how we import `System.Drawing`—the `Rectangle` struct defines the button’s location and size. This is where the **ActiveX CommandButton** will live.

`System.Drawing` をインポートしていることに注目してください—`Rectangle` 構造体がボタンの位置とサイズを定義します。ここが **ActiveX CommandButton** が配置される場所です。

---

## Step 3: **InsertForms2OleControl** を使用して **CommandButton を追加**

Here’s the heart of the tutorial: inserting the button itself. The `InsertForms2OleControl` method takes three arguments—control type, a `Rectangle`, and optionally a name. We’ll use `OleControlType.CommandButton` to specify the exact control we want.

チュートリアルの核心です：ボタンそのものを挿入します。`InsertForms2OleControl` メソッドは 3 つの引数を受け取ります—コントロールの種類、`Rectangle`、そしてオプションで名前です。ここでは `OleControlType.CommandButton` を使用して、目的のコントロールを指定します。

```csharp
        // Step 3: Insert an ActiveX CommandButton at (0,0) with width=100, height=30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));
```

その一呼び出しで多くのことが行われます：

1. **作成** Word ファイル内に OLE オブジェクトを作成します。  
2. **登録** それを ActiveX CommandButton として登録し、Word がクリック可能な UI 要素として表示します。  
3. **配置** 提供した矩形に従って配置します。  

ボタンのキャプションやその他のプロパティを変更したい場合は、挿入後に基礎となる `OleFormat` にアクセスして設定できます。ほとんどのシナリオでは、デフォルトのキャプション (“CommandButton1”) で十分です。

---

## Step 4: **CommandButton** を含む Word 文書を保存

Saving is straightforward—just point to a folder you have write access to. The file extension must be `.docx` for the button to survive the round‑trip.

保存は簡単です—書き込み権限のあるフォルダーを指定するだけです。ボタンを保持するためには、ファイル拡張子を `.docx` にする必要があります。

```csharp
        // Step 4: Save the document with the embedded button
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

When you open `CommandButton.docx` in Microsoft Word, you’ll see a small button at the top‑left corner of the first page. Clicking it does nothing out‑of‑the‑box (that would require VBA), but the control is fully functional and can be wired up later.

`CommandButton.docx` を Microsoft Word で開くと、1 ページ目の左上隅に小さなボタンが表示されます。クリックしても何も起こりません（VBA が必要です）が、コントロールは完全に機能しており、後から接続できます。

> **なぜこれが機能するのか:** Aspose.Words は OLE ストリームを直接 DOCX パッケージに書き込むため、実行時に Word がコントロールを生成する必要がありません。これにより、ボタンは配置した正確な位置に表示されます。

---

## Step 5: Word でボタンを確認

Open the generated file:

1. Microsoft Word を起動します。  
2. **File → Open** に移動し、`CommandButton.docx` を選択します。  
3. “CommandButton1” とラベル付けされた長方形のボタンが表示されるはずです。  

If you don’t see the button, make sure **Design Mode** is enabled (Developer → Design Mode). This toggles the visual representation of ActiveX controls.

ボタンが表示されない場合は、**Design Mode** が有効になっていることを確認してください（Developer → Design Mode）。これにより ActiveX コントロールの視覚的表現が切り替わります。

---

## Step 6: 高度なオプション – **ActiveX CommandButton** のカスタマイズ

Below are a few quick tweaks you might find handy:

以下は便利な簡単な調整例です：

| 目的 | コードスニペット |
|------|--------------|
| キャプションの変更 | ```csharp<br/>OleFormat ole = builder.CurrentParagraph.Runs[0].OleFormat;<br/>ole.OleControlCaption = "Submit";``` |
| マクロ名の設定（Word マクロサポートが必要） | ```csharp<br/>ole.OleControlMacroName = "MyMacro";``` |
| 挿入後のサイズ変更 | ```csharp<br/>builder.MoveToDocumentEnd();<br/>builder.InsertForms2OleControl(OleControlType.CommandButton, new Rectangle(0,0,150,40));``` |

These snippets demonstrate the flexibility of `InsertForms2OleControl`. You can even embed other ActiveX controls like `CheckBox` or `ListBox` by swapping the `OleControlType` enum.

これらのスニペットは `InsertForms2OleControl` の柔軟性を示しています。`OleControlType` 列挙体を変更することで、`CheckBox` や `ListBox` など他の ActiveX コントロールも埋め込むことができます。

---

## 完全な動作例

Below is the complete, copy‑paste‑ready program that **creates a word document button** from scratch:

以下は、最初から **Word 文書ボタンを作成** するための、完全でコピー＆ペースト可能なプログラムです：

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class CreateWordDocumentButton
{
    static void Main()
    {
        // 1️⃣ Create a new empty document
        Document document = new Document();

        // 2️⃣ Initialize DocumentBuilder – the tool that lets us edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert an ActiveX CommandButton at position (0,0) with size 100x30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));

        // 4️⃣ Save the .docx file – this is where the button lives
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);

        Console.WriteLine($"✅ Document with button saved to: {outputPath}");
    }
}
```

**Expected output when you run the program:**

**プログラム実行時の期待出力:**

```
✅ Document with button saved to: C:\Temp\CommandButton.docx
```

Open the resulting file and you’ll see the button exactly where the code placed it.

生成されたファイルを開くと、コードが配置した場所にボタンが正確に表示されます。

---

## よくある落とし穴と回避策

- **Missing `System.Drawing` reference** – `Rectangle` 構造体はそこにあります。これがないとコンパイラがエラーを出します。  
- **Using an older Aspose.Words version** – 初期リリースでは `InsertForms2OleControl` が完全にサポートされていませんでした。最新の安定版パッケージにアップグレードしてください。  
- **Saving as `.doc` instead of `.docx`** – 古いバイナリ形式では OLE ストリームが除去され、ボタンが消えてしまいます。  
- **Running on a headless server without Word installed** – ボタンはファイル内に残りますが、Word がないとプレビューできません。自動生成パイプラインでは問題ありません。

---

## 次のステップ – **Word 文書ボタン作成** ワークフローの拡張

Now that you’ve mastered the basics, consider these next‑level ideas:

基本をマスターしたので、次のレベルのアイデアを検討してみてください：

- **VBA マクロ** をボタンに添付してカスタムビジネスロジックを実装します。  
- 動的フォームのためにループで **複数のボタンを生成** します。  
- **Aspose.PDF と組み合わせ**、同じ文書を PDF にエクスポートしながらビジュアルレイアウトを保持します（ボタンは PDF では静的画像になります）。  
- **

## 次に学ぶべきことは？

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを探求するのに役立ちます。

- [Aspose.Words for .NET で Word 文書を作成](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Aspose.Words を使用した Word の長方形シェイプ作成 – ステップバイステップガイド](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words を使用した Word 文書へのインライン画像挿入](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}