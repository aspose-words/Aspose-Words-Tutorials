---
"description": "تعلّم كيفية حفظ المستندات بتنسيق OOXML باستخدام Aspose.Words لجافا. وفّر الحماية والتحسين والتخصيص لملفاتك بسهولة."
"linktitle": "حفظ المستندات بتنسيق OOXML"
"second_title": "واجهة برمجة تطبيقات معالجة مستندات Java Aspose.Words"
"title": "حفظ المستندات بتنسيق OOXML في Aspose.Words لـ Java"
"url": "/ar/java/document-loading-and-saving/saving-documents-as-ooxml-format/"
"weight": 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# حفظ المستندات بتنسيق OOXML في Aspose.Words لـ Java


## مقدمة لحفظ المستندات بتنسيق OOXML في Aspose.Words لـ Java

في هذا الدليل، سنستكشف كيفية حفظ المستندات بتنسيق OOXML باستخدام Aspose.Words لجافا. OOXML (Office Open XML) هو تنسيق ملفات يستخدمه Microsoft Word وتطبيقات Office الأخرى. سنغطي خيارات وإعدادات مختلفة لحفظ المستندات بتنسيق OOXML.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من إعداد مكتبة Aspose.Words for Java في مشروعك.

## حفظ مستند باستخدام تشفير كلمة المرور

يمكنك تشفير مستندك بكلمة مرور مع حفظه بتنسيق OOXML. إليك الطريقة:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// تحميل المستند
Document doc = new Document("Document.docx");

// إنشاء OoxmlSaveOptions وتعيين كلمة المرور
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// حفظ المستند بالتشفير
doc.save("EncryptedDoc.docx", saveOptions);
```

## إعداد التوافق مع OOXML

يمكنك تحديد مستوى توافق OOXML عند حفظ المستند. على سبيل المثال، يمكنك ضبطه على ISO 29500:2008 (صارم). إليك الطريقة:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// تحميل المستند
Document doc = new Document("Document.docx");

// تحسين لـ Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// إنشاء OoxmlSaveOptions وتعيين مستوى الامتثال
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// حفظ المستند بإعدادات التوافق
doc.save("ComplianceDoc.docx", saveOptions);
```

## تحديث خاصية آخر وقت تم حفظه

يمكنك اختيار تحديث خاصية "آخر وقت حفظ" للمستند عند حفظه. إليك الطريقة:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// تحميل المستند
Document doc = new Document("Document.docx");

// إنشاء OoxmlSaveOptions وتمكين تحديث خاصية Last Saved Time
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// احفظ المستند بالخاصية المحدثة
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## الحفاظ على شخصيات التحكم القديمة

إذا كان مستندك يحتوي على أحرف تحكم قديمة، يمكنك اختيار الاحتفاظ بها أثناء الحفظ. إليك الطريقة:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// تحميل مستند يحتوي على أحرف تحكم قديمة
Document doc = new Document("LegacyControlChars.doc");

// إنشاء OoxmlSaveOptions بتنسيق FLAT_OPC وتمكين الاحتفاظ بأحرف التحكم القديمة
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// حفظ المستند باستخدام أحرف التحكم القديمة
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## ضبط مستوى الضغط

يمكنك ضبط مستوى الضغط عند حفظ المستند. على سبيل المثال، يمكنك ضبطه على SUPER_FAST لضغط أقل. إليك الطريقة:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// تحميل المستند
Document doc = new Document("Document.docx");

// إنشاء OoxmlSaveOptions وتعيين مستوى الضغط
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// احفظ المستند بمستوى الضغط المحدد
doc.save("FastCompressionDoc.docx", saveOptions);
```

هذه بعض الخيارات والإعدادات الرئيسية التي يمكنك استخدامها لحفظ المستندات بتنسيق OOXML باستخدام Aspose.Words لجافا. لا تتردد في استكشاف المزيد من الخيارات وتخصيص عملية حفظ المستندات حسب الحاجة.

## الكود المصدري الكامل لحفظ المستندات بتنسيق OOXML في Aspose.Words لـ Java

```java
public void encryptDocxWithPassword() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setPassword("password"); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.EncryptDocxWithPassword.docx", saveOptions);
}
@Test
public void ooxmlComplianceIso29500_2008_Strict() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.OoxmlComplianceIso29500_2008_Strict.docx", saveOptions);
}
@Test
public void updateLastSavedTimeProperty() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setUpdateLastSavedTimeProperty(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
}
@Test
public void keepLegacyControlChars() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Legacy control character.doc");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setKeepLegacyControlChars(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
}
@Test
public void setCompressionLevel() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.SetCompressionLevel.docx", saveOptions);
}
```

## خاتمة

في هذا الدليل الشامل، استكشفنا كيفية حفظ المستندات بتنسيق OOXML باستخدام Aspose.Words لجافا. سواءً كنت بحاجة إلى تشفير مستنداتك بكلمات مرور، أو ضمان التوافق مع معايير OOXML المحددة، أو تحديث خصائص المستند، أو الحفاظ على أحرف التحكم القديمة، أو ضبط مستويات الضغط، يوفر Aspose.Words مجموعة متنوعة من الأدوات لتلبية احتياجاتك.

## الأسئلة الشائعة

### كيف يمكنني إزالة حماية كلمة المرور من مستند محمي بكلمة مرور؟

لإزالة الحماية بكلمة مرور من مستند محمي بكلمة مرور، يمكنك فتح المستند بكلمة المرور الصحيحة ثم حفظه دون تحديد كلمة مرور في خيارات الحفظ. سيؤدي هذا إلى حفظ المستند بدون حماية بكلمة مرور.

### هل يمكنني تعيين خصائص مخصصة عند حفظ مستند بتنسيق OOXML؟

نعم، يمكنك تعيين خصائص مخصصة للمستند قبل حفظه بتنسيق OOXML. استخدم `BuiltInDocumentProperties` و `CustomDocumentProperties` الفئات لتعيين خصائص مختلفة مثل المؤلف والعنوان والكلمات الأساسية والخصائص المخصصة.

### ما هو مستوى الضغط الافتراضي عند حفظ مستند بتنسيق OOXML؟

مستوى الضغط الافتراضي عند حفظ مستند بتنسيق OOXML باستخدام Aspose.Words لـ Java هو `NORMAL`. يمكنك تغيير مستوى الضغط إلى `SUPER_FAST` أو `MAXIMUM` حسب الحاجة.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}