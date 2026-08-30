---
category: general
date: 2026-07-26
description: Как вставить кнопку ActiveX в документ Word с помощью Aspose.Words –
  узнайте, как задать подпись кнопки, её позицию и размер всего в несколько строк.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert activex
- set button caption
language: ru
lastmod: 2026-07-26
og_description: Как вставить кнопку ActiveX в документ Word с помощью Aspose.Words.
  Следуйте этому пошаговому руководству, чтобы задать подпись кнопки, её положение
  и размер.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX CommandButton
  with a custom caption
og_title: Как вставить кнопку ActiveX в Word — быстрый гид
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: How to insert ActiveX button in a Word document using Aspose.Words
    – learn to set button caption, position, and size in just a few lines.
  headline: How to Insert ActiveX Button in Word – Set Button Caption
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- Document generation
title: Как вставить кнопку ActiveX в Word – задать подпись кнопки
url: /ru/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как вставить кнопку ActiveX в Word – Установить подпись кнопки

Когда‑то задавались вопросом, **как вставить ActiveX**‑контролы в файл Word без открытия пользовательского интерфейса? Вы не одиноки. Во многих корпоративных приложениях нужна кликабельная кнопка, запускающая макрос, и выполнение этой задачи программно экономит часы работы. В этом руководстве показано, как именно **вставить ActiveX** CommandButton с помощью Aspose.Words for Java и, да, как **установить подпись кнопки**, чтобы пользователь знал, что нажимать.

Мы пройдём весь процесс: от настройки библиотеки, создания нового документа, добавления кнопки, настройки её размера и положения, задания дружелюбной подписи и, наконец, сохранения файла. К концу вы получите готовый `.docx`, который откроется в Word с полностью функционирующей кнопкой ActiveX, готовой вызвать ваш макрос.

---

## Что вы узнаете

- Как установить и подключить Aspose.Words в проект Java.  
- Как создать новый `Document` и `DocumentBuilder`.  
- **Вставить ActiveX** CommandButton одной строкой кода.  
- **Установить подпись кнопки**, задать её позицию и размеры.  
- Сохранить документ и открыть его в Word, чтобы увидеть результат.

Предварительный опыт работы с ActiveX не требуется; достаточно базовых знаний Java и копии Aspose.Words.

---

## Требования

- Java 8 или новее, установленная на вашем компьютере.  
- Maven или Gradle для управления зависимостями (покажем пример для Maven).  
- Лицензионная или оценочная копия **Aspose.Words for Java** (бесплатная пробная версия подходит для этой демонстрации).  
- Microsoft Word (любая современная версия) для тестирования сгенерированного файла.

---

## Шаг 1: Настройте Aspose.Words в вашем проекте

Для начала добавьте зависимость Aspose.Words. Если вы используете Maven, поместите следующее в ваш `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for the latest version -->
</dependency>
```

Пользователи Gradle могут добавить:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

После быстрого `mvn clean install` (или `gradle build`) библиотека окажется в вашем classpath, и вы готовы писать код.

---

## Шаг 2: Создайте новый документ и Builder

`Document` представляет весь файл Word, а `DocumentBuilder` позволяет его редактировать. Можно сравнить Builder с ручкой, рисующей на чистом холсте.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();                 // creates an empty .docx
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Зачем начинать с пустого документа? Это гарантирует полный контроль над каждым добавляемым элементом и отсутствие скрытого форматирования, которое могло бы вас позже удивить.

---

## Шаг 3: Вставьте контрол ActiveX CommandButton

Теперь к главному. Aspose.Words предоставляет метод `insertForms2OleControl`, который может разместить любой указанный вами ActiveX‑контрол. Здесь мы запрашиваем **CommandButton**.

```java
        // Step 3: Insert a CommandButton ActiveX control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

Метод возвращает объект `Forms2OleControl`, дающий программный доступ к свойствам кнопки. Именно здесь **как вставить activex** превращается в однострочник — без необходимости работать с низкоуровневыми COM‑API.

---

## Шаг 4: Позиция, размер и установка подписи кнопки

Кнопка, плавающая посередине страницы, не слишком полезна. Нужно разместить её там, где пользователь её ожидает, задать разумный размер и, что самое важное, **установить подпись кнопки**, чтобы было понятно, что произойдёт при нажатии.

```java
        // Step 4a: Position the button (coordinates are in points)
        commandBtn.setLeft(100);   // distance from the left margin
        commandBtn.setTop(150);    // distance from the top margin

        // Step 4b: Define width and height
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Step 4c: Set the button caption (the text that appears on the button)
        commandBtn.setCaption("Click Me");
```

**Почему именно эти числа?** Word использует пункты (1 pt ≈ 1/72 дюйма). `100 pt` ≈ 1,4 дюйма от левого края, `150 pt` ≈ 2,1 дюйма от верхнего края — примерно центр стандартной страницы A4. Корректируйте их под свой макет.

Установка подписи критична; без неё кнопка выглядит как пустой прямоугольник. Метод `setCaption` принимает любую строку, так что при необходимости её можно локализовать позже.

---

## Шаг 5: Сохраните документ

Наконец, запишите документ на диск. Вы можете выбрать любую папку, только убедитесь, что путь существует.

```java
        // Step 5: Save the document to a .docx file
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Когда откроете `ActiveXButton.docx` в Word, вы увидите аккуратно размещённую кнопку с подписью **«Click Me»**. При двойном щелчке Word предложит включить макросы (поскольку ActiveX‑контролы считаются макрос‑включёнными). После этого вы сможете привязать VBA‑процедуру к событию `Click` кнопки.

---

## Особые случаи и советы, которые легко упустить

- **Формат с поддержкой макросов**: Word отключает ActiveX‑контролы в обычных `.docx`, если пользователь не включит макросы. Если нужна работа «из коробки», сохраняйте как `.docm` (macro‑enabled) с помощью `doc.save(outputPath, SaveFormat.DOCM);`.
- **Совместимость**: Более старые версии Word (до 2007) используют бинарный формат `.doc`. Aspose.Words умеет сохранять в этом формате, но свойства контролов могут выглядеть немного иначе.
- **Настройки безопасности**: В некоторых корпоративных средах ActiveX заблокирован. Если кнопка не появляется, проверьте Центр управления безопасностью Word → Настройки ActiveX.
- **Несколько кнопок**: Нужно больше одной? Просто повторите вызов `insertForms2OleControl` и скорректируйте значения `Left`/`Top` каждой кнопки. Сохраняйте ссылки на возвращаемые объекты, чтобы задавать индивидуальные подписи.
- **Стилизация подписи**: Подпись наследует шрифт по умолчанию. Чтобы изменить её, придётся редактировать внутренний XML или применить стиль Word после вставки — это выходит за рамки данного быстрого руководства, но реализуемо через API `ParagraphFormat` Aspose.Words.

---

## Полный рабочий пример

Ниже приведён полностью готовый к запуску Java‑класс. Скопируйте его в свою IDE, поправьте путь вывода и нажмите **Run**.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Position the button (points from the left/top margins)
        commandBtn.setLeft(100);
        commandBtn.setTop(150);

        // Set size (width × height in points)
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Set the button caption – this is the visible text
        commandBtn.setCaption("Click Me");

        // Save the document; you may also use SaveFormat.DOCM for macro‑enabled files
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

**Ожидаемый результат**: После выполнения в консоли будет выведен путь сохранения. Открыв сгенерированный файл в Word, вы увидите кнопку, расположенную примерно в центре страницы, с подписью «Click Me». При нажатии произойдёт стандартное событие ActiveX Click (для реакции потребуется привязать VBA‑макрос).

---

## Заключение

Теперь вы знаете **как вставить ActiveX** CommandButton в документ Word программно с помощью Aspose.Words и точно понимаете, как **установить подпись кнопки**, задать её позицию и размер. Этот подход избавляет от ручной работы с UI, легко интегрируется в автоматические генераторы отчётов и даёт полный контроль над элементом.

## Что изучать дальше?


Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс содержит полностью рабочие примеры кода с пошаговыми объяснениями, помогающие освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Insert an Image into Word Document Header | Aspose.Words for .NET](/words/english/net/header-footer-formatting/insert-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}