---
category: general
date: 2026-02-28
description: تعلم كيفية تضمين الصور أثناء تحويل المستند إلى ماركداون. صدّر الماركداون
  مع الصور واحصل على صور مدمجة داخل الماركداون باستخدام جافا.
draft: false
keywords:
- how to embed images
- convert doc to markdown
- convert word to markdown
- export markdown with images
- inline images in markdown
language: ar
og_description: اكتشف كيفية تضمين الصور أثناء تحويل مستند Word إلى Markdown. يوضح
  لك هذا الدليل كيفية تصدير Markdown مع الصور والحفاظ عليها داخل النص.
og_title: كيفية تضمين الصور عند تحويل Word إلى Markdown
tags:
- markdown
- java
- Aspose.Words
- image handling
title: كيفية تضمين الصور عند تحويل Word إلى Markdown – دليل كامل
url: /ar/java/document-conversion-and-export/how-to-embed-images-when-converting-word-to-markdown-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تضمين الصور عند تحويل Word إلى Markdown – دليل كامل

هل تساءلت يومًا **كيفية تضمين الصور** في ملف Markdown تقوم بإنشائه من مستند Word؟ ربما جربت تصديرًا سريعًا، وانتهى بك الأمر بمجموعة من ملفات الصور المعلقة والروابط المكسورة. هذه مشكلة شائعة—خصوصًا عندما تحتاج إلى ملف `.md` واحد ومحمول يمكنك وضعه في مولد مواقع ثابت أو ملف README على GitHub.

الأخبار السارة؟ يمكنك إخبار أداة التصدير بدمج كل صورة كسلسلة مشفرة Base64، بحيث يكون ملف Markdown الناتج ذاتيًا. في هذا الدليل سنستعرض الخطوات الدقيقة، نعرض لك كامل كود Java، ونشرح لماذا كل جزء مهم. في النهاية ستكون قادرًا على **تحويل doc إلى markdown** مع تضمين الصور، وسترى أيضًا كيف تعدل العملية لسيناريوهات أخرى مثل “تصدير markdown مع الصور” أو “دمج الصور في markdown”.

## ما ستتعلمه

- المكتبات المطلوبة وإعداد مشروع بسيط.  
- كيفية تكوين `MarkdownSaveOptions` لجعل الصور تتحول إلى URI بيانات Base64.  
- لماذا استخدام `ResourceSavingCallback` هو أنقى طريقة للتحكم في معالجة الصور.  
- كيفية التحقق من أن ملف Markdown يحتوي فعليًا على الصور المدمجة.  
- نصائح للحالات الخاصة (صور كبيرة، أنواع MIME مختلفة، واعتبارات الأداء).  

لا تحتاج إلى خبرة سابقة مع Aspose.Words؛ خلفية أساسية في Java تكفي.

---

## المتطلبات المسبقة

قبل أن نغوص في الكود، تأكد من أن لديك:

| المتطلب | لماذا يهم |
|-------------|----------------|
| **Java 17+** (or any recent JDK) | واجهة برمجة تطبيقات Aspose.Words for Java تستهدف Java 8+، لكن استخدام أحدث JDK يمنحك أدوات `Base64` المدمجة. |
| **Aspose.Words for Java** (latest version) | هذه المكتبة توفر `MarkdownSaveOptions` وبنية الـ callback التي سنستخدمها. |
| **A Word document** (`.docx`) that contains at least one image | نحتاج إلى شيء للتحويل؛ المثال يفترض وجود ملف اسمه `sample.docx`. |
| **An IDE or text editor** (IntelliJ, VS Code, etc.) | لتجميع وتشغيل العينة بسرعة. |

أضف تبعية Aspose إلى ملف `pom.xml` (Maven) أو `build.gradle` (Gradle). إليك مقتطف Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Check the latest version on Maven Central -->
</dependency>
```

إذا كنت تفضل Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **نصيحة احترافية:** تقدم Aspose تجربة مجانية لمدة 30 يومًا. احصل على مفتاح ترخيص مؤقت وسجّله مبكرًا لتجنب رسائل العلامة المائية.

## الخطوة 1: إنشاء خيارات حفظ Markdown

أول شيء نفعله هو إنشاء كائن `MarkdownSaveOptions`. هذا الكائن يخبر Aspose كيف نريد أن يتصرف التحويل—معالجة الخطوط، تنسيق القوائم، والأهم بالنسبة لنا، معالجة الصور.

```csharp
// Step 1: Create Markdown save options
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions();
```

في Java الصياغة هي نفسها؛ فقط استبدل كلمة `csharp` بـ `java` في كتلة الشيفرة لاحقًا.  
لماذا هذا مهم: بدون تخصيص الخيارات، سيكتب Aspose كل صورة في ملف منفصل بجوار `.md`. من خلال إعداد كائن الخيارات الآن، نمنح أنفسنا نقطة اعتراض على السلوك الافتراضي.

## الخطوة 2: اعتراض موارد الصور وترميزها كـ Base64

Aspose يطلق callback في كل مرة يريد فيها كتابة مورد (صورة، CSS، إلخ). من خلال تنفيذ `IResourceSavingCallback` يمكننا تحديد ما نفعله بكل مورد. المقتطف أدناه يتحقق مما إذا كان المورد صورة، يمسح اسم الملف (حتى لا يُنشأ ملف خارجي)، يرمز البيانات الثنائية إلى Base64، ويحدد نوع MIME المناسب.

```java
// Step 2: Embed all images directly as Base64 data
markdownSaveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
    @Override
    public void resourceSaving(ResourceSavingArgs args) {
        // Check if the resource being saved is an image
        if (args.getResourceType() == ResourceType.IMAGE) {
            // Suppress writing an external image file
            args.setResourceFileName(null);
            // Encode the image bytes to a Base64 string
            args.setResourceData(Base64.getEncoder()
                    .encodeToString(args.getResourceData()));
            // Set the appropriate MIME type for the embedded image
            args.setResourceContentType("image/png");
        }
    }
});
```

**ما الذي يحدث خلف الكواليس؟**

1. **`args.getResourceType()`** – تصنف Aspose كل كتلة صادرة. نحن نهتم فقط بـ `ResourceType.IMAGE`.  
2. **`args.setResourceFileName(null)`** – بتعيين اسم الملف إلى null نخبر المكتبة *بعدم* كتابة ملف فعلي.  
3. **`Base64.getEncoder().encodeToString(...)`** – مصفوفة البايتات الخام تتحول إلى سلسلة نصية يمكن وضعها بأمان في URI بيانات Markdown.  
4. **`args.setResourceContentType("image/png")`** – هذا يضمن أن وسم Markdown المُنشأ يبدو كـ `![alt](data:image/png;base64,…)`. إذا كان المستند المصدر يحتوي على JPEGs، يمكنك فحص البايتات الأصلية واختيار `"image/jpeg"` بدلاً من ذلك.

> **لماذا Base64؟**  
> معالجات Markdown التي تدعم URIs البيانات ستعرض الصورة مباشرة، ويظل الملف الناتج محمولًا—بدون أصول إضافية للنسخ. هذا مفيد خصوصًا لملفات README على GitHub أو مواقع الوثائق التي تمنع الموارد الخارجية.

## الخطوة 3: تنفيذ التحويل

الآن بعد أن أصبحت الخيارات جاهزة، قم بتحميل مستند Word الخاص بك واستدعِ `save`. المسار الذي تقدمه سيكون موقع ملف Markdown المُولد.

```java
// Step 3: Load the source Word document
Document doc = new Document("sample.docx");

// Step 4: Save the document as a Markdown file using the configured options
doc.save("output/doc.md", markdownSaveOptions);
```

هذا كل شيء—سطران فقط من كود التحويل الفعلي. جميع الأعمال الثقيلة (قراءة DOCX، استخراج الصور، تحويل الفقرات) يتم التعامل معها بواسطة Aspose.

## الخطوة 4: التحقق من النتيجة – ظهور الصور المدمجة

افتح `output/doc.md` في أي محرر نصوص. يجب أن ترى شيئًا مثل:

```markdown
# Sample Document

Here is an inline image:

![Image 1](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...
```

إذا قمت بلصق Markdown في عارض يدعم URIs البيانات (GitHub، معاينة VS Code، أو مولد موقع ثابت)، ستظهر الصورة دون أي ملفات إضافية.

**تحقق سريع من الصحة**:  

- **ابحث عن `data:image/`** – إذا وجدت بعض السلاسل الطويلة، فإن الدمج نجح.  
- **عد نمط `![](`** – يجب أن يتطابق مع عدد الصور في ملف Word الأصلي.

## التعامل مع الحالات الخاصة

### الصور الكبيرة

Base64 يزيد الحجم الأصلي بحوالي **33 %**. بالنسبة للصور الكبيرة جدًا (مثل الصور عالية الدقة)، قد يصبح ملف Markdown صعبًا. ضع في اعتبارك الاستراتيجيات التالية:

| الاستراتيجية | متى يُستخدم |
|----------|--------------|
| **إعادة التحجيم قبل التحويل** – استخدم `java.awt.Image` لتقليل الحجم. | عندما يحتوي المستند المصدر على أصول عالية الدقة لا تحتاج إلى الحجم الكامل. |
| **التحويل إلى JPEG** – غيّر `args.setResourceContentType("image/jpeg")`. | للصور الفوتوغرافية حيث يكون تنسيق PNG غير مضطر. |
| **تقسيم المستند** – قسّم ملف Word إلى أقسام وصدر كل قسم على حدة. | عندما تحتاج إلى الحفاظ على ملف Markdown تحت حد حجم معين (مثلاً حد 10 ميغابايت في GitHub). |

### صور غير PNG

إذا كان مستند Word يحتوي على صيغ مختلطة، يمكنك اكتشاف نوع MIME ديناميكيًا:

```java
String mime = args.getResourceContentType(); // returns something like "image/jpeg"
args.setResourceContentType(mime); // keep original type
```

Aspose يملأ بالفعل `ResourceContentType`، لذا غالبًا لا تحتاج إلى كتابة `"image/png"` يدويًا.

### نصائح الأداء

- **أعد استخدام مثيل واحد من `Base64.Encoder`** إذا كنت تقوم بتحويل العديد من الصور في حلقة.  
- **فعّل `markdownSaveOptions.setExportImagesAsBase64(true)`** (إذا كان إصدار API يدعم ذلك) لتجنب الـ callback تمامًا.  
- **شغّل التحويل في خيط خلفي** عند معالجة وثائق ضخمة في بيئة خادم.

## مثال عملي كامل (مجتمع بالكامل)

فيما يلي برنامج Java جاهز للنسخ واللصق يتضمن الاستيرادات، معالجة الأخطاء، والتدفق الكامل الذي ناقشناه.

```java
import com.aspose.words.*;
import java.util.Base64;
import java.nio.file.Paths;

public class WordToMarkdownWithEmbeddedImages {
    public static void main(String[] args) {
        try {
            // Load the source DOCX
            Document doc = new Document("sample.docx");

            // Configure Markdown save options
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();

            // Embed images as Base64 data URIs
            mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
                @Override
                public void resourceSaving(ResourceSavingArgs rsArgs) {
                    if (rsArgs.getResourceType() == ResourceType.IMAGE) {
                        // Prevent external file creation
                        rsArgs.setResourceFileName(null);
                        // Encode image bytes to Base64
                        String base64 = Base64.getEncoder()
                                .encodeToString(rsArgs.getResourceData());
                        rsArgs.setResourceData(base64);
                        // Preserve original MIME type (PNG, JPEG, etc.)
                        String mime = rsArgs.getResourceContentType();
                        rsArgs.setResourceContentType(mime);
                    }
                }
            });

            // Define output path (ensure directory exists)
            String outputPath = Paths.get("output", "doc.md").toString();
            doc.save(outputPath, mdOptions);

            System.out.println("Conversion complete! Markdown saved to: " + outputPath);
        } catch (Exception e) {
            System.err.println("Error during conversion: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**الناتج المتوقع**: ملف `doc.md` واحد يحتوي على صور Base64 مدمجة، جاهز لأي أداة تدعم Markdown.

## الأسئلة المتكررة

**س1: هل يعمل هذا مع إصدارات أقدم من Aspose.Words؟**  
*عادةً نعم.* واجهة الـ callback مستقرة منذ الإصدار 19. ومع ذلك، اختصار `setExportImagesAsBase64` ظهر في الإصدارات اللاحقة، لذا إذا كنت تستخدم نسخة أقدم فستحتاج إلى الـ callback الصريح الموضح أعلاه.

**س2: ماذا لو احتجت إلى تصدير إلى GitHub Flavored Markdown (GFM)؟**  
`MarkdownSaveOptions` من Aspose ينتج بالفعل صsyntax متوافق مع GFM. الخطوة الإضافية الوحيدة هي التأكد من أن محرك عرض المستودع يدعم URIs البيانات—GitHub يدعم ذلك.

**س3: هل يمكنني استخدام هذا النهج لتنسيقات أخرى، مثل HTML؟**  
بالتأكيد. نفس `ResourceSavingCallback` يعمل مع `HtmlSaveOptions`. فقط غيّر فئة الخيارات واحتفظ بمنطق Base64.

## 

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}