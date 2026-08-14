---
category: general
date: 2026-08-14
description: Aspose.Words を使用して Word 文書に ActiveX ボタンを追加する方法 – 空の Word 文書を作成し、プログラムで
  ActiveX ボタンを挿入する方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert activex button
- create empty word document
- create word document aspose
language: ja
lastmod: 2026-08-14
og_description: Aspose.Words を使用して Word 文書に ActiveX ボタンを追加する方法。このチュートリアルでは、空の Word
  文書を作成し、ActiveX ボタンを挿入し、結果を保存する手順を示します。
og_image_alt: Screenshot of an ActiveX button inserted into a Word document using
  Aspose.Words
og_title: WordにActiveXボタンを追加する方法 – Aspose.Wordsガイド
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  headline: How to add ActiveX button in a Word document with Aspose.Words
  type: TechArticle
- description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  name: How to add ActiveX button in a Word document with Aspose.Words
  steps:
  - name: Does the button work in all Word versions?
    text: ActiveX controls are supported in the desktop version of Word on Windows.
      They are not rendered in Word Online, Word for macOS, or mobile clients. If
      you need cross‑platform interactivity, consider using content controls or HTML‑based
      solutions instead.
  - name: What if I need a different size or position?
    text: '`InsertForms2OleControl` places the control at the current builder cursor.
      To move it, adjust the cursor with `builder.MoveTo` before insertion, or modify
      the control’s `Left` and `Top` properties after creation:'
  - name: Can I add other ActiveX types?
    text: Yes. The `Forms2OleControlType` enumeration includes `CheckBox`, `OptionButton`,
      `ListBox`, and more. Replace `CommandButton` with the desired enum value and
      adjust properties accordingly.
  - name: Is a macro required for the button to do something?
    text: The button itself does nothing until you attach VBA code. In Word, press
      **Alt+F11** to open the VBA editor, locate `btnSubmit_Click`, and write the
      desired logic. The generated document will retain the VBA project if you enable
      the **SaveFormat.Doc** (legacy `.doc`) format, but `.docx` files cannot
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Word automation
- C#
title: Aspose.Words を使用して Word 文書に ActiveX ボタンを追加する方法
url: /ja/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# WordドキュメントにActiveXボタンを追加する方法（Aspose.Words使用）

生成されたWordファイルに **ActiveXの追加方法** コントロールを追加する必要がある場合、このガイドでは正確な手順を示します。**ActiveXボタンを挿入** する方法をプログラムで学び、**空のWordドキュメントを作成** するところから、Microsoft Wordで開ける保存済みファイルまでをカバーします。

VBAコードを実行したりマクロをトリガーしたりするボタンの追加は、レポート自動生成、フォームテンプレート、インタラクティブ契約書などで一般的な要件です。Aspose.Words for .NET を使用すれば、Office を起動せずにドキュメントを構築でき、処理が高速でサーバーフレンドリーです。

## 前提条件

開始する前に、以下がインストールされていることを確認してください。

* .NET 6.0（またはそれ以降）SDK がインストール済み。
* Visual Studio 2022 または任意の C# 対応 IDE。
* Aspose.Words for .NET NuGet パッケージ（`Aspose.Words` バージョン 24.9 以上）。  
  以下でインストールします:
  ```bash
  dotnet add package Aspose.Words
  ```
* ActiveX ボタンをテストする場合は Windows 環境が必要です。ActiveX コントロールは Windows 版 Microsoft Word が必要です。

## 手順 1: 空のWordドキュメントを作成

最初のタスクはメモリ上に **空のWordドキュメントを作成** することです。Aspose.Words はこの目的のために `Document` クラスを提供しています。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, blank Word document.
Document doc = new Document();
```

`Document` は .docx ファイル全体を表します。この時点ではページはありませんが、すぐにコンテンツの追加を開始できます。

## 手順 2: DocumentBuilder を初期化

`DocumentBuilder` はテキスト、画像、その他のオブジェクトをドキュメントに挿入できるヘルパーです。先ほど作成した `Document` インスタンスで動作します。

```csharp
// Initialise the builder with the blank document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

ビルダーはカーソル位置を保持します。この行の後に挿入したものは、最初のページの先頭に表示されます。

## 手順 3: ActiveX CommandButton コントロールを挿入

Aspose.Words はレガシーフォームコントロール（ActiveX を含む）を追加するために `InsertForms2OleControl` メソッドを公開しています。このメソッドにはコントロールの種類とサイズ（ポイント単位）が必要です。

```csharp
// Insert an ActiveX CommandButton (150x30 points).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

返される `Forms2OleControl` オブジェクトを使用して、コントロールの名前やキャプションなどのプロパティを設定できます。

## 手順 4: ボタンのプロパティを設定

意味のある `Name` を設定すると、後で VBA コードからコントロールを参照できます。`Caption` はユーザーがボタン上で見るテキストです。

```csharp
// Set the button’s programmatic name (used in VBA) and displayed caption.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

> **Pro tip:** 名前は短く英数字のみで保ちましょう。スペースや特殊文字を含む名前は Word に拒否されます。

## 手順 5: ドキュメントを保存

最後に、ドキュメントをディスクに書き出します。最新の Word ファイルには `.docx` 拡張子を使用してください。ActiveX ボタンは `.doc` ファイルでも同様に機能しますが、`.docx` が新規プロジェクトの推奨フォーマットです。

```csharp
// Save the document containing the ActiveX button.
doc.Save(@"C:\Temp\ActiveXButton.docx");
```

`ActiveXButton.docx` を Microsoft Word で開くと、クリック可能な **Submit** ボタンが表示されます。マクロを有効にすれば、`btnSubmit_Click` に VBA コードを割り当て、ユーザーがボタンをクリックしたときに実行させることができます。

## 完全な実行可能サンプル

すべての要素を組み合わせると、コピー＆ペーストして実行できる自己完結型プログラムが完成します。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create an empty Word document.
            Document doc = new Document();

            // Step 2: Initialise DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX CommandButton control.
            Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Step 4: Set button properties.
            cmdBtn.Name = "btnSubmit";
            cmdBtn.Caption = "Submit";

            // Step 5: Save the document.
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Expected output** – プログラム実行後、コンソールに保存場所が表示され、生成されたファイルを Word で開くと、最初のページ上部に **Submit** とラベル付けされたボタンが配置されていることが確認できます。

## よくある質問とエッジケースの対処

### ボタンはすべてのWordバージョンで動作しますか？

ActiveX コントロールは Windows 上のデスクトップ版 Word でサポートされています。Word Online、macOS 用 Word、モバイルクライアントでは表示されません。クロスプラットフォームでのインタラクティブ性が必要な場合は、コンテンツコントロールや HTML ベースのソリューションの使用を検討してください。

### サイズや位置を変更したい場合は？

`InsertForms2OleControl` は現在のビルダーカーソル位置にコントロールを配置します。位置を変更するには、挿入前に `builder.MoveTo` でカーソルを調整するか、作成後にコントロールの `Left` と `Top` プロパティを変更します。

```csharp
cmdBtn.Left = 100;   // points from the left margin
cmdBtn.Top = 200;    // points from the top margin
```

### 他のActiveXタイプを追加できますか？

はい。`Forms2OleControlType` 列挙体には `CheckBox`、`OptionButton`、`ListBox` などが含まれます。`CommandButton` を目的の列挙値に置き換え、必要に応じてプロパティを調整してください。

### ボタンに何かさせるためにマクロは必要ですか？

ボタン自体は VBA コードを割り当てるまで何も実行しません。Word で **Alt+F11** を押して VBA エディタを開き、`btnSubmit_Click` を見つけてロジックを記述します。**SaveFormat.Doc**（レガシー `.doc`）形式で保存すれば VBA プロジェクトが保持されますが、`.docx` ファイルは VBA マクロを格納できません。埋め込み VBA が必要な場合は `.doc` 形式を使用してください。

## 結論

これで Aspose.Words を使用して Word ファイルに **ActiveXの追加方法** が分かりました。**空のWordドキュメントを作成**、`DocumentBuilder` を初期化、**ActiveXボタンを挿入**、プロパティを設定し、ファイルを保存する手順に従うことで、.NET コードから直接インタラクティブな Word テンプレートを生成できます。

次は、**ActiveXボタンのイベントハンドリング**、テーブルや画像用の **create word document aspose** の追加、エンタープライズ展開向けのマクロ有効ドキュメントの保護など、関連トピックを探求してください。さまざまなコントロールタイプやレイアウトオプションを試して、アプリケーションのニーズに合わせたユーザー体験を実現しましょう。

コーディングを楽しんでください！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックをカバーしています。各リソースには、完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Aspose.Words を使用したヘッダーとフッター付き Word ドキュメントの作成](/words/english/net/header-footer-formatting/create-header-footer/)
- [Aspose.Words for .NET を使用した Word ドキュメントへのグループ シェイプの作成](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words を使用したテーブル付き Word ドキュメントの作成](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}