---
category: general
date: 2026-07-20
description: Как добавить кнопку в документ Word с помощью Aspose.Words. Научитесь
  вставлять кнопку Forms2OleControl с помощью DocumentBuilder за считанные минуты.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add button to word document
- Forms2OleControl
- DocumentBuilder
- insertForms2OleControl
- Word automation
language: ru
lastmod: 2026-07-20
og_description: Как добавить кнопку в документ Word с помощью Aspose.Words. Следуйте
  этому практическому руководству, чтобы внедрить кнопку CommandButton Forms2OleControl
  с использованием Java.
og_image_alt: Screenshot of a Word document with a clickable button added via Aspose.Words
  (how to add button to word document)
og_title: Как добавить кнопку в документ Word – Полный учебник Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  headline: How to Add Button to Word Document – Step‑by‑Step Guide
  type: TechArticle
- description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  name: How to Add Button to Word Document – Step‑by‑Step Guide
  steps:
  - name: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
    text: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
  - name: '`100` – width in points (≈1.39 inches).'
    text: '`100` – width in points (≈1.39 inches).'
  - name: '`30` – height in points (≈0.42 inches).'
    text: '`30` – height in points (≈0.42 inches).'
  type: HowTo
tags:
- Aspose.Words
- Java
- Office Automation
title: Как добавить кнопку в документ Word – пошаговое руководство
url: /ru/java/using-document-elements/how-to-add-button-to-word-document-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как добавить кнопку в документ Word – Полный учебник Aspose.Words

Когда‑то задавались вопросом **как добавить кнопку в документ Word** без открытия пользовательского интерфейса и кликов? Вы не одиноки. Многие разработчики нуждаются в программном внедрении интерактивных элементов — представьте кнопку «Submit» в шаблоне, которую позже заполняет конечный пользователь. Хорошая новость: с Aspose.Words for Java это можно сделать в паре строк кода.

В этом учебнике мы пошагово пройдем процесс вставки `Forms2OleControl` типа **CommandButton** с помощью `DocumentBuilder`. К концу вы получите готовый файл `.docx` с кликабельной кнопкой, подпись которой — «Click Me». Никаких загадок, только понятный код и объяснение каждой строки.

## Что вы узнаете

- Как создать новый документ Word с нуля.  
- Как использовать **DocumentBuilder** для размещения **Forms2OleControl**.  
- Почему следует задавать подпись кнопки и её размер так, как мы делаем.  
- Как сохранить и проверить результат.  
- Распространённые подводные камни (например, отсутствие библиотек, неподдерживаемые типы элементов управления) и как их избежать.  

**Prerequisites** – Вам нужен Java 8+ (или новее) и библиотека Aspose.Words for Java (версия 23.12 или новее). IDE, такая как IntelliJ IDEA или Eclipse, упростит работу, но подойдёт любой текстовый редактор.

---

## Шаг 1: Настройте проект и импортируйте зависимости

Прежде чем любой код выполнится, Maven (или Gradle) должен знать, откуда получать Aspose.Words. Добавьте следующий фрагмент в ваш `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

Если вы предпочитаете Gradle, эквивалент выглядит так:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Pro tip:** Используйте последнюю версию; более старые могут не содержать API `Forms2OleControl`.

После того как зависимость будет разрешена, вы готовы писать Java‑код.

---

## Шаг 2: Создайте новый документ и получите DocumentBuilder

Класс `Document` представляет весь пакет `.docx`, а `DocumentBuilder` — кисть, которой вы рисуете содержимое. Считайте `DocumentBuilder` «курсорoм», знающим, куда помещать следующий элемент.

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder tied to the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:** Инициализация нового `Document` дает чистый холст. Builder автоматически указывает на первый абзац, поэтому вам не нужно вручную управлять секциями или страницами.

---

## Шаг 3: Вставьте Forms2OleControl типа CommandButton

Теперь звезда шоу: `insertForms2OleControl`. Этот метод создаёт OLE (Object Linking and Embedding)‑элемент, который Word воспринимает как форму. Мы передадим три аргумента:

1. `Forms2OleControlType.COMMANDBUTTON` — сообщает Word, что нам нужна кнопка.  
2. `100` — ширина в пунктах (≈1,39 дюйма).  
3. `30` — высота в пунктах (≈0,42 дюйма).  

```java
        // Step 3: Insert a CommandButton with specific dimensions
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

**How it works:** Под капотом Aspose.Words генерирует соответствующий XML в части `word/document.xml`, ссылаясь на OLE‑объект. Переданные размеры учитываются движком разметки Word, поэтому кнопка появляется точно в том месте, где находится курсор builder’а.

---

## Шаг 4: Установите подпись (текст) на кнопку

Кнопка без подписи сбивает с толку — представьте бесшумную кнопку лифта. Метод `setCaption` задаёт видимый текст:

```java
        // Step 4: Define the button's label
        commandButton.setCaption("Click Me");
```

Подпись можно изменить на любую: «Submit», «Approve» или даже локализованную строку. Она хранится в свойствах OLE‑объекта, поэтому Word отобразит её нативно.

---

## Шаг 5: Сохраните документ и проверьте результат

Наконец, запишите файл на диск. Выберите папку, в которую у вас есть права записи; иначе получите `IOException`.

```java
        // Step 5: Persist the document
        String outputPath = "output/button-demo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Откройте `button-demo.docx` в Microsoft Word. Вы должны увидеть кнопку с подписью **Click Me**, расположенную в верхней части документа. При клике в Word будет выполнено стандартное OLE‑поведение (обычно placeholder‑сообщение, если только не привязан макрос).

---

## Распространённые граничные случаи и как их решить

| Ситуация | Почему происходит | Как исправить |
|-----------|-------------------|---------------|
| **Missing `Forms2OleControl` type** | В более старых версиях Aspose.Words этот enum не был доступен. | Обновите до версии 23.12+ или новее. |
| **Button appears as a picture** | Настройки безопасности Word блокируют OLE‑элементы. | Включите «Trust access to the VBA project object model» в Trust Center, либо используйте макрос‑включённый `.docm`. |
| **Incorrect size** | Путаница между пунктами и пикселями. | Помните, 1 point = 1/72 inch. Корректируйте числа соответственно. |
| **Saving throws `FileNotFoundException`** | Путь не существует. | Убедитесь, что каталог (`output/`) создан перед `doc.save`. Используйте `new File("output").mkdirs();`. |

---

## Расширение примера: добавление нескольких кнопок или других элементов управления

Если требуется более одной кнопки, просто переместите курсор builder’а с помощью `builder.moveTo` или `builder.writeln()` перед повторным вызовом `insertForms2OleControl`.

```java
        // Add a second button below the first
        builder.writeln(); // moves to a new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");
```

Вы также можете вставить **CheckBox**, **ComboBox** или **ListBox**, заменив `Forms2OleControlType.COMMANDBUTTON` на соответствующее значение enum (`CHECKBOX`, `COMBOBOX` и т.д.). Параметры ширины/высоты остаются теми же.

---

## Как это вписывается в более крупные сценарии автоматизации Word

- **Template Generation:** Создайте шаблон контракта, включающий кнопку «Approve» для последующего подтверждения.  
- **Reporting:** Генерируйте ежедневный отчёт с кнопкой «Refresh Data», вызывающей макрос.  
- **Form Distribution:** Рассылайте анкету с заранее заполненными интерактивными элементами.  

Все эти сценарии выигрывают от подхода **Word automation**, который мы продемонстрировали. Встраивая элементы управления программно, вы исключаете ручное редактирование и снижаете риск ошибок.

---

## Полный исходный код (готов к копированию)

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a CommandButton (width: 100pt, height: 30pt)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

        // Set the button caption
        commandButton.setCaption("Click Me");

        // Optionally add a second button
        builder.writeln(); // new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");

        // Save the document
        String outputPath = "output/button-demo.docx";
        new java.io.File("output").mkdirs(); // ensure directory exists
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

**Expected output:** При открытии `output/button-demo.docx` в Microsoft Word вы увидите две кнопки — «Click Me» и «Submit» — расположенные вертикально в верхней части файла.

---

## Заключение

Мы ответили на вопрос **как добавить кнопку в документ Word** с помощью Aspose.Words for Java, шаг за шагом. Начиная с пустого `Document`, мы использовали **DocumentBuilder** для вставки `Forms2OleControl` типа **CommandButton**, задали дружелюбную подпись и сохранили результат. Подход масштабируется на несколько элементов управления и легко интегрируется в более широкие конвейеры **Word automation**.

Готовы к следующему вызову? Попробуйте заменить кнопку на **CheckBox** или привяжите макрос, реагирующий на клик пользователя в файле `.docm`. Тот же шаблон работает — просто измените enum и подпись.

Если столкнётесь с проблемами, дважды проверьте версию библиотеки и права доступа к папке вывода. Оставляйте комментарии с вопросами или делитесь своими кейсами. Приятного кодинга!

## Что вам стоит изучить дальше?

Следующие учебники охватывают тесно связанные темы, развивая техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Как создавать поля формы и добавлять содержимое с помощью DocumentBuilder в Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Вставка встроенного изображения в документ Word с помощью Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Создание групповой фигуры в документе Word с помощью Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}