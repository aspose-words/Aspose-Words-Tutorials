---
category: general
date: 2026-09-27
description: Aspose.Words for Python を使用して図形に影を設定する方法を学びましょう。このガイドでは、図形への影の追加、影効果の適用、影の色の設定について説明します。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to set shadow
- add shadow to shape
- apply shadow effect
- set shadow color
- how to add shadow
language: ja
lastmod: 2026-09-27
og_description: Aspose.Words for Python を使用してシェイプに影を設定する方法。ステップバイステップのガイドに従って、シェイプに影を追加し、影効果を適用し、影の色を設定します。
og_image_alt: Screenshot showing how to set shadow on a shape in a Word document
og_title: Aspose.Words for Pythonでシェイプに影を設定する方法
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to set shadow on a shape with Aspose.Words for Python. This
    guide covers add shadow to shape, apply shadow effect, and set shadow color.
  headline: How to set shadow on a shape in Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Shapes
- Shadow effect
title: Aspose.Words for Pythonでシェイプに影を設定する方法
url: /ja/python/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Python でシェイプに影を設定する方法

描画オブジェクトに **影の設定方法** が必要な場合、このガイドでは手順全体を示します。シェイプに影を追加し、影のぼかし、オフセット、色を設定し、コードから離れることなく更新されたドキュメントを保存する方法が分かります。

このチュートリアルは、すでに基本的な Aspose.Words for Python 環境が整っていることを前提としています。記事の最後までに、DOCX ファイル内の任意のシェイプにプロフェッショナルな外観の影効果を適用できるようになります。

## 前提条件

* Python 3.8+ がインストールされていること。
* Aspose.Words for Python via .NET (`pip install aspose-words`) がインストールされていること。
* 少なくとも1つのシェイプ（例: 四角形または画像）を含む Word 文書（`input.docx`）。  
  文書が空の場合、コードはデモ用に新しいシェイプを作成します。

これらの項目が揃っていれば、以降の手順をインポートエラーなく実行できます。

## 手順 1: Word 文書を読み込むまたは作成する

最初の操作は `Document` オブジェクトを取得することです。既存のファイルを読み込むか、新規に作成できます。

```python
import aspose.words as aw

# Load an existing document, or create a new blank document if the file does not exist.
try:
    doc = aw.Document("YOUR_DIRECTORY/input.docx")
except Exception:
    doc = aw.Document()          # Creates an empty document
    # Optional: add a paragraph so the document is not completely empty.
    builder = aw.DocumentBuilder(doc)
    builder.writeln("Document created for shadow demo.")
```

*このステップが重要な理由*: `Document` オブジェクトはすべての Word 処理操作のエントリーポイントです。これがなければシェイプにアクセスしたり、ビジュアル効果を適用したりできません。

## 手順 2: 対象シェイプを取得する

シェイプの外観を操作するには、シェイプノードへの参照が必要です。以下の例は、ドキュメント階層で最初に見つかったシェイプを取得します。

```python
# Retrieve the first shape in the document tree.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# If the document has no shapes, create one for demonstration purposes.
if shape is None:
    builder = aw.DocumentBuilder(doc)
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
    shape.wrap_type = aw.drawing.WrapType.INLINE
```

*このステップが重要な理由*: `add shadow to shape` には具体的なシェイプオブジェクトが必要です。コードはドキュメントにシェイプがない場合のエッジケースを安全に処理し、すべての読者がチュートリアルを実行できるようにします。

## 手順 3: 影の外観を設定する

これでシェイプの `shadow` プロパティを調整して **影効果を適用** できます。以下の設定は控えめで暗い影を与えます。

```python
# Set the shadow blur radius (softness). Larger values produce a more diffused shadow.
shape.shadow.blur = 5.0

# Horizontal displacement of the shadow in points.
shape.shadow.offset_x = 2.0

# Vertical displacement of the shadow in points.
shape.shadow.offset_y = 2.0

# Set the shadow color. This demonstrates **set shadow color** to black.
shape.shadow.color = aw.Color.black

# Enable the shadow (some older versions require explicit visibility).
shape.shadow.visible = True
```

*各プロパティが重要な理由*:

| Property | Effect |
|----------|--------|
| `blur`   | 影のぼかし具合を制御します。 |
| `offset_x` / `offset_y` | シェイプからの方向と距離を決定します。 |
| `color`  | 影の色相を定義します。任意の `aw.Color` を使用できます。 |
| `visible`| 影が出力ファイルに描画されることを保証します。 |

`aw.Color.black` を `aw.Color.from_argb(255, 0, 0, 0)` に置き換えてカスタム RGBA 値を使用したり、他の事前定義された色を使用したりできます。

## 手順 4: 変更された文書を保存する

影を設定した後、変更を新しいファイルに保存します。

```python
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved with shadow effect at: {output_path}")
```

Microsoft Word で `output.docx` を開くと、選択したシェイプに右方向に 2 pt、下方向に 2 pt 移動した柔らかい黒い影が表示されます。

## 完全な動作例

すべての手順をまとめると、IDE にコピー＆ペーストできる単体のスクリプトが得られます。

```python
import aspose.words as aw

def add_shadow_to_first_shape(input_path: str, output_path: str):
    # Load or create the document.
    try:
        doc = aw.Document(input_path)
    except Exception:
        doc = aw.Document()
        builder = aw.DocumentBuilder(doc)
        builder.writeln("Document created for shadow demo.")

    # Retrieve the first shape; create one if none exist.
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
    if shape is None:
        builder = aw.DocumentBuilder(doc)
        shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
        shape.wrap_type = aw.drawing.WrapType.INLINE

    # Apply shadow settings.
    shape.shadow.blur = 5.0
    shape.shadow.offset_x = 2.0
    shape.shadow.offset_y = 2.0
    shape.shadow.color = aw.Color.black
    shape.shadow.visible = True

    # Save the result.
    doc.save(output_path)
    print(f"Shadow applied and saved to {output_path}")

# Example usage
if __name__ == "__main__":
    add_shadow_to_first_shape(
        input_path="YOUR_DIRECTORY/input.docx",
        output_path="YOUR_DIRECTORY/output.docx"
    )
```

スクリプトを実行すると、最初のシェイプに設定した影が付いた `output.docx` が生成されます。

## よくある落とし穴と回避方法

| Issue | Reason | Fix |
|-------|--------|-----|
| `shape` がドキュメント読み込み後でも `None` になる | ドキュメントに描画オブジェクトが含まれていません。 | 手順 2 に示したフォールバックのシェイプ作成ブロックを使用します。 |
| Word で影が表示されない | `shape.shadow.visible` が `False` のまま、またはドキュメントが古い形式（例: `.doc`）で保存されている。 | `visible = True` に設定し、`.docx` 形式で保存してください。 |
| 色が期待と異なる | ドキュメントのテーマが明示的な色設定を上書きしています。 | テーマの上書きを無効にした後に `shape.shadow.color` を設定するか、`aw.Color.from_argb` を使用してください。 |

これらのエッジケースに対処することで、実運用コードでも堅牢なソリューションとなります。

## 効果の拡張（次のステップ）

これで **影の追加方法** が分かったので、関連する拡張機能を検討できます：

* **apply shadow effect** を `shape.shadow` のサブプロパティを調整して、グラデーションや複数の影を持つ **apply shadow effect** を実現します。
* ユーザー入力やテーマカラーに基づいて **set shadow color** を動的に使用します。
* **add shadow to shape** を回転、線スタイル、3‑D 効果などの他の書式設定アクションと組み合わせます。
* `doc.get_child_nodes(aw.NodeType.SHAPE, True)` を反復処理して、ドキュメント内のすべてのシェイプに影の追加を自動化します。

これらの拡張により、洗練された視覚的に一貫した出力を生成する高度なドキュメント生成パイプラインを構築できます。

## 結論

これで、Aspose.Words for Python を使用してシェイプに **how to set shadow** を設定する完全な実行可能ソリューションが手に入りました。本ガイドでは、ドキュメントの読み込み、シェイプの取得または作成、ぼかし・オフセット・**set shadow color** の設定、そして最終的なファイル保存までをカバーしました。このパターンを自動化プロジェクトの任意のシェイプに適用し、デザイン要件に合わせて追加のビジュアル調整を試してみてください。

---

*他のシェイプタイプ、色、オフセット値に合わせてコードを自由に適応してください。問題が発生した場合は、まず「Common pitfalls」テーブルを確認すると良いでしょう。*

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Add shadow to shape in C# – Complete Guide to Apply Shadow Effect](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-c-complete-guide-to-apply-shadow-effe/)
- [Add shadow to shape in Word – Complete Aspose.Words Guide](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}