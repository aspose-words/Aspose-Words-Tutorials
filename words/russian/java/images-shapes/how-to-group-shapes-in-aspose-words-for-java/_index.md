---
category: general
date: 2026-10-20
description: Как группировать фигуры в Aspose.Words для Java — узнайте, как вставить
  прямоугольную форму, сгруппировать их и сохранить документ в одном руководстве.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- how to insert rectangle
language: ru
lastmod: 2026-10-20
og_description: Как группировать фигуры в Aspose.Words для Java. Этот учебник показывает,
  как вставить прямоугольную фигуру, сгруппировать их и экспортировать результат.
og_image_alt: Screenshot of a Word document showing two grouped rectangle shapes created
  with Aspose.Words for Java
og_title: Как сгруппировать фигуры в Aspose.Words для Java – пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: How to group shapes in Aspose.Words for Java – learn how to insert
    rectangle shape, group them, and save the document in a single guide.
  headline: How to group shapes in Aspose.Words for Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- shape manipulation
title: Как сгруппировать фигуры в Aspose.Words для Java
url: /ru/java/images-shapes/how-to-group-shapes-in-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как группировать фигуры в Aspose.Words for Java

Если вам нужно **как группировать фигуры** в документе Word с использованием Aspose.Words for Java, это руководство покажет вам полный рабочий процесс. Вы узнаете, как **вставить прямоугольную фигуру**, добавить второй прямоугольник, сгруппировать две фигуры и, наконец, сохранить файл — всё с понятным, исполняемым кодом.

Группировка фигур полезна, когда нужно перемещать, вращать или стилизовать несколько рисунков как единый объект. Независимо от того, создаёте ли вы шаблон отчёта, диаграмму или пользовательский флаер, освоение группировки фигур экономит время и сохраняет согласованность макета.

В этом руководстве вы:

* Создадите новый `Document` и `DocumentBuilder`.
* **Как вставить прямоугольник** фигуры с точными размерами.
* Сгруппируете прямоугольники в `GroupShape`.
* Сохраните документ и проверите результат.

> **Prerequisite** – Вы должны добавить Aspose.Words for Java (v23.12 или новее) в ваш проект. Пользователи Maven могут включить зависимость, показанную ниже.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

---

## Что понадобится

| Item | Reason |
|------|--------|
| Java 17+ | Современные возможности языка и лучшая производительность |
| Aspose.Words for Java | Предоставляет API `DocumentBuilder`, `Shape` и `GroupShape` |
| IDE (IntelliJ IDEA, Eclipse, VS Code и др.) | Для компиляции и запуска примера |
| Права записи в папку | Документ будет сохранён на диск |

---

## Как вставить прямоугольную фигуру

Первый шаг — создать `Document` и `DocumentBuilder`. Builder предоставляет методы, такие как `insertShape`, для размещения графических объектов.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle (100 × 50 points).
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Optional: give the rectangle a fill color for visibility.
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Step 3: Insert the second rectangle (80 × 40 points).
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // The two rectangles are currently independent objects.
        // Below we will group them together.
```

> **Why this matters** – Использование `insertShape` — это стандартный способ **как вставить прямоугольник** объектов в Aspose.Words. Он автоматически добавляет фигуру в текущий абзац документа, поэтому вам не нужно управлять низкоуровневым OpenXML.

---

## Регулировка позиций прямоугольников (необязательно)

Если второму прямоугольнику требуется пользовательское расположение относительно первого, вы можете изменить его свойства `left` и `top`. Этот шаг необязателен, но часто нужен для точного размещения диаграммы.

```java
        // Optional: reposition the second rectangle 20 points to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        // Optional: align the top edges.
        rectangle2.setTop(rectangle1.getTop());
```

> **Pro tip:** Все измерения указаны в пунктах (1 pt ≈ 1/72 in). Используйте `convertPointsToPixels`, если нужны значения в пикселях для расчётов в UI.

---

## Как группировать фигуры

Теперь, когда прямоугольники созданы, их можно разместить внутри `GroupShape`. Группировка заставляет две фигуры вести себя как один объект — перемещение, вращение или форматирование группы будет влиять на обе фигуры.

```java
        // Step 4: Insert an empty GroupShape.
        GroupShape group = builder.insertGroupShape();

        // Step 5: Add the rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Optional: set a border for the whole group.
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);
```

> **Why grouping works** – `GroupShape` наследуется от `Shape`, поэтому группу можно использовать так же, как любой другой графический объект. При вызове `appendChild` фигуры удаляются из своего исходного места и становятся дочерними элементами группы.

---

## Сохранение документа, содержащего сгруппированные фигуры

Наконец, запишите документ на диск. Файл будет содержать один `GroupShape` с двумя вложенными прямоугольниками.

```java
        // Step 6: Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Ожидаемый результат

Откройте `GroupShape.docx` в Microsoft Word:

* Вы увидите два прямоугольника (синий и зелёный), расположенных рядом.
* Выбор любого из прямоугольников выделяет всю группу — перетаскивание перемещает их вместе.
* У группы есть тонкая красная граница, подтверждающая применение свойств `GroupShape`.

Если щёлкнуть правой кнопкой мыши по группе и выбрать **Group → Ungroup**, прямоугольники вернутся к независимым фигурам, демонстрируя обратимость операции группировки.

---

## Общие варианты и граничные случаи

| Situation | How to handle it |
|-----------|------------------|
| **More than two shapes** | Insert each shape, then append all to the same `GroupShape`. |
| **Different shape types** (e.g., ellipse, picture) | Use `builder.insertShape(ShapeType.ELLIPSE, …)` or `builder.insertImage(...)` before appending. |
| **Scaling the group** | Call `group.setWidth(newWidth)` or `group.setHeight(newHeight)`; children scale proportionally. |
| **Rotating the group** | `group.setRotationAngle(45);` rotates the whole collection around its center. |
| **Preserving original positions** | Store each shape’s `left`/`top` before grouping and restore after ungrouping if needed. |

---

## Полный, исполняемый пример

Ниже приведён полный Java‑класс, который можно скопировать и вставить в вашу IDE. Он включает все импорты, обработку ошибок и комментарии для ясности.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert the first rectangle (100 × 50 points) and give it a blue fill.
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Insert the second rectangle (80 × 40 points) with a green fill.
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // Optional positioning – move the second rectangle 20 pt to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        rectangle2.setTop(rectangle1.getTop());

        // Insert an empty group shape.
        GroupShape group = builder.insertGroupShape();

        // Add both rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Style the group (red border, 1.5 pt weight).
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);

        // Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

Запустите программу, откройте полученный `GroupShape.docx`, и вы увидите сгруппированные прямоугольники точно так, как описано.

---

## Заключение

Теперь вы знаете **как группировать фигуры** в Aspose.Words for Java, от создания документа до вставки прямоугольных фигур, настройки их позиций и окончательной группировки с помощью `GroupShape`. Эта техника позволяет рассматривать несколько рисунков как единый объект, упрощая корректировку макета и обеспечивая визуальную согласованность.

**Следующие шаги**

* Исследуйте **как вставить прямоугольник** фигуры с различными шаблонами заливки или границами.  
* Скомбинируйте **вставить прямоугольную фигуру** с текстовыми полями для создания подписанных диаграмм.  
* Поэкспериментируйте с вращением или масштабированием группы, чтобы создавать более сложные графики.

Не стесняйтесь адаптировать код для других типов фигур, больших групп или сценариев динамической генерации документов. Приятного кодинга!

## Что вам следует изучить дальше?

Следующие руководства охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Вставка прямоугольной фигуры в Java – группировка и позиционирование фигур](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [как вставить групповую фигуру в Java – полное руководство](/words/english/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/)
- [Как установить тень у фигуры в Aspose.Words – полное руководство](/words/english/java/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}