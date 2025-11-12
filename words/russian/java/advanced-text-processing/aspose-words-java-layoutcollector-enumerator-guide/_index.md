---
date: '2025-11-12'
description: Изучите, как использовать LayoutCollector и LayoutEnumerator в Aspose.Words
  for Java для анализа разбиения на страницы, обхода макета документа, реализации
  обратных вызовов макета и перезапуска нумерации страниц в непрерывных разделах.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
- analyze pagination java
- use layoutcollector page span
- traverse document layout
- restart page numbering sections
- implement layout callback
language: ru
title: Анализ пагинации в Java с инструментами разметки Aspose.Words
url: /java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Анализ разбиения на страницы в Java с помощью инструментов разметки Aspose.Words

## Введение  

Если вам необходимо **анализировать разбиение на страницы** или **просматривать разметку документа** в Java‑приложении, Aspose.Words for Java предоставляет два мощных API: **`LayoutCollector`** и **`LayoutEnumerator`**. Эти классы позволяют определить, сколько страниц занимает узел, пройтись по каждому элементу разметки, реагировать на события разметки и даже перезапустить нумерацию страниц в непрерывных разделах. В этом руководстве мы пошагово рассмотрим каждую функцию, покажем реальные фрагменты кода и объясним ожидаемые результаты, чтобы вы могли сразу применить их на практике.

Вы узнаете, как:

* **использовать LayoutCollector** для получения начальной и конечной страницы любого узла (use layoutcollector page span)  
* **просматривать разметку документа** с помощью LayoutEnumerator (traverse document layout)  
* **реализовать обратные вызовы разметки** для реакции на события разбиения (implement layout callback)  
* **перезапустить нумерацию страниц** в непрерывных разделах (restart page numbering sections)  

Начнём.

## Требования  

### Необходимые библиотеки  

| Инструмент сборки | Зависимость |
|-------------------|-------------|
| **Maven** | ```xml<br><dependency><groupId>com.aspose</groupId><artifactId>aspose-words</artifactId><version>25.3</version></dependency>``` |
| **Gradle** | ```gradle<br>implementation 'com.aspose:aspose-words:25.3'``` |

> **Примечание:** Номер версии оставлен для совместимости; код работает с любой современной версией Aspose.Words for Java.

### Окружение  

* JDK 8 или новее  
* IDE, например IntelliJ IDEA или Eclipse  

### Знания  

Достаточно базовых навыков программирования на Java и знакомства с Maven/Gradle, чтобы следовать примерам.

## Настройка Aspose.Words  

Прежде чем вы сможете вызвать любой API разметки, библиотека должна быть лицензирована (или использоваться в режиме пробной версии). Ниже показан минимальный код инициализации:

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Load your license file – skip this line for a trial evaluation
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

*Этот код не изменяет документ; он лишь подготавливает среду Aspose.*  

Теперь перейдём к основным возможностям.

## Функция 1: Использование **LayoutCollector** для анализа разбиения на страницы  

`LayoutCollector` сопоставляет каждый узел в `Document` со страницами, которые он занимает. Это самый надёжный способ **use layoutcollector page span** для анализа разбиения.

### Пошаговая реализация  

1. **Создать новый документ и привязать LayoutCollector.**  
2. **Вставить содержимое, вызывающее разбиение** (например, разрывы страниц, разрывы разделов).  
3. **Обновить разметку** с помощью `updatePageLayout()`.  
4. **Запросить у коллектора** начальную страницу, конечную страницу и общее количество охваченных страниц.

#### 1️⃣ Инициализация Document и LayoutCollector  

```java
Document doc = new Document();                 // Empty document
LayoutCollector layoutCollector = new LayoutCollector(doc);
```

#### 2️⃣ Заполнение документа  

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);
```

#### 3️⃣ Обновление разметки и получение метрик  

```java
layoutCollector.clear();          // Reset any previous mappings
doc.updatePageLayout();           // Force pagination calculation

int pagesSpanned = layoutCollector.getNumPagesSpanned(doc);
assert pagesSpanned == 5;         // Expected: the document occupies 5 pages
System.out.println("Document spans " + pagesSpanned + " pages.");
```

**Ожидаемый вывод**

```
Document spans 5 pages.
```

> **Почему это работает:** `updatePageLayout()` заставляет Aspose.Words пересчитать разметку, после чего `LayoutCollector` может точно сообщать о диапазонах страниц.

## Функция 2: Просмотр разметки документа с помощью **LayoutEnumerator**  

Когда необходимо **traverse document layout** (например, для пользовательского рендеринга или анализа), `LayoutEnumerator` предоставляет древовидный вид страниц, абзацев, строк и слов.

### Пошаговая реализация  

1. Загрузить существующий документ, содержащий элементы разметки.  
2. Создать экземпляр `LayoutEnumerator`.  
3. Перейти к корневому элементу `PAGE`.  
4. Обходить разметку вперёд и назад с помощью рекурсивных вспомогательных методов.

#### 1️⃣ Загрузка документа и создание перечислителя  

```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);
```

#### 2️⃣ Позиционирование на уровне страниц  

```java
layoutEnumerator.moveParent(LayoutEntityType.PAGE);
```

#### 3️⃣ Прямой обход (по глубине)  

```java
traverseLayoutForward(layoutEnumerator, 1);
```

#### 4️⃣ Обратный обход  

```java
traverseLayoutBackward(layoutEnumerator, 1);
```

> **Вспомогательные методы** (`traverseLayoutForward` / `traverseLayoutBackward`) реализованы рекурсивно для посещения каждого дочернего элемента и вывода его типа и индекса страницы. Их можно адаптировать для сбора статистики, рендеринга графики или изменения свойств разметки.

## Функция 3: Реализация **Layout Callbacks**  

Иногда требуется реагировать, когда Aspose.Words завершает разметку части документа. Реализация `IPageLayoutCallback` позволяет **implement layout callback** логику, например, сохранять каждую страницу как изображение.

### Пошаговая реализация  

1. Присвоить экземпляр обратного вызова свойству `LayoutOptions` документа.  
2. Внутри обратного вызова обработать события `PART_REFLOW_FINISHED` и `CONVERSION_FINISHED`.  
3. Сохранить текущую страницу в PNG с помощью `ImageSaveOptions`.

#### 1️⃣ Регистрация обратного вызова  

```java
doc.getLayoutOptions().setCallback(new RenderPageLayoutCallback());
doc.updatePageLayout();                     // Triggers the callback events
```

#### 2️⃣ Класс обратного вызова  

```java
private static class RenderPageLayoutCallback implements IPageLayoutCallback {
    public void notify(PageLayoutCallbackArgs a) throws Exception {
        if (a.getEvent() == PageLayoutEvent.PART_REFLOW_FINISHED) {
            notifyPartFinished(a);
        } else if (a.getEvent() == PageLayoutEvent.CONVERSION_FINISHED) {
            notifyConversionFinished(a);
        }
    }

    private void renderPage(PageLayoutCallbackArgs a, int pageIndex) throws Exception {
        ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.PNG);
        saveOptions.setPageSet(new PageSet(pageIndex));

        try (FileOutputStream stream = new FileOutputStream(
                "YOUR_ARTIFACTS_DIR/PageLayoutCallback.page-" + (pageIndex + 1) + ".png")) {
            a.getDocument().save(stream, saveOptions);
        }
    }

    // You can add custom logic here for partFinished / conversionFinished
}
```

**Что происходит:** Каждый раз, когда часть разметки завершает перепоток, обратный вызов рендерит эту страницу в PNG‑файл, предоставляя визуальный след процесса разбиения.

## Функция 4: Перезапуск нумерации страниц в **непрерывных разделах**  

Если документ содержит непрерывные разделы, вы можете захотеть, чтобы нумерация страниц перезапускалась только на новой физической странице. Это достигается настройкой `ContinuousSectionRestart`.

### Пошаговая реализация  

1. Загрузить целевой документ.  
2. Изменить параметр `ContinuousSectionPageNumberingRestart`.  
3. Снова вызвать `updatePageLayout()`, чтобы применить изменение.

#### 1️⃣ Загрузка документа  

```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Continuous section page numbering.docx");
```

#### 2️⃣ Настройка поведения перезапуска  

```java
doc.getLayoutOptions()
   .setContinuousSectionPageNumberingRestart(ContinuousSectionRestart.FROM_NEW_PAGE_ONLY);
doc.updatePageLayout();            // Apply the new numbering rule
```

**Результат:** Номера страниц теперь будут перезапускаться только при начале новой физической страницы, что сохраняет чистый профессиональный вид отчётов или книг.

## Практические применения  

| Сценарий | Какой API помогает | Выгода |
|----------|--------------------|--------|
| **Аудит длинных контрактов** | `LayoutCollector` | Быстро определить, какие пункты охватывают несколько страниц. |
| **Пользовательский рендеринг PDF** | `LayoutEnumerator` | Обойти дерево разметки для экспорта каждой строки в векторную графику. |
| **Предпросмотр документа в реальном времени** | Layout callbacks | Генерировать изображения страниц «на лету» по мере редактирования. |
| **Многоразделные отчёты** | Перезапуск нумерации в непрерывных разделах | Сохранять логичную нумерацию без ручных правок. |

## Советы по производительности  

* **Удаляйте неиспользуемые узлы** перед вызовом `updatePageLayout()` — меньше элементов — быстрее разбиение.  
* **Повторно используйте один LayoutCollector** для множества запросов, а не создавайте новый каждый раз.  
* **Ограничьте глубину обхода** при работе с LayoutEnumerator, если нужны только данные уровня страниц.  
* **Закрывайте потоки** (как показано в примере обратного вызова), чтобы избежать утечек памяти при работе с большими документами.

## Заключение  

Овладев `LayoutCollector`, `LayoutEnumerator`, обратными вызовами разметки и нумерацией в непрерывных разделах, вы получаете полноценный набор инструментов для **analyze pagination java**, **traverse document layout** и **restart page numbering sections**. Эти API позволяют создавать надёжные, высокопроизводительные конвейеры обработки текста, обеспечивая профессиональные результаты каждый раз.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}