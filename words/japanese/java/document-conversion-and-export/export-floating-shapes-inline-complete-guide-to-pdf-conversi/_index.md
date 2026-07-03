---
category: general
date: 2026-07-03
description: Word を PDF にインライン変換する際に、フローティング シェイプをインラインでエクスポートします。Java で PDF オプションを設定し、Word
  を PDF として保存する方法を学びましょう。
draft: false
keywords:
- export floating shapes inline
- convert word to pdf inline
- how to set pdf options
- save word as pdf options
language: ja
og_description: Word文書をPDFに変換する際に、浮動形状をインラインでエクスポートします。このチュートリアルでは、PDFオプションの設定方法と、WordをPDFとして保存するオプションの設定方法を示します。
og_title: インラインでフローティングシェイプをエクスポート – Java PDF変換ガイド
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  headline: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  type: TechArticle
- description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  name: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  steps:
  - name: 1. “What if my document contains complex SmartArt?”
    text: SmartArt is treated as a drawing object. The inline flag works for most
      vector shapes, but very intricate SmartArt may still be rendered as an image.
      In those cases, consider flattening the SmartArt in Word before conversion,
      or use `pdfOptions.setExportSmartArtAsImage(true)` to force image export.
  - name: 2. “Can I combine inline and block exports in the same document?”
    text: Unfortunately the API applies the setting globally. If you need mixed behavior,
      split the document into sections, export each section separately with different
      options, then merge the PDFs using `PdfMerger`.
  - name: 3. “Does this affect font embedding?”
    text: No. Font embedding is controlled by `pdfOptions.setEmbedFullFonts(true)`
      (default). You can safely enable or disable it without touching the inline shape
      flag.
  - name: 4. “How do I verify that shapes are really `<span>`?”
    text: Open the resulting PDF in a tool like **PDF.js** or **Adobe Acrobat** →
      **Edit PDF** → **Object Inspector**. You’ll see the shape wrapped in a `<span>`
      element in the underlying XML. If you see `<div>`, the option wasn’t applied.
  type: HowTo
tags:
- Java
- PDF
- Aspose.Words
title: インラインでフローティングシェイプをエクスポート – PDF変換完全ガイド
url: /ja/java/document-conversion-and-export/export-floating-shapes-inline-complete-guide-to-pdf-conversi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# インラインで浮動形状をエクスポート – PDF変換の完全ガイド

Word文書をPDFに変換するときに**インラインで浮動形状をエクスポート**する必要がありましたか？ あなたは一人ではありません—多くの開発者が、図やアイコンが謎のように別レイヤーに移動してしまう問題に直面しています。 良いニュースは、単一のPDFオプションでこれらの形状を `<span>` タグ内にしっかり収め、Wordで見た通りにレイアウトを保持できることです。

このチュートリアルでは、Javaで**PDFオプションを設定する方法**を順を追って説明し、**WordをPDFとして保存するオプション**の正確なコードを示し、デフォルトのブロックレベルエクスポートではなく**インラインでWordをPDFに変換**したい理由を解説します。最後まで読むと、MavenやGradleプロジェクトにすぐ組み込める実行可能なスニペットが手に入ります。

## 学習内容

- 浮動形状のインライン `<span>` とブロック `<div>` エクスポートの違い。  
- `PdfSaveOptions` を設定してインライン描画を強制する方法。  
- `.docx` を読み込み、オプションを適用し、PDFとして書き出すステップバイステップのコード。  
- 一般的な落とし穴（フォントが欠如、未対応の形状）とその回避策。  
- 出力のテスト方法や、他のドキュメント要素へのアプローチ拡張のヒント。

**前提条件** – Java 8 以降、Aspose.Words for Java ライブラリ（または `PdfSaveOptions` クラスと同等の API）、そして浮動形状を含むサンプル Word ファイル（本チュートリアルでは `FloatingShapes.docx` を使用）を用意してください。その他の外部ツールは不要です。

---

## 手順 1: ソース Word ドキュメントを読み込む

最初に行うのは、変換したい `.docx` を開くことです。これは簡単ですが、パスが絶対パスであるか、クラスパスから正しく解決されていることを確認してください。

```java
import com.aspose.words.Document;

// Step 1: Load the source Word document
Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");
```

*この点が重要な理由:*  
ドキュメントが正しく読み込まれない場合、続く PDF 変換で `FileNotFoundException` がスローされます。`Document` を使用することで、ページ上に存在する浮動形状を含む内部オブジェクトモデルが完全に構築されます。

## 手順 2: PDF 保存オプションを作成し、浮動形状をインラインに設定する

ここがポイントです。デフォルトでは Aspose.Words は浮動形状をブロックレベルの `<div>` 要素としてエクスポートし、HTML ベースの PDF ではフローが崩れることがあります。`setExportFloatingShapesAsInlineTag(true)` を設定すると、エンジンは各形状をインラインの `<span>` でラップします。

```java
import com.aspose.words.PdfSaveOptions;

// Step 2: Create PDF save options and set floating shapes to be exported as inline <span> elements
PdfSaveOptions pdfOptions = new PdfSaveOptions();
pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → <span>, false → <div>
```

*この点が重要な理由:*  
- **レイアウト忠実度** – インラインタグは形状を周囲のテキストと整列させ、不要な隙間を防ぎます。  
- **検索可能性** – インライン要素は PDF リーダーによって正しくインデックスされやすくなります。  
- **スタイリング制御** – 後で PDF を HTML に変換する場合、CSS で `<span>` を対象にできます。

> **プロのコツ:** 特定のドキュメントで従来のブロック動作が必要な場合は、`false` を渡すか、呼び出し自体を省略してください。

## 手順 3: 設定したオプションでドキュメントを PDF として保存する

ここで、読み込んだ `Document` と `PdfSaveOptions` を組み合わせてファイルを書き出します。この1行が主要な処理を行います。

```java
// Step 3: Save the document as a PDF using the configured options
doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);
```

*この点が重要な理由:*  
`save` メソッドは `pdfOptions` に設定したすべてのフラグを尊重します。オプションを渡し忘れるとデフォルトのブロックエクスポートに戻り、**インラインで浮動形状をエクスポート**する目的が失われます。

## 完全動作サンプル

すべてをまとめたコンパクトなプログラムですぐにコンパイルして実行できます。`YOUR_DIRECTORY` を実際のパスに置き換えてください。

```java
import com.aspose.words.*;

public class ExportFloatingShapesInlineDemo {
    public static void main(String[] args) {
        try {
            // Load the source Word document
            Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");

            // Configure PDF options to export floating shapes as inline <span>
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true);

            // Save as PDF with the above options
            doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);

            System.out.println("PDF created successfully with inline floating shapes.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**期待される出力** – プログラム実行後、`FloatingShapes.pdf` を開きます。形状がテキストにぴったり寄り添って表示され、余分な空白がなく、PDF の内部構造を確認すれば各形状が `<span>` タグで囲まれているはずです。

![インラインで浮動形状をエクスポートした例](https://example.com/export-inline.png "PDFでインラインにレンダリングされた浮動形状を示すスクリーンショット")

*画像の代替テキスト:* **export floating shapes inline** のスクリーンショット（インライン形状がある PDF）。

## よくある質問とエッジケース

### 1. 「ドキュメントに複雑な SmartArt が含まれている場合は？」

SmartArt は描画オブジェクトとして扱われます。インラインフラグはほとんどのベクター形状で機能しますが、非常に複雑な SmartArt は画像としてレンダリングされることがあります。その場合は、変換前に Word で SmartArt をフラット化するか、`pdfOptions.setExportSmartArtAsImage(true)` を使用して画像エクスポートを強制してください。

### 2. 「同じドキュメントでインラインとブロックのエクスポートを組み合わせられますか？」

残念ながら API は設定をグローバルに適用します。混在した動作が必要な場合は、ドキュメントをセクションに分割し、各セクションを異なるオプションで個別にエクスポートし、`PdfMerger` を使って PDF を結合してください。

### 3. 「フォント埋め込みに影響はありますか？」

いいえ。フォント埋め込みは `pdfOptions.setEmbedFullFonts(true)`（デフォルト）で制御されます。インライン形状フラグに触れずに、自由に有効化または無効化できます。

### 4. 「形状が本当に `<span>` になっているかどうかを確認する方法は？」

生成された PDF を **PDF.js** や **Adobe Acrobat** → **PDF を編集** → **オブジェクト インスペクタ** などのツールで開きます。基礎となる XML で形状が `<span>` 要素でラップされているのが確認できます。`<div>` が見える場合は、オプションが適用されていません。

## アプローチの拡張 – 関連オプション

ここに来たら、他の PDF 変換オプションも検討したくなるでしょう。

| Option | 機能 | 典型的な使用例 |
|--------|------|----------------|
| `setCompressImages(true)` | 画像サイズを削減する | ダウンロードを高速化 |
| `setUseHighQualityRendering(true)` | ベクター描画を向上させる | 印刷品質の PDF |
| `setExportDocumentStructure(true)` | アクセシビリティ用に構造タグを追加する | WCAG 準拠 |
| `setSaveFormat(SaveFormat.PDF)` | 形式を明示的に設定する（ほとんど不要） | マルチフォーマットパイプライン |

これらの設定は、レイアウト忠実度とパフォーマンスの両方が必要な **convert word to pdf inline** シナリオと相性が良いです。

## 変換のテスト

1. **ビジュアルチェック** – PDF を 2 つのビューア（Chrome と Adobe Reader）で開き、形状が揃っているか確認する。  
2. **自動差分** – `pdfbox` などのライブラリを使って XML を抽出し、`<span>` タグの存在をアサートする。  
3. **パフォーマンスベンチマーク** – `setCompressImages` の有無でかかる時間を測定し、トレードオフを確認する。

簡単な JUnit の例:

```java
@Test
public void testInlineExport() throws Exception {
    Document doc = new Document("src/test/resources/FloatingShapes.docx");
    PdfSaveOptions opts = new PdfSaveOptions();
    opts.setExportFloatingShapesAsInlineTag(true);
    ByteArrayOutputStream out = new ByteArrayOutputStream();
    doc.save(out, opts);
    String pdfXml = new String(out.toByteArray(), StandardCharsets.UTF_8);
    assertTrue(pdfXml.contains("<span"));
}
```

## 結論

これで、**インラインで浮動形状をエクスポート**しながら **インラインで Word を PDF に変換**するための、堅実なエンドツーエンドのソリューションが手に入りました。`PdfSaveOptions` を設定することで各形状に使用される HTML タグを制御し、PDF を整然と検索可能に保てます。出力をテストし、画像圧縮などの関連オプションを調整し、複雑な SmartArt といったエッジケースにも対処することを忘れずに。

次のステップに進みますか？同じ手法を **インラインで浮動テーブルをエクスポート** に適用したり、Aspose の `HtmlSaveOptions` を使って CSS スタイルの PDF を試したりしてみてください。ロード、設定、保存というパターンは、ほぼすべてのドキュメントから PDF への変換シナリオで有効です。

**how to set pdf options** や別のライブラリでの **save word as pdf options** に関する質問があれば、コメントを残してください。ハッピーコーディング！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれ、追加の API 機能を習得し、プロジェクトで代替実装アプローチを探求するのに役立ちます。

- [Aspose.Words for Java を使用した Word から PDF への変換](/words/english/java/document-converting/)
- [Aspose.Words for Java でドキュメントを PDF として保存する方法](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Word ドキュメント構造を PDF にエクスポート](/words/english/net/programming-with-pdfsaveoptions/export-document-structure/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}