---
category: general
date: 2026-09-11
description: Zapisz dokument Word po edycji wykresu pierścieniowego przy użyciu Aspose.Words
  for Java. Dowiedz się, jak zmienić rozmiar otworu w wykresie pierścieniowym, obrócić
  wykres pierścieniowy oraz edytować właściwości wykresu pierścieniowego.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word document
- rotate doughnut chart
- edit doughnut chart
- change doughnut hole
- change chart hole size
language: pl
lastmod: 2026-09-11
og_description: Zapisz dokument Word po edycji wykresu pierścieniowego przy użyciu
  Aspose.Words for Java. Ten samouczek pokazuje, jak zmienić rozmiar otworu w wykresie
  pierścieniowym, obrócić wykres pierścieniowy oraz dostosować wygląd wykresu.
og_image_alt: Java code editing a doughnut chart before saving Word document
og_title: Zapisz dokument Word po edycji wykresu pierścieniowego – przewodnik Java
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Save Word document after editing a doughnut chart with Aspose.Words
    for Java. Learn how to change doughnut hole size, rotate doughnut chart, and edit
    doughnut chart properties.
  headline: Save Word document after editing doughnut chart in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word
- Chart
- Doughnut
title: Zapisz dokument Word po edycji wykresu pierścieniowego w Javie
url: /pl/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zapisz dokument Word po edycji wykresu pierścieniowego w Javie

Jeśli potrzebujesz **zapisać dokument Word**, który zawiera spersonalizowany wykres pierścieniowy, ten przewodnik pokaże Ci dokładnie, jak to zrobić. W kilku linijkach Javy możesz zmienić rozmiar otworu wykresu, obrócić wykres pierścieniowy, a następnie zapisać wynik na dysku.

Zobaczysz kompletny, gotowy do uruchomienia przykład wykorzystujący Aspose.Words for Java, plus wskazówki dotyczące obsługi wielu wykresów, weryfikacji typów węzłów i unikania typowych pułapek. Nie są wymagane żadne zewnętrzne odwołania — wszystko, czego potrzebujesz, jest w zestawie.

## Wymagania wstępne

Zanim rozpoczniesz, upewnij się, że masz:

- Java 17 lub nowszą
- Maven lub Gradle do zarządzania zależnościami
- Aspose.Words for Java (wersja 23.9 lub późniejsza) dodany do projektu  
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.9</version>
  </dependency>
  ```
- Plik Word (`input.docx`) zawierający pojedynczy wykres pierścieniowy

## Krok 1: Załaduj dokument Word

Pierwszym krokiem jest otwarcie pliku źródłowego. Ten krok jest niezbędny, ponieważ wszystkie kolejne operacje działają na obiekcie `Document` w pamięci.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // Load the Word document that contains a doughnut chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Dlaczego?** Ładowanie dokumentu tworzy reprezentację DOM, która pozwala przeglądać kształty, tabele i wykresy. Jeśli pliku nie da się otworzyć, Aspose.Words rzuca wyjątek, więc od razu wiesz, że ścieżka jest nieprawidłowa.

## Krok 2: Znajdź kształt wykresu pierścieniowego

Wykres jest przechowywany wewnątrz węzła `Shape`. Pobieramy pierwszy kształt, który zawiera wykres, i rzutujemy jego renderer na `Chart`.

```java
        // Find the first shape that contains a chart
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        // Ensure the shape actually holds a chart
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        // Get the Chart object for further manipulation
        Chart chart = chartShape.getChart();
```

> **Dlaczego?** Sprawdzenie `isChart()` zapobiega `ClassCastException`, gdy dokument zawiera obrazy lub inne kształty przed wykresem. Dzięki temu kod jest odporny na dokumenty z mieszanym zawartością.

## Krok 3: Zmień rozmiar otworu wykresu pierścieniowego  

Teraz edytujemy otwór wykresu. Metoda `setHoleSize` przyjmuje procent promienia wykresu (10 – 90).

```java
        // Adjust the size of the doughnut hole (percentage of the chart radius)
        chart.setHoleSize(30);   // The hole occupies 30 % of the radius
```

> **Dlaczego?** Zmiana otworu wykresu (`change doughnut hole` / `change chart hole size`) pozwala podkreślić lub zminimalizować centralny obszar. Wartości spoza zakresu 10‑90 % są ignorowane przez API.

## Krok 4: Obróć wykres pierścieniowy  

Aby kontrolować, od którego miejsca zaczyna się pierwszy segment, ustaw kąt pierwszego segmentu. To efektywnie **rotate doughnut chart**.

```java
        // Rotate the chart so that the first slice starts at a custom angle
        chart.setFirstSliceAngle(45);   // Starts the first slice at 45 degrees
```

> **Dlaczego?** Obracanie wykresu jest przydatne, gdy chcesz, aby konkretny segment znajdował się na górze lub aby dopasować go do specyfikacji projektu.

## Krok 5: Zapisz zaktualizowany dokument  

Na koniec zapisz zmiany do nowego pliku. To moment, w którym **save Word document** z edytowanym wykresem.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Oczekiwany wynik:** `output.docx` zawiera oryginalną treść, ale wykres pierścieniowy ma teraz otwór o wielkości 30 % i jego pierwszy segment zaczyna się od 45 °. Otwierając plik w Microsoft Word, zobaczysz przekształcony wykres.

## Pełny działający przykład

Poniżej znajduje się kompletny program, który możesz skopiować i wkleić do swojego IDE. Zawiera wszystkie importy oraz obsługę błędów potrzebną do **edit doughnut chart** i **save Word document** w sposób bezpieczny.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Locate the first chart shape
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        Chart chart = chartShape.getChart();

        // 3. Change the doughnut hole size
        chart.setHoleSize(30); // 30 % hole

        // 4. Rotate the doughnut chart
        chart.setFirstSliceAngle(45); // start at 45°

        // 5. Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Oczekiwany wynik

Po otwarciu `output.docx`:

- Centralny otwór wykresu pierścieniowego zajmuje mniej więcej jedną trzecią promienia wykresu.  
- Pierwszy segment zaczyna się w pozycji 45 stopni, przesuwając cały wykres zgodnie z ruchem wskazówek zegara.  

Obie zmiany wizualne są od razu widoczne w Wordzie.

## Typowe warianty i przypadki brzegowe

| Sytuacja | Jak postępować |
|-----------|----------------|
| **Wiele wykresów** | Przejdź przez `doc.getChildNodes(NodeType.SHAPE, true)` i filtruj `shape.isChart()`; zastosuj `setHoleSize` / `setFirstSliceAngle` do każdego `Chart`. |
| **Wykres nie jest pierścieniowy** | Sprawdź `chart.getType()`; wywołuj `setHoleSize` tylko wtedy, gdy `chart.getType() == ChartType.DOUGHNUT`. |
| **Dynamiczna zmiana rozmiaru otworu** | Oblicz żądany procent na podstawie wartości danych, a następnie wywołaj `setHoleSize(computedValue)`. |
| **Zapis do strumienia** | Użyj |

## Co powinieneś nauczyć się dalej?


Poniższe samouczki dotyczą tematów ściśle powiązanych, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Save Word with Password using Aspose.Words for Java](/words/english/java/document-loading-and-saving/advance-saving-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}