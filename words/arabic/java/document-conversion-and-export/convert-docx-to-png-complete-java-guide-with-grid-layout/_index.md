---
category: general
date: 2026-06-27
description: حوّل ملفات DOCX إلى PNG بسرعة باستخدام Aspose.Words للغة Java. تعلّم
  تصدير جميع الصفحات بصيغة PNG وتحديد عدد الصفوف في كل صفحة وعدد الأعمدة في كل صفحة
  دفعة واحدة.
draft: false
keywords:
- convert docx to png
- export all pages png
- how to set rows per page
- how to set columns per page
language: ar
og_description: تحويل DOCX إلى PNG في Java باستخدام Aspose.Words. يوضح هذا الدليل
  كيفية تصدير جميع الصفحات كـ PNG وتكوين عدد الصفوف في كل صفحة وعدد الأعمدة في كل
  صفحة.
og_title: تحويل DOCX إلى PNG – دليل تصدير شبكة Java
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Convert DOCX to PNG quickly using Aspose.Words for Java. Learn to export
    all pages PNG and set rows per page and columns per page in one go.
  headline: Convert DOCX to PNG – Complete Java Guide with Grid Layout
  type: TechArticle
tags:
- Aspose.Words
- Java
- DOCX
- PNG
- Image conversion
title: تحويل DOCX إلى PNG – دليل جافا كامل مع تخطيط الشبكة
url: /ar/java/document-conversion-and-export/convert-docx-to-png-complete-java-guide-with-grid-layout/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تحويل DOCX إلى PNG – دليل Java الكامل مع تخطيط الشبكة

هل تساءلت يومًا كيف **تحويل DOCX إلى PNG** دون حفظ كل صفحة يدويًا؟ لست وحدك. يواجه العديد من المطورين صعوبة عندما يحتاجون إلى صورة واحدة تُظهر عدة صفحات في آنٍ واحد، خاصةً لصور المعاينة المصغرة أو للمشاركة السريعة.  

خبر سار: باستخدام Aspose.Words for Java يمكنك **تصدير جميع الصفحات PNG** بضغطة واحدة، ويمكنك أيضًا تحديد **كيفية تعيين الصفوف لكل صفحة** و**كيفية تعيين الأعمدة لكل صفحة**. في هذا الدرس سنستعرض العملية بالكامل، من تحميل مستند Word إلى إنتاج صورة شبكة مرتبة.

## ما يغطيه هذا الدرس

سنبدأ بسرد المتطلبات المسبقة، ثم نقسم الحل إلى خطوات واضحة. في النهاية، ستكون قادرًا على:

* تحميل أي ملف `.docx` من القرص.  
* تكوين `ImageSaveOptions` لتصدير **جميع الصفحات PNG** مرة واحدة.  
* تعريف شبكة 2 × 2 (أو أي حجم) باستخدام **كيفية تعيين الصفوف لكل صفحة** و**كيفية تعيين الأعمدة لكل صفحة**.  
* حفظ النتيجة كملف PNG واحد يمكنك تضمينه في أي مكان.

بدون سكريبتات خارجية، بدون حركات سطر أوامر—فقط كود Java نقي يمكنك وضعه في مشروعك.

### المتطلبات المسبقة

| المتطلب | لماذا هو مهم |
|-------------|----------------|
| Java 8 أو أحدث | Aspose.Words 23.9+ يحتاج على الأقل Java 8. |
| Aspose.Words for Java JAR | يوفر الفئات `Document` و `ImageSaveOptions`. |
| ملف `.docx` للاختبار | المصدر الذي ستحوله. |
| IDE أو أداة بناء (Maven/Gradle) | لتجميع وتشغيل المثال. |

إذا كان لديك كل ما سبق، رائع—لنبدأ.

## الخطوة 1: إعداد المشروع واستيراد Aspose.Words

أولاً، أضف تبعية Aspose.Words. إذا كنت تستخدم Maven، الصق هذا في ملف `pom.xml` الخاص بك:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

لـ Gradle، يكون الشكل كالتالي:

```groovy
implementation 'com.aspose:aspose-words:23.9'
```

بمجرد أن تكون المكتبة على مسار الفئة (classpath)، يمكنك بدء كتابة الكود. بيان الاستيراد بسيط:

```java
import com.aspose.words.*;
```

> **نصيحة احترافية:** احفظ ملفات Aspose jar في مجلد `libs/` وأضفها إلى مسار البناء إذا لم تكن تستخدم مدير تبعيات.

## الخطوة 2: تحميل المستند المصدر

تحميل DOCX سهل كما توجيه مُنشئ `Document` إلى مسار ملف. هذه هي الخطوة الأولى الملموسة في **convert docx to png**.

```java
// Step 2: Load the source document
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

استبدل `YOUR_DIRECTORY` بالمجلد الفعلي الذي يوجد فيه ملف Word الخاص بك. إذا لم يُعثر على الملف، ستطرح Aspose استثناء `FileNotFoundException`، لذا تأكد من صحة المسار.

## الخطوة 3: إنشاء خيارات حفظ الصورة للـ PNG

الآن نخبر Aspose أننا نريد إخراج PNG. تسمح لك الفئة `ImageSaveOptions` بضبط التحويل بدقة، بما في ذلك العلامة الحيوية **export all pages png**.

```java
// Step 3: Create image save options for PNG format
ImageSaveOptions pngOptions = new ImageSaveOptions(SaveFormat.PNG);
```

في هذه المرحلة يصبح كائن الخيارات جاهزًا، لكننا لم نحدد *كيفية* التعامل مع الصفحات المتعددة بعد.

## الخطوة 4: تصدير جميع الصفحات PNG

بشكل افتراضي، سيحفظ Aspose كل صفحة كملف منفصل. لتجميعها معًا، اضبط `pageCount` إلى `0`. في مصطلحات Aspose، يعني `0` “جميع الصفحات”.

```java
// Step 4: Export all pages (0 means all pages)
pngOptions.setPageCount(0);
```

الآن تعرف المكتبة أنك تريد **تصدير جميع الصفحات PNG** دفعة واحدة. إذا كنت تريد فقط الصفحات الثلاث الأولى، يمكنك استخدام `pngOptions.setPageCount(3);`.

## الخطوة 5: ترتيب الصفحات في تخطيط شبكة

هنا يأتي سحر **كيفية تعيين الصفوف لكل صفحة** و**كيفية تعيين الأعمدة لكل صفحة**. سنطلب من Aspose ترتيب الصفحات في شبكة، مشابهة لورقة الاتصال.

```java
// Step 5: Arrange pages in a grid layout
pngOptions.setPageLayout(ImageSaveOptions.PageLayout.GRID);
```

تخطيط `GRID` يخبر المحرك بترصيف الصفحات أفقياً وعمودياً وفق الأبعاد التي سنحددها لاحقًا.

## الخطوة 6: تعريف أبعاد الشبكة (صفوف × أعمدة)

يمكنك اختيار أي تركيبة تناسب احتياجاتك. المثال أدناه يُنشئ شبكة 2 × 2، لكن يمكنك بسهولة التحويل إلى 3 × 4 أو حتى صف واحد.

```java
// Step 6: Define the grid dimensions (2 rows × 2 columns)
pngOptions.setRowsPerPage(2);      // how to set rows per page
pngOptions.setColumnsPerPage(2);   // how to set columns per page
```

إذا كان لديك صفحات أكثر من الخلايا، سيستمر Aspose إلى الصف التالي تلقائيًا. وعلى العكس، إذا كان عدد الصفحات أقل، ستبقى الخلايا الفارغة شفافة.

## الخطوة 7: حفظ المستند كصورة PNG واحدة

أخيرًا، نخبر Aspose بكتابة الصورة المدمجة إلى القرص. يمكن أن يكون اسم الملف أي شيء تريده؛ فقط احتفظ بامتداد `.png`.

```java
// Step 7: Save the document as a single PNG image using the grid layout
document.save("YOUR_DIRECTORY/Grid.png", pngOptions);
```

عند انتهاء البرنامج، ستجد `Grid.png` في نفس المجلد. افتحه، وسترى الصفحات الأربعة الأولى من `input.docx` مرتبة في شبكة 2 × 2 أنيقة.

### النتيجة المتوقعة

| الصفحة | الموضع في الشبكة |
|------|------------------|
| 1    | أعلى‑يسار |
| 2    | أعلى‑يمين |
| 3    | أسفل‑يسار |
| 4    | أسفل‑يمين |

إذا كان مستندك المصدر يحتوي على أكثر من أربع صفحات، ستبدأ الصفحة الخامسة صفًا جديدًا (إذا زدت `rowsPerPage`) أو ستُهمل (إذا أبقيت الشبكة 2 × 2). سيحتفظ PNG بأبعاد الصفحة الأصلية، لذا سيكون حجم الصورة النهائي `rows × pageHeight` في `columns × pageWidth`.

## مثال كامل يعمل

فيما يلي البرنامج الكامل الجاهز للتنفيذ بلغة Java. انسخه إلى فئة تسمى `DocxToPngGrid.java`، عدل المسارات، ثم شغّله.

```java
import com.aspose.words.*;

public class DocxToPngGrid {
    public static void main(String[] args) {
        try {
            // 1️⃣ Load the DOCX file
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // 2️⃣ Prepare PNG save options
            ImageSaveOptions pngOptions = new ImageSaveOptions(SaveFormat.PNG);
            pngOptions.setPageCount(0);                     // export all pages PNG
            pngOptions.setPageLayout(ImageSaveOptions.PageLayout.GRID);

            // 3️⃣ Configure grid (2 rows × 2 columns)
            pngOptions.setRowsPerPage(2);   // how to set rows per page
            pngOptions.setColumnsPerPage(2); // how to set columns per page

            // 4️⃣ Save the combined image
            document.save("YOUR_DIRECTORY/Grid.png", pngOptions);

            System.out.println("Conversion complete! Check Grid.png.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

شغّله باستخدام:

```bash
javac -cp "path/to/aspose-words-23.9.jar" DocxToPngGrid.java
java -cp ".:path/to/aspose-words-23.9.jar" DocxToPngGrid
```

سترى الرسالة `Conversion complete!` مطبوعة في وحدة التحكم، وسيظهر ملف `Grid.png` في المجلد المستهدف.

## أسئلة شائعة وحالات خاصة

**ماذا لو أردت تنسيق صورة مختلف؟**  
استبدل `SaveFormat.PNG` بـ `SaveFormat.JPEG` أو `SaveFormat.TIFF`. يبقى باقي الكود كما هو.

**هل يمكنني التحكم في جودة الصورة؟**  
نعم. بالنسبة لـ JPEG يمكنك استدعاء `pngOptions.setJpegQuality(90);`. لا توجد إعداد جودة للـ PNG لأنه غير مضغوط.

**ماذا عن المستندات الكبيرة؟**  
عند التعامل مع عدد كبير من الصفحات، قد يصبح PNG الناتج ضخمًا من حيث الذاكرة. فكر في زيادة `rowsPerPage`/`columnsPerPage` أو تقسيم الناتج إلى صور متعددة.

**هل أحتاج إلى ترخيص؟**  
يعمل Aspose.Words في وضع التقييم بدون ترخيص، لكن PNG المولد سيحتوي على علامة مائية. اشترِ ترخيصًا لإزالتها.

## نصائح احترافية للاستخدام في الإنتاج

* **إعادة استخدام `ImageSaveOptions`** – إذا كنت تحول العديد من المستندات دفعة واحدة، أنشئ الخيارات مرة واحدة وأعد استخدامها لتقليل إنشاء الكائنات.  
* **تدفق الإخراج** – بدلاً من الحفظ إلى ملف، يمكنك الكتابة إلى `ByteArrayOutputStream` وإرسال PNG عبر HTTP.  
* **سلامة الخيوط** – كائنات `Document` غير آمنة للخيوط، لذا أنشئ `Document` جديد لكل خيط.  
* **تحليل الذاكرة** – بالنسبة لملفات PDF التي تتجاوز 100 صفحة، راقب استهلاك الـ heap؛ قد تحتاج إلى زيادة علم JVM `-Xmx`.

## الخلاصة

لقد استعرضنا طريقة عملية **تحويل docx إلى png** باستخدام Aspose.Words for Java، بدءًا من تحميل الملف إلى تكوين **export all pages png**، وإظهار **كيفية تعيين الصفوف لكل صفحة** و**كيفية تعيين الأعمدة لكل صفحة** لتخطيط شبكة. تُعطيك الصورة PNG الوحيدة لمحة بصرية مدمجة لمستند Word متعدد الصفحات—مثالية للمعاينات، مرفقات البريد الإلكتروني، أو المشاركة السريعة.

هل أنت مستعد للتحدي التالي؟ جرّب إضافة علامة مائية إلى كل صفحة، أو جرب أحجام شبكة مختلفة لتتناسب مع تصميم واجهتك. يمكنك أيضًا ربط هذا التحويل بمولد PDF لإنتاج تقارير متعددة الصيغ في خط أنابيب واحد.

إذا واجهت أي صعوبات، اترك تعليقًا أدناه—برمجة سعيدة!  

![convert docx to png example](placeholder.png){alt="مثال تحويل docx إلى png"}

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية تحويل DOCX إلى PNG في Java – Aspose.Words](/words/spanish/java/document-converting/converting-documents-images/)
- [Wie man DOCX in PNG in Java konvertiert – Aspose.Words](/words/german/java/document-converting/converting-documents-images/)
- [Comment convertir DOCX en PNG en Java – Aspose.Words](/words/french/java/document-converting/converting-documents-images/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}