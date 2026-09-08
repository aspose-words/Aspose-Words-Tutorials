---
category: general
date: 2026-09-08
description: C# と Aspose.Words を使用して Word 文書にコンテンツコントロールを挿入する方法を学びます。コンテンツコントロールの作成、プレースホルダーの設定、ファイルの保存手順が含まれます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert content control
- create content control
language: ja
lastmod: 2026-09-08
og_description: C# と Aspose.Words を使用して Word ファイルにコンテンツコントロールを挿入します。このガイドに従ってコンテンツコントロールを作成し、プレースホルダー
  テキストを設定し、ドキュメントを保存してください。
og_image_alt: Insert content control example in a Word document
og_title: C#でWordにコンテンツコントロールを挿入する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to insert content control in a Word document using C# and
    Aspose.Words. Includes steps to create content control, set placeholder, and save
    the file.
  headline: How to insert content control in a Word document with C#
  type: TechArticle
tags:
- content control
- Aspose.Words
- C#
- Word automation
title: C#でWord文書にコンテンツコントロールを挿入する方法
url: /ja/net/programming-with-sdt/how-to-insert-content-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で Word 文書にコンテンツ コントロールを挿入する方法

Word 文書に **コンテンツ コントロール** を挿入する必要がある場合、このガイドでは完全な実行可能なソリューションを示します。また、プログラムで **コンテンツ コントロール** を作成し、プレースホルダー テキストを設定し、ファイルをディスクに書き込む方法も学べます。

コンテンツ コントロールを使用すると、ユーザーが入力、繰り返し、またはロックできる領域を定義できます。テンプレート、フォーム、動的レポートで広く使用されています。以下の手順は Aspose.Words for .NET ライブラリを使用しており、.NET 6+、.NET Framework 4.6+、および .NET Core で動作します。

## Word 文書にコンテンツ コントロールを挿入する方法

1. **プロジェクトに Aspose.Words を追加する**  
   プロジェクト フォルダーでターミナルを開き、次のコマンドを実行します:

   ```bash
   dotnet add package Aspose.Words
   ```

   このパッケージには、コンテンツ コントロールに必要な `Document`、`DocumentBuilder`、`StructuredDocumentTag` クラスが含まれています。

2. **新しい空の文書を作成する**  

   ```csharp
   // Step 1: Create a new empty document and a DocumentBuilder
   Document doc = new Document();
   DocumentBuilder builder = new DocumentBuilder(doc);
   ```

   `Document` オブジェクトは .docx ファイル全体を表し、`DocumentBuilder` はノード挿入用の便利なカーソルを提供します。

## Aspose.Words を使用したコンテンツ コントロールの作成

コンテンツ コントロールは `StructuredDocumentTag` (SDT) クラスで表されます。以下のコードは **プレーンテキスト** コンテンツ コントロールを作成し、後でクエリできるタイトルを付与します。

```csharp
// Step 2: Create a plain‑text StructuredDocumentTag (content control)
//         - Set a title that can be used to identify the control
//         - Provide placeholder text that appears when the control is empty
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,
    SdtType.PlainText,      // Plain‑text control
    MarkupLevel.Block);    // Block‑level control (behaves like a paragraph)

sdt.Title = "CustomerName";
sdt.PlaceholderName = "Enter name here";
```

*重要なポイント:*
- `SdtType.PlainText` はコントロールがプレーン文字のみを受け付けることを保証します。  
- `MarkupLevel.Block` はコントロールを完全な段落として動作させ、フォーム フィールドに最適です。  
- `Title` プロパティは、検索やデータバインディング時に使用できる安定した識別子です。

## プレースホルダーとデフォルト テキストの設定

プレースホルダーはユーザーが入力する前に案内します。また、コントロールにデフォルトのコンテンツを事前に設定することもできます。

```csharp
// Step 4: Optionally set default content for the control
sdt.XmlMapping.SetXmlFragment("<text>John Doe</text>");
```

XML フラグメントはコントロールのデータ型と一致する必要があります。プレーンテキスト コントロールの場合、`<text>` 要素が必須です。この手順を省略すると、以前に定義したプレースホルダーが代わりに表示されます。

## 任意の位置にコンテンツ コントロールを挿入する

`DocumentBuilder` のカーソルがコントロールの表示位置を決定します。デフォルトでは、カーソルは文書の先頭にあります。

```csharp
// Step 3: Insert the StructuredDocumentTag into the document at the builder's current position
builder.InsertNode(sdt);
```

テーブル、ヘッダー、または既存の段落の後にコントロールが必要な場合は、まずビルダーを移動させます:

```csharp
builder.MoveToDocumentEnd();   // Example: place the control at the end of the file
builder.InsertNode(sdt);
```

## 挿入したコンテンツ コントロール付きの文書を保存する

```csharp
// Step 5: Save the document with the content control
doc.Save(@"C:\Temp\SDT.docx");
```

ファイル `SDT.docx` には、プレーンテキスト コンテンツ コントロールが含まれ、タイトルは **CustomerName**、プレースホルダーは “Enter name here”、デフォルトテキストは “John Doe” となっています。

![Word 文書にコンテンツ コントロールを挿入した例](insert-content-control.png)

*画像の代替テキスト:* Word 文書にコンテンツ コントロールを挿入した例

### 期待される結果

Microsoft Word で `SDT.docx` を開くと:
- デフォルトテキストを削除すると、灰色のプレースホルダー “Enter name here” が表示されます。  
- コントロール内をクリックするとハイライトされ、編集可能であることが示されます。  
- **Developer** タブ（有効な場合）に、プロパティ ペインでコントロールのタイトル **CustomerName** が表示されます。

## 完全な動作例

以下は、コピーしてコンパイルし、実行できる単一の自己完結型プログラムです。プロジェクトの設定からファイルの保存までのすべての手順を示しています。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class InsertContentControlDemo
{
    static void Main()
    {
        // 1. Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a plain‑text content control (StructuredDocumentTag)
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            doc,
            SdtType.PlainText,
            MarkupLevel.Block);

        sdt.Title = "CustomerName";          // Identifier for later use
        sdt.PlaceholderName = "Enter name here";

        // 3. Insert the control at the current cursor position
        builder.InsertNode(sdt);

        // 4. Set default text (optional)
        sdt.XmlMapping.SetXmlFragment("<text>John Doe</text>");

        // 5. Save the document
        string outputPath = @"C:\Temp\SDT.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

`dotnet run` でプログラムを実行します。実行後、生成されたファイルを開き、コンテンツ コントロールが記載どおりに表示されていることを確認してください。

## 実用的なヒントと一般的な落とし穴

| Situation | Recommended approach |
|-----------|----------------------|
| **同じタイプの複数コントロール** | 各コントロールに固有の `Title` を付けます。後で `doc.GetChildNodes(NodeType.StructuredDocumentTag, true).Cast<StructuredDocumentTag>().FirstOrDefault(s => s.Title == "YourTitle")` を使用してコントロールを取得できます。 |
| **Word でコントロールが表示されない** | 文書を `.docx` 拡張子で保存し、`Aspose.Words` のバージョンが使用している Office バージョンと互換性があることを確認してください。 |
| **リッチテキスト コントロールが必要** | `PlainText` の代わりに `SdtType.RichText` を使用します。XML フラグメントは `<w:richText>` 要素を使用します。 |
| **テーブルセル内にコントロールを配置する** | まずビルダーをセルに移動させます: `builder.MoveTo(cell.FirstParagraph); builder.InsertNode(sdt);`。 |
| **大規模文書でのパフォーマンス** | `StructuredDocumentTag` を一度作成し、同一のコントロールが多数必要な場合は再利用します。`sdt.Clone(true)` でクローンを作成できます。 |

## 次のステップ

- **繰り返しコンテンツ コントロール** (`SdtType.RepeatingSection`) を作成し、動的に拡張するテーブルに使用します。  
- `sdt.XmlMapping.LoadXml(xmlString)` を使用してコンテンツ コントロールを XML データにバインドします。  
- ユーザーの編集を防ぎつつプログラムからの更新は許可するために、コントロールをロックします (`sdt.LockContentControl = true`)。  

これらのトピックを探求することで、Aspose.Words を使用した堅牢な Word テンプレートの構築能力が向上します。

---

**結論**  
これで、C# を使用して Word 文書に **コンテンツ コントロール** を挿入する方法が分かりました。このチュートリアルでは、コントロールの作成、プレースホルダーとデフォルトテキストの設定、目的の位置への挿入、最終ファイルの保存について説明しました。この基礎があれば、Word のネイティブ コンテンツ コントロール機能を活用した高度なフォーム、差し込み印刷テンプレート、そして自動レポートを構築できます。

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [コンテンツ コントロールのスタイル設定](/words/english/net/programming-with-sdt/set-content-control-style/)
- [コンテンツ コントロールの色設定](/words/english/net/programming-with-sdt/set-content-control-color/)
- [Aspose.Words for Java で DocumentBuilder を使用してフォーム フィールドを作成しコンテンツを追加する方法](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}