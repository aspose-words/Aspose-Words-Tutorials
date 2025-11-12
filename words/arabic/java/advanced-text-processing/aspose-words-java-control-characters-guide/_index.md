---
date: '2025-11-12'
description: تعلم كيفية إدراج الأحرف التحكمية، وإدارة عودة السطر، وإضافة فواصل الصفحات
  أو الأعمدة في جافا باستخدام Aspose.Words لتنسيق المستند بدقة.
keywords:
- Aspose.Words control characters
- Java document formatting with Aspose.Words
- inserting control characters in Java
- insert control characters java
- manage carriage returns
- add page break aspose
- insert non‑breaking space
- create multi‑column layout
language: ar
title: إدراج أحرف التحكم في جافا باستخدام Aspose.Words
url: /java/advanced-text-processing/aspose-words-java-control-characters-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إدراج أحرف التحكم في Java باستخدام Aspose.Words
## المقدمة
هل تحتاج إلى تحكم دقيق بالبكسل في فواصل الأسطر، والمسافات البادئة (Tabs)، أو تقسيم الصفحات عند إنشاء الفواتير، والتقارير، أو النشرات الإخبارية؟  
أحرف التحكم هي اللبنات غير المرئية التي تتيح لك تشكيل تخطيط المستند برمجياً.  
في هذا الدرس ستتعلم كيفية **إدراج**، **التحقق**، و**إدارة** أحرف التحكم مثل عودة السطر (carriage return)، والمسافات غير القابلة للكسر (non‑breaking space)، وفواصل الأعمدة باستخدام Aspose.Words for Java API.

**ما ستحققه:**
1. إدراج والتحقق من عودة السطر، وتغذية السطر (line feed)، وفواصل الصفحات.  
2. إضافة مسافات، علامات تبويب، مسافات غير قابلة للكسر، وفواصل الأعمدة لإنشاء تخطيطات متعددة الأعمدة.  
3. تطبيق نصائح الأداء وفق أفضل الممارسات لأتمتة المستندات على نطاق واسع.

## المتطلبات المسبقة
قبل أن نبدأ، تأكد من توفر ما يلي:

| المتطلب | التفاصيل |
|-------------|----------|
| **Aspose.Words for Java** | الإصدار 25.3 أو أحدث (يبقى الـ API ثابتاً عبر الإصدارات اللاحقة). |
| **JDK** | Java 8 + (يوصى بـ Java 11 أو 17). |
| **IDE** | IntelliJ IDEA، Eclipse، أو أي محرر يدعم Java. |
| **أداة البناء** | Maven **أو** Gradle لإدارة الاعتمادات. |
| **الترخيص** | ملف ترخيص Aspose.Words مؤقت أو مُشتَرٍ. |

### قائمة التحقق السريعة للبيئة
1. تثبيت Maven **أو** Gradle.  
2. وجود ملف الترخيص في مسار يمكن الوصول إليه (مثال: `src/main/resources/aspose.words.lic`).  
3. تجميع المشروع دون أخطاء.

## إعداد Aspose.Words
سنضيف المكتبة أولاً إلى المشروع، ثم نقوم بتحميل الترخيص. اختر نظام البناء الذي يناسب سير عملك.

### اعتماد Maven
أضف المقتطف التالي إلى ملف `pom.xml` داخل `<dependencies>`:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### اعتماد Gradle
أدرج هذا السطر داخل كتلة `dependencies` في `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### تهيئة الترخيص (كود Java)
```java
License license = new License();
license.setLicense("path/to/aspose.words.lic");
```

> **ملاحظة:** استبدل `"path/to/aspose.words.lic"` بالمسار الفعلي لملف الترخيص الخاص بك.

## الميزة 1: معالجة عودة السطر وفواصل الصفحات
تُعد عودة السطر (`ControlChar.CR`) وفواصل الصفحات (`ControlChar.PAGE_BREAK`) أساسية عندما تحتاج إلى أن يعكس النص الناتج التخطيط البصري للمستند.

### تنفيذ خطوة بخطوة
1. **إنشاء Document وDocumentBuilder جديدين.**  
2. **كتابة فقرتين.**  
3. **التحقق من أن النص المُولَّد يحتوي على أحرف التحكم المتوقعة.**  
4. **قص النص وإعادة التحقق من النتيجة.**

#### 1. إنشاء Document
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

#### 2. إدراج الفقرات
```java
builder.writeln("Hello world!");
builder.writeln("Hello again!");
```

#### 3. التحقق من أحرف التحكم
```java
String expectedTextWithCR = MessageFormat.format("Hello world!{0}", ControlChar.CR) +
        MessageFormat.format("Hello again!{0}", ControlChar.CR) +
        ControlChar.PAGE_BREAK;
assert doc.getText().equals(expectedTextWithCR) :
        "Text does not match expected value with control characters.";
```

#### 4. قص النص والتحقق
```java
String expectedTrimmedText = MessageFormat.format("Hello world!{0}", ControlChar.CR) + "Hello again!";
assert doc.getText().trim().equals(expectedTrimmedText) :
        "Trimmed text does not match expected value.";
```

**النتيجة:** الآن يحتوي النص المستخرج بـ `doc.getText()` على رموز CR وفواصل الصفحات الصريحة، مما يضمن أن الأنظمة المت downstream (مثل مُصدِّرات النص العادي) تحافظ على التخطيط.

## الميزة 2: إدراج أنواع مختلفة من أحرف التحكم
إلى جانب عودة السطر، توفر Aspose.Words ثوابت للمسافات، وعلامات التبويب، وتغذية السطر، وفواصل الفقرات، وفواصل الأعمدة. يوضح هذا القسم كيفية تضمين كل منها.

### تنفيذ خطوة بخطوة
1. **تهيئة DocumentBuilder جديد.**  
2. **كتابة أمثلة للمسافات، والمسافات غير القابلة للكسر، وعلامات التبويب.**  
3. **إضافة تغذية السطر، وفواصل الفقرات، وفواصل الأقسام، ثم التحقق من عدد العقد.**  
4. **إنشاء تخطيط بعمودين وإدراج فاصل عمود.**

#### 1. تهيئة DocumentBuilder
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

#### 2. إدراج أحرف المسافات
- **مسافة (`ControlChar.SPACE_CHAR`)**
```java
builder.write("Before space." + ControlChar.SPACE_CHAR + "After space.");
```
- **مسافة غير قابلة للكسر (`ControlChar.NON_BREAKING_SPACE`)**
```java
builder.write("Before NBSP." + ControlChar.NON_BREAKING_SPACE + "After NBSP.");
```
- **علامة تبويب (`ControlChar.TAB`)**
```java
builder.write("Before tab." + ControlChar.TAB + "After tab.");
```

#### 3. تغذية السطر، وفواصل الفقرات، وفواصل الأقسام
```java
// Verify initial paragraph count is 1
Assert.assertEquals(1, doc.getFirstSection().getBody()
        .getChildNodes(NodeType.PARAGRAPH, true).getCount());

// Insert a line feed (creates a new paragraph)
builder.write("Before line feed." + ControlChar.LINE_FEED + "After line feed.");
Assert.assertEquals(2, doc.getFirstSection().getBody()
        .getChildNodes(NodeType.PARAGRAPH, true).getCount());

// Insert a paragraph break
builder.write("Before paragraph break." + ControlChar.PARAGRAPH_BREAK + "After paragraph break.");
Assert.assertEquals(3, doc.getFirstSection().getBody()
        .getChildNodes(NodeType.PARAGRAPH, true).getCount());

// Insert a section break (still one Section object, but a break marker)
builder.write("Before section break." + ControlChar.SECTION_BREAK + "After section break.");
assert doc.getSections().getCount() == 1 :
        "Section count mismatch after section break.";
```

#### 4. فاصل عمود في تخطيط متعدد الأعمدة
```java
// Add a second section to host two columns
doc.appendChild(new Section(doc));
builder.moveToSection(1);
builder.getCurrentSection().getPageSetup().getTextColumns().setCount(2);

// Insert a column break between the two columns
builder.write("Text at end of column 1." + ControlChar.COLUMN_BREAK + "Text at beginning of column 2.");
```

**النتيجة:** يحتوي المستند الآن على صفحة ذات عمودين حيث يتدفق النص تلقائياً من العمود الأول إلى الثاني بعد `COLUMN_BREAK`.

## تطبيقات عملية
| السيناريو | كيف تساعد أحرف التحكم |
|----------|-----------------------|
| **إنشاء الفواتير** | استخدم `PAGE_BREAK` لبدء صفحة جديدة لكل دفعة فواتير. |
| **التقرير المالي** | رتب الأرقام باستخدام `TAB` واحفظ العناوين معًا باستخدام `NON_BREAKING_SPACE`. |
| **تخطيط النشرة الإخبارية** | أنشئ مقالات جنبًا إلى جنب باستخدام `COLUMN_BREAK` في قسم متعدد الأعمدة. |
| **تصدير محتوى CMS** | حافظ على بنية الأسطر عند تحويل النص الغني إلى نص عادي عبر `LINE_FEED`. |
| **القوالب الآلية** | أدخل `PARAGRAPH_BREAK` أو `SECTION_BREAK` ديناميكياً بناءً على مدخلات المستخدم. |

## اعتبارات الأداء
* **الإدراج على دفعات:** اجمع عدة استدعاءات `write` في عملية واحدة لتقليل عمليات إعادة التدفق الداخلية.  
* **تجنب التنقل المتكرر بين العقد:** خزن نتائج `NodeCollection` عندما تحتاج إلى عد الفقرات بشكل متكرر.  
* **تحليل المستندات الكبيرة:** استخدم أدوات تحليل Java (مثل VisualVM) لتحديد نقاط الاختناق في حلقات معالجة النص.

## الخلاصة
أصبح لديك الآن طريقة خطوة بخطوة **لإدراج**، **للتحقق**، و**لتحسين** أحرف التحكم في مستندات Java باستخدام Aspose.Words. تُتيح لك هذه التقنيات إنتاج فواتير، تقارير، ومنشورات متعددة الأعمدة بمستوى احترافي برمجياً.

## الخطوات التالية
1. جرب ثوابت `ControlChar` إضافية مثل `EM_SPACE` أو `EN_SPACE`.  
2. ادمج أحرف التحكم مع حقول الدمج البريدي لإنشاء مستندات ديناميكية.  
3. استكشف ميزات Aspose.Words مثل **حماية المستند**، **العلامات المائية**، و**إدراج الصور** لإثراء مخرجاتك أكثر.

**جرّبها اليوم:** أضف المقاطع البرمجية أعلاه إلى مشروع Java التالي وشاهد كيف يمكن لأحرف التحكم الدقيقة تحسين سير عمل المستندات لديك!

## الأسئلة المتكررة
1. **ما هو حرف التحكم؟**  
   رمز غير قابل للطباعة (مثل علامة التبويب أو تغذية السطر) يؤثر على تخطيط المستند دون الظهور كنص مرئي.

2. **كيف أبدأ باستخدام Aspose.Words for Java؟**  
   أضف اعتماد Maven أو Gradle، حمّل الترخيص، واتبع أمثلة الكود في هذا الدليل.

3. **هل يمكنني استخدام فواصل الأعمدة في النشرات الإخبارية؟**  
   نعم—`ControlChar.COLUMN_BREAK` يعمل مع خاصية `TextColumns` لتقسيم المحتوى عبر الأعمدة.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}