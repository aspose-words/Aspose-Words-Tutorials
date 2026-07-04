---
category: general
date: 2026-06-05
description: مثال Python لإنشاء مستند Word يوضح كيفية إضافة ظل إلى شكل وتطبيق تأثير
  الظل في Word باستخدام Aspose.Words.
draft: false
keywords:
- create word document python
- how to add shadow
- add shadow to shape
- apply shadow effect word
- insert shape with shadow
language: ar
og_description: دليل إنشاء مستند Word باستخدام بايثون يشرح لك كيفية إضافة ظل إلى شكل
  وتطبيق تأثير الظل في Word باستخدام Aspose.Words.
og_title: إنشاء مستند Word باستخدام Python – إضافة ظل إلى الشكل
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: Create Word document Python example shows how to add shadow to a shape,
    applying shadow effect in Word with Aspose.Words.
  headline: Create Word Document Python – Add Shadow to Shape Guide
  type: TechArticle
- questions:
  - answer: Absolutely. Use `builder.insert_image(...)` to place an image, then access
      `image_shape.shadow_format` just like we did with the rectangle.
    question: Can I add a shadow to a picture instead of a shape?
  - answer: Yes. Aspose.Words preserves shape effects during conversion, so the PDF
      will retain the shadow.
    question: Does the shadow survive when I convert the document to PDF?
  - answer: Call `builder.insert_shape` for each shape, then configure each shape’s
      `shadow_format` independently. No shared state.
    question: What if I need multiple shapes with different shadows?
  - answer: 'Minimal for typical documents. If you’re generating thousands of shapes,
      consider batch processing or limiting blur radius to keep rendering fast. ##
      Conclusion We’ve just demonstrated how to **create Word document python** code
      that inserts a rectangle and **adds shadow to shape** using Aspose.Word'
    question: Is there a performance impact when adding many shadows?
  type: FAQPage
tags:
- python
- aspose-words
- document automation
title: إنشاء مستند Word باستخدام Python – دليل إضافة الظل إلى الشكل
url: /ar/python/images-shapes/create-word-document-python-add-shadow-to-shape-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word باستخدام Python – دليل إضافة ظل إلى الشكل

هل تساءلت يومًا كيف يمكنك **create Word document python** كتابة كود لا يضيف شكلًا فحسب، بل يمنحه ظلًا أنيقًا أيضًا؟ لست وحدك. في العديد من التقارير والفواتير والنشرات التسويقية، يمكن للظل الخفيف أن يجعل المستطيل يبدو وكأنه يخرج من الصفحة، مضيفًا عمقًا دون الحاجة إلى رسومات إضافية.

في هذا البرنامج التعليمي سنستعرض مثالًا كاملاً وقابلًا للتنفيذ يوضح بالضبط **how to add shadow** إلى شكل باستخدام Aspose.Words for Python. في النهاية ستحصل على ملف `.docx` يحتوي على مستطيل يلقي ظلًا ناعمًا بزاوية 45 درجة — مثالي لجعل مستنداتك تبدو مصقولة ومهنية.

## ما يغطيه هذا الدليل

سنبدأ بإعداد البيئة، ثم إنشاء مستند Word جديد، وإدراج مستطيل، وتكوين خصائص الظل، وأخيرًا حفظ الملف. خلال العملية سنناقش لماذا كل إعداد مهم، والأخطاء الشائعة، وبعض الحيل الإضافية التي يمكنك تجربتها. لا حاجة لمراجع خارجية؛ كل ما تحتاجه موجود هنا.

**المتطلبات المسبقة**

- Python 3.8+ مثبت  
- حزمة `aspose-words` (`pip install aspose-words`)  
- إلمام أساسي بصياغة Python (إذا كنت قد كتبت “Hello, World!” من قبل، فأنت جاهز)

هل أنت جاهز؟ لنبدأ.

## الخطوة 1: تهيئة المستند – أساسيات **Create Word Document Python**

أول شيء تحتاجه هو كائن مستند فارغ و`DocumentBuilder` يتيح لك إضافة المحتوى. فكر في الـ builder كقلم يكتب داخل ملف Word.

```python
import aspose.words as aw

# Create a new, empty Word document
doc = aw.Document()

# DocumentBuilder gives us a convenient way to add elements
builder = aw.DocumentBuilder(doc)
```

*لماذا هذا مهم:* `aw.Document()` هو نقطة الدخول لأي عملية Aspose.Words. بدونها لا يمكنك إضافة أشكال أو نص أو أي عنصر آخر. الـ builder يحتفظ بإشارة إلى المستند، لذا لا تحتاج إلى تمرير المستند يدويًا.

## الخطوة 2: إدراج مستطيل – باستخدام منطق **Insert Shape With Shadow**

الآن سنضع مستطيلًا على الصفحة. الأبعاد بوحدات النقاط (1 pt ≈ 1/72 inch)، لذا 150 × 100 pts يعطي صندوقًا متناسقًا بشكل جيد.

```python
# Insert a rectangle shape of 150x100 points
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
```

*نصيحة احترافية:* إذا كنت بحاجة إلى شكل مختلف، فقط استبدل `ShapeType.RECTANGLE` بـ `ShapeType.ELLIPSE` أو `ShapeType.CLOUD`، إلخ. نفس كود إعداد الظل يعمل مع أي شكل تختاره.

## الخطوة 3: تطبيق تأثير الظل – **How To Add Shadow** بدقة

هنا يحدث السحر. كائن `shadow_format` يتحكم في الرؤية، والمسافة، والطمس، والزاوية، واللون، والشفافية. اضبط كل خاصية للحصول على المظهر الذي ترغب به.

```python
# Grab the shadow formatting object
shadow = rectangle_shape.shadow_format

# Make the shadow visible
shadow.visible = True

# Set how far the shadow sits from the shape (in points)
shadow.distance = 5.0

# Blur radius controls softness; higher = fuzzier edges
shadow.blur = 3.0

# Angle determines the light source direction (degrees clockwise from the x‑axis)
shadow.angle = 45

# Choose a color – black works for most professional documents
shadow.color = aw.drawing.Color.black

# Transparency is a float from 0 (opaque) to 1 (fully transparent)
shadow.transparency = 0.4   # 40 % transparent gives a subtle effect
```

**لماذا كل إعداد مهم**

| الخاصية | الاستخدام الشائع | التأثير البصري |
|----------|-------------|---------------|
| `visible` | تشغيل أو إيقاف التأثير | لا ظل إذا كان `False` |
| `distance` | يتحكم في الإزاحة عن الشكل | القيم الأكبر تدفع الظل بعيدًا أكثر |
| `blur` | ينعم الحواف | الطمس الأعلى = ظل أكثر انتشارًا |
| `angle` | يحاكي اتجاه الضوء | 0° = الظل إلى اليمين، 90° = أسفل |
| `color` | يتطابق مع العلامة التجارية أو السمة | الظلال البيضاء نادراً ما تكون منطقية |
| `transparency` | يضبط الشفافية | 0.0 = صلب، 0.8 = بالكاد يُلاحظ |

*خطأ شائع:* نسيان ضبط `shadow.visible = True` ينتج عنه شكل سليم لكن بدون ظل — من السهل تجاهله عندما تكون مركّزًا على اللون أو الحجم.

## الخطوة 4: حفظ المستند – الخطوة النهائية **Create Word Document Python**

بعد تكوين الشكل، ببساطة اكتب المستند إلى القرص. يمكنك اختيار أي تنسيق مدعوم (`.docx`, `.pdf`, `.html`, إلخ). في هذا الدليل سنستخدم الصيغة الكلاسيكية `.docx`.

```python
# Save the document to the desired location
output_path = "shadowed_shape.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

عند فتح `shadowed_shape.docx` في Microsoft Word (أو أي عارض متوافق)، سترى مستطيلًا بظل واضح بزاوية 45 درجة — تمامًا ما يصفه الكود أعلاه.

### النتيجة المتوقعة

- ملف Word صفحة واحدة.  
- مستطيل واحد مركّز في المكان الذي كان الـ builder فيه.  
- ظل أسود شبه شفاف إزاحته 5 pts، مطمّس بـ 3 pts، ومُسقَط بزاوية 45°.

إذا لم ترى الظل، تحقق مرة أخرى من أن `shadow.visible` هو `True` وأنك تستخدم عارضًا يحترم تأثيرات الأشكال (معظم إصدارات Word الحديثة تفعل ذلك).

## إضافي: تعديل الظل لأنماط مختلفة

قد ترغب في مظهر أكثر نعومة لتقرير شركة، أو ظل جريء ملون لنشرة تسويقية. إليك بعض الاختلافات السريعة:

```python
# Soft gray shadow for subtle emphasis
shadow.color = aw.drawing.Color.gray
shadow.transparency = 0.6
shadow.blur = 5.0
shadow.distance = 3.0

# Red, dramatic shadow for a creative brochure
shadow.color = aw.drawing.Color.red
shadow.transparency = 0.2
shadow.blur = 2.0
shadow.angle = 120
```

التجربة بهذه القيم هي أفضل طريقة لفهم كيفية عمل **add shadow to shape** عمليًا.

## معاينة بصرية (مع نص بديل مضمّن)

![شكل مستطيل بظل في مستند Word – مثال create word document python](/images/shadowed_rectangle.png)

*نص بديل:* *شكل مستطيل بظل في مستند Word – مثال create word document python.*

## الأسئلة المتكررة

**س: هل يمكنني إضافة ظل إلى صورة بدلاً من شكل؟**  
ج: بالتأكيد. استخدم `builder.insert_image(...)` لوضع صورة، ثم الوصول إلى `image_shape.shadow_format` كما فعلنا مع المستطيل.

**س: هل يبقى الظل عند تحويل المستند إلى PDF؟**  
ج: نعم. Aspose.Words يحافظ على تأثيرات الأشكال أثناء التحويل، لذا سيحتفظ ملف PDF بالظل.

**س: ماذا لو احتجت إلى عدة أشكال بظلال مختلفة؟**  
ج: استدعِ `builder.insert_shape` لكل شكل، ثم قم بتكوين `shadow_format` لكل شكل على حدة. لا توجد حالة مشتركة.

**س: هل هناك تأثير على الأداء عند إضافة العديد من الظلال؟**  
ج: تأثير ضئيل للمستندات العادية. إذا كنت تُنشئ آلاف الأشكال، فكر في المعالجة الدفعية أو تقليل نصف قطر الطمس للحفاظ على سرعة العرض.

## الخلاصة

لقد عرضنا للتو كيفية كتابة كود **create Word document python** يدرج مستطيلًا و**adds shadow to shape** باستخدام Aspose.Words. من خلال تكوين `shadow_format`، يمكنك **apply shadow effect word** على المستندات مع تحكم دقيق في المسافة، والطمس، والزاوية، واللون، والشفافية. نفس النمط يعمل مع أي شكل أو صورة أو حتى مربع نص، مما يمنحك مجموعة أدوات متعددة الاستخدامات لإنشاء مستندات ذات مظهر احترافي.

ما التالي؟ جرّب دمج عدة أشكال، وضع نص فوقها، أو تصدير إلى PDF لترى الظل يبقى بعد التحويل. يمكنك أيضًا استكشاف تأثيرات بصرية أخرى مثل التوهج أو الانعكاس — فقط استبدل `shadow_format` بـ `glow_format` أو `reflection_format`.

برمجة سعيدة، ولتكن مستنداتك دائمًا ذات عمق إضافي!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء مستند Word فارغ مع شكل مستطيل بظل – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [إنشاء شكل مستطيل في Word باستخدام Aspose.Words – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [إنشاء شكل مجموعة في مستند Word باستخدام Aspose.Words لـ .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}