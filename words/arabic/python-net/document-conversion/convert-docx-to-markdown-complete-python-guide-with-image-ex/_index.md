---
category: general
date: 2026-06-27
description: تحويل ملفات docx إلى markdown باستخدام Python. تعلم استخراج الصور من Word وحفظ
  مخرجات markdown باستخدام رد نداء مخصص.
draft: false
keywords:
- convert docx to markdown
- extract images from word
- convert word to markdown
- python docx to markdown
- save markdown output
language: ar
og_description: تحويل ملفات docx إلى markdown باستخدام بايثون، استخراج الصور من Word،
  وحفظ الناتج بصيغة markdown عبر استدعاء مخصص للموارد.
og_title: تحويل docx إلى markdown – دليل بايثون مع استخراج الصور
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Convert docx to markdown using Python. Learn to extract images from
    Word and save markdown output with a custom callback.
  headline: Convert docx to markdown – Complete Python Guide with Image Extraction
  type: TechArticle
- description: Convert docx to markdown using Python. Learn to extract images from
    Word and save markdown output with a custom callback.
  name: Convert docx to markdown – Complete Python Guide with Image Extraction
  steps:
  - name: Expected Output
    text: '```markdown # Sample Document'
  - name: Quick sanity check
    text: '```bash # On Unix/macOS cat YOUR_DIRECTORY/output.md ls YOUR_DIRECTORY/images/
      ```'
  - name: Dealing with duplicate image names
    text: 'Word sometimes reuses the same internal name for different pictures. To
      avoid overwriting, you can tweak `image_saver`:'
  - name: Converting large documents
    text: 'For multi‑megabyte documents, consider streaming the output to avoid memory
      spikes:'
  type: HowTo
tags:
- Python
- Aspose.Words
- Document Conversion
title: تحويل docx إلى markdown – دليل بايثون الكامل مع استخراج الصور
url: /ar/python/document-conversion/convert-docx-to-markdown-complete-python-guide-with-image-ex/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تحويل docx إلى markdown – دليل Python كامل مع استخراج الصور

هل تساءلت يوماً كيف **تحول docx إلى markdown** دون فقدان الصور المدمجة في ملف Word الخاص بك؟ لست وحدك. يواجه العديد من المطورين مشكلة عندما تُفقد الصور أثناء التحويل، فتظهر روابط مكسورة في markdown أو، والأسوأ، لا توجد صور على الإطلاق.  

الخبر السار؟ ببضع أسطر من Python و Aspose.Words يمكنك تحويل ملف `.docx` إلى markdown نظيف **وبينما** تستخرج كل صورة إلى مجلد تختاره. في هذا الدرس سنستعرض العملية بالكامل، من تثبيت المكتبة إلى ربط رد نداء (callback) يحفظ كل صورة في المكان الذي تريد.

بنهاية هذا الدليل ستتمكن من **تحويل word إلى markdown**، استخراج كل رسومات، و **حفظ ناتج markdown** جاهز لمولدات المواقع الثابتة، خطوط أنابيب التوثيق، أو أي سير عمل يركز على markdown أولاً.

## ما الذي ستحتاجه

- Python 3.8 أو أحدث (الكود يعمل على 3.9+ أيضاً)  
- إمكانية الوصول إلى `pip` لتثبيت الحزم الخارجية  
- ترخيص صالح لـ Aspose.Words for Python (الإصدار التجريبي المجاني يكفي للتقييم)  
- ملف `input.docx` تجريبي يحتوي على نص وعلى الأقل صورة واحدة  

هذا كل ما تحتاجه—بدون تثبيت Office ثقيل، بدون COM interop، فقط Python نقي.

## الخطوة 1: تثبيت Aspose.Words for Python

أولاً، لنحصل على المكتبة. افتح الطرفية ونفّذ:

```bash
pip install aspose-words
```

إذا صادفت خطأ في الصلاحيات، أضف `--user` أو استخدم بيئة افتراضية. بعد انتهاء التثبيت، ستحصل على حزمة `aspose.words` (تُستورد كـ `aw` في الأمثلة).

> **نصيحة احترافية:** حافظ على نظافة ملف `requirements.txt`؛ أضف `aspose-words==<latest-version>` حتى يتمكن المتعاونون من استنساخ البيئة بدقة.

## الخطوة 2: إعداد رد نداء مخصص لحفظ الصور

تتيح لك Aspose.Words ربط رد نداء *حفظ الموارد* بعملية الحفظ. فكر فيه كوسيط يستقبل تدفق البايتات لكل صورة ويخبر المكتبة أين تُشير إليها في ملف markdown المُولد.

هذا هو جوهر رد النداء:

```python
# Step 1: Define a callback to store extracted images in a custom folder
def image_saver(image_bytes, image_name):
    """
    Saves an image to YOUR_DIRECTORY/images/ and returns the relative path
    that will be placed in the markdown file.
    """
    # Ensure the target folder exists
    import os
    target_dir = os.path.join("YOUR_DIRECTORY", "images")
    os.makedirs(target_dir, exist_ok=True)

    # Build the full path on disk
    file_path = os.path.join(target_dir, image_name)

    # Write the raw image bytes to disk
    with open(file_path, "wb") as f:
        f.write(image_bytes)

    # Return the path that markdown will use (relative to the .md file)
    return os.path.join("images", image_name)
```

**لماذا هذا مهم:**  
- **التحكم** – يمكنك تحديد بنية المجلدات، نظام التسمية، أو حتى تحويل صيغة الصورة إذا احتجت.  
- **القابلية للنقل** – المسار النسبي المُعاد يجعل markdown قابلًا للنقل بين الأجهزة طالما أن مجلد `images` ينتقل معه.  
- **الأداء** – يُستدعى رد النداء مرة واحدة لكل صورة فقط، مما يتجنب الكتابة المتكررة.

## الخطوة 3: تكوين خيارات حفظ Markdown

الآن نربط رد النداء بكائن `MarkdownSaveOptions`. هذا يخبر Aspose.Words باستخدام `image_saver` كلما صادفت مورد صورة.

```python
# Step 2: Create Markdown save options and attach the callback
md_options = aw.saving.MarkdownSaveOptions()
md_options.resource_saving_callback = image_saver
```

يمكنك أيضًا تعديل بعض الإعدادات الاختيارية هنا، مثل `export_images_as_base64` (ضعه `False` لأننا نريد ملفات منفصلة) أو `add_table_of_contents` إذا كنت تحتاج فهرسًا. بالنسبة لهذا الدليل سنبقى على الإعدادات الافتراضية.

## الخطوة 4: تحميل مستند Word المصدر

تحميل ملف `.docx` سهل. فقط أعطِ Aspose.Words مسار الملف:

```python
# Step 3: Load the source Word document
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

إذا كان المستند كبيرًا، قد تفكر في بثه باستخدام `aw.LoadOptions`، لكن في معظم الحالات يكفي المُنشئ البسيط.

## الخطوة 5: حفظ كـ Markdown – دع رد النداء يقوم بالعمل الشاق

أخيرًا، نطلب من Aspose.Words كتابة ملف markdown. ستستدعي المكتبة `image_saver` لكل صورة مدمجة، تخزن الملفات، وتدرج روابط markdown الصحيحة للصور.

```python
# Step 4: Save the document as Markdown, letting the callback handle image resources
doc.save("YOUR_DIRECTORY/output.md", md_options)
```

عند انتهاء العملية ستلاحظ شيئين:

1. `output.md` يحتوي على نص markdown مع أسطر مثل `![](images/image1.png)`  
2. مجلد فرعي `images` مليء بكل صورة مستخرجة.

### النتيجة المتوقعة

```markdown
# Sample Document

This is a paragraph from the Word file.

![](images/image1.png)

Another paragraph follows the picture.
```

افتح `output.md` في أي عارض markdown (VS Code، GitHub، MkDocs) وسترى الصورة معروضة تمامًا كما ظهرت في ملف Word الأصلي.

## الخطوة 6: التحقق من النتيجة ومعالجة الحالات الخاصة

### فحص سريع للمنطقية

```bash
# On Unix/macOS
cat YOUR_DIRECTORY/output.md
ls YOUR_DIRECTORY/images/
```

تأكد من أن أسماء ملفات الصور تطابق المسارات في markdown. إذا لاحظت صورًا مفقودة، تحقق من أن رد النداء أعاد **المسار النسبي** (وليس المطلق) وأن مجلد `images` مُشار إليه بشكل صحيح.

### التعامل مع أسماء صور مكررة

أحيانًا يعيد Word استخدام نفس الاسم الداخلي لصور مختلفة. لتجنب الكتابة فوق بعضها، يمكنك تعديل `image_saver`:

```python
import uuid

def image_saver(image_bytes, image_name):
    unique_name = f"{uuid.uuid4().hex}_{image_name}"
    # rest of the code uses unique_name instead of image_name
    ...
    return os.path.join("images", unique_name)
```

### تحويل مستندات ضخمة

للمستندات متعددة الميجابايت، فكر في بث الناتج لتجنب ارتفاع استهلاك الذاكرة:

```python
with open("YOUR_DIRECTORY/output.md", "w", encoding="utf-8") as out_file:
    doc.save(out_file, md_options)
```

تتعامل Aspose.Words مع البث داخليًا، لذا لا تحتاج إلى تحميل كامل markdown في الذاكرة.

## الخطوة 7: أتمتة سير العمل (اختياري)

إذا كنت بحاجة لمعالجة مجموعة من ملفات Word دفعةً واحدة، غلف المنطق داخل حلقة:

```python
import glob

for doc_path in glob.glob("YOUR_DIRECTORY/*.docx"):
    doc = aw.Document(doc_path)
    base_name = os.path.splitext(os.path.basename(doc_path))[0]
    md_path = f"YOUR_DIRECTORY/{base_name}.md"
    doc.save(md_path, md_options)
    print(f"Converted {doc_path} → {md_path}")
```

الآن يمكنك وضع مئة ملف `.docx` في الدليل ودع السكريبت يعالجها، كل ملف مع مجلد `images` الخاص به.

## الخلاصة

غطينا كل ما تحتاجه **لتحويل docx إلى markdown** مع الحفاظ على كل صورة، باستخدام سكريبت Python بسيط وآلية رد النداء القوية في Aspose.Words. الآن تعرف كيف:

- **استخراج الصور من Word** عبر `resource_saving_callback` مخصص  
- **تحويل word إلى markdown** بأقل إعدادات  
- **حفظ ناتج markdown** جنبًا إلى جنب مع مجلد صور منظم  

من هنا يمكنك تجربة إضافات markdown أخرى (جداول، حواشي) أو دمج السكريبت في خط أنابيب CI يبني التوثيق تلقائيًا. السماء هي الحد—فقط تذكر أن تجعل منطق حفظ الصور مرنًا، وسيظل markdown نظيفًا.

هل لديك أسئلة حول الحالات الخاصة أو الترخيص؟ اترك تعليقًا أدناه، وتمنياتنا لك ببرمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [How to Save Markdown from Word – Complete Python Guide](/words/english/python-net/document-conversion/how-to-save-markdown-from-word-complete-python-guide/)
- [Convert Docx File To Markdown](/words/english/net/basic-conversions/docx-to-markdown/)
- [Convert Word to Markdown – Embed Images as Base64](/words/english/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}