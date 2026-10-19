---
category: general
date: 2026-02-10
description: تضمين الصور بصيغة base64 أثناء تحويل DOCX إلى Markdown باستخدام Java
  – تصدير Markdown مع معادلات LaTeX بسهولة.
draft: false
keywords:
- embed images as base64
- convert docx to markdown
- export markdown with latex
- convert word equations latex
- java convert docx markdown
language: ar
og_description: دمج الصور بصيغة base64 أثناء تحويل DOCX إلى Markdown باستخدام Java
  – تعلّم تصدير Markdown مع معادلات LaTeX في دليل واحد.
og_title: إدراج الصور كـ base64 عند تحويل DOCX إلى Markdown في Java
tags:
- Aspose.Words
- Java
- Markdown
- LaTeX
title: تضمين الصور بصيغة base64 عند تحويل DOCX إلى Markdown في Java
url: /ar/java/document-conversion-and-export/embed-images-as-base64-when-converting-docx-to-markdown-in-j/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تضمين الصور كـ base64 عند تحويل DOCX إلى Markdown في Java

هل احتجت يومًا إلى **تضمين الصور كـ base64** أثناء تحويل ملف Word DOCX إلى Markdown؟ لست وحدك. يواجه العديد من المطورين مشكلة عندما يشير الـ Markdown المُولد إلى ملفات صور خارجية، مما يعرقل قابلية النقل لمولدات المواقع الثابتة أو خطوط أنابيب التوثيق.  

الخبر السار؟ باستخدام Aspose.Words for Java يمكنك إخبار المُصدِّر بدمج كل صورة كسلسلة Base64‑مشفرّة، وفي الوقت نفسه تصدير معادلات Office Math كـ LaTeX. في هذا الدرس سنستعرض العملية بالكامل—من إعداد المشروع إلى ملف `.md` النهائي—حتى تتمكن من نسخ الحل ولصقه مباشرة في قاعدة الشيفرة الخاصة بك.

## ما ستتعلمه

- **تحويل docx إلى markdown** باستخدام `MarkdownSaveOptions` من Aspose.Words.  
- كيفية **تضمين الصور كـ base64** لجعل الـ Markdown مكتملًا ذاتيًا.  
- الحيلة لتصديـر **markdown مع latex** للمعادلات، لجعل الناتج متوافقًا مع أدوات مثل Pandoc أو MkDocs.  
- نظرة سريعة على **convert word equations latex** ولماذا يُفضَّل LaTeX للرياضيات على الويب.  
- مثال جاهز **java convert docx markdown** يمكنك تكييفه في دقائق.

> **المتطلبات المسبقة:** Java 17 (أو أي إصدار LTS حديث)، Maven أو Gradle، ورخصة Aspose.Words for Java (الإصدار التجريبي المجاني يكفي للاختبار).

---

## الخطوة 1: إعداد مشروع Java الخاص بك (convert docx to markdown)

أولًا، أنشئ مشروع Maven جديد (أو أضف إلى مشروع موجود). أضف تبعية Aspose.Words إلى `pom.xml`:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.10</version> <!-- latest at time of writing -->
    </dependency>
</dependencies>
```

إذا كنت تفضّل Gradle، فالمكافئ هو:

```groovy
implementation 'com.aspose:aspose-words:24.10'
```

> **نصيحة احترافية:** احرص على تحديث رقم الإصدار؛ الإصدارات الأحدث تجلب إصلاحات للأخطاء المتعلقة بترميز الصور وتصدير LaTeX.

بعد حل التبعية، ستكون جاهزًا لكتابة شيفرة Java التي **java convert docx markdown** بطريقة نظيفة وقابلة لإعادة الإنتاج.

## الخطوة 2: تحميل مستند DOCX المصدر

السطر الأول في أي خط أنابيب تحويل هو تحميل الملف المصدر. فئة `Document` في Aspose.Words تُجرد تفاصيل تنسيق الملف، لذا لا تحتاج للقلق بشأن تفاصيل `.docx` الداخلية.

```java
import com.aspose.words.*;

public class MdToLatex {
    public static void main(String[] args) throws Exception {
        // Load the DOCX you want to transform
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

لماذا ننشئ كائن `Document` هنا؟ لأنه يمنحنا الوصول إلى نموذج الكائن الكامل—الفقرات، الصور، وكائنات Office Math—مما يسمح لنا بالتحكم في طريقة حفظ كل جزء لاحقًا.

## الخطوة 3: تكوين خيارات حفظ Markdown (export markdown with latex)

الآن ننشئ مثيلًا من `MarkdownSaveOptions`. هذا الكائن هو المكان الذي نخبر فيه Aspose.Words بـ **تضمين الصور كـ base64** وتصدير المعادلات كـ LaTeX.

```java
        // Create options for Markdown export
        MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions();

        // Export Office Math as LaTeX (key setting for export markdown with latex)
        markdownSaveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

        // Embed images directly as Base64 strings (the primary requirement)
        markdownSaveOptions.setExportImagesAsBase64(true);
```

### لماذا LaTeX للمعادلات؟

معظم مولدات المواقع الثابتة تفهم كتل `$…$` أو `$$…$$` وتُمرّرها إلى MathJax أو KaTeX. عبر تصدير Office Math كـ LaTeX، تتجنب الصورة المتكلفة التي قد يولّدها Word كبديل. هذا هو جوهر **convert word equations latex**.

### لماذا صور Base64؟

تضمين الصور كـ Base64 يحافظ على ملف الـ Markdown محمولًا—بدون مجلد صور إضافي، دون روابط مكسورة عند نقل المستودع. كما يبسط خطوط أنابيب CI التي تُجمع الوثائق في قطعة واحدة.

## الخطوة 4: حفظ المستند كـ Markdown (java convert docx markdown)

مع وجود الخيارات، السطر النهائي يكتب الملف إلى القرص.

```java
        // Save the document as a Markdown file using the configured options
        document.save("YOUR_DIRECTORY/output.md", markdownSaveOptions);
    }
}
```

هذا كل شيء—شغّل الفئة، وستحصل على `output.md` يحتوي على:

- نص عادي مُحوَّل إلى صيغة Markdown.  
- صور ممثَّلة بـ `![alt text](data:image/png;base64,iVBORw0KGgo…)`.  
- معادلات مثل `$$\frac{a}{b}=c$$` جاهزة لـ MathJax.

### مقتطف من المخرجات المتوقعة

```markdown
# Sample Document

Here is an inline image:

![Sample Image](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABkAAA...

And a math formula:

$$E = mc^2$$
```

لاحظ أن سطر الصورة يبدأ بـ `data:image/png;base64,`—هذا هو سحر **embed images as base64**.

## الخطوة 5: الحالات الخاصة ونصائح الأداء

### الصور الكبيرة

ترميز Base64 يضيف تقريبًا 33 ٪ إلى الحجم. إذا كنت تتعامل مع صور عالية الدقة، ففكّر في تقليل حجمها قبل التحويل أو تعطيل Base64 لتلك الصور المحددة:

```java
markdownSaveOptions.getImageSavingCallback().setExportImagesAsBase64(false);
```

### استهلاك الذاكرة

عند معالجة ملفات DOCX ضخمة، تقوم Aspose.Words ببث المحتوى، لكن ترميز Base64 لا يزال يتطلب تحميل الصورة بالكامل في الذاكرة. إذا صادفت `OutOfMemoryError`، زد حجم heap الخاص بـ JVM (`-Xmx2g`) أو قسّم المستند إلى أقسام أصغر.

### الترميز الانتقائي

إذا كنت تحتاج فقط إلى **تضمين الصور كـ base64** لأقسام معينة، نفّذ `IImageSavingCallback` مخصصًا وقرّر لكل صورة ما إذا كانت ستُشفَّر أم لا.

```java
class MyImageSavingCallback implements IImageSavingCallback {
    public void imageSaving(ImageSavingArgs args) {
        if (args.getImageFileName().contains("logo")) {
            args.setExportImagesAsBase64(true);
        } else {
            args.setExportImagesAsBase64(false);
        }
    }
}
markdownSaveOptions.setImageSavingCallback(new MyImageSavingCallback());
```

## الخطوة 6: التحقق من النتيجة (convert docx to markdown)

افتح `output.md` في أي عارض Markdown يدعم صور HTML وLaTeX (مثل VS Code مع امتداد *Markdown+Math*). يجب أن ترى:

1. جميع الصور معروضة دون أي ملفات خارجية.  
2. المعادلات مُعرضة بشكل جميل عبر MathJax.  
3. بنية المستند الأصلية محفوظة.

إذا لاحظت أي شيء غير صحيح، تأكد من أن `OfficeMathExportMode` مضبوط على `LATEX`—الإعداد الافتراضي هو `IMAGE`، والذي سيستبدل المعادلات بـ PNGs، مما يُفقد هدف **export markdown with latex**.

## أسئلة شائعة وإجابات سريعة

- **هل يعمل هذا مع ملفات .doc؟**  
  نعم. Aspose.Words يتعامل مع `.doc` و `.docx` بصورة موحدة؛ فقط وجه `Document` إلى الملف الأقدم.  

- **هل يمكنني التحكم في صيغة الصورة؟**  
  بشكل افتراضي يستخدم Aspose.Words PNG. يمكنك تغييره عبر `markdownSaveOptions.setImageFormat(ImageSaveOptions.ImageFormat.JPEG)` قبل تفعيل Base64.  

- **ماذا لو أردت مجلد صور منفصل بدلاً من Base64؟**  
  اضبط `markdownSaveOptions.setExportImagesAsBase64(false)` ويمكنك تحديد `markdownSaveOptions.setImagesFolder("images")`.  

- **هل إخراج LaTeX متوافق مع Pandoc؟**  
  بالتأكيد. Pandoc يتعامل مع كتل `$…$` و `$$…$$` كـ LaTeX خام، لذا يمكنك تمرير الـ Markdown مباشرة إلى عمليات التحويل إلى PDF أو HTML أو EPUB.

---

## الخلاصة

أصبح لديك الآن مثال كامل وقابل للتنفيذ ي **embed images as base64** أثناء **convert docx to markdown** و **export markdown with latex** للمعادلات. يوضح المقتطف أعلاه سير العمل بالكامل—from إعداد المشروع إلى معالجة الحالات الخاصة—مما يمنحك أساسًا قويًا لأي مهمة أتمتة توثيق.

الخطوات التالية؟ جرّب ربط هذا التحويل بمهمة Gradle، أو مرّر الـ Markdown المُولد إلى مولد موقع ثابت مثل MkDocs. يمكنك أيضًا تجربة **convert word equations latex** للرياضيات الأكثر تعقيدًا، أو استكشاف `HtmlSaveOptions` من Aspose.Words إذا احتجت HTML بدلًا من Markdown.

برمجة سعيدة، ولتظل توثيقاتك دائمًا محمولة ومُظهرة بأجمل صورة!  

![embed images as base64 example](placeholder-image.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}