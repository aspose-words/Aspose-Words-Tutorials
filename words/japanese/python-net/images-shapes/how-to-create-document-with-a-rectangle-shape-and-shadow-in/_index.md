---
category: general
date: 2026-10-04
description: Pythonでドキュメントを作成し、Aspose.Wordsを使用して図形に影を追加する方法。影の色設定、長方形図形の挿入、外側の影のカスタマイズを学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create document
- add shadow to shape
- set shadow color
- insert rectangle shape
- how to add shadow
language: ja
lastmod: 2026-10-04
og_description: Pythonでドキュメントを作成し、図形に影を追加する方法。このガイドでは、影の色を設定し、長方形の図形を挿入し、Aspose.Wordsを使用して外側の影を適用する手順を示します。
og_image_alt: Python code inserting a rectangle shape with a visible shadow into a
  Word document
og_title: Pythonで矩形シェイプと影付きのドキュメントを作成する方法
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  headline: How to create document with a rectangle shape and shadow in Python
  type: TechArticle
- description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  name: How to create document with a rectangle shape and shadow in Python
  steps:
  - name: Why does the shadow sometimes appear invisible?
    text: The shadow is only rendered if `shadow.visible` is set to `True` **and**
      the shape’s `wrap_type` allows it to be displayed. An inline shape works reliably;
      floating shapes may require additional layout adjustments.
  - name: How can I change the shadow color to match a brand palette?
    text: 'Replace `aw.drawing.Color.black` with a custom RGB value:'
  - name: What if I need the shape to appear behind text?
    text: Set the wrap type to `WrapType.BEHIND` and adjust the `z_order_position`
      if necessary. Keep in mind that some viewers may render behind‑text shapes differently.
  - name: Can I apply the same shadow settings to multiple shapes?
    text: Yes. Create a helper function that configures the shadow and call it for
      each shape you insert. This promotes code reuse and ensures consistent styling.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Pythonで矩形シェイプと影付きのドキュメントを作成する方法
url: /ja/python/images-shapes/how-to-create-document-with-a-rectangle-shape-and-shadow-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Pythonで矩形シェイプと影付きドキュメントを作成する方法

スタイル付きの矩形を含む **ドキュメントの作成方法** が必要な方へ。本ガイドでは、Aspose.Words for Python を使用して **シェイプに影を追加** し、影の色、オフセット、ぼかしを制御する完全なソリューションを提供します。チュートリアルの最後までに、洗練された外観の `.docx` ファイルを生成できるようになります。

以下の手順では、ライブラリのインストールから影の外観のカスタマイズまでを網羅しています。外部ドキュメントは不要で、コードはそのままコピーして実行し、プロジェクトに適用できます。また、**矩形シェイプの挿入**、**外側の影スタイルの選択**、影が見えない、ラップ設定が正しくないといった一般的な落とし穴への対処方法も学べます。

## 前提条件

開始する前に、以下を確認してください。

* Python 3.8 以上がインストールされていること。
* 有効な Aspose.Words for Python ライセンス（または無料評価キー）。
* Python スクリプトの基本的な知識。
* 生成されたドキュメントを保存できるファイルシステム上の場所へのアクセス権。

pip で SDK をインストールできます:

```bash
pip install aspose-words
```

## 手順 1: ライブラリをインポートし、新しい空白ドキュメントを作成

新しいドキュメントの作成は、Word 自動化シナリオの最初のアクションです。`aw.Document()` コンストラクタは、テキスト、画像、シェイプを自由に追加できる空のファイルを提供します。

```python
import aspose.words as aw

# Create a new blank document
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

`DocumentBuilder` オブジェクトはコンテンツの挿入を簡素化します。現在のカーソル位置を追跡し、セクションを手動で管理せずに要素を順次追加できます。

## 手順 2: 必要なサイズの矩形シェイプを挿入

矩形シェイプは視覚要素のコンテナとして機能します。幅と高さはポイント単位で指定できます（1 pt ≈ 1/72 in）。

```python
# Insert a rectangle shape that is 150 pt wide and 80 pt tall
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

この時点ではシェイプに視覚的なスタイルが付いていないため、単なる輪郭として表示されます。次の手順で深みと色を付けます。

## 手順 3: シェイプをテキストにインラインで流すよう設定

シェイプが **インライン** の場合、段落内の文字として振る舞います。これにより、矩形が文書レイアウト内で期待通りの位置に留まります。

```python
# Make the shape inline so it follows the text flow
rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE
```

テキストの上にシェイプを浮かせたい場合は `WrapType.SQUARE` や `WrapType.TOP_BOTTOM` を使用できますが、ほとんどのレポートではインラインシェイプの方がレイアウトを予測しやすくなります。

## 手順 4: 影を表示させ、色を選択

影が見えなければ視覚的な効果はありません。`visible` フラグで効果を有効にし、`color` プロパティで色相を決定します。黒はクラシックで控えめな深みを提供します。

```python
# Enable the shadow and set its color to black
rectangle_shape.shadow.visible = True
rectangle_shape.shadow.color = aw.drawing.Color.black
```

`aw.drawing.Color.black` の代わりに `aw.drawing.Color.gray` やカスタム RGB 値（例: `aw.drawing.Color.from_argb(255, 128, 128, 128)`）を使用できます。

## 手順 5: 影のオフセットとぼかしを設定して深みを付与

オフセットは影がシェイプからどれだけ離れるかを制御し、ぼかし半径はエッジを柔らかくします。小さい値はくっきりした影、大きい値は柔らかい印象になります。

```python
# Horizontal and vertical offset of 5 pt each
rectangle_shape.shadow.offset_x = 5
rectangle_shape.shadow.offset_y = 5

# Blur radius of 3 pt for a gentle feather
rectangle_shape.shadow.blur = 3
```

デザインガイドラインに合わせて数値を調整してください。重いドロップシャドウが必要な場合は、オフセットとぼかしの両方を増やすと良いでしょう。

## 手順 6: 外側の影スタイルを選択

Aspose.Words には `INNER`、`OUTER`、`PERSPECTIVE` など複数の影スタイルがあります。**外側** スタイルはシェイプの境界の外側に影を配置し、すっきりとしたプロフェッショナルな外観を実現します。

```python
# Apply an outer shadow style
rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

よりドラマチックな効果が欲しい場合は `ShadowStyle.PERSPECTIVE` を試してください。三次元的な傾きが加わります。

## 手順 7: 影付きシェイプを保存

保存によりファイルが確定し、すべての書式設定がディスクに書き込まれます。書き込み権限のあるディレクトリを選び、説明的なファイル名を付けましょう。

```python
# Save the document to the desired location
output_path = "output/ShapeWithShadow.docx"
document.save(output_path)
print(f"Document saved to {output_path}")
```

スクリプトを実行すると、矩形に可視化されたカラー影が付いた Word ファイルが生成されます。Microsoft Word または LibreOffice で開き、結果を確認してください。

## 完全な実行可能サンプル

以下は、ここまで説明したすべての手順を組み込んだ完全なスクリプトです。`create_shadowed_shape.py` という名前で保存し、`python create_shadowed_shape.py` で実行してください。

```python
import aspose.words as aw
import os

def main():
    # Ensure the output directory exists
    output_dir = "output"
    os.makedirs(output_dir, exist_ok=True)

    # Step 1: Create a new blank document
    document = aw.Document()
    builder = aw.DocumentBuilder(document)

    # Step 2: Insert a rectangle shape of the desired size
    rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

    # Step 3: Set the shape to be inline with the text flow
    rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE

    # Step 4: Make the shadow visible and choose its color
    rectangle_shape.shadow.visible = True
    rectangle_shape.shadow.color = aw.drawing.Color.black

    # Step 5: Define the shadow's offset and blur to give it depth
    rectangle_shape.shadow.offset_x = 5   # horizontal offset in points
    rectangle_shape.shadow.offset_y = 5   # vertical offset in points
    rectangle_shape.shadow.blur = 3       # blur radius in points

    # Step 6: Choose an outer shadow style
    rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER

    # Step 7: Save the document with the shaped shadow
    output_path = os.path.join(output_dir, "ShapeWithShadow.docx")
    document.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    main()
```

**期待される出力**

`ShapeWithShadow.docx` を開くと、ページ中央に単一の矩形が表示されます。矩形の右下に微妙な黒い影がオフセットされ、少しぼかされて深みが出ています。影は外側スタイルなので、矩形内部には交差しません。

## よくある質問とエッジケース

### なぜ影が時々見えなくなるのですか？

影は `shadow.visible` が `True` に設定され、かつシェイプの `wrap_type` が表示を許可している場合にのみ描画されます。インラインシェイプは信頼性が高く、浮動シェイプは追加のレイアウト調整が必要になることがあります。

### ブランドカラーに合わせて影の色を変更するには？

`aw.drawing.Color.black` をカスタム RGB 値に置き換えます。

```python
rectangle_shape.shadow.color = aw.drawing.Color.from_argb(255, 0, 120, 215)  # corporate blue
```

### シェイプをテキストの背後に表示したい場合は？

`WrapType.BEHIND` に設定し、必要に応じて `z_order_position` を調整します。ただし、一部のビューアでは背後テキストシェイプの描画が異なる場合があります。

### 複数のシェイプに同じ影設定を適用できますか？

はい。影を設定するヘルパー関数を作成し、挿入する各シェイプで呼び出すことで、コードの再利用とスタイルの一貫性が保てます。

```python
def apply_shadow(shape, color=aw.drawing.Color.black, offset=5, blur=3):
    shape.shadow.visible = True
    shape.shadow.color = color
    shape.shadow.offset_x = offset
    shape.shadow.offset_y = offset
    shape.shadow.blur = blur
    shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

## 結論

これで、Aspose.Words for Python を使用して矩形シェイプとカスタマイズされた影を含む **ドキュメントの作成方法** がマスターできました。チュートリアルでは、矩形の挿入、インライン設定、影の有効化、色・オフセット・ぼかし・スタイルの設定、そしてファイルの保存までを網羅しました。

ここからは、**シェイプへの影の追加**、データに基づく **影の色設定**、画像やテキストボックスへの **影の追加** など、関連トピックを探求できます。ブランドガイドラインやデザインシステムに合わせて、サイズ、色、影スタイルを自由に実験してください。

Word ドキュメントの自動化をさらに進めたいですか？ テーブル、ヘッダー、動的コンテンツの追加に挑戦してみましょう—各ステップは本ガイドで示した原則に基づいています。コーディングを楽しんでください！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには、ステップバイステップの解説と完全なコード例が含まれており、API の追加機能を習得したり、プロジェクトで代替実装アプローチを検討したりするのに役立ちます。

- [矩形シェイプを作成し、影を追加して PDF として保存](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [影付き矩形シェイプで空白の Word 文書を作成 – ステップバイステップガイド](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words for Pythonで文書変数を管理する方法：完全ガイド](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}