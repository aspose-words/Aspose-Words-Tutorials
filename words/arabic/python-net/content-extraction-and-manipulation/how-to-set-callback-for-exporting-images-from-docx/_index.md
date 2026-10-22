---
category: general
date: 2026-06-24
description: كيفية تعيين رد نداء لتصدير الصور من ملف DOCX عند حفظه كملف Markdown.
  تعلّم كيفية استخراج الصور، استخراج SVG من Word، وحفظ ملف DOCX كـ Markdown مع معالجة
  مخصصة.
draft: false
keywords:
- how to set callback
- export images from docx
- how to extract images
- save docx as markdown
- extract svg from word
language: ar
og_description: كيفية تعيين رد الاتصال لتصدير الصور من DOCX عند التحويل إلى Markdown.
  يوضح هذا الدليل كيفية استخراج الصور وملفات SVG بكفاءة.
og_title: كيفية تعيين رد الاتصال لتصدير الصور من DOCX
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  headline: How to Set Callback for Exporting Images from DOCX
  type: TechArticle
- description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  name: How to Set Callback for Exporting Images from DOCX
  steps:
  - name: '**Deterministic names** – useful for version control or CDN publishing.'
    text: '**Deterministic names** – useful for version control or CDN publishing.'
  - name: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
    text: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
  - name: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
    text: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Conversion
title: كيفية تعيين رد النداء لتصدير الصور من DOCX
url: /ar/python/content-extraction-and-manipulation/how-to-set-callback-for-exporting-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تعيين رد نداء لتصدير الصور من DOCX

هل تساءلت يومًا **كيفية تعيين رد نداء** حتى تتمكن من **تصدير الصور من DOCX** أثناء تحويله إلى Markdown؟ لست وحدك. يواجه العديد من المطورين مشكلة عندما تقوم عملية التحويل الافتراضية بإلقاء جميع الصور في مجلد عام أو، والأسوأ، تفقد رسومات SVG تمامًا.  

في هذا الدرس سنستعرض حلًا كاملًا وجاهزًا للتنفيذ يجيب على سؤال “كيفية تعيين رد نداء”، ويظهر **كيفية استخراج الصور**، بل ويغطي **استخراج SVG من Word**. في النهاية ستتمكن من **حفظ DOCX كـ Markdown** باستخدام نظام تسمية مخصص لكل مورد صورة—دون الحاجة لتدخل يدوي.

## ما ستتعلمه

- لماذا يُعد رد النداء أنظف طريقة للتحكم في أسماء ملفات الصور أثناء التحويل.  
- كيفية ربط رد النداء بـ Aspose.Words’s `MarkdownSaveOptions.resource_saving_callback`.  
- كود خطوة بخطوة يستخرج **PNG**، **JPG**، **SVG**، وأي مورد مدمج آخر.  
- نصائح للتعامل مع تصادم الأسماء، الملفات الكبيرة، وخصوصيات المسارات عبر الأنظمة.  

> **نصيحة احترافية:** إذا كنت تستخدم Aspose.Words بالفعل في خط أنابيب أكبر، يمكنك إضافة هذا رد النداء دون تعديل باقي الكود.

![مخطط كيفية تعيين رد النداء](https://example.com/images/how-to-set-callback.png "كيفية تعيين رد النداء")

## المتطلبات المسبقة

- Python 3.8+ (المثال يستخدم f‑strings، لذا 3.6+ يكفي).  
- حزمة `aspose-words` مثبتة (`pip install aspose-words`).  
- ملف DOCX يحتوي على صور نقطية **و** رسومات متجهة (SVG).  
- إلمام أساسي بدوال Python وإدخال/إخراج الملفات.

إذا كان لديك هذه المتطلبات، لنبدأ.

## كيفية تعيين رد نداء لتصدير الصور من DOCX

جوهر الحل يكمن في **رد نداء حفظ الموارد**. تقوم Aspose.Words باستدعاء هذا المفوض لكل صورة أو SVG تريد كتابتها عندما تستدعي `document.save`. بإرجاع زوج `(new_name, data)` تحدد كلًا من اسم الملف ومحتوى البايت.

```python
import aspose.words as aw
import os
import hashlib

# Step 1: Load the source document
document = aw.Document("YOUR_DIRECTORY/input.docx")
```

### لماذا رد نداء؟

بدون رد نداء، تقوم Aspose.Words بإنشاء ملفات مسماة `image1.png`، `image2.svg`، إلخ، وتضعها في مجلد بجوار ملف Markdown. هذا مناسب للعرض السريع، لكن في بيئة الإنتاج غالبًا ما تحتاج إلى:

1. **أسماء حتمية** – مفيدة للتحكم في الإصدارات أو نشر CDN.  
2. **تجنب التصادم** – صورتان بنفس الاسم الأصلي لن تكتبان فوق بعضهما.  
3. **هياكل مجلدات مخصصة** – ربما تريد جميع الأصول تحت `/assets/docs/`.

يمنحك رد النداء التحكم الكامل في هذه الثلاثة مخاوف.

## تصدير الصور من DOCX باستخدام رد نداء الموارد

فيما يلي تنفيذ رد النداء. يقوم بتجزئة البيانات الثنائية لإنتاج لاحقة فريدة، ويحافظ على امتداد الملف الأصلي، ويعيد اسم الملف الجديد مع البايتات الخام.

```python
def resource_callback(resource):
    """
    Called for every image/SVG that MarkdownSaveOptions wants to write.
    Returns a tuple (new_name, data) to control the saved file name.
    """
    # Preserve the original extension (.png, .svg, …)
    extension = os.path.splitext(resource.name)[1]

    # Compute a short hash of the image bytes – guarantees uniqueness
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]

    # Build a deterministic, collision‑free filename
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data
```

#### معالجة الحالات الطرفية

- **ملفات كبيرة:** SHA‑256 يعمل جيدًا لأي حجم؛ يتم حساب التجزئة في الذاكرة، لذا كن حذرًا من قيود الذاكرة إذا كنت تعالج ملفات PDF ضخمة.  
- **امتدادات مفقودة:** قد تخزن بعض ملفات Word القديمة الصور دون امتداد صريح. في هذه الحالة سيكون `extension` فارغًا؛ يمكنك تعيين القيمة الافتراضية إلى `.bin` أو فحص أول بضعة بايتات لتخمين الصيغة.  
- **موارد غير صور:** يتم استدعاء رد النداء لكل مورد خارجي (مثل كائنات OLE). إذا كنت تهتم فقط بالصور/SVGs، قم بالفلترة باستخدام `resource.type` قبل المتابعة.

## كيفية استخراج الصور وSVGs من Word

الآن نربط رد النداء بعملية حفظ Markdown. كائن `MarkdownSaveOptions` يكشف عن الخاصية `resource_saving_callback` لهذا الغرض بالضبط.

```python
# Step 2: Configure Markdown save options to use the callback
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.resource_saving_callback = resource_callback

# Optional: set the folder where images will be placed relative to the .md file
markdown_options.resource_folder = "assets/images"
```

تعيين `resource_folder` اختياري لكنه مفيد في كثير من الأحيان. إذا تركته، ستنتهي الصور بجوار ملف Markdown، مما قد يملأ جذر مشروعك.

### حفظ المستند

```python
# Step 3: Save the document as Markdown, letting the callback store the resources
output_md_path = "YOUR_DIRECTORY/output.md"
document.save(output_md_path, markdown_options)
print(f"Markdown saved to {output_md_path}")
```

عند تشغيل السكريبت، سترى سلسلة من الملفات مثل:

```
assets/images/img_a1b2c3d4e5.png
assets/images/img_f6g7h8i9j0.svg
```

وسيحتوي `output.md` المُولد على روابط صور تشير إلى تلك الأسماء المحددة بالضبط:

```markdown
![Image](assets/images/img_a1b2c3d4e5.png)
```

هذا هو جزء **كيفية استخراج الصور** عمليًا—كل صورة، نقطية أو متجهة، أصبحت الآن أصلًا منفصلًا ومسمىً فريدًا.

## حفظ DOCX كـ Markdown مع معالجة مخصصة للصور

بجمع كل ذلك معًا، إليك السكريبت الكامل الذي يمكنك نسخه‑ولصقه في ملف يُسمى `convert_docx_to_md.py`:

```python
import aspose.words as aw
import os
import hashlib

def resource_callback(resource):
    """Control the naming of each exported image/SVG."""
    extension = os.path.splitext(resource.name)[1] or ".bin"
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data

def convert_docx_to_markdown(input_path, output_md_path, image_folder="assets/images"):
    # Load the DOCX
    document = aw.Document(input_path)

    # Set up Markdown options with our callback
    md_options = aw.saving.MarkdownSaveOptions()
    md_options.resource_saving_callback = resource_callback
    md_options.resource_folder = image_folder

    # Ensure the output directory exists
    os.makedirs(os.path.dirname(output_md_path), exist_ok=True)
    os.makedirs(os.path.join(os.path.dirname(output_md_path), image_folder), exist_ok=True)

    # Perform the conversion
    document.save(output_md_path, md_options)
    print(f"✅ Conversion complete! Markdown at: {output_md_path}")

if __name__ == "__main__":
    # Adjust these paths to your environment
    INPUT_DOCX = "YOUR_DIRECTORY/input.docx"
    OUTPUT_MD = "YOUR_DIRECTORY/output.md"
    convert_docx_to_markdown(INPUT_DOCX, OUTPUT_MD)
```

**لماذا يعمل هذا:**  
- `resource_callback` يضمن أن كل صورة تحصل على اسم فريد وقابل لإعادة الإنتاج.  
- `resource_folder` يحافظ على نظافة Markdown عبر فصل الأصول.  
- استدعاءات `os.makedirs` تحميك من أخطاء “المجلد غير موجود” عندما يُشغل السكريبت على جهاز جديد.

## استخراج SVG من Word – ماذا عن الرسومات المتجهة؟

تُعامل SVGs بنفس طريقة PNGs بواسطة رد النداء لأنها مجرد `resource` أخرى. الفارق الوحيد هو أن بعض إصدارات Word القديمة تُضمّن SVGs ككائنات *OfficeArt*، والتي تقوم Aspose.Words بتحويلها تلقائيًا إلى PNG نقطي ما لم تقم بتمكين علم **preserve SVG** صراحةً:

```python
md_options.export_svg = True  # Keep original SVG markup
```

أضف هذا السطر قبل الحفظ، وسيتلقى رد النداء موارد بامتداد `.svg`، مما يحافظ على بيانات المتجهات الواضحة—مثالي للوثائق الويب المتجاوبة.

## أسئلة شائعة ومشكلات محتملة

| السؤال | الإجابة |
|----------|--------|
| **ماذا لو كانت صورتان متطابقتان؟** | ستكون قيمة تجزئة SHA‑256 متطابقة، وبالتالي ستتصادم أسماء الملفات. إذا كنت بحاجة إلى النسختين، أدرج `resource.name` الأصلي في حساب التجزئة (مثال: `hash(resource.name + resource.data)`). |
| **هل يمكنني تغيير المجلد حسب نوع الملف؟** | نعم. داخل `resource_callback` يمكنك فحص `extension` وإرجاع مسار مثل `f"png/{new_name}"` للصور النقطية و `f"svg/{new_name}"` للمتجهات. |
| **هل يعمل هذا على Linux/macOS؟** | بالطبع. يستخدم الكود `os.path` الذي يج abstracts separators المسارات. فقط تأكد من أن ملف ترخيص Aspose.Words (`aspose.words.lic`) متاح إذا كنت تستخدم النسخة المدفوعة. |
| **ماذا عن استهلاك الذاكرة للوثائق الضخمة؟** | يتلقى رد النداء **مصفوفة البايت الكاملة** لكل مورد، مما يعني أن الصورة بأكملها تُخزن مؤقتًا في الذاكرة. للملفات متعددة الجيجابايت قد ترغب في تدفق البيانات إلى القرص داخل رد النداء بدلاً من إرجاعها. |

## الخلاصة

أنت الآن تعرف **كيفية تعيين رد نداء** للتحكم في استخراج الصور عندما **تحفظ DOCX كـ Markdown**. يتيح لك هذا النهج **تصدير الصور من DOCX**، **استخراج SVG من Word**، والحفاظ على Markdown نظيفًا وحتميًا.  

في سكريبت واحد مستقل غطينا تحميل المستند، تعريف رد نداء حفظ الموارد، تكوين `MarkdownSaveOptions`، ومعالجة الحالات الطرفية مثل تصادم الأسماء والرسومات المتجهة. النتيجة هي مجموعة من الأصول ذات أسماء فريدة بجانب ملف Markdown مرتبط بشكل مثالي—جاهز لمولدات المواقع الثابتة، خطوط توثيق، أو أي سير عمل يحتاج إلى أصول نظيفة وقابلة لإعادة الاستخدام.  

**الخطوات التالية؟**  
- جرّب ربط هذا مع مولد موقع ثابت مثل MkDocs لنشر مستندات Word تلقائيًا.  
- جرب `markdown_options.export_images_as_base64 = True` إذا كنت تفضّل الصور المضمنة بدلاً من الملفات الخارجية.  
- تعمّق أكثر في ردود النداء الأخرى في Aspose.Words (مثل `document_saving_callback`) للتحكم في ناتج Markdown نفسه.  

هل لديك المزيد من الأسئلة حول **كيفية استخراج الصور** من صيغ Office أخرى، أو تحتاج مساعدة في تعديل رد النداء لتناسب نمط تسمية معين؟ اترك تعليقًا أدناه، وتمنياتنا لك بالبرمجة السعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة شاملة من الكود مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إعادة تسمية الصور عند تحويل DOCX إلى Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)
- [كيفية حفظ Markdown من DOCX – دليل خطوة بخطوة](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}