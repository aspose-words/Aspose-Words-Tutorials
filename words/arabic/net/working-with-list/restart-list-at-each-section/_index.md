---
title: إعادة تشغيل القائمة في كل قسم
linktitle: إعادة تشغيل القائمة في كل قسم
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إعادة تشغيل القوائم عند كل قسم في مستندات Word باستخدام Aspose.Words for .NET. اتبع دليلنا المفصل خطوة بخطوة لإدارة القوائم بفعالية.
weight: 10
url: /ar/net/working-with-list/restart-list-at-each-section/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إعادة تشغيل القائمة في كل قسم

## مقدمة

قد يبدو إنشاء مستندات منظمة ومنظمة بشكل جيد في بعض الأحيان أشبه بحل لغز معقد. أحد أجزاء هذا اللغز هو إدارة القوائم بشكل فعال، وخاصةً عندما تريد إعادة تشغيلها عند كل قسم. باستخدام Aspose.Words for .NET، يمكنك إنجاز ذلك بسلاسة. دعنا نتعمق في كيفية إعادة تشغيل القوائم عند كل قسم في مستندات Word الخاصة بك باستخدام Aspose.Words for .NET.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

1.  Aspose.Words for .NET: قم بتنزيل أحدث إصدار من البرنامج وتثبيته[إصدارات Aspose](https://releases.aspose.com/words/net/) صفحة.
2. بيئة .NET: قم بإعداد بيئة التطوير الخاصة بك مع تثبيت .NET.
3. الفهم الأساسي للغة C#: يوصى بالتعرف على لغة البرمجة C#.
4.  ترخيص Aspose: يمكنك اختيار[رخصة مؤقتة](https://purchase.aspose.com/temporary-license/) إذا لم يكن لديك واحدة.

## استيراد مساحات الأسماء

قبل كتابة الكود، تأكد من استيراد المساحات الأساسية الضرورية:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Lists;
```

الآن، دعونا نقوم بتقسيم العملية إلى خطوات متعددة لتسهيل متابعتها.

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

استرداد القائمة التي قمت بإنشائها للتو وتعيينها`IsRestartAtEachSection`الممتلكات ل`true`يضمن هذا إعادة ترقيم القائمة عند كل قسم جديد.

```csharp
List list = doc.Lists[0];
list.IsRestartAtEachSection = true;
```

## الخطوة 4: إنشاء منشئ المستندات وربط القائمة

 إنشاء`DocumentBuilder` لإدراج المحتوى في المستند وربطه بالقائمة.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.ListFormat.List = list;
```

## الخطوة 5: إضافة عناصر القائمة وإدراج فاصل القسم

الآن، أضف عناصر إلى القائمة. لتوضيح وظيفة إعادة التشغيل، سنقوم بإدراج فاصل قسم بعد عدد معين من العناصر.

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

والآن، إليك ما تحتاج إليه! باتباع هذه الخطوات، يمكنك إعادة تشغيل القوائم بسهولة عند كل قسم في مستندات Word باستخدام Aspose.Words for .NET. هذه الميزة مفيدة بشكل لا يصدق لإنشاء مستندات منظمة بشكل جيد تتطلب أقسامًا منفصلة بترقيم قائمتها الخاص. باستخدام Aspose.Words، يصبح التعامل مع مثل هذه المهام أمرًا سهلاً، مما يسمح لك بالتركيز على صياغة محتوى عالي الجودة.

## الأسئلة الشائعة

### هل يمكنني إعادة تشغيل القوائم في كل قسم لأنواع القوائم المختلفة؟
نعم، يسمح لك Aspose.Words for .NET بإعادة تشغيل أنواع مختلفة من القوائم، بما في ذلك القوائم المرقمة والقوائم النقطية.

### ماذا لو أردت تخصيص تنسيق الترقيم؟
 يمكنك تخصيص تنسيق الترقيم عن طريق تعديل`ListTemplate` الخاصية عند إنشاء القائمة.

### هل هناك حد لعدد العناصر الموجودة في القائمة؟
لا، لا يوجد حد معين لعدد العناصر التي يمكنك الحصول عليها في القائمة باستخدام Aspose.Words لـ .NET.

### هل يمكنني استخدام هذه الميزة في تنسيقات مستندات أخرى مثل PDF؟
نعم، يمكنك استخدام Aspose.Words لتحويل مستندات Word إلى تنسيقات أخرى مثل PDF مع الاحتفاظ ببنية القائمة.

### كيف يمكنني الحصول على نسخة تجريبية مجانية من Aspose.Words لـ .NET؟
 يمكنك الحصول على نسخة تجريبية مجانية من[إصدارات Aspose](https://releases.aspose.com/) صفحة.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
