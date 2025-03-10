---
title: 在 Aspose.Words for Java 中打印文档
linktitle: 打印文件
second_title: Aspose.Words Java 文档处理 API
description: 了解如何使用 Aspose.Words for Java 打印文档。在 Java 应用程序中无缝打印的分步指南。
weight: 10
url: /zh/java/printing-documents/printing-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中打印文档


如果您想使用 Aspose.Words for Java 打印文档，那么您来对地方了。在本分步指南中，我们将使用提供的源代码引导您完成使用 Aspose.Words for Java 打印文档的过程。

## 介绍

打印文档是许多应用程序中的常见任务。Aspose.Words for Java 提供了强大的 API 来处理 Word 文档，包括打印文档的功能。在本教程中，我们将逐步指导您完成打印 Word 文档的过程。

## 设置你的环境

在深入研究代码之前，请确保您已满足以下先决条件：

- 已安装 Java 开发工具包 (JDK)
- 下载 Aspose.Words for Java 库并添加到您的项目中

## 加载文档

首先，您需要加载要打印的 Word 文档。替换`"Your Document Directory"`您的文档的路径和`"Your Output Directory"`使用所需的输出目录。

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Rendering.docx");
```

## 创建打印作业

接下来，我们将创建一个打印作业来打印我们加载的文档。下面的代码片段初始化打印作业并设置所需的打印机设置。

```java
//创建一个打印作业来打印我们的文档。
PrinterJob pj = PrinterJob.getPrinterJob();
//使用文档的页数初始化属性集。
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
//将打印机设置连同其他参数一起传递到打印文档。
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
```

## 打印文档

现在我们已经设置了打印作业，是时候打印文档了。以下代码片段将文档与打印作业关联起来并启动打印过程。

```java
//使用打印作业传递要打印的文档。
pj.setPrintable(awPrintDoc);
pj.print();
```
## 完整源代码
```java
string dataDir = "Your Document Directory";
Document doc = new Document(dataDir + "Rendering.docx");
//创建一个打印作业来打印我们的文档。
PrinterJob pj = PrinterJob.getPrinterJob();
//使用文档的页数初始化属性集。
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
//将打印机设置连同其他参数一起传递到打印文档。
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
//使用打印作业传递要打印的文档。
pj.setPrintable(awPrintDoc);
pj.print();
```
MultipagePrintDocument 源代码
```java
class MultipagePrintDocument implements Printable
{
    private final Document mDocument;
    private final int mPagesPerSheet;
    private final boolean mPrintPageBorders;
    private final AttributeSet mAttributeSet;
    //<摘要>
    //自定义 PrintDocument 类的构造函数。
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
        //属性集中定义的页面开始和结束索引。
        int[][] pageRanges = ((PageRanges) mAttributeSet.get(PageRanges.class)).getMembers();
        int fromPage = pageRanges[0][0] - 1;
        int toPage = pageRanges[0][1] - 1;
        Dimension thumbCount = getThumbCount(mPagesPerSheet, pf);
        //计算下一步要渲染的页面索引。
        int pagesOnCurrentSheet = (int) (page * (thumbCount.getWidth() * thumbCount.getHeight()));
        //如果页面索引超过总页面范围，则没有任何内容
        //需要渲染更多内容。
        if (pagesOnCurrentSheet > (toPage - fromPage))
            return Printable.NO_SUCH_PAGE;
        //以点为单位计算每个缩略图占位符的大小。
        Point2D.Float thumbSize = new Point2D.Float((float) (pf.getImageableWidth() / thumbCount.getWidth()),
                (float) (pf.getImageableHeight() / thumbCount.getHeight()));
        //计算这张纸上要打印的第一页的数字。
        int startPage = pagesOnCurrentSheet + fromPage;
        //选择在此纸张上要打印的最后一页的页码。
        int pageTo = Math.max(startPage + mPagesPerSheet - 1, toPage);
        //循环遍历所选页面，从存储的当前页面到计算的
        //最后一页。
        for (int pageIndex = startPage; pageIndex <= pageTo; pageIndex++) {
            //计算列和行的索引。
            int rowIdx = (int) Math.floor((pageIndex - startPage) / thumbCount.getWidth());
            int columnIdx = (int) Math.floor((pageIndex - startPage) % thumbCount.getWidth());
            //在世界坐标中定义缩略图位置（在本例中为点）。
            float thumbLeft = columnIdx * thumbSize.x;
            float thumbTop = rowIdx * thumbSize.y;
            try {
                //计算左侧和顶部的起始位置。
                int leftPos = (int) (thumbLeft + pf.getImageableX());
                int topPos = (int) (thumbTop + pf.getImageableY());
                //使用计算出的坐标将文档页面渲染到 Graphics 对象
                //和缩略图占位符大小。
                //有用的返回值是页面呈现的比例。
                float scale = mDocument.renderToSize(pageIndex, (Graphics2D) g, leftPos, topPos, (int) thumbSize.x,
                        (int) thumbSize.y);
                //绘制页面边框（页面缩略图可能小于缩略图
                //占位符大小）。
                if (mPrintPageBorders) {
                    //获取页面的实际 100% 大小（以点为单位）。
                    Point2D.Float pageSize = mDocument.getPageInfo(pageIndex).getSizeInPoints();
                    //使用已知的比例因子在缩放后的页面周围绘制边框。
                    g.setColor(Color.black);
                    g.drawRect(leftPos, topPos, (int) (pageSize.x * scale), (int) (pageSize.y * scale));
                    //在缩略图占位符周围绘制边框。
                    g.setColor(Color.red);
                    g.drawRect(leftPos, topPos, (int) thumbSize.x, (int) thumbSize.y);
                }
            } catch (Exception e) {
                //如果渲染期间发生任何错误，则不执行任何操作。
                //如果渲染期间出现任何错误，这将绘制一张空白页。
            }
        }
        return Printable.PAGE_EXISTS;
    }
    private Dimension getThumbCount(int pagesPerSheet, PageFormat pf) {
        Dimension size;
        //定义工作表上的列数和行数
        //横向纸张。
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
        //如果纸张是纵向，则交换宽度和高度。
        if ((pf.getWidth() - pf.getImageableX()) < (pf.getHeight() - pf.getImageableY()))
            return new Dimension((int) size.getHeight(), (int) size.getWidth());
        return size;
	}
}
```

## 结论

恭喜！您已成功使用 Aspose.Words for Java 打印了 Word 文档。本分步指南应可帮助您将文档打印无缝集成到 Java 应用程序中。

## 常见问题解答

### 问题 1: 我可以使用 Aspose.Words for Java 打印文档的特定页面吗？

是的，您可以在打印文档时指定页面范围。在代码示例中，我们使用了`attributes.add(new PageRanges(1, doc.getPageCount()))`打印所有页面。您可以根据需要调整页面范围。

### Q2: Aspose.Words for Java 适合批量打印吗？

当然！Aspose.Words for Java 非常适合批量打印任务。您可以遍历文档列表并使用类似的代码逐一打印它们。

### Q3：如何处理打印错误或异常？

您应该处理打印过程中可能发生的任何潜在异常。有关处理异常的信息，请查看 Aspose.Words for Java 文档。

### Q4：我可以进一步自定义打印设置吗？

是的，您可以自定义打印设置以满足您的特定要求。浏览 Aspose.Words for Java 文档以了解有关可用打印选项的更多信息。

### Q5：在哪里可以获得有关 Aspose.Words for Java 的更多帮助和支持？

如需更多支持和帮助，您可以访问[Aspose.Words for Java 论坛](https://forum.aspose.com/).

---

现在您已成功学习了如何使用 Aspose.Words for Java 打印文档，您可以开始在 Java 应用程序中实现此功能。祝您编码愉快！
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
