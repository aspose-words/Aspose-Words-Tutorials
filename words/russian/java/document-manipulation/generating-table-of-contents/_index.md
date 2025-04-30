---
"description": "Узнайте, как создавать и настраивать оглавление (TOC) с помощью Aspose.Words для Java. Создавайте организованные и профессиональные документы без усилий."
"linktitle": "Создание оглавления"
"second_title": "API обработки документов Java Aspose.Words"
"title": "Создание оглавления в Aspose.Words для Java"
"url": "/ru/java/document-manipulation/generating-table-of-contents/"
"weight": 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Создание оглавления в Aspose.Words для Java


## Введение в генерацию оглавления в Aspose.Words для Java

В этом уроке мы проведем вас через процесс создания оглавления (TOC) с помощью Aspose.Words для Java. TOC — это важная функция для создания организованных документов. Мы рассмотрим, как настроить внешний вид и макет TOC.

## Предпосылки

Прежде чем начать, убедитесь, что в вашем проекте Java установлен и настроен Aspose.Words для Java.

## Шаг 1: Создайте новый документ

Для начала давайте создадим новый документ, с которым будем работать.

```java
Document doc = new Document();
```

## Шаг 2: Настройте стили оглавления

Чтобы настроить внешний вид вашего TOC, вы можете изменить стили, связанные с ним. В этом примере мы сделаем записи TOC первого уровня жирными.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

## Шаг 3: Добавьте содержимое в документ

Вы можете добавить свой контент в документ. Этот контент будет использован для генерации TOC.

## Шаг 4: Создание оглавления

Чтобы сгенерировать TOC, вставьте поле TOC в нужное место в вашем документе. Это поле будет автоматически заполнено на основе заголовков и стилей в вашем документе.

```java
// Вставьте поле оглавления в нужное место документа.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

## Шаг 5: Сохраните документ.

Наконец, сохраните документ с оглавлением.

```java
doc.save("your_output_path_here");
```

## Настройка позиций табуляции в оглавлении

Вы также можете настроить табуляции в вашем TOC, чтобы контролировать макет номеров страниц. Вот как можно изменить табуляции:

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Получите первую табуляцию, использованную в этом абзаце, которая выравнивает номера страниц.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Удалите старую вкладку.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // Вставьте новую вкладку в измененной позиции (например, на 50 единиц влево).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

Теперь в вашем документе есть настроенное оглавление с настроенными позициями табуляции для выравнивания номеров страниц.


## Заключение

В этом уроке мы изучили, как создать оглавление (TOC) с помощью Aspose.Words для Java, мощной библиотеки для работы с документами Word. Хорошо структурированное оглавление необходимо для организации и навигации по длинным документам, и Aspose.Words предоставляет инструменты для создания и настройки оглавлений без усилий.

## Часто задаваемые вопросы

### Как изменить форматирование записей TOC?

Вы можете изменить стили, связанные с уровнями TOC, используя `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`, где X — уровень TOC.

### Как добавить больше уровней в TOC?

Чтобы включить больше уровней в оглавление, вы можете изменить поле оглавления и указать желаемое количество уровней.

### Могу ли я изменить позиции табуляции для определенных записей оглавления?

Да, как показано в примере кода выше, вы можете изменить позиции табуляции для определенных записей оглавления, перебирая абзацы и изменяя позиции табуляции соответствующим образом.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}