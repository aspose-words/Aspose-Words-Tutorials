---
category: general
date: 2026-09-11
description: Aspose.Words DocumentBuilder を使用してコードで forms2olecontrol を作成する方法を学びます。このステップバイステップガイドでは、ActiveX
  コマンドボタンの挿入、setOleClassName の使用、サイズ設定について説明します。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create forms2olecontrol in code
- ActiveX command button
- Aspose.Words DocumentBuilder
- setOleClassName method
- Forms2OleControl size
language: ja
lastmod: 2026-09-11
og_description: Aspose.Words を使用してコードで forms2olecontrol を作成します。このガイドに従って ActiveX コマンドボタンを挿入し、クラス名を設定し、サイズを調整してください。
og_image_alt: Screenshot of a Word document showing a newly created ActiveX command
  button inserted via code
og_title: コードで forms2olecontrol を作成する – 完全な Aspose.Words ガイド
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  headline: How to create forms2olecontrol in code with Aspose.Words
  type: TechArticle
- description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  name: How to create forms2olecontrol in code with Aspose.Words
  steps:
  - name: Initialise the DocumentBuilder
    text: The `DocumentBuilder` class is the entry point for most document‑generation
      tasks in Aspose.Words. It gives you methods to add text, images, tables, and,
      importantly for this tutorial, OLE controls.
  - name: Insert the Forms2OleControl
    text: The `insertForms2OleControl` method returns a `Forms2OleControl` object.
      This object represents the OLE control placeholder that Word will render as
      an ActiveX button.
  - name: Specify the ActiveX class with setOleClassName
    text: Word needs to know which type of ActiveX control to render. The class name
      for a standard command button is `"Forms.CommandButton.1"`.
  - name: Adjust the Forms2OleControl size
    text: A button that is too small or too large looks unprofessional. You can control
      its dimensions with `setWidth` and `setHeight`.
  - name: Save the document and test
    text: After configuring the control, save the document to a location of your choice.
  - name: When to use Forms2OleControl vs. Content Controls
    text: If you only need simple data entry (e.g., a plain text field), Word’s built‑in
      content controls are lighter weight. Use `Forms2OleControl` when you require
      full ActiveX functionality such as event handling or custom VBA interaction.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Aspose.Words を使用してコードで forms2olecontrol を作成する方法
url: /ja/java/using-document-elements/how-to-create-forms2olecontrol-in-code-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words を使用したコードで forms2olecontrol を作成する方法

コードで **forms2olecontrol を作成** する必要がある場合、このガイドでは Aspose.Words .NET API を使用して正確に行う方法を示します。ActiveX コマンドボタンが必要なテンプレートを自動化する場合でも、単にプログラムで Word ドキュメントを拡張したい場合でも、以下の手順でコントロールの挿入から外観の設定までをすべてカバーしています。

このチュートリアルでは **Aspose.Words DocumentBuilder** を使用して **ActiveX command button** を挿入し、**setOleClassName メソッド** でクラスを設定し、**Forms2OleControl size** を調整する方法を学びます。外部ツールは不要で、.NET 開発環境と Aspose.Words ライブラリさえあれば始められます。

## Prerequisites

開始する前に、以下が揃っていることを確認してください。

* .NET 6.0 以降がインストールされていること（コードは .NET Framework 4.7+ でも動作します）
* 最新バージョンの Aspose.Words for .NET NuGet パッケージ
* C# の基本的な知識と、Word 文書における ActiveX コントロールの概念に慣れていること

これらのいずれかが不足している場合は、次のコマンドで NuGet パッケージをインストールしてください。

```bash
dotnet add package Aspose.Words
```

## What this tutorial covers

* `DocumentBuilder` インスタンスの作成
* `Forms2OleControl` の挿入（ActiveX コマンドボタンの基礎オブジェクト）
* `setOleClassName` で正しいクラス名を設定
* **Forms2OleControl size** プロパティを使用して幅と高さを設定
* ドキュメントを保存し、結果を確認

ガイドの最後まで読むと、クリック可能なボタンを含む完全に機能する Word ファイルが作成でき、さらにカスタマイズしたり VBA マクロにバインドしたりできます。

---

## How to create forms2olecontrol in code – step‑by‑step

### Step 1: Initialise the DocumentBuilder

`DocumentBuilder` クラスは Aspose.Words におけるほとんどの文書生成タスクのエントリーポイントです。テキスト、画像、テーブルの追加はもちろん、このチュートリアルで重要になる OLE コントロールの操作も提供します。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Initialise the builder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

**この点が重要な理由:**  
`DocumentBuilder` は文書内の現在のカーソル位置を保持します。早期にインスタンス化しておくことで、後続の挿入（たとえば **ActiveX command button**）が期待通りの位置に配置されます。

### Step 2: Insert the Forms2OleControl

`insertForms2OleControl` メソッドは `Forms2OleControl` オブジェクトを返します。このオブジェクトは Word が ActiveX ボタンとしてレンダリングする OLE コントロールのプレースホルダーを表します。

```csharp
// Insert the Forms2OleControl at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

**この点が重要な理由:**  
この呼び出しがなければコントロールのプロパティを操作できません。返される `Forms2OleControl` により、**setOleClassName メソッド**、サイズ属性、その他 OLE 固有の設定にフルアクセスできます。

### Step 3: Specify the ActiveX class with setOleClassName

Word はどのタイプの ActiveX コントロールをレンダリングするかを知る必要があります。標準的なコマンドボタンのクラス名は `"Forms.CommandButton.1"` です。

```csharp
// Tell Word that this OLE control is a CommandButton
commandButton.SetOleClassName("Forms.CommandButton.1");
```

**この点が重要な理由:**  
`setOleClassName` メソッドは汎用 OLE プレースホルダーと具体的な **ActiveX command button** を結びつける橋渡しです。クラス名が間違っていると、空のオブジェクトになるか、ドキュメントを開いたときに実行時エラーが発生します。

### Step 4: Adjust the Forms2OleControl size

サイズが小さすぎても大きすぎてもプロフェッショナルに見えません。`setWidth` と `setHeight` で寸法を制御できます。

```csharp
// Set the visual dimensions (points) of the button
commandButton.SetWidth(80);   // width in points
commandButton.SetHeight(30);  // height in points
```

**この点が重要な理由:**  
これらのプロパティが **Forms2OleControl size** を構成します。ボタンの見た目に影響し、添付したマクロが十分なクリック領域を持つことを保証します。

### Step 5: Save the document and test

コントロールの設定が完了したら、任意の場所にドキュメントを保存します。

```csharp
// Save the document as a .docx file
doc.Save("ActiveXButton.docx");
```

`ActiveXButton.docx` を Microsoft Word で開きます。デフォルトのキャプション「CommandButton1」が付いたボタンが表示されるはずです。VBA マクロを追加しない限りクリックしても何も起こりませんが、コントロール自体は完全に機能しています。

**期待される出力:**  

![ActiveX コマンドボタンが挿入された Word ドキュメント](/images/activeX-button.png "コードで新しく作成された ActiveX コマンドボタンが挿入された Word ドキュメントのスクリーンショット")

*画像の alt テキストはアクセシビリティと SEO のために主要キーワードを含んでいます。*

---

## Understanding the ActiveX Forms2OleControl class

`Forms2OleControl` クラスは Word が ActiveX 要素に使用する低レベル OLE インフラストラクチャをラップしています。`Shape` から継承しているため、必要に応じて通常のシェイプ書式設定（枠線、回転など）も適用できます。

* **ActiveX command button** – 最も一般的な使用例です。Word の開発者ツールを使ってマクロにバインドできます。
* **setOleClassName method** – Word がロードする COM クラスを決定します。他の有効な値には `"Forms.TextBox.1"` や `"Forms.ComboBox.1"` があります。
* **Forms2OleControl size** – `SetWidth`/`SetHeight` で制御します。これらのメソッドはポイント単位を受け取ります（1 pt = 1/72 in）。

### When to use Forms2OleControl vs. Content Controls

単純なデータ入力（例: プレーンテキストフィールド）のみが必要な場合は、Word の組み込みコンテンツコントロールの方が軽量です。イベント処理やカスタム VBA 連携など、フル ActiveX 機能が必要なときに `Forms2OleControl` を使用します。

---

## Setting additional properties (optional)

コア手順だけでも **forms2olecontrol をコードで作成** できますが、ボタンの外観や動作を細かく調整したくなることが多いでしょう。

```csharp
// Change the button caption (requires a VBA macro to read it)
commandButton.SetOleData("Caption", "Submit");

// Disable the button initially
commandButton.SetOleData("Enabled", false);

// Add a tooltip
commandButton.SetOleData("ToolTipText", "Click to submit the form");
```

**この点が重要な理由:**  
`SetOleData` を使うと OLE ストリームに任意のプロパティ値を書き込めます。VBA に頼らず **ActiveX command button** を柔軟にカスタマイズできる最も柔軟な方法です。

---

## Common pitfalls and troubleshooting

| 症状 | 考えられる原因 | 対策 |
|--------|--------------|-----|
| ボタンが灰色のボックスとして表示される | `setOleClassName` に渡されたクラス名が間違っている | 文字列が正確に `"Forms.CommandButton.1"`（大文字小文字を区別）であることを確認してください |
| サイズが変更されない | コントロールを挿入する前に幅/高さを設定している | `InsertForms2OleControl` の **後** に必ず `SetWidth`/`SetHeight` を呼び出す |
| ドキュメントを開くと “OLE object not found” エラーが出る | Aspose.Words のライセンスがない（評価版では OLE が制限される可能性がある） | 有効なライセンスを適用するか、フル OLE サポート付きの無料トライアルを使用する |
| ボタンのキャプションが “CommandButton1” のままになる | `SetOleData` が使用されていない、またはマクロがプロパティを読み取っていない | VBA マクロで `"Caption"` プロパティを読み取るか、Word UI でキャプションを設定してください |

---

## Full, runnable example

以下はコンソールアプリケーションの完全なサンプルです。コピーして貼り付け、実行できます。この例は本チュートリアルで説明したすべての内容を示しています。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace Forms2OleControlDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1. Create a new document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2. Insert the Forms2OleControl (ActiveX placeholder)
            Forms2OleControl commandButton = builder.InsertForms2OleControl();

            // 3. Set the ActiveX class to CommandButton
            commandButton.SetOleClassName("Forms.CommandButton.1");

            // 4. Define the visual size of the button
            commandButton.SetWidth(80);   // 80 points = ~1.11 inches
            commandButton.SetHeight(30);  // 30 points = ~0.42 inches

            // Optional: set a custom caption via OLE data (requires VBA to read)
            commandButton.SetOleData("Caption", "Submit");

            // 5. Save the document
            string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**各セクションの説明**

* **Using ディレクティブ** – `Document`、`DocumentBuilder`、`Forms2OleControl` に必要な Aspose.Words 名前空間をインポートします。
* **Document 作成** – 空の Word ファイルをインスタンス化します。
* **InsertForms2OleControl** – ビルダーの現在のカーソル位置に OLE コントロールを配置します。
* **SetOleClassName** – コントロールが **ActiveX command button** であることを Word に指示します。
* **SetWidth / SetHeight** – プロフェッショナルな外観になるよう **Forms2OleControl size** を調整します。
* **SetOleData（オプション）** – キャプションなどの追加プロパティを書き込む方法を示します。
* **Save** – 最終的な `.docx` ファイルをディスクに書き込みます。

プログラムを実行（`dotnet run`）し、`ActiveXButton.docx` を開くと、後でマクロにリンクできるボタンが表示されます。

---

## Conclusion

これで **forms2olecontrol をコードで作成** する方法を Aspose.Words を使って習得しました。`DocumentBuilder` の初期化から **ActiveX command button** の `setOleClassName` 設定、そして **Forms2OleControl size** の制御までを網羅しています。このアプローチにより、複雑な Word 文書を自動化し、インタラクティブな UI 要素を埋め込み、ロジックをすべてコード内に保持できます

## What Should You Learn Next?

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、独自プロジェクトで代替実装を検討したりするのに役立ちます。

- [Java 用 Aspose.Words の DocumentBuilder でフォームフィールドを作成しコンテンツを追加する方法](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words for .NET を使用して Word ドキュメントにグループ シェイプを作成する](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words で Word に矩形シェイプを作成する – ステップバイステップ ガイド](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}