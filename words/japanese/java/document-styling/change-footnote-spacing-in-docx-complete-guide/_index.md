---
category: general
date: 2026-07-20
description: DOCX ファイルの脚注間隔を簡単に変更できます。間隔の設定方法、脚注区切りの調整方法、そして Java で段落の行間を設定する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote spacing
- how to set spacing
- adjust footnote separator
- set paragraph line spacing
- change line spacing docx
language: ja
lastmod: 2026-07-20
og_description: DOCXファイルの脚注間隔を素早く変更します。このガイドでは、間隔の設定方法、脚注区切り線の調整、そしてJavaで段落の行間をカスタマイズする方法を示します。
og_image_alt: Screenshot showing Java code that changes footnote spacing in a DOCX
  document
og_title: DOCXで脚注の間隔を変更する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Change footnote spacing in DOCX files easily. Learn how to set spacing,
    adjust footnote separator, and set paragraph line spacing with Java.
  headline: Change footnote spacing in DOCX – Complete Guide
  type: TechArticle
tags:
- footnote
- docx
- java
- spacing
title: DOCXで脚注の間隔を変更する – 完全ガイド
url: /ja/java/document-styling/change-footnote-spacing-in-docx-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX の脚注間隔を変更する – 完全ガイド

Word 文書で **脚注間隔を変更** したいと思ったことはありませんか？でもどこから始めればいいか分からない…という方は多いです。論文を仕上げるときでも契約書を微調整するときでも、脚注の区切り線を適切に設定するだけで大きな違いが生まれます。  

このチュートリアルでは、**間隔の設定方法**、脚注区切り線の調整、そして **段落の行間設定** を Java ベースのライブラリを使って解説します。最後まで読めば、任意のプロジェクトに組み込める実行可能なサンプルが手に入ります。

## 必要なもの

- Java 17 以上（コードは最新の言語機能を使用しています）
- 依存関係管理のための Maven または Gradle
- 少なくとも 1 つの脚注が含まれる DOCX ファイル（手動で作成しても構いません）
- **Aspose.Words for Java** ライブラリ（または互換性のある API；例では Aspose を使用します）

以上です—重いフレームワークは不要で、純粋な Java と 1 つのライブラリだけです。

![DOCX の脚注間隔変更例](/images/footnote-spacing.png){alt="DOCX の脚注間隔変更例"}

## 手順 1: DOCX ドキュメントを読み込む（脚注間隔の変更）

最初に行うべきことは Word ファイルを開くことです。これにより操作可能な `Document` オブジェクトが取得できます。

```java
import com.aspose.words.*;

public class FootnoteSpacingDemo {
    public static void main(String[] args) throws Exception {
        // Load the DOCX file – change the path to your own file
        Document doc = new Document("input.docx");
        
        // Continue with spacing adjustments...
        adjustFootnoteSeparator(doc);
        
        // Save the updated document
        doc.save("output.docx");
    }
}
```

*Why this matters*: ドキュメントの読み込みは **脚注間隔を変更** するためのエントリーポイントです。`Document` インスタンスがなければ、脚注区切り線や段落フォーマットにアクセスできません。

## 手順 2: 脚注区切り線を取得して調整する（脚注区切り線の調整）

脚注区切り線は本文と脚注リストの間にある非表示の段落です。その行間を変更するには、その段落を取得して書式を調整する必要があります。

```java
private static void adjustFootnoteSeparator(Document doc) throws Exception {
    // Get the footnote separator (the first one is usually the default separator)
    FootnoteSeparator separator = doc.getFootnoteSeparator();
    
    // If the document has no separator (rare), create one
    if (separator == null) {
        separator = new FootnoteSeparator(doc);
        doc.getFootnotes().add(separator);
    }
    
    // Access the underlying paragraph and set line spacing
    Paragraph sepParagraph = separator.getSeparatorParagraph();
    ParagraphFormat fmt = sepParagraph.getParagraphFormat();
    
    // Set line spacing to 12 points – this is the core of "change footnote spacing"
    fmt.setLineSpacing(12.0);
    
    // Optional: also adjust spacing before/after if needed
    fmt.setSpaceBefore(0);
    fmt.setSpaceAfter(0);
}
```

### この解決策が問題を解決する方法

- **脚注区切り線を取得** – これが実際に変更したい対象で、*脚注区切り線の調整* 要件を満たします。
- **行間を設定** – `setLineSpacing(12.0)` はその非表示段落の *間隔設定方法* に直接対応します。
- **エッジケースの処理** – もしドキュメントに区切り線が存在しない場合は、その場で作成し、`NullPointerException` を防ぎます。

## 手順 3: 変更を検証して保存する（段落の行間設定）

区切り線を変更したら、変更が保存されたことを確認したくなります。Word で保存ファイルを開けば新しい間隔が確認できますが、プログラムからもチェック可能です。

```java
private static void verifySpacing(Document doc) throws Exception {
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    double spacing = sep.getSeparatorParagraph().getParagraphFormat().getLineSpacing();
    System.out.println("Current footnote separator line spacing: " + spacing);
}
```

`main` 内の `doc.save(...)` の直前に `verifySpacing(doc);` を追加します。プログラムを実行すると次のように表示されます。

```
Current footnote separator line spacing: 12.0
```

これにより **DOCX の行間変更** 操作が成功したことが確認できます。

## よくある落とし穴とプロのコツ

- **落とし穴**: `setLineSpacing` に “12” のように見える値を渡すと、実際には “12 pt” と解釈され “12 行” ではありません。Aspose はポイント単位を期待するため、12 は 12 pt を意味します。二倍行間にしたい場合は `24.0` を使用してください。
- **プロのコツ**: すべての脚注タイプ（区切り線、継続区切り線など）で統一した外観が必要な場合は、`doc.getFootnoteContinuationSeparator()` と `doc.getFootnoteContinuationNotice()` に対して同様の手順を繰り返してください。
- **落とし穴**: 変更後に `save()` を呼び忘れることです。メモリ上のドキュメントは変わりますが、ディスク上のファイルはそのままです。
- **プロのコツ**: 行間変更に加えてスタイル更新（`ParagraphStyle`）を組み合わせると、脚注セクションを完全に仕上げることができます。

## 完全な動作例（すべての手順を 1 ファイルにまとめたもの）

```java
import com.aspose.words.*;

public class FootnoteSpacingDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the DOCX document
        Document doc = new Document("input.docx");

        // 2️⃣ Adjust the footnote separator – this is where we "change footnote spacing"
        adjustFootnoteSeparator(doc);

        // 3️⃣ Verify the new line spacing (optional but handy for debugging)
        verifySpacing(doc);

        // 4️⃣ Save the result – now your footnotes have the desired spacing
        doc.save("output.docx");
        System.out.println("Footnote spacing updated and saved to output.docx");
    }

    private static void adjustFootnoteSeparator(Document doc) throws Exception {
        FootnoteSeparator separator = doc.getFootnoteSeparator();
        if (separator == null) {
            separator = new FootnoteSeparator(doc);
            doc.getFootnotes().add(separator);
        }
        Paragraph sepParagraph = separator.getSeparatorParagraph();
        ParagraphFormat fmt = sepParagraph.getParagraphFormat();

        // Core operation: "set paragraph line spacing" for the separator
        fmt.setLineSpacing(12.0);   // 12 pt line spacing
        fmt.setSpaceBefore(0);
        fmt.setSpaceAfter(0);
    }

    private static void verifySpacing(Document doc) throws Exception {
        FootnoteSeparator sep = doc.getFootnoteSeparator();
        double spacing = sep.getSeparatorParagraph().getParagraphFormat().getLineSpacing();
        System.out.println("Current footnote separator line spacing: " + spacing);
    }
}
```

上記コードを新しい Java クラスに貼り付け、Aspose.Words の Maven 依存関係を追加して実行してください。`output.docx` の脚注区切り線の行間が **12 pt** に設定され、実質的に **脚注間隔が変更** されます。

### Maven 依存関係

`pom.xml` に以下のスニペットを追加します：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

Gradle を使用する場合は、同等の設定は次の通りです：

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

## 結論

Java を使って DOCX ファイルの **脚注間隔を変更** する方法を学びました。ドキュメントを読み込み、**脚注区切り線** を取得し、**段落の行間設定** を適用することで、脚注の外観を正確にコントロールできます。  

ここからは、脚注テキストのスタイル変更やカスタム区切り線の追加、さらには複数文書への一括更新自動化など、関連する調整を試すことができます。  

**脚注区切り線の調整** やその他の Word 自動化タスクについて質問があれば、コメントを残してください。楽しいコーディングを！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Word 文書のアジア文字段落間隔とインデントを変更する](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)
- [アジア文字段落間隔とインデントを変更する](/words/german/net/document-formatting/change-asian-paragraph-spacing-and-indents/)
- [アジア文字段落間隔とインデントを変更する](/words/french/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}