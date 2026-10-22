---
category: general
date: 2026-10-13
description: C#でWordの図形をグループ化 – Aspose.Words を使用して図形をグループ化し、グループに図形を追加する方法を簡単な手順で学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- add shapes to group
language: ja
lastmod: 2026-10-13
og_description: C# と Aspose.Words を使用して Word で図形をグループ化します。このガイドに従って、図形をグループ化し、Word
  文書内のグループに図形を追加する方法を学びましょう。
og_image_alt: Screenshot of a Word document showing two shapes combined into a single
  grouped shape
og_title: C#でWordの図形をグループ化する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  headline: Group shapes in Word using C# – complete programming guide
  type: TechArticle
- description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  name: Group shapes in Word using C# – complete programming guide
  steps:
  - name: Load the Word document
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Retrieve the shapes you want to group
    text: '```csharp // Get the first shape (index 0) and second shape (index 1) from
      the whole document. Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0,
      true); Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true); ```'
  - name: Create a new `GroupShape` container
    text: '```csharp GroupShape groupShape = new GroupShape(doc); ```'
  - name: Add the individual shapes to the group
    text: '```csharp groupShape.AppendChild(firstShape); groupShape.AppendChild(secondShape);
      ```'
  - name: Insert the group shape into the document body
    text: '```csharp // Insert the group as the last child of the first paragraph.
      Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph; firstParagraph.AppendChild(groupShape);
      ```'
  - name: Save the modified document
    text: '```csharp string outputPath = @"YOUR_DIRECTORY\output.docx"; doc.Save(outputPath);
      ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: C#でWordの図形をグループ化する – 完全プログラミングガイド
url: /ja/net/programming-with-shapes/group-shapes-in-word-using-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#でWordのシェイプをグループ化する – 完全プログラミングガイド

Wordでシェイプをプログラムで**グループ化**する必要がある場合、このガイドで正確な方法を示します。最初の2文が終わる頃には、必要なコード、各ステップの理由、そして**シェイプをグループに追加**する方法がサプライズなしで分かります。

`.docx` ファイルの読み込みから更新されたドキュメントの保存まで、すべてをカバーします。このチュートリアルは、基本的な C# の知識と Aspose.Words for .NET ライブラリへの参照があることを前提としています。外部ドキュメントは不要で、コピーして貼り付け、実行するだけです。

## 前提条件

- .NET 6.0 以降（コードは .NET Framework 4.7+ でも動作します）
- Aspose.Words for .NET NuGet パッケージ（`Install-Package Aspose.Words`）
- 既に少なくとも2つのシェイプ（画像や AutoShape など）を含む Word ドキュメント（`input.docx`）

> **プロのコツ:** テストする場合は、Word の UI で矩形を2つ作成したシンプルな Word ファイルを作りましょう。`input.docx` として、管理できるフォルダーに保存してください。

## Wordでシェイプをグループ化する – ステップバイステップガイド

以下では、プロセスを5つの論理的ステップに分解します。各ステップには正確な C# コード、*なぜ*その行が必要かの説明、そして一般的な落とし穴に関する短いメモが含まれます。

### 手順 1: Word ドキュメントを読み込む

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
```

**Why:** `Document` は Word 操作のエントリーポイントです。完全なファイルパスを指定することで、ドキュメントがメモリに読み込まれ、ノードツリーのクエリや変更が可能になります。

**Pitfall:** 作業ディレクトリが異なる場合、相対パスを渡すと失敗することがあります。絶対パスを使用するか、`AppContext.BaseDirectory` と `Path.Combine` を使ってください。

### 手順 2: グループ化したいシェイプを取得する

```csharp
// Get the first shape (index 0) and second shape (index 1) from the whole document.
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);
```

**Why:** `GetChild` はドキュメントツリーを走査し、要求されたタイプの *n 番目* のノードを返します。`isDeep` を `true` に設定すると、現在のセクションだけでなくドキュメント全体を検索します。

**Edge case:** ドキュメントにシェイプが2つ未満しかない場合、`firstShape` または `secondShape` が `null` となり、キャストしようとしたときに例外がスローされます。これを防ぐには次のようにします:

```csharp
if (firstShape == null || secondShape == null)
    throw new InvalidOperationException("The document must contain at least two shapes to group.");
```

### 手順 3: 新しい `GroupShape` コンテナを作成する

```csharp
GroupShape groupShape = new GroupShape(doc);
```

**Why:** `GroupShape` は複数の `Shape` オブジェクトを保持できる親ノードとして機能します。`Shape` から継承しているため、通常のシェイプが許可される場所（例: 段落内）ならどこにでも挿入できます。

### 手順 4: 個々のシェイプをグループに追加する

```csharp
groupShape.AppendChild(firstShape);
groupShape.AppendChild(secondShape);
```

**Why:** `AppendChild` はシェイプを元の位置から新しいグループへ移動します。この呼び出しの後、元のシェイプは独立したノードとしては存在せず、`groupShape` の一部になります。

**Tip:** グループ化すると子シェイプの相対位置が自動的に調整されます。特定のレイアウトが必要な場合は、子を追加する*前に* `GroupShape.Bounds` プロパティを設定してください。

```csharp
// Example: set the group to start at (100, 100) points and be 300x200 points large.
groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);
```

### 手順 5: グループシェイプをドキュメント本文に挿入する

```csharp
// Insert the group as the last child of the first paragraph.
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
firstParagraph.AppendChild(groupShape);
```

**Why:** `GroupShape` はレンダリングされるために段落（またはテーブルセル）内に配置する必要があります。最初の段落に追加することで、既存のレイアウトを乱さずに表示位置を保証します。

### 手順 6: 変更されたドキュメントを保存する

```csharp
string outputPath = @"YOUR_DIRECTORY\output.docx";
doc.Save(outputPath);
```

**Why:** `Save` はメモリ上の変更を `.docx` ファイルに書き戻します。オーバーロードを変更すれば、ストリームや PDF に保存することも可能です。

**Result verification:** Microsoft Word で `output.docx` を開きます。元の2つのシェイプが単一のグループ化オブジェクトに結合されているはずです。グループを選択すると、標準的な Word のグループハンドルが表示されます。

## プログラムでシェイプをグループ化する方法 – 詳細な洞察

- **Node ownership:** `AppendChild` を呼び出すと、シェイプの `ParentNode` 参照が自動的に変更されます。これにより、ドキュメントを破損させる可能性のある「孤立」ノードが防止されます。
- **Preserving formatting:** グループ化してもシェイプの書式設定（塗りつぶし色、線のスタイルなど）は**失われません**。すべての子シェイプは元のプロパティを保持します。
- **Nested groups:** `GroupShape` は他の `GroupShape` オブジェクトを含めることができ、複数レベルの階層を実現します。内部のグループを他のシェイプと同様に扱えばよいです。

## 後でシェイプをグループに追加し管理する

最初のグループ作成後にさらにシェイプを追加する必要がある場合、同じ `GroupShape` インスタンスを再利用できます:

```csharp
// Assume we have a third shape somewhere in the document.
Shape thirdShape = (Shape)doc.GetChild(NodeType.Shape, 2, true);
groupShape.AppendChild(thirdShape);
```

後でグループ解除が必要なときは、`groupShape.GetChildNodes(NodeType.Shape, true)` を反復処理し、各子シェイプを希望する場所に再挿入します。

```csharp
foreach (Shape child in groupShape.GetChildNodes(NodeType.Shape, true))
{
    // Example: move each child back to the original paragraph.
    firstParagraph.AppendChild(child);
}
firstParagraph.RemoveChild(groupShape); // Remove the empty group container.
```

**Why this matters:** ワークフローによっては、一時的にグループ化（例: 複数オブジェクトの配置揃え）してから、個別の編集のためにグループ解除が必要になることがあります。

## 完全に実行可能なサンプル

以下は、単体でコンパイルしてそのまま実行できるプログラムです。`YOUR_DIRECTORY` を実際のフォルダー パスに置き換えてください。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Load the document.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2. Retrieve the first two shapes.
        Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);

        if (firstShape == null || secondShape == null)
        {
            Console.WriteLine("Document must contain at least two shapes.");
            return;
        }

        // 3. Create a GroupShape container.
        GroupShape groupShape = new GroupShape(doc);

        // Optional: define the group’s bounding box.
        groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);

        // 4. Add the shapes to the group.
        groupShape.AppendChild(firstShape);
        groupShape.AppendChild(secondShape);

        // 5. Insert the group into the first paragraph.
        Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(groupShape);

        // 6. Save the result.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Grouped shapes saved to {outputPath}");
    }
}
```

**Expected output:** `output.docx` を開くと、元の2つのシェイプが単一のグループ化オブジェクトとして表示されます。グループを選択すると、慣れ親しんだ Word のグループハンドルが表示され、全体を一括で移動、サイズ変更、回転させることができます。

## 結論

これで、C# と Aspose.Words を使用して **Word のシェイプをグループ化**する方法が分かり、**シェイプをグループに追加**し、後で操作またはグループ解除する正確な手順も確認できました。この手法は、レポートレイアウトの自動化、複合図の作成、または複数オブジェクトの正確な配置が必要な Word テンプレートの作成に最適です。

次に、異なるアンカータイプで **シェイプをグループ化**する方法や、グループ化オブジェクトへの **高度な書式設定**の適用、またはグループ化結果を PDF にエクスポートするなどの関連トピックを探求してください。グループの入れ子を試して、プログラムで複雑なグラフィックを構築してみましょう。

コーディングを楽しんでください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法に基づく密接に関連したトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Aspose.Words for .NET を使用した Word ドキュメントへのシェイプ挿入](/words/english/net/working-with-shapes/insert-shape/)
- [Aspose.Words for .NET を使用した Word ドキュメントでのグループシェイプ作成](/words/english/net/working-with-shapes/add-group-shape/)
- [Word シェイプへの影効果追加 – 完全 C# ガイド](/words/english/net/programming-with-shapes/add-shadow-effect-to-word-shapes-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}