---
date: '2025-11-12'
description: تعلم خطوة بخطوة كيفية إدراج فواصل الصفحات، والمسافات البادئة، والمسافات
  غير القابلة للكسر، وتنسيقات متعددة الأعمدة باستخدام Aspose.Words للغة Java – عزّز
  أتمتة مستنداتك اليوم.
keywords:
- how to insert control characters
- add page break java
- manage carriage return aspose
- insert non breaking space
- create multi column layout
- Aspose.Words control characters
- Java document formatting
- text layout automation
- document generation Java
- Aspose.Words API
language: ar
title: إدراج أحرف التحكم باستخدام Aspose.Words للـ Java
url: /java/advanced-text-processing/aspose-words-java-control-characters-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إدراج أحرف التحكم باستخدام Aspose.Words for Java

## لماذا تُعد أحرف التحكم مهمة في مستندات Java
عند إنشاء الفواتير أو التقارير أو النشرات إحصائيًا، يكون تخطيط النص الدقيق أمرًا لا يمكن التفاوض عليه. تسمح لك أحرف التحكم مثل **فواصل الصفحات**، **المسافات البادئة**، و**المسافات غير القابلة للكسر** بتحديد مكان ظهور المحتوى بالضبط دون تعديل يدوي. في هذا البرنامج التعليمي ستتعرف على كيفية إدارة هذه الأحرف باستخدام Aspose.Words for Java API، لتظهر مستنداتك احترافية من أول مرة تُنشأ فيها.

**ما ستحققه في هذا الدليل**
1. إدراج والتحقق من عودة السطر (carriage return)، تغذية السطر (line feed)، وفواصل الصفحات.  
2. إضافة المسافات، والمسافات البادئة (tabs)، والمسافات غير القابلة للكسر لتنسيق النص.  
3. إنشاء تخطيطات متعددة الأعمدة باستخدام فواصل الأعمدة.  
4. تطبيق نصائح الأداء المثلى للمستندات الكبيرة.

## المتطلبات المسبقة
قبل أن نبدأ، تأكد من أن لديك ما يلي جاهزًا:

| المتطلب | التفاصيل |
|-------------|---------|
| **Aspose.Words for Java** | الإصدار 25.3 أو أحدث (API متوافق مع الإصدارات السابقة). |
| **JDK** | 8 أو أعلى. |
| **IDE** | IntelliJ IDEA، Eclipse، أو أي بيئة تطوير Java تفضلها. |
| **أداة بناء** | Maven **أو** Gradle لإدارة الاعتمادات. |
| **رخصة** | ملف رخصة Aspose.Words مؤقت أو مُشتَرَى (`aspose.words.lic`). |

### قائمة التحقق لإعداد البيئة
1. تثبيت Maven **أو** Gradle.  
2. إضافة اعتماد Aspose.Words (انظر القسم التالي).  
3. وضع ملف الرخصة في موقع آمن وتدوين المسار.

## إضافة Aspose.Words إلى مشروعك

### Maven
أدرج المقتطف التالي في ملف `pom.xml` الخاص بك:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle
أضف هذا السطر إلى `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### تهيئة الرخصة
بعد الحصول على الرخصة، قم بتهيئتها في بداية تطبيقك:

```java
License license = new License();
license.setLicense("path/to/aspose.words.lic");
```

> **ملاحظة:** بدون رخصة تعمل المكتبة في وضع التقييم، والذي يضيف علامات مائية.

## دليل التنفيذ

سنغطي ميزتين أساسيتين: **معالجة عودة السطر** و**إدراج أحرف التحكم المتنوعة**. كل ميزة مقسمة إلى خطوات مرقمة، وتسبق كل كتلة شفرة فقرة توضيحية قصيرة.

### الميزة 1 – معالجة عودة السطر وفواصل الصفحات
أحرف التحكم مثل `ControlChar.CR` (عودة السطر) و`ControlChar.PAGE_BREAK` (فاصل صفحة) تحدد التدفق المنطقي للمستند. يوضح المثال التالي كيفية التحقق من أن هذه الأحرف موضوعة بشكل صحيح.

#### خطوة بخطوة

1. **إنشاء Document وDocumentBuilder جديدين**  
   كائن `Document` هو الحاوية لكل المحتوى؛ يوفر `DocumentBuilder` API سلس لإضافة النص.

   ```java
   Document doc = new Document();
   DocumentBuilder builder = new DocumentBuilder(doc);
   ```

2. **إدراج فقرتين بسيطتين**  
   كل استدعاء `writeln` يضيف تلقائيًا فاصل فقرة.

   ```java
   builder.writeln("Hello world!");
   builder.writeln("Hello again!");
   ```

3. **بناء السلسلة المتوقعة مع أحرف التحكم**  
   نستخدم `MessageFormat` لتضمين `ControlChar.CR` و`ControlChar.PAGE_BREAK` في النص المتوقع.

   ```java
   String expectedTextWithCR = MessageFormat.format("Hello world!{0}", ControlChar.CR) +
           MessageFormat.format("Hello again!{0}", ControlChar.CR) +
           ControlChar.PAGE_BREAK;
   assert doc.getText().equals(expectedTextWithCR) :
           "Text does not match expected value with control characters.";
   ```

4. **قص نص المستند وإعادة التحقق**  
   يزيل القص (trim) المسافات البيضاء الزائدة مع الحفاظ على فواصل الأسطر المقصودة.

   ```java
   String expectedTrimmedText = MessageFormat.format("Hello world!{0}", ControlChar.CR) + "Hello again!";
   assert doc.getText().trim().equals(expectedTrimmedText) :
           "Trimmed text does not match expected value.";
   ```

> **النتيجة:** تؤكد العبارات الشرطية أن تمثيل النص الداخلي للمستند يحتوي على عودة السطر وفاصل الصفحة بالضبط كما تتوقع.

### الميزة 2 – إدراج أحرف تحكم متنوعة
الآن نستكشف كيفية تضمين المسافات، والمسافات البادئة، وتغذيات الأسطر، وفواصل الفقرات، وفواصل الأعمدة مباشرة في المستند.

#### خطوة بخطوة

1. **تهيئة DocumentBuilder جديد**  
   البدء بمستند نظيف يضمن عزل الأمثلة.

   ```java
   Document doc = new Document();
   DocumentBuilder builder = new DocumentBuilder(doc);
   ```

2. **إدراج أحرف متعلقة بالمسافات**  

   *حرف المسافة (`ControlChar.SPACE_CHAR`)*  
   ```java
   builder.write("Before space." + ControlChar.SPACE_CHAR + "After space.");
   ```

   *المسافة غير القابلة للكسر (`ControlChar.NON_BREAKING_SPACE`)*  
   ```java
   builder.write("Before NBSP." + ControlChar.NON_BREAKING_SPACE + "After NBSP.");
   ```

   *حرف التبويب (`ControlChar.TAB`)*  
   ```java
   builder.write("Before tab." + ControlChar.TAB + "After tab.");
   ```

3. **إضافة تغذيات الأسطر وفواصل الفقرات**  

   *تغذية السطر (Line feed) تُنشئ سطرًا جديدًا داخل نفس الفقرة.*  
   ```java
   // Verify that we start with a single paragraph
   Assert.assertEquals(1, doc.getFirstSection().getBody()
           .getChildNodes(NodeType.PARAGRAPH, true).getCount());

   builder.write("Before line feed." + ControlChar.LINE_FEED + "After line feed.");

   // After inserting a line feed, a second paragraph should appear
   Assert.assertEquals(2, doc.getFirstSection().getBody()
           .getChildNodes(NodeType.PARAGRAPH, true).getCount());
   ```

   *فاصل الفقرة (`ControlChar.PARAGRAPH_BREAK`)*  
   ```java
   builder.write("Before paragraph break." + ControlChar.PARAGRAPH_BREAK + "After paragraph break.");
   Assert.assertEquals(3, doc.getFirstSection().getBody()
           .getChildNodes(NodeType.PARAGRAPH, true).getCount());
   ```

   *فاصل القسم (`ControlChar.SECTION_BREAK`)*  
   ```java
   builder.write("Before section break." + ControlChar.SECTION_BREAK + "After section break.");
   assert doc.getSections().getCount() == 1 :
           "Section count mismatch after section break.";
   ```

4. **إنشاء تخطيط متعدد الأعمدة باستخدام فاصل عمود**  

   أولاً، أضف قسمًا ثانيًا ومكّن عمودين:

   ```java
   doc.appendChild(new Section(doc));
   builder.moveToSection(1);
   builder.getCurrentSection().getPageSetup().getTextColumns().setCount(2);
   ```

   ثم أدخل فاصل عمود لنقل المحتوى من العمود 1 إلى العمود 2:

   ```java
   builder.write("Text at end of column 1." + ControlChar.COLUMN_BREAK + "Text at beginning of column 2.");
   ```

> **النتيجة:** بعد تشغيل الشفرة، يحتوي المستند على مسافات، وتبويبات، وتغذيات أسطر، وفواصل فقرات، وفواصل أقسام، وتخطيط عمودين—كل ذلك يتم بواسطة أحرف التحكم في Aspose.Words.

## حالات الاستخدام الواقعية
| السيناريو | كيف تساعد أحرف التحكم |
|----------|-----------------------|
| **إنشاء الفواتير** | فرض فواصل صفحات بعد عدد معين من بنود السطر للحفاظ على المجموعات في صفحة جديدة. |
| **التقارير المالية** | محاذاة الأعمدة باستخدام التبويبات والمسافات غير القابلة للكسر لتنسيق الأرقام بشكل ثابت. |
| **النشرات والكتيبات** | نشر فواصل الأعمدة للمقالات المتجاورة دون الحاجة لتصميم يدوي. |
| **المستندات المدفوعة من CMS** | إدراج تغذيات أسطر وفواصل فقرات ديناميكيًا بناءً على محتوى المستخدم. |
| **إنشاء مستندات دفعي** | استخدام إدراج جماعي لأحرف التحكم لتقليل عبء المعالجة. |

## نصائح الأداء للمستندات الكبيرة
- **الإدراج على دفعات:** اجمع عدة استدعاءات `write` في بيان واحد عندما يكون ذلك ممكنًا.  
- **تجنب حسابات التخطيط المتكررة:** أدخل جميع أحرف التحكم قبل تنفيذ عمليات ثقيلة مثل الحفظ أو التصدير.  
- **استخدم Java Flight Recorder** لتحديد أي عنق زجاجة في معالجة النص.

## الخلاصة
أصبح لديك الآن طريقة واضحة خطوة بخطوة لإتقان أحرف التحكم باستخدام Aspose.Words for Java. من خلال إدراج المسافات، والتبويبات، وتغذيات الأسطر، وفواصل الصفحات، وفواصل الأعمدة برمجيًا، يمكنك إنتاج فواتير، وتقارير، ومنشورات متعددة الأعمدة منسقة تمامًا دون تعديل يدوي.

**الخطوات التالية:**  
- جرب دمج أحرف التحكم مع رموز الحقول لإنشاء محتوى ديناميكي.  
- استكشف ميزات Aspose.Words مثل الدمج البريدي (mail‑merge)، حماية المستند، وتحويل PDF لتوسيع خط أنابيب الأتمتة الخاص بك.

**دعوة للعمل:** جرّب دمج هذه المقاطع البرمجية في مشروع Java التالي لك ولاحظ مدى تحسين نظافة وموثوقية المستندات التي تُنشئها!

## الأسئلة المتكررة

1. **ما هو حرف التحكم؟**  
   رمز غير قابل للطباعة (مثل التبويب، تغذية السطر، فاصل الصفحة) يؤثر على تخطيط النص دون الظهور كحرف مرئي.

2. **هل أحتاج رخصة مدفوعة لاستخدام هذه الميزات؟**  
   رخصة مؤقتة تكفي للتقييم؛ الرخصة الكاملة تزيل العلامات المائية وتفتح جميع إمكانيات الـ API.

3. **هل يمكنني استخدام `ControlChar.COLUMN_BREAK` في مستند ذو عمود واحد؟**  
   نعم، لكن الفاصل سيأخذ مفعوله فقط بعد تكوين القسم ليحتوي على أعمدة متعددة عبر `PageSetup.getTextColumns().setCount()`.

4. **هل هناك طريقة لسرد جميع أحرف التحكم المتاحة؟**  
   جميع الثوابت موجودة في الفئة `com.aspose.words.ControlChar`؛ راجع وثائق الـ API الرسمية للحصول على القائمة الكاملة.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}