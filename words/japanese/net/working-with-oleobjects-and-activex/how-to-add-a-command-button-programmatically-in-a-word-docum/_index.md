---
category: general
date: 2026-10-13
description: Aspose.Words を使用してプログラムでコマンドボタンを追加する方法を学びます。このガイドでは、完全な C# コードで Word
  文書のボタンを作成する方法も示しています。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button programmatically
- create word document button
language: ja
lastmod: 2026-10-13
og_description: Aspose.Words を使用して、Word 文書にプログラムでコマンド ボタンを追加します。この完全なチュートリアルに従って、C#
  で Word 文書のボタンを作成してください。
og_image_alt: Screenshot of a Word document with a command button inserted programmatically
og_title: Word文書にコマンドボタンをプログラムで追加する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  headline: How to add a command button programmatically in a Word document
  type: TechArticle
- description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  name: How to add a command button programmatically in a Word document
  steps:
  - name: 'Create a new console project:'
    text: 'Create a new console project:'
  - name: 'Add the Aspose.Words NuGet package:'
    text: 'Add the Aspose.Words NuGet package:'
  - name: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
    text: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Word文書にプログラムでコマンドボタンを追加する方法
url: /ja/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word ドキュメントにコマンド ボタンをプログラムで追加する方法  

プログラムでコマンド ボタンを **追加する** 必要がある場合、Aspose.Words は OLE フォーム コントロールを .docx ファイルに直接埋め込むことができるシンプルな API を提供します。このチュートリアルでは、Microsoft Word でドキュメントを開いたときに通常のフォーム ボタンと同様に動作する **Word ドキュメント ボタンの作成** に必要なすべての手順を解説します。  

開発環境の設定方法、ボタンの挿入、プロパティの構成、結果の検証方法を学べます。外部ユーティリティは不要で、.NET プロジェクトと Aspose.Words for .NET ライブラリだけで完了します。  

## 前提条件  

開始する前に、以下が揃っていることを確認してください：  

* .NET 6.0 SDK 以降がインストールされていること。  
* Aspose.Words for .NET の最新バージョン（例では 23.12 を使用していますが、22.x 以降のリリースであれば動作します）。  
* Visual Studio 2022 や Visual Studio Code などの IDE。  

Aspose.Words はプラットフォームに依存しないため、コードは Windows、macOS、Linux で実行できます。  

## 手順 1: プロジェクトをセットアップし Aspose.Words を参照する  

1. 新しいコンソール プロジェクトを作成します：  

   ```bash
   dotnet new console -n WordButtonDemo
   cd WordButtonDemo
   ```  

2. Aspose.Words NuGet パッケージを追加します：  

   ```bash
   dotnet add package Aspose.Words
   ```  

3. **Program.cs** を開き、次の手順で示す雛形に内容を置き換えます。  

このようにプロジェクトを設定すると、フォーム コントロールに必要な `Aspose.Words` と `Aspose.Words.Drawing.Forms` 名前空間をコンパイラが正しく見つけられるようになります。  

## 手順 2: 空のドキュメントと DocumentBuilder を初期化する  

`Document` クラスは Word ファイル全体を表し、`DocumentBuilder` はコンテンツ追加用のフルエント API を提供します。  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;
using System.Drawing;   // required for RectangleF

// Create an empty document.
Document doc = new Document();

// Create a builder linked to the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```  

*この手順が重要な理由* – `DocumentBuilder` がなければ、ページ上でボタンを正確に配置できません。ビルダーは現在のカーソル位置を考慮するため、後で複数のコントロールを挿入するのが容易になります。  

## 手順 3: コマンド ボタン OLE コントロールを挿入する  

Aspose.Words はコマンド ボタンを `ControlType.CommandButton` タイプの OLE コントロールとして扱います。位置とサイズはポイント単位（1 ポイント = 1/72 インチ）で測定した `RectangleF` で指定します。  

```csharp
// Define the button rectangle: X=100, Y=150, Width=120, Height=30 (points)
RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

// Insert the command button at the current cursor position.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    buttonRect);
```  

**重要ポイント**  

* 矩形の原点 (X, Y) はページ左上隅を基準とします。  
* `Width` または `Height` を変更すると、ボタンの表示サイズが変わります。  
* `InsertForms2OleControl` は、さらに構成可能な `Forms2OleControl` オブジェクトを返します。  

## 手順 4: ボタンの名前とキャプションを設定する  

**name** は Word のマクロ エンジンがコントロールを識別するために使用され、**caption** はユーザーに表示されるテキストです。  

```csharp
// Set a unique identifier for the button.
commandButton.Name = "cmdSubmit";

// Set the text displayed on the button.
commandButton.Caption = "Submit";
```  

後で VBA マクロを追加する予定がある場合は、Word のマクロ レコーダがこのプロパティを参照するため、分かりやすい名前を付けてください。  

## 手順 5: （オプション）ドキュメントを保存し結果を確認する  

ファイルを保存すると、Microsoft Word で開いてボタンが表示され機能することを確認できます。  

```csharp
// Save the document to the output folder.
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButtonDemo.docx");
doc.Save(outputPath);

Console.WriteLine($"Document saved to: {outputPath}");
```  

Word で *CommandButtonDemo.docx* を開くと、左余白から約 1.4 インチ、ページ上部から約 2.1 インチの位置に **Submit** とラベル付けされたボタンが表示されます。デフォルトではマクロが割り当てられていないためクリックしても何も起こりませんが、ビジュアル コントロールは完全に機能しています。  

## 手順 6: エッジケースと一般的な落とし穴  

| 状況 | 注意点 | 推奨される対策 |
|-----------|-------------------|-----------------|
| **ボタンが既存のテキストと重なる** | 矩形が段落と交差し、レイアウトの問題が発生する可能性があります。 | `builder.Writeln()` を呼び出してカーソルを新しい行に移動した後にボタンを挿入するか、`Y` 座標を調整してください。 |
| **ドキュメントを開くと警告が表示される** | 一部の Word バージョンでは、リンクされたプログラムがない OLE コントロールに警告が付くことがあります。 | コントロールのタイプが `CommandButton` であることを確認してください。Word は標準的なフォーム要素として扱い、外部プログラムは不要です。 |
| **ヘッドレス環境の Linux で実行** | UI をテストするために Word を起動できませんが、ファイル自体は有効です。 | `commandButton.Name`、`commandButton.Caption` などコントロールのプロパティを読み取るユニットテストを使用して、正しく設定されたことを検証してください。 |
| **複数のボタンが必要** | カーソルを移動せずに同じ `DocumentBuilder` を再利用すると、前のボタンの上に新しいボタンが重なります。 | 各挿入前に `builder.MoveToDocumentEnd()` を呼び出すか、矩形の `Y` 値を調整してください。 |

これらのエッジケースに早期に対処することで、数十個のコントロールを持つフルフォームへスケールする際の時間を節約できます。  

## 手順 7: 完全な実行可能サンプル  

以下は、NuGet の復元以外は変更せずにコピー・貼り付け・実行できる自己完結型プログラムです。  

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

namespace WordButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a new empty document.
            Document doc = new Document();

            // 2. Create a DocumentBuilder to work with the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Define the button rectangle (position + size).
            RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

            // 4. Insert the command button OLE control.
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                buttonRect);

            // 5. Set identifying properties.
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // 6. Save the document.
            string outputPath = Path.Combine(
                Environment.CurrentDirectory,
                "CommandButtonDemo.docx");
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

**期待される出力**  

プログラムを実行すると、以下のようなパスが出力されます：  

```
Document saved to: C:\Path\To\WordButtonDemo\CommandButtonDemo.docx
```  

生成された *CommandButtonDemo.docx* を開くと、コードで定義した座標に配置された単一の **Submit** ボタンが表示されます。追加の UI 要素は表示されず、**プログラムでコマンド ボタンを追加する** ワークフローが正常に完了したことが確認できます。  

## 結論  

これで、Aspose.Words を使用して Word ドキュメントに **プログラムでコマンド ボタンを追加する** 方法と、後で VBA マクロや外部自動化ツールに接続できる **Word ドキュメント ボタンの作成** 方法が分かりました。手順は、ドキュメントの初期化、OLE `CommandButton` コントロールの挿入、プロパティの設定、ファイルの保存です。  

ここからは、以下のことが考えられます：  

* ステップ 3 を別の `ControlType` 値で繰り返し、チェックボックスやテキスト フィールドなどのコントロールを追加する。  
* ボタンに VBA マクロを割り当て、フォームの保存やメール送信などの操作を実行させる。  
* フィールド定義のデータ駆動コレクションをループして、フォーム全体を動的に生成する。  

矩形座標やボタンのキャプションを試行錯誤して、UI デザインに合わせてください。コーディングを楽しんで！  

## 次に学ぶべきことは？  

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。  

- [Aspose.Words for .NET を使用して Word ドキュメントにコンボ ボックス フォーム フィールドを追加する](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Aspose.Words for .NET を使用して Word ドキュメントにチェック ボックス フォーム フィールドを追加する](/words/english/net/add-content-using-documentbuilder/insert-check-box/)
- [Aspose.Words で空白の Word ドキュメントを作成する – ステップバイステップ ガイド](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}