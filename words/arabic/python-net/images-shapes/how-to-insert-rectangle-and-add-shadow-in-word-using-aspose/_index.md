---
category: general
date: 2026-05-30
description: كيفية إدراج مستطيل وإضافة ظل في Word باستخدام Aspose – دليل خطوة بخطوة
  بلغة Python لإنشاء مستند Word مع تأثير ظل الشكل.
draft: false
keywords:
- how to insert rectangle
- add shadow to shape
- how to add shape shadow
- apply shadow effect word
- create word document aspose
language: ar
og_description: كيفية إدراج مستطيل وإضافة ظل في Word باستخدام Aspose – تعلم إنشاء
  مستند Word بتأثير ظل الشكل باستخدام Python.
og_title: كيفية إدراج مستطيل وإضافة ظل في Word باستخدام Aspose
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: How to insert rectangle and add shadow in Word using Aspose – a step‑by‑step
    Python guide to create a Word document with shape shadow effect.
  headline: How to insert rectangle and add shadow in Word using Aspose
  type: TechArticle
- description: How to insert rectangle and add shadow in Word using Aspose – a step‑by‑step
    Python guide to create a Word document with shape shadow effect.
  name: How to insert rectangle and add shadow in Word using Aspose
  steps:
  - name: What each property does
    text: '| Property | Effect | Typical Range | |----------|--------|---------------|
      | `visible` | Turns the shadow on/off | `True` / `False` | | `distance` | How
      far the shadow sits from the shape | 2 – 10 pts | | `blur` | Softness of the
      shadow edges | 4 – 12 pts | | `color` | Shadow hue; dark gray is a sa'
  - name: Adding Multiple Shapes
    text: If you need more than one rectangle, simply repeat the `insert_shape` call.
      Remember to move the builder’s cursor (`builder.move_to(shape)`) or adjust `shape.left`/`shape.top`
      to avoid overlap.
  - name: Changing the Shape Type
    text: While this guide focuses on rectangles, the same pattern works for ovals,
      stars, or custom free‑form shapes. Replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`,
      `ShapeType.CLOUD`, etc., and the shadow settings remain identical.
  - name: Saving to Other Formats
    text: 'Aspose.Words can export to PDF, PNG, or even XPS with a single line:'
  - name: Handling Large Documents
    text: When generating massive reports, consider calling `doc.update_page_layout()`
      after inserting all shapes. This forces a layout pass and can improve performance
      when you later convert to PDF.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word Automation
title: كيفية إدراج مستطيل وإضافة ظل في Word باستخدام Aspose
url: /ar/python/images-shapes/how-to-insert-rectangle-and-add-shadow-in-word-using-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إدراج مستطيل وإضافة ظل في Word باستخدام Aspose

هل تساءلت يومًا **كيفية إدراج مستطيل** في ملف Word دون فتح الواجهة؟ لست وحدك. يحتاج العديد من المطورين إلى إنشاء تقارير، فواتير، أو شهادات بسرعة، ورسم مستطيل بسيط بظل جميل يمكن أن يجعل المخرجات تبدو مصقولة. في هذا الدرس سنستعرض الخطوات الدقيقة لإنشاء مستند Word، وإضافة شكل مستطيل، وتطبيق ظل واقعي باستخدام Aspose.Words للغة Python.

سنغطي كل شيء من إعداد حزمة Aspose إلى تعديل مسافة الظل، الضبابية، والشفافية. في النهاية ستحصل على قطعة شفرة قابلة لإعادة الاستخدام يمكنك وضعها في أي خط أنابيب أتمتة. لا سحر، فقط شفرة واضحة وبعض النصائح العملية.

## المتطلبات المسبقة

- Python 3.8+ مثبت (الكود يعمل على 3.9، 3.10، والإصدارات الأحدث)
- رخصة نشطة لـ Aspose.Words للغة Python أو مفتاح تقييم مجاني
- حزمة `aspose-words` مثبتة عبر `pip install aspose-words`
- مجلد قابل للكتابة حيث سيتم حفظ **create word document aspose** المُولد

هذا كل شيء—لا ملفات DLL إضافية، لا تفاعل COM، فقط Python نقي.

## الخطوة 1: تهيئة المستند (How to create word document aspose)

أولًا وقبل كل شيء: تحتاج إلى كائن `Document` جديد. فكر فيه كقماش فارغ. الكود التالي ينشئ المستند و`DocumentBuilder` الذي سيسمح لنا بإدراج الأشكال.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

*لماذا هذا مهم:* يمنحك `DocumentBuilder` واجهة برمجة تطبيقات عالية المستوى لإضافة فقرات، جداول، و—نعم—أشكال دون التعامل مع شجرات العقد منخفضة المستوى. إذا تخطيت الـ builder وتعاملت مع العقد مباشرة، ستحصل على شفرة مطولة يصعب صيانتها.

## الخطوة 2: إدراج المستطيل (how to insert rectangle)

الآن نقوم فعليًا **how to insert rectangle**. تعتبر Aspose.Words المستطيل كنوع شكل عام. تحدد العرض والارتفاع بالنقاط (1 نقطة ≈ 1/72 إنش). لا تتردد في تعديل القيم لتناسب تخطيطك.

```python
# Step 2: Insert a rectangle shape of the desired size
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

> **نصيحة احترافية:** إذا كنت بحاجة إلى وضع المستطيل في موقع محدد على الصفحة، قم بتعيين `shape.left` و `shape.top` بعد الإدراج. هذا يمنحك تحكمًا دقيقًا على مستوى البكسل.

## الخطوة 3: الوصول إلى تنسيق ظل الشكل (add shadow to shape)

اللمسة البصرية للشكل تكمن في `ShadowFormat`. من خلال استرجاعه، نحصل على إمكانية الوصول إلى كل خاصية تحدد مظهر الظل.

```python
# Step 3: Access the shape's shadow format
shadow = shape.shadow_format
```

في هذه المرحلة يكون الظل غير مرئي—فكر فيه كطبقة مخفية تنتظر تعليماتك.

## الخطوة 4: ضبط الظل (how to add shape shadow, apply shadow effect word)

هنا يحدث السحر. سنقوم بتفعيل الظل وتعديل مظهره. القيم أدناه تنتج ظلًا ناعمًا مائلًا يعمل جيدًا لمعظم المستندات، لكن يمكنك التجربة.

```python
# Step 4: Make the shadow visible and configure its appearance
shadow.visible = True                # Show the shadow
shadow.distance = 5.0                # Distance from the shape (points)
shadow.blur = 8.0                    # Blur radius (points)
shadow.color = aw.Color.dark_grey   # Shadow color
shadow.opacity = 0.6                 # Opacity (0‑1)
shadow.angle = 45.0                  # Direction in degrees
```

### ما الذي تفعله كل خاصية

| الخاصية | التأثير | النطاق النموذجي |
|----------|--------|---------------|
| `visible` | تشغيل/إيقاف الظل | `True` / `False` |
| `distance` | المسافة بين الظل والشكل | 2 – 10 نقطة |
| `blur` | نعومة حواف الظل | 4 – 12 نقطة |
| `color` | لون الظل؛ الرمادي الداكن هو الافتراضي الآمن | أي `aw.Color` |
| `opacity` | الشفافية؛ 0 = غير مرئي، 1 = صلب | 0.3 – 0.8 للمظهر الخفيف |
| `angle` | اتجاه الضوء | 0 – 360° |

**لماذا تعديل هذه؟** يمكن لظل مضبوط جيدًا أن يجعل المستطيل المسطح يبدو مرتفعًا عن الصفحة، مضيفًا عمقًا دون أي صور. إذا ضبطت `opacity` عاليًا جدًا، سيظهر الظل قاسيًا؛ وإذا كان منخفضًا جدًا سيختفي.

## الخطوة 5: حفظ المستند (create word document aspose)

أخيرًا، احفظ الملف على القرص. يمكنك استخدام أي امتداد يدعمه Aspose.Words (`.docx`, `.pdf`, `.html`). في هذا الدرس سنستخدم `.docx`.

```python
# Step 5: Save the document with the shaped shadow
output_path = "output/ShapeWithShadow.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

افتح الملف الناتج في Microsoft Word، وسترى مستطيلًا واضحًا بظل خفيف—تمامًا ما تتوقعه من قالب مصمم بشكل احترافي.

![كيفية إدراج شكل مستطيل مع ظل باستخدام Aspose.Words](/images/rectangle-shadow.png){alt="كيفية إدراج شكل مستطيل مع ظل باستخدام Aspose.Words"}

*تُظهر لقطة الشاشة (أعلى) المستطيل مع الظل المطبق. لاحظ الضبابية اللطيفة وزاوية 45° التي تعطي مظهرًا طبيعيًا.*

## تنوعات شائعة وحالات حافة

### إضافة أشكال متعددة

إذا كنت بحاجة إلى أكثر من مستطيل واحد، ببساطة كرر استدعاء `insert_shape`. تذكر تحريك مؤشر الـ builder (`builder.move_to(shape)`) أو تعديل `shape.left`/`shape.top` لتجنب التداخل.

```python
# Example: Insert a second rectangle 200 points to the right
second_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
second_shape.left = shape.left + 200
second_shape.top = shape.top
```

### تغيير نوع الشكل

بينما يركز هذا الدليل على المستطيلات، يعمل النمط نفسه مع الأشكال البيضاوية، النجوم، أو الأشكال الحرة المخصصة. استبدل `ShapeType.RECTANGLE` بـ `ShapeType.OVAL`، `ShapeType.CLOUD`، إلخ، وستظل إعدادات الظل متطابقة.

### الحفظ بصيغ أخرى

يمكن لـ Aspose.Words تصدير إلى PDF، PNG، أو حتى XPS بسطر واحد:

```python
doc.save("output/ShapeWithShadow.pdf")
```

يتم الحفاظ على عرض الظل عبر الصيغ، لذا سيظهر ملف PDF الخاص بك تمامًا مثل ملف Word.

### التعامل مع المستندات الكبيرة

عند إنشاء تقارير ضخمة، فكر في استدعاء `doc.update_page_layout()` بعد إدراج جميع الأشكال. هذا يجبر عملية تخطيط واحدة ويمكن أن يحسن الأداء عندما تقوم لاحقًا بتحويلها إلى PDF.

## مثال كامل يعمل (جميع الخطوات مجمعة)

فيما يلي السكربت الكامل الذي يمكنك نسخه‑ولصقه في ملف باسم `rectangle_shadow.py`. شغّله باستخدام `python rectangle_shadow.py` وتحقق من مجلد `output`.

```python
import aspose.words as aw
import os

# Ensure the output directory exists
os.makedirs("output", exist_ok=True)

# Initialize the document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

# Configure the shadow
shadow = shape.shadow_format
shadow.visible = True
shadow.distance = 5.0
shadow.blur = 8.0
shadow.color = aw.Color.dark_grey
shadow.opacity = 0.6
shadow.angle = 45.0

# Save the document
output_path = "output/ShapeWithShadow.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

تشغيل هذا السكربت ينتج نفس المستند الذي ناقشناه سابقًا. لا تتردد في تعديل القيم؛ الشفرة بسيطة عمدًا لتتمكن من التجربة دون خوف.

## الأسئلة المتكررة

**س: هل يعمل هذا على Linux?**

## ماذا يجب أن تتعلم بعد ذلك؟

- [إنشاء مستند Word Java – إضافة شكل مستطيل مع تأثير الظل](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [إنشاء مستند Word فارغ مع شكل مستطيل مظلل – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [دروس ظل شكل Aspose.Words – إضافة ظل إلى شكل Word في C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}