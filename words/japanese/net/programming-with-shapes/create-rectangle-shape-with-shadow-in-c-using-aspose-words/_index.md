---
category: general
date: 2026-03-22
description: C#で矩形シェイプを作成し、Aspose.Wordsを使用してシェイプに影を追加します。影の付け方、矩形の作り方、影のプロパティ設定方法を学びましょう。
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- how to add shadow
- how to create rectangle
- how to set shadow
language: ja
og_description: C#で矩形シェイプを作成し、Aspose.Wordsを使用してシェイプに影を追加します。影の追加方法、矩形の作成方法、影の設定方法をステップバイステップで解説します。
og_title: C#で影付きの長方形シェイプを作成する – 完全ガイド
tags:
- Aspose.Words
- C#
- Document Automation
title: Aspose.Words を使用して C# で影付きの長方形シェイプを作成する
url: /ja/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# と Aspose.Words で影付きの長方形シェイプを作成する

Word 文書に **長方形シェイプ** を作成したいが、さりげないドロップシャドウの付け方が分からない…という経験はありませんか？同じ壁にぶつかる開発者は多いです。このガイドでは Aspose.Words を使って **シェイプに影を追加する** 方法をステップバイステップで解説し、途中で “**影の付け方**”、 “**長方形の作り方**”、 “**影の設定方法**” についても答えていきます。

まずはクリーンな `Document` を用意し、長方形を描画し、影を有効化して、ぼかし、距離、角度、色を調整し、最後にファイルを保存します。最後まで実行すれば、ページ上に浮かんでいるように見えるグレーの長方形が入った `.docx` が手に入ります。難しいことはなく、どの .NET プロジェクトにもコピペできるシンプルなコードです。

## 前提条件

始める前に以下を用意してください。

* **Aspose.Words for .NET**（2026年3月時点の最新バージョン）。`Install-Package Aspose.Words` で NuGet から取得できます。
* .NET 開発環境 – Visual Studio、Rider、あるいは C# 拡張機能が入った VS Code でも OK。
* 基本的な C# の知識 – コンソールアプリや WinForms アプリを作れる程度で構いません。

以上です。余計なライブラリや隠し手順は不要です。準備はできましたか？さあ、始めましょう。

## 手順 1: 空のドキュメントを初期化する

**長方形シェイプを作成**するには、まず Word ファイルを表す `Document` オブジェクトというコンテナが必要です。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new empty document
Document document = new Document();
```

`Document` クラスは Aspose.Words のすべての操作のエントリーポイントです。空白のキャンバスと考えてください。これがなければシェイプやテーブル、テキストを追加できません。

## 手順 2: 影を付ける長方形を作成する

ここで **長方形の作り方** を示します。`Shape` を `Rectangle` タイプでインスタンス化し、サイズをポイント単位で設定します（1 ポイント ≈ 1/72 インチ）。

```csharp
// Step 2: Create a rectangular shape that will hold the shadow
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points
rectangleShape.Height = 100; // height in points
```

なぜ 200 × 100 ポイントにしたかというと、デモ用としては十分に大きく、影がはっきり見えるサイズだからです。ページを圧迫しすぎない程度です。レイアウトに合わせて数値は自由に調整してください。

## 手順 3: 影効果を有効化し外観を設定する

本チュートリアルの核心です。**影の付け方** と **影の設定方法** を解説します。Aspose.Words はすべてのシェイプに `Shadow` オブジェクトを提供しており、効果のオンオフや各種パラメータを調整できます。

```csharp
// Step 3: Enable the shadow effect and configure its appearance
rectangleShape.Shadow.Enabled    = true;                     // turn the shadow on
rectangleShape.Shadow.BlurRadius = 5;                       // blur radius in pixels
rectangleShape.Shadow.Distance   = 8;                       // distance from the shape in pixels
rectangleShape.Shadow.Angle      = 45;                      // direction of the light source (degrees)
rectangleShape.Shadow.Color      = System.Drawing.Color.Gray; // shadow color
```

* **BlurRadius** はエッジを柔らかくします。値が大きいほど影が拡散したように見えます。  
* **Distance** は影を長方形から遠ざけます。  
* **Angle** は光源の方向を決めます。45° にすると対角線上の自然な見た目になります。  
* **Color** は任意の `System.Drawing.Color` を指定できます。デフォルトはグレーですが、`Color.Black` で濃くしたり、`Color.LightGray` で控えめにしたりできます。

プロのコツ: `Enabled = false` にすると他のすべての影設定は無視されるので、必ずこのフラグが true になっているか確認しましょう。

## 手順 4: シェイプをドキュメント本文に挿入する

長方形と影の設定が完了したら、ドキュメントに配置します。最も簡単なのは、最初のセクションの最初の段落に追加することです。

```csharp
// Step 4: Insert the shape into the first paragraph of the document body
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

既にテキストがある場合は、特定の `Paragraph` や `Table` のセルを探してそこにシェイプを挿入することも可能です。`AppendChild` メソッドは汎用的で、任意の `Node` 型に対して使用できます。

## 手順 5: ドキュメントを保存し結果を確認する

最後にファイルを書き出します。パスは好きな場所に変更してください。フォルダーが存在しないと例外がスローされます。

```csharp
// Step 5: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowedRectangle.docx");
```

生成された `ShadowedRectangle.docx` を Microsoft Word（または LibreOffice）で開くと、右下方向に斜めのクリアな影が付いたグレーの長方形が表示されます。影が薄すぎると感じたら、`BlurRadius` または `Distance` を増やして再実行してください。試行錯誤も楽しみの一部です。

![Create rectangle shape with shadow example](rectangle-shadow.png){alt="影付き長方形シェイプの例"}

### 期待される出力

* 1 ページの Word 文書  
* ページ左上に配置された 200 × 100 ポイントのグレー長方形  
* 45° 角度で 8 ピクセルオフセット、5 ピクセルぼかしの控えめなグレー影

## シェイプへの影の付け方 – 詳細解説

「**影をアニメーションさせたり、ユーザー入力に応じて変化させられるか**」と疑問に思うかもしれません。Aspose.Words 自体はアニメーションをサポートしていませんが、保存前にプログラムで影のプロパティを変更すれば、見た目が異なる複数バージョンのドキュメントを生成できます。例えば、色のコレクションをループで回す例です。

```csharp
Color[] shadowColors = { Color.Gray, Color.Black, Color.DarkSlateGray };
foreach (var col in shadowColors)
{
    rectangleShape.Shadow.Color = col;
    document.Save($@"C:\Temp\Shadow_{col.Name}.docx");
}
```

この小さなスニペットは **影の設定方法** を動的に行う例で、テーマ別レポートの生成に便利です。

## 長方形の作り方 – 代替シェイプ

丸みを帯びた長方形が必要な場合は、`ShapeType` を次のように切り替えます。

```csharp
Shape rounded = new Shape(document, ShapeType.RoundRectangle);
rounded.Width  = 200;
rounded.Height = 100;
rounded.Shadow.Enabled = true; // shadow works the same way
```

または、正方形を作りたいときは `Width` と `Height` を同じに設定します。影のプロパティは同じなので、**影の付け方** はどのシェイプでも同様に適用できます。

## よくある落とし穴とトラブルシューティング

| 症状 | 考えられる原因 | 対策 |
|------|----------------|------|
| 影が表示されない | `Shadow.Enabled` が `false` のまま | `rectangleShape.Shadow.Enabled = true;` に設定 |
| 影が鋭すぎる | `BlurRadius` が 0 に設定されている | `BlurRadius` を少なくとも 3 以上に増やす |
| 保存時に `FileNotFoundException` が発生 | 保存先フォルダーが存在しない | フォルダーを事前に作成するか、有効なパスを使用 |
| シェイプが見えない | 幅・高さが 0 に設定されている | 両方のサイズが 0 より大きいことを確認 |

これらのポイントに注意すれば、 “なぜシェイプが表示されないのか” といった典型的な問題を回避できます。

## まとめ – 実現したこと

* Aspose.Words を使って新規 Word 文書に **長方形シェイプを作成**  
* `Shadow.Enabled` フラグをオンにし、ぼかし・距離・角度・色を調整して **シェイプに影を追加**  
* **影の付け方**、**長方形の作り方**、**影の設定方法** をシンプルで再利用可能なコードスニペットで実演  
* 任意の C# プロジェクトに貼り付けてすぐに動作する完全なサンプルを提供  

## 次のステップは？

基本をマスターしたら、以下も検討してみてください。

* **画像への影の付け方** – 同じ `Shadow` API が `ShapeType.Image` にも適用可能です。  
* **複数シェイプの組み合わせ** – Word 内でフローチャートやインフォグラフィックを作成。  
* **PDF へのエクスポート** – 影を付けた後に `document.Save("output.pdf")` とすれば、印刷向けの PDF が得られます。

色、角度、グラデーションフィルなどを自由に試してみましょう。API は柔軟なので、Word を手動で開かずにプロフェッショナルな文書を作成できます。

---

コーディングを楽しんでください！問題があれば下のコメント欄に書き込むか、Aspose.Words フォーラムをチェックしてください。コミュニティが迅速にサポートしてくれます。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}