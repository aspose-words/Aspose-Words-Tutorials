---
title: استخدام الحواشي السفلية والختامية في Aspose.Words للغة Java
linktitle: استخدام الحواشي السفلية والختامية
second_title: واجهة برمجة تطبيقات معالجة المستندات في Java Aspose.Words
description: تعلم كيفية استخدام الحواشي السفلية والختامية بشكل فعال في Aspose.Words for Java. قم بتعزيز مهاراتك في تنسيق المستندات اليوم!
weight: 13
url: /ar/java/using-document-elements/using-footnotes-and-endnotes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# استخدام الحواشي السفلية والختامية في Aspose.Words للغة Java


في هذا البرنامج التعليمي، سنطلعك على عملية استخدام الحواشي السفلية والتعليقات الختامية في Aspose.Words for Java. الحواشي السفلية والتعليقات الختامية هي عناصر أساسية في تنسيق المستندات، وغالبًا ما تُستخدم للاستشهادات والمراجع والمعلومات الإضافية. يوفر Aspose.Words for Java وظائف قوية للعمل مع الحواشي السفلية والتعليقات الختامية بسلاسة.

## 1. مقدمة حول الحواشي السفلية والختامية

الحواشي السفلية والتعليقات الختامية هي تعليقات توضيحية توفر معلومات تكميلية أو اقتباسات داخل مستند. تظهر الحواشي السفلية في أسفل الصفحة، بينما يتم جمع التعليقات الختامية في نهاية القسم أو المستند. تُستخدم عادةً في الأوراق الأكاديمية والتقارير والمستندات القانونية للإشارة إلى المصادر أو توضيح المحتوى.

## 2. إعداد البيئة الخاصة بك

قبل أن نتعمق في العمل مع الحواشي السفلية والختامية، عليك إعداد بيئة التطوير الخاصة بك. تأكد من تثبيت واجهة برمجة التطبيقات Aspose.Words for Java وتكوينها في مشروعك.

## 3. إضافة الحواشي السفلية إلى مستندك

لإضافة الحواشي السفلية إلى مستندك، اتبع الخطوات التالية:
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";

public void getFootnoteOptions(){
    Document doc = new Document(dataDir + "Document.docx");
    
    // قم بتحديد عدد الأعمدة التي سيتم تنسيق منطقة الحواشي بها.
    doc.getFootnoteOptions().setColumns(3);
    doc.save("Your Directory Path" + "WorkingWithFootnotes.SetFootNoteColumns.docx");
}
```

## 4. تعديل خيارات الحاشية السفلية

يمكنك تعديل خيارات الحاشية السفلية لتخصيص مظهرها وسلوكها. وإليك الطريقة:
```java
@Test
public void setFootnoteAndEndNotePosition() throws Exception {
    Document doc = new Document(dataDir + "Document.docx");
    
    doc.getFootnoteOptions().setPosition(FootnotePosition.BENEATH_TEXT);
    doc.getEndnoteOptions().setPosition(EndnotePosition.END_OF_SECTION);
    
    doc.save(outPath + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
}
```

## 5. إضافة التعليقات الختامية إلى مستندك

إن إضافة التعليقات الختامية إلى مستندك أمر بسيط. إليك مثال على ذلك:
```java
@Test
public void setEndnoteOptions() throws Exception {
    Document doc = new Document(dataDir + "Document.docx");
    DocumentBuilder builder = new DocumentBuilder(doc);
    
    builder.write("Some text");
    builder.insertFootnote(FootnoteType.ENDNOTE, "Footnote text.");
    
    EndnoteOptions option = doc.getEndnoteOptions();
    option.setRestartRule(FootnoteNumberingRule.RESTART_PAGE);
    option.setPosition(EndnotePosition.END_OF_SECTION);
    
    doc.save(outPath + "WorkingWithFootnotes.SetEndnoteOptions.docx");
}
```

## 6. تخصيص إعدادات التعليقات الختامية

يمكنك تخصيص إعدادات الملاحظة الختامية بشكل أكبر لتلبية متطلبات مستندك.

## الكود المصدر الكامل
```java
	string dataDir = "Your Document Directory";
	string outPath = "Your Output Directory";
	public void getFootnoteOptions(){
        Document doc = new Document(dataDir + "Document.docx");
        // قم بتحديد عدد الأعمدة التي سيتم تنسيق منطقة الحواشي بها.
        doc.getFootnoteOptions().setColumns(3);
        doc.save("Your Directory Path" + "WorkingWithFootnotes.SetFootNoteColumns.docx");
    }
    @Test
    public void setFootnoteAndEndNotePosition() throws Exception
    {
        Document doc = new Document(dataDir + "Document.docx");
        doc.getFootnoteOptions().setPosition(FootnotePosition.BENEATH_TEXT);
        doc.getEndnoteOptions().setPosition(EndnotePosition.END_OF_SECTION);
        doc.save(outPath + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
    }
    @Test
    public void setEndnoteOptions() throws Exception
    {
        Document doc = new Document(dataDir + "Document.docx");
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.write("Some text");
        builder.insertFootnote(FootnoteType.ENDNOTE, "Footnote text.");
        EndnoteOptions option = doc.getEndnoteOptions();
        option.setRestartRule(FootnoteNumberingRule.RESTART_PAGE);
        option.setPosition(EndnotePosition.END_OF_SECTION);
        doc.save(outPath + "WorkingWithFootnotes.SetEndnoteOptions.docx");
	}
```

## 7. الخاتمة

في هذا البرنامج التعليمي، استكشفنا كيفية العمل مع الحواشي السفلية والختامية في Aspose.Words for Java. هذه الميزات لا تقدر بثمن لإنشاء مستندات منظمة بشكل جيد مع الاستشهادات والمراجع المناسبة.

الآن بعد أن تعلمت كيفية استخدام الحواشي السفلية والختامية، يمكنك تحسين تنسيق مستندك وجعل المحتوى الخاص بك أكثر احترافية.

### الأسئلة الشائعة

### 1. ما هو الفرق بين الحواشي السفلية والحواشي النهائية؟
تظهر الحواشي في أسفل الصفحة، في حين يتم جمع الحواشي في نهاية القسم أو المستند.

### 2. كيف يمكنني تغيير موضع الحواشي السفلية أو الختامية؟
 يمكنك استخدام`setPosition` طريقة لتغيير موضع الحواشي السفلية أو الختامية.

### 3. هل يمكنني تخصيص تنسيق الحواشي السفلية والختامية؟
نعم، يمكنك تخصيص تنسيق الحواشي السفلية والختامية باستخدام Aspose.Words لـ Java.

### 4. هل الحواشي السفلية والختامية مهمة في تنسيق المستندات؟
نعم، تعتبر الحواشي السفلية والختامية ضرورية لتوفير المراجع والمعلومات الإضافية في المستندات.

لا تتردد في استكشاف المزيد من ميزات Aspose.Words for Java وتعزيز قدراتك على إنشاء المستندات. استمتع بالبرمجة!
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
