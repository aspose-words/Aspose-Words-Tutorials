---
category: general
date: 2025-12-18
description: احفظ مستند Word كملف PDF بسرعة باستخدام Aspose.Words للغة Python. تعلم
  كيفية تحويل Word إلى PDF، وتصدير الأشكال العائمة، ومعالجة تحويل ملفات docx في سكريبت
  واحد.
draft: false
keywords:
- save word as pdf
- convert word to pdf
- how to convert docx
- how to export shapes
- python word to pdf conversion
language: ar
og_description: احفظ مستند Word كملف PDF فورًا. يوضح هذا الدليل كيفية تحويل DOCX،
  وتصدير الأشكال، وإجراء تحويل Word إلى PDF باستخدام بايثون مع Aspose.Words.
og_title: حفظ Word كملف PDF – دورة بايثون كاملة
tags:
- Aspose.Words
- PDF conversion
- Python
title: حفظ مستند Word كملف PDF باستخدام Python – دليل كامل لتصدير الأشكال وتحويل DOCX
url: /arabic/python/document-operations/save-word-as-pdf-with-python-full-guide-to-export-shapes-and/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ Word كـ PDF – دليل Python كامل

هل تساءلت يومًا كيف **save Word as PDF** دون فتح Microsoft Word؟ ربما تقوم بأتمتة خط أنابيب تقارير أو تحتاج إلى معالجة دفعة من العشرات من العقود. الخبر السار هو أنك لست مضطرًا لتحديق في الواجهة—Aspose.Words for Python يمكنه القيام بالعمل الشاق في بضع أسطر من الشيفرة.

في هذا الدليل ستتعرف بالضبط على كيفية **convert Word to PDF**، وتصدير الأشكال العائمة كوسوم مضمنة، ومعالجة المشكلة الشائعة “كيفية تصدير الأشكال”. بنهاية الدليل ستحصل على سكريبت جاهز للتنفيذ يحول أي ملف `.docx` إلى PDF نظيف، حتى عندما يحتوي الملف الأصلي على صور أو مربعات نصية أو WordArt.

---

![مخطط يوضح سير عمل حفظ word كـ pdf – تحميل docx، ضبط خيارات PDF، تصدير إلى PDF](image.png)

## ما ستحتاجه

- **Python 3.8+** – أي نسخة حديثة تعمل؛ اختبرنا على 3.11.
- **Aspose.Words for Python via .NET** – تثبيت باستخدام `pip install aspose-words`.
- ملف **input.docx** تجريبي يحتوي على شكل عائم واحد على الأقل (مثل صورة أو مربع نص).  
- إلمام أساسي بسكريبتات Python (لا يلزم معرفة متقدمة).

هذا كل شيء. لا حاجة لتثبيت Office، ولا لتفاعل COM، فقط شفرة صافية.

## الخطوة 1: تحميل مستند Word المصدر

أولاً، علينا تحميل ملف `.docx` إلى الذاكرة. Aspose.Words يتعامل مع المستند كرسمة كائنات، بحيث يمكنك تعديلها قبل الحفظ.

```python
import aspose.words as aw

# Step 1 – Load the source Word document
# Replace "YOUR_DIRECTORY/input.docx" with the actual path to your file.
document = aw.Document("YOUR_DIRECTORY/input.docx")
```

*لماذا هذا مهم:* تحميل المستند يمنحك الوصول إلى كل عقدة—الفقرات، الجداول، والأهم بالنسبة لنا، **floating shapes**. إذا تخطيت هذه الخطوة، لن تتاح لك فرصة تعديل طريقة عرض تلك الأشكال في PDF.

## الخطوة 2: تكوين خيارات حفظ PDF – تصدير الأشكال العائمة كوسوم مضمنة

بشكل افتراضي، Aspose.Words يحاول الحفاظ على التخطيط الدقيق للأجسام العائمة، مما قد يسبب أحيانًا تغيرات في التخطيط داخل PDF. ضبط `export_floating_shapes_as_inline_tag` يجبر تلك الأجسام على أن تُعامل كعناصر مضمنة، مما ينتج نتيجة أكثر توقعًا.

```python
# Step 2 – Configure PDF save options
pdf_save_options = aw.saving.PdfSaveOptions()
pdf_save_options.export_floating_shapes_as_inline_tag = True
```

*لماذا هذا مهم:* إذا كنت تسأل **how to export shapes** من ملف Word، فهذا العلم هو الجواب. إنه يطلب من المحرك تغليف كل شكل عائم بوسم `<span>` مخفي، والذي يعامله مُولِّد PDF كجزء من تدفق النص العادي. النتيجة؟ لا صور معزولة تطفو خارج الصفحة.

### متى قد ترغب في الاحتفاظ بالإعداد الافتراضي؟

- إذا كان المستند يعتمد على تموضع دقيق (مثل تخطيط كتيب)، اترك العلم `False`.
- بالنسبة لمعظم تقارير الأعمال، الفواتير، أو العقود، ضبطه إلى `True` يزيل المفاجآت.

## الخطوة 3: حفظ المستند كملف PDF

الآن بعد ضبط الخيارات، يمكننا أخيرًا **save Word as PDF**. طريقة `save` تأخذ مسار الإخراج وكائن الخيارات الذي قمنا بتكوينه.

```python
# Step 3 – Save the document as a PDF using the configured options
# Replace "YOUR_DIRECTORY/output.pdf" with your desired output location.
document.save("YOUR_DIRECTORY/output.pdf", pdf_save_options)
```

عند انتهاء السكريبت، تحقق من `output.pdf`. يجب أن ترى النص الأصلي، الجداول، وأي أشكال عائمة تم عرضها مضمنة—تمامًا ما تتوقعه من تحويل نظيف.

## سكريبت كامل وجاهز للتنفيذ

بجمع كل ذلك معًا، إليك المثال الكامل الذي يمكنك نسخه‑ولصقه في ملف اسمه `convert_docx_to_pdf.py`:

```python
import aspose.words as aw

def convert_docx_to_pdf(input_path: str, output_path: str) -> None:
    """
    Convert a DOCX file to PDF while exporting floating shapes as inline tags.
    
    Parameters
    ----------
    input_path : str
        Full path to the source .docx file.
    output_path : str
        Desired path for the generated PDF.
    """
    # Load the Word document
    document = aw.Document(input_path)

    # Set PDF options – export floating shapes as inline tags
    pdf_options = aw.saving.PdfSaveOptions()
    pdf_options.export_floating_shapes_as_inline_tag = True

    # Save as PDF
    document.save(output_path, pdf_options)

if __name__ == "__main__":
    # Example usage – adjust paths as needed
    convert_docx_to_pdf(
        input_path="YOUR_DIRECTORY/input.docx",
        output_path="YOUR_DIRECTORY/output.pdf"
    )
```

### النتيجة المتوقعة

تشغيل السكريبت يجب أن ينتج PDF يحتوي على:

1. يحافظ على جميع النصوص والعناوين والجداول.
2. يعرض الصور أو مربعات النص **inline** مع الفقرات المحيطة.
3. يطابق التخطيط الأصلي بدقة، دون كائنات عائمة متشتتة.

يمكنك التحقق بفتح الـ PDF في أي عارض—Adobe Reader، Chrome، أو حتى تطبيق هاتف.

## تنوعات شائعة وحالات حافة

### تحويل ملفات متعددة في مجلد

إذا كنت بحاجة إلى **convert word to pdf** لمجلد كامل، غلف الدالة داخل حلقة:

```python
import os, glob

source_folder = "YOUR_DIRECTORY/docs"
target_folder = "YOUR_DIRECTORY/pdfs"
os.makedirs(target_folder, exist_ok=True)

for docx_path in glob.glob(os.path.join(source_folder, "*.docx")):
    pdf_name = os.path.splitext(os.path.basename(docx_path))[0] + ".pdf"
    pdf_path = os.path.join(target_folder, pdf_name)
    convert_docx_to_pdf(docx_path, pdf_path)
```

### التعامل مع المستندات المحمية بكلمة مرور

Aspose.Words يمكنه فتح الملفات المشفرة بتوفير كلمة مرور:

```python
load_options = aw.loading.LoadOptions()
load_options.password = "mySecret"
protected_doc = aw.Document("protected.docx", load_options)
protected_doc.save("protected.pdf", pdf_options)
```

### استخدام مُولِّد PDF مختلف

أحيانًا قد ترغب في دقة أعلى (مثل الحفاظ على أشكال الخط الدقيقة). غيّر المُولِّد:

```python
pdf_options.pdf_rendering_options = aw.saving.PdfRenderingOptions()
pdf_options.pdf_rendering_options.use_emf_embedded_fonts = True
```

## نصائح احترافية ومخاطر

- **Pro tip:** دائمًا اختبر بمستند يحتوي على شكل عائم واحد على الأقل. هذه أسرع طريقة للتأكد من أن علم `export_floating_shapes_as_inline_tag` يقوم بوظيفته.
- **Watch out for:** الصور الكبيرة جدًا يمكن أن تزيد حجم PDF. فكر في تقليل دقتها قبل التحويل باستخدام `ImageSaveOptions`.
- **Version check:** الـ API المعروض يعمل مع Aspose.Words 23.9 وما بعده. إذا كنت تستخدم نسخة أقدم، قد يكون اسم الخاصية `ExportFloatingShapesAsInlineTag` (حرف “E” كبير).

## الخاتمة

أصبح لديك الآن حل متكامل من البداية للنهاية لـ **save Word as PDF** باستخدام Python. بتحميل المستند، تعديل خيارات حفظ PDF، واستدعاء `save`، أصبحت متمكنًا من جوهر **python word to pdf conversion** بينما تعلمت أيضًا **how to export shapes** بشكل صحيح.

من هنا يمكنك:

- معالجة دفعة من آلاف الملفات،
- دمج السكريبت في خدمة ويب،
- توسيعه للتعامل مع ملفات DOCX محمية بكلمة مرور، أو
- التحويل إلى تنسيق إخراج آخر مثل XPS أو HTML.

جرّبه، عدّل الخيارات، ودع الأتمتة تتولى الأعمال الشاقة في سير عمل المستندات. برمجة سعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}