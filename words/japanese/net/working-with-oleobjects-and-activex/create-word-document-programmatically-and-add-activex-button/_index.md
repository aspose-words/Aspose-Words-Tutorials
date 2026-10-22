---
category: general
date: 2026-08-10
description: Aspose.Words を使用してプログラムで Word 文書を作成し、ActiveX コントロールのボタンを追加します。数分で ActiveX
  コマンドボタンを挿入できます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add activex control word
- insert activex command button
language: ja
lastmod: 2026-08-10
og_description: Aspose.Words を使用してプログラムで Word 文書を作成し、ActiveX コントロールのボタンを追加します。ActiveX
  コマンドボタンをすばやく挿入する方法を学びましょう。
og_image_alt: Screenshot of a Word document created programmatically with an ActiveX
  command button
og_title: プログラムでWord文書を作成 – C#でActiveXボタンを追加
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  headline: Create word document programmatically and add ActiveX button
  type: TechArticle
- description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  name: Create word document programmatically and add ActiveX button
  steps:
  - name: Open `ActiveX_CommandButton.docx` in Microsoft Word.
    text: Open `ActiveX_CommandButton.docx` in Microsoft Word.
  - name: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
    text: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
  - name: Click **Design Mode**. The button should appear with the label “Submit”.
    text: Click **Design Mode**. The button should appear with the label “Submit”.
  - name: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
    text: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- C#
title: Word文書をプログラムで作成し、ActiveXボタンを追加する
url: /ja/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# プログラムでWord文書を作成し、ActiveXボタンを追加する

If you need to **create word document programmatically**, this guide walks you through the entire process with Aspose.Words for .NET. You’ll also learn how to **add activex control word** elements and **insert activex command button** objects in a single, self‑contained example.

プログラムでWord文書を**作成**する必要がある場合、このガイドではAspose.Words for .NET を使用した全工程を解説します。また、**ActiveX コントロール**要素の**追加**や**ActiveX コマンドボタン**オブジェクトの**挿入**方法も、単一の自己完結型サンプルで学べます。

Generating Word files from code removes the manual step of opening Microsoft Word, letting you build reports, invoices, or data‑driven contracts automatically. By the end of this tutorial you will have a ready‑to‑run C# console app that produces a `.docx` file containing an interactive ActiveX CommandButton.

コードからWordファイルを生成することで、Microsoft Word を手動で開く手間が省け、レポートや請求書、データ駆動型の契約書などを自動的に作成できます。このチュートリアルの最後までに、インタラクティブなActiveX CommandButton を含む `.docx` ファイルを生成する、すぐに実行可能な C# コンソールアプリが完成します。

## 前提条件

Before you start, make sure you have:

* .NET 6.0 SDK or later (the code also works with .NET Framework 4.6+)
* Visual Studio 2022 or any IDE that supports .NET development
* A valid Aspose.Words for .NET license (you can use the free evaluation key for testing)
* Basic familiarity with C# syntax and the concept of COM/ActiveX controls

> **プロのコツ:** 生成した文書を Word がインストールされていないユーザーに配布する場合、ActiveX コントロールのランタイムファイルを `.docx` と同じフォルダーに配置するか、マクロ有効テンプレートを提供してください。

## プログラムでWord文書を作成する – 初期設定

First, add the Aspose.Words NuGet package to your project:

```bash
dotnet add package Aspose.Words
```

Then create a new console project (if you don’t already have one):

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
```

Open the generated `Program.cs` file – we’ll replace its contents with the full solution below.

## 手順 1: 名前空間のインポートとライセンスの設定

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // OPTIONAL: Apply your Aspose.Words license to remove evaluation watermarks.
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");
```

*Why this matters*: Importing `Aspose.Words.Drawing` gives you access to `Forms2OleControl`, the class that represents an ActiveX control inside a Word document. Setting a license early prevents runtime warnings in production.

*Why this matters*: `Aspose.Words.Drawing` をインポートすると、Word 文書内の ActiveX コントロールを表すクラス `Forms2OleControl` が使用可能になります。ライセンスを早期に設定することで、本番環境での実行時警告を防げます。

## 手順 2: 空白ドキュメントと DocumentBuilder の作成

```csharp
            // Create a new empty Word document.
            Document doc = new Document();

            // DocumentBuilder provides a convenient API for inserting text, tables, and controls.
            DocumentBuilder builder = new DocumentBuilder(doc);
```

The `Document` object is the in‑memory representation of a `.docx` file. `DocumentBuilder` works like a cursor that you move around the document to insert elements.

`Document` オブジェクトは `.docx` ファイルのメモリ上の表現です。`DocumentBuilder` は文書内を移動しながら要素を挿入できるカーソルのように機能します。

## 手順 3: ActiveX CommandButton コントロールの挿入

```csharp
            // Insert an ActiveX CommandButton.
            // Parameters: control type, width, height, left position, top position (all in points).
            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, // ActiveX type
                100,   // Width in points
                50,    // Height in points
                150,   // Left offset from the page margin
                200);  // Top offset from the page margin
```

`InsertForms2OleControl` creates an OLE object that Word treats as an ActiveX control. The coordinate system uses points (1 point = 1/72 inch), which matches Word’s layout engine.

`InsertForms2OleControl` は Word が ActiveX コントロールとして扱う OLE オブジェクトを作成します。座標系はポイント単位（1 ポイント = 1/72 インチ）で、Word のレイアウトエンジンと一致します。

## 手順 4: ボタンのキャプションとオプションプロパティの設定

```csharp
            // Set the text that appears on the button.
            commandBtn.Caption = "Submit";

            // Optional: assign a macro name that Word will call when the button is clicked.
            // commandBtn.OnAction = "MyMacroName";
```

Setting the `Caption` property is the most common way to label the button. If you need the button to execute a VBA macro, assign the macro name to `OnAction`. This tutorial focuses on the visual part; macro integration is covered in the “Next steps” section.

`Caption` プロパティを設定するのがボタンにラベルを付ける最も一般的な方法です。ボタンに VBA マクロを実行させたい場合は、マクロ名を `OnAction` に割り当てます。このチュートリアルはビジュアル面に焦点を当てており、マクロ統合は「次のステップ」セクションで取り上げます。

## 手順 5: ドキュメントの保存

```csharp
            // Define the output path – change this to a folder that exists on your machine.
            string outputPath = @"ActiveX_CommandButton.docx";

            // Save the document with the embedded ActiveX control.
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

When you run the program, you’ll see a console message confirming that `ActiveX_CommandButton.docx` has been written to disk.

プログラムを実行すると、`ActiveX_CommandButton.docx` がディスクに書き込まれたことを示すコンソールメッセージが表示されます。

### 完全なソースコード（コピー＆ペースト用）

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton,
                100, 50, 150, 200);

            commandBtn.Caption = "Submit";
            // commandBtn.OnAction = "MyMacroName";

            string outputPath = @"ActiveX_CommandButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Running the snippet produces a Word file that contains a clickable **ActiveX command button**. Open the file in Microsoft Word, switch to **Design Mode** (Developer tab → Design Mode), and you’ll see the button rendered exactly where you placed it.

このスニペットを実行すると、クリック可能な **ActiveX command button** を含む Word ファイルが生成されます。Microsoft Word でファイルを開き、**Design Mode**（Developer タブ → Design Mode）に切り替えると、配置した場所にボタンが正確に表示されます。

## 手順 6: 結果の確認

1. Open `ActiveX_CommandButton.docx` in Microsoft Word.  
   Microsoft Word で `ActiveX_CommandButton.docx` を開きます。
2. Enable the **Developer** tab if it isn’t visible (`File → Options → Customize Ribbon → check Developer`).  
   **Developer** タブが表示されていない場合は有効にします（`File → Options → Customize Ribbon → Developer` にチェック）。
3. Click **Design Mode**. The button should appear with the label “Submit”.  
   **Design Mode** をクリックします。ボタンに “Submit” というラベルが表示されます。
4. If you added an `OnAction` macro, click the button while Design Mode is off to trigger the macro.  
   `OnAction` マクロを追加した場合、Design Mode をオフにした状態でボタンをクリックするとマクロが実行されます。

If the button does not show, ensure that Word’s security settings allow ActiveX controls (`File → Options → Trust Center → Trust Center Settings → ActiveX Settings`).  
ボタンが表示されない場合は、Word のセキュリティ設定で ActiveX コントロールが許可されていることを確認してください（`File → Options → Trust Center → Trust Center Settings → ActiveX Settings`）。

## よくある質問とエッジケース

| 質問 | 回答 |
|----------|--------|
| **他の ActiveX タイプを挿入できますか？** | はい。`Forms2OleControlType` 列挙体には `CheckBox`、`OptionButton`、`ComboBox` などが含まれます。`CommandButton` を目的の列挙値に置き換えてください |

## 次に学ぶべきことは？

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Aspose.Words for .NET を使用して Word 文書にグループ シェイプを作成する](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words を使用してヘッダーとフッター付きの Word 文書を作成する](/words/english/net/header-footer-formatting/create-header-footer/)
- [Aspose.Words を使用して Word 文書にインライン画像を挿入する](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}