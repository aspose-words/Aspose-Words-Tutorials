---
category: general
date: 2026-08-20
description: Быстро добавьте линии‑выноски к круговой диаграмме в Java. Узнайте, как
  вставлять, выделять, менять цвет и подписывать сектора с помощью Chart API.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add leader lines to pie chart
- pie chart explosion Java
- set sector color Chart API
- builder.insertChart usage
- ChartType.PIE example
language: ru
lastmod: 2026-08-20
og_description: Добавьте линии‑выноски к круговой диаграмме в Java с кратким примером.
  Следуйте этому руководству, чтобы вставлять, отделять, перекрашивать и подписывать
  срезы с помощью Chart API.
og_image_alt: Screenshot showing a pie chart with an exploded slice and leader lines
  – add leader lines to pie chart
og_title: Добавьте линии‑выноски к круговой диаграмме в Java — пошаговое руководство
  по Chart API
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Add leader lines to pie chart in Java quickly. Learn to insert, explode,
    recolor, and label slices using the Chart API.
  headline: How to add leader lines to pie chart in Java with the Chart API
  type: TechArticle
tags:
- pie chart
- Java
- Chart API
- data visualization
title: Как добавить линии‑выноски к круговой диаграмме в Java с помощью Chart API
url: /ru/java/using-document-elements/how-to-add-leader-lines-to-pie-chart-in-java-with-the-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как добавить направляющие линии к круговой диаграмме в Java с помощью Chart API

Если вам нужно **добавить направляющие линии к круговой диаграмме** в Java, это руководство проведёт вас через весь процесс. Вы увидите, как вставить круговую диаграмму, «взорвать» сектор для акцента, изменить его цвет и, наконец, включить направляющие линии, которые подпишут взорванный сегмент.

В примере используется стандартный Chart API, присутствующий во многих Java‑библиотеках для отчётности. Внешние инструменты не требуются, код работает в любой среде JDK 8+.

## Что вы получите

К концу этого урока вы сможете:

* Создать `Chart` типа `ChartType.PIE` с пользовательским размером.  
* Взорвать первый сектор, чтобы привлечь внимание.  
* Установить цвет взорванного сектора в синий.  
* **Добавить направляющие линии к круговой диаграмме**, чтобы метка сектора была чётко соединена.

У вас уже должен быть Java‑проект с библиотекой Chart в classpath. Если вы используете Maven, добавьте зависимость, указанную в разделе требований.

## Требования

* Установлен JDK 8 или новее.  
* Библиотека Chart (например, `com.example.chart:chart-api:2.5.0`).  
* Базовое знакомство с классами Java и вызовами методов.

---

## Как добавить направляющие линии к круговой диаграмме

Ниже представлен полностью готовый к запуску пример, демонстрирующий каждый шаг. Код специально сделан автономным, чтобы вы могли скопировать, вставить и выполнить его без изменений.

```java
// File: AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Demonstrates adding leader lines to a pie chart in Java.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // 1️⃣ Insert a pie chart with the desired size
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 2️⃣ Pull out the first slice for emphasis (explosion)
        chart.getSeries().get(0).setExplosion(20);

        // 3️⃣ Change the color of the first slice to blue
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // 4️⃣ Show leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional: Save the chart as an image file
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart saved to pie-with-leader-lines.png");
    }
}
```

### Пояснение к каждому шагу

| Шаг | Что делает код | Почему это важно |
|------|-------------------|----------------|
| **1️⃣ Вставить круговую диаграмму** | `builder.insertChart(ChartType.PIE, 400, 300)` создаёт круговую диаграмму размером 400 × 300 пикселей. | Определяет контейнер диаграммы и её размеры, что влияет на размещение меток и длину направляющих линий. |
| **2️⃣ Взорвать первый сектор** | `setExplosion(20)` смещает сектор на 20 % от радиуса. | Взорванный сектор привлекает взгляд и делает направляющую линию видимой. |
| **3️⃣ Установить цвет сектора** | `setSectorColor(Color.BLUE)` меняет заливку сектора на синий. | Контраст цвета улучшает читаемость, особенно когда сектор выделен. |
| **4️⃣ Включить направляющие линии** | `setLeaderLines(true)` включает соединительные линии, связывающие сектор с его меткой. | Направляющие линии обеспечивают читаемость метки, даже если сектор вынесен наружу. |

Вызов `saveAsPng` необязателен, но полезен для проверки визуального результата. После выполнения программы вы должны увидеть изображение, похожее на показанное ниже.

![Add leader lines to pie chart](https://example.com/assets/pie-leader-lines.png "Add leader lines to pie chart – exploded slice with blue color and leader lines")

*Рисунок: Круговая диаграмма, где первый сектор взорван, окрашен в синий и соединён с меткой направляющей линией.*

## Настройка направляющих линий (расширенно)

Базовый вызов `setLeaderLines(true)` использует стиль по умолчанию библиотеки. Вы можете дополнительно управлять внешним видом:

```java
// Change leader line color to dark gray
chart.setLeaderLineColor(Color.DARK_GRAY);

// Increase line thickness for better visibility
chart.setLeaderLineWidth(2);

// Position labels outside the chart area
chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);
```

Эти параметры удобны, когда нужно соответствовать фирменному стилю или улучшить доступность.

### Обработка нескольких серий

Если ваша круговая диаграмма содержит более одной серии, вы можете включать направляющие линии только для конкретного сектора. Используйте индекс серии, чтобы обратиться к нужному элементу:

```java
// Enable leader lines only for the second series, third slice
chart.getSeries().get(1).get(2).setExplosion(15);
chart.getSeries().get(1).get(2).setLeaderLineEnabled(true);
```

Когда сектор не взорван, направляющая линия обычно скрывается автоматически, но её можно принудительно отобразить с помощью `setLeaderLineEnabled(true)`.

## Типичные ошибки и как их избежать

| Ошибка | Симптом | Решение |
|--------|---------|-----|
| **Направляющие линии не видны** | Диаграмма отображается без соединительных линий. | Убедитесь, что сектор взорван (`setExplosion` > 0) или явно включите направляющие линии у сектора. |
| **Перекрытие меток** | Метки сталкиваются друг с другом. | Увеличьте размер диаграммы или задайте `setLabelPlacement(Chart.LabelPlacement.OUTSIDE)`. |
| **Цвет не применён** | Сектор остаётся с цветом по умолчанию. | Проверьте, что вы обращаетесь к правильному индексу серии (`getSeries().get(0)`). |
| **Изображение не сохраняется** | `saveAsPng` бросает исключение. | Проверьте права записи в каталог вывода и поддержку экспорта в PNG у библиотеки. |

Устранение этих проблем на ранних этапах предотвращает сюрпризы во время выполнения и даёт отполированную диаграмму.

## Полный листинг исходного кода

Для удобства снова приводим полный файл исходного кода, включая импорты и комментарии:

```java
// AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Complete example that adds leader lines to a pie chart.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // Create a builder and insert a 400×300 pie chart
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // Explode the first slice (20% offset) and color it blue
        chart.getSeries().get(0).setExplosion(20);
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // Turn on leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional styling
        chart.setLeaderLineColor(Color.DARK_GRAY);
        chart.setLeaderLineWidth(2);
        chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);

        // Export the chart as a PNG image
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart generated successfully.");
    }
}
```

Запуск этой программы создаёт `pie-with-leader-lines.png`, где отображается круговая диаграмма с взорванным синим сектором и чёткими направляющими линиями, указывающими на метку сектора.

## Заключение

Теперь вы знаете, как **добавить направляющие линии к круговой диаграмме** в Java с использованием Chart API. Процесс состоит из вставки `ChartType.PIE`, взрыва нужного сектора, настройки его цвета и включения направляющих линий. С помощью дополнительных параметров стиля можно тонко настроить цвет линии, её толщину и размещение меток под любые визуальные требования.

Далее изучайте связанные темы, такие как **pie chart explosion Java**, **set sector color Chart API** и **builder.insertChart usage**, чтобы создавать более сложные визуализации: донат‑диаграммы, составные круги или интерактивные панели.

Экспериментируйте с разными индексами секторов, цветами и стилями направляющих линий — ваши диаграммы станут информативнее и визуально привлекательнее с каждой правкой. Приятного кодинга!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс содержит полностью рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Add Date Time Values To Axis Of A Chart](/words/english/net/programming-with-charts/date-time-values-to-axis/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}