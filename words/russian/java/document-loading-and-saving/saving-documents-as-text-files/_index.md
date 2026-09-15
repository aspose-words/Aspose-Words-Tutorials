---
date: 2025-12-24
description: Узнайте, как создать текстовый файл из документов Word с помощью Aspose.Words
  для Java. Это руководство показывает, как преобразовать Word в txt, использовать
  табуляцию и сохранить документ Word как txt.
linktitle: Saving Documents as Text Files
second_title: Aspose.Words Java Document Processing API
title: Как создать простой текстовый файл с помощью Aspose.Words для Java
url: /ru/java/document-loading-and-saving/saving-documents-as-text-files/
weight: 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Как создать plain text файл с Aspose.Words для Java

## Введение в сохранение документов в виде текстовых файлов в Aspose.Words для Java

В этом руководстве вы узнаете **как создать plain text файл** из документа Word с помощью библиотеки Aspose.Words для Java. Независимо от того, нужно ли вам **конвертировать word в txt**, автоматизировать генерацию отчётов или просто извлечь сырой текст для дальнейшей обработки, это руководство проведёт вас через весь процесс — от создания документа до тонкой настройки параметров сохранения, таких как **использовать табуляцию для отступов** или добавить bidi‑метки. Приступим!

## Быстрые ответы
- **Какой основной класс используется для создания документа?** `Document` из Aspose.Words.  
- **Какой параметр добавляет bidi‑метки для языков с письмом справа налево?** `TxtSaveOptions.setAddBidiMarks(true)`.  
- **Как задать отступ элементов списка с помощью табов?** Установите `ListIndentation.Character` в `'\t'`.  
- **Нужна ли лицензия для разработки?** Бесплатная trial‑версия подходит для тестирования; для продакшн‑использования требуется лицензия.  
- **Могу ли я сохранить файл с произвольным именем и путём?** Да — передайте полный путь в `doc.save()`.

## Предварительные требования

Прежде чем начать, убедитесь, что у вас есть следующее:

- Установленный Java Development Kit (JDK) на вашей системе.  
- Библиотека Aspose.Words for Java, интегрированная в ваш проект. Вы можете скачать её [здесь](https://releases.aspose.com/words/java/).  
- Базовые знания программирования на Java.

## Шаг 1: Создать документ

Чтобы **сохранить word как txt**, нам сначала нужен экземпляр `Document`. Ниже простой Java‑фрагмент, который создаёт документ и записывает несколько строк многоязычного текста:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

В этом коде мы создаём новый документ, добавляем английский, иврит и арабский тексты, и включаем форматирование справа налево для абзаца на иврите.

## Шаг 2: Определить параметры сохранения текста

Далее мы настраиваем, как документ будет сохраняться в виде plain text файла. Aspose.Words предоставляет класс `TxtSaveOptions`, который позволяет управлять всем — от bidi‑меток до отступов списка.

### Пример 1: Добавление bidi‑меток (как сохранить txt с корректной поддержкой RTL)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

Установка `AddBidiMarks` в `true` гарантирует, что символы справа налево правильно отображаются в получаемом **plain text файле**.

### Пример 2: Использование символа табуляции для отступов списка (use tab indentation)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Здесь мы указываем Aspose.Words добавить символ табуляции (`'\t'`) перед каждым уровнем списка, делая вывод текста более читабельным.

## Шаг 3: Сохранить документ как текст

Теперь, когда параметры сохранения готовы, вы можете сохранить документ как **plain text файл**:

```java
doc.save("output.txt", saveOptions);
```

Замените `"output.txt"` полным путём, где вы хотите сохранить файл.

## Полный исходный код для сохранения документов в виде текстовых файлов в Aspose.Words для Java

```java
    public void addBidiMarks() throws Exception
    {        
		Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("Hello world!");
        builder.getParagraphFormat().setBidi(true);
        builder.writeln("שלום עולם!");
        builder.writeln("مرحبا بالعالم!");
        TxtSaveOptions saveOptions = new TxtSaveOptions(); { saveOptions.setAddBidiMarks(true); }
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
    }
    @Test
    public void useTabCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Create a list with three levels of indentation.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(1);
        saveOptions.getListIndentation().setCharacter('\t');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseTabCharacterPerLevelForListIndentation.txt", saveOptions);
    }
    @Test
    public void useSpaceCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Create a list with three levels of indentation.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(3);
        saveOptions.getListIndentation().setCharacter(' ');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
	}
```

## Распространённые проблемы и решения

| Проблема | Решение |
|----------|---------|
| **Bidi‑символы отображаются как нечитаемый текст** | Убедитесь, что включён `setAddBidiMarks(true)` и файл открывается с кодировкой UTF‑8. |
| **Отступы списка выглядят неправильно** | Проверьте, что `ListIndentation.Count` и `Character` установлены в нужные значения (таб `'\t'` или пробел `' '` ). |
| **Файл не создан** | Убедитесь, что путь к директории существует и приложение имеет права на запись. |

## Часто задаваемые вопросы

### Как добавить bidi‑метки к выходному тексту?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Можно ли настроить символ отступа списка?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Подходит ли Aspose.Words для Java для работы с многоязычным текстом?

Да, Aspose.Words for Java поддерживает широкий спектр языков и кодировок, что делает её идеальной для извлечения и сохранения многоязычного контента в виде plain text.

### Как получить доступ к дополнительной документации и ресурсам по Aspose.Words для Java?

Вы можете найти полную документацию и ресурсы на странице Aspose.Words for Java Documentation: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

### Где можно скачать Aspose.Words для Java?

Вы можете скачать библиотеку с официального сайта: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/).

### Что делать, если нужно **конвертировать word в txt** в пакетном режиме?

Оберните показанный выше код в цикл, который загружает каждый файл `.docx`, применяет те же `TxtSaveOptions` и сохраняет каждый как `.txt`. Убедитесь, что освобождаете ресурсы, удаляя объекты `Document` после каждой итерации.

### Поддерживает ли API сохранение напрямую в поток вместо файла?

Да, вы можете передать `OutputStream` в `doc.save(outputStream, saveOptions)` для обработки в памяти или при интеграции с веб‑сервисами.

---

**Последнее обновление:** 2025-12-24  
**Тестировано с:** Aspose.Words for Java 24.12 (latest)  
**Автор:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}