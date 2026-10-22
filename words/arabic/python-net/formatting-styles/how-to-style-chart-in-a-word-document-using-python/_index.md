---
category: general
date: 2026-08-11
description: كيفية تنسيق المخطط في مستند Word باستخدام Python – تحميل مستند Word باستخدام
  Python وتطبيق نمط مخطط محدد مسبقًا بسرعة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to style chart
- load word document python
- apply predefined chart style
- apply chart style word
language: ar
lastmod: 2026-08-11
og_description: كيفية تنسيق المخطط في مستند Word باستخدام Python. تعلّم كيفية تحميل
  مستند Word باستخدام Python، وتطبيق نمط مخطط محدد مسبقًا، وحفظ الملف المحدث.
og_image_alt: Screenshot of Python code applying a chart style to a Word document
og_title: كيفية تنسيق المخطط في Word باستخدام Python – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-08-11'
  description: How to style chart in a Word document using Python – load Word document
    python and apply predefined chart style quickly.
  headline: How to style chart in a Word document using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Chart styling
- Word automation
title: كيفية تنسيق المخطط في مستند Word باستخدام Python
url: /ar/python/formatting-styles/how-to-style-chart-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تنسيق المخطط في مستند Word باستخدام Python

إذا كنت بحاجة إلى **كيفية تنسيق المخطط** في ملف Word، فإن هذا الدليل يوضح لك الخطوات الدقيقة. بنهاية الجملتين الأوليين ستعرف كيفية تحميل مستند Word باستخدام Python، استخراج المخطط، وتطبيق نمط مخطط مسبق التعريف. هذا الحل يعمل مع مكتبة Aspose.Words for Python ولا يتطلب تعديل يدوي للمستند.

ستتعلم كيفية **load word document python**، اختيار أول شكل مخطط، تعيين نمط مدمج، وحفظ الملف المعدل. يغطي الدليل أيضًا الأخطاء الشائعة، مثل التعامل مع المستندات التي لا تحتوي على مخططات واختيار تعداد النمط الصحيح. لا تحتاج إلى أدوات خارجية بخلاف حزمة Aspose.Words.

## كيفية تنسيق المخطط في مستند Word باستخدام Python

تطبيق نمط على مخطط هو عملية سطر واحد بمجرد حصولك على كائن `Chart`. المكتبة توفر تعداد `ChartStyle`، الذي يحتوي على عشرات من المظاهر المسبقة (Style 1 … Style 50). في هذا القسم نعيّن **Style 5**، لكن يمكنك استبدال قيمة التعداد بأي نمط يتناسب مع إرشادات التصميم الخاصة بك.

```python
import aspose.words as aw

# Load the Word document that contains a chart
doc = aw.Document("YOUR_DIRECTORY/input.docx")

# Retrieve the first chart shape in the document
chart_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
chart = chart_shape.as_chart()

# Apply a predefined chart style (Style 5) to the chart
chart.style = aw.drawing.ChartStyle.STYLE_5

# Save the modified document
doc.save("YOUR_DIRECTORY/output.docx")
```

**لماذا يعمل هذا:**  
* `aw.Document` يقوم بتحليل ملف .docx ويبني نموذج كائنات.  
* `get_child(..., aw.NodeType.SHAPE, ...)` يحدد أول شكل، وهو حاوية المخطط.  
* `as_chart()` يحول الشكل إلى كائن `Chart`، مكشفًا خاصية `style`.  
* تعيين `ChartStyle.STYLE_5` يخبر Aspose.Words باستبدال السمة البصرية للمخطط بالتعريف المسبق.

ملف الإخراج `output.docx` يحتوي على نفس البيانات كما الأصل ولكن مع المخطط المعروض باستخدام النمط المحدد.

## تحميل مستند Word في Python

قبل أن تتمكن من تنسيق مخطط، يجب عليك **load word document python** بشكل صحيح. مُنشئ `aw.Document` يقبل مسارًا إلى ملف .docx أو .doc أو .rtf. تأكد من أن مسار الملف مطلق أو أن دليل العمل يشير إلى موقع ملف الإدخال الخاص بك.

```python
# Example: absolute path on Windows
doc_path = r"C:\Projects\Charts\input.docx"
doc = aw.Document(doc_path)
```

**نصائح لتحميل المستندات:**

* استخدم السلاسل الخام (`r"..."`) على نظام Windows لتجنب هروب الشرطات المائلة.  
* تحقق من وجود الملف باستخدام `os.path.isfile(doc_path)` لتفادي أخطاء وقت التشغيل.  
* إذا كان المستند يحتوي على أقسام محمية، قدم كلمة المرور عبر `aw.LoadOptions`.

```python
import os
if not os.path.isfile(doc_path):
    raise FileNotFoundError(f"Document not found: {doc_path}")
```

## تطبيق نمط مخطط مسبق التعريف

خطوة **apply predefined chart style** هي المكان الذي يحدث فيه التحول البصري. Aspose.Words تعرف تعداد `ChartStyle` بقيم تتراوح من `STYLE_1` إلى `STYLE_50`. كل نمط يطابق مجموعة من الألوان، العلامات، وتنسيقات الخط التي تحاكي سمات المخططات المدمجة في Microsoft Office.

```python
# Choose any style from STYLE_1 to STYLE_50
desired_style = aw.drawing.ChartStyle.STYLE_12
chart.style = desired_style
```

**متى تستخدم نمطًا مسبقًا:**  

* تحتاج إلى مظهر موحد عبر مستندات متعددة.  
* تتغير بيانات المخطط بشكل متكرر، لكن السمة البصرية يجب أن تظل ثابتة.  
* تريد تجنب التنسيق اليدوي في واجهة Word.

**حالة حافة – مستند بدون مخططات:**  
إذا أعاد `doc.get_child(aw.NodeType.SHAPE, 0, True)` القيمة `None`، سيثير السكربت خطأ `AttributeError`. احمِ نفسك من ذلك بالتحقق من نوع العقدة قبل التحويل.

```python
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
if shape is None or not shape.has_chart:
    raise ValueError("No chart found in the document.")
chart = shape.as_chart()
```

## حفظ المستند المنسق

بعد التنسيق، حفظ التغييرات أمر بسيط. طريقة `doc.save` تكتب نموذج الكائنات المحدث إلى ملف .docx. يمكنك أيضًا تصديره إلى صيغ أخرى مثل PDF أو HTML أو PNG إذا كان الاستهلاك اللاحق يتطلب تمثيلًا مختلفًا.

```python
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)          # Saves as DOCX
doc.save("output.pdf")         # Optional: export to PDF
```

**التحقق:** افتح `output.docx` في Microsoft Word. يجب أن يعرض المخطط السمة الجديدة، وتظل أي سلاسل بيانات تحتفظ بالقيم الأصلية. إذا صدرت إلى PDF، يبقى النمط البصري متطابقًا.

## الأخطاء الشائعة والنصائح العملية

| المشكلة | السبب | الحل |
|-------|-------|-----|
| `AttributeError: 'NoneType' object has no attribute 'as_chart'` | لم يتم العثور على شكل مخطط في الفهرس 0 | استخدم `doc.get_child(..., 0, True)` داخل كتلة try/except أو كرّر عبر جميع الأشكال باستخدام `doc.get_child_nodes(aw.NodeType.SHAPE, True)`. |
| تطبيق نمط خاطئ | استخدام قيمة تعداد غير موجودة (مثل `STYLE_0`) | اختر قيمة `ChartStyle` صالحة (1‑50). |
| الملف غير محفوظ | مسار الإخراج يشير إلى دليل للقراءة فقط | تأكد من أن العملية تملك صلاحيات كتابة أو غيّر الدليل. |
| اختفاء المخطط بعد الحفظ | الشكل لم يكن مخططًا (مثل صورة) | تحقق من `shape.has_chart` قبل التحويل. |

**نصيحة احترافية:** خزن `ChartStyle` الذي تستخدمه غالبًا في ثابت لتتمكن من إعادة استخدامه عبر سكربتات متعددة دون الحاجة لكتابة التعداد في كل مرة.

```python
DEFAULT_CHART_STYLE = aw.drawing.ChartStyle.STYLE_5
chart.style = DEFAULT_CHART_STYLE
```

## مثال كامل من البداية إلى النهاية

فيما يلي السكربت الكامل القابل للتنفيذ والذي يدمج جميع الممارسات المثلى التي نوقشت أعلاه. استبدل `YOUR_DIRECTORY` بالمجلد الفعلي الذي يحتوي على ملفات Word الخاصة بك.

```python
import os
import aspose.words as aw

# ----------------------------------------------------------------------
# Configuration
# ----------------------------------------------------------------------
INPUT_PATH = r"YOUR_DIRECTORY/input.docx"
OUTPUT_PATH = r"YOUR_DIRECTORY/output.docx"
DEFAULT_STYLE = aw.drawing.ChartStyle.STYLE_5

# ----------------------------------------------------------------------
# Load the document
# ----------------------------------------------------------------------
if not os.path.isfile(INPUT_PATH):
    raise FileNotFoundError(f"Input file not found: {INPUT_PATH}")

doc = aw.Document(INPUT_PATH)

# ----------------------------------------------------------------------
# Locate the first chart
# ----------------------------------------------------------------------
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
if shape is None or not shape.has_chart:
    raise ValueError("No chart shape found in the document.")

chart = shape.as_chart()

# ----------------------------------------------------------------------
# Apply the predefined chart style
# ----------------------------------------------------------------------
chart.style = DEFAULT_STYLE

# ----------------------------------------------------------------------
# Save the modified document
# ----------------------------------------------------------------------
doc.save(OUTPUT_PATH)

print(f"Chart style applied successfully. Saved to {OUTPUT_PATH}")
```

**النتيجة المتوقعة:**  
عند فتح `output.docx`، سيظهر المخطط الأول بالسمة البصرية المحددة بـ `STYLE_5`. جميع نقاط البيانات، المحاور، والأساطير تظل دون تغيير، مما يثبت أن التنسيق مستقل عن البيانات الأساسية.

## الخلاصة

أنت الآن تعرف **كيفية تنسيق المخطط** في مستند Word باستخدام Python. غطى الدليل كيفية **load word document python**، استخراج شكل المخطط، **apply predefined chart style**، وحفظ الملف المحدث. باستخدام هذه اللبنات يمكنك أتمتة إنشاء التقارير، فرض هوية الشركة، أو معالجة مئات المستندات دفعيًا دون جهد يدوي.

بعد ذلك، استكشف تخصيصات أخرى للمخطط مثل تغيير ألوان السلاسل، إضافة تسميات البيانات، أو تصدير المخطط كصورة. اطلع على وثائق Aspose.Words لمواضيع مثل **apply chart style word**، **chart data manipulation**، و**document conversion** لتوسيع قدرات الأتمتة لديك.

لا تتردد في تجربة قيم `ChartStyle` مختلفة ودمج هذا السكربت في خطوط أنابيب أكبر تُنشئ تقارير Word من قواعد البيانات أو الـ APIs. برمجة سعيدة!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم استعراضها في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insert Simple Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-simple-column-chart/)
- [Insert Area Chart Into A Word Document](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}