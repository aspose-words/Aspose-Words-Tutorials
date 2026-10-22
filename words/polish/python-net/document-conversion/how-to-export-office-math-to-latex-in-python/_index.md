---
category: general
date: 2026-10-07
description: Dowiedz się, jak wyeksportować równania Office Math do LaTeX w Pythonie
  przy użyciu Aspose.Words. Ten przewodnik krok po kroku pokazuje, jak wyeksportować
  równania z Worda do formatu LaTeX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to export office math to latex
- how to export equations from word
- Aspose.Words Python
- LaTeX conversion
- Office Math extraction
language: pl
lastmod: 2026-10-07
og_description: Jak wyeksportować formuły Office Math do LaTeX w Pythonie przy użyciu
  Aspose.Words. Skorzystaj z tego przewodnika, aby szybko i niezawodnie eksportować
  równania z Worda.
og_image_alt: Screenshot of LaTeX equation output generated from a Word document
og_title: Eksport matematyki Office do LaTeXa w Pythonie – kompletny przewodnik
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to export office math to LaTeX in Python with Aspose.Words.
    This step‑by‑step guide shows you how to export equations from Word to LaTeX format.
  headline: How to export office math to LaTeX in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- LaTeX
- Office Math
title: Jak wyeksportować równania Office do LaTeX w Pythonie
url: /pl/python/document-conversion/how-to-export-office-math-to-latex-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak wyeksportować Office Math do LaTeX w Pythonie

Jeśli potrzebujesz wyeksportować Office Math do LaTeX, ten przewodnik pokaże Ci, jak wyeksportować równania z Worda przy użyciu Aspose.Words for Python. Zobaczysz kompletny, gotowy do uruchomienia przykład, który konwertuje plik `.docx` zawierający obiekty Office Math na zwykły kod LaTeX.

Eksportowanie równań jest częstym wymogiem, gdy chcesz ponownie wykorzystać treść z Worda w artykułach naukowych, generatorach stron statycznych lub w dowolnym procesie opartym na LaTeX. Poniższe kroki obejmują wszystko, od instalacji SDK po weryfikację wygenerowanego wyniku.

## Wymagania wstępne

Zanim rozpoczniesz, upewnij się, że masz:

* Python 3.8 lub nowszy zainstalowany na swoim komputerze.  
* Ważną licencję na **Aspose.Words for Python via .NET** (darmowa wersja ewaluacyjna wystarczy do testów).  
* Dostęp do `pip`, aby zainstalować pakiet `aspose-words`.  
* Dokument Word (`.docx`) zawierający przynajmniej jeden obiekt Office Math (równanie). W tym samouczku zakładamy, że plik nosi nazwę `math.docx` i znajduje się w `YOUR_DIRECTORY`.

> **Porada:** Jeśli nie masz pliku licencyjnego, umieść licencję trial (`Aspose.Words.lic`) w tym samym katalogu co Twój skrypt; SDK automatycznie ją wykryje.

## Instalacja Aspose.Words for Python

Pierwszym krokiem jest dodanie biblioteki Aspose.Words do środowiska Pythona.

```bash
pip install aspose-words
```

Uruchomienie tego polecenia instaluje pakiet `aspose.words` oraz wszystkie wymagane komponenty środowiska .NET. Po instalacji możesz zaimportować bibliotekę przy pomocy `import aspose.words as aw`.

## Krok 1: Załaduj dokument Word zawierający równania

Musisz wczytać źródłowy plik `.docx`, zanim będziesz mógł manipulować jego zawartością. Klasa `Document` odczytuje plik do pamięci i daje dostęp do każdego elementu, w tym obiektów Office Math.

```python
import aspose.words as aw

# Replace YOUR_DIRECTORY with the actual path to your files
doc_path = "YOUR_DIRECTORY/math.docx"

# Load the Word document that holds the equations
document = aw.Document(doc_path)
```

Załadowanie dokumentu jest niezbędne, ponieważ proces eksportu działa na reprezentacji w pamięci, a nie bezpośrednio na systemie plików.

## Krok 2: Utwórz opcje zapisu TXT i ustaw tryb eksportu

Aspose.Words zapisuje dokument jako zwykły tekst przy użyciu `TxtSaveOptions`. Domyślnie obiekty Office Math są renderowane jako znaki Unicode, co traci strukturę matematyczną. Ustawienie `office_math_export_mode` na `LATEX` instruuje SDK, aby generował kod LaTeX dla każdego równania.

```python
# Create TXT save options to control the export behavior
txt_options = aw.saving.TxtSaveOptions()

# Export any Office Math (equations) in LaTeX format
txt_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
```

Stała `OfficeMathExportMode.LATEX` jest kluczem, który włącza konwersję do LaTeX. Bez niej wynik zawierałby jedynie przybliżenia tekstowe równań.

## Krok 3: Zapisz dokument jako plik tekstowy przy użyciu skonfigurowanych opcji

Teraz zapisz dokument do pliku `.txt`. SDK zastosuje opcje skonfigurowane w poprzednim kroku, tworząc plik, w którym każde równanie pojawia się jako fragment LaTeX.

```python
# Destination path for the exported LaTeX text file
out_path = "YOUR_DIRECTORY/out.txt"

# Save the document using the TXT options that include LaTeX conversion
document.save(out_path, txt_options)

print(f"LaTeX export completed. File saved to: {out_path}")
```

Po zakończeniu skryptu, `out.txt` zawiera oryginalny tekst z Worda oraz reprezentacje LaTeX każdego obiektu Office Math.

## Zweryfikuj wynik LaTeX

Otwórz `out.txt` w dowolnym edytorze tekstu, aby zobaczyć rezultat. Typowe równanie, takie jak *\(a^2 + b^2 = c^2\)*, pojawi się jako:

```
\[
a^{2}+b^{2}=c^{2}
\]
```

Jeśli wolisz zobaczyć LaTeX bezpośrednio w konsoli, możesz odczytać plik i wydrukować jego zawartość:

```python
with open(out_path, "r", encoding="utf-8") as f:
    latex_content = f.read()
    print("--- LaTeX content start ---")
    print(latex_content)
    print("--- LaTeX content end ---")
```

Wynik powinien odpowiadać równaniom w oryginalnym dokumencie Word, zachowując ułamki, indeksy górne, dolne oraz inne symbole matematyczne.

## Jak wyeksportować równania z Worda – obsługa przypadków brzegowych

Podstawowy przepływ działa w większości dokumentów, ale niektóre scenariusze wymagają dodatkowej uwagi:

| Sytuacja | Zalecane podejście |
|-----------|----------------------|
| **Dokument zawiera mieszane MathML i Office Math** | Użyj `OfficeMathExportMode.MATHML` dla wyjścia MathML lub wykonaj drugi przebieg z `LATEX` po ręcznej konwersji MathML do LaTeX. |
| **Duże dokumenty powodują obciążenie pamięci** | Przetwarzaj dokument w sekcjach: wczytaj sekcję, wyeksportuj, a następnie zwolnij pamięć przed przejściem do kolejnej. |
| **Równania znajdują się w nagłówkach lub stopkach** | Tryb eksportu obsługuje je automatycznie, ale sprawdź, czy otaczający tekst nie zostaje usunięty przez niestandardowe opcje zapisu. |
| **Brak licencji skutkuje znakiem wodnym wersji ewaluacyjnej** | Upewnij się, że plik licencji jest załadowany przed jakąkolwiek operacją `Document`: `aw.License().set_license("Aspose.Words.lic")`. |

Rozwiązanie tych przypadków brzegowych zapewnia, że **jak wyeksportować Office Math do LaTeX** działa niezawodnie w różnych plikach Word.

## Pełny skrypt

Poniżej znajduje się kompletny, samodzielny skrypt Pythona, który możesz skopiować, wkleić i uruchomić. Zawiera obsługę błędów oraz komentarze dla przejrzystości.

```python
import aspose.words as aw
import os
import sys

def export_office_math_to_latex(input_docx: str, output_txt: str) -> None:
    """
    Exports Office Math objects from a Word document to LaTeX format.
    Parameters
    ----------
    input_docx : str
        Path to the source .docx file containing equations.
    output_txt : str
        Path where the LaTeX‑enhanced plain‑text file will be saved.
    """
    if not os.path.isfile(input_docx):
        sys.exit(f"Error: Input file not found – {input_docx}")

    # Load the document
    document = aw.Document(input_docx)

    # Configure TXT save options for LaTeX conversion
    txt_options = aw.saving.TxtSaveOptions()
    txt_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX

    # Save the result
    document.save(output_txt, txt_options)
    print(f"LaTeX export completed. File saved to: {output_txt}")

if __name__ == "__main__":
    # Update these paths to match your environment
    INPUT_PATH = "YOUR_DIRECTORY/math.docx"
    OUTPUT_PATH = "


## Co powinieneś nauczyć się dalej?


Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne, działające przykłady kodu wraz z wyczerpującymi wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Convert docx to markdown – Export Math Equations to LaTeX with Aspose.Words](/words/english/java/document-conversion-and-export/convert-docx-to-markdown-export-math-equations-to-latex-with/)
- [Save docx as txt – Export Equations to LaTeX with Aspose.Words](/words/english/net/programming-with-officemath/save-docx-as-txt-export-equations-to-latex-with-aspose-words/)
- [How to Export LaTeX from Word – Convert DOCX to Markdown](/words/english/python-net/document-conversion/how-to-export-latex-from-word-convert-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}