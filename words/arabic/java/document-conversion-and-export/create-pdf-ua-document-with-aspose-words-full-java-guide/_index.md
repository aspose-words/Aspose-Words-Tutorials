---
category: general
date: 2026-04-28
description: إنشاء مستند PDF UA باستخدام Aspose.Words للغة Java. تعلّم كيفية تحميل
  ملفات docx مع الاسترداد، وتصدير المعادلات إلى LaTeX، وحفظ markdown من Word، واسترجاع
  الخطوط المفقودة.
draft: false
keywords:
- create PDF UA document
- retrieve missing fonts
- export equations to LaTeX
- save markdown from Word
- load docx with recovery
language: ar
og_description: إنشاء مستند PDF UA باستخدام Aspose.Words للغة Java. دليل خطوة بخطوة
  يغطي تحميل الاستعادة، تصدير LaTeX، حفظ Markdown، واسترجاع الخطوط المفقودة.
og_title: إنشاء مستند PDF UA – دورة جافا كاملة
tags:
- Aspose.Words
- Java
- PDF/UA
title: إنشاء مستند PDF UA باستخدام Aspose.Words – دليل Java الكامل
url: /ar/java/document-conversion-and-export/create-pdf-ua-document-with-aspose-words-full-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند PDF UA – دليل Java كامل

هل تحتاج إلى **إنشاء مستند PDF UA** من ملف Word مع معالجة المحتوى التالف؟ في هذا الدرس سنرشدك إلى تحميل DOCX مع الاسترداد، وتصدير المعادلات إلى LaTeX، وحفظ Markdown من Word، واسترجاع الخطوط المفقودة — كل ذلك باستخدام Aspose.Words for Java.  

إذا سبق لك أن واجهت ملف .docx معطوب وتساءلت لماذا لا يكون ملف PDF الخاص بك قابلاً للوصول، فأنت في المكان الصحيح. في النهاية ستحصل على ملف PDF/UA 1 متوافق بالكامل، وإصدار Markdown يحتوي على معادلات LaTeX، وقائمة واضحة بأي استبدالات للخطوط حدثت أثناء التحميل.

## ما ستحتاجه

- **Aspose.Words for Java** (أحدث نسخة حتى عام 2026) – أضف تبعية Maven/Gradle أو ملف JAR إلى مسار الـ classpath.  
- Java 17 أو أحدث (تستخدم الـ API الـ streams، لذا يُنصح باستخدام JDK حديث).  
- عينة `input.docx` قد تحتوي على أقسام تالفة، معادلات Office Math، وأشكال عائمة.  

لا توجد مكتبات إضافية مطلوبة؛ كل شيء موجود داخل Aspose.Words.

---

## الخطوة 1 – تحميل DOCX مع وضع الاسترداد  

عند تلف المستند جزئياً، يُطلق القارئ الافتراضي استثناءً. بتمكين وضع الاسترداد تُخبر Aspose.Words بالاستمرار وعرض التحذيرات بدلاً من ذلك.

```java
import com.aspose.words.*;

public class LatestFeaturesDemo {

    public static void main(String[] args) throws Exception {

        // 1️⃣ Load the document with recovery to gracefully handle corruption
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

*لماذا هذا مهم:* يمنع وضع الاسترداد انقطاع خط الأنابيب بالكامل بسبب فقرة واحدة سيئة. كما يملأ `doc.getWarnings()` لتتمكن لاحقاً من **استرجاع الخطوط المفقودة** وغيرها من المشكلات.

---

## الخطوة 2 – تصدير المعادلات إلى LaTeX داخل ملف Markdown  

معظم المطورين يحبون Markdown للتوثيق، لكن معادلات Word المدمجة صعبة النسخ. Aspose.Words يمكنه ترجمتها مباشرة إلى LaTeX.

```java
        // 2️⃣ Configure Markdown export with LaTeX for Office Math
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

        // Store images in a sub‑folder so the Markdown stays tidy
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });

        // Save the Markdown file
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);
```

*نصيحة احترافية:* يضمن الـ callback أن كل صورة مستخرجة تُحفظ تحت `imgs/`. هذا يحاكي طريقة عرض GitHub للـ Markdown – نظيفة وقابلة للنقل.

---

## الخطوة 3 – إنشاء مستند PDF / UA مع وسم صحيح  

الامتثال لـ PDF/UA (Universal Accessibility) إلزامي للعديد من مشاريع القطاع العام. الخيارات التالية تجعل Aspose.Words يضع وسومًا صحيحة للأشكال العائمة وتضبط علامة الامتثال لـ PDF/UA.

```java
        // 3️⃣ Prepare PDF/UA export options
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);          // Enforce PDF/UA‑1
        pdfOptions.setExportFloatingShapesAsInlineTag(true);      // Tag floating shapes

        // Save the accessible PDF
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);
```

*ما ستراه:* عند فتح `output.pdf` في Adobe Acrobat Pro سيظهر “PDF/UA‑1 compliant” ضمن خصائص المستند. جميع الأشكال العائمة (صناديق النص، الصور) ستحصل على وسوم مناسبة لقارئات الشاشة.

---

## الخطوة 4 – تعديل ظل الشكل (تنسيق اختياري)  

على الرغم من أنه غير مطلوب للقدرة على الوصول، قد يكون تعديل الجوانب البصرية مفيدًا للتقارير الداخلية.

```java
        // 4️⃣ Grab the first shape and modify its shadow
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(java.awt.Color.GRAY);
```

*لماذا نهتم؟* إذا كان الـ PDF يُستخدم أيضًا كقطعة تسويقية، فإن الظل الخفيف يمنح التخطيط مظهرًا مصقولًا دون كسر الامتثال.

---

## الخطوة 5 – استرجاع الخطوط المفقودة والتحذيرات الأخرى  

أثناء تحميل الاسترداد، يسجل Aspose.Words أي استبدالات للخطوط. سردها يساعدك على اتخاذ قرار ما إذا كنت ستضمّن الخط الصحيح أو تقبل البديل.

```java
        // 5️⃣ Enumerate font‑substitution warnings
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName() +
                                   " → substituted: " + fsw.getSubstitutedFontName());
            }
        }

        // You can also handle other warning types here (e.g., content loss)
    }
}
```

*الناتج النموذجي* (ستظهر على وحدة التحكم شيئًا مثل):

```
=== Font Substitution Report ===
Missing: Calibri → substituted: Arial
Missing: Times New Roman → substituted: Liberation Serif
```

إذا لاحظت فقدان خطوط حيوية، ففكّر في تثبيتها على الخادم أو تضمينها عبر `PdfSaveOptions.setEmbedFullFonts(true)`.

---

## مثال كامل يعمل  

فيما يلي الفئة الكاملة في Java جاهزة للتنفيذ. الصقها في IDE الخاص بك، عدّل المسارات، ثم اضغط **Run**.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to:
 *  • load a DOCX with recovery,
 *  • export equations to LaTeX inside Markdown,
 *  • create a PDF/UA‑1 compliant PDF,
 *  • modify shape shadows,
 *  • and list any font‑substitution warnings.
 */
public class LatestFeaturesDemo {
    public static void main(String[] args) throws Exception {

        // ---- Step 1: Load DOCX with recovery ----
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // ---- Step 2: Export equations to LaTeX in Markdown ----
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);

        // ---- Step 3: Save as PDF/UA with proper tagging ----
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);

        // ---- Step 4: Optional – adjust the first shape’s shadow ----
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(Color.getGray());

        // ---- Step 5: List any missing‑font warnings ----
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName()
                                   + " → substituted: " + fsw.getSubstitutedFontName());
            }
        }
    }
}
```

**النتائج المتوقعة**

| Output | Description |
|--------|-------------|
| `output.md` | ملف Markdown حيث تظهر كل معادلة Office Math كـ LaTeX (`$…$`). تُحفظ الصور تحت `imgs/`. |
| `output.pdf` | مستند متوافق مع PDF/UA‑1؛ افتحه في Acrobat لتجد “PDF/UA‑1” تحت File → Properties → Standards. |
| Console | قائمة بأي خطوط مفقودة، مثال: “Missing: Calibri → substituted: Arial”. |

---

## الأسئلة المتكررة (FAQ)

**س: هل يعمل هذا مع إصدارات Aspose.Words القديمة؟**  
ج: تم تقديم الـ enums `RecoveryMode`، `OfficeMathExportMode.LATEX`، و `PdfCompliance.PDF_UA_1` في الإصدار 22.8. إذا كنت تستخدم نسخة أقدم، عليك الترقية – ميزات القدرة على الوصول غير متوفرة في الإصدارات السابقة.

**س: ماذا لو أردت تضمين الخطوط الأصلية بدلاً من الاستبدال؟**  
ج: اضبط `pdfOptions.setEmbedFullFonts(true)` وتأكد من أن ملفات الخطوط متاحة على مسار خطوط الـ JVM.

**س: هل يمكنني التصدير إلى صيغ ترميز أخرى (مثل HTML) مع الحفاظ على معادلات LaTeX؟**  
ج: نعم. استخدم `HtmlSaveOptions` واضبط `setOfficeMathExportMode(OfficeMathExportMode.LATEX)` – نفس الـ enum يعمل عبر الصيغ المختلفة.

**س: ملف DOCX يحتوي على العديد من الأشكال العائمة؛ هل سيتم وسمها جميعًا؟**  
ج: مع `setExportFloatingShapesAsInlineTag(true)`، يلف Aspose.Words كل شكل عائم بوسم `<Figure>` للـ PDF/UA، مما يلبي معظم فحوصات قارئات الشاشة.

---

## الخلاصة  

لقد أظهرنا لك الآن كيفية **إنشاء مستند PDF UA** من مصدر Word، مع **تحميل docx باستخدام الاسترداد**، **تصدير المعادلات إلى LaTeX**، **حفظ markdown من Word**، و**استرجاع الخطوط المفقودة**. الشيفرة مكتوبة بالكامل ذاتيًا، تعمل على أي بيئة Java 17+، وتنتج ملفات جاهزة لكل من تدقيق القدرة على الوصول وتطوير التطبيقات.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}