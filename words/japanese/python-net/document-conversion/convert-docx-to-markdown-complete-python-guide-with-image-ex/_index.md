---
category: general
date: 2026-06-27
description: Python を使って docx を markdown に変換します。Word から画像を抽出し、カスタムコールバックで markdown
  出力を保存する方法を学びます。
draft: false
keywords:
- convert docx to markdown
- extract images from word
- convert word to markdown
- python docx to markdown
- save markdown output
language: ja
og_description: Pythonでdocxをmarkdownに変換し、Wordから画像を抽出し、カスタムリソースコールバックを使用してmarkdown出力を保存する。
og_title: docxをmarkdownに変換 – 画像抽出付きPythonガイド
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Convert docx to markdown using Python. Learn to extract images from
    Word and save markdown output with a custom callback.
  headline: Convert docx to markdown – Complete Python Guide with Image Extraction
  type: TechArticle
- description: Convert docx to markdown using Python. Learn to extract images from
    Word and save markdown output with a custom callback.
  name: Convert docx to markdown – Complete Python Guide with Image Extraction
  steps:
  - name: Expected Output
    text: '```markdown # Sample Document'
  - name: Quick sanity check
    text: '```bash # On Unix/macOS cat YOUR_DIRECTORY/output.md ls YOUR_DIRECTORY/images/
      ```'
  - name: Dealing with duplicate image names
    text: 'Word sometimes reuses the same internal name for different pictures. To
      avoid overwriting, you can tweak `image_saver`:'
  - name: Converting large documents
    text: 'For multi‑megabyte documents, consider streaming the output to avoid memory
      spikes:'
  type: HowTo
tags:
- Python
- Aspose.Words
- Document Conversion
title: docx を markdown に変換 – 画像抽出付き完全 Python ガイド
url: /ja/python/document-conversion/convert-docx-to-markdown-complete-python-guide-with-image-ex/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# docx を markdown に変換 – 画像抽出付き完全 Python ガイド

Word ファイルに埋め込まれた画像を失わずに **docx を markdown に変換** したいと思ったことはありませんか？ あなただけではありません。多くの開発者が、変換時に画像が失われ、markdown に壊れたリンクや、最悪の場合画像が全く表示されないという壁にぶつかります。

朗報です！ Python と Aspose.Words を数行書くだけで、`.docx` をきれいな markdown にシームレスに変換し、画像を任意のフォルダーに抽出できます。このチュートリアルでは、ライブラリのインストールから、画像を保存するコールバックを設定して希望の場所に保存するまで、全工程を解説します。

このガイドを終える頃には、**Word を markdown に変換**し、すべての画像を取り出し、**markdown 出力を保存**できるようになります。静的サイトジェネレーター、ドキュメントパイプライン、あるいは markdown‑first のワークフローにすぐに活用できます。

## 必要なもの

- Python 3.8 以上（コードは 3.9+ でも動作）  
- `pip` でサードパーティーパッケージをインストールできる環境  
- 有効な Aspose.Words for Python ライセンス（評価用の無料トライアルで可）  
- テキストと少なくとも 1 つの画像を含むサンプル `input.docx`  

以上です—重い Office のインストールや COM 連携は不要、純粋な Python だけです。

## Step 1: Aspose.Words for Python をインストール

まずはライブラリを取得します。ターミナルで次のコマンドを実行してください。

```bash
pip install aspose-words
```

権限エラーが出た場合は `--user` を付けるか、仮想環境を使用してください。インストールが完了すると、`aspose.words` パッケージ（例では `aw` としてインポート）を利用できるようになります。

> **プロのコツ:** `requirements.txt` を整えておきましょう。`aspose-words==<latest-version>` を追加すれば、共同作業者が環境を正確に再現できます。

## Step 2: カスタム画像保存コールバックを設定

Aspose.Words では *リソース保存コールバック* を使って保存パイプラインにフックできます。これは、各画像のバイトストリームを受け取り、生成された markdown ファイル内での参照先を指示するミドルマンのようなものです。

コールバックの核心は次の通りです：

```python
# Step 1: Define a callback to store extracted images in a custom folder
def image_saver(image_bytes, image_name):
    """
    Saves an image to YOUR_DIRECTORY/images/ and returns the relative path
    that will be placed in the markdown file.
    """
    # Ensure the target folder exists
    import os
    target_dir = os.path.join("YOUR_DIRECTORY", "images")
    os.makedirs(target_dir, exist_ok=True)

    # Build the full path on disk
    file_path = os.path.join(target_dir, image_name)

    # Write the raw image bytes to disk
    with open(file_path, "wb") as f:
        f.write(image_bytes)

    # Return the path that markdown will use (relative to the .md file)
    return os.path.join("images", image_name)
```

**この仕組みが重要な理由:**  
- **制御** – フォルダー構成や命名規則、必要なら画像形式の変換まで自由に決められます。  
- **可搬性** – 返却する相対パスにより、`images` フォルダーさえ同梱すればマシン間で markdown がそのまま機能します。  
- **パフォーマンス** – 各画像に対して一度だけコールバックが実行され、重複書き込みを防ぎます。

## Step 3: Markdown 保存オプションを構成

次に、`MarkdownSaveOptions` オブジェクトにコールバックを結び付けます。これにより、Aspose.Words は画像リソースに遭遇したときに `image_saver` を使用します。

```python
# Step 2: Create Markdown save options and attach the callback
md_options = aw.saving.MarkdownSaveOptions()
md_options.resource_saving_callback = image_saver
```

ここで `export_images_as_base64`（別ファイルにしたいので `False` に設定）や、目次が必要な場合は `add_table_of_contents` など、いくつかのオプションを調整できます。このガイドではデフォルト設定のまま進めます。

## Step 4: ソースの Word 文書を読み込む

`.docx` の読み込みはシンプルです。ファイルパスを Aspose.Words に渡すだけです：

```python
# Step 3: Load the source Word document
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

文書が大きい場合は `aw.LoadOptions` を使ってストリーミング読み込みを検討できますが、ほとんどのケースではシンプルなコンストラクタで十分です。

## Step 5: Markdown として保存 – コールバックに全て任せる

最後に、Aspose.Words に markdown ファイルを書き出すよう指示します。ライブラリは埋め込み画像ごとに `image_saver` を呼び出し、ファイルを保存し、適切な markdown 画像リンクを埋め込みます。

```python
# Step 4: Save the document as Markdown, letting the callback handle image resources
doc.save("YOUR_DIRECTORY/output.md", md_options)
```

処理が完了すると次の 2 つが生成されます：

1. `output.md` – `![](images/image1.png)` のような画像リンクを含む markdown テキスト  
2. `images` サブフォルダー – 抽出された画像がすべて格納されます

### 期待される出力

```markdown
# Sample Document

This is a paragraph from the Word file.

![](images/image1.png)

Another paragraph follows the picture.
```

任意の markdown プレビューア（VS Code、GitHub、MkDocs など）で `output.md` を開くと、元の Word ファイルと同じように画像が表示されます。

## Step 6: 結果を検証し、エッジケースに対処

### 簡易サニティチェック

```bash
# On Unix/macOS
cat YOUR_DIRECTORY/output.md
ls YOUR_DIRECTORY/images/
```

画像ファイル名が markdown 内のパスと一致しているか確認してください。画像が欠落している場合は、コールバックが **相対** パスを返しているか（絶対パスではないか）と、`images` フォルダーが正しく参照されているかを再確認しましょう。

### 重複画像名への対処

Word は異なる画像に同じ内部名を付与することがあります。上書きを防ぐために、`image_saver` を次のように調整できます：

```python
import uuid

def image_saver(image_bytes, image_name):
    unique_name = f"{uuid.uuid4().hex}_{image_name}"
    # rest of the code uses unique_name instead of image_name
    ...
    return os.path.join("images", unique_name)
```

### 大容量文書の変換

数メガバイト規模の文書では、メモリスパイクを防ぐために出力をストリーミングすることを検討してください：

```python
with open("YOUR_DIRECTORY/output.md", "w", encoding="utf-8") as out_file:
    doc.save(out_file, md_options)
```

Aspose.Words は内部でストリーミングを処理するので、markdown 全体を RAM に読み込む必要はありません。

## Step 7: ワークフローを自動化（任意）

フォルダー内の複数の Word ファイルを一括処理したい場合は、ロジックをループで包みます：

```python
import glob

for doc_path in glob.glob("YOUR_DIRECTORY/*.docx"):
    doc = aw.Document(doc_path)
    base_name = os.path.splitext(os.path.basename(doc_path))[0]
    md_path = f"YOUR_DIRECTORY/{base_name}.md"
    doc.save(md_path, md_options)
    print(f"Converted {doc_path} → {md_path}")
```

これで `.docx` を 100 件ほどディレクトリに投入すれば、スクリプトが自動的に処理し、各ファイルに対応した `images` サブフォルダーが作成されます。

## 結論

画像をすべて保持しながら **docx を markdown に変換**する方法を、シンプルな Python スクリプトと Aspose.Words の強力なコールバック機構を使って解説しました。これで以下が実現できます：

- カスタム `resource_saving_callback` で **Word から画像を抽出**  
- 最小構成で **Word を markdown に変換**  
- 整然とした画像フォルダーと共に **markdown 出力を保存**  

ここからは、テーブルや脚注といった追加の markdown 拡張機能を試したり、CI パイプラインに組み込んで自動的にドキュメントをビルドしたりできます。可能性は無限大です—画像保存ロジックを柔軟に保てば、markdown は常に整然と保たれます。

エッジケースやライセンスに関する質問があれば、下のコメント欄にどうぞ。Happy coding!

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには、ステップバイステップの解説と完全なコード例が含まれているので、API の追加機能をマスターしたり、別の実装アプローチを自分のプロジェクトに取り入れたりするのに役立ちます。

- [How to Save Markdown from Word – Complete Python Guide](/words/english/python-net/document-conversion/how-to-save-markdown-from-word-complete-python-guide/)
- [Convert Docx File To Markdown](/words/english/net/basic-conversions/docx-to-markdown/)
- [Convert Word to Markdown – Embed Images as Base64](/words/english/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}