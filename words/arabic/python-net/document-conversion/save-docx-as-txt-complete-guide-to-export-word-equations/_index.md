---
category: general
date: 2026-06-24
description: تعلم كيفية حفظ ملفات docx كملفات txt وتصدير المعادلات من Word باستخدام LaTeX.
  كود بايثون خطوة بخطوة لتحويل النص إلى نص عادي.
draft: false
keywords:
- save docx as txt
- how to export equations
- export equations from word
- save word plain text
- export word equations latex
language: ar
og_description: احفظ ملف docx كملف txt مع تصدير معادلات LaTeX. اتبع هذا الدليل لتصدير
  معادلات Word بنمط LaTeX والحصول على ملفات نصية عادية.
og_title: حفظ ملف docx كملف txt – دورة بايثون كاملة
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Learn how to save docx as txt and export equations from Word using
    LaTeX. Step‑by‑step Python code for plain‑text conversion.
  headline: save docx as txt – Complete Guide to Export Word Equations
  type: TechArticle
- description: Learn how to save docx as txt and export equations from Word using
    LaTeX. Step‑by‑step Python code for plain‑text conversion.
  name: save docx as txt – Complete Guide to Export Word Equations
  steps:
  - name: '**Python 3.8+** installed (any recent version works).'
    text: '**Python 3.8+** installed (any recent version works).'
  - name: '**Aspose.Words for Python via .NET** – install with'
    text: '**Aspose.Words for Python via .NET** – install with'
  - name: A Word document (`.docx`) that contains at least one equation.
    text: A Word document (`.docx`) that contains at least one equation.
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Conversion
title: حفظ ملف docx كـ txt – دليل شامل لتصدير معادلات Word
url: /ar/python/document-conversion/save-docx-as-txt-complete-guide-to-export-word-equations/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ docx كـ txt – دليل كامل لتصدير معادلات Word

هل تساءلت يومًا كيف **حفظ docx كـ txt** مع الحفاظ على صيغ الرياضيات المزعجة؟ لست وحدك. يواجه العديد من المطورين صعوبة عندما يحتاجون إلى مخرجات نصية بسيطة لكنهم لا يزالون يرغبون في أن تُعرض المعادلات بصيغة قابلة للاستخدام.  

في هذا الدرس سنستعرض الخطوات الدقيقة لـ **حفظ docx كـ txt**، موضحين لك **كيفية تصدير المعادلات** من Word إلى LaTeX، ولماذا هذا مهم للمعالجة اللاحقة. في النهاية ستحصل على سكريبت Python جاهز للتنفيذ يحول ملف `.docx` مليء بالمعادلات إلى ملف `.txt` نظيف مع تنسيق LaTeX.

## ما ستتعلمه

- المتطلبات الدنيا (Python 3، Aspose.Words for Python)
- كيفية تكوين `TxtSaveOptions` للتحكم في تصدير المعادلات
- الفرق بين النص العادي وإخراج معادلات LaTeX
- كيفية التحقق من نجاح التصدير ومعالجة المشكلات الشائعة
- مثال كامل قابل للتنفيذ يمكنك نسخه ولصقه فورًا  

بدون إطالة، مجرد حل عملي يمكنك دمجه في أي مشروع.

## المتطلبات المسبقة

قبل أن نبدأ، تأكد من وجود ما يلي:

1. **Python 3.8+** مثبت (أي نسخة حديثة تعمل).
2. **Aspose.Words for Python via .NET** – تثبيت عبر  
   ```bash
   pip install aspose-words
   ```
3. مستند Word (`.docx`) يحتوي على معادلة واحدة على الأقل.  
   إذا لم يكن لديك واحد، أنشئ ملفًا سريعًا في Microsoft Word وأدرج معادلة عبر *Insert → Equation*.

هذا كل شيء—بدون مكتبات إضافية، بدون تبعيات ثقيلة.  

---

![مخطط يوضح سير عمل حفظ docx كـ txt مع تصدير معادلات LaTeX](https://example.com/images/save-docx-as-txt-workflow.png "سير عمل حفظ docx كـ txt")

*نص بديل للصورة: سير عمل حفظ docx كـ txt يظهر خطوات التحويل*

## الخطوة 1: تحميل مستند Word – التحضير لحفظ docx كـ txt

أولًا: تحتاج إلى جلب ملف `.docx` المصدر إلى الذاكرة. Aspose.Words يجعل ذلك سطرًا واحدًا.

```python
import aspose.words as aw

# Load the Word document that holds the equations
doc = aw.Document("YOUR_DIRECTORY/math.docx")
```

> **لماذا هذا مهم:** تحميل المستند يمنحنا الوصول إلى نموذج الكائنات الداخلي، مما يسمح لنا بتعديل خيارات الحفظ قبل أن **نحفظ docx كـ txt** فعليًا. بدون هذه الخطوة لا يمكنك التحكم في وضع تصدير المعادلات.

## الخطوة 2: تكوين TxtSaveOptions – كيفية تصدير المعادلات إلى LaTeX

الآن يأتي جوهر الدرس: إخبار Aspose.Words **كيفية تصدير المعادلات**. فئة `TxtSaveOptions` تعرض خاصية `office_math_export_mode` التي تقبل عدة قيم تعداد. سنختار `LATEX` لأنه مدعوم على نطاق واسع في سير العمل العلمي.

```python
# Create TXT save options to fine‑tune the export
txt_opts = aw.saving.TxtSaveOptions()
# Export equations as LaTeX markup – this is the key for export word equations latex
txt_opts.office_math_export_mode = aw.saving.TxtOfficeMathExportMode.LATEX
```

ملاحظة سريعة حول الأوضاع الأخرى:

| الوضع | النتيجة |
|------|--------|
| `TEXT` | تتحول المعادلات إلى رموز رياضية Unicode عادية (غالبًا غير قابلة للقراءة). |
| `MATHML` | تُنشئ MathML – ممتاز لـ HTML، لكنه كبير الحجم للنص العادي. |
| `LATEX` | ينتج شفرة LaTeX – مثالي لسلاسل العمل الأكاديمية. |

اختيار `LATEX` يلبي متطلبات **تصدير المعادلات من Word** مع الحفاظ على حجم الملف معقولًا.

## الخطوة 3: تنفيذ الحفظ – أخيرًا حفظ docx كـ txt

مع تحميل المستند وتعيين الخيارات، الخطوة الأخيرة هي الحفظ. طريقة `save` تأخذ مسار الهدف وكائن الخيارات الذي قمنا بتكوينه.

```python
# Save the document as a plain‑text file using our LaTeX export settings
output_path = "YOUR_DIRECTORY/math.txt"
doc.save(output_path, txt_opts)

print(f"Document saved successfully to {output_path}")
```

> **ما ستراه:** الملف الناتج `math.txt` يحتوي على الفقرات العادية تمامًا كما تظهر في Word، لكن كل معادلة تُستبدل بقطعة LaTeX، مثال:

```
Here is a quadratic formula:
\[
x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
\]
```

هذا هو جوهر **حفظ Word كنص عادي** مع الحفاظ على دقة المعادلات.

## الخطوة 4: التحقق من التصدير – فحص أن تصدير معادلات Word إلى LaTeX نجح

من السهل الافتراض أن كل شيء سار على ما يرام، لكن فحص سريع يوفّر عليك صداعًا لاحقًا. افتح ملف `.txt` المُولد في أي محرر:

```python
with open(output_path, "r", encoding="utf-8") as f:
    contents = f.read()
    print("First 200 characters of the output file:")
    print(contents[:200])
```

ابحث عن الفواصل `\[` و`\]` التي تحيط بشفرة LaTeX. إذا رأيت XML Word الخام بدلاً من ذلك، تحقق مرة أخرى من أنك استخدمت `TxtOfficeMathExportMode.LATEX`.  

---

## المشكلات الشائعة عند تصدير المعادلات من Word

| العَرَض | السبب المحتمل | الحل |
|---------|--------------|-----|
| تظهر المعادلات كـ `??` | الخط مفقود في المستند الأصلي | تأكد من أن المعادلة تستخدم خط Office Math مدعوم (Cambria Math). |
| شفرة LaTeX مفقودة | `office_math_export_mode` تركت على الوضع الافتراضي (`TEXT`) | عيّن الوضع إلى `LATEX` كما هو موضح في الخطوة 2. |
| ملف الإخراج فارغ | مسار ملف غير صحيح أو عدم وجود أذونات كتابة | تحقق من أن `output_path` يشير إلى دليل قابل للكتابة. |
| الأحرف غير ASCII مشوهة | ترميز الملف خاطئ | استخدم `encoding="utf-8"` عند فتح الملف للتحقق. |

الوعي بهذه القضايا يجعل عملية **حفظ docx كـ txt** سلسة وقابلة للتكرار.

## تعديلات متقدمة – تجاوز الأساسيات

إذا كنت تحتاج إلى مزيد من التحكم، توفر `TxtSaveOptions` مفاتيح إضافية:

- `encoding`: عيّن إلى `aw.saving.Encoding.UTF8` لإخراج UTF‑8 صريح.
- `preserve_table_layout`: الحفاظ على عرض أعمدة الجداول عند التحويل إلى نص.
- `add_bidi_marks`: مفيد للغات من اليمين إلى اليسار.

إليك مثال سريع يجمع بعض هذه الخيارات:

```python
txt_opts.encoding = aw.saving.Encoding.UTF8
txt_opts.preserve_table_layout = True
txt_opts.add_bidi_marks = True
doc.save("YOUR_DIRECTORY/advanced_math.txt", txt_opts)
```

هذا المقتطف مثالي عندما تحتاج إلى **حفظ Word كنص عادي** للوثائق متعددة اللغات.

## البرنامج الكامل – جاهز للتنفيذ

فيما يلي السكريبت الكامل القابل للتنفيذ بلغة Python الذي يدمج كل ما تناولناه. انسخه، عدّل المسارات، وستكون جاهزًا.

```python
import aspose.words as aw

def convert_docx_to_txt_with_latex(input_path: str, output_path: str) -> None:
    """
    Loads a .docx file, configures TxtSaveOptions to export equations as LaTeX,
    and saves the result as a plain‑text .txt file.

    Parameters:
        input_path (str): Full path to the source .docx file.
        output_path (str): Desired path for the generated .txt file.
    """
    # Load the source document
    doc = aw.Document(input_path)

    # Set up save options – this is the key for export word equations latex
    txt_opts = aw.saving.TxtSaveOptions()
    txt_opts.office_math_export_mode = aw.saving.TxtOfficeMathExportMode.LATEX
    txt_opts.encoding = aw.saving.Encoding.UTF8  # Ensure UTF‑8 output

    # Perform the conversion
    doc.save(output_path, txt_opts)

    print(f"Successfully saved '{input_path}' as plain text with LaTeX equations to '{output_path}'.")

if __name__ == "__main__":
    # Adjust these paths to match your environment
    src = "YOUR_DIRECTORY/math.docx"
    dst = "YOUR_DIRECTORY/math.txt"
    convert_docx_to_txt_with_latex(src, dst)

    # Quick verification
    with open(dst, "r", encoding="utf-8") as f:
        sample = f.read(300)
        print("\n--- Sample of the generated file ---")
        print(sample)
```

تشغيل هذا السكريبت سيولد ملف `math.txt` يحتوي على نص المستند الأصلي بالإضافة إلى معادلات بصيغة LaTeX—بالضبط ما تحتاجه عندما **تحفظ docx كـ txt** للمعالجة اللاحقة مثل النشر العلمي أو استخراج البيانات.

---

## الخلاصة

لقد عرضنا طريقة موثوقة لـ **حفظ docx كـ txt** مع الحفاظ على كل معادلة بصيغة LaTeX. الخطوات الأساسية كانت تحميل المستند، تكوين `TxtSaveOptions` لت **تصدير المعادلات من Word** في وضع `LATEX`، وأخيرًا حفظ الملف النصي.  

مع هذه المعرفة يمكنك الآن أتمتة تحويل تقارير Word، ملاحظات المحاضرات، أو الأوراق البحثية إلى ملفات نصية نظيفة تتعامل بسلاسة مع الأدوات الداعمة لـ LaTeX.  

إذا كنت مستعدًا للتحدي التالي، جرّب تصدير نفس المستند إلى **Markdown** (باستخدام `aw.saving.SaveFormat.MARKDOWN`) أو جرب إخراج `MATHML` لتدفقات العمل الموجهة للويب. النمط نفسه—تحميل، ضبط الخيارات، حفظ—ينطبق على جميع الصيغ، مما يجعل قاعدة الشيفرة مرنة ومستقبلية.  

هل لديك أسئلة حول حالات خاصة أو تحتاج مساعدة في دمج هذا في خط أنابيب أكبر؟ اترك تعليقًا أدناه، وتمنياتنا لك بالبرمجة السعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم استعراضها في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [حفظ المستند كـ TXT – دليل C# كامل لتحويل DOCX إلى نص عادي](/words/english/net/programming-with-txtsaveoptions/save-document-as-txt-complete-c-guide-to-convert-docx-to-pla/)
- [كيفية تصدير LaTeX من Word – دليل خطوة بخطوة](/words/english/net/basic-conversions/how-to-export-latex-from-word-step-by-step-guide/)
- [حفظ docx كـ markdown – دليل C# كامل مع معادلات LaTeX](/words/english/net/programming-with-markdownsaveoptions/save-docx-as-markdown-complete-c-guide-with-latex-equations/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}