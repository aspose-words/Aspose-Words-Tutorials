---
category: general
date: 2026-08-07
description: Aspose.Words for Python を使用して PDF に長方形を描画し、図形に影を追加する方法、影の設定方法、そしてドキュメントを
  PDF として保存する方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle in pdf
- add shadow to shape
- save document as pdf
- configure shape shadow
language: ja
lastmod: 2026-08-07
og_description: Aspose.Words for Python を使用して PDF に長方形を描画します。このチュートリアルでは、図形に影を追加し、影の設定方法を示し、プロフェッショナルな文書生成のために文書を
  PDF として保存する方法を解説します。
og_image_alt: PDF page showing a rectangle shape with a visible shadow created by
  Aspose.Words for Python
og_title: Aspose.Words for PythonでPDFに矩形を描く – ガイド
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Draw rectangle in PDF using Aspose.Words for Python and learn how to
    add shadow to shape, configure shape shadow, and save document as PDF.
  headline: Draw rectangle in PDF with Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF
- Shape
- Shadow
title: Aspose.Words for PythonでPDFに矩形を描画する
url: /ja/python/images-shapes/draw-rectangle-in-pdf-with-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Python を使用して PDF に矩形を描画する

Pythonで作業中に **PDF に矩形を描画** する必要がある場合、このガイドは完全な、すぐに実行できるソリューションを提供します。**図形に影を追加** する方法、影の設定方法、そして最終的に **PDF として文書を保存** する方法を正確に確認できます。

シェーディングされた矩形の作成は、レポート、請求書、視覚的注釈などで一般的な要件です。このチュートリアルの最後までに、リアルな影付きの矩形を含む PDF を生成する単一スクリプトが手に入り、サイズ、色、オフセットを任意のデザインに合わせて調整する方法が理解できるようになります。

## 前提条件

開始する前に、以下を確認してください：

* Python 3.8+ がインストールされていること。
* Aspose.Words for Python via .NET パッケージ (`aspose-words`) – 以下でインストール:

```bash
pip install aspose-words
```

* PDF を保存しようとしているフォルダーへの書き込み権限があること。

追加のライブラリは不要です。Aspose.Words が形状作成、影の設定、PDF エクスポートを内部で処理します。

## ステップ 1: 新しい空白ドキュメントを作成する（PDF に矩形を描画 – 初期化）

最初のステップは `Document` オブジェクトをインスタンス化することです。このオブジェクトは PDF 全体を表し、セクション、段落、形状のコンテナを提供します。

```python
import aspose.words as aw

# Create an empty Word document – it will become a PDF later
doc = aw.Document()
```

**なぜ重要か:** Aspose.Words は PDF 生成を Word ドキュメントモデルからの変換として扱うため、最終出力が PDF であっても `Document` から開始します。

## ステップ 2: 文書本文に矩形形状を挿入する

矩形は特定の `ShapeType` です。最初のセクションの本文に追加すると、PDF に保存したときに自動的に新しいページが作成されます。

```python
# Append a rectangle shape to the first section's body
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Set the rectangle's dimensions (points = 1/72 inch)
rectangle.width = 200   # 200 pt ≈ 2.78 in
rectangle.height = 100  # 100 pt ≈ 1.39 in

# Optional: give the shape some visible text
rectangle.text = "Shadow demo"
```

**解説:** `width` と `height` プロパティは PDF 内での形状の視覚的サイズを制御します。テキストを追加すると、テスト時に矩形が確認しやすくなります。

## ステップ 3: 形状に影を追加 – 有効化とカスタマイズ

ここで影効果をオンにし、外観を微調整します。これが **add shadow to shape** キーワードの出番です。

```python
# Access the shape's shadow effect object
shadow = rectangle.shadow_effect

# Make the shadow visible
shadow.visible = True

# Configure blur radius (pt) – higher values produce a softer edge
shadow.blur = 8

# Set the distance (offset) from the shape in points
shadow.distance = 5

# Define the direction of the shadow in degrees (0 = right, 90 = down)
shadow.angle = 45

# Choose a shadow color – black works for most documents
shadow.color = aw.drawing.Color.black
```

**なぜ形状の影を設定するのか:** `blur`、`distance`、`angle` を調整することで、リアルな照明効果をシミュレートでき、生成された PDF の可読性と視覚的階層が向上します。

## ステップ 4: 文書を PDF として保存 – 最終出力

矩形とその影が定義されたら、最後のステップは Word 文書を PDF にエクスポートすることです。これで **save document as pdf** の要件が満たされます。

```python
# Define the output path – replace YOUR_DIRECTORY with an actual folder
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)
print(f"PDF saved to {output_path}")
```

`shadow_rectangle.pdf` を開くと、灰色の枠線が付いた矩形が「Shadow demo」というタイトルとともに、鮮明な斜め影が付いた単一ページとして表示されます。

### 期待される出力

* `shadow_rectangle.pdf` という名前の PDF ファイル。
* 200 pt × 100 pt の矩形が 1 ページに表示。
* 45° の角度で 5 pt オフセット、8 pt のぼかしが適用された影が可視。

## ステップ 5: バリエーションとエッジケースの検討（任意）

実務でよく使われる調整例を以下に示します：

| バリエーション | コードスニペット | 使用する場面 |
|-----------|--------------|-------------|
| **異なる形状タイプ**（例: 楕円） | `aw.drawing.ShapeType.OVAL` を `RECTANGLE` の代わりに使用 | 丸みを帯びたグラフィックやバッジが必要な場合 |
| **カスタム影色** | `shadow.color = aw.drawing.Color.from_argb(255, 100, 100, 100)` | グレーまたはブランド固有の影が必要な場合 |
| **複数の形状** | 形状作成ブロックを繰り返し、`left`/`top` プロパティを調整 | 複雑な図を構築する場合 |
| **形状内にテキストなし** | `rectangle.text = "..."` を省略 | 形状が純粋に装飾目的の場合 |
| **高 DPI 出力** | `doc.save(output_path, aw.SaveFormat.PDF, aw.PdfSaveOptions())` に `PdfSaveOptions` で画像品質を設定 | 印刷用 PDF の場合 |

**プロのコツ:** 他のプロパティを調整する前に必ず `shadow.visible = True` を設定してください。設定しないと変更が無視されます。

## 完全スクリプト – コピーして貼り付け、実行

```python
import aspose.words as aw

# 1️⃣ Create a new blank document
doc = aw.Document()

# 2️⃣ Add a rectangle shape
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
rectangle.width = 200          # width in points
rectangle.height = 100         # height in points
rectangle.text = "Shadow demo"

# 3️⃣ Configure a visible shadow effect
shadow = rectangle.shadow_effect
shadow.visible = True
shadow.blur = 8                # blur radius (pt)
shadow.distance = 5            # offset distance (pt)
shadow.angle = 45              # direction (degrees)
shadow.color = aw.drawing.Color.black

# 4️⃣ Save the document as a PDF
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)

print(f"PDF successfully created at: {output_path}")
```

ターミナルまたは IDE からスクリプトを実行してください。`YOUR_DIRECTORY` を実際のフォルダー パス（例: `"/tmp"` や `"C:\\Users\\Me\\Documents"`）に置き換えます。

## 結論

これで Aspose.Words for Python を使用して **PDF に矩形を描画** し、**図形に影を追加**、**形状の影を設定**、そして **PDF として文書を保存** する方法が分かりました。完全な例は文書作成から最終エクスポートまでのすべての手順を示しており、オプションのバリエーションはコードをより複雑なシナリオに適応させる方法を提供します。

次に検討できること：

* 他の形状タイプ（`ShapeType.LINE`、`ShapeType.ELLIPSE`）の追加。
* グラデーション塗りや枠線を適用して視覚的魅力を高める。
* `PdfSaveOptions` を使用してフォント埋め込みや画像圧縮を制御。

パラメーターを自由に試して、ブランドやデザインガイドラインに合わせてください。PDF スクリプト作成を楽しんでください！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを基にした、密接に関連するトピックをカバーしています。各リソースには、ステップバイステップの説明と完全な動作コード例が含まれており、追加の API 機能を習得したり、独自プロジェクトで代替実装アプローチを探求したりするのに役立ちます。

- [Aspose.Words for Python を使用した PDF ブックマークの最適化](/words/english/python-net/performance-optimization/optimize-pdf-bookmarks-aspose-words-python/)
- [Aspose.Words for Python で PDF 読み込み時に画像をスキップして最適化](/words/hindi/python-net/performance-optimization/optimize-pdf-loading-python-aspose-words-skip-images/)
- [Aspose.Words Python PDF 操作](/words/hongkong/python-net/document-operations/aspose-words-python-pdf-manipulation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}