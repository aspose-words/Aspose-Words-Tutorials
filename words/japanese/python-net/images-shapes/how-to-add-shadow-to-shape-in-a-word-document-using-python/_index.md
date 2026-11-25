---
category: general
date: 2026-11-25
description: PythonでWord文書の図形に影を追加する。Wordに長方形の図形を挿入し、Aspose.Wordsを使用して透明な影を適用する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- insert rectangle shape word
- how to create word document python
- Aspose.Words Python
- shape formatting Python
language: ja
lastmod: 2026-11-25
og_description: Python を使用して Word 文書の図形に影を追加します。このチュートリアルでは、Word に長方形の図形を挿入し、Aspose.Words
  を使用して 30% の透明な影を設定する方法を示します。
og_image_alt: Add shadow to shape example in a Word document created by Python
og_title: PythonでWord文書の図形に影を追加する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Add shadow to shape in a Word document with Python. Learn how to insert
    rectangle shape in Word and apply a transparent shadow using Aspose.Words.
  headline: How to add shadow to shape in a Word document using Python
  type: TechArticle
tags:
- Python
- Aspose.Words
- Word automation
title: Python を使用して Word 文書の図形に影を追加する方法
url: /ja/python/images-shapes/how-to-add-shadow-to-shape-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python を使用して Word 文書の図形に影を追加する方法

Word 文書に **影を追加** したい場合、このガイドでは完全に実行可能なソリューションを示します。Word ファイルの作成方法、長方形の図形の挿入方法、30 % の透明な影の適用方法を、すべて Aspose.Words for Python ライブラリを使用して確認できます。

Word 文書をプログラムで操作することで、手動での書式設定から解放され、レポート、契約書、マーケティングチラシなどを大規模に生成できます。このチュートリアルの最後までに、"**how to create Word document python**" という質問に対して、すぐに実行できるコードサンプルで答えられるようになります。

## 前提条件

* Python 3.8 以上がインストールされていること。
* 有効な Aspose.Words for Python ライセンス（評価用の無料トライアルでも可）。
* `aspose-words` パッケージを `pip install aspose-words` でインストールする。
* 出力ファイルを書き込めるフォルダー（コード中の `YOUR_DIRECTORY` を置き換えてください）。

追加の依存関係は必要ありません。

## 手順 1: 新しい Word 文書を作成する

最初のステップは `Document` オブジェクトをインスタンス化することです。このオブジェクトはメモリ上の .docx ファイル全体を表します。

```python
import aspose.words as aw

# Create an empty Word document
doc = aw.Document()
# DocumentBuilder provides a convenient API for adding content
builder = aw.DocumentBuilder(doc)
```

`DocumentBuilder` は仮想カーソルのように機能します。メソッドを呼び出すと、ライブラリは現在のカーソル位置に対応する要素を挿入します。

## 手順 2: 長方形の図形を挿入する

次に、ビルダーの `insert_shape` メソッドを使用して **長方形の図形を挿入** します。このメソッドは図形の種類とサイズ（ポイント単位、1 ポイント = 1/72 インチ）を指定する必要があります。

```python
# Insert a rectangle shape that is 100 points wide and 50 points tall
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)
```

デザインに合わせて寸法を変更できます。長方形は文書の描画レイヤーの一部となり、後で塗りつぶし、輪郭、影などを変更できます。

## 手順 3: 図形の影フォーマットにアクセスする

すべての描画オブジェクトは影の外観を制御する `shadow_format` プロパティを公開しています。これを取得して、透明度、オフセット、ぼかし、色を調整できます。

```python
# Get the ShadowFormat object for the rectangle
shadow = shape.shadow_format
```

この時点で図形はデフォルトの影（影なし）です。`ShadowFormat` オブジェクトには、リアルな効果を作成するために必要なすべてのパラメータが格納されています。

## 手順 4: 影を 30 % 透明にする

透明度は `0`（完全に不透明）から `1`（完全に透明）までの値で表されます。`0.3` に設定すると 30 % 透明な影になり、テキストを圧倒せずに深みを加えるのに十分です。

```python
# Apply a 30 % transparent shadow
shadow.transparency = 0.3
# Optional: adjust other shadow properties for a nicer look
shadow.visible = True               # Ensure the shadow is turned on
shadow.distance = 4                 # Distance of the shadow from the shape (points)
shadow.blur = 4                     # Amount of blur applied to the shadow
shadow.color = aw.Color.black       # Shadow color
```

これらの追加プロパティは必須ではありませんが、効果を微調整できることを示しています。`visible` フラグは重要で、これを忘れると他の設定が構成されていても影が表示されません。

## 手順 5: 文書を保存して結果を確認する

最後に、文書をディスクに書き込みます。生成された `.docx` ファイルを Microsoft Word や互換ビューアで開くと、透明な影が適用された長方形が表示されます。

```python
# Save the document to the desired location
output_path = r"YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

`output.docx` を開くと、右下にオフセットした控えめなグレーの影が付いたシンプルな長方形が表示されます。影の 30 % 透明度により、図形がページから浮き上がって見えます。

![図形への影の追加例](placeholder-image.png){: .align-center alt="Python で作成した Word 文書における図形への影の追加例"}

## 完全な実行可能スクリプト

すべてのパーツを組み合わせると、コピーして貼り付け、すぐに実行できる自己完結型スクリプトが得られます。

```python
import aspose.words as aw

def create_word_with_shadow(output_path: str):
    """
    Creates a Word document that contains a rectangle shape
    with a 30 % transparent shadow.
    """
    # Step 1: Initialize document and builder
    doc = aw.Document()
    builder = aw.DocumentBuilder(doc)

    # Step 2: Insert rectangle shape
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)

    # Step 3: Access shadow format
    shadow = shape.shadow_format

    # Step 4: Configure shadow properties
    shadow.visible = True
    shadow.transparency = 0.3
    shadow.distance = 4
    shadow.blur = 4
    shadow.color = aw.Color.black

    # Step 5: Save the document
    doc.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    # Replace with a valid folder on your machine
    create_word_with_shadow(r"YOUR_DIRECTORY/output.docx")
```

**期待される出力:** 生成された `output.docx` を開くと、長方形が軽い半透明の影を落とした単一ページが表示されます。追加の書式設定は不要です。

## よくあるバリエーションとエッジケース

| Situation | How to adapt the code |
|-----------|-----------------------|
| **異なる図形タイプ**（例: 楕円） | `aw.drawing.ShapeType.RECTANGLE` を `aw.drawing.ShapeType.ELLIPSE` に変更します。 |
| **カスタム影の色** | 赤みがかった影にするには `shadow.color = aw.Color.from_argb(255, 128, 0, 0)` を設定します。 |
| **複数の図形** | `builder.insert_shape` を繰り返し呼び出します。各呼び出しは個別にスタイル設定できる `Shape` オブジェクトを返します。 |
| **PDF として保存** | `doc.save(output_path)` を `doc.save(output_path.replace('.docx', '.pdf'))` に置き換え、拡張子を `.pdf` にします。 |
| **ライセンスなしで実行** | 無料トライアルは最初のページに透かしを追加します。製品環境で使用する場合はライセンスを取得して透かしを除去してください。 |

## ヒントとベストプラクティス

* **ビルダーを再利用する**: 文書全体で単一の `DocumentBuilder` インスタンスを保持し、不要なオブジェクト生成を避けます。
* **リソースを解放する**: 長時間実行するサービスでは、保存後に `doc.dispose()` を呼び出してネイティブメモリを解放します。
* **出力を検証する**: Open XML 標準への準拠を確認したい場合は、保存前に `doc.validate(aw.ValidationType.FULL_VALIDATION)` を使用します。
* **バージョン互換性**: このコードは Aspose.Words for Python ≥ 22.9 で動作します。`pip install --upgrade aspose-words` でパッケージを最新に保ってください。

## 結論

これで、Python を使用して Word 文書の **図形に影を追加** する方法が分かりました。5 つの手順（文書の作成、**長方形の図形を挿入**、影の設定、保存）に従うことで、レポート、請求書、マーケティング資料などの洗練された文書生成を自動化できます。

ここからは、グラデーション塗りつぶし、テキストの折り返し、文書の PDF 変換など、他の書式設定オプションを検討できます。これらのトピックはすべて、本チュートリアルで紹介した `DocumentBuilder` と図形書式設定の概念に基づいています。

コーディングを楽しんで、シンプルな影が自動生成された Word 文書にもたらす視覚的な深みを体感してください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトでの代替実装方法を探求するのに役立ちます。

- [Python を使用して Word 文書に長方形の図形を作成する方法](/words/english/python-net/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/)
- [Python で図形に影を追加 – 完全な Aspose.Words チュートリアル](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [空白の Word 文書を作成し、図形に影を追加する – 完全な Python ガイド](/words/english/python-net/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-pyth/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}