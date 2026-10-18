---
category: general
date: 2026-03-06
description: كيفية تحويل المعادلات من مستند Word إلى تنسيق LaTeX وحفظها كنص عادي.
  تعلّم كيفية تصدير الرياضيات، حفظ ملف Word كنص، والمزيد.
draft: false
keywords:
- how to convert equations
- how to export math
- save word as text
- how to save txt
- save docx as txt
language: ar
og_description: كيفية تحويل المعادلات من مستند Word إلى تنسيق LaTeX وحفظها كنص عادي.
  يوضح لك هذا الدليل كيفية تصدير الرياضيات، حفظ ملف Word كنص، والمزيد.
og_title: كيفية تحويل المعادلات في Word إلى LaTeX – حفظ كملف TXT
tags:
- Aspose.Words
- C#
- LaTeX
- Document Conversion
title: كيفية تحويل المعادلات في Word إلى LaTeX – حفظ كملف TXT
url: /ar/net/programming-with-officemath/how-to-convert-equations-in-word-to-latex-save-as-txt/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تحويل المعادلات في Word إلى LaTeX – حفظ كملف TXT

تحويل المعادلات من مستند Word إلى تنسيق LaTeX هو حاجة شائعة للمطورين الذين يتعاملون مع الأوراق العلمية، محتوى التعلم الإلكتروني، أو أي سير عمل يربط بين Microsoft Office و LaTeX. هل واجهت صعوبة في نسخ كتلة Office Math معقدة وانتهى الأمر برموز مشوشة؟ أنت لست وحدك.  

في هذا الدرس سنستعرض حلاً كاملاً وجاهزًا للتنفيذ يقوم **بتصدير الرياضيات** من ملف `.docx`، وتحويلها إلى LaTeX نظيف، ثم **يحفظ النتيجة كنص عادي** (`.txt`). في النهاية ستعرف كيف **تصدّر الرياضيات**، **تحفظ Word كنص**، وحتى كيف **تحفظ docx كملف txt** للمعالجة اللاحقة.

## ما ستتعلمه

- لماذا Aspose.Words خيار قوي لتحويل المعادلات.
- كيفية تكوين `TxtSaveOptions` لإنتاج LaTeX بدلاً من Unicode الخام.
- الكود C# الدقيق الذي يمكنك إدراجه في أي مشروع .NET.
- معالجة الحالات الطرفية (مثل المستندات بدون معادلات، إصدارات Aspose القديمة).
- نصائح عملية لتجنب المشكلات عند تحويل دفعات كبيرة.

### المتطلبات المسبقة

| المتطلب | السبب |
|-------------|--------|
| .NET 6.0 أو أحدث (أو .NET Framework 4.7+) | Aspose.Words for .NET يدعم كلاهما. |
| حزمة NuGet الخاصة بـ Aspose.Words for .NET (≥ 23.9) | الإصدارات الأحدث تتضمن تعداد `OfficeMathExportMode.LaTeX`. |
| ملف Word (`.docx`) يحتوي على كائنات Office Math | التحويل يعمل فقط على كائنات المعادلات الفعلية. |
| Visual Studio، VS Code، أو أي بيئة تطوير C# تفضلها | لا حاجة لأدوات خاصة. |

إذا لم تقم بإضافة Aspose.Words بعد، نفّذ:

```bash
dotnet add package Aspose.Words
```

هذا كل شيء—لا حاجة للبحث عن DLL إضافية.

![مثال على تحويل المعادلات](/images/convert-equations.png "رسم توضيحي لكيفية تحويل المعادلات")

## تنفيذ خطوة بخطوة

فيما يلي نقسم العملية إلى ثلاث مراحل واضحة. كل مرحلة لها عنوان H2 الخاص بها، بحيث يمكنك القفز مباشرة إلى الجزء الذي تحتاجه.

### كيفية تحويل المعادلات: تحميل المستند المصدر

أولاً نحتاج إلى تحميل ملف Word إلى الذاكرة. فئة `Document` تمثل حزمة `.docx` بالكامل، وتمنحنا الوصول إلى كل فقرة، جدول،—والأهم—كائن Office Math.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word document that contains Office Math equations
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Quick sanity check – is there any math at all?
bool hasMath = document.GetChildNodes(NodeType.OfficeMath, true).Count > 0;
if (!hasMath)
{
    Console.WriteLine("⚠️ No equations found. The output file will be empty.");
}
```

**لماذا هذا مهم:**  
إذا تخطيت فحص الصحة وكان المستند يفتقر إلى المعادلات، ستحصل على ملف `.txt` فارغ وتضيع وقت الإدخال/الإخراج. استدعاء `GetChildNodes` منخفض التكلفة ويعطيك رسالة تشخيصية واضحة.

### كيفية تصدير الرياضيات: تكوين خيارات حفظ النص

تتيح لك Aspose.Words التحكم في طريقة عرض Office Math عند حفظه كنص عادي. عن طريق ضبط `OfficeMathExportMode` إلى `LaTeX`، تقوم المكتبة بترجمة كل معادلة إلى صياغة LaTeX صحيحة بدلاً من تمثيل Unicode الافتراضي.

```csharp
// Set up text save options to export Office Math as LaTeX markup
TxtSaveOptions txtSaveOptions = new TxtSaveOptions
{
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,
    // Optional: preserve line breaks for readability
    PreserveTableLayout = true,
    Encoding = Encoding.UTF8
};
```

**لماذا هذا مهم:**  
التصدير الافتراضي (`OfficeMathExportMode.Text`) سيعطيك شيئًا مثل “∫ f(x)dx”، والذي يبدو جيدًا في PDF لكنه يعرقل العديد من خطوط أنابيب LaTeX. التحويل إلى `LaTeX` ينتج `\int f(x)\,dx`، جاهز للإدراج في ملف `.tex`.

### كيفية حفظ TXT: كتابة النص الغني بـ LaTeX إلى القرص

الآن بعد ضبط الخيارات، نستدعي ببساطة `Save`. الطريقة تحترم `TxtSaveOptions` التي مررناها، لذا الملف الناتج يحتوي على LaTeX الخام متداخلًا مع أي محتوى نص عادي محيط.

```csharp
// Save the document as a plain‑text file using the configured options
string outputPath = "YOUR_DIRECTORY/output.txt";
document.Save(outputPath, txtSaveOptions);

Console.WriteLine($"✅ Conversion complete! LaTeX saved to: {outputPath}");
```

**الناتج المتوقع:**  
افتح `output.txt` في أي محرر وسترى شيئًا مثل:

```
Here is a simple equation:
\int_{0}^{\infty} e^{-x^2} \,dx = \frac{\sqrt{\pi}}{2}
And a second one:
E = mc^{2}
```

الجمل المحيطة تبقى دون تعديل، بينما كل كتلة Office Math تتحول إلى LaTeX نظيف.

## معالجة الحالات الطرفية الشائعة

| الموقف | ما الذي يجب فعله |
|-----------|------------|
| المستند لا يحتوي على معادلات | فحص الصحة أعلاه يحذرك بالفعل. يمكنك اختيار تخطي الحفظ أو كتابة سطر نائب. |
| إصدار Aspose.Words قديم (< 22.9) | `OfficeMathExportMode.LaTeX` غير متوفر. قم بترقية حزمة NuGet أو عُد إلى `OfficeMathExportMode.Text` ومعالجة Unicode يدويًا بعد ذلك. |
| تحويل دفعات كبيرة (مئات الملفات) | غلف المنطق داخل حلقة `foreach`، أعد استخدام نسخة واحدة من `TxtSaveOptions`، وفكر في الإدخال/الإخراج غير المتزامن (`await document.SaveAsync`). |
| معادلات بخطوط أو رموز مخصصة | LaTeX سيحافظ على الدلالة الرياضية، لكن التنسيق البصري (اللون، الحجم) سيفقد—هذا متوقع في سير عمل النص العادي. |
| الحاجة إلى PDF بدلاً من TXT | استبدل `TxtSaveOptions` بـ `PdfSaveOptions`؛ نفس `OfficeMathExportMode` يعمل مع PDF أيضًا. |

**نصيحة احترافية:** عند معالجة العديد من الملفات، سجّل كل من النجاحات والفشل في ملف CSV. بهذه الطريقة يمكنك بسرعة تحديد المستندات التي لم تحتوي على رياضيات أو التي أطلقت استثناءات.

## مثال كامل جاهز للتنفيذ (نسخ‑لصق)

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Saving;

class EquationConverter
{
    static void Main()
    {
        // 1️⃣ Load the source .docx
        string inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Verify that the document actually has Office Math objects
        bool hasMath = doc.GetChildNodes(NodeType.OfficeMath, true).Count > 0;
        if (!hasMath)
        {
            Console.WriteLine("⚠️ No equations found in the source document.");
        }

        // 3️⃣ Configure save options to export LaTeX
        TxtSaveOptions options = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX,
            PreserveTableLayout = true,
            Encoding = Encoding.UTF8
        };

        // 4️⃣ Save as plain‑text (.txt)
        string outputPath = "YOUR_DIRECTORY/output.txt";
        doc.Save(outputPath, options);

        Console.WriteLine($"✅ Done! LaTeX equations saved to \"{outputPath}\"");
    }
}
```

شغّل البرنامج (`dotnet run` إذا كنت تستخدم مشروعًا كونسول) وستحصل على ملف `.txt` منظم جاهز لأي سير عمل LaTeX.

## الأسئلة المتكررة

**س: هل يعمل هذا مع `.doc` (الصيغة الثنائية القديمة)؟**  
**ج:** نعم، Aspose.Words يدعم كلًا من `.doc` و `.docx`. فقط وجه `Document` إلى ملف `.doc`؛ نفس `OfficeMathExportMode.LaTeX` ينطبق.

**س: ماذا لو أردت الحفاظ على تنسيق Word الأصلي؟**  
**ج:** النص العادي لا يمكنه الاحتفاظ بالتنسيق. للحصول على مخرجات منسقة، فكر في الحفظ كـ HTML (`HtmlSaveOptions`) أو PDF (`PdfSaveOptions`). تصدير LaTeX يبقى كما هو.

**س: هل يمكنني التحويل مباشرة إلى ملف `.tex`؟**  
**ج:** ليس مباشرةً، لكن يمكنك إعادة تسمية `.txt` إلى `.tex` بعد الحفظ، أو تغليف الناتج بمقدمة LaTeX بسيطة بنفسك.

## الخلاصة

أصبح لديك الآن طريقة شاملة ومتكاملة **لتحويل المعادلات** من مستند Word إلى LaTeX و **حفظ Word كنص** دون فقدان أي معنى رياضي. من خلال تكوين `TxtSaveOptions` لاستخدام `OfficeMathExportMode.LaTeX`، ستحصل على ترميز نظيف يتعامل بسلاسة مع أي معالج LaTeX.

من هنا قد ترغب في استكشاف **كيفية تصدير الرياضيات** إلى صيغ أخرى (HTML, Markdown) أو أتمتة **حفظ docx كـ txt** لمجموعات كبيرة من الأوراق العلمية. النمط نفسه—تحميل، تكوين، حفظ—ينطبق على جميع الحالات، لذا لا تتردد في التجربة.

هل لديك سيناريوهات أخرى ترغب في استكشافها؟ اترك تعليقًا أو راسلني على GitHub. تحويل سعيد!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}