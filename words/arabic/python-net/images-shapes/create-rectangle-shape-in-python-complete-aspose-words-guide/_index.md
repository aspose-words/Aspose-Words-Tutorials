---
category: general
date: 2026-06-24
description: إنشاء شكل مستطيل في بايثون باستخدام Aspose.Words، وتعلم كيفية إضافة ظل
  إلى الشكل، وتعيين زاوية الظل، وحفظ المستند كملف PDF في دقائق.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shape shadow
- set shadow angle
language: ar
og_description: إنشاء شكل مستطيل في بايثون، إضافة ظل إلى الشكل، ضبط زاوية الظل، وحفظ
  المستند كملف PDF باستخدام Aspose.Words. اتبع هذا الدليل خطوة بخطوة.
og_title: إنشاء شكل مستطيل في بايثون – دليل Aspose.Words الكامل
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  headline: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  name: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: What if I need a different shape?
    text: Aspose.Words supports many `ShapeType` values (ellipse, star, callout, etc.).
      Simply replace `aw.drawing.ShapeType.RECTANGLE` with the desired enum, like
      `aw.drawing.ShapeType.ELLIPSE`.
  - name: Can I add multiple shadows?
    text: The API exposes only one `ShadowFormat` per shape, but you can simulate
      multiple shadows by duplicating the shape, offsetting each copy, and adjusting
      transparency.
  - name: How do I change the shadow color to match my brand?
    text: Just set `shadow.color` to any `aw.drawing.Color`. For a brand blue, use
      `aw.drawing.Color.from_argb(255, 0, 120, 215)`.
  - name: What about saving as DOCX instead of PDF?
    text: Replace `document.save(pdf_path)` with `document.save("output/shadowed_rectangle.docx")`.
      The shadow rendering is preserved across both formats.
  - name: Does the shadow work on older PDF viewers?
    text: Aspose.Words renders the shadow as a vector effect, which is widely supported.
      However, very old viewers might flatten the effect; testing on your target audience’s
      devices is always a good habit.
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: إنشاء شكل مستطيل في بايثون – دليل Aspose.Words الكامل
url: /ar/python/images-shapes/create-rectangle-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء شكل مستطيل في بايثون – دليل Aspose.Words الكامل

هل تساءلت يوماً كيف **create rectangle shape** في مستند Word باستخدام بايثون؟ ربما تحتاج إلى صندوق توضيحي جريء، إشارة بصرية لمخطط، أو مجرد مستطيل أنيق لتقرير. أياً كان السبب، فقد وصلت إلى المكان الصحيح. في هذا الدرس سنستعرض العملية بالكامل — من إدراج المستطيل، إلى إضافة ظل خفيف، تعديل زاوية الظل، وأخيراً **save document as PDF** لتتمكن من مشاركته مع أي شخص.

سنستخدم **Aspose.Words for Python via .NET**، مكتبة قوية تتيح لك تعديل ملفات Word دون الحاجة إلى فتح Word نفسه. بنهاية هذا الدليل ستكون قادراً على الإجابة على سؤال *“how to add shape shadow”* بثقة، وستحصل على سكريبت جاهز للتنفيذ يمكنك إدراجه في أي مشروع.

---

## ما ستحتاجه

- **Python 3.8+** مثبت على جهازك.  
- **Aspose.Words for Python via .NET** (حزمة `aspose-words`). قم بتثبيتها عبر:

  ```bash
  pip install aspose-words
  ```

- مجلد قابل للكتابة حيث سيتم حفظ ملف PDF المُولد.  
- (اختياري) بيئة تطوير متكاملة أو محرر نصوص — VS Code يعمل بشكل ممتاز.

هذا كل شيء. لا تحتاج إلى ملفات DLL إضافية، ولا تثبيت Office، مجرد حزمة pip واحدة.

## الخطوة 1: إعداد المستند والباني

الأول الذي يجب عليك فعله هو إنشاء كائنات صديقة لـ **create rectangle shape**: `Document` و `DocumentBuilder`. فكر في الـ Builder كقلمك؛ فهو يرسم كل شيء لك.

```python
import aspose.words as aw

# Initialize a new blank document
document = aw.Document()

# DocumentBuilder gives us a convenient way to add content
builder = aw.DocumentBuilder(document)
```

> **Why this matters:** يمثل كائن `Document` ملف .docx بالكامل، بينما يوفر `DocumentBuilder` طرقاً مثل `insert_shape` تجعل رسم الأشكال سهلًا للغاية.

## الخطوة 2: إدراج شكل المستطيل

الآن بعد أن أصبح لدينا Builder، يمكننا أخيراً **create rectangle shape**. تحتاج طريقة `insert_shape` إلى ثلاثة معاملات: نوع الشكل، العرض، والارتفاع. سنستخدم عرض 200 pt وارتفاع 100 pt للحصول على نسبة متناسقة.

```python
# Insert a rectangle with a width of 200 points and a height of 100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

في هذه المرحلة قد نجحت في **create rectangle shape** داخل المستند. إذا فتحت ملف DOCX المُولد (سنقوم بذلك لاحقاً)، سترى مستطيلًا بسيطًا يقع حيث كان المؤشر.

## الخطوة 3: الوصول إلى كائن تنسيق الظل

لـ **add shadow to shape**، نحتاج أولاً إلى الحصول على تنسيق ظل الشكل. كل شكل في Aspose.Words يمتلك خاصية `shadow_format` التي تكشف عن جميع إعدادات الظل.

```python
# Grab the shadow formatting object for later tweaks
shadow = rectangle.shadow_format
```

وجود مرجع `shadow` يتيح لنا التحكم في الرؤية، الضبابية، المسافة، الزاوية، اللون، والشفافية — كل ذلك في بضع أسطر من الشيفرة.

## الخطوة 4: تفعيل الظل وتكوين مظهره

هنا يحدث السحر. سنقوم بـ **add shadow to shape**، نجعل الظل مضببًا قليلًا، نُحرفه قليلًا، نحدد الاتجاه (جزء **set shadow angle**)، ونمنحه لونًا أسودًا شبه شفاف.

```python
# Turn the shadow on
shadow.visible = True

# Soften the edges – a blur radius of 8 points looks natural
shadow.blur_radius = 8.0

# Push the shadow away from the rectangle by 5 points
shadow.distance = 5.0

# Set the direction of the light source – 45 degrees creates a diagonal drop
shadow.angle = 45

# Choose a color; black works well for most documents
shadow.color = aw.drawing.Color.black

# Make the shadow 30 % transparent for a subtle effect
shadow.transparency = 0.3
```

> **Pro tip:** إذا احتجت إلى تأثير أكثر دراماتيكية، زد `blur_radius` أو قلل `transparency`. وعلى العكس، يمكن الحصول على ظل حاد وكامل الشفافية باستخدام `blur_radius = 0` و `transparency = 0`.

## الخطوة 5: حفظ المستند كملف PDF

لقد **create rectangle shape**، وقد **add shadow to shape**، والآن سنقوم بـ **save document as PDF** حتى يبدو الناتج متطابقًا على أي جهاز. تجعلك Aspose.Words تنفذ ذلك بسطر واحد.

```python
# Define where you want the PDF to land
output_path = "output/shadowed_rectangle.pdf"

# Save the whole document (including the rectangle with its shadow) as PDF
document.save(output_path)
print(f"PDF saved to {output_path}")
```

تشغيل السكريبت سيولد `shadowed_rectangle.pdf` داخل مجلد `output`. افتحه بأي عارض PDF وسترى مستطيلًا نظيفًا بظل ناعم بزاوية 45 درجة — تمامًا ما قمنا بتكوينه.

## مثال كامل يعمل

فيما يلي السكريبت الكامل الجاهز للتنفيذ والذي يجمع جميع الخطوات السابقة. انسخه إلى ملف باسم `create_rectangle_with_shadow.py` ثم نفّذ الأمر `python create_rectangle_with_shadow.py`.

```python
import aspose.words as aw
import os

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Initialize document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert the rectangle shape (200 pt × 100 pt)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Access shadow formatting
shadow = rectangle.shadow_format

# 4️⃣ Configure shadow – visible, blurred, offset, angled, colored, semi‑transparent
shadow.visible = True
shadow.blur_radius = 8.0          # softer edges
shadow.distance = 5.0            # how far the shadow sits from the shape
shadow.angle = 45                # direction in degrees – this is the **set shadow angle** step
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.3        # 30 % transparent

# 5️⃣ Save the document as PDF
pdf_path = os.path.join(output_dir, "shadowed_rectangle.pdf")
document.save(pdf_path)

print(f"✅ PDF created at: {pdf_path}")
```

**Expected output:** ملف PDF يُظهر مستطيلًا واحدًا بظل مائل لطيف. لا صفحات إضافية، ولا قطع مخفية — فقط الشكل الذي صممناه.

## أسئلة شائعة وحالات خاصة

### ماذا لو احتجت إلى شكل مختلف؟

يدعم Aspose.Words العديد من قيم `ShapeType` (إهليلج، نجمة، توضيح، إلخ). ما عليك سوى استبدال `aw.drawing.ShapeType.RECTANGLE` بالعدد المطلوب، مثل `aw.drawing.ShapeType.ELLIPSE`.

### هل يمكن إضافة ظلال متعددة؟

تُظهر الـ API `ShadowFormat` واحدًا فقط لكل شكل، لكن يمكنك محاكاة ظلال متعددة عن طريق تكرار الشكل، إزاحة كل نسخة، وتعديل الشفافية.

### كيف أغيّر لون الظل ليتناسب مع علامتي التجارية؟

ما عليك سوى تعيين `shadow.color` إلى أي `aw.drawing.Color`. للون أزرق العلامة التجارية، استخدم `aw.drawing.Color.from_argb(255, 0, 120, 215)`.

### ماذا عن الحفظ كملف DOCX بدلاً من PDF؟

استبدل `document.save(pdf_path)` بـ `document.save("output/shadowed_rectangle.docx")`. يتم الحفاظ على تمثيل الظل في كلا الصيغتين.

### هل يعمل الظل على عارضات PDF القديمة؟

تُظهر Aspose.Words الظل كأثر متجه، وهو مدعوم على نطاق واسع. ومع ذلك، قد تقوم بعض العارضات القديمة بتسطيح التأثير؛ لذا يُنصح باختبار الملف على أجهزة الجمهور المستهدف.

## نصائح لتلميع ملف PDF الخاص بك

- **Add a border:** `rectangle.line_format.width = 1.5` وحدد لونًا لإطار واضح.  
- **Center the rectangle:** استخدم `builder.move_to_document_start()` قبل الإدراج، ثم `builder.paragraph_format.alignment = aw.ParagraphAlignment.CENTER`.  
- **Combine with text:** أدخل `TextFragment` بعد المستطيل لتسمية الشكل، مثلاً `"Important Section"`.

هذه التعديلات الصغيرة يمكن أن تحول المستطيل البسيط إلى صندوق توضيحي مصقول يبدو احترافيًا في التقارير، العروض، أو الكتب الإلكترونية.

## الخاتمة

أصبح لديك الآن وصفة شاملة من البداية إلى النهاية لـ **create rectangle shape** في بايثون، **add shadow to shape**, **set shadow angle**, و **save document as PDF** باستخدام Aspose.Words. الخطوات مباشرة، والشيفرة مكتملة ذاتيًا، وقد رأيت لماذا كل سطر مهم — من تهيئة المستند إلى صقل ملف PDF النهائي.

بعد ذلك، قد تستكشف **how to add shape shadow** في رسومات أكثر تعقيدًا، تجرب ملء التدرجات، أو تولد جداول داخل الأشكال. تدعم المكتبة أيضًا ربط الأشكال بالإشارات المرجعية، وهو ما قد يكون مفيدًا للـ PDFs التفاعلية.

هل جربت تعديلًا مختلفًا؟ شاركه في التعليقات، أو اطرح أي أسئلة متبقية. برمجة سعيدة، واستمتع بإضافة عمق إضافي إلى مستنداتك! 

![شكل مستطيل مع ظل – مثال على إنشاء شكل مستطيل في بايثون](/images/rectangle-shadow.png)


## ما الذي ينبغي أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك الخاصة.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}