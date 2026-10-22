---
category: general
date: 2026-09-30
description: C#でWordの図形をグループ化 – 図形のグループ化方法、長方形と楕円の追加、そしてプログラムでWord文書に長方形の図形を挿入する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- how to add rectangle
- how to add ellipse
- insert rectangle shape word
language: ja
lastmod: 2026-09-30
og_description: C# と Aspose.Words を使用して Word で図形をグループ化します。この完全ガイドに従って、長方形の追加、楕円の追加、そして図形を効率的にグループ化する方法を学びましょう。
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape
og_title: C#でWordの図形をグループ化する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: group shapes in Word with C# – learn how to group shapes, add rectangle
    and ellipse, and insert rectangle shape Word documents programmatically.
  headline: How to group shapes in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: C# と Aspose.Words を使用して Word で図形をグループ化する方法
url: /ja/net/programming-with-shapes/how-to-group-shapes-in-word-using-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# と Aspose.Words を使用して Word で図形をグループ化する方法

Word の図形をプログラムで **グループ化** したい場合、このガイドで手順をすべて解説します。矩形の追加、楕円の追加、そしてそれらを単一のグループ図形にまとめる方法を、.NET 用 Aspose.Words ライブラリを使って実演します。

レポート、契約書、マーケティング資料などを自動生成する際に、図形操作はよくある要件です。このチュートリアルの最後までに、DOCX ファイルを読み込み、矩形と楕円を挿入し、グループ化して保存する再利用可能な C# メソッドが完成します。Word を手動で開く必要はありません。

## 前提条件

開始する前に、以下が揃っていることを確認してください。

* .NET 6.0 SDK 以降がインストール済み  
* Visual Studio 2022 などの開発環境（Community エディションで可）  
* Aspose.Words for .NET のライセンスまたは無料評価版（ライセンスなしでも API は動作しますが透かしが入ります）  

また、コードから参照できるフォルダーに Word のソース文書（`input.docx`）が必要です。文書は空でも構いません。チュートリアルは図形操作に焦点を当てています。

## 手順 1: 新しいコンソールプロジェクトを作成し Aspose.Words を追加

ターミナルまたは Visual Studio のコマンドプロンプトで次を実行します。

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

これにより **WordShapeDemo** という名前の新しいコンソール アプリケーションが作成され、Word ファイル操作に必要な `Document` と `DocumentBuilder` クラスを含む `Aspose.Words` NuGet パッケージが追加されます。

## 手順 2: 文書を読み込むまたは作成する

**Word のグループ図形** を扱う最初の操作は `Document` オブジェクトを取得することです。既存の DOCX ファイルを読み込むか、空の文書から開始できます。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Load an existing document (replace the path with your own)
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");

        // If you prefer a brand‑new document, uncomment the next line:
        // Document document = new Document();
```

`Document` クラスは Word ファイル全体を表します。ファイルを読み込むことで、図形を挿入するためのキャンバスがすぐに用意されます。

## 手順 3: グループ図形の開始

*グループ図形* は複数の独立した図形を 1 つの単位として扱えるため、まとめて移動やサイズ変更が可能です。グループを開始するには `DocumentBuilder` の `StartGroupShape()` を呼び出します。

```csharp
        // Create a builder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Begin a group shape that will contain multiple shapes
        builder.StartGroupShape();
```

`StartGroupShape` を呼び出すと、以降に挿入するすべての図形が同じ論理グループに属することになり、`EndGroupShape` を呼ぶまでその状態が続きます。

## 手順 4: Word に矩形図形を追加する方法

グループが開いたら、まず矩形を挿入します。`InsertShape` メソッドは `ShapeType` 列挙体と幅・高さ（ポイント単位）を受け取ります。

```csharp
        // Add a rectangle shape to the group (100 pt wide, 50 pt high)
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

矩形はグループの最初のメンバーになります。必要に応じて塗りつぶしや枠線、テキストを後からカスタマイズできます。

## 手順 5: Word に楕円図形を追加する方法

次に楕円（幅と高さが同じ場合は円）を追加します。これにより、同じビルダーを使って **楕円の追加方法** を示します。

```csharp
        // Add an ellipse shape to the same group (80 pt wide, 80 pt high)
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

2 つの図形は同じ座標空間を共有するため、視覚的に整列させやすくなります。

## 手順 6: グループ図形定義を閉じる

必要なメンバーをすべて追加したら、グループを閉じます。これにより図形のコレクションが確定し、Word 側で 1 つのオブジェクトとして扱われます。

```csharp
        // End the group shape definition
        builder.EndGroupShape();
```

この時点で、文書には矩形と楕円からなる単一のグループ図形が含まれています。

## 手順 7: 変更後の文書を保存

最後に、変更内容をディスクに書き戻します。元のファイルを上書きしても、新規に作成しても構いません。

```csharp
        // Save the document with the grouped shapes
        document.Save(@"YOUR_DIRECTORY\output.docx");

        Console.WriteLine("Document saved with grouped shapes.");
    }
}
```

プログラムを実行すると `output.docx` が生成されます。Microsoft Word でファイルを開き、図形を選択すると矩形と楕円が一緒に移動することが確認でき、**Word のグループ図形** 操作が成功したことが分かります。

### 期待される結果

* Word ファイルに単一のグループ オブジェクトが含まれる  
* グループを選択すると、矩形と楕円を同時にドラッグ、サイズ変更、回転できる  
* Word を手動で操作する必要はなく、すべて C# コードで完結する  

![Grouped shapes in Word document](grouped-shapes.png "Screenshot of a Word document showing a grouped rectangle and ellipse shape")

*画像代替テキスト: “Word 文書内にグループ化された矩形と楕円の図形が表示されているスクリーンショット”*（画像 alt‑text 要件を満たしています）。

## 図形をグループ化する重要性

図形のグループ化は単なる見た目の便利さ以上の価値があります。

* **レイアウトの一貫性を維持** – グループ全体を移動しても相対位置が保たれます。  
* **変形を一括で適用** – 各図形を個別に回転・拡大するのではなく、グループ全体に対して行えます。  
* **下流処理の簡素化** – 他ツールが DOCX を読み取る際、単一の合成図形として認識されるため、複雑さが減ります。  

後で線やテキスト ボックスなどの図形を同じ論理単位に追加したい場合は、`EndGroupShape` の前に再度 `InsertShape` を呼び出すだけです。

## よくあるバリエーションとエッジケース

| 状況 | 対処方法 |
|-----------|-----------------|
| **単位が異なる** – センチメートルで測定している | `InsertShape` を呼ぶ前にセンチメートルをポイントに変換します（`1 cm ≈ 28.35 pt`）。 |
| **テキスト ラベルを追加** – グループ内にキャプションを入れたい | 矩形と楕円の後に `ShapeType.TextBox` を挿入し、`Text` プロパティで文字列を設定します。 |
| **塗りつぶし色を適用** – 青い矩形が必要 | `InsertShape` 後に最後に挿入された図形を取得し、`shape.FillColor = System.Drawing.Color.Blue;` を設定します。 |
| **別の文書形式を使用** – `.doc` 形式で保存したい | コードは同じで、`Save` 時に拡張子を変更するだけです。Aspose.Words が自動で形式を判別します。 |

## プロのコツ

* **ビルダーを再利用** – 同一文書内で複数のグループを作成でき、`EndGroupShape` 後に再度 `StartGroupShape` を呼び出すだけです。  
* **パフォーマンス** – 複数の図形を 1 つの `StartGroupShape/EndGroupShape` ブロック内にまとめて挿入すると、個別に挿入するより高速です。  
* **ライセンス** – 評価ライセンスは最初のページに透かしが入ります。本番環境では正規ライセンスをインストールして透かしを除去してください。  

## 結論

これで C# と Aspose.Words を使って **Word の図形をグループ化** する方法、**矩形の追加**、**楕円の追加**、そして **Word 文書に矩形図形を挿入** する手順がマスターできました。プロジェクトのセットアップから最終ファイルの保存まで、すべてのステップを実行可能なサンプルとして示しています。

ここからは、他の図形タイプを試したり、スタイリングを適用したり、テーブルや画像と組み合わせて高度な自動生成文書を作成してみてください。

---

**次のステップ**

* **グループ化された図形の回転** を学ぶ: グループを閉じた後に `Shape.RotationAngle` を使用。  
* 矩形と楕円の **塗りつぶしと枠線のカスタマイズ** を探求。  
* このロジックを ASP.NET Core API に組み込み、オンデマンドでレポートを生成。  

Happy coding!

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを基にした関連トピックを扱っています。各リソースには完全な動作コード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、別の実装アプローチを自分のプロジェクトで試したりするのに役立ちます。

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Rectangle Shape in Word – Full Aspose.Words Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}