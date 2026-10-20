---
category: general
date: 2026-07-29
description: Aspose.Words を使用して Word 文書にコマンドボタンを追加します。ActiveX コントロールのプロパティ設定方法と、コマンドボタンのキャプション設定方法を、簡単な手順で学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button to word document
- set activex control properties
- set command button caption
- Aspose.Words ActiveX example
- C# insert ActiveX control
language: ja
lastmod: 2026-07-29
og_description: Aspose.Words を使用して Word 文書にコマンドボタンを追加します。このチュートリアルでは、ActiveX コントロールのプロパティを設定し、コマンドボタンのキャプションをすばやく設定する方法を示します。
og_image_alt: Screenshot of a Word document with a Submit command button inserted
  via C#
og_title: Word文書にコマンドボタンを追加 – Aspose.Words ステップバイステップ
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  headline: Add Command Button to Word Document with Aspose.Words – Complete Guide
  type: TechArticle
- description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  name: Add Command Button to Word Document with Aspose.Words – Complete Guide
  steps:
  - name: Setting the Caption
    text: 'The caption is the text that appears on the button itself. To **set command
      button caption**, simply assign a string to the `Caption` property:'
  - name: Naming the Control
    text: 'Giving the control a meaningful name makes it easier to reference later
      (for example, when automating Word macros). We’ll set the `Name` property:'
  - name: Positioning on the Page
    text: 'Word uses points (1/72 of an inch) for layout. Adjust the `Left` and `Top`
      properties to place the button where you need it:'
  - name: Expected Result
    text: 1. The Word document opens with a single page. 2. A rectangular button labeled
      **Submit** appears at the coordinates you specified. 3. If you right‑click the
      button and choose **Properties**, you’ll see the name `btnSubmit` and other
      properties you set.
  - name: Inserting Other ActiveX Types
    text: 'The `InsertForms2OleControl` method isn’t limited to command buttons. You
      can embed check boxes, option buttons, or even custom ActiveX objects:'
  - name: Handling Word Versions
    text: Older Word versions (pre‑2007) use the binary `.doc` format, which stores
      ActiveX controls differently. Aspose.Words automatically converts the control
      when you save as `.doc`, but some properties (like precise positioning) may
      shift. If you target legacy formats, test the output in the specific Wor
  - name: Security Settings
    text: 'Word may disable ActiveX controls on machines with strict macro security.
      To avoid a “Security Warning” dialog, consider:'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Aspose.Words を使用して Word 文書にコマンドボタンを追加する – 完全ガイド
url: /ja/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 文書にコマンドボタンを追加 – 完全プログラミングウォークスルー

Ever needed to **add command button to word document** but weren’t sure which API calls to use? You’re not alone; many developers hit that wall when they first try to embed interactive controls in a DOCX file. The good news is that Aspose.Words makes it surprisingly painless. In this guide we’ll walk through creating a CommandButton ActiveX control, **set activex control properties**, and **set command button caption**—all with clean C# code you can copy‑paste right now.

Word 文書に **add command button to word document** が必要だったが、どの API 呼び出しを使用すればよいか分からなかったことはありませんか？ あなたは一人ではありません。多くの開発者が DOCX ファイルにインタラクティブなコントロールを埋め込もうとしたときに同じ壁にぶつかります。良いニュースは、Aspose.Words が驚くほど簡単にしてくれることです。このガイドでは、CommandButton ActiveX コントロールの作成、**set activex control properties**、そして **set command button caption** を、すぐにコピー＆ペーストできるクリーンな C# コードで解説します。

このチュートリアルの最後までに、クリック可能な「Submit」ボタンを含む完全に機能する Word ファイルが手に入り、Microsoft Word で開くことができます。外部の VBA スクリプトは不要で、手動の UI 操作も不要です—純粋にプログラムで制御します。

## 学べること

* 空の Word 文書と `DocumentBuilder` の作成方法。
* Aspose.Words を使用して **add command button to word document** を行う正確なメソッド呼び出し。
* サイズ、位置、名前などの **set activex control properties** の方法。
* ボタンに希望通りの文字が表示されるように **set command button caption** を設定する正しい手法。
* 異なるボタンタイプ、DPI スケーリング、Word バージョン互換性などのエッジケースへの対処ヒント。

> **Prerequisite:** Aspose.Words for .NET がインストールされた Visual Studio（または任意の C# IDE）（NuGet パッケージ `Aspose.Words`）。ActiveX の事前経験は不要です。

## 手順 1: プロジェクトの設定と名前空間のインポート

まず **add command button to word document** を行うために、Aspose.Words を参照する C# プロジェクトが必要です。新しい .NET コンソール アプリを作成し、NuGet パッケージを追加します：

```bash
dotnet add package Aspose.Words
```

次に、必要な名前空間をソース ファイルに追加します：

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;
```

これら 3 つの `using` ディレクティブにより、ActiveX 挿入を実現する `Document`、`DocumentBuilder`、`Forms2OleControl` クラスにアクセスできます。

*Pro tip:* Visual Studio を使用している場合、クラス名を入力すると IDE が自動的に追加を提案してくれます。

## 手順 2: 空のドキュメントとビルダーの作成

新しい `Document` オブジェクトは空の Word ファイルを表します。`DocumentBuilder` は、描画やテキスト挿入、そして何より重要な ActiveX コントロールの配置を可能にする便利な「ペン」です。

```csharp
// Initialize a new, empty Word document.
Document doc = new Document();

// Attach a builder to the document for editing.
DocumentBuilder builder = new DocumentBuilder(doc);
```

この時点でドキュメントは単なる空白のキャンバスです—コマンドボタンを待つ白紙の紙と考えてください。

## 手順 3: CommandButton ActiveX コントロールの挿入

いよいよ **add command button to word document** を行います。Aspose.Words は `InsertForms2OleControl` メソッドを提供しており、コントロールの種類とサイズを指定できます。ここでは `Forms2OleControlType.CommandButton` を使用し、幅 150 ポイント、高さ 30 ポイントのサイズを設定します。

```csharp
// Insert a CommandButton ActiveX control with a specific size.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton,
    width: 150,
    height: 30);
```

このメソッドは `Forms2OleControl` インスタンスを返し、次のステップで **set activex control properties** に使用します。

## 手順 4: コントロールの設定 – 名前、キャプション、位置

### キャプションの設定

キャプションはボタン上に表示されるテキストです。**set command button caption** を行うには、単に文字列を `Caption` プロパティに代入します：

```csharp
commandButton.Caption = "Submit";
```

`"Submit"` を好きな文字列（“Save”、 “Export”、 “Launch” など）に変更すれば、Word はその文字列をそのまま表示します。

### コントロールの名前付け

コントロールに意味のある名前を付けることで、後で参照しやすくなります（例: Word マクロの自動化時）。`Name` プロパティを設定します：

```csharp
commandButton.Name = "btnSubmit";
```

### ページ上での位置設定

Word はレイアウトにポイント（1 インチの 1/72）を使用します。`Left` と `Top` プロパティを調整して、ボタンを希望の位置に配置します：

```csharp
commandButton.Left = 100; // 100 points from the left margin
commandButton.Top  = 200; // 200 points from the top of the page
```

ボタンを段落に対して整列させたい場合は、まずビルダーのカーソルを移動させてからコントロールを挿入すると、座標はその位置を基準にします。

*Edge case:* 高 DPI モニターでは、Word 上での見た目のサイズが若干異なる場合があります。デバイス間でボタンの実際のサイズを一定に保つには、対象 DPI（通常 Word は 96 DPI）に基づいてポイントを計算してください。

## 手順 5: ドキュメントの保存

ボタンの設定が完了したら、ファイルの保存はワンライナーです：

```csharp
// Save the document; the ActiveX control is stored inside the DOCX.
doc.Save("CommandButton.docx");
```

生成された `CommandButton.docx` には完全に機能する ActiveX ボタンが含まれます。Microsoft Word で開くと、配置した通りの位置に「Submit」ボタンが表示されます。

### 期待される結果

1. Word 文書が単一ページで開く。
2. 指定した座標に **Submit** とラベル付けされた長方形のボタンが表示される。
3. ボタンを右クリックして **Properties** を選択すると、名前 `btnSubmit` と設定した他のプロパティが表示される。

## 手順 6: 高度なバリエーションと一般的な落とし穴

### 他の ActiveX タイプの挿入

`InsertForms2OleControl` メソッドはコマンドボタンに限定されません。チェックボックス、オプションボタン、さらにはカスタム ActiveX オブジェクトも埋め込めます：

```csharp
// Example: Insert a CheckBox instead of a CommandButton.
Forms2OleControl checkBox = builder.InsertForms2OleControl(
    Forms2OleControlType.CheckBox,
    width: 20,
    height: 20);
checkBox.Name = "chkAgree";
checkBox.Caption = "I Agree";
```

同じ **set activex control properties** パターンが適用されます—タイプ列挙子を入れ替えるだけです。

### Word バージョンの取り扱い

古い Word バージョン（2007 年以前）はバイナリの `.doc` 形式を使用し、ActiveX コントロールの保存方法が異なります。Aspose.Words は `.doc` として保存すると自動的にコントロールを変換しますが、正確な位置など一部のプロパティはずれる可能性があります。レガシーフォーマットを対象とする場合は、対象の Word バージョンで出力をテストしてください。

### セキュリティ設定

Word はマクロセキュリティが厳しい環境では ActiveX コントロールを無効にすることがあります。「セキュリティ警告」ダイアログを回避するために、以下を検討してください：

* 信頼できる証明書で文書に署名する。
* ユーザーにそのファイルの場所で ActiveX コンテンツを有効にするよう指示する。
* セキュリティが懸念される場合は、マクロなしの代替手段（例: プレーンなコンテンツコントロール）を使用する。

## 手順 7: 完全な動作例

以下は、説明したすべての手順を組み込んだ、完全な実行可能プログラムです。`Program.cs` にコピーし、必要に応じて出力パスを調整して **Run** を実行してください。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            width: 150,   // Width in points
            height: 30);  // Height in points

        // Step 3: Set the control's name and caption.
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Step 4: Position the control on the page.
        commandButton.Left = 100; // 100 points from left edge
        commandButton.Top  = 200; // 200 points from top edge

        // Optional: Add a paragraph above the button for context.
        builder.MoveToDocumentEnd();
        builder.Writeln("Click the button below to submit the form:");

        // Step 5: Save the document.
        string outputPath = "CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved successfully to {outputPath}");
    }
}
```

**このコードの動作:**

* 新しいドキュメントから開始する。
* コマンドボタンを挿入し、**sets activex control properties** と **sets command button caption** を行う。
* 簡単な説明段落を追加する。
* ファイルを `CommandButton.docx` として保存する。

プログラムを実行し、生成されたファイルを開くと、説明テキストの下にボタンが配置されているのが確認できます。

## 結論

ここでは、Aspose.Words を使用して **add command button to word document** を行い、**set activex control properties** と **set command button caption** を設定する方法を簡潔で本番環境向けの C# スニペットで示しました。この手法はスケーラブルで、コントロールの種類を変更したり、サイズを調整したり、データソースをループして数十個のボタンを自動的に埋め込むことができます。

さらに進めたいですか？次を試してみてください：

* ボタンをデータエクスポートをトリガーするマクロにバインドする。
* `Picture` プロパティを使用してボタン内に画像やカスタムアイコンを追加する。
* 複数の ActiveX コントロール（テキストボックス、コンボボックスなど）を組み合わせて完全なフォームを構築する。

実験は Word 自動化をマスターする最良の方法です。問題が発生したら、DPI 計算と Word のセキュリティ設定を再確認してください。コーディングを楽しんで、あなたの文書がますますインタラクティブになりますように！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを探求するのに役立ちます。

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}