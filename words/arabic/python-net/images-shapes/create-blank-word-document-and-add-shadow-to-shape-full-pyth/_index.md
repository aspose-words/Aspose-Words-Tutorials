---
category: general
date: 2026-07-20
description: إنشاء مستند Word فارغ باستخدام Python وتعلم كيفية إضافة ظل إلى الشكل
  باستخدام Aspose.Words، بما في ذلك كيفية إضافة الظل وتطبيق لون الظل.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add shadow to shape
- how to add shadow
- apply shadow color
language: ar
lastmod: 2026-07-20
og_description: إنشاء مستند Word فارغ في بايثون واكتشاف كيفية إضافة ظل إلى الشكل،
  بالإضافة إلى نصائح حول تطبيق لون الظل للحصول على مستندات مصقولة.
og_image_alt: Screenshot showing a blank Word document with a shape that has a shadow
  applied
og_title: إنشاء مستند Word فارغ – إضافة ظل إلى الشكل باستخدام بايثون
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Create blank word document in Python and learn how to add shadow to
    shape with Aspose.Words, including how to add shadow and apply shadow color.
  headline: Create Blank Word Document and Add Shadow to Shape – Full Python Guide
  type: TechArticle
- description: Create blank word document in Python and learn how to add shadow to
    shape with Aspose.Words, including how to add shadow and apply shadow color.
  name: Create Blank Word Document and Add Shadow to Shape – Full Python Guide
  steps:
  - name: Why start with a blank document?
    text: Because it guarantees that no hidden styles or remnants from templates interfere
      with the **shadow** effect we’ll add later. A clean document also speeds up
      processing, especially when you generate thousands of files in a batch job.
  - name: Why these values?
    text: '- A **blur of 5.0** gives a gentle feathered look without making the shape
      look detached. - Offsets of **2.0** create a subtle depth effect—enough to be
      noticeable but not overpowering. - Using **black** is a safe default; however,
      you can replace it with `aw.drawing.Color.from_argb(255, 30, 144, 25'
  - name: Expected Output
    text: '- A single‑page Word file. - A 200 × 100 pt rectangle positioned 100 pt
      from the top‑left corner. - A shadow that is **blurred**, **offset** by 2 pt
      on both axes, and colored **black** (or your custom color).'
  type: HowTo
- questions:
  - answer: It’s the most neutral shape, making the shadow effect obvious.
    question: Why a rectangle?
  - answer: The code safely grabs the first paragraph or creates one, so it works
      on both fresh and populated docs.
    question: What if the document already has content?
  type: FAQPage
tags:
- Aspose.Words
- Python
- Document Automation
- Shape Styling
title: إنشاء مستند Word فارغ وإضافة ظل إلى الشكل – دليل Python الكامل
url: /ar/python/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-pyth/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word فارغ وإضافة ظل إلى الشكل – دليل Python الكامل

هل احتجت يومًا إلى **إنشاء مستند Word فارغ** من الصفر ثم جعل شكل يبرز بظل خفيف؟ لست وحدك. سواء كنت تبني محرك قوالب أو تقوم بنمذجة تقرير، فإن إتقان طريقة إضافة ظل إلى الشكل يمكن أن يمنح ملفات Word مظهرًا احترافيًا.

في هذا الدرس سنستعرض العملية بالكامل باستخدام Aspose.Words for Python via .NET. سنبدأ بإنشاء مستند Word فارغ، ثم إدراج شكل بسيط، ثم **إضافة ظل إلى الشكل**، وضبط الضبابية والإزاحات، وأخيرًا **تطبيق لون الظل** ليتناسب مع هوية علامتك التجارية. في النهاية ستحصل على سكريبت جاهز يمكنك دمجه في أي مشروع.

## ما ستتعلمه

- كيفية **إنشاء مستند Word فارغ** برمجيًا باستخدام Aspose.Words.  
- الخطوات الدقيقة **لإضافة ظل إلى الشكل** والتحكم في مظهره.  
- لماذا تفاصيل **كيفية إضافة الظل** (الضبابية، الإزاحة) مهمة لتسلسل البصري.  
- تقنيات **تطبيق لون الظل** للحصول على تنسيق موحد عبر المستندات.  
- الأخطاء الشائعة (مثل عدم وجود الشكل، الصيغ غير المدعومة) وكيفية تجنبها.

> **المتطلبات المسبقة** – تحتاج إلى Python 3.8+ وحزمة `aspose-words` مثبتة (`pip install aspose-words`). لا يلزم خبرة سابقة في Aspose، لكن فهم أساسي لكائنات Python سيساعدك.

![Create blank word document with a shadowed shape](image.png){alt="إنشاء مستند Word فارغ مع شكل يحتوي على ظل مُطبق"}

## إنشاء مستند Word فارغ باستخدام Aspose.Words (Python)

أول شيء في قائمة التحقق هو **مستند Word فارغ** يمكننا ملؤه لاحقًا. تجعل Aspose.Words ذلك سطرًا واحدًا:

```python
import aspose.words as aw

# Step 1: Instantiate a new, empty document
doc = aw.Document()
```

هذا السطر يمنحنا لوحة نظيفة—كأنها ورقة جديدة. في الخلفية، تقوم Aspose بإنشاء بنية المستند اللازمة (الأقسام، الجسم، إلخ) بحيث لا تحتاج للقلق بشأن XML منخفض المستوى.

### لماذا نبدأ بمستند فارغ؟

لأن ذلك يضمن عدم وجود أنماط مخفية أو بقايا من القوالب قد تؤثر على تأثير **الظل** الذي سنضيفه لاحقًا. المستند النظيف يسرّع أيضًا المعالجة، خاصةً عند توليد آلاف الملفات في مهمة دفعة.

## إدراج شكل قبل إضافة الظل

لا يمكنك إضافة ظل لشيء غير موجود، أليس كذلك؟ لذا لنضع مستطيلًا بسيطًا على الصفحة الأولى. هذا أيضًا يوضح سير عمل **إضافة ظل إلى الشكل** في سيناريو واقعي.

```python
# Step 2: Create a rectangle shape (200x100 points) and add it to the first section
shape = aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
shape.width = 200
shape.height = 100
shape.left = 100   # Horizontal position from the left margin
shape.top = 100    # Vertical position from the top margin

# Add the shape to the document’s first paragraph (creates one if missing)
first_section = doc.first_section
first_paragraph = first_section.body.first_paragraph
if first_paragraph is None:
    first_paragraph = aw.Paragraph(doc)
    first_section.body.append_child(first_paragraph)

first_paragraph.append_child(shape)
```

بعض الملاحظات:

- **لماذا مستطيل؟** إنه الشكل الأكثر حيادية، مما يجعل تأثير الظل واضحًا.  
- **ماذا لو كان المستند يحتوي على محتوى بالفعل؟** الكود يلتقط الفقرة الأولى بأمان أو ينشئ واحدة، لذا يعمل على المستندات الفارغة والمملوءة على حد سواء.

## إضافة ظل إلى الشكل – تنفيذ خطوة بخطوة

الآن بعد أن أصبح لدينا شكل، حان الوقت للإجابة على سؤال **كيفية إضافة الظل**. توفر Aspose.Words كائن `Shadow` مع عدة خصائص يمكن تعديلها.

```python
# Step 3: Enable a shadow on the shape
shape.shadow = aw.drawing.Shadow()
```

هذا السطر يفعّل ميزة الظل. بشكل افتراضي، يكون الظل أسود، مع ضبابية معتدلة وإزاحة صفرية. لنخصصه.

## كيفية إضافة الظل: ضبط الضبابية، الإزاحة، واللون

يعتمد التأثير البصري للظل إلى حد كبير على ثلاثة معلمات:

1. **نصف قطر الضبابية** – يتحكم في مدى نعومة الحواف.  
2. **الإزاحة X/Y** – تحرك الظل أفقيًا وعموديًا.  
3. **اللون** – يتيح لك مطابقة ألوان العلامة التجارية.

إليك التكوين الكامل:

```python
# Step 4: Set the blur radius (higher = softer)
shape.shadow.blur = 5.0          # 5 points blur

# Step 5: Define horizontal and vertical offsets
shape.shadow.offset_x = 2.0      # 2 points to the right
shape.shadow.offset_y = 2.0      # 2 points down

# Step 6: Choose the shadow color (apply shadow color)
shape.shadow.color = aw.drawing.Color.black  # You can use any RGB value
```

### لماذا هذه القيم؟

- **ضبابية 5.0** تعطي مظهرًا ناعمًا دون أن يجعل الشكل يبدو منفصلًا.  
- إزاحات **2.0** تخلق تأثير عمق خفيف—كافي ليُلاحظ لكن ليس مفرطًا.  
- استخدام **الأسود** هو الإعداد الآمن؛ يمكنك استبداله بـ `aw.drawing.Color.from_argb(255, 30, 144, 255)` للحصول على ظل أزرق بارد يتماشى مع لون العلامة التجارية.

## تطبيق لون الظل لتنسيق دقيق

إذا كنت بحاجة إلى ظل غير أسود، فإن خطوة **تطبيق لون الظل** بسيطة. تسمح لك Aspose بتعريف أي لون ARGB:

```python
# Example: Apply a navy blue shadow
navy = aw.drawing.Color.from_argb(255, 0, 0, 128)  # Fully opaque, RGB(0,0,128)
shape.shadow.color = navy
```

> **نصيحة احترافية:** عند العمل مع قوالب الشركات، احفظ ألوان العلامة التجارية في ملف JSON وحمّلها وقت التشغيل. بهذه الطريقة يمكنك تبديل ألوان الظل عبر المستندات دون تعديل الكود.

## حفظ المستند والتحقق من النتيجة

انتهى كل العمل الشاق؛ الآن نحتاج فقط إلى حفظ الملف. تدعم Aspose صيغًا متعددة، لكن لنلتزم بـ DOCX الشائع.

```python
# Step 7: Save the document to disk
output_path = "ShadowedShape.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

افتح `ShadowedShape.docx` في Microsoft Word (أو LibreOffice) وسترى مستطيلًا بظل ناعم ونظيف—تمامًا ما قمنا بتكوينه.

### النتيجة المتوقعة

- ملف Word من صفحة واحدة.  
- مستطيل بحجم 200 × 100 pt موضعه 100 pt من الزاوية العليا اليسرى.  
- ظل **مضبب**، **مُزاح** بمقدار 2 pt على كلا المحورين، ولونه **أسود** (أو اللون المخصص الخاص بك).

إذا ظهر الشكل بدون ظل، تأكد من أنك استدعيت `shape.shadow = aw.drawing.Shadow()` *قبل* ضبط الخصائص الأخرى. الترتيب مهم لأن كائن `Shadow` يجب أن يكون موجودًا أولًا.

## الأخطاء الشائعة والحالات الطرفية

| المشكلة | السبب | الحل |
|-------|-------|-----|
| `shape` هو `None` | محاولة جلب شكل قبل وجوده | أدخل شكلًا أولًا (انظر قسم “إدراج شكل”) |
| الظل غير مرئي في Word | لون الظل يطابق الخلفية (مثلاً أبيض على أبيض) | اختر لونًا متباينًا أو زد الضبابية |
| الإزاحات كبيرة جدًا | يتحرك الظل خارج الصفحة، فيظهر مقطوعًا | حافظ على الإزاحات أقل من 10 pt لأحجام الصفحات القياسية |
| فشل الحفظ مع `PermissionError` | الملف مفتوح في Word أثناء تشغيل السكريبت | أغلق الملف أو احفظه في مسار مختلف |

## مثال كامل يعمل (جاهز للنسخ واللصق)

```python
import aspose.words as aw

# 1️⃣ Create a blank Word document
doc = aw.Document()

# 2️⃣ Insert a rectangle shape
shape = aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
shape.width = 200
shape.height = 100
shape.left = 100
shape.top = 100

first_section = doc.first_section
first_paragraph = first_section.body.first_paragraph
if first_paragraph is None:
    first_paragraph = aw.Paragraph(doc)
    first_section.body.append_child(first_paragraph)

first_paragraph.append_child(shape)

# 3️⃣ Enable shadow
shape.shadow = aw.drawing.Shadow()

# 4️⃣ Configure blur, offset, and color
shape.shadow.blur = 5.0
shape.shadow.offset_x = 2.0
shape.shadow.offset_y = 2.0
shape.shadow.color = aw.drawing.Color.black   # Change to any color you like

# 5️⃣ Save the result
output_path = "ShadowedShape.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

شغّل السكريبت، افتح الملف المُولد، وسترى المستطيل المظلّل—دليل على أنك نجحت في **إنشاء مستند Word فارغ**، **إضافة ظل إلى الشكل**، و**تطبيق لون الظل**.

## الخطوات التالية والمواضيع ذات الصلة

- **تنسيق النص** – تعلّم كيفية إضافة فقرات منسقة جنبًا إلى جنب مع الأشكال.  
- **أشكال متعددة** – حلقة عبر قائمة من الأشكال وأضف لكل منها ظلًا فريدًا.  
- **التصدير إلى PDF** – تحويل DOCX إلى PDF مع الحفاظ على تأثيرات الظل (`doc.save("output.pdf")`).  
- **الألوان الديناميكية** – سحب ألوان العلامة التجارية من ملف إعدادات وتطبيقها برمجيًا.

كل ما سبق يبني على المفاهيم الأساسية التي غطيناها هنا، لذا لا تتردد في التجربة. كلما لعبت أكثر مع Aspose.Words، كلما أدركت مرونتها في أتمتة المستندات.

---

**باختصار:** الآن تعرف كيف **تنشئ مستند Word فارغ**، **تضيف ظلًا إلى الشكل**، وتفهم تفاصيل **كيفية إضافة الظل** (الضبابية، الإزاحة)، وتطبق **لون الظل** بثقة للحصول على مظهر مصقول. جرّبه في مشروع التقارير التالي—لا مزيد من المستطيلات الباهتة.

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}