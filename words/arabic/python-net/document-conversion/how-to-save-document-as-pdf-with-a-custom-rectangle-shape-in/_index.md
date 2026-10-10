---
category: general
date: 2026-10-07
description: تعرّف على كيفية حفظ المستند كملف PDF مع إضافة شكل مستطيل وظل مخصص باستخدام
  Aspose.Words للغة بايثون. يتضمن الشرح كودًا خطوة بخطوة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save document as pdf
- add rectangle shape
- export word to pdf
- set rectangle dimensions
- draw rectangle word
language: ar
lastmod: 2026-10-07
og_description: احفظ المستند كملف PDF باستخدام شكل مستطيل مخصص باستخدام Aspose.Words
  للبايثون. اتبع المثال الكامل لرسم وتنسيق وتصدير Word إلى PDF.
og_image_alt: Screenshot of the generated PDF showing the rectangle shape after save
  document as pdf
og_title: حفظ المستند كملف PDF مع شكل مستطيل – دليل بايثون الكامل
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  headline: How to save document as PDF with a custom rectangle shape in Python
  type: TechArticle
- description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  name: How to save document as PDF with a custom rectangle shape in Python
  steps:
  - name: Initialize a new blank document
    text: '```python import aspose.words as aw'
  - name: Add rectangle shape to the document
    text: '```python # Create a rectangle shape and attach it to the document. rectangle
      = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)'
  - name: Set rectangle dimensions
    text: '```python # Define width and height in points (1 point = 1/72 inch). rectangle.width
      = 200 # 200 points ≈ 2.78 inches rectangle.height = 100 # 100 points ≈ 1.39
      inches ```'
  - name: (Optional) Apply a visible custom shadow
    text: '```python shadow = rectangle.shadow_format shadow.visible = True # Show
      the shadow shadow.blur = 5.0 # Softness of the shadow edge shadow.distance =
      3.0 # How far the shadow is offset shadow.angle = 45 # Direction in degrees
      shadow.color = aw.drawing.Color.black ```'
  - name: Save document as PDF
    text: '```python output_path = "output/shadow_rectangle.pdf" document.save(output_path)
      print(f"PDF saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Word automation
title: كيفية حفظ المستند كملف PDF مع شكل مستطيل مخصص في بايثون
url: /ar/python/document-conversion/how-to-save-document-as-pdf-with-a-custom-rectangle-shape-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية حفظ المستند كملف PDF مع شكل مستطيل مخصص في بايثون

إذا كنت بحاجة إلى **حفظ المستند كملف PDF** مع إضافة رسومات مخصصة، يوضح لك هذا الدليل كيفية القيام بذلك. سنستعرض إنشاء ملف Word فارغ، **رسم شكل مستطيل**، ضبط حجمه، تطبيق ظل مرئي، وأخيرًا **تصدير Word إلى PDF** باستخدام مكتبة Aspose.Words للبايثون.

سوف تحصل في النهاية على ملف PDF يحتوي على مستطيل موضعه بدقة، جاهز للتقارير، الفواتير، أو أي سيناريو لأتمتة المستندات. لا تحتاج إلى أدوات خارجية—فقط بايثون وحزمة Aspose.Words.

## ما ستحتاجه

| المتطلب | سبب أهميته |
|-------------|----------------|
| Python 3.8+ | تستهدف واجهة Aspose.Words للبايثون إصدارات المفسرات الحديثة. |
| `aspose-words` package (`pip install aspose-words`) | يوفر مساحة الاسم `aw` المستخدمة في أمثلة الشيفرة. |
| الإلمام الأساسي ببايثون والبرمجة الكائنية التوجه | يتعامل الدليل مع كائنات مثل `Document` و `Shape`. |
| صلاحية كتابة في المجلد الذي سيُحفظ فيه ملف PDF | خطوة **حفظ المستند كملف PDF** تكتب ملفًا على القرص. |

> **نصيحة احترافية:** استخدم بيئة افتراضية (`python -m venv venv`) للحفاظ على عزل الاعتمادات.

## كيفية حفظ المستند كملف PDF مع شكل مستطيل

### الخطوة 1: تهيئة مستند فارغ جديد

```python
import aspose.words as aw

# Create an empty Word document – this is the canvas for our shape.
document = aw.Document()
```

إنشاء كائن `Document` جديد يمنحك مجموعة صفحات نظيفة. يمكنك أيضًا تحميل ملف *.docx* موجود إذا رغبت في **تصدير Word إلى PDF** لاحقًا، لكن البدء من الصفر يبقي المثال مركزًا.

### الخطوة 2: إضافة شكل مستطيل إلى المستند

```python
# Create a rectangle shape and attach it to the document.
rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

# The shape must be placed inside a paragraph before it appears.
paragraph = document.first_section.body.first_paragraph
paragraph.append_child(rectangle)
```

تستخدم خطوة `add rectangle shape` القيمة `ShapeType.RECTANGLE`. من خلال إلحاق الشكل بفقرة، يعرف Aspose.Words أين يرسمه في ملف PDF النهائي.

### الخطوة 3: ضبط أبعاد المستطيل

```python
# Define width and height in points (1 point = 1/72 inch).
rectangle.width = 200   # 200 points ≈ 2.78 inches
rectangle.height = 100  # 100 points ≈ 1.39 inches
```

ضبط **أبعاد المستطيل** بشكل صريح يضمن أن الشكل يبدو متسقًا عبر المنصات. يمكنك أيضًا استخدام المساعدات `convert_to_inches` إذا كنت تفضل الوحدات الإمبراطورية.

### الخطوة 4: (اختياري) تطبيق ظل مخصص مرئي

```python
shadow = rectangle.shadow_format
shadow.visible = True          # Show the shadow
shadow.blur = 5.0              # Softness of the shadow edge
shadow.distance = 3.0          # How far the shadow is offset
shadow.angle = 45              # Direction in degrees
shadow.color = aw.drawing.Color.black
```

الظل يجعل المستطيل يبرز في ملف PDF. علم `shadow.visible` ضروري؛ بدون هذا العلم لا تؤثر الخصائص الأخرى.

### الخطوة 5: حفظ المستند كملف PDF

```python
output_path = "output/shadow_rectangle.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

استدعاء `document.save` مع امتداد **.pdf** يحفظ **المستند كملف PDF** تلقائيًا باستخدام محول PDF المدمج في Aspose.Words. لا تحتاج إلى خطوات تحويل إضافية، وهذا هو السبب في أن هذه الطريقة هي الطريقة الموصى بها لـ **تصدير Word إلى PDF**.

> **لماذا يعمل هذا:**  
> يقوم Aspose.Words بكتابة تخطيط المستند، بما في ذلك المستطيل وظله، مباشرةً إلى تدفق PDF. العملية لا تفقد الجودة وتحافظ على جودة المتجهات.

## الكود الكامل (سكريبت واحد)

```python
import aspose.words as aw

def create_pdf_with_rectangle(output_path: str):
    """
    Creates a PDF that contains a single rectangle shape with a custom shadow.
    The function demonstrates:
    • add rectangle shape
    • set rectangle dimensions
    • export Word to PDF (save document as pdf)
    """
    # 1️⃣ Create a new blank document
    document = aw.Document()

    # 2️⃣ Insert a rectangle shape
    rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

    # 3️⃣ Set the shape's size
    rectangle.width = 200   # points
    rectangle.height = 100  # points

    # 4️⃣ Configure a visible shadow
    shadow = rectangle.shadow_format
    shadow.visible = True
    shadow.blur = 5.0
    shadow.distance = 3.0
    shadow.angle = 45
    shadow.color = aw.drawing.Color.black

    # 5️⃣ Add shape to the first paragraph
    paragraph = document.first_section.body.first_paragraph
    paragraph.append_child(rectangle)

    # 6️⃣ Save the document as PDF
    document.save(output_path)
    print(f"PDF successfully saved to: {output_path}")

if __name__ == "__main__":
    create_pdf_with_rectangle("output/shadow_rectangle.pdf")
```

تشغيل هذا السكريبت ينتج ملف `shadow_rectangle.pdf` الذي يبدو هكذا:

![مخطط للملف PDF المُولد يُظهر شكل المستطيل بعد حفظ المستند كملف PDF](placeholder-image.png)

*يحتوي ملف PDF على صفحة واحدة مع مستطيل ذو ظل أسود مركّز في المستند.*

## الأسئلة الشائعة والحالات الخاصة

| السؤال | الإجابة |
|----------|--------|
| **هل يمكنني وضع المستطيل في موقع محدد؟** | نعم. اضبط `rectangle.left` و `rectangle.top` (بالنقاط) قبل الحفظ. |
| **ماذا لو احتجت إلى أشكال متعددة؟** | أنشئ كائنات `Shape` إضافية، اضبط كل واحدة، وألحقها بالفقرة نفسها أو فقرات مختلفة. |
| **هل يؤثر الظل على حجم ملف PDF؟** | تأثيره طفيف فقط؛ يُخزن الظل كبيانات متجهة، وليس كصورة نقطية. |
| **هل يمكنني استخدام هذا لتحويل ملفات *.docx* موجودة؟** | بالتأكيد. استبدل `aw.Document()` بـ `aw.Document("input.docx")` وستبقى باقي الخطوات دون تغيير. |
| **هل هناك طريقة لتغيير لون تعبئة المستطيل؟** | اضبط `rectangle.fill_color = aw.drawing.Color.light_blue` (أو أي `Color` تفضله). |

## الخطوات التالية

الآن بعد أن عرفت كيفية **حفظ المستند كملف PDF** مع مستطيل مخصص، قد ترغب في استكشاف:

* **تصدير Word إلى PDF** مع رؤوس وتذييلات وأرقام صفحات.  
* **إضافة كائنات رسم أخرى** (`Ellipse`, `Polygon`) باستخدام نفس فئة `Shape`.  
* **معالجة دفعة** لمجلد من ملفات Word، وتطبيق نفس طبقة المستطيل على كل ملف.  

تتبع هذه الإضافات نفس النمط: إنشاء شكل، ضبط خصائصه، و **حفظ المستند كملف PDF**.

---

**الملخص:** يوضح لك هذا الدليل كيفية **حفظ المستند كملف PDF** مع **إضافة شكل مستطيل**، **ضبط أبعاد المستطيل**، وتطبيق ظل مخصص باستخدام Aspose.Words للبايثون. الكود الكامل جاهز للنسخ، التشغيل، وتكييفه مع خطوط أتمتة المستندات الخاصة بك. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء شكل مستطيل، إضافة ظل وحفظ PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [إضافة مستطيل إلى PDF باستخدام Aspose.Words – دليل خطوة بخطوة](/words/english/python-net/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/)
- [حفظ المستند كملف PDF باستخدام Aspose.Words – دليل C# كامل](/words/english/net/programming-with-pdfsaveoptions/save-document-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}