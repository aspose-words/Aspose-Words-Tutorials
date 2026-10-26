---
category: general
date: 2026-10-26
description: تعلم كيفية تحديد الترميز في Java باستخدام LoadOptions. يغطي هذا الدليل
  ترميز الأحرف وطريقة setEncoding وخيارات تحميل المستند.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to specify encoding
- character encoding in Java
- LoadOptions encoding
- setEncoding method
- document loading options
- Aspose.Words for Java
language: ar
lastmod: 2026-10-26
og_description: كيفية تحديد الترميز في جافا باستخدام Aspose.Words. اتبع هذا الدليل
  الكامل لتحميل المستندات باستخدام مجموعة الأحرف الصحيحة.
og_image_alt: Screenshot showing how to specify encoding in Java LoadOptions
og_title: كيفية تحديد الترميز في جافا باستخدام Aspose.Words – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to specify encoding in Java using LoadOptions. This guide
    covers character encoding, setEncoding method, and document loading options.
  headline: How to specify encoding when loading a document with Aspose.Words for
    Java
  type: TechArticle
- description: Learn how to specify encoding in Java using LoadOptions. This guide
    covers character encoding, setEncoding method, and document loading options.
  name: How to specify encoding when loading a document with Aspose.Words for Java
  steps:
  - name: 5.1 Loading from an `InputStream`
    text: 'Sometimes you receive a document as a stream (e.g., from a web service).
      You can still control the encoding by passing the stream together with `LoadOptions`:'
  - name: 5.2 Fallback when the encoding is unknown
    text: If you cannot determine the source file’s charset, you can attempt a detection
      library (such as ICU4J) before setting the encoding. Once you have a guess,
      invoke `setEncoding` with that value. This approach reduces the risk of mis‑decoded
      text.
  - name: 5.3 Dealing with unsupported encodings
    text: Java supports a wide range of code pages, but a few legacy encodings may
      be missing. In that case, consider converting the file to UTF‑8 externally (e.g.,
      using `iconv`) before loading it with Aspose.Words. After conversion, you can
      omit the `setEncoding` call because UTF‑8 is the default for most m
  type: HowTo
tags:
- Java
- Encoding
- Aspose.Words
title: كيفية تحديد الترميز عند تحميل مستند باستخدام Aspose.Words للـ Java
url: /ar/java/document-loading-and-saving/how-to-specify-encoding-when-loading-a-document-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تحديد الترميز عند تحميل مستند باستخدام Aspose.Words للـ Java

إذا كنت بحاجة إلى **كيفية تحديد الترميز** لملف مصدر في Java، فإن هذا الدليل يوضح لك الخطوات الدقيقة. سواء كان المستند يستخدم Big5 أو UTF‑8 أو أي مجموعة أحرف أخرى، يمكنك التحكم في عملية القراءة باستخدام `LoadOptions`. في نهاية الدليل ستفهم لماذا الترميز مهم، وكيفية تطبيق طريقة `setEncoding`، وكيفية التحقق من أن المستند تم تحميله بشكل صحيح.

تحميل مستند بالترميز الصحيح يمنع النص المشوه ويضمن عرض المحتوى متعدد اللغات كما هو مقصود. يغطي هذا الدليل:

* دور **الترميز في Java** عند قراءة الملفات.  
* كيفية تكوين **ترميز LoadOptions** لـ Aspose.Words.  
* كود عملي يمكنك نسخه إلى مشروعك.  
* الأخطاء الشائعة مثل عدم توافق الترميزات وكيفية استكشافها وإصلاحها.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* مجموعة تطوير جافا (JDK) 8 أو أعلى.  
* Maven أو Gradle لإدارة الاعتمادات.  
* Aspose.Words للـ Java 23.10 أو أحدث (الإصدار المستخدم في هذا الدليل).  
* مستند نصي تجريبي (`input.doc`) محفوظ بالترميز المطلوب (مثال: Big5).

لا تحتاج إلى أي مكتبات إضافية؛ المثال يستخدم فقط واجهة برمجة تطبيقات Aspose.Words الأساسية.

## الخطوة 1: إضافة Aspose.Words إلى مشروعك

إذا كنت تستخدم Maven، أضف الاعتماد التالي إلى ملف `pom.xml` الخاص بك:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

لـ Gradle، ضع هذا السطر في ملف `build.gradle` الخاص بك:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

إدراج المكتبة يجعل الفئات `LoadOptions` و `Document` و `Encoding` متاحة للاستخدام.

## الخطوة 2: إنشاء كائن `LoadOptions`

`LoadOptions` يتيح لك تخصيص طريقة فتح Aspose.Words للملف. إنشاء الكائن هو الجزء الأول من **كيفية تحديد الترميز**.

```java
// Step 2: Create load options to customize how the document is opened
LoadOptions loadOptions = new LoadOptions();
```

كائن `LoadOptions` يبدأ بالإعدادات الافتراضية. ستقوم بتعديل خصائصه في الخطوة التالية.

## الخطوة 3: تعيين الترميز المطلوب

طريقة `setEncoding` تحدد **الترميز في Java** الذي يجب على القارئ استخدامه. في هذا المثال نختار صفحة الترميز Big5، وهي شائعة لملفات النصوص الصينية التقليدية.

```java
// Step 3: Specify the character encoding (Big5) for the source file
loadOptions.setEncoding(Encoding.getEncoding("Big5"));
```

*لماذا هذا مهم*: إذا تم تفسير بايتات الملف بصفحة ترميز خاطئة، ستظهر الأحرف كعلامات استفهام أو رموز غير مفهومة. من خلال استدعاء `setEncoding` صراحةً، تخبر Aspose.Words بفك تشفير تدفق البايتات باستخدام جدول تحويل Big5.

يمكنك استبدال `"Big5"` بأي اسم مجموعة أحرف يدعمها Java، مثل `"UTF-8"` أو `"ISO-8859-1"` أو `"Windows-1252"`. تُطلق الطريقة استثناء `UnsupportedEncodingException` إذا كان الاسم غير صالح، لذا قد ترغب في التقاط هذا الاستثناء في الكود الإنتاجي.

## الخطوة 4: تحميل المستند باستخدام الخيارات المكوّنة

الآن بعد أن تم ضبط **ترميز LoadOptions**، مرّر الخيارات إلى مُنشئ `Document`. تكمل هذه الخطوة سير عمل **كيفية تحديد الترميز** الأساسي.

```java
// Step 4: Load the document using the configured options
Document doc = new Document("YOUR_DIRECTORY/input.doc", loadOptions);
```

استبدل `YOUR_DIRECTORY` بالمسار المطلق أو النسبي إلى ملفك. الآن يحتوي كائن `Document` على المحتوى المفكك بالكامل، مع احترام الترميز الذي حددته.

## الخطوة 5: التحقق من أن النص تم تحميله بشكل صحيح

التحقق السريع يساعدك على التأكد من أن الترميز تم تطبيقه كما هو متوقع. يمكنك استخراج نص المستند وطباعته إلى وحدة التحكم:

```java
// Step 5: Output the document text to verify correct decoding
System.out.println(doc.getText());
```

إذا أظهرت وحدة التحكم أحرف صينية مقروءة (أو اللغة التي تتوقعها)، فإن الترميز نجح. إذا ما زلت ترى مخرجات مشوهة، فتأكد من ترميز الملف الأصلي وتحقق من أن اسم مجموعة الأحرف يطابق تمامًا.

## معالجة الحالات الطرفية الشائعة

### 5.1 التحميل من `InputStream`

أحيانًا تستقبل مستندًا كتيار (مثلاً من خدمة ويب). لا يزال بإمكانك التحكم في الترميز بتمرير التيار مع `LoadOptions`:

```java
try (InputStream stream = new FileInputStream("YOUR_DIRECTORY/input.doc")) {
    Document docFromStream = new Document(stream, loadOptions);
    System.out.println(docFromStream.getText());
}
```

تنطبق نفس **خيارات تحميل المستند**، وتظل استدعاءة `setEncoding` كما هي.

### 5.2 الحل الاحتياطي عندما يكون الترميز غير معروف

إذا لم تستطع تحديد مجموعة أحرف الملف المصدر، يمكنك تجربة مكتبة كشف الترميز (مثل ICU4J) قبل ضبط الترميز. بمجرد الحصول على تخمين، استدعِ `setEncoding` بذلك القيمة. يقلل هذا النهج من خطر النص غير المفكك بشكل صحيح.

### 5.3 التعامل مع الترميزات غير المدعومة

يدعم Java مجموعة واسعة من صفحات الترميز، لكن قد تفتقد بعض الترميزات القديمة. في هذه الحالة، فكر في تحويل الملف إلى UTF‑8 خارجيًا (مثلاً باستخدام `iconv`) قبل تحميله بـ Aspose.Words. بعد التحويل، يمكنك حذف استدعاء `setEncoding` لأن UTF‑8 هو الإعداد الافتراضي لمعظم واجهات البرمجة الحديثة.

## نصيحة احترافية: إعادة استخدام `LoadOptions` للمعالجة الدفعية

إذا كنت بحاجة إلى تحميل العديد من المستندات التي تشترك في نفس مجموعة الأحرف، أنشئ كائن `LoadOptions` واحدًا وأعد استخدامه:

```java
LoadOptions sharedOptions = new LoadOptions();
sharedOptions.setEncoding(Encoding.getEncoding("Big5"));

String[] files = {"doc1.doc", "doc2.doc", "doc3.doc"};
for (String file : files) {
    Document d = new Document("YOUR_DIRECTORY/" + file, sharedOptions);
    // Process each document...
}
```

إعادة استخدام الكائن يقلل من عبء إنشاء الكائنات ويضمن ترميزًا متسقًا عبر الدفعة بأكملها.

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يدمج جميع الخطوات، يتضمن الاستيرادات الضرورية، ويتعامل مع الاستثناءات المحتملة.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.Encoding;

import java.io.FileInputStream;
import java.io.InputStream;
import java.io.UnsupportedEncodingException;

public class LoadDocumentWithEncoding {
    public static void main(String[] args) {
        // Path to the input document
        String inputPath = "YOUR_DIRECTORY/input.doc";

        try {
            // Create LoadOptions and set the desired charset (Big5 in this case)
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setEncoding(Encoding.getEncoding("Big5"));

            // Load the document using the configured options
            Document doc = new Document(inputPath, loadOptions);

            // Output the document text to verify correct decoding
            System.out.println("Document text:");
            System.out.println(doc.getText());

            // Optional: load from InputStream using the same options
            try (InputStream stream = new FileInputStream(inputPath)) {
                Document docFromStream = new Document(stream, loadOptions);
                System.out.println("Text from stream:");
                System.out.println(docFromStream.getText());
            }

        } catch (UnsupportedEncodingException e) {
            System.err.println("The specified encoding is not supported: " + e.getMessage());
        } catch (Exception e) {
            System.err.println("Error loading document: " + e.getMessage());
        }
    }
}
```

**الناتج المتوقع** (بافتراض أن الملف المصدر يحتوي على نص صيني مشفر بـ Big5):

```
Document text:
【此處顯示正確的中文內容】...
Text from stream:
【此處顯示正確的中文內容】...
```

إذا عرض الناتج رموزًا غير قابلة للقراءة، راجع اسم مجموعة الأحرف أو تحقق من الترميز الأصلي للملف.

## الأسئلة المتكررة

**هل يعمل هذا مع صيغ مستندات أخرى (DOCX, RTF, HTML)؟**  
نعم. نفس كائن `LoadOptions` ينطبق على أي صيغة يدعمها Aspose.Words. الشرط الوحيد هو أن الملف الأساسي يستخدم مجموعة الأحرف المحددة فعليًا.

**ماذا لو احتجت لتغيير الترميز بعد تحميل المستند؟**  
الترميز يؤثر فقط على مرحلة القراءة. بمجرد وجود كائن `Document`، يصبح تمثيله الداخلي بـ Unicode مستقلاً عن مجموعة الأحرف الأصلية. لتغيير ترميز الإخراج، عدّل `SaveOptions` عند حفظ الملف.

**هل يمكنني استخدام هذا النهج مع مكتبات أخرى (مثل Apache POI)؟**  
Apache POI يتعامل مع كشف مجموعة الأحرف الخاصة به للصيغ الثنائية القديمة، لكن مفهوم تمرير مجموعة أحرف إلى القارئ مشابه. بالنسبة لـ Aspose.Words، فإن `LoadOptions` هو الطريقة الرسمية للتحكم في **كيفية تحديد الترميز**.

## الخلاصة

أنت الآن تعرف **كيفية تحديد الترميز** عند تحميل مستند باستخدام Aspose.Words للـ Java. من خلال إنشاء كائن `LoadOptions`، واستدعاء طريقة `setEncoding`، وتمرير الخيارات إلى مُنشئ `Document`، تضمن أن بايتات الملف تُفسَّر بشكل صحيح. هذه الممارسة تُزيل النص المشوه، تدعم المحتوى متعدد اللغات، وتندمج بسلاسة مع المعالجة الدفعية أو تدفقات البيانات.

استكشف المواضيع ذات الصلة مثل **خيارات تحميل المستند**، **الحفظ بترميزات محددة**، و**معالجة Unicode في Java** لتعميق مهاراتك في معالجة النصوص. جرب أسماء مجموعات أحرف مختلفة، اجمع هذا النهج مع تحويل PDF، أو دمجه في خدمة ويب تقبل تحميلات بترميزات متنوعة.

برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة شاملة مع شرح خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية تحويل نص RTF بترميز UTF-8 في Java باستخدام Aspose.Words](/words/english/java/document-operations/load-rtf-with-utf8-java-asposewords/)
- [كيفية ضبط الخيارات في Aspose.Words للـ Java – دليل كامل](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [استعادة مستند Word DOCX تالف باستخدام Aspose.Words LoadOptions – دليل Java](/words/english/java/document-loading-and-saving/recover-corrupted-word-document-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}