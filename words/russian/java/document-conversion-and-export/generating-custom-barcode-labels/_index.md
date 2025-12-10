---
date: 2025-12-10
description: "Узнайте, как создавать пользовательские штрих‑коды с помощью Aspose.Words
  для Java. Этот пошаговый руководств\n\n показывает, как встраивать штрих‑коды в
  документы Word."
linktitle: Generating Custom Barcode Labels
second_title: Aspose.Words Java Document Processing API
title: Создание пользовательских штрих‑кодов в Aspose.Words для Java
url: /ru/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Генерация пользовательских штрих‑кодов в Aspose.Words для Java

## Введение в генерацию пользовательских штрих‑кодов в Aspose.Words для Java

Штрих‑коды являются неотъемлемой частью современных приложений — будь то управление запасами, печать билетов или создание удостоверений личности. В этом руководстве вы **создадите пользовательские метки со штрих‑кодом** и внедрите их непосредственно в документ Word с помощью интерфейса `IBarcodeGenerator`. Мы пройдем каждый шаг, от настройки окружения до вставки изображения штрих‑кода, чтобы вы могли сразу начать использовать штрих‑коды в своих Java‑проектах.

## Быстрые ответы
- **Что изучает это руководство?** Как генерировать пользовательские метки со штрих‑кодом и внедрять их в файл Word с помощью Aspose.Words для Java.  
- **Какой тип штрих‑кода используется в примере?** QR‑код (можно заменить на любой поддерживаемый тип).  
- **Нужна ли лицензия?** Для неограниченного доступа во время разработки требуется временная лицензия.  
- **Какая версия Java требуется?** JDK 8 или выше.  
- **Можно ли изменить размер или цвета штрих‑кода?** Да — измените настройки `BarcodeParameters` и `BarcodeGenerator`.

## Предварительные требования

Прежде чем приступить к кодированию, убедитесь, что у вас есть следующее:

- Java Development Kit (JDK): версия 8 или выше.  
- Библиотека Aspose.Words для Java: [Download here](https://releases.aspose.com/words/java/).  
- Библиотека Aspose.BarCode для Java: [Download here](https://releases.aspose.com/).  
- Интегрированная среда разработки (IDE): IntelliJ IDEA, Eclipse или любая другая IDE.  
- Временная лицензия: получите [temporary license](https://purchase.aspose.com/temporary-license/) для неограниченного доступа.

## Импорт пакетов

Мы будем использовать библиотеки Aspose.Words и Aspose.BarCode. Импортируйте следующие пакеты в ваш проект:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Эти импорты дают нам доступ к API генерации штрих‑кода и классам документа Word, которые нам потребуются.

## Шаг 1: Создание вспомогательного класса для операций со штрих‑кодом

Чтобы основной код оставался чистым, мы инкапсулируем общие вспомогательные функции — такие как **преобразование twips в пиксели** и **конвертация hex‑цвета** — во вспомогательном классе.

### Код

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

- `twipsToPixels` — Word измеряет размеры в **twips**; этот метод преобразует их в пиксели экрана, что удобно при точной настройке размеров штрих‑кода.  
- `convertColor` — Преобразует шестнадцатеричную строку (например, `"FF0000"` для красного) в объект `java.awt.Color`, позволяя **вставлять штрих‑код** с пользовательскими цветами переднего и заднего плана.

## Шаг 2: Реализация пользовательского генератора штрих‑кода

Теперь реализуем интерфейс `IBarcodeGenerator`. Этот класс будет отвечать за **генерацию изображений qr‑code java**‑стиля, которые Aspose.Words сможет внедрять.

### Код

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

- `getBarcodeImage` создает экземпляр `BarcodeGenerator`, применяет цвета, переданные через `BarcodeParameters`, и в конце возвращает `BufferedImage`.  
- Метод также корректно обрабатывает ошибки, возвращая изображение‑заполнитель, что гарантирует отсутствие сбоев при создании документа Word.

## Шаг 3: Генерация штрих‑кода и **вставка штрих‑кода в Word**

С готовым генератором мы можем создать изображение штрих‑кода и **вставить его в документ Word**.

### Код

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

1. **Инициализация документа** — Создает новый `Document` (или можно загрузить существующий шаблон).  
2. **Параметры штрих‑кода** — Определяют тип штрих‑кода (`QR`), значение для кодирования и цвета переднего/заднего плана.  
3. **Вставка изображения** — `builder.insertImage` размещает сгенерированный штрих‑код нужного размера (200 × 200 пикселей). Это ядро **вставки штрих‑кода** в файл Word.  
4. **Сохранение** — Финальный документ `CustomBarcodeLabels.docx` содержит встроенный штрих‑код, готовый к печати или распространению.

## Почему генерировать пользовательские метки со штрих‑кодом с помощью Aspose.Words?

- **Полный контроль** над внешним видом штрих‑кода (тип, размер, цвета).  
- **Бесшовная интеграция** — нет необходимости в промежуточных файлах изображений; штрих‑код генерируется в памяти и вставляется напрямую.  
- **Кросс‑платформенность** — работает на любой ОС, поддерживающей Java, что делает его идеальным для серверной генерации документов.  
- **Масштабируемость** — можно перебрать источник данных и создать сотни персонализированных меток за один запуск.

## Распространённые проблемы и их решение

| Симптом | Вероятная причина | Решение |
|---------|-------------------|---------|
| Штрих‑код отображается пустым | Цвета `BarcodeParameters` одинаковы (например, черный на черном) | Проверьте значения `foregroundColor` и `backgroundColor`. |
| Изображение искажено | Неправильные пиксельные размеры, переданные в `insertImage` | Скорректируйте аргументы ширины/высоты или используйте конвертацию `twipsToPixels` для точного размера. |
| Ошибка «Unsupported barcode type» | Используется тип, не распознанный `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` | Убедитесь, что строка типа штрих‑кода соответствует одному из поддерживаемых `EncodeTypes` (например, `"QR"`, `"CODE128"`). |

## Часто задаваемые вопросы

**В: Можно ли использовать Aspose.Words для Java без лицензии?**  
О: Да, но будут ограничения. Получите [temporary license](https://purchase.aspose.com/temporary-license/) для полной функциональности.

**В: Какие типы штрих‑кодов я могу генерировать?**  
О: Aspose.BarCode поддерживает QR, Code 128, EAN‑13 и многие другие форматы. См. [documentation](https://reference.aspose.com/words/java/) для полного списка.

**В: Как изменить размер штрих‑кода?**  
О: Отрегулируйте аргументы ширины и высоты в `builder.insertImage` или используйте `twipsToPixels` для преобразования единиц измерения Word в пиксели.

**В: Можно ли использовать пользовательские шрифты для текста штрих‑кода?**  
О: Да, шрифт текста можно настроить через свойство `CodeTextParameters` объекта `BarcodeGenerator`.

**В: Где получить помощь при возникновении проблем?**  
О: Посетите [support forum](https://forum.aspose.com/c/words/8/) для получения помощи от сообщества и инженеров Aspose.

## Заключение

Следуя приведённым шагам, вы теперь знаете, как **генерировать пользовательские изображения штрих‑кода** и **вставлять штрих‑код в документы Word** с помощью Aspose.Words для Java. Этот метод достаточно гибок для меток инвентаря, билетов на мероприятия или любой ситуации, когда штрих‑код должен быть частью генерируемого документа. Экспериментируйте с различными типами штрих‑кодов и параметрами стилизации, чтобы подобрать оптимальное решение под ваши бизнес‑задачи.

---

**Последнее обновление:** 2025-12-10  
**Тестировано с:** Aspose.Words для Java 24.12, Aspose.BarCode для Java 24.12  
**Автор:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}