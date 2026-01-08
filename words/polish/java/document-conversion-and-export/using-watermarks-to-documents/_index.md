---
date: 2025-12-18
description: Dowiedz się, jak dodać znak wodny do dokumentów przy użyciu Aspose.Words
  for Java, w tym przykład znaku wodnego z obrazem, zmiana koloru znaku wodnego, ustawienie
  przezroczystości znaku wodnego oraz usunięcie znaku wodnego z dokumentu.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Jak dodać znak wodny do dokumentów przy użyciu Aspose.Words dla Javy
url: /pl/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak dodać znak wodny do dokumentów przy użyciu Aspose.Words dla Javy

## Wprowadzenie do dodawania znaków wodnych do dokumentów w Aspose.Words dla Javy

W tym samouczku dowiesz się **jak dodać znak wodny** do dokumentów Word przy użyciu Aspose.Words dla Javy. Znaki wodne to szybki sposób oznaczenia pliku jako poufny, szkic lub zatwierdzony; mogą być oparte na tekście lub obrazie. Przeprowadzimy Cię przez konfigurację biblioteki, tworzenie znaków wodnych tekstowych i graficznych, dostosowywanie ich wyglądu (w tym zmianę koloru i ustawienie przezroczystości), a także usuwanie znaku wodnego, gdy nie jest już potrzebny.

## Szybkie odpowiedzi
- **Czym jest znak wodny?** Półprzezroczysta nakładka (tekstowa lub graficzna), która pojawia się za główną treścią dokumentu.  
- **Czy mogę dodać wiele znaków wodnych?** Tak – utwórz kilka obiektów `Shape` i dodaj każdy do wybranych sekcji.  
- **Jak zmienić kolor znaku wodnego?** Dostosuj właściwość `Color` w `TextWatermarkOptions`.  
- **Czy istnieje przykład znaku wodnego graficznego?** Zobacz sekcję „Dodawanie znaków wodnych graficznych” poniżej.  
- **Czy potrzebna jest licencja, aby usunąć znak wodny?** Do użytku produkcyjnego wymagana jest ważna licencja Aspose.Words.

## Konfiguracja Aspose.Words dla Javy

Zanim zaczniemy dodawać znaki wodne do dokumentów, musimy skonfigurować Aspose.Words dla Javy. Wykonaj poniższe kroki, aby rozpocząć:

1. Pobierz Aspose.Words dla Javy z [tutaj](https://releases.aspose.com/words/java/).  
2. Dodaj bibliotekę Aspose.Words dla Javy do swojego projektu Java.  
3. Zaimportuj niezbędne klasy w swoim kodzie Java.

Teraz, gdy biblioteka jest już skonfigurowana, przejdźmy do rzeczywistego tworzenia znaków wodnych.

## Dodawanie znaków wodnych tekstowych

Znaki wodne tekstowe są popularnym wyborem, gdy chcesz dodać informację tekstową do dokumentu. Oto jak dodać znak wodny tekstowy przy użyciu Aspose.Words dla Javy:

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

**Dlaczego to ważne:** Modyfikując `setFontFamily`, `setFontSize` i `setColor`, możesz **zmienić kolor znaku wodnego**, aby pasował do Twojej identyfikacji wizualnej, a `setSemitransparent(true)` pozwala **ustawić przezroczystość znaku wodnego** dla subtelnego efektu.

## Dodawanie znaków wodnych graficznych

Oprócz znaków wodnych tekstowych możesz także dodawać znaki wodne graficzne do dokumentów. Poniżej znajduje się **przykład znaku wodnego graficznego**, który pokazuje, jak osadzić logo lub stempel w formacie PNG:

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

Możesz powtórzyć ten blok z różnymi obrazami lub pozycjami, aby **dodać wiele znaków wodnych** do jednego pliku.

## Dostosowywanie znaków wodnych

Znaki wodne można dostosować, zmieniając ich wygląd i położenie. Dla znaków wodnych tekstowych możesz zmienić czcionkę, rozmiar, kolor i układ. Dla znaków wodnych graficznych możesz modyfikować rozmiar, obrót i wyrównanie, jak pokazano w poprzednich przykładach.

## Usuwanie znaków wodnych

Jeśli potrzebujesz **usunąć znak wodny** z dokumentu, poniższy kod przegląda wszystkie kształty i usuwa te zidentyfikowane jako znaki wodne:

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

## Typowe scenariusze użycia i wskazówki

- **Poufne szkice:** Dodaj półprzezroczysty znak wodny tekstowy, np. „CONFIDENTIAL”.  
- **Branding:** Użyj znaku wodnego graficznego zawierającego logo Twojej firmy.  
- **Znaki wodne specyficzne dla sekcji:** Przejdź przez `doc.getSections()` i dodaj znak wodny tylko do wybranych sekcji.  
- **Wskazówka wydajnościowa:** Ponownie używaj tej samej instancji `TextWatermarkOptions`, gdy stosujesz ten sam znak wodny w wielu dokumentach.

## Najczęściej zadawane pytania

### Jak mogę zmienić czcionkę znaku wodnego tekstowego?

Aby zmienić czcionkę znaku wodnego tekstowego, zmodyfikuj właściwość `setFontFamily` w `TextWatermarkOptions`. Przykład:

```java
options.setFontFamily("Times New Roman");
```

### Czy mogę dodać wiele znaków wodnych do jednego dokumentu?

Tak, możesz dodać wiele znaków wodnych, tworząc kilka obiektów `Shape` z różnymi ustawieniami i dodając je do dokumentu.

### Czy można obrócić znak wodny?

Tak, możesz obrócić znak wodny, ustawiając właściwość `setRotation` w obiekcie `Shape`. Wartości dodatnie obracają znak wodny zgodnie z ruchem wskazówek zegara, a wartości ujemne – przeciwnie.

### Jak mogę uczynić znak wodny półprzezroczystym?

Aby znak wodny był półprzezroczysty, ustaw właściwość `setSemitransparent` na `true` w `TextWatermarkOptions`.

### Czy mogę dodać znaki wodne do konkretnych sekcji dokumentu?

Tak, możesz dodać znaki wodne do wybranych sekcji, iterując po sekcjach i dodając znak wodny do tych, które chcesz.

---

**Ostatnia aktualizacja:** 2025-12-18  
**Testowano z:** Aspose.Words dla Javy 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}