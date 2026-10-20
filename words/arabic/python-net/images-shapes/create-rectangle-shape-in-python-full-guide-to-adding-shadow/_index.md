---
category: general
date: 2026-05-04
description: تعلم كيفية إنشاء شكل مستطيل، وكيفية إضافة شكل بظلال، وتغيير لون الظل،
  وتعيين مسافة الظل، وحفظ المستند كملف PDF باستخدام Aspose.Words للغة Python.
draft: false
keywords:
- create rectangle shape
- how to add shape
- change shadow color
- save document as pdf
- set shadow distance
language: ar
og_description: إنشاء شكل مستطيل باستخدام Aspose.Words للبايثون، وتعلم كيفية إضافة
  الشكل، وتغيير لون الظل، وتعيين مسافة الظل، وحفظ المستند كملف PDF.
og_title: إنشاء شكل مستطيل – إضافة ظل، تغيير اللون وحفظه كملف PDF
tags:
- Aspose.Words
- Python
- PDF generation
title: إنشاء شكل مستطيل في بايثون – دليل كامل لإضافة الظلال وحفظه كملف PDF
url: /ar/python/images-shapes/create-rectangle-shape-in-python-full-guide-to-adding-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء شكل مستطيل – دليل كامل لمطوري بايثون

هل احتجت يوماً إلى **create rectangle shape** في مستند Word وتساءلت كيف تضيف له ظلًا مصقولًا؟ ربما تقوم بإنشاء مولد تقارير وتهمك اللمسة البصرية—خاصة عندما يكون الناتج النهائي ملف PDF. الخبر السار؟ مع Aspose.Words for Python يمكنك ليس فقط **how to add shape** بل أيضًا تعديل كل خاصية للظل، من اللون إلى المسافة، ثم **save document as pdf** في تدفق واحد سلس.

في هذا الدليل سنستعرض العملية بالكامل خطوة بخطوة. سترى الشيفرة الدقيقة التي يمكنك نسخها‑لصقها، وتفهم *لماذا* كل سطر مهم، وتلتقط بعض النصائح للتعامل مع الحالات الخاصة (مثل الظلال الشفافة أو DPI غير القياسي). في النهاية ستكون قادرًا على **create rectangle shape**, تخصيص ظله، وتصدير PDF واضح دون عناء.

## المتطلبات المسبقة

- تثبيت Python 3.8+ على جهازك.  
- Aspose.Words for Python عبر `pip install aspose-words`.  
- إلمام أساسي بالبرمجة الكائنية في Python (لا شيء معقد).  

إذا كان لديك بيئة افتراضية مُعدّة بالفعل، فقط نفّذ أمر التثبيت وستكون جاهزًا للبدء.

## الخطوة 1: تهيئة المستند والباني

قبل أن تتمكن من **how to add shape**, تحتاج إلى مستند فارغ للعمل معه. تمثل فئة `Document` الملف بأكمله، و`DocumentBuilder` هي فرشاتك.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder to edit it
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

*لماذا هذا مهم:* `Document` يحتوي على جميع الأقسام والصفحات والموارد. `DocumentBuilder` يوفّر لك API سلس لإدراج المحتوى بالضبط حيث تحتاجه—فكّر فيه كالمؤشر في معالج النصوص.

## الخطوة 2: إدراج شكل المستطيل

الآن نضيف فعليًا **how to add shape**. طريقة `insert_shape` تحتاج إلى نوع الشكل وأبعاده (بالنقاط). هنا نختار مستطيل 200 × 100 pt ونملأه بلون أزرق فاتح.

```python
# Step 2: Insert a rectangle shape and give it a light‑blue fill
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,  # shape type
    200,                            # width in points
    100)                            # height in points
rectangle_shape.fill_color = aw.Color.light_blue
```

*نصيحة احترافية:* إذا كنت تحتاج إلى محاذاة الشكل مع النص الموجود، استخدم `builder.move_to` قبل الإدراج، أو عدّل خصائص `left`/`top` بعد الإنشاء.

## الخطوة 3: تشغيل الظل

الشكل بدون ظل يبدو مسطحًا. لتطبيق **set shadow distance** وجعل التأثير مرئيًا، احصل على تنسيق الظل وفعلّه.

```python
# Step 3: Access the shape's shadow format and make the shadow visible
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
```

*لماذا هذه الخطوة:* تنسيق الظل هو كائن منفصل؛ تفعيل `visible` هو أول شيء يجب القيام به، وإلا ستُتجاهل جميع خصائص الظل الأخرى.

## الخطوة 4: تنسيق الظل – اللون، الضبابية، المسافة، الاتجاه

هنا يحدث السحر. سنقوم بـ **change shadow color**, ضبط نصف قطر الضبابية، تحديد مدى بُعد الظل عن المستطيل، وتدويره 45°.

```python
# Step 4: Configure the appearance of the shadow
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER   # outer shadow
rectangle_shadow.blur_radius = 10.0                    # blur amount (pixels)
rectangle_shadow.distance = 5.0                        # distance from the shape
rectangle_shadow.direction = 45.0                     # angle in degrees
rectangle_shadow.color = aw.Color.gray                 # shadow colour
```

*شرح كل خاصية:*

| Property | ما الذي يفعله | القيم النموذجية |
|----------|--------------|----------------|
| `style` | يحدد ما إذا كان الظل *داخلي* أم *خارجي*. | `OUTER` (الأكثر شيوعًا) |
| `blur_radius` | يتحكم في النعومة؛ كلما ارتفع الرقم كلما كان الحافة أكثر ضبابية. | 0–20 px هو المعتاد |
| `distance` | مدى إزاحة الظل عن الشكل. | 0–10 pt للظل الخفيف، >10 للظل الدرامي |
| `direction` | زاوية مصدر الضوء، تُقاس باتجاه عقارب الساعة من المحور x. | 0‑360° |
| `color` | لون الظل. | أي `aw.Color` (مثال: `gray`, `dark_red`) |

*حالة خاصة:* إذا ضبطت `distance` إلى `0` سيجلس الظل مباشرة تحت الشكل، مما يخفي تعبئة الشكل. احتفظ بالقيمة أعلى من `0` للحصول على إزاحة مرئية.

## الخطوة 5: حفظ المستند كملف PDF

أخيرًا، نحن **save document as pdf**. Aspose.Words يقوم تلقائيًا ب rasterisation للظل، لذا سيظهر الـ PDF تمامًا كما هو في عرض Word.

```python
# Step 5: Save the document as a PDF with the shadowed shape
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

*لماذا PDF؟* ملفات PDF تحافظ على التخطيط عبر المنصات، مما يجعلها مثالية للتقارير، الفواتير، أو أي مستند قابل للطباعة.

---

![إنشاء شكل مستطيل مع ظل](https://example.com/images/rectangle-shadow.png){: .align-center alt="مثال على إنشاء شكل مستطيل مع ظل"}

*الصورة أعلاه تُظهر النتيجة النهائية في PDF – مستطيل أزرق فاتح مع ظل رمادي خارجي ناعم، تمامًا كما قمنا بإعداده.*

## أسئلة شائعة وتنوعات

### ماذا لو احتجت إلى ظل **شفاف**؟

قم بتعيين قناة ألفا على لون الظل:

```python
transparent_gray = aw.Color.from_argb(128, 0, 0, 0)  # 50% opacity black
rectangle_shadow.color = transparent_gray
```

### هل يمكنني تطبيق نفس الظل على أشكال متعددة؟

نعم. استخرج `ShadowFormat` من شكل واحد وعيّنه لآخر:

```python
another_shape = builder.insert_shape(aw.drawing.ShapeType.ELLIPSE, 150, 150)
another_shape.shadow_format = rectangle_shadow.clone()
```

### كيف أغيّر الظل لنوع **شكل مختلف**؟

جميع أنواع الأشكال تشترك في نفس خصائص `ShadowFormat`، لذا يمكنك إعادة استخدام نفس كتلة الإعداد—فقط استبدل `ShapeType.RECTANGLE` بـ `ShapeType.OVAL`، `ShapeType.TRIANGLE`، إلخ.

### ماذا عن **ملفات PDF عالية الدقة** للطباعة؟

حدد `PdfSaveOptions` مع DPI أعلى:

```python
options = aw.saving.PdfSaveOptions()
options.image_resolution = 300  # 300 DPI for print quality
document.save(output_path, options)
```

## ملخص

لقد غطينا كل ما تحتاجه لتتمكن من **create rectangle shape**, **how to add shape**, تخصيص **shadow colour**, **set shadow distance**, وأخيرًا **save document as pdf**. النص الكامل القابل للتنفيذ يبدو هكذا:

```python
import aspose.words as aw

# Initialise document
document = aw.Document()
builder = aw.DocumentBuilder(document)

# Insert rectangle shape
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle_shape.fill_color = aw.Color.light_blue

# Enable and style shadow
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER
rectangle_shadow.blur_radius = 10.0
rectangle_shadow.distance = 5.0
rectangle_shadow.direction = 45.0
rectangle_shadow.color = aw.Color.gray

# Save as PDF
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

شغّل النص، افتح الملف الناتج `ShadowedShape.pdf`، وسترى مستطيلًا واضحًا مع ظل رمادي خفيف—تمامًا ما تتوقعه من تقرير مُنسق احترافيًا.

## ما التالي؟

- **استكشف أنواع أشكال أخرى** (`ShapeType.OVAL`, `ShapeType.LINE`) لإثراء مستنداتك.  
- **اجمع عدة ظلال** عن طريق تكديس الأشكال؛ يمكنك حتى إنشاء تأثير “توهج” باستخدام ظل داخلي بلون ساطع.  
- **أتمتة المعالجة الدفعية**: حلق عبر مجموعة من صفوف البيانات، أنشئ شكلًا لكل صف، وادمج كل شيء في PDF واحد.  
- **دمج مع مكتبات Aspose أخرى** (مثل Aspose.Slides) إذا كنت بحاجة لتصدير نفس المظهر إلى PowerPoint.

لا تتردد في التجربة—غيّر `blur_radius`، العب بـ `direction`، أو استبدل `gray` بلون خاص بالعلامة التجارية. الـ API مرن بما يكفي ليُحدث تعديل بسيط تغييرًا كبيرًا في التأثير البصري.

هل لديك أسئلة أو سيناريو صعب؟ اترك تعليقًا أدناه أو تواصل مع منتديات مجتمع Aspose. ترميز سعيد، واستمتع بالمستطيلات ذات الظلال الجميلة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}