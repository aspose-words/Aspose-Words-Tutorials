---
category: general
date: 2026-06-21
description: Python を使用して Word を Markdown にエクスポートし、Word から画像を保存します。docx を Markdown
  に変換する方法、Python でバイナリファイルを書き込む方法、docx から画像を抽出する方法を学びましょう。
draft: false
keywords:
- export word to markdown
- convert docx to markdown
- save images from word
- write binary file python
- how to extract images from docx
language: ja
og_description: Word を Markdown にエクスポートし、Word から画像を自動的に保存します。このステップバイステップガイドでは、docx
  を Markdown に変換する方法、Python でバイナリファイルを書き込む方法、そして docx から画像を抽出する方法を紹介します。
og_title: Word を Markdown にエクスポート – 完全な Python チュートリアル
schemas:
- author: Aspose
  dateModified: '2026-06-21'
  description: Export Word to Markdown and save images from Word using Python. Learn
    how to convert docx to markdown, write binary file python, and extract images
    from docx.
  headline: Export Word to Markdown – Full Guide with Image Extraction in Python
  type: TechArticle
- description: Export Word to Markdown and save images from Word using Python. Learn
    how to convert docx to markdown, write binary file python, and extract images
    from docx.
  name: Export Word to Markdown – Full Guide with Image Extraction in Python
  steps:
  - name: Expected Output Example
    text: 'If `input.docx` contained a single picture named `image1.png`, the resulting
      `output.md` might look like:'
  - name: What if the document has duplicate image names?
    text: 'Aspose.Words will suggest the same name for identical images. Our callback
      uses the suggested name directly, which could cause overwrites. To avoid that,
      modify the callback to append a unique identifier:'
  - name: Can I change the image format during extraction?
    text: Absolutely. After writing the binary data, you could open it with Pillow
      (`PIL.Image`) and save it as a different format (e.g., JPEG). This is useful
      when you need to **convert docx to markdown** for a web‑optimized site.
  - name: Does this work on macOS/Linux as well as Windows?
    text: Yes. The code uses `os.path` and avoids hard‑coded path separators, so it’s
      cross‑platform. Just remember to grant the script write permissions to the target
      directory.
  - name: What if I need to export tables or footnotes too?
    text: '`MarkdownSaveOptions` supports a range of features—tables become markdown
      tables, footnotes become inline references. No extra code is required; just
      experiment with the generated markdown to see how it renders.'
  type: HowTo
tags:
- python
- docx
- markdown
- image-extraction
title: Word を Markdown にエクスポート – Python で画像抽出を行う完全ガイド
url: /ja/python/document-conversion/export-word-to-markdown-full-guide-with-image-extraction-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Export Word to Markdown – Full Guide with Image Extraction in Python

Word 文書から画像を失わずに **export Word to markdown** したいと思ったことはありませんか？同じ悩みを抱える開発者は多く、`.docx` からクリーンな markdown へ、埋め込まれた画像をすべて保持したまま移行したいという要望が頻繁に寄せられます。  

このチュートリアルでは、**convert docx to markdown** だけでなく **save images from word** ファイルも抽出できる、純粋な Python ソリューションをステップバイステップで解説します。最後まで実行できるスクリプトが完成し、バイナリファイルを書き出す python スタイルと、必要なすべての画像を取得できるようになります。

## What This Guide Covers

- Aspose.Words for Python の正しいインストール方法  
- バイナリデータを書き込むコールバックの定義  
- 画像処理付きで Word 文書を markdown に変換  
- 出力結果の検証と、よくある落とし穴のトラブルシューティング  

外部サービスは不要、手動でのコピー＆ペーストも不要です。プロジェクトにそのまま組み込める単一スクリプトが完成します。

## Prerequisites

始める前に以下を用意してください。

| Requirement | Why it matters |
|-------------|----------------|
| Python 3.8+ | Modern syntax and type hints |
| `pip` access | To install the Aspose.Words package |
| Write permission to a folder | The callback will **write binary file python** style |
| A `.docx` file with images | To see the **save images from word** feature in action |

これらに心当たりがなくても安心してください。次のステップで設定方法を詳しく説明します。

## Step 1: Install Aspose.Words for Python via pip

Aspose.Words は、埋め込みメディアを含む Word 文書全体を理解できる強力なライブラリです。以下のコマンドでインストールします。

```bash
pip install aspose-words
```

> **Pro tip:** 仮想環境 (`python -m venv venv`) を使うと依存関係が整理され、他のプロジェクトとのバージョン衝突も防げます。

## Step 2: Create a Resource‑Saving Callback (Write Binary File Python)

このソリューションの核心は、画像などのバイナリリソースを受け取り保存先を決定するコールバックです。ここで **write binary file python** スタイルを実装します。

```python
def my_resource_saver(resource: bytes, suggested_name: str) -> str:
    """
    Save a binary resource (e.g., an image) to a custom folder and
    return the relative path for markdown linking.

    :param resource: Raw binary data of the resource.
    :param suggested_name: A filename suggested by Aspose.Words.
    :return: Relative path to be used in the markdown file.
    """
    # Build a relative path inside a custom folder.
    folder = "custom_images"
    os.makedirs(folder, exist_ok=True)          # Ensure the folder exists.
    file_path = os.path.join(folder, suggested_name)

    # Write the binary data to disk – classic write binary file python.
    with open(file_path, "wb") as f:
        f.write(resource)

    # Return the path so the Markdown writer can reference it.
    return file_path
```

**Why a callback?**  
Aspose.Words は画像の保存場所を知りません。`my_resource_saver` を渡すことで、ファイル名やフォルダ構造、さらには画像圧縮といった後処理まで自由にコントロールできます。

## Step 3: Load the Source Word Document

次に、変換したい `.docx` ファイルをライブラリに読み込ませます。

```python
import aspose.words as aw
import os

# Adjust the path to your actual file location.
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)
```

ファイルが見つからない場合は、パスを再確認し、スクリプトに読み取り権限があるか確認してください。Windows でスラッシュが混在するミスは `os.path.join` が自動で対処します。

## Step 4: Configure Markdown Save Options and Attach the Callback

ここで全体を結び付けます。Aspose.Words に markdown 出力を指示し、画像が見つかったときに `my_resource_saver` を呼び出すよう設定します。

```python
# Create Markdown save options.
md_save = aw.saving.MarkdownSaveOptions()

# Attach the resource‑saving callback.
md_save.resource_saving_callback = my_resource_saver
```

markdown の出力設定はここで調整可能です（例: `md_save.export_images_as_base64 = False` にすれば画像は埋め込みではなく別ファイルになります）。**how to extract images from docx** の目的であれば、別ファイルとして保存する方が一般的に扱いやすいです。

## Step 5: Export the Document – The Final Export Word to Markdown Call

残るは、実際に変換を実行するワンライナーです。

```python
output_md = "YOUR_DIRECTORY/output.md"
doc.save(output_md, md_save)
print(f"✅ Markdown saved to {output_md}")
print(f"🖼️ Images stored in ./custom_images/")
```

スクリプトを実行すると、`output.md` と同階層に `custom_images` フォルダが作成され、元の Word ファイルに含まれていたすべての画像が格納されます。markdown では相対パスで画像が参照されるため、静的サイトジェネレータや GitHub のレンダリングでもそのまま利用できます。

### Expected Output Example

`input.docx` に `image1.png` という画像が 1 枚だけ含まれていた場合、生成される `output.md` は次のようになります。

```markdown
# Sample Document

Here is an illustration:

![image1.png](custom_images/image1.png)

More text follows...
```

フォルダ構成は以下の通りです。

```
/YOUR_DIRECTORY/
│─ input.docx
│─ output.md
└─ custom_images/
   └─ image1.png
```

## Common Questions & Edge Cases

### What if the document has duplicate image names?

同一画像に対して Aspose.Words は同じ名前を提案します。コールバックがそのまま使用すると上書きされてしまう可能性があります。回避策として、コールバックで一意な識別子を付加してください。

```python
import uuid

def my_resource_saver(resource, suggested_name):
    unique_name = f"{uuid.uuid4().hex}_{suggested_name}"
    # rest of the code unchanged...
```

### Can I change the image format during extraction?

もちろん可能です。バイナリを書き出した後に Pillow (`PIL.Image`) で読み込み、別フォーマット（例: JPEG）で保存すれば、**convert docx to markdown** したサイト向けに画像を最適化できます。

### Does this work on macOS/Linux as well as Windows?

はい。`os.path` を使用し、パス区切り文字をハードコーディングしていないため、クロスプラットフォームで動作します。対象ディレクトリへの書き込み権限だけは確保してください。

### What if I need to export tables or footnotes too?

`MarkdownSaveOptions` は多数の機能をサポートしています。テーブルは markdown のテーブル形式に、脚注はインライン参照に変換されます。追加コードは不要なので、生成された markdown を確認しながら調整してください。

## Full Script – Ready to Copy & Paste

以下に、今回説明したすべてを網羅した実行可能なサンプルを示します。`export_word_to_md.py` として保存し、`python export_word_to_md.py` で実行してください。

```python
import os
import uuid
import aspose.words as aw

def my_resource_saver(resource: bytes, suggested_name: str) -> str:
    """
    Save binary resources (images) to a custom folder and return
    the relative path for markdown references.
    """
    folder = "custom_images"
    os.makedirs(folder, exist_ok=True)

    # Ensure unique filenames to avoid collisions.
    unique_name = f"{uuid.uuid4().hex}_{suggested_name}"
    file_path = os.path.join(folder, unique_name)

    with open(file_path, "wb") as f:
        f.write(resource)

    return file_path

def main():
    # ------------------------------------------------------------------
    # 1️⃣ Load the Word document you want to convert.
    # ------------------------------------------------------------------
    doc_path = "YOUR_DIRECTORY/input.docx"
    if not os.path.isfile(doc_path):
        raise FileNotFoundError(f"❌ {doc_path} does not exist.")
    doc = aw.Document(doc_path)

    # ------------------------------------------------------------------
    # 2️⃣ Set up markdown options and plug in the image callback.
    # ------------------------------------------------------------------
    md_save = aw.saving.MarkdownSaveOptions()
    md_save.resource_saving_callback = my_resource_saver

    # ------------------------------------------------------------------
    # 3️⃣ Perform the export – this is the core **export word to markdown** step.
    # ------------------------------------------------------------------
    output_md = "YOUR_DIRECTORY/output.md"
    doc.save(output_md, md_save)

    print(f"✅ Markdown exported to: {output_md}")
    print(f"🖼️ Extracted images are in the folder: ./custom_images/")

if __name__ == "__main__":
    main()
```

実行後、任意の markdown ビューアで `output.md` を開くと、元の Word のテキスト、見出し、**save images from word**、その他すべての要素が忠実に再現されていることが確認できます。

## Conclusion

ここでは、埋め込み画像をすべて保持しながら **export word to markdown** する堅牢な方法を示しました。Aspose.Words とカスタム **resource‑saving callback** を組み合わせることで、**convert docx to markdown**、**write binary file python**、そして **how to extract images from docx** の疑問にシングルスクリプトで答えることができます。

次のステップとして、Pillow で画像圧縮を行う処理を追加したり、CI パイプラインに組み込んでドキュメントを自動変換したりしてみてください。可能性は無限大です。ぜひこの土台を活用して、より高度な自動化に挑戦してください。

ご意見や問題があればコメントで教えてください—Happy coding!

## What Should You Learn Next?

以下のチュートリアルは、本ガイドで学んだテクニックを応用した関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれており、API の追加機能習得や代替実装の探索に役立ちます。

- [How to Save Markdown from Word – Complete Python Guide](/words/english/python-net/document-conversion/how-to-save-markdown-from-word-complete-python-guide/)
- [Recover Corrupted DOCX & Convert Word to Markdown](/words/english/python-net/document-conversion/recover-corrupted-docx-convert-word-to-markdown/)
- [Save Word Images – Convert Word to Markdown with Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}