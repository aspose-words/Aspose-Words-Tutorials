---
category: general
date: 2026-08-14
description: كيفية إضافة ظل إلى شكل في Word باستخدام Python – تعلم تطبيق تأثير الظل،
  إنشاء تأثير الظل، وحفظ مستند Word بكفاءة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add shadow
- apply shadow effect
- create shadow effect
- save word document
- add shadow to shape
language: ar
lastmod: 2026-08-14
og_description: كيفية إضافة ظل إلى شكل في Word باستخدام Python. اتبع هذا الدليل الكامل
  لتطبيق تأثير الظل، وإنشاء تأثير الظل، وحفظ مستند Word بمظهر احترافي.
og_image_alt: Screenshot illustrating how to add shadow to a Word shape using Python
og_title: كيفية إضافة ظل إلى شكل في Word باستخدام بايثون – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add shadow to a Word shape using Python – learn to apply shadow
    effect, create shadow effect, and save Word document efficiently.
  headline: How to add shadow to a Word shape using Python
  type: TechArticle
- description: How to add shadow to a Word shape using Python – learn to apply shadow
    effect, create shadow effect, and save Word document efficiently.
  name: How to add shadow to a Word shape using Python
  steps:
  - name: Load the Word document
    text: '```python import aspose.words as aw'
  - name: Retrieve the target shape
    text: '```python # Get the first shape in the document tree. shape = doc.get_child(aw.NodeType.SHAPE,
      0, True) ```'
  - name: Create a shadow object for the shape
    text: '```python # Instantiate a Shadow object and assign it to the shape. shape.shadow
      = aw.Shadow() ```'
  - name: Configure the shadow’s appearance
    text: '```python # Adjust the softness of the shadow edges. shape.shadow.blur
      = 5 # Higher values = softer edges'
  - name: Save the document to apply the changes
    text: '```python # Save the modified document. Overwrite or specify a new file
      name. doc.save("YOUR_DIRECTORY/output.docx") ```'
  - name: Expected result
    text: 'When you open `output.docx` in Microsoft Word:'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
- Document styling
title: كيفية إضافة ظل إلى شكل Word باستخدام Python
url: /ar/python/images-shapes/how-to-add-shadow-to-a-word-shape-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إضافة ظل إلى شكل Word باستخدام Python

إذا كنت بحاجة إلى **كيفية إضافة ظل** إلى شكل داخل مستند Word، يوضح لك هذا الدليل الخطوات الدقيقة. ستتعلم كيفية تطبيق تأثير الظل، إنشاء تأثير الظل، وحفظ مستند Word دون مغادرة بيئة التطوير المتكاملة الخاصة بك.

إضافة ظل بصري يجعل المخططات، التعليقات التوضيحية، والرموز تبرز، مما يحسن قابلية القراءة للمستخدمين النهائيين. يفترض الدرس أنك تمتلك معرفة أساسية بـ Python وإصدار حديث من مكتبة Aspose.Words for Python مثبتة.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* Python 3.8 أو أحدث مثبت.
* حزمة `aspose-words` (`pip install aspose-words`) – المكتبة التي تتعامل مع ملفات DOCX.
* مستند Word (`input.docx`) يحتوي على شكل واحد على الأقل (مثلاً AutoShape أو صورة).

هذه المتطلبات تضمن أن الكود يعمل دون تعديل على Windows أو macOS أو Linux.

## كيفية إضافة ظل إلى شكل في مستند Word

الأقسام التالية تقسم المهمة إلى خطوات واضحة مرقمة. كل خطوة تشرح **لماذا** العملية مهمة، وليس فقط **ماذا** تكتب.

### الخطوة 1: تحميل مستند Word

```python
import aspose.words as aw

# Load the existing DOCX file. Replace YOUR_DIRECTORY with the actual path.
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

*لماذا هذا مهم:* تحميل المستند يُنشئ تمثيلاً في الذاكرة يمكنك تعديلها. بدون هذا الكائن، لا يمكنك الوصول إلى الأشكال أو تطبيق الأنماط.

### الخطوة 2: استرجاع الشكل المستهدف

```python
# Get the first shape in the document tree.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
```

*لماذا هذا مهم:* `get_child` يتجول في شجرة عقد المستند ويعيد نوع العقدة المطلوب. الوسيط الثالث (`True`) يُخبر Aspose.Words بالبحث بشكل متكرر، مما يضمن العثور على الشكل حتى لو كان داخل فقرة أو جدول.

> **نصيحة احترافية:** إذا كان مستندك يحتوي على أشكال متعددة، استخدم `doc.get_child_nodes(aw.NodeType.SHAPE, True)` وتكرار عبر المجموعة واختر الشكل الذي تحتاجه حسب الفهرس أو بفحص `shape.title` أو `shape.alt_text`.

### الخطوة 3: إنشاء كائن ظل للشكل

```python
# Instantiate a Shadow object and assign it to the shape.
shape.shadow = aw.Shadow()
```

*لماذا هذا مهم:* كائن `Shadow` يحمل جميع المعلمات البصرية (التمويه، المسافة، اللون، إلخ). ربطه بالشكل يخبر Word بعرض ظل عند فتح المستند.

### الخطوة 4: ضبط مظهر الظل

```python
# Adjust the softness of the shadow edges.
shape.shadow.blur = 5          # Higher values = softer edges

# Set how far the shadow is offset from the shape.
shape.shadow.distance = 3     # Measured in points

# Optional: change the shadow color to a light gray.
shape.shadow.color = aw.Color.gray

# Optional: set the shadow's transparency (0 = opaque, 255 = fully transparent).
shape.shadow.transparency = 50
```

*لماذا هذا مهم:* `blur` يتحكم في انتشار الظل، بينما `distance` يحدد الإزاحة. تعديل هذه القيم يتيح لك تحقيق رفع خفيف أو تأثير ظل درامي. تعديل `color` و `transparency` يضيف تخصيصًا إضافيًا للمظهر، وهو أمر أساسي عندما يتبع المستند دليل نمط الشركة.

### الخطوة 5: حفظ المستند لتطبيق التغييرات

```python
# Save the modified document. Overwrite or specify a new file name.
doc.save("YOUR_DIRECTORY/output.docx")
```

*لماذا هذا مهم:* طريقة `save` تكتب التغييرات الموجودة في الذاكرة إلى ملف DOCX فعلي. بعد الحفظ، سيفتح `output.docx` في Microsoft Word ويعرض الشكل مع الظل المُكوَّن.

## البرنامج الكامل الذي يمكنك تشغيله اليوم

فيما يلي البرنامج الكامل الجاهز للتنفيذ بلغة Python. استبدل `YOUR_DIRECTORY` بالمجلد الذي يحتوي على ملفاتك.

```python
import aspose.words as aw

# 1️⃣ Load the source document.
doc = aw.Document("YOUR_DIRECTORY/input.docx")

# 2️⃣ Retrieve the first shape (you can loop for multiple shapes).
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# 3️⃣ Attach a new Shadow object.
shape.shadow = aw.Shadow()

# 4️⃣ Configure shadow properties.
shape.shadow.blur = 5
shape.shadow.distance = 3
shape.shadow.color = aw.Color.gray
shape.shadow.transparency = 50

# 5️⃣ Save the updated document.
doc.save("YOUR_DIRECTORY/output.docx")
```

### النتيجة المتوقعة

عند فتح `output.docx` في Microsoft Word:

* سيظهر الشكل الأول بظل رمادي ناعم مُزاح بثلاث نقاط.
* حواف الظل ستظهر مُطمّهة، مما يمنح الشكل رفعًا ثلاثي الأبعاد طفيفًا.
* لا يتغير أي محتوى آخر في المستند.

إذا لم تشاهد الظل، تحقق من أن الشكل ليس صورة ذات شفافية مضبوطة على 100 % أو أن وضع عرض المستند (Print Layout) مفعل.

## الاختلافات الشائعة والحالات الخاصة

| الحالة | كيفية تعديل الكود |
|-----------|-----------------------|
| **أشكال متعددة** | استخدم `doc.get_child_nodes(aw.NodeType.SHAPE, True)` وتكرار عبر المجموعة، مطبقًا نفس إعدادات الظل على كل شكل. |
| **فقط بعض الأشكال تحتاج إلى ظل** | افحص `shape.name` أو `shape.title` داخل الحلقة وطبق الظل فقط عندما يتطابق الاسم مع معاييرك. |
| **ألوان ظل مختلفة** | عيّن `shape.shadow.color = aw.Color(255, 0, 0)` للحصول على ظل أحمر، أو استخدم `aw.Color.from_argb(alpha, r, g, b)` لتخصيص الشفافية. |
| **لا يوجد شكل موجود** | احط عملية الاسترجاع بكتلة `try/except`؛ إذا كان `shape` يساوي `None`، أنشئ `Shape` جديد (مثل مستطيل) وأضفه إلى المستند قبل تطبيق الظل. |
| **الحفظ إلى PDF** | بعد إضافة الظل، استدعِ `doc.save("output.pdf")` – سيظهر الظل بشكل صحيح في تصدير PDF. |

هذه الاختلافات تضمن أن يكون الدرس مفيدًا سواء كنت تعالج قالبًا واحدًا أو دفعة من المستندات.

## كيفية إضافة ظل دون Aspose.Words (بديل)

إذا كنت تفضّل مكتبة `python-docx`، لا يمكنك ضبط الظل مباشرة لأن المكتبة لا تُظهر عناصر الظل VML/OOXML الأساسية. في هذه الحالة، سيتعين عليك تعديل XML يدويًا:

```python
from docx import Document
from lxml import etree

doc = Document("input.docx")
shape = doc.inline_shapes[0]._inline
# Insert <v:shadow> element here (complex XML manipulation)
```

نظرًا لأن Aspose.Words يوفر واجهة برمجة تطبيقات عالية المستوى لـ `Shadow`، فإن **كيفية إضافة ظل** يكون أكثر بساطة مع هذه المكتبة.

## الخطوات التالية

الآن بعد أن عرفت **كيفية إضافة ظل** إلى شكل، يمكنك:

* **تطبيق تأثير الظل** على الجداول أو مربعات النص باستخدام نفس فئة `Shadow`.
* **إنشاء تأثير ظل** بدمج مختلف للتمويه والمسافة لأغراض العلامة التجارية.
* استكشاف **إضافة ظل إلى الشكل** إلى جانب خيارات تنسيق أخرى مثل وزن الخط، لون التعبئة، والدوران.
* أتمتة المعالجة الجماعية بقراءة مجلد من ملفات DOCX، تطبيق الظل، وحفظ كل ملف باسم يحتوي على طابع زمني.

هذه الإضافات تسمح لك ببناء خط أنابيب تنسيق مستندات كامل المميزات يتوافق مع معايير التصميم المؤسسية.

---

*لقد تعلمت كيفية إضافة ظل إلى شكل Word باستخدام Python، وكيفية تطبيق تأثير الظل، وكيفية إنشاء تأثير الظل، وكيفية حفظ مستند Word مع التنسيق الجديد.* لا تتردد في تجربة المعلمات، ومشاركة نتائجك في التعليقات!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [إنشاء مستند Word بلغة Java – إضافة شكل مستطيل مع تأثير الظل](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [دروس ظل شكل Aspose.Words – إضافة ظل إلى شكل Word بلغة C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [كيفية حفظ Markdown من Word – دليل Python كامل](/words/english/python-net/document-conversion/how-to-save-markdown-from-word-complete-python-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}