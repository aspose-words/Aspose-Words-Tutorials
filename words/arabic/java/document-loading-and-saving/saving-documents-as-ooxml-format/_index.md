---
date: 2025-12-29
description: تعلم كيفية تشفير ملفات docx باستخدام كلمة مرور عبر خيارات الحفظ في Aspose.Words للجافا.
  احمِ، حسّن، وخصّص ملفات OOXML الخاصة بك بسهولة.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: كيفية تشفير ملف DOCX بكلمة مرور باستخدام Aspose.Words للغة Java
url: /ar/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تشفير ملف DOCX باستخدام كلمة مرور مع Aspose.Words for Java

في هذا الدليل ستكتشف **كيفية تشفير ملف docx باستخدام كلمة مرور** أثناء حفظ المستندات بصيغة OOXML باستخدام Aspose.Words for Java. سواءً كنت تحمي تقارير سرية أو تأمن مسودات عقود، توضح الخطوات أدناه بالضبط كيفية تطبيق حماية كلمة المرور وضبط خيارات حفظ OOXML الأخرى.

## إجابات سريعة
- **هل يمكنني تشفير ملف DOCX باستخدام كلمة مرور؟** نعم، استخدم `OoxmlSaveOptions.setPassword()` قبل الحفظ.  
- **أي فئة تتحكم في إعدادات حفظ OOXML؟** `OoxmlSaveOptions` (جزء من Aspose.Words).  
- **هل أحتاج إلى ترخيص لحماية كلمة المرور؟** يلزم وجود ترخيص صالح لـ Aspose.Words للاستخدام في بيئة الإنتاج.  
- **هل يمكنني دمج التشفير مع إعدادات الامتثال؟** بالتأكيد – قم بتعيين كل من `setPassword` و `setCompliance` على نفس كائن `OoxmlSaveOptions`.  
- **ما هي مستويات الضغط المتاحة؟** `NORMAL`، `SUPER_FAST`، و `MAXIMUM` عبر `CompressionLevel`.

## ما هو “encrypt docx with password”؟
تشفير ملف DOCX يعني أن محتويات الملف تُخزن بشكل مشفر ولا يمكن فتحه إلا بعد إدخال كلمة المرور الصحيحة. هذا يحمي المعلومات الحساسة من الوصول غير المصرح به مع السماح لأدوات Word القياسية بفتح الملف بمجرد توفير كلمة المرور.

## لماذا نستخدم خيارات حفظ Aspose.Words للتشفير؟
توفر Aspose.Words مجموعة غنية من **aspose words save options** التي تتيح لك التحكم ليس فقط في التشفير بل أيضاً في مستويات الامتثال، الضغط، ومعالجة الأحرف القديمة – كل ذلك من خلال كود Java. هذا يلغي الحاجة إلى معالجة يدوية بعد الحفظ أو أدوات طرف ثالث.

## المتطلبات المسبقة
- مجموعة تطوير Java (JDK 8 أو أعلى)  
- مكتبة Aspose.Words for Java مضافة إلى مشروعك (Maven/Gradle أو JAR)  
- ترخيص صالح لـ Aspose.Words للاستخدام في الإنتاج (اختياري للتقييم)

## حفظ مستند مع تشفير كلمة مرور

يمكنك تشفير مستندك بكلمة مرور أثناء حفظه بصيغة OOXML. إليك الطريقة:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the password
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Save the document with encryption
doc.save("EncryptedDoc.docx", saveOptions);
```

## ضبط امتثال OOXML

يمكنك تحديد مستوى امتثال OOXML عند حفظ المستند. على سبيل المثال، يمكنك ضبطه على ISO 29500:2008 (Strict). إليك الطريقة:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Load the document
Document doc = new Document("Document.docx");

// Optimize for Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Create OoxmlSaveOptions and set the compliance level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Save the document with compliance setting
doc.save("ComplianceDoc.docx", saveOptions);
```

## تحديث خاصية “Last Saved Time”

يمكنك اختيار تحديث خاصية “Last Saved Time” للمستند عند الحفظ. إليك الطريقة:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and enable updating the Last Saved Time property
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Save the document with the updated property
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## الحفاظ على أحرف التحكم القديمة

إذا كان مستندك يحتوي على أحرف تحكم قديمة، يمكنك اختيار الاحتفاظ بها أثناء الحفظ. إليك الطريقة:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// Load a document with legacy control characters
Document doc = new Document("LegacyControlChars.doc");

// Create OoxmlSaveOptions with the FLAT_OPC format and enable keeping legacy control characters
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Save the document with legacy control characters
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## ضبط مستوى الضغط

يمكنك تعديل مستوى الضغط عند حفظ المستند. على سبيل المثال، يمكنك ضبطه على **SUPER_FAST** للحصول على أقل ضغط ممكن. إليك الطريقة:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the compression level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Save the document with the specified compression level
doc.save("FastCompressionDoc.docx", saveOptions);
```

هذه بعض الخيارات والإعدادات الرئيسية التي يمكنك استخدامها عند حفظ المستندات بصيغة OOXML باستخدام Aspose.Words for Java. لا تتردد في استكشاف المزيد من الخيارات وتخصيص عملية حفظ المستند حسب الحاجة.

## الكود الكامل لحفظ المستندات بصيغة OOXML في Aspose.Words for Java

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

## الخلاصة

في هذا الدليل الشامل، استعرضنا كيفية **encrypt docx with password** وضبط مجموعة من خيارات حفظ OOXML باستخدام Aspose.Words for Java. سواءً كنت تحتاج إلى حماية محتوى سري، أو الالتزام بمعايير ISO الصارمة، أو الحفاظ على الأحرف القديمة، أو التحكم في مستوى الضغط، توفر المكتبة تحكمًا دقيقًا عبر نفس واجهة برمجة `OoxmlSaveOptions`.

## الأسئلة المتكررة

**س: كيف يمكنني إزالة حماية كلمة المرور من مستند محمي بكلمة مرور؟**  
ج: افتح المستند باستخدام كلمة المرور الصحيحة، ثم احفظه مرة أخرى دون استدعاء `setPassword`. سيصبح الملف الجديد غير محمي.

**س: هل يمكنني تعيين خصائص مخصصة عند حفظ مستند بصيغة OOXML؟**  
ج: نعم. استخدم `BuiltInDocumentProperties` أو `CustomDocumentProperties` على كائن `Document` قبل استدعاء `save`.

**س: ما هو مستوى الضغط الافتراضي عند حفظ مستند بصيغة OOXML؟**  
ج: الافتراضي هو `NORMAL`. يمكنك التحويل إلى `SUPER_FAST` للسرعة أو `MAXIMUM` للحصول على حجم ملف أصغر.

**س: هل تعمل خيارات حفظ aspose words مع إصدارات Word القديمة؟**  
ج: نعم. من خلال ضبط `MsWordVersion` وإعدادات الامتثال، يمكنك استهداف Word 2007‑2019 وضمان التوافق.

**س: هل يمكن دمج عدة خيارات حفظ في عملية واحدة؟**  
ج: بالتأكيد. أنشئ كائنًا واحدًا من `OoxmlSaveOptions`، عيّن جميع الخصائص المطلوبة (كلمة المرور، الامتثال، الضغط، إلخ)، ومرره إلى `doc.save()`.

---

**آخر تحديث:** 2025-12-29  
**تم الاختبار مع:** Aspose.Words for Java 24.12  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}