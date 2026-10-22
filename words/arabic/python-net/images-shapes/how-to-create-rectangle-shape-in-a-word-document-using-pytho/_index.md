---
category: general
date: 2026-09-30
description: تعلم كيفية إنشاء شكل مستطيل، وتطبيق الظل على الشكل، وحفظ مستند Word مع
  الشكل باستخدام Aspose.Words للغة Python.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- how to add shape
- apply shadow to shape
- set shadow blur
- save word with shape
language: ar
lastmod: 2026-09-30
og_description: إنشاء شكل مستطيل في مستند Word بسرعة. يوضح هذا الدرس كيفية إضافة الشكل،
  تطبيق الظل على الشكل، ضبط تمويه الظل، وحفظ مستند Word مع الشكل.
og_image_alt: Screenshot of a Word document showing a rectangle shape with a soft
  shadow
og_title: إنشاء شكل مستطيل في Word باستخدام Python – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Learn how to create rectangle shape, apply shadow to shape, and save
    Word with shape using Aspose.Words for Python.
  headline: How to create rectangle shape in a Word document using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- Shapes
title: كيفية إنشاء شكل مستطيل في مستند Word باستخدام Python
url: /ar/python/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء شكل مستطيل في مستند Word باستخدام Python

إذا كنت بحاجة إلى **إنشاء شكل مستطيل** في ملف Word، فإن هذا الدليل يوضح لك حلاً كاملاً قابلاً للتنفيذ. ستتعرف على كيفية إضافة الشكل، تطبيق تأثير الظل، ضبط الضبابية، وأخيرًا **حفظ Word مع الشكل** بحيث يمكن فتح النتيجة في Microsoft Word أو أي عارض متوافق.

يستخدم المثال **Aspose.Words for Python via .NET**، وهي مكتبة تتيح لك التعامل مع مستندات Word دون الحاجة إلى تثبيت Microsoft Office. لا تحتاج إلى خبرة مسبقة في الـ API—فقط معرفة أساسية بـ Python.

## ما ستحققه

- إدراج مستطيل في القسم الأول من مستند جديد.  
- تكوين ظل ناعم عن طريق ضبط الضبابية، الإزاحة، واللون.  
- حفظ المستند على القرص والتحقق من النتيجة البصرية.

## المتطلبات المسبقة

- Python 3.8 أو أحدث.  
- حزمة `aspose-words` مثبتة (`pip install aspose-words`).  
- صلاحية كتابة في دليل الإخراج.

## إنشاء شكل مستطيل وتكوين مظهره

الخطوة الأولى هي إنشاء مستند فارغ وإضافة شكل مستطيل إليه. سيعمل الشكل كقماش لتأثير الظل.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Step 1: Create a new blank document
doc = aw.Document()

# Step 2: Add a rectangle shape to the first section
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Optional: Define the shape’s size and position (in points)
shape.width = aw.ConvertUtil.inch_to_point(2)   # 2 inches wide
shape.height = aw.ConvertUtil.inch_to_point(1)  # 1 inch tall
shape.left = aw.ConvertUtil.inch_to_point(1)    # 1 inch from the left margin
shape.top = aw.ConvertUtil.inch_to_point(1)     # 1 inch from the top margin
```

**لماذا هذا مهم:**  
إنشاء المستطيل يمنحك كائنًا ملموسًا (`shape`) يمكنك تنسيقه لاحقًا. ضبط الأبعاد بشكل صريح يضمن أن الشكل يبدو بنفس الشكل على كل منصة.

## كيفية إضافة الشكل إلى مستند Word

بينما يضيف الكود أعلاه المستطيل بالفعل، قد تحتاج لاحقًا إلى إضافة أشكال إضافية (مثل الدوائر أو الأسهم). نفس النمط يُطبق: استدعِ `append_child` على جسم المستند ومرّر نوع الـ `ShapeType` المطلوب.

```python
# Example: Adding a second shape – an ellipse
ellipse = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.ELLIPSE)
)
ellipse.width = aw.ConvertUtil.inch_to_point(1.5)
ellipse.height = aw.ConvertUtil.inch_to_point(1)
ellipse.left = aw.ConvertUtil.inch_to_point(3.5)
ellipse.top = aw.ConvertUtil.inch_to_point(1)
```

**نصيحة:** استخدم تعداد `ShapeType` لاستكشاف جميع الأشكال المدعومة. هذا يحافظ على قابلية قراءة الكود ويتجنب الأرقام السحرية.

## تطبيق الظل على الشكل وضبط ضبابية الظل

يضيف الظل عمقًا واهتمامًا بصريًا. تسمح لك فئة `ShadowEffect` بالتحكم في الضبابية، الإزاحة، واللون. أدناه نطبق ظلًا أسودًا ناعمًا على المستطيل.

```python
# Step 3: Configure a shadow effect for the rectangle
shadow = ShadowEffect()
shadow.blur = 5.0          # Sets the softness of the shadow edge
shadow.offset_x = 2.0      # Horizontal displacement from the shape
shadow.offset_y = 2.0      # Vertical displacement from the shape
shadow.color = aw.Color.black

# Step 4: Apply the shadow effect to the shape
shape.shadow = shadow
```

**لماذا نضبط الضبابية؟**  
تحدد `blur` مدى انتشار الظل. القيمة المنخفضة (مثلاً 1.0) تنتج حافة حادة، بينما القيمة الأعلى (مثلاً 5.0) تخلق تلاشيًا لطيفًا، وهو غالبًا أكثر جاذبية من الناحية الجمالية.

**حالة خاصة:** إذا ضبطت `blur` على 0، يصبح الظل صورة صلبة. قد يعرض بعض العارضين ذلك مع عيوب التنعيم، لذا اختر قيمة أكبر من 0 للحصول على مخرجات أكثر سلاسة.

## حفظ Word مع الشكل

حفظ المستند ينهى جميع التغييرات. طريقة `save` تكتب ملف `.docx` يمكن لأي معالج Word حديث فتحه.

```python
# Step 5: Save the document to see the result
output_path = "output.docx"   # Adjust the path as needed
doc.save(output_path)
print(f"Document saved to {output_path}")
```

عند فتح `output.docx`، سترى مستطيلًا موضعًا على بُعد بوصة واحدة من الزاوية العليا اليسرى، مع ظل أسود ناعم مُزاح نقطتين إلى اليمين وإلى الأسفل. تجعل ضبابية الظل الشكل يبدو كأنه مرفوع عن الصفحة.

**نصيحة احترافية:** إذا كنت بحاجة إلى إنشاء مستندات متعددة داخل حلقة، أعد استخدام نفس كائن `Document` وامسح جسمه بين كل تكرار لتقليل استهلاك الذاكرة.

## الاختلافات الشائعة واستكشاف الأخطاء وإصلاحها

| الحالة | ما الذي يجب تغييره | السبب |
|-----------|----------------|--------|
| لون ظل مختلف | `shadow.color = aw.Color.red` | استخدم ألوان العلامة أو أبرز الأشكال المهمة. |
| إزاحة ظل أكبر | زيادة `shadow.offset_x`/`offset_y` | تعزيز العمق لتصاميم واجهات المستخدم. |
| عدم وجود ظل على الإطلاق | حذف سطر `shape.shadow = shadow` | مفيد للتقارير البسيطة. |
| تصدير إلى PDF بدلاً من DOCX | `doc.save("output.pdf")` | PDF مثالي للتوزيع غير القابل للتعديل. |

إذا لم يظهر الشكل، تحقق من أنك تضيفه إلى القسم الصحيح (`get_first_section()`) وأن المستند يُحفظ بعد التعديلات.

## مثال كامل قابل للتنفيذ

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Create a new blank document
doc = aw.Document()

# Add a rectangle shape
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
shape.width = aw.ConvertUtil.inch_to_point(2)
shape.height = aw.ConvertUtil.inch_to_point(1)
shape.left = aw.ConvertUtil.inch_to_point(1)
shape.top = aw.ConvertUtil.inch_to_point(1)

# Configure and apply a shadow
shadow = ShadowEffect()
shadow.blur = 5.0
shadow.offset_x = 2.0
shadow.offset_y = 2.0
shadow.color = aw.Color.black
shape.shadow = shadow

# Save the document
output_path = "output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

تشغيل السكريبت ينتج `output.docx` يحتوي على المستطيل مع ظل ناعم. افتح الملف في Microsoft Word لتتأكد من أن التأثير البصري يطابق الوصف.

## الخلاصة

أنت الآن تعرف **كيفية إنشاء شكل مستطيل**، **كيفية إضافة الشكل** إلى مستند Word، **تطبيق الظل على الشكل**، **ضبط ضبابية الظل**، وأخيرًا **حفظ Word مع الشكل** باستخدام Aspose.Words for Python. يمكن توسيع النمط نفسه لتشمل أنواع أشكال أخرى، ألوانًا، وتأثيرات مختلفة، مما يمنحك سيطرة كاملة على رسومات المستند دون الاعتماد على أتمتة Office.

**الخطوات التالية**

- جرب `Shape.fill` لإضافة تدرجات أو خلفيات صورة.  
- استخدم كائنات `Paragraph` لوضع نص داخل المستطيل.  
- اجمع عدة أشكال لبناء مخططات معقدة، ثم صدّرها إلى PDF للتوزيع.  

لا تتردد في تعديل الكود لاحتياجاتك في التقارير أو القوالب، وشارك نتائجك في التعليقات!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}