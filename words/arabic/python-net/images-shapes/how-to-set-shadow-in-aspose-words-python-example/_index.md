---
category: general
date: 2026-08-01
description: كيفية تعيين الظل على شكل في Word باستخدام Aspose.Words للغة Python. تعلم
  كيفية تغيير الشفافية، وضبط الضبابية، وتغيير مسافة الظل بسرعة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to set shadow
- how to change opacity
- how to adjust blur
- change shadow distance
- how to use aspose.words
language: ar
lastmod: 2026-08-01
og_description: كيفية تعيين الظل على شكل باستخدام Aspose.Words للبايثون. اتبع هذا
  الدليل خطوة بخطوة لتغيير الشفافية، وضبط الضبابية، وتغيير مسافة الظل.
og_image_alt: Screenshot showing how to set shadow on a shape using Aspose.Words in
  Python
og_title: كيفية ضبط الظل في Aspose.Words – دليل سريع للبايثون
schemas:
- author: Aspose
  dateModified: '2026-08-01'
  description: How to set shadow on a Word shape using Aspose.Words for Python. Learn
    to change opacity, adjust blur, and change shadow distance quickly.
  headline: How to Set Shadow in Aspose.Words – Python Example
  type: TechArticle
- description: How to set shadow on a Word shape using Aspose.Words for Python. Learn
    to change opacity, adjust blur, and change shadow distance quickly.
  name: How to Set Shadow in Aspose.Words – Python Example
  steps:
  - name: '**Create the document** (or load a template).'
    text: '**Create the document** (or load a template).'
  - name: '**Insert the logo shape** (via `DocumentBuilder.insert_image` or `Shape`).'
    text: '**Insert the logo shape** (via `DocumentBuilder.insert_image` or `Shape`).'
  - name: '**Call `apply_shadow`** with your brand’s shadow specs.'
    text: '**Call `apply_shadow`** with your brand’s shadow specs.'
  - name: '**Export** to DOCX, PDF, or HTML with a single line of code.'
    text: '**Export** to DOCX, PDF, or HTML with a single line of code.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Shadow Formatting
- Word Automation
title: كيفية تعيين الظل في Aspose.Words – مثال بايثون
url: /ar/python/images-shapes/how-to-set-shadow-in-aspose-words-python-example/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تعيين الظل في Aspose.Words – مثال Python

هل تساءلت يومًا **كيف يتم تعيين الظل** على شكل Word دون فتح المستند يدويًا؟ لست وحدك—الكثير من المطورين يواجهون هذه المشكلة عند أتمتة التقارير أو إنشاء قوالب متسقة مع العلامة التجارية. الخبر السار؟ مع Aspose.Words for Python يمكنك تعديل ظل الشكل، الشفافية، الضبابية، والمسافة ببضع أسطر من الشيفرة فقط.

في هذا الدرس سنستعرض مثالًا كاملاً وقابلًا للتنفيذ يوضح **كيفية تعيين الظل**، **كيفية تغيير الشفافية**، **كيفية تعديل الضبابية**، وحتى **تغيير مسافة الظل**. بنهاية الدرس ستحصل على فهم قوي **كيفية استخدام Aspose.Words** لتنسيق الأشكال برمجيًا.

---

![How to set shadow on a shape using Aspose.Words](image-placeholder.png){alt="كيفية تعيين الظل على شكل باستخدام Aspose.Words"}

## المتطلبات المسبقة

قبل أن نبدأ، تأكد من وجود ما يلي:

| المتطلب | السبب |
|-------------|--------|
| Python 3.8+ | بنية حديثة، تلميحات نوع |
| حزمة `aspose-words` (pip install aspose-words) | المكتبة الأساسية لمعالجة Word |
| ملف `input.docx` تجريبي يحتوي على شكل واحد على الأقل | الشكل الذي سنضيف له الظل |
| صلاحية كتابة في المجلد الذي ستحفظ فيه `output.docx` | لحفظ التغييرات |

لا حاجة إلى ملفات DLL إضافية أو COM interop—Aspose.Words مكتبة Python صافية، لذا يمكنك تشغيلها على Windows أو macOS أو Linux.

---

## كيفية تعيين الظل على شكل باستخدام Aspose.Words

فيما يلي **النص الكامل** للسكريبت. يقوم بتحميل المستند، العثور على أول شكل (بشكل متكرر)، ضبط الظل، ثم حفظ النتيجة. كل سطر مشروح لتفهم **لماذا** هو موجود، وليس فقط **ماذا** يفعل.

```python
# ------------------------------------------------------------
# How to Set Shadow – Full Python Example using Aspose.Words
# ------------------------------------------------------------
import aspose.words as aw  # Import the Aspose.Words namespace

def apply_shadow(
    input_path: str,
    output_path: str,
    distance: int = 5,
    blur: float = 4.0,
    opacity: float = 0.6
) -> None:
    """
    Demonstrates how to set shadow on the first shape in a Word document.
    
    Parameters
    ----------
    input_path : str
        Path to the source .docx file.
    output_path : str
        Path where the modified .docx will be saved.
    distance : int, optional
        How far the shadow is offset from the shape (default = 5 points).
    blur : float, optional
        Blur radius of the shadow (default = 4.0 points).
    opacity : float, optional
        Opacity of the shadow (0 = fully transparent, 1 = fully opaque).
    """
    # Step 1: Load the Word document
    doc = aw.Document(input_path)

    # Step 2: Retrieve the first shape in the document (searches recursively)
    # The `True` flag makes the search go deep into headers, footers, and groups.
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

    if shape is None:
        raise ValueError("No shape found in the document. Add a shape and try again.")

    # Step 3: Configure the shadow appearance for the shape
    # ----------------------------------------------------
    # distance → how far the shadow sits away from the shape edge
    # blur     → softness of the shadow edge
    # opacity  → transparency level (0‑1 range)
    shape.shadow_format.distance = distance          # change shadow distance
    shape.shadow_format.blur = blur                  # how to adjust blur
    shape.shadow_format.opacity = opacity            # how to change opacity

    # Optional: tweak color and style if you need more control
    shape.shadow_format.color = aw.Color.black
    shape.shadow_format.style = aw.ShadowStyle.OUTER_SHADOW

    # Step 4: Save the modified document
    doc.save(output_path)

# -----------------------------------------------------------------
# Example usage – adjust the parameters to see different results
# -----------------------------------------------------------------
if __name__ == "__main__":
    apply_shadow(
        input_path="YOUR_DIRECTORY/input.docx",
        output_path="YOUR_DIRECTORY/output.docx",
        distance=8,       # increase distance for a more pronounced offset
        blur=6.5,         # higher blur makes the shadow softer
        opacity=0.75      # make the shadow a bit more solid
    )
```

### لماذا يعمل هذا

* **`doc.get_child(..., True)`** – العلم `True` يخبر Aspose.Words بالبحث **بشكل متكرر**، لذا حتى الأشكال داخل رؤوس الصفحات، تذييلاتها، أو الكائنات المجمعة يتم العثور عليها. هذا مهم عندما لا تعرف بالضبط مكان وجود الشكل.
* **`shadow_format`** – هذه الخاصية تجمع كل إعدادات الظل. عبر ضبط `distance` و `blur` و `opacity` تتحكم في العمق البصري للشكل. تعديل أي من هذه القيم يوضح **كيفية تغيير الشفافية**، **كيفية تعديل الضبابية**، و**تغيير مسافة الظل** في نداء واحد متكامل.
* **الحفظ** – `doc.save` يكتب ملف `.docx` جديد تمامًا. يبقى الأصلي دون تعديل، وهو نمط آمن للمعالجة الدفعة.

---

## كيفية تغيير شفافية ظل الشكل

تحدد الشفافية مدى وضوح الظل. النطاق من 0.0 (غير مرئي تمامًا) إلى 1.0 (صامد بالكامل). في الشيفرة أعلاه يمكنك ببساطة تعديل معامل `opacity`:

```python
shape.shadow_format.opacity = 0.85  # 85% opaque – looks richer on dark backgrounds
```

> **نصيحة محترف:** عند توليد ملفات PDF لاحقًا، غالبًا ما تُترجم الشفافية العالية إلى ظل أعمق وأكثر قابلية للطباعة. جرب القيم بين 0.4 و 0.9 لتجد النقطة المثالية وفقًا لإرشادات علامتك التجارية.

---

## كيفية تعديل الضبابية للحصول على مظهر ناعم

الضبابية هي نصف قطر الضباب Gaussian المطبق على حواف الظل. كلما ارتفعت القيمة، يصبح التأثير أكثر نعومة:

```python
shape.shadow_format.blur = 10.0  # Very soft, almost hazy shadow
```

إذا كنت تحتاج إلى مظهر ظل حاد (مثل أسلوب “Microsoft PowerPoint”)، اضبط `blur` على قيمة منخفضة مثل `1.0`.

---

## تغيير مسافة الظل لإنشاء عمق

المسافة تُقاس بالنقاط (1 pt = 1/72 in). كلما زادت المسافة بين الظل والشكل، يبدو الشكل وكأنه يطفو أعلى:

```python
shape.shadow_format.distance = 12  # Shadow shifts 12 pt away from the shape
```

اجمع مسافة `distance` أكبر مع ضبابية `blur` معتدلة للحصول على تأثير درامي “مرفوع”.

---

## تجميع كل شيء – مشروع صغير

تخيل أنك تبني مولد تقارير آلي يدرج شعار الشركة داخل مربع نص. تريد أن يكون لكل شعار ظل خفيف يتماشى مع النمط المؤسسي. باستخدام الدالة `apply_shadow` يمكنك:

1. **إنشاء المستند** (أو تحميل قالب).
2. **إدراج شكل الشعار** (عن طريق `DocumentBuilder.insert_image` أو `Shape`).
3. **استدعاء `apply_shadow`** مع مواصفات الظل الخاصة بعلامتك.
4. **تصدير** إلى DOCX أو PDF أو HTML بسطر واحد من الشيفرة.

نظرًا لأن الدالة تقبل معلمات، يمكنك تخزين إعدادات الظل في ملف JSON وتطبيقها على عشرات المستندات—دون الحاجة إلى تعديل يدوي.

---

## أسئلة شائعة وحالات خاصة

| السؤال | الجواب |
|----------|--------|
| **ماذا لو كان المستند يحتوي على أشكال متعددة؟** | المثال يستهدف *أول* شكل. لتأثير جميع الأشكال، استخدم حلقة مع `doc.get_child_nodes(aw.NodeType.SHAPE, True)` وطبق إعدادات `shadow_format` نفسها على كل عقدة. |
| **هل يمكنني تعيين لون ظل مختلف؟** | بالتأكيد. استخدم `shape.shadow_format.color = aw.Color(255, 0, 0)` للحصول على ظل أحمر، أو أي `aw.Color` تفضله. |
| **هل تبقى هذه الإعدادات بعد التحويل إلى PDF؟** | نعم. Aspose.Words يحافظ على خصائص الظل عند التحويل إلى PDF، رغم أن قيم الضبابية العالية قد تُقرب. |
| **هل هناك تأثير على الأداء في المستندات الكبيرة؟** | واجهة برمجة الظل تتعامل فقط مع كائنات الشكل، لذا حتى تقريرًا من 500 صفحة يُعالج في مليثانية. عنق الزجاجة عادةً هو I/O، وليس ضبط الظل. |
| **هل يمكن إزالة الظل لاحقًا؟** | اضبط `shape.shadow_format.is_visible = False` أو أعد تعيين الخصائص إلى القيم الافتراضية. |

---

## ملخص المثال الكامل العامل

إليك السكريبت بالكامل مرة أخرى، بدون تعليقات لتسهيل النسخ واللصق السريع:

```python
import aspose.words as aw

def apply_shadow(input_path, output_path, distance=5, blur=4.0, opacity=0.6):
    doc = aw.Document(input_path)
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
    if shape is None:
        raise ValueError("No shape found.")
    shape.shadow_format.distance = distance
    shape.shadow_format.blur = blur
    shape.shadow_format.opacity = opacity
    shape.shadow_format.color = aw.Color.black
    shape.shadow_format.style = aw.ShadowStyle.OUTER_SHADOW
    doc.save(output_path)

if __name__ == "__main__":
    apply_shadow(
        "YOUR_DIRECTORY/input.docx",
        "YOUR_DIRECTORY/output.docx",
        distance=8,
        blur=6.5,
        opacity=0.75
    )
```

شغّل السكريبت، افتح `output.docx`، وسترى الشكل يحمل ظلًا أنيقًا يتطابق مع المعلمات التي ضبطتها.

---

## الخاتمة

لقد غطينا **

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك الخاصة.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [How to Implement Comments and Replies in Word Documents using Aspose.Words for Python](/words/english/python-net/annotations-comments/aspose-words-python-comments-replies/)
- [How to Manage Document Variables with Aspose.Words in Python: A Complete Guide](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}