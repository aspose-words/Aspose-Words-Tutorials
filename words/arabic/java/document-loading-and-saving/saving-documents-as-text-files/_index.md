---
title: حفظ المستندات كملفات نصية في Aspose.Words لـ Java
linktitle: حفظ المستندات كملفات نصية
second_title: واجهة برمجة تطبيقات معالجة المستندات في Java Aspose.Words
description: تعرف على كيفية حفظ المستندات كملفات نصية في Aspose.Words for Java. اتبع دليلنا خطوة بخطوة مع أمثلة أكواد Java.
weight: 24
url: /ar/java/document-loading-and-saving/saving-documents-as-text-files/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ المستندات كملفات نصية في Aspose.Words لـ Java


## مقدمة لحفظ المستندات كملفات نصية في Aspose.Words لـ Java

في هذا البرنامج التعليمي، سنستكشف كيفية حفظ المستندات كملفات نصية باستخدام مكتبة Aspose.Words for Java. Aspose.Words عبارة عن واجهة برمجة تطبيقات Java قوية للعمل مع مستندات Word، وتوفر خيارات متنوعة لحفظ المستندات بتنسيقات مختلفة، بما في ذلك النص العادي. سنغطي الخطوات اللازمة لتحقيق ذلك وسنقدم عينة من أكواد Java على طول الطريق.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من توفر المتطلبات الأساسية التالية:

- تم تثبيت Java Development Kit (JDK) على نظامك.
-  تم دمج مكتبة Aspose.Words for Java في مشروعك. يمكنك تنزيلها من[هنا](https://releases.aspose.com/words/java/).
- المعرفة الأساسية لبرمجة جافا.

## الخطوة 1: إنشاء مستند

لحفظ مستند كملف نصي، نحتاج أولاً إلى إنشاء مستند باستخدام Aspose.Words. فيما يلي مقتطف بسيط من كود Java لإنشاء مستند يحتوي على بعض المحتوى:

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

بعد ذلك، نحتاج إلى تحديد خيارات حفظ النص التي تحدد كيفية حفظ المستند كملف نصي. يمكننا تكوين إعدادات مختلفة مثل إضافة علامات ثنائية الاتجاه، وقائمة المسافات البادئة، والمزيد. دعنا نلقي نظرة على مثالين:

### المثال 1: إضافة علامات البيدي

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

 في هذا المثال، نقوم بإنشاء`TxtSaveOptions` الكائن وتعيين`AddBidiMarks`الممتلكات ل`true` لتضمين علامات البيدي في إخراج النص.

### المثال 2: استخدام حرف Tab لإضافة مسافة بادئة إلى القائمة

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

هنا، قمنا بتكوين خيارات الحفظ لاستخدام حرف علامة التبويب لتجويف القائمة مع عدد 1.

## الخطوة 3: حفظ المستند كنص

الآن بعد أن حددنا خيارات حفظ النص، يمكننا حفظ المستند كملف نصي. يوضح الكود التالي كيفية القيام بذلك:

```java
doc.save("output.txt", saveOptions);
```

 يستبدل`"output.txt"` مع مسار الملف المطلوب حيث تريد حفظ ملف النص.

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

في هذا البرنامج التعليمي، تعلمنا كيفية حفظ المستندات كملفات نصية في Aspose.Words for Java. لقد قمنا بتغطية الخطوات اللازمة لإنشاء مستند، وتحديد خيارات حفظ النص، وحفظ المستند بتنسيق نصي. يوفر Aspose.Words مرونة كبيرة عندما يتعلق الأمر بحفظ المستندات، مما يسمح لك بتخصيص الناتج وفقًا لمتطلباتك المحددة.

## الأسئلة الشائعة

### كيف أضيف علامات bidi إلى إخراج النص؟

 لإضافة علامات bidi إلى إخراج النص، اضبط`AddBidiMarks` ممتلكات`TxtSaveOptions` ل`true`. على سبيل المثال:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### هل يمكنني تخصيص حرف المسافة البادئة للقائمة؟

 نعم، يمكنك تخصيص حرف المسافة البادئة للقائمة عن طريق تكوين`ListIndentation` ممتلكات`TxtSaveOptions`على سبيل المثال، لاستخدام حرف علامة التبويب لإضافة مسافة بادئة إلى القائمة، يمكنك القيام بما يلي:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### هل Aspose.Words for Java مناسب للتعامل مع النصوص المتعددة اللغات؟

نعم، يعد برنامج Aspose.Words for Java مناسبًا للتعامل مع النصوص متعددة اللغات. فهو يدعم العديد من اللغات وترميزات الأحرف، مما يجعله خيارًا متعدد الاستخدامات للعمل مع المستندات بلغات مختلفة.

### كيف يمكنني الوصول إلى مزيد من الوثائق والموارد لـ Aspose.Words for Java؟

 يمكنك العثور على وثائق وموارد شاملة لـ Aspose.Words for Java على موقع وثائق Aspose:[توثيق Aspose.Words للغة Java](https://reference.aspose.com/words/java/).

### أين يمكنني تنزيل Aspose.Words لـ Java؟

 يمكنك تنزيل مكتبة Aspose.Words for Java من موقع Aspose على الويب:[تنزيل Aspose.Words لجافا](https://releases.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
