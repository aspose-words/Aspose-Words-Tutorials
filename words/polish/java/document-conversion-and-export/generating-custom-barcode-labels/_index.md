---
date: 2026-10-23
description: Dowiedz się, jak tworzyć etykiety Java z kodem QR przy użyciu Aspose.Words.
  Ten przewodnik krok po kroku pokazuje, jak osadzać barcode w dokumentach Word oraz
  dostosowywać rozmiar, kolory i format.
keywords:
- create qr code java
- how to create barcode label
- add barcode to word document
- embed barcode in word
lastmod: 2026-10-23
linktitle: Generowanie niestandardowych etykiet Barcode
og_description: Dowiedz się, jak tworzyć etykiety Java z kodem QR przy użyciu Aspose.Words.
  Ten przewodnik wyjaśnia osadzanie barcode, kontrolę rozmiaru oraz dostosowywanie
  kolorów w dokumentach Word.
og_image_alt: 'Developer guide: generate custom QR code labels in Java with Aspose.Words'
og_title: Jak tworzyć etykiety Java z kodem QR przy użyciu Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to create QR code Java labels with Aspose.Words. This step‑by‑step
    guide shows you how to embed barcodes in Word documents and customize size, colors,
    and format.
  headline: How to create QR code Java labels using Aspose.Words
  type: TechArticle
- description: Learn how to create QR code Java labels with Aspose.Words. This step‑by‑step
    guide shows you how to embed barcodes in Word documents and customize size, colors,
    and format.
  name: How to create QR code Java labels using Aspose.Words
  steps:
  - name: '**Document initialization** – Creates a fresh `Document` (or you could
      load an existing template).'
    text: '**Document initialization** – Creates a fresh `Document` (or you could
      load an existing template).'
  - name: '**Barcode parameters** – Defines the barcode type (`QR`), the value to
      encode, and the foreground/background colors.'
    text: '**Barcode parameters** – Defines the barcode type (`QR`), the value to
      encode, and the foreground/background colors.'
  - name: '**Image insertion** – `builder.insertImage` places the generated barcode
      at the desired size (200 × 200 pixels). This is the core of **how to embed barcode
      in Word**.'
    text: '**Image insertion** – `builder.insertImage` places the generated barcode
      at the desired size (200 × 200 pixels). This is the core of **how to embed barcode
      in Word**.'
  - name: '**Saving** – The final document, `CustomBarcodeLabels.docx`, contains the
      embedded barcode ready for printing or distribution.'
    text: '**Saving** – The final document, `CustomBarcodeLabels.docx`, contains the
      embedded barcode ready for printing or distribution.'
  type: HowTo
- questions:
  - answer: Yes, but it will have evaluation limitations. Obtain a [temporary license](https://purchase.aspose.com/temporary-license/)
      for full functionality.
    question: Can I use Aspose.Words for Java without a license?
  - answer: Aspose.BarCode supports QR, Code 128, EAN‑13, DataMatrix, PDF417, and
      many other formats—over 20 symbologies in total. See the [documentation](https://reference.aspose.com/words/java/)
      for the complete list.
    question: What types of barcodes can I generate?
  - answer: Adjust the width and height arguments in `builder.insertImage`, or calculate
      exact Word twips using `twipsToPixels` for pixel‑perfect control.
    question: How can I change the barcode size?
  - answer: Yes, you can customize the text font through the `CodeTextParameters`
      property of the `BarcodeGenerator`.
    question: Is it possible to use custom fonts for the barcode text?
  - answer: Visit the [support forum](https://forum.aspose.com/c/words/8/) for assistance
      from the Aspose community and engineers.
    question: Where can I get help if I run into problems?
  type: FAQPage
second_title: Aspose.Words Java Document Processing API
tags:
- barcode generation
- Aspose.Words
- Java document processing
- QR code
title: Jak tworzyć etykiety Java z kodem QR przy użyciu Aspose.Words
url: /pl/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak tworzyć etykiety QR code w Javie przy użyciu Aspose.Words

Kody kreskowe są niezbędne w nowoczesnych aplikacjach — niezależnie od tego, czy zarządzasz zapasami, drukujesz bilety, czy tworzysz karty identyfikacyjne. W tym samouczku **utworzysz etykiety QR code w Javie** i osadzisz je bezpośrednio w dokumencie Word przy użyciu interfejsu `IBarcodeGenerator`. Przejdziemy przez każdy krok, od konfiguracji środowiska po wstawienie obrazu kodu kreskowego, abyś mógł od razu rozpocząć używanie kodów kreskowych w swoich projektach Java.

## Szybkie odpowiedzi
- **Co uczy ten samouczek?** Jak tworzyć etykiety QR code w Javie i osadzać je w pliku Word przy użyciu Aspose.Words dla Javy.  
- **Jaki typ kodu kreskowego jest używany w przykładzie?** QR code (możesz zamienić go na dowolny z ponad 20 obsługiwanych typów).  
- **Czy potrzebna jest licencja?** Wymagana jest tymczasowa licencja, aby uzyskać nieograniczony dostęp podczas rozwoju.  
- **Jakiej wersji Javy wymaga?** JDK 8 lub wyższej.  
- **Czy mogę zmienić rozmiar lub kolory kodu kreskowego?** Tak — zmodyfikuj ustawienia `BarcodeParameters` i `BarcodeGenerator`.

## Co to jest create QR code Java?
`create QR code Java` odnosi się do programowego generowania obrazu QR‑code w środowisku Java i wstawiania go do dokumentu lub komponentu UI. Aspose.Words dla Javy wraz z Aspose.BarCode pozwala na tworzenie obrazu w całości w pamięci, unikając plików tymczasowych.

## Dlaczego generować niestandardowe etykiety kodów kreskowych przy użyciu Aspose.Words?
Aspose.Words obsługuje **ponad 35 formatów wejściowych i wyjściowych** i może przetworzyć **dokumenty o 500 stronach w mniej niż 3 sekundy** na standardowym sprzęcie serwerowym. Korzystając z generowania kodów kreskowych w pamięci, uzyskasz pełną kontrolę nad typem, rozmiarem i kolorami, jednocześnie zachowując przepływ pracy w pełni skoncentrowany na Javie i niezależny od platformy.

## Prerequisites
- Java Development Kit (JDK): wersja 8 lub wyższa.  
- Aspose.Words for Java Library: [Download here](https://releases.aspose.com/words/java/).  
- Aspose.BarCode for Java Library: [Download here](https://releases.aspose.com/).  
- Zintegrowane środowisko programistyczne (IDE): IntelliJ IDEA, Eclipse lub dowolne inne IDE, które preferujesz.  
- Tymczasowa licencja: uzyskaj [temporary license](https://purchase.aspose.com/temporary-license/) dla nieograniczonego dostępu.

## Importowanie pakietów

Użyjemy bibliotek Aspose.Words i Aspose.BarCode. Zaimportuj następujące pakiety do swojego projektu:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Te importy dają nam dostęp do API generowania kodów kreskowych oraz klas dokumentu Word, które będą potrzebne.

## Krok 1: utwórz klasę pomocniczą do operacji na kodach kreskowych

Klasa pomocnicza zawiera wielokrotnego użytku metody, takie jak **konwersja twipsów na piksele** oraz **konwersja koloru szesnastkowego**.  
Klasa `CustomBarcodeGeneratorUtils` udostępnia statyczne metody do konwersji jednostek i obsługi kolorów.

### Kod

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
- `twipsToPixels` – Word mierzy wymiary w **twipsach**; ta metoda konwertuje je na piksele ekranu, co jest przydatne, gdy trzeba precyzyjnie określić rozmiar obrazu kodu kreskowego.  
- `convertColor` – zamienia ciąg szesnastkowy (np. "FF0000" dla czerwonego) na obiekt `java.awt.Color`, umożliwiając **dodanie kodu kreskowego do dokumentu Word** z niestandardowymi kolorami pierwszego planu i tła.

## Krok 2: zaimplementuj własny generator kodów kreskowych

Teraz zaimplementujemy interfejs `IBarcodeGenerator`. Ta klasa jest odpowiedzialna za **generowanie obrazów QR code w Javie**, które Aspose.Words może osadzić.  
Interfejs `IBarcodeGenerator` definiuje jedną metodę zwracającą `BufferedImage` reprezentujący kod kreskowy.

### Kod

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
- `getBarcodeImage` tworzy instancję `BarcodeGenerator`, stosuje kolory podane w `BarcodeParameters` i ostatecznie zwraca `BufferedImage`.  
- Metoda także elegancko obsługuje błędy, zwracając obraz zastępczy, co zapewnia, że tworzenie dokumentu Word nigdy nie spowoduje awarii.

## Jak osadzić kod kreskowy w Wordzie przy użyciu Aspose.Words?

Wczytaj plik Word za pomocą `new Document("template.docx")` (lub utwórz nowy `Document`) i wywołaj `builder.insertImage` z obrazem kodu kreskowego zwróconym przez generator. Ten dwustopniowy wzorzec osadza kod kreskowy bezpośrednio, bez zapisywania pośredniego pliku na dysku. Określając wymiary obrazu w pikselach lub konwertując twipsy Worda na piksele, możesz kontrolować dokładny rozmiar i położenie kodu kreskowego w dokumencie, zapewniając profesjonalny układ, który drukuje się poprawnie na każdej drukarce.

## Krok 3: wygeneruj kod kreskowy i osadź go w Wordzie

Gdy generator jest gotowy, możemy teraz wygenerować obraz kodu kreskowego i **wstawić go do dokumentu Word**.

### Kod

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

1. **Inicjalizacja dokumentu** – Tworzy nowy `Document` (lub możesz wczytać istniejący szablon).  
2. **Parametry kodu kreskowego** – Definiuje typ kodu (`QR`), wartość do zakodowania oraz kolory pierwszego planu i tła.  
3. **Wstawianie obrazu** – `builder.insertImage` umieszcza wygenerowany kod kreskowy w żądanym rozmiarze (200 × 200 pikseli). To jest sedno **jak osadzić kod kreskowy w Wordzie**.  
4. **Zapisywanie** – Końcowy dokument, `CustomBarcodeLabels.docx`, zawiera osadzony kod kreskowy gotowy do druku lub dystrybucji.

## Typowe problemy i rozwiązywanie

| Objaw | Prawdopodobna przyczyna | Rozwiązanie |
|---------|--------------|-----|
| Kod kreskowy jest pusty | Kolory w `BarcodeParameters` są takie same (np. czarny na czarnym) | Sprawdź wartości `foregroundColor` i `backgroundColor`. |
| Obraz jest zniekształcony | Nieprawidłowe wymiary w pikselach przekazane do `insertImage` | Dostosuj argumenty szerokości/wysokości lub użyj konwersji `twipsToPixels` dla precyzyjnego rozmiaru. |
| Błąd nieobsługiwanego typu kodu kreskowego | Użycie typu nie rozpoznawanego przez `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` | Upewnij się, że ciąg typu kodu kreskowego odpowiada jednemu z obsługiwanych `EncodeTypes` (np. "QR", "CODE128"). |

## Najczęściej zadawane pytania

**Q: Czy mogę używać Aspose.Words dla Javy bez licencji?**  
**A:** Tak, ale będą obowiązywać ograniczenia wersji ewaluacyjnej. Uzyskaj [temporary license](https://purchase.aspose.com/temporary-license/) dla pełnej funkcjonalności.

**Q: Jakie typy kodów kreskowych mogę generować?**  
**A:** Aspose.BarCode obsługuje QR, Code 128, EAN‑13, DataMatrix, PDF417 i wiele innych formatów — ponad 20 symbologii w sumie. Zobacz [documentation](https://reference.aspose.com/words/java/) po pełną listę.

**Q: Jak mogę zmienić rozmiar kodu kreskowego?**  
**A:** Dostosuj argumenty szerokości i wysokości w `builder.insertImage` lub oblicz dokładne twipsy Worda używając `twipsToPixels` dla precyzyjnej kontroli w pikselach.

**Q: Czy można używać własnych czcionek dla tekstu kodu kreskowego?**  
**A:** Tak, możesz dostosować czcionkę tekstu poprzez właściwość `CodeTextParameters` klasy `BarcodeGenerator`.

**Q: Gdzie mogę uzyskać pomoc, jeśli napotkam problemy?**  
**A:** Odwiedź [support forum](https://forum.aspose.com/c/words/8/) aby uzyskać pomoc od społeczności Aspose i inżynierów.

## Podsumowanie

Postępując zgodnie z powyższymi krokami, teraz wiesz, jak **tworzyć obrazy QR code w Javie** i **osadzać kod kreskowy w dokumentach Word** przy użyciu Aspose.Words dla Javy. Ta technika jest na tyle elastyczna, że sprawdzi się w etykietach inwentaryzacyjnych, biletach na wydarzenia czy w każdej sytuacji, w której kod kreskowy musi być częścią generowanego dokumentu. Eksperymentuj z różnymi typami kodów, kolorami i opcjami rozmiaru, aby dopasować je do konkretnych potrzeb biznesowych.

**Ostatnia aktualizacja:** 2026-10-23  
**Testowano z:** Aspose.Words for Java 24.12, Aspose.BarCode for Java 24.12  
**Autor:** Aspose

## Powiązane samouczki

- [Utwórz PDF z Worda z generowaniem kodów kreskowych – Aspose.Words dla Javy](/words/java/document-conversion-and-export/using-barcode-generation/)
- [Zapisz Word jako PDF z przewodnikiem Aspose Words krok po kroku – Java](/words/java/document-conversion-and-export/save-word-as-pdf-with-aspose-words-step-by-step-java-guide/)
- [Utwórz pusty dokument Word w Javie z Aspose Words](/words/java/document-manipulation/create-blank-word-document-in-java-with-aspose-words/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}