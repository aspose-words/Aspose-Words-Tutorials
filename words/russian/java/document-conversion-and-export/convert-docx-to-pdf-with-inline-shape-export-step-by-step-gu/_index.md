---
category: general
date: 2026-02-18
description: Узнайте, как конвертировать DOCX в PDF и сохранять Word в PDF, сохраняя
  плавающие объекты. Это руководство показывает, как правильно экспортировать объекты.
draft: false
keywords:
- convert docx to pdf
- save word as pdf
- how to export shapes
language: ru
og_description: Конвертировать DOCX в PDF и узнать, как экспортировать фигуры. Следуйте
  этому полному руководству, чтобы сохранить Word в PDF с правильной разметкой.
og_title: Конвертация DOCX в PDF – Руководство по экспорту встроенных объектов
tags:
- Aspose.Words
- Java
- PDF conversion
title: Преобразовать DOCX в PDF с экспортом встроенных фигур — пошаговое руководство
url: /ru/java/document-conversion-and-export/convert-docx-to-pdf-with-inline-shape-export-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Конвертация DOCX в PDF – Руководство по экспорту встроенных фигур

Когда‑то вам нужно **конвертировать DOCX в PDF**, но вы боитесь, что плавающие изображения или текстовые блоки исчезнут или сместятся? Вы не одиноки. Во многих проектах — например, в автоматических генераторах отчётов или конвейерах пакетной обработки — сохранение точного макета Word‑документа является обязательным.

Хорошая новость? С несколькими строками кода вы можете **сохранить Word как PDF** и управлять тем, будут ли плавающие фигуры экспортированы как встроенные теги или останутся блочными элементами. Ниже вы увидите, **как экспортировать фигуры** именно так, как вам нужно, а также несколько советов, которые избавят от типичных проблем.

---

## Что вы узнаете

* Загрузить файл `.docx` с диска.  
* Настроить `PdfSaveOptions` так, чтобы плавающие фигуры экспортировались как встроенные теги.  
* Записать полученный PDF в выбранную вами папку.  
* Понять, почему важен флаг `setExportFloatingShapesAsInlineTag` и когда его стоит отключать.  

Никаких внешних сервисов, никакого волшебного UI «клик‑для‑скачивания» — только чистый Java‑код, который можно добавить в любой проект Maven или Gradle.

---

## Требования

| Требование | Почему это важно |
|-------------|----------------|
| **Aspose.Words for Java** (v23.12 или новее) | Предоставляет классы `Document` и `PdfSaveOptions`, используемые в примере. |
| **JDK 8+** | Библиотека компилирована для Java 8 и новее; более старые среды выполнения вызовут `UnsupportedClassVersionError`. |
| **DOCX‑файл** с хотя бы одной плавающей фигурой (изображение, текстовый блок, WordArt) | Чтобы увидеть эффект опции экспорта фигур, нужен документ, действительно содержащий плавающие объекты. |

Если у вас уже есть всё необходимое, отлично — перейдём к делу.

---

## Шаг 1 – Загрузка исходного документа  

Сначала создаём экземпляр `Document`, указывая путь к нужному `.docx`. Конструктор читает файл в память, разбирает пакет OpenXML и подготавливает внутреннюю модель объектов.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

// Adjust the path to your environment
String inputPath = "YOUR_DIRECTORY/input.docx";

Document doc = new Document(inputPath);
```

> **Совет:** Если вы обрабатываете множество файлов в цикле, переиспользуйте один объект `Document` только после вызова `doc.close()` (или позвольте сборщику мусора освободить его). Это предотвращает утечки дескрипторов файлов в Windows.

---

## Шаг 2 – Настройка параметров сохранения PDF для экспорта фигур  

Сердце руководства находится здесь. `PdfSaveOptions` позволяет задать, как будет происходить конверсия. Установка `setExportFloatingShapesAsInlineTag(true)` заставляет каждую плавающую фигуру рассматривать как *встроенный* элемент в структуре тегов PDF. Это значит, что скрин‑ридеры будут читать фигуру в том же порядке, что и окружающий текст, что часто требуется для соответствия требованиям доступности.

```java
import com.aspose.words.PdfSaveOptions;

PdfSaveOptions pdfOptions = new PdfSaveOptions();
// true → inline tagging (shape behaves like a character)
// false → block‑level tagging (shape sits in its own block)
pdfOptions.setExportFloatingShapesAsInlineTag(true);
```

**Когда стоит установить `false`?**  
Если ваш PDF предназначен только для печати и вы хотите, чтобы фигуры сохраняли своё оригинальное позиционирование, не влияя на логический порядок чтения, можно предпочесть блочное тегирование. По умолчанию значение `false`, поэтому в этом руководстве мы явно включаем поведение inline.

---

## Шаг 3 – Сохранение документа как PDF  

Теперь, когда параметры готовы, вызываем `save`, передавая целевое имя файла и объект опций. Библиотека берёт на себя тяжёлую работу: движок разметки, встраивание шрифтов и генерацию тегов.

```java
String outputPath = "YOUR_DIRECTORY/shapes.pdf";
doc.save(outputPath, pdfOptions);
```

После завершения вызова вы найдёте `shapes.pdf` в указанной папке. Откройте его в Adobe Acrobat или любом PDF‑просмотрщике, который показывает теги (обычно **File → Properties → Tags**), и вы увидите, что плавающая фигура отображается как встроенный тег.

---

## Полный, готовый к запуску пример  

Собрав всё вместе, получаем автономный Java‑класс, который можно скомпилировать и запустить. Убедитесь, что JAR Aspose.Words находится в вашем classpath.

```java
import com.aspose.words.*;

public class DocxToPdfWithShapes {
    public static void main(String[] args) {
        try {
            // 1️⃣ Load the source DOCX
            String inputPath = "YOUR_DIRECTORY/input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Configure PDF options – export floating shapes as inline tags
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → inline tagging

            // 3️⃣ Save as PDF
            String outputPath = "YOUR_DIRECTORY/shapes.pdf";
            doc.save(outputPath, pdfOptions);

            System.out.println("✅ Conversion complete! PDF saved to: " + outputPath);
        } catch (Exception e) {
            System.err.println("❌ Something went wrong: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Ожидаемый результат:**  
- PDF‑файл содержит тот же текстовый контент, что и оригинальный DOCX.  
- Любые плавающие изображения или текстовые блоки теперь помечены *inline*, то есть они находятся в порядке чтения, а не как отдельные блоки.  
- Если открыть панель **Tags** в PDF, вы увидите элемент `<Figure>`, вложенный в `<Paragraph>` — именно то, что гарантирует `setExportFloatingShapesAsInlineTag(true)`.

---

## Часто задаваемые вопросы и особые случаи  

### 1️⃣ Работает ли это с DOCX‑файлами, защищёнными паролем?  
Да — просто укажите пароль перед загрузкой:

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("mySecret");
Document doc = new Document(inputPath, loadOptions);
```

### 2️⃣ А как насчёт SVG или EMF‑изображений внутри Word‑файла?  
Aspose.Words автоматически растеризует векторную графику при сохранении в PDF. Если нужно сохранить её векторной, установите:

```java
pdfOptions.setRasterizeTransformedElements(false);
```

### 3️⃣ Как сохранить гиперссылки при конвертации?  
Ссылки сохраняются по умолчанию. Однако, если отключить теги (`pdfOptions.setSaveFormat(SaveFormat.PDF)` без опций), вы можете потерять логическую структуру. Оставьте объект `PdfSaveOptions`, чтобы сохранить и теги, и ссылки.

### 4️⃣ Можно ли пакетно обрабатывать папку с DOCX‑файлами?  
Конечно. Оберните логику `DocxToPdfWithShapes` в цикл, который перебирает `Files.list(Paths.get("YOUR_DIRECTORY"))`. Не забудьте обрабатывать исключения для каждого файла, чтобы один плохой документ не остановил весь процесс.

---

## Советы из практики  

* **Следите за отсутствием шрифтов.** Если исходный DOCX использует пользовательский шрифт, не установленный на сервере, PDF подставит запасной, что может нарушить макет. Используйте `pdfOptions.setFontEmbeddingMode(FontEmbeddingMode.EMBED_ALL)`, чтобы принудительно встраивать все шрифты.  
* **Тестирование доступности.** После конвертации запустите **Accessibility Checker** в Acrobat. Встроенное тегирование обычно повышает оценку, но вам всё равно может потребоваться добавить альтернативный текст к изображениям вручную.  
* **Совет по производительности:** Для больших документов (100+ страниц) включите `pdfOptions.setMemoryOptimization(true)`, чтобы снизить потребление кучи.

---

## Визуальная проверка  

Ниже показан быстрый скриншот PDF, открытого в Adobe Acrobat, где в панели **Tags** выделена встроенная фигура.

![Convert DOCX to PDF example output](image.png)

*Alt text: пример вывода конвертации docx в pdf, показывающий встроенные теги фигур.*

---

## Итоги  

Теперь вы знаете, **как конвертировать DOCX в PDF**, контролируя способ экспорта плавающих объектов. Переключая `setExportFloatingShapesAsInlineTag`, вы решаете, станут ли фигуры частью порядка чтения или останутся независимыми блоками — это критично как для доступности, так и для визуального соответствия.

Дальше вы можете:

* **Сохранять Word как PDF** массово для архивирования.  
* Экспериментировать с другими `PdfSaveOptions`, например `setCompliance(PdfCompliance.PDF_A_1B)` для долговременного хранения.  
* Глубже изучить **как экспортировать фигуры**, исследуя полную документацию Aspose.Words или пробуя флаг `setExportDocumentStructure(true)` для более богатых деревьев тегов.

Попробуйте, поиграйте с опциями, и пусть ваши PDF выглядят именно так, как вам нужно. Счастливого кодинга!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}