---
category: general
date: 2026-08-01
description: Aspose.Words for Python を使用して Word の図形に影を設定する方法。不透明度の変更、ぼかしの調整、影の距離の変更をすばやく学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to set shadow
- how to change opacity
- how to adjust blur
- change shadow distance
- how to use aspose.words
language: ja
lastmod: 2026-08-01
og_description: Aspose.Words for Pythonでシェイプに影を設定する方法。ステップバイステップのチュートリアルに従って、不透明度を変更し、ぼかしを調整し、影の距離を変更しましょう。
og_image_alt: Screenshot showing how to set shadow on a shape using Aspose.Words in
  Python
og_title: Aspose.Wordsで影を設定する方法 – 簡単Pythonガイド
schemas:
- author: Aspose
  dateModified: '2026-08-01'
  description: How to set shadow on a Word shape using Aspose.Words for Python. Learn
    to change opacity, adjust blur, and change shadow distance quickly.
  headline: How to Set Shadow in Aspose.Words – Python Example
  type: TechArticle
- description: How to set shadow on a Word shape using Aspose.Words for Python. Learn
    to change opacity, adjust blur, and change shadow distance quickly.
  name: How to Set Shadow in Aspose.Words – Python Example
  steps:
  - name: '**Create the document** (or load a template).'
    text: '**Create the document** (or load a template).'
  - name: '**Insert the logo shape** (via `DocumentBuilder.insert_image` or `Shape`).'
    text: '**Insert the logo shape** (via `DocumentBuilder.insert_image` or `Shape`).'
  - name: '**Call `apply_shadow`** with your brand’s shadow specs.'
    text: '**Call `apply_shadow`** with your brand’s shadow specs.'
  - name: '**Export** to DOCX, PDF, or HTML with a single line of code.'
    text: '**Export** to DOCX, PDF, or HTML with a single line of code.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Shadow Formatting
- Word Automation
title: Aspose.Wordsで影を設定する方法 – Pythonの例
url: /ja/python/images-shapes/how-to-set-shadow-in-aspose-words-python-example/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words で影を設定する方法 – Python の例

Word のシェイプに対して、ドキュメントを手動で開かずに **影を設定する方法** を考えたことはありませんか？ あなただけではありません—レポートの自動化やブランド一貫性のあるテンプレート作成時に、多くの開発者がこの問題に直面します。良いニュースは、Aspose.Words for Python を使えば、シェイプの影、透明度、ぼかし、距離を数行のコードで調整できることです。

このチュートリアルでは、**影を設定する方法**、**透明度を変更する方法**、**ぼかしを調整する方法**、さらには **影の距離を変更する方法** を示す、完全に実行可能なサンプルを順を追って解説します。最後まで読めば、**Aspose.Words を使ってプログラムからシェイプをスタイリングする方法** をしっかりと理解できるようになります。

---

![Aspose.Words を使用したシェイプへの影の設定方法](image-placeholder.png){alt="Aspose.Words を使用したシェイプへの影の設定方法"}

## 前提条件

開始する前に、以下を用意してください。

| 要件 | 理由 |
|------|------|
| Python 3.8+ | モダンな構文、型ヒント |
| `aspose-words` パッケージ (pip install aspose-words) | Word 操作のコアライブラリ |
| 少なくとも1つのシェイプが含まれるサンプル `input.docx` | 影を付けるシェイプ |
| `output.docx` を保存するフォルダーへの書き込み権限 | 変更を永続化するため |

余分な DLL や COM インタープラは不要です—Aspose.Words は純粋な Python ライブラリなので、Windows、macOS、Linux のいずれでも実行できます。

---

## Aspose.Words でシェイプに影を設定する方法

以下は **完全** なスクリプトです。ドキュメントを読み込み、最初のシェイプ（再帰的に検索）を見つけ、影を設定し、結果を保存します。各行にコメントを付けているので、**何をしているか** だけでなく **なぜ** そうするのか が分かります。

```python
# ------------------------------------------------------------
# How to Set Shadow – Full Python Example using Aspose.Words
# ------------------------------------------------------------
import aspose.words as aw  # Import the Aspose.Words namespace

def apply_shadow(
    input_path: str,
    output_path: str,
    distance: int = 5,
    blur: float = 4.0,
    opacity: float = 0.6
) -> None:
    """
    Demonstrates how to set shadow on the first shape in a Word document.
    
    Parameters
    ----------
    input_path : str
        Path to the source .docx file.
    output_path : str
        Path where the modified .docx will be saved.
    distance : int, optional
        How far the shadow is offset from the shape (default = 5 points).
    blur : float, optional
        Blur radius of the shadow (default = 4.0 points).
    opacity : float, optional
        Opacity of the shadow (0 = fully transparent, 1 = fully opaque).
    """
    # Step 1: Load the Word document
    doc = aw.Document(input_path)

    # Step 2: Retrieve the first shape in the document (searches recursively)
    # The `True` flag makes the search go deep into headers, footers, and groups.
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

    if shape is None:
        raise ValueError("No shape found in the document. Add a shape and try again.")

    # Step 3: Configure the shadow appearance for the shape
    # ----------------------------------------------------
    # distance → how far the shadow sits away from the shape edge
    # blur     → softness of the shadow edge
    # opacity  → transparency level (0‑1 range)
    shape.shadow_format.distance = distance          # change shadow distance
    shape.shadow_format.blur = blur                  # how to adjust blur
    shape.shadow_format.opacity = opacity            # how to change opacity

    # Optional: tweak color and style if you need more control
    shape.shadow_format.color = aw.Color.black
    shape.shadow_format.style = aw.ShadowStyle.OUTER_SHADOW

    # Step 4: Save the modified document
    doc.save(output_path)

# -----------------------------------------------------------------
# Example usage – adjust the parameters to see different results
# -----------------------------------------------------------------
if __name__ == "__main__":
    apply_shadow(
        input_path="YOUR_DIRECTORY/input.docx",
        output_path="YOUR_DIRECTORY/output.docx",
        distance=8,       # increase distance for a more pronounced offset
        blur=6.5,         # higher blur makes the shadow softer
        opacity=0.75      # make the shadow a bit more solid
    )
```

### なぜこれが機能するのか

* **`doc.get_child(..., True)`** – `True` フラグにより Aspose.Words は **再帰的に** 検索し、ヘッダー・フッターやグループ化オブジェクト内のシェイプまで見つけます。シェイプの正確な位置が分からない場合に重要です。
* **`shadow_format`** – このプロパティは影に関するすべての設定をまとめます。`distance`、`blur`、`opacity` を設定することでシェイプの視覚的な奥行きをコントロールできます。これらの値を変更することで、**透明度の変更方法**、**ぼかしの調整方法**、**影の距離の変更方法** を一つの呼び出しで実演できます。
* **保存** – `doc.save` は新しい `.docx` を書き出します。元のファイルはそのまま残るため、バッチ処理に安全なパターンです。

---

## シェイプの影の透明度を変更する方法

透明度は影の透過度を決定します。範囲は 0.0（完全に見えない）から 1.0（完全に不透明）です。上記のコードでは `opacity` 引数を変更するだけで調整できます。

```python
shape.shadow_format.opacity = 0.85  # 85% opaque – looks richer on dark backgrounds
```

> **プロのコツ:** 後で PDF を生成する場合、透明度が高いほど影が深く、印刷に適した見た目になります。0.4〜0.9 の間で試して、ブランドガイドラインに合う最適な値を見つけてください。

---

## 柔らかい見た目のためにぼかしを調整する方法

ぼかしは影のエッジに適用されるガウスぼかしの半径です。数値が大きいほどフェザー状の効果になります。

```python
shape.shadow_format.blur = 10.0  # Very soft, almost hazy shadow
```

はっきりとしたドロップシャドウ（「Microsoft PowerPoint」スタイル）を求める場合は、`blur` を `1.0` のような低い値に設定してください。

---

## 奥行きを演出するために影の距離を変更する

距離はポイント単位で測定されます（1 pt = 1/72 in）。影を遠くに移動させると、シェイプがより高く浮いているように見えます。

```python
shape.shadow_format.distance = 12  # Shadow shifts 12 pt away from the shape
```

大きめの `distance` と程よい `blur` を組み合わせると、ドラマチックな「持ち上げ」効果が得られます。

---

## すべてをまとめたミニプロジェクト

自動レポートジェネレータでテキストボックス内に会社ロゴを挿入し、すべてのロゴに企業スタイルに合わせた微妙な影を付けたいと想像してください。`apply_shadow` 関数を使えば以下が可能です。

1. **ドキュメントを作成**（またはテンプレートをロード）。
2. **ロゴのシェイプを挿入**（`DocumentBuilder.insert_image` または `Shape` を使用）。
3. **`apply_shadow` を呼び出し**、ブランドの影の仕様を渡す。
4. **エクスポート**：DOCX、PDF、または HTML にワンラインで出力。

関数がパラメータを受け取るので、影の設定を JSON ファイルに保存し、数十のドキュメントに一括適用できます—手動で調整する手間は不要です。

---

## よくある質問とエッジケース

| 質問 | 回答 |
|------|------|
| **ドキュメントに複数のシェイプがある場合はどうしますか？** | この例は *最初の* シェイプを対象にしています。すべてのシェイプに影を付けるには、`doc.get_child_nodes(aw.NodeType.SHAPE, True)` でループし、各ノードに同じ `shadow_format` 設定を適用します。 |
| **別の影の色を設定できますか？** | もちろんです。`shape.shadow_format.color = aw.Color(255, 0, 0)` のように赤い影を設定したり、任意の `aw.Color` を使用できます。 |
| **PDF への変換後もこれらの設定は保持されますか？** | はい。Aspose.Words は PDF へのレンダリング時に影のプロパティを保持しますが、非常に高いぼかし値は近似されることがあります。 |
| **大きなドキュメントでパフォーマンスへの影響はありますか？** | 影 API はシェイプオブジェクトだけに作用するため、500 ページのレポートでも数ミリ秒で処理できます。ボトルネックは通常 I/O であり、影設定自体は軽量です。 |
| **後で影を削除できますか？** | `shape.shadow_format.is_visible = False` と設定するか、プロパティをデフォルトにリセットすれば影を削除できます。 |

---

## 完全動作サンプルのまとめ

コメントを除いた全スクリプトを再掲します。コピー＆ペーストで即座に実行できます。

```python
import aspose.words as aw

def apply_shadow(input_path, output_path, distance=5, blur=4.0, opacity=0.6):
    doc = aw.Document(input_path)
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
    if shape is None:
        raise ValueError("No shape found.")
    shape.shadow_format.distance = distance
    shape.shadow_format.blur = blur
    shape.shadow_format.opacity = opacity
    shape.shadow_format.color = aw.Color.black
    shape.shadow_format.style = aw.ShadowStyle.OUTER_SHADOW
    doc.save(output_path)

if __name__ == "__main__":
    apply_shadow(
        "YOUR_DIRECTORY/input.docx",
        "YOUR_DIRECTORY/output.docx",
        distance=8,
        blur=6.5,
        opacity=0.75
    )
```

スクリプトを実行し、`output.docx` を開くと、設定したパラメータに合わせたきれいな影がシェイプに適用されていることが確認できます。

---

## 結論

私たちは **

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示したテクニックを基にした、密接に関連するトピックを扱っています。各リソースには、完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得したり、独自プロジェクトで代替実装アプローチを探求したりするのに役立ちます。

- [Aspose.Words シェイプ影チュートリアル – C# で Word シェイプに影を追加](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Aspose.Words for Python を使用した Word ドキュメントでのコメントと返信の実装方法](/words/english/python-net/annotations-comments/aspose-words-python-comments-replies/)
- [Aspose.Words for Python でドキュメント変数を管理する方法：完全ガイド](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}