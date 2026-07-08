---
category: general
date: 2026-07-03
description: إضافة ظل إلى الشكل في بايثون باستخدام Aspose.Words. تعلّم كيفية تطبيق
  الظل على المستطيل وإدراج شكل بظل في بضع أسطر فقط.
draft: false
keywords:
- add shadow to shape
- apply shadow to rectangle
- how to add shape shadow
- insert shape with shadow
language: ar
og_description: أضف ظلًا إلى الشكل في بايثون بسرعة. يوضح هذا الدليل كيفية تطبيق الظل
  على المستطيل وإدراج شكل مع ظل باستخدام Aspose.Words.
og_title: إضافة ظل إلى الشكل في بايثون – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Add shadow to shape in Python using Aspose.Words. Learn how to apply
    shadow to rectangle and insert shape with shadow in just a few lines.
  headline: Add Shadow to Shape in Python – Complete Programming Guide
  type: TechArticle
- description: Add shadow to shape in Python using Aspose.Words. Learn how to apply
    shadow to rectangle and insert shape with shadow in just a few lines.
  name: Add Shadow to Shape in Python – Complete Programming Guide
  steps:
  - name: '**Forgot to enable `shadow.visible`** – The shadow properties exist, but
      they stay hidden until you set `visible = True`.'
    text: '**Forgot to enable `shadow.visible`** – The shadow properties exist, but
      they stay hidden until you set `visible = True`.'
  - name: '**Using the wrong shape type** – Not all shapes support shadows (e.g.,
      line shapes). Stick with `ShapeType.RECTANGLE`, `OVAL`, or `CLOUD`.'
    text: '**Using the wrong shape type** – Not all shapes support shadows (e.g.,
      line shapes). Stick with `ShapeType.RECTANGLE`, `OVAL`, or `CLOUD`.'
  - name: '**Saving before configuring** – If you call `doc.save()` before setting
      the shadow, you’ll get a plain rectangle. Always configure first.'
    text: '**Saving before configuring** – If you call `doc.save()` before setting
      the shadow, you’ll get a plain rectangle. Always configure first.'
  - name: '**License issues** – Running without a license adds a watermark. Double‑check
      the path to your `.lic` file.'
    text: '**License issues** – Running without a license adds a watermark. Double‑check
      the path to your `.lic` file.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
title: إضافة ظل إلى الشكل في بايثون – دليل برمجة شامل
url: /ar/python/images-shapes/add-shadow-to-shape-in-python-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إضافة ظل إلى الشكل في بايثون – دليل برمجة شامل

هل تساءلت يومًا **كيف تضيف ظلًا للشكل** في مستند Word عندما تقوم بأتمتة التقارير؟ لست الوحيد. إضافة ظل خفيف يمكن أن يجعل المستطيل يبرز، محولًا كتلة نصية مملة إلى إشارة بصرية تجذب انتباه القارئ.  

في هذا الدرس سنستعرض مثالًا عمليًا يوضح بالضبط **كيف تضيف ظلًا للشكل** باستخدام مكتبة Aspose.Words للبايثون. في النهاية ستعرف كيف **تطبق الظل على المستطيل**، وتدرج شكلًا بظل، وتحفظ النتيجة كملف PDF — كل ذلك في أقل من دقيقة من الشيفرة.

## ما ستتعلمه

- إعداد Aspose.Words للبايثون في بيئة افتراضية  
- **إدراج شكل بظل** – تحديدًا مستطيل  
- تكوين خصائص الظل مثل الضبابية (blur)، المسافة (distance)، الزاوية (angle)، الشفافية (opacity)، واللون (color)  
- حفظ المستند كملف PDF والتحقق من المظهر البصري  

لا يلزم أي خبرة سابقة مع Aspose؛ فقط فهم أساسي للبايثون ورغبة في التجربة.

## المتطلبات المسبقة

- تثبيت Python 3.8+ على جهازك  
- وجود ترخيص فعال لـ Aspose.Words للبايثون (أو مفتاح تقييم مجاني)  
- محرر نصوص أو بيئة تطوير متكاملة (VS Code، PyCharm، أو حتى دفتر ملاحظات بسيط)  

إذا كان كل ذلك جاهزًا، لنبدأ.

---

## إضافة ظل إلى الشكل – تنفيذ خطوة بخطوة

فيما يلي السكربت الكامل وجاهز للتنفيذ. لا تتردد في نسخه إلى ملف يُسمى `shadow_example.py` وتشغيله.

```python
# shadow_example.py
import aspose.words as aw
import aspose.words.drawing as drawing

# Step 1: Create a new document and a builder to edit it
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Step 2: Insert a rectangle shape with the desired size
# This is where we **apply shadow to rectangle** later on
rectangle = builder.insert_shape(drawing.ShapeType.RECTANGLE, 200, 100)

# Step 3: Access the shape's shadow format
shadow = rectangle.shadow_format

# Step 4: Enable the shadow and configure its appearance
shadow.visible = True          # Show the shadow
shadow.blur = 5.0              # Blur radius for a soft edge
shadow.distance = 4.0          # Offset from the shape (in points)
shadow.angle = 45              # Direction in degrees (45° = diagonal down‑right)
shadow.opacity = 0.7           # Transparency (0 = fully transparent, 1 = opaque)
shadow.color = aw.Color.black  # Classic black shadow

# Step 5: Save the document with the shaped shadow
doc.save("shadow_demo.pdf")
print("Document saved as shadow_demo.pdf")
```

> **نصيحة احترافية:** إذا كنت تفضل لونًا مختلفًا، ما عليك سوى استبدال `aw.Color.black` بـ `aw.Color.gray` أو أي قيمة RGB مخصصة.

### لماذا كل خطوة مهمة

- **إنشاء المستند والباني** يمنحك لوحة نظيفة. `DocumentBuilder` هو الأداة الأساسية التي تسمح لك بإدراج الأشكال والنصوص والمزيد.  
- **إدراج المستطيل** هو جوهر عملية **إدراج شكل بظل**. يمكنك تغيير الأبعاد (`200, 100`) لتناسب تخطيطك.  
- **الوصول إلى `shadow_format`** يوفر كائنًا مخصصًا يعزل جميع إعدادات الظل، مما يبقي الشيفرة منظمة.  
- **تكوين الظل** يتيح لك محاكاة الإضاءة الواقعية. `blur` ينعّم الحواف، `distance` يدفع الظل بعيدًا، و`angle` يحدد اتجاهه — تخيل مصدر ضوء بزاوية 45°.  
- **الحفظ كملف PDF** اختياري؛ يمكنك أيضًا الحفظ كـ `.docx` إذا كنت تحتاج إلى تعديل إضافي في Word.  

---

## إعداد Aspose.Words للبايثون

إذا لم تقم بتثبيت المكتبة بعد، نفّذ الأمر:

```bash
pip install aspose-words
```

تأكد من وجود ملف ترخيص صالح (`Aspose.Words.lic`) في نفس دليل السكربت، أو اضبط الترخيص برمجيًا:

```python
license = aw.License()
license.set_license("Aspose.Words.lic")
```

بدون ترخيص ستحصل على علامة مائية في الصفحة الأولى، وهذا مقبول للاختبار لكنه غير مناسب للإنتاج.

---

## تعديل معلمات الظل (متقدم)

أحيانًا لا تتطابق القيم الافتراضية مع لغة التصميم الخاصة بك. إليك ورقة غش سريعة:

| الخاصية | النطاق المعتاد | التأثير البصري |
|----------|---------------|---------------|
| `blur`   | 0‑10          | القيم الأعلى → ظل أكثر نعومة |
| `distance` | 0‑10        | المسافة الأكبر → يتحرك الظل بعيدًا عن الشكل |
| `angle`  | 0‑360         | يتحكم في الاتجاه؛ 0° = اليسار، 90° = الأعلى |
| `opacity`| 0‑1           | 0 = غير مرئي، 1 = صلب |
| `color`  | Any `aw.Color`| استخدم ألوان العلامة التجارية لمظهر مخصص |

يمكنك حتى تحريك هذه القيم إذا كنت تولد سلسلة من الشرائح — فقط قم بالتكرار عبر قائمة الزوايا وأعد حفظ كل مستند.

---

## التحقق من النتيجة

افتح `shadow_demo.pdf` في أي عارض PDF. يجب أن ترى مستطيلًا نظيفًا مع ظل أسود ناعم شبه شفاف مائل قطريًا إلى الأسفل واليمين. إذا كان الظل شديدًا جدًا، قلل `opacity` أو زد `blur`. تحتاج إلى مظهر أخف؟ جرّب `aw.Color.gray` بدلًا من الأسود.

![مثال على إضافة ظل إلى الشكل](https://example.com/shadow_demo.png "مثال على إضافة ظل إلى الشكل")

*نص بديل للصورة: “مثال على إضافة ظل إلى الشكل – مستطيل مع ظل مسقط تم إنشاؤه باستخدام Aspose.Words للبايثون.”*

---

## الأخطاء الشائعة وكيفية تجنّبها

1. **نسيت تمكين `shadow.visible`** – خصائص الظل موجودة، لكنها تظل مخفية حتى تقوم بتعيين `visible = True`.  
2. **استخدام نوع الشكل الخطأ** – ليست كل الأشكال تدعم الظلال (مثل الأشكال الخطية). استخدم `ShapeType.RECTANGLE`، `OVAL`، أو `CLOUD`.  
3. **الحفظ قبل التكوين** – إذا استدعيت `doc.save()` قبل ضبط الظل، ستحصل على مستطيل عادي. دائمًا قم بالتكوين أولاً.  
4. **مشكلات الترخيص** – التشغيل بدون ترخيص يضيف علامة مائية. تحقق مرة أخرى من مسار ملف `.lic` الخاص بك.

---

## توسيع المثال

الآن بعد أن أتقنت **إضافة ظل إلى الشكل**, فكر في الخطوات التالية:

- **تطبيق الظل على أشكال أخرى** مثل `OVAL` أو `CLOUD` باستخدام نفس النمط.  
- **دمج ظلال متعددة** عن طريق تراكب الأشكال وضبط المسافات للحصول على تأثير ثلاثي الأبعاد.  
- **تصدير إلى صيغ أخرى** (`docx`، `html`) لرؤية كيف يعرض الظل في عارضات مختلفة.  
- **دمجها في مولد تقارير أكبر** حيث يحصل كل مخطط أو جدول على ظل خفيف لتسلسل بصري.  

جميع هذه الأفكار تعيد استخدام المنطق الأساسي الذي غطيناه، لذا ستقضي وقتًا أقل في البحث على جوجل ووقتًا أكثر في البناء.

---

## الخلاصة

لقد حولنا سكربتًا بسيطًا إلى حل قوي لـ **إضافة ظل إلى الشكل** في بايثون. من خلال إنشاء مستند، إدراج مستطيل، الوصول إلى `shadow_format` الخاص به، تخصيص المظهر، وأخيرًا حفظ الملف، لديك الآن نمط قابل لإعادة الاستخدام يمكن دمجه في أي خط أنابيب تقارير مؤتمت.

تذكر أن قوة الظل لا تكمن فقط في الجماليات بل في توجيه انتباه القارئ. سواء كنت تولد فواتير، كتيبات تسويقية، أو لوحات تحكم داخلية، فإن الظل المضعف بشكل جيد يمكن أن يجعل محتواك يبدو مصقولًا واحترافيًا.

هل لديك أسئلة حول تعديل الظل أو دمجه مع ميزات Aspose الأخرى؟ اترك تعليقًا أدناه، وبرمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [دروس ظل شكل Aspose.Words – إضافة ظل إلى شكل Word في C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [إنشاء شكل مستطيل في Word باستخدام Aspose.Words – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [إنشاء مستند Word بلغة Java – إضافة شكل مستطيل مع تأثير الظل](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}