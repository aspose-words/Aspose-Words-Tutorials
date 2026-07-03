---
category: general
date: 2026-07-03
description: Eksportuj pływające kształty w linii podczas konwertowania Worda na PDF
  w linii. Dowiedz się, jak ustawić opcje PDF i zapisać Worda jako PDF w Javie.
draft: false
keywords:
- export floating shapes inline
- convert word to pdf inline
- how to set pdf options
- save word as pdf options
language: pl
og_description: Eksportuj pływające kształty w linii podczas konwertowania dokumentu
  Word na PDF. Ten samouczek pokazuje, jak ustawić opcje PDF i zapisać Word jako PDF.
og_title: Eksportowanie pływających kształtów w linii – Przewodnik konwersji PDF w
  Javie
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  headline: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  type: TechArticle
- description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  name: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  steps:
  - name: 1. “What if my document contains complex SmartArt?”
    text: SmartArt is treated as a drawing object. The inline flag works for most
      vector shapes, but very intricate SmartArt may still be rendered as an image.
      In those cases, consider flattening the SmartArt in Word before conversion,
      or use `pdfOptions.setExportSmartArtAsImage(true)` to force image export.
  - name: 2. “Can I combine inline and block exports in the same document?”
    text: Unfortunately the API applies the setting globally. If you need mixed behavior,
      split the document into sections, export each section separately with different
      options, then merge the PDFs using `PdfMerger`.
  - name: 3. “Does this affect font embedding?”
    text: No. Font embedding is controlled by `pdfOptions.setEmbedFullFonts(true)`
      (default). You can safely enable or disable it without touching the inline shape
      flag.
  - name: 4. “How do I verify that shapes are really `<span>`?”
    text: Open the resulting PDF in a tool like **PDF.js** or **Adobe Acrobat** →
      **Edit PDF** → **Object Inspector**. You’ll see the shape wrapped in a `<span>`
      element in the underlying XML. If you see `<div>`, the option wasn’t applied.
  type: HowTo
tags:
- Java
- PDF
- Aspose.Words
title: Eksportowanie pływających kształtów w linii – Kompletny przewodnik konwersji
  PDF
url: /pl/java/document-conversion-and-export/export-floating-shapes-inline-complete-guide-to-pdf-conversi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Eksportowanie pływających kształtów inline – Kompletny przewodnik po konwersji do PDF

Czy kiedykolwiek musiałeś **eksportować pływające kształty inline** podczas konwersji dokumentu Word do PDF? Nie jesteś sam — wielu programistów napotyka ten problem, gdy ich diagramy lub ikony nagle przenoszą się na osobne warstwy. Dobrą wiadomością jest to, że pojedyncza opcja PDF może utrzymać te kształty wewnątrz znaczników `<span>`, zachowując układ dokładnie taki, jak w Wordzie.

W tym samouczku przejdziemy przez **ustawianie opcji PDF** w Javie, pokażemy dokładny kod do **zapisu Word jako PDF z opcjami**, oraz wyjaśnimy, dlaczego warto **konwertować Word do PDF inline** zamiast domyślnego eksportu na poziomie bloku. Po zakończeniu będziesz mieć gotowy fragment kodu, który możesz wkleić do dowolnego projektu Maven lub Gradle.

## Czego się nauczysz

- Różnicę między eksportem inline `<span>` a blokowym `<div>` dla pływających kształtów.  
- Jak skonfigurować `PdfSaveOptions`, aby wymusić renderowanie inline.  
- Krok‑po‑kroku kod, który ładuje plik `.docx`, stosuje opcję i zapisuje PDF.  
- Typowe pułapki (brak czcionek, nieobsługiwane kształty) oraz jak ich unikać.  
- Wskazówki dotyczące testowania wyniku i rozszerzania podejścia na inne elementy dokumentu.

**Wymagania wstępne** – potrzebujesz Java 8 lub nowszej, biblioteki Aspose.Words for Java (lub dowolnego API, które udostępnia klasę `PdfSaveOptions`), oraz przykładowego pliku Word z pływającymi kształtami (w samouczku używany jest `FloatingShapes.docx`). Nie są potrzebne żadne dodatkowe narzędzia.

---

## Krok 1: Załaduj źródłowy dokument Word

Pierwszą rzeczą, którą robisz, jest otwarcie pliku `.docx`, który chcesz przekształcić. To proste, ale upewnij się, że ścieżka jest absolutna lub poprawnie rozwiązywana z classpathu.

```java
import com.aspose.words.Document;

// Step 1: Load the source Word document
Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");
```

*Dlaczego to ważne:*  
Jeśli dokument nie zostanie poprawnie załadowany, kolejna konwersja do PDF zgłosi `FileNotFoundException`. Użycie klasy `Document` zapewnia pełne wypełnienie wewnętrznego modelu obiektowego, w tym wszystkich pływających kształtów znajdujących się na stronie.

---

## Krok 2: Utwórz opcje zapisu PDF i ustaw pływające kształty jako inline

Tutaj dzieje się magia. Domyślnie Aspose.Words eksportuje pływające kształty jako elementy blokowe `<div>`, co może zepsuć przepływ w PDF‑ach opartych na HTML. Wywołanie `setExportFloatingShapesAsInlineTag(true)` mówi silnikowi, aby owinął każdy kształt w znacznik inline `<span>`.

```java
import com.aspose.words.PdfSaveOptions;

// Step 2: Create PDF save options and set floating shapes to be exported as inline <span> elements
PdfSaveOptions pdfOptions = new PdfSaveOptions();
pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → <span>, false → <div>
```

*Dlaczego to ważne:*  
- **Wierność układu** – Znaczniki inline utrzymują kształt wyrównany z otaczającym tekstem, unikając niechcianych przerw.  
- **Wyszukiwalność** – Elementy inline są częściej prawidłowo indeksowane przez czytniki PDF.  
- **Kontrola stylów** – Możesz docelowo stylować `<span>` przy pomocy CSS, jeśli później konwertujesz PDF z powrotem do HTML.

> **Pro tip:** Jeśli kiedykolwiek potrzebujesz starego zachowania blokowego dla konkretnego dokumentu, po prostu przekaż `false` lub pomiń wywołanie w ogóle.

---

## Krok 3: Zapisz dokument jako PDF przy użyciu skonfigurowanych opcji

Teraz łączysz załadowany `Document` z `PdfSaveOptions` i zapisujesz plik. Ten pojedynczy wiersz wykonuje całą ciężką pracę.

```java
// Step 3: Save the document as a PDF using the configured options
doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);
```

*Dlaczego to ważne:*  
Metoda `save` respektuje każdy flag ustawiony w `pdfOptions`. Pominięcie przekazania opcji spowoduje powrót do domyślnego eksportu blokowego, co niweczy cel **eksportowania pływających kształtów inline**.

---

## Pełny działający przykład

Łącząc wszystko razem, oto kompaktowy program, który możesz skompilować i uruchomić od razu. Zamień `YOUR_DIRECTORY` na rzeczywistą ścieżkę na swoim komputerze.

```java
import com.aspose.words.*;

public class ExportFloatingShapesInlineDemo {
    public static void main(String[] args) {
        try {
            // Load the source Word document
            Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");

            // Configure PDF options to export floating shapes as inline <span>
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true);

            // Save as PDF with the above options
            doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);

            System.out.println("PDF created successfully with inline floating shapes.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Oczekiwany wynik** – Po uruchomieniu programu otwórz `FloatingShapes.pdf`. Powinieneś zobaczyć kształty przylegające do tekstu, bez dodatkowej białej przestrzeni, a reprezentacja HTML (jeśli przeanalizujesz wewnętrzną strukturę PDF) będzie zawierała znaczniki `<span>` wokół każdego kształtu.

![Export floating shapes inline example](https://example.com/export-inline.png "Screenshot showing floating shapes rendered inline in the PDF")

*Tekst alternatywny obrazu:* **eksportowanie pływających kształtów inline** zrzut ekranu PDF z kształtami inline.

---

## Często zadawane pytania i przypadki brzegowe

### 1. „Co jeśli mój dokument zawiera złożony SmartArt?”

SmartArt jest traktowany jako obiekt rysunkowy. Flaga inline działa dla większości wektorowych kształtów, ale bardzo skomplikowany SmartArt może nadal być renderowany jako obraz. W takich przypadkach rozważ spłaszczenie SmartArt w Wordzie przed konwersją lub użyj `pdfOptions.setExportSmartArtAsImage(true)`, aby wymusić eksport jako obraz.

### 2. „Czy mogę łączyć eksport inline i blokowy w tym samym dokumencie?”

Niestety ustawienie API jest stosowane globalnie. Jeśli potrzebujesz mieszanej zachowania, podziel dokument na sekcje, wyeksportuj każdą sekcję osobno z różnymi opcjami, a następnie połącz PDF‑y przy pomocy `PdfMerger`.

### 3. „Czy to wpływa na osadzanie czcionek?”

Nie. Osadzanie czcionek jest kontrolowane przez `pdfOptions.setEmbedFullFonts(true)` (wartość domyślna). Możesz bezpiecznie włączać lub wyłączać tę opcję, nie dotykając flagi inline dla kształtów.

### 4. „Jak zweryfikować, że kształty naprawdę są `<span>`?”

Otwórz wygenerowany PDF w narzędziu takim jak **PDF.js** lub **Adobe Acrobat** → **Edit PDF** → **Object Inspector**. Zobaczysz kształt otoczony elementem `<span>` w leżącym pod spodem XML. Jeśli zobaczysz `<div>`, opcja nie została zastosowana.

---

## Rozszerzanie podejścia – powiązane opcje

Skoro już tu jesteś, możesz również przyjrzeć się innym „gałkom” konwersji PDF:

| Opcja | Co robi | Typowe zastosowanie |
|--------|--------------|------------------|
| `setCompressImages(true)` | Zmniejsza rozmiar obrazów | Szybsze pobieranie |
| `setUseHighQualityRendering(true)` | Poprawia renderowanie wektorów | PDF‑y gotowe do druku |
| `setExportDocumentStructure(true)` | Dodaje znaczniki strukturalne dla dostępności | Zgodność z WCAG |
| `setSaveFormat(SaveFormat.PDF)` | Jawnie ustawia format (rzadko potrzebne) | Potoki wieloformatowe |

Te ustawienia doskonale współgrają ze scenariuszami **konwersji Word do PDF inline**, gdzie potrzebujesz zarówno wierności układu, jak i wydajności.

---

## Testowanie konwersji

1. **Sprawdzenie wizualne** – Otwórz PDF w dwóch przeglądarkach (Chrome i Adobe Reader), aby upewnić się, że kształty są wyrównane.  
2. **Automatyczny diff** – Użyj biblioteki takiej jak `pdfbox`, aby wyodrębnić XML i asertywnie sprawdzić obecność znaczników `<span>`.  
3. **Benchmark wydajności** – Zmierz czas wykonania z i bez `setCompressImages`, aby zobaczyć kompromis.

Przykład szybkiego testu JUnit:

```java
@Test
public void testInlineExport() throws Exception {
    Document doc = new Document("src/test/resources/FloatingShapes.docx");
    PdfSaveOptions opts = new PdfSaveOptions();
    opts.setExportFloatingShapesAsInlineTag(true);
    ByteArrayOutputStream out = new ByteArrayOutputStream();
    doc.save(out, opts);
    String pdfXml = new String(out.toByteArray(), StandardCharsets.UTF_8);
    assertTrue(pdfXml.contains("<span"));
}
```

---

## Podsumowanie

Masz teraz solidne, kompleksowe rozwiązanie dla **eksportowania pływających kształtów inline** podczas **konwersji Word do PDF inline**. Konfigurując `PdfSaveOptions`, kontrolujesz znacznik HTML używany dla każdego kształtu, utrzymując PDF‑y schludne i przeszukiwalne. Pamiętaj, aby testować wynik, dostosowywać powiązane opcje, takie jak kompresja obrazów, oraz obsługiwać przypadki brzegowe, np. złożony SmartArt.

Gotowy na kolejny krok? Spróbuj zastosować tę samą technikę do **eksportowania pływających tabel inline** lub eksperymentuj z PDF‑ami stylowanymi CSS przy pomocy `HtmlSaveOptions` Aspose. Ten sam wzorzec — load, configure, save — sprawdza się w prawie każdym scenariuszu dokument‑do‑PDF.

Masz więcej pytań o **jak ustawić opcje PDF** lub potrzebujesz pomocy przy **zapisie Word jako PDF z opcjami** w innej bibliotece? zostaw komentarz i powodzenia w kodowaniu!

## Co warto się nauczyć dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne, działające przykłady kodu oraz szczegółowe wyjaśnienia, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Convert Word to PDF with Aspose.Words for Java](/words/english/java/document-converting/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Export Word Document Structure to PDF Document](/words/english/net/programming-with-pdfsaveoptions/export-document-structure/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}