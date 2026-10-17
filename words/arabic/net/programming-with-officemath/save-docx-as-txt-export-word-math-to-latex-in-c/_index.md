---
category: general
date: 2026-03-24
description: تعلم كيفية حفظ ملفات docx كملفات txt وتحويل Word إلى LaTeX. يوضح هذا
  الدليل كيفية تصدير المعادلات الرياضية إلى LaTeX باستخدام Aspose.Words.
draft: false
keywords:
- save docx as txt
- convert word to latex
- how to export math
- save document as txt
- export equations to latex
language: ar
og_description: احفظ ملف docx كملف txt وحوّل Word إلى LaTeX. دليل خطوة‑بخطوة حول كيفية
  تصدير المعادلات الرياضية إلى LaTeX باستخدام C#.
og_title: حفظ ملف docx كملف txt – تصدير معادلات Word إلى LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
- Document Conversion
title: حفظ ملف docx كملف txt – تصدير معادلات Word إلى LaTeX في C#
url: /ar/net/programming-with-officemath/save-docx-as-txt-export-word-math-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ docx كملف txt – تصدير معادلات Word إلى LaTeX في C#

هل احتجت يومًا إلى **حفظ docx كملف txt** مع الحفاظ على معادلات Office Math المتقنة؟ لست وحدك. في العديد من المشاريع—الأوراق الأكاديمية، خطوط أنابيب التقارير الآلية، أو معاينات سريعة—ستحتاج إلى نسخة نصية بسيطة من ملف Word مع الحفاظ على الرياضيات بصيغة يفهمها LaTeX.

الخبر السار هو أن Aspose.Words for .NET يتيح لك فعل ذلك ببضع أسطر من C#. في هذا الدرس سنستعرض تحميل ملف *.docx*، ضبط خيارات الحفظ بحيث يتم تصدير الرياضيات كـ LaTeX، وأخيرًا كتابة النتيجة إلى ملف *.txt*. بنهاية الدرس ستعرف **كيفية تصدير الرياضيات** من Word، **تحويل Word إلى LaTeX**، وستحصل على مستند *txt* جاهز للمعالجة اللاحقة.

> **ما ستحصل عليه:** عينة كود كاملة قابلة للتنفيذ، شرح لماذا كل إعداد مهم، نصائح للحالات الخاصة، وخطوة تحقق سريعة لتتأكد من نجاح التحويل.

## المتطلبات المسبقة

قبل أن نبدأ، تأكد من وجود ما يلي:

- **Aspose.Words for .NET** (أحدث حزمة NuGet حتى 2026‑03).  
- بيئة تطوير .NET (Visual Studio، Rider، أو VS Code مع امتداد C#).  
- مستند Word (`input.docx`) يحتوي على كائن Office Math واحد على الأقل (مثل معادلة تم إنشاؤها عبر محرر المعادلات).  
- إلمام أساسي بصياغة C#—لا شيء معقد، مجرد عبارات `using` المعتادة وطريقة `Main`.

إذا كان كل ذلك متوفرًا، لنبدأ.

## الخطوة 1: تحميل المستند المصدر **لحفظ docx كملف txt**

أول ما نحتاجه هو كائن `Document` يمثل ملف *.docx* الذي نريد تحويله. Aspose.Words ي abstracts تنسيق الملف، لذا لا تحتاج للقلق بشأن تفاصيل OpenXML الداخلية.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Load the source document containing equations
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // ... next steps will follow
    }
}
```

*لماذا هذا مهم:* تحميل المستند يمنحنا الوصول إلى شجرة العقد، بما فيها أي عقد `OfficeMath` التي تحمل المعادلات. إذا لم يُعثر على الملف، يرمي Aspose استثناء `FileNotFoundException` واضح، لتعرف فورًا ما الخطأ.

## الخطوة 2: ضبط خيارات حفظ TXT – **تحويل Word إلى LaTeX**

بشكل افتراضي، حفظ الملف كنص عادي سيزيل كل التنسيقات—including الرياضيات. تسمح لنا فئة `TxtSaveOptions` بإخبار المكتبة بالضبط كيف تتعامل مع Office Math. ضبط `OfficeMathExportMode` إلى `LaTeX` يحول كل معادلة إلى تمثيل LaTeX الخاص بها.

```csharp
// Step 2: Configure TXT save options to export Office Math as LaTeX
TxtSaveOptions txtSaveOptions = new TxtSaveOptions
{
    // This flag makes every OfficeMath node become a LaTeX string.
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
};
```

*لماذا هذا مهم:* LaTeX هو اللغة المشتركة للنشر العلمي. بتصديره إلى LaTeX نحافظ على دلالة المعادلة بدلاً من تحويلها إلى رموز غير قابلة للقراءة. إذا احتجت صيغة مختلفة (مثل MathML)، يمكنك استبدال `OfficeMathExportMode.MathML` هنا—مثال آخر على **كيفية تصدير الرياضيات** بطريقة تناسب أدواتك اللاحقة.

## الخطوة 3: حفظ المستند كملف نصي باستخدام الخيارات المضبوطة

الآن بعد ضبط الخيارات، الخطوة الأخيرة هي سطر واحد فقط: استدعِ `Save` مع مسار الهدف وكائن `TxtSaveOptions`.

```csharp
// Step 3: Save the document as a plain‑text file using the configured options
doc.Save("YOUR_DIRECTORY/Math.txt", txtSaveOptions);
```

هذا كل شيء! سيحتوي الملف `Math.txt` على النص العادي من مستند Word، وستظهر كل معادلة كمقتطف LaTeX محاط بـ `$…$` (inline) أو `$$…$$` (display) حسب التخطيط الأصلي.

### النتيجة المتوقعة

إذا كان `input.docx` يحتوي على معادلة بسيطة مثل *x² + y² = z²*، فإن السطر المقابل في `Math.txt` سيظهر كالتالي:

```
The Pythagorean theorem is expressed as $x^{2} + y^{2} = z^{2}$ in LaTeX.
```

يمكنك فتح الملف الناتج بأي محرر، تمريره إلى مُجمّع LaTeX، أو توجيهه إلى معالج markdown يدعم معادلات LaTeX.

![لقطة شاشة لـ Math.txt تُظهر معادلات LaTeX](/images/save-docx-as-txt-example.png "مثال حفظ docx كملف txt")

*نص بديل للصورة:* **مثال حفظ docx كملف txt** – ملف نصي عادي يحتوي على معادلات LaTeX.

## كيفية تصدير الرياضيات – التحقق من التحويل

فحص سريع يحمّك من الأخطاء الخفية لاحقًا. بعد استدعاء `Save`، اقرأ الملف مرة أخرى واطبع الأسطر القليلة الأولى:

```csharp
// Optional verification step
string[] lines = File.ReadAllLines("YOUR_DIRECTORY/Math.txt");
Console.WriteLine("First 5 lines of the exported txt:");
for (int i = 0; i < Math.Min(5, lines.Length); i++)
{
    Console.WriteLine(lines[i]);
}
```

إذا رأيت مقاطع LaTeX بدلاً من رموز Unicode مشوشة، فقد نجحت **تصدير المعادلات إلى LaTeX**. إذا لم يحدث ذلك، تأكد من أن المستند المصدر يحتوي فعليًا على كائنات `OfficeMath`—المعادلات النصية العادية لن تُحوَّل.

## الحالات الخاصة والنصائح العملية (حفظ المستند كملف txt)

| الحالة | ما يجب مراقبته | التعديل الموصى به |
|-----------|-------------------|-------------------|
| **مستندات كبيرة (>100 MB)** | استهلاك الذاكرة يزداد عند تحميل الملف بالكامل. | استخدم `LoadOptions` مع `LoadFormat.Docx` وابدأ القراءة عبر تدفق إذا واجهت `OutOfMemoryException`. |
| **معادلات برموز مخصصة** | قد لا يوجد مكافئ LaTeX مباشر لبعض الرموز النادرة. | عالج الناتج بعد ذلك بقاموس استبدال بسيط (مثلاً استبدل `\unicode{...}` بالماكرو المناسب). |
| **محتوى متعدد اللغات** | تُحافظ Unicode على الأحرف، لكن LaTeX قد يحتاج حزمًا مثل `inputenc`. | أضف `\usepackage[utf8]{inputenc}` في أعلى مستند LaTeX عند التجميع لاحقًا. |
| **تحتاج نصًا عاديًا بدون LaTeX** | علم `OfficeMathExportMode` يُجبر على LaTeX. | اضبط `OfficeMathExportMode = OfficeMathExportMode.Text` للحصول على وصف نصي بدلاً من ذلك. |

> **نصيحة محترف:** إذا كنت تخطط لمعالجة دفعات من الملفات، غلف منطق الثلاث خطوات في طريقة قابلة لإعادة الاستخدام:

```csharp
static void ConvertDocxToTxtWithLatex(string srcPath, string dstPath)
{
    Document doc = new Document(srcPath);
    TxtSaveOptions opts = new TxtSaveOptions { OfficeMathExportMode = OfficeMathExportMode.LaTeX };
    doc.Save(dstPath, opts);
}
```

يمكنك بعدها استدعاء `ConvertDocxToTxtWithLatex` داخل حلقة `foreach` على مجلد يحتوي على ملفات Word.

## الخطوات التالية – توسيع سير العمل

الآن بعد أن عرفت **كيفية تصدير الرياضيات** من Word و**حفظ docx كملف txt**، قد ترغب في:

- **دمج مع خط أنابيب Markdown** – أضف كتلة YAML في مقدمة `Math.txt` ومرّرها إلى مولّدات المواقع الثابتة.  
- **الدمج مع نظام بناء LaTeX** – اجمع عدة ملفات `.txt` في مصدر `.tex` واحد وشغّل `pdflatex`.  
- **استكشاف صيغ تصدير أخرى** – يدعم Aspose.Words أيضًا `HtmlSaveOptions` مع إخراج MathML، مثالي للعارضات على الويب.  

كل أحد هذه السيناريوهات يعيد استخدام الفكرة الأساسية: ضبط `SaveOptions` المناسبة وترك Aspose يتولى الجزء الصعب.

---

### TL;DR

أظهرنا لك كيفية **حفظ docx كملف txt** مع **تحويل Word إلى LaTeX** لكل كائن Office Math، مما يجيب بفعالية على سؤال **كيفية تصدير الرياضيات** و**تصدير المعادلات إلى LaTeX** في C#. المثال الكامل القابل للتنفيذ موجود في مقاطع الكود أعلاه، ومع خطوة التحقق الاختيارية يمكنك التأكد من نجاح التحويل. لا تتردد في تعديل الإعدادات لتناسب سير عملك، ونتمنى لك برمجة سعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}