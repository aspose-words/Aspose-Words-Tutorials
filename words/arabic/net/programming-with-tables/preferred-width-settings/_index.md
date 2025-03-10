---
title: إعدادات العرض المفضلة
linktitle: إعدادات العرض المفضلة
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إنشاء جداول بإعدادات عرض مطلقة ونسبية وتلقائية في Aspose.Words لـ .NET باستخدام هذا الدليل خطوة بخطوة.
weight: 10
url: /ar/net/programming-with-tables/preferred-width-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إعدادات العرض المفضلة

## مقدمة

تُعد الجداول وسيلة فعّالة لتنظيم المعلومات وتقديمها في مستندات Word. عند العمل بالجداول في Aspose.Words for .NET، تتوفر لديك عدة خيارات لتعيين عرض خلايا الجدول لضمان ملاءمتها لتخطيط المستند بشكل مثالي. سيرشدك هذا الدليل خلال عملية إنشاء الجداول بإعدادات العرض المفضلة باستخدام Aspose.Words for .NET، مع التركيز على خيارات تحديد الحجم المطلقة والنسبية والتلقائية. 

## المتطلبات الأساسية

قبل الغوص في البرنامج التعليمي، تأكد من أن لديك ما يلي:

1.  Aspose.Words for .NET: تأكد من تثبيت Aspose.Words for .NET في بيئة التطوير الخاصة بك. يمكنك تنزيله[هنا](https://releases.aspose.com/words/net/).

2. بيئة تطوير .NET: قم بإعداد بيئة تطوير .NET، مثل Visual Studio.

3. المعرفة الأساسية بلغة C#: ستساعدك المعرفة ببرمجة C# على فهم مقتطفات التعليمات البرمجية والأمثلة بشكل أفضل.

4.  توثيق Aspose.Words: راجع[توثيق Aspose.Words](https://reference.aspose.com/words/net/) لمزيد من المعلومات التفصيلية حول واجهة برمجة التطبيقات والقراءة الإضافية.

## استيراد مساحات الأسماء

قبل البدء في الترميز، تحتاج إلى استيراد المساحات الأساسية اللازمة إلى مشروع C# الخاص بك:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

توفر هذه المساحات الأسماء إمكانية الوصول إلى الوظائف الأساسية لـ Aspose.Words وكائن الجدول، مما يسمح لك بالتعامل مع جداول المستندات.

دعنا نقوم بتقسيم عملية إنشاء جدول بإعدادات عرض مفضلة مختلفة إلى خطوات واضحة وقابلة للإدارة.

## الخطوة 1: تهيئة المستند وDocumentBuilder

العنوان: إنشاء مستند جديد وDocumentBuilder

 الشرح: ابدأ بإنشاء مستند Word جديد و`DocumentBuilder` مثال.`DocumentBuilder` توفر الفئة طريقة بسيطة لإضافة المحتوى إلى مستندك.

```csharp
// قم بتحديد المسار لحفظ المستند.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// إنشاء مستند جديد.
Document doc = new Document();

// إنشاء DocumentBuilder لهذه الوثيقة.
DocumentBuilder builder = new DocumentBuilder(doc);
```

 هنا، يمكنك تحديد الدليل الذي سيتم حفظ المستند فيه وتهيئة`Document` و`DocumentBuilder` أشياء.

## الخطوة 2: إدراج الخلية الأولى في الجدول ذات العرض المطلق

أدخل الخلية الأولى في الجدول بعرض ثابت يبلغ 40 نقطة. سيضمن هذا أن تحافظ هذه الخلية دائمًا على عرض يبلغ 40 نقطة بغض النظر عن حجم الجدول.

```csharp
// إدراج خلية ذات حجم مطلق.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPoints(40);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightYellow;
builder.Writeln("Cell at 40 points width");
```

في هذه الخطوة، تبدأ في إنشاء الجدول وإدراج خلية بعرض مطلق.`PreferredWidth.FromPoints(40)` تحدد الطريقة عرض الخلية بـ 40 نقطة، و`Shading.BackgroundPatternColor` يطبق لون الخلفية الأصفر الفاتح.

## الخطوة 3: إدراج خلية ذات حجم نسبي

قم بإدراج خلية أخرى بعرض يعادل 20% من إجمالي عرض الجدول. يضمن هذا التحديد النسبي للحجم أن تتناسب الخلية بشكل متناسب مع عرض الجدول.

```csharp
// إدراج خلية ذات حجم نسبي (نسبة مئوية).
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(20);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
builder.Writeln("Cell at 20% width");
```

سيكون عرض هذه الخلية 20% من إجمالي عرض الجدول، مما يجعلها قابلة للتكيف مع أحجام شاشات مختلفة أو تخطيطات مستندات.

### الخطوة 4: إدراج خلية ذات حجم تلقائي

وأخيرًا، قم بإدراج خلية يتم تغيير حجمها تلقائيًا استنادًا إلى المساحة المتوفرة المتبقية في الجدول.

```csharp
// إدراج خلية ذات حجم تلقائي.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.Auto;
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightGreen;
builder.Writeln("Cell automatically sized. The size of this cell is calculated from the table preferred width.");
builder.Writeln("In this case the cell will fill up the rest of the available space.");
```

 ال`PreferredWidth.Auto` يتيح الإعداد لهذه الخلية التمدد أو الانكماش بناءً على المساحة المتبقية بعد احتساب الخلايا الأخرى. وهذا يضمن أن يبدو تخطيط الجدول متوازنًا واحترافيًا.

## الخطوة 5: الانتهاء من المستند وحفظه

بمجرد إدراج جميع الخلايا، أكمل الجدول واحفظ المستند في المسار المحدد.

```csharp
// احفظ المستند.
doc.Save(dataDir + "WorkingWithTables.PreferredWidthSettings.docx");
```

تؤدي هذه الخطوة إلى إنهاء الجدول وحفظ المستند باسم الملف "WorkingWithTables.PreferredWidthSettings.docx" في الدليل المخصص لك.

## خاتمة

إن إنشاء جداول بإعدادات العرض المفضلة في Aspose.Words for .NET أمر بسيط بمجرد فهم خيارات تحديد الحجم المختلفة المتاحة. سواء كنت بحاجة إلى عرض خلايا ثابت أو نسبي أو تلقائي، يوفر لك Aspose.Words المرونة اللازمة للتعامل بكفاءة مع سيناريوهات تخطيط الجدول المختلفة. باتباع الخطوات الموضحة في هذا الدليل، يمكنك ضمان أن تكون جداولك منظمة بشكل جيد وجذابة بصريًا في مستندات Word الخاصة بك.

## الأسئلة الشائعة

### ما هو الفرق بين العرض المطلق والعرض النسبي للخلايا؟
تكون عروض الخلايا المطلقة ثابتة ولا تتغير، بينما يتم تعديل العروض النسبية استنادًا إلى العرض الإجمالي للجدول.

### هل يمكنني استخدام النسب السلبية للعرض النسبي؟
لا، النسب المئوية السلبية غير صالحة لعرض الخلايا. النسب المئوية الإيجابية فقط هي المسموح بها.

### كيف تعمل ميزة تغيير الحجم التلقائي؟
ضبط الحجم التلقائي يضبط عرض الخلية لملء أي مساحة متبقية في الجدول بعد تحديد حجم الخلايا الأخرى.

### هل يمكنني تطبيق أنماط مختلفة على خلايا ذات إعدادات عرض مختلفة؟
نعم، يمكنك تطبيق أنماط وتنسيقات مختلفة على الخلايا بغض النظر عن إعدادات عرضها.

### ماذا يحدث إذا كان العرض الإجمالي للجدول أقل من مجموع عرض كل الخلايا؟
سيقوم الجدول تلقائيًا بتعديل عرض الخلايا لتناسب المساحة المتوفرة، مما قد يؤدي إلى انكماش بعض الخلايا.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
