---
category: general
date: 2026-02-10
description: كيفية التعامل مع الخطوط في Java باستخدام Aspose.Words. تعرّف على تحذيرات
  استبدال الخطوط، واستدعاءات LoadOptions، ومعالجة الخطوط المفقودة في بضع خطوات.
draft: false
keywords:
- how to handle fonts
- font substitution warnings
- Aspose.Words Java
- LoadOptions warning callback
- MissingFont.docx handling
language: ar
og_description: كيفية التعامل مع الخطوط في جافا باستخدام Aspose.Words. يوضح هذا الدليل
  خطوة بخطوة معالجة استبدال الخطوط، واستدعاءات التحذير، وإدارة الخطوط المفقودة.
og_title: كيفية التعامل مع الخطوط في جافا – دليل Aspose.Words الكامل
tags:
- Java
- Aspose.Words
- Document Processing
title: كيفية التعامل مع الخطوط في جافا باستخدام Aspose.Words – دليل كامل
url: /ar/java/document-rendering/how-to-handle-fonts-in-java-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية التعامل مع الخطوط في جافا – دليل كامل

هل تساءلت يومًا **كيف تتعامل مع الخطوط** عندما يشير مستند Word إلى خط غير مثبت على الخادم الخاص بك؟ هذا السيناريو يسبب إرباكًا للعديد من المطورين، خاصةً عندما تقوم بأتمتة إنشاء المستندات أو تحويلها باستخدام Aspose.Words. الخبر السار؟ يمكنك التقاط كل حدث استبدال خط والرد عليه—بدون أي تخمين.

في هذا البرنامج التعليمي سنستعرض مثالًا واقعيًا يوضح **كيفية التعامل مع الخطوط** باستخدام Aspose.Words for Java. سنربط رد نداء تحذير، ونفلتر فقط تحذيرات استبدال الخطوط، ونطبع رسالة ودية لكل خط مفقود. في النهاية ستفهم لماذا هذا مهم، وكيفية تنفيذه بشكل نظيف، وما الذي تتوقعه عند تشغيل الكود.

> **ما ستحصل عليه:** فئة Java كاملة جاهزة للتنفيذ، شرح لكل سطر، نصائح للاستخدام في الإنتاج، وطريقة سريعة للتحقق من النتيجة.

---

## المتطلبات المسبقة

- **Java 8** (أو أحدث) مثبت على جهازك.  
- **Aspose.Words for Java** JAR (أحدث نسخة حتى 2026‑02، مثال: `aspose-words-23.11.jar`).  
- مستند تجريبي (`MissingFont.docx`) يشير إلى خط غير مثبت لديك.  
- بيئة تطوير (IntelliJ IDEA، Eclipse، أو حتى محرر نصوص بسيط + سطر الأوامر).

لا تحتاج إلى أطر إضافية—فقط Java عادية وملف JAR الخاص بـ Aspose.Words.

![مخطط يوضح كيفية التعامل مع الخطوط في جافا باستخدام Aspose.Words](https://example.com/handle-fonts-diagram.png "مخطط كيفية التعامل مع الخطوط")

*نص بديل للصورة: مخطط كيفية التعامل مع الخطوط*

## الخطوة 1 – إعداد رد نداء التحذير (جوهر **كيفية التعامل مع الخطوط**)

عند تحميل Aspose.Words لمستند، يُطلق سلسلة من كائنات `WarningInfo` لأي شيء غير مثالي. من خلال إرفاق `IWarningCallback`، يمكنك اعتراض تلك التحذيرات في الوقت الفعلي.

```java
import com.aspose.words.*;

public class FontSubstitutionDemo {

    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions and register a warning callback.
        LoadOptions loadOptions = new LoadOptions();

        // The callback will be invoked for every warning Aspose.Words emits.
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // 2️⃣ Filter for FONT_SUBSTITUTION warnings only.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Substituted font: " + info.getDescription());
                }
                // Other warning types are ignored – you could log them here if you wish.
            }
        });
```

**لماذا هذا مهم:**  
إذا تخطيت رد النداء، سيستبدل Aspose.Words الخطوط المفقودة بخط افتراضي بصمت، ولن تعرف أي الخطوط كانت مفقودة. من خلال معالجة التحذير، تحصل على رؤية واضحة ويمكنك اتخاذ قرار بإدراج خط بديل، أو تسجيل المشكلة، أو حتى إلغاء العملية.

---

## الخطوة 2 – تحميل المستند باستخدام `LoadOptions` المُكوَّنة

الآن بعد أن أصبح رد النداء جاهزًا، نقوم ببساطة بتحميل المستند. يتم تمرير كائن `LoadOptions` الذي أنشأناه أعلاه مباشرةً إلى مُنشئ `Document`.

```java
        // 3️⃣ Load a document that may contain missing fonts.
        // Replace the path with the actual location of your test file.
        Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // At this point the warning callback runs automatically.
        // Any font substitution will be printed to the console.
```

**ما الذي تتوقعه:**  
عندما يشير `MissingFont.docx` إلى، على سبيل المثال، *Comic Sans MS* لكن الخادم يحتوي فقط على *Arial*، سيطبع رد النداء شيئًا مثل:

```
Substituted font: Font 'Comic Sans MS' was substituted with 'Arial'.
```

إذا تم تحميل المستند دون أي خطوط مفقودة، لن يُطبع شيء—وهذا بالضبط ما تريد عندما تتعامل مع **كيفية التعامل مع الخطوط** بسلاسة.

---

## الخطوة 3 – (اختياري) التحقق من جدول خطوط المستند

أحيانًا تحتاج إلى فحص الخطوط التي يستخدمها المستند فعليًا بعد التحميل. Aspose.Words يجعل ذلك سهلًا.

```java
        // Optional: List all fonts the document thinks it has.
        FontInfoCollection fonts = document.getFontInfos();
        System.out.println("\n--- Fonts used in the document ---");
        for (FontInfo font : fonts) {
            System.out.println(font.getFullName());
        }
    }
}
```

**متى تستخدم هذا:**  
إذا كنت تبني معالج دفعات يجب أن يبلغ عن الخطوط المفقودة قبل نشر PDF، فإن طباعة جدول الخطوط يمنحك فحصًا نهائيًا.

---

## مثال كامل قابل للتنفيذ

بجمع كل ذلك معًا، إليك الفئة الكاملة التي يمكنك نسخها ولصقها في `FontSubstitutionDemo.java` وتشغيلها:

```java
import com.aspose.words.*;

public class FontSubstitutionDemo {
    public static void main(String[] args) throws Exception {

        // Step 1 – Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Handle only font‑substitution warnings.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Substituted font: " + info.getDescription());
                }
            }
        });

        // Step 2 – Load the document that may contain missing fonts.
        Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // Step 3 – (Optional) List the fonts the document finally uses.
        FontInfoCollection fonts = document.getFontInfos();
        System.out.println("\n--- Fonts used in the document ---");
        for (FontInfo font : fonts) {
            System.out.println(font.getFullName());
        }
    }
}
```

**تشغيل الكود:**  

```bash
javac -cp "aspose-words-23.11.jar" FontSubstitutionDemo.java
java -cp ".:aspose-words-23.11.jar" FontSubstitutionDemo
```

يجب أن ترى رسائل الاستبدال متبوعةً بقائمة الخطوط النهائية.

---

## أسئلة شائعة وحالات حافة

### ماذا لو احتجت إلى استبدال الخط بنفسي؟

رد النداء التحذيري يخبرك فقط *ما* تم استبداله. إذا أردت فرض خط بديل محدد، يمكنك استخدام `FontSettings`:

```java
FontSettings fontSettings = new FontSettings();
fontSettings.setSubstitutionSettings(new FontSubstitutionSettings() {{
    getTableSubstitution().addSubstitutes("MissingFont", "Arial");
}});
loadOptions.setFontSettings(fontSettings);
```

الآن أي ظهور لـ “MissingFont” سيستبدل بـ “Arial” قبل تحميل المستند.

### هل يعمل هذا عند الحفظ كملف PDF؟

بالطبع. نفس رد النداء يُطلق أثناء `document.save("out.pdf")` إذا كان مُحرك PDF يحتاج أيضًا إلى استبدال الخطوط. احتفظ بنفس `LoadOptions` أو أرفق رد نداء جديد إلى `PdfSaveOptions`.

### كيف يتصرف هذا في بيئة متعددة الخيوط؟

`LoadOptions` **ليس** آمنًا للاستخدام المتعدد الخيوط، لذا أنشئ نسخة جديدة لكل خيط. يمكن أن يكون رد النداء نفسه بدون حالة (كما هو موضح) أو يمكنك حقن مسجل يكون مدركًا للخيوط.

### ماذا لو كان الخط المفقود خطًا مخصصًا للشركة؟

عادةً ما تقوم بدمج ذلك الخط في مجلد الخطوط على الخادم وتوجيه Aspose.Words إليه عبر `FontSettings.setFontsFolder("path/to/fonts", true)`. سيتوقف رد النداء عن الإطلاق لهذا الخط لأنه لم يعد مفقودًا.

---

## نصائح احترافية للتعامل مع الخطوط في بيئة الإنتاج

- **سجّل، لا تكتفِ بـ `System.out.println`** – استخدم إطار تسجيل مناسب (SLF4J، Log4j) حتى تتمكن من التقاط التحذيرات في نظام المراقبة الخاص بك.  
- **خزن نتائج البحث عن الخطوط في الذاكرة** – إذا كنت تعالج آلاف المستندات، تجنّب فحص دليل الخطوط في النظام بشكل متكرر. حمّل الخطوط مرة واحدة في كائن `FontSettings` وأعد استخدامه.  
- **افشل بسرعة عندما تكون الخطوط الحرجة مفقودة** – يمكنك رمي استثناء داخل رد النداء إذا كان خط معين ضروريًا للامتثال للعلامة التجارية.  
- **اختبر مع مجموعة متنوعة من المستندات** – تضمّن PDFs، DOCX، وDOC؛ كل تنسيق قد يُطلق أنواع تحذير مختلفة.

---

## الخلاصة

لقد غطينا **كيفية التعامل مع الخطوط** في جافا باستخدام Aspose.Words من البداية إلى النهاية:

1. إرفاق `IWarningCallback` لالتقاط تحذيرات استبدال الخطوط.  
2. تحميل المستند باستخدام `LoadOptions` بحيث يعمل رد النداء تلقائيًا.  
3. (اختياري) فحص قائمة الخطوط النهائية لتأكيد النتيجة.  

باتباع هذه الخطوات ستحصل على رؤية كاملة للخطوط المفقودة، ويمكنك فرض سياسات الخطوط الخاصة بالشركة، وتجنب الاستبدالات الصامتة التي قد تفسد مظهر ملفات PDF أو Word التي تُنشئها.

هل أنت مستعد للتحدي التالي؟ جرّب استبدال رد النداء لتسجيل *جميع* التحذيرات، جرب `FontSettings` لقواعد استبدال مخصصة، أو دمج هذه المنطق في خدمة مايكرو Spring‑Boot التي تعالج المستندات في الوقت الفعلي.

برمجة سعيدة، ولتظهر مستنداتك دائمًا بالخط المناسب!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}