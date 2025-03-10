---
title: 在 Aspose.Words for Java 中使用頁首和頁尾
linktitle: 使用頁首和頁尾
second_title: Aspose.Words Java 文件處理 API
description: 逐步學習如何在 Aspose.Words for Java 中使用頁首和頁尾。輕鬆建立專業文件。
weight: 16
url: /zh-hant/java/using-document-elements/using-headers-and-footers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中使用頁首和頁尾


在本綜合指南中，我們將引導您完成在 Aspose.Words for Java 中使用頁首和頁尾的過程。頁首和頁尾是文件格式化的基本元素，Aspose.Words 提供了強大的工具來根據您的需求建立和自訂它們。

現在，讓我們詳細介紹每個步驟。

## 1.Aspose.Words簡介

Aspose.Words 是一個功能強大的 Java API，可讓您以程式設計方式建立、操作和呈現 Word 文件。它提供了廣泛的文檔格式功能，包括頁首和頁尾。

## 2. 設定 Java 環境

在開始使用 Aspose.Words 之前，請確保您已正確設定 Java 開發環境。您可以在 Aspose.Words 文件頁面上找到必要的設定說明：[Aspose.Words Java 文檔](https://reference.aspose.com/words/java/).

## 3. 建立新文檔

要使用頁首和頁尾，您需要使用 Aspose.Words 建立一個新文件。以下程式碼示範如何執行此操作：

```java
//用於建立新文件的 Java 程式碼
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 4. 了解頁面設定

頁面設定對於控製文件的佈局至關重要。您可以使用下列命令指定與頁首和頁尾相關的各種屬性`PageSetup`班級。例如：

```java
//設定頁面屬性
Section currentSection = builder.getCurrentSection();
PageSetup pageSetup = currentSection.getPageSetup();
pageSetup.setDifferentFirstPageHeaderFooter(true);
pageSetup.setHeaderDistance(20.0);
```

## 5.不同的首頁頁首/頁腳

Aspose.Words 允許您為文件的首頁設定不同的頁首和頁尾。使用`pageSetup.setDifferentFirstPageHeaderFooter(true);`啟用此功能。

## 6. 使用標頭

### 6.1.新增文字到標題

您可以使用以下命令向標題添加文本`DocumentBuilder`。這是一個例子：

```java
//將文字新增至首頁標題
builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.getFont().setName("Arial");
builder.getFont().setBold(true);
builder.getFont().setSize(14.0);
builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

### 6.2.將圖像插入標題

要將圖像插入標題中，您可以使用`insertImage`方法。這是一個例子：

```java
//將圖像插入標題中
builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
    RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
```

### 6.3.自訂標題樣式

您可以透過設定各種屬性（例如字體、對齊方式等）來自訂標題樣式，如上面的範例所示。

## 7. 使用頁尾

### 7.1.新增文字到頁腳

與頁首類似，您可以使用以下命令向頁腳添加文本`DocumentBuilder`。這是一個例子：

```java
//將文字加入主頁腳
builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
//根據需要插入文字和字段
```

### 7.2.將影像插入頁腳

若要將圖像插入頁腳，請使用`insertImage`方法，就像標題中一樣。

### 7.3.自訂頁腳樣式

使用自訂頁腳樣式`DocumentBuilder`，類似於自訂標題。

## 8. 頁碼

您可以使用以下欄位在頁首和頁尾中包含頁碼`PAGE`和`NUMPAGES`。當您新增或刪除頁面時，這些欄位會自動更新。

## 9. 頁尾中的版權訊息

若要將版權資訊新增至文件的頁腳，您可以使用包含兩個儲存格的表格，一個向左對齊，另一個向右對齊，如程式碼片段所示。

## 10. 使用多個部分

Aspose.Words 可讓您處理文件中的多個部分。您可以為每個部分設定不同的頁面設定和頁首/頁尾。

## 11. 景觀方向

如果需要，您可以將特定部分的方向變更為橫向模式。

## 12. 複製前面部分的頁首/頁尾

建立複雜文件時，複製前面部分的頁首和頁尾可以節省時間。

## 13. 儲存文檔

建立並自訂文件後，不要忘記使用`doc.save()`方法。

## 完整的原始碼
```java
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        Section currentSection = builder.getCurrentSection();
        PageSetup pageSetup = currentSection.getPageSetup();
        //指定我們是否希望首頁的頁首/頁尾與其他頁面不同。
        //您也可以使用 PageSetup.OddAndEvenPagesHeaderFooter 屬性來指定
        //奇數頁和偶數頁有不同的頁首/頁尾。
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
        //將定位的圖像插入標題的左上角/左上角。
        //距頁面上/左邊緣的距離設定為 10 點。
        builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
            RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.write("Aspose.Words Header/Footer Creation Primer.");
        builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
        //我們使用一個包含兩個單元格的表格來將文字的一部分放在該行上（帶有頁碼）。
        //左對齊，文字的其他部分（有版權）右對齊。
        builder.startTable();
        builder.getCellFormat().clearFormatting();
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        //它使用 PAGE 和 NUMPAGES 欄位自動計算當前頁碼和頁數。
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
        //進行分頁以建立第二頁，在該頁上將看到主頁首/頁尾。
        builder.insertBreak(BreakType.PAGE_BREAK);
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        currentSection = builder.getCurrentSection();
        pageSetup = currentSection.getPageSetup();
        pageSetup.setOrientation(Orientation.LANDSCAPE);
        //本節不需要不同的首頁頁首/頁腳，我們只需要文件中的一個標題頁，
        //並且該頁面的頁首/頁尾已在上一節中定義。
        pageSetup.setDifferentFirstPageHeaderFooter(false);
        //此部分顯示上一部分的頁首/頁尾
        //預設呼叫 currentSection.HeadersFooters.LinkToPrevious(false) 取消此頁面寬度
        //新部分不同，因此我們需要為頁腳表設定不同的儲存格寬度。
        currentSection.getHeadersFooters().linkToPrevious(false);
        //如果我們想要使用本節已經存在的頁首/頁尾集。
        //但透過一些小的修改，複製頁首/頁尾可能會更方便
        //從上一節中取得並在我們想要的地方應用必要的修改。
        copyHeadersFootersFromPreviousSection(currentSection);
        HeaderFooter primaryFooter = currentSection.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);
        Row row = primaryFooter.getTables().get(0).getFirstRow();
        row.getFirstCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        row.getLastCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        doc.save("Your Directory Path" + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```	
copyHeadersFootersFromPreviousSection方法的原始碼
```java
    //<摘要>
    //將頁首/頁尾從上一節複製並複製到指定節。
    /// </摘要>
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

在本教程中，我們介紹了在 Aspose.Words for Java 中使用頁首和頁尾的基礎知識。您已經學習如何建立、自訂頁首和頁尾並設定樣式，以及其他基本的文件格式設定技術。

如需更多詳細資訊和進階功能，請參閱[Aspose.Words Java 文檔](https://reference.aspose.com/words/java/).

## 常見問題解答

### 1. 如何將頁碼新增至文件頁尾？
您可以透過插入頁碼來新增頁碼`PAGE`使用 Aspose.Words 將欄位新增至頁尾。

### 2. Aspose.Words與Java開發環境相容嗎？
是的，Aspose.Words 提供了對 Java 開發的支援。確保您已進行必要的設定。

### 3. 我可以自訂頁首和頁尾的字體和樣式嗎？
當然，您可以自訂字體、對齊方式和其他樣式，以使頁首和頁尾在視覺上更具吸引力。

### 4.奇數頁和偶數頁可以有不同的頁首嗎？
是的，您可以使用`PageSetup.OddAndEvenPagesHeaderFooter`為奇數頁和偶數頁指定不同的頁首。

### 5. 如何開始使用 Aspose.Words for Java？
首先，請訪問[Aspose.Words Java 文檔](https://reference.aspose.com/words/java/)有關使用 API 的全面指導。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
