---
category: general
date: 2026-06-17
description: تعلم كيفية حفظ المستند أثناء إضافة ظل مخصص إلى شكل مستطيل في بايثون باستخدام
  Aspose.Words. يتضمن كيفية إضافة الظل، إنشاء المستطيل، تطبيق الظل، وتعيين الشفافية.
draft: false
keywords:
- how to save document
- how to add shadow
- how to create rectangle
- how to apply shadow
- how to set opacity
language: ar
og_description: دليل خطوة بخطوة حول كيفية حفظ المستند، إضافة الظل، إنشاء مستطيل، تطبيق
  الظل، وتعيين الشفافية باستخدام Aspose.Words للبايثون.
og_title: كيفية حفظ المستند مع مستطيل مُظلَل – دورة بايثون كاملة
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Learn how to save document while adding a custom shadow to a rectangle
    shape in Python using Aspose.Words. Includes how to add shadow, create rectangle,
    apply shadow, and set opacity.
  headline: How to Save Document with a Shadowed Rectangle – Full Python Guide
  type: TechArticle
tags:
- Aspose.Words
- Python
- Document Automation
title: كيفية حفظ المستند مع مستطيل مُظلَّل – دليل بايثون كامل
url: /ar/python/images-shapes/how-to-save-document-with-a-shadowed-rectangle-full-python-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية حفظ المستند مع مستطيل مظلل – دليل بايثون كامل

هل تساءلت يومًا **كيفية حفظ المستند** الذي يحتوي على مستطيل مظلل بشكل جميل؟ ربما تقوم بإنشاء مولد تقارير وتحتاج إلى تلك اللمسة البصرية الإضافية—​أنت لست وحدك. في هذا الدرس سنستعرض **كيفية إضافة الظل** إلى شكل، **كيفية إنشاء مستطيل**، **كيفية تطبيق الظل**، وأخيرًا **كيفية ضبط الشفافية** قبل أن **نحفظ المستند** فعليًا.

سنستخدم Aspose.Words for Python via .NET، مكتبة قوية تتيح لك التعامل مع ملفات Word دون الحاجة إلى تثبيت Office. بنهاية هذا الدليل ستحصل على سكريبت جاهز للتنفيذ ينتج ملف *.docx* يحتوي على مستطيل يبدو كأنه يطفو عن الصفحة. لا إطالة، فقط حل عملي من البداية حتى النهاية.

## ما ستتعلمه

- الكود الدقيق اللازم **إنشاء مستطيل** شكل برمجيًا.  
- كيفية تمكين **تأثير الظل المخصص** وتعديل الضبابية، المسافة، الاتجاه، اللون، و**الشفافية**.  
- النداء الدقيق الذي **يحفظ المستند** على القرص، بما في ذلك مراعاة مسار المجلد.  
- نصائح لضبط معلمات الظل لأنماط بصرية مختلفة.  

**المتطلبات المسبقة:** Python 3.8+، Aspose.Words for Python via .NET (التثبيت عبر `pip install aspose-words`)، ومجلد قابل للكتابة على جهازك. هذا كل شيء—لا تبعيات إضافية.

![لقطة شاشة توضح كيفية حفظ المستند مع مستطيل مظلل](shadowed_rectangle.png "كيفية حفظ المستند مع مستطيل مظلل")

## الخطوة 1: إعداد المشروع واستيراد Aspose.Words

قبل أن نغوص في الأشكال، دعنا نتأكد من توفر المكتبة.

```python
# Install Aspose.Words if you haven’t already:
# pip install aspose-words

import aspose.words as aw
```

> **نصيحة احترافية:** استخدم بيئة افتراضية حتى يبقى تثبيت Python العام نظيفًا. كما يجعل من السهل تثبيت نسخة Aspose.Words التي اختبرت معها.

## الخطوة 2: كيفية إنشاء شكل مستطيل

إنشاء مستطيل هو الأساس—​بدون شكل لا يوجد ما يُظلله. توفر فئة `DocumentBuilder` طريقة سلسة لإدراج الأشكال مباشرةً في المستند.

```python
# Step 2: Create a new blank document and a builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# Insert a rectangle of 200x100 points (about 2.78 x 1.39 inches)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

**لماذا هذا مهم:** تُعيد طريقة `insert_shape` كائن `Shape` يمكننا تعديله لاحقًا. تُعبّر الأبعاد بالنقاط (1 pt = 1/72 in)، مما يمنحك تحكمًا دقيقًا في الحجم النهائي.

### تخصيص المستطيل (اختياري)

قد ترغب في تغيير التعبئة أو الحد:

```python
rectangle.fill_color = aw.drawing.Color.light_blue
rectangle.line_format.width = 2.0  # points
rectangle.line_format.color = aw.drawing.Color.dark_blue
```

هذه الأسطر اختيارية لكنها توضح كيفية تنسيق المستطيل قبل إضافة الظل.

## الخطوة 3: كيفية إضافة الظل – تمكين التأثير

الآن للجزء الممتع: إضافة الظل. تُظهر Aspose.Words خاصية `shadow_effect` التي تحتوي على جميع إعدادات الظل.

```python
# Step 3: Enable and configure a custom shadow for the rectangle
shadow = rectangle.shadow_effect
shadow.enabled = True               # Turn the shadow on
shadow.blur_radius = 5.0            # Softness of the shadow edge (points)
shadow.distance = 3.0               # How far the shadow is offset (points)
shadow.direction = 45               # Angle in degrees (0 = left, 90 = down)
shadow.color = aw.drawing.Color.black
shadow.opacity = 0.6                # 60% opaque – this is where we **how to set opacity**
```

**لماذا نضبط كل خاصية:**

- **`blur_radius`** ينعّم الحافة، مما يجعل الظل يبدو أكثر طبيعية.  
- **`distance`** يبعد الظل عن الشكل؛ قيمة أكبر تُنشئ تأثير “الطفو”.  
- **`direction`** يحدد من أين يأتي مصدر الضوء—​45° يعطي إسقاطًا قطريًا.  
- **`color`** و **`opacity`** يتحكمان في الوزن البصري؛ اللون الأسود شبه الشفاف يعمل جيدًا في معظم المستندات.  

### حالات حافة وتنوعات

- **ضبابية كبيرة جدًا:** إذا ضبطت `blur_radius` فوق 20، قد يصبح الظل غير قابل للتمييز عن الشكل—​استخدمه باعتدال.  
- **شفافية كاملة:** ضبط `opacity = 1.0` ينتج ظلًا أسودًا صلبًا؛ جيد للعناوين الدرامية.  
- **بدون ضبابية:** `blur_radius = 0` يخلق ظلًا حادًا، يشبه الرسومات المتجهية.

## الخطوة 4: كيفية تطبيق إعدادات الظل وحفظ المستند

مع تكوين المستطيل وظله، الخطوة الأخيرة هي حفظ الملف. هنا نجيب أخيرًا على **كيفية حفظ المستند**.

```python
# Step 4: Save the document with the shadowed rectangle
output_path = "output/shadowed_rectangle.docx"
document.save(output_path)

print(f"Document saved successfully at: {output_path}")
```

**ملاحظات مهمة حول الحفظ:**

- يجب أن يكون المجلد (`output/` في المثال) موجودًا؛ وإلا سيُطلق `document.save` استثناء `FileNotFoundError`. استخدم `os.makedirs('output', exist_ok=True)` مسبقًا إذا احتجت لإنشائه برمجيًا.  
- تحدد Aspose.Words تنسيق الملف تلقائيًا من الامتداد، لذا فإن `.docx` يمنحك مستند Word حديث. يمكنك أيضًا حفظه كـ `.pdf` بتغيير الامتداد.

## السكريبت الكامل – جميع الخطوات في مكان واحد

بجمع كل شيء معًا، إليك السكريبت الكامل الجاهز للتنفيذ:

```python
import os
import aspose.words as aw

# Ensure the output directory exists
os.makedirs("output", exist_ok=True)

# 1️⃣ Create a blank document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert a rectangle (200x100 points)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Optional styling (feel free to comment out)
rectangle.fill_color = aw.drawing.Color.light_blue
rectangle.line_format.width = 2.0
rectangle.line_format.color = aw.drawing.Color.dark_blue

# 3️⃣ Configure shadow effect
shadow = rectangle.shadow_effect
shadow.enabled = True
shadow.blur_radius = 5.0
shadow.distance = 3.0
shadow.direction = 45
shadow.color = aw.drawing.Color.black
shadow.opacity = 0.6  # How to set opacity

# 4️⃣ Save the document (how to save document)
output_file = "output/shadowed_rectangle.docx"
document.save(output_file)

print(f"Document saved successfully at: {output_file}")
```

تشغيل هذا السكريبت ينتج `output/shadowed_rectangle.docx`. افتحه في Microsoft Word، وسترى مستطيلًا أزرق فاتحًا مع ظل أسود شبه شفاف خفيف يتحرك نحو الأسفل‑اليمين.

## أسئلة شائعة ومشكلات محتملة

- **“هل يمكنني استخدام نوع شكل مختلف؟** بالتأكيد. استبدل `aw.drawing.ShapeType.RECTANGLE` بـ `CIRCLE` أو `ELLIPSE` أو أي قيمة تعداد مدعومة أخرى. يعمل API الظل بنفس الطريقة.  
- **“ماذا لو احتجت إلى لون ظل مختلف؟** فقط اضبط `shadow.color` إلى أي `aw.drawing.Color` تريد، مثل `aw.drawing.Color.gray`.  
- **“هل قيمة الشفافية دائمًا بين 0 و 1؟** نعم. القيم خارج هذا النطاق تُقيد، لكن من الأفضل البقاء ضمن الفاصل 0‑1 للحصول على نتائج متوقعة.  
- **“هل أحتاج إلى استدعاء `document.update_page_layout()` قبل الحفظ؟** لا. تتعامل Aspose.Words مع التخطيط تلقائيًا عند الحفظ، رغم أنه يمكنك استدعاؤه يدويًا إذا كنت تجري تعديلات كبيرة وتحتاج إلى بيانات تخطيطية وسيطة.

## الخطوات التالية – إلى أين تذهب من هنا

الآن بعد أن عرفت **كيفية حفظ المستند** مع مستطيل مظلل، قد ترغب في استكشاف:

- **كيفية إضافة الظل** إلى عناصر أخرى مثل الصور أو مربعات النص.  
- **كيفية إنشاء مستطيل** بتعبئات تدرجية للحصول على مرئيات أغنى.  
- **كيفية تطبيق الظل** بشكل ديناميكي بناءً على مدخلات المستخدم (مثلاً، السماح لواجهة المستخدم بالتحكم في نصف قطر الضبابية).  
- **كيفية ضبط الشفافية** لأشكال متعددة متراكبة لتحقيق تأثيرات العمق.  

كل من هذه المواضيع يبني على نفس المفاهيم الأساسية التي غطيناها، لذا أنت في موقع جيد لتوسيع الحل.

**الخلاصة:** لقد أتقنت الآن سير العمل الكامل—من إنشاء مستطيل، تكوين ظله، تعديل الشفافية، وحتى **كيفية حفظ المستند** مع جميع هذه الإعدادات محفوظة. جرّبه، عدّل المعلمات، وشاهد ملفات Word الخاصة بك تكتسب مظهرًا احترافيًا ثلاثي الأبعاد.

برمجة سعيدة، ولا تتردد في ترك تعليق إذا واجهت أي صعوبات!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء مستند Word فارغ مع شكل مستطيل مظلل – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [كيفية حفظ Markdown من Word – دليل بايثون كامل](/words/english/python-net/document-conversion/how-to-save-markdown-from-word-complete-python-guide/)
- [كيفية إضافة الظل في C# – دليل برمجة كامل](/words/english/python-net/images-shapes/how-to-add-shadow-in-c-complete-programming-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}