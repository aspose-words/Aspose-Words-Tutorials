---
date: 2026-02-19
description: Poznaj sposób tworzenia dokumentu z znakiem wodnym przy użyciu Aspose.Words
  for Java oraz dodawania znaku wodnego w postaci obrazu w Javie, aby uzyskać profesjonalnie
  wyglądające dokumenty.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Utwórz dokument z znakiem wodnym przy użyciu Aspose.Words dla Javy
url: /pl/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz dokument ze znakiem wodnym przy użyciu Aspose.Words dla Javy

W tym samouczku **utworzysz dokument ze znakiem wodnym** przy użyciu API Aspose.Words dla Javy. Znaki wodne — zarówno tekstowe, jak i graficzne — pomagają oznaczyć plik jako poufny, wersję roboczą lub zatwierdzony, i mogą być stosowane programowo w każdym dokumencie Word. Przeprowadzimy Cię przez konfigurację biblioteki, dodawanie zarówno tekstowych, jak i graficznych znaków wodnych, dostosowywanie ich wyglądu oraz ich usuwanie, gdy nie będą już potrzebne.

## Szybkie odpowiedzi
- **Co robi znak wodny?** Nakłada tekst lub obraz na każdą stronę, aby przekazać status lub branding.  
- **Która biblioteka dodaje znaki wodne w Javie?** Aspose.Words for Java zapewnia wbudowaną obsługę znaków wodnych.  
- **Czy mogę dodać znak wodny jako obraz?** Tak — użyj klasy `Shape` i podejścia `add image watermark java`.  
- **Czy znak wodny jest półprzezroczysty?** Możesz kontrolować krycie za pomocą `setSemitransparent` dla znaków wodnych tekstowych.  
- **Czy potrzebna jest licencja?** Darmowa wersja próbna działa do testów; licencja komercyjna jest wymagana w produkcji.

## Co to jest znak wodny i dlaczego go używać?

Znak wodny to delikatna nakładka — tekstowa lub graficzna — dodawana do każdej strony dokumentu. Jest powszechnie używany do wskazywania **poufności**, **statusu wersji roboczej** lub **brandingu** bez zmiany podstawowej treści. Dodawanie znaków wodnych programowo zapewnia spójność w dużych partiach plików i oszczędza czas w porównaniu z ręczną edycją.

## Konfiguracja Aspose.Words dla Javy

1. Pobierz Aspose.Words for Java z [here](https://releases.aspose.com/words/java/).  
2. Dodaj pobrany plik JAR (lub zależność Maven/Gradle) do ścieżki klas swojego projektu.  
3. Importuj wymagane klasy w swoim pliku źródłowym Java:

```java
import com.aspose.words.*;
import java.awt.Color;
import java.nio.file.*;
```

## Jak dodać znak wodny tekstowy

Znaki wodne tekstowe są idealne do oznaczania dokumentu jako „CONFIDENTIAL” lub „DRAFT”. Poniższy fragment pokazuje czysty sposób **utworzenia dokumentu ze znakiem wodnym** przy użyciu `TextWatermarkOptions`.

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Define TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Set the watermark text and options
doc.getWatermark().setText("Test", options);

// Save the document with the watermark
doc.save("DocumentWithWatermark.docx");
```

### Dostosowywanie znaku wodnego tekstowego
- **Rodzina i rozmiar czcionki** – zmień `setFontFamily` i `setFontSize`.  
- **Kolor** – użyj dowolnego `java.awt.Color`.  
- **Układ** – wybierz `HORIZONTAL`, `DIAGONAL`, itp.  
- **Przezroczystość** – włącz `setSemitransparent(true)`, aby uzyskać jaśniejszy wygląd.

## Jak dodać znak wodny graficzny (add image watermark java)

Znaki wodne graficzne są doskonałe dla logo lub własnych grafik. Poniżej znajduje się przykład **add image watermark java**, który wstawia plik PNG w centrum każdej strony.

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Load the image for the watermark
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Set the watermark size and position
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Add the watermark to the document
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Save the document with the watermark
doc.save("DocumentWithImageWatermark.docx");
```

### Wskazówki dotyczące znaków wodnych graficznych
- **Zmiana rozmiaru** — użyj `setWidth` / `setHeight`, aby dopasować do strony.  
- **Pozycja** — może być wyśrodkowana lub wyrównana do dowolnego marginesu przy użyciu `RelativeHorizontalPosition` / `RelativeVerticalPosition`.  
- **Przezroczystość** — można zastosować, regulując kanał alfa obrazu przed jego załadowaniem.

## Jak usunąć znaki wodne

Gdy dokument nie potrzebuje już znaku wodnego, możesz go usunąć programowo. Poniższy kod iteruje po wszystkich kształtach i usuwa te, które w nazwie zawierają „Watermark”.

```java
// Create a Document instance
Document doc = new Document("DocumentWithWatermark.docx");

// Remove the watermark
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Save the document without the watermark
doc.save("DocumentWithoutWatermark.docx");
```

## Typowe pułapki i rozwiązywanie problemów

- **Brak znaku wodnego po zapisaniu** – upewnij się, że wywołujesz `doc.save()` po ustawieniu znaku wodnego.  
- **Obraz się nie wyświetla** – sprawdź, czy ścieżka do obrazu jest prawidłowa i czy plik jest w obsługiwanym formacie (PNG, JPEG, BMP).  
- **Przezroczystość nie została zastosowana** – `setSemitransparent(true)` działa tylko dla znaków wodnych tekstowych; w przypadku obrazów edytuj kanał alfa PNG.  
- **Wiele sekcji** – jeśli dokument ma kilka sekcji, dodaj znak wodny do ciała każdej sekcji lub użyj `doc.getWatermark().setText(...)`, co zastosuje go globalnie.

## Najczęściej zadawane pytania

**P: Jak mogę zmienić czcionkę znaku wodnego tekstowego?**  
M: Zmodyfikuj właściwość `setFontFamily` w `TextWatermarkOptions`, np. `options.setFontFamily("Times New Roman");`.

**P: Czy mogę dodać wiele znaków wodnych do jednego dokumentu?**  
M: Tak. Utwórz wiele obiektów `Shape` (dla obrazów) lub wywołaj `doc.getWatermark().setText(...)` z różnymi opcjami dla każdego znaku wodnego.

**P: Czy można obrócić znak wodny?**  
M: Dla znaków wodnych graficznych ustaw rotację na obiekcie `Shape` za pomocą `watermark.setRotation(angle)`. Dla znaków wodnych tekstowych użyj właściwości `setLayout` (np. `WatermarkLayout.DIAGONAL`).

**P: Jak mogę uczynić znak wodny półprzezroczystym?**  
M: Ustaw `options.setSemitransparent(true)` w `TextWatermarkOptions`. Dla obrazów dostosuj przezroczystość obrazu przed jego załadowaniem.

**P: Czy mogę dodać znaki wodne do konkretnych sekcji dokumentu?**  
M: Tak. Iteruj przez `doc.getSections()` i dodaj znak wodny tylko do wybranych sekcji.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Ostatnia aktualizacja:** 2026-02-19  
**Testowano z:** Aspose.Words for Java 24.12 (latest)  
**Autor:** Aspose