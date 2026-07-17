---
category: general
date: 2026-07-16
description: Создайте круговую диаграмму в Java с использованием Aspose.Words. Узнайте,
  как добавить выноски, отобразить легенду диаграммы и «взрывать» сектор в одном руководстве.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add leader lines
- show chart legend
- how to explode slice
- how to add legend
language: ru
lastmod: 2026-07-16
og_description: Создайте круговую диаграмму в Java с помощью Aspose.Words. Это руководство
  показывает, как добавить линии‑выноски, отобразить легенду диаграммы и «взрыв» сектора,
  предоставляя вам отшлифованный визуальный результат за считанные минуты.
og_image_alt: Screenshot of a Java‑generated pie chart with an exploded slice and
  visible legend
og_title: Создание круговой диаграммы с Aspose.Words Java — Полный учебник по форматированию
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  headline: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  name: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  steps:
  - name: Java 17 (or later) installed.
    text: Java 17 (or later) installed.
  - name: Aspose.Words for Java JAR on your classpath.
    text: Aspose.Words for Java JAR on your classpath.
  - name: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
    text: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart Formatting
- Data Visualization
title: Создание круговой диаграммы с помощью Aspose.Words Java – Полное пошаговое
  руководство
url: /ru/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание круговой диаграммы с Aspose.Words Java – Полное пошаговое руководство

Задумывались ли вы когда‑нибудь, как **создать круговую диаграмму** программно на Java без борьбы с низкоуровневыми API рисования? Вы не одиноки. Многие разработчики нуждаются в быстрой визуализации для отчетов, панелей мониторинга или автоматических документов, и они выбирают Aspose.Words, потому что он справляется с тяжелой работой.  

В этом руководстве мы пройдемся по полному, готовому к запуску примеру, который не только **создает круговую диаграмму**, но и показывает, как **добавить leader lines**, **показать chart legend** и даже **вырезать кусок** для акцента. К концу вы получите файл `.docx`, выглядящий достаточно профессионально, чтобы произвести впечатление на клиента.

> **Быстрый результат:** Ниже приведенный фрагмент кода работает сразу же с Aspose.Words for Java 23.9 (или любой более новой версией). Никаких дополнительных зависимостей, только JAR.

## Что вы узнаете

- Создать пустой документ Word с помощью `DocumentBuilder`.
- Вставить **круговую диаграмму** произвольного размера.
- Использовать функцию **explode slice** для выделения точки данных.
- Включить **leader lines**, чтобы вырезанный кусок оставался соединённым с меткой.
- Включить **chart legend**, чтобы читатели могли мгновенно определить каждый кусок.
- Сохранить результат в файл `.docx`, который можно открыть в Microsoft Word или LibreOffice.

**Требования** – Вам понадобится:

1. Java 17 (или новее) установлен.
2. JAR Aspose.Words for Java в вашем classpath.
3. Базовая IDE или текстовый редактор — IntelliJ IDEA, Eclipse, VS Code, что угодно.

Итак, приступим.

## Шаг 1: Инициализация документа и билдера – Подготовка к **созданию круговой диаграммы**

Сначала нам нужен чистый холст документа. `Document` представляет весь файл Word, а `DocumentBuilder` — помощник, позволяющий добавлять содержимое.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();               // the container for our Word file
        DocumentBuilder builder = new DocumentBuilder(doc); // convenient API for adding elements
```

> **Почему это важно:** Начало с нового `Document` гарантирует отсутствие скрытых стилей или оставшихся объектов, которые могли бы помешать рендерингу диаграммы.

## Шаг 2: Вставка **круговой диаграммы** – Размер имеет значение

Aspose.Words делает вставку диаграммы однострочным вызовом. Здесь мы запрашиваем круговую диаграмму размером 400 × 300 точек — примерно 5,5 × 4,2 дюйма на типичном экране.

```java
        // Step 2: Insert a pie chart of size 400x300 points
        Shape chartShape = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = chartShape.getChart(); // the underlying chart object we will format
```

> **Полезный совет:** Если нужен другой размер, просто измените два числовых аргумента. API работает в точках, где 72 точки = 1 дюйм.

## Шаг 3: **Как вырезать кусок** – Выделение ключевой точки данных

Вырезание куска вытягивает его из остальной части круга, привлекая внимание читателя. Метод `setExplosion` принимает целое число, представляющее расстояние в точках.

```java
        // Step 3: Explode the first slice to emphasize it
        chart.getSeries().get(0).setExplosion(10); // 10 points outward
```

> **Что если у вас несколько серий?** Вы можете вызвать `setExplosion` для любого индекса серии (`get(1)`, `get(2)`, …), чтобы вырезать разные куски.

## Шаг 4: **Добавить leader lines** и **показать chart legend** – Соединяем точки

Когда кусок вырезан, метка может отдалиться. Leader lines удерживают метку привязанной, сохраняя читаемость. Одновременно легенда предоставляет быстрый ключ для всех кусков.

```java
        // Step 4: Enable leader lines for the exploded slice and show the legend
        chart.getSeries().get(0).setLeaderLines(true); // draws a line from slice to its label
        chart.setShowLegend(true);                     // makes the legend visible below the chart
```

> **Почему включать leader lines?** Без них метка может выглядеть «плавающей», сбивая пользователей с толку, к какому куску она относится.  
> **Нужна пользовательская позиция легенды?** Используйте `chart.getLegend().setPosition(LegendPosition.TOP)` или любое другое значение перечисления.

## Шаг 5: Сохранение документа – Финальный шаг **создания круговой диаграммы**

Наконец, сохраняем документ на диск. Скорректируйте путь к папке, в которую у вас есть права записи.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartDemo.docx");
    }
}
```

Запустите программу, откройте сгенерированный `PieChartDemo.docx`, и вы должны увидеть красиво оформленную круговую диаграмму с вырезанным первым куском, leader lines и видимой легендой.

![Пример круговой диаграммы с вырезанным куском и легендой](pie-chart-example.png){: .center-image alt="Пример создания круговой диаграммы с вырезанным куском, leader lines и легендой"}

### Ожидаемый результат

При открытии файла Word диаграмма будет выглядеть примерно так:

- Круговая диаграмма размером 400 × 300 pt.  
- Первый кусок смещён на 10 pt.  
- Тонкая leader line соединяет вырезанный кусок с его меткой.  
- Легенда под диаграммой перечисляет названия каждой серии.

Если вы не видите leader line, дважды проверьте, что `setLeaderLines(true)` вызывается *после* установки значения взрыва — порядок имеет значение.

## Распространённые ошибки и как их избежать

| Проблема | Почему происходит | Как исправить |
|----------|-------------------|---------------|
| **Легенда не отображается** | `setShowLegend(true)` был опущен или вызван у неверного объекта диаграммы. | Убедитесь, что вызываете `chart.setShowLegend(true)` **после** получения `Chart` из shape. |
| **Отсутствует leader line** | Кусок не был вырезан, или тип диаграммы не поддерживает leader lines. | Только `ChartType.PIE` (или `PIE_3D`) поддерживает leader lines. Сначала вызовите `setExplosion`, затем `setLeaderLines(true)`. |
| **Кусок не перемещается** | Значение взрыва слишком мало (0‑2 pt). | Увеличьте целое число, например `setExplosion(10)` или больше для более заметного эффекта. |
| **Диаграмма выглядит искажённой** | Использование несоразмерного размера (ширина ≠ высота) может «сплющить» круг. | Держите ширину и высоту одинаковыми или близкими; 400 × 300 работает, но 400 × 400 даст идеальный круг. |

## Расширенные настройки (необязательно)

Если хотите пойти дальше базовых возможностей, рассмотрите:

- **Пользовательские цвета**: `chart.getSeries().get(0).getDataPoints().get(i).getFormat().getFill().setForeColor(Color.RED);`
- **Подписи данных**: `chart.getSeries().get(0).setDataLabelType(ChartDataLabelType.CATEGORY);`
- **Эффект 3‑D**: замените `ChartType.PIE` на `ChartType.PIE_3D`.

Эти параметры позволяют точно настроить визуал под корпоративные руководства по брендингу.

## Итоги – Что мы достигли

Мы начали с пустого документа Word, **создали круговую диаграмму**, **вырезали первый кусок**, **добавили leader lines** и **показали chart legend**. Весь процесс укладывается в компактный метод `main`, что упрощает интеграцию в более крупные конвейеры отчётности.

## Следующие шаги

- **Добавить больше серий**: заполнить диаграмму реальными данными из базы данных или CSV.  
- **Экспорт в PDF**: используйте `doc.save("output.pdf", SaveFormat.PDF);` для создания PDF‑версии.  
- **Комбинировать с другими объектами**: вставьте таблицы, изображения или дополнительные диаграммы для полного отчёта.

Если вам интересны другие типы диаграмм — столбчатые, линейные, гистограммы — просто замените `ChartType.PIE` на соответствующее перечисление и следуйте тем же шагам форматирования.

---

*Удачной работы с диаграммами!* Оставляйте комментарии, если что‑то не сработало как ожидалось, или делитесь тем, как вы настроили позицию легенды. Ваш отзыв помогает всем нам создавать лучшие автоматизированные документы.

## Что вам стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Как создать столбчатую диаграмму с помощью Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Как создавать PDF‑документы с помощью Aspose.Words for Java | Document Processing API](/words/english/java/)
- [Как добавить водяной знак в документы с помощью Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}