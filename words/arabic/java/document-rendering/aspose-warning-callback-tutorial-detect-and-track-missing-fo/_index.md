---
category: general
date: 2026-03-17
description: تعلم درس استدعاء التحذير في Aspose لاكتشاف الخطوط المفقودة وتتبعها في
  مستندات Java مع مثال كامل قابل للتنفيذ.
draft: false
keywords:
- aspose warning callback tutorial
- detect missing fonts
- track missing fonts
language: ar
og_description: أتقن درس استدعاء التحذير في Aspose لاكتشاف الخطوط المفقودة وتتبعها
  في سير عمل معالجة المستندات في Java.
og_title: دليل استدعاء التحذير في Aspose – اكتشاف الخطوط المفقودة
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: دليل استدعاء التحذير في Aspose – اكتشاف وتتبع الخطوط المفقودة
url: /ar/java/document-rendering/aspose-warning-callback-tutorial-detect-and-track-missing-fo/
---

translate.

List items: translate.

"## Conclusion" translate.

Paragraph.

"Next, you might explore:" translate.

List items.

"Give it a spin, tweak the callbacks to suit your logging framework, and watch your document workflow become far more robust. Happy coding!" translate.

Now produce final content with shortcodes unchanged.

Let's craft Arabic translation.

Be careful with RTL: Arabic text left to right? We'll just write Arabic.

Proceed.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# aspose warning callback tutorial – اكتشاف وتتبع الخطوط المفقودة

هل تساءلت يوماً كيف **تكتشف الخطوط المفقودة** عند تحويل أو تعديل ملفات Word باستخدام Aspose.Words؟ لست وحدك. في العديد من المشاريع الواقعية، يمكن أن يتسبب خط واحد مفقود في حدوث تشوهات في التخطيط، وتحتاج إلى طريقة موثوقة **لتتبع الخطوط المفقودة** قبل أن تسبب لك مشاكل لاحقاً.  

الخبر السار؟ دليل **aspose warning callback tutorial** يوفّر لك نقطة ربط برمجية نظيفة تطبع تحذيرات استبدال الخطوط في لحظة حدوثها. في هذا الدليل سنستعرض إعداد الاستدعاء، تحميل المستند، ورؤية التحذيرات أثناء التنفيذ — كل ذلك باستخدام Java.

بنهاية هذا المقال ستتمكن من اكتشاف الخطوط المفقودة تلقائياً، تسجيلها، وتحديد ما إذا كنت ستدمج بديلاً أو تعدل ملفات المصدر. لا حاجة لأدوات خارجية.

## المتطلبات المسبقة

- **Java 8+** (الكود يُجمّع مع أي JDK حديث)
- **Aspose.Words for Java** الإصدار 23.10 أو أحدث – حمّله من بوابة Aspose أو أضف الاعتماد في Maven.
- عينة DOCX تُشير عمداً إلى خط غير مُثبت على جهازك (مثال: “Comic Sans MS” على نظام Linux).

هذا كل ما تحتاجه — لا مكتبات إضافية، ولا خطوات بناء معقدة.

## الخطوة 1: تسجيل استدعاء التحذير – جوهر دليل aspose warning callback tutorial

أول شيء يُعلّمه الدليل هو كيفية إرفاق مستمع تحذير. Aspose.Words يُطلق كائن `WarningInfo` لكل مشكلة يواجهها، وعلم `WarningSource.FONT_SUBSTITUTION` يُخبرنا بالضبط متى يتم استبدال خط.

```java
import com.aspose.words.*;

public class FontDiagnostics {
    public static void main(String[] args) throws Exception {

        // Step 1: Register a warning callback to capture font substitution warnings.
        Document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about font‑substitution events.
                if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution warning:");
                    System.out.println("  Original:   " + info.getDescription());
                    System.out.println("  Substituted:" + info.getAdditionalInfo());
                }
            }
        });
```

**لماذا هذا مهم:** بدون الاستدعاء، يقوم Aspose باستبدال الخطوط المفقودة بصمت، ولن تعرف أي الحروف قد تبدو غير صحيحة. عبر تسجيل التحذير، يمكنك **اكتشاف الخطوط المفقودة** مبكراً وتحديد ما إذا كنت ستدمج الخط الصحيح.

> **نصيحة احترافية:** إذا كنت بحاجة لتجميع التحذيرات لتقارير لاحقة، احفظها في `List<WarningInfo>` بدلاً من طباعتها مباشرة.

## الخطوة 2: تحميل المستند – حيث قد تُخفى الخطوط المفقودة

الآن نقوم بتحميل ملف DOCX الذي قد يشير إلى خطوط غير موجودة على الجهاز. عملية التحميل تُفعّل استدعاء التحذير إذا كان هناك أي خطوط مفقودة.

```java
        // Step 2: Load a document that may contain missing fonts.
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

**ما الذي يحدث خلف الكواليس؟** Aspose يحلل تعريفات الأنماط في المستند، يفحص كل مقطع نصي، ويتحقق من مستودع الخطوط في النظام. عندما لا يجد التطابق الدقيق، يلجأ إلى بديل ويُطلق التحذير الذي ربطناه للتو.

## الخطوة 3: حفظ المستند – تفريغ التحذيرات

أخيراً، نحفظ المستند. عملية الحفظ تُعيد تقييم الخطوط أيضاً، لذا أي تحذيرات لم تُصدر أثناء التحميل ستظهر الآن.

```java
        // Step 3: Save the document; any font substitution warnings will be printed by the callback.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

عند تشغيل البرنامج، ستظهر لك مخرجات في وحدة التحكم مشابهة لـ:

```
Font substitution warning:
  Original:   Font "Comic Sans MS" not found.
  Substituted: Using "Arial" as fallback.
```

تُثبت هذه المخرجات أن **aspose warning callback tutorial** يعمل، وقد نجحت في **اكتشاف الخطوط المفقودة** وتصبح الآن **تتبع الخطوط المفقودة** عبر السجل.

## كيفية اكتشاف الخطوط المفقودة في مستند Word – ما بعد الأساسيات

نهج الاستدعاء رائع للتنفيذ مرة واحدة، لكن أحياناً تحتاج إلى أداة قابلة لإعادة الاستخدام. إليك غلاف سريع يمكنك إدراجه في أي مشروع:

```java
public class FontMissingChecker {
    private final List<String> missingFonts = new ArrayList<>();

    public FontMissingChecker() {
        Document.setWarningCallback((WarningInfo info) -> {
            if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                missingFonts.add(info.getDescription());
            }
        });
    }

    public List<String> check(String path) throws Exception {
        new Document(path); // triggers warnings
        return missingFonts;
    }
}
```

استخدمه هكذا:

```java
FontMissingChecker checker = new FontMissingChecker();
List<String> fonts = checker.check("input.docx");
if (!fonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    fonts.forEach(System.out::println);
}
```

الآن لديك طريقة **detect missing fonts** قابلة لإعادة الاستخدام تُعيد قائمة يمكنك تمريرها إلى خط أنابيب CI أو واجهة مستخدم.

## تتبع الخطوط المفقودة باستخدام Aspose.Words – تقارير للفرق

في فريق أكبر، قد ترغب في إنتاج تقرير CSV لكل الخطوط المفقودة عبر مستندات متعددة. اجمع الأداة السابقة مع تكرار بسيط للملفات:

```java
import java.nio.file.*;
import java.io.*;

public class BulkFontReporter {
    public static void main(String[] args) throws Exception {
        Path folder = Paths.get("YOUR_DIRECTORY");
        try (BufferedWriter writer = Files.newBufferedWriter(folder.resolve("missing-fonts-report.csv"))) {
            writer.write("Document,Missing Font\n");
            Files.list(folder)
                 .filter(p -> p.toString().endsWith(".docx"))
                 .forEach(p -> {
                     try {
                         FontMissingChecker checker = new FontMissingChecker();
                         List<String> missing = checker.check(p.toString());
                         for (String msg : missing) {
                             // Extract font name from description
                             String font = msg.replaceAll("Font \"(.*?)\".*", "$1");
                             writer.write(p.getFileName() + "," + font + "\n");
                         }
                     } catch (Exception e) {
                         // In a real app, log the error
                     }
                 });
        }
        System.out.println("Report generated at missing-fonts-report.csv");
    }
}
```

تشغيل هذا السكريبت سيعطيك ملف CSV **track missing fonts** يمكن لكل مطور إلقاء نظرة عليه قبل رفع المستند إلى الإنتاج.

## المشكلات الشائعة وكيفية تجنّبها

| المشكلة | لماذا تحدث | الحل |
|---------|------------|------|
| **عدم تشغيل الاستدعاء** | نسيت ضبط الاستدعاء **قبل** تحميل المستند. | ضع `Document.setWarningCallback` في أعلى دالة `main`. |
| **ظهور التحذير الأول فقط** | Aspose يخزن التحذيرات لكل كائن `Document`. | استخدم كائن `Document` جديد لكل ملف، أو أعد ضبط الاستدعاء بين التشغيلات. |
| **اسم الخط غير صحيح في السجل** | الوصف يحتوي على نص إضافي (“Font … not found”). | احذف النص الزائد باستخدام regex كما هو موضح في مثال CSV. |
| **تأثير الأداء على دفعات كبيرة** | الاستدعاء يُنفّذ على كل مقطع نصي، مما قد يكون مكلفاً. | حدّد الفحص إلى خطوة ما قبل التنفيذ؛ تخطى الحفظ إذا كنت تحتاج فقط إلى الكشف. |

## النتائج المتوقعة والتحقق

1. **مخرجات وحدة التحكم** – يجب أن ترى على الأقل سطر “Font substitution warning” لكل خط مفقود.  
2. **تقرير CSV** – بعد انتهاء السكريبت الجماعي، افتح `missing-fonts-report.csv` وتأكد أن كل صف يُظهر اسم المستند والخط المفقود بدقة.  
3. **المستند المحفوظ** – ملف DOCX الناتج سيُظهر الخطوط البديلة، لكن قد يختلف التخطيط البصري عن الأصلي.

إذا لم يتصرف أي من هذه الخطوات كما هو موصوف، تحقق من أن ملف JAR الخاص بـ Aspose.Words موجود في مسار الـ classpath وأن `input.docx` فعلاً يشير إلى خط غير موجود على نظام التشغيل الخاص بك.

## الخاتمة

لقد أكملت للتو **aspose warning callback tutorial** الذي يوضح كيفية **detect missing fonts** و **track missing fonts** في تطبيقات Java. عبر تسجيل مستمع تحذير، تحميل المستند، وربما تصدير النتائج، تحصل على رؤية كاملة للمشكلات المتعلقة بالخطوط قبل أن تظهر في بيئة الإنتاج.

الخطوات التالية قد تشمل:

- دمج الخط المفقود مباشرة باستخدام `LoadOptions.setFontSubstitution`.
- استخدام فئة `FontSettings` لتعيين خطوط بديلة محددة للخطوط المفقودة.
- دمج تقرير CSV في خط أنابيب CI/CD لإيقاف البناء عندما تظهر خطوط غير موثقة.

جرّبه، عدّل الاستدعاءات لتتناسب مع إطار التسجيل الذي تستخدمه، وشاهد سير عمل المستندات يصبح أكثر صلابة. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}