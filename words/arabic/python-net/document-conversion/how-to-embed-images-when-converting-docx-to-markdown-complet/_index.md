---
category: general
date: 2026-05-04
description: تعلم كيفية تضمين الصور أثناء تحويل DOCX إلى Markdown باستخدام Aspose.Words.
  يتضمن خطوات تحويل Word إلى Markdown، استخراج الصور من DOCX، وتضمين الصور كـ Base64.
draft: false
keywords:
- how to embed images
- convert docx to markdown
- convert word to markdown
- extract images from docx
- embed images as base64
language: ar
og_description: اكتشف كيفية تضمين الصور أثناء تحويل DOCX إلى Markdown باستخدام Aspose.Words
  للبايثون. يتضمن الكود الكامل، الشروحات، ونصائح لاستخراج الصور من DOCX وتضمينها كـ
  base64.
og_title: كيفية تضمين الصور عند تحويل DOCX إلى Markdown – خطوة بخطوة
tags:
- Aspose.Words
- Python
- Markdown
- Document Conversion
title: كيفية تضمين الصور عند تحويل DOCX إلى Markdown – دليل كامل
url: /ar/python/document-conversion/how-to-embed-images-when-converting-docx-to-markdown-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تضمين الصور عند تحويل DOCX إلى Markdown – دليل كامل

هل تساءلت يومًا **كيفية تضمين الصور** في ملف Markdown نشأ من مستند Word؟ لست الوحيد. يواجه العديد من المطورين صعوبة عندما يحاولون تحويل DOCX إلى Markdown وينتهي بهم الأمر بروابط صور مكسورة. الخبر السار؟ ببضع أسطر من Python و Aspose.Words يمكنك الحفاظ على كل صورة سليمة، حتى كـ Base64 data‑URI.

في هذا الدرس سنستعرض العملية بالكامل: من تثبيت Aspose.Words، تحميل ملف DOCX يحتوي على صور، استخراج تلك الصور، وأخيرًا **تضمين الصور كسلاسل base64** داخل ملف Markdown المُولد. في النهاية ستتمكن من **تحويل docx إلى markdown**، **تحويل word إلى markdown**، وحتى **استخراج الصور من docx** لاستخدامات أخرى—كل ذلك دون مغادرة بيئة التطوير المتكاملة الخاصة بك.

> **المتطلبات المسبقة**  
> * Python 3.8+  
> * حزمة `aspose-words` (الإصدار التجريبي المجاني يعمل لمعظم السيناريوهات)  
> * ملف DOCX يحتوي على صورة واحدة على الأقل (سنسميه `Images.docx`)  

إذا كنت مرتاحًا مع pip وعمليات I/O الأساسية للملفات، فأنت جاهز. لنبدأ.

---

## كيفية تضمين الصور أثناء تحويل DOCX إلى Markdown

هذا العنوان H2 يفي مباشرةً بقاعدة الكلمة المفتاحية الأساسية ويخبر كل من محركات البحث ومساعدي الذكاء الاصطناعي بالضبط ما يغطيه هذا القسم.

### الخطوة 1: تثبيت Aspose.Words للـ Python

أولاً، احصل على المكتبة من PyPI. اسم الحزمة هو `aspose-words`، ولا يجب الخلط بينها وبين نسخة .NET.

```bash
pip install aspose-words
```

> **نصيحة احترافية:** إذا كنت خلف بروكسي مؤسسي، أضف `--proxy http://your-proxy:port` إلى الأمر.  

تقوم عملية تثبيت الحزمة أيضًا بسحب تبعيات `aspose-words` الخاصة، مثل `aspose-words-cloud`. لا حاجة لأي إعداد إضافي للتحويل المحلي.

### الخطوة 2: تحميل مستند DOCX المصدر

سنستخدم الفئة `aw.Document` لفتح الملف. هذه الخطوة هي المكان الذي **تستخرج فيه الصور من docx** إذا احتجت إليها بشكل منفصل.

```python
import aspose.words as aw
import base64

# Path to the Word file that contains images
doc_path = "YOUR_DIRECTORY/Images.docx"

# Load the document into memory
document = aw.Document(doc_path)
```

> **لماذا هذا مهم:** تحميل المستند يمنحك الوصول إلى `resource_saving_callback` لاحقًا، وهو النقطة التي يستخدمها Aspose لتحديد كيفية كتابة الصور أثناء عملية حفظ Markdown.

### الخطوة 3: تعريف رد نداء يحول كل صورة إلى Base64 data‑URI

يسمح لك Aspose بالتقاط كل مورد (صور، خطوط، إلخ) كان سيُكتب عادةً إلى القرص. من خلال توفير رد نداء يمكننا استبدال المعالجة الافتراضية القائمة على الملفات بسلسلة Base64 مدمجة.

```python
def embed_images_callback(resource):
    """
    Called for every resource Aspose wants to save.
    If the resource is an image, we convert it to a data‑URI.
    """
    # Only process image resources; other types fall back to default handling
    if resource.resource_type == aw.saving.MarkdownResourceType.IMAGE:
        # Build the data‑URI: data:<mime>;base64,<encoded bytes>
        data_uri = (
            f"data:{resource.mime_type};base64,"
            f"{base64.b64encode(resource.bytes).decode()}"
        )
        # Return a tuple (resource name, encoded data) – name is ignored for data‑URI
        return (resource.name, data_uri.encode())
    # Returning None tells Aspose to use its default saving logic
    return None
```

> **حالة حافة:** بعض ملفات Word تضم صور SVG. يُبلغ Aspose عن نوع MIME كـ `image/svg+xml`، وهو ما يدعمه الـ data‑URI أيضًا. إذا كان عارض Markdown المستهدف لا يعرض SVG، ففكّر في تحويله إلى PNG داخل رد النداء.

### الخطوة 4: تكوين خيارات حفظ Markdown وإرفاق رد النداء

الآن نخبر Aspose باستخدام رد النداء الذي عرّفناه للتو. هذا هو جوهر **كيفية تضمين الصور** في ملف Markdown النهائي.

```python
# Create save options for Markdown
markdown_options = aw.saving.MarkdownSaveOptions()

# Attach our custom callback
markdown_options.resource_saving_callback = embed_images_callback
```

يمكنك أيضًا تعديل `markdown_options` للتحكم في مستويات العناوين، حدود كتل الشيفرة، أو ما إذا كان سيتم إنشاء مجلد موارد منفصل. في هذا الدليل نحتفظ بالإعدادات الافتراضية لأن نهج الـ data‑URI يلغي الحاجة لأي مجلد إضافي.

### الخطوة 5: حفظ المستند كـ Markdown مع صور Base64 مدمجة

أخيرًا، نكتب ملف الإخراج. النتيجة هي ملف `.md` واحد يحتوي على كل صورة كسلسلة Base64—دون الحاجة إلى أصول خارجية.

```python
output_path = "YOUR_DIRECTORY/ImagesEmbedded.md"
document.save(output_path, markdown_options)

print(f"✅ Markdown with embedded images saved to: {output_path}")
```

عند فتح `ImagesEmbedded.md` في عارض Markdown (VS Code، GitHub، أو مولد موقع ثابت)، يجب أن تظهر كل صورة في الموضع الذي كانت فيه في مستند Word الأصلي.

> **ما ستراه:**  
> ```markdown
> ![Picture1](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
> ```  
> السلسلة الطويلة بعد `base64,` هي البيانات الثنائية للصورة، مُشفرة بطريقة يمكن للمتصفحات فك تشفيرها مباشرةً.

---

## تحويل DOCX إلى Markdown دون فقدان الصور – المشكلات الشائعة

على الرغم من أن الشيفرة أعلاه تعمل مباشرةً، يواجه المطورون غالبًا بعض العقبات. إليك أكثر الأسئلة شيوعًا والإجابات التي تحافظ على سلاسة التحويل.

### 1. “الصور لا تزال مفقودة بعد التحويل”

* **تحقق من نوع MIME:** بعض ملفات DOCX القديمة تخزن الصور بنوع MIME عام (`application/octet-stream`). سيظل رد النداء يدمجها، لكن بعض عارضي Markdown يرفضون عرض الأنواع غير المعروفة. يمكنك فرض رجوع إلى `image/png` في رد النداء إذا كنت تعرف تنسيق الصورة.
* **المستندات الكبيرة:** يضيف Base64 حوالي 33 % إلى الحجم. إذا كنت تحول ملف Word حجمه 10 ميغابايت، قد يصبح حجم Markdown الناتج ~13 ميغابايت. معظم المحررات الحديثة تتعامل مع ذلك، لكن مولدات المواقع الثابتة قد تكون لها حدود. فكر في استخراج الصور إلى مجلد بدلاً من دمجها إذا كان الحجم يمثل قلقًا.

### 2. “هل يمكنني أيضًا استخراج الصور من DOCX للاستخدام المنفصل؟”

بالطبع. يمكن لنفس رد النداء كتابة بايتات الصورة إلى القرص قبل إرجاع الـ data‑URI.

```python
import os

def embed_and_save_images(resource):
    if resource.resource_type == aw.saving.MarkdownResourceType.IMAGE:
        # Save the raw image to a folder
        os.makedirs("extracted_images", exist_ok=True)
        with open(f"extracted_images/{resource.name}", "wb") as f:
            f.write(resource.bytes)

        # Then embed as Base64 (same as before)
        data_uri = f"data:{resource.mime_type};base64,{base64.b64encode(resource.bytes).decode()}"
        return (resource.name, data_uri.encode())
    return None
```

تشغيل هذا الإصدار سيعطيك كلًا من مجلد `extracted_images` **و** ملف Markdown مع صور Base64 مدمجة—مثالي للمشاريع التي تحتاج إلى كليهما.

### 3. “ماذا عن الجداول، الحواشي، أو ميزات Word الخاصة؟”

يحاول Aspose.Words الحفاظ على أكبر قدر ممكن من التنسيق، لكن Markdown يمتلك مجموعة ميزات محدودة. تُحول الجداول إلى صيغة مفصولة بأنابيب، بينما تتحول الحواشي إلى علامات نصية عادية. إذا كنت تحتاج إلى مخرجات أغنى (مثل HTML)، غيّر `MarkdownSaveOptions` إلى `HtmlSaveOptions` واحتفظ بمنطق رد النداء نفسه.

---

## مثال كامل قابل للتنفيذ – جاهز للنسخ واللصق

بدمج كل شيء معًا، إليك سكربت واحد يمكنك وضعه في أي مجلد مشروع. عدّل القيم `YOUR_DIRECTORY` لتشير إلى ملفاتك الفعلية.

```python
# ------------------------------------------------------------
# How to embed images while converting DOCX to Markdown
# ------------------------------------------------------------
# Prerequisites:
#   pip install aspose-words
# ------------------------------------------------------------

import aspose.words as aw
import base64
import os

# ------------------------------------------------------------------
# 1️⃣  Define the callback that embeds images as Base64 data‑URIs
# ------------------------------------------------------------------
def embed_images_callback(resource):
    """
    Aspose calls this for each external resource (image, font, etc.).
    We only care about images – everything else falls back to default.
    """
    if resource.resource_type == aw.saving.MarkdownResourceType.IMAGE:
        # Optional: also write the image to disk for later reuse
        os.makedirs("extracted_images", exist_ok=True)
        with open(f"extracted_images/{resource.name}", "wb") as img_file:
            img_file.write(resource.bytes)

        # Build the Base64 data‑URI
        data_uri = (
            f"data:{resource.mime_type};base64,"
            f"{base64.b64encode(resource.bytes).decode()}"
        )
        # Return name (ignored) and the encoded URI as bytes
        return (resource.name, data_uri.encode())
    return None  # Use Aspose's default handling for non‑image resources

# ------------------------------------------------------------------
# 2️⃣  Load the DOCX that contains images
# ------------------------------------------------------------------
doc_path = "YOUR_DIRECTORY/Images.docx"
document = aw.Document(doc_path)

# ------------------------------------------------------------------
# 3️⃣  Prepare Markdown save options and hook the callback
# ------------------------------------------------------------------
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.resource_saving_callback = embed_images_callback

# ------------------------------------------------------------------
# 4️⃣  Save as Markdown with images embedded as Base64
# ------------------------------------------------------------------
output_path = "YOUR_DIRECTORY/ImagesEmbedded.md"
document.save(output_path, markdown_options)

print(f"✅ Success! Markdown saved to {output_path}")
print("   Images are now inline Base64 data‑URIs.")
```

**النتيجة المتوقعة:** افتح `ImagesEmbedded.md` وسترى النص الأصلي بالإضافة إلى وسوم صور مدمجة مثل `![Picture1](data:image/png;base64,…)`. لا حاجة لملفات صور خارجية.

---

## الخلاصة

غطّينا **كيفية تضمين الصور** عندما **تحول docx إلى markdown**، وأظهرنا لك كيف **استخراج الصور من docx**، وبيّنّا أن أنقى طريقة **لتضمين الصور كـ base64** هي باستخدام Aspose.Words للـ Python. السكربت الكامل أعلاه جاهز للتنفيذ، وتوضح الشروحات “لماذا” وراء كل سطر—حتى تتمكن من تكييفه لمشاريعك دون تخمين.

هل تريد التعمق أكثر؟ جرّب الخطوات التالية:

* **تحويل Word إلى markdown** مع مستويات عناوين مخصصة عبر تعديل `markdown_options.heading_level`.
* **إنشاء PDF** من نفس DOCX ومقارنة كيفية معالجة الصور في صيغ إخراج مختلفة.
* **دمج السكربت في خط أنابيب CI** بحيث ينتج كل تعديل تلقائيًا لقطة Markdown لتوثيقك.

لا تتردد في التجربة—ربما تستبدل تضمين Base64 بعنوان CDN للملفات الضخمة، أو تضيف OCR للصور الممسوحة. السماء هي الحد، والآن لديك أساس قوي.

If you hit any sn
{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}