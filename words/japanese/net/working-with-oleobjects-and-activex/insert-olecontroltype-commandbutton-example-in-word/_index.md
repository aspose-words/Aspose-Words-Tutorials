---
category: general
date: 2026-08-17
description: Aspose.Words を使用して Word に OleControlType.CommandButton の例を挿入します。プログラムで
  Word 文書にフォーム コントロールを追加する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert olecontroltype.commandbutton example
- how to add form controls to word document
- Aspose.Words ActiveX button
- C# Word automation
- programmatic form controls
language: ja
lastmod: 2026-08-17
og_description: Aspose.Words を使用して Word に OleControlType.CommandButton の例を挿入します。このガイドに従って、Word
  文書にフォーム コントロールを追加しましょう。
og_image_alt: Screenshot showing an ActiveX CommandButton inserted into a Word document
  using Aspose.Words
og_title: WordにOleControlType.CommandButtonの例を挿入
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: Insert OleControlType.CommandButton example in Word using Aspose.Words.
    Learn how to add form controls to a Word document programmatically.
  headline: Insert OleControlType.CommandButton example in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Word に OleControlType.CommandButton の例を挿入
url: /ja/net/working-with-oleobjects-and-activex/insert-olecontroltype-commandbutton-example-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word に OleControlType.CommandButton の例を挿入する

Word ファイルに **OleControlType.CommandButton の例を挿入** したい場合は、このガイドをご覧ください。Aspose.Words を使用して **Word 文書にフォーム コントロールを追加する方法** を学び、完全に実行可能な C# プログラムを手に入れられます。

ActiveX ボタンなどのフォーム コントロールを使用すると、契約書やアンケート、社内ツールなどのインタラクティブな Word テンプレートを作成できます。以下の手順では、プロジェクトのセットアップから、保存した `.docx` ファイルでボタンが正しく表示されていることの確認まで、すべてをカバーしています。

## 前提条件

開始する前に、以下がインストールされていることを確認してください。

- .NET 6.0 SDK 以降  
- Visual Studio 2022（または任意の C# IDE）  
- Aspose.Words for .NET のライセンス、または無料の一時ライセンス  
- C# と Word ファイルの基本的な知識  

> **プロのコツ:** 無料トライアルを使用している場合は、実行ファイルと同じフォルダーにライセンス ファイルを配置し、`Main` の開始時にロードしてください。

## 手順 1: 新しいコンソール プロジェクトを作成し Aspose.Words を追加する

ターミナルで次のコマンドを実行します。

```bash
dotnet new console -n OleCommandButtonDemo
cd OleCommandButtonDemo
dotnet add package Aspose.Words
```

これによりクリーンなプロジェクトが作成され、最新の Aspose.Words パッケージが取得されます。`Document`、`DocumentBuilder`、`InsertForms2OleControl` API が **OleControlType.CommandButton の例を挿入** するために必要です。

## 手順 2: 完全なプログラムを書く

`Program.cs` を作成または置き換えて、以下のコードを貼り付けます。必要な `using` ディレクティブ、ライセンスのロード、元のスニペットに示された 4 ステップのワークフローがすべて含まれています。

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;          // For OleControlType

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Optional: load a trial or commercial license.
        // -------------------------------------------------
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // -------------------------------------------------
        // Step 1: Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // Step 2: Initialize a DocumentBuilder to work with the document
        // -------------------------------------------------
        DocumentBuilder builder = new DocumentBuilder(doc);

        // -------------------------------------------------
        // Step 3: Insert an ActiveX CommandButton control
        // -------------------------------------------------
        // OleControlType.CommandButton creates a CommandButton.
        // "ClickMe" is the control's name.
        // The Rectangle defines the button's position (x, y) and size (width, height).
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "ClickMe",
            new Rectangle(100, 100, 80, 30));

        // -------------------------------------------------
        // Step 4: Save the document containing the ActiveX button
        // -------------------------------------------------
        string outputPath = "ActiveXButton.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### 各行の重要ポイント

* **ライセンスのロード** – 評価版の制限を受けないようにします。  
* **`Document doc = new Document();`** – すべての Word コンテンツのコンテナを作成します。これが **OleControlType.CommandButton の例を挿入** の基盤です。  
* **`DocumentBuilder builder = new DocumentBuilder(doc);`** – テキスト、画像、コントロールを追加するためのフルエント API を提供します。  
* **`InsertForms2OleControl`** – **Word 文書にフォーム コントロールを追加する方法** を実装する核心メソッドです。`OleControlType.CommandButton` 列挙値により Aspose.Words は ActiveX ボタンを作成します。  
* **`new Rectangle(100, 100, 80, 30)`** – 左余白と上余白からそれぞれ 100 ポイント離れた位置に、幅 80 ポイント・高さ 30 ポイントのボタンを配置します。レイアウトに合わせて数値を調整してください。  
* **`doc.Save`** – .docx ファイルをディスクに書き込みます。これでファイルに埋め込まれたボタンが含まれます。

## 手順 3: プログラムをビルドして実行する

プロジェクト フォルダーから次を実行します。

```bash
dotnet run
```

コンソールに次のメッセージが表示されます。

```
Document saved to ActiveXButton.docx
```

`ActiveXButton.docx` を Microsoft Word で開きます。ページの中央付近に **ClickMe** とラベル付けされたボタンが表示されます。ボタンをクリックすると、デフォルトの ActiveX 動作がトリガーされます（通常はマクロを割り当てていない限り何もしません）。

![insert olecontroltype.commandbutton example](/images/activex-button.png "Word 文書に挿入された ActiveX CommandButton")

*画像の代替テキスト:* insert olecontroltype.commandbutton example – Word 文書に表示された ActiveX CommandButton

## 手順 4: ボタンのカスタマイズ（任意）

基本的な **OleControlType.CommandButton の例を挿入** ではデフォルトのボタンが作成されます。キャプションやフォントを変更したり、OLE オブジェクトを直接編集してマクロを割り当てることも可能です。以下は、挿入後にボタンのキャプションを変更する簡潔な方法です。

```csharp
// Retrieve the first shape (our button) from the document
Shape buttonShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

// Access the OLE format and set the caption
buttonShape.OleFormat.GetControl().SetProperty("Caption", "Submit");
```

> **注意:** OLE プロパティの直接操作には、基盤となる COM インターフェイスの理解が必要です。ほとんどのシナリオではデフォルトのキャプションで十分です。

## 手順 5: よくある落とし穴と回避策

| 問題 | 発生理由 | 対策 |
|------|----------|------|
| ボタンが Word に表示されない | ドキュメントを `.docx` で保存したが、OLE コントロールを除去するビューア（例: Google Docs）で開いた | Microsoft Word または編集権限のある Word Online で開く |
| 実行時エラー `ArgumentOutOfRangeException` | `Rectangle` の座標がページ余白外になっている | ページサイズ内の値（例: A4 なら 0‑500）を使用する |
| ライセンス例外 | トライアル ライセンスは 30 日で期限切れになる | 有効なライセンス ファイルをロードするか、Aspose から延長トライアルを取得する |

## 手順 6: 大規模自動化プロジェクトでの活用例

**Word 文書にフォーム コントロールを追加する方法** を大量に適用する必要がある場合（例: 数百件の契約テンプレート生成）、挿入ロジックを再利用可能なメソッドにラップします。

```csharp
static void AddCommandButton(DocumentBuilder builder, string name, Rectangle bounds)
{
    builder.InsertForms2OleControl(OleControlType.CommandButton, name, bounds);
}
```

これにより、データ行を処理するループ内で `AddCommandButton` を呼び出し、各生成ドキュメントに一意のボタン名（例: `Approve_001`、`Approve_002`）を付与できます。

## 結論

これで、Aspose.Words for .NET を使用して **Word 文書にフォーム コントロールを追加する方法** を示す完全な **OleControlType.CommandButton の例を挿入** が完成しました。本チュートリアルでは、プロジェクトのセットアップ、完全なソースコード、カスタマイズのヒント、一般的なトラブルシューティング手順を網羅しました。

次に検討できること:

- **CheckBox** や **ComboBox** など他のコントロール タイプの追加 (`OleControlType.CheckBox`, `OleControlType.ComboBox`)  
- リッチなインタラクティブ性のためにボタンを VBA マクロにバインドする  
- 同じドキュメントから PDF を生成し、フォーム フィールドを保持する

さまざまなサイズ、位置、コントロール名を試して、特定のユースケースに合わせてください。コーディングを楽しんでください！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを基にした密接に関連するトピックをカバーしています。各リソースには、完全に動作するコード例とステップバイステップの解説が含まれており、追加の API 機能を習得したり、独自プロジェクトで代替実装アプローチを探求したりするのに役立ちます。

- [Insert Combo Box Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-combo-box-form-field/)
- [Insert Check Box Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)
- [Insert Text Input Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}