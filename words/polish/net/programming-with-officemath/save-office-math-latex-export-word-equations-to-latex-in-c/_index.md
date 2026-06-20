---
category: general
date: 2026-04-21
description: Szybko zapisz matematyczny LaTeX w Office przy użyciu Aspose.Words –
  dowiedz się także, jak zapisać zwykły tekst Worda i wyeksportować równania Worda
  do LaTeX w jednym kroku.
draft: false
keywords:
- save office math latex
- save word plain text
- export word equations latex
- convert word math latex
- convert word equations mathml
language: pl
og_description: zapisz matematyczny LaTeX Office natychmiast; dowiedz się, jak eksportować
  równania Word do LaTeX i konwertować matematyczny LaTeX Word przy użyciu Aspose.Words
  w C#.
og_title: Zapisz Office Math LaTeX – Eksportuj równania Worda do LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
title: zapisz office math latex – Eksportuj równania z Worda do LaTeXa w C#
url: /pl/net/programming-with-officemath/save-office-math-latex-export-word-equations-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# save office math latex – Eksportuj równania Word do LaTeX przy użyciu Aspose.Words

Czy kiedykolwiek potrzebowałeś **save office math latex** z pliku `.docx`, ale nie wiedziałeś, od czego zacząć? Nie jesteś sam, a dobra wiadomość jest taka, że rozwiązanie jest dość proste. W tym przewodniku przeprowadzimy Cię krok po kroku przez eksport równań Word do LaTeX (i nawet MathML) przy użyciu Aspose.Words dla .NET, jednocześnie pokazując, jak **save word plain text** wraz z równaniami.

Omówimy wszystko, co możesz się zastanawiać: dlaczego warto wybrać LaTeX zamiast innych formatów, jak skonfigurować `TxtSaveOptions` oraz co zrobić, jeśli potrzebujesz **convert word math latex** do innej reprezentacji. Na końcu będziesz mieć działający fragment kodu, który pobiera dokument Word z obiektami Office Math i zapisuje czysty plik `.txt` zawierający równania LaTeX (lub MathML). Bez zewnętrznych narzędzi, bez ręcznego kopiowania — po prostu czysty kod C#, który możesz wkleić do dowolnego projektu.

## Wymagania wstępne

- **Aspose.Words for .NET** (v23.10 lub nowszy). Pakiet NuGet to `Aspose.Words`.
- Środowisko programistyczne .NET (Visual Studio, Rider lub VS Code z rozszerzeniem C#).
- Plik Word (`.docx`) zawierający przynajmniej jedno równanie utworzone w edytorze Office Math.
- Podstawowa znajomość składni C# — nic skomplikowanego, tylko standardowe instrukcje `using`.

Jeśli już masz zaznaczone te pozycje, świetnie — zanurzmy się.

## Krok 1 – Skonfiguruj opcje **save office math latex**

Pierwszą rzeczą, którą musisz zrobić, jest poinformowanie Aspose.Words, jak ma być renderowana zawartość matematyczna. Klasa `TxtSaveOptions` posiada właściwość `OfficeMathExportMode`, która przyjmuje trzy wartości: `LaTeX`, `MathML` lub `Text`. Dla naszego głównego celu wybierzemy `LaTeX`.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Configure TXT save options to export equations as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // This line makes the library output LaTeX for every Office Math object
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
    // You could also use OfficeMathExportMode.MathML or .Text here
};
```

**Dlaczego to ważne:** Gdy ustawisz `OfficeMathExportMode` na `LaTeX`, każde równanie zostaje przekształcone w surowy kod LaTeX. Ten kod może później zostać skompilowany dowolnym silnikiem LaTeX, zapewniając typografię pixel‑perfect bez konieczności ręcznego przepisywania formuł.

> **Porada:** Jeśli kiedykolwiek będziesz potrzebował **convert word equations mathml**, po prostu zamień wartość wyliczenia na `OfficeMathExportMode.MathML`. Reszta kodu pozostaje bez zmian.

## Krok 2 – Załaduj dokument Word (scenariusz **save word plain text**)

Następnie ładujemy źródłowy plik `.docx`. Ten krok jest identyczny, niezależnie od tego, czy interesuje Cię tylko wyodrębnienie zwykłego tekstu, czy także równania w LaTeX.

```csharp
// Load the document that contains Office Math objects
Document doc = new Document(@"C:\MyDocs\input.docx");

// Optional: verify that the document actually has equations
bool hasMath = doc.GetChildNodes(NodeType.OfficeMath, true).Count > 0;
if (!hasMath)
{
    Console.WriteLine("Warning: No Office Math objects found in the document.");
}
```

**Co się tutaj dzieje?** Konstruktor `Document` wczytuje plik do pamięci. Szybka kontrola przy użyciu `GetChildNodes` pomaga wykryć typowy przypadek brzegowy — próba eksportu LaTeX z pliku, który nie zawiera równań. To małe zabezpieczenie, które później oszczędza Ci zagadkowo pustego wyniku.

## Krok 3 – **save office math latex** do pliku tekstowego

Teraz w końcu zapisujemy plik. Metoda `Save` respektuje wcześniej skonfigurowane `TxtSaveOptions`, więc wynikowy plik `.txt` będzie zawierał zarówno zwykły tekst, jak i fragmenty LaTeX dla każdego równania.

```csharp
// Define the output path
string outputPath = @"C:\MyDocs\Equations.txt";

// Save the document as plain text, with LaTeX equations embedded
doc.Save(outputPath, txtOptions);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

Po otwarciu `Equations.txt` zobaczysz coś w rodzaju:

```
This is a sample paragraph.

\begin{equation}
E = mc^2
\end{equation}

Another paragraph follows.
```

Bloki LaTeX są automatycznie otoczone `\begin{equation}` … `\end{equation}`, co czyni je gotowymi do wstawienia w dowolnym dokumencie LaTeX.

## Krok 4 – Alternatywnie: **convert word equations mathml** zamiast LaTeX

Jeśli Twój dalszy łańcuch narzędzi preferuje MathML (na przykład strona internetowa renderująca równania za pomocą MathJax), po prostu zmień tryb eksportu:

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
doc.Save(@"C:\MyDocs\EquationsMathML.txt", txtOptions);
```

Wyjście będzie teraz zawierało znaczniki MathML w stylu XML, takie jak:

```xml
<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>E</mi>
  <mo>=</mo>
  <mi>m</mi>
  <msup><mi>c</mi><mn>2</mn></msup>
</math>
```

To szybki sposób na **convert word equations mathml** bez pisania własnego parsera.

## Krok 5 – Bonus: **save word plain text** przy zachowaniu oddzielnych równań

Czasami potrzebujesz czystej wersji tekstowej dokumentu *bez* wbudowanego LaTeX lub MathML. Możesz to osiągnąć, przełączając tryb eksportu na `Text` i wykonując drugi zapis:

```csharp
// Export pure plain text (no math markup)
txtOptions.OfficeMathExportMode = OfficeMathExportMode.Text;
doc.Save(@"C:\MyDocs\PlainDocument.txt", txtOptions);
```

Teraz masz trzy pliki obok siebie:

| File                         | Contents                               |
|------------------------------|----------------------------------------|
| `Equations.txt`              | Zwykły tekst **+** równania LaTeX       |
| `EquationsMathML.txt`        | Zwykły tekst **+** równania MathML      |
| `PlainDocument.txt`          | Czysty tekst, równania usunięte        |

## Pełny działający przykład (gotowy do kopiowania i wklejania)

Poniżej znajduje się kompletny program, który możesz skompilować i uruchomić bez zmian. Demonstruje **save office math latex**, **export word equations latex**, **convert word math latex** oraz **save word plain text** — wszystko w jednym schludnym skrypcie.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure TXT save options for LaTeX export
        TxtSaveOptions txtOptions = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };

        // 2️⃣ Load the source Word document
        string inputPath = @"C:\MyDocs\input.docx";
        Document doc = new Document(inputPath);

        // Quick sanity check for equations
        if (doc.GetChildNodes(NodeType.OfficeMath, true).Count == 0)
        {
            Console.WriteLine("No equations found – proceeding with plain‑text export only.");
        }

        // 3️⃣ Save with LaTeX equations embedded
        string latexPath = @"C:\MyDocs\Equations.txt";
        doc.Save(latexPath, txtOptions);
        Console.WriteLine($"LaTeX export saved to {latexPath}");

        // 4️⃣ Switch to MathML and save (optional)
        txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
        string mathmlPath = @"C:\MyDocs\EquationsMathML.txt";
        doc.Save(mathmlPath, txtOptions);
        Console.WriteLine($"MathML export saved to {mathmlPath}");

        // 5️⃣ Finally, pure plain‑text export (no math markup)
        txtOptions.OfficeMathExportMode = OfficeMathExportMode.Text;
        string plainPath = @"C:\MyDocs\PlainDocument.txt";
        doc.Save(plainPath, txtOptions);
        Console.WriteLine($"Plain‑text export saved to {plainPath}");
    }
}
```

**Oczekiwany rezultat:** Po uruchomieniu znajdziesz trzy pliki tekstowe w `C:\MyDocs`. Otwórz `Equations.txt` i zobaczysz bloki LaTeX; `EquationsMathML.txt` będzie zawierał MathML; `PlainDocument.txt` będzie wolny od jakichkolwiek znaczników równań.

## Częste pytania i przypadki brzegowe

- **Co jeśli potrzebuję LaTeX tylko dla podzbioru równań?**  
  Użyj API węzła `OfficeMath`, aby iterować po każdym równaniu, wyeksportować je ręcznie przy pomocy `MathConverter` i zamienić tekst zastępczy tam, gdzie chcesz. To podejście daje precyzyjną kontrolę, ale dodaje kilka dodatkowych linii kodu.

- **Czy to działa z .NET Core / .NET 5+?**  
  Zdecydowanie tak. Aspose.Words jest wieloplatformowy, więc ten sam kod działa na Windows, Linux i macOS, o ile wersja środowiska uruchomieniowego spełnia wymagania biblioteki.

- **Czy mogę zmienić otoczenie LaTeX (`\begin{equation}`) na inne?**  
  Tak. Ustaw `txtOptions.OfficeMathExportMode = OfficeMathExportMode.LaTeX`, a następnie zmodyfikuj `txtOptions.MathExportSettings` (dostępne w nowszych wersjach), aby dostosować delimitery.

- **Obawy o wydajność przy bardzo dużych dokumentach?**  
  Biblioteka strumieniuje wyjście, więc zużycie pamięci pozostaje umiarkowane. Jednak

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}