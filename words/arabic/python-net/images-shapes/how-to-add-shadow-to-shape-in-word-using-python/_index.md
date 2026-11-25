---
category: general
date: 2026-11-25
description: تعلم كيفية إضافة ظل إلى الشكل في Word باستخدام Aspose.Words للغة Python
  – كود خطوة بخطوة، شروحات، وأفضل الممارسات.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add shadow to shape in word
- Aspose.Words shadow formatting
- Python shape shadow
- Word document shape manipulation
- configure shadow offset
- set shape shadow color
language: ar
lastmod: 2026-11-25
og_description: كيفية إضافة ظل إلى الشكل في Word باستخدام Aspose.Words للبايثون. اتبع
  هذا البرنامج التعليمي لتمكين وتخصيص ظلال الأشكال في مستنداتك.
og_image_alt: Screenshot showing a Word shape with a black shadow applied using Python
og_title: كيفية إضافة ظل إلى الشكل في Word باستخدام Python – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to add shadow to shape in Word with Aspose.Words for Python
    – step‑by‑step code, explanations, and best practices.
  headline: How to add shadow to shape in Word using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- Shape formatting
title: كيفية إضافة ظل إلى الشكل في Word باستخدام Python
url: /ar/python/images-shapes/how-to-add-shadow-to-shape-in-word-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إضافة ظل إلى الشكل في Word باستخدام Python

إذا كنت بحاجة إلى **كيفية إضافة ظل إلى الشكل في Word**، فإن هذا الدليل يوضح لك الخطوات الدقيقة باستخدام Aspose.Words for Python. في نهاية البرنامج التعليمي ستحصل على مستند Word حيث يعرض الشكل الأول ظلًا أسود مع إزاحة وتعتيم مخصصين.

سترى أيضًا كيف تعمل نفس التقنية على أي شكل في المستند، مما يجعل من السهل تحسين التقارير، النشرات، أو المواد التسويقية. لا تحتاج إلى خبرة سابقة مع Aspose.Words—فقط معرفة أساسية بـ Python.

## ما ستحتاجه

- Python 3.8+ (الكود يعمل على Windows، macOS، وLinux)  
- حزمة `aspose-words` (`pip install aspose-words`)  
- ملف `.docx` يحتوي على شكل واحد على الأقل (مثلاً، مستطيل أو صورة تم إدراجها)  

## الخطوة 1: إعداد Aspose.Words لـ Python

أولاً قم بتثبيت المكتبة واستيراد المساحات الاسمية المطلوبة. حزمة `aspose.words` تمنحك وصولًا كاملًا إلى نموذج كائنات Word، بما في ذلك خصائص ظل الشكل.

```python
# Install the package (run once in your terminal)
# pip install aspose-words

import aspose.words as aw
```

> **نصيحة احترافية:** استخدم بيئة افتراضية للحفاظ على عزل الاعتمادات عن المشاريع الأخرى.

## الخطوة 2: تحميل مستند Word

تحميل المستند سهل باستخدام `aw.Document`. استبدل `"YOUR_DIRECTORY/input.docx"` بالمسار إلى ملف المصدر الخاص بك.

```python
# Load the Word document
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

كائن `Document` يمثل ملف Word بالكامل ويوفر طرقًا للتنقل في شجرة العقد الخاصة به.

## الخطوة 3: استرجاع أول شكل في المستند

الشكل هو عقدة من النوع `NodeType.SHAPE`. طريقة `get_child` تبحث في شجرة المستند وتعيد أول عقدة مطابقة.

```python
# Retrieve the first shape (index 0) in the document
first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
```

إذا كان المستند يحتوي على أشكال متعددة، غيّر الفهرس لاستهداف شكل مختلف. العلم `True` يضمن أن البحث عميق (أي أنه يبحث داخل رؤوس وتذييلات الجداول).

## الخطوة 4: تطبيق تنسيق الظل على الشكل

كل شكل يمتلك خاصية `shadow_format` التي تتحكم في الرؤية، اللون، الإزاحات، التعتيم، وأكثر. أدناه نقوم بتمكين الظل، ضبط لونه إلى الأسود، وتكوين الإزاحات الأفقية/العمودية ونصف قطر التعتيم.

```python
# Access the shape's shadow formatting object
shadow_format = first_shape.shadow_format

# Enable the shadow and configure its appearance
shadow_format.visible = True                     # Make the shadow visible
shadow_format.color = aw.drawing.Color.black    # Set shadow color to black
shadow_format.offset_x = 4                      # Horizontal offset (points)
shadow_format.offset_y = 4                      # Vertical offset (points)
shadow_format.blur = 6                          # Blur radius (points)
```

### لماذا هذه الإعدادات مهمة

- `visible = True` يُفعِّل التأثير؛ بدون ذلك لا تؤثر الخصائص الأخرى.  
- `color` يحدد درجة لون الظل؛ الأسود يوفر أقوى تباين.  
- `offset_x` و `offset_y` يتحكمان في مدى إزاحة الظل عن الشكل؛ القيم المتطابقة تُنشئ ظلًا قطريًا.  
- `blur` ينعّم الحواف، مما يجعل الظل يبدو أكثر طبيعية.

يمكنك تجربة ألوان أخرى (`aw.drawing.Color.red`) أو إزاحات أكبر للحصول على تأثير درامي. هذه المرونة جزء من **تنسيق ظل Aspose.Words**.

## الخطوة 5: حفظ المستند المعدل (اختياري)

بعد تكوين الظل، اكتب التغييرات مرة أخرى إلى القرص. يمكنك استبدال الملف الأصلي أو إنشاء ملف جديد.

```python
# Save the updated document
doc.save("YOUR_DIRECTORY/output.docx")
```

فتح `output.docx` في Microsoft Word سيظهر الشكل الأول بظل أسود مرئي، مائلًا 4 نقطة أفقيًا وعموديًا، ومُعتَّمًا بـ 6 نقاط.

![how to add shadow to shape in Word screenshot](image.png){alt="كيفية إضافة ظل إلى الشكل في Word باستخدام Python"}

## الحالات الشائعة والسيناريوهات الخاصة

| الحالة | كيفية تعديل الكود |
|-----------|------------------------|
| **Multiple shapes** | Loop through `doc.get_child_nodes(aw.NodeType.SHAPE, True)` and apply the same `shadow_format` to each shape. |
| **Different shadow colors** | Set `shadow_format.color = aw.drawing.Color.from_argb(255, 255, 0, 0)` for a red shadow. |
| **No shadow needed on some shapes** | Add a conditional check: `if shape.name == "TitleShape": continue`. |
| **Saving as PDF** | Use `doc.save("output.pdf")`; the shadow is preserved in the PDF rendering. |
| **Older Word versions** | Aspose.Words works with .doc and .docx alike; the same API applies. |

تُظهر هذه الاختلافات مدى **تلاعب أشكال مستند Word** الذي يمكنك تحقيقه ببضع أسطر من Python.

## الخلاصة

أنت الآن تعرف **كيفية إضافة ظل إلى الشكل في Word** برمجيًا باستخدام Aspose.Words for Python. سير العمل الكامل—إعداد المكتبة، تحميل المستند، استرجاع الشكل، تكوين ظله، وحفظ النتيجة—يغطي أكثر الحالات شيوعًا ويمنحك أساسًا قويًا لتنسيق الأشكال المتقدم.

بعد ذلك، جرّب دمج هذه التقنية مع خيارات تنسيق أخرى مثل **set shape shadow color**، **configure shadow offset**، أو حتى تطبيق التدرجات والانعكاسات. استكشاف هذه الميزات سيمكنك من إنشاء مستندات مصقولة وجاهزة للطباعة بالكامل من خلال الكود.

--- 

*هل أنت مستعد لأتمتة مزيد من ميزات Word؟ اطلع على دروسنا حول “how to change shape fill color in Word” و “how to insert watermarks with Aspose.Words”.*

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك الخاصة.

- [Add Shadow to Shape in Python with Aspose.Words – Full Guide](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-with-aspose-words-full-guide/)
- [How to apply shadow effect to a Word shape with Aspose.Words](/words/english/python-net/images-shapes/how-to-apply-shadow-effect-to-a-word-shape-with-aspose-words/)
- [Create Word Document Python – Add Shadow to Shape Guide](/words/english/python-net/images-shapes/create-word-document-python-add-shadow-to-shape-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}