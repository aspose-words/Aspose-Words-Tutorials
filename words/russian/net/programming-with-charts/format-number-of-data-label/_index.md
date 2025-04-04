---
title: Форматировать число меток данных на диаграмме
linktitle: Форматировать число меток данных на диаграмме
second_title: API обработки документов Aspose.Words
description: Узнайте, как форматировать метки данных в диаграммах с помощью Aspose.Words для .NET с помощью этого пошагового руководства. Улучшайте свои документы Word без усилий.
weight: 10
url: /ru/net/programming-with-charts/format-number-of-data-label/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Форматировать число меток данных на диаграмме

## Введение

Создание интересных и информативных документов часто подразумевает включение диаграмм с хорошо отформатированными метками данных. Если вы разработчик .NET, который хочет улучшить свои документы Word с помощью сложных диаграмм, Aspose.Words для .NET — фантастическая библиотека, которая поможет вам в этом. Это руководство проведет вас через процесс форматирования числовых меток в диаграмме с помощью Aspose.Words для .NET, шаг за шагом.

## Предпосылки

Прежде чем погрузиться в код, необходимо выполнить несколько предварительных условий:

-  Aspose.Words for .NET: Убедитесь, что у вас установлена библиотека Aspose.Words for .NET. Если вы еще не установили ее, вы можете[скачать здесь](https://releases.aspose.com/words/net/).
- Среда разработки: у вас должна быть настроена среда разработки .NET. Настоятельно рекомендуется Visual Studio.
- Базовые знания C#: знакомство с программированием на C# необходимо, поскольку это руководство подразумевает написание и понимание кода C#.
-  Временная лицензия: Чтобы использовать Aspose.Words без каких-либо ограничений, вы можете получить[временная лицензия](https://purchase.aspose.com/temporary-license/).

Теперь давайте рассмотрим пошаговый процесс форматирования числовых меток в диаграмме.

## Импорт пространств имен

Первым делом нам нужно импортировать необходимые пространства имен для работы с Aspose.Words для .NET. Добавьте следующие строки в начало вашего файла C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Шаг 1: Настройте каталог документов

Прежде чем вы сможете начать работать с документом Word, вам необходимо указать каталог, в котором будет сохранен ваш документ. Это необходимо для операции сохранения в дальнейшем.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Заменять`"YOUR DOCUMENT DIRECTORY"` с фактическим путем к каталогу ваших документов.

## Шаг 2: Инициализация документа и DocumentBuilder

 Следующий шаг — инициализация нового`Document` и а`DocumentBuilder` .`DocumentBuilder` — вспомогательный класс, позволяющий нам конструировать содержимое документа.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Шаг 3: Вставьте диаграмму в документ

 Теперь давайте вставим диаграмму в документ с помощью`DocumentBuilder`В этом уроке мы будем использовать линейный график в качестве примера.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
chart.Title.Text = "Data Labels With Different Number Format";
```

Здесь мы вставляем линейную диаграмму с определенной шириной и высотой и задаем заголовок диаграммы.

## Шаг 4: Очистите серию по умолчанию и добавьте новую серию

По умолчанию диаграмма будет иметь некоторые предварительно сгенерированные ряды. Нам нужно очистить их и добавить наши собственные ряды с определенными точками данных.

```csharp
// Удалить созданную по умолчанию серию.
chart.Series.Clear();

// Добавьте новые ряды с пользовательскими точками данных.
ChartSeries series1 = chart.Series.Add("Aspose Series 1", 
	new string[] { "Category 1", "Category 2", "Category 3" }, 
	new double[] { 2.5, 1.5, 3.5 });
```

## Шаг 5: Включите метки данных

Чтобы отобразить метки данных на диаграмме, нам необходимо включить их для нашей серии.

```csharp
series1.HasDataLabels = true;
series1.DataLabels.ShowValue = true;
```

## Шаг 6: Форматирование меток данных

Суть этого руководства — форматирование меток данных. Мы можем применять различные числовые форматы к каждой метке данных по отдельности.

```csharp
series1.DataLabels[0].NumberFormat.FormatCode = "\"$\"#,##0.00"; // Формат валюты
series1.DataLabels[1].NumberFormat.FormatCode = "dd/mm/yyyy"; // Формат даты
series1.DataLabels[2].NumberFormat.FormatCode = "0.00%"; // Процентный формат
```

 Кроме того, вы можете связать формат метки данных с исходной ячейкой. При связывании`NumberFormat` будут сброшены до общих и унаследованы от исходной ячейки.

```csharp
series1.DataLabels[2].NumberFormat.IsLinkedToSource = true;
```

## Шаг 7: Сохраните документ.

Наконец, сохраните документ в указанном каталоге.

```csharp
doc.Save(dataDir + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

Это сохранит ваш документ под указанным именем и обеспечит сохранность вашей диаграммы с отформатированными метками данных.

## Заключение

Форматирование меток данных в диаграмме с помощью Aspose.Words for .NET может значительно повысить читабельность и профессионализм ваших документов Word. Следуя этому пошаговому руководству, вы теперь сможете создать диаграмму, добавить ряд данных и отформатировать метки данных в соответствии со своими потребностями. Aspose.Words for .NET — это мощный инструмент, который позволяет выполнять обширную настройку и автоматизацию документов Word, что делает его бесценным активом для разработчиков .NET.

## Часто задаваемые вопросы

### Что такое Aspose.Words для .NET?
Aspose.Words для .NET — мощная библиотека для программного создания, обработки и преобразования документов Word с использованием C#.

### Могу ли я форматировать другие типы диаграмм с помощью Aspose.Words для .NET?
Да, Aspose.Words для .NET поддерживает различные типы диаграмм, включая линейчатые, столбчатые, круговые и другие.

### Как получить временную лицензию на Aspose.Words для .NET?
Вы можете получить временную лицензию[здесь](https://purchase.aspose.com/temporary-license/).

### Можно ли связать метки данных с исходными ячейками в Excel?
Да, вы можете связать метки данных с исходными ячейками, что позволит унаследовать числовой формат от исходной ячейки.

### Где я могу найти более подробную документацию по Aspose.Words для .NET?
 Вы можете найти полную документацию[здесь](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
