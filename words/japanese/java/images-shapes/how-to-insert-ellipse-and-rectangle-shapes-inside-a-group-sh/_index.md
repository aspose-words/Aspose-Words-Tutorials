---
category: general
date: 2026-10-23
description: Aspose.Words を使用して Word に楕円を挿入し、長方形の図形を追加する方法を学びます。図形へのカーソル移動やグループ図形の作成方法も含まれます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert ellipse
- how to add rectangle
- move cursor to shape
- insert rectangle shape word
- how to create group shape
language: ja
lastmod: 2026-10-23
og_description: Aspose.Words を使用して Word に楕円を挿入し、長方形の図形を追加する方法。カーソルを図形に移動し、グループ図形を作成する手順をステップバイステップでご案内します。
og_image_alt: Screenshot of a Word document showing a group shape containing a rectangle
  and an ellipse
og_title: Wordのグループ図形に楕円形と長方形を挿入する方法
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to insert ellipse and how to add rectangle shape in Word
    using Aspose.Words. Includes move cursor to shape and how to create group shape.
  headline: How to insert ellipse and rectangle shapes inside a group shape with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Aspose.Wordsでグループシェイプ内に楕円形と長方形シェイプを挿入する方法
url: /ja/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words でグループ シェイプ内に楕円形と矩形を挿入する方法

Word 文書に **楕円形をプログラムで挿入する方法** を知りたい方のために、本ガイドではその全工程を示します。また、**矩形シェイプの追加方法**、**シェイプへカーソルを移動する方法**、そして複数の描画オブジェクトを保持する **グループ シェイプの作成方法** も学べます。

Word の自動化では描画オブジェクトの正確な配置が必要になることが多いです。このチュートリアルを終える頃には、矩形と楕円がグループ化された `.docx` ファイルを生成でき、さらにスタイリングやエクスポートに活用できます。必要なのは Aspose.Words for .NET ライブラリと .NET 開発環境だけです。

## 前提条件

開始する前に、以下が揃っていることを確認してください。

* .NET 6.0 以降がインストールされていること。
* Aspose.Words for .NET（NuGet パッケージ `Aspose.Words`）がプロジェクトに追加されていること。
* C# の基本構文と Visual Studio（または任意の IDE）に関する基礎知識。

これらの要件により、追加設定なしでコードがコンパイルできます。

## Word でグループ シェイプを作成する方法

グループ シェイプは、複数のシェイプを 1 つのユニットとして移動、回転、書式設定できるコンテナです。以下のコードは、特定のサイズ（300 × 200 ポイント）のグループを作成し、以降の描画操作の準備を行います。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapeDemo
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a group shape that will act as a container for other shapes.
        GroupShape group = builder.InsertGroupShape(300, 200);
        
        // The group shape is now part of the document.
        // Subsequent shape insertions will be placed inside this group.
```

*この手順が重要な理由*：グループ シェイプはローカル座標系を定義します。カーソルをグループ内に移動した後に追加されるすべてのシェイプは、グループの原点を基準に配置されるため、レイアウト計算がシンプルになります。

## 矩形シェイプを Word に追加する方法

グループが作成されたので、**矩形シェイプをグループ内に挿入**できます。矩形は背景や他のコンテンツのビジュアル プレースホルダーとして機能します。

```csharp
        // Move the cursor into the group so that the next shape is added to it.
        builder.MoveTo(group);
        
        // Insert a rectangle of width 100 points and height 50 points.
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

*解説*：`MoveTo(group)` はビルダーに対し、アクティブな挿入ポイントがグループ シェイプであることを指示します。カーソルを移動しないまま `InsertShape` を呼び出すと、矩形はドキュメント本体に追加され、グループ外になってしまいます。

## 楕円形を挿入する方法

矩形が配置されたら、次に **楕円形を挿入する方法** を示します。楕円は同じグループ内の中心に配置され、必要に応じて矩形と重なります。

```csharp
        // Keep the cursor inside the same group.
        builder.MoveTo(group);
        
        // Insert an ellipse of width 80 points and height 80 points.
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

*カーソルを移動する必要がある理由*：`InsertShape` の各呼び出しは現在のカーソル位置を基準にします。`MoveTo(group)` を再度呼び出すことで、楕円もグループの子要素となり、意図した階層構造が保たれます。

## 追加オブジェクトを挿入する前にシェイプへカーソルを移動する

後でさらにシェイプを追加する必要がある場合は、**シェイプへカーソルを移動**してから各挿入を行ってください。このパターンにより、グループ外への誤配置を防げます。

```csharp
        // Example: add a third shape, such as a line.
        builder.MoveTo(group);
        builder.InsertShape(ShapeType.Line, 150, 0);
```

*ヒント*：`MoveTo(group)` を再利用するコストは低く、コードの可読性も向上します。挿入コンテキストが明示的になるため、将来の保守も容易になります。

## ドキュメントを保存する

最後に、ドキュメントをディスクに永続化します。例では指定したフォルダーに `GroupShape.docx` として保存します。

```csharp
        // Save the document to the desired location.
        document.Save(@"C:\Temp\GroupShape.docx");
    }
}
```

保存したファイルを Microsoft Word で開くと、矩形と楕円が正しく配置された単一のグループが表示されます。

### 期待される出力

* `GroupShape.docx` という名前の `.docx` ファイル。
* ドキュメント内にサイズ 300 × 200 ポイントのグループ化された描画オブジェクト。
* グループ内には：
  * 原点に配置された矩形（100 × 50 ポイント）。
  * 矩形と重なる楕円（80 × 80 ポイント）。
  * カーソルを移動した後に追加したその他のシェイプ。

## 一般的なバリエーションとエッジケース

| 状況 | 推奨アプローチ |
|-----------|----------------------|
| **異なる単位サイズ** | Aspose.Words はポイント（1 pt = 1/72 in）を使用します。`InsertShape` を呼び出す前にセンチメートルやインチをポイントに変換してください。 |
| **グループ内のシェイプを回転させる** | シェイプを挿入した後、`ShapeBase` オブジェクトを取得し、`ShapeBase.RotationAngle` を設定します。 |
| **シェイプ内にテキストを追加する** | `ShapeBase.AppendChild(new Paragraph(document))` を使用し、続いて目的のテキストを含む `Run` を追加します。 |
| **DOCX ではなく PDF に保存する** | `document.Save("GroupShape.pdf", SaveFormat.Pdf);` を呼び出します。グループ階層は PDF 出力でも保持されます。 |

これらのバリエーションにより、同じ **楕円形を挿入する方法** のロジックをさまざまな実務シナリオに応用できます。

## プロのコツ

* **同じ `DocumentBuilder` インスタンスを再利用** – メモリ使用量が削減され、ドキュメント状態が一貫します。
* **シェイプの寸法を検証** – 幅や高さが極端に大きいと、古い Word バージョンで描画問題が発生することがあります。
* **スタイリングの前にグループ化** – すべての子要素を追加した後にグループに塗りつぶし色や線スタイルを適用すると、外観が統一されます。

## 結論

これで、Aspose.Words を使用して Word 文書のグループ化コンテナ内に **楕円形を挿入する方法** と **矩形シェイプを追加する方法** が理解できました。各挿入前に **シェイプへカーソルを移動** することで、階層が整然と保たれ、誤配置を防げます。完全なサンプルはコンパイル・実行でき、さらにカスタマイズやエクスポートが可能なグループ シェイプを生成します。

もっと学びたいですか？このテクニックを **グループ シェイプの作成方法** と組み合わせて複雑な図を作成したり、**矩形シェイプの挿入** とテキストボックスを組み合わせてリッチなレポートを生成したりしてみてください。ハッピーコーディング！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを基にした、密接に関連するトピックをカバーしています。各リソースには、ステップバイステップの解説と完全なコード例が含まれており、API の追加機能をマスターしたり、独自プロジェクトで代替実装を試したりするのに役立ちます。

- [Aspose.Words を使用して Word に矩形シェイプとグループ シェイプを作成する方法](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [C# で空白の Word 文書を作成し、隠し楕円シェイプを追加する方法](/words/english/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/)
- [C# でグループ シェイプ docx を作成し、インタラクティブ コントロールを追加する方法](/words/english/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}