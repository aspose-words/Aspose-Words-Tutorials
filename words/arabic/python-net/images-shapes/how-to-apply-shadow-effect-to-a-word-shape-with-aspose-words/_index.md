---
category: general
date: 2026-09-21
description: تعلم كيفية تطبيق تأثير الظل على شكل في Word باستخدام Aspose.Words للغة
  Python. يوضح هذا الدليل كيفية إضافة الظل، وتعيين لون الظل، وحفظ المستند المعدل.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- apply shadow effect
- how to add shadow
- add shadow to shape
- set shadow color
- save edited document
language: ar
lastmod: 2026-09-21
og_description: تطبيق تأثير الظل على شكل Word باستخدام Aspose.Words للغة Python. اتبع
  الدليل خطوة بخطوة لإضافة الظل، وتحديد لون الظل، وحفظ المستند المعدل بكفاءة.
og_image_alt: Screenshot of a Word document showing a shape with a custom shadow applied
  via Aspose.Words Python code
og_title: تطبيق تأثير الظل على شكل Word باستخدام Aspose.Words في Python
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to apply shadow effect to a Word shape using Aspose.Words
    for Python. This guide shows how to add shadow, set shadow color, and save edited
    document.
  headline: How to apply shadow effect to a Word shape with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- shadow effect
title: كيفية تطبيق تأثير الظل على شكل Word باستخدام Aspose.Words
url: /ar/python/images-shapes/how-to-apply-shadow-effect-to-a-word-shape-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تطبيق تأثير الظل على شكل Word باستخدام Aspose.Words

إذا كنت بحاجة إلى **تطبيق تأثير الظل** على شكل في مستند Word، فإن هذا الدليل يوضح لك الطريقة بالضبط. باستخدام Aspose.Words for Python يمكنك **إضافة ظل إلى الشكل**، التحكم في **تعيين لون الظل**، و**حفظ المستند المعدل** دون الحاجة إلى فتح Word يدويًا.

في الأقسام أدناه ستتعلم سير العمل الكامل — من تحميل ملف .docx، استرجاع الشكل المستهدف، ضبط خصائص الظل، إلى كتابة النتيجة مرة أخرى إلى القرص. لا تحتاج إلى أدوات خارجية، والكود يعمل مع Aspose.Words 23.9 أو أحدث.

## المتطلبات السابقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* Python 3.8 أو أحدث مثبت.
* ترخيص فعال لـ Aspose.Words for Python (أو مفتاح تقييم مجاني).
* ملف Word (`input.docx`) يحتوي على شكل واحد على الأقل (مثل مستطيل أو صورة).

يمكنك تثبيت المكتبة باستخدام pip:

```bash
pip install aspose-words
```

## الخطوة 1: تحميل مستند Word

الخطوة الأولى في **كيفية إضافة ظل** هي فتح الملف المصدر. تمثل Aspose.Words المستند باستخدام الفئة `Document`.

```python
# Import the Aspose.Words library
import aspose.words as aw

# Load the Word document from the local folder
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

*لماذا هذا مهم:* تحميل الملف ينشئ نموذج كائن في الذاكرة يمكنك التلاعب به برمجياً. تُتيح لك نسخة `Document` الوصول إلى كل عقدة، بما في ذلك الأشكال.

## الخطوة 2: استرجاع الشكل الذي تريد تعديله

يمكن أن يحتوي مستند Word على العديد من الأشكال. للتبسيط، يلتقط هذا المثال **أول شكل** (الفهرس 0). إذا كنت بحاجة إلى شكل محدد، يمكنك التكرار عبر `doc.get_child_nodes`.

```python
# Retrieve the first shape in the document hierarchy
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
```

*نصيحة:* استخدم `True` للمعامل `isDeep` للبحث في شجرة المستند بالكامل، وليس فقط في الأطفال المباشرين.

## الخطوة 3: ضبط مظهر ظل الشكل

الآن **نضيف ظلًا إلى الشكل** ونضبط خصائصه البصرية. يتحكم كائن `Shadow` في الضبابية، الإزاحات، واللون.

```python
# Configure shadow blur (softness)
shape.shadow.blur = 5.0               # Higher value = softer shadow

# Set horizontal and vertical offsets
shape.shadow.offset_x = 2.0           # Moves shadow right
shape.shadow.offset_y = 2.0           # Moves shadow down

# Set the shadow color – this is the **set shadow color** step
shape.shadow.color = aw.Color.black   # You can use any aw.Color (e.g., aw.Color.red)
```

### لماذا هذه الإعدادات؟

* **Blur** يحدد مدى انتشار الظل. القيمة `5.0` تعطي مظهرًا ناعمًا واحترافيًا.
* **OffsetX/Y** يغيران موقع الظل بالنسبة للشكل، مما يخلق عمقًا.
* **Color** يتيح لك مطابقة العلامة التجارية أو إرشادات التصميم. استخدام `aw.Color.black` هو الإعداد الافتراضي الآمن، لكن أي لون RGB يعمل.

يمكنك تجربة خصائص أخرى مثل `shape.shadow.opacity` (نطاق 0‑1) للحصول على ظلال شبه شفافة.

## الخطوة 4: حفظ المستند المعدل

بعد تطبيق الظل، يجب **حفظ المستند المعدل** لتثبيت التغييرات. تقوم Aspose.Words بكتابة الملف بنفس الصيغة التي تم تحميله بها، ما لم تحدد صيغة مختلفة.

```python
# Save the document with the updated shape
doc.save("YOUR_DIRECTORY/output.docx")
```

*النتيجة:* فتح `output.docx` في Microsoft Word سيظهر الشكل الأصلي الآن مع ظل أسود، مائل قليلاً.

## مثال كامل قابل للتنفيذ

جمع جميع الخطوات معًا يمنحك سكريبتًا واحدًا يمكنك نسخه ولصقه وتشغيله:

```python
# ------------------------------------------------------------
# Apply shadow effect to a shape in a Word document using
# Aspose.Words for Python. This script demonstrates:
#   • how to add shadow
#   • add shadow to shape
#   • set shadow color
#   • save edited document
# ------------------------------------------------------------

import aspose.words as aw

# 1️⃣ Load the source document
doc = aw.Document("YOUR_DIRECTORY/input.docx")

# 2️⃣ Get the first shape (change the index if needed)
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# 3️⃣ Apply shadow settings
shape.shadow.blur = 5.0               # Soft shadow
shape.shadow.offset_x = 2.0           # Horizontal shift
shape.shadow.offset_y = 2.0           # Vertical shift
shape.shadow.color = aw.Color.black   # Shadow color (black)

# 4️⃣ Write the result back to disk
doc.save("YOUR_DIRECTORY/output.docx")

print("Shadow effect applied and document saved as output.docx")
```

### النتيجة المتوقعة

* يطبع الطرفية: `Shadow effect applied and document saved as output.docx`.
* فتح `output.docx` يظهر الشكل مع ظل أسود ناعم مُزاح بمقدار 2 نقطة أفقيًا وعموديًا.

## أسئلة شائعة وحالات خاصة

| السؤال | الجواب |
|----------|--------|
| **هل يمكنني استهداف شكل محدد بالاسم؟** | نعم. استخدم `doc.get_child_nodes(aw.NodeType.SHAPE, True)` للتكرار ومطابقة `shape.name`. |
| **ماذا لو لم يحتوي المستند على أشكال؟** | سيكون `shape` مساويًا لـ `None`. احمِ الكود: `if shape is None: raise ValueError("No shape found.")`. |
| **كيف أستخدم لون RGB مخصص؟** | أنشئ `aw.Color` باستخدام `aw.Color.from_argb(alpha, red, green, blue)`. مثال: `aw.Color.from_argb(255, 255, 0, 0)` للون أحمر ساطع. |
| **هل الظل مرئي في جميع عارضات Word؟** | الظل جزء من تنسيق الشكل ويظهر في Word، Word Online، ومعظم عارضات الطرف الثالث التي تحترم تنسيق OOXML. |
| **هل يمكنني تطبيق نفس الظل على أشكال متعددة؟** | قم بالتكرار على مجموعة الأشكال واضبط نفس خصائص `shadow` لكل عنصر. |

## نصائح احترافية للاستخدام في الإنتاج

* **المعالجة الدفعية:** غلف السكريبت في دالة تقبل مسارات الإدخال والإخراج، ثم استدعها داخل حلقة لمعالجة عشرات الملفات.
* **الأداء:** إعادة استخدام نسخة `Document` واحدة لتعديلات متعددة يقلل من استهلاك الذاكرة.
* **الترخيص:** عند استخدام ترخيص تجريبي، سيحتوي المستند المحفوظ على علامة مائية. استخدم ترخيصًا صحيحًا لإزالتها.

## الخلاصة

أنت الآن تعرف كيف **تطبق تأثير الظل** على شكل Word باستخدام Aspose.Words for Python، بما في ذلك الخطوات لـ **إضافة ظل إلى الشكل**، **تعيين لون الظل**، و**حفظ المستند المعدل**. مع المثال القابل للتنفيذ الكامل يمكنك دمج تنسيق الظل في أي خط أنابيب توليد مستندات آلي.

**الخطوات التالية:** استكشف خيارات تنسيق أخرى للأشكال مثل الحدود، التوهج، أو الدوران ثلاثي الأبعاد (`shape.line_format`, `shape.rotation`). يمكنك أيضًا دمج هذه التقنية مع دمج البريد في Aspose.Words لإنشاء تقارير مخصصة تحمل نمطًا بصريًا موحدًا.

برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [Add Shadow Effect to Word Shapes – Complete C# Guide](/words/english/net/programming-with-shapes/add-shadow-effect-to-word-shapes-complete-c-guide/)
- [Add shadow to shape in Word – Complete Aspose.Words Guide](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}