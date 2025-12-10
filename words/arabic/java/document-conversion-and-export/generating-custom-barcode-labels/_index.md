---
date: 2025-12-10
description: تعلم كيفية إنشاء ملصقات باركود مخصصة باستخدام Aspose.Words للغة Java.
  يوضح لك هذا الدليل خطوة بخطوة كيفية تضمين الباركود في مستندات Word.
linktitle: Generating Custom Barcode Labels
second_title: Aspose.Words Java Document Processing API
title: إنشاء ملصقات باركود مخصصة في Aspose.Words لجافا
url: /ar/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء ملصقات باركود مخصصة في Aspose.Words للـ Java

## مقدمة حول إنشاء باركود مخصص في Aspose.Words للـ Java

الباركودات أساسية في التطبيقات الحديثة — سواء كنت تدير المخزون، أو تطبع تذاكر، أو تنشئ بطاقات هوية. في هذا الدرس ستقوم **بإنشاء ملصقات باركود مخصصة** وتضمينها مباشرةً في مستند Word باستخدام واجهة `IBarcodeGenerator`. سنستعرض كل خطوة، من إعداد البيئة إلى إدراج صورة الباركود، لتتمكن من استخدام الباركود في مشاريع الخاصة بك فورًا.

## إجابات سريعة
- **ماذا يعلّمك هذا الدرس؟** كيفية إنشاء ملصقات باركود مخصصة وتضمينها في ملف Word باستخدام Aspose.Words للـ Java.  
- **ما نوع الباركود المستخدم في المثال؟** رمز QR (يمكن استبداله بأي نوع مدعوم).  
- **هل أحتاج إلى ترخيص؟** يلزم الحصول على ترخيص مؤقت للوصول غير المحدود أثناء التطوير.  
- **ما نسخة Java المطلوبة؟** JDK 8 أو أعلى.  
- **هل يمكنني تغيير حجم الباركود أو ألوانه؟** نعم — عدّل إعدادات `BarcodeParameters` و `BarcodeGenerator`.

## المتطلبات المسبقة

قبل البدء بالبرمجة، تأكد من توفر ما يلي:

- مجموعة تطوير Java (JDK): الإصدار 8 أو أعلى.  
- مكتبة Aspose.Words للـ Java: [Download here](https://releases.aspose.com/words/java/).  
- مكتبة Aspose.BarCode للـ Java: [Download here](https://releases.aspose.com/).  
- بيئة تطوير متكاملة (IDE): IntelliJ IDEA، Eclipse، أو أي IDE تفضله.  
- ترخيص مؤقت: احصل على [temporary license](https://purchase.aspose.com/temporary-license/) للوصول غير المحدود.

## استيراد الحزم

سنستخدم مكتبات Aspose.Words و Aspose.BarCode. استورد الحزم التالية في مشروعك:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

تمنحنا هذه الاستيرادات إمكانية الوصول إلى واجهة برمجة تطبيقات إنشاء الباركود وفئات مستندات Word التي سنحتاجها.

## الخطوة 1: إنشاء فئة مساعدة لعمليات الباركود

للحفاظ على نظافة الكود الرئيسي، سنجعل المساعدات العامة — مثل **تحويل twips إلى بكسل** و **تحويل اللون السداسي** — في فئة مساعدة.

### الكود

```java
class CustomBarcodeGeneratorUtils {
    public static double twipsToPixels(String heightInTwips, double defVal) {
        try {
            int lVal = Integer.parseInt(heightInTwips);
            return (lVal / 1440.0) * 96.0; // Assuming default DPI is 96
        } catch (Exception e) {
            return defVal;
        }
    }

    public static Color convertColor(String inputColor, Color defVal) {
        if (inputColor == null || inputColor.isEmpty()) return defVal;
        try {
            int color = Integer.parseInt(inputColor, 16);
            return new Color((color & 0xFF), ((color >> 8) & 0xFF), ((color >> 16) & 0xFF));
        } catch (Exception e) {
            return defVal;
        }
    }
}
```

**شرح**

- `twipsToPixels` – تقيس Word الأبعاد بوحدات **twips**؛ هذه الطريقة تحوّلها إلى بكسل الشاشة، وهو مفيد عندما تحتاج لتحديد حجم صورة الباركود بدقة.  
- `convertColor` – يحول سلسلة سداسية (مثال: `"FF0000"` للون الأحمر) إلى كائن `java.awt.Color`، مما يتيح لك **كيفية إدراج باركود** بألوان أمامية وخلفية مخصصة.

## الخطوة 2: تنفيذ مولّد الباركود المخصص

الآن سننفّذ واجهة `IBarcodeGenerator`. ستكون هذه الفئة مسؤولة عن **إنشاء صور qr code java**‑style يمكن لـ Aspose.Words تضمينها.

### الكود

```java
class CustomBarcodeGenerator implements IBarcodeGenerator {
    public BufferedImage getBarcodeImage(BarcodeParameters parameters) {
        try {
            BarcodeGenerator gen = new BarcodeGenerator(
                CustomBarcodeGeneratorUtils.getBarcodeEncodeType(parameters.getBarcodeType()),
                parameters.getBarcodeValue()
            );

            gen.getParameters().getBarcode().setBarColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getForegroundColor(), Color.BLACK)
            );
            gen.getParameters().setBackColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getBackgroundColor(), Color.WHITE)
            );

            return gen.generateBarCodeImage();
        } catch (Exception e) {
            return new BufferedImage(100, 100, BufferedImage.TYPE_INT_ARGB);
        }
    }

    public BufferedImage getOldBarcodeImage(BarcodeParameters parameters) {
        throw new UnsupportedOperationException();
    }
}
```

**شرح**

- `getBarcodeImage` ينشئ كائنًا من `BarcodeGenerator`، يطبّق الألوان الممررة عبر `BarcodeParameters`، ثم يُعيد صورة `BufferedImage`.  
- الطريقة تتعامل بأناقة مع الأخطاء عبر إرجاع صورة بديلة، مما يضمن عدم تعطل إنشاء مستند Word.

## الخطوة 3: إنشاء باركود **وتضمينه في Word**

مع وجود المولّد جاهزًا، يمكننا الآن إنتاج صورة باركود و**إدراجها في مستند Word**.

### الكود

```java
import com.aspose.words.*;

public class GenerateCustomBarcodeLabels {
    public static void main(String[] args) throws Exception {
        // Load or create a Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Set up custom barcode generator
        CustomBarcodeGenerator barcodeGenerator = new CustomBarcodeGenerator();
        BarcodeParameters barcodeParameters = new BarcodeParameters();
        barcodeParameters.setBarcodeType("QR");
        barcodeParameters.setBarcodeValue("https://example.com");
        barcodeParameters.setForegroundColor("000000");
        barcodeParameters.setBackgroundColor("FFFFFF");

        // Generate barcode image
        BufferedImage barcodeImage = barcodeGenerator.getBarcodeImage(barcodeParameters);

        // Insert barcode image into Word document
        builder.insertImage(barcodeImage, 200, 200);

        // Save the document
        doc.save("CustomBarcodeLabels.docx");

        System.out.println("Barcode labels generated successfully!");
    }
}
```

**شرح**

1. **تهيئة المستند** – ينشئ `Document` جديد (أو يمكنك تحميل قالب موجود).  
2. **معلمات الباركود** – تحدد نوع الباركود (`QR`)، والقيمة المراد ترميزها، وألوان الخلفية/الأمام.  
3. **إدراج الصورة** – `builder.insertImage` يضع الباركود المُولَّد بالحجم المطلوب (200 × 200 بكسل). هذا هو جوهر **كيفية إدراج باركود** في ملف Word.  
4. **الحفظ** – المستند النهائي `CustomBarcodeLabels.docx` يحتوي على الباركود المضمّن جاهزًا للطباعة أو التوزيع.

## لماذا نُنشئ ملصقات باركود مخصصة باستخدام Aspose.Words؟

- **تحكم كامل** في مظهر الباركود (النوع، الحجم، الألوان).  
- **تكامل سلس** — لا حاجة لملفات صورة وسيطة؛ يتم إنشاء الباركود في الذاكرة وإدراجه مباشرة.  
- **متعدد المنصات** — يعمل على أي نظام تشغيل يدعم Java، ما يجعله مثاليًا لإنشاء المستندات من جانب الخادم.  
- **قابل للتوسع** — يمكنك تكرار العملية عبر مصدر بيانات لإنشاء مئات الملصقات المخصَّصة في تشغيل واحد.

## المشكلات الشائعة & استكشاف الأخطاء

| العَرَض | السبب المحتمل | الحل |
|---------|--------------|-----|
| الباركود يظهر فارغًا | ألوان `BarcodeParameters` متطابقة (مثلاً، أسود على أسود) | تحقق من قيم `foregroundColor` و `backgroundColor`. |
| الصورة مشوّهة | أبعاد بكسل غير صحيحة تم تمريرها إلى `insertImage` | عدّل قيم العرض/الارتفاع أو استخدم تحويل `twipsToPixels` للحصول على حجم دقيق. |
| خطأ نوع باركود غير مدعوم | استخدام نوع غير معروف في `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` | تأكد من أن سلسلة نوع الباركود تطابق أحد `EncodeTypes` المدعومة (مثل `"QR"`، `"CODE128"`). |

## الأسئلة المتكررة

**س: هل يمكنني استخدام Aspose.Words للـ Java بدون ترخيص؟**  
ج: نعم، لكن سيواجهك بعض القيود. احصل على [temporary license](https://purchase.aspose.com/temporary-license/) للوظائف الكاملة.

**س: ما أنواع الباركود التي يمكنني إنشاؤها؟**  
ج: يدعم Aspose.BarCode QR، Code 128، EAN‑13، والعديد من الصيغ الأخرى. راجع [documentation](https://reference.aspose.com/words/java/) للقائمة الكاملة.

**س: كيف يمكنني تغيير حجم الباركود؟**  
ج: عدّل قيم العرض والارتفاع في `builder.insertImage`، أو استخدم `twipsToPixels` لتحويل وحدات قياس Word إلى بكسل.

**س: هل يمكنني استخدام خطوط مخصصة لنص الباركود؟**  
ج: نعم، يمكنك تخصيص خط النص عبر خاصية `CodeTextParameters` في `BarcodeGenerator`.

**س: أين يمكنني الحصول على مساعدة إذا واجهت مشاكل؟**  
ج: زر [support forum](https://forum.aspose.com/c/words/8/) للحصول على مساعدة من مجتمع Aspose والمهندسين.

## الخلاصة

باتباع الخطوات أعلاه، أصبحت الآن تعرف **كيفية إنشاء صور باركود مخصصة** و**تضمين الباركود في مستندات Word** باستخدام Aspose.Words للـ Java. هذه التقنية مرنة بما يكفي لبطاقات المخزون، تذاكر الفعاليات، أو أي سيناريو يتطلب وجود باركود ضمن مستند مُولَّد. جرّب أنواعًا مختلفة من الباركود وخيارات التنسيق لتتناسب مع احتياجات عملك الخاصة.

---

**آخر تحديث:** 2025-12-10  
**تم الاختبار مع:** Aspose.Words للـ Java 24.12، Aspose.BarCode للـ Java 24.12  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}