---
"description": "إتقان خيارات التحميل في Aspose.Words لجافا. خصّص تحميل المستندات، وتشفيرها، وتحويل الأشكال، وتعيين إصدارات Word، والمزيد لمعالجة مستندات جافا بكفاءة."
"linktitle": "استخدام خيارات التحميل"
"second_title": "واجهة برمجة تطبيقات معالجة مستندات Java Aspose.Words"
"title": "استخدام خيارات التحميل في Aspose.Words لـ Java"
"url": "/ar/java/document-loading-and-saving/using-load-options/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# استخدام خيارات التحميل في Aspose.Words لـ Java


## مقدمة للعمل مع خيارات التحميل في Aspose.Words لـ Java

في هذا البرنامج التعليمي، سنستكشف كيفية استخدام خيارات التحميل في Aspose.Words لجافا. تتيح لك هذه الخيارات تخصيص كيفية تحميل المستندات ومعالجتها. سنغطي سيناريوهات مختلفة، بما في ذلك تحديث الحقول غير المكتملة، وتحميل المستندات المشفرة، وتحويل الأشكال إلى Office Math، وتعيين إصدار MS Word، وتحديد مجلد مؤقت، ومعالجة التحذيرات، وتحويل ملفات التعريف إلى PNG. لنبدأ خطوة بخطوة.

## تحديث الحقول المتسخة

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

يوضح هذا المقطع من التعليمات البرمجية كيفية تحديث الحقول المتسخة في مستند. `setUpdateDirtyFields(true)` يتم استخدام الطريقة للتأكد من تحديث الحقول المتسخة أثناء تحميل المستند.

## تحميل مستند مشفر

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

هنا، نقوم بتحميل مستند مشفر باستخدام كلمة مرور. `LoadOptions` يقبل المنشئ كلمة مرور المستند، ويمكنك أيضًا تحديد كلمة مرور جديدة عند حفظ المستند باستخدام `OdtSaveOptions`.

## تحويل الشكل إلى رياضيات مكتبية

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

يوضح هذا الكود كيفية تحويل الأشكال إلى كائنات Office Math أثناء تحميل المستند. `setConvertShapeToOfficeMath(true)` تتيح هذه الطريقة إجراء هذا التحويل.

## تعيين إصدار MS Word

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

يمكنك تحديد إصدار مايكروسوفت وورد لتحميل المستند. في هذا المثال، قمنا بتعيين الإصدار إلى مايكروسوفت وورد ٢٠١٠ باستخدام `setMswVersion`.

## استخدام المجلد المؤقت

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

عن طريق تعيين المجلد المؤقت باستخدام `setTempFolder`يمكنك التحكم في مكان تخزين الملفات المؤقتة أثناء معالجة المستندات.

## استدعاء تحذيري

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // تعامل مع التحذيرات فور ظهورها أثناء تحميل المستندات.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

يوضح هذا الكود كيفية إعداد استدعاء تحذيري للتعامل مع التحذيرات أثناء تحميل المستندات. يمكنك تخصيص سلوك تطبيقك عند ظهور التحذيرات.

## تحويل ملفات التعريف إلى PNG

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

لتحويل ملفات التعريف (مثل WMF) إلى صور PNG أثناء تحميل المستند، يمكنك استخدام `setConvertMetafilesToPng(true)` طريقة.

## كود المصدر الكامل للعمل مع خيارات التحميل في Aspose.Words لـ Java

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
	// إنشاء كائن LoadOptions جديد، والذي سيقوم بتحميل المستندات وفقًا لمواصفات MS Word 2019 افتراضيًا
	// وتغيير إصدار التحميل إلى Microsoft Word 2010.
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
		// يطبع التحذيرات وتفاصيلها عند ظهورها أثناء تحميل المستند.
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

## خاتمة

في هذا البرنامج التعليمي، تناولنا جوانب مختلفة من استخدام خيارات التحميل في Aspose.Words لجافا. تلعب خيارات التحميل دورًا محوريًا في تخصيص طريقة تحميل المستندات ومعالجتها، مما يسمح لك بتخصيص معالجة مستنداتك وفقًا لاحتياجاتك الخاصة. لنلخص النقاط الرئيسية التي تناولها هذا الدليل:

## الأسئلة الشائعة

### كيف يمكنني التعامل مع التحذيرات أثناء تحميل المستند؟

يمكنك إعداد مكالمة تحذيرية كما هو موضح في `warningCallback()` الطريقة المذكورة أعلاه. قم بتخصيص `DocumentLoadingWarningCallback` فئة للتعامل مع التحذيرات وفقًا لمتطلبات تطبيقك.

### هل يمكنني تحويل الأشكال إلى كائنات Office Math عند تحميل مستند؟

نعم، يمكنك تحويل الأشكال إلى كائنات Office Math باستخدام `loadOptions.setConvertShapeToOfficeMath(true)`.

### كيف يمكنني تحديد إصدار MS Word لتحميل المستند؟

يستخدم `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` لتحديد إصدار MS Word لتحميل المستند.

### ما هو الغرض من `setTempFolder` الطريقة في خيارات التحميل؟

ال `setTempFolder` تسمح لك الطريقة بتحديد المجلد الذي سيتم تخزين الملفات المؤقتة فيه أثناء معالجة المستندات.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}