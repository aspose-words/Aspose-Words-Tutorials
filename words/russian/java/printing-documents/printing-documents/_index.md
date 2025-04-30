---
"description": "Узнайте, как печатать документы с помощью Aspose.Words для Java. Пошаговое руководство для бесперебойной печати в ваших приложениях Java."
"linktitle": "Печать документов"
"second_title": "API обработки документов Java Aspose.Words"
"title": "Печать документов в Aspose.Words для Java"
"url": "/ru/java/printing-documents/printing-documents/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Печать документов в Aspose.Words для Java


Если вы хотите печатать документы с помощью Aspose.Words for Java, вы в правильном месте. В этом пошаговом руководстве мы проведем вас через процесс печати документов с помощью Aspose.Words for Java, используя предоставленный исходный код.

## Введение

Печать документов — это обычная задача во многих приложениях. Aspose.Words for Java предоставляет мощный API для работы с документами Word, включая возможность их печати. В этом руководстве мы проведем вас через процесс печати документа Word шаг за шагом.

## Настройка вашей среды

Прежде чем углубляться в код, убедитесь, что выполнены следующие предварительные условия:

- Установлен комплект разработки Java (JDK)
- Библиотека Aspose.Words for Java загружена и добавлена в ваш проект

## Загрузка документа

Для начала вам нужно загрузить документ Word, который вы хотите распечатать. Заменить `"Your Document Directory"` с путем к вашему документу и `"Your Output Directory"` с желаемым выходным каталогом.

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Rendering.docx");
```

## Создание задания на печать

Далее мы создадим задание печати для печати нашего загруженного документа. Фрагмент кода ниже инициализирует задание печати и устанавливает нужные настройки принтера.

```java
// Создайте задание на печать, чтобы распечатать наш документ.
PrinterJob pj = PrinterJob.getPrinterJob();
// Инициализируйте набор атрибутов с указанием количества страниц в документе.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// Передайте настройки принтера вместе с другими параметрами в печатный документ.
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
```

## Печать документа

Теперь, когда мы настроили наше задание печати, пришло время распечатать документ. Следующий фрагмент кода связывает документ с заданием печати и инициирует процесс печати.

```java
// Передайте документ на печать с помощью задания на печать.
pj.setPrintable(awPrintDoc);
pj.print();
```
## Полный исходный код
```java
string dataDir = "Your Document Directory";
Document doc = new Document(dataDir + "Rendering.docx");
// Создайте задание на печать, чтобы распечатать наш документ.
PrinterJob pj = PrinterJob.getPrinterJob();
// Инициализируйте набор атрибутов с указанием количества страниц в документе.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// Передайте настройки принтера вместе с другими параметрами в печатный документ.
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
// Передайте документ на печать с помощью задания на печать.
pj.setPrintable(awPrintDoc);
pj.print();
```
Исходный код MultipagePrintDocument
```java
class MultipagePrintDocument implements Printable
{
    private final Document mDocument;
    private final int mPagesPerSheet;
    private final boolean mPrintPageBorders;
    private final AttributeSet mAttributeSet;
    /// <резюме>
    /// Конструктор пользовательского класса PrintDocument.
    /// </резюме> 
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
        // Начальный и конечный индексы страницы, определенные в наборе атрибутов.
        int[][] pageRanges = ((PageRanges) mAttributeSet.get(PageRanges.class)).getMembers();
        int fromPage = pageRanges[0][0] - 1;
        int toPage = pageRanges[0][1] - 1;
        Dimension thumbCount = getThumbCount(mPagesPerSheet, pf);
        // Рассчитайте индекс страницы, которая будет отображена следующей.
        int pagesOnCurrentSheet = (int) (page * (thumbCount.getWidth() * thumbCount.getHeight()));
        // Если индекс страницы больше, чем общий диапазон страниц, то ничего нет
        // больше для визуализации.
        if (pagesOnCurrentSheet > (toPage - fromPage))
            return Printable.NO_SUCH_PAGE;
        // Рассчитайте размер каждого заполнителя миниатюры в пунктах.
        Point2D.Float thumbSize = new Point2D.Float((float) (pf.getImageableWidth() / thumbCount.getWidth()),
                (float) (pf.getImageableHeight() / thumbCount.getHeight()));
        // Подсчитайте номер первой страницы, которая будет напечатана на этом листе бумаги.
        int startPage = pagesOnCurrentSheet + fromPage;
        // Выберите номер последней страницы, которая будет напечатана на этом листе бумаги.
        int pageTo = Math.max(startPage + mPagesPerSheet - 1, toPage);
        // Перебрать выбранные страницы от сохраненной текущей страницы до вычисленной
        // последняя страница.
        for (int pageIndex = startPage; pageIndex <= pageTo; pageIndex++) {
            // Рассчитайте индексы столбцов и строк.
            int rowIdx = (int) Math.floor((pageIndex - startPage) / thumbCount.getWidth());
            int columnIdx = (int) Math.floor((pageIndex - startPage) % thumbCount.getWidth());
            // Определите местоположение миниатюры в мировых координатах (в данном случае в точках).
            float thumbLeft = columnIdx * thumbSize.x;
            float thumbTop = rowIdx * thumbSize.y;
            try {
                // Рассчитайте левую и верхнюю стартовые позиции.
                int leftPos = (int) (thumbLeft + pf.getImageableX());
                int topPos = (int) (thumbTop + pf.getImageableY());
                // Визуализируйте страницу документа в объекте Graphics, используя рассчитанные координаты.
                // и размер заполнителя миниатюры.
                // Полезным возвращаемым значением является масштаб, в котором была отображена страница.
                float scale = mDocument.renderToSize(pageIndex, (Graphics2D) g, leftPos, topPos, (int) thumbSize.x,
                        (int) thumbSize.y);
                // Нарисуйте границы страницы (миниатюра страницы может быть меньше миниатюры
                // размер заполнителя).
                if (mPrintPageBorders) {
                    // Получите реальный 100% размер страницы в пунктах.
                    Point2D.Float pageSize = mDocument.getPageInfo(pageIndex).getSizeInPoints();
                    // Нарисуйте границу вокруг масштабированной страницы, используя известный коэффициент масштабирования.
                    g.setColor(Color.black);
                    g.drawRect(leftPos, topPos, (int) (pageSize.x * scale), (int) (pageSize.y * scale));
                    // Нарисуйте рамку вокруг заполнителя миниатюры.
                    g.setColor(Color.red);
                    g.drawRect(leftPos, topPos, (int) thumbSize.x, (int) thumbSize.y);
                }
            } catch (Exception e) {
                // Если во время рендеринга возникли какие-либо ошибки, то ничего не делайте.
                // Если во время рендеринга возникнут какие-либо ошибки, будет нарисована пустая страница.
            }
        }
        return Printable.PAGE_EXISTS;
    }
    private Dimension getThumbCount(int pagesPerSheet, PageFormat pf) {
        Dimension size;
        // Определите количество столбцов и строк на листе для
        // Бумага альбомной ориентации.
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
        // Поменяйте местами ширину и высоту, если бумага имеет портретную ориентацию.
        if ((pf.getWidth() - pf.getImageableX()) < (pf.getHeight() - pf.getImageableY()))
            return new Dimension((int) size.getHeight(), (int) size.getWidth());
        return size;
	}
}
```

## Заключение

Поздравляем! Вы успешно распечатали документ Word с помощью Aspose.Words for Java. Это пошаговое руководство должно помочь вам легко интегрировать печать документов в ваши приложения Java.

## Часто задаваемые вопросы

### В1: Могу ли я распечатать определенные страницы документа с помощью Aspose.Words для Java?

Да, вы можете указать диапазон страниц при печати документа. В примере кода мы использовали `attributes.add(new PageRanges(1, doc.getPageCount()))` для печати всех страниц. Вы можете настроить диапазон страниц по мере необходимости.

### В2: Подходит ли Aspose.Words для Java для пакетной печати?

Конечно! Aspose.Words for Java хорошо подходит для пакетной печати. Вы можете перебирать список документов и печатать их один за другим, используя похожий код.

### В3: Как обрабатывать ошибки и исключения при печати?

Вам следует обрабатывать любые потенциальные исключения, которые могут возникнуть в процессе печати. Проверьте документацию Aspose.Words for Java для получения информации об обработке исключений.

### В4: Могу ли я дополнительно настроить параметры печати?

Да, вы можете настроить параметры печати в соответствии с вашими конкретными требованиями. Изучите документацию Aspose.Words for Java, чтобы узнать больше о доступных параметрах печати.

### В5: Где я могу получить дополнительную помощь и поддержку по Aspose.Words для Java?

Для получения дополнительной поддержки и помощи вы можете посетить [Форум Aspose.Words для Java](https://forum.aspose.com/).

---

Теперь, когда вы успешно научились печатать документы с помощью Aspose.Words для Java, вы можете начать внедрять эту функциональность в свои приложения Java. Удачного кодирования!


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}