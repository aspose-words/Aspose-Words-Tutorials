---
category: general
date: 2026-07-29
description: إضافة ظل إلى الشكل في Word باستخدام Python و Aspose.Words. تعلّم كيفية
  تطبيق تأثير الظل على مستندات Word بسرعة مع مثال كامل للكود.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- apply shadow effect word
language: ar
lastmod: 2026-07-29
og_description: أضف ظلًا إلى الشكل في مستندات Word باستخدام Python. يوضح هذا الدليل
  كيفية تطبيق تأثير الظل على ملفات Word باستخدام Aspose.Words، مع الشيفرة والنصائح.
og_image_alt: Word document displaying a rectangle shape with a soft gray shadow applied
og_title: إضافة الظل إلى الشكل في Word – دليل Python
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Add shadow to shape in Word using Python and Aspose.Words. Learn how
    to apply shadow effect Word documents quickly with a full code example.
  headline: Add Shadow to Shape in Word with Python – Complete Guide
  type: TechArticle
- description: Add shadow to shape in Word using Python and Aspose.Words. Learn how
    to apply shadow effect Word documents quickly with a full code example.
  name: Add Shadow to Shape in Word with Python – Complete Guide
  steps:
  - name: '**No shape found** – If your document only contains text, the script will
      raise a `ValueError`. Add a shape first or extend the script to iterate over
      all `Shape` nodes.'
    text: '**No shape found** – If your document only contains text, the script will
      raise a `ValueError`. Add a shape first or extend the script to iterate over
      all `Shape` nodes.'
  - name: '**License watermark** – Running the code without a proper license inserts
      an “Aspose.Words Evaluation” watermark on each page. Grab a trial license from
      the Aspose portal to keep the output clean.'
    text: '**License watermark** – Running the code without a proper license inserts
      an “Aspose.Words Evaluation” watermark on each page. Grab a trial license from
      the Aspose portal to keep the output clean.'
  - name: '**Incorrect file paths** – Using relative paths can cause `FileNotFoundError`
      when the script’s working directory differs. Prefer `os.path.abspath` or pass
      absolute paths.'
    text: '**Incorrect file paths** – Using relative paths can cause `FileNotFoundError`
      when the script’s working directory differs. Prefer `os.path.abspath` or pass
      absolute paths.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word Automation
title: إضافة ظل إلى الشكل في Word باستخدام Python – دليل كامل
url: /ar/python/images-shapes/add-shadow-to-shape-in-word-with-python-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إضافة ظل إلى الشكل في Word باستخدام Python – دليل شامل

هل احتجت يومًا إلى **add shadow to shape** في مستند Word لكنك لم تكن متأكدًا من أين تبدأ؟ في هذا الدرس سنرشدك إلى طريقة عملية لـ **apply shadow effect Word** باستخدام مكتبة Aspose.Words for Python.

إذا كنت قد لعبت يومًا بواجهة المستخدم وفكرت، “يجب أن يكون هناك طريقة برمجية للقيام بذلك”، فأنت في المكان الصحيح. في النهاية ستحصل على سكريبت قابل للتنفيذ يضيف ظلًا ناعمًا إلى أي شكل تختاره.

## المتطلبات المسبقة

- Python 3.8+ مثبت (أي نسخة حديثة تعمل)
- رخصة Aspose.Words for Python سارية أو نسخة تجريبية مجانية (تعمل الواجهة البرمجية بدون رخصة لكنها تضيف علامة مائية)
- مستند Word (`.docx`) يحتوي بالفعل على شكل واحد على الأقل (مستطيل أو صورة أو SmartArt)
- إلمام أساسي باستيراد Python ومعالجة الاستثناءات

> **نصيحة احترافية:** إذا لم يكن لديك شكل بعد، افتح Word، أدرج مستطيلًا بسيطًا، واحفظ الملف باسم `input.docx` في مجلد يمكنك الإشارة إليه من السكريبت الخاص بك.

## تثبيت Aspose.Words for Python

شغّل أمر pip التالي في الطرفية الخاصة بك:

```bash
pip install aspose-words
```

هذا يجلب أحدث إصدار 23.x، والذي يدعم خصائص الظل على عقد `Shape`.

## الخطوة 1: تحميل مستند Word

أول شيء نقوم به هو فتح ملف `.docx` الموجود. هنا تبدأ عملية **add shadow to shape**.

```python
import aspose.words as aw

# Load the source document
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)
```

> **لماذا هذا مهم:** `aw.Document` يحلل ملف Word بالكامل إلى بنية شبيهة بـ DOM، مما يتيح لنا استعراض العقد مثل الأشكال والفقرات والجداول.

## الخطوة 2: تحديد الشكل المستهدف

توفر Aspose.Words طريقة بحث عميقة `get_child` يمكنها جلب أول شكل بغض النظر عن مستوى التداخل. إذا كان لديك عدة أشكال، يمكنك تعديل الفهرس أو التكرار عبر جميعها.

```python
# Retrieve the first shape (deep search = True)
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

if shape is None:
    raise ValueError("No shape found in the document. Add a shape and try again.")
```

> **حالة حافة:** بعض المستندات تحتوي فقط على كائنات رسم (مثل الصور). تُمثل هذه أيضًا كعقد `Shape`، لذا يعمل هذا الكود لكل من المستطيلات والصور.

## الخطوة 3: ضبط مظهر الظل

الآن يأتي جوهر **add shadow to shape**—ضبط خصائص الظل. القيم التالية تعطي مظهرًا دقيقًا واحترافيًا:

```python
# Softness of the shadow edges
shape.shadow_blur = 5.0

# Horizontal and vertical offsets (in points)
shape.shadow_offset_x = 2.0
shape.shadow_offset_y = 2.0

# Transparency – 0 is invisible, 1 is solid
shape.shadow_opacity = 0.7
```

يمكنك تجربة هذه الأرقام:

- زيادة `shadow_blur` للحصول على حافة أكثر ضبابية.
- استخدام إزاحات سلبية لتحريك الظل إلى اليسار أو الأعلى.
- تعديل `shadow_opacity` لجعل الظل أكثر وضوحًا.

> **لماذا هذه القيم الافتراضية؟** تشبه الضبابية بمقدار 5 نقاط الظل الافتراضي في Word، بينما تجعل الشفافية 0.7 التأثير ملحوظًا دون أن يغمر لون تعبئة الشكل.

## الخطوة 4: حفظ المستند المعدل

أخيرًا، اكتب التغييرات إلى ملف جديد. الحفاظ على الأصل دون تعديل يسهل عملية تصحيح الأخطاء.

```python
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Shadow applied! Saved updated file to {output_path}")
```

في هذه المرحلة، لقد نجحت في **add shadow to shape** ويمكنك فتح `output.docx` لرؤية التأثير.

## مثال عملي كامل

بجمع كل ذلك معًا، إليك سكريبت مستقل يمكنك نسخه ولصقه وتشغيله فورًا:

```python
import aspose.words as aw
import os

def add_shadow_to_first_shape(input_file: str, output_file: str) -> None:
    """
    Loads a Word document, adds a soft shadow to the first shape,
    and saves the result to a new file.

    Parameters
    ----------
    input_file : str
        Path to the source .docx file.
    output_file : str
        Destination path for the modified document.
    """
    # Verify the input exists
    if not os.path.isfile(input_file):
        raise FileNotFoundError(f"Input file not found: {input_file}")

    # Load the document
    doc = aw.Document(input_file)

    # Find the first shape (deep search)
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

    if shape is None:
        raise ValueError("No shape found in the document. Insert a shape and retry.")

    # Apply shadow settings
    shape.shadow_blur = 5.0
    shape.shadow_offset_x = 2.0
    shape.shadow_offset_y = 2.0
    shape.shadow_opacity = 0.7

    # Save the updated document
    doc.save(output_file)

if __name__ == "__main__":
    INPUT_DOC = "YOUR_DIRECTORY/input.docx"
    OUTPUT_DOC = "YOUR_DIRECTORY/output.docx"
    add_shadow_to_first_shape(INPUT_DOC, OUTPUT_DOC)
    print("✅ Shadow added successfully.")
```

### النتيجة المتوقعة

افتح `output.docx` وسترى الشكل الأصلي الآن يضيف ظلًا رماديًا ناعمًا، مائلًا قليلاً إلى اليمين والأسفل. هذا التأثير يعكس ما تحصل عليه عند تطبيق **apply shadow effect word** يدويًا عبر الواجهة.

![Shadowed shape example](https://example.com/shadowed_shape.png "Word shape with a soft shadow"){: .center-image width="600" alt="Screenshot showing a shape with a shadow in a Word document"}

## تطبيق تأثير الظل في Word – خيارات متقدمة

إذا كنت بحاجة إلى مزيد من التحكم، تتيح لك Aspose.Words تعديل خصائص إضافية:

| Property | Description | Typical Range |
|----------|-------------|---------------|
| `shadow_color` | لون الظل (الافتراضي هو الأسود) | أي `aw.Color` |
| `shadow_type` | يحدد ما إذا كان الظل **خارجيًا**، **داخليًا**، أو **منظوريًا** | تعداد `aw.ShadowType` |
| `shadow_transform` | يطبق مصفوفة تحويل مخصصة للظلال المائلة | متقدم – استخدم بحذر |

مثال على ضبط ظل أزرق:

```python
shape.shadow_color = aw.Color.from_argb(255, 0, 0, 255)  # Opaque blue
shape.shadow_type = aw.ShadowType.OUTER
```

هذه الإعدادات تتيح لك **apply shadow effect Word** المستندات بطرق إبداعية، مثل إضافة ظل ملون إلى شعار.

## الأخطاء الشائعة وكيفية تجنبها

1. **No shape found** – إذا كان المستند يحتوي فقط على نص، سيُطلق السكريبت استثناء `ValueError`. أضف شكلًا أولاً أو وسّع السكريبت للتكرار عبر جميع عقد `Shape`.
2. **License watermark** – تشغيل الكود بدون رخصة صحيحة يضيف علامة مائية “Aspose.Words Evaluation” على كل صفحة. احصل على رخصة تجريبية من بوابة Aspose للحفاظ على النتيجة نظيفة.
3. **Incorrect file paths** – استخدام مسارات نسبية قد يسبب `FileNotFoundError` عندما يختلف دليل عمل السكريبت. يفضَّل استخدام `os.path.abspath` أو تمرير مسارات مطلقة.

## الخطوات التالية

الآن بعد أن أتقنت **add shadow to shape**، قد ترغب في استكشاف المواضيع ذات الصلة:

- **Apply shadow effect Word** إلى عدة أشكال داخل حلقة
- تحويل المستند المُحسّن بالظل إلى PDF (`doc.save("output.pdf")`)
- تغيير لون الظل بناءً على تعبئة الشكل (تنسيق ديناميكي)
- استخدام Aspose.Words لإدراج أشكال جديدة برمجيًا قبل تطبيق الظلال

كل من هذه الإضافات يبني على نفس مفاهيم API، لذا ستجد منحنى التعلم سهلًا.

## الخلاصة

لقد غطينا كل ما تحتاجه لـ **add shadow to shape** في ملف Word باستخدام Python: تحميل المستند، تحديد الشكل، ضبط معلمات الظل، وحفظ النتيجة. السكريبت الكامل أعلاه جاهز للإدراج في أي خط أنابيب أتمتة، وتساعدك النصائح الإضافية على **apply shadow effect Word** المستندات في سيناريوهات أكثر تعقيدًا.

جرّبه، عدّل قيم الضبابية والشفافية، وشاهد كيف يمكن لظل صغير أن يُحدث فرقًا بصريًا كبيرًا. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [دورة تعليمية حول ظل شكل Aspose.Words – إضافة ظل إلى شكل Word في C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [إنشاء شكل مستطيل في Word باستخدام Aspose.Words – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [إنشاء مستند Word بلغة Java – إضافة شكل مستطيل مع تأثير الظل](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}