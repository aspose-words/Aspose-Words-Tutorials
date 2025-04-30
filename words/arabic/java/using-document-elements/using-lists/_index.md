---
"description": "تعلّم استخدام القوائم في Aspose.Words لجافا مع هذا البرنامج التعليمي خطوة بخطوة. نظّم مستنداتك ونسّقها بفعالية."
"linktitle": "استخدام القوائم"
"second_title": "واجهة برمجة تطبيقات معالجة مستندات Java Aspose.Words"
"title": "استخدام القوائم في Aspose.Words للغة Java"
"url": "/ar/java/using-document-elements/using-lists/"
"weight": 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# استخدام القوائم في Aspose.Words للغة Java


في هذا البرنامج التعليمي الشامل، سنستكشف كيفية استخدام القوائم بفعالية في Aspose.Words لجافا، وهي واجهة برمجة تطبيقات فعّالة للعمل مع مستندات مايكروسوفت وورد برمجيًا. تُعد القوائم أساسية لهيكلة وتنظيم محتوى مستنداتك. سنغطي جانبين رئيسيين من العمل مع القوائم: إعادة تشغيل القوائم في كل قسم، وتحديد مستوياتها. لنبدأ!

## مقدمة إلى Aspose.Words للغة Java

قبل أن نبدأ العمل مع القوائم، لنتعرف على Aspose.Words لجافا. توفر هذه الواجهة البرمجية للمطورين الأدوات اللازمة لإنشاء مستندات Word وتعديلها ومعالجتها في بيئة جافا. إنها حل متعدد الاستخدامات لمهام تتراوح من إنشاء المستندات البسيطة إلى التنسيق وإدارة المحتوى المعقدة.

### إعداد بيئتك

للبدء، تأكد من تثبيت Aspose.Words لجافا وإعداده في بيئة التطوير لديك. يمكنك تنزيله. [هنا](https://releases.aspose.com/words/java/). 

## إعادة تشغيل القوائم في كل قسم

في العديد من الحالات، قد تحتاج إلى إعادة تشغيل القوائم في كل قسم من مستندك. قد يكون هذا مفيدًا لإنشاء مستندات منظمة ذات أقسام متعددة، مثل التقارير أو الأدلة أو الأوراق الأكاديمية.

فيما يلي دليل خطوة بخطوة حول كيفية تحقيق ذلك باستخدام Aspose.Words لـ Java:

### تهيئة مستندك: 
ابدأ بإنشاء كائن مستند جديد.

```java
Document doc = new Document();
```

### إضافة قائمة مرقمة: 
أضف قائمة مرقمة إلى مستندك. سنستخدم نمط الترقيم الافتراضي.

```java
doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
```

### تكوين إعدادات القائمة: 
\تمكين القائمة لإعادة التشغيل عند كل قسم.

```java
List list = doc.getLists().get(0);
list.isRestartAtEachSection(true);
```

### إعداد DocumentBuilder: 
قم بإنشاء DocumentBuilder لإضافة المحتوى إلى مستندك.

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.getListFormat().setList(list);
```

### إضافة عناصر القائمة: 
استخدم حلقة لإضافة عناصر القائمة إلى مستندك. سنضيف فاصلًا مقطعيًا بعد العنصر الخامس عشر.

```java
for (int i = 1; i < 45; i++) {
    builder.writeln(MessageFormat.format("List Item {0}", i));
    if (i == 15)
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
}
```

### احفظ مستندك: 
احفظ المستند بالخيارات المطلوبة.

```java
OoxmlSaveOptions options = new OoxmlSaveOptions();
options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);
doc.save(outPath + "RestartListAtEachSection.docx", options);
```

من خلال اتباع الخطوات التالية، يمكنك إنشاء مستندات تحتوي على قوائم تتجدد عند كل قسم، مع الحفاظ على بنية محتوى واضحة ومنظمة.

## تحديد مستويات القائمة

يتيح لك Aspose.Words لجافا تحديد مستويات القوائم، وهو أمر مفيد بشكل خاص عند الحاجة إلى تنسيقات قوائم مختلفة ضمن مستندك. لنستكشف كيفية القيام بذلك:

### تهيئة مستندك: 
إنشاء كائن مستند جديد.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### إنشاء قائمة مرقمة: 
تطبيق قالب القائمة المرقمة من Microsoft Word.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
```

### تحديد مستويات القائمة: 
قم بالتكرار خلال مستويات القائمة المختلفة وأضف المحتوى.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### إنشاء قائمة نقطية: 
الآن، دعونا نقوم بإنشاء قائمة نقطية.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
```

### تحديد مستويات القائمة المنقطة: 
على غرار القائمة المرقمة، حدد المستويات وأضف المحتوى.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### تنسيق قائمة التوقف: 
لإيقاف تنسيق القائمة، قم بتعيين القائمة إلى قيمة فارغة.

```java
builder.getListFormat().setList(null);
```

### احفظ مستندك: 
احفظ المستند.

```java
builder.getDocument().save(outPath + "SpecifyListLevel.docx");
```

من خلال اتباع الخطوات التالية، يمكنك إنشاء مستندات بمستويات قائمة مخصصة، مما يسمح لك بالتحكم في تنسيق القوائم في مستنداتك.

## الكود المصدر الكامل
```java
	string outPath = "Your Output Directory";
 public void restartListAtEachSection() throws Exception
    {
        Document doc = new Document();
        doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
        List list = doc.getLists().get(0);
        list.isRestartAtEachSection(true);
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.getListFormat().setList(list);
        for (int i = 1; i < 45; i++)
        {
            builder.writeln(MessageFormat.format("List Item {0}", i));
            if (i == 15)
                builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        }
        // سيتم كتابة IsRestartAtEachSection فقط إذا كان التوافق أعلى من OoxmlComplianceCore.Ecma376.
        OoxmlSaveOptions options = new OoxmlSaveOptions(); { options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL); }
        doc.save(outPath + "WorkingWithList.RestartListAtEachSection.docx", options);
    }
    @Test
    public void specifyListLevel() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // إنشاء قائمة مرقمة استنادًا إلى أحد قوالب قوائم Microsoft Word
        // وتطبيقه على الفقرة الحالية لمنشئ المستند.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
        // هناك تسعة مستويات في هذه القائمة، دعنا نجربها جميعًا.
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // إنشاء قائمة نقطية استنادًا إلى أحد قوالب قائمة Microsoft Word
        // وتطبيقه على الفقرة الحالية لمنشئ المستند.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // هذه طريقة لإيقاف تنسيق القائمة.
        builder.getListFormat().setList(null);
        builder.getDocument().save(outPath + "WorkingWithList.SpecifyListLevel.docx");
    }
    @Test
    public void restartListNumber() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // إنشاء قائمة بناءً على قالب.
        List list1 = doc.getLists().add(ListTemplate.NUMBER_ARABIC_PARENTHESIS);
        list1.getListLevels().get(0).getFont().setColor(Color.RED);
        list1.getListLevels().get(0).setAlignment(ListLevelAlignment.RIGHT);
        builder.writeln("List 1 starts below:");
        builder.getListFormat().setList(list1);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        // لإعادة استخدام القائمة الأولى، نحتاج إلى إعادة تشغيل الترقيم عن طريق إنشاء نسخة من تنسيق القائمة الأصلية.
        List list2 = doc.getLists().addCopy(list1);
        // يمكننا تعديل القائمة الجديدة بأي طريقة، بما في ذلك تعيين رقم بداية جديد.
        list2.getListLevels().get(0).setStartAt(10);
        builder.writeln("List 2 starts below:");
        builder.getListFormat().setList(list2);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        builder.getDocument().save(outPath + "WorkingWithList.RestartListNumber.docx");
	}
```

## خاتمة

تهانينا! لقد تعلمت كيفية التعامل مع القوائم بفعالية في Aspose.Words for Java. القوائم أساسية لتنظيم وعرض المحتوى في مستنداتك. سواءً كنت بحاجة إلى إعادة تشغيل القوائم في كل قسم أو تحديد مستوياتها، يوفر Aspose.Words for Java الأدوات اللازمة لإنشاء مستندات احترافية.

الآن يمكنك استخدام هذه الميزات بثقة لتحسين مهام إنشاء المستندات وتنسيقها. إذا كانت لديك أي أسئلة أو كنت بحاجة إلى مزيد من المساعدة، فلا تتردد في التواصل مع [منتدى مجتمع Aspose](https://forum.aspose.com/) للحصول على الدعم.

## الأسئلة الشائعة

### كيف أقوم بتثبيت Aspose.Words لـ Java؟
يمكنك تنزيل Aspose.Words for Java من [هنا](https://releases.aspose.com/words/java/) واتبع تعليمات التثبيت الموجودة في الوثائق.

### هل يمكنني تخصيص تنسيق ترقيم القوائم؟
نعم، يوفر Aspose.Words لجافا خيارات شاملة لتخصيص تنسيقات ترقيم القوائم. يمكنك مراجعة وثائق واجهة برمجة التطبيقات (API) لمزيد من التفاصيل.

### هل Aspose.Words for Java متوافق مع أحدث معايير مستندات Word؟
نعم، يمكنك تكوين Aspose.Words لـ Java للامتثال لمعايير مستند Word المختلفة، بما في ذلك ISO 29500.

### هل يمكنني إنشاء مستندات معقدة تحتوي على جداول وصور باستخدام Aspose.Words for Java؟
بالتأكيد! يدعم Aspose.Words لجافا تنسيق المستندات المتقدم، بما في ذلك الجداول والصور وغيرها. راجع الوثائق للاطلاع على أمثلة.

### أين يمكنني الحصول على ترخيص مؤقت لـ Aspose.Words for Java؟
يمكنك الحصول على ترخيص مؤقت [هنا](https://purchase.aspose.com/temporary-license/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}