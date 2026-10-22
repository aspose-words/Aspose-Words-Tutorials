---
category: general
date: 2026-10-04
description: Jak utworzyć dokument w Pythonie i dodać cień do kształtu przy użyciu
  Aspose.Words. Dowiedz się, jak ustawić kolor cienia, wstawić prostokątny kształt
  i dostosować zewnętrzny cień.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create document
- add shadow to shape
- set shadow color
- insert rectangle shape
- how to add shadow
language: pl
lastmod: 2026-10-04
og_description: Jak utworzyć dokument w Pythonie i dodać cień do kształtu. Ten przewodnik
  pokazuje, jak ustawić kolor cienia, wstawić prostokątny kształt i zastosować zewnętrzny
  cień przy użyciu Aspose.Words.
og_image_alt: Python code inserting a rectangle shape with a visible shadow into a
  Word document
og_title: Jak stworzyć dokument z prostokątnym kształtem i cieniem w Pythonie
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  headline: How to create document with a rectangle shape and shadow in Python
  type: TechArticle
- description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  name: How to create document with a rectangle shape and shadow in Python
  steps:
  - name: Why does the shadow sometimes appear invisible?
    text: The shadow is only rendered if `shadow.visible` is set to `True` **and**
      the shape’s `wrap_type` allows it to be displayed. An inline shape works reliably;
      floating shapes may require additional layout adjustments.
  - name: How can I change the shadow color to match a brand palette?
    text: 'Replace `aw.drawing.Color.black` with a custom RGB value:'
  - name: What if I need the shape to appear behind text?
    text: Set the wrap type to `WrapType.BEHIND` and adjust the `z_order_position`
      if necessary. Keep in mind that some viewers may render behind‑text shapes differently.
  - name: Can I apply the same shadow settings to multiple shapes?
    text: Yes. Create a helper function that configures the shadow and call it for
      each shape you insert. This promotes code reuse and ensures consistent styling.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Jak stworzyć dokument z prostokątnym kształtem i cieniem w Pythonie
url: /pl/python/images-shapes/how-to-create-document-with-a-rectangle-shape-and-shadow-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć dokument z prostokątnym kształtem i cieniem w Pythonie

Jeśli potrzebujesz **jak utworzyć dokument**, który zawiera stylizowany prostokąt, ten przewodnik zapewnia pełne rozwiązanie. Zobaczysz, jak **dodać cień do kształtu**, ustawić kolor cienia i kontrolować jego przesunięcie oraz rozmycie — wszystko przy użyciu Aspose.Words for Python. Po zakończeniu samouczka będziesz mógł wygenerować plik `.docx`, który wygląda profesjonalnie i jest gotowy do dystrybucji.

Kroki poniżej obejmują wszystko, od instalacji biblioteki po dostosowanie wyglądu cienia. Nie potrzebna jest żadna zewnętrzna dokumentacja; kod jest gotowy do skopiowania, uruchomienia i dostosowania do własnych projektów. Nauczysz się także, jak **wstawić prostokątny kształt**, wybrać **styl zewnętrznego cienia** oraz radzić sobie z typowymi problemami, takimi jak niewidoczne cienie czy nieprawidłowe ustawienia zawijania.

## Wymagania wstępne

Przed rozpoczęciem upewnij się, że masz:

* Zainstalowany Python 3.8 lub nowszy.
* Aktywną licencję Aspose.Words for Python (lub darmowy klucz ewaluacyjny).
* Podstawową znajomość skryptowania w Pythonie.
* Dostęp do lokalizacji w systemie plików, w której zostanie zapisany wygenerowany dokument.

Możesz zainstalować SDK przy pomocy pip:

```bash
pip install aspose-words
```

## Krok 1: Import biblioteki i utworzenie nowego pustego dokumentu

Utworzenie nowego dokumentu to pierwsza akcja w każdym scenariuszu automatyzacji Worda. Konstruktor `aw.Document()` daje Ci pusty plik, który możesz wypełnić tekstem, obrazami lub kształtami.

```python
import aspose.words as aw

# Create a new blank document
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

Obiekt `DocumentBuilder` upraszcza wstawianie treści. Śledzi bieżącą pozycję kursora, dzięki czemu możesz dodawać elementy kolejno, bez ręcznego zarządzania sekcjami.

## Krok 2: Wstaw prostokątny kształt o żądanym rozmiarze

Prostokątny kształt działa jako kontener dla elementów wizualnych. Możesz określić jego szerokość i wysokość w punktach (1 pt ≈ 1/72 in).

```python
# Insert a rectangle shape that is 150 pt wide and 80 pt tall
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

Na tym etapie kształt nie ma żadnego stylu wizualnego, więc wygląda jak zwykła obwódka. Kolejne kroki nadadzą mu głębię i kolor.

## Krok 3: Ustaw kształt, aby przepływał w linii z otaczającym tekstem

Gdy kształt jest **inline**, zachowuje się jak znak w akapicie. Dzięki temu prostokąt pozostaje w miejscu, którego oczekujesz w układzie dokumentu.

```python
# Make the shape inline so it follows the text flow
rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE
```

Jeśli wolisz, aby kształt unosił się nad tekstem, możesz użyć `WrapType.SQUARE` lub `WrapType.TOP_BOTTOM`, ale w większości raportów kształt inline zapewnia przewidywalny układ.

## Krok 4: Uczyń cień widocznym i wybierz jego kolor

Cień, który nie jest widoczny, nie przynosi żadnych korzyści wizualnych. Flaga `visible` aktywuje efekt, a właściwość `color` określa jego odcień. Użycie czerni daje klasyczną, subtelną głębię.

```python
# Enable the shadow and set its color to black
rectangle_shape.shadow.visible = True
rectangle_shape.shadow.color = aw.drawing.Color.black
```

Możesz zamienić `aw.drawing.Color.black` na dowolny inny kolor, na przykład `aw.drawing.Color.gray` lub własną wartość RGB (`aw.drawing.Color.from_argb(255, 128, 128, 128)`).

## Krok 5: Zdefiniuj przesunięcie i rozmycie cienia, aby nadać mu głębię

Przesunięcie kontroluje, jak daleko cień jest odsunięty od kształtu, natomiast promień rozmycia wygładza krawędzie. Małe wartości tworzą ostry cień; większe wartości dają bardziej miękki wygląd.

```python
# Horizontal and vertical offset of 5 pt each
rectangle_shape.shadow.offset_x = 5
rectangle_shape.shadow.offset_y = 5

# Blur radius of 3 pt for a gentle feather
rectangle_shape.shadow.blur = 3
```

Eksperymentuj z tymi liczbami, aby dopasować je do wytycznych projektowych. Dla mocnego cienia spadającego możesz zwiększyć zarówno offset, jak i blur.

## Krok 6: Wybierz styl zewnętrznego cienia

Aspose.Words oferuje kilka stylów cieni, takich jak `INNER`, `OUTER` i `PERSPECTIVE`. Styl **outer** umieszcza cień poza granicą kształtu, co jest idealne dla czystego, profesjonalnego wyglądu.

```python
# Apply an outer shadow style
rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

Jeśli potrzebujesz bardziej dramatycznego efektu, wypróbuj `ShadowStyle.PERSPECTIVE` — dodaje trójwymiarowy pochylenie.

## Krok 7: Zapisz dokument z kształtem i cieniem

Zapis finalizuje plik i zapisuje wszystkie formatowania na dysku. Wybierz katalog, w którym masz uprawnienia do zapisu, i nadaj plikowi opisową nazwę.

```python
# Save the document to the desired location
output_path = "output/ShapeWithShadow.docx"
document.save(output_path)
print(f"Document saved to {output_path}")
```

Uruchomienie skryptu tworzy plik Word, który zawiera prostokąt z widocznym, kolorowym cieniem. Otwórz plik w Microsoft Word lub LibreOffice, aby zweryfikować rezultat.

## Pełny działający przykład

Poniżej znajduje się kompletny skrypt, który zawiera wszystkie omówione kroki. Skopiuj kod do pliku o nazwie `create_shadowed_shape.py` i uruchom go poleceniem `python create_shadowed_shape.py`.

```python
import aspose.words as aw
import os

def main():
    # Ensure the output directory exists
    output_dir = "output"
    os.makedirs(output_dir, exist_ok=True)

    # Step 1: Create a new blank document
    document = aw.Document()
    builder = aw.DocumentBuilder(document)

    # Step 2: Insert a rectangle shape of the desired size
    rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

    # Step 3: Set the shape to be inline with the text flow
    rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE

    # Step 4: Make the shadow visible and choose its color
    rectangle_shape.shadow.visible = True
    rectangle_shape.shadow.color = aw.drawing.Color.black

    # Step 5: Define the shadow's offset and blur to give it depth
    rectangle_shape.shadow.offset_x = 5   # horizontal offset in points
    rectangle_shape.shadow.offset_y = 5   # vertical offset in points
    rectangle_shape.shadow.blur = 3       # blur radius in points

    # Step 6: Choose an outer shadow style
    rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER

    # Step 7: Save the document with the shaped shadow
    output_path = os.path.join(output_dir, "ShapeWithShadow.docx")
    document.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    main()
```

**Oczekiwany wynik**

Po otwarciu `ShapeWithShadow.docx` zobaczysz pojedynczy prostokąt wyśrodkowany na stronie. Prostokąt jest otoczony subtelnym czarnym cieniem przesuniętym w dół‑w prawo, lekko rozmytym, aby stworzyć wrażenie głębi. Cień respektuje styl zewnętrzny, więc nie przecina wnętrza prostokąta.

## Częste pytania i przypadki brzegowe

### Dlaczego cień czasami jest niewidoczny?

Cień jest renderowany tylko wtedy, gdy `shadow.visible` jest ustawione na `True` **i** typ zawijania kształtu (`wrap_type`) pozwala na jego wyświetlenie. Kształt inline działa niezawodnie; kształty unoszące się mogą wymagać dodatkowych korekt układu.

### Jak mogę zmienić kolor cienia, aby pasował do palety marki?

Zamień `aw.drawing.Color.black` na własną wartość RGB:

```python
rectangle_shape.shadow.color = aw.drawing.Color.from_argb(255, 0, 120, 215)  # corporate blue
```

### Co zrobić, jeśli potrzebuję, aby kształt pojawił się za tekstem?

Ustaw typ zawijania na `WrapType.BEHIND` i w razie potrzeby dostosuj `z_order_position`. Pamiętaj, że niektóre przeglądarki mogą renderować kształty za tekstem inaczej.

### Czy mogę zastosować te same ustawienia cienia do wielu kształtów?

Tak. Utwórz funkcję pomocniczą, która konfiguruje cień, i wywołuj ją dla każdego wstawianego kształtu. To promuje ponowne użycie kodu i zapewnia spójny styl.

```python
def apply_shadow(shape, color=aw.drawing.Color.black, offset=5, blur=3):
    shape.shadow.visible = True
    shape.shadow.color = color
    shape.shadow.offset_x = offset
    shape.shadow.offset_y = offset
    shape.shadow.blur = blur
    shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

## Podsumowanie

Teraz wiesz, **jak utworzyć dokument**, który zawiera prostokątny kształt z dostosowanym cieniem przy użyciu Aspose.Words for Python. Samouczek obejmował wstawianie prostokąta, ustawianie kształtu jako inline, włączanie cienia, ustawianie jego koloru, przesunięcia, rozmycia i stylu oraz ostateczne zapisywanie pliku.

Od tego momentu możesz zgłębiać powiązane tematy, takie jak **add shadow to shape** dla innych typów kształtów, **set shadow color** dynamicznie w oparciu o dane, lub **how to add shadow** do obrazów i pól tekstowych. Eksperymentuj z różnymi wymiarami, kolorami i stylami cieni, aby dopasować je do wytycznych marki lub systemu projektowego.

Gotowy, aby zautomatyzować więcej dokumentów Word? Spróbuj dodać tabele, nagłówki lub dynamiczną treść — każdy krok opiera się na tych samych zasadach przedstawionych tutaj. Powodzenia w kodowaniu!

## Co warto nauczyć się dalej?

Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki zaprezentowane w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Utwórz prostokątny kształt, dodaj cień i zapisz PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Utwórz pusty dokument Word z prostokątnym kształtem z cieniem – przewodnik krok po kroku](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Jak zarządzać zmiennymi dokumentu przy użyciu Aspose.Words w Pythonie: kompletny przewodnik](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}