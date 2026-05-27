---
category: general
date: 2026-05-26
description: قم بتعيين إعدادات الخط الافتراضية في Aspose.Words للـ Java وتعلم كيفية
  تعيين إعدادات الخط واكتشاف الخطوط المفقودة في بضع أسطر من الشيفرة فقط.
draft: false
keywords:
- set default font settings
- set font settings
- detect missing fonts
language: ar
og_description: تعيين إعدادات الخط الافتراضية في Aspose.Words للغة Java، وتعلم كيفية
  ضبط إعدادات الخط واكتشاف الخطوط المفقودة بسرعة وموثوقية.
og_title: تعيين إعدادات الخط الافتراضية في Aspose.Words لـ Java
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Set default font settings in Aspose.Words for Java and learn how to
    set font settings and detect missing fonts in just a few lines of code.
  headline: Set Default Font Settings in Aspose.Words for Java – Complete Guide
  type: TechArticle
- description: Set default font settings in Aspose.Words for Java and learn how to
    set font settings and detect missing fonts in just a few lines of code.
  name: Set Default Font Settings in Aspose.Words for Java – Complete Guide
  steps:
  - name: '**Aspose.Words for Java** (version 23.10 or newer) on your classpath.'
    text: '**Aspose.Words for Java** (version 23.10 or newer) on your classpath.'
  - name: A Java 17 (or later) development kit – any modern JDK works.
    text: A Java 17 (or later) development kit – any modern JDK works.
  - name: A DOCX file that intentionally uses a font you don't have installed (e.g.,
      *“MissingFont.ttf”*).
    text: A DOCX file that intentionally uses a font you don't have installed (e.g.,
      *“MissingFont.ttf”*).
  type: HowTo
tags:
- Aspose.Words
- Java
- Font Management
title: تعيين إعدادات الخط الافتراضية في Aspose.Words للغة جافا – دليل كامل
url: /ar/java/document-styling/set-default-font-settings-in-aspose-words-for-java-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تعيين إعدادات الخط الافتراضية في Aspose.Words for Java – دليل كامل

هل تساءلت يومًا كيف **تعيين إعدادات الخط الافتراضية** عند تحميل مستند Word باستخدام Aspose.Words for Java؟ لست وحدك. يمكن أن تحول الأحرف المفقودة تقريرًا مصقولًا إلى فوضى مشوشة، وإن اكتشاف تحذيرات استبدال الخط مبكرًا يوفر ساعات من تصحيح الأخطاء.  

في هذا البرنامج التعليمي سنستعرض مثالًا مختصرًا وشاملًا **يحدد إعدادات الخط الافتراضية**، ويُظهر لك كيفية **تحديد إعدادات الخط** برمجيًا، ويُظهر طريقة موثوقة **لاكتشاف الخطوط المفقودة** قبل أن تُفسد تخطيطك.

---

## ما ستتعلمه

- كيفية إنشاء كائن `LoadOptions` مع نسخة جديدة من `FontSettings`.  
- كيفية إرفاق مستمع تحذير سيقوم **باكتشاف الخطوط المفقودة** أثناء تحميل المستند.  
- كيفية تحميل ملف DOCX بينما يقوم المستمع بالإبلاغ بصمت عن أي استبدالات.  
- نصائح لتخصيص خطوط الاحتياطي ومعالجة الحالات الخاصة في بيئة الإنتاج.

لا مكتبات إضافية، ولا ملفات تكوين غامضة—فقط Java عادية و Aspose.Words.

---

## المتطلبات المسبقة

قبل أن نبدأ، تأكد من أن لديك:

1. **Aspose.Words for Java** (الإصدار 23.10 أو أحدث) في مسار الفئات الخاص بك.  
2. مجموعة تطوير Java 17 (أو أحدث) – أي JDK حديث يعمل.  
3. ملف DOCX يستخدم عمدًا خطًا غير مثبت لديك (مثال، *“MissingFont.ttf”*).  

إذا كنت تفتقد ملف JAR الخاص بـ Aspose، احصل عليه من مستودع Maven الرسمي:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
</dependency>
```

هذا كل شيء—لا حاجة لتثبيت خطوط إضافية لهذا العرض.

---

## الخطوة 1: إنشاء LoadOptions و **تحديد إعدادات الخط الافتراضية**

أول شيء نحتاجه هو كائن `LoadOptions` نظيف يخبر Aspose كيف يتصرف عندما يصادف خطوطًا غير معروفة. باستدعاء `setFontSettings(new FontSettings())` نقوم **بتحديد إعدادات الخط الافتراضية** التي تبدأ بقائمة احتياطي فارغة.

```java
import com.aspose.words.*;

public class FontSubstitutionDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create load options with default font settings.
        LoadOptions loadOptions = new LoadOptions();
        // This line **sets default font settings** – a blank slate for us.
        loadOptions.setFontSettings(new FontSettings());
```

> **لماذا هذا مهم:**  
> عندما لا تقوم بتكوين الخطوط صراحةً، يلجأ Aspose إلى مجموعة الخطوط الافتراضية للنظام، مما قد يخفي مشاكل الخطوط المفقودة. ببدء استخدام نسخة جديدة من `FontSettings` تحصل على سيطرة كاملة على الخطوط التي تُعتبر صالحة.

---

## الخطوة 2: إرفاق مستمع تحذير **لاكتشاف الخطوط المفقودة**

يقوم Aspose بإصدار كائن `WarningInfo` لكل استبدال يقوم به. بالاستماع إلى `WarningType.FONT_SUBSTITUTION` يمكننا **اكتشاف الخطوط المفقودة** فور تحليل المستند.

```java
        // Step 2: Attach a warning listener to capture font‑substitution warnings.
        loadOptions.getWarnings().addWarningListener(warningInfo -> {
            if (warningInfo.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution: " + warningInfo.getDescription());
            }
        });
```

> **نصيحة احترافية:** يعمل المستمع على نفس الخيط الذي يحمل المستند، لذا لا يوجد تقريبًا أي تأثير على الأداء. إذا كنت بحاجة لجمع التحذيرات للتحليل لاحقًا، ادفعها إلى `List<WarningInfo>` بدلاً من طباعتها مباشرة.

---

## الخطوة 3: تحميل المستند باستخدام الخيارات المكوَّنة

الآن بعد أن **حددنا إعدادات الخط** وأعددنا مستمعًا، نقوم ببساطة بتحميل الملف. أي خط مفقود سيُطلق رد النداء الخاص بنا فورًا.

```java
        // Step 3: Load the document using the configured load options.
        Document doc = new Document("YOUR_DIRECTORY/doc-with-missing-font.docx", loadOptions);
```

إذا كان الملف المصدر يشير إلى خط غير مثبت، سترى مخرجات مشابهة لـ:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

هذا السطر يخبرك بالضبط أي خط كان مفقودًا وأي خط احتياطي تم استخدامه—مثالي للتسجيل أو ملاحظات المستخدم.

---

## الخطوة 4: متابعة المعالجة العادية (اختياري)

في هذه المرحلة يكون المستند محملاً بالكامل، ويمكنك المتابعة بأي تعديل ترغب به—تحرير، تحويل إلى PDF، أو استخراج النص. المستمع التحذيري قد أتم مهمته بالفعل، لذا لا تحتاج إلى فحوصات إضافية.

```java
        // Normal processing can continue here; the listener already reported any substitutions.
        // Example: save as PDF
        doc.save("output.pdf");
    }
}
```

> **ماذا لو أردت احتياطيًا مخصصًا؟**  
> بدلاً من ترك `FontSettings` فارغًا، يمكنك إضافة خطوط محددة:

```java
FontSettings fs = new FontSettings();
fs.setSubstitutionSettings(new FontSubstitutionSettings());
fs.getSubstitutionSettings().getDefaultFontSubstitution().setDefaultFontName("Times New Roman");
loadOptions.setFontSettings(fs);
```

الآن أي خط مفقود سيُستبدل بـ *Times New Roman*—خيار موثوق لمعظم المستندات الغربية.

---

## نظرة بصرية

![مخطط يوضح كيفية تعيين إعدادات الخط الافتراضية في Aspose.Words for Java](image.png "مخطط لتدفق تعيين إعدادات الخط الافتراضية")

*نص بديل: مخطط تدفق تعيين إعدادات الخط الافتراضية في Aspose.Words for Java.*

---

## الأخطاء الشائعة وكيفية تجنبها

| المشكلة | لماذا يحدث | الحل |
|---------|------------|------|
| **نسيت استدعاء `setFontSettings`** | Aspose يستخدم الإعدادات الافتراضية للنظام، مما يخفي الخطوط المفقودة. | دائمًا أنشئ نسخة جديدة من `FontSettings` وعيّنها إلى `LoadOptions`. |
| **المستمع لم يُفعَّل** | تم إضافة المستمع بعد تحميل المستند. | أضف مستمع التحذير *قبل* استدعاء `new Document(...)`. |
| **خطأ إملائي في المسار يؤدي إلى `FileNotFoundException`** | المسار المكتوب صلبًا لا يتطابق مع حساسية حالة نظام التشغيل. | استخدم `Paths.get("...").toAbsolutePath()` أو اضبط مسارًا نسبيًا من جذر المشروع. |
| **الخطوط المفقودة المتعددة تغمر السجلات** | المستندات الكبيرة قد تولد العشرات من التحذيرات. | صَفِّ التكرارات أو اجمع الرسائل في `Set<String>` قبل الطباعة. |

---

## توسيع الحل

إذا كنت بحاجة إلى **تحديد إعدادات الخط** لتطبيق كامل، فكر في إنشاء `FontSettings` ككائن مفرد وإعادة استخدامه عبر جميع `LoadOptions`. بهذه الطريقة تحافظ على استراتيجية احتياطي متسقة وتجنب إنشاء كائنات متكررة.

```java
public class FontConfig {
    private static final FontSettings sharedSettings = createSettings();

    private static FontSettings createSettings() {
        FontSettings fs = new FontSettings();
        // Add custom fallback fonts here
        return fs;
    }

    public static LoadOptions getLoadOptions() {
        LoadOptions lo = new LoadOptions();
        lo.setFontSettings(sharedSettings);
        return lo;
    }
}
```

الآن يمكن لأي جزء من قاعدة الكود الخاصة بك ببساطة استدعاء `FontConfig.getLoadOptions()` والاستفادة فورًا من نفس منطق **تعيين إعدادات الخط الافتراضية**.

---

## الخلاصة

لقد غطينا الآن كل ما تحتاجه **لتعيين إعدادات الخط الافتراضية** في Aspose.Words for Java، **تحديد إعدادات الخط** برمجيًا، و **اكتشاف الخطوط المفقودة** قبل أن تفسد مخرجاتك. المثال الكامل القابل للتنفيذ موجود في مقتطفات الشيفرة أعلاه، ويمكنك لصقه مباشرةً في بيئة التطوير المتكاملة (IDE) لرؤية التحذيرات تعمل.

خطوات قادمة؟ جرّب استبدال خط الاحتياطي، جرب صيغ مستندات مختلفة (DOC، RTF، HTML)، أو دمج جامع التحذيرات في لوحة مراقبة. كلما لعبت أكثر مع `FontSettings`، كلما زادت ثقتك بأن المستندات التي تُنشئها تظهر بالضبط كما هو مقصود—بدون مفاجآت، بدون أحرف مكسورة.

هل لديك أسئلة أو سيناريو استبدال خط معقد؟ اترك تعليقًا أدناه، وتمنياتنا لك بالبرمجة السعيدة!

## دروس ذات صلة

- [تعيين إعدادات احتياطي الخط](/words/english/net/working-with-fonts/set-font-fallback-settings/)
- [تعيين إعدادات احتياطي الخط](/words/chinese/net/working-with-fonts/set-font-fallback-settings/)
- [تعيين إعدادات احتياطي الخط](/words/arabic/net/working-with-fonts/set-font-fallback-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}