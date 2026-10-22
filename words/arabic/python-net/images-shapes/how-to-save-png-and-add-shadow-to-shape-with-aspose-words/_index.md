---
category: general
date: 2026-08-17
description: كيفية حفظ PNG باستخدام Aspose.Words للبايثون. تعلم إضافة ظل إلى الشكل،
  حفظ المستند كملف PDF وتصدير Word إلى PNG في دليل واحد.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save png
- add shadow to shape
- save document as pdf
- export word to png
- convert word to pdf
language: ar
lastmod: 2026-08-17
og_description: كيفية حفظ PNG باستخدام Aspose.Words. يوضح هذا البرنامج التعليمي إضافة
  ظل إلى شكل، حفظ المستند كملف PDF، وتصدير Word إلى PNG.
og_image_alt: Screenshot of a Word document with a rectangle shape that has a shadow,
  saved as PNG and PDF
og_title: كيفية حفظ PNG وإضافة ظل إلى الشكل باستخدام Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  headline: How to save PNG and add shadow to shape with Aspose.Words
  type: TechArticle
- description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  name: How to save PNG and add shadow to shape with Aspose.Words
  steps:
  - name: Pro tip
    text: If you need a sharper shadow, reduce `blur`. For a more pronounced offset,
      increase `distance`. The `Shadow` class also exposes `angle` and `transparency`
      for fine‑tuned control.
  - name: 'Optional: higher‑resolution PNG'
    text: '```python png_options = aw.image.PngSaveOptions() png_options.resolution
      = 300 # DPI doc.save("output/high_res_output.png", png_options) ```'
  - name: Expected output
    text: 'Running the script creates three files:'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Image export
title: كيفية حفظ PNG وإضافة ظل إلى الشكل باستخدام Aspose.Words
url: /ar/python/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية حفظ PNG وإضافة ظل إلى الشكل باستخدام Aspose.Words

إذا كنت بحاجة إلى **كيفية حفظ PNG** من ملف Word، فإن هذا الدليل يقدم لك حلاً كاملاً قابلاً للتنفيذ. ستتعرف أيضًا على كيفية **إضافة ظل إلى الشكل**، **حفظ المستند كملف PDF**، و**تصدير Word إلى PNG** دون مغادرة بيئة Aspose.Words.

يغطي هذا البرنامج التعليمي كل ما يلزم لتحويل مستند Word فارغ إلى ملف PDF وصورة PNG، مع تطبيق تأثير ظل بسيط على شكل مستطيل. لا تحتاج إلى أدوات خارجية، والكود يعمل مع Aspose.Words for Python via .NET 7 أو أحدث.

## ما ستحققه

بنهاية هذه المقالة ستكون قادرًا على:

* إنشاء مستند Word جديد برمجيًا.  
* إدراج شكل مستطيل وتكوين تأثير الظل.  
* حفظ نفس المستند كملف PDF.  
* تصدير المستند كصورة PNG.  

هذه الخطوات تجيب على الاستفسار الشائع **كيفية حفظ PNG** مع معالجة **إضافة ظل إلى الشكل** و**حفظ المستند كملف PDF** في سير عمل واحد.

## المتطلبات المسبقة

* Python 3.9 أو أحدث.  
* Aspose.Words for Python via .NET مثبت (`pip install aspose-words`).  
* صلاحية كتابة إلى دليل الإخراج الذي تحدده.  

إذا لم تقم بتثبيت Aspose.Words بعد، نفّذ:

```bash
pip install aspose-words
```

## كيفية حفظ PNG باستخدام Aspose.Words

الخطوة الأساسية الأولى هي إنشاء مستند و`DocumentBuilder`. يوفّر الـ builder واجهة برمجة تطبيقات سلسة لإدراج محتوى مثل الأشكال، الجداول، أو النص.

```python
import aspose.words as aw

# Create a new blank document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` يمثل ملف Word بالكامل في الذاكرة. `aw.DocumentBuilder` يشير إلى موقع الإدراج الحالي، والذي يكون في البداية بداية القسم الأول (والوحيد).

## إضافة ظل إلى الشكل قبل التصدير

يمكن أن يكون الشكل أي كائن رسم—مستطيل، إهليلج، أو مضلع مخصص. هنا نقوم بإنشاء مستطيل بحجم 100 × 100 نقطة وتطبيق ظل ناعم.

```python
# Insert a rectangle shape (100x100 points)
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

# Configure a simple shadow
shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Softness of the shadow edges
shape.shadow.distance = 3.0      # Distance from the shape
shape.shadow.color = aw.Color.black
```

لماذا نضبط الظل قبل الحفظ؟ تقوم Aspose.Words برسم الظل أثناء مراحل تصدير PDF وPNG، لذا يُحافظ على التأثير البصري في كلا تنسيقَي الإخراج.

### نصيحة احترافية
إذا كنت بحاجة إلى ظل أكثر حدة، قلل قيمة `blur`. للحصول على إزاحة أكثر وضوحًا، زد قيمة `distance`. كما تُتيح فئة `Shadow` ضبط `angle` و`transparency` للتحكم الدقيق.

## حفظ المستند كملف PDF

حفظ مستند Word كملف PDF هو سطر واحد بمجرد أن يصبح المحتوى جاهزًا. ثابت `SaveFormat.PDF` يُخبر Aspose.Words بإجراء التحويل.

```python
# Save the document as PDF (shadow is rendered in the output)
pdf_path = "output/output.pdf"
doc.save(pdf_path, aw.SaveFormat.PDF)
```

يحتوي ملف PDF الناتج على المستطيل مع الظل الدقيق الذي حددته. تتعامل Aspose.Words مع الرسومات المتجهة، لذا يبقى حجم PDF معتدلًا.

## تصدير Word إلى PNG

إن تصدير إلى PNG يُنشئ صورة نقطية لكل صفحة. بشكل افتراضي تستخدم Aspose.Words 96 DPI؛ يمكنك زيادة هذه القيمة للحصول على إخراج بدقة أعلى عبر توفير كائن `PngSaveOptions`.

```python
# Export the same document as PNG
png_path = "output/output.png"
doc.save(png_path, aw.SaveFormat.PNG)
```

عند **تصدير Word إلى PNG**، يتم حفظ كل صفحة كملف PNG منفصل. نظرًا لأن مستند المثال لدينا يحتوي على صفحة واحدة فقط، يظهر ملف PNG واحد فقط.

### اختياري: PNG بدقة أعلى

```python
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI
doc.save("output/high_res_output.png", png_options)
```

دقة DPI أعلى مفيدة عندما يُستخدم PNG في الطباعة أو عندما تحتاج إلى صورة مصغرة واضحة.

## البرنامج الكامل – نسخ، لصق، وتشغيل

فيما يلي البرنامج الكامل المستقل الذي يُنفّذ كل خطوة موصوفة أعلاه. احفظه باسم `generate_assets.py` وشغّله من سطر الأوامر.

```python
import os
import aspose.words as aw

# ------------------------------------------------------------------
# 1. Prepare output folder
# ------------------------------------------------------------------
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# ------------------------------------------------------------------
# 2. Create a new blank document and a builder
# ------------------------------------------------------------------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ------------------------------------------------------------------
# 3. Insert a rectangle shape and add a shadow
# ------------------------------------------------------------------
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Soft edges
shape.shadow.distance = 3.0      # Offset from shape
shape.shadow.color = aw.Color.black

# ------------------------------------------------------------------
# 4. Save as PDF (demonstrates "save document as pdf")
# ------------------------------------------------------------------
pdf_path = os.path.join(output_dir, "output.pdf")
doc.save(pdf_path, aw.SaveFormat.PDF)

# ------------------------------------------------------------------
# 5. Export as PNG (demonstrates "how to save png")
# ------------------------------------------------------------------
png_path = os.path.join(output_dir, "output.png")
doc.save(png_path, aw.SaveFormat.PNG)

# ------------------------------------------------------------------
# 6. Optional high‑resolution PNG (demonstrates "export word to png")
# ------------------------------------------------------------------
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI for sharper output
high_res_png_path = os.path.join(output_dir, "high_res_output.png")
doc.save(high_res_png_path, png_options)

print(f"Files written to {os.path.abspath(output_dir)}")
```

### النتيجة المتوقعة

تشغيل البرنامج يُنشئ ثلاثة ملفات:

* `output/output.pdf` – ملف PDF يحتوي على مستطيل يُسقط ظلًا أسود.  
* `output/output.png` – صورة PNG بدقة 96 DPI لنفس الصفحة.  
* `output/high_res_output.png` – صورة PNG بدقة 300 DPI لجودة أعلى.  

افتح أيًا من الملفات في عارضك المفضل للتحقق من أن الظل يظهر بالضبط كما تم تعريفه.

## أسئلة شائعة وحالات خاصة

**ماذا لو لم يكن دليل الإخراج موجودًا؟**  
يقوم البرنامج باستدعاء `os.makedirs(output_dir, exist_ok=True)`، مما ينشئ المجلد تلقائيًا. هذا يمنع حدوث `FileNotFoundError` أثناء عمليات الحفظ.

**هل يمكنني إضافة أشكال متعددة بظلال مختلفة؟**  
نعم. أنشئ كائنات `Shape` إضافية، واضبط خاصية `shadow` لكل منها بشكل مستقل، ثم أدخلها باستخدام `builder.insert_node(shape)` قبل الحفظ.

**هل سيُحافظ على الظل عند التحويل إلى تنسيقات نقطية أخرى (مثل JPEG)؟**  
تقوم Aspose.Words برسم الظل لجميع التنسيقات النقطية المدعومة بواسطة `SaveFormat`. يمكنك استبدال `aw.SaveFormat.PNG` بـ `aw.SaveFormat.JPEG` وسيظل الظل ظاهرًا.

**كيف يختلف هذا عن “convert word to pdf”؟**  
`convert word to pdf` هو في الأساس نفس العملية التي تُجرى في الخطوة 4. استدعاء `doc.save` نفسه مع `SaveFormat.PDF` يتعامل مع التحويل داخليًا، مع الحفاظ على التخطيط، الخطوط، والرسومات مثل الظلال.

**هل هناك حد لحجم الشكل؟**  
يُقاس الشكل بالنقاط (1 pt ≈ 1/72 inch). قد تزيد الأبعاد الكبيرة جدًا من حجم الملف الناتج، لكن Aspose.Words لا يفرض حدًا ثابتًا. عدّل معاملات `width` و`height` عند إنشاء `aw.Shape` لتناسب تخطيطك.

## الخلاصة

أنت الآن تعرف **كيفية حفظ PNG** من مستند Word بينما تتعلم أيضًا **إضافة ظل إلى الشكل**، **حفظ المستند كملف PDF**، و**تصدير Word إلى PNG** باستخدام Aspose.Words for Python. يُظهر البرنامج الكامل نمطًا نظيفًا وقابلًا للتكرار يمكنك تكييفه للمستندات الأكبر، الصفحات المتعددة، أو تأثيرات رسومية أكثر تعقيدًا.

الخطوات التالية قد تشمل:

* تجربة قيم `ShapeType` أخرى (إهليلج، سحابة، إلخ).  
* استخدام `

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [How to Convert DOCX to PNG in Java – Aspose.Words](/words/english/java/document-converting/converting-documents-images/)
- [Save Word Documents as PostScript in Python Using Aspose.Words: A Comprehensive Guide](/words/english/python-net/document-operations/save-docs-as-postscript-using-aspose-words-python/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}