---
category: general
date: 2026-10-16
description: Utwórz pusty dokument Word, wstaw kształt w Wordzie, dodaj zewnętrzny
  cień i zapisz jako PDF przy użyciu Pythona.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert shape in word
- save as pdf python
- add outer shadow shape
- create pdf with shape
language: pl
lastmod: 2026-10-16
og_description: Utwórz pusty dokument Word z kształtem zewnętrznego cienia przy użyciu
  Aspose.Words dla Pythona. Ten przewodnik pokazuje, jak wstawić kształt, zastosować
  cień i zapisać plik jako PDF.
og_image_alt: Screenshot of a Word document containing a rectangle shape with an outer
  shadow, saved as PDF
og_title: Utwórz pusty dokument Word z cieniem kształtu – przewodnik Pythona
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document, insert shape in Word, add outer shadow,
    and save as PDF using Python.
  headline: Create blank Word document with shadowed shape in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- PDF generation
- Shape styling
title: Utwórz pusty dokument Word z cieniowanym kształtem w Pythonie
url: /pl/python/word-automation/create-blank-word-document-with-shadowed-shape-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz pusty dokument Word z kształtem z cieniem w Pythonie

Jeśli potrzebujesz **utworzyć pusty dokument Word** i dodać własną grafikę, ten przewodnik Cię poprowadzi. Przejdziemy krok po kroku, jak **wstawić kształt w Wordzie**, zastosować **cień zewnętrzny** oraz **zapisz jako PDF przy użyciu Pythona**.

Nauczysz się, jak skonfigurować Aspose.Words for Python, zbudować prostokąt, wystylizować jego cień i wygenerować PDF zachowujący efekt wizualny. Nie wymagana jest wcześniejsza znajomość API Aspose, ale przydatna będzie podstawowa wiedza o Pythonie oraz działająca instalacja Python 3.10 lub nowszej.

## Prerequisites

Zanim rozpoczniesz, upewnij się, że masz:

* Python 3.10 lub nowszy zainstalowany.
* Aktywną licencję Aspose.Words for Python (bezpłatna wersja próbna wystarczy do oceny).
* Dostęp do `pip`, aby zainstalować pakiet `aspose-words`.
* Uprawnienia do zapisu w katalogu, w którym zostanie zapisany PDF.

Bibliotekę możesz zainstalować jednym poleceniem:

```bash
pip install aspose-words
```

## Create blank Word document – environment setup

Pierwszym krokiem jest utworzenie pustego pliku Word, który posłuży jako płótno dla kształtu.

```python
import aspose.words as aw

# Initialize a new, empty document
doc = aw.Document()
# DocumentBuilder provides convenient methods for adding content
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` reprezentuje całkowicie pusty plik Word. Korzystając z `DocumentBuilder`, uzyskasz dostęp do metod takich jak `insert_shape`, które wykorzystamy w następnym kroku.

## Insert shape in Word and set dimensions

Teraz dodajemy prostokąt, który później otrzyma cień zewnętrzny. Rozmiar podawany jest w punktach (1 pt ≈ 1/72 cala).

```python
# Insert a rectangle shape with a width of 200 pt and a height of 100 pt
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)
```

Wywołanie `insert_shape` zwraca obiekt `Shape`, który możesz dalej dostosowywać. W tym momencie dokument już zawiera widoczny prostokąt po otwarciu w Microsoft Word.

## Add outer shadow shape – customizing the effect

Aspose.Words udostępnia klasę `ShadowEffect`, aby określić właściwości cienia, takie jak styl, rozmycie, odległość i kolor.

```python
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a new shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # Choose an outer shadow
shadow.blur = 5.0                         # Softness of the shadow edges
shadow.distance = 3.0                     # Offset distance from the shape
shadow.color = aw.Color.black             # Shadow color

# Apply the shadow to the rectangle
rectangle.shadow = shadow
```

Ustawienie `style` na `OUTER` zapewnia, że cień pojawia się poza krawędzią prostokąta, nadając subtelną, trójwymiarową estetykę. Możesz eksperymentować z `blur` i `distance`, aby uzyskać cień bardziej zwartą lub rozproszoną.

## Save as PDF python – finalizing the document

Po wystylizowaniu kształtu dokument można zapisać bezpośrednio jako PDF. Aspose.Words obsługuje konwersję wewnętrznie, zachowując efekt cienia.

```python
output_path = "output/shape_with_shadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Gdy otworzysz `shape_with_shadow.pdf` w dowolnym przeglądarce PDF, zobaczysz prostokąt z zewnętrznym cieniem dokładnie takim, jak w Wordzie.

## Full working example

Poniżej pełny skrypt łączący wszystkie kroki. Skopiuj go do pliku o nazwie `create_word_with_shadow.py` i uruchom.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1. Create a blank Word document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2. Insert a rectangle shape
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)

# 3. Define and apply an outer shadow
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER
shadow.blur = 5.0
shadow.distance = 3.0
shadow.color = aw.Color.black
rectangle.shadow = shadow

# 4. Save the document as PDF
pdf_path = os.path.join(output_dir, "shape_with_shadow.pdf")
doc.save(pdf_path)

print(f"PDF generated at: {pdf_path}")
```

**Expected output**

Uruchomienie skryptu wypisuje linię potwierdzającą, np.:

```
PDF generated at: output/shape_with_shadow.pdf
```

Otwarcie wygenerowanego PDF pokazuje jedną stronę zawierającą prostokąt 200 pt × 100 pt z delikatnym czarnym cieniem zewnętrznym.

## Common variations and edge cases

* **Changing shadow color** – Zamień `aw.Color.black` na dowolną inną wartość `aw.Color`, np. `aw.Color.red` lub `aw.Color.from_argb(255, 0, 120, 215)`.
* **Using a different shape** – Zmień `aw.drawing.ShapeType.RECTANGLE` na `OVAL`, `DIAMOND` lub dowolną obsługiwaną wartość wyliczeniową.
* **Saving as DOCX instead of PDF** – Wywołaj `doc.save("output/shape.docx")`, aby zachować format Word.
* **Multiple shapes** – Utwórz dodatkowe kształty, wywołując ponownie `builder.insert_shape`; każdy kształt może mieć własny `ShadowEffect`.

**Pro tip:** Jeśli musisz umieścić kształt w określonym miejscu, ustaw `rectangle.left` i `rectangle.top` po wstawieniu. Dzięki temu uzyskasz precyzyjną kontrolę położenia w pikselach.

## Conclusion

Teraz wiesz, jak **utworzyć pusty dokument Word**, **wstawić kształt w Wordzie**, **dodać cień zewnętrzny** oraz **zapisać jako PDF przy użyciu Pythona**. Pełny przykład kodu demonstruje cały przepływ od początku do końca, a wyjaśnienia pokazują, dlaczego każde wywołanie API jest potrzebne.

Od tego momentu możesz eksplorować bardziej zaawansowane opcje stylizacji, dodać tekst wewnątrz kształtu lub połączyć wiele kształtów, aby tworzyć złożone diagramy. Eksperymentuj z różnymi parametrami cienia, aby dopasować je do wizualnego języka Twojej marki i włącz tę metodę do większych potoków generowania dokumentów.

Happy coding!

## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Create PDF from Word – Complete Python Guide with Aspose.Words](/words/english/python-net/document-conversion/create-pdf-from-word-complete-python-guide-with-aspose-words/)
- [Add Shadow to Shape in Word with Aspose.Words – Step‑by‑Step](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}