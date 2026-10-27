---
category: general
date: 2026-10-23
description: C#で空白のWord文書を作成し、Aspose.Wordsを使用してボタンを含むActiveXコントロールの挿入方法を学ぶ。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- create activex control
- word document activex button
language: ja
lastmod: 2026-10-23
og_description: C#で空白のWord文書を作成し、Aspose.Wordsを使用してボタンを含むActiveXコントロールの挿入方法を学びます。
og_image_alt: Result of creating a blank Word document with an ActiveX Submit button
og_title: 空白のWord文書を作成し、C#でActiveXボタンを追加する
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button in C#
  type: TechArticle
- description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  name: Create a blank Word document and add an ActiveX button in C#
  steps:
  - name: Instantiate a `Document`.
    text: Instantiate a `Document`.
  - name: Use `DocumentBuilder` to work with the file.
    text: Use `DocumentBuilder` to work with the file.
  - name: Call `InsertForms2OleControl` to **how to insert activex** controls.
    text: Call `InsertForms2OleControl` to **how to insert activex** controls.
  - name: Configure the control’s properties (**create activex control**).
    text: Configure the control’s properties (**create activex control**).
  - name: Save the file, yielding a **word document activex button** ready for VBA
      integration.
    text: Save the file, yielding a **word document activex button** ready for VBA
      integration.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: C#で空白のWord文書を作成し、ActiveXボタンを追加する
url: /ja/java/document-manipulation/create-a-blank-word-document-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 空の Word ドキュメントを作成し、C# で ActiveX ボタンを追加する

プログラムで **create blank Word document** を作成する必要がある場合、このガイドでは正確な手順を示します。新しいドキュメントを作成し、ActiveX CommandButton を挿入し、ファイルを保存する完全な実行可能サンプルが Aspose.Words for .NET を使用して確認できます。

Word ファイルの操作は、単なるプレーンテキスト以上のことが必要になることが多いです。**ActiveX button** を追加すると、マクロ有効テンプレートや Windows のみのソリューションで使用できるインタラクティブな機能を埋め込むことができます。このチュートリアルの最後までに、任意の ActiveX コントロールを挿入できるようになりますが、最も一般的なシナリオである **word document activex button**（フォーム送信用）に焦点を当てます。

## 前提条件

* .NET 6.0 以降（コードは .NET Framework 4.7+ でも動作します）
* Visual Studio 2022（または任意の C# IDE）
* **Aspose.Words for .NET** NuGet パッケージ  
  ```bash
  dotnet add package Aspose.Words
  ```
* C# 構文の基本的な知識

> **プロのコツ:** Aspose.Words は商用ライブラリですが、テスト用の無料一時ライセンスを提供しています。評価用の透かしが入らないよう、早めにライセンスをインストールしてください。

## 手順 1: Aspose.Words で空の Word ドキュメントを作成する

最初のステップは `Document` オブジェクトをインスタンス化することです。これはメモリ上の空の `.docx` ファイルを表します。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
```

`Document` はセクション、ページ、コンテンツが何もない状態で開始します。**create blank word document** のように、ゼロからレポートを生成するシナリオに必要な白紙の状態です。

## 手順 2: DocumentBuilder を取得してドキュメントを編集する

`DocumentBuilder` はテキスト、画像、コントロールを追加するための便利な API を提供します。これを使用して ActiveX コントロールの位置を指定します。

```csharp
// Obtain a DocumentBuilder tied to the blank document
DocumentBuilder builder = new DocumentBuilder(document);
```

ビルダーは自動的にデフォルトのセクションと最初のページを追加するため、すぐにオブジェクトの挿入を開始できます。

## 手順 3: ドキュメントに ActiveX コントロールを挿入する方法

Aspose.Words は OLE/ActiveX オブジェクトを埋め込むために `InsertForms2OleControl` を提供しています。このメソッドはコントロールの種類、幅、高さ（ポイント単位）を指定する必要があります。以下では **CommandButton** を挿入します—レガシーな Word テンプレートで見られる古典的なフォームボタンです。

```csharp
// Insert an ActiveX CommandButton control (100 × 30 points)
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

> **なぜ機能するか:** `Forms2OleControlType.COMMANDBUTTON` は、ActiveX をサポートする Windows 環境でドキュメントが開かれたときにクリックイベントに応答できるボタンを Word に作成させます。

## 手順 4: ActiveX コントロールを作成し、プロパティを設定する

ここでボタンにプログラム上の名前と表示用キャプションを設定します。これは開発者が見落としがちな **create activex control** の部分です。

```csharp
// Set the button's name (used in VBA) and the text shown to users
commandButton.Name = "btnSubmit";
commandButton.Caption = "Submit";
```

* `Name` は VBA マクロから参照する識別子です（`ActiveDocument.InlineShapes("btnSubmit")`）。
* `Caption` はボタン自体に表示されるラベルです。

## 手順 5: ActiveX ボタン付きの Word ドキュメントを保存する

最後に、ドキュメントをディスクに書き込みます。ファイル拡張子は `.docx`（後でマクロを追加する場合は `.docm`）である必要があります。例ではプレースホルダー フォルダーに保存していますので、実際のパスに置き換えてください。

```csharp
// Save the document containing the ActiveX button
string outputPath = @"C:\Temp\ActiveXButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

生成されたファイルを Microsoft Word（Windows のみ）で開くと、VBA コードに接続できる機能的な **word document activex button** が表示されます。

## 完全な動作例

以下は新しいコンソール プロジェクトにコピー＆ペーストできる完全なプログラムです。

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
            // 1. Create a blank Word document
            Document document = new Document();

            // 2. Get a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3. Insert an ActiveX CommandButton (100 × 30 points)
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

            // 4. Configure the button
            commandButton.Name = "btnSubmit";
            commandButton.Caption = "Submit";

            // 5. Save the file
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**プログラム実行時の期待出力**

```
Document saved to C:\Temp\ActiveXButton.docx
```

生成された `ActiveXButton.docx` を Word で開くと、最初のページ上部に **Submit** とラベル付けされたボタンが配置されていることが確認できます。

## エッジケースと一般的な落とし穴

| Situation | What to watch for | Recommendation |
|-----------|-------------------|----------------|
| macOS または Linux で実行 | ActiveX は Windows のみの技術であるため、ボタンはプレースホルダーとして表示されます。 | このチュートリアルは Windows 向けテンプレートでのみ使用してください。 |
| Word Online でドキュメントを開く | ブラウザ表示では ActiveX コントロールはサポートされていません。 | 代替 UI を提供するか、デスクトップ クライアントでファイルを開くよう指示してください。 |
| マクロ有効ファイルが必要 | `.docx` ファイルは VBA コードを保存できません。 | `.docm` として保存する（`document.Save("MyFile.docm", SaveFormat.Docm)`）し、マクロは別途追加してください。 |
| コントロールのサイズが合わない | 幅/高さの値はポイント単位です（1 pt ≈ 1/72 in）。 | 希望の視覚サイズになるよう数値を調整してください。 |

## よくある質問

**ボタン以外の ActiveX コントロールを挿入するには？**  
同じ `InsertForms2OleControl` メソッドを使用し、`COMBOBOX` や `LISTBOX` などの別の `Forms2OleControlType` 列挙値を渡します。

**ボタンのフォントや色を変更できますか？**  
ActiveX ボタンの外観はホスト アプリケーション（Word）と基盤となる Windows テーマによって決まります。ドキュメントを開いた後、VBA で `ForeColor` や `BackColor` などのプロパティを変更できます。

**C# から直接クリック ハンドラを追加する方法はありますか？**  
いいえ。クリック イベントは VBA または Word アドインで処理する必要があります。ボタンは Word のプロセス内で実行され、.NET アプリケーションからは直接制御できません。

## 結論

これで、**create blank Word document** をプログラムで作成し、Aspose.Words for .NET を使用して **ActiveX button** を埋め込む方法が分かりました。カバーした手順は次のとおりです：

1. `Document` をインスタンス化する。
2. `DocumentBuilder` を使用してファイルを操作する。
3. `InsertForms2OleControl` を呼び出して **how to insert activex** コントロールを挿入する。
4. コントロールのプロパティを設定する（**create activex control**）。
5. ファイルを保存し、VBA 統合用の **word document activex button** を生成する。

ここからは、他のコントロールタイプの追加、VBA マクロの接続、またはボタンを静的画像として保持したまま PDF へ変換するなどを試すことができます。さまざまなサイズ、キャプション、名前で実験してみてください。

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法に基づく密接に関連したトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Aspose.Words を使用して Word ドキュメントに ActiveX ボタンを追加する方法](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [ActiveX ボタン付き Word ドキュメントの作成 – C# ガイド](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}