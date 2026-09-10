---
date: 2025-12-18
description: Узнайте, как добавить водяной знак в документы с помощью Aspose.Words
  for Java, включая пример водяного знака‑изображения, изменение цвета водяного знака,
  настройку его прозрачности и удаление водяного знака из документа.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Как добавить водяной знак в документы с помощью Aspose.Words для Java
url: /ru/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Как добавить водяной знак в документы с помощью Aspose.Words для Java

## Введение в добавление водяных знаков в документы с помощью Aspose.Words для Java

В этом руководстве вы узнаете **как добавить водяной знак** в документы Word с помощью Aspose.Words для Java. Водяные знаки – быстрый способ пометить файл как конфиденциальный, черновик или одобренный; они могут быть текстовыми или графическими. Мы пройдем процесс настройки библиотеки, создания текстовых и графических водяных знаков, настройки их внешнего вида (включая изменение цвета водяного знака и установку прозрачности), а также удаления водяного знака из документа, когда он больше не нужен.

## Краткие ответы
- **Что такое водяной знак?** Полупрозрачный наложенный слой (текст или изображение), который отображается позади основного содержимого документа.  
- **Можно ли добавить несколько водяных знаков?** Да – создайте несколько объектов `Shape` и добавьте каждый в нужные разделы.  
- **Как изменить цвет водяного знака?** Отрегулируйте свойство `Color` в `TextWatermarkOptions`.  
- **Есть ли пример графического водяного знака?** См. раздел «Добавление изображений‑водяных знаков» ниже.  
- **Нужна ли лицензия для удаления водяного знака?** Для использования в продакшене требуется действующая лицензия Aspose.Words.

## Настройка Aspose.Words для Java

Прежде чем начать добавлять водяные знаки в документы, необходимо настроить Aspose.Words для Java. Выполните следующие шаги:

1. Скачайте Aspose.Words для Java с [здесь](https://releases.aspose.com/words/java/).  
2. Добавьте библиотеку Aspose.Words для Java в ваш Java‑проект.  
3. Импортируйте необходимые классы в ваш Java‑код.

Теперь, когда библиотека настроена, перейдём к созданию водяных знаков.

## Добавление текстовых водяных знаков

Текстовые водяные знаки – популярный выбор, когда нужно добавить в документ текстовую информацию. Ниже показано, как добавить текстовый водяной знак с помощью Aspose.Words для Java:

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Define TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Set the watermark text and options
doc.getWatermark().setText("Test", options);

// Save the document with the watermark
doc.save("DocumentWithWatermark.docx");
```

**Почему это важно:** Путём настройки `setFontFamily`, `setFontSize` и `setColor` вы можете **изменить цвет водяного знака** в соответствии с фирменным стилем, а `setSemitransparent(true)` позволяет **установить прозрачность водяного знака** для более мягкого эффекта.

## Добавление изображений‑водяных знаков

Помимо текстовых водяных знаков, вы также можете добавлять графические водяные знаки в документы. Ниже приведён **пример графического водяного знака**, демонстрирующий, как встроить PNG‑логотип или печать:

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Load the image for the watermark
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Set the watermark size and position
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Add the watermark to the document
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Save the document with the watermark
doc.save("DocumentWithImageWatermark.docx");
```

Вы можете повторить этот блок с другими изображениями или позициями, чтобы **добавить несколько водяных знаков** в один файл.

## Настройка водяных знаков

Водяные знаки можно настраивать, изменяя их внешний вид и позицию. Для текстовых водяных знаков можно менять шрифт, размер, цвет и расположение. Для графических водяных знаков можно изменять размер, вращение и выравнивание, как показано в предыдущих примерах.

## Удаление водяных знаков

Если необходимо **удалить водяной знак** из документа, следующий код проходит по всем фигурам и удаляет те, которые идентифицированы как водяные знаки:

```java
// Create a Document instance
Document doc = new Document("DocumentWithWatermark.docx");

// Remove the watermark
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Save the document without the watermark
doc.save("DocumentWithoutWatermark.docx");
```

## Общие сценарии использования и советы

- **Конфиденциальные черновики:** Применяйте полупрозрачный текстовый водяной знак типа «CONFIDENTIAL».  
- **Брендинг:** Используйте графический водяной знак с логотипом вашей компании.  
- **Водяные знаки для отдельных разделов:** Проходите по `doc.getSections()` и добавляйте водяной знак только в выбранные разделы.  
- **Совет по производительности:** При применении одного и того же водяного знака к множеству документов переиспользуйте один экземпляр `TextWatermarkOptions`.

## Часто задаваемые вопросы

### Как изменить шрифт текстового водяного знака?

Чтобы изменить шрифт текстового водяного знака, измените свойство `setFontFamily` в `TextWatermarkOptions`. Например:

```java
options.setFontFamily("Times New Roman");
```

### Можно ли добавить несколько водяных знаков в один документ?

Да, вы можете добавить несколько водяных знаков, создав несколько объектов `Shape` с разными настройками и добавив их в документ.

### Можно ли повернуть водяной знак?

Да, водяной знак можно повернуть, установив свойство `setRotation` в объекте `Shape`. Положительные значения вращают водяной знак по часовой стрелке, отрицательные – против часовой стрелки.

### Как сделать водяной знак полупрозрачным?

Чтобы сделать водяной знак полупрозрачным, установите свойство `setSemitransparent` в `true` в `TextWatermarkOptions`.

### Можно ли добавить водяные знаки только в определённые разделы документа?

Да, вы можете добавить водяные знаки в конкретные разделы, проходя по разделам и вставляя водяной знак в нужные из них.

---

**Последнее обновление:** 2025-12-18  
**Тестировано с:** Aspose.Words для Java 24.12  
**Автор:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}