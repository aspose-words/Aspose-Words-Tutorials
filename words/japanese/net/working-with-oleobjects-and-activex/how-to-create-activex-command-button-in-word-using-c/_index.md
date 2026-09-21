---
category: general
date: 2026-09-21
description: Aspose.Words と C# を使用して、Word 文書に ActiveX コマンド ボタンを作成する方法を学びます。ステップバイステップのガイドでは、挿入、配置、保存について説明します。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- aspose.words activex
- c# documentbuilder
- insertforms2olecontrol
- activeX control in word
- programmatically add button
language: ja
lastmod: 2026-09-21
og_description: C# と Aspose.Words を使用して Word 文書に ActiveX コマンドボタンを作成します。この完全なチュートリアルで、ボタンの挿入、配置、保存をプログラムで行う方法をご確認ください。
og_image_alt: Screenshot showing an ActiveX command button inserted in a Word document
  using C#
og_title: C#でWordにActiveXコマンドボタンを作成する – 完全ガイド
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create ActiveX command button in a Word document with
    Aspose.Words and C#. Step‑by‑step guide covers insertion, positioning, and saving.
  headline: How to create ActiveX command button in Word using C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
- DocumentBuilder
title: C# を使用して Word に ActiveX コマンドボタンを作成する方法
url: /ja/net/working-with-oleobjects-and-activex/how-to-create-activex-command-button-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# WordでActiveXコマンドボタンをC#で作成する方法

Wordファイル内に **ActiveX コマンド ボタン** を作成する必要がある場合、このガイドでは正確な手順を示します。Aspose.Words for .NET を使用すると、ボタンを C# コードだけで追加、配置、設定できます。

ActiveX ボタンをプログラムで挿入することで、手動の UI 作業が不要になり、フォーム、レポート、インタラクティブテンプレート向けの自動文書生成が可能になります。このチュートリアルでは、**DocumentBuilder**、**InsertForms2OleControl** メソッド、および関連プロパティを使用して、完全に機能するボタンを作成する方法を学びます。

## 必要なもの

開始する前に、以下が揃っていることを確認してください。

* .NET 6.0 SDK 以降（コードは .NET Framework 4.7+ でも動作します）
* Aspose.Words for .NET（NuGet パッケージ `Aspose.Words`）
* Visual Studio 2022 や VS Code などの IDE
* C# と Word 文書の基本概念に関する知識

Microsoft Word のインストールは不要です。Aspose.Words は Word 本体とは独立して動作します。

## 手順 1: C# プロジェクトの設定

新しいコンソールプロジェクトを作成し、Aspose.Words パッケージを追加します。

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

`Aspose.Words` ライブラリは、文書操作に使用する **DocumentBuilder** クラスを提供します。

## 手順 2: 文書とビルダーの初期化

最初のコードブロックは空の文書と `DocumentBuilder` インスタンスを作成します。このオブジェクトがすべての Word 処理操作のエントリーポイントになります。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// Create a new blank document.
Document doc = new Document();

// Create a builder to edit the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

**ポイント:** `DocumentBuilder` は現在のカーソル位置を保持するため、以降の挿入はカーソルがある場所に正確に配置されます。

## 手順 3: ActiveX コマンドボタンの挿入

**InsertForms2OleControl** メソッドは、指定されたタイプの ActiveX コントロールを作成します。ここでは `CommandButton` を要求し、サイズをポイント単位（200 × 30 pt）で指定します。

```csharp
// Insert an ActiveX CommandButton control (200 × 30 pt).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    OleControlType.CommandButton, 200, 30);
```

**解説:**  
* `OleControlType.CommandButton` は、Aspose.Words にボタンを作成させ、他のコントロールタイプではないことを指示します。  
* メソッドは `Forms2OleControl` オブジェクトを返し、位置やプロパティのフィールドを公開します。

## 手順 4: ボタンの位置設定とプロパティ設定

挿入後、ページ上の任意の場所にボタンを移動し、プログラム上の名前と表示キャプションを設定できます。

```csharp
// Position the button (coordinates are in points).
cmdBtn.Left = 100;          // X‑coordinate
cmdBtn.Top = 150;           // Y‑coordinate

// Set the button's programmatic name and displayed text.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

**プロのコツ:** 座標系はページ左上隅が原点です。`Left` と `Top` を調整して、他のフォームフィールドと整列させてください。

## 手順 5: 文書の保存

最後に、文書をディスクに書き出します。ファイルには ActiveX ボタンが含まれ、Microsoft Word で開くとインタラクティブになります。

```csharp
// Save the document that now contains the ActiveX button.
doc.Save("ActiveXCommandButton.docx");
```

`ActiveXCommandButton.docx` を Word で開くと、指定した位置に **Submit** とラベル付けされたボタンが表示されます。Word 上でクリックすると、デフォルトのコマンドボタン動作がトリガーされます（後で VBA や Word アドインでカスタマイズ可能）。

## 完全な実行可能サンプル

すべてのコードを組み合わせると、コピー＆ペーストしてすぐに実行できる自己完結型プログラムが完成します。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX CommandButton (200 × 30 pt).
        Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
            OleControlType.CommandButton, 200, 30);

        // 3. Position and configure the button.
        cmdBtn.Left = 100;          // X‑coordinate (points)
        cmdBtn.Top = 150;           // Y‑coordinate (points)
        cmdBtn.Name = "btnSubmit";
        cmdBtn.Caption = "Submit";

        // 4. Save the document.
        doc.Save("ActiveXCommandButton.docx");

        Console.WriteLine("Document created successfully.");
    }
}
```

**期待される出力:** コンソールに *“Document created successfully.”* と表示され、フォルダーに `ActiveXCommandButton.docx` が生成されます。Word でファイルを開くと、左余白から 100 pt、ページ上部から 150 pt の位置に配置されたクリック可能な **Submit** ボタンが確認できます。

## よくある落とし穴と回避策

| 問題 | 発生原因 | 対策 |
|------|----------|------|
| ボタンがページ外に表示される | `Left`/`Top` の値がページサイズを超えている | `doc.FirstSection.PageSetup.PageWidth` と `PageHeight` を使用して安全な座標を計算する |
| Word でボタンが見えない | ActiveX コントロールを除去する形式（例: `.txt`）で保存した | 常に `.docx` または `.doc` 形式で保存する |
| 実行時エラー `ArgumentOutOfRangeException` | 幅または高さが 0 または負の値に設定されている | `InsertForms2OleControl` に渡すサイズ引数が正の数であることを確認する |

## ソリューションの拡張

`Enabled`、`Visible` などの追加プロパティを設定したり、VBA マクロを添付したりしてボタンをさらにカスタマイズできます。**Forms2OleControl** クラスは、チェックボックス（`OleControlType.CheckBox`）やコンボボックス（`OleControlType.ComboBox`）など、他の ActiveX コントロールの挿入もサポートします。

複数のボタンをループで生成したい場合は、挿入ロジックをヘルパーメソッドにまとめてください。

```csharp
static Forms2OleControl AddCommandButton(DocumentBuilder builder,
    string name, string caption, double left, double top)
{
    var btn = builder.InsertForms2OleControl(OleControlType.CommandButton, 200, 30);
    btn.Name = name;
    btn.Caption = caption;
    btn.Left = left;
    btn.Top = top;
    return btn;
}
```

## 結論

これで C# と Aspose.Words を使用して Word 文書に **ActiveX コマンド ボタン** を作成する方法が分かりました。プロジェクトのセットアップ、`InsertForms2OleControl` によるボタン挿入、位置設定、最終保存までの手順を網羅しました。この基礎を活かして、複雑なフォームの自動化やインタラクティブコントロールの埋め込み、Word 文書を大規模な .NET ソリューションに統合することが可能です。

次は、**Aspose.Words ActiveX** フォームフィールド、**C# DocumentBuilder** の高度なスタイリング、チェックボックスやドロップダウンリスト用の **ActiveX control in Word** のプログラム的追加など、関連トピックを探求してください。座標やサイズを調整し、独自のレイアウト要件に合わせて実験してみましょう。コーディングを楽しんでください！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示した手法を応用した関連トピックを扱っています。各リソースには、完全なコード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、代替実装アプローチを自分のプロジェクトで試したりするのに役立ちます。

- [Aspose.Words for .NET を使用した Word ドキュメントの作成](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Aspose.Words で Word に長方形シェイプを作成 – ステップバイステップガイド](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words を使用したテーブル付き Word ドキュメントの作成](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}