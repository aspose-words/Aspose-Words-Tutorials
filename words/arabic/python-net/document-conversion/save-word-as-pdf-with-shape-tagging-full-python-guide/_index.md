---
category: general
date: 2026-05-30
description: احفظ ملف Word كـ PDF مع وضع علامات على الأشكال في بايثون. حوّل ملف docx
  إلى PDF، اجعل الـ PDF قابلاً للوصول، وتعلم كيفية وضع علامات على الأشكال العائمة
  لتحسين إمكانية الوصول.
draft: false
keywords:
- save word as pdf
- convert docx to pdf
- convert word document pdf
- make pdf accessible
- how to tag shapes
language: ar
og_description: احفظ ملف Word كـ PDF باستخدام Python وضع علامات على الأشكال العائمة
  لتسهيل الوصول. تعلم كيفية تحويل docx إلى PDF وجعل PDF سهل الوصول في دقائق.
og_title: حفظ ملف Word كـ PDF مع وضع علامات على الأشكال – دليل Python الكامل
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Save Word as PDF with shape tagging in Python. Convert docx to pdf,
    make pdf accessible, and learn how to tag floating shapes for better accessibility.
  headline: Save Word as PDF with Shape Tagging – Full Python Guide
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for Python via .NET runs on .NET Core, which is cross‑platform.
      Just install the appropriate runtime (`dotnet-sdk-6.0` or later) and the `aspose-words`
      package.
    question: Does this work on Linux?
  - answer: Absolutely. Wrap the `convert_word_to_accessible_pdf` call in a `for`
      loop that iterates over `os.listdir()` and filters for `*.docx`.
    question: Can I batch‑process a folder of .docx files?
  - answer: Iterate over `doc.get_child_nodes(aw.NodeType.SHAPE, True)` and set `shape.title`
      or `shape.alternative_text` before saving.
    question: What if I need to add custom alt text to each shape?
  - answer: 'The inline tagging respects the original layout; however, if you enable
      PDF/A compliance, some visual tweaks (like color profiles) might be applied
      automatically. ## Wrapping Up We’ve just covered how to **save Word as PDF**
      while ensuring that floating shapes are tagged correctly for accessibility.'
    question: Is there a way to keep the original layout exactly the same?
  type: FAQPage
tags:
- Aspose.Words
- PDF conversion
- Python
- Document automation
title: حفظ ملف Word كـ PDF مع وضع علامات على الأشكال – دليل Python الكامل
url: /ar/python/document-conversion/save-word-as-pdf-with-shape-tagging-full-python-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ Word كملف PDF مع وضع العلامات على الأشكال – دليل Python كامل

هل تساءلت يومًا كيف **تحفظ Word كملف PDF** مع الحفاظ على إمكانية الوصول إلى الأشكال العائمة؟ لست الوحيد. في العديد من البيئات ذات المتطلبات الصارمة للامتثال، لا يكفي ملف PDF عادي—قُرّاء الشاشة يحتاجون إلى علامات صحيحة، خاصةً للأشكال التي تحلق فوق النص.

في هذا الدرس سنستعرض مثالًا كاملاً قابلاً للتنفيذ يوضح لك كيفية **convert docx to pdf**، وضبط خيارات PDF بحيث يكون الناتج صحيحًا بصريًا *ومتاحًا*، وأخيرًا وضع العلامات على الأشكال بالطريقة الصحيحة. في النهاية ستحصل على حل بملف واحد يمكنك إدراجه في أي مشروع Python.

## ما ستتعلمه

- تحميل مستند Word يحتوي على أشكال عائمة (صور، مربعات نص، مخططات).  
- استخدام Aspose.Words for Python via .NET لـ **convert Word document pdf** مع وضع علامات مخصصة.  
- تمكين وضع العلامات *inline* حتى يلتزم PDF بمعايير إمكانية الوصول.  
- التحقق من النتيجة ومعالجة المشكلات الشائعة مثل الخطوط المفقودة أو الصور ذات الحجم الكبير.  

لا خدمات خارجية، لا حيل سطر أوامر غامضة—فقط كود Python بسيط وبعض الملاحظات التوضيحية.

## المتطلبات المسبقة

| المتطلب | السبب |
|-------------|--------|
| Python 3.9+ | مطلوب من قبل حزمة Aspose .Words for Python via .NET. |
| `aspose-words` حزمة NuGet مثبتة (via `pip install aspose-words`) | توفر مساحة الاسم `aw` المستخدمة في المثال. |
| ملف `.docx` يحتوي على شكل عائم واحد على الأقل (مثل مربع نص) | يظهر ميزة وضع العلامات. |
| اختياري: مدقق PDF/A‑1a (مثل veraPDF) إذا كنت بحاجة إلى توثيق إمكانية الوصول. | يساعدك على التأكد من أن PDF قابل للوصول فعليًا. |

إذا لم تستخدم Aspose.Words من قبل، فكر فيها كـ “Swiss army knife” لمعالجة المستندات—أكثر قوة من مكتبة `python-docx` المدمجة، خاصةً عندما تحتاج إلى مخرجات PDF مع تحكم دقيق.

## الخطوة 1: تثبيت واستيراد Aspose.Words

أولًا وقبل كل شيء—قم بتثبيت المكتبة واستيراد الفئات اللازمة. هذه الخطوة قصيرة، لكن تخطيها سيجعلك تواجه `ImportError` لاحقًا.

```bash
pip install aspose-words
```

```python
# Step 1: Import the Aspose.Words namespace
import aspose.words as aw
```

> **نصيحة محترف:** إذا كنت تعمل في بيئة افتراضية، فعّلها قبل تشغيل أمر `pip`. سيساعدك ذلك على الحفاظ على نظافة تبعيات المشروع.

## الخطوة 2: تحميل مستند Word الذي يحتوي على أشكال عائمة

الآن نفتح الملف المصدر فعليًا. يقبل مُنشئ `Document` مسارًا أو تدفقًا، لذا يمكنك تمريره أي شيء من ملف محلي إلى كائن S3.

```python
# Step 2: Load the source .docx
input_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(input_path)
```

> **لماذا هذا مهم:** تحميل المستند يمنحنا الوصول إلى شجرة العقد الداخلية، حيث تمثل الأشكال العائمة ككائنات `Shape`. إذا لم يكن الملف موجودًا، سيُطلق Aspose استثناء `FileNotFoundError` يمكنك التقاطه ومعالجته برفق.

## الخطوة 3: تكوين خيارات حفظ PDF لوضع علامات الأشكال القابلة للوصول

هذا هو جوهر الدرس. بشكل افتراضي، يقوم Aspose.Words بحفظ الأشكال العائمة كعلامات *block‑level*، والتي تعالجها العديد من التقنيات المساعدة كعناصر منفصلة غير مرتبة للقراءة. ضبط `export_floating_shapes_as_inline_tag` إلى `True` يجبر الأشكال على أن تُوسم *inline*، مما يحافظ على ترتيب القراءة ويحسن تجربة قارئ الشاشة.

```python
# Step 3: Create PDF save options and enable inline shape tagging
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.export_floating_shapes_as_inline_tag = True   # True → inline (accessible) tagging
```

> **كيف يعمل:** عندما تكون `export_floating_shapes_as_inline_tag` مساوية لـ `True`، يضيف Aspose علامات `<Figure>` حول كل شكل ويضعها في تدفق المستند. هذا هو النهج الموصى به للامتثال **make pdf accessible**، خاصةً وفقًا لتوجيه WCAG 2.1 Guideline 1.3.1.

### تعديلات اختيارية

| الخيار | الوصف | القيمة النموذجية |
|--------|-------|-------------------|
| `pdf_opts.compliance` | يضبط مستوى الامتثال PDF/A (مثال: PDF/A‑1a). | `aw.saving.PdfCompliance.PDF_A_1A` |
| `pdf_opts.embed_full_fonts` | يضمّن جميع الخطوط المستخدمة لتجنب الاستبدال. | `True` |
| `pdf_opts.save_format` | يفرض تنسيق الإخراج (مفيد إذا قمت بالتبديل لاحقًا إلى XPS). | `aw.SaveFormat.PDF` |

يمكنك ربط هذه الإعدادات إذا كان مشروعك يتطلب معايير أكثر صرامة.

## الخطوة 4: حفظ المستند كملف PDF باستخدام الخيارات المكوّنة

أخيرًا، نكتب ملف الإخراج. طريقة `save` تأخذ مسار الوجهة وكائن الخيارات الذي قمنا بتهيئته للتو.

```python
# Step 4: Save the document as a PDF with the accessible tagging options
output_path = "YOUR_DIRECTORY/output.pdf"
doc.save(output_path, pdf_opts)
print(f"✅ PDF saved to {output_path}")
```

هذا كل شيء—عملية **convert word document pdf** الخاصة بك اكتملت. سيحتوي PDF الناتج على الأشكال العائمة موسومة inline، مما يجعله أكثر صداقة للتقنيات المساعدة.

## التحقق من PDF القابل للوصول

إذا أردت التأكد تمامًا من أن PDF يلتزم بمعايير إمكانية الوصول، افتحه في Adobe Acrobat Pro وتفقد لوحة **Tags**. يجب أن ترى إدخالات مثل:

```
/Figure
  /Alt (optional alt text you may have set)
  /Para
```

بدلاً من ذلك، شغّل مدقق سطر الأوامر:

```bash
verapdf --format text output.pdf
```

إذا أعاد المدقق “No errors”، فقد نجحت في **make pdf accessible**.

## حالات الحافة الشائعة وكيفية التعامل معها

| الحالة | ما قد يحدث خطأً | الحل المقترح |
|-----------|---------------------|---------------|
| المستند يحتوي على العديد من الصور عالية الدقة | حجم PDF ينتفخ، الأداء يتدهور. | اضبط `pdf_opts.jpeg_quality = 80` أو قلل حجم الصور باستخدام `doc.get_child_nodes(aw.NodeType.SHAPE, True)` قبل الحفظ. |
| الخطوط مفقودة على الخادم | النص يظهر بخطوط بديلة، مما يكسر التخطيط. | فعّل `pdf_opts.embed_full_fonts = True` وتأكد من تثبيت الخطوط المطلوبة على نظام التشغيل المضيف. |
| الأشكال لا تحتوي على نص بديل | أدوات الوصول تقرأ “Figure” بدون وصف. | قم بالتكرار على الأشكال وتعيين `shape.title = "Description"` قبل الحفظ. |
| مستندات كبيرة (>100 MB) | أخطاء نفاد الذاكرة على بيئات 32‑bit. | استخدم `PdfSaveOptions.memory_usage_setting = aw.saving.MemoryUsageSetting.LOW` لتدفق المحتوى. |
| تحتاج إلى PDF/A‑2b بدلاً من PDF/A‑1a | عدم توافق الامتثال. | اضبط `pdf_opts.compliance = aw.saving.PdfCompliance.PDF_A_2B`. |

معالجة هذه السيناريوهات مبكرًا توفر عليك إعادة العمل على التحويل لاحقًا.

## مثال كامل يعمل

فيما يلي النص الكامل للسكريبت الذي يمكنك نسخه ولصقه في ملف باسم `convert_to_accessible_pdf.py`. فقط استبدل `YOUR_DIRECTORY` بالمسارات الفعلية للمجلدات.

```python
import aspose.words as aw

def convert_word_to_accessible_pdf(input_docx: str, output_pdf: str) -> None:
    """
    Loads a Word document, configures PDF save options to tag floating shapes inline,
    and saves the result as an accessible PDF.
    """
    # Load the .docx file
    doc = aw.Document(input_docx)

    # Configure PDF options for accessible shape tagging
    pdf_opts = aw.saving.PdfSaveOptions()
    pdf_opts.export_floating_shapes_as_inline_tag = True   # Inline tagging for accessibility
    pdf_opts.compliance = aw.saving.PdfCompliance.PDF_A_1A  # Optional: enforce PDF/A‑1a
    pdf_opts.embed_full_fonts = True                       # Ensure fonts are embedded

    # Save the PDF
    doc.save(output_pdf, pdf_opts)
    print(f"✅ Successfully saved accessible PDF to: {output_pdf}")

if __name__ == "__main__":
    # Adjust these paths as needed
    INPUT_PATH = "YOUR_DIRECTORY/input.docx"
    OUTPUT_PATH = "YOUR_DIRECTORY/output.pdf"

    convert_word_to_accessible_pdf(INPUT_PATH, OUTPUT_PATH)
```

تشغيل السكريبت:

```bash
python convert_to_accessible_pdf.py
```

ستظهر لك رسالة التأكيد، وسيحتوي `output.pdf` على أشكال موسومة inline جاهزة لقُرّاء الشاشة.

## الأسئلة المتكررة

**س: هل يعمل هذا على Linux؟**  
ج: نعم. يعمل Aspose.Words for Python via .NET على .NET Core، وهو متعدد المنصات. فقط قم بتثبيت البيئة المناسبة (`dotnet-sdk-6.0` أو أحدث) وحزمة `aspose-words`.

**س: هل يمكنني معالجة مجموعة من ملفات .docx دفعيًا؟**  
ج: بالتأكيد. غلف استدعاء `convert_word_to_accessible_pdf` داخل حلقة `for` تتنقل عبر `os.listdir()` وتفلتر ملفات `*.docx`.

**س: ماذا لو أردت إضافة نص بديل مخصص لكل شكل؟**  
ج: قم بالتكرار على `doc.get_child_nodes(aw.NodeType.SHAPE, True)` واضبط `shape.title` أو `shape.alternative_text` قبل الحفظ.

**س: هل هناك طريقة للحفاظ على التخطيط الأصلي تمامًا؟**  
ج: وضع العلامات inline يحافظ على التخطيط الأصلي؛ ومع ذلك، إذا فعّلت امتثال PDF/A، قد تُطبق بعض التعديلات البصرية (مثل ملفات تعريف الألوان) تلقائيًا.

## الخاتمة

لقد غطينا للتو كيفية **حفظ Word كملف PDF** مع ضمان أن الأشكال العائمة موسومة بشكل صحيح لتكون قابلة للوصول. الخطوات—التحميل، التكوين، الحفظ—

## ما الذي يجب أن تتعلمه بعد ذلك؟

- [إنشاء PDF قابل للوصول من Word – التحويل إلى PDF/UA](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-word-convert-to-pdf-ua/)
- [حفظ Word كملف PDF باستخدام Aspose.Words – دليل C# كامل](/words/english/net/basic-conversions/save-word-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}