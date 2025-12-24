---
date: 2025-12-10
description: Dowiedz się, jak generować własne etykiety z kodami kreskowymi przy użyciu
  Aspose.Words for Java. Ten przewodnik krok po kroku pokazuje, jak osadzać kody kreskowe
  w dokumentach Word.
linktitle: Generating Custom Barcode Labels
second_title: Aspose.Words Java Document Processing API
title: Generuj niestandardowe etykiety kodów kreskowych w Aspose.Words dla Javy
url: /pl/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Generowanie niestandardowych etykiet kodów kreskowych w Aspose.Words dla Javy

## Wprowadzenie do generowania niestandardowego kodu kreskowego w Aspose.Words dla Javy

Kody kreskowe są niezbędne w nowoczesnych aplikacjach — niezależnie od tego, czy zarządzasz zapasami, drukujesz bilety, czy tworzysz karty identyfikacyjne. W tym samouczku **wygenerujesz niestandardowe etykiety kodów kreskowych** i osadzisz je bezpośrednio w dokumencie Word przy użyciu interfejsu `IBarcodeGenerator`. Przejdziemy krok po kroku, od konfiguracji środowiska po wstawienie obrazu kodu kreskowego, abyś mógł od razu rozpocząć używanie kodów kreskowych w swoich projektach Java.

## Szybkie odpowiedzi
- **Co uczy ten samouczek?** Jak generować niestandardowe etykiety kodów kreskowych i osadzać je w pliku Word przy użyciu Aspose.Words dla Javy.  
- **Jaki typ kodu kreskowego jest używany w przykładzie?** Kod QR (można go zamienić na dowolny obsługiwany typ).  
- **Czy potrzebna jest licencja?** Wymagana jest tymczasowa licencja, aby uzyskać nieograniczony dostęp podczas rozwoju.  
- **Jakiej wersji Javy wymaga?** JDK 8 lub wyższej.  
- **Czy mogę zmienić rozmiar lub kolory kodu kreskowego?** Tak — zmodyfikuj ustawienia `BarcodeParameters` i `BarcodeGenerator`.

## Wymagania wstępne

Zanim zaczniemy kodować, upewnij się, że masz następujące elementy:

- Java Development Kit (JDK): wersja 8 lub wyższa.  
- Biblioteka Aspose.Words dla Javy: [Pobierz tutaj](https://releases.aspose.com/words/java/).  
- Biblioteka Aspose.BarCode dla Javy: [Pobierz tutaj](https://releases.aspose.com/).  
- Zintegrowane środowisko programistyczne (IDE): IntelliJ IDEA, Eclipse lub dowolne inne IDE, które preferujesz.  
- Tymczasowa licencja: Uzyskaj [tymczasową licencję](https://purchase.aspose.com/temporary-license/) dla nieograniczonego dostępu.

## Importowanie pakietów

Użyjemy bibliotek Aspose.Words i Aspose.BarCode. Zaimportuj następujące pakiety do swojego projektu:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Te importy dają dostęp do API generowania kodów kreskowych oraz klas dokumentu Word, których będziemy potrzebować.

## Krok 1: Utwórz klasę pomocniczą do operacji na kodach kreskowych

Aby utrzymać główny kod w czystości, umieścimy wspólne pomocniki — takie jak **konwersja twipsów na piksele** oraz **konwersja koloru szesnastkowego** — w klasie narzędziowej.

### Code

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

**Explanation**

- `twipsToPixels` – Word mierzy wymiary w **twips**; ta metoda konwertuje je na piksele ekranu, co jest przydatne, gdy trzeba precyzyjnie określić rozmiar obrazu kodu kreskowego.  
- `convertColor` – Zamienia ciąg szesnastkowy (np. `"FF0000"` dla czerwonego) na obiekt `java.awt.Color`, pozwalając na **jak wstawić kod kreskowy** z własnymi kolorami pierwszego planu i tła.

## Krok 2: Zaimplementuj własny generator kodów kreskowych

Teraz zaimplementujemy interfejs `IBarcodeGenerator`. Ta klasa będzie odpowiedzialna za **generowanie obrazów w stylu qr code java**, które Aspose.Words może osadzić.

### Code

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

**Explanation**

- `getBarcodeImage` tworzy instancję `BarcodeGenerator`, stosuje kolory podane w `BarcodeParameters` i ostatecznie zwraca `BufferedImage`.  
- Metoda obsługuje również błędy, zwracając obraz zastępczy, co zapewnia, że tworzenie dokumentu Word nigdy nie zakończy się awarią.

## Krok 3: Wygeneruj kod kreskowy i **osadź kod kreskowy w Wordzie**

Z gotowym generatorem możemy teraz wyprodukować obraz kodu kreskowego i **wstawić go do dokumentu Word**.

### Code

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

**Explanation**

1. **Inicjalizacja dokumentu** – Tworzy nowy `Document` (lub możesz wczytać istniejący szablon).  
2. **Parametry kodu kreskowego** – Definiuje typ kodu (`QR`), wartość do zakodowania oraz kolory pierwszego planu i tła.  
3. **Wstawianie obrazu** – `builder.insertImage` umieszcza wygenerowany kod kreskowy w żądanym rozmiarze (200 × 200 pikseli). To jest sedno **jak wstawić kod kreskowy** do pliku Word.  
4. **Zapisywanie** – Końcowy dokument, `CustomBarcodeLabels.docx`, zawiera osadzony kod kreskowy gotowy do druku lub dystrybucji.

## Dlaczego generować niestandardowe etykiety kodów kreskowych przy użyciu Aspose.Words?

- **Pełna kontrola** nad wyglądem kodu kreskowego (typ, rozmiar, kolory).  
- **Bezproblemowa integracja** — nie potrzeba plików pośrednich; kod kreskowy jest generowany w pamięci i wstawiany bezpośrednio.  
- **Cross‑platform** — działa na każdym systemie operacyjnym obsługującym Javę, co czyni go idealnym do generowania dokumentów po stronie serwera.  
- **Skalowalny** — możesz iterować po źródle danych, aby w jednym przebiegu stworzyć setki spersonalizowanych etykiet.

## Typowe problemy i rozwiązywanie

| Symptom | Likely Cause | Fix |
|---------|--------------|-----|
| Kod kreskowy jest pusty | Kolory w `BarcodeParameters` są takie same (np. czarny na czarnym) | Sprawdź wartości `foregroundColor` i `backgroundColor`. |
| Obraz jest zniekształcony | Nieprawidłowe wymiary w pikselach przekazane do `insertImage` | Dostosuj argumenty szerokości/wysokości lub użyj konwersji `twipsToPixels` dla precyzyjnego rozmiaru. |
| Błąd nieobsługiwanego typu kodu kreskowego | Użycie typu nie rozpoznawanego przez `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` | Upewnij się, że ciąg typu kodu kreskowego odpowiada jednemu z obsługiwanych `EncodeTypes` (np. `"QR"`, `"CODE128"`). |

## Najczęściej zadawane pytania

**P:** Czy mogę używać Aspose.Words dla Javy bez licencji?  
**O:** Tak, ale będą pewne ograniczenia. Uzyskaj [tymczasową licencję](https://purchase.aspose.com/temporary-license/) dla pełnej funkcjonalności.

**P:** Jakie typy kodów kreskowych mogę generować?  
**O:** Aspose.BarCode obsługuje QR, Code 128, EAN‑13 i wiele innych formatów. Sprawdź [dokumentację](https://reference.aspose.com/words/java/) po pełną listę.

**P:** Jak mogę zmienić rozmiaru kreskowego?  
**O:** Dostosuj argumenty szerokości i wysokości w `builder.insertImage` lub użyj `twipsToPixels`, aby przeliczyć jednostki pomiarowe Worda na piksele.

**P:** Czy można używać własnych czcionek dla tekstu kodu kreskowego?  
**O:** Tak, możesz dostosować czcionkę tekstu poprzez właściwość `CodeTextParameters` obiektu `BarcodeGenerator`.

**P:** Gdzie mogę uzyskać pomoc, jeśli napotkam problemy?  
**O:** Odwiedź [forum wsparcia](https://forum.aspose.com/c/words/8/) po pomoc od społeczności Aspose i inżynierów.

## Podsumowanie

Postępując zgodnie z powyższymi krokami, teraz wiesz, jak **generować niestandardowe obrazy kodów kreskowych** i **osadzać kod kreskowy w dokumentach Word** przy użyciu Aspose.Words dla Javy. Ta technika jest wystarczająco elastyczna, aby tworzyć etykiety magazynowe, bilety na wydarzenia lub dowolny scenariusz, w którym kod kreskowy musi być częścią generowanego dokumentu. Eksperymentuj z różnymi typami kodów i opcjami stylizacji, aby dopasować je do konkretnych potrzeb biznesowych.

---

**Ostatnia aktualizacja:** 2025-12-10  
**Testowano z:** Aspose.Words for Java 24.12, Aspose.BarCode for Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}