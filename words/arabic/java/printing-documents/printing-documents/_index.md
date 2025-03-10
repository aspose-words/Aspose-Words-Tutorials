---
title: طباعة المستندات في Aspose.Words للغة Java
linktitle: طباعة المستندات
second_title: واجهة برمجة تطبيقات معالجة المستندات في Java Aspose.Words
description: تعرف على كيفية طباعة المستندات باستخدام Aspose.Words for Java. دليل خطوة بخطوة للطباعة بسلاسة في تطبيقات Java الخاصة بك.
weight: 10
url: /ar/java/printing-documents/printing-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# طباعة المستندات في Aspose.Words للغة Java


إذا كنت تبحث عن طباعة مستندات باستخدام Aspose.Words for Java، فأنت في المكان المناسب. في هذا الدليل التفصيلي، سنوضح لك عملية طباعة المستندات باستخدام Aspose.Words for Java باستخدام الكود المصدر المقدم.

## مقدمة

تُعد طباعة المستندات مهمة شائعة في العديد من التطبيقات. يوفر Aspose.Words for Java واجهة برمجة تطبيقات قوية للعمل مع مستندات Word، بما في ذلك القدرة على طباعتها. في هذا البرنامج التعليمي، سنرشدك خلال عملية طباعة مستند Word خطوة بخطوة.

## إعداد البيئة الخاصة بك

قبل أن نتعمق في الكود، تأكد من توفر المتطلبات الأساسية التالية:

- تم تثبيت Java Development Kit (JDK)
- تم تنزيل مكتبة Aspose.Words for Java وإضافتها إلى مشروعك

## تحميل المستند

 للبدء، ستحتاج إلى تحميل مستند Word الذي تريد طباعته. استبدل`"Your Document Directory"` مع المسار إلى مستندك و`"Your Output Directory"` مع دليل الإخراج المطلوب.

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Rendering.docx");
```

## إنشاء مهمة طباعة

بعد ذلك، سننشئ مهمة طباعة لطباعة المستند المحمّل. يقوم مقطع التعليمات البرمجية أدناه بتهيئة مهمة الطباعة وتعيين إعدادات الطابعة المطلوبة.

```java
// قم بإنشاء مهمة طباعة لطباعة مستندنا بها.
PrinterJob pj = PrinterJob.getPrinterJob();
// قم بتهيئة مجموعة السمات باستخدام عدد الصفحات الموجودة في المستند.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// قم بتمرير إعدادات الطابعة مع المعلمات الأخرى إلى مستند الطباعة.
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
```

## طباعة الوثيقة

الآن بعد أن قمنا بإعداد مهمة الطباعة، حان الوقت لطباعة المستند. يقوم مقطع التعليمات البرمجية التالي بربط المستند بمهمة الطباعة وبدء عملية الطباعة.

```java
// قم بتمرير المستند المراد طباعته باستخدام مهمة الطباعة.
pj.setPrintable(awPrintDoc);
pj.print();
```
## الكود المصدر الكامل
```java
string dataDir = "Your Document Directory";
Document doc = new Document(dataDir + "Rendering.docx");
// قم بإنشاء مهمة طباعة لطباعة مستندنا بها.
PrinterJob pj = PrinterJob.getPrinterJob();
// قم بتهيئة مجموعة السمات باستخدام عدد الصفحات الموجودة في المستند.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// قم بتمرير إعدادات الطابعة مع المعلمات الأخرى إلى مستند الطباعة.
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
// قم بتمرير المستند المراد طباعته باستخدام مهمة الطباعة.
pj.setPrintable(awPrintDoc);
pj.print();
```
الكود المصدر لـ MultipagePrintDocument
```java
class MultipagePrintDocument implements Printable
{
    private final Document mDocument;
    private final int mPagesPerSheet;
    private final boolean mPrintPageBorders;
    private final AttributeSet mAttributeSet;
    /// <ملخص>
    ///منشئ فئة PrintDocument المخصصة.
    // / </ملخص>
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
        //مؤشرات بداية ونهاية الصفحة كما هو محدد في مجموعة السمات.
        int[][] pageRanges = ((PageRanges) mAttributeSet.get(PageRanges.class)).getMembers();
        int fromPage = pageRanges[0][0] - 1;
        int toPage = pageRanges[0][1] - 1;
        Dimension thumbCount = getThumbCount(mPagesPerSheet, pf);
        // احسب مؤشر الصفحة الذي سيتم عرضه بعد ذلك.
        int pagesOnCurrentSheet = (int) (page * (thumbCount.getWidth() * thumbCount.getHeight()));
        // إذا كان فهرس الصفحة أكبر من نطاق الصفحات الإجمالي، فلا يوجد شيء
        // المزيد لتقديمه.
        if (pagesOnCurrentSheet > (toPage - fromPage))
            return Printable.NO_SUCH_PAGE;
        // احسب حجم كل عنصر نائب للصورة المصغرة بالنقاط.
        Point2D.Float thumbSize = new Point2D.Float((float) (pf.getImageableWidth() / thumbCount.getWidth()),
                (float) (pf.getImageableHeight() / thumbCount.getHeight()));
        // احسب رقم الصفحة الأولى التي سيتم طباعتها على هذه الورقة.
        int startPage = pagesOnCurrentSheet + fromPage;
        // قم باختيار رقم الصفحة الأخيرة التي سيتم طباعتها على هذه الورقة.
        int pageTo = Math.max(startPage + mPagesPerSheet - 1, toPage);
        // قم بالتنقل عبر الصفحات المحددة من الصفحة الحالية المخزنة إلى الصفحة المحسوبة
        // الصفحة الاخيرة
        for (int pageIndex = startPage; pageIndex <= pageTo; pageIndex++) {
            // حساب مؤشرات العمود والصف.
            int rowIdx = (int) Math.floor((pageIndex - startPage) / thumbCount.getWidth());
            int columnIdx = (int) Math.floor((pageIndex - startPage) % thumbCount.getWidth());
            // قم بتحديد موقع الصورة المصغرة في إحداثيات العالم (النقاط في هذه الحالة).
            float thumbLeft = columnIdx * thumbSize.x;
            float thumbTop = rowIdx * thumbSize.y;
            try {
                // احسب موضع البداية الأيسر والأعلى.
                int leftPos = (int) (thumbLeft + pf.getImageableX());
                int topPos = (int) (thumbTop + pf.getImageableY());
                // عرض صفحة المستند إلى كائن الرسومات باستخدام الإحداثيات المحسوبة
                // وحجم العنصر المصغر.
                // قيمة الإرجاع المفيدة هي المقياس الذي تم عرض الصفحة به.
                float scale = mDocument.renderToSize(pageIndex, (Graphics2D) g, leftPos, topPos, (int) thumbSize.x,
                        (int) thumbSize.y);
                //ارسم حدود الصفحة (يمكن أن تكون الصورة المصغرة للصفحة أصغر من الصورة المصغرة)
                // حجم العنصر النائب).
                if (mPrintPageBorders) {
                    // احصل على الحجم الحقيقي للصفحة بنسبة 100٪ بالنقاط.
                    Point2D.Float pageSize = mDocument.getPageInfo(pageIndex).getSizeInPoints();
                    // ارسم الحدود حول الصفحة المُدرجة باستخدام عامل المقياس المعروف.
                    g.setColor(Color.black);
                    g.drawRect(leftPos, topPos, (int) (pageSize.x * scale), (int) (pageSize.y * scale));
                    // ارسم الحدود حول العنصر النائب للصورة المصغرة.
                    g.setColor(Color.red);
                    g.drawRect(leftPos, topPos, (int) thumbSize.x, (int) thumbSize.y);
                }
            } catch (Exception e) {
                // إذا حدثت أي أخطاء أثناء العرض، فلا تفعل شيئًا.
                // سيؤدي هذا إلى رسم صفحة فارغة إذا كانت هناك أي أخطاء أثناء العرض.
            }
        }
        return Printable.PAGE_EXISTS;
    }
    private Dimension getThumbCount(int pagesPerSheet, PageFormat pf) {
        Dimension size;
        // قم بتحديد عدد الأعمدة والصفوف في الورقة
        // ورق موجه للمناظر الطبيعية.
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
        // قم بتبديل العرض والارتفاع إذا كان الورق في الاتجاه الرأسي.
        if ((pf.getWidth() - pf.getImageableX()) < (pf.getHeight() - pf.getImageableY()))
            return new Dimension((int) size.getHeight(), (int) size.getWidth());
        return size;
	}
}
```

## خاتمة

تهانينا! لقد نجحت في طباعة مستند Word باستخدام Aspose.Words for Java. سيساعدك هذا الدليل التفصيلي على دمج طباعة المستندات في تطبيقات Java بسلاسة.

## الأسئلة الشائعة

### س1: هل يمكنني طباعة صفحات محددة من مستند باستخدام Aspose.Words لـ Java؟

 نعم، يمكنك تحديد نطاق الصفحات عند طباعة مستند. في مثال الكود، استخدمنا`attributes.add(new PageRanges(1, doc.getPageCount()))`لطباعة كافة الصفحات. يمكنك تعديل نطاق الصفحات حسب الحاجة.

### س2: هل Aspose.Words for Java مناسب للطباعة الدفعية؟

بالتأكيد! يعد برنامج Aspose.Words for Java مناسبًا جدًا لمهام الطباعة الدفعية. يمكنك تكرار قائمة من المستندات وطباعتها واحدة تلو الأخرى باستخدام كود مماثل.

### س3: كيف يمكنني التعامل مع أخطاء الطباعة أو الاستثناءات؟

يجب عليك التعامل مع أي استثناءات محتملة قد تحدث أثناء عملية الطباعة. راجع وثائق Aspose.Words for Java للحصول على معلومات حول التعامل مع الاستثناءات.

### س4: هل يمكنني تخصيص إعدادات الطباعة بشكل أكبر؟

نعم، يمكنك تخصيص إعدادات الطباعة لتلبية متطلباتك المحددة. استكشف وثائق Aspose.Words for Java لمعرفة المزيد حول خيارات الطباعة المتاحة.

### س5: أين يمكنني الحصول على مزيد من المساعدة والدعم لـ Aspose.Words لـ Java؟

 لمزيد من الدعم والمساعدة، يمكنك زيارة[منتدى Aspose.Words للغة Java](https://forum.aspose.com/).

---

الآن بعد أن تعلمت بنجاح كيفية طباعة المستندات باستخدام Aspose.Words for Java، يمكنك البدء في تنفيذ هذه الوظيفة في تطبيقات Java الخاصة بك. استمتع بالبرمجة!
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
