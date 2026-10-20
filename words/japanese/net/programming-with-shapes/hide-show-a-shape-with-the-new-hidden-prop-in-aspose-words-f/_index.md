---
category: general
date: 2026-10-20
description: Aspose.Words for C# を使用して、新しい `Hidden` プロパティでシェイプを非表示/表示にします。シェイプの表示/非表示の切り替え方法、エッジケースの処理、結果の保存方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Hide/Show a Shape with the new `Hidden` prop
- Aspose.Words hide shape
- C# shape hidden property
- Word document shape visibility
- programmatically hide shape
language: ja
lastmod: 2026-10-20
og_description: Aspose.Words for C# の新しい `Hidden` プロパティを使用してシェイプを非表示/表示にします。シェイプの可視性切り替えをマスターし、一般的な落とし穴を回避しましょう。
og_image_alt: Screenshot of a Word document where a shape is hidden using the Hidden
  property
og_title: Aspose.Words (C#) の新しい `Hidden` プロパティでシェイプを非表示/表示する
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Hide/Show a Shape with the new `Hidden` prop using Aspose.Words for
    C#. Learn how to toggle shape visibility, handle edge cases, and save the result.
  headline: Hide/Show a Shape with the new `Hidden` prop in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Aspose.Words for C# の新しい `Hidden` プロパティでシェイプを非表示/表示する
url: /ja/net/programming-with-shapes/hide-show-a-shape-with-the-new-hidden-prop-in-aspose-words-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for C# の新しい `Hidden` プロパティでシェイプを非表示/表示する方法

Word 文書で新しい `Hidden` プロパティを使用してシェイプを **非表示/表示** する必要がある場合、このガイドでは Aspose.Words for .NET を使った具体的な手順を示します。レポートの生成、テンプレートの作成、インポートされた文書のクリーンアップなど、シェイプの可視性をプログラムで制御することで手作業の編集を省くことができます。

このチュートリアルでは、文書の読み込み、シェイプの取得、`Hidden` プロパティの切り替え、変更後のファイル保存の方法を学びます。また、複数シェイプの処理やインラインとフローティングのグラフィックの違いといった一般的なバリエーションもカバーしています。

## 前提条件

* .NET 6.0（またはそれ以降）がインストールされていること – Aspose.Words は .NET Standard 2.0 と .NET Core をサポートしています。
* **Aspose.Words for .NET** のライセンス版（無料トライアルでも試すことができます）。
* Visual Studio 2022 や Visual Studio Code などの IDE。
* 少なくとも 1 つのシェイプ（画像、SmartArt、描画キャンバスなど）を含む Word 文書（`input.docx`）。

## 手順 1: Word 文書を読み込む

最初の操作は、ディスク上の .docx ファイルを表す `Document` オブジェクトを作成することです。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*このステップが重要な理由*: `Document` はすべての Aspose.Words 操作のエントリーポイントです。ファイルをメモリに読み込むことで、シェイプを含むノードツリー全体にフルアクセスできます。

## 手順 2: 対象シェイプを取得する

可視性を切り替えるには、シェイプノードへの参照を取得する必要があります。以下の例は文書内の最初のシェイプを取得しますが、名前、タイプ、インデックスでシェイプを検索するようロジックを変更できます。

```csharp
// Get the first Shape node in the document tree
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

if (shape == null)
{
    throw new InvalidOperationException("No shape was found in the document.");
}
```

*このステップが重要な理由*: `true` を指定した `GetChild` は深い検索を行い、テーブルやヘッダー内に入れ子になっているシェイプでも見つけられます。`null` チェックを行うことで、シェイプがまったく存在しない文書での `NullReferenceException` を防げます。

## 手順 3: `Hidden` プロパティでシェイプを非表示にする

Aspose.Words はシェイプが描画または印刷されるかどうかを制御する `Hidden` プロパティを導入しました。`true` に設定するとシェイプが非表示になり、`false` に設定すると再び表示されます。

```csharp
// Hide the shape so it will not appear in the rendered document
shape.Hidden = true;
```

以前非表示にしたシェイプを **表示** したい場合は、単に `false` を代入してください。

```csharp
// Show the shape again
shape.Hidden = false;
```

*このステップが重要な理由*: `Hidden` プロパティはフローティングシェイプとインラインシェイプの両方で機能し、Word のネイティブな「Hidden」書式とも統合されています。シェイプを削除するよりも、ノードが文書ツリーに残るためレイアウトや参照が保持され、信頼性が高まります。

## 手順 4: 変更した文書を保存する

可視性を調整したら、変更を新しいファイル（または必要に応じて元のファイルを上書き）に書き戻します。

```csharp
// Save the document with the updated shape visibility
doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");
```

*このステップが重要な理由*: `Save` はメモリ上のノードツリーを .docx パッケージとしてシリアライズし、Word が開ける形にします。`Hidden` フラグは永続化されるため、Microsoft Word でファイルを開くと `Hidden` 設定に従ってシェイプが表示または非表示になります。

## 完全な実行可能サンプル

すべての手順を組み合わせると、コピーしてコンパイルし実行できる自己完結型プログラムが完成します。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShowShapeExample
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first shape in the document
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found. Exiting.");
            return;
        }

        // 3. Toggle the Hidden property
        // Hide the shape
        shape.Hidden = true;
        // To show the shape again, uncomment the following line:
        // shape.Hidden = false;

        // 4. Save the modified document
        doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");

        Console.WriteLine("Document saved. Shape hidden = " + shape.Hidden);
    }
}
```

**期待される出力**（プログラム実行時）:

```
Document saved. Shape hidden = True
```

`ShapeHidden.docx` を Microsoft Word で開くと、対象シェイプが非表示になった文書が表示されます。保存前に `shape.Hidden = false;` と設定すれば、シェイプが再び現れます。

## 複数シェイプの処理

上記の例は単一シェイプに対して機能しますが、実務の文書では多数のグラフィックが含まれることが多いです。条件に合致するすべてのシェイプを非表示または表示するには、ループを使用します（例: 特定の名前やタイプ）。

```csharp
// Hide every picture shape in the document
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Image)
    {
        s.Hidden = true; // hide picture
    }
}
doc.Save("YOUR_DIRECTORY/AllPicturesHidden.docx");
```

*Tip*: `ShapeType` でフィルタリングすれば、テキストボックスや SmartArt など装飾要素を誤って非表示にすることを防げます。

## エッジケースとベストプラクティス

| 状況 | 推奨される対処 |
|-----------|----------------------|
| **ヘッダー/フッター内のシェイプ** | まずヘッダー/フッター ノードを取得し、そのサブドキュメントで `GetChild(NodeType.Shape, …)` を呼び出します。 |
| **文書にシェイプが存在しない** | `GetChild` 後に必ず `null` をチェックするか、`doc.GetChildNodes(NodeType.Shape, true).Count` でシェイプ数を確認します。 |
| **異なる Word バージョン間で hidden フラグを保持したい** | `Hidden` プロパティはシェイプの XML に `<w:hidden/>` として保存され、Word 2007 以降でサポートされています。 |
| **大容量文書でのパフォーマンス** | `doc.GetChildNodes(NodeType.Shape, true)` を一度だけ呼び出し、コレクションを再利用して `GetChild` を繰り返し呼ぶのを避けます。 |

## プロのコツ: `Hidden` と `WrapType` を組み合わせる

シェイプを非表示にしても、ラップ設定を変更しない限り Word はその占有領域を確保します。`WrapType = WrapType.None` と設定すれば、プレースホルダー領域が削除されます。

```csharp
shape.Hidden = true;
shape.WrapType = WrapType.None;
```

これにより、シェイプが存在しなかったかのようにレイアウトが縮小し、クリーンなレポート作成に役立ちます。

## 結論

これで Aspose.Words for C# を使用して **新しい `Hidden` プロパティでシェイプを非表示/表示** する方法が分かりました。文書の読み込み、シェイプの取得、`Hidden` プロパティの切り替え、変更の永続化という一連の手順を網羅しています。null チェック、複数シェイプの処理、ラップ設定の調整といったベストプラクティスに従うことで、あらゆる Word 自動化シナリオでシェイプの可視性を確実に制御できます。

次に進むには以下のステップを検討してください：

* カスタムメタデータに基づいて **複数シェイプを非表示/表示**（「プログラムでシェイプを非表示にする」テクニックを使用）。
* Aspose.Words フィールドを使って **`Hidden` と条件付きコンテンツを組み合わせ**、動的レポートを生成。
* **他のノードプロパティ** を探求（例: チャートオブジェクトの `Visible`、段落レベル制御の `IsDeleted`）。

コーディングを楽しみながら、Aspose.Words が提供する細かなシェイプ可視性制御を活用してください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示したテクニックを基にした密接に関連するトピックを取り上げています。各リソースには、完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得したり、独自プロジェクトで代替実装アプローチを検討したりするのに役立ちます。

- [C# を使用して Word でシェイプを非表示にする方法 – ステップバイステップガイド](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-using-c-step-by-step-guide/)
- [C# で Word のシェイプを非表示にする方法 – ステップバイステップガイド](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-with-c-step-by-step-guide/)
- [非表示の楕円シェイプ付き空白 Word 文書の作成 – 完全 C# ガイド](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}