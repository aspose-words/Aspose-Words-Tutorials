---
category: general
date: 2026-09-11
description: Учебник по редактированию подписей диаграммы, показывающий, как изменить
  положение подписи диаграммы, настроить подпись данных, скрыть название категории
  и отобразить значение подписи с помощью Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit chart label tutorial
- change chart label position
- customize chart data label
- hide chart category name
- show chart label value
language: ru
lastmod: 2026-09-11
og_description: Учебник по редактированию подписей диаграммы проводит вас через изменение
  положения подписи диаграммы, настройку подписи данных, скрытие названия категории
  диаграммы и отображение значения подписи, используя Aspose.Words для .NET.
og_image_alt: Screenshot of a Word document displaying a chart with customized data
  labels
og_title: Учебник по редактированию подписей диаграммы — настройка подписей диаграмм
  Word в C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Edit chart label tutorial showing how to change chart label position,
    customize chart data label, hide chart category name, and show chart label value
    with Aspose.Words.
  headline: Edit chart label tutorial – modify Word chart labels in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart manipulation
title: Учебник по редактированию подписей диаграммы — изменение подписей диаграмм
  Word в C#
url: /ru/net/programming-with-charts/edit-chart-label-tutorial-modify-word-chart-labels-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Руководство по редактированию подписей диаграммы – изменение подписей диаграмм Word в C#

Если вам нужно **edit chart label tutorial** для документа Word, это руководство покажет, как изменить позицию подписи диаграммы, настроить подпись данных диаграммы, скрыть название категории диаграммы и отобразить значение подписи диаграммы с помощью Aspose.Words for .NET. Вы увидите полный, готовый к запуску пример, который можно вставить в любой проект C#.

Работа с подписями диаграмм часто требуется при программной генерации отчетов, счетов или панелей мониторинга. Это руководство охватывает каждый шаг — от загрузки документа до сохранения изменений — чтобы вы могли создавать отшлифованные диаграммы без ручного редактирования.

## Требования

* .NET 6.0 или новее установлен  
* Действительная лицензия Aspose.Words for .NET (или временный оценочный ключ)  
* Visual Studio 2022 или любая IDE, совместимая с C#  
* Файл Word (`Chart.docx`), содержащий как минимум одну диаграмму  

Дополнительные пакеты NuGet не требуются, кроме `Aspose.Words`.

## Шаг 1: Настройка проекта и импорт пространств имён

Создайте новое консольное приложение и добавьте пакет Aspose.Words через NuGet:

```bash
dotnet new console -n ChartLabelEditor
cd ChartLabelEditor
dotnet add package Aspose.Words
```

Откройте `Program.cs` и импортируйте необходимые пространства имён:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
```

Эти пространства имён дают доступ к классу `Document` для работы с файлами Word и к классам `Chart` для манипуляций элементами диаграмм.

## Шаг 2: Загрузка документа Word, содержащего диаграмму

Первая исполняемая строка загружает исходный документ. Замените `YOUR_DIRECTORY` фактическим путём, где находится `Chart.docx`.

```csharp
// Load the Word document containing the chart
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");
```

Загрузка документа создаёт представление в памяти, которое можно обходить и изменять.

## Шаг 3: Получение первой диаграммы в документе

Диаграммы хранятся как дочерние узлы типа `NodeType.Chart`. Метод `GetChild` ищет в дереве документа и возвращает диаграмму, которую нужно отредактировать.

```csharp
// Retrieve the first chart object (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

Если в документе несколько диаграмм, измените индекс, чтобы обратиться к другой.

## Шаг 4: Доступ и настройка подписи данных первой серии

Каждая серия диаграммы имеет объект `DataLabel`, управляющий отображением подписи. Ниже показан код, демонстрирующий четыре ключевых настройки, требуемые вторичными ключевыми словами руководства.

```csharp
// Access the data label of the first series (index 0)
ChartDataLabel label = chart.Series[0].DataLabel;

// Change chart label position – place the label in the center of each data point
label.Position = DataLabelPosition.Center;

// Customize chart data label – use a custom separator between label parts
label.Separator = "; ";

// Hide chart category name – the category text will not be shown
label.ShowCategoryName = false;

// Show chart label value – the numeric value of the point will be displayed
label.ShowValue = true;
```

**Почему эти настройки важны**

* `DataLabelPosition.Center` перемещает подпись из положения по умолчанию вне точки в центр точки данных, делая диаграмму легче читаемой, когда точки плотно расположены.  
* Установка пользовательского `Separator` позволяет контролировать, как объединяются название серии, значение и другие части.  
* Скрытие названия категории (`ShowCategoryName = false`) уменьшает визуальный шум, когда категория уже очевидна по оси.  
* Включение `ShowValue` гарантирует отображение фактического значения данных, что часто требуется в финансовых или статистических отчётах.

## Шаг 5: Сохранение изменённого документа

После настройки свойств подписи сохраните изменения в новый файл:

```csharp
// Save the updated document with customized chart labels
doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");
```

Новый файл (`CustomLabelChart.docx`) содержит тот же макет диаграммы, но с изменённым видом подписи.

## Полный исходный код

Ниже приведена полная, готовая к запуску программа. Скопируйте её в `Program.cs`, скорректируйте пути к файлам и запустите проект.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the Word document that contains a chart
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label of the first series
            ChartDataLabel label = chart.Series[0].DataLabel;

            // 4️⃣ Customize the label appearance
            label.Position = DataLabelPosition.Center;   // change chart label position
            label.Separator = "; ";                      // customize chart data label
            label.ShowValue = true;                      // show chart label value
            label.ShowCategoryName = false;              // hide chart category name

            // 5️⃣ Save the modified document
            doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");

            Console.WriteLine("Chart label customization complete.");
        }
    }
}
```

### Ожидаемый результат

Откройте `CustomLabelChart.docx` в Microsoft Word. Вы должны увидеть подпись первой серии диаграммы, центрированную на каждой точке данных, отображающую только числовое значение и использующую «; » в качестве разделителя. Названия категорий больше не будут отображаться рядом со значениями.

## Часто задаваемые вопросы и особые случаи

| Вопрос | Ответ |
|----------|--------|
| **Что если документ не содержит диаграмм?** | Пример проверяет, является ли диаграмма `null`, и при отсутствии диаграммы корректно завершает работу с сообщением в консоли. |
| **Могу ли я редактировать подписи для нескольких серий?** | Да. Пройдитесь в цикле по `chart.Series` и примените те же настройки `DataLabel` к каждому `Series[i].DataLabel`. |
| **Как изменить стиль шрифта подписи?** | Используйте `label.Font` (например, `label.Font.Size = 10; label.Font.Color = Color.Blue;`). |
| **Поддерживается ли `DataLabelPosition.Center` для всех типов диаграмм?** | Большинство 2‑D типов диаграмм поддерживают его. Для 3‑D диаграмм некоторые позиции могут игнорироваться Word. |
| **Нужна ли лицензия для Aspose.Words?** | Режим оценки работает, но добавляет водяной знак. Лицензия удаляет водяной знак и открывает полный набор функций. |

## Профессиональные советы

* **Пакетная обработка:** Оберните логику загрузки и сохранения в метод, принимающий пути ввода и вывода. Это упрощает обработку десятков документов в цикле.  
* **Производительность:** Переиспользуйте один экземпляр `Document` при изменении нескольких диаграмм в одном файле, чтобы избежать повторных операций ввода‑вывода.  
* **Тестирование:** Проверяйте изменения подписи, автоматизируя визуальное сравнение (например, с помощью безголового просмотрщика Word), если необходимо проверять вывод в CI‑конвейерах.

## Следующие шаги

Теперь, когда вы освоили основы **edit chart label tutorial**, рассмотрите возможность изучения:

* **Изменить позицию подписи диаграммы** для других серий или разных типов диаграмм  
* **Настроить форматирование подписи данных диаграммы**: числовые форматы, цвета шрифта или заливку фона  
* **Скрыть название категории диаграммы** при сохранении названия серии для многосерийных диаграмм  
* **Отобразить значение подписи диаграммы** вместе с процентными значениями для круговых диаграмм  

Эти темы углубят ваш контроль над эстетикой диаграмм Word и подготовят к продвинутым сценариям отчётности.

---

*Счастливого кодинга! Если это руководство оказалось полезным, поделитесь им с коллегами или внесите улучшения на GitHub.*

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в собственных проектах.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Chart Data Label](/words/german/net/programming-with-charts/chart-data-label/)
- [Chart Data Label](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}