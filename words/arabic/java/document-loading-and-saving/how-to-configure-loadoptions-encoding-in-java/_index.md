---
category: general
date: 2026-10-20
description: تكوين ترميز LoadOptions في Java لقراءة المستندات بشكل صحيح وتغيير ترميز
  المستند إلى UTF-8 باستخدام Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- configure LoadOptions encoding
- change document encoding to utf-8
- Aspose.Words Java encoding
- Java document conversion
- character set handling Java
language: ar
lastmod: 2026-10-20
og_description: قم بتكوين ترميز LoadOptions في Java لضمان معالجة الأحرف بشكل صحيح
  وتعلم كيفية تغيير ترميز المستند إلى UTF-8 باستخدام Aspose.Words.
og_image_alt: Screenshot showing Java code that configures LoadOptions encoding and
  saves a document
og_title: تكوين ترميز LoadOptions في جافا – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Configure LoadOptions encoding in Java to correctly read documents
    and change document encoding to UTF-8 with Aspose.Words.
  headline: How to configure LoadOptions encoding in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Encoding
title: كيفية تكوين ترميز LoadOptions في جافا
url: /ar/java/document-loading-and-saving/how-to-configure-loadoptions-encoding-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تكوين ترميز LoadOptions في Java

إذا كنت بحاجة إلى **تكوين ترميز LoadOptions** في Java، يوضح لك هذا الدليل كيفية تعيين مجموعة الأحرف الصحيحة ثم **تغيير ترميز المستند إلى UTF-8** باستخدام Aspose.Words. يمنع الترميز الصحيح ظهور نص مشوش عند تحميل ملفات تستخدم صفحات ترميز قديمة مثل Big5 أو Shift_JIS أو Windows‑1252.

سوف تتعلم كيفية:

* إنشاء مثيل `LoadOptions` بترميز محدد،
* تحميل مستند المصدر الذي يستخدم ذلك الترميز،
* حفظ المستند بترميز مختلف (UTF‑8) دون فقدان البيانات،
* التحقق من نجاح التحويل.

يفترض هذا الشرح أن لديك بيئة تطوير Java أساسية ورخصة صالحة لـ Aspose.Words for Java. لا توجد أدوات خارجية مطلوبة.

## المتطلبات المسبقة

| المتطلب | لماذا يهم |
|-------------|----------------|
| Java 17 أو أحدث | يوفر ميزات لغة حديثة ودعم طويل الأمد. |
| Aspose.Words for Java (الإصدار 23.9 أو أحدث) | فئة `LoadOptions` موجودة في هذه المكتبة. |
| مستند مصدر مشفر بصفحة ترميز قديمة (مثل Big5) | يوضح الحاجة إلى ترميز مخصص. |
| بيئة تطوير متكاملة أو أداة بناء (Maven/Gradle) | يسهل تجميع وتشغيل المثال. |

أضف تبعية Aspose.Words إلى ملف `pom.xml` إذا كنت تستخدم Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## تكوين ترميز LoadOptions

الخطوة الأولى هي إخبار Aspose.Words بمجموعة الأحرف التي يجب توقعها عند قراءة الملف. يتم ذلك عبر تكوين كائن `LoadOptions`.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import java.nio.charset.Charset;

// Step 1: Create LoadOptions and set the desired encoding (Big5 in this example)
LoadOptions loadOptions = new LoadOptions();
loadOptions.setEncoding(Charset.forName("Big5"));
```

**لماذا هذا مهم:** عندما يتم حفظ مستند بترميز قديم، يفترض المحمل الافتراضي أنه UTF‑8. من خلال تعيين الترميز صراحةً، تتجنب ظهور الأحرف المشوشة (mojibake) وتحافظ على النص الأصلي.

### نصيحة احترافية
إذا لم تكن متأكدًا من الترميز الذي يستخدمه الملف، يمكنك فحص علامة ترتيب البايتات (BOM) أو سؤال موفر المستند. تشمل الترميزات القديمة الشائعة `Big5` و `Shift_JIS` و `Windows-1252`.

## تحميل المستند باستخدام الخيارات المكوَّنة

الآن بعد أن أصبح `LoadOptions` جاهزًا، حمِّل ملف المصدر. يضمن المُنشئ الذي يقبل مسار ملف ومثيل `LoadOptions` تطبيق الترميز المخصص.

```java
// Step 2: Load the document using the configured LoadOptions
String sourcePath = "C:/Docs/big5_doc.docx";
Document doc = new Document(sourcePath, loadOptions);
```

**لماذا هذا مهم:** كائن `Document` يحتوي الآن على النص تمامًا كما هو في الملف الأصلي، لأن المحمل احترم صفحة الترميز Big5 التي قدمتها.

## تغيير ترميز المستند إلى UTF-8

يخزن Aspose.Words النص داخليًا كـ Unicode، لذا فإن عملية حفظ المستند تحدد الترميز الخارجي. لإنتاج ملف UTF‑8، احفظ ببساطة دون تحديد ترميز إضافي—UTF‑8 هو الافتراضي لتنسيقات Office Open XML الحديثة. ومع ذلك، يمكنك فرضه صراحةً للتوضيح.

```java
// Step 3: Save the document using UTF-8 encoding (default for .docx)
String outputPath = "C:/Docs/Converted.docx";
doc.save(outputPath);
```

إذا كنت بحاجة إلى تمثيل نص عادي (مثل `.txt`) بترميز UTF‑8، مرّر كائن `SaveOptions`:

```java
import com.aspose.words.TxtSaveOptions;

// Save as UTF-8 encoded plain text
TxtSaveOptions txtOptions = new TxtSaveOptions();
txtOptions.setEncoding(Charset.forName("UTF-8"));
doc.save("C:/Docs/Converted.txt", txtOptions);
```

**لماذا هذا مهم:** حفظ الملف كـ UTF‑8 يضمن أن أي نظام لاحق—خدمات ويب، قواعد بيانات، أو محررات حديثة—يمكنه قراءة الملف دون خطوات تحويل إضافية.

## التحقق من التحويل

طريقة سريعة لتأكيد نجاح تغيير الترميز هي قراءة الملف المحفوظ مرة أخرى باستخدام قارئ UTF‑8 وطباعة بعض الأحرف.

```java
import java.nio.file.Files;
import java.nio.file.Paths;

byte[] utf8Bytes = Files.readAllBytes(Paths.get(outputPath));
String content = new String(utf8Bytes, Charset.forName("UTF-8"));
System.out.println("First 200 characters of the converted file:");
System.out.println(content.substring(0, Math.min(200, content.length())));
```

إذا كان الإخراج يعرض أحرفًا قابلة للقراءة (دون رموز �)، فإن التحويل قد نجح كما هو متوقع.

## مثال كامل قابل للتنفيذ

فيما يلي برنامج مستقل يجمع جميع الخطوات معًا. استبدل مسارات الملفات بمواقعك الخاصة.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.TxtSaveOptions;
import java.nio.charset.Charset;
import java.nio.file.Files;
import java.nio.file.Paths;

public class EncodingDemo {
    public static void main(String[] args) throws Exception {
        // 1. Configure LoadOptions with the source encoding (Big5)
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setEncoding(Charset.forName("Big5"));

        // 2. Load the legacy‑encoded document
        String sourcePath = "C:/Docs/big5_doc.docx";
        Document doc = new Document(sourcePath, loadOptions);

        // 3. Save as UTF‑8 encoded .docx (default) and .txt for verification
        String docxOutput = "C:/Docs/Converted.docx";
        doc.save(docxOutput); // UTF‑8 by default

        String txtOutput = "C:/Docs/Converted.txt";
        TxtSaveOptions txtOptions = new TxtSaveOptions();
        txtOptions.setEncoding(Charset.forName("UTF-8"));
        doc.save(txtOutput, txtOptions);

        // 4. Verify the .txt file content
        byte[] utf8Bytes = Files.readAllBytes(Paths.get(txtOutput));
        String content = new String(utf8Bytes, Charset.forName("UTF-8"));
        System.out.println("First 200 characters of the UTF‑8 text file:");
        System.out.println(content.substring(0, Math.min(200, content.length())));
    }
}
```

**الناتج المتوقع**

```
First 200 characters of the UTF-8 text file:
[Readable Chinese characters from the original Big5 document...]
```

إذا ظهرت الأحرف بشكل صحيح، فقد نجحت في **تكوين ترميز LoadOptions** و**تغيير ترميز المستند إلى UTF-8**.

## المشكلات الشائعة وكيفية تجنبها

| العَرَض | السبب | الحل |
|---------|-------|-----|
| حروف مشوشة بعد التحميل | `LoadOptions` غير مُعيّن أو اسم مجموعة الأحرف غير صحيح | تأكد من أن `loadOptions.setEncoding(Charset.forName("Big5"))` يتطابق مع صفحة الترميز الخاصة بملف المصدر. |
| `UnsupportedEncodingException` | اسم مجموعة الأحرف مكتوب بشكل خاطئ | استخدم الاسم الدقيق المذكور في `Charset.availableCharsets()`. |
| الملف الناتج لا يزال يظهر أحرفًا مشوشة | تم حفظه كتنسيق قديم (مثل `.rtf`) دون خيارات UTF‑8 | استخدم `TxtSaveOptions` مع `setEncoding("UTF-8")` أو احفظ كملف `.docx`. |
| تباطؤ الأداء في الملفات الكبيرة | إعادة إنشاء `LoadOptions` لكل مستند | أعد استخدام كائن `LoadOptions` واحد عند معالجة العديد من الملفات التي تستخدم نفس ترميز المصدر. |

## الخلاصة

أنت الآن تعرف **كيفية تكوين ترميز LoadOptions** في Java لقراءة المستندات المشفرة بترميزات قديمة و**كيفية تغيير ترميز المستند إلى UTF-8** لاستهلاك آمن في الأنظمة اللاحقة. يعمل هذا النهج مع أي صفحة ترميز يدعمها صف `Charset` في Java، مما يجعله حلًا مرنًا للتطبيقات متعددة اللغات.

بعد ذلك، قد ترغب في استكشاف:

* **تحويل دفعي** – تكرار عبر مجلد من المستندات وتطبيق نفس منطق الترميز.
* **اكتشاف الترميز** – استخدم مكتبات مثل `juniversalchardet` لاكتشاف الترميز المصدر تلقائيًا قبل تكوين `LoadOptions`.
* **الحفاظ على التنسيق** – جرب حفظ المستند كـ PDF أو HTML مع الحفاظ على توافق UTF‑8.

لا تتردد في تعديل الشيفرة لتتناسب مع بنية مشروعك، ودع واجهة Aspose.Words القوية تتولى الجزء الثقيل من معالجة المستندات.

![مقتطف شفرة يوضح تكوين ترميز LoadOptions وحفظ المستند](/images/encoding-demo.png){: .align-center alt="مثال شفرة Java لتكوين ترميز LoadOptions"}

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية تعيين LoadOptions في Aspose.Words لـ Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [كيفية تحويل نص RTF بترميز UTF-8 في Java باستخدام Aspose.Words](/words/english/java/document-operations/load-rtf-with-utf8-java-asposewords/)
- [استعادة مستند DOCX Word تالف باستخدام Aspose.Words LoadOptions – دليل Java](/words/english/java/document-loading-and-saving/recover-corrupted-word-document-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}