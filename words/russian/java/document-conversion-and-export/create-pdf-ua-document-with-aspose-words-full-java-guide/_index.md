---
category: general
date: 2026-04-28
description: Создайте PDF‑документ UA с помощью Aspose.Words для Java. Узнайте, как
  загружать docx с восстановлением, экспортировать уравнения в LaTeX, сохранять markdown
  из Word и получать недостающие шрифты.
draft: false
keywords:
- create PDF UA document
- retrieve missing fonts
- export equations to LaTeX
- save markdown from Word
- load docx with recovery
language: ru
og_description: Создайте PDF‑UA документ с помощью Aspose.Words для Java. Пошаговое
  руководство, охватывающее восстановление при загрузке, экспорт в LaTeX, сохранение
  в Markdown и получение недостающих шрифтов.
og_title: Создать PDF UA документ – Полный учебник по Java
tags:
- Aspose.Words
- Java
- PDF/UA
title: Создание PDF‑UA документа с помощью Aspose.Words – полное руководство по Java
url: /ru/java/document-conversion-and-export/create-pdf-ua-document-with-aspose-words-full-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание PDF UA‑документа – Полный Java‑урок

Нужно **создать PDF UA‑документ** из файла Word, одновременно обрабатывая повреждённый контент? В этом руководстве мы пройдём процесс загрузки DOCX в режиме восстановления, экспорта уравнений в LaTeX, сохранения Markdown из Word и получения сведений о недостающих шрифтах — всё с помощью Aspose.Words for Java.  

Если вы когда‑нибудь сталкивались с битым .docx и задавались вопросом, почему ваш PDF не доступен, вы попали по адресу. К концу вы получите полностью‑соответствующий PDF/UA 1 файл, версию в Markdown с уравнениями LaTeX и чёткий список всех замен шрифтов, произошедших при загрузке.

## Что понадобится

- **Aspose.Words for Java** (последняя версия на 2026 год) — добавьте зависимость Maven/Gradle или JAR в classpath.  
- Java 17 или новее (API использует потоки, поэтому рекомендуется свежий JDK).  
- Пример `input.docx`, который может содержать повреждённые секции, уравнения Office Math и плавающие объекты.  

Дополнительные библиотеки не требуются; всё находится внутри Aspose.Words.

---

## Шаг 1 – Загрузка DOCX в режиме восстановления  

Когда документ частично повреждён, загрузчик по умолчанию бросает исключение. Включив режим восстановления, вы заставляете Aspose.Words продолжать работу и выводить предупреждения вместо ошибок.

```java
import com.aspose.words.*;

public class LatestFeaturesDemo {

    public static void main(String[] args) throws Exception {

        // 1️⃣ Load the document with recovery to gracefully handle corruption
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

*Почему это важно:* Режим восстановления предотвращает поломку всей конвейерной цепочки из‑за одного плохого абзаца. Он также заполняет `doc.getWarnings()`, чтобы позже **получить недостающие шрифты** и другие проблемы.

---

## Шаг 2 – Экспорт уравнений в LaTeX внутри файла Markdown  

Большинство разработчиков любят Markdown для документации, но встроенные уравнения Word сложно копировать. Aspose.Words может переводить их напрямую в LaTeX.

```java
        // 2️⃣ Configure Markdown export with LaTeX for Office Math
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

        // Store images in a sub‑folder so the Markdown stays tidy
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });

        // Save the Markdown file
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);
```

*Совет:* Обратный вызов гарантирует, что каждое извлечённое изображение окажется в папке `imgs/`. Это имитирует способ рендеринга Markdown на GitHub — чисто и портативно.

---

## Шаг 3 – Создание PDF / UA‑документа с правильной разметкой  

Соответствие PDF/UA (Universal Accessibility) обязательно для многих государственных проектов. Следующие параметры заставляют Aspose.Words правильно тегировать плавающие объекты и устанавливать флаг соответствия PDF/UA.

```java
        // 3️⃣ Prepare PDF/UA export options
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);          // Enforce PDF/UA‑1
        pdfOptions.setExportFloatingShapesAsInlineTag(true);      // Tag floating shapes

        // Save the accessible PDF
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);
```

*Что вы увидите:* Открыв `output.pdf` в Adobe Acrobat Pro, в свойствах документа будет указано «PDF/UA‑1 compliant». Все плавающие объекты (текстовые блоки, изображения) получат соответствующие теги для скрин‑ридеров.

---

## Шаг 4 – Настройка тени у формы (необязательно)  

Хотя это не требуется для доступности, небольшие визуальные правки могут пригодиться для внутренних отчётов.

```java
        // 4️⃣ Grab the first shape and modify its shadow
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(java.awt.Color.GRAY);
```

*Зачем это нужно?* Если PDF также используется в маркетинговых целях, лёгкая тень делает макет более изысканным, не нарушая требований доступности.

---

## Шаг 5 – Получение недостающих шрифтов и других предупреждений  

Во время загрузки в режиме восстановления Aspose.Words фиксирует любые замены шрифтов. Их список помогает решить, встраивать правильный шрифт или принимать замену.

```java
        // 5️⃣ Enumerate font‑substitution warnings
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName() +
                                   " → substituted: " + fsw.getSubstitutedFontName());
            }
        }

        // You can also handle other warning types here (e.g., content loss)
    }
}
```

*Типичный вывод* (в консоли вы увидите что‑то вроде):

```
=== Font Substitution Report ===
Missing: Calibri → substituted: Arial
Missing: Times New Roman → substituted: Liberation Serif
```

Если обнаружены критически важные недостающие шрифты, установите их на сервере или внедрите через `PdfSaveOptions.setEmbedFullFonts(true)`.

---

## Полный рабочий пример  

Ниже представлен полностью готовый к запуску Java‑класс. Скопируйте его в IDE, поправьте пути и нажмите **Run**.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to:
 *  • load a DOCX with recovery,
 *  • export equations to LaTeX inside Markdown,
 *  • create a PDF/UA‑1 compliant PDF,
 *  • modify shape shadows,
 *  • and list any font‑substitution warnings.
 */
public class LatestFeaturesDemo {
    public static void main(String[] args) throws Exception {

        // ---- Step 1: Load DOCX with recovery ----
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // ---- Step 2: Export equations to LaTeX in Markdown ----
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);

        // ---- Step 3: Save as PDF/UA with proper tagging ----
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);

        // ---- Step 4: Optional – adjust the first shape’s shadow ----
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(Color.getGray());

        // ---- Step 5: List any missing‑font warnings ----
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName()
                                   + " → substituted: " + fsw.getSubstitutedFontName());
            }
        }
    }
}
```

**Ожидаемые результаты**

| Вывод | Описание |
|--------|-------------|
| `output.md` | Файл Markdown, где каждое уравнение Office Math представлено в виде LaTeX (`$…$`). Изображения сохраняются в `imgs/`. |
| `output.pdf` | Документ, соответствующий PDF/UA‑1; откройте в Acrobat, чтобы увидеть «PDF/UA‑1» в Файл → Свойства → Стандарты. |
| Консоль | Список недостающих шрифтов, например «Missing: Calibri → substituted: Arial». |

---

## Часто задаваемые вопросы (FAQ)

**В: Работает ли это со старыми версиями Aspose.Words?**  
О: Перечисленные перечисления `RecoveryMode`, `OfficeMathExportMode.LATEX` и `PdfCompliance.PDF_UA_1` появились в версии 22.8. Если у вас более старая версия, обновитесь — функции доступности не портированы назад.

**В: Как встроить оригинальные шрифты вместо замен?**  
О: Установите `pdfOptions.setEmbedFullFonts(true)` и убедитесь, что файлы шрифтов доступны в пути шрифтов JVM.

**В: Можно ли экспортировать в другие разметочные форматы (например, HTML), сохраняя уравнения LaTeX?**  
О: Да. Используйте `HtmlSaveOptions` и задайте `setOfficeMathExportMode(OfficeMathExportMode.LATEX)` — тот же enum работает для разных форматов.

**В: Мой DOCX содержит множество плавающих объектов; будут ли они все тегированы?**  
О: При включённом `setExportFloatingShapesAsInlineTag(true)` Aspose.Words оборачивает каждый плавающий объект в тег `<Figure>` для PDF/UA, что удовлетворяет большинству проверок скрин‑ридеров.

---

## Итоги  

Мы только что продемонстрировали, как **создать PDF UA‑документ** из Word‑источника, одновременно **загружая DOCX в режиме восстановления**, **экспортируя уравнения в LaTeX**, **сохраняя Markdown из Word** и **получая недостающие шрифты**. Код полностью автономный, работает в любой среде Java 17+ и генерирует артефакты, готовые как для аудитов доступности, так и для разработчиков.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}