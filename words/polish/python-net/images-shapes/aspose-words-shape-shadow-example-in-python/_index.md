---
category: general
date: 2026-11-18
description: Przykład cienia kształtu w Aspose.Words pokazuje, jak dodać cień do kształtu
  w Wordzie przy użyciu Pythona. Postępuj zgodnie z tym przewodnikiem krok po kroku,
  aby zmodyfikować i zapisać dokument.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words shape shadow example
- python shape shadow
- Aspose.Words for Python
- modify shape shadow
- document manipulation Aspose
language: pl
lastmod: 2026-11-18
og_description: Przykład cienia kształtu w Aspose.Words demonstruje dodawanie cienia
  do kształtu w Wordzie przy użyciu Pythona. Poznaj pełny kod, dlaczego każdy krok
  ma znaczenie i jak go dostosować.
og_image_alt: Aspose.Words shape shadow example – Word document displaying a shape
  with a shadow applied using Python
og_title: Przykład cienia kształtu Aspose.Words – przewodnik Pythona
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Aspose.Words shape shadow example shows how to add a shadow to a Word
    shape using Python. Follow this step‑by‑step guide to modify and save the document.
  headline: Aspose.Words shape shadow example in Python
  type: TechArticle
- description: Aspose.Words shape shadow example shows how to add a shadow to a Word
    shape using Python. Follow this step‑by‑step guide to modify and save the document.
  name: Aspose.Words shape shadow example in Python
  steps:
  - name: Expected outcome
    text: Open `output.docx` in Microsoft Word. The first shape you added should now
      display a soft shadow that is offset by 2 pt horizontally and vertically, with
      a blur radius of 5 pt. All other content remains unchanged.
  - name: 'Alternative: Find a shape by name'
    text: 'If your document contains several shapes, you might prefer to locate a
      specific one:'
  - name: Working with multiple shapes
    text: 'If you need to apply the same shadow to every shape, iterate over the node
      collection:'
  - name: Applying a shadow to a specific shape type
    text: You can filter by `ShapeType` (e.g., `aw.ShapeType.IMAGE`). This is useful
      when you only want to affect pictures, not AutoShapes.
  - name: Handling documents without shapes
    text: The script already raises a clear `ValueError` if no shape is found. In
      production code you might log the issue and continue processing other files.
  - name: Compatibility notes
    text: '* The code works with **Aspose.Words for Python via .NET** version 23.10
      and later. * The shadow effect is supported in Word 2007+ (`.docx`). Older formats
      (`.doc`) will lose the effect after conversion.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Przykład cienia kształtu Aspose.Words w Pythonie
url: /pl/python/images-shapes/aspose-words-shape-shadow-example-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Przykład cienia kształtu Aspose.Words w Pythonie

Przykład cienia kształtu Aspose.Words demonstruje, jak dodać efekt cienia do kształtu w dokumencie Word przy użyciu Pythona. W tym samouczku otrzymasz kompletny, gotowy do uruchomienia skrypt, który ładuje dokument, konfiguruje cień i zapisuje wynik.

Dodanie cienia do kształtu to powszechny sposób na poprawę hierarchii wizualnej w raportach, broszurach czy fakturach. Poniższy kod działa z Aspose.Words for Python via .NET i nie wymaga dodatkowych bibliotek zewnętrznych.

## Czego się nauczysz

* Jak załadować plik `.docx` przy użyciu **Aspose.Words for Python**.  
* Jak zlokalizować pierwszy kształt (w tym kształty wewnątrz tabel lub grup).  
* Jak skonfigurować rozmycie cienia, poziome i pionowe przesunięcie.  
* Jak zapisać zmodyfikowany dokument, zachowując całą pozostałą zawartość.  

**Wymagania wstępne**

* Python 3.8 lub nowszy.  
* Aspose.Words for Python via .NET zainstalowany (`pip install aspose-words`).  
* Dokument Word (`input.docx`) zawierający co najmniej jeden kształt (np. obraz, AutoShape lub pole tekstowe).  

If you need to install the library, run:

```bash
pip install aspose-words
```

## Przegląd przykładu cienia kształtu Aspose.Words

Poniższy skrypt jest pełnym rozwiązaniem. Podąża za czterema logicznymi krokami typowego przepływu pracy **document manipulation Aspose**: ładowanie, lokalizacja, modyfikacja i zapis.

```python
import aspose.words as aw

# ----------------------------------------------------------------------
# Step 1: Load the Word document
# ----------------------------------------------------------------------
# Replace YOUR_DIRECTORY with the path that contains input.docx.
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)

# ----------------------------------------------------------------------
# Step 2: Access the first shape (including descendants)
# ----------------------------------------------------------------------
# NodeType.SHAPE searches for any shape node. The third argument (True)
# tells Aspose.Words to search recursively through all child nodes.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# Verify that a shape was found; raise a clear error if not.
if shape is None:
    raise ValueError("No shape found in the document. Ensure input.docx contains a shape.")

# ----------------------------------------------------------------------
# Step 3: Configure the shape's shadow
# ----------------------------------------------------------------------
# The Shadow object controls visual appearance. Adjust the properties
# to achieve the desired effect.
shape.shadow.blur = 5          # Softness of the shadow (0‑15 is typical)
shape.shadow.offset_x = 2      # Horizontal displacement in points
shape.shadow.offset_y = 2      # Vertical displacement in points

# Optional: Change shadow color or transparency if needed.
# shape.shadow.color = aw.Color.black
# shape.shadow.transparency = 0.5

# ----------------------------------------------------------------------
# Step 4: Save the modified document
# ----------------------------------------------------------------------
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)

print(f"Shadow applied successfully. Saved to {output_path}")
```

### Oczekiwany rezultat

Otwórz `output.docx` w programie Microsoft Word. Pierwszy dodany kształt powinien teraz wyświetlać miękki cień, przesunięty o 2 pt w poziomie i w pionie, z promieniem rozmycia 5 pt. Cała pozostała zawartość pozostaje niezmieniona.

## Krok 1: Załaduj dokument Word

Ładowanie dokumentu jest pierwszą operacją w każdym przepływie pracy **Aspose.Words for Python**. Klasa `Document` parsuje plik i buduje model obiektowy w pamięci. Ponieważ biblioteka działa na platformie .NET, może efektywnie obsługiwać duże pliki.

*Dlaczego to ważne:* Załadowanie dokumentu raz i utrzymanie referencji (`doc`) unika powtarzających się operacji I/O, co poprawia wydajność przy konieczności zastosowania wielu modyfikacji.

## Krok 2: Uzyskaj dostęp do kształtu

Kształty mogą być bezpośrednimi dziećmi ciała dokumentu, lub mogą być zagnieżdżone w tabelach, grupach lub płótnach rysunkowych. Użycie `get_child(NodeType.SHAPE, 0, True)` przeszukuje rekurencyjnie i zwraca pierwszy pasujący kształt.

*Dlaczego to ważne:* Flaga `True` zapewnia, że nie przegapisz kształtów ukrytych wewnątrz innych węzłów. Jeśli ją pominiesz, rozważane będą tylko kształty najwyższego poziomu, a wiele rzeczywistych dokumentów zwróci `None`.

### Alternatywa: Znajdź kształt po nazwie

If your document contains several shapes, you might prefer to locate a specific one:

```python
shape = doc.get_child(aw.NodeType.SHAPE, lambda n: n.name == "MyLogo", True)
```

Ten fragment kodu demonstruje wariant **python shape shadow**, który filtruje po właściwości `name` kształtu.

## Krok 3: Skonfiguruj cień kształtu

Właściwość `shadow` obiektu `Shape` daje precyzyjną kontrolę nad efektem wizualnym. Trzy najczęściej dostosowywane atrybuty to:

| Właściwość | Typowy zakres | Efekt wizualny |
|------------|---------------|----------------|
| `blur`   | 0 – 15        | Wyższe wartości tworzą miększą krawędź. |
| `offset_x` | –10 – 10   | Dodatnie wartości przesuwają cień w prawo. |
| `offset_y` | –10 – 10   | Dodatnie wartości przesuwają cień w dół. |

Możesz także modyfikować `color`, `transparency`, `visible` i `style`. Przykład ustawia umiarkowane rozmycie i niewielkie przesunięcie, aby cień był subtelny.

**Wskazówka:** Gdy kształt już ma cień, powyższe właściwości nadpisują istniejące ustawienia. Jeśli musisz zachować oryginalny styl, odczytaj bieżące wartości przed ich zmianą.

## Krok 4: Zapisz zmodyfikowany dokument

Wywołanie `doc.save()` zapisuje reprezentację w pamięci z powrotem do pliku `.docx`. Aspose.Words automatycznie aktualizuje wszystkie wewnętrzne powiązania, więc plik wyjściowy pozostaje w pełni kompatybilny z Microsoft Word.

*Dlaczego to ważne:* Zapisanie tylko raz na końcu procesu zmniejsza ryzyko uszkodzenia pliku i poprawia ogólną szybkość, szczególnie przy przetwarzaniu wielu dokumentów w trybie wsadowym.

## Typowe warianty i przypadki brzegowe

### Praca z wieloma kształtami

Jeśli musisz zastosować ten sam cień do każdego kształtu, iteruj po kolekcji węzłów:

```python
for shp in doc.get_child_nodes(aw.NodeType.SHAPE, True):
    shp.shadow.blur = 5
    shp.shadow.offset_x = 2
    shp.shadow.offset_y = 2
```

### Zastosowanie cienia do określonego typu kształtu

Możesz filtrować po `ShapeType` (np. `aw.ShapeType.IMAGE`). Jest to przydatne, gdy chcesz wpływać tylko na obrazy, a nie na AutoShapes.

```python
for shp in doc.get_child_nodes(aw.NodeType.SHAPE, True):
    if shp.shape_type == aw.ShapeType.IMAGE:
        shp.shadow.blur = 4
```

### Obsługa dokumentów bez kształtów

Skrypt już zgłasza wyraźny `ValueError`, jeśli nie zostanie znaleziony żaden kształt. W kodzie produkcyjnym możesz zalogować problem i kontynuować przetwarzanie innych plików.

### Uwagi dotyczące kompatybilności

- Kod działa z **Aspose.Words for Python via .NET** w wersji 23.10 i nowszej.  
- Efekt cienia jest obsługiwany w Word 2007+ (`.docx`). Starsze formaty (`.doc`) utracą efekt po konwersji.

## Podsumowanie

Ten **aspose.words shape shadow example** prowadzi Cię przez ładowanie pliku Word, znajdowanie kształtu, konfigurowanie jego cienia i zapisywanie wyniku przy użyciu **Aspose.Words for Python**. Masz teraz wzorzec, który można ponownie wykorzystać w dowolnym scenariuszu **document manipulation Aspose** obejmującym ulepszenia wizualne.

Następnie możesz zbadać:

* Dodawanie wypełnień gradientowych lub stylów linii do kształtów (`modify shape shadow` i inne właściwości wizualne).  
* Łączenie konfiguracji cienia z formatowaniem tekstu w celu stworzenia w pełni stylizowanych szablonów.  
* Automatyzację procesu dla serii dokumentów przy użyciu `os.listdir` i wzorca pokazanego powyżej.

Śmiało eksperymentuj z różnymi poziomami rozmycia, przesunięciami i kolorami, aby dopasować je do wytycznych Twojej marki. Szczęśliwego kodowania!

## Co powinieneś się nauczyć dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Dodaj cień do kształtu w Pythonie – Kompletny samouczek Aspose.Words](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [Jak ustawić cień na kształcie w Aspose.Words for Python](/words/english/python-net/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-for-python/)
- [Jak zapisać PNG i dodać cień do kształtu przy użyciu Aspose.Words](/words/english/python-net/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}