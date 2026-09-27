---
category: general
date: 2026-09-27
description: Aspose.Words を使用して C# でグループ シェイプを含む Word 文書をプログラムで作成します。このステップバイステップ
  ガイドに従ってファイルを生成し、便利なヒントを学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- how to create group shape word
- Aspose.Words group shape
- C# Word automation
- StructuredDocumentTag example
language: ja
lastmod: 2026-09-27
og_description: Aspose.Words を使用して、プログラムでグループ シェイプを含む Word 文書を作成します。このチュートリアルでは、完全な
  C# コードを順に解説し、各ステップを説明し、最終的な出力を示します。
og_image_alt: Screenshot of a Word document containing a group shape with a text placeholder
og_title: プログラムでグループシェイプ付きWord文書を作成する – C# ガイド
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  headline: Programmatically create a Word document with a group shape
  type: TechArticle
- description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  name: Programmatically create a Word document with a group shape
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works with .NET Framework 4.7+). - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`). - A C# IDE such as
      Visual Studio 2022 or VS Code with the C# extension.'
  - name: Expected output screenshot (conceptual)
    text: '``` +-----------------------------------------------------------+ | ┌───────────────────────────────────────────────┐
      | | │ [Enter text here] │ | | └───────────────────────────────────────────────┘
      | +-----------------------------------------------------------+ ```'
  - name: Adding more child shapes
    text: 'You can enrich the group by appending additional drawing objects, such
      as pictures or text boxes:'
  - name: Controlling wrapping style
    text: 'If you need the group shape to stay behind text or to have tight wrapping,
      set the `WrapType` property:'
  - name: 'Edge case: Empty group shape'
    text: A `GroupShape` without children renders as an invisible placeholder. Always
      verify that at least one child (e.g., an SDT or a picture) is added; otherwise
      Word may drop the group during saving.
  - name: Compatibility note
    text: Aspose.Words 23.10+ fully supports `GroupShape` and `StructuredDocumentTag`.
      If you target older versions, the `AppendChild` method may behave differently,
      and you might need to call `UpdatePageLayout` after saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: プログラムでグループシェイプを含むWord文書を作成する
url: /ja/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# プログラムでグループシェイプを持つ Word 文書を作成する

**プログラムで Word 文書** を作成し、そこにグループ化された図形を含める必要がある場合、このガイドでは Aspose.Words for .NET を使用した具体的な手順を示します。契約書ジェネレータ、レポートビルダー、フォーム入力ツールなどを構築する際に、完全な C# コード、各 API 呼び出しの意味、一般的なエッジケースの対処方法を学べます。

Word でグループシェイプを作成するのは、Word オブジェクトモデルがグループシェイプを他の描画オブジェクトのコンテナとして扱うため、やや難しく感じられることがあります。このチュートリアルでは **グループシェイプ Word 文書の作成方法** に答えるだけでなく、グループ内にプレーンテキストの StructuredDocumentTag (SDT) を埋め込んで、シェイプが編集可能なコンテンツを保持できるようにする方法も示します。

## 実現できること

- `Document` と `DocumentBuilder` を使用して新しい空白の Word 文書を初期化する
- カーソル位置に `GroupShape` を挿入する
- グループシェイプにプレーンテキストの `StructuredDocumentTag` (SDT) を追加する
- `.docx` として保存し、Microsoft Word で開けるようにする
- 将来の拡張に備えて `GroupShape` と `StructuredDocumentTag` の主要プロパティを理解する

### 前提条件

- .NET 6.0 以降（コードは .NET Framework 4.7+ でも動作します）
- Aspose.Words for .NET NuGet パッケージ（`Install-Package Aspose.Words`）
- Visual Studio 2022 や C# 拡張機能付き VS Code などの C# IDE

---

## プログラムで Word 文書を作成する – プロジェクトのセットアップ

1. **新しいコンソールプロジェクトを作成**  
   ```bash
   dotnet new console -n WordGroupShapeDemo
   cd WordGroupShapeDemo
   dotnet add package Aspose.Words
   ```
2. **IDE でプロジェクトを開き**、`Program.cs` の内容を次のセクションで示すコードに置き換えます。

> **プロのコツ:** プロジェクトフォルダーはできるだけ整理しておきましょう。Aspose.Words は絶対パスを指定しない限り、作業ディレクトリに出力ファイルを書き込みます。

## Step 1: Initialize the document and builder

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

// Create a new blank document.
Document doc = new Document();

// DocumentBuilder gives you a cursor to insert nodes.
DocumentBuilder builder = new DocumentBuilder(doc);

// Optional: set the page size or margins if your shape must fit a specific area.
builder.PageSetup.PageWidth = 595;   // A4 width in points
builder.PageSetup.PageHeight = 842;  // A4 height in points
```

**Why this matters:**  
`Document` は Word ファイル全体を表し、`DocumentBuilder` はノードツリーを手動でたどらずに新しい要素の位置を決められます。ページサイズを早めに設定しておくことで、グループシェイプがページからはみ出すのを防げます。

## Step 2: Insert a GroupShape at the current cursor location

```csharp
// Create an empty GroupShape container.
GroupShape groupShape = new GroupShape(doc)
{
    // Give the group a size that comfortably holds its children.
    Width = 300,
    Height = 150,

    // Position the group relative to the page (you can also use RelativeHorizontalPosition).
    Left = 100,
    Top = 100
};

// Insert the group shape into the document where the builder is currently positioned.
builder.InsertNode(groupShape);
```

**Explanation:**  
`GroupShape` は他のシェイプ、画像、テキストボックスなどを保持できる描画オブジェクトです。`Width`、`Height`、`Left`、`Top` を設定することで、ページ上の正確な配置を制御します。`InsertNode` メソッドはシェイプを本文のフローに挿入し、浮動オブジェクトとして振る舞います。

## Step 3: Add a plain‑text StructuredDocumentTag (SDT) inside the group

```csharp
// Create a plain‑text SDT that will act as a content placeholder.
StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Provide a helpful tag title that appears as a tooltip in Word.
    Title = "GroupShapeText",
    // Set default placeholder text.
    PlaceholderName = "Enter text here"
};

// Append the SDT to the group shape's child collection.
groupShape.AppendChild(sdtTag);
```

**Why use an SDT?**  
StructuredDocumentTag は Word のネイティブなコンテンツコントロールです。保存された文書内でユーザーが直接テキストを編集でき、後からプログラムでデータ抽出も可能です。グループシェイプ内に SDT を配置すれば、視覚的なグルーピングと編集可能なコンテンツを組み合わせられます。

## Step 4: Save the document

```csharp
// Define the output path – replace with your desired directory.
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShapeDemo.docx");

// Save the document in DOCX format.
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to: {outputPath}");
```

**Result:**  
Microsoft Word で `GroupShapeDemo.docx` を開くと、浮動矩形（グループシェイプ）内部に「Enter text here」というプレースホルダーが表示されます。ユーザーはシェイプ内をクリックして直接文字入力が可能です。

### Expected output screenshot (conceptual)

```
+-----------------------------------------------------------+
|   ┌───────────────────────────────────────────────┐   |
|   │  [Enter text here]                               │   |
|   └───────────────────────────────────────────────┘   |
+-----------------------------------------------------------+
```

外側の箱が `GroupShape`、内側の灰色領域が `StructuredDocumentTag` です。

---

## How to create group shape word – additional considerations

### Adding more child shapes

以下のように画像やテキストボックスなどの描画オブジェクトを追加して、グループを拡張できます：

```csharp
// Example: add a picture inside the same group.
Shape picture = new Shape(doc, ShapeType.Image)
{
    ImageData = ImageData.FromFile("logo.png"),
    Width = 100,
    Height = 50,
    Left = 10,
    Top = 80
};
groupShape.AppendChild(picture);
```

### Controlling wrapping style

テキストの背後に配置したり、タイトな折り返しにしたい場合は `WrapType` プロパティを設定します：

```csharp
groupShape.WrapType = WrapType.Inline; // Makes the shape behave like a paragraph.
```

### Edge case: Empty group shape

子要素がない `GroupShape` は目に見えないプレースホルダーとして描画されます。必ず少なくとも 1 つの子要素（例: SDT または画像）を追加してください。そうしないと保存時に Word がグループを削除してしまうことがあります。

### Compatibility note

Aspose.Words 23.10 以降は `GroupShape` と `StructuredDocumentTag` を完全にサポートしています。古いバージョンを対象とする場合、`AppendChild` の挙動が異なることがあり、保存後に `UpdatePageLayout` を呼び出す必要があるかもしれません。

---

## Complete runnable example

以下のコード全体を `Program.cs` に貼り付けてプロジェクトを実行してください。上記の手順をすべて含んだ、単一の自己完結型プログラムです。



## What Should You Learn Next?

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれており、追加の API 機能を習得したり、独自プロジェクトで代替実装を検討したりする際に役立ちます。

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}