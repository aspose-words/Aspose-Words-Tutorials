---
category: general
date: 2026-11-22
description: C#でプログラム的にWord文書を作成し、長方形のシェイプを挿入し、複数のシェイプを挿入し、Aspose.Wordsを使用してシェイプを書き込む。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- insert rectangle shape
- insert multiple shapes
- write shapes to word
language: ja
lastmod: 2026-11-22
og_description: C#でプログラム的にWord文書を作成し、長方形シェイプを挿入、複数のシェイプを追加し、Aspose.Wordsを使用してシェイプを書き込む。
og_image_alt: Screenshot of a Word document showing a rectangle and an ellipse grouped
  together
og_title: C#でプログラム的にシェイプ付きWord文書を作成する
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  headline: Programmatically create Word document with shapes in C#
  type: TechArticle
- description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  name: Programmatically create Word document with shapes in C#
  steps:
  - name: '**Initialize** a new `Document` and a `DocumentBuilder`.'
    text: '**Initialize** a new `Document` and a `DocumentBuilder`.'
  - name: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
    text: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
  - name: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
    text: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: C#でプログラム的に図形付きWord文書を作成する
url: /ja/net/programming-with-shapes/programmatically-create-word-document-with-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# でシェイプを含む Word 文書をプログラムで作成する

カスタムグラフィックを含む **Word 文書をプログラムで作成** する必要がある場合、このガイドでは Aspose.Words for .NET を使用してその方法を示します。矩形シェイプの挿入、追加シェイプの追加、グループ化、そして最終的にシェイプを Word に書き出す方法を、数行の C# で学びます。

グラフィック付きの Word ファイルを作成するために、手動での編集やマクロスクリプトはもはや必要ありません。このチュートリアルの最後までに、矩形と楕円をグループ化した `.docx` ファイルを生成する再利用可能なメソッドが手に入り、下流の処理やレポート作成にすぐに利用できます。

## 必要なもの

- .NET 6.0 以降（コードは .NET Framework 4.6+ でも動作します）
- Aspose.Words for .NET（NuGet パッケージ `Aspose.Words`）
- Visual Studio 2022 などの IDE（C# をコンパイルできるエディタであれば何でも構いません）

> **プロのコツ:** コーディングを始める前に CLI コマンド `dotnet add package Aspose.Words` でパッケージをインストールしてください。

## プログラムで Word 文書を作成する – 概要

全体のフローは 3 つの論理的フェーズで構成されています。

1. **Initialize**（初期化）: 新しい `Document` と `DocumentBuilder` を作成します。  
2. **Insert multiple shapes**（複数シェイプの挿入）: 矩形と楕円を挿入し、`GroupShape` 内に配置します。  
3. **Write shapes to Word**（シェイプを書き出す）: `Document` を `.docx` ファイルとして保存します。

各フェーズは以下の専用ステップにまとめられているので、コードをそのままプロジェクトにコピー＆ペーストできます。

![プログラムでグループ化されたシェイプを含む Word 文書を作成](grouped-shapes.png){: .align-center alt="プログラムでグループ化されたシェイプを含む Word 文書を作成"}

## ステップ 1: ドキュメントとビルダーの初期化

`Document` クラスは Word ファイル全体を表し、`DocumentBuilder` はコンテンツ追加のための流暢な API を提供します。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document document = new Document();

// Initialize a DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this matters:* `Document` を最初に作成することで、クリーンなキャンバスが得られます。`DocumentBuilder` は現在の挿入位置を追跡し、後でシェイプを段落階層に添付する際に不可欠です。

## ステップ 2: グループシェイプコンテナの挿入

`GroupShape` は複数の個別シェイプを単一のユニットとして扱えるようにします。これにより、シェイプをまとめて移動やサイズ変更が可能になります。

```csharp
// Insert a group shape container at the current cursor position
GroupShape groupShape = builder.InsertGroupShape();
```

*Explanation:* `InsertGroupShape` は空のコンテナを挿入し、自動的に現在のシェイプとして設定します。グループを閉じるまで、以降のシェイプ挿入はすべてこのコンテナに追加されます。

## 矩形シェイプの挿入

まず最初のグラフィックとして矩形を追加します。これにより **insert rectangle shape** の要件が満たされます。

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

矩形はグループの書式コンテキストを継承するため、`GroupShape` 内に表示されます。必要に応じて、後で線の色や塗りつぶし、テキストを設定することも可能です。

## 複数シェイプの挿入

**insert multiple shapes** 機能を示すために、矩形の直後に楕円を追加します。グループを閉じるまで、任意の数のシェイプ（例: 三角形、星形）を追加し続けることができます。

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

この時点でグループには矩形と楕円という 2 つの異なるシェイプが含まれます。同じ親を共有しているため、ユニットとして一括で移動できます。

## ステップ 3: グループシェイプを段落階層に添付する

Word 文書はコンテンツを段落ツリーに格納します。最終ファイルでグループを表示させるには、現在の段落に添付する必要があります。

```csharp
// Append the group shape to the current paragraph so it becomes part of the document flow
groupShape.AppendChild(builder.CurrentParagraph);
```

*Why this step is required:* グループを段落に追加しなければ、シェイプはメモリ上にのみ存在し、ドキュメント保存時に省略されます。

## ステップ 4: ドキュメントの保存 – シェイプを Word に書き出す

最後に、メモリ上の `Document` をディスクに永続化します。これにより **write shapes to word** の目標が達成されます。

```csharp
// Define the output path (adjust the folder as needed)
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");

// Save the document in DOCX format
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Microsoft Word で `GroupShape.docx` を開くと、コードが挿入した通りに矩形と楕円がグループ化された状態で表示されます。

### 期待される出力

- プロジェクトの出力フォルダーに **GroupShape.docx** という名前のファイルが作成されます。
- Word ファイル内部: 1 つの段落に、グループ化された矩形（100 pt × 50 pt）と楕円（80 pt × 40 pt）が含まれます。いずれかのシェイプを選択すると、グループ全体が選択されます。

## 一般的なエッジケースの対処

| 状況 | 推奨事項 |
|-----------|----------------|
| **異なる DPI またはページサイズ** | シェイプを挿入する前に `builder.PageSetup.PaperSize` を明示的に設定し、予期しないスケーリングを防止します。 |
| **シェイプを正確に配置する必要がある** | `builder.MoveTo` で挿入ポイントを移動し、`groupShape.Left` と `groupShape.Top` プロパティ（単位はポイント）を設定します。 |

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説付きの完全なコード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [C# で Word 文書を作成 – 矩形シェイプと影の挿入](/words/english/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/)
- [C# でプログラム的に Word 文書を作成しシェイプをグループ化](/words/english/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/)
- [プログラムでグループシェイプを含む Word 文書を作成](/words/english/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}