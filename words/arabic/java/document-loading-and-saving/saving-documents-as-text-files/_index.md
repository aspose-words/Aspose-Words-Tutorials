---
"description": "تعلّم كيفية حفظ المستندات كملفات نصية في Aspose.Words لجافا. اتبع دليلنا خطوة بخطوة مع أمثلة أكواد جافا."
"linktitle": "حفظ المستندات كملفات نصية"
"second_title": "واجهة برمجة تطبيقات معالجة مستندات Java Aspose.Words"
"title": "حفظ المستندات كملفات نصية في Aspose.Words لـ Java"
"url": "/ar/java/document-loading-and-saving/saving-documents-as-text-files/"
"weight": 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# حفظ المستندات كملفات نصية في Aspose.Words لـ Java


## مقدمة لحفظ المستندات كملفات نصية في Aspose.Words لـ Java

في هذا البرنامج التعليمي، سنستكشف كيفية حفظ المستندات كملفات نصية باستخدام مكتبة Aspose.Words لجافا. Aspose.Words هي واجهة برمجة تطبيقات Java فعّالة للعمل مع مستندات Word، وتوفر خيارات متنوعة لحفظ المستندات بتنسيقات مختلفة، بما في ذلك النص العادي. سنشرح خطوات تحقيق ذلك، ونقدم أمثلة على أكواد Java.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من توفر المتطلبات الأساسية التالية:

- تم تثبيت Java Development Kit (JDK) على نظامك.
- مكتبة Aspose.Words لجافا مُدمجة في مشروعك. يمكنك تنزيلها من [هنا](https://releases.aspose.com/words/java/).
- المعرفة الأساسية ببرمجة جافا.

## الخطوة 1: إنشاء مستند

لحفظ مستند كملف نصي، نحتاج أولًا إلى إنشاء مستند باستخدام Aspose.Words. إليك مقطع برمجي بسيط بلغة جافا لإنشاء مستند يحتوي على بعض المحتوى:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

في هذا الكود نقوم بإنشاء مستند جديد وإضافة بعض النصوص إليه، بما في ذلك النصوص بلغات مختلفة.

## الخطوة 2: تحديد خيارات حفظ النص

بعد ذلك، نحتاج إلى تحديد خيارات حفظ النص التي تُحدد كيفية حفظ المستند كملف نصي. يمكننا ضبط إعدادات مُختلفة، مثل إضافة علامات ثنائية الاتجاه، ومسافة بادئة للقوائم، وغيرها. لنلقِ نظرة على مثالين:

### المثال 1: إضافة علامات بيدي

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

في هذا المثال، نقوم بإنشاء `TxtSaveOptions` الكائن وتعيين `AddBidiMarks` الممتلكات إلى `true` لتضمين علامات bidi في إخراج النص.

### المثال 2: استخدام حرف Tab لإضافة مسافة بادئة إلى القائمة

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

هنا، قمنا بتكوين خيارات الحفظ لاستخدام حرف علامة التبويب لتجويف القائمة مع عدد 1.

## الخطوة 3: حفظ المستند كنص

بعد تحديد خيارات حفظ النص، يمكننا حفظ المستند كملف نصي. يوضح الكود التالي كيفية القيام بذلك:

```java
doc.save("output.txt", saveOptions);
```

يستبدل `"output.txt"` مع مسار الملف المطلوب حيث تريد حفظ ملف النص.

## الكود المصدري الكامل لحفظ المستندات كملفات نصية في Aspose.Words لـ Java

```java
    public void addBidiMarks() throws Exception
    {        
		Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("Hello world!");
        builder.getParagraphFormat().setBidi(true);
        builder.writeln("שלום עולם!");
        builder.writeln("مرحبا بالعالم!");
        TxtSaveOptions saveOptions = new TxtSaveOptions(); { saveOptions.setAddBidiMarks(true); }
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
    }
    @Test
    public void useTabCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // إنشاء قائمة تحتوي على ثلاثة مستويات من المسافة البادئة.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(1);
        saveOptions.getListIndentation().setCharacter('\t');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseTabCharacterPerLevelForListIndentation.txt", saveOptions);
    }
    @Test
    public void useSpaceCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // إنشاء قائمة تحتوي على ثلاثة مستويات من المسافة البادئة.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(3);
        saveOptions.getListIndentation().setCharacter(' ');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
	}
```

## خاتمة

في هذا البرنامج التعليمي، تعلمنا كيفية حفظ المستندات كملفات نصية في Aspose.Words لجافا. تناولنا خطوات إنشاء مستند، وتحديد خيارات حفظ النص، وحفظه بتنسيق نصي. يوفر Aspose.Words مرونة كبيرة في حفظ المستندات، مما يسمح لك بتخصيص المخرجات لتلبية احتياجاتك الخاصة.

## الأسئلة الشائعة

### كيف أضيف علامات bidi إلى إخراج النص؟

لإضافة علامات bidi إلى إخراج النص، اضبط `AddBidiMarks` ممتلكات `TxtSaveOptions` ل `true`. على سبيل المثال:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### هل يمكنني تخصيص حرف المسافة البادئة للقائمة؟

نعم، يمكنك تخصيص حرف المسافة البادئة للقائمة عن طريق تكوين `ListIndentation` ممتلكات `TxtSaveOptions`على سبيل المثال، لاستخدام حرف الجدولة لإضافة مسافة بادئة إلى القائمة، يمكنك القيام بما يلي:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### هل Aspose.Words for Java مناسب للتعامل مع النصوص المتعددة اللغات؟

نعم، يُعدّ Aspose.Words for Java مناسبًا للتعامل مع النصوص متعددة اللغات. فهو يدعم لغات وترميزات أحرف متنوعة، مما يجعله خيارًا متعدد الاستخدامات للعمل مع المستندات بمختلف اللغات.

### كيف يمكنني الوصول إلى مزيد من الوثائق والموارد الخاصة بـ Aspose.Words for Java؟

يمكنك العثور على وثائق وموارد شاملة لـ Aspose.Words for Java على موقع وثائق Aspose: [توثيق Aspose.Words لـ Java](https://reference.aspose.com/words/java/).

### أين يمكنني تنزيل Aspose.Words لـ Java؟

يمكنك تنزيل مكتبة Aspose.Words for Java من موقع Aspose الإلكتروني: [تنزيل Aspose.Words لـ Java](https://releases.aspose.com/words/java/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}