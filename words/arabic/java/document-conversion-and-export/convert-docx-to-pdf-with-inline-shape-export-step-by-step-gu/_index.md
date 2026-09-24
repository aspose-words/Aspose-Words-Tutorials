---
category: general
date: 2026-02-18
description: تعلم كيفية تحويل DOCX إلى PDF وحفظ ملف Word كـ PDF مع الحفاظ على الأشكال
  العائمة. يوضح هذا الدليل كيفية تصدير الأشكال بشكل صحيح.
draft: false
keywords:
- convert docx to pdf
- save word as pdf
- how to export shapes
language: ar
og_description: حوّل ملفات DOCX إلى PDF وتعرّف على كيفية تصدير الأشكال. اتبع هذا الدرس
  الكامل لحفظ مستند Word كملف PDF مع وضع العلامات بشكل صحيح.
og_title: تحويل DOCX إلى PDF – دليل تصدير الشكل المضمن
tags:
- Aspose.Words
- Java
- PDF conversion
title: تحويل DOCX إلى PDF مع تصدير الشكل المضمن – دليل خطوة بخطوة
url: /ar/java/document-conversion-and-export/convert-docx-to-pdf-with-inline-shape-export-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تحويل DOCX إلى PDF – دليل تصدير الشكل المضمن

هل احتجت يومًا إلى **تحويل DOCX إلى PDF** لكنك كنت قلقًا من أن الصور أو صناديق النص العائمة قد تختفي أو تتحرك؟ لست وحدك. في العديد من المشاريع—فكر في مولدات التقارير الآلية أو خطوط المعالجة الدفعية—الحفاظ على التخطيط الدقيق لمستند Word أمر لا يمكن التفاوض عليه.  

الأخبار السارة؟ ببضع أسطر من الشيفرة يمكنك **حفظ Word كـ PDF** والتحكم فيما إذا كانت تلك الأشكال العائمة تتحول إلى وسوم مضمنة أو تبقى كعناصر على مستوى الكتلة. أدناه سترى بالضبط **كيفية تصدير الأشكال** بالطريقة التي تريدها، بالإضافة إلى مجموعة من النصائح التي تحميك من الأخطاء الشائعة.

---

## ما ستتعلمه

* تحميل ملف `.docx` من القرص.  
* تكوين `PdfSaveOptions` بحيث يتم تصدير الأشكال العائمة كوسوم مضمنة.  
* كتابة ملف PDF الناتج إلى مجلد من اختيارك.  
* فهم سبب أهمية علم `setExportFloatingShapesAsInlineTag` ومتى قد تقوم بتغييره.  

لا خدمات خارجية، ولا واجهة مستخدم سحرية “انقر‑للتنزيل”—فقط شيفرة Java صافية يمكنك إدراجها في أي مشروع Maven أو Gradle.

---

## المتطلبات المسبقة

| Requirement | Why it matters |
|-------------|----------------|
| **Aspose.Words for Java** (v23.12 or later) | يوفر الفئات `Document` و `PdfSaveOptions` المستخدمة في المثال. |
| **JDK 8+** | المكتبة مُجمَّعة لـ Java 8 وما بعده؛ الإصدارات الأقدم ستطلق `UnsupportedClassVersionError`. |
| **A DOCX file** with at least one floating shape (image, text box, WordArt) | لرؤية تأثير خيار تصدير الشكل، تحتاج إلى مستند يحتوي فعليًا على كائنات عائمة. |

إذا كان لديك هذه العناصر بالفعل، رائع—لنبدأ.

---

## الخطوة 1 – تحميل المستند المصدر  

أولاً نقوم بإنشاء مثيل `Document` يشير إلى ملف `.docx` الذي تريد تحويله. يقرأ المُنشئ الملف إلى الذاكرة، يحلل حزمة OpenXML، ويجهز نموذج الكائن الداخلي.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

// Adjust the path to your environment
String inputPath = "YOUR_DIRECTORY/input.docx";

Document doc = new Document(inputPath);
```

> **نصيحة احترافية:** إذا كنت تعالج العديد من الملفات في حلقة، أعد استخدام كائن `Document` واحد فقط بعد أن تستدعي `doc.close()` (أو تدع جامع القمامة يتعامل معه). هذا يمنع تسرب مقبض الملف على نظام Windows.

---

## الخطوة 2 – تكوين خيارات حفظ PDF لتصدير الأشكال  

هنا يكمن جوهر الدرس. `PdfSaveOptions` يتيح لك تحديد سلوك التحويل. ضبط `setExportFloatingShapesAsInlineTag(true)` يجبر كل شكل عائم على أن يُعامل كعنصر *مضمن* في بنية وسوم PDF. هذا يعني أن قارئات الشاشة ستقرأ الشكل بنفس ترتيب النص المحيط، وهو غالبًا ما يكون مطلوبًا للامتثال لإمكانية الوصول.

```java
import com.aspose.words.PdfSaveOptions;

PdfSaveOptions pdfOptions = new PdfSaveOptions();
// true → inline tagging (shape behaves like a character)
// false → block‑level tagging (shape sits in its own block)
pdfOptions.setExportFloatingShapesAsInlineTag(true);
```

**متى قد تقوم بضبطه إلى `false`؟**  
إذا كان PDF مخصصًا للتوزيع للطباعة فقط وتريد أن تحتفظ الأشكال بموضعها الأصلي دون التأثير على ترتيب القراءة المنطقي، قد تفضّل وسمًا على مستوى الكتلة. القيمة الافتراضية هي `false`، لذا قمنا بتمكين سلوك الإدراج صراحةً لهذا الدرس.

---

## الخطوة 3 – حفظ المستند كملف PDF  

الآن بعد أن أصبحت الخيارات جاهزة، استدعِ `save` مع اسم الملف الهدف وكائن الخيارات. المكتبة تتولى الأعمال الثقيلة: محرك التخطيط، تضمين الخطوط، وتوليد الوسوم.

```java
String outputPath = "YOUR_DIRECTORY/shapes.pdf";
doc.save(outputPath, pdfOptions);
```

بعد انتهاء الاستدعاء، ستجد `shapes.pdf` في المجلد المحدد. افتحه في Adobe Acrobat أو أي عارض PDF يُظهر الوسوم (عادةً تحت **File → Properties → Tags**) وستلاحظ أن الشكل العائم يظهر كوسم مضمن.

---

## مثال كامل قابل للتنفيذ  

بجمع كل ذلك معًا، إليك فئة Java مستقلة يمكنك تجميعها وتشغيلها. تأكد من أن ملف JAR الخاص بـ Aspose.Words موجود في مسار الفئات (classpath).

```java
import com.aspose.words.*;

public class DocxToPdfWithShapes {
    public static void main(String[] args) {
        try {
            // 1️⃣ Load the source DOCX
            String inputPath = "YOUR_DIRECTORY/input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Configure PDF options – export floating shapes as inline tags
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → inline tagging

            // 3️⃣ Save as PDF
            String outputPath = "YOUR_DIRECTORY/shapes.pdf";
            doc.save(outputPath, pdfOptions);

            System.out.println("✅ Conversion complete! PDF saved to: " + outputPath);
        } catch (Exception e) {
            System.err.println("❌ Something went wrong: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**النتيجة المتوقعة:**  
- يحتوي ملف PDF على نفس المحتوى النصي كما في DOCX الأصلي.  
- أي صور أو صناديق نص عائمة الآن مُوسَّمة *مضمنة*، مما يعني أنها تظهر في ترتيب القراءة بدلاً من ككتل منفصلة.  
- إذا فتحت لوحة **Tags** في PDF، سترى عنصر `<Figure>` متداخل داخل `<Paragraph>`—بالضبط ما يضمنه `setExportFloatingShapesAsInlineTag(true)`.

---

## الأسئلة المتكررة وحالات الحافة  

### 1️⃣ هل يعمل هذا مع ملفات DOCX محمية بكلمة مرور؟

نعم—ما عليك سوى توفير كلمة المرور قبل التحميل:

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("mySecret");
Document doc = new Document(inputPath, loadOptions);
```

### 2️⃣ ماذا عن صور SVG أو EMF داخل ملف Word؟

Aspose.Words يقوم تلقائيًا بتحويل الرسومات المتجهة إلى نقطية عند الحفظ إلى PDF. إذا كنت تحتاجها أن تبقى متجهة، اضبط:

```java
pdfOptions.setRasterizeTransformedElements(false);
```

### 3️⃣ كيف أحافظ على الروابط التشعبية أثناء التحويل؟

يتم الاحتفاظ بالروابط بشكل افتراضي. ومع ذلك، إذا عطلت الوسوم (`pdfOptions.setSaveFormat(SaveFormat.PDF)` بدون خيارات)، قد تفقد البنية المنطقية. احتفظ بكائن `PdfSaveOptions` للحفاظ على كل من الوسوم والروابط.

### 4️⃣ هل يمكنني معالجة مجموعة من ملفات DOCX دفعيًا؟

بالتأكيد. ضع منطق `DocxToPdfWithShapes` داخل حلقة تتكرر على `Files.list(Paths.get("YOUR_DIRECTORY"))`. تذكر معالجة الاستثناءات لكل ملف حتى لا يتوقف التنفيذ بسبب مستند واحد سيء.

---

## نصائح من الميدان  

* **احذر الخطوط المفقودة.** إذا كان DOCX المصدر يستخدم خطًا مخصصًا غير مثبت على الخادم، سيستبدل PDF الخط بخيار احتياطي، مما قد يخل بالتخطيط. استخدم `pdfOptions.setFontEmbeddingMode(FontEmbeddingMode.EMBED_ALL)` لفرض التضمين.  
* **اختبار إمكانية الوصول.** بعد التحويل، شغّل **Accessibility Checker** في Acrobat. عادةً ما يحسن وسم الإدراج النتيجة، لكن قد تحتاج إلى إضافة نص بديل للصور يدويًا.  
* **نصيحة أداء:** للمستندات الكبيرة (أكثر من 100 صفحة)، فعّل `pdfOptions.setMemoryOptimization(true)` لتقليل استهلاك الذاكرة.

---

## تأكيد بصري  

فيما يلي لقطة شاشة سريعة للـ PDF المفتوح في Adobe Acrobat، تُظهر الشكل الموسوم كـ *مضمن* مميزًا في لوحة **Tags**.

![مثال تحويل DOCX إلى PDF يظهر وسوم الشكل المضمن](image.png)

---

## الخلاصة  

أنت الآن تعرف **كيفية تحويل DOCX إلى PDF** مع التحكم في طريقة تصدير الكائنات العائمة. من خلال تبديل `setExportFloatingShapesAsInlineTag`، تقرر ما إذا كانت الأشكال تصبح جزءًا من ترتيب القراءة أو تبقى ككتل مستقلة—وهو أمر حاسم لكل من إمكانية الوصول والدقة البصرية.  

من هنا يمكنك:

* **حفظ Word كـ PDF** بالجملة للأرشفة.  
* تجربة خيارات `PdfSaveOptions` الأخرى مثل `setCompliance(PdfCompliance.PDF_A_1B)` للحفظ على المدى الطويل.  
* الغوص أعمق في **كيفية تصدير الأشكال** من خلال استكشاف وثائق Aspose.Words الكاملة أو تجربة علم `setExportDocumentStructure(true)` للحصول على شجر وسوم أغنى.

جرّبه، عدّل الخيارات، ودع ملفات PDF الخاصة بك تبدو تمامًا كما تحتاجها. برمجة سعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}