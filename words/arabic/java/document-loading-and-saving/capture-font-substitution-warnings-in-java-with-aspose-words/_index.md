---
category: general
date: 2026-06-27
description: تعلم كيفية التقاط تحذيرات استبدال الخطوط في Java باستخدام Aspose.Words.
  يغطي هذا الدليل خطوة بخطوة أيضًا استدعاءات التحذير واستخدام LoadOptions.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words warning callback
- Java LoadOptions example
- font substitution handling
- document processing with Aspose
language: ar
og_description: التقاط تحذيرات استبدال الخطوط في جافا باستخدام Aspose.Words. اتبع
  هذا الدليل لإعداد ردود التحذير، واستخدام LoadOptions، ومعالجة الخطوط المفقودة.
og_title: التقاط تحذيرات استبدال الخطوط في جافا – دليل Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to capture font substitution warnings in Java using Aspose.Words.
    This step‑by‑step tutorial also covers warning callbacks and LoadOptions usage.
  headline: Capture Font Substitution Warnings in Java with Aspose.Words – Complete
    Guide
  type: TechArticle
- questions:
  - answer: Yes. The warning callback is format‑agnostic; it fires for any document
      type that Aspose.Words loads (DOC, DOCX, RTF, HTML, etc.). The only difference
      is the set of warnings that may appear.
    question: Does this work with PDF or other formats?
  - answer: Absolutely. Inside the `warning` method, inspect `info.getWarningType()`
      for other enum values such as `WarningType.IMAGE_RESOLUTION`. Then handle them
      accordingly.
    question: Can I capture other warning types, like *image resolution* warnings?
  - answer: 'Store each `info.getDescription()` in a `List<String>` inside the callback.
      After loading, you’ll have a collection you can log, send to a monitoring service,
      or use to trigger a font‑download routine. ## Conclusion You now know **how
      to capture font substitution warnings** in Java using Aspose.Word'
    question: What if I need the list of substituted fonts after the document loads?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Document Conversion
title: التقاط تحذيرات استبدال الخطوط في جافا باستخدام Aspose.Words – الدليل الكامل
url: /ar/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# التقاط تحذيرات استبدال الخطوط في Java باستخدام Aspose.Words – دليل كامل

هل احتجت يومًا إلى **التقاط تحذيرات استبدال الخطوط** أثناء تحميل ملف DOCX يستخدم خطوطًا نادرة؟ لست وحدك. في العديد من المشاريع الواقعية—مثل مولدات التقارير الآلية أو محولات المستندات الدفعية—تؤدي الخطوط المفقودة إلى استبدالات صامتة يمكن أن تفسد دقة التخطيط.  

لحسن الحظ، توفر لك Aspose.Words طريقة نظيفة للاستماع إلى تلك التحذيرات. في هذا البرنامج التعليمي سنستعرض كيفية تكوين **LoadOptions**، وربط **Aspose.Words warning callback**، وطباعة كل إشعار *استبدال خط* إلى وحدة التحكم. في النهاية ستعرف بالضبط متى تم استبدال خط وكيفية التعامل معه برمجيًا.

> **ما ستحصل عليه:** مقطع Java قابل للتنفيذ بالكامل، شرح *لماذا* كل جزء مهم، ونصائح للتعامل مع الحالات الخاصة مثل مجلدات الخطوط المخصصة.

## المتطلبات المسبقة وما ستحتاجه

قبل أن نبدأ، تأكد من وجود ما يلي:

- Java 8 أو أحدث (الكود يعمل أيضًا مع Java 11+).
- أحدث ملف JAR لـ Aspose.Words for Java (حمّله من الموقع الرسمي أو Maven Central).
- ملف DOCX يحتوي على خطوط غير مثبتة على جهازك (مثلاً *font‑rich.docx* الموجود في مجموعة عروض Aspose).
- بيئة تطوير متكاملة (IntelliJ IDEA، Eclipse، أو حتى VS Code مع ملحقات Java).

لا توجد مكتبات خارجية مطلوبة بخلاف Aspose.Words، والمثال يعمل داخل طريقة `main` عادية.

## الخطوة 1: إعداد LoadOptions – نقطة الدخول للتحميل المخصص

`LoadOptions` هي حقيبة إعدادات Aspose.Words التي تخبر المكتبة *كيف* تقرأ المستند. بشكل افتراضي، تستبدل الخطوط المفقودة صامتًا، لكن يمكنك تغيير هذا السلوك باستخدام رد نداء التحذير.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to customize loading behavior
        LoadOptions loadOptions = new LoadOptions();
```

**لماذا هذا مهم:** بدون `LoadOptions`، يتم تحميل المستند بهدوء، وتفقد القدرة على رؤية الخطوط المفقودة. بإنشاء نسخة تحصل على نقطة ربط لنظام التحذير.

## الخطوة 2: تعريف رد نداء التحذير *لالتقاط تحذيرات استبدال الخطوط*

تُرسل Aspose.Words أحداث التحذير عبر واجهة `IWarningCallback`. نفّذها داخلًا (أو كفئة منفصلة) وقم بفلترة `WarningType.FONT_SUBSTITUTION`.

```java
        // Step 2: Define a warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Only react to font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });
```

**الشرح:**  
- `info.getWarningType()` يُظهر لك فئة التحذير.  
- `WarningType.FONT_SUBSTITUTION` هو قيمة الـ enum التي نهتم بها.  
- `info.getDescription()` يحتوي على رسالة قابلة للقراءة للبشر، مثل *“Font 'Comic Sans MS' not found, substituted with 'Arial'.”*  

بطباعة الوصف، **تلتقط تحذيرات استبدال الخطوط** في الوقت الفعلي.

## الخطوة 3: تحميل المستند باستخدام LoadOptions المُكوَّن

الآن بعد أن تم إعداد رد النداء، حمّل ملف DOCX. سيُطلق رد النداء تلقائيًا أثناء التحليل.

```java
        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);
```

استبدل `YOUR_DIRECTORY` بالمسار الفعلي لملف الاختبار الخاص بك. عندما يُنفّذ مُنشئ `Document`، أي خط مفقود سيُفعّل رد النداء المُعرّف سابقًا، وسترى رسائل الاستبدال على وحدة التحكم.

## الخطوة 4: التحقق من المستند المحمَّل (اختياري لكن مفيد)

بعد التحميل، قد ترغب في التأكد من سلامة المستند—عدد الصفحات، استخراج النص، إلخ. هذه الخطوة ليست ضرورية لالتقاط التحذيرات، لكنها تساعدك على رؤية تأثير الاستبدالات.

```java
        // Optional: Output basic document info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + document.getPageCount());
```

إذا تم استبدال خط، قد يتغير التخطيط قليلًا؛ فحص عدد الصفحات يمكن أن يكشف عن هذه التغييرات.

## الخطوة 5: متقدم – التعامل مع الخطوط المستبدلة برمجيًا

أحيانًا لا تريد فقط تسجيل التحذير—قد تحتاج إلى تضمين خط احتياطي أو تعديل الأنماط. إليك نمطًا سريعًا يمكنك اعتماده.

```java
        // Advanced: Register a fallback font folder to reduce substitutions
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains the missing fonts
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);
```

بإشارة Aspose.Words إلى مجلد يحتوي على الخطوط الأصلية، يمكنك *منع* الاستبدال تمامًا. إذا كان المجلد مفقودًا، يظل رد النداء يلتقط الحدث، مما يمنحك استراتيجية احتياطية.

## مثال كامل يعمل

بدمج كل ما سبق، إليك البرنامج الكامل الجاهز للتنفيذ:

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Initialize LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // Set up warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // OPTIONAL: Register a custom fonts folder to avoid substitution
        FontSettings fontSettings = new FontSettings();
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);

        // Load the document – warnings will be printed automatically
        Document doc = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);

        // Verify basic info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + doc.getPageCount());
    }
}
```

**الناتج المتوقع على وحدة التحكم** (عند مواجهة خط مفقود):

```
Font substituted: Font 'Pacifico' not found, substituted with 'Arial'.
Document loaded successfully.
Page count: 3
```

إذا كانت جميع الخطوط موجودة، يبقى رد النداء صامتًا—لا يُطبع شيء، وهذا هو السلوك المتوقع.

## الأخطاء الشائعة ونصائح الخبراء

| المشكلة | لماذا تحدث | الحل |
|---------|------------|------|
| **رد النداء لا يُنفّذ أبدًا** | نسيت ربط رد النداء بـ `LoadOptions` **أو** استخدمت المُنشئ الافتراضي لـ `Document` دون تمرير `loadOptions`. | احرص دائمًا على استدعاء `loadOptions.setWarningCallback(...)` **واستخدام** النسخة `new Document(path, loadOptions)`. |
| **الكثير من التحذيرات يملأ السجل** | المستندات الكبيرة التي تحتوي على خطوط مفقودة كثيرة تُولّد تحذيرًا لكل استبدال. | قم بفلترة إضافية عبر فحص `info.getDescription()` لأسماء خطوط محددة، أو جمع التحذيرات في قائمة لمعالجتها لاحقًا. |
| **الخطوط المستبدلة تؤثر على التخطيط** | الخط الاحتياطي قد يختلف في القياسات (الحجم، التباعد). | قدم مجلد خطوط مخصص (انظر الخطوة 5) أو عدّل أنماط المستند بعد التحميل. |
| **التنفيذ على خادم بدون واجهة رسومية** | قد يعتمد الاستبدال الافتراضي على خطوط نظام غير مثبتة على الخادم. | وزّع الخطوط المطلوبة مع تطبيقك ووجّه `FontSettings` إلى ذلك المجلد. |

## الأسئلة المتكررة

**س: هل يعمل هذا مع PDF أو صيغ أخرى؟**  
ج: نعم. رد النداء غير مرتبط بالصيغ؛ يُطلق لأي نوع مستند تقوم Aspose.Words بتحميله (DOC، DOCX، RTF، HTML، إلخ). الاختلاف الوحيد هو مجموعة التحذيرات التي قد تظهر.

**س: هل يمكنني التقاط أنواع تحذيرات أخرى، مثل تحذيرات *دقة الصورة*؟**  
ج: بالتأكيد. داخل طريقة `warning`، افحص `info.getWarningType()` لقيم enum أخرى مثل `WarningType.IMAGE_RESOLUTION`. ثم عالجها حسب الحاجة.

**س: ماذا لو أردت قائمة بالخطوط المستبدلة بعد تحميل المستند؟**  
ج: احفظ كل `info.getDescription()` في `List<String>` داخل رد النداء. بعد التحميل، ستحصل على مجموعة يمكنك تسجيلها، إرسالها إلى خدمة مراقبة، أو استخدامها لتشغيل روتين تنزيل خطوط.

## الخلاصة

أنت الآن تعرف **كيفية التقاط تحذيرات استبدال الخطوط** في Java باستخدام Aspose.Words، ولماذا كل جزء من اللغز مهم، وكيفية توسيع الحل لسيناريوهات العالم الحقيقي. من خلال الاستفادة من `LoadOptions`، و`Aspose.Words warning callback`، و`FontSettings` الاختيارية، تحصل على رؤية كاملة للخطوط المفقودة وتستطيع الحفاظ على موثوقية خطوط تحويل المستندات.

هل أنت مستعد للخطوة التالية؟ جرّب استبدال `System.out.println` بمسجل مثل SLF4J، أو دمج قائمة التحذيرات في واجهة مستخدم تنبه المستخدمين قبل إتمام تحويل دفعة. يمكنك أيضًا استكشاف **Aspose.Words warning callback** لأنواع تحذيرات أخرى، مثل *الميزات غير المدعومة* أو تنبيهات *الصور عالية الدقة*.  

برمجة سعيدة، ولتظل ملفات PDF الخاصة بك خالية من استبدالات الخطوط غير المتوقعة! 

![لقطة شاشة تُظهر ناتج وحدة التحكم للتحذيرات الملتقطة لاستبدال الخطوط](image-placeholder.png "التقاط تحذيرات استبدال الخطوط")


## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تُكمل التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}