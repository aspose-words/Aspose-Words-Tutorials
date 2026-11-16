---
category: general
date: 2026-11-15
description: Создайте прямоугольную форму в Word с помощью Java и узнайте, как добавлять
  формы в Word, задавать их размеры и эффективно сохранять документ Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add shapes to word
- save word document
- set shape dimensions
- define shape size
language: ru
lastmod: 2026-11-15
og_description: Создайте прямоугольную форму в документе Word с помощью Java. Узнайте,
  как добавлять формы в Word, задавать их размеры и сохранять документ Word за считанные
  минуты.
og_image_alt: Screenshot showing a rectangle shape inside a group shape in a Word
  document
og_title: Создайте прямоугольную форму в Word с помощью Java – пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  headline: Create rectangle shape in a Word document using Java
  type: TechArticle
- description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  name: Create rectangle shape in a Word document using Java
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well). * Aspose.Words
      for Java 23.10 or newer – you can obtain it from Maven Central. * A basic understanding
      of Java syntax and object‑oriented concepts.'
  - name: Expected output
    text: '* A Word file named `RectangleShapeDemo.docx`. * Inside the first paragraph,
      a group shape containing a 100 pt × 50 pt rectangle. * No text is added, so
      the rectangle appears on a blank page.'
  - name: What’s next?
    text: '* Explore **add shapes to Word** by inserting circles, arrows, or text
      boxes. * Combine multiple shapes into a single `GroupShape` and apply transformations
      (rotate, flip). * Generate reports that embed charts as shapes, then **save
      Word document** as PDF for sharing.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Создать прямоугольную форму в документе Word с помощью Java
url: /ru/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание прямоугольной фигуры в документе Word с помощью Java

Если вам нужно **create rectangle shape** внутри файла Word, это руководство покажет, как сделать это с помощью Java. Вы увидите, как **add shapes to Word**, управлять **set shape dimensions** и, наконец, **save Word document** не выходя из вашей IDE.

В последующих разделах вы получите полностью готовый пример, объяснение каждой строки и советы по распространённым подводным камням, таким как проблемы с размерами и совместимостью документа. Внешние ссылки не требуются — только библиотека Aspose.Words for Java.

## Что вы узнаете

* Как инициализировать `Document` и `DocumentBuilder`.
* Как вставить **group shape** и разместить внутри него прямоугольник.
* Как **define shape size** с помощью `setWidth` и `setHeight`.
* Как **save Word document** в формате `.docx`.
* Обработка граничных случаев для разных размеров страниц и настроек DPI.

### Предварительные требования

* Java 17 или новее (код также компилируется с Java 8).
* Aspose.Words for Java 23.10 или новее — вы можете получить её из Maven Central.
* Базовое понимание синтаксиса Java и объектно‑ориентированных концепций.

> **Pro tip:** Если вы планируете добавить позже больше фигур (например, круги или текстовые поля), держите их внутри того же `GroupShape`. Это значительно упрощает перемещение, вращение или форматирование всей коллекции.

## Шаг 1: Инициализация документа и builder'а

Первый шаг — создать пустой файл Word и `DocumentBuilder`, позволяющий записывать содержимое.  

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Почему это важно:* `Document` представляет весь файл, а `DocumentBuilder` предоставляет высокоуровневые методы для вставки текста, таблиц и **shapes**. Без builder'а вам пришлось бы вручную управлять низкоуровневыми узлами.

## Шаг 2: Вставка group shape для удержания нескольких фигур

**group shape** работает как контейнер; вы можете добавить несколько фигур и позже рассматривать их как один объект (например, перемещать или вращать вместе).

```java
        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();
```

*Зачем использовать group shape?* Если позже вы решите добавить стрелки, круги или подписи вокруг прямоугольника, группа сохранит всё выровненным. Это также упрощает процесс **add shapes to Word**, так как для каждой новой фигуры требуется лишь один вызов `appendChild`.

## Шаг 3: Создание прямоугольной фигуры

Теперь мы создаём настоящий прямоугольник, который будет находиться внутри группы. Конструктору `Shape` нужен владелец `Document` и тип требуемой фигуры.

```java
        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
```

*Почему прямоугольник?* `ShapeType.RECTANGLE` — самый распространённый примитив для выделения разделов, создания заполнителей или рисования простых макетов UI непосредственно в Word.

## Шаг 4: Определение размера прямоугольника

Установка размеров — это то, где **set shape dimensions** становится важным. Вы можете использовать любую единицу измерения, поддерживаемую Aspose.Words; по умолчанию — пункты (1 pt = 1/72 дюйма).

```java
        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

> **Note:** Если вы предпочитаете миллиметры, вызовите `rectangle.setWidth(ConversionUtil.inchesToPoints(1.39));`, где `1.39 in ≈ 35 mm`. Это демонстрирует гибкость **define shape size**.

## Шаг 5: Добавление прямоугольника в group shape

Добавление прямоугольника в ранее созданную группу делает его видимым в документе.

```java
        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);
```

На данном этапе прямоугольник расположен в левом верхнем углу группы. При необходимости точного размещения вы можете позже переместить его с помощью `rectangle.setLeft(...)` и `rectangle.setTop(...)`.

## Шаг 6: (Опционально) Сохранить документ, чтобы увидеть результат

Наконец, запишите документ на диск. Это шаг **save Word document**, который создаёт файл `.docx`, который можно открыть в Microsoft Word, LibreOffice или Google Docs.

```java
        // Step 6: Save the document (optional but recommended for verification)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

Запуск программы создаёт `RectangleShapeDemo.docx`, содержащий один прямоугольник внутри group shape. Открытие файла показывает простой белый прямоугольник — точно того размера, который вы задали.

### Ожидаемый результат

* Файл Word с именем `RectangleShapeDemo.docx`.
* Внутри первого абзаца — group shape, содержащий прямоугольник 100 pt × 50 pt.
* Текст не добавлен, поэтому прямоугольник отображается на пустой странице.

## Распространённые варианты и граничные случаи

| Ситуация | Как адаптировать код |
|-----------|-----------------------|
| **Different page size** (e.g., A4) | Вызовите `document.getFirstSection().getPageSetup().setPaperSize(PaperSize.A4);` перед вставкой фигуры. |
| **Higher DPI for printing** | Умножьте ширину/высоту на нужный DPI‑коэффициент, например `rectangle.setWidth(200 * 2);` для двойного разрешения. |
| **Adding a text label inside the rectangle** | Создайте `Shape` типа `TEXT_BOX`, задайте её `setWidth`/`setHeight`, соответствующие прямоугольнику, затем добавьте её в тот же `GroupShape`. |
| **Rotating the rectangle** | Используйте `rectangle.setRotationAngle(45);` для вращения на 45 градусов по часовой стрелке. |
| **Saving as PDF instead of DOCX** | Замените `document.save("output.docx");` на `document.save("output.pdf");` — тот же API работает для PDF, сохраняет прямоугольник. |

## Советы для надёжной реализации

1. **Reuse the builder** — после вставки group shape вы можете продолжать добавлять абзацы или таблицы без создания нового экземпляра builder'а.
2. **Dispose resources** — хотя сборщик мусора Java обрабатывает большинство объектов, явный вызов `document.close();` (при работе с потоками) предотвращает утечки дескрипторов файлов.
3. **Validate dimensions** — перед вызовом `setWidth`/`setHeight` убедитесь, что значения положительные; отрицательные значения вызывают `IllegalArgumentException`.
4. **Version compatibility** — код работает с Aspose.Words 23.x и новее. Более ранние версии могут требовать `Shape.setSize(width, height)` вместо отдельных сеттеров.

## Полный, исполняемый пример

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();

        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);

        // Optional: set a light gray fill to make it visible in Word
        rectangle.getFillColor() .setRGB(200, 200, 200);

        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);

        // Step 6: Save the document (you can also save as PDF)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

> **Result verification:** Откройте `output/RectangleShapeDemo.docx` в Microsoft Word. Вы должны увидеть прямоугольник указанного размера, центрированный в верхней части первой страницы. Если прямоугольник выглядит слишком маленьким, скорректируйте значения, передаваемые в `setWidth` и `setHeight`.

## Заключение

Теперь вы знаете, как **create rectangle shape** в файле Word с помощью Java, как **add shapes to Word** через `GroupShape`, как **set shape dimensions** и **define shape size**, а также как **save Word document** для дальнейшего распространения. Та же схема работает с другими типами фигур, позволяя программно создавать сложные диаграммы.

### Что дальше?

* Исследуйте **add shapes to Word**, вставляя круги, стрелки или текстовые поля.
* Объедините несколько фигур в один `GroupShape` и примените трансформации (вращение, отражение).
* Создавайте отчёты, встраивая диаграммы как фигуры, а затем **save Word document** в PDF для распространения.

Не стесняйтесь экспериментировать с размерами, цветами и позиционированием, чтобы подобрать их под ваш конкретный сценарий. Приятного кодинга!

## Что вам стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide](/words/english/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/)
- [Create word document java – hide shape and set fill color](/words/english/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}