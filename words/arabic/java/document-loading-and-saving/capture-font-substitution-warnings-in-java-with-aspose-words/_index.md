---
category: general
date: 2026-01-11
description: تعلم كيفية التقاط تحذيرات استبدال الخطوط باستخدام Aspose.Words للغة Java.
  يغطي هذا الدليل خطوة بخطوة أيضًا خيارات التحميل واستدعاءات التحذير.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words font substitution
- Java warning callback
- LoadOptions usage
- document loading warnings
language: ar
og_description: التقاط تحذيرات استبدال الخطوط باستخدام Aspose.Words for Java. اتبع
  هذا الدليل لإعداد LoadOptions واستدعاء التحذير لتحميل المستندات بشكل موثوق.
og_title: التقاط تحذيرات استبدال الخط في جافا – دليل كامل
tags:
- Aspose.Words
- Java
- Document Processing
title: التقاط تحذيرات استبدال الخطوط في جافا باستخدام Aspose.Words – دليل كامل
url: /ar/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# التقاط تحذيرات استبدال الخط – دليل Java الكامل

هل احتجت يوماً إلى **التقاط تحذيرات استبدال الخط** عند فتح مستند Word يحتوي على خطوط مفقودة؟ هذا الأمر يسبب صداعاً شائعاً، خاصةً عندما تقوم بإنشاء ملفات PDF أو الطباعة على خادم لا يملك جميع الخطوط المثبتة. الخبر السار؟ Aspose.Words for Java يجعل الأمر سهلًا—فقط قم بتهيئة كائن `LoadOptions` وربطه بواجهة رد نداء التحذير. في هذا الدليل ستتعرف على كيفية القيام بذلك، ولماذا هو مهم، وما الذي تتوقعه عندما يتم إطلاق التحذير.

سنتطرق أيضاً إلى مواضيع ذات صلة مثل **استبدال خطوط Aspose.Words**، واستخدام **رد نداء التحذير في Java**، وأفضل الممارسات لـ **استخدام LoadOptions**. في النهاية ستحصل على مقطع جاهز للتنفيذ يسجل كل حدث خط مفقود، بحيث لا يفاجئك أي شيء في عمليات المعالجة اللاحقة.

## المتطلبات المسبقة

قبل أن نبدأ، تأكد من وجود ما يلي:

- Java 17 (أو أي JDK حديث) مثبت ومُعد.
- Aspose.Words for Java 23.10 (أو أحدث) موجود في مسار الـ classpath.
- مستند Word يشير إلى خط غير موجود محليًا (مثال: `DocWithMissingFont.docx`).
- إلمام أساسي بكتل try/catch في Java—لا شيء معقد.

إذا كان أي من هذه غير مألوف لك، خذ لحظة لتثبيت المكتبة من Maven Central:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
</dependency>
```

الآن بعد أن تم إعداد الأساسيات، لننتقل إلى الكود.

## الخطوة 1: إعداد رد نداء التحذير **للتقاط تحذيرات استبدال الخط**

أول شيء تحتاجه هو رد نداء ستستدعيه Aspose.Words كلما صادفت خطًا مفقودًا. هنا نُـ **نلتقط تحذيرات استبدال الخط**. يقوم رد النداء بتنفيذ واجهة `IWarningCallback` ويتفقد `WarningType`.

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    // Custom callback that prints details of each font substitution warning
    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            // Only act on font‑substitution warnings
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Code continues in the next steps...
    }
}
```

**لماذا هذا مهم:** بدون رد نداء، تقوم Aspose.Words باستبدال الخط المفقود بخط افتراضي بصمت، ولن تعرف أن المظهر البصري قد تغير. من خلال التقاط التحذير، يمكنك تسجيله، أو إرسال تنبيه، أو حتى إيقاف التحميل إذا كان الخط المفقود حاسمًا.

## الخطوة 2: تهيئة **LoadOptions** وتسجيل رد النداء

الآن ننشئ كائن `LoadOptions` ونربط به `FontWarningCallback` الخاص بنا. هذه الخطوة أساسية لاستخدام **LoadOptions** وتضمن أن كل تحميل مستند يمر عبر نفس مرشح التحذير.

```java
public static void main(String[] args) throws Exception {
    // Step 2: Prepare LoadOptions and hook the warning callback
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new FontWarningCallback());

    // Continue to load the document in the next step...
}
```

**نصيحة:** يمكنك إعادة استخدام نفس كائن `LoadOptions` لعدة مستندات، مما يوفر بعض الأسطر المتكررة ويضمن معالجة **تحذيرات تحميل المستند** بشكل متسق عبر تطبيقك.

## الخطوة 3: تحميل المستند ومراقبة الناتج

بعد ربط رد النداء، ما عليك سوى تحميل ملف Word. إذا كان المستند يشير إلى خط غير مثبت، سيُطلق رد النداء ويطبع التفاصيل على وحدة التحكم.

```java
    // Step 3: Load the document using the configured LoadOptions
    Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

    // Step 4: Confirm that the load completed
    System.out.println("Document loaded; check console for any font‑substitution warnings.");
}
```

### ناتج وحدة التحكم المتوقع

بافتراض أن `DocWithMissingFont.docx` يشير إلى الخط المفقود *“Comic Sans MS”*، سترى شيئًا مشابهًا لـ:

```
Font substitution warning:
  Original font: Comic Sans MS
  Substituted by: Arial
Document loaded; check console for any font‑substitution warnings.
```

إذا كان المستند **لا يحتوي على خطوط مفقودة**، ستظهر السطر الأخير فقط في وحدة التحكم، مؤكدًا أن رد النداء لم ينتج أي إنذارات زائفة.

## الخطوة 4: معالجة الحالات الخاصة والمشكلات الشائعة

### عدة خطوط مفقودة

إذا استخدم المستند عدة خطوط غير متوفرة، سيُنفّذ رد النداء مرةً لكل خط. ستحصل على سلسلة من الرسائل، كل منها يحتوي على `source` و `description` خاصين به. لا تحتاج إلى كود إضافي—فقط تأكد من أن نظام التسجيل الخاص بك يستطيع التعامل مع استدعاءات سريعة متتالية.

### كتم التحذيرات

في حالات نادرة قد ترغب في تجاهل بعض الاستبدالات (مثلاً، تعرف أن بديلًا معينًا مقبول). قم بتمديد منطق رد النداء:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION &&
    !info.getSource().equalsIgnoreCase("SomeFontYouAccept")) {
    // Log or act on the warning
}
```

### أمان الخيوط (Thread Safety)

`LoadOptions` في Aspose.Words غير آمن للخيط (thread‑safe) بشكل افتراضي. إذا كنت تقوم بتحميل مستندات بشكل متوازي، أنشئ كائن `LoadOptions` منفصل لكل خيط، أو قم بمزامنة رد النداء لتجنب حالات السباق.

## الخطوة 5: التحقق من الخط المستبدل في المستند الناتج

بعد التحميل، قد ترغب في التأكد من أن الاستبدال فعلاً حدث. تتيح لك الـ API التجول عبر جميع الـ runs وفحص اسم الخط الفعلي:

```java
for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
    System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
}
```

هذا المقتطف يطبع كل run نصي مع الخط النهائي الخاص به. إنه فحص سريع مفيد عندما تبني خطوط أنابيب تحويل PDF تلقائية.

## مثال عملي كامل

بدمج كل ما سبق، إليك البرنامج الكامل الجاهز للتنفيذ:

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Prepare LoadOptions and register the warning callback
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new FontWarningCallback());

        // Load the document (replace with your actual path)
        Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

        // Optional: verify effective fonts in the document
        for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
            System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
        }

        System.out.println("Document loaded; check console for any font‑substitution warnings.");
    }
}
```

احفظه باسم `FontSubstitutionInfo.java`، ثم قم بترجمته باستخدام `javac` وشغّله عبر `java FontSubstitutionInfo`. يجب أن ترى رسائل التحذير (إن وجدت) متبوعةً بقائمة الـ runs وخطوطها النهائية.

## دليل بصري

![لقطة شاشة لإخراج وحدة التحكم تُظهر تحذيرات استبدال الخط](/images/font-substitution-warning.png "مثال على التقاط تحذيرات استبدال الخط")

*نص بديل:* **التقاط تحذيرات استبدال الخط** – إخراج وحدة التحكم بعد تحميل مستند يحتوي على خطوط مفقودة.

## الخلاصة

أصبح بإمكانك الآن **التقاط تحذيرات استبدال الخط** باستخدام Aspose.Words for Java. من خلال تهيئة كائن `LoadOptions` وتوفير `IWarningCallback` مخصص، تحصل على رؤية كاملة لأي أحداث خطوط مفقودة قد تؤثر صامتًا على مظهر المستند. هذه التقنية تتكامل مباشرةً مع معالجة **استبدال خطوط Aspose.Words**، وتضمن تحذيرات تحميل مستند موثوقة، وتمنحك المرونة لتسجيلها أو تنبيهها أو إيقافها وفقًا لقواعد عملك.

### ما التالي؟

- استكشف أنماط **رد نداء التحذير في Java** لأنواع تحذيرات أخرى (مثل `DEPRECATED_FEATURE`).
- اجمع هذه الطريقة مع **تحويل PDF** لضمان أن الخطوط المستبدلة لا تُفسد التخطيط.
- تعمق أكثر في **استخدام LoadOptions**—جرّب `Password`، `Encoding`، و `ResourceLoadingCallback` لسيناريوهات أكثر تقدماً.

لا تتردد في تعديل رد النداء، توجيه التحذيرات إلى إطار تسجيل، أو حتى رمي استثناء مخصص إذا كان خط حاسم مفقود. السماء هي الحد، والآن لديك أساس صلب للبناء عليه.

برمجة سعيدة، ولتظهر مستنداتك دائمًا كما تتوقع!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}