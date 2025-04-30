---
"description": "تعرّف على كيفية تصدير مستندات Word إلى Markdown مع جداول مُحاذاة باستخدام Aspose.Words لـ .NET. اتبع دليلنا خطوة بخطوة لإنشاء جداول Markdown مثالية."
"linktitle": "التصدير إلى Markdown مع محاذاة محتوى الجدول"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "التصدير إلى Markdown مع محاذاة محتوى الجدول"
"url": "/ar/net/programming-with-markdownsaveoptions/export-into-markdown-with-table-content-alignment/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# التصدير إلى Markdown مع محاذاة محتوى الجدول

## مقدمة

أهلاً! هل تساءلت يومًا عن كيفية تصدير مستند Word إلى تنسيق Markdown مع جداول متناسقة بدقة؟ سواء كنت مطورًا تعمل على التوثيق أو مجرد شخص مولع بتنسيق Markdown، فهذا الدليل مناسب لك. سنتعمق في تفاصيل استخدام Aspose.Words for .NET لتحقيق ذلك. هل أنت مستعد لتحويل جداول Word إلى جداول Markdown متناسقة بدقة؟ هيا بنا نبدأ!

## المتطلبات الأساسية

قبل أن نتعمق في الكود، هناك بعض الأشياء التي ستحتاج إلى وضعها في مكانها:

1. مكتبة Aspose.Words لـ .NET: تأكد من توفر مكتبة Aspose.Words لـ .NET لديك. يمكنك تنزيلها من [صفحة إصدارات Aspose](https://releases.aspose.com/words/net/).
2. بيئة التطوير: قم بإعداد بيئة التطوير الخاصة بك. يُعد Visual Studio خيارًا شائعًا لتطوير .NET.
3. المعرفة الأساسية بلغة C#: يعد فهم لغة C# أمرًا ضروريًا لأننا سنكتب التعليمات البرمجية بهذه اللغة.
4. نموذج مستند Word: احصل على مستند Word يمكنك استخدامه للاختبار.

## استيراد مساحات الأسماء

قبل البدء بالبرمجة، لنستورد مساحات الأسماء اللازمة. سيُتيح لنا هذا الوصول إلى فئات وأساليب Aspose.Words التي سنستخدمها.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## الخطوة 1: تهيئة المستند وDocumentBuilder

أولاً وقبل كل شيء، نحتاج إلى إنشاء مستند Word جديد وتهيئة `DocumentBuilder` كائن لبدء بناء مستندنا.

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// إنشاء مستند جديد.
Document doc = new Document();

// تهيئة DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder(doc);
```

## الخطوة 2: إدراج الخلايا ومحاذاة المحتوى

بعد ذلك، سنُدرج بعض الخلايا في مستندنا ونضبط محاذاتها. هذا ضروري لضمان بقاء تصدير Markdown بالمحاذاة الصحيحة.

```csharp
// أدخل خلية واضبط المحاذاة إلى اليمين.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Cell1");

// أدخل خلية أخرى واضبط المحاذاة إلى المركز.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Write("Cell2");
```

## الخطوة 3: تعيين محاذاة محتوى الجدول لتصدير Markdown

الآن، حان الوقت لتكوين `MarkdownSaveOptions` للتحكم في محاذاة محتوى الجدول في ملف Markdown المُصدَّر. سنحفظ المستند بإعدادات محاذاة مختلفة لنرى كيف يعمل.

```csharp
// إنشاء كائن MarkdownSaveOptions.
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    TableContentAlignment = TableContentAlignment.Left
};

// حفظ المستند مع محاذاة إلى اليسار.
doc.Save(dataDir + "LeftTableContentAlignment.md", saveOptions);

// قم بتغيير المحاذاة إلى اليمين ثم احفظ.
saveOptions.TableContentAlignment = TableContentAlignment.Right;
doc.Save(dataDir + "RightTableContentAlignment.md", saveOptions);

// قم بتغيير المحاذاة إلى المركز ثم احفظها.
saveOptions.TableContentAlignment = TableContentAlignment.Center;
doc.Save(dataDir + "CenterTableContentAlignment.md", saveOptions);
```

## الخطوة 4: استخدام محاذاة محتوى الجدول التلقائية

ال `Auto` يأخذ خيار المحاذاة المحاذاة من الفقرة الأولى في عمود الجدول المقابل. هذا مفيد عند وجود محاذاة متعددة في جدول واحد.

```csharp
// ضبط المحاذاة إلى تلقائي.
saveOptions.TableContentAlignment = TableContentAlignment.Auto;

// حفظ المستند مع المحاذاة التلقائية.
doc.Save(dataDir + "AutoTableContentAlignment.md", saveOptions);
```

## خاتمة

ها قد انتهيت! تصدير مستندات Word إلى Markdown مع جداول مصفوفة باستخدام Aspose.Words لـ .NET سهلٌ للغاية بمجرد معرفة كيفية القيام بذلك. تُسهّل هذه المكتبة القوية التحكم في تنسيق ومحاذاة جداولك، مما يضمن ظهور مستندات Markdown بالشكل الذي تريده. برمجة ممتعة!

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟
Aspose.Words for .NET هي مكتبة قوية تمكن المطورين من إنشاء مستندات Word وتعديلها وتحويلها وتصديرها برمجيًا.

### هل يمكنني تعيين محاذات مختلفة لأعمدة مختلفة في نفس الجدول؟
نعم، باستخدام `Auto` خيار المحاذاة، يمكنك الحصول على محاذاة مختلفة استنادًا إلى الفقرة الأولى في كل عمود.

### هل أحتاج إلى ترخيص لاستخدام Aspose.Words لـ .NET؟
نعم، يتطلب Aspose.Words for .NET ترخيصًا للعمل بكامل وظائفه. يمكنك الحصول على [رخصة مؤقتة](https://purchase.aspose.com/temporary-license/) للتقييم.

### هل من الممكن تصدير عناصر مستند أخرى إلى Markdown باستخدام Aspose.Words؟
نعم، يدعم Aspose.Words تصدير عناصر مختلفة مثل العناوين والقوائم والصور إلى تنسيق Markdown.

### أين يمكنني الحصول على الدعم إذا واجهت مشاكل؟
يمكنك الحصول على الدعم من [منتدى دعم Aspose.Words](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}