---
title: استخدام كائنات OLE وعناصر التحكم ActiveX في Aspose.Words للغة Java
linktitle: استخدام كائنات OLE وعناصر التحكم ActiveX
second_title: واجهة برمجة تطبيقات معالجة المستندات في Java Aspose.Words
description: تعلم كيفية استخدام كائنات OLE وعناصر التحكم ActiveX في Aspose.Words for Java. أنشئ مستندات تفاعلية بسهولة. ابدأ الآن!
weight: 21
url: /ar/java/using-document-elements/using-ole-objects-and-activex/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# استخدام كائنات OLE وعناصر التحكم ActiveX في Aspose.Words للغة Java

في هذا البرنامج التعليمي، سنستكشف كيفية العمل مع كائنات OLE (ربط الكائنات وتضمينها) وعناصر التحكم ActiveX في Aspose.Words for Java. تعد كائنات OLE وعناصر التحكم ActiveX أدوات قوية تتيح لك تحسين مستنداتك عن طريق تضمين أو ربط محتوى خارجي، مثل جداول البيانات أو ملفات الوسائط المتعددة أو عناصر التحكم التفاعلية. تابع معنا بينما نتعمق في أمثلة التعليمات البرمجية ونتعلم كيفية استخدام هذه الميزات بشكل فعال.

### المتطلبات الأساسية

قبل أن نبدأ، تأكد من توفر المتطلبات الأساسية التالية:

1.  Aspose.Words for Java : تأكد من تثبيت مكتبة Aspose.Words في مشروع Java الخاص بك. يمكنك تنزيلها من[هنا](https://releases.aspose.com/words/java/).

2. بيئة تطوير Java: يجب أن يكون لديك بيئة تطوير Java عاملة تم إعدادها على نظامك.

### إدراج كائن OLE

لنبدأ بإدراج كائن OLE في مستند Word. سنقوم بإنشاء مستند Word بسيط ثم إدراج كائن OLE يمثل صفحة ويب.

```java
string outPath = "Your Output Directory";
public void insertOleObject() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObject("http://www.aspose.com، "htmlfile"، صحيح، صحيح، لا شيء)؛
    doc.save("Your Directory Path" + "WorkingWithOleObjectsAndActiveX.InsertOleObject.docx");
}
```

في هذا الكود نقوم بإنشاء مستند جديد وإدراج كائن OLE يعرض موقع Aspose ويمكنك استبدال عنوان URL بالمحتوى المطلوب.

### إدراج كائن OLE باستخدام OlePackage

بعد ذلك، دعنا نستكشف كيفية إدراج كائن OLE باستخدام OlePackage. يتيح لك هذا تضمين ملفات خارجية ككائنات OLE في مستندك.

```java
@Test
public void insertOleObjectWithOlePackage() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    byte[] bs = FileUtils.readFileToByteArray(new File("Your Directory Path" + "Zip file.zip"));
    try (ByteArrayInputStream stream = new ByteArrayInputStream(bs))
    {
        Shape shape = builder.insertOleObject(stream, "Package", true, null);
        OlePackage olePackage = shape.getOleFormat().getOlePackage();
        olePackage.setFileName("filename.zip");
        olePackage.setDisplayName("displayname.zip");
        doc.save(outPath + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
    }
}
```

في هذا المثال، نقوم بإدراج كائن OLE باستخدام OlePackage، مما يسمح لك بتضمين ملفات خارجية ككائنات مضمنة.

### إدراج كائن OLE كأيقونة

الآن، دعنا نرى كيفية إدراج كائن OLE كأيقونة. يعد هذا مفيدًا عندما تريد عرض أيقونة تمثل ملفًا مضمنًا.

```java
@Test
public void insertOleObjectAsIcon() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObjectAsIcon("Your Directory Path" + "Presentation.pptx", false, getImagesDir() + "Logo icon.ico", "My embedded file");
    doc.save(outPath + "WorkingWithOleObjectsAndActiveX.InsertOleObjectAsIcon.docx");
}
```

في هذا الكود، نقوم بإدراج كائن OLE كأيقونة، مما يوفر تمثيلًا أكثر جاذبية من الناحية البصرية للمحتوى المضمن.

### قراءة خصائص عنصر التحكم ActiveX

الآن، دعنا ننتقل إلى التركيز على عناصر تحكم ActiveX. سنتعلم كيفية قراءة خصائص عناصر تحكم ActiveX داخل مستند Word.

```java
@Test
public void readActiveXControlProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "ActiveX controls.docx");
    String properties = "";
    for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true))
    {
        if (shape.getOleFormat() == null) break;
        OleControl oleControl = shape.getOleFormat().getOleControl();
        if (oleControl.isForms2OleControl())
        {
            Forms2OleControl checkBox = (Forms2OleControl) oleControl;
            properties = properties + "\nCaption: " + checkBox.getCaption();
            properties = properties + "\nValue: " + checkBox.getValue();
            properties = properties + "\nEnabled: " + checkBox.getEnabled();
            properties = properties + "\nType: " + checkBox.getType();
            if (checkBox.getChildNodes() != null)
            {
                properties = properties + "\nChildNodes: " + checkBox.getChildNodes();
            }
            properties += "\n";
        }
    }
    properties = properties + "\nTotal ActiveX Controls found: " + doc.getChildNodes(NodeType.SHAPE, true).getCount();
    System.out.println("\n" + properties);
}
```

في هذا الكود، نقوم بالتكرار عبر الأشكال في مستند Word، وتحديد عناصر التحكم ActiveX، واسترجاع خصائصها.

### خاتمة

تهانينا! لقد تعلمت كيفية العمل مع كائنات OLE وعناصر التحكم ActiveX في Aspose.Words for Java. تفتح هذه الميزات عالمًا من الاحتمالات لإنشاء مستندات ديناميكية وتفاعلية.

### الأسئلة الشائعة

### ما هو الغرض من كائنات OLE في مستند Word؟ 
   - تتيح لك كائنات OLE تضمين محتوى خارجي أو ربطه، مثل الملفات أو صفحات الويب، داخل مستند Word.

### هل يمكنني تخصيص مظهر كائنات OLE في مستندي؟ 
   - نعم، يمكنك تخصيص مظهر كائنات OLE، بما في ذلك تعيين الأيقونات وأسماء الملفات.

### ما هي عناصر التحكم ActiveX، وكيف يمكنها تحسين مستنداتي؟ 
   - عناصر التحكم ActiveX عبارة عن عناصر تفاعلية يمكنها إضافة وظائف إلى مستندات Word، مثل عناصر التحكم في النماذج أو مشغلات الوسائط المتعددة.

### هل Aspose.Words for Java مناسب لأتمتة المستندات على مستوى المؤسسة؟ 
   - نعم، Aspose.Words for Java هي مكتبة قوية لأتمتة إنشاء المستندات ومعالجتها في تطبيقات Java.

### أين يمكنني الحصول على إمكانية الوصول إلى Aspose.Words لـ Java؟ 
   -  يمكنك تنزيل Aspose.Words for Java من[هنا](https://releases.aspose.com/words/java/).

ابدأ باستخدام Aspose.Words for Java اليوم واكتشف الإمكانات الكاملة لأتمتة المستندات وتخصيصها!

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
