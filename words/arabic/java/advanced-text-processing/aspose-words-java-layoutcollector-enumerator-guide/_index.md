---
date: '2026-01-14'
description: تعلم كيفية إعادة بدء ترقيم الصفحات باستخدام Aspose.Words Java واستخدام
  LayoutCollector لاستخراج بيانات الترميز، وتحديث تخطيط الصفحة، وتحويل الصفحات إلى
  صور.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
title: إعادة بدء ترقيم الصفحات باستخدام Aspose.Words Java – LayoutCollector و LayoutEnumerator
url: /ar/java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إعادة تشغيل ترقيم الصفحات باستخدام Aspose.Words Java – LayoutCollector & LayoutEnumerator

## المقدمة

هل تواجه صعوبة في **إعادة تشغيل ترقيم الصفحات** في مستندات Java الكبيرة مع الحاجة أيضًا إلى تحليل الترقيم أو تحويل الصفحات إلى صور؟ باستخدام **Aspose.Words for Java**، يمكنك الاستفادة من `LayoutCollector` و `LayoutEnumerator` ليس فقط لإعادة تشغيل ترقيم الصفحات بل أيضًا **استخراج بيانات الترقيم**، **تحديث تخطيط الصفحة**، و **تحويل الصفحات إلى صور** للمعاينات أو ملفات PDF. يوضح هذا الدليل كل خطوة، بدءًا من إعداد المكتبة إلى تنفيذ ردود النداء التي تمنحك التحكم الكامل في عرض المستند.

**ما ستتعلمه**
- كيفية استخدام `LayoutCollector` لاستخراج بيانات الترقيم وتحديد نطاق الصفحات.
- التجوال في تخطيط المستند باستخدام `LayoutEnumerator`.
- تنفيذ ردود نداء تخطيط الصفحة **لتحويل الصفحات إلى صور**.
- **إعادة تشغيل ترقيم الصفحات** في الأقسام المتصلة باستخدام خيارات التخطيط.
- نصائح **لتحديث تخطيط الصفحة** بفعالية.

## إجابات سريعة
- **كيف يمكنني إعادة تشغيل ترقيم الصفحات في مستند Java؟** استخدم `doc.getLayoutOptions().setContinuousSectionPageNumberingRestart(...)` ثم استدعِ `doc.updatePageLayout()`.
- **أي فئة تستخرج بيانات الترقيم؟** `LayoutCollector` توفر فهارس الصفحة البداية/النهاية لأي عقدة.
- **هل يمكنني تحويل كل صفحة إلى صورة؟** نعم—نفّذ `IPageLayoutCallback` واستخدم `ImageSaveOptions`.
- **هل يجب استدعاء تحديث تخطيط الصفحة يدويًا؟** بعد تعديل خيارات التخطيط، دائمًا استدعِ `doc.updatePageLayout()`.
- **ما الإصدار المطلوب من Aspose.Words؟** الأمثلة تعمل مع Aspose.Words for Java 25.3 (أو أحدث).

## ما هو إعادة تشغيل ترقيم الصفحات؟

إعادة تشغيل ترقيم الصفحات تسمح لك ببدء تسلسل ترقيم جديد في قسم معين من المستند، وهو أمر أساسي للتقارير، الكتب، أو العقود التي تتطلب ترقيمًا منفصلًا للفصول أو الملاحق. يوفر Aspose.Words خيار تخطيط يتيح لك التحكم في هذا السلوك دون الحاجة إلى حيل يدوية لكسر الصفحات.

## لماذا نستخدم LayoutCollector و LayoutEnumerator؟

- **LayoutCollector** يمنحك وصولًا برمجيًا إلى تفاصيل الترقيم، مما يمكنك من **استخراج بيانات الترقيم** مثل الصفحة الأولى والأخيرة لأي عقدة.
- **LayoutEnumerator** يسمح لك بالتجول في شجرة التخطيط البصري، مما يسهل تحديد الصفحات أو الفقرات أو الأسطر للتصوير المخصص أو التحليل.
- معًا يبسطان مهام التخطيط المعقدة التي كانت تتطلب تحويلات PDF مكلفة أو حسابات يدوية.

## المتطلبات المسبقة

### المكتبات المطلوبة والإصدارات
تأكد من تثبيت Aspose.Words for Java الإصدار 25.3 (أو أحدث).

**Maven:**
```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

**Gradle:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### متطلبات إعداد البيئة
- تثبيت مجموعة تطوير جافا (JDK).
- IntelliJ IDEA، Eclipse، أو أي بيئة تطوير جافا تفضلها.
- رخصة صالحة لـ Aspose.Words (يمكنك استخدام نسخة تجريبية مجانية للتقييم).

### المتطلبات المعرفية
معرفة أساسية ببرمجة جافا كافية.

## إعداد Aspose.Words
أولاً، دمج مكتبة Aspose.Words في مشروعك. يمكنك الحصول على رخصة تجريبية مجانية [هنا](https://releases.aspose.com/words/java/) أو استخدام رخصة مؤقتة للاختبار.

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Set up the license (if available)
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

مع جاهزية المكتبة، يمكننا الغوص في الميزات الأساسية.

## دليل التنفيذ

### الميزة 1: استخدام LayoutCollector لتحليل نطاق الصفحات
تتيح لك ميزة `LayoutCollector` تحديد كيفية امتداد العقد عبر الصفحات، وهو الأساس **لاستخراج بيانات الترقيم**.

#### نظرة عامة
من خلال الاستفادة من `LayoutCollector`، يمكنك استرجاع فهارس الصفحة البداية والنهاية لأي عقدة وحساب إجمالي عدد الصفحات التي تحتلها.

#### خطوات التنفيذ

**1. تهيئة المستند و LayoutCollector**
```java
Document doc = new Document();
LayoutCollector layoutCollector = new LayoutCollector(doc);
```

**2. ملء المستند**
هنا، سنضيف محتوى يمتد عبر عدة صفحات:
```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);
```

**3. تحديث التخطيط واسترجاع المقاييس**
```java
layoutCollector.clear();
doc.updatePageLayout();

assert layoutCollector.getNumPagesSpanned(doc) == 5;
```

#### شرح
- **`DocumentBuilder`** يضيف نصًا وفواصل صفحات/أقسام.
- **`updatePageLayout()`** يعيد حساب معلومات التخطيط لضمان دقة بيانات الترقيم.

### الميزة 2: التجوال باستخدام LayoutEnumerator
`LayoutEnumerator` يتيح تنقلًا فعالًا عبر شجرة التخطيط البصري.

#### نظرة عامة
يمكنك التجول عبر الصفحات، الفقرات، الأسطر، وغيرها من كيانات التخطيط، وهو مفيد للتصوير المخصص أو التشخيص.

#### خطوات التنفيذ

**1. تهيئة المستند و LayoutEnumerator**
```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);
```

**2. التجوال للأمام وللخلف**
```java
layoutEnumerator.moveParent(LayoutEntityType.PAGE);

// Traverse forward
traverseLayoutForward(layoutEnumerator, 1);

// Traverse backward
traverseLayoutBackward(layoutEnumerator, 1);
```

#### شرح
- **`moveParent()`** ينقل المُعدِّل إلى الكيان الأب (في هذه الحالة، مستوى الصفحة).
- طرق التجوال المتكررة تتيح لك استكشاف كامل هيكل التخطيط.

### الميزة 3: ردود نداء تخطيط الصفحة
نفّذ ردود نداء لمراقبة أحداث التخطيط و**تحويل الصفحات إلى صور** عند الحاجة.

#### نظرة عامة
واجهة `IPageLayoutCallback` تُخبرك عندما ينتهي جزء من المستند من إعادة التدفق أو عند اكتمال التحويل.

#### خطوات التنفيذ

**1. تعيين رد النداء**
```java
doc.getLayoutOptions().setCallback(new RenderPageLayoutCallback());
doc.updatePageLayout();
```

**2. تنفيذ طرق رد النداء**
```java
private static class RenderPageLayoutCallback implements IPageLayoutCallback {
    public void notify(PageLayoutCallbackArgs a) throws Exception {
        if (a.getEvent() == PageLayoutEvent.PART_REFLOW_FINISHED) {
            notifyPartFinished(a);
        } else if (a.getEvent() == PageLayoutEvent.CONVERSION_FINISHED) {
            notifyConversionFinished(a);
        }
    }

    private void renderPage(PageLayoutCallbackArgs a, int pageIndex) throws Exception {
        ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.PNG);
        saveOptions.setPageSet(new PageSet(pageIndex));

        try (FileOutputStream stream = new FileOutputStream("YOUR_ARTIFACTS_DIR/PageLayoutCallback.page-" + (pageIndex + 1) + ".png")) {
            a.getDocument().save(stream, saveOptions);
        }
    }
}
```

#### شرح
- **`notify()`** يتفاعل مع أحداث التخطيط.
- **`ImageSaveOptions`** مع `PageSet` يتيح لك **تحويل الصفحات إلى صور** (PNG في هذا المثال).

### الميزة 4: إعادة تشغيل ترقيم الصفحات في الأقسام المتصلة
تحكم في ترقيم الصفحات عندما يكون لديك عدة أقسام تتدفق بشكل متصل.

#### نظرة عامة
عن طريق ضبط خيار `ContinuousSectionRestart`، يمكنك تحديد ما إذا كان ترقيم الصفحات يعاد بدءه في صفحة جديدة أو يستمر بسلاسة.

#### خطوات التنفيذ

**1. تحميل المستند**
```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Continuous section page numbering.docx");
```

**2. ضبط خيارات ترقيم الصفحات**
```java
doc.getLayoutOptions().setContinuousSectionPageNumberingRestart(ContinuousSectionRestart.FROM_NEW_PAGE_ONLY);
doc.updatePageLayout();
```

#### شرح
- **`setContinuousSectionPageNumberingRestart()`** يحدد كيفية تعامل Aspose.Words مع الترقيم في الأقسام المتصلة.
- بعد تعديل الخيار، **قم بتحديث تخطيط الصفحة** لتطبيق التغييرات.

## التطبيقات العملية
1. **تحليل ترقيم المستند** – استخدم `LayoutCollector` لتدقيق كيفية انتشار المحتوى عبر الصفحات وضبط الهوامش أو الفواصل وفقًا لذلك.
2. **تحويل PDF** – اجمع بين `LayoutEnumerator` ورد النداء لإنشاء صور صفحات عالية الدقة قبل تحويلها إلى PDF.
3. **تحديثات المستند الديناميكية** – استجب لأحداث التخطيط (مثل توسع جدول) وقم بإعادة تصوير الصفحات المتأثرة تلقائيًا.
4. **تقارير متعددة الأقسام** – طبّق **إعادة تشغيل ترقيم الصفحات** لإعطاء كل فصل نظام ترقيم خاص به مع الحفاظ على تدفق مستمر.

## اعتبارات الأداء
- احذف الأقسام غير المستخدمة أو المحتوى المخفي قبل استدعاء `updatePageLayout()` للحفاظ على سرعة المعالجة.
- استخدم واجهات برمجة التطبيقات المتدفقة للملفات الكبيرة لتجنب تحميل الملف بالكامل في الذاكرة.
- قلل عمق التجوال المتكرر في `LayoutEnumerator` إذا كنت بحاجة فقط إلى معلومات على مستوى الصفحة.

## المشكلات الشائعة والحلول
| المشكلة | السبب | الحل |
|-------|-------|-----|
| `layoutCollector.getNumPagesSpanned()` يُعيد 0 | لم يتم تحديث التخطيط | استدعِ `doc.updatePageLayout()` قبل الاستعلام |
| الصور لا تُولد في رد النداء | نقص إعداد `ImageSaveOptions` | تأكد من ضبط `saveOptions.setPageSet(new PageSet(pageIndex))` |
| ترقيم الصفحات لا يعاد تشغيله | قيمة `ContinuousSectionRestart` غير صحيحة | استخدم `ContinuousSectionRestart.FROM_NEW_PAGE_ONLY` لإعادة تشغيل حقيقية |

## الأسئلة المتكررة

**س: هل يمكنني استخراج رقم الصفحة الدقيق لفقرة معينة؟**  
ج: نعم—استخدم `LayoutCollector` للحصول على الصفحة البداية لعقدة الفقرة ثم استدعِ `doc.updatePageLayout()` لضمان حداثة البيانات.

**س: هل يؤثر `update page layout` على محتوى المستند؟**  
ج: لا. فهو يعيد حساب معلومات التخطيط فقط؛ النص والتنسيق يبقيان دون تغيير.

**س: كيف يمكنني تحويل جميع صفحات مستند كبير إلى صور بكفاءة؟**  
ج: نفّذ `IPageLayoutCallback` وعالج كل صفحة على حدة، ويمكنك استخدام تعدد الخيوط للعمليات ذات الإدخال/الإخراج المكثف.

**س: هل يمكن إعادة تشغيل الترقيم فقط لبعض الأقسام؟**  
ج: نعم—طبق `setContinuousSectionPageNumberingRestart` على خيارات تخطيط القسم المحدد قبل استدعاء `updatePageLayout()`.

**س: أي إصدار من Aspose.Words قدم `LayoutCollector`؟**  
ج: `LayoutCollector` متاح منذ إصدارات 2020 المبكرة؛ الأمثلة تستخدم الإصدار 25.3.

## الخاتمة
من خلال إتقان **إعادة تشغيل ترقيم الصفحات**، و`LayoutCollector`، و`LayoutEnumerator`، أصبحت الآن تملك مجموعة أدوات قوية لمعالجة النص المتقدمة في Aspose.Words for Java. سواء كنت بحاجة إلى **استخراج بيانات الترقيم**، **تحويل الصفحات إلى صور**، أو مجرد التحكم في ترقيم الصفحات عبر الأقسام، فإن هذه الواجهات تمنحك تحكمًا برمجيًا دقيقًا مع الحفاظ على أداء عالٍ.

---

**آخر تحديث:** 2026-01-14  
**تم الاختبار مع:** Aspose.Words for Java 25.3  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}