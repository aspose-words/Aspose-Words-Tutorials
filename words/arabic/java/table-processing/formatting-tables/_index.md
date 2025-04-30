---
"description": "أتقن فن تنسيق الجداول في المستندات باستخدام Aspose.Words لجافا. استكشف الإرشادات خطوة بخطوة وأمثلة من أكواد المصدر لتنسيق الجداول بدقة."
"linktitle": "تنسيق الجداول في المستندات"
"second_title": "واجهة برمجة تطبيقات معالجة مستندات Java Aspose.Words"
"title": "تنسيق الجداول في المستندات"
"url": "/ar/java/table-processing/formatting-tables/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تنسيق الجداول في المستندات

## مقدمة

هل أنت مستعد للبدء بإنشاء جداول في مستندات Word بسهولة باستخدام Aspose.Words لجافا؟ الجداول أساسية لتنظيم البيانات، ومع هذه المكتبة القوية، يمكنك إنشاء جداول وتعبئتها وحتى دمجها برمجيًا في مستندات Word. في هذا الدليل المفصل، سنستكشف كيفية إنشاء الجداول ودمج الخلايا وإضافة جداول متداخلة.

## المتطلبات الأساسية

قبل البدء في الترميز، تأكد من أن لديك ما يلي:

- تم تثبيت Java Development Kit (JDK) على نظامك.
- Aspose.Words لمكتبة Java. [تحميله هنا](https://releases.aspose.com/words/java/).
- فهم أساسي لبرمجة جافا.
- بيئة تطوير متكاملة مثل IntelliJ IDEA، أو Eclipse، أو أي بيئة تطوير متكاملة أخرى تشعر بالراحة معها.
- أ [رخصة مؤقتة](https://purchase.aspose.com/temporary-license/) لفتح إمكانيات Aspose.Words الكاملة.

## استيراد الحزم

لاستخدام Aspose.Words في جافا، عليك استيراد الفئات والحزم المطلوبة. أضف هذه الاستيرادات إلى أعلى ملف جافا:

```java
import com.aspose.words.*;
```

دعونا نقسم العملية إلى خطوات صغيرة الحجم لتسهيل متابعتها بشكل كبير.

## الخطوة 1: إنشاء مستند وجدول

ما هو أول شيء تحتاجه؟ وثيقة للعمل عليها!

ابدأ بإنشاء مستند وورد جديد وجدول. أضِف الجدول إلى نص المستند.

```java
Document doc = new Document();
Table table = new Table(doc);
doc.getFirstSection().getBody().appendChild(table);
```

- `Document`:يمثل مستند Word.
- `Table`:إنشاء جدول فارغ.
- `appendChild`:يضيف الجدول إلى نص المستند.

## الخطوة 2: إضافة الصفوف والخلايا إلى الجدول

جدول بدون صفوف وخلايا؟ هذا مثل سيارة بدون عجلات! لنحل هذه المشكلة.

```java
Row firstRow = new Row(doc);
table.appendChild(firstRow);

Cell firstCell = new Cell(doc);
firstRow.appendChild(firstCell);
```

- `Row`:يمثل صفًا في الجدول.
- `Cell`:يمثل خلية في الصف.
- `appendChild`:يضيف الصفوف والخلايا إلى الجدول.

## الخطوة 3: إضافة نص إلى خلية

حان الوقت لإضافة بعض الشخصية إلى طاولتنا!

```java
Paragraph paragraph = new Paragraph(doc);
firstCell.appendChild(paragraph);

Run run = new Run(doc, "Hello world!");
paragraph.appendChild(run);
```

- `Paragraph`:إضافة فقرة إلى الخلية.
- `Run`:يضيف نصًا إلى الفقرة.

## الخطوة 4: دمج الخلايا في جدول

هل تريد دمج الخلايا لإنشاء رأس أو نطاق؟ الأمر في غاية السهولة!

```java
DocumentBuilder builder = new DocumentBuilder(doc);

builder.insertCell();
builder.getCellFormat().setHorizontalMerge(CellMerge.FIRST);
builder.write("Text in merged cells.");

builder.insertCell();
builder.getCellFormat().setHorizontalMerge(CellMerge.PREVIOUS);
builder.endRow();
```

- `DocumentBuilder`:يبسط إنشاء المستندات.
- `setHorizontalMerge`:دمج الخلايا أفقيًا.
- `write`:يضيف المحتوى إلى الخلايا المدمجة.

## الخطوة 5: إضافة الجداول المتداخلة

هل أنت مستعد للارتقاء؟ لنُضِف جدولًا داخل جدول.

```java
builder.moveTo(table.getRows().get(0).getCells().get(0).getFirstParagraph());

builder.startTable();
builder.insertCell();
builder.write("Hello world!");
builder.endTable();
```

- `moveTo`:ينقل المؤشر إلى مكان محدد في المستند.
- `startTable`:يبدأ إنشاء جدول متداخل.
- `endTable`:ينتهي الجدول المتداخل.

## خاتمة

تهانينا! لقد تعلمت كيفية إنشاء الجداول وتعبئتها وتنسيقها باستخدام Aspose.Words لجافا. من إضافة نص إلى دمج الخلايا وتضمين الجداول، أصبحت لديك الآن الأدوات اللازمة لهيكلة البيانات بفعالية في مستندات Word.

## الأسئلة الشائعة

### هل من الممكن إضافة ارتباط تشعبي إلى خلية جدول؟

نعم، يمكنك إضافة روابط تشعبية إلى خلايا الجدول في Aspose.Words لجافا. إليك الطريقة:

```java
builder.moveTo(table.getRows().get(0).getCells().get(0).getFirstParagraph());

// قم بإدراج ارتباط تشعبي وتأكيده باستخدام التنسيق المخصص.
// سيكون الرابط التشعبي عبارة عن جزء نصي قابل للنقر والذي سيأخذنا إلى الموقع المحدد في عنوان URL.
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Google website", "https://www.google.com"، خطأ)؛
```

### هل يمكنني استخدام Aspose.Words لـ Java مجانًا؟  
يمكنك استخدامه مع القيود أو الحصول عليه [نسخة تجريبية مجانية](https://releases.aspose.com/) لاستكشاف كامل إمكاناتها.

### كيف أقوم بدمج الخلايا عموديا في جدول؟  
استخدم `setVerticalMerge` طريقة `CellFormat` فئة، مماثلة للدمج الأفقي.

### هل يمكنني إضافة صور إلى خلية الجدول؟  
نعم يمكنك استخدام `DocumentBuilder` لإدراج الصور في خلايا الجدول.

### أين يمكنني العثور على المزيد من الموارد حول Aspose.Words for Java؟  
التحقق من [التوثيق](https://reference.aspose.com/words/java/) أو ال [منتدى الدعم](https://forum.aspose.com/c/words/8/) للحصول على إرشادات مفصلة.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}