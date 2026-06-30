---
category: general
date: 2026-06-30
description: كيفية إعادة تسمية الصور أثناء تحويل DOCX إلى markdown. تعلّم تغيير أسماء
  الصور وحفظ ملف Word كـ markdown بأسماء ملفات صور مخصصة.
draft: false
keywords:
- how to rename images
- convert docx to markdown
- change image names
- save word as markdown
- custom image filenames
language: ar
og_description: كيفية إعادة تسمية الصور أثناء تحويل DOCX إلى markdown. يوضح لك هذا
  الدليل كيفية تغيير أسماء الصور، حفظ Word كـ markdown، واستخدام أسماء ملفات صور مخصصة.
og_title: كيفية إعادة تسمية الصور عند تحويل DOCX إلى Markdown
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: How to rename images while converting DOCX to markdown. Learn to change
    image names and save Word as markdown with custom image filenames.
  headline: How to Rename Images When Converting DOCX to Markdown
  type: TechArticle
- description: How to rename images while converting DOCX to markdown. Learn to change
    image names and save Word as markdown with custom image filenames.
  name: How to Rename Images When Converting DOCX to Markdown
  steps:
  - name: Why Use a GUID?
    text: '* **Uniqueness** – A GUID (`uuid4`) guarantees that two images will never
      clash, even across multiple runs. * **Traceability** – If you need to debug
      later, the GUID can be logged alongside the original Word paragraph number.
      * **Portability** – No reliance on the original Word naming scheme, which '
  - name: Expected Output (excerpt)
    text: '```markdown # Sample Document'
  - name: What if the document contains non‑image resources?
    text: Our callback already checks the file extension and returns `True` for anything
      that isn’t an image. This means CSS files, fonts, or embedded OLE objects keep
      their original names, which is usually what you want when you **save word as
      markdown**.
  - name: Can I use a custom naming scheme instead of GUIDs?
    text: 'Absolutely. Replace the `uuid.uuid4()` call with any function that returns
      a string. For example, you could prepend the original paragraph index:'
  - name: How does this affect performance on large documents?
    text: The callback runs once per resource, so the overhead is minimal—mostly the
      time to generate a GUID. Even a 200‑page report with dozens of images finishes
      in under a second on a modern laptop.
  - name: What if I need the image filenames to be deterministic (e.g., for CI builds)?
    text: 'Swap `uuid.uuid4()` for a hash of the original image bytes:'
  type: HowTo
tags:
- Aspose.Words
- Python
- Markdown
- Image Processing
title: كيفية إعادة تسمية الصور عند تحويل DOCX إلى Markdown
url: /ar/python/document-conversion/how-to-rename-images-when-converting-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إعادة تسمية الصور عند تحويل DOCX إلى Markdown

هل تساءلت يومًا **عن كيفية إعادة تسمية الصور** تلقائيًا عند تحويل ملف DOCX إلى Markdown؟ لست وحدك. في العديد من خطوط توثيق المستندات تصبح أسماء الصور الافتراضية (مثل `image1.png`) كابوسًا لتتبعها، خاصةً عندما يتم التحكم في نسخة الـ markdown نفسها عبر الفرق.  

الخبر السار هو أن Aspose.Words for Python يجعل من السهل **تغيير أسماء الصور** أثناء العملية، ويمكنك الحفاظ على نظافة ملف الـ Markdown مع الحفاظ على مجلد من الأصول ذات الأسماء المخصصة.  

في هذا الدرس ستتعلم كيفية:

* تحميل مستند Word (`.docx`) في Python.  
* ربط عملية حفظ الـ Markdown بدالة رد نداء (callback) تُعطي كل صورة اسمًا يعتمد على GUID.  
* حفظ المستند كـ Markdown بحيث يشير الملف المُولد إلى الصور التي أُعيد تسميتها.  

إذا كنت مرتاحًا مع أساسيات Python ولديك Aspose.Words مثبتًا، فستكون جاهزًا للعمل خلال أقل من خمس دقائق. لا سكريبتات خارجية، لا إعادة تسمية يدوية—فقط برنامج واحد مستقل يقوم بكل العمل الشاق نيابةً عنك.

---

## المتطلبات المسبقة — ما تحتاجه قبل البدء

| المتطلب | لماذا هو مهم |
|-------------|----------------|
| **Python 3.7+** | يستخدم المثال f‑strings وتلميحات الأنواع التي تم تقديمها في 3.6، لكن 3.7+ يوفّر لك وظائف `os.path.splitext` المريحة. |
| **Aspose.Words for Python via .NET** (`pip install aspose-words`) | هذه المكتبة توفر الفئة `aw.Document` و`MarkdownSaveOptions` التي نعتمد عليها. |
| **إذن كتابة** إلى مجلد الإخراج | سيقوم رد النداء بإنشاء ملفات صور جديدة، لذا يجب أن يُسمح للسكريبت بكتابتها. |
| **ملف DOCX** تريد تحويله | أي شيء من تقرير بسيط إلى دليل معقد سيعمل. |

> **نصيحة احترافية:** إذا كنت تستخدم بيئة افتراضية، فعّلها قبل تثبيت Aspose.Words. فهي تعزل الاعتمادات وتجنب تضارب الإصدارات.

---

## الخطوة 1: تحميل مستند Word  

أول شيء تقوم به عندما تريد **تحويل docx إلى markdown** هو فتح الملف المصدر. Aspose.Words يخفّف عنك كل التعامل منخفض المستوى مع OPC، لذا سطر واحد يكفي للقيام بالمهمة.

```python
import aspose.words as aw

# Replace YOUR_DIRECTORY with the folder that holds your .docx file
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

*لماذا هذا مهم:* بدون تحميل المستند لا يمكنك فحص موارده، ولن يكون لدى مُصدّر الـ Markdown ما يكتبه. كائن `aw.Document` يحمل حزمة Word بالكامل في الذاكرة، مما يجعل من الآمن تعديلها قبل الحفظ.

---

## الخطوة 2: كتابة رد نداء **يعيد تسمية موارد الصور**  

Aspose.Words يتيح لك توصيل `resource_saving_callback` إلى `MarkdownSaveOptions`. يتلقى رد النداء كل مورد (صور، CSS، إلخ) قبل كتابته إلى القرص. من خلال تعديل `resource.file_name` يمكننا فرض **أسماء صور مخصصة**.

```python
def rename_image_resource(resource):
    """
    Rename image resources with a unique GUID before saving.
    This is where we implement how to rename images.
    """
    import uuid, os

    # Guard: only process image resources, ignore CSS or other files
    if not resource.file_name.lower().endswith(('.png', '.jpg', '.jpeg', '.gif', '.bmp')):
        return True  # Let Aspose handle non‑image resources unchanged

    # Extract the original extension so we keep PNG as PNG, JPG as JPG, etc.
    _, ext = os.path.splitext(resource.file_name)

    # Generate a globally unique identifier and tack the original extension on
    new_name = f"{uuid.uuid4()}{ext}"
    resource.file_name = new_name

    # Returning True tells Aspose to proceed with the default saving logic
    return True
```

### لماذا نستخدم GUID؟

* **Uniqueness** – GUID (`uuid4`) يضمن أن صورتين لن تتصادما أبدًا، حتى عبر تشغيلات متعددة.  
* **Traceability** – إذا احتجت إلى تتبع الأخطاء لاحقًا، يمكن تسجيل GUID جنبًا إلى جنب مع رقم الفقرة الأصلي في Word.  
* **Portability** – لا يعتمد على نظام تسمية Word الأصلي، الذي قد يحتوي على مسافات أو أحرف خاصة تُعطّل روابط Markdown.

---

## الخطوة 3: ربط رد النداء بخيارات حفظ Markdown  

الآن نخبر Aspose باستخدام منطق إعادة التسمية كلما كتب صورة إلى مجلد الإخراج.

```python
md_options = aw.saving.MarkdownSaveOptions()
md_options.resource_saving_callback = rename_image_resource

# Optional: control where images are placed relative to the markdown file
md_options.images_folder = "images"  # creates a sub‑folder called 'images'
```

*شرح:* فئة `MarkdownSaveOptions` تتحكم في كل شيء من فواصل الأسطر إلى موقع مجلد الصور. عبر تعيين `resource_saving_callback` تحصل على **نقطة ربط** تُنفّذ لكل مورد مضمّن، مما يتيح لك **تغيير أسماء الصور** قبل أن تُكتب على القرص.

---

## الخطوة 4: حفظ المستند كـ Markdown – القطعة النهائية  

مع وجود رد النداء، تصبح الخطوة الأخيرة بسيطة.

```python
output_path = "YOUR_DIRECTORY/CustomResources.md"
doc.save(output_path, md_options)
print(f"Markdown saved to {output_path}")
```

عند انتهاء السكريبت، ستجد:

* `CustomResources.md` – تمثيل الـ Markdown لملف Word الخاص بك.  
* مجلد `images/` (أو أي اسم حددته) يحتوي على ملفات مثل `d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e.png`.  

ملف الـ Markdown سيشير إلى أسماء الملفات الجديدة المعتمدة على GUID، لذا أي معالج لاحق (GitHub، MkDocs، إلخ) سيستقبل الصور الصحيحة دون الحاجة لإعادة تسميتها يدويًا.

### النتيجة المتوقعة (مقتطف)

```markdown
# Sample Document

Here is an image that was originally called `image1.png` in the DOCX:

![d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e](images/d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e.png)

And another one:

![a1b2c3d4-e5f6-7a8b-9c0d-e1f2a3b4c5d6](images/a1b2c3d4-e5f6-7a8b-9c0d-e1f2a3b4c5d6.jpg)
```

ستختلف GUIDs في كل تشغيل، لكن النمط يبقى نفسه.

---

## معالجة الحالات الخاصة والأسئلة الشائعة  

### ماذا لو احتوى المستند على موارد غير صور؟  

رد النداء الخاص بنا يتحقق بالفعل من امتداد الملف ويُعيد `True` لأي شيء ليس صورة. هذا يعني أن ملفات CSS، الخطوط، أو كائنات OLE المضمّنة تحتفظ بأسمائها الأصلية، وهو ما تريده عادةً عندما **تحفظ word كـ markdown**.

### هل يمكنني استخدام نظام تسمية مخصص بدلاً من GUIDs؟  

بالطبع. استبدل استدعاء `uuid.uuid4()` بأي دالة تُعيد سلسلة. على سبيل المثال، يمكنك إلحاق فهرس الفقرة الأصلي:

```python
new_name = f"para{resource.resource_id}{ext}"
```

فقط تأكد أن الاسم الناتج فريد عبر المستند بأكمله.

### كيف يؤثر هذا على الأداء في المستندات الكبيرة؟  

رد النداء يُنفّذ مرة واحدة لكل مورد، لذا فإن الحمل الإضافي ضئيل—معظم الوقت يُقضى في توليد GUID. حتى تقريرًا من 200 صفحة يحتوي على عشرات الصور يكتمل في أقل من ثانية على حاسوب محمول حديث.

### ماذا لو احتجت إلى أسماء صور حتمية (مثلاً لبُنى CI)؟  

استبدل `uuid.uuid4()` بعملية تجزئة (hash) لبايتات الصورة الأصلية:

```python
import hashlib
hash = hashlib.sha256(resource.raw_bytes).hexdigest()[:12]
new_name = f"{hash}{ext}"
```

هذا يُنتج نفس اسم الملف في كل مرة تُشغّل فيها السكريبت على نفس الصورة المصدر.

---

## سكريبت كامل يعمل – انسخ، الصق، شغّل  



## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة‑بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك الخاصة.

- [حفظ docx كـ markdown – دليل C# كامل مع استخراج الصور](/words/english/net/programming-with-markdownsaveoptions/save-docx-as-markdown-full-c-guide-with-image-extraction/)
- [كيفية حفظ Markdown من DOCX – دليل خطوة‑بخطوة](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}