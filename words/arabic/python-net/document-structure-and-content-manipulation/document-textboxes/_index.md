---
"description": "حسّن مظهر المستندات باستخدام Aspose.Words Python! تعلّم خطوة بخطوة كيفية إنشاء وتخصيص مربعات النص في مستندات Word. حسّن تصميم وتنسيق وتنسيق المحتوى لمستندات جذابة."
"linktitle": "تحسين المحتوى المرئي باستخدام مربعات النص في مستندات Word"
"second_title": "Aspose.Words Python Document Management API"
"title": "تحسين المحتوى المرئي باستخدام مربعات النص في مستندات Word"
"url": "/ar/python-net/document-structure-and-content-manipulation/document-textboxes/"
"weight": 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تحسين المحتوى المرئي باستخدام مربعات النص في مستندات Word


مربعات النص ميزة فعّالة في مستندات Word، تُمكّنك من إنشاء تخطيطات محتوى جذابة بصريًا ومنظّمة. مع Aspose.Words لـ Python، يمكنك الارتقاء بإنشاء مستنداتك إلى مستوى أعلى من خلال دمج مربعات النص بسلاسة. في هذا الدليل المُفصّل، سنستكشف كيفية تحسين المحتوى المرئي باستخدام مربعات النص باستخدام واجهة برمجة تطبيقات Aspose.Words لـ Python.

## مقدمة

تُوفر مربعات النص طريقةً متعددة الاستخدامات لعرض المحتوى داخل مستند Word. فهي تتيح لك عزل النصوص والصور، والتحكم في موضعها، وتطبيق تنسيق مُحدد على محتوى مربع النص. سيُرشدك هذا الدليل خلال عملية استخدام Aspose.Words لـ Python لإنشاء مربعات نص وتخصيصها داخل مستنداتك.

## المتطلبات الأساسية

قبل أن تبدأ، تأكد من أن لديك ما يلي:

- تم تثبيت Python على نظامك.
- فهم أساسي لبرمجة بايثون.
- Aspose.Words لمراجع API الخاصة بـ Python.

## تثبيت Aspose.Words لـ Python

للبدء، عليك تثبيت حزمة Aspose.Words لبايثون. يمكنك القيام بذلك باستخدام pip، مُثبّت حزمة بايثون، باستخدام الأمر التالي:

```python
pip install aspose-words
```

## إضافة مربعات نصية إلى مستند Word

لنبدأ بإنشاء مستند وورد جديد وإضافة مربع نص إليه. إليك مثال على مقتطف برمجي لتحقيق ذلك:

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

في هذا الكود نقوم بإنشاء كود جديد `Document` و أ `DocumentBuilder`. ال `insert_text_box` تُستخدم هذه الطريقة لإضافة مربع نص إلى المستند. يمكنك تخصيص محتوى وموضع وحجم مربع النص حسب احتياجاتك.

## تنسيق مربعات النص

يمكنك تطبيق التنسيق على النص داخل مربع النص، تمامًا كما تفعل مع النص العادي. إليك مثال لتغيير حجم ولون خط محتوى مربع النص:

```python
textbox.paragraphs[0].runs[0].font.size = 14
textbox.paragraphs[0].runs[0].font.color.rgb = aw.Color.blue
```

## وضع مربعات النص

يُعد التحكم في موضع مربعات النص أمرًا بالغ الأهمية لتحقيق التصميم المطلوب. يمكنك ضبط الموضع باستخدام `left` و `top` الخصائص. على سبيل المثال:

```python
textbox.left = aw.ConvertUtil.inch_to_points(1.5)
textbox.top = aw.ConvertUtil.inch_to_points(2)
```

## إضافة الصور إلى مربعات النص

يمكن أن تحتوي مربعات النص أيضًا على صور. لإضافة صورة إلى مربع النص، يمكنك استخدام الكود التالي:

```python
shape = textbox.append_child(aw.drawing.Shape(doc, aw.drawing.ShapeType.IMAGE))
shape.image_data.set_image("path/to/your/image.png")
```

## تنسيق النص داخل مربعات النص

يمكنك تطبيق أنماط مختلفة على النص داخل مربع النص، مثل الغامق والمائل والمسطر. إليك مثال:

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

في هذا الدليل، استكشفنا عملية تحسين المحتوى المرئي باستخدام مربعات النص في مستندات Word باستخدام واجهة برمجة تطبيقات Aspose.Words Python. تُتيح مربعات النص طريقة مرنة لتنظيم وتنسيق وتنسيق المحتوى داخل مستنداتك، مما يجعلها أكثر جاذبية وجاذبية بصريًا.

## الأسئلة الشائعة

### كيف أقوم بتغيير حجم مربع النص؟

لتغيير حجم مربع النص، يمكنك ضبط خصائص العرض والارتفاع باستخدام `width` و `height` صفات.

### هل يمكنني تدوير مربع النص؟

نعم، يمكنك تدوير مربع النص عن طريق ضبط `rotation` الملكية إلى الزاوية المطلوبة.

### كيف أضيف حدودًا إلى مربع النص؟

يمكنك إضافة حدود إلى مربع النص باستخدام `textbox.border` الممتلكات وتخصيص مظهرها.

### هل يمكنني تضمين الروابط التشعبية داخل مربع النص؟

بالتأكيد! يمكنك إدراج روابط تشعبية في محتوى مربع النص لتوفير موارد أو مراجع إضافية.

### هل من الممكن نسخ ولصق مربعات النص بين المستندات؟

نعم، يمكنك نسخ مربع نص من مستند واحد ولصقه في مستند آخر باستخدام `builder.insert_node` طريقة.

مع Aspose.Words لبايثون، لديك الأدوات اللازمة لإنشاء مستندات جذابة بصريًا ومنظمة جيدًا، تتضمن مربعات النص بسلاسة. جرّب أنماطًا وتخطيطات ومحتوى مختلفًا لتعزيز تأثير مستندات وورد. تصميم مستندات ممتع!

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}