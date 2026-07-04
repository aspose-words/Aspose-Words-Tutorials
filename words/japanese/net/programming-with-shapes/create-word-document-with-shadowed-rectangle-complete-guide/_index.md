---
category: general
date: 2026-04-21
description: スタイル付きの長方形と影を持つWord文書を作成します。C#で影の追加、長方形シェイプの挿入、影の色設定などの方法を学びましょう。
draft: false
keywords:
- create word document
- how to add shadow
- insert rectangle shape
- create rectangle in word
- set shadow color
language: ja
og_description: C#でWord文書を作成し、影付きの長方形シェイプを追加します。このガイドに従って、影の色、ぼかし、オフセットを簡単に設定しましょう。
og_title: 影付き長方形でWord文書を作成 – ステップバイステップ
tags:
- Aspose.Words
- C#
- Document Automation
title: 影付き長方形でWord文書を作成する – 完全ガイド
url: /ja/net/programming-with-shapes/create-word-document-with-shadowed-rectangle-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 影付き長方形でWord文書を作成 – 完全ガイド

普通のテキストページよりも少し洗練された **Word文書** を作りたくありませんか？レポートのテンプレートやチラシを作成していて、さりげない影付きの長方形があれば十分ということもあるでしょう。このチュートリアルでは、長方形シェイプの挿入、影の有効化、色・ぼかし・オフセットのカスタマイズを C# と Aspose.Words で行う手順を詳しく解説します。

また、Word 2016、2019、最新の Office 365 ビルドのいずれでも動作する **影の追加方法** もカバーします。最後には、影付き長方形が描かれた *.docx* ファイルを保存でき、各プロパティの「なぜ」も理解できるようになります。

## 前提条件

- .NET 6（または最近の .NET Framework バージョン）  
- Aspose.Words for .NET NuGet パッケージ（`Install-Package Aspose.Words`）  
- C# 文法の基本的な知識  
- Visual Studio などの IDE（任意のエディタでも可）

追加のライブラリは不要です。すべて Aspose.Words の中に収められています。

## Step 1 – Initialize the Document and Builder (Create Word Document)

プログラムで **Word文書** を作成するには、まず `Document` クラスから始めます。`DocumentBuilder` はペイントブラシのようなもので、テキストやシェイプ、その他の要素を追加できます。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowRectangleDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*重要ポイント:* `Document` オブジェクトは .docx ファイル全体を表します。これがなければ、長方形や影を添付する場所がありません。

## Step 2 – Insert a Rectangle Shape (Insert Rectangle Shape)

ここで実際に **長方形シェイプを挿入** します。`InsertShape` メソッドは `ShapeType` 列挙体と、幅・高さ（ポイント単位）を受け取ります。

```csharp
        // Step 2: Insert a rectangle shape of the desired size (200x100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

*プロのコツ:* 1 ポイントは約 1/72 インチです。したがって 200 pts はおよそ 2.78 インチの幅に相当します。レイアウトに合わせて数値を調整してください。

## Step 3 – Enable the Shadow (How to Add Shadow)

影はデフォルトで無効化されています。`Visible` フラグをオンにして有効にします。

```csharp
        // Step 3: Turn on the shadow for the shape
        rectangle.ShadowFormat.Visible = true;
```

*何が起きているか?* `Visible` が true の場合、Word は次に設定する他のプロパティに基づいてドロップシャドウを描画します。

## Step 4 – Customize Shadow Appearance (Set Shadow Color, Blur, Offsets)

ここで **影の色**、ぼかし半径、X/Y オフセットを **設定** します。自由に試してみてください。値を変えると、柔らかな光、深いドロップ、あるいは「浮いている」ような効果が得られます。

```csharp
        // Step 4: Define the shadow appearance – colour, blur radius and offsets
        rectangle.ShadowFormat.Color = Color.Gray;   // shadow colour
        rectangle.ShadowFormat.Blur = 5.0;           // blur radius (points)
        rectangle.ShadowFormat.OffsetX = 4.0;        // horizontal offset (points)
        rectangle.ShadowFormat.OffsetY = 4.0;        // vertical offset (points)
```

*なぜこの数値か?* ぼかし 5 pts はやさしいフェザーエッジを作り、オフセット 4 pts は右下に影をずらし、左上から光が当たっているように見せます。`Color` を `Color.Black` に変更すればコントラストが強くなり、`Color.FromArgb(128, 0, 0, 0)` を使えば半透明の黒になります。

### エッジケースとバリエーション

- **ぼかしなし:** `Blur = 0` に設定すると、くっきりとしたハードエッジの影になります。  
- **負のオフセット:** `OffsetX = -4` とすれば影を左側に移動できます。  
- **別のシェイプ:** 同じ影プロパティは円形、三角形、フリードローシェイプでも機能します—Step 2 の `ShapeType` を変更するだけです。  
- **互換性:** Aspose.Words は影データを Office Open XML 形式で書き出すため、Word 2010‑2021 および Office 365 で問題なく動作します。

## Step 5 – Save the Document (Create Word Document)

最後にファイルをディスクに保存します。サポートされている任意の形式（`.docx`、`.pdf`、`.odt` など）を選べますが、このガイドでは従来の Word 形式に絞ります。

```csharp
        // Step 5: Save the document with the shaped shadow
        document.Save("ShadowRectangle.docx");
    }
}
```

**ShadowRectangle.docx** を Microsoft Word で開くと、グレーの長方形に右下方向へ微妙にぼかされた影が付いているのが確認できます—まさにスクリプト通りの結果です。

### 期待される出力

- 1 ページの *.docx* ファイル。  
- `InsertShape` 呼び出し時のカーソル位置を中心とした 200 pt × 100 pt の長方形。  
- 右下に 4 pts、下にも 4 pts のオフセット、ぼかし 5 pt のグレー影。

シェイプがセンタリングされていない場合は、`builder.MoveTo` でカーソル位置を調整するか、挿入後にシェイプの `Left` と `Top` プロパティを変更してください。

## よくある質問とトラブルシューティング

**Q: Word で影が表示されません。**  
A: `ShadowFormat.Visible` が `true` になっているか確認してください。また、Aspose.Words のバージョンが最新か（影機能はバージョン 20.3 で追加）もチェックしましょう。

**Q: 影にグラデーションを適用できますか？**  
A: `ShadowFormat` では直接はできません。Word の UI ではグラデーション影がサポートされていますが、Open XML スキーマ（Aspose.Words が従うもの）では実線カラーの影しか公開されていません。XML を手動で編集する必要があります—高度なシナリオです。

**Q: 透明な長方形に影だけ付けたい場合は？**  
A: 挿入後に `rectangle.FillColor = Color.Transparent;` と設定してください。影は塗りつぶしとは独立して描画されます。

## 本番コード向けプロティップ

- **Builder の再利用:** 複数シェイプを追加する場合は同じ `DocumentBuilder` インスタンスを使い回すと、シェイプごとに新しいインスタンスを作るオーバーヘッドを削減できます。  
- **バッチ保存:** すべての変更が終わったら一度だけ保存しましょう。頻繁な I/O は大規模文書生成を遅くします。  
- **例外処理:** 全体を `try / catch` で囲み、`Aspose.Words` の例外をログに残すと、テンプレートが破損した際に行番号など有用な情報が得られます。

## 次のステップ（関連トピック）

- **画像やテキストボックスに影を追加**（同様の `ShadowFormat` 使用）。  
- **テーブルセル内に長方形シェイプを挿入**してカスタムセルスタイリング。  
- **Word のネイティブ XML で長方形を作成**（生の Open XML が好きな方向け）。  
- **ユーザー入力やテーマカラーに応じて影色を動的に設定**。

さまざまな色、ぼかし半径、オフセットを試してみてください。たとえば企業レポートには柔らかいブルーの光、ドラマチックなチラシには濃い黒の影など、可能性は無限です。コード変更は最小限で済みます。

---

### クイックまとめ

- **Word文書をゼロから作成** しました。  
- **長方形シェイプを挿入**し、影を有効化しました。  
- **影の色、ぼかし、オフセット** を設定してプロフェッショナルな外観に仕上げました。  
- ファイルを保存し、配布可能な状態にしました。

これで、Word 自動化プロジェクトに視覚的なアクセントを加えるための確固たる基盤ができました。さらにアイデアがあればコメントで教えてください。会話を続けましょう。ハッピーコーディング！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}