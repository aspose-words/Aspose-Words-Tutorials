---
"date": "2025-03-28"
"description": "تعرّف على كيفية أتمتة توقيع المستندات باستخدام Aspose.Words لجافا. يغطي هذا البرنامج التعليمي إعداد بيئتك، وإنشاء بيانات اختبار، وإضافة أسطر توقيع، وتوقيع المستندات رقميًا."
"title": "أتمتة توقيع المستندات في جافا باستخدام Aspose.Words - دليل شامل"
"url": "/ar/java/mail-merge-reporting/aspose-words-java-document-signing-tutorial/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# أتمتة توقيع المستندات في جافا باستخدام Aspose.Words: دليل شامل

## مقدمة

في عالم الأعمال سريع الخطى اليوم، تُعدّ إدارة المستندات بكفاءة أمرًا بالغ الأهمية. أتمتة إنشاء المستندات وتوقيعها رقميًا تُوفّر الوقت وتُقلّل الأخطاء. سيُرشدك هذا البرنامج التعليمي إلى كيفية استخدام Aspose.Words لجافا لإنشاء بيانات اختبار للموقّعين، وإضافة أسطر توقيع، وتوقيع المستندات رقميًا.

**ما سوف تتعلمه:**
- إعداد Aspose.Words في مشروع Java
- إنشاء بيانات توقيع الاختبار باستخدام Java
- إضافة أسطر التوقيع إلى مستندات Word
- التوقيع الرقمي على المستندات باستخدام الشهادات الرقمية

لنبدأ بإعداد بيئة التطوير الخاصة بك!

## المتطلبات الأساسية

قبل الخوض في البرنامج التعليمي، تأكد من أن الإعداد الخاص بك يلبي المتطلبات التالية:

- **مجموعة تطوير Java (JDK):** الإصدار 8 أو أعلى.
- **بيئة التطوير المتكاملة (IDE):** مثل IntelliJ IDEA أو Eclipse.
- **كلمات Aspose.Words لـ Java:** يمكن تضمين هذه المكتبة عبر Maven أو Gradle.

### متطلبات المعرفة

سيكون من المفيد فهم أساسيات برمجة جافا والإلمام بكيفية التعامل مع الملفات والتدفقات. إذا كنت جديدًا على Aspose، فلا تقلق، سنغطي الأساسيات.

## إعداد Aspose.Words

لاستخدام Aspose.Words for Java في مشروعك، اتبع الخطوات التالية:

### تبعية Maven

أضف التبعية التالية إلى ملفك `pom.xml` ملف:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### اعتماد Gradle

بالنسبة لمشاريع Gradle، قم بتضمين هذا السطر في `build.gradle` ملف:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### الحصول على الترخيص

توفر Aspose خيارات ترخيص مختلفة:

- **نسخة تجريبية مجانية:** قم بتنزيل نسخة تجريبية مجانية لاختبار الميزات.
- **رخصة مؤقتة:** الحصول على ترخيص مؤقت لأغراض التقييم.
- **شراء:** للحصول على إمكانية الوصول الكامل، قم بشراء ترخيص من موقع Aspose الإلكتروني.

تأكد من إعداد مشروعك بالتبعيات اللازمة والتراخيص اللازمة. سيسمح لك هذا الإعداد بالاستفادة من إمكانيات Aspose القوية في معالجة المستندات بسلاسة.

## دليل التنفيذ

سنتناول كل ميزة خطوة بخطوة، بدءًا من إنشاء بيانات توقيع الاختبار.

### الميزة 1: إنشاء بيانات اختبار للموقعين

#### ملخص

تُنشئ هذه الميزة قائمةً بالموقّعين بمعرفاتٍ وأسماءٍ ومناصبٍ وصورٍ فريدة. تُعد هذه الميزة ضروريةً لاختبار سيناريوهات توقيع المستندات دون استخدام بياناتٍ فعلية.

##### الخطوة 1: إعداد فئة Java الخاصة بك

إنشاء فئة باسم `SignPersonCreator` واستيراد المكتبات الضرورية:

```java
import java.io.ByteArrayOutputStream;
import java.io.FileInputStream;
import java.io.IOException;
import java.io.InputStream;
import java.util.ArrayList;
import java.util.UUID;

class DocumentHelper {
    public static byte[] getBytesFromStream(InputStream inputStream) throws IOException {
        int numRead; 
        byte[] buffer = new byte[1024]; 
        ByteArrayOutputStream baos = new ByteArrayOutputStream();

        while ((numRead = inputStream.read(buffer)) != -1) {
            baos.write(buffer, 0, numRead);
        }
        return baos.toByteArray();
    }
}

public class SignPersonCreator {
    private static ArrayList<SignPersonTestClass> gSignPersonList;

    public static void main(String[] args) throws IOException {
        createSignPersonData();
        System.out.println("Test data successfully added!");
    }

    private static void createSignPersonData() throws IOException {
        InputStream inputStream = new FileInputStream(YOUR_DOCUMENT_DIRECTORY + "Logo.jpg");

        gSignPersonList = new ArrayList<>();
        gSignPersonList.add(new SignPersonTestClass(UUID.randomUUID(), "Ron Williams", "Chief Executive Officer",
                DocumentHelper.getBytesFromStream(inputStream)));
        gSignPersonList.add(new SignPersonTestClass(UUID.randomUUID(), "Stephen Morse", "Head of Compliance",
                DocumentHelper.getBytesFromStream(inputStream)));
    }
}
```

##### توضيح

- **معرف UUID:** إنشاء معرف فريد لكل موقع.
- **الحصول على بايتات من التدفق:** يقوم بتحويل ملف صورة إلى مجموعة بايتات للتخزين.

### الميزة 2: إضافة سطر التوقيع إلى المستند

#### ملخص

تضيف هذه الميزة سطر توقيع إلى مستندك، وتربطه بتفاصيل الموقع.

##### الخطوة 1: إنشاء فئة SignatureLineAdder

تنفيذ `SignatureLineAdder` الصف على النحو التالي:

```java
import com.aspose.words.*;

class SignatureLineAdder {
    public static void main(String[] args) throws Exception {
        String srcDocumentPath = YOUR_DOCUMENT_DIRECTORY + "Document.docx";
        String dstDocumentPath = YOUR_OUTPUT_DIRECTORY + "SignDocumentCustom.Sign.docx";
        
        SignPersonTestClass signPersonInfo = gSignPersonList.stream()
                .filter(x -> x.getName().equals("Ron Williams")).findFirst().orElse(null);

        if (signPersonInfo != null) {
            addSignatureLine(srcDocumentPath, dstDocumentPath, signPersonInfo);
            System.out.println("Signature line added successfully!");
        } else {
            System.out.println("Sign person does not exist, please check your parameters.");
        }
    }

    private static void addSignatureLine(final String srcDocumentPath, final String dstDocumentPath,
                                         final SignPersonTestClass signPersonInfo) throws Exception {
        Document document = new Document(srcDocumentPath);
        DocumentBuilder builder = new DocumentBuilder(document);

        SignatureLineOptions signatureLineOptions = new SignatureLineOptions();
        signatureLineOptions.setSigner(signPersonInfo.getName());
        signatureLineOptions.setSignerTitle(signPersonInfo.getPosition());

        SignatureLine signatureLine = builder.insertSignatureLine(signatureLineOptions).getSignatureLine();
        signatureLine.setId(String.valueOf(signPersonInfo.getPersonId()));

        builder.getDocument().save(dstDocumentPath);
    }
}
```

##### توضيح

- **خيارات سطر التوقيع:** يقوم بتكوين اسم المُوقّع ولقبه.
- **إدراج سطر التوقيع:** يقوم بإدراج سطر التوقيع في المستند عند موضع المؤشر الحالي.

### الميزة 3: توقيع المستند باستخدام شهادة رقمية

#### ملخص

تقوم هذه الميزة بتوقيع المستند رقميًا باستخدام شهادة رقمية، مما يضمن صحته وسلامته.

##### الخطوة 1: إنشاء فئة DocumentSigner

تنفيذ `DocumentSigner` فصل:

```java
import com.aspose.words.*;

class DocumentSigner {
    public static void main(String[] args) throws Exception {
        String srcDocumentPath = YOUR_DOCUMENT_DIRECTORY + "Document.docx";
        String dstDocumentPath = YOUR_OUTPUT_DIRECTORY + "SignDocumentCustom.Sign.docx";
        String certificatePath = YOUR_DOCUMENT_DIRECTORY + "morzal.pfx";
        String certificatePassword = "aw";

        SignPersonTestClass signPersonInfo = gSignPersonList.stream()
                .filter(x -> x.getName().equals("Ron Williams")).findFirst().orElse(null);

        if (signPersonInfo != null) {
            signDocument(srcDocumentPath, dstDocumentPath, signPersonInfo, certificatePath, certificatePassword);
            System.out.println("Document successfully signed!");
        } else {
            System.out.println("Sign person does not exist, please check your parameters.");
        }
    }

    private static void signDocument(final String srcDocumentPath, final String dstDocumentPath,
                                     final SignPersonTestClass signPersonInfo, final String certificatePath,
                                     final String certificatePassword) throws Exception {
        Document document = new Document(dstDocumentPath);

        CertificateHolder certificateHolder = CertificateHolder.create(certificatePath, certificatePassword);

        SignOptions signOptions = new SignOptions();
        signOptions.setSignatureLineId(String.valueOf(
            signPersonInfo.getPersonId()));

        document.sign(signOptions, certificateHolder);
    }
}
```

##### توضيح

- **حامل الشهادة:** يمثل الشهادة الرقمية المستخدمة للتوقيع.
- **لافتة:** طريقة توقيع المستند بالخيارات والشهادة المحددة.

## خاتمة

في هذا البرنامج التعليمي، تعلمت كيفية أتمتة إنشاء المستندات وتوقيعها في جافا باستخدام Aspose.Words. باتباع هذه الخطوات، يمكنك تبسيط عمليات إدارة المستندات، وتعزيز الأمان، وضمان سلامة البيانات. لمزيد من الاستكشاف، يمكنك التعمق في ميزات Aspose.Words الأكثر تقدمًا.

**الخطوات التالية:**
- استكشف ميزات Aspose.Words الإضافية مثل دمج البريد أو إنشاء التقارير.
- قم بمراجعة وثائق Aspose للحصول على أدلة مفصلة ومراجع API.
- قم بتجربة تنسيقات المستندات المختلفة التي يدعمها Aspose.Words.

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}