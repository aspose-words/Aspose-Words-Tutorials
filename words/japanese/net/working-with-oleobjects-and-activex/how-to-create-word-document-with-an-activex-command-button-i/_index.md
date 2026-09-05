---
category: general
date: 2026-09-05
description: Aspose.Words C# を使用して Word 文書を作成し、ActiveX コマンドボタンの挿入方法、ボタンサイズの設定、インタラクティブなボタン機能の追加方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to insert activex
- add command button
- add interactive button
- set button size
language: ja
lastmod: 2026-09-05
og_description: C#でWord文書を作成し、ActiveXコマンドボタンを挿入します。このチュートリアルでは、ボタンのサイズ設定方法とインタラクティブなボタン機能の追加方法を示します。
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
  created with C#
og_title: C#でActiveXコマンドボタン付きWord文書を作成する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  headline: How to create Word document with an ActiveX command button in C#
  type: TechArticle
- description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  name: How to create Word document with an ActiveX command button in C#
  steps:
  - name: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
    text: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
  - name: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
    text: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
  - name: '**Configure the button** – caption, size, and position.'
    text: '**Configure the button** – caption, size, and position.'
  - name: '**Save** the document to disk.'
    text: '**Save** the document to disk.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
- UI controls
title: C#でActiveXコマンドボタン付きのWord文書を作成する方法
url: /ja/net/working-with-oleobjects-and-activex/how-to-create-word-document-with-an-activex-command-button-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で ActiveX コマンドボタン付き Word 文書を作成する方法

プログラムで **Word 文書を作成** し、クリック可能な UI 要素を埋め込む必要がある場合、このガイドで具体的な手順を示します。Aspose.Words for .NET を使用すれば、**Word 文書を作成**、**コマンドボタンを追加**、外観の制御がすべて Microsoft Word を開かずに行えます。

**ActiveX** コントロールの挿入方法、**ボタンサイズの設定**、インタラクティブな UI コンポーネントとしてのボタンの動作方法を学べます。COM や VBA の事前経験は不要で、.NET 開発環境と Aspose.Words ライブラリさえあれば始められます。

## このチュートリアルで達成できること

* **Word 文書を作成**（C# でゼロから）。
* **ActiveX コマンドボタンを挿入**（従来の “Click Me” コントロール）。
* **ボタンサイズ** と位置を正確に設定。
* 必要に応じてシンプルな **インタラクティブ ボタン** ロジックを追加（例: マクロ プレースホルダー）。
* ファイルを `.docx` として保存し、Microsoft Word または互換ビューアで開けます。

### 前提条件

| Requirement | Reason |
|-------------|--------|
| .NET 6.0 以降 | C# コードのランタイムを提供します。 |
| Aspose.Words for .NET（最新バージョン） | サンプルで使用する `Document`、`DocumentBuilder`、`Forms2OleControl` API を提供します。 |
| Visual Studio 2022（または任意の C# IDE） | サンプルのコンパイルと実行が容易になります。 |
| 基本的な C# の知識 | コードの流れを理解するために必要です。 |

> **プロのコツ:** Aspose.Words のトライアル版を使用している場合、評価用の透かしが入らないようにコード実行前にライセンスを設定してください。

## Word 文書作成の全体ワークフロー

このプロセスは 4 つの論理的なステップで構成されます。

1. **新しいドキュメントを初期化**し、編集用に `DocumentBuilder` を作成します。  
2. `InsertForms2OleControl` を使用して **ActiveX コマンドボタンを挿入**。  
3. **ボタンを設定** – キャプション、サイズ、位置。  
4. ドキュメントをディスクに **保存**。

各ステップは以下のセクションで個別に説明します。

![ActiveX ボタン付き Word 文書](/images/activex-button.png "C# で作成された ActiveX コマンドボタンを含む Word 文書のスクリーンショット")

## ActiveX コマンドボタンの挿入方法

**ActiveX の挿入方法** のパートは `InsertForms2OleControl` メソッドから始まります。このメソッドは COM ベースのコントロールを作成し、Word はそれを ActiveX オブジェクトとして扱います。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// 1️⃣ Create a blank document and a builder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 2️⃣ Insert an ActiveX CommandButton control.
//    Parameters: control type, width, height, left, top (all in points).
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // ActiveX type
    150,                           // Width (points)
    100,                           // Height (points)
    50,                            // Left offset from page margin
    50);                           // Top offset from page margin
```

**この動作の理由:** `OleControlType.CommandButton` は Aspose.Words に従来の VB スタイルのボタンを作成するよう指示します。サイズと位置はポイント単位で指定され（1 ポイント = 1/72 インチ）、レイアウトを正確に制御できます。

## コマンドボタンの追加とボタンサイズの設定方法

コントロールを挿入した後、視覚的プロパティを調整できます。**コマンドボタンの追加** のステップでは **ボタンサイズの設定** も扱います。

```csharp
// 3️⃣ Set the button's caption – the text the user sees.
commandButton.Caption = "Click Me";

// 4️⃣ Optionally change size after insertion (if you need dynamic sizing).
//    Width and height are mutable properties.
commandButton.Width = 200;   // New width in points
commandButton.Height = 80;   // New height in points

// 5️⃣ Move the button if you need a different position.
commandButton.Left = 100;    // New left offset
commandButton.Top = 120;     // New top offset
```

**説明:**  

* `Caption` はボタンに表示されるラベルです。  
* `Width` と `Height` は、初期挿入後に **ボタンサイズを設定** でき、実行時データにサイズが依存する場合に便利です。  
* `Left` と `Top` は、ドキュメントを再作成せずにコントロールの位置を再配置します。

> **よくある落とし穴:** ピクセルではなくポイントを使用し忘れると、ボタンが小さすぎたり大きすぎたりします。画面測定値から始める場合は常にピクセル値を（`px * 72 / DPI`）に変換してください。

## インタラクティブ ボタンの追加（オプション）

ActiveX ボタンはクリック時にマクロを実行できますが、C# から VBA コードを埋め込むことは純粋な Aspose.Words のワークフローの範囲外です。その代わりに、Word がマクロ名として認識するプレースホルダー プロパティを追加できます。

```csharp
// 6️⃣ Assign a macro name (the macro must exist in the Word template).
commandButton.OleFormat.Object = "MyMacroName";
```

ユーザーが生成された `.docx` を Word で開くと、ボタンをクリックした際に `MyMacroName` の実行が試みられます。マクロが存在しない場合、Word は作成を促すダイアログを表示します。

**この機能を使用する理由:** フィールドを埋めるマクロが必要な企業用フォームでは、C# コードはボタンを配置するだけで済み、マクロロジックは文書の VBA プロジェクトに存在します。

## ドキュメントの保存と結果の確認

```csharp
// 7️⃣ Save the document to the desired folder.
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "CommandButton.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

**期待される出力:** Microsoft Word で `CommandButton.docx` を開くと、**Click Me** とラベル付けされたボタンが左余白から 100 pts、上余白から 120 pts の位置に表示されます。ボタンのサイズは **200 pts × 80 pts** です。ボタンをクリックすると（存在すれば）マクロのプレースホルダーが実行されます。

## 完全な動作例

以下は、すべてを組み合わせた完全な実行可能プログラムです。新しいコンソール アプリ プロジェクトにコピーし、Aspose.Words の NuGet パッケージを追加して実行してください。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton, // ActiveX type
            150,                         // Initial width
            100,                         // Initial height
            50,                          // Left offset
            50);                         // Top offset

        // Set button caption and resize.
        commandButton.Caption = "Click Me";
        commandButton.Width = 200;   // Set button size (width)
        commandButton.Height = 80;   // Set button size (height)
        commandButton.Left = 100;    // Re‑position horizontally
        commandButton.Top = 120;     // Re‑position vertically

        // Optional: link to a macro named MyMacroName.
        commandButton.OleFormat.Object = "MyMacroName";

        // Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

プログラムを実行し、生成されたファイルを開きます。**インタラクティブ ボタン** が表示され、さらにカスタマイズできる状態になっています。

## よくある質問

| Question | Answer |
|----------|--------|
| **.NET Core でも動作しますか？** | はい。Aspose.Words は .NET Standard をサポートしているため、同じコードが .NET 5/6/7 でも動作します。 |
| **他の ActiveX コントロール（例: CheckBox）も使用できますか？** | もちろんです。`OleControlType.CommandButton` を `OleControlType.CheckBox`、`OleControlType.OptionButton` などに置き換えてください。 |
| **横向きページでより大きなボタンが必要な場合はどうすればよいですか？** | `Width`、`Height`、`Left`、`Top` プロパティを比例的に調整します。ページの向きに関係なくポイントは同じであることを忘れないでください。 |
| **ボタンをクリック可能にするためにマクロは必要ですか？** | いいえ。ボタンは UI 要素として完全に機能します。マクロはクリック時にカスタム動作を追加するだけです。 |

## 結論

これで、Aspose.Words を使用して **Word 文書を作成**、**コマンドボタンを追加**、**ボタンサイズを設定**、そしてオプションでボタンをマクロにリンクして **インタラクティブ ボタン** の動作を実現する方法が分かりました。この手法により、フォーム作成の自動化、動的レポートの生成、または C# から直接 Word ベースの UI プロトタイプを構築できます。

次に、以下を検討してみてください：

* **アンケートフォーム用の ActiveX チェックボックスの挿入方法**。  
* `DocumentBuilder` を使用してボタン周囲に **リッチテキスト コンテンツを追加**する方法。  
* ボタンを機能させたまま **文書を保護**する方法。  

さまざまなコントロールタイプ、サイズ、マクロ名を試して、特定のシナリオに合わせてみてください。コーディングを楽しんで！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装方法を検討するのに役立ちます。

- [Aspose.Words for .NET を使用した Word 文書の作成](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Aspose.Words を使用した Word 文書へのインライン画像挿入](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Aspose.Words を使用した表付き Word 文書の作成](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}