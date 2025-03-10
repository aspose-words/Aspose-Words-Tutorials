---
title: Макет в ячейке
linktitle: Макет в ячейке
second_title: API обработки документов Aspose.Words
description: Узнайте, как настроить макет в ячейке с помощью Aspose.Words для .NET с помощью этого всеобъемлющего руководства. Идеально подходит для разработчиков, желающих настроить документы Word.
weight: 10
url: /ru/net/programming-with-shapes/layout-in-cell/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Макет в ячейке

## Введение

Если вы когда-либо хотели настроить макет ячеек таблицы в документах Word программным способом, вы попали по адресу. Сегодня мы углубимся в то, как настроить макет в ячейке с помощью Aspose.Words для .NET. Мы рассмотрим практический пример, разбив его пошагово, чтобы вы могли легко следовать инструкциям.

## Предпосылки

Прежде чем перейти к коду, давайте убедимся, что у вас есть все необходимое:

1.  Aspose.Words for .NET: Убедитесь, что у вас установлена библиотека Aspose.Words for .NET. Если у вас ее нет, вы можете[скачать здесь](https://releases.aspose.com/words/net/).
2. Среда разработки: Вам понадобится среда разработки, настроенная на .NET. Visual Studio — отличный выбор, если вы ищете рекомендации.
3. Базовые знания C#: хотя я и объясню каждый шаг, базовые знания C# помогут вам легче следовать курсу.
4.  Каталог документов: Подготовьте путь к каталогу, в котором вы будете сохранять свои документы. Мы будем называть это`YOUR DOCUMENT DIRECTORY`.

## Импорт пространств имен

Для начала убедитесь, что вы импортируете необходимые пространства имен в свой проект:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Давайте разобьем процесс на управляемые этапы.

## Шаг 1: Создайте новый документ

 Сначала мы создадим новый документ Word и инициализируем`DocumentBuilder` объект, помогающий нам конструировать наш контент.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Шаг 2: Создайте таблицу и задайте формат строк

Начнем с построения таблицы и укажем высоту и правило высоты для строк.

```csharp
builder.StartTable();
builder.RowFormat.Height = 100;
builder.RowFormat.HeightRule = HeightRule.Exactly;
```

## Шаг 3: Вставьте ячейки и заполните их содержимым

Далее мы циклим, чтобы вставить ячейки в таблицу. Для каждых 7 ячеек мы будем заканчивать строку, чтобы создать новую.

```csharp
for (int i = 0; i < 31; i++)
{
    if (i != 0 && i % 7 == 0) builder.EndRow();
    builder.InsertCell();
    builder.Write("Cell contents");
}
builder.EndTable();
```

## Шаг 4: Добавьте форму водяного знака

 Теперь давайте добавим водяной знак в наш документ. Мы создадим`Shape` объект и задать его свойства.

```csharp
Shape watermark = new Shape(doc, ShapeType.TextPlainText)
{
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    RelativeVerticalPosition = RelativeVerticalPosition.Page,
    IsLayoutInCell = true, // Отобразить фигуру за пределами ячейки таблицы, если она будет помещена в ячейку.
    Width = 300,
    Height = 70,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    Rotation = -40
};
```

## Шаг 5: Настройте внешний вид водяного знака

Мы дополнительно настроим внешний вид водяного знака, задав его цвет и текстовые свойства.

```csharp
watermark.FillColor = Color.Gray;
watermark.StrokeColor = Color.Gray;
watermark.TextPath.Text = "watermarkText";
watermark.TextPath.FontFamily = "Arial";
watermark.Name = $"WaterMark_{Guid.NewGuid()}";
watermark.WrapType = WrapType.None;
```

## Шаг 6: Вставьте водяной знак в документ

Мы найдем последний фрагмент в документе и вставим водяной знак в эту позицию.

```csharp
Run run = doc.GetChildNodes(NodeType.Run, true)[doc.GetChildNodes(NodeType.Run, true).Count - 1] as Run;
builder.MoveTo(run);
builder.InsertNode(watermark);
```

## Шаг 7: Оптимизация документа для Word 2010

Для обеспечения совместимости мы оптимизируем документ для Word 2010.

```csharp
doc.CompatibilityOptions.OptimizeFor(MsWordVersion.Word2010);
```

## Шаг 8: Сохраните документ.

Наконец, мы сохраним наш документ в указанном каталоге.

```csharp
doc.Save(dataDir + "WorkingWithShapes.LayoutInCell.docx");
```

## Заключение

И вот оно! Вы успешно создали документ Word с настроенной табличной компоновкой и добавили водяной знак с помощью Aspose.Words for .NET. Цель этого руководства — предоставить четкое пошаговое руководство, которое поможет вам понять каждую часть процесса. С этими навыками вы теперь можете создавать более сложные и настроенные документы Word программным путем.

## Часто задаваемые вопросы

### Могу ли я использовать другой шрифт для текста водяного знака?
 Да, вы можете изменить шрифт, установив`watermark.TextPath.FontFamily` свойство нужного вам шрифта.

### Как настроить положение водяного знака?
 Вы можете изменить`RelativeHorizontalPosition`, `RelativeVerticalPosition`, `HorizontalAlignment` , и`VerticalAlignment` свойства для настройки положения водяного знака.

### Можно ли использовать изображение вместо текста для водяного знака?
 Конечно! Вы можете создать`Shape` с типом`ShapeType.Image` и установите его изображение с помощью`ImageData.SetImage` метод.

### Можно ли создавать таблицы с разной высотой строк?
Да, вы можете установить разную высоту для каждого ряда, изменив`RowFormat.Height` свойство перед вставкой ячеек в эту строку.

### Как удалить водяной знак из документа?
 Вы можете удалить водяной знак, найдя его в коллекции фигур документа и вызвав`Remove` метод.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
