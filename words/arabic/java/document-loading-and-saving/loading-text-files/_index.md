---
date: 2025-12-27
description: تعلم كيفية تعيين الاتجاه، تحميل ملفات txt، حذف الفراغات، وتحويل txt إلى
  docx باستخدام Aspose.Words للغة Java.
linktitle: Loading Text Files with
second_title: Aspose.Words Java Document Processing API
title: كيفية تعيين الاتجاه وتحميل ملفات النص باستخدام Aspose.Words للغة Java
url: /ar/java/document-loading-and-saving/loading-text-files/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تعيين الاتجاه وتحميل ملفات النص باستخدام Aspose.Words for Java

## مقدمة حول تحميل ملفات النص باستخدام Aspose.Words for Java

في هذا الدليل، ستكتشف **كيفية تعيين الاتجاه** عند تحميل مستندات النص العادي وتتعرف على طرق عملية لـ **تحميل txt**، **قص المسافات**، و**تحويل txt إلى docx** باستخدام Aspose.Words for Java. سواءً كنت تبني خدمة تحويل مستندات أو تحتاج إلى تحكم دقيق في اكتشاف القوائم، فإن هذا البرنامج التعليمي يمرّ بك عبر كل خطوة مع شروحات واضحة وشيفرة جاهزة للتنفيذ.

## إجابات سريعة
- **كيف يمكنني تعيين اتجاه النص لملف TXT محمّل؟** استخدم `TxtLoadOptions.setDocumentDirection(DocumentDirection.AUTO)` أو حدد `LEFT_TO_RIGHT` / `RIGHT_TO_LEFT`.
- **هل يمكن لـ Aspose.Words اكتشاف القوائم المرقمة في النص العادي؟** نعم – فعّل `DetectNumberingWithWhitespaces` في `TxtLoadOptions`.
- **كيف يمكنني قص المسافات البادئة واللاحقة؟** اضبط `TxtLeadingSpacesOptions.TRIM` و `TxtTrailingSpacesOptions.TRIM`.
- **هل من الممكن تحويل ملف TXT إلى DOCX في سطر واحد؟** حمّل ملف TXT باستخدام `TxtLoadOptions` واستدعِ `Document.save("output.docx")`.
- **ما إصدار Java المطلوب؟** Java 8+ يكفي لـ Aspose.Words 24.x.

## ما هو “كيفية تعيين الاتجاه” في Aspose.Words؟
عندما يحتوي ملف النص على نصوص من اليمين إلى اليسار (مثل العبرية أو العربية)، يجب على المكتبة معرفة ترتيب القراءة. يتيح لك تعداد `DocumentDirection` **تعيين الاتجاه** يدويًا أو السماح لـ Aspose باكتشافه تلقائيًا، مما يضمن تخطيطًا صحيحًا وتنسيقًا ثنائي الاتجاه.

## لماذا نستخدم Aspose.Words لتحميل ملفات TXT؟
- **اكتشاف القوائم بدقة** – يتعامل مع القوائم المرقمة، والقوائم النقطية، والقوائم المفصولة بالمسافات.
- **معالجة المسافات بدقة** – قص أو الحفاظ على المسافات البادئة/اللاحقة.
- **اكتشاف تلقائي لاتجاه النص** – مثالي للمستندات متعددة اللغات.
- **تحويل خطوة واحدة** – حمّل ملف `.txt` واحفظه كـ `.docx` أو `.pdf` أو أي صيغة مدعومة أخرى.

## المتطلبات المسبقة
- Java 8 أو أحدث.
- مكتبة Aspose.Words for Java (أضف تبعية Maven/Gradle أو ملف JAR إلى مشروعك).
- معرفة أساسية بتدفقات I/O في Java.

## دليل خطوة بخطوة

### الخطوة 1: اكتشاف القوائم (كيفية تحميل txt)
لتحميل مستند نصي واكتشاف القوائم تلقائيًا، أنشئ كائنًا من `TxtLoadOptions` وفعل اكتشاف القوائم. يوضح الشيفرة أدناه عدة أنماط قوائم ويفعل الترقيم المدرك للمسافات.

```java
// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
// Upon loading, the first three lists will always be detected by Aspose.Words,
// and List objects will be created for them after loading.
final String TEXT_DOC = "Full stop delimiters:\n" +
        "1. First list item 1\n" +
        "2. First list item 2\n" +
        "3. First list item 3\n\n" +
        "Right bracket delimiters:\n" +
        "1) Second list item 1\n" +
        "2) Second list item 2\n" +
        "3) Second list item 3\n\n" +
        "Bullet delimiters:\n" +
        "• Third list item 1\n" +
        "• Third list item 2\n" +
        "• Third list item 3\n\n" +
        "Whitespace delimiters:\n" +
        "1 Fourth list item 1\n" +
        "2 Fourth list item 2\n" +
        "3 Fourth list item 3";
// The fourth list, with whitespace in between the list number and list item contents,
// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
// to avoid paragraphs that start with numbers being mistakenly detected as lists.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Load the document while applying LoadOptions as a parameter and verify the result.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

> **نصيحة احترافية:** إذا كنت تحتاج فقط إلى اكتشاف القوائم الأساسي، يمكنك تخطي خيار المسافات – سيظل Aspose يتعرف على الأنماط القياسية `1.` و `1)`.

### الخطوة 2: معالجة خيارات المسافات (كيفية قص المسافات)
غالبًا ما تتسبب المسافات البادئة واللاحقة في حدوث تشوهات تنسيقية. استخدم `TxtLeadingSpacesOptions` و `TxtTrailingSpacesOptions` للتحكم في هذا السلوك.

```java
@Test
public void handleSpacesOptions() throws Exception {
    final String TEXT_DOC = "      Line 1 \n" +
            "    Line 2   \n" +
            " Line 3       ";
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
        loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
    }
    Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
```

> **لماذا يهم ذلك:** قص المسافات يمنع المسافات البادئة غير المرغوبة في الـ DOCX الناتج، مما يجعل المستند يبدو نظيفًا دون الحاجة إلى معالجة يدوية لاحقة.

### الخطوة 3: التحكم في اتجاه النص (كيفية تعيين الاتجاه)
لللغات من اليمين إلى اليسار، عيّن اتجاه المستند قبل التحميل. المثال أدناه يحمل ملف نص عبري ويطبع علم الـ bidi لتأكيد الاتجاه.

```java
@Test
public void documentTextDirection() throws Exception {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setDocumentDirection(DocumentDirection.AUTO);
    }
    Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
    Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
    System.out.println(paragraph.getParagraphFormat().getBidi());
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
}
```

> **مشكلة شائعة:** نسيان تعيين `DocumentDirection` قد يؤدي إلى تشويه النص العربي/العبراني حيث تظهر الأحرف بترتيب غير صحيح.

### الشيفرة المصدرية الكاملة لتحميل ملفات النص باستخدام Aspose.Words for Java
فيما يلي الشيفرة الكاملة الجاهزة للتنفيذ التي تجمع بين اكتشاف القوائم، معالجة المسافات، والتحكم في الاتجاه. يمكنك نسخها ولصقها في فئة واحدة وتشغيل طرق الاختبار الثلاثة بشكل منفصل.

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
	// Upon loading, the first three lists will always be detected by Aspose.Words,
	// and List objects will be created for them after loading.
	final String TEXT_DOC = "Full stop delimiters:\n" +
			"1. First list item 1\n" +
			"2. First list item 2\n" +
			"3. First list item 3\n\n" +
			"Right bracket delimiters:\n" +
			"1) Second list item 1\n" +
			"2) Second list item 2\n" +
			"3) Second list item 3\n\n" +
			"Bullet delimiters:\n" +
			"• Third list item 1\n" +
			"• Third list item 2\n" +
			"• Third list item 3\n\n" +
			"Whitespace delimiters:\n" +
			"1 Fourth list item 1\n" +
			"2 Fourth list item 2\n" +
			"3 Fourth list item 3";
	// The fourth list, with whitespace inbetween the list number and list item contents,
	// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
	// to avoid paragraphs that start with numbers being mistakenly detected as lists.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Load the document while applying LoadOptions as a parameter and verify the result.
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
}
@Test
public void handleSpacesOptions() throws Exception {
	final String TEXT_DOC = "      Line 1 \n" +
			"    Line 2   \n" +
			" Line 3       ";
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
		loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
	}
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
@Test
public void documentTextDirection() throws Exception {
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDocumentDirection(DocumentDirection.AUTO);
	}
	Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
	Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
	System.out.println(paragraph.getParagraphFormat().getBidi());
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
	}
```

## المشكلات الشائعة والحلول
| المشكلة | السبب | الحل |
|-------|-------|-----|
| القوائم غير مكتشفة | `DetectNumberingWithWhitespaces` ترك `false` للقوائم المفصولة بالمسافات | فعّل `loadOptions.setDetectNumberingWithWhitespaces(true)` |
| مسافة بادئة إضافية بعد التحميل | تم الحفاظ على المسافات البادئة | اضبط `TxtLeadingSpacesOptions.TRIM` |
| النص العبري يظهر مقلوبًا | لم يتم تعيين اتجاه المستند أو تم تعيينه إلى `LEFT_TO_RIGHT` | استخدم `DocumentDirection.AUTO` أو `RIGHT_TO_LEFT` |
| ملف DOCX الناتج فارغ | لم يتم إعادة تعيين تدفق الإدخال قبل التحميل الثاني | أعد إنشاء `ByteArrayInputStream` لكل استدعاء تحميل |

## الأسئلة المتكررة

### س: ما هو Aspose.Words for Java؟
A: Aspose.Words for Java هي مكتبة معالجة مستندات قوية تسمح للمطورين بإنشاء وتعديل وتحويل مستندات Word برمجيًا في تطبيقات Java. تدعم مجموعة واسعة من الميزات، من تحميل النص البسيط إلى التنسيق المعقد والتحويل.

### س: كيف يمكنني البدء مع Aspose.Words for Java؟
A: 1. قم بتحميل وتثبيت مكتبة Aspose.Words for Java. 2. راجع الوثائق على [Aspose.Words for Java API Reference](https://reference.aspose.com/words/java/) للحصول على معلومات مفصلة وأمثلة. 3. استكشف الشيفرات النموذجية والبرامج التعليمية لتعلم كيفية استخدام المكتبة بفعالية.

### س: كيف يمكنني تحميل مستند نصي باستخدام Aspose.Words for Java؟
A: استخدم الفئة `TxtLoadOptions` مع مُنشئ `Document`. حدد الخيارات مثل اكتشاف القوائم، معالجة المسافات، أو اتجاه النص كما هو موضح في الأقسام خطوة بخطوة أعلاه.

### س: هل يمكنني تحويل مستند نصي محمّل إلى صيغ أخرى؟
A: نعم. بعد تحميل ملف TXT إلى كائن `Document`، استدعِ `doc.save("output.pdf")` أو `doc.save("output.docx")` أو أي صيغة مدعومة أخرى.

### س: كيف يمكنني معالجة المسافات في المستندات النصية المحمّلة؟
A: تحكم في المسافات البادئة واللاحقة باستخدام `TxtLeadingSpacesOptions` و `TxtTrailingSpacesOptions`. اضبطهما على `TRIM` لإزالة المسافات غير المرغوبة، أو على `PRESERVE` إذا كنت تحتاج إلى الحفاظ على التباعد الأصلي.

### س: ما هي أهمية اتجاه النص في Aspose.Words for Java؟
A: يضمن اتجاه النص عرضًا صحيحًا للنصوص من اليمين إلى اليسار (العبرية، العربية، إلخ). من خلال تعيين `DocumentDirection`، تضمن أن يتم عرض النص ثنائي الاتجاه بشكل سليم في المستند الناتج.

### س: أين يمكنني العثور على المزيد من الموارد والدعم لـ Aspose.Words for Java؟
A: زر [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/) للحصول على مراجع API، عينات شيفرة، وأدلة تفصيلية. يمكنك أيضًا الانضمام إلى منتديات مجتمع Aspose أو التواصل مع دعم Aspose لأسئلة محددة.

### س: هل Aspose.Words for Java مناسب للمشاريع التجارية؟
A: نعم. توفر خيارات ترخيص للاستخدام الشخصي والتجاري. راجع شروط الترخيص على موقع Aspose لاختيار الخطة المناسبة لمشروعك.

## الخلاصة
أصبح لديك الآن مجموعة أدوات كاملة لـ **تحميل ملفات txt**، **اكتشاف القوائم**، **قص المسافات**، و**تعيين الاتجاه** عند تحويل النص العادي إلى مستندات Word غنية باستخدام Aspose.Words for Java. طبّق هذه الأنماط لأتمتة سير عمل المستندات، تحسين الدعم متعدد اللغات، وضمان مخرجات نظيفة ومهنية في كل مرة.

---

**آخر تحديث:** 2025-12-27  
**تم الاختبار مع:** Aspose.Words for Java 24.12  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}