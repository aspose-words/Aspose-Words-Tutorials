---
category: general
date: 2026-09-08
description: C#でActiveXコントロールを挿入しながらdocxを保存する方法。プログラムでコマンドボタンを追加する手順をステップバイステップでご案内します。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save docx
- insert activex control
- add activex button
- create word document programmatically
- how to add command button
language: ja
lastmod: 2026-09-08
og_description: C#でActiveXコントロールを挿入しながらdocxを保存する方法。このチュートリアルでは、プログラムでWord文書を作成し、コマンドボタンを追加し、ファイルを永続化する手順を解説します。
og_image_alt: How to save docx with an ActiveX command button displayed in the document
og_title: C#でdocxを保存し、ActiveXボタンを埋め込む方法
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: How to save docx while inserting an ActiveX control in C#. Follow this
    step‑by‑step guide to add a command button programmatically.
  headline: How to save docx and insert an ActiveX button with C#
  type: TechArticle
tags:
- C#
- Word automation
- ActiveX
- Docx
title: C#でdocxを保存し、ActiveXボタンを挿入する方法
url: /ja/net/working-with-oleobjects-and-activex/how-to-save-docx-and-insert-an-activex-button-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で docx を保存し、ActiveX ボタンを挿入する方法

Word 文書をプログラムで作成し、インタラクティブなボタン付きで docx として保存したい場合は、このガイドをご参照ください。ActiveX コントロールの挿入、ActiveX ボタンの追加、そして C# と Aspose.Words ライブラリを使用した .docx ファイルの保存方法を学べます。

このチュートリアルでは、**プログラムで Word 文書を作成**し、**コマンド ボタン**を埋め込み、ディスクにファイルを永続化するまでのすべての手順を解説します。COM オブジェクトの事前知識は不要ですが、C# の基本的な知識と Visual Studio がインストールされていることが前提です。

## 前提条件

開始する前に、以下が揃っていることを確認してください。

* .NET 6.0 SDK 以降  
* Visual Studio 2022（または任意の C# IDE）  
* Aspose.Words for .NET NuGet パッケージ（`Install-Package Aspose.Words`）  
* C# プロジェクト構成の基本的な理解  

これらがあれば、コードは追加設定なしでコンパイルおよび実行できます。

## 手順 1: 新しい C# コンソール プロジェクトを作成

Word 自動化ロジックをホストするコンソール アプリケーションを作成します。

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

上記コマンドは **WordActiveXDemo** というフォルダーを作成し、Aspose.Words の参照を追加し、コンパイル用のプロジェクトを準備します。

## 手順 2: プログラムで Word 文書を作成

生成された `Program.cs` ファイルを開き、必要な `using` ディレクティブを追加します。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;   // not used directly but required for some overloads
```

次に空の `Document` オブジェクトをインスタンス化します。このオブジェクトはメモリ上の Word ファイル全体を表します。

```csharp
// Step 2: Create a new blank document
Document document = new Document();
```

`Document` クラスはすべての Word 処理操作のエントリ ポイントです。この段階では文書にページはありませんが、コンテンツを追加すると Aspose.Words が自動的にデフォルト セクションを作成します。

## 手順 3: ActiveX コントロールを挿入 – ActiveX ボタンを追加

**Forms2OleControl** オブジェクトを使用すると、Word の段落内に ActiveX コントロールを埋め込めます。以下のコードは幅 150 pt、高さ 30 pt の **CommandButton** を挿入します。

```csharp
// Step 3: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX CommandButton control with the desired size
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

`InsertForms2OleControl` はコントロールを作成し、強く型付けされた `Forms2OleControl` インスタンスを返します。返されたインスタンスはさらに設定可能です。このメソッドはコントロールをホストする新しい段落を自動的に追加するため、段落オブジェクトを手動で管理する必要はありません。

## 手順 4: コマンド ボタンを設定 – ボタン プロパティの追加方法

ボタンの **Name** と **Caption** プロパティを設定し、実行時に識別しやすく、ユーザーにとって分かりやすい UI にします。

```csharp
// Step 4: Set the control's name and caption
commandButton.Name = "cmdSubmit";
commandButton.Caption = "Submit";
```

`Name` 属性は、後で VBA や Word マクロからボタンのクリック イベントを処理する際に便利です。`Caption` はエンド ユーザーがボタン上で見るテキストです。

### プロのヒント
C# からクリック処理を自動化したい場合は、`cmdSubmit` を参照する VBA マクロを埋め込んでおきます。文書を開くと Word がマクロの有効化を促すダイアログを表示しますが、これは ActiveX コントロールに対する標準的なセキュリティ動作です。

## 手順 5: docx の保存方法

コントロールを配置したら、文書を .docx ファイルとして永続化します。`Save` メソッドは拡張子に基づいて適切な形式を自動的に選択します。

```csharp
// Step 5: Save the document containing the CommandButton
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

ファイルの保存で **docx の保存方法** のワークフローは完了です。生成されたファイルは Microsoft Word で開くことができ、最初のページに ActiveX ボタンが表示されます。ボタンをクリックすると、マクロが添付されていない限りプレースホルダー メッセージが表示されます。

## 手順 6: プログラムを実行し結果を確認

コンソール アプリをコンパイルして実行します。

```bash
dotnet run
```

プログラムが終了したら、`C:\Temp\CommandButton.docx` を Microsoft Word で開きます。

* 文書は 1 ページで、上部付近に **Submit** ボタンが配置されています。  
* ボタン上にマウスを合わせると、`cmdSubmit` という名前のツールチップが表示されます。  
* コンテンツは失われず、ファイル サイズは標準的な空白 .docx と同程度です。

ボタンが表示されない場合は、以下を確認してください。

1. Word の **Trust Center** 設定で ActiveX コントロールが許可されていること。  
2. ファイルが `.docx` 拡張子で保存されていること（`.doc` ではない）。

## エッジケースと一般的なバリエーション

| 状況 | 推奨される調整 |
|-----------|------------------------|
| ボタンのサイズを変更したい | `InsertForms2OleControl` の幅と高さの引数を変更します。 |
| 特定のページにボタンを配置したい | ページを追加した後に `builder.MoveToDocumentEnd();` を使用するか、コントロールの前に改ページを挿入します。 |
| Aspose.Words が使用できない環境をサポートしたい | Open XML SDK を使用して `w:object` 要素を挿入しますが、コードはかなり複雑になります。 |
| マクロ有効文書が必要 | `.docm` 拡張子で保存します（`document.Save("MyDoc.docm");`）し、`cmdSubmit_Click` を処理する VBA モジュールを埋め込みます。 |

## 完全なソースコード

以下は `Program.cs` にそのまま貼り付けて実行できる、完全な自己完結型プログラムです（出力パスを除き変更不要です）。

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
            // Create a new blank document
            Document document = new Document();

            // Initialize a DocumentBuilder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control with the desired size
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Set the control's name and caption
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // Save the document containing the CommandButton
            string outputPath = @"C:\Temp\CommandButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### コンソールでの期待出力

```
Document saved to C:\Temp\CommandButton.docx
```

Word でファイルを開くと **Submit** と表示されたボタンが現れます。ボタンをクリックすると、デフォルトの ActiveX 動作（マクロが未設定の場合はメッセージ ボックス）がトリガーされます。

## 結論

このチュートリアルでは、**docx の保存方法** と **ActiveX コントロール**（具体的にはコマンド ボタン）の埋め込み手順を示しました。これで **プログラムで Word 文書を作成**し、ボタンのプロパティを設定し、エンド ユーザーが操作できる形でファイルを永続化する方法が習得できました。

次に取り組めること：

* `cmdSubmit_Click` を処理する VBA マクロの追加。  
* チェック ボックスやコンボ ボックスなど、他の ActiveX コントロールの挿入。  
* 複数ページにわたる文書を生成し、複数のインタラクティブ要素を配置。

さまざまなコントロール種別やレイアウト オプションを試して、業務プロセスを効率化するリッチでインタラクティブな Word テンプレートを作成してください。


## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示した手法を応用した関連トピックを扱っています。各リソースには完全な動作コード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、別の実装アプローチを自分のプロジェクトで試したりするのに役立ちます。

- [Aspose.Words – docx を txt に変換し、Word 方程式を LaTeX としてエクスポートする完全ガイド](/words/english/net/basic-conversions/save-docx-as-txt-complete-guide-to-export-word-equations-as/)
- [docx の復旧方法 – 破損した Word ファイル向け C# ガイド](/words/english/net/programming-with-loadoptions/how-to-recover-docx-c-guide-for-corrupted-word-files/)
- [Word を Markdown に保存する方法 – 完全 C# ガイド](/words/english/net/programming-with-markdownsaveoptions/how-to-save-word-as-markdown-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}