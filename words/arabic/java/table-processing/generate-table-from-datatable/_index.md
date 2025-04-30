---
"description": "تعلّم كيفية إنشاء جدول من جدول بيانات باستخدام Aspose.Words لجافا. أنشئ مستندات Word احترافية بجداول منسقة بكل سهولة."
"linktitle": "إنشاء جدول من جدول البيانات"
"second_title": "واجهة برمجة تطبيقات معالجة مستندات Java Aspose.Words"
"title": "إنشاء جدول من جدول البيانات"
"url": "/ar/java/table-processing/generate-table-from-datatable/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء جدول من جدول البيانات

## مقدمة

إنشاء الجداول ديناميكيًا من مصادر البيانات مهمة شائعة في العديد من التطبيقات. سواء كنت تُنشئ تقارير أو فواتير أو ملخصات بيانات، فإن ملء جدول بالبيانات برمجيًا يوفر عليك الكثير من الوقت والجهد. في هذا البرنامج التعليمي، سنستكشف كيفية إنشاء جدول من جدول بيانات باستخدام Aspose.Words لجافا. سنقسم العملية إلى خطوات سهلة، لضمان فهمك الواضح لكل جزء.

## المتطلبات الأساسية

قبل الغوص في الكود، دعنا نتأكد من أن لديك كل ما تحتاجه للبدء:

1. مجموعة تطوير جافا (JDK): تأكد من تثبيت JDK على جهازك. يمكنك تنزيله من [موقع أوراكل](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html).
   
2. Aspose.Words لجافا: ستحتاج إلى مكتبة Aspose.Words. يمكنك تنزيل أحدث إصدار من [صفحة إصدارات Aspose](https://releases.aspose.com/words/java/).

3. IDE: بيئة التطوير المتكاملة (IDE) مثل IntelliJ IDEA أو Eclipse ستجعل عملية الترميز أسهل.

4. المعرفة الأساسية بلغة جافا: ستساعدك المعرفة بمفاهيم برمجة جافا على فهم مقتطفات التعليمات البرمجية بشكل أفضل.

5. بيانات نموذجية: في هذا البرنامج التعليمي، سنستخدم ملف XML باسم "List of people.xml" لمحاكاة مصدر بيانات. يمكنك إنشاء هذا الملف ببيانات نموذجية للاختبار.

## الخطوة 1: إنشاء مستند جديد

أولاً، علينا إنشاء مستند جديد حيث سيكون جدولنا. هذا هو مساحة العمل.

```java
Document doc = new Document();
```

هنا، نقوم بإنشاء مثيل جديد `Document` هذا الكائن سيكون بمثابة وثيقة العمل التي سنقوم من خلالها ببناء الجدول الخاص بنا.

## الخطوة 2: تهيئة DocumentBuilder

بعد ذلك سوف نستخدم `DocumentBuilder` الفئة التي تسمح لنا بالتعامل مع المستند بسهولة أكبر.

```java
DocumentBuilder builder = new DocumentBuilder(doc);
```

ال `DocumentBuilder` يوفر الكائن طرقًا لإدراج الجداول والنصوص والعناصر الأخرى في المستند.

## الخطوة 3: تعيين اتجاه الصفحة

نظرًا لأننا نتوقع أن يكون جدولنا عريضًا، فسنقوم بتعيين اتجاه الصفحة إلى أفقي.

```java
doc.getFirstSection().getPageSetup().setOrientation(Orientation.LANDSCAPE);
```

تعتبر هذه الخطوة بالغة الأهمية لأنها تضمن أن يتناسب جدولنا بشكل جيد مع الصفحة دون أن يتم قطعه.

## الخطوة 4: تحميل البيانات من XML

الآن، نحتاج إلى تحميل بياناتنا من ملف XML إلى `DataTable`.ومن هنا تأتي بياناتنا.

```java
DataSet ds = new DataSet();
ds.readXml(getMyDir() + "List of people.xml");
DataTable dataTable = ds.getTables().get(0);
```

هنا، نقرأ ملف XML ونسترد الجدول الأول من مجموعة البيانات. هذا `DataTable` سوف تحتوي على البيانات التي نريد عرضها في مستندنا.

## الخطوة 5: استيراد الجدول من DataTable

الآن يأتي الجزء المثير: استيراد بياناتنا إلى المستند كجدول.

```java
Table table = importTableFromDataTable(builder, dataTable, true);
```

نحن نسمي هذه الطريقة `importTableFromDataTable`، مروراً `DocumentBuilder`، ملكنا `DataTable`، وقيمة منطقية للإشارة إلى ما إذا كان سيتم تضمين عناوين الأعمدة.

## الخطوة 6: تصميم الجدول

بمجرد أن نحصل على طاولتنا، يمكننا تطبيق بعض التصميمات عليها لجعلها تبدو جيدة.

```java
table.setStyleIdentifier(StyleIdentifier.MEDIUM_LIST_2_ACCENT_1);
table.setStyleOptions(TableStyleOptions.FIRST_ROW | TableStyleOptions.ROW_BANDS | TableStyleOptions.LAST_COLUMN);
```

يطبق هذا الكود نمطًا محددًا مسبقًا على الجدول، مما يعزز جاذبيته البصرية وسهولة قراءته.

## الخطوة 7: إزالة الخلايا غير المرغوب فيها

إذا كان لديك أي أعمدة لا تريد عرضها، مثل عمود الصورة، فيمكنك إزالته بسهولة.

```java
table.getFirstRow().getLastCell().removeAllChildren();
```

تضمن هذه الخطوة أن يعرض جدولنا المعلومات ذات الصلة فقط.

## الخطوة 8: حفظ المستند

وأخيرًا، نحفظ مستندنا بالجدول الناتج.

```java
doc.save(getArtifactsDir() + "WorkingWithTables.BuildTableFromDataTable.docx");
```

يحفظ هذا السطر المستند في الدليل المحدد، مما يسمح لك بمراجعة النتائج.

## طريقة importTableFromDataTable

دعونا نلقي نظرة عن كثب على `importTableFromDataTable` الطريقة. هذه الطريقة مسؤولة عن إنشاء بنية الجدول وملئها بالبيانات.

### الخطوة 1: ابدأ الجدول

أولاً، نحتاج إلى بدء جدول جديد في المستند.

```java
Table table = builder.startTable();
```

يؤدي هذا إلى تهيئة جدول جديد في مستندنا.

### الخطوة 2: إضافة عناوين الأعمدة

إذا أردنا تضمين عناوين الأعمدة، نتحقق من `importColumnHeadings` علَم.

```java
if (importColumnHeadings) {
    // تخزين التنسيق الأصلي
    boolean boldValue = builder.getFont().getBold();
    int paragraphAlignmentValue = builder.getParagraphFormat().getAlignment();

    // تعيين تنسيق العنوان
    builder.getFont().setBold(true);
    builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

    // إدراج أسماء الأعمدة
    for (DataColumn column : dataTable.getColumns()) {
        builder.insertCell();
        builder.writeln(column.getColumnName());
    }

    builder.endRow();

    // استعادة التنسيق الأصلي
    builder.getFont().setBold(boldValue);
    builder.getParagraphFormat().setAlignment(paragraphAlignmentValue);
}
```

يقوم هذا الكتلة من التعليمات البرمجية بتنسيق صف العنوان وإدراج أسماء الأعمدة من `DataTable`.

### الخطوة 3: ملء الجدول بالبيانات

الآن، نقوم بالمرور على كل صف من `DataTable` لإدراج البيانات في الجدول.

```java
for (DataRow dataRow : (Iterable<DataRow>) dataTable.getRows()) {
    for (Object item : dataRow.getItemArray()) {
        builder.insertCell();
        switch (item.getClass().getName()) {
            case "DateTime":
                Date dateTime = (Date) item;
                SimpleDateFormat simpleDateFormat = new SimpleDateFormat("MMMM d, yyyy");
                builder.write(simpleDateFormat.format(dateTime));
                break;
            default:
                builder.write(item.toString());
                break;
        }
    }
    builder.endRow();
}
```

في هذا القسم، سنتعامل مع أنواع مختلفة من البيانات، وتنسيق التواريخ بشكل مناسب أثناء إدراج بيانات أخرى كنص.

### الخطوة 4: إنهاء الجدول

وأخيرًا، ننتهي من الجدول بعد إدخال كافة البيانات.

```java
builder.endTable();
```

يشير هذا الخط إلى نهاية جدولنا، مما يسمح بـ `DocumentBuilder` لنعلم أننا انتهينا من هذا القسم.

## خاتمة

ها قد انتهيت! لقد تعلمت بنجاح كيفية إنشاء جدول من جدول بيانات باستخدام Aspose.Words لجافا. باتباع هذه الخطوات، يمكنك بسهولة إنشاء جداول ديناميكية في مستنداتك استنادًا إلى مصادر بيانات متنوعة. سواء كنت تُنشئ تقارير أو فواتير، ستُبسط هذه الطريقة سير عملك وتُحسّن عملية إنشاء مستنداتك.

## الأسئلة الشائعة

### ما هو Aspose.Words لـ Java؟
Aspose.Words for Java هي مكتبة قوية لإنشاء مستندات Word ومعالجتها وتحويلها برمجيًا.

### هل يمكنني استخدام Aspose.Words مجانًا؟
نعم، يُقدّم Aspose نسخة تجريبية مجانية. يُمكنك تنزيلها من [هنا](https://releases.aspose.com/).

### كيف أقوم بتنسيق الجداول في Aspose.Words؟
بإمكانك تطبيق الأنماط باستخدام معرفات الأنماط المحددة مسبقًا والخيارات التي توفرها المكتبة.

### ما هي أنواع البيانات التي يمكنني إدراجها في الجداول؟
يمكنك إدراج أنواع مختلفة من البيانات، بما في ذلك النصوص والأرقام والتاريخ، والتي يمكن تنسيقها وفقًا لذلك.

### أين يمكنني الحصول على الدعم لـ Aspose.Words؟
يمكنك العثور على الدعم وطرح الأسئلة على [منتدى Aspose](https://forum.aspose.com/c/words/8/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}