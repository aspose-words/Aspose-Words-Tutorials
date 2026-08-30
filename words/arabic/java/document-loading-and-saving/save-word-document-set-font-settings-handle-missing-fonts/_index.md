---
category: general
date: 2026-04-24
description: تعلم كيفية حفظ مستند Word باستخدام Aspose.Words مع ضبط إعدادات الخط ومعالجة
  الخطوط المفقودة باستخدام كود Java سهل المتابعة.
draft: false
keywords:
- save word document
- set font settings
- how to set font settings
- aspose words font substitution
- handle missing fonts
language: ar
og_description: احفظ مستند Word باستخدام Aspose.Words مع ضبط إعدادات الخط ومعالجة
  الخطوط المفقودة. دليل Java كامل للمطورين.
og_title: حفظ مستند Word – ضبط إعدادات الخط، التعامل مع الخطوط المفقودة
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: حفظ مستند Word – ضبط إعدادات الخط، التعامل مع الخطوط المفقودة
url: /ar/java/document-loading-and-saving/save-word-document-set-font-settings-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ مستند Word – ضبط إعدادات الخط، معالجة الخطوط المفقودة

هل احتجت يوماً إلى **حفظ مستند Word** لكن الملف الأصلي يستخدم خطوطاً لا يتوفر على خادمك؟ هذه مشكلة شائعة يمكن أن تحول خط أنابيب الأتمتة السلس إلى صداع.  

الخبر السار؟ مع Aspose.Words يمكنك **ضبط إعدادات الخط** في الوقت الفعلي، التقاط تحذيرات الخطوط المفقودة، ولا يزال بإمكانك الحصول على مستند Word محفوظ بشكل مثالي. في هذا الدرس سنستعرض مثالًا كاملاً بلغة Java يوضح **كيفية ضبط إعدادات الخط**، معالجة تحذيرات *استبدال الخط* المزعجة، وأخيرًا **حفظ مستند Word** دون مفاجآت.

## ما ستتعلمه

- كيفية تكوين `LoadOptions` باستخدام كائن `FontSettings` مخصص.  
- كيفية تسجيل رد نداء تحذير (warning callback) يُبلغ عن أحداث **aspose words font substitution**.  
- كيفية تحميل ملف DOCX، السماح لـ Aspose باستبدال الخطوط المفقودة، ثم **حفظ مستند Word** في موقع جديد.  
- نصائح لمعالجة الحالات الخاصة مثل الملفات المشفرة أو المستندات التي تحتوي على خطوط مدمجة.  

لا تحتاج إلى أي مكتبات إضافية بخلاف Aspose.Words، والكود يعمل مع أحدث إصدار 24.x (اعتبارًا من أبريل 2026).  

---

![مخطط يوضح سير عمل حفظ مستند Word مع إعدادات الخط ورد نداء التحذير](font-workflow.png "مخطط يوضح سير عمل حفظ مستند Word")

## حفظ مستند Word مع إعدادات خط مخصصة

الخطوة الأولى هي إخبار Aspose.Words بما يجب فعله عندما لا يستطيع العثور على خط يُشير إليه المستند الأصلي. هنا يأتي دور **ضبط إعدادات الخط**.

```java
import com.aspose.words.*;

public class FontDiagnostics {
    public static void main(String[] args) throws Exception {
        // -----------------------------------------------------------------
        // Step 1: Prepare LoadOptions with a fresh FontSettings instance.
        // -----------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();
        // By default FontSettings uses system fonts, but we can add folders later.
        loadOptions.setFontSettings(new FontSettings());

        // -----------------------------------------------------------------
        // Step 2: Register a warning callback to catch FONT_SUBSTITUTION alerts.
        // -----------------------------------------------------------------
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about missing‑font warnings.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution: " + info.getDescription());
                }
            }
        });

        // -----------------------------------------------------------------
        // Step 3: Load the source document using the configured options.
        // -----------------------------------------------------------------
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // -----------------------------------------------------------------
        // Step 4: Save the processed document – fonts have been substituted.
        // -----------------------------------------------------------------
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**لماذا يعمل هذا:**  
- `LoadOptions` يخبر Aspose.Words باستخدام `FontSettings` المزوَّدة عند تحليل الملف.  
- `IWarningCallback` يعترض أي رسائل **aspose words font substitution**، موفرًا لك سجلًا مباشرًا للخطوط المفقودة.  
- عند استدعاء `document.save(...)`، يقوم Aspose تلقائيًا باستبدال الخطوط المفقودة بأقرب تطابقات من النظام أو المجلدات التي أضفتها إلى `FontSettings`.

### النتيجة المتوقعة

تشغيل البرنامج يطبع سطورًا مثل:

```
Font substitution: Font 'Calibri' was not found. Substituted with 'Arial'.
Font substitution: Font 'Cambria' was not found. Substituted with 'Times New Roman'.
```

وبالنهاية ستحصل على `output.docx` الذي يبدو تمامًا كالأصلي—باستثناء أن الخطوط المفقودة تم استبدالها، وتم **حفظ مستند Word** بنجاح على القرص.

## كيفية ضبط إعدادات الخط في Aspose.Words

إذا كنت بحاجة إلى مزيد من التحكم—مثلاً تريد توجيه Aspose إلى مجلد خطوط مخصص أو تضمين خط احتياطي—فقط عدّل كائن `FontSettings` قبل ربطه بـ `LoadOptions`.

```java
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder that contains your private fonts.
fontSettings.setFontsFolder("C:/MyCustomFonts", true);

// Optionally, set a default substitution font (e.g., "Arial").
fontSettings.setDefaultFontName("Arial");

// Attach the configured FontSettings to LoadOptions.
loadOptions.setFontSettings(fontSettings);
```

**متى تستخدم هذا:**  
- تطبيقك يعمل داخل حاوية لا تحتوي إلا على مجموعة قليلة من خطوط النظام.  
- لديك خطوط العلامة التجارية للشركة مخزنة في مشاركة شبكة آمنة.  
- تريد ضمان أن يكون خط احتياطي محدد (مثل “Arial”) مستخدمًا دائمًا، لتجنب الاستبدالات غير المتوقعة.

## معالجة الخطوط المفقودة – رد نداء استبدال الخط

رد نداء التحذير الذي سجلناه سابقًا هو جوهر منطق **معالجة الخطوط المفقودة**. يمكنك توسيعه ليقوم بـ:

1. **جمع التحذيرات** في قائمة للتقارير المستقبلية.  
2. **إلقاء استثناء** إذا كان خط حاسم مفقودًا (مثلاً خط الشعار).  
3. **تسجيل في نظام مراقبة** (Splunk، ELK، إلخ) لتتبع المراجعات.

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    private final List<String> missingFonts = new ArrayList<>();

    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            String msg = "Missing font: " + info.getDescription();
            System.out.println(msg);
            missingFonts.add(msg);
        }
    }

    // Helper to retrieve all missing‑font messages after loading.
    public List<String> getMissingFonts() {
        return missingFonts;
    }
});
```

**نصيحة احترافية:** إذا كنت بحاجة إلى إيقاف العملية عندما يكون خط معين غير موجود، قارن `info.getDescription()` مع قائمة بيضاء وألقِ `RuntimeException` عندما لا يتطابق.

## مثال Java كامل – من البداية إلى النهاية

بتجميع كل ما سبق، إليك برنامجًا مستقلًا يمكنك نسخه ولصقه في بيئة التطوير المتكاملة (IDE). تأكد من وجود ملف JAR الخاص بـ Aspose.Words for Java في مسار الـ classpath.

```java
import com.aspose.words.*;
import java.util.*;

public class SaveWordWithFontHandling {
    public static void main(String[] args) throws Exception {
        // ------------------- Configure FontSettings -------------------
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains any custom fonts you might need.
        fontSettings.setFontsFolder("C:/CustomFonts", true);
        // Ensure a safe fallback.
        fontSettings.setDefaultFontName("Arial");

        // ------------------- Prepare LoadOptions -------------------
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setFontSettings(fontSettings);

        // ------------------- Warning callback (handle missing fonts) -------------------
        loadOptions.setWarningCallback(new IWarningCallback() {
            private final List<String> missing = new ArrayList<>();

            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBstitution) {
                    String msg = "Font substitution: " + info.getDescription();
                    System.out.println(msg);
                    missing.add(msg);
                }
            }

            public List<String> getMissing() {
                return missing;
            }
        });

        // ------------------- Load the source DOCX -------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // ------------------- Save the result -------------------
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

شغّل البرنامج، راقب وحدة التحكم لأي **font

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}