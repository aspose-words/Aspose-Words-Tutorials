---
category: general
date: 2026-11-22
description: إنشاء زر ماكرو في مستند Word باستخدام Java. تعلم كيفية إدراج زر أمر،
  تعيين نص الزر، وربط الماكرو بالزر لإنشاء مستندات تفاعلية.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create macro button
- insert command button
- set button text
- link macro to button
- add interactive button
language: ar
lastmod: 2026-11-22
og_description: إنشاء زر ماكرو في مستند Word باستخدام Java. يوضح هذا الدرس كيفية إدراج
  زر أمر، تعيين نص الزر، وربط الماكرو بالزر لتحقيق التفاعل الكامل.
og_image_alt: Screenshot of a Word document showing a macro button created with Java
  code
og_title: إنشاء زر ماكرو في مستند Word باستخدام Java – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  headline: How to create macro button in a Word document with Aspose.Words for Java
  type: TechArticle
- description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  name: How to create macro button in a Word document with Aspose.Words for Java
  steps:
  - name: Insert command button into the document
    text: '`DocumentBuilder.insertForms2OleControl` creates an OLE control of the
      specified type. The `Forms2OleControlType.COMMAND_BUTTON` constant tells Aspose.Words
      to generate a command button that can host a macro.'
  - name: Set button text (caption)
    text: The caption is the visible label on the button. Use `setCaption` to define
      what the user sees.
  - name: Link macro to button
    text: A macro is identified by its name, for example `MyMacro`. The `setOnClick`
      method stores this name in the button’s `OnClick` event handler.
  - name: Add interactive button to a Word document
    text: After configuring the OLE control, you may want to position it, resize it,
      or add surrounding text. The `DocumentBuilder` continues to operate on the document,
      so you can insert paragraphs before or after the button.
  - name: Expected output
    text: 'Running the program generates `MacroButtonDemo.docm`. Opening the file
      in Microsoft Word shows:'
  type: HowTo
tags:
- Aspose.Words
- Java
- OLE controls
- Automation
title: كيفية إنشاء زر ماكرو في مستند Word باستخدام Aspose.Words للـ Java
url: /ar/java/using-document-elements/how-to-create-macro-button-in-a-word-document-with-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء زر ماكرو في مستند Word باستخدام Aspose.Words للغة Java

إذا كنت بحاجة إلى **إنشاء زر ماكرو** في ملف Word، فإن هذا الدليل يوضح لك الخطوات الدقيقة المطلوبة. ستتعلم كيفية **إدراج زر أمر**، **تعيين نص الزر**، و**ربط الماكرو بالزر** بحيث يصبح المستند تفاعليًا بالكامل.

غالبًا ما يدمج المطورون عناصر تحكم OLE لتشغيل ماكرو VBA من داخل المستند. يغطي هذا البرنامج التعليمي سير العمل الكامل، من إعداد المشروع إلى مثال Java قابل للتنفيذ يضيف **زرًا تفاعليًا** إلى ملف .docx. لا تحتاج إلى أي سكريبتات خارجية—كل شيء يُنفّذ داخل عملية Java.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من توفر ما يلي:

* JDK 17 أو أحدث مثبت.
* Maven 3.8+ (أو Gradle) لإدارة الاعتمادات.
* Aspose.Words للغة Java 23.9 أو أحدث – المكتبة توفر `DocumentBuilder` وواجهات برمجة OLE control.
* إلمام أساسي بـ Java وماكرو VBA.

إذا كان أي من هذه العناصر مفقودًا، قم بتثبيته أولًا؛ سيفترض باقي الدليل توفرها.

## كيفية إنشاء زر ماكرو باستخدام Aspose.Words للغة Java

يتكون جوهر الحل من أربع عمليات:

1. **إدراج زر أمر** OLE داخل المستند.
2. **تعيين نص الزر** (التسمية) التي يراها المستخدم.
3. **ربط الماكرو بالزر** بحيث يتم تشغيل روتين VBA المطلوب عند النقر.
4. **حفظ المستند** مع الماكرو المدمج.

يتم شرح كل عملية في قسمها الخاص أدناه.

### الخطوة 1: إدراج زر أمر داخل المستند

`DocumentBuilder.insertForms2OleControl` ينشئ عنصر تحكم OLE من النوع المحدد. الثابت `Forms2OleControlType.COMMAND_BUTTON` يخبر Aspose.Words بإنشاء زر أمر يمكنه استضافة ماكرو.

```java
import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load a blank document or create a new one
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**لماذا هذا مهم:** عنصر تحكم OLE يعمل كحاوية للماكرو. بدون إدراجه، لا يوجد عنصر مرئي يمكن للمستخدم النقر عليه.

### الخطوة 2: تعيين نص الزر (التسمية)

التسمية هي النص الظاهر على الزر. استخدم `setCaption` لتحديد ما يراه المستخدم.

```java
        // Set the button's caption – this is the text displayed on the button
        commandButton.setCaption("Run Report");
```

**لماذا هذا مهم:** نص زر واضح يحسّن من قابلية الاستخدام. طريقة `setCaption` تُحدّث خاصية `Caption` لعنصر OLE، والتي يعرضها Word كتسمية للزر.

### الخطوة 3: ربط الماكرو بالزر

يُعرّف الماكرو باسمه، على سبيل المثال `MyMacro`. طريقة `setOnClick` تخزن هذا الاسم في معالج الحدث `OnClick` للزر.

```java
        // Assign a macro to run when the button is clicked
        commandButton.setOnClick("MyMacro");
```

**لماذا هذا مهم:** ربط الماكرو يخلق السلوك التفاعلي. عندما ينقر المستخدم الزر في Word، يتم تنفيذ روتين VBA المرتبط.

### الخطوة 4: إضافة زر تفاعلي إلى مستند Word

بعد تكوين عنصر تحكم OLE، قد ترغب في وضعه، تغيير حجمه، أو إضافة نص محيط. يظل `DocumentBuilder` يعمل على المستند، لذا يمكنك إدراج فقرات قبل أو بعد الزر.

```java
        // Add a descriptive paragraph before the button
        builder.moveToDocumentStart();
        builder.writeln("Click the button below to generate the report:");

        // Move the cursor back to the button location (optional)
        builder.moveTo(commandButton.getNode());

        // Optionally, resize the button (width and height in points)
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // Save the document with the macro-enabled format
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

**لماذا هذا مهم:** حفظ الملف كـ `.docm` يحافظ على كود الماكرو. إذا حفظته كـ `.docx`، سيُفقد مرجع الماكرو.

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل بلغة Java، بما في ذلك الاستيرادات، معالجة الاستثناءات، وتعليقات توضح كل خطوة. انسخ الكود إلى مشروع Maven يحتوي على اعتماد Aspose.Words وشغّله.

```java
// Maven dependency (add to pom.xml):
// <dependency>
//   <groupId>com.aspose</groupId>
//   <artifactId>aspose-words</artifactId>
//   <version>23.9</version>
// </dependency>

import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new empty document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Write an introductory paragraph
        builder.writeln("Press the button to execute the macro:");

        // 4. Insert the command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 5. Set the visual caption of the button
        commandButton.setCaption("Run Report");

        // 6. Link the button to a VBA macro named MyMacro
        commandButton.setOnClick("MyMacro");

        // 7. Resize the button for better appearance
        commandButton.setWidth(120);   // points
        commandButton.setHeight(30);   // points

        // 8. Save the document as a macro‑enabled file
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

### النتيجة المتوقعة

تشغيل البرنامج يولّد ملف `MacroButtonDemo.docm`. عند فتح الملف في Microsoft Word سيظهر:

* فقرة تقول *“Press the button to execute the macro:”*.
* زر يحمل التسمية **Run Report** مباشرةً أسفل الفقرة.
* عند النقر على الزر، يحاول Word تشغيل الماكرو `MyMacro`. (يجب إضافة كود VBA الفعلي إلى المستند يدويًا أو عبر خطوة أتمتة أخرى.)

إذا لم يكن الماكرو موجودًا، سيظهر تحذير أمان في Word، وهو سلوك قياسي للمستندات المفعّلة للماكرو.

## الاختلافات الشائعة والحالات الخاصة

| السيناريو | كيفية تعديل الكود |
|----------|-------------------|
| **تسمية زر مختلفة** | غيّر السلسلة الممررة إلى `setCaption`. |
| **أزرار متعددة** | استدعِ `insertForms2OleControl` عدة مرات، كل مرة مع `setCaption` و `setOnClick` الخاصين بها. |
| **أسماء ماكرو مخصصة** | استبدل `"MyMacro"` بأي اسم إجراء VBA صالح، مثل `"ExportToExcel"`. |
| **قيود حجم الزر** | عدّل قيم `setWidth` و `setHeight`؛ Word يطبق النقاط التي تحددها. |
| **إدراج الماكرو برمجيًا** | استخدم `Document.getBuiltInDocumentProperties().add("Macros", …)` أو خطوة حقن VBA منفصلة؛ Aspose.Words لا يكتب كود VBA بنفسه. |

**نصيحة احترافية:** اختبر دائمًا ملف `.docm` المُولّد على جهاز يكون أمان الماكرو فيه مضبوطًا على *Enable all macros* أثناء التطوير. في بيئة الإنتاج، وقع الماكرو بشهادة موثوقة لتجنب نوافذ التحذير.

## قائمة التحقق من استكشاف الأخطاء وإصلاحها

* **الزر لا يظهر** – تأكد من حفظ المستند كـ `.docm` وفتحه في نسخة Word تدعم عناصر تحكم OLE.
* **الماكرو لا يعمل** – تحقق من أن اسم الماكرو مطابق تمامًا، بما في ذلك حالة الأحرف، وأن الماكرو موجود في مشروع VBA الخاص بالمستند.
* **تقصير تسمية الزر** – زد عرض الزر باستخدام `setWidth` لاستيعاب النص الأطول.
* **تحول غير متوقع في التخطيط** – استخدم `builder.moveTo` لتحديد موضع المؤشر بدقة قبل إدراج العنصر.

## الخلاصة

أصبحت الآن تعرف كيف **تنشئ زر ماكرو** في مستند Word باستخدام Java، **تدرج زر أمر**، **تعيّن نص الزر**، وتربط **الماكرو بالزر** لتحقيق تفاعل كامل. يوضح المثال الكامل كل استدعاء API مطلوب، ويشرح لماذا كل خطوة مهمة، ويقدم إرشادات للتعديلات الشائعة.

الخطوات التالية قد تشمل:

* **إضافة زر تفاعلي** إلى قوالب موجودة بدلاً من مستند جديد.
* **حقن كود VBA برمجيًا** باستخدام Open XML SDK أو أداة أتمتة ثانية.
* **دمج عناصر تحكم OLE متعددة** (مربعات اختيار، قوائم) لإنشاء نماذج غنية.

جرّب تسميات مختلفة، أسماء ماكرو، وأحجام أزرار لتتناسب مع حالتك الخاصة. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [How to insert command button in a Word document using Java](/words/english/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/)
- [How to set button position in a Word document with Java](/words/english/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/)
- [How to Insert ActiveX Button in Word – Set Button Caption](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}