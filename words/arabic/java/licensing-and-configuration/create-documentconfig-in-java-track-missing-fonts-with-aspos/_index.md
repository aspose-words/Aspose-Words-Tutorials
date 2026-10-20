---
category: general
date: 2026-07-06
description: إنشاء DocumentConfig في جافا لتتبع الخطوط المفقودة باستخدام Aspose.Words
  – دليل كامل خطوة بخطوة للمطورين.
draft: false
keywords:
- create documentconfig
- track missing fonts
language: ar
og_description: إنشاء DocumentConfig في Java لتتبع الخطوط المفقودة باستخدام Aspose.Words.
  تعلّم سير العمل الكامل، من الإعداد إلى معالجة التحذيرات.
og_title: إنشاء DocumentConfig في Java – تتبع الخطوط المفقودة
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Create DocumentConfig in Java to track missing fonts using Aspose.Words
    – a complete, step‑by‑step guide for developers.
  headline: Create DocumentConfig in Java – Track Missing Fonts with Aspose.Words
  type: TechArticle
- description: Create DocumentConfig in Java to track missing fonts using Aspose.Words
    – a complete, step‑by‑step guide for developers.
  name: Create DocumentConfig in Java – Track Missing Fonts with Aspose.Words
  steps:
  - name: Prerequisites
    text: '| Requirement | Reason | |-------------|--------| | Java 8 or newer | Aspose.Words
      for Java supports JDK 8+. | | Aspose.Words for Java library (latest version)
      | Provides `DocumentConfig`, `IWarningCallback`, etc. | | An IDE or build tool
      (IntelliJ, Eclipse, Maven/Gradle) | To compile and run the sa'
  - name: Maven
    text: '```xml <dependency> <groupId>com.aspose</groupId> <artifactId>aspose-words</artifactId>
      <version>23.12</version> <!-- use the latest version --> </dependency> ```'
  - name: Gradle (Kotlin DSL)
    text: '```kotlin implementation("com.aspose:aspose-words:23.12") ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Font Substitution
title: إنشاء DocumentConfig في Java – تتبع الخطوط المفقودة باستخدام Aspose.Words
url: /ar/java/licensing-and-configuration/create-documentconfig-in-java-track-missing-fonts-with-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء DocumentConfig في Java – تتبع الخطوط المفقودة باستخدام Aspose.Words

**Create DocumentConfig in Java** لمراقبة تحذيرات استبدال الخطوط عند تحميل مستند Word. هل تساءلت يومًا لماذا تبدو بعض الأحرف غريبة بعد فتح ملف DOCX؟ من المحتمل أن الخط الأصلي غير موجود على الجهاز، وأن Aspose.Words يستبدله بصمت. في هذا الدرس سنوضح لك بالضبط كيفية **تتبع الخطوط المفقودة** حتى لا تتفاجأ بحرف غريب مرة أخرى.

سنستعرض كل ما تحتاجه: إعداد Maven/Gradle، الكود الذي ينشئ `DocumentConfig`، `IWarningCallback` مخصص يفلتر فقط تنبيهات استبدال الخطوط، وطريقة سريعة لتسجيل تلك الرسائل. في النهاية ستحصل على مثال قابل للتنفيذ يطبع كل تحذير خط مفقود إلى وحدة التحكم (أو إلى ملف إذا فضلت).

---

## ما ستتعلمه

- لماذا يعتبر `DocumentConfig` المكان المناسب لاعتراض أحداث استبدال الخطوط.  
- كيفية **تتبع الخطوط المفقودة** دون إغراق سجلاتك بتحذيرات غير ذات صلة.  
- برنامج Java كامل وجاهز للنسخ واللصق يوضح التقنية.  
- نصائح لتوسيع الحل—مثل كتابة التحذيرات إلى قاعدة بيانات أو إرسال تنبيهات بريد إلكتروني.

### المتطلبات المسبقة

| المتطلب | السبب |
|-------------|--------|
| Java 8 أو أحدث | Aspose.Words for Java يدعم JDK 8+. |
| مكتبة Aspose.Words for Java (أحدث نسخة) | توفر `DocumentConfig`، `IWarningCallback`، إلخ. |
| بيئة تطوير متكاملة أو أداة بناء (IntelliJ, Eclipse, Maven/Gradle) | لتجميع وتشغيل العينة. |
| ملف DOCX يحتوي على خطوط غير مثبتة على جهازك | لرؤية التحذير أثناء التنفيذ. |

إذا كان لديك مشروع بالفعل، فقط أضف تبعية Aspose وستكون جاهزًا للبدء.

---

## الخطوة 1: إضافة Aspose.Words إلى مشروعك

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- use the latest version -->
</dependency>
```

### Gradle (Kotlin DSL)

```kotlin
implementation("com.aspose:aspose-words:23.12")
```

> **نصيحة احترافية:** نسخة التجربة المجانية تعمل بشكل ممتاز للاختبار، لكن تذكر تطبيق ترخيص للإنتاج لإزالة علامة التقييم.

---

## الخطوة 2: إنشاء DocumentConfig وتسجيل Callback للتحذيرات

جوهر الحل يكمن في هذا المقتطف. نحن **ننشئ DocumentConfig**، نرفق `IWarningCallback` مخصص، ونخبره بـ **تتبع الخطوط المفقودة** فقط.

```java
import com.aspose.words.*;

public class FontSubstitutionDiagnostics {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a configuration object.
        DocumentConfig config = new DocumentConfig();

        // 2️⃣ Attach a warning callback that reacts only to font‑substitution warnings.
        config.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // 3️⃣ Filter for FONT_SUBSTITUTION type.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // 4️⃣ This is where we **track missing fonts**.
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // 5️⃣ Load the document using the configuration we just prepared.
        Document doc = new Document("YOUR_DIRECTORY/input.docx", config);

        // Optional: do something with the document, e.g., save as PDF.
        // doc.save("output.pdf");
    }
}
```

**لماذا يعمل هذا:** عندما يقوم Aspose.Words بتحليل مستند، ينتج كائنات `WarningInfo` لأي شذوذ. من خلال توفير callback، يمكنك اعتراض تلك التحذيرات *قبل* أن تختفي في الفراغ. شرط `if` يضمن أننا نتتبع فقط **الخطوط المفقودة**، متجاهلين التحذيرات الأخرى مثل العلامات المهجورة أو الميزات غير المدعومة.

---

## الخطوة 3: تشغيل المثال وملاحظة النتيجة

ضع ملف DOCX يشير إلى خط غير موجود لديك (مثلاً “Comic Sans MS” على نظام Linux). نفّذ البرنامج:

```bash
$ javac -cp "aspose-words-23.12.jar" FontSubstitutionDiagnostics.java
$ java -cp ".:aspose-words-23.12.jar" FontSubstitutionDiagnostics
```

سترى شيئًا مشابهًا لـ:

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

كل سطر يطابق خطًا مفقودًا استبدله Aspose تلقائيًا. إذا لم توجد خطوط مفقودة، يبقى البرنامج صامتًا—وهو ما تريد لسجل نظيف.

---

## الخطوة 4: حفظ قائمة الخطوط المفقودة (اختياري)

الطباعة إلى وحدة التحكم مفيدة للعرض، لكن في خدمة واقعية قد تحتاج لتخزين البيانات. إليك طريقة سريعة لكتابة التحذيرات إلى ملف نصي.

```java
import java.io.FileWriter;
import java.io.IOException;

public class FontSubstitutionDiagnostics {

    private static final String LOG_PATH = "missing-fonts.log";

    public static void main(String[] args) throws Exception {
        DocumentConfig config = new DocumentConfig();

        config.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) throws IOException {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substituted: " + info.getDescription();
                    System.out.println(message);
                    try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                        fw.write(message + System.lineSeparator());
                    }
                }
            }
        });

        Document doc = new Document("YOUR_DIRECTORY/input.docx", config);
    }
}
```

الآن كل حدث خط مفقود يضيف سطرًا إلى `missing-fonts.log`. يمكنك لاحقًا تحليل هذا الملف، ربطه بلوحة مراقبة، أو حتى تشغيل تنبيه إذا اختفى خط حاسم من الخادم.

---

## الخطوة 5: الأخطاء الشائعة وكيفية تجنبها

| العَرَض | السبب المحتمل | الحل |
|---------|--------------|-----|
| لا تظهر تحذيرات رغم أن DOCX يستخدم خطوطًا غير معروفة | لم يتم تسجيل الـ Callback أو تم استدعاء `setWarningCallback` بعد تحميل المستند | تأكد من تنفيذ `config.setWarningCallback(...)` **قبل** إنشاء كائن `Document`. |
| تعطل التطبيق بـ `NullPointerException` | `info.getDescription()` قد تُعيد `null` لبعض أنواع التحذيرات النادرة | احمِ من الـ null: `String desc = info.getDescription(); if (desc != null) …` |
| تدفق تحذيرات غير ذات صلة يملأ وحدة التحكم | هل الـ Callback يفلتر فقط `FONT_SUBSTITUTION`؟ | راجع شرط `if (info.getWarningType() == WarningType.FONT_SUBSTITUTION)`. |
| بطء الأداء عند معالجة دفعات كبيرة | كتابة إلى ملف بشكل متزامن لكل تحذير | اجمع الكتابات أو استخدم `BufferedWriter` لتقليل حمل الإدخال/الإخراج. |

---

## الخطوة 6: توسيع الحل – من وحدة التحكم إلى بيئة المؤسسة

- **تسجيل إلى قاعدة البيانات:** استبدل `FileWriter` بعملية إدراج JDBC؛ احفظ `documentName`، `missingFont`، و`timestamp`.  
- **تنبيهات بريد إلكتروني:** اربط بـ JavaMail؛ أرسل ملخصًا بعد معالجة دفعة من المستندات.  
- **منطق استبدال مخصص:** بدلاً من ترك Aspose يختار بديلًا، يمكنك تحميل مجموعة خطوط محلية عبر `FontSettings.setFontsFolder()` وإعادة تحميل المستند إذا حدث استبدال.

هذه الامتدادات تحافظ على الفكرة الأساسية—**إنشاء DocumentConfig** و**تتبع الخطوط المفقودة**—مع القدرة على التوسع لتلبية احتياجات الإنتاج.

---

## الخاتمة

أصبح لديك الآن نمط ثابت وجاهز للنسخ واللصق **لإنشاء DocumentConfig** في Java واستخدامه **لتتبع الخطوط المفقودة** مع Aspose.Words. النهج خفيف الوزن، يتطلب بضع أسطر من الكود فقط، ويمنحك تحكمًا كاملًا في طريقة معالجة تحذيرات استبدال الخطوط. سواء كنت تبني خدمة تحويل مستندات، مولد تقارير آلي، أو أداة تدقيق امتثال، فإن معرفة الخطوط المفقودة بدقة يمكن أن توفر ساعات من التصحيح.

ما الخطوة التالية؟ جرّب استبدال إخراج وحدة التحكم بسجل JSON منظم، أو دمج الـ callback في خدمة microservice بـ Spring Boot تعالج التحميلات في الوقت الفعلي. وإذا صادفت حالات خاصة—مثل خط OpenType مخصص لا يستطيع Aspose تحليله—اترك تعليقًا أدناه؛ سنحل المشكلة معًا.

برمجة سعيدة، ولتظهر ملفات PDF دائمًا بالخطوط التي تتوقعها!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [استخدام الخطوط في Aspose.Words for Java](/words/english/java/using-document-elements/using-fonts/)
- [تخصيص ألوان السمات والخطوط في Aspose.Words Java: دليل شامل](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [كيفية إنشاء مستندات PDF باستخدام Aspose.Words for Java | واجهة برمجة معالجة المستندات](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}