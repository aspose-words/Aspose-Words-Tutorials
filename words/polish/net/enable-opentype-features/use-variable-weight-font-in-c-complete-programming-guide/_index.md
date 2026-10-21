---
category: general
date: 2026-06-02
description: Dowiedz się, jak używać czcionki o zmiennej grubości w C# i programowo
  ustawiać wagę czcionki, jednocześnie zmieniając kod rozciągania czcionki dla dynamicznej
  typografii.
draft: false
keywords:
- use variable weight font
- set font weight programmatically
- change font stretch code
- variable font Aspose.Words
- dynamic typography C#
language: pl
og_description: Użyj czcionki o zmiennej grubości w C#, aby programowo ustawiać wagę
  czcionki i zmieniać kod rozciągnięcia czcionki, umożliwiając dynamiczną typografię
  w dokumentach.
og_title: Użyj czcionki o zmiennej grubości w C# – pełny przewodnik
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  headline: Use Variable Weight Font in C# – Complete Programming Guide
  type: TechArticle
- description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  name: Use Variable Weight Font in C# – Complete Programming Guide
  steps:
  - name: What if the font doesn’t appear at all?
    text: '- **Missing FontSettings**: Double‑check that `doc.FontSettings = fontSettings;`
      is executed **before** any text is added. - **Incorrect family name**: Use `fontSettings.GetFonts()`
      to list all discovered families; copy the exact string. - **Unsupported weight/stretch**:
      Some variable fonts only sup'
  - name: Can I change the weight after the document is saved?
    text: Yes. The `Run` object is mutable, so you can adjust `FontWeight` or `FontStretch`
      at any point before the final `Save`. If you need to toggle weights dynamically
      (e.g., based on user interaction), consider generating separate runs for each
      state.
  - name: Does this work with DOCX output?
    text: Absolutely. The variable‑weight metadata is stored in the underlying OpenXML,
      and modern versions of Word can interpret it. However, older Word versions may
      ignore the stretch setting.
  type: HowTo
tags:
- C#
- Aspose.Words
- Variable Fonts
title: Użyj czcionki o zmiennej grubości w C# – Kompletny przewodnik programistyczny
url: /pl/net/enable-opentype-features/use-variable-weight-font-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Używanie czcionki o zmiennej grubości w C# – Kompletny przewodnik programistyczny

Czy kiedykolwiek potrzebowałeś **używać czcionki o zmiennej grubości** w projekcie .NET, ale nie byłeś pewien, jak sprawić, by waga i rozciągnięcie reagowały na dane wejściowe użytkownika? Nie jesteś sam. W wielu scenariuszach UI lub raportowania chcesz, aby tekst dostosowywał się — może lekki nagłówek, który staje się pogrubiony po najechaniu, lub akapit, który rozszerza swoją szerokość dla podkreślenia. Dobre wieści są takie, że z Aspose.Words możesz **ustawiać wagę czcionki programowo** i nawet **zmieniać kod rozciągnięcia czcionki** w locie.

W tym samouczku przeprowadzimy Cię przez praktyczny przykład, który pokazuje dokładnie, jak załadować czcionkę o zmiennej grubości, zastosować niestandardową wagę i dostroić ustawienie rozciągnięcia — wszystko przy użyciu przejrzystego kodu C#, który możesz skopiować i wkleić. Po zakończeniu będziesz mieć działającą aplikację konsolową, która generuje PDF prezentujący efekt.

---

## Czego będziesz potrzebować

- **Aspose.Words for .NET** (v23.12 lub nowszy). Biblioteka zawiera pełne wsparcie dla czcionek o zmiennej grubości.
- Folder zawierający przynajmniej jedną czcionkę o zmiennej grubości, np. *RobotoFlex‑Variable.ttf*. Możesz ją pobrać z Google Fonts.
- .NET 6 SDK (lub dowolna nowsza wersja .NET) oraz wybrane przez Ciebie środowisko IDE.
- Podstawowa znajomość C# — nic skomplikowanego, tylko kilka linijek kodu.

To wszystko. Nie potrzebujesz dodatkowych pakietów NuGet poza Aspose.Words i nie ma żadnych skomplikowanych plików konfiguracyjnych.

---

![Przykład użycia czcionki o zmiennej grubości](https://example.com/variable-weight-sample.png "Demonstracja użycia czcionki o zmiennej grubości")

*Alt text: zrzut ekranu pokazujący użycie czcionki o zmiennej grubości w wygenerowanym dokumencie PDF.*

---

## Krok 1: Skonfiguruj FontSettings i wskaż folder z czcionkami  

Najpierw — Aspose.Words musi wiedzieć, gdzie znajdują się Twoje czcionki o zmiennej grubości. Robisz to, tworząc obiekt `FontSettings` i dołączając `FolderFontSource`. Flaga `true` mówi silnikowi, aby przeszukiwał także podfoldery, co jest przydatne, gdy trzymasz wiele rodzin czcionek razem.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create FontSettings and point to the folder containing variable‑weight fonts
var fontSettings = new FontSettings();
fontSettings.SetFontSources(new FontSourceBase[]
{
    new FolderFontSource(@"C:\MyProject\Fonts\", true) // Adjust path to your own directory
});
```

**Dlaczego to ważne:** Bez zarejestrowania folderu Aspose.Words przechodzi do czcionek systemowych i zignoruje dane o zmiennej grubości osadzone w Twoim własnym pliku czcionki. Ten krok jest fundamentem dla wszystkiego, co nastąpi.

---

## Krok 2: Dołącz FontSettings do dokumentu  

Teraz tworzymy nowy `Document` (lub ładujemy istniejący) i wskazujemy mu użycie `FontSettings`, które właśnie przygotowaliśmy. To powiązanie udostępnia dane o zmiennej grubości każdemu `Run`, który dodamy później.

```csharp
// Step 2: Attach the FontSettings to the document
var doc = new Document();          // Starts with a blank document
doc.FontSettings = fontSettings;   // Connects our custom fonts
```

Jeśli już masz szablon — powiedzmy plik Word z miejscami na wstawki — możesz zamienić `new Document()` na `new Document("Template.docx")`. Te same `FontSettings` zostaną zastosowane.

---

## Krok 3: Dodaj Run tekstu, który będzie używał czcionki o zmiennej grubości  

**Run** to najmniejsza jednostka formatowania tekstu w Aspose.Words. Utworzymy go, wstawimy do nowego akapitu, a później zmienimy jego atrybuty czcionki.

```csharp
// Step 3: Add a run of text that will use the variable‑weight font
var paragraph = new Paragraph(doc);
doc.FirstSection.Body.AppendChild(paragraph);

var run = new Run(doc, "Variable‑weight text demo");
paragraph.AppendChild(run);
```

Na tym etapie tekst zostanie wyrenderowany domyślną czcionką (zwykle Times New Roman). Magia nastąpi, gdy przypiszemy rodzinę czcionki o zmiennej grubości.

---

## Krok 4: Wybierz rodzinę czcionki o zmiennej grubości  

Tutaj faktycznie **używamy czcionki o zmiennej grubości**. Ustaw `Font.Name` na dokładną nazwę rodziny zdefiniowaną wewnątrz pliku czcionki zmiennej. Dla Roboto Flex nazwą jest `"Roboto Flex"`.

```csharp
// Step 4: Choose the variable‑weight font family
run.Font.Name = "Roboto Flex";
```

Jeśli nie jesteś pewien nazwy rodziny, otwórz plik `.ttf` w przeglądarce czcionek lub użyj metody `fontSettings.GetFonts()`, aby wyliczyć dostępne rodziny.

---

## Krok 5: Ustaw wagę i rozciągnięcie czcionki programowo  

Teraz sedno samouczka: **ustawiamy wagę czcionki programowo** i **zmieniamy kod rozciągnięcia czcionki**. Obie właściwości przyjmują wartości całkowite, które mapują specyfikację OpenType.

```csharp
// Step 5: Specify the desired weight and stretch for the run
run.Font.FontWeight = 300;   // Light weight (300)
run.Font.FontStretch = 125; // Expanded stretch (125% of normal width)
```

- **FontWeight**: 100 (Thin) → 900 (Black). Wybierz dowolną wartość obsługiwaną przez czcionkę zmienną.
- **FontStretch**: 50 (Ultra‑Condensed) → 200 (Ultra‑Expanded). Domyślnie 100 (Normal).

> **Pro tip:** Nie każda czcionka zmienna udostępnia pełny zakres. Jeśli ustawisz wartość, której nie obsługuje, silnik przytnie ją do najbliższej dostępnej wagi lub rozciągnięcia.

---

## Krok 6: Zapisz dokument i zweryfikuj wynik  

Na koniec zapisz dokument jako PDF (lub DOCX) i otwórz go, aby zobaczyć efekt. PDF to świetny format do wizualnej weryfikacji, ponieważ renderowanie jest spójne na wszystkich platformach.

```csharp
// Step 6: Save the document as PDF
doc.Save(@"C:\MyProject\Output\VariableWeightDemo.pdf", SaveFormat.Pdf);
```

Gdy otworzysz *VariableWeightDemo.pdf*, powinieneś zobaczyć frazę „Variable‑weight text demo” wyrenderowaną w lekkiej, nieco rozszerzonej wersji Roboto Flex. Zmień `FontWeight` na `700` i `FontStretch` na `80`, a następnie uruchom ponownie — zobaczysz, jak tekst staje się pogrubiony i bardziej skondensowany.

---

## Często zadawane pytania i przypadki brzegowe  

### Co zrobić, gdy czcionka w ogóle się nie pojawia?  

- **Missing FontSettings**: Upewnij się, że `doc.FontSettings = fontSettings;` jest wykonane **przed** dodaniem jakiegokolwiek tekstu.
- **Incorrect family name**: Użyj `fontSettings.GetFonts()`, aby wyświetlić wszystkie wykryte rodziny; skopiuj dokładny ciąg znaków.
- **Unsupported weight/stretch**: Niektóre czcionki zmienne obsługują tylko podzbiór zakresu 100‑900 wagi. Użyj `run.Font.FontWeight = 400;` jako bezpiecznego fallbacku.

### Czy mogę zmienić wagę po zapisaniu dokumentu?  

Tak. Obiekt `Run` jest mutowalny, więc możesz dostosować `FontWeight` lub `FontStretch` w dowolnym momencie przed ostatecznym wywołaniem `Save`. Jeśli potrzebujesz dynamicznie przełączać wagi (np. w zależności od interakcji użytkownika), rozważ generowanie osobnych `Run` dla każdego stanu.

### Czy to działa przy wyjściu DOCX?  

Zdecydowanie. Metadane o zmiennej grubości są przechowywane w podstawowym OpenXML, a nowoczesne wersje Worda potrafią je interpretować. Starsze wersje Worda mogą jednak zignorować ustawienie rozciągnięcia.

---

## Pełny działający przykład  

Poniżej znajduje się kompletny program konsolowy, który możesz od razu skompilować i uruchomić. Zawiera wszystkie niezbędne dyrektywy `using`, obsługę błędów i komentarze.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace VariableWeightDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure FontSettings
            var fontSettings = new FontSettings();
            fontSettings.SetFontSources(new FontSourceBase[]
            {
                // 👉 Point to your local folder containing the variable‑weight font files
                new FolderFontSource(@"C:\MyProject\Fonts\", true)
            });

            // 2️⃣ Create the document and attach FontSettings
            var doc = new Document();
            doc.FontSettings = fontSettings;

            // 3️⃣ Build a paragraph with a run of text
            var paragraph = new Paragraph(doc);
            doc.FirstSection.Body.AppendChild(paragraph);
            var run = new Run(doc, "Variable‑weight text demo");
            paragraph.AppendChild(run);

            // 4️⃣ Apply the variable‑weight font family
            run.Font.Name = "Roboto Flex";

            // 5️⃣ Set weight (300 = Light) and stretch (125 = Expanded)
            run.Font.FontWeight = 300;   // set font weight programmatically
            run.Font.FontStretch = 125; // change font stretch code

            // 6️⃣ Save as PDF to verify the rendering
            string outputPath = @"C:\MyProject\Output\VariableWeightDemo.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}");
            Console.WriteLine("Open the PDF to see the light, expanded Roboto Flex text.");
        }
    }
}
```

**Oczekiwany wynik:** Konsola wypisuje ścieżkę zapisu, a wygenerowany PDF pokazuje tekst w lekkim, rozszerzonym stylu — dokładnie tak, jak skonfigurowaliśmy.

---

## Podsumowanie  

Omówiliśmy, jak **używać czcionki o zmiennej grubości** w C# z Aspose.Words, pokazaliśmy, jak **ustawiać wagę czcionki programowo**, oraz przedstawiliśmy dokładny **kod zmiany rozciągnięcia czcionki**, potrzebny do rozszerzania lub zwężania glifów. Kroki są proste: skonfiguruj `FontSettings`, podłącz je do `Document`, utwórz `Run`, wybierz rodzinę czcionki o zmiennej grubości i na koniec dostrój `FontWeight` oraz `FontStretch`.

---

## Co dalej?  

- **Dynamiczna integracja UI**: Podłącz tę samą logikę do aplikacji WinForms lub WPF, aby użytkownicy mogli wybierać wagę/rozciągnięcie za pomocą suwaków.
- **Wiele runów**: Połącz kilka `Run` o różnych wagach w jednym akapicie, aby uzyskać bogate hierarchie typograficzne.
- **Zaawansowane osie**: Niektóre czcionki zmienne udostępniają dodatkowe osie (np. pochylenie, rozmiar optyczny). Użyj `run.Font.FontStyle` lub zbadaj `FontVariationSettings` dla jeszcze precyzyjniejszej kontroli.
- **Wskazówki wydajnościowe**: Cache'uj instancję `FontSettings` przy przetwarzaniu wielu dokumentów, aby uniknąć wielokrotnego skanowania folderów.

Śmiało eksperymentuj — zamień *Roboto Flex* na *Inter Variable* lub dowolną inną czcionkę OpenType zmienną i zobacz, jak Twoje dokumenty zyskują nowy poziom elastyczności wizualnej. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu oraz krok‑po‑kroku wyjaśnienia, pomagające opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Użyj czcionki z docelowej maszyny](/words/english/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Użyj czcionki z docelowej maszyny](/words/german/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Użyj czcionki z docelowej maszyny](/words/french/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}