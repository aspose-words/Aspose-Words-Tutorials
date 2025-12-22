---
category: general
date: 2025-12-22
description: تحميل مستند Word في Java وتعلم كيفية الحصول على رسائل التحذير، خاصةً
  التعامل مع الخطوط المفقودة. يغطي هذا الدليل خطوة بخطوة التحذيرات، استبدال الخطوط،
  وأفضل الممارسات.
draft: false
keywords:
- load word document
- get warning messages
- handle missing fonts
- Aspose.Words warnings
- font substitution warning
language: ar
og_description: تحميل مستند Word في Java واسترجاع رسائل التحذير فورًا. تعلم كيفية
  التعامل مع الخطوط المفقودة بأمثلة عملية على الكود.
og_title: تحميل مستند Word في Java – الحصول على التحذيرات وإدارة الخطوط المفقودة
tags:
- Java
- Aspose.Words
- Document Processing
title: تحميل مستند Word في Java – دليل كامل للحصول على رسائل التحذير ومعالجة الخطوط
  المفقودة
url: /ar/java/document-loading-and-saving/load-word-document-in-java-complete-guide-to-get-warning-mes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تحميل مستند Word في Java – دليل كامل للحصول على رسائل التحذير ومعالجة الخطوط المفقودة

هل احتجت يومًا إلى **تحميل مستند Word في Java** وتساءلت لماذا تختفي بعض الخطوط أو لماذا تستمر في رؤية تحذيرات غامضة؟ لست وحدك. في العديد من المشاريع، خاصة عندما تنتقل المستندات بين الأجهزة، تتسبب الخطوط المفقودة في ظهور رسائل `FontSubstitutionWarning` التي يمكن أن تُخل بتوقعات التخطيط.  

في هذا الدرس سنُظهر لك **كيفية تحميل مستند Word**، **استرجاع رسائل التحذير**، و**معالجة الخطوط المفقودة** بسلاسة. في النهاية ستحصل على مقتطف جاهز للتنفيذ يطبع كل تحذير، لتتمكن من اتخاذ قرار ما إذا كنت ستدمج الخطوط، تستبدلها، أو تسجل المشكلة للمراجعة لاحقًا.

> **ما ستتعلمه**
> - الكود الدقيق اللازم **لتحميل مستند Word** باستخدام Aspose.Words for Java.  
> - كيفية التكرار على `document.getWarnings()` وتصفية `FontSubstitutionWarning`.  
> - نصائح للتعامل مع الخطوط المفقودة، بما في ذلك دمج الخطوط أو توفير بدائل.  

## المتطلبات المسبقة

- تثبيت Java 8 أو أحدث.  
- Maven (أو Gradle) لإدارة التبعيات.  
- مكتبة Aspose.Words for Java (الإصدار التجريبي المجاني يكفي لهذا العرض).  

إذا لم تقم بعد بإضافة Aspose.Words إلى مشروعك، أضف تبعية Maven التالية:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Check for the latest version -->
</dependency>
```

*(يمكنك أيضًا استخدام ما يعادلها في Gradle – الواجهة البرمجية (API) هي نفسها.)*  

## الخطوة 1: إعداد Load Options – نقطة الانطلاق لتحميل مستند Word

قبل أن تقوم فعليًا **بتحميل مستند Word**، قد ترغب في تعديل كيفية تعامل المكتبة مع الموارد المفقودة. `LoadOptions` يمنحك التحكم في استبدال الخطوط، تحميل الصور، وأكثر.

```java
import com.aspose.words.*;

public class LoadDocumentDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Prepare load options (default options are fine for most cases)
        LoadOptions loadOptions = new LoadOptions();

        // Optional: Force the library to use a specific font folder
        // loadOptions.setFontSettings(new FontSettings());
        // loadOptions.getFontSettings().setFontsFolder("C:/MyFonts", true);
```

> **لماذا هذا مهم:**  
> باستخدام `LoadOptions` تضمن أنه عندما تواجه عملية **تحميل مستند Word** خطًا مفقودًا، تعرف المكتبة أين تبحث عن بدائل. إذا تخطيت هذه الخطوة، قد تحصل على سيل من رسائل `FontSubstitutionWarning` غير متوقعة.

## الخطوة 2: تحميل مستند Word باستخدام الخيارات المحددة

الآن نقوم فعليًا **بتحميل مستند Word** من القرص. المُنشئ يأخذ مسار الملف و`LoadOptions` التي قمنا بإعدادها للتو.

```java
        // Step 2: Load the Word document with the specified options
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

> **نصيحة:**  
> إذا كان الملف مدمجًا داخل JAR أو يأتي من تدفق شبكة، استخدم نسخة `InputStream` من مُنشئ `Document`. منطق معالجة التحذيرات يبقى كما هو.

## الخطوة 3: استرجاع وتصفية رسائل التحذير – التركيز على الخطوط المفقودة

Aspose.Words يخزن أي مشكلات يواجهها أثناء التحميل في `WarningInfoCollection`. سنقوم بالتكرار عبرها، نبحث عن `FontSubstitutionWarning`، ونطبع كل رسالة.

```java
        // Step 3: Retrieve any warnings generated during loading
        for (WarningInfo warning : document.getWarnings()) {
            // Step 4: Identify font substitution warnings and display their messages
            if (warning instanceof FontSubstitutionWarning) {
                System.out.println("[Font Warning] " + warning.getMessage());
            } else {
                // Optionally handle other warning types
                System.out.println("[Other Warning] " + warning.getMessage());
            }
        }
    }
}
```

**الإخراج المتوقع (مثال):**

```
[Font Warning] Font 'Calibri' not found. Substituted with 'Arial'.
[Font Warning] Font 'Times New Roman' not found. Substituted with 'Liberation Serif'.
```

الآن لديك نظرة واضحة على **استرجاع رسائل التحذير** المتعلقة بالخطوط المفقودة، ويمكنك اتخاذ القرار المناسب للخطوة التالية.

## الخطوة 4: معالجة الخطوط المفقودة – استراتيجيات عملية

رؤية تحذيرات الخط مفيدة، لكن من المحتمل أنك تريد **معالجة الخطوط المفقودة** حتى يظهر المستند النهائي كما قصده المؤلف تمامًا.

### 4.1 دمج الخطوط مباشرةً في المستند

إذا كنت تتحكم في ملف `.docx` الأصلي، فعّل دمج الخطوط عند الحفظ:

```java
FontSettings fontSettings = new FontSettings();
fontSettings.setEmbedTrueTypeFonts(true);
document.setFontSettings(fontSettings);
document.save("output.docx");
```

> **النتيجة:** الملف `output.docx` الناتج يحمل الخطوط المطلوبة، مما يلغي معظم تحذيرات الاستبدال على الأجهزة اللاحقة.

###4.2 توفير مجلد خطوط مخصص

إذا كان دمج الخطوط غير ممكن (مثلاً بسبب قيود الترخيص)، وجه Aspose.Words إلى مجلد يحتوي على الخطوط المفقودة:

```java
FontSettings fontSettings = new FontSettings();
fontSettings.setFontsFolder("C:/SharedFonts", true); // true = scan subfolders
loadOptions.setFontSettings(fontSettings);
```

الآن عندما **تحمّل مستند Word**، ستجد المكتبة الخطوط المفقودة وتوقف إصدار التحذيرات.

### 4.3 تسجيل التحذيرات للمراجعة

في بيئة الإنتاج، قد ترغب في التقاط التحذيرات في ملف سجل بدلاً من طباعتها على وحدة التحكم:

```java
import java.io.FileWriter;
import java.io.PrintWriter;

PrintWriter logger = new PrintWriter(new FileWriter("load-warnings.log", true));
for (WarningInfo warning : document.getWarnings()) {
    logger.println("[Warning] " + warning.getMessage());
}
logger.close();
```

هذا النهج يفي بمتطلبات الامتثال حيث يجب عليك إثبات أن الخطوط المفقودة تم اكتشافها ومعالجتها.

## الخطوة 5: مثال كامل يعمل – كل الأجزاء معًا

فيما يلي الفئة الكاملة الجاهزة للتنفيذ التي توضح **تحميل مستند Word**، **استرجاع رسائل التحذير**، و**معالجة الخطوط المفقودة** باستخدام مجلد خطوط مخصص.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.PrintWriter;

public class WordLoadWithWarnings {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Prepare load options
        LoadOptions loadOptions = new LoadOptions();

        // 👉 Optional: point to a custom font folder
        FontSettings fontSettings = new FontSettings();
        fontSettings.setFontsFolder("C:/SharedFonts", true);
        loadOptions.setFontSettings(fontSettings);

        // 2️⃣ Load the document
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // 3️⃣ Open a log file for warning capture
        PrintWriter logger = new PrintWriter(new FileWriter("load-warnings.log", true));

        // 4️⃣ Iterate through warnings
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                System.out.println("[Font Warning] " + warning.getMessage());
                logger.println("[Font Warning] " + warning.getMessage());
            } else {
                System.out.println("[Other Warning] " + warning.getMessage());
                logger.println("[Other Warning] " + warning.getMessage());
            }
        }

        // 5️⃣ (Optional) Save with embedded fonts
        FontSettings embedSettings = new FontSettings();
        embedSettings.setEmbedTrueTypeFonts(true);
        doc.setFontSettings(embedSettings);
        doc.save("output-with-embedded-fonts.docx");

        logger.close();
    }
}
```

**ما يفعله هذا المثال:**
1. يضبط `LoadOptions` ويوجه المحرك إلى مجلد يحتوي على الخطوط المفقودة.  
2. **يحمّل مستند Word** مع جمع أي تحذيرات.  
3. يطبع ويسجل كل تحذير، مع التركيز على `FontSubstitutionWarning`.  
4. يحفظ نسخة جديدة مع دمج الخطوط، مما يلغي التحذيرات المستقبلية.  

## الأسئلة المتكررة (FAQ)

**س: هل يعمل هذا مع ملفات `.doc` القديمة؟**  
ج: نعم. Aspose.Words يدعم كلًا من `.doc` و`.docx`. منطق معالجة التحذيرات هو نفسه.

**س: ماذا لو لم أستطع دمج الخطوط بسبب الترخيص؟**  
ج: استخدم نهج مجلد الخطوط المخصص (الخطوة 4.2). يحترم هذا الترخيص مع الحفاظ على الدقة البصرية التي تحتاجها.

**س: هل سيؤثر جمع التحذيرات على الأداء؟**  
ج: تأثيره ضئيل. تُخزن التحذيرات في مجموعة خفيفة الوزن. إذا كان لديك آلاف المستندات، يمكنك تعطيل التحذيرات في `LoadOptions` (`loadOptions.setWarningCallback(null)`) لكنك ستفقد القدرة على **استرجاع رسائل التحذير**.

## الخلاصة

لقد استعرضنا كل خطوة مطلوبة **لتحميل مستند Word** في Java، **استرجاع رسائل التحذير**، و**معالجة الخطوط المفقودة** بفعالية. من خلال تكوين `LoadOptions`، التكرار على `document.getWarnings()`، وتطبيق إما دمج الخطوط أو مجلد خطوط مخصص، ستحصل على سيطرة كاملة على تأثير الخطوط المفقودة على الناتج.

الآن يمكنك معالجة ملفات Word بثقة في أي تطبيق Java—سواء كان خدمة تحويل دفعي، عارض مستندات، أو مولد تقارير من جانب الخادم. الخطوة التالية قد تكون استكشاف **كيفية استبدال الخطوط المفقودة برمجيًا** أو **تحويل المستند إلى PDF مع الحفاظ على التخطيط**. السماء هي الحد.

*برمجة سعيدة، ولتظل مستنداتك دائمًا تحتفظ بجميع خطوطها!*  

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}