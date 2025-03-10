---
title: Aspose.Words for Java でヘッダーとフッターを使用する
linktitle: ヘッダーとフッターの使用
second_title: Aspose.Words Java ドキュメント処理 API
description: Aspose.Words for Java でヘッダーとフッターを使用する方法を段階的に学習します。プロフェッショナルなドキュメントを簡単に作成できます。
weight: 16
url: /ja/java/using-document-elements/using-headers-and-footers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でヘッダーとフッターを使用する


この包括的なガイドでは、Aspose.Words for Java でヘッダーとフッターを操作する手順について説明します。ヘッダーとフッターはドキュメントの書式設定に不可欠な要素であり、Aspose.Words には、ニーズに応じてヘッダーとフッターを作成およびカスタマイズするための強力なツールが用意されています。

それでは、それぞれのステップを詳しく見ていきましょう。

## 1. Aspose.Words の紹介

Aspose.Words は、Word 文書をプログラムで作成、操作、レンダリングできる強力な Java API です。ヘッダーやフッターなど、文書の書式設定に関する広範な機能を提供します。

## 2. Java環境の設定

Aspose.Words の使用を開始する前に、Java 開発環境が正しく設定されていることを確認してください。必要なセットアップ手順は、Aspose.Words のドキュメント ページに記載されています。[Aspose.Words Java ドキュメント](https://reference.aspose.com/words/java/).

## 3. 新しいドキュメントを作成する

ヘッダーとフッターを操作するには、Aspose.Words を使用して新しいドキュメントを作成する必要があります。次のコードは、その方法を示しています。

```java
//新しいドキュメントを作成するための Java コード
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 4. ページ設定を理解する

ページ設定は文書のレイアウトを制御する上で重要です。ヘッダーとフッターに関連するさまざまなプロパティを`PageSetup`クラス。例:

```java
//ページプロパティの設定
Section currentSection = builder.getCurrentSection();
PageSetup pageSetup = currentSection.getPageSetup();
pageSetup.setDifferentFirstPageHeaderFooter(true);
pageSetup.setHeaderDistance(20.0);
```

## 5. 最初のページのヘッダー/フッターが異なる

Aspose.Wordsでは、文書の最初のページに異なるヘッダーとフッターを設定できます。`pageSetup.setDifferentFirstPageHeaderFooter(true);`この機能を有効にします。

## 6. ヘッダーの操作

### 6.1. ヘッダーにテキストを追加する

ヘッダーにテキストを追加するには、`DocumentBuilder`次に例を示します。

```java
//最初のページのヘッダーにテキストを追加する
builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.getFont().setName("Arial");
builder.getFont().setBold(true);
builder.getFont().setSize(14.0);
builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

### 6.2. ヘッダーに画像を挿入する

ヘッダーに画像を挿入するには、`insertImage`方法。次に例を示します。

```java
//ヘッダーに画像を挿入する
builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
    RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
```

### 6.3. ヘッダースタイルのカスタマイズ

上記の例に示すように、フォント、配置などのさまざまなプロパティを設定することで、ヘッダー スタイルをカスタマイズできます。

## 7. フッターの操作

### 7.1. フッターにテキストを追加する

ヘッダーと同様に、フッターにもテキストを追加できます。`DocumentBuilder`次に例を示します。

```java
//プライマリフッターにテキストを追加する
builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
//必要に応じてテキストとフィールドを挿入します
```

### 7.2. フッターへの画像の挿入

フッターに画像を挿入するには、`insertImage`ヘッダーと同じようにメソッドを使用します。

### 7.3. フッタースタイルのカスタマイズ

フッターのスタイルをカスタマイズするには、`DocumentBuilder`ヘッダーのカスタマイズと同様です。

## 8. ページ番号

次のようなフィールドを使用して、ヘッダーとフッターにページ番号を含めることができます。`PAGE`そして`NUMPAGES`これらのフィールドは、ページを追加または削除すると自動的に更新されます。

## 9. フッターの著作権情報

ドキュメントのフッターに著作権情報を追加するには、コード スニペットに示すように、1 つのセルを左に、もう 1 つのセルを右に揃えた 2 つのセルを持つテーブルを使用します。

## 10. 複数のセクションの操作

Aspose.Words を使用すると、ドキュメント内の複数のセクションを操作できます。セクションごとに異なるページ設定やヘッダー/フッターを設定できます。

## 11. 横向き

必要に応じて、特定のセクションの向きを横向きに変更できます。

## 12. 前のセクションからヘッダー/フッターをコピーする

前のセクションからヘッダーとフッターをコピーすると、複雑なドキュメントを作成するときに時間を節約できます。

## 13. ドキュメントを保存する

ドキュメントを作成してカスタマイズしたら、`doc.save()`方法。

## 完全なソースコード
```java
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        Section currentSection = builder.getCurrentSection();
        PageSetup pageSetup = currentSection.getPageSetup();
        //最初のページのヘッダー/フッターを他のページと異なるものにするかどうかを指定します。
        // PageSetup.OddAndEvenPagesHeaderFooterプロパティを使用して指定することもできます。
        //奇数ページと偶数ページで異なるヘッダー/フッターを使用します。
        pageSetup.setDifferentFirstPageHeaderFooter(true);
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
        builder.getFont().setName("Arial");
        builder.getFont().setBold(true);
        builder.getFont().setSize(14.0);
        builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_PRIMARY);
        //ヘッダーの左上隅に配置された画像を挿入します。
        //ページの上端/左端からの距離は 10 ポイントに設定されています。
        builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
            RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.write("Aspose.Words Header/Footer Creation Primer.");
        builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
        // 2 つのセルを持つ表を使用して、行のテキストの一部 (ページ番号付き) を作成します。
        //左揃えにし、テキストのその他の部分 (著作権付き) を右揃えにします。
        builder.startTable();
        builder.getCellFormat().clearFormatting();
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        // PAGE フィールドと NUMPAGES フィールドを使用して、現在のページ番号とページ数を自動的に計算します。
        builder.write("Page ");
        builder.insertField("PAGE", "");
        builder.write(" of ");
        builder.insertField("NUMPAGES", "");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.LEFT);
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        builder.write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.endRow();
        builder.endTable();
        builder.moveToDocumentEnd();
        //改ページして、主要なヘッダー/フッターが表示される 2 番目のページを作成します。
        builder.insertBreak(BreakType.PAGE_BREAK);
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        currentSection = builder.getCurrentSection();
        pageSetup = currentSection.getPageSetup();
        pageSetup.setOrientation(Orientation.LANDSCAPE);
        //このセクションでは、最初のページのヘッダー/フッターは不要で、ドキュメントにはタイトルページが1つだけ必要です。
        //このページのヘッダー/フッターは前のセクションですでに定義されています。
        pageSetup.setDifferentFirstPageHeaderFooter(false);
        //このセクションには前のセクションのヘッダー/フッターが表示されます
        //デフォルトでは、このページの幅をキャンセルするにはcurrentSection.HeadersFooters.LinkToPrevious(false)を呼び出します。
        //新しいセクションでは異なるため、フッター テーブルに異なるセル幅を設定する必要があります。
        currentSection.getHeadersFooters().linkToPrevious(false);
        //このセクションに既に設定されているヘッダー/フッターを使用する場合。
        //しかし、少し変更を加えると、ヘッダー/フッターをコピーするのが便利になるかもしれません。
        //前のセクションから必要な変更を必要な場所に適用します。
        copyHeadersFootersFromPreviousSection(currentSection);
        HeaderFooter primaryFooter = currentSection.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);
        Row row = primaryFooter.getTables().get(0).getFirstRow();
        row.getFirstCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        row.getLastCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        doc.save("Your Directory Path" + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```	
copyHeadersFootersFromPreviousSection メソッドのソースコード
```java
    //<要約>
    //前のセクションのヘッダー/フッターを複製して、指定したセクションにコピーします。
    /// </要約>
    private void copyHeadersFootersFromPreviousSection(Section section)
    {
        Section previousSection = (Section)section.getPreviousSibling();
        if (previousSection == null)
            return;
        section.getHeadersFooters().clear();
        for (HeaderFooter headerFooter : (Iterable<HeaderFooter>) previousSection.getHeadersFooters())
            section.getHeadersFooters().add(headerFooter.deepClone(true));
	}
```

## 結論

このチュートリアルでは、Aspose.Words for Java でのヘッダーとフッターの操作の基本について説明しました。ヘッダーとフッターの作成、カスタマイズ、スタイル設定の方法や、その他の重要なドキュメント書式設定テクニックについて学習しました。

詳細と高度な機能については、[Aspose.Words Java ドキュメント](https://reference.aspose.com/words/java/).

## よくある質問

### 1. ドキュメントのフッターにページ番号を追加するにはどうすればよいですか?
ページ番号を追加するには、`PAGE` Aspose.Words を使用して、フィールドをフッターに追加します。

### 2. Aspose.Words は Java 開発環境と互換性がありますか?
はい、Aspose.Words は Java 開発をサポートしています。必要な設定が完了していることを確認してください。

### 3. ヘッダーとフッターのフォントとスタイルをカスタマイズできますか?
もちろん、フォント、配置、その他のスタイルをカスタマイズして、ヘッダーとフッターを視覚的に魅力的にすることができます。

### 4. 奇数ページと偶数ページに異なるヘッダーを設定することは可能ですか?
はい、使えます`PageSetup.OddAndEvenPagesHeaderFooter`奇数ページと偶数ページに異なるヘッダーを指定します。

### 5. Aspose.Words for Java を使い始めるにはどうすればよいですか?
まず、[Aspose.Words Java ドキュメント](https://reference.aspose.com/words/java/) API の使用に関する包括的なガイダンス。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
