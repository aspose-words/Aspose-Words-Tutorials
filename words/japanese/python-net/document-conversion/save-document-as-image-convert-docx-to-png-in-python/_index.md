---
category: general
date: 2026-08-17
description: Aspose.Words for Python を使用して文書を画像として保存し、すべてのページを PNG 形式でエクスポートします。1
  つのコマンドで DOCX を PNG に変換する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save document as image
- convert docx to png
- export docx to png
- export all pages png
- export word pages image
language: ja
lastmod: 2026-08-17
og_description: Aspose.Words for Python を使用して、ドキュメントを画像として保存し、すべてのページを PNG にエクスポートします。このガイドでは、DOCX
  を PNG に効率的に変換する方法を示します。
og_image_alt: Diagram showing a multi‑page Word document converted into a single PNG
  grid preview
og_title: Pythonでドキュメントを画像として保存し、DOCXをPNGに変換する
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: Save document as image and export all pages PNG using Aspose.Words
    for Python. Learn to convert DOCX to PNG with a single command.
  headline: 'Save document as image: convert DOCX to PNG in Python'
  type: TechArticle
- description: Save document as image and export all pages PNG using Aspose.Words
    for Python. Learn to convert DOCX to PNG with a single command.
  name: 'Save document as image: convert DOCX to PNG in Python'
  steps:
  - name: '**Save format** – PNG is lossless and widely supported.'
    text: '**Save format** – PNG is lossless and widely supported.'
  - name: '**Page set** – defines the range of pages to export; using `0, document.page_count`
      captures every page.'
    text: '**Page set** – defines the range of pages to export; using `0, document.page_count`
      captures every page.'
  - name: '**Layout** – `GRID` arranges all exported pages into a single image, which
      is ideal for preview scenarios.'
    text: '**Layout** – `GRID` arranges all exported pages into a single image, which
      is ideal for preview scenarios.'
  type: HowTo
tags:
- Aspose.Words
- Python
- DOCX
title: 'ドキュメントを画像として保存: PythonでDOCXをPNGに変換'
url: /ja/python/document-conversion/save-document-as-image-convert-docx-to-png-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ドキュメントを画像として保存: PythonでDOCXをPNGに変換

ドキュメントを **画像として保存** し、複数ページの Word ファイルのプレビューを 1 枚にまとめたい場合は、この記事で Aspose.Words for Python を使った手順をご紹介します。また、 **DOCX を PNG に変換** する方法もシンプルに学べます。

Word 文書の各ページを PNG にエクスポートする処理を自前でループを書いて行うのは手間がかかります。Aspose.Words には **すべてのページを PNG にエクスポート** できる組み込みオプションがあり、レイアウト・解像度・ページ範囲を自由に設定できます。このチュートリアルの最後までに、ソース文書の全ページをグリッド形式の PNG に変換する、すぐに実行可能なスクリプトが完成します。

## 前提条件

開始する前に以下を確認してください。

* Python 3.8 以上がインストールされていること。
* `aspose-words` パッケージ（`pip install aspose-words`）がインストール済み。
* 2 ページ以上ある Word ファイル（`.docx`）。
* 生成した PNG を保存したいディレクトリへの書き込み権限。

追加の外部ツールは不要です。Aspose.Words がメモリ上だけで変換を完結させます。

## 手順 1: Word 文書をロードする

最初のステップは、ソース DOCX ファイルを表す `aw.Document` オブジェクトを作成することです。このオブジェクトを通じて文書内のすべてのページ、セクション、リソースにアクセスできます。

```python
import aspose.words as aw

# Load the multi‑page Word document
doc_path = "YOUR_DIRECTORY/multi_page.docx"
document = aw.Document(doc_path)
```

*このステップが重要な理由*: 文書を一度ロードすれば、Aspose.Words が後で任意の画像形式にレンダリングできる完全なオブジェクトモデルが手に入ります。`aw.Document` クラスはファイルの整合性も検証するため、DOCX が破損している場合は早期にエラーが返ります。

## 手順 2: PNG 保存オプションを作成し設定する

Aspose.Words では `ImageSaveOptions` を使って文書のラスタライズ方法を制御します。このステップでは次の 3 つの重要プロパティを設定します。

1. **保存形式** – PNG はロスレスで広くサポートされています。
2. **ページセット** – エクスポートするページ範囲を指定します。`0, document.page_count` とすれば全ページが対象になります。
3. **レイアウト** – `GRID` はエクスポートしたすべてのページを 1 枚の画像に配置し、プレビュー用途に最適です。

```python
# Configure PNG export options
png_options = aw.saving.ImageSaveOptions(aw.SaveFormat.PNG)

# Export all pages (page index starts at 0)
png_options.page_set = aw.saving.PageSet(0, document.page_count)

# Arrange pages in a grid layout (rows × columns are auto‑calculated)
png_options.layout = aw.saving.ImageSaveOptions.PageLayout.GRID

# Optional: increase resolution for sharper output (default is 96 DPI)
png_options.resolution = 150  # DPI
```

*このステップが重要な理由*: `page_set` を全範囲に設定すれば、ページを手動で走査せずに **docx を png にエクスポート** できます。`GRID` レイアウトはページを横並びにした単一画像を生成し、**Word ページを画像としてエクスポート** する要件をコンパクトに満たします。`resolution` を調整すれば、細かいディテールが含まれる文書でも高品質に出力できます。

## 手順 3: 文書を単一 PNG プレビューとして保存する

オプションが整ったら、保存はワンライナーで完了します。Aspose.Words が上記設定に従って PNG ファイルを書き出します。

```python
# Destination path for the combined PNG image
output_path = "YOUR_DIRECTORY/preview.png"

# Perform the export – this creates one PNG that contains all pages
document.save(output_path, png_options)
print(f"Document successfully saved as image: {output_path}")
```

**期待される出力**

スクリプトを実行すると `preview.png` が生成されます。元の DOCX が 3 ページの場合、PNG はそれら 3 ページをグリッド状（例: 2 × 2 で最後のセルは空）にタイル表示します。任意の画像ビューアで開けば、すべてのページが正しくラスタライズされていることが確認できます。

### プロのコツ

特定のページだけが必要な場合は、`PageSet` の引数を変更します。例:

```python
# Export pages 2‑4 only (zero‑based index)
png_options.page_set = aw.saving.PageSet(1, 4)
```

この書き方でも **すべてのページを PNG にエクスポート** するロジックは保持され、対象範囲だけを処理することで大容量文書のメモリ使用量を削減できます。

## 大容量文書とメモリ制約への対処

ページ数が数十〜数百に及ぶ文書を扱うと、生成される PNG が非常に大きくなることがあります。以下の対策を検討してください。

* **必要なときだけ `resolution` を上げる** – DPI を上げるとファイルサイズが増大します。
* **`PageLayout.SINGLE_COLUMN` を使用** – グリッドではなく縦方向のストリップになるため、スクロールが楽になります。
* **出力をストリーム化** – 画像をディスクに書き込まずネットワーク経由で送信したい場合は、Aspose.Words が `BytesIO` ストリームへの保存もサポートしています。

```python
import io

stream = io.BytesIO()
document.save(stream, png_options)
# Now `stream.getvalue()` holds the PNG bytes
```

## すぐにコピー＆ペーストできる完全スクリプト

以下に、これまで説明したすべての手順を組み込んだ実行可能なサンプルを示します。`YOUR_DIRECTORY` を実際のフォルダー パスに置き換えてください。

```python
import aspose.words as aw

# ----------------------------------------------------------------------
# 1. Load the source DOCX file
# ----------------------------------------------------------------------
doc_path = "YOUR_DIRECTORY/multi_page.docx"
document = aw.Document(doc_path)

# ----------------------------------------------------------------------
# 2. Configure PNG export options (save document as image)
# ----------------------------------------------------------------------
png_options = aw.saving.ImageSaveOptions(aw.SaveFormat.PNG)

# Export every page (export docx to png)
png_options.page_set = aw.saving.PageSet(0, document.page_count)

# Arrange pages in a grid (export word pages image)
png_options.layout = aw.saving.ImageSaveOptions.PageLayout.GRID

# Optional: higher DPI for sharper output
png_options.resolution = 150

# ----------------------------------------------------------------------
# 3. Save the combined PNG file
# ----------------------------------------------------------------------
output_path = "YOUR_DIRECTORY/preview.png"
document.save(output_path, png_options)

print(f"Document successfully saved as image: {output_path}")
```

このスクリプトを走らせると、`multi_page.docx` の全ページを含む単一 PNG が生成されます。テーブル、画像、複雑なレイアウトを含む任意の DOCX ファイルでも同様に動作します。

## 結論

これで **ドキュメントを画像として保存**、**DOCX を PNG に変換**、そして **すべてのページを PNG にエクスポート** する方法がマスターできました。`ImageSaveOptions` を活用すれば手動ループを回避し、グリッド形式のプレビューを簡単に作成でき、解像度やレイアウトも自由にコントロールできます。

次に試してみると良い項目:

* 他のラスタ形式（JPEG、BMP）へのエクスポート – `SaveFormat` を変更するだけです。
* エクスポート前に透かしや注釈を追加 – `Document` オブジェクトを操作します。
* このスクリプトを Web サービスに組み込み、オンデマンドでプレビューを生成。

`layout` や `resolution` の値をいろいろ試して、アプリケーションのパフォーマンスと品質のバランスを最適化してください。コーディングを楽しんでください！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれているので、API の追加機能を習得したり、別の実装アプローチを自分のプロジェクトに取り入れたりするのに役立ちます。

- [Optimize RTF Image Handling in Python using Aspose.Words API: Save as WMF and Ensure Compatibility](/words/english/python-net/images-shapes/optimize-rtf-image-handling-aspose-words-python/)
- [Convert DOCX to Fixed-Form XAML in Python Using Aspose.Words: A Comprehensive Guide](/words/english/python-net/document-operations/python-docx-to-xaml-aspose-tutorial/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}