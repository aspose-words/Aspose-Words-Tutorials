---
date: '2026-02-06'
description: تعلم كيفية تحميل HTML VML باستخدام Aspose.Words for Java، تشفير ملفات
  HTML Java، تعيين URI الأساسي للـ HTML، وتكوين خيارات التحكم في HTML.
keywords:
- Aspose.Words for Java
- HTML document processing
- document encryption
title: تحميل HTML VML باستخدام Aspose.Words للـ Java – دليل كامل
url: /ar/java/document-operations/aspose-words-java-html-features-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# ميزات HTML الشاملة مع Aspose.Words for Java: دليل المطور

## المقدمة

التنقل في عالم معالجة المستندات المعقد يمكن أن يكون مرهقًا، خاصةً عند التعامل مع ميزات HTML المتنوعة. سواء كنت تتعامل مع دعم لغة العلامات المتجهة (VML)، أو المستندات المشفرة، أو سلوكيات استيراد HTML المحددة، فإن **Aspose.Words for Java** يقدم حلاً قويًا. في هذا الدليل، ستتعلم **how to load html vml** بكفاءة وأمان، بالإضافة إلى تغطية مهام ذات صلة مثل **encrypt html java**، **set html base uri**، و **configure html control**.

ما ستتعلمه:
- كيفية تحميل مستندات HTML بدعم VML.
- تقنيات التعامل مع HTML ثابت الصفحة والتحذيرات.
- طرق تشفير وتحميل مستندات HTML محمية بكلمة مرور.
- استخدام عناوين URI الأساسية في خيارات تحميل HTML.
- استيراد عناصر إدخال HTML كعلامات مستند منسقة أو حقول نموذج.
- تجاهل عناصر `<noscript>` أثناء تحميل HTML.
- تكوين أوضاع استيراد الكتل للتحكم في الحفاظ على بنية HTML.
- دعم قواعد `@font-face` للخطوط المخصصة.

## إجابات سريعة
- **ما هي الطريقة الأساسية لتمكين VML عند تحميل HTML؟** Set `loadOptions.setSupportVml(true)`.
- **هل يمكنني تحميل ملفات HTML محمية بكلمة مرور؟** Yes, pass the password to `HtmlLoadOptions`.
- **كيف يمكنني حل مسارات الصور النسبية؟** Use `loadOptions.setBaseUri("your/base/uri")`.
- **هل من الممكن استيراد `<select>` كحقل نموذج؟** Set `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)`.
- **ما هو الصنف الذي يلتقط التحذيرات أثناء التحميل؟** Implement `IWarningCallback` and assign it to `loadOptions.setWarningCallback(...)`.

## المتطلبات المسبقة

قبل أن نبدأ بتنفيذ ميزات HTML المختلفة باستخدام Aspose.Words for Java، تأكد من إعداد بيئتك بشكل صحيح:

- **المكتبات المطلوبة:** تحتاج إلى مكتبة Aspose.Words الإصدار 25.3 أو أحدث.
- **بيئة التطوير:** يفترض هذا الدليل أنك تستخدم إما Maven أو Gradle لإدارة التبعيات.
- **قاعدة المعرفة:** فهم أساسي للغة Java ومعرفة بمستندات HTML سيكون مفيدًا.

## إعداد Aspose.Words

لبدء العمل مع Aspose.Words، تحتاج أولاً إلى تضمينه في مشروعك. فيما يلي الخطوات لإعداد المكتبة باستخدام Maven و Gradle:

### Maven

أضف التبعيات التالية إلى ملف `pom.xml` الخاص بك:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle

قم بتضمين هذا في ملف `build.gradle` الخاص بك:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### الحصول على الترخيص

يتطلب Aspose.Words ترخيصًا للحصول على الوظائف الكاملة. يمكنك الحصول على نسخة تجريبية مجانية، طلب ترخيص مؤقت، أو شراء ترخيص دائم. زر [صفحة الشراء](https://purchase.aspose.com/buy) للمزيد من التفاصيل.

لتهيئة Aspose.Words في مشروع Java الخاص بك، تأكد من إعداد الترخيص بشكل صحيح:

```java
import com.aspose.words.License;

public class InitializeAspose {
    public static void main(String[] args) throws Exception {
        License license = new License();
        license.setLicense("path/to/your/license/file.lic");
        
        System.out.println("Aspose.Words is ready to use!");
    }
}
```

## دليل التنفيذ

سنقسم التنفيذ إلى أقسام بناءً على الميزات التي نرغب في تنفيذها.

### كيفية تحميل html vml باستخدام Aspose.Words

**نظرة عامة:** يسمح تحميل مستند HTML بدعم VML بعرض مرن للرسومات المتجهة مثل المخططات والأشكال. هذه هي الخطوة الأساسية للكلمة المفتاحية الرئيسية **load html vml**.

#### خطوة بخطوة

1. **إعداد خيارات التحميل**

```java
import com.aspose.words.Document;
import com.aspose.words.HtmlLoadOptions;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setSupportVml(true); // Enable VML support
```

2. **تحميل المستند**

```java
Document doc = new Document("path/to/VML conditional.htm", loadOptions);
```

3. **التحقق من نوع الصورة**

```java
import com.aspose.words.NodeType;
import com.aspose.words.Shape;

Shape imageShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
String expectedImageType = "JPG"; // Adjust based on actual logic

if (!imageShape.getImageData().getImageType().toString().equals(expectedImageType)) {
    throw new AssertionError("Unexpected image type loaded.");
}
```

### تحميل HTML ثابت ومعالجة التحذيرات

**نظرة عامة:** قد ينتج عن تحميل مستندات HTML ثابتة الصفحات تحذيرات تحتاج إلى إدارة للحصول على معالجة دقيقة.

#### خطوة بخطوة

1. **تعريف رد نداء التحذير**

```java
import com.aspose.words.IWarningCallback;
import com.aspose.words.WarningInfo;
import java.util.ArrayList;

private static class ListDocumentWarnings implements IWarningCallback {
    private final ArrayList<WarningInfo> mWarnings = new ArrayList<>();

    public void warning(WarningInfo info) { 
        mWarnings.add(info); 
    }

    public ArrayList<WarningInfo> warnings() { return mWarnings; }
}
```

2. **تكوين خيارات التحميل**

```java
HtmlLoadOptions loadOptions = new HtmlLoadOptions();
ListDocumentWarnings warningCallback = new ListDocumentWarnings();
loadOptions.setWarningCallback(warningCallback);
```

3. **تحميل المستند والتحقق من التحذيرات**

```java
Document doc = new Document("path/to/HtmlFixed.html", loadOptions);

if (warningCallback.warnings().size() != 1) {
    throw new AssertionError("Unexpected number of warnings.");
}
```

### تشفير مستندات HTML

**نظرة عامة:** يضمن تشفير مستند HTML بكلمة مرور وصولًا آمنًا، وهو أمر أساسي للمعلومات الحساسة—هذا يلبي سيناريو **encrypt html java**.

#### خطوة بخطوة

1. **تحضير خيارات التوقيع الرقمي**

```java
import com.aspose.words.CertificateHolder;
import com.aspose.words.DigitalSignatureUtil;
import com.aspose.words.SignOptions;

CertificateHolder certificateHolder = CertificateHolder.create("path/to/morzal.pfx", "aw");
SignOptions signOptions = new SignOptions();
signOptions.setComments("Comment");
signOptions.setSignTime(new Date());
signOptions.setDecryptionPassword("docPassword");
```

2. **توقيع وتشفير المستند**

```java
String inputFileName = "path/to/Encrypted.docx";
String outputFileName = "path/to/output/directory/HtmlLoadOptions.EncryptedHtml.html";

DigitalSignatureUtil.sign(inputFileName, outputFileName, certificateHolder, signOptions);
```

3. **تحميل المستند المشفر**

```java
import com.aspose.words.Document;

HtmlLoadOptions loadOptions = new HtmlLoadOptions("docPassword");
Document doc = new Document(outputFileName, loadOptions);

if (!doc.getText().trim().equals("Test encrypted document.")) {
    throw new AssertionError("Unexpected document text.");
}
```

### عنوان URI الأساسي لخيارات تحميل HTML

**نظرة عامة:** يساعد تحديد **set html base uri** في حل عناوين URI النسبية، خاصةً عند التعامل مع الصور أو الموارد المرتبطة الأخرى.

#### خطوة بخطوة

1. **تكوين خيارات التحميل مع عنوان URI الأساسي**

```java
HtmlLoadOptions loadOptions = new HtmlLoadOptions(LoadFormat.HTML, "", "path/to/imageDir");
```

2. **تحميل المستند والتحقق من الصورة**

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;

Document doc = new Document("path/to/Missing image.html", loadOptions);
Shape imageShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);

if (!imageShape.isImage()) {
    throw new AssertionError("Expected an image shape.");
}
```

### استيراد عنصر HTML Select كعلامة مستند منسقة

**نظرة عامة:** لتعديل سلوك **configure html control**، يمكنك استيراد عناصر `<select>` كعلامات مستند منسقة، مما يمنحك تحكمًا أدق في حقول النماذج داخل مستندات Word.

#### خطوة بخطوة

1. **تحديد نوع التحكم المفضل**

```java
import com.aspose.words.HtmlLoadOptions;
import com.aspose.words.ControlType;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag);
```

2. **تحميل المستند والتحقق من البنية**

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.StructuredDocumentTag;

Document doc = new Document("path/to/Input HTML with select element.html", loadOptions);
StructuredDocumentTag sdt = (StructuredDocumentTag)doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (!sdt.getTagName().equals("Select")) {
    throw new AssertionError("Expected a Structured Document Tag with tag name 'Select'.");
}
```

## المشكلات الشائعة والحلول

| المشكلة | السبب | الحل |
|---------|-------|------|
| الرسومات VML لا تظهر | تم ترك علم `supportVml` على القيمة الافتراضية (`false`) | تأكد من استدعاء `loadOptions.setSupportVml(true)` قبل التحميل. |
| الصور مفقودة بعد التحميل | لا يمكن حل المسارات النسبية | استخدم **set html base uri** (`loadOptions.setBaseUri(...)`) لتوجيه إلى المجلد الصحيح. |
| HTML محمي بكلمة مرور يسبب استثناء | لم يتم توفير كلمة المرور | مرّر كلمة المرور إلى `new HtmlLoadOptions("yourPassword")`. |
| عناصر التحكم في النموذج تظهر كنص عادي | `HtmlControlType` غير صحيح | قم بتعيين `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` أو `FormField` حسب الحاجة. |
| تحذيرات غير متوقعة | عناصر HTML غير معالجة | نفّذ `IWarningCallback` لالتقاط ومراجعة التحذيرات. |

## الأسئلة المتكررة

**س: هل يمكنني تحميل ملفات HTML تحتوي على كل من رسومات VML و SVG الحديثة؟**  
**ج:** نعم. فعّل VML باستخدام `setSupportVml(true)`؛ يتم التعامل مع SVG تلقائيًا بواسطة Aspose.Words.

**س: كيف يمكنني تشفير مستند HTML دون استخدام شهادة رقمية؟**  
**ج:** استخدم مُنشئ `HtmlLoadOptions` الذي يقبل كلمة مرور واحفظ المستند باستخدام `Document.save(..., SaveFormat.HTML)` بعد تعيين كلمة المرور.

**س: ماذا يحدث إذا كان عنوان URI الأساسي يشير إلى مجلد غير موجود؟**  
**ج:** سيطلق Aspose.Words استثناء `FileNotFoundException` للموارد المفقودة. تحقق من المسار قبل التحميل.

**س: هل يمكن تغيير نوع التحكم الافتراضي لجميع عناصر نموذج HTML؟**  
**ج:** نعم. استخدم `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` لتطبيقه عالميًا.

**س: هل ردود نداء التحذير آمنة في بيئات متعددة الخيوط؟**  
**ج:** يجب أن تكون تنفيذات رد النداء آمنة في بيئات متعددة الخيوط إذا كنت تخطط لتحميل المستندات بشكل متزامن. استخدم مجموعات متزامنة أو تخزين محلي لكل خيط.

---

**آخر تحديث:** 2026-02-06  
**تم الاختبار مع:** Aspose.Words for Java 25.3  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}