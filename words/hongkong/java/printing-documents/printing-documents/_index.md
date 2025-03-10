---
title: 在 Aspose.Words for Java 中列印文檔
linktitle: 列印文件
second_title: Aspose.Words Java 文件處理 API
description: 了解如何使用 Aspose.Words for Java 列印文件。在 Java 應用程式中進行無縫列印的逐步指南。
weight: 10
url: /zh-hant/java/printing-documents/printing-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中列印文檔


如果您想使用 Aspose.Words for Java 列印文檔，那麼您來對地方了。在本逐步指南中，我們將引導您使用所提供的原始程式碼完成使用 Aspose.Words for Java 列印文件的過程。

## 介紹

列印文件是許多應用中的常見任務。 Aspose.Words for Java 提供了強大的 API 來處理 Word 文檔，包括列印它們的功能。在本教學中，我們將引導您逐步完成列印 Word 文件的過程。

## 設定您的環境

在我們深入研究程式碼之前，請確保您具備以下先決條件：

- 安裝了 Java 開發工具包 (JDK)
- 下載 Aspose.Words for Java 程式庫並將其新增至您的專案中

## 載入文檔

首先，您需要載入要列印的 Word 文件。代替`"Your Document Directory"`以及您的文件的路徑和`"Your Output Directory"`與所需的輸出目錄。

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Rendering.docx");
```

## 建立列印作業

接下來，我們將建立一個列印作業來列印載入的文件。下面的程式碼片段初始化列印作業並設定所需的印表機設定。

```java
//建立一個列印作業來列印我們的文件。
PrinterJob pj = PrinterJob.getPrinterJob();
//使用文件中的頁數初始化屬性集。
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
//將印表機設定與其他參數一起傳遞到列印文件。
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
```

## 列印文件

現在我們已經設定了列印作業，是時候列印文件了。以下程式碼片段將文件與列印作業相關聯並啟動列印過程。

```java
//使用列印作業傳遞要列印的文件。
pj.setPrintable(awPrintDoc);
pj.print();
```
## 完整的原始碼
```java
string dataDir = "Your Document Directory";
Document doc = new Document(dataDir + "Rendering.docx");
//建立一個列印作業來列印我們的文件。
PrinterJob pj = PrinterJob.getPrinterJob();
//使用文件中的頁數初始化屬性集。
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
//將印表機設定與其他參數一起傳遞到列印文件。
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
//使用列印作業傳遞要列印的文件。
pj.setPrintable(awPrintDoc);
pj.print();
```
MultipagePrintDocument的原始碼
```java
class MultipagePrintDocument implements Printable
{
    private final Document mDocument;
    private final int mPagesPerSheet;
    private final boolean mPrintPageBorders;
    private final AttributeSet mAttributeSet;
    //<摘要>
    //自訂PrintDocument 類別的建構子。
    // / </摘要>
    public MultipagePrintDocument(Document document, int pagesPerSheet, boolean printPageBorders,
                                  AttributeSet attributes) {
        if (document == null)
            throw new IllegalArgumentException("document");
        mDocument = document;
        mPagesPerSheet = pagesPerSheet;
        mPrintPageBorders = printPageBorders;
        mAttributeSet = attributes;
    }
    public int print(Graphics g, PageFormat pf, int page) {
        //屬性集中定義的頁面開始和結束索引。
        int[][] pageRanges = ((PageRanges) mAttributeSet.get(PageRanges.class)).getMembers();
        int fromPage = pageRanges[0][0] - 1;
        int toPage = pageRanges[0][1] - 1;
        Dimension thumbCount = getThumbCount(mPagesPerSheet, pf);
        //計算接下來要呈現的頁面索引。
        int pagesOnCurrentSheet = (int) (page * (thumbCount.getWidth() * thumbCount.getHeight()));
        //如果頁面索引大於總頁面範圍，則沒有任何內容
        //更多要渲染的內容。
        if (pagesOnCurrentSheet > (toPage - fromPage))
            return Printable.NO_SUCH_PAGE;
        //計算每個縮圖佔位符的大小（以磅為單位）。
        Point2D.Float thumbSize = new Point2D.Float((float) (pf.getImageableWidth() / thumbCount.getWidth()),
                (float) (pf.getImageableHeight() / thumbCount.getHeight()));
        //計算這張紙上要列印的第一頁頁碼。
        int startPage = pagesOnCurrentSheet + fromPage;
        //選擇要列印在這張紙上的最後一頁的頁碼。
        int pageTo = Math.max(startPage + mPagesPerSheet - 1, toPage);
        //從儲存的目前頁面循環遍歷所選頁面以計算
        //最後一頁。
        for (int pageIndex = startPage; pageIndex <= pageTo; pageIndex++) {
            //計算列索引和行索引。
            int rowIdx = (int) Math.floor((pageIndex - startPage) / thumbCount.getWidth());
            int columnIdx = (int) Math.floor((pageIndex - startPage) % thumbCount.getWidth());
            //定義世界座標中的縮圖位置（在本例中為點）。
            float thumbLeft = columnIdx * thumbSize.x;
            float thumbTop = rowIdx * thumbSize.y;
            try {
                //計算左側和頂部的起始位置。
                int leftPos = (int) (thumbLeft + pf.getImageableX());
                int topPos = (int) (thumbTop + pf.getImageableY());
                //使用計算的座標將文件頁面渲染到 Graphics 對象
                //和縮圖佔位符大小。
                //有用的回傳值是呈現頁面的比例。
                float scale = mDocument.renderToSize(pageIndex, (Graphics2D) g, leftPos, topPos, (int) thumbSize.x,
                        (int) thumbSize.y);
                //繪製頁面邊框（頁面縮圖可以比縮圖小）
                //佔位符大小）。
                if (mPrintPageBorders) {
                    //取得頁面的實際 100% 大小（以磅為單位）。
                    Point2D.Float pageSize = mDocument.getPageInfo(pageIndex).getSizeInPoints();
                    //使用已知的比例因子在縮放頁面周圍繪製邊框。
                    g.setColor(Color.black);
                    g.drawRect(leftPos, topPos, (int) (pageSize.x * scale), (int) (pageSize.y * scale));
                    //在縮圖佔位符周圍繪製邊框。
                    g.setColor(Color.red);
                    g.drawRect(leftPos, topPos, (int) thumbSize.x, (int) thumbSize.y);
                }
            } catch (Exception e) {
                //如果渲染期間發生任何錯誤，則不執行任何操作。
                //如果渲染過程中出現任何錯誤，這將繪製空白頁面。
            }
        }
        return Printable.PAGE_EXISTS;
    }
    private Dimension getThumbCount(int pagesPerSheet, PageFormat pf) {
        Dimension size;
        //定義工作表上的列數和行數
        //風景紙。
        switch (pagesPerSheet) {
            case 16:
                size = new Dimension(4, 4);
                break;
            case 9:
                size = new Dimension(3, 3);
                break;
            case 8:
                size = new Dimension(4, 2);
                break;
            case 6:
                size = new Dimension(3, 2);
                break;
            case 4:
                size = new Dimension(2, 2);
                break;
            case 2:
                size = new Dimension(2, 1);
                break;
            default:
                size = new Dimension(1, 1);
                break;
        }
        //如果紙張為縱向，則交換寬度和高度。
        if ((pf.getWidth() - pf.getImageableX()) < (pf.getHeight() - pf.getImageableY()))
            return new Dimension((int) size.getHeight(), (int) size.getWidth());
        return size;
	}
}
```

## 結論

恭喜！您已使用 Aspose.Words for Java 成功列印了 Word 文件。本逐步指南將幫助您將文件列印無縫整合到 Java 應用程式中。

## 常見問題解答

### Q1：我可以使用 Aspose.Words for Java 列印文件的特定頁面嗎？

是的，您可以在列印文件時指定頁面範圍。在程式碼範例中，我們使用了`attributes.add(new PageRanges(1, doc.getPageCount()))`列印所有頁面。您可以根據需要調整頁面範圍。

### Q2：Aspose.Words for Java適合大量列印嗎？

絕對地！ Aspose.Words for Java 非常適合大量列印任務。您可以遍歷文件清單並使用類似的程式碼逐一列印它們。

### Q3：如何處理列印錯誤或異常？

您應該處理列印過程中可能發生的任何潛在異常。有關處理異常的信息，請查看 Aspose.Words for Java 文件。

### Q4：我可以進一步自訂列印設定嗎？

是的，您可以自訂列印設定以滿足您的特定要求。瀏覽 Aspose.Words for Java 文檔，以了解更多有關可用列印選項的資訊。

### 問題 5：我可以在哪裡獲得有關 Aspose.Words for Java 的更多協助和支援？

如需更多支援和協助，您可以訪問[Aspose.Words for Java 論壇](https://forum.aspose.com/).

---

現在您已經成功學習如何使用 Aspose.Words for Java 列印文檔，您可以開始在 Java 應用程式中實現此功能。快樂編碼！
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
