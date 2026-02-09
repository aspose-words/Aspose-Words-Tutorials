---
date: 2026-02-09
description: Generuj własne etykiety z kodami kreskowymi przy użyciu Aspose Barcode
  Java w Aspose.Words for Java. Dowiedz się, jak osadzić kod kreskowy w dokumentach
  Word oraz generować przykłady kodów QR w Javie.
linktitle: Generating Custom Barcode Labels
second_title: Aspose.Words Java Document Processing API
title: Generowanie niestandardowych etykiet kodów kreskowych z Aspose Barcode Java
url: /pl/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Generowanie niestandardowych etykiet kodów kreskowych przy użyciu Aspose Barcode Java

## Wprowadzenie do generowania niestandardowych etykiet kodów kreskowych w Aspose.Words dla Javy

Kody kreskowe są niezbędne w nowoczesnych aplikacjach, a **Aspose Barcode Java** ułatwia ich tworzenie bezpośrednio w dokumentach Word. Niezależnie od tego, czy musisz **embed barcode in Word**, wygenerować kod QR dla adresu URL, czy przeliczyć jednostki miary, ten samouczek przeprowadzi Cię przez wszystko, czego potrzebujesz. Gotowy, aby zanurzyć się w temat? Zaczynajmy!

## Szybkie odpowiedzi
- **Jaka biblioteka tworzy kody kreskowe w Javie?** Aspose Barcode Java paired with Aspose.Words for Java.  
- **Jaki typ kodu kreskowego jest pokazany?** QR code (generate qr code java).  
- **Jak przeliczyć twipsy na piksele?** Use the provided `twipsToPixels` utility method.  
- **Czy mogę dodać kod kreskowy do istniejącego pliku Word?** Yes – just use the `DocumentBuilder.insertImage` method.  
- **Czy potrzebuję licencji?** A temporary license removes evaluation limits.

## Czym jest Aspose Barcode Java?
Aspose Barcode Java to potężne API, które umożliwia programistom generowanie szerokiej gamy kodów kreskowych 1D i 2D (w tym kodów QR) w sposób programowy. W połączeniu z Aspose.Words dla Javy, możesz **embed barcode in Word** dokumenty bez opuszczania środowiska Java.

## Dlaczego warto używać Aspose Barcode Java z Aspose.Words?
- **Pełna kontrola** nad wyglądem kodu kreskowego (kolory, rozmiar, format).  
- **Bezproblemowa integracja** – obraz kodu kreskowego może być wstawiony bezpośrednio do dokumentu Word.  
- **Cross‑platform** – działa na każdej platformie zgodnej z Javą.  
- **Rozszerzalny** – możesz tworzyć klasy pomocnicze, aby ponownie wykorzystywać logikę kodów kreskowych w różnych projektach.

## Wymagania wstępne

Before we start coding, ensure you have the following:

- Java Development Kit (JDK): wersja 8 lub wyższa.  
- Aspose.Words for Java Library: [Download here](https://releases.aspose.com/words/java/).  
- Aspose.BarCode for Java Library: [Download here](https://releases.aspose.com/).  
- Zintegrowane środowisko programistyczne (IDE): IntelliJ IDEA, Eclipse lub dowolne IDE, które preferujesz.  
- Licencja tymczasowa: uzyskaj [temporary license](https://purchase.aspose.com/temporary-license/) dla nieograniczonego dostępu.

## Importowanie pakietów

We’ll use Aspose.Words and Aspose.BarCode libraries. Import the following packages into your project:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

These imports allow us to utilize barcode generation features and integrate them into Word documents.

Let’s break this task into manageable steps.

## Krok 1: Utwórz klasę pomocniczą dla operacji kodów kreskowych

To simplify barcode‑related operations, we’ll create a utility class with helper methods for common tasks, such as color conversion and **convert twips to pixels**.

### Code:

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

**Wyjaśnienie**

- `twipsToPixels` konwertuje jednostkę miary używaną w Wordzie (twips) na piksele ekranu – przydatny pomocnik, gdy potrzebne jest precyzyjne rozmiarowanie.  
- `convertColor` przetwarza szesnastkowy ciąg kolorów (np. “FF0000”) na obiekt Java `Color`, umożliwiając dostosowanie pierwszego planu i tła kodu kreskowego.

## Krok 2: Zaimplementuj własny generator kodów kreskowych

Zaimplementujemy interfejs `IBarcodeGenerator`, aby Aspose.Words mógł żądać obrazu kodu kreskowego za każdym razem, gdy napotka pole kodu kreskowego.

### Code:

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

**Wyjaśnienie**

- `getBarcodeImage` tworzy `BarcodeGenerator` używając typu **generate qr code java**, który określasz (QR w naszym przykładzie).  
- Stosuje kolory pierwszego planu i tła za pomocą metod pomocniczych, a następnie zwraca wyrenderowany obraz.  
- Obraz zapasowy zapewnia kontynuację programu, nawet jeśli tworzenie kodu kreskowego się nie powiedzie.

## Krok 3: Wygeneruj kod kreskowy i dodaj go do dokumentu Word

Teraz łączymy wszystko: tworzymy dokument, generujemy kod kreskowy i **how to add barcode** do pliku Word.

### Code:

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

**Wyjaśnienie**

1. **Inicjalizacja dokumentu** – tworzy nowy `Document` (lub możesz załadować istniejący .docx).  
2. **Parametry kodu kreskowego** – definiują typ (`QR`), wartość i kolory, demonstrując użycie **generate qr code java**.  
3. **Wstawianie obrazu** – `builder.insertImage` umieszcza kod kreskowy w wybranym miejscu, skutecznie pokazując **how to add barcode** do pliku Word.  
4. **Zapisywanie** – końcowy dokument (`CustomBarcodeLabels.docx`) zawiera wbudowany kod kreskowy gotowy do druku lub dystrybucji.

## Typowe problemy i rozwiązania

| Problem | Przyczyna | Rozwiązanie |
|---------|-----------|-------------|
| Kod kreskowy pojawia się pusty | Nieprawidłowy ciąg kolorów lub nieobsługiwany typ kodu kreskowego | Zweryfikuj format szesnastkowy koloru i użyj obsługiwanego typu (np. QR, Code128). |
| Rozmiar obrazu jest nieprawidłowy | Niepoprawna konwersja pikseli | Użyj `twipsToPixels`, aby obliczyć dokładne wymiary na podstawie układu Worda. |
| Wyjątek licencyjny | Brak ważnej licencji Aspose | Zastosuj tymczasową lub zakupioną licencję przed uruchomieniem kodu. |

## Najczęściej zadawane pytania

**Q: Czy mogę używać Aspose.Words dla Javy bez licencji?**  
A: Tak, ale napotkasz ograniczenia wersji ewaluacyjnej. Uzyskaj [temporary license](https://purchase.aspose.com/temporary-license/) dla pełnej funkcjonalności.

**Q: Jakie typy kodów kreskowych mogę generować?**  
A: Aspose.BarCode obsługuje QR, Code 128, EAN‑13 i wiele innych. Zobacz oficjalną [documentation](https://reference.aspose.com/words/java/) po pełną listę.

**Q: Jak mogę zmienić rozmiar kodu kreskowego?**  
A: Dostosuj parametry szerokości/wysokości w `builder.insertImage` lub zmodyfikuj właściwości `XDimension` i `BarHeight` obiektu `BarcodeGenerator`.

**Q: Czy mogę używać własnych czcionek dla części czytelnej dla człowieka w kodzie kreskowym?**  
A: Oczywiście. Użyj właściwości `CodeTextParameters`, aby ustawić rodzinę czcionki, rozmiar i styl.

**Q: Gdzie mogę uzyskać pomoc dotyczącą Aspose.Words?**  
A: Odwiedź [support forum](https://forum.aspose.com/c/words/8/) po pomoc społeczności i oficjalne wsparcie.

---

**Ostatnia aktualizacja:** 2026-02-09  
**Testowano z:** Aspose.Words for Java 24.12, Aspose.BarCode for Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}