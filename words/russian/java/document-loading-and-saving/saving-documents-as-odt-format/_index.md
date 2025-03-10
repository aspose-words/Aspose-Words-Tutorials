---
title: Сохранение документов в формате ODT в Aspose.Words для Java
linktitle: Сохранение документов в формате ODT
second_title: API обработки документов Java Aspose.Words
description: Узнайте, как сохранять документы в формате ODT с помощью Aspose.Words для Java. Обеспечьте совместимость с офисными пакетами с открытым исходным кодом.
weight: 19
url: /ru/java/document-loading-and-saving/saving-documents-as-odt-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Сохранение документов в формате ODT в Aspose.Words для Java


## Введение в сохранение документов в формате ODT в Aspose.Words для Java

В этой статье мы рассмотрим, как сохранять документы в формате ODT (Open Document Text) с помощью Aspose.Words for Java. ODT — популярный формат документов открытого стандарта, используемый различными офисными пакетами, включая OpenOffice и LibreOffice. Сохраняя документы в формате ODT, вы можете обеспечить совместимость с этими программными пакетами.

## Предпосылки

Прежде чем начать, убедитесь, что у вас выполнены следующие предварительные условия:

1. Среда разработки Java: убедитесь, что в вашей системе установлен Java Development Kit (JDK).

2.  Aspose.Words for Java: Загрузите и установите библиотеку Aspose.Words for Java. Ссылку на скачивание вы найдете[здесь](https://releases.aspose.com/words/java/).

3. Образец документа: у вас должен быть образец документа Word (например, «Document.docx»), который вы хотите преобразовать в формат ODT.

## Шаг 1: Загрузите документ

Сначала загрузим документ Word с помощью Aspose.Words для Java:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
```

 Здесь,`"Your Directory Path"` должен указывать на каталог, в котором находится ваш документ.

## Шаг 2: Укажите параметры сохранения ODT

Чтобы сохранить документ в формате ODT, нам нужно указать параметры сохранения ODT. Кроме того, мы можем задать единицу измерения для документа. Open Office использует сантиметры, а MS Office — дюймы. Мы установим дюймы:

```java
OdtSaveOptions saveOptions = new OdtSaveOptions();
saveOptions.setMeasureUnit(OdtSaveMeasureUnit.INCHES);
```

## Шаг 3: Сохраните документ

Теперь пришло время сохранить документ в формате ODT:

```java
doc.save("Your Directory Path" + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

 Здесь,`"Your Directory Path"` должен указывать на каталог, в котором вы хотите сохранить преобразованный ODT-файл.

## Полный исходный код для сохранения документов в формате ODT в Aspose.Words для Java

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
// Open Office использует сантиметры при указании длины, ширины и других измеряемых форматов.
// и свойства содержимого в документах, тогда как MS Office использует дюймы.
OdtSaveOptions saveOptions = new OdtSaveOptions(); { saveOptions.setMeasureUnit(OdtSaveMeasureUnit.INCHES); }
doc.save("Your Directory Path" + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

## Заключение

В этой статье мы узнали, как сохранять документы в формате ODT с помощью Aspose.Words for Java. Это может быть особенно полезно, когда вам нужно обеспечить совместимость с офисными пакетами с открытым исходным кодом, такими как OpenOffice и LibreOffice.

## Часто задаваемые вопросы

### Как загрузить Aspose.Words для Java?

 Вы можете загрузить Aspose.Words для Java с веб-сайта Aspose. Посетите[эта ссылка](https://releases.aspose.com/words/java/) для доступа к странице загрузки.

### В чем преимущество сохранения документов в формате ODT?

Сохранение документов в формате ODT обеспечивает совместимость с офисными пакетами с открытым исходным кодом, такими как OpenOffice и LibreOffice, что упрощает пользователям этих программных пакетов доступ к документам и их редактирование.

### Нужно ли указывать единицу измерения при сохранении в формате ODT?

Да, указывать единицу измерения — это хорошая практика. Open Office по умолчанию использует сантиметры, поэтому установка дюймов обеспечивает единообразное форматирование.

### Можно ли конвертировать несколько документов в формат ODT в пакетном режиме?

Да, вы можете автоматизировать преобразование нескольких документов в формат ODT с помощью Aspose.Words для Java, пройдясь по файлам документов и применив процесс преобразования.

### Совместим ли Aspose.Words для Java с последними версиями Java?

Aspose.Words for Java регулярно обновляется для поддержки последних версий Java, обеспечивая совместимость и улучшение производительности. Обязательно проверьте системные требования в документации для получения последней информации.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
