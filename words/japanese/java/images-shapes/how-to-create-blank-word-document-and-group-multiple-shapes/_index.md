---
category: general
date: 2026-10-26
description: C#で空白のWord文書を作成し、グループシェイプの挿入方法を学んだ後、矩形シェイプをそのグループに追加します。このガイドでは、複数のシェイプをグループ化する手順をステップバイステップで解説します。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group multiple shapes
- insert rectangle shape
- how to insert group
- how to add rectangle
language: ja
lastmod: 2026-10-26
og_description: C#で空白のWord文書を作成し、グループの挿入方法を確認した後、矩形シェイプを追加します。完全なコード例で複数のシェイプのグループ化をマスターしましょう。
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle shape
og_title: 空白のWord文書を作成し、複数の図形をグループ化する – C#チュートリアル
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create a blank Word document in C# and learn how to insert a group
    shape, then add a rectangle shape to the group. This guide covers group multiple
    shapes step‑by‑step.
  headline: How to create blank Word document and group multiple shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: 空白のWord文書を作成し、複数の図形をグループ化する方法
url: /ja/java/images-shapes/how-to-create-blank-word-document-and-group-multiple-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 空白の Word ドキュメントを作成し、複数の図形をグループ化する方法

プログラムで **空白の Word ドキュメントを作成** したい場合、このチュートリアルで手順をすべて解説します。グループ図形を挿入し、そこに **矩形 (rectangle)** を追加する方法を見ていきます。空のドキュメントから図形のグループ化までのフルワークフローを網羅しています。

Word ファイルを扱う際は、複数の図形をまとめて配置することが多くなります。たとえば、複数の図形で構成されたダイアグラムです。本ガイドの最後まで読むと、**複数の図形をグループ化** し、**矩形図形を挿入** し、**グループの挿入方法** と **矩形の追加方法** をクリーンかつ再利用可能な形で実装できるようになります。

## 必要なもの

* .NET 6.0 以降（コードは .NET Framework 4.6+ でも動作します）
* **Aspose.Words for .NET** NuGet パッケージ (`Install-Package Aspose.Words`)
* C# と Visual Studio IDE の基本的な知識（他の IDE でも可）

> **プロのコツ:** Aspose.Words は完全にオフラインで動作します。パッケージをインストールすれば、インターネット接続は不要です。

## 手順 1: 空白の Word ドキュメントを作成する

最初の操作は空の `Document` オブジェクトをインスタンス化することです。このオブジェクトが、後で図形を追加する **空白の Word ドキュメント** を表します。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – create a new blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*重要性:* セクションや段落が何もない `Document` でも、有効な .docx ファイルです。クリーンな状態から開始することで、後から追加する図形に対して隠れた書式設定が干渉することを防げます。

## 手順 2: グループ図形を挿入する（how to insert group）

**グループ図形** は、他の描画オブジェクトを保持できるコンテナのようなものです。Aspose.Words では `InsertGroupShape` で作成します。

```csharp
        // Step 2 – insert a group shape that will hold other shapes
        GroupShape group = builder.InsertGroupShape();   // <-- container for shapes
```

*なぜグループ化するのか？* グループ化すると、複数の図形を 1 つの単位として移動、回転、サイズ変更できます。要素の位置合わせが必要なダイアグラムでは必須の機能です。

## 手順 3: 矩形図形を挿入する（insert rectangle shape）

次に、ドキュメントに矩形を追加します。`InsertShape` メソッドは `Shape` オブジェクトを返し、後でグループに結び付けられます。

```csharp
        // Step 3 – create a rectangle shape with specific dimensions
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

*なぜ矩形か？* 矩形はフローチャート、UI モックアップ、プレースホルダー画像などで最も頻繁に使用される基本形状です。サイズはポイント単位で指定します（1 pt ≈ 1/72 インチ）。

## 手順 4: 矩形をグループに追加する（how to add rectangle）

`InsertShape` で作成した図形はドキュメント本体に直接配置されます。これをグループの一部にするには、`GroupShape` の `AppendChild` を呼び出します。

```csharp
        // Step 4 – add the rectangle to the previously created group
        group.AppendChild(rectangle);   // <-- rectangle now belongs to the group
```

*内部で何が起きているか？* `AppendChild` は矩形ノードをドキュメントのメインストーリーからグループの内部コレクションへ移動させ、サイズと位置をグループの原点に対して相対的に保持します。

## 手順 5: ドキュメントを保存する

最後に、ファイルをディスクに書き出します。生成された `.docx` を Microsoft Word で開くと、グループ化された矩形が確認できます。

```csharp
        // Step 5 – save the document to a file
        doc.Save("GroupedShapeExample.docx");
    }
}
```

> **エッジケース:** 同じグループにさらに図形（円や線など）を追加したい場合は、**手順 3** と **手順 4** を新しい図形ごとに繰り返してから保存してください。グループは自動的にバウンディングボックスを拡張し、すべての子要素を包含します。

## 複数の図形をグループ化する方法 – 例の拡張

以下のスニペットは、同じグループに 2 番目の図形（楕円）を追加する例です。これにより、**複数の図形をグループ化** する方法が示されています。

```csharp
        // Additional shape: an ellipse
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
        group.AppendChild(ellipse);   // now the group contains rectangle + ellipse
```

`GroupedShapeExample.docx` を開くと、矩形と楕円が Word でグループを選択したときに一緒に移動することが確認できます。

## よくある質問とトラブルシューティング

| 質問 | 回答 |
|----------|--------|
| **Aspose.Words のライセンスは必要ですか？** | 無料評価版はライセンスなしで動作しますが、透かしが入ります。製品版ではライセンスを適用して透かしを除去し、パフォーマンスを最大化してください。 |
| **図形の位置を正確に指定できますか？** | はい。図形を挿入した後、`Shape.Left`, `Shape.Top`, `Shape.Width`, `Shape.Height` プロパティで位置とサイズを設定できます。 |
| **保存後に矩形が消えてしまう場合は？** | 矩形を挿入した後、必ず `group.AppendChild(rectangle)` を **先に** 呼び出してください。まずドキュメント本体に図形を追加し、次にグループへ移動する必要があります。 |
| **異なるセクション間で図形をグループ化できますか？** | できません。グループ内のすべての図形は同じストーリー（セクション）に属している必要があります。必要に応じてセクションごとに別々のグループを作成してください。 |

## まとめ

これで **空白の Word ドキュメントを作成**、**グループを挿入**、**矩形を追加**、そして **複数の図形をグループ化** する方法が習得できました。上記の完全なサンプルはコンソール アプリにコピーしてすぐに実行できます。

## 次のステップ

* **矩形図形** のサイズや色を変更してみましょう（例: `rectangle.FillColor = Color.LightBlue;`）。  
* 他の図形タイプ（`ShapeType.Polygon`, `ShapeType.Line`）を試して、ダイアグラムを豊かにしましょう。  
* 最終的な `.docx` を PDF に変換して配布できるようにします（例: `doc.Save("output.pdf");`）。  
* 既存のテキストがある文書に **矩形を追加** する方法を学びましょう – `DocumentBuilder.MoveTo` を使って、グループを必要な位置に配置できます。

コードを自分のレポートやダイアグラム生成のニーズに合わせて自由にカスタマイズしてください。ハッピーコーディング！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを基にした、密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作サンプルが含まれており、API の追加機能をマスターしたり、独自の実装アプローチを探求したりするのに役立ちます。

- [空白の Word ドキュメントを作成し、C# で図形をグループ化する方法](/words/english/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/)
- [Word で図形をグループ化し、文書に図形を追加する方法](/words/english/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/)
- [Aspose.Words で矩形図形を作成し、図形をグループ化する方法](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}