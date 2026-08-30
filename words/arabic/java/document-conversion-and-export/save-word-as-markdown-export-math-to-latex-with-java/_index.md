---
category: general
date: 2026-05-26
description: احفظ مستند Word كملف markdown واكتشف كيفية تصدير المعادلات الرياضية إلى
  LaTeX باستخدام Aspose.Words للغة Java. حوّل معادلات Word إلى LaTeX في بضع أسطر فقط.
draft: false
keywords:
- save word as markdown
- how to export math
- convert word equations latex
- docx to markdown latex
language: ar
og_description: احفظ مستند Word كملف Markdown وتعلم كيفية تصدير المعادلات الرياضية
  إلى LaTeX باستخدام Aspose.Words للغة Java. دليل كامل وقابل للتنفيذ.
og_title: احفظ Word كـ Markdown – تصدير الرياضيات إلى LaTeX باستخدام Java
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Save word as markdown and discover how to export math equations to
    LaTeX using Aspose.Words for Java. Convert Word equations LaTeX in just a few
    lines.
  headline: Save word as markdown – Export Math to LaTeX with Java
  type: TechArticle
- description: Save word as markdown and discover how to export math equations to
    LaTeX using Aspose.Words for Java. Convert Word equations LaTeX in just a few
    lines.
  name: Save word as markdown – Export Math to LaTeX with Java
  steps:
  - name: Maven
    text: '```xml <dependency> <groupId>com.aspose</groupId> <artifactId>aspose-words</artifactId>
      <version>24.9</version> <!-- Check for the latest version --> </dependency>
      ```'
  - name: Gradle
    text: '```gradle implementation ''com.aspose:aspose-words:24.9'' ```'
  - name: Why this works
    text: '- **`Document`** is Aspose’s entry point; it abstracts the `.docx` file
      and gives you access to every node, including equations. - **`MarkdownSaveOptions`**
      tells the library *how* you want the output. The default behavior is to render
      equations as images, which defeats the purpose of a text‑based f'
  type: HowTo
tags:
- Aspose.Words
- Java
- Markdown
- LaTeX
- Office Math
title: حفظ Word كـ markdown – تصدير الرياضيات إلى LaTeX باستخدام Java
url: /ar/java/document-conversion-and-export/save-word-as-markdown-export-math-to-latex-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ Word كـ Markdown – تصدير الرياضيات إلى LaTeX باستخدام Java

هل احتجت يوماً إلى **حفظ Word كـ Markdown** لكنك كنت قلقاً من أن تتحول معادلاتك إلى فوضى غير مفهومة؟ لست وحدك. في هذا الدليل سنستعرض **كيفية تصدير الرياضيات** من ملف `.docx` مباشرة إلى LaTeX بينما يصبح باقي المستند Markdown نظيفاً.

سنتناول كل شيء من إعداد مكتبة Aspose.Words إلى التحقق من ملف `out.md` النهائي. في النهاية ستتمكن من **تحويل معادلات Word إلى LaTeX** باستدعاء طريقة واحدة، وستفهم التفاصيل الصغيرة التي تجعل التحويل موثوقاً.

---

## ما ستحتاجه

- **Java 8+** – الكود يعمل على أي JDK حديث.  
- **Aspose.Words for Java** – إما الاعتماد عبر Maven/Gradle أو ملف JAR إذا كنت تفضّل الإعداد اليدوي.  
- مستند Word (`math.docx`) يحتوي على معادلة Office Math واحدة على الأقل.  
- بيئة تطوير متكاملة (IDE) أو سطر أوامر بسيط `javac`/`java` – حسب ما تفضله.

إذا كان لديك هذه بالفعل، فهذا رائع. إذا لا، القسم التالي يوضح بالضبط كيفية إضافة المكتبة إلى مشروعك.

---

## حفظ Word كـ Markdown – الخطوة 1: إضافة Aspose.Words إلى مشروعك

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Check for the latest version -->
</dependency>
```

### Gradle

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **نصيحة احترافية:** Aspose تقدم رخصة مؤقتة مجانية للاختبار. ضع ملف `license.xml` في مجلد الموارد الخاص بك واستدعِ `License license = new License(); license.setLicense("license.xml");` قبل تحميل أي مستند.

بعد حل الاعتماد، ستكون جاهزاً لكتابة كود التحويل.

---

## كيفية تصدير معادلات الرياضيات إلى LaTeX

العمل الشاق يتم بواسطة `MarkdownSaveOptions`. عند تغيير `OfficeMathExportMode` إلى `LATEX`، يتم تحويل كل كائن Office Math إلى جزء LaTeX داخل ناتج الـ Markdown.

```java
import com.aspose.words.*;

public class MathToLatexMarkdown {
    public static void main(String[] args) throws Exception {
        // Load the Word document containing Office Math equations
        Document doc = new Document("YOUR_DIRECTORY/math.docx");

        // Create Markdown save options
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();

        // Configure the options to export Office Math as LaTeX
        saveOptions.setOfficeMathExportMode(
            MarkdownSaveOptions.OfficeMathExportMode.LATEX);

        // Save the document as a Markdown file with LaTeX equations
        doc.save("YOUR_DIRECTORY/out.md", saveOptions);
    }
}
```

### لماذا يعمل هذا

- **`Document`** هو نقطة الدخول في Aspose؛ فهو يُجَسِّد ملف `.docx` ويمنحك الوصول إلى كل عقدة، بما في ذلك المعادلات.  
- **`MarkdownSaveOptions`** يخبر المكتبة *كيف* تريد النتيجة. السلوك الافتراضي هو تحويل المعادلات إلى صور، مما يتعارض مع هدف التنسيق النصي.  
- **`OfficeMathExportMode.LATEX`** يجبر المحرك على تحويل كل عقدة `OfficeMath` إلى ما يعادلها في LaTeX، مما يتيح لمحللات Markdown (مثل GitHub أو Jekyll) عرضها عند دمجها مع إضافة MathJax.

---

## تحويل معادلات Word إلى LaTeX – الخطوة 2: التحقق من ناتج الـ Markdown

بعد تشغيل البرنامج، افتح `out.md`. يجب أن ترى شيئاً مشابهاً لهذا:

```markdown
# Sample Document

This paragraph contains an inline equation $E = mc^2$ and a displayed equation:

$$
\int_{a}^{b} f(x)\,dx = F(b) - F(a)
$$

Regular text continues here.
```

> **ملاحظة:** يتم تغليف أجزاء LaTeX بـ `$…$` للرياضيات داخل السطر و `$$…$$` للرياضيات ككتل. هذه هي الصيغة القياسية التي يفهمها معظم مولّدات المواقع الثابتة عندما يكون MathJax مفعلاً.

إذا كنت تفضّل أن تبقى المعادلات داخل السطر فقط، يمكنك تعديل `MarkdownSaveOptions` أكثر:

```java
saveOptions.setExportMathAsText(true); // forces inline $…$ only
```

---

## تحويل Docx إلى Markdown LaTeX – الخطوة 3: الحالات الخاصة والمشكلات الشائعة

| الحالة | ما الذي يجب مراقبته | الحل |
|-----------|-------------------|-----|
| **معادلات متداخلة معقدة** | قد تُخرج Aspose أقواساً إضافية `{}` يتعامل معها بعض المحللات حرفياً. | قم بمعالجة الـ Markdown بعد الإنشاء باستخدام تعبير نمطي بسيط لتقليص `{{` → `{`. |
| **غياب MathJax على الموقع المستهدف** | تظهر المعادلات ككود LaTeX خام. | أضف `<script src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>` إلى قالب HTML الخاص بك. |
| **مستندات كبيرة** | ارتفاع استهلاك الذاكرة لأن المستند بالكامل يُحمَّل دفعة واحدة. | استخدم `LoadOptions.setLoadFormat(LoadFormat.DOCX)` وفكّر في معالجة الصفحات على دفعات إذا واجهت `OutOfMemoryError`. |
| **عدم تعيين الرخصة** | ستظهر لك تحذير وقد يكون الناتج مائيًا (مُعلَّم). | حمِّل الرخصة مبكراً في `main` كما هو موضح في نصيحة Maven أعلاه. |

---

## حفظ Word كـ Markdown – مثال عملي كامل

فيما يلي فئة مستقلة يمكنك نسخها ولصقها في أي مشروع Java. فقط استبدل `YOUR_DIRECTORY` بالمسار إلى ملفاتك.

```java
import com.aspose.words.*;

public class MathToLatexMarkdown {
    public static void main(String[] args) throws Exception {
        // Optional: Apply a temporary license if you have one
        // License license = new License();
        // license.setLicense("license.xml");

        // 1️⃣ Load the source .docx
        Document doc = new Document("YOUR_DIRECTORY/math.docx");

        // 2️⃣ Prepare Markdown options with LaTeX export
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
        saveOptions.setOfficeMathExportMode(
            MarkdownSaveOptions.OfficeMathExportMode.LATEX);

        // 3️⃣ Save as .md – this is the moment we **save word as markdown**
        doc.save("YOUR_DIRECTORY/out.md", saveOptions);

        System.out.println("Conversion complete! Check out.md for LaTeX equations.");
    }
}
```

شغِّل البرنامج (`java MathToLatexMarkdown`) وسترى رسالة في وحدة التحكم تؤكد النجاح. افتح `out.md` في أي محرر – يجب أن تكون المعادلات مقتطفات LaTeX نظيفة جاهزة للعرض.

---

## لقطة من الناتج المتوقع

![ناتج حفظ Word كـ Markdown مع معادلات LaTeX](https://example.com/images/markdown-latex-output.png "ناتج حفظ Word كـ Markdown مع معادلات LaTeX")

*تُظهر الصورة مقتطفاً من الـ Markdown المُولَّد حيث تُغلف المعادلة `\int_{a}^{b} f(x)\,dx` بـ `$$`.*

---

## الخلاصة

لقد أظهرنا للتو كيفية **حفظ Word كـ Markdown** مع الحفاظ على كل معادلة Office Math كـ LaTeX أصلي. الخطوة الأساسية كانت ضبط `MarkdownSaveOptions` باستخدام `OfficeMathExportMode.LATEX`، مما يحول خط أنابيب تحويل Word إلى Markdown التقليدي إلى أداة تحويل تدعم الرياضيات بالكامل.

الآن يمكنك:

1. كيفية تصدير الرياضيات من أي ملف `.docx` دون فقدان الدقة.  
2. تحويل معادلات Word إلى LaTeX لمولدات المواقع الثابتة أو الوثائق أو المدونات الأكاديمية.  
3. توسيع النهج لمعالجة دفعات متعددة من الملفات، دمجه مع خطوط أنابيب CI، أو حتى بناء خدمة ويب صغيرة.

إذا كنت فضوليًا بشأن الخطوة التالية، جرّب دمج هذا مع **docx to markdown latex** للمستندات التي تحتوي على الكثير من الصور، أو استكشف `HtmlSaveOptions` من Aspose للحصول على نسخة HTML جاهزة للويب. الاحتمالات لا حصر لها—جرّب، واختبر، ثم شارك نتائجك مع المجتمع.

هل لديك أسئلة أو معادلة صعبة لم تُعرض كما هو متوقع؟ اترك تعليقًا أدناه، وبرمجة سعيدة!

## دروس ذات صلة

- [كيفية تصدير LaTeX من Word: تحويل DOCX إلى Markdown وحفظه كـ PDF](/words/english/java/document-conversion-and-export/how-to-export-latex-from-word-convert-docx-to-markdown-save/)
- [تحويل docx إلى markdown – تصدير معادلات الرياضيات إلى LaTeX باستخدام Aspose.Words](/words/english/java/document-conversion-and-export/convert-docx-to-markdown-export-math-equations-to-latex-with/)
- [كيفية تحويل Word إلى PDF باستخدام Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}