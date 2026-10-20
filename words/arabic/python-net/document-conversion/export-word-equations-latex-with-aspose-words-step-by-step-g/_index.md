---
category: general
date: 2026-08-07
description: تصدير معادلات LaTeX في Word إلى ملفات LaTeX باستخدام Aspose.Words. تعلّم
  كيفية تحويل رياضيات Word إلى LaTeX واستخراج المعادلات من Word بسرعة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- export word equations latex
- convert word math latex
- extract latex from word
- extract equations from word
language: ar
lastmod: 2026-08-07
og_description: تصدير معادلات Word بصيغة LaTeX باستخدام Aspose.Words. يوضح هذا الدليل
  كيفية تحويل رياضيات Word إلى LaTeX واستخراج المعادلات من Word في سكريبت واحد.
og_image_alt: Screenshot of a Python script exporting Word equations to LaTeX
og_title: تصدير معادلات Word إلى LaTeX – دليل Aspose.Words الكامل
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Export word equations latex to LaTeX files using Aspose.Words. Learn
    how to convert word math latex and extract equations from word quickly.
  headline: Export word equations latex with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Export word equations latex to LaTeX files using Aspose.Words. Learn
    how to convert word math latex and extract equations from word quickly.
  name: Export word equations latex with Aspose.Words – step‑by‑step guide
  steps:
  - name: Expected output
    text: 'If `equations.docx` contains two equations, the resulting `out.txt` might
      look like:'
  - name: Verify the file
    text: Open `out.txt` in any text editor and confirm that every equation is represented
      by LaTeX. If an equation is missing, it is likely not an Office Math object
      (e.g., an image of a formula). In that case, you must replace the image manually
      or use OCR tools.
  - name: 'Edge case: Documents without Office Math'
    text: 'If the source document contains no Office Math objects, the output file
      will be plain text without LaTeX blocks. You can check the presence of equations
      beforehand:'
  - name: 'Edge case: Large documents'
    text: 'For very large `.docx` files, consider streaming the output to avoid high
      memory consumption:'
  - name: Next steps
    text: '* Explore `aw.saving.TxtSaveOptions` properties such as `encoding` to control
      character sets. * Combine the exported LaTeX with a template engine (e.g., Jinja2)
      to generate full LaTeX reports. * If you need inline math rather than display
      math, set `txt_save_options.math_output_mode = aw.saving.Math'
  type: HowTo
tags:
- Aspose.Words
- Python
- LaTeX
- Word equations
title: تصدير معادلات Word إلى LaTeX باستخدام Aspose.Words – دليل خطوة بخطوة
url: /ar/python/document-conversion/export-word-equations-latex-with-aspose-words-step-by-step-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تصدير معادلات Word بصيغة LaTeX باستخدام Aspose.Words – دليل خطوة بخطوة

إذا كنت بحاجة إلى **تصدير معادلات Word بصيغة LaTeX**، فإن هذا الدليل يوضح لك بالضبط كيفية القيام بذلك. ستتعلم أيضًا كيفية **تحويل معادلات Word إلى LaTeX** واستخراج تمثيل LaTeX الأساسي لكل معادلة في ملف Word.

يغطي الدليل كل ما تحتاجه لتشغيل سكريبت بايثون يقرأ مستند *.docx*، يضبط خيارات الحفظ المناسبة، ويكتب ملف نصي *.txt* يحتوي على كود LaTeX. لا تحتاج إلى أدوات خارجية بخلاف Aspose.Words for Python.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* Python 3.8 أو أحدث مثبت.
* ترخيص فعال لـ Aspose.Words for Python عبر .NET (أو مفتاح تقييم مجاني).
* مستند Word (`.docx`) يحتوي على معادلات Office Math تريد استخراجها.
* إلمام أساسي بنظام الاستيراد في بايثون.

إذا كان أي من هذه العناصر مفقودًا، قم بتثبيته الآن؛ الخطوات أدناه تفترض توفرها.

## الخطوة 1: تثبيت Aspose.Words for Python

افتح الطرفية ونفّذ:

```bash
pip install aspose-words
```

حزمة `aspose-words` توفر مساحة الاسم `aw` المستخدمة في أمثلة الشيفرة. تثبيت الحزمة يحل مشكلة `ImportError` التي تظهر عندما يحاول السكريبت استيراد `aw`.

## الخطوة 2: تحميل مستند Word الذي يحتوي على المعادلات

```python
import aspose.words as aw

# Load the source document. Replace the path with the location of your .docx file.
document = aw.Document("YOUR_DIRECTORY/equations.docx")
```

فئة `aw.Document` تقوم بتحليل ملف Word بالكامل، بما في ذلك النصوص، الصور، وكائنات Office Math. تحميل المستند هو الخطوة الأولى نحو **استخراج LaTeX من Word** لأن المكتبة تنشئ تمثيلًا في الذاكرة لكل معادلة.

## الخطوة 3: ضبط خيارات حفظ TXT لتصدير Office Math كـ LaTeX

```python
txt_save_options = aw.saving.TxtSaveOptions()
txt_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
```

`TxtSaveOptions` تخبر Aspose.Words كيفية كتابة ملف الإخراج. ضبط `office_math_export_mode` إلى `LATEX` يوجه المكتبة لاستبدال كل كائن Office Math بما يعادله من LaTeX. هذه هي الآلية الأساسية التي تمكّنك من **تصدير معادلات Word بصيغة LaTeX** في نداء واحد.

## الخطوة 4: حفظ المستند كملف نصي عادي

```python
output_path = "YOUR_DIRECTORY/out.txt"
document.save(output_path, txt_save_options)
print(f"LaTeX export completed. File saved to {output_path}")
```

عند تنفيذ `document.save` مع `txt_save_options` المُكوَّنة، تقوم Aspose.Words بكتابة ملف `.txt` حيث تظهر كل معادلة ككود LaTeX محاط بنص الفقرات العادي. النتيجة هي مصدر LaTeX نظيف وقابل للبحث يمكنك تمريره إلى أي مُجمع LaTeX.

### النتيجة المتوقعة

إذا كان `equations.docx` يحتوي على معادلتين، قد يبدو `out.txt` الناتج كالتالي:

```
This is a paragraph before the first equation.

\[
\frac{a}{b} = c
\]

Another paragraph.

\[
E = mc^2
\]

End of document.
```

لاحظ أن كتل LaTeX محاطة بـ `\[` و `\]`، وهو الفاصل الافتراضي للرياضيات العرضية الذي تستخدمه Aspose.Words.

## الخطوة 5: التحقق من التصدير ومعالجة الحالات الخاصة

### التحقق من الملف

افتح `out.txt` في أي محرر نصوص وتأكد من أن كل معادلة ممثلة بـ LaTeX. إذا كانت معادلة مفقودة، فمن المحتمل أنها ليست كائن Office Math (مثل صورة لصيغة). في هذه الحالة، يجب استبدال الصورة يدويًا أو استخدام أدوات OCR.

### حالة خاصة: مستندات بدون Office Math

إذا كان المستند الأصلي لا يحتوي على كائنات Office Math، فإن ملف الإخراج سيكون نصًا عاديًا بدون كتل LaTeX. يمكنك التحقق من وجود المعادلات مسبقًا:

```python
has_math = any(isinstance(node, aw.Math.OfficeMath) for node in document.get_child_nodes(aw.NodeType.OFFICE_MATH, True))
if not has_math:
    print("No Office Math equations found; nothing to export.")
```

### حالة خاصة: مستندات كبيرة

لملفات `.docx` الكبيرة جدًا، فكر في تدفق الإخراج لتجنب استهلاك الذاكرة العالي:

```python
with open(output_path, "w", encoding="utf-8") as out_file:
    document.save(out_file, txt_save_options)
```

التدفق يكتب كل صفحة بشكل متسلسل، مما يحافظ على استهلاك الذاكرة منخفضًا مع الاستمرار في **تصدير معادلات Word بصيغة LaTeX** بشكل صحيح.

## الخطوة 6: أتمتة العملية لعدة ملفات (اختياري)

إذا كنت بحاجة إلى **استخراج المعادلات من Word** دفعيًا، غلف المنطق داخل دالة وتكرارها على مجلد:

```python
import os

def export_latex_from_docx(src_path, dst_path):
    doc = aw.Document(src_path)
    options = aw.saving.TxtSaveOptions()
    options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
    doc.save(dst_path, options)

source_dir = "YOUR_DIRECTORY/source_docs"
target_dir = "YOUR_DIRECTORY/latex_exports"

os.makedirs(target_dir, exist_ok=True)

for filename in os.listdir(source_dir):
    if filename.lower().endswith(".docx"):
        src = os.path.join(source_dir, filename)
        dst = os.path.join(target_dir, os.path.splitext(filename)[0] + ".txt")
        export_latex_from_docx(src, dst)
        print(f"Exported {filename} → {dst}")
```

هذا السكريبت المساعد **يحوّل معادلات Word إلى LaTeX** لكل مستند في المجلد، مما يجعل سير العمل قابلًا للتوسع للمشاريع الكبيرة.

## الخلاصة

أصبح لديك الآن حل كامل وقابل للتنفيذ لـ **تصدير معادلات Word بصيغة LaTeX** باستخدام Aspose.Words for Python. يقوم السكريبت بتحميل ملف Word، ضبط `TxtSaveOptions` لإنتاج LaTeX، وكتابة النتيجة إلى ملف نصي عادي. باستخدام المقتطف الاختياري للمعالجة الجماعية، يمكنك أيضًا **استخراج LaTeX من Word** و**استخراج المعادلات من Word** عبر العديد من المستندات بأقل جهد.

### الخطوات التالية

* استكشف خصائص `aw.saving.TxtSaveOptions` مثل `encoding` للتحكم في مجموعات الأحرف.
* دمج LaTeX المُصدَّر مع محرك قوالب (مثل Jinja2) لإنشاء تقارير LaTeX كاملة.
* إذا كنت تحتاج إلى رياضيات داخلية بدلاً من عرضية، اضبط `txt_save_options.math_output_mode = aw.saving.MathOutputMode.INLINE`.

لا تتردد في تجربة الإعدادات ودمج السكريبت في خط أنابيب توليد المستندات الخاص بك. Happy coding!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [How to Export LaTeX from Word – Step‑by‑Step Guide](/words/english/net/basic-conversions/how-to-export-latex-from-word-step-by-step-guide/)
- [How to Export LaTeX from Word: Convert DOCX to Markdown with Aspose](/words/english/net/programming-with-markdownsaveoptions/how-to-export-latex-from-word-convert-docx-to-markdown-with/)
- [Save docx as txt – Export Word Math to LaTeX with C#](/words/english/net/programming-with-officemath/save-docx-as-txt-export-word-math-to-latex-with-c/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}