---
date: '2025-11-12'
description: تعلم كيفية استخدام LayoutCollector و LayoutEnumerator في Aspose.Words
  for Java لتحليل ترقيم الصفحات، وتصفح تخطيط المستند، وتنفيذ ردود الاتصال الخاصة بالتخطيط،
  وإعادة بدء ترقيم الصفحات في الأقسام المتصلة.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
- analyze pagination java
- use layoutcollector page span
- traverse document layout
- restart page numbering sections
- implement layout callback
language: ar
title: تحليل تقسيم الصفحات في جافا باستخدام أدوات تخطيط Aspose.Words
url: /java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تحليل ترقيم الصفحات في Java باستخدام أدوات تخطيط Aspose.Words

## المقدمة  

إذا كنت بحاجة إلى **تحليل ترقيم الصفحات** أو **استعراض تخطيط المستند** في تطبيق Java، فإن Aspose.Words for Java يوفّر لك واجهتين برمجيتين قويّتين: **`LayoutCollector`** و **`LayoutEnumerator`**. تتيح لك هذه الفئات معرفة عدد الصفحات التي يشغلها كل عقدة، والتنقل عبر كل كيان تخطيطي، والاستجابة لأحداث التخطيط، وحتى إعادة بدء ترقيم الصفحات في الأقسام المتصلة. في هذا الدليل سنستعرض كل ميزة خطوةً بخطوة، ونظهر مقتطفات شفرة واقعية، ونشرح النتائج المتوقعة حتى تتمكن من تطبيقها فورًا.

سوف تتعلم كيف:

* **استخدام LayoutCollector** للحصول على الصفحة البداية والنهاية لأي عقدة (use layoutcollector page span)  
* **استعراض تخطيط المستند** باستخدام LayoutEnumerator (traverse document layout)  
* **تنفيذ ردود نداء التخطيط** للاستجابة لأحداث الترقيم (implement layout callback)  
* **إعادة بدء ترقيم الصفحات** في الأقسام المتصلة (restart page numbering sections)  

هيا نبدأ.

## المتطلبات المسبقة  

### المكتبات المطلوبة  

| أداة البناء | التبعيات |
|------------|----------|
| **Maven** | ```xml<br><dependency><groupId>com.aspose</groupId><artifactId>aspose-words</artifactId><version>25.3</version></dependency>``` |
| **Gradle** | ```gradle<br>implementation 'com.aspose:aspose-words:25.3'``` |

> **ملاحظة:** تم الحفاظ على رقم الإصدار للتوافق؛ الشفرة تعمل مع أي إصدار حديث من Aspose.Words for Java.

### البيئة  

* JDK 8 أو أحدث  
* بيئة تطوير متكاملة مثل IntelliJ IDEA أو Eclipse  

### المعرفة  

برمجة Java الأساسية والإلمام بـ Maven/Gradle كافيان لمتابعة الأمثلة.

## إعداد Aspose.Words  

قبل أن تتمكن من استدعاء أي واجهة برمجة تخطيط، يجب ترخيص المكتبة (أو استخدامها في وضع التجربة). يوضح المقتطف أدناه التهيئة الدنيا:

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Load your license file – skip this line for a trial evaluation
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

*الشفرة لا تُعدّل أي مستند؛ بل تُحضّر بيئة Aspose فقط.*  

الآن يمكننا الغوص في الميزات الأساسية.

## الميزة 1: استخدام **LayoutCollector** لتحليل ترقيم الصفحات  

`LayoutCollector` يربط كل عقدة في `Document` بالصفحات التي تشغلها. هذه هي الطريقة الأكثر موثوقية لـ **use layoutcollector page span** لتحليل الترقيم.

### تنفيذ خطوة‑بخطوة  

1. **إنشاء مستند جديد وإرفاق LayoutCollector.**  
2. **إدراج محتوى يُجبر على الترقيم** (مثل فواصل الصفحات، فواصل الأقسام).  
3. **تحديث التخطيط** باستخدام `updatePageLayout()`.  
4. **استعلام المجمع** عن الصفحة البداية، الصفحة النهاية، وإجمالي عدد الصفحات المشغولة.

#### 1️⃣ تهيئة المستند وLayoutCollector  

```java
Document doc = new Document();                 // Empty document
LayoutCollector layoutCollector = new LayoutCollector(doc);
```

#### 2️⃣ ملء المستند  

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);
```

#### 3️⃣ تحديث التخطيط واستخراج المقاييس  

```java
layoutCollector.clear();          // Reset any previous mappings
doc.updatePageLayout();           // Force pagination calculation

int pagesSpanned = layoutCollector.getNumPagesSpanned(doc);
assert pagesSpanned == 5;         // Expected: the document occupies 5 pages
System.out.println("Document spans " + pagesSpanned + " pages.");
```

**الناتج المتوقع**

```
Document spans 5 pages.
```

> **لماذا يعمل:** `updatePageLayout()` يجبر Aspose.Words على إعادة حساب التخطيط، وبعد ذلك يمكن لـ `LayoutCollector` الإبلاغ بدقة عن نطاق الصفحات.

## الميزة 2: استعراض تخطيط المستند باستخدام **LayoutEnumerator**  

عندما تحتاج إلى **استعراض تخطيط المستند** (مثلاً للتصيير المخصص أو التحليل)، يوفر `LayoutEnumerator` عرضًا شجريًا للصفحات، الفقرات، الأسطر، والكلمات.

### تنفيذ خطوة‑بخطوة  

1. تحميل مستند موجود يحتوي على كيانات تخطيطية.  
2. إنشاء نسخة من `LayoutEnumerator`.  
3. الانتقال إلى كيان الجذر `PAGE`.  
4. استعراض التخطيط إلى الأمام وإلى الخلف باستخدام طرق مساعدة تكرارية.

#### 1️⃣ تحميل المستند وإنشاء الـ Enumerator  

```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);
```

#### 2️⃣ التمركز على مستوى الصفحة  

```java
layoutEnumerator.moveParent(LayoutEntityType.PAGE);
```

#### 3️⃣ الاستعراض إلى الأمام (عمق‑أول)  

```java
traverseLayoutForward(layoutEnumerator, 1);
```

#### 4️⃣ الاستعراض إلى الخلف  

```java
traverseLayoutBackward(layoutEnumerator, 1);
```

> **الطرق المساعدة** (`traverseLayoutForward` / `traverseLayoutBackward`) تُنفّذ تكراريًا لزيارة كل كيان فرعي وطباعة نوعه ورقم صفحته. يمكنك تعديلها لجمع إحصائيات، تصيير رسومات، أو تعديل خصائص التخطيط.

## الميزة 3: تنفيذ **ردود نداء التخطيط**  

أحيانًا تحتاج إلى الاستجابة عندما تنتهي Aspose.Words من تخطيط جزء من المستند. تنفيذ `IPageLayoutCallback` يتيح لك **implement layout callback** مثل حفظ كل صفحة كصورة.

### تنفيذ خطوة‑بخطوة  

1. تعيين كائن رد نداء إلى `LayoutOptions` الخاص بالمستند.  
2. داخل رد النداء،