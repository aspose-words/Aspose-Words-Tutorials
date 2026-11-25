---
category: general
date: 2026-11-25
description: Dodaj cień do kształtu w dokumencie Word przy użyciu Pythona. Dowiedz
  się, jak wstawić prostokątny kształt w Wordzie i zastosować przezroczysty cień przy
  użyciu Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- insert rectangle shape word
- how to create word document python
- Aspose.Words Python
- shape formatting Python
language: pl
lastmod: 2026-11-25
og_description: Dodaj cień do kształtu w dokumencie Word przy użyciu Pythona. Ten
  samouczek pokazuje, jak wstawić prostokątny kształt w Wordzie i ustawić 30 % przezroczysty
  cień za pomocą Aspose.Words.
og_image_alt: Add shadow to shape example in a Word document created by Python
og_title: Dodaj cień do kształtu w dokumencie Word przy użyciu Pythona – przewodnik
  krok po kroku
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Add shadow to shape in a Word document with Python. Learn how to insert
    rectangle shape in Word and apply a transparent shadow using Aspose.Words.
  headline: How to add shadow to shape in a Word document using Python
  type: TechArticle
tags:
- Python
- Aspose.Words
- Word automation
title: Jak dodać cień do kształtu w dokumencie Word przy użyciu Pythona
url: /pl/python/images-shapes/how-to-add-shadow-to-shape-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak dodać cień do kształtu w dokumencie Word przy użyciu Pythona

Jeśli potrzebujesz **dodać cień do kształtu** w dokumencie Word, ten przewodnik pokaże Ci kompletną, gotową do uruchomienia rozwiązanie. Zobaczysz, jak utworzyć plik Word, wstawić prostokątny kształt i zastosować 30 % przezroczysty cień — wszystko przy użyciu biblioteki Aspose.Words for Python.

Programowe operowanie na dokumentach Word oszczędza ręcznego formatowania i pozwala generować raporty, umowy czy materiały marketingowe w dużej skali. Po zakończeniu tego tutorialu będziesz w stanie odpowiedzieć na pytanie „**jak stworzyć dokument Word w Pythonie**” gotowym przykładem kodu.

## Wymagania wstępne

Zanim zaczniesz, upewnij się, że masz:

* Python 3.8 lub nowszy.
* Aktywną licencję Aspose.Words for Python (bezpłatna wersja próbna działa w trybie ewaluacyjnym).
* Pakiet `aspose-words` zainstalowany poleceniem `pip install aspose-words`.
* Folder, w którym można zapisać plik wyjściowy (zastąp w kodzie `YOUR_DIRECTORY`).

Nie są wymagane żadne dodatkowe zależności.

## Krok 1: Utwórz nowy dokument Word

Pierwszym krokiem jest utworzenie obiektu `Document`. Obiekt ten reprezentuje cały plik .docx w pamięci.

```python
import aspose.words as aw

# Create an empty Word document
doc = aw.Document()
# DocumentBuilder provides a convenient API for adding content
builder = aw.DocumentBuilder(doc)
```

`DocumentBuilder` działa jak wirtualny kursor. Gdy wywołujesz jego metody, biblioteka wstawia odpowiednie elementy w bieżącej pozycji kursora.

## Krok 2: Wstaw prostokątny kształt

Następnie **wstaw prostokątny kształt** używając metody `insert_shape` buildera. Metoda wymaga typu kształtu oraz jego rozmiaru w punktach (1 punkt = 1/72 cala).

```python
# Insert a rectangle shape that is 100 points wide and 50 points tall
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)
```

Możesz zmienić wymiary, aby dopasować je do swojego projektu. Prostokąt staje się częścią warstwy rysunkowej dokumentu, co oznacza, że później możesz modyfikować jego wypełnienie, obrys lub cień.

## Krok 3: Uzyskaj dostęp do formatu cienia kształtu

Każdy obiekt rysunkowy udostępnia właściwość `shadow_format`, która kontroluje wygląd cienia. Pobierz ją, aby móc dostosować przezroczystość, offset, rozmycie i kolor.

```python
# Get the ShadowFormat object for the rectangle
shadow = shape.shadow_format
```

Na tym etapie kształt ma domyślny cień (brak cienia). Obiekt `ShadowFormat` zawiera wszystkie parametry potrzebne do stworzenia realistycznego efektu.

## Krok 4: Ustaw cień na 30 % przezroczysty

Przezroczystość wyrażana jest jako wartość od `0` (całkowicie nieprzezroczysty) do `1` (całkowicie przezroczysty). Ustawienie jej na `0.3` daje 30 % przezroczysty cień, co zazwyczaj wystarcza, aby dodać głębię bez przytłaczania tekstu.

```python
# Apply a 30 % transparent shadow
shadow.transparency = 0.3
# Optional: adjust other shadow properties for a nicer look
shadow.visible = True               # Ensure the shadow is turned on
shadow.distance = 4                 # Distance of the shadow from the shape (points)
shadow.blur = 4                     # Amount of blur applied to the shadow
shadow.color = aw.Color.black       # Shadow color
```

Te dodatkowe właściwości nie są wymagane, ale ilustrują, jak można precyzyjnie dostroić efekt. Flaga `visible` jest niezbędna; jeśli ją pominiesz, cień nie pojawi się, mimo że pozostałe ustawienia są skonfigurowane.

## Krok 5: Zapisz dokument, aby zobaczyć rezultat

Na koniec zapisz dokument na dysku. Otworzenie wygenerowanego pliku `.docx` w Microsoft Word lub innym kompatybilnym przeglądarce pokaże prostokąt z zastosowanym przezroczystym cieniem.

```python
# Save the document to the desired location
output_path = r"YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Gdy otworzysz `output.docx`, zobaczysz prosty prostokąt z subtelnym szarym cieniem przesuniętym w dół‑w prawo. Przezroczystość cienia wynosząca 30 % sprawia, że kształt wydaje się unosić nad stroną.

![Add shadow to shape example](placeholder-image.png){: .align-center alt="Przykład dodania cienia do kształtu w dokumencie Word utworzonym przy użyciu Pythona"}

## Pełny, gotowy do uruchomienia skrypt

Połączenie wszystkich elementów daje samodzielny skrypt, który możesz skopiować, wkleić i od razu uruchomić.

```python
import aspose.words as aw

def create_word_with_shadow(output_path: str):
    """
    Creates a Word document that contains a rectangle shape
    with a 30 % transparent shadow.
    """
    # Step 1: Initialize document and builder
    doc = aw.Document()
    builder = aw.DocumentBuilder(doc)

    # Step 2: Insert rectangle shape
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)

    # Step 3: Access shadow format
    shadow = shape.shadow_format

    # Step 4: Configure shadow properties
    shadow.visible = True
    shadow.transparency = 0.3
    shadow.distance = 4
    shadow.blur = 4
    shadow.color = aw.Color.black

    # Step 5: Save the document
    doc.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    # Replace with a valid folder on your machine
    create_word_with_shadow(r"YOUR_DIRECTORY/output.docx")
```

**Oczekiwany wynik:** Otworzenie wygenerowanego `output.docx` wyświetla jedną stronę z prostokątem, który rzuca lekki, półprzezroczysty cień. Nie jest wymagana żadna dodatkowa formatowanie.

## Typowe warianty i przypadki brzegowe

| Sytuacja | Jak dostosować kod |
|-----------|-----------------------|
| **Inny typ kształtu** (np. elipsa) | Zmien `aw.drawing.ShapeType.RECTANGLE` na `aw.drawing.ShapeType.ELLIPSE`. |
| **Niestandardowy kolor cienia** | Ustaw `shadow.color = aw.Color.from_argb(255, 128, 0, 0)` dla cienia o odcieniu czerwieni. |
| **Wiele kształtów** | Wywołuj `builder.insert_shape` wielokrotnie; każde wywołanie zwraca osobny obiekt `Shape`, który możesz stylizować niezależnie. |
| **Zapis jako PDF** | Zamień `doc.save(output_path)` na `doc.save(output_path.replace('.docx', '.pdf'))` i użyj rozszerzenia `.pdf`. |
| **Uruchamianie bez licencji** | Bezpłatna wersja próbna dodaje znak wodny na pierwszej stronie. Uzyskaj licencję, aby go usunąć w środowisku produkcyjnym. |

Te warianty pokazują, że ten sam wzorzec — utwórz dokument, wstaw kształt, dostosuj `shadow_format`, zapisz — obejmuje większość scenariuszy automatyzacji.

## Wskazówki i najlepsze praktyki

* **Ponowne użycie buildera**: Trzymaj jedną instancję `DocumentBuilder` dla całego dokumentu, aby uniknąć niepotrzebnego tworzenia obiektów.
* **Zwolnij zasoby**: W długotrwałych usługach wywołaj `doc.dispose()` po zapisaniu, aby zwolnić pamięć natywną.
* **Waliduj wynik**: Użyj `doc.validate(aw.ValidationType.FULL_VALIDATION)` przed zapisem, jeśli musisz zapewnić zgodność ze standardem Open XML.
* **Kompatybilność wersji**: Kod działa z Aspose.Words for Python ≥ 22.9. Upewnij się, że pakiet jest aktualny, wykonując `pip install --upgrade aspose-words`.

## Podsumowanie

Teraz wiesz, jak **dodać cień do kształtu** w dokumencie Word przy użyciu Pythona. Postępując zgodnie z pięcioma krokami — utwórz dokument, **wstaw prostokątny kształt**, skonfiguruj cień i zapisz — możesz zautomatyzować tworzenie eleganckich dokumentów, takich jak raporty, faktury czy materiały marketingowe.  

Od tego momentu możesz eksplorować inne opcje formatowania, takie jak wypełnienia gradientowe, opływanie tekstu czy konwersja dokumentu do PDF. Każdy z tych tematów opiera się na tych samych koncepcjach `DocumentBuilder` i formatowania kształtów, które zostały wprowadzone w tym tutorialu.

Miłego kodowania i ciesz się wizualną głębią, jaką prosty cień może dodać do Twoich zautomatyzowanych dokumentów Word!


## Co powinieneś nauczyć się dalej?


Poniższe tutoriale obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Jak utworzyć prostokątny kształt w dokumencie Word przy użyciu Pythona](/words/english/python-net/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/)
- [Dodaj cień do kształtu w Pythonie – Kompletny tutorial Aspose.Words](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [Utwórz pusty dokument Word i dodaj cień do kształtu – Pełny przewodnik Python](/words/english/python-net/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-pyth/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}