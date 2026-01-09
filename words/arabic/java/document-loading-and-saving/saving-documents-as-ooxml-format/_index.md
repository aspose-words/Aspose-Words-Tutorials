---
date: 2026-01-09
description: تعلم كيفية تشفير ملفات docx بكلمة مرور وتغيير مستوى الضغط عند حفظ المستندات
  بصيغة OOXML باستخدام Aspose.Words للغة Java.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: تشفير ملف docx بكلمة مرور – حفظ OOXML باستخدام Aspose.Words Java
url: /ar/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تشفير ملف docx بكلمة مرور – حفظ OOXML باستخدام Aspose.Words Java

## مقدمة حول حفظ المستندات بصيغة OOXML في Aspose.Words for Java

## إجابات سريعة
- **كيف يمكنني حماية ملف Word؟** استخدم `OoxmlSaveOptions.setPassword("yourPassword")` قبل الحفظ.  
- **ما مستوى توافق OOXML الذي يجب أن أختاره؟** ISO 29500 2008 Strict للحصول على أقصى توافق مع إصدارات Office الحديثة.  
- **هل يمكنني الاحتفاظ بأحرف التحكم القديمة؟** نعم، فعّل `setKeepLegacyControlChars(true)`.  
- **كيف يمكنني تغيير مستوى الضغط؟** اضبط `setCompressionLevel(CompressionLevel.SUPER_FAST)` أو `MAXIMUM` حسب الحاجة.  
- **هل تؤثر هذه الخيارات على حجم الملف؟** مستوى الضغط ومعالجة أحرف التحكم القديمة يمكن أن يغيّر حجم ملف .docx النهائي بشكل ملحوظ.

## ما هو “تشفير docx بكلمة مرور”؟
تشفير ملف DOCX يعني أن المستند يُحفظ باستخدام تشفير AES‑256، ويتطلب كلمة مرور لفتحه في Word أو أي عارض متوافق. هذا أمر أساسي لحماية المعلومات السرية عندما يتم مشاركة الملفات عبر البريد الإلكتروني أو التخزين السحابي أو بوابات الإنترانت.

## لماذا نستخدم خيارات حفظ OOXML؟
- **الأمان:** حماية كلمة المرور تمنع الوصول غير المصرح به.  
- **التوافق:** إعدادات التوافق تضمن أن الملف يعمل عبر إصدارات Word المختلفة.  
- **الأداء:** ضبط الضغط يمكن أن يسرّع عملية الحفظ أو يقلل حجم الملف.  
- **الحفظ:** الاحتفاظ بأحرف التحكم القديمة يحافظ على الدقة عند تحويل المستندات القديمة.

## المتطلبات المسبقة
- مكتبة Aspose.Words for Java مضافة إلى مشروعك (Maven/Gradle أو JAR يدوي).  
- Java 8 أو أعلى.  
- مستند مصدر (`.docx` أو `.doc`) تريد معالجته.

## حفظ مستند مع تشفير كلمة المرور
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

> **نصيحة احترافية:** اختر كلمة مرور قوية واحفظها بأمان؛ لا يمكن استعادة كلمة المرور من الملف المشفر.

## ضبط توافق OOXML
يمكنك تحديد مستوى توافق OOXML عند حفظ المستند. على سبيل المثال، يمكنك ضبطه على ISO 29500:2008 (Strict). إليك الطريقة:

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

## تحديث خاصية وقت الحفظ الأخير
يمكنك اختيار تحديث خاصية "وقت الحفظ الأخير" للمستند عند حفظه. إليك الطريقة:

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

## الاحتفاظ بأحرف التحكم القديمة
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

## كيفية تغيير مستوى الضغط عند حفظ OOXML
يمكنك تعديل مستوى الضغط عند حفظ المستند. على سبيل المثال، يمكنك ضبطه على `SUPER_FAST` لأقل ضغط أو `MAXIMUM` لأصغر حجم ملف. إليك الطريقة:

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
في هذا الدليل الشامل، استعرضنا كيفية **تشفير docx بكلمة مرور** وحفظ المستندات بصيغة OOXML باستخدام Aspose.Words for Java. سواء كنت بحاجة إلى حماية ملفاتك، أو ضمان توافق OOXML الصارم، أو تحديث خصائص المستند، أو الحفاظ على أحرف التحكم القديمة، أو **تغيير مستوى الضغط**، فإن Aspose.Words يوفر مجموعة متنوعة من الأدوات لتلبية متطلباتك.

## الأسئلة المتكررة

**س: كيف يمكنني إزالة حماية كلمة المرور من مستند محمي بكلمة مرور؟**  
ج: افتح المستند باستخدام كلمة المرور الصحيحة، ثم احفظه دون تحديد كلمة مرور في `OoxmlSaveOptions`. سيؤدي ذلك إلى إنشاء نسخة غير محمية.

**س: هل يمكنني تعيين خصائص مخصصة عند حفظ مستند بصيغة OOXML؟**  
ج: نعم. استخدم `BuiltInDocumentProperties` و `CustomDocumentProperties` على كائن `Document` قبل استدعاء `save()`.

**س: ما هو مستوى الضغط الافتراضي عند حفظ مستند بصيغة OOXML؟**  
ج: الافتراضي هو `CompressionLevel.NORMAL`. يمكنك التحويل إلى `SUPER_FAST` للسرعة أو `MAXIMUM` لأصغر حجم ملف.

**س: هل سيؤثر تمكين `keepLegacyControlChars` على التوافق مع إصدارات Word الحديثة؟**  
ج: يمكن لـ Word الحديث فتح ملفات تحتوي على أحرف تحكم قديمة، لكن قد تُعرض بعض الميزات القديمة بشكل مختلف. استخدم هذا الخيار فقط عندما تحتاج إلى الحفاظ على المحتوى الأصلي بدقة.

**س: هل يمكن دمج خيارات حفظ متعددة (مثل كلمة المرور + الضغط) في استدعاء واحد؟**  
ج: بالتأكيد. قم بتكوين جميع الخصائص المطلوبة على كائن `OoxmlSaveOptions` واحد قبل تمريره إلى `doc.save()`.

---

**آخر تحديث:** 2026-01-09  
**تم الاختبار مع:** Aspose.Words for Java 24.12  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}