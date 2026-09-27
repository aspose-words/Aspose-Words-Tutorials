---
category: general
date: 2026-09-27
description: تعلم كيفية تعيين الظل على شكل باستخدام Aspose.Words للبايثون. يغطي هذا
  الدليل إضافة الظل إلى الشكل، تطبيق تأثير الظل، وتعيين لون الظل.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to set shadow
- add shadow to shape
- apply shadow effect
- set shadow color
- how to add shadow
language: ar
lastmod: 2026-09-27
og_description: كيفية تعيين الظل على شكل باستخدام Aspose.Words للبايثون. اتبع الدليل
  خطوة بخطوة لإضافة ظل إلى الشكل، وتطبيق تأثير الظل، وتحديد لون الظل.
og_image_alt: Screenshot showing how to set shadow on a shape in a Word document
og_title: كيفية تعيين الظل على شكل في Aspose.Words للبايثون
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to set shadow on a shape with Aspose.Words for Python. This
    guide covers add shadow to shape, apply shadow effect, and set shadow color.
  headline: How to set shadow on a shape in Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Shapes
- Shadow effect
title: كيفية تعيين الظل على شكل في Aspose.Words للبايثون
url: /ar/python/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تعيين الظل على شكل في Aspose.Words للـ Python

إذا كنت بحاجة إلى **كيفية تعيين الظل** لكائن رسم، يوضح هذا الدليل العملية بالكامل. سترى كيفية إضافة ظل إلى الشكل، وتكوين ضبابية الظل، والإزاحة، واللون، وحفظ المستند المحدث دون مغادرة الشيفرة.

يفترض هذا الدليل أنك تمتلك بالفعل بيئة أساسية لـ Aspose.Words للـ Python. بحلول نهاية المقال ستتمكن من تطبيق تأثير ظل احترافي على أي شكل في ملف DOCX.

## المتطلبات المسبقة

* Python 3.8+ مثبت.
* Aspose.Words للـ Python عبر .NET (`pip install aspose-words`) مثبت.
* مستند Word (`input.docx`) يحتوي على شكل واحد على الأقل (مثل مستطيل أو صورة).  
  إذا كان المستند فارغًا، سيقوم الشيفرة بإنشاء شكل جديد للتوضيح.

هذه العناصر تضمن أن الخطوات التالية ستعمل دون أخطاء استيراد.

## الخطوة 1: تحميل أو إنشاء مستند Word

العملية الأولى هي الحصول على كائن `Document`. يمكنك إما تحميل ملف موجود أو إنشاء ملف جديد.

```python
import aspose.words as aw

# Load an existing document, or create a new blank document if the file does not exist.
try:
    doc = aw.Document("YOUR_DIRECTORY/input.docx")
except Exception:
    doc = aw.Document()          # Creates an empty document
    # Optional: add a paragraph so the document is not completely empty.
    builder = aw.DocumentBuilder(doc)
    builder.writeln("Document created for shadow demo.")
```

*لماذا هذه الخطوة مهمة*: كائن `Document` هو نقطة الدخول لجميع عمليات معالجة Word. بدون هذا الكائن لا يمكنك الوصول إلى الأشكال أو تطبيق التأثيرات البصرية.

## الخطوة 2: استرجاع الشكل المستهدف

لتعديل مظهر الشكل تحتاج إلى مرجع إلى عقدة الشكل. المثال أدناه يجلب أول شكل موجود في شجرة المستند.

```python
# Retrieve the first shape in the document tree.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# If the document has no shapes, create one for demonstration purposes.
if shape is None:
    builder = aw.DocumentBuilder(doc)
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
    shape.wrap_type = aw.drawing.WrapType.INLINE
```

*لماذا هذه الخطوة مهمة*: `add shadow to shape` يتطلب كائن شكل ملموس. يتعامل الشيفرة بأمان مع الحالة التي لا يحتوي فيها المستند على أشكال، مما يضمن أن الدليل يعمل لكل القارئ.

## الخطوة 3: تكوين مظهر الظل

الآن يمكنك **تطبيق تأثير الظل** عن طريق تعديل خاصية `shadow` للشكل. الإعدادات التالية تعطي ظلًا خفيفًا ومظلمًا.

```python
# Set the shadow blur radius (softness). Larger values produce a more diffused shadow.
shape.shadow.blur = 5.0

# Horizontal displacement of the shadow in points.
shape.shadow.offset_x = 2.0

# Vertical displacement of the shadow in points.
shape.shadow.offset_y = 2.0

# Set the shadow color. This demonstrates **set shadow color** to black.
shape.shadow.color = aw.Color.black

# Enable the shadow (some older versions require explicit visibility).
shape.shadow.visible = True
```

*لماذا كل خاصية مهمة*:

| الخاصية | التأثير |
|----------|--------|
| `blur`   | يتحكم في مدى وضوح الظل. |
| `offset_x` / `offset_y` | يحدد الاتجاه والمسافة من الشكل. |
| `color`  | يحدد لون الظل؛ يمكنك استخدام أي `aw.Color`. |
| `visible`| يضمن أن الظل يتم عرضه في ملف الإخراج. |

يمكنك استبدال `aw.Color.black` بـ `aw.Color.from_argb(255, 0, 0, 0)` للحصول على قيمة RGBA مخصصة، أو أي لون معرف مسبقًا آخر.

## الخطوة 4: حفظ المستند المعدل

بعد تكوين الظل، احفظ التغييرات في ملف جديد.

```python
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved with shadow effect at: {output_path}")
```

عند فتح `output.docx` في Microsoft Word، سيظهر الشكل المحدد بظل أسود ناعم مُزاح بمقدار 2 pt إلى اليمين و2 pt إلى الأسفل.

## مثال كامل يعمل

جمع جميع الخطوات معًا يعطي سكريبت مستقل يمكنك نسخه ولصقه في بيئة التطوير المتكاملة (IDE) الخاصة بك.

```python
import aspose.words as aw

def add_shadow_to_first_shape(input_path: str, output_path: str):
    # Load or create the document.
    try:
        doc = aw.Document(input_path)
    except Exception:
        doc = aw.Document()
        builder = aw.DocumentBuilder(doc)
        builder.writeln("Document created for shadow demo.")

    # Retrieve the first shape; create one if none exist.
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
    if shape is None:
        builder = aw.DocumentBuilder(doc)
        shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
        shape.wrap_type = aw.drawing.WrapType.INLINE

    # Apply shadow settings.
    shape.shadow.blur = 5.0
    shape.shadow.offset_x = 2.0
    shape.shadow.offset_y = 2.0
    shape.shadow.color = aw.Color.black
    shape.shadow.visible = True

    # Save the result.
    doc.save(output_path)
    print(f"Shadow applied and saved to {output_path}")

# Example usage
if __name__ == "__main__":
    add_shadow_to_first_shape(
        input_path="YOUR_DIRECTORY/input.docx",
        output_path="YOUR_DIRECTORY/output.docx"
    )
```

تشغيل السكريبت ينتج `output.docx` حيث يحمل الشكل الأول الظل المُكوَّن.

## المشكلات الشائعة وكيفية تجنبها

| المشكلة | السبب | الحل |
|-------|--------|-----|
| `shape` هو `None` حتى بعد تحميل المستند | المستند لا يحتوي على كائنات رسم. | استخدم كتلة إنشاء الشكل الاحتياطي المعروضة في الخطوة 2. |
| الظل لا يظهر في Word | `shape.shadow.visible` ترك كـ `False` أو تم حفظ المستند بصيغة أقدم (مثل `.doc`). | تأكد من أن `visible = True` واحفظ كـ `.docx`. |
| اللون يبدو مختلفًا عما هو متوقع | سمة المستند تتجاوز الألوان الصريحة. | قم بتعيين `shape.shadow.color` بعد تعطيل تجاوز السمة، أو استخدم `aw.Color.from_argb`. |

## توسيع التأثير (الخطوات التالية)

الآن بعد أن عرفت **كيفية إضافة الظل**، يمكنك استكشاف التحسينات ذات الصلة:

* **apply shadow effect** مع تدرج أو ظلال متعددة عن طريق تعديل الخصائص الفرعية لـ `shape.shadow`.
* استخدم **set shadow color** بشكل ديناميكي بناءً على إدخال المستخدم أو ألوان السمة.
* اجمع **add shadow to shape** مع إجراءات تنسيق أخرى مثل الدوران، نمط الخط، أو تأثيرات ثلاثية الأبعاد.
* قم بأتمتة إضافة الظل لكل شكل في المستند عن طريق التكرار عبر `doc.get_child_nodes(aw.NodeType.SHAPE, True)`.

## الخلاصة

أصبح لديك الآن حل كامل وقابل للتنفيذ لـ **كيفية تعيين الظل** على شكل باستخدام Aspose.Words للـ Python. يغطي الدليل تحميل المستند، استرجاع أو إنشاء شكل، تكوين الضبابية، الإزاحة، و**set shadow color**، وأخيرًا حفظ الملف. طبق هذا النمط على أي شكل في مشاريع الأتمتة الخاصة بك وجرب تعديلات بصرية إضافية لتلبية متطلبات التصميم الخاصة بك.

--- 

*لا تتردد في تعديل الشيفرة لأنواع أشكال أخرى، ألوان، أو قيم إزاحة. إذا واجهت أي مشاكل، فإن مراجعة جدول “المشكلات الشائعة” هي خطوة أولى جيدة.*

## ما الذي ينبغي أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إضافة ظل إلى الشكل في C# – دليل كامل لتطبيق تأثير الظل](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-c-complete-guide-to-apply-shadow-effe/)
- [إضافة ظل إلى الشكل في Word – دليل كامل لـ Aspose.Words](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [إنشاء شكل مستطيل، إضافة ظل وحفظ كـ PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}