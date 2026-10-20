---
category: general
date: 2026-07-19
description: Aspose.Words C# を使用して Word 文書を作成し、ActiveX コマンドボタンの追加方法、ボタンサイズの設定、プログラムによるボタンの挿入方法を学ぶ。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to add activex
- insert command button
- set button size
- how to insert button
language: ja
lastmod: 2026-07-19
og_description: Aspose.Words C# を使用して Word 文書を作成し、数秒で ActiveX コマンドボタンを埋め込みます。ボタンのサイズ設定とボタンの挿入を簡単に行えるステップバイステップガイドに従ってください。
og_image_alt: Screenshot of a Word document showing an ActiveX command button inserted
  via C#
og_title: ActiveX ボタンで Word 文書を作成 – C# チュートリアル
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  headline: Create Word Document with ActiveX Button – C# Guide
  type: TechArticle
- description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  name: Create Word Document with ActiveX Button – C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works on .NET Framework 4.7+). - A valid
      Aspose.Words for .NET license (or a free evaluation key). - Visual Studio 2022
      (or any IDE you like). - Basic familiarity with C# and object‑oriented programming.'
  - name: Platform Limitations
    text: '- ActiveX controls only run on the Windows version of Word. If your audience
      includes macOS or Word Online users, the button will appear as a static image.
      - Some corporate environments disable ActiveX for security; you may need to
      sign the document or inform users to enable content.'
  - name: VBA Interaction (Optional)
    text: If you want the button to execute a macro, you’ll have to add a VBA project
      to the document after saving. Aspose.Words does not generate VBA code automatically,
      but you can use the `Document.VbaProject` API to inject it.
  - name: Naming Collisions
    text: Always give each control a unique `Name`. Re‑using the same name can cause
      runtime errors when Word tries to resolve the control.
  - name: Performance Tip
    text: When inserting many controls, reuse a single `DocumentBuilder` instance
      and avoid calling `doc.Save` inside a loop. Batch the inserts and save once
      at the end.
  - name: What’s Next?
    text: '- **Style the button** – change fonts, colors, or add an image background.
      - **Attach VBA macros** – make the button perform calculations or launch external
      programs. - **Combine with other controls** – checkboxes, list boxes, or even
      embedded Excel sheets.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: ActiveXボタンでWord文書を作成する – C#ガイド
url: /ja/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ActiveX ボタン付き Word 文書の作成 – 完全 C# ガイド

Word 文書に機能する ActiveX ボタンを含めて **Word 文書を作成** したいと思ったことはありませんか？レポートを自動化して、ファイル内にクリック可能な「承認」コントロールが必要な場合などに最適です。このチュートリアルでは、Aspose.Words for .NET を使用して ActiveX コマンドボタンを追加し、サイズを設定し、必要な場所に挿入する方法をステップバイステップで解説します。

手動で Word を開かずに *how to add activex* コントロールを追加したいと考えている方は、ここが正解です。最後まで実行可能なサンプルと、各手順の明確な説明、一般的な落とし穴への対処法をご紹介します。

## 学べること

- C# プロジェクトで Aspose.Words を設定する方法  
- **create word document** と ActiveX コマンドボタンを埋め込む正確なコード  
- **set button size** とキャプション・名前のカスタマイズ方法  
- **insert command button** と **how to insert button** を文書内任意の位置に挿入する正しい手順  
- エッジケース（Word バージョン、プラットフォーム制限、セキュリティ警告）への考慮点

### 前提条件

- .NET 6.0 以上（コードは .NET Framework 4.7+ でも動作します）。  
- 有効な Aspose.Words for .NET ライセンス（または無料評価キー）。  
- Visual Studio 2022（またはお好みの IDE）。  
- C# とオブジェクト指向プログラミングの基本的な知識。

他のサードパーティライブラリは不要です。

---

## Step 1: Create Word Document – Project Setup

**insert command button** を挿入できるようにする前に、作業用の空白の Word ファイルが必要です。このステップでは、Aspose.Words を使った古典的な “create word document” パターンも紹介します。

```csharp
// Add the Aspose.Words NuGet package first:
//   dotnet add package Aspose.Words
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

// 1️⃣  Initialize a new blank document.
Document doc = new Document();

// 1️⃣  Create a DocumentBuilder – it lets us place content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Why this matters:** `Document` は .docx ファイル全体を表し、`DocumentBuilder` は現在のカーソル位置を追跡します。以降のすべての挿入（ActiveX コントロールを含む）はこのビルダーを基準に行われます。

---

## Step 2: How to Add ActiveX – Build the CommandButton Control

文書が用意できたので、**how to add activex** の部分に取り組みます。Aspose.Words は ActiveX オブジェクト用に `Forms2OleControl` クラスを提供しています。ここではコマンドボタンを作成し、**set button size** の要件を含むプロパティを設定します。

```csharp
// 2️⃣  Create the ActiveX command button.
Forms2OleControl commandButton = new Forms2OleControl(
    doc,                     // Parent document
    Forms2OleControlType.CommandButton); // Control type

// Configure appearance – this is where we **set button size**.
commandButton.Width = 120;          // Width in points (≈1.67 inches)
commandButton.Height = 30;          // Height in points (≈0.42 inches)

// Set the text the user sees.
commandButton.Caption = "Click Me";

// Give the control a unique name for later reference.
commandButton.Name = "cmdButton1";
```

> **Pro tip:** サイズはポイント単位で測定されます（1 ポイント = 1/72 インチ）。レイアウトに合わせて数値を調整してください。典型的なツールバーボタンなら 120 × 30 がちょうど良いです。

---

## Step 3: Insert Command Button – The Core of **Insert Command Button**

コントロールの準備ができたので、**insert command button** をビルダーの現在位置に文書へ挿入します。ビルダーは任意の場所（例：段落の後）に移動させてからこのメソッドを呼び出すことができます。

```csharp
// 3️⃣  Insert the prepared ActiveX control into the document.
builder.InsertForms2OleControl(commandButton);
```

特定のブックマークに **how to insert button** したい場合は、まずビルダーを移動させます：

```csharp
builder.MoveToBookmark("MyPlace"); // Ensure a bookmark named 'MyPlace' exists
builder.InsertForms2OleControl(commandButton);
```

> **What happens behind the scenes?** Aspose.Words は必要な OLE オブジェクトストリームを .docx パッケージに書き込み、Word が余分なマクロなしでボタンを描画できるようにします。

---

## Step 4: Save the Document – Finishing the **Create Word Document** Cycle

最終ステップはシンプルです：ファイルをディスクに保存します。これで **create word document** の一連の流れが完了し、ActiveX が埋め込まれた状態で保存されます。

```csharp
// 4️⃣  Save the document where you want it.
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
```

生成されたファイルを Microsoft Word（Windows のみ）で開きます。 “Click Me” とラベル付けされたクリック可能なボタンが表示されるはずです。ボタンをクリックすると CommandButton のデフォルトアクションがトリガーされますが、VBA コードを添付しない限り何も起こりません。ただしコントロール自体は完全に機能します。

> **Expected output:** 1 ページだけの .docx ファイルで、挿入ポイントにセンタリングされた 120 × 30 pt のボタンが配置され、キャプションは “Click Me”。  
> ![ActiveX button inserted into a Word document](placeholder-image.png)  
> *Image alt text:* **ActiveX button inserted into a Word document using C#** (matches `og_image_alt`).

---

## Step 5: Edge Cases, Security, and Best Practices

### プラットフォームの制限
- ActiveX コントロールは Windows 版 Word でのみ動作します。macOS や Word Online のユーザーがいる場合、ボタンは静的画像として表示されます。  
- 一部の企業環境ではセキュリティ上の理由で ActiveX が無効化されています。その場合、文書に署名を付与するか、ユーザーにコンテンツの有効化を案内する必要があります。

### VBA との連携（オプション）
ボタンにマクロを実行させたい場合は、保存後に VBA プロジェクトを文書に追加する必要があります。Aspose.Words は VBA コードを自動生成しませんが、`Document.VbaProject` API を使って注入できます。

### 名前の衝突
各コントロールには必ず一意の `Name` を付けてください。同じ名前を再利用すると、Word がコントロールを解決できずに実行時エラーが発生します。

### パフォーマンスのヒント
多数のコントロールを挿入する場合は、単一の `DocumentBuilder` インスタンスを再利用し、ループ内で `doc.Save` を呼び出さないようにします。挿入をバッチ処理し、最後に一度だけ保存してください。

---

## Full Working Example

すべてをまとめた、コピー＆ペーストで動作する完全なプログラムは以下です：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Create and configure the ActiveX command button.
        Forms2OleControl commandButton = new Forms2OleControl(
            doc, Forms2OleControlType.CommandButton);
        commandButton.Width = 120;          // Set button size – width
        commandButton.Height = 30;          // Set button size – height
        commandButton.Caption = "Click Me";
        commandButton.Name = "cmdButton1";

        // Insert the button at the current cursor position.
        builder.InsertForms2OleControl(commandButton);

        // Save the document.
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

プログラムを実行し、保存されたファイルを開くと、ビルダーが位置していた正確な場所にボタンが表示されます。

---

## Conclusion

我々は **create word document** をゼロから作成し、`Forms2OleControl` の設定で **how to add activex** を学び、**set button size** プロパティをマスターし、**insert command button** と **how to insert button** を任意の場所に正しく挿入する方法を実演しました。

この単一のコードサンプルから、インタラクティブなフォームを備えたテンプレート作成、ユーザー承認が必要な契約書の自動生成、あるいはレポート内に便利なコントロールを散りばめるといった、よりリッチな Word 自動化の基盤が手に入ります。

### 次にやること

- **Style the button** – フォントや色を変更したり、画像背景を追加したりします。  
- **Attach VBA macros** – ボタンに計算処理や外部プログラム起動をさせます。  
- **Combine with other controls** – チェックボックス、リストボックス、さらには埋め込み Excel シートなどと組み合わせます。  

自由に試してみて、問題が発生したらコメントを残してください。Happy coding、そして Aspose.Words で Word の自動化を楽しんでください！

## What Should You Learn Next?

以下のチュートリアルは、本ガイドで示した手法を基にした、密接に関連するトピックを扱っています。各リソースには、完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得したり、独自プロジェクトで代替実装アプローチを探求したりするのに役立ちます。

- [Aspose.Words for .NET を使用した Word 文書の作成](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Aspose.Words for .NET を使用した Word 文書へのグループ シェイプ作成](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words を使用した Word 文書へのインライン画像挿入](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}