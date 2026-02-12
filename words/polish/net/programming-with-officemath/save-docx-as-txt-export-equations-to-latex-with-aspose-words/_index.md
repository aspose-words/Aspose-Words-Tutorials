---
category: general
date: 2026-02-12
description: Zapisz plik docx jako txt i konwertuj równania do LaTeX w jednym kroku.
  Dowiedz się, jak eksportować matematykę z Worda przy użyciu C# i Aspose.Words.
draft: false
keywords:
- save docx as txt
- convert docx to txt
- how to export math
- convert equations to latex
- how to export equations
language: pl
og_description: Zapisz plik docx jako txt i wyeksportuj równania do LaTeX przy użyciu
  C#. Przewodnik krok po kroku dla Aspose.Words.
og_title: Zapisz docx jako txt – Eksportuj równania Word do LaTeX
tags:
- Aspose.Words
- C#
- Document Conversion
title: Zapisz docx jako txt – Eksportuj równania do LaTeX przy użyciu Aspose.Words
url: /pl/net/programming-with-officemath/save-docx-as-txt-export-equations-to-latex-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zapisz docx jako txt – Eksportuj równania Word do LaTeX przy użyciu Aspose.Words

Kiedykolwiek potrzebowałeś **zapisz docx jako txt**, ale napotykałeś problem, gdy Twój dokument zawiera Office Math? Nie jesteś sam. Większość programistów zakłada, że eksport do zwykłego tekstu po prostu usunie wszystko, jednak równania znikają, pozostawiając nieczytelny bałagan.  

Dobre wieści? Z Aspose.Words możesz **zapisz docx jako txt** *oraz* poinstruować bibliotekę, aby renderowała każde równanie jako kod LaTeX. W tym samouczku przeprowadzimy Cię przez cały proces, od wczytania pliku `.docx` po wygenerowanie czystego `.txt`, który zawiera całą Twoją matematykę w formacie gotowym do publikacji naukowej.

Po zakończeniu będziesz wiedział **jak eksportować matematykę** z Worda, dlaczego możesz chcieć **konwertować równania do LaTeX**, oraz jak **konwertować docx na txt** bez utraty ważnych treści.

## Czego będziesz potrzebować

- **Aspose.Words for .NET** (wersja 23.8 lub nowsza). Pakiet NuGet to `Aspose.Words`.
- Środowisko programistyczne .NET (Visual Studio, Rider lub VS Code z rozszerzeniem C#).
- Przykładowy dokument Word (`input.docx`) zawierający przynajmniej jeden obiekt Office Math.
- Podstawowa znajomość C# i aplikacji konsolowych.

Nie są wymagane żadne dodatkowe narzędzia firm trzecich; wszystko działa w czystym C#.

## Krok 1 – Wczytaj dokument źródłowy

Pierwszą rzeczą, którą robimy, jest odczytanie pliku Word do obiektu `Document`. Ten obiekt reprezentuje cały pakiet Word w pamięci, dając dostęp do akapitów, tabel i ukrytych węzłów Office Math.

```csharp
using Aspose.Words;

// Step 1: Load the source document
Document doc = new Document(@"C:\MyFiles\input.docx");
```

> **Dlaczego to ważne:** Wczytanie dokumentu w ten sposób pozwala Aspose.Words zachować oryginalną strukturę, więc gdy później eksportujemy do TXT, biblioteka nadal wie, gdzie znajduje się każde równanie.

## Krok 2 – Powiedz Aspose.Words, jak obsługiwać Office Math

Domyślnie `TxtSaveOptions` po prostu zapisuje zwykły tekst i pomija wszelką matematykę. Zmieniamy to zachowanie, ustawiając `OfficeMathExportMode` na `LaTeX`. Dzięki temu silnik zastępuje każdy obiekt Office Math jego reprezentacją w LaTeX.

```csharp
// Step 2: Configure TXT save options to export Office Math as LaTeX
TxtSaveOptions txtSaveOptions = new TxtSaveOptions
{
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
};
```

> **Pro tip:** Jeśli kiedykolwiek potrzebujesz równań w formacie MathML, zamień `OfficeMathExportMode.LaTeX` na `OfficeMathExportMode.MathML`. To samo API działa dla obu formatów.

## Krok 3 – Zapisz dokument jako plik tekstowy

Teraz wykonujemy rzeczywistą konwersję. Metoda `Save` otrzymuje ścieżkę docelową oraz opcje, które właśnie skonfigurowaliśmy.

```csharp
// Step 3: Save the document as a plain‑text file using the configured options
doc.Save(@"C:\MyFiles\Equations.txt", txtSaveOptions);
```

Gdy kod zostanie uruchomiony, plik `Equations.txt` będzie zawierał:

```
This is a sample paragraph.
Here is an inline equation: $E = mc^2$
And a displayed equation:
\[
\int_{a}^{b} f(x)\,dx = F(b) - F(a)
\]
```

> **Co widzisz:** Każdy obiekt Office Math jest teraz otoczony delimiterami LaTeX (`$…$` dla inline, `\[`…`\]` dla display). Otaczający tekst pozostaje dokładnie taki, jaki był w oryginalnym DOCX.

## Pełny, gotowy do uruchomienia przykład

Poniżej znajduje się minimalna aplikacja konsolowa, którą możesz skopiować i wkleić do nowego projektu C# i od razu uruchomić.

```csharp
using System;
using Aspose.Words;

namespace DocxToTxtWithLatex
{
    class Program
    {
        static void Main(string[] args)
        {
            // Define input and output paths
            string inputPath = @"C:\MyFiles\input.docx";
            string outputPath = @"C:\MyFiles\Equations.txt";

            // Load the Word document
            Document doc = new Document(inputPath);

            // Configure save options – export equations as LaTeX
            TxtSaveOptions saveOptions = new TxtSaveOptions
            {
                OfficeMathExportMode = OfficeMathExportMode.LaTeX
            };

            // Perform the conversion
            doc.Save(outputPath, saveOptions);

            Console.WriteLine($"Successfully saved TXT with LaTeX equations to: {outputPath}");
        }
    }
}
```

### Oczekiwany wynik

Otwórz `Equations.txt` w dowolnym edytorze tekstu. Powinieneś zobaczyć oryginalne akapity, a każde równanie pojawi się jako kod LaTeX. Ten plik jest teraz gotowy do przekazania do kompilatora LaTeX, procesora markdown lub dowolnego systemu rozumiejącego składnię LaTeX.

## Często zadawane pytania i przypadki brzegowe

### 1. *Co jeśli mój dokument nie zawiera równań?*  
Konwersja nadal działa; Aspose.Words po prostu zapisze treść tekstową. Nie zostaną dodane dodatkowe delimitery LaTeX.

### 2. *Czy mogę dostosować delimitery?*  
Tak. `TxtSaveOptions` udostępnia właściwości `InlineMathDelimiter` i `DisplayMathDelimiter`. Na przykład:

```csharp
saveOptions.InlineMathDelimiter = @"\(";
saveOptions.DisplayMathDelimiter = @"\[\[";
```

### 3. *Co z dużymi dokumentami (setki MB)?*  
Aspose.Words strumieniuje plik wewnętrznie, więc zużycie pamięci pozostaje umiarkowane. Jednak możesz chcieć zwiększyć ustawienie `MemoryUsage`, jeśli napotkasz `OutOfMemoryException`.

### 4. *Czy wyjście LaTeX jest gwarantowanie kompilowalne?*  
Aspose.Words stosuje mapowanie Office Math na LaTeX zdefiniowane przez Microsoft. Większość typowych konstrukcji (ułamki, całki, sumy, macierze) kompiluje się bez problemu. Rzadkie symbole mogą wymagać ręcznej korekty.

### 5. *Czy mogę także eksportować do innych formatów tekstowych?*  
Oczywiście. Ten sam schemat działa dla `HtmlSaveOptions`, `MarkdownSaveOptions` itp. Wystarczy zamienić `TxtSaveOptions` na odpowiednią klasę.

## Wskazówki dla płynnej pracy

- **Zweryfikuj wynik**: Uruchom szybki `pdflatex` na małym fragmencie, aby upewnić się, że wygenerowany LaTeX nie brakuje potrzebnych pakietów.
- **Przetwarzanie wsadowe**: Owiń powyższy kod w pętlę `foreach`, aby konwertować wiele plików DOCX jednocześnie.
- **Logowanie**: Użyj `Console.WriteLine` lub właściwego loggera, aby przechwycić wszelkie ostrzeżenia Aspose.Words dotyczące nieobsługiwanych funkcji matematycznych.
- **Sprawdzenie wersji**: Enum `OfficeMathExportMode` został wprowadzony w Aspose.Words 22.9. Jeśli używasz starszej wersji, zaktualizuj ją przez NuGet.

## Podsumowanie

Pokazaliśmy, jak **zapisz docx jako txt** zachowując każde równanie w formacie LaTeX. Trójstopniowe podejście — wczytaj, skonfiguruj, zapisz — obejmuje cały przepływ pracy, a pełny przykład pozwala wstawić kod do dowolnego projektu .NET od razu.  

Jeśli chcesz **konwertować docx na txt** do dalszego przetwarzania, lub po prostu potrzebujesz **jak eksportować równania** do pracy naukowej, ta metoda jest zarówno niezawodna, jak i łatwa do rozszerzenia. Następnie możesz zbadać **jak eksportować matematykę** do innych języków znaczników (MathML, ASCIIMath) lub połączyć wyjście TXT z generatorami stron statycznych dla dokumentacji.

Miłego kodowania i niech Twoje konwersje będą wolne od błędów!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}