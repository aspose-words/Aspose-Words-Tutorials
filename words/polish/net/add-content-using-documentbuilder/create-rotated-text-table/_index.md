---
title: Utwórz tabelę z obróconym tekstem w dokumencie Word przy użyciu Aspose.Words dla .NET
weight: 110
limit:
description: Naucz się tworzyć tabelę w Wordzie o stałych szerokościach kolumn, obróconym tekście, precyzyjnych wysokościach wierszy i wypełnionych komórkach przy użyciu Aspose.Words dla .NET.
keywords: [Aspose.Words for .NET, rotated text table, fixed column widths, vertical alignment Aspose.Words, set row height Word, populate table cells .NET]
url: /net/add-content-using-documentbuilder/create-rotated-text-table/
date: '2026-09-16'
lastmod: '2026-09-16'
schemas:
- author: Aspose
  dateModified: '2026-09-16'
  description: Naucz się tworzyć tabelę w Wordzie o stałych szerokościach kolumn,
    obróconym tekście, precyzyjnych wysokościach wierszy i wypełnionych komórkach
    przy użyciu Aspose.Words dla .NET.
  headline: Utwórz tabelę z obróconym tekstem w dokumencie Word przy użyciu Aspose.Words
    dla .NET
  type: TechArticle
- description: Naucz się tworzyć tabelę w Wordzie o stałych szerokościach kolumn,
    obróconym tekście, precyzyjnych wysokościach wierszy i wypełnionych komórkach
    przy użyciu Aspose.Words dla .NET.
  name: Utwórz tabelę z obróconym tekstem w dokumencie Word przy użyciu Aspose.Words
    dla .NET
  steps:
  - name: Utwórz nowy obiekt Document oraz DocumentBuilder, które będą używane do
      budowy tabeli.
    text: Utwórz nowy obiekt Document oraz DocumentBuilder, które będą używane do
      budowy tabeli.
  - name: Rozpocznij nową tabelę, wstaw pierwszą komórkę i ustal stałe szerokości
      kolumn, aby nie były automatycznie dopasowywane.
    text: Rozpocznij nową tabelę, wstaw pierwszą komórkę i ustal stałe szerokości
      kolumn, aby nie były automatycznie dopasowywane.
  - name: Wyśrodkuj pionowo zawartość w bieżącej komórce i wpisz tekst pierwszej komórki
      pierwszego wiersza.
    text: Wyśrodkuj pionowo zawartość w bieżącej komórce i wpisz tekst pierwszej komórki
      pierwszego wiersza.
  - name: Wstaw drugą komórkę pierwszego wiersza i wpisz jej tekst.
    text: Wstaw drugą komórkę pierwszego wiersza i wpisz jej tekst.
  - name: Zamknij pierwszy wiersz, finalizując jego układ.
    text: Zamknij pierwszy wiersz, finalizując jego układ.
  - name: Rozpocznij pierwszą komórkę drugiego wiersza, ustaw wysokość wiersza dokładnie
      na 100 punktów, obróć tekst w górę i wpisz tekst komórki.
    text: Rozpocznij pierwszą komórkę drugiego wiersza, ustaw wysokość wiersza dokładnie
      na 100 punktów, obróć tekst w górę i wpisz tekst komórki.
  - name: Wstaw drugą komórkę drugiego wiersza, obróć jej tekst w dół i wpisz tekst
      komórki.
    text: Wstaw drugą komórkę drugiego wiersza, obróć jej tekst w dół i wpisz tekst
      komórki.
  - name: Zamknij drugi wiersz, kończąc drugą linię tabeli.
    text: Zamknij drugi wiersz, kończąc drugą linię tabeli.
  - name: Zakończ budowanie tabeli, zamykając jej strukturę.
    text: Zakończ budowanie tabeli, zamykając jej strukturę.
  - name: Zapisz ukończony dokument do pliku .docx.
    text: Zapisz ukończony dokument do pliku .docx.
  type: HowTo
- questions:
  - answer: Po ustaleniu szerokości kolumn, przypisz szerokość każdej komórce za pomocą
      `builder.CellFormat.Width = <valueInPoints>;` przed wstawieniem kolejnej komórki;
      tabela zachowa te dokładne szerokości.
    question: Jak mogę ustawić konkretne szerokości kolumn po wywołaniu `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`?
  - answer: '`builder.CellFormat.VerticalAlignment` jest ustawieniem na poziomie komórki,
      więc musisz ustawić je ponownie dla komórek w drugim wierszu (np. `builder.CellFormat.VerticalAlignment
      = CellVerticalAlignment.Center;`) przed zapisaniem ich zawartości.'
    question: Dlaczego wyrównanie pionowe wpływa tylko na pierwszy wiersz, a nie na
      drugi wiersz?
  - answer: Tak — ustaw `builder.RowFormat.Height` oraz `builder.RowFormat.HeightRule
      = HeightRule.Exactly` przed każdym wywołaniem `builder.EndRow();`; kolejny wiersz
      może mieć inną wartość wysokości.
    question: Czy mogę nadać każdemu wierszowi inną dokładną wysokość i jeśli tak,
      to jak?
  - answer: Zresetuj orientację, przypisując `builder.CellFormat.Orientation = TextOrientation.Horizontal;`
      przed zapisaniem do kolejnej komórki.
    question: Jak przywrócić domyślną orientację tekstu po użyciu `TextOrientation.Upward`
      lub `Downward`?
  type: FAQPage
images:
- /net/add-content-using-documentbuilder/create-rotated-text-table/og-image.png
og_title: Utwórz tabelę z obróconym tekstem w Wordzie przy użyciu Aspose.Words
og_description: Krok po kroku kod do budowy tabeli o stałej szerokości z pionowo obróconym tekstem i dokładnymi wysokościami wierszy.
og_image_alt: Zrzut ekranu przedstawiający dokument Word z tabelą, która ma stałe szerokości kolumn, obrócony tekst w komórkach i określone wysokości wierszy, utworzoną przy użyciu Aspose.Words dla .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz tabelę z obróconym tekstem w dokumencie Word przy użyciu Aspose.Words dla .NET
Ten tutorial pokazuje, jak wygenerować dokument Word i dodać tabelę, której kolumny mają stałe szerokości, wiersze dokładne wysokości, a tekst w komórkach jest obrócony pionowo. Nauczysz się ustawiać wyrównanie pionowe, stosować orientację tekstu, wypełniać każdą komórkę treścią i ostatecznie zapisywać dokument — wszystko przy użyciu Aspose.Words dla .NET.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/create-rotated-text-table" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Jak mogę ustawić konkretne szerokości kolumn po wywołaniu `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`?**  
A: Po ustaleniu szerokości kolumn, przypisz szerokość każdej komórce za pomocą `builder.CellFormat.Width = <valueInPoints>;` przed wstawieniem kolejnej komórki; tabela zachowa te dokładne szerokości.

**Q: Dlaczego wyrównanie pionowe wpływa tylko na pierwszy wiersz, a nie na drugi wiersz?**  
A: `builder.CellFormat.VerticalAlignment` jest ustawieniem na poziomie komórki, więc musisz ustawić je ponownie dla komórek w drugim wierszu (np. `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`) przed zapisaniem ich zawartości.

**Q: Czy mogę nadać każdemu wierszowi inną dokładną wysokość i jeśli tak, to jak?**  
A: Tak — ustaw `builder.RowFormat.Height` oraz `builder.RowFormat.HeightRule = HeightRule.Exactly` przed każdym wywołaniem `builder.EndRow();`; kolejny wiersz może mieć inną wartość wysokości.

**Q: Jak przywrócić domyślną orientację tekstu po użyciu `TextOrientation.Upward` lub `Downward`?**  
A: Zresetuj orientację, przypisując `builder.CellFormat.Orientation = TextOrientation.Horizontal;` przed zapisaniem do kolejnej komórki.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}