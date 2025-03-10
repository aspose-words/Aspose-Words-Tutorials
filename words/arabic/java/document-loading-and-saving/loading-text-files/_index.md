---
title: تحميل ملفات النصوص باستخدام Aspose.Words لـ Java
linktitle: تحميل ملفات النصوص باستخدام
second_title: واجهة برمجة تطبيقات معالجة المستندات في Java Aspose.Words
description: اكتشف قوة Aspose.Words للغة Java. تعلم كيفية تحميل المستندات النصية وإدارة القوائم والتعامل مع المسافات والتحكم في اتجاه النص.
weight: 13
url: /ar/java/document-loading-and-saving/loading-text-files/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تحميل ملفات النصوص باستخدام Aspose.Words لـ Java


## مقدمة لتحميل ملفات النصوص باستخدام Aspose.Words لـ Java

في هذا الدليل، سنستكشف كيفية تحميل ملفات نصية باستخدام Aspose.Words for Java ومعالجتها كمستندات Word. وسنغطي جوانب مختلفة مثل اكتشاف القوائم ومعالجة المسافات والتحكم في اتجاه النص.

## الخطوة 1: اكتشاف القوائم

لتحميل مستند نصي واكتشاف القوائم، يمكنك اتباع الخطوات التالية:

```java
// إنشاء مستند نص عادي في شكل سلسلة تحتوي على أجزاء يمكن تفسيرها كقوائم.
// عند التحميل، سيتم دائمًا اكتشاف القوائم الثلاث الأولى بواسطة Aspose.Words،
// وسيتم إنشاء قائمة الكائنات لهم بعد التحميل.
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
//القائمة الرابعة، مع وجود مسافة بيضاء بين رقم القائمة ومحتويات عناصر القائمة،
// سيتم اكتشافه كقائمة فقط إذا تم تعيين "DetectNumberingWithWhitespaces" في كائن LoadOptions على true،
// لتجنب اكتشاف الفقرات التي تبدأ بأرقام عن طريق الخطأ على أنها قوائم.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// قم بتحميل المستند أثناء تطبيق LoadOptions كمعلمة وتحقق من النتيجة.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

 يوضح هذا الكود كيفية تحميل مستند نصي بتنسيقات قائمة مختلفة واستخدام`DetectNumberingWithWhitespaces` خيار لاكتشاف القوائم بشكل صحيح.

## الخطوة 2: التعامل مع خيارات المسافات

للتحكم بالمسافات البادئة واللاحقة عند تحميل مستند نصي، يمكنك استخدام الكود التالي:

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

 في هذا المثال، نقوم بتحميل مستند نصي وتقليص المسافات البادئة واللاحقة باستخدام`TxtLeadingSpacesOptions.TRIM` و`TxtTrailingSpacesOptions.TRIM`.

## الخطوة 3: التحكم في اتجاه النص

لتحديد اتجاه النص عند تحميل مستند نصي، يمكنك استخدام الكود التالي:

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

يضبط هذا الرمز اتجاه المستند للكشف التلقائي (`DocumentDirection.AUTO`ويحمل مستندًا نصيًا بنص عبري. يمكنك ضبط اتجاه المستند حسب الحاجة.

## الكود المصدر الكامل لتحميل ملفات النصوص باستخدام Aspose.Words لـ Java

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// إنشاء مستند نص عادي في شكل سلسلة تحتوي على أجزاء يمكن تفسيرها كقوائم.
	// عند التحميل، سيتم دائمًا اكتشاف القوائم الثلاث الأولى بواسطة Aspose.Words،
	// وسيتم إنشاء قائمة الكائنات لهم بعد التحميل.
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
	// القائمة الرابعة، مع وجود مسافة بيضاء بين رقم القائمة ومحتويات عنصر القائمة،
	// سيتم اكتشافه كقائمة فقط إذا تم تعيين "DetectNumberingWithWhitespaces" في كائن LoadOptions على true،
	// لتجنب اكتشاف الفقرات التي تبدأ بأرقام عن طريق الخطأ على أنها قوائم.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// قم بتحميل المستند أثناء تطبيق LoadOptions كمعلمة وتحقق من النتيجة.
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

## خاتمة

في هذا الدليل، استكشفنا كيفية تحميل ملفات نصية باستخدام Aspose.Words for Java، واكتشاف القوائم، والتعامل مع المسافات، والتحكم في اتجاه النص. تتيح لك هذه التقنيات التعامل مع المستندات النصية بفعالية في تطبيقات Java.

## الأسئلة الشائعة

### ما هو Aspose.Words لـ Java؟

Aspose.Words for Java هي مكتبة معالجة مستندات قوية تتيح للمطورين إنشاء مستندات Word ومعالجتها وتحويلها برمجيًا في تطبيقات Java. وهي توفر مجموعة واسعة من الميزات للعمل مع النصوص والجداول والصور وعناصر المستندات الأخرى.

### كيف يمكنني البدء باستخدام Aspose.Words لـ Java؟

للبدء في استخدام Aspose.Words لـ Java، اتبع الخطوات التالية:
1. قم بتنزيل وتثبيت مكتبة Aspose.Words for Java.
2.  راجع الوثائق الموجودة في[مرجع API لـ Aspose.Words لـ Java](https://reference.aspose.com/words/java/) للحصول على معلومات مفصلة وأمثلة.
3. استكشف التعليمات البرمجية والدروس التعليمية لتعلم كيفية استخدام المكتبة بشكل فعال.

### كيف أقوم بتحميل مستند نصي باستخدام Aspose.Words لـ Java؟

 لتحميل مستند نصي باستخدام Aspose.Words for Java، يمكنك استخدام`TxtLoadOptions` الصف و`Document` تأكد من تحديد الخيارات المناسبة للتعامل مع المسافات واتجاه النص حسب الحاجة. راجع الدليل خطوة بخطوة في هذه المقالة للحصول على مثال مفصل.

### هل يمكنني تحويل مستند نصي محمل إلى تنسيقات أخرى؟

 نعم، يتيح لك Aspose.Words for Java تحويل مستند نصي محمل إلى تنسيقات مختلفة، بما في ذلك DOCX وPDF والمزيد. يمكنك استخدام`Document` فئة لإجراء التحويلات. راجع الوثائق للحصول على أمثلة تحويل محددة.

### كيف أتعامل مع المسافات في المستندات النصية المحملة؟

 يمكنك التحكم في كيفية التعامل مع المسافات البادئة واللاحقة في مستندات النصوص المحملة باستخدام`TxtLoadOptions` . خيارات مثل`TxtLeadingSpacesOptions` و`TxtTrailingSpacesOptions`تسمح لك بقص المساحات أو الحفاظ عليها حسب الحاجة. راجع قسم "خيارات التعامل مع المساحات" في هذا الدليل للحصول على مثال.

### ما هي أهمية اتجاه النص في Aspose.Words لـ Java؟

يعد اتجاه النص أمرًا ضروريًا للمستندات التي تحتوي على نصوص أو لغات مختلطة، مثل العبرية أو العربية. يوفر Aspose.Words for Java خيارات لتحديد اتجاه النص، مما يضمن عرض النص وتنسيقه بشكل صحيح بهذه اللغات. يوضح قسم "التحكم في اتجاه النص" في هذا الدليل كيفية تعيين اتجاه النص.

### أين يمكنني العثور على المزيد من الموارد والدعم لـ Aspose.Words for Java؟

 للحصول على موارد إضافية ووثائق ودعم، قم بزيارة[توثيق Aspose.Words للغة Java](https://reference.aspose.com/words/java/)يمكنك أيضًا المشاركة في منتديات مجتمع Aspose.Words أو الاتصال بدعم Aspose للحصول على المساعدة بشأن مشكلات أو استفسارات محددة.

### هل Aspose.Words for Java مناسب للمشاريع التجارية؟

نعم، يعد برنامج Aspose.Words for Java مناسبًا للمشروعات الشخصية والتجارية على حدٍ سواء. فهو يوفر خيارات ترخيص لاستيعاب سيناريوهات الاستخدام المختلفة. تأكد من مراجعة شروط الترخيص والأسعار على موقع Aspose على الويب لاختيار الترخيص المناسب لمشروعك.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
