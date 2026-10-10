---
category: general
date: 2026-10-10
description: 空白のWord文書を作成し、画像をWordに挿入し、画像グループを追加して、保存したファイルでシェイプを非表示にします。ステップバイステップのガイドに従ってください。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert image into word
- add image group
- hide shape word document
language: ja
lastmod: 2026-10-10
og_description: 空白のWord文書を作成し、画像をWordに挿入し、画像グループを追加してシェイプを非表示にします。このガイドでは、完全なC#コードを示しています。
og_image_alt: Screenshot of a blank Word document with a hidden image group
og_title: 空白のWord文書を作成し、画像グループを追加して、図形を非表示にする
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Create a blank Word document, insert image into Word, add an image
    group, and hide shape in the saved file. Follow this step‑by‑step guide.
  headline: Create a blank Word document, add an image group, hide shape
  type: TechArticle
tags:
- Word automation
- Aspose.Words
- C#
- Document processing
title: 空白のWord文書を作成し、画像グループを追加し、図形を非表示にする
url: /ja/java/images-shapes/create-a-blank-word-document-add-an-image-group-hide-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 空白のWord文書を作成し、画像グループを追加し、シェイプを非表示にする

空白のWord文書を**作成**し、後で視覚要素を非表示にしたい場合、このチュートリアルで正確な手順を示します。Wordに画像を挿入し、画像グループを追加し、シェイプを非表示にする方法を、単一の再利用可能なC#ルーチンで学びます。

Aspose.Words for .NET ライブラリを使用します。このライブラリを使うと、Microsoft Word をインストールせずに .docx ファイルを操作できます。このガイドの最後までに、非表示の画像グループを含む Word ファイルを生成する実行可能なプログラムが作成でき、下流処理や条件付き表示に利用できます。

## 前提条件

- .NET 6.0 以上（コードは .NET Framework 4.6+ でも動作します）
- Aspose.Words for .NET NuGet パッケージ（`Install-Package Aspose.Words`）
- 画像ファイルを読み取り、出力ドキュメントを書き込めるディスク上のフォルダー
- C# と Visual Studio（またはお好みの IDE）に関する基本的な知識

## Aspose.Words を使用して空白の Word 文書を作成する

最初のステップは**空白のWord文書を作成**することです。Aspose.Words は、メモリ上の Word ファイルを表す `Document` クラスを提供します。引数なしでインスタンス化すると、コンテンツを追加できる空の文書が得られます。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();                 // blank .docx container
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this matters:* 空白の文書から開始することで、後で追加するシェイプに影響を与える隠れた書式設定や残存セクションがないことが保証されます。

## DocumentBuilder を使用して Word に画像を挿入する

次に、画像を保持するグループシェイプを最初に作成することで、**Word に画像を挿入**します。グループシェイプを使用すると、複数の描画オブジェクトを単一のユニットとして扱えるため、後でそれらをまとめて非表示にしたり移動したりする際に便利です。

```csharp
        // Step 2: Insert a group shape with the desired size (width: 300, height: 200)
        GroupShape group = builder.InsertGroupShape(300, 200);
```

`InsertGroupShape` メソッドは空のコンテナを作成します。サイズはポイント単位（1 ポイント = 1/72 インチ）です。埋め込む画像の解像度に合わせてサイズを調整してください。

## 文書に画像グループを追加する

ここでは、ビルダーのカーソルを新しく作成したグループ内に移動し、画像を挿入することで**画像グループを追加**します。その後のすべての挿入はグループの一部となります。

```csharp
        // Step 3: Position the builder inside the group so subsequent inserts go into it
        builder.MoveTo(group);

        // Step 4: Add an image to the group shape
        // Replace the path with the actual location of your PNG/JPEG file
        builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");
```

*Tip:* 絶対パスまたは正しくエスケープされた相対パスを使用してください。そうしないと `InsertImage` が `FileNotFoundException` をスローします。

## Word 文書でシェイプを非表示にする

最後に、グループの `Hidden` プロパティを `true` に設定することで**シェイプを Word 文書で非表示**にします。非表示のシェイプは Word で文書を開いたときに表示されませんが、ファイル内には残り、後でプログラムから再表示できます。

```csharp
        // Step 5: Hide the entire group (the image will not be visible in the saved document)
        group.Hidden = true;

        // Step 6: Save the document with the hidden group
        doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");
    }
}
```

Microsoft Word で *GroupHidden.docx* を開くと、画像グループが非表示になっているため完全に空白のページが表示されます。ファイルには画像データが残っており、必要に応じて `group.Hidden = false` で再表示できます。

## 完全な実行可能サンプル

以下は、新しいコンソールプロジェクトにコピー＆ペーストできる完全なプログラムです：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a group shape (300 pt × 200 pt)
            GroupShape group = builder.InsertGroupShape(300, 200);

            // 3️⃣ Move inside the group so inserts become part of it
            builder.MoveTo(group);

            // 4️⃣ Insert the image (replace with your own file)
            builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");

            // 5️⃣ Hide the group so the image is not shown
            group.Hidden = true;

            // 6️⃣ Save the result
            doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");

            Console.WriteLine("Document created successfully.");
        }
    }
}
```

**期待される出力**

- `GroupHidden.docx` という名前のファイルが `YOUR_DIRECTORY` に作成されます。
- Word でファイルを開くと空白ページが表示されます。
- `group.Hidden = false` に変更して再保存することで、非表示の画像を表示できます。

## 一般的なバリエーションとエッジケース

| Situation | How to adapt the code |
|-----------|----------------------|
| **Multiple images** | `builder.MoveTo(group)` の後に追加の `InsertImage` 呼び出しを挿入します。すべての画像は同じグループ内に留まり、非表示フラグを共有します。 |
| **Different image formats** | Aspose.Words は PNG、JPEG、BMP、GIF、TIFF をサポートします。拡張子を変更するだけで、コードの変更は不要です。 |
| **Conditional visibility** | カスタムドキュメント変数（`doc.Variables.Add("ShowImages", "true")`）を保存し、実行時にその値に基づいて `group.Hidden` を切り替えます。 |
| **Large documents** | レイアウトシフトを防ぐため、グループを挿入する前に特定のページにグループを作成します（`builder.InsertBreak(BreakType.PageBreak)`）。 |
| **Compatibility with older Word versions** | レガシー `.doc` 形式が必要な場合は `doc.Save("output.doc", SaveFormat.Doc)` として保存します。非表示シェイプは同様に動作します。 |

**Pro tip:** すべての子要素を挿入した *後* に必ず `group.Hidden = true` を設定してください。コンテンツを追加する前にフラグを変更すると、古いバージョンの Word で一部の要素が予期せず表示されることがあります。

## 結論

これで、Aspose.Words for .NET を使用して **空白のWord文書を作成**、**Word に画像を挿入**、**画像グループを追加**、そして **シェイプをWord文書で非表示** にする方法がわかりました。完全なサンプルは、文書の初期化から非表示画像グループを含むファイルの保存までのすべての手順を示しています。

次に、以下を検討できます：

- 同じグループにテキストボックスやチャートを追加する
- `DocumentBuilder.StartBookmark` / `EndBookmark` を使用して非表示セクションをマークする
- ユーザー入力やドキュメント変数に基づいてプログラムで可視性を切り替える

さまざまなシェイプ、サイズ、可視性ルールを試して、Automation シナリオに合わせてください。コーディングを楽しんで！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Aspose.Words for .NET を使用した Word 文書へのグループシェイプ作成](/words/english/net/working-with-shapes/add-group-shape/)
- [.NET で浮動画像付き Word 文書を作成](/words/english/net/add-content-using-documentbuilder/insert-floating-image/)
- [Aspose.Words を使用した Word 文書へのインライン画像挿入](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}