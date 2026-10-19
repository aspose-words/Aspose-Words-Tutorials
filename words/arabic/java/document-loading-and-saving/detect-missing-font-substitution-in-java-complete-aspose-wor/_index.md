---
category: general
date: 2026-06-05
description: اكتشاف استبدال الخط المفقود في جافا باستخدام Aspose.Words. تعلّم كيفية
  تكوين LoadOptions و FontSettings ودالات التحذير لضمان معالجة موثوقة للمستندات.
draft: false
keywords:
- detect missing font substitution
- Java Aspose.Words
- LoadOptions configuration
- FontSettings warning callback
- document loading Java
language: ar
og_description: اكتشاف استبدال الخط المفقود في Java باستخدام Aspose.Words. يوضح هذا
  الدليل خطوة بخطوة كيفية إعداد LoadOptions و FontSettings واستدعاء التحذير لالتقاط
  الخطوط المفقودة.
og_title: اكتشاف استبدال الخط المفقود في جافا – دليل Aspose.Words الكامل
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: detect missing font substitution in Java using Aspose.Words. Learn
    how to configure LoadOptions, FontSettings, and warning callbacks for reliable
    document processing.
  headline: detect missing font substitution in Java – Complete Aspose.Words Guide
  type: TechArticle
- description: detect missing font substitution in Java using Aspose.Words. Learn
    how to configure LoadOptions, FontSettings, and warning callbacks for reliable
    document processing.
  name: detect missing font substitution in Java – Complete Aspose.Words Guide
  steps:
  - name: 4.1 Quick verification
    text: Run the program from your IDE or via `java -cp .;aspose-words-23.12.jar
      MissingFontDetector`. If the document references a font you don’t have, you’ll
      see the warning message printed. If the console stays silent, either the font
      exists on your machine or the document doesn’t request any missing font
  - name: 4.2 Logging instead of `System.out`
    text: 'In production code you probably want a logger:'
  - name: 4.3 Handling other warning types
    text: 'The callback receives *all* warnings, not just font issues. If you’d like
      to keep an eye on other problems (e.g., `UNKNOWN_STYLE`), add extra `if` branches.
      Here’s a quick example:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Font handling
title: اكتشاف استبدال الخط المفقود في Java – دليل Aspose.Words الكامل
url: /ar/java/document-loading-and-saving/detect-missing-font-substitution-in-java-complete-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# اكتشاف استبدال الخط المفقود في Java – دليل Aspose.Words الكامل

هل تساءلت يومًا كيف **تكتشف استبدال الخط المفقود** عند تحميل مستند Word في Java؟ لست وحدك. الخطوط المفقودة يمكن أن تتسبب في تشويه ملفات PDF أو الصفحات المعروضة بصمت، واكتشافها مبكرًا يوفر ساعات من وقت التصحيح. في هذا الدرس سنستعرض حلًا عمليًا لا يقوم فقط بتحميل المستند بل يخبرك أيضًا بالضبط متى يحدث استبدال الخط.

سنغطي كل شيء من إنشاء `LoadOptions` إلى ربط `WarningCallback` الذي يطبع رسالة واضحة كلما استبدلت Aspose.Words خطًا مفقودًا. في النهاية ستحصل على مقتطف قابل لإعادة الاستخدام يعمل مع أي ملف `.docx`، وستفهم *لماذا* كل جزء مهم. لا مكتبات إضافية، مجرد Java عادي وAspose.Words.

## ما ستتعلمه

- كيفية تكوين **LoadOptions** لاستخدام **FontSettings** مخصصة.  
- كيفية تنفيذ **IWarningCallback** يلتقط تحذيرات `FONT_SUBSTITUTION`.  
- كيفية تحميل مستند مع مراقبة آمنة للخطوط المفقودة.  
- مخرجات وحدة التحكم المتوقعة وكيفية تعديل الكود لاستخدام أطر تسجيل (logging) مختلفة.  

**المتطلبات المسبقة**: تثبيت Java 8+، وجود Aspose.Words for Java (الإصدار 23.12 أو أحدث) في مسار الفئة (classpath)، وعينة `.docx` تشير إلى خط غير مثبت على جهازك. هذا كل ما تحتاجه—لا أدوات بناء إضافية مطلوبة.

---

## الخطوة 1: إعداد المشروع وإضافة Aspose.Words

قبل الغوص في الكود، تأكد من توفر Aspose.Words. إذا كنت تستخدم Maven، أضف الاعتماد التالي إلى ملف `pom.xml` الخاص بك:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

إذا كنت تفضل Gradle، فإن ما يعادله هو:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

بعد إضافة المكتبة إلى مسار الفئة، يمكنك **اكتشاف استبدال الخط المفقود** في استدعاء طريقة واحد.

---

## الخطوة 2: إنشاء LoadOptions وربط FontSettings

جوهر الحل يكمن في إعداد كائن `LoadOptions` يعرف كيف يراقب مشاكل الخطوط. إليك الكود مفصلًا سطرًا بسطر.

```java
import com.aspose.words.*;

public class MissingFontDetector {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Prepare load options – this object controls how the document is read.
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Create FontSettings – it holds font‑related configuration.
        FontSettings fontSettings = new FontSettings();

        // 3️⃣ Register a warning callback that will be invoked on font substitution.
        fontSettings.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about FONT_SUBSTITUTION warnings.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substitution detected: " + info.getMessage());
                }
            }
        });

        // 4️⃣ Attach the FontSettings to the LoadOptions.
        loadOptions.setFontSettings(fontSettings);
```

**لماذا هذا مهم**: `LoadOptions` يخبر Aspose.Words *كيف* يفسر الملف الوارد. من خلال توصيل `FontSettings` مخصصة، نمنح القارئ نقطة ربط (`IWarningCallback`) تُفعل **بالضبط عندما يتم استبدال خط مفقود**. بدون هذا النداء العكسي، ستستبدل Aspose.Words الخط صامتًا ولن تعرف ذلك.

---

## الخطوة 3: تحميل المستند باستخدام الخيارات المكوَّنة

الآن بعد أن نظام التحذير جاهز، يصبح تحميل المستند أمرًا بسيطًا.

```java
        // 5️⃣ Load the document using the prepared options.
        // Replace the path with the location of your test file.
        String docPath = "YOUR_DIRECTORY/docWithMissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Optional: do something with the document (e.g., save as PDF).
        // doc.save("output.pdf");
    }
}
```

عند تنفيذ استدعاء `new Document(...)`، تقوم Aspose.Words بقراءة الملف، وتفحص كل إشارة إلى خط، وإذا لم تتمكن من العثور على خط مطابق على النظام، فإنها تُطلق طريقة `warning` التي عرّفناها مسبقًا. ستظهر سطرًا في وحدة التحكم مثل:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

هذا السطر هو ناتج **اكتشاف استبدال الخط المفقود** الذي كنت تبحث عنه.

---

## الخطوة 4: التحقق من النتيجة وتعديل النداء العكسي (متقدم)

### 4.1 التحقق السريع

شغّل البرنامج من بيئة التطوير المتكاملة (IDE) أو عبر `java -cp .;aspose-words-23.12.jar MissingFontDetector`. إذا كان المستند يشير إلى خط غير موجود لديك، فسترى رسالة التحذير مطبوعة. إذا بقيت وحدة التحكم صامتة، فإما أن الخط موجود على جهازك أو أن المستند لا يطلب أي خطوط مفقودة.

### 4.2 التسجيل بدلاً من `System.out`

في الكود الإنتاجي ربما ترغب باستخدام مسجل (logger):

```java
import java.util.logging.Logger;

private static final Logger logger = Logger.getLogger(MissingFontDetector.class.getName());

fontSettings.setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        logger.warning("Font substitution: " + info.getMessage());
    }
});
```

هذا التغيير الصغير يجعل آلية **اكتشاف استبدال الخط المفقود** تتفاعل بسلاسة مع أنظمة التسجيل الموجودة.

### 4.3 معالجة أنواع تحذير أخرى

النداء العكسي يستقبل *جميع* التحذيرات، وليس فقط مشاكل الخطوط. إذا أردت مراقبة مشاكل أخرى (مثل `UNKNOWN_STYLE`)، أضف فروع `if` إضافية. إليك مثالًا سريعًا:

```java
if (info.getWarningType() == WarningType.UNKNOWN_STYLE) {
    logger.info("Unknown style encountered: " + info.getMessage());
}
```

---

## الخطوة 5: الأخطاء الشائعة ونصائح احترافية

| المشكلة | لماذا تحدث | الحل |
|--------|------------|------|
| **لا يظهر أي تحذير** | الخط موجود فعليًا على نظام التشغيل، أو يستخدم المستند بديلًا يعتبره Aspose.Words “موجودًا”. | احذف الخط من النظام مؤقتًا أو استخدم اسم خط غير موجود فعليًا في المستند المصدر. |
| **النداء العكسي لا يُستدعى أبدًا** | تم استدعاء `setWarningCallback` على كائن `FontSettings` *مختلف* عن ذلك المرفق بـ `LoadOptions`. | تأكد من استدعاء `loadOptions.setFontSettings(fontSettings)` **بعد** تكوين النداء العكسي. |
| **تباطؤ الأداء** | تحميل العديد من المستندات الكبيرة مع النداءات العكسية قد يضيف عبئًا. | خزن كائن `FontSettings` واحد واستخدمه عبر عمليات التحميل المتعددة إذا كنت تعالج دفعات. |
| **تعدد الخيوط** | `FontSettings` غير آمن للخطوط المتعددة بشكل افتراضي. | أنشئ `FontSettings` منفصل لكل خيط أو قم بمزامنة الوصول. |

**نصيحة احترافية**: إذا كنت تولد ملفات PDF لخدمة ويب، قد ترغب في جمع كل تحذيرات الاستبدال في قائمة وإرجاعها في استجابة الـ API، بدلاً من طباعتها على وحدة التحكم.

---

## مثال كامل جاهز للتنفيذ (انسخه‑الصقه)

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {
        // Prepare load options
        LoadOptions loadOptions = new LoadOptions();

        // Configure font settings with a warning callback
        FontSettings fontSettings = new FontSettings();
        fontSettings.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substitution detected: " + info.getMessage());
                }
            }
        });

        // Attach font settings to load options
        loadOptions.setFontSettings(fontSettings);

        // Path to the document that contains a missing font
        String docPath = "YOUR_DIRECTORY/docWithMissingFont.docx";

        // Load the document – this triggers the callback if needed
        Document doc = new Document(docPath, loadOptions);

        // Optional: save as PDF to verify visual output
        // doc.save("output.pdf");

        System.out.println("Document loaded successfully.");
    }
}
```

**مخرجات وحدة التحكم المتوقعة** (بافتراض أن الملف يشير إلى خط مفقود):

```
⚠️ Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
Document loaded successfully.
```

إذا لم توجد خطوط مفقودة، فسترى فقط السطر النهائي “Document loaded successfully.”.

---

## الخلاصة

لقد أوضحنا للتو كيفية **اكتشاف استبدال الخط المفقود** في Java باستخدام Aspose.Words. من خلال تكوين `LoadOptions`، وإنشاء كائن `FontSettings`، وربط `IWarningCallback`، تحصل على رؤية كاملة لكل خط تستبدله المكتبة خلف الكواليس. هذه الطريقة لا تمنع الأخطاء الصامتة في العرض فحسب، بل تمنحك أيضًا نقطة ربط للتسجيل، والتنبيه، أو حتى تضمين خطوط بديلة تلقائيًا.

من هنا يمكنك:

- توسيع النداء العكسي لجمع التحذيرات في قائمة للردود عبر الـ API.  
- دمج هذه التقنية مع تكوينات **LoadOptions** لسيناريوهات أخرى (مثل تحميل موارد مخصصة).  
- استكشاف نظام **Aspose.Words for Java** الأوسع: التحويل إلى PDF، استخراج النص، أو تنفيذ دمج البريد (mail merge).

جرّبه، عدّل المسجل، ودع تطبيقاتك تُنبهك عندما يختفي خط. برمجة سعيدة!

## ما الذي ينبغي أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شفرة كاملة مع شروحات خطوة‑بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [التقاط تحذيرات استبدال الخط في Java باستخدام Aspose.Words – دليل كامل](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [استخدام خيارات وإعدادات المستند في Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}