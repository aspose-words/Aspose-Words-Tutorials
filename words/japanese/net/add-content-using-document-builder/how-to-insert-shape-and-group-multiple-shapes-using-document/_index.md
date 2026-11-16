---
category: general
date: 2026-11-15
description: Aspose.Words DocumentBuilder を使用して、Word 文書に図形を挿入し、複数の図形をグループ化する方法を学びます。矩形の挿入例と複数図形の挿入例が含まれています。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert shape
- group multiple shapes
- insert multiple shapes
- insert rectangle shape
language: ja
lastmod: 2026-11-15
og_description: Aspose.Words を使用して Word ファイルに図形を挿入する方法。このガイドでは、複数の図形のグループ化、長方形の図形の挿入、そして複数の図形を効率的に追加する方法を取り上げます。
og_image_alt: Screenshot showing how to insert shape and group multiple shapes in
  a Word document using DocumentBuilder
og_title: DocumentBuilder を使用してシェイプを挿入し、複数のシェイプをグループ化する方法
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  headline: How to insert shape and group multiple shapes using DocumentBuilder in
    C#
  type: TechArticle
- description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  name: How to insert shape and group multiple shapes using DocumentBuilder in C#
  steps:
  - name: Why use a group?
    text: '* **Single‑point transformation** – rotate or resize the whole group with
      one call. * **Logical organization** – the Word document tree reflects the grouping,
      making later edits easier. * **Consistent layout** – moving the group keeps
      the relative positions of its children intact.'
  - name: Adding more shapes – extending **insert multiple shapes** inside the group
    text: 'You can keep calling `InsertShape` while the cursor remains inside the
      `GroupShape`. For example, to add a triangle:'
  - name: Expected output
    text: '* **First two shapes** – a rectangle and an ellipse placed independently
      on the page. * **Grouped block** – a rectangle, an ellipse, and a triangle that
      move together when you click any of them in Word.'
  type: HowTo
tags:
- Aspose.Words
- C#
- DocumentBuilder
- Shape handling
title: C# の DocumentBuilder を使用してシェイプを挿入し、複数のシェイプをグループ化する方法
url: /ja/net/add-content-using-document-builder/how-to-insert-shape-and-group-multiple-shapes-using-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DocumentBuilder を使用してシェイプを挿入し、複数のシェイプをグループ化する方法（C#）

Aspose.Words を使用して Word 文書に **シェイプを挿入する方法** を知りたい場合、このガイドでは正確な手順を示します。また、**複数のシェイプをグループ化**して単一のオブジェクトとして動作させる方法や、**矩形シェイプを挿入**する方法も学べます。

ドキュメント自動化では、チャートやロゴ、コールアウトなど複数のグラフィックを追加し、整理された状態に保つ必要があります。このチュートリアルの最後までに、**複数のシェイプを挿入**し、グループ内に配置して、クリーンで再利用可能なレイアウトを保存できるようになります。

## 前提条件

* .NET 6.0 以降がインストールされていること  
* Visual Studio 2022（または任意の C# IDE）  
* Aspose.Words for .NET のライセンスまたは無料評価キー  
* C# と Aspose.Words の `DocumentBuilder` クラスの基本的な知識  

他のサードパーティライブラリは **必要ありません**。必要なものはすべて Aspose.Words に含まれています。

## 手順 1: NuGet で Aspose.Words をインストール

Visual Studio でプロジェクトを開き、Package Manager Console で次のコマンドを実行します：

```powershell
Install-Package Aspose.Words
```

このパッケージには、本チュートリアル全体で使用する `DocumentBuilder`、`Shape`、`GroupShape` クラスが含まれています。

## 手順 2: DocumentBuilder インスタンスの作成 – **シェイプを挿入する方法** の基礎

最初の実行可能なコード行は `DocumentBuilder` の作成です。このオブジェクトにより、ドキュメントツリーへ直接アクセスでき、シェイプを希望の位置に正確に配置できます。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Initialise a new blank document
        Document doc = new Document();
        // Create a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // The rest of the tutorial inserts and groups shapes here …
    }
}
```

*重要な理由*: `DocumentBuilder` はカーソル（「挿入ポイント」）を保持します。以降のすべての `Insert...` 呼び出しはこのカーソルを使用するため、後で `GroupShape` にカーソルを移動させてすべてのシェイプを一緒に保ちます。

## 手順 3: **矩形シェイプを挿入** – 最初に追加するグラフィック

矩形はテーブル、画像、コールアウトなどの一般的なプレースホルダーです。`InsertShape` に `ShapeType.Rectangle` を指定し、幅と高さをポイント単位で設定します（1 pt ≈ 1/72 インチ）。

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

矩形は現在のカーソル位置に表示されます。必要に応じて、後で塗りつぶし、線のスタイル、テキストなどをカスタマイズできます。

## 手順 4: 別のシェイプを挿入 – 視覚的バリエーションとして楕円

複数のシェイプを追加することで **複数のシェイプを挿入** することを示します。楕円は文書の流れで矩形の後に配置されます。

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

この時点で文書には 2 つの独立したシェイプが含まれています。カーソルを移動したりテキストを追加しても、シェイプは挿入された位置に残ります。

## 手順 5: **複数のシェイプをグループ化** して単一ユニットとして動作させる

複数のグラフィックを一緒に移動、回転、または書式設定する必要がある場合、グループ化は不可欠です。以下のコードは `GroupShape` を作成し、ビルダーのカーソルをその内部に移動させ、同じシェイプを再度挿入します—このときシェイプはグループの子要素になります。

```csharp
// 1️⃣ Create a GroupShape and add it to the document tree
GroupShape group = new GroupShape(builder.Document);
builder.InsertNode(group);

// 2️⃣ Position the cursor inside the group so new inserts go into it
builder.MoveTo(group);

// 3️⃣ Insert a rectangle shape inside the group
builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Insert an ellipse shape inside the same group
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

### なぜグループを使用するのか？

* **単一ポイント変換** – 1 回の呼び出しでグループ全体を回転またはサイズ変更できます。  
* **論理的な整理** – Word のドキュメントツリーがグループ化を反映し、後の編集が容易になります。  
* **一貫したレイアウト** – グループを移動しても子要素間の相対位置が保たれます。

### さらにシェイプを追加 – グループ内で **複数のシェイプを挿入** を拡張

`GroupShape` の内部にカーソルがある間は `InsertShape` を呼び出し続けられます。例えば、三角形を追加するには次のようにします：

```csharp
builder.InsertShape(ShapeType.Triangle, 60, 60);
```

各呼び出しはグループコンテキストを尊重するため、三角形は自動的に同じグループセットの一部になります。

## 手順 6: ドキュメントを保存し、結果を確認

すべてのシェイプを配置したら、ドキュメントを `.docx` ファイルとして保存します。Microsoft Word（または互換ビューア）でファイルを開くと、2 つの個別シェイプの後に、同じ矩形、楕円、三角形を含むグループ化されたセットが表示されます。

```csharp
// Save the document
doc.Save("GroupedShapesDemo.docx");
```

### 期待される出力

* **最初の 2 つのシェイプ** – ページ上に個別に配置された矩形と楕円。  
* **グループ化ブロック** – Word でいずれかをクリックすると一緒に移動する矩形、楕円、三角形。

グループ内の任意のシェイプを選択してグループ化をテストできます。Word は全体のコレクションをハイライトし、**複数のシェイプをグループ化** 操作が成功したことを確認します。

## よくある落とし穴とプロのコツ

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| シェイプが意図したページ外に表示される | ビルダーのカーソルが `GroupShape` に移動されていなかったため | `GroupShape` に属するすべての `InsertShape` 呼び出しの **前に** `builder.MoveTo(group)` を必ず呼び出す。 |
| 保存後にグループが消える | グループがドキュメントのノードコレクションに追加されずに挿入されたため | `GroupShape` 作成直後に `builder.InsertNode(group)` を使用する。 |
| ドキュメント DPI の影響でサイズが予期せず変わる | Aspose.Words はポイント単位を使用するため、ピクセルで考えると寸法が合わないことがある | ピクセルをポイントに変換（`points = pixels * 72 / 96`）するか、直接ポイントで作業する。 |
| シェイプが意図せず重なる | 明示的な位置指定がなかったため、Word が順次配置する | 挿入後に `Shape.Left` と `Shape.Top` を設定して正確な配置を制御する。 |

**プロのコツ:** グループ化後、グループの `Shapes` コレクション（`group.Shapes`）を取得して、反復処理、名前変更、または一括書式設定を行えます。

## 手順 7: 例の拡張 – 次は何をするか？

**シェイプを挿入する方法**、**矩形シェイプを挿入**、そして **複数のシェイプをグループ化** が分かったので、以下を検討できます：

* **グループ化シェイプのアニメーション** – グループに回転や反転プロパティを設定する。  
* **スタイルの適用** – `Shape.FillColor`、`Shape.LineFormat`、`Shape.TextBox` を使用してラベルを追加する。  
* **PDF へのエクスポート** – `doc.Save("output.pdf")` を呼び出すと、同じグループ化レイアウトが正しくレンダリングされます。

これらすべての拡張は同じ `DocumentBuilder` ワークフローを再利用するため、コードがクリーンで保守しやすくなります。

## 結論

このチュートリアルでは、Aspose.Words を使用して Word 文書に **シェイプを挿入する方法**、**矩形シェイプを挿入**、そして **複数のシェイプをグループ化** して単一オブジェクトとして動作させる方法を示しました。ステップバイステップのコードに従うことで、確実に **複数のシェイプを挿入**し、グループ化して、プログラムでプロフェッショナルな文書を作成できます。

さまざまなシェイプタイプ、色、グループ変換を自由に試してみてください。準備ができたら、このパターンを大規模なレポートやテンプレートソリューションに統合し、複雑な文書レイアウトを自動化しましょう。コーディングを楽しんでください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Aspose.Words for .NET を使用した Word 文書へのシェイプ挿入](/words/english/net/working-with-shapes/insert-shape/)
- [Aspose.Words を使用して Word 文書のグループシェイプ内に楕円と矩形シェイプを作成・挿入する方法](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Aspose.Words を使用した Word 文書でのシェイプのグループ化方法](/words/english/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}