---
category: general
date: 2026-05-30
description: تسجيل رد نداء التحذير في Java لتتبع الخطوط المفقودة وتخصيص تحميل المستند
  باستخدام Aspose.Words. تعلّم الحل الكامل خطوة بخطوة.
draft: false
keywords:
- register warning callback
- track missing fonts
- customize document loading
language: ar
og_description: تسجيل رد التحذير في Java لتتبع الخطوط المفقودة وتخصيص تحميل المستند.
  دليل كامل مع الشيفرة والتفسيرات.
og_title: تسجيل رد نداء التحذير في جافا – تتبع الخطوط المفقودة
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  headline: Register warning callback in Java – Track missing fonts
  type: TechArticle
- description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  name: Register warning callback in Java – Track missing fonts
  steps:
  - name: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
    text: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
  - name: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
    text: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
  - name: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
    text: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
  type: HowTo
- questions:
  - answer: It’s the interface Aspose.Words uses for all warning types, giving you
      a single entry point for many possible issues.
    question: Why `IWarningCallback`?
  - answer: Aspose.Words only allows one warning handler. If you need to log to both
      a file and the console, implement a composite callback that forwards the warning
      to multiple destinations.
    question: Multiple callbacks?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Font handling
title: تسجيل رد النداء للتحذير في جافا – تتبع الخطوط المفقودة
url: /ar/java/document-loading-and-saving/register-warning-callback-in-java-track-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تسجيل رد النداء التحذيري في Java – تتبع الخطوط المفقودة

هل تساءلت يومًا كيف **تتبع الخطوط المفقودة** عند تحميل مستند Word باستخدام Aspose.Words for Java؟ ربما رأيت تلك الاستبدالات الصامتة للخطوط وفكرت، “ماذا حدث لتنسيقي؟” الخبر السار هو أنك لست بحاجة للتخمين. من خلال **تسجيل رد النداء التحذيري**، يمكنك التقاط كل حدث استبدال خط في اللحظة التي يُقرأ فيها المستند، ويمكنك أيضًا **تخصيص تحميل المستند** ليناسب خط أنابيبك.

في هذا الدرس سنستعرض مثالًا عمليًا يوضح بالضبط كيفية إعداد رد النداء، ولماذا هو مهم، وكيفية الحفاظ على نظافة بقية خط أنابيب المعالجة. في النهاية ستحصل على فئة Java جاهزة للتنفيذ تطبع كل تحذير بخصوص الخط المفقود وت保存 نسخة معالجة من المستند. لا حاجة لمراجع خارجية—فقط كود صافي وقابل للتنفيذ.

> **ما ستحصل عليه:**  
> • برنامج Java كامل يستخدم Aspose.Words  
> • شروحات خطوة بخطوة لكل سطر  
> • نصائح للتعامل مع الحالات الخاصة مثل الملفات المشفرة أو الدفعات الكبيرة  
> • فحص سريع يمكنك تشغيله على أي ملف `.docx`

## المتطلبات المسبقة

- **Java 17** (أو أي JDK حديث) مثبت ومُعَّرّ `JAVA_HOME`.  
- **Aspose.Words for Java** JAR في مسار الفئات الخاص بك. يمكنك الحصول على أحدث نسخة من مستودع Maven Central:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- replace with the newest -->
</dependency>
```

- مستند Word تجريبي (`input.docx`) تعتقد أنه يحتوي على خطوط غير مثبتة على جهازك.  
- بيئة تطوير متكاملة (IDE) أو أداة بناء سطر الأوامر (Maven/Gradle) التي ترتاح لاستخدامها.

هذا كل شيء. لا خطوط إضافية، لا خدمات إضافية—فقط Java عادي و Aspose.Words.

## لماذا تسجيل رد النداء التحذيري؟

تخيل **رد النداء التحذيري** ككاميرا أمان لعملية تحميل المستند. عندما تواجه Aspose.Words حرفًا مفقودًا، لا تُطلق استثناءً؛ بل تستبدله بهدوء بخط احتياطي. هذا الاستبدال الصامت قد يفسد تنسيقك، خاصةً في ملفات PDF أو الفواتير التي تعتمد على العلامة التجارية. من خلال تسجيل رد النداء يمكنك:

1. **الحصول على رؤى فورية** – كل تحذير `FONT_SUBSTITUTION` يُرسل فورًا.  
2. **التسجيل أو الرد** – يمكنك تسجيله في ملف، رفع تنبيه، أو حتى استبدال الخط برمجيًا.  
3. **الحفاظ على مخرجات نظيفة** – معرفة الخطوط المفقودة تمكنك من إصلاح المستند الأصلي قبل النشر.

باختصار، يحول رد النداء مشكلة مخفية إلى مشكلة مرئية، مما يجعل خط أنابيب المستندات أكثر موثوقية.

## الخطوة 1 – إنشاء `LoadOptions` لتخصيص طريقة تحميل المستند

أول شيء نقوم به هو إنشاء كائن `LoadOptions`. هذا الكائن هو البوابة لكل تعديل قد تحتاجه أثناء التحميل، من معالجة كلمة المرور إلى ميزة **تسجيل رد النداء التحذيري**.

```java
// Step 1: Prepare LoadOptions for custom loading behavior
LoadOptions loadOptions = new LoadOptions();
```

لماذا لا نستدعي مباشرة `new Document("file.docx")`؟ لأنه بدون `LoadOptions` تفقد الفرصة للربط بأحداث التحميل. `LoadOptions` هو المكان الوحيد الذي تسمح لك فيه Aspose.Words **بتخصيص تحميل المستند**.

## الخطوة 2 – تسجيل رد النداء التحذيري لتتبع الخطوط المفقودة

الآن يأتي نجم العرض: نحن **نسجل رد النداء التحذيري** الذي ينفّذ `IWarningCallback`. داخل طريقة `warning` نقوم بفلترة `WarningType.FONT_SUBSTITUTION` ونطبع رسالة مفيدة.

```java
// Step 2: Register a warning handler that reports font substitution events
loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

- **لماذا `IWarningCallback`؟** إنها الواجهة التي تستخدمها Aspose.Words لجميع أنواع التحذيرات، وتوفر لك نقطة دخول واحدة للعديد من المشكلات المحتملة.  
- **الفلترة ضرورية** – بدون شرط `if` سترى تحذيرات حول صور مفقودة، ميزات مهجورة، إلخ، مما سيملأ سجلاتك.  
- **سلامة الخيوط** – رد النداء يُنفّذ على نفس الخيط الذي يحمل المستند، لذا يمكنك تحديث الهياكل المشتركة بأمان إذا احتجت لتجميع النتائج لاحقًا.

هذا المقتطف **يسجل رد النداء التحذيري**، ومن الآن فصاعدًا سيتم طباعة كل حدث خط مفقود إلى `stdout`. هذا هو جوهر **تتبع الخطوط المفقودة**.

## الخطوة 3 – تحميل المستند باستخدام `LoadOptions` المُكوَّن

مع وجود رد النداء، نقوم أخيرًا بتحميل الملف. إذا كان المستند يشير إلى خط غير موجود لديك، سيُطلق رد النداء قبل أن يتم إنشاء كائن المستند بالكامل.

```java
// Step 3: Load the document with our custom LoadOptions
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

استبدل `YOUR_DIRECTORY` بالمسار الفعلي على جهازك. يقوم مُنشئ `Document` بقراءة الملف، وتطبيق أي كلمة مرور (إذا قمت بتعيينها في `loadOptions`)، ويُطلق رد النداء التحذيري لكل خط مفقود. سترى مخرجات مثل:

```
Font substitution detected: Font 'Calibri' was substituted with 'Arial'.
```

هذا السطر يثبت أنك نجحت في **تتبع الخطوط المفقودة**.

## الخطوة 4 – متابعة معالجة المستند (اختياري)

في هذه المرحلة يمكنك تعديل المستند كما تشاء—استبدال النص، إدراج صور، أو حتى استبدال الخطوط المستبدلة برمجيًا. رد النداء قد زودك بالفعل بقائمة الخطوط المشكلة، لذا يمكنك، على سبيل المثال، تضمين خط احتياطي:

```java
// Optional: Replace missing fonts with a known fallback (e.g., Liberation Sans)
FontSettings fontSettings = new FontSettings();
fontSettings.setSubstitutionSettings(new FontSubstitutionSettings());
fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
    .add("Calibri", "Liberation Sans");
document.setFontSettings(fontSettings);
```

لا تتردد في تخطي هذا الجزء إذا كنت تحتاج فقط إلى **تتبع الخطوط المفقودة**. المفتاح هو أنك الآن تمتلك المعلومات اللازمة لاتخاذ قرار مستنير.

## الخطوة 5 – حفظ المستند المعالج

أخيرًا، احفظ المستند. يمكنك استبدال الأصلي، حفظه في موقع جديد، أو تصديره إلى PDF—كل ذلك دون فقدان بيانات التحذير التي تم جمعها مسبقًا.

```java
// Step 5: Save the processed document
document.save("YOUR_DIRECTORY/processed.docx");
System.out.println("Document saved successfully.");
```

تشغيل الفئة بالكامل سيولد مخرجات على وحدة التحكم لكل خط مفقود وملف جديد يُدعى `processed.docx` في نفس المجلد.

## مثال عملي كامل

فيما يلي الفئة الكاملة بلغة Java التي يمكنك نسخها ولصقها في بيئة التطوير المتكاملة الخاصة بك. تشمل كل ما ناقشنا، بالإضافة إلى دالة `main` الصغيرة.

```java
import com.aspose.words.*;

public class FontDiagnostic {
    public static void main(String[] args) throws Exception {
        // Step 1: Create LoadOptions to customize how the document is loaded
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Register a warning handler that reports font substitution events
        loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution detected: " + info.getDescription());
                }
            }
        });

        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Optional Step 4: Replace missing fonts with a fallback (if desired)
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
        //     .add("Calibri", "Liberation Sans");
        // document.setFontSettings(fontSettings);

        // Step 5: Save the processed document
        document.save("YOUR_DIRECTORY/processed.docx");
        System.out.println("Document saved successfully.");
    }
}
```

### المخرجات المتوقعة

عند تشغيل البرنامج على مستند يستخدم خطًا غير مثبت على نظامك، سترى شيئًا مشابهًا لـ:

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
Font substitution detected: Font 'Cambria Math' was substituted with 'Arial Unicode MS'.
Document saved successfully.
```

إذا كان المستند لا يحتوي على **خطوط مفقودة**، سيبقى سطر الأوامر صامتًا حتى سطر “Document saved successfully.” النهائي—وهو بالضبط ما تتوقعه من تنفيذ **تسجيل رد النداء التحذيري** المتقن.

## نصائح احترافية ومشكلات شائعة

- **هل هناك ردود نداء متعددة؟** Aspose.Words يسمح فقط بمعالج تحذير واحد. إذا كنت بحاجة إلى التسجيل في ملف وعلى وحدة التحكم معًا، نفّذ رد نداء مركب يوجه التحذير إلى وجهات متعددة.  
- **دفعات كبيرة** – عند معالجة مئات الملفات، فكر في إعادة استخدام كائن `LoadOptions` واحد؛ إنشاءه لكل ملف يضيف عبئًا غير ضروري.  
- **المستندات المشفرة** – عيّن كلمة المرور في `LoadOptions` قبل التحميل، وإلا ستحصل على استثناء `IncorrectPasswordException` قبل أن يُطلق رد النداء أبدًا.  
- **الأداء** – رد النداء يُنفّذ بشكل متزامن. إذا كنت تسجل إلى خدمة عن بُعد، خزن الرسائل مؤقتًا وقم بتفريغها بعد اكتمال التحميل لتجنب اختناقات I/O.  
- **الخط الاحتياطي** – يمكنك أيضًا توفير مجموعة `FontSource` مخصصة إذا كان لديك خطوط ملكية تريد أن تأخذها Aspose.Words في الاعتبار قبل اللجوء إلى خطوط النظام.

## الخلاصة

لقد تعلمت الآن كيفية **تسجيل رد النداء التحذيري** في Java، وتتبع **الخطوط المفقودة** بفعالية، و**تخصيص تحميل المستند** باستخدام Aspose.Words. الحل مستقل، يعمل بدالة `main` واحدة، ويمنحك رؤية فورية لأي استبدال خط قد يظل غير ملحوظ.

ما الخطوات التالية؟ جرّب توسيع رد النداء لكتابة التحذيرات إلى ملف CSV لأغراض التدقيق، أو دمجه مع معالج دفعات يضمّن الخطوط المفقودة تلقائيًا. يمكنك أيضًا استكشاف أنواع تحذير أخرى مثل `IMAGE_SUBSTITUTION` أو `DEPRECATED_FEATURE`—النمط نفسه ينطبق.

برمجة سعيدة، ولتظهر مستنداتك دائمًا كما قصدت!

![تسجيل رد النداء التحذيري مخطط](register-warning-callback.png "تدفق تسجيل رد النداء التحذيري")

## ماذا يجب أن تتعلم بعد ذلك؟

- [رد النداء التحذيري في مستند Word](/words/english/net/programming-with-loadoptions/warning-callback/)
- [تخصيص ألوان السمات والخطوط في Aspose.Words Java: دليل شامل](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [تتبع التغييرات في مستندات Word باستخدام Aspose.Words Java: دليل كامل لتعديلات المستند](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}