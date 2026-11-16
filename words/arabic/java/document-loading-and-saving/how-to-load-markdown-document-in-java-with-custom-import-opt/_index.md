---
category: general
date: 2026-11-15
description: تعلم كيفية تحميل مستند ماركداون في جافا باستخدام LoadOptions للحفاظ على
  تنسيق التسطير والتحكم في سلوك الاستيراد.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- load markdown document
- LoadOptions
- import underline formatting
- Document class
- custom import behavior
language: ar
lastmod: 2026-11-15
og_description: حمّل مستند ماركداون في جافا باستخدام LoadOptions. احفظ تنسيق الخط
  السفلي وقم بضبط سلوك الاستيراد بدقة في بضع أسطر من الشيفرة فقط.
og_image_alt: Screenshot of Java code loading a markdown document with custom LoadOptions
og_title: تحميل مستند ماركداون في جافا – دليل خيارات الاستيراد المخصصة
schemas:
- author: GroupDocs
  dateModified: '2026-11-15'
  description: Learn how to load markdown document in Java using LoadOptions to preserve
    underline formatting and control import behavior.
  headline: How to load markdown document in Java with custom import options
  type: TechArticle
- description: Learn how to load markdown document in Java using LoadOptions to preserve
    underline formatting and control import behavior.
  name: How to load markdown document in Java with custom import options
  steps:
  - name: Why you need a `LoadOptions` instance
    text: '* **Predictable results** – Without explicit options the parser may drop
      or change formatting. * **Future‑proofing** – Adding new flags later (e.g.,
      handling tables or code blocks) is as simple as setting another property.'
  - name: When to enable this flag
    text: '* Your markdown contains emphasis that relies on underlining (common in
      technical documentation). * You are generating PDFs or HTML where visual fidelity
      matters.'
  - name: Verifying the load
    text: 'You can quickly confirm that the document loaded correctly:'
  - name: Pro tip
    text: 'Always log the effective `LoadOptions` before loading the file. This makes
      debugging easier when the document doesn’t look as expected:'
  type: HowTo
tags:
- Java
- Markdown
- File I/O
title: كيفية تحميل مستند ماركداون في جافا مع خيارات استيراد مخصصة
url: /ar/java/document-loading-and-saving/how-to-load-markdown-document-in-java-with-custom-import-opt/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تحميل مستند markdown في Java مع خيارات استيراد مخصصة

إذا كنت بحاجة إلى **تحميل مستند markdown** مع الحفاظ على تنسيق محدد، يوضح لك هذا الدليل حلاً مختصرًا وجاهزًا للإنتاج. من خلال تكوين كائن `LoadOptions` يمكنك التحكم في كيفية استيراد تنسيق التسطير والميزات الأخرى من ملف المصدر.

يغطي الدليل كل ما تحتاج معرفته: الاستيرادات المطلوبة، كود خطوة بخطوة، لماذا كل إعداد مهم، والمخاطر الشائعة التي يجب تجنبها. لا تحتاج إلى وثائق خارجية—فقط انسخ، الصق، وشغّل.

## المتطلبات المسبقة

* تثبيت Java 17 أو أحدث.
* المكتبة التي توفر `Document` و `LoadOptions` (مثال: مجموعة أدوات معالجة markdown مثل **GroupDocs.Viewer** أو **Aspose.Words**). عدّل عبارات الاستيراد إذا كنت تستخدم حزمة مختلفة.
* ملف markdown (`input.md`) موجود في دليل يمكنك الإشارة إليه من الكود الخاص بك.

## الخطوة 1: إنشاء كائن `LoadOptions` لتخصيص سلوك الاستيراد

```java
// Import the necessary classes from the SDK
import com.example.sdk.LoadOptions;
import com.example.sdk.Document;

// Step 1: Instantiate LoadOptions for fine‑grained control
LoadOptions loadOptions = new LoadOptions();
```

`LoadOptions` هي الفئة المركزية التي تخبر **Document class** كيفية تفسير ملف المصدر. بإنشاء مثيل تحصل على إمكانية الوصول إلى العشرات من العلامات—إحدى هذه العلامات هي القدرة على استيراد تنسيق التسطير.

### لماذا تحتاج إلى مثيل `LoadOptions`

* **نتائج متوقعة** – بدون خيارات صريحة قد يتجاهل المحلل أو يغيّر التنسيق.
* **التحضير للمستقبل** – إضافة علامات جديدة لاحقًا (مثل معالجة الجداول أو كتل الشيفرة) يكون ببساطة عن طريق ضبط خاصية أخرى.

## الخطوة 2: تمكين استيراد تنسيق التسطير

```java
// Step 2: Turn on underline import
loadOptions.setImportUnderlineFormatting(true);
```

استدعاء `setImportUnderlineFormatting(true)` يُفعِّل علامة **import underline formatting**. عندما تكون هذه العلامة `true`، سيحتفظ أي نص كان مُسطَّرًا في markdown الأصلي بهذا النمط في كائن `Document` الناتج.

### متى يجب تمكين هذه العلامة

* يحتوي markdown الخاص بك على تأكيد يعتمد على التسطير (شائع في الوثائق التقنية).
* تقوم بإنشاء ملفات PDF أو HTML حيث تهم الدقة البصرية.

إذا تخطيت هذه الخطوة، سيظهر النص المُسطَّر كنص عادي، مما قد يربك القراء الذين يعتمدون على الإشارات البصرية.

## الخطوة 3: تحميل ملف markdown باستخدام `LoadOptions` المُكوَّن

```java
// Step 3: Load the markdown document with the custom options
Document markdownDoc = new Document("YOUR_DIRECTORY/input.md", loadOptions);
```

تمرير مثيل `loadOptions` إلى مُنشئ `Document` يُخبر **Document class** بتطبيق قواعد الاستيراد المخصصة أثناء قراءة `input.md`.

### التحقق من التحميل

يمكنك بسرعة التأكد من أن المستند تم تحميله بشكل صحيح:

```java
System.out.println("Document loaded. Page count: " + markdownDoc.getPageCount());
```

إذا كان الملف مفقودًا أو المسار غير صحيح، يُطلق المُنشئ استثناءً توضيحيًا، مما يتيح لك معالجة الخطأ بلطف.

## مثال كامل قابل للتنفيذ

فيما يلي برنامج كامل يمكنك تجميعه وتشغيله كما هو (استبدل اسم الحزمة بالاسم الذي يتطابق مع SDK الخاص بك).

```java
import com.example.sdk.LoadOptions;
import com.example.sdk.Document;

public class LoadMarkdownExample {
    public static void main(String[] args) {
        // 1️⃣ Create LoadOptions to customize import behavior
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Enable importing of underline formatting from the source
        loadOptions.setImportUnderlineFormatting(true);

        // 3️⃣ Load the markdown document using the configured options
        try {
            Document markdownDoc = new Document("YOUR_DIRECTORY/input.md", loadOptions);
            System.out.println("Markdown document loaded successfully.");
            System.out.println("Page count: " + markdownDoc.getPageCount());
        } catch (Exception e) {
            System.err.println("Failed to load markdown document: " + e.getMessage());
        }
    }
}
```

**الناتج المتوقع (بافتراض أن الملف موجود ويحتوي على صفحة واحدة على الأقل من المحتوى):**

```
Markdown document loaded successfully.
Page count: 1
```

إذا تعذر العثور على الملف، ستظهر رسالة خطأ مثل:

```
Failed to load markdown document: File not found: YOUR_DIRECTORY/input.md
```

## الحالات الخاصة ونصائح أفضل الممارسات

| الحالة | ما الذي يجب مراقبته | النهج الموصى به |
|-----------|-------------------|----------------------|
| **مسار الملف يحتوي على مسافات** | `new Document("C:/My Docs/input.md", ...)` قد يتعطل على بعض أنظمة التشغيل. | استخدم `java.nio.file.Paths` لإنشاء المسار بأمان: `Paths.get("C:", "My Docs", "input.md").toString()` |
| **ملفات markdown الكبيرة** | تحميل ملفات كبيرة جدًا قد يستهلك الذاكرة. | فعّل خيارات البث إذا كان SDK يوفرها، أو زد حجم ذاكرة JVM (`-Xmx`). |
| **عدم وجود دعم للتسطير** | بعض إصدارات SDK تتجاهل علامة التسطير. | تأكد من أنك تستخدم نسخة تدعم `setImportUnderlineFormatting`. راجع ملاحظات الإصدار. |
| **الحاجة إلى عدة علامات استيراد** | قد تحتاج أيضًا إلى الحفاظ على الجداول، كتل الشيفرة، إلخ. | ربط setters إضافية على `loadOptions`، مثال: `loadOptions.setImportTables(true);` |

### نصيحة احترافية

دوّن دائمًا الـ `LoadOptions` الفعّال قبل تحميل الملف. هذا يجعل عملية تصحيح الأخطاء أسهل عندما لا يظهر المستند كما هو متوقع:

```java
System.out.println("Import underline formatting: " + loadOptions.isImportUnderlineFormatting());
```

## نظرة بصرية

![Screenshot of Java code loading a markdown document with custom LoadOptions](load-markdown.png)

*Alt text: لقطة شاشة لكود Java يقوم بتحميل مستند markdown مع LoadOptions مخصص.*

## الخلاصة

أنت الآن تعرف كيف **تحميل مستند markdown** في Java مع الحفاظ على تنسيق التسطير وممارسة **سلوك استيراد مخصص** عبر `LoadOptions`. نمط الخطوات الثلاث—إنشاء `LoadOptions`، تمكين العلامات المطلوبة، وتمرير الخيارات إلى مُنشئ `Document`—ينطبق أيضًا على العديد من إعدادات الاستيراد الأخرى.

من هنا يمكنك استكشاف علامات إضافية مثل `setImportTables`، دمج `Document` المحمَّل مع محول PDF، أو تضمين المستند في عارض ويب. نفس النهج يعمل مع أنواع ملفات أخرى يدعمها SDK، مما يجعل هذا النمط أداة متعددة الاستخدامات في مجموعة أدوات Java الخاصة بك.

--- 

*الخطوات التالية:*  

* تعلم كيفية **تصدير المستند المحمَّل إلى PDF** أو HTML.  
* استكشف القائمة الكاملة لخصائص `LoadOptions` لضبط تحليل markdown بدقة.  
* دمج معالجة الأخطاء وتسجيل السجلات لتطبيقات جاهزة للإنتاج.

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [تحميل تسطير markdown في Java – دليل برمجة كامل](/words/english/java/document-loading-and-saving/load-markdown-underline-in-java-complete-programming-guide/)
- [كيفية تحميل Markdown في Java – دليل كامل](/words/english/java/document-loading-and-saving/how-to-load-markdown-in-java-complete-guide/)
- [كيفية قراءة وتحميل ملف Markdown في Java باستخدام Aspose.Words](/words/english/java/document-loading-and-saving/how-to-read-markdown-file-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}