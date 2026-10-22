---
category: general
date: 2026-08-04
description: استعادة ملفات docx التالفة باستخدام وضع الاسترداد في Aspose.Words وتحويل
  ملفات docx إلى markdown مع تصدير المعادلات بصيغة LaTeX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- recover corrupted docx
- convert docx to markdown
- how to use recovery mode
- export equations latex
language: ar
lastmod: 2026-08-04
og_description: استعد ملفات docx التالفة باستخدام وضع الاستعادة في Aspose.Words، ثم
  حوّل ملفات docx إلى markdown مع تصدير المعادلات بصيغة LaTeX. اتبع هذا الدليل خطوة بخطوة
  لإنشاء مخرجات PDF و TXT أيضًا.
og_image_alt: Screenshot of Aspose.Words Python code converting a corrupted docx to
  markdown with LaTeX equations
og_title: استعادة ملف docx التالف وتحويله إلى markdown – دليل Aspose
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Recover corrupted docx files using Aspose.Words recovery mode and convert
    docx to markdown, exporting equations as LaTeX.
  headline: Recover corrupted docx and convert to markdown with Aspose
  type: TechArticle
- description: Recover corrupted docx files using Aspose.Words recovery mode and convert
    docx to markdown, exporting equations as LaTeX.
  name: Recover corrupted docx and convert to markdown with Aspose
  steps:
  - name: Export floating shapes as inline tags
    text: Floating images or text boxes can cause layout issues when converting to
      PDF. Setting `export_floating_shapes_as_inline_tag` forces Aspose.Words to treat
      those shapes as regular inline elements, preserving the visual flow.
  - name: Adjust the shadow of the first shape
    text: You might want to enhance the appearance of a specific shape before saving
      the final PDF. The code below accesses the first `Shape` node, enables its shadow,
      and tweaks visual parameters.
  - name: Expected output
    text: '| File | Description | |------|-------------| | `output.md` | Markdown
      version of the original DOCX. All equations appear as LaTeX (`$...$` or `$$...$$`).
      | | `output.txt` | Plain‑text dump'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document conversion
title: استعادة ملف docx التالف وتحويله إلى markdown باستخدام Aspose
url: /ar/python/document-conversion/recover-corrupted-docx-and-convert-to-markdown-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# استعادة ملف docx التالف وتحويله إلى markdown باستخدام Aspose

إذا كنت بحاجة إلى **استعادة ملفات docx التالفة**، توفر Aspose.Words وضع استعادة مدمج يمكنه إصلاح مستندات Word التالفة تلقائيًا. بمجرد استعادة الملف يمكنك **تحويل docx إلى markdown**، وحتى **تصدير معادلات LaTeX** للاستخدام السلس في المستندات العلمية. يوضح لك هذا الدليل بالضبط كيفية القيام بذلك في Python، بالإضافة إلى بعض الخيارات الإضافية لإخراج PDF والنص العادي.

ستتعلم كيفية:

* تحميل ملف DOCX قد يكون مكسورًا باستخدام وضع الاستعادة.  
* حفظ المستند المستعاد كـ Markdown مع معادلات بصيغة LaTeX.  
* إنشاء نسخة نصية عادية (TXT) تحتوي أيضًا على معادلات LaTeX.  
* تصدير إلى PDF مع وضع علامات على الأشكال العائمة كعناصر داخلية.  
* تعديل ظل شكل معين وإنتاج ملف PDF نهائي.

لا تحتاج إلى أدوات خارجية—فقط مكتبة Aspose.Words المجانية للـ Python.

## المتطلبات المسبقة

| المتطلب | لماذا يهم |
|-------------|----------------|
| Python 3.8+ | مطلوب من قبل Aspose.Words للـ Python |
| حزمة `aspose-words` (`pip install aspose-words`) | توفر مساحة الاسم `aw` المستخدمة في الكود |
| ملف DOCX قد يكون تالفًا (مثال: `corrupted.docx`) | يوضح سير عمل الاستعادة |
| صلاحية كتابة إلى دليل الإخراج | السكريبت يكتب عدة ملفات (`.md`, `.txt`, `.pdf`) |

تأكد من تكوين ترخيص Aspose.Words (تجربة مجانية أو مدفوع) بشكل صحيح إذا تجاوزت حدود التقييم.

## استعادة docx التالف باستخدام Aspose.Words

الخطوة الأولى هي إخبار Aspose.Words بمعاملة ملف الإدخال على أنه قد يكون مكسورًا. يتم ذلك باستخدام `LoadOptions.recovery_mode`.

```python
import aspose.words as aw

# Step 1: Load a possibly corrupted document using recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER   # Enables automatic recovery of damaged files
doc = aw.Document("YOUR_DIRECTORY/corrupted.docx", load_options)
```

**لماذا يعمل هذا:**  
`RecoveryMode.RECOVER` يجبر المحمل على تجاهل الأخطاء الهيكلية ومحاولة إعادة بناء شجرة المستند. إذا كان الملف تالفًا جزئيًا فقط، سيتم استعادة معظم المحتوى—بما في ذلك النصوص، الصور، والمعادلات.

**نصيحة:** إذا كنت تريد فقط التحقق من صحة المستند دون إصلاحه، استخدم `RecoveryMode.NO_RECOVERY`. للاستعادة الكاملة، احتفظ بالإعداد كما هو موضح.

## تحويل docx إلى markdown مع معادلات LaTeX

بمجرد أن يكون المستند في الذاكرة، يمكنك حفظه كـ Markdown. ضبط `office_math_export_mode` إلى `LATEX` يخبر Aspose.Words بتحويل كل معادلة Word إلى سلسلة LaTeX.

```python
# Step 2: Save the document as Markdown while exporting equations in LaTeX format
markdown_save_options = aw.saving.MarkdownSaveOptions()
markdown_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.md", markdown_save_options)
```

الملف الناتج `output.md` سيظهر كملف Markdown عادي، لكن كل معادلة ستظهر ككود LaTeX داخل `$...$` (مضمن) أو `$$...$$` (عرض). هذا ضروري للأدوات اللاحقة مثل Pandoc أو دفاتر Jupyter التي تفهم صيغة LaTeX.

## كيفية استخدام وضع الاستعادة للملفات التالفة

يمكن إعادة استخدام وضع الاستعادة لأي عملية تحميل. فيما يلي نمط مختصر يمكنك نسخه إلى سكريبتات أخرى:

```python
def load_with_recovery(path: str) -> aw.Document:
    opts = aw.loading.LoadOptions()
    opts.recovery_mode = aw.loading.RecoveryMode.RECOVER
    return aw.Document(path, opts)
```

استدعاء `load_with_recovery("myfile.docx")` يُعيد كائن `Document` قد حاول Aspose.Words إصلاحه مسبقًا. هذه الدالة توضح **كيفية استخدام وضع الاستعادة** بأمان عبر المشاريع.

## تصدير معادلات LaTeX عند الحفظ إلى markdown و txt

إذا كنت تحتاج أيضًا إلى نسخة نصية عادية، فإن علم `office_math_export_mode` يعمل مع `TxtSaveOptions`.

```python
# Step 3: Save the same document as plain‑text (TXT) with LaTeX equations
txt_save_options = aw.saving.TxtSaveOptions()
txt_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_save_options)
```

ملف `.txt` يحتوي على النص الخام لمستند Word، وكل معادلة ممثلة ككود LaTeX. هذا التنسيق مفيد للفهرسة أو لتغذية المحتوى إلى محركات بحث تفهم LaTeX.

## خيارات إضافية: PDF مع أشكال داخلية وظل الشكل

### تصدير الأشكال العائمة كعلامات داخلية

الصور أو صناديق النص العائمة قد تتسبب في مشاكل تخطيطية عند التحويل إلى PDF. ضبط `export_floating_shapes_as_inline_tag` يجبر Aspose.Words على معالجة تلك الأشكال كعناصر داخلية عادية، مما يحافظ على تدفق المحتوى البصري.

```python
# Step 4: Export the document to PDF and tag floating shapes as inline elements
pdf_save_options = aw.saving.PdfSaveOptions()
pdf_save_options.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_save_options)
```

### تعديل ظل الشكل الأول

قد ترغب في تحسين مظهر شكل معين قبل حفظ PDF النهائي. الكود أدناه يصل إلى أول عقدة `Shape`، يفعّل الظل، ويضبط بعض المعلمات البصرية.

```python
# Step 5: Adjust the shadow of the first shape and save the result
first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
shape_shadow = first_shape.shadow_format
shape_shadow.visible = True
shape_shadow.blur = 5.0          # Controls shadow softness
shape_shadow.distance = 3.0      # Distance from the shape
shape_shadow.angle = 45          # Direction of the light source
shape_shadow.color = aw.Color.black

doc.save("YOUR_DIRECTORY/shadowed.pdf")
```

**النتيجة:** `shadowed.pdf` يبدو مطابقة لـ `output.pdf` لكن الشكل الأول الآن يضيف ظلًا أسودًا خفيفًا، مما قد يحسن القراءة في العروض التقديمية.

## سكريبت كامل قابل للتنفيذ

فيما يلي السكريبت الكامل الذي يجمع جميع الخطوات. انسخه إلى ملف باسم `recover_and_convert.py`، استبدل `YOUR_DIRECTORY` بمسار فعلي، ثم نفّذ `python recover_and_convert.py`.

```python
import aspose.words as aw

# -------------------------------------------------
# 1. Load the possibly corrupted DOCX using recovery mode
# -------------------------------------------------
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER
doc = aw.Document("YOUR_DIRECTORY/corrupted.docx", load_options)

# -------------------------------------------------
# 2. Save as Markdown with LaTeX equations
# -------------------------------------------------
markdown_save_options = aw.saving.MarkdownSaveOptions()
markdown_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.md", markdown_save_options)

# -------------------------------------------------
# 3. Save as plain‑text (TXT) with LaTeX equations
# -------------------------------------------------
txt_save_options = aw.saving.TxtSaveOptions()
txt_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_save_options)

# -------------------------------------------------
# 4. Export to PDF, converting floating shapes to inline
# -------------------------------------------------
pdf_save_options = aw.saving.PdfSaveOptions()
pdf_save_options.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_save_options)

# -------------------------------------------------
# 5. Add a shadow to the first shape and save a new PDF
# -------------------------------------------------
first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
shape_shadow = first_shape.shadow_format
shape_shadow.visible = True
shape_shadow.blur = 5.0
shape_shadow.distance = 3.0
shape_shadow.angle = 45
shape_shadow.color = aw.Color.black

doc.save("YOUR_DIRECTORY/shadowed.pdf")
```

### المخرجات المتوقعة

| الملف | الوصف |
|------|-------------|
| `output.md` | نسخة Markdown من ملف DOCX الأصلي. جميع المعادلات تظهر كـ LaTeX (`$...$` أو `$$...$$`). |
| `output.txt` | تفريغ نص عادي |

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية استخدام Markdown: تحويل DOCX إلى Markdown مع معادلات LaTeX](/words/english/net/programming-with-markdownsaveoptions/how-to-use-markdown-convert-docx-to-markdown-with-latex-equa/)
- [كيفية استعادة docx باستخدام Aspose.Words – خطوة بخطوة](/words/english/net/programming-with-loadoptions/how-to-recover-docx-with-aspose-words-step-by-step/)
- [استعادة DOCX التالف وتحويل Word إلى Markdown](/words/english/python-net/document-conversion/recover-corrupted-docx-convert-word-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}