---
category: general
date: 2026-10-26
description: كيفية تصدير ماركداون من ملف DOCX باستخدام Aspose.Words للبايثون. تعلم
  تحويل docx إلى ماركداون، تحويل المعادلات إلى LaTeX، حفظ المستند كملف txt، وكيفية
  حفظه كملف pdf.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to export markdown
- convert docx to markdown
- convert equations to latex
- save document as txt
- how to save pdf
language: ar
lastmod: 2026-10-26
og_description: كيفية تصدير ماركداون من ملف DOCX باستخدام Aspose.Words للبايثون. يوضح
  هذا الدليل كيفية تحويل ملف docx إلى ماركداون، وتصدير المعادلات إلى LaTeX، وحفظ المستند
  كملف txt، وكيفية حفظه كملف pdf.
og_image_alt: Screenshot showing DOCX converted to markdown with equations rendered
  as LaTeX
og_title: كيفية تصدير ماركداون من ملف DOCX – دليل بايثون كامل
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: How to export markdown from a DOCX file with Aspose.Words for Python.
    Learn to convert docx to markdown, convert equations to LaTeX, save document as
    txt, and how to save pdf.
  headline: How to export markdown from a DOCX using Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- document conversion
title: كيفية تصدير ماركداون من ملف DOCX باستخدام Aspose.Words للبايثون
url: /ar/python/document-conversion/how-to-export-markdown-from-a-docx-using-aspose-words-for-py/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تصدير markdown من ملف DOCX باستخدام Aspose.Words للغة Python

إذا كنت بحاجة إلى **how to export markdown** من مستند Word، فإن هذا الدليل يوفر حلاً جاهزًا للتنفيذ. سترى كيف تقوم **convert docx to markdown**، وكيف تقوم **convert equations to LaTeX**، وكيف **save document as txt**، و**how to save pdf** – كل ذلك باستخدام سكريبت واحد من Aspose.Words للغة Python.

يستعرض الدليل كل كائن خيار، ويشرح لماذا كل إعداد مهم، ويظهر الكود الدقيق الذي يمكنك لصقه في مشروعك. لا تحتاج إلى مراجع خارجية؛ فقط مكتبة Aspose.Words للغة Python وملف DOCX للاختبار.

## المتطلبات المسبقة

* Python 3.8+ مثبت  
* حزمة `aspose-words` (`pip install aspose-words`)  
* ملف DOCX (مسمى `input.docx` في الأمثلة)  
* صلاحية كتابة إلى دليل الإخراج  

هذه المتطلبات تضمن تشغيل السكريبت دون أخطاء في الصلاحيات أو الاعتمادات.

## الخطوة 1: تحميل ملف DOCX في وضع الاستعادة  

تحميل ملف قد يكون تالفًا في **recovery mode** يمنع استثناءات وقت التشغيل ويسمح لـ Aspose.Words بمحاولة إصلاح المستند.

```python
import aspose.words as aw

# LoadOptions enables recovery mode to handle corrupted input files
load_opts = aw.loading.LoadOptions()
load_opts.recovery_mode = aw.loading.RecoveryMode.RECOVER

# The Document object represents the entire Word file
doc = aw.Document("YOUR_DIRECTORY/input.docx", load_opts)
```

*لماذا وضع الاستعادة؟*  
عندما يحتوي ملف DOCX على أجزاء مكسورة (مثل العلاقات المفقودة)، فإن `RecoveryMode.RECOVER` يخبر المكتبة بتجاهل تلك الأخطاء ولا يزال ينتج كائن `Document` قابل للاستخدام. هذا مفيد بشكل خاص في خطوط الأنابيب الآلية حيث لا يمكنك فحص كل ملف يدويًا.

## الخطوة 2: تصدير إلى Markdown وتحويل المعادلات إلى LaTeX  

Markdown هي لغة توصيف خفيفة الوزن، لكن معادلات Word تحتاج إلى تمثيل خاص. ضبط `office_math_export_mode` إلى `LATEX` يجعل Aspose.Words يعرض كل معادلة كمقتطف LaTeX داخل ملف Markdown.

```python
# MarkdownSaveOptions controls how the document is written as .md
md_opts = aw.saving.MarkdownSaveOptions()
md_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX

# Save the document as Markdown
doc.save("YOUR_DIRECTORY/output.md", md_opts)
```

**Result:** الملف `output.md` المُولد يحتوي على نص عادي، عناوين، وأي معادلات Office Math محاطة بـ `$…$` أو `$$…$$` كفواصل LaTeX، جاهزة لمعالجات LaTeX اللاحقة أو مولدات المواقع الثابتة.

## الخطوة 3: حفظ كملف نص عادي مع الاستمرار في تحويل المعادلات إلى LaTeX  

إذا كنت تحتاج فقط إلى نسخة النص الخام من المستند، فإن `TxtSaveOptions` يقوم بالمهمة. علم `office_math_export_mode` نفسه يضمن ظهور المعادلات كـ LaTeX في ملف `.txt`.

```python
txt_opts = aw.saving.TxtSaveOptions()
txt_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX

doc.save("YOUR_DIRECTORY/output.txt", txt_opts)
```

*نصيحة:* إخراج النص العادي مثالي لخطوط أنابيب فهرسة البحث لأنه يزيل كل التنسيق مع الحفاظ على المحتوى الرياضي بشكل قابل للتحليل.

## الخطوة 4: إنشاء PDF ووضع علامة على الأشكال العائمة كعناصر داخلية  

عند التحويل إلى PDF، يمكن أن تتسبب الأشكال العائمة (مثل الصور المثبتة إلى فقرة) في تغيرات التخطيط. تمكين `export_floating_shapes_as_inline_tag` يجبر تلك الأشكال على أن تُعامل كعناصر داخلية، مما ينتج غالبًا تخطيط PDF أكثر توقعًا.

```python
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.export_floating_shapes_as_inline_tag = True

doc.save("YOUR_DIRECTORY/output.pdf", pdf_opts)
```

**لماذا هذا مهم:** بعض عارضات PDF تفسر الأشكال العائمة بشكل مختلف، مما يؤدي إلى صور غير موضوعة بشكل صحيح. وضع علامة عليها كعناصر داخلية يضمن أن ترتيب العناصر البصرية يطابق مستند Word الأصلي.

## البرنامج الكامل – نسخ، لصق، وتشغيل  

فيما يلي البرنامج الكامل القابل للتنفيذ الذي يجمع بين الخطوات الأربع. استبدل `YOUR_DIRECTORY` بمسار المجلد الفعلي على جهازك.

```python
import aspose.words as aw

# -------------------------------------------------
# 1. Load the DOCX with recovery mode
# -------------------------------------------------
load_opts = aw.loading.LoadOptions()
load_opts.recovery_mode = aw.loading.RecoveryMode.RECOVER
doc = aw.Document("YOUR_DIRECTORY/input.docx", load_opts)

# -------------------------------------------------
# 2. Export to Markdown (equations → LaTeX)
# -------------------------------------------------
md_opts = aw.saving.MarkdownSaveOptions()
md_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.md", md_opts)

# -------------------------------------------------
# 3. Export to plain text (equations → LaTeX)
# -------------------------------------------------
txt_opts = aw.saving.TxtSaveOptions()
txt_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_opts)

# -------------------------------------------------
# 4. Export to PDF (floating shapes → inline)
# -------------------------------------------------
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_opts)
```

### النتيجة المتوقعة

| الملف | الوصف |
|------|-------------|
| `output.md` | الإصدار Markdown من ملف DOCX، مع جميع معادلات Office Math مُعروضة كـ LaTeX (`$…$`). |
| `output.txt` | نسخة نص عادي، تحتوي أيضًا على معادلات LaTeX. |
| `output.pdf` | ملف PDF حيث تُجبر الأشكال العائمة على أن تكون داخلية، مما يحافظ على دقة التخطيط. |

## التغييرات الشائعة ومعالجة الحالات الطرفية  

| الحالة | التعديل |
|-----------|------------|
| **تحتاج إلى HTML بدلاً من Markdown** | استخدم `aw.saving.HtmlSaveOptions()` واضبط `office_math_export_mode` بالمثل. |
| **حافظ على موضع الصورة الأصلي في PDF** | عيّن `pdf_opts.export_floating_shapes_as_inline_tag = False`. |
| **المستندات الكبيرة تسبب ضغطًا على الذاكرة** | حمّل الملف باستخدام `LoadOptions.memory_optimization = True`. |
| **تريد فقط تصدير قسم واحد** | استخدم `doc.select_nodes("//w:sectPr")` لعزل القسم قبل الحفظ. |

## نصيحة احترافية: معالجة دفعة من ملفات DOCX المتعددة  

إذا كان لديك مجلد مليء بملفات Word، غلف السكريبت في حلقة بسيطة:

```python
import os, aspose.words as aw

input_folder = "YOUR_DIRECTORY/docs"
output_folder = "YOUR_DIRECTORY/converted"

for filename in os.listdir(input_folder):
    if filename.lower().endswith(".docx"):
        path = os.path.join(input_folder, filename)
        doc = aw.Document(path, aw.loading.LoadOptions(recovery_mode=aw.loading.RecoveryMode.RECOVER))

        base = os.path.splitext(filename)[0]

        # Markdown
        md_opts = aw.saving.MarkdownSaveOptions()
        md_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
        doc.save(os.path.join(output_folder, f"{base}.md"), md_opts)

        # Text
        txt_opts = aw.saving.TxtSaveOptions()
        txt_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
        doc.save(os.path.join(output_folder, f"{base}.txt"), txt_opts)

        # PDF
        pdf_opts = aw.saving.PdfSaveOptions()
        pdf_opts.export_floating_shapes_as_inline_tag = True
        doc.save(os.path.join(output_folder, f"{base}.pdf"), pdf_opts)
```

هذا النمط يوسع خطوات **how to export markdown**، **convert docx to markdown**، **convert equations to latex**، **save document as txt**، و**how to save pdf** عبر أي عدد من الملفات مع أقل تغييرات في الكود.

## الخلاصة

أنت الآن تعرف **how to export markdown** من ملف DOCX باستخدام Aspose.Words للغة Python، وكيفية **convert docx to markdown**، وكيفية **convert equations to LaTeX**، وكيفية **save document as txt**، و**how to save pdf** مع خيارات وضع العلامات على الأشكال. يوضح البرنامج الكامل سير عمل جاهز للإنتاج، وتساعد النصائح الإضافية في تكييف الحل لإخراج HTML، أو بيئات محدودة الذاكرة، أو سيناريوهات المعالجة الدفعية.

هل أنت مستعد لدمج هذا في خط أنابيب معالجة المستندات الخاص بك؟ جرّب تغيير مسارات الإخراج، واختبر فئات `SaveOptions` الأخرى، واستكشف مجموعة الميزات الغنية في Aspose.Words لمزيد من صيغ التحويل. برمجة سعيدة!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية حفظ docx كـ markdown مع LaTeX باستخدام Aspose.Words](/words/english/python-net/document-conversion/how-to-save-docx-as-markdown-with-latex-using-aspose-words/)
- [كيفية تصدير LaTeX من Word – تحويل DOCX إلى Markdown](/words/english/python-net/document-conversion/how-to-export-latex-from-word-convert-docx-to-markdown/)
- [كيفية حفظ PDF وتحويل DOCX إلى Markdown](/words/english/python-net/document-conversion/how-to-save-pdf-and-convert-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}