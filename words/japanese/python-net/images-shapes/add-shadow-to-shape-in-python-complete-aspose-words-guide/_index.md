---
category: general
date: 2026-08-11
description: Aspose.Words for Python を使用して図形に影を追加します。図形に影を付ける方法、ぼかしを適用する方法、オフセットと色をカスタマイズする方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- add shape shadow
- apply blur to shape
- Aspose.Words shadow effect
- Python Word shape styling
language: ja
lastmod: 2026-08-11
og_description: Aspose.Words for Python を使用して図形に影を追加します。このガイドでは、図形にぼかしを適用し、オフセットを設定し、影の色を選択する方法を数行のコードで示します。
og_image_alt: Word document screenshot showing a shape with a black shadow applied
og_title: Pythonで図形に影を追加する – ステップバイステップ Aspose.Words チュートリアル
schemas:
- author: Aspose
  dateModified: '2026-08-11'
  description: Add shadow to shape using Aspose.Words for Python. Learn how to add
    shape shadow, apply blur to shape, and customize offset and color.
  headline: Add shadow to shape in Python – complete Aspose.Words guide
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python. Learn how to add
    shape shadow, apply blur to shape, and customize offset and color.
  name: Add shadow to shape in Python – complete Aspose.Words guide
  steps:
  - name: Adding shadow to a specific shape by name
    text: 'If your document contains several shapes, you may want to target one by
      its `name` property:'
  - name: Skipping non‑visual nodes
    text: Sometimes a shape node can be a placeholder (e.g., a drawing canvas without
      visual content). Guard against this by checking `shape.is_image` or `shape.is_picture_frame`
      before applying the shadow.
  - name: Working with grouped shapes
    text: When shapes are grouped, the group itself is a `Shape` node. To apply a
      shadow to each member, iterate through `shape.get_child_nodes(aw.NodeType.SHAPE,
      True)`.
  - name: What’s next?
    text: '- Explore **apply blur to shape** for other effects like glow or soft edges.
      - Combine shadows with **shape borders** or **reflection** to create richer
      graphics. - Convert the edited document to PDF (`doc.save("output.pdf", aw.SaveFormat.PDF)`)
      for distribution.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Pythonで図形に影を追加する – 完全なAspose.Wordsガイド
url: /ja/python/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python でシェイプに影を追加 – 完全な Aspose.Words ガイド

Word 文書に **シェイプに影を追加** したい場合、このチュートリアルでは Aspose.Words for Python を使った具体的な手順を示します。レポートジェネレータやドキュメントテンプレートサービスを構築している方は、シェイプの影を追加し、ぼかしを適用し、数行のコードで影の外観を微調整する方法を学べます。

本ガイドでは、必要なインポート、対象シェイプの取得（入れ子ノードを含む）、影のプロパティ設定、一般的なエッジケースの処理、そして変更後の文書の保存までを網羅しています。最後まで読めば、.docx ファイルを扱う任意の Python プロジェクトにすぐ組み込める再利用可能なスニペットが手に入ります。

## 前提条件

開始する前に、以下が揃っていることを確認してください。

- **Python 3.8+** がインストール済み
- **Aspose.Words for Python via .NET**（`pip install aspose-words` でインストール）
- 少なくとも 1 つのシェイプ（矩形、画像、SmartArt など）を含む Word 文書（`input.docx`）
- Python と Aspose.Words オブジェクトモデルの基本的な知識

## 手順 1: Aspose.Words をインポートし、文書を開く

まず `aspose.words` パッケージ（一般的に `aw` とエイリアス）をインポートし、ソース文書をロードします。

```python
import aspose.words as aw

# Load the Word document from the file system
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)
```

*Why this matters*: 文書を開くことで、シェイプが存在するノードツリーにアクセスできます。`aw.Document` クラスは以降のすべての操作のエントリーポイントです。

## 手順 2: 最初のシェイプを取得（入れ子ノードを含む）

シェイプは `Paragraph` の直接子である場合もあれば、テーブルや他のコンテナの内部に入れ子になっている場合もあります。`get_child` に `is_deep=True` を指定すれば、入れ子の深さに関係なく最初のシェイプを取得できます。

```python
# Retrieve the first shape in the document, searching recursively
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

if shape is None:
    raise ValueError("No shape found in the document. Add a shape before applying a shadow.")
```

*Why this matters*: `add shape shadow` 操作には `Shape` オブジェクトが必要です。深い検索を行うことで、テーブルやグループコンテナ内に隠れたシェイプを見逃すことが防げます。

## 手順 3: 影を有効化し、基本プロパティを設定

Aspose.Words では影は複数のプロパティで表現されます。まず `shadow_visible` を `True` に設定して影をオンにします。

```python
# Enable the shadow effect
shape.shadow_visible = True
```

これでぼかし半径、オフセット、カラーを設定できるようになります。

## 手順 4: シェイプにぼかしを適用し、オフセット値を定義

ぼかし半径は影の柔らかさを決めます。`5.0` の値は目立ちすぎず、適度なぼかしを提供します。オフセットは影を水平方向・垂直方向に移動させます。

```python
# Apply blur to shape – this is the "apply blur to shape" part
shape.shadow_blur = 5.0          # Blur radius in points

# Define horizontal (X) and vertical (Y) offsets
shape.shadow_offset_x = 2.0     # Move shadow 2 points to the right
shape.shadow_offset_y = 2.0     # Move shadow 2 points down
```

*Why this matters*: `shadow_blur` とオフセット値を調整することで、文書のビジュアルスタイルに合ったリアルな奥行き効果を作り出せます。

## 手順 5: 影の色を選択（カスタムカラーでシェイプに影を追加）

任意の `aw.Color` を使用できます。ここでは黒を選択していますが、`aw.Color.red` や `aw.Color.from_argb(255, 0, 120, 215)` などに置き換えても構いません。

```python
# Set the shadow color – black in this example
shape.shadow_color = aw.Color.black
```

*Why this matters*: 色は影が周囲のコンテンツとどのように相互作用するかを決めます。明るい背景では濃い影が目立ち、暗いページでは薄い影の方が見やすくなります。

## 手順 6: 更新した文書を保存

最後に変更をディスクに書き込みます。元のファイルを上書きするか、新しいファイルとして保存できます。

```python
output_path = "YOUR_DIRECTORY/output_with_shadow.docx"
doc.save(output_path)

print(f"Shadow applied successfully. Saved to {output_path}")
```

`output_with_shadow.docx` を Microsoft Word で開くと、最初のシェイプに指定したぼかしとオフセットが適用されたソフトな黒い影が表示されます。

## 完全な実行可能サンプル

すべてをまとめた、すぐに実行できるスクリプトは以下の通りです。

```python
import aspose.words as aw

def add_shadow_to_first_shape(input_path: str, output_path: str,
                              blur: float = 5.0,
                              offset_x: float = 2.0,
                              offset_y: float = 2.0,
                              color: aw.Color = aw.Color.black) -> None:
    """
    Loads a Word document, finds the first shape (deep search),
    and applies a shadow effect.

    Parameters
    ----------
    input_path : str
        Path to the source .docx file.
    output_path : str
        Path where the modified document will be saved.
    blur : float, optional
        Blur radius for the shadow. Default is 5.0 points.
    offset_x : float, optional
        Horizontal offset of the shadow. Default is 2.0 points.
    offset_y : float, optional
        Vertical offset of the shadow. Default is 2.0 points.
    color : aw.Color, optional
        Shadow color. Default is black.
    """
    # Load the document
    doc = aw.Document(input_path)

    # Retrieve the first shape, searching recursively
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

    if shape is None:
        raise ValueError("No shape found in the document. Insert a shape before calling this function.")

    # Enable shadow and configure its appearance
    shape.shadow_visible = True
    shape.shadow_blur = blur
    shape.shadow_offset_x = offset_x
    shape.shadow_offset_y = offset_y
    shape.shadow_color = color

    # Save the result
    doc.save(output_path)

if __name__ == "__main__":
    INPUT_DOC = "YOUR_DIRECTORY/input.docx"
    OUTPUT_DOC = "YOUR_DIRECTORY/output_with_shadow.docx"
    add_shadow_to_first_shape(INPUT_DOC, OUTPUT_DOC)
```

**Expected output**: `output_with_shadow.docx` を開くと、最初のシェイプに水平・垂直それぞれ 2 pt のオフセットとぼかしが適用された控えめな黒い影が表示され、指定したパラメータ通りになっていることが確認できます。

## 複数シェイプとエッジケースの処理

### 名前で特定シェイプに影を追加

文書に複数のシェイプがある場合、`name` プロパティで対象を指定できます。

```python
target_name = "MyRectangle"
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)  # start with first shape
while shape is not None and shape.name != target_name:
    shape = shape.next_sibling(aw.NodeType.SHAPE)

if shape is None:
    raise ValueError(f"Shape named '{target_name}' not found.")
```

### 非表示ノードをスキップ

シェイプノードがプレースホルダー（例: 描画キャンバスだが実体がない）であることがあります。影を適用する前に `shape.is_image` や `shape.is_picture_frame` をチェックしてガードしましょう。

```python
if not shape.is_image and not shape.is_picture_frame:
    # Proceed only if the shape can display a shadow
    shape.shadow_visible = True
```

### グループ化されたシェイプの扱い

シェイプがグループ化されている場合、グループ自体も `Shape` ノードです。各メンバーに影を付けるには `shape.get_child_nodes(aw.NodeType.SHAPE, True)` を使ってイテレートします。

```python
if shape.is_group:
    for child in shape.get_child_nodes(aw.NodeType.SHAPE, True):
        child.shadow_visible = True
        child.shadow_blur = blur
        child.shadow_offset_x = offset_x
        child.shadow_offset_y = offset_y
        child.shadow_color = color
```

これらのバリエーションにより、さまざまな文書レイアウトでもコードが堅牢に動作します。

## 完璧な影を作るプロのコツ

- **一貫性**: レポート内のすべてのシェイプで同じぼかし半径とオフセットを使用し、ビジュアル言語を統一します。
- **パフォーマンス**: 高解像度画像が多数ある場合、影を付けるとファイルサイズが増加します。後で PDF へ変換する予定がある場合は出力サイズをテストしてください。
- **カラーコントラスト**: ダークページの場合は、`aw.Color.gray` などの明るめの影を検討し、視認性を保ちます。
- **プレビュー**: Word の「影」UI は Aspose.Words のプロパティと同一なので、手動で試行し、得られた値をスクリプトにコピーペーストすると便利です。

## 結論

これで Aspose.Words for Python を使って Word 文書のシェイプに **影を追加** する方法が分かりました。シェイプの取得、影の有効化、**add shape shadow** としてカスタムぼかし・オフセット・カラーを設定し、結果を保存するまでを網羅しました。上記の再利用可能関数を組み込めば、任意のドキュメント生成パイプラインに簡単にこの効果を追加できます。

### 次にやること

- **apply blur to shape** を活用して、グローやソフトエッジなど他の効果を試す
- 影と **shape borders** や **reflection** を組み合わせ、よりリッチなグラフィックを作成
- 編集した文書を PDF に変換（`doc.save("output.pdf", aw.SaveFormat.PDF)`）して配布

さまざまなカラー、ぼかしレベル、オフセット値を試して、ブランドガイドラインに合わせてください。コーディングを楽しんでください！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを基にした関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、代替実装アプローチを自分のプロジェクトで試したりするのに役立ちます。

- [Aspose.Words Shape Shadow Tutorial – C# で Word シェイプに影を追加](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Aspose.Words で Word に矩形シェイプを作成 – ステップバイステップガイド](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words for .NET を使用して Word 文書にグループシェイプを作成](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}