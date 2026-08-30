---
category: general
date: 2026-05-30
description: Pythonで形状タグ付け付きのWordをPDFとして保存。docxをPDFに変換し、PDFをアクセシブルにし、アクセシビリティ向上のためにフローティングシェイプにタグ付けする方法を学ぶ。
draft: false
keywords:
- save word as pdf
- convert docx to pdf
- convert word document pdf
- make pdf accessible
- how to tag shapes
language: ja
og_description: PythonでWordをPDFに変換し、アクセシビリティのためにフローティングシェイプにタグ付け。docxをPDFに変換し、数分でPDFをアクセシブルにする方法を学びましょう。
og_title: Shapeタグ付けでWordをPDFに保存 – 完全Pythonガイド
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Save Word as PDF with shape tagging in Python. Convert docx to pdf,
    make pdf accessible, and learn how to tag floating shapes for better accessibility.
  headline: Save Word as PDF with Shape Tagging – Full Python Guide
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for Python via .NET runs on .NET Core, which is cross‑platform.
      Just install the appropriate runtime (`dotnet-sdk-6.0` or later) and the `aspose-words`
      package.
    question: Does this work on Linux?
  - answer: Absolutely. Wrap the `convert_word_to_accessible_pdf` call in a `for`
      loop that iterates over `os.listdir()` and filters for `*.docx`.
    question: Can I batch‑process a folder of .docx files?
  - answer: Iterate over `doc.get_child_nodes(aw.NodeType.SHAPE, True)` and set `shape.title`
      or `shape.alternative_text` before saving.
    question: What if I need to add custom alt text to each shape?
  - answer: 'The inline tagging respects the original layout; however, if you enable
      PDF/A compliance, some visual tweaks (like color profiles) might be applied
      automatically. ## Wrapping Up We’ve just covered how to **save Word as PDF**
      while ensuring that floating shapes are tagged correctly for accessibility.'
    question: Is there a way to keep the original layout exactly the same?
  type: FAQPage
tags:
- Aspose.Words
- PDF conversion
- Python
- Document automation
title: Shapeタグ付けでWordをPDFとして保存 – 完全Pythonガイド
url: /ja/python/document-conversion/save-word-as-pdf-with-shape-tagging-full-python-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 形状タグ付け付きで Word を PDF として保存 – 完全な Python ガイド

Word を **PDF に保存** しながら、浮動する形状をアクセシブルに保つ方法を考えたことはありませんか？ あなただけではありません。コンプライアンスが厳しい環境では、単なる PDF だけでは不十分です。スクリーンリーダーは適切なタグ付けが必要で、特にテキスト上に浮かんでいる形状は重要です。

このチュートリアルでは、**docx を pdf に変換** し、PDF のオプションを設定して視覚的に正しいだけでなくアクセシブルになるようにし、最後に形状を正しくタグ付けする完全な実行可能サンプルを順を追って解説します。最後まで読めば、任意の Python プロジェクトに組み込めるワンファイルのソリューションが手に入ります。

## 学べること

- 浮動形状（画像、テキストボックス、図）を含む Word 文書の読み込み  
- Aspose.Words for Python via .NET を使用して **Word 文書を pdf に変換** し、カスタムタグ付けを実施  
- *インライン* タグ付けモードを有効にして、PDF がアクセシビリティ基準を満たすようにする  
- 結果の検証方法と、フォント欠損や画像サイズ過大といった一般的な落とし穴への対処  

外部サービス不要、難解なコマンドライン操作も不要 — 純粋な Python コードと数行の解説だけです。

## 前提条件

作業を始める前に以下を用意してください。

| 必要条件 | 理由 |
|-------------|--------|
| Python 3.9+ | Aspose .Words for Python via .NET パッケージが要求するバージョン |
| `aspose-words` NuGet パッケージ（`pip install aspose-words` でインストール） | サンプルで使用する `aw` 名前空間を提供 |
| 少なくとも 1 つの浮動形状（例：テキストボックス）を含む `.docx` ファイル | タグ付け機能のデモンストレーション |
| 任意：PDF/A‑1a バリデータ（例：veraPDF） | アクセシビリティを正式に認証したい場合に使用 |

Aspose.Words は、組み込みの `python-docx` ライブラリよりもはるかに強力な「スイスアーミーナイフ」的存在です。特に PDF 出力を細かく制御したいときに威力を発揮します。

## 手順 1: Aspose.Words のインストールとインポート

まずはライブラリをインストールし、必要なクラスをインポートします。このステップは短いですが、抜かすと後で `ImportError` が発生します。

```bash
pip install aspose-words
```

```python
# Step 1: Import the Aspose.Words namespace
import aspose.words as aw
```

> **プロのコツ:** 仮想環境を使用している場合は、`pip` コマンドを実行する前に環境をアクティベートしてください。これによりプロジェクトの依存関係が整理されます。

## 手順 2: 浮動形状を含む Word 文書をロード

次に、実際にソースファイルを開きます。`Document` コンストラクタはパスまたはストリームを受け取るので、ローカルファイルでも S3 オブジェクトでも好きなものを渡せます。

```python
# Step 2: Load the source .docx
input_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(input_path)
```

> **なぜ重要か:** 文書をロードすると内部ノードツリーにアクセスでき、浮動形状は `Shape` オブジェクトとして表現されています。ファイルが存在しない場合、Aspose は `FileNotFoundError` をスローするので、適切にキャッチしてハンドリングしてください。

## 手順 3: アクセシブルな形状タグ付けのための PDF 保存オプションを設定

ここがチュートリアルの核心です。デフォルトでは Aspose.Words は浮動形状を *ブロックレベル* タグとして保存しますが、多くの支援技術はこれを別個の非読順要素として扱います。`export_floating_shapes_as_inline_tag` を `True` に設定すると、形状が *インライン* タグとして扱われ、読順が保持されスクリーンリーダーの体験が向上します。

```python
# Step 3: Create PDF save options and enable inline shape tagging
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.export_floating_shapes_as_inline_tag = True   # True → inline (accessible) tagging
```

> **動作概要:** `export_floating_shapes_as_inline_tag` が `True` の場合、Aspose は各形状の周囲に `<Figure>` タグを挿入し、文書フロー内に配置します。これは **make pdf accessible** コンプライアンス、特に WCAG 2.1 ガイドライン 1.3.1 に推奨されるアプローチです。

### オプション設定例

| オプション | 説明 | 典型的な値 |
|--------|-------------|---------------|
| `pdf_opts.compliance` | PDF/A コンプライアンスレベルを設定（例: PDF/A‑1a） | `aw.saving.PdfCompliance.PDF_A_1A` |
| `pdf_opts.embed_full_fonts` | 置換を防ぐために使用フォントをすべて埋め込む | `True` |
| `pdf_opts.save_format` | 出力形式を強制指定（後で XPS に切り替える場合に便利） | `aw.SaveFormat.PDF` |

プロジェクトの要件が厳しい場合は、これらの設定をチェーンして使用できます。

## 手順 4: 設定したオプションで PDF として保存

最後に、出力ファイルを書き出します。`save` メソッドは保存先パスと先ほど構成したオプションオブジェクトを受け取ります。

```python
# Step 4: Save the document as a PDF with the accessible tagging options
output_path = "YOUR_DIRECTORY/output.pdf"
doc.save(output_path, pdf_opts)
print(f"✅ PDF saved to {output_path}")
```

これで **convert word document pdf** の操作は完了です。生成された PDF には浮動形状がインラインでタグ付けされ、支援技術に対して格段にフレンドリーになります。

## アクセシブル PDF の検証

PDF が本当にアクセシビリティ基準を満たしているか確認したい場合は、Adobe Acrobat Pro で **Tags** パネルを開きます。以下のようなエントリが表示されるはずです。

```
/Figure
  /Alt (optional alt text you may have set)
  /Para
```

あるいはコマンドラインバリデータを実行します。

```bash
verapdf --format text output.pdf
```

バリデータが「No errors」を返せば、**make pdf accessible** に成功したことになります。

## よくあるエッジケースと対処法

| 状況 | 起こり得る問題 | 推奨対策 |
|-----------|---------------------|---------------|
| **文書に高解像度画像が多数含まれる** | PDF サイズが膨張し、パフォーマンスが低下 | `pdf_opts.jpeg_quality = 80` に設定するか、`doc.get_child_nodes(aw.NodeType.SHAPE, True)` で画像を縮小してから保存 |
| **サーバーにフォントが欠損している** | 代替フォントで表示され、レイアウトが崩れる | `pdf_opts.embed_full_fonts = True` を有効にし、必要なフォントを OS にインストール |
| **形状に代替テキストが設定されていない** | 支援技術が「Figure」だけを読み上げ、説明が欠如 | 保存前に形状を走査し、`shape.title = "説明"` を設定 |
| **大容量文書（>100 MB）** | 32 ビットランタイムでメモリ不足エラー | `PdfSaveOptions.memory_usage_setting = aw.saving.MemoryUsageSetting.LOW` を使用してストリーミング保存 |
| **PDF/A‑2b が必要** | コンプライアンスが PDF/A‑1a と不一致 | `pdf_opts.compliance = aw.saving.PdfCompliance.PDF_A_2B` に変更 |

早めにこれらのシナリオに対処すれば、後からの手戻りを防げます。

## 完全動作サンプル

以下は `convert_to_accessible_pdf.py` というファイル名で保存できる、完全なスクリプトです。`YOUR_DIRECTORY` を実際のフォルダパスに置き換えてください。

```python
import aspose.words as aw

def convert_word_to_accessible_pdf(input_docx: str, output_pdf: str) -> None:
    """
    Loads a Word document, configures PDF save options to tag floating shapes inline,
    and saves the result as an accessible PDF.
    """
    # Load the .docx file
    doc = aw.Document(input_docx)

    # Configure PDF options for accessible shape tagging
    pdf_opts = aw.saving.PdfSaveOptions()
    pdf_opts.export_floating_shapes_as_inline_tag = True   # Inline tagging for accessibility
    pdf_opts.compliance = aw.saving.PdfCompliance.PDF_A_1A  # Optional: enforce PDF/A‑1a
    pdf_opts.embed_full_fonts = True                       # Ensure fonts are embedded

    # Save the PDF
    doc.save(output_pdf, pdf_opts)
    print(f"✅ Successfully saved accessible PDF to: {output_pdf}")

if __name__ == "__main__":
    # Adjust these paths as needed
    INPUT_PATH = "YOUR_DIRECTORY/input.docx"
    OUTPUT_PATH = "YOUR_DIRECTORY/output.pdf"

    convert_word_to_accessible_pdf(INPUT_PATH, OUTPUT_PATH)
```

スクリプト実行例:

```bash
python convert_to_accessible_pdf.py
```

実行すると確認メッセージが表示され、`output.pdf` にはスクリーンリーダー向けにインラインタグ付けされた形状が含まれます。

## FAQ

**Q: Linux でも動作しますか？**  
A: はい。Aspose.Words for Python via .NET は .NET Core 上で動作し、クロスプラットフォームです。適切なランタイム（`dotnet-sdk-6.0` 以降）と `aspose-words` パッケージをインストールすれば OK です。

**Q: .docx ファイルが入ったフォルダを一括処理したいです。**  
A: 可能です。`convert_word_to_accessible_pdf` 呼び出しを `for` ループでラップし、`os.listdir()` で `*.docx` をフィルタリングしてください。

**Q: 各形状にカスタム代替テキストを付与したい場合は？**  
A: `doc.get_child_nodes(aw.NodeType.SHAPE, True)` を走査し、保存前に `shape.title` または `shape.alternative_text` を設定します。

**Q: 元のレイアウトを完全に保持したいですか？**  
A: インラインタグ付けはレイアウトをそのまま保持しますが、PDF/A コンプライアンスを有効にすると色プロファイルなどの微調整が自動的に適用されることがあります。

## まとめ

**Word を PDF として保存** し、浮動形状が正しくタグ付けされたアクセシブルな PDF を作成する方法を解説しました。手順は「ロード → 設定 → 保存」の 3 ステップです。

## 次に学ぶべきこと

- [Create Accessible PDF from Word – Convert to PDF/UA](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-word-convert-to-pdf-ua/)
- [Save Word as PDF with Aspose.Words – Complete C# Guide](/words/english/net/basic-conversions/save-word-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}