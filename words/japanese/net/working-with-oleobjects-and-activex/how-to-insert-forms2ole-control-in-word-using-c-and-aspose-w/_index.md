---
category: general
date: 2026-11-22
description: C# を使用して Word に Forms2Ole コントロールを挿入する方法を学びましょう。このステップバイステップガイドでは、DocumentBuilder、コマンドボタンの配置、.docx
  の保存について解説します。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert forms2ole control word
- Aspose.Words
- DocumentBuilder
- command button
- C# Word automation
language: ja
lastmod: 2026-11-22
og_description: C#でWordにForms2Oleコントロールを挿入します。Aspose.Words と DocumentBuilder を使用してコマンドボタンを追加する方法をご覧ください。
og_image_alt: Screenshot of a Word document showing an inserted Forms2Ole command
  button created with C#
og_title: C#でWordにForms2Oleコントロールを挿入する – 完全ガイド
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn to insert a Forms2Ole control in Word with C#. This step‑by‑step
    guide covers DocumentBuilder, command button placement, and saving the .docx.
  headline: How to insert Forms2Ole control in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: C# と Aspose.Words を使用して Word に Forms2Ole コントロールを挿入する方法
url: /ja/net/working-with-oleobjects-and-activex/how-to-insert-forms2ole-control-in-word-using-c-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# と Aspose.Words を使用して Word に Forms2Ole コントロールを挿入する方法

Word に **Forms2Ole コントロールを挿入** する必要がある場合、このチュートリアルでは C# を使ってその手順を正確に示します。入力可能なテンプレートを作成する場合や、フォーム作成を自動化する場合でも、以下のソリューションでコマンドボタンをプログラムから追加できます。

空白のドキュメントの作成方法、`DocumentBuilder` を使用してコントロールを配置する方法、そして結果を `.docx` として保存する方法を学びます。また、座標系や古い Word バージョンとの互換性など、一般的な落とし穴についても解説します。

## 前提条件

* .NET 6.0 以降（コードは .NET Framework 4.6 以上でも動作します）
* Aspose.Words for .NET（NuGet パッケージ `Aspose.Words`）
* C# と Word オブジェクトモデルの基本的な理解
* Visual Studio や VS Code などの IDE

## 手順 1: プロジェクトの設定と名前空間のインポート

新しいコンソール アプリケーションを作成し、Aspose.Words パッケージを追加します：

```bash
dotnet new console -n InsertForms2OleDemo
cd InsertForms2OleDemo
dotnet add package Aspose.Words
```

`Program.cs` で必要な名前空間をインポートします：

```csharp
using System;
using System.Drawing;               // for Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;        // for Forms2OleControl
```

> **プロのコツ:** 最新の Aspose.Words バージョンを使用すると、`Forms2OleControl` API の完全なサポートが得られます。

## 手順 2: 空白のドキュメントを作成し DocumentBuilder を初期化する

`Document` クラスは Word ファイルを表し、`DocumentBuilder` はコンテンツを挿入するメソッドを提供します。

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Initialize DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` はカーソルのように機能します。この行の後、ドキュメント内の任意の場所に要素を配置できます。

## 手順 3: ボタンの位置とサイズを定義する

Word は座標をポイントで測定します（1 pt ≈ 1/72 in）。`System.Drawing` の `Rectangle` 構造体はコントロールの境界を表します。

```csharp
// Step 3: Define the button's position and size (x, y, width, height)
Rectangle buttonBounds = new Rectangle(0, 0, 100, 30); // 100 pt wide, 30 pt tall
```

- `0,0` は現在のページの左上隅にコントロールを配置します。
- `x` と `y` を調整してボタンを別の位置に移動します（例: `new Rectangle(150, 200, 100, 30)`）。

## 手順 4: Forms2Ole コマンドボタンを挿入する

ここで `InsertForms2OleControl` を使用してコントロールを追加します。このメソッドはコントロールのタイプ、名前、そして上記で定義した境界を必要とします。

```csharp
// Step 4: Insert a Forms2Ole command button named "ClickMe"
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,   // type of control
    "ClickMe",                  // internal name (used for VBA or macros)
    buttonBounds);              // position and size
```

返される `Forms2OleControl` オブジェクトを使用して、`Enabled`、`Visible` などのプロパティを変更したり、後でマクロ名を割り当てることもできます。

### なぜ Forms2Ole を使用するのか？

- **レガシー互換性** – Forms2Ole コントロールは Word 97‑2003（`.doc`）および新しい `.docx` ファイルで動作します。
- **マクロサポート** – VBA マクロをトリガーできるため、インタラクティブなテンプレートに最適です。
- **正確な配置** – コンテンツコントロールとは異なり、正確な座標を制御できます。

## 手順 5: ドキュメントを保存する

最後に、ファイルをディスクに書き込みます。書き込み権限のあるフォルダーを選択してください。

```csharp
// Step 5: Save the document to see the inserted button
string outputPath = @"./output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

`output.docx` を Microsoft Word で開きます。最初のページ左上隅に **ClickMe** とラベル付けされたボタンが表示されます。Word でクリックしてもマクロを割り当てるまで何も起こりませんが、コントロールは完全に機能します。

## 一般的なエッジケースの対処方法

| Situation | How to address it |
|-----------|-------------------|
| **ボタンがページ外に表示される** | `Rectangle` の座標がページ余白内に収まっているか確認してください。`builder.PageSetup.PageWidth` と `PageHeight` を使用して安全な境界を計算します。 |
| **古い Word バージョンでコントロールが表示されない** | Forms2Ole の Word 97‑2003 互換性を保証するため、ドキュメントを `.doc` として保存します（`doc.Save("output.doc", SaveFormat.Doc)`）。 |
| **キャプションを変更する必要がある** | 挿入後に `commandButton.Caption = "Submit";` を設定します。 |
| **マクロを割り当てる** | `commandButton.MacroName = "MyMacro"` を設定します。マクロはドキュメントの VBA プロジェクトに存在している必要があります。 |
| **複数のボタン** | 異なる `Rectangle` の値とユニークな名前で手順 4 を繰り返します。 |

## 完全な実行可能サンプル

すべてをまとめると、以下のようにコピー＆ペーストして実行できる単体プログラムがあります。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace InsertForms2OleDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document doc = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Define button bounds (x, y, width, height) in points
            Rectangle buttonBounds = new Rectangle(0, 0, 100, 30);

            // Insert a Forms2Ole command button named "ClickMe"
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                "ClickMe",
                buttonBounds);

            // Optional: set button caption
            commandButton.Caption = "Click Me!";

            // Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**期待される出力:** プログラムを実行すると、`output.docx` が Word で開かれ、最初のページ左上に *Click Me!* とラベル付けされたクリック可能なボタンが配置されています。

## 結論

これで C# と Aspose.Words を使用して **Word に Forms2Ole コントロールを挿入** する方法がわかりました。このプロセスは `Document` を作成し、`Rectangle` で位置を指定し、`DocumentBuilder` を介して `InsertForms2OleControl` を呼び出すことです。完全なコードサンプルとエッジケースのガイダンスがあれば、任意の自動化 Word ワークフローにコマンドボタンを組み込むことができます。

### 次のステップ

- `CheckBox` や `OptionButton` など、他の `ControlType` の値を調査する。
- Forms2Ole コントロールと VBA マクロを組み合わせてインタラクティブなフォームを作成する。
- `DocumentBuilder.MoveTo` を使用して、特定の段落やテーブル上にボタンを配置する。
- 高度なプロパティ設定については、Aspose.Words の **Forms2Ole** ドキュメントを確認する。

コーディングを楽しんで、C# と Aspose.Words でよりリッチな Word ドキュメントを作成してください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [C# を使用して Word ドキュメントに OLE コマンドボタンを挿入する方法](/words/english/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/)
- [Aspose.Words で Word に ActiveX コントロールを追加する方法 – ステップバイステップガイド](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/)
- [Aspose.Words で Word ドキュメントにコマンドボタンを追加する – 完全ガイド](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}