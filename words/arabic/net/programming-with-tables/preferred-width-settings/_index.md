---
"description": "تعرف على كيفية إنشاء جداول بإعدادات العرض المطلق والنسب والتلقائي في Aspose.Words لـ .NET باستخدام هذا الدليل خطوة بخطوة."
"linktitle": "إعدادات العرض المفضلة"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "إعدادات العرض المفضلة"
"url": "/ar/net/programming-with-tables/preferred-width-settings/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إعدادات العرض المفضلة

## مقدمة

تُعد الجداول وسيلة فعّالة لتنظيم المعلومات وعرضها في مستندات Word. عند العمل مع الجداول في Aspose.Words لـ .NET، تتوفر لديك عدة خيارات لضبط عرض خلايا الجدول لضمان ملاءمتها لتخطيط مستندك تمامًا. سيرشدك هذا الدليل خلال عملية إنشاء الجداول بإعدادات العرض المفضلة لديك باستخدام Aspose.Words لـ .NET، مع التركيز على خيارات تغيير الحجم المطلق والنسبي والتلقائي. 

## المتطلبات الأساسية

قبل الغوص في البرنامج التعليمي، تأكد من أن لديك ما يلي:

1. Aspose.Words for .NET: تأكد من تثبيت Aspose.Words for .NET في بيئة التطوير لديك. يمكنك تنزيله. [هنا](https://releases.aspose.com/words/net/).

2. بيئة تطوير .NET: قم بإعداد بيئة تطوير .NET، مثل Visual Studio.

3. المعرفة الأساسية بلغة C#: ستساعدك المعرفة ببرمجة C# على فهم مقتطفات التعليمات البرمجية والأمثلة بشكل أفضل.

4. توثيق Aspose.Words: راجع [توثيق Aspose.Words](https://reference.aspose.com/words/net/) للحصول على معلومات مفصلة حول واجهة برمجة التطبيقات (API) وقراءة المزيد.

## استيراد مساحات الأسماء

قبل البدء في الترميز، تحتاج إلى استيراد المساحات الأساسية اللازمة إلى مشروع C# الخاص بك:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

توفر هذه المساحات الاسمية إمكانية الوصول إلى الوظائف الأساسية لـ Aspose.Words وكائن Table، مما يسمح لك بالتعامل مع جداول المستندات.

دعنا نقسم عملية إنشاء جدول بإعدادات عرض مفضلة مختلفة إلى خطوات واضحة وقابلة للإدارة.

## الخطوة 1: تهيئة المستند وDocumentBuilder

العنوان: إنشاء مستند جديد وDocumentBuilder

الشرح: ابدأ بإنشاء مستند Word جديد و `DocumentBuilder` مثال. ال `DocumentBuilder` توفر الفئة طريقة بسيطة لإضافة المحتوى إلى مستندك.

```csharp
// قم بتحديد المسار لحفظ المستند.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// إنشاء مستند جديد.
Document doc = new Document();

// إنشاء DocumentBuilder لهذه الوثيقة.
DocumentBuilder builder = new DocumentBuilder(doc);
```

هنا، يمكنك تحديد الدليل الذي سيتم حفظ المستند فيه وتهيئة `Document` و `DocumentBuilder` أشياء.

## الخطوة 2: إدراج الخلية الأولى في الجدول ذات العرض المطلق

أدخل الخلية الأولى في الجدول بعرض ثابت قدره 40 نقطة. سيضمن هذا بقاء عرض هذه الخلية ثابتًا بغض النظر عن حجم الجدول.

```csharp
// إدراج خلية ذات حجم مطلق.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPoints(40);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightYellow;
builder.Writeln("Cell at 40 points width");
```

في هذه الخطوة، تبدأ بإنشاء الجدول وإدراج خلية بعرض مطلق. `PreferredWidth.FromPoints(40)` تحدد الطريقة عرض الخلية بـ 40 نقطة، و `Shading.BackgroundPatternColor` يطبق لون الخلفية باللون الأصفر الفاتح.

## الخطوة 3: إدراج خلية ذات حجم نسبي

أدرج خلية أخرى بعرض ٢٠٪ من إجمالي عرض الجدول. يضمن هذا التحديد النسبي لحجم الخلية تناسبًا متناسبًا مع عرض الجدول.

```csharp
// إدراج خلية ذات حجم نسبي (نسبة مئوية).
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(20);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
builder.Writeln("Cell at 20% width");
```

سيكون عرض هذه الخلية 20% من العرض الإجمالي للجدول، مما يجعلها قابلة للتكيف مع أحجام شاشات مختلفة أو تخطيطات مستندات.

### الخطوة 4: إدراج خلية ذات حجم تلقائي

أخيرًا، قم بإدراج خلية يتم تغيير حجمها تلقائيًا استنادًا إلى المساحة المتوفرة المتبقية في الجدول.

```csharp
// إدراج خلية ذات حجم تلقائي.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.Auto;
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightGreen;
builder.Writeln("Cell automatically sized. ال size of this cell is calculated from the table preferred width.");
builder.Writeln("In this case the cell will fill up the rest of the available space.");
```

The `PreferredWidth.Auto` يسمح هذا الإعداد بتوسيع هذه الخلية أو تقليصها بناءً على المساحة المتبقية بعد احتساب الخلايا الأخرى. هذا يضمن أن يبدو تصميم الجدول متوازنًا واحترافيًا.

## الخطوة 5: إنهاء المستند وحفظه

بمجرد إدراج جميع الخلايا، أكمل الجدول واحفظ المستند في المسار المحدد.

```csharp
// احفظ المستند.
doc.Save(dataDir + "WorkingWithTables.PreferredWidthSettings.docx");
```

تؤدي هذه الخطوة إلى إنهاء الجدول وحفظ المستند باسم الملف "WorkingWithTables.PreferredWidthSettings.docx" في الدليل المخصص لك.

## خاتمة

إنشاء جداول بإعدادات العرض المفضلة في Aspose.Words لـ .NET سهلٌ للغاية بمجرد فهم خيارات تغيير الحجم المختلفة المتاحة. سواءً كنت بحاجة إلى عرض خلايا ثابت، أو نسبي، أو تلقائي، يوفر Aspose.Words المرونة اللازمة للتعامل بكفاءة مع مختلف سيناريوهات تخطيط الجداول. باتباع الخطوات الموضحة في هذا الدليل، يمكنك ضمان تنظيم جداولك بشكل جيد وجاذبية بصريًا في مستندات Word.

## الأسئلة الشائعة

### ما هو الفرق بين العرض المطلق والعرض النسبي للخلايا؟
تكون عروض الخلايا المطلقة ثابتة ولا تتغير، بينما يتم تعديل العروض النسبية استنادًا إلى العرض الإجمالي للجدول.

### هل يمكنني استخدام النسب المئوية السلبية للعرض النسبي؟
لا، النسب المئوية السالبة غير صالحة لعرض الخلايا. النسب المئوية الموجبة فقط مسموح بها.

### كيف تعمل ميزة تغيير الحجم تلقائيًا؟
يتيح لك تغيير الحجم تلقائيًا ضبط عرض الخلية لملء أي مساحة متبقية في الجدول بعد تغيير حجم الخلايا الأخرى.

### هل يمكنني تطبيق أنماط مختلفة على خلايا ذات إعدادات عرض مختلفة؟
نعم، يمكنك تطبيق أنماط وتنسيقات مختلفة على الخلايا بغض النظر عن إعدادات عرضها.

### ماذا يحدث إذا كان العرض الإجمالي للجدول أقل من مجموع عرض كل الخلايا؟
سيقوم الجدول تلقائيًا بتعديل عرض الخلايا لتناسب المساحة المتوفرة، مما قد يؤدي إلى انكماش بعض الخلايا.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}