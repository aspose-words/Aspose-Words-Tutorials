---
category: general
date: 2026-03-19
description: تعلم كيفية التقاط التحذيرات في Aspose.Words for Java واكتشاف الخطوط المفقودة.
  يوضح هذا الدليل خطوة بخطوة أيضًا كيفية التعامل مع الخطوط المفقودة بسلاسة.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to detect missing fonts
- handle missing fonts
language: ar
og_description: كيفية التقاط التحذيرات في Aspose.Words للـ Java، واكتشاف الخطوط المفقودة،
  ومعالجة الخطوط المفقودة مع مثال كامل للشفرة.
og_title: كيفية التقاط التحذيرات – اكتشاف الخطوط المفقودة في Aspose.Words
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: كيفية التقاط التحذيرات – اكتشاف الخطوط المفقودة في Aspose.Words
url: /ar/java/document-rendering/how-to-capture-warnings-detect-missing-fonts-in-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية التقاط التحذيرات – اكتشاف الخطوط المفقودة في Aspose.Words

هل تساءلت يومًا **كيف يتم التقاط التحذيرات** عندما يتم تحميل مستند Word وبعض الخطوط غير متوفرة على الجهاز؟ لست وحدك. في العديد من المشاريع الواقعية، تتسبب الخطوط المفقودة في تغييرات تخطيط صامتة، والطريقة الوحيدة لمعرفة ما حدث هي الاستماع إلى تدفق التحذيرات الذي تصدره Aspose.Words.  

في هذا الدرس سنستعرض مثالًا كاملًا جاهزًا للتنفيذ **يكشف الخطوط المفقودة**، ويظهر لك **كيفية اكتشاف الخطوط المفقودة** برمجيًا، بل ويعطيك نصيحة سريعة حول **معالجة الخطوط المفقودة** لضمان بقاء المخرجات متوقعة.

> **ملاحظة سريعة:** يعمل الكود مع Aspose.Words 23.9 (أو أحدث) ويتطلب Java 8+.

---

## ما ستحتاجه

- **Aspose.Words for Java** (اعتماد Maven/Gradle أو ملف JAR على مسار الفئة)  
- ملف Word (`input.docx`) يحتوي على إشارة إلى خط غير مثبت على نظامك (مثلاً “Comic Sans MS”)  
- بيئة تطوير Java أو إعداد سطر أوامر بسيط باستخدام `javac`/`java`  

لا توجد مكتبات أخرى مطلوبة—كل ما تحتاجه موجود داخل حزمة Aspose.Words.

---

## الخطوة 1 – إعداد LoadOptions لالتقاط التحذيرات  

لبدء الاستماع إلى التحذيرات يجب إنشاء كائن `LoadOptions`. هذا الكائن يخبر المحمل بتتبع أي مشكلات يواجهها، مثل الخطوط المفقودة.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions that will store warning information
        LoadOptions loadOptions = new LoadOptions();

        // ... the rest of the code follows
```

**لماذا هذا مهم:** بدون `LoadOptions` يستبدل المحمل الخطوط المفقودة بخط النظام الافتراضي بصمت، ولن تعرف أن استبدالًا قد حدث. تمكين التحذيرات يمنحك رؤية كاملة.

---

## الخطوة 2 – تحميل المستند باستخدام LoadOptions  

الآن نقوم بتحميل المستند فعليًا. يتم تمرير `LoadOptions` الذي أنشأناه إلى المُنشئ، لذا أي تحذير يُولد أثناء التحليل يُلتقط.

```java
        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**نصيحة محترف:** إذا كنت تعالج العديد من الملفات دفعة واحدة، أعد استخدام نفس كائن `LoadOptions` لتجنب إنشاء كائنات غير ضرورية.

---

## الخطوة 3 – التكرار على التحذيرات الملتقطة  

تخزن Aspose.Words كل تحذير ككائن `WarningInfo`. نحن نهتم فقط بالتحذيرات المتعلقة بالخطوط، لذا نقوم بفلترة `FontSubstitutionWarningInfo`.

```java
        // Step 3: Loop through all warnings generated while loading
        for (WarningInfo warning : document.getWarnings()) {
            // Step 3a: Keep only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // Step 4: Output the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());
            }
        }
    }
}
```

**التفسير:**  
- `document.getWarnings()` تُعيد قائمة بكل التحذيرات التي حدثت أثناء التحميل.  
- `FontSubstitutionWarningInfo` يحتوي على جزأين مهمين: **الخط المطلوب** (الخط الذي طلبه ملف DOCX) و**الخط الفعلي** الذي استعادت إليه Aspose.Words.  
- بطباعة كلا القيمتين، ترى فورًا أي الخطوط مفقودة وما هو الاستبدال الذي تم.

---

## الخطوة 4 – (اختياري) معالجة الخطوط المفقودة برمجيًا  

التقاط التحذيرات هو نصف القصة فقط. بمجرد معرفة أن خطًا ما مفقود، قد ترغب في **معالجة الخطوط المفقودة** عبر توفير استبدال مخصص أو تسجيل المشكلة للمراجعة لاحقًا.

```java
                // Optional: Replace the missing font with a known fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
```

**لماذا نفعل ذلك؟**  
- يضمن عرضًا متسقًا عبر الأجهزة.  
- يمنع تغييرات التخطيط غير المتوقعة في ملفات PDF أو الصور التي تُنشأ لاحقًا.  

يمكنك أيضًا تخزين تفاصيل التحذير في قاعدة بيانات، أو إرسال بريد إلكتروني إلى فريق المحتوى، أو حتى إيقاف العملية إذا كان الخط حاسمًا مفقودًا.

---

## مثال كامل يعمل  

فيما يلي البرنامج الكامل القابل للتنفيذ. ما عليك سوى استبدال `YOUR_DIRECTORY/input.docx` بمسار ملف الاختبار الخاص بك، وإضافة ملف JAR الخاص بـ Aspose.Words إلى مسار الفئة، ثم تشغيله.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // 3️⃣ Iterate through all warnings
        for (WarningInfo warning : document.getWarnings()) {
            // 3a️⃣ Filter only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // 4️⃣ Display the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());

                // 5️⃣ (Optional) Provide a custom fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
            }
        }

        // 6️⃣ Save the document if you need to see the result with the fallback applied
        document.save("output.docx");
    }
}
```

**الناتج المتوقع** (عند عدم وجود “Comic Sans MS”):

```
Requested: Comic Sans MS → Substituted: Arial
```

بعد تشغيل كود الاستبدال الاختياري، سيُظهر الملف المحفوظ `output.docx` الخط **Arial** في كل المواضع التي كان يُشار فيها إلى “Comic Sans MS” أصلاً.

---

## أسئلة شائعة وحالات حافة  

| السؤال | الجواب |
|----------|--------|
| *ماذا لو كان المستند يحتوي على عدة خطوط مفقودة؟* | سيُصدر الحلقة تحذيرًا لكل خط مفقود. يمكنك جمعها في `Map<String, String>` للمعالجة الدفعة. |
| *هل يعمل هذا مع ملفات PDF المُولدة من المستند؟* | بالتأكيد. يحدث استبدال الخط أثناء مرحلة التحميل، لذا أي تصدير لاحق (PDF، HTML، صورة) يستخدم الخطوط التي تم حلها. |
| *هل يمكنني كتم التحذيرات بدلًا من التقاطها؟* | نعم—اضبط `loadOptions.setWarningCallback(null);` لكنك ستفقد الرؤية حول الخطوط المفقودة. |
| *هل تُمسح قائمة التحذيرات بعد الحفظ؟* | مجموعة التحذيرات تتبع كائن `Document`. بعد استدعاء `document.save()`، تبقى القائمة دون تغيير ما لم تقم بإنشاء `Document` جديد. |
| *ماذا عن الخطوط المخصصة المضمنة في DOCX؟* | تُعامل الخطوط المضمنة كمتوفرة؛ ستستخدمها Aspose.Words حتى وإن لم تكن مثبتة على الجهاز المضيف. |

---

## نصائح محترف للاستخدام في الإنتاج  

- **تخزين إعدادات الخطوط مؤقتًا:** إذا كنت تعالج مئات الملفات، أنشئ `FontSettings` واحدًا مع الاستبدالات المفضلة وأعد استخدامه لتقليل الحمل.  
- **سجّل البيانات بشكل منظم:** بدلاً من `System.out` العادي، احفظ التحذيرات في سجل JSON—هذا يسهل التحليلات اللاحقة (مثل “أكثر الخطوط مفقودة”).  
- **التحقق مبكرًا:** نفّذ “تحميل جاف” سريع باستخدام `LoadOptions` قبل المعالجة الثقيلة؛ أوقف العملية مبكرًا إذا كانت الخطوط الحرجة مفقودة.  
- **سلامة الخيوط:** كائنات `Document` غير آمنة للاستخدام المتعدد الخيوط. احتفظ بمعالجة كل ملف في خيطه الخاص أو استخدم `LoadOptions` محليًا لكل خيط.  

---

## الخلاصة  

أنت الآن تعرف **كيفية التقاط التحذيرات** في Aspose.Words للـ Java، **اكتشاف الخطوط المفقودة**، و**معالجة الخطوط المفقودة** باستخدام استراتيجية استبدال نظيفة. من خلال الاستفادة من `LoadOptions` والتكرار على `document.getWarnings()`، تحصل على رؤية كاملة لأحداث استبدال الخطوط، مما يضمن أن المستندات التي تُنشئها تبدو كما هو متوقع في جميع البيئات.

هل أنت مستعد للخطوة التالية؟ جرّب توسيع هذا النمط إلى **اكتشاف الصور المفقودة**، **تتبع الميزات غير المدعومة**، أو حتى **تضمين الخطوط المفقودة تلقائيًا** في ملف الإخراج. نهج التقاط التحذيرات يعمل في العديد من سيناريوهات معالجة المستندات، مما يجعل شفرتك قوية ومُستعدة للمستقبل.

برمجة سعيدة، ولتظهر مستنداتك دائمًا بشكل جميل!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}