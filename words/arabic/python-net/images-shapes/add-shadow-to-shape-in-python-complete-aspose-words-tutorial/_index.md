---
category: general
date: 2026-06-08
description: أضف ظلًا إلى الشكل باستخدام Aspose.Words للبايثون وقم بتعيين لون تعبئة
  الشكل في بضع خطوات فقط. تعلّم سير العمل الكامل مع كود قابل للتنفيذ.
draft: false
keywords:
- add shadow to shape
- set shape fill color
- Aspose.Words Python shadow
- shape formatting Python
- PDF generation Aspose
language: ar
og_description: أضف ظلًا إلى الشكل باستخدام Aspose.Words للبايثون وقم بتعيين لون تعبئة
  الشكل فورًا. اتبع هذا الدليل خطوة بخطوة لإنشاء مخرجات PDF.
og_title: إضافة ظل إلى الشكل في بايثون – دليل Aspose.Words الكامل
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Add shadow to shape using Aspose.Words for Python and set shape fill
    color in just a few steps. Learn the full workflow with runnable code.
  headline: Add Shadow to Shape in Python – Complete Aspose.Words Tutorial
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python and set shape fill
    color in just a few steps. Learn the full workflow with runnable code.
  name: Add Shadow to Shape in Python – Complete Aspose.Words Tutorial
  steps:
  - name: Create the Document and Builder
    text: '```python import aspose.words as aw from aspose.words.drawing import ShadowEffect,
      ShadowType, Color'
  - name: Insert a Rectangle Shape and Set Its Fill Color
    text: '```python # Insert a rectangle shape of width 200 points and height 100
      points. rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE,
      200, 100)'
  - name: Define the Shadow Effect
    text: '```python # Create a new shadow effect object. shape_shadow = ShadowEffect()
      shape_shadow.type = ShadowType.OUTER # outer shadow around the shape shape_shadow.blur_radius
      = 10.0 # softer edges shape_shadow.distance = 5.0 # how far the shadow sits
      from the shape shape_shadow.direction = 45 # angle in'
  - name: Apply the Shadow to the Shape
    text: '```python # Attach the shadow effect to the rectangle. rectangle_shape.shadow_effect
      = shape_shadow ```'
  - name: Save the Document as PDF
    text: '```python # Choose a folder you have write access to. output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
      doc.save(output_path) print(f"Document saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
title: إضافة ظل إلى الشكل في بايثون – دليل Aspose.Words الكامل
url: /ar/python/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إضافة ظل إلى الشكل في بايثون – دليل Aspose.Words الكامل

هل تساءلت يومًا كيف **تضيف ظلًا إلى الشكل** عند إنشاء مستند باستخدام Aspose.Words للبايثون؟ لست وحدك. سواء كنت تبني قالب تقرير، أو نشرة تسويقية، أو مخططًا تقنيًا، فإن الظل الخفيف يمكن أن يجعل المستطيل يبرز ويظهر أكثر احترافية.  

في هذا الدليل سنوضح لك أيضًا **كيفية تعيين لون تعبئة الشكل**، بحيث تحصل على مستطيل مُصمم بالكامل جاهز لتصدير PDF. الحل بسيط، والكود جاهز للتنفيذ، والشرح وراء كل سطر موضح باللغة الإنجليزية البسيطة.

## ما يغطيه هذا الدرس

- تهيئة مستند Aspose.Words و الـ Builder.  
- إدراج شكل مستطيل و **تعيين لون تعبئته**.  
- تعريف وتطبيق **تأثير الظل** على ذلك الشكل.  
- حفظ النتيجة كملف PDF.  
- مثال كامل قابل للتنفيذ بالإضافة إلى نصائح لتجنب المشكلات الشائعة.

بنهاية المقال ستتمكن من إدراج مستطيل مُصمم في أي ملف Word أو PDF باستخدام بضع أسطر فقط من بايثون. دون أدوات خارجية، دون تخمين.

> **المتطلبات المسبقة** – تحتاج إلى Python 3.7+ وحزمة `aspose-words` (`pip install aspose-words`). أي بيئة تطوير متكاملة أو محرر نصوص تختاره يكفي؛ Visual Studio Code يعمل بشكل ممتاز.

---

## إضافة ظل إلى الشكل – خطوة بخطوة

فيما يلي نقسم العملية إلى أجزاء منطقية. كل خطوة تتضمن الكود الدقيق الذي تحتاجه، شرحًا مختصرًا لـ *سبب أهميتها*، ونصيحة سريعة لتجنب الوقوع في مشاكل لاحقًا.

### الخطوة 1: إنشاء المستند والـ Builder

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowType, Color

# Create a new, empty document.
doc = aw.Document()

# DocumentBuilder gives us a convenient way to add content.
builder = aw.DocumentBuilder(doc)
```

**لماذا هذا مهم:** `Document` هو الحاوية لكل شيء — الصفحات، الأنماط، الصور، والأشكال. `DocumentBuilder` هو الـ API عالي المستوى الذي يتيح لنا وضع الكائنات دون القلق بشأن شجرة العقد منخفضة المستوى.

### الخطوة 2: إدراج شكل مستطيل وتعيين لون تعبئته

```python
# Insert a rectangle shape of width 200 points and height 100 points.
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Set the interior color of the shape.
rectangle_shape.fill_color = Color.BLUE   # <-- set shape fill color
```

**لماذا هذا مهم:** الشكل يعمل كقماش لظلنا. من خلال **تعيين لون تعبئة الشكل** نتأكد أن المستطيل ليس مجرد صندوق شفاف؛ بل يصبح عنصرًا مرئيًا يمكن للظل أن يبرزّه. يمكنك استبدال `Color.BLUE` بأي قيمة RGB أو حتى تدرج لوني إذا كنت تحتاج إلى مزيد من التألق.

> **نصيحة احترافية:** إذا كنت تخطط لإعادة استخدام نفس اللون عبر العديد من الأشكال، احفظه في متغير (`my_fill = Color.from_argb(0, 120, 200, 255)`) وأعد استخدام هذا المرجع.

### الخطوة 3: تعريف تأثير الظل

```python
# Create a new shadow effect object.
shape_shadow = ShadowEffect()
shape_shadow.type = ShadowType.OUTER          # outer shadow around the shape
shape_shadow.blur_radius = 10.0               # softer edges
shape_shadow.distance = 5.0                   # how far the shadow sits from the shape
shape_shadow.direction = 45                   # angle in degrees (45° = diagonal)
shape_shadow.color = Color.from_argb(128, 0, 0, 0)  # semi‑transparent black
```

**لماذا هذا مهم:** الظل ليس مجرد خدعة بصرية؛ إنه ينقل العمق والهرمية. `blur_radius` يتحكم في النعومة، `distance` يحدد الإزاحة، و `direction` يسمح لك بمحاكاة مصدر الضوء. عدّل هذه القيم لتتناسب مع لغة التصميم الخاصة بك.

### الخطوة 4: تطبيق الظل على الشكل

```python
# Attach the shadow effect to the rectangle.
rectangle_shape.shadow_effect = shape_shadow
```

**لماذا هذا مهم:** حتى يتم تنفيذ هذا السطر، يظل الشكل مسطحًا. تعيين `shadow_effect` يخبر Aspose.Words بأن يرسم المستطيل مع الظل المحدد عند حفظ المستند.

### الخطوة 5: حفظ المستند كملف PDF

```python
# Choose a folder you have write access to.
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

**لماذا هذا مهم:** حفظ الملف كـ PDF يثبت التنسيق البصري، مما يجعل الظل يظهر بالضبط كما صممته. يمكنك أيضًا حفظه كـ `.docx` إذا كنت تحتاج إلى تعديل لاحقًا — Aspose.Words يتعامل مع كلا الصيغتين بسلاسة.

---

## تعيين لون تعبئة الشكل – تخصيص المظهر

إذا كنت تحتاج إلى درجة لون مختلفة، استبدل تعيين `Color.BLUE` بأي من الأمثلة التالية:

```python
# Solid RGB color
rectangle_shape.fill_color = Color.from_argb(255, 255, 165, 0)   # orange

# Semi‑transparent fill
rectangle_shape.fill_color = Color.from_argb(128, 0, 128, 0)    # 50% transparent green
```

> **لماذا قد تحتاج هذا:** تعبئة شبه شفافة مع ظل يمكن أن تخلق تأثير "زجاجي" شائع في نماذج واجهات المستخدم الحديثة.

---

## مثال كامل يعمل

إليك البرنامج الكامل في كتلة واحدة. انسخه والصقه في ملف اسمه `shadow_shape.py` وشغّله — بافتراض أنك قمت بتثبيت `aspose-words`.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowType, Color

# 1️⃣ Create document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2️⃣ Insert rectangle and set fill color
rect = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
rect.fill_color = Color.BLUE          # set shape fill color

# 3️⃣ Configure shadow
shadow = ShadowEffect()
shadow.type = ShadowType.OUTER
shadow.blur_radius = 10.0
shadow.distance = 5.0
shadow.direction = 45
shadow.color = Color.from_argb(128, 0, 0, 0)

# 4️⃣ Apply shadow
rect.shadow_effect = shadow

# 5️⃣ Save as PDF
output = "ShadowShape.pdf"
doc.save(output)
print(f"✅ PDF generated: {output}")
```

**الناتج المتوقع:** افتح `ShadowShape.pdf` وسترى مستطيلًا أزرق مع ظل أسود ناعم مائل إلى الأسفل‑اليمين. يجب أن يبدو الظل مشوشًا قليلًا، مما يمنح الشكل مظهرًا مرتفعًا.

---

## المشكلات الشائعة والنصائح الاحترافية

| المشكلة | سبب حدوثه | الحل |
|------|----------------|-----|
| **الظل غير مرئي** | تعبئة الشكل شفافة بالكامل أو عارض الـ PDF يعطل الظلال. | تأكد من أن `fill_color` غير شفاف (`alpha = 255`) أو عدل شفافية `color` للظل. |
| **خطأ في مسار الملف** | `YOUR_DIRECTORY` غير موجود أو لا تملك صلاحية الكتابة. | استخدم `os.makedirs("YOUR_DIRECTORY", exist_ok=True)` قبل `doc.save`. |
| **استيراد غير صحيح** | محاولة استيراد `ShadowEffect` من وحدة فرعية خاطئة. | استورد بالضبط كما هو موضح: `from aspose.words.drawing import ShadowEffect, ShadowType, Color`. |
| **لون غير متوقع** | استخدام `Color.from_argb` بترتيب خاطئ (alpha, red, green, blue). | تذكر الترتيب: **alpha**, **red**, **green**, **blue**. |

---

## الخطوات التالية – توسيع مجموعة أدوات الشكل

الآن بعد أن عرفت كيف **تضيف ظلًا إلى الشكل** و **تحدد لون تعبئة الشكل**، يمكنك استكشاف:

- **تعبئات تدرجية** (`LinearGradientBrush`) لخلفيات أغنى.  
- **ظلال متعددة** (داخلية + خارجية) عن طريق ربط كائنات `ShadowEffect`.  
- **أنواع أشكال أخرى** (`Ellipse`, `Polygon`) لإنشاء أيقونات أو عناصر مخطط تدفق.  
- **دمج الـ PDF** في استجابة ويب أو مرفق بريد إلكتروني باستخدام Flask أو Django.

كل من هذه المواضيع يبني على نفس المفاهيم الأساسية التي تم تغطيتها هنا، لذا ستشعر بالراحة.

---

## الخلاصة

لقد استعرضنا العملية الكاملة **لإضافة ظل إلى الشكل** في Aspose.Words للبايثون مع **تحديد لون تعبئة الشكل**. من إنشاء المستند إلى تصدير PDF، الكود مستقل وجاهز للاستخدام في الإنتاج.  

لا تتردد في تعديل نصف قطر التشويش، المسافة، أو اللون لتتناسب مع إرشادات علامتك التجارية. إذا واجهت حالة خاصة أو لديك طلب ميزة، اترك تعليقًا أدناه — برمجة سعيدة!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة قابلة للتنفيذ مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إعداد ترخيص Aspose.Words في بايثون](/words/english/python-net/getting-started/aspose-words-license-python-setup/)
- [إنشاء شكل مستطيل في Word باستخدام Aspose.Words – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [دروس ظل الشكل في Aspose.Words – إضافة ظل إلى شكل Word بلغة C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}