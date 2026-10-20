---
date: '2026-10-02'
description: تعلم كيفية إنشاء إشارات مرجعية متداخلة وحفظ إشارات مرجعية PDF في Word
  باستخدام Aspose.Words for Java، مما يتيح تنقلًا فعالًا في ملفات PDF.
keywords:
- how to create bookmarks
- convert word pdf bookmarks
- save word pdf bookmarks
lastmod: '2026-10-02'
og_description: كيفية إنشاء إشارات مرجعية في PDF باستخدام Aspose.Words for Java. تعلم
  إضافة إشارات مرجعية متداخلة، وتعيين مستويات المخطط، وحفظ إشارات مرجعية PDF في Word
  بكفاءة.
og_image_alt: Developer guide showing nested PDF bookmarks creation with Aspose.Words
  for Java
og_title: كيفية إنشاء إشارات مرجعية في PDF باستخدام Aspose.Words for Java
schemas:
- author: Aspose
  dateModified: '2026-10-02'
  description: Learn how to create nested bookmarks and save Word PDF bookmarks using
    Aspose.Words for Java, enabling efficient PDF navigation.
  headline: How to create bookmarks in PDF with Aspose.Words for Java
  type: TechArticle
- description: Learn how to create nested bookmarks and save Word PDF bookmarks using
    Aspose.Words for Java, enabling efficient PDF navigation.
  name: How to create bookmarks in PDF with Aspose.Words for Java
  steps:
  - name: '**Free trial** – Download from [Aspose''s release page](https://releases.aspose.com/words/java/)
      to test full capabilities.'
    text: '**Free trial** – Download from [Aspose''s release page](https://releases.aspose.com/words/java/)
      to test full capabilities.'
  - name: '**Temporary license** – Apply at [Aspose’s temporary license page](https://purchase.aspose.com/temporary-license/)
      if you need a short‑term key.'
    text: '**Temporary license** – Apply at [Aspose’s temporary license page](https://purchase.aspose.com/temporary-license/)
      if you need a short‑term key.'
  - name: '**Purchase** – Obtain a permanent license from the [Aspose’s purchasing
      portal](https://purchase.aspose.com/buy).'
    text: '**Purchase** – Obtain a permanent license from the [Aspose’s purchasing
      portal](https://purchase.aspose.com/buy).'
  type: HowTo
- questions:
  - answer: Add the Maven or Gradle dependency shown above, then load your license
      file at runtime.
    question: How do I install Aspose.Words for Java?
  - answer: Yes, but without outline levels the PDF’s navigation pane will list all
      bookmarks at the same hierarchy, which can be confusing for readers.
    question: Can I use bookmarks without setting outline levels?
  - answer: Technically no, but for usability keep nesting to 3‑4 levels so users
      can easily scan the list.
    question: Is there a limit to how deep bookmarks can be nested?
  - answer: The library streams content and offers `optimizeResources()` to reduce
      memory footprint; monitoring JVM heap is still recommended for multi‑hundred‑page
      files.
    question: How does Aspose handle very large documents?
  - answer: Yes, you can use Aspose.PDF for Java to edit, add, or remove bookmarks
      in an existing PDF.
    question: Can I modify bookmarks after the PDF is created?
  type: FAQPage
tags:
- PDF bookmarks
- Aspose.Words
- Java PDF generation
- nested bookmarks
- document processing
title: كيفية إنشاء إشارات مرجعية في PDF باستخدام Aspose.Words for Java
url: /ar/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء إشارات مرجعية في PDF باستخدام Aspose.Words for Java

## مقدمة
إذا كنت بحاجة إلى **إنشاء إشارات مرجعية متداخلة** في ملف PDF تم إنشاؤه من مستند Word، فقد وصلت إلى المكان الصحيح. في هذا البرنامج التعليمي سنستعرض العملية الكاملة باستخدام Aspose.Words for Java، بدءًا من إعداد المكتبة إلى تكوين مستويات مخطط الإشارات المرجعية وأخيرًا **حفظ إشارات مرجعية Word PDF** بحيث يكون ملف PDF النهائي سهل التنقل. ستفهم لماذا تُعد الإشارات المرجعية مهمة، وسترى استدعاءات API الدقيقة، وستحصل على نصائح للتعامل مع المستندات الكبيرة.

**ما ستتعلم**
- كيفية إعداد Aspose.Words for Java
- كيفية **إنشاء إشارات مرجعية متداخلة** داخل مستند Word
- كيفية تعيين مستويات المخطط لتصفح PDF واضح
- كيفية **حفظ إشارات مرجعية Word PDF** باستخدام `PdfSaveOptions`

## إجابات سريعة
- **ما هو الهدف الأساسي؟** إنشاء إشارات مرجعية متداخلة وحفظ إشارات مرجعية Word PDF في ملف PDF واحد.  
- **ما المكتبة المطلوبة؟** Aspose.Words for Java (v25.3 أو أحدث).  
- **هل أحتاج إلى ترخيص؟** نسخة تجريبية مجانية تعمل للاختبار؛ يلزم ترخيص تجاري للإنتاج.  
- **هل يمكنني التحكم في مستويات المخطط؟** نعم، باستخدام `PdfSaveOptions` و `BookmarksOutlineLevelCollection`.  
- **هل هذا مناسب للمستندات الكبيرة؟** نعم، مع إدارة الذاكرة المناسبة وتحسين الموارد.

## ما هو “إنشاء إشارات مرجعية متداخلة”؟
إنشاء إشارات مرجعية متداخلة يعني وضع إشارة مرجعية داخل أخرى، مما يشكل هيكلًا هرميًا يعكس الأقسام المنطقية في مستندك. ينعكس هذا الهرم في لوحة تنقل PDF، مما يسمح للقراء بالقفز مباشرة إلى فصول أو أقسام فرعية محددة.

## لماذا تستخدم Aspose.Words for Java لحفظ إشارات مرجعية Word PDF؟
يدعم Aspose.Words for Java **أكثر من 35 تنسيقًا للإدخال والإخراج** — بما في ذلك DOCX و ODT و RTF و PDF و HTML و EPUB — ويمكنه معالجة مستندات تصل إلى 500 صفحة في أقل من 3 ثوانٍ على خادم عادي. فهو يُجرد التعامل منخفض المستوى مع PDF، مما يتيح لك التركيز على هيكل المحتوى مع الحفاظ على جميع ميزات Word مثل الأنماط والصور والجداول.

## المتطلبات المسبقة
- **المكتبات**: Aspose.Words for Java (v25.3+).  
- **بيئة التطوير**: JDK 8 أو أحدث، IDE مثل IntelliJ IDEA أو Eclipse.  
- **أداة البناء**: Maven أو Gradle (حسب تفضيلك).  
- **المعرفة الأساسية**: برمجة Java، أساسيات Maven/Gradle.

## إعداد Aspose.Words
أضف المكتبة إلى مشروعك باستخدام أحد المقتطفات التالية.

**Maven**  
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```  

**Gradle**  
```gradle
implementation 'com.aspose:aspose-words:25.3'
```  

### الحصول على الترخيص
Aspose.Words هو منتج تجاري، لكن يمكنك البدء بنسخة تجريبية مجانية:

1. **Free trial** – حمّل من [Aspose's release page](https://releases.aspose.com/words/java/) لاختبار جميع القدرات.  
2. **Temporary license** – قدّم طلبًا على [Aspose’s temporary license page](https://purchase.aspose.com/temporary-license/) إذا كنت بحاجة إلى مفتاح قصير الأمد.  
3. **Purchase** – احصل على ترخيص دائم من [Aspose’s purchasing portal](https://purchase.aspose.com/buy).

بمجرد حصولك على ملف `.lic`، قم بتحميله عند بدء تشغيل التطبيق لفتح جميع الميزات.

## دليل التنفيذ
فيما يلي شرح خطوة بخطوة. كل كتلة شفرة تبقى دون تغيير عن البرنامج التعليمي الأصلي للحفاظ على الوظيفة.

### كيفية إنشاء إشارات مرجعية متداخلة في مستند Word
#### كيفية تهيئة المستند والباني
للشروع، تحتاج إلى كائن `Document` و `DocumentBuilder`.  
`Document` هو الكائن الأعلى مستوى في Aspose.Words الذي يمثل ملف Word واحد في الذاكرة.  
`DocumentBuilder` يوفر API يعتمد على المؤشر لإدراج النصوص والجداول والصور والإشارات المرجعية.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```  

#### كيفية إدراج الإشارة المرجعية الأولى (الأصلية)
تبدأ إشارة مرجعية باستخدام `startBookmark` وتغلقها لاحقًا باستخدام `endBookmark`.  
`startBookmark` يحدد بداية منطقة الإشارة المرجعية؛ `endBookmark` المقابل يحدد نهايتها.

```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```  

#### كيفية تداخل إشارة مرجعية ثانية داخل الأولى
عن طريق استدعاء `startBookmark` مرة أخرى قبل إغلاق الإشارة المرجعية الخارجية، تنشئ إشارة مرجعية فرعية.  
الإشارة المرجعية المتداخلة ترث مستوى المخطط من الأصل ما لم تقم بتعيين مستوى مختلف صراحةً لاحقًا.

```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```  

#### كيفية إغلاق الإشارة المرجعية الخارجية
إغلاق الإشارة المرجعية الخارجية يُكمل الهرم.  
تأكد من أن كل `startBookmark` له `endBookmark` مطابق؛ وإلا قد يفتقد PDF الإشارة المرجعية أو يظهر خطأ.

```java
builder.endBookmark("Bookmark 1");
```  

#### كيفية إضافة إشارة مرجعية ثالثة منفصلة
يمكنك إضافة إشارات مرجعية إضافية من المستوى الأعلى بعد الزوج المتداخل.  
ستظهر هذه كعناصر شقيقة في لوحة تنقل PDF.

```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```  

## كيفية حفظ إشارات مرجعية Word PDF وتعيين مستويات المخطط
### كيفية تكوين PdfSaveOptions
`PdfSaveOptions` يتحكم في إعدادات PDF الخاصة، بما في ذلك مستويات مخطط الإشارات المرجعية.

```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```  

### كيفية تعيين مستويات المخطط لكل إشارة مرجعية
`BookmarksOutlineLevelCollection` يتيح لك ربط كل اسم إشارة مرجعية بمستوى مخطط (1 = المستوى الأعلى).

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```  

### كيفية حفظ المستند كملف PDF
أخيرًا، استدعِ `save` مع الخيارات المكوَّنة.  
طريقة `save` تكتب المستند بالتنسيق المحدد؛ عند استخدام `PdfSaveOptions`، يتم أيضًا تضمين هيكل الإشارات المرجعية في ملف PDF.

```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```  

## المشكلات الشائعة والحلول
- **الإشارات المرجعية المفقودة** – تحقق من أن كل `startBookmark` له `endBookmark` مطابق.  
- **الهرم غير الصحيح** – تأكد من أن أرقام مستويات المخطط تعكس علاقة الأصل‑الطفل المطلوبة (الأرقام الأقل = المستوى الأعلى).  
- **حجم الملف الكبير** – احذف الأنماط أو الصور غير المستخدمة قبل الحفظ، أو استدعِ `doc.optimizeResources()` لتقليل استهلاك الذاكرة.

## التطبيقات العملية
| السيناريو | فائدة الإشارات المرجعية المتداخلة |
|----------|-----------------------------------|
| العقود القانونية | القفز السريع إلى البنود والبنود الفرعية |
| التقارير التقنية | التنقل عبر الأقسام المعقدة والملحقات |
| مواد التعلم الإلكتروني | الوصول المباشر إلى الفصول والدروس والاختبارات |

## اعتبارات الأداء
- **استخدام الذاكرة** – عالج المستندات الكبيرة على دفعات أو استخدم `DocumentBuilder.insertDocument` لدمج أجزاء أصغر.  
- **حجم الملف** – ضغط الصور وإزالة المحتوى المخفي قبل تحويل PDF.  
- **السرعة** – يمكن لـ Aspose.Words تحويل مستند من 300 صفحة إلى PDF في أقل من ثانيتين على خادم عادي، بفضل محرك العرض الأصلي الخاص به.

## الخلاصة
أنت الآن تعرف كيفية **إنشاء إشارات مرجعية متداخلة**، وتكوين مستويات المخطط الخاصة بها، و**حفظ إشارات مرجعية Word PDF** باستخدام Aspose.Words for Java. هذه التقنية تحسن بشكل كبير تنقل PDF، مما يجعل مستنداتك أكثر احترافية وسهولة في الاستخدام.

**الخطوات التالية**: جرب هياكل إشارات مرجعية أعمق، دمج هذه المنطق في خطوط معالجة الدفعات، أو الجمع بينها وبين Aspose.PDF for Java لتعديل الإشارات المرجعية بعد إنشاء PDF.

## الأسئلة المتكررة
**س: كيف أقوم بتثبيت Aspose.Words for Java؟**  
ج: أضف تبعية Maven أو Gradle الموضحة أعلاه، ثم حمّل ملف الترخيص الخاص بك أثناء التشغيل.

**س: هل يمكنني استخدام الإشارات المرجعية دون تعيين مستويات المخطط؟**  
ج: نعم، لكن بدون مستويات المخطط ستظهر جميع الإشارات المرجعية في لوحة تنقل PDF على نفس المستوى الهرمي، مما قد يربك القراء.

**س: هل هناك حد لعمق تداخل الإشارات المرجعية؟**  
ج: تقنيًا لا، لكن من أجل سهولة الاستخدام يُفضَّل حصر التداخل إلى 3‑4 مستويات حتى يتمكن المستخدمون من مسح القائمة بسهولة.

**س: كيف يتعامل Aspose مع المستندات الكبيرة جدًا؟**  
ج: المكتبة تبث المحتوى وتوفر `optimizeResources()` لتقليل استهلاك الذاكرة؛ لا يزال يُنصح بمراقبة مساحة heap في JVM للملفات التي تتجاوز مئات الصفحات.

**س: هل يمكنني تعديل الإشارات المرجعية بعد إنشاء PDF؟**  
ج: نعم، يمكنك استخدام Aspose.PDF for Java لتعديل أو إضافة أو إزالة الإشارات المرجعية في PDF موجود.

**الموارد**
- [توثيق Aspose.Words](https://reference.aspose.com/words/java/)  
- [تحميل أحدث الإصدارات](https://releases.aspose.com/words/java/)  
- [شراء ترخيص](https://purchase.aspose.com/buy)  
- [نسخة تجريبية مجانية](https://releases.aspose.com/words/java/)  
- [طلب ترخيص مؤقت](https://purchase.aspose.com/temporary-license/)  
- [منتدى دعم Aspose](https://forum.aspose.com/c/words/10)

---

**آخر تحديث:** 2026-10-02  
**تم الاختبار مع:** Aspose.Words 25.3 for Java  
**المؤلف:** Aspose

## دروس ذات صلة

- [إضافة إشارات مرجعية Word باستخدام Aspose.Words for Java – الإدراج، التحديث، الحذف](/words/java/content-management/aspose-words-java-manage-bookmarks/)
- [حفظ Word كـ PDF باستخدام Aspose Words خطوة بخطوة دليل Java](/words/java/document-conversion-and-export/save-word-as-pdf-with-aspose-words-step-by-step-java-guide/)
- [تحويل Word إلى PDF باستخدام Aspose.Words for Java](/words/java/document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}