---
category: general
date: 2026-09-30
description: Aspose.Words for Python を使用して、長方形の図形を作成し、図形に影を適用し、図形付きの Word を保存する方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- how to add shape
- apply shadow to shape
- set shadow blur
- save word with shape
language: ja
lastmod: 2026-09-30
og_description: Word文書に矩形の図形をすばやく作成します。このチュートリアルでは、図形の追加、図形への影の適用、影のぼかし設定、そして図形付きのWordを保存する方法を示します。
og_image_alt: Screenshot of a Word document showing a rectangle shape with a soft
  shadow
og_title: PythonでWordに長方形を作成する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Learn how to create rectangle shape, apply shadow to shape, and save
    Word with shape using Aspose.Words for Python.
  headline: How to create rectangle shape in a Word document using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- Shapes
title: PythonでWord文書に長方形の図形を作成する方法
url: /ja/python/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python を使用して Word 文書に長方形シェイプを作成する方法

Word ファイルに **長方形シェイプを作成** したい場合、このガイドでは完全に実行可能なソリューションを示します。シェイプの追加方法、影効果の適用、ぼかしの調整、そして最終的に **シェイプ付きの Word を保存** して Microsoft Word や互換ビューアで開けるようにする手順が分かります。

この例では **Aspose.Words for Python via .NET** を使用します。このライブラリは Microsoft Office をインストールせずに Word 文書を操作できます。API の事前知識は不要で、基本的な Python の知識さえあれば始められます。

## 何ができるようになるか

- 新規ドキュメントの最初のセクションに長方形を挿入する。  
- ぼかし、オフセット、カラーを設定してソフトな影を構成する。  
- ドキュメントをディスクに保存し、視覚的な結果を確認する。

## 前提条件

- Python 3.8 以上。  
- `aspose-words` パッケージがインストール済み（`pip install aspose-words`）。  
- 出力ディレクトリへの書き込み権限。

## 長方形シェイプを作成し外観を設定する

最初のステップは空のドキュメントをインスタンス化し、そこに長方形シェイプを追加することです。このシェイプが影効果のキャンバスになります。

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Step 1: Create a new blank document
doc = aw.Document()

# Step 2: Add a rectangle shape to the first section
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Optional: Define the shape’s size and position (in points)
shape.width = aw.ConvertUtil.inch_to_point(2)   # 2 inches wide
shape.height = aw.ConvertUtil.inch_to_point(1)  # 1 inch tall
shape.left = aw.ConvertUtil.inch_to_point(1)    # 1 inch from the left margin
shape.top = aw.ConvertUtil.inch_to_point(1)     # 1 inch from the top margin
```

**なぜ重要か:**  
長方形を作成することで、後からスタイルを適用できる具体的なオブジェクト（`shape`）が得られます。明示的にサイズを指定することで、プラットフォーム間で同一の見た目を保証できます。

## Word 文書にシェイプを追加する方法

上記コードですでに長方形は追加されていますが、後で円や矢印など他のシェイプを追加したくなることもあるでしょう。同じパターンで、ドキュメントの body に対して `append_child` を呼び、目的の `ShapeType` を渡します。

```python
# Example: Adding a second shape – an ellipse
ellipse = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.ELLIPSE)
)
ellipse.width = aw.ConvertUtil.inch_to_point(1.5)
ellipse.height = aw.ConvertUtil.inch_to_point(1)
ellipse.left = aw.ConvertUtil.inch_to_point(3.5)
ellipse.top = aw.ConvertUtil.inch_to_point(1)
```

**ヒント:** `ShapeType` 列挙体を使ってサポートされているすべてのシェイプを確認しましょう。これによりコードが読みやすくなり、マジックナンバーの使用を避けられます。

## シェイプに影を適用しぼかしを設定する

影は奥行きと視覚的な興味を加えます。`ShadowEffect` クラスを使ってぼかし、オフセット、カラーを制御します。以下では長方形にソフトな黒い影を適用します。

```python
# Step 3: Configure a shadow effect for the rectangle
shadow = ShadowEffect()
shadow.blur = 5.0          # Sets the softness of the shadow edge
shadow.offset_x = 2.0      # Horizontal displacement from the shape
shadow.offset_y = 2.0      # Vertical displacement from the shape
shadow.color = aw.Color.black

# Step 4: Apply the shadow effect to the shape
shape.shadow = shadow
```

**なぜぼかしを設定するのか？**  
`blur` は影の拡散度合いを決めます。低い値（例: 1.0）だとエッジが鋭くなり、高い値（例: 5.0）だと優しいフェードになります。後者の方が美的に好まれることが多いです。

**エッジケース:** `blur` を 0 に設定すると、影は実体のあるシルエットになります。一部のビューアではエイリアシングのアーティファクトが出る可能性があるため、滑らかな出力を得るには 0 より大きい値を選びましょう。

## シェイプ付き Word を保存する

ドキュメントを永続化すると、すべての変更が確定します。`save` メソッドは `.docx` ファイルを書き出し、最新の Word プロセッサで開くことができます。

```python
# Step 5: Save the document to see the result
output_path = "output.docx"   # Adjust the path as needed
doc.save(output_path)
print(f"Document saved to {output_path}")
```

`output.docx` を開くと、左上隅から 1 インチ離れた位置に長方形が配置され、右下に 2 ポイントずらしたソフトな黒影が付いているのが確認できます。影のぼかしにより、シェイプがページから浮き上がって見える効果が得られます。

**プロのコツ:** ループで多数のドキュメントを生成する場合、同じ `Document` インスタンスを再利用し、各イテレーション間で body をクリアするとメモリ使用量を抑えられます。

## よくあるバリエーションとトラブルシューティング

| 状況 | 変更点 | 理由 |
|-----------|----------------|--------|
| 異なる影の色 | `shadow.color = aw.Color.red` | ブランドカラーを使用したり、重要なシェイプを強調したりするため。 |
| 影のオフセットを大きくする | `shadow.offset_x`/`offset_y` を増やす | UI モックアップで深さを強調したい場合。 |
| 影を全く付けない | `shape.shadow = shadow` 行を省く | ミニマリストなレポートに適しています。 |
| DOCX ではなく PDF にエクスポートする | `doc.save("output.pdf")` | 読み取り専用配布に最適な PDF。 |

シェイプが表示されない場合は、正しいセクション（`get_first_section()`）に追加しているか、変更後にドキュメントを保存しているかを確認してください。

## 完全な実行可能サンプル

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Create a new blank document
doc = aw.Document()

# Add a rectangle shape
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
shape.width = aw.ConvertUtil.inch_to_point(2)
shape.height = aw.ConvertUtil.inch_to_point(1)
shape.left = aw.ConvertUtil.inch_to_point(1)
shape.top = aw.ConvertUtil.inch_to_point(1)

# Configure and apply a shadow
shadow = ShadowEffect()
shadow.blur = 5.0
shadow.offset_x = 2.0
shadow.offset_y = 2.0
shadow.color = aw.Color.black
shape.shadow = shadow

# Save the document
output_path = "output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

スクリプトを実行すると、ソフトな影付きの長方形が入った `output.docx` が生成されます。Microsoft Word でファイルを開き、視覚効果が説明通りであることを確認してください。

## 結論

これで **長方形シェイプの作成**、**Word 文書へのシェイプ追加**、**シェイプへの影の適用**、**影のぼかし設定**、そして最終的に **シェイプ付き Word の保存** を Aspose.Words for Python を使って行う方法が分かりました。同じパターンを他のシェイプタイプ、カラー、エフェクトに拡張すれば、Office の自動化に依存せずにドキュメントグラフィックを完全にコントロールできます。

**次のステップ**

- `Shape.fill` を使ってグラデーションや画像背景を追加してみましょう。  
- `Paragraph` オブジェクトで長方形内部にテキストを配置する。  
- 複数のシェイプを組み合わせて複雑な図を作成し、PDF にエクスポートして配布する。  

コードを自由に適応し、レポートやテンプレート作成に活用してください。結果はコメントでシェアしましょう！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示したテクニックを基にした、密接に関連するトピックを扱っています。各リソースには完全な動作コード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、独自プロジェクトで代替実装アプローチを探求したりするのに役立ちます。

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}