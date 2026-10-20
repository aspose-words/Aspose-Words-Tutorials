---
category: general
date: 2026-08-04
description: Zmień separator przypisu w C# przy użyciu Aspose.Words – dowiedz się,
  jak edytować separator przypisu i zmienić separator przypisu końcowego w dokumentach
  Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote separator
- edit footnote separator
- how to change footnote separator
- change endnote separator
language: pl
lastmod: 2026-08-04
og_description: Zmień separator przypisu w C# przy użyciu Aspose.Words. Ten przewodnik
  pokazuje, jak edytować separator przypisu, dostosować separator przypisu końcowego
  i zapisać zaktualizowany dokument.
og_image_alt: Screenshot showing the changed footnote separator in a Word document
og_title: Zmień separator przypisów w C# – kompletny przewodnik Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Change footnote separator in C# using Aspose.Words – learn how to edit
    footnote separator and change endnote separator in Word documents.
  headline: Change footnote separator in C# using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
- Document processing
title: Zmień separator przypisu w C# przy użyciu Aspose.Words
url: /pl/net/working-with-footnote-and-endnote/change-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zmiana separatora przypisu w C# przy użyciu Aspose.Words

Jeśli potrzebujesz **zmienić separator przypisu** w dokumencie Word, ten tutorial przeprowadzi Cię krok po kroku przez dokładne instrukcje przy użyciu Aspose.Words dla .NET. Niezależnie od tego, czy chcesz zamienić domyślną linię na symbol, czy zastosować inny styl do separatorów przypisów końcowych, poniższy kod obejmuje pełny przepływ pracy.  
Nauczysz się także, jak **edytować separator przypisu** oraz powiązaną operację **zmiany separatora przypisu końcowego**, aby ten sam dokument miał spójny styl zarówno dla przypisów, jak i przypisów końcowych. Nie są wymagane żadne zewnętrzne narzędzia — wystarczy kilka linii C#.

## Co osiągniesz

* Załaduj istniejący plik *.docx* zawierający przypisy i przypisy końcowe.  
* Uzyskaj dostęp do węzłów separatorów dla przypisów, kontynuacji przypisów i przypisów końcowych.  
* Zamień znak separatora (na przykład zmień domyślną linię na gwiazdkę).  
* Zapisz zmodyfikowany dokument, nie tracąc żadnej innej zawartości.  

Tutorial zakłada, że masz podstawową znajomość C# i zainstalowany pakiet NuGet **Aspose.Words** (wersja 24.9 lub nowsza).

---

## Wymagania wstępne

| Requirement | Reason |
|-------------|--------|
| .NET 6.0+ lub .NET Framework 4.7.2+ | Wymagane środowisko uruchomieniowe dla Aspose.Words |
| Biblioteka Aspose.Words for .NET | Dostarcza API `Document` i `FootnoteOptions` |
| Plik Word wejściowy (`input.docx`) z co najmniej jednym przypisem lub przypisem końcowym | Demonstracja zmiany separatora |

Możesz dodać Aspose.Words do swojego projektu przy użyciu następującego polecenia CLI:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

---

## Krok 1: Załaduj dokument zawierający przypisy

Pierwszą operacją jest odczytanie pliku źródłowego do obiektu `Document`. Obiekt ten reprezentuje cały plik Word w pamięci i daje dostęp do wszystkich jego węzłów.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Load the .docx file that contains footnotes and endnotes.
Document document = new Document(@"C:\Docs\input.docx");
```

**Dlaczego to ważne:** Ładowanie dokumentu jest punktem wyjścia dla każdej manipulacji. Jeśli plik nie zostanie znaleziony, Aspose.Words rzuca `FileNotFoundException`, więc przed kontynuacją upewnij się, że ścieżka jest prawidłowa.

---

## Krok 2: Uzyskaj dostęp do węzłów separatorów przypisu i przypisu końcowego

`Document.FootnoteOptions` udostępnia trzy węzły separatorów:

* `Separator` – linia pojawiająca się po zbiorze przypisów na pierwszej stronie.  
* `ContinuationSeparator` – linia używana, gdy przypisy kontynuują się na kolejnej stronie.  
* `EndnoteSeparator` – linia oddzielająca główny tekst od listy przypisów końcowych.

Pobierasz te węzły jako ogólne obiekty `Node`, a następnie rzutujesz je na `Run`, aby zmodyfikować tekst.

```csharp
// Retrieve the three separator nodes.
Node footnoteSeparator = document.FootnoteOptions.Separator;
Node footnoteContinuation = document.FootnoteOptions.ContinuationSeparator;
Node endnoteSeparator = document.FootnoteOptions.EndnoteSeparator;
```

**Dlaczego to ważne:** Te węzły są jedynymi miejscami, w których znajduje się wizualny znak separatora. Zmiana jakiegokolwiek innego węzła (np. zwykłego akapitu) nie wpłynie na formatowanie przypisu.

---

## Krok 3: Zmień znak separatora przypisu

Najczęstszym wymaganiem jest zamiana domyślnej linii na symbol, taki jak gwiazdka (`*`). Ponieważ separator jest przechowywany jako `Run`, możesz bezpiecznie zmodyfikować jego właściwość `Text`.

```csharp
// Change the primary footnote separator to an asterisk.
if (footnoteSeparator is Run footnoteRun)
{
    footnoteRun.Text = "*";
}

// Optionally, change the continuation separator as well.
if (footnoteContinuation is Run continuationRun)
{
    continuationRun.Text = "*";
}
```

**Dlaczego to ważne:** Bezpośrednia edycja `Run.Text` aktualizuje wizualną reprezentację w końcowym dokumencie bez wpływu na inną zawartość przypisu. Ten sam wzorzec można użyć do zastosowania dowolnego ciągu, w tym znaków Unicode.

---

## Krok 4: Zmień separator przypisu końcowego (opcjonalnie)

Jeśli potrzebujesz również **zmienić separator przypisu końcowego**, proces jest analogiczny do zmiany separatora przypisu. Zamień tekst `endnoteSeparator` na wybrany znak.

```csharp
// Change the endnote separator to a dash.
if (endnoteSeparator is Run endnoteRun)
{
    endnoteRun.Text = "-";
}
```

**Dlaczego to ważne:** Przypisy końcowe często mają inny styl niż przypisy. Udostępnienie osobnego separatora pozwala zachować spójność wizualną z wytycznymi projektowymi dokumentu.

---

## Krok 5: Zapisz zmodyfikowany dokument

Po wszystkich modyfikacjach zapisz zmiany przy użyciu `Document.Save`. Możesz nadpisać oryginalny plik lub zapisać go w nowej lokalizacji.

```csharp
// Save the updated document.
document.Save(@"C:\Docs\ModifiedSeparators.docx");
```

**Dlaczego to ważne:** `Save` zapisuje reprezentację w pamięci na dysk, zachowując wszystkie inne elementy (style, obrazy, tabele) niezmienione.

---

## Pełny, gotowy do uruchomienia przykład

Łącząc wszystkie elementy, oto samodzielna aplikacja konsolowa, która demonstruje cały przepływ pracy:

```csharp
using System;
using Aspose.Words;

namespace FootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document.
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Access separator nodes.
            Node footnoteSep = doc.FootnoteOptions.Separator;
            Node footnoteCont = doc.FootnoteOptions.ContinuationSeparator;
            Node endnoteSep = doc.FootnoteOptions.EndnoteSeparator;

            // 3️⃣ Change footnote separator to an asterisk.
            if (footnoteSep is Run footnoteRun)
                footnoteRun.Text = "*";

            // Optional: also change the continuation separator.
            if (footnoteCont is Run contRun)
                contRun.Text = "*";

            // 4️⃣ Change endnote separator to a dash.
            if (endnoteSep is Run endnoteRun)
                endnoteRun.Text = "-";

            // 5️⃣ Save the result.
            string outputPath = @"C:\Docs\ModifiedSeparators.docx";
            doc.Save(outputPath);

            Console.WriteLine("Document saved to " + outputPath);
        }
    }
}
```

**Oczekiwany rezultat:** Otwórz *ModifiedSeparators.docx* w Microsoft Word. Linia separatora przypisu na dole pierwszej strony przypisów będzie teraz pojedynczą gwiazdką (`*`). Jeśli dokument zawiera przypisy końcowe, linia oddzielająca główny tekst od listy przypisów końcowych pojawi się jako myślnik (`-`). Cała pozostała zawartość (tekst, obrazy, tabele) pozostanie niezmieniona.

---

## Częste pytania i obsługa przypadków brzegowych

| Question | Answer |
|----------|--------|
| **Co jeśli dokument nie zawiera przypisów?** | `FootnoteOptions.Separator` nadal zwraca węzeł `Run`, ale jego tekst może być pusty. Kod bezpiecznie sprawdza typ węzła przed jego modyfikacją. |
| **Czy mogę użyć ciągu wieloznakowego (np. "***")?** | Tak. Właściwość `Run.Text` akceptuje dowolny ciąg, w tym znaki Unicode. |
| **Czy zmiana separatora wpłynie na istniejącą numerację przypisów?** | Nie. Separator jest niezależny od schematu numeracji. |
| **Czy muszę zwolnić obiekt `Document`?** | `Document` implementuje `IDisposable` pośrednio poprzez `Node`. W krótkotrwałej aplikacji konsolowej jest to opcjonalne, ale w usługach działających długo warto użyć bloku `using`. |
| **Jak to działa w .NET Core vs .NET Framework?** | API jest identyczne we wszystkich środowiskach; liczy się tylko wersja docelowego frameworka (musi być obsługiwana przez pakiet Aspose.Words). |

**Wskazówka:** Jeśli potrzebujesz zastosować różne separatory w różnych sekcjach, możesz iterować po `doc.GetChildNodes(NodeType.Footnote, true)` i indywidualnie dostosowywać właściwość `Separator` każdego przypisu. To bardziej zaawansowane, ale przydatne w złożonych dokumentach.

---

## Podsumowanie

Teraz wiesz, jak **zmienić separator przypisu** i **zmienić separator przypisu końcowego** w pliku Word przy użyciu Aspose.Words dla C#. Poradnik obejmował ładowanie dokumentu, dostęp do odpowiednich węzłów separatorów, modyfikację ich tekstu oraz zapis wyniku — wszystko w jednej, samodzielnej aplikacji.  
Od tego momentu możesz zgłębiać powiązane tematy, takie jak **edycja stylu separatora przypisu**, dostosowywanie numeracji przypisów lub stosowanie formatowania warunkowego w zależności od układu strony. Ten sam wzorzec (pobranie węzła, rzutowanie na `Run`, modyfikacja `Text`) działa w wielu innych scenariuszach przetwarzania dokumentów Word.  
Miłego kodowania i zachęcamy do eksperymentowania z różnymi symbolami lub nawet osadzania obrazów jako separatorów, aby uzyskać naprawdę unikalny układ dokumentu!

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletny działający kod z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Przetwarzanie tekstu z przypisami i przypisami końcowymi](/words/english/net/working-with-footnote-and-endnote/)
- [Pobierz separator stylu akapitu w dokumencie Word](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Wstaw separator stylu dokumentu w Word](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}