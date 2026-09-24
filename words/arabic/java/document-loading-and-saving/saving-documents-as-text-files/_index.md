---
date: 2025-12-24
description: تعلم كيفية إنشاء ملف نص عادي من مستندات Word باستخدام Aspose.Words للغة
  Java. يوضح هذا الدليل كيفية تحويل Word إلى txt، واستخدام مسافات التبويب للإنذاء،
  وحفظ Word كملف txt.
linktitle: Saving Documents as Text Files
second_title: Aspose.Words Java Document Processing API
title: كيفية إنشاء ملف نص عادي باستخدام Aspose.Words لجافا
url: /ar/java/document-loading-and-saving/saving-documents-as-text-files/
weight: 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء ملف نص عادي باستخدام Aspose.Words للـ Java

## مقدمة حول حفظ المستندات كملفات نصية في Aspose.Words للـ Java

في هذا الدرس، ستتعلم **كيفية إنشاء ملف نص عادي** من مستند Word باستخدام مكتبة Aspose.Words للـ Java. سواء كنت بحاجة إلى **تحويل word إلى txt**، أو أتمتة إنشاء التقارير، أو ببساطة استخراج النص الخام للمعالجة اللاحقة، فإن هذا الدليل يشرح لك سير العمل بالكامل—من إنشاء المستند إلى ضبط خيارات الحفظ مثل **استخدام مسافة تبويب** أو إضافة علامات bidi. لنبدأ!

## إجابات سريعة
- **ما هو الصنف الأساسي لإنشاء مستند؟** `Document` من Aspose.Words.  
- **أي خيار يضيف علامات bidi للغات من اليمين إلى اليسار؟** `TxtSaveOptions.setAddBidiMarks(true)`.  
- **كيف يمكنني إزاحة عناصر القائمة باستخدام علامات تبويب؟** اضبط `ListIndentation.Character` إلى `'\t'`.  
- **هل أحتاج إلى ترخيص للتطوير؟** النسخة التجريبية المجانية تكفي للاختبار؛ الترخيص مطلوب للإنتاج.  
- **هل يمكنني حفظ الملف باسم ومسار مخصص؟** نعم—مرّر المسار الكامل إلى `doc.save()`.

## المتطلبات المسبقة

قبل أن نبدأ، تأكد من توفر المتطلبات التالية:

- مجموعة تطوير Java (JDK) مثبتة على نظامك.  
- مكتبة Aspose.Words للـ Java مدمجة في مشروعك. يمكنك تحميلها من [هنا](https://releases.aspose.com/words/java/).  
- معرفة أساسية ببرمجة Java.

## الخطوة 1: إنشاء مستند

لـ **حفظ word كـ txt**، نحتاج أولاً إلى كائن `Document`. فيما يلي مقتطف Java بسيط ينشئ مستندًا ويكتب بضع أسطر من النص متعدد اللغات:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

في هذا الكود ننشئ مستندًا جديدًا، نضيف نصًا بالإنجليزية والعبرية والعربية، ونفعّل تنسيق من اليمين إلى اليسار للفقرة العبرية.

## الخطوة 2: تعريف خيارات حفظ النص

بعد ذلك، نضبط كيفية حفظ المستند كملف نص عادي. توفر Aspose.Words الصنف `TxtSaveOptions`، الذي يتيح لك التحكم في كل شيء من علامات bidi إلى إزاحة القوائم.

### مثال 1: إضافة علامات Bidi (كيفية حفظ txt مع دعم RTL صحيح)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

ضبط `AddBidiMarks` على `true` يضمن تمثيل الأحرف من اليمين إلى اليسار بشكل صحيح في **ملف النص العادي** الناتج.

### مثال 2: استخدام حرف التبويب لإزاحة القوائم (use tab indentation)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

هنا نخبر Aspose.Words بإضافة حرف تبويب (`'\t'`) قبل كل مستوى من مستويات القائمة، مما يجعل مخرجات النص أسهل للقراءة.

## الخطوة 3: حفظ المستند كنص

الآن بعد أن تم إعداد خيارات الحفظ، يمكنك حفظ المستند كـ **ملف نص عادي**:

```java
doc.save("output.txt", saveOptions);
```

استبدل `"output.txt"` بالمسار الكامل حيث تريد تخزين الملف.

## الكود الكامل لحفظ المستندات كملفات نصية في Aspose.Words للـ Java

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
        // Create a list with three levels of indentation.
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
        // Create a list with three levels of indentation.
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

## المشكلات الشائعة والحلول

| المشكلة | الحل |
|-------|----------|
| **ظهور أحرف bidi مشوهة** | تأكد من تمكين `setAddBidiMarks(true)` وافتح الملف الناتج بترميز UTF‑8. |
| **إزاحة القائمة غير صحيحة** | تحقق من ضبط `ListIndentation.Count` و`Character` إلى القيم المطلوبة (تبويب `'\t'` أو مسافة `' '` ). |
| **الملف غير مُنشأ** | تأكد من وجود مسار الدليل ومن أن التطبيق يملك صلاحيات الكتابة. |

## الأسئلة المتكررة

### كيف أضيف علامات bidi إلى مخرجات النص؟

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### هل يمكنني تخصيص حرف إزاحة القائمة؟

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### هل Aspose.Words للـ Java مناسب للتعامل مع النص متعدد اللغات؟

نعم، يدعم Aspose.Words للـ Java مجموعة واسعة من اللغات وترميزات الأحرف، مما يجعله مثاليًا لاستخراج وحفظ المحتوى متعدد اللغات كنص عادي.

### كيف يمكنني الوصول إلى مزيد من الوثائق والموارد الخاصة بـ Aspose.Words للـ Java؟

يمكنك العثور على وثائق شاملة وموارد على صفحة وثائق Aspose.Words للـ Java: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

### أين يمكنني تحميل Aspose.Words للـ Java؟

يمكنك تحميل المكتبة من الموقع الرسمي: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/).

### ماذا لو احتجت إلى **تحويل word إلى txt** في عملية دفعة؟

قم بلف الكود أعلاه داخل حلقة تقوم بتحميل كل ملف `.docx`، وتطبيق نفس `TxtSaveOptions`، وحفظ كل ملف كـ `.txt`. احرص على تحرير كائنات `Document` بعد كل تكرار لتوفير الموارد.

### هل تدعم الـ API الحفظ مباشرة إلى تدفق بدلاً من ملف؟

نعم، يمكنك تمرير `OutputStream` إلى `doc.save(outputStream, saveOptions)` للمعالجة في الذاكرة أو عند التكامل مع خدمات الويب.

---

**آخر تحديث:** 2025-12-24  
**تم الاختبار مع:** Aspose.Words للـ Java 24.12 (الأحدث)  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}