---
title: Formatowanie tabel i style tabel
linktitle: Formatowanie tabel i style tabel
second_title: Aspose.Words API przetwarzania dokumentów Java
description: Dowiedz się, jak formatować tabele i stosować style za pomocą Aspose.Words for Java. Ten przewodnik krok po kroku obejmuje ustawianie obramowań, cieniowanie komórek i stosowanie stylów tabeli.
weight: 17
url: /pl/java/document-conversion-and-export/formatting-tables-and-table-styles/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formatowanie tabel i style tabel


## Wstęp

Jeśli chodzi o formatowanie dokumentów, tabele odgrywają kluczową rolę w organizowaniu i prezentowaniu danych w sposób przejrzysty. Jeśli pracujesz z Javą i Aspose.Words, masz do dyspozycji potężne narzędzia do tworzenia i formatowania tabel w dokumentach. Niezależnie od tego, czy projektujesz prostą tabelę, czy stosujesz zaawansowane style, Aspose.Words dla Javy oferuje szereg funkcji, które pomogą Ci osiągnąć profesjonalnie wyglądające rezultaty.

W tym przewodniku przeprowadzimy Cię przez proces formatowania tabel i stosowania stylów tabel przy użyciu Aspose.Words for Java. Nauczysz się, jak ustawiać obramowania tabel, stosować cieniowanie komórek i używać stylów tabel, aby poprawić wygląd dokumentów. Na koniec będziesz mieć umiejętności tworzenia dobrze sformatowanych tabel, które wyróżnią Twoje dane.

## Wymagania wstępne

Zanim zaczniemy, jest kilka rzeczy, które musisz mieć na miejscu:

1. Java Development Kit (JDK): Upewnij się, że masz zainstalowany JDK 8 lub nowszy. Aspose.Words for Java wymaga zgodnego JDK, aby działać poprawnie.
2. Zintegrowane środowisko programistyczne (IDE): IDE, takie jak IntelliJ IDEA lub Eclipse, pomoże Ci zarządzać projektami Java i usprawni proces tworzenia oprogramowania.
3.  Biblioteka Aspose.Words dla Java: Pobierz najnowszą wersję Aspose.Words dla Java[Tutaj](https://releases.aspose.com/words/java/) i uwzględnij go w swoim projekcie.
4. Przykładowy kod: Będziemy korzystać z przykładowych fragmentów kodu, dlatego upewnij się, że masz podstawową wiedzę na temat programowania w Javie i wiesz, jak integrować biblioteki ze swoim projektem.

## Importuj pakiety

Aby pracować z Aspose.Words for Java, musisz zaimportować odpowiednie pakiety do swojego projektu. Pakiety te dostarczają klas i metod niezbędnych do manipulowania dokumentami i formatowania ich.

```java
import com.aspose.words.*;
```

To polecenie importu udostępnia wszystkie podstawowe klasy wymagane do tworzenia i formatowania tabel w dokumentach.

## Krok 1: Formatowanie tabel

Formatowanie tabel w Aspose.Words dla Java obejmuje ustawianie obramowań, cieniowanie komórek i stosowanie różnych opcji formatowania. Oto, jak możesz to zrobić:

### Załaduj dokument

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Utwórz i sformatuj tabelę

```java
Table table = builder.startTable();
builder.insertCell();

// Ustaw obramowanie całej tabeli.
table.setBorders(LineStyle.SINGLE, 2.0, Color.BLACK);
        
// Ustaw cieniowanie komórki dla tej komórki.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.RED);
builder.writeln("Cell #1");

builder.insertCell();
        
// Określ inne cieniowanie komórki dla drugiej komórki.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.GREEN);
builder.writeln("Cell #2");

builder.endRow();
```

### Dostosuj obramowania komórek

```java
// Wyczyść formatowanie komórek z poprzednich operacji.
builder.getCellFormat().clearFormatting();

builder.insertCell();

// Utwórz większe obramowanie dla pierwszej komórki tego wiersza.
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

### Wyjaśnienie

W tym przykładzie:
- Ustaw obramowanie: Ustawiamy obramowanie całej tabeli na styl pojedynczej linii o grubości 2,0 punktów.
- Cieniowanie komórek: Pierwsza komórka jest cieniowana na czerwono, a druga na zielono. Pomaga to wizualnie odróżnić komórki.
- Obramowania komórek: W przypadku trzeciej komórki tworzymy grubsze obramowania, aby wyróżnić ją w inny sposób niż pozostałe.

## Krok 2: Stosowanie stylów tabeli

Style tabel w Aspose.Words for Java pozwalają na zastosowanie wstępnie zdefiniowanych opcji formatowania do tabel, co ułatwia uzyskanie spójnego wyglądu. Oto jak zastosować styl do tabeli:

### Utwórz dokument i tabelę

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Table table = builder.startTable();
        
// Przed ustawieniem formatowania tabeli musimy wstawić co najmniej jeden wiersz.
builder.insertCell();
```

### Zastosuj styl tabeli

```java
// Ustaw styl tabeli na podstawie unikalnego identyfikatora stylu.
table.setStyleIdentifier(StyleIdentifier.MEDIUM_SHADING_1_ACCENT_1);
        
// Zastosuj funkcje, które powinny być sformatowane przez styl.
table.setStyleOptions(TableStyleOptions.FIRST_COLUMN | TableStyleOptions.ROW_BANDS | TableStyleOptions.FIRST_ROW);
table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS);
```

### Dodaj dane tabeli

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

### Wyjaśnienie

W tym przykładzie:
- Ustaw styl tabeli: Stosujemy wstępnie zdefiniowany styl (`MEDIUM_SHADING_1_ACCENT_1`) do tabeli. Ten styl obejmuje formatowanie różnych części tabeli.
- Opcje stylu: Określamy, że pierwsza kolumna, pasma wierszy i pierwszy wiersz powinny być sformatowane zgodnie z opcjami stylu.
-  AutoFit: Używamy`AUTO_FIT_TO_CONTENTS` aby zapewnić, że tabela dopasuje swój rozmiar do zawartości.

## Wniosek

masz to! Udało Ci się sformatować tabele i zastosować style za pomocą Aspose.Words for Java. Dzięki tym technikom możesz tworzyć tabele, które są nie tylko funkcjonalne, ale również atrakcyjne wizualnie. Skuteczne formatowanie tabel może znacznie poprawić czytelność i profesjonalny wygląd Twoich dokumentów.

Aspose.Words for Java to solidne narzędzie oferujące rozbudowane funkcje do manipulacji dokumentami. Opanowując formatowanie tabel i style, jesteś o krok bliżej wykorzystania pełnej mocy tej biblioteki.

## Często zadawane pytania

### 1. Czy mogę używać niestandardowych stylów tabeli, które nie są zawarte w opcjach domyślnych?

 Tak, możesz definiować i stosować niestandardowe style do swoich tabel za pomocą Aspose.Words dla Java. Sprawdź[dokumentacja](https://reference.aspose.com/words/java/) aby uzyskać więcej szczegółów na temat tworzenia niestandardowych stylów.

### 2. Jak mogę zastosować formatowanie warunkowe do tabel?

Aspose.Words for Java umożliwia programowe dostosowywanie formatowania tabeli na podstawie warunków. Można to zrobić, sprawdzając określone kryteria w kodzie i stosując odpowiednie formatowanie.

### 3. Czy mogę sformatować połączone komórki w tabeli?

Tak, możesz formatować scalone komórki tak jak zwykłe komórki. Upewnij się, że zastosujesz formatowanie po scaleniu komórek, aby zobaczyć odzwierciedlone zmiany.

### 4. Czy istnieje możliwość dynamicznej zmiany układu tabeli?

Tak, możesz dynamicznie dostosowywać układ tabeli, modyfikując rozmiary komórek, szerokość tabeli i inne właściwości na podstawie zawartości lub danych wprowadzonych przez użytkownika.

### 5. Gdzie mogę uzyskać więcej informacji na temat formatowania tabel?

 Aby uzyskać bardziej szczegółowe przykłady i opcje, odwiedź stronę[Dokumentacja API Aspose.Words](https://reference.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
