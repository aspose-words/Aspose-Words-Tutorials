---
category: general
date: 2026-11-22
description: Узнайте, как добавить форму в Word с помощью Aspose.Words for Java —
  вставить прямоугольник и скрыть его программно.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shape to word
- how to insert shape
- how to hide shape
- hide shape in word
language: ru
lastmod: 2026-11-22
og_description: Добавьте форму в Word с помощью Aspose.Words для Java. В этом руководстве
  показано, как вставить прямоугольник, скрыть форму и сохранить документ.
og_image_alt: Screenshot of Java code that adds and hides a shape in a Word document
og_title: Добавьте форму в Word с помощью Aspose.Words – руководство по Java
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  headline: How to add shape to Word documents with Aspose.Words for Java
  type: TechArticle
- description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  name: How to add shape to Word documents with Aspose.Words for Java
  steps:
  - name: Expected output
    text: '* The file `output.docx` opens without any visible shapes. * If you inspect
      the document with Aspose.Words (e.g., `doc.getChildNodes(NodeType.SHAPE, true).size()`),
      the shape count will be **1**, confirming that the shape exists but is hidden.'
  - name: 1. Creating a shape in a fresh document
    text: 'If you start from scratch, replace the load line with:'
  - name: 2. Positioning the shape precisely
    text: 'By default, `insertShape` places the shape at the current cursor location.
      To position it absolutely:'
  - name: 3. Controlling visibility per output format
    text: 'If you need the shape visible in the Word UI but hidden when exporting
      to PDF, use `Shape.setWrapType(WrapType.NONE)` together with `Hidden`:'
  - name: 4. Adding text inside the shape
    text: 'A rectangle can contain a text frame:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: Как добавить фигуру в документы Word с помощью Aspose.Words для Java
url: /ru/java/images-shapes/how-to-add-shape-to-word-documents-with-aspose-words-for-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как добавить форму в документы Word с помощью Aspose.Words для Java

Если вам нужно **добавлять формы в документы Word** программно, Aspose.Words for Java делает это простым. В этом руководстве вы узнаете **как вставлять форму**, управлять её видимостью и **как скрыть форму**, чтобы конечный файл выглядел точно так, как вы ожидаете.

Вы пройдёте через полностью готовый, исполняемый пример, который загружает существующий `.docx`, вставляет прямоугольник, скрывает его и сохраняет результат. Никакие внешние скрипты или ручные шаги не требуются, а руководство охватывает распространённые варианты, такие как создание нового документа с нуля или скрытие формы только при печати.

## Предварительные требования

* Java 17 (или новее) установлен – более ранние версии работают, но последняя LTS обеспечивает лучшую производительность.  
* Maven 3.8+ для управления зависимостями.  
* Действительная лицензия Aspose.Words for Java (бесплатная оценочная версия подходит для обучения).  
* IDE или текстовый редактор по вашему выбору (например, IntelliJ IDEA, VS Code).

## Шаг 1: Добавьте Aspose.Words в ваш Maven‑проект

Добавьте следующую зависимость в ваш `pom.xml`. Это подтянет последнюю стабильную версию (по состоянию на ноябрь 2026).

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

> **Совет:** Используйте тег `<scope>provided</scope>`, если планируете распространять JAR вместе со своей логикой лицензирования.

## Добавление формы в Word – инициализация документа

Первый функциональный шаг – получить объект `Document`. Вы можете либо загрузить существующий файл, либо создать новый.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document (or create a new one)
        Document doc = new Document("input.docx");   // <-- replace with your path
        // If you prefer a blank document, use:
        // Document doc = new Document();
```

*Почему это важно*: Класс `Document` является точкой входа для всех манипуляций с Word. Загрузка существующего файла сохраняет стили, колонтитулы и нижние колонтитулы, тогда как новый документ даёт чистый лист.

## Как вставить форму в документ Word

Далее создайте `DocumentBuilder` для изменения содержимого документа. Builder предоставляет методы для вставки текста, таблиц и **форм**.

```java
        // Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape with a width of 100 points and height of 50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
```

Вызов `insertShape` возвращает объект `Shape`, который можно дополнительно настроить (цвет, граница, текст и т.д.). Размеры задаются в пунктах (1 pt = 1/72 in).

*Почему вы можете захотеть использовать прямоугольник*: Прямоугольники – самый распространённый контейнер для аннотаций, водяных знаков или заполнителей. Вы можете заменить `ShapeType.RECTANGLE` на `ShapeType.ELLIPSE`, `ShapeType.LINE` и т.п., чтобы удовлетворить разные визуальные потребности.

## Как скрыть форму в Word

Иногда требуется, чтобы форма существовала для расчётов макета, но не отображалась в финальном виде. Aspose.Words предоставляет метод `setHidden(true)` для этого.

```java
        // Hide the shape so it does not appear when the document is opened
        rectangle.setHidden(true);
```

Флаг hidden работает так же, как параметр форматирования **Hidden** в Microsoft Word: форма исключается из визуального макета, но всё равно участвует в объектной модели документа. Это полезно для:

* Сохранения метаданных или маркеров, которые ваше приложение считывает позже.  
* Создания заполнителей, которые удаляются непосредственно перед публикацией.  
* Управления видимостью для разных форматов вывода (например, скрыть в HTML, но оставить в PDF).

> **Примечание:** Скрытые формы по умолчанию всё равно экспортируются в PDF. Если нужно исключить их и из PDF, установите `rectangle.getWrapType( ) = WrapType.NONE` и скорректируйте свойство `Hidden` соответствующим образом.

## Шаг 4: Сохраните изменённый документ

Наконец, сохраните изменения в новый файл.

```java
        // Save the document with the hidden rectangle
        doc.save("output.docx");   // <-- replace with your desired output path
    }
}
```

Когда вы откроете `output.docx` в Microsoft Word, прямоугольник будет невидим, но останется частью дерева документа. Вы можете программно проверить его наличие, заново загрузив файл и проверив `Shape.isHidden()`.

### Ожидаемый результат

* Файл `output.docx` открывается без каких‑либо видимых форм.  
* Если вы проанализируете документ с помощью Aspose.Words (например, `doc.getChildNodes(NodeType.SHAPE, true).size()`), количество форм будет **1**, подтверждая, что форма существует, но скрыта.

## Расширенные варианты и крайние случаи

### 1. Создание формы в новом документе

Если вы начинаете с нуля, замените строку загрузки на:

```java
Document doc = new Document();          // creates an empty Word file
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Report Title");        // add a title before the shape
```

### 2. Точное позиционирование формы

По умолчанию `insertShape` размещает форму в текущей позиции курсора. Чтобы позиционировать её абсолютно:

```java
rectangle.setLeft(72);   // 1 inch from the left margin
rectangle.setTop(144);   // 2 inches from the top of the page
rectangle.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangle.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
```

### 3. Управление видимостью в зависимости от формата вывода

Если вам нужна форма, видимая в пользовательском интерфейсе Word, но скрытая при экспорте в PDF, используйте `Shape.setWrapType(WrapType.NONE)` вместе с `Hidden`:

```java
rectangle.setHidden(false);                 // visible in Word
rectangle.getParagraph().getParagraphFormat()
        .setPageBreakBefore(true);          // ensure it stays on its own line
// When converting to PDF, hide it programmatically:
if (exportingToPdf) {
    rectangle.setHidden(true);
}
```

### 4. Добавление текста внутрь формы

Прямоугольник может содержать текстовый фрейм:

```java
Shape textBox = builder.insertShape(ShapeType.TEXT_BOX, 200, 50);
textBox.getTextBox().setInternalMarginLeft(5);
textBox.getTextBox().setInternalMarginTop(5);
builder.moveTo(textBox.getFirstParagraph());
builder.write("Confidential");
```

Затем вы можете скрыть текстовое поле тем же вызовом `setHidden(true)`.

## Распространённые ошибки и как их избежать

| Симптом | Причина | Решение |
|---------|---------|---------|
| Форма отображается даже после `setHidden(true)` | Документ был сохранён до установки флага hidden. | Убедитесь, что вызываете `setHidden(true)` **до** `doc.save()`. |
| Размер формы выглядит искажённым | Путаница между пунктами и пикселями на экранах с высоким DPI. | Используйте пункты (72 pt = 1 in) для согласованного размера на всех платформах. |
| Скрытая форма всё равно печатается | Некоторые принтеры игнорируют флаг hidden. | Установите `Shape.setWrapType(WrapType.NONE)` и также очистите `Shape.getParagraph().getParagraphFormat().setPageBreakBefore(false)`. |

## Заключение

Теперь вы знаете, как **добавлять формы в документы Word** с помощью Aspose.Words for Java, **как вставлять форму** и **как скрывать форму**, чтобы она оставалась невидимой для конечных пользователей, но всё равно была частью структуры документа. Полный пример выше загружает файл, вставляет прямоугольник, скрывает его и сохраняет результат, охватывая как типичные сценарии использования, так и несколько крайних случаев.

Отсюда вы можете изучать связанные темы, такие как **как вставлять форму** с пользовательскими цветами заливки, **как скрывать форму в Word** для условной печати, или автоматизацию массовой обработки документов с Aspose.Words. Экспериментируйте с различными значениями `ShapeType`, вариантами позиционирования и флагами видимости, чтобы подобрать оптимальный процесс для вашего рабочего потока.

Приятного кодинга и наслаждайтесь гибкостью, которую программное управление Word приносит в ваши Java‑приложения!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в собственных проектах.

- [Создать документ Word программно, добавить и скрыть форму в Java с помощью Aspose.Words](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [Как скрыть форму в документе Word с помощью Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Создать пустой документ .docx Word и добавить скрытую прямоугольную форму с Aspose.Words](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}