---
category: general
date: 2026-05-30
description: تعلم كيفية الحفظ كنص عادي وتحويل ملف docx إلى txt مع الحفاظ على المعادلات.
  مثال Java خطوة بخطوة مع تصدير معادلات Word.
draft: false
keywords:
- save as plain text
- convert docx to txt
- export word equations
- save word as txt
- convert word with equations
language: ar
og_description: 'دليل حفظ كملف نص عادي: تحويل docx إلى txt، تصدير معادلات Word، وحفظ
  Word كملف txt باستخدام Aspose.Words.'
og_title: حفظ كنص عادي – تصدير معادلات Word في جافا
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Learn how to save as plain text and convert docx to txt while preserving
    equations. Step‑by‑step Java example with export word equations.
  headline: save as plain text – Complete Guide to Export Word Equations
  type: TechArticle
- description: Learn how to save as plain text and convert docx to txt while preserving
    equations. Step‑by‑step Java example with export word equations.
  name: save as plain text – Complete Guide to Export Word Equations
  steps:
  - name: Expected Output
    text: 'Open `MathSample.txt` in any editor and you’ll see something like:'
  - name: What if the target system doesn’t support Unicode?
    text: 'If you need an ASCII‑only fallback, switch the export mode to `OfficeMathExportMode.TEXT`.
      The equations will be rendered as plain text approximations (e.g., “sum(i=1
      to n) i”). Just replace the line:'
  - name: Can I batch‑process a folder of DOCX files?
    text: Absolutely. Wrap the loading and saving logic inside a `File[] files = new
      File("inputFolder").listFiles();` loop. Remember to handle exceptions per file
      to avoid the whole batch stopping on a single corrupt document.
  - name: What about tables or images?
    text: '`TxtSaveOptions` strips non‑text elements by design. If you need a richer
      export (e.g., CSV for tables), consider `CsvSaveOptions` instead. Images are
      omitted because plain text cannot embed binary data.'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Conversion
title: حفظ كملف نص عادي – الدليل الكامل لتصدير معادلات Word
url: /ar/java/document-conversion-and-export/save-as-plain-text-complete-guide-to-export-word-equations/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ كنص عادي – دليل كامل لتحويل DOCX مع المعادلات

هل احتجت يومًا إلى **حفظ كنص عادي** لكن ملف Word الخاص بك يحتوي على صيغ رياضية تتشوه؟ لست وحدك. سواءً كنت تقوم بأرشفة الأوراق البحثية، أو تغذية فهرس بحث، أو تحتاج فقط إلى نسخة خفيفة من عقد، فإن التحدي هو الحفاظ على كائنات OfficeMath قابلة للقراءة بعد التحويل.

الأمر هو أن معظم المحولات الساذجة تُخرج رموز المعادلات كحروف غير قابلة للقراءة. في هذا الدليل سنوضح لك بالضبط كيفية **تحويل docx إلى txt** مع الحفاظ على المعادلات كـ Unicode، أي *تصدير معادلات Word* بتنسيق نظيف وقابل للبحث. في النهاية ستحصل على مقطع Java جاهز للتنفيذ يقوم **بحفظ Word كنص** دون فقدان الرياضيات.

## ما يغطيه هذا الدرس

- المتطلبات الضرورية (Aspose.Words for Java)  
- إعداد **TxtSaveOptions** للتحكم في وضع التصدير  
- برنامج Java كامل وقابل للتنفيذ يقوم **تحويل Word مع المعادلات** بأمان  
- المشكلات الشائعة (مشكلات الخطوط، عدم وجود دعم Unicode) وكيفية تجنبها  
- الخطوات التالية: تعديل فواصل الأسطر، معالجة الجداول، والمعالجة الدفعية  

لا حاجة إلى روابط توثيق خارجية — كل ما تحتاجه موجود هنا.

## المتطلبات المسبقة

- Java 8 أو أحدث مثبت على جهازك  
- Maven أو Gradle لإدارة الاعتمادات (سنستخدم Maven في المثال)  
- ملف DOCX يحتوي على كائن OfficeMath واحد على الأقل (معادلة)  

إذا كان لديك هذه المتطلبات، لنبدأ.

## الخطوة 1: إضافة اعتماد Aspose.Words

أولاً، احصل على مكتبة Aspose.Words for Java. هي منتج تجاري، لكنهم يقدمون ترخيصًا مؤقتًا مجانيًا يعمل للتطوير.

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

> **نصيحة احترافية:** ضع ملف `aspose-words-24.9.jar` في مسار الـ classpath إذا لم تكن تستخدم Maven.

## الخطوة 2: تحميل المستند المصدر

الآن سنقوم **بتحميل المستند المصدر**. فئة `Document` تقرأ أي تنسيق Word، بما في ذلك `.docx` مع المعادلات المدمجة.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

public class DocxToTxtConverter {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the source document
        Document document = new Document("YOUR_DIRECTORY/input.docx");
        // ... we'll add the save logic next
    }
}
```

لاحظ كيف أن اسم المتغير `document` يعكس مفهوم ملف Word، مما يجعل الشيفرة ذاتية الشرح.

## الخطوة 3: تكوين TxtSaveOptions لتصدير المعادلات

جوهر سير عمل **تصدير معادلات Word** يكمن في `TxtSaveOptions`. بشكل افتراضي، يقوم Aspose بإزالة OfficeMath، لكن يمكننا تغيير ذلك باستخدام `OfficeMathExportMode.UNICODE`.

```java
import com.aspose.words.TxtSaveOptions;
import com.aspose.words.OfficeMathExportMode;

// Inside main after loading the document
TxtSaveOptions txtSaveOptions = new TxtSaveOptions();
txtSaveOptions.setOfficeMathExportMode(OfficeMathExportMode.UNICODE);
```

ضبط الوضع إلى `UNICODE` يخبر Aspose بأن يعرض كل معادلة كتمثيل Unicode الخاص بها (مثال: “∑”، “√”). هذا هو ما يجعل ملف النص العادي لا يزال *قابلًا للقراءة* من قبل البشر وقابلًا للبحث بواسطة الأدوات.

## الخطوة 4: حفظ المستند كنص عادي

أخيرًا، نقوم **بحفظ النص العادي** باستخدام الخيارات المكوّنة. هذه هي الخطوة التي يبرز فيها الكلمة المفتاحية الأساسية حقًا.

```java
// Step 4: Save the document as a plain‑text file with the configured options
document.save("YOUR_DIRECTORY/MathSample.txt", txtSaveOptions);
System.out.println("Conversion complete! File saved as plain text.");
```

هذا السطر الواحد يقوم بالعمل الشاق: يكتب ملف `.txt`، يحتفظ بالمعادلات، ويحافظ على فواصل الأسطر. لقد نجحت الآن في **تحويل docx إلى txt** مع الحفاظ على الرياضيات.

## مثال كامل يعمل

بجمع كل ذلك معًا، إليك البرنامج الكامل الذي يمكنك نسخه ولصقه في بيئة التطوير المتكاملة (IDE) الخاصة بك.

```java
import com.aspose.words.Document;
import com.aspose.words.TxtSaveOptions;
import com.aspose.words.OfficeMathExportMode;

public class DocxToTxtConverter {
    public static void main(String[] args) throws Exception {
        // Load the DOCX that contains equations
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Prepare TXT save options: export OfficeMath as Unicode
        TxtSaveOptions txtSaveOptions = new TxtSaveOptions();
        txtSaveOptions.setOfficeMathExportMode(OfficeMathExportMode.UNICODE);

        // Save as plain text
        document.save("YOUR_DIRECTORY/MathSample.txt", txtSaveOptions);

        System.out.println("Conversion complete! File saved as plain text.");
    }
}
```

### النتيجة المتوقعة

افتح `MathSample.txt` في أي محرر وسترى شيئًا مثل:

```
This is a sample paragraph.
∑_{i=1}^{n} i = n(n+1)/2
Another line of text.
```

تظهر المعادلة كرمز جمع Unicode صحيح، مما يثبت أن علم **تصدير معادلات Word** قد عمل.

## أسئلة شائعة وحالات خاصة

### ماذا لو كان النظام المستهدف لا يدعم Unicode؟

إذا كنت تحتاج إلى بديل يدعم ASCII فقط، غيّر وضع التصدير إلى `OfficeMathExportMode.TEXT`. ستُعرض المعادلات كتقريبات نصية عادية (مثال: “sum(i=1 to n) i”). فقط استبدل السطر التالي:

```java
txtSaveOptions.setOfficeMathExportMode(OfficeMathExportMode.TEXT);
```

### هل يمكنني معالجة مجموعة من ملفات DOCX دفعيًا؟

بالطبع. ضع منطق التحميل والحفظ داخل حلقة `File[] files = new File("inputFolder").listFiles();`. تذكر معالجة الاستثناءات لكل ملف لتجنب توقف الدفعة بأكملها عند وجود مستند واحد معطوب.

### ماذا عن الجداول أو الصور؟

`TxtSaveOptions` يزيل العناصر غير النصية حسب التصميم. إذا كنت بحاجة إلى تصدير أكثر غنى (مثال: CSV للجداول)، فكر في استخدام `CsvSaveOptions` بدلاً من ذلك. تُحذف الصور لأن النص العادي لا يمكنه تضمين بيانات ثنائية.

## نصائح احترافية لتحويلات موثوقة

- **احصل على الترخيص مبكرًا**: سيظهر Aspose تحذيرًا إذا شغلت البرنامج بدون ترخيص بعد 30 يومًا. أضف `License license = new License(); license.setLicense("Aspose.Words.lic");` في بداية `main`.  
- **ترميز UTF‑8**: المكتبة تكتب UTF‑8 بشكل افتراضي. إذا كنت تحتاج إلى صفحة ترميز مختلفة، اضبط `txtSaveOptions.setEncoding(Encoding.getEncoding("windows-1252"));`.  
- **نهايات الأسطر**: للحصول على نمط Windows CRLF، استدعِ `txtSaveOptions.setSaveFormat(SaveFormat.TEXT);` (الإعداد الافتراضي يستخدم بالفعل نهايات أسطر خاصة بالنظام).  

## نظرة بصرية

![مخطط سير عمل حفظ كنص عادي](placeholder.png){alt="سير عمل حفظ كنص عادي يوضح التحميل، تكوين الخيارات، وحفظ الخطوات"}

يوضح المخطط خط أنابيب من ثلاث خطوات قمنا ببرمجتها للتو: تحميل → تكوين → حفظ.

## الخلاصة

أنت الآن تعرف كيف **تحفظ كنص عادي** بينما **تحول docx إلى txt** وتحتفظ بكل معادلة دون تغيير. المفتاح كان تكوين `TxtSaveOptions` باستخدام `OfficeMathExportMode.UNICODE`، مما يتيح لك **تصدير معادلات Word** بتنسيق نظيف وقابل للبحث. مع هذه الأساسيات يمكنك بسهولة **حفظ Word كنص**، معالجة المجلدات دفعيًا، أو تعديل وضع التصدير لبيئات مختلفة.

ما الخطوة التالية؟ جرّب إضافة واجهة سطر أوامر بحيث يمكن للمستخدمين توجيه الأداة إلى أي مجلد، أو جرب `CsvSaveOptions` لاستخراج الجداول إلى ملفات CSV. الإمكانيات لـ **تحويل Word مع المعادلات** لا حصر لها، والآن لديك نقطة انطلاق قوية وجديرة بالاستشهاد.

برمجة سعيدة، ولتكن تحويلاتك إلى نص عادي خالية من الفقدان إلى الأبد!

## ما الذي يجب أن تتعلمه بعد ذلك؟

- [حفظ المستند كملف TXT – دليل سريع لتصدير معادلات Word](/words/english/java/document-conversion-and-export/save-document-as-txt-quick-guide-to-exporting-word-math/)
- [تحويل docx إلى markdown – تصدير معادلات الرياضيات إلى LaTeX باستخدام Aspose.Words](/words/english/java/document-conversion-and-export/convert-docx-to-markdown-export-math-equations-to-latex-with/)
- [كيفية تصدير LaTeX من Word: تحويل DOCX إلى Markdown وحفظ كملف PDF](/words/english/java/document-conversion-and-export/how-to-export-latex-from-word-convert-docx-to-markdown-save/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}