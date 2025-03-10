---
title: Używanie znaków wodnych w dokumentach w Aspose.Words dla Java
linktitle: Używanie znaków wodnych w dokumentach
second_title: Aspose.Words API przetwarzania dokumentów Java
description: Dowiedz się, jak dodawać znaki wodne do dokumentów w Aspose.Words for Java. Dostosuj znaki wodne tekstowe i graficzne, aby uzyskać profesjonalnie wyglądające dokumenty.
weight: 15
url: /pl/java/document-conversion-and-export/using-watermarks-to-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Używanie znaków wodnych w dokumentach w Aspose.Words dla Java


## Wprowadzenie do dodawania znaków wodnych do dokumentów w Aspose.Words dla Java

tym samouczku pokażemy, jak dodawać znaki wodne do dokumentów za pomocą interfejsu API Aspose.Words for Java. Znaki wodne to przydatny sposób na oznaczanie dokumentów tekstem lub grafiką, aby wskazać ich status, poufność lub inne istotne informacje. W tym przewodniku omówimy zarówno znaki wodne tekstowe, jak i graficzne.

## Konfigurowanie Aspose.Words dla Java

Zanim zaczniemy dodawać znaki wodne do dokumentów, musimy skonfigurować Aspose.Words dla Java. Aby rozpocząć, wykonaj następujące kroki:

1.  Pobierz Aspose.Words dla Java z[Tutaj](https://releases.aspose.com/words/java/).
2. Dodaj bibliotekę Aspose.Words for Java do swojego projektu Java.
3. Zaimportuj niezbędne klasy do kodu Java.

Teraz gdy mamy już skonfigurowaną bibliotekę, możemy przystąpić do dodawania znaków wodnych.

## Dodawanie znaków wodnych tekstowych

Znaki wodne tekstowe są powszechnym wyborem, gdy chcesz dodać informacje tekstowe do swoich dokumentów. Oto, jak możesz dodać znak wodny tekstowy za pomocą Aspose.Words dla Java:

```java
// Utwórz instancję dokumentu
Document doc = new Document("Document.docx");

// Zdefiniuj opcje znaku wodnego TextWatermark
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

//Ustaw tekst i opcje znaku wodnego
doc.getWatermark().setText("Test", options);

// Zapisz dokument ze znakiem wodnym
doc.save("DocumentWithWatermark.docx");
```

## Dodawanie znaków wodnych do obrazów

Oprócz znaków wodnych tekstowych możesz również dodawać znaki wodne obrazkowe do swoich dokumentów. Oto jak dodać znak wodny obrazkowy:

```java
// Utwórz instancję dokumentu
Document doc = new Document("Document.docx");

// Załaduj obraz dla znaku wodnego
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Ustaw rozmiar i pozycję znaku wodnego
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Dodaj znak wodny do dokumentu
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Zapisz dokument ze znakiem wodnym
doc.save("DocumentWithImageWatermark.docx");
```

## Dostosowywanie znaków wodnych

Możesz dostosować znaki wodne, dostosowując ich wygląd i położenie. W przypadku znaków wodnych tekstowych możesz zmienić czcionkę, rozmiar, kolor i układ. W przypadku znaków wodnych obrazkowych możesz zmodyfikować ich rozmiar i położenie, jak pokazano w poprzednich przykładach.

## Usuwanie znaków wodnych

Aby usunąć znaki wodne z dokumentu, możesz skorzystać z następującego kodu:

```java
// Utwórz instancję dokumentu
Document doc = new Document("DocumentWithWatermark.docx");

// Usuń znak wodny
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Zapisz dokument bez znaku wodnego
doc.save("DocumentWithoutWatermark.docx");
```


## Wniosek

tym samouczku nauczyliśmy się, jak dodawać znaki wodne do dokumentów za pomocą Aspose.Words for Java. Niezależnie od tego, czy musisz dodać tekstowe, czy graficzne znaki wodne, Aspose.Words zapewnia narzędzia do ich wydajnego dostosowywania i zarządzania nimi. Możesz również usuwać znaki wodne, gdy nie są już potrzebne, zapewniając, że Twoje dokumenty są czyste i profesjonalne.

## Najczęściej zadawane pytania

### Jak mogę zmienić czcionkę tekstu znaku wodnego?

 Aby zmienić czcionkę znaku wodnego, zmodyfikuj`setFontFamily` nieruchomość w`TextWatermarkOptions`. Na przykład:

```java
options.setFontFamily("Times New Roman");
```

### Czy mogę dodać wiele znaków wodnych do jednego dokumentu?

 Tak, możesz dodać wiele znaków wodnych do dokumentu, tworząc wiele`Shape` obiektów o różnych ustawieniach i dodawanie ich do dokumentu.

### Czy można obrócić znak wodny?

 Tak, możesz obrócić znak wodny, ustawiając`setRotation` nieruchomość w`Shape` obiekt. Wartości dodatnie obracają znak wodny zgodnie z ruchem wskazówek zegara, a wartości ujemne obracają go w kierunku przeciwnym do ruchu wskazówek zegara.

### Jak mogę sprawić, aby znak wodny był półprzezroczysty?

 Aby uczynić znak wodny półprzezroczystym, ustaw`setSemitransparent`nieruchomość do`true` w`TextWatermarkOptions`.

### Czy mogę dodać znaki wodne do wybranych sekcji dokumentu?

Tak, możesz dodać znaki wodne do konkretnych sekcji dokumentu, przechodząc przez sekcje i dodając znak wodny do żądanych sekcji.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
