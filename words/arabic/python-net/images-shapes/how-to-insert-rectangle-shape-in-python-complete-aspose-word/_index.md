---
category: general
date: 2026-06-27
description: تعلم كيفية إدراج شكل مستطيل في بايثون باستخدام Aspose.Words، وتغيير لون
  الظل، وإضافة ظل خارجي، وتطبيق تأثير الظل على الشكل—كل ذلك في درس واحد.
draft: false
keywords:
- how to insert rectangle shape
- how to change shadow color
- how to add outer shadow
- apply shadow effect to shape
language: ar
og_description: تعلّم كيفية إدراج شكل مستطيل في بايثون، وتغيير لون ظله، وإضافة ظل
  خارجي، وتطبيق تأثير الظل على الشكل باستخدام Aspose.Words.
og_title: كيفية إدراج شكل مستطيل في بايثون – دليل Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  headline: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  name: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: Pro tip
    text: If you need the rectangle positioned at a specific location, use `builder.move_to`
      before inserting, or adjust `rectangle.left` and `rectangle.top` after creation.
  - name: Edge case
    text: If you forget to set `shadow.opacity`, the default is fully opaque, which
      can make the shadow look like a solid shape. Always pair a color change with
      an appropriate opacity level.
  - name: Common pitfalls
    text: '- **Missing directory:** `doc.save` will raise an error if the folder doesn’t
      exist. Create it first or use `os.makedirs`. - **Version mismatch:** The shadow
      API requires Aspose.Words 22.9+; older versions silently ignore shadow settings.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
title: كيفية إدراج شكل مستطيل في بايثون – دليل Aspose.Words الكامل
url: /ar/python/images-shapes/how-to-insert-rectangle-shape-in-python-complete-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إدراج شكل مستطيل في بايثون – دليل Aspose.Words الكامل

هل تساءلت يومًا **how to insert rectangle shape** في مستند Word باستخدام بايثون؟ لست وحدك—العديد من المطورين يواجهون هذه المشكلة عند أتمتة التقارير أو إنشاء القوالب. الخبر السار هو أن Aspose.Words يجعل الأمر سهلًا للغاية، وفي هذا الدرس سنستعرض العملية بالكامل، من رسم المستطيل إلى إضافة ظل خارجي أنيق.

سنغطي أيضًا **how to change shadow color**، **how to add outer shadow**، والخطوة الأخيرة **apply shadow effect to shape**. في النهاية ستحصل على مستطيل مُنسق بالكامل يمكنك إدراجه برمجيًا في أي ملف .docx.

## المتطلبات المسبقة

- Python 3.8+ مثبت على جهازك  
- Aspose.Words for Python عبر `pip install aspose-words`  
- إلمام أساسي ببرمجة بايثون (لا تحتاج إلى معرفة عميقة بواجهة Word‑API)  

إذا كان لديك كل ذلك، رائع—لنبدأ. إذا لم يكن كذلك، احصل على المكتبة أولًا؛ باقي الدليل يفترض أن الاستيراد يعمل بدون مشاكل.

## كيفية إدراج شكل مستطيل باستخدام Aspose.Words for Python

الخطوة الأولى هي بالضبط ما يَعِدُ به المفتاح الأساسي: **how to insert rectangle shape**. سننشئ مستندًا جديدًا، نُنشئ `DocumentBuilder`، ونضع مستطيلًا على الصفحة.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a fresh document and a builder to add content
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle shape of 200x100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Optional: give the rectangle a light fill so the shadow is visible
rectangle.fill_color = aw.drawing.Color.light_blue
```

> **Why this matters:** استدعاء `insert_shape` هو جوهر *how to insert rectangle shape*. يُعيد كائن `Shape` يمكنك تعديل خصائصه لاحقًا—الحجم، الموقع، التعبئة، الحدود، إلخ. لاحظ أننا أيضًا نحدد `fill_color`؛ بدونها قد يندمج الظل مع صفحة بيضاء، مما يجعل رؤيته صعبًا.

### نصيحة احترافية
إذا كنت بحاجة إلى وضع المستطيل في موقع محدد، استخدم `builder.move_to` قبل الإدراج، أو عدل `rectangle.left` و `rectangle.top` بعد الإنشاء.

## تغيير لون ظل الشكل

الآن بعد أن أصبح المستطيل موجودًا في المستند، دعنا نجيب على **how to change shadow color**. تُوفر Aspose.Words كائن `ShadowEffect` حيث يمكنك تعيين خاصية `color` إلى أي قيمة RGB.

```python
# Create a shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # we’ll also cover outer shadow later
shadow.blur_radius = 8.0                  # smooth edges
shadow.distance = 6.0                     # how far the shadow sits from the shape
shadow.direction = 45                     # angle in degrees
shadow.opacity = 0.6                      # semi‑transparent

# Change the shadow color to a deep gray instead of black
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)

# Apply the shadow to our rectangle
rectangle.shadow = shadow
```

> **Why you’d want this:** الظل الأسود الداكن قد يكون قاسيًا جدًا، خاصةً في المستندات ذات الألوان الفاتحة. تعديل اللون يتيح لك مطابقة هوية الشركة أو ببساطة الحصول على تأثير بصري أكثر نعومة.

### حالة حافة
إذا نسيت تعيين `shadow.opacity`، فإن القيمة الافتراضية تكون غير شفافة بالكامل، مما قد يجعل الظل يبدو كشكل صلب. احرص دائمًا على ربط تغيير اللون بمستوى شفافية مناسب.

## إضافة تأثير ظل خارجي

السؤال التالي الذي يطرحه الكثيرون هو **how to add outer shadow**. علم `ShadowStyle.OUTER` يخبر Aspose.Words برسم الظل خارج حدود الشكل بدلاً من داخله.

المقتطف البرمجي أعلاه يستخدم بالفعل `ShadowStyle.OUTER`، لكن لنُظهر هذا الإعداد بشكل منفصل للتوضيح:

```python
# Ensure the shadow style is outer
shadow.style = ShadowStyle.OUTER
```

إذا قمت بتغيير إلى `ShadowStyle.INNER`، سيظهر الظل *داخل* المستطيل، وهو مفيد لتأثيرات النقش. في معظم سيناريوهات تصميم المستندات، يعطي النمط الخارجي مظهر ظل طبيعي.

## تطبيق تأثير الظل على الشكل

لقد قمنا بالفعل بـ **apply shadow effect to shape** عن طريق تعيين `rectangle.shadow = shadow`. الآن لنُجَمِّع كل شيء معًا ونحفظ المستند، مؤكدين أن التأثير يبقى.

```python
# Save the document – choose a folder you have write access to
output_path = "output/RectangleWithShadow.docx"
doc.save(output_path)

print(f"Document saved to {output_path}. Open it to see the rectangle with its outer shadow.")
```

عند فتح `RectangleWithShadow.docx` في Microsoft Word، يجب أن ترى مستطيلًا أزرق فاتح مع ظل رمادي خارجي خفيف بزاوية 45°. سيكون الظل مُطمسًا قليلًا ومُزاحًا، تمامًا كما ضبطنا.

### أخطاء شائعة
- **المجلد غير موجود:** سيُظهر `doc.save` خطأ إذا لم يكن المجلد موجودًا. أنشئه أولًا أو استخدم `os.makedirs`.
- **عدم توافق الإصدارات:** يتطلب API الظل Aspose.Words 22.9+؛ الإصدارات الأقدم تتجاهل إعدادات الظل بصمت.

## مثال كامل يعمل

فيما يلي السكربت الكامل الجاهز للتنفيذ الذي يجمع جميع الخطوات. انسخه‑الصقه في ملف باسم `rectangle_shadow.py` وشغّله باستخدام `python rectangle_shadow.py`.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Create a new document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2️⃣ Insert the rectangle shape (how to insert rectangle shape)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle.fill_color = aw.drawing.Color.light_blue   # make the shape visible

# 3️⃣ Define the shadow (how to change shadow color, how to add outer shadow)
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # outer shadow
shadow.blur_radius = 8.0
shadow.distance = 6.0
shadow.direction = 45
shadow.opacity = 0.6
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)  # custom gray

# 4️⃣ Apply the shadow (apply shadow effect to shape)
rectangle.shadow = shadow

# 5️⃣ Save the file
output_path = os.path.join(output_dir, "RectangleWithShadow.docx")
doc.save(output_path)

print(f"✅ Document generated: {output_path}")
```

**الناتج المتوقع:** مستند Word (`RectangleWithShadow.docx`) يحتوي على مستطيل واحد بظل رمادي خارجي. افتحه في Word للتحقق من التأثير البصري.

## الأسئلة المتكررة

| السؤال | الجواب |
|----------|--------|
| *هل يمكنني استخدام نوع شكل مختلف؟* | بالتأكيد—استبدل `ShapeType.RECTANGLE` بـ `ShapeType.OVAL` أو `ShapeType.TRIANGLE` وغيرها، وستظل منطقية الظل نفسها. |
| *ماذا لو أردت حدًا أكثر سمكًا؟* | عيّن `rectangle.line_width = 2.0` (نقطة) قبل تطبيق الظل. |
| *هل يمكن تحريك الظل؟* | ليس مباشرةً باستخدام Aspose.Words؛ ستحتاج إلى تصدير إلى HTML/CSS لإضافة الحركة. |
| *هل يعمل هذا على macOS؟* | نعم—Aspose.Words مستقل عن المنصة طالما أن بايثون يعمل. |

## الخلاصة

استعرضنا **how to insert rectangle shape**، وشرحنا **how to change shadow color**، وتناولنا **how to add outer shadow**، وأخيرًا أظهرنا لك كيفية **apply shadow effect to shape** باستخدام Aspose.Words for Python. السكربت الكامل جاهز للإدماج في أي خط أنابيب أتمتة، مما يمنحك مستطيلًا بمظهر احترافي وظل مصقول في ثوانٍ.

هل أنت مستعد للخطوة التالية؟ جرّب تغيير لون التعبئة، تجربة زوايا `direction` مختلفة، أو إضافة أشكال متعددة إلى نفس الصفحة. يمكنك أيضًا استكشاف API تنسيق النص الغني في Aspose.Words لدمج الظلال مع النص المنسق—مثالي لتقارير جذابة بصريًا.

إذا وجدت هذا الدرس مفيدًا، اضغط إعجاب، شاركه مع زملائك، أو اترك تعليقًا بأصنافك الخاصة. برمجة سعيدة!

![Diagram showing how to insert rectangle shape with an outer shadow applied in a Word document](/images/rectangle-shadow.png)


## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}