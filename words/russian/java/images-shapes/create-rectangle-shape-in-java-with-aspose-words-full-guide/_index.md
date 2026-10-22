---
category: general
date: 2026-07-06
description: Создайте прямоугольную форму в Java с помощью Aspose.Words — узнайте,
  как добавить тень к форме, установить её прозрачность и сохранить документ в PDF.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- set shape transparency
- save document as pdf
- how to add shadow
language: ru
og_description: Создайте прямоугольную форму в Java с помощью Aspose.Words. Это руководство
  показывает, как добавить тень к форме, установить её прозрачность и сохранить документ
  в PDF.
og_title: Создание прямоугольной формы в Java – учебник Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Create rectangle shape in Java using Aspose.Words – learn how to add
    shadow to shape, set shape transparency, and save document as PDF.
  headline: Create rectangle shape in Java with Aspose.Words – Full Guide
  type: TechArticle
- description: Create rectangle shape in Java using Aspose.Words – learn how to add
    shadow to shape, set shape transparency, and save document as PDF.
  name: Create rectangle shape in Java with Aspose.Words – Full Guide
  steps:
  - name: 1️⃣ What if I need a larger rectangle?
    text: Just change the width and height parameters in `insertShape`. Remember that
      72 pt = 1 in, so `400.0, 200.0` would give you a 5.5 × 2.8 inch rectangle.
  - name: 2️⃣ Can I use a different color for the shadow?
    text: Absolutely. The `ShadowFormat` class also exposes `setColor(java.awt.Color)`.
      For a subtle gray shadow, try `shadow.setColor(java.awt.Color.DARK_GRAY);`.
  - name: 3️⃣ Does `save document as pdf` work on all platforms?
    text: Yes. Aspose.Words for Java is platform‑agnostic; the same code runs on Windows,
      macOS, and Linux as long as you have a compatible JRE.
  - name: 4️⃣ How do I remove the shadow later?
    text: Call `rect.getShadowFormat().clear();` or set the `Visible` property to
      `false` (`shadow.setVisible(false);`).
  - name: 5️⃣ What about DPI and image quality?
    text: When saving to PDF, Aspose automatically uses 300 DPI for vector graphics
      like shapes, so you get crisp results regardless of zoom level.
  type: HowTo
tags:
- Aspose.Words
- Java
- PDF
- Shape
- Shadow
title: Создание прямоугольной фигуры в Java с Aspose.Words – полное руководство
url: /ru/java/images-shapes/create-rectangle-shape-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание прямоугольной фигуры в Java с Aspose.Words – Полное руководство

Задумывались ли вы когда‑нибудь, как **создать прямоугольную фигуру** в Java без борьбы с низкоуровневыми API рисования? Вы не одиноки. Многие разработчики нуждаются в быстром, надёжном способе добавить прямоугольник в документ Word, придать ему лёгкую тень, настроить прозрачность и затем экспортировать результат в PDF.  

В этом руководстве мы пройдём всё шаг за шагом, с полным, готовым к запуску кодом. К концу вы узнаете, **как добавить тень** к фигуре, как **установить прозрачность фигуры**, и как **сохранить документ в PDF** с помощью Aspose.Words for Java. Без лишних слов, только практические рекомендации, которые можно сразу скопировать‑вставить в ваш проект.

## Что вы узнаете

- Минимальная настройка, необходимая для работы с Aspose.Words в Java‑проекте.  
- Как программно **создать прямоугольную фигуру**.  
- Точные вызовы, необходимые для **добавления тени к фигуре** и настройки её размытия, смещения и непрозрачности.  
- Способы **установки прозрачности фигуры**, чтобы прямоугольник гармонично сочетался с окружающим содержимым.  
- Самый простой способ **сохранить документ в PDF** без дополнительных шагов конвертации.  

Если вы уверенно владеете базовым Java и у вас есть сборка Maven или Gradle, вы готовы приступить.

## Требования

- Java 8 или новее.  
- Aspose.Words for Java 23.x (или последняя версия на момент чтения).  
- IDE или инструмент сборки командной строки (IntelliJ, Eclipse, Maven, Gradle — выбирайте любой).  

> **Pro tip:** Aspose предлагает бесплатную временную лицензию для оценки. Скачайте её в портале аккаунта и разместите файл `license.xml` в classpath; иначе в PDF будет водяной знак.

---

## Шаг 1: **Создать прямоугольную фигуру** с Aspose.Words

Первое, что нам нужно, — это пустой `Document` и `DocumentBuilder`. Builder — это рабочий конструктор, который позволяет вставлять фигуры напрямую в поток документа.

```java
import com.aspose.words.*;

public class RectangleShadowDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new empty Word document
        Document doc = new Document();

        // 2️⃣ Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3️⃣ Insert a rectangle shape – 200 points wide, 100 points tall
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 200.0, 100.0);
        // Optional: give the rectangle a light gray fill so the shadow is visible
        rect.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
```

**Почему это важно:** `ShapeType.RECTANGLE` сообщает Aspose, что нам нужен идеальный прямоугольник. Ширина и высота задаются в пунктах (1 pt ≈ 1/72 in), что даёт тонкую настройку окончательного размера.

---

## Шаг 2: **Добавить тень к фигуре**

Теперь, когда у нас есть прямоугольник, добавим ему лёгкую падающую тень. Объект `ShadowFormat` раскрывает всё необходимое — радиус размытия, смещение по X/Y и даже прозрачность.

```java
        // 4️⃣ Configure the shadow effect
        ShadowFormat shadow = rect.getShadowFormat();
        shadow.setBlur(5.0);          // Softness of the shadow edge
        shadow.setOffsetX(3.0);       // Horizontal shift (points)
        shadow.setOffsetY(3.0);       // Vertical shift (points)
        shadow.setTransparency(0.3); // 30 % transparent – makes it look natural
```

**Почему это важно:** Тень без размытия выглядит как жёсткая линия, что редко требуется дизайнерам. Вызов `setBlur` сглаживает края, а `setTransparency` позволяет тени плавно исчезать в фоне. Настраивайте эти значения в соответствии с вашими UI‑руководствами.

---

## Шаг 3: **Установить прозрачность фигуры**

Иногда требуется, чтобы сам прямоугольник был полупрозрачным — например, для наложения логотипа или водяного знака. Aspose делает это в одну строку.

```java
        // 5️⃣ Make the rectangle partially transparent (optional)
        rect.getFillFormat().setTransparency(0.2); // 20 % transparent fill
```

**Почему это важно:** Прозрачность может спасти жизнь при наложении фигур. Обратите внимание, что прозрачность самой тени независима, так что вы можете иметь лёгкую фигуру с более тёмной тенью, если это подходит вашему дизайну.

---

## Шаг 4: **Сохранить документ в PDF**

Вся визуальная работа завершена; последний шаг — сохранить документ. Aspose.Words может напрямую записывать в PDF, устраняя необходимость в отдельной библиотеке конвертации.

```java
        // 6️⃣ Persist the document as a PDF file
        String outPath = "output/RectangleWithShadow.pdf";
        doc.save(outPath, SaveFormat.PDF);
        System.out.println("PDF saved to: " + outPath);
    }
}
```

**Почему это важно:** Указывая `SaveFormat.PDF`, библиотека автоматически обрабатывает встраивание шрифтов, сжатие изображений и соответствие PDF/A. Полученный файл готов к распространению, печати или архивированию.

---

## Полный рабочий пример

Объединяя всё вместе, представляем полностью готовый к запуску класс. Скопируйте‑вставьте, при необходимости измените путь вывода, и вы получите PDF с прямоугольником, отбрасывающим реалистичную тень.

```java
import com.aspose.words.*;

public class RectangleShadowDemo {
    public static void main(String[] args) throws Exception {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert rectangle shape (200×100 points)
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 200.0, 100.0);
        rect.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);

        // Add shadow effect
        ShadowFormat shadow = rect.getShadowFormat();
        shadow.setBlur(5.0);
        shadow.setOffsetX(3.0);
        shadow.setOffsetY(3.0);
        shadow.setTransparency(0.3);

        // Optional: make the rectangle itself partially transparent
        rect.getFillFormat().setTransparency(0.2);

        // Save as PDF
        String outPath = "output/RectangleWithShadow.pdf";
        doc.save(outPath, SaveFormat.PDF);
        System.out.println("PDF saved to: " + outPath);
    }
}
```

**Ожидаемый результат:** При открытии `RectangleWithShadow.pdf` вы увидите светло‑серый прямоугольник, центрированный на первой странице, слегка «поднятый» над страницей мягкой полупрозрачной тенью. Сама фигура имеет 20 % прозрачности, позволяя просвечивать любой подлежащий текст (если вы его добавите).

---

## Часто задаваемые вопросы и особые случаи

### 1️⃣ Что делать, если нужен более крупный прямоугольник?

Просто измените параметры ширины и высоты в `insertShape`. Помните, что 72 pt = 1 in, так что `400.0, 200.0` даст вам прямоугольник размером 5.5 × 2.8 дюйма.

### 2️⃣ Можно ли использовать другой цвет для тени?

Конечно. Класс `ShadowFormat` также предоставляет `setColor(java.awt.Color)`. Для лёгкой серой тени попробуйте `shadow.setColor(java.awt.Color.DARK_GRAY);`.

### 3️⃣ Работает ли `save document as pdf` на всех платформах?

Да. Aspose.Words for Java платформенно‑независим; тот же код работает на Windows, macOS и Linux, при условии совместимой JRE.

### 4️⃣ Как позже удалить тень?

Вызовите `rect.getShadowFormat().clear();` или установите свойство `Visible` в `false` (`shadow.setVisible(false);`).

### 5️⃣ Что насчёт DPI и качества изображений?

При сохранении в PDF Aspose автоматически использует 300 DPI для векторной графики, такой как фигуры, поэтому вы получаете чёткие результаты независимо от уровня масштабирования.

---

## Pro Tips & Best Practices

- **Пакетная обработка:** Если нужно сгенерировать десятки PDF, переиспользуйте один экземпляр `Document` и очищайте только его секции между итерациями, чтобы снизить нагрузку на GC.  
- **Лицензирование:** Поместите `License license = new License(); license.setLicense("license.xml");` в начало `main`, чтобы избежать водяного знака оценки.  
- **Производительность:** Рендеринг тени дешёв для простых фигур, но сложные контуры могут замедлять генерацию PDF. Профилируйте при обработке больших пакетов.  
- **Тестирование:** Сначала используйте `Document.save(..., SaveFormat.DOCX)`, чтобы убедиться, что фигура правильно отображается в Word, перед конвертацией в PDF.

---

## Заключение

Теперь вы знаете, как **создать прямоугольную фигуру** в Java с Aspose.Words, **добавить тень к фигуре**, **установить прозрачность фигуры** и, наконец, **сохранить документ в PDF**. Код автономный, работает с последней библиотекой Aspose и демонстрирует основные вызовы API, необходимые в большинстве сценариев автоматизации документов.

Готовы к следующему вызову? Попробуйте заменить прямоугольник на эллипс, поэкспериментировать с градиентными заливками или изучить, как **добавить тень** к текстовым фреймам. Принципы те же, а API Aspose делает всё простым как разрезать хлеб.

Счастливого кодинга, и не стесняйтесь оставить комментарий, если столкнётесь с проблемами!

## Что стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в собственных проектах.

- [Создать документ Word на Java – Добавить прямоугольную фигуру с эффектом тени](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Как сохранить документ в PDF с Aspose.Words для Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Как создать поля формы и добавить контент с помощью DocumentBuilder в Aspose.Words для Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}