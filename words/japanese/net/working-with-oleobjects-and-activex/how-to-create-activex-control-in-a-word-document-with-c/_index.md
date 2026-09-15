---
category: general
date: 2026-09-14
description: C#でWord文書にActiveXコントロールを作成する。ActiveXの挿入方法、インタラクティブなボタンの追加、そしてプログラムで.docxファイルを生成する方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- how to insert activex
- add interactive button
- create word document
- create button with code
language: ja
lastmod: 2026-09-14
og_description: C#でWord文書にActiveXコントロールを作成します。この完全な例に従ってActiveXを挿入し、インタラクティブなボタンを追加し、ファイルを保存してください。
og_image_alt: Screenshot of a Word document containing a newly created ActiveX CommandButton
og_title: C# を使用して Word で ActiveX コントロールを作成する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Create ActiveX control in a Word document with C#. Learn how to insert
    ActiveX, add interactive button, and generate the .docx file programmatically.
  headline: How to create ActiveX control in a Word document with C#
  type: TechArticle
tags:
- ActiveX
- C#
- Word automation
title: C#でWord文書にActiveXコントロールを作成する方法
url: /ja/net/working-with-oleobjects-and-activex/how-to-create-activex-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# を使用して Word ドキュメントに ActiveX コントロールを作成する方法

Microsoft Word ファイル内に **ActiveX コントロールを作成** する必要がある場合、このガイドでは完全で実行可能なソリューションを示します。ActiveX CommandButton の挿入方法、プロパティの設定方法、そして C# コードだけで生成された `.docx` ファイルの保存方法を正確に確認できます。

Word ドキュメントにインタラクティブなボタンを追加することは、エンドユーザーがドキュメント UI から直接マクロやカスタムロジックをトリガーできるようにしたい場合の一般的な要件です。以下の例では、サードパーティツールに依存せずに **ActiveX の挿入方法** を示し、さらにプログラムで **Word ドキュメントの作成方法** もカバーしています。

このチュートリアルの最後までに、**コードでボタンを作成** できるようになり、キャプションをカスタマイズし、ActiveX コントロールを保持したポータブルな Word ファイルを作成できます。

## 前提条件

- .NET 6.0 以降（Aspose.Words for .NET ライブラリは .NET Core および .NET Framework と互換性があります）
- `Aspose.Words` NuGet パッケージへの参照  
  ```bash
  dotnet add package Aspose.Words
  ```
- C# とオブジェクト指向プログラミングの基本知識

## 手順 1: プロジェクトのセットアップと名前空間のインポート

新しいコンソールプロジェクトを作成します（または既存の C# アプリケーションにコードを統合します）。必要な名前空間をインポートして、コンパイラが Word 処理クラスを見つけられるようにします。

```csharp
using System;
using System.Drawing;               // Provides RectangleF
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
```

> **この手順が重要な理由** – `Aspose.Words` API は、`Document`、`DocumentBuilder`、`Forms2OleControl` クラスを提供し、オブジェクトレベルで Word ファイルを操作できます。これらの参照がなければ、残りのコードはコンパイルできません。

## 手順 2: 新しい Word ドキュメントと DocumentBuilder の作成

`Document` オブジェクトは全体の `.docx` パッケージを表し、`DocumentBuilder` はコンテンツ挿入のためのフルエント API を提供します。

```csharp
// Step 2: Initialize a fresh Word document
Document document = new Document();

// Attach a builder to the document – the builder knows where to write next
DocumentBuilder builder = new DocumentBuilder(document);
```

> **説明** – 新しい `Document` をインスタンス化すると、クリーンなキャンバスが得られます。ビルダーのカーソルは最初のセクションの先頭に位置し、次の挿入の準備が整っています。

## 手順 3: ActiveX CommandButton の挿入

`InsertForms2OleControl` を使用して、特定の位置に ActiveX コントロールを配置します。このメソッドはコントロールの種類と、X/Y 座標とサイズ（ポイント単位）を定義する `RectangleF` を必要とします。

```csharp
// Step 3: Add an ActiveX CommandButton at (100,100) with width 120 and height 30
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **この方法が機能する理由** – `OleControlType.CommandButton` は API に標準的な Windows CommandButton を作成するよう指示します。矩形はページ左上隅を基準にボタンの位置を決めるため、必要な場所に **インタラクティブなボタンを追加** できます。

## 手順 4: ボタンのプロパティ設定

ここでボタンの表示テキスト（`Caption`）と内部名（`Name`）を設定します。これらのプロパティはユーザーが見るもの、そして後で VBA コードが参照できるものです。

```csharp
// Step 4: Define the button’s caption and programmatic name
commandButton.Caption = "Click Me";
commandButton.Name = "btnClick";
```

> **実用的なヒント** – `Name` はドキュメント内で一意である必要があります。そうでないと、VBA マクロが誤ったコントロールを参照してしまう可能性があります。

## 手順 5: ドキュメントの保存

最後に、ファイルをディスクに書き込みます。ActiveX コントロールは Word パッケージ内に保存されるため、保存されたファイルは Microsoft Word で開いたときに完全な機能を保持します。

```csharp
// Step 5: Persist the document – the ActiveX control stays embedded
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **結果** – Word で `CommandButton.docx` を開くと、「Click Me」というラベルの付いたクリック可能な CommandButton が表示されます。コントロールは Word の UI（`Developer → Design Mode → Properties`）を通じてマクロにリンクできます。

## 完全なソース一覧

すべての手順を組み合わせると、コピーして貼り付け、実行できる単一の自己完結型プログラムが得られます。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an ActiveX CommandButton at the desired location
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new RectangleF(100, 100, 120, 30));

        // Set the button's caption and internal name
        commandButton.Caption = "Click Me";
        commandButton.Name = "btnClick";

        // Save the document – the control is preserved
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### 期待される出力

プログラムを実行すると、確認メッセージが出力されます：

```
Document saved to C:\Temp\CommandButton.docx
```

生成されたファイルを Microsoft Word で開くと、指定した座標に **CommandButton** が配置されているのが確認できます。デザインモードでボタンをクリックするとハイライトされ、実行モードでは標準的な ActiveX ボタンと同様に動作します。

## 一般的なバリエーションとエッジケース

| シナリオ | 調整 |
|----------|------------|
| **異なるコントロールタイプ** | `OleControlType.CommandButton` を `OleControlType.CheckBox`、`OleControlType.OptionButton` などに置き換えます。 |
| **複数のボタン** | `InsertForms2OleControl` を繰り返し呼び出し、各新しいボタンの `RectangleF` 座標を更新します。 |
| **動的サイズ設定** | ページサイズ（`builder.PageSetup.PageWidth`）に基づいて矩形の寸法を計算します。 |
| **ストリームへの保存** | Web API からファイルを返す必要がある場合は `document.Save(stream, SaveFormat.Docx)` を使用します。 |
| **Word 97‑2003 形式** | 保存形式を `SaveFormat.Doc` に変更して、ActiveX コントロールを埋め込んだままの `.doc` ファイルを生成します。 |

> **プロのコツ:** 生成されたドキュメントは必ず対象となる Word バージョンでテストしてください。古いバージョンではデフォルトで ActiveX コントロールを無効にするセキュリティ設定が適用されることがあります。

## よくある質問

**.NET Core でも動作しますか？**  
はい。Aspose.Words ライブラリはクロスプラットフォームで、.NET Core および .NET 5/6+ と完全に互換性があります。

**ボタンにプログラムでマクロを割り当てることはできますか？**  
API は VBA コードを直接埋め込むことはできません。ドキュメント生成後に Word で開き、Developer タブを有効にして、`btnClick` を参照するマクロを記録または作成してください。

**ボタンが表示されない場合はどうすればよいですか？**  
Word で `Developer` タブが有効になっていること、ドキュメントが **Protected View** で開かれていないことを確認してください。また、矩形の座標がページ余白内に収まっているかも確認してください。

## 結論

C# を使用して Word ファイル内に **ActiveX コントロールを作成** する方法が分かりました。このチュートリアルでは **ActiveX の挿入方法** を取り上げ、**インタラクティブなボタンの追加** を実演し、**Word ドキュメントの作成** を最初から示し、**コードでボタンを作成** して保存後も保持できることを示しました。

ここからは、他の ActiveX タイプを調査したり、ボタンを VBA マクロに接続したり、ロジックを大規模なドキュメント生成サービスに組み込んだりできます。必要なユーザー体験に合わせて、サイズ、位置、コントロールのプロパティを色々試してみてください。

---

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法に基づく密接に関連したトピックを取り上げています。各リソースには、完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [新しい Word ドキュメントの作成](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Word ドキュメントに VBA プロジェクトを作成](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Aspose.Words for .NET で Word ドキュメントを作成およびスタイル設定](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}