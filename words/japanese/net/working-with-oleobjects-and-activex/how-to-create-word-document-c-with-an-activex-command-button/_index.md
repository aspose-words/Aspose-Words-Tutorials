---
category: general
date: 2026-10-26
description: C#でWord文書を作成し、プログラムでActiveXボタンを追加する方法を学びましょう。このステップバイステップガイドでは、コマンドボタンの挿入、デザイン時に非表示にする方法、そしてファイルの保存について解説します。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to add activex button
- create command button word
- programmatically add command button
language: ja
lastmod: 2026-10-26
og_description: C#でWord文書を作成し、プログラムでActiveXボタンを追加します。実行時にのみ表示されるコマンドボタンを埋め込む完全なチュートリアルをご覧ください。
og_image_alt: Screenshot of a Word document created with C# that contains an ActiveX
  command button
og_title: ActiveX コマンドボタン付きの Word ドキュメントを C# で作成する – 完全ガイド
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document C# and add an ActiveX button programmatically.
    This step‑by‑step guide covers inserting a command button, hiding it at design
    time, and saving the file.
  headline: How to create Word document C# with an ActiveX command button
  type: TechArticle
tags:
- C#
- Aspose.Words
- ActiveX
- Word automation
title: ActiveX コマンドボタン付きの Word 文書を C# で作成する方法
url: /ja/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で ActiveX コマンドボタン付き Word ドキュメントを作成する方法

インタラクティブなボタンを含む **create Word document C#** が必要な場合、このガイドで正確な手順を示します。最初の2文を読めば全体的なアプローチが分かり、以下の手順で必要なコードを1行ずつ解説します。

ActiveX ボタンの追加方法、デザイン時に非表示にし、ユーザーがファイルを開いたときにのみ表示させる方法を学びます。また、セキュリティ警告やバージョン互換性といった一般的な落とし穴も取り上げているので、信頼性の高いドキュメントを提供できます。

## 前提条件

* .NET 6.0 以降がインストールされていること  
* **Aspose.Words for .NET** のライセンス版（無料トライアルでも実験は可能）  
* C# と Visual Studio の基本的な知識（.NET をサポートする任意の IDE で構いません）  

追加の NuGet パッケージは `Aspose.Words` 以外必要ありません。

## ステップ 1: Word ドキュメント C# を作成し DocumentBuilder を初期化する

最初のステップは `Document` オブジェクトと `DocumentBuilder` をインスタンス化することです。`Document` は .docx ファイル全体を表し、`DocumentBuilder` はコンテンツ追加用の流暢なメソッドを提供します。

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document document = new Document();

        // Attach a builder to the document so we can insert nodes.
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Why this matters:** `DocumentBuilder` がなければ、OpenXML DOM を手動で操作する必要があり、エラーが起きやすく読みづらくなります。ビルダーはこれらの詳細を抽象化し、正しく構成された Word ファイルを保証します。

## ステップ 2: ActiveX ボタンの追加方法 – CommandButton コントロールの挿入

ここでは特定の位置に **CommandButton ActiveX コントロール** を挿入します。矩形はボタンの位置 (X, Y) とサイズ (幅, 高さ) をポイント単位で定義します。

```csharp
        // Define the button's position and size.
        RectangleF buttonRect = new RectangleF(100, 100, 120, 30);

        // Insert the ActiveX CommandButton control.
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,   // Type of ActiveX control
            buttonRect,                          // Geometry
            "ClickMe");                          // Caption shown at design time
```

**Why this matters:** `InsertForms2OleControl` は真の ActiveX OLE オブジェクトを作成できる Aspose.Words 唯一のメソッドです。`Forms2OleControlType.CommandButton` 列挙値は、Word に汎用 OLE コンテナではなくクリック可能なボタンを埋め込むよう指示します。

## ステップ 3: コマンドボタンをプログラムで追加 – ランタイムまで非表示にする

Word は挿入された形状をデフォルトで表示します。テンプレート設計時にボタンを非表示にするには、ビルダーが作成した形状の `Hidden` プロパティを設定します。

```csharp
        // Retrieve the shape that represents the newly added control.
        Shape oleShape = (Shape)builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)[0];

        // Hide the shape; it will become visible when the document is opened.
        oleShape.Hidden = true;
```

**Why this matters:** `Hidden = true` を設定すると、デザインビューでボタンが邪魔になるのを防げます。Word でドキュメントを開くと、ランタイム環境が自動的にコントロールを表示し、意図したユーザー体験を保ちます。

## ステップ 4: ファイルを保存 – コマンドボタン付き Word ドキュメントを作成

最後に、ドキュメントをディスクに書き出します。アプリケーションが書き込み可能なパスを選び、`.docx` 拡張子を使用して最新の互換性を確保します。

```csharp
        // Save the document containing the ActiveX button.
        document.Save(@"C:\Temp\ActiveXButton.docx");
    }
}
```

**Why this matters:** `.docx` で保存すると、埋め込まれた ActiveX コントロールが Office Open XML 標準に準拠し、Word 2007 以降でサポートされます。レガシーな `.doc` が必要な場合は拡張子を変更し、`SaveFormat.Doc` を使用してください。

## 完全な動作例

すべてを組み合わせた完全なプログラムを以下に示します。コピーして貼り付け、実行できます。

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Step 1: Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control.
        RectangleF commandButtonRect = new RectangleF(100, 100, 120, 30);
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            commandButtonRect,
            "ClickMe");

        // Step 3: Hide the control so it appears only at runtime.
        Shape oleShape = (Shape)builder.CurrentParagraph
                                         .GetChildNodes(NodeType.Shape, true)[0];
        oleShape.Hidden = true;

        // Step 4: Save the document containing the ActiveX control.
        document.Save(@"C:\Temp\ActiveX.docx");
    }
}
```

**Expected output:** プログラム実行後、Microsoft Word で `C:\Temp\ActiveX.docx` を開きます。空白のドキュメントが表示され、デザインモードではボタンは見えません。**Alt + F9** を押してフィールドコードの表示切替えを行い、ボタン領域をクリックすると Word が ActiveX コントロールを描画し、操作可能になります（例: ダブルクリックでプロパティを表示）。

## エッジケースとベストプラクティスのヒント

| 状況 | 注意点 | 推奨される対策 |
|-----------|-------------------|-----------------|
| **ユーザーが ActiveX を無効化** | Word がセキュリティ警告を表示したり、コントロールをブロックする可能性があります。 | エンドユーザーに Trust Center で “ActiveX controls” を有効にするよう指示するか、マクロ署名済みの代替手段を提供してください。 |
| **Word Online でドキュメントを開く** | Word Online は ActiveX をサポートしていないため、ボタンは省略されます。 | クラウド対応が必要な場合は、代替のハイパーリンクまたはコンテンツコントロールを使用してください。 |
| **異なる DPI 設定** | 高 DPI ディスプレイでは矩形のサイズが大きくまたは小さく表示されることがあります。 | `GraphicsUnit.Point`（デフォルト）を使用し、一般的な DPI 設定（96 dpi、120 dpi）でテストしてください。 |
| **複数のボタン** | `GetChildNodes(NodeType.Shape, true)[0]` 呼び出しは最初の形状しか取得しません。 | `builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)` をループし、追加した各形状に対して `Hidden` を設定してください。 |
| **レガシー .doc 形式** | .doc で保存すると、一部の ActiveX プロパティが失われます。 | 厳格なレガシー要件がない限り、`.docx` を使用してください。 |

**Pro tip:** ボタンを挿入した後、Word の UI で `OnAction` プロパティにマクロを割り当てることができます。これにより、追加の C# コードを書かずにカスタムクリック動作を定義できます。

## よくある質問

* **これは .NET Core でも動作しますか？**  
  はい。Aspose.Words for .NET は .NET 5、.NET 6 以降と完全に互換性があります。同じ NuGet パッケージを参照してください。

* **ドキュメント生成後にボタンのキャプションを変更できますか？**  
  `InsertForms2OleControl` で設定したキャプションはデザイン時のデフォルトテキストになります。ユーザーは Word で編集可能ですが、`Shape.OleFormat` API を介して OLE オブジェクトのプロパティにアクセスすることで、プログラムからキャプションを更新することもできます。

* **ボタンのサイズを変更したい場合はどうすればよいですか？**  
  `RectangleF` の値を調整してください。最初の 2 つのパラメータが X と Y の座標、後の 2 つが幅と高さ（ポイント単位、1 pt = 1/72 インチ）です。

## 結論

これで **create Word document C#** と **programmatically add command button** を Aspose.Words を使って行う方法が分かりました。このチュートリアルでは、ドキュメントの初期化、ActiveX ボタンの挿入、ランタイムまでの非表示、最終ファイルの保存を解説しました。これらの構成要素を使えば、生成する任意の Word テンプレートにインタラクティブなコントロールを埋め込めます。

次に、**how to add ActiveX button** のイベントハンドリングや、VBA を使った **create command button word** のスタイリング、既存ドキュメントへの **programmatically add command button** などの関連トピックを探ってみてください。このパターンをチェックボックス、コンボボックス、カスタム OLE オブジェクトに拡張する場合も同様の手順で行えます—`Forms2OleControlType` 列挙値を変更するだけです。

実験を始めましょう：キャプションを変更したり、位置を調整したり、複数のコントロールを連結したりしてください。練習すればするほど、C# からリッチでインタラクティブな Word ドキュメントを提供する技術が身につきます。コーディングを楽しんで！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトでの代替実装方法を検討するのに役立ちます。

- [Word ドキュメントにコマンドボタンをプログラムで追加する方法](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [Aspose.Words で Word ドキュメントに ActiveX ボタンを追加する方法](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [ActiveX ボタン付き Word ドキュメントの作成 – C# ガイド](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}