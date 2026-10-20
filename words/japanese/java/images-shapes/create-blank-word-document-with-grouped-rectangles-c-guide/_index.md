---
category: general
date: 2026-07-23
description: C#で空白のWord文書を作成し、長方形の図形を追加します。Aspose.Words を使用して、図形の挿入方法と図形のグループ化方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- group shapes word
- how to insert shapes
- how to group shapes
language: ja
lastmod: 2026-07-23
og_description: C#で空白のWord文書を作成し、図形の挿入、長方形の追加、図形のグループ化をAspose.Wordsで学ぶ。
og_image_alt: Screenshot showing a blank Word document with two rectangle shapes grouped
  together
og_title: グループ化された長方形で空白のWord文書を作成 – C#チュートリアル
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  headline: Create blank word document with grouped rectangles – C# guide
  type: TechArticle
- description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  name: Create blank word document with grouped rectangles – C# guide
  steps:
  - name: What if I need more than two shapes?
    text: Just keep calling `builder.InsertShape(...)` and `group.AppendChild(...)`
      for each new shape. The group can hold any number of children.
  - name: Can I set fill colour or border on the rectangles?
    text: 'Absolutely. After creating a rectangle you can tweak its `FillColor`, `OutlineColor`,
      and `LineWidth`:'
  - name: How do I move the whole group after it’s been created?
    text: 'Use the group''s `Left` and `Top` properties, measured in points:'
  - name: What about scaling the group?
    text: Set `group.Width` and `group.Height` or use `group.ScaleX` / `group.ScaleY`.
      The child rectangles retain their proportions relative to the group.
  - name: Does this work with older .doc files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. The only limitation is that some newer shape features may be down‑sampled
      when saving to the older binary format.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: グループ化された矩形で空白のWord文書を作成 – C# ガイド
url: /ja/java/images-shapes/create-blank-word-document-with-grouped-rectangles-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# グループ化された長方形を含む空白のWord文書を作成 – C# ガイド

すでに形状のセットが含まれた **create blank word document** を作成したいと思ったことはありませんか？ しかし、うまくグループ化する方法が分からなかった… あなただけではありません。多くのレポート作成やテンプレート生成シナリオでは、プレースホルダーとして機能する数個の長方形があるクリーンなキャンバスが欲しく、これらを単一のユニットとして一緒に移動させたいものです。

このチュートリアルでは、Aspose.Words ライブラリを使用して **create blank word document**、**add rectangle shape**、そして **group shapes word** の正確な手順を順に解説します。最後まで実行すれば、2つの長方形がグループ化された状態の `.docx` ファイルが手に入り、以後の位置変更やサイズ変更が同時に両方に適用されます。

また、フォーラムや Stack Overflow でよく出る “**how to insert shapes**” と “**how to group shapes**” の質問にも答えます。外部ドキュメントは不要です—必要な情報はすべてここにあります。

---

## 前提条件

- .NET 6 以降（コードは .NET Core でもコンパイル可能）
- Aspose.Words for .NET（NuGet パッケージ `Aspose.Words`）
- C# の基本構文の理解（“Hello World” を書いたことがあれば問題ありません）

まだ Aspose.Words をインストールしていない場合は、以下を実行してください：

```bash
dotnet add package Aspose.Words
```

以上です—余計な DLL や COM インタープロは不要で、クリーンな NuGet 参照だけです。

## 手順 1: blank word document を作成し、builder を初期化する

最初に空の `Document` オブジェクトを作成します。これは新しい紙のようなものです。次に `DocumentBuilder` を添付します。これは Aspose が提供する、コンテンツ挿入に便利なツールです。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();               // <-- create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Why this matters:** `DocumentBuilder` がないと、低レベルのノードツリーを手動で操作する必要があり、エラーが起きやすくなります。builder は `.docx` ファイルの XML の複雑さを抽象化します。

## 手順 2: How to insert shapes – まずグループ コンテナを追加する

Aspose では、後で他の形状を保持できる *group shape* を挿入できます。これは **group shapes word** の基礎となります。

```csharp
        // Step 2: Insert a group shape that will act as a container
        Shape group = builder.InsertGroupShape();
```

> **Pro tip:** 子形状を追加するまでグループ自体は目に見えません。そのため、次のステップまで生成されたドキュメントに何も表示されません。

## 手順 3: Add rectangle shape – 実際に表示されるオブジェクト

ここでは **add rectangle shape** を2回行い、それぞれサイズを指定します。`InsertShape` メソッドは `ShapeType` とポイント単位の寸法を受け取ります（1 pt ≈ 1/72 インチ）。

```csharp
        // Step 3: Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); // 100 pt × 50 pt
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);  // 80 pt × 40 pt
```

> **Why rectangles?** 長方形は最もシンプルな幾何形状で、プレースホルダーやボタン風 UI モック、シンプルなグラフィック要素に最適です。

## 手順 4: How to group shapes – 長方形をグループに結合する

長方形を作成したので、先に挿入したグループ形状の子として追加することで **how to group shapes** を実行します。

```csharp
        // Step 4: Append the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);
```

> **What happens under the hood?** グループ形状はドキュメントの XML ツリーで親ノードになります。グループを移動すると、2つの長方形が一緒に移動し、相対位置が保たれます。

## 手順 5: Save the document – これでグループ化された形状の Word ファイルが完成です

最後に、ドキュメントをディスクに保存します。パスはご使用のマシンに存在する場所に変更してください。

```csharp
        // Step 5: Save the document with the grouped shapes
        doc.Save("GroupShape.docx");   // Creates a blank word document with grouped rectangles
    }
}
```

以上が全プログラムです。実行して `GroupShape.docx` を開くと、2つの長方形が一緒に配置されているのが確認できます。1つを選択すると、グループ全体がハイライトされます—これが **group shapes word** の期待通りの動作です。

## 完全なソースコードを一括で

便利なように、完全なコピー＆ペースト可能な例を以下に示します：

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape that will contain other shapes
        Shape group = builder.InsertGroupShape();

        // Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);

        // Add the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);

        // Save the document
        doc.Save("GroupShape.docx");
    }
}
```

**Expected output:** `GroupShape.docx` を開くと、空白ページに2つの長方形がグループ化されて表示されます。1つの長方形を選択すると自動的にもう1つも選択され、グループ化が成功したことが確認できます。

## よくある質問とエッジケースの対処

### 2つ以上の形状が必要な場合は？

`builder.InsertShape(...)` と `group.AppendChild(...)` を新しい形状ごとに呼び出し続ければ OK です。グループは任意の数の子を保持できます。

### 長方形に塗りつぶし色や枠線を設定できますか？

もちろんです。長方形を作成した後、`FillColor`、`OutlineColor`、`LineWidth` を調整できます：

```csharp
rect1.FillColor = System.Drawing.Color.LightBlue;
rect1.OutlineColor = System.Drawing.Color.DarkBlue;
rect1.LineWidth = 1.5;
```

### 作成後にグループ全体を移動するには？

ポイント単位で測定されるグループの `Left` と `Top` プロパティを使用します：

```csharp
group.Left = 150;   // move 150 pt from the left margin
group.Top  = 200;   // move 200 pt from the top of the page
```

### グループのスケーリングは？

`group.Width` と `group.Height` を設定するか、`group.ScaleX` / `group.ScaleY` を使用します。子長方形はグループに対する比例を保ちます。

### 古い .doc ファイルでも動作しますか？

Aspose.Words はファイル形式を抽象化しているため、同じコードが `.doc` と `.docx` の両方で動作します。唯一の制限は、古いバイナリ形式で保存する際に一部の新しい形状機能がダウンサンプルされる可能性があることです。

## 本番向けコードのプロティップ

- **Dispose of resources** – 大きなファイルを扱う場合は `Document` を `using` ブロックでラップしてメモリを速やかに解放してください。
- **Error handling** – カスタムフォントを埋め込む場合は `Aspose.Words.Fonts.FontSettingsException` を捕捉してください。
- **Performance** – 多数の形状を挿入する際は、`doc.LayoutOptions = new LayoutOptions { UpdateFields = false };` でレイアウト更新を一時的に無効にし、後で再有効化するとパフォーマンスが向上します。

## 結論

これで、Aspose.Words を使用した C# における **how to create blank word document**、**add rectangle shape**、そして **group shapes word** の方法が分かりました。この例は、重要な “**how to insert shapes**” と “**how to group shapes**” の手順を網羅し、各行の意図を説明するとともに、カスタマイズやエッジケース、ベストプラクティスにも触れています。

次のステップとして、**how to insert images**、**add text inside grouped shapes**、または **export the document to PDF** を試すことができます—いずれも `DocumentBuilder` と形状操作の同じパターンに従います。実験を続けてください。Aspose API はほぼすべての Word 自動化シナリオに対応できるほど豊富です。

コーディングを楽しんでください。問題があれば遠慮なくコメントを残してください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Aspose.Words for .NET を使用した Word 文書へのシェイプ挿入](/words/english/net/working-with-shapes/insert-shape/)
- [Aspose.Words for .NET を使用した Word 文書でのグループシェイプ作成](/words/english/net/working-with-shapes/add-group-shape/)
- [C# を使用した Word の長方形シェイプ作成 – ステップバイステップガイド](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}