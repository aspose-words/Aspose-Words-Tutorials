---
category: general
date: 2026-06-08
description: اعثر على الخطوط المفقودة بسرعة باستخدام Aspose.Words for Java. تعلم كيفية
  تشخيص تحذيرات استبدال الخطوط وإصلاح مشكلات الخطوط المفقودة في بضع خطوات فقط.
draft: false
keywords:
- find missing fonts
- Aspose.Words for Java
- FontSubstitutionWarning
- LoadOptions
- document warnings
language: ar
og_description: اعثر على الخطوط المفقودة في ملفات DOCX الخاصة بك باستخدام Aspose.Words
  for Java. يوضح هذا الدرس كيفية تمكين التشخيص، قراءة أحداث FontSubstitutionWarning،
  وعرض أسماء الخطوط الأصلية مقابل الخطوط المستبدلة.
og_title: العثور على الخطوط المفقودة في جافا – Aspose.Words خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Find missing fonts quickly using Aspose.Words for Java. Learn to diagnose
    font substitution warnings and fix missing font issues in just a few steps.
  headline: Find Missing Fonts in Java with Aspose.Words – Complete Guide
  type: TechArticle
- description: Find missing fonts quickly using Aspose.Words for Java. Learn to diagnose
    font substitution warnings and fix missing font issues in just a few steps.
  name: Find Missing Fonts in Java with Aspose.Words – Complete Guide
  steps:
  - name: Expected Console Output
    text: '``` Font substituted: Comic Sans MS → Arial Font substituted: MyCustomFont
      → Times New Roman ```'
  - name: Missing Font but No Warning
    text: Sometimes a font is embedded in the DOCX, but the embedding is corrupted.
      Aspose will still raise a `FontSubstitutionWarning` because it cannot render
      the text. To differentiate, check `fsWarning.isFontEmbedded()` (available in
      newer versions).
  - name: Multiple Substitutions for the Same Font
    text: A single missing font may be substituted multiple times across different
      runs if the fallback hierarchy changes (e.g., first tries Arial, then falls
      back to Helvetica). Keep a `Set<String>` of `getOriginalFontName()` to deduplicate
      if you only need a list of unique missing fonts.
  - name: Performance Considerations
    text: Loading very large DOCX files (hundreds of MB) while collecting warnings
      can add overhead. If you only need font diagnostics, set `loadOptions.setValidateStructure(false)`
      to skip deep validation. This speeds up the process without affecting warning
      generation.
  type: HowTo
tags:
- Java
- Aspose.Words
- fonts
- diagnostics
title: العثور على الخطوط المفقودة في جافا باستخدام Aspose.Words – دليل كامل
url: /ar/java/document-rendering/find-missing-fonts-in-java-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# العثور على الخطوط المفقودة في Java باستخدام Aspose.Words – دليل شامل

هل تساءلت يومًا كيف **العثور على الخطوط المفقودة** في مستند Word قبل أن يفسد تخطيطك؟ لست وحدك—المطورون يواجهون باستمرار استبدالات صامتة للخطوط تُفسد ملفات PDF أو التقارير المطبوعة. الخبر السار هو أن Aspose.Words for Java يوفّر لك واجهة برمجة تطبيقات تشخيص مدمجة تجعل اكتشاف تلك الخطوط المفقودة أمرًا سهلًا.

في هذا الدرس سنستعرض مثالًا واقعيًا يقوم بتحميل ملف DOCX، تمكين جمع التحذيرات، وطباعة كل *FontSubstitutionWarning* تحتاج معرفتها. في النهاية ستتمكن من تسجيل اسم الخط الأصلي، الخط البديل الذي اختاره Aspose، وتحديد ما إذا كنت ستدمج الخط المفقود بنفسك.

## ما ستحتاجه

قبل أن نبدأ، تأكد من وجود التالي:

* **Aspose.Words for Java** (أحدث إصدار 23.x) في مسار الـ classpath الخاص بك.  
* بيئة تطوير Java 8+ (IDE من اختيارك، Maven/Gradle يعملان جيدًا).  
* ملف DOCX تجريبي يُشير عمدًا إلى خط غير مثبت على جهازك—لنسميه `MissingFonts.docx`.

هذا كل ما تحتاجه. لا مكتبات إضافية، لا إعدادات معقدة، فقط Java صافية وAspose.

![مخطط العثور على الخطوط المفقودة](https://example.com/find-missing-fonts.png "مخطط العثور على الخطوط المفقودة")

*الصورة أعلاه توضح التدفق: تحميل → تشخيص → تحذيرات → إخراج.*

## الخطوة 1: إعداد LoadOptions وتحديد تنسيق المستند

أول ما نقوم به هو إنشاء كائن **LoadOptions**. هذا يخبر Aspose.Words كيف يفسّر الملف الوارد، وبشكل أساسي يُفعّل جمع *تحذيرات المستند*.

```java
import com.aspose.words.*;

public class FontSubstitutionDiagnostics {
    public static void main(String[] args) throws Exception {
        // Create LoadOptions and force DOCX format (helps when the file extension is misleading)
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setLoadFormat(LoadFormat.DOCX);
```

*لماذا نستخدم LoadOptions؟*  
بدونه، يظل Aspose يحمل الملف لكنه قد يتخطى بعض بيانات التشخيص. من خلال تحديد التنسيق صراحةً تضمن توليد تحذيرات متسقة، خاصةً عند التعامل مع ملفات قديمة أو تالفة.

## الخطوة 2: تحميل المستند مع تمكين التشخيص

الآن نقوم بقراءة الملف فعليًا. مُنشئ `Document` يبدأ تلقائيًا في جمع التحذيرات، والتي ستتضمن لاحقًا أي كائنات **FontSubstitutionWarning**.

```java
        // Load the document located in your project folder
        Document doc = new Document("YOUR_DIRECTORY/MissingFonts.docx", loadOptions);
```

> **نصيحة احترافية:** إذا كنت تستخدم Maven، أضف تبعية Aspose.Words إلى ملف `pom.xml`. بهذه الطريقة يتم سحب الـ JAR تلقائيًا ولن تحتاج لإدارة الـ classpath يدويًا.

## الخطوة 3: فحص تحذيرات المستند لأحداث استبدال الخطوط

Aspose يخزن كل تحذير في مجموعة يمكنك التكرار عليها. نقوم بفلترة كائنات `FontSubstitutionWarning` لأنها تشير تحديدًا إلى خط مفقود تم استبداله.

```java
        // Iterate over all warnings generated during load
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsWarning = (FontSubstitutionWarning) warning;
```

*ماذا يحدث هنا؟*  
`doc.getWarnings()` تُعيد `List<WarningInfo>`. من خلال التحقق `instanceof FontSubstitutionWarning` نعزل فقط الإدخالات المتعلقة بالخطوط، متجاهلين التحذيرات الأخرى مثل “ميزة غير مدعومة” أو “تحويل صورة”.

## الخطوة 4: إخراج أسماء الخط الأصلي والبديل

أخيرًا، نطبع كلًا من اسم الخط المفقود (الأصلي) والخط الذي اختاره Aspose كبديل. هذا الإخراج مثالي للتسجيل أو لتغذيته في فحص خط أنابيب البناء.

```java
                // Print the original font and the font Aspose substituted it with
                System.out.println("Font substituted: " + fsWarning.getOriginalFontName()
                        + " → " + fsWarning.getSubstitutedFontName());
            }
        }
    }
}
```

### الإخراج المتوقع في وحدة التحكم

```
Font substituted: Comic Sans MS → Arial
Font substituted: MyCustomFont → Times New Roman
```

إذا لم يظهر أي شيء، فهذا يعني **عدم اكتشاف أي خطوط مفقودة**—المستند لديك يحتوي بالفعل على الخطوط الموجودة على الجهاز الذي يشغل الكود.

## الخطوة 5: معالجة الحالات الخاصة والمشكلات الشائعة

### خط مفقود دون تحذير

أحيانًا يكون الخط مدمجًا في DOCX، لكن الدمج تالف. سيظل Aspose يرفع `FontSubstitutionWarning` لأنه لا يستطيع عرض النص. للتمييز، تحقق من `fsWarning.isFontEmbedded()` (متاح في الإصدارات الأحدث).

### استبدالات متعددة لنفس الخط

خط مفقود واحد قد يُستبدل عدة مرات عبر تشغيلات مختلفة إذا تغيرت سلسلة fallback (مثلاً، أولًا يجرب Arial، ثم ينتقل إلى Helvetica). احتفظ بـ `Set<String>` من `getOriginalFontName()` لإزالة التكرارات إذا كنت تحتاج فقط قائمة بالخطوط المفقودة الفريدة.

### اعتبارات الأداء

تحميل ملفات DOCX ضخمة (مئات الميجابايت) مع جمع التحذيرات قد يضيف عبئًا. إذا كنت تحتاج فقط إلى تشخيص الخطوط، عيّن `loadOptions.setValidateStructure(false)` لتجاوز التحقق العميق. هذا يسرّع العملية دون التأثير على توليد التحذيرات.

## مكافأة: أتمتة دمج الخطوط

بمجرد معرفة الخطوط المفقودة، يمكنك دمجها برمجيًا:

```java
for (String missingFont : missingFontsSet) {
    // Assume you have the TTF file for the missing font in a known folder
    FontSettings.getDefaultInstance().setFontsFolder("YOUR_FONTS_FOLDER", true);
}
```

الدمج يضمن أن ملف PDF النهائي أو DOCX المحفوظ يعرض المحتوى بالضبط كما هو مقصود على أي جهاز—لا مفاجآت استبدال أخرى.

## ملخص: كيفية العثور على الخطوط المفقودة باستخدام Aspose.Words

- **إنشاء LoadOptions** وتحديد تنسيق التحميل.  
- **تحميل المستند** بينما Aspose يجمع التحذيرات.  
- **التكرار على `doc.getWarnings()`**، مع فلترة `FontSubstitutionWarning`.  
- **طباعة** `getOriginalFontName()` و `getSubstitutedFontName()` لمعرفة الخطوط المفقودة.  
- **اختياري:** إزالة التكرارات، فحص حالة الدمج، أو دمج الخطوط المفقودة تلقائيًا.

هذه هي الحل الكامل **للعثور على الخطوط المفقودة** في تطبيق Java باستخدام Aspose.Words. الآن لديك طريقة موثوقة لاكتشاف مشاكل الخط مبكرًا، والحفاظ على تناسق ملفات PDF، وتجنب المفاجآت غير السارة في بيئة الإنتاج.

## ما الذي يمكنك استكشافه لاحقًا؟

* **دمج الخطوط** تلقائيًا (انظر المقتطف الإضافي).  
* **إنشاء PDF** بعد إصلاح الخطوط للتحقق من المظهر البصري.  
* **استخدام FontSettings** في Aspose.Words لتحديد سلسلة fallback مخصصة.  
* **تشغيل نفس التشخيص على ملفات DOC، RTF، أو HTML**—فقط غيّر `LoadFormat` وفقًا لذلك.

لا تتردد في تجربة أنواع مستندات وعائلات خطوط مختلفة. إذا واجهت أي صعوبة، اترك تعليقًا أدناه أو راجع الوثائق الرسمية لـ Aspose API للـ Java لمزيد من التخصيص المتعمق.

برمجة سعيدة، ولتظهر مستنداتك دائمًا بالخطوط التي قصدتها!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [استخدام الخطوط في Aspose.Words لـ Java](/words/english/java/using-document-elements/using-fonts/)
- [التقاط تحذيرات استبدال الخطوط في Java باستخدام Aspose.Words – دليل شامل](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [كيفية اكتشاف الخطوط في Aspose.Words – التعامل مع التحذيرات والإعدادات](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}