---
category: general
date: 2026-06-27
description: Zarejestruj wywołanie zwrotne ostrzeżeń w Aspose.Words, aby przechwytywać
  podstawienia czcionek i problemy z ładowaniem. Poznaj krok po kroku użycie klasy
  LoadOptions w Aspose.Words.
draft: false
keywords:
- register warning callback aspose.words
- aspose.words warning callback
- loadoptions font substitution warning
- document loading warning handling
- aspose.words loadoptions example
language: pl
og_description: Zarejestruj wywołanie zwrotne ostrzeżeń w Aspose.Words, aby monitorować
  podstawienia czcionek i inne ostrzeżenia przy ładowaniu. Przejrzyj ten pełny samouczek,
  aby uzyskać solidną implementację.
og_title: Zarejestruj wywołanie zwrotne ostrzeżeń w Aspose.Words – Kompletny przewodnik
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Register warning callback in Aspose.Words to catch font substitutions
    and loading issues. Learn step‑by‑step usage of LoadOptions with Aspose.Words.
  headline: Register Warning Callback in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Register warning callback in Aspose.Words to catch font substitutions
    and loading issues. Learn step‑by‑step usage of LoadOptions with Aspose.Words.
  name: Register Warning Callback in Aspose.Words – Complete Programming Guide
  steps:
  - name: 4.1 Logging to a File Instead of Console
    text: 'In production you rarely want console spam. Swap `Console.WriteLine` for
      a logger (e.g., `Serilog`, `NLog`) or write to a text file:'
  - name: 4.2 Providing a Custom Font Directory
    text: 'If your environment uses corporate fonts, tell Aspose.Words where to look
      before it falls back to substitution:'
  - name: 4.3 Handling Non‑Font Warnings
    text: 'You can broaden the scope to capture any loading warning:'
  - name: 5.1 Verify with a Document That Has Missing Fonts
    text: Create a small DOCX that references a font not installed on your machine
      (e.g., “Comic Sans MS” on a Linux server). Run the loader; you should see a
      substitution message.
  - name: 5.2 Benchmark Overhead
    text: The callback adds negligible overhead—roughly a few microseconds per warning.
      If you’re loading thousands of documents, you might batch log entries or disable
      the callback for non‑critical runs.
  - name: 5.3 Edge Cases
    text: '- **Multiple Substitutions for the Same Font:** Aspose.Words may fire the
      callback multiple times if the same missing font appears on different pages.
      Deduplicate in your logger if needed. - **Encrypted Documents:** If the DOCX
      is password‑protected, you must also set `loadOptions.Password`. The cal'
  type: HowTo
tags:
- aspose-words
- warning-callback
- csharp
- document-processing
title: Zarejestruj wywołanie zwrotne ostrzeżeń w Aspose.Words – Kompletny przewodnik
  programistyczny
url: /pl/net/programming-with-loadoptions/register-warning-callback-in-aspose-words-complete-programmi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rejestracja callbacku ostrzeżeń w Aspose.Words – Kompletny przewodnik programistyczny

Zastanawiałeś się kiedyś, jak **zarejestrować callback ostrzeżeń w Aspose.Words**, aby dokładnie widzieć, które czcionki są zamieniane podczas ładowania dokumentu? Nie jesteś sam. Wielu programistów napotyka problem, gdy cicha zamiana czcionek psuje układ generowanego pliku PDF lub Word.  

W tym samouczku przeprowadzimy Cię krok po kroku przez praktyczne rozwiązanie, które nie tylko rejestruje callback ostrzeżeń w Aspose.Words, ale także wyjaśnia *dlaczego* warto to zrobić, jak działa callback „pod maską” i z jakimi przypadkami brzegowymi możesz się spotkać. Po zakończeniu będziesz w stanie logować każdą zamianę czcionki, przechwytywać inne ostrzeżenia podczas ładowania i utrzymywać swoją linię przetwarzania dokumentów przejrzystą.

## Czego się nauczysz

- Konfigurowania **LoadOptions**, aby kontrolować zachowanie przy ładowaniu dokumentu.  
- Rejestrowania **callbacku ostrzeżeń**, który wywoływany jest przy zamianie czcionek i innych typach ostrzeżeń.  
- Ładowania pliku DOCX z użyciem skonfigurowanych opcji i interpretacji wyników callbacku.  
- Typowych pułapek (brakujące czcionki, własne foldery czcionek oraz kwestie wydajności).  

**Wymagania wstępne:** Visual Studio 2022 (lub dowolne IDE C#), środowisko uruchomieniowe .NET 6+, oraz aktywna licencja Aspose.Words (bezpłatna wersja próbna wystarczy do eksperymentów). Nie są potrzebne dodatkowe pakiety NuGet poza `Aspose.Words`.

---

![Diagram ilustrujący przepływ rejestracji callbacku ostrzeżeń w Aspose.Words oraz obsługę ostrzeżeń o zamianie czcionek](register-warning-callback-aspose-words.png "diagram rejestracji callbacku ostrzeżeń aspose.words")

## Krok 1: Utwórz LoadOptions – punkt wejścia dla obsługi ostrzeżeń  

Zanim callback będzie mógł się uruchomić, potrzebujesz instancji **LoadOptions**. Traktuj ją jak panel sterowania, który przekazujesz Aspose.Words, mówiąc: „załaduj ten plik, ale daj znać, jeśli coś będzie nie tak”.  

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Loading.Warning;

// Initialize LoadOptions – this object will carry our warning callback.
var loadOptions = new LoadOptions();
```

> **Dlaczego to ważne:** `LoadOptions` pozwala dostosować wszystko, od haseł szyfrowania po katalogi czcionek. Dołączając do tego obiektu callback ostrzeżeń, zamieniasz cichy proces w obserwowalny.

## Krok 2: Zarejestruj callback ostrzeżeń – przechwyć zamiany czcionek  

Teraz przychodzi gwiazda programu: **callback ostrzeżeń**. Zarejestrujemy anonimową metodę (lambda), którą Aspose.Words wywoła przy każdym ostrzeżeniu podczas ładowania. Wewnątrz callbacku filtrujemy `WarningType.FontSubstitution` i wypisujemy przyjazny komunikat.

```csharp
// Register a warning callback to be notified of font substitutions.
loadOptions.WarningCallback = (sender, args) =>
{
    // The callback runs for each loading warning; we care about font substitution warnings.
    if (args.WarningType == WarningType.FontSubstitution)
    {
        // Cast to the more specific warning info type.
        var fontWarning = (FontSubstitutionWarningInfo)args;
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
    // Optional: handle other warning types here (e.g., MissingResource, UnsupportedFeature).
};
```

> **Pro tip:** Jeśli chcesz także logować brakujące obrazy lub nieobsługiwane funkcje, dodaj dodatkowe gałęzie `if` sprawdzające `args.WarningType`. Dzięki temu Twoja **rejestracja callbacku ostrzeżeń w Aspose.Words** stanie się jedynym miejscem obsługi wszystkich diagnostyk ładowania.

## Krok 3: Załaduj dokument przy użyciu skonfigurowanego LoadOptions  

Po podłączeniu callbacku kolejny krok to po prostu załadowanie dokumentu. Przekaż instancję `loadOptions` do konstruktora `Document`. Za każdym razem, gdy Aspose.Words napotka czcionkę, której nie znajdzie, Twój callback się uruchomi i zapisze komunikat w konsoli.

```csharp
// Load the DOCX while the warning callback is active.
var doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

Uruchom program, a zobaczysz wyjście podobne do:

```
Font 'Calibri' was substituted with 'Arial'.
Font 'Times New Roman' was substituted with 'Liberation Serif'.
```

To sedno **rejestracji callbacku ostrzeżeń aspose.words** – trzyetapowy wzorzec, który możesz ponownie wykorzystać w dowolnym projekcie.

## Krok 4: Rozszerzenie callbacku dla scenariuszy produkcyjnych  

### 4.1 Logowanie do pliku zamiast konsoli  

W produkcji rzadko chcesz mieć spam w konsoli. Zamień `Console.WriteLine` na logger (np. `Serilog`, `NLog`) lub zapisz do pliku tekstowego:

```csharp
loadOptions.WarningCallback = (sender, args) =>
{
    if (args.WarningType == WarningType.FontSubstitution)
    {
        var info = (FontSubstitutionWarningInfo)args;
        File.AppendAllText("font-warnings.log",
            $"[WARN] {DateTime.Now}: Font '{info.FontName}' → '{info.SubstitutedFontName}'{Environment.NewLine}");
    }
};
```

### 4.2 Dostarczenie własnego katalogu czcionek  

Jeśli w Twoim środowisku używane są firmowe czcionki, poinformuj Aspose.Words, gdzie ich szukać, zanim przejdzie do zamiany:

```csharp
loadOptions.FontSettings = new FontSettings();
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
```

Teraz callback może wywoływać się *rzadziej*, ponieważ silnik znajdzie właściwe czcionki.

### 4.3 Obsługa ostrzeżeń nie‑dotyczących czcionek  

Możesz poszerzyć zakres, aby przechwytywać dowolne ostrzeżenie podczas ładowania:

```csharp
loadOptions.WarningCallback = (sender, args) =>
{
    switch (args.WarningType)
    {
        case WarningType.FontSubstitution:
            var f = (FontSubstitutionWarningInfo)args;
            Log($"Font '{f.FontName}' → '{f.SubstitutedFontName}'");
            break;
        case WarningType.MissingResource:
            var m = (MissingResourceWarningInfo)args;
            Log($"Missing resource: {m.ResourceType} - {m.ResourceName}");
            break;
        // Add more cases as needed.
    }
};
```

## Krok 5: Testowanie implementacji – czego się spodziewać  

### 5.1 Weryfikacja na dokumencie z brakującymi czcionkami  

Utwórz mały DOCX, który odwołuje się do czcionki niezainstalowanej na Twojej maszynie (np. „Comic Sans MS” na serwerze Linux). Uruchom loader; powinieneś zobaczyć komunikat o zamianie.  

### 5.2 Benchmark obciążenia  

Callback dodaje znikomy narzut – kilka mikrosekund na każde ostrzeżenie. Jeśli ładujesz tysiące dokumentów, możesz grupować wpisy w logu lub wyłączyć callback w niekrytycznych uruchomieniach.

### 5.3 Przypadki brzegowe  

- **Wiele zamian tej samej czcionki:** Aspose.Words może wywołać callback wielokrotnie, jeśli brakująca czcionka występuje na różnych stronach. Zde‑duplikuj wpisy w loggerze, jeśli to konieczne.  
- **Zaszyfrowane dokumenty:** Jeśli DOCX jest chroniony hasłem, musisz także ustawić `loadOptions.Password`. Callback nadal się uruchomi po odszyfrowaniu.  
- **Asynchroniczne ładowanie:** API jest synchroniczne, ale możesz owinąć wywołanie ładowania w `Task.Run` dla przetwarzania w tle; callback pozostaje bezpieczny wątkowo.

## Typowe pułapki i jak ich unikać  

| Pułapka | Dlaczego się pojawia | Rozwiązanie |
|---------|----------------------|-------------|
| **Brak jakiegokolwiek wyjścia** | Callback nie został przypisany *lub* `WarningCallback` został nadpisany później. | Upewnij się, że przypisujesz callback **jednokrotnie** przed ładowaniem i nie zmieniasz `loadOptions` po przypisaniu. |
| **Wyjątek nieprawidłowego rzutowania** | Próba rzutowania ostrzeżenia, które nie jest `FontSubstitutionWarningInfo`. | Zawsze sprawdzaj `args.WarningType` przed rzutowaniem. |
| **Spowolnienie wydajności** | Logowanie synchroniczne do wolnego docelowego I/O. | Używaj asynchronicznych frameworków logujących lub buforuj zapisy. |
| **Brak własnych czcionek** | Katalog czcionek nie został dodany do `FontSettings`. | Dodaj `SetFontsFolder` jak pokazano w Kroku 4.2. |

## Pełny działający przykład – kopiuj‑i‑uruchom  

Poniżej znajduje się samodzielny program, który możesz wkleić do nowego projektu aplikacji konsolowej. Demonstruje cały przepływ od początku do końca.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Loading.Warning;

class Program
{
    static void Main()
    {
        // 1️⃣ Create LoadOptions.
        var loadOptions = new LoadOptions();

        // 2️⃣ Register the warning callback (register warning callback Aspose.Words).
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                var fontInfo = (FontSubstitutionWarningInfo)args;
                Console.WriteLine(
                    $"Font '{fontInfo.FontName}' was substituted with '{fontInfo.SubstitutedFontName}'.");
            }
            // Optional: handle other warnings here.
        };

        // Optional: tell Aspose where to find corporate fonts.
        // loadOptions.FontSettings = new FontSettings();
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", true);

        // 3️⃣ Load the document using the configured options.
        string filePath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        var doc = new Document(filePath, loadOptions);

        // At this point the document is loaded, and any font substitutions have been printed.
        Console.WriteLine("Document loaded successfully.");
    }
}
```

**Oczekiwane wyjście w konsoli** (przy brakujących czcionkach):

```
Font 'Calibri' was substituted with 'Arial'.
Font 'Times New Roman' was substituted with 'Liberation Serif'.
Document loaded successfully.
```

Uruchom program, a zobaczysz dokładnie, które czcionki Aspose.Words zamienił, uzyskując pełną przejrzystość procesu ładowania.

---

## Podsumowanie  

Właśnie omówiliśmy **jak zarejestrować callback ostrzeżeń w Aspose.Words**, dlaczego jest to dobra praktyka w każdym przepływie przetwarzania dokumentów oraz jak rozszerzyć ten wzorzec o logowanie, własne czcionki i szerszą obsługę ostrzeżeń. Dzięki zaledwie trzem liniom kodu zamieniasz czarną skrzynkę ładowania w audytowalny, debugowalny krok – koniec z tajemniczymi zmianami układu.

Co dalej? Spróbuj połączyć ten callback z **Aspose.Words SaveOptions**, aby logować ostrzeżenia zarówno przy ładowaniu, jak i zapisie, lub podłącz callback do API webowego, które przetwarza przesyłane pliki w czasie rzeczywistym. Możesz także zgłębić inne słowa kluczowe, które wprowadziliśmy – takie jak *loadoptions font substitution warning* – aby dopracować wydajność lub zintegrować się z panelem monitoringu.

Masz pytania lub trudny scenariusz? zostaw komentarz, a wspólnie znajdziemy rozwiązanie. Miłego kodowania i niech Twoje PDF‑y zawsze renderują się z właściwymi czcionkami!

## Co warto nauczyć się dalej?


Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletny kod oraz szczegółowe wyjaśnienia, pomagające opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Aspose Words Java Callback Custom Savings](/words/german/java/images-shapes/aspose-words-java-callback-custom-savings/)
- [Aspose Words Java Callback Custom Savings](/words/french/java/images-shapes/aspose-words-java-callback-custom-savings/)
- [Aspose Words Java Callback Custom Savings](/words/spanish/java/images-shapes/aspose-words-java-callback-custom-savings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}