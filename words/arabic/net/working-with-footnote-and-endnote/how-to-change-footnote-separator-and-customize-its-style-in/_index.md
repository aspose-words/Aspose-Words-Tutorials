---
category: general
date: 2026-10-13
description: كيفية تغيير فاصل الحاشية السفلية في مستند Word باستخدام Aspose.Words.
  تعلّم كيفية تغيير لون الخط في مستند Word برمجيًا.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to change footnote separator
- change font color in word document
- style footnote separator programmatically
- Aspose.Words footnote formatting
- C# Word automation
language: ar
lastmod: 2026-10-13
og_description: كيفية تغيير فاصل الحاشية السفلية في مستند Word باستخدام Aspose.Words.
  يوضح لك هذا الدرس كيفية تغيير لون الخط في مستند Word باستخدام C#.
og_image_alt: Screenshot of a Word document showing red footnote separator and blue
  endnote separator
og_title: كيفية تغيير فاصل الحواشي السفلية في مستند Word – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  headline: How to change footnote separator and customize its style in a Word document
  type: TechArticle
- description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  name: How to change footnote separator and customize its style in a Word document
  steps:
  - name: Why each line matters
    text: '* **Loading the document** (`new Document`) gives you an in‑memory representation
      that Aspose.Words can manipulate. * **`GetChild` with `ParagraphNodeType.FootnoteSeparator`**
      returns the hidden paragraph that Word uses to draw the line separating footnotes
      from the main text. The same method works '
  - name: Expected output
    text: 'When you open `FootnoteSeparatorsStyled.docx` in Microsoft Word:'
  - name: 1. Install Aspose.Words
    text: 'Open a terminal in your project folder and run:'
  - name: 2. Prepare the input file
    text: Place `Footnotes.docx` in a known directory (e.g., `C:\Docs`). Ensure the
      file contains at least one footnote and one endnote so the separator nodes exist.
  - name: 3. Write the C# program
    text: Create a new console project (`dotnet new console -n FootnoteStyler`) and
      replace the generated `Program.cs` with the full code block from the **How to
      change footnote separator** section. Remember to adjust the file paths to match
      your environment.
  - name: 4. Run and verify
    text: 'Execute the program:'
  - name: 5. Extend the solution
    text: '* **Different colors:** Use any `System.Drawing.Color` value, e.g., `Color.FromArgb(255,
      128, 0)` for orange. * **Custom line style:** Instead of changing the color,
      you can modify `ParagraphFormat` properties such as `LineSpacing`, `Shading`,
      or even replace the separator character. * **Multiple do'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- footnotes
- document styling
title: كيفية تغيير فاصل الحاشية وتخصيص نمطها في مستند Word
url: /ar/net/working-with-footnote-and-endnote/how-to-change-footnote-separator-and-customize-its-style-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تغيير فاصل الحاشية وتخصيص نمطه في مستند Word

إذا كنت بحاجة إلى **how to change footnote separator** في مستند Word، فإن هذا الدليل يقدم لك حلاً كاملاً وجاهزًا للتنفيذ. باستخدام Aspose.Words for .NET يمكنك أيضًا **change font color in Word document** لعناصر مثل فواصل الحواشي والحواشي الختامية، مما يجعل الملف النهائي يتطابق مع علامتك التجارية أو دليل النمط الخاص بك.

غالبًا ما يسأل مؤلفو المستندات: *لماذا يبدو فاصل الحاشية الافتراضي بسيطًا، وكيف يمكنني جعله بارزًا؟* الجواب هو الوصول مباشرة إلى كائنات الفقرات الفاصلة، تعديل خصائص الخط الخاصة بها، ثم حفظ النتيجة. هذا الدليل يشرح لك كل خطوة، من تحميل ملف .docx إلى حفظ المخرجات المنسقة.

ستتعلم كيفية:

* تحميل ملف Word يحتوي بالفعل على حواشي وحواشي ختامية.  
* تحديد فقرات فاصل الحاشية وفاصل الحاشية الختامية.  
* تغيير لون الخط لكل فاصل (أحمر للحواشي، أزرق للحواشي الختامية).  
* حفظ المستند المعدل دون فقدان أي محتوى موجود.

لا تحتاج إلى أدوات خارجية بخلاف مكتبة Aspose.Words وبيئة تطوير .NET.

## المتطلبات المسبقة

* .NET 6.0 SDK أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.7+).  
* Visual Studio 2022، Rider، أو أي محرر C# تفضله.  
* حزمة NuGet Aspose.Words for .NET (`Aspose.Words`).  
* ملف Word تجريبي (`Footnotes.docx`) يحتوي على حاشية واحدة على الأقل وحاشية ختامية واحدة.

> **نصيحة احترافية:** إذا لم يكن لديك ملف تجريبي، أنشئ مستند Word جديد، أدخل حاشية (`References → Insert Footnote`) وحاشية ختامية (`References → Insert Endnote`). احفظه باسم `Footnotes.docx` في مجلد يمكنك الإشارة إليه من الشيفرة.

## كيفية تغيير فاصل الحاشية باستخدام Aspose.Words

النواة في هذه المهمة هي استرجاع الفقرات الخاصة التي تعرضها Aspose.Words كعُقد *separator*. هذه العُقد من النوع `Paragraph` ويمكن تنسيقها مثل أي فقرة أخرى.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

class FootnoteSeparatorStyler
{
    static void Main()
    {
        // Step 1: Load the source document that already contains footnotes/endnotes.
        Document doc = new Document(@"C:\Docs\Footnotes.docx");

        // Step 2: Get the footnote separator paragraph.
        Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

        // Step 3: Get the endnote separator paragraph.
        Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

        // Step 4: Change the font color of the footnote separator to red.
        footnoteSeparator.Font.Color = Color.Red;

        // Step 5: Change the font color of the endnote separator to blue.
        endnoteSeparator.Font.Color = Color.Blue;

        // Step 6: Save the modified document.
        doc.Save(@"C:\Docs\FootnoteSeparatorsStyled.docx");
    }
}
```

### لماذا كل سطر مهم

* **Loading the document** (`new Document`) يمنحك تمثيلًا في الذاكرة يمكن لـ Aspose.Words التلاعب به.  
* **`GetChild` with `ParagraphNodeType.FootnoteSeparator`** يُعيد الفقرة المخفية التي يستخدمها Word لرسم الخط الفاصل بين الحواشي والنص الرئيسي. نفس الطريقة تعمل لفاصل الحاشية الختامية.  
* **Changing `Font.Color`** يؤثر مباشرة على مظهر الخط لأن Word يعرض الفاصل كفقرة تحتوي على حرف “‑” واحد. ضبط اللون إلى `Color.Red` (أو أي `System.Drawing.Color`) يحدّث النمط البصري.  
* **Saving** يكتب التغييرات إلى ملف .docx يمكن لأي معالج Word فتحه.

### النتيجة المتوقعة

عند فتح `FootnoteSeparatorsStyled.docx` في Microsoft Word:

* يظهر خط فاصل الحاشية **باللون الأحمر**.  
* يظهر خط فاصل الحاشية الختامية **باللون الأزرق**.  

جميع محتويات الحواشي والحواشي الختامية الأصلية تبقى دون تعديل.

## تغيير لون الخط في مستند Word باستخدام C#

العملية الموضحة أعلاه هي حالة خاصة من قدرة أوسع: **change font color in Word document** برمجيًا. بمجرد حصولك على `Paragraph` أو `Run` أو أي `Node` يحتوي نصًا، يمكنك تعديل خاصية `Font.Color` الخاصة به.

```csharp
// Example: Change the color of all headings (style "Heading 1") to dark green.
foreach (Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.StyleIdentifier == StyleIdentifier.Heading1)
        para.Font.Color = Color.DarkGreen;
}
```

* يمر هذا المقتطف على كل فقرة، يتحقق مما إذا كانت تستخدم نمط `Heading 1`، ويضبط لون الخط.  
* يمكنك تعديل الشرط لاستهداف الحواشي أو الجداول أو أي نوع عقدة آخر.

## تحليل خطوة بخطوة

### 1. تثبيت Aspose.Words

افتح طرفية في مجلد مشروعك وشغّل:

```bash
dotnet add package Aspose.Words
```

الحزمة تشمل جميع التجميعات المطلوبة للكود المعروض سابقًا.

### 2. إعداد ملف الإدخال

ضع `Footnotes.docx` في مسار معروف (مثال: `C:\Docs`). تأكد أن الملف يحتوي على حاشية واحدة على الأقل وحاشية ختامية واحدة حتى تكون عُقد الفواصل موجودة.

### 3. كتابة برنامج C#

أنشئ مشروعًا جديدًا من نوع console (`dotnet new console -n FootnoteStyler`) واستبدل ملف `Program.cs` المُولد بكتلة الشيفرة الكاملة من قسم **How to change footnote separator**. تذكر تعديل مسارات الملفات لتتناسب مع بيئتك.

### 4. تشغيل والتحقق

نفّذ البرنامج:

```bash
dotnet run
```

بعد انتهاء التنفيذ، افتح `FootnoteSeparatorsStyled.docx`. يجب أن ترى الخطوط الحمراء والزرقاء للفواصل كما هو موضح.

### 5. توسيع الحل

* **ألوان مختلفة:** استخدم أي قيمة من `System.Drawing.Color`، مثل `Color.FromArgb(255, 128, 0)` للبرتقالي.  
* **نمط خط مخصص:** بدلاً من تغيير اللون، يمكنك تعديل خصائص `ParagraphFormat` مثل `LineSpacing`، `Shading`، أو حتى استبدال حرف الفاصل.  
* **عدة مستندات:** غلف المنطق داخل طريقة تقبل مسارات الإدخال والإخراج، ثم استدعها في حلقة لمعالجة دفعة من الملفات.

## المشكلات الشائعة وكيفية تجنّبها

| العَرَض | السبب | الحل |
|---------|-------|-----|
| `GetChild` returns `null` | المستند المصدر لا يحتوي على فاصل حاشية/حاشية ختامية (مثلاً لا توجد حواشي). | أضف حاشية أو حاشية ختامية على الأقل، أو تحقق من `null` قبل الوصول إلى `Font`. |
| Color change not visible | يُعرض الفاصل كخط بدلاً من حرف في بعض إصدارات Word. | اضبط `ParagraphFormat.LineSpacingRule = LineSpacingRule.Exactly` و`ParagraphFormat.LineSpacing = 1` لإجبار ظهور حرف مرئي. |
| Runtime exception `FileNotFoundException` | مسار الملف غير صحيح. | استخدم مسارات مطلقة أو `Path.Combine` مع `Environment.CurrentDirectory`. |

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه‑ولصقه في تطبيق console. يتضمن معالجة الأخطاء وتعليقات توضح كل عملية.

```csharp
using System;
using System.Drawing;
using Aspose.Words;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // Paths – update these to match your environment.
            const string inputPath = @"C:\Docs\Footnotes.docx";
            const string outputPath = @"C:\Docs\FootnoteSeparatorsStyled.docx";

            // Load the document.
            Document doc = new Document(inputPath);

            // Retrieve footnote separator.
            Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

            // Retrieve endnote separator.
            Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

            // Guard against missing separators.
            if (footnoteSeparator == null || endnoteSeparator == null)
            {
                Console.WriteLine("The document does not contain footnote or endnote separators.");
                return;
            }

            // Change colors – this is the core of “change font color in word document”.
            footnoteSeparator.Font.Color = Color.Red;   // Footnote separator → red
            endnoteSeparator.Font.Color = Color.Blue; // Endnote separator → blue

            // Save the result.
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

تشغيل هذا البرنامج ينتج ملف Word يكون فيه خط فاصل الحاشية أحمر وخط فاصل الحاشية الختامية أزرق، محققًا متطلبات **how to change footnote separator** مع إظهار **change font color in word document**.

## الخلاصة

أنت الآن تعرف **how to change footnote separator** في مستند Word باستخدام Aspose.Words for .NET وكيفية **change font color in Word document** برمجيًا. الخطوات هي:

1. تحميل المستند.  
2. استرجاع فقرات الفاصل المخفية.  
3. ضبط خاصية `Font.Color` لها.  
4. حفظ الملف المعدل.

من هنا يمكنك استكشاف تنسيقات أكثر تقدمًا—تعديل سمك الخط، تطبيق خطوط مختلفة، أو أتمتة العملية عبر العديد من الملفات. إتقان هذه التقنيات يمنحك تحكمًا دقيقًا في مظهر مستندات Word مباشرةً من كود C#.

---

## ماذا يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Get Paragraph Style Separator In Word Document](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Add Page Numbers to the Footer of a Word Document Using Aspose.Words for .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}