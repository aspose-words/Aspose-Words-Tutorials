---
category: general
date: 2026-06-27
description: Aspose.Words を使用して Python で矩形シェイプを挿入し、影の色を変更し、外側の影を追加し、シェイプに影効果を適用する方法を、すべてひとつのチュートリアルで学びましょう。
draft: false
keywords:
- how to insert rectangle shape
- how to change shadow color
- how to add outer shadow
- apply shadow effect to shape
language: ja
og_description: Pythonで長方形シェイプを挿入し、影の色を変更し、外側の影を追加し、Aspose.Wordsでシェイプに影効果を適用する方法をマスターする。
og_title: Pythonで長方形シェイプを挿入する方法 – Aspose.Wordsチュートリアル
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  headline: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  name: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: Pro tip
    text: If you need the rectangle positioned at a specific location, use `builder.move_to`
      before inserting, or adjust `rectangle.left` and `rectangle.top` after creation.
  - name: Edge case
    text: If you forget to set `shadow.opacity`, the default is fully opaque, which
      can make the shadow look like a solid shape. Always pair a color change with
      an appropriate opacity level.
  - name: Common pitfalls
    text: '- **Missing directory:** `doc.save` will raise an error if the folder doesn’t
      exist. Create it first or use `os.makedirs`. - **Version mismatch:** The shadow
      API requires Aspose.Words 22.9+; older versions silently ignore shadow settings.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
title: Pythonで矩形シェイプを挿入する方法 – 完全なAspose.Wordsガイド
url: /ja/python/images-shapes/how-to-insert-rectangle-shape-in-python-complete-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Pythonで長方形シェイプを挿入する方法 – 完全な Aspose.Words ガイド

Word 文書に **長方形シェイプを挿入する方法** を Python で知りたくありませんか？ 同じ問題に直面している開発者は多く、レポートの自動化やテンプレート作成で悩むことがよくあります。良いニュースは、Aspose.Words を使えばこの作業がとても簡単になることです。本チュートリアルでは、長方形を描画し、外側の影を付けるまでの全工程を解説します。

また、**影の色の変更方法**、**外側の影の追加方法**、そして最終的に **シェイプに影効果を適用する方法** もカバーします。最後まで読めば、プログラムで任意の .docx ファイルに挿入できる、完全にスタイリングされた長方形が作成できます。

## 前提条件

- Python 3.8+ がインストールされていること  
- `pip install aspose-words` で Aspose.Words for Python を導入済み  
- 基本的な Python スクリプトの知識（Word API の深い知識は不要）  

これらが揃っていれば、さっそく始めましょう。まだの場合はまずライブラリを取得してください。以降の手順はインポートが問題なく行える前提で説明します。

## Aspose.Words for Python で長方形シェイプを挿入する方法

最初のステップはキーワード通り **長方形シェイプを挿入する方法** です。新しいドキュメントを作成し、`DocumentBuilder` を生成してページに長方形を配置します。

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a fresh document and a builder to add content
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle shape of 200x100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Optional: give the rectangle a light fill so the shadow is visible
rectangle.fill_color = aw.drawing.Color.light_blue
```

> **ポイント:** `insert_shape` 呼び出しが *長方形シェイプを挿入する方法* の核心です。これにより `Shape` オブジェクトが返され、サイズ・位置・塗りつぶし・枠線などを後から自由に操作できます。`fill_color` も設定しておかないと、影が白紙に溶け込んで見えにくくなることがあります。

### プロのコツ
長方形を特定の位置に配置したい場合は、挿入前に `builder.move_to` を使用するか、作成後に `rectangle.left` と `rectangle.top` を調整してください。

## シェイプの影の色を変更する方法

長方形が文書内に配置されたので、次は **影の色を変更する方法** を見ていきます。Aspose.Words では `ShadowEffect` オブジェクトの `color` プロパティに任意の RGB 値を設定できます。

```python
# Create a shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # we’ll also cover outer shadow later
shadow.blur_radius = 8.0                  # smooth edges
shadow.distance = 6.0                     # how far the shadow sits from the shape
shadow.direction = 45                     # angle in degrees
shadow.opacity = 0.6                      # semi‑transparent

# Change the shadow color to a deep gray instead of black
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)

# Apply the shadow to our rectangle
rectangle.shadow = shadow
```

> **なぜ必要か:** 黒い濃い影は特に明るい文書では強すぎます。色を調整すれば、企業のブランディングに合わせたり、より柔らかいビジュアル効果を実現できます。

### エッジケース
`shadow.opacity` を設定し忘れると、デフォルトで完全不透明になるため、影が実体化した形に見えてしまいます。色変更と同時に適切な不透明度も設定しましょう。

## 外側の影効果を追加する方法

多くの人が次に尋ねるのは **外側の影を追加する方法** です。`ShadowStyle.OUTER` フラグを指定すると、Aspose.Words はシェイプの輪郭の外側に影を描画します。

上記コードでもすでに `ShadowStyle.OUTER` を使用していますが、分かりやすくするためにこの設定だけを抜き出して示します。

```python
# Ensure the shadow style is outer
shadow.style = ShadowStyle.OUTER
```

`ShadowStyle.INNER` に切り替えると、影は長方形の内部に表示され、エンボス効果などに利用できます。ほとんどの文書デザインシナリオでは、外側スタイルが自然なドロップシャドウになります。

## シェイプに影効果を適用する方法

すでに `rectangle.shadow = shadow` によって **シェイプに影効果を適用** しています。ここで全体をまとめてドキュメントを保存し、効果が保持されていることを確認しましょう。

```python
# Save the document – choose a folder you have write access to
output_path = "output/RectangleWithShadow.docx"
doc.save(output_path)

print(f"Document saved to {output_path}. Open it to see the rectangle with its outer shadow.")
```

`RectangleWithShadow.docx` を Microsoft Word で開くと、淡い青色の長方形に 45° の角度で薄いグレーの外側影が付いているはずです。影は少しぼかされ、オフセットされており、設定通りに表示されます。

### よくある落とし穴
- **ディレクトリが存在しない:** `doc.save` はフォルダが無いとエラーになります。事前に作成するか `os.makedirs` を使用してください。  
- **バージョン不一致:** 影の API は Aspose.Words 22.9 以降が必要です。古いバージョンでは影設定が無視されます。

## 完全動作サンプル

以下は、すべての手順を組み合わせた実行可能なスクリプトです。`rectangle_shadow.py` という名前で保存し、`python rectangle_shadow.py` で実行してください。

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Create a new document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2️⃣ Insert the rectangle shape (how to insert rectangle shape)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle.fill_color = aw.drawing.Color.light_blue   # make the shape visible

# 3️⃣ Define the shadow (how to change shadow color, how to add outer shadow)
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # outer shadow
shadow.blur_radius = 8.0
shadow.distance = 6.0
shadow.direction = 45
shadow.opacity = 0.6
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)  # custom gray

# 4️⃣ Apply the shadow (apply shadow effect to shape)
rectangle.shadow = shadow

# 5️⃣ Save the file
output_path = os.path.join(output_dir, "RectangleWithShadow.docx")
doc.save(output_path)

print(f"✅ Document generated: {output_path}")
```

**期待される出力:** `RectangleWithShadow.docx` という Word 文書が生成され、単一の長方形にグレーの外側影が付いています。Word で開いてビジュアル効果を確認してください。

## FAQ

| 質問 | 回答 |
|----------|--------|
| *別のシェイプタイプは使えますか？* | もちろんです。`ShapeType.RECTANGLE` を `ShapeType.OVAL`、`ShapeType.TRIANGLE` などに置き換えれば、同じ影ロジックが適用されます。 |
| *枠線を太くしたい場合は？* | 影を適用する前に `rectangle.line_width = 2.0`（ポイント）を設定してください。 |
| *影をアニメーションさせることは可能ですか？* | Aspose.Words だけでは直接はできません。HTML/CSS にエクスポートすればアニメーションが可能です。 |
| *macOS でも動作しますか？* | はい。Python が動作すれば、Aspose.Words はプラットフォームに依存しません。 |

## 結論

**長方形シェイプを挿入する方法**、**影の色を変更する方法**、**外側の影を追加する方法**、そして **シェイプに影効果を適用する方法** を Aspose.Words for Python で実践しました。完全なスクリプトは任意の自動化パイプラインにすぐ組み込め、数秒でプロフェッショナルな外観の長方形と洗練された影を作成できます。

次のステップに進みませんか？塗りつぶし色を変えてみたり、`direction` の角度をいろいろ試したり、同じページに複数のシェイプを配置してみましょう。また、Aspose.Words の豊富なテキスト書式設定 API と組み合わせて、影付きテキストで目を引くレポートを作成することも可能です。

このチュートリアルが役に立ったら、いいねやシェア、コメントであなたのバリエーションを教えてください。ハッピーコーディング！

![Diagram showing how to insert rectangle shape with an outer shadow applied in a Word document](/images/rectangle-shadow.png)


## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには完全な動作コード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、独自プロジェクトで代替実装を検討したりするのに役立ちます。

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}