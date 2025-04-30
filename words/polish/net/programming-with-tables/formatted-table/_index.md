---
"description": "Dowiedz się, jak tworzyć i formatować tabele w dokumentach programu Word za pomocą pakietu Aspose.Words dla platformy .NET, korzystając ze szczegółowego przewodnika krok po kroku."
"linktitle": "Sformatowana tabela"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Sformatowana tabela"
"url": "/pl/net/programming-with-tables/formatted-table/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sformatowana tabela

## Wstęp

Tworzenie i formatowanie tabel w dokumentach Word programowo może wydawać się trudnym zadaniem, ale dzięki Aspose.Words dla .NET staje się proste i łatwe do opanowania. W tym samouczku przeprowadzimy Cię przez proces tworzenia sformatowanej tabeli w dokumencie Word przy użyciu Aspose.Words dla .NET. Omówimy wszystko, od konfiguracji środowiska po zapisywanie dokumentu z pięknie sformatowaną tabelą.

## Wymagania wstępne

Zanim zagłębisz się w kod, upewnijmy się, że masz wszystko, czego potrzebujesz:

1. Biblioteka Aspose.Words dla .NET: Pobierz ją z [Tutaj](https://releases.aspose.com/words/net/).
2. Środowisko programistyczne: IDE, np. Visual Studio.
3. .NET Framework: Upewnij się, że na Twoim komputerze jest zainstalowany .NET Framework.

## Importuj przestrzenie nazw

Zanim napiszesz właściwy kod, musisz zaimportować niezbędne przestrzenie nazw:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

## Krok 1: Skonfiguruj katalog dokumentów

Najpierw musisz określić ścieżkę, w której zostanie zapisany Twój dokument.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Zastępować `"YOUR DOCUMENT DIRECTORY"` z rzeczywistą ścieżką, pod którą chcesz zapisać dokument.

## Krok 2: Zainicjuj dokument i DocumentBuilder

Teraz zainicjuj nowy dokument i obiekt DocumentBuilder.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Ten `DocumentBuilder` jest klasą pomocniczą, która upraszcza proces tworzenia dokumentów.

## Krok 3: Uruchom tabelę

Następnie zacznij tworzyć tabelę za pomocą `StartTable` metoda.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

Aby rozpocząć tworzenie tabeli konieczne jest wstawienie komórki.

## Krok 4: Zastosuj formatowanie całej tabeli

Możesz zastosować formatowanie, które wpływa na całą tabelę. Na przykład ustawienie lewego wcięcia:

```csharp
table.LeftIndent = 20.0;
```

## Krok 5: Formatowanie wiersza nagłówka

Ustaw wysokość, wyrównanie i inne właściwości wiersza nagłówka.

```csharp
builder.RowFormat.Height = 40.0;
builder.RowFormat.HeightRule = HeightRule.AtLeast;
builder.CellFormat.Shading.BackgroundPatternColor = Color.FromArgb(198, 217, 241);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Font.Size = 16;
builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.CellFormat.Width = 100.0;
builder.Write("Header Row,\n Cell 1");
```

W tym kroku sprawimy, że wiersz nagłówka się wyróżni, ustawiając kolor tła, rozmiar czcionki i wyrównanie.

## Krok 6: Wstaw dodatkowe komórki nagłówka

Wstaw więcej komórek do wiersza nagłówka:

```csharp
builder.InsertCell();
builder.Write("Header Row,\n Cell 2");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Header Row,\n Cell 3");
builder.EndRow();
```

## Krok 7: Formatowanie wierszy treści

Po skonfigurowaniu nagłówka sformatuj treść tabeli:

```csharp
builder.CellFormat.Shading.BackgroundPatternColor = Color.White;
builder.CellFormat.Width = 100.0;
builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;
builder.RowFormat.Height = 30.0;
builder.RowFormat.HeightRule = HeightRule.Auto;
```

## Krok 8: Wstaw rzędy ciała

Wstaw wiersze treści z treścią:

```csharp
builder.InsertCell();
builder.Font.Size = 12;
builder.Font.Bold = false;
builder.Write("Row 1, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 1, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 1, Cell 3 Content");
builder.EndRow();
```

Powtórz dla kolejnych rzędów:

```csharp
builder.InsertCell();
builder.CellFormat.Width = 100.0;
builder.Write("Row 2, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 2, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 2, Cell 3 Content.");
builder.EndRow();
builder.EndTable();
```

## Krok 9: Zapisz dokument

Na koniec zapisz dokument w podanym katalogu:

```csharp
doc.Save(dataDir + "WorkingWithTables.FormattedTable.docx");
```

Spowoduje to utworzenie i zapisanie dokumentu Word zawierającego sformatowaną tabelę.

## Wniosek

I masz to! Wykonując te kroki, możesz utworzyć dobrze sformatowaną tabelę w dokumencie Worda przy użyciu Aspose.Words dla .NET. Ta potężna biblioteka ułatwia programowe manipulowanie dokumentami Worda, oszczędzając czas i wysiłek.

## Najczęściej zadawane pytania

### Czym jest Aspose.Words dla .NET?
Aspose.Words for .NET to zaawansowana biblioteka umożliwiająca programowe tworzenie, edycję i konwersję dokumentów Word.

### Czy mogę użyć różnych kolorów dla różnych rzędów?
Tak, możesz stosować różne formatowanie, w tym kolory, w różnych wierszach i komórkach.

### Czy Aspose.Words dla .NET jest darmowy?
Aspose.Words dla .NET to płatna biblioteka, ale można ją pobrać [bezpłatny okres próbny](https://releases.aspose.com/).

### Jak uzyskać pomoc techniczną dotyczącą Aspose.Words dla platformy .NET?
Możesz uzyskać wsparcie od [Fora społeczności Aspose](https://forum.aspose.com/c/words/8).

### Czy mogę tworzyć inne typy dokumentów za pomocą Aspose.Words dla .NET?
Tak, Aspose.Words dla platformy .NET obsługuje różne formaty dokumentów, w tym PDF, HTML i TXT.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}