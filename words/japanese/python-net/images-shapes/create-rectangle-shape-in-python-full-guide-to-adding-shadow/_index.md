---
category: general
date: 2026-05-04
description: Aspose.Words for Python を使用して、長方形の図形の作成方法、影付きの図形の追加方法、影の色の変更、影の距離の設定、そして文書を
  PDF として保存する方法を学びます。
draft: false
keywords:
- create rectangle shape
- how to add shape
- change shadow color
- save document as pdf
- set shadow distance
language: ja
og_description: Aspose.Words for Python を使用して長方形のシェイプを作成し、シェイプの追加方法、影の色の変更、影の距離の設定、そしてドキュメントを
  PDF として保存する方法を学びます。
og_title: 長方形を作成 – 影を追加、色を変更、PDFとして保存
tags:
- Aspose.Words
- Python
- PDF generation
title: Pythonで長方形を作成する – 影の追加とPDF保存の完全ガイド
url: /ja/python/images-shapes/create-rectangle-shape-in-python-full-guide-to-adding-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 長方形シェイプの作成 – Python 開発者向け完全チュートリアル

Word 文書で **長方形シェイプを作成** したい、そして洗練された影を付ける方法が知りたいことはありませんか？レポートジェネレータを構築していて、最終出力が PDF の場合は特にビジュアルの仕上がりが重要です。朗報です！Aspose.Words for Python を使えば、**シェイプの追加方法** だけでなく、色から距離まであらゆる影のプロパティを調整し、**PDF として文書を保存** するまでをスムーズに行えます。

このガイドでは、プロセス全体をステップバイステップで解説します。コピー＆ペーストできる正確なコードを示し、各行が *なぜ* 必要なのかを理解し、エッジケース（透明な影や非標準 DPI など）の対処法もいくつか紹介します。最後まで読めば、**長方形シェイプを作成** し、影をカスタマイズし、スムーズにクリアな PDF をエクスポートできるようになります。

## 前提条件

- Python 3.8+ がインストールされていること。  
- `pip install aspose-words` で Aspose.Words for Python を導入。  
- オブジェクト指向 Python の基本が分かっていること（特別な知識は不要）。  

すでに仮想環境がある場合は、インストールコマンドを実行するだけで準備完了です。

## 手順 1: ドキュメントとビルダーの初期化

**シェイプの追加方法** を実行する前に、作業用の空白ドキュメントが必要です。`Document` クラスがファイル全体を表し、`DocumentBuilder` がペイントブラシの役割を果たします。

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder to edit it
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

*このステップが重要な理由:* `Document` はすべてのセクション、ページ、リソースを保持します。`DocumentBuilder` はフルエント API を提供し、コンテンツを正確に挿入できる—まるでワードプロセッサのカーソルのようです。

## 手順 2: 長方形シェイプの挿入

ここで実際に **シェイプの追加方法** を行います。`insert_shape` メソッドにはシェイプの種類とサイズ（ポイント単位）が必要です。ここでは 200 × 100 pt の長方形を選び、淡いブルーの塗りを設定します。

```python
# Step 2: Insert a rectangle shape and give it a light‑blue fill
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,  # shape type
    200,                            # width in points
    100)                            # height in points
rectangle_shape.fill_color = aw.Color.light_blue
```

*プロのコツ:* 既存テキストに合わせてシェイプを配置したい場合は、挿入前に `builder.move_to` を使用するか、作成後に `left`/`top` プロパティで調整してください。

## 手順 3: 影を有効化

影のないシェイプは平坦に見えます。**影の距離を設定** し効果を可視化するために、影フォーマットを取得して有効にします。

```python
# Step 3: Access the shape's shadow format and make the shadow visible
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
```

*このステップの意義:* 影フォーマットは別オブジェクトです。`visible` をオンにしなければ、他の影プロパティはすべて無視されます。

## 手順 4: 影のスタイル設定 – 色、ぼかし、距離、方向

ここが本番です。**影の色を変更** し、ぼかし半径を調整し、影がシェイプからどれだけ離れるかを設定し、45° 回転させます。

```python
# Step 4: Configure the appearance of the shadow
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER   # outer shadow
rectangle_shadow.blur_radius = 10.0                    # blur amount (pixels)
rectangle_shadow.distance = 5.0                        # distance from the shape
rectangle_shadow.direction = 45.0                     # angle in degrees
rectangle_shadow.color = aw.Color.gray                 # shadow colour
```

*各プロパティの説明:*

| プロパティ | 機能 | 典型的な値 |
|------------|------|------------|
| `style` | 影が *内側* か *外側* かを決定 | `OUTER`（最も一般的） |
| `blur_radius` | ぼかしの強さ。数値が大きいほど柔らかい | 0–20 px が一般的 |
| `distance` | 影がシェイプからどれだけオフセットするか | 微妙な場合は 0–10 pt、ドラマチックにしたい場合は >10 |
| `direction` | 光源の角度。x 軸から時計回りに測定 | 0‑360° |
| `color` | 影の色相 | 任意の `aw.Color`（例: `gray`, `dark_red`） |

*エッジケース:* `distance` を `0` に設定すると影がシェイプの直下に重なり、塗りが事実上隠れてしまいます。可視的なオフセットを得るには `0` より大きい値を使用してください。

## 手順 5: 文書を PDF として保存

最後に **PDF として文書を保存** します。Aspose.Words は影を自動的にラスタライズするため、PDF は Word の表示とまったく同じ見た目になります。

```python
# Step 5: Save the document as a PDF with the shadowed shape
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

*PDF を選ぶ理由:* PDF はプラットフォーム間でレイアウトを保持するため、レポートや請求書、印刷物に最適です。

---

![Create rectangle shape with shadow](https://example.com/images/rectangle-shadow.png){: .align-center alt="影付き長方形の作成例"}

*上の画像は最終的な PDF 出力例です – 淡いブルーの長方形に柔らかいグレーの外側影が付いており、設定通りに表示されています。*

## よくある質問とバリエーション

### **透明な** 影が必要な場合は？

影の色にアルファチャンネルを設定します：

```python
transparent_gray = aw.Color.from_argb(128, 0, 0, 0)  # 50% opacity black
rectangle_shadow.color = transparent_gray
```

### 複数のシェイプに同じ影を適用できますか？

はい。あるシェイプから `ShadowFormat` を取得し、別のシェイプに割り当てれば完了です：

```python
another_shape = builder.insert_shape(aw.drawing.ShapeType.ELLIPSE, 150, 150)
another_shape.shadow_format = rectangle_shadow.clone()
```

### **別のシェイプタイプ** の影を変更したい場合は？

すべてのシェイプタイプは同じ `ShadowFormat` プロパティを共有しているので、同じ設定ブロックを再利用できます—`ShapeType.RECTANGLE` を `ShapeType.OVAL`、`ShapeType.TRIANGLE` などに置き換えるだけです。

### 印刷向けの **高解像度 PDF** が必要な場合は？

`PdfSaveOptions` で DPI を高く指定します：

```python
options = aw.saving.PdfSaveOptions()
options.image_resolution = 300  # 300 DPI for print quality
document.save(output_path, options)
```

## まとめ

**長方形シェイプの作成**、**シェイプの追加方法**、**影の色** のカスタマイズ、**影の距離設定**、そして最終的に **PDF として文書を保存** するために必要なすべてを網羅しました。完全に実行可能なスクリプトは以下の通りです：

```python
import aspose.words as aw

# Initialise document
document = aw.Document()
builder = aw.DocumentBuilder(document)

# Insert rectangle shape
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle_shape.fill_color = aw.Color.light_blue

# Enable and style shadow
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER
rectangle_shadow.blur_radius = 10.0
rectangle_shadow.distance = 5.0
rectangle_shadow.direction = 45.0
rectangle_shadow.color = aw.Color.gray

# Save as PDF
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

スクリプトを実行し、生成された `ShadowedShape.pdf` を開くと、微妙なグレーの影が付いた鮮明な長方形が表示されます—プロフェッショナルなレポートに期待される通りの仕上がりです。

## 次のステップは？

- **他のシェイプタイプ**（`ShapeType.OVAL`、`ShapeType.LINE` など）を試して文書を豊かにする。  
- **複数の影を組み合わせ**、シェイプをレイヤー化して「グロー」効果を作成（内側影に明るい色を使用）。  
- **バッチ処理の自動化**：データ行のコレクションをループし、行ごとにシェイプを生成して単一の PDF に統合。  
- **他の Aspose ライブラリ**（例: Aspose.Slides）と統合し、同じビジュアルを PowerPoint にエクスポート。

ぜひ実験してみてください—`blur_radius` を変更したり、`direction` をいじったり、`gray` をブランド固有の色に置き換えたり。API は柔軟なので、少しの調整でビジュアルインパクトが大きく変わります。

質問や難しいシナリオがありますか？コメントを残すか、Aspose コミュニティフォーラムで質問してください。コーディングを楽しみながら、影付き長方形を存分に活用しましょう！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}