---
category: general
date: 2026-08-20
description: 完全なC#サンプルを使って、ActiveXコントロールの作成方法、ボタンサイズの設定方法、そしてWordへのボタン追加方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- set button size
- add button to word
- how to insert button
- create clickable button
language: ja
lastmod: 2026-08-20
og_description: C#でWordファイルにActiveXコントロールを作成する。このチュートリアルでは、ボタンのサイズ設定、Wordへのボタン追加、クリック可能なボタンの作成方法を示します。
og_image_alt: Screenshot of a Word document showing a newly created ActiveX control
  button
og_title: WordでActiveXコントロールを作成する – ステップバイステップ C# ガイド
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  headline: How to create ActiveX control in a Word document using C#
  type: TechArticle
- description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  name: How to create ActiveX control in a Word document using C#
  steps:
  - name: Why this works
    text: '* `InsertForms2OleControl` tells Word to embed an OLE object of type **CommandButton**,
      which is the classic ActiveX button class. * The width and height arguments
      directly **set button size**; Word translates the values from points (1 pt ≈
      1/72 in). * Naming the control (`Name = "btnSubmit"`) makes'
  - name: Pro tip
    text: 'If you want a square button, set both dimensions to the same value:'
  - name: 1. What if the button does not appear after saving?
    text: '* Verify that the Aspose.Words version supports `InsertForms2OleControl`.
      Versions prior to 22.5 lack this feature. * Ensure the target file format is
      `.docx` or `.doc`. Older formats like `.rtf` cannot store ActiveX objects.'
  - name: 2. Can I insert the button at a specific bookmark?
    text: 'Yes. Move the builder to the bookmark before calling `InsertForms2OleControl`:'
  - name: 3. How to **set button size** dynamically based on text length?
    text: Calculate the required width using the `Graphics.MeasureString` method (from
      `System.Drawing`) and convert pixels to points (`points = pixels * 72 / DPI`).
      Then pass the computed width to `InsertForms2OleControl`.
  - name: 4. Is there a way to add multiple buttons in a loop?
    text: 'Absolutely. Wrap the insertion logic in a `for` loop and adjust the `Left`
      and `Top` properties for each iteration:'
  type: HowTo
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
title: C# を使用して Word 文書に ActiveX コントロールを作成する方法
url: /ja/java/integration-interoperability/how-to-create-activex-control-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# を使用して Word 文書に ActiveX コントロールを作成する方法

Microsoft Word ファイル内に **ActiveX コントロールを作成** する必要がある場合、このガイドで手順を正確に示します。**Word にボタンを追加** し、ボタンのサイズを設定し、コントロールをクリック可能にする方法を、短く自己完結型の C# プログラムで確認できます。

このチュートリアルで学べること：

* インタラクティブな Word 文書で ActiveX コントロールがなぜ有用かを理解する。  
* **ボタンサイズを設定** しキャプションを割り当てるために必要な正確なコードを学ぶ。  
* 後でマクロや外部ロジックに接続できる **クリック可能なボタンを作成** する方法を見る。  

この手順は Aspose.Words .NET 23.12 以降で動作し、.NET 開発環境さえあれば実行できます。

> **前提条件** – 有効な Aspose.Words ライセンス（または評価版）と Visual Studio 2022 もしくは任意の C# IDE がインストールされていること。

---

## Word 文書に ActiveX コントロールを作成する方法

最初のステップは空の `Document` と `DocumentBuilder` をインスタンス化することです。`DocumentBuilder` は ActiveX コントロールなどのオブジェクトを挿入するための高レベル API を提供します。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document and obtain a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // The rest of the steps are explained in the following sections.
            InsertActiveXButton(builder);

            // Save the result so you can open it in Word.
            doc.Save("ActiveXButton.docx");
            Console.WriteLine("Document saved as ActiveXButton.docx");
        }
```

次に定義する `InsertActiveXButton` メソッドに、**ボタンを挿入する方法** とその設定ロジックが含まれています。

```csharp
        /// <summary>
        /// Inserts a CommandButton ActiveX control, sets its size, name, and caption.
        /// </summary>
        static void InsertActiveXButton(DocumentBuilder builder)
        {
            // Step 2: Insert a CommandButton ActiveX control with the desired size (width: 100, height: 30).
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                "CommandButton", 100, 30);

            // Step 3: Assign a name to the control for later reference.
            commandButton.Name = "btnSubmit";

            // Step 4: Set the caption that will be displayed on the button.
            commandButton.Caption = "Submit";

            // Optional: Position the button on the page (e.g., 100 points from the top left).
            commandButton.Left = 100;
            commandButton.Top = 150;
        }
    }
}
```

プログラムを実行すると **ActiveXButton.docx** が作成されます。Word でファイルを開くと **Submit** とラベル付けされたボタンが表示されます。コントロールは完全に機能し、クリックすると標準の `CommandButton_Click` イベントが発生し、後で VBA マクロにバインドできます。

### なぜこれが機能するのか

* `InsertForms2OleControl` は Word に **CommandButton** というタイプの OLE オブジェクトを埋め込むよう指示し、これは従来の ActiveX ボタン クラスです。  
* 幅と高さの引数は直接 **ボタンサイズを設定** します。Word はポイント単位（1 pt ≈ 1/72 in）に変換します。  
* コントロールに `Name = "btnSubmit"` と名前を付けることで、VBA から `ActiveDocument.InlineShapes("btnSubmit")` のように簡単に参照できます。  

---

## ボタンサイズとキャプションの設定

外観を変えたい場合は、`InsertForms2OleControl` 呼び出しの数値引数を調整します。メソッドシグネチャは次のとおりです。

```csharp
Forms2OleControl InsertForms2OleControl(string progId, double width, double height);
```

* **progId** – ActiveX クラスのプログラム識別子（標準ボタンの場合は `"CommandButton"`）。  
* **width / height** – ポイント単位のサイズ。たとえば幅 2 cm のボタンは `width = 56.7`（2 cm ≈ 56.7 pt）を使用します。  

挿入後にキャプションを変更することも可能です：

```csharp
commandButton.Caption = "Send Request";
```

キャプションを変更してもサイズには影響しませんが、ユーザーへの視覚的フィードバックは変わります。

### プロのコツ

正方形のボタンが必要な場合は、両方の寸法を同じ値に設定します：

```csharp
Forms2OleControl squareBtn = builder.InsertForms2OleControl("CommandButton", 50, 50);
squareBtn.Caption = "OK";
```

---

## Word にボタンを追加し、クリック可能にする

上記コードですでに **Word にボタンを追加** しています。ボタンに動作を持たせるには、`Click` イベントを処理する VBA マクロを作成する必要があります。以下の最小限のマクロを Word VBA エディタ（`Alt+F11` → Insert → Module）に貼り付けてください。

```vba
Sub btnSubmit_Click()
    MsgBox "You clicked the Submit button!", vbInformation
End Sub
```

コントロールの名前が `btnSubmit` であるため、Word は自動的に `Click` イベントを `btnSubmit_Click` にマッピングします。これが外部ライブラリを使用せずに **クリック可能なボタンを作成** する標準的な方法です。

> **注意:** Word のマクロ セキュリティ設定により ActiveX コントロールがブロックされることがあります。ドキュメントの「すべてのマクロを有効にする」または「VBA マクロを有効にする」を選択するか、運用環境ではマクロにデジタル署名を付与してください。

---

## よくある質問：ボタンの挿入とトラブルシューティング

### 1. 保存後にボタンが表示されない場合は？

* Aspose.Words のバージョンが `InsertForms2OleControl` をサポートしているか確認してください。22.5 より前のバージョンにはこの機能がありません。  
* 対象ファイル形式が `.docx` または `.doc` であることを確認してください。`.rtf` などの古い形式は ActiveX オブジェクトを格納できません。

### 2. 特定のブックマークにボタンを挿入できるか？

はい。`InsertForms2OleControl` を呼び出す前にビルダーをブックマークへ移動します：

```csharp
builder.MoveToBookmark("InsertHere");
builder.InsertForms2OleControl("CommandButton", 100, 30);
```

### 3. テキスト長に基づいて **ボタンサイズを動的に設定** する方法は？

`System.Drawing` の `Graphics.MeasureString` メソッドで必要な幅を計算し、ピクセルをポイントに変換します（`points = pixels * 72 / DPI`）。計算した幅を `InsertForms2OleControl` に渡します。

### 4. ループで複数のボタンを追加する方法は？

もちろん可能です。挿入ロジックを `for` ループで囲み、各イテレーションで `Left` と `Top` プロパティを調整します：

```csharp
for (int i = 0; i < 3; i++)
{
    Forms2OleControl btn = builder.InsertForms2OleControl("CommandButton", 80, 25);
    btn.Name = $"btnOption{i + 1}";
    btn.Caption = $"Option {i + 1}";
    btn.Left = 50;
    btn.Top = 100 + i * 40; // stagger vertically
}
```

---

## 期待される出力

プログラムを実行し **ActiveXButton.docx** を開くと：

* 1 つの **Submit** ボタンが最初のページ左上付近に表示されます。  
* ボタンサイズは指定した寸法（`100 pt × 30 pt`）と一致します。  
* VBA マクロを追加している場合、ボタンをクリックするとメッセージボックスが表示されます：「You clicked the Submit button!」。

これで **ActiveX コントロールを作成**、**ボタンサイズを設定**、**Word にボタンを追加** でき、さらに **ボタンを挿入する方法** と **クリック可能なボタンを作成** する方法を習得しました。今後の自動化タスクに活用してください。

---

## 結論

このチュートリアルでは C# を使用して Word 文書内に **ActiveX コントロールを作成** する方法を学びました。手順に従うことで **ボタンサイズを設定** し、コントロールに意味のある名前を付け、**Word にボタンを追加** して VBA マクロに結び付けた **クリック可能なボタン** にすることができます。  

次に検討できること：

* VBA の代わりに .NET COM アドインにボタンをバインドする。  
* `CheckBox` や `ComboBox` など他の ActiveX クラスを使用する。  
* 複数コントロールを含む完全なフォームの自動作成を行う。

さまざまなサイズで実験してみてください。

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示した手法に基づく関連トピックをカバーしています。各リソースには完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを探求するのに役立ちます。

- [Create Word Document with Floating Image in .NET](/words/english/net/add-content-using-document-builder/insert-floating-image/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create Accessible PDF from Word – Complete Guide](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-from-word-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}