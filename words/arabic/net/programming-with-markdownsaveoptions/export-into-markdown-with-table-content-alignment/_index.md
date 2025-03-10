---
title: التصدير إلى Markdown مع محاذاة محتوى الجدول
linktitle: التصدير إلى Markdown مع محاذاة محتوى الجدول
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية تصدير مستندات Word إلى Markdown مع جداول مصطفة باستخدام Aspose.Words for .NET. اتبع دليلنا خطوة بخطوة للحصول على جداول Markdown مثالية.
weight: 10
url: /ar/net/programming-with-markdownsaveoptions/export-into-markdown-with-table-content-alignment/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# التصدير إلى Markdown مع محاذاة محتوى الجدول

## مقدمة

مرحبًا! هل تساءلت يومًا عن كيفية تصدير مستند Word الخاص بك إلى تنسيق Markdown مع جداول مصطفة بشكل مثالي؟ سواء كنت مطورًا يعمل على التوثيق أو مجرد شخص يحب Markdown، فهذا الدليل مناسب لك. سنتعمق في التفاصيل الدقيقة لاستخدام Aspose.Words for .NET لتحقيق ذلك. هل أنت مستعد لتحويل جداول Word الخاصة بك إلى جداول Markdown مصطفة بشكل أنيق؟ لنبدأ!

## المتطلبات الأساسية

قبل أن نتعمق في الكود، هناك بعض الأشياء التي ستحتاج إلى وضعها في مكانها:

1.  مكتبة Aspose.Words for .NET: تأكد من أن لديك مكتبة Aspose.Words for .NET. يمكنك تنزيلها من[صفحة إصدارات Aspose](https://releases.aspose.com/words/net/).
2. بيئة التطوير: قم بإعداد بيئة التطوير الخاصة بك. يعد Visual Studio خيارًا شائعًا لتطوير .NET.
3. المعرفة الأساسية بلغة C#: يعد فهم لغة C# أمرًا ضروريًا لأننا سنكتب التعليمات البرمجية بهذه اللغة.
4. نموذج مستند Word: احصل على مستند Word يمكنك استخدامه للاختبار.

## استيراد مساحات الأسماء

قبل أن نبدأ في كتابة التعليمات البرمجية، دعنا نستورد مساحات الأسماء الضرورية. وهذا سيتيح لنا الوصول إلى فئات وطرق Aspose.Words التي سنستخدمها.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## الخطوة 1: تهيئة المستند وDocumentBuilder

أولاً وقبل كل شيء، نحتاج إلى إنشاء مستند Word جديد وتهيئة`DocumentBuilder` كائن لبدء بناء مستندنا.

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// إنشاء مستند جديد.
Document doc = new Document();

// تهيئة DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder(doc);
```

## الخطوة 2: إدراج الخلايا ومحاذاة المحتوى

بعد ذلك، سنقوم بإدراج بعض الخلايا في مستندنا وتعيين محاذاتها. يعد هذا أمرًا بالغ الأهمية لضمان احتفاظ تصدير Markdown بالمحاذاة الصحيحة.

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

 الآن، حان الوقت لتكوين`MarkdownSaveOptions` للتحكم في محاذاة محتوى الجدول في ملف Markdown المُصدَّر. سنحفظ المستند بإعدادات محاذاة مختلفة لنرى كيف يعمل.

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

// قم بتغيير المحاذاة إلى المركز ثم احفظ.
saveOptions.TableContentAlignment = TableContentAlignment.Center;
doc.Save(dataDir + "CenterTableContentAlignment.md", saveOptions);
```

## الخطوة 4: استخدام محاذاة محتوى الجدول تلقائيًا

 ال`Auto`يأخذ خيار المحاذاة المحاذاة من الفقرة الأولى في عمود الجدول المقابل. يمكن أن يكون هذا مفيدًا عندما يكون لديك محاذاة مختلطة في جدول واحد.

```csharp
// ضبط المحاذاة إلى تلقائي.
saveOptions.TableContentAlignment = TableContentAlignment.Auto;

// حفظ المستند مع المحاذاة التلقائية.
doc.Save(dataDir + "AutoTableContentAlignment.md", saveOptions);
```

## خاتمة

والآن، لقد انتهيت! إن تصدير مستندات Word إلى Markdown مع جداول مصطفة باستخدام Aspose.Words for .NET أمر سهل للغاية بمجرد أن تعرف كيفية القيام بذلك. تسهل هذه المكتبة القوية التحكم في تنسيق ومحاذاة الجداول، مما يضمن أن تبدو مستندات Markdown الخاصة بك بالشكل الذي تريده. استمتع بالبرمجة!

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟
Aspose.Words for .NET هي مكتبة قوية تتيح للمطورين إنشاء مستندات Word وتعديلها وتحويلها وتصديرها برمجيًا.

### هل يمكنني تعيين محاذات مختلفة لأعمدة مختلفة في نفس الجدول؟
 نعم، عن طريق استخدام`Auto` خيار المحاذاة، يمكنك الحصول على محاذاة مختلفة استنادًا إلى الفقرة الأولى في كل عمود.

### هل أحتاج إلى ترخيص لاستخدام Aspose.Words لـ .NET؟
 نعم، يتطلب Aspose.Words for .NET ترخيصًا للحصول على الوظائف الكاملة. يمكنك الحصول على ترخيص[رخصة مؤقتة](https://purchase.aspose.com/temporary-license/) للتقييم.

### هل من الممكن تصدير عناصر مستند أخرى إلى Markdown باستخدام Aspose.Words؟
نعم، يدعم Aspose.Words تصدير عناصر مختلفة مثل العناوين والقوائم والصور إلى تنسيق Markdown.

### أين يمكنني الحصول على الدعم إذا واجهت مشاكل؟
 يمكنك الحصول على الدعم من[منتدى دعم Aspose.Words](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
