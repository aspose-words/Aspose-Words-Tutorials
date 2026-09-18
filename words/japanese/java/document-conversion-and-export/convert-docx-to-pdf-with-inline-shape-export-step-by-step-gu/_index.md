---
category: general
date: 2026-02-18
description: DOCX を PDF に変換し、Word を PDF として保存する際に浮動形状を保持する方法を学びましょう。このガイドでは、形状を正しくエクスポートする方法を示します。
draft: false
keywords:
- convert docx to pdf
- save word as pdf
- how to export shapes
language: ja
og_description: DOCX を PDF に変換し、シェイプのエクスポート方法を学びましょう。この完全なチュートリアルに従って、適切なタグ付けを行った
  Word を PDF として保存してください。
og_title: DOCXをPDFに変換 – インラインシェイプエクスポートガイド
tags:
- Aspose.Words
- Java
- PDF conversion
title: インラインシェイプエクスポートでDOCXをPDFに変換する – ステップバイステップガイド
url: /ja/java/document-conversion-and-export/convert-docx-to-pdf-with-inline-shape-export-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX から PDF へ変換 – インラインシェイプエクスポートガイド

DOCX を **PDF に変換** したいけれど、浮動画像やテキストボックスが消えたり位置がずれたりすることを心配したことはありませんか？ あなただけではありません。自動レポートジェネレータやバッチ処理パイプラインなど、多くのプロジェクトで Word 文書の正確なレイアウトを保持することは絶対条件です。  

良いニュースです。数行のコードで **Word を PDF として保存** でき、浮動シェイプをインラインタグに変換するかブロックレベル要素のままにするかを制御できます。以下では、希望通りに **シェイプをエクスポートする方法** を正確に示し、一般的な落とし穴を回避するためのいくつかのヒントも紹介します。

---

## 学べること

* ディスクから `.docx` ファイルを読み込む。  
* `PdfSaveOptions` を設定し、浮動シェイプをインラインタグとしてエクスポートする。  
* 生成された PDF を任意のフォルダーに書き出す。  
* `setExportFloatingShapesAsInlineTag` フラグが重要な理由と、いつ切り替えるべきかを理解する。  

外部サービスや魔法のような “クリックでダウンロード” UI は不要です。純粋な Java コードだけで、任意の Maven または Gradle プロジェクトに組み込むことができます。

## 前提条件

| 要件 | 重要な理由 |
|-------------|----------------|
| **Aspose.Words for Java** (v23.12 以上) | サンプルで使用される `Document` と `PdfSaveOptions` クラスを提供します。 |
| **JDK 8+** | ライブラリは Java 8 以降向けにコンパイルされており、古いランタイムでは `UnsupportedClassVersionError` がスローされます。 |
| **浮動シェイプ（画像、テキストボックス、WordArt）を少なくとも1つ含む DOCX ファイル** | シェイプエクスポートオプションの効果を確認するには、実際に浮動オブジェクトが含まれる文書が必要です。 |

これらがすでに揃っているなら、素晴らしいです—さっそく始めましょう。

## ステップ 1 – ソースドキュメントの読み込み  

まず、変換したい `.docx` を指す `Document` インスタンスを作成します。コンストラクタはファイルをメモリに読み込み、OpenXML パッケージを解析し、内部オブジェクトモデルを準備します。

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

// Adjust the path to your environment
String inputPath = "YOUR_DIRECTORY/input.docx";

Document doc = new Document(inputPath);
```

> **プロのコツ:** ループで多数のファイルを処理する場合、`doc.close()` を呼び出した後（またはガベージコレクタに任せて）にのみ、単一の `Document` オブジェクトを再利用してください。これにより Windows でのファイルハンドルリークを防げます。

## ステップ 2 – シェイプをエクスポートするための PDF 保存オプションの設定  

チュートリアルの核心はここにあります。`PdfSaveOptions` を使用すると、変換の挙動を指定できます。`setExportFloatingShapesAsInlineTag(true)` を設定すると、すべての浮動シェイプが PDF のタグ構造内で *インライン* 要素として扱われます。つまり、スクリーンリーダーは周囲のテキストと同じ順序でシェイプを読み上げるため、アクセシビリティ遵守にしばしば必要とされます。

```java
import com.aspose.words.PdfSaveOptions;

PdfSaveOptions pdfOptions = new PdfSaveOptions();
// true → inline tagging (shape behaves like a character)
// false → block‑level tagging (shape sits in its own block)
pdfOptions.setExportFloatingShapesAsInlineTag(true);
```

**`false` に設定するのはいつですか？**  
PDF が印刷専用の配布を目的としており、シェイプの元の位置を保持しつつ論理的な読み順に影響させたくない場合は、ブロックレベルのタグ付けを選択するかもしれません。デフォルトは `false` なので、このチュートリアルではインライン動作を明示的に有効にしています。

## ステップ 3 – ドキュメントを PDF として保存  

オプションの準備ができたら、対象のファイル名とオプションオブジェクトを指定して `save` を呼び出します。ライブラリがレイアウトエンジン、フォント埋め込み、タグ生成といった重い処理を行います。

```java
String outputPath = "YOUR_DIRECTORY/shapes.pdf";
doc.save(outputPath, pdfOptions);
```

呼び出しが完了すると、指定したフォルダーに `shapes.pdf` が作成されます。Adobe Acrobat やタグを表示できる任意の PDF ビューア（通常は **File → Properties → Tags**）で開くと、浮動シェイプがインラインタグとして表示されていることが確認できます。

## 完全な実行可能サンプル  

すべてをまとめると、以下のような単体でコンパイル・実行できる Java クラスになります。Aspose.Words の JAR がクラスパスに含まれていることを確認してください。

```java
import com.aspose.words.*;

public class DocxToPdfWithShapes {
    public static void main(String[] args) {
        try {
            // 1️⃣ Load the source DOCX
            String inputPath = "YOUR_DIRECTORY/input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Configure PDF options – export floating shapes as inline tags
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → inline tagging

            // 3️⃣ Save as PDF
            String outputPath = "YOUR_DIRECTORY/shapes.pdf";
            doc.save(outputPath, pdfOptions);

            System.out.println("✅ Conversion complete! PDF saved to: " + outputPath);
        } catch (Exception e) {
            System.err.println("❌ Something went wrong: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**期待される結果:**  
- PDF ファイルは元の DOCX と同じテキストコンテンツを含みます。  
- すべての浮動画像やテキストボックスは *インライン* タグ付けされ、別々のブロックではなく読み順に沿って表示されます。  
- PDF の **Tags** パネルを開くと、`<Paragraph>` の内部に `<Figure>` 要素が入れ子になっているのが確認でき、これは `setExportFloatingShapesAsInlineTag(true)` が保証する結果です。

## よくある質問とエッジケース  

### 1️⃣ パスワード保護された DOCX ファイルでも動作しますか？

はい。読み込む前にパスワードを指定するだけです。

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("mySecret");
Document doc = new Document(inputPath, loadOptions);
```

### 2️⃣ Word ファイル内の SVG や EMF 画像はどうですか？

Aspose.Words は PDF 保存時にベクターグラフィックを自動的にラスタライズします。ベクターのまま保持したい場合は、次のように設定します。

```java
pdfOptions.setRasterizeTransformedElements(false);
```

### 3️⃣ 変換時にハイパーリンクを保持するには？

リンクはデフォルトで保持されます。ただし、タグを無効にすると（`pdfOptions.setSaveFormat(SaveFormat.PDF)` のみでオプションを付けない場合）論理構造が失われる可能性があります。タグとリンクの両方を保持するために `PdfSaveOptions` オブジェクトを使用してください。

### 4️⃣ DOCX ファイルのフォルダーをバッチ処理できますか？

もちろん可能です。`DocxToPdfWithShapes` のロジックを `Files.list(Paths.get("YOUR_DIRECTORY"))` を反復するループでラップしてください。ファイルごとに例外処理を行い、1つの不正な文書が全体の実行を停止しないようにしましょう。

## 現場からのヒント  

* **フォント欠如に注意。** ソース DOCX がサーバーにインストールされていないカスタムフォントを使用している場合、PDF は代替フォントに置き換えられ、レイアウトが崩れる可能性があります。`pdfOptions.setFontEmbeddingMode(FontEmbeddingMode.EMBED_ALL)` を使用して埋め込みを強制してください。  
* **アクセシビリティのテスト。** 変換後に Acrobat の **Accessibility Checker** を実行してください。インラインタグ付けは通常スコアを向上させますが、画像に代替テキストを手動で追加する必要がある場合があります。  
* **パフォーマンスのヒント:** 大きな文書（100 ページ以上）では、`pdfOptions.setMemoryOptimization(true)` を有効にしてヒープ使用量を削減してください。

## ビジュアルでの確認  

以下は Adobe Acrobat で開いた PDF のスクリーンショットで、**Tags** ペインにハイライトされたインラインタグ付けされたシェイプが表示されています。

![インラインシェイプタグを示す DOCX から PDF への変換例出力](image.png)

## まとめ  

これで、浮動オブジェクトのエクスポート方法を制御しながら **DOCX を PDF に変換する方法** が分かりました。`setExportFloatingShapesAsInlineTag` を切り替えることで、シェイプを読み順の一部にするか、独立したブロックとして保持するかを選択でき、アクセシビリティと視覚的忠実度の両方にとって重要です。

ここからできることは次のとおりです：

- **Word を PDF として大量に保存** してアーカイブする。  
- 長期保存のために `setCompliance(PdfCompliance.PDF_A_1B)` など、他の `PdfSaveOptions` を試す。  
- 完全な Aspose.Words ドキュメントを参照したり、リッチなタグツリーのために `setExportDocumentStructure(true)` フラグを試すなど、**シェイプのエクスポート方法** をさらに深く掘り下げる。  

ぜひ試してみて、オプションを調整し、PDF が必要な通りに見えるようにしてください。コーディングを楽しんで！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}