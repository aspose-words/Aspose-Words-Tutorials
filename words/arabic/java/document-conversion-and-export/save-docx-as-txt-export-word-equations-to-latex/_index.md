---
category: general
date: 2026-05-04
description: احفظ ملف docx كملف txt بسرعة باستخدام Aspose.Words للغة Java. تعلّم كيفية
  تحويل Word إلى txt، والحفاظ على فواصل الأسطر، وتصدير المعادلات إلى LaTeX.
draft: false
keywords:
- save docx as txt
- convert word to txt
- how to preserve line breaks
- convert docx to plain text
- export word equations latex
language: ar
og_description: احفظ ملف docx كملف txt باستخدام Aspose.Words للغة Java. يوضح هذا الدليل
  كيفية تحويل docx إلى نص عادي، مع الحفاظ على فواصل الأسطر، وتصدير المعادلات بصيغة LaTeX.
og_title: حفظ ملف docx كملف txt – تصدير معادلات Word إلى LaTeX
tags:
- aspose-words
- java
- txt-export
title: احفظ ملف docx كملف txt – تصدير معادلات Word إلى LaTeX
url: /ar/java/document-conversion-and-export/save-docx-as-txt-export-word-equations-to-latex/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ docx كملف txt – تصدير معادلات Word إلى LaTeX

هل تساءلت يومًا كيف **تحفظ docx كملف txt** دون فقدان الرياضيات التي كتبتها بعناية في Word؟ لست وحدك. يحتاج العديد من المطورين إلى تفريغ ملف Word إلى نص عادي مع الحفاظ على قابلية قراءة المعادلات، والحيلة المعتادة للنسخ واللصق تشوه الرموز.  

في هذا الدرس سنستعرض حلًا كاملًا وجاهزًا للتنفيذ **يحوّل Word إلى txt**، ويحافظ على كل فاصل سطر بالضبط كما هو، ويُخرج LaTeX لأي كائنات OfficeMath. في النهاية ستحصل على برنامج Java واحد يقوم بكل ذلك—بدون الحاجة لتدخل يدوي.

## ما ستتعلمه

- كيف **تحفظ docx كملف txt** باستخدام Aspose.Words for Java.  
- الطريقة الصحيحة **لتحويل word إلى txt** مع الحفاظ على فواصل الأسطر (`how to preserve line breaks`).  
- كيف **تصدّر معادلات word إلى latex** بحيث يحتوي ملف `.txt` الناتج على ترميز LaTeX نظيف.  
- نصائح للتعامل مع الحالات الخاصة مثل الفقرات الفارغة أو الصور المدمجة.  
- عينة كود كاملة قابلة للتنفيذ يمكنك إضافتها إلى مشروعك اليوم.

### المتطلبات المسبقة

- Java 8 أو أعلى مثبت على جهازك.  
- نسخة حديثة من **Aspose.Words for Java** (تم اختبار الكود مع 23.12).  
- ملف `.docx` يحتوي على معادلة واحدة على الأقل (OfficeMath).  
- إلمام أساسي بـ Maven أو Gradle لإضافة تبعية Aspose.

> **نصيحة احترافية:** إذا لم يكن لديك ترخيص بعد، تقدم Aspose ترخيصًا مؤقتًا مجانيًا يزيل علامة التقييم المائية.

---

## الخطوة 1: إعداد المشروع وإضافة Aspose.Words

أولاً، أنشئ مشروع Maven (أو Gradle) جديد. أضف تبعية Aspose.Words إلى ملف `pom.xml` الخاص بك:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

إذا كنت تفضّل Gradle، فالمكافئ هو:

```groovy
implementation 'com.aspose:aspose-words:23.12'
```

بمجرد أن تكون المكتبة على مسار الفئة (classpath)، ستكون جاهزًا **لتحويل docx إلى نص عادي**.

## الخطوة 2: تحميل مستند Word

سنبدأ بتحميل ملف `.docx` المصدر. هذه هي النقطة التي ينسى فيها الكثير من المبتدئين معالجة `IOException`، لذا نغلف كل شيء في try‑catch أو نكتفي بـ `throws Exception` للبساطة.

```java
import com.aspose.words.*;

public class TxtMathExport {
    public static void main(String[] args) throws Exception {
        // Load the Word document containing equations
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

> **لماذا هذا مهم:** `Document` ي抽象 (يُجَسِّد) بنية الملف بالكامل، مما يمنحنا الوصول إلى الفقرات، والـ runs، وعُقَد OfficeMath المخفية التي تحمل المعادلات.

## الخطوة 3: تكوين خيارات حفظ TXT

الآن يأتي جوهر الدرس—إخبار Aspose بالضبط كيف نريد أن يبدو ملف النص. هناك إعدادان حاسمان:

1. **OfficeMathExportMode.LATEX** – يحوّل كل معادلة إلى صيغة LaTeX.  
2. **PreserveLineBreaks = true** – يحافظ على فواصل الأسطر تمامًا كما هي في ملف Word الأصلي (`how to preserve line breaks`).

```java
        // Create TXT save options and set the math export mode to LaTeX
        TxtSaveOptions txtSaveOptions = new TxtSaveOptions();
        txtSaveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

        // Preserve line breaks exactly as they appear in the source
        txtSaveOptions.setPreserveLineBreaks(true);
```

> **شرح:** بشكل افتراضي، كان Aspose سيُسطّح المستند، مُزيلًا معظم التنسيقات. ضبط `PreserveLineBreaks` يضمن أن كل عودة صلبة في Word تتحول إلى سطر جديد في الناتج، وهو أمر أساسي عندما تُدخل النص لاحقًا في سكريبت أو نظام تحكم بالإصدار.

## الخطوة 4: حفظ المستند كملف نص عادي

أخيرًا، نكتب المحتوى المُحوَّل إلى القرص. طريقة `save` تأخذ مسار الهدف والخيارات التي بنيناها للتو.

```java
        // Save the document as a plain‑text file with the configured options
        document.save("YOUR_DIRECTORY/output.txt", txtSaveOptions);
    }
}
```

هذا كل شيء—شغّل البرنامج وسترى `output.txt` بجوار ملف المصدر. افتحه بأي محرر وستلاحظ:

- الفقرات العادية تظهر كما كانت في Word.  
- كل معادلة أصبحت الآن سلسلة LaTeX، مثلًا `\int_{a}^{b} f(x)\,dx`.  
- لا توجد أسطر فارغة إضافية، بفضل `setPreserveLineBreaks(true)`.

![مثال حفظ docx كملف txt](image.png "حفظ docx كملف txt – عينة مخرجات تُظهر معادلات LaTeX")

### عينة النتيجة المتوقعة

إذا كان `input.docx` يحتوي على المعادلة *∑_{i=1}^{n} i = n(n+1)/2*، فإن السطر الناتج في `output.txt` سيظهر هكذا:

```
\sum_{i=1}^{n} i = \frac{n\,(n+1)}{2}
```

كل ما تبقى يبقى نصًا عاديًا، مما يجعل الملف مثاليًا للمعالجة اللاحقة (مثلًا، إمداده إلى مولِّد موقع ثابت أو مترجم LaTeX).

---

## أسئلة شائعة وحالات حافة

### ماذا لو لم يحتوي المستند على معادلات؟

إعداد `OfficeMathExportMode.LATEX` لا يفعل شيئًا عندما لا توجد عقد OfficeMath، لذا يكون الناتج نصًا عاديًا فقط. لا حاجة لمعالجة إضافية.

### كيف تتعامل مع مستندات كبيرة (مئات الصفحات)؟

Aspose يبث الإخراج، لذا يبقى استهلاك الذاكرة منخفضًا. ومع ذلك، قد ترغب في زيادة حجم heap الخاص بـ JVM إذا كنت تعالج ملفات ضخمة (`-Xmx2g` نقطة بداية آمنة).

### هل يمكنني التصدير إلى صيغ أخرى مثل HTML مع الحفاظ على المعادلات؟

بالطبع. استبدل `TxtSaveOptions` بـ `HtmlSaveOptions` واضبط `setOfficeMathExportMode(OfficeMathExportMode.LATEX)`—ستُدمج نفس ترميزات LaTeX داخل وسوم `<span>`.

### هل يعمل هذا على macOS/Linux؟

نعم. Aspose.Words for Java مستقل عن المنصة؛ فقط تأكد من أن متغيّر البيئة `JAVA_HOME` يشير إلى JDK متوافق.

## مثال كامل يعمل (جاهز للنسخ واللصق)

فيما يلي البرنامج الكامل، جاهز للترجمة والتنفيذ. استبدل `YOUR_DIRECTORY` بالمجلد الفعلي الذي يحتوي على `input.docx`.

```java
import com.aspose.words.*;

public class TxtMathExport {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the Word document containing equations
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Create TXT save options and set the math export mode to LaTeX
        TxtSaveOptions txtSaveOptions = new TxtSaveOptions();
        txtSaveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

        // Step 3: Preserve line breaks exactly as they appear in the source
        txtSaveOptions.setPreserveLineBreaks(true);

        // Step 4: Save the document as a plain‑text file with the configured options
        document.save("YOUR_DIRECTORY/output.txt", txtSaveOptions);
    }
}
```

شغّله باستخدام:

```bash
mvn compile exec:java -Dexec.mainClass=TxtMathExport
```

أو، إذا كنت تستخدم Gradle:

```bash
./gradlew run --args='YOUR_DIRECTORY/input.docx'
```

## ملخص وخطوات قادمة

لقد أظهرنا لك **كيفية حفظ docx كملف txt** مع الحفاظ على كل فاصل سطر وتحويل معادلات Word إلى LaTeX نظيف. النهج قابل للتوسع، يحترم حدود الذاكرة، ويعمل على أي نظام تشغيل يدعم Java.

تبحث عن المزيد؟

- **تحويل docx إلى نص عادي** للغات أخرى (مثل Python) – نمط الخيار نفسه ينطبق.  
- **معالجة دفعة** لمجلد كامل من ملفات `.docx` عبر حلقة على كائنات `File[]`.  
- **دمج** الناتج في مولِّد موقع ثابت مثل Hugo، حيث يمكن عرض مقتطفات LaTeX باستخدام MathJax.

لا تتردد في تجربة `TxtSaveOptions`—يمكنك تبديل `setEncoding(Encoding.UTF_8)` إذا كنت تحتاج إلى مجموعة أحرف محددة، أو تمكين `setExportHeadersFooters(true)` للحفاظ على نص الرأس/التذييل.

إذا واجهت أي مشكلة، اترك تعليقًا أدناه أو راجع الوثائق الرسمية لـ Aspose—فهي شاملة بشكل مفاجئ وتضم عشرات السيناريوهات الواقعية.

برمجة سعيدة، واستمتع ببساطة تحويل ملفات Word الغنية إلى نص خفيف الوزن جاهز للـ LaTeX!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}