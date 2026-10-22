---
category: general
date: 2026-08-07
description: C# を使用して Word 文書に ActiveX コントロールを追加する方法を学びます。ボタンにマクロを関連付け、クリック可能なボタンの
  Word 例を追加することも含まれます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex control
- associate macro with button
- add clickable button word
- add command button word
language: ja
lastmod: 2026-08-07
og_description: Aspose.Words を使用して Word 文書に ActiveX コントロールを追加する方法。このガイドに従ってボタンを挿入し、ボタンにマクロを関連付け、クリック可能なボタンを追加します。
og_image_alt: Screenshot showing a Word document with an ActiveX command button inserted
  via Aspose.Words
og_title: Word に ActiveX コントロールを追加する方法 – 完全な C# チュートリアル
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  headline: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  name: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  steps:
  - name: Why each line matters
    text: '| Line | Purpose | |------|---------| | `Document doc = new Document();`
      | Instantiates a fresh Word package in memory. | | `DocumentBuilder builder
      = new DocumentBuilder(doc);` | Provides a fluent API for inserting content,
      including ActiveX controls. | | `InsertForms2OleControl` | The only Aspose.'
  - name: Common pitfalls when associating a macro
    text: '* **Macro security settings** – If the document is opened on a machine
      with strict security policies, the macro may be blocked. Provide instructions
      to lower the security level or sign the macro. * **Naming conflicts** – The
      macro name must be unique within the document’s VBA project; otherwise Word'
  - name: 'Edge case: Long captions'
    text: Word truncates captions that exceed the button’s width. To avoid clipping,
      either increase the width argument in `InsertForms2OleControl` or shorten the
      text. Testing with different languages (e.g., German or Japanese) is advisable
      because character width varies.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Aspose.Words を使用して Word に ActiveX コントロールを追加する方法 – ステップバイステップガイド
url: /ja/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# WordでAspose.Wordsを使用してActiveXコントロールを追加する方法

Microsoft Word ファイルにプログラムで **ActiveX コントロールを追加する方法** が必要な場合、本チュートリアルでは Aspose.Words for .NET を使用した正確な手順を示します。コマンドボタンの挿入方法、キャプションの設定方法、そして **ボタンにマクロを関連付ける** 方法を確認できます。最後には、完全に機能するボタンを含むマクロ有効 `.docm` ファイルが作成できます。

インタラクティブなテンプレート（ローン申請書、従業員オンボーディングフォーム、レポート自動化など）を作成する際に、ActiveX ボタンを追加することは一般的な要件です。このガイドではコードの各行を詳しく解説し、**なぜ** それが重要なのかを説明するとともに、遭遇しやすい落とし穴も取り上げます。

## 前提条件

* .NET 6（または .NET Core 3.1 / .NET Framework 4.8）がインストールされていること。
* 有効な Aspose.Words for .NET ライセンスまたは一時評価キー。
* Visual Studio 2022（または C# をサポートする任意の IDE）。
* ボタンがトリガーするマクロを作成する予定がある場合は、Word マクロ（VBA）の基本的な知識。

> **Pro tip:** サンプルを実行する際は、書き込み権限のあるフォルダーに出力を保存してください。そうしないと `doc.Save` が例外をスローします。

## Aspose.Words を使用して Word 文書に ActiveX コントロールを追加する方法

このソリューションの核心は、短い C# プログラムで新しいドキュメントを作成し、ActiveX **CommandButton** コントロールを挿入し、マクロ有効ドキュメント（`.docm`）として保存することです。コードは完全で、コピー＆ペーストだけで使用できます。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert an ActiveX CommandButton control (Forms2OleControl)
        // Parameters: control type, left, top, width, height (in points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            0,   // left position (points)
            0,   // top position (points)
            150, // width (points)
            30   // height (points)
        );

        // Step 3: Set the button's visible caption – this is the add clickable button word
        commandButton.Caption = "Click Me";

        // Step 4 (optional): Associate a macro with the button's click action
        // This demonstrates how to associate macro with button
        commandButton.OnAction = "MyMacro";

        // Step 5: Save the document as a macro‑enabled file to preserve the button reference
        // The file extension .docm tells Word to keep ActiveX controls and macros
        doc.Save("CommandButton.docm");
    }
}
```

### 各行が重要な理由

| 行 | 目的 |
|------|---------|
| `Document doc = new Document();` | メモリ内に新しい Word パッケージをインスタンス化します。 |
| `DocumentBuilder builder = new DocumentBuilder(doc);` | ActiveX コントロールを含むコンテンツ挿入のためのフルエント API を提供します。 |
| `InsertForms2OleControl` | ActiveX コントロールを作成する唯一の Aspose.Words メソッドです。コントロールタイプ（`CommandButton`）とジオメトリを指定します。 |
| `commandButton.Caption = "Click Me";` | エンドユーザーが見る **ボタンの表示テキスト** を設定します。キャプションがないとボタンは空白のままになります。 |
| `commandButton.OnAction = "MyMacro";` | **ボタンにマクロを関連付ける** – クリック時に実行する VBA マクロを Word に指示します。 |
| `doc.Save("CommandButton.docm");` | ドキュメントをマクロ有効ファイルとして保存します。通常の `.docx` ではコントロールとマクロが除去されます。 |

> **Note:** 座標（left、top）はポイント単位で測定されます（1 pt ≈ 1/72 in）。ページ上でボタンを配置したい位置に合わせて調整してください。

## ボタンにマクロを関連付ける方法

`OnAction` プロパティはボタンを `MyMacro` という名前の VBA マクロにリンクします。このマクロは Word ファイル内に手動で作成するか、プログラムで VBA コードを注入して作成する必要があります（Aspose.Words は VBA コードを書き込みません）。以下は Word の **Developer → Visual Basic** エディタで追加できる最小限のマクロ例です。

```vba
Sub MyMacro()
    MsgBox "Button clicked!", vbInformation, "ActiveX Demo"
End Sub
```

ユーザーが `CommandButton.docm` を開いてボタンをクリックすると、Word は `MyMacro` を実行しメッセージボックスを表示します。マクロのセキュリティが **通知なしですべてのマクロを無効にする** に設定されている場合、ボタンは無効化された状態で表示されます。ユーザーにはドキュメントのマクロを有効にするか、信頼できる証明書でマクロに署名するよう案内してください。

### マクロを関連付ける際の一般的な落とし穴

* **Macro security settings** – セキュリティポリシーが厳しいマシンでドキュメントを開くと、マクロがブロックされる可能性があります。セキュリティレベルを下げる手順やマクロに署名する方法を提供してください。  
* **Naming conflicts** – マクロ名はドキュメントの VBA プロジェクト内で一意である必要があります。重複すると Word は「duplicate procedure name」エラーを出します。  
* **64‑bit vs 32‑bit Word** – ActiveX コントロール自体は同様に動作しますが、Office のバージョンに応じて VBA エディタが異なる警告メッセージを表示することがあります。

## Word フォームにクリック可能なボタンテキストを追加する方法

`Caption` プロパティはユーザーがボタン上で見るテキストです。さらにカスタマイズすることも可能です。

```csharp
commandButton.Caption = "Submit Form";
commandButton.Font.Size = 10;      // Adjust font size
commandButton.Font.Name = "Arial"; // Choose a readable font
```

ユーザー入力に応じてキャプションを動的に変更したい場合は、後から Word のオブジェクトモデルを介してコントロールにアクセスできます。

```vba
Sub UpdateButtonCaption()
    Dim btn As InlineShape
    Set btn = ActiveDocument.InlineShapes(1).OLEFormat.Object
    btn.Caption = "Updated Text"
End Sub
```

### エッジケース: 長いキャプション

ボタンの幅を超えるキャプションは Word によって切り詰められます。切り取られないようにするには、`InsertForms2OleControl` の幅引数を増やすか、テキストを短くしてください。文字幅が言語によって異なるため、ドイツ語や日本語など複数の言語でテストすることを推奨します。

## フォーム自動化のためのコマンドボタンテキストの追加方法

視覚的なキャプションに加えて、**add command button word** の概念はコントロールのプログラム上の名前を指します。Aspose.Words は ActiveX コントロールに直接的な `Name` プロパティを提供しませんが、`AltText` フィールドを設定すれば、Word はそれをコントロールの識別子として扱います。

```csharp
commandButton.AltText = "SubmitButton";
```

後で VBA からは `AltText` の値でボタンを参照できます。

```vba
Sub FindButton()
    Dim shp As Shape
    For Each shp In ActiveDocument.Shapes
        If shp.AlternativeText = "SubmitButton" Then
            MsgBox "Found the Submit button!"
        End If
    Next shp
End Sub
```

この手法は複数のボタンがあり、プログラム上でそれらを区別したい場合に便利です。

## 完全な動作例

以下はコンソール アプリケーションとしてコンパイル・実行できる完全なプログラムです。オプションのスタイリング、マクロの関連付け、各ステップの説明コメントが含まれています。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class AddActiveXButton
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert an ActiveX CommandButton.
        //    left=50pt, top=100pt places the button away from the margin.
        Forms2OleControl btn = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            50,   // left
            100,  // top
            200,  // width
            40    // height
        );

        // 3️⃣ Add clickable button word (caption) and style it.
        btn.Caption = "Submit Form";
        btn.Font.Size = 11;
        btn.Font.Name = "Calibri";

        // 4️⃣ Associate macro with button – this is how to associate macro with button.
        btn.OnAction = "SubmitMacro";

        // 5️⃣ Give the control a friendly identifier (add command button word).
        btn.AltText = "SubmitButton";

        // 6️⃣ Save as macro‑enabled document.
        doc.Save("SubmitForm.docm");
    }
}
```

**Expected result:** Microsoft Word で `SubmitForm.docm` を開くと、青枠のボタンに *Submit Form* と表示されます。ボタンをクリックすると、VBA マクロ `SubmitMacro` が実行され（マクロをドキュメントに追加している前提）、メッセージボックスが表示されます。`Forms2OleControl` オブジェクトを使ってボタンの位置やサイズ、スタイルをさらに変更できます。

## ソリューションのテスト

1. C# コンソール アプリをビルドして実行します。  
2. 生成された `SubmitForm.docm` を Word で開きます。  
3. プロンプトが表示されたらマクロを有効にします。  
4. *Submit Form* ボタンをクリックします – `SubmitMacro` で定義したメッセージボックスが表示されるはずです。

ボタンは表示されるが何も起こらない場合は、マクロ名が正確に `SubmitMacro` と一致しているか、マクロセキュリティが実行をブロックしていないかを再確認してください。

## よくある質問

| 質問 | 回答 |
|----------|--------|
| *Can I add more than one ActiveX button?* | はい。`InsertForms2OleControl` を複数回呼び出し、座標を変えて配置します。`OnAction` と `AltText` の値をそれぞれ異なるものにすれば区別できます。 |
| *Is the ActiveX control visible in Word Online?* | いいえ。 |

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法に密接に関連するトピックを取り上げています。各リソースには完全なコード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、独自プロジェクトで代替実装を検討したりする際に役立ちます。

- [Document Builder を使用してコンテンツを追加する (Aspose.Words for .NET)](/words/english/net/add-content-using-document-builder/)
- [Aspose.Words シェイプ シャドウ チュートリアル – C# で Word シェイプに影を追加](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Word 文書に新しいセクションを追加する | Aspose.Words for .NET](/words/english/net/document-sections/add-section/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}