---
category: general
date: 2026-06-24
description: Jak używać IWarningCallback do wykrywania brakujących czcionek w dokumentach
  Aspose.Words. Poznaj pełny, działający przykład oraz najlepsze praktyki.
draft: false
keywords:
- how to use iwarningcallback
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- missing font detection in .docx
language: pl
og_description: Jak używać IWarningCallback do wykrywania brakujących czcionek w Aspose.Words.
  Skorzystaj z przewodnika krok po kroku, aby uzyskać kompletną, gotową do produkcji
  rozwiązanie.
og_title: Jak używać IWarningCallback – wykrywać brakujące czcionki
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to use IWarningCallback to detect missing fonts in Aspose.Words
    documents. Learn a full, runnable example and best practices.
  headline: How to Use IWarningCallback – Detect Missing Fonts with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Processing
title: Jak używać IWarningCallback – wykrywanie brakujących czcionek w Aspose.Words
url: /pl/net/working-with-fonts/how-to-use-iwarningcallback-detect-missing-fonts-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak używać IWarningCallback – Wykrywanie brakujących czcionek w Aspose.Words

Używanie **IWarningCallback** jest niezbędne, gdy pracujesz z Aspose.Words i musisz **wykrywać brakujące czcionki** w pliku DOCX. W tym przewodniku przeprowadzimy Cię przez kompletny przykład, który możesz skopiować i wkleić, pokazując dokładnie, jak używać IWarningCallback do przechwytywania ostrzeżeń o podstawianiu czcionek, dlaczego jest to ważne i co zrobić po ich przechwyceniu.

Jeśli kiedykolwiek otworzyłeś dokument i zobaczyłeś zniekształcony tekst, ponieważ niestandardowa czcionka nie była zainstalowana, znasz tę frustrację. Po zakończeniu tego samouczka będziesz mieć niezawodny sposób na wykrywanie tych problemów programowo, ich logowanie lub nawet automatyczne zastosowanie czcionki zapasowej.

## Czego się nauczysz

- Cel **IWarningCallback** i kiedy go używać.  
- Jak zaimplementować własny zbieracz ostrzeżeń, który izoluje zdarzenia **detect missing fonts**.  
- Podłączenie zbieracza do **LoadOptions**, aby każde ładowanie dokumentu było monitorowane.  
- Weryfikacja wyniku i obsługa przypadków brzegowych (wiele brakujących czcionek, ciche ostrzeżenia itp.).  

### Wymagania wstępne

- .NET 6.0 lub nowszy (kod działa również na .NET Framework 4.6+).  
- Aspose.Words for .NET zainstalowany przez NuGet (`Install-Package Aspose.Words`).  
- Plik DOCX, który odwołuje się do czcionki nieobecnej w systemie (np. `DocumentWithMissingFont.docx`).  

Nie są wymagane dodatkowe biblioteki — wszystko znajduje się w obrębie Aspose.Words.

---

## Jak używać IWarningCallback do wykrywania brakujących czcionek w Aspose.Words

Poniżej znajduje się **pełny, działający program**. Skopiuj go do nowego projektu konsolowego, dostosuj ścieżkę do pliku i uruchom. Zobaczysz wyjście w konsoli dla każdego ostrzeżenia o brakującej czcionce.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 1: Create a warning collector that implements IWarningCallback.
    // This collector will be invoked each time Aspose.Words raises a warning.
    class FontWarningCollector : IWarningCallback
    {
        // The Warning method receives a WarningInfo object.
        // We filter for FontSubstitution warnings because those indicate missing fonts.
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // Print the warning to the console – you could also log to a file or database.
                Console.WriteLine($"[Missing Font] {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2: Configure LoadOptions to use our custom collector.
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // Step 3: Load the document with the specified options.
            // Any font that cannot be resolved triggers the warning collector above.
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

            try
            {
                Document doc = new Document(docPath, loadOptions);
                Console.WriteLine("Document loaded successfully.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error loading document: {ex.Message}");
            }

            // Keep the console window open when debugging.
            Console.WriteLine("Press any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Oczekiwany wynik

Jeśli `DocumentWithMissingFont.docx` odwołuje się do czcionki o nazwie *„MyFancyFont”*, której nie ma zainstalowanej, zobaczysz coś podobnego:

```
[Missing Font] Font substitution: The font 'MyFancyFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
Press any key to exit...
```

Każda linia poprzedzona **[Missing Font]** jest generowana przez naszą implementację **IWarningCallback**, co dowodzi, że skutecznie **detect missing fonts**.

---

## Krok 1: Implementacja interfejsu IWarningCallback

Dlaczego potrzebujemy własnej klasy? Aspose.Words generuje **ostrzeżenia** z różnych powodów — problemy z formatem pliku, przestarzałe funkcje oraz, co najważniejsze dla nas, podstawianie czcionek. Implementując `IWarningCallback`, otrzymujemy hak, który odbiera każde ostrzeżenie w momencie jego wystąpienia. Filtrowanie pod kątem `WarningType.FontSubstitution` izoluje konkretny scenariusz, w którym czcionka jest brakująca.

**Pro tip:** Jeśli potrzebujesz przechwycić *wszystkie* ostrzeżenia w celach diagnostycznych, po prostu usuń sprawdzenie `if` i loguj każdy `info.Type`.

## Krok 2: Podłączenie callbacku do LoadOptions

`LoadOptions` jest bramą, która informuje Aspose.Words, jak traktować wczytywany dokument. Ustawienie `WarningCallback` na instancję naszego zbieracza zapewnia, że callback jest aktywny przez cały proces ładowania. Ten sam obiekt `LoadOptions` możesz ponownie używać dla wielu dokumentów, co jest przydatne w potokach przetwarzania wsadowego.

**Common question:** *Co się stanie, jeśli załaduję dokument bez podania LoadOptions?*  
Odpowiedź: Aspose.Words nadal będzie generować ostrzeżenia wewnętrznie, ale bez callbacku zostaną one cicho odrzucone i stracisz możliwość **detect missing fonts**.

## Krok 3: Ładowanie dokumentu i przechwytywanie ostrzeżeń o brakujących czcionkach

Konstruktor `Document`, który przyjmuje ścieżkę do pliku i `LoadOptions`, wykonuje ciężką pracę. Podczas parsowania pliku każde brakujące źródło czcionki wywołuje naszą metodę `FontWarningCollector.Warning`. Wyjście w konsoli potwierdza, że mechanizm działa.

**Edge case:** Jeden dokument może odwoływać się do kilku nieobecnych czcionek. Callback uruchamia się raz dla każdej brakującej czcionki, więc zobaczysz wiele linii — idealne do stworzenia kompleksowego raportu.

## Dlaczego używać IWarningCallback zamiast ręcznych sprawdzeń czcionek?

Można by ręcznie przeszukiwać właściwości `Run.Font` po załadowaniu dokumentu, ale wymagałoby to pomyślnego załadowania dokumentu najpierw — co nie powiedzie się, jeśli czcionka jest całkowicie niedostępna. System ostrzeżeń działa **przed** jakąkolwiek podmianą, dając prawdziwy obraz tego, co jest brakujące.

Dodatkowo, callback działa **jako część potoku ładowania**, co oznacza, że możesz przerwać proces wcześnie, podmienić czcionki w locie lub logować szczegółowe diagnostyki bez dodatkowych przejść po drzewie dokumentu.

## Obsługa wielu brakujących czcionek w sposób elegancki

Jeśli spodziewasz się wielu brakujących czcionek, rozważ zebranie ich w kolekcję:

```csharp
class AggregatingFontCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}
```

Po załadowaniu możesz iterować po `MissingFonts` i na przykład zapisać je do pliku CSV dla zespołu projektowego.

## Bonus: Logowanie ostrzeżeń do pliku

Wyjście w konsoli jest wystarczające dla demonstracji, ale kod produkcyjny zazwyczaj loguje do trwałego magazynu. Zastąp wywołanie `Console.WriteLine` czymś w stylu:

```csharp
File.AppendAllText("font-warnings.log", $"{DateTime.Now}: {info.Description}{Environment.NewLine}");
```

Teraz masz ścieżkę audytu, którą można przeglądać później, spełniając wymogi zgodności.

---

## Zakończenie

Omówiliśmy **jak używać IWarningCallback** do **detect missing fonts** w Aspose.Words, od implementacji callbacku po podłączenie go do `LoadOptions` i obsługę wynikających ostrzeżeń. To podejście daje Ci wgląd w czasie rzeczywistym w problemy związane z czcionkami, umożliwiając logowanie, podmianę lub powiadamianie użytkowników przed renderowaniem dokumentu.

Kolejne kroki, które możesz rozważyć:

- **Fallback fonts:** programowo przypisać domyślną czcionkę, gdy następuje podstawienie.  
- **Batch processing:** iterować po folderze dokumentów, ponownie używając tego samego `AggregatingFontCollector`.  
- **User feedback:** wyświetlać ostrzeżenia o brakujących czcionkach w interfejsie użytkownika zamiast w konsoli.

Wypróbuj to w swoim projekcie — koniec z tajemniczymi zniekształconymi tekstami, tylko przejrzyste, praktyczne diagnostyki. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne, działające przykłady kodu z krok po kroku wyjaśnieniami, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak załadować DOCX i wykrywać brakujące czcionki – Kompletny przewodnik C#](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [Jak wykrywać czcionki w Aspose.Words – Obsługa ostrzeżeń i ustawień](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Jak używać LoadOptions w Aspose.Words – Kompletny przewodnik](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}