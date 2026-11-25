---
category: general
date: 2026-11-25
description: إضافة ظل إلى الشكل في مستند Word باستخدام Python. تعلّم كيفية إدراج شكل
  مستطيل في Word وتطبيق ظل شفاف باستخدام Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- insert rectangle shape word
- how to create word document python
- Aspose.Words Python
- shape formatting Python
language: ar
lastmod: 2026-11-25
og_description: إضافة ظل إلى الشكل في مستند Word باستخدام Python. يوضح هذا الدرس كيفية
  إدراج شكل مستطيل في Word وتعيين ظل شفاف بنسبة 30٪ باستخدام Aspose.Words.
og_image_alt: Add shadow to shape example in a Word document created by Python
og_title: إضافة ظل إلى الشكل في مستند Word باستخدام Python – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Add shadow to shape in a Word document with Python. Learn how to insert
    rectangle shape in Word and apply a transparent shadow using Aspose.Words.
  headline: How to add shadow to shape in a Word document using Python
  type: TechArticle
tags:
- Python
- Aspose.Words
- Word automation
title: كيفية إضافة ظل إلى الشكل في مستند Word باستخدام Python
url: /ar/python/images-shapes/how-to-add-shadow-to-shape-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إضافة ظل إلى الشكل في مستند Word باستخدام Python

إذا كنت بحاجة إلى **إضافة ظل إلى الشكل** في مستند Word، فإن هذا الدليل يوضح لك حلاً كاملاً قابلاً للتنفيذ. سترى كيفية إنشاء ملف Word، وإدراج شكل مستطيل، وتطبيق ظل شفاف بنسبة 30 % — كل ذلك باستخدام مكتبة Aspose.Words for Python.

العمل مع مستندات Word برمجياً يوفر عليك التنسيق اليدوي ويسمح لك بإنشاء تقارير، عقود، أو منشورات تسويقية على نطاق واسع. بنهاية هذا الدرس ستكون قادرًا على الإجابة على سؤال “**how to create Word document python**” بعينة شفرة جاهزة للتنفيذ.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من أن لديك:

* Python 3.8 أو أحدث مثبت.
* رخصة Aspose.Words for Python سارية (الإصدار التجريبي المجاني يعمل للتقييم).
* `aspose-words` الحزمة مثبتة عبر `pip install aspose-words`.
* مجلد يمكن كتابة ملف الإخراج فيه (استبدل `YOUR_DIRECTORY` في الشيفرة).

لا توجد تبعيات إضافية مطلوبة.

## الخطوة 1: إنشاء مستند Word جديد

الخطوة الأولى هي إنشاء كائن `Document`. هذا الكائن يمثل ملف .docx بالكامل في الذاكرة.

```python
import aspose.words as aw

# Create an empty Word document
doc = aw.Document()
# DocumentBuilder provides a convenient API for adding content
builder = aw.DocumentBuilder(doc)
```

`DocumentBuilder` يعمل كالمؤشر الافتراضي. عندما تستدعي طرقه، تقوم المكتبة بإدراج العناصر المقابلة في موقع المؤشر الحالي.

## الخطوة 2: إدراج شكل مستطيل في Word

بعد ذلك تقوم **بإدراج شكل مستطيل في Word** باستخدام طريقة `insert_shape` الخاصة بالـ builder. تتطلب الطريقة نوع الشكل وحجمه بالنقاط (1 نقطة = 1/72 بوصة).

```python
# Insert a rectangle shape that is 100 points wide and 50 points tall
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)
```

يمكنك تغيير الأبعاد لتتناسب مع تصميمك. يصبح المستطيل جزءًا من طبقة الرسم في المستند، مما يعني أنه يمكنك تعديل ملئه أو حدوده أو ظله لاحقًا.

## الخطوة 3: الوصول إلى تنسيق ظل الشكل

كل كائن رسم يكشف عن خاصية `shadow_format` التي تتحكم في مظهر الظل. استخرجها حتى تتمكن من تعديل الشفافية، الإزاحة، الضبابية، واللون.

```python
# Get the ShadowFormat object for the rectangle
shadow = shape.shadow_format
```

في هذه المرحلة يكون الشكل لديه الظل الافتراضي (بدون ظل). كائن `ShadowFormat` يحتوي على جميع المعلمات التي تحتاجها لإنشاء تأثير واقعي.

## الخطوة 4: جعل الظل شفافًا بنسبة 30 %

يتم التعبير عن الشفافية كقيمة بين `0` (معتم بالكامل) و `1` (شفاف بالكامل). ضبطها إلى `0.3` ينتج ظلًا شفافًا بنسبة 30 %، وهو غالبًا ما يكون كافيًا لإضافة عمق دون إغراق النص.

```python
# Apply a 30 % transparent shadow
shadow.transparency = 0.3
# Optional: adjust other shadow properties for a nicer look
shadow.visible = True               # Ensure the shadow is turned on
shadow.distance = 4                 # Distance of the shadow from the shape (points)
shadow.blur = 4                     # Amount of blur applied to the shadow
shadow.color = aw.Color.black       # Shadow color
```

هذه الخصائص الإضافية ليست ضرورية، لكنها توضح كيف يمكنك ضبط التأثير بدقة. علم `visible` أساسي؛ إذا نسيته، لن يظهر الظل حتى لو تم تكوين الإعدادات الأخرى.

## الخطوة 5: حفظ المستند لعرض النتيجة

أخيرًا، احفظ المستند على القرص. فتح ملف `.docx` الناتج في Microsoft Word أو أي عارض متوافق يظهر المستطيل مع الظل الشفاف المطبق.

```python
# Save the document to the desired location
output_path = r"YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

عند فتح `output.docx`، سترى مستطيلًا بسيطًا مع ظل رمادي خفيف مائل إلى أسفل‑اليمين. شفافية الظل بنسبة 30 % تجعل الشكل يبدو مرتفعًا عن الصفحة.

![Add shadow to shape example](placeholder-image.png){: .align-center alt="مثال على إضافة ظل إلى الشكل في مستند Word تم إنشاؤه باستخدام Python"}

## البرنامج الكامل القابل للتنفيذ

جمع كل الأجزاء معًا يمنحك سكريبتًا مستقلًا يمكنك نسخه، لصقه، وتشغيله فورًا.

```python
import aspose.words as aw

def create_word_with_shadow(output_path: str):
    """
    Creates a Word document that contains a rectangle shape
    with a 30 % transparent shadow.
    """
    # Step 1: Initialize document and builder
    doc = aw.Document()
    builder = aw.DocumentBuilder(doc)

    # Step 2: Insert rectangle shape
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)

    # Step 3: Access shadow format
    shadow = shape.shadow_format

    # Step 4: Configure shadow properties
    shadow.visible = True
    shadow.transparency = 0.3
    shadow.distance = 4
    shadow.blur = 4
    shadow.color = aw.Color.black

    # Step 5: Save the document
    doc.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    # Replace with a valid folder on your machine
    create_word_with_shadow(r"YOUR_DIRECTORY/output.docx")
```

**الناتج المتوقع:** فتح `output.docx` المُولد يعرض صفحة واحدة بها مستطيل يلقي ظلًا خفيفًا شبه شفاف. لا يلزم أي تنسيق إضافي.

## الاختلافات الشائعة وحالات الحافة

| الحالة | كيفية تعديل الشيفرة |
|-----------|-----------------------|
| **نوع الشكل مختلف** (مثال: إهليلج) | غيّر `aw.drawing.ShapeType.RECTANGLE` إلى `aw.drawing.ShapeType.ELLIPSE`. |
| **لون ظل مخصص** | عيّن `shadow.color = aw.Color.from_argb(255, 128, 0, 0)` للحصول على ظل أحمر. |
| **أشكال متعددة** | استدعِ `builder.insert_shape` بشكل متكرر؛ كل استدعاء يُعيد كائن `Shape` منفصل يمكنك تنسيقه بشكل مستقل. |
| **الحفظ كملف PDF** | استبدل `doc.save(output_path)` بـ `doc.save(output_path.replace('.docx', '.pdf'))` واستخدم امتداد `.pdf`. |
| **التشغيل بدون رخصة** | الإصدار التجريبي المجاني يضيف علامة مائية إلى الصفحة الأولى. احصل على رخصة لإزالتها للاستخدام الإنتاجي. |

تُظهر هذه الاختلافات أن النمط نفسه — إنشاء مستند، إدراج شكل، تعديل `shadow_format`، حفظ — يغطي معظم سيناريوهات الأتمتة.

## نصائح وممارسات أفضل

* **إعادة استخدام الـ builder**: احتفظ بنسخة واحدة من `DocumentBuilder` لكامل المستند لتجنب إنشاء كائنات غير ضرورية.
* **تحرير الموارد**: في الخدمات طويلة التشغيل، استدعِ `doc.dispose()` بعد الحفظ لتحرير الذاكرة الأصلية.
* **التحقق من صحة الإخراج**: استخدم `doc.validate(aw.ValidationType.FULL_VALIDATION)` قبل الحفظ إذا كنت بحاجة لضمان التوافق مع معيار Open XML.
* **توافق الإصدارات**: الشيفرة تعمل مع Aspose.Words for Python ≥ 22.9. تأكد من أن حزمك محدثة باستخدام `pip install --upgrade aspose-words`.

## الخلاصة

أنت الآن تعرف كيفية **إضافة ظل إلى الشكل** في مستند Word باستخدام Python. باتباع الخطوات الخمس — إنشاء مستند، **إدراج شكل مستطيل في Word**، ضبط الظل، ثم الحفظ — يمكنك أتمتة إنشاء مستندات مصقولة للتقارير، الفواتير، أو المواد التسويقية.  

من هنا قد ترغب في استكشاف خيارات تنسيق أخرى مثل التعبئات المتدرجة، التفاف النص، أو تحويل المستند إلى PDF. كل من هذه المواضيع يبنى على نفس مفاهيم `DocumentBuilder` وتنسيق الشكل التي تم تقديمها في هذا الدرس.

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة شيفرة كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إنشاء شكل مستطيل في مستند Word باستخدام Python](/words/english/python-net/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/)
- [إضافة ظل إلى الشكل في Python – دليل Aspose.Words الكامل](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [إنشاء مستند Word فارغ وإضافة ظل إلى الشكل – دليل Python كامل](/words/english/python-net/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-pyth/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}