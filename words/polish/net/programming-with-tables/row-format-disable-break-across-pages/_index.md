---
title: Format wiersza Wyłącz podział na strony
linktitle: Format wiersza Wyłącz podział na strony
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak wyłączyć podział wierszy na stronach w dokumentach programu Word przy użyciu pakietu Aspose.Words for .NET, aby zachować czytelność i formatowanie tabeli.
weight: 10
url: /pl/net/programming-with-tables/row-format-disable-break-across-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Format wiersza Wyłącz podział na strony

## Wstęp

Podczas pracy z tabelami w dokumentach Worda możesz chcieć upewnić się, że wiersze nie są dzielone na strony, co może być niezbędne do zachowania czytelności i formatowania dokumentów. Aspose.Words for .NET zapewnia łatwy sposób na wyłączenie podziału wierszy na strony.

W tym samouczku pokażemy Ci, jak wyłączyć podział wierszy na stronach w dokumencie programu Word za pomocą pakietu Aspose.Words for .NET.

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że spełniasz następujące wymagania wstępne:
- Zainstalowano bibliotekę Aspose.Words dla .NET.
- Dokument programu Word zawierający tabelę rozciągającą się na wiele stron.

## Importuj przestrzenie nazw

Najpierw zaimportuj niezbędne przestrzenie nazw do swojego projektu:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Krok 1: Załaduj dokument

Załaduj dokument zawierający tabelę rozciągającą się na wiele stron.

```csharp
// Ścieżka do katalogu dokumentów
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## Krok 2: Uzyskaj dostęp do tabeli

Uzyskaj dostęp do pierwszej tabeli w dokumencie. Zakłada się, że tabela, którą chcesz zmodyfikować, jest pierwszą tabelą w dokumencie.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Krok 3: Wyłącz dzielenie między stronami dla wszystkich wierszy

 Przejdź przez każdy wiersz w tabeli i ustaw`AllowBreakAcrossPages`nieruchomość do`false`. Dzięki temu wiersze nie będą dzielone na strony.

```csharp
// Wyłącz dzielenie między strony dla wszystkich wierszy w tabeli.
foreach (Row row in table.Rows)
    row.RowFormat.AllowBreakAcrossPages = false;
```

## Krok 4: Zapisz dokument

Zapisz zmodyfikowany dokument w podanym katalogu.

```csharp
doc.Save(dataDir + "WorkingWithTables.RowFormatDisableBreakAcrossPages.docx");
```

## Wniosek

W tym samouczku pokazaliśmy, jak wyłączyć podział wierszy na stronach w dokumencie Word za pomocą Aspose.Words dla .NET. Postępując zgodnie z powyższymi krokami, możesz upewnić się, że wiersze tabeli pozostaną nienaruszone i nie zostaną podzielone na stronach, zachowując czytelność i formatowanie dokumentu.

## Najczęściej zadawane pytania

### Czy mogę wyłączyć podział wierszy na stronach dla konkretnego wiersza, a nie dla wszystkich wierszy?  
 Tak, możesz wyłączyć podziały wierszy dla określonych wierszy, uzyskując dostęp do żądanego wiersza i ustawiając jego`AllowBreakAcrossPages`nieruchomość do`false`.

### Czy ta metoda działa w przypadku tabel zawierających połączone komórki?  
 Tak, ta metoda działa w przypadku tabel ze scalonymi komórkami. Właściwość`AllowBreakAcrossPages` dotyczy całego wiersza, niezależnie od scalenia komórek.

### Czy ta metoda zadziała, jeśli tabela jest zagnieżdżona w innej tabeli?  
Tak, możesz uzyskać dostęp i modyfikować zagnieżdżone tabele w ten sam sposób. Upewnij się, że poprawnie odwołujesz się do zagnieżdżonej tabeli przez jej indeks lub inne właściwości.

### Jak mogę sprawdzić, czy wiersz pozwala na podział na strony?  
 Możesz sprawdzić, czy wiersz pozwala na podział na strony, uzyskując dostęp do`AllowBreakAcrossPages` własność`RowFormat` i sprawdzając jego wartość.

### Czy istnieje sposób, aby zastosować to ustawienie do wszystkich tabel w dokumencie?  
Tak, możesz przejść przez wszystkie tabele w dokumencie i zastosować to ustawienie do każdej z nich.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
