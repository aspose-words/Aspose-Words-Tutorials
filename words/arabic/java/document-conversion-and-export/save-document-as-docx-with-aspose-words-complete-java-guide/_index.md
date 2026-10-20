---
category: general
date: 2026-06-08
description: احفظ المستند بصيغة DOCX باستخدام Aspose.Words في Java. تعلم كيفية إضافة
  ظل إلى الشكل، وتعيين لون تعبئة الشكل، والتحكم في شفافية الشكل خطوة بخطوة.
draft: false
keywords:
- save document as docx
- add shadow to shape
- how to set shape transparency
- how to insert rectangle shape
- set shape fill color
language: ar
og_description: احفظ المستند بصيغة DOCX باستخدام Aspose.Words في جافا. يوضح هذا الدليل
  كيفية إضافة ظل إلى الشكل، وتعيين لون تعبئة الشكل، وضبط شفافية الشكل.
og_title: حفظ المستند كملف DOCX باستخدام Aspose.Words – دليل جافا
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Save document as DOCX using Aspose.Words in Java. Learn to add shadow
    to shape, set shape fill color, and control shape transparency step‑by‑step.
  headline: Save Document as DOCX with Aspose.Words – Complete Java Guide
  type: TechArticle
- description: Save document as DOCX using Aspose.Words in Java. Learn to add shadow
    to shape, set shape fill color, and control shape transparency step‑by‑step.
  name: Save Document as DOCX with Aspose.Words – Complete Java Guide
  steps:
  - name: Expected Result
    text: 'Open `ShadowShape.docx` in Microsoft Word or LibreOffice:'
  - name: What if the shadow isn’t visible?
    text: Shadows are rendered only if the shape isn’t clipped by page margins. Ensure
      there’s enough white space around the shape, or increase the page size via `document.getFirstSection().getPageSetup().setPaperSize(PaperSize.A4)`
      before inserting the shape.
  - name: Can I add multiple shapes?
    text: Absolutely. Just call `builder.insertShape` again after the first shape,
      or move the cursor with `builder.moveTo` to position subsequent shapes. Each
      shape gets its own `ShadowFormat` and fill settings.
  - name: How to make the rectangle transparent instead of the shadow?
    text: Use `rectangleShape.setTransparency(0.5)` (or `setFillColor` with an alpha
      channel). The `setTransparency` method on the shape itself controls the fill’s
      opacity, whereas the one on `ShadowFormat` affects the shadow.
  - name: Does this work with older Word versions?
    text: Yes. Aspose.Words writes `.docx` files that are compatible with Word 2007
      and later. If you need legacy `.doc` support, change the file extension to `.doc`
      and Aspose will automatically downgrade the format.
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Generation
title: حفظ المستند كملف DOCX باستخدام Aspose.Words – دليل Java الكامل
url: /ar/java/document-conversion-and-export/save-document-as-docx-with-aspose-words-complete-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ المستند كملف DOCX باستخدام Aspose.Words – دليل Java الكامل

هل تساءلت يوماً كيف **تحفظ المستند كملف docx** مع إضافة لمسة بصرية إلى الأشكال؟ لست وحدك. يواجه العديد من المطورين صعوبة عندما يحتاجون إلى طريقة سريعة لإنشاء ملف Word يحتوي على مستطيل بلون تعبئة مخصص وظل خفيف. في هذا الدرس سنستعرض بالضبط ذلك—كيفية إدراج شكل مستطيل، تعيين لون التعبئة، تعديل الشفافية، وأخيراً **حفظ المستند كملف docx** بسطر واحد من الكود.

سنجيب أيضاً على الأسئلة المتبقية مثل: *كيفية إضافة ظل إلى الشكل*، *كيفية ضبط شفافية الشكل*، و*كيفية إدراج شكل مستطيل* دون أن تفقد أعصابك. بنهاية الدرس ستحصل على برنامج Java جاهز للتنفيذ ينتج ملف `.docx` مصقول، مثالي للتقارير، الفواتير، أو أي مستند يحتاج إلى لمسة تصميم.

## ما ستتعلمه

- الخطوات الدقيقة **لحفظ المستند كملف docx** باستخدام Aspose.Words for Java.
- كيفية **إضافة ظل إلى الشكل** والتحكم في إزاحته، الضبابية، ولونه.
- الصياغة الخاصة بـ **كيفية ضبط شفافية الشكل** لجعل الظل يبدو مثالياً.
- الطريقة الخاصة بـ **كيفية إدراج شكل مستطيل** وإعطائه خلفية باستخدام **set shape fill color**.
- نصائح، متاعب شائعة، وتوصيات أفضل الممارسات للعمل مع الأشكال في مستندات Word.

> **المتطلبات المسبقة:** تثبيت Java 8+، وجود Maven أو Gradle لجلب Aspose.Words، وفهم أساسي لصياغة Java. لا تحتاج إلى خبرة سابقة مع Aspose—فقط اتبع الخطوات.

---

## الخطوة 1: إعداد Aspose.Words في مشروع Java الخاص بك

قبل أن نتمكن من **حفظ المستند كملف docx**، نحتاج إلى مكتبة Aspose.Words على مسار الفئة. إذا كنت تستخدم Maven، أضف الاعتماد التالي إلى ملف `pom.xml` الخاص بك:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Use the latest stable version -->
</dependency>
```

لـ Gradle، ضع هذا في ملف `build.gradle` الخاص بك:

```groovy
implementation 'com.aspose:aspose-words:23.12'
```

بعد حل المكتبة، ستكون جاهزاً لكتابة الكود الذي سيقوم **بحفظ المستند كملف docx**.

## الخطوة 2: إنشاء مستند فارغ جديد وDocumentBuilder

فئة `Document` تمثل ملف Word بالكامل، بينما `DocumentBuilder` هي فرشاتك. فكر في الـ builder كالمؤشر الذي يتيح لك إدراج نص، جداول، أو أشكال في أي موضع تحتاجه.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Create a fresh, empty document
        Document document = new Document();

        // DocumentBuilder lets us add content to the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

في هذه المرحلة يكون المستند فارغاً، لكن لدينا الأدوات اللازمة **لحفظ المستند كملف docx** لاحقاً.

## الخطوة 3: كيفية إدراج شكل مستطيل

الجزء الممتع الآن—إضافة مستطيل. طريقة `insertShape` تستقبل تعداد `ShapeType`، العرض، والارتفاع (بالنقاط). إذا كنت تتساءل عن الوحدات، 72 نقطة تساوي بوصة واحدة، لذا 200 × 100 نقطة تعطيك تقريباً مستطيل بحجم 2.78 × 1.39 بوصة.

```java
        // Insert a rectangle shape of 200x100 points
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 200, 100);
```

هذا السطر الواحد يقوم بثلاثة أشياء:

1. ينشئ كائن الشكل.
2. يضعه في موضع المؤشر الحالي.
3. يُعيد مرجعاً (`rectangleShape`) حتى نتمكن من تعديل مظهره.

## الخطوة 4: تعيين لون تعبئة الشكل

مربع رمادي عادي ليس مثيراً، أليس كذلك؟ لنمنحه **set shape fill color** يتماشى مع لوحة ألوان علامتنا التجارية. تستخدم Aspose `java.awt.Color` لقيم الألوان، لذا اختر أي ثابت أو أنشئ قيمة RGB مخصصة.

```java
        // Apply a light gray fill color to the rectangle
        rectangleShape.setFillColor(java.awt.Color.LIGHT_GRAY);
```

يمكنك استبدال `LIGHT_GRAY` بـ `Color.BLUE`، أو `new Color(255, 215, 0)` (ذهب)، أو أي لون تفضله. المفتاح هو أن الشكل الآن يمتلك خلفية، والتي ستظهر بمجرد **حفظ المستند كملف docx**.

## الخطوة 5: إضافة ظل إلى الشكل

الظلال تعطي العمق. توفر Aspose كائن `ShadowFormat` حيث يمكنك التحكم في الإزاحة، نصف قطر الضبابية، الشفافية، واللون. دعنا نستعرض كل خاصية.

```java
        // Configure shadow offset (horizontal & vertical) in points
        rectangleShape.getShadowFormat().setOffsetX(5);
        rectangleShape.getShadowFormat().setOffsetY(5);

        // Set the blur radius – higher values make the shadow softer
        rectangleShape.getShadowFormat().setBlurRadius(4);

        // **How to set shape transparency** – 0.0 = fully opaque, 1.0 = fully transparent
        rectangleShape.getShadowFormat().setTransparency(0.3); // 30% transparent

        // Choose a dark gray color for the shadow itself
        rectangleShape.getShadowFormat().setColor(java.awt.Color.DARK_GRAY);
```

لاحظ التعليق الذي يُعد إجابة سريعة على *كيفية ضبط شفافية الشكل*. طريقة `setTransparency` تتوقع قيمة مزدوجة بين 0 و 1، مما يجعل ضبط المظهر بديهياً.

> **نصيحة احترافية:** إذا أردت تأثيراً أكثر دراماتيكية، زد `OffsetX/Y` إلى 10 و`BlurRadius` إلى 8. فقط تذكر أن الإزاحات الكبيرة قد تدفع الظل خارج هوامش الصفحة، مما قد يُقص عند الطباعة.

## الخطوة 6: حفظ المستند كملف DOCX

اكتمل كل العمل البصري؛ الآن ببساطة **نحفظ المستند كملف docx**. تسمح لك Aspose بتحديد الصيغة عبر امتداد الملف، لذا تمرير `"ShadowShape.docx"` يكفي.

```java
        // Persist the document to a .docx file
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

استبدل `YOUR_DIRECTORY` بمسار مطلق أو نسبي يمكن لعملية Java الكتابة إليه. عند تشغيل البرنامج، سيظهر ملف Word في ذلك الموقع، يحتوي على مستطيل بلون تعبئة رمادي فاتح وظل رمادي داكن خفيف.

### النتيجة المتوقعة

افتح `ShadowShape.docx` في Microsoft Word أو LibreOffice:

- صفحة واحدة بها مستطيل مركزي.
- داخل المستطيل رمادي فاتح.
- ظل ناعم، شبه شفاف، رمادي داكن يظهر 5 نقطة إلى اليمين والأسفل، مما يمنح الشكل مظهرًا مرتفعًا.

إذا رأيت هذه العناصر، تهانينا—لقد نجحت في **حفظ المستند كملف docx** مع شكل مُصمم!

## أسئلة شائعة وحالات خاصة

### ماذا لو لم يظهر الظل؟

يتم عرض الظلال فقط إذا لم يكن الشكل مقطوعًا بهوامش الصفحة. تأكد من وجود مساحة بيضاء كافية حول الشكل، أو زد حجم الصفحة عبر `document.getFirstSection().getPageSetup().setPaperSize(PaperSize.A4)` قبل إدراج الشكل.

### هل يمكن إضافة أشكال متعددة؟

بالطبع. فقط استدعِ `builder.insertShape` مرة أخرى بعد الشكل الأول، أو حرّك المؤشر باستخدام `builder.moveTo` لتحديد موضع الأشكال التالية. كل شكل يحصل على إعدادات `ShadowFormat` وتعبئة خاصة به.

### كيف أجعل المستطيل شفافًا بدلاً من الظل؟

استخدم `rectangleShape.setTransparency(0.5)` (أو `setFillColor` مع قناة ألفا). طريقة `setTransparency` على الشكل نفسه تتحكم في شفافية التعبئة، بينما تلك الموجودة على `ShadowFormat` تؤثر على الظل.

### هل يعمل هذا مع إصدارات Word القديمة؟

نعم. تكتب Aspose.Words ملفات `.docx` متوافقة مع Word 2007 وما بعده. إذا كنت تحتاج دعم `.doc` القديم، غير امتداد الملف إلى `.doc` وستقوم Aspose بتخفيض الصيغة تلقائيًا.

## مثال كامل يعمل

فيما يلي البرنامج الكامل الجاهز للتنفيذ. انسخه‑الصقه في بيئة التطوير المتكاملة، عدّل مسار الإخراج، ثم اضغط **Run**.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape of desired size and set its fill color
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 200, 100);
        rectangleShape.setFillColor(java.awt.Color.LIGHT_GRAY); // set shape fill color

        // Step 3: Configure the shadow effect – offset, blur, transparency, and color
        rectangleShape.getShadowFormat().setOffsetX(5);
        rectangleShape.getShadowFormat().setOffsetY(5);
        rectangleShape.getShadowFormat().setBlurRadius(4);
        rectangleShape.getShadowFormat().setTransparency(0.3); // how to set shape transparency
        rectangleShape.getShadowFormat().setColor(java.awt.Color.DARK_GRAY); // add shadow to shape

        // Step 4: Save the document with the shaped shadow to a file
        document.save("YOUR_DIRECTORY/ShadowShape.docx"); // save document as docx
    }
}
```

شغّل البرنامج، افتح الملف المُنشأ، واستمتع بالنتيجة. 🎉

## ملخص: لماذا هذا النهج رائع

- **البساطة:** أربع خطوات منطقية فقط **لحفظ المستند كملف docx** مع مستطيل مُصمم.
- **المرونة:** كل خاصية بصرية (`fill color`، `shadow offset`، `blur radius`، `transparency`) متاحة عبر API واضح.
- **القابلية للنقل:** يعمل نفس الكود على Windows، macOS، وLinux طالما تم تثبيت Java وAspose.Words.
- **الصيانة:** بفصل إنشاء الشكل، تنسيقه، وحفظه، يمكنك توسيع المثال بسهولة—إضافة نص، صور، أو حتى حلقات تولد أشكالاً متعددة.

## الخطوات التالية والمواضيع ذات الصلة

- **إضافة نص داخل المستطيل** باستخدام `builder.insertParagraph` بعد تحديد موضع المؤشر.
- **إنشاء تعبئة متدرجة** عبر `rectangleShape.getFill().setFillType(FillType.GRADIENT)`.
- **التصدير إلى PDF** باستدعاء `document.save("output.pdf")`—مثالي للتوزيع.
- استكشاف **كيفية إدراج شكل مستطيل** داخل الجداول أو الرؤوس لتصاميم أكثر تعقيدًا.
- الغوص في **set shape fill color** باستخدام قيم RGB مخصصة أو تعبئات نمطية للعلامة التجارية.

لا تتردد في التجربة—بدل الألوان، غير شفافية الظل، أو رص أشكالًا متعددة. API الخاص بـ Aspose.Words سخي، والآن تعرف النمط الأساسي **لحفظ المستند كملف docx** مع تحسينات بصرية.

---

![save document as docx example](alt="save document as docx example showing rectangle with shadow")

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to Load HTML and Save as DOCX using Aspose.Words for Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}