---
date: '2025-11-13'
description: تعلم كيفية استخدام Aspose.Words for Java LayoutCollector و LayoutEnumerator
  لتحليل نطاقات الصفحات، وتصفح كيانات التخطيط، وتنفيذ ردود النداء، وإعادة ترقيم الصفحات
  بكفاءة.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
- page span analysis java
- traverse layout entities java
- page layout callbacks java
- restart page numbering java
- document pagination Java
- Aspose.Words layout API
- Java text processing
language: ar
title: 'Aspose.Words Java: دليل LayoutCollector و LayoutEnumerator'
url: /java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إتقان Aspose.Words Java: دليل كامل لـ LayoutCollector و LayoutEnumerator لمعالجة النصوص

## المقدمة

هل تواجه صعوبات في إدارة تخطيطات المستندات المعقدة باستخدام تطبيقات Java الخاصة بك؟ سواءً كان الأمر يتعلق بتحديد عدد الصفحات التي يغطيها قسم ما أو بالتنقل عبر كيانات التخطيط بكفاءة، فإن هذه المهام قد تكون شاقة. مع **Aspose.Words for Java**، لديك أدوات قوية مثل `LayoutCollector` و `LayoutEnumerator` تُبسِّط هذه العمليات، مما يتيح لك التركيز على تقديم محتوى استثنائي. في هذا الدليل الشامل، سنستكشف كيفية الاستفادة من هذه الميزات لتعزيز قدرات معالجة المستندات لديك.

**ما ستتعلمه:**
- استخدام `LayoutCollector` في Aspose.Words للتحليل الدقيق لمدى تغطية الصفحات.
- التنقل الفعال في المستندات باستخدام `LayoutEnumerator`.
- تنفيذ ردود نداء (callbacks) للتخطيط لتحديثات وعرض ديناميكي.
- التحكم في ترقيم الصفحات في الأقسام المتصلة بفعالية.

لنغص في كيفية تحويل هذه الأدوات لعمليات معالجة المستندات الخاصة بك. قبل أن نبدأ، تأكد من أنك مستعد عبر مراجعة قسم المتطلبات المسبق أدناه.

## المتطلبات المسبقة

للتبع هذا الدليل، تأكد من توفر ما يلي:

### المكتبات والإصدارات المطلوبة
تأكد من تثبيت Aspose.Words for Java الإصدار 25.3.

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
ستحتاج إلى:
- مجموعة تطوير جافا (JDK) مثبتة على جهازك.
- بيئة تطوير متكاملة (IDE) مثل IntelliJ IDEA أو Eclipse لتشغيل واختبار الشيفرة.

### المتطلبات المعرفية
يفضل أن تكون لديك معرفة أساسية ببرمجة Java لتتمكن من المتابعة بفعالية.

## إعداد Aspose.Words
أولاً، تأكد من دمج مكتبة Aspose.Words في مشروعك. يمكنك الحصول على ترخيص تجريبي مجاني [هنا](https://releases.aspose.com/words/java/) أو اختيار ترخيص مؤقت إذا لزم الأمر. لبدء استخدام Aspose.Words في Java، قم بتهيئتها كما يلي:

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

مع إكمال الإعداد، دعنا نتعمق في الميزات الأساسية لـ `LayoutCollector` و `LayoutEnumerator`.

## دليل التنفيذ

### الميزة 1: استخدام LayoutCollector لتحليل مدى تغطية الصفحات
تتيح لك ميزة `LayoutCollector` تحديد كيفية امتداد العقد في المستند عبر الصفحات، مما يساعد في تحليل الترقيم.

#### نظرة عامة
من خلال الاستفادة من `LayoutCollector`، يمكننا معرفة فهارس الصفحات البداية والنهاية لأي عقدة، بالإضافة إلى عدد الصفحات الإجمالي التي تغطيها.

#### خطوات التنفيذ

**1. تهيئة Document و LayoutCollector**
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
- **`DocumentBuilder`**: يُستخدم لإدراج محتوى في المستند.
- **`updatePageLayout()`**: يضمن دقة مقاييس الصفحات.

### الميزة 2: التنقل باستخدام LayoutEnumerator
يتيح لك `LayoutEnumerator` التنقل الفعال عبر كيانات تخطيط المستند، موفرًا رؤى مفصلة حول خصائص كل عنصر وموقعه.

#### نظرة عامة
تساعد هذه الميزة في التنقل البصري عبر بنية التخطيط، وهو أمر مفيد لمهام العرض والتحرير.

#### خطوات التنفيذ

**1. تهيئة Document و LayoutEnumerator**
```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);
```

**2. التنقل للأمام والخلف**
للتنقل عبر تخطيط المستند:
```java
layoutEnumerator.moveParent(LayoutEntityType.PAGE);

// Traverse forward
traverseLayoutForward(layoutEnumerator, 1);

// Traverse backward
traverseLayoutBackward(layoutEnumerator, 1);
```

#### شرح
- **`moveParent()`**: ينتقل إلى الكيانات الأم.
- **طرق التنقل**: مُنفذة بشكل متكرر لتغطية شاملة.

### الميزة 3: ردود نداء تخطيط الصفحات
توضح هذه الميزة كيفية تنفيذ ردود نداء لمراقبة أحداث تخطيط الصفحات أثناء معالجة المستند.

#### نظرة عامة
استخدم واجهة `IPageLayoutCallback` للتفاعل مع تغييرات التخطيط المحددة، مثل إعادة تدفق قسم أو انتهاء التحويل.

#### خطوات التنفيذ

**1. تعيين رد نداء**
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
- **`notify()`**: يتعامل مع أحداث التخطيط.
- **`ImageSaveOptions`**: يضبط خيارات العرض.

### الميزة 4: إعادة تشغيل ترقيم الصفحات في الأقسام المتصلة
توضح هذه الميزة كيفية التحكم في ترقيم الصفحات في الأقسام المتصلة، لضمان تدفق سلس للمستند.

#### نظرة عامة
إدارة أرقام الصفحات بفعالية عند التعامل مع مستندات متعددة الأقسام باستخدام `ContinuousSectionRestart`.

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
- **`setContinuousSectionPageNumberingRestart()`**: يحدد كيفية إعادة تشغيل ترقيم الصفحات في الأقسام المتصلة.

## التطبيقات العملية
إليك بعض السيناريوهات الواقعية التي يمكن فيها تطبيق هذه الميزات:
1. **تحليل ترقيم المستندات:** استخدم `LayoutCollector` لتحليل وتعديل تخطيط المحتوى لتحقيق ترقيم مثالي.
2. **عرض PDF:** استعن بـ `LayoutEnumerator` للتنقل وعرض ملفات PDF بدقة، مع الحفاظ على البنية البصرية.
3. **تحديثات المستند الديناميكية:** نفّذ ردود نداء لتفعيل إجراءات عند تغييرات تخطيط محددة، مما يعزز معالجة المستند في الوقت الفعلي.
4. **المستندات متعددة الأقسام:** سيطر على ترقيم الصفحات في التقارير أو الكتب ذات الأقسام المتصلة لتنسيق احترافي.

## اعتبارات الأداء
لضمان أفضل أداء:
- قلل حجم المستند بإزالة العناصر غير الضرورية قبل تحليل التخطيط.
- استخدم طرق تنقل فعّالة لتقليل زمن المعالجة.
- راقب استهلاك الموارد، خاصةً عند التعامل مع مستندات ضخمة.

## الخاتمة
من خلال إتقان `LayoutCollector` و `LayoutEnumerator`، فتحت أمامك إمكانيات قوية في Aspose.Words for Java. لا تُبسِّط هذه الأدوات التخطيطات المعقدة فحسب، بل تعزز أيضًا قدرتك على إدارة ومعالجة النصوص بفعالية. armed with this knowledge, you're well-equipped to tackle any advanced text processing challenge that comes your way.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}