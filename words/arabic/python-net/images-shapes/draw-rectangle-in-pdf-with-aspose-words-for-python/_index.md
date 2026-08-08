---
category: general
date: 2026-08-07
description: ارسم مستطيلًا في ملف PDF باستخدام Aspose.Words للغة Python وتعلم كيفية
  إضافة ظل إلى الشكل، وتكوين ظل الشكل، وحفظ المستند كملف PDF.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle in pdf
- add shadow to shape
- save document as pdf
- configure shape shadow
language: ar
lastmod: 2026-08-07
og_description: ارسم مستطيلًا في PDF باستخدام Aspose.Words للبايثون. يوضح هذا الدرس
  كيفية إضافة ظل إلى الشكل، وتكوين ظل الشكل، وحفظ المستند كملف PDF لتوليد مستندات
  احترافية.
og_image_alt: PDF page showing a rectangle shape with a visible shadow created by
  Aspose.Words for Python
og_title: ارسم مستطيلًا في PDF باستخدام Aspose.Words للبايثون – دليل
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Draw rectangle in PDF using Aspose.Words for Python and learn how to
    add shadow to shape, configure shape shadow, and save document as PDF.
  headline: Draw rectangle in PDF with Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF
- Shape
- Shadow
title: رسم مستطيل في PDF باستخدام Aspose.Words للبايثون
url: /ar/python/images-shapes/draw-rectangle-in-pdf-with-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# رسم مستطيل في PDF باستخدام Aspose.Words للـ Python

إذا كنت بحاجة إلى **رسم مستطيل في PDF** أثناء العمل بلغة Python، فإن هذا الدليل يقدم لك حلاً كاملاً وجاهزًا للتنفيذ. ستتعرف بالضبط على كيفية **إضافة ظل إلى الشكل**، وتكوين ذلك الظل، وأخيرًا **حفظ المستند كملف PDF** للتوزيع أو الأرشفة.

إنشاء مستطيل مُظلّل هو طلب شائع في التقارير، الفواتير، أو التعليقات البصرية. في نهاية هذا الشرح ستحصل على سكريبت واحد ينتج ملف PDF يحتوي على مستطيل بظل واقعي، وستفهم كيفية تعديل الحجم، اللون، والإزاحة لتتناسب مع أي تصميم.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* Python 3.8+ مثبت.
* حزمة Aspose.Words للـ Python عبر .NET (`aspose-words`) – ثبّتها باستخدام:

```bash
pip install aspose-words
```

* صلاحية كتابة في المجلد الذي تنوي حفظ ملف PDF فيه.

لا توجد مكتبات إضافية مطلوبة؛ فـ Aspose.Words يتولى إنشاء الأشكال، تكوين الظل، وتصدير PDF داخليًا.

## الخطوة 1: إنشاء مستند فارغ جديد (رسم مستطيل في PDF – التهيئة)

الخطوة الأولى هي إنشاء كائن `Document`. يمثل هذا الكائن ملف PDF بالكامل ويوفر حاوية للأقسام، الفقرات، والأشكال.

```python
import aspose.words as aw

# Create an empty Word document – it will become a PDF later
doc = aw.Document()
```

**لماذا هذا مهم:** يتعامل Aspose.Words مع إنشاء PDF كتحويل من نموذج مستند Word، لذا نبدأ بـ `Document` رغم أن النتيجة النهائية هي PDF.

## الخطوة 2: إدراج شكل مستطيل في جسم المستند

المستطيل هو نوع محدد من `ShapeType`. نضيفه إلى جسم القسم الأول، والذي يُنشئ تلقائيًا صفحة جديدة عند حفظه كملف PDF.

```python
# Append a rectangle shape to the first section's body
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Set the rectangle's dimensions (points = 1/72 inch)
rectangle.width = 200   # 200 pt ≈ 2.78 in
rectangle.height = 100  # 100 pt ≈ 1.39 in

# Optional: give the shape some visible text
rectangle.text = "Shadow demo"
```

**شرح:** تتحكم خاصيتي `width` و `height` في الحجم البصري للشكل داخل PDF. إضافة نص تجعل من السهل التحقق من المستطيل أثناء الاختبار.

## الخطوة 3: إضافة ظل إلى الشكل – التفعيل والتخصيص

الآن نقوم بتفعيل تأثير الظل ونضبط مظهره بدقة. هنا يأتي دور كلمة **add shadow to shape**.

```python
# Access the shape's shadow effect object
shadow = rectangle.shadow_effect

# Make the shadow visible
shadow.visible = True

# Configure blur radius (pt) – higher values produce a softer edge
shadow.blur = 8

# Set the distance (offset) from the shape in points
shadow.distance = 5

# Define the direction of the shadow in degrees (0 = right, 90 = down)
shadow.angle = 45

# Choose a shadow color – black works for most documents
shadow.color = aw.drawing.Color.black
```

**لماذا نُكوّن ظل الشكل؟** تعديل `blur` و `distance` و `angle` يسمح لك بمحاكاة إضاءة واقعية، مما يحسن من قابلية القراءة والهرمية البصرية في ملفات PDF المُولدة.

## الخطوة 4: حفظ المستند كملف PDF – النتيجة النهائية

بعد تعريف المستطيل وظله، الخطوة الأخيرة هي تصدير مستند Word إلى PDF. هذا يحقق مطلب **save document as pdf**.

```python
# Define the output path – replace YOUR_DIRECTORY with an actual folder
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)
print(f"PDF saved to {output_path}")
```

عند فتح `shadow_rectangle.pdf`، ستظهر لك صفحة واحدة تحتوي على مستطيل بحدود رمادية بعنوان “Shadow demo” مع ظل قطري واضح.

### النتيجة المتوقعة

* ملف PDF اسمه `shadow_rectangle.pdf`.
* صفحة واحدة تحتوي على مستطيل بحجم 200 pt × 100 pt.
* ظل مرئي إزاحته 5 pt بزاوية 45°، مع تمويه بقيمة 8 pt.

## الخطوة 5: استكشاف التغييرات والحالات الخاصة (اختياري)

فيما يلي بعض التعديلات الشائعة التي قد تحتاجها في المشاريع الواقعية:

| التغيير | مقتطف الكود | متى يُستخدم |
|-----------|--------------|-------------|
| **نوع شكل مختلف** (مثل إهليلج) | `aw.drawing.ShapeType.OVAL` بدلاً من `RECTANGLE` | للرسومات المستديرة أو الشارات |
| **لون ظل مخصص** | `shadow.color = aw.drawing.Color.from_argb(255, 100, 100, 100)` | عندما يكون الظل رماديًا أو يحمل لون العلامة التجارية |
| **أشكال متعددة** | كرّر كتلة إنشاء الشكل وعدّل خصائص `left`/`top` | لبناء مخططات معقدة |
| **بدون نص داخل الشكل** | احذف `rectangle.text = "..."` | عندما يكون الشكل ديكوريًا فقط |
| **إخراج بدقة DPI أعلى** | `doc.save(output_path, aw.SaveFormat.PDF, aw.PdfSaveOptions())` مع ضبط `PdfSaveOptions` لجودة الصورة | لملفات PDF جاهزة للطباعة |

**نصيحة احترافية:** دائمًا عيّن `shadow.visible = True` قبل تعديل الخصائص الأخرى؛ وإلا سيتجاهل التغييرات بصمت.

## السكريبت الكامل – انسخه، الصقه، وشغّله

```python
import aspose.words as aw

# 1️⃣ Create a new blank document
doc = aw.Document()

# 2️⃣ Add a rectangle shape
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
rectangle.width = 200          # width in points
rectangle.height = 100         # height in points
rectangle.text = "Shadow demo"

# 3️⃣ Configure a visible shadow effect
shadow = rectangle.shadow_effect
shadow.visible = True
shadow.blur = 8                # blur radius (pt)
shadow.distance = 5            # offset distance (pt)
shadow.angle = 45              # direction (degrees)
shadow.color = aw.drawing.Color.black

# 4️⃣ Save the document as a PDF
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)

print(f"PDF successfully created at: {output_path}")
```

شغّل السكريبت من الطرفية أو بيئة التطوير المتكاملة. استبدل `YOUR_DIRECTORY` بمسار مجلد حقيقي، مثل `"/tmp"` أو `"C:\\Users\\Me\\Documents"`.

## الخلاصة

أصبحت الآن تعرف كيف **ترسم مستطيل في PDF** باستخدام Aspose.Words للـ Python، **تضيف ظلًا إلى الشكل**، **تُكوّن ظل الشكل**، و**تحفظ المستند كملف PDF**. يوضح المثال الكامل كل خطوة من إنشاء المستند حتى التصدير النهائي، وتظهر التغييرات الاختيارية كيفية تعديل الكود لسيناريوهات أكثر تعقيدًا.

الخطوات التالية التي يمكنك استكشافها:

* إضافة أنواع أشكال أخرى (`ShapeType.LINE`, `ShapeType.ELLIPSE`).
* تطبيق تعبئات تدرجية أو حدود لتعزيز الجاذبية البصرية.
* استخدام `PdfSaveOptions` لتضمين الخطوط أو التحكم في ضغط الصور.

لا تتردد في تجربة المعلمات لتتناسب مع هوية علامتك التجارية أو إرشادات التصميم. نتمنى لك تجربة ممتعة في برمجة PDF!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Optimize PDF Bookmarks Using Aspose.Words for Python](/words/english/python-net/performance-optimization/optimize-pdf-bookmarks-aspose-words-python/)
- [Optimize Pdf Loading Python Aspose Words Skip Images](/words/hindi/python-net/performance-optimization/optimize-pdf-loading-python-aspose-words-skip-images/)
- [Aspose Words Python Pdf Manipulation](/words/hongkong/python-net/document-operations/aspose-words-python-pdf-manipulation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}