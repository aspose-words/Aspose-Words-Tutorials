---
category: general
date: 2026-09-11
description: Aspose.Words を使用して、C# で Word 文書を作成し、プログラムでコマンド ボタンを追加する方法を、簡単な手順で学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- programmatically add command button
language: ja
lastmod: 2026-09-11
og_description: C#でWord文書を作成し、Aspose.Wordsを使用してプログラム的にコマンドボタンを追加します。動作するソリューションのための完全なガイドをご覧ください。
og_image_alt: Screenshot of a Word document containing a Submit command button created
  with C#
og_title: C#でWord文書を作成 – コマンドボタンをプログラムで追加
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  headline: How to create word document c# and programmatically add a command button
  type: TechArticle
- description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  name: How to create word document c# and programmatically add a command button
  steps:
  - name: Launch Word and open `CommandButton.docx`.
    text: Launch Word and open `CommandButton.docx`.
  - name: You should see a button labeled **Submit** in the document body.
    text: You should see a button labeled **Submit** in the document body.
  - name: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
    text: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
title: C#でWord文書を作成し、プログラムでコマンドボタンを追加する方法
url: /ja/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-and-programmatically-add-a-com/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で Word 文書を作成し、プログラムからコマンドボタンを追加する方法

**C# で Word 文書を作成**し、インタラクティブなボタンを埋め込みたい場合、このガイドで手順をすべて解説します。Aspose.Words を使用すれば、数行のコードでプログラムからコマンドボタンを追加でき、Word での手作業 UI 作成が不要になります。

このチュートリアルで学べること：

* C# で空の Word ファイルを初期化する方法
* ActiveX **CommandButton** コントロールを挿入する方法
* ボタンの名前やキャプションなどのプロパティを設定する方法
* ドキュメントを保存し、Microsoft Word で開いたときにボタンが表示されるようにする方法

必要な外部ツールは Aspose.Words for .NET ライブラリだけです。手順は .NET 6+ または .NET Framework 4.6.2 以降でも動作します。

## 前提条件

開始する前に、以下を用意してください。

| Requirement | Reason |
|------------|--------|
| .NET 6 SDK（または .NET Framework 4.6.2 以上） | C# プロジェクトのランタイムを提供します。 |
| Visual Studio 2022（または任意の C# IDE） | コードの作成、ビルド、実行を容易にします。 |
| Aspose.Words for .NET NuGet パッケージ | サンプルで使用する `Document`、`DocumentBuilder`、`Forms2OleControl` クラスを提供します。 |
| C# の基本構文に関する知識 | 追加学習なしでコードを追跡できます。 |

NuGet コンソールから Aspose.Words パッケージを追加できます：

```powershell
Install-Package Aspose.Words
```

## 手順 1: 新しい C# コンソールプロジェクトをセットアップ

Word ファイルを生成するコンソール アプリケーションを作成します。ターミナルを開き、以下を実行してください。

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

生成された `Program.cs` ファイルに、以降の手順で示すコードを配置します。

## 手順 2: 空のドキュメントと DocumentBuilder を作成

最初の操作は、空の `.docx` ファイルを表す `Document` オブジェクトと、ドキュメント内容を編集できる `DocumentBuilder` をインスタンス化することです。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Step 2: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**重要ポイント:**  
`Document` はすべての Word 要素（段落、表、コントロール）を保持するコンテナです。`DocumentBuilder` は現在のカーソル位置にオブジェクトを挿入できるフルエント API を提供し、低レベルのノードコレクションを直接扱う必要がありません。

## 手順 3: ActiveX CommandButton コントロールを挿入

Aspose.Words は `InsertForms2OleControl` メソッドを通じてレガシー ActiveX コントロールの挿入をサポートしています。このメソッドにはコントロールの種類とサイズ（ポイント単位）を指定します。

```csharp
        // Step 3: Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);
```

**内部で何が起きているか:**  
Word は ActiveX コントロールを OLE（Object Linking and Embedding）オブジェクトとして扱います。`Forms2OleControl` クラスは OLE データをラップし、`Name` や `Caption` といったプロパティを公開します。

## 手順 4: ボタンの名前とキャプションを設定

コントロールを配置したら、実行時プロパティをカスタマイズできます。意味のある `Name` を設定すると後でボタンを特定しやすくなり、`Caption` はボタンに表示されるテキストを決定します。

```csharp
        // Step 4: Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";
```

**プロのコツ:**  
VBA でボタンのクリックイベントを処理する場合、`Name` がマクロ名として使用されます（例: `Sub btnSubmit_Click()`）。

## 手順 5: ドキュメントをディスクに保存

最後に、`.docx` ファイルとしてドキュメントを書き出します。書き込み権限のあるフォルダーを選択してください。サンプルでは相対パスを使用しており、プロジェクトの出力ディレクトリに解決されます。

```csharp
        // Step 5: Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

プログラムを実行すると `CommandButton.docx` が生成されます。Microsoft Word でファイルを開くと、クリック可能な **Submit** ボタンが表示されます：

![Word document with a Submit command button](/images/command-button.png "C# で作成された Submit コマンドボタンを含む Word 文書のスクリーンショット")

*画像代替テキスト (og_image_alt):* `C# で作成された Submit コマンドボタンを含む Word 文書のスクリーンショット`

## 結果の検証

1. Word を起動し、`CommandButton.docx` を開く。  
2. 文書本文に **Submit** とラベル付けされたボタンが表示されていることを確認。  
3. ボタン上にマウスを合わせると、**プロパティ** ペイン（開発タブ → プロパティ）に `btnSubmit` という名前が表示されます。  

ボタンが表示されない場合は、Word の **開発** タブが有効になっているか確認してください（ファイル → オプション → リボンのカスタマイズ → **開発** にチェック）。開発タブが無効だと ActiveX コントロールは非表示になります。

## よくあるバリエーションとエッジケースの対処

| Situation | Recommended adjustment |
|-----------|------------------------|
| **異なるボタンサイズ** | `InsertForms2OleControl` の幅と高さの引数を変更します。例: `150, 40` で大きめのボタンが作成できます。 |
| **複数ボタン** | `InsertForms2OleControl` を繰り返し呼び出し、呼び出し間でビルダーのカーソルを移動させます（`builder.Writeln();` など）。 |
| **ActiveX なしのボタン** | 互換性が必要な古い Word バージョン向けに、`InsertFormField` を使用してレガシーフォーム フィールド（チェックボックス等）を追加します。 |
| **クロスプラットフォーム利用** | ActiveX コントロールは Windows 用 Word のみ動作します。Mac や Web ビューア向けには、ボタン風に装飾したハイパーリンクの挿入を検討してください。 |
| **セキュリティ警告** | ActiveX コントロールを含む文書を開くと警告が表示されることがあります。信頼できる証明書で文書に署名するとこの摩擦が軽減されます。 |

## 完全な実行可能サンプル

以下は `Program.cs` にコピペできる完全なプログラムです。Aspose.Words の NuGet パッケージを追加した後、そのままコンパイル・実行できます。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);

        // Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**コンソールへの期待出力:**

```
Document saved to C:\Path\To\WordButtonDemo\bin\Debug\net6.0\CommandButton.docx
```

生成されたファイルを開くと、**Submit** ボタンが操作可能な状態で表示されます。

## まとめ

これで **C# で Word 文書を作成**し、**プログラムからコマンドボタン** コントロールを追加する方法が分かりました。手順は `Document` の初期化、`Forms2OleControl` の挿入、プロパティ設定、保存の 4 ステップに集約されます。ここからは次のような拡張が可能です。

* `ControlType` を変更してチェックボックスやテキスト フィールドなど他のコントロールを追加  
* ボタンに VBA マクロを紐付けてカスタムロジックを実装  
* メールマージやテンプレート埋め込みなど、Aspose.Words の他機能と組み合わせる  

サイズ、キャプション、ボタン数を自由に調整し、あなたの自動化シナリオに合わせて活用してください。コーディングを楽しんでください！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれており、API の追加機能習得や代替実装アプローチの探求に役立ちます。

- [Aspose.Words を使用したヘッダーとフッター付き Word 文書の作成](/words/english/net/header-footer-formatting/create-header-footer/)
- [Aspose.Words for .NET を使用した Word 文書へのコンテンツ追加](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Aspose.Words for .NET で Word 文書にグループ シェイプを作成](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}