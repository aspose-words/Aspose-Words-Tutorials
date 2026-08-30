---
category: general
date: 2026-07-20
description: إنشاء مستند Word فارغ باستخدام Aspose.Words وإضافة ظل إلى الشكل. تعلّم
  كيفية تعديل عتمة الظل والشفافية في بضع خطوات فقط.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add shadow to shape
- add shadow effect
- change shadow transparency
- change shadow opacity
language: ar
lastmod: 2026-07-20
og_description: إنشاء مستند Word فارغ باستخدام Aspose.Words وإضافة تأثير ظل إلى شكل.
  تغيير شفافية الظل والشفافية مع أمثلة شفرة واضحة.
og_image_alt: Screenshot showing a Word document with a shape that has a semi‑transparent
  shadow
og_title: إنشاء مستند Word فارغ وإضافة ظل إلى الشكل – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Create blank Word document with Aspose.Words and add shadow to shape.
    Learn how to change shadow opacity and transparency in just a few steps.
  headline: Create Blank Word Document and Add Shadow to Shape – Full Tutorial
  type: TechArticle
- description: Create blank Word document with Aspose.Words and add shadow to shape.
    Learn how to change shadow opacity and transparency in just a few steps.
  name: Create Blank Word Document and Add Shadow to Shape – Full Tutorial
  steps:
  - name: Expected Output
    text: When you open **ShadowedShape.docx**, you should see a rectangle with a
      gray, semi‑transparent shadow that has a gentle blur. The shadow will be offset
      slightly down and to the right, giving the illusion that the shape is lifted
      off the page.
  - name: What if the document already contains multiple shapes?
    text: 'The current script grabs the *first* shape (`index 0`). To target a specific
      shape, change the index or iterate over all shapes:'
  - name: Can I change the shadow color?
    text: 'Absolutely. Shadow color is another property:'
  - name: How do I make the shadow offset differently?
    text: 'Adjust `distance_x` and `distance_y`:'
  - name: Does this work with older Word versions?
    text: Aspose.Words writes the modern OOXML format (`.docx`). Word 2007+ can open
      it without issues. For legacy `.doc` files, call `doc.save("file.doc", aw.SaveFormat.DOC)`—the
      shadow properties will still be preserved.
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
- Word Shapes
title: إنشاء مستند Word فارغ وإضافة ظل إلى الشكل – دليل كامل
url: /ar/python/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-tuto/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word فارغ وإضافة ظل إلى الشكل – دليل كامل

هل احتجت يومًا إلى **إنشاء مستند Word فارغ** ثم جعل شكل يبرز بظل خفيف؟ لست وحدك. في العديد من التقارير، النشرات، أو لوحات التحكم الداخلية يمكن للعمق البسيط أن يحول مستطيلًا مسطحًا إلى إشارة بصرية تجذب الانتباه.  

في هذا الدليل سنستعرض كيفية إنشاء ملف Word جديد باستخدام Aspose.Words for Python، استخراج الشكل الأول، ثم **إضافة ظل إلى الشكل** مع تعديل الشفافية والطمس. في النهاية ستحصل على مستند يبدو مصقولًا—دون الحاجة إلى تعديل يدوي.

> **ما ستحصل عليه** – سكريبت كامل قابل للتنفيذ، شرح *لماذا* كل سطر مهم، ونصائح للتعامل مع المستندات التي لا تحتوي على شكل مسبقًا.

## المتطلبات المسبقة

- Python 3.8+ مثبت (أي نسخة حديثة تعمل)
- Aspose.Words for Python عبر `pip install aspose-words`
- إلمام أساسي بـ Python ومفهوم “الشكل” في Word (مثل مربع النص، الصورة، أو الشكل التلقائي)

لا توجد مكتبات أخرى مطلوبة؛ الكود مستقل بذاته.

## الخطوة 1: إنشاء مستند Word فارغ باستخدام Aspose.Words

أولًا، نحتاج إلى لوحة قماش نظيفة. Aspose.Words يجعل ذلك سهلًا—فقط أنشئ كائن `Document`.

```python
import aspose.words as aw

# Step 1: Create a new blank document
doc = aw.Document()
print("✅ Blank Word document created.")
```

*لماذا هذا مهم*: فئة `Document` هي نقطة الدخول لكل عملية. بدءًا بمستند جديد يضمن عدم وجود تنسيقات مخفية قد تسبب مفاجآت لاحقًا.

## الخطوة 2: إدراج شكل تجريبي (لأننا نحتاج شيء نضيف له الظل)

إذا شغّلت السكريبت على ملف فارغ ستواجه مشكلة عند محاولة جلب شكل—فليس هناك أي شكل. لنضيف مستطيلًا بسيطًا حتى تكون الخطوات التالية لها هدف.

```python
# Step 2: Add a rectangle shape to the first page
builder = aw.DocumentBuilder(doc)
builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
print("🔲 Rectangle shape inserted.")
```

> **نصيحة احترافية**: عدّل قيم العرض/الارتفاع (200, 100) لتتناسب مع احتياجات التصميم الخاصة بك. الأشكال الأكبر تُظهر الظلال بوضوح أكبر.

## الخطوة 3: استرجاع أول شكل في المستند

الآن بعد أن لدينا شكلًا، يمكننا سحبها بأمان. طريقة `get_child` تتجول في شجرة العقد وتعيد أول عقدة من النوع المطلوب.

```python
# Step 3: Retrieve the first shape (index 0) – true = deep search
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

if shape is None:
    raise ValueError("No shape found in the document.")
print(f"🕵️ Retrieved shape of type: {shape.shape_type}")
```

*لماذا نتحقق من `None`*: في سيناريوهات العالم الحقيقي قد يتم إنشاء المستند في مكان آخر، وغياب الشكل سيتسبب بخطأ `AttributeError` غير واضح. رمي استثناء واضح يوفر وقت التصحيح.

## الخطوة 4: إضافة تأثير الظل – تغيير شفافية الظل

الظل ليس مجرد زخرفة بصرية؛ يمكنه أن يعكس التسلسل الهرمي. لنجعله شبه شفاف بتعيين الشفافية إلى 75 %.

```python
# Step 4: Set shadow opacity (0.0 = fully transparent, 1.0 = fully opaque)
shape.shadow.opacity = 0.75
print(f"🌫️ Shadow opacity set to {shape.shadow.opacity}")
```

**فهم الشفافية**: القيمة عدد عشري بين 0 و 1. الأرقام الأقل تجعل الظل يختفي في الخلفية، والأرقام الأعلى تجعله يبرز. لمعظم المستندات الشبيهة بواجهات المستخدم، يتراوح 0.5–0.8 طبيعيًا.

## الخطوة 5: تعريف طمس الظل – تغيير شفافية الظل

نصف قطر الطمس يتحكم في مدى نعومة حافة الظل. نصف قطر أكبر ينتج تلاشيًا أهدأ، محاكياً انتشار الضوء الطبيعي.

```python
# Step 5: Define blur radius (in points) for a softer edge
shape.shadow.blur_radius = 8.0
print(f"🔍 Blur radius set to {shape.shadow.blur_radius} points")
```

*لماذا الطمس مهم*: الظل الحاد قد يبدو رخيصًا، بينما الطمس الخفيف يضيف عمقًا دون أن يغمر المحتوى.

## الخطوة 6: حفظ المستند والتحقق من النتيجة

أخيرًا، نكتب المستند إلى القرص. افتح ملف `.docx` الناتج في Word لتشاهد المستطيل مع ظله الجديد.

```python
output_path = "ShadowedShape.docx"
doc.save(output_path)
print(f"💾 Document saved as '{output_path}'. Open it in Word to see the effect.")
```

### النتيجة المتوقعة

عند فتح **ShadowedShape.docx**، يجب أن ترى مستطيلًا بظل رمادي شبه شفاف مع طمس خفيف. سيكون الظل مُزاحًا قليلًا إلى الأسفل وإلى اليمين، ما يعطي الانطباع بأن الشكل مرفوع عن الصفحة.

## الحالات الخاصة والأسئلة الشائعة

### ماذا لو كان المستند يحتوي بالفعل على عدة أشكال؟

السكريبت الحالي يلتقط *أول* شكل (`index 0`). لاستهداف شكل معين، غيّر الفهرس أو كرّر عبر جميع الأشكال:

```python
for i in range(doc.get_child_nodes(aw.NodeType.SHAPE, True).count):
    shp = doc.get_child(aw.NodeType.SHAPE, i, True)
    # Apply shadow settings to each shape
    shp.shadow.opacity = 0.6
    shp.shadow.blur_radius = 5.0
```

### هل يمكنني تغيير لون الظل؟

بالطبع. لون الظل هو خاصية أخرى:

```python
shape.shadow.color = aw.drawing.Color.black
```

### كيف أجعل إزاحة الظل مختلفة؟

عدّل `distance_x` و `distance_y`:

```python
shape.shadow.distance_x = 5   # shift right
shape.shadow.distance_y = 5   # shift down
```

### هل يعمل هذا مع إصدارات Word القديمة؟

Aspose.Words يكتب بصيغة OOXML الحديثة (`.docx`). يمكن لـ Word 2007 وما بعده فتحه دون مشاكل. بالنسبة للملفات القديمة `.doc`، استخدم `doc.save("file.doc", aw.SaveFormat.DOC)`—ستظل خصائص الظل محفوظة.

## ملخص السكريبت الكامل

بجمع كل ما سبق، إليك المثال الكامل الجاهز للتنفيذ:

```python
import aspose.words as aw

# Create a new blank document
doc = aw.Document()
print("✅ Blank Word document created.")

# Insert a rectangle shape (so we have something to shadow)
builder = aw.DocumentBuilder(doc)
builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
print("🔲 Rectangle shape inserted.")

# Retrieve the first shape in the document
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
if shape is None:
    raise ValueError("No shape found in the document.")
print(f"🕵️ Retrieved shape of type: {shape.shape_type}")

# Add shadow effect – change opacity
shape.shadow.opacity = 0.75
print(f"🌫️ Shadow opacity set to {shape.shadow.opacity}")

# Change shadow transparency – define blur radius
shape.shadow.blur_radius = 8.0
print(f"🔍 Blur radius set to {shape.shadow.blur_radius} points")

# Optional: tweak color and offset
shape.shadow.color = aw.drawing.Color.gray
shape.shadow.distance_x = 4
shape.shadow.distance_y = 4

# Save the document
output_path = "ShadowedShape.docx"
doc.save(output_path)
print(f"💾 Document saved as '{output_path}'. Open it in Word to see the effect.")
```

شغّل هذا السكريبت، افتح الملف المُولد، وسترى الشكل محاطًا بظل أنيق—ما يحتاجه أي تقرير مصقول.

## الخلاصة

الآن تعرف **كيفية إنشاء مستند Word فارغ** باستخدام Aspose.Words، إدراج شكل، و**إضافة ظل إلى الشكل** مع إتقان *تغيير شفافية الظل* و*تغيير طمس الظل*. الخطوات بسيطة، لكن الأثر البصري كبير.  

بعد ذلك، يمكنك استكشاف **إضافة تأثير الظل** للصور، تجربة قيم `blur_radius` مختلفة، أو دمج عدة أشكال في رسم مركب واحد. للمزيد من التفاصيل، راجع وثائق Aspose حول [تنسيق الشكل](https://docs.aspose.com/words/python-net/shape/) ودليل [أتمتة المستندات](https://docs.aspose.com/words/python-net/) العام.

هل جربت تعديلًا مختلفًا؟ اترك تعليقًا أدناه—مشاركة التجارب الواقعية تقوي المجتمع. Happy coding!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}