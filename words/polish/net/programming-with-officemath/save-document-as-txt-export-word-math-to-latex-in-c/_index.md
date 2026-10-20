---
category: general
date: 2026-04-24
description: Zapisz dokument jako txt i konwertuj Word na LaTeX za pomocą Aspose.Words.
  Dowiedz się, jak szybko eksportować równania matematyczne z Worda do LaTeX.
draft: false
keywords:
- save document as txt
- convert word to latex
- convert word equations to latex
- export word math latex
language: pl
og_description: Zapisz dokument jako txt i konwertuj równania Worda na LaTeX przy
  użyciu C#. Kompletny przewodnik krok po kroku z kodem.
og_title: Zapisz dokument jako TXT – Eksportuj matematykę Worda do LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
title: Zapisz dokument jako TXT – Eksportuj matematykę Word do LaTeX w C#
url: /pl/net/programming-with-officemath/save-document-as-txt-export-word-math-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zapisz dokument jako TXT – Eksportowanie równań Word do LaTeX w C#

Kiedykolwiek potrzebowałeś **save document as txt** zachowując przy tym swoje eleganckie równania? Nie jesteś jedyny. Wbudowana w Word funkcja „Save as plain text” usuwa Office Math, pozostawiając nieczytelny bełkot. Co gdybyś mógł zachować te równania, ale w czystym LaTeXie?  

W tym tutorialu przejdziemy krok po kroku przez dokładne instrukcje, jak **convert Word to LaTeX**‑ready text przy użyciu Aspose.Words for .NET. Na końcu będziesz mieć plik `.txt`, w którym każde równanie jest przedstawione jako prawidłowy znacznik LaTeX, gotowy do wstawienia do artykułu lub pliku markdown. Bez zewnętrznych konwerterów, bez ręcznego kopiowania‑wklejania — tylko kilka linii C#.

## Czego się nauczysz

- Jak wczytać plik `.docx` przy użyciu Aspose.Words.
- Konfigurowanie `TxtSaveOptions`, aby Office Math był eksportowany jako LaTeX.
- Zapisanie wyniku do pliku tekstowego, który możesz otworzyć w dowolnym edytorze.
- Obsługa przypadków brzegowych dla równań w linii i wyświetlanych, oraz szybka wskazówka dotycząca przetwarzania wsadowego wielu dokumentów.

### Wymagania wstępne

- .NET 6.0 lub nowszy (kod działa również z .NET Framework 4.6+).
- Pakiet NuGet Aspose.Words dla .NET (`Install-Package Aspose.Words`).
- Dokument Word zawierający przynajmniej jedno równanie (obiekt Office Math).

---

## Krok 1: Zainstaluj Aspose.Words i skonfiguruj projekt

Najpierw dodaj bibliotekę do swojego projektu. Otwórz terminal w folderze rozwiązania i uruchom:

```bash
dotnet add package Aspose.Words
```

> **Wskazówka:** Jeśli używasz Visual Studio, interfejs NuGet Package Manager działa równie dobrze — wyszukaj „Aspose.Words” i kliknij Zainstaluj.

Teraz utwórz nową aplikację konsolową (lub wstaw kod do istniejącej). Dyrektywy `using`, które będą potrzebne, to:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Dzięki nim klasy `Document` i typ `TxtSaveOptions` będą dostępne.

## Krok 2: Wczytaj dokument źródłowy

Musimy wskazać Aspose.Words na plik Word zawierający równania. Zastąp `YOUR_DIRECTORY/input.docx` rzeczywistą ścieżką na swoim komputerze.

```csharp
// Load the source .docx file
Document doc = new Document(@"C:\MyDocs\input.docx");
```

> **Dlaczego to ważne:** Wczytanie dokumentu daje Aspose.Words pełny dostęp do wewnętrznych obiektów Office Math, które w przeciwnym razie są niewidoczne dla prostego eksportera tekstu.

## Krok 3: Skonfiguruj TxtSaveOptions do eksportu LaTeX

Magia dzieje się w obiekcie `TxtSaveOptions`. Ustawiając `OfficeMathExportMode` na `LaTeX`, każde równanie zostaje przekształcone do swojego odpowiednika w LaTeX.

```csharp
// Configure save options to export Office Math as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // Export all Office Math objects as LaTeX code
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Optional: keep line breaks similar to the original layout
    PreserveTableLayout = true
};
```

> **A co jeśli potrzebujesz MathML?** Zmień `OfficeMathExportMode` na `MathML`. To samo API obsługuje kilka formatów wyjściowych.

## Krok 4: Zapisz dokument jako zwykły tekst

Teraz zapisujemy plik. Powstały `Math.txt` będzie zawierał zwykły tekst oraz fragmenty LaTeX dla każdego równania.

```csharp
// Save the document as a .txt file with LaTeX equations
doc.Save(@"C:\MyDocs\Math.txt", txtOptions);
Console.WriteLine("Document saved as txt with LaTeX equations.");
```

Uruchomienie programu generuje plik, który wygląda mniej więcej tak:

```
This is a simple paragraph.

Here is an inline equation: $E = mc^2$

And a displayed equation:
\[
\int_{0}^{\infty} e^{-x} \, dx = 1
\]
```

Zauważ, że równanie w linii używa `$…$`, a równanie wyświetlane jest otoczone `\[` i `\]`. To standardowa konwencja LaTeX, a Aspose.Words robi to automatycznie.

## Krok 5: Zweryfikuj wynik (opcjonalnie)

Jeśli chcesz podwójnie sprawdzić poprawność LaTeX, możesz wprowadzić plik `.txt` do kompilatora LaTeX, takiego jak `pdflatex`, lub do internetowego renderera, np. Overleaf. Tekst powinien się kompilować bez błędów, a równania pojawią się dokładnie tak, jak w Wordzie.

```bash
pdflatex Math.txt
```

Jeśli pojawi się komunikat „Undefined control sequence”, upewnij się, że potrzebne pakiety LaTeX (np. `amsmath`) są dołączone w preambule, gdy wstawiasz tekst do większego dokumentu LaTeX.

## Obsługa typowych wariantów

### Konwertowanie wielu plików w folderze

```csharp
string[] files = Directory.GetFiles(@"C:\MyDocs\", "*.docx");
foreach (var file in files)
{
    Document d = new Document(file);
    d.Save(Path.ChangeExtension(file, ".txt"), txtOptions);
}
Console.WriteLine("Batch conversion complete.");
```

### Obsługa równań w linii vs. wyświetlanych

Aspose.Words automatycznie wykrywa typ równania na podstawie jego układu w Wordzie. Jeśli musisz wymusić konkretny styl, możesz przetworzyć wynik:

```csharp
string txt = File.ReadAllText(@"C:\MyDocs\Math.txt");
txt = txt.Replace("$", "\\(").Replace("$", "\\)"); // forces inline math delimiters
File.WriteAllText(@"C:\MyDocs\Math_fixed.txt", txt);
```

### Eksport do innych formatów

Jeśli LaTeX nie jest twoim celem, po prostu zmień tryb eksportu:

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML; // for MathML
```

Lub użyj `HtmlSaveOptions`, jeśli wolisz MathML osadzone w HTML.

## Pełny działający przykład

Poniżej znajduje się kompletny, gotowy do uruchomienia program. Skopiuj i wklej go do `Program.cs` w projekcie konsolowym .NET.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToLatexTxt
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the source document
            Document doc = new Document(@"C:\MyDocs\input.docx");

            // 2️⃣ Set up save options to export Office Math as LaTeX
            TxtSaveOptions saveOptions = new TxtSaveOptions
            {
                OfficeMathExportMode = OfficeMathExportMode.LaTeX,
                PreserveTableLayout = true
            };

            // 3️⃣ Save as plain‑text with LaTeX equations
            string outputPath = @"C:\MyDocs\Math.txt";
            doc.Save(outputPath, saveOptions);

            Console.WriteLine($"✅ Saved document as txt at: {outputPath}");
            Console.WriteLine("Open the file to see LaTeX‑formatted equations.");
        }
    }
}
```

Uruchom program (`dotnet run`), otwórz `Math.txt` i zobaczysz zawartość Worda z zachowanymi równaniami LaTeX.

## Najczęściej zadawane pytania

**Q: Czy to działa ze starszymi plikami .doc?**  
A: Tak — Aspose.Words może otworzyć starsze pliki `.doc`, ale skomplikowane równania mogą być przechowywane jako obrazy. W takim przypadku eksporter użyje komentarza zastępczego.

**Q: Co jeśli równanie zawiera niestandardowe symbole?**  
A: Aspose.Words mapuje większość symboli Office Math na standardowe polecenia LaTeX. W przypadku naprawdę niestandardowych symboli może być konieczna ręczna edycja wygenerowanego LaTeX.

**Q: Czy wynik jest kodowany w UTF‑8?**  
A: Domyślnie `TxtSaveOptions` zapisuje w UTF‑8, co jest bezpieczne dla większości języków i symboli.

## Podsumowanie

Teraz wiesz, jak **save document as txt** zachowując każde równanie jako czysty znacznik LaTeX. To podejście pozwala **convert Word to LaTeX** bez narzędzi zewnętrznych i skaluje się od pojedynczego pliku do całych folderów. Następnie możesz zbadać **convert word equations to LaTeX** w przetwarzaniu wsadowym lub zagłębić się w **export word math latex** dla potoków HTML lub Markdown.

Śmiało eksperymentuj — zamień `OfficeMathExportMode` na MathML, dostosuj obsługę podziałów linii lub włącz ten fragment kodu do większego procesu generowania dokumentów. Szczęśliwego kodowania i niech twoje równania zawsze renderują się perfekcyjnie!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}