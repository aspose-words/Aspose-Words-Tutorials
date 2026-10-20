---
category: general
date: 2026-05-04
description: كيفية ضبط الدقة لتصدير Markdown من Word. تعلم دقة صور Markdown، وكيفية
  تصدير المعادلات، وحفظ Word كـ Markdown باستخدام Java.
draft: false
keywords:
- how to set resolution
- markdown image resolution
- how to use markdown
- how to export equations
- save word as markdown
language: ar
og_description: كيفية تعيين الدقة لتصدير Markdown من Word. يوضح هذا الدليل دقة صور
  Markdown، وتصدير المعادلات، وحفظ Word كـ Markdown.
og_title: كيفية ضبط الدقة عند حفظ ملف Word كـ Markdown
tags:
- Aspose.Words
- Java
- Markdown
- Document Export
title: كيفية تعيين الدقة عند حفظ ملف Word كـ Markdown
url: /ar/java/document-conversion-and-export/how-to-set-resolution-when-saving-word-as-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية ضبط الدقة عند حفظ Word كملف Markdown

هل تساءلت يومًا **كيف يتم ضبط الدقة** للصور التي تظهر في ملف Markdown تم إنشاؤه من مستند Word؟ لست وحدك. يواجه العديد من المطورين مشكلة عندما تبدو صور الرياضيات المرسومة بشكل نقطي غير واضحة، خاصةً على الشاشات ذات الـ DPI العالي.  

في هذا الدرس سنستعرض الخطوات الدقيقة للتحكم في *دقة صور Markdown* مع إظهار **كيفية تصدير المعادلات** كـ LaTeX، وأخيرًا **كيفية حفظ Word كملف markdown** باستخدام Aspose.Words for Java. في النهاية ستحصل على ملف Markdown واضح وجاهز للإنتاج يعرض المعادلات بدقة عالية والصور بجودة تناسب احتياجاتك.

## المتطلبات المسبقة

- Java 17 (أو أي JDK حديث)  
- Aspose.Words for Java 23.6 أو أحدث – يمكنك الحصول عليه من Maven Central  
- مستند Word (`.docx`) يحتوي على كائنات OfficeMath (معادلات) وربما صور نقطية  
- إلمام أساسي بـ Maven/Gradle وبيئة تطوير (IntelliJ IDEA، Eclipse، VS Code، إلخ.)

لا توجد مكتبات إضافية مطلوبة؛ كل شيء آخر يتم التعامل معه بواسطة Aspose.Words.

---

## كيفية ضبط الدقة لتصدير Markdown

> **نصيحة احترافية:** الدقة التي تختارها تؤثر مباشرةً على حجم الملف للصور المولدة. قيمة **300 dpi** تُعد توازنًا جيدًا لمعظم عارضات Markdown على الويب.

```java
// Step 1: Load the source Word document containing equations
Document doc = new Document("YOUR_DIRECTORY/Math.docx");

// Step 2: Create Markdown save options to control the export behavior
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();

// Step 3: Export OfficeMath objects as LaTeX expressions
saveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

// Step 4 (optional): Set image resolution for any rasterized Math images
saveOptions.setImageResolution(300);   // <-- this is where we set the resolution

// Step 5: Save the document as a Markdown file using the configured options
doc.save("YOUR_DIRECTORY/MathExport.md", saveOptions);
```

استدعاء `setImageResolution(int dpi)` هو جوهر **كيفية ضبط الدقة**. يوجه Aspose.Words إلى تحويل أي صور احتياطية (مثلًا عندما لا يمكن تمثيل معادلة بصيغة LaTeX صافية) إلى نقاط‑في‑البوصة المحددة. إذا حذفت هذا السطر، ستعود المكتبة إلى قيمتها الافتراضية 220 dpi، والتي قد تبدو غير واضحة على شاشات Retina.

### لماذا نستخدم LaTeX للمعادلات؟

عند تصدير المعادلات كـ LaTeX (`OfficeMathExportMode.LATEX`)، يحتوي ملف Markdown الناتج على كود LaTeX خام محاط بـ `$…$` أو `$$…$$`. معظم عارضات Markdown الحديثة (GitHub، GitLab، MkDocs مع MathJax) ستعرض هذه كرسومات متجهة واضحة وقابلة للتكبير—لا توجد مشاكل دقة هنا. إعداد الدقة يهم فقط **دقة صور Markdown** لأي صور نقطية احتياطية، مثل المخططات أو الصور المدمجة التي لا يدعمها Markdown أصلاً.

---

## كيفية استخدام دقة صور Markdown بفعالية

إذا كنت بحاجة إلى تضمين صور عادية (مثل لقطات الشاشة) داخل ملف Word، فستُحوَّل هذه الصور إلى PNG بواسطة Aspose.Words. نفس طريقة `setImageResolution` تُطبق، مما يضمن أن ملفات PNG ستحمل DPI الذي تحدده. إليك قائمة سريعة:

1. **اختر DPI يتناسب مع المنصة المستهدفة** – 72 dpi للويب القديم، 150 dpi للشاشات العادية، 300 dpi للملفات PDF ذات الجودة الطباعية.  
2. **اختبر النتيجة** – افتح ملف `.md` المُولَّد في العارض المفضل لديك وقم بالتكبير للتحقق من الوضوح.  
3. **ضع في اعتبارك حجم الملف** – DPI أعلى ينتج PNG أكبر؛ إذا كانت السرعة أو النطاق الترددي مشكلة، جرّب 200 dpi وقارن النتائج.

---

## كيفية تصدير المعادلات كـ LaTeX

السطر `saveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);` يوجه Aspose.Words إلى تحويل كل كائن OfficeMath إلى LaTeX. هذا هو النهج الموصى به لأن:

- **قابلية التوسع** – LaTeX يُظهر بأي حجم دون فقدان الجودة.  
- **قابلية التحرير** – يمكنك تعديل كود LaTeX مباشرة في ملف Markdown لاحقًا.  
- **التوافق** – معظم مولّدات المواقع الثابتة وأدوات التوثيق تدعم عرض LaTeX بالفعل.

إذا احتجت إلى الرجوع إلى الصور الاحتياطية، ما عليك سوى تغيير الإعداد إلى `OfficeMathExportMode.IMAGE`. في هذه الحالة تصبح الدقة التي تحددها أكثر أهمية.

---

## حفظ Word كملف Markdown – مثال كامل من البداية إلى النهاية

فيما يلي مقتطف مشروع Maven كامل يمكن تشغيله يوضح سير العمل بالكامل، من تعريف الاعتماديات إلى التنفيذ.

```xml
<!-- pom.xml -->
<project xmlns="http://maven.apache.org/POM/4.0.0" ...>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>markdown-export</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.6</version>
        </dependency>
    </dependencies>
</project>
```

```java
// src/main/java/com/example/MarkdownMathExport.java
package com.example;

import com.aspose.words.*;

public class MarkdownMathExport {
    public static void main(String[] args) throws Exception {
        // Load the source Word document containing equations and images
        Document doc = new Document("src/main/resources/Math.docx");

        // Configure Markdown export options
        MarkdownSaveOptions options = new MarkdownSaveOptions();
        options.setOfficeMathExportMode(OfficeMathExportMode.LATEX); // export equations as LaTeX
        options.setImageResolution(300); // set resolution for rasterized images

        // Save as Markdown
        doc.save("output/MathExport.md", options);

        System.out.println("✅ Markdown export complete! Check output/MathExport.md");
    }
}
```

**النتيجة المتوقعة:** سيحتوي `MathExport.md` على كتل LaTeX لكل معادلة، وأي صور مدمجة ستظهر كروابط PNG بدقة 300 DPI. افتح الملف في عارض Markdown يدعم MathJax (مثل VS Code مع إضافة Markdown Preview Enhanced) وسترى معادلات وصور حادة تمامًا.

---

## الأسئلة الشائعة والحالات الخاصة

### ماذا لو احتجت DPI مختلف لصورة واحدة فقط؟

Aspose.Words يطبق DPI عالميًا عبر `setImageResolution`. للتعامل مع DPI مختلف لكل صورة، سيتعين عليك معالجة ملف Markdown بعد إنشائه: استبدل ملفات PNG بإصدارات ذات دقة أعلى وعدّل روابط الصور يدويًا. ليس مثالياً، لكنه ممكن لحالات قليلة خاصة.

### هل يعمل هذا على Linux/macOS؟

بالطبع. المكتبة مكتوبة بجافا بحتة، لذا يمكن تشغيل الكود في أي بيئة تدعم JDK. فقط تأكد من أن مسارات الملفات تستخدم الشرط المائل `/` أو `Paths.get(...)` للتعامل المستقل عن النظام.

### ماذا عن إخراج SVG؟

إذا فضلت صورًا متجهة للمخططات، يمكنك ضبط `saveOptions.setExportImagesAsSvg(true);`. ملفات SVG تتجاهل DPI، لذا تختفي مشكلة **دقة صور Markdown**. مع ذلك، ليست كل عارضات Markdown تدعم SVG بشكل جيد، لذا اختبر المنصة المستهدفة أولًا.

### هل يمكنني تضمين ملف Markdown الناتج في مولّد موقع ثابت؟

نعم. الناتج هو ملف `.md` عادي بصيغة Markdown القياسية مع محددات LaTeX. معظم المولّدات (Jekyll، Hugo، MkDocs) ستقبل ذلك مباشرة. فقط تأكد من تفعيل MathJax أو KaTeX في إعدادات الموقع.

---

## الخلاصة

غطّينا **كيفية ضبط الدقة** للصور عند **حفظ Word كملف markdown**، وتعمقنا في تفاصيل **دقة صور Markdown**، وأظهرنا **كيفية تصدير المعادلات** كـ LaTeX، وعرضنا التنفيذ الكامل بلغة Java. من خلال تعديل `setImageResolution` واختيار `OfficeMathExportMode` المناسب، ستحصل على تحكم دقيق في جودة العرض وحجم الملف.

هل أنت مستعد للخطوة التالية؟ جرّب دمج هذا النهج مع Aspose.PDF لتحويل نفس مصدر Word مباشرة إلى PDF، أو جرّب `setExportImagesAsSvg(true)` للحصول على رسومات متجهة. التقنيات التي تعلمتها هنا هي أساس لأي خط أنابيب توثيق آلي.

إذا وجدت هذا الدليل مفيدًا، أعطه نجمة على GitHub، شاركه مع زملائك، أو اترك تعليقًا أدناه بأفكارك ونصائحك. Happy coding!  

![مثال على ضبط الدقة](resolution.png "كيفية ضبط الدقة عند حفظ Word كملف Markdown")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}