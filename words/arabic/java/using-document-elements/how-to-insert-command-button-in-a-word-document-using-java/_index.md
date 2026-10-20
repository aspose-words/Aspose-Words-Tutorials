---
category: general
date: 2026-08-23
description: تعلم كيفية إدراج زر أمر في مستند Word باستخدام Java و Aspose.Words. يوضح
  هذا الدليل كيفية إضافة عنصر تحكم نموذج، تعيين اسم الزر، وتضمين زر ActiveX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert command button
- add form control
- how to add button
- set button name
- add activex button
language: ar
lastmod: 2026-08-23
og_description: إدراج زر أمر في مستند Word باستخدام Java. اتبع هذا الدليل لإضافة عنصر
  تحكم نموذج، وتعيين اسم الزر، وتضمين زر ActiveX باستخدام Aspose.Words.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX command button
og_title: إدراج زر أمر في Word باستخدام Java – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  headline: How to insert command button in a Word document using Java
  type: TechArticle
- description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  name: How to insert command button in a Word document using Java
  steps:
  - name: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
    text: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
  - name: The **Submit** button appears where the cursor was positioned during insertion.
    text: The **Submit** button appears where the cursor was positioned during insertion.
  - name: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
    text: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: كيفية إدراج زر أمر في مستند Word باستخدام Java
url: /ar/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إدراج زر أمر في مستند Word باستخدام Java

إذا كنت بحاجة إلى **إدراج زر أمر** في ملف Word، فإن هذا الدليل يوضح لك حلاً كاملاً باستخدام Aspose.Words for Java. سترى كيفية إضافة عنصر تحكم نموذج، ضبط التسمية التوضيحية له، وتعيين اسم الزر دون مغادرة بيئة التطوير المتكاملة الخاصة بك.

يغطي الدليل كل ما تحتاجه لإنشاء ملف `.docx` يحتوي على زر ActiveX جاهز للاستخدام في Microsoft Word. لا يلزم أي أدوات إضافية، ويعمل المثال على Java 8+.

## ما ستتعلمه

* كيفية إضافة عنصر تحكم نموذج من النوع **CommandButton** إلى مستند Word.  
* الخطوات الدقيقة لـ **set button name** و **add activex button**.  
* كيفية حفظ المستند بحيث يظهر الزر بشكل صحيح عند فتحه في Word.  

يجب أن يكون لديك بيئة تطوير Java أساسية ومشروع Maven أو Gradle يمكنه استيراد مكتبة Aspose.Words.

## المتطلبات المسبقة

| المتطلب | السبب |
|-------------|--------|
| Java 8 أو أحدث | Aspose.Words for Java يعمل على Java 8+. |
| أداة بناء Maven أو Gradle | يبسط إضافة تبعية Aspose.Words. |
| رخصة Aspose.Words for Java (أو تجربة مجانية) | مطلوب للحصول على مجموعة الميزات الكاملة؛ API يعمل في وضع التقييم. |
| IDE مثل IntelliJ IDEA أو Eclipse | يسهل تحرير وتشغيل المثال. |

## الخطوة 1: إضافة Aspose.Words إلى مشروعك

إذا كنت تستخدم Maven، أضف التبعية التالية إلى `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest version -->
</dependency>
```

بالنسبة لـ Gradle، ضع هذا السطر في `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

بعد حل التبعية، يمكنك استيراد فئات المكتبة في ملف مصدر Java الخاص بك.

## الخطوة 2: إدراج زر أمر – الكود الأساسي

أنشئ فئة Java جديدة تسمى `InsertCommandButtonDemo`. الكود أدناه ينفذ جميع الإجراءات الأربعة المطلوبة لـ **insert command button**:

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Add form control – an ActiveX CommandButton – to the document
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 3️⃣ Set button name and displayed caption (this answers the "set button name" need)
        commandButton.setName("btnSubmit");
        commandButton.setCaption("Submit");

        // 4️⃣ Save the document with the embedded button
        doc.save("CommandButtonDemo.docx");
    }
}
```

### لماذا كل سطر مهم

* **Document & DocumentBuilder** – توفر تمثيلًا في الذاكرة لملف Word وواجهة API لتعديل محتوياته.  
* **insertForms2OleControl** – هذه الطريقة **adds form control** من النوع `COMMAND_BUTTON`. الكائن `Forms2OleControl` المرتجع يمثل عنصر التحكم ActiveX.  
* **setName** – يعيّن معرفًا برمجيًا (`btnSubmit`). يمكن للماكروهات في Word أو VBA الإشارة إلى هذا الاسم لاحقًا.  
* **setCaption** – يحدد النص الذي يراه المستخدم على الزر، مُجيبًا على سؤال “كيفية إضافة زر”.  
* **save** – يكتب ملف `.docx` إلى القرص، محافظًا على زر ActiveX المدمج.

تشغيل البرنامج ينشئ ملف `CommandButtonDemo.docx` في دليل العمل. فتح الملف في Microsoft Word يظهر زرًا مُعنونًا **Submit** يمكنك النقر عليه (سيعرض حوار ActiveX افتراضي في وضع التقييم).

## الخطوة 3: التحقق من الزر المُدرج في Word

1. افتح `CommandButtonDemo.docx` باستخدام Microsoft Word (2016 أو أحدث).  
2. يظهر زر **Submit** في المكان الذي كان المؤشر فيه أثناء الإدراج.  
3. انقر بزر الماوس الأيمن على الزر واختر **Properties** لتلاحظ أن حقل **Name** يحتوي على `btnSubmit`.  

إذا لم يظهر الزر، تأكد من تمكين **ActiveX controls** في إعدادات مركز الثقة (Trust Center) في Word.

## الخطوة 4: تخصيص الزر (اختياري)

يمكنك تخصيص الزر أكثر عن طريق تعديل حجمه أو موقعه أو إضافة ماكرو VBA. تُظهر فئة `Forms2OleControl` خصائص إضافية مثل `setWidth` و `setHeight` و `setLeft`. أدناه مثال يجعل الزر أكبر:

```java
commandButton.setWidth(100);   // Width in points
commandButton.setHeight(30);   // Height in points
commandButton.setLeft(50);     // Horizontal offset from the left margin
```

يمكن وضع هذه الأسطر بعد استدعاء `setCaption`. إنها توضح تخصيص **add activex button** بما يتجاوز الإدراج الأساسي.

## المشكلات الشائعة وكيفية تجنبها

| العَرَض | السبب | الحل |
|---------|-------|-----|
| الزر لا يظهر في Word | تم حفظ المستند قبل إضافة عنصر التحكم | تأكد من استدعاء `insertForms2OleControl` قبل `doc.save`. |
| تسمية الزر فارغة | `setCaption` لم تُستدعَ أو استُدعِت بسلسلة فارغة | قدّم سلسلة غير فارغة، مثل `"Submit"`. |
| VBA لا يمكنه العثور على الزر | عدم تطابق الاسم بين كود VBA وقيمة `setName` | احرص على أن يكون الاسم متسقًا؛ استخدم `setName("btnSubmit")` وأشر إلى `btnSubmit` في VBA. |
| تحذير أمان عند فتح الملف | أمان الماكرو في Word يمنع عناصر التحكم ActiveX | عدّل Trust Center > إعدادات الماكرو، أو وقع المستند بشهادة موثوقة. |

## مثال كامل قابل للتنفيذ

فيما يلي ملف المصدر الكامل، جاهز للنسخ واللصق في IDE الخاص بك. يتضمن عبارات الاستيراد، معالجة الاستثناءات، وكتلة تعليق تشرح كل خطوة رئيسية.

```java
// InsertCommandButtonDemo.java
// Demonstrates how to insert an ActiveX CommandButton into a Word document using Aspose.Words for Java.

import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Add a CommandButton form control (ActiveX) to the document.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button – set its programmatic name and visible caption.
        commandButton.setName("btnSubmit");   // This answers the "set button name" requirement.
        commandButton.setCaption("Submit");   // This is the text the user sees.

        // Optional: Resize and reposition the button (demonstrates add activex button customization).
        commandButton.setWidth(100);
        commandButton.setHeight(30);
        commandButton.setLeft(50);

        // Step 4: Save the document. The button is now embedded and will appear in Word.
        doc.save("CommandButtonDemo.docx");
    }
}
```

**النتيجة المتوقعة:** بعد تشغيل البرنامج، يحتوي `CommandButtonDemo.docx` على زر **Submit** واحد. فتح الملف في Word يظهر الزر بالضبط حيث كان مؤشر `DocumentBuilder` موجودًا.

## الخطوات التالية

* **Add more form controls** – استخدم `Forms2OleControlType.CHECK_BOX` و `RADIO_BUTTON` أو `TEXT_BOX` لبناء نماذج Word كاملة.  
* **Combine with mail merge** – أدخل الأزرار في مستند تم دمجه بالبريد لإنشاء نماذج تفاعلية مخصصة.  
* **Attach VBA macros** – أدمج VBA برمجيًا يتفاعل مع حدث `Click` للزر لأتمتة متقدمة.  

هذه المواضيع توسّع بشكل طبيعي تقنية **add form control** التي تعلمتها للتو.

---

### ملخص

أنت الآن تعرف كيف **insert command button** في مستند Word باستخدام Java، وكيف **add form control**، وكيف **set button name**، وكيف **add activex button** تخصيصات. المثال الكامل يعمل مباشرةً، ويمكنك تعديله ليناسب أي سير عمل لتوليد المستندات. ترميز سعيد!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إنشاء حقول نموذج وإضافة محتوى باستخدام DocumentBuilder في Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [إدراج حقل نموذج صندوق اختيار (Combo Box) في مستند Word](/words/english/net/working-with-form-fields/insert-form-fields/)
- [إدراج حقل نموذج مربع اختيار (Check Box) في مستند Word](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}