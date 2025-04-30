---
"description": "تعلّم كيفية إنشاء مستندات Word بصفوف عناوين جداول متكررة باستخدام Aspose.Words لـ .NET. اتبع هذا الدليل لضمان مستندات احترافية ومُحسّنة."
"linktitle": "كرر الصفوف في الصفحات اللاحقة"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "كرر الصفوف في الصفحات اللاحقة"
"url": "/ar/net/programming-with-tables/repeat-rows-on-subsequent-pages/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# كرر الصفوف في الصفحات اللاحقة

## مقدمة

إنشاء مستند وورد برمجيًا قد يكون مهمة شاقة، خاصةً عند الحاجة إلى الحفاظ على التنسيق عبر صفحات متعددة. هل سبق لك أن حاولت إنشاء جدول في وورد، ثم اكتشفت أن صفوف العناوين لا تتكرر في الصفحات التالية؟ لا تقلق! مع Aspose.Words لـ .NET، يمكنك بسهولة ضمان تكرار عناوين الجداول في كل صفحة، مما يضفي مظهرًا احترافيًا وأنيقًا على مستنداتك. في هذا البرنامج التعليمي، سنشرح لك خطوات تحقيق ذلك باستخدام أمثلة برمجية بسيطة وشروحات مفصلة. هيا بنا!

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

1. Aspose.Words for .NET: يمكنك تنزيله [هنا](https://releases.aspose.com/words/net/).
2. تم تثبيت .NET Framework على جهازك.
3. Visual Studio أو أي IDE آخر يدعم تطوير .NET.
4. فهم أساسي لبرمجة C#.

تأكد من تثبيت Aspose.Words لـ .NET وإعداد بيئة التطوير الخاصة بك قبل المتابعة.

## استيراد مساحات الأسماء

للبدء، عليك استيراد مساحات الأسماء اللازمة في مشروعك. أضف التعليمات التالية في أعلى ملف C#:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

تتضمن هذه المساحات الأسماء الفئات والطرق المطلوبة للتعامل مع مستندات Word والجداول.

## الخطوة 1: تهيئة المستند

أولاً، دعنا ننشئ مستند Word جديدًا و `DocumentBuilder` لبناء جدولنا.

```csharp
// المسار إلى دليل المستندات الخاص بك 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

يقوم هذا الكود بإنشاء مستند جديد و `DocumentBuilder` الكائن الذي يساعد في بناء بنية المستند.

## الخطوة 2: بدء الجدول وتحديد صفوف الرأس

بعد ذلك، سنبدأ الجدول ونحدد صفوف الرأس التي نريد تكرارها في الصفحات اللاحقة.

```csharp
builder.StartTable();
builder.RowFormat.HeadingFormat = true;
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.CellFormat.Width = 100;

builder.InsertCell();
builder.Writeln("Heading row 1");
builder.EndRow();

builder.InsertCell();
builder.Writeln("Heading row 2");
builder.EndRow();
```

هنا نبدأ جدولًا جديدًا، ونضبط `HeadingFormat` الممتلكات إلى `true` للإشارة إلى أن الصفوف هي رؤوس، وتحديد محاذاة وعرض الخلايا.

## الخطوة 3: إضافة صفوف البيانات إلى الجدول

الآن، سنضيف صفوف بيانات متعددة إلى جدولنا. لن تتكرر هذه الصفوف في الصفحات اللاحقة.

```csharp
builder.CellFormat.Width = 50;
builder.ParagraphFormat.ClearFormatting();
for (int i = 0; i < 50; i++)
{
    builder.InsertCell();
    builder.RowFormat.HeadingFormat = false;
    builder.Write("Column 1 Text");
    
    builder.InsertCell();
    builder.Write("Column 2 Text");
    builder.EndRow();
}
```

تقوم هذه الحلقة بإدراج 50 صفًا من البيانات في الجدول، مع عمودين في كل صف. `HeadingFormat` تم ضبطه على `false` لهذه الصفوف، لأنها ليست صفوف رأسية.

## الخطوة 4: حفظ المستند

وأخيرًا، نقوم بحفظ المستند في الدليل المحدد.

```csharp
doc.Save(dataDir + "WorkingWithTables.RepeatRowsOnSubsequentPages.docx");
```

يؤدي هذا إلى حفظ المستند بالاسم المحدد في دليل المستند الخاص بك.

## خاتمة

وهذا كل ما في الأمر! ببضعة أسطر برمجية فقط، يمكنك إنشاء مستند Word بجداول تحتوي على صفوف عناوين متكررة في الصفحات التالية باستخدام Aspose.Words لـ .NET. هذا لا يُحسّن سهولة قراءة مستنداتك فحسب، بل يضمن أيضًا مظهرًا متناسقًا واحترافيًا. الآن، جرّب هذا في مشاريعك!

## الأسئلة الشائعة

### هل يمكنني تخصيص صفوف الرأس بشكل أكبر؟
نعم، يمكنك تطبيق تنسيق إضافي على صفوف الرأس عن طريق تعديل خصائص `ParagraphFormat`، `RowFormat`، و `CellFormat`.

### هل من الممكن إضافة المزيد من الأعمدة إلى الجدول؟
بالتأكيد! يمكنك إضافة أي عدد من الأعمدة عن طريق إدخال المزيد من الخلايا داخل `InsertCell` طريقة.

### كيف يمكنني جعل الصفوف الأخرى تتكرر في الصفحات اللاحقة؟
لتكرار أي صف، اضبط `RowFormat.HeadingFormat` الممتلكات إلى `true` لهذا الصف المحدد.

### هل يمكنني استخدام هذه الطريقة للجداول الموجودة في مستند؟
نعم، يمكنك تعديل الجداول الموجودة عن طريق الوصول إليها من خلال `Document` الكائن وتطبيق تنسيق مماثل.

### ما هي خيارات تنسيق الجدول الأخرى المتوفرة في Aspose.Words لـ .NET؟
يوفر Aspose.Words لـ .NET مجموعة واسعة من خيارات تنسيق الجداول، بما في ذلك دمج الخلايا، وإعدادات الحدود، ومحاذاة الجدول. اطلع على [التوثيق](https://reference.aspose.com/words/net/) لمزيد من التفاصيل.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}