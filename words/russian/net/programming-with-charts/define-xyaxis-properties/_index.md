---
"description": "Узнайте, как определить свойства оси XY в диаграмме с помощью Aspose.Words для .NET с помощью этого пошагового руководства. Идеально подходит для разработчиков .NET."
"linktitle": "Определить свойства оси XY на диаграмме"
"second_title": "API обработки документов Aspose.Words"
"title": "Определить свойства оси XY на диаграмме"
"url": "/ru/net/programming-with-charts/define-xyaxis-properties/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Определить свойства оси XY на диаграмме

## Введение

Диаграммы — мощный инструмент для визуализации данных. Когда вам нужно создавать профессиональные документы с динамическими диаграммами, Aspose.Words for .NET — бесценная библиотека. В этой статье вы узнаете о процессе определения свойств осей XY в диаграмме с помощью Aspose.Words for .NET, разбив каждый шаг на части, чтобы обеспечить ясность и простоту понимания.

## Предпосылки

Прежде чем приступить к кодированию, необходимо выполнить несколько предварительных условий:

1. Aspose.Words for .NET: Убедитесь, что у вас есть библиотека Aspose.Words for .NET. Вы можете [скачать здесь](https://releases.aspose.com/words/net/).
2. Среда разработки: вам понадобится интегрированная среда разработки (IDE), например Visual Studio.
3. .NET Framework: убедитесь, что ваша среда разработки настроена для разработки .NET.
4. Базовые знания C#: это руководство предполагает, что у вас есть базовые знания программирования на C#.

## Импорт пространств имен

Для начала вам нужно импортировать необходимые пространства имен в ваш проект. Это гарантирует вам доступ ко всем классам и методам, необходимым для создания и управления документами и диаграммами.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

Мы разобьем процесс на простые шаги, каждый из которых будет посвящен определенной части определения свойств оси XY на диаграмме.

## Шаг 1: Инициализация документа и DocumentBuilder

Сначала вам нужно инициализировать новый документ и `DocumentBuilder` объект. `DocumentBuilder` помогает вставлять содержимое в документ.

```csharp
// Путь к каталогу ваших документов 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Шаг 2: Вставьте диаграмму

Далее вы вставите диаграмму в документ. В этом примере мы будем использовать диаграмму Area. Вы можете настроить размеры диаграммы по мере необходимости.

```csharp
// Вставить диаграмму
Shape shape = builder.InsertChart(ChartType.Area, 432, 252);
Chart chart = shape.Chart;
```

## Шаг 3: Очистите серию по умолчанию и добавьте пользовательские данные

По умолчанию диаграмма будет иметь некоторые предопределенные серии. Мы очистим их и добавим наши пользовательские серии данных.

```csharp
chart.Series.Clear();
chart.Series.Add("Aspose Series 1",
	new DateTime[]
	{
		new DateTime(2002, 01, 01), new DateTime(2002, 06, 01), new DateTime(2002, 07, 01),
		new DateTime(2002, 08, 01), new DateTime(2002, 09, 01)
	},
	new double[] { 640, 320, 280, 120, 150 });
```

## Шаг 4: Определите свойства оси X

Теперь пришло время определить свойства оси X. Это включает в себя установку типа категории, настройку пересечения осей и настройку делений и меток.

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.CategoryType = AxisCategoryType.Category;
xAxis.Crosses = AxisCrosses.Custom;
xAxis.CrossesAt = 3; // Измеряется в единицах отображения оси Y (сотни).
xAxis.ReverseOrder = true;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
xAxis.TickLabelOffset = 200;
```

## Шаг 5: Определите свойства оси Y

Аналогичным образом вы зададите свойства для оси Y. Сюда входит настройка положения метки деления, основных и дополнительных единиц, единицы отображения и масштабирования.

```csharp
ChartAxis yAxis = chart.AxisY;
yAxis.TickLabelPosition = AxisTickLabelPosition.High;
yAxis.MajorUnit = 100;
yAxis.MinorUnit = 50;
yAxis.DisplayUnit.Unit = AxisBuiltInUnit.Hundreds;
yAxis.Scaling.Minimum = new AxisBound(100);
yAxis.Scaling.Maximum = new AxisBound(700);
```

## Шаг 6: Сохраните документ.

Наконец, сохраните документ в указанном вами каталоге. Это сгенерирует документ Word с настроенной диаграммой.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

## Заключение

Создание и настройка диаграмм в документах Word с помощью Aspose.Words for .NET становится простым, если вы понимаете необходимые шаги. Это руководство провело вас через процесс определения свойств осей XY в диаграмме, от инициализации документа до сохранения конечного продукта. С этими навыками вы сможете создавать подробные, профессионально выглядящие диаграммы, которые улучшат ваши документы.

## Часто задаваемые вопросы

### Какие типы диаграмм можно создавать с помощью Aspose.Words для .NET?
Вы можете создавать различные типы диаграмм, включая диаграммы с областями, столбчатые, линейные, круговые и другие.

### Как установить Aspose.Words для .NET?
Вы можете загрузить Aspose.Words для .NET с сайта [здесь](https://releases.aspose.com/words/net/) и следуйте предоставленным инструкциям по установке.

### Могу ли я настроить внешний вид своих диаграмм?
Да, Aspose.Words для .NET позволяет выполнять расширенную настройку диаграмм, включая цвета, шрифты и свойства осей.

### Существует ли бесплатная пробная версия Aspose.Words для .NET?
Да, вы можете получить бесплатную пробную версию. [здесь](https://releases.aspose.com/).

### Где я могу найти больше учебных пособий и документации?
Дополнительные руководства и подробную документацию вы можете найти на сайте [Страница документации Aspose.Words для .NET](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}