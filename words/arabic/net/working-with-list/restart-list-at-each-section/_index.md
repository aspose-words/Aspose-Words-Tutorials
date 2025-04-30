---
"description": "تعرّف على كيفية إعادة تشغيل القوائم عند كل قسم في مستندات Word باستخدام Aspose.Words لـ .NET. اتبع دليلنا المفصل خطوة بخطوة لإدارة القوائم بفعالية."
"linktitle": "إعادة تشغيل القائمة في كل قسم"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "إعادة تشغيل القائمة في كل قسم"
"url": "/ar/net/working-with-list/restart-list-at-each-section/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إعادة تشغيل القائمة في كل قسم

## مقدمة

إنشاء مستندات منظمة ومنظمة جيدًا قد يبدو أحيانًا أشبه بحل لغز معقد. أحد جوانب هذا اللغز هو إدارة القوائم بفعالية، خاصةً عند الرغبة في إعادة تشغيلها عند كل قسم. مع Aspose.Words لـ .NET، يمكنك إنجاز ذلك بسلاسة. لنستعرض كيفية إعادة تشغيل القوائم عند كل قسم في مستندات Word باستخدام Aspose.Words لـ .NET.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

1. Aspose.Words for .NET: قم بتنزيل أحدث إصدار من البرنامج وتثبيته [إصدارات Aspose](https://releases.aspose.com/words/net/) صفحة.
2. بيئة .NET: قم بإعداد بيئة التطوير الخاصة بك مع تثبيت .NET.
3. الفهم الأساسي للغة البرمجة C#: يوصى بالتعرف على لغة البرمجة C#.
4. ترخيص Aspose: يمكنك اختيار [رخصة مؤقتة](https://purchase.aspose.com/temporary-license/) إذا لم يكن لديك واحدة.

## استيراد مساحات الأسماء

قبل كتابة الكود، تأكد من استيراد المساحات الأساسية اللازمة:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Lists;
```

الآن، دعونا نقسم العملية إلى خطوات متعددة لتسهيل متابعتها.

## الخطوة 1: تهيئة المستند

أولاً، ستحتاج إلى إنشاء مثيل مستند جديد.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
```

## الخطوة 2: إضافة قائمة مرقمة

بعد ذلك، أضف قائمة مرقمة إلى المستند. ستتبع هذه القائمة تنسيق الترقيم الافتراضي.

```csharp
doc.Lists.Add(ListTemplate.NumberDefault);
```

## الخطوة 3: الوصول إلى القائمة وتعيين خاصية إعادة التشغيل

استرداد القائمة التي قمت بإنشائها للتو وتعيينها `IsRestartAtEachSection` الممتلكات إلى `true`. ويضمن هذا إعادة ترقيم القائمة عند كل قسم جديد.

```csharp
List list = doc.Lists[0];
list.IsRestartAtEachSection = true;
```

## الخطوة 4: إنشاء منشئ المستندات وربط القائمة

إنشاء `DocumentBuilder` لإدراج المحتوى في المستند وربطه بالقائمة.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.ListFormat.List = list;
```

## الخطوة 5: إضافة عناصر القائمة وإدراج فاصل القسم

الآن، أضف عناصر إلى القائمة. لتوضيح وظيفة إعادة التشغيل، سنُدرج فاصلًا مقطعيًا بعد عدد مُحدد من العناصر.

```csharp
for (int i = 1; i < 45; i++)
{
    builder.Writeln($"List item {i}");

    if (i == 15)
        builder.InsertBreak(BreakType.SectionBreakNewPage);
}
```

## الخطوة 6: حفظ المستند

وأخيرا، قم بحفظ المستند مع الخيارات المناسبة لضمان التوافق.

```csharp
OoxmlSaveOptions options = new OoxmlSaveOptions { Compliance = OoxmlCompliance.Iso29500_2008_Transitional };
doc.Save(dataDir + "WorkingWithList.RestartListAtEachSection.docx", options);		
```

## خاتمة

وهذا كل ما في الأمر! باتباع هذه الخطوات، يمكنك بسهولة إعادة تشغيل القوائم في كل قسم من مستندات Word باستخدام Aspose.Words لـ .NET. هذه الميزة مفيدة للغاية لإنشاء مستندات منظمة تتطلب أقسامًا منفصلة بترقيم قوائم خاص بها. مع Aspose.Words، يصبح التعامل مع هذه المهام سهلاً للغاية، مما يتيح لك التركيز على صياغة محتوى عالي الجودة.

## الأسئلة الشائعة

### هل يمكنني إعادة تشغيل القوائم في كل قسم لأنواع القوائم المختلفة؟
نعم، يسمح لك Aspose.Words for .NET بإعادة تشغيل أنواع مختلفة من القوائم، بما في ذلك القوائم النقطية والمرقمة.

### ماذا لو أردت تخصيص تنسيق الترقيم؟
يمكنك تخصيص تنسيق الترقيم عن طريق تعديل `ListTemplate` الخاصية عند إنشاء القائمة.

### هل هناك حد لعدد العناصر في القائمة؟
لا، لا يوجد حد محدد لعدد العناصر التي يمكنك الحصول عليها في القائمة باستخدام Aspose.Words لـ .NET.

### هل يمكنني استخدام هذه الميزة في تنسيقات مستندات أخرى مثل PDF؟
نعم، يمكنك استخدام Aspose.Words لتحويل مستندات Word إلى تنسيقات أخرى مثل PDF مع الاحتفاظ ببنية القائمة.

### كيف يمكنني الحصول على نسخة تجريبية مجانية من Aspose.Words لـ .NET؟
يمكنك الحصول على نسخة تجريبية مجانية من [إصدارات Aspose](https://releases.aspose.com/) صفحة.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}