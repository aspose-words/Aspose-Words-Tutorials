---
category: general
date: 2026-07-26
description: Вставьте прямоугольную форму в Java с помощью Aspose.Words. Узнайте,
  как задать размер формы, позицию формы и как группировать формы в файле DOCX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- set shape size
- position shape
- how to group shapes
- how to add rectangle
language: ru
lastmod: 2026-07-26
og_description: Вставьте прямоугольную форму в Java, чтобы создавать насыщенные графические
  элементы DOCX. Следуйте этому пошаговому руководству, чтобы легко задавать размер
  формы, позицию и группировать формы.
og_image_alt: Screenshot showing a rectangle shape inserted and grouped in a Java‑generated
  Word document
og_title: Вставка прямоугольной формы в Java — мастерство группировки и позиционирования
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert rectangle shape in Java using Aspose.Words. Learn how to set
    shape size, position shape, and how to group shapes in a DOCX file.
  headline: Insert Rectangle Shape in Java – Group and Position Shapes
  type: TechArticle
tags:
- Aspose.Words
- Java
- Shapes
- DOCX
title: Вставка прямоугольной формы в Java — группировка и позиционирование форм
url: /ru/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Вставка прямоугольной фигуры в Java – Группировка и позиционирование фигур

Когда‑то вам **нужно было вставить прямоугольную фигуру** в документ Word, пиша код на Java? Вы не одиноки — разработчики, создающие отчёты, счета‑фактуры или пользовательские шаблоны, постоянно сталкиваются с этой задачей. Хорошая новость: несколько строк кода Aspose.Words for Java позволяют **вставить прямоугольную фигуру**, **задать размер фигуры**, **позиционировать её**, а также **группировать фигуры**, чтобы они перемещались как единое целое.

В этом руководстве мы пройдём весь процесс от создания пустого документа до сохранения `.docx`, содержащего два аккуратно сгруппированных прямоугольника. К концу вы узнаете, **как добавить прямоугольники**, управлять их размерами, размещать их точно там, где нужно, и объединять в переиспользуемую группу. Никаких внешних библиотек, кроме Aspose.Words, не требуется, а код работает с Java 8 и выше.

## Предварительные требования

- Java 8 или новее (я использую JDK 17, но подойдёт любой JDK, поддерживающий Maven)
- Aspose.Words for Java 23.9 или новее — добавьте зависимость в `pom.xml` или скачайте JAR
- Базовое понимание синтаксиса Java (если умеете писать метод `main`, вам достаточно)
- Любая IDE или текстовый редактор (IntelliJ IDEA, Eclipse, VS Code …)

> **Pro tip:** Если вы используете Maven, зависимость выглядит так:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Теперь, когда подготовка завершена, приступим к коду.

## Вставка прямоугольной фигуры и задание её размера

Первым делом создаём новый `Document` и `DocumentBuilder`. Builder — это ваш «перо», которым рисуются фигуры на странице. Ниже мы **вставляем прямоугольную фигуру** и сразу **задаём её размер** 100 × 80 пунктов.

```java
import com.aspose.words.*;

public class GroupedRectanglesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder to add content
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape(400, 200);
        // The group itself is 400×200 points – adjust as needed

        // ---------- First rectangle ----------
        // Insert rectangle shape
        Shape rectangle1 = new Shape(document, ShapeType.RECTANGLE);
        // Set shape size
        rectangle1.setWidth(100);
        rectangle1.setHeight(80);
        // Position shape inside the group
        rectangle1.setLeft(20);   // 20 points from the left edge of the group
        rectangle1.setTop(30);    // 30 points from the top edge of the group
        // Add the rectangle to the group
        group.appendChild(rectangle1);
```

Обратите внимание, что вызовы `setWidth`/`setHeight` **задают размер фигуры** в пунктах (1 pt ≈ 1/72 дюйма). Можно также использовать `setSize`, если предпочитаете один метод, но явные вызовы делают намерение кристально ясным.

## Позиционирование фигуры на странице

После создания первого прямоугольника нам нужно **позиционировать** второй так, чтобы он не перекрывал первый. Позиционирование работает тем же способом: задаём свойства `Left` и `Top` относительно начала группы.

```java
        // ---------- Second rectangle ----------
        Shape rectangle2 = new Shape(document, ShapeType.RECTANGLE);
        rectangle2.setWidth(120);
        rectangle2.setHeight(60);
        // Position this rectangle a bit farther to the right and lower down
        rectangle2.setLeft(150);
        rectangle2.setTop(50);
        group.appendChild(rectangle2);
```

Если задаётесь вопросом, почему мы используем `setLeft`, а не `setX`, то это потому, что Aspose.Words следует классической системе координат Windows GDI — `Left` — горизонтальное смещение, `Top` — вертикальное. Изменяя эти значения, вы точно настраиваете расположение без необходимости работать с таблицами или абзацами.

## Как группировать фигуры

Вы можете спросить: «Зачем вообще нужна группа?» Группировка имеет смысл, когда нужно перемещать фигуры вместе, вращать их как единое целое или применять общий стиль. В приведённом выше фрагменте кода мы уже создали `GroupShape` через `builder.insertGroupShape`. Этот объект по сути является контейнером — представьте его как папку, в которой хранятся другие файлы фигур.

> **Почему это важно:** Если позже вы решите добавить подпись или повернуть всю схему, достаточно изменить только группу, а не каждый прямоугольник по отдельности.

## Как добавить прямоугольник в группу

Сам процесс **добавления прямоугольника** в группу сводится к вызову `group.appendChild(rectangle)`. Под капотом Aspose.Words обновляет внутреннюю коллекцию группы и автоматически пересчитывает ограничивающий прямоугольник, чтобы группа по‑прежнему помещалась в заданные ширину и высоту.

```java
        // At this point the group already contains both rectangles.
        // You can also set the group’s border or fill if you like.
        group.getShapeStyle().setLineColor(Color.BLACK);
        group.getShapeStyle().setFillColor(Color.LIGHTGRAY);
```

Можно поэкспериментировать с другими `ShapeType` — `ShapeType.ELLIPSE`, `ShapeType.TRIANGLE` и т.д. — и тот же шаблон `appendChild` будет работать.

## Сохранение документа

Наконец, сохраняем документ на диск. Путь может быть абсолютным или относительным; просто убедитесь, что папка существует.

```java
        // Step 5: Save the document containing the grouped shapes
        String outPath = "output/GroupShape.docx";
        document.save(outPath);
        System.out.println("Document saved to: " + outPath);
    }
}
```

Открыв `GroupShape.docx` в Microsoft Word, вы увидите два прямоугольника рядом, оба заперты внутри светло‑серой рамки. Выделив серую рамку, вы одновременно выделите оба прямоугольника — доказательство того, что **группировка фигур** действительно работает.

![Grouped rectangles in a Word document](placeholder-image.png){: .center-image alt="пример вставки прямоугольной фигуры, показывающий два прямоугольника, сгруппированных в DOCX‑файле, сгенерированном Java"}

*Текст alt изображения (SEO):* **пример вставки прямоугольной фигуры, показывающий два прямоугольника, сгруппированных в DOCX‑файле, сгенерированном Java**.

## Ожидаемый результат

- Файл `GroupShape.docx` в папке `output`.
- Внутри документа: группа 400 × 200 pt, содержащая два прямоугольника (100 × 80 pt и 120 × 60 pt), расположенных соответственно в точках (20, 30) и (150, 50).
- У группы тонкая чёрная граница и светло‑серый залив, визуально подчёркивающий группировку.

Откройте файл и попробуйте перетащить серую рамку — оба прямоугольника должны переместиться вместе. Если этого не происходит, проверьте, что вы вызвали `group.appendChild` для каждой фигуры.

## Распространённые ошибки и граничные случаи

| Проблема | Почему происходит | Решение |
|----------|-------------------|---------|
| **Прямоугольники выходят за пределы страницы** | Значения `Left`/`Top` превышают размеры группы | Увеличьте размер группы (`insertGroupShape(width, height)`) или уменьшите смещения |
| **Группа исчезает после сохранения** | У группы `Width`/`Height` равны 0 | Укажите ненулевые размеры при вызове `insertGroupShape` |
| **Цвета фигур отображаются неверно** | По умолчанию заливка прозрачна; Word может отобразить её как белую | Явно задайте `setFillColor` или используйте `ShapeStyle` |
| **Исключение `ArgumentOutOfRangeException`** | Используются отрицательные координаты | Держите `Left` и `Top` неотрицательными |

Устранение этих проблем на ранних этапах избавит вас от головной боли «почему моя фигура исчезла?», с которой сталкиваются многие новички.

## Итоги и дальнейшие шаги

Мы прошли полный цикл **вставки прямоугольной фигуры** в Java: создание документа, **задание размера фигуры**, **позиционирование**, **группировка фигур** и **добавление прямоугольника** в эту группу. Полный, готовый к запуску пример находится в кодовом блоке выше, и вы можете сразу вставить его в Maven‑проект, чтобы увидеть результат.

Что дальше? Попробуйте поэкспериментировать с:

- Добавлением текста внутрь каждого прямоугольника через

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс содержит полностью рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}