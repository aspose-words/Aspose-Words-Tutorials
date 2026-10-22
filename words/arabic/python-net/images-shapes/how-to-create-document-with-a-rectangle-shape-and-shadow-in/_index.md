---
category: general
date: 2026-10-04
description: كيفية إنشاء مستند في بايثون وإضافة ظل إلى الشكل باستخدام Aspose.Words.
  تعلّم تعيين لون الظل، وإدراج شكل مستطيل، وتخصيص الظل الخارجي.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create document
- add shadow to shape
- set shadow color
- insert rectangle shape
- how to add shadow
language: ar
lastmod: 2026-10-04
og_description: كيفية إنشاء مستند في بايثون وإضافة ظل إلى الشكل. يوضح لك هذا الدليل
  كيفية تعيين لون الظل، وإدراج شكل مستطيل، وتطبيق ظل خارجي باستخدام Aspose.Words.
og_image_alt: Python code inserting a rectangle shape with a visible shadow into a
  Word document
og_title: كيفية إنشاء مستند بشكل مستطيل وظل في بايثون
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  headline: How to create document with a rectangle shape and shadow in Python
  type: TechArticle
- description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  name: How to create document with a rectangle shape and shadow in Python
  steps:
  - name: Why does the shadow sometimes appear invisible?
    text: The shadow is only rendered if `shadow.visible` is set to `True` **and**
      the shape’s `wrap_type` allows it to be displayed. An inline shape works reliably;
      floating shapes may require additional layout adjustments.
  - name: How can I change the shadow color to match a brand palette?
    text: 'Replace `aw.drawing.Color.black` with a custom RGB value:'
  - name: What if I need the shape to appear behind text?
    text: Set the wrap type to `WrapType.BEHIND` and adjust the `z_order_position`
      if necessary. Keep in mind that some viewers may render behind‑text shapes differently.
  - name: Can I apply the same shadow settings to multiple shapes?
    text: Yes. Create a helper function that configures the shadow and call it for
      each shape you insert. This promotes code reuse and ensures consistent styling.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: كيفية إنشاء مستند بشكـل مستطيل وظل في بايثون
url: /ar/python/images-shapes/how-to-create-document-with-a-rectangle-shape-and-shadow-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مستند يحتوي على شكل مستطيل وظل في Python

إذا كنت بحاجة إلى **كيفية إنشاء مستند** يحتوي على مستطيل مُنسق، فإن هذا الدليل يقدم حلاً كاملاً. ستتعرف على كيفية **إضافة ظل إلى الشكل**، وتعيين لون الظل، والتحكم في إزاحته وتلطيخه—كل ذلك باستخدام Aspose.Words for Python. في نهاية البرنامج التعليمي يمكنك إنشاء ملف `.docx` يبدو مصقولًا وجاهزًا للتوزيع.

الخطوات أدناه تغطي كل شيء بدءًا من تثبيت المكتبة وحتى تخصيص مظهر الظل. لا حاجة إلى وثائق خارجية؛ الكود جاهز للنسخ، التشغيل، والتكييف مع مشاريعك الخاصة. ستتعلم أيضًا كيفية **إدراج شكل مستطيل**، اختيار **نمط الظل الخارجي**، ومعالجة المشكلات الشائعة مثل الظلال غير المرئية أو إعدادات الالتفاف غير الصحيحة.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* Python 3.8 أو أحدث مثبت.
* ترخيص فعال لـ Aspose.Words for Python (أو مفتاح تقييم مجاني).
* إلمام أساسي ببرمجة Python.
* إمكانية الوصول إلى موقع على نظام الملفات حيث سيتم حفظ المستند المُنشأ.

يمكنك تثبيت الـ SDK باستخدام pip:

```bash
pip install aspose-words
```

## الخطوة 1: استيراد المكتبة وإنشاء مستند فارغ جديد

إنشاء مستند جديد هو الإجراء الأول في أي سيناريو أتمتة Word. يُعطيك المُنشئ `aw.Document()` ملفًا فارغًا يمكنك ملؤه بالنصوص أو الصور أو الأشكال.

```python
import aspose.words as aw

# Create a new blank document
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

كائن `DocumentBuilder` يبسط عملية إدراج المحتوى. فهو يتتبع موضع المؤشر الحالي، بحيث يمكنك إضافة العناصر بشكل متسلسل دون الحاجة لإدارة الأقسام يدويًا.

## الخطوة 2: إدراج شكل مستطيل بالحجم المطلوب

يعمل شكل المستطيل كحاوية للعناصر البصرية. يمكنك تحديد عرضه وارتفاعه بالنقاط (1 pt ≈ 1/72 in).

```python
# Insert a rectangle shape that is 150 pt wide and 80 pt tall
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

في هذه المرحلة لا يمتلك الشكل أي تنسيق بصري، لذا يظهر كحدود بسيطة. الخطوات التالية ستمنحه العمق واللون.

## الخطوة 3: ضبط الشكل ليكون متدفقًا داخل النص المحيط

عندما يكون الشكل **متداخلًا** (inline)، يتصرف كحرف داخل الفقرة. هذا يضمن بقاء المستطيل في الموضع المتوقع داخل تخطيط المستند.

```python
# Make the shape inline so it follows the text flow
rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE
```

إذا كنت تفضل أن يطفو الشكل فوق النص، يمكنك استخدام `WrapType.SQUARE` أو `WrapType.TOP_BOTTOM`، لكن بالنسبة لمعظم التقارير يبقى الشكل المتداخل هو الأكثر استقرارًا في التخطيط.

## الخطوة 4: جعل الظل مرئيًا واختيار لونه

الظل غير المرئي لا يقدم أي فائدة بصرية. علم `visible` يُفعّل التأثير، وخصيصة `color` تحدد لونه. استخدام اللون الأسود يعطي عمقًا كلاسيكيًا وهادئًا.

```python
# Enable the shadow and set its color to black
rectangle_shape.shadow.visible = True
rectangle_shape.shadow.color = aw.drawing.Color.black
```

يمكنك استبدال `aw.drawing.Color.black` بأي لون آخر، مثل `aw.drawing.Color.gray` أو قيمة RGB مخصصة (`aw.drawing.Color.from_argb(255, 128, 128, 128)`).

## الخطوة 5: تحديد إزاحة الظل وتلطيخه لإضفاء العمق

الإزاحة تتحكم في مدى إزاحة الظل عن الشكل، بينما نصف قطر التلطيخ ينعّم الحواف. القيم الصغيرة تُنتج ظلًا حادًا؛ القيم الأكبر تُعطي مظهرًا أكثر نعومة.

```python
# Horizontal and vertical offset of 5 pt each
rectangle_shape.shadow.offset_x = 5
rectangle_shape.shadow.offset_y = 5

# Blur radius of 3 pt for a gentle feather
rectangle_shape.shadow.blur = 3
```

جرّب تعديل هذه الأرقام لتتناسب مع إرشادات التصميم الخاصة بك. للحصول على ظل قوي يمكنك زيادة كل من الإزاحة والتلطيخ.

## الخطوة 6: اختيار نمط الظل الخارجي

توفر Aspose.Words عدة أنماط للظل، مثل `INNER`، `OUTER`، و`PERSPECTIVE`. النمط **الخارجي** يضع الظل خارج حدود الشكل، وهو مثالي لمظهر نظيف واحترافي.

```python
# Apply an outer shadow style
rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

إذا رغبت في تأثير أكثر دراماتيكية، جرّب `ShadowStyle.PERSPECTIVE`—فهو يضيف ميلًا ثلاثي الأبعاد.

## الخطوة 7: حفظ المستند مع الشكل المظلل

الحفظ يُنهي الملف ويكتب جميع التنسيقات إلى القرص. اختر دليلًا لديك صلاحية كتابة فيه، ومنح الملف اسمًا وصفيًا.

```python
# Save the document to the desired location
output_path = "output/ShapeWithShadow.docx"
document.save(output_path)
print(f"Document saved to {output_path}")
```

تشغيل السكريبت ينتج ملف Word يحتوي على مستطيل بظل مرئي وملون. افتح الملف في Microsoft Word أو LibreOffice للتحقق من النتيجة.

## مثال كامل قابل للتنفيذ

فيما يلي السكريبت الكامل الذي يدمج جميع الخطوات التي نوقشت. انسخ الكود إلى ملف باسم `create_shadowed_shape.py` ونفّذه باستخدام `python create_shadowed_shape.py`.

```python
import aspose.words as aw
import os

def main():
    # Ensure the output directory exists
    output_dir = "output"
    os.makedirs(output_dir, exist_ok=True)

    # Step 1: Create a new blank document
    document = aw.Document()
    builder = aw.DocumentBuilder(document)

    # Step 2: Insert a rectangle shape of the desired size
    rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

    # Step 3: Set the shape to be inline with the text flow
    rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE

    # Step 4: Make the shadow visible and choose its color
    rectangle_shape.shadow.visible = True
    rectangle_shape.shadow.color = aw.drawing.Color.black

    # Step 5: Define the shadow's offset and blur to give it depth
    rectangle_shape.shadow.offset_x = 5   # horizontal offset in points
    rectangle_shape.shadow.offset_y = 5   # vertical offset in points
    rectangle_shape.shadow.blur = 3       # blur radius in points

    # Step 6: Choose an outer shadow style
    rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER

    # Step 7: Save the document with the shaped shadow
    output_path = os.path.join(output_dir, "ShapeWithShadow.docx")
    document.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    main()
```

**الناتج المتوقع**

عند فتح `ShapeWithShadow.docx`، ستلاحظ مستطيلًا واحدًا في وسط الصفحة. يرافق المستطيل ظل أسود خفيف مائل إلى أسفل‑يمين، مُلطّخ قليلًا لإضفاء العمق. الظل يلتزم بالنمط الخارجي، لذا لا يتقاطع مع داخل المستطيل.

## أسئلة شائعة وحالات خاصة

### لماذا يظهر الظل أحيانًا غير مرئي؟

يتم رسم الظل فقط إذا تم ضبط `shadow.visible` على `True` **و** سمح `wrap_type` الخاص بالشكل بعرضه. الشكل المتداخل يعمل بشكل موثوق؛ قد تتطلب الأشكال العائمة تعديلات إضافية في التخطيط.

### كيف يمكنني تغيير لون الظل ليتطابق مع لوحة ألوان العلامة التجارية؟

استبدل `aw.drawing.Color.black` بقيمة RGB مخصصة:

```python
rectangle_shape.shadow.color = aw.drawing.Color.from_argb(255, 0, 120, 215)  # corporate blue
```

### ماذا لو أردت أن يكون الشكل خلف النص؟

قم بضبط نوع الالتفاف إلى `WrapType.BEHIND` وعدّل `z_order_position` إذا لزم الأمر. ضع في الاعتبار أن بعض العارضات قد تُظهر الأشكال الخلفية بطريقة مختلفة.

### هل يمكنني تطبيق نفس إعدادات الظل على عدة أشكال؟

نعم. أنشئ دالة مساعدة تُكوّن الظل واستدعها لكل شكل تُدرجه. هذا يعزز إعادة استخدام الكود ويضمن تنسيقًا موحدًا.

```python
def apply_shadow(shape, color=aw.drawing.Color.black, offset=5, blur=3):
    shape.shadow.visible = True
    shape.shadow.color = color
    shape.shadow.offset_x = offset
    shape.shadow.offset_y = offset
    shape.shadow.blur = blur
    shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

## الخلاصة

أنت الآن تعرف **كيفية إنشاء مستند** يحتوي على شكل مستطيل بظل مخصص باستخدام Aspose.Words for Python. غطى الدليل إدراج المستطيل، جعل الشكل متداخلًا، تفعيل الظل، ضبط لونه، إزاحته، تلطيخه، ونمطه، وأخيرًا حفظ الملف.

من هنا يمكنك استكشاف مواضيع ذات صلة مثل **إضافة ظل إلى الشكل** لأشكال أخرى، **تعيين لون الظل** ديناميكيًا بناءً على البيانات، أو **كيفية إضافة ظل** إلى الصور ومربعات النص. جرّب أبعادًا، ألوانًا، وأنماط ظل مختلفة لتتناسب مع إرشادات علامتك التجارية أو نظام التصميم الخاص بك.

هل أنت مستعد لأتمتة المزيد من مستندات Word؟ جرّب إضافة جداول، رؤوس، أو محتوى ديناميكي في الخطوة التالية—كل خطوة تبني على نفس المبادئ التي تم توضيحها هنا. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [How to Manage Document Variables with Aspose.Words in Python&#58; A Complete Guide](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}