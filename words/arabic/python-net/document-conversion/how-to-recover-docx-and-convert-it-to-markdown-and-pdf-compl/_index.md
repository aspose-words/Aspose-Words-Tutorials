---
category: general
date: 2026-05-30
description: تعلم كيفية استعادة ملفات docx، وتعيين الظل، وتحويل markdown الخاص بـ docx
  إلى كل من markdown و pdf باستخدام Aspose.Words للغة بايثون. يتضمن الشرح كود خطوة
  بخطوة.
draft: false
keywords:
- how to recover docx
- convert docx markdown
- save as markdown
- save as pdf
- how to set shadow
language: ar
og_description: كيفية استعادة ملف docx، تعيين الظل، وحفظه كملف markdown أو pdf باستخدام
  Aspose.Words. دليل كامل للمطورين.
og_title: كيفية استعادة ملف DOCX وتحويله إلى Markdown و PDF – دليل بايثون
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Learn how to recover docx, set shadow, and convert docx markdown to
    both markdown and pdf using Aspose.Words for Python. Step‑by‑step code included.
  headline: How to Recover DOCX and Convert It to Markdown and PDF – Complete Python
    Guide
  type: TechArticle
tags:
- Aspose.Words
- Python
- Document Conversion
title: كيفية استعادة ملف DOCX وتحويله إلى Markdown وPDF – دليل بايثون الكامل
url: /ar/python/document-conversion/how-to-recover-docx-and-convert-it-to-markdown-and-pdf-compl/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية استعادة ملف DOCX وتحويله إلى Markdown و PDF – دليل Python الكامل

هل تساءلت يومًا **كيف تستعيد ملفات docx** التي ترفض الفتح في Word؟ ربما تلقيت تقريرًا تالفًا من عميل، أو أن مهمة دفعة ليلية أنتجت مستندًا غير مكتمل. في تلك اللحظات لا تريد مجرد زر “إعادة المحاولة”—تحتاج إلى طريقة موثوقة لاستخراج الأجزاء الصالحة، تعديل المظهر، ثم تسليم النتيجة بالصيغ التي يستخدمها أصحاب المصلحة فعليًا.

هذا بالضبط ما سنقوم به في هذا الدرس. سنظهر لك كيفية استعادة DOCX، **كيفية إضافة ظل** على الشكل الأول، ثم **تحويل docx إلى markdown**، **حفظه كـ markdown**، وأخيرًا **حفظه كـ pdf**—كل ذلك باستخدام مكتبة Aspose.Words للـ Python القوية. بنهاية الدرس ستحصل على سكريبت واحد يحول ملف Word معطوب إلى مخرجات نظيفة بصيغة Markdown و PDF، مع تأثير ظل خفيف على أي رسومات.

> **نصيحة:** يعمل الكود مع Aspose.Words 22.12 أو أحدث؛ قد تفتقد الإصدارات القديمة بعض علامات التوافق الجديدة مع PDF/UA.

---

## ما ستحتاجه

قبل أن نبدأ، تأكد من وجود ما يلي:

| المتطلبات | السبب |
|-------------|--------|
| Python 3.8+ | بناء جملة حديث وتلميحات نوع |
| `aspose-words` package (`pip install aspose-words`) | المكتبة الأساسية للتحميل، التحرير، والحفظ |
| ملف DOCX (حتى إذا كان تالفًا) | المستند المصدر |
| إلمام أساسي بدوال Python | لمتابعة التدفق بسهولة |

هذا كل شيء—لا تحتاج إلى DLLs إضافية، ولا تثبيت Office، ولا استدعاءات نظام غامضة. تتولى Aspose.Words كل الأعمال الثقيلة داخليًا.

---

## ## كيفية استعادة DOCX والاستمرار في العمل معه

أول شيء يجب القيام به هو تحميل المستند المحتمل الضرر في **وضع الاستعادة**. توفر Aspose.Words فئة `DocumentLoadOptions` حيث يمكنك تفعيل `RecoveryMode`. عندما تُضبط على `RECOVER`، تحاول المكتبة إعادة بناء شجرة العقد الداخلية، متجاهلةً فقط الأجزاء التي لا يمكن إصلاحها.

```python
import aspose.words as aw

# -------------------------------------------------
# Step 1 – Load the DOCX with recovery enabled
# -------------------------------------------------
load_opts = aw.loading.DocumentLoadOptions()
load_opts.recovery_mode = aw.loading.RecoveryMode.RECOVER

# Replace YOUR_DIRECTORY with the real path to your file
doc = aw.Document("YOUR_DIRECTORY/input.docx", load_opts)

print("Document loaded. Nodes recovered:", doc.get_child_nodes(aw.NodeType.ANY, True).get_count())
```

**لماذا هذا مهم:** إذا تخطيت الاستعادة، سيُطلق مُنشئ `Document` استثناءً في اللحظة التي يصادف فيها فسادًا، مما يوقف كامل خط الأنابيب. بتمكين الاستعادة تحصل على كائن `Document` قابل للاستخدام حتى عندما يرفض Word فتح الملف.

---

## ## كيفية إضافة ظل على الشكل الأول

يمكن للظل الخفيف أن يجعل الشعار أو المخطط يبرز، خاصةً عندما تقوم لاحقًا بتصديره إلى PDF/UA حيث تُطبق قواعد إمكانية الوصول. المقتطف التالي يلتقط أول عقدة `Shape` في المستند ويضبط `ShadowFormat` الخاصة بها.

```python
# -------------------------------------------------
# Step 2 – Find the first shape and apply a shadow
# -------------------------------------------------
first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True).as_shape()
shadow = first_shape.shadow_format

# Enable the shadow and tweak its appearance
shadow.visible = True
shadow.distance = 4          # distance of the shadow from the shape (points)
shadow.blur = 6              # blur radius (points)
shadow.color = aw.Color.gray
shadow.opacity = 0.7         # 70% opacity for a soft look

print("Shadow applied to shape:", first_shape.name)
```

**خطأ شائع:** إذا لم يحتوي المستند على أشكال، فإن `get_child` تُعيد `None` ويتعطل السكريبت. يمكن لشرط حماية سريع أن ينقذك:

```python
if first_shape is not None:
    # apply shadow (as above)
else:
    print("No shapes found – skipping shadow step.")
```

---

## ## تحويل DOCX إلى Markdown (حفظ كـ Markdown)

الآن بعد أن أصبح المستند سليمًا وتم تطبيق التعديل البصري، دعنا **نحول docx إلى markdown**. يمكن لـ Aspose.Words تصدير Markdown مع معالجة معادلات Office Math، والتي سنصدرها كـ LaTeX لأقصى درجة من الدقة.

```python
# -------------------------------------------------
# Step 3 – Export to Markdown, preserving Math as LaTeX
# -------------------------------------------------
md_options = aw.saving.MarkdownSaveOptions()
md_options.office_math_export_mode = aw.saving.MarkdownOfficeMathExportMode.LATEX

# Again, replace the path with your desired output location
md_path = "YOUR_DIRECTORY/Combined.md"
doc.save(md_path, md_options)

print("Markdown file saved to:", md_path)
```

**ما ستراه:** يحتوي ملف `.md` الناتج على بناء جملة Markdown عادي للفقرات والعناوين والقوائم، بينما تظهر أي معادلات مدمجة ككتل LaTeX محاطة بـ `$$ … $$`. افتحه في VS Code أو أي عارض Markdown للتحقق.

---

## ## حفظ كـ PDF مع إمكانية الوصول (حفظ كـ PDF)

أخيرًا، سن **نحفظ كـ pdf** مع ضمان أن الأشكال العائمة التي عدلناها سابقًا تُصدَّر كعناصر علامة داخلية. هذا يحافظ على تناسق التخطيط عبر المشاهدين ويحقق توافق PDF/UA 1 مع إمكانية الوصول.

```python
# -------------------------------------------------
# Step 4 – Export to PDF/UA with inline‑tagged floating shapes
# -------------------------------------------------
pdf_options = aw.saving.PdfSaveOptions()
pdf_options.export_floating_shapes_as_inline_tag = True
pdf_options.compliance = aw.saving.PdfCompliance.PDF_UA_1

pdf_path = "YOUR_DIRECTORY/Combined.pdf"
doc.save(pdf_path, pdf_options)

print("PDF file saved to:", pdf_path)
```

**لماذا PDF/UA؟** يضيف PDF/UA (Universal Accessibility) وسومًا يمكن لقارئات الشاشة تفسيرها، مما يجعل مستندك أكثر صداقة للمستخدمين ذوي الإعاقات. كما أن علم `export_floating_shapes_as_inline_tag` يمنع فصل الأشكال عن النص المحيط، وهو مصدر شائع لانحراف التخطيط.

---

## ## السكريبت الكامل – حل شامل

نجمع كل ما سبق في سكريبت جاهز للتنفيذ يغطي **كيفية استعادة docx**، **كيفية إضافة ظل**، **تحويل docx إلى markdown**، **حفظه كـ markdown**، و **حفظه كـ pdf**. انسخه، الصقه، وعدل مسارات الملفات لتتناسب مع بيئتك.

```python
import aspose.words as aw

def recover_and_convert(input_path: str, output_dir: str):
    # ---------- Load with recovery ----------
    load_opts = aw.loading.DocumentLoadOptions()
    load_opts.recovery_mode = aw.loading.RecoveryMode.RECOVER
    doc = aw.Document(input_path, load_opts)
    print(f"Loaded '{input_path}'. Node count:", doc.get_child_nodes(aw.NodeType.ANY, True).get_count())

    # ---------- Apply shadow to first shape ----------
    first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
    if first_shape is not None:
        shape = first_shape.as_shape()
        shadow = shape.shadow_format
        shadow.visible = True
        shadow.distance = 4
        shadow.blur = 6
        shadow.color = aw.Color.gray
        shadow.opacity = 0.7
        print(f"Shadow set on shape '{shape.name}'.")
    else:
        print("No shapes detected – shadow step skipped.")

    # ---------- Save as Markdown ----------
    md_options = aw.saving.MarkdownSaveOptions()
    md_options.office_math_export_mode = aw.saving.MarkdownOfficeMathExportMode.LATEX
    md_path = f"{output_dir}/Combined.md"
    doc.save(md_path, md_options)
    print("Markdown saved at:", md_path)

    # ---------- Save as PDF/UA ----------
    pdf_options = aw.saving.PdfSaveOptions()
    pdf_options.export_floating_shapes_as_inline_tag = True
    pdf_options.compliance = aw.saving.PdfCompliance.PDF_UA_1
    pdf_path = f"{output_dir}/Combined.pdf"
    doc.save(pdf_path, pdf_options)
    print("PDF saved at:", pdf_path)

# Example usage – replace with your actual paths
if __name__ == "__main__":
    recover_and_convert("YOUR_DIRECTORY/input.docx", "YOUR_DIRECTORY")
```

شغّل السكريبت باستخدام `python recover_and_convert.py`. إذا سارت الأمور بسلاسة ستحصل على ملفين في `YOUR_DIRECTORY`:

* **Combined.md** – Markdown نظيف، LaTeX لأي معادلات، والصورة التي تم تحسين ظلها مدمجة كعلامة صورة عادية.
* **Combined.pdf** – PDF متوافق مع PDF/UA، مع الحفاظ على ظل الشكل الأول، والأشكال العائمة مدمجة داخل النص.

---

## ## النتيجة المتوقعة والتحقق

| الملف | ما يجب ملاحظته |
|------|------------------|
| `Combined.md` | عناوين Markdown قياسية (`#`, `##`)، قوائم نقطية، وأي رياضيات تُعرض كـ `$$ … $$`. افتحه في عارض Markdown لتتأكد من التنسيق. |
| `Combined.pdf` | وسوم إمكانية الوصول (استخدم “Read Out Loud” في Adobe Acrobat للاختبار)، يجب أن يظهر الشكل الأول بظل رمادي خفيف، ويجب أن يتطابق التخطيط مع DOCX الأصلي قدر الإمكان. |

إذا فتح PDF دون أخطاء وعرض الـ Markdown بشكل صحيح، فقد نجحت في **استعادة الـ DOCX**، وتطبيق تعديل بصري، وتصديره.

## ما الذي يجب أن تتعلمه بعد ذلك؟

- [كيفية استعادة docx باستخدام Aspose.Words – خطوة بخطوة](/words/english/net/programming-with-loadoptions/how-to-recover-docx-with-aspose-words-step-by-step/)
- [كيفية حفظ Markdown من DOCX – دليل خطوة بخطوة](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)
- [حفظ docx كـ pdf باستخدام Aspose.Words – دليل C# الكامل](/words/english/net/programming-with-pdfsaveoptions/save-docx-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}