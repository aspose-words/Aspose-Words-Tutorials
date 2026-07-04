---
category: general
date: 2026-06-20
description: Aspose.Words for .NET を使用して、図形に素早く影を追加し、影の透明度の変更、図形への影の追加、ぼかし影の適用方法を学びましょう。
draft: false
keywords:
- add shadow to shape
- how to change shadow transparency
- how to add shape shadow
- how to apply blur shadow
language: ja
og_description: Word ファイルの図形に影を付け、影の透明度の変更方法を確認し、図形の影を追加し、明確なコード例でぼかし影を適用します。
og_title: 形状に影を追加 – ステップバイステップ C# チュートリアル
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Add shadow to shape quickly and learn how to change shadow transparency,
    add shape shadow, and apply blur shadow using Aspose.Words for .NET.
  headline: Add Shadow to Shape in Word Documents – Complete C# Guide
  type: TechArticle
- description: Add shadow to shape quickly and learn how to change shadow transparency,
    add shape shadow, and apply blur shadow using Aspose.Words for .NET.
  name: Add Shadow to Shape in Word Documents – Complete C# Guide
  steps:
  - name: What if the shape has no existing shadow object?
    text: Aspose.Words automatically creates a `Shadow` object when you first access
      `targetShape.Shadow`. No extra initialization is required.
  - name: Does this work with other shape types, like circles or pictures?
    text: Absolutely. The shadow API is shape‑agnostic. Just retrieve the appropriate
      `Shape` node, and the same properties apply.
  - name: How to make the shadow invisible again?
    text: Set `targetShape.Shadow.Visible = false;` or simply omit the shadow configuration.
  - name: Compatibility with older .NET versions?
    text: The code uses only features available in Aspose.Words 23.x and .NET Standard
      2.0+, so it runs on .NET Framework 4.6.1 and newer.
  type: HowTo
tags:
- Aspose.Words
- C#
- Document Automation
- Shapes
title: Word文書の図形に影を追加する – 完全なC#ガイド
url: /ja/net/programming-with-shapes/add-shadow-to-shape-in-word-documents-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word ドキュメントのシェイプに影を追加 – 完全な C# ガイド

Word ファイルで UI をいじらずに **シェイプに影を追加** したいと思ったことはありませんか？ あなたは一人ではありません。多くの開発者がプログラムでドキュメントの見た目を向上させる必要があり、朗報です。Aspose.Words を使えばそれはとても簡単です。

このチュートリアルでは、**シェイプに影を追加** する正確な手順を解説し、**影の透明度を変更** する方法、さまざまなシナリオで **シェイプに影を追加** する方法、さらに **ぼかし影を適用** してプロフェッショナルな奥行き効果を出す方法を紹介します。最後まで読めば、任意の .NET プロジェクトに貼り付けられる再利用可能なコードスニペットが手に入ります。

## 学べること

- DOCX を読み込み、シェイプを取得し、影のプロパティを設定する方法
- `Transparency` で影の不透明度を調整する方法
- ぼかしとオフセットを適用してリアルなドロップシャドウを作成する方法
- 変更後のドキュメントを保存し、結果を確認する方法
- 複数シェイプ、異なるシェイプタイプ、エッジケースの取り扱いに関するヒント

> **前提条件:** .NET 6 以降、Aspose.Words for .NET（NuGet パッケージ `Aspose.Words`）、および C# の基本的な知識。UI ツールは不要です。

![add shadow to shape example](image.png){ alt="シェイプに影を追加した例" }

## 手順 1: プロジェクトを設定しドキュメントを読み込む

**シェイプに影を追加** する前に、操作対象となる Document オブジェクトが必要です。このステップはシンプルですが重要です。ファイルを読み込まなければ、何も変更できません。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load an existing DOCX that already contains a shape (e.g., a rectangle)
Document document = new Document(@"C:\Docs\input.docx");
```

*なぜ重要か:*  
`Document` は Aspose.Words のすべての操作のエントリーポイントです。早い段階でファイルを読み込むことで、以降のシェイプ操作が正しいノードツリー上で行われます。

## 手順 2: 対象シェイプを取得する

ドキュメントがメモリ上にロードされたら、影を付けたいシェイプを探します。シェイプが複数ある場合はインデックスを調整するか、より高度なセレクタを使用してください。

```csharp
// Grab the first shape in the document – change the index if needed
Shape targetShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
```

> **ヒント:** `document.GetChild(NodeType.Shape, index, true)` を使うと再帰的に検索できます。名前で特定のシェイプを取得したい場合は `targetShape.Name` を確認してください。

## 手順 3: 影を有効化し基本色を設定する

影は可視化され、色が設定されて初めて表示されます。薄いダークグレーを選べば、明るい背景でも違和感がありません。

```csharp
// Make sure the shadow is turned on
targetShape.Shadow.Visible = true;

// Choose a neutral color for the shadow
targetShape.Shadow.Color = Color.DarkGray;
```

*解説:*  
`Visible` を `true` に設定すると効果が有効になり、`Color.DarkGray` がほとんどのドキュメントテーマと衝突しない中立的なトーンを提供します。

## 手順 4: 影の透明度を変更する方法

透明度は影を自然に見せる鍵です。`0` が完全に不透明、`1` が完全に透明です。以下は **影の透明度を 30 % に変更** するコードです。

```csharp
// 30 % transparent (0.3 means 30 % see‑through)
targetShape.Shadow.Transparency = 0.3;
```

*なぜ 0.3 か？*  
30 % の透明度は実際の照明を模倣し、シェイプのエッジを圧倒しません。`0.5` にすると柔らかい印象に、`0.1` にすると影が強調されます。

## 手順 5: 奥行きを出すぼかし影の適用方法

エッジがはっきりした影は平坦に見えます。ぼかしを加えることで奥行き感が生まれます。ここではコードで **ぼかし影を適用** する方法を示します。

```csharp
// Define the blur radius (in points). Larger values = softer shadow.
targetShape.Shadow.BlurRadius = 5;   // 5 pt blur

// Offset determines where the shadow falls relative to the shape.
targetShape.Shadow.OffsetX = 3;      // 3 pt to the right
targetShape.Shadow.OffsetY = 3;      // 3 pt downwards
```

*何が起きているか:*  
`BlurRadius` がエッジを柔らかくし、`OffsetX/Y` が左上から光が当たっているかのように影の位置を調整します。デザインに合わせて数値を変更してください。

## 手順 6: 複数シェイプに影を追加する方法（オプション）

ドキュメントにシェイプが多数ある場合、**シェイプに影を追加** したいことが多いでしょう。簡単なループで実現できます。

```csharp
// Iterate over every shape in the document
foreach (Shape shape in document.GetChildNodes(NodeType.Shape, true))
{
    shape.Shadow.Visible = true;
    shape.Shadow.Color = Color.DarkGray;
    shape.Shadow.Transparency = 0.3;
    shape.Shadow.BlurRadius = 5;
    shape.Shadow.OffsetX = 3;
    shape.Shadow.OffsetY = 3;
}
```

*プロのコツ:*  
ループ内で `shape.ShapeType == ShapeType.Rectangle` をチェックすれば、矩形だけに影を付けることができます。

## 手順 7: 変更後のドキュメントを保存する

すべての処理が完了したら、変更を永続化します。元のファイルを上書きするか、別の場所に保存できます。

```csharp
// Save to a new file to keep the original untouched
document.Save(@"C:\Docs\output.docx");
```

`output.docx` を Word で開くと、対象にした矩形（または任意のシェイプ）に薄い半透明のぼかし影が付いていることが確認できます。

## よくある質問とエッジケース

### シェイプに既存の Shadow オブジェクトがない場合は？
`targetShape.Shadow` に初めてアクセスした時点で Aspose.Words が自動的に `Shadow` オブジェクトを作成します。追加の初期化は不要です。

### 円や画像など、他のシェイプタイプでも動作しますか？
もちろんです。Shadow API はシェイプに依存しません。対象の `Shape` ノードを取得すれば、同じプロパティが適用できます。

### 影を再び非表示にするには？
`targetShape.Shadow.Visible = false;` と設定するか、影の設定自体を省略してください。

### 古い .NET バージョンでも動作しますか？
このコードは Aspose.Words 23.x と .NET Standard 2.0 以上の機能だけを使用しています。そのため .NET Framework 4.6.1 以降でも動作します。

## 完全動作サンプル

以下はすべてをまとめた、すぐに実行できるプログラムです。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load the document that contains the shape
        Document doc = new Document(@"C:\Docs\input.docx");

        // Retrieve the first shape (e.g., a rectangle) from the document
        Shape rect = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        // Enable shadow and set its basic properties
        rect.Shadow.Visible = true;
        rect.Shadow.Color = Color.DarkGray;

        // How to change shadow transparency – 30 % transparent
        rect.Shadow.Transparency = 0.3;

        // How to apply blur shadow – add depth with blur and offset
        rect.Shadow.BlurRadius = 5;   // 5 pt blur radius
        rect.Shadow.OffsetX = 3;      // horizontal offset
        rect.Shadow.OffsetY = 3;      // vertical offset

        // Save the modified document
        doc.Save(@"C:\Docs\output.docx");
    }
}
```

**期待される結果:** `output.docx` を開くと、元の矩形がダークグレーで 30 % 透明、ぼかしがかかった影が右下に少しオフセットされた状態で表示されます。

## 結論

プログラムで **シェイプに影を追加** するために必要な手順をすべて網羅しました。ファイルの読み込みから透明度・ぼかしの調整まで、**影の透明度を変更**、**シェイプに影を追加**、**ぼかし影を適用** する方法を習得しました。

次のステップに進む準備はできましたか？ 以下を試してみてください。

- 異なる影の色 (`Color.Black`, `Color.FromArgb(128, 0, 0, 0)`) でより濃い効果を出す
- シェイプサイズに応じた動的オフセットで比例感を保つ
- 影とグラデーションや反射を組み合わせて高度なスタイリングを実現する

質問や問題があればコメントで教えてください。楽しいコーディングを！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれており、API の追加機能をマスターしたり、独自の実装アプローチを探求したりするのに役立ちます。

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Add Group Shape](/words/english/net/programming-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}