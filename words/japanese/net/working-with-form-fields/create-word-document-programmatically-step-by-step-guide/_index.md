---
category: general
date: 2026-08-04
description: C# を使用してプログラムで Word 文書を作成します。数ステップで Aspose.Words を使ってプログラム的にコマンドボタンを追加する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- programmatically add command button
- Aspose.Words InsertForms2OleControl
- C# Word automation
- OLE command button in Word
language: ja
lastmod: 2026-08-04
og_description: Aspose.Words を使用してプログラムで Word 文書を作成します。このガイドでは、プログラムでコマンドボタンを追加し、設定し、ファイルを保存する方法を示します。
og_image_alt: Screenshot of a Word document that contains a Command Button added programmatically
og_title: プログラムでWord文書を作成する – 完全C#チュートリアル
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  headline: Create word document programmatically – step‑by‑step guide
  type: TechArticle
- description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  name: Create word document programmatically – step‑by‑step guide
  steps:
  - name: The `ControlType` enum value (here `CommandButton`).
    text: The `ControlType` enum value (here `CommandButton`).
  - name: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
    text: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
  - name: Optionally, additional OLE properties (not needed for the basic button).
    text: Optionally, additional OLE properties (not needed for the basic button).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: プログラムでWord文書を作成する – ステップバイステップガイド
url: /ja/net/working-with-form-fields/create-word-document-programmatically-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# プログラムで Word 文書を作成する – 完全な C# チュートリアル

もし **プログラムで Word 文書を作成** したい場合は、このガイドで Aspose.Words for .NET を使用した具体的な手順を示します。数行の C# で空の `.docx` ファイルを生成し、**programmatically add command button** コントロールを追加し、プロパティを設定し、結果を保存できます。

以下の手順では、プロジェクトのセットアップからエッジケースの処理までをすべてカバーしています。コードを自分のアプリケーションにコピーして、変更せずに実行できます。

## 期待できる成果

* メモリ上だけで新しい Word 文書を初期化する。  
* **Programmatically add command button** OLE コントロールを任意の位置とサイズで追加する。  
* ボタンのキャプション、内部名、その他の OLE プロパティを設定する。  
* 生成された文書をディスクまたはストリームに保存し、さらに処理できるようにする。  

### 前提条件

* .NET 6.0 以降（コードは .NET Framework 4.6+ でも動作します）。  
* 有効な Aspose.Words for .NET ライセンス（または無料評価版）。  
* C# と Visual Studio（またはお好みの IDE）に関する基本的な知識。  

> **Pro tip:** ライセンスなしでサンプルを実行すると、Aspose.Words は最初のページに小さな評価用透かしを追加します。

## 手順 1: プロジェクトのセットアップと必要な名前空間のインポート

新しいコンソール アプリ（または既存のサービスに統合）を作成し、Aspose.Words NuGet パッケージを追加します：

```bash
dotnet add package Aspose.Words
```

次に、`.cs` ファイルの先頭に必須の名前空間をインクルードします：

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
```

これらのインポートにより、`Document`、`DocumentBuilder`、`Forms2OleControl`、および位置指定に使用する `RectangleF` 構造体にアクセスできるようになります。

## 手順 2: 新しい Word 文書を初期化する

どの **create word document programmatically** ワークフローでも最初の操作は `Document` オブジェクトをインスタンス化することです。このオブジェクトは明示的に保存するまでメモリ内にのみ存在します。

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Attach a DocumentBuilder to simplify content insertion
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` は次の要素が配置される位置を追跡するカーソルのように機能します。これを使用することでコードが簡潔になり、Word に直接入力する感覚と同様になります。

## 手順 3: コマンドボタン OLE コントロールを挿入する

Aspose.Words は `InsertForms2OleControl` メソッドを提供し、コマンドボタン、チェックボックス、コンボボックスなどの OLE オブジェクトを埋め込むことができます。このメソッドは 3 つの引数を必要とします：

1. `ControlType` 列挙体の値（ここでは `CommandButton`）。  
2. コントロールの X‑Y 位置と幅‑高さを定義する `RectangleF`（単位はポイント、72 pt = 1 inch）。  
3. オプションで追加の OLE プロパティ（基本的なボタンには不要）。  

```csharp
// Step 3: Programmatically add command button at (100,100) with size 120×30 points
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Why this works:** `InsertForms2OleControl` は文書内に OLE コンテナを作成し、`Forms2OleControl` ラッパーを返します。このラッパーを使用すると、低レベルの COM インタープロを扱わずに基になる OLE オブジェクト（実際のボタン）を操作できます。

## 手順 4: ボタンのキャプションと内部名を設定する

挿入後、通常はボタンにユーザーが見るラベルと、マクロやアドインが後で参照できる内部識別子を付与します。

```csharp
// Step 4: Set caption and name of the button
commandButton.OleFormat.OleObject.Caption = "Click Me";
commandButton.OleFormat.OleObject.Name = "cmdClickMe";
```

- `Caption` は Word UI 上でボタンに表示されるテキストです。  
- `Name` は VBA や外部の自動化スクリプトで使用されるプログラム上の識別子です。  

### オプション: ボタンにマクロを割り当てる

ボタンがクリックされたときに VBA マクロを実行する予定がある場合、マクロ名を付与できます：

```csharp
commandButton.OleFormat.OleObject.MacroName = "MyMacro";
```

> **Edge case:** ターゲット文書がマクロのないマシンで開かれると、Word はセキュリティ警告を表示します。必ずマクロに署名するか、必要な設定についてユーザーに通知してください。

## 手順 5: 文書を保存する

ファイルはディスク、`MemoryStream`、または Web API のレスポンスオブジェクトに直接書き込むことができます。コンソール デモで最も簡単な方法はローカル フォルダーに保存することです：

```csharp
// Step 5: Persist the document containing the button
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

生成された `.docx` を Microsoft Word で開くと、機能するコマンドボタンが表示され、ラベルは “Click Me” です。ボタンをクリックすると、割り当てられたマクロ（存在すれば）が実行され、無ければデフォルトメッセージが表示されます。

## 完全な動作例

`Program.cs` に以下のプログラムをコピーして実行してください。**create word document programmatically** の全フローとエラーハンドリングを示しています。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        try
        {
            // 1️⃣ Initialise a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a CommandButton OLE control
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                new RectangleF(100, 100, 120, 30));

            // 3️⃣ Set button properties
            commandButton.OleFormat.OleObject.Caption = "Click Me";
            commandButton.OleFormat.OleObject.Name = "cmdClickMe";
            // Optional macro assignment (uncomment if needed)
            // commandButton.OleFormat.OleObject.MacroName = "MyMacro";

            // 4️⃣ Save the document
            string outputPath = @"C:\Temp\CommandButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document created successfully at {outputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ Error: {ex.Message}");
        }
    }
}
```

**Expected result:** Word で `CommandButton.docx` を開くと、ラベルが “Click Me” のボタンが表示されます。ボタン上にマウスを合わせると、プロパティ ペインに名前 `cmdClickMe` が表示されます。

## よくある質問とトラブルシューティング

| Question | Answer |
|----------|--------|
| *既存の文書にボタンを追加できますか？* | はい。`new Document("Existing.docx")` でファイルを読み込み、同じ `InsertForms2OleControl` 呼び出しを使用します。 |
| *`RectangleF` はどの単位を使用しますか？* | ポイント（1 inch = 72 pt）。ボタンの位置を正確に調整するために値を変更してください。 |
| *ボタンは Mac 用 Word でも動作しますか？* | OLE コントロールは Windows の Word のみでサポートされています。Mac ではボタンは静的画像として表示されます。 |
| *本番環境で使用する際にライセンスは必要ですか？* | 商用ライセンスを取得すると、評価用透かしが削除され、すべての機能が利用可能になります。 |
| *挿入後にボタンのサイズを変更するには？* | `commandButton.Width` と `commandButton.Height` を変更するか、新しい `RectangleF` で再挿入してください。 |

## ソリューションの拡張

これで **programmatically add command button** コントロールの方法が分かったので、以下の関連トピックを探求できます：

* **Insert other form controls** – `ControlType.CheckBox`、`ControlType.OptionButton` などを使用します（二次キーワード *Aspose.Words InsertForms2OleControl* をカバー）。  
* **Populate the document with dynamic data** – データベースから取得したデータをテーブルや差し込み印刷フィールドにマージします。  
* **Export to PDF** – ボタンを追加した後、`doc.Save("output.pdf", SaveFormat.Pdf)` を呼び出して PDF バージョンを生成します（*C# Word automation* に関連）。

## 結論

これで、Aspose.Words for .NET を使用した **create word document programmatically** と **programmatically add command button** の完全な本番対応パターンが手に入りました。このチュートリアルでは、プロジェクトのセットアップ、文書の初期化、OLE ボタンの挿入、プロパティの設定、ファイルの保存について説明しました。コードを他のフォームコントロールの挿入やマクロの付与、Web サービスやバックグラウンド ジョブへの統合などに自由に応用してください。

コーディングを楽しんで、Word 文書の自動化を満喫してください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Create Word Document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}