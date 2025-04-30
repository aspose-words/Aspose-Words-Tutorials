---
"description": "Узнайте, как сохранять документы как текстовые файлы в Aspose.Words для Java. Следуйте нашему пошаговому руководству с примерами кода Java."
"linktitle": "Сохранение документов в виде текстовых файлов"
"second_title": "API обработки документов Java Aspose.Words"
"title": "Сохранение документов в виде текстовых файлов в Aspose.Words для Java"
"url": "/ru/java/document-loading-and-saving/saving-documents-as-text-files/"
"weight": 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Сохранение документов в виде текстовых файлов в Aspose.Words для Java


## Введение в сохранение документов в виде текстовых файлов в Aspose.Words для Java

В этом уроке мы рассмотрим, как сохранять документы в виде текстовых файлов с помощью библиотеки Aspose.Words for Java. Aspose.Words — это мощный API Java для работы с документами Word, который предоставляет различные возможности сохранения документов в разных форматах, включая простой текст. Мы рассмотрим шаги для достижения этого и предоставим пример кода Java по ходу дела.

## Предпосылки

Прежде чем начать, убедитесь, что у вас выполнены следующие предварительные условия:

- В вашей системе установлен Java Development Kit (JDK).
- Библиотека Aspose.Words for Java интегрирована в ваш проект. Вы можете скачать ее с [здесь](https://releases.aspose.com/words/java/).
- Базовые знания программирования на Java.

## Шаг 1: Создайте документ

Чтобы сохранить документ как текстовый файл, нам сначала нужно создать документ с помощью Aspose.Words. Вот простой фрагмент кода Java для создания документа с некоторым содержимым:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

В этом коде мы создаем новый документ и добавляем в него текст, включая текст на разных языках.

## Шаг 2: Определите параметры сохранения текста

Далее нам нужно определить параметры сохранения текста, которые указывают, как документ должен быть сохранен в виде текстового файла. Мы можем настроить различные параметры, такие как добавление двунаправленных меток, отступов в списке и т. д. Давайте рассмотрим два примера:

### Пример 1: Добавление биди-меток

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

В этом примере мы создаем `TxtSaveOptions` объект и установите `AddBidiMarks` собственность `true` для включения двунаправленных знаков в текстовый вывод.

### Пример 2: Использование символа табуляции для отступа списка

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Здесь мы настраиваем параметры сохранения для использования символа табуляции для отступа списка со значением 1.

## Шаг 3: Сохраните документ как текст

Теперь, когда мы определили параметры сохранения текста, мы можем сохранить документ как текстовый файл. Следующий код демонстрирует, как это сделать:

```java
doc.save("output.txt", saveOptions);
```

Заменять `"output.txt"` с желаемым путем к файлу, в котором вы хотите сохранить текстовый файл.

## Полный исходный код для сохранения документов в виде текстовых файлов в Aspose.Words для Java

```java
    public void addBidiMarks() throws Exception
    {        
		Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("Hello world!");
        builder.getParagraphFormat().setBidi(true);
        builder.writeln("שלום עולם!");
        builder.writeln("مرحبا بالعالم!");
        TxtSaveOptions saveOptions = new TxtSaveOptions(); { saveOptions.setAddBidiMarks(true); }
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
    }
    @Test
    public void useTabCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Создайте список с тремя уровнями отступов.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(1);
        saveOptions.getListIndentation().setCharacter('\t');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseTabCharacterPerLevelForListIndentation.txt", saveOptions);
    }
    @Test
    public void useSpaceCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Создайте список с тремя уровнями отступов.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(3);
        saveOptions.getListIndentation().setCharacter(' ');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
	}
```

## Заключение

В этом уроке мы узнали, как сохранять документы в виде текстовых файлов в Aspose.Words для Java. Мы рассмотрели шаги по созданию документа, определению параметров сохранения текста и сохранению документа в текстовом формате. Aspose.Words обеспечивает большую гибкость при сохранении документов, позволяя вам адаптировать вывод в соответствии с вашими конкретными требованиями.

## Часто задаваемые вопросы

### Как добавить двунаправленные знаки в выводимый текст?

Чтобы добавить двунаправленные знаки к текстовому выводу, установите `AddBidiMarks` собственность `TxtSaveOptions` к `true`. Например:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Могу ли я настроить символ отступа в списке?

Да, вы можете настроить символ отступа списка, настроив `ListIndentation` собственность `TxtSaveOptions`. Например, чтобы использовать символ табуляции для отступа списка, можно сделать следующее:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Подходит ли Aspose.Words для Java для обработки многоязычного текста?

Да, Aspose.Words for Java подходит для обработки многоязычного текста. Он поддерживает различные языки и кодировки символов, что делает его универсальным выбором для работы с документами на разных языках.

### Как мне получить доступ к дополнительной документации и ресурсам по Aspose.Words для Java?

Подробную документацию и ресурсы по Aspose.Words для Java можно найти на веб-сайте документации Aspose: [Документация Aspose.Words для Java](https://reference.aspose.com/words/java/).

### Где можно скачать Aspose.Words для Java?

Вы можете загрузить библиотеку Aspose.Words для Java с веб-сайта Aspose: [Загрузить Aspose.Words для Java](https://releases.aspose.com/words/java/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}