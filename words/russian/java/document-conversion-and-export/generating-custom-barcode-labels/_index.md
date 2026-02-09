---
date: 2026-02-09
description: Создавайте пользовательские штрихкоды с помощью Aspose Barcode Java в
  Aspose.Words for Java. Узнайте, как встраивать штрихкоды в документы Word и генерировать
  примеры QR‑кода на Java.
linktitle: Generating Custom Barcode Labels
second_title: Aspose.Words Java Document Processing API
title: Создание пользовательских штрих‑кодов‑этикеток с помощью Aspose Barcode Java
url: /ru/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

.

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Генерация пользовательских штрих‑кодов с Aspose Barcode Java

## Введение в генерацию пользовательских штрих‑кодов в Aspose.Words for Java

Штрих‑коды являются неотъемлемой частью современных приложений, а **Aspose Barcode Java** упрощает их создание непосредственно в документах Word. Нужно **вставить штрих‑код в Word**, сгенерировать QR‑код для URL или преобразовать единицы измерения — этот учебник проведёт вас через всё необходимое. Готовы начать? Поехали!

## Быстрые ответы
- **Какая библиотека создаёт штрих‑коды в Java?** Aspose Barcode Java в паре с Aspose.Words for Java.  
- **Какой тип штрих‑кода демонстрируется?** QR‑code (generate qr code java).  
- **Как преобразовать twips в пиксели?** Используйте предоставленный метод `twipsToPixels`.  
- **Можно ли добавить штрих‑код в существующий файл Word?** Да — просто используйте метод `DocumentBuilder.insertImage`.  
- **Нужна ли лицензия?** Временная лицензия снимает ограничения оценки.

## Что такое Aspose Barcode Java?
Aspose Barcode Java — мощный API, позволяющий разработчикам программно генерировать широкий спектр 1D и 2D штрих‑кодов (включая QR‑коды). В сочетании с Aspose.Words for Java вы можете **вставить штрих‑код в Word** документы, не покидая среду Java.

## Почему стоит использовать Aspose Barcode Java вместе с Aspose.Words?
- **Полный контроль** над внешним видом штрих‑кода (цвета, размер, формат).  
- **Бесшовная интеграция** — изображение штрих‑кода можно вставить напрямую в документ Word.  
- **Кросс‑платформенность** — работает на любой платформе, совместимой с Java.  
- **Расширяемость** — можно создавать вспомогательные классы для повторного использования логики штрих‑кода в разных проектах.

## Предварительные требования

Перед тем как приступить к кодированию, убедитесь, что у вас есть следующее:

- Java Development Kit (JDK): версия 8 или выше.  
- Библиотека Aspose.Words for Java: [Download here](https://releases.aspose.com/words/java/).  
- Библиотека Aspose.BarCode for Java: [Download here](https://releases.aspose.com/).  
- Интегрированная среда разработки (IDE): IntelliJ IDEA, Eclipse или любая другая IDE.  
- Временная лицензия: получите [temporary license](https://purchase.aspose.com/temporary-license/) для снятия ограничений.

## Импорт пакетов

Мы будем использовать библиотеки Aspose.Words и Aspose.BarCode. Импортируйте следующие пакеты в ваш проект:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Эти импорты позволяют использовать функции генерации штрих‑кодов и интегрировать их в документы Word.

Разобьём задачу на управляемые шаги.

## Шаг 1: Создание вспомогательного класса для операций со штрих‑кодами

Чтобы упростить работу со штрих‑кодами, создадим утилитный класс с методами‑помощниками для общих задач, таких как преобразование цвета и **convert twips to pixels**.

### Код:

```java
class CustomBarcodeGeneratorUtils {
    public static double twipsToPixels(String heightInTwips, double defVal) {
        try {
            int lVal = Integer.parseInt(heightInTwips);
            return (lVal / 1440.0) * 96.0; // Assuming default DPI is 96
        } catch (Exception e) {
            return defVal;
        }
    }

    public static Color convertColor(String inputColor, Color defVal) {
        if (inputColor == null || inputColor.isEmpty()) return defVal;
        try {
            int color = Integer.parseInt(inputColor, 16);
            return new Color((color & 0xFF), ((color >> 8) & 0xFF), ((color >> 16) & 0xFF));
        } catch (Exception e) {
            return defVal;
        }
    }
}
```

**Пояснение**

- `twipsToPixels` преобразует единицу измерения, используемую в Word (twips), в экранные пиксели — удобный помощник, когда требуется точный размер.  
- `convertColor` переводит строку шестнадцатеричного цвета (например, “FF0000”) в объект Java `Color`, позволяя настраивать передний и задний план штрих‑кода.

## Шаг 2: Реализация пользовательского генератора штрих‑кодов

Мы реализуем интерфейс `IBarcodeGenerator`, чтобы Aspose.Words мог запрашивать изображение штрих‑кода каждый раз, когда встречает поле штрих‑кода.

### Код:

```java
class CustomBarcodeGenerator implements IBarcodeGenerator {
    public BufferedImage getBarcodeImage(BarcodeParameters parameters) {
        try {
            BarcodeGenerator gen = new BarcodeGenerator(
                CustomBarcodeGeneratorUtils.getBarcodeEncodeType(parameters.getBarcodeType()),
                parameters.getBarcodeValue()
            );

            gen.getParameters().getBarcode().setBarColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getForegroundColor(), Color.BLACK)
            );
            gen.getParameters().setBackColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getBackgroundColor(), Color.WHITE)
            );

            return gen.generateBarCodeImage();
        } catch (Exception e) {
            return new BufferedImage(100, 100, BufferedImage.TYPE_INT_ARGB);
        }
    }

    public BufferedImage getOldBarcodeImage(BarcodeParameters parameters) {
        throw new UnsupportedOperationException();
    }
}
```

**Пояснение**

- `getBarcodeImage` создаёт `BarcodeGenerator`, используя тип **generate qr code java**, который вы указываете (в примере — QR).  
- Он применяет цвета переднего и заднего плана через вспомогательные методы, затем возвращает отрисованное изображение.  
- Запасное изображение гарантирует продолжение работы программы, даже если создание штрих‑кода завершилось ошибкой.

## Шаг 3: Генерация штрих‑кода и добавление его в документ Word

Теперь объединяем всё: создаём документ, генерируем штрих‑код и **how to add barcode** в файл Word.

### Код:

```java
import com.aspose.words.*;

public class GenerateCustomBarcodeLabels {
    public static void main(String[] args) throws Exception {
        // Load or create a Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Set up custom barcode generator
        CustomBarcodeGenerator barcodeGenerator = new CustomBarcodeGenerator();
        BarcodeParameters barcodeParameters = new BarcodeParameters();
        barcodeParameters.setBarcodeType("QR");
        barcodeParameters.setBarcodeValue("https://example.com");
        barcodeParameters.setForegroundColor("000000");
        barcodeParameters.setBackgroundColor("FFFFFF");

        // Generate barcode image
        BufferedImage barcodeImage = barcodeGenerator.getBarcodeImage(barcodeParameters);

        // Insert barcode image into Word document
        builder.insertImage(barcodeImage, 200, 200);

        // Save the document
        doc.save("CustomBarcodeLabels.docx");

        System.out.println("Barcode labels generated successfully!");
    }
}
```

**Пояснение**

1. **Инициализация документа** — создаёт новый `Document` (или можно загрузить существующий .docx).  
2. **Параметры штрих‑кода** — задают тип (`QR`), значение и цвета, демонстрируя использование **generate qr code java**.  
3. **Вставка изображения** — `builder.insertImage` размещает штрих‑код в нужном месте, фактически показывая **how to add barcode** в файл Word.  
4. **Сохранение** — конечный документ (`CustomBarcodeLabels.docx`) содержит встроенный штрих‑код, готовый к печати или распространению.

## Распространённые проблемы и решения

| Проблема | Причина | Решение |
|----------|---------|---------|
| Штрих‑код отображается пустым | Неправильная строка цвета или неподдерживаемый тип штрих‑кода | Проверьте формат шестнадцатеричного цвета и используйте поддерживаемый тип (например, QR, Code128). |
| Размер изображения неверный | Ошибка при преобразовании в пиксели | Используйте `twipsToPixels` для точного расчёта размеров на основе разметки Word. |
| Исключение лицензии | Отсутствует действительная лицензия Aspose | Примените временную или приобретённую лицензию перед запуском кода. |

## Часто задаваемые вопросы

**В: Можно ли использовать Aspose.Words for Java без лицензии?**  
О: Да, но будут ограничения оценки. Получите [temporary license](https://purchase.aspose.com/temporary-license/) для полной функциональности.

**В: Какие типы штрих‑кодов я могу генерировать?**  
О: Aspose.BarCode поддерживает QR, Code 128, EAN‑13 и многие другие. См. официальную [documentation](https://reference.aspose.com/words/java/) для полного списка.

**В: Как изменить размер штрих‑кода?**  
О: Отрегулируйте параметры ширины/высоты в `builder.insertImage` или измените свойства `XDimension` и `BarHeight` у объекта `BarcodeGenerator`.

**В: Можно ли использовать пользовательские шрифты для читаемой части штрих‑кода?**  
О: Конечно. Используйте свойство `CodeTextParameters` для задания семейства шрифта, размера и стиля.

**В: Где можно получить помощь по Aspose.Words?**  
О: Посетите [support forum](https://forum.aspose.com/c/words/8/) для общения с сообществом и официальной поддержки.

---

**Последнее обновление:** 2026-02-09  
**Тестировано с:** Aspose.Words for Java 24.12, Aspose.BarCode for Java 24.12  
**Автор:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}