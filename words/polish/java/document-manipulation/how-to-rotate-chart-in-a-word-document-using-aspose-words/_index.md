---
category: general
date: 2026-10-10
description: Dowiedz się, jak obrócić wykres w pliku Word i zmodyfikować wykres w
  Wordzie, aby zmienić rozmiar wykresu pierścieniowego, z pełnym przykładem w Javie.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to rotate chart
- modify chart in word
- change doughnut chart size
- Aspose.Words chart manipulation
- Java chart API
language: pl
lastmod: 2026-10-10
og_description: Jak obrócić wykres w pliku Word i zmodyfikować wykres w Wordzie, aby
  zmienić rozmiar wykresu pierścieniowego przy użyciu Aspose.Words dla Javy.
og_image_alt: Screenshot showing a rotated doughnut chart after applying how to rotate
  chart steps
og_title: Jak obrócić wykres w dokumencie Word – krok po kroku przewodnik Java
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Learn how to rotate chart in a Word file and modify chart in Word to
    change doughnut chart size with a complete Java example.
  headline: How to rotate chart in a Word document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Jak obrócić wykres w dokumencie Word przy użyciu Aspose.Words
url: /pl/java/document-manipulation/how-to-rotate-chart-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak obrócić wykres w dokumencie Word przy użyciu Aspose.Words

Jeśli potrzebujesz **how to rotate chart** w pliku Microsoft Word, ten przewodnik pokaże Ci dokładne kroki. Dowiesz się także, jak **modify chart in Word** aby **change doughnut chart size** bez opuszczania kodu Java.

Automatyzacja Worda często przypomina serię niepowiązanych wywołań API, ale z Aspose.Words możesz traktować wykres jak każdy inny węzeł dokumentu. Po zakończeniu tego samouczka będziesz mieć działający program, który wczytuje istniejący plik `.docx`, obraca wykres typu doughnut o 45°, zmniejsza otwór do 50 % promienia i zapisuje wynik jako nowy plik.

## Wymagania wstępne

* Zainstalowany Java 17 lub nowszy.
* Maven (lub Gradle) do zarządzania zależnościami.
* Dokument Word wejściowy (`input.docx`) zawierający już wykres typu doughnut.
* Ważna licencja Aspose.Words for Java (lub użyj trybu ewaluacji).

## Krok 1: Skonfiguruj projekt Maven

Utwórz nowy projekt Maven lub dodaj następującą zależność do istniejącego pliku `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

Uruchomienie `mvn clean install` pobierze bibliotekę i udostępni klasy w Twojej ścieżce klas.

## Krok 2: Wczytaj dokument Word zawierający wykres

Pierwszą operacją jest otwarcie istniejącego dokumentu. Klasa `Document` reprezentuje cały plik.

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Wczytanie pliku **nie** modyfikuje go; po prostu tworzy reprezentację w pamięci, którą możesz przeglądać i edytować.

## Krok 3: Utwórz DocumentBuilder do nawigacji

`DocumentBuilder` zapewnia API podobne do kursora, umożliwiające przemieszczanie się po drzewie dokumentu. Użyjemy go do znalezienia pierwszego kształtu wykresu.

```java
        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder zaczyna od początku dokumentu, ale w razie potrzeby możesz przenieść go do dowolnego węzła.

## Krok 4: Pobierz pierwszy kształt wykresu

Wykresy są przechowywane jako węzły `Shape`. Filtrując węzły potomne typu `NodeType.SHAPE`, możemy wyodrębnić obiekt wykresu.

```java
        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();
```

Jeśli dokument zawiera wiele wykresów, możesz iterować po `getChildNodes` i sprawdzać każdy `Shape` pod kątem `hasChart()` przed rzutowaniem.

## Krok 5: Obróć wykres (how to rotate chart)

Wykres typu doughnut to w zasadzie wykres kołowy z otworem. Obrócenie go zmienia kąt początkowy pierwszego segmentu.

```java
        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);
```

Metoda `setStartAngle` oczekuje wartości typu double reprezentującej stopnie. Dodatnie wartości obracają zgodnie z ruchem wskazówek zegara, natomiast ujemne – przeciwnie.

## Krok 6: Zmień rozmiar otworu wykresu doughnut (change doughnut chart size)

Rozmiar otworu wyrażany jest jako ułamek promienia wykresu. Wartość `0.5` oznacza, że otwór zajmuje 50 % całkowitego promienia.

```java
        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);
```

**Wskazówka:** Prawidłowy zakres to `0.0` (brak otworu, czyli zwykły wykres kołowy) do `0.9` (bardzo cienki pierścień). Wartości poza tym zakresem spowodują wyrzucenie `IllegalArgumentException`.

## Krok 7: Zapisz zmodyfikowany dokument

Na koniec zapisz zmiany na dysk.

```java
        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");
    }
}
```

Po otwarciu `DoughnutFormatted.docx` w programie Microsoft Word zobaczysz wykres doughnut obrócony o 45° i otwór zmniejszony do połowy pierwotnego rozmiaru.

## Pełny, działający przykład

Łącząc wszystkie elementy, oto kompletny program, który możesz skopiować i wkleić do swojego IDE:

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Ensure the shape actually contains a chart
        if (!chartShape.hasChart()) {
            System.out.println("No chart found in the first shape.");
            return;
        }

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();

        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);

        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);

        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");

        System.out.println("Chart rotated and doughnut size changed successfully.");
    }
}
```

### Oczekiwany wynik

Uruchomienie programu wypisuje:

```
Chart rotated and doughnut size changed successfully.
```

Otwarcie `DoughnutFormatted.docx` pokazuje wykres doughnut, którego pierwszy segment zaczyna się od pozycji 45°, a wewnętrzny promień zajmuje połowę zewnętrznego promienia.

## Typowe warianty i przypadki brzegowe

| Sytuacja | Co dostosować | Dlaczego ma znaczenie |
|-----------|----------------|----------------|
| **Multiple charts** | Iteruj przez `getChildNodes(NodeType.SHAPE, true)` i sprawdzaj `shape.hasChart()` dla każdego | Gwarantuje, że modyfikujesz zamierzony wykres, a nie pierwszy |
| **Bar or line chart** | `setStartAngle` nie ma zastosowania; użyj `chart.getSeries().get(0).setFillFormat(...)` dla innych modyfikacji wizualnych | Nie wszystkie typy wykresów obsługują obrót; tylko wykresy doughnut/pie mają kąt początkowy |
| **Chart without a doughnut hole** | Pomiń `setDoughnutHoleSize` lub najpierw przekształć typ wykresu na doughnut za pomocą `chart.setChartType(ChartType.DONUT)` | Zmiana rozmiaru otworu w wykresie nie‑doughnut powoduje wyjątek |
| **Large documents** | Użyj `DocumentBuilder.moveToDocumentStart()` i `builder.moveToNode(chartShape)` dla ukierunkowanej nawigacji | Poprawia wydajność, unikając pełnego przeglądania niepowiązanych węzłów |

## Profesjonalne wskazówki dla niezawodnej manipulacji wykresami

* **Cache the chart reference** – Jeśli planujesz modyfikować kilka właściwości, zachowaj lokalną zmienną `Chart` zamiast wielokrotnego wywoływania `chartShape.getChart()`.
* **Validate input values** – Przed wywołaniem `setStartAngle` lub `setDoughnutHoleSize` zweryfikuj zakres, aby uniknąć błędów w czasie wykonania.
* **Use a license** – Tryb ewaluacji wstawia znak wodny na pierwszej stronie. Zastosowanie licencji (`License license = new License(); license.setLicense("Aspose.Words.lic");`) go usuwa.

## Kolejne kroki

Teraz, gdy znasz **how to rotate chart** i **change doughnut chart size**, możesz eksplorować inne scenariusze **modify chart in Word**:

* Zmieniaj kolory segmentów przy użyciu `chart.getSeries().get(0).getDataPoints().get(i).getFillFormat().setForeColor(Color.getRed())`.
* Dodawaj etykiety danych wywołując `chart.getSeries().get(0).setHasDataLabel(true)`.
* Eksportuj wykres jako obraz przy użyciu `chart.toImage(300, 300, ImageType.PNG)`.

Każde z tych rozszerzeń stosuje ten sam schemat: uzyskaj obiekt `Chart`, wywołaj odpowiedni setter i zapisz dokument.

---

**Właśnie opanowałeś obracanie i zmianę rozmiaru wykresów doughnut w Wordzie przy użyciu Javy.** Śmiało dostosuj kod do innych typów wykresów, zintegrować go z większym potokiem generowania dokumentów lub połączyć z Aspose.Slides do automatyzacji PowerPointa. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z krok po kroku wyjaśnieniami, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak utworzyć wykres kolumnowy przy użyciu Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Ukryj oś wykresu w dokumencie Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Wstaw wykres bąbelkowy w dokumencie Word](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}