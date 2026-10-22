---
category: general
date: 2026-08-07
description: كيفية ضبط الخيارات في Aspose.Words for Java، حفظ كملف docx وتغيير ترميز
  المستند باستخدام ترميز المصدر ودعم Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to set options
- save as docx
- change document encoding
- set document encoding
- source encoding java
language: ar
lastmod: 2026-08-07
og_description: كيفية ضبط الخيارات في Aspose.Words for Java، ثم حفظ الملف كـ docx
  مع تغيير ترميز المستند. اتبع هذا الدليل لإتقان ترميز المصدر في جافا.
og_image_alt: Screenshot of Java code that sets load options and saves a document
  as docx
og_title: كيفية ضبط الخيارات في Aspose.Words للـ Java – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: how to set options in Aspose.Words for Java, save as docx and change
    document encoding with source encoding java support.
  headline: How to set options in Aspose.Words for Java – complete guide
  type: TechArticle
- description: how to set options in Aspose.Words for Java, save as docx and change
    document encoding with source encoding java support.
  name: How to set options in Aspose.Words for Java – complete guide
  steps:
  - name: Using a different code page
    text: 'If your source files use a different legacy encoding (e.g., Windows‑1252
      or Shift_JIS), replace `"Big5"` with the appropriate charset name:'
  - name: Loading from a stream
    text: 'When you read a file from a network source or a database blob, pass an
      `InputStream` together with `LoadOptions`:'
  - name: Saving to other formats
    text: 'Aspose.Words supports PDF, HTML, RTF, and many more. To **save as docx**
      you already have the code; to save as PDF, change the file extension:'
  - name: Handling password‑protected files
    text: 'If the legacy document is encrypted, provide the password when constructing
      the `Document`:'
  - name: Performance tip
    text: When processing large batches, reuse a single `LoadOptions` instance. Creating
      a new object for each file adds negligible overhead, but reusing reduces garbage‑collection
      pressure.
  type: HowTo
tags:
- Aspose.Words
- Java
- Document processing
title: كيفية ضبط الخيارات في Aspose.Words للـ Java – دليل كامل
url: /ar/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية ضبط الخيارات في Aspose.Words for Java – دليل شامل

إذا كنت بحاجة إلى **كيفية ضبط الخيارات** لتحميل ملف Word قديم في Java، فإن هذا الدليل يوضح الخطوات الدقيقة. ستتعلم كيفية تغيير ترميز المستند، وتكوين ترميز المصدر java، وأخيرًا **حفظ كـ docx** بصيغة ملف حديثة.

يغطي الدليل كل سطر يجب كتابته، يشرح لماذا كل خيار مهم، ويقدم مثالًا جاهزًا للتنفيذ. في النهاية ستتمكن من معالجة أي مستند قديم يستخدم صفحة ترميز غير UTF‑8 مثل Big5.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* مجموعة تطوير جافا (JDK) 8 أو أحدث مثبتة.
* Maven أو Gradle لإدارة الاعتمادات، أو ملف Aspose.Words for Java JAR على مسار الفئة.
* ملف Word قديم (`input.docx`) مرمز بصفحة الترميز Big5.
* صلاحية كتابة إلى دليل الإخراج.

جميع الشيفرات في هذا الدليل تُجمع مع Java 17 و Aspose.Words 23.9.0.

## كيفية ضبط الخيارات لتحميل مستند

الخطوة الأولى هي إنشاء كائن `LoadOptions` وتكوين **ترميز المصدر** الخاص به. طريقة `setEncoding` تخبر Aspose.Words كيف يفسر بايتات الملف الوارد.

```java
import com.aspose.words.*;
import java.nio.charset.Charset;

public class EncodingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create load options and set the source encoding to Big5
        LoadOptions loadOptions = new LoadOptions();
        // source encoding java – Big5 is a traditional Chinese code page
        loadOptions.setEncoding(Charset.forName("Big5"));

        // Step 2: Load the legacy document using the configured options
        Document legacyDoc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Step 3: Save the document in the modern format
        legacyDoc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**لماذا يعمل هذا:**  
`LoadOptions` يؤثر فقط على مرحلة القراءة. بتعيين `Charset.forName("Big5")` تُخبر المكتبة بمعاملة البايتات الخام كحروف Big5. إذا حذفت هذه الدعوة، سيفترض Aspose.Words الترميز UTF‑8، مما يفسد الأحرف الصينية في العديد من الملفات القديمة.

## حفظ كـ docx بعد تغيير الترميز

بمجرد تحميل المستند بالـ **set document encoding** الصحيح، يمكنك تصديره إلى أي صيغة يدعمها Aspose.Words. المثال أعلاه يستخدم `Document.save` مع اسم ملف `.docx`، مما يُطلق عملية **save as docx**.

```java
// Save the document in the modern format (DOCX)
legacyDoc.save("YOUR_DIRECTORY/output.docx");
```

ملف `output.docx` الناتج يحتوي على نص Unicode، لذا يُعرض بشكل صحيح على أي منصة دون الحاجة إلى صفحة ترميز محددة.

## التحقق من التحويل

لتأكيد نجاح التحويل، افتح `output.docx` في Microsoft Word أو LibreOffice أو أي عارض DOCX. يجب أن تظهر الأحرف الصينية سليمة، وسيكون حجم الملف مقاربًا لحجم مستند تم إنشاؤه مباشرةً في محرر حديث.

إذا كنت تفضّل التحقق برمجيًا، يمكنك قراءة الملف المحفوظ مرة أخرى إلى كائن `Document` وفحص النص:

```java
Document verify = new Document("YOUR_DIRECTORY/output.docx");
System.out.println(verify.getText().substring(0, 100)); // prints first 100 characters
```

ستظهر مخرجات وحدة التحكم الأحرف المفككة بشكل صحيح، مما يثبت أن **change document encoding** كان فعالًا.

## الاختلافات الشائعة وحالات الحافة

### استخدام صفحة ترميز مختلفة

إذا كانت ملفات المصدر تستخدم ترميزًا قديمًا مختلفًا (مثل Windows‑1252 أو Shift_JIS)، استبدل `"Big5"` باسم مجموعة الأحرف المناسب:

```java
loadOptions.setEncoding(Charset.forName("Shift_JIS"));
```

### التحميل من تدفق (Stream)

عند قراءة ملف من مصدر شبكة أو كائن BLOB في قاعدة البيانات، مرّر `InputStream` مع `LoadOptions`:

```java
try (InputStream stream = Files.newInputStream(Paths.get("input.docx"))) {
    Document doc = new Document(stream, loadOptions);
    doc.save("output.docx");
}
```

### الحفظ إلى صيغ أخرى

يدعم Aspose.Words PDF و HTML و RTF والعديد غيرها. لـ **save as docx** لديك الشيفرة بالفعل؛ لحفظ كـ PDF، غير امتداد الملف:

```java
legacyDoc.save("output.pdf");
```

تطبيق تكوين `LoadOptions` نفسه ينطبق بغض النظر عن صيغة الهدف.

### التعامل مع الملفات المحمية بكلمة مرور

إذا كان المستند القديم مشفرًا، قدم كلمة المرور عند إنشاء كائن `Document`:

```java
loadOptions.setPassword("mySecret");
Document protectedDoc = new Document("protected.docx", loadOptions);
```

### نصيحة أداء

عند معالجة دفعات كبيرة، أعد استخدام كائن `LoadOptions` واحد. إنشاء كائن جديد لكل ملف يضيف حملاً ضئيلًا، لكن إعادة الاستخدام تقلل من ضغط جمع القمامة.

## مشروع كامل قابل للتنفيذ

فيما يلي ملف `pom.xml` كامل لمشروع Maven يجلب الاعتماد المطلوب من Aspose.Words. انسخ فئة `EncodingDemo.java` إلى `src/main/java` وشغّل `mvn compile exec:java`.

```xml
<!-- pom.xml -->
<project xmlns="http://maven.apache.org/POM/4.0.0" 
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>encoding-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>

    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.9.0</version>
            <classifier>jdk17</classifier>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.codehaus.mojo</groupId>
                <artifactId>exec-maven-plugin</artifactId>
                <version>3.1.0</version>
                <configuration>
                    <mainClass>EncodingDemo</mainClass>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>
```

تشغيل `mvn exec:java` ينتج `output.docx` في الدليل المحدد. يوضح البرنامج **كيفية ضبط الخيارات**، **تغيير ترميز المستند**، و **حفظ كـ docx** في تدفق واحد مختصر.

## نصائح احترافية ومخاطر

* **لا تُهمل مجموعة الأحرف** عندما يكون المصدر يستخدم صفحة ترميز غير UTF‑8؛ الافتراض الافتراضي يؤدي إلى نص مشوش.
* **تحقق من المخرجات** على جهاز يدعم اللغة المستهدفة؛ الفحص البصري هو أسرع طريقة للتحقق من الصحة.
* **تجنب كتابة مسارات الملفات صراحةً** في الكود الإنتاجي. استخدم ملفات إعداد أو متغيرات بيئية لجعل الكود قابلًا للنقل.
* **احرص على تحديث نسخة Aspose.Words**. الإصدارات الجديدة تضيف دعمًا لترميزات إضافية وتحسن الأداء للمستندات الكبيرة.

## الخلاصة

أنت الآن تعرف **كيفية ضبط الخيارات** في Aspose.Words for Java، وتكوين **ترميز المصدر java**، و**تغيير ترميز المستند**، و**حفظ كـ docx** بصيغة Unicode آمنة. المثال الكامل، إعداد Maven، وإرشادات الحالات الخاصة تمنحك أساسًا قويًا لمعالجة ملفات Word القديمة في أي تطبيق جافا.

الخطوات التالية تشمل استكشاف صيغ إخراج أخرى مثل PDF، دمج التحويل في خط أنابيب معالجة دفعات، وتجربة `LoadOptions` مخصصة مثل `Password` أو `LoadFormat`. happy coding!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}