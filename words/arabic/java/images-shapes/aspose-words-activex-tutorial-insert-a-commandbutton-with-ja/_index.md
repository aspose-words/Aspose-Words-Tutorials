---
category: general
date: 2026-08-07
description: يظهر دليل Aspose.Words ActiveX كيفية إضافة عنصر تحكم CommandButton إلى
  مستند Word باستخدام Java. تعلّم الكود الكامل، والإعدادات، وخطوات الحفظ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose words activex tutorial
- aspose.words java
- activeX control java
- documentbuilder insert control
- forms2olecontrol usage
language: ar
lastmod: 2026-08-07
og_description: يشرح دليل Aspose.Words ActiveX كيفية تضمين عنصر تحكم CommandButton
  ActiveX في مستند Word باستخدام Java. اتبع المثال الكامل لإنشاء المستند وتكوينه وحفظه.
og_image_alt: Screenshot of a Word document with a CommandButton added via Aspose.Words
  ActiveX tutorial
og_title: دليل Aspose.Words ActiveX – دليل خطوة بخطوة للـ Java
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  headline: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  type: TechArticle
- description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  name: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  steps:
  - name: Initialize a `Document` and `DocumentBuilder`.
    text: Initialize a `Document` and `DocumentBuilder`.
  - name: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
    text: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
  - name: Set the button’s name, caption, size, and position.
    text: Set the button’s name, caption, size, and position.
  - name: Save the document as a .docx file that contains the ActiveX control.
    text: Save the document as a .docx file that contains the ActiveX control.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
title: دليل Aspose.Words ActiveX – إدراج زر CommandButton باستخدام Java
url: /ar/java/images-shapes/aspose-words-activex-tutorial-insert-a-commandbutton-with-ja/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ActiveX tutorial – إدراج زر CommandButton باستخدام Java

إذا كنت بحاجة إلى تضمين عنصر تحكم ActiveX في ملف Word، فإن **دروس Aspose.Words ActiveX** هذه ستقودك خلال العملية بالكامل. سترى كيفية إنشاء مستند فارغ، وإدراج زر CommandButton، وتعيين خصائصه، وحفظ النتيجة—كل ذلك باستخدام كود Java بسيط.

يستخدم المثال Aspose.Words for Java API، مما يلغي الحاجة إلى Microsoft Office على خادم البناء. بنهاية هذا الدليل يمكنك إنشاء ملفات .docx تحتوي على عناصر تحكم CommandButton تعمل بالكامل وجاهزة للاستخدام في بيئات Windows.

## المتطلبات المسبقة

- مجموعة تطوير Java (JDK) 8 أو أحدث مثبتة.
- Maven أو أداة بناء أخرى لإدارة التبعيات.
- رخصة Aspose.Words for Java (أو مفتاح تقييم مؤقت) لتجنب علامات التقييم المائية.
- إلمام أساسي بصياغة Java والبرمجة الكائنية.

> **نصيحة احترافية:** أضف تبعية Aspose.Words Maven إلى ملف `pom.xml` الخاص بك لتسمح للـ IDE بحل الفئات تلقائيًا:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version -->
</dependency>
```

## الخطوة 1: إنشاء مستند فارغ جديد و`DocumentBuilder`

`Document` تمثل ملف Word في الذاكرة، بينما `DocumentBuilder` توفر API سلسة لتحرير المستند. تهيئة كلا الكائنين تُعد المستند لتعديلات إضافية.

```java
import com.aspose.words.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty Word document
        Document document = new Document();

        // DocumentBuilder lets you add text, tables, and controls
        DocumentBuilder builder = new DocumentBuilder(document);
```

**لماذا هذا مهم:**  
`DocumentBuilder` يتتبع موضع المؤشر الحالي، لذا أي عملية إدراج لاحقة—مثل إضافة عنصر تحكم—تظهر بالضبط حيث تريد.

## الخطوة 2: إدراج عنصر تحكم ActiveX من نوع CommandButton

Aspose.Words يتيح `Forms2OleControl` لكائنات ActiveX. طريقة `insertForms2OleControl` تتطلب نوع العنصر، الذي تحدده عبر تعداد `Forms2OleControlType`.

```java
        // Insert a CommandButton ActiveX control at the current cursor location
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**شرح:**  
العنصر المُدرج هو كائن قائم على COM سيقوم Word بعرضه كزر قابل للنقر عندما يُفتح المستند في بيئة Windows.

## الخطوة 3: ضبط خصائص الزر

بعد الإدراج، يمكنك تعديل اسم الزر، التسمية، الحجم، والموضع. هذه الخصائص تؤثر على مظهر العنصر وسلوكه داخل Word.

```java
        // Set the logical name used by VBA or external scripts
        commandButton.setName("cmdSubmit");

        // Text displayed on the button face
        commandButton.setCaption("Submit");

        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);
        commandButton.setTop(150);

        // Define the button’s dimensions (width × height) in points
        commandButton.setWidth(80);
        commandButton.setHeight(30);
```

**لماذا هذه الإعدادات مهمة:**  

- **Name** – يتيح ماكرو VBA الإشارة إلى العنصر (`ActiveDocument.Forms("cmdSubmit")`).
- **Caption** – يحدد التسمية المرئية التي ينقر عليها المستخدمون.
- **Left / Top** – يتحكم في الموضع بالنسبة لهوامش الصفحة.
- **Width / Height** – يضمن حجمًا بصريًا ثابتًا عبر مختلف دقات الشاشات.

## الخطوة 4: حفظ المستند

استدعاء `save` يكتب التمثيل الموجود في الذاكرة إلى ملف فعلي. يمكنك اختيار أي تنسيق مدعوم (`.docx`, `.doc`, `.pdf`, إلخ). في هذا الدليل نحتفظ بالتنسيق الأصلي لـ Word.

```java
        // Persist the document with the embedded ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

**النتيجة:**  
فتح `ActiveXDemo.docx` في Microsoft Word يعرض زر CommandButton مُسمى **Submit** موضعًا عند الإحداثيات المحددة. النقر على الزر يُفعل السلوك الافتراضي (لا يوجد كود VBA مرفق بشكل افتراضي).

## الكود المصدر الكامل

بجمع الأجزاء معًا، البرنامج الكامل القابل للتنفيذ يبدو هكذا:

```java
import com.aspose.words.*;
import com.aspose.words.forms.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button's properties
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // Step 4: Save the document with the ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

### النتيجة المتوقعة

- ملف باسم **ActiveXDemo.docx** موجود في مجلد `output`.
- عند فتحه في Microsoft Word (Windows)، يعرض المستند زرًا قابلًا للنقر **Submit** في الموضع المحدد.
- يمكن اختيار الزر، تحريكه، أو ربطه بكود VBA عبر واجهة Word (Developer → Properties).

## التعامل مع التغييرات الشائعة

| السيناريو | التعديل |
|----------|------------|
| **حفظ كـ .doc** (تنسيق قديم) | `document.save("ActiveXDemo.doc", SaveFormat.DOC);` |
| **إضافة معالج حدث** | لا يُظهر Word أحداث ActiveX عبر Aspose.Words. يجب إضافة كود VBA يدويًا بعد إنشاء المستند. |
| **عناصر تحكم متعددة** | كرّر كتلة الإدراج/الضبط مع قيم `setName` و `setCaption` مختلفة. |
| **نوع عنصر تحكم مختلف (مثال: CheckBox)** | استخدم `Forms2OleControlType.CHECKBOX` في استدعاء `insertForms2OleControl`. |
| **منصات غير Windows** | عناصر تحكم ActiveX تُعرض فقط في Word على Windows. للحلول متعددة المنصات، فكر في عناصر التحكم بالمحتوى (`StructuredDocumentTag`). |

## أفضل الممارسات والمخاطر المحتملة

- **License early** – سجّل رخصة Aspose.Words الخاصة بك قبل إنشاء `Document` لتجنب رسائل التقييم.
- **Coordinate system** – تُقاس المواضع بالنقاط (1 pt = 1/72 in). حوّل من البكسل أو السنتيمتر إذا كان تصميم واجهة المستخدم يستخدم تلك الوحدات.
- **File paths** – استخدم مسارات مطلقة أو API `Paths` في Java لتجنب `FileNotFoundException` عندما لا يكون دليل الإخراج موجودًا.
- **Thread safety** – `Document` و`DocumentBuilder` غير آمانين في بيئات متعددة الخيوط. أنشئ نسخًا منفصلة لكل خيط إذا كنت تولد المستندات بشكل متوازي.
- **Testing** – تحقق من المستند المُولد على نسخة Word المستهدفة (مثال: Word 2016, Word 365) لأن الإصدارات القديمة قد تعرض عناصر تحكم ActiveX بشكل مختلف.

## الخلاصة

هذه **دروس Aspose.Words ActiveX** تُظهر كيفية إضافة عنصر تحكم CommandButton برمجيًا إلى مستند Word باستخدام Java. تعلمت كيفية:

1. تهيئة `Document` و`DocumentBuilder`.
2. إدراج `Forms2OleControl` من النوع `COMMAND_BUTTON`.
3. ضبط اسم الزر، التسمية، الحجم، والموضع.
4. حفظ المستند كملف .docx يحتوي على عنصر التحكم ActiveX.

من هنا يمكنك استكشاف أنواع عناصر تحكم إضافية، أتمتة حقن ماكرو VBA، أو دمج عناصر تحكم ActiveX مع ميزات أخرى في Aspose.Words مثل الدمج البريدي وعناصر التحكم بالمحتوى. جرّب تخطيطات مختلفة ودمج المستندات المُولدة في خط أنابيب التقارير الأكبر القائم على Java.

---

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [استخدام كائنات OLE وعناصر تحكم ActiveX في Aspose.Words for Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [كيفية إنشاء حقول نموذج وإضافة محتوى باستخدام DocumentBuilder في Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [تحويل Word إلى RTF مع دليل Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-rtf-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}