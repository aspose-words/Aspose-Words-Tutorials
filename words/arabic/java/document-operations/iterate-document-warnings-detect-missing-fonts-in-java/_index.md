---
category: general
date: 2026-04-28
description: تكرار تحذيرات المستند في ملف Word لاكتشاف الخطوط المفقودة، استرجاع أسماء
  الخطوط المفقودة وطباعة تفاصيل الخطوط المفقودة باستخدام Aspose.Words للغة Java.
draft: false
keywords:
- iterate document warnings
- detect missing fonts
- load word document
- retrieve missing font
- print missing font
language: ar
og_description: تكرار تحذيرات المستند للعثور على الخطوط المفقودة، استرجاع أسماء الخطوط
  المفقودة، وطباعة تفاصيل الخطوط المفقودة مع مثال Java كامل.
og_title: 'تكرار تحذيرات المستند: اكتشاف الخطوط المفقودة في جافا'
tags:
- Aspose.Words
- Java
- Document Processing
title: 'تكرار تحذيرات المستند: اكتشاف الخطوط المفقودة في جافا'
url: /ar/java/document-operations/iterate-document-warnings-detect-missing-fonts-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تكرار تحذيرات المستند – اكتشاف الخطوط المفقودة في Java

في أي مرة احتجت إلى **تكرار تحذيرات المستند** عند فتح ملف Word وتساءلت عن الخطوط المفقودة؟ لست وحدك. يمكن أن تتسبب الخطوط المفقودة في تشويه مظهر التقرير، وبدون وسيلة لاكتشافها قد تقوم بإرسال مستند لا يشبه الأصل على الإطلاق.  

في هذا الدرس سنوضح لك كيفية **اكتشاف الخطوط المفقودة** عن طريق تحميل مستند Word، وتكرار تحذيراته، واسترجاع أسماء الخطوط المفقودة، وأخيرًا طباعة معلومات الخطوط المفقودة — كل ذلك باستخدام Aspose.Words for Java.  

سنغطي كل شيء من أول سطر كود حتى مخرجات وحدة التحكم المتوقعة، بحيث يمكنك نسخ‑لصق حل يعمل في مشروعك الآن. لا حاجة لأي مستندات إضافية.

## المتطلبات المسبقة

- Java 8 أو أحدث مثبت.
- مكتبة Aspose.Words for Java (أحدث نسخة حتى 2026‑04‑28).
- ملف Word قد يحتوي على خطوط غير مثبتة على جهازك (مثال: `doc-with-missing-font.docx`).

إذا كان لديك هذه المتطلبات بالفعل، رائع — أنت جاهز **لتحميل مستند word** والبدء في التكرار.

## الخطوة 1 – تحميل مستند Word باستخدام الخيارات الافتراضية

قبل أن نتمكن من **تكرار تحذيرات المستند**، يجب تحميل الملف إلى الذاكرة. تتيح لك Aspose.Words القيام بذلك باستدعاء مُنشئ واحد. عادةً ما تكون `LoadOptions` الافتراضية كافية، لكننا سنظهر إنشاء صريح للتوضيح.

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {

        // Step 1: Prepare load options (default settings are fine for this example)
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/doc-with-missing-font.docx", loadOptions);
```

> **لماذا هذا مهم:**  
> تحميل المستند يُفعل Aspose.Words لفحص الملف بحثًا عن أي موارد لا يمكنه حلها، مثل الخطوط غير المثبتة محليًا. تُخزن هذه المشكلات كـ **تحذيرات**، والتي سنقوم **بتكرار تحذيرات المستند** عليها في الخطوة التالية.

## الخطوة 2 – تكرار تحذيرات المستند للعثور على مشاكل الخطوط

الآن يأتي جوهر الحل: نمر عبر كل تحذير جمعته المكتبة أثناء التحميل. كائنات `WarningInfo` تخبرنا بما حدث خطأ، ويمكننا تصفية `FontSubstitutionWarning` لـ **اكتشاف الخطوط المفقودة**.

```java
        // Step 3: Iterate over all warnings generated during loading
        for (WarningInfo warningInfo : document.getWarnings()) {
            // Step 4: Identify font substitution warnings
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;

                // Step 5: Output the missing font name and the font that was used as a substitute
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }
    }
}
```

> **نصيحة احترافية:** فحص `instanceof` يضمن أننا نتعامل فقط مع التحذيرات المتعلقة بالخطوط، متجاهلين غيرها مثل مشاكل تحميل الصور. هذا يجعل الحلقة فعّالة ويحافظ على تركيز المخرجات على الخطوط التي تحتاج فعلاً إلى **استرجاع معلومات الخط المفقود** لها.

### مخرجات وحدة التحكم المتوقعة

```
Missing font: Arial Black
Substituted with: Liberation Sans
Missing font: Calibri
Substituted with: Liberation Sans
```

إذا لم يحتوي المستند على خطوط مفقودة، تنتهي الحلقة بصمت — لا شيء لـ **طباعة الخط المفقود**.

## الخطوة 3 – لماذا لا نكتفي بالتقاط استثناء؟

قد تتساءل، “لماذا لا أُغلف استدعاء `new Document(...)` بكتلة try‑catch وأبحث عن استثناء؟” الجواب ذو جانبين:

1. **معلومات تفصيلية:** الاستثناءات تخبرك فقط أن شيئًا ما فشل. التحذيرات تعطيك اسم الخط الدقيق والبديل الذي اختارته Aspose.Words.
2. **مشكلات غير قاتلة:** عادةً ما تكون الخطوط المفقودة غير قاتلة؛ يظل المستند يُحمَّل، لكن الدقة البصرية تتأثر. من خلال **تكرار تحذيرات المستند**، تحتفظ بالقدرة على معالجة باقي الملف.

## الخطوة 4 – توسيع المثال: جمع الخطوط المفقودة في قائمة

أحيانًا تحتاج إلى الخطوط المفقودة لمعالجة إضافية — ربما لتضمينها أو لتنبيه المستخدم عبر واجهة المستخدم. إليك تعديل سريع يجمع الأسماء في `Set<String>`.

```java
        // Collect missing fonts for later use
        Set<String> missingFonts = new HashSet<>();

        for (WarningInfo warningInfo : document.getWarnings()) {
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;
                missingFonts.add(fontWarning.getMissingFontName());

                // Still print for immediate feedback
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }

        // Example of using the collected data
        System.out.println("Total missing fonts: " + missingFonts.size());
```

الآن لديك طريقة نظيفة لـ **استرجاع الخط المفقود** برمجيًا، يمكنك تمريرها إلى وحدة تقارير أو معالج تثبيت الخطوط.

## الخطوة 5 – اعتبارات واقعية

- **استبدالات متعددة:** يمكن استبدال خط مفقود واحد بخطوط مختلفة في أجزاء مختلفة من المستند. ستحتوي قائمة التحذيرات على كل حدوث، لذا قد ترى إدخالات مكررة للخط المفقود.
- **الأداء:** تحميل مستندات ضخمة قد يولد آلاف التحذيرات. إذا كنت تهتم بالخطوط فقط، قم بالتصفية مبكرًا كما هو موضح للحفاظ على سرعة الحلقة.
- **خطوط متعددة المنصات:** على Linux، يكون الخط البديل الافتراضي غالبًا *Liberation Sans*. على Windows، قد يكون *Arial*. معرفة البديل يساعدك على اتخاذ قرار ما إذا كنت بحاجة إلى تضمين خطوط مخصصة مع تطبيقك.

## الخطوة 6 – مساعدة بصرية

في الأسفل لقطة شاشة لمخرجات وحدة التحكم (نص alt يتضمن الكلمة المفتاحية الأساسية لتحسين محركات البحث).

![مخرجات وحدة التحكم لتكرار تحذيرات المستند تُظهر الخطوط المفقودة والبدائل](/images/iterate-document-warnings.png)

*نص alt:* *مثال على تكرار تحذيرات المستند يعرض أسماء الخطوط المفقودة وتفاصيل الاستبدال.*

## الخلاصة

لقد تعلمت الآن كيفية **تكرار تحذيرات المستند** في Aspose.Words for Java، **اكتشاف الخطوط المفقودة**، **تحميل مستند word** بأمان، **استرجاع معلومات الخط المفقود**، و**طباعة تفاصيل الخط المفقود** إلى وحدة التحكم. يعمل مقتطف الكود الكامل كما هو، ويمكنك تكييفه لتسجيله في ملف، أو عرض حوار واجهة مستخدم، أو حتى تضمين الخطوط المفقودة تلقائيًا.

بعد ذلك، قد ترغب في استكشاف كيفية **تحميل مستند word** بمصادر خطوط مخصصة (مثلاً إضافة مجلد يحتوي على خطوط الشركة) أو كيفية تضمين الخطوط المفقودة مباشرةً في الملف للحفاظ على التخطيط عبر الأجهزة. كلا الموضوعين يبنيان بشكل طبيعي على ما غطيناه هنا.

برمجة سعيدة، ولتظل ملفات PDF الخاصة بك دائمًا تبدو كما تريد بالضبط!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}