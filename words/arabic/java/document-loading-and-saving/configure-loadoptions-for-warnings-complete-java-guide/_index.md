---
category: general
date: 2026-06-30
description: تكوين LoadOptions للتحذيرات في Aspose.Words Java. تعلّم كيفية إعداد رد
  نداء تحذيري لاستبدال الخطوط وغيرها من تحذيرات خيارات التحميل.
draft: false
keywords:
- configure loadoptions for warnings
- Aspose.Words font substitution
- Java warning callback
- document loading options
- handle font warnings
language: ar
og_description: تكوين LoadOptions للتحذيرات في Aspose.Words Java. يوضح هذا الدليل
  كيفية التقاط تنبيهات استبدال الخطوط باستخدام رد نداء التحذير.
og_title: تكوين LoadOptions للتحذيرات – دليل Java
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Configure LoadOptions for warnings in Aspose.Words Java. Learn to set
    up a warning callback for font substitution and other load‑options warnings.
  headline: Configure LoadOptions for Warnings – Complete Java Guide
  type: TechArticle
tags:
- aspose-words
- java
- warnings
- font-substitution
title: تكوين LoadOptions للتحذيرات – دليل جافا الكامل
url: /ar/java/document-loading-and-saving/configure-loadoptions-for-warnings-complete-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تكوين LoadOptions للتحذيرات – دليل Java الكامل

هل احتجت يوماً إلى **تكوين LoadOptions للتحذيرات** عند فتح مستند Word باستخدام Aspose.Words for Java؟ لست وحدك. يواجه العديد من المطورين مشكلة عندما يتم استبدال خط مفقود بصمت، مما يجعل ملف PDF النهائي يبدو غير متطابق مع العلامة التجارية. الخبر السار؟ من خلال ربط **Java warning callback** إلى `LoadOptions` الخاص بك، يمكنك التقاط كل تنبيه استبدال خط في اللحظة التي يحدث فيها.

في هذا البرنامج التعليمي سنستعرض مثالًا عمليًا لا يوضح فقط كيفية إعداد الـ callback بل يشرح أيضًا *لماذا* كل جزء مهم. في النهاية ستتمكن من **معالجة تحذيرات الخطوط**، تسجيلها، أو حتى استبدال الخطوط مباشرةً—بدون أي تخمين.

## ما ستحصل عليه

- برنامج Java كامل قابل للتنفيذ يطبع كل تحذير استبدال خط.
- فهم آلية **استبدال خطوط Aspose.Words**.
- نصائح لتخصيص معالجة التحذيرات للمشاريع الكبيرة.
- رؤية حول **خيارات تحميل المستند** ومتى يجب تعديلها.

> **المتطلبات المسبقة:** Java 8+ ومكتبة Aspose.Words for Java (الإصدار 23.9 أو أحدث). لا توجد تبعيات خارجية أخرى مطلوبة.

---

## الخطوة 1: تكوين LoadOptions للتحذيرات

أول شيء تحتاجه هو كائن `LoadOptions` يعرف أنه يجب أن يبلغ عن التحذيرات. فكر في `LoadOptions` كصندوق الأدوات الذي تسلمه إلى Aspose.Words قبل أن يفتح الملف.

```java
// Step 1: Create LoadOptions and attach a warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font‑substitution warnings.
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

**لماذا هذا مهم:**  
`LoadOptions` يتحكم في طريقة قراءة المكتبة للمستند. من خلال تعيين `IWarningCallback`، تخبر Aspose.Words باستدعاء الكود الخاص بك كلما صادفت شيئًا يستحق الانتباه—مثل خط مفقود. بدون ذلك، ستستبدل المكتبة الخط بصمت ولن تعرف ذلك.

> **نصيحة احترافية:** إذا أردت التقاط *جميع* التحذيرات، احذف شرط `if`. الآن نركز على مشاكل الخطوط لأنها الأكثر شيوعًا في إحداث مفاجآت في التخطيط.

---

## الخطوة 2: تحميل المستند باستخدام الخيارات المكوّنة

الآن بعد أن أصبح الـ callback جاهزًا، قم بتحميل ملف `.docx` الخاص بك (أو أي تنسيق مدعوم) باستخدام نفس `LoadOptions`. هنا حيث **خيارات تحميل المستند** تبدأ فعليًا في العمل.

```java
// Step 2: Load the document with the warning‑aware LoadOptions.
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**خلف الكواليس:**  
عند تحليل Aspose.Words للملف `input.docx`، يقوم بمسح جداول الخطوط. إذا كان هناك خط مشار إليه في المستند غير مثبت على الجهاز المضيف، فإن المحرك يطلق تحذير `FONT_SUBSTITUTION`، مما يؤدي فورًا إلى تشغيل الـ callback الذي عرّفناه سابقًا.

---

## الخطوة 3: حفظ المستند – تم طباعة التحذيرات بالفعل

حفظ المستند أمر بسيط، لكنه اللحظة التي يمكنك فيها التحقق من أن الـ callback تم تشغيله بشكل صحيح. جميع التحذيرات تُطبع خلال خطوة التحميل، لذا عملية الحفظ هي مجرد تنظيف.

```java
// Step 3: Save the document. Any warnings were already printed in Step 1.
document.save("YOUR_DIRECTORY/output.docx");
```

**المخرجات المتوقعة في وحدة التحكم:**  

```
Font substitution detected: Font 'Calibri' is not installed. Substituted with 'Arial'.
Font substitution detected: Font 'Times New Roman' is not installed. Substituted with 'Liberation Serif'.
```

إذا لم ترى أي شيء، فإما أن المستند يستخدم خطوطًا مثبتة فقط، أو أن الـ callback لم يتم ربطه بشكل صحيح—تحقق مرة أخرى من الخطوة 1.

---

## الخطوة 4: توسيع الـ Callback لت **معالجة تحذيرات الخطوط** بأناقة

الطباعة إلى وحدة التحكم مناسبة للعرض التوضيحي، لكن كود الإنتاج غالبًا ما يحتاج إلى معالجة أكثر غنى: تسجيل إلى ملف، إرسال تنبيهات، أو حتى استبدال الخطوط برمجيًا.

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Log to a file (simple example)
            try (FileWriter fw = new FileWriter("font-warnings.log", true)) {
                fw.write("WARN: " + info.getDescription() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
            // Optionally replace the missing font with a fallback.
            FontSettings.getDefaultInstance().setSubstitutionSettings(
                new FontSubstitutionSettings() {{
                    getTableSubstitution().addSubstitutes("Calibri", "Arial");
                }}
            );
        }
    }
});
```

**لماذا قد تقوم بذلك:**  
ملف السجل يمنحك نظرة ما بعد الفحص، خاصةً عند معالجة دفعات من المستندات. يوضح كتلة الاستبدال الاختيارية كيفية **تكوين LoadOptions للتحذيرات** *و* التدخل لفرض سياسة الخطوط الخاصة بالمؤسسة.

---

## متقدم: التحكم في سيناريوهات **استبدال خطوط Aspose.Words** الأخرى

الـ warning callback ليس مقصورًا على الخطوط المفقودة. يمكنك أيضًا التقاط:

- **حروف Unicode غير المدعومة** (`WarningType.UNSUPPORTED_CHAR`).
- **مشكلات النصوص المعقدة** (`WarningType.COMPLEX_SCRIPT`).

فقط قم بتوسيع شرط `if`:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
    // handle fonts
} else if (info.getWarningType() == WarningType.UNSUPPORTED_CHAR) {
    System.out.println("Unsupported character: " + info.getDescription());
}
```

هذا يجعل حلك قويًا للمستندات متعددة اللغات، وهي حالة شائعة في التطبيقات العالمية.

---

## مثال كامل يعمل

فيما يلي البرنامج الكامل الجاهز للتنفيذ. الصقه في أي بيئة تطوير Java، استبدل القيم `YOUR_DIRECTORY`، ثم اضغط *Run*.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

public class FontSubstitutionDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Configure LoadOptions for warnings.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution: " + info.getDescription());

                    // Optional: Log to a file.
                    try (FileWriter fw = new FileWriter("font-warnings.log", true)) {
                        fw.write("WARN: " + info.getDescription() + System.lineSeparator());
                    } catch (IOException e) {
                        e.printStackTrace();
                    }

                    // Optional: Force a specific fallback font.
                    FontSettings.getDefaultInstance().setSubstitutionSettings(
                        new FontSubstitutionSettings() {{
                            getTableSubstitution().addSubstitutes("Calibri", "Arial");
                        }}
                    );
                }
            }
        });

        // Step 2: Load the document using the configured LoadOptions.
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Step 3: Save the document. Warnings have already been printed.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### النتيجة المتوقعة

- تطبع وحدة التحكم أي تحذيرات استبدال خطوط.
- `font-warnings.log` يحتوي على قائمة مؤرخة (إذا احتفظت بالتسجيل الاختياري).
- `output.docx` يتم حفظه بالخطوط المستبدلة، مطابقة للبديل الذي حددته.

---

## الأخطاء الشائعة وكيفية تجنّبها

| المشكلة | سبب حدوثها | الحل |
|---------|------------|------|
| **عدم ظهور أي تحذيرات** | لم يتم ربط الـ callback، أو أن المستند يستخدم خطوطًا مثبتة فقط. | تأكد من أن `loadOptions.setWarningCallback(...)` تم استدعاؤه *قبل* تحميل المستند. |
| **FileNotFoundException** على `input.docx` | المسار غير صحيح أو الملف غير موجود في حزمة المشروع. | استخدم مسارًا مطلقًا أو ضع الملف في مجلد الموارد الخاص بالمشروع. |
| **تباطؤ الأداء** عند معالجة آلاف المستندات | تسجيل مفرط إلى القرص لكل تحذير. | قم بتجميع السجلات وكتابتها على دفعات، أو قلل التسجيل إلى التحذيرات الحرجة فقط. |
| **استبدال خط غير متوقع** رغم وجود بديل | لم يتم تطبيق جدول الاستبدال في الوقت المناسب. | قم بتعيين إعدادات الاستبدال **قبل** تحميل المستند، أو استخدم `FontSettings.setSubstitutionSettings` عالميًا. |

---

## الخطوات التالية

الآن بعد أن أتقنت **تكوين LoadOptions للتحذيرات**، فكر في المواضيع التالية:

- **معالجة دفعات**: التكرار عبر مجلد من المستندات، وتجميع جميع تحذيرات الخطوط في تقرير واحد.
- **موفري خطوط مخصصين**: تحميل الخطوط من مشاركة شبكة أو موارد مدمجة بدلاً من نظام التشغيل المحلي.
- **دمج مع أطر التسجيل** مثل Log4j لتتبع على مستوى المؤسسة.
- استكشف خيارات **تحميل المستند** الأخرى مثل اكتشاف `LoadFormat` أو معالجة `Password` للملفات المحمية.

كل من هذه يبني على نفس النمط—إنشاء كائن `LoadOptions`، ربط الـ callbacks المناسبة، والسماح لـ Aspose.Words بالقيام بالعمل الشاق.

## الخلاصة

لقد غصنا بعمق في كيفية **تكوين LoadOptions للتحذيرات** في Aspose.Words for Java، إعداد **Java warning callback**، واستخدام هذه المعلومات **لمعالجة تحذيرات الخطوط** بذكاء. الكود مختصر، المفاهيم واضحة، والآن لديك أساس قوي لتوسيع معالجة التحذيرات إلى سيناريوهات أخرى مثل الأحرف غير المدعومة أو النصوص المعقدة.

جرّبه، عدّل جدول الاستبدال ليتطابق مع خطوط علامتك التجارية، وستلاحظ اختفاء استبدالات الخطوط الصامتة. برمجة سعيدة!

![مخطط يوضح تدفق تكوين LoadOptions للتحذيرات، تحميل المستند، التقاط أحداث استبدال الخطوط، وحفظ الناتج](configure-loadoptions-for-warnings-diagram.png "تدفق تكوين LoadOptions للتحذيرات")

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [التقاط تحذيرات استبدال الخطوط في Java باستخدام Aspose.Words – دليل كامل](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [كيفية ضبط LoadOptions في Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [كيفية تحميل مستندات RTF مع تكوين خيارات تحميل RTF في Aspose.Words for Java](/words/english/java/document-loading-and-saving/configuring-rtf-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}