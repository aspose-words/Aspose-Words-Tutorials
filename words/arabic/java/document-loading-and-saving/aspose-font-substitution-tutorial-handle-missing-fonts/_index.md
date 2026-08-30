---
category: general
date: 2026-05-04
description: يوضح دليل استبدال الخطوط في Aspose كيفية التعامل مع الخطوط المفقودة في
  Java باستخدام ردود التحذير وLoadOptions لتحميل المستندات بشكل موثوق.
draft: false
keywords:
- aspose font substitution tutorial
- handle missing fonts
- Aspose.Words font warning callback
- Java LoadOptions warning handling
- missing font detection Aspose
language: ar
og_description: يوضح دليل استبدال الخطوط في Aspose كيفية التعامل مع الخطوط المفقودة
  في Java، والتقاط أحداث الاستبدال، والحفاظ على مظهر مستنداتك صحيحًا.
og_title: دليل استبدال الخطوط في Aspose – التعامل مع الخطوط المفقودة
tags:
- Aspose.Words
- Java
- Font Management
title: دليل استبدال الخطوط في Aspose – التعامل مع الخطوط المفقودة
url: /ar/java/document-loading-and-saving/aspose-font-substitution-tutorial-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# برنامج Aspose لاستبدال الخطوط – التعامل مع الخطوط المفقودة

هل احتجت إلى **دروس استبدال الخطوط في Aspose** لأن ملف DOCX تقوم بتحميله يظهر بشكل غير صحيح فجأة؟ لست وحدك—الخطوط المفقودة مصدر خفي للأخطاء يمكن أن يحول تقريرًا منسقًا إلى فوضى مشوشة. الخبر السار هو أن Aspose.Words يوفّر لك طريقة نظيفة **للتعامل مع الخطوط المفقودة** قبل أن تُفسد التخطيط.

في هذا الدليل سنستعرض مثالًا كاملًا جاهزًا للتنفيذ بلغة Java يلتقط تحذيرات استبدال الخطوط، يشرح لماذا كل جزء مهم، ويظهر لك كيفية التحقق من النتيجة. بنهاية القراءة ستعرف بالضبط كيف تحافظ على مظهر مستنداتك حادًا حتى عندما لا تكون الخطوط الأصلية موجودة على الجهاز.

## ما ستتعلمه

- كيفية تسجيل `IWarningCallback` مخصص يستمع لأحداث `FONT_SUBSTITUTION`.  
- لماذا يُعد استخدام `LoadOptions` النهج الموصى به لمعالجة الخطوط بشكل موثوق.  
- طرق اختبار الحل باستخدام مستند متعمد الفشل.  
- الأخطاء الشائعة (مثل نسيان تعيين الـ callback) والحلول السريعة.  

**المتطلبات المسبقة**: تثبيت Java 8+، رخصة صالحة لـ Aspose.Words for Java (أو النسخة التجريبية المجانية)، وبيئة تطوير متكاملة مثل IntelliJ أو Eclipse. لا تحتاج إلى مكتبات خارجية أخرى.

---

![مخطط درس استبدال الخطوط في Aspose](https://example.com/images/font-substitution-diagram.png "مخطط درس استبدال الخطوط في Aspose")

## الخطوة 1 – تعريف Callback للتحذير لالتقاط عمليات الاستبدال  

أول شيء تقوم به Aspose.Words عندما لا يستطيع العثور على الخط المطلوب هو إطلاق حدث `WarningInfo`. من خلال تنفيذ `IWarningCallback` يمكنك تسجيله، عرضه، أو حتى إلغاء التحميل إذا رغبت.

```java
// Step 1: Create a callback that prints font‑substitution warnings
class FontWarningCollector implements IWarningCallback {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
}
```

**لماذا هذا مهم** – بدون Callback لن تعرف أبدًا أن Aspose استبدل *Arial* بـ *Liberation Sans* (أو أي خط بديل اختاره). هذا الاستبدال الصامت يمكن أن يسبب تحولات في التخطيط، خاصةً في الجداول أو التخطيطات متعددة الأعمدة.

---

## الخطوة 2 – ربط الـ Callback بـ `LoadOptions`

`LoadOptions` هو المركز الرئيسي لكل ما يؤثر على طريقة قراءة المستند. من خلال توصيل الـ Callback هنا تضمن أن **أي** مستند يُحمَّل بهذه الخيارات سيُطلق منطق التحذير الخاص بك.

```java
// Step 2: Wire the callback into LoadOptions
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new FontWarningCollector());
```

**نصيحة** – إذا كنت تخطط لتحميل عدة مستندات دفعة واحدة، أعد استخدام نفس كائن `LoadOptions`. هذا يوفر تكلفة إنشاء الكائنات ويحافظ على توحيد سجلاتك.

---

## الخطوة 3 – تحميل مستند قد يحتاج إلى استبدال الخطوط  

الآن نقوم بقراءة ملف نعلم أنه يفتقد خطًا ما. استبدل `YOUR_DIRECTORY` بالمجلد الذي يحتوي على ملفات الاختبار الخاصة بك.

```java
// Step 3: Load a document that deliberately references a missing font
String inputPath = "YOUR_DIRECTORY/missing-font.docx";
Document doc = new Document(inputPath, loadOptions);
```

عندما يصادف المحمل حرفًا لا يمكن عرضه، يقوم الـ Callback من **الخطوة 1** بطباعة رسالة ودية إلى وحدة التحكم. مثال:

```
Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

**حالة حدية** – إذا كان المستند يحتوي على خطوط **مضمنة**، ستستخدم Aspose تلك أولًا وتتخطى التحذير. هذا سلوك متوقع؛ ترى التحذيرات فقط للخطوط المفقودة فعليًا.

---

## الخطوة 4 – حفظ المستند (الآن مع الخطوط المستبدلة)

بعد انتهاء التحميل، تكون Aspose قد استبدلت الخطوط المفقودة داخليًا. حفظ المستند يحافظ على الاستبدال، لذا سيظهر الناتج تمامًا كما رأيت في وحدة التحكم.

```java
// Step 4: Persist the document – the fonts are already substituted if needed
String outputPath = "YOUR_DIRECTORY/loaded.docx";
doc.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

افتح `loaded.docx` في Word أو LibreOffice وستلاحظ أن التخطيط لم يتغير، رغم أن الخط الأصلي غير مثبت على جهازك.

---

## الخطوة 5 – التحقق من النتيجة برمجيًا (اختياري)

إذا أردت التأكد تمامًا من عدم وجود استبدالات غير متوقعة، يمكنك الاستعلام عن جدول الخطوط في المستند بعد التحميل.

```java
// Optional: List all fonts actually used in the saved document
for (FontInfo fontInfo : doc.getFontInfos()) {
    System.out.println("Used font: " + fontInfo.getFontName());
}
```

يجب أن يحتوي الإخراج على الخط البديل (مثل *Arial*) بدلًا من الخط المفقود. هذا مفيد لسلاسل الأنابيب الآلية حيث تحتاج إلى ضمان أن الـ PDF أو DOCX النهائي يلتزم بمتطلبات العلامة التجارية.

---

## نصائح احترافية ومخاطر شائعة

- **نصيحة احترافية:** عيّن `loadOptions.setFontSettings(new FontSettings())` إذا كنت بحاجة لتوجيه Aspose إلى مجلد خطوط مخصص قبل التحميل. هذا يقلل عدد الاستبدالات.  
- **احذر من:** نسيان استدعاء `setWarningCallback`. سيستمر الكود في التنفيذ، لكنك ستفقد رسائل التشخيص الحيوية.  
- **ملاحظة أداء:** تحميل مستندات كبيرة تحتوي على العديد من الخطوط المفقودة قد يولد الكثير من التحذيرات. فكر في تقليل الإخراج أو الكتابة إلى ملف سجل بدلاً من `System.out`.  
- **ماذا لو أردت إلغاء التحميل عند الاستبدال؟** استبدل استدعاء `System.out.println` بـ `throw new RuntimeException(info.getDescription())` داخل الـ Callback. هذا يجبر التحميل على الفشل، وهو مفيد لسيناريوهات الالتزام الصارم.

---

## الأسئلة المتكررة

**س: هل يعمل هذا مع صيغ PDF أو الصور؟**  
ج: الـ Callback مخصص لمرحلة التحميل الخاصة بصيغ معالجة Word (`.docx`, `.doc`, `.rtf`, إلخ). معالجة PDF تستخدم خط أنابيب مختلف، لكن لا يزال بإمكانك التقاط تحذيرات متعلقة بالخطوط عبر `PdfLoadOptions`.

**س: هل يمكنني استبدال خط محدد بآخر من اختياري؟**  
ج: نعم. أنشئ كائن `FontSettings`، استدعِ `fontSettings.getSubstitutionSettings().getTableSubstitutes().addSubstitutes("MissingFont", "MyPreferredFont")`، ثم عيّنها إلى `loadOptions.setFontSettings(fontSettings)`.

**س: هل الـ Callback آمن للاستخدام في بيئات متعددة الخيوط؟**  
ج: التنفيذ الافتراضي غير متزامن. إذا كنت تحمل مستندات بشكل متوازي، تأكد من أن تنفيذ الـ Callback يتعامل مع الوصول المتزامن (مثل استخدام `ConcurrentLinkedQueue` للتسجيل).

---

## الخلاصة

أصبح لديك الآن **دروس استبدال الخطوط في Aspose** الكامل الذي يوضح كيفية **التعامل مع الخطوط المفقودة** بأناقة في Java. من خلال تعريف `IWarningCallback` مخصص، ربطه بـ `LoadOptions`، وحفظ المستند، تحافظ على اتساق المخرجات بغض النظر عن الخطوط المثبتة على الجهاز المضيف.

من هنا يمكنك استكشاف:

- جداول استبدال خطوط مخصصة لتوافق العلامة التجارية.  
- دمج مسجل التحذيرات مع SLF4J أو Log4j لتشخيصات جاهزة للإنتاج.  
- توسيع الـ Callback لجمع إحصائيات عبر دفعة من المستندات.

جرّبه، عدّل الخطوط البديلة، ودع مستنداتك تظل جميلة حتى عندما تختفي الخطوط الأصلية. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}