---
category: general
date: 2026-05-04
description: تعلم كيفية تضمين الصور في Markdown عند تحويل DOCX إلى markdown باستخدام
  Python و Aspose.Words. كما يمكنك الاطلاع على كيفية استعادة ملفات DOCX التالفة.
draft: false
keywords:
- how to embed images
- convert docx to markdown
- how to convert docx
- embed images as base64
- recover corrupted docx
language: ar
og_description: تعلم كيفية تضمين الصور في Markdown عند تحويل ملفات DOCX، مع مثال خطوة
  بخطوة بلغة Python ونصائح لاستعادة ملفات DOCX التالفة.
og_title: كيفية تضمين الصور في ماركداون من DOCX – دليل كامل
tags:
- Aspose.Words
- Python
- Markdown
- DOCX conversion
title: كيفية تضمين الصور في ماركداون من DOCX – دليل كامل
url: /ar/python/document-conversion/how-to-embed-images-in-markdown-from-docx-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تضمين الصور في Markdown من DOCX – دليل كامل

هل تساءلت يومًا **كيفية تضمين الصور** في Markdown أثناء تحويل ملف DOCX؟ يوضح لك هذا الدليل بالضبط **كيفية تضمين الصور** باستخدام Python و Aspose.Words، ويعمل حتى عندما يكون المستند الأصلي متضررًا جزئيًا. سنغطي أيضًا **تحويل docx إلى markdown**، ونشرح **كيفية تحويل docx**، ونظهر **تضمين الصور كـ base64**، ونوضح لك كيفية **استعادة ملفات docx التالفة** دون عناء.

في الدقائق القليلة القادمة ستحصل على سكريبت قابل للتنفيذ، وفهم واضح لأهمية كل سطر، ومجموعة من النصائح العملية التي يمكنك نسخها ولصقها في مشاريعك. لا تبعيات مخفية، ولا اختصارات غامضة مثل “انظر إلى الوثائق”—فقط حل متكامل من البداية إلى النهاية.

---

## ما ستبنيه

* سكريبت Python يقوم بتحميل ملف DOCX (حتى إذا كان تالفًا) باستخدام Aspose.Words.
* رد نداء مخصص (callback) يحول كل صورة مدمجة إلى URI بيانات **Base64**، مما يجيب فعليًا على سؤال **كيفية تضمين الصور** مباشرة داخل ملف Markdown.
* ملف Markdown تُظهر فيه المعادلات بصيغة LaTeX، وتتحول الأشكال العائمة إلى وسوم داخلية، وتُضمن جميع الصور بأمان داخل النص.
* قائمة مراجعة قصيرة لتصحيح الأخطاء الشائعة عند **تحويل docx إلى markdown**.

---

## المتطلبات

| المتطلبات | لماذا يهم |
|-------------|----------------|
| Python 3.8+ | مطلوب لحزمة `aspose.words`. |
| `aspose-words` pip package | توفر مساحة الاسم `aw` المستخدمة في جميع أنحاء الكود. |
| ملف DOCX (أي حجم) | المصدر الذي ستقوم بتحويله. |
| اختياري: DOCX تالف | لاختبار مسار **استعادة docx التالف**. |

ثبت المكتبة باستخدام:

```bash
pip install aspose-words
```

---

## إعداد البيئة

قبل أن نغوص في عملية التحويل الفعلية، تأكد من أن بيئتك يمكنها العثور على تجميع Aspose.Words. إذا كنت تستخدم بيئة افتراضية، فعّلها أولاً:

```bash
# Activate your venv (Linux/macOS)
source venv/bin/activate

# Or on Windows
venv\Scripts\activate
```

الآن استورد الوحدات التي سنحتاجها. لاحظ استيراد `base64` – فهو قلب **تضمين الصور كـ base64**.

```python
# Step 1: Import Aspose.Words and base64 for encoding image data
import aspose.words as aw
import base64
```

> **نصيحة احترافية:** إذا حصلت على خطأ `ModuleNotFoundError`، تحقق مرة أخرى من أنك قمت بتثبيت `aspose-words` داخل نفس البيئة الافتراضية التي تشغل منها السكريبت.

---

## كتابة رد نداء تضمين الصورة

تتيح لك Aspose.Words ربط عملية الحفظ عبر *رد نداء حفظ الموارد*. هنا نجيب على **كيفية تضمين الصور** بتحويل الحمولة الثنائية إلى سلسلة URI بيانات.

```python
# Step 2: Define a callback that converts embedded images to Base64 data URIs
def embed_images(resource):
    # We only care about images; other resources (like CSS) are ignored.
    if resource.resource_type == aw.saving.MarkdownResourceType.IMAGE:
        # Build a data URI: data:<mime_type>;base64,<encoded_bytes>
        data_uri = f"data:{resource.mime_type};base64,{base64.b64encode(resource.bytes).decode()}"
        # Return a tuple (name, bytes) – the name is used as the image reference.
        return (resource.name, data_uri.encode())
    # Returning None tells Aspose to skip this resource.
    return None
```

**لماذا يعمل هذا:** خاصية `resource.bytes` تحتفظ ببايتات الصورة الخام. `base64.b64encode` يحول تلك البايتات إلى سلسلة ASCII، ونضيف نوع MIME مسبقًا حتى تعرف المتصفحات كيفية عرض الصورة. النتيجة هي ملف Markdown مستقل لا يحتوي على ملفات صور خارجية – تمامًا ما يعد به **تضمين الصور كـ base64**.

---

## تحميل DOCX بوضع الاستعادة

أحد أكثر المشكلات شيوعًا هو التعامل مع ملفات Word المتضررة جزئيًا. توفر Aspose.Words *وضع الاستعادة* الذي يحاول إنقاذ ما يمكن. هذا يلبي متطلب **استعادة docx التالف**.

```python
# Step 3: Load the source DOCX document with recovery mode enabled
load_options = aw.LoadOptions()
load_options.recovery_mode = aw.LoadOptions.RecoveryMode.RECOVER  # Attempts to fix broken parts
doc = aw.Document("YOUR_DIRECTORY/input.docx", load_options)
```

إذا كان الملف سليمًا، يكون وضع الاستعادة شبه خالٍ من أي عبء. إذا كان تالفًا، سيتخطى Aspose الأجزاء غير القابلة للقراءة مع الاستمرار في تقديم كائن مستند قابل للاستخدام.

---

## تكوين خيارات تصدير Markdown

الآن نخبر Aspose بالضبط كيف نريد أن يبدو ناتج Markdown. هناك إعدادان حاسمان للحصول على نتيجة نظيفة:

* `office_math_export_mode = LATEX` – يحول معادلات Word إلى LaTeX، والتي يفهمها معظم عارضات Markdown.
* `export_floating_shapes_as_inline_tag = True` – يجبر الصور العائمة على التصرف كصور داخلية، مما يجعل الملف النهائي يبدو أشبه بعرض PDF.

```python
# Step 4: Configure Markdown export options
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.office_math_export_mode = aw.saving.MarkdownOfficeMathExportMode.LATEX
markdown_options.resource_saving_callback = embed_images      # Hook we defined earlier
markdown_options.export_floating_shapes_as_inline_tag = True
```

---

## حفظ ملف Markdown

مع ربط كل شيء، الخطوة الأخيرة هي سطر واحد يكتب Markdown إلى القرص. سيُستدعى رد النداء الذي قدمناه لكل صورة، محولًا **كيفية تضمين الصور** إلى جزء سلس من خط أنابيب الحفظ.

```python
# Step 5: Save the document as a Markdown file with the configured options
doc.save("YOUR_DIRECTORY/output.md", markdown_options)
print("✅ Conversion complete! Find your Markdown at YOUR_DIRECTORY/output.md")
```

عند فتح `output.md` ستظهر لك شيء مشابه:

```markdown
![image1](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

ذلك السطر هو نتيجة **تضمين الصور كـ base64** – الصورة تعيش بالكامل داخل ملف Markdown، لذا يمكنك توزيع ملف `.md` واحد في أي مكان دون القلق من فقدان الأصول.

---

## التحقق من الناتج واستكشاف الأخطاء

### فحص سريع للمنطقية

1. افتح `output.md` في عارض Markdown (VS Code، Typora، معاينة GitHub، إلخ).
2. تأكد من ظهور جميع الصور بشكل صحيح.
3. ابحث عن كتل LaTeX للمعادلات، على سبيل المثال:

   ```latex
   $$\int_{0}^{\infty} e^{-x^2} dx = \frac{\sqrt{\pi}}{2}$$
   ```

إذا كانت الصور مفقودة، تحقق مرة أخرى من:

* أن ملف DOCX المصدر يحتوي فعليًا على صور.
* أن `resource.mime_type` يتم اكتشافه (نادرًا قد يكون `image/svg+xml`؛ لا يزال Aspose يتعامل معه).

### حالات الحافة الشائعة

| الحالة | ما الذي يجب فعله |
|-----------|------------|
| **DOCX تالف لا يزال يسبب أخطاء** | اضبط `load_options.password` إذا كان الملف محميًا بكلمة مرور، أو حاول فتح الملف في Word وإعادة حفظه. |
| **الصور الكبيرة جدًا تسبب ملفات Markdown ضخمة** | قم بتغيير حجم الصور قبل التحويل أو عدل الـ callback لتقليل الحجم باستخدام Pillow (`PIL.Image`). |
| **You need external image files instead of

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}