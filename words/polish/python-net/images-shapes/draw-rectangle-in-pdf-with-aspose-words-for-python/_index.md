---
category: general
date: 2026-08-07
description: Rysuj prostokąt w pliku PDF przy użyciu Aspose.Words dla Pythona i dowiedz
  się, jak dodać cień do kształtu, skonfigurować cień kształtu oraz zapisać dokument
  jako PDF.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle in pdf
- add shadow to shape
- save document as pdf
- configure shape shadow
language: pl
lastmod: 2026-08-07
og_description: Rysuj prostokąt w PDF za pomocą Aspose.Words dla Pythona. Ten samouczek
  pokazuje, jak dodać cień do kształtu, skonfigurować cień kształtu oraz zapisać dokument
  jako PDF w celu profesjonalnego generowania dokumentów.
og_image_alt: PDF page showing a rectangle shape with a visible shadow created by
  Aspose.Words for Python
og_title: Rysowanie prostokąta w PDF przy użyciu Aspose.Words dla Pythona – przewodnik
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Draw rectangle in PDF using Aspose.Words for Python and learn how to
    add shadow to shape, configure shape shadow, and save document as PDF.
  headline: Draw rectangle in PDF with Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF
- Shape
- Shadow
title: Rysowanie prostokąta w PDF przy użyciu Aspose.Words dla Pythona
url: /pl/python/images-shapes/draw-rectangle-in-pdf-with-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rysowanie prostokąta w PDF przy użyciu Aspose.Words for Python

Jeśli potrzebujesz **rysować prostokąt w PDF** pracując w Pythonie, ten przewodnik dostarczy Ci kompletne, gotowe do uruchomienia rozwiązanie. Zobaczysz dokładnie, jak **dodać cień do kształtu**, skonfigurować ten cień i w końcu **zapisać dokument jako PDF** do dystrybucji lub archiwizacji.

Tworzenie cieniowanego prostokąta to częsty wymóg w raportach, fakturach czy adnotacjach wizualnych. Po zakończeniu tego samouczka będziesz mieć pojedynczy skrypt, który generuje PDF zawierający prostokąt z realistycznym cieniem, a także zrozumiesz, jak dostosować rozmiar, kolor i offset, aby pasowały do dowolnego projektu.

## Wymagania wstępne

Zanim rozpoczniesz, upewnij się, że masz:

* Zainstalowany Python 3.8+.
* Pakiet Aspose.Words for Python via .NET (`aspose-words`) – zainstaluj za pomocą:

```bash
pip install aspose-words
```

* Uprawnienia do zapisu w folderze, w którym zamierzasz zapisać PDF.

Nie są wymagane dodatkowe biblioteki; Aspose.Words obsługuje tworzenie kształtów, konfigurację cienia i eksport do PDF wewnętrznie.

## Krok 1: Utwórz nowy pusty dokument (rysowanie prostokąta w PDF – inicjalizacja)

Pierwszym krokiem jest utworzenie obiektu `Document`. Obiekt ten reprezentuje cały plik PDF i zapewnia kontener dla sekcji, akapitów i kształtów.

```python
import aspose.words as aw

# Create an empty Word document – it will become a PDF later
doc = aw.Document()
```

**Dlaczego to ważne:** Aspose.Words traktuje generowanie PDF jako konwersję z modelu dokumentu Word, więc zaczynamy od `Document`, mimo że ostatecznym wynikiem jest PDF.

## Krok 2: Wstaw kształt prostokąta do ciała dokumentu

Prostokąt to określony `ShapeType`. Dodajemy go do ciała pierwszej sekcji, co automatycznie tworzy nową stronę przy zapisie jako PDF.

```python
# Append a rectangle shape to the first section's body
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Set the rectangle's dimensions (points = 1/72 inch)
rectangle.width = 200   # 200 pt ≈ 2.78 in
rectangle.height = 100  # 100 pt ≈ 1.39 in

# Optional: give the shape some visible text
rectangle.text = "Shadow demo"
```

**Wyjaśnienie:** Właściwości `width` i `height` kontrolują wizualny rozmiar kształtu w PDF. Dodanie tekstu ułatwia weryfikację prostokąta podczas testów.

## Krok 3: Dodaj cień do kształtu – włącz i dostosuj

Teraz włączamy efekt cienia i precyzyjnie dopasowujemy jego wygląd. To właśnie tutaj wchodzi w grę fraza **add shadow to shape**.

```python
# Access the shape's shadow effect object
shadow = rectangle.shadow_effect

# Make the shadow visible
shadow.visible = True

# Configure blur radius (pt) – higher values produce a softer edge
shadow.blur = 8

# Set the distance (offset) from the shape in points
shadow.distance = 5

# Define the direction of the shadow in degrees (0 = right, 90 = down)
shadow.angle = 45

# Choose a shadow color – black works for most documents
shadow.color = aw.drawing.Color.black
```

**Dlaczego konfigurować cień kształtu?** Dostosowanie `blur`, `distance` i `angle` pozwala symulować realistyczne oświetlenie, co poprawia czytelność i hierarchię wizualną w generowanych PDF‑ach.

## Krok 4: Zapisz dokument jako PDF – wynik końcowy

Po zdefiniowaniu prostokąta i jego cienia, ostatnim krokiem jest wyeksportowanie dokumentu Word do PDF. Spełnia to wymóg **save document as pdf**.

```python
# Define the output path – replace YOUR_DIRECTORY with an actual folder
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)
print(f"PDF saved to {output_path}")
```

Po otwarciu `shadow_rectangle.pdf` zobaczysz jedną stronę zawierającą szary prostokąt o obramowaniu, zatytułowany „Shadow demo”, z wyraźnym, skośnym cieniem.

### Oczekiwany wynik

* Plik PDF o nazwie `shadow_rectangle.pdf`.
* Jedna strona z prostokątem 200 pt × 100 pt.
* Widoczny cień przesunięty o 5 pt pod kątem 45°, rozmyty o 8 pt.

## Krok 5: Eksploruj warianty i przypadki brzegowe (opcjonalnie)

Poniżej znajdują się typowe modyfikacje, które mogą być potrzebne w rzeczywistych projektach:

| Wariant | Fragment kodu | Kiedy używać |
|-----------|--------------|-------------|
| **Inny typ kształtu** (np. elipsa) | `aw.drawing.ShapeType.OVAL` zamiast `RECTANGLE` | Dla zaokrąglonych grafik lub odznak |
| **Niestandardowy kolor cienia** | `shadow.color = aw.drawing.Color.from_argb(255, 100, 100, 100)` | Gdy potrzebny jest szary lub specyficzny dla marki cień |
| **Wiele kształtów** | Powtórz blok tworzenia kształtu i dostosuj właściwości `left`/`top` | Do budowy złożonych diagramów |
| **Brak tekstu wewnątrz kształtu** | Pomiń `rectangle.text = "..."` | Gdy kształt ma pełnić wyłącznie funkcję dekoracyjną |
| **Wyjście o wyższej rozdzielczości DPI** | `doc.save(output_path, aw.SaveFormat.PDF, aw.PdfSaveOptions())` z ustawionymi opcjami `PdfSaveOptions` dla jakości obrazu | Dla PDF‑ów gotowych do druku |

**Wskazówka:** Zawsze ustaw `shadow.visible = True` przed modyfikacją innych właściwości; w przeciwnym razie zmiany zostaną zignorowane.

## Pełny skrypt – kopiuj, wklej i uruchom

```python
import aspose.words as aw

# 1️⃣ Create a new blank document
doc = aw.Document()

# 2️⃣ Add a rectangle shape
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
rectangle.width = 200          # width in points
rectangle.height = 100         # height in points
rectangle.text = "Shadow demo"

# 3️⃣ Configure a visible shadow effect
shadow = rectangle.shadow_effect
shadow.visible = True
shadow.blur = 8                # blur radius (pt)
shadow.distance = 5            # offset distance (pt)
shadow.angle = 45              # direction (degrees)
shadow.color = aw.drawing.Color.black

# 4️⃣ Save the document as a PDF
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)

print(f"PDF successfully created at: {output_path}")
```

Uruchom skrypt w terminalu lub IDE. Zastąp `YOUR_DIRECTORY` rzeczywistą ścieżką folderu, np. `"/tmp"` lub `"C:\\Users\\Me\\Documents"`.

## Podsumowanie

Teraz wiesz, jak **rysować prostokąt w PDF** używając Aspose.Words for Python, **dodać cień do kształtu**, **skonfigurować cień kształtu** oraz **zapisać dokument jako PDF**. Pełny przykład demonstruje każdy krok od tworzenia dokumentu po ostateczny eksport, a opcjonalne warianty pokazują, jak dostosować kod do bardziej złożonych scenariuszy.

Następnie możesz zgłębić:

* Dodawanie innych typów kształtów (`ShapeType.LINE`, `ShapeType.ELLIPSE`).
* Stosowanie wypełnień gradientowych lub obramowań w celu zwiększenia atrakcyjności wizualnej.
* Użycie `PdfSaveOptions` do osadzania czcionek lub kontrolowania kompresji obrazów.

Śmiało eksperymentuj z parametrami, aby dopasować je do swojej marki lub wytycznych projektowych. Miłego skryptowania PDF!


## Co powinieneś nauczyć się dalej?


Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każde z nich zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, pomagające opanować dodatkowe funkcje API i poznać alternatywne podejścia implementacyjne w własnych projektach.

- [Optimize PDF Bookmarks Using Aspose.Words for Python](/words/english/python-net/performance-optimization/optimize-pdf-bookmarks-aspose-words-python/)
- [Optimize Pdf Loading Python Aspose Words Skip Images](/words/hindi/python-net/performance-optimization/optimize-pdf-loading-python-aspose-words-skip-images/)
- [Aspose Words Python Pdf Manipulation](/words/hongkong/python-net/document-operations/aspose-words-python-pdf-manipulation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}