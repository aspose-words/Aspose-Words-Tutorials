---
category: general
date: 2026-10-07
description: Dowiedz się, jak zapisać dokument jako PDF, dodając kształt prostokąta
  i niestandardowy cień przy użyciu Aspose.Words dla Pythona. Dołączony kod krok po
  kroku.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save document as pdf
- add rectangle shape
- export word to pdf
- set rectangle dimensions
- draw rectangle word
language: pl
lastmod: 2026-10-07
og_description: Zapisz dokument jako PDF z niestandardowym kształtem prostokąta przy
  użyciu Aspose.Words dla Pythona. Przejrzyj pełny przykład, aby narysować, sformatować
  i wyeksportować dokument Word do PDF.
og_image_alt: Screenshot of the generated PDF showing the rectangle shape after save
  document as pdf
og_title: Zapisz dokument jako PDF z prostokątnym kształtem – kompletny przewodnik
  Pythona
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  headline: How to save document as PDF with a custom rectangle shape in Python
  type: TechArticle
- description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  name: How to save document as PDF with a custom rectangle shape in Python
  steps:
  - name: Initialize a new blank document
    text: '```python import aspose.words as aw'
  - name: Add rectangle shape to the document
    text: '```python # Create a rectangle shape and attach it to the document. rectangle
      = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)'
  - name: Set rectangle dimensions
    text: '```python # Define width and height in points (1 point = 1/72 inch). rectangle.width
      = 200 # 200 points ≈ 2.78 inches rectangle.height = 100 # 100 points ≈ 1.39
      inches ```'
  - name: (Optional) Apply a visible custom shadow
    text: '```python shadow = rectangle.shadow_format shadow.visible = True # Show
      the shadow shadow.blur = 5.0 # Softness of the shadow edge shadow.distance =
      3.0 # How far the shadow is offset shadow.angle = 45 # Direction in degrees
      shadow.color = aw.drawing.Color.black ```'
  - name: Save document as PDF
    text: '```python output_path = "output/shadow_rectangle.pdf" document.save(output_path)
      print(f"PDF saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Word automation
title: Jak zapisać dokument jako PDF z niestandardowym kształtem prostokąta w Pythonie
url: /pl/python/document-conversion/how-to-save-document-as-pdf-with-a-custom-rectangle-shape-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak zapisać dokument jako PDF z niestandardowym kształtem prostokąta w Pythonie

Jeśli potrzebujesz **save document as PDF** dodając własne grafiki, ten przewodnik pokaże Ci, jak to zrobić. Przejdziemy przez tworzenie pustego pliku Word, **drawing a rectangle shape**, ustawianie jego rozmiaru, zastosowanie widocznego cienia oraz w końcu **export Word to PDF** przy użyciu biblioteki Aspose.Words for Python.

Uzyskasz PDF zawierający idealnie umieszczony prostokąt, gotowy do raportów, faktur lub dowolnego scenariusza automatyzacji dokumentów. Nie są wymagane żadne zewnętrzne narzędzia — tylko Python i pakiet Aspose.Words.

## Czego będziesz potrzebować

| Wymaganie | Dlaczego jest ważne |
|-----------|----------------------|
| Python 3.8+ | API Aspose.Words for Python jest skierowane do nowoczesnych interpreterów. |
| Pakiet `aspose-words` (`pip install aspose-words`) | Dostarcza przestrzeń nazw `aw` używaną w przykładach kodu. |
| Podstawowa znajomość Pythona i programowania obiektowego | Tutorial manipuluje obiektami takimi jak `Document` i `Shape`. |
| Uprawnienia do zapisu w folderze, w którym zostanie zapisany PDF | Krok `save document as pdf` zapisuje plik na dysku. |

> **Wskazówka:** Użyj wirtualnego środowiska (`python -m venv venv`), aby izolować zależności.

## Jak zapisać dokument jako PDF z kształtem prostokąta

Poniżej znajduje się kompletny, gotowy do uruchomienia przykład. Każdy krok jest wyjaśniony, abyś rozumiał **dlaczego** wykonujemy daną akcję, a nie tylko **co** robi kod.

### Krok 1: Zainicjuj nowy pusty dokument

```python
import aspose.words as aw

# Create an empty Word document – this is the canvas for our shape.
document = aw.Document()
```

Utworzenie nowego obiektu `Document` zapewnia czystą kolekcję stron. Możesz także wczytać istniejący plik *.docx*, jeśli chcesz później **export Word to PDF**, ale rozpoczęcie od pustego dokumentu utrzymuje przykład skoncentrowany.

### Krok 2: Dodaj kształt prostokąta do dokumentu

```python
# Create a rectangle shape and attach it to the document.
rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

# The shape must be placed inside a paragraph before it appears.
paragraph = document.first_section.body.first_paragraph
paragraph.append_child(rectangle)
```

Krok `add rectangle shape` używa `ShapeType.RECTANGLE`. Dodając kształt do akapitu, Aspose.Words wie, gdzie go wyrenderować w ostatecznym PDF.

### Krok 3: Ustaw wymiary prostokąta

```python
# Define width and height in points (1 point = 1/72 inch).
rectangle.width = 200   # 200 points ≈ 2.78 inches
rectangle.height = 100  # 100 points ≈ 1.39 inches
```

Ustawienie explicite **wymiarów prostokąta** zapewnia spójny wygląd kształtu na różnych platformach. Możesz także użyć pomocników `convert_to_inches`, jeśli wolisz jednostki imperialne.

### Krok 4: (Opcjonalnie) Zastosuj widoczny niestandardowy cień

```python
shadow = rectangle.shadow_format
shadow.visible = True          # Show the shadow
shadow.blur = 5.0              # Softness of the shadow edge
shadow.distance = 3.0          # How far the shadow is offset
shadow.angle = 45              # Direction in degrees
shadow.color = aw.drawing.Color.black
```

Cień sprawia, że prostokąt wyróżnia się w PDF. Flaga `shadow.visible` jest wymagana; bez niej pozostałe właściwości nie mają efektu.

### Krok 5: Zapisz dokument jako PDF

```python
output_path = "output/shadow_rectangle.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Wywołanie `document.save` z rozszerzeniem **.pdf** automatycznie **save document as pdf** przy użyciu wbudowanego renderera PDF Aspose.Words. Nie są potrzebne dodatkowe kroki konwersji, dlatego ta metoda jest zalecaną drogą do **export Word to PDF**.

> **Dlaczego to działa:** Aspose.Words zapisuje układ dokumentu, w tym prostokąt i jego cień, bezpośrednio do strumienia PDF. Proces jest bezstratny i zachowuje jakość wektorową.

## Pełny kod źródłowy (pojedynczy skrypt)

```python
import aspose.words as aw

def create_pdf_with_rectangle(output_path: str):
    """
    Creates a PDF that contains a single rectangle shape with a custom shadow.
    The function demonstrates:
    • add rectangle shape
    • set rectangle dimensions
    • export Word to PDF (save document as pdf)
    """
    # 1️⃣ Create a new blank document
    document = aw.Document()

    # 2️⃣ Insert a rectangle shape
    rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

    # 3️⃣ Set the shape's size
    rectangle.width = 200   # points
    rectangle.height = 100  # points

    # 4️⃣ Configure a visible shadow
    shadow = rectangle.shadow_format
    shadow.visible = True
    shadow.blur = 5.0
    shadow.distance = 3.0
    shadow.angle = 45
    shadow.color = aw.drawing.Color.black

    # 5️⃣ Add shape to the first paragraph
    paragraph = document.first_section.body.first_paragraph
    paragraph.append_child(rectangle)

    # 6️⃣ Save the document as PDF
    document.save(output_path)
    print(f"PDF successfully saved to: {output_path}")

if __name__ == "__main__":
    create_pdf_with_rectangle("output/shadow_rectangle.pdf")
```

Uruchomienie tego skryptu generuje `shadow_rectangle.pdf`, który wygląda tak:

![Diagram wygenerowanego PDF pokazujący kształt prostokąta po zapisaniu dokumentu jako pdf](placeholder-image.png)

*PDF zawiera jedną stronę z czarnym prostokątem z cieniem, wyśrodkowanym w dokumencie.*

## Częste pytania i przypadki brzegowe

| Pytanie | Odpowiedź |
|----------|-----------|
| **Czy mogę umieścić prostokąt w określonym miejscu?** | Tak. Ustaw `rectangle.left` i `rectangle.top` (w punktach) przed zapisem. |
| **Co jeśli potrzebuję wielu kształtów?** | Utwórz dodatkowe obiekty `Shape`, skonfiguruj każdy i dołącz je do tego samego lub różnych akapitów. |
| **Czy cień wpływa na rozmiar PDF?** | Tylko nieznacznie; cień jest przechowywany jako metadane wektorowe, a nie jako obraz rastrowy. |
| **Czy mogę użyć tego do konwersji istniejących plików *.docx*?** | Oczywiście. Zamień `aw.Document()` na `aw.Document("input.docx")`, a pozostałe kroki pozostaną niezmienione. |
| **Czy istnieje sposób na zmianę koloru wypełnienia prostokąta?** | Ustaw `rectangle.fill_color = aw.drawing.Color.light_blue` (lub dowolny `Color`, który preferujesz). |

## Kolejne kroki

Teraz, gdy wiesz jak **save document as PDF** z niestandardowym prostokątem, możesz zbadać:

* **Export Word to PDF** z nagłówkami, stopkami i numerami stron.  
* **Add other drawing objects** (`Ellipse`, `Polygon`) przy użyciu tej samej klasy `Shape`.  
* **Batch process** folder plików Word, stosując tę samą warstwę prostokąta do każdego.  

Te rozszerzenia podążają za tym samym schematem: utwórz kształt, skonfiguruj jego właściwości i **save document as pdf**.

---

**Podsumowanie:** Ten samouczek pokazał, jak **save document as PDF** jednocześnie **add rectangle shape**, **set rectangle dimensions** i zastosować niestandardowy cień przy użyciu Aspose.Words for Python. Pełny skrypt jest gotowy do skopiowania, uruchomienia i dostosowania do własnych potoków automatyzacji dokumentów. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Utwórz kształt prostokąta, dodaj cień i zapisz PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Dodaj prostokąt do PDF przy użyciu Aspose.Words – przewodnik krok po kroku](/words/english/python-net/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/)
- [Zapisz dokument jako PDF z Aspose.Words – kompletny przewodnik C#](/words/english/net/programming-with-pdfsaveoptions/save-document-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}