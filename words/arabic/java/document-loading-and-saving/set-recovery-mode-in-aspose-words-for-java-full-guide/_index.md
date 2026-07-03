---
category: general
date: 2026-07-03
description: قم بتعيين وضع الاسترداد لاستعادة ملفات Word التالفة في Java وعرض عدد
  الصفحات بعد التحميل. تعلم خطوة بخطوة مع Aspose.Words.
draft: false
keywords:
- set recovery mode
- display page count
- recover corrupted word
- Aspose.Words Java
- document loading options
language: ar
og_description: قم بتعيين وضع الاسترداد في Aspose.Words for Java لاستعادة ملفات Word
  التالفة وعرض عدد الصفحات. تابع المثال الكامل الآن.
og_title: تعيين وضع الاسترداد في Aspose.Words للجافا – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Set recovery mode to recover corrupted Word files in Java and display
    page count after loading. Learn step‑by‑step with Aspose.Words.
  headline: Set Recovery Mode in Aspose.Words for Java – Full Guide
  type: TechArticle
- description: Set recovery mode to recover corrupted Word files in Java and display
    page count after loading. Learn step‑by‑step with Aspose.Words.
  name: Set Recovery Mode in Aspose.Words for Java – Full Guide
  steps:
  - name: Why `RecoveryMode.PARSE`?
    text: '- **PARSE** – Aspose.Words parses whatever fragments it can understand,
      stitching together a partially functional document. Ideal when you need *any*
      content out of a broken file. - **SKIP** – The library skips over corrupted
      sections entirely, which can be faster but may discard more data.'
  - name: 1️⃣ Corrupted Header/Footer Sections
    text: Sometimes only the main body parses while headers and footers are lost.
      If you rely on those for branding, you may need to re‑inject them after recovery.
  - name: 2️⃣ Images That Won’t Load
    text: Embedded images often get stripped out when the zip container (the underlying
      `.docx` format) is damaged. You can catch this by iterating over `doc.getSections()`
      and checking `Section.getBody().getParagraphs()` for `Shape` objects.
  - name: 3️⃣ Large Documents and Memory
    text: Recovering a 200‑page corrupted file can be memory‑intensive. Consider increasing
      the JVM heap size (`-Xmx2g`) when you anticipate huge documents.
  - name: 4️⃣ License Restrictions
    text: The evaluation version caps certain features, but **recovery** is fully
      functional. However, the printed page count may be limited to a few pages in
      the trial. Always test with a licensed build for production.
  - name: Maven `pom.xml` snippet
    text: '```xml <dependency> <groupId>com.aspose</groupId> <artifactId>aspose-words</artifactId>
      <version>23.12</version> </dependency> ```'
  - name: Java source file `RecoveryModeDemo.java`
    text: '```java import com.aspose.words.*;'
  type: HowTo
- questions:
  - answer: That usually means the file is beyond salvage—perhaps the zip container
      is completely broken. In such cases, you might need a third‑party repair tool
      before handing it to Aspose.Words.
    question: What if `RecoveryMode.PARSE` still throws an exception?
  - answer: 'Absolutely. Implement `IWarningCallback` to capture any warnings Aspose.Words
      emits during the parsing process. This gives you insight into which parts were
      skipped. ```java loadOptions.setWarningCallback(new IWarningCallback() { public
      void warning(WarningInfo info) { System.out.println("Warning: "'
    question: Can I combine `RecoveryMode.PARSE` with custom document loading callbacks?
  - answer: 'No. Aspose.Words works on a copy in memory; the source file remains untouched
      unless you explicitly call `doc.save()`. --- ## ## Wrap‑Up We’ve covered how
      to **set recovery mode** in Aspose.Words for Java, why `PARSE` is generally
      the best choice for salvaging a broken document, and how to **display'
    question: Does changing the recovery mode affect the original file?
  type: FAQPage
tags:
- Java
- Aspose.Words
- Word recovery
title: تعيين وضع الاسترداد في Aspose.Words للـ Java – دليل كامل
url: /ar/java/document-loading-and-saving/set-recovery-mode-in-aspose-words-for-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تعيين وضع الاسترداد في Aspose.Words للـ Java – دليل كامل

هل تساءلت يومًا كيف **تعيين وضع الاسترداد** عند تحميل ملف `.docx` تالف باستخدام Aspose.Words؟ لست الوحيد الذي يحك رأسه بسبب مستندات Word الفاسدة التي ترفض الفتح. في هذا الدرس سنستعرض ذلك بالضبط — كيفية تكوين المكتبة **لاستعادة ملفات Word الفاسدة** ثم **عرض عدد الصفحات** للمحتوى الذي تم تحميله بنجاح.

سنغطي كل شيء من تعديل `LoadOptions` الصغير إلى السطر النهائي `System.out.println` الذي يخبرك بعدد الصفحات التي نجت من مهمة الإنقاذ. لا إطالة، مجرد حل عملي جاهز للنسخ واللصق يعمل مع أحدث إصدار Aspose.Words 23.12.

## ما ستتعلمه

- لماذا وضع الاسترداد مهم وأي خيارات تقدمها Aspose.Words.  
- كيف **تعيين وضع الاسترداد** برمجياً باستخدام Java.  
- طرق **عرض عدد الصفحات** بعد تحميل المستند، لتأكيد نجاح الاسترداد.  
- المشكلات الشائعة عند التعامل مع ملفات Word الفاسدة وكيفية تجنبها.  

قبل أن نبدأ، تأكد من أن لديك:

1. رخصة صالحة لـ Aspose.Words للـ Java (أو مفتاح تقييم مؤقت).  
2. Java 17 أو أحدث مثبت على جهازك.  
3. ملف `Corrupted.docx` الفاسد الذي تريد اختباره.  

هل لديك هذه؟ رائع—لنبدأ العمل.

> **نصيحة احترافية:** حتى إذا كنت تستخدم نسخة تجريبية، فإن ميزات الاسترداد تعمل بنفس الطريقة كما في نسخة مرخصة.

---

## ## كيفية تعيين وضع الاسترداد مع Aspose.Words للـ Java

جوهر الحل يكمن في فئة `LoadOptions`. بشكل افتراضي، تحاول Aspose.Words بأقصى ما لديها تحميل المستند، ولكن عندما يكون الملف مكسورًا بشكل كبير تحتاج إلى إخبارها *كيف* تتصرف. هنا يأتي دور **تعيين وضع الاسترداد**.

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a LoadOptions instance – this object holds all the loading preferences.
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Choose the recovery mode. PARSE attempts to salvage as much as possible,
        //    while SKIP simply skips unreadable parts.
        loadOptions.setRecoveryMode(RecoveryMode.PARSE);

        // 3️⃣ Load the document using the configured options.
        Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // 4️⃣ Finally, display the number of pages that were successfully recovered.
        System.out.println("Document loaded, page count = " + doc.getPageCount());
    }
}
```

### لماذا `RecoveryMode.PARSE`؟

- **PARSE** – تقوم Aspose.Words بتحليل أي شظايا يمكنها فهمها، وتجميعها في مستند جزئي الوظيفة. مثالي عندما تحتاج إلى *أي* محتوى من ملف مكسور.  
- **SKIP** – تتخطى المكتبة الأقسام الفاسدة بالكامل، مما قد يكون أسرع لكنه قد يتخلص من المزيد من البيانات.  

في معظم السيناريوهات الواقعية، يعتبر **PARSE** الخيار الأكثر أمانًا لأنه يزيد من كمية النصوص والصور والتنسيقات القابلة للاسترداد.

---

## ## عرض عدد الصفحات بعد الاسترداد

بمجرد تحميل المستند، الخطوة المنطقية التالية هي التحقق من نجاح العملية. أبسط مقياس، لكنه الأكثر إخبارًا، هو عدد الصفحات. طريقة `Document.getPageCount()` تقوم بذلك بالضبط.

```java
int pages = doc.getPageCount();
System.out.println("Document loaded, page count = " + pages);
```

إذا كان الملف غير قابل للقراءة تمامًا، ستطرح Aspose.Words استثناءً *قبل* أن تصل إلى هذا السطر. عندما ترى عدد صفحات يساوي `0` أو رقمًا منخفضًا جدًا، فهذا يعني عادةً أن وضع الاسترداد اضطر إلى حذف أجزاء كبيرة من الملف الأصلي.

**الإخراج المتوقع (مثال):**

```
Document loaded, page count = 12
```

هذا يخبرك أن المكتبة نجحت في إعادة بناء اثني عشر صفحة من المصدر الفاسد—وذلك إنجاز جيد لملف `.docx` مكسور.

---

## ## حالات الحافة والمشكلات الشائعة

### 1️⃣ أقسام رأس/تذييل الفاسدة

أحيانًا يتم تحليل النص الرئيسي فقط بينما تُفقد رؤوس وتذييلات الصفحات. إذا كنت تعتمد عليها للعلامة التجارية، قد تحتاج إلى إعادة حقنها بعد الاسترداد.

### 2️⃣ الصور التي لا تُحمَّل

غالبًا ما تُزال الصور المدمجة عندما يتضرر حاوية zip (تنسيق `.docx` الأساسي). يمكنك اكتشاف ذلك عن طريق التكرار عبر `doc.getSections()` والتحقق من `Section.getBody().getParagraphs()` للعثور على كائنات `Shape`.

```java
for (Section sec : doc.getSections()) {
    for (Paragraph para : sec.getBody().getParagraphs()) {
        for (Node node : para.getChildNodes(NodeType.SHAPE, true)) {
            Shape shape = (Shape) node;
            System.out.println("Found image: " + shape.getName());
        }
    }
}
```

إذا لم يطبع الحلقة أي شيء، فمن المحتمل أن وضع الاسترداد قد تخطى الصور.

### 3️⃣ المستندات الكبيرة والذاكرة

استعادة ملف فاسد يحتوي على 200 صفحة قد يستهلك الكثير من الذاكرة. فكر في زيادة حجم كومة JVM (`-Xmx2g`) عندما تتوقع مستندات ضخمة.

### 4️⃣ قيود الترخيص

الإصدار التجريبي يحد من بعض الميزات، لكن **الاسترداد** يعمل بالكامل. ومع ذلك، قد يكون عدد الصفحات المطبوعة محدودًا ببضع صفحات في النسخة التجريبية. اختبر دائمًا باستخدام نسخة مرخصة للإنتاج.

---

## ## مثال كامل من البداية إلى النهاية (قابل للتنفيذ)

فيما يلي برنامج مستقل يمكنك وضعه في أي مشروع Maven أو Gradle. يتضمن إعلان الاعتماد الضروري لـ Aspose.Words 23.12.

### Maven `pom.xml` مقتطف

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### ملف مصدر Java `RecoveryModeDemo.java`

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) {
        try {
            // Initialize load options
            LoadOptions loadOptions = new LoadOptions();

            // Set recovery mode to PARSE – this is the key step to recover corrupted Word files.
            loadOptions.setRecoveryMode(RecoveryMode.PARSE);

            // Load the possibly damaged document
            Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

            // Display the page count to confirm how much content was recovered.
            System.out.println("Document loaded, page count = " + doc.getPageCount());

            // (Optional) Save the recovered document for further inspection.
            doc.save("YOUR_DIRECTORY/Recovered.docx");
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**ما يفعله هذا:**

1. يعيّن وضع الاسترداد – جوهر الدرس.  
2. يقوم بتحميل الملف الفاسد باستخدام `LoadOptions` المُكوَّنة.  
3. **يعرض عدد الصفحات**، مما يمنحك تغذية راجعة فورية.  
4. يحفظ نسخة مُنقّاة (`Recovered.docx`) لتتمكن من فتحها في Word لاحقًا.

شغّل البرنامج باستخدام:

```bash
javac -cp "path/to/aspose-words-23.12.jar" RecoveryModeDemo.java
java -cp ".:path/to/aspose-words-23.12.jar" RecoveryModeDemo
```

يجب أن ترى عدد الصفحات يُطبع على وحدة التحكم، مما يؤكد نجاح الاسترداد.

---

## ## نظرة بصرية (صورة)

![مخطط تدفق تعيين وضع الاسترداد](https://example.com/images/recovery-mode-flow.png "مخطط يوضح كيفية عمل تعيين وضع الاسترداد في Aspose.Words للـ Java")

*يتضمن النص البديل الكلمة المفتاحية الأساسية **set recovery mode** لتلبية متطلبات تحسين محركات البحث.*

---

## ## الأسئلة المتكررة

**س: ماذا لو استمر `RecoveryMode.PARSE` في طرح استثناء؟**  
ج: عادةً ما يعني ذلك أن الملف لا يمكن إنقاذه—ربما تكون حاوية zip مكسورة تمامًا. في مثل هذه الحالات، قد تحتاج إلى أداة إصلاح من طرف ثالث قبل تمريره إلى Aspose.Words.

**س: هل يمكنني دمج `RecoveryMode.PARSE` مع ردود نداء تحميل المستند المخصصة؟**  
ج: بالتأكيد. نفّذ `IWarningCallback` لالتقاط أي تحذيرات تصدرها Aspose.Words أثناء عملية التحليل. هذا يمنحك نظرة على الأجزاء التي تم تخطيها.

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    public void warning(WarningInfo info) {
        System.out.println("Warning: " + info.getDescription());
    }
});
```

**س: هل يؤثر تغيير وضع الاسترداد على الملف الأصلي؟**  
ج: لا. تعمل Aspose.Words على نسخة في الذاكرة؛ يبقى الملف الأصلي دون تعديل ما لم تقم صراحةً باستدعاء `doc.save()`.

---

## ## الخلاصة

لقد غطينا كيفية **تعيين وضع الاسترداد** في Aspose.Words للـ Java، ولماذا يعتبر `PARSE` عادةً الخيار الأفضل لإنقاذ مستند مكسور، وكيفية **عرض عدد الصفحات** للتحقق من النتيجة. باتباع المثال الكامل، لديك الآن حل جاهز للتنفيذ يمكنه **استعادة ملفات Word الفاسدة** وتزويدك بتغذية راجعة فورية حول نجاح العملية.

الخطوات التالية؟ جرّب استبدال `RecoveryMode.SKIP` لتلاحظ الفرق، جرب مع ملفات متعددة الأقسام وكبيرة الحجم، أو دمج المنطق في خدمة ويب تقوم تلقائيًا بإصلاح المستندات التي يرفعها المستخدمون. نفس النمط يعمل مع ملفات PDF (باستخدام Aspose.PDF) وحتى مع استعادة النص العادي باستخدام مكتبات أخرى—فقط تذكر الفكرة الأساسية: ضبط المحمل، محاولة الاسترداد، ثم التحقق باستخدام مقياس بسيط مثل عدد الصفحات.

برمجة سعيدة، ولتظل مستنداتك سليمة!

---

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شاملة من الكود مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية تعيين LoadOptions في Aspose.Words للـ Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Aspose.Words Java: دليل شامل لمعالجة مستندات Word](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [دمج ملفات Word متعددة باستخدام Aspose.Words للـ Java](/words/english/java/document-manipulation/cloning-and-combining-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}