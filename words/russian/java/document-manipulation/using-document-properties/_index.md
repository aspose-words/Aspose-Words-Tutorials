---
title: Использование свойств документа в Aspose.Words для Java
linktitle: Использование свойств документа
second_title: API обработки документов Java Aspose.Words
description: Оптимизируйте управление документами с помощью Aspose.Words для Java. Научитесь работать со свойствами документа, добавлять пользовательские метаданные и многое другое в этом всеобъемлющем руководстве.
weight: 32
url: /ru/java/document-manipulation/using-document-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Использование свойств документа в Aspose.Words для Java


## Введение в свойства документа

Свойства документа являются важной частью любого документа. Они предоставляют дополнительную информацию о самом документе, такую как его заголовок, автор, тема, ключевые слова и многое другое. В Aspose.Words для Java вы можете управлять как встроенными, так и пользовательскими свойствами документа.

## Перечисление свойств документа

### Встроенные свойства

Для извлечения и работы со встроенными свойствами документа можно использовать следующий фрагмент кода:

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

Этот код отобразит имя документа и встроенные свойства, включая такие свойства, как «Название», «Автор» и «Ключевые слова».

### Пользовательские свойства

Для работы с пользовательскими свойствами документа можно использовать следующий фрагмент кода:

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

В этом фрагменте кода показано, как добавлять пользовательские свойства документа, включая логическое значение, строку, дату, номер редакции и числовое значение.

## Удаление свойств документа

Чтобы удалить определенные свойства документа, можно использовать следующий код:

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

Этот код удаляет пользовательское свойство «Дата авторизации» из документа.

## Настройка ссылки на контент

В некоторых случаях вам может понадобиться создать ссылки в вашем документе. Вот как это можно сделать:

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // Добавить связанное с содержимым свойство.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

В этом фрагменте кода показано, как создать закладку в документе и добавить пользовательское свойство документа, ссылающееся на эту закладку.

## Преобразование единиц измерения

В Aspose.Words for Java вы можете легко конвертировать единицы измерения. Вот пример того, как это сделать:

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Установите поля в дюймах.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

Этот фрагмент кода устанавливает различные поля и расстояния в дюймах, преобразуя их в пункты.

## Использование управляющих символов

Управляющие символы могут быть полезны при работе с текстом. Вот как заменить управляющий символ в тексте:

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Замените управляющий символ "\r" на "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

В этом примере мы заменяем возврат каретки (`\r`) с возвратом каретки, за которым следует перевод строки (`\r\n`).

## Заключение

Свойства документа играют важную роль в эффективном управлении и организации ваших документов в Aspose.Words for Java. Независимо от того, работаете ли вы со встроенными свойствами, пользовательскими свойствами или используете управляющие символы, в вашем распоряжении есть ряд инструментов для улучшения возможностей управления документами.

## Часто задаваемые вопросы

### Как получить доступ к встроенным свойствам документа?

 Чтобы получить доступ к встроенным свойствам документа в Aspose.Words для Java, вы можете использовать`getBuiltInDocumentProperties` метод на`Document` объект. Этот метод возвращает коллекцию встроенных свойств, которые можно перебирать.

### Могу ли я добавить в документ пользовательские свойства?

 Да, вы можете добавлять пользовательские свойства документа с помощью`CustomDocumentProperties` Коллекция. Вы можете определить пользовательские свойства с различными типами данных, включая строки, логические значения, даты и числовые значения.

### Как удалить определенное пользовательское свойство документа?

 Чтобы удалить определенное пользовательское свойство документа, вы можете использовать`remove` метод на`CustomDocumentProperties`коллекции, передавая в качестве параметра имя свойства, которое требуется удалить.

### Какова цель ссылки на содержимое документа?

Ссылка на содержимое внутри документа позволяет создавать динамические ссылки на определенные части документа. Это может быть полезно для создания интерактивных документов или перекрестных ссылок между разделами.

### Как можно преобразовать различные единицы измерения в Aspose.Words для Java?

 Вы можете конвертировать между различными единицами измерения в Aspose.Words для Java, используя`ConvertUtil` класс. Он предоставляет методы для преобразования единиц измерения, таких как дюймы в пункты, пункты в сантиметры и т. д.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
