---
"description": "تعرّف على كيفية إعداد إعدادات الخط الاحتياطي في Aspose.Words لـ .NET. يضمن هذا الدليل الشامل عرض جميع الأحرف في مستنداتك بشكل صحيح."
"linktitle": "تعيين إعدادات الخط الاحتياطي"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "تعيين إعدادات الخط الاحتياطي"
"url": "/ar/net/working-with-fonts/set-font-fallback-settings/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تعيين إعدادات الخط الاحتياطي

## مقدمة

عند العمل مع مستندات تحتوي على عناصر نصية متنوعة، مثل لغات مختلفة أو أحرف خاصة، من الضروري ضمان عرض هذه العناصر بشكل صحيح. يوفر Aspose.Words for .NET ميزة فعّالة تُسمى "إعدادات الخط الاحتياطي"، والتي تُساعد في تحديد قواعد استبدال الخطوط عندما لا يدعم الخط الأصلي أحرفًا معينة. في هذا الدليل، سنستكشف كيفية إعداد "إعدادات الخط الاحتياطي" باستخدام Aspose.Words for .NET من خلال برنامج تعليمي خطوة بخطوة.

## المتطلبات الأساسية

قبل الغوص في البرنامج التعليمي، تأكد من أن لديك المتطلبات الأساسية التالية:

- المعرفة الأساسية بلغة C#: الإلمام بلغة البرمجة C# وإطار عمل .NET.
- Aspose.Words لـ .NET: التنزيل والتثبيت من [رابط التحميل](https://releases.aspose.com/words/net/).
- بيئة التطوير: إعداد مثل Visual Studio لكتابة وتشغيل التعليمات البرمجية الخاصة بك.
- مستند نموذجي: احصل على مستند نموذجي (على سبيل المثال، `Rendering.docx`) جاهزة للاختبار.
- قواعد الرجوع إلى الخط XML: قم بإعداد ملف XML الذي يحدد قواعد الرجوع إلى الخط.

## استيراد مساحات الأسماء

لاستخدام Aspose.Words، عليك استيراد مساحات الأسماء اللازمة. يتيح لك هذا الوصول إلى مختلف الفئات والأساليب اللازمة لمعالجة المستندات.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;
```

## الخطوة 1: تحديد دليل المستندات

أولاً، حدد المجلد الذي تُخزَّن فيه مستندك. هذا ضروري لتحديد موقع مستندك ومعالجته.

```csharp
// المسار إلى دليل المستندات
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## الخطوة 2: تحميل المستند

قم بتحميل مستندك إلى Aspose.Words `Document` الكائن. تسمح لك هذه الخطوة بالعمل مع المستند برمجيًا.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## الخطوة 3: تكوين إعدادات الخط

إنشاء جديد `FontSettings` كائن وحمّل إعدادات الخط الاحتياطي من ملف XML. يحتوي ملف XML هذا على قواعد الخط الاحتياطي.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.FallbackSettings.Load(dataDir + "Font fallback rules.xml");
```

## الخطوة 4: تطبيق إعدادات الخط على المستند

تعيين التكوين `FontSettings` إلى المستند. هذا يضمن تطبيق قواعد الخط الاحتياطي عند عرض المستند.

```csharp
doc.FontSettings = fontSettings;
```

## الخطوة 5: حفظ المستند

أخيرًا، احفظ المستند. سيتم استخدام إعدادات الخط البديلة أثناء عملية الحفظ لضمان استبدال الخط بشكل صحيح.

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

باتباع هذه الخطوات، يمكنك إعداد واستخدام إعدادات الخط الاحتياطي بفعالية في Aspose.Words لـ .NET. هذا يضمن عرض جميع الأحرف في مستنداتك بشكل صحيح، حتى لو كان الخط الأصلي لا يدعم بعض الأحرف. سيؤدي تطبيق هذه الإعدادات إلى تحسين جودة مستنداتك وقابليتها للقراءة بشكل كبير.

## الأسئلة الشائعة

### س1: ما هو Font Fallback؟

Font Fallback هي ميزة تسمح باستبدال الخطوط عندما لا يدعم الخط الأصلي أحرفًا معينة، مما يضمن العرض المناسب لجميع عناصر النص.

### س2: هل يمكنني تحديد خطوط احتياطية متعددة؟

نعم، يمكنك تحديد عدة خطوط احتياطية في قواعد XML. سيتحقق Aspose.Words من كل خط بالترتيب المحدد حتى يجد خطًا يدعم الحرف.

### س3: أين يمكنني تنزيل Aspose.Words لـ .NET؟

يمكنك تنزيله من [صفحة تنزيل Aspose](https://releases.aspose.com/words/net/).

### س4: كيف أقوم بإنشاء ملف XML لقواعد الرجوع إلى الخطوط؟

يمكن إنشاء ملف XML باستخدام أي محرر نصوص. يجب أن يتبع الهيكل الموضح في المثال المقدم في هذا البرنامج التعليمي.

### س5: هل هناك دعم متاح لـ Aspose.Words؟

نعم، يمكنك العثور على الدعم على [منتدى دعم Aspose.Words](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}