---
category: general
date: 2025-12-25
description: كيفية تصدير LaTeX أثناء تحويل DOCX إلى markdown وحفظ المستند كملف PDF
  — دليل خطوة بخطوة مع كود Java.
draft: false
keywords:
- how to export latex
- convert docx to markdown
- save document as pdf
- how to save pdf
- save word as markdown
language: ar
og_description: تعلم كيفية تصدير LaTeX أثناء تحويل DOCX إلى markdown وحفظ المستند
  كملف PDF باستخدام Java. الكود الكامل والنصائح.
og_title: كيفية تصدير LaTeX من Word – تحويل DOCX إلى Markdown وحفظ PDF
tags:
- Aspose.Words
- Java
- Document Conversion
title: 'كيفية تصدير LaTeX من Word: تحويل DOCX إلى Markdown وحفظه كملف PDF'
url: /ar/java/document-conversion-and-export/how-to-export-latex-from-word-convert-docx-to-markdown-save/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيف تصدر LaTeX من Word: تحويل DOCX إلى Markdown وحفظه كملف PDF

هل تساءلت يومًا **كيف تصدر LaTeX** من ملف Word دون فقدان أي من تلك المعادلات المتقنة؟ لست وحدك. في العديد من المشاريع—الأوراق الأكاديمية، المدونات التقنية، أو الوثائق الداخلية—يحتاج الأشخاص إلى استخراج LaTeX من `.docx`، تحويل كل شيء إلى markdown، مع الحفاظ على نسخة PDF مرتبة للتوزيع.  

في هذا الدرس سنستعرض كامل الخطوات: **تحويل docx إلى markdown**، **تصدير LaTeX**، و**حفظ المستند كملف PDF** باستخدام مكتبة Aspose.Words for Java. في النهاية ستحصل على برنامج Java جاهز للتنفيذ يقوم بكل ذلك، بالإضافة إلى مجموعة من النصائح العملية التي يمكنك نسخها ولصقها في قاعدة الشيفرة الخاصة بك.

## ما ستتعلمه

- تحميل مستند Word قد يكون تالفًا في وضع الاسترداد.  
- تصدير معادلات Office Math كـ LaTeX عند الحفظ كـ markdown.  
- حفظ نفس المستند كـ PDF مع معالجة الأشكال العائمة كعلامات داخلية.  
- تخصيص طريقة حفظ الصور أثناء تصدير markdown (تخزين الصور في مجلد مخصص).  
- كيفية **حفظ word كـ markdown** مع الحفاظ على نسخة PDF عالية الجودة.  

**المتطلبات المسبقة**: Java 17 أو أحدث، Maven أو Gradle، ورخصة Aspose.Words for Java (الإصدار التجريبي المجاني يكفي للتجربة). لا توجد مكتبات طرف ثالث أخرى مطلوبة.

---

## الخطوة 1: إعداد المشروع

أولاً، لنضيف ملف jar الخاص بـ Aspose.Words إلى مسار الفئات. إذا كنت تستخدم Maven، أضف هذا الاعتماد إلى ملف `pom.xml` الخاص بك:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Check for the latest version -->
</dependency>
```

أما بالنسبة لـ Gradle، فالأمر هو سطر واحد:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **نصيحة احترافية:** استخدم دائمًا أحدث نسخة مستقرة؛ فهي تتضمن إصلاحات الأخطاء لوضع الاسترداد وتصدير LaTeX.

أنشئ فئة Java جديدة باسم `DocxProcessor.java`. سنستورد كل ما نحتاجه:

```java
import com.aspose.words.*;

import java.io.File;
import java.io.IOException;
```

---

## الخطوة 2: تحميل المستند في وضع الاسترداد

الملفات التالفة تحدث—خاصةً عندما تنتقل عبر البريد الإلكتروني أو مزامنة السحابة. يتيح لك Aspose.Words فتحها في *وضع الاسترداد* حتى لا تفقد كل شيء.

```java
public class DocxProcessor {

    public static void main(String[] args) throws Exception {
        // Adjust these paths to match your environment
        String inputPath = "YOUR_DIRECTORY/corrupted.docx";
        String outputMarkdown = "YOUR_DIRECTORY/output.md";
        String outputPdf = "YOUR_DIRECTORY/output.pdf";
        String customMarkdown = "YOUR_DIRECTORY/output_with_custom_images.md";

        // Step 2: Load with recovery mode
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER); // STRICT, IGNORE are alternatives
        Document doc = new Document(inputPath, loadOptions);

        // Continue with export steps...
```

لماذا نستخدم `RecoveryMode.RECOVER`؟ لأنه يحاول إنقاذ أكبر قدر ممكن من المحتوى، مع الاستمرار في رمي استثناء إذا كان الملف غير قابل للقراءة تمامًا. هذا يوازن بين الأمان والعملية.

---

## الخطوة 3: تصدير LaTeX أثناء تحويل DOCX إلى Markdown

الآن يأتي نجمة العرض: **كيفية تصدير LaTeX** من مستند Word. تحتوي فئة `MarkdownSaveOptions` على خاصية `OfficeMathExportMode` التي تتيح لك اختيار LaTeX أو MathML أو إخراج صورة. سنختار LaTeX.

```java
        // Step 3: Export Office Math as LaTeX during markdown conversion
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        doc.save(outputMarkdown, mdOptions);
```

سيحتوي الملف الناتج `output.md` على قطع LaTeX محاطة بـ `$…$` للمعادلات داخل السطر أو `$$…$$` للمعادلات المدمجة. إذا فتحت الملف في محرر markdown يدعم MathJax أو KaTeX، ستظهر المعادلات بشكل جميل.

> **لماذا LaTeX؟** لأنه اللغة المشتركة للنشر العلمي. التصدير مباشرة إلى LaTeX يتجنب التحويل الفاقد الذي ستحصل عليه إذا اخترت الصور.

---

## الخطوة 4: حفظ المستند كـ PDF (مع الحفاظ على الأشكال العائمة)

غالبًا ما تحتاج إلى نسخة PDF للمراجعين الذين لا يفضلون markdown. يجعل Aspose.Words ذلك سهلًا، ويمكنك التحكم في طريقة معالجة الأشكال العائمة (مثل المخططات).

```java
        // Step 4: Save as PDF, exporting floating shapes as inline tags
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        doc.save(outputPdf, pdfOptions);
```

ضبط `ExportFloatingShapesAsInlineTag` إلى `true` يحول كل شكل عائم إلى علامة `<span>` داخلية في بنية PDF، وهو ما يمكن أن يكون مفيدًا للمعالجة اللاحقة (مثل أدوات إمكانية الوصول للـ PDF).

---

## الخطوة 5: تخصيص معالجة الصور عند حفظ markdown

بشكل افتراضي، يضع Aspose.Words كل صورة في نفس المجلد الخاص بملف markdown، مسميًا إياها تسلسليًا. إذا كنت تفضل مجلد فرعي منظم `images/`، يمكنك ربط ذلك عبر `ResourceSavingCallback`.

```java
        // Step 5: Custom image folder for markdown export
        MarkdownSaveOptions customMdOptions = new MarkdownSaveOptions();
        customMdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) {
                // Place each image under YOUR_DIRECTORY/images/
                String imageFolder = "YOUR_DIRECTORY/images/";
                new File(imageFolder).mkdirs(); // Ensure the folder exists
                args.setFileName(imageFolder + args.getFileName());
                // You could also modify the stream here or skip saving if needed
            }
        });

        doc.save(customMarkdown, customMdOptions);
```

الآن جميع الصور المشار إليها في `output_with_custom_images.md` تُخزن بشكل أنيق تحت `images/`. هذا يجعل التحكم في الإصدارات أنظف ويعكس التخطيط النموذجي الذي تراه على GitHub.

---

## مثال عملي كامل

بجمع كل ما سبق، إليك ملف `DocxProcessor.java` الكامل الذي يمكنك تجميعه وتشغيله:

```java
import com.aspose.words.*;

import java.io.File;

public class DocxProcessor {

    public static void main(String[] args) throws Exception {
        // ==== USER CONFIGURATION ====
        String inputPath        = "YOUR_DIRECTORY/corrupted.docx";
        String outputMarkdown   = "YOUR_DIRECTORY/output.md";
        String outputPdf        = "YOUR_DIRECTORY/output.pdf";
        String customMarkdown   = "YOUR_DIRECTORY/output_with_custom_images.md";

        // ==== 1️⃣ Load document with recovery mode ====
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER);
        Document doc = new Document(inputPath, loadOptions);

        // ==== 2️⃣ Export LaTeX while converting to markdown ====
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        doc.save(outputMarkdown, mdOptions);

        // ==== 3️⃣ Save as PDF, handling floating shapes ====
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        doc.save(outputPdf, pdfOptions);

        // ==== 4️⃣ Custom image folder for markdown export ====
        MarkdownSaveOptions customMdOptions = new MarkdownSaveOptions();
        customMdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) {
                String imageFolder = "YOUR_DIRECTORY/images/";
                new File(imageFolder).mkdirs();
                args.setFileName(imageFolder + args.getFileName());
            }
        });
        doc.save(customMarkdown, customMdOptions);

        System.out.println("All exports completed successfully!");
    }
}
```

### النتيجة المتوقعة

- `output.md` – ملف markdown يحتوي على معادلات LaTeX (`$…$` و `$$…$$`).  
- `output.pdf` – PDF عالي الدقة، مع تحويل الأشكال العائمة إلى علامات داخلية.  
- `output_with_custom_images.md` – نفس ملف markdown لكن جميع الصور مخزنة تحت `images/`.  

افتح markdown في VS Code مع إضافة *Markdown Preview Enhanced*، وسترى المعادلات معروضة تمامًا كما ظهرت في ملف Word الأصلي.

---

## الأسئلة المتكررة (FAQs)

**س: هل يعمل هذا مع ملفات .doc أم فقط .docx؟**  
ج: نعم. يكتشف Aspose.Words الصيغة تلقائيًا. فقط غير امتداد الملف في `inputPath`.

**س: ماذا لو أردت MathML بدلًا من LaTeX؟**  
ج: استبدل `OfficeMathExportMode.LATEX` بـ `OfficeMathExportMode.MATHML`. باقي الخطوات تبقى كما هي.

**س: هل يمكنني تخطي خطوة PDF؟**  
ج: بالتأكيد. فقط علق كتلة PDF. الشيفرة معيارية، لذا يمكنك **حفظ المستند كـ PDF** فقط عندما تحتاجه.

**س: كيف أتعامل مع المستندات المحمية بكلمة مرور؟**  
ج: استخدم `LoadOptions.setPassword("yourPassword")` قبل إنشاء كائن `Document`.

**س: هل هناك طريقة لتضمين LaTeX مباشرةً داخل PDF؟**  
ج: ليس بشكل أصلي؛ ملفات PDF لا تفهم LaTeX. سيتوجب عليك تحويل المعادلات إلى صور أولًا، مما يُفقد هدف تصدير LaTeX النظيف.

---

## الحالات الخاصة والنصائح

- **الصور التالفة**: إذا تعذّر قراءة صورة، سيُدرج Aspose.Words عنصرًا نائبًا. يمكنك اكتشاف ذلك في `ResourceSavingCallback` عبر فحص `args.getStream().available()`.
- **المستندات الكبيرة**: للملفات التي تتجاوز 100 MB، فكر في بث مخرجات PDF (`doc.save(outputPdf, pdfOptions)` حيث `outputPdf` هو `FileOutputStream`) لتقليل الضغط على الذاكرة.
- **الأداء**: تمكين `RecoveryMode.IGNORE` يسرّع التحميل لكنه قد يحذف محتوى. استخدم `RECOVER` لتوازن بين السرعة والسلامة.
- **تطبيق الترخيص**: في وضع التجربة، يُضاف علامة مائية إلى كل مستند محفوظ. سجّل ترخيصًا لإزالتها—فقط نفّذ `License license = new License(); license.setLicense("Aspose.Words.lic");` قبل أي عملية معالجة.

---

## الخلاصة

ها أنت ذا—**كيفية تصدير LaTeX** من ملف Word، **تحويل docx إلى markdown**، و**حفظ المستند كـ PDF** في برنامج Java واحد مرتب. تناولنا التحميل في وضع الاسترداد، تصدير LaTeX، إنشاء PDF مع معالجة الأشكال العائمة، ومجلدات الصور المخصصة للـ markdown.  

من هنا يمكنك تجربة صيغ تصدير أخرى (HTML، EPUB)، دمج هذه المنطق في خدمة ويب، أو أتمتة معالجة دفعات من عشرات الملفات. جميع اللبنات الأساسية جاهزة، وواجهة Aspose.Words تجعل توسيع سير العمل أمرًا سهلًا.

إذا وجدت هذا الدليل مفيدًا، أعطه نجمة على GitHub، شاركه مع زملائك، أو اترك تعليقًا أدناه مع تعديلاتك الخاصة. برمجة سعيدة، ولتظهر معادلات LaTeX دائمًا بلا أخطاء! 

![Diagram showing the conversion pipeline from DOCX → Markdown (with LaTeX) → PDF, alt text: "كيفية تصدير LaTeX أثناء تحويل DOCX إلى markdown وحفظه كـ PDF"] 

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}