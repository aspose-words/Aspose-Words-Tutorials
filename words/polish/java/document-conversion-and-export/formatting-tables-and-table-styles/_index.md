---
date: 2025-11-28
description: Naucz się zmieniać obramowania komórek i formatować tabele przy użyciu
  Aspose.Words dla Javy. Ten przewodnik krok po kroku obejmuje ustawianie obramowań,
  stosowanie stylu pierwszej kolumny, automatyczne dopasowywanie zawartości tabeli
  oraz stosowanie stylów tabel.
language: pl
linktitle: How to Change Cell Borders in Tables – Aspose.Words for Java
second_title: Aspose.Words Java Document Processing API
title: Jak zmienić obramowanie komórek w tabelach – Aspose.Words for Java
url: /java/document-conversion-and-export/formatting-tables-and-table-styles/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak zmienić obramowania komórek w tabelach – Aspose.Words for Java

## Wstęp

Jeśli chodzi o formatowanie dokumentów, tabele odgrywają kluczową rolę, a **znajomość sposobu zmiany obramowań komórek** jest niezbędna do tworzenia przejrzystych, profesjonalnych układów. Jeśli programujesz w Javie i używasz Aspose.Words, masz już potężny zestaw narzędzi pod ręką. W tym samouczku przeprowadzimy Cię krok po kroku przez cały proces formatowania tabel, zmiany obramowań komórek, zastosowania *stylu pierwszej kolumny* oraz użycia *automatycznego dopasowywania zawartości tabeli*, aby Twoje dokumenty wyglądały dopracowanie.

## Szybkie odpowiedzi
- **Jaka jest podstawowa klasa do budowania tabel?** `DocumentBuilder` tworzy tabele i komórki programowo.  
- **Jak zmienić grubość obramowania jednej komórki?** Użyj `builder.getCellFormat().getBorders().getLeft().setLineWidth(value)`.  
- **Czy mogę zastosować predefiniowany styl tabeli?** Tak – wywołaj `table.setStyleIdentifier(StyleIdentifier.YOUR_STYLE)`.  
- **Jaką metodą automatycznie dopasować tabelę do jej zawartości?** `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)`.  
- **Czy potrzebna jest licencja do użytku produkcyjnego?** Ważna licencja Aspose.Words jest wymagana przy użyciu nie‑trial.

## Co oznacza „jak zmienić obramowania komórek” w Aspose.Words?

Zmiana obramowań komórek oznacza dostosowanie widocznych linii oddzielających komórki – ich koloru, szerokości i stylu linii. Aspose.Words udostępnia bogate API, które pozwala regulować te właściwości na poziomie tabeli, wiersza lub pojedynczej komórki, dając precyzyjną kontrolę nad wyglądem dokumentów.

## Dlaczego warto używać Aspose.Words for Java do stylizacji tabel?

- **Spójny wygląd na wszystkich platformach** – ten sam kod stylizacji działa na Windows, Linux i macOS.  
- **Brak zależności od Microsoft Word** – generuj lub modyfikuj dokumenty po stronie serwera.  
- **Bogata biblioteka stylów** – wbudowane style tabel (np. *styl pierwszej kolumny*) oraz pełne możliwości auto‑fit.  

## Wymagania wstępne

1. **Java Development Kit (JDK) 8+** – upewnij się, że `java` znajduje się w zmiennej PATH.  
2. **IDE** – IntelliJ IDEA, Eclipse lub dowolny edytor, którego używasz.  
3. **Aspose.Words for Java** – pobierz najnowszy plik JAR ze [strony oficjalnej](https://releases.aspose.com/words/java/).  
4. **Podstawowa znajomość Javy** – powinieneś umieć tworzyć projekt Maven/Gradle i dodawać zewnętrzne pliki JAR.

## Importowanie pakietów

Aby rozpocząć pracę z tabelami, potrzebujesz podstawowych klas Aspose.Words:

```java
import com.aspose.words.*;
```

Ten pojedynczy import daje dostęp do `Document`, `DocumentBuilder`, `Table`, `StyleIdentifier` i wielu innych narzędzi.

## Jak zmienić obramowania komórek

Poniżej stworzymy prostą tabelę, zmienimy jej ogólne obramowania, a następnie dostosujemy poszczególne komórki.

### Krok 1: Załaduj nowy dokument

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Krok 2: Utwórz tabelę i ustaw globalne obramowania

```java
Table table = builder.startTable();
builder.insertCell();

// Set the borders for the entire table.
table.setBorders(LineStyle.SINGLE, 2.0, Color.BLACK);
        
// Set the cell shading for this cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.RED);
builder.writeln("Cell #1");

builder.insertCell();
        
// Specify a different cell shading for the second cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.GREEN);
builder.writeln("Cell #2");

builder.endRow();
```

### Krok 3: Zmień obramowania jednej komórki

```java
// Clear the cell formatting from previous operations.
builder.getCellFormat().clearFormatting();

builder.insertCell();

// Create larger borders for the first cell of this row.
builder.getCellFormat().getBorders().getLeft().setLineWidth(4.0);
builder.getCellFormat().getBorders().getRight().setLineWidth(4.0);
builder.getCellFormat().getBorders().getTop().setLineWidth(4.0);
builder.getCellFormat().getBorders().getBottom().setLineWidth(4.0);
builder.writeln("Cell #3");

builder.insertCell();
builder.getCellFormat().clearFormatting();
builder.writeln("Cell #4");
        
doc.save("FormatTableAndCellWithDifferentBorders.docx");
```

#### Co robi kod
- **Globalne obramowania** – `table.setBorders` nadaje całej tabeli czarną linię o grubości 2 punktów.  
- **Cieniowanie komórek** – pokazuje, jak pokolorować poszczególne komórki (czerwoną i zieloną).  
- **Niestandardowe obramowania komórki** – trzecia komórka otrzymuje obramowanie o grubości 4 punktów po wszystkich stronach, co wyróżnia ją wizualnie.

## Zastosowanie stylów tabel (w tym styl pierwszej kolumny)

Style tabel pozwalają nadać spójny wygląd jednym wywołaniem. Pokażemy także, jak włączyć *styl pierwszej kolumny* i automatycznie dopasować tabelę do zawartości.

### Krok 4: Utwórz nowy dokument do stylizacji

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Table table = builder.startTable();
        
// We must insert at least one row first before setting any table formatting.
builder.insertCell();
```

### Krok 5: Zastosuj predefiniowany styl i włącz formatowanie pierwszej kolumny

```java
// Set the table style based on a unique style identifier.
table.setStyleIdentifier(StyleIdentifier.MEDIUM_SHADING_1_ACCENT_1);
        
// Apply which features should be formatted by the style.
table.setStyleOptions(TableStyleOptions.FIRST_COLUMN | TableStyleOptions.ROW_BANDS | TableStyleOptions.FIRST_ROW);

// Auto‑fit the table so columns shrink or expand to fit the content.
table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS);
```

### Krok 6: Wypełnij tabelę danymi

```java
builder.writeln("Item");
builder.getCellFormat().setRightPadding(40.0);
builder.insertCell();
builder.writeln("Quantity (kg)");
builder.endRow();

builder.insertCell();
builder.writeln("Apples");
builder.insertCell();
builder.writeln("20");
builder.endRow();

builder.insertCell();
builder.writeln("Bananas");
builder.insertCell();
builder.writeln("40");
builder.endRow();

builder.insertCell();
builder.writeln("Carrots");
builder.insertCell();
builder.writeln("50");
builder.endRow();

doc.save("BuildTableWithStyle.docx");
```

#### Dlaczego to ważne
- **Identyfikator stylu** – `MEDIUM_SHADING_1_ACCENT_1` nadaje tabeli czysty, cieniowany wygląd.  
- **Styl pierwszej kolumny** – podkreślenie pierwszej kolumny zwiększa czytelność, szczególnie w raportach.  
- **Paski wierszy** – naprzemienne kolory wierszy ułatwiają przegląd dużych tabel.  
- **Auto‑fit** – zapewnia, że szerokość tabeli dostosowuje się do zawartości, zapobiegając obcięciu tekstu.

## Typowe problemy i rozwiązywanie

| Problem | Typowa przyczyna | Szybka naprawa |
|-------|----------------|-----------|
| Obramowania nie są widoczne | Użycie `clearFormatting()` po ustawieniu obramowań | Ustaw obramowania **po** wyczyszczeniu formatowania lub zastosuj je ponownie. |
| Cieniowanie ignorowane w scalonych komórkach | Cieniowanie zastosowane przed scaleniem | Zastosuj cieniowanie **po** scaleniu komórek. |
| Szerokość tabeli przekracza marginesy strony | Brak auto‑fit | Wywołaj `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` lub ustaw stałą szerokość. |
| Styl nie został zastosowany | Nieprawidłowa wartość `StyleIdentifier` | Sprawdź, czy identyfikator istnieje w wersji Aspose.Words, której używasz. |

## Najczęściej zadawane pytania

**P: Czy mogę używać własnych stylów tabel, które nie są w domyślnych opcjach?**  
O: Tak, możesz tworzyć i stosować własne style programowo. Zobacz dokumentację [Aspose.Words](https://reference.aspose.com/words/java/) po szczegóły.

**P: Jak zastosować formatowanie warunkowe do komórek?**  
O: Użyj standardowej logiki Java do sprawdzania wartości komórek, a następnie wywołaj odpowiednie metody formatowania (np. zmień kolor tła, jeśli wartość przekracza określony próg).

**P: Czy można formatować scalone komórki tak samo jak zwykłe?**  
O: Oczywiście. Po scaleniu komórek zastosuj cieniowanie lub obramowania przy użyciu tych samych API `CellFormat`.

**P: Co zrobić, gdy tabela ma się dynamicznie zmieniać w zależności od danych wprowadzonych przez użytkownika?**  
O: Dostosuj szerokości kolumn lub ponownie wywołaj `autoFit` po wstawieniu nowych danych, aby przeliczyć układ.

**P: Gdzie mogę znaleźć więcej przykładów stylizacji tabel?**  
O: Oficjalna [dokumentacja API Aspose.Words](https://reference.aspose.com/words/java/) zawiera obszerne zestawy przykładów.

## Zakończenie

Masz teraz kompletny zestaw narzędzi do **zmiany obramowań komórek**, zastosowania *stylu pierwszej kolumny* oraz **automatycznego dopasowywania zawartości tabeli** przy użyciu Aspose.Words for Java. Opanowując te techniki, możesz tworzyć dokumenty, które są zarówno bogate w dane, jak i atrakcyjne wizualnie – idealne do raportów, faktur i wszelkich innych krytycznych dla biznesu wyjść.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Ostatnia aktualizacja:** 2025-11-28  
**Testowane z:** Aspose.Words for Java 24.12 (najnowsza w momencie pisania)  
**Autor:** Aspose