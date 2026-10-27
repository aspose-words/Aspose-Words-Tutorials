---
category: general
date: 2026-10-16
description: كيفية تصدير LaTeX من مستند Word باستخدام Aspose.Words. تعلّم تحويل DOCX
  إلى LaTeX، حفظ Word كملف TXT، واستخراج المعادلات في سكريبت واحد.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to export latex
- convert docx to latex
- export word equations latex
- save word as txt
- extract equations latex
language: ar
lastmod: 2026-10-16
og_description: كيفية تصدير LaTeX من مستند Word باستخدام Aspose.Words. يوضح لك هذا
  الدليل كيفية تحويل DOCX إلى LaTeX، وحفظ Word كملف TXT، واستخراج المعادلات بسرعة.
og_image_alt: How to export LaTeX from Word using Aspose.Words
og_title: كيفية تصدير LaTeX من مستندات Word – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: How to export LaTeX from a Word document using Aspose.Words. Learn
    to convert DOCX to LaTeX, save Word as TXT, and extract equations in a single
    script.
  headline: How to export LaTeX from Word documents using Aspose.Words
  type: TechArticle
- description: How to export LaTeX from a Word document using Aspose.Words. Learn
    to convert DOCX to LaTeX, save Word as TXT, and extract equations in a single
    script.
  name: How to export LaTeX from Word documents using Aspose.Words
  steps:
  - name: Load the Word document containing equations
    text: '```python import aspose.words as aw'
  - name: Create TXT save options
    text: '```python txt_opts = aw.saving.TxtSaveOptions() ```'
  - name: Set the export mode for Office Math objects to LaTeX
    text: '```python # Export all Office Math objects as LaTeX markup txt_opts.office_math_export_mode
      = aw.saving.OfficeMathExportMode.LATEX ```'
  - name: Save the document as a plain‑text file using the configured options
    text: '```python # The resulting file will contain regular text plus LaTeX for
      each equation doc.save("YOUR_DIRECTORY/out.txt", txt_opts) ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- LaTeX
- DOCX conversion
- Equation extraction
title: كيفية تصدير LaTeX من مستندات Word باستخدام Aspose.Words
url: /ar/python/document-conversion/how-to-export-latex-from-word-documents-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تصدير LaTeX من مستندات Word باستخدام Aspose.Words

كيفية تصدير LaTeX من مستند Word هي حاجة شائعة عندما تريد إعادة استخدام المحتوى الرياضي في الأوراق العلمية. إذا كنت بحاجة إلى تحويل DOCX إلى LaTeX مع الحفاظ على كائنات Office Math، فإن هذا الدليل يشرح الخطوات الدقيقة باستخدام Aspose.Words للغة Python.

سترى سكريبت كامل قابل للتنفيذ يقوم بتحميل ملف *.docx*، ضبط خيارات الحفظ، وكتابة ملف نصي يحتوي على ترميز LaTeX لكل معادلة. يشرح الدليل أيضًا لماذا كل إعداد مهم، كيفية التعامل مع الحالات الخاصة، وما يمكن توقعه في الناتج.

![How to export LaTeX from Word using Aspose.Words](images/export-latex.png)

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من أن لديك:

* Python 3.8 أو أحدث مثبت.
* رخصة سارية لـ **Aspose.Words for Python via .NET** (الإصدار التجريبي المجاني يعمل للاختبار).
* حزمة `aspose-words` مثبتة:

```bash
pip install aspose-words
```

لا توجد مكتبات طرف ثالث إضافية مطلوبة؛ Aspose.Words يتعامل مع التحويل داخليًا.

## كيفية تصدير LaTeX باستخدام Aspose.Words

جوهر الحل يتكون من أربع عبارات قصيرة. كل واحدة تمثل خطوة منطقية في خط أنابيب التحويل.

### الخطوة 1: تحميل مستند Word الذي يحتوي على المعادلات

```python
import aspose.words as aw

# Replace the path with the location of your source DOCX file
doc = aw.Document("YOUR_DIRECTORY/equations.docx")
```

`aw.Document` يقوم بتحليل حزمة Word بالكامل، بما في ذلك كائنات Office Math. تحميل المستند أولاً يضمن أن كل معادلة متاحة للتصدير لاحقًا.

### الخطوة 2: إنشاء خيارات حفظ TXT

```python
txt_opts = aw.saving.TxtSaveOptions()
```

`TxtSaveOptions` يخبر Aspose.Words بكتابة ناتج نصي عادي. بشكل افتراضي سيزيل المحرك التنسيق، لكننا سنفعل لاحقًا تصدير LaTeX للمعادلات.

### الخطوة 3: ضبط وضع التصدير لكائنات Office Math إلى LaTeX

```python
# Export all Office Math objects as LaTeX markup
txt_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
```

خاصية `office_math_export_mode` تتحكم في كيفية عرض المعادلات. ضبطها إلى `LATEX` يحول كل عنصر MathML إلى ما يعادله في LaTeX، وهو ما تحتاجه لـ **export word equations latex**.

### الخطوة 4: حفظ المستند كملف نصي باستخدام الخيارات المكوَّنة

```python
# The resulting file will contain regular text plus LaTeX for each equation
doc.save("YOUR_DIRECTORY/out.txt", txt_opts)
```

استدعاء `save` يكتب ملف `.txt` يخلط الفقرات العادية مع شظايا LaTeX. هذا يلبي متطلب **save word as txt** مع الحفاظ على جودة ترميز المعادلات.

## تحويل DOCX إلى LaTeX بأقل كود

جمع الخطوات الأربع معًا ينتج سكريبتًا مضغوطًا يقوم بـ **تحويل docx إلى latex** في بضع أسطر فقط:

```python
import aspose.words as aw

def export_docx_to_latex(source_path: str, target_path: str) -> None:
    """
    Loads a DOCX file, exports all Office Math objects as LaTeX,
    and writes the result to a plain‑text file.
    """
    doc = aw.Document(source_path)                     # Load the source
    txt_opts = aw.saving.TxtSaveOptions()              # Prepare TXT options
    txt_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
    doc.save(target_path, txt_opts)                    # Write the output

# Example usage
export_docx_to_latex(
    "YOUR_DIRECTORY/equations.docx",
    "YOUR_DIRECTORY/out.txt"
)
```

تشغيل السكريبت ينتج `out.txt`. مثال نموذجي يبدو هكذا:

```
This is a paragraph introducing the equation.

\[
E = mc^{2}
\]

Another paragraph follows the displayed formula.
```

شظية LaTeX `\[` … `\]` تُولد تلقائيًا لكل كائن Office Math، مما يجعل الملف جاهزًا للإدراج في مستند LaTeX دون معالجة إضافية.

## تصدير معادلات Word LaTeX – معالجة المشكلات الشائعة

بينما يعمل التدفق الأساسي لمعظم المستندات، قد تواجه الحالات التالية:

| الحالة | سبب الأهمية | الإصلاح المقترح |
|-----------|----------------|-----------------|
| **المعادلات داخل الجداول** | تُعامل خلايا الجدول كفقرات منفصلة؛ لا يزال المُصدِّر يعمل، لكن قد يختلف التباعد. | بعد التصدير، تحقق يدويًا من بيئة `\begin{tabular}` المحيطة أو استخدم سكريبت ما بعد المعالجة لتغليف شظايا LaTeX. |
| **اتجاه اللغة المختلط (RTL/LTR)** | Aspose.Words يحترم الاتجاه الأصلي، مما قد يؤثر على عرض LaTeX. | أضف `\usepackage{bidi}` في مقدمة LaTeX إذا كنت تحتاج دعم من اليمين إلى اليسار. |
| **المستندات الكبيرة** | حفظ النص العادي يحمِّل الملف بالكامل في الذاكرة. | استخدم `txt_opts.save_format = aw.SaveFormat.TXT` وعالج الملف على أجزاء إذا كانت الذاكرة محدودة. |
| **الرخصة مفقودة** | النسخة التجريبية تُدرج علامة مائية في الناتج. | طبّق رخصة صالحة قبل استدعاء `aw.Document`. مثال: `aw.License().set_license("Aspose.Words.lic")`. |

معالجة هذه الحالات الطرفية يضمن أن **استخراج المعادلات latex** يعمل بموثوقية عبر ملفات المصدر المختلفة.

## حفظ Word كـ TXT مع الحفاظ على المعادلات – طرق بديلة

إذا كنت تفضل تنسيق إخراج مختلف، يدعم Aspose.Words أيضًا:

* **HTML** – `aw.saving.HtmlSaveOptions` مع `office_math_export_mode = LATEX`.
* **Markdown** – `aw.saving.MarkdownSaveOptions` مع نفس وضع التصدير.

كلا البديلين يحافظان على ترميز LaTeX سليماً، مما يمنحك مرونة لاستخدام تنسيقات شبيهة بـ **save word as txt** تتناسب مع الأدوات اللاحقة.

## استخراج معادلات LaTeX من مستند – سكريبت تحقق سريع

بعد حصولك على `out.txt`، قد ترغب في عزل معادلات LaTeX فقط. المقتطف التالي يوضح استخراجًا بسيطًا باستخدام التعابير النمطية:

```python
import re

def extract_latex_equations(txt_path: str) -> list[str]:
    """
    Returns a list of LaTeX equation strings found in a plain‑text file.
    """
    with open(txt_path, "r", encoding="utf-8") as f:
        content = f.read()
    # Matches LaTeX between \[ and \] or $$...$$
    pattern = r"\\\[(.*?)\\\]|\\\$(.*?)\\\$"
    matches = re.findall(pattern, content, re.DOTALL)
    # Flatten the tuple results and strip whitespace
    equations = [eq.strip() for pair in matches for eq in pair if eq]
    return equations

# Example usage
eqs = extract_latex_equations("YOUR_DIRECTORY/out.txt")
print("Found equations:", len(eqs))
for i, eq in enumerate(eqs, 1):
    print(f"{i}: {eq}")
```

تشغيل هذا السكريبت يطبع كل شظية LaTeX مستخرجة، مؤكدًا أن **export word equations latex** نجح.

## الخلاصة

أنت الآن تعرف **كيفية تصدير LaTeX** من مستند Word باستخدام Aspose.Words، وكيفية **تحويل DOCX إلى LaTeX**، وكيفية **حفظ Word كـ TXT** مع الحفاظ على ترميز المعادلات، وكيفية **استخراج المعادلات LaTeX** للمعالجة الإضافية. المثال الكامل يُظهر تحويلًا موثوقًا بمرور واحد يعمل مع أي ملف Word حديث يحتوي على كائنات Office Math.

من هنا قد تستكشف:

* إنشاء هيكل مشروع LaTeX كامل (المقدمة، `

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف طرق تنفيذ بديلة في مشاريعك الخاصة.

- [حفظ DOCX كـ TXT – تصدير معادلات Word إلى LaTeX](/words/english/net/programming-with-txtsaveoptions/save-docx-as-txt-export-word-equations-to-latex/)
- [تحويل docx إلى txt – تصدير معادلات Word كـ LaTeX](/words/english/net/basic-conversions/convert-docx-to-txt-export-word-equations-as-latex/)
- [كيفية تحويل المعادلات في Word إلى LaTeX – حفظ كـ TXT](/words/english/net/programming-with-officemath/how-to-convert-equations-in-word-to-latex-save-as-txt/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}