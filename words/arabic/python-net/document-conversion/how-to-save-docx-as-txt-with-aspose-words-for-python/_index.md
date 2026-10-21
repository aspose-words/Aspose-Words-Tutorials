---
category: general
date: 2026-09-21
description: احفظ ملف docx كملف txt باستخدام Aspose.Words للغة Python. حوّل مستند Word إلى
  نص عادي وصّدّر المعادلات إلى LaTeX في ثلاث خطوات بسيطة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx as txt
- convert word to plain text
- how to convert docx to txt
- save document as plain text
- export equations to latex
language: ar
lastmod: 2026-09-21
og_description: احفظ ملفات docx كملفات txt باستخدام Aspose.Words للبايثون. تعلم كيفية
  تحويل Word إلى نص عادي وتصدير المعادلات إلى LaTeX في بضع أسطر من الشيفرة.
og_image_alt: Screenshot showing save docx as txt code snippet in Python
og_title: حفظ ملف docx كملف txt باستخدام Aspose.Words للبايثون – دليل سريع
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Save docx as txt using Aspose.Words for Python. Convert Word to plain
    text and export equations to LaTeX in three simple steps.
  headline: How to save docx as txt with Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- document conversion
- plain text
- LaTeX
title: كيفية حفظ ملف docx كملف txt باستخدام Aspose.Words للبايثون
url: /ar/python/document-conversion/how-to-save-docx-as-txt-with-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية حفظ ملف docx كملف txt باستخدام Aspose.Words للبايثون

إذا كنت بحاجة إلى **حفظ docx كـ txt**، يوضح لك هذا الدليل كيفية القيام بذلك باستخدام Aspose.Words للبايثون. تحويل مستند Word إلى نص عادي مع الحفاظ على المعادلات أمر بسيط عندما تتبع هذه الخطوات.

سوف تتعلم كيفية **تحويل word إلى نص عادي**، وتكوين وضع التصدير لكائنات Office Math، والتحقق من أن الملف الناتج يحتوي على ترميز LaTeX للمعادلات. يفترض الدرس أن لديك معرفة أساسية بالبايثون وإصدار حديث من بايثون (3.8+).

## تثبيت Aspose.Words للبايثون

قبل كتابة أي كود، قم بتثبيت حزمة Aspose.Words من PyPI.

```bash
pip install aspose-words
```

المكتبة توفر مساحة الاسم `aw` المستخدمة طوال هذا الدرس. التثبيت خطوة مرة واحدة؛ نفس الحزمة تعمل لجميع التحويلات اللاحقة.

## إعداد المستند المصدر

ضع ملف DOCX الذي تريد تحويله في دليل معروف. استخدام مسار مطلق يجنب الالتباس عندما يتم تشغيل السكريبت من دليل عمل مختلف.

```python
import aspose.words as aw
import os

# Define input and output paths
input_path = os.path.abspath("YOUR_DIRECTORY/input.docx")
output_path = os.path.abspath("YOUR_DIRECTORY/output.txt")
```

فئة `aw.Document` تقرأ ملف DOCX وتُنشئ تمثيلاً في الذاكرة يمكنك تعديلها أو حفظها بصيغ أخرى.

## تكوين خيارات حفظ TXT

لـ **حفظ docx كـ txt**، يجب إنشاء كائن `TxtSaveOptions`. يتيح لك هذا الكائن التحكم في طريقة عرض كائنات Office Math.

```python
# Step 1: Load the source document
doc = aw.Document(input_path)

# Step 2: Create TXT save options and specify how Office Math objects should be exported
txt_opts = aw.saving.TxtSaveOptions()
txt_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
```

ضبط `office_math_export_mode` إلى `LATEX` يضمن كتابة أي معادلات كرموز LaTeX بدلاً من رموز Unicode العادية. هذا يلبي متطلب **تصدير المعادلات إلى latex**.

## حفظ المستند كنص عادي

الآن يمكنك كتابة المستند إلى ملف نص عادي باستخدام الخيارات المكوَّنة.

```python
# Step 3: Save the document as a plain‑text file using the configured options
doc.save(output_path, txt_opts)
print(f"Document saved as plain text at: {output_path}")
```

استدعاء `doc.save` يُجري التحويل في سطر واحد، محققًا هدف **حفظ المستند كنص عادي**.

## التحقق من الناتج

افتح ملف `output.txt` المُولَّد بأي محرر نصوص. يجب أن ترى فقرات عادية متبوعة بقطع LaTeX لكل معادلة، على سبيل المثال:

```
This is a sample paragraph.

\[
\int_{a}^{b} f(x)\,dx = F(b) - F(a)
\]

Another paragraph without equations.
```

إذا كان الملف يحتوي على ترميز LaTeX، فإن خطوة **تصدير المعادلات إلى latex** قد نجحت بشكل صحيح.

## الحالات الخاصة والنصائح العملية

* **Missing fonts** – Aspose.Words تستبدل الخطوط المفقودة بخط افتراضي. لا يتأثر ناتج النص العادي، لكن قد تتغير الدقة البصرية للمعادلات المُعرَضة. تأكد من أن المستند المصدر يستخدم خطوطًا قياسية أو قم بتضمينها عندما يكون ذلك ممكنًا.
* **Large documents** – بالنسبة للملفات التي يزيد حجمها عن 100 MB، فكر في بث الإدخال باستخدام `aw.loading.LoadOptions` لتقليل استهلاك الذاكرة.
* **Non‑ASCII characters** – فئة `TxtSaveOptions` تستخدم ترميز UTF‑8 افتراضيًا، مما يحافظ على الأحرف Unicode. إذا كنت بحاجة إلى ترميز مختلف، اضبط `txt_opts.encoding = aw.saving.Encoding.ASCII` (غير موصى به لمعظم اللغات).
* **Path handling** – دائمًا استخدم `os.path.abspath` أو `pathlib.Path` لتجنب مفاجآت المسارات النسبية، خاصةً عندما يُشغَّل السكريبت كمهمة مجدولة.

## السكريبت الكامل للنسخ السريع واللصق

فيما يلي المثال الكامل القابل للتنفيذ الذي يدمج جميع الخطوات التي تم مناقشتها.

```python
import aspose.words as aw
import os

def save_docx_as_txt(input_docx: str, output_txt: str) -> None:
    """
    Converts a DOCX file to plain text and exports any Office Math objects as LaTeX.
    """
    # Load the source document
    doc = aw.Document(input_docx)

    # Configure TXT save options
    txt_opts = aw.saving.TxtSaveOptions()
    txt_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX

    # Save as plain‑text file
    doc.save(output_txt, txt_opts)

if __name__ == "__main__":
    # Adjust these paths for your environment
    input_path = os.path.abspath("YOUR_DIRECTORY/input.docx")
    output_path = os.path.abspath("YOUR_DIRECTORY/output.txt")

    # Ensure the output directory exists
    os.makedirs(os.path.dirname(output_path), exist_ok=True)

    save_docx_as_txt(input_path, output_path)
    print(f"Document saved as plain text at: {output_path}")
```

تشغيل هذا السكريبت ينتج ملف `.txt` يحتوي على نص المستند الأصلي وتمثيلات LaTeX لأي معادلات، محققًا هدف **كيفية تحويل docx إلى txt**.

![لقطة شاشة لشفرة حفظ docx كـ txt في بايثون](placeholder-image.png){: .img-fluid alt="لقطة شاشة لشفرة حفظ docx كـ txt في بايثون"}

## الخلاصة

أنت الآن تعرف كيفية **حفظ docx كـ txt** باستخدام Aspose.Words للبايثون، وكيفية **تحويل word إلى نص عادي**، وكيفية **تصدير المعادلات إلى latex** عند الحاجة. المثال الكامل يوضح النهج الموصى به لتحويل مستندات Word إلى ملفات نصية عادية مع الحفاظ على المحتوى الرياضي.

بعد ذلك، استكشف صيغ تصدير أخرى مثل HTML أو PDF عن طريق تعديل فئة خيارات الحفظ. يمكنك أيضًا تجربة محددات مخصصة لإخراج النص العادي أو دمج هذا التحويل في خطوط معالجة مستندات أكبر.

برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Aspose.Words – حفظ docx كـ txt وتصدير معادلات Word كـ LaTeX – دليل كامل](/words/english/net/basic-conversions/save-docx-as-txt-complete-guide-to-export-word-equations-as/)
- [حفظ docx كـ txt – تصدير المعادلات إلى LaTeX باستخدام Aspose.Words](/words/english/net/programming-with-officemath/save-docx-as-txt-export-equations-to-latex-with-aspose-words/)
- [تحويل docx إلى txt – تصدير معادلات Word كـ LaTeX](/words/english/java/document-conversion-and-export/convert-docx-to-txt-export-word-equations-as-latex/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}