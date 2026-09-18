---
category: general
date: 2026-09-18
description: Создайте пустой документ и вставьте фигуры в Word с помощью Aspose.Words —
  узнайте, как добавить треугольник и многое другое.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- add shapes to word
- how to insert triangle
- add triangle shape
- create word document
language: ru
lastmod: 2026-09-18
og_description: Создайте пустой документ в Word с помощью Aspose.Words и узнайте,
  как вставить треугольник, сгруппировать фигуры и другие графические элементы. Следуйте
  этому полному руководству.
og_image_alt: Screenshot of a Word document showing a grouped shape with a triangle
  inside
og_title: Создайте пустой документ и добавьте фигуры в Word — пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document and insert shapes to Word with Aspose.Words –
    learn how to add a triangle shape and more.
  headline: How to create blank document and add shapes to Word
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Как создать пустой документ и добавить фигуры в Word
url: /ru/java/images-shapes/how-to-create-blank-document-and-add-shapes-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать пустой документ и добавить фигуры в Word

Если вам нужно **создать пустой документ** и затем обогатить его графикой, это руководство покажет вам, как именно. Мы пройдем процесс создания файла Word с нуля и **добавить фигуры в Word**, включая **как вставить треугольник** форму, используя Aspose.Words for Java.

Вы завершите руководство готовым к использованию файлом *.docx*, содержащим сгруппированную фигуру с треугольником. Шаги охватывают всё от настройки проекта до сохранения окончательного **create word document**. Ниже внешних инструментов, кроме Aspose.Words, не требуется.

## Требования

* Java 17 или новее установлен  
* Maven или Gradle для управления зависимостями  
* Лицензия Aspose.Words for Java (бесплатная оценочная версия подходит для этой демонстрации)  

Если вы предпочитаете другую систему сборки, скорректируйте синтаксис зависимостей соответственно. Код работает на любой платформе, поддерживающей Java.

## Создать пустой документ с помощью Aspose.Words

Первая операция — **создать пустой документ** в памяти. Aspose.Words предоставляет класс `Document`, представляющий файл Word без содержимого.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank document
```

`new Document()` конструктор создает пустую структуру *.docx*, которую вы позже можете заполнять абзацами, таблицами или графикой. Поскольку документ пуст, вы полностью контролируете каждый добавляемый элемент.

## Добавить фигуры в Word – вставка групповой фигуры

Групповая фигура позволяет рассматривать несколько графических элементов как единое целое. Это удобно, когда нужно перемещать или изменять размер нескольких фигур одновременно.

```java
        // Step 2: Initialize a DocumentBuilder to construct content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a group shape of size 300 × 300 points
        GroupShape group = builder.insertGroupShape(300.0, 300.0);
```

`DocumentBuilder` — основной API для добавления содержимого. Вызов `insertGroupShape` создаёт контейнер размером 300 × 300 пунктов (примерно 4 × 4 дюйма). После этого вызова курсор находится *внутри* группы, готовый к добавлению дополнительных фигур.

### Зачем использовать групповую фигуру?

Группировка сохраняет выравнивание связанных графических элементов и упрощает применение единообразного форматирования. Если позже вы решите переместить треугольник, вся группа переместится вместе, сохраняя макет.

## Как вставить треугольник внутри группы

Теперь мы рассматриваем **how to insert triangle** форму. Треугольник является одним из встроенных значений `ShapeType`.

```java
        // Step 4: Move the cursor into the group's first paragraph
        builder.moveTo(group.getFirstParagraph());

        // Step 5: Insert a triangle shape of size 60 × 60 points inside the group
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);
```

Вызов `moveTo` гарантирует, что точка вставки builder находится в первом абзаце группы. Затем `insertShape` добавляет треугольник размером 60 × 60 пунктов. Поскольку курсор находится внутри группы, треугольник становится дочерним элементом групповой фигуры.

**Подсказки по добавлению треугольника**:

* Размер измеряется в пунктах; 72 пункта равны одному дюйму. Настройте размеры под ваш макет.  
* Если нужна другая ориентация, используйте `builder.getCurrentParagraph().getParagraphFormat().setAlignment()` для выравнивания фигуры внутри группы.  
* Треугольник наследует заливку и стили линий группы, если вы не переопределите их с помощью `shape.getFillColor()` или `shape.getStrokeColor()`.

## Сохранить документ – create word document

После создания графики вы сохраняете файл. Этот шаг завершает операцию **create word document**.

```java
        // Step 6: Save the document with the extended group shape
        doc.save("ExtendedGroup.docx");               // create word document
    }
}
```

`doc.save` записывает представление в памяти на диск в виде стандартного документа Word. Вы можете открыть `ExtendedGroup.docx` в Microsoft Word, LibreOffice или любом просмотрщике, поддерживающем формат OOXML. Файл отобразит групповую фигуру, содержащую треугольник, точно как построено кодом.

## Полный исполняемый пример

Собрав все части вместе, представляем полный пример программы, который вы можете скопировать, скомпилировать и запустить:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Prepare a builder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a group shape (300 × 300 points)
        GroupShape group = builder.insertGroupShape(300.0, 300.0);

        // 4. Position the cursor inside the group
        builder.moveTo(group.getFirstParagraph());

        // 5. Insert a triangle shape (60 × 60 points)
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);

        // 6. Save the file – this creates the final Word document
        doc.save("ExtendedGroup.docx");
    }
}
```

### Ожидаемый результат

При открытии `ExtendedGroup.docx` вы увидите одну групповую фигуру, занимающую центр страницы. Внутри этой группы небольший треугольник появляется в позиции по умолчанию. Треугольник можно выбрать и переместить вместе с группой, подтверждая, что **add shapes to word** сработало как задумано.

## Часто задаваемые вопросы и особые случаи

| Вопрос | Ответ |
|----------|--------|
| *Могу ли я добавить более одной фигуры внутри группы?* | Да. После вставки треугольника оставьте курсор внутри группы и вызовите `builder.insertShape` снова с другим `ShapeType`. |
| *Что если мне нужен красный треугольник?* | Получите объект `Shape`, возвращаемый `insertShape`, и вызовите `shape.getFillColor().setColor(Color.RED)`. |
| *Работает ли это со старыми файлами .doc?* | Aspose.Words сохраняет в указанном вами формате. Используйте `doc.save("file.doc", SaveFormat.DOC)`, чтобы создать документ Word старого формата. |
| *Как изменить границу группы?* | Используйте `group.getStrokeColor().setColor(Color.BLUE)` и `group.setLineWeight(2.0)`, чтобы настроить контур. |
| *Можно ли повернуть треугольник?* | Вызовите `shape.getRotation()`, чтобы задать угол в градусах. |

## Профессиональные советы

* **Повторное использование builder** – создание нового `DocumentBuilder` для каждой фигуры добавляет накладные расходы. Держите один builder на документ.  
* **Преобразование единиц** – если вы работаете с миллиметрами, преобразуйте их в пункты (`points = mm * 2.83465`).  
* **Производительность** – для больших документов вызывайте `doc.updatePageLayout()` только один раз после добавления всех фигур.  

## Заключение

Теперь вы знаете, как **create blank document**, **add shapes to Word**, и конкретно **how to insert triangle** форму с помощью Aspose.Words for Java. Полный пример демонстрирует весь процесс от пустого файла до сохранённого **create word document**, содержащего сгруппированный треугольник.

Отсюда вы можете исследовать дополнительные значения `ShapeType`, применять пользовательское стилизование или комбинировать несколько групп для создания сложных диаграмм. Экспериментируйте с различными размерами, цветами и позициями, чтобы освоить автоматизацию Word в Java.

--- 

*Готовы автоматизировать ваш следующий отчёт? Склонируйте пример, измените размеры и интегрируйте код в своё приложение уже сегодня.*

## Что вам стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Создать групповую фигуру в документе Word с помощью Aspose.Words для .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Создать пустой документ Word с фигурой прямоугольника с тенью – пошаговое руководство](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Создать прямоугольную фигуру в Word с Aspose.Words – пошаговое руководство](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}