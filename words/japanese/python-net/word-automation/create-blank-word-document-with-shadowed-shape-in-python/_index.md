---
category: general
date: 2026-10-16
description: Python を使用して、空白の Word 文書を作成し、Word に図形を挿入し、外側の影を付けて PDF として保存する。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert shape in word
- save as pdf python
- add outer shadow shape
- create pdf with shape
language: ja
lastmod: 2026-10-16
og_description: Aspose.Words for Python を使用して、外側に影が付いたシェイプを持つ空白の Word 文書を作成します。このガイドでは、シェイプの挿入方法、影の適用方法、そしてファイルを
  PDF として保存する手順を示します。
og_image_alt: Screenshot of a Word document containing a rectangle shape with an outer
  shadow, saved as PDF
og_title: シェイプの影付き空白Word文書を作成 – Pythonガイド
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document, insert shape in Word, add outer shadow,
    and save as PDF using Python.
  headline: Create blank Word document with shadowed shape in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- PDF generation
- Shape styling
title: Pythonで影付きシェイプを持つ空白のWord文書を作成する
url: /ja/python/word-automation/create-blank-word-document-with-shadowed-shape-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Pythonで影付きシェイプの空白Word文書を作成

もし **create blank Word document** を作成し、カスタムグラフィックを追加したい場合は、このガイドが役立ちます。**insert shape in Word** の方法、**outer shadow shape** の適用、そして最終的に **save as PDF using Python** の手順を順に説明します。

このチュートリアルでは、Aspose.Words for Python のセットアップ方法、矩形の作成、影のスタイル設定、そして視覚効果を保持したまま PDF を生成する手順を学びます。Aspose API の事前知識は不要ですが、基本的な Python の知識と Python 3.10 以降がインストールされている環境が必要です。

## 前提条件

開始する前に、以下を確認してください。

* Python 3.10 以上がインストールされていること。
* 有効な Aspose.Words for Python ライセンス（評価用の無料トライアルでも可）。
* `aspose-words` パッケージをインストールできる `pip` 環境。
* PDF を保存するディレクトリへの書き込み権限。

以下のコマンド一つでライブラリをインストールできます。

```bash
pip install aspose-words
```

## 空白の Word 文書を作成 – 環境設定

最初のステップは、シェイプを配置するキャンバスとなる空の Word ファイルを作成することです。

```python
import aspose.words as aw

# Initialize a new, empty document
doc = aw.Document()
# DocumentBuilder provides convenient methods for adding content
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` は完全に空白の Word ファイルを表します。`DocumentBuilder` を使用すると、次のステップで利用する `insert_shape` などのメソッドにアクセスできます。

## Word にシェイプを挿入しサイズを設定

次に、後で外側の影を付ける矩形を追加します。サイズはポイントで指定します（1 pt ≈ 1/72 インチ）。

```python
# Insert a rectangle shape with a width of 200 pt and a height of 100 pt
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)
```

`insert_shape` の呼び出しは `Shape` オブジェクトを返し、さらにカスタマイズ可能です。この時点で、Microsoft Word で開くと矩形が表示された状態になっています。

## 外側の影シェイプを追加 – 効果のカスタマイズ

Aspose.Words では `ShadowEffect` クラスを使って、影のスタイル、ぼかし、距離、色などのプロパティを定義できます。

```python
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a new shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # Choose an outer shadow
shadow.blur = 5.0                         # Softness of the shadow edges
shadow.distance = 3.0                     # Offset distance from the shape
shadow.color = aw.Color.black             # Shadow color

# Apply the shadow to the rectangle
rectangle.shadow = shadow
```

`style` を `OUTER` に設定すると、影が矩形の境界の外側に表示され、さりげない 3‑D 効果が得られます。`blur` や `distance` を調整して、影をより鋭くしたり、拡散させたりできます。

## PDF として保存 – ドキュメントの最終化

シェイプのスタイリングが完了したら、ドキュメントを直接 PDF として保存できます。Aspose.Words が内部で変換を行い、影効果を保持します。

```python
output_path = "output/shape_with_shadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

任意の PDF ビューアで `shape_with_shadow.pdf` を開くと、Word で見たのと同じ外側の影が付いた矩形が表示されます。

## 完全な動作例

以下は全手順を組み合わせたスクリプトです。`create_word_with_shadow.py` という名前で保存し、実行してください。

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1. Create a blank Word document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2. Insert a rectangle shape
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)

# 3. Define and apply an outer shadow
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER
shadow.blur = 5.0
shadow.distance = 3.0
shadow.color = aw.Color.black
rectangle.shadow = shadow

# 4. Save the document as PDF
pdf_path = os.path.join(output_dir, "shape_with_shadow.pdf")
doc.save(pdf_path)

print(f"PDF generated at: {pdf_path}")
```

**期待される出力**

スクリプトを実行すると確認メッセージが表示されます（例）:

```
PDF generated at: output/shape_with_shadow.pdf
```

生成された PDF を開くと、200 pt × 100 pt の矩形に柔らかい黒色の外側影が付いた 1 ページが表示されます。

## よくあるバリエーションとエッジケース

* **影の色を変更** – `aw.Color.black` を `aw.Color.red` や `aw.Color.from_argb(255, 0, 120, 215)` などの別の `aw.Color` 値に置き換えます。
* **別のシェイプを使用** – `aw.drawing.ShapeType.RECTANGLE` を `OVAL`、`DIAMOND` などサポートされている列挙値に変更します。
* **PDF ではなく DOCX で保存** – `doc.save("output/shape.docx")` とすれば Word 形式のまま保存できます。
* **複数シェイプの作成** – `builder.insert_shape` を再度呼び出して追加シェイプを作成できます。各シェイプはそれぞれ独自の `ShadowEffect` を持てます。

**プロのコツ**: シェイプを特定の位置に配置したい場合は、挿入後に `rectangle.left` と `rectangle.top` を設定してください。これによりピクセル単位で正確な配置が可能になります。

## 結論

これで **create blank Word document**、**insert shape in Word**、**add outer shadow shape**、そして **save as PDF using Python** の手順が習得できました。完全なコードサンプルはエンドツーエンドのワークフローを示しており、各 API 呼び出しが必要な理由も解説しています。

ここからは、さらに高度なスタイリングオプションを探求したり、シェイプ内にテキストを追加したり、複数シェイプを組み合わせて複雑な図を作成したりできます。影のパラメータを調整してブランドのビジュアル言語に合わせ、ドキュメント生成パイプラインに組み込んでみてください。

Happy coding!

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを基にした関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、代替実装アプローチを自分のプロジェクトに取り入れたりするのに役立ちます。

- [矩形シェイプを作成し、影を追加して PDF を保存](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Word から PDF を作成 – Aspose.Words を使用した完全な Python ガイド](/words/english/python-net/document-conversion/create-pdf-from-word-complete-python-guide-with-aspose-words/)
- [Aspose.Words で Word のシェイプに影を付ける – ステップバイステップ](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}