---
category: general
date: 2026-10-16
description: إنشاء مستند Word فارغ، إدراج شكل في Word، إضافة ظل خارجي، وحفظه كملف
  PDF باستخدام بايثون.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert shape in word
- save as pdf python
- add outer shadow shape
- create pdf with shape
language: ar
lastmod: 2026-10-16
og_description: إنشاء مستند Word فارغ مع شكل ظل خارجي باستخدام Aspose.Words للغة Python.
  يوضح هذا الدليل كيفية إدراج الشكل، وتطبيق الظل، وحفظ الملف كملف PDF.
og_image_alt: Screenshot of a Word document containing a rectangle shape with an outer
  shadow, saved as PDF
og_title: إنشاء مستند Word فارغ مع ظل الشكل – دليل بايثون
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document, insert shape in Word, add outer shadow,
    and save as PDF using Python.
  headline: Create blank Word document with shadowed shape in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- PDF generation
- Shape styling
title: إنشاء مستند Word فارغ مع شكل مظلَّل في بايثون
url: /ar/python/word-automation/create-blank-word-document-with-shadowed-shape-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word فارغ مع شكل مظلّل في Python

إذا كنت بحاجة إلى **إنشاء مستند Word فارغ** وإضافة رسم مخصص، فإن هذا الدليل يغطي ما تحتاجه. سنستعرض كيفية **إدراج شكل في Word**، وتطبيق **شكل ظل خارجي**، وأخيرًا **حفظه كملف PDF باستخدام Python**.

ستتعلم كيفية إعداد Aspose.Words for Python، بناء مستطيل، تنسيق ظله، وتوليد ملف PDF يحافظ على التأثير البصري. لا يلزم أي خبرة سابقة مع Aspose API، لكن يجب أن تكون لديك معرفة أساسية بـ Python وتثبيت فعال لـ Python 3.10 أو أحدث.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من أن لديك:

* Python 3.10 أو أحدث مثبت.
* ترخيص فعال لـ Aspose.Words for Python (يمكنك استخدام نسخة تجريبية مجانية للتقييم).
* إمكانية الوصول إلى `pip` لتثبيت حزمة `aspose-words`.
* صلاحية كتابة في الدليل الذي سيُحفظ فيه ملف PDF.

يمكنك تثبيت المكتبة بأمر واحد:

```bash
pip install aspose-words
```

## إنشاء مستند Word فارغ – إعداد البيئة

الخطوة الأولى هي إنشاء ملف Word فارغ سيعمل كقماش للشكل.

```python
import aspose.words as aw

# Initialize a new, empty document
doc = aw.Document()
# DocumentBuilder provides convenient methods for adding content
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` يمثل ملف Word فارغ تمامًا. باستخدام `DocumentBuilder` ستحصل على طرق مثل `insert_shape`، والتي سنستخدمها في الخطوة التالية.

## إدراج شكل في Word وتحديد الأبعاد

الآن نضيف مستطيل سيتلقى لاحقًا ظلًا خارجيًا. الحجم يُعبّر عنه بالنقاط (1 pt ≈ 1/72 inch).

```python
# Insert a rectangle shape with a width of 200 pt and a height of 100 pt
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)
```

استدعاء `insert_shape` يُعيد كائن `Shape` يمكنك تخصيصه أكثر. في هذه المرحلة يحتوي المستند بالفعل على مستطيل مرئي عند فتحه في Microsoft Word.

## إضافة ظل خارجي للشكل – تخصيص التأثير

توفر Aspose.Words فئة `ShadowEffect` لتعريف خصائص الظل مثل النمط، الضبابية، المسافة، واللون.

```python
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a new shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # Choose an outer shadow
shadow.blur = 5.0                         # Softness of the shadow edges
shadow.distance = 3.0                     # Offset distance from the shape
shadow.color = aw.Color.black             # Shadow color

# Apply the shadow to the rectangle
rectangle.shadow = shadow
```

تعيين `style` إلى `OUTER` يضمن ظهور الظل خارج حدود المستطيل، مما يمنح مظهرًا ثلاثي الأبعاد خفيفًا. يمكنك التجربة مع `blur` و `distance` للحصول على ظل أكثر تشددًا أو انتشارًا.

## حفظ كملف PDF باستخدام Python – إكمال المستند

بعد تنسيق الشكل، يمكن حفظ المستند مباشرة كملف PDF. تتولى Aspose.Words عملية التحويل داخليًا، مع الحفاظ على تأثير الظل.

```python
output_path = "output/shape_with_shadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

عند فتح `shape_with_shadow.pdf` في أي عارض PDF، ستظهر المستطيل مع الظل الخارجي تمامًا كما ظهر في Word.

## مثال كامل يعمل

فيما يلي السكربت الكامل الذي يجمع جميع الخطوات. انسخه إلى ملف باسم `create_word_with_shadow.py` وشغّله.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1. Create a blank Word document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2. Insert a rectangle shape
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)

# 3. Define and apply an outer shadow
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER
shadow.blur = 5.0
shadow.distance = 3.0
shadow.color = aw.Color.black
rectangle.shadow = shadow

# 4. Save the document as PDF
pdf_path = os.path.join(output_dir, "shape_with_shadow.pdf")
doc.save(pdf_path)

print(f"PDF generated at: {pdf_path}")
```

**الناتج المتوقع**

تشغيل السكربت يطبع سطر تأكيد، مثلًا:

```
PDF generated at: output/shape_with_shadow.pdf
```

فتح ملف PDF الناتج يُظهر صفحة واحدة تحتوي على مستطيل بحجم 200 pt × 100 pt مع ظل أسود ناعم خارجي.

## الاختلافات الشائعة وحالات الحافة

* **تغيير لون الظل** – استبدل `aw.Color.black` بأي قيمة `aw.Color` أخرى، مثل `aw.Color.red` أو `aw.Color.from_argb(255, 0, 120, 215)`.
* **استخدام شكل مختلف** – غيّر `aw.drawing.ShapeType.RECTANGLE` إلى `OVAL` أو `DIAMOND` أو أي قيمة من القيم المدعومة في الـ enum.
* **الحفظ كـ DOCX بدلاً من PDF** – استدعِ `doc.save("output/shape.docx")` للحفاظ على تنسيق Word.
* **أشكال متعددة** – أنشئ أشكالًا إضافية باستدعاء `builder.insert_shape` مرة أخرى؛ يمكن لكل شكل أن يمتلك `ShadowEffect` خاصًا به.

**نصيحة احترافية:** إذا كنت بحاجة إلى وضع الشكل في موقع محدد، عيّن `rectangle.left` و `rectangle.top` بعد الإدراج. يمنحك ذلك تحكمًا دقيقًا في موضع الشكل.

## الخلاصة

أنت الآن تعرف كيفية **إنشاء مستند Word فارغ**، **إدراج شكل في Word**، **إضافة ظل خارجي للشكل**، و**حفظه كملف PDF باستخدام Python**. يوضح مثال الشيفرة الكامل سير العمل من البداية إلى النهاية، وتوضح الشروحات سبب ضرورة كل استدعاء API.

من هنا يمكنك استكشاف خيارات تنسيق أكثر تقدمًا، إضافة نص داخل الشكل، أو دمج عدة أشكال لإنشاء مخططات معقدة. جرّب معلمات الظل المختلفة لتتناسب مع هوية علامتك التجارية، ودمج هذا النهج في خطوط أنابيب توليد المستندات الأكبر.

برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Create PDF from Word – Complete Python Guide with Aspose.Words](/words/english/python-net/document-conversion/create-pdf-from-word-complete-python-guide-with-aspose-words/)
- [Add Shadow to Shape in Word with Aspose.Words – Step‑by‑Step](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}