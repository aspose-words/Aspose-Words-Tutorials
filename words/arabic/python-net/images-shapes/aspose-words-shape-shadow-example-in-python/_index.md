---
category: general
date: 2026-11-18
description: مثال ظل الشكل في Aspose.Words يوضح كيفية إضافة ظل إلى شكل في Word باستخدام
  بايثون. اتبع هذا الدليل خطوة بخطوة لتعديل وحفظ المستند.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words shape shadow example
- python shape shadow
- Aspose.Words for Python
- modify shape shadow
- document manipulation Aspose
language: ar
lastmod: 2026-11-18
og_description: مثال ظل الشكل في Aspose.Words يوضح إضافة ظل إلى شكل Word باستخدام
  Python. تعلم الكود الكامل، ولماذا كل خطوة مهمة، وكيفية تكييفه.
og_image_alt: Aspose.Words shape shadow example – Word document displaying a shape
  with a shadow applied using Python
og_title: مثال على ظل الشكل في Aspose.Words – دليل بايثون
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Aspose.Words shape shadow example shows how to add a shadow to a Word
    shape using Python. Follow this step‑by‑step guide to modify and save the document.
  headline: Aspose.Words shape shadow example in Python
  type: TechArticle
- description: Aspose.Words shape shadow example shows how to add a shadow to a Word
    shape using Python. Follow this step‑by‑step guide to modify and save the document.
  name: Aspose.Words shape shadow example in Python
  steps:
  - name: Expected outcome
    text: Open `output.docx` in Microsoft Word. The first shape you added should now
      display a soft shadow that is offset by 2 pt horizontally and vertically, with
      a blur radius of 5 pt. All other content remains unchanged.
  - name: 'Alternative: Find a shape by name'
    text: 'If your document contains several shapes, you might prefer to locate a
      specific one:'
  - name: Working with multiple shapes
    text: 'If you need to apply the same shadow to every shape, iterate over the node
      collection:'
  - name: Applying a shadow to a specific shape type
    text: You can filter by `ShapeType` (e.g., `aw.ShapeType.IMAGE`). This is useful
      when you only want to affect pictures, not AutoShapes.
  - name: Handling documents without shapes
    text: The script already raises a clear `ValueError` if no shape is found. In
      production code you might log the issue and continue processing other files.
  - name: Compatibility notes
    text: '* The code works with **Aspose.Words for Python via .NET** version 23.10
      and later. * The shadow effect is supported in Word 2007+ (`.docx`). Older formats
      (`.doc`) will lose the effect after conversion.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: مثال على ظل الشكل في Aspose.Words باستخدام بايثون
url: /ar/python/images-shapes/aspose-words-shape-shadow-example-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# مثال ظل الشكل في Aspose.Words باستخدام بايثون

يوضح مثال ظل الشكل في Aspose.Words كيفية إضافة تأثير الظل إلى شكل في مستند Word باستخدام بايثون. في هذا الدرس ستحصل على برنامج نصي كامل قابل للتنفيذ يقوم بتحميل مستند، ضبط الظل، وحفظ النتيجة.

يُعد تطبيق الظل على الشكل طريقة شائعة لتحسين التسلسل البصري في التقارير، الكتيبات، أو الفواتير. يعمل الكود أدناه مع Aspose.Words for Python via .NET ولا يتطلب أي مكتبات طرف ثالث إضافية.

## ما ستتعلمه

* كيفية تحميل ملف `.docx` باستخدام **Aspose.Words for Python**.  
* كيفية تحديد أول شكل (بما في ذلك الأشكال داخل الجداول أو المجموعات).  
* كيفية ضبط ضبابية الظل، الإزاحة الأفقية، والإزاحة العمودية.  
* كيفية حفظ المستند المعدل مع الحفاظ على جميع المحتويات الأخرى.  

**المتطلبات المسبقة**

* Python 3.8 أو أحدث.  
* Aspose.Words for Python via .NET مثبت (`pip install aspose-words`).  
* مستند Word (`input.docx`) يحتوي على شكل واحد على الأقل (مثل صورة، AutoShape، أو مربع نص).  

إذا كنت بحاجة لتثبيت المكتبة، نفّذ:

```bash
pip install aspose-words
```

## نظرة عامة على مثال ظل الشكل في Aspose.Words

البرنامج النصي التالي هو الحل الكامل. يتبع الخطوات الأربع المنطقية لتدفق عمل **تعديل المستندات باستخدام Aspose** النموذجي: التحميل، التحديد، التعديل، والحفظ.

```python
import aspose.words as aw

# ----------------------------------------------------------------------
# Step 1: Load the Word document
# ----------------------------------------------------------------------
# Replace YOUR_DIRECTORY with the path that contains input.docx.
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)

# ----------------------------------------------------------------------
# Step 2: Access the first shape (including descendants)
# ----------------------------------------------------------------------
# NodeType.SHAPE searches for any shape node. The third argument (True)
# tells Aspose.Words to search recursively through all child nodes.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# Verify that a shape was found; raise a clear error if not.
if shape is None:
    raise ValueError("No shape found in the document. Ensure input.docx contains a shape.")

# ----------------------------------------------------------------------
# Step 3: Configure the shape's shadow
# ----------------------------------------------------------------------
# The Shadow object controls visual appearance. Adjust the properties
# to achieve the desired effect.
shape.shadow.blur = 5          # Softness of the shadow (0‑15 is typical)
shape.shadow.offset_x = 2      # Horizontal displacement in points
shape.shadow.offset_y = 2      # Vertical displacement in points

# Optional: Change shadow color or transparency if needed.
# shape.shadow.color = aw.Color.black
# shape.shadow.transparency = 0.5

# ----------------------------------------------------------------------
# Step 4: Save the modified document
# ----------------------------------------------------------------------
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)

print(f"Shadow applied successfully. Saved to {output_path}")
```

### النتيجة المتوقعة

افتح `output.docx` في Microsoft Word. يجب أن يعرض الشكل الأول الذي أضفته الآن ظلًا ناعمًا مُزاح بمقدار 2 pt أفقيًا وعموديًا، مع نصف قطر ضبابية قدره 5 pt. جميع المحتويات الأخرى تبقى دون تغيير.

## الخطوة 1: تحميل مستند Word

يُعد تحميل المستند العملية الأولى في أي تدفق عمل **Aspose.Words for Python**. تقوم فئة `Document` بتحليل الملف وإنشاء نموذج كائن في الذاكرة. نظرًا لأن المكتبة تعمل على منصة .NET، يمكنها معالجة الملفات الكبيرة بكفاءة.

*لماذا هذا مهم:* تحميل المستند مرة واحدة والاحتفاظ بمرجع (`doc`) يجنب عمليات الإدخال/الإخراج المتكررة، مما يحسن الأداء عند الحاجة لتطبيق تعديلات متعددة.

## الخطوة 2: الوصول إلى الشكل

يمكن أن تكون الأشكال أطفالًا مباشرةً لجسم المستند، أو يمكن أن تكون متداخلة داخل جداول، مجموعات، أو قماش رسم. يستخدم `get_child(NodeType.SHAPE, 0, True)` البحث المتكرر ويعيد أول شكل مطابق.

*لماذا هذا مهم:* علم `True` يضمن عدم تفويت الأشكال المخفية داخل عقد أخرى. إذا حذفت هذا العلم، فستُؤخذ فقط الأشكال ذات المستوى الأعلى في الاعتبار، وستُعيد العديد من المستندات الواقعية `None`.

### بديل: العثور على شكل حسب الاسم

إذا كان مستندك يحتوي على عدة أشكال، قد تفضّل تحديد شكل معين:

```python
shape = doc.get_child(aw.NodeType.SHAPE, lambda n: n.name == "MyLogo", True)
```

هذا المقتطف يوضح تنويعة **python shape shadow** التي تُفلتر حسب خاصية `name` للشكل.

## الخطوة 3: ضبط ظل الشكل

خاصية `shadow` لكائن `Shape` تمنحك تحكمًا دقيقًا في التأثير البصري. الثلاثة خصائص التي يتم تعديلها غالبًا هي:

| الخاصية | النطاق المعتاد | التأثير البصري |
|----------|---------------|---------------|
| `blur`   | 0 – 15        | القيم الأعلى تُنتج حافة أكثر نعومة. |
| `offset_x` | –10 – 10   | القيم الإيجابية تحرك الظل إلى اليمين. |
| `offset_y` | –10 – 10   | القيم الإيجابية تحرك الظل إلى الأسفل. |

يمكنك أيضًا تعديل `color`، `transparency`، `visible`، و `style`. يحدد المثال ضبابية معتدلة وإزاحة طفيفة للحفاظ على ظلال هادئة.

**نصيحة احترافية:** عندما يكون للشكل ظل موجود مسبقًا، فإن الخصائص أعلاه تستبدل الإعدادات الحالية. إذا كنت بحاجة للحفاظ على النمط الأصلي، اقرأ القيم الحالية قبل تعديلها.

## الخطوة 4: حفظ المستند المعدل

استدعاء `doc.save()` يكتب تمثيل الذاكرة مرة أخرى إلى ملف `.docx`. تقوم Aspose.Words تلقائيًا بتحديث جميع العلاقات الداخلية، لذا يبقى ملف الإخراج متوافقًا بالكامل مع Microsoft Word.

*لماذا هذا مهم:* حفظ المستند مرة واحدة فقط في نهاية العملية يقلل من خطر فساد الملف ويحسن السرعة العامة، خاصةً عند معالجة العديد من المستندات في دفعة واحدة.

## تنويعات شائعة وحالات حافة

### العمل مع أشكال متعددة

إذا كنت بحاجة لتطبيق نفس الظل على كل شكل، يمكنك التكرار عبر مجموعة العقد:

```python
for shp in doc.get_child_nodes(aw.NodeType.SHAPE, True):
    shp.shadow.blur = 5
    shp.shadow.offset_x = 2
    shp.shadow.offset_y = 2
```

### تطبيق ظل على نوع شكل محدد

يمكنك الفلترة حسب `ShapeType` (مثل `aw.ShapeType.IMAGE`). هذا مفيد عندما تريد التأثير فقط على الصور، وليس على AutoShapes.

```python
for shp in doc.get_child_nodes(aw.NodeType.SHAPE, True):
    if shp.shape_type == aw.ShapeType.IMAGE:
        shp.shadow.blur = 4
```

### معالجة مستندات بدون أشكال

يقوم البرنامج النصي بالفعل بإثارة استثناء `ValueError` واضح إذا لم يُعثر على أي شكل. في كود الإنتاج قد تقوم بتسجيل المشكلة ومتابعة معالجة ملفات أخرى.

### ملاحظات التوافق

* يعمل الكود مع **Aspose.Words for Python via .NET** الإصدار 23.10 وما بعده.  
* تأثير الظل مدعوم في Word 2007+ (`.docx`). الصيغ القديمة (`.doc`) ستفقد التأثير بعد التحويل.

## الخلاصة

هذا **aspose.words shape shadow example** يرشّحك عبر تحميل ملف Word، تحديد شكل، ضبط ظله، وحفظ النتيجة باستخدام **Aspose.Words for Python**. لديك الآن نمط قابل لإعادة الاستخدام لأي سيناريو **تعديل مستندات Aspose** يتضمن تحسينات بصرية.

بعد ذلك، قد ترغب في استكشاف:

* إضافة تعبئات تدرجية أو أنماط خطوط إلى الأشكال (`modify shape shadow` وغيرها من الخصائص البصرية).  
* دمج ضبط الظل مع تنسيق النص لإنشاء قوالب مصممة بالكامل.  
* أتمتة العملية لمجموعة من المستندات باستخدام `os.listdir` والنمط الموضح أعلاه.

لا تتردد في تجربة مستويات ضبابية مختلفة، إزاحات، وألوان لتتناسب مع إرشادات العلامة التجارية الخاصة بك. برمجة سعيدة!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [Add Shadow to Shape in Python – Complete Aspose.Words Tutorial](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [How to set shadow on a shape in Aspose.Words for Python](/words/english/python-net/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-for-python/)
- [How to save PNG and add shadow to shape with Aspose.Words](/words/english/python-net/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}