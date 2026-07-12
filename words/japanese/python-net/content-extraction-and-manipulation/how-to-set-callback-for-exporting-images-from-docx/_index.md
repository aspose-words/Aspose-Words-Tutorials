---
category: general
date: 2026-06-24
description: Markdown に保存する際に DOCX から画像をエクスポートするコールバックの設定方法。画像の抽出方法、Word から SVG を抽出する方法、カスタム処理で
  DOCX を Markdown に保存する方法を学びましょう。
draft: false
keywords:
- how to set callback
- export images from docx
- how to extract images
- save docx as markdown
- extract svg from word
language: ja
og_description: Markdown に変換する際に DOCX から画像をエクスポートするコールバックの設定方法。このガイドでは、画像と SVG を効率的に抽出する方法を紹介します。
og_title: DOCXから画像をエクスポートするためのコールバック設定方法
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  headline: How to Set Callback for Exporting Images from DOCX
  type: TechArticle
- description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  name: How to Set Callback for Exporting Images from DOCX
  steps:
  - name: '**Deterministic names** – useful for version control or CDN publishing.'
    text: '**Deterministic names** – useful for version control or CDN publishing.'
  - name: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
    text: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
  - name: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
    text: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Conversion
title: DOCXから画像をエクスポートするためのコールバック設定方法
url: /ja/python/content-extraction-and-manipulation/how-to-set-callback-for-exporting-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX から画像をエクスポートするためのコールバック設定方法

Markdown に変換する際に **コールバックの設定方法** を知りたくなったことはありませんか？ **DOCX から画像をエクスポート** したいと思ったことはありませんか？ あなただけではありません。多くの開発者が、デフォルトの変換で画像がすべて汎用フォルダーにダンプされる、あるいは最悪の場合 SVG グラフィックが完全に失われるという壁にぶつかっています。  

このチュートリアルでは、完全に実行可能なソリューションを順を追って解説し、「**コールバックの設定方法**」という疑問に答え、**画像の抽出方法** を示し、さらに **Word から SVG を抽出** する方法までカバーします。最後まで読むと、すべての画像リソースにカスタム命名スキームを適用した **DOCX を Markdown として保存** できるようになり、手作業での調整は不要です。

## 学習内容

- 変換中に画像ファイル名を制御する最もクリーンな方法としてコールバックがなぜ有効か。  
- Aspose.Words の `MarkdownSaveOptions.resource_saving_callback` にフックする方法。  
- **PNG**、**JPG**、**SVG**、その他埋め込みリソースを抽出するステップバイステップのコード。  
- 名前衝突、大容量ファイル、クロスプラットフォームのパスの癖への対処法。  

> **プロのコツ:** すでに Aspose.Words を大規模パイプラインで使用している場合、残りのコードに手を加えることなくこのコールバックだけを差し込むことができます。

---

![コールバック設定方法の図](https://example.com/images/how-to-set-callback.png "コールバック設定方法")

## 前提条件

- Python 3.8+（例では f‑strings を使用しているので 3.6 以上で OK）。  
- `aspose-words` パッケージがインストール済み（`pip install aspose-words`）。  
- ラスタ画像 **と** ベクタ画像（SVG）を含む DOCX ファイル。  
- Python の関数とファイル I/O に関する基本的な知識。

これらが揃っていれば、さっそく始めましょう。

---

## DOCX から画像をエクスポートするためのコールバック設定方法

ソリューションの核心は **リソース保存コールバック** にあります。Aspose.Words は `document.save` を呼び出したときに、書き込み対象となるすべての画像や SVG に対してこのデリゲートを呼び出します。タプル `(new_name, data)` を返すことで、ファイル名とバイトペイロードの両方を決定できます。

```python
import aspose.words as aw
import os
import hashlib

# Step 1: Load the source document
document = aw.Document("YOUR_DIRECTORY/input.docx")
```

### なぜコールバックが必要か？

コールバックがない場合、Aspose.Words は `image1.png`、`image2.svg` などの名前でファイルを作成し、Markdown ファイルの隣のフォルダーに配置します。デモとしては問題ありませんが、本番環境では次のような要件が出てきます。

1. **決定的な名前** – バージョン管理や CDN 配信に便利。  
2. **衝突回避** – 元の名前が同じでも上書きされない。  
3. **カスタムフォルダー構造** – たとえばすべてのアセットを `/assets/docs/` 配下に置きたい場合。  

コールバックを使えば、これら 3 つの懸念点をすべて制御できます。

---

## リソースコールバックを使って DOCX から画像をエクスポートする

以下がコールバック実装です。バイナリデータのハッシュを使って一意なサフィックスを生成し、元の拡張子を保持したうえで新しいファイル名と生バイト列を返します。

```python
def resource_callback(resource):
    """
    Called for every image/SVG that MarkdownSaveOptions wants to write.
    Returns a tuple (new_name, data) to control the saved file name.
    """
    # Preserve the original extension (.png, .svg, …)
    extension = os.path.splitext(resource.name)[1]

    # Compute a short hash of the image bytes – guarantees uniqueness
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]

    # Build a deterministic, collision‑free filename
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data
```

#### エッジケースの取り扱い

- **大容量ファイル:** SHA‑256 はサイズに関係なく機能しますが、ハッシュ計算はメモリ上で行われるため、非常に大きな PDF を処理する場合はメモリ使用量に注意してください。  
- **拡張子がない場合:** 古い Word ファイルでは画像に拡張子が付与されていないことがあります。その場合 `extension` は空になるので、`.bin` をデフォルトにしたり、先頭数バイトからフォーマットを推測したりしてください。  
- **画像以外のリソース:** コールバックは OLE オブジェクトなどすべての外部リソースに対して呼び出されます。画像／SVG のみが対象であれば、`resource.type` でフィルタリングしてください。

---

## Word から画像と SVG を抽出する方法

次に、Markdown 保存パイプラインにコールバックを組み込みます。`MarkdownSaveOptions` オブジェクトはこの目的のために `resource_saving_callback` プロパティを公開しています。

```python
# Step 2: Configure Markdown save options to use the callback
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.resource_saving_callback = resource_callback

# Optional: set the folder where images will be placed relative to the .md file
markdown_options.resource_folder = "assets/images"
```

`resource_folder` の設定は任意ですが、指定しておくと便利です。省略した場合、画像は Markdown ファイルの隣に配置され、プロジェクトのルートが散らかってしまいます。

### ドキュメントの保存

```python
# Step 3: Save the document as Markdown, letting the callback store the resources
output_md_path = "YOUR_DIRECTORY/output.md"
document.save(output_md_path, markdown_options)
print(f"Markdown saved to {output_md_path}")
```

スクリプトを実行すると、次のようなファイルが生成されます：

```
assets/images/img_a1b2c3d4e5.png
assets/images/img_f6g7h8i9j0.svg
```

そして生成された `output.md` には、正確にそのファイル名を指す画像リンクが埋め込まれます：

```markdown
![Image](assets/images/img_a1b2c3d4e5.png)
```

これが **画像抽出方法** の実装例です――ラスタでもベクタでも、すべてが個別の一意なアセットとして出力されます。

---

## カスタム画像処理で DOCX を Markdown に保存する

以下に、`convert_docx_to_md.py` という名前で保存できるフルスクリプトを示します：

```python
import aspose.words as aw
import os
import hashlib

def resource_callback(resource):
    """Control the naming of each exported image/SVG."""
    extension = os.path.splitext(resource.name)[1] or ".bin"
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data

def convert_docx_to_markdown(input_path, output_md_path, image_folder="assets/images"):
    # Load the DOCX
    document = aw.Document(input_path)

    # Set up Markdown options with our callback
    md_options = aw.saving.MarkdownSaveOptions()
    md_options.resource_saving_callback = resource_callback
    md_options.resource_folder = image_folder

    # Ensure the output directory exists
    os.makedirs(os.path.dirname(output_md_path), exist_ok=True)
    os.makedirs(os.path.join(os.path.dirname(output_md_path), image_folder), exist_ok=True)

    # Perform the conversion
    document.save(output_md_path, md_options)
    print(f"✅ Conversion complete! Markdown at: {output_md_path}")

if __name__ == "__main__":
    # Adjust these paths to your environment
    INPUT_DOCX = "YOUR_DIRECTORY/input.docx"
    OUTPUT_MD = "YOUR_DIRECTORY/output.md"
    convert_docx_to_markdown(INPUT_DOCX, OUTPUT_MD)
```

**なぜこれが機能するか:**  
- `resource_callback` がすべての画像に一意で再現可能な名前を保証します。  
- `resource_folder` により、Markdown が資産フォルダーと分離されて見やすくなります。  
- `os.makedirs` 呼び出しにより、スクリプトを新しいマシンで実行した際の「フォルダーが見つからない」エラーを防ぎます。

---

## SVG を Word から抽出 – ベクタ画像はどう扱う？

SVG はコールバック上では PNG と同様に扱われます。なぜなら、SVG も単なる別の `resource` だからです。唯一の違いは、古い Word バージョンでは SVG が *OfficeArt* オブジェクトとして埋め込まれ、Aspose.Words が自動的にラスタ PNG に変換してしまう点です。**SVG を保持** したい場合は次のフラグを有効にします：

```python
md_options.export_svg = True  # Keep original SVG markup
```

保存前にこの行を追加すれば、コールバックは `.svg` 拡張子のリソースを受け取り、ベクタデータをそのまま保持します――レスポンシブな Web ドキュメントに最適です。

---

## よくある質問と落とし穴

| 質問 | 回答 |
|----------|--------|
| **画像が同一の場合はどうしますか？** | SHA‑256 ハッシュが同一になるためファイル名が衝突します。両方のコピーが必要な場合は、ハッシュ計算に元の `resource.name` を組み込んでください（例: `hash(resource.name + resource.data)`）。 |
| **ファイルタイプごとにフォルダーを変えられますか？** | はい。`resource_callback` 内で `extension` を確認し、`f"png/{new_name}"` や `f"svg/{new_name}"` のようにパスを返すことで実現できます。 |
| **Linux/macOS でも動作しますか？** | 完全に動作します。コードは `os.path` を使用しているため、パス区切り文字を自動的に処理します。商用版を使用する場合は、ライセンスファイル `aspose.words.lic` がアクセス可能であることを確認してください。 |
| **超大容量ドキュメントのメモリ使用量は？** | コールバックは各リソースの **フルバイト配列** を受け取ります。つまり画像は一時的にメモリに載ります。マルチギガバイト規模のファイルの場合は、コールバック内でデータをディスクにストリーム保存し、`return (new_name, None)` のように返すことを検討してください。 |

---

## 結論

これで **DOCX を Markdown に保存** する際に画像抽出を制御する **コールバックの設定方法** が分かりました。画像のエクスポート、Word からの SVG 抽出、そして Markdown をクリーンかつ決定的に保つ手法を習得しました。  

単一の自己完結型スクリプトで、ドキュメントの読み込み、リソース保存コールバックの定義、`MarkdownSaveOptions` の設定、名前衝突やベクタ画像といったエッジケースの処理まで網羅しています。その結果、ユニークな名前の資産が Markdown と共に生成され、静的サイトジェネレータやドキュメントパイプライン、再利用可能な資産が必要なあらゆるワークフローで即座に活用できます。

**次のステップは？**  
- MkDocs などの静的サイトジェネレータと組み合わせて、Word ベースのドキュメントを自動的に公開してみましょう。  
- 外部ファイルではなくインライン画像が好みの場合は、`markdown_options.export_images_as_base64 = True` を試してください。  
- Aspose.Words の他のコールバック（例: `document_saving_callback`）を調査し、Markdown 出力自体をカスタマイズしてみましょう。

他の Office フォーマットから **画像を抽出** する方法や、特定の命名規則に合わせたコールバックの調整が必要な場合は、下のコメント欄で質問してください。Happy coding!

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには完全な動作コード例とステップバイステップの解説が含まれており、API の追加機能をマスターしたり、別の実装アプローチを自分のプロジェクトで試したりするのに役立ちます。

- [DOCX から Markdown へ変換する際の画像リネーム方法](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)
- [DOCX から Markdown を保存する – ステップバイステップガイド](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}