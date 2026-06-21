---
category: general
date: 2026-06-21
description: إنشاء شكل مستطيل في بايثون باستخدام Aspose.Words. تعلم كيفية إضافة ظل
  إلى الشكل، وتعيين لون تعبئة الشكل، وحفظ المستند كملف PDF في دقائق.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- set shape fill color
language: ar
og_description: إنشاء شكل مستطيل في بايثون باستخدام Aspose.Words. يوضح هذا الدليل
  كيفية إضافة ظل إلى الشكل، وتعيين لون تعبئة الشكل، وحفظ المستند كملف PDF.
og_title: إنشاء شكل مستطيل في بايثون – دليل Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-21'
  description: Create rectangle shape in Python using Aspose.Words. Learn how to add
    shadow to shape, set shape fill color, and save document as PDF in minutes.
  headline: Create rectangle shape in Python – Aspose.Words tutorial
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF generation
title: إنشاء شكل مستطيل في بايثون – دليل Aspose.Words
url: /ar/python/images-shapes/create-rectangle-shape-in-python-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء شكل مستطيل في Python – دليل Aspose.Words

هل تساءلت يومًا **كيف تنشئ شكل مستطيل** في مستند Word أثناء كتابة الكود بلغة Python؟ لست وحدك. يواجه العديد من المطورين صعوبة عندما يحتاجون إلى عنصر بصري سريع—مثل صندوق ملون بظل خفيف—ثم تصديره كملف PDF.  

في هذا الدليل سنستعرض مثالًا كاملاً قابلاً للتنفيذ **ينشئ شكل مستطيل**، **يضبط لون تعبئة الشكل**، **يضيف ظلًا إلى الشكل**، وأخيرًا **يحفظ المستند كملف PDF**. لا مراجع غامضة، فقط كود ملموس يمكنك نسخه‑ولصقه وتشغيله اليوم.

## ما ستحتاجه

قبل أن نبدأ، تأكد من وجود ما يلي على جهازك:

- Python 3.8 أو أحدث (الصياغة التي نستخدمها تعمل على أي نسخة حديثة).
- ترخيص فعال لـ Aspose.Words for Python أو نسخة تجريبية مجانية (المكتبة مكتوبة بالكامل بـ Python، ولا تحتاج إلى COM).
- محرر نصوص أو بيئة تطوير متكاملة تشعر بالراحة معها—VS Code يعمل جيدًا، لكن أي محرر سيؤدي المهمة.

هذا كل ما تحتاجه. لا أطر عمل ثقيلة، ولا تبعيات نظام تشغيل إضافية. لنبدأ.

## الخطوة 1: تثبيت Aspose.Words for Python

أولًا وقبل كل شيء. إذا لم تقم بذلك بعد، احصل على الحزمة من PyPI:

```bash
pip install aspose-words
```

لماذا هذه الخطوة مهمة: Aspose.Words يوفر الفئتين `Document` و `DocumentBuilder` اللتين سنعتمد عليهما. بدون المكتبة، لن توجد الدوال اللاحقة—مثل `insert_shape`—وبالتالي سيتعطل السكربت قبل أن يرسم أي شيء.

> **نصيحة احترافية:** حافظ على بيئة افتراضية نظيفة. نفّذ `python -m venv .venv && source .venv/bin/activate` قبل التثبيت، حتى تبقى المكتبة معزولة عن حزم النظام.

## الخطوة 2: إنشاء مستند جديد وDocumentBuilder

الآن سنقوم فعليًا **بإنشاء شكل مستطيل** – لكن أولًا نحتاج إلى لوحة فارغة.

```python
import aspose.words as aw

# Initialize a new, empty Word document
doc = aw.Document()
# DocumentBuilder lets us add content programmatically
builder = aw.DocumentBuilder(doc)
```

كائن `Document` يمثل الملف بالكامل، بينما `DocumentBuilder` هو أداة مساعدة تعرف موضع المؤشر ويمكنها إدراج العناصر في تلك النقطة. فكر في الـ builder كقلم يكتب على الصفحة.

## الخطوة 3: إدراج شكل المستطيل

هنا يحدث الإجراء الأساسي. سن **ننشئ شكل مستطيل** بعرض وارتفاع ثابتين، ثم نحدد موقعه على الصفحة.

```python
# Insert a rectangle 200 points wide and 100 points tall
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

لماذا المستطيل؟ إنه أبسط شكل يتيح لنا عرض ألوان التعبئة والظلال. إذا احتجت إلى دائرة أو نجمة لاحقًا، استبدل `ShapeType.RECTANGLE` بقيمة enum أخرى.

## الخطوة 4: ضبط لون تعبئة الشكل

الصندوق الأبيض العادي ليس مثيرًا، لذا لن **نضبط لون تعبئة الشكل** إلى لون هادئ—الأزرق الفاتح يناسب التقارير.

```python
# Apply a light‑blue background to the rectangle
rectangle.fill_color = aw.Color.light_blue
```

يمكنك استخدام أي من أعضاء `aw.Color` المعرفة مسبقًا (`red`, `green`, `dark_gray`, إلخ) أو تمرير قيمة RGB (`aw.Color.from_argb(255, 30, 144, 255)`). لون التعبئة هو ما يراه المستخدم قبل تطبيق أي ظل أو حد.

## الخطوة 5: إضافة ظل إلى الشكل

الآن لللمسة البصرية: **إضافة ظل إلى الشكل**. الظلال تعطي عمقًا وتبرز المستطيل على الصفحة.

```python
# Grab the shadow format object
shadow = rectangle.shadow_format

# Turn the shadow on
shadow.visible = True
# Choose a dark gray tone for realism
shadow.color = aw.Color.dark_gray
# Blur radius controls softness (5 points is a nice middle ground)
shadow.blur = 5
# Horizontal and vertical offsets shift the shadow relative to the shape
shadow.offset_x = 3
shadow.offset_y = 3
# Slight transparency makes the shadow feel natural
shadow.transparency = 0.2
# Use an outer shadow – you could also try INSET for a different effect
shadow.type = aw.drawing.ShadowType.OUTER
```

**كيف نضيف الظل**؟ الكود أعلاه يفعل ذلك بالضبط، لكن دعنا نفصل سبب أهمية كل خاصية:

- `visible` – يفعّل أو يطفئ التأثير.
- `color` – يحدد اللون؛ اللون الرمادي الداكن يحاكي الإضاءة الطبيعية.
- `blur` – القيم الأعلى تنتج حافة أكثر نعومة.
- `offset_x` / `offset_y` – يحركان الظل بعيدًا عن الشكل؛ عدّل هاتين القيمتين لمحاكاة زوايا إضاءة مختلفة.
- `transparency` – 0 يعني صلابة، 1 يعني شفافية كاملة؛ 0.2 يعطي انطباعًا خفيفًا.
- `type` – `OUTER` يلقي الظل خارج الشكل، بينما `INNER` يضعه داخله.

إذا أردت ظلًا درامياً، زد `blur` إلى 10‑15 ورفع `offset_x`/`offset_y` إلى 6‑8.

## الخطوة 6: حفظ المستند كملف PDF

كل هذا الجهد لا فائدة منه إذا لم نستطع **حفظ المستند كملف PDF** ومشاركته. Aspose.Words يجعل ذلك سطرًا واحدًا:

```python
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

لماذا PDF؟ ملفات PDF تحافظ على التخطيط عبر المنصات، مما يجعلها مثالية للتقارير، الفواتير، أو أي مادة قابلة للطباعة. طريقة `save` تكتشف امتداد الملف تلقائيًا وتختار الصيغة المناسبة—فقط تأكد أن المسار ينتهي بـ `.pdf`.

### النتيجة المتوقعة

افتح ملف `ShapeWithShadow.pdf` الناتج وسترى مستطيلًا أزرق فاتحًا مركّزًا بالقرب من أعلى الصفحة الأولى، مع ظل رمادي داكن ناعم مُزاح قليلًا إلى اليمين والأسفل. حواف الشكل واضحة، الظل خفيف، وحجم الملف عادةً أقل من 100 KB.

## إضافي: تعديل الظلال – إجابات على “كيف أضيف ظل”

قد تتساءل، *“هل يمكنني تغيير اتجاه الظل دون تحريك الشكل؟”* بالتأكيد. موقع الظل مستقل عن إحداثيات الشكل؛ فقط عدّل `offset_x` و `offset_y`. القيم الموجبة تحرك الظل إلى اليمين/الأسفل، والقيم السالبة تحركه إلى اليسار/الأعلى. لمصدر ضوء من أعلى‑اليسار، استخدم `offset_x = -3` و `offset_y = -3`.

سؤال شائع آخر: *“ماذا لو أردت عدة ظلال على نفس الشكل؟”* Aspose.Words يدعم ظلًا واحدًا فقط لكل شكل. إذا احتجت تأثيرات طبقية، أنشئ نسخة مكررة من الشكل، أزحها قليلًا، وطبق ظلًا مختلفًا على كل نسخة. هذه حيلة بسيطة لكنها فعّالة.

## البرنامج الكامل – جاهز للتنفيذ

فيما يلي السكربت الكامل المستقل. انسخه إلى ملف باسم `create_rectangle_with_shadow.py` وشغّله باستخدام `python create_rectangle_with_shadow.py`.

```python
import aspose.words as aw

# ---------- Initialize document ----------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ---------- Insert rectangle ----------
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# ---------- Set fill color ----------
rectangle.fill_color = aw.Color.light_blue

# ---------- Configure shadow ----------
shadow = rectangle.shadow_format
shadow.visible = True
shadow.color = aw.Color.dark_gray
shadow.blur = 5
shadow.offset_x = 3
shadow.offset_y = 3
shadow.transparency = 0.2
shadow.type = aw.drawing.ShadowType.OUTER

# ---------- Save as PDF ----------
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

> **ملاحظة:** استبدل `YOUR_DIRECTORY` بمسار مطلق أو نسبي موجود على جهازك. إذا لم يكن المجلد موجودًا، سيُطلق Python استثناء `FileNotFoundError`.

## الأخطاء الشائعة وكيفية تجنّبها

| المشكلة | السبب | الحل |
|-------|----------------|-----|
| الظل لا يظهر | `shadow.visible` يبقى على القيمة الافتراضية `False` | تأكد من `shadow.visible = True` |
| الشكل غير مرئي | لون التعبئة مضبوط على `aw.Color.transparent` أو `None` | استخدم لونًا صلبًا مثل `aw.Color.light_blue` |
| PDF فارغ | نسيان استدعاء `doc.save` أو حفظه بامتداد غير صحيح | نفّذ `doc.save("output.pdf")` وتحقق من المسار |
| خطأ وقت التشغيل `ImportError` | Aspose.Words غير مثبت أو البيئة غير صحيحة | نفّذ `pip install aspose-words` داخل البيئة الافتراضية النشطة |

## الخطوات التالية – استكشاف المزيد من الأشكال والتنسيق

الآن بعد أن أتقنت **إنشاء شكل مستطيل**، يمكنك:

- استبدال `ShapeType.RECTANGLE` بـ `ShapeType.ELLIPSE` أو `ShapeType.PENTAGON` لتجربة أشكال أخرى.
- إضافة نص داخل الشكل باستخدام `builder.move_to(rectangle.absolute_position)` ثم `builder.writeln("Hello World")`.
- دمج عدة أشكال في مجموعة باستخدام `group = aw.drawing.GroupShape(doc)` لإنشاء مخططات معقدة.
- تصدير إلى صيغ أخرى مثل DOCX (`doc.save("output.docx")`) أو HTML (`doc.save("output.html")`) لترى كيف يُترجم الظل.

كل هذه الإضافات تبنى على المفاهيم الأساسية نفسها: **إضافة ظل إلى الشكل**، **ضبط لون تعبئة الشكل**، و **حفظ المستند كملف PDF** (أو صيغة أخرى).

---

### معاينة الصورة *(اختياري)*

![Create rectangle shape with shadow in Python](https://example.com/rectangle-shadow.png "Create rectangle shape with shadow in Python")

*تُظهر اللقطة الناتج النهائي لملف PDF مع مستطيل أزرق فاتح وظل خارجي خفيف.*

---

## الخلاصة

استعرضنا جميع الخطوات اللازمة **لإنشاء شكل مستطيل** في Python، تطبيق تعبئة مخصصة، **إضافة ظل إلى الشكل**، وأخيرًا **حفظ المستند كملف PDF**. الكود قابل للتنفيذ بالكامل، والشروحات تغطي *السبب* وراء كل خاصية، وتطرقنا إلى الحالات الشائعة وكيفية التعامل معها.

## ما الذي ينبغي أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تُبني على التقنيات التي استعرضناها في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة‑بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}