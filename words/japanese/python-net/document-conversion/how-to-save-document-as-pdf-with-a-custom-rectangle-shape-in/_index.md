---
category: general
date: 2026-10-07
description: Aspose.Words for Python を使用して、矩形シェイプとカスタム シャドウを追加しながら文書を PDF として保存する方法を学びます。ステップバイステップのコードが含まれています。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save document as pdf
- add rectangle shape
- export word to pdf
- set rectangle dimensions
- draw rectangle word
language: ja
lastmod: 2026-10-07
og_description: Aspose.Words for Python を使用して、カスタムの長方形シェイプで文書を PDF として保存します。描画、スタイル設定、Word
  から PDF へのエクスポートの完全な例をご覧ください。
og_image_alt: Screenshot of the generated PDF showing the rectangle shape after save
  document as pdf
og_title: 矩形シェイプで文書をPDFとして保存 – 完全なPythonガイド
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  headline: How to save document as PDF with a custom rectangle shape in Python
  type: TechArticle
- description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  name: How to save document as PDF with a custom rectangle shape in Python
  steps:
  - name: Initialize a new blank document
    text: '```python import aspose.words as aw'
  - name: Add rectangle shape to the document
    text: '```python # Create a rectangle shape and attach it to the document. rectangle
      = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)'
  - name: Set rectangle dimensions
    text: '```python # Define width and height in points (1 point = 1/72 inch). rectangle.width
      = 200 # 200 points ≈ 2.78 inches rectangle.height = 100 # 100 points ≈ 1.39
      inches ```'
  - name: (Optional) Apply a visible custom shadow
    text: '```python shadow = rectangle.shadow_format shadow.visible = True # Show
      the shadow shadow.blur = 5.0 # Softness of the shadow edge shadow.distance =
      3.0 # How far the shadow is offset shadow.angle = 45 # Direction in degrees
      shadow.color = aw.drawing.Color.black ```'
  - name: Save document as PDF
    text: '```python output_path = "output/shadow_rectangle.pdf" document.save(output_path)
      print(f"PDF saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Word automation
title: Pythonでカスタム矩形シェイプを使用して文書をPDFとして保存する方法
url: /ja/python/document-conversion/how-to-save-document-as-pdf-with-a-custom-rectangle-shape-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Pythonでカスタム矩形シェイプを使用して文書をPDFとして保存する方法

カスタムグラフィックを追加しながら **文書をPDFとして保存** したい場合、このガイドで手順を示します。空の Word ファイルを作成し、**矩形シェイプを描画**、サイズを設定し、可視の影を適用し、最後に Aspose.Words for Python ライブラリを使用して **Word を PDF にエクスポート** します。

この手順を完了すると、レポートや請求書、あらゆる文書自動化シナリオに適した、完璧に配置された矩形を含む PDF が得られます。外部ツールは不要で、Python と Aspose.Words パッケージだけで実現できます。

## 必要なもの

| 要件 | 重要な理由 |
|------|------------|
| Python 3.8+ | Aspose.Words for Python API は最新のインタプリタを対象としています。 |
| `aspose-words` パッケージ (`pip install aspose-words`) | コード例で使用される `aw` 名前空間を提供します。 |
| Python とオブジェクト指向プログラミングの基本的な知識 | チュートリアルでは `Document` や `Shape` といったオブジェクトを操作します。 |
| PDF を保存するフォルダーへの書き込み権限 | `save document as pdf` 手順でファイルを書き込みます。 |

> **プロのコツ:** 仮想環境 (`python -m venv venv`) を使用して依存関係を分離しましょう。

## 矩形シェイプ付きで文書をPDFとして保存する手順

以下は完全に実行可能なサンプルです。各ステップで **何を** 行うかだけでなく **なぜ** それを行うのかも解説します。

### 手順 1: 新しい空白ドキュメントを初期化する

```python
import aspose.words as aw

# Create an empty Word document – this is the canvas for our shape.
document = aw.Document()
```

新しい `Document` オブジェクトを作成すると、クリーンなページコレクションが得られます。後で **Word を PDF にエクスポート** したい場合は既存の *.docx* をロードすることも可能ですが、空白から始めることで例がシンプルになります。

### 手順 2: ドキュメントに矩形シェイプを追加する

```python
# Create a rectangle shape and attach it to the document.
rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

# The shape must be placed inside a paragraph before it appears.
paragraph = document.first_section.body.first_paragraph
paragraph.append_child(rectangle)
```

`add rectangle shape` ステップでは `ShapeType.RECTANGLE` を使用します。シェイプを段落に追加することで、Aspose.Words は最終的な PDF での描画位置を把握します。

### 手順 3: 矩形のサイズを設定する

```python
# Define width and height in points (1 point = 1/72 inch).
rectangle.width = 200   # 200 points ≈ 2.78 inches
rectangle.height = 100  # 100 points ≈ 1.39 inches
```

明示的に **矩形のサイズ** を設定することで、プラットフォーム間で形状の見た目が一貫します。インチ単位が好みの場合は `convert_to_inches` ヘルパーを使用することもできます。

### 手順 4: (オプション) 可視のカスタム影を適用する

```python
shadow = rectangle.shadow_format
shadow.visible = True          # Show the shadow
shadow.blur = 5.0              # Softness of the shadow edge
shadow.distance = 3.0          # How far the shadow is offset
shadow.angle = 45              # Direction in degrees
shadow.color = aw.drawing.Color.black
```

影を付けると矩形が PDF 内で際立ちます。`shadow.visible` フラグが必須で、これが無いと他のプロパティは効果を持ちません。

### 手順 5: 文書をPDFとして保存する

```python
output_path = "output/shadow_rectangle.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

`document.save` に **.pdf** 拡張子を指定して呼び出すと、Aspose.Words の組み込み PDF レンダラが自動的に **save document as pdf** を実行します。追加の変換ステップは不要で、これが **Word を PDF にエクスポート** する推奨方法です。

> **なぜこれが機能するのか:** Aspose.Words は矩形とその影を含む文書レイアウトを直接 PDF ストリームに書き込みます。プロセスはロスレスで、ベクター品質が保持されます。

## 完全なソースコード（単一スクリプト）

```python
import aspose.words as aw

def create_pdf_with_rectangle(output_path: str):
    """
    Creates a PDF that contains a single rectangle shape with a custom shadow.
    The function demonstrates:
    • add rectangle shape
    • set rectangle dimensions
    • export Word to PDF (save document as pdf)
    """
    # 1️⃣ Create a new blank document
    document = aw.Document()

    # 2️⃣ Insert a rectangle shape
    rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

    # 3️⃣ Set the shape's size
    rectangle.width = 200   # points
    rectangle.height = 100  # points

    # 4️⃣ Configure a visible shadow
    shadow = rectangle.shadow_format
    shadow.visible = True
    shadow.blur = 5.0
    shadow.distance = 3.0
    shadow.angle = 45
    shadow.color = aw.drawing.Color.black

    # 5️⃣ Add shape to the first paragraph
    paragraph = document.first_section.body.first_paragraph
    paragraph.append_child(rectangle)

    # 6️⃣ Save the document as PDF
    document.save(output_path)
    print(f"PDF successfully saved to: {output_path}")

if __name__ == "__main__":
    create_pdf_with_rectangle("output/shadow_rectangle.pdf")
```

このスクリプトを実行すると、`shadow_rectangle.pdf` が生成され、以下のようになります：

![生成された PDF の図：save document as pdf 後の矩形シェイプを示す](placeholder-image.png)

*PDF には、ドキュメントの中央に黒い影付き矩形が配置された単一ページが含まれます。*

## よくある質問とエッジケース

| 質問 | 回答 |
|------|------|
| **矩形を特定の位置に配置できますか？** | はい。保存前に `rectangle.left` と `rectangle.top`（ポイント単位）を設定してください。 |
| **複数のシェイプが必要な場合は？** | 追加の `Shape` オブジェクトを作成し、各々を設定して同じ段落または別の段落に追加します。 |
| **影は PDF のサイズに影響しますか？** | ほとんど影響しません。影はベクターメタデータとして保存され、ラスタ画像ではありません。 |
| **既存の *.docx* ファイルを変換に使用できますか？** | もちろん可能です。`aw.Document()` を `aw.Document("input.docx")` に置き換えれば、残りの手順はそのままです。 |
| **矩形の塗りつぶし色を変更できますか？** | `rectangle.fill_color = aw.drawing.Color.light_blue` のように、任意の `Color` を設定してください。 |

## 次のステップ

カスタム矩形で **文書をPDFとして保存** できるようになったので、以下を試してみてください：

* **ヘッダー、フッター、ページ番号付きで Word を PDF にエクスポート**。  
* 同じ `Shape` クラスを使って **他の描画オブジェクト**（`Ellipse`、`Polygon`）を追加。  
* フォルダー内の Word ファイルを一括処理し、各ファイルに同じ矩形オーバーレイを適用。  

これらの拡張も同じパターンに従います：シェイプを作成し、プロパティを設定し、**save document as pdf** を実行するだけです。

---

**まとめ:** 本チュートリアルでは、Aspose.Words for Python を使用して **文書をPDFとして保存** しながら **矩形シェイプを追加**、**矩形サイズを設定**、そしてカスタム影を適用する方法を示しました。完全なスクリプトはコピーして実行でき、独自の文書自動化パイプラインにすぐに組み込めます。コーディングを楽しんでください！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得したり、独自プロジェクトで代替実装アプローチを探求したりするのに役立ちます。

- [矩形シェイプを作成し、影を付けて PDF に保存](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Aspose.Words で矩形を PDF に追加 – ステップバイステップガイド](/words/english/python-net/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/)
- [Aspose.Words で文書を PDF に保存 – 完全 C# ガイド](/words/english/net/programming-with-pdfsaveoptions/save-document-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}