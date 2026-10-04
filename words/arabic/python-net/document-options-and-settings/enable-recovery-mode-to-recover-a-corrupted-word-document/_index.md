---
category: general
date: 2026-10-04
description: تمكين وضع الاسترداد في Aspose.Words لاستعادة مستند Word تالف بأمان. اتبع
  الدليل خطوة بخطوة مع كود Python الكامل والشروحات.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- enable recovery mode
- recover corrupted word document
- Aspose.Words load options
- document recovery Python
- handling damaged .docx files
language: ar
lastmod: 2026-10-04
og_description: تمكين وضع الاسترداد لاستعادة مستند Word تالف باستخدام Aspose.Words.
  يوضح هذا البرنامج التعليمي شفرة Python الدقيقة، ولماذا تعمل، وكيفية التعامل مع الحالات
  الحدية.
og_image_alt: Screenshot of Python code loading a corrupted Word document with recovery
  mode enabled
og_title: تفعيل وضع الاسترداد لاستعادة مستند Word تالف – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Enable recovery mode in Aspose.Words to recover a corrupted Word document
    safely. Follow the step‑by‑step guide with full Python code and explanations.
  headline: Enable recovery mode to recover a corrupted Word document
  type: TechArticle
- description: Enable recovery mode in Aspose.Words to recover a corrupted Word document
    safely. Follow the step‑by‑step guide with full Python code and explanations.
  name: Enable recovery mode to recover a corrupted Word document
  steps:
  - name: Create `LoadOptions` and set `recovery_mode` to `RECOVER`.
    text: Create `LoadOptions` and set `recovery_mode` to `RECOVER`.
  - name: Load the `.docx` using those options.
    text: Load the `.docx` using those options.
  - name: Verify the mode and optionally save a repaired copy.
    text: Verify the mode and optionally save a repaired copy.
  type: HowTo
tags:
- Aspose.Words
- Python
- Document processing
- Error handling
title: تمكين وضع الاسترداد لاستعادة مستند Word تالف
url: /ar/python/document-options-and-settings/enable-recovery-mode-to-recover-a-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تمكين وضع الاسترداد لاستعادة مستند Word تالف

إذا كنت بحاجة إلى **تمكين وضع الاسترداد** عند تحميل ملف Word، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك باستخدام Aspose.Words for Python. من خلال تشغيل وضع الاسترداد يمكنك **استعادة مستند Word تالف** كان سيتسبب بخطأ استثناءً.

في الأقسام التالية ستتعلم:

* أي الفئات والخصائص تتحكم في سلوك الاسترداد.  
* كيفية تحميل ملف `.docx` قد يكون تالفًا دون تعطل تطبيقك.  
* نصائح لاستكشاف مشكلات التحميل الشائعة وتخصيص استراتيجية الاسترداد.

> **المتطلبات المسبقة** – لديك Aspose.Words for Python مثبتًا (`pip install aspose-words`) وفهم أساسي لإدخال وإخراج الملفات في Python.

## ما يفعله وضع الاسترداد ولماذا يجب تمكينه

Aspose.Words يحلل البنية الداخلية لملف Word قبل عرضه ككائن `Document`. عندما يكون الملف تالفًا—أجزاء مفقودة، XML معطوب، أو علاقات غير صالحة—يمكن للمحلل إما:

| الوضع | السلوك |
|------|------------|
| `STRICT` | يرمي استثناءً عند أول علامة على الفساد. |
| `IGNORE_ERRORS` | يتخطى الأجزاء غير القابلة للقراءة لكنه قد يفقد المحتوى بصمت. |
| `RECOVER` (خيار **تمكين وضع الاسترداد**) | يحاول إعادة بناء المستند، مع الحفاظ على أكبر قدر ممكن من المحتوى وعرض الوضع المختار عبر `load_options.recovery_mode`. |

`RECOVER` هو الخيار الموصى به عندما يجب عليك **استعادة ملفات Word تالف** للمعالجة اللاحقة، مثل استخراج النص أو التحويل إلى PDF.

## الخطوة 1: إنشاء خيارات التحميل وتمكين وضع الاسترداد

الخطوة الأولى هي إنشاء كائن `LoadOptions` وتعيين الخاصية `recovery_mode` إلى `RecoveryMode.RECOVER`. هذا يخبر المكتبة بالدخول في مسار الاسترداد أثناء التحليل.

```python
import aspose.words as aw

# Step 1: Create load options and enable recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER  # alternatives: .IGNORE_ERRORS, .STRICT
```

**لماذا هذا مهم:**  
إذا تخطيت هذه الخطوة وكان المستند تالفًا، سيُطلق المُنشئ `aw.Document(...)` استثناءً `InvalidOperationException`. تمكين وضع الاسترداد يمنع التعطل ويعطيك كائن `Document` مُصلح جزئيًا يمكنك الاستمرار في العمل معه.

## الخطوة 2: تحميل المستند المحتمل التلف باستخدام الخيارات المحددة

مرّر كائن `load_options` إلى مُنشئ `Document`. سيطبق المحمل الآن خوارزمية الاسترداد تلقائيًا.

```python
# Step 2: Load the potentially corrupted document using the specified options
doc_path = "YOUR_DIRECTORY/Corrupted.docx"
doc = aw.Document(doc_path, load_options)
```

**نصيحة:** استبدل `YOUR_DIRECTORY` بالمسار المطلق أو النسبي الذي يمكن لبيئة التشغيل الوصول إليه. إذا لم يكن الملف موجودًا، سيُطلق Aspose.Words استثناءً `FileNotFoundError` قبل أن يصل إلى منطق الاسترداد.

## الخطوة 3: التحقق من تطبيق وضع الاسترداد

يمكنك تأكيد الوضع النشط عن طريق فحص `load_options.recovery_mode`. هذا مفيد للتسجيل أو المعالجة الشرطية لاحقًا في سير العمل.

```python
# Step 3: Confirm that the document was loaded with the chosen recovery mode
print("Document loaded with recovery mode:", load_options.recovery_mode)
```

**الناتج المتوقع**

```
Document loaded with recovery mode: RecoveryMode.RECOVER
```

إذا أظهر الناتج `RECOVER`، فقد نجحت في **تمكين وضع الاسترداد** وأصبح المستند الآن جاهزًا للمعالجة الإضافية (مثل استخراج النص، التحويل إلى PDF، أو حفظ نسخة مُصلحة).

## الخطوة 4 (اختياري): حفظ نسخة مُصَلاحَة للاستخدام المستقبلي

بعد التحميل، قد ترغب في حفظ المستند المستعاد حتى لا تحتاج إلى تكرار خطوة الاسترداد.

```python
# Optional: Save the repaired document
repaired_path = "YOUR_DIRECTORY/Corrupted_Repaired.docx"
doc.save(repaired_path)
print(f"Repaired document saved to {repaired_path}")
```

الحفظ ينشئ ملف `.docx` جديد تعتبره Aspose.Words صالحًا، ويمكن فتحه في Microsoft Word دون تحذيرات.

## أسئلة شائعة ومعالجة الحالات الخاصة

| السؤال | الإجابة |
|----------|--------|
| **ماذا لو كان المستند غير قابل للقراءة تمامًا؟** | حتى في وضع `RECOVER`، بعض الملفات لا يمكن إصلاحها. سيتم إنشاء كائن `Document` لكنه قد يحتوي على صفحة فارغة واحدة فقط. تحقق من `doc.get_page_count()` لتأكيد المحتوى. |
| **هل يمكنني التحويل إلى `IGNORE_ERRORS` بعد التحميل؟** | لا. يجب تعيين وضع الاسترداد **قبل** تشغيل مُنشئ `Document`. أنشئ كائن `LoadOptions` جديد إذا كنت بحاجة إلى استراتيجية مختلفة. |
| **هل يؤثر وضع الاسترداد على الأداء؟** | نعم، يضيف بعض الحمل الإضافي لأن المكتبة تحاول إعادة بناء الأجزاء المكسورة. التأثير ضئيل لمعظم الملفات (< 2 ميغابايت). |
| **هل هذا النهج مستقل عن اللغة؟** | المفهوم نفسه موجود في واجهات .NET و Java و Node.js (`LoadOptions.RecoveryMode`). يتغير بناء الكود، لكن المنطق هو نفسه. |

## نصيحة احترافية: تسجيل معلومات الاسترداد التفصيلية

توفر Aspose.Words خاصية `LoadOptions.recovery_callback` التي تستقبل رسائل تفصيلية حول كل خطوة استرداد. ربطها يمكن أن يساعدك في تشخيص سبب فشل مستند معين.

```python
def recovery_logger(message):
    print("[Recovery] ", message)

load_options.recovery_callback = recovery_logger
```

الآن سيتم طباعة كل إصلاح داخلي (مثل “Removed duplicate relationship”) إلى وحدة التحكم.

## مثال كامل قابل للتنفيذ

بتجميع جميع الأجزاء معًا، إليك سكربت مستقل يمكنك نسخه ولصقه وتشغيله فورًا:

```python
import aspose.words as aw

def enable_recovery_and_load(doc_path: str, save_repaired: bool = False):
    # Create load options and enable recovery mode
    load_options = aw.loading.LoadOptions()
    load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER

    # Optional: attach a simple logger
    load_options.recovery_callback = lambda msg: print("[Recovery] ", msg)

    # Load the document with recovery enabled
    doc = aw.Document(doc_path, load_options)

    # Verify the mode
    print("Document loaded with recovery mode:", load_options.recovery_mode)

    # Show basic info
    print("Page count:", doc.page_count)
    print("Word count:", doc.get_text().split())

    # Optionally save a repaired copy
    if save_repaired:
        repaired_path = doc_path.replace(".docx", "_repaired.docx")
        doc.save(repaired_path)
        print(f"Repaired document saved to {repaired_path}")

    return doc

if __name__ == "__main__":
    corrupted_path = "YOUR_DIRECTORY/Corrupted.docx"
    enable_recovery_and_load(corrupted_path, save_repaired=True)
```

تشغيل السكربت يطبع وضع الاسترداد، عدد الصفحات، وقائمة الكلمات المستخرجة من المستند المُصلَح. إذا قمت بتعيين `save_repaired=True`، سيظهر ملف نظيف جديد بجانب الأصلي.

## الخلاصة

أنت الآن تعرف كيفية **تمكين وضع الاسترداد** في Aspose.Words for Python واستعادة ملفات **Word التالفة** بشكل موثوق. الخطوات الأساسية هي:

1. إنشاء `LoadOptions` وتعيين `recovery_mode` إلى `RECOVER`.  
2. تحميل ملف `.docx` باستخدام تلك الخيارات.  
3. التحقق من الوضع وربما حفظ نسخة مُصلَحة.

من هنا يمكنك استكشاف مواضيع إضافية مثل **استخراج النص من مستند مستعاد**، **تحويله إلى PDF**، أو **أتمتة الاسترداد الجماعي** لمكتبات المستندات الكبيرة.

---

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شاملة من الشيفرة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [استعادة DOCX تالف – دليل كامل لتمكين وضع الاسترداد والحصول على الصفحة](/words/english/python-net/document-operations/recover-corrupted-docx-complete-guide-to-enable-recovery-mod/)
- [استعادة DOCX تالف – فتح وتحميل مستند Word](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)
- [استعادة docx تالف باستخدام Aspose.Words – ضبط وضع الاسترداد وخيارات التحميل](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}