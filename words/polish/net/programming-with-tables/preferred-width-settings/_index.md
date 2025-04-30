---
"description": "Dowiedz się, jak tworzyć tabele z bezwzględnymi, względnymi i automatycznymi ustawieniami szerokości w Aspose.Words dla platformy .NET, korzystając z tego przewodnika krok po kroku."
"linktitle": "Preferowane ustawienia szerokości"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Preferowane ustawienia szerokości"
"url": "/pl/net/programming-with-tables/preferred-width-settings/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Preferowane ustawienia szerokości

## Wstęp

Tabele to potężny sposób na organizowanie i prezentowanie informacji w dokumentach Word. Podczas pracy z tabelami w Aspose.Words for .NET masz kilka opcji ustawiania szerokości komórek tabeli, aby zapewnić, że idealnie pasują do układu dokumentu. Ten przewodnik przeprowadzi Cię przez proces tworzenia tabel z preferowanymi ustawieniami szerokości przy użyciu Aspose.Words for .NET, skupiając się na opcjach bezwzględnego, względnego i automatycznego ustalania rozmiaru. 

## Wymagania wstępne

Zanim przejdziesz do samouczka, upewnij się, że posiadasz następujące rzeczy:

1. Aspose.Words dla .NET: Upewnij się, że Aspose.Words dla .NET jest zainstalowany w Twoim środowisku programistycznym. Możesz go pobrać [Tutaj](https://releases.aspose.com/words/net/).

2. Środowisko programistyczne .NET: Skonfiguruj środowisko programistyczne .NET, np. Visual Studio.

3. Podstawowa wiedza o języku C#: Znajomość programowania w języku C# pomoże Ci lepiej zrozumieć fragmenty kodu i przykłady.

4. Dokumentacja Aspose.Words: Zapoznaj się z [Dokumentacja Aspose.Words](https://reference.aspose.com/words/net/) aby uzyskać szczegółowe informacje na temat interfejsu API i dalsze informacje.

## Importuj przestrzenie nazw

Zanim zaczniesz kodować, musisz zaimportować niezbędne przestrzenie nazw do swojego projektu C#:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Te przestrzenie nazw zapewniają dostęp do podstawowych funkcjonalności Aspose.Words i obiektu Table, umożliwiając manipulowanie tabelami dokumentów.

Podzielmy proces tworzenia tabeli z różnymi preferowanymi ustawieniami szerokości na jasne i łatwe do opanowania kroki.

## Krok 1: Zainicjuj dokument i DocumentBuilder

Nagłówek: Tworzenie nowego dokumentu i DocumentBuilder

Wyjaśnienie: Zacznij od utworzenia nowego dokumentu Word i `DocumentBuilder` instancja. `DocumentBuilder` Klasa ta zapewnia prosty sposób dodawania treści do dokumentu.

```csharp
// Zdefiniuj ścieżkę do zapisania dokumentu.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Utwórz nowy dokument.
Document doc = new Document();

// Utwórz DocumentBuilder dla tego dokumentu.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Tutaj określasz katalog, w którym zostanie zapisany dokument i inicjujesz `Document` I `DocumentBuilder` obiekty.

## Krok 2: Wstaw pierwszą komórkę tabeli o szerokości bezwzględnej

Wstaw pierwszą komórkę do tabeli o stałej szerokości 40 punktów. Dzięki temu komórka ta zawsze będzie miała szerokość 40 punktów, niezależnie od rozmiaru tabeli.

```csharp
// Wstaw komórkę o rozmiarze bezwzględnym.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPoints(40);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightYellow;
builder.Writeln("Cell at 40 points width");
```

W tym kroku rozpoczynasz tworzenie tabeli i wstawiasz komórkę o szerokości bezwzględnej. `PreferredWidth.FromPoints(40)` metoda ustawia szerokość komórki na 40 punktów i `Shading.BackgroundPatternColor` stosuje jasnożółty kolor tła.

## Krok 3: Wstaw komórkę o względnym rozmiarze

Wstaw inną komórkę o szerokości 20% całkowitej szerokości tabeli. To względne skalowanie zapewnia, że komórka dopasowuje się proporcjonalnie do szerokości tabeli.

```csharp
// Wstaw komórkę o rozmiarze względnym (procentowym).
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(20);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
builder.Writeln("Cell at 20% width");
```

Szerokość tej komórki będzie wynosić 20% całkowitej szerokości tabeli, dzięki czemu będzie można ją dostosować do różnych rozmiarów ekranu i układów dokumentu.

### Krok 4: Wstaw komórkę o automatycznym rozmiarze

Na koniec wstaw komórkę, która automatycznie dopasuje swój rozmiar do ilości wolnego miejsca w tabeli.

```csharp
// Wstaw komórkę o automatycznym rozmiarze.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.Auto;
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightGreen;
builder.Writeln("Cell automatically sized. Ten size of this cell is calculated from the table preferred width.");
builder.Writeln("In this case the cell will fill up the rest of the available space.");
```

The `PreferredWidth.Auto` ustawienie pozwala tej komórce rozszerzać się lub kurczyć w oparciu o przestrzeń pozostałą po uwzględnieniu innych komórek. Dzięki temu układ tabeli wygląda na zrównoważony i profesjonalny.

## Krok 5: Zakończ i zapisz dokument

Po wstawieniu wszystkich komórek uzupełnij tabelę i zapisz dokument w określonej ścieżce.

```csharp
// Zapisz dokument.
doc.Save(dataDir + "WorkingWithTables.PreferredWidthSettings.docx");
```

Ten krok kończy tworzenie tabeli i zapisuje dokument pod nazwą pliku „WorkingWithTables.PreferredWidthSettings.docx” w wyznaczonym katalogu.

## Wniosek

Tworzenie tabel z preferowanymi ustawieniami szerokości w Aspose.Words dla .NET jest proste, gdy zrozumiesz różne dostępne opcje rozmiarów. Niezależnie od tego, czy potrzebujesz stałych, względnych czy automatycznych szerokości komórek, Aspose.Words zapewnia elastyczność, aby sprawnie obsługiwać różne scenariusze układu tabeli. Postępując zgodnie z krokami opisanymi w tym przewodniku, możesz upewnić się, że Twoje tabele są dobrze ustrukturyzowane i atrakcyjne wizualnie w dokumentach Word.

## Najczęściej zadawane pytania

### Jaka jest różnica pomiędzy bezwzględną i względną szerokością komórki?
Bezwzględne szerokości komórek są stałe i nie ulegają zmianie, natomiast szerokości względne są dostosowywane na podstawie całkowitej szerokości tabeli.

### Czy mogę używać ujemnych wartości procentowych dla szerokości względnych?
Nie, ujemne procenty nie są ważne dla szerokości komórek. Dozwolone są tylko dodatnie procenty.

### Jak działa funkcja automatycznego dopasowywania rozmiaru?
Funkcja automatycznego dostosowywania rozmiaru dostosowuje szerokość komórki, aby wypełnić całą przestrzeń pozostałą w tabeli po dopasowaniu rozmiaru innych komórek.

### Czy mogę zastosować różne style do komórek o różnych ustawieniach szerokości?
Tak, możesz stosować różne style i formatowanie do komórek bez względu na ustawienia ich szerokości.

### Co się stanie, jeśli całkowita szerokość tabeli będzie mniejsza od sumy szerokości wszystkich komórek?
Tabela automatycznie dostosuje szerokość komórek do dostępnej przestrzeni, co może spowodować zmniejszenie rozmiaru niektórych komórek.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}