---
category: general
date: 2026-06-30
description: أضف ظلًا إلى الشكل باستخدام Aspose.Words للبايثون. تعلّم كيفية ضبط مسافة
  الظل، وتخصيص الضبابية، وحفظ ملف PDF يحتوي على ظل الشكل بسرعة.
draft: false
keywords:
- add shadow to shape
- how to set shadow distance
- how to add shape shadow
- Aspose.Words Python shadow
- shape formatting Python
language: ar
og_description: إضافة ظل إلى الشكل في مستند Word باستخدام Aspose.Words للغة Python.
  يوضح هذا البرنامج التعليمي كيفية ضبط مسافة الظل، والضبابية، واللون، ثم حفظه كملف
  PDF.
og_title: إضافة ظل إلى الشكل في بايثون – دليل Aspose.Words الكامل
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Add shadow to shape using Aspose.Words for Python. Learn how to set
    shadow distance, customize blur, and save a PDF with shape shadow quickly.
  headline: Add Shadow to Shape in Python with Aspose.Words – Full Guide
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python. Learn how to set
    shadow distance, customize blur, and save a PDF with shape shadow quickly.
  name: Add Shadow to Shape in Python with Aspose.Words – Full Guide
  steps:
  - name: What if I need a different shape?
    text: Replace `aw.drawing.ShapeType.RECTANGLE` with any other enum value, e.g.,
      `aw.drawing.ShapeType.ELLIPSE`. The same shadow properties apply—no extra code
      needed.
  - name: Can I apply a shadow to multiple shapes at once?
    text: 'Yes. Loop over the shapes you create and configure each `shadow_format`
      individually. Here’s a quick snippet:'
  - name: How do I change the shadow’s opacity?
    text: 'Use the `shadow.transparency` property (0 = opaque, 1 = fully transparent):'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: إضافة ظل إلى الشكل في بايثون باستخدام Aspose.Words – دليل كامل
url: /ar/python/images-shapes/add-shadow-to-shape-in-python-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إضافة ظل إلى الشكل في بايثون باستخدام Aspose.Words – دليل كامل

إضافة ظل إلى الشكل في مستند Word باستخدام Aspose.Words للبايثون أسهل مما تتصور. إذا تساءلت يومًا **كيف تحدد مسافة الظل** أو **كيف تضيف ظلًا للشكل** للحصول على مظهر مصقول، فهذا الدليل يغطي كل ما تحتاجه.

في الدقائق القليلة القادمة سنستعرض كل شيء: من إنشاء مستند جديد، إدراج مستطيل، تعديل خصائص الظل، إلى حفظ ملف PDF يعرض التأثير. في النهاية ستتمكن من إضافة ظل إلى أي شكل—مستطيل، إهليلج، أو رسم مخصص—دون الحاجة للغوص في وثائق الـ API.

> **المتطلبات المسبقة** – يجب أن يكون لديك Python 3.7+ مثبتًا، ورخصة Aspose.Words للبايثون (أو نسخة تجريبية مجانية)، ومعرفة أساسية ببرمجة بايثون. لا توجد مكتبات خارجية أخرى مطلوبة.

---

## إضافة ظل إلى الشكل – نظرة عامة خطوة بخطوة

فيما يلي خريطة سريعة لما سنحققه:

1. **إنشاء مستند جديد** واستخدام `DocumentBuilder` لتعديله.  
2. **إدراج شكل مستطيل** بالحجم الذي تحتاجه.  
3. **تمكين وتخصيص الظل** – هنا يبرز المفتاح الأساسي.  
4. **حفظ المستند** كملف PDF يحتفظ بظل الشكل.

كل خطوة مفصلة في قسمها الخاص، بحيث يمكنك نسخ‑لصق الشيفرات مباشرةً إلى بيئة التطوير الخاصة بك.

---

## الخطوة 1: تهيئة المستند والبنّاء

أولًا وقبل كل شيء—بدون `Document` لا شيء لتعمل عليه. الـ `DocumentBuilder` هو فرشاتك.

```python
import aspose.words as aw

# Create a new, empty Word document
document = aw.Document()

# Attach a builder to the document for easy editing
builder = aw.DocumentBuilder(document)
```

*لماذا هذا مهم*: كائن `Document` يمثل الملف بالكامل، بينما يبسط `DocumentBuilder` إدراج النصوص والجداول والأشكال. فكر في الـ builder كالمؤشر الذي يمكنك تحريكه في جميع أنحاء الصفحة.

---

## الخطوة 2: إدراج شكل مستطيل

الآن سنضيف مستطيلًا—قماشنا لتأثير الظل. يمكنك استبدال `RECTANGLE` بـ `ELLIPSE` أو `STAR` أو أي قيمة أخرى من `ShapeType` إذا احتجت إلى شكل مختلف.

```python
# Insert a rectangle with width=200pt and height=100pt
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

*نصيحة احترافية*: الأبعاد بوحدات النقاط (1 pt ≈ 1/72 إنش). اضبطها لتناسب تخطيطك؛ الظل سيتكيف تلقائيًا.

---

## كيفية تعيين مسافة الظل

تحدد **المسافة** للظل إلى أي مدى يظهر بعيدًا عن الشكل. المسافة الأكبر تحاكي مصدر ضوء أبعد، بينما القيمة الأصغر تعطي رفعًا خفيفًا.

```python
# Access the shadow format of the shape
shadow = rectangle_shape.shadow_format

# Make the shadow visible
shadow.visible = True

# Set the distance (in points) from the shape
shadow.distance = 4.0          # <-- this is the "how to set shadow distance" part
```

> **ملاحظة**: تعمل المسافة مع `angle`. تغيير الزاوية يدور الظل حول الشكل، بينما `distance` يدفعه إلى الخارج.

---

## كيفية إضافة ظل للشكل – تخصيص الضبابية، اللون، والزاوية

إضافة الظل ليست مجرد تشغيله؛ غالبًا ما تريد تعديل الضبابية، اللون، والاتجاه للحصول على تأثير واقعي.

```python
# Define how blurry the shadow should be (larger = softer)
shadow.blur_radius = 5.0       # Soft edge for a natural look

# Choose the direction (in degrees). 45° points down‑right.
shadow.angle = 45

# Set the shadow color – black works for most cases
shadow.color = aw.drawing.Color.black
```

*لماذا هذه الإعدادات؟*  
- **نصف قطر الضبابية** ينعّم الحافة، مما يمنع ظهور silhouette حاد.  
- **الزاوية** تحاكي مصدر الضوء؛ 45° هي القيمة الافتراضية الشائعة التي تبدو متوازنة.  
- **اللون** يمكن أن يكون أي كائن `Color`؛ جرّب `Color.gray` لتأثير أهدأ.

---

## الخطوة 4: حفظ المستند كملف PDF

بمجرد أن يصبح الشكل وظله جاهزين، يصبح حفظ النتيجة أمرًا سهلًا. Aspose.Words يتولى تحويل الملف إلى PDF تلقائيًا، مع الحفاظ على الدقة البصرية.

```python
# Save the document to a PDF file (adjust the path as needed)
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
document.save(output_path)
print(f"Document saved to {output_path}")
```

*الناتج المتوقع*: افتح ملف `ShadowShape.pdf` المُولَّد. سترى صفحة واحدة تحتوي على مستطيل بحجم 200 × 100 pt، وظله يبعد 4 pt بزاوية 45°، مع ضبابية 5 pt. يجب أن يظهر الظل كهالة رمادية‑سوداء خفيفة تحيط بالشكل.

---

## أسئلة شائعة وحالات خاصة

### ماذا لو احتجت إلى شكل مختلف؟

استبدل `aw.drawing.ShapeType.RECTANGLE` بأي قيمة أخرى من الـ enum، مثل `aw.drawing.ShapeType.ELLIPSE`. نفس خصائص الظل تنطبق—بدون الحاجة إلى كود إضافي.

### هل يمكن تطبيق الظل على عدة أشكال في آن واحد؟

نعم. يمكنك حلقة (loop) عبر الأشكال التي تنشئها وتكوين كل `shadow_format` على حدة. إليك مقتطفًا سريعًا:

```python
for shape_type in [aw.drawing.ShapeType.RECTANGLE, aw.drawing.ShapeType.ELLIPSE]:
    shp = builder.insert_shape(shape_type, 150, 80)
    shp.shadow_format.visible = True
    shp.shadow_format.distance = 3.0
    shp.shadow_format.blur_radius = 4.0
```

### كيف أغيّر شفافية الظل؟

استخدم الخاصية `shadow.transparency` (0 = معتم، 1 = شفاف تمامًا):

```python
shadow.transparency = 0.3   # 30 % transparent
```

---

## مثال كامل يعمل

فيما يلي السكربت الكامل—انسخه، عدّل مسار المخرجات، ثم شغّله. لا توجد أجزاء مفقودة.

```python
import aspose.words as aw

# 1️⃣ Create a new document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert a rectangle shape (200 × 100 pt)
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Enable and configure the shadow (add shadow to shape)
shadow = rectangle_shape.shadow_format
shadow.visible = True                # Show the shadow
shadow.blur_radius = 5.0             # Soft edges
shadow.distance = 4.0                # How far the shadow lies from the shape
shadow.angle = 45                    # Direction of the light source
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.0            # Fully opaque (optional)

# 4️⃣ Save as PDF
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
document.save(output_path)
print(f"PDF with shape shadow saved at: {output_path}")
```

شغّل السكربت، ثم افتح ملف PDF الناتج. ستلاحظ المستطيل مع ظل واضح ومُزاح—تمامًا ما يُعد به **add shadow to shape**.

---

## الخلاصة

لقد أظهرنا لك كيفية **إضافة ظل إلى الشكل** في مستند Word باستخدام Aspose.Words للبايثون، مع تغطية الخطوات الأساسية لـ **تحديد مسافة الظل**، تخصيص الضبابية، الزاوية، واللون، وأخيرًا تصدير PDF يحافظ على التأثير. هذه التقنية تعمل مع أي نوع من الأشكال، ويمكنك توسيعها باستخدام حلقات، تعديل الشفافية، أو حتى ظلال متدرجة.

هل أنت مستعد للتحدي التالي؟ جرّب دمج عدة ظلال، تراكب الأشكال، أو إنشاء تقرير حيث يحصل كل رسم بياني على ظل مميز. التجربة ستُرسّخ المفاهيم وتكشف عن إمكانيات جديدة لأتمتة المستندات.

إذا وجدت هذا الدليل مفيدًا، لا تتردد في مشاركته، وضع نجمة على مستودع Aspose.Words، أو ترك تعليق بنصائحك الخاصة لتعديل الظلال. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تُبني على التقنيات التي تم استعراضها في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}