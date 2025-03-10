---
title: تعيين إعدادات الخط الاحتياطي
linktitle: تعيين إعدادات الخط الاحتياطي
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إعداد إعدادات الخط الاحتياطي في Aspose.Words for .NET. يضمن هذا الدليل الشامل عرض جميع الأحرف في مستنداتك بشكل صحيح.
weight: 10
url: /ar/net/working-with-fonts/set-font-fallback-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تعيين إعدادات الخط الاحتياطي

## مقدمة

عند العمل مع مستندات تحتوي على عناصر نصية متنوعة، مثل لغات مختلفة أو أحرف خاصة، من المهم التأكد من عرض هذه العناصر بشكل صحيح. يوفر Aspose.Words for .NET ميزة قوية تسمى إعدادات الرجوع إلى الخلف للخطوط، والتي تساعد في تحديد قواعد استبدال الخطوط عندما لا يدعم الخط الأصلي أحرفًا معينة. في هذا الدليل، سنستكشف كيفية إعداد إعدادات الرجوع إلى الخلف للخطوط باستخدام Aspose.Words for .NET في برنامج تعليمي خطوة بخطوة.

## المتطلبات الأساسية

قبل الخوض في البرنامج التعليمي، تأكد من توفر المتطلبات الأساسية التالية:

- المعرفة الأساسية بلغة C#: الإلمام بلغة البرمجة C# وإطار عمل .NET.
-  Aspose.Words for .NET: تنزيل وتثبيت من[رابط التحميل](https://releases.aspose.com/words/net/).
- بيئة التطوير: إعداد مثل Visual Studio لكتابة وتشغيل التعليمات البرمجية الخاصة بك.
-  مستند نموذجي: احصل على مستند نموذجي (على سبيل المثال،`Rendering.docx`) جاهزة للاختبار.
- قواعد الرجوع إلى الخط XML: قم بإعداد ملف XML الذي يحدد قواعد الرجوع إلى الخط.

## استيراد مساحات الأسماء

لاستخدام Aspose.Words، تحتاج إلى استيراد مساحات الأسماء الضرورية. يتيح لك هذا الوصول إلى الفئات والطرق المختلفة المطلوبة لمعالجة المستندات.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;
```

## الخطوة 1: تحديد دليل المستندات

أولاً، قم بتحديد الدليل الذي سيتم تخزين مستندك فيه. يعد هذا أمرًا ضروريًا لتحديد موقع مستندك ومعالجته.

```csharp
// المسار إلى دليل المستندات
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## الخطوة 2: تحميل المستند

 قم بتحميل مستندك إلى Aspose.Words`Document` الكائن. تسمح لك هذه الخطوة بالعمل مع المستند برمجيًا.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## الخطوة 3: تكوين إعدادات الخط

 إنشاء جديد`FontSettings` قم بتحميل إعدادات الرجوع إلى الخط من ملف XML. يحتوي ملف XML هذا على قواعد الرجوع إلى الخط.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.FallbackSettings.Load(dataDir + "Font fallback rules.xml");
```

## الخطوة 4: تطبيق إعدادات الخط على المستند

 تعيين التكوين`FontSettings`إلى المستند. وهذا يضمن تطبيق قواعد الرجوع إلى الخط عند عرض المستند.

```csharp
doc.FontSettings = fontSettings;
```

## الخطوة 5: احفظ المستند

أخيرًا، احفظ المستند. سيتم استخدام إعدادات الخط البديل أثناء عملية الحفظ لضمان استبدال الخط بشكل صحيح.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontFallbackSettings.pdf");
```

## ملف XML: قواعد الرجوع إلى الخطوط

فيما يلي مثال لكيفية ظهور ملف XML الذي يحدد قواعد الرجوع إلى الخط:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<FontFallbackSettings xmlns="Aspose.Words">
    <FallbackTable>
        <Rule Ranges="0B80-0BFF" FallbackFonts="Vijaya"/>
        <Rule Ranges="1F300-1F64F" FallbackFonts="Segoe UI Emoji, Segoe UI Symbol"/>
        <Rule Ranges="2000-206F, 2070-209F, 20B9" FallbackFonts="Arial" />
        <Rule Ranges="3040-309F" FallbackFonts="MS Gothic" BaseFonts="Times New Roman"/>
        <Rule Ranges="3040-309F" FallbackFonts="MS Mincho"/>
        <Rule FallbackFonts="Arial Unicode MS"/>
    </FallbackTable>
</FontFallbackSettings>
```

## خاتمة

باتباع هذه الخطوات، يمكنك إعداد واستخدام إعدادات الخط الاحتياطي في Aspose.Words لـ .NET بشكل فعال. وهذا يضمن عرض مستنداتك لجميع الأحرف بشكل صحيح، حتى إذا كان الخط الأصلي لا يدعم أحرفًا معينة. سيؤدي تنفيذ هذه الإعدادات إلى تحسين جودة مستنداتك وقابليتها للقراءة بشكل كبير.

## الأسئلة الشائعة

### س1: ما هو Font Fallback؟

Font Fallback هي ميزة تسمح باستبدال الخطوط عندما لا يدعم الخط الأصلي أحرفًا معينة، مما يضمن العرض المناسب لجميع عناصر النص.

### س2: هل يمكنني تحديد خطوط احتياطية متعددة؟

نعم، يمكنك تحديد خطوط احتياطية متعددة في قواعد XML. سيتحقق Aspose.Words من كل خط بالترتيب المحدد حتى يجد الخط الذي يدعم الحرف.

### س3: أين يمكنني تنزيل Aspose.Words لـ .NET؟

 يمكنك تنزيله من[صفحة تحميل برنامج Aspose](https://releases.aspose.com/words/net/).

### س4: كيف أقوم بإنشاء ملف XML لقواعد الرجوع إلى الخط؟

يمكن إنشاء ملف XML باستخدام أي محرر نصوص. ويجب أن يتبع الهيكل الموضح في المثال المقدم في هذا البرنامج التعليمي.

### س5: هل يتوفر الدعم لـ Aspose.Words؟

 نعم، يمكنك العثور على الدعم على[منتدى دعم Aspose.Words](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
