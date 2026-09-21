---
category: general
date: 2026-09-21
description: Создайте пустой документ Word со скрытым эллипсом с помощью C#. Узнайте,
  как скрыть фигуру в Word и программно создать скрытую фигуру.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create ellipse
- hide shape in word
- create hidden shape
language: ru
lastmod: 2026-09-21
og_description: Создайте пустой документ Word со скрытым эллипсом с помощью C#. Это
  руководство показывает, как скрыть фигуру в Word и программно создавать скрытые
  фигуры.
og_image_alt: Screenshot of a blank Word document that contains a hidden ellipse shape
  created with C#
og_title: Создать пустой документ Word со скрытой эллиптической фигурой в C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document with a hidden ellipse using C#. Learn how
    to hide shape in Word and generate a hidden shape programmatically.
  headline: How to create blank Word document and add a hidden ellipse shape in C#
  type: TechArticle
- questions:
  - answer: The shape’s XML adds a few hundred bytes, which is negligible for most
      use cases. The file remains essentially the same size as a truly empty document.
    question: Does hiding a shape affect document size?
  - answer: Yes. Load the document, locate the shape (`doc.GetChildNodes(NodeType.Shape,
      true)`), and set `shape.Hidden = false`.
    question: Can I unhide the shape later programmatically?
  - answer: No. Hidden objects are excluded from the print layout, so the printed
      page stays blank.
    question: Will the hidden shape appear when printing?
  - answer: 'The `Hidden` property is part of the OOXML spec, so any Word processor
      that fully implements OOXML (Word, LibreOffice, Google Docs) will respect the
      hidden flag. --- ## Conclusion You now know how to **create blank Word document**,
      **how to create ellipse**, **hide shape in Word**, and **create hidd'
    question: Is this approach compatible with Office Open XML (OOXML) only?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: Как создать пустой документ Word и добавить скрытый эллипс в C#
url: /ru/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать пустой документ Word и добавить скрытую форму эллипса в C#

Если вам нужно **создать пустой документ Word**, содержащий невидимую графику, это руководство покажет вам, как это сделать. К концу урока у вас будет файл .docx, который выглядит пустым, но на самом деле хранит форму эллипса, скрытую от разметки.

Мы будем использовать Aspose.Words for .NET для создания документа, вставки эллипса, его скрытия и сохранения файла. Шаги также охватывают **как создать эллипс** объекты, правильный способ **скрыть форму в Word**, и как **создать скрытую форму** код, который работает с любым проектом .NET.

## Предварительные требования

* .NET 6.0 SDK или более поздняя версия установлен  
* Visual Studio 2022 (или любой редактор C#)  
* Лицензия Aspose.Words for .NET или бесплатная оценочная копия  
* Базовое знакомство с синтаксисом C#  

Дополнительные пакеты NuGet не требуются, кроме `Aspose.Words`.

## Создание пустого документа Word с помощью Aspose.Words

Первый шаг — создать пустой файл Word. Это дает нам чистый холст, куда мы позже сможем вставить скрытую графику.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();

        // The document is currently empty – it contains no paragraphs or shapes.
        // This is the foundation for all further operations.
```

**Почему мы начинаем с пустого документа** – Начало с пустого файла гарантирует, что никакое нежелательное содержимое не будет мешать скрытой форме. Это также сохраняет минимальный размер файла, что полезно, когда документ позже используется как шаблон.

## Как создать эллипс внутри пустого документа

Далее нам нужен `DocumentBuilder` для добавления содержимого. Builder позволяет точно разместить формы там, где мы хотим.

```csharp
        // Step 2: Initialize a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert an ellipse shape (width: 100 points, height: 50 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

        // The ellipse now exists on the page, but it is visible by default.
```

**Объяснение** – `ShapeType.Ellipse` сообщает Aspose.Words нарисовать почти круглую фигуру. Ширина и высота измеряются в пунктах (1 pt ≈ 1/72 дюйма). Вы можете настроить эти значения под свои дизайнерские требования.

## Скрыть форму в Word, чтобы она не отображалась в разметке

Форма, которая скрыта, всё равно присутствует в XML документа, что может быть полезно для метаданных, условного форматирования или последующих программных модификаций. Чтобы скрыть её, мы устанавливаем свойство `Hidden` в `true`.

```csharp
        // Step 4: Hide the shape so it does not appear in the layout
        ellipse.Hidden = true;

        // When Hidden = true, Word treats the shape as if it were not there.
        // The shape remains in the document’s DOM, allowing you to retrieve or modify it later.
```

**Почему скрывать форму** – Скрытые формы игнорируются движком разметки, поэтому страница выглядит полностью пустой. Однако данные формы сохраняются, что может быть полезно для хранения маркеров, закладок или пользовательского XML, который могут читать последующие процессы.

## Сохранить документ со скрытой формой

Наконец мы записываем файл на диск. Сохранённый `.docx` откроется в Microsoft Word без видимого содержимого, однако скрытый эллипс всё ещё присутствует.

```csharp
        // Step 5: Save the document with the hidden shape
        doc.Save(@"C:\Temp\HiddenEllipse.docx");

        // The file now contains a hidden ellipse and appears empty when opened.
    }
}
```

**Проверка** – Откройте сгенерированный файл в Word, затем нажмите `Alt+F9`, чтобы переключить отображение полей, и `Ctrl+A` → `Ctrl+Shift+F9`, чтобы увидеть скрытые объекты. Вы увидите эллипс в XML документа (`word/document.xml`), но ничего на странице не будет.

---

## Полный, исполняемый пример

Ниже приведена полная программа, которую вы можете скопировать и вставить в новый консольный проект. Она включает все директивы `using` и метод `Main`, чтобы вы могли запустить её без дополнительной инфраструктуры.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank Word document
            Document doc = new Document();

            // 2️⃣ Prepare a builder to insert content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse (100 pt × 50 pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the ellipse so the page stays empty
            ellipse.Hidden = true;

            // 5️⃣ Save the file
            string outPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outPath);

            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Ожидаемый вывод** – Когда вы запустите программу, консоль выведет путь к файлу, а полученный файл Word не будет содержать видимых объектов. Если вы исследуете документ с помощью zip‑утилиты (`.docx` — это zip‑архив), вы найдёте элемент `<w:pict>`, описывающий эллипс внутри `word/document.xml`.

---

## Общие варианты и граничные случаи

| Сценарий | Что изменить | Почему это важно |
|----------|--------------|------------------|
| **Разная форма** | Замените `ShapeType.Ellipse` на `ShapeType.Rectangle`, `ShapeType.Line` и т.д. | Позволяет скрывать другие графические элементы, сохраняя тот же рабочий процесс. |
| **Несколько скрытых форм** | Вызовите `InsertShape` несколько раз и установите `Hidden = true` для каждой. | Полезно для встраивания набора маркеров или заполнителей. |
| **Условная видимость** | Используйте `shape.Visible = false` вместе с `shape.Hidden = true` для дополнительной безопасности. | Некоторые старые версии Word по‑разному обрабатывают `Visible`; установка обоих покрывает все случаи. |
| **Сохранение в поток** | Замените `doc.Save(path)` на `doc.Save(stream, SaveFormat.Docx)`. | Позволяет отправлять документ напрямую по HTTP или сохранять его в базе данных. |
| **Применение стиля** | После вставки измените `ellipse.FillColor`, `ellipse.LineWeight` и т.д. перед скрытием. | Стилизация формы сохраняется в XML, что может быть полезно для последующего раскрытия. |

**Совет профессионала:** Всегда тестируйте скрытую форму в целевой версии Word (например, Word 2019, Word 365), потому что иногда возникают особенности рендеринга, когда скрытые объекты взаимодействуют со сложными макетами страниц.

---

## Часто задаваемые вопросы

**В: Влияет ли скрытие формы на размер документа?**  
**О:** XML формы добавляет несколько сотен байт, что несущественно для большинства случаев. Файл остаётся практически того же размера, что и действительно пустой документ.

**В: Могу ли я позже программно раскрыть форму?**  
**О:** Да. Загрузите документ, найдите форму (`doc.GetChildNodes(NodeType.Shape, true)`) и установите `shape.Hidden = false`.

**В: Появится ли скрытая форма при печати?**  
**О:** Нет. Скрытые объекты исключаются из печатной разметки, поэтому печатная страница остаётся пустой.

**В: Совместим ли этот подход только с Office Open XML (OOXML)?**  
**О:** Свойство `Hidden` является частью спецификации OOXML, поэтому любой процессор Word, полностью реализующий OOXML (Word, LibreOffice, Google Docs), будет учитывать флаг скрытия.

---

## Заключение

Теперь вы знаете, как **создать пустой документ Word**, **создать эллипс**, **скрыть форму в Word** и **создать скрытую форму** с помощью Aspose.Words for .NET. Руководство охватило весь жизненный цикл — от инициализации пустого файла до вставки, скрытия и сохранения формы — а также шаги проверки и общие варианты.

Далее вы можете изучить:

* Добавление скрытых текстовых полей для метаданных (техника `hide shape in word`, применённая к тексту)  
* Использование пользовательских XML‑частей для хранения структурированных данных вместе со скрытыми формами  
* Преобразование документа со скрытой формой в PDF с сохранением скрытых элементов  

Экспериментируйте с различными формами и настройками видимости, чтобы увидеть, как скрытое содержимое может служить лёгким хранилищем данных внутри файлов Word.

Удачной разработки!

## Что вам стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, которые опираются на техники, продемонстрированные в этом руководстве. Каждый ресурс включает полные работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with a Shadowed Rectangle – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}