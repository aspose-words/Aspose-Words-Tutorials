---
category: general
date: 2026-10-16
description: Jak wyeksportować LaTeX z dokumentu Word przy użyciu Aspose.Words. Dowiedz
  się, jak konwertować DOCX na LaTeX, zapisywać Word jako TXT i wyodrębniać równania
  w jednym skrypcie.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to export latex
- convert docx to latex
- export word equations latex
- save word as txt
- extract equations latex
language: pl
lastmod: 2026-10-16
og_description: Jak wyeksportować LaTeX z dokumentu Word przy użyciu Aspose.Words.
  Ten przewodnik pokazuje, jak przekonwertować DOCX na LaTeX, zapisać Word jako TXT
  oraz szybko wyodrębnić równania.
og_image_alt: How to export LaTeX from Word using Aspose.Words
og_title: Jak wyeksportować LaTeX z dokumentów Word – przewodnik krok po kroku
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: How to export LaTeX from a Word document using Aspose.Words. Learn
    to convert DOCX to LaTeX, save Word as TXT, and extract equations in a single
    script.
  headline: How to export LaTeX from Word documents using Aspose.Words
  type: TechArticle
- description: How to export LaTeX from a Word document using Aspose.Words. Learn
    to convert DOCX to LaTeX, save Word as TXT, and extract equations in a single
    script.
  name: How to export LaTeX from Word documents using Aspose.Words
  steps:
  - name: Load the Word document containing equations
    text: '```python import aspose.words as aw'
  - name: Create TXT save options
    text: '```python txt_opts = aw.saving.TxtSaveOptions() ```'
  - name: Set the export mode for Office Math objects to LaTeX
    text: '```python # Export all Office Math objects as LaTeX markup txt_opts.office_math_export_mode
      = aw.saving.OfficeMathExportMode.LATEX ```'
  - name: Save the document as a plain‑text file using the configured options
    text: '```python # The resulting file will contain regular text plus LaTeX for
      each equation doc.save("YOUR_DIRECTORY/out.txt", txt_opts) ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- LaTeX
- DOCX conversion
- Equation extraction
title: Jak wyeksportować LaTeX z dokumentów Word przy użyciu Aspose.Words
url: /pl/python/document-conversion/how-to-export-latex-from-word-documents-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak wyeksportować LaTeX z dokumentów Word przy użyciu Aspose.Words

Eksportowanie LaTeX z dokumentu Word jest powszechną potrzebą, gdy chcesz ponownie wykorzystać treści matematyczne w publikacjach naukowych. Jeśli potrzebujesz konwertować DOCX do LaTeX zachowując obiekty Office Math, ten samouczek przeprowadzi Cię krok po kroku przez dokładne instrukcje przy użyciu Aspose.Words dla Pythona.

Zobaczysz kompletny, gotowy do uruchomienia skrypt, który wczytuje plik *.docx*, konfiguruje opcje zapisu i zapisuje plik tekstowy zawierający znacznik LaTeX dla każdej równania. Poradnik wyjaśnia również, dlaczego każde ustawienie ma znaczenie, jak radzić sobie z przypadkami brzegowymi i czego oczekiwać w wyniku.

![Jak wyeksportować LaTeX z Word przy użyciu Aspose.Words](images/export-latex.png)

## Wymagania wstępne

* Python 3.8 lub nowszy zainstalowany.
* Aktywna licencja na **Aspose.Words for Python via .NET** (bezpłatna wersja próbna działa do testów).
* Pakiet `aspose-words` zainstalowany:

```bash
pip install aspose-words
```

Nie są wymagane dodatkowe biblioteki firm trzecich; Aspose.Words obsługuje konwersję wewnętrznie.

## Jak wyeksportować LaTeX przy użyciu Aspose.Words

Rdzeń rozwiązania składa się z czterech krótkich instrukcji. Każda z nich odpowiada logicznemu krokowi w potoku konwersji.

### Krok 1: Wczytaj dokument Word zawierający równania

```python
import aspose.words as aw

# Replace the path with the location of your source DOCX file
doc = aw.Document("YOUR_DIRECTORY/equations.docx")
```

`aw.Document` parsuje cały pakiet Word, w tym obiekty Office Math. Wczytanie dokumentu najpierw zapewnia, że każde równanie jest dostępne do późniejszego eksportu.

### Krok 2: Utwórz opcje zapisu TXT

```python
txt_opts = aw.saving.TxtSaveOptions()
```

`TxtSaveOptions` informuje Aspose.Words, aby zapisał wyjście jako czysty tekst. Domyślnie silnik usuwałby formatowanie, ale później włączymy eksport LaTeX dla równań.

### Krok 3: Ustaw tryb eksportu obiektów Office Math na LaTeX

```python
# Export all Office Math objects as LaTeX markup
txt_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
```

Właściwość `office_math_export_mode` kontroluje sposób renderowania równań. Ustawienie jej na `LATEX` konwertuje każdy element MathML na jego odpowiednik LaTeX, co jest potrzebne do **export word equations latex**.

### Krok 4: Zapisz dokument jako plik tekstowy używając skonfigurowanych opcji

```python
# The resulting file will contain regular text plus LaTeX for each equation
doc.save("YOUR_DIRECTORY/out.txt", txt_opts)
```

Wywołanie `save` zapisuje plik `.txt`, który miesza normalne akapity z fragmentami LaTeX. Spełnia to wymaganie **save word as txt**, jednocześnie dostarczając wysokiej jakości znaczniki równań.

## Konwertuj DOCX do LaTeX przy minimalnym kodzie

Połączenie czterech kroków daje kompaktowy skrypt, który **convert docx to latex** w zaledwie kilku linijkach:

```python
import aspose.words as aw

def export_docx_to_latex(source_path: str, target_path: str) -> None:
    """
    Loads a DOCX file, exports all Office Math objects as LaTeX,
    and writes the result to a plain‑text file.
    """
    doc = aw.Document(source_path)                     # Load the source
    txt_opts = aw.saving.TxtSaveOptions()              # Prepare TXT options
    txt_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
    doc.save(target_path, txt_opts)                    # Write the output

# Example usage
export_docx_to_latex(
    "YOUR_DIRECTORY/equations.docx",
    "YOUR_DIRECTORY/out.txt"
)
```

Uruchomienie skryptu generuje `out.txt`. Typowy fragment wygląda tak:

```
This is a paragraph introducing the equation.

\[
E = mc^{2}
\]

Another paragraph follows the displayed formula.
```

Fragment LaTeX `\[` … `\]` jest generowany automatycznie dla każdego obiektu Office Math, co sprawia, że plik jest gotowy do włączenia w dokument LaTeX bez dodatkowego przetwarzania.

## Eksport równań Word do LaTeX – obsługa typowych pułapek

Choć podstawowy przepływ działa dla większości dokumentów, możesz napotkać następujące sytuacje:

| Situation | Why it matters | Recommended fix |
|-----------|----------------|-----------------|
| **Równania wewnątrz tabel** | Komórki tabeli są traktowane jako oddzielne akapity; eksportujący nadal działa, ale odstępy mogą się różnić. | Po eksporcie ręcznie sprawdź otaczające środowisko `\begin{tabular}` lub użyj skryptu post‑processingowego, aby otoczyć fragmenty LaTeX. |
| **Mieszany kierunek języka (RTL/LTR)** | Aspose.Words respektuje oryginalny kierunek, co może wpływać na renderowanie LaTeX. | Dodaj `\usepackage{bidi}` w preambule LaTeX, jeśli potrzebujesz wsparcia dla prawej‑do‑lewej. |
| **Duże dokumenty** | Zapis jako czysty tekst strumieniuje cały plik do pamięci. | Użyj `txt_opts.save_format = aw.SaveFormat.TXT` i przetwarzaj plik w częściach, jeśli pamięć jest ograniczona. |
| **Brak licencji** | Wersja próbna wstawia znak wodny do wyniku. | Zastosuj ważną licencję przed wywołaniem `aw.Document`. Przykład: `aw.License().set_license("Aspose.Words.lic")`. |

Rozwiązanie tych przypadków brzegowych zapewnia, że **extract equations latex** działa niezawodnie w różnych plikach źródłowych.

## Zapisz Word jako TXT zachowując równania – alternatywne podejścia

Jeśli wolisz inny format wyjściowy, Aspose.Words obsługuje również:

* **HTML** – `aw.saving.HtmlSaveOptions` z `office_math_export_mode = LATEX`.
* **Markdown** – `aw.saving.MarkdownSaveOptions` z tym samym trybem eksportu.

Obie alternatywy zachowują znacznik LaTeX w całości, dając Ci elastyczność do formatów podobnych do **save word as txt**, które lepiej pasują do narzędzi downstream.

## Wyodrębnij równania LaTeX z dokumentu – szybki skrypt walidacyjny

Po uzyskaniu `out.txt` możesz chcieć wyodrębnić tylko równania LaTeX. Poniższy fragment pokazuje prostą ekstrakcję przy użyciu wyrażeń regularnych:

```python
import re

def extract_latex_equations(txt_path: str) -> list[str]:
    """
    Returns a list of LaTeX equation strings found in a plain‑text file.
    """
    with open(txt_path, "r", encoding="utf-8") as f:
        content = f.read()
    # Matches LaTeX between \[ and \] or $$...$$
    pattern = r"\\\[(.*?)\\\]|\\\$(.*?)\\\$"
    matches = re.findall(pattern, content, re.DOTALL)
    # Flatten the tuple results and strip whitespace
    equations = [eq.strip() for pair in matches for eq in pair if eq]
    return equations

# Example usage
eqs = extract_latex_equations("YOUR_DIRECTORY/out.txt")
print("Found equations:", len(eqs))
for i, eq in enumerate(eqs, 1):
    print(f"{i}: {eq}")
```

Uruchomienie tego skryptu wypisuje każdy wyodrębniony fragment LaTeX, potwierdzając, że **export word equations latex** powiodło się.

## Zakończenie

Teraz wiesz **jak wyeksportować LaTeX** z dokumentu Word przy użyciu Aspose.Words, jak **konwertować DOCX do LaTeX**, jak **zapisać Word jako TXT** zachowując znaczniki równań oraz jak **wyodrębnić równania LaTeX** do dalszego przetwarzania. Pełny przykład demonstruje niezawodną, jednoprzebiegową konwersję, która działa z każdym nowoczesnym plikiem Word zawierającym obiekty Office Math.

Od tego miejsca możesz eksplorować:

* Generowanie pełnej struktury projektu LaTeX (preambuła, `

## Co powinieneś się nauczyć dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Zapisz DOCX jako TXT – Eksportuj równania Word do LaTeX](/words/english/net/programming-with-txtsaveoptions/save-docx-as-txt-export-word-equations-to-latex/)
- [Konwertuj docx do txt – Eksportuj równania Word jako LaTeX](/words/english/net/basic-conversions/convert-docx-to-txt-export-word-equations-as-latex/)
- [Jak konwertować równania w Word do LaTeX – Zapisz jako TXT](/words/english/net/programming-with-officemath/how-to-convert-equations-in-word-to-latex-save-as-txt/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}