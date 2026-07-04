---
category: general
date: 2026-05-26
description: Создание документа Word на C# с помощью Aspose.Words, вставка прямоугольной
  формы, установка цвета заливки и добавление эффекта тени — пошаговое руководство.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- how to set fill
language: ru
og_description: Создайте документ Word на C# с помощью Aspose.Words. Узнайте, как
  вставить прямоугольную форму, задать её цвет заливки и добавить эффект тени.
og_title: Создать документ Word – вставить прямоугольную форму и тень в C#
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create Word document in C# with Aspose.Words, insert rectangle shape,
    set fill color, and add shadow effect – step‑by‑step guide.
  headline: Create Word Document – Insert Rectangle Shape & Shadow in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Создать документ Word – вставить прямоугольную форму и тень в C#
url: /ru/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание документа Word – вставка прямоугольной формы и тени в C#

Задумывались ли вы когда‑нибудь, как **создать документ Word** программно, не открывая Microsoft Word? Вы не одиноки. Во многих сценариях автоматизации — подумайте о счетах‑фактурах, контрактах или массовой генерации отчетов — вам нужен надёжный способ создать файл .docx, добавить в него форму, задать ей цвет и, возможно, тень для более профессионального вида.

В этом руководстве мы пошагово покажем, как использовать Aspose.Words for .NET для **создания документа Word**, **вставки прямоугольной формы**, применения заливки и **добавления тени**. К концу вы получите готовый к сохранению файл, который можно передать в любой последующий процесс.

Мы также коснёмся **как вставить форму** гибким способом и почему **как задать заливку** важно для визуальной согласованности. Без лишних слов — только код, который можно скопировать‑вставить и запустить.

## Необходимые условия

Прежде чем начать, убедитесь, что у вас есть:

- .NET 6+ (или .NET Framework 4.7+) установлен.
- Действительная лицензия Aspose.Words for .NET (или временный оценочный ключ).
- Visual Studio, Rider или любой другой IDE для C#.
- Базовое знакомство с синтаксисом C# — ничего сложного не требуется.

Есть всё? Отлично, приступим.

## Шаг 1 – Создание документа Word

Первое, что нужно, — пустой объект документа. Это холст, на котором будет всё остальное.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder.
Document doc = new Document();                 // The document itself.
DocumentBuilder builder = new DocumentBuilder(doc); // Helper to add content.
```

`Document` представляет файл .docx в памяти, а `DocumentBuilder` предоставляет удобный API для вставки текста, таблиц и форм. **Создание документа Word** таким способом мгновенно — без UI, без COM‑interop, только чистый .NET.

## Шаг 2 – Вставка прямоугольной формы

Теперь, когда у нас есть документ, давайте **вставим прямоугольную форму**. Метод `InsertShape` принимает перечисление `ShapeType`, ширину и высоту (в пунктах). Мы используем прямоугольник размером 150 × 80 пунктов, что примерно соответствует 2 × 1 дюйму.

```csharp
// Step 2: Insert a rectangle shape of the desired size.
Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

За кулисами Aspose создаёт объект `Shape`, добавляет его в текущий абзац и возвращает ссылку, которую можно стилизовать. Это и есть **как вставить форму** — одна строка кода, но невероятно мощная.

## Шаг 3 – Как задать заливку

Форма без заливки невидима на белой странице. Дадим ей приятный светло‑голубой фон.

```csharp
// Step 3: Apply a fill color to make the shape visible.
shape.FillColor = System.Drawing.Color.LightBlue; // Any System.Drawing.Color works.
```

Можно также использовать градиенты, текстуры или даже заливку изображением, но сплошной цвет упрощает пример. Это демонстрирует **как задать заливку** любой созданной формы, обеспечивая ожидаемый визуальный эффект.

## Шаг 4 – Как добавить тень

Тени придают глубину и делают форму более выразительной. Aspose.Words предоставляет объект `ShadowFormat`, где можно включить видимость, выбрать цвет и точно настроить размытие, расстояние и угол.

```csharp
// Step 4: Configure the shadow effect – enable it, set color, blur, distance and angle.
shape.ShadowFormat.Visible = true;                     // Turn the shadow on.
shape.ShadowFormat.Color = System.Drawing.Color.Gray; // Shadow color.
shape.ShadowFormat.BlurRadius = 4.0;                  // Softness in pixels.
shape.ShadowFormat.Distance = 3.0;                    // How far the shadow is offset.
shape.ShadowFormat.Angle = 45;                        // Direction of the offset (degrees).
```

Почему именно такие значения? Угол 45° имитирует естественный свет сверху‑справа, умеренное размытие делает тень мягкой, а небольшое расстояние не позволяет форме выглядеть оторванной. Экспериментируйте — изменение угла на 135° заставит тень падать вниз‑влево, например.

## Шаг 5 – Сохранение документа

Вся работа завершена; теперь запишем файл на диск. Выберите любой путь, но убедитесь, что папка существует.

```csharp
// Step 5: Save the document with the shaped shadow.
doc.Save("YOUR_DIRECTORY/ShadowShape.docx");
```

Когда откроете `ShadowShape.docx` в Microsoft Word, вы увидите светло‑голубой прямоугольник с мягкой серой тенью — точно то, что мы запрограммировали.

## Полный рабочий пример

Объединяя всё вместе, получаем полностью готовую к копированию программу:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a rectangle shape (150 × 80 points).
        Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

        // 3️⃣ Set a solid fill color so the shape is visible.
        shape.FillColor = System.Drawing.Color.LightBlue;

        // 4️⃣ Add a subtle shadow for depth.
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.Color = System.Drawing.Color.Gray;
        shape.ShadowFormat.BlurRadius = 4.0;   // pixels
        shape.ShadowFormat.Distance = 3.0;     // pixels
        shape.ShadowFormat.Angle = 45;        // degrees

        // 5️⃣ Persist the document.
        doc.Save("ShadowShape.docx");
    }
}
```

### Ожидаемый результат

- Файл с именем **ShadowShape.docx** появляется в указанной папке.
- При открытии в Word отображается светло‑голубой прямоугольник, центрированный на первой странице.
- Прямоугольник отбрасывает серую тень под углом 45°, создавая лёгкий 3‑D эффект.

## Часто задаваемые вопросы и особые случаи

**Что делать, если нужна другая форма?**  
Замените `ShapeType.Rectangle` на любое другое значение перечисления (`Ellipse`, `Star`, `Arrow` и т.д.). Остальная часть кода остаётся без изменений.

**Можно ли добавить текст внутри формы?**  
Да — после создания формы вызовите `shape.AppendChild(new Paragraph(doc))`, а затем вставьте `Run` с нужным текстом. Не забудьте настроить свойства `shape.TextBox`, если требуется обтекание.

**Как насчёт DPI или единиц измерения?**  
Aspose работает в пунктах (1 pt = 1/72 дюйма). Если предпочитаете сантиметры, умножайте на 28.35 (поскольку 1 см ≈ 28.35 pt).

**Нужна ли лицензия для работы?**  
Оценочная версия добавляет водяной знак на первую страницу. Полноценная лицензия убирает его и открывает весь API.

## Советы и подводные камни

- **Pro tip:** Вызовите `builder.MoveToDocumentEnd()` перед вставкой формы, если хотите разместить её в самом конце документа.
- **Осторожно:** Сохранение в папку только для чтения вызовет `UnauthorizedAccessException`. Убедитесь, что приложение имеет права записи.
- **Заметка о производительности:** При массовой генерации (сотни документов) переиспользуйте один экземпляр `Document` как шаблон и клонируйте его с помощью `doc.Clone(true)`, чтобы избежать повторных затрат на инициализацию.

## Заключение

Теперь вы знаете, как **создать документ Word**, **вставить прямоугольную форму**, **задать заливку** и **добавить тень** с помощью Aspose.Words for .NET. Приведённый фрагмент кода — автономное решение, которое можно внедрить в любой проект C#, будь то консольное приложение, веб‑API или фоновая служба.

Дальше вы можете исследовать:

- Добавление нескольких форм с разными цветами.
- Использование градиентов или заливки изображениями (`shape.FillColor = ...` → `shape.FillPattern`).
- Комбинирование форм с таблицами для сложных макетов отчётов.

Попробуйте, поиграйте с параметрами и наблюдайте, как ваши автоматизированные файлы Word становятся более профессиональными всего лишь несколькими строками кода. Приятного кодинга!

## Связанные руководства

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}