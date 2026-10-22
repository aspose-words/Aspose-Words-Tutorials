---
category: general
date: 2026-10-13
description: Naucz się zamiany czcionek w dokumencie przy użyciu C#. Ten przewodnik
  pokazuje, jak ustawić kodowanie big5, załadować plik DOCX i zastąpić starsze czcionki
  nowoczesnymi.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- font substitution in document
- big5 encoding
- C# LoadOptions
- legacy font replacement
- document encoding for Chinese
- Docx loading C#
language: pl
lastmod: 2026-10-13
og_description: Zastępowanie czcionek w dokumencie jest niezbędne przy pracy ze starszymi
  chińskimi plikami. Skorzystaj z tego krok po kroku poradnika, aby wczytać plik DOCX
  w kodowaniu big5 i zamienić stare czcionki.
og_image_alt: Screenshot of C# code that performs font substitution in document
og_title: Zastępowanie czcionek w dokumencie przy użyciu C# – kompletny przewodnik
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn font substitution in document using C#. This guide shows how
    to set big5 encoding, load a DOCX, and replace legacy fonts with modern ones.
  headline: How to perform font substitution in document with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Unicode
- Chinese text
title: Jak wykonać zamianę czcionki w dokumencie przy użyciu C#
url: /pl/net/working-with-fonts/how-to-perform-font-substitution-in-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zastępowanie czcionek w dokumencie – kompletny samouczek C#

Jeśli potrzebujesz **font substitution in document**, aby poprawnie renderować starsze chińskie pliki, ten przewodnik pokaże Ci dokładnie, jak to zrobić. Konfigurując odpowiednie kodowanie tekstu i zamieniając przestarzałą czcionkę na nowoczesną, zapewniasz, że końcowy plik DOCX wyświetli się zgodnie z zamierzeniami.

Przetwarzanie dokumentów często się nie udaje, gdy źródło używa starego kodowania, takiego jak **big5**, lub odwołuje się do czcionki, która już nie istnieje w systemie. Ten samouczek przeprowadzi Cię przez ładowanie pliku DOCX z prawidłowym **big5 encoding**, zastosowanie **legacy font replacement** i wygenerowanie czystego wyniku, który działa na dowolnym komputerze z systemem Windows.

Nauczysz się:

* Jak utworzyć obiekt `LoadOptions` z **big5 encoding**.  
* Jak otworzyć plik DOCX przy użyciu **C# LoadOptions**.  
* Jak wykonać **font substitution in document** mapując starą czcionkę na nowoczesny odpowiednik.  
* Obsługa przypadków brzegowych dla brakujących czcionek i wielu rodzin czcionek.

Żadne zewnętrzne narzędzia nie są wymagane poza biblioteką Aspose.Words for .NET, a pełny kod można skopiować do projektu konsolowego i uruchomić od razu.

## Wymagania wstępne

* .NET 6.0 lub nowszy (przykład używa składni konsoli .NET 6).  
* Aspose.Words for .NET – zainstaluj za pomocą `dotnet add package Aspose.Words`.  
* Plik DOCX zapisany z **big5 encoding**, który odwołuje się do starszej czcionki `MingLiU-ExtB`.  
* Podstawowa znajomość C# oraz Visual Studio lub dowolnego wybranego IDE.

## Krok 1: Skonfiguruj projekt i zaimportuj przestrzenie nazw

Utwórz nową aplikację konsolową i dodaj wymagane dyrektywy `using`. Zapewnia to, że kod kompiluje się bez dodatkowych modyfikacji.

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSubstitutionDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The tutorial steps are called from here.
            PerformFontSubstitution();
        }

        static void PerformFontSubstitution()
        {
            // Steps 2‑4 are implemented inside this method.
        }
    }
}
```

> **Wskazówka:** Trzymaj metodę `Main` w minimalnej formie; poprawia to czytelność i ułatwia śledzenie samouczka.

## Krok 2: Zdefiniuj opcje ładowania z prawidłowym kodowaniem tekstu (big5 dla tradycyjnego chińskiego)

Klasa `LoadOptions` informuje Aspose.Words, jak interpretować surowe bajty w pliku źródłowym. Użycie **big5 encoding** jest kluczowe dla tradycyjnych chińskich znaków, które zostały zapisane przy użyciu tej starszej strony kodowej.

```csharp
// Step 2: Define load options with big5 encoding.
LoadOptions loadOptions = new LoadOptions
{
    // Explicitly set the encoding to the traditional Chinese code page.
    Encoding = Encoding.GetEncoding("big5")
};
```

**Dlaczego to ważne:** Jeśli pominiesz kodowanie lub użyjesz domyślnego UTF‑8, znaki mogą pojawić się jako zniekształcone symbole (mojibake). Określenie `big5` zachowuje oryginalne glify przed jakąkolwiek zamianą czcionek.

## Krok 3: Załaduj plik DOCX przy użyciu określonego kodowania

Przekaż instancję `loadOptions` do konstruktora `Document`. To ładuje plik, respektując **document encoding for Chinese**, które zdefiniowałeś wcześniej.

```csharp
// Step 3: Load the DOCX file with the big5 encoding.
string inputPath = @"C:\Docs\big5_doc.docx"; // Update this path to your file location.
Document doc = new Document(inputPath, loadOptions);
```

Jeśli plik nie zostanie znaleziony, program zgłosi `FileNotFoundException`. Upewnij się, że ścieżka jest prawidłowa i że aplikacja ma uprawnienia do odczytu.

## Krok 4: Zamień starszą czcionkę na nowoczesny odpowiednik

Wiele starszych chińskich dokumentów odwołuje się do `MingLiU-ExtB`, która może nie być dostępna w nowszych instalacjach Windows. Mapowanie jej na `Microsoft JhengHei` (szeroko dostępna czcionka Unicode) zapewnia prawidłowe renderowanie.

```csharp
// Step 4: Perform font substitution in document.
doc.FontInfos.Substitution.Add("MingLiU-ExtB", "Microsoft JhengHei");

// Optional: Verify that the substitution succeeded.
foreach (FontInfo fontInfo in doc.FontInfos)
{
    Console.WriteLine($"Original: {fontInfo.FontFamilyName}, Substituted: {fontInfo.SubstitutedFontFamilyName}");
}
```

**Wyjaśnienie:**  
* `FontInfos.Substitution.Add(oldFont, newFont)` rejestruje globalną regułę zamiany. Za każdym razem, gdy Aspose.Words napotka `MingLiU-ExtB`, zamieni ją na `Microsoft JhengHei`.  
* Opcjonalna pętla wypisuje mapowanie, co jest przydatne przy debugowaniu dużych dokumentów z wieloma rodzinami czcionek.

## Krok 5: Zapisz przetworzony dokument

Po zamianie zapisz dokument do nowego pliku. Wyjście wyświetli chiński tekst przy użyciu nowoczesnej czcionki, eliminując ostrzeżenia o brakujących glifach.

```csharp
// Step 5: Save the updated document.
string outputPath = @"C:\Docs\big5_doc_fixed.docx";
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to {outputPath}");
```

Otwórz powstały plik w Microsoft Word lub dowolnym przeglądarce DOCX; powinieneś zobaczyć tradycyjne chińskie znaki renderowane czysto przy użyciu `Microsoft JhengHei`.

## Obsługa przypadków brzegowych i typowych pułapek

| Situation | Recommended approach |
|-----------|----------------------|
| **Czcionka źródłowa nie jest wymieniona w dokumencie** | Użyj `doc.FontInfos.Substitution.Add` z wzorcem wieloznacznym, np. `doc.FontInfos.Substitution.Add("*MingLiU*", "Microsoft JhengHei")`. |
| **Wiele starszych czcionek wymaga zamiany** | Wywołaj `Add` dla każdej pary lub wczytaj słownik zamian z pliku konfiguracyjnego. |
| **Docelowa czcionka jest niedostępna na docelowym komputerze** | Wybierz czcionkę dostarczaną z systemem Windows (np. `Arial Unicode MS`) lub osadź czcionkę używając `doc.FontInfos.EmbeddingMode = FontEmbeddingMode.EmbedAll`. |
| **Błędy kodowania nadal się pojawiają** | Sprawdź, czy plik źródłowy naprawdę używa **big5**; możesz przejrzeć plik w edytorze szesnastkowym lub użyć `File.ReadAllBytes` i porównać wzorce bajtów. |

## Pełny działający przykład

Poniżej znajduje się kompletny, samodzielny program. Skopiuj go do `Program.cs`, dostosuj ścieżki plików i uruchom.

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSubstitutionDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            PerformFontSubstitution();
        }

        static void PerformFontSubstitution()
        {
            // 1️⃣ Define big5 encoding for Traditional Chinese.
            LoadOptions loadOptions = new LoadOptions
            {
                Encoding = Encoding.GetEncoding("big5")
            };

            // 2️⃣ Load the DOCX that uses the legacy font.
            string inputPath = @"C:\Docs\big5_doc.docx";
            Document doc = new Document(inputPath, loadOptions);

            // 3️⃣ Substitute MingLiU-ExtB with Microsoft JhengHei.
            doc.FontInfos.Substitution.Add("MingLiU-ExtB", "Microsoft JhengHei");

            // 4️⃣ (Optional) Log substitution details for verification.
            foreach (FontInfo fontInfo in doc.FontInfos)
            {
                Console.WriteLine($"Original: {fontInfo.FontFamilyName}, Substituted: {fontInfo.SubstitutedFontFamilyName}");
            }

            // 5️⃣ Save the corrected document.
            string outputPath = @"C:\Docs\big5_doc_fixed.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"✅ Font substitution in document completed. Output saved to {outputPath}");
        }
    }
}
```

**Oczekiwany wynik:** Otwierając `big5_doc_fixed.docx` zobaczysz wszystkie tradycyjne chińskie znaki poprawnie renderowane, bez ostrzeżeń o brakujących glifach, ponieważ `MingLiU-ExtB` został zastąpiony przez `Microsoft JhengHei`.

## Zakończenie

Masz teraz niezawodną metodę dla zadań **font substitution in document** przy użyciu C#. Konfigurując **big5 encoding**, ładując DOCX za pomocą `LoadOptions` i mapując starsze czcionki na nowoczesne odpowiedniki, eliminujesz problemy z renderowaniem, które dotykają starsze chińskie pliki.

Od tego momentu możesz:

* Rozszerzyć mapę zamian, aby obejmowała dodatkowe starsze czcionki.  
* Zautomatyzować proces dla partii dokumentów (pętla po katalogu).  
* Połączyć zamianę czcionek z innymi transformacjami dokumentu, takimi jak znak wodny lub konwersja do PDF.

Śmiało eksperymentuj z różnymi czcionkami docelowymi lub osadzaj własne czcionki dla pełnej przenośności. Jeśli napotkasz problemy, wróć do powyższej tabeli przypadków brzegowych lub skonsultuj dokumentację Aspose.Words w celu zaawansowanej obsługi czcionek.

Miłego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Włącz ostrzeżenia o zamianie czcionek w Aspose.Words – Kompletny przewodnik](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Loguj ostrzeżenia o zamianie czcionek – Kompletny przewodnik Aspose.Words](/words/english/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/)
- [Ładuj z kodowaniem w dokumencie Word](/words/english/net/programming-with-loadoptions/load-with-encoding/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}