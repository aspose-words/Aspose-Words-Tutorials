---
category: general
date: 2026-05-04
description: Как установить разрешение при экспорте Markdown из Word. Узнайте о разрешении
  изображений в Markdown, как экспортировать уравнения и сохранять Word в формате
  Markdown на Java.
draft: false
keywords:
- how to set resolution
- markdown image resolution
- how to use markdown
- how to export equations
- save word as markdown
language: ru
og_description: Как установить разрешение при экспорте Markdown из Word. Это руководство
  показывает разрешение изображений в markdown, экспорт уравнений и сохранение Word
  в формате markdown.
og_title: Как установить разрешение при сохранении Word в Markdown
tags:
- Aspose.Words
- Java
- Markdown
- Document Export
title: Как установить разрешение при сохранении Word в Markdown
url: /ru/java/document-conversion-and-export/how-to-set-resolution-when-saving-word-as-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как установить разрешение при сохранении Word в Markdown

Когда‑нибудь задумывались **как установить разрешение** для изображений, которые появляются в файле Markdown, сгенерированном из документа Word? Вы не одиноки. Многие разработчики сталкиваются с проблемой, когда изображения математических формул по умолчанию выглядят размытыми, особенно на экранах с высоким DPI.  

В этом руководстве мы пройдем точные шаги по управлению *разрешением изображений в markdown* и также покажем **как экспортировать уравнения** в LaTeX, а в конце — **как сохранить Word в markdown** с помощью Aspose.Words for Java. К концу вы получите чёткий, готовый к продакшену файл Markdown, в котором уравнения отображаются чисто, а изображения — с нужным качеством.

## Требования

- Java 17 (или любой современный JDK)  
- Aspose.Words for Java 23.6 или новее — можно взять из Maven Central  
- Документ Word (`.docx`), содержащий объекты OfficeMath (уравнения) и, возможно, растровые изображения  
- Базовое знакомство с Maven/Gradle и IDE (IntelliJ IDEA, Eclipse, VS Code и т.д.)

Дополнительные библиотеки не требуются; всё остальное обрабатывается Aspose.Words.

---

## Как установить разрешение при экспорте в Markdown

> **Совет:** Выбранное вами разрешение напрямую влияет на размер файлов сгенерированных изображений. Значение **300 dpi** является хорошим компромиссом для большинства веб‑ориентированных Markdown‑просмотрщиков.

```java
// Step 1: Load the source Word document containing equations
Document doc = new Document("YOUR_DIRECTORY/Math.docx");

// Step 2: Create Markdown save options to control the export behavior
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();

// Step 3: Export OfficeMath objects as LaTeX expressions
saveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

// Step 4 (optional): Set image resolution for any rasterized Math images
saveOptions.setImageResolution(300);   // <-- this is where we set the resolution

// Step 5: Save the document as a Markdown file using the configured options
doc.save("YOUR_DIRECTORY/MathExport.md", saveOptions);
```

Вызов `setImageResolution(int dpi)` является ядром **как установить разрешение**. Он указывает Aspose.Words растеризовать любые резервные изображения (например, когда уравнение нельзя представить в чистом LaTeX) с указанным количеством точек на дюйм. Если опустить эту строку, библиотека использует значение по умолчанию 220 dpi, что может выглядеть размыто на Retina‑экранах.

### Почему использовать LaTeX для уравнений?

Когда вы экспортируете уравнения в LaTeX (`OfficeMathExportMode.LATEX`), полученный Markdown содержит необработанный LaTeX‑код, заключённый в `$…$` или `$$…$$`. Большинство современных Markdown‑рендереров (GitHub, GitLab, MkDocs с MathJax) отобразят их как чёткие масштабируемые векторные графики — проблем с разрешением не будет. Настройка разрешения важна только для **разрешения изображений в markdown** любых растровых резервных изображений, таких как встроенные диаграммы или картинки, которые не поддерживаются нативно в Markdown.

---

## Как эффективно использовать разрешение изображений в Markdown

Если вам нужно вставить обычные картинки (например, скриншоты) в ваш файл Word, они будут преобразованы в PNG Aspose.Words. Тот же метод `setImageResolution` применяется, гарантируя, что эти PNG унаследуют указанное вами DPI. Вот быстрый чек‑лист:

1. **Выберите DPI, соответствующий вашей целевой платформе** — 72 dpi для устаревшего веба, 150 dpi для стандартных дисплеев, 300 dpi для PDF печати высокого качества.  
2. **Проверьте результат** — откройте сгенерированный файл `.md` в вашем любимом просмотрщике и увеличьте масштаб, чтобы убедиться в чёткости.  
3. **Учтите размер файлов** — более высокий DPI приводит к большим PNG; если важна пропускная способность, поэкспериментируйте с 200 dpi и сравните.

---

## Как экспортировать уравнения в LaTeX

Строка `saveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);` указывает Aspose.Words преобразовать каждый объект OfficeMath в LaTeX. Это рекомендуемый подход, потому что:

- **Масштабируемость** — LaTeX отображается в любом размере без потери качества.  
- **Редактируемость** — Вы можете позже корректировать LaTeX непосредственно в файле Markdown.  
- **Совместимость** — Большинство генераторов статических сайтов и инструментов документации уже поддерживают рендеринг LaTeX.

Если когда‑нибудь понадобится старый резервный вариант на основе изображений, просто переключитесь на `OfficeMathExportMode.IMAGE`. В этом случае установленное вами разрешение становится ещё более критичным.

---

## Сохранить Word в Markdown — полный сквозной пример

Ниже приведён полный, исполняемый фрагмент Maven‑проекта, демонстрирующий весь процесс от объявления зависимостей до выполнения.

```xml
<!-- pom.xml -->
<project xmlns="http://maven.apache.org/POM/4.0.0" ...>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>markdown-export</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.6</version>
        </dependency>
    </dependencies>
</project>
```

```java
// src/main/java/com/example/MarkdownMathExport.java
package com.example;

import com.aspose.words.*;

public class MarkdownMathExport {
    public static void main(String[] args) throws Exception {
        // Load the source Word document containing equations and images
        Document doc = new Document("src/main/resources/Math.docx");

        // Configure Markdown export options
        MarkdownSaveOptions options = new MarkdownSaveOptions();
        options.setOfficeMathExportMode(OfficeMathExportMode.LATEX); // export equations as LaTeX
        options.setImageResolution(300); // set resolution for rasterized images

        // Save as Markdown
        doc.save("output/MathExport.md", options);

        System.out.println("✅ Markdown export complete! Check output/MathExport.md");
    }
}
```

**Ожидаемый результат:** `MathExport.md` будет содержать блоки LaTeX для каждого уравнения, а любые встроенные картинки появятся как ссылки PNG с DPI 300. Откройте файл в Markdown‑просмотрщике, поддерживающем MathJax (например, VS Code с расширением Markdown Preview Enhanced), и вы увидите идеально чёткие уравнения и изображения.

---

## Часто задаваемые вопросы и особые случаи

### Что если мне нужен другой DPI только для одного изображения?

Aspose.Words применяет DPI глобально через `setImageResolution`. Чтобы задать DPI для отдельного изображения, вам придётся пост‑обработать сгенерированный Markdown: заменить PNG‑файлы на версии с более высоким разрешением и вручную скорректировать ссылки на изображения. Не идеально, но выполнимо для небольшого количества особых случаев.

### Работает ли это на Linux/macOS?

Абсолютно. Библиотека написана полностью на Java, поэтому тот же код работает везде, где установлен JDK. Просто убедитесь, что пути к файлам используют прямые слэши или `Paths.get(...)` для платформенно‑независимой обработки.

### Что насчёт вывода в SVG?

Если вы предпочитаете векторные изображения для диаграмм, можете установить `saveOptions.setExportImagesAsSvg(true);`. SVG игнорируют DPI, поэтому проблема **разрешения изображений в markdown** исчезает. Однако не все Markdown‑рендереры корректно работают с SVG, поэтому сначала протестируйте целевую платформу.

### Могу ли я встроить сгенерированный Markdown в генератор статических сайтов?

Да. Выходной файл — обычный `.md` со стандартным синтаксисом Markdown плюс разделители LaTeX. Большинство генераторов (Jekyll, Hugo, MkDocs) примут его без проблем. Просто не забудьте включить MathJax или KaTeX в конфигурации сайта.

---

## Заключение

Мы рассмотрели **как установить разрешение** для изображений при **сохранении Word в markdown**, изучили нюансы **разрешения изображений в markdown**, продемонстрировали **как экспортировать уравнения** в LaTeX и показали полную реализацию на Java. Настраивая `setImageResolution` и выбирая правильный `OfficeMathExportMode`, вы получаете точный контроль над визуальной точностью и размером файлов.

Готовы к следующему шагу? Попробуйте сочетать этот подход с Aspose.PDF для прямого преобразования того же источника Word в PDF, либо поэкспериментируйте с `setExportImagesAsSvg(true)` для векторной графики. Техники, изученные здесь, являются строительными блоками любой автоматизированной конвейерной системы документации.

Если этот гид оказался полезным, поставьте звёздочку на GitHub, поделитесь им с коллегами или оставьте комментарий ниже со своими советами. Счастливого кодинга!  

![Пример установки разрешения](resolution.png "Как установить разрешение при сохранении Word в Markdown")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}