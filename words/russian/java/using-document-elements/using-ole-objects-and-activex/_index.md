---
title: Использование объектов OLE и элементов управления ActiveX в Aspose.Words для Java
linktitle: Использование объектов OLE и элементов управления ActiveX
second_title: API обработки документов Java Aspose.Words
description: Изучите использование объектов OLE и элементов управления ActiveX в Aspose.Words для Java. Создавайте интерактивные документы с легкостью. Начните прямо сейчас!
weight: 21
url: /ru/java/using-document-elements/using-ole-objects-and-activex/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Использование объектов OLE и элементов управления ActiveX в Aspose.Words для Java

В этом уроке мы рассмотрим, как работать с объектами OLE (Object Linking and Embedding) и элементами управления ActiveX в Aspose.Words для Java. Объекты OLE и элементы управления ActiveX — это мощные инструменты, которые позволяют вам улучшать ваши документы путем внедрения или связывания внешнего контента, например, электронных таблиц, файлов мультимедиа или интерактивных элементов управления. Следуйте за нами, пока мы углубляемся в примеры кода и узнаем, как эффективно использовать эти функции.

### Предпосылки

Прежде чем начать, убедитесь, что у вас выполнены следующие предварительные условия:

1.  Aspose.Words для Java: Убедитесь, что в вашем проекте Java установлена библиотека Aspose.Words. Вы можете загрузить ее с[здесь](https://releases.aspose.com/words/java/).

2. Среда разработки Java: в вашей системе должна быть настроена рабочая среда разработки Java.

### Вставка объекта OLE

Давайте начнем со вставки объекта OLE в документ Word. Мы создадим простой документ Word, а затем вставим объект OLE, представляющий веб-страницу.

```java
string outPath = "Your Output Directory";
public void insertOleObject() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObject("http://www.aspose.com", "htmlfile", правда, правда, null);
    doc.save("Your Directory Path" + "WorkingWithOleObjectsAndActiveX.InsertOleObject.docx");
}
```

В этом коде мы создаем новый документ и вставляем объект OLE, который отображает веб-сайт Aspose. Вы можете заменить URL на желаемый контент.

### Вставка объекта OLE с помощью OlePackage

Далее давайте рассмотрим, как вставить объект OLE с помощью OlePackage. Это позволяет вам встраивать внешние файлы как объекты OLE в ваш документ.

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

В этом примере мы вставляем объект OLE с помощью OlePackage, что позволяет включать внешние файлы в качестве встроенных объектов.

### Вставка объекта OLE в качестве значка

Теперь давайте посмотрим, как вставить объект OLE в качестве значка. Это полезно, когда вы хотите отобразить значок, представляющий встроенный файл.

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

В этом коде мы вставляем объект OLE в качестве значка, обеспечивая более визуально привлекательное представление встроенного содержимого.

### Чтение свойств элемента управления ActiveX

Теперь давайте переключим внимание на элементы управления ActiveX. Мы научимся читать свойства элементов управления ActiveX в документе Word.

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

В этом коде мы перебираем фигуры в документе Word, идентифицируем элементы управления ActiveX и извлекаем их свойства.

### Заключение

Поздравляем! Вы научились работать с объектами OLE и элементами управления ActiveX в Aspose.Words для Java. Эти функции открывают целый мир возможностей для создания динамических и интерактивных документов.

### Часто задаваемые вопросы

### Каково назначение объектов OLE в документе Word? 
   - Объекты OLE позволяют встраивать или связывать внешний контент, например файлы или веб-страницы, в документ Word.

### Могу ли я настроить внешний вид объектов OLE в моем документе? 
   - Да, вы можете настраивать внешний вид объектов OLE, включая установку значков и имен файлов.

### Что такое элементы управления ActiveX и как они могут улучшить мои документы? 
   - Элементы управления ActiveX — это интерактивные элементы, которые могут добавлять функциональность в документы Word, например элементы управления формами или мультимедийные проигрыватели.

### Подходит ли Aspose.Words for Java для автоматизации документооборота на корпоративном уровне? 
   - Да, Aspose.Words для Java — это мощная библиотека для автоматизации создания и обработки документов в приложениях Java.

### Где я могу получить доступ к Aspose.Words для Java? 
   -  Вы можете загрузить Aspose.Words для Java с сайта[здесь](https://releases.aspose.com/words/java/).

Начните работу с Aspose.Words для Java уже сегодня и раскройте весь потенциал автоматизации и настройки документов!

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
