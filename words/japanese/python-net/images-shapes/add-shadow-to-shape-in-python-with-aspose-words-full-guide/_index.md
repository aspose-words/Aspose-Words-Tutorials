---
category: general
date: 2026-06-30
description: Aspose.Words for Python を使用して図形に影を追加します。影の距離の設定方法、ぼかしのカスタマイズ方法、そして影付きの
  PDF をすばやく保存する方法を学びましょう。
draft: false
keywords:
- add shadow to shape
- how to set shadow distance
- how to add shape shadow
- Aspose.Words Python shadow
- shape formatting Python
language: ja
og_description: Aspose.Words for Python を使用して、Word 文書の図形に影を追加します。このチュートリアルでは、影の距離、ぼかし、色の設定方法と、PDF
  への保存方法を示します。
og_title: Pythonで図形に影を追加する – 完全なAspose.Wordsガイド
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Add shadow to shape using Aspose.Words for Python. Learn how to set
    shadow distance, customize blur, and save a PDF with shape shadow quickly.
  headline: Add Shadow to Shape in Python with Aspose.Words – Full Guide
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python. Learn how to set
    shadow distance, customize blur, and save a PDF with shape shadow quickly.
  name: Add Shadow to Shape in Python with Aspose.Words – Full Guide
  steps:
  - name: What if I need a different shape?
    text: Replace `aw.drawing.ShapeType.RECTANGLE` with any other enum value, e.g.,
      `aw.drawing.ShapeType.ELLIPSE`. The same shadow properties apply—no extra code
      needed.
  - name: Can I apply a shadow to multiple shapes at once?
    text: 'Yes. Loop over the shapes you create and configure each `shadow_format`
      individually. Here’s a quick snippet:'
  - name: How do I change the shadow’s opacity?
    text: 'Use the `shadow.transparency` property (0 = opaque, 1 = fully transparent):'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Aspose.Words を使用した Python でシェイプに影を追加する – 完全ガイド
url: /ja/python/images-shapes/add-shadow-to-shape-in-python-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python と Aspose.Words でシェイプに影を追加する – 完全ガイド

Aspose.Words for Python を使って Word 文書のシェイプに影を追加するのは、思ったより簡単です。**影の距離の設定方法**や**シェイプに影を追加する方法**で、洗練された外観を実現したいと考えている方のために、このガイドがすべてカバーします。

数分で、ドキュメントの作成、長方形の挿入、影プロパティの調整、そして効果を確認できる PDF の保存までを順に解説します。最後まで読めば、長方形・楕円・カスタム描画など、任意のシェイプに影を付ける方法が API ドキュメントを探さずに分かります。

> **Prerequisites** – Python 3.7 以上がインストールされていること、Aspose.Words for Python のライセンス（または無料評価版）を取得していること、そして Python スクリプトの基本が分かっていることが必要です。その他の外部ライブラリは不要です。

---

## シェイプに影を追加する – 手順概要

以下は本チュートリアルで実行する流れです。

1. **新しいドキュメント** とそれを編集する `DocumentBuilder` を作成。  
2. 必要なサイズの **長方形シェイプ** を挿入。  
3. **影を有効化しカスタマイズ** – ここが本チュートリアルの核です。  
4. **PDF として保存** し、シェイプの影が保持されることを確認。

各ステップは独立したセクションになっているので、コードスニペットをそのまま IDE に貼り付けて実行できます。

---

## Step 1: Initialize the Document and Builder

まずは `Document` がなければ何もできません。`DocumentBuilder` はあなたのペイントブラシです。

```python
import aspose.words as aw

# Create a new, empty Word document
document = aw.Document()

# Attach a builder to the document for easy editing
builder = aw.DocumentBuilder(document)
```

*Why this matters*: `Document` オブジェクトはファイル全体を表し、`DocumentBuilder` はテキスト、テーブル、シェイプの挿入を簡略化します。ビルダーはページ上を自由に移動できるカーソルのようなものです。

---

## Step 2: Insert a Rectangle Shape

次に長方形を追加します—影効果のキャンバスです。必要に応じて `RECTANGLE` を `ELLIPSE`、`STAR`、その他の `ShapeType` に置き換えて別の形状にできます。

```python
# Insert a rectangle with width=200pt and height=100pt
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

*Pro tip*: サイズはポイント単位です (1 pt ≈ 1/72 inch)。レイアウトに合わせて調整してください。影は自動的にスケーリングされます。

---

## How to Set Shadow Distance

影の **distance** はシェイプからどれだけ離れて表示されるかを決めます。距離が大きいほど光源が遠くにあるように見え、距離が小さいと微妙な浮き上がりになります。

```python
# Access the shadow format of the shape
shadow = rectangle_shape.shadow_format

# Make the shadow visible
shadow.visible = True

# Set the distance (in points) from the shape
shadow.distance = 4.0          # <-- this is the "how to set shadow distance" part
```

> **Note**: distance は `angle` と連動します。角度を変えると影がシェイプの周りを回転し、distance が影を外側へ押し出します。

---

## How to Add Shape Shadow – Customizing Blur, Color, and Angle

影をオンにするだけでなく、リアルな効果を得るためにぼかし、色、方向を調整したいことが多いです。

```python
# Define how blurry the shadow should be (larger = softer)
shadow.blur_radius = 5.0       # Soft edge for a natural look

# Choose the direction (in degrees). 45° points down‑right.
shadow.angle = 45

# Set the shadow color – black works for most cases
shadow.color = aw.drawing.Color.black
```

*Why these settings?*  
- **Blur radius** はエッジを柔らかくし、硬いシルエットにならないようにします。  
- **Angle** は光源の方向をシミュレートします。45° はバランスの取れたデフォルトです。  
- **Color** は任意の `Color` オブジェクトで指定できます。柔らかい効果を求めるなら `Color.gray` を試してください。

---

## Step 4: Save the Document as PDF

シェイプと影の設定が完了したら、結果を保存するのはとても簡単です。Aspose.Words が自動的に PDF へ変換し、ビジュアルの忠実度を保持します。

```python
# Save the document to a PDF file (adjust the path as needed)
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
document.save(output_path)
print(f"Document saved to {output_path}")
```

*Expected output*: 生成された `ShadowShape.pdf` を開くと、200 × 100 pt の長方形が 4 pt 離れた位置に 45° の角度で影が落ち、5 pt のぼかしが適用されています。影はシェイプに沿った微かなグレイ‑ブラックのハローとして表示されます。

---

## Common Questions & Edge Cases

### 別の形状が必要な場合は？

`aw.drawing.ShapeType.RECTANGLE` を他の列挙値、例 `aw.drawing.ShapeType.ELLIPSE` に置き換えるだけです。影のプロパティは同じままで、追加コードは不要です。

### 複数のシェイプに一括で影を適用できる？

可能です。作成したシェイプをループし、各 `shadow_format` を個別に設定します。以下は簡易サンプルです。

```python
for shape_type in [aw.drawing.ShapeType.RECTANGLE, aw.drawing.ShapeType.ELLIPSE]:
    shp = builder.insert_shape(shape_type, 150, 80)
    shp.shadow_format.visible = True
    shp.shadow_format.distance = 3.0
    shp.shadow_format.blur_radius = 4.0
```

### 影の不透明度を変更するには？

`shadow.transparency` プロパティを使用します (0 = 不透明、1 = 完全に透明)：

```python
shadow.transparency = 0.3   # 30 % transparent
```

---

## Full Working Example

以下が完全なスクリプトです。コピーして出力フォルダーを調整し、実行してください。抜けている部分はありません。

```python
import aspose.words as aw

# 1️⃣ Create a new document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert a rectangle shape (200 × 100 pt)
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Enable and configure the shadow (add shadow to shape)
shadow = rectangle_shape.shadow_format
shadow.visible = True                # Show the shadow
shadow.blur_radius = 5.0             # Soft edges
shadow.distance = 4.0                # How far the shadow lies from the shape
shadow.angle = 45                    # Direction of the light source
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.0            # Fully opaque (optional)

# 4️⃣ Save as PDF
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
document.save(output_path)
print(f"PDF with shape shadow saved at: {output_path}")
```

スクリプトを実行し、生成された PDF を開きます。長方形に鮮明でオフセットされた影が付いているはずです—**add shadow to shape** が約束した通りです。

---

## Conclusion

本稿では、Aspose.Words for Python を使用して Word 文書のシェイプに **影を追加する** 方法を実演しました。**影の距離を設定**、ぼかし・角度・色のカスタマイズ、そして効果を保持した PDF へのエクスポートまでの重要ステップを網羅しています。この手法は任意のシェイプタイプで機能し、ループや不透明度調整、グラデーション影などに拡張可能です。

次の課題に挑戦してみませんか？複数の影を組み合わせたり、シェイプをレイヤー化したり、各チャートに個別のスタイリッシュな影を付けたレポートを生成したりしてみましょう。実践することで概念が定着し、ドキュメント自動化の新たな可能性が見えてきます。

このガイドが役に立ったら、ぜひシェアしたり、Aspose.Words リポジトリにスターを付けたり、独自の影調整テクニックをコメントで共有してください。Happy coding!

## What Should You Learn Next?

以下のチュートリアルは、本ガイドで示したテクニックを基にした、密接に関連するテーマを扱っています。各リソースには、ステップバイステップの解説と完全なコード例が含まれており、API の追加機能をマスターしたり、独自プロジェクトで代替実装を試したりするのに役立ちます。

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}