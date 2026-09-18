---
category: general
date: 2026-02-15
description: Узнайте, как получить недостающие шрифты при загрузке документа Word
  в Java с помощью Aspose.Words. Включает обработку предупреждающих обратных вызовов
  и замену шрифтов.
draft: false
keywords:
- how to get missing fonts
- Aspose.Words missing font
- font substitution warning
- Java LoadOptions warning callback
- document processing Java
language: ru
og_description: Как получить недостающие шрифты в Java с Aspose.Words. Узнайте о обработчиках
  предупреждений, замене шрифтов и лучших практиках обработки документов.
og_title: Как получить недостающие шрифты в Java – руководство Aspose.Words
tags:
- Aspose.Words
- Java
- Font Management
title: Как получить недостающие шрифты в Java — руководство Aspose.Words
url: /ru/java/document-loading-and-saving/how-to-get-missing-fonts-in-java-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как получить недостающие шрифты в Java – руководство Aspose.Words

Вы когда‑нибудь открывали документ Word в Java и видели странные замены шрифтов, задаваясь вопросом **как получить недостающие шрифты**? Вы не первый, кто столкнулся с этим сюрпризом. Во многих корпоративных приложениях предупреждения о недостающих шрифтах могут нарушить визуальную точность отчётов, контрактов или маркетинговых материалов.

Хорошая новость? Aspose.Words предоставляет простой способ перехватывать такие предупреждения через обратный вызов, чтобы вы могли вести журнал, заменять шрифты или даже оповещать пользователей до рендеринга документа. В этом руководстве мы пройдём полный, готовый к запуску пример, показывающий **как получить недостающие шрифты**, объясняющий, почему важен обратный вызов, и рассматривающий несколько приёмов для реальных проектов.

> **Pro tip:** Если вы уже используете Aspose.Words 22.12 или новее, показанный ниже API работает «из коробки» без дополнительной настройки.

---

![Диаграмма, иллюстрирующая получение недостающих шрифтов с помощью обратного вызова предупреждений Aspose.Words](how-to-get-missing-fonts-diagram.png "диаграмма получения недостающих шрифтов")

## Что покрывает это руководство

- Настройка **Java LoadOptions warning callback** для перехвата предупреждений о замене шрифтов.  
- Фильтрация предупреждений, чтобы видеть только те, которые связаны с недостающими шрифтами.  
- Вывод понятного, человекочитаемого отчёта о том, какие шрифты были заменены и чем они заменены.  
- Советы по работе с большими документами, настройке уровня предупреждений и интеграции решения в более крупный конвейер обработки.

К концу этого руководства вы сможете ответить на вопрос «**как получить недостающие шрифты**?» готовым к запуску фрагментом кода и чётким пониманием underlying механики.

### Предварительные требования

- Установлен Java 8 или новее.  
- Библиотека Aspose.Words for Java (скачайте с официального сайта или добавьте через Maven/Gradle).  
- Документ Word, который ссылается на шрифт, не установленный на вашей машине (например, `MissingFont.docx`).  

Если чего‑то не хватает, получите библиотеку сейчас — добавление её в Maven так же просто:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version> <!-- replace with the latest version -->
</dependency>
```

---

## Шаг 1: Подготовьте коллекцию для предупреждений о замене шрифтов

Перед загрузкой документа нам нужен контейнер для хранения всех предупреждений, которые генерирует Aspose.Words. `ArrayList<WarningInfo>` отлично подходит, потому что сохраняет порядок и позволяет позже итерировать элементы.

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

// Step 1: Create a list that will hold warning information.
List<WarningInfo> fontWarnings = new ArrayList<>();
```

*Почему это важно:* Обратный вызов предупреждений может сработать десятки раз для одного файла — каждая недостающая глиф, каждая проблема с внедрённым изображением и т.д. Сначала собирая их, вы ускоряете фазу загрузки и откладываете обработку в контролируемый цикл.

---

## Шаг 2: Настройте LoadOptions с обратным вызовом предупреждений

Aspose.Words позволяет подключить `IWarningCallback`. Внутри обратного вызова мы будем добавлять каждый `WarningInfo` в наш список из Шага 1.

```java
// Step 2: Set up LoadOptions with a custom warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Capture every warning; we'll filter later.
        fontWarnings.add(info);
    }
});
```

*Объяснение:* Метод `warning` вызывается **синхронно** во время загрузки документа. Просто помещая `WarningInfo` в `fontWarnings`, мы избегаем тяжёлого ввода‑вывода (например, записи в файл), который мог бы замедлить загрузку. Этот паттерн — collect‑then‑process — рекомендован для обработки больших пакетов предупреждений.

---

## Шаг 3: Загрузите документ, используя сконфигурированные параметры

Теперь действительно читаем файл Word. Если документ содержит шрифты, которые не установлены, Aspose.Words автоматически заменит их и вызовет наш обратный вызов предупреждений.

```java
// Step 3: Load the document with the warning‑aware LoadOptions.
String filePath = "YOUR_DIRECTORY/MissingFont.docx"; // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

*Что происходит «под капотом»?* Aspose.Words парсит таблицу шрифтов файла, сравнивает её с шрифтами, доступными в ОС, и для каждой недостающей записи создаёт `WarningInfo` с `WarningSource.FontSubstitution`. Этот источник — ключ, который мы будем использовать для изоляции предупреждений о недостающих шрифтах.

---

## Шаг 4: Отфильтруйте и отобразите только предупреждения о замене шрифтов

После загрузки `fontWarnings` может содержать смесь сообщений (например, устаревшие функции, проблемы с изображениями). Нас интересуют только недостающие шрифты, поэтому пробегаем список и выводим лаконичный отчёт.

```java
// Step 4: Output any font‑substitution warnings that were captured.
for (WarningInfo warning : fontWarnings) {
    if (warning.getSource() == WarningSource.FontSubstitution) {
        System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                           warning.getAdditionalInfo() + "'");
    }
}
```

**Пример вывода**

```
Substituted 'Comic Sans MS' with 'Arial'
Substituted 'Times New Roman PS' with 'Times New Roman'
```

*Почему это полезно:* Поле `description` сообщает, какой шрифт запросил документ, а `additionalInfo` — какой шрифт фактически использовал Aspose.Words. Имея эти данные, вы можете:

- Предложить пользователю установить недостающий шрифт.  
- Программно внедрить заменяющий шрифт в документ (`doc.getFontInfos().add(...)`).  
- Залогировать событие для аудита соответствия.

---

## Обработка граничных случаев и распространённых вариантов

### 1. Подавление предупреждений, не связанных со шрифтами

Если нужны только сообщения о шрифтах, можно сузить обратный вызов:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        fontWarnings.add(info);
    }
});
```

Это уменьшает нагрузку на память при обработке огромных пакетов.

### 2. Настройка уровня серьёзности предупреждений

Aspose.Words классифицирует предупреждения по `WarningType`. Для недостающих шрифтов обычно используется `WarningType.FontSubstitution`. Если нужно рассматривать их как ошибки (например, прервать загрузку), выбросьте исключение внутри обратного вызова:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        throw new RuntimeException("Missing font detected: " + info.getDescription());
    }
});
```

### 3. Работа с потоками вместо файлов

Иногда документы приходят из базы данных или HTTP‑запроса. Тот же подход работает с `InputStream`:

```java
InputStream docStream = new ByteArrayInputStream(bytesFromDb);
Document doc = new Document(docStream, loadOptions);
```

Не забудьте закрыть поток после загрузки.

### 4. Использование пользовательской папки шрифтов

Если у вас есть набор корпоративных шрифтов на общем диске, укажите Aspose.Words эту папку:

```java
loadOptions.setFontSettings(new FontSettings());
loadOptions.getFontSettings().setFontsFolder("C:/CorporateFonts", true);
```

Теперь библиотека будет искать шрифты там *сначала*, прежде чем обращаться к системным, что значительно уменьшит количество предупреждений о недостающих шрифтах.

---

## Полный рабочий пример

Собрав всё вместе, получаем автономный класс, который можно добавить в любой Java‑проект:

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

public class MissingFontDetector {

    public static void main(String[] args) {
        // 1️⃣ Prepare a collection for warnings.
        List<WarningInfo> fontWarnings = new ArrayList<>();

        // 2️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(info -> fontWarnings.add(info));

        // (Optional) Point to a custom font folder.
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.setFontsFolder("C:/CorporateFonts", true);
        // loadOptions.setFontSettings(fontSettings);

        // 3️⃣ Load the document.
        String docPath = "YOUR_DIRECTORY/MissingFont.docx";
        Document doc;
        try {
            doc = new Document(docPath, loadOptions);
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            return;
        }

        // 4️⃣ Print missing‑font warnings.
        System.out.println("=== Missing Font Report ===");
        for (WarningInfo warning : fontWarnings) {
            if (warning.getSource() == WarningSource.FontSubstitution) {
                System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                                   warning.getAdditionalInfo() + "'");
            }
        }
        System.out.println("=== End of Report ===");
    }
}
```

Запустите программу, и вы увидите аккуратный список всех шрифтов, которые Aspose.Words пришлось заменить. Никаких дополнительных библиотек, никакой скрытой магии — только чистый Java и мощь **Aspose.Words missing font** API.

---

## Заключение

Мы ответили на главный вопрос **как получить недостающие шрифты** в среде Java с помощью Aspose.Words. Подключив обратный вызов предупреждений `LoadOptions`, собирая объекты `WarningInfo` и фильтруя их по источнику `FontSubstitution`, вы получаете полную видимость проблем с шрифтами до любого рендеринга. Подход масштабируется от утилит для одиночных файлов до массивных пакетных процессоров и достаточно гибок для работы с пользовательскими папками шрифтов, обработкой серьёзности или вводом из потоков.

Что дальше? Попробуйте внедрить заменённые шрифты непосредственно в документ (`doc.getFontInfos().add(...)`), чтобы итоговый файл был полностью автономным, либо интегрировать отчёт о предупреждениях в панель мониторинга. Также стоит изучить связанные темы, такие как **document processing Java**, **Aspose.Words font substitution warning** и **Java LoadOptions warning callback**, чтобы углубить свои знания.

Счастливого кодинга, и пусть ваши документы всегда отображаются с ожидаемыми шрифтами!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}