---
category: general
date: 2026-08-23
description: Узнайте, как вставить кнопку команды в документ Word с помощью Java и
  Aspose.Words. Это руководство показывает, как добавить элемент управления формы,
  задать имя кнопки и внедрить кнопку ActiveX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert command button
- add form control
- how to add button
- set button name
- add activex button
language: ru
lastmod: 2026-08-23
og_description: Вставьте кнопку команды в документ Word с помощью Java. Следуйте этому
  руководству, чтобы добавить элемент управления формы, задать имя кнопки и внедрить
  кнопку ActiveX с помощью Aspose.Words.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX command button
og_title: Вставка командной кнопки в Word с помощью Java – пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  headline: How to insert command button in a Word document using Java
  type: TechArticle
- description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  name: How to insert command button in a Word document using Java
  steps:
  - name: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
    text: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
  - name: The **Submit** button appears where the cursor was positioned during insertion.
    text: The **Submit** button appears where the cursor was positioned during insertion.
  - name: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
    text: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Как вставить кнопку управления в документ Word с помощью Java
url: /ru/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как вставить кнопку команды в документ Word с помощью Java

Если вам нужно **insert command button** в файл Word, этот учебник покажет полное решение с Aspose.Words for Java. Вы увидите, как добавить элемент управления формы, настроить его подпись и установить имя кнопки, не выходя из вашей IDE.

Руководство охватывает всё, что нужно для создания `.docx`, содержащего кнопку ActiveX, готовую к использованию в Microsoft Word. Дополнительные инструменты не требуются, пример работает на Java 8+.

## Что вы узнаете

* Как добавить элемент управления формы типа **CommandButton** в документ Word.  
* Точные шаги для **set button name** и **add activex button** свойств.  
* Как сохранить документ, чтобы кнопка отображалась корректно при открытии в Word.  

У вас должна быть базовая среда разработки Java и проект Maven или Gradle, способный импортировать библиотеку Aspose.Words.

## Требования

| Требование | Причина |
|-------------|--------|
| Java 8 или новее | Aspose.Words for Java работает на Java 8+. |
| Инструмент сборки Maven или Gradle | Упрощает добавление зависимости Aspose.Words. |
| Лицензия Aspose.Words for Java (или бесплатная пробная версия) | Требуется для полного набора функций; API работает в режиме оценки. |
| IDE, например IntelliJ IDEA или Eclipse | Облегчает редактирование и запуск примера. |

## Шаг 1: Добавьте Aspose.Words в ваш проект

Если вы используете Maven, добавьте следующую зависимость в `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest version -->
</dependency>
```

Для Gradle поместите эту строку в `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

После разрешения зависимости вы можете импортировать классы библиотеки в ваш Java‑файл.

## Шаг 2: Вставка command button – основной код

Создайте новый Java‑класс с именем `InsertCommandButtonDemo`. Приведённый ниже код выполняет все четыре действия, необходимые для **insert command button**:

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Add form control – an ActiveX CommandButton – to the document
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 3️⃣ Set button name and displayed caption (this answers the "set button name" need)
        commandButton.setName("btnSubmit");
        commandButton.setCaption("Submit");

        // 4️⃣ Save the document with the embedded button
        doc.save("CommandButtonDemo.docx");
    }
}
```

### Почему каждая строка важна

* **Document & DocumentBuilder** – Предоставляют представление Word‑файла в памяти и API для изменения его содержимого.  
* **insertForms2OleControl** – Этот метод **adds form control** типа `COMMAND_BUTTON`. Возвращаемый объект `Forms2OleControl` представляет элемент управления ActiveX.  
* **setName** – Присваивает программный идентификатор (`btnSubmit`). Макросы Word или VBA могут ссылаться на это имя позже.  
* **setCaption** – Определяет текст, который пользователь видит на кнопке, отвечая на вопрос «как добавить кнопку».  
* **save** – Записывает `.docx` на диск, сохраняет встроенную кнопку ActiveX.  

Запуск программы создаёт `CommandButtonDemo.docx` в рабочем каталоге. Открытие файла в Microsoft Word показывает кнопку с подписью **Submit**, по которой можно кликнуть (будет отображён диалог ActiveX по умолчанию в режиме оценки).

## Шаг 3: Проверка вставленной кнопки в Word

1. Откройте `CommandButtonDemo.docx` в Microsoft Word (2016 или новее).  
2. Кнопка **Submit** появляется там, где курсор был размещён во время вставки.  
3. Щёлкните правой кнопкой мыши по кнопке и выберите **Properties**, чтобы увидеть, что поле **Name** содержит `btnSubmit`.  

Если кнопка не отображается, убедитесь, что **ActiveX controls** включены в настройках Trust Center Word.

## Шаг 4: Настройка кнопки (необязательно)

Вы можете дополнительно настроить кнопку, изменив её размер, позицию или добавив макрос VBA. Класс `Forms2OleControl` раскрывает дополнительные свойства, такие как `setWidth`, `setHeight` и `setLeft`. Ниже пример, увеличивающий кнопку:

```java
commandButton.setWidth(100);   // Width in points
commandButton.setHeight(30);   // Height in points
commandButton.setLeft(50);     // Horizontal offset from the left margin
```

Эти строки можно разместить после вызова `setCaption`. Они демонстрируют настройку **add activex button**, выходящую за пределы базовой вставки.

## Распространённые подводные камни и как их избежать

| Симптом | Причина | Решение |
|---------|-------|-----|
| Кнопка не отображается в Word | Документ сохранён до добавления элемента управления | Убедитесь, что `insertForms2OleControl` вызывается до `doc.save`. |
| Подпись кнопки пуста | `setCaption` не вызван или вызван с пустой строкой | Укажите непустую строку, например, `"Submit"`. |
| VBA не может найти кнопку | Несоответствие имени между кодом VBA и значением `setName` | Сохраняйте имя согласованным; используйте `setName(\"btnSubmit\")` и обращайтесь к `btnSubmit` в VBA. |
| Предупреждение безопасности при открытии файла | Безопасность макросов Word блокирует элементы управления ActiveX | Настройте Trust Center > Macro Settings или подпишите документ доверенным сертификатом. |

## Полный, исполняемый пример

Ниже полный исходный файл, готовый к копированию и вставке в вашу IDE. Он включает операторы импорта, обработку исключений и блок комментариев, объясняющий каждый основной шаг.

```java
// InsertCommandButtonDemo.java
// Demonstrates how to insert an ActiveX CommandButton into a Word document using Aspose.Words for Java.

import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Add a CommandButton form control (ActiveX) to the document.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button – set its programmatic name and visible caption.
        commandButton.setName("btnSubmit");   // This answers the "set button name" requirement.
        commandButton.setCaption("Submit");   // This is the text the user sees.

        // Optional: Resize and reposition the button (demonstrates add activex button customization).
        commandButton.setWidth(100);
        commandButton.setHeight(30);
        commandButton.setLeft(50);

        // Step 4: Save the document. The button is now embedded and will appear in Word.
        doc.save("CommandButtonDemo.docx");
    }
}
```

**Ожидаемый результат:** После запуска программы `CommandButtonDemo.docx` содержит одну кнопку **Submit**. Открытие файла в Word показывает кнопку точно там, где находился курсор `DocumentBuilder`.

## Следующие шаги

* **Add more form controls** – Используйте `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON` или `TEXT_BOX` для создания полноценных форм Word.  
* **Combine with mail merge** – Вставляйте кнопки в документ, созданный с помощью слияния почты, чтобы создать персонализированные интерактивные формы.  
* **Attach VBA macros** – Программно внедряйте VBA, реагирующий на событие `Click` кнопки, для расширенной автоматизации.  

Эти темы естественно расширяют технику **add form control**, которую вы только что освоили.

### Итоги

Теперь вы знаете, как **insert command button** в документ Word с помощью Java, как **add form control**, как **set button name**, и как выполнять настройки **add activex button**. Полный пример работает сразу же, и вы можете адаптировать его под любой процесс генерации документов. Приятного кодинга!

## Что вам следует изучить дальше?

Следующие учебники охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Как создавать поля формы и добавлять содержимое с помощью DocumentBuilder в Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Вставить поле формы Combo Box в документ Word](/words/english/net/working-with-form-fields/insert-form-fields/)
- [Вставить поле формы Check Box в документ Word](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}