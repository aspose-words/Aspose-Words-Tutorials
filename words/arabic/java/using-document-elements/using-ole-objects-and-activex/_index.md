---
"description": "تعلم استخدام كائنات OLE وعناصر تحكم ActiveX في Aspose.Words لجافا. أنشئ مستندات تفاعلية بسهولة. ابدأ الآن!"
"linktitle": "استخدام كائنات OLE وعناصر التحكم ActiveX"
"second_title": "واجهة برمجة تطبيقات معالجة مستندات Java Aspose.Words"
"title": "استخدام كائنات OLE وعناصر التحكم ActiveX في Aspose.Words لـ Java"
"url": "/ar/java/using-document-elements/using-ole-objects-and-activex/"
"weight": 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# استخدام كائنات OLE وعناصر التحكم ActiveX في Aspose.Words لـ Java

في هذا البرنامج التعليمي، سنستكشف كيفية العمل مع كائنات OLE (ربط الكائنات وتضمينها) وعناصر تحكم ActiveX في Aspose.Words لجافا. تُعد كائنات OLE وعناصر تحكم ActiveX أدوات فعّالة تُمكّنك من تحسين مستنداتك من خلال تضمين أو ربط محتوى خارجي، مثل جداول البيانات، وملفات الوسائط المتعددة، أو عناصر التحكم التفاعلية. تابع معنا لنتعمق في أمثلة التعليمات البرمجية ونتعلم كيفية استخدام هذه الميزات بفعالية.

### المتطلبات الأساسية

قبل أن نبدأ، تأكد من توفر المتطلبات الأساسية التالية:

1. Aspose.Words لجافا: تأكد من تثبيت مكتبة Aspose.Words في مشروع جافا. يمكنك تنزيلها من [هنا](https://releases.aspose.com/words/java/).

2. بيئة تطوير Java: يجب أن يكون لديك بيئة تطوير Java عاملة تم إعدادها على نظامك.

### إدراج كائن OLE

لنبدأ بإدراج كائن OLE في مستند Word. سننشئ مستند Word بسيطًا، ثم نضيف كائن OLE يمثل صفحة ويب.

```java
string outPath = "Your Output Directory";
public void insertOleObject() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObject("http://www.aspose.com"، "htmlfile"، صحيح، صحيح، لا شيء)؛
    doc.save("Your Directory Path" + "WorkingWithOleObjectsAndActiveX.InsertOleObject.docx");
}
```

في هذا الكود، ننشئ مستندًا جديدًا ونُدرج كائن OLE لعرض موقع Aspose. يمكنك استبدال عنوان URL بالمحتوى المطلوب.

### إدراج كائن OLE باستخدام OlePackage

بعد ذلك، لنستكشف كيفية إدراج كائن OLE باستخدام OlePackage. يتيح لك هذا تضمين ملفات خارجية ككائنات OLE في مستندك.

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

لنرى الآن كيفية إدراج كائن OLE كأيقونة. هذا مفيد عند عرض أيقونة تمثل ملفًا مُضمّنًا.

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

الآن، لننتقل إلى عناصر تحكم ActiveX. سنتعلم كيفية قراءة خصائص عناصر تحكم ActiveX في مستند Word.

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

تهانينا! لقد تعلمت كيفية العمل مع كائنات OLE وعناصر تحكم ActiveX في Aspose.Words لجافا. هذه الميزات تفتح آفاقًا واسعة لإنشاء مستندات ديناميكية وتفاعلية.

### الأسئلة الشائعة

### ما هو الغرض من كائنات OLE في مستند Word؟ 
   - تتيح لك كائنات OLE تضمين محتوى خارجي أو ربطه، مثل الملفات أو صفحات الويب، داخل مستند Word.

### هل يمكنني تخصيص مظهر كائنات OLE في مستندي؟ 
   - نعم، يمكنك تخصيص مظهر كائنات OLE، بما في ذلك تعيين الرموز وأسماء الملفات.

### ما هي عناصر التحكم ActiveX، وكيف يمكنها تحسين مستنداتي؟ 
   - عناصر التحكم ActiveX عبارة عن عناصر تفاعلية يمكنها إضافة وظائف إلى مستندات Word الخاصة بك، مثل عناصر التحكم في النماذج أو مشغلات الوسائط المتعددة.

### هل Aspose.Words for Java مناسب لأتمتة المستندات على مستوى المؤسسة؟ 
   - نعم، Aspose.Words for Java هي مكتبة قوية لأتمتة إنشاء المستندات ومعالجتها في تطبيقات Java.

### أين يمكنني الحصول على إمكانية الوصول إلى Aspose.Words لـ Java؟ 
   - يمكنك تنزيل Aspose.Words for Java من [هنا](https://releases.aspose.com/words/java/).

ابدأ باستخدام Aspose.Words for Java اليوم واكتشف الإمكانات الكاملة لأتمتة المستندات وتخصيصها!



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}