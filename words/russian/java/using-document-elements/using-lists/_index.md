---
title: Использование списков в Aspose.Words для Java
linktitle: Использование списков
second_title: API обработки документов Java Aspose.Words
description: Изучите использование списков в Aspose.Words для Java с помощью этого пошагового руководства. Эффективно организуйте и форматируйте свои документы.
weight: 18
url: /ru/java/using-document-elements/using-lists/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Использование списков в Aspose.Words для Java


В этом всеобъемлющем руководстве мы рассмотрим, как эффективно использовать списки в Aspose.Words для Java, мощном API для программной работы с документами Microsoft Word. Списки необходимы для структурирования и организации контента в ваших документах. Мы рассмотрим два ключевых аспекта работы со списками: перезапуск списков в каждом разделе и указание уровней списков. Давайте погрузимся!

## Введение в Aspose.Words для Java

Прежде чем начать работать со списками, давайте познакомимся с Aspose.Words for Java. Этот API предоставляет разработчикам инструменты для создания, изменения и управления документами Word в среде Java. Это универсальное решение для задач от простого создания документов до сложного форматирования и управления содержимым.

### Настройка вашей среды

 Для начала убедитесь, что у вас установлен и настроен Aspose.Words for Java в вашей среде разработки. Вы можете скачать его[здесь](https://releases.aspose.com/words/java/). 

## Перезапуск списков в каждом разделе

Во многих сценариях вам может потребоваться перезапустить списки в каждом разделе документа. Это может быть полезно для создания структурированных документов с несколькими разделами, таких как отчеты, руководства или научные статьи.

Вот пошаговое руководство по достижению этого с помощью Aspose.Words для Java:

### Инициализируйте свой документ: 
Начните с создания нового объекта документа.

```java
Document doc = new Document();
```

### Добавить нумерованный список: 
Добавьте нумерованный список в ваш документ. Мы будем использовать стиль нумерации по умолчанию.

```java
doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
```

### Настроить параметры списка: 
\Включить перезапуск списка в каждом разделе.

```java
List list = doc.getLists().get(0);
list.isRestartAtEachSection(true);
```

### Настройка DocumentBuilder: 
Создайте DocumentBuilder для добавления контента в ваш документ.

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.getListFormat().setList(list);
```

### Добавить элементы списка: 
Используйте цикл для добавления элементов списка в документ. Мы вставим разрыв раздела после 15-го элемента.

```java
for (int i = 1; i < 45; i++) {
    builder.writeln(MessageFormat.format("List Item {0}", i));
    if (i == 15)
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
}
```

### Сохраните документ: 
Сохраните документ с желаемыми параметрами.

```java
OoxmlSaveOptions options = new OoxmlSaveOptions();
options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);
doc.save(outPath + "RestartListAtEachSection.docx", options);
```

Выполнив эти шаги, вы сможете создавать документы со списками, которые начинаются заново в каждом разделе, сохраняя четкую и организованную структуру контента.

## Указание уровней списка

Aspose.Words for Java позволяет вам указывать уровни списков, что особенно полезно, когда вам нужны разные форматы списков в вашем документе. Давайте рассмотрим, как это сделать:

### Инициализируйте свой документ: 
Создайте новый объект документа.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Создайте нумерованный список: 
Примените шаблон нумерованного списка из Microsoft Word.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
```

### Укажите уровни списка: 
Просматривайте различные уровни списка и добавляйте контент.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Создайте маркированный список: 
Теперь давайте создадим маркированный список.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
```

### Укажите уровни маркированного списка: 
Аналогично нумерованному списку укажите уровни и добавьте контент.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Форматирование списка стоп-сигналов: 
Чтобы остановить форматирование списка, установите для него значение null.

```java
builder.getListFormat().setList(null);
```

### Сохраните документ: 
Сохраните документ.

```java
builder.getDocument().save(outPath + "SpecifyListLevel.docx");
```

Выполнив эти шаги, вы сможете создавать документы с настраиваемыми уровнями списков, что позволит вам контролировать форматирование списков в ваших документах.

## Полный исходный код
```java
	string outPath = "Your Output Directory";
 public void restartListAtEachSection() throws Exception
    {
        Document doc = new Document();
        doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
        List list = doc.getLists().get(0);
        list.isRestartAtEachSection(true);
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.getListFormat().setList(list);
        for (int i = 1; i < 45; i++)
        {
            builder.writeln(MessageFormat.format("List Item {0}", i));
            if (i == 15)
                builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        }
        // IsRestartAtEachSection будет записан только в том случае, если соответствие выше, чем OoxmlComplianceCore.Ecma376.
        OoxmlSaveOptions options = new OoxmlSaveOptions(); { options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL); }
        doc.save(outPath + "WorkingWithList.RestartListAtEachSection.docx", options);
    }
    @Test
    public void specifyListLevel() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Создайте нумерованный список на основе одного из шаблонов списков Microsoft Word.
        //и применить его к текущему абзацу конструктора документа.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
        // В этом списке девять уровней, давайте попробуем их все.
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Создайте маркированный список на основе одного из шаблонов списков Microsoft Word.
        //и применить его к текущему абзацу конструктора документа.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Это способ прекратить форматирование списка.
        builder.getListFormat().setList(null);
        builder.getDocument().save(outPath + "WorkingWithList.SpecifyListLevel.docx");
    }
    @Test
    public void restartListNumber() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Создайте список на основе шаблона.
        List list1 = doc.getLists().add(ListTemplate.NUMBER_ARABIC_PARENTHESIS);
        list1.getListLevels().get(0).getFont().setColor(Color.RED);
        list1.getListLevels().get(0).setAlignment(ListLevelAlignment.RIGHT);
        builder.writeln("List 1 starts below:");
        builder.getListFormat().setList(list1);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        // Чтобы повторно использовать первый список, нам необходимо перезапустить нумерацию, создав копию исходного форматирования списка.
        List list2 = doc.getLists().addCopy(list1);
        // Мы можем изменить новый список любым способом, включая установку нового стартового номера.
        list2.getListLevels().get(0).setStartAt(10);
        builder.writeln("List 2 starts below:");
        builder.getListFormat().setList(list2);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        builder.getDocument().save(outPath + "WorkingWithList.RestartListNumber.docx");
	}
```

## Заключение

Поздравляем! Вы научились эффективно работать со списками в Aspose.Words for Java. Списки имеют решающее значение для организации и представления контента в ваших документах. Если вам нужно перезапустить списки в каждом разделе или указать уровни списков, Aspose.Words for Java предоставляет инструменты, необходимые для создания профессионально выглядящих документов.

Теперь вы можете уверенно использовать эти функции для улучшения задач по созданию и форматированию документов. Если у вас есть вопросы или вам нужна дополнительная помощь, не стесняйтесь обращаться к[Форум сообщества Aspose](https://forum.aspose.com/) за поддержку.

## Часто задаваемые вопросы

### Как установить Aspose.Words для Java?
 Вы можете загрузить Aspose.Words для Java с сайта[здесь](https://releases.aspose.com/words/java/) и следуйте инструкциям по установке, приведенным в документации.

### Могу ли я настроить формат нумерации списков?
Да, Aspose.Words for Java предоставляет обширные возможности для настройки форматов нумерации списков. Подробности можно узнать в документации API.

### Совместим ли Aspose.Words для Java с последними стандартами документов Word?
Да, вы можете настроить Aspose.Words для Java для соответствия различным стандартам документов Word, включая ISO 29500.

### Можно ли создавать сложные документы с таблицами и изображениями с помощью Aspose.Words для Java?
Конечно! Aspose.Words для Java поддерживает расширенное форматирование документов, включая таблицы, изображения и многое другое. Ознакомьтесь с примерами в документации.

### Где я могу получить временную лицензию для Aspose.Words для Java?
Вы можете получить временную лицензию[здесь](https://purchase.aspose.com/temporary-license/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
