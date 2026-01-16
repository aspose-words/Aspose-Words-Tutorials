---
date: 2026-01-16
description: Узнайте, как преобразовать дюймы в пункты, читать метаданные документа
  в Java, добавлять пользовательские свойства в Java и задавать поля страницы в Java
  с помощью Aspose.Words для Java.
linktitle: Using Document Properties
second_title: Aspose.Words Java Document Processing API
title: Преобразование дюймов в пункты — использование свойств документа в Aspose.Words
  для Java
url: /ru/java/document-manipulation/using-document-properties/
weight: 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Конвертация дюймов в пункты – использование свойств документа в Aspose.Words для Java

В этом руководстве вы узнаете, как **конвертировать дюймы в пункты** при установке полей страницы, читать document metadata Java, добавлять custom properties Java и работать со built‑in document properties с помощью Aspose.Words для Java. Независимо от того, генерируете ли вы отчёты, счета‑фактуры или юридические документы, освоив эти техники, вы получите тонкий контроль над внешним видом и метаданными ваших файлов Word.

## Быстрые ответы
- **Как конвертировать дюймы в пункты?** Используйте `ConvertUtil.inchToPoint(value)` из Aspose.Words.
- **Можно ли читать метаданные документа в Java?** Да — вызовите `doc.getBuiltInDocumentProperties()` или `doc.getCustomDocumentProperties()`.
- **Как добавить custom property в Java?** Используйте `doc.getCustomDocumentProperties().add(name, value)`.
- **Какой метод задает поля страницы в пунктах?** `PageSetup.setTopMargin`, `setBottomMargin` и т.д. принимают значения в пунктах.
- **Поддерживается ли ссылка на закладку?** Да — используйте `addLinkToContent` в коллекции custom properties.

## Введение в свойства документа

Свойства документа являются важной частью любого файла Word. Они хранят информацию, такую как title, author, subject, keywords и любые custom metadata, необходимые для последующей обработки. В Aspose.Words для Java вы можете управлять как built‑in, так и custom document properties, а также контролировать детали макета, такие как поля, конвертируя единицы измерения (например, **convert inches to points**).

## Что такое «convert inches to points»?

В Word измерения макета задаются в пунктах (1 point = 1/72 дюйма). Конвертация дюймов в пункты позволяет задавать поля, отступы и интервалы, используя привычные имперские единицы, в то время как API работает с пунктами внутри.

## Почему управлять метаданными документа в Java?

Встраивание metadata упрощает поиск, категоризацию и автоматизацию рабочих процессов. Например, вы можете пометить контракт флагом “Authorized” или сохранить номер ревизии для аудита. Чтение и запись этой информации программно обеспечивает согласованность при работе с большими партиями документов.

## Предварительные требования
- Java 17+ (или совместимый JDK)
- Библиотека Aspose.Words для Java, добавленная в ваш проект (Maven/Gradle)
- Пример файла `.docx` (например, `Properties.docx`), размещённый в доступном каталоге

## Пошаговое руководство

### Перечисление built‑in свойств документа
Ниже простой тест, который открывает документ и выводит все built‑in свойства, такие как Title, Author и Keywords.

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

> **Pro tip:** Используйте этот фрагмент, чтобы убедиться, что ваши метаданные были корректно записаны на предыдущих шагах.

### Добавление custom свойств документа (add custom properties java)
Custom properties позволяют хранить любые типы данных, которые вам нужны — boolean, string, date, number и т.д.

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

> **Почему это важно:** Добавление флага, например **Authorized**, может управлять downstream процессами одобрения без изменения содержимого документа.

### Удаление custom свойства
Если свойство больше не требуется, вы можете удалить его чисто.

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

### Настройка ссылки на контент (bookmark linking)
Вы можете создать bookmark, а затем добавить custom property, указывающий на эту закладку, что позволяет создавать динамические перекрёстные ссылки.

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // Add linked to content property.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

### Конвертация между единицами измерения (set page margins java)
Здесь проявляется основной ключевой запрос. Мы задаём поля в дюймах, а затем **convert inches to points** с помощью `ConvertUtil`.

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Set margins in inches.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

> **Примечание:** `ConvertUtil` также предоставляет `pointToInch`, `mmToPoint` и т.д. для гибкой работы с макетом.

### Использование управляющих символов (read document metadata java)
Управляющие символы помогают очистить текстовые потоки. Этот пример заменяет возврат каретки (`\r`) на последовательность разрыва строки Windows (`\r\n`).

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Replace "\r" control character with "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

## Распространённые проблемы и решения

| Проблема | Причина | Решение |
|----------|---------|---------|
| Поля выглядят неправильно после конвертации | Использована неправильная единица измерения (например, см вместо дюймов) | Убедитесь, что вызываете `ConvertUtil.inchToPoint` для значений в дюймах |
| Custom property не отображается | Свойство добавлено после сохранения документа | Вызовите `doc.save(...)` после добавления свойств |
| Ссылка на закладку не работает | Опечатка в имени закладки | Убедитесь, что имя закладки точно совпадает в `addLinkToContent` |

## Часто задаваемые вопросы

### Как получить доступ к built‑in свойствам документа?

Чтобы получить доступ к built‑in свойствам документа в Aspose.Words для Java, используйте метод `getBuiltInDocumentProperties` объекта `Document`. Этот метод возвращает коллекцию built‑in свойств, по которой можно итерировать.

### Можно ли добавить custom свойства документа в документ?

Да, вы можете добавить custom свойства документа, используя коллекцию `CustomDocumentProperties`. Вы можете определить custom properties с различными типами данных, включая strings, booleans, dates и numeric values.

### Как удалить конкретное custom свойство документа?

Чтобы удалить конкретное custom свойство документа, используйте метод `remove` коллекции `CustomDocumentProperties`, передав имя свойства, которое нужно удалить, в качестве параметра.

### Какова цель ссылки на контент внутри документа?

Ссылка на контент внутри документа позволяет создавать динамические ссылки на определённые части документа. Это полезно для создания интерактивных документов или перекрёстных ссылок между разделами.

### Как конвертировать между разными единицами измерения в Aspose.Words для Java?

Вы можете конвертировать между разными единицами измерения в Aspose.Words для Java, используя класс `ConvertUtil`. Он предоставляет методы для преобразования единиц, таких как inches в points, points в centimeters и многое другое.

## Часто задаваемые вопросы

**Q: Как прочитать document metadata Java без полной загрузки файла?**  
A: Используйте `DocumentInfo` для получения основных свойств без полной загрузки содержимого документа.

**Q: Можно ли программно задать поля страницы Java для существующих документов?**  
A: Да — откройте документ, измените поля `PageSetup` (при необходимости конвертируйте inches в points) и сохраните.

**Q: Возможно ли экспортировать custom properties в PDF metadata?**  
A: При сохранении в PDF Aspose.Words автоматически сопоставляет custom document properties с PDF custom metadata.

**Q: Влияют ли управляющие символы на конвертацию в PDF?**  
A: Они сохраняются при конвертации; однако может потребоваться нормализовать окончания строк для согласованности.

**Q: Какая версия Aspose.Words требуется для `ConvertUtil`?**  
A: `ConvertUtil` доступен, начиная с Aspose.Words 16.5; любая современная версия поддерживает его.

## Заключение

Освоив **convert inches to points**, чтение document metadata Java и добавление custom properties Java, вы получаете полный контроль как над визуальным макетом, так и над скрытыми данными ваших файлов Word. Эти возможности позволяют создавать автоматизированные конвейеры обработки документов, обеспечивать соблюдение требований и формировать богато оформленные отчёты — всё с помощью Aspose.Words для Java.

---

**Последнее обновление:** 2026-01-16  
**Тестировано с:** Aspose.Words для Java 24.11  
**Автор:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}