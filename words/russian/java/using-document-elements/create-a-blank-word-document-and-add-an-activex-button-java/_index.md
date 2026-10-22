---
category: general
date: 2026-10-16
description: Создайте пустой документ Word с помощью Java и узнайте, как добавить
  кнопку ActiveX, установить её подпись и настроить её размеры с использованием Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add activex button
- set button caption
- set button dimensions
language: ru
lastmod: 2026-10-16
og_description: Создайте пустой документ Word с помощью Java, затем добавьте кнопку
  ActiveX, задайте её подпись и определите её размеры, используя Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with an ActiveX button inserted
og_title: Создайте пустой документ Word и вставьте кнопку ActiveX — руководство по
  Java
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document with Java and learn how to add an ActiveX
    button, set its caption, and adjust its dimensions using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button (Java)
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
title: Создайте пустой документ Word и добавьте кнопку ActiveX (Java)
url: /ru/java/using-document-elements/create-a-blank-word-document-and-add-an-activex-button-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создать пустой документ Word и добавить кнопку ActiveX (Java)

Если вам нужно **создать пустой документ Word** программно, это руководство покажет, как сделать это с помощью Java и Aspose.Words. Вы также узнаете, как **добавить кнопку ActiveX**, **установить подпись кнопки** и **задать размеры кнопки**, чтобы элемент выглядел точно так, как вы ожидаете.

Этот учебник охватывает:

* Инициализацию пустого файла Word с помощью Aspose.Words for Java.  
* Вставку элемента управления ActiveX `CommandButton`.  
* Настройку подписи и размеров кнопки.  
* Сохранение окончательного файла `.docx`.

Вы должны иметь базовые знания Java и актуальную версию библиотеки Aspose.Words for Java (код работает с 23.9 и новее). Дополнительные зависимости не требуются.

![Create a blank Word document with an ActiveX button](/images/activex-button-example.png){: .align-center alt="Создать пустой документ Word с кнопкой ActiveX"}

## Создать пустой документ Word с Aspose.Words

Первый шаг — создать пустой объект `Document`. Этот объект представляет весь файл Word в памяти и предоставляет класс `DocumentBuilder` для редактирования.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(doc);
        
        // The rest of the steps follow here...
```

**Почему это важно:**  
Создание пустого документа дает вам чистый холст, избегая скрытых стилей или разделов, которые могут помешать последующим вычислениям макета.

## Добавить кнопку ActiveX в документ

Aspose.Words позволяет встраивать устаревшие элементы управления ActiveX через класс `Forms2OleControl`. Следующий код вставляет элемент управления `CommandButton` в текущую позицию курсора.

```java
        // Step 2: Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Define the exact ActiveX class name (CommandButton)
        commandButton.setOleClassName("Forms.CommandButton.1");
```

**Подсказка:** Значение `setOleClassName` `"Forms.CommandButton.1"` — это ProgID стандартной кнопки Microsoft Forms. Использование другого ProgID (например, `"Forms.CheckBox.1"`) вставит элемент управления другого типа.

## Установить подпись кнопки

Подпись — это текст, отображаемый на поверхности кнопки. Вы можете изменить её в любой момент до сохранения документа.

```java
        // Step 3: Set the button's caption
        commandButton.setCaption("Click Me");
```

**Зачем это нужно:** Пользователи понимают элемент управления только тогда, когда его назначение ясно. Установка осмысленной подписи повышает удобство использования, особенно когда документ открывается в Word на Windows.

## Установить размеры кнопки

Позиция и размер задаются в пунктах (1 пункт = 1/72 дюйма). Отрегулируйте значения под ваш макет.

```java
        // Step 4: Define button size and location
        commandButton.setLeft(100);    // distance from the left edge of the page
        commandButton.setTop(200);     // distance from the top edge of the page
        commandButton.setWidth(120);   // width of the button
        commandButton.setHeight(30);   // height of the button
```

**Распространённые варианты:**

| Сценарий | Настройка |
|----------|------------|
| Больше кнопка для сенсорных экранов | Увеличьте `setWidth` и `setHeight` пропорционально |
| Кнопка по центру страницы | Вычислите `left = (pageWidth - width) / 2` |
| Несколько кнопок в колонке | Увеличьте `setTop` для каждой новой кнопки |

## Сохранить документ, содержащий кнопку ActiveX

Наконец, запишите документ на диск. Формат `.docx` сохраняет элемент управления ActiveX для Windows‑версий Microsoft Word.

```java
        // Step 5: Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

**Ожидаемый результат:** Открытие `ActiveXCommandButton.docx` в Word (Windows) показывает пустую страницу с кликабельной кнопкой с подписью **Click Me**, расположенной на 100 пт от левого поля и 200 пт от верхнего поля.

## Полный, исполняемый пример

Скопируйте весь класс ниже в вашу IDE, добавьте JAR‑файл Aspose.Words for Java в classpath проекта и запустите его.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setOleClassName("Forms.CommandButton.1");

        // Set button caption
        commandButton.setCaption("Click Me");

        // Set button dimensions and position
        commandButton.setLeft(100);    // points from left edge
        commandButton.setTop(200);     // points from top edge
        commandButton.setWidth(120);   // width in points
        commandButton.setHeight(30);   // height in points

        // Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

Запуск программы создаёт `ActiveXCommandButton.docx` в рабочем каталоге. Откройте его в Microsoft Word (Windows), чтобы убедиться, что кнопка отображается точно так, как сконфигурирована.

## Почему рекомендуется такой подход

* **Простота:** Используется только ядро API Aspose.Words; не требуется COM‑interop или дополнительные библиотеки.  
* **Переносимость:** Код работает на любой платформе, поддерживающей Java, хотя сам элемент управления ActiveX работает только в Windows‑версиях Word.  
* **Поддерживаемость:** Все свойства (подпись, размеры, позиция) задаются через понятные, самодокументирующиеся методы, что упрощает будущие изменения.

## Распространённые подводные камни и как их избежать

| Подводный камень | Решение |
|------------------|----------|
| Кнопка не появляется в Word на macOS или Linux | Элементы управления ActiveX работают только в Windows. Используйте другой элемент (например, контент‑контроль) для кроссплатформенных документов. |
| Подпись обрезается | Убедитесь, что ширина кнопки достаточна для текста; увеличьте `setWidth` или используйте более короткую подпись. |
| Кнопка перекрывает другой контент | Отрегулируйте значения `setTop` и `setLeft` или вставьте новый абзац перед элементом управления, чтобы дать ему собственное пространство. |

## Следующие шаги

Теперь, когда вы умеете **создавать пустой документ Word**, **добавлять кнопку ActiveX**, **устанавливать подпись кнопки** и **задавать размеры кнопки**, вы можете исследовать:

* Добавление кода обработки событий через VBA‑макросы (требуется встраивание модуля макросов).  
* Вставку нескольких элементов управления в табличный макет для формоподобных документов.  
* Использование **FormField** API Aspose.Words для кроссплатформенных решений форм.

Экспериментируйте с различными размерами, позициями и подписями, чтобы подобрать оптимальный дизайн вашего документа. Приятного кодинга!

## Что вам следует изучить дальше?

Следующие учебники охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Создать документ Word Java – Добавить прямоугольную форму с эффектом тени](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Как создать поля формы и добавить содержимое с помощью DocumentBuilder в Aspose.Words для Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Добавить водяной знак в документ с помощью Aspose.Words для Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}