---
date: 2026-02-19
description: Узнайте, как создать документ с водяным знаком с помощью Aspose.Words
  для Java и добавить изображение водяного знака в Java для профессионально выглядящих
  документов.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Создание документа с водяным знаком с помощью Aspose.Words для Java
url: /ru/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Создание документа с водяным знаком с помощью Aspose.Words for Java

В этом руководстве вы **создадите документ с водяным знаком** с помощью API Aspose.Words for Java. Водяные знаки — будь то текст или изображения — помогают пометить файл как конфиденциальный, черновик или одобренный, и их можно программно применять к любому документу Word. Мы пройдем настройку библиотеки, добавление как текстовых, так и графических водяных знаков, настройку их внешнего вида и даже их удаление, когда они больше не нужны.

## Быстрые ответы
- **Что делает водяной знак?** Он накладывает текст или изображение на каждую страницу, чтобы передать статус или бренд.  
- **Какая библиотека добавляет водяные знаки в Java?** Aspose.Words for Java предоставляет встроенную поддержку водяных знаков.  
- **Можно ли добавить графический водяной знак?** Да — используйте класс `Shape` и подход `add image watermark java`.  
- **Является ли водяной знак полупрозрачным?** Вы можете управлять непрозрачностью через `setSemitransparent` для текстовых водяных знаков.  
- **Нужна ли лицензия?** Бесплатная пробная версия подходит для тестирования; для продакшена требуется коммерческая лицензия.

## Что такое водяной знак и зачем его использовать?

Водяной знак — это слабый наложенный слой — текстовый или графический — добавляемый к каждой странице документа. Он обычно используется для указания **конфиденциальности**, **статуса черновика** или **брендинга**, не изменяя основной контент. Программное добавление водяных знаков обеспечивает согласованность при работе с большими партиями файлов и экономит время по сравнению с ручным редактированием.

## Настройка Aspose.Words for Java

Прежде чем начинать добавлять водяные знаки, убедитесь, что библиотека готова к использованию в вашем проекте:

1. Скачайте Aspose.Words for Java с [здесь](https://releases.aspose.com/words/java/).  
2. Добавьте загруженный JAR (или зависимость Maven/Gradle) в classpath вашего проекта.  
3. Импортируйте необходимые классы в ваш Java‑файл:

```java
import com.aspose.words.*;
import java.awt.Color;
import java.nio.file.*;
```

Теперь, когда библиотека настроена, давайте перейдём к реальному коду водяного знака.

## Как добавить текстовый водяной знак

Текстовые водяные знаки идеальны для пометки документа как «CONFIDENTIAL» или «DRAFT». Ниже приведён фрагмент, показывающий простой способ **создать документ с водяным знаком** с использованием `TextWatermarkOptions`.

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

### Настройка текстового водяного знака
- **Семейство шрифтов и размер** — измените `setFontFamily` и `setFontSize`.  
- **Цвет** — используйте любой `java.awt.Color`.  
- **Размещение** — выберите `HORIZONTAL`, `DIAGONAL` и т.д.  
- **Прозрачность** — включите `setSemitransparent(true)` для более лёгкого вида.

## Как добавить графический водяной знак (add image watermark java)

Графические водяные знаки подходят для логотипов или пользовательской графики. Ниже приведён пример **add image watermark java**, который вставляет PNG в центр каждой страницы.

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

### Советы по графическим водяным знакам
- **Изменение размера** с помощью `setWidth` / `setHeight` для подгонки под страницу.  
- **Позиция** может быть центрирована или выровнена по любому полю с использованием `RelativeHorizontalPosition` / `RelativeVerticalPosition`.  
- **Прозрачность** может быть применена путём регулировки альфа‑канала изображения перед загрузкой.

## Как удалить водяные знаки

Когда документ больше не нуждается в водяном знаке, его можно удалить программно. Приведённый ниже код проходит по всем фигурам и удаляет те, в имени которых содержится «Watermark».

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

## Распространённые ошибки и их устранение
- **Водяной знак отсутствует после сохранения** — убедитесь, что вызываете `doc.save()` после установки водяного знака.  
- **Изображение не отображается** — проверьте правильность пути к изображению и поддерживаемый формат файла (PNG, JPEG, BMP).  
- **Прозрачность не применяется** — `setSemitransparent(true)` работает только для текстовых водяных знаков; для изображений отредактируйте альфа‑канал PNG.  
- **Несколько секций** — если в документе несколько секций, добавьте водяной знак в тело каждой секции или используйте `doc.getWatermark().setText(...)`, который применяется глобально.

## Часто задаваемые вопросы

**В: Как изменить шрифт текстового водяного знака?**  
О: Измените свойство `setFontFamily` в `TextWatermarkOptions`, например, `options.setFontFamily("Times New Roman");`.

**В: Можно ли добавить несколько водяных знаков в один документ?**  
О: Да. Создайте несколько объектов `Shape` (для изображений) или вызовите `doc.getWatermark().setText(...)` с разными параметрами для каждого водяного знака.

**В: Можно ли повернуть водяной знак?**  
О: Для графических водяных знаков задайте вращение у объекта `Shape` через `watermark.setRotation(angle)`. Для текстовых водяных знаков используйте свойство `setLayout` (например, `WatermarkLayout.DIAGONAL`).

**В: Как сделать водяной знак полупрозрачным?**  
О: Установите `options.setSemitransparent(true)` в `TextWatermarkOptions`. Для изображений отрегулируйте их непрозрачность перед загрузкой.

**В: Можно ли добавить водяные знаки только в определённые секции документа?**  
О: Да. Пройдитесь по `doc.getSections()` и добавьте водяной знак только в нужные секции.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Последнее обновление:** 2026-02-19  
**Тестировано с:** Aspose.Words for Java 24.12 (latest)  
**Автор:** Aspose