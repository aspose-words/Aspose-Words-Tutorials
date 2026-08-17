---
category: general
date: 2026-08-17
description: Aspose.Words for Python を使用して PNG を保存する方法。形状に影を追加し、ドキュメントを PDF として保存し、Word
  を PNG にエクスポートする方法を1つのガイドで学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save png
- add shadow to shape
- save document as pdf
- export word to png
- convert word to pdf
language: ja
lastmod: 2026-08-17
og_description: Aspose.WordsでPNGを保存する方法。このチュートリアルでは、シェイプに影を追加し、ドキュメントをPDFとして保存し、WordをPNGにエクスポートする方法を示します。
og_image_alt: Screenshot of a Word document with a rectangle shape that has a shadow,
  saved as PNG and PDF
og_title: Aspose.WordsでPNGを保存し、シェイプに影を追加する方法
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  headline: How to save PNG and add shadow to shape with Aspose.Words
  type: TechArticle
- description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  name: How to save PNG and add shadow to shape with Aspose.Words
  steps:
  - name: Pro tip
    text: If you need a sharper shadow, reduce `blur`. For a more pronounced offset,
      increase `distance`. The `Shadow` class also exposes `angle` and `transparency`
      for fine‑tuned control.
  - name: 'Optional: higher‑resolution PNG'
    text: '```python png_options = aw.image.PngSaveOptions() png_options.resolution
      = 300 # DPI doc.save("output/high_res_output.png", png_options) ```'
  - name: Expected output
    text: 'Running the script creates three files:'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Image export
title: Aspose.WordsでPNGを保存し、図形に影を追加する方法
url: /ja/python/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words で PNG を保存し、図形に影を付ける方法

Word ファイルから **PNG を保存する方法** が必要な場合、このガイドは完全で実行可能なソリューションを提供します。また、**図形に影を付ける**、**文書を PDF として保存**、そして **Word を PNG にエクスポート** する方法も確認できます。すべて Aspose.Words for Python via .NET 7 以降の環境内で完結します。

このチュートリアルでは、空の Word 文書を PDF と PNG 画像に変換し、矩形図形にシンプルな影効果を適用する手順をすべて解説します。外部ツールは不要で、コードは Aspose.Words for Python via .NET でそのまま動作します。

## 本記事で達成できること

この記事を読み終えると、以下ができるようになります。

* プログラムから新しい Word 文書を作成する。  
* 矩形図形を挿入し、影効果を設定する。  
* 同じ文書を PDF ファイルとして保存する。  
* 文書を PNG 画像としてエクスポートする。  

これらの手順は、**PNG を保存する方法** に加えて **図形に影を付ける**、**文書を PDF として保存** という一般的な要件に一括で対応します。

## 前提条件

* Python 3.9 以上  
* Aspose.Words for Python via .NET がインストール済み（`pip install aspose-words`）  
* 出力先ディレクトリへの書き込み権限  

まだ Aspose.Words をインストールしていない場合は、以下を実行してください。

```bash
pip install aspose-words
```

## Aspose.Words で PNG を保存する手順

最初のステップは、`Document` と `DocumentBuilder` を作成することです。`DocumentBuilder` は、図形やテーブル、テキストなどのコンテンツを流暢に挿入できる API を提供します。

```python
import aspose.words as aw

# Create a new blank document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` はメモリ上の Word ファイル全体を表し、`aw.DocumentBuilder` は現在の挿入位置を指します。初期位置は最初（唯一）のセクションの先頭です。

## エクスポート前に図形に影を付ける

図形は矩形、楕円、カスタムポリゴンなど任意の描画オブジェクトです。ここでは 100 × 100 ポイントの矩形を作成し、ソフトな影を適用します。

```python
# Insert a rectangle shape (100x100 points)
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

# Configure a simple shadow
shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Softness of the shadow edges
shape.shadow.distance = 3.0      # Distance from the shape
shape.shadow.color = aw.Color.black
```

なぜ保存前に影を設定するのか？ Aspose.Words は PDF と PNG のエクスポート時に影を描画するため、両方の出力形式で視覚効果が保持されます。

### プロのコツ
より鋭い影が必要な場合は `blur` を小さくします。オフセットを大きくしたい場合は `distance` を増やしてください。`Shadow` クラスは `angle` と `transparency` も公開しており、細かい調整が可能です。

## 文書を PDF として保存

コンテンツが整ったら、PDF への変換はワンライナーで完了します。`SaveFormat.PDF` 定数が Aspose.Words に変換処理を指示します。

```python
# Save the document as PDF (shadow is rendered in the output)
pdf_path = "output/output.pdf"
doc.save(pdf_path, aw.SaveFormat.PDF)
```

生成された PDF には、定義した通りの影付き矩形が含まれます。Aspose.Words はベクターグラフィックを扱うため、PDF のサイズは控えめです。

## Word を PNG にエクスポート

PNG エクスポートは各ページをラスタ画像として出力します。デフォルトは 96 DPI ですが、`PngSaveOptions` オブジェクトで DPI を上げれば高解像度の画像が得られます。

```python
# Export the same document as PNG
png_path = "output/output.png"
doc.save(png_path, aw.SaveFormat.PNG)
```

**Word を PNG にエクスポート** すると、各ページが個別の PNG ファイルとして保存されます。サンプル文書は 1 ページだけなので、1 つの PNG ファイルが生成されます。

### オプション: 高解像度 PNG

```python
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI
doc.save("output/high_res_output.png", png_options)
```

高 DPI は印刷用途や高品質サムネイルが必要な場合に有用です。

## 完全スクリプト – コピーして貼り付け、実行するだけ

以下は、上記手順をすべて実装した完全なスタンドアロン スクリプトです。`generate_assets.py` として保存し、コマンドラインから実行してください。

```python
import os
import aspose.words as aw

# ------------------------------------------------------------------
# 1. Prepare output folder
# ------------------------------------------------------------------
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# ------------------------------------------------------------------
# 2. Create a new blank document and a builder
# ------------------------------------------------------------------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ------------------------------------------------------------------
# 3. Insert a rectangle shape and add a shadow
# ------------------------------------------------------------------
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Soft edges
shape.shadow.distance = 3.0      # Offset from shape
shape.shadow.color = aw.Color.black

# ------------------------------------------------------------------
# 4. Save as PDF (demonstrates "save document as pdf")
# ------------------------------------------------------------------
pdf_path = os.path.join(output_dir, "output.pdf")
doc.save(pdf_path, aw.SaveFormat.PDF)

# ------------------------------------------------------------------
# 5. Export as PNG (demonstrates "how to save png")
# ------------------------------------------------------------------
png_path = os.path.join(output_dir, "output.png")
doc.save(png_path, aw.SaveFormat.PNG)

# ------------------------------------------------------------------
# 6. Optional high‑resolution PNG (demonstrates "export word to png")
# ------------------------------------------------------------------
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI for sharper output
high_res_png_path = os.path.join(output_dir, "high_res_output.png")
doc.save(high_res_png_path, png_options)

print(f"Files written to {os.path.abspath(output_dir)}")
```

### 期待される出力

スクリプトを実行すると次の 3 ファイルが作成されます。

* `output/output.pdf` – 矩形に黒い影が付いた PDF  
* `output/output.png` – 同ページの 96 DPI PNG レンダリング  
* `output/high_res_output.png` – 300 DPI の高品質 PNG  

好きなビューアでファイルを開き、影が期待通りに表示されていることを確認してください。

## よくある質問とエッジケース

**出力ディレクトリが存在しない場合はどうなる？**  
スクリプトは `os.makedirs(output_dir, exist_ok=True)` を呼び出すため、フォルダが自動的に作成されます。これにより保存時の `FileNotFoundError` を防げます。

**異なる影を持つ複数の図形を追加できるか？**  
可能です。追加の `Shape` オブジェクトを作成し、各 `shadow` プロパティを個別に設定してから `builder.insert_node(shape)` で挿入すれば OK です。

**他のラスタ形式（例: JPEG）に変換した場合でも影は保持されるか？**  
Aspose.Words は `SaveFormat` がサポートするすべてのラスタ形式で影を描画します。`aw.SaveFormat.PNG` を `aw.SaveFormat.JPEG` に置き換えても影は表示されます。

**「convert word to pdf」とは何が違うのか？**  
`convert word to pdf` はステップ 4 で実行する操作と本質的に同じです。`doc.save` に `SaveFormat.PDF` を指定するだけで内部的に変換が行われ、レイアウトやフォント、影などのグラフィックが保持されます。

**図形サイズに制限はあるか？**  
図形はポイント単位（1 pt ≈ 1/72 インチ）で測定されます。非常に大きなサイズはファイルサイズ増加につながりますが、Aspose.Words にハードリミットはありません。`aw.Shape` 作成時の `width` と `height` を調整してレイアウトに合わせてください。

## 結論

これで **Word 文書から PNG を保存する方法** と同時に **図形に影を付ける**、**文書を PDF として保存**、**Word を PNG にエクスポート** する手順がマスターできました。完全なスクリプトは、より大きな文書や複数ページ、複雑なグラフィック効果へ拡張できるクリーンで再利用可能なパターンを示しています。

次のステップとしては以下が考えられます。

* 他の `ShapeType`（楕円、雲形など）を試す  
* Using `

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、独自プロジェクトで代替実装を検討したりするのに役立ちます。

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [How to Convert DOCX to PNG in Java – Aspose.Words](/words/english/java/document-converting/converting-documents-images/)
- [Save Word Documents as PostScript in Python Using Aspose.Words: A Comprehensive Guide](/words/english/python-net/document-operations/save-docs-as-postscript-using-aspose-words-python/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}