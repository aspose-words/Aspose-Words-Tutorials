---
category: general
date: 2026-08-11
description: إضافة ظل إلى الشكل باستخدام Aspose.Words للغة Python. تعلم كيفية إضافة
  ظل إلى الشكل، وتطبيق الضبابية على الشكل، وتخصيص الإزاحة واللون.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- add shape shadow
- apply blur to shape
- Aspose.Words shadow effect
- Python Word shape styling
language: ar
lastmod: 2026-08-11
og_description: أضف ظلًا إلى الشكل باستخدام Aspose.Words للبايثون. يوضح لك هذا الدليل
  كيفية تطبيق التمويه على الشكل، وضبط الإزاحات، واختيار ألوان الظل في بضع أسطر من
  الشيفرة فقط.
og_image_alt: Word document screenshot showing a shape with a black shadow applied
og_title: إضافة ظل إلى الشكل في بايثون – دليل Aspose.Words خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-08-11'
  description: Add shadow to shape using Aspose.Words for Python. Learn how to add
    shape shadow, apply blur to shape, and customize offset and color.
  headline: Add shadow to shape in Python – complete Aspose.Words guide
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python. Learn how to add
    shape shadow, apply blur to shape, and customize offset and color.
  name: Add shadow to shape in Python – complete Aspose.Words guide
  steps:
  - name: Adding shadow to a specific shape by name
    text: 'If your document contains several shapes, you may want to target one by
      its `name` property:'
  - name: Skipping non‑visual nodes
    text: Sometimes a shape node can be a placeholder (e.g., a drawing canvas without
      visual content). Guard against this by checking `shape.is_image` or `shape.is_picture_frame`
      before applying the shadow.
  - name: Working with grouped shapes
    text: When shapes are grouped, the group itself is a `Shape` node. To apply a
      shadow to each member, iterate through `shape.get_child_nodes(aw.NodeType.SHAPE,
      True)`.
  - name: What’s next?
    text: '- Explore **apply blur to shape** for other effects like glow or soft edges.
      - Combine shadows with **shape borders** or **reflection** to create richer
      graphics. - Convert the edited document to PDF (`doc.save("output.pdf", aw.SaveFormat.PDF)`)
      for distribution.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: إضافة ظل إلى الشكل في بايثون – الدليل الكامل لـ Aspose.Words
url: /ar/python/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إضافة ظل إلى الشكل في Python – دليل Aspose.Words الكامل

إذا كنت بحاجة إلى **إضافة ظل إلى الشكل** في مستند Word، يوضح لك هذا الدرس بالضبط كيفية القيام بذلك باستخدام Aspose.Words for Python. سواء كنت تبني مولد تقارير أو خدمة قوالب مستندات، ستتعلم كيفية إضافة ظل للشكل، تطبيق تمويه (blur) على الشكل، وضبط مظهر الظل بدقة في بضع أسطر من الشيفرة فقط.

يغطي الدليل كل ما تحتاجه: الاستيرادات المطلوبة، تحديد الشكل المستهدف (بما في ذلك العقد المتداخلة)، تكوين خصائص الظل، معالجة الحالات الشائعة، وحفظ المستند المعدل. في النهاية ستحصل على مقطع شيفرة قابل لإعادة الاستخدام يمكنك إدراجه في أي مشروع Python يعمل مع ملفات .docx.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من أن لديك:

- **Python 3.8+** مثبت.
- **Aspose.Words for Python عبر .NET** (تثبيت باستخدام `pip install aspose-words`).
- مستند Word (`input.docx`) يحتوي على شكل واحد على الأقل (مثل مستطيل أو صورة أو SmartArt).
- إلمام أساسي بـ Python ونموذج كائن Aspose.Words.

## الخطوة 1: استيراد Aspose.Words وفتح المستند

الخطوة الأولى هي استيراد حزمة `aspose.words` (المعروفة عادةً بالاسم المختصر `aw`) وتحميل المستند المصدر.

```python
import aspose.words as aw

# Load the Word document from the file system
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)
```

*لماذا هذا مهم*: فتح المستند يمنحك الوصول إلى شجرة العقد حيث توجد الأشكال. فئة `aw.Document` هي نقطة الدخول لجميع التعديلات اللاحقة.

## الخطوة 2: تحديد أول شكل (بما في ذلك العقد المتداخلة)

يمكن أن تكون الأشكال أبناء مباشرة لـ `Paragraph` أو متداخلة داخل حاويات أخرى (مثل الجداول). استخدام `get_child` مع تعيين علم `is_deep` إلى `True` يضمن لك استرجاع أول شكل بغض النظر عن العمق.

```python
# Retrieve the first shape in the document, searching recursively
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

if shape is None:
    raise ValueError("No shape found in the document. Add a shape before applying a shadow.")
```

*لماذا هذا مهم*: عملية **add shape shadow** تتطلب كائن `Shape`. البحث العميق يمنعك من فقدان الأشكال المخفية داخل الجداول أو حاويات المجموعات.

## الخطوة 3: تمكين الظل وتعيين الخصائص الأساسية

يمثل Aspose.Words الظل بعدة خصائص. أولاً، شغّل الظل بتعيين `shadow_visible` إلى `True`.

```python
# Enable the shadow effect
shape.shadow_visible = True
```

الآن يمكنك تكوين نصف قطر التمويه (blur radius)، الإزاحات (offsets)، واللون.

## الخطوة 4: تطبيق تمويه على الشكل وتعريف قيم الإزاحة

نصف قطر التمويه يتحكم في مدى نعومة الظل. القيمة `5.0` تعطي تمويهًا ملحوظًا لكن غير مفرط. الإزاحات تحرك الظل أفقيًا وعموديًا.

```python
# Apply blur to shape – this is the "apply blur to shape" part
shape.shadow_blur = 5.0          # Blur radius in points

# Define horizontal (X) and vertical (Y) offsets
shape.shadow_offset_x = 2.0     # Move shadow 2 points to the right
shape.shadow_offset_y = 2.0     # Move shadow 2 points down
```

*لماذا هذا مهم*: تعديل `shadow_blur` وقيم الإزاحة يتيح لك إنشاء تأثيرات عمق واقعية تتماشى مع النمط البصري لمستندك.

## الخطوة 5: اختيار لون الظل (add shape shadow مع لون مخصص)

يمكنك استخدام أي `aw.Color`. هنا نختار اللون الأسود، لكن يمكنك استبداله بـ `aw.Color.red` أو `aw.Color.from_argb(255, 0, 120, 215)`، إلخ.

```python
# Set the shadow color – black in this example
shape.shadow_color = aw.Color.black
```

*لماذا هذا مهم*: اللون يحدد كيفية تفاعل الظل مع المحتوى المحيط. الظلال الداكنة تكون أكثر وضوحًا على الخلفيات الفاتحة، بينما الظلال الفاتحة تعمل بشكل أفضل على الصفحات الداكنة.

## الخطوة 6: حفظ المستند المحدث

أخيرًا، اكتب التغييرات إلى القرص. يمكنك استبدال الملف الأصلي أو إنشاء ملف جديد.

```python
output_path = "YOUR_DIRECTORY/output_with_shadow.docx"
doc.save(output_path)

print(f"Shadow applied successfully. Saved to {output_path}")
```

عند فتح `output_with_shadow.docx` في Microsoft Word، سيظهر أول شكل بظل أسود ناعم مع التمويه والإزاحة المحددين.

## مثال كامل قابل للتنفيذ

بجمع كل ما سبق، إليك سكربت مستقل يمكنك تشغيله فورًا:

```python
import aspose.words as aw

def add_shadow_to_first_shape(input_path: str, output_path: str,
                              blur: float = 5.0,
                              offset_x: float = 2.0,
                              offset_y: float = 2.0,
                              color: aw.Color = aw.Color.black) -> None:
    """
    Loads a Word document, finds the first shape (deep search),
    and applies a shadow effect.

    Parameters
    ----------
    input_path : str
        Path to the source .docx file.
    output_path : str
        Path where the modified document will be saved.
    blur : float, optional
        Blur radius for the shadow. Default is 5.0 points.
    offset_x : float, optional
        Horizontal offset of the shadow. Default is 2.0 points.
    offset_y : float, optional
        Vertical offset of the shadow. Default is 2.0 points.
    color : aw.Color, optional
        Shadow color. Default is black.
    """
    # Load the document
    doc = aw.Document(input_path)

    # Retrieve the first shape, searching recursively
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

    if shape is None:
        raise ValueError("No shape found in the document. Insert a shape before calling this function.")

    # Enable shadow and configure its appearance
    shape.shadow_visible = True
    shape.shadow_blur = blur
    shape.shadow_offset_x = offset_x
    shape.shadow_offset_y = offset_y
    shape.shadow_color = color

    # Save the result
    doc.save(output_path)

if __name__ == "__main__":
    INPUT_DOC = "YOUR_DIRECTORY/input.docx"
    OUTPUT_DOC = "YOUR_DIRECTORY/output_with_shadow.docx"
    add_shadow_to_first_shape(INPUT_DOC, OUTPUT_DOC)
```

**الناتج المتوقع**: فتح `output_with_shadow.docx` يظهر أول شكل بظل أسود خفيف تم تمويهه وإزاحته بمقدار 2 pt أفقيًا وعموديًا، مطابقًا للمعلمات التي قمت بتمريرها.

## معالجة أشكال متعددة وحالات الحافة

### إضافة ظل إلى شكل محدد بالاسم

إذا كان مستندك يحتوي على عدة أشكال، قد ترغب في استهداف أحدها باستخدام خاصية `name` الخاصة به:

```python
target_name = "MyRectangle"
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)  # start with first shape
while shape is not None and shape.name != target_name:
    shape = shape.next_sibling(aw.NodeType.SHAPE)

if shape is None:
    raise ValueError(f"Shape named '{target_name}' not found.")
```

### تخطي العقد غير المرئية

أحيانًا قد يكون عقد الشكل عنصرًا نائبًا (مثل لوحة رسم بدون محتوى مرئي). احمِ نفسك من ذلك بفحص `shape.is_image` أو `shape.is_picture_frame` قبل تطبيق الظل.

```python
if not shape.is_image and not shape.is_picture_frame:
    # Proceed only if the shape can display a shadow
    shape.shadow_visible = True
```

### العمل مع الأشكال المجمعة

عند تجميع الأشكال، تكون المجموعة نفسها عقدة `Shape`. لتطبيق ظل على كل عضو، قم بالتكرار عبر `shape.get_child_nodes(aw.NodeType.SHAPE, True)`.

```python
if shape.is_group:
    for child in shape.get_child_nodes(aw.NodeType.SHAPE, True):
        child.shadow_visible = True
        child.shadow_blur = blur
        child.shadow_offset_x = offset_x
        child.shadow_offset_y = offset_y
        child.shadow_color = color
```

هذه المتغيرات تضمن أن يعمل الكود الخاص بك بثبات عبر تخطيطات المستند المختلفة.

## نصائح احترافية للحصول على ظلال مثالية

- **الاتساق**: استخدم نفس نصف قطر التمويه والإزاحة لجميع الأشكال في التقرير للحفاظ على لغة بصرية متسقة.
- **الأداء**: تطبيق الظلال على عشرات الصور عالية الدقة قد يزيد من حجم الملف. اختبر حجم الناتج إذا كنت تخطط لتوليد ملفات PDF لاحقًا.
- **تباين اللون**: على خلفيات الصفحات الداكنة، فكر في ظل أفتح (`aw.Color.gray`) للحفاظ على الوضوح.
- **المعاينة**: واجهة Word الخاصة بـ “Shadow” تعكس خصائص Aspose.Words، لذا يمكنك التجربة يدويًا ثم نسخ القيم الناتجة إلى السكربت الخاص بك.

## الخلاصة

أنت الآن تعرف كيف **تضيف ظلًا إلى الشكل** في مستند Word باستخدام Aspose.Words for Python. غطى الدليل كيفية تحديد الشكل، تمكين الظل، **add shape shadow** مع تمويه مخصص، إزاحات، ولون، ثم حفظ النتيجة. باستخدام الدالة القابلة لإعادة الاستخدام أعلاه، يمكنك دمج هذا التأثير في أي خط أنابيب لتوليد المستندات.

### ما التالي؟

- استكشف **apply blur to shape** لتأثيرات أخرى مثل التوهج أو الحواف الناعمة.
- اجمع الظلال مع **shape borders** أو **reflection** لإنشاء رسومات أغنى.
- حوّل المستند المعدل إلى PDF (`doc.save("output.pdf", aw.SaveFormat.PDF)`) للتوزيع.

- [دروس ظل الشكل في Aspose.Words – إضافة ظل إلى شكل Word في C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [إنشاء شكل مستطيل في Word باستخدام Aspose.Words – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [إنشاء شكل مجموعة في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}