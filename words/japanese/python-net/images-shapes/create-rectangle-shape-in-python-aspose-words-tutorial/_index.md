---
category: general
date: 2026-06-21
description: Aspose.Words を使用して Python で矩形シェイプを作成します。シェイプに影を追加し、塗りつぶし色を設定し、数分でドキュメントを
  PDF として保存する方法を学びましょう。
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- set shape fill color
language: ja
og_description: Aspose.Words を使用して Python で矩形シェイプを作成します。このガイドでは、シェイプに影を追加し、シェイプの塗りつぶし色を設定し、ドキュメントを
  PDF として保存する方法を示します。
og_title: Pythonで矩形シェイプを作成 – Aspose.Wordsチュートリアル
schemas:
- author: Aspose
  dateModified: '2026-06-21'
  description: Create rectangle shape in Python using Aspose.Words. Learn how to add
    shadow to shape, set shape fill color, and save document as PDF in minutes.
  headline: Create rectangle shape in Python – Aspose.Words tutorial
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF generation
title: Pythonで長方形シェイプを作成 – Aspose.Wordsチュートリアル
url: /ja/python/images-shapes/create-rectangle-shape-in-python-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Pythonで矩形シェイプを作成 – Aspose.Wordsチュートリアル

Pythonでコードを書きながら、Word文書に**矩形シェイプ**を作成したいと思ったことはありませんか？ あなただけではありません。多くの開発者が、色付きの箱にさりげない影を付けて、PDFとしてエクスポートしたいという壁にぶつかります。

このガイドでは、**矩形シェイプを作成**し、**シェイプの塗りつぶし色を設定**し、**シェイプに影を追加**し、最後に**文書をPDFとして保存**する、完全に実行可能なサンプルを順を追って解説します。曖昧な説明はなく、すぐにコピー＆ペーストして実行できる具体的なコードだけを提供します。

## 必要な環境

本題に入る前に、以下がマシンに揃っていることを確認してください。

- Python 3.8 以上（使用している構文は最近のバージョンであればすべて動作します）。
- 有効な Aspose.Words for Python のライセンス、または無料トライアル（ライブラリは純粋な Python で、COM 連携は不要です）。
- お好みのテキストエディタまたは IDE（VS Code が便利ですが、他でも構いません）。

以上です。重いフレームワークや OS レベルの追加依存は不要です。さっそく始めましょう。

## Step 1: Aspose.Words for Python をインストール

まずはじめに、まだインストールしていない場合は PyPI からパッケージを取得します。

```bash
pip install aspose-words
```

この手順が重要な理由: Aspose.Words が提供する `Document` と `DocumentBuilder` クラスがなければ、後で使用する `insert_shape` などのメソッドは存在せず、スクリプトはラインすら描画できずにクラッシュします。

> **Pro tip:** 仮想環境をきれいに保ちましょう。`python -m venv .venv && source .venv/bin/activate` を実行してからインストールすれば、ライブラリがシステムパッケージから分離されます。

## Step 2: 新しい Document と DocumentBuilder を作成

ここで実際に**矩形シェイプを作成**しますが、まずは空のキャンバスが必要です。

```python
import aspose.words as aw

# Initialize a new, empty Word document
doc = aw.Document()
# DocumentBuilder lets us add content programmatically
builder = aw.DocumentBuilder(doc)
```

`Document` オブジェクトはファイル全体を表し、`DocumentBuilder` はカーソル位置を管理し、その位置に要素を挿入できる便利なヘルパーです。ビルダーはページに書き込むペンのようなものと考えてください。

## Step 3: 矩形シェイプを挿入

ここがメインの処理です。固定幅・固定高さの**矩形シェイプを作成**し、ページ上に配置します。

```python
# Insert a rectangle 200 points wide and 100 points tall
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

なぜ矩形かというと、塗りつぶし色や影を示すのに最もシンプルな形状だからです。後で円や星が必要になったら、`ShapeType.RECTANGLE` を別の enum 値に置き換えるだけです。

## Step 4: シェイプの塗りつぶし色を設定

白い箱だけでは面白くないので、**シェイプの塗りつぶし色**を柔らかい色に設定します。レポートでは淡い青が見栄えします。

```python
# Apply a light‑blue background to the rectangle
rectangle.fill_color = aw.Color.light_blue
```

事前定義された `aw.Color` メンバー（`red`, `green`, `dark_gray` など）を使うか、RGB タプル（例: `aw.Color.from_argb(255, 30, 144, 255)`）を渡すことができます。塗りつぶし色は影や枠線が適用される前にユーザーが目にする色です。

## Step 5: シェイプに影を追加

次に**シェイプに影を追加**して、視覚的な磨きをかけます。影は奥行きを与え、矩形がページ上で際立ちます。

```python
# Grab the shadow format object
shadow = rectangle.shadow_format

# Turn the shadow on
shadow.visible = True
# Choose a dark gray tone for realism
shadow.color = aw.Color.dark_gray
# Blur radius controls softness (5 points is a nice middle ground)
shadow.blur = 5
# Horizontal and vertical offsets shift the shadow relative to the shape
shadow.offset_x = 3
shadow.offset_y = 3
# Slight transparency makes the shadow feel natural
shadow.transparency = 0.2
# Use an outer shadow – you could also try INSET for a different effect
shadow.type = aw.drawing.ShadowType.OUTER
```

**影を追加する方法**は上記コードそのものですが、各プロパティの意味を解説します:

- `visible` – 効果のオン/オフを切り替えます。
- `color` – 色を定義します。濃い灰色は自然光を模倣します。
- `blur` – 値が大きいほどエッジが柔らかくなります。
- `offset_x` / `offset_y` – 影をシェイプから離す距離です。光源の角度に合わせて調整します。
- `transparency` – 0 が不透明、1 が完全に透明です。0.2 で控えめな印象に。
- `type` – `OUTER` はシェイプの外側に影を落とし、`INNER` は内側に影を入れます。

ドラマチックなドロップシャドウが欲しい場合は、`blur` を 10‑15 に上げ、`offset_x`/`offset_y` を 6‑8 に設定すると効果的です。

## Step 6: 文書を PDF として保存

**文書を PDF として保存**し、他者と共有できなければ意味がありません。Aspose.Words ならワンライナーで完了します。

```python
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

PDF が選ばれる理由: PDF はプラットフォーム間でレイアウトを保持するため、レポートや請求書、印刷物に最適です。`save` メソッドはファイル拡張子を自動判別し、適切な形式で保存します。拡張子が `.pdf` であることだけ確認してください。

### 期待される結果

生成された `ShapeWithShadow.pdf` を開くと、1 ページ目の上部付近に淡い青色の矩形が中央に配置され、右下に少しずれた柔らかい濃灰色の影が付いているはずです。矩形のエッジはくっきり、影は控えめで、ファイルサイズは概ね 100 KB 未満です。

## ボーナス: 影の調整 – 「影の追加方法」への回答

*「シェイプを動かさずに影の方向だけ変えられる？」* と疑問に思うかもしれません。もちろん可能です。影の位置はシェイプの座標とは独立しているので、`offset_x` と `offset_y` を調整してください。正の値で右下方向、負の値で左上方向に移動します。左上から光が当たる設定は `offset_x = -3`、`offset_y = -3` が目安です。

別のよくある質問: *「同じシェイプに複数の影を付けられるか？」* Aspose.Words はシェイプあたり 1 つの影しかサポートしていません。レイヤード効果が必要な場合は、シェイプを複製して少しずらし、別々の影を付与するというハックが有効です。

## 完全スクリプト – 実行可能

以下が完結した自己完結型スクリプトです。`create_rectangle_with_shadow.py` という名前で保存し、`python create_rectangle_with_shadow.py` で実行してください。

```python
import aspose.words as aw

# ---------- Initialize document ----------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ---------- Insert rectangle ----------
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# ---------- Set fill color ----------
rectangle.fill_color = aw.Color.light_blue

# ---------- Configure shadow ----------
shadow = rectangle.shadow_format
shadow.visible = True
shadow.color = aw.Color.dark_gray
shadow.blur = 5
shadow.offset_x = 3
shadow.offset_y = 3
shadow.transparency = 0.2
shadow.type = aw.drawing.ShadowType.OUTER

# ---------- Save as PDF ----------
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

> **Note:** `YOUR_DIRECTORY` を実際に存在する絶対パスまたは相対パスに置き換えてください。フォルダーが存在しない場合、Python は `FileNotFoundError` をスローします。

## よくある落とし穴と回避策

| 問題 | 発生理由 | 対処方法 |
|------|----------|----------|
| 影が表示されない | `shadow.visible` がデフォルトの `False` のまま | `shadow.visible = True` を設定 |
| シェイプが見えない | 塗りつぶし色が `aw.Color.transparent` または `None` に設定されている | `aw.Color.light_blue` などの不透明色を使用 |
| PDF が空 | `doc.save` を呼び忘れた、または拡張子が間違っている | `doc.save("output.pdf")` を呼び、パスを確認 |
| `ImportError` が発生 | Aspose.Words がインストールされていない、または仮想環境が違う | アクティブな venv 内で `pip install aspose-words` を実行 |

## 次のステップ – さらに多くのシェイプと書式設定を探求

**矩形シェイプを作成**できたので、次は以下に挑戦できます:

- `ShapeType.RECTANGLE` を `ShapeType.ELLIPSE` や `ShapeType.PENTAGON` に置き換えて、他の幾何形状を試す。
- `builder.move_to(rectangle.absolute_position)` の後に `builder.writeln("Hello World")` を呼び出して、シェイプ内部にテキストを追加。
- `group = aw.drawing.GroupShape(doc)` を使って複数シェイプをグループ化し、複雑な図を作成。
- `doc.save("output.docx")` や `doc.save("output.html")` で DOCX や HTML へエクスポートし、影がどのように変換されるか確認。

これらすべては同じコア概念に基づきます: **シェイプに影を追加**、**シェイプの塗りつぶし色を設定**、そして **文書を PDF（または他形式）として保存**。

---

### 画像プレビュー *(任意)*

![Pythonで影付き矩形シェイプを作成](https://example.com/rectangle-shadow.png "Pythonで影付き矩形シェイプを作成")

*スクリーンショットは、淡い青色の矩形と控えめな外側影が付いた最終 PDF 出力を示しています。*

---

## 結論

Python で **矩形シェイプを作成**し、カスタム塗りつぶしを適用し、**シェイプに影を追加**し、最終的に **文書を PDF として保存**するまでの手順をすべて解説しました。コードはそのまま実行可能で、各プロパティの背後にある理由も説明しています。また、一般的なエッジケースと次に学ぶべき内容にも触れました。

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで扱ったテクニックを応用した関連トピックをカバーしています。各リソースには完全なコード例とステップバイステップの解説が含まれており、API の追加機能をマスターしたり、別の実装アプローチを自分のプロジェクトで試したりするのに役立ちます。

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}