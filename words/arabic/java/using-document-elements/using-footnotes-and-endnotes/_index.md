---
"description": "تعلم كيفية استخدام الحواشي السفلية والختامية بفعالية في Aspose.Words لجافا. حسّن مهاراتك في تنسيق المستندات اليوم!"
"linktitle": "استخدام الحواشي السفلية والختامية"
"second_title": "واجهة برمجة تطبيقات معالجة مستندات Java Aspose.Words"
"title": "استخدام الحواشي السفلية والختامية في Aspose.Words للغة Java"
"url": "/ar/java/using-document-elements/using-footnotes-and-endnotes/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# استخدام الحواشي السفلية والختامية في Aspose.Words للغة Java


في هذا البرنامج التعليمي، سنشرح لك عملية استخدام الحواشي السفلية والختامية في Aspose.Words لجافا. تُعد الحواشي السفلية والختامية عناصر أساسية في تنسيق المستندات، وغالبًا ما تُستخدم للاستشهادات والمراجع والمعلومات الإضافية. يوفر Aspose.Words لجافا وظائف قوية للتعامل مع الحواشي السفلية والختامية بسلاسة.

## 1. مقدمة عن الحواشي السفلية والختامية

الحواشي السفلية والختامية هي تعليقات توضيحية تُقدم معلومات أو استشهادات إضافية ضمن المستند. تظهر الحواشي السفلية في أسفل الصفحة، بينما تُجمع الحواشي الختامية في نهاية القسم أو المستند. تُستخدم عادةً في الأوراق الأكاديمية والتقارير والوثائق القانونية للإشارة إلى المصادر أو توضيح المحتوى.

## 2. إعداد بيئتك

قبل الخوض في العمل مع الحواشي السفلية والختامية، عليك إعداد بيئة التطوير الخاصة بك. تأكد من تثبيت واجهة برمجة تطبيقات Aspose.Words for Java وتهيئتها في مشروعك.

## 3. إضافة الحواشي السفلية إلى مستندك

لإضافة الحواشي السفلية إلى مستندك، اتبع الخطوات التالية:
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";

public void getFootnoteOptions(){
    Document doc = new Document(dataDir + "Document.docx");
    
    // قم بتحديد عدد الأعمدة التي سيتم تنسيق منطقة الحواشي السفلية بها.
    doc.getFootnoteOptions().setColumns(3);
    doc.save("Your Directory Path" + "WorkingWithFootnotes.SetFootNoteColumns.docx");
}
```

## 4. تعديل خيارات الحاشية السفلية

يمكنك تعديل خيارات الحواشي السفلية لتخصيص مظهرها وسلوكها. إليك الطريقة:
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

إضافة التعليقات الختامية إلى مستندك سهلة. إليك مثال:
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

يمكنك تخصيص إعدادات الملاحظات الختامية بشكل أكبر لتلبية متطلبات مستندك.

## الكود المصدر الكامل
```java
	string dataDir = "Your Document Directory";
	string outPath = "Your Output Directory";
	public void getFootnoteOptions(){
        Document doc = new Document(dataDir + "Document.docx");
        // قم بتحديد عدد الأعمدة التي سيتم تنسيق منطقة الحواشي السفلية بها.
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

في هذا البرنامج التعليمي، استكشفنا كيفية التعامل مع الحواشي السفلية والختامية في Aspose.Words لجافا. هذه الميزات قيّمة لإنشاء مستندات منظمة مع استشهادات ومراجع مناسبة.

الآن بعد أن تعلمت كيفية استخدام الحواشي السفلية والختامية، يمكنك تحسين تنسيق مستندك وجعل المحتوى الخاص بك أكثر احترافية.

### الأسئلة الشائعة

### 1. ما هو الفرق بين الحواشي السفلية والحواشي النهائية؟
تظهر الحواشي السفلية في أسفل الصفحة، في حين يتم جمع الحواشي النهائية في نهاية القسم أو المستند.

### 2. كيف يمكنني تغيير موضع الحواشي السفلية أو النهائية؟
يمكنك استخدام `setPosition` طريقة لتغيير موضع الحواشي السفلية أو النهائية.

### 3. هل يمكنني تخصيص تنسيق الحواشي السفلية والختامية؟
نعم، يمكنك تخصيص تنسيق الحواشي السفلية والختامية باستخدام Aspose.Words for Java.

### 4. هل الحواشي السفلية والختامية مهمة في تنسيق المستندات؟
نعم، تعتبر الحواشي السفلية والختامية ضرورية لتوفير المراجع والمعلومات الإضافية في المستندات.

لا تتردد في استكشاف المزيد من ميزات Aspose.Words لجافا، وحسّن قدراتك على إنشاء المستندات. برمجة ممتعة!


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}