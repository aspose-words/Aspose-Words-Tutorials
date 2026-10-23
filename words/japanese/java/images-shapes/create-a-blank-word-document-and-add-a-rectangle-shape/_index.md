---
category: general
date: 2026-10-23
description: 空白のWord文書を作成し、長方形の図形を追加し、Aspose.Words を使用して Word 内で図形を非表示にします。.NET 開発者向けのステップバイステップコード。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- how to insert shape
- hide shape word
language: ja
lastmod: 2026-10-23
og_description: 空白のWord文書を作成し、長方形のシェイプを追加して、Aspose.Wordsでそのシェイプを非表示にします。完全なC#サンプルに従ってください。
og_image_alt: Screenshot of a Word document containing a hidden rectangle shape
og_title: 空白のWord文書を作成し、非表示の長方形シェイプを追加する
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create a blank Word document, add a rectangle shape, and hide the shape
    in Word using Aspose.Words. Step‑by‑step code for .NET developers.
  headline: Create a blank Word document and add a rectangle shape
  type: TechArticle
tags:
- Aspose.Words
- .NET
- Word automation
title: 空白のWord文書を作成し、長方形の図形を追加する
url: /ja/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 空白のWord文書を作成し、長方形の図形を追加する

If you need to **空白のWord文書を作成**, this guide shows you how to do it with Aspose.Words for .NET. You’ll also learn **図形の挿入方法**—specifically a rectangle—and **図形を非表示にする** so it doesn’t affect the layout.

The tutorial walks through every line of code, explains why each step matters, and covers common pitfalls such as hidden‑shape visibility in different Word view modes. By the end you will have a fully functional `.docx` file that contains a hidden rectangle shape you can later reveal or manipulate programmatically.

## 前提条件

- .NET 6.0 以上（コードは .NET Framework 4.6+ でも動作します）
- Aspose.Words for .NET NuGet パッケージ（`Install-Package Aspose.Words`）
- Visual Studio 2022 や C# 拡張機能がインストールされた VS Code などの開発環境
- C# の構文と Word 文書の概念に関する基本的な知識

Aspose.Words は完全にメモリ上で動作するため、追加の Office インストールは不要です。

## 空白のWord文書を作成する

最初のステップは空の `Document` オブジェクトをインスタンス化することです。このオブジェクトは、まだセクションや段落、コンテンツが何も含まれていない Word ファイルを表します。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

**この点が重要な理由:**  
空白の `Document` はクリーンなキャンバスを提供します。既存のテンプレートから開始すると、hidden shape が不要なスタイルを継承する可能性があります。最初から作成することで、後で追加する長方形の図形が唯一の制御対象コンテンツになることが保証されます。

## 文書に長方形の図形を追加する

次に、文書にコンテンツを配置するために `DocumentBuilder` が必要です。ビルダーの `InsertShape` メソッドは、長方形、円、カスタム描画などの **図形を挿入** する標準的な方法です。

```csharp
// Step 2: Initialize a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(document);

// Step 3: Insert a rectangle shape of size 200x100 points
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**この点が重要な理由:**  
`InsertShape` は `Shape` オブジェクトを返し、さらに設定（色、線のスタイルなど）できます。サイズはポイント単位（1 ポイント = 1/72 インチ）で指定され、Word の内部測定システムと一致します。

### オプション: 長方形のスタイル設定

後で非表示を解除したときに長方形に可視の枠線を持たせたい場合は、線の太さと色を設定できます。

```csharp
rectangleShape.LineWeight = 0.5;               // Thin border
rectangleShape.LineColor = System.Drawing.Color.Blue;
```

これらの行はオプションです。次のステップで図形が非表示になるためです。

## Word で図形を非表示にする

Word では、図形をレイアウトから非表示にしつつ、文書のオブジェクトモデルの一部として残すことができます。`Hidden` プロパティを `true` に設定すると、通常表示では図形が見えなくなりますが、API 経由で選択可能なままです。

```csharp
// Step 4: Hide the shape so it does not appear in the layout
rectangleShape.Hidden = true;
```

**この点が重要な理由:**  
非表示の図形は、メタデータの保存や後で処理するプレースホルダー、特定の条件下でのみ表示する条件付きコンテンツ（例: 最終レポート生成時）に便利です。図形はファイル内に残るため、後で `rectangleShape.Hidden = false;` とプログラムで非表示を解除できます。

## 文書を保存する

最後に、文書をディスクに書き込みます。ファイル拡張子が Word の形式を決定し、`.docx` は最新の Open XML 形式です。

```csharp
// Step 5: Save the document with the hidden shape
string outputPath = @"C:\Temp\HiddenShape.docx";
document.Save(outputPath);
```

**結果:**  
`HiddenShape.docx` を Microsoft Word で開くと、空のページが表示されます。長方形は見えませんが、**Home → Select → Selection Pane** に移動すると、図形が一覧に表示され、表示/非表示を切り替えることができます。

## 完全な動作例

以下はコピーして貼り付け、実行できる完全なプログラムです。必要な `using` 文とコメントがすべて含まれています。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for content insertion
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape (200x100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Optional styling (comment out if not needed)
        rectangleShape.LineWeight = 0.5;
        rectangleShape.LineColor = System.Drawing.Color.Blue;

        // Hide the shape so it does not appear in the layout
        rectangleShape.Hidden = true;

        // Save the document
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**期待される出力:**  

- コンソールに保存パスが表示されます。  
- `HiddenShape.docx` は Word で空白ページとして開きます。  
- 長方形の図形は存在しますが非表示です。*Selection Pane* で確認するか、プログラムで `Hidden = false` を設定してファイルを再度開くことで確認できます。

## よくある質問とエッジケース

| 質問 | 回答 |
|----------|--------|
| **他の図形タイプも非表示にできますか？** | はい。任意の `Shape`（例: `ShapeType.Ellipse`、`ShapeType.Picture`）は `Hidden` プロパティをサポートしています。 |
| **非表示の図形はファイルサイズを増加させますか？** | 増加はごくわずかです（数キロバイト程度）。図形データは `.docx` パッケージ内の XML として保存されるためです。 |
| **図形を印刷プレビューでのみ表示したい場合はどうすればいいですか？** | `Hidden` の代わりに `Shape.IsPrint` プロパティを使用します。`IsPrint = false` に設定すると、印刷出力からは図形が非表示になりますが、画面上では表示されたままです。 |
| **後で図形の非表示を解除するには？** | 文書をロードし、図形を検索（例: `Shape.Name` で）してから `shape.Hidden = false;` と設定し、保存します。 |
| **.doc（バイナリ）形式でも動作しますか？** | はい、Aspose.Words は `document.Save("file.doc");` を使用して `.doc` に保存できます。非表示フラグは保持されます。 |

## プロのコツ

- **図形に名前を付ける**: `rectangleShape.Name = "PlaceholderRectangle";` とすると、後で `document.GetChildNodes(NodeType.Shape, true).Cast<Shape>().FirstOrDefault(s => s.Name == "PlaceholderRectangle")` で検索しやすくなります。
- **バッチ処理**: 多数の文書に非表示の図形を追加する必要がある場合、コードをメソッドにまとめて `DocumentBuilder` インスタンスを再利用します。
- **パフォーマンス**: 図形の作成はコストが低いですが、大きな文書を頻繁に保存すると I/O がボトルネックになることがあります。中間処理には `MemoryStream` の使用を検討してください。

## 結論

これで、Aspose.Words for .NET を使用して **空白のWord文書を作成**、**長方形の図形を追加**、そして **図形を非表示にする** 方法が分かりました。この手法により、後で表示または操作できる見えないプレースホルダーを埋め込むことができ、動的レポート生成、条件付きコンテンツ、文書テンプレート化に役立ちます。

次に学ぶべきことは？

- `ShapeType.Picture` を使用して長方形を画像やチャートに置き換える。
- ヘッダー/フッター セクションで **図形の挿入方法** を使用し、透かしスタイルのプレースホルダーを作成する。
- 非表示の図形と **長方形の図形を追加** に基づくデータ検証を組み合わせる（例: 図形の `AlternativeText` プロパティに JSON を保存）。

コーディングを楽しんでください。また、他の図形タイプや表示オプションを自由に試して、文書自動化のニーズに合わせてみてください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Word 文書の作成 – 長方形の図形と影の追加方法](/words/english/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/)
- [Aspose.Words for .NET を使用した Word 文書でのグループ図形の作成](/words/english/net/working-with-shapes/add-group-shape/)
- [非表示の楕円形を含む空白の Word 文書の作成 – 完全 C# ガイド](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}