---
category: general
date: 2026-02-15
description: Создайте прямоугольную форму в документе Word с помощью Java. Узнайте,
  как добавить тень к форме, сохранить документ Word и добавить прямоугольную форму
  с помощью Aspose.Words.
draft: false
keywords:
- create rectangle shape
- save word document
- how to shadow shape
- add shape shadow
- add rectangle shape
language: ru
og_description: Создайте прямоугольную форму в файле Word с помощью Java. Это руководство
  показывает, как добавить тень к форме, сохранить документ Word и пошагово добавить
  прямоугольную форму.
og_title: Создать прямоугольную форму – учебник Java Aspose.Words
tags:
- Aspose.Words
- Java
- Document Automation
title: Создание прямоугольной формы в Word с помощью Java – Полное руководство
url: /ru/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

/products/products-backtop-button >}}

Now translate.

Make sure to preserve markdown formatting, code block placeholders unchanged.

Let's produce final Russian translation.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание прямоугольной формы в Word с помощью Java – Полное руководство

Когда‑нибудь вам нужно было **создать прямоугольную форму** в файле Word, но вы не знали, с чего начать? Вы не одиноки — многие разработчики сталкиваются с этой задачей при автоматизации отчетов или счетов. Хорошая новость: с Aspose.Words for Java вы можете быстро создать прямоугольник, добавить к нему красивую тень и сохранить документ Word всего в нескольких строках кода.

В этом руководстве мы пройдем все шаги: от инициализации пустого документа до настройки тени и окончательного сохранения файла. К концу вы узнаете, **как добавить тень к форме**, как **добавить тень к форме**, и как **добавить прямоугольную форму** в любой генерируемый документ Word. Никакой внешней документации не требуется — только чистый, исполняемый код.

## Prerequisites

- Java 8 или новее (API также работает с Java 11+).  
- Библиотека Aspose.Words for Java (версия 23.9 или новее).  
- IDE, например IntelliJ IDEA или Eclipse — подойдёт любой.  
- Базовое знакомство с синтаксисом Java.

> **Pro tip:** Если вы используете Maven, добавьте зависимость Aspose.Words в ваш `pom.xml` и позвольте IDE выполнить остальное.

---

## Step 1: Initialize a New Document – How to **create rectangle shape**  

Первым делом нужен чистый холст. В Aspose.Words такой холст представляет объект `Document`.

```java
import com.aspose.words.*;

public class ShadowShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

Класс `Document` представляет весь файл .docx. Думайте о нем как о блокноте, в который позже вы **добавите прямоугольную форму** и её тень.

## Step 2: Build the Rectangle – **Add rectangle shape**  

Теперь мы действительно создаём прямоугольник. Установим его размер, расположение и цвет заливки.

```java
        // Step 2: Create a rectangle shape and set its size and layout
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);
        rectangleShape.setFillColor(java.awt.Color.LIGHT_GRAY);
```

Почему обертка `INLINE`? Потому что мы хотим, чтобы форма вела себя как абзац — идеально для простых отчетов. При необходимости можно изменить её на `TOPBOTTOM`, если позже потребуется обтекание текста вокруг формы.

## Step 3: Apply a Shadow – **How to shadow shape**  

Плоский прямоугольник выглядит несколько скучно. Добавление тени придаёт глубину и делает документ более профессиональным. Здесь мы отвечаем на вопрос «**как добавить тень к форме**» на практике.

```java
        // Step 3: Configure the shape's shadow appearance
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.DARK_GRAY);
        rectangleShape.getShadowFormat().setBlurRadius(5.0);
        rectangleShape.getShadowFormat().setOffsetX(4.0);
        rectangleShape.getShadowFormat().setOffsetY(4.0);
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

Каждое свойство делает что‑то конкретное:

- `setVisible(true)` включает тень.  
- `setColor` выбирает темно‑серый цвет для мягкого эффекта.  
- `setBlurRadius` управляет мягкостью краёв.  
- `setOffsetX/Y` смещает тень вправо и вниз, имитируя источник света.  
- `setTransparency` делает тень слегка полупрозрачной, чтобы форма оставалась в центре внимания.

> **Note:** Если понадобится цветная тень, просто передайте другой `java.awt.Color` в `setColor`.

## Step 4: Insert the Shape into the Document  

Когда прямоугольник и его тень готовы, мы вставляем их в первый раздел документа.

```java
        // Step 4: Add the shape to the first section of the document
        document.getFirstSection().getBody().appendChild(rectangleShape);
```

Добавление в тело документа размещает форму там, где бы находился новый абзац. Если нужен прямоугольник в определённом месте, можно использовать `insertBefore` или работать с коллекцией `Paragraph`.

## Step 5: **Save Word document** – Persist Your Work  

Последний шаг — записать файл на диск. Это момент, когда вы действительно **сохраняете документ Word**.

```java
        // Step 5: Save the document with the shadowed shape
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Замените `YOUR_DIRECTORY` на абсолютный или относительный путь на вашем компьютере. После выполнения программы откройте `ShadowShape.docx` в Microsoft Word — вы увидите светло‑серый прямоугольник с мягкой тёмной тенью.

![Диаграмма, показывающая прямоугольную форму с тенью, созданную с помощью Aspose.Words](https://example.com/rectangle-shadow.png "создание прямоугольной формы с тенью")

---

## Common Questions & Edge Cases  

### Что делать, если нужно несколько прямоугольников?  

Просто повторите **Step 2** и **Step 3** в цикле, меняя `setWidth`, `setHeight` или `setFillColor` на каждой итерации. Не забудьте дать каждой форме уникальное имя переменной или хранить их в списке.

### Можно ли экспортировать в PDF вместо DOCX?  

Конечно. После добавления формы вызовите `document.save("output.pdf")`. Aspose.Words выполнит конвертацию, сохранив тень.

### Как работать со старыми версиями Word?  

Используйте перегрузку `document.save("file.doc", SaveFormat.DOC)`. API автоматически понижает версии, но имейте в виду, что некоторые стили тени могут выглядеть немного иначе в старых форматах.

### Как изменить направление тени?  

Изменяйте `setOffsetX` и `setOffsetY`. Положительный X смещает тень вправо, отрицательный — влево. Положительный Y смещает вниз, отрицательный — вверх. Поэкспериментируйте с этими значениями, чтобы имитировать источник света под любым углом.

---

## Tips for Working with Shapes  

- **Group shapes**: если нужен ярлык рядом с прямоугольником, создайте `GroupShape` и добавьте в него и прямоугольник, и `TextBox`.  
- **Z‑order matters**: используйте `shape.moveToFront()` или `shape.moveToBack()`, чтобы контролировать, какая форма будет сверху.  
- **Performance**: добавление сотен форм может замедлить процесс. Сгруппируйте их в один раздел, а затем один раз вызовите `document.updatePageLayout()` в конце.

---

## Recap  

Мы рассмотрели, как **создать прямоугольную форму** в документе Word с помощью Java, как **добавить тень к форме**, и как **сохранить документ Word** с полученным результатом. Полный, исполняемый код находится в приведённых выше фрагментах, а теперь вы понимаете «почему» каждого свойства — так что можете менять цвета, размытие и смещения под любой дизайн.

Готовы к следующему вызову? Попробуйте объединить прямоугольник с диаграммой или экспортировать файл в PDF и посмотреть, как отобразится тень. Вы также можете исследовать **добавление прямоугольной формы** внутри таблиц для стильных макетов отчетов.

Счастливого кодинга, и пусть ваши документы всегда выглядят так же чётко, как ваш код!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}