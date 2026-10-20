---
category: general
date: 2026-08-04
description: Aspose.Words を使用して空白の Word ドキュメントを作成し、コマンド ボタンを挿入します。C# でボタンのサイズを設定し、クリック可能なボタンを追加する方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert command button
- add clickable button
- set button size
- create command button
language: ja
lastmod: 2026-08-04
og_description: Aspose.Words を使用して空白の Word 文書を作成し、コマンドボタンを挿入します。このガイドでは、ボタンのサイズ設定、クリック可能なボタンの追加、ファイルの保存方法を示します。
og_image_alt: Screenshot of a Word document containing a clickable command button
  created with C#
og_title: 空白のWord文書を作成し、コマンドボタンを追加する – 完全C#チュートリアル
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  headline: Create blank word document with a command button – step‑by‑step guide
  type: TechArticle
- description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  name: Create blank word document with a command button – step‑by‑step guide
  steps:
  - name: The ProgID of the OLE control – `"CommandButton"` for a standard button.
    text: The ProgID of the OLE control – `"CommandButton"` for a standard button.
  - name: A `Rectangle` that defines the **set button size** and position.
    text: A `Rectangle` that defines the **set button size** and position.
  - name: The caption that appears on the button.
    text: The caption that appears on the button.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: コマンドボタンで空白のWord文書を作成する – ステップバイステップガイド
url: /ja/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# コマンドボタン付きの空白のWord文書を作成する – ステップバイステップガイド

インタラクティブなボタンを含む **空白のWord文書を作成** する必要がある場合、このチュートリアルでは Aspose.Words for .NET を使用して正確に行う方法を示します。**コマンドボタンを挿入** の方法や外観の調整、クリック可能にする方法を C# の数行で学べます。

このガイドはプロジェクトのセットアップから最終ファイルの保存までを網羅しているので、完全なソリューションを自分のアプリケーションにコピー＆ペーストできます。途中で **クリック可能なボタンを追加**、**ボタンサイズを設定**、そしてプログラムで **コマンドボタンを作成** する方法も解説します。

## 前提条件

開始する前に、以下がインストールされていることを確認してください。

* .NET 6.0 SDK 以降がインストールされていること。
* Visual Studio 2022（または .NET をサポートする任意の IDE）。
* Aspose.Words for .NET NuGet パッケージ（`Aspose.Words` バージョン 23.12 以上）。
* C# とオブジェクト指向プログラミングの基本的な知識。

Microsoft Word に依存せず完全に独立して動作するため、追加の Office Interop アセンブリは不要です。

## 手順 1: .NET プロジェクトの設定

Word 自動化コードをホストするコンソール アプリケーションを作成します。

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

このコマンドは `WordButtonDemo` という新しいフォルダーを作成し、実行可能な `Program.cs` と Aspose.Words ライブラリを追加します。

## 手順 2: 空白のWord文書を作成

最初の操作は **空白のWord文書を作成** することです。Aspose.Words は、空の Word ファイルを表す `Document` クラスを標準で提供しています。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a new, empty Word document.
Document doc = new Document();
```

空白の文書を作成すると、段落や表、あるいはこのケースでは OLE コマンドボタンを追加できるクリーンなキャンバスが得られます。

## 手順 3: DocumentBuilder の初期化

`DocumentBuilder` は文書にコンテンツを挿入できるヘルパーです。先ほど作成した文書にアタッチする必要があります。

```csharp
// Attach a DocumentBuilder to the empty document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

ビルダーは現在のカーソル位置を保持するため、以降の挿入は希望する正確な場所で行われます。

## 手順 4: コマンドボタンの挿入

ここで **コマンドボタンを挿入**（OLE `Forms2OleControl`）します。`InsertForms2OleControl` メソッドは 3 つの引数を必要とします。

1. OLE コントロールの ProgID – 標準ボタンの場合は `"CommandButton"`。
2. **ボタンサイズを設定** し位置を定義する `Rectangle`。
3. ボタンに表示されるキャプション。

```csharp
// Define the button's position (x, y) and size (width, height).
Rectangle buttonRect = new Rectangle(0, 0, 120, 30); // 120 px wide, 30 px high

// Insert the command button with the desired caption.
Forms2OleControl cmdButton = builder.InsertForms2OleControl(
    "CommandButton",   // ProgID for a CommandButton control
    buttonRect,        // Position and size
    "Click Me");       // Caption displayed on the button
```

Word で文書を開くと、ボタンはネイティブのフォーム コントロールと同様に動作し、クリックすると（存在すれば）関連付けられたマクロが実行されます。これにより **クリック可能なボタンを追加** という要件が満たされます。

### なぜ Forms2OleControl を使用するのか？

`Forms2OleControl` は OLE オブジェクトを DOCX ファイルに直接埋め込み、Word Interop アセンブリを必要とせずにコントロールのプロパティを保持します。Word のバージョンを問わず動作する **コマンドボタンを作成** する最も信頼性の高い方法です。

## 手順 5: ボタンのカスタマイズ（オプション）

**ボタンサイズを設定** をより正確に行いたい場合や、フォントや背景色などの追加プロパティを変更したい場合は、Aspose.Words が基になる OLE オブジェクトを公開しているため、さらに調整が可能です。

```csharp
// Example: change the button's background color (requires OLE automation).
// Note: This step is optional and demonstrates additional customization.
cmdButton.OleFormat.Icon = true; // Show an icon instead of the default appearance.
```

別のサイズが必要な場合は、手順 4 の `Rectangle` の値を調整するだけです。座標はポイント単位（1 pt = 1/72 inch）で測定され、たとえば `120` は約 1.67 インチの幅に相当します。

## 手順 6: 文書の保存

最後に文書をディスクに書き出します。生成されたファイルは **空白のWord文書** に完全に機能するコマンドボタンが含まれています。

```csharp
// Save the document as a .docx file.
doc.Save("CommandButtonDemo.docx");
```

`CommandButtonDemo.docx` を Microsoft Word で開くと、「Click Me」というラベルのボタンが表示されます。ボタンをクリックすると、カスタムマクロを添付していない限りデフォルトのマクロ ダイアログが表示されます。

## 完全なソースコード

以下は `Program.cs` にコピーできるフル プログラムです。上記のすべての手順が含まれており、変更なしでコンパイルできます。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordButtonDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Create a blank word document.
            Document doc = new Document();

            // Step 3: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 4: Define button size and insert command button.
            Rectangle buttonRect = new Rectangle(0, 0, 120, 30);
            Forms2OleControl cmdButton = builder.InsertForms2OleControl(
                "CommandButton",
                buttonRect,
                "Click Me");

            // Optional: further customization (e.g., set icon).
            // cmdButton.OleFormat.Icon = true;

            // Step 6: Save the document.
            doc.Save("CommandButtonDemo.docx");

            System.Console.WriteLine("Document created successfully.");
        }
    }
}
```

### 期待される結果

プログラムを実行すると `CommandButtonDemo.docx` が生成されます。Word でファイルを開くと次のように表示されます。

* **Click Me** とラベル付けされたボタンが 1 ページに表示されます。
* ボタンは **ボタンサイズを設定**（120 × 30 ポイント）を尊守しています。
* ボタンをクリックすると Word のデフォルトのコマンドボタン動作がトリガーされ、**クリック可能なボタンを追加** が成功したことが確認できます。

## よくある質問とエッジケース

| 質問 | 回答 |
|----------|--------|
| **この方法は .doc ファイルでも動作しますか？** | はい。`doc.Save("file.doc")` のようにファイル拡張子を変更してください。OLE コントロールはレガシー バイナリ形式にも保存されます。 |
| **複数のボタンが必要な場合は？** | `InsertForms2OleControl` を繰り返し呼び出し、各ボタンの `Rectangle` を調整して重ならないようにします。 |
| **ボタンにマクロを添付できますか？** | ボタン自体にマクロコードは含まれません。VBA マクロを手動で、または `Document` オブジェクトの `Modules` コレクションを介して文書に追加する必要があります。 |
| **PDF エクスポート時にボタンは表示されますか？** | Aspose.Words で DOCX を PDF にエクスポートすると、ボタンはインタラクティブなコントロールではなく静的な画像としてレンダリングされます。 |
| **サポートされている Word のバージョンは？** | OLE コマンドボタンは Word 2007 以降で動作します。これは標準的な Forms2.0 仕様に準拠しています。 |

## 結論

これで Aspose.Words for .NET を使用して **空白のWord文書を作成**、**コマンドボタンを挿入**、**クリック可能なボタンを追加**、そして **ボタンサイズを設定** する方法が分かりました。完全なサンプルは **コマンドボタンを作成** のワークフローを最初から最後まで示しており、より高度な Word 自動化タスクの基礎となります。

## 次のステップ

* `InsertForms2OleControl` の ProgID を変更して、`CheckBox`、`ListBox` など他の OLE コントロールを探索する。  
* ボタンと VBA マクロを組み合わせて、ユーザーがクリックしたときにカスタム アクションを実行させる。  
* `DocumentBuilder` を使ってボタンを挿入する前に、表、画像、脚注などの追加コンテンツを文書に追加する。  
* **ボタンサイズを設定** の値を実験し、文書のレイアウト要件に合わせる。

コーディングを楽しみながら、インタラクティブなコントロールでリッチな Word 文書を構築してください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックをカバーしています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得したり、独自プロジェクトで代替実装アプローチを探求したりするのに役立ちます。

- [Aspose.Words for .NET を使用した Word 文書でのグループシェイプの作成](/words/english/net/working-with-shapes/add-group-shape/)
- [影付き矩形シェイプ付きの空白のWord文書を作成 – ステップバイステップガイド](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words for .NET を使用した Word 文書の作成](/words/english/net/add-content-using-document-builder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}