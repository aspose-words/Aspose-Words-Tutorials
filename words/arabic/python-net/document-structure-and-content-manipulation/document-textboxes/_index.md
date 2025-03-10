---
title: تحسين المحتوى المرئي باستخدام مربعات النص في مستندات Word
linktitle: تحسين المحتوى المرئي باستخدام مربعات النص في مستندات Word
second_title: Aspose.Words - واجهة برمجة تطبيقات إدارة المستندات باستخدام Python
description: قم بتعزيز الصور المرئية للمستندات باستخدام Aspose.Words Python! تعرّف خطوة بخطوة على كيفية إنشاء وتخصيص مربعات النص في مستندات Word. ارتقِ بتخطيط المحتوى وتنسيقه وتصميمه للحصول على مستندات جذابة.
weight: 25
url: /ar/python-net/document-structure-and-content-manipulation/document-textboxes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تحسين المحتوى المرئي باستخدام مربعات النص في مستندات Word


تُعد مربعات النص ميزة قوية في مستندات Word تتيح لك إنشاء تخطيطات محتوى منظمة وجذابة بصريًا. باستخدام Aspose.Words for Python، يمكنك رفع مستوى إنشاء المستندات إلى المستوى التالي من خلال دمج مربعات النص في مستنداتك بسلاسة. في هذا الدليل التفصيلي، سنستكشف كيفية تحسين المحتوى المرئي باستخدام مربعات النص باستخدام واجهة برمجة تطبيقات Aspose.Words Python.

## مقدمة

توفر مربعات النص طريقة متعددة الاستخدامات لعرض المحتوى داخل مستند Word. فهي تسمح لك بعزل النص والصور والتحكم في موضعها وتطبيق التنسيق بشكل خاص على المحتوى داخل مربع النص. سيرشدك هذا الدليل خلال عملية استخدام Aspose.Words for Python لإنشاء مربعات نص وتخصيصها داخل مستنداتك.

## المتطلبات الأساسية

قبل أن تبدأ، تأكد من أن لديك ما يلي:

- تم تثبيت Python على نظامك.
- فهم أساسي لبرمجة بايثون.
- Aspose.Words لمراجع API الخاصة بـ Python.

## تثبيت Aspose.Words لـ Python

للبدء، تحتاج إلى تثبيت حزمة Aspose.Words لـ Python. يمكنك القيام بذلك باستخدام pip، مثبت حزمة Python، باستخدام الأمر التالي:

```python
pip install aspose-words
```

## إضافة مربعات نصية إلى مستند Word

لنبدأ بإنشاء مستند Word جديد وإضافة مربع نص إليه. فيما يلي مقتطف من التعليمات البرمجية لتحقيق ذلك:

```python
import aspose.words as aw

doc = aw.Document()
builder = aw.DocumentBuilder(doc=doc)
textbox = aw.drawing.Shape(doc, aw.drawing.ShapeType.TEXT_BOX)
textbox.width = 100
textbox.height = 100
textbox.text_box.layout_flow = aw.drawing.LayoutFlow.BOTTOM_TO_TOP
textbox.append_child(aw.Paragraph(doc))
builder.insert_node(textbox)
builder.move_to(textbox.first_paragraph)
builder.write('This text is flipped 90 degrees to the left.')
```

 في هذا الكود نقوم بإنشاء كود جديد`Document` و أ`DocumentBuilder` . ال`insert_text_box` تُستخدم هذه الطريقة لإضافة مربع نص إلى المستند. يمكنك تخصيص محتوى وموضع وحجم مربع النص وفقًا لمتطلباتك.

## تنسيق مربعات النص

يمكنك تطبيق التنسيق على النص داخل مربع النص، تمامًا كما تفعل مع النص العادي. فيما يلي مثال لتغيير حجم الخط ولون محتوى مربع النص:

```python
textbox.paragraphs[0].runs[0].font.size = 14
textbox.paragraphs[0].runs[0].font.color.rgb = aw.Color.blue
```

## وضع مربعات النص

 يعد التحكم في موضع مربعات النص أمرًا بالغ الأهمية لتحقيق التخطيط المطلوب. يمكنك ضبط الموضع باستخدام`left` و`top` الخصائص. على سبيل المثال:

```python
textbox.left = aw.ConvertUtil.inch_to_points(1.5)
textbox.top = aw.ConvertUtil.inch_to_points(2)
```

## إضافة الصور إلى مربعات النص

يمكن أن تحتوي مربعات النص أيضًا على صور. لإضافة صورة إلى مربع نص، يمكنك استخدام مقتطف التعليمات البرمجية التالي:

```python
shape = textbox.append_child(aw.drawing.Shape(doc, aw.drawing.ShapeType.IMAGE))
shape.image_data.set_image("path/to/your/image.png")
```

## تنسيق النص داخل مربعات النص

يمكنك تطبيق أنماط مختلفة على النص داخل مربع النص، مثل الخط الغامق والمائل والمسطر. فيما يلي مثال:

```python
textbox.paragraphs[0].runs[0].font.bold = True
textbox.paragraphs[0].runs[0].font.italic = True
textbox.paragraphs[0].runs[0].font.underline = aw.words.Underline.SINGLE
```

## حفظ المستند

بمجرد إضافة مربعات النص وتخصيصها، يمكنك حفظ المستند باستخدام الكود التالي:

```python
doc.save("output.docx")
```

## خاتمة

في هذا الدليل، استكشفنا عملية تحسين المحتوى المرئي باستخدام مربعات النص في مستندات Word باستخدام واجهة برمجة تطبيقات Aspose.Words Python. توفر مربعات النص طريقة مرنة لتنظيم المحتوى وتنسيقه وتنسيقه داخل مستنداتك، مما يجعلها أكثر جاذبية وجاذبية بصريًا.

## الأسئلة الشائعة

### كيف أقوم بتغيير حجم مربع النص؟

 لتغيير حجم مربع النص، يمكنك ضبط خصائص العرض والارتفاع باستخدام`width` و`height` صفات.

### هل يمكنني تدوير مربع النص؟

 نعم، يمكنك تدوير مربع النص عن طريق ضبط`rotation` الملكية إلى الزاوية المطلوبة.

### كيف أضيف حدودًا إلى مربع النص؟

 يمكنك إضافة حدود إلى مربع النص باستخدام`textbox.border`الممتلكات وتخصيص مظهرها.

### هل يمكنني تضمين ارتباطات تشعبية داخل مربع النص؟

بالتأكيد! يمكنك إدراج ارتباطات تشعبية في محتوى مربع النص لتوفير مصادر أو مراجع إضافية.

### هل من الممكن نسخ ولصق مربعات النص بين المستندات؟

 نعم، يمكنك نسخ مربع نص من مستند واحد ولصقه في مستند آخر باستخدام`builder.insert_node` طريقة.

مع Aspose.Words for Python، لديك الأدوات اللازمة لإنشاء مستندات جذابة بصريًا ومنظمة جيدًا تتضمن مربعات نصية بسلاسة. جرّب أنماطًا وتخطيطات ومحتوى مختلفين لتعزيز تأثير مستندات Word الخاصة بك. تصميم مستندات سعيد!
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
