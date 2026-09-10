---
date: 2025-12-20
description: تعلم كيفية تحميل HTML وتحويل HTML إلى DOCX باستخدام Aspose.Words للغة
  Java. يوضح الدليل خطوة بخطوة كيفية حفظ ملفات DOCX واستخدام علامات المستند المهيكلة.
linktitle: Loading and Saving HTML Documents
second_title: Aspose.Words Java Document Processing API
title: كيفية تحميل HTML وحفظه كملف DOCX باستخدام Aspose.Words للـ Java
url: /ar/java/document-loading-and-saving/loading-and-saving-html-documents/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تحميل HTML وحفظه كملف DOCX باستخدام Aspose.Words for Java

## مقدمة حول تحميل وحفظ مستندات HTML باستخدام Aspose.Words for Java

في هذه المقالة، سنستكشف **كيفية تحميل HTML** وحفظه كملف DOCX باستخدام مكتبة Aspose.Words for Java. Aspose.Words هي API قوية تتيح لك معالجة مستندات Word برمجيًا، وتضم دعمًا قويًا لاستيراد/تصدير HTML. سنستعرض العملية بالكامل، من إعداد خيارات التحميل إلى حفظ النتيجة كمستند Word.

## إجابات سريعة
- **ما هو الصنف الأساسي لتحميل HTML؟** `Document` مع `HtmlLoadOptions`.
- **أي خيار يفعّل Structured Document Tags؟** `HtmlLoadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG)`.
- **هل يمكنني تحويل HTML إلى DOCX في خطوة واحدة؟** نعم – قم بتحميل HTML واستدعِ `doc.save(...".docx")`.
- **هل أحتاج إلى ترخيص للتطوير؟** النسخة التجريبية المجانية تكفي للاختبار؛ يلزم ترخيص تجاري للإنتاج.
- **ما نسخة Java المطلوبة؟** Java 8 أو أعلى مدعومة.

## ما هو “كيفية تحميل HTML” في سياق Aspose.Words؟

تحميل HTML يعني قراءة سلسلة أو ملف HTML وتحويله إلى كائن `Document` من Aspose.Words. يمكن بعد ذلك تعديل هذا الكائن أو تنسيقه أو حفظه بأي تنسيق يدعمه الـ API، مثل DOCX أو PDF أو RTF.

## لماذا نستخدم Aspose.Words لتحويل HTML إلى DOCX؟

- **يحافظ على التخطيط** – الجداول والقوائم والصور تبقى كما هي.
- **يدعم Structured Document Tags** – مثالي لإنشاء عناصر تحكم المحتوى في Word.
- **لا يتطلب Microsoft Office** – يعمل على أي خادم أو بيئة سحابية.
- **أداء عالي** – يعالج ملفات HTML الكبيرة بسرعة.

## المتطلبات المسبقة

1. **مكتبة Aspose.Words for Java** – قم بتنزيلها من [here](https://releases.aspose.com/words/java/).
2. **بيئة تطوير Java** – JDK 8+ مثبتة ومُكوَّنة.
3. **إلمام أساسي بـ Java I/O** – سنستخدم `ByteArrayInputStream` لتغذية سلسلة HTML.

## كيفية تحميل مستندات HTML

فيما يلي مثال مختصر يوضح تحميل مقطع HTML مع تفعيل ميزة **structured document tag**.

```java
final String HTML = "\r\n
					<html>\r\n
					<select name='ComboBox' size='1'>\r\n
					<option value='val1'>item1</option>\r\n
					<option value='val2'></option>\r\n
					</select>\r\n
					</html>\r\n";

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
{
    loadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG);
}

Document doc = new Document(new ByteArrayInputStream(HTML.getBytes(StandardCharsets.UTF_8)), loadOptions);
```

**شرح**

- نقوم بإنشاء سلسلة `HTML` تحتوي على عنصر تحكم `<select>` بسيط.
- `HtmlLoadOptions` يتيح لنا تحديد كيفية تفسير HTML. ضبط نوع التحكم المفضَّل إلى `STRUCTURED_DOCUMENT_TAG` يُخبر Aspose.Words بتحويل عناصر تحكم النماذج في HTML إلى عناصر تحكم محتوى في Word.
- مُنشئ `Document` يقرأ HTML من `ByteArrayInputStream` باستخدام ترميز UTF‑8.

## كيفية الحفظ كملف DOCX (تحويل HTML إلى DOCX)

بعد تحميل HTML إلى كائن `Document`، يصبح حفظه كملف DOCX أمرًا بسيطًا:

```java
doc.save("Your Directory Path" + "WorkingWithHtmlLoadOptions.PreferredControlType.docx");
```

استبدل `"Your Directory Path"` بالمجلد الفعلي الذي تريد ظهور ملف الإخراج فيه.

## الكود الكامل لتحميل وحفظ مستندات HTML

فيما يلي المثال الكامل الجاهز للتنفيذ والذي يجمع بين خطوات التحميل والحفظ. لا تتردد في نسخه ولصقه في بيئة التطوير المتكاملة الخاصة بك.

```java
final String HTML = "\r\n
					<html>\r\n
					<select name='ComboBox' size='1'>\r\n
					<option value='val1'>item1</option>\r\n
					<option value='val2'></option>\r\n
					</select>\r\n
					</html>\r\n";
HtmlLoadOptions loadOptions = new HtmlLoadOptions();
{
	loadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG);
}
Document doc = new Document(new ByteArrayInputStream(HTML.getBytes(StandardCharsets.UTF_8)), loadOptions);
doc.save("Your Directory Path" + "WorkingWithHtmlLoadOptions.PreferredControlType.docx");
```

## الأخطاء الشائعة والنصائح

| المشكلة | لماذا يحدث | كيفية الإصلاح |
|-------|----------------|------------|
| **خطوط مفقودة** | HTML يشير إلى خطوط غير مثبتة على الخادم. | دمج الخطوط في DOCX باستخدام `FontSettings` أو التأكد من توفر الخطوط المطلوبة. |
| **الصور غير معروضة** | لا يمكن حل مسارات الصور النسبية. | استخدم عناوين URL مطلقة أو حمّل الصور إلى `MemoryStream` واضبط `HtmlLoadOptions.setImageSavingCallback`. |
| **نوع التحكم غير محوَّل** | `setPreferredControlType` غير مضبوطة أو مضبوطة على enum غير صحيح. | تحقق من أنك تستخدم `HtmlControlType.STRUCTURED_DOCUMENT_TAG`. |
| **مشكلات الترميز** | سلسلة HTML مشفرة بترميز مختلف. | استخدم دائمًا `StandardCharsets.UTF_8` عند تحويل السلسلة إلى بايتات. |

## الأسئلة المتكررة

### كيف أقوم بتثبيت Aspose.Words for Java؟

يمكن تنزيل Aspose.Words for Java من [here](https://releases.aspose.com/words/java/). اتبع دليل التثبيت على صفحة التحميل لإضافة ملفات JAR إلى مسار الفئة (classpath) في مشروعك.

### هل يمكنني تحميل مستندات HTML معقدة باستخدام Aspose.Words؟

نعم، يمكن لـ Aspose.Words for Java معالجة HTML معقد، بما في ذلك الجداول المتداخلة، وتنسيق CSS، والعناصر التفاعلية الخالية من JavaScript. اضبط `HtmlLoadOptions` (مثل `setLoadImages` أو `setCssStyleSheetFileName`) لتحسين عملية الاستيراد.

### ما هي صيغ المستندات الأخرى التي يدعمها Aspose.Words؟

يدعم Aspose.Words الصيغ DOC و DOCX و RTF و HTML و PDF و EPUB و XPS والعديد غيرها. يتيح الـ API حفظًا بسطر واحد إلى أي من هذه الصيغ.

### هل Aspose.Words مناسب لأتمتة المستندات على مستوى المؤسسات؟

بالتأكيد. يستخدمه كبار المؤسسات لتوليد التقارير تلقائيًا، وتحويل المستندات بالجملة، ومعالجة المستندات على الخادم دون الاعتماد على Microsoft Office.

### أين يمكنني العثور على مزيد من الوثائق والأمثلة لـ Aspose.Words for Java؟

يمكنك استكشاف مرجع الـ API الكامل ومزيد من الدروس على موقع وثائق Aspose.Words for Java: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

---

**آخر تحديث:** 2025-12-20  
**تم الاختبار مع:** Aspose.Words for Java 24.12 (أحدث نسخة وقت الكتابة)  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}