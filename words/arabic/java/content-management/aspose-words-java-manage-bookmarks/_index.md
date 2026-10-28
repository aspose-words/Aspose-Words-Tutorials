---
date: '2026-10-28'
description: تعرف على كيفية استخدام رخصة Aspose.Words for Java لإضافة وتحديث وحذف
  إشارات Word برمجيًا. يتضمن خطوات إدراج إشارة java وحذف إشارات المستند.
keywords:
- aspose words java license
- how to add bookmark
- insert bookmark java
- delete bookmarks document
lastmod: '2026-10-28'
og_description: تعرف على كيفية استخدام رخصة Aspose.Words for Java لإضافة وتحديث وحذف
  إشارات Word برمجيًا. يتضمن خطوات إدراج إشارة java وحذف إشارات المستند.
og_image_alt: Guide showing how to manage Word bookmarks with Aspose.Words for Java
  license
og_title: 'رخصة Aspose.Words for Java: إضافة وإزالة إشارات Word'
schemas:
- author: Aspose
  dateModified: '2026-10-28'
  description: Learn how to use the Aspose.Words for Java license to add, update,
    and delete Word bookmarks programmatically. Includes insert bookmark java and
    delete bookmarks document steps.
  headline: 'Aspose.Words for Java license: add and remove Word bookmarks'
  type: TechArticle
- description: Learn how to use the Aspose.Words for Java license to add, update,
    and delete Word bookmarks programmatically. Includes insert bookmark java and
    delete bookmarks document steps.
  name: 'Aspose.Words for Java license: add and remove Word bookmarks'
  steps:
  - name: '**Free trial** – explore the API without cost.'
    text: '**Free trial** – explore the API without cost.'
  - name: '**Temporary license** – extend testing beyond the trial period.'
    text: '**Temporary license** – extend testing beyond the trial period.'
  - name: '**Full license** – required for production deployments; this is where the
      **aspose words java license** is applied.'
    text: '**Full license** – required for production deployments; this is where the
      **aspose words java license** is applied.'
  - name: '**Legal contracts** – Jump straight to clauses or definitions.'
    text: '**Legal contracts** – Jump straight to clauses or definitions.'
  - name: '**Technical manuals** – Link to code snippets or troubleshooting steps.'
    text: '**Technical manuals** – Link to code snippets or troubleshooting steps.'
  - name: '**Data‑heavy reports** – Reference specific table cells for dynamic dashboards.'
    text: '**Data‑heavy reports** – Reference specific table cells for dynamic dashboards.'
  - name: '**Academic papers** – Navigate between sections, figures, and citations.'
    text: '**Academic papers** – Navigate between sections, figures, and citations.'
  - name: '**Business proposals** – Highlight key metrics for quick stakeholder review.'
    text: '**Business proposals** – Highlight key metrics for quick stakeholder review.'
  type: HowTo
- questions:
  - answer: Yes. Load the document, use `DocumentBuilder` to navigate to the desired
      location, and call `startBookmark`/`endBookmark`. Save the document afterwards.
    question: Can I add a bookmark to an existing document without rewriting the whole
      file?
  - answer: Use `Bookmark.remove()`; this deletes the bookmark marker only, leaving
      the content untouched.
    question: How do I delete a bookmark without removing its surrounding text?
  - answer: Iterate through `doc.getRange().getBookmarks()` and call `getName()` on
      each `Bookmark` object.
    question: Is there a way to list all bookmark names in a document?
  - answer: 'Yes. Pass the password to the `Document` constructor: `new Document(path,
      new LoadOptions() {{ setPassword("pwd"); }})`.'
    question: Does Aspose.Words support password‑protected Word files?
  - answer: Aspose.Words for Java supports Java 8 through Java 17, including all LTS
      releases.
    question: Which Java versions are officially supported?
  type: FAQPage
tags:
- aspose words java
- bookmark management
- java document processing
- aspose license
title: 'رخصة Aspose.Words for Java: إضافة وإزالة إشارات Word'
url: /ar/java/content-management/aspose-words-java-manage-bookmarks/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إضافة إشارات مرجعية في Word باستخدام Aspose.Words for Java: الإدراج، التحديث، والإزالة

## مقدمة
تتيح لك **aspose words java license** العمل مع ملفات Microsoft Word دون الحاجة إلى تثبيت Microsoft Office. يتيح لك إضافة إشارات مرجعية في Word وضع علامة على أي جزء من المستند—فقرات، خلايا جدول، أو صور—حتى تتمكن من القفز مباشرة إلى ذلك المحتوى لاحقًا. باستخدام Aspose.Words for Java يمكنك إدراج، تحديث، وحذف هذه الإشارات برمجيًا، مما يحول ملفًا ثابتًا إلى أصل ديناميكي قابل للبحث ويتوسع عبر بيئات Windows وLinux وmacOS.

## إجابات سريعة
- **ما هي الفئة الأساسية لإنشاء المستندات؟** `DocumentBuilder`  
- **ما هي الطريقة التي تبدأ إشارة مرجعية؟** `builder.startBookmark("BookmarkName")`  
- **هل يمكنني إزالة إشارة مرجعية دون حذف محتواها؟** نعم، استخدم `Bookmark.remove()`  
- **هل أحتاج إلى ترخيص للاستخدام في الإنتاج؟** بالتأكيد—طبق ترخيص Aspose.Words for Java الخاص بك.  
- **هل Aspose.Words متوافق مع Java 17؟** نعم، يدعم Java 8 إلى 17.

## ما هو “add bookmarks word”؟
إضافة إشارات مرجعية في Word تعني وضع علامة مسماة داخل ملف Microsoft Word يمكن الإشارة إليها لاحقًا عبر الكود. يمكن للعلامة (الإشارة المرجعية) أن تحيط بأي عقدة—نص، خلية جدول، صورة—مما يتيح لك تحديد، قراءة، أو استبدال ذلك المحتوى برمجيًا.

## لماذا إعداد Aspose.Words for Java؟
إعداد **aspose.words java** يمنحك واجهة برمجة تطبيقات قوية خالية من الاعتمادات وقت التشغيل لأتمتة Word. يتيح لك إنشاء، تعديل، وعرض مستندات Word بالكامل في Java دون الحاجة إلى Microsoft Office، ويدعم ميزات متقدمة مثل دمج البريد، تحويل المستندات، ومعالجة التخطيطات المعقدة. ستحصل على:

- التحكم الكامل في بنية المستند دون الحاجة إلى تثبيت Microsoft Office.  
- معالجة عالية الأداء للملفات الكبيرة؛ يمكن لـ Aspose.Words التعامل مع مستندات من 500 صفحة في أقل من 3 ثوانٍ على عتاد خادم قياسي.  
- توافق عبر الأنظمة (Windows، Linux، macOS).  

الآن بعد أن فهمت “السبب”، دعنا نجهز البيئة.

## المتطلبات المسبقة
- **Aspose.Words for Java** الإصدار 25.3 أو أحدث.  
- JDK 8 أو أحدث (يوصى بـ Java 17).  
- بيئة تطوير متكاملة مثل IntelliJ IDEA أو Eclipse.  
- معرفة أساسية بـ Java وإلمام بـ Maven أو Gradle.

## إعداد Aspose.Words
قم بتضمين المكتبة في مشروعك إما عبر Maven أو Gradle:

### تبعية Maven
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### تنفيذ Gradle
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### خطوات الحصول على الترخيص
1. **تجربة مجانية** – استكشف الـ API بدون تكلفة.  
2. **ترخيص مؤقت** – تمديد الاختبار بعد فترة التجربة.  
3. **ترخيص كامل** – مطلوب للنشر في الإنتاج؛ هنا يتم تطبيق **aspose words java license**.

تهيئة الترخيص في كود Java الخاص بك:

```java
License license = new License();
license.setLicense("path/to/your/aspose.words.lic");
```

## كيف تستخدم ترخيص Aspose.Words for Java لإدارة الإشارات المرجعية؟
حمّل الترخيص أولاً، ثم يمكنك بأمان إضافة، تحديث، أو حذف الإشارات المرجعية دون مواجهة حدود التقييم. يزيل الترخيص قيود 20 صفحة والعلامة المائية، مما يسمح بحجم مستند غير محدود والوصول الكامل للميزات. من خلال تطبيق الترخيص أثناء التشغيل، يمكنك أيضًا تمكين جميع واجهات برمجة التطبيقات المتميزة، مثل التحويل عالي الدقة، التنسيق المتقدم، ودعم المستندات المشفرة، مما يضمن موثوقية على مستوى الإنتاج.

### إدراج إشارة مرجعية

#### نظرة عامة
إدراج إشارة مرجعية يتيح لك وضع علامة على قطعة محتوى لاسترجاعها لاحقًا.

#### تعريف المرجع
`DocumentBuilder` هو API قائم على المؤشر يتيح لك إدراج نصوص، جداول، صور، وإشارات مرجعية في مستند Word برمجيًا.

#### الخطوات
**1. تهيئة المستند والباني:**  
```java
Document doc = new Document();
documentBuilder builder = new DocumentBuilder(doc);
```  

**2. بدء وإنهاء الإشارة المرجعية:**  
```java
builder.startBookmark("My Bookmark");
builder.write("Contents of My Bookmark.");
builder.endBookmark("My Bookmark");
doc.save(YOUR_OUTPUT_DIRECTORY + "Bookmarks.Insert.docx");
```  
*لماذا؟* وضع علامة على نص معين بإشارة مرجعية يجعل التنقل والتحديثات اللاحقة أمرًا بسيطًا.

### الوصول إلى إشارة مرجعية والتحقق منها

#### نظرة عامة
بعد إضافة إشارة مرجعية، غالبًا ما تحتاج إلى تأكيد وجودها قبل التلاعب بها.

#### تعريف المرجع
`Bookmark` يمثل موقعًا مسمىً في شجرة المستند يمكنك الاستعلام عنه، تحريكه، أو حذفه.

#### الخطوات
**1. تحميل المستند:**  
```java
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "Bookmarks.Insert.docx");
```  

**2. التحقق من اسم الإشارة المرجعية:**  
```java
String bookmarkName = doc.getRange().getBookmarks().get(0).getName();
if (!"My Bookmark".equals(bookmarkName)) {
    throw new AssertionError("Bookmark name does not match expected value.");
}
```  
*لماذا؟* التحقق يمنع التغييرات العرضية على القسم الخطأ.

### إنشاء وتحديث وطباعة الإشارات المرجعية

#### نظرة عامة
إدارة عدة إشارات مرجعية في آن واحد أمر شائع في التقارير والعقود.

#### الخطوات
**1. إنشاء عدة إشارات مرجعية:**  
```java
Document doc = new Document();
documentBuilder builder = new DocumentBuilder(doc);
for (int i = 1; i <= 3; i++) {
    String bookmarkName = "MyBookmark_" + i;
    builder.write("Text before bookmark.");
    builder.startBookmark(bookmarkName);
    builder.write(MessageFormat.format("Text inside {0}.", bookmarkName));
    builder.endBookmark(bookmarkName);
    builder.writeln("Text after bookmark.");
}
```  

**2. تحديث الإشارات المرجعية:**  
```java
BookmarkCollection bookmarks = doc.getRange().getBookmarks();
bookmarks.get(0).setName("{bookmarks[0].Name}_NewName");
bookmarks.get("MyBookmark_2").setText("Updated text contents of {bookmarks[1].Name}");
```  

**3. طباعة معلومات الإشارة المرجعية:**  
```java
for (int i = 0; i < bookmarks.getCount(); i++) {
    Bookmark bookmark = bookmarks.get(i);
    System.out.println(bookmark.getName() + ": " + bookmark.getText().trim());
}
doc.save(YOUR_OUTPUT_DIRECTORY + "UpdatedBookmarks.docx");
```  
*لماذا؟* تحديث أسماء أو نصوص الإشارات المرجعية يحافظ على توافق المستند مع قواعد الأعمال المتغيرة.

### العمل مع إشارات مرجعية لأعمدة الجداول

#### نظرة عامة
الإشارات داخل الجداول تتيح لك استهداف خلايا دقيقة، مفيد للتقارير المدفوعة بالبيانات.

#### الخطوات
**1. تحديد إشارات مرجعية للأعمدة:**  
```java
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "Table column bookmarks.doc");
for (Bookmark bookmark : doc.getRange().getBookmarks()) {
    if (bookmark.isColumn()) {
        Row row = (Row) bookmark.getBookmarkStart().getAncestor(NodeType.ROW);
        if (row != null && bookmark.getFirstColumn() < row.getCells().getCount()) {
            System.out.println(MessageFormat.format("First Column: {0}", row.getCells().get(bookmark.getFirstColumn()).getText().trim()));
            System.out.println(MessageFormat.format("Last Column: {0}", row.getCells().get(bookmark.getLastColumn()).getText().trim()));
        }
    }
}
```  
*لماذا؟* هذا المنطق يستخرج بيانات خاصة بالعمود دون الحاجة إلى تحليل الجدول بالكامل.

### إزالة الإشارات المرجعية من مستند

#### نظرة عامة
عندما لا تكون الإشارة المرجعية ضرورية بعد الآن، فإن إزالتها تحافظ على نظافة المستند وتحسن الأداء.

#### الخطوات
**1. إدراج عدة إشارات مرجعية:**  
```java
Document doc = new Document();
documentBuilder builder = new DocumentBuilder(doc);
for (int i = 1; i <= 5; i++) {
    String bookmarkName = "MyBookmark_" + i;
    builder.startBookmark(bookmarkName);
    builder.write(MessageFormat.format("Text inside {0}.", bookmarkName));
    builder.endBookmark(bookmarkName);
    builder.insertBreak(BreakType.PARAGRAPH_BREAK);
}
```  

**2. إزالة الإشارات المرجعية:**  
```java
BookmarkCollection bookmarks = doc.getRange().getBookmarks();
bookmarks.get(0).remove();
bookmarks.remove(bookmarks.get("MyBookmark_2"));
doc.getRange().getBookmarks().removeAt(1);
doc.getRange().getBookmarks().clear();
doc.save(YOUR_OUTPUT_DIRECTORY + "RemovedBookmarks.docx");
```  
*لماذا؟* إدارة الإشارات المرجعية بكفاءة تمنع الفوضى وتقلل حجم الملف.

## تطبيقات عملية
1. **العقود القانونية** – الانتقال مباشرة إلى البنود أو التعريفات.  
2. **الأدلة التقنية** – ربط بقطعات الشيفرة أو خطوات استكشاف الأخطاء.  
3. **تقارير كثيفة البيانات** – الإشارة إلى خلايا جدول محددة للوحة معلومات ديناميكية.  
4. **الأوراق الأكاديمية** – التنقل بين الأقسام، الرسوم، والاقتباسات.  
5. **العروض التجارية** – إبراز المقاييس الرئيسية لمراجعة سريعة من أصحاب المصلحة.

## اعتبارات الأداء
- **حافظ على عدد الإشارات المرجعية معقولًا** في المستندات الكبيرة جدًا؛ كل إشارة مرجعية تضيف عبئًا صغيرًا.  
- استخدم **أسماء مختصرة ووصفية** (مثال: `Clause_5_Confidentiality`).  
- بانتظام **نظف الإشارات المرجعية غير المستخدمة** باستخدام خطوات الإزالة المذكورة أعلاه.

## المشكلات الشائعة والحلول

| المشكلة | الحل |
|-------|----------|
| *لم يتم العثور على الإشارة المرجعية بعد الحفظ* | تحقق من أنك تستخدم الاسم الدقيق للإشارة المرجعية (حسّاس لحالة الأحرف). |
| *نص الإشارة المرجعية يظهر فارغًا* | تأكد من استدعاء `builder.write()` **بين** `startBookmark` و `endBookmark`. |
| *تباطؤ الأداء على الملفات الضخمة* | قصر الإشارات المرجعية على الأقسام الضرورية وتنظيفها عندما لا تكون مطلوبة. |
| *الترخيص غير مطبق* | تأكد من أن مسار ملف `.lic` صحيح وأن الملف متاح أثناء التشغيل. |

## الأسئلة المتكررة

**س: هل يمكنني إضافة إشارة مرجعية إلى مستند موجود دون إعادة كتابة الملف بالكامل؟**  
ج: نعم. قم بتحميل المستند، استخدم `DocumentBuilder` للتنقل إلى الموقع المطلوب، واستدعِ `startBookmark`/`endBookmark`. احفظ المستند بعد ذلك.

**س: كيف أحذف إشارة مرجعية دون إزالة النص المحيط بها؟**  
ج: استخدم `Bookmark.remove()`؛ هذا يحذف علامة الإشارة المرجعية فقط، ويترك المحتوى دون تعديل.

**س: هل هناك طريقة لسرد جميع أسماء الإشارات المرجعية في مستند؟**  
ج: قم بالتكرار عبر `doc.getRange().getBookmarks()` واستدعِ `getName()` على كل كائن `Bookmark`.

**س: هل يدعم Aspose.Words ملفات Word المحمية بكلمة مرور؟**  
ج: نعم. مرّر كلمة المرور إلى مُنشئ `Document`: `new Document(path, new LoadOptions() {{ setPassword("pwd"); }})`.

**س: أي إصدارات Java مدعومة رسميًا؟**  
ج: يدعم Aspose.Words for Java إصدارات Java 8 إلى Java 17، بما في ذلك جميع إصدارات LTS.

---

**آخر تحديث:** 2026-10-28  
**تم الاختبار مع:** Aspose.Words for Java 25.3  
**المؤلف:** Aspose

## دروس مرتبطة

- [إضافة عنصر تحكم محتوى في مستند Word باستخدام Aspose Words](/words/java/document-manipulation/add-content-control-in-word-document-with-aspose-words/)
- [استخراج الروابط التشعبية في Word Java – إتقان إدارة الروابط التشعبية مع Aspose.Words](/words/java/content-management/master-hyperlink-management-word-aspose-words-java/)
- [كيفية إنشاء حقول نموذج وإضافة محتوى باستخدام DocumentBuilder في Aspose.Words for Java](/words/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}