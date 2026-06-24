---
category: general
date: 2026-06-24
description: Aspose.Words を使用して Python で長方形の図形を作成し、図形に影を追加する方法、影の角度を設定する方法、そして数分でドキュメントを
  PDF として保存する方法を学びます。
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shape shadow
- set shadow angle
language: ja
og_description: Pythonで矩形シェイプを作成し、シェイプに影を追加して影の角度を設定し、Aspose.Wordsで文書をPDFとして保存します。ステップバイステップのガイドに従ってください。
og_title: Pythonで矩形シェイプを作成 – 完全なAspose.Wordsチュートリアル
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  headline: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  name: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: What if I need a different shape?
    text: Aspose.Words supports many `ShapeType` values (ellipse, star, callout, etc.).
      Simply replace `aw.drawing.ShapeType.RECTANGLE` with the desired enum, like
      `aw.drawing.ShapeType.ELLIPSE`.
  - name: Can I add multiple shadows?
    text: The API exposes only one `ShadowFormat` per shape, but you can simulate
      multiple shadows by duplicating the shape, offsetting each copy, and adjusting
      transparency.
  - name: How do I change the shadow color to match my brand?
    text: Just set `shadow.color` to any `aw.drawing.Color`. For a brand blue, use
      `aw.drawing.Color.from_argb(255, 0, 120, 215)`.
  - name: What about saving as DOCX instead of PDF?
    text: Replace `document.save(pdf_path)` with `document.save("output/shadowed_rectangle.docx")`.
      The shadow rendering is preserved across both formats.
  - name: Does the shadow work on older PDF viewers?
    text: Aspose.Words renders the shadow as a vector effect, which is widely supported.
      However, very old viewers might flatten the effect; testing on your target audience’s
      devices is always a good habit.
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Pythonで長方形シェイプを作成 – 完全なAspose.Wordsガイド
url: /ja/python/images-shapes/create-rectangle-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Pythonで矩形シェイプを作成 – 完全な Aspose.Words ガイド

Pythonを使ってWord文書に**create rectangle shape**（矩形シェイプ）を作成する方法を考えたことはありますか？太字のコールアウトボックスが必要だったり、図の視覚的なヒントが欲しかったり、レポート用の装飾的な矩形が欲しかったりするかもしれません。どんなケースでも、ここが正しい場所です。このチュートリアルでは、矩形の挿入から、さりげない影の追加、影の角度の調整、そして最終的に**save document as PDF**（文書をPDFとして保存）まで、全工程を順に解説します。

**Aspose.Words for Python via .NET** を使用します。この強力なライブラリを使えば、Word を実際に開くことなく Word ファイルを操作できます。本ガイドの最後までに、*“how to add shape shadow”*（シェイプに影を追加する方法）という質問に自信を持って答えられるようになり、任意のプロジェクトに組み込める実行可能なスクリプトが手に入ります。

---

## 必要なもの

- **Python 3.8+** がマシンにインストールされていること。  
- **Aspose.Words for Python via .NET** (`aspose-words` パッケージ)。以下でインストールします：

  ```bash
  pip install aspose-words
  ```

- 生成された PDF を保存できる書き込み可能なフォルダー。  
- （オプション）IDE またはテキストエディタ—VS Code が便利です。

以上です。余分な DLL や Office のインストールは不要で、pip パッケージ一つだけです。

## ステップ 1: ドキュメントとビルダーの設定

最初に行うべきことは、**create rectangle shape** に対応したオブジェクト、すなわち `Document` と `DocumentBuilder` を作成することです。ビルダーはペンのようなものと考えてください。すべてを描画してくれます。

```python
import aspose.words as aw

# Initialize a new blank document
document = aw.Document()

# DocumentBuilder gives us a convenient way to add content
builder = aw.DocumentBuilder(document)
```

> **なぜ重要か:** `Document` オブジェクトは .docx ファイル全体を表し、`DocumentBuilder` は `insert_shape` のようなメソッドを提供して、シェイプの描画を簡単にします。

## ステップ 2: 矩形シェイプの挿入

ビルダーが用意できたので、いよいよ**create rectangle shape** が可能です。`insert_shape` メソッドは 3 つの引数、すなわちシェイプの種類、幅、そして高さを受け取ります。ここでは、バランスの取れたサイズとして幅 200 pt、高さ 100 pt を使用します。

```python
# Insert a rectangle with a width of 200 points and a height of 100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

この時点で、ドキュメント内に**create rectangle shape** に成功しています。生成された DOCX を開くと（後ほど実演します）、カーソル位置にシンプルな矩形が配置されているのが確認できます。

## ステップ 3: 影の書式設定オブジェクトへのアクセス

**add shadow to shape** を行うには、まずシェイプの影の書式設定を取得する必要があります。Aspose.Words のすべてのシェイプは、影に関するすべての設定を公開する `shadow_format` プロパティを持っています。

```python
# Grab the shadow formatting object for later tweaks
shadow = rectangle.shadow_format
```

`shadow` 参照を取得すれば、可視性、ぼかし、距離、角度、色、透明度を数行のコードで切り替えることができます。

## ステップ 4: 影を有効化し外観を設定

ここが魔法の場面です。**add shadow to shape** を行い、少しぼかしを加え、少しオフセットし、方向（**set shadow angle** の部分）を設定し、半透明の黒色を付与します。

```python
# Turn the shadow on
shadow.visible = True

# Soften the edges – a blur radius of 8 points looks natural
shadow.blur_radius = 8.0

# Push the shadow away from the rectangle by 5 points
shadow.distance = 5.0

# Set the direction of the light source – 45 degrees creates a diagonal drop
shadow.angle = 45

# Choose a color; black works well for most documents
shadow.color = aw.drawing.Color.black

# Make the shadow 30 % transparent for a subtle effect
shadow.transparency = 0.3
```

> **プロのコツ:** よりドラマチックな効果が必要な場合は `blur_radius` を増やすか `transparency` を下げてください。逆に、シャープで完全に不透明な影は `blur_radius = 0` と `transparency = 0` で実現できます。

## ステップ 5: ドキュメントを PDF として保存

**create rectangle shape** を行い、**add shadow to shape** を実施したので、最後に**save document as PDF** して、どのデバイスでも同一の結果が得られるようにします。Aspose.Words ではこれがワンライナーで実現できます。

```python
# Define where you want the PDF to land
output_path = "output/shadowed_rectangle.pdf"

# Save the whole document (including the rectangle with its shadow) as PDF
document.save(output_path)
print(f"PDF saved to {output_path}")
```

スクリプトを実行すると、`output` フォルダーに `shadowed_rectangle.pdf` が生成されます。任意の PDF ビューアで開くと、柔らかい 45 度の影が付いたきれいな矩形が表示されます—まさに設定した通りです。

## 完全な動作例

以下は、上記すべてのステップを組み合わせた完全な実行可能スクリプトです。`create_rectangle_with_shadow.py` という名前のファイルにコピー＆ペーストし、`python create_rectangle_with_shadow.py` を実行してください。

```python
import aspose.words as aw
import os

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Initialize document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert the rectangle shape (200 pt × 100 pt)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Access shadow formatting
shadow = rectangle.shadow_format

# 4️⃣ Configure shadow – visible, blurred, offset, angled, colored, semi‑transparent
shadow.visible = True
shadow.blur_radius = 8.0          # softer edges
shadow.distance = 5.0            # how far the shadow sits from the shape
shadow.angle = 45                # direction in degrees – this is the **set shadow angle** step
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.3        # 30 % transparent

# 5️⃣ Save the document as PDF
pdf_path = os.path.join(output_dir, "shadowed_rectangle.pdf")
document.save(pdf_path)

print(f"✅ PDF created at: {pdf_path}")
```

**Expected output:** 1 つの矩形にやさしい対角線上の影が付いた PDF ファイルが生成されます。余分なページや隠れたアーティファクトはなく、作成したシェイプだけが表示されます。

## よくある質問とエッジケース

### 別のシェイプが必要な場合は？

Aspose.Words は多数の `ShapeType` 値（楕円、星形、コールアウトなど）をサポートしています。`aw.drawing.ShapeType.RECTANGLE` を目的の列挙子、例えば `aw.drawing.ShapeType.ELLIPSE` に置き換えるだけです。

### 複数の影を追加できますか？

API ではシェイプごとに 1 つの `ShadowFormat` しか提供されませんが、シェイプを複製し、各コピーをオフセットし、透明度を調整することで複数の影をシミュレートできます。

### ブランドに合わせて影の色を変更するには？

`shadow.color` に任意の `aw.drawing.Color` を設定すれば OK です。ブランドの青色にしたい場合は、`aw.drawing.Color.from_argb(255, 0, 120, 215)` を使用します。

### PDF ではなく DOCX として保存するには？

`document.save(pdf_path)` を `document.save("output/shadowed_rectangle.docx")` に置き換えてください。影の描画は両方の形式で保持されます。

### 古い PDF ビューアでも影は機能しますか？

Aspose.Words は影をベクター効果として描画するため、広くサポートされています。ただし、非常に古いビューアでは効果がフラット化される可能性があります。対象ユーザーのデバイスでテストすることを常におすすめします。

## PDF を磨くためのヒント

- **枠線を追加:** `rectangle.line_format.width = 1.5` と色を設定して、はっきりしたアウトラインを作ります。  
- **矩形を中央揃え:** 挿入前に `builder.move_to_document_start()` を使用し、続いて `builder.paragraph_format.alignment = aw.ParagraphAlignment.CENTER` を設定します。  
- **テキストと組み合わせ:** 矩形の後に `TextFragment` を挿入してラベル付けします。例: `"Important Section"`。

これらの小さな調整により、シンプルな矩形がレポート、提案書、電子書籍などでプロフェッショナルに見える洗練されたコールアウトボックスに変わります。

## 結論

これで、Python で **create rectangle shape** を行い、**add shadow to shape**、**set shadow angle**、そして Aspose.Words を使用して **save document as PDF** するための、確実なエンドツーエンドの手順が手に入りました。手順はシンプルで、コードは完全に自己完結しています。また、ドキュメントの初期化から最終 PDF の仕上げまで、各行がなぜ重要かをご理解いただけたと思います。

次のステップとして、**how to add shape shadow** をより複雑な図形に適用したり、グラデーション塗りを試したり、シェイプ内にテーブルを生成したりしてみてください。また、ライブラリはシェイプをブックマークにリンクする機能も提供しており、インタラクティブな PDF を作成する際に便利です。

試した独自のアイデアがありますか？コメントで共有するか、残っている質問があれば遠慮なくどうぞ。コーディングを楽しんで、文書にさらなる奥行きを加えてください！

![影付き矩形シェイプ – Pythonで矩形シェイプを作成する例](/images/rectangle-shadow.png)

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした、密接に関連するトピックを扱っています。各リソースには、完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [JavaでWord文書を作成 – 影付き矩形シェイプの追加](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words シェイプ影チュートリアル – C#でWordシェイプに影を追加](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [C#でWordに矩形シェイプを作成 – ステップバイステップガイド](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}