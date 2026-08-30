---
category: general
date: 2026-04-28
description: Aspose.Words for Java を使用して PDF UA ドキュメントを作成します。復元機能で docx を読み込み、数式を
  LaTeX にエクスポートし、Word から Markdown を保存し、欠落フォントを取得する方法を学びます。
draft: false
keywords:
- create PDF UA document
- retrieve missing fonts
- export equations to LaTeX
- save markdown from Word
- load docx with recovery
language: ja
og_description: Aspose.Words for Java を使用して PDF UA ドキュメントを作成する。リカバリ ローディング、LaTeX エクスポート、Markdown
  保存、欠落フォントの取得を網羅したステップバイステップ ガイド。
og_title: PDF UAドキュメントの作成 – 完全なJavaチュートリアル
tags:
- Aspose.Words
- Java
- PDF/UA
title: Aspose.WordsでPDF/UAドキュメントを作成 – 完全Javaガイド
url: /ja/java/document-conversion-and-export/create-pdf-ua-document-with-aspose-words-full-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# PDF UA ドキュメントの作成 – 完全 Java チュートリアル

Word ファイルから **PDF UA ドキュメント** を作成し、破損したコンテンツにも対応したいですか？このチュートリアルでは、回復モードで DOCX を読み込み、数式を LaTeX にエクスポートし、Word から Markdown を保存し、欠損フォントを取得する方法を Aspose.Words for Java を使って解説します。  

壊れた .docx を見て「なぜ PDF がアクセシブルにならないのか？」と悩んだことがあるなら、ここが最適です。最後まで実行すれば、完全に準拠した PDF/UA 1 ファイル、LaTeX 数式を含む Markdown バージョン、そしてロード時に発生したフォント置換の一覧が手に入ります。

## 必要なもの

- **Aspose.Words for Java**（2026 年時点の最新バージョン） – Maven/Gradle の依存関係または JAR をクラスパスに追加してください。  
- Java 17 以上（API はストリームを使用するため、最新の JDK が推奨されます）。  
- 破損したセクション、Office Math 数式、フローティングシェイプが含まれる可能性のあるサンプル `input.docx`。  

追加のライブラリは不要です。すべて Aspose.Words 内に収められています。

---

## Step 1 – 回復モードで DOCX をロード  

ドキュメントが部分的に破損している場合、デフォルトローダーは例外をスローします。回復モードを有効にすると、Aspose.Words は処理を続行し、警告を出力します。

```java
import com.aspose.words.*;

public class LatestFeaturesDemo {

    public static void main(String[] args) throws Exception {

        // 1️⃣ Load the document with recovery to gracefully handle corruption
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

*重要ポイント:* 回復モードにより、1 つの不良パラグラフが原因でパイプライン全体が停止するのを防げます。また `doc.getWarnings()` が埋められるため、後で **欠損フォントの取得** やその他の問題を確認できます。

---

## Step 2 – Markdown ファイル内に数式を LaTeX でエクスポート  

多くの開発者がドキュメント作成に Markdown を好みますが、Word の組み込み数式はコピーが面倒です。Aspose.Words はそれらを直接 LaTeX に変換できます。

```java
        // 2️⃣ Configure Markdown export with LaTeX for Office Math
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

        // Store images in a sub‑folder so the Markdown stays tidy
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });

        // Save the Markdown file
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);
```

*プロのコツ:* コールバックにより抽出された画像はすべて `imgs/` 配下に保存されます。これは GitHub が Markdown をレンダリングする方式と同じで、クリーンかつポータブルです。

---

## Step 3 – 正しいタグ付けで PDF / UA ドキュメントを作成  

PDF/UA（Universal Accessibility）準拠は多くの公共セクター案件で必須です。以下のオプションを使用すると、Aspose.Words はフローティングシェイプに正しいタグを付け、PDF/UA 準拠フラグを設定します。

```java
        // 3️⃣ Prepare PDF/UA export options
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);          // Enforce PDF/UA‑1
        pdfOptions.setExportFloatingShapesAsInlineTag(true);      // Tag floating shapes

        // Save the accessible PDF
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);
```

*期待できる結果:* Adobe Acrobat Pro で `output.pdf` を開くと、文書プロパティに「PDF/UA‑1 compliant」と表示されます。すべてのフローティングシェイプ（テキストボックス、画像）にはスクリーンリーダー向けの適切なタグが付与されます。

---

## Step 4 – シェイプの影を調整（オプションのスタイリング）  

アクセシビリティには必須ではありませんが、内部レポート用にビジュアルを微調整したい場合に便利です。

```java
        // 4️⃣ Grab the first shape and modify its shadow
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(java.awt.Color.GRAY);
```

*なぜやるのか:* PDF がマーケティング資料としても使われる場合、さりげない影を付けるだけでレイアウトが洗練され、かつ準拠性は損なわれません。

---

## Step 5 – 欠損フォントとその他の警告を取得  

回復ロード時に、Aspose.Words はフォント置換情報を記録します。一覧化することで、正しいフォントを埋め込むか、フォールバックを受け入れるか判断できます。

```java
        // 5️⃣ Enumerate font‑substitution warnings
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName() +
                                   " → substituted: " + fsw.getSubstitutedFontName());
            }
        }

        // You can also handle other warning types here (e.g., content loss)
    }
}
```

*典型的な出力*（コンソールに次のように表示されます）:

```
=== Font Substitution Report ===
Missing: Calibri → substituted: Arial
Missing: Times New Roman → substituted: Liberation Serif
```

重要なフォントが欠損している場合は、サーバーにインストールするか、`PdfSaveOptions.setEmbedFullFonts(true)` で埋め込むことを検討してください。

---

## 完全動作サンプル  

以下は実行可能な完全な Java クラスです。IDE に貼り付け、パスを調整して **Run** をクリックしてください。

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to:
 *  • load a DOCX with recovery,
 *  • export equations to LaTeX inside Markdown,
 *  • create a PDF/UA‑1 compliant PDF,
 *  • modify shape shadows,
 *  • and list any font‑substitution warnings.
 */
public class LatestFeaturesDemo {
    public static void main(String[] args) throws Exception {

        // ---- Step 1: Load DOCX with recovery ----
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // ---- Step 2: Export equations to LaTeX in Markdown ----
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);

        // ---- Step 3: Save as PDF/UA with proper tagging ----
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);

        // ---- Step 4: Optional – adjust the first shape’s shadow ----
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(Color.getGray());

        // ---- Step 5: List any missing‑font warnings ----
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName()
                                   + " → substituted: " + fsw.getSubstitutedFontName());
            }
        }
    }
}
```

**期待される結果**

| 出力 | 説明 |
|--------|-------------|
| `output.md` | すべての Office Math 数式が LaTeX（`$…$`）として出力される Markdown ファイル。画像は `imgs/` 配下に保存。 |
| `output.pdf` | PDF/UA‑1 準拠ドキュメント。Acrobat で「File → Properties → Standards」に「PDF/UA‑1」と表示されます。 |
| コンソール | 欠損フォントの一覧、例: “Missing: Calibri → substituted: Arial”。 |

---

## よくある質問 (FAQ)

**Q: 古い Aspose.Words バージョンでも動作しますか？**  
A: `RecoveryMode`、`OfficeMathExportMode.LATEX`、`PdfCompliance.PDF_UA_1` は 22.8 で導入されました。古いリリースをご使用の場合はアップグレードしてください。アクセシビリティ機能はバックポートされていません。

**Q: 置換ではなく元のフォントを埋め込みたい場合は？**  
A: `pdfOptions.setEmbedFullFonts(true)` を設定し、JVM のフォントパスにフォントファイルが存在することを確認してください。

**Q: LaTeX 数式を保持したまま他のマークアップ形式（例: HTML）にエクスポートできますか？**  
A: はい。`HtmlSaveOptions` を使用し、`setOfficeMathExportMode(OfficeMathExportMode.LATEX)` を設定すれば、同じ enum が各形式で機能します。

**Q: DOCX に多数のフローティングシェイプが含まれていますが、すべてタグ付けされますか？**  
A: `setExportFloatingShapesAsInlineTag(true)` を有効にすると、Aspose.Words は各フローティングシェイプを `<Figure>` タグでラップし、PDF/UA のスクリーンリーダーチェックをほぼ満たします。

---

## まとめ  

Word ソースから **PDF UA ドキュメント** を作成し、**docx の回復ロード**、**数式の LaTeX エクスポート**、**Word からの Markdown 保存**、そして **欠損フォントの取得** までを一連の流れで実装できました。コードは完全に自己完結型で、Java 17+ 環境ならどこでも動作し、アクセシビリティ監査と開発者向け資産の両方に即座に利用可能です。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}