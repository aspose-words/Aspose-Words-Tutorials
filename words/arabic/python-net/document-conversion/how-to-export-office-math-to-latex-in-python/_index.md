---
category: general
date: 2026-10-07
description: تعلم كيفية تصدير معادلات Office Math إلى LaTeX في بايثون باستخدام Aspose.Words.
  يوضح لك هذا الدليل خطوة بخطوة كيفية تصدير المعادلات من Word إلى تنسيق LaTeX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to export office math to latex
- how to export equations from word
- Aspose.Words Python
- LaTeX conversion
- Office Math extraction
language: ar
lastmod: 2026-10-07
og_description: كيفية تصدير معادلات Office Math إلى LaTeX في بايثون باستخدام Aspose.Words.
  اتبع هذا الدليل لتصدير المعادلات من Word بسرعة وبشكل موثوق.
og_image_alt: Screenshot of LaTeX equation output generated from a Word document
og_title: تصدير صيغ أوفيس الرياضية إلى LaTeX في بايثون – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to export office math to LaTeX in Python with Aspose.Words.
    This step‑by‑step guide shows you how to export equations from Word to LaTeX format.
  headline: How to export office math to LaTeX in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- LaTeX
- Office Math
title: كيفية تصدير الرياضيات من Office إلى LaTeX في بايثون
url: /ar/python/document-conversion/how-to-export-office-math-to-latex-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تصدير الرياضيات المكتبية إلى LaTeX في Python

إذا كنت بحاجة إلى تصدير الرياضيات المكتبية إلى LaTeX، يوضح لك هذا الدليل كيفية تصدير المعادلات من Word باستخدام Aspose.Words for Python. ستشاهد مثالًا كاملاً قابلاً للتنفيذ يحول ملف `.docx` يحتوي على كائنات Office Math إلى شفرة LaTeX نصية عادية.

تصدير المعادلات هو طلب شائع عندما تريد إعادة استخدام محتوى Word في الأوراق العلمية، أو مولدات المواقع الثابتة، أو أي سير عمل يعتمد على LaTeX. تغطي الخطوات أدناه كل شيء من تثبيت SDK إلى التحقق من المخرجات التي تم إنشاؤها.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من أن لديك:

* Python 3.8 أو أحدث مثبت على جهازك.
* رخصة صالحة لـ **Aspose.Words for Python via .NET** (التقييم المجاني يعمل للاختبار).
* إمكانية الوصول إلى `pip` لتثبيت حزمة `aspose-words`.
* مستند Word (`.docx`) يحتوي على كائن Office Math واحد على الأقل (معادلة). في هذا الدرس نفترض أن الملف اسمه `math.docx` وموجود في `YOUR_DIRECTORY`.

> **نصيحة احترافية:** إذا لم يكن لديك ملف ترخيص، ضع ترخيص التجربة (`Aspose.Words.lic`) في نفس الدليل الذي يحتوي على السكريبت الخاص بك؛ سيقوم SDK بتحميله تلقائيًا.

## تثبيت Aspose.Words for Python

الخطوة الأولى هي إضافة مكتبة Aspose.Words إلى بيئة Python الخاصة بك.

```bash
pip install aspose-words
```

تشغيل الأمر يثبت حزمة `aspose.words` وجميع مكونات .NET runtime المطلوبة. بعد التثبيت، يمكنك استيراد المكتبة باستخدام `import aspose.words as aw`.

## الخطوة 1: تحميل مستند Word الذي يحتوي على المعادلات

يجب عليك تحميل ملف `.docx` المصدر قبل أن تتمكن من تعديل محتواه. تقوم فئة `Document` بقراءة الملف إلى الذاكرة وتمنحك الوصول إلى كل عنصر، بما في ذلك كائنات Office Math.

```python
import aspose.words as aw

# Replace YOUR_DIRECTORY with the actual path to your files
doc_path = "YOUR_DIRECTORY/math.docx"

# Load the Word document that holds the equations
document = aw.Document(doc_path)
```

تحميل المستند أمر أساسي لأن عملية التصدير تعمل على تمثيل الذاكرة، وليس على نظام الملفات مباشرة.

## الخطوة 2: إنشاء خيارات حفظ TXT وتعيين وضع التصدير

يقوم Aspose.Words بحفظ المستند كنص عادي باستخدام `TxtSaveOptions`. بشكل افتراضي، تُعرض كائنات Office Math كحروف Unicode، مما يفقد البنية الرياضية. ضبط `office_math_export_mode` إلى `LATEX` يخبر SDK بإصدار شفرة LaTeX لكل معادلة.

```python
# Create TXT save options to control the export behavior
txt_options = aw.saving.TxtSaveOptions()

# Export any Office Math (equations) in LaTeX format
txt_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
```

الثابت `OfficeMathExportMode.LATEX` هو المفتاح الذي يفعّل تحويل LaTeX. بدون هذا الإعداد، سيحتوي الناتج على تقريبات نصية عادية للمعادلات.

## الخطوة 3: حفظ المستند كملف نص عادي باستخدام الخيارات المكوّنة

الآن اكتب المستند إلى ملف `.txt`. يطبق SDK الخيارات التي قمت بتكوينها في الخطوة السابقة، منتجًا ملفًا يظهر فيه كل معادلة كجزء LaTeX.

```python
# Destination path for the exported LaTeX text file
out_path = "YOUR_DIRECTORY/out.txt"

# Save the document using the TXT options that include LaTeX conversion
document.save(out_path, txt_options)

print(f"LaTeX export completed. File saved to: {out_path}")
```

عند انتهاء السكريبت، يحتوي `out.txt` على النص الأصلي من Word بالإضافة إلى تمثيلات LaTeX لكل كائن Office Math.

## التحقق من مخرجات LaTeX

افتح `out.txt` في أي محرر نصوص لرؤية النتيجة. معادلة نموذجية مثل *\(a^2 + b^2 = c^2\)* ستظهر كالتالي:

```
\[
a^{2}+b^{2}=c^{2}
\]
```

إذا كنت تفضّل عرض LaTeX مباشرة في وحدة التحكم، يمكنك قراءة الملف مرة أخرى وطباعة محتوياته:

```python
with open(out_path, "r", encoding="utf-8") as f:
    latex_content = f.read()
    print("--- LaTeX content start ---")
    print(latex_content)
    print("--- LaTeX content end ---")
```

يجب أن يتطابق الناتج مع المعادلات في مستند Word الأصلي، مع الحفاظ على الكسور، والرفع، والخفض، وغيرها من الرموز الرياضية.

## كيفية تصدير المعادلات من Word – التعامل مع الحالات الخاصة

بينما يعمل التدفق الأساسي لمعظم المستندات، تتطلب بعض السيناريوهات اهتمامًا إضافيًا:

| الحالة | النهج الموصى به |
|-----------|----------------------|
| **المستند يحتوي على مزيج من MathML و Office Math** | استخدم `OfficeMathExportMode.MATHML` للحصول على مخرجات MathML، أو نفّذ تمريرة ثانية بـ `LATEX` بعد تحويل MathML إلى LaTeX يدويًا. |
| **المستندات الكبيرة تسبب ضغطًا على الذاكرة** | عالج المستند على أقسام: حمّل قسمًا، صدّره، ثم حرّره قبل الانتقال إلى القسم التالي. |
| **المعادلات داخل رؤوس أو حواشي** | وضع التصدير يتعامل معها تلقائيًا، لكن تحقق من عدم حذف النص المحيط بواسطة خيارات حفظ مخصصة. |
| **غياب الترخيص يؤدي إلى علامة مائية للتقييم** | تأكد من تحميل ملف الترخيص قبل أي عملية على `Document`: `aw.License().set_license("Aspose.Words.lic")`. |

معالجة هذه الحالات الخاصة تضمن أن **كيفية تصدير الرياضيات المكتبية إلى LaTeX** تعمل بشكل موثوق عبر ملفات Word المتنوعة.

## السكريبت الكامل

فيما يلي السكريبت الكامل المستقل للـ Python الذي يمكنك نسخه، لصقه، وتشغيله. يتضمن معالجة الأخطاء وتعليقات لتوضيح الفكرة.



## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شاملة من الشيفرة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك الخاصة.

- [تحويل docx إلى markdown – تصدير معادلات الرياضيات إلى LaTeX باستخدام Aspose.Words](/words/english/java/document-conversion-and-export/convert-docx-to-markdown-export-math-equations-to-latex-with/)
- [حفظ docx كملف txt – تصدير المعادلات إلى LaTeX باستخدام Aspose.Words](/words/english/net/programming-with-officemath/save-docx-as-txt-export-equations-to-latex-with-aspose-words/)
- [كيفية تصدير LaTeX من Word – تحويل DOCX إلى Markdown](/words/english/python-net/document-conversion/how-to-export-latex-from-word-convert-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}