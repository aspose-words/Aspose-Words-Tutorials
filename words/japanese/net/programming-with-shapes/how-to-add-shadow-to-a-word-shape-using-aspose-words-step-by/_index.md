---
category: general
date: 2026-01-06
description: Aspose.Words C# を使用して Word の図形に影を追加する方法。図形に影を適用し、影の角度を設定し、影の距離をすばやく調整する方法を学びましょう。
draft: false
keywords:
- how to add shadow
- apply shadow to shape
- add shape shadow
- set shadow angle
- adjust shadow distance
language: ja
og_description: C#でWordの図形に影を追加する方法。このチュートリアルでは、図形に影を適用し、影の角度を設定し、Aspose.Wordsで影の距離を調整する方法を示します。
og_title: Wordの図形に影を追加する方法 – 完全なAspose.Wordsガイド
tags:
- Aspose.Words
- C#
- Document Processing
- Graphics
title: Aspose.Words を使用して Word の図形に影を追加する方法 – ステップバイステップガイド
url: /ja/net/programming-with-shapes/how-to-add-shadow-to-a-word-shape-using-aspose-words-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words を使用して Word のシェイプに影を追加する方法

Word 文書を開かずにシェイプに **影を追加する方法** を考えたことはありませんか？ 開発者はレポートや請求書、マーケティングフライヤーに視覚的な磨きをかけたいことが多いですが、毎回 UI を起動したくはありません。

このチュートリアルでは、**影を追加する方法** をプログラムで実装する手順を解説し、各プロパティの意味を説明しながら、*シェイプに影を適用する*、*影の角度を設定する*、*影の距離を調整する* を数行の C# コードで実現する方法を示します。

> **得られるもの:** DOCX を読み込み、最初のシェイプにリアルなドロップシャドウを追加し、結果を新しいファイルとして保存する完全に実行可能なサンプルです。外部ツールは不要で、Aspose.Words for .NET だけで完結します。

## 前提条件

- .NET 6.0（または最近の .NET Framework バージョン）  
- Aspose.Words for .NET ≥ 23.10（執筆時点での最新安定版）  
- 少なくとも 1 つの描画シェイプが含まれる Word 文書（`shapes.docx`）  
- Visual Studio、Rider、またはお好みの C# IDE  

ライブラリが不足している場合は、NuGet から取得してください。

```bash
dotnet add package Aspose.Words
```

基本は以上ですので、実際の手順に入りましょう。

## シェイプに影を追加する – 概要

**シェイプに影を追加する方法** の核心は、各 `Shape` が公開する `ShadowFormat` オブジェクトにあります。`ShadowFormat` は影の「スタイルシート」のようなもので、可視性、色、ぼかし、オフセット、方向といったプロパティを制御します。

大まかな流れは次の通りです：

1. ソース文書を読み込む。  
2. 対象の `Shape` を取得する。  
3. その `ShadowFormat` を取得する。  
4. 影の視覚プロパティを設定する（*影の角度を設定* と *影の距離を調整* を含む）。  
5. 変更した文書を保存する。

各ステップは個別のセクションに分かれているので、必要な部分だけを抜き出して利用できます。

<img src="shadow-example.png" alt="Word 文書における影の追加例">

## 手順 1 – Word 文書を読み込む

まず、ソースファイルを指す `Document` インスタンスが必要です。この操作は軽量で、Aspose.Words がファイルをストリームし、メモリ上の DOM を構築します。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Load the DOCX that already contains a shape.
Document doc = new Document("YOUR_DIRECTORY/shapes.docx");
```

**なぜ重要か:** 文書を読み込むことでノードツリーにアクセスでき、シェイプは `NodeType.Shape` として存在します。これがなければ影を適用する対象がありません。

## 手順 2 – 最初のシェイプ（または任意のシェイプ）を取得する

シェイプはインデックス、名前、またはカスタム述語で取得できます。ここでは簡単のため、文書内の最初のシェイプを取得します。`GetChild` メソッドは深さ優先でツリーを走査し、要求されたノードを返します。

```csharp
// Grab the first shape – change the index if you need a different one.
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (shape == null)
{
    throw new InvalidOperationException("No shape found in the document.");
}
```

**プロのコツ:** 文書に複数のシェイプがある場合は、`doc.GetChildNodes(NodeType.Shape, true)` をループして各シェイプに影を適用すると便利です。これはスライドやページ全体に *シェイプに影を追加* したいときの一般的なバリエーションです。

## 手順 3 – 影の書式オブジェクトにアクセスして設定する

いよいよ **シェイプに影を追加する方法** の核心、`ShadowFormat` にたどり着きました。このオブジェクトが影の外観に関するすべての調整項目を保持しています。

```csharp
// Step 3: Get the shadow format for the shape.
ShadowFormat shadow = shape.ShadowFormat;

// Make the shadow visible.
shadow.Visible = true;

// Choose a dark gray color for a subtle effect.
shadow.Color = Color.DarkGray;

// Set transparency to 30 % (0.0 = opaque, 1.0 = fully transparent).
shadow.Transparency = 0.3;

// Blur radius – larger values give a softer edge.
shadow.Size = 5;
```

### 影の角度を設定し、影の距離を調整する

ここで *影の角度を設定* と *影の距離を調整* のキーワードが登場します。角度は光源の方向を決め、距離はシェイプから影がどれだけ離れるかを定義します。

```csharp
// Angle in degrees – 45° points down‑right.
shadow.Angle = 45;

// Distance in points – how far the shadow is shifted.
shadow.Distance = 3;
```

**なぜこの数値か？** 45° の角度に距離 3 pts を組み合わせると、左上から光が当たっているような自然な見た目になります。自由に試してみてください。0° は影が真下に、180° は上に配置されます。

## 手順 4 – 文書を保存して結果を確認する

影のプロパティ設定が完了したら、文書をディスクに書き出すだけです。Aspose.Words が低レベルの OOXML をすべて処理します。

```csharp
// Save the modified document with the new shadow effect.
doc.Save("YOUR_DIRECTORY/shadowed.docx");
```

`shadowed.docx` を Microsoft Word または互換ビューアで開くと、最初のシェイプに 45° 方向のソフトなダークグレーのドロップシャドウが適用されているはずです。

### 簡易検証チェックリスト

- **可視性:** 影が実際に描画されているか？（`shadow.Visible` が `true` であること）  
- **色と透明度:** 影は濃い黒ではなく、微妙なグレーに見えるか？  
- **角度と距離:** 指定した方向に影がオフセットされているか？  
- **ぼかし（サイズ）:** エッジはデザインに適した滑らかさか？

問題がある場合は該当プロパティを調整し、再保存してください。変更は即座に反映されます。

## よくあるバリエーションとエッジケースの対処

### 複数シェイプに影を追加する

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape s in shapes)
{
    ShadowFormat sf = s.ShadowFormat;
    sf.Visible = true;
    sf.Color = Color.Black;
    sf.Transparency = 0.2;
    sf.Size = 4;
    sf.Angle = 30;
    sf.Distance = 2;
}
doc.Save("YOUR_DIRECTORY/all_shapes_shadowed.docx");
```

### 影をリセット（削除）する

条件付きで *シェイプに影を追加* した後にオフにしたい場合は次のようにします：

```csharp
shape.ShadowFormat.Visible = false;
```

### 互換性に関する注意点

- Aspose.Words 23.10 以降は DOCX、DOC、さらには PDF エクスポートでも影プロパティを完全にサポートします。  
- `doc.Save("out.pdf")` で PDF に変換しても影効果は保持されます。  
- 古い Word バージョン（< 2007）は OOXML の影情報を保存できないため、`.doc` 形式で保存すると効果が失われます。ベストな結果を得るには `.docx` を使用してください。

## プロのコツ – 再利用可能なヘルパーメソッドを作る

多くのプロジェクトで同じ影設定を適用する場合は、ユーティリティメソッドにまとめると便利です：

```csharp
public static void ApplyStandardShadow(Shape target, Color? color = null,
                                        double transparency = 0.3,
                                        double size = 5,
                                        double angle = 45,
                                        double distance = 3)
{
    ShadowFormat sf = target.ShadowFormat;
    sf.Visible = true;
    sf.Color = color ?? Color.DarkGray;
    sf.Transparency = transparency;
    sf.Size = size;
    sf.Angle = angle;
    sf.Distance = distance;
}
```

これで `ApplyStandardShadow(shape);` と一行書くだけで *シェイプに影を適用* できます。

## 結論

Aspose.Words を使って Word のシェイプに **影を追加する方法** を最初から最後まで解説しました。文書を読み込み、シェイプを取得し、`ShadowFormat`（*影の角度を設定* と *影の距離を調整* を含む）を構成し、ファイルを保存するだけで、Word を開くことなくプロフェッショナルなドロップシャドウを任意の図に付与できます。

色や透明度を変えて *シェイプに影を適用* したり、コレクション全体に *シェイプに影を追加* したり、*影の角度を設定* でドラマチックな照明効果を試したりしてみてください。次のステップとして、境界線、反射、3‑D 回転など他のスタイリング機能と組み合わせることが考えられます。

エッジケースやパフォーマンス、PDF 変換に関する質問があればコメントで教えてください。Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}