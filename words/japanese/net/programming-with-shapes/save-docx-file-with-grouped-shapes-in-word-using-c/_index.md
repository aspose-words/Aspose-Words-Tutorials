---
category: general
date: 2026-08-04
description: Wordで矩形シェイプとグループシェイプを追加しながら、プログラムでdocxファイルを保存する方法。シェイプのサイズ設定やテキストボックスの作成をプログラムで学ぶ。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx file
- add rectangle shape
- group shapes word
- set shape dimensions
- create textbox programmatically
language: ja
lastmod: 2026-08-04
og_description: C# を使用して矩形シェイプを追加し、Word でシェイプをグループ化し、シェイプのサイズを設定し、プログラムでテキストボックスを作成して
  docx ファイルを保存する。
og_image_alt: Screenshot of a saved docx file that contains a grouped rectangle and
  textbox
og_title: Wordでグループ化されたシェイプを含むdocxファイルを保存する – C#ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  headline: Save docx file with grouped shapes in Word using C#
  type: TechArticle
- description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  name: Save docx file with grouped shapes in Word using C#
  steps:
  - name: 1. Create a new document and a builder
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing; using Aspose.Words.Drawing.Shapes;'
  - name: 2. Add rectangle shape to a group
    text: '```csharp // Create a group container that will hold all shapes. GroupShape
      group = new GroupShape(doc) { Width = 400, // Set shape dimensions for the group.
      Height = 200 };'
  - name: 3. Group shapes in Word document
    text: The `GroupShape` class aggregates multiple drawing objects. Grouping is
      useful when you want to treat several objects as a single unit (e.g., moving,
      rotating, or copying them together).
  - name: 4. Set shape dimensions for precise layout
    text: Both the group and its child shapes need explicit dimensions; otherwise
      Word applies default sizes that may not match your design.
  - name: 5. Create textbox programmatically inside the group
    text: '```csharp // Add a textbox shape with custom text. Shape textBox = new
      Shape(doc, ShapeType.TextBox) { Width = 180, Height = 100, Left = 210, // Position
      relative to the group’s coordinate system. Top = 10 };'
  - name: 6. Insert group shape and **save docx file**
    text: '```csharp // Insert the completed group into the document at the current
      cursor position. builder.InsertNode(group);'
  - name: Expected output
    text: '* A file named **GroupShape.docx** appears in the output directory. * Opening
      the file shows a rectangular shape on the left and a textbox containing “Grouped
      text” on the right, both locked together. * Selecting either shape moves the
      entire group, confirming that **group shapes word** functionalit'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: C# を使用して Word でグループ化されたシェイプを含む docx ファイルを保存する
url: /ja/net/programming-with-shapes/save-docx-file-with-grouped-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# を使用して Word でグループ化されたシェイプを含む docx ファイルを保存する

複数のシェイプを一緒に配置した **save docx file** が必要な場合、このガイドでは C# での実装方法を示します。**add rectangle shape** の方法、Word 文書内でシェイプをグループ化する手順、**set shape dimensions** の設定方法、そして **create textbox programmatically** の作成方法を学べます。ソリューションは最新の Aspose.Words for .NET に対応しており、.NET 6 以降で動作します。

このチュートリアルは、プロジェクトのセットアップから最終的な `doc.Save` 呼び出しまでのすべての手順を解説します。完了すると、任意のコンソール アプリや ASP.NET プロジェクトに貼り付け可能な再利用可能なコード スニペットが手に入ります。外部スクリプトや DOCX ファイルの手動編集は不要です。

## 前提条件

開始する前に、以下が揃っていることを確認してください。

* .NET 6 SDK（またはそれ以降）がインストールされていること。
* **Aspose.Words for .NET** の有効なライセンス（無料トライアルでもテストは可能）。
* Visual Studio 2022、VS Code、または .NET プロジェクトをビルドできる任意の IDE。

コードは Aspose.Words 名前空間のみを使用するため、追加の NuGet パッケージは不要です。

## Word でグループ化されたシェイプを含む docx ファイルを保存する

ソリューションの核心は、矩形とテキスト ボックスを含む `GroupShape` を作成し、これを文書に挿入して `doc.Save` を呼び出すことです。以下のセクションでプロセスを段階的に解説します。

### 1. 新しいドキュメントとビルダーを作成する

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // Initialize a blank document.
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for editing the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*このステップが重要な理由* – 新規の `Document` オブジェクトは空の *.docx* ファイルを表します。`DocumentBuilder` は `InsertNode` などの高レベルメソッドを提供し、グループ シェイプの配置に使用します。

### 2. グループに矩形シェイプを追加する

```csharp
        // Create a group container that will hold all shapes.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,   // Set shape dimensions for the group.
            Height = 200
        };

        // Add a rectangle shape that will be part of the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,   // Set shape dimensions for the rectangle.
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);
```

*このステップが重要な理由* – **add rectangle shape** の操作は、正確なサイズと位置を持つビジュアル要素を定義する方法を示します。矩形は `group` の内部に存在するため、後でグループ全体を移動すると矩形も自動的に移動します。

### 3. Word 文書内でシェイプをグループ化する

`GroupShape` クラスは複数の描画オブジェクトを集約します。グループ化は、複数のオブジェクトを単一ユニットとして扱いたい場合（例: 移動、回転、コピー）に便利です。

```csharp
        // The group now contains the rectangle; we will add more shapes next.
```

*グループ化する理由* – グループ化によりレイアウトの複雑さが軽減されます。各シェイプを個別に配置する代わりに、グループの `Left`、`Top`、`Width`、`Height` を一度だけ調整すれば済みます。

### 4. 正確なレイアウトのためにシェイプのサイズを設定する

グループ本体と子シェイプの両方に明示的なサイズが必要です。さもなければ Word はデフォルトサイズを適用し、デザインと合致しないことがあります。

```csharp
        // Example of adjusting the group’s overall size.
        group.Width = 400;   // Overall width of the grouped area.
        group.Height = 200;  // Overall height of the grouped area.
```

*サイズを設定する理由* – 正確な測定により、矩形とテキスト ボックスが意図せず重なり合うことを防ぎ、最終的な **save docx file** が期待通りのレイアウトになることが保証されます。

### 5. グループ内にテキスト ボックスをプログラムで作成する

```csharp
        // Add a textbox shape with custom text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,   // Position relative to the group’s coordinate system.
            Top = 10
        };

        // Populate the textbox with a paragraph containing a run.
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);

        // Append the textbox to the same group.
        group.AppendChild(textBox);
```

*このステップが重要な理由* – **create textbox programmatically** のセクションは、シェイプ内にリッチテキストを埋め込む方法を示します。`Paragraph` と `Run` を使用することで、後からフォーマットを完全に制御できます。

### 6. グループ シェイプを挿入し **docx ファイルを保存する**

```csharp
        // Insert the completed group into the document at the current cursor position.
        builder.InsertNode(group);

        // Save the document to the file system.
        doc.Save("GroupShape.docx");   // The file now contains a rectangle and a textbox grouped together.
    }
}
```

*最終ステップが重要な理由* – `InsertNode` 呼び出しは、ビルダーのカーソル位置にグループ化されたシェイプを正確に配置します。`doc.Save` メソッドが **save docx file** 操作を実行し、完全な Word 文書をディスクに書き出します。

> **結果:** Microsoft Word で *GroupShape.docx* を開くと、左側に矩形、右側にテキスト ボックスが表示され、両方が単一のグループとしてロックされています。グループ全体をユニットとして移動・サイズ変更したり、追加の書式設定を適用したりできます。

## 完全な実行可能サンプル

以下のコードを新しいコンソール プロジェクト（`dotnet new console`）に貼り付け、`dotnet run` を実行してください。プログラムはプロジェクトの出力フォルダーに `GroupShape.docx` を作成します。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a group shape container.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,
            Height = 200
        };

        // 3. Add rectangle shape.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);

        // 4. Add textbox shape with text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,
            Top = 10
        };
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);
        group.AppendChild(textBox);

        // 5. Insert the group into the document.
        builder.InsertNode(group);

        // 6. Save the document.
        doc.Save("GroupShape.docx");
    }
}
```

### 期待される出力

* 出力ディレクトリに **GroupShape.docx** という名前のファイルが生成されます。
* ファイルを開くと、左側に矩形シェイプ、右側に「Grouped text」というテキストが入ったテキスト ボックスが表示され、両方がロックされた状態です。
* いずれかのシェイプを選択するとグループ全体が移動し、**group shapes word** 機能が期待通りに動作していることが確認できます。

## 一般的なバリエーションとエッジケース

| Situation | Recommendation |
|-----------|----------------|
| 2 つ以上のシェイプが必要 | `builder.InsertNode` を呼び出す前に、追加の `Shape` オブジェクトを `group` に Append してください。 |
| 特定のページにグループを表示したい | `builder.MoveToDocumentEnd()` または `builder.MoveToPage(pageNumber)` でビルダーのカーソルを移動します。 |
| 異なる単位（例: センチメートル）を使用したい | `ConvertUtil.InchToPoint(1.0)` を使ってインチをポイントに変換し、Word が期待する単位に合わせます。 |
| テキスト ボックスに文字列を回り込ませたい | テキスト ボックス作成後に `textBox.TextBoxWrap = TextBoxWrapType.Square` を設定します。 |
| 古い .NET Framework バージョンで作業する場合 | 同じ API は .NET Framework 4.7 以降でも動作しますが、適切なバージョンの Aspose.Words を参照してください。 |

**プロのコツ:** 子シェイプをすべて追加した **後** にグループの `Width` と `Height` を設定してください。これにより、グループが内容全体を完全に囲み、Word で開いたときにクリッピングが発生しません。

## 結論

Aspose.Words for .NET を使用して、**save docx file** と同時に **add rectangle shape**、**group shapes word**、**set shape dimensions**、そして **create textbox programmatically** を実現する方法が理解できました。完全なサンプルは、チャートや画像など、より複雑なレイアウトにも応用できるクリーンで再利用可能なパターンを示しています。

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを基にした関連トピックを扱っています。各リソースには、ステップバイステップの説明と完全なコード例が含まれており、API の追加機能を習得したり、独自プロジェクトで代替実装を検討したりする際に役立ちます。

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}