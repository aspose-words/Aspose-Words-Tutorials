---
category: general
date: 2026-10-07
description: Aspose.Words C# を使用して Word 文書に OLE コマンドボタンを挿入する方法を学びましょう。DocumentBuilder、プロパティ、ファイルの保存に関するステップバイステップのガイドです。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert OLE command button
- Aspose.Words OLE control
- C# DocumentBuilder InsertForms2OleControl
- OleControlType CommandButton
- Word OLE command button
language: ja
lastmod: 2026-10-07
og_description: C# を使用して Word 文書に OLE コマンドボタンを挿入します。この簡潔なチュートリアルに従い、Aspose.Words で機能する
  CommandButton を追加、設定、保存してください。
og_image_alt: Insert OLE command button example in Word document
og_title: C#でWordにOLEコマンドボタンを挿入する – 完全なAspose.Wordsガイド
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  headline: How to insert OLE command button in a Word document using C#
  type: TechArticle
- description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  name: How to insert OLE command button in a Word document using C#
  steps:
  - name: Why this works
    text: '* `DocumentBuilder` is the primary API for building Word documents programmatically.
      * `InsertForms2OleControl` tells Aspose.Words to embed a **Forms2 OLE control**,
      which is the legacy Word form technology that supports command buttons, check
      boxes, etc. * The `OleControlType.CommandButton` enum va'
  - name: 1. What if the button does not appear where I expect?
    text: '* Word uses points, not pixels. Convert screen pixels to points (`points
      = pixels * 72 / DPI`). * Ensure the rectangle does not intersect page margins;
      otherwise Word may shift the control.'
  - name: 2. Can I insert the button into an existing document?
    text: Yes. Load the document with `new Document("Existing.docx")` and use the
      same `DocumentBuilder` workflow. Just remember to move the builder’s cursor
      (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, etc.)
      before calling `InsertForms2OleControl`.
  - name: 3. How do I attach a macro to the button?
    text: 'Aspose.Words does not create VBA code, but you can embed a macro after
      the document is generated:'
  - name: 4. Does this work with .NET Core on Linux?
    text: The OLE control is a Windows‑specific feature because it relies on COM.
      On Linux the button will be inserted, but it will appear as a static picture
      without interactive behavior. For cross‑platform interactive forms, consider
      using content controls (`StructuredDocumentTag`) instead.
  - name: 5. What if I need a different size or multiple buttons?
    text: Create additional `Rectangle` objects with unique coordinates and repeat
      the `InsertForms2OleControl` call. Each button can have its own `Caption` and
      `Name`.
  type: HowTo
tags:
- Aspose.Words
- C#
- OLE
- Word automation
title: C# を使用して Word 文書に OLE コマンドボタンを挿入する方法
url: /ja/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# を使用して Word ドキュメントに OLE コマンド ボタンを挿入する方法

プログラムで Word ファイルに **insert OLE command button** を挿入する必要がある場合、このガイドでは Aspose.Words for .NET を使用して正確な手順を示します。フォーム入力レポートを作成する場合や、ユーザー操作が必要なテンプレートを自動化する場合でも、以下の手順で完全な実行可能なソリューションが得られます。

空白のドキュメントを作成し、`DocumentBuilder` を使用して `Forms2OleControl` を配置し、ボタンのキャプションと名前を設定し、最後に `.docx` として保存する方法を学びます。Aspose.Words ライブラリ以外に外部ツールは必要ありません。

## 前提条件

* .NET 6.0 以降（コードは .NET Framework 4.7 以上でも動作します）
* 有効な Aspose.Words for .NET ライセンスまたは無料評価キー
* Visual Studio 2022（またはお好みの C# IDE）
* C# の構文と Word OLE の概念に関する基本的な知識

> **プロのコツ:** 無料評価版を使用している場合、生成されたドキュメントには小さな透かしが入ります。ライセンス版では自動的に透かしが除去されます。

## 手順 1: Aspose.Words のインストール

NuGet を使用して Aspose.Words パッケージをプロジェクトに追加します:

```bash
dotnet add package Aspose.Words
```

このパッケージには OLE コントロールに必要な `Aspose.Words.Drawing` と `Aspose.Words.Drawing.Ole` 名前空間が含まれています。

## 手順 2: DocumentBuilder を使用して OLE コマンド ボタンを挿入する

このチュートリアルの中心となるのは `InsertForms2OleControl` メソッドです。特定の位置とサイズで **Forms2 OLE CommandButton** を作成します。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System.Drawing;

// Create a new blank document and a DocumentBuilder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Define the rectangle where the button will appear (x, y, width, height)
// Values are in points (1 point = 1/72 inch)
Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

// Insert the Forms2 OLE CommandButton control
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // <-- OleControlType CommandButton (secondary keyword)
    buttonRect);

// Set the button's caption and name properties
commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";
```

### これが機能する理由

* `DocumentBuilder` はプログラムで Word ドキュメントを構築するための主要 API です。  
* `InsertForms2OleControl` は Aspose.Words に **Forms2 OLE コントロール** を埋め込むよう指示します。これはコマンドボタンやチェックボックスなどをサポートする従来の Word フォーム技術です。  
* `OleControlType.CommandButton` 列挙値は、挿入されるコントロールが **command button** であることを指定します。これは **insert OLE command button** を求めた際の正確なタイプです。  
* `Rectangle` は視覚的な配置を決定します。レイアウトに合わせて X/Y 座標や幅/高さを調整してください。

## 手順 3: ドキュメントを保存する

ボタンの設定が完了したら、ドキュメントをディスクに書き出します。Aspose.Words がサポートする任意の形式（`.docx`、`.pdf`、`.odt` など）を選択できます。このチュートリアルでは Word ドキュメントとして保存します。

```csharp
// Choose a folder you have write access to
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");

// Save the document containing the button
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

`CommandButton.docx` を Microsoft Word で開くと、**Click Me** とラベル付けされたクリック可能なボタンが表示されます。Word でボタンを押すとデフォルトの「マクロの実行」ダイアログが起動します。これはボタンが OLE フォームコントロールであるためです。必要に応じて後でマクロや VBA コードを割り当てることができます。

## 手順 4: 結果の確認（期待される出力）

生成されたファイルを開きます:

1. ボタンは指定した座標に表示されます（ページ左上から約 1.4 インチ）。  
2. キャプションは **Click Me** と表示されます。  
3. 名前プロパティ（`cmdSubmit`）は Word の **Developer → Properties** ペインに表示されます。VBA からコントロールを参照する際に便利です。

![Word ドキュメント内の OLE コマンド ボタン挿入例](insert-ole-button.png)

*画像の代替テキスト*: **Word ドキュメント内の OLE コマンド ボタン挿入例**（アクセシビリティと SEO のための主要キーワードを含む）。

## エッジケースとよくある質問

### 1. ボタンが期待した位置に表示されない場合は？

* Word はピクセルではなくポイントを使用します。画面ピクセルをポイントに変換してください（`points = pixels * 72 / DPI`）。  
* 矩形がページ余白と交差しないようにしてください。交差すると Word がコントロールを移動させることがあります。

### 2. 既存のドキュメントにボタンを挿入できますか？

はい。`new Document("Existing.docx")` でドキュメントを読み込み、同じ `DocumentBuilder` のワークフローを使用します。`InsertForms2OleControl` を呼び出す前に、ビルダーのカーソルを移動すること（`builder.MoveToDocumentEnd()`、`builder.MoveToBookmark("myBookmark")` など）を忘れないでください。

### 3. ボタンにマクロを割り当てるには？

Aspose.Words は VBA コードを生成しませんが、ドキュメント生成後にマクロを埋め込むことができます:

```csharp
// Load the generated document
Document doc = new Document(outputPath);

// Add a VBA macro module (requires Aspose.Words licensing)
doc.VbaProject.Modules.Add("Module1", "Sub cmdSubmit_Click()\n MsgBox \"Button clicked!\"\nEnd Sub");

// Save again
doc.Save(outputPath);
```

### 4. .NET Core on Linux でも動作しますか？

OLE コントロールは COM に依存するため Windows 固有の機能です。Linux ではボタンは挿入されますが、インタラクティブな動作はなく静的な画像として表示されます。クロスプラットフォームでインタラクティブなフォームが必要な場合は、コンテンツコントロール（`StructuredDocumentTag`）の使用を検討してください。

### 5. 異なるサイズや複数のボタンが必要な場合は？

ユニークな座標を持つ追加の `Rectangle` オブジェクトを作成し、`InsertForms2OleControl` 呼び出しを繰り返します。各ボタンはそれぞれ独自の `Caption` と `Name` を持つことができます。

## 完全な動作例

以下はコンソールアプリケーションにコピー＆ペーストできる完全なプログラムです。必要な `using` ディレクティブ、エラーハンドリング、コメントがすべて含まれています。

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

namespace OleCommandButtonDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document
                Document document = new Document();
                DocumentBuilder builder = new DocumentBuilder(document);

                // 2️⃣ Define button rectangle (x, y, width, height) in points
                Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

                // 3️⃣ Insert the Forms2 OLE CommandButton control
                Forms2OleControl commandButton = builder.InsertForms2OleControl(
                    OleControlType.CommandButton,
                    buttonRect);

                // 4️⃣ Set visual properties
                commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
                commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";

                // 5️⃣ Save the document
                string outputPath = Path.Combine(
                    Environment.CurrentDirectory,
                    "CommandButton.docx");

                document.Save(outputPath);
                Console.WriteLine($"Document saved successfully: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Error: {ex.Message}");
            }
        }
    }
}
```

プログラムを実行し、生成された `CommandButton.docx` を開くと、**Click Me** ボタンが表示され、さらにカスタマイズできる状態になっています。

## 結論

これで C# と Aspose.Words を使用して Word ドキュメントに **insert OLE command button** を挿入する方法が分かりました。このチュートリアルでは以下をカバーしました:

* Aspose.Words パッケージのインストール  
* `OleControlType.CommandButton` を使用した `DocumentBuilder.InsertForms2OleControl` の利用  
* ボタンプロパティ（`Caption`、`Name`）の設定  
* 出力の保存と検証  

ここからは、チェックボックスやコンボボックス、Excel ワークシート全体の埋め込みなどに使用できる **Aspose.Words OLE control** などの関連トピックを探求できます。また、より大規模なテンプレートで **Word OLE command button** の自動化を試したり、クロスプラットフォーム対応を向上させるために OLE コントロールを最新の **content controls** に置き換えることも検討できます。

矩形の値を調整したり、複数のボタンを追加したり、VBA マクロを割り当ててアプリケーションの要件に合わせて自由にカスタマイズしてください。コーディングを楽しんでください！

## 次に学ぶべきことは？

以下のチュートリアルは本ガイドで示した手法に基づく、密接に関連したトピックを取り上げています。各リソースには完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得し、プロジェクトでの代替実装方法を検討するのに役立ちます。

- [Word ドキュメントに Ole オブジェクトを挿入する](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object/)
- [Word ドキュメントに Ole オブジェクトをアイコンとして挿入する](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon/)
- [Ole パッケージを使用して Word に Ole オブジェクトを挿入する](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}