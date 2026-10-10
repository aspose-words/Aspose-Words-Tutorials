---
category: general
date: 2026-10-10
description: Aspose.Words を使用して C# でボタンのテキストを設定し、ActiveX ボタンを追加します。ボタンの挿入方法、ボタン コントロールの作成方法、Word
  文書でのキャプションのカスタマイズ方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button text
- how to insert button
- create button control
- add activex control
- add activex button
language: ja
lastmod: 2026-10-10
og_description: C# と Aspose.Words を使用してボタンのテキストを設定し、ActiveX ボタンを追加します。このステップバイステップガイドに従って、ボタンを挿入し、ボタン
  コントロールを作成し、キャプションをカスタマイズしてください。
og_image_alt: Screenshot of a Word document showing an ActiveX button with custom
  text
og_title: C#でボタンのテキストを設定し、ActiveXボタンを追加する完全ガイド
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Set button text and add an ActiveX button in C# using Aspose.Words.
    Learn how to insert button, create button control, and customize the caption in
    a Word document.
  headline: Set button text and add an ActiveX button in C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- button control
- document automation
title: C#でボタンのテキストを設定し、ActiveXボタンを追加する
url: /ja/java/document-manipulation/set-button-text-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#でボタンテキストを設定し、ActiveXボタンを追加する

Word 文書内の ActiveX ボタンの **set button text** を設定する必要がある場合、このガイドで正確な手順を示します。チュートリアルの最後までに、**insert button** ができ、**button control** を作成し、C# の数行のコードだけでキャプションをカスタマイズできるようになります。

ActiveX コントロールを使用することは、Word でインタラクティブなフォームを作成したいとき、――契約テンプレート、アンケート、社内ツールの構築などです。この例では Aspose.Words for .NET を使用します。このライブラリは Microsoft Office をインストールせずに Word ファイルを操作できます。

## 前提条件

開始する前に、以下がインストールされていることを確認してください。

* .NET 6.0 SDK 以降がインストールされていること  
* Visual Studio 2022（または C# をサポートする任意の IDE）  
* Aspose.Words for .NET のライセンス（学習用には無料評価版で可）  

`Aspose.Words` NuGet パッケージへの参照も必要です：

```bash
dotnet add package Aspose.Words
```

## Word 文書にボタンを挿入する方法

最初のステップは新しい `Document` と `DocumentBuilder` を作成することです。ビルダーはコンテンツ（ActiveX コントロールを含む）を追加するためのエントリーポイントです。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:** `Document` は .docx ファイル全体を表し、`DocumentBuilder` は `InsertParagraph` や `InsertFormField` などの高レベルメソッドを提供します。クリーンなドキュメントから開始することで、ボタンが希望通りの位置に正確に表示されます。

## Forms2OleControl でボタンコントロールを作成する

ここで実際のボタンコントロールを作成します。`Forms2OleControl` は Aspose.Words がすべての ActiveX オブジェクトに使用するクラスで、`COMMANDBUTTON` タイプは Word 内でクリック可能なボタンとして表示されます。

```csharp
        // Step 2: Insert a Forms2OleControl of type COMMANDBUTTON
        Forms2OleControl button = builder.InsertForms2OleControl(
            Forms2OleControlType.COMMANDBUTTON, // control type
            100,  // left position (points)
            50,   // top position (points)
            200,  // width (points)
            150); // height (points)
```

**Explanation:**  
* `InsertForms2OleControl` は指定した正確な座標にコントロールを配置します。  
* サイズはポイントで定義されます（1 ポイント = 1/72 インチ）。レイアウトに合わせてこれらの数値を調整してください。

## ActiveX コントロールを追加し、一意の名前を付ける

各 ActiveX オブジェクトは一意の名前を持つべきです。これにより、後で（例：VBA でイベントを処理する際）参照できます。

```csharp
        // Step 3: Assign a unique name to the control
        button.SetName("MyActiveXButton");
```

**Tip:** 名前にスペースや特殊文字を使用しないでください。Word は名前を内部フォームモデルの識別子として扱います。

## ActiveX ボタンのテキスト（キャプション）を設定する

ここが主要キーワード **set button text** が重要になる箇所です。`Caption` プロパティはユーザーがボタン上で見るラベルを定義します。

```csharp
        // Step 4: Set the text that appears on the button
        button.SetCaption("Click Me");
```

ドキュメントを保存する前であれば、いつでもキャプションを変更できます。後で UI をローカライズする必要がある場合は、別の文字列で `SetCaption` を再度呼び出すだけです。

## ドキュメントを保存し、結果を確認する

最後に、ドキュメントをディスクに書き出します。Microsoft Word でファイルを開くと、カスタムキャプションが設定されたボタンが表示されます。

```csharp
        // Step 5: Save the document
        doc.Save("ActiveXButton.docx");
        System.Console.WriteLine("Document created with an ActiveX button.");
    }
}
```

**Expected output:** Word で *ActiveXButton.docx* を開くと、指定した座標に配置されたボタンが表示され、ラベルは **Click Me** です。ボタンをクリックすると、デフォルトの Word コマンドボタンの動作がトリガーされます（後で VBA でカスタマイズ可能）。

![Set button text example](https://example.com/activex-button.png){alt="ボタンテキスト設定例"}

## ActiveX ボタンを追加し、イベントを処理する（オプション）

ボタンにカスタムアクションを実行させたい場合、`Click` イベントに反応する VBA マクロを追加できます。マクロはプログラムで注入可能ですが、これは本チュートリアルの範囲外です。重要なのは、ボタンがすでに配置されキャプションが設定されていることですので、任意のイベントハンドリングに備えています。

## よくある落とし穴と回避方法

| 問題 | 発生理由 | 対策 |
|-------|----------------|-----|
| ボタンがずれて表示される | 座標はピクセルではなくポイントで指定されている | ピクセル値をポイントに変換する（`points = pixels * 72 / DPI`） |
| 保存後にキャプションが変更されない | `SetCaption` が `Save` の後に呼び出されている | `doc.Save` を呼び出す **前に** 常にキャプションを設定する |
| 古い Word バージョンでコントロールが表示されない | 一部の古い Word ビルドは完全な ActiveX サポートがない | 対象の Word バージョンでテストし、代替として `CheckBox` または `DropDownList` の使用を検討する |
| 出力にライセンス警告が表示される | 評価ライセンスが期限切れになる | 有効な Aspose.Words ライセンスを `License license = new License(); license.SetLicense("Aspose.Words.lic");` で適用する |

## 完全な実行可能サンプル

以下に、コピー＆ペーストして実行できる完全なプログラムを示します。必要な `using` ディレクティブがすべて含まれ、ドキュメント作成から保存までの全工程を実演します。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert an ActiveX command button at a specific location
            Forms2OleControl button = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON,
                100,   // left (points)
                50,    // top (points)
                200,   // width (points)
                150);  // height (points)

            // Give the button a unique identifier
            button.SetName("MyActiveXButton");

            // Set the visible text on the button (set button text)
            button.SetCaption("Click Me");

            // Save the document
            const string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}. Open it in Word to see the button.");
        }
    }
}
```

`dotnet run` でプログラムを実行します。実行後、*ActiveXButton.docx* を開き、ボタンのキャプションが **Click Me** であることを確認してください。

## 学んだことのまとめ

* Aspose.Words を使用して ActiveX ボタンの **set button text** 方法を学びました。  
* Word 文書に **how to insert button**、**create button control**、**add activex control** を行う正確な手順を確認しました。  
* 任意のフォームベースの Word 自動化プロジェクトに適用できる再利用可能なコードスニペットが手に入ります。

## 次のステップ

* `Forms2OleControlType` の他の値（例：`CHECKBOX` や `LISTBOX`）を調査して、よりリッチなフォームを構築しましょう。  
* ボタンを VBA マクロと組み合わせて、計算やデータ検証を実行します。  
* ドキュメントが入力された後、Aspose.Words の `FormField` API を使用してユーザー入力を読み取ります。

サイズ、位置、キャプションを自由に試して、デザイン要件に合わせてください。問題が発生した場合は、Aspose.Words のドキュメントに本チュートリアルで使用されたすべてのクラスの詳細なリファレンスがあります。

コーディングを楽しんでください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれ、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Aspose.Words で空白の Word 文書を作成 – ステップバイステップガイド](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Aspose.Words で Word の図形に影を追加 – ステップバイステップ](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)
- [Aspose.Words for .NET を使用して Word 文書のフッターにページ番号を追加](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}