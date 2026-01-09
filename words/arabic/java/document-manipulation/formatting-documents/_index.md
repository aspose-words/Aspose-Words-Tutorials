---
date: 2026-01-09
description: تعلم كيفية إنشاء قائمة متعددة المستويات، وتطبيق نمط الفقرة، وضبط محاذاة
  الفقرة، وإنشاء مستندات Word باستخدام Aspose.Words للغة Java. يغطي هذا الدليل تقنيات
  التنسيق للمستندات المهنية.
linktitle: Formatting Documents
second_title: Aspose.Words Java Document Processing API
title: كيفية إنشاء قائمة متعددة المستويات وتنسيق المستندات في Aspose.Words للـ Java
url: /ar/java/document-manipulation/formatting-documents/
weight: 29
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تنسيق المستندات في Aspose.Words for Java

## مقدمة حول تنسيق المستندات في Aspose.Words for Java

في عالم معالجة المستندات بلغة Java، تُعد Aspose.Words for Java أداة قوية ومتعددة الاستخدامات. سواءً كنت تُنشئ تقارير، أو تصمم فواتير، أو تبني تخطيطات معقدة، فستحتاج غالبًا إلى **إنشاء قائمة متعددة المستويات** وتطبيق تنسيقات فقرات متقدمة. في هذا الدليل الشامل، سنستعرض كيفية تنسيق المستندات، وإنشاء مستند Word من الصفر، وضبط محاذاة الفقرات، والمسافة اليسرى، وغيرها من التفاصيل الطباعية. لنبدأ خطوة بخطوة.

## إجابات سريعة
- **كيف يمكنني إنشاء قائمة متعددة المستويات؟** استخدم `DocumentBuilder.getListFormat().applyNumberDefault()` وأضف عناصر القائمة بالتتابع.  
- **هل يمكنني ضبط محاذاة الفقرة؟** نعم، استدعِ `ParagraphFormat.setAlignment(ParagraphAlignment.CENTER)` أو أي محاذاة أخرى.  
- **ما الطريقة التي تضيف مسافة يسار؟** استخدم `ParagraphFormat.setLeftIndent(double)` لتحديد الهامش الأيسر.  
- **كيف يمكنني إنشاء مستند Word برمجيًا؟** أنشئ كائن `Document`، أضف المحتوى باستخدام `DocumentBuilder`، ثم استدعِ `save("MyDoc.docx")`.  
- **هل هناك طريقة لتطبيق نمط فقرة مخصص؟** عيّن معرف النمط عبر `ParagraphFormat.setStyleIdentifier(StyleIdentifier.TITLE)`.

## إعداد بيئتك

قبل الغوص في تفاصيل تنسيق المستندات، من الضروري إعداد بيئتك. تأكد من تثبيت Aspose.Words for Java بشكل صحيح وتكوينه في مشروعك. يمكنك تنزيله من [here](https://releases.aspose.com/words/java/).

## إنشاء مستند بسيط

لنبدأ بـ **إنشاء مستند Word** باستخدام Aspose.Words for Java. يوضح المقتطف البرمجي التالي بلغة Java كيفية إنشاء مستند وإضافة بعض النص إليه:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello, Aspose.Words for Java!");
doc.save("MyDocument.docx");
```

## ضبط المسافة بين النص الآسيوي واللاتيني

توفر Aspose.Words for Java ميزات قوية لمعالجة تباعد النص. يمكنك ضبط المسافة تلقائيًا بين النص الآسيوي واللاتيني كما هو موضح أدناه:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setAddSpaceBetweenFarEastAndAlpha(true);
paragraphFormat.setAddSpaceBetweenFarEastAndDigit(true);
builder.writeln("Automatically adjust space between Asian and Latin text");
builder.writeln("Automatically adjust space between Asian text and numbers");
doc.save("SpaceBetweenAsianAndLatinText.docx");
```

## العمل مع الطباعة الآسيوية

للتحكم في إعدادات الطباعة الآسيوية، راجع المقتطف البرمجي التالي:

```java
Document doc = new Document("AsianTypography.docx");
ParagraphFormat format = doc.getFirstSection().getBody().getParagraphs().get(0).getParagraphFormat();
format.setFarEastLineBreakControl(false);
format.setWordWrap(true);
format.setHangingPunctuation(false);
doc.save("AsianTypographyLineBreakGroup.docx");
```

## تنسيق الفقرات

تتيح لك Aspose.Words for Java **ضبط محاذاة الفقرة**، **تحديد المسافة اليسرى**، وتنسيق الفقرات بسهولة. إليك مثالًا:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setAlignment(ParagraphAlignment.CENTER);
paragraphFormat.setLeftIndent(50.0);
paragraphFormat.setRightIndent(50.0);
paragraphFormat.setSpaceAfter(25.0);
builder.writeln("I'm a very nice formatted paragraph. I'm intended to demonstrate how the left and right indents affect word wrapping.");
builder.writeln("I'm another nice formatted paragraph. I'm intended to demonstrate how the space after paragraph looks like.");
doc.save("ParagraphFormatting.docx");
```

## تنسيق القوائم متعددة المستويات

إنشاء هياكل **قائمة متعددة المستويات** هو طلب شائع في تنسيق المستندات. تُبسّط Aspose.Words for Java هذه العملية:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.getListFormat().applyNumberDefault();
builder.writeln("Item 1");
// Add more items here...
doc.save("MultilevelListFormatting.docx");
```

## تطبيق أنماط الفقرات

تسمح لك Aspose.Words for Java **بتطبيق نمط الفقرة** بسهولة:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.TITLE);
builder.write("Hello, Styled Paragraph!");
doc.save("ApplyParagraphStyle.docx");
```

## إضافة حدود وتظليل للفقرات

عزّز المظهر البصري لمستندك بإضافة حدود وتظليل:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
BorderCollection borders = builder.getParagraphFormat().getBorders();
// Customize borders here...
Shading shading = builder.getParagraphFormat().getShading();
// Customize shading here...
builder.write("I'm a formatted paragraph with double border and nice shading.");
doc.save("ApplyBordersAndShadingToParagraph.docx");
```

## تعديل تباعد الفقرات والمسافات للغة الآسيوية

قم بضبط تباعد الفقرات والمسافات للنص الآسيوي بدقة:

```java
Document doc = new Document("AsianTypography.docx");
ParagraphFormat format = doc.getFirstSection().getBody().getFirstParagraph().getParagraphFormat();
format.setCharacterUnitLeftIndent(10.0);
format.setCharacterUnitRightIndent(10.0);
format.setCharacterUnitFirstLineIndent(20.0);
format.setLineUnitBefore(5.0);
format.setLineUnitAfter(10.0);
doc.save("ChangeAsianParagraphSpacingAndIndents.docx");
```

## الالتقاط إلى الشبكة

حسّن التخطيط عند العمل مع الأحرف الآسيوية عبر الالتقاط إلى الشبكة:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Paragraph par = doc.getFirstSection().getBody().getFirstParagraph();
par.getParagraphFormat().setSnapToGrid(true);
builder.writeln("Lorem ipsum dolor sit amet, consectetur adipiscing elit...");
par.getRuns().get(0).getFont().setSnapToGrid(true);
doc.save("SnapToGrid.docx");
```

## اكتشاف فواصل أنماط الفقرات

إذا كنت بحاجة إلى العثور على فواصل الأنماط في مستندك، يمكنك استخدام الشيفرة التالية:

```java
Document doc = new Document("Document.docx");
for (Paragraph paragraph : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (paragraph.getBreakIsStyleSeparator())
    {
        System.out.println("Separator Found!");
    }
}
```

## الخاتمة

في هذه المقالة، استعرضنا جوانب مختلفة من تنسيق المستندات في Aspose.Words for Java، بما في ذلك كيفية **إنشاء قائمة متعددة المستويات**، **تطبيق نمط الفقرة**، **ضبط محاذاة الفقرة**، و**تحديد المسافة اليسرى**. armed with these insights, you can generate professional‑looking Word documents for your Java applications. تذكّر الرجوع إلى [Aspose.Words for Java documentation](https://reference.aspose.com/words/java/) لمزيد من الإرشادات المتعمقة.

## الأسئلة المتكررة

**س: كيف يمكنني تنزيل Aspose.Words for Java؟**  
ج: يمكنك تنزيل Aspose.Words for Java من [this link](https://releases.aspose.com/words/java/).

**س: هل Aspose.Words for Java مناسبة لإنشاء مستندات معقدة؟**  
ج: بالتأكيد! توفر Aspose.Words for Java إمكانيات واسعة لإنشاء وتنسيق مستندات معقدة بسهولة.

**س: هل يمكنني تطبيق أنماط مخصصة على الفقرات باستخدام Aspose.Words for Java؟**  
ج: نعم، يمكنك تطبيق أنماط مخصصة على الفقرات لمنح مستنداتك مظهرًا فريدًا.

**س: هل تدعم Aspose.Words for Java القوائم متعددة المستويات؟**  
ج: نعم، توفر Aspose.Words for Java دعمًا ممتازًا لإنشاء وتنسيق القوائم متعددة المستويات.

**س: كيف يمكنني تحسين تباعد الفقرات للنص الآسيوي؟**  
ج: يمكنك ضبط تباعد الفقرات للنص الآسيوي عن طريق تعديل الإعدادات ذات الصلة في Aspose.Words for Java.

**س: ما هي أسهل طريقة لإنشاء مستند Word برمجيًا؟**  
ج: أنشئ كائن `Document`، استخدم `DocumentBuilder` لإضافة المحتوى، واستدعِ `save("YourFile.docx")`.

**س: هل هناك نصائح أداء للمستندات الكبيرة؟**  
ج: استخدم واجهات برمجة التطبيقات المتدفقة (streaming APIs) وتخلص من الكائنات غير المستخدمة بسرعة للحفاظ على استهلاك الذاكرة منخفضًا.

---

**آخر تحديث:** 2026-01-09  
**تم الاختبار مع:** Aspose.Words for Java 24.12 (أحدث إصدار)  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}