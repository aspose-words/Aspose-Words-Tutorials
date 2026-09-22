---
date: '2026-09-22'
description: تعلم كيفية تعيين مستويات العلامات المرجعية في ملفات PDF باستخدام Aspose.Words
  for Java، واكتشف كيفية تحويل Word إلى PDF مع العلامات المرجعية المتداخلة بكفاءة.
keywords:
- how to set bookmark
- convert word to pdf
- add bookmarks to pdf
- generate pdf with bookmarks
- java create pdf bookmarks
lastmod: '2026-09-22'
og_description: تعلم كيفية تعيين مستويات العلامات المرجعية في ملفات PDF باستخدام Aspose.Words
  for Java، واكتشف كيفية تحويل Word إلى PDF مع العلامات المرجعية المتداخلة بكفاءة.
og_image_alt: Developer guide showing how to set PDF bookmark outline levels using
  Aspose.Words for Java
og_title: كيفية تعيين مستويات العلامات المرجعية في ملفات PDF باستخدام Aspose.Words
  Java
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Learn how to set bookmark levels in PDFs using Aspose.Words for Java,
    and discover how to convert Word to PDF with nested bookmarks efficiently.
  headline: How to set bookmark levels in PDFs with Aspose.Words Java
  type: TechArticle
- description: Learn how to set bookmark levels in PDFs using Aspose.Words for Java,
    and discover how to convert Word to PDF with nested bookmarks efficiently.
  name: How to set bookmark levels in PDFs with Aspose.Words Java
  steps:
  - name: '**Free trial** – download from [Aspose''s release page](https://releases.aspose.com/words/java/)
      to evaluate the full feature set.'
    text: '**Free trial** – download from [Aspose''s release page](https://releases.aspose.com/words/java/)
      to evaluate the full feature set.'
  - name: '**Temporary license** – request one at [Aspose’s temporary license page](https://purchase.aspose.com/temporary-license/)
      for short‑term projects.'
    text: '**Temporary license** – request one at [Aspose’s temporary license page](https://purchase.aspose.com/temporary-license/)
      for short‑term projects.'
  - name: '**Purchase** – obtain a perpetual license via the [Aspose’s purchasing
      portal](https://purchase.aspose.com/buy).'
    text: '**Purchase** – obtain a perpetual license via the [Aspose’s purchasing
      portal](https://purchase.aspose.com/buy).'
  - name: '**Initialize Document and Builder**'
    text: '**Initialize Document and Builder**'
  - name: '**Insert the outer bookmark**'
    text: '**Insert the outer bookmark**'
  - name: '**Nest a second bookmark inside the first**'
    text: '**Nest a second bookmark inside the first**'
  - name: '**Close the outer bookmark**'
    text: '**Close the outer bookmark**'
  - name: '**Add a separate third bookmark**'
    text: '**Add a separate third bookmark**'
  - name: '**Set up `PdfSaveOptions`**'
    text: '**Set up `PdfSaveOptions`**'
  - name: '**Assign outline levels** – the `PdfBookmark` class (available through
      `document.getBookmarks()`) stores the level for each bookmark. Levels range
      from 0 (root) to 9 (maximum).'
    text: '**Assign outline levels** – the `PdfBookmark` class (available through
      `document.getBookmarks()`) stores the level for each bookmark. Levels range
      from 0 (root) to 9 (maximum).'
  type: HowTo
- questions:
  - answer: Add the Maven or Gradle dependency shown earlier, then place your license
      file in the classpath and initialize it with `License license = new License();
      license.setLicense("Aspose.Words.Java.lic");`.
    question: How do I install Aspose.Words for Java?
  - answer: Yes, but without levels the PDF viewer shows a flat list, making navigation
      harder for long documents.
    question: Can I add bookmarks without setting outline levels?
  - answer: Technically up to nine levels are supported by the PDF specification;
      deeper nesting is ignored by most viewers.
    question: Is there a limit to how deep bookmarks can be nested?
  - answer: It processes documents page‑by‑page and offers memory‑saving options,
      allowing you to convert files with hundreds of pages without exhausting RAM.
    question: How does Aspose.Words handle very large PDFs?
  - answer: Yes – use Aspose.PDF for Java to modify, reorder, or delete bookmarks
      in an existing PDF.
    question: Can I edit the bookmarks after the PDF is saved?
  type: FAQPage
tags:
- pdf bookmarks
- aspose.words
- java pdf generation
- document outline
title: كيفية تعيين مستويات العلامات المرجعية في ملفات PDF باستخدام Aspose.Words Java
url: /ar/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تعيين مستويات العلامات المرجعية في ملفات PDF باستخدام Aspose.Words Java

## المقدمة
إذا كنت تواجه صعوبة في تنظيم العلامات المرجعية لملفات PDF بعد تحويل مستندات Word، فأنت في المكان الصحيح. يوضح هذا الدليل **كيفية تعيين العلامة المرجعية** في ملفات PDF باستخدام Aspose.Words for Java، بحيث يتمكن قراؤك من الانتقال مباشرة إلى القسم المناسب دون الحاجة إلى التمرير المستمر.

**ما ستتعلمه**
- تثبيت وترخيص Aspose.Words for Java
- إنشاء علامات مرجعية متداخلة داخل ملف Word
- تكوين مستويات العلامات المرجعية لتصفح PDF نظيف
- حفظ ملف PDF النهائي بشجرة علامات مرجعية مُهيكلة بالكامل

### إجابات سريعة
- **هل يمكنني إضافة علامات مرجعية متداخلة؟** نعم – يتيح لك Aspose.Words تعشيق العلامات المرجعية إلى أي عمق.
- **هل أحتاج إلى ترخيص لإخراج PDF؟** ترخيص مؤقت أو مُشتَرٍ يفتح جميع ميزات PDF.
- **ما نسخة Java المطلوبة؟** Java 8 أو أعلى؛ المكتبة متوافقة مع Java 17 أيضًا.
- **كم عدد مستويات المخطط المدعومة؟** حتى 9 مستويات، وفقًا لمواصفات PDF.
- **هل يمكن تغيير المستويات بعد الحفظ؟** يمكنك تعديلها قبل الحفظ، ولكن ليس بعد إنشاء ملف PDF.

## المتطلبات المسبقة
- **المكتبات**: Aspose.Words for Java ≥ 25.3.
- **بيئة التطوير**: JDK 8+ وIDE مثل IntelliJ IDEA أو Eclipse.
- **المعرفة الأساسية**: أساسيات برمجة Java وأدوات البناء Maven أو Gradle.

## ما هو كيفية تعيين العلامة المرجعية؟
*كيفية تعيين العلامة المرجعية* تشير إلى عملية تعيين مستوى مخطط لكل علامة مرجعية بحيث يعرض عارضو PDF هذه العلامات في شجرة هرمية. من خلال تعريف هذه المستويات، تحول قائمة روابط مسطحة إلى لوحة تنقل بديهية قابلة للطي.

## لماذا تستخدم Aspose.Words لمستويات مخطط العلامات المرجعية؟
يمكن لـ Aspose.Words معالجة **أكثر من 35 تنسيقًا إدخاليًا** (بما في ذلك DOCX و ODT و RTF) وتصدير إلى **PDF و XPS و HTML و EPUB والمزيد**. يتعامل مع مستندات تصل إلى **500 صفحة** في أقل من **3 ثوانٍ** على خادم عادي، مع الحفاظ على التخطيطات المعقدة وهياكل العلامات المرجعية المتداخلة دون الحاجة إلى Microsoft Word.

## إعداد Aspose.Words
للبدء، أضف المكتبة إلى مشروعك. أدناه مقتطفات الاعتماد التي لديك بالفعل في الدليل الأصلي.

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

### الحصول على الترخيص
Aspose.Words تجارية، ولكن يمكنك البدء بنسخة تجريبية مجانية.

1. **نسخة تجريبية مجانية** – قم بالتحميل من [Aspose's release page](https://releases.aspose.com/words/java/) لتقييم مجموعة الميزات الكاملة.  
2. **ترخيص مؤقت** – اطلب واحدًا من [Aspose’s temporary license page](https://purchase.aspose.com/temporary-license/) للمشاريع قصيرة الأجل.  
3. **شراء** – احصل على ترخيص دائم عبر [Aspose’s purchasing portal](https://purchase.aspose.com/buy).

بعد حصولك على ملف `.lic`، قم بتحميله عند بدء تشغيل التطبيق لفتح جميع إمكانيات PDF.

## كيفية تعيين مستويات مخطط العلامة المرجعية؟
حمّل مستند Word الخاص بك، أنشئ علامات مرجعية متداخلة، عيّن مستويات المخطط، وأخيرًا احفظ كملف PDF. الإجابة المباشرة هي:

> ابدأ بإنشاء كائن `Document`، واستخدم `DocumentBuilder` لإدراج العلامات المرجعية البداية/النهاية، عيّن `OutlineLevel` لكل علامة مرجعية عبر `PdfSaveOptions.getBookmarksOutlineLevel()`، ثم استدعِ `document.save("output.pdf", saveOptions)`. هذه السلسلة تُنشئ ملف PDF حيث تظهر العلامات المرجعية في شجرة هرمية تمامًا كما حددتها.

### تنفيذ خطوة بخطوة

#### إنشاء علامات مرجعية متداخلة
`DocumentBuilder` هو واجهة برمجة التطبيقات القائمة على المؤشر في Aspose.Words لإدراج النصوص والجداول والصور والعلامات المرجعية في مستند برمجيًا.

1. **تهيئة Document و Builder**  
   ```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```  

2. **إدراج العلامة المرجعية الخارجية**  
   ```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```  

3. **إدراج علامة مرجعية ثانية داخل الأولى**  
   ```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```  

4. **إغلاق العلامة المرجعية الخارجية**  
   ```java
builder.endBookmark("Bookmark 1");
```  

5. **إضافة علامة مرجعية ثالثة منفصلة**  
   ```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```  

#### تكوين مستويات مخطط العلامة المرجعية
`PdfSaveOptions` يتيح لك التحكم في كيفية كتابة العلامات المرجعية إلى ملف PDF، بما في ذلك تسلسلها الهرمي.

1. **إعداد `PdfSaveOptions`**  
   ```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```  

2. **تعيين مستويات المخطط** – فئة `PdfBookmark` (المتاحة عبر `document.getBookmarks()`) تخزن المستوى لكل علامة مرجعية. تتراوح المستويات من 0 (الجذر) إلى 9 (الحد الأقصى).  
   ```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```  

3. **حفظ ملف PDF**  
   ```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```  

## المشكلات الشائعة واستكشاف الأخطاء
- **العلامات المرجعية المفقودة** – يجب أن يكون لكل `startBookmark` علامة `endBookmark` مطابقة. يُطلق الـ builder استثناءً إذا كانت غير متوازنة.  
- **التسلسل الهرمي غير الصحيح** – تحقق من أن العلامات المرجعية الفرعية تُدرج بعد علامة البداية للوالد ولكن قبل علامة النهاية للوالد.  
- **المستندات الكبيرة** – استدعِ `document.removeUnusedResources()` قبل الحفظ لتقليل استهلاك الذاكرة.  

## التطبيقات العملية
1. **العقود القانونية** – الانتقال سريعًا إلى البنود والجداول والملحقات.  
2. **التقارير السنوية** – تمكين أصحاب المصلحة من التنقل بين الأقسام والجداول والرسوم البيانية بنقرة واحدة.  
3. **وحدات التعلم الإلكتروني** – هيكلة الفصول والدروس والاختبارات لتجربة تعلم سلسة.  

## اعتبارات الأداء
- **إزالة المحتوى غير المستخدم** – استخدم `document.removeUnusedResources()` للحفاظ على حجم PDF بأقل حد.  
- **الحفظ المتدفق** – للملفات التي تتجاوز 200 ميغابايت، استخدم `PdfSaveOptions.setUseMemorySaving(true)` لتجنب تحميل المستند بالكامل في الذاكرة.  

## الأسئلة المتكررة

**س: كيف أقوم بتثبيت Aspose.Words for Java؟**  
ج: أضف اعتماد Maven أو Gradle الموضح سابقًا، ثم ضع ملف الترخيص في مسار الفئة (classpath) وقم بتهيئته باستخدام `License license = new License(); license.setLicense("Aspose.Words.Java.lic");`.

**س: هل يمكنني إضافة علامات مرجعية دون تعيين مستويات المخطط؟**  
ج: نعم، ولكن بدون مستويات يعرض عارض PDF قائمة مسطحة، مما يجعل التنقل أصعب في المستندات الطويلة.

**س: هل هناك حد لعمق تعشيق العلامات المرجعية؟**  
ج: تقنيًا تدعم مواصفة PDF ما يصل إلى تسعة مستويات؛ التعشيق الأعمق يتم تجاهله من قبل معظم العارضين.

**س: كيف يتعامل Aspose.Words مع ملفات PDF الكبيرة جدًا؟**  
ج: يعالج المستندات صفحةً بصفحة ويقدم خيارات توفير الذاكرة، مما يتيح لك تحويل ملفات بمئات الصفحات دون استنزاف الذاكرة.

**س: هل يمكن تعديل العلامات المرجعية بعد حفظ ملف PDF؟**  
ج: نعم – استخدم Aspose.PDF for Java لتعديل أو إعادة ترتيب أو حذف العلامات المرجعية في ملف PDF موجود.

## الخلاصة
أنت الآن تعرف **كيفية تعيين مستويات العلامات المرجعية** في ملفات PDF باستخدام Aspose.Words for Java. من خلال إنشاء علامات مرجعية متداخلة وتعيين مستويات هرمية، تحول ملف PDF عادي إلى مستند احترافي وسهل الاستخدام. جرب هياكل مختلفة، ودمج هذه التقنية مع ميزات Aspose الأخرى (مثل التوقيعات الرقمية أو العلامات المائية)، ودمجها في خطوط إنتاج إنشاء المستندات لتحقيق أقصى تأثير.

---

**آخر تحديث:** 2026-09-22  
**تم الاختبار مع:** Aspose.Words for Java 25.3  
**المؤلف:** Aspose  

**الموارد ذات الصلة**: [Aspose.Words Documentation](https://reference.aspose.com/words/java/) | [Download Latest Releases](https://releases.aspose.com/words/java/) | [Purchase a License](https://purchase.aspose.com/buy) | [Free Trial](https://releases.aspose.com/words/java/) | [Temporary License Application](https://purchase.aspose.com/temporary-license/) | [Aspose Support Forum](https://forum.aspose.com/c/words/10)

## دروس ذات صلة

- [إتقان Aspose.Words for Java: كيفية إدراج وإدارة العلامات المرجعية في مستندات Word](/words/java/content-management/aspose-words-java-manage-bookmarks/)
- [استخدام العلامات المرجعية في Aspose.Words for Java](/words/java/document-manipulation/using-bookmarks/)
- [حفظ المستندات كملف PDF في Aspose.Words for Java](/words/java/document-loading-and-saving/saving-documents-as-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}