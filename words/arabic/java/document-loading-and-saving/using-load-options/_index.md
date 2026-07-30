---
date: 2025-12-27
description: تعلم كيفية تعيين LoadOptions في Aspose.Words للغة Java، بما في ذلك كيفية
  تحديد مجلد مؤقت، تعيين إصدار Word، تحويل ملفات الميتا إلى PNG، وتحويل الشكل إلى
  رياضيات لمعالجة مستندات مرنة.
linktitle: Using Load Options
second_title: Aspose.Words Java Document Processing API
title: كيفية تعيين LoadOptions في Aspose.Words للغة Java
url: /ar/java/document-loading-and-saving/using-load-options/
weight: 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تعيين LoadOptions في Aspose.Words للـ Java

في هذا البرنامج التعليمي سنستعرض **كيفية تعيين LoadOptions** لمجموعة متنوعة من السيناريوهات الواقعية عند العمل مع Aspose.Words للـ Java. تمنحك LoadOptions تحكمًا دقيقًا في طريقة فتح المستند — سواء كنت بحاجة إلى تحديث الحقول المتسخة، العمل مع ملفات مشفرة، تحويل الأشكال إلى Office Math، أو إخبار المكتبة بمكان تخزين البيانات المؤقتة. بنهاية هذا الدليل ستكون قادرًا على تخصيص سلوك التحميل ليتوافق تمامًا مع متطلبات تطبيقك.

## إجابات سريعة
- **ما هي LoadOptions؟** كائن تكوين يؤثر على طريقة تحميل Aspose.Words للمستند.  
- **هل يمكنني تحديث الحقول أثناء التحميل؟** نعم — اضبط `setUpdateDirtyFields(true)`.  
- **كيف أفتح ملفًا محميًا بكلمة مرور؟** مرّر كلمة المرور إلى مُنشئ `LoadOptions`.  
- **هل يمكن تغيير المجلد المؤقت؟** استخدم `setTempFolder("path")`.  
- **أي طريقة تحول الأشكال إلى Office Math؟** `setConvertShapeToOfficeMath(true)`.

## لماذا نستخدم LoadOptions؟
تتيح لك LoadOptions تجنّب خطوات المعالجة بعد التحميل، تقليل استهلاك الذاكرة، وضمان تفسير المستند بالضبط كما تحتاج. على سبيل المثال، تحويل ملفات الميتا إلى PNG أثناء التحميل يمنع مشاكل التحويل اللاحقة، وتحديد إصدار MS Word يساعد في الحفاظ على دقة التخطيط عند التعامل مع ملفات قديمة.

## المتطلبات المسبقة
- Java 17 أو أحدث  
- Aspose.Words للـ Java (أحدث إصدار)  
- ترخيص Aspose صالح للاستخدام في الإنتاج  

## دليل خطوة بخطوة

### تحديث الحقول المتسخة

عند احتواء المستند على حقول تم تعديلها ولكن لم يتم تحديثها، يمكنك إخبار Aspose.Words بتحديثها تلقائيًا أثناء التحميل.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

*يضمن استدعاء `setUpdateDirtyFields(true)` إعادة حساب أي حقول متسخة فور فتح المستند.*

### تحميل مستند مشفر

إذا كان ملف المصدر محميًا بكلمة مرور، قدم كلمة المرور عند إنشاء كائن `LoadOptions`. يمكنك أيضًا تعيين كلمة مرور جديدة عند الحفظ بصيغة مختلفة.

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

### تحويل الشكل إلى Office Math

بعض المستندات القديمة تخزن المعادلات كأشكال رسومية. تمكين هذا الخيار يحول تلك الأشكال إلى كائنات Office Math أصلية، مما يسهل تعديلها لاحقًا.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

### تحديد إصدار MS Word

تحديد إصدار Word المستهدف يساعد المكتبة على اختيار قواعد العرض الصحيحة، خاصةً عند التعامل مع صيغ ملفات أقدم.

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

### استخدام مجلد مؤقت

قد تولد المستندات الكبيرة ملفات مؤقتة (مثل استخراج الصور). يمكنك توجيه هذه الملفات إلى مجلد تختاره، وهو مفيد للبيئات المعزولة.

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

### رد نداء التحذير

أثناء التحميل، قد تُصدر Aspose.Words تحذيرات (مثل ميزات غير مدعومة). تنفيذ رد نداء يتيح لك تسجيل هذه الأحداث أو التعامل معها.

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Handle warnings as they arise during document loading.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

### تحويل ملفات الميتا إلى PNG

يمكن تحويل ملفات الميتا مثل WMF إلى PNG أثناء التحميل، مما يضمن عرضًا ثابتًا عبر المنصات.

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

## الكود الكامل للعمل مع LoadOptions في Aspose.Words للـ Java

```java
public void updateDirtyFields() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setUpdateDirtyFields(true);
	}
	Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
}
@Test
public void loadEncryptedDocument() throws Exception {
	Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
@Test
public void convertShapeToOfficeMath() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertShapeToOfficeMath(true);
	}
	Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
}
@Test
public void setMsWordVersion() throws Exception {
	// Create a new LoadOptions object, which will load documents according to MS Word 2019 specification by default
	// and change the loading version to Microsoft Word 2010.
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setMswVersion(MsWordVersion.WORD_2010);
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
@Test
public void useTempFolder() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setTempFolder("Your Directory Path");
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
@Test
public void warningCallback() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
public static class DocumentLoadingWarningCallback implements IWarningCallback {
	public void warning(WarningInfo info) {
		// Prints warnings and their details as they arise during document loading.
		System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
		System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
	}
}
@Test
public void convertMetafilesToPng() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertMetafilesToPng(true);
	}
	Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
@Test
public void loadChm() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setEncoding(Charset.forName("windows-1251"));
	}
	Document doc = new Document("Your Directory Path" + "HTML help.chm", loadOptions);
}
```

## حالات الاستخدام الشائعة والنصائح

- **خطوط تحويل دفعية** – اجمع بين `setTempFolder` ووظيفة مجدولة لمعالجة مئات الملفات دون ملء دليل النظام المؤقت.  
- **ترحيل المستندات القديمة** – استخدم `setMswVersion` مع `setConvertShapeToOfficeMath` لنقل مستندات الهندسة القديمة إلى صيغة حديثة مع الحفاظ على المعادلات.  
- **معالجة المستندات بأمان** – اجمع بين `loadEncryptedDocument` و`OdtSaveOptions` لإعادة تشفير الملفات بكلمة مرور جديدة بصيغة مختلفة.  

## الأسئلة المتكررة

**س: كيف يمكنني التعامل مع التحذيرات أثناء تحميل المستند؟**  
ج: نفّذ `IWarningCallback` مخصص (كما هو موضح في مثال *رد نداء التحذير*) وسجّله عبر `loadOptions.setWarningCallback(...)`. يتيح لك ذلك تسجيل التحذير أو تجاهله أو إيقاف العملية بناءً على شدته.

**س: هل يمكنني تحويل الأشكال إلى كائنات Office Math عند تحميل المستند؟**  
ج: نعم—استدعِ `loadOptions.setConvertShapeToOfficeMath(true)` قبل إنشاء كائن `Document`. ستستبدل المكتبة الأشكال المتوافقة تلقائيًا بكائنات Office Math الأصلية.

**س: كيف أحدد إصدار MS Word لتحميل المستند؟**  
ج: استخدم `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` (أو أي قيمة أخرى من الـ enum) لتخبر Aspose.Words بقواعد العرض الخاصة بإصدار Word المحدد.

**س: ما الغرض من طريقة `setTempFolder` في LoadOptions؟**  
ج: توجه جميع الملفات المؤقتة التي تُنشأ أثناء التحميل (مثل الصور المستخرجة) إلى مجلد تتحكم فيه، وهو أمر أساسي للبيئات التي تقيّد استخدام دليل النظام المؤقت.

**س: هل يمكن تحويل ملفات الميتا مثل WMF إلى PNG أثناء التحميل؟**  
ج: بالتأكيد—فعّل ذلك عبر `loadOptions.setConvertMetafilesToPng(true)`. يضمن ذلك تخزين الصور النقطية كـ PNG، مما يحسّن التوافق مع عارضات الصور الحديثة.

## الخلاصة

غطّينا التقنيات الأساسية **لكيفية تعيين LoadOptions** في Aspose.Words للـ Java، من تحديث الحقول المتسخة إلى التعامل مع الملفات المشفرة، تحويل الأشكال، تحديد إصدار Word، توجيه التخزين المؤقت، والمزيد. باستخدام هذه الخيارات يمكنك بناء خطوط معالجة مستندات قوية وعالية الأداء تتكيف مع مجموعة واسعة من سيناريوهات الإدخال.

---

**آخر تحديث:** 2025-12-27  
**تم الاختبار مع:** Aspose.Words للـ Java 24.11  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}