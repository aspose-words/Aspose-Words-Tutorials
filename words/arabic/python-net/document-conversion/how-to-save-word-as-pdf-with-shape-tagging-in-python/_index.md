---
category: general
date: 2026-11-15
description: احفظ مستند Word كملف PDF باستخدام Python و Aspose.Words، وتعلم كيفية
  تصدير الأشكال وتعليم الأشكال العائمة كـ inline للحصول على تحويل دقيق من docx إلى
  PDF.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word as pdf
- convert docx to pdf
- how to export shapes
- how to convert docx
- how to tag shapes
language: ar
lastmod: 2026-11-15
og_description: احفظ مستند Word كملف PDF باستخدام بايثون و Aspose.Words. يوضح هذا
  الدليل كيفية تصدير الأشكال، وتوسيم الأشكال العائمة كضمنية، وتحويل ملفات docx إلى
  PDF بشكل موثوق.
og_image_alt: Screenshot of Python code that saves a Word document as PDF with shape
  tagging
og_title: حفظ مستند Word كملف PDF مع وضع علامات على الأشكال في Python – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Save Word as PDF in Python using Aspose.Words, learn how to export
    shapes and tag floating shapes as inline for accurate docx to PDF conversion.
  headline: How to save Word as PDF with shape tagging in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF conversion
title: كيفية حفظ ملف Word كـ PDF مع وضع وسوم للأشكال في بايثون
url: /ar/python/document-conversion/how-to-save-word-as-pdf-with-shape-tagging-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية حفظ Word كملف PDF مع وضع العلامات على الأشكال في Python

إذا كنت بحاجة إلى **حفظ Word كملف PDF** والحفاظ على كل رسم في مكانه بالضبط، يوضح لك هذا الدليل طريقة موثوقة للقيام بذلك باستخدام Aspose.Words for Python. ستتعلم أيضًا **كيفية تصدير الأشكال** و**كيفية وضع العلامات على الأشكال** بحيث تتحول الكائنات العائمة إلى عناصر مضمنة أثناء التحويل.

في هذا الدرس نغطي:

* تحويل ملف DOCX إلى PDF (`convert docx to pdf`)  
* تصدير الأشكال العائمة كعلامات مضمنة (`how to export shapes`)  
* وضع العلامات على الأشكال أثناء عملية حفظ PDF (`how to tag shapes`)  

لا تحتاج إلى أدوات خارجية—فقط بضع أسطر من كود Python.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من أن لديك:

* تثبيت Python 3.8+  
* رخصة نشطة لـ Aspose.Words for Python (أو نسخة تجريبية مجانية)  
* حزمة `aspose-words` مثبتة (`pip install aspose-words`)  
* ملف DOCX (`input.docx`) يحتوي على أشكال عائمة (صور، مربعات نص، إلخ)

## الخطوة 1: تثبيت واستيراد Aspose.Words

أولاً، أضف المكتبة إلى بيئتك واستوردها في السكريبت الخاص بك.

```python
# Install the package (run once):
# pip install aspose-words

import aspose.words as aw
```

*لماذا؟* يوفر وحدة `aspose.words` الفئة `Document` و `PdfSaveOptions` التي نحتاجها للتحكم في معالجة الأشكال.

## الخطوة 2: تحميل مستند Word

استخدم مُنشئ `Document` لقراءة ملف المصدر.

```python
# Load the Word document you want to convert
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

إذا لم يكن الملف موجودًا، تقوم Aspose.Words بإثارة استثناء `FileNotFoundError`. غلف الاستدعاء داخل كتلة `try/except` للاستخدام في بيئة الإنتاج.

## الخطوة 3: تكوين خيارات حفظ PDF – تصدير ووضع العلامات على الأشكال

المفتاح لتحويل نظيف هو كائن `PdfSaveOptions`. ضبط `export_floating_shapes_as_inline_tag` إلى `True` يُخبر المحرك بمعاملة الرسومات العائمة كعناصر مضمنة، مما يلغي تحولات التخطيط في ملف PDF الناتج.

```python
# Create PDF save options and enable inline tagging for floating shapes
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.export_floating_shapes_as_inline_tag = True  # how to tag shapes
```

*لماذا؟* عندما تكون `export_floating_shapes_as_inline_tag` مساوية لـ `False` (الإعداد الافتراضي)، تحتفظ الأشكال العائمة ببيانات الموقع الأصلية، مما قد يتسبب في ظهورها في مواضع خاطئة في ملف PDF. تمكين العلامة المضمنة يجبر Aspose.Words على تضمين علامة XML صغيرة يفسرها مُعالج PDF ككائن مضمن، مما يحافظ على الدقة البصرية.

## الخطوة 4: حفظ المستند كملف PDF

الآن احفظ ملف PDF باستخدام الخيارات المُكوَّنة.

```python
# Save the document as a PDF, applying the shape‑tagging options
output_path = "YOUR_DIRECTORY/output.pdf"
doc.save(output_path, pdf_opts)

print(f"PDF saved to {output_path}")
```

بعد التنفيذ، يحتوي `output.pdf` على تخطيط Word الأصلي مع جميع الأشكال العائمة مُعالجة بشكل صحيح كعناصر مضمنة.

## الخطوة 5: التحقق من التحويل (اختياري)

يمكنك التحقق برمجياً من أن ملف PDF تم إنشاؤه ويحتوي على صفحة واحدة على الأقل:

```python
import os
from aspose.pdf import Document as PdfDocument

if os.path.exists(output_path):
    pdf_doc = PdfDocument(output_path)
    print(f"PDF has {pdf_doc.pages.count} page(s).")
else:
    raise FileNotFoundError("PDF was not created.")
```

*نصيحة:* استخدم عارض PDF للتحقق مرة أخرى من أن الصور، ومربعات النص، والشرح تظهر تمامًا في المواضع التي كانت عليها في ملف DOCX.

## الاختلافات الشائعة وحالات الحافة

| الحالة | ما الذي يجب تغييره |
|-----------|----------------|
| **تحتاج إلى إبقاء الأشكال العائمة عائمة** | اضبط `pdf_opts.export_floating_shapes_as_inline_tag = False`. |
| **تحويل عدة ملفات دفعة واحدة** | قم بالتكرار عبر قائمة من مسارات الملفات وأعد استخدام كائن `PdfSaveOptions` واحد. |
| **تريد تضمين كلمة مرور** | استخدم `pdf_opts.encrypt_options.password = "your‑password"` قبل استدعاء `save`. |
| **المستندات الكبيرة تسبب ضغطًا على الذاكرة** | فعّل `pdf_opts.memory_optimization = True` لتقليل استهلاك الذاكرة. |

## نصيحة احترافية: التعامل مع الخطوط المفقودة

إذا كان ملف DOCX المصدر يستخدم خطوطًا غير مثبتة على الخادم، قد يلجأ عرض PDF إلى الخط الافتراضي. سجِّل الخطوط المفقودة باستخدام `FontSettings`:

```python
font_settings = aw.FontSettings()
font_settings.set_fonts_folder("YOUR_DIRECTORY/fonts", recursive=True)
doc.font_settings = font_settings
```

هذا يضمن أن يبدو ملف PDF مطابقًا للملف Word الأصلي.

## مثال كامل قابل للتنفيذ

```python
import aspose.words as aw
import os

def convert_docx_to_pdf(input_path: str, output_path: str) -> None:
    """
    Saves a Word document as PDF while tagging floating shapes as inline.
    """
    # Load the DOCX
    doc = aw.Document(input_path)

    # Optional: register custom fonts
    # font_settings = aw.FontSettings()
    # font_settings.set_fonts_folder("fonts", recursive=True)
    # doc.font_settings = font_settings

    # Configure PDF options to export shapes as inline tags
    pdf_opts = aw.saving.PdfSaveOptions()
    pdf_opts.export_floating_shapes_as_inline_tag = True  # how to tag shapes

    # Save as PDF
    doc.save(output_path, pdf_opts)
    print(f"PDF saved to {output_path}")

if __name__ == "__main__":
    INPUT = "YOUR_DIRECTORY/input.docx"
    OUTPUT = "YOUR_DIRECTORY/output.pdf"

    if not os.path.isfile(INPUT):
        raise FileNotFoundError(f"Input file not found: {INPUT}")

    convert_docx_to_pdf(INPUT, OUTPUT)

    # Verify creation
    if os.path.isfile(OUTPUT):
        from aspose.pdf import Document as PdfDocument
        pdf = PdfDocument(OUTPUT)
        print(f"Conversion successful – PDF has {pdf.pages.count} page(s).")
    else:
        raise RuntimeError("PDF conversion failed.")
```

تشغيل السكريبت ينتج `output.pdf` مع جميع الأشكال العائمة مُعلمة بشكل صحيح، مما يمنحك نتيجة **save word as pdf** نظيفة.

## الخلاصة

أنت الآن تعرف كيفية **حفظ Word كملف PDF** في Python مع التحكم في معالجة الأشكال. من خلال ضبط `PdfSaveOptions.export_floating_shapes_as_inline_tag`، يمكنك بثقة **تحويل docx إلى pdf**، **تصدير الأشكال** كعلامات مضمنة، والإجابة على **كيفية وضع العلامات على الأشكال** أثناء التحويل.  

من هنا قد ترغب في استكشاف:

* إضافة علامات مائية (`pdf_opts.add_watermark`) – امتداد طبيعي لتخصيص PDF.  
* تحويل صيغ أخرى (HTML، EPUB) باستخدام نمط `save` نفسه.  
* أتمتة التحويلات الدفعية لمستودعات المستندات الكبيرة.

جرّب السكريبت، جرب الإعدادات الاختيارية، ودمجه في خط أنابيب معالجة المستندات اليوم. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [حفظ Word كملف PDF – تحويل الأشكال إلى مضمنة باستخدام Aspose.Words](/words/english/python-net/document-conversion/save-word-as-pdf-convert-shapes-to-inline-with-aspose-words/)
- [كيفية حفظ Word كملف PDF باستخدام Aspose.Words for Python](/words/english/python-net/document-conversion/how-to-save-word-as-pdf-with-aspose-words-for-python/)
- [كيفية تحويل DOCX إلى PDF في Python باستخدام Aspose.Words](/words/english/python-net/document-conversion/how-to-convert-docx-to-pdf-in-python-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}