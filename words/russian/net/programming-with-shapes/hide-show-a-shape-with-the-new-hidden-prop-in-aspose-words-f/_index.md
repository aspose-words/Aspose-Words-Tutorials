---
category: general
date: 2026-10-20
description: Скрывайте/отображайте форму с помощью нового свойства `Hidden` в Aspose.Words
  для C#. Узнайте, как переключать видимость формы, обрабатывать крайние случаи и
  сохранять результат.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Hide/Show a Shape with the new `Hidden` prop
- Aspose.Words hide shape
- C# shape hidden property
- Word document shape visibility
- programmatically hide shape
language: ru
lastmod: 2026-10-20
og_description: Скрывайте/показывайте форму с новым свойством `Hidden` в Aspose.Words
  для C#. Овладейте переключением видимости формы и избегайте распространённых ошибок.
og_image_alt: Screenshot of a Word document where a shape is hidden using the Hidden
  property
og_title: Скрыть/показать объект с новым свойством `Hidden` в Aspose.Words (C#)
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Hide/Show a Shape with the new `Hidden` prop using Aspose.Words for
    C#. Learn how to toggle shape visibility, handle edge cases, and save the result.
  headline: Hide/Show a Shape with the new `Hidden` prop in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Скрыть/показать форму с новым свойством `Hidden` в Aspose.Words для C#
url: /ru/net/programming-with-shapes/hide-show-a-shape-with-the-new-hidden-prop-in-aspose-words-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Скрыть/Показать объект с новым свойством `Hidden` в Aspose.Words для C#

Если вам нужно **скрыть/показать объект с новым свойством `Hidden`** в документе Word, это руководство покажет, как сделать это с помощью Aspose.Words для .NET. Независимо от того, генерируете ли вы отчёты, создаёте шаблоны или очищаете импортированные документы, программное управление видимостью объектов экономит время, избавляя от ручного редактирования.

В этом учебнике вы узнаете, как загрузить документ, найти объект, переключить свойство `Hidden` и сохранить изменённый файл. Шаги также охватывают распространённые варианты, такие как обработка нескольких объектов и работа с встроенными и плавающими графиками.

## Предварительные требования

* .NET 6.0 (или новее) установлен – Aspose.Words поддерживает .NET Standard 2.0 и .NET Core.  
* Лицензионная копия **Aspose.Words for .NET** (бесплатная пробная версия подходит для изучения).  
* IDE, например Visual Studio 2022 или Visual Studio Code.  
* Документ Word (`input.docx`), содержащий хотя бы один объект (например, изображение, SmartArt или холст для рисования).

## Шаг 1: Загрузка документа Word

Первая операция – создать объект `Document`, представляющий файл .docx на диске.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Почему этот шаг важен*: `Document` – точка входа для всех операций Aspose.Words. Загрузка файла в память даёт полный доступ к дереву узлов, включая объекты Shape.

## Шаг 2: Получение целевого объекта

Чтобы переключить видимость, необходимо получить ссылку на узел объекта. Пример ниже извлекает первый объект в документе, но вы можете адаптировать логику для поиска объектов по имени, типу или индексу.

```csharp
// Get the first Shape node in the document tree
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

if (shape == null)
{
    throw new InvalidOperationException("No shape was found in the document.");
}
```

*Почему этот шаг важен*: `GetChild` с параметром `true` выполняет глубокий поиск, гарантируя, что вы найдёте объекты даже если они вложены в таблицы или колонтитулы. Проверка на `null` предотвращает `NullReferenceException`, когда в документе нет объектов.

## Шаг 3: Скрыть объект с помощью свойства `Hidden`

Aspose.Words introduced the `Hidden` property to control whether a shape is rendered or printed. Setting it to `true` hides the shape; setting it to `false` makes the shape visible again.

```csharp
// Hide the shape so it will not appear in the rendered document
shape.Hidden = true;
```

Если вам нужно **показать** ранее скрытый объект, просто присвойте `false`:

```csharp
// Show the shape again
shape.Hidden = false;
```

*Почему этот шаг важен*: Свойство `Hidden` работает как для плавающих, так и для встроенных объектов и интегрировано с нативным форматом Word «Hidden». Такой подход надёжнее, чем удаление объекта, поскольку узел остаётся в дереве документа, сохраняя разметку и ссылки.

## Шаг 4: Сохранение изменённого документа

После изменения видимости запишите изменения в новый файл (или при желании перезапишите оригинал).

```csharp
// Save the document with the updated shape visibility
doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");
```

*Почему этот шаг важен*: `Save` сериализует дерево узлов в памяти в пакет .docx, который может открыть Word. Флаг скрытия сохраняется, поэтому при открытии файла в Microsoft Word объект будет отображён согласно настройке `Hidden`.

## Полный, исполняемый пример

Объединив все шаги, вы получаете автономную программу, которую можно скопировать, скомпилировать и запустить.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShowShapeExample
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first shape in the document
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found. Exiting.");
            return;
        }

        // 3. Toggle the Hidden property
        // Hide the shape
        shape.Hidden = true;
        // To show the shape again, uncomment the following line:
        // shape.Hidden = false;

        // 4. Save the modified document
        doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");

        Console.WriteLine("Document saved. Shape hidden = " + shape.Hidden);
    }
}
```

**Ожидаемый вывод** при запуске программы:

```
Document saved. Shape hidden = True
```

Открытие `ShapeHidden.docx` в Microsoft Word показывает документ без целевого объекта. Если перед сохранением установить `shape.Hidden = false;`, объект появится снова.

## Обработка нескольких объектов

Приведённый выше пример работает с одним объектом. В реальных документах часто встречается множество графических элементов. Используйте цикл, чтобы скрыть или показать все объекты, удовлетворяющие условию (например, определённому имени или типу).

```csharp
// Hide every picture shape in the document
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Image)
    {
        s.Hidden = true; // hide picture
    }
}
doc.Save("YOUR_DIRECTORY/AllPicturesHidden.docx");
```

*Подсказка*: Фильтрация по `ShapeType` помогает избежать случайного скрытия декоративных элементов, таких как текстовые поля или SmartArt.

## Пограничные случаи и лучшие практики

| Ситуация | Рекомендуемое решение |
|-----------|----------------------|
| **Объект находится в колонтитуле/нижнем колонтитуле** | Сначала получите узел колонтитула/нижнего колонтитула, затем вызовите `GetChild(NodeType.Shape, …)` на этом поддокументе. |
| **Документ не содержит объектов** | Всегда проверяйте `null` после `GetChild` или проверяйте `doc.GetChildNodes(NodeType.Shape, true).Count`. |
| **Необходимо сохранять флаг hidden при разных версиях Word** | Свойство `Hidden` хранится в XML объекта как `<w:hidden/>`, что поддерживается в Word 2007 и более новых версиях. |
| **Производительность при работе с большими документами** | Вызовите `doc.GetChildNodes(NodeType.Shape, true)` один раз и переиспользуйте полученную коллекцию вместо многократных вызовов `GetChild`. |

## Профессиональный совет: Сочетание `Hidden` с `WrapType`

Когда объект скрыт, Word всё равно резервирует место, которое он занимал, если только вы не измените его режим обтекания. Установка `WrapType = WrapType.None` удаляет область‑заполнитель.

```csharp
shape.Hidden = true;
shape.WrapType = WrapType.None;
```

Это заставляет макет схлопнуться так, как будто объект никогда не существовал, что полезно при генерации чистых отчётов.

## Заключение

Теперь вы знаете, как **скрыть/показать объект с новым свойством `Hidden`** с помощью Aspose.Words для C#. Решение охватывает загрузку документа, поиск объекта, переключение свойства `Hidden` и сохранение изменений. Следуя рекомендациям – проверке на `null`, обработке нескольких объектов и настройке обтекания – вы сможете надёжно управлять видимостью объектов в любой автоматизации Word.

Готовы изучать дальше? Рассмотрите следующие шаги:

* **Скрыть/Показать несколько объектов** на основе пользовательских метаданных (использует технику «программного скрытия объекта»).  
* **Сочетать `Hidden` с условным содержимым** с помощью полей Aspose.Words для динамической генерации отчётов.  
* **Исследовать другие свойства узлов**, такие как `Visible` для объектов диаграмм или `IsDeleted` для управления на уровне абзаца.

Удачной разработки и наслаждайтесь тонким контролем, который предоставляет Aspose.Words для управления видимостью объектов в документах Word!

## Что изучать дальше?

Следующие учебники охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [how to hide shape in Word using C# – step-by-step guide](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-using-c-step-by-step-guide/)
- [How to Hide Shape in Word with C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-with-c-step-by-step-guide/)
- [Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}