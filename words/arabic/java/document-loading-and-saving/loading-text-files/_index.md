---
"description": "اكتشف قوة Aspose.Words في جافا. تعلم كيفية تحميل المستندات النصية، وإدارة القوائم، والتعامل مع المسافات، والتحكم في اتجاه النص."
"linktitle": "تحميل ملفات النصوص مع"
"second_title": "واجهة برمجة تطبيقات معالجة مستندات Java Aspose.Words"
"title": "تحميل ملفات النصوص باستخدام Aspose.Words لـ Java"
"url": "/ar/java/document-loading-and-saving/loading-text-files/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تحميل ملفات النصوص باستخدام Aspose.Words لـ Java


## مقدمة لتحميل ملفات النصوص باستخدام Aspose.Words لـ Java

في هذا الدليل، سنستكشف كيفية تحميل ملفات نصية باستخدام Aspose.Words لجافا ومعالجتها كمستندات وورد. سنغطي جوانب مختلفة، مثل اكتشاف القوائم، ومعالجة المسافات، والتحكم في اتجاه النص.

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
// القائمة الرابعة، مع وجود مسافة بيضاء بين رقم القائمة ومحتويات عناصر القائمة،
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

يوضح هذا الكود كيفية تحميل مستند نصي بتنسيقات قائمة مختلفة واستخدام `DetectNumberingWithWhitespaces` خيار لاكتشاف القوائم بشكل صحيح.

## الخطوة 2: التعامل مع خيارات المسافات

للتحكم في المسافات البادئة واللاحقة عند تحميل مستند نصي، يمكنك استخدام الكود التالي:

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

في هذا المثال، نقوم بتحميل مستند نصي وتقليص المسافات البادئة واللاحقة باستخدام `TxtLeadingSpacesOptions.TRIM` و `TxtTrailingSpacesOptions.TRIM`.

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

يضبط هذا الكود اتجاه المستند إلى الاكتشاف التلقائي (`DocumentDirection.AUTO`) ويُحمّل مستندًا نصيًا بالنص العبري. يمكنك تعديل اتجاه المستند حسب الحاجة.

## كود المصدر الكامل لتحميل ملفات النصوص باستخدام Aspose.Words لـ Java

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
	// القائمة الرابعة، مع وجود مسافة بيضاء بين رقم القائمة ومحتويات عناصر القائمة،
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

في هذا الدليل، استكشفنا كيفية تحميل ملفات النصوص باستخدام Aspose.Words لجافا، واكتشاف القوائم، ومعالجة المسافات، والتحكم في اتجاه النص. تتيح لك هذه التقنيات التعامل مع مستندات النصوص بفعالية في تطبيقات جافا.

## الأسئلة الشائعة

### ما هو Aspose.Words لـ Java؟

Aspose.Words for Java هي مكتبة معالجة مستندات فعّالة، تُمكّن المطورين من إنشاء مستندات Word وتعديلها وتحويلها برمجيًا في تطبيقات Java. وتوفر مجموعة واسعة من الميزات للتعامل مع النصوص والجداول والصور وعناصر المستندات الأخرى.

### كيف يمكنني البدء باستخدام Aspose.Words لـ Java؟

للبدء في استخدام Aspose.Words لـ Java، اتبع الخطوات التالية:
1. قم بتنزيل وتثبيت مكتبة Aspose.Words for Java.
2. راجع الوثائق الموجودة في [مرجع Aspose.Words لواجهة برمجة تطبيقات Java](https://reference.aspose.com/words/java/) لمزيد من المعلومات والأمثلة التفصيلية.
3. استكشف التعليمات البرمجية والدروس التعليمية لمعرفة كيفية استخدام المكتبة بشكل فعال.

### كيف أقوم بتحميل مستند نصي باستخدام Aspose.Words لـ Java؟

لتحميل مستند نصي باستخدام Aspose.Words for Java، يمكنك استخدام `TxtLoadOptions` الصف و `Document` تأكد من تحديد الخيارات المناسبة للتعامل مع المسافات واتجاه النص حسب الحاجة. راجع الدليل التفصيلي في هذه المقالة للاطلاع على مثال مفصل.

### هل يمكنني تحويل مستند نصي محمل إلى تنسيقات أخرى؟

نعم، يتيح لك Aspose.Words for Java تحويل مستند نصي مُحمّل إلى صيغ مختلفة، بما في ذلك DOCX وPDF وغيرها. يمكنك استخدام `Document` فئة لإجراء التحويلات. راجع الوثائق للاطلاع على أمثلة محددة للتحويلات.

### كيف أتعامل مع المسافات في مستندات النصوص المحملة؟

يمكنك التحكم في كيفية التعامل مع المسافات البادئة واللاحقة في مستندات النصوص المحملة باستخدام `TxtLoadOptions`. خيارات مثل `TxtLeadingSpacesOptions` و `TxtTrailingSpacesOptions` يسمح لك بقص المساحات أو الحفاظ عليها حسب الحاجة. راجع قسم "خيارات التعامل مع المساحات" في هذا الدليل للاطلاع على مثال.

### ما هي أهمية اتجاه النص في Aspose.Words لـ Java؟

يُعدّ توجيه النص أمرًا أساسيًا للمستندات التي تحتوي على نصوص أو لغات مختلطة، مثل العبرية أو العربية. يوفر Aspose.Words لجافا خيارات لتحديد اتجاه النص، مما يضمن عرضًا وتنسيقًا سليمين للنص بهذه اللغات. يوضح قسم "التحكم في اتجاه النص" في هذا الدليل كيفية ضبط اتجاه النص.

### أين يمكنني العثور على المزيد من الموارد والدعم لـ Aspose.Words for Java؟

للحصول على موارد إضافية ووثائق ودعم، قم بزيارة [توثيق Aspose.Words لـ Java](https://reference.aspose.com/words/java/)يمكنك أيضًا المشاركة في منتديات مجتمع Aspose.Words أو الاتصال بدعم Aspose للحصول على المساعدة بشأن مشكلات أو استفسارات محددة.

### هل Aspose.Words for Java مناسب للمشاريع التجارية؟

نعم، يُعد Aspose.Words for Java مناسبًا للمشاريع الشخصية والتجارية على حد سواء. يوفر خيارات ترخيص تناسب مختلف سيناريوهات الاستخدام. تأكد من مراجعة شروط الترخيص والأسعار على موقع Aspose الإلكتروني لاختيار الترخيص المناسب لمشروعك.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}