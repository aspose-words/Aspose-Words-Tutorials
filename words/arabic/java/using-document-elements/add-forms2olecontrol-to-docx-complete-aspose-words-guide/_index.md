---
category: general
date: 2026-07-23
description: تعلم كيفية إضافة Forms2OleControl إلى ملف DOCX باستخدام Aspose.Words.
  يوضح هذا الدليل خطوة بخطوة إدراج عنصر تحكم ActiveX CommandButton في Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add forms2olecontrol to docx
- insert ActiveX control in DOCX
- Aspose.Words Forms2OleControl example
- embed CommandButton in Word document
- Java DocumentBuilder ActiveX
language: ar
lastmod: 2026-07-23
og_description: أضف Forms2OleControl إلى DOCX على الفور. اتبع هذا الدليل العملي لتضمين
  زر CommandButton من نوع ActiveX باستخدام Aspose.Words للغة Java.
og_image_alt: Screenshot of Java code that adds Forms2OleControl to DOCX using Aspose.Words
og_title: إضافة Forms2OleControl إلى DOCX – دليل Aspose.Words الكامل
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: Learn how to add Forms2OleControl to DOCX using Aspose.Words. This
    step‑by‑step guide shows inserting an ActiveX CommandButton control in Java.
  headline: Add Forms2OleControl to DOCX – Complete Aspose.Words Guide
  type: TechArticle
- description: Learn how to add Forms2OleControl to DOCX using Aspose.Words. This
    step‑by‑step guide shows inserting an ActiveX CommandButton control in Java.
  name: Add Forms2OleControl to DOCX – Complete Aspose.Words Guide
  steps:
  - name: Using a Different ActiveX Control
    text: 'If you want a checkbox instead of a button, just change the control type:'
  - name: Embedding Multiple Controls
    text: Call `builder.insertForms2OleControl()` multiple times, moving the cursor
      with `builder.moveTo()` or inserting text between calls. Each call adds a new
      OLE container, so you can build complex forms inside a single DOCX.
  - name: Working with .NET
    text: The same logic applies to C#—the method names are identical (`DocumentBuilder.InsertForms2OleControl()`).
      If you’re on .NET, replace the Java syntax with its C# counterpart, but the
      **embed CommandButton in Word document** concept stays unchanged.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Java
- DOCX
title: إضافة Forms2OleControl إلى DOCX – دليل Aspose.Words الكامل
url: /ar/java/using-document-elements/add-forms2olecontrol-to-docx-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إضافة Forms2OleControl إلى DOCX – دليل Aspose.Words الكامل

هل تساءلت يومًا كيف **تضيف Forms2OleControl إلى DOCX** دون أن تجهد نفسك؟ لست الوحيد. سواء كنت تبني تقريرًا يعتمد على القوالب أو تحتاج إلى زر قابل للنقر داخل ملف Word، فإن تضمين عنصر تحكم ActiveX هو السر.

في هذا الدليل سنستعرض مثالًا عمليًا **يضيف Forms2OleControl إلى DOCX** باستخدام Aspose.Words for Java. ستشاهد الكود الكامل، وتفهم لماذا كل سطر مهم، وستحصل على نصائح للتعامل مع المشكلات التي غالبًا ما تعيق المطورين.

## ما ستتعلمه

- كيفية إعداد Aspose.Words في مشروع Java  
- الخطوات الدقيقة **لإدراج عنصر تحكم ActiveX في DOCX** (نعم، الكلمة المفتاحية الرئيسية مرة أخرى)  
- تكوين خصائص CommandButton بحيث يتصرف كعنصر واجهة مستخدم حقيقي  
- حفظ المستند والتحقق من أن العنصر مدمج فعليًا  

لا تحتاج إلى خبرة سابقة في ActiveX، لكن فهم أساسي لـ Java و Maven/Gradle سيجعل العملية أسهل. جاهز؟ لنبدأ.

---

## الخطوة 1: إعداد Aspose.Words في مشروعك

قبل أن تتمكن من **إضافة Forms2OleControl إلى DOCX**، تحتاج إلى مكتبة Aspose.Words على مسار الفئة (classpath). أسهل طريقة هي عبر Maven:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

> **نصيحة احترافية:** إذا كنت تستخدم Gradle، فإن المكافئ هو `implementation 'com.aspose:aspose-words:24.9'`.  

لماذا هذا مهم: Aspose.Words توفر طريقة `DocumentBuilder.insertForms2OleControl()` التي سنعتمد عليها **لإدراج عنصر تحكم ActiveX في DOCX**. بدون المكتبة، لن يعرف المترجم ما هو `Forms2OleControl`.

---

## الخطوة 2: إضافة Forms2OleControl إلى DOCX

الآن يأتي جوهر الدليل—هنا نضيف فعليًا **Forms2OleControl إلى DOCX**. سننشئ مستندًا جديدًا، نُنشئ كائن `DocumentBuilder`، ثم نستدعي طريقة الإدراج.

```java
import com.aspose.words.*;

public class ActiveXExample {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2.2: Insert an ActiveX Forms2OleControl (CommandButton)
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Step 2.3: Configure the CommandButton properties
        commandButton.setOleControlType(OleControlType.COMMANDBUTTON);
        commandButton.setName("MyButton");
        commandButton.setCaption("Click Me");

        // Step 2.4: Save the document with the embedded control
        String outPath = "output/ActiveXButton.docx";
        document.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

**ما الذي يحدث هنا؟**  

- `new Document()` يمنحنا لوحة فارغة. فكر فيها كصفحة جديدة جاهزة لـ **إدراج عنصر تحكم ActiveX في DOCX**.  
- `builder.insertForms2OleControl()` ينشئ حاوية OLE منخفضة المستوى التي تسميها Aspose.Words *Forms2OleControl*. هذه هي النداء الوحيد في الـ API الذي **يضيف Forms2OleControl إلى DOCX** فعليًا.  
- تعيين `OleControlType.COMMANDBUTTON` يخبر Word أن كائن OLE يجب أن يتصرف كزر CommandButton كلاسيكي—تمامًا كما تضيف زرًا إلى نموذج في مصمم الواجهة.  
- أخيرًا، `document.save(...)` يكتب ملف .docx، محافظًا على عنصر ActiveX المدمج.

---

## الخطوة 3: تكوين خصائص CommandButton (لماذا يهم)

إدراج العنصر فقط يعطيك مكانًا فارغًا. لجعله مفيدًا، عليك ضبط بعض الخصائص:

| الخاصية | الغرض | القيمة النموذجية |
|----------|---------|---------------|
| `setOleControlType` | يحدد نوع عنصر التحكم ActiveX (زر، مربع اختيار، إلخ) | `OleControlType.COMMANDBUTTON` |
| `setName` | المعرف الداخلي المستخدم من قبل ماكرو Word أو سكريبتات VBA | `"MyButton"` |
| `setCaption` | النص المعروض على سطح الزر | `"Click Me"` |

إذا تخطيت هذه الخطوات، سيظهر الزر باسم عام دون تسمية—شيء لن ينقره المستخدم. أيضًا، تذكر أن عناصر تحكم ActiveX **محددة للمنصة**؛ فهي تعمل فقط على أجهزة Windows التي تحتوي على مكتبات COM المناسبة.

> **احذر:** عندما تفتح ملف DOCX المُولد على منصة غير Windows (مثل macOS)، سيظهر Word صورة بديلة بدلاً من زر فعلي. هذه قيود طبيعية لـ ActiveX، وليست خطأ في الكود.

---

## الخطوة 4: حفظ المستند والتحقق منه

نداء `document.save(...)` يكتب ملف DOCX قياسي يمكن لأي نسخة حديثة من Microsoft Word فتحه. بعد تشغيل البرنامج، افتح `ActiveXButton.docx`:

1. ابحث عن زر “Click Me” في المكان الذي أدرجته فيه.  
2. انقر بزر الفأرة الأيمن على الزر → **Properties** لتأكيد الاسم والتسمية.  
3. انقر على الزر؛ سيظهر مربع رسالة بسيط في Word إذا كنت قد أرفقت ماكرو (خارج نطاق هذا الدليل).

إذا كان الزر مفقودًا، تحقق من أنك استخدمت مثال **Aspose.Words Forms2OleControl** بشكل صحيح وأن مجلد الإخراج موجود.

> **حالة خاصة:** إذا كنت تريد أن يُشغل الزر ماكرو، سيتعين عليك إضافة كود VBA إلى المستند بعد حفظه. يمكن لـ Aspose.Words حقن VBA باستخدام واجهة `Document.getBuiltInDocumentProperties()`، لكن هذا دليل كامل بحد ذاته.

---

## تنوعات شائعة ومشكلات محتملة

### استخدام عنصر تحكم ActiveX مختلف
إذا أردت مربع اختيار بدلاً من زر، فقط غيّر نوع العنصر:

```java
commandButton.setOleControlType(OleControlType.CHECKBOX);
commandButton.setCaption("Accept Terms");
```

### تضمين عناصر تحكم متعددة
استدعِ `builder.insertForms2OleControl()` عدة مرات، مع تحريك المؤشر باستخدام `builder.moveTo()` أو إدراج نص بين الاستدعاءات. كل استدعاء يضيف حاوية OLE جديدة، مما يتيح لك بناء نماذج معقدة داخل مستند DOCX واحد.

### العمل مع .NET
تنطبق نفس المنطق على C#—أسماء الطرق هي نفسها (`DocumentBuilder.InsertForms2OleControl()`). إذا كنت على .NET، استبدل صيغة Java بنظيرها في C#، لكن مفهوم **تضمين CommandButton في مستند Word** يبقى دون تغيير.

---

## الخلاصة

أصبح لديك الآن مثال عملي من البداية إلى النهاية **يضيف Forms2OleControl إلى DOCX** باستخدام Aspose.Words for Java. من خلال إنشاء مستند فارغ، إدراج عنصر التحكم ActiveX، تكوين خصائصه، وحفظ الملف، أصبحت متمكنًا من الخطوات الأساسية **لإدراج عنصر تحكم ActiveX في DOCX** ويمكنك توسيع هذا النمط إلى أنواع أخرى من العناصر.

ما الخطوة التالية؟ جرّب دمج هذه التقنية مع دمج البريد في Aspose.Words لإنشاء نماذج مخصصة، أو استكشف إضافة ماكرو VBA لجعل الزر يقوم بعمل فعلي. السماء هي الحد عندما تمزج **مثال Aspose.Words Forms2OleControl** مع منطق عملك الخاص.

برمجة سعيدة، ولا تتردد في ترك تعليق إذا واجهت أي صعوبات!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إنشاء حقول نموذج وإضافة محتوى باستخدام DocumentBuilder في Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [إضافة إشارات مرجعية إلى Word باستخدام Aspose.Words for Java – إدراج، تحديث، حذف](/words/english/java/content-management/aspose-words-java-manage-bookmarks/)
- [كيفية إضافة علامة مائية إلى المستندات باستخدام Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}