---
"description": "Узнайте, как добавлять водяные знаки в документы в Aspose.Words для Java. Настройте текстовые и графические водяные знаки для профессионально выглядящих документов."
"linktitle": "Использование водяных знаков в документах"
"second_title": "API обработки документов Java Aspose.Words"
"title": "Использование водяных знаков в документах в Aspose.Words для Java"
"url": "/ru/java/document-conversion-and-export/using-watermarks-to-documents/"
"weight": 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Использование водяных знаков в документах в Aspose.Words для Java


## Введение в добавление водяных знаков в документы в Aspose.Words для Java

В этом руководстве мы рассмотрим, как добавлять водяные знаки в документы с помощью API Aspose.Words for Java. Водяные знаки — это полезный способ маркировать документы текстом или графикой, чтобы указать их статус, конфиденциальность или другую важную информацию. В этом руководстве мы рассмотрим как текстовые, так и графические водяные знаки.

## Настройка Aspose.Words для Java

Прежде чем начать добавлять водяные знаки в документы, нам нужно настроить Aspose.Words для Java. Выполните следующие шаги, чтобы начать:

1. Загрузите Aspose.Words для Java с сайта [здесь](https://releases.aspose.com/words/java/).
2. Добавьте библиотеку Aspose.Words для Java в свой проект Java.
3. Импортируйте необходимые классы в свой код Java.

Теперь, когда у нас настроена библиотека, давайте приступим к добавлению водяных знаков.

## Добавление текстовых водяных знаков

Текстовые водяные знаки являются обычным выбором, когда вы хотите добавить текстовую информацию в свои документы. Вот как можно добавить текстовый водяной знак с помощью Aspose.Words для Java:

```java
// Создать экземпляр документа
Document doc = new Document("Document.docx");

// Определить параметры текстового водяного знака
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Установите текст и параметры водяного знака
doc.getWatermark().setText("Test", options);

// Сохраните документ с водяным знаком
doc.save("DocumentWithWatermark.docx");
```

## Добавление водяных знаков на изображение

В дополнение к текстовым водяным знакам вы также можете добавлять водяные знаки-изображения в свои документы. Вот как добавить водяной знак-изображение:

```java
// Создать экземпляр документа
Document doc = new Document("Document.docx");

// Загрузите изображение для водяного знака
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Установите размер и положение водяного знака
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Добавить водяной знак в документ
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Сохраните документ с водяным знаком
doc.save("DocumentWithImageWatermark.docx");
```

## Настройка водяных знаков

Вы можете настроить водяные знаки, изменив их внешний вид и положение. Для текстовых водяных знаков вы можете изменить шрифт, размер, цвет и макет. Для водяных знаков с изображениями вы можете изменить их размер и положение, как показано в предыдущих примерах.

## Удаление водяных знаков

Чтобы удалить водяные знаки из документа, вы можете использовать следующий код:

```java
// Создать экземпляр документа
Document doc = new Document("DocumentWithWatermark.docx");

// Удалить водяной знак
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Сохраните документ без водяного знака
doc.save("DocumentWithoutWatermark.docx");
```


## Заключение

В этом уроке мы узнали, как добавлять водяные знаки в документы с помощью Aspose.Words для Java. Если вам нужно добавить текстовые или графические водяные знаки, Aspose.Words предоставляет инструменты для их эффективной настройки и управления. Вы также можете удалить водяные знаки, когда они больше не нужны, гарантируя, что ваши документы будут чистыми и профессиональными.

## Часто задаваемые вопросы

### Как изменить шрифт текстового водяного знака?

Чтобы изменить шрифт текстового водяного знака, измените `setFontFamily` недвижимость в `TextWatermarkOptions`. Например:

```java
options.setFontFamily("Times New Roman");
```

### Можно ли добавить несколько водяных знаков в один документ?

Да, вы можете добавить несколько водяных знаков в документ, создав несколько `Shape` объекты с различными настройками и добавление их в документ.

### Можно ли повернуть водяной знак?

Да, вы можете вращать водяной знак, установив `setRotation` недвижимость в `Shape` объект. Положительные значения вращают водяной знак по часовой стрелке, а отрицательные значения вращают его против часовой стрелки.

### Как сделать водяной знак полупрозрачным?

Чтобы сделать водяной знак полупрозрачным, установите `setSemitransparent` собственность `true` в `TextWatermarkOptions`.

### Могу ли я добавить водяные знаки в определенные разделы документа?

Да, вы можете добавлять водяные знаки в определенные разделы документа, перебирая разделы и добавляя водяной знак в нужные разделы.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}