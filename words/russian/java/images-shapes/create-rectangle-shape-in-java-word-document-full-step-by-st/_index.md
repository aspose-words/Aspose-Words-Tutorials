---
category: general
date: 2026-05-26
description: Создайте прямоугольную форму в документе Word на Java и примените эффект
  тени. Узнайте, как добавить тень к форме, установить расстояние тени и сохранить
  файл.
draft: false
keywords:
- create rectangle shape
- apply shadow effect
- create word document java
- add shape shadow
- set shadow distance
language: ru
og_description: Создайте прямоугольную форму в документе Word на Java, примените эффект
  тени, добавьте тень к форме и задайте расстояние тени с помощью Aspose.Words.
og_title: Создание прямоугольной формы в документе Word на Java – Полное руководство
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create rectangle shape in a Java Word document and apply shadow effect.
    Learn how to add shape shadow, set shadow distance, and save the file.
  headline: Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in a Java Word document and apply shadow effect.
    Learn how to add shape shadow, set shadow distance, and save the file.
  name: Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide
  steps:
  - name: “Can I use a different shape?”
    text: Absolutely. Replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`, `ShapeType.LINE`,
      or any other supported enum. The rest of the shadow code stays the same.
  - name: “What if I need multiple shadows?”
    text: Aspose.Words only supports a single shadow per shape. To simulate multiple
      shadows, duplicate the shape, offset each copy, and adjust the transparency.
  - name: “Is the shadow visible in LibreOffice?”
    text: Yes—Aspose.Words writes standard OOXML, which LibreOffice interprets correctly.
      The shadow may look slightly different due to rendering engines, but the effect
      persists.
  - name: “How do I change the shadow color to match my brand?”
    text: Just swap `java.awt.Color.GRAY` with any `java.awt.Color` you prefer, such
      as `new java.awt.Color(0, 120, 215)` for a corporate blue.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word Automation
title: Создание прямоугольной фигуры в документе Word на Java – полное пошаговое руководство
url: /ru/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание прямоугольной формы в Java Word Document – Полное пошаговое руководство

Когда‑нибудь вам нужно было **create rectangle shape** в Java Word документе, но вы не знали, с чего начать? Вы не одиноки — многие разработчики сталкиваются с этой проблемой при программной генерации отчетов или счетов. В этом руководстве мы подробно покажем, как **create rectangle shape**, применить аккуратную тень и точно настроить расстояние тени, чтобы результат выглядел профессионально.

Мы будем использовать Aspose.Words for Java, мощную библиотеку, позволяющую манипулировать Word‑файлами без установки Microsoft Office. К концу этого руководства вы сможете создавать проекты **create word document java**, которые **add shape shadow**, **apply shadow effect** и **set shadow distance** всего несколькими строками кода.

---

## Что вы создадите

- Новый файл `.docx`, содержащий циановый прямоугольник.
- Реалистичная падающая тень, размытая, под углом и частично прозрачная.
- Полный контроль над расстоянием тени от формы.
- Готовый к запуску Java‑класс, который можно добавить в любой проект Maven или Gradle.

Никаких внешних инструментов, никаких ручных действий в UI — только чистый код.

---

## Предварительные требования

- Java 8 или новее (код работает на Java 11, Java 17 и т.д.).
- Библиотека Aspose.Words for Java (доступна через Maven Central).
- IDE или текстовый редактор по вашему выбору (IntelliJ IDEA, Eclipse, VS Code…).
- Базовое знакомство с синтаксисом Java.

Если вы никогда не добавляли зависимость Maven, вот быстрый фрагмент:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

Теперь давайте погрузимся.

---

## Шаг 1: Создание прямоугольной формы в документе Word

Первое, что нам нужно, — пустой документ и `DocumentBuilder`. Думайте о билдере как о перье, которое пишет в документ. Как только он у нас есть, мы можем **create rectangle shape** одним вызовом метода.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape of 150x80 points.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        // Make the shape visible by filling it with cyan.
        rectangleShape.setFillColor(java.awt.Color.CYAN);
```

> **Почему это важно:** Метод `insertShape` не только создает геометрию, но и добавляет форму во внутреннюю коллекцию документа, так что вы можете сразу приступить к её стилизации.

---

## Шаг 2: Применение эффекта тени к форме

Теперь, когда прямоугольник находится на странице, мы **apply shadow effect**. Тени придают глубину, заставляя форму выглядеть так, будто она поднялась над страницей — тонкое улучшение UI, которое может повысить читаемость в отчетах.

```java
        // Retrieve the shadow format object.
        ShadowFormat shadowFormat = rectangleShape.getShadowFormat();

        // Enable the shadow and configure its appearance.
        shadowFormat.setVisible(true);          // Turn the shadow on.
        shadowFormat.setBlur(5.0);              // Soft blur radius.
        shadowFormat.setAngle(45.0);            // Direction of the shadow.
        shadowFormat.setColor(java.awt.Color.GRAY); // Shadow color.
        shadowFormat.setTransparency(0.3);     // 30% transparent.
```

> **Pro tip:** Размытие `5.0` выглядит естественно для большинства документов, отображаемых на экране. Если вы печатаете, возможно, захотите немного уменьшить значение, чтобы избежать размытого вида.

---

## Шаг 3: Установка расстояния тени – точная настройка положения

Тени — это не только размытие; им также нужен правильный сдвиг. Здесь мы **set shadow distance**. Расстояние `7.0` пунктов создает умеренный сдвиг, заметный, но не навязчивый.

```java
        // Define how far the shadow sits from the shape.
        shadowFormat.setDistance(7.0); // Distance in points.
```

> **Что если мне нужен больший сдвиг?** Увеличьте значение; уменьшите его для более плотного вида. Помните, расстояние работает вместе с углом, чтобы правильно позиционировать тень.

---

## Шаг 4: Сохранение документа – сохранение вашей работы

Наконец, мы записываем документ на диск. Измените путь на тот, где вы хотите хранить файл.

```java
        // Save the document with the rectangle and its shadow.
        doc.save("YOUR_DIRECTORY/shadow.docx");
    }
}
```

Запуск класса создаёт файл `shadow.docx`, который при открытии в Microsoft Word или LibreOffice показывает циановый прямоугольник с мягкой серой тенью, наклонённой под 45° и сдвинутой на 7 пунктов.

---

## Полный рабочий пример

Ниже приведён полностью готовый к копированию код. Он включает все импорты, комментарии и финальный вызов `save`.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape of the desired size.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        // Step 3: Apply a fill color to make the shape visible.
        rectangleShape.setFillColor(java.awt.Color.CYAN);

        // Step 4: Configure the shape's shadow effect.
        ShadowFormat shadowFormat = rectangleShape.getShadowFormat();
        shadowFormat.setVisible(true);          // Enable the shadow.
        shadowFormat.setBlur(5.0);              // Set the blur radius.
        shadowFormat.setDistance(7.0);          // Define how far the shadow is from the shape.
        shadowFormat.setAngle(45.0);            // Set the direction of the shadow.
        shadowFormat.setColor(java.awt.Color.GRAY); // Choose the shadow color.
        shadowFormat.setTransparency(0.3);      // Make the shadow partially transparent.

        // Step 5: Save the document with the shaped shadow.
        doc.save("YOUR_DIRECTORY/shadow.docx");
    }
}
```

**Ожидаемый результат:** Откройте `shadow.docx` → вы увидите циановый прямоугольник, центрированный на первой странице, отбрасывающий лёгкую серую тень, слегка смещённую вниз‑вправо. Размытие и прозрачность тени делают её похожей на естественное освещение.

---

## Часто задаваемые вопросы и особые случаи

### «Могу ли я использовать другую форму?»

Абсолютно. Замените `ShapeType.RECTANGLE` на `ShapeType.OVAL`, `ShapeType.LINE` или любой другой поддерживаемый enum. Остальной код тени остаётся без изменений.

### «Что если мне нужны несколько теней?»

Aspose.Words поддерживает только одну тень на форму. Чтобы имитировать несколько теней, продублируйте форму, сдвиньте каждую копию и отрегулируйте прозрачность.

### «Видна ли тень в LibreOffice?»

Да — Aspose.Words записывает стандартный OOXML, который LibreOffice корректно интерпретирует. Тень может выглядеть немного иначе из‑за разных движков рендеринга, но эффект сохраняется.

### «Как изменить цвет тени, чтобы он соответствовал моему бренду?»

Просто замените `java.awt.Color.GRAY` на любой `java.awt.Color`, который вам нужен, например `new java.awt.Color(0, 120, 215)` для корпоративного синего.

---

## Иллюстрация

![create rectangle shape in Java Word document](https://example.com/images/rectangle-shadow.png)

*Alt text:* **create rectangle shape** иллюстрация, показывающая циановый прямоугольник с серой падающей тенью в документе Word.

---

## Итоги и дальнейшие шаги

Мы рассмотрели, как **create rectangle shape**, **apply shadow effect**, **add shape shadow** и **set shadow distance** с помощью Aspose.Words for Java. Код автономный, работает на любой современной JDK и создаёт полированный файл `.docx`, готовый к распространению.

Хотите пойти дальше? Попробуйте:

- Добавить текст внутри прямоугольника с помощью `builder.moveTo(rectangleShape.getAbsolutePosition())`.
- Создать таблицу форм для построения диаграммы.
- Экспортировать документ в PDF (`doc.save("output.pdf", SaveFormat.PDF);`).

Каждое из этих действий опирается на те же основы, которые мы только что изучили, так что вы будете чувствовать себя уверенно, расширяя пример.

---

## Заключительные мысли

Освоив задачи **create word document java**, такие как формирование и затенение, вы получаете огромное преимущество при автоматизации отчетов, контрактов или маркетинговых материалов. Подход, показанный здесь, чистый, поддерживаемый и — что самое важное — легко настраиваемый под любой визуальный стиль, который вам нужен.

Запустите код, поиграйте с размытием, углом и расстоянием, и наблюдайте, как ваши документы превращаются из скучных в полированные. Если столкнётесь с проблемой, оставьте комментарий ниже; я с радостью помогу.

Удачной разработки!

## Похожие руководства

- [Создать документ Word на Java – Добавить прямоугольную форму с эффектом тени](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Как создать поля формы и добавить содержимое с помощью DocumentBuilder в Aspose.Words для Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Создать PDF из Word с генерацией штрихкода – Aspose.Words для Java](/words/english/java/document-conversion-and-export/using-barcode-generation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}