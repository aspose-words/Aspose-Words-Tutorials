---
category: general
date: 2026-02-15
description: تعلم كيفية الحصول على الخطوط المفقودة عند تحميل مستند Word في Java باستخدام
  Aspose.Words. يتضمن استدعاءات التحذير ومعالجة استبدال الخطوط.
draft: false
keywords:
- how to get missing fonts
- Aspose.Words missing font
- font substitution warning
- Java LoadOptions warning callback
- document processing Java
language: ar
og_description: كيفية الحصول على الخطوط المفقودة في جافا باستخدام Aspose.Words. اكتشف
  ردود التحذير، معالجة استبدال الخطوط، وأفضل الممارسات لمعالجة المستندات.
og_title: كيفية الحصول على الخطوط المفقودة في جافا – دليل Aspose.Words
tags:
- Aspose.Words
- Java
- Font Management
title: كيفية الحصول على الخطوط المفقودة في جافا – دليل Aspose.Words
url: /ar/java/document-loading-and-saving/how-to-get-missing-fonts-in-java-aspose-words-guide/
---

_X}} which are not code fences; they are placeholders. Keep them.

Make sure markdown formatting preserved.

Now produce final output with all translated content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيف تحصل على الخطوط المفقودة في جافا – دليل Aspose.Words

هل فتحت مستند Word في جافا ورأيت استبدالات خطوط غريبة وتساءلت **كيف تحصل على الخطوط المفقودة**؟ لست الأول الذي يواجه هذه المفاجأة. في العديد من تطبيقات المؤسسات، يمكن لتحذيرات الخطوط المفقودة أن تفسد الدقة البصرية للتقارير أو العقود أو المواد التسويقية.

الخبر السار؟ Aspose.Words يزودك بطريقة نظيفة لالتقاط تلك التحذيرات عبر رد نداء (callback)، بحيث يمكنك تسجيلها أو استبدالها أو حتى تنبيه المستخدمين قبل أن يتم عرض المستند. في هذا الدرس سنستعرض مثالًا كاملاً وقابلًا للتنفيذ يوضح **كيف تحصل على الخطوط المفقودة**، يشرح لماذا رد النداء مهم، ويغطي بعض الحيل في الحالات الخاصة التي قد تحتاجها في مشاريع العالم الحقيقي.

> **نصيحة احترافية:** إذا كنت تستخدم بالفعل Aspose.Words 22.12 أو أحدث، فإن الـ API المعروض أدناه يعمل مباشرةً دون أي إعداد إضافي.

![مخطط يوضح كيفية الحصول على الخطوط المفقودة باستخدام رد نداء التحذير في Aspose.Words](how-to-get-missing-fonts-diagram.png "how to get missing fonts diagram")

## ما يغطيه هذا الدرس

- إعداد **Java LoadOptions warning callback** لالتقاط تحذيرات استبدال الخطوط.  
- تصفية التحذيرات بحيث ترى فقط تلك المتعلقة بالخطوط المفقودة.  
- طباعة تقرير واضح وسهل القراءة يوضح أي الخطوط تم استبدالها وما تم استبداله به.  
- نصائح للتعامل مع المستندات الكبيرة، تخصيص مستوى التحذير، ودمج الحل في خط معالجة أكبر.

بنهاية هذا الدليل ستتمكن من الإجابة على سؤال “**كيف تحصل على الخطوط المفقودة**؟” باستخدام مقتطف شفرة جاهز للتنفيذ وفهم قوي للآليات الأساسية.

### المتطلبات المسبقة

- تثبيت Java 8 أو أحدث.  
- مكتبة Aspose.Words for Java (قم بتنزيلها من الموقع الرسمي أو أضفها عبر Maven/Gradle).  
- مستند Word يشير إلى خط غير مثبت على جهازك (مثال: `MissingFont.docx`).  

إذا كان أي من هذه غير متوفر لديك، احصل على المكتبة الآن—إضافتها إلى Maven بسيطة كالتالي:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version> <!-- replace with the latest version -->
</dependency>
```

## الخطوة 1: إعداد مجموعة لتخزين تحذيرات استبدال الخطوط

قبل تحميل المستند نحتاج إلى مكان لتخزين أي تحذيرات تصدرها Aspose.Words. `ArrayList<WarningInfo>` يعمل بشكل جيد لأنه يحافظ على الترتيب ويسمح لنا بالتكرار لاحقًا.

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

// Step 1: Create a list that will hold warning information.
List<WarningInfo> fontWarnings = new ArrayList<>();
```

*لماذا هذا مهم:* يمكن لرد النداء التحذيري أن يُطلق عشرات المرات لملف واحد—فكر في كل حرف مفقود، كل مشكلة صورة مدمجة، إلخ. بجمعها أولاً، تحافظ على سرعة مرحلة التحميل وتؤجل المعالجة إلى حلقة مُتحكم فيها.

## الخطوة 2: تكوين LoadOptions مع رد نداء تحذيري

Aspose.Words يتيح لك توصيل `IWarningCallback`. داخل رد النداء سنضيف كل `WarningInfo` إلى قائمتنا من الخطوة 1.

```java
// Step 2: Set up LoadOptions with a custom warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Capture every warning; we'll filter later.
        fontWarnings.add(info);
    }
});
```

*شرح:* يتم استدعاء طريقة `warning` **متزامنًا** أثناء تحميل المستند. من خلال دفع `WarningInfo` إلى `fontWarnings` ببساطة، نتجنب أي عمليات I/O ثقيلة (مثل التسجيل إلى ملف) قد تبطئ التحميل. هذا النمط—جمع ثم معالجة—هو الطريقة الموصى بها للتعامل مع دفعات كبيرة من التحذيرات.

## الخطوة 3: تحميل المستند باستخدام الخيارات المكوَّنة

الآن نقوم فعليًا بقراءة ملف Word. إذا كان المستند يحتوي على خطوط غير مثبتة، ستقوم Aspose.Words تلقائيًا باستبدالها وإطلاق رد النداء التحذيري الذي ربطناه للتو.

```java
// Step 3: Load the document with the warning‑aware LoadOptions.
String filePath = "YOUR_DIRECTORY/MissingFont.docx"; // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

*ماذا يحدث خلف الكواليس؟* تقوم Aspose.Words بتحليل جدول الخطوط في الملف، وتقارنها بالخطوط المتاحة على نظام التشغيل المضيف، ولكل إدخال مفقود تنشئ `WarningInfo` مع `WarningSource.FontSubstitution`. هذا المصدر هو المفتاح الذي سنستخدمه لعزل تحذيرات الخطوط المفقودة.

## الخطوة 4: تصفية وعرض تحذيرات استبدال الخطوط فقط

بعد التحميل، قد يحتوي `fontWarnings` على مزيج من الرسائل (مثل الميزات المهجورة، مشاكل الصور). نحن نهتم فقط بالخطوط المفقودة، لذا نمر عبر القائمة ونطبع تقريرًا مختصرًا.

```java
// Step 4: Output any font‑substitution warnings that were captured.
for (WarningInfo warning : fontWarnings) {
    if (warning.getSource() == WarningSource.FontSubstitution) {
        System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                           warning.getAdditionalInfo() + "'");
    }
}
```

**نموذج الإخراج**

```
Substituted 'Comic Sans MS' with 'Arial'
Substituted 'Times New Roman PS' with 'Times New Roman'
```

*لماذا هذا مفيد:* حقل `description` يخبرك بأي خط طلبه المستند، بينما `additionalInfo` يخبرك بما استخدمته Aspose.Words فعليًا. مسلحًا بهذه البيانات يمكنك:

- طلب من المستخدم تثبيت الخط المفقود.  
- تضمين خط بديل برمجيًا في المستند (`doc.getFontInfos().add(...)`).  
- تسجيل الحدث لتدقيق الامتثال.

## معالجة الحالات الخاصة والاختلافات الشائعة

### 1. قمع التحذيرات غير المتعلقة بالخطوط

إذا كنت تريد فقط الرسائل المتعلقة بالخطوط، يمكنك تضييق رد النداء:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        fontWarnings.add(info);
    }
});
```

هذا يقلل من استهلاك الذاكرة عند معالجة دفعات ضخمة.

### 2. تعديل شدة التحذير

Aspose.Words يصنف التحذيرات حسب `WarningType`. بالنسبة للخطوط المفقودة عادةً ما ترى `WarningType.FontSubstitution`. إذا احتجت إلى التعامل معها كأخطاء (مثلاً إلغاء التحميل)، ارمِ استثناءً داخل رد النداء:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        throw new RuntimeException("Missing font detected: " + info.getDescription());
    }
});
```

### 3. العمل مع التدفقات بدلاً من الملفات

أحيانًا تأتي المستندات من قاعدة بيانات أو طلب HTTP. نفس النهج يعمل مع `InputStream`:

```java
InputStream docStream = new ByteArrayInputStream(bytesFromDb);
Document doc = new Document(docStream, loadOptions);
```

فقط تذكر إغلاق التدفق بعد التحميل.

### 4. استخدام مجلد خطوط مخصص

إذا كان لديك مجموعة من خطوط الشركة المخزنة على محرك مشترك، وجه Aspose.Words إلى ذلك المجلد:

```java
loadOptions.setFontSettings(new FontSettings());
loadOptions.getFontSettings().setFontsFolder("C:/CorporateFonts", true);
```

الآن ستبحث المكتبة هناك *قبل* اللجوء إلى خطوط النظام، مما يقلل بشكل كبير عدد تحذيرات الخطوط المفقودة.

## مثال كامل يعمل

بجمع كل شيء معًا، إليك فئة مستقلة يمكنك وضعها في أي مشروع Java:

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

public class MissingFontDetector {

    public static void main(String[] args) {
        // 1️⃣ Prepare a collection for warnings.
        List<WarningInfo> fontWarnings = new ArrayList<>();

        // 2️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(info -> fontWarnings.add(info));

        // (Optional) Point to a custom font folder.
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.setFontsFolder("C:/CorporateFonts", true);
        // loadOptions.setFontSettings(fontSettings);

        // 3️⃣ Load the document.
        String docPath = "YOUR_DIRECTORY/MissingFont.docx";
        Document doc;
        try {
            doc = new Document(docPath, loadOptions);
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            return;
        }

        // 4️⃣ Print missing‑font warnings.
        System.out.println("=== Missing Font Report ===");
        for (WarningInfo warning : fontWarnings) {
            if (warning.getSource() == WarningSource.FontSubstitution) {
                System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                                   warning.getAdditionalInfo() + "'");
            }
        }
        System.out.println("=== End of Report ===");
    }
}
```

شغّل هذا البرنامج، وسترى قائمة مرتبة بكل خط اضطرّت Aspose.Words لاستبداله. لا مكتبات إضافية، لا سحر مخفي—فقط جافا صافية وقوة واجهة برمجة تطبيقات **Aspose.Words missing font**.

## الخلاصة

لقد أجبنا على السؤال الأساسي **كيف تحصل على الخطوط المفقودة** في بيئة Java باستخدام Aspose.Words. من خلال إرفاق رد نداء تحذيري `LoadOptions`، جمع كائنات `WarningInfo`، وتصفية مصادر `FontSubstitution`، تحصل على رؤية كاملة لمشكلات الخطوط قبل حدوث أي عرض. هذا النهج يتوسع من أدوات ملف واحد إلى معالجات دفعات ضخمة، وهو مرن بما يكفي لاستيعاب مجلدات خطوط مخصصة، معالجة الشدة، أو مدخلات قائمة على التدفق.

الخطوات التالية؟ حاول تضمين الخطوط المستبدلة مباشرةً في المستند (`doc.getFontInfos().add(...)`) بحيث يكون الملف النهائي مستقلًا تمامًا، أو دمج تقرير التحذير في لوحة مراقبة. يمكنك أيضًا استكشاف مواضيع ذات صلة مثل **document processing Java**، **Aspose.Words font substitution warning**، و **Java LoadOptions warning callback** لتعميق خبرتك.

برمجة سعيدة، ولتظهر مستنداتك دائمًا بالخطوط التي تتوقعها!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}