---
category: general
date: 2026-04-04
description: التقاط تحذيرات استبدال الخطوط أثناء تحميل مستندات Word باستخدام Aspose.Words
  for Java واكتشاف الخطوط المفقودة تلقائيًا. اتبع هذا الدليل خطوة بخطوة.
draft: false
keywords:
- capture font substitution warnings
- detect missing fonts
language: ar
og_description: التقط تحذيرات استبدال الخطوط أثناء تحميل مستندات Word باستخدام Aspose.Words
  for Java واكتشف الخطوط المفقودة في بضع خطوات سهلة.
og_title: التقاط تحذيرات استبدال الخطوط – اكتشاف الخطوط المفقودة
tags:
- Aspose.Words
- Java
- Document Processing
title: التقاط تحذيرات استبدال الخط – اكتشاف الخطوط المفقودة
url: /ar/java/document-loading-and-saving/capture-font-substitution-warnings-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# التقاط تحذيرات استبدال الخط – اكتشاف الخطوط المفقودة

هل احتجت يوماً إلى **التقاط تحذيرات استبدال الخط** عند فتح ملف Word، لتكتشف أن خطًا أساسيًا مفقود؟ لست وحدك. في العديد من سير عمل المؤسسات، يمكن أن يتحول تقرير منسق بشكل مثالي إلى فوضى مشوشة بسبب خط مفقود، والوحيدة التي تحصل عليها هي تحذير صامت لا يراه معظم المطورين.

الخبر السار هو أن Aspose.Words for Java يتيح لك الارتباط بعملية التحميل و**اكتشاف الخطوط المفقودة** قبل أن تسبب لك مشاكل لاحقًا. في هذا الدرس سنستعرض مثالًا كاملاً وقابلًا للتنفيذ يطبع كل تحذير استبدال مباشرةً إلى وحدة التحكم، حتى تتمكن من اتخاذ قرار ما إذا كنت ستضمّن الخط الصحيح، تستبدله، أو تنبه المستخدم.

بنهاية هذا الدليل ستعرف كيف:

* إعداد كائن `LoadOptions` مع رد نداء تحذير مخصص.
* تصفية رد النداء بحيث يتفاعل فقط مع أحداث استبدال الخط.
* تحميل أي ملف `.docx` ورؤية التحذيرات فورًا.
* توسيع الحل لتسجيل التحذيرات، رمي الاستثناءات، أو حتى تثبيت الخطوط المفقودة تلقائيًا.

لا حاجة إلى وثائق خارجية—مجرد بضع أسطر من Java وملف Aspose.Words JAR.

## المتطلبات المسبقة

قبل أن نبدأ، تأكد من أن لديك:

* Java 8 أو أحدث مثبتًا (أفضل نسخة LTS هي الأنسب).
* Aspose.Words for Java 23.11 أو أحدث – يمكنك الحصول على الحزمة عبر Maven أو تحميل ملف JAR مباشرة من موقع Aspose.
* مستند Word يحتوي على خط غير موجود على جهاز التطوير الخاص بك (مثال: “MyFancyFont”).  
* بيئة تطوير متكاملة أو محرر نصوص من اختيارك – أستخدم IntelliJ IDEA، لكن Eclipse أو VS Code يكفيان.

إذا كان أي من هذه غير مألوف لك، توقف وقم بتثبيته أولًا؛ باقي الدرس يفترض أن كل شيء جاهز.

---

## التقاط تحذيرات استبدال الخط باستخدام Aspose.Words

تكمن جوهر الحل في كائن `LoadOptions`. من خلال تعيين `IWarningCallback` يمكننا اعتراض كل تحذير تصدره المكتبة أثناء مرحلة التحميل.

```java
import com.aspose.words.*;

public class FontDiagnosticsTutorial {
    public static void main(String[] args) throws Exception {

        // Step 1️⃣: Create LoadOptions and set a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Capture only font substitution warnings.
                if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
                    System.out.println("Font substitution: " + info.getDescription());
                }
            }
        });

        // Step 2️⃣: Load the document. The callback runs automatically.
        Document doc = new Document("YOUR_DIRECTORY/document-with-missing-font.docx", loadOptions);

        // Step 3️⃣: If you reach this line, the document is loaded.
        // Any missing‑font warnings have already been printed to the console.
        System.out.println("Document loaded successfully.");
    }
}
```

**لماذا يعمل هذا:**  
`LoadOptions` تخبر Aspose.Words كيف يتعامل مع الملف الوارد. واجهة `IWarningCallback` هي نقطة ربط تستقبل كائن `WarningInfo` لكل *تحذير*. من خلال فحص `info.getWarningType()` نقوم بتصفية كل شيء ما عدا `SUBSTITUTED_FONT`. خاصية `description` تحتوي على رسالة قابلة للقراءة مثل “Font 'MyFancyFont' was substituted with 'Arial'”.

### ناتج وحدة التحكم المتوقع

إذا كان المستند المصدر يشير إلى خط غير مثبت، سترى شيئًا مثل:

```
Font substitution: Font 'MyFancyFont' was substituted with 'Arial'.
Document loaded successfully.
```

إذا كان المستند يستخدم خطوطًا موجودة على الجهاز فقط، سيبقى رد النداء صامتًا وستحصل فقط على السطر النهائي “Document loaded successfully.”.

---

## اكتشاف الخطوط المفقودة في المستند الخاص بك

قد تتساءل، *“هل تحذير الاستبدال هو نفسه الخط المفقود؟”* في معظم الحالات، نعم—Aspose.Words يستبدل الخط المفقود بخط احتياطي ويبلغ عنه عبر `SUBSTITUTED_FONT`. ومع ذلك، هناك حالات حافة يكون فيها الخط موجودًا لكن النمط الدقيق (غامق‑مائل، ميزات OpenType محددة) غير متوفر، مما يؤدي إلى استبدال طفيف.

لتكون متأكدًا تمامًا من أنك التقطت كل الفجوات، يمكنك دمج رد النداء التحذيري مع فحص ما بعد التحميل:

```java
// After loading the document, iterate through all runs.
for (Paragraph para : (Iterable<Paragraph>) doc.getFirstSection().getBody().getChildNodes(NodeType.PARAGRAPH, true)) {
    for (Run run : (Iterable<Run>) para.getChildNodes(NodeType.RUN, true)) {
        Font font = run.getFont();
        if (font.getName().equalsIgnoreCase("MyFancyFont")) {
            System.out.println("Run still uses the missing font: " + font.getName());
        }
    }
}
```

**نصيحة محترف:** إذا وجدت أي مقاطع لا تزال تشير إلى الخط المفقود، يمكنك استبدالها مباشرةً:

```java
font.setName("Arial"); // fallback
```

بهذه الطريقة تضمن نتيجة بصرية متسقة، حتى لو تم قمع التحذير الأصلي.

---

## الأخطاء الشائعة وكيفية تجنّبها

| المشكلة | لماذا يحدث | الحل |
|---------|------------|------|
| **نسيان تعيين رد النداء** | `LoadOptions` يستخدم رد نداء لا يفعل شيئًا افتراضيًا، لذا تختفي التحذيرات. | دائمًا استدعِ `loadOptions.setWarningCallback(...)` قبل التحميل. |
| **استخدام نوع تحذير خاطئ** | `WarningType.SUBSTITUTED_FONT` هو النوع الوحيد الذي يشير إلى الخطوط المفقودة. | صَفِّ على `WarningType.SUBSTITUTED_FONT` *بالضبط*؛ الأنواع الأخرى (مثل `UNKNOWN_FILE_FORMAT`) غير ذات صلة. |
| **تحديد مسارات ملفات ثابتة** | يعمل محليًا لكنه يفشل في خطوط CI/CD. | استخدم مسارًا نسبيًا أو مرّر موقع الملف كمعامل سطر أوامر. |
| **تجاهل الخطوط Unicode** | بعض الخطوط المفقودة تكون مشكلة فقط لبعض الأحرف. | اختبر بمستند يحتوي على مجموعة الأحرف الكاملة التي تتوقع دعمها. |
| **التشغيل على خادم بدون إعداد خطوط** | قد يفتقر الخادم إلى أي خطوط احتياطية، مما يسبب استبدالات غير متوقعة. | ثبّت مجموعة بسيطة من الخطوط الشائعة (Arial, Times New Roman) على الخادم. |

---

## توسيع الحل

الآن بعد أن يمكنك **التقاط تحذيرات استبدال الخط**، قد ترغب في:

* **تسجيل التحذيرات إلى ملف** – استبدل `System.out.println` بمسجل مثل SLF4J.
* **رمي استثناء** – مفيد في خطوط الأنابيب الآلية حيث يجب أن يفشل البناء عند وجود خط مفقود:

```java
if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
    throw new RuntimeException("Missing font detected: " + info.getDescription());
}
```

* **تثبيت الخطوط المفقودة تلقائيًا** – حمّل ملف TTF/OTF المطلوب أثناء التشغيل وأضفه إلى `GraphicsEnvironment` في Java. هذا سيناريو أكثر تقدمًا، لكنه ممكن تمامًا.

---

## المخطط (اختياري)

![Capture font substitution warnings flow diagram showing LoadOptions → WarningCallback → Console output](capture-font-substitution-warnings-diagram.png)

*نص بديل:* “مخطط تدفق يوضح كيفية توجيه Aspose.Words لتحذيرات الخط المفقود إلى رد نداء مخصص.”

---

## الخلاصة

لقد غطينا للتو كيفية **التقاط تحذيرات استبدال الخط** و**اكتشاف الخطوط المفقودة** عند تحميل مستندات Word باستخدام Aspose.Words for Java. من خلال تكوين كائن `LoadOptions` وتنفيذ `IWarningCallback` صغير، تحصل على رؤية كاملة لعملية استبدال الخطوط، مما يتيح لك تسجيلها، استبدالها، أو إيقاف العملية عند نقص الخطوط.

باختصار: عيّن رد النداء، صَفِّ على `SUBSTITUTED_FONT`، حمّل المستند، وتعامل مع الناتج حسب احتياجات تطبيقك. من هنا يمكنك التوسع إلى أطر تسجيل، فحوصات CI، أو حتى توفير الخطوط تلقائيًا.

هل تريد التعمق أكثر؟ جرّب:

* **ضم الخطوط** مباشرةً إلى المستند المحفوظ (`doc.save(..., SaveOptions.createSaveOptions(SaveFormat.DOCX))` مع `FontEmbeddingMode.EMBED_ALL`).
* **إنشاء PDF** بعد تصحيح الخطوط، لضمان أن المخرجات النهائية تبدو كما هو متوقع.
* **مسح مجلد كامل** من المستندات للبحث عن خطوط مفقودة وإنتاج تقرير ملخص.

هذا كل شيء الآن—برمجة سعيدة، ولتظهر مستنداتك دائمًا بالخط المناسب!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}