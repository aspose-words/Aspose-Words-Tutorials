---
category: general
date: 2026-09-21
description: تعلم كيفية تعيين RenderChoiceFormFieldBorder إلى false في Aspose.Words
  لتصدير حقول النماذج في Word بدون حدود. يتضمن الكود الكامل والنصائح.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set renderchoiceformfieldborder false
- Aspose.Words PDF conversion
- disable choice field border
- PdfSaveOptions configuration
- Word form fields
- convert Word to PDF
language: ar
lastmod: 2026-09-21
og_description: عيّن RenderChoiceFormFieldBorder إلى false لإزالة الحدود من حقول النموذج
  الاختيارية عند تحويل Word إلى PDF باستخدام Aspose.Words.
og_image_alt: PDF preview showing choice form fields without borders after setting
  RenderChoiceFormFieldBorder false
og_title: عيّن RenderChoiceFormFieldBorder إلى false لتصدير PDF نظيف
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to set RenderChoiceFormFieldBorder false in Aspose.Words
    to export Word form fields without borders. Includes full code and tips.
  headline: How to set RenderChoiceFormFieldBorder false when converting Word to PDF
  type: TechArticle
- description: Learn how to set RenderChoiceFormFieldBorder false in Aspose.Words
    to export Word form fields without borders. Includes full code and tips.
  name: How to set RenderChoiceFormFieldBorder false when converting Word to PDF
  steps:
  - name: Additional PdfSaveOptions you may want to set
    text: '| Option | Typical value | When to use it | |----------------------------|---------------|----------------|
      | `Compliance` | `PdfCompliance.PdfA1b` | For archival PDFs | | `EmbedStandardFonts`
      | `true` | To avoid font substitution on other machines | | `SaveFormat` | `SaveFormat.Pdf`
      | Explicitly st'
  - name: Verifying the result
    text: Open `NoBorderChoice.pdf` in any PDF viewer (Adobe Acrobat, Foxit Reader,
      or the browser). You should see the drop‑down or combo‑box fields rendered as
      plain text placeholders—no gray rectangle is visible. The fields remain interactive;
      clicking on them still displays the list of choices.
  - name: Sample code for checking form fields
    text: '```csharp int choiceFieldCount = 0; foreach (FormField field in doc.Range.FormFields)
      { if (field.Type == FieldType.FieldFormDropDown || field.Type == FieldType.FieldFormComboBox)
      choiceFieldCount++; } Console.WriteLine($"Document contains {choiceFieldCount}
      choice form fields."); ```'
  type: HowTo
tags:
- Aspose.Words
- PDF conversion
- C#
- Form fields
title: كيفية ضبط RenderChoiceFormFieldBorder على false عند تحويل Word إلى PDF
url: /ar/net/programming-with-pdfsaveoptions/how-to-set-renderchoiceformfieldborder-false-when-converting/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تعيين RenderChoiceFormFieldBorder إلى false عند تحويل Word إلى PDF

إذا كنت بحاجة إلى **تعيين RenderChoiceFormFieldBorder إلى false** أثناء تصدير مستند Word يحتوي على حقول نموذج اختيار، يوضح لك هذا الدليل الخطوات الدقيقة. من خلال تعطيل رسم الحدود، يصبح ملف PDF الناتج أكثر نظافة ويتطابق مع تخطيط المستند الأصلي.

في هذا البرنامج التعليمي ستتعلم كيفية تكوين **PdfSaveOptions** في Aspose.Words، ولماذا هذا الإعداد مهم، وكيفية التعامل مع الحالات الطرفية الشائعة مثل المستندات التي لا تحتوي على أي حقول نموذج. تعمل الحلول مع أحدث نسخة من Aspose.Words for .NET (v23.10 في وقت كتابة هذا الدليل) وتحتاج فقط إلى بضع أسطر من كود C#.

## المتطلبات المسبقة

* .NET 6.0 أو أحدث مثبت.
* ترخيص صالح لـ Aspose.Words for .NET (أو مفتاح تقييم مجاني).
* مستند Word (`.docx`) يحتوي على حقول نموذج اختيار (مثل القوائم المنسدلة أو صناديق الجمع).
* Visual Studio 2022 (أو أي بيئة تطوير C#).

## الخطوة 1: تحميل مستند Word المصدر

الخطوة الأولى هي إنشاء كائن `Document` يمثل ملف المصدر الخاص بك. تقوم Aspose.Words بقراءة الملف إلى الذاكرة، مما يتيح لك فحص محتواه أو تعديلّه قبل التحويل.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word document that contains choice form fields
Document doc = new Document("YOUR_DIRECTORY/FormWithChoices.docx");
```

**لماذا هذا مهم:**  
تحميل المستند يمنحك الوصول إلى مجموعة حقول النموذج، والتي يمكنك لاحقًا الاستعلام عنها للتأكد من أن الملف يحتوي فعليًا على حقول اختيار. إذا لم يحتوي المستند على مثل هذه الحقول، فإن إعداد `RenderChoiceFormFieldBorder` لا يؤثر بصريًا، لكن الكود لا يزال يعمل بأمان.

## الخطوة 2: تكوين PdfSaveOptions وتعيين RenderChoiceFormFieldBorder إلى false

`PdfSaveOptions` يتحكم في كل جانب من مخرجات PDF، من جودة الصورة إلى رسم حقول النموذج. تعيين `RenderChoiceFormFieldBorder` إلى `false` يخبر المُعالج بتجاهل المستطيل الرمادي الذي يحيط عادةً بالحقول المنسدلة وصناديق الجمع.

```csharp
// Create PDF save options and disable the rendering of choice field borders
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    RenderChoiceFormFieldBorder = false
};
```

**لماذا هذا مهم:**  
بشكل افتراضي، تقوم Aspose.Words برسم حد رفيع حول حقول نموذج الاختيار حتى يتمكن المستخدمون من رؤية مكان التفاعل. في العديد من سيناريوهات النشر—مثل النماذج القابلة للطباعة أو التقارير المصقولة—يكون الحد غير مرغوب فيه. يوفر علم `RenderChoiceFormFieldBorder` طريقة سطر واحد لإيقافه.

### خيارات PdfSaveOptions إضافية قد ترغب في تعيينها

| Option                     | Typical value               | When to use it                              |
|----------------------------|-----------------------------|---------------------------------------------|
| `Compliance`               | `PdfCompliance.PdfA1b`      | لملفات PDF الأرشيفية                       |
| `EmbedStandardFonts`       | `true`                      | لتجنب استبدال الخطوط على أجهزة أخرى         |
| `SaveFormat`               | `SaveFormat.Pdf`            | يحدد صراحةً تنسيق الهدف (اختياري)          |

يمكنك ربط هذه الإعدادات مع علم الحد:

```csharp
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    RenderChoiceFormFieldBorder = false,
    Compliance = PdfCompliance.PdfA1b,
    EmbedStandardFonts = true
};
```

## الخطوة 3: حفظ المستند كملف PDF باستخدام الخيارات المكوّنة

الآن بعد تعيين الخيارات، استدعِ `Document.Save` مع مسار الوجهة وكائن `PdfSaveOptions`.

```csharp
// Save the document as a PDF using the configured options
doc.Save("YOUR_DIRECTORY/NoBorderChoice.pdf", pdfOptions);
```

**لماذا هذا مهم:**  
طريقة `Save` تقوم بالتحويل الفعلي. لأن `pdfOptions` يحتوي على `RenderChoiceFormFieldBorder = false`، فإن ملف PDF الناتج سيحتوي على حقول الاختيار **بدون** الحد المحيط.

### التحقق من النتيجة

افتح `NoBorderChoice.pdf` في أي عارض PDF (Adobe Acrobat، Foxit Reader، أو المتصفح). يجب أن ترى حقول القائمة المنسدلة أو صندوق الجمع تُعرض كنصوص بديلة عادية—لا يُرى أي مستطيل رمادي. تظل الحقول تفاعلية؛ النقر عليها لا يزال يعرض قائمة الخيارات.

## التعامل مع الحالات الطرفية

| الحالة                              | النهج الموصى به |
|-------------------------------------|-----------------|
| **المستند لا يحتوي على حقول نموذج اختيار** | علم الحد لا يؤثر. يمكنك اختيارياً فحص `doc.Range.FormFields.Count` قبل التحويل لتخطي التكوين غير الضروري. |
| **ملف Word محمي بكلمة مرور**       | حمّل المستند باستخدام كائن `LoadOptions` الذي يتضمن كلمة المرور، ثم طبق نفس `PdfSaveOptions`. |
| **مستندات كبيرة (> 100 ميغابايت)** | استخدم خيارات `MemoryOptimization` على `PdfSaveOptions` لتقليل استهلاك الذاكرة أثناء التحويل. |
| **الحاجة إلى الحفاظ على الحد لبعض الحقول المحددة** | بعد تحميل المستند، قم بالتكرار على `doc.Range.FormFields`، عيّن `FieldType` إلى `FieldType.FieldFormDropDown` أو `FieldFormComboBox`، واضبط خاصية `Border` يدويًا قبل الحفظ. |

### مثال على الكود للتحقق من حقول النموذج

```csharp
int choiceFieldCount = 0;
foreach (FormField field in doc.Range.FormFields)
{
    if (field.Type == FieldType.FieldFormDropDown || field.Type == FieldType.FieldFormComboBox)
        choiceFieldCount++;
}
Console.WriteLine($"Document contains {choiceFieldCount} choice form fields.");
```

إذا كان `choiceFieldCount` صفرًا، يمكنك تخطي تكوين الحد تمامًا، مما يوفر كمية صغيرة من وقت المعالجة.

## مثال كامل يعمل

فيما يلي البرنامج الكامل القابل للتنفيذ الذي يجمع كل شيء معًا. استبدل `YOUR_DIRECTORY` بالمسار الفعلي على جهازك.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source Word document
        Document doc = new Document("YOUR_DIRECTORY/FormWithChoices.docx");

        // Optional: verify that the document contains choice fields
        int choiceCount = 0;
        foreach (FormField field in doc.Range.FormFields)
        {
            if (field.Type == FieldType.FieldFormDropDown ||
                field.Type == FieldType.FieldFormComboBox)
                choiceCount++;
        }
        Console.WriteLine($"Found {choiceCount} choice form fields.");

        // 2️⃣ Configure PdfSaveOptions and set RenderChoiceFormFieldBorder false
        PdfSaveOptions pdfOptions = new PdfSaveOptions
        {
            RenderChoiceFormFieldBorder = false,
            // Example of additional options you might need
            Compliance = PdfCompliance.PdfA1b,
            EmbedStandardFonts = true
        };

        // 3️⃣ Save the PDF
        string outputPath = "YOUR_DIRECTORY/NoBorderChoice.pdf";
        doc.Save(outputPath, pdfOptions);
        Console.WriteLine($"PDF saved to {outputPath} with borders disabled.");
    }
}
```

**المخرجات المتوقعة في وحدة التحكم**

```
Found 3 choice form fields.
PDF saved to C:\MyProjects\NoBorderChoice.pdf with borders disabled.
```

عند فتح `NoBorderChoice.pdf`، تظهر حقول القائمة المنسدلة بدون الحد الرمادي الافتراضي، مما يمنح المستند مظهرًا أنظف مع الحفاظ على التفاعلية.

## نصائح احترافية ومخاطر شائعة

* **نصيحة احترافية:** إذا كنت تُنشئ ملفات PDF في خدمة ويب، عيّن `pdfOptions.SaveFormat = SaveFormat.Pdf` صراحةً لتجنب مشاكل اكتشاف الصيغة غير المقصودة.
* **احذر من:** الإصدارات القديمة من Aspose.Words (قبل v20) لا تُظهر `RenderChoiceFormFieldBorder`. قم بالترقية إلى أحدث إصدار لاستخدام هذا العلم.
* **نصيحة أداء:** أعد استخدام كائن `PdfSaveOptions` واحد عند تحويل العديد من المستندات في دفعة؛ إنشاء كائن جديد في كل مرة يضيف عبئًا غير ضروري.
* **نصيحة اختبار:** أدرج اختبار وحدة يقوم بتحميل ملف `.docx` معروف يحتوي على قائمة منسدلة، ينفذ التحويل، ويتأكد من أن تدفق PDF الناتج لا يحتوي على التعليق التوضيحي `/Border` لتلك الحقول.

## الخلاصة

أنت الآن تعرف **كيفية تعيين RenderChoiceFormFieldBorder إلى false** لإنشاء ملفات PDF بدون حدود حقول الاختيار باستخدام Aspose.Words. يغطي الحل تحميل المستند، تكوين `PdfSaveOptions`، حفظ PDF، والتعامل مع الحالات الطرفية مثل عدم وجود حقول نموذج أو مصادر محمية بكلمة مرور.  

بعد ذلك، قد تستكشف مواضيع ذات صلة مثل **تعطيل حد حقل الاختيار** لأنواع أخرى من حقول النموذج، أو تتعلم كيفية **تحويل Word إلى PDF** بدقة صورة مخصصة باستخدام `ImageSaveOptions`. كلا الموضوعين يعمقان إتقانك لـ **تحويل PDF باستخدام Aspose.Words** ويمنحانك التحكم الكامل في مظهر المستند النهائي.

برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [تحويل Word إلى PDF باستخدام C# و Aspose.Words – دليل](/words/english/net/basic-conversions/convert-word-to-pdf-in-c-using-aspose-words-guide/)
- [حفظ Word كـ PDF باستخدام Aspose Words – دليل C# كامل](/words/hindi/net/programming-with-pdfsaveoptions/save-word-as-pdf-with-aspose-words-complete-c-guide/)
- [تحويل Word إلى PDF باستخدام Aspose.Words for Java](/words/english/java/document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}