---
category: general
date: 2026-05-04
description: Dowiedz się, jak utworzyć kształt prostokąta, jak dodać kształt z cieniami,
  zmienić kolor cienia, ustawić odległość cienia oraz zapisać dokument jako PDF przy
  użyciu Aspose.Words dla Pythona.
draft: false
keywords:
- create rectangle shape
- how to add shape
- change shadow color
- save document as pdf
- set shadow distance
language: pl
og_description: Utwórz prostokątny kształt przy użyciu Aspose.Words dla Pythona, dowiedz
  się, jak dodać kształt, zmienić kolor cienia, ustawić odległość cienia i zapisać
  dokument jako PDF.
og_title: Utwórz kształt prostokąta – Dodaj cień, zmień kolor i zapisz jako PDF
tags:
- Aspose.Words
- Python
- PDF generation
title: Tworzenie kształtu prostokąta w Pythonie – Kompletny przewodnik po dodawaniu
  cieni i zapisywaniu jako PDF
url: /pl/python/images-shapes/create-rectangle-shape-in-python-full-guide-to-adding-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz kształt prostokąta – Kompletny samouczek dla programistów Pythona

Kiedykolwiek potrzebowałeś **create rectangle shape** w dokumencie Word i zastanawiałeś się, jak dodać mu elegancki cień? Być może tworzysz generator raportów i liczy się wizualna jakość — szczególnie gdy ostateczny wynik to PDF. Dobra wiadomość? Dzięki Aspose.Words for Python możesz nie tylko **how to add shape**, ale także dostroić każdą właściwość cienia, od koloru po odległość, a następnie **save document as pdf** w jednym płynnym procesie.

W tym przewodniku przejdziemy krok po kroku przez cały proces. Zobaczysz dokładny kod, który możesz skopiować‑wkleić, zrozumiesz *dlaczego* każda linia ma znaczenie i poznasz kilka wskazówek dotyczących przypadków brzegowych (np. przezroczyste cienie lub niestandardowe DPI). Po zakończeniu będziesz w stanie **create rectangle shape**, dostosować jego cień i wyeksportować wyraźny PDF bez problemu.

## Prerequisites

- Python 3.8+ zainstalowany na Twoim komputerze.  
- Aspose.Words for Python poprzez `pip install aspose-words`.  
- Podstawowa znajomość programowania obiektowego w Pythonie (nic skomplikowanego).  

Jeśli masz już skonfigurowane wirtualne środowisko, po prostu uruchom polecenie instalacji i jesteś gotowy do działania.

## Step 1: Initialise the Document and Builder

Zanim będziesz mógł **how to add shape**, potrzebujesz pustego dokumentu, na którym będziesz pracować. Klasa `Document` reprezentuje cały plik, a `DocumentBuilder` jest Twoim pędzlem.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder to edit it
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

*Why this matters:* `Document` przechowuje wszystkie sekcje, strony i zasoby. `DocumentBuilder` zapewnia płynne API do wstawiania treści dokładnie tam, gdzie tego potrzebujesz — można to porównać do kursora w edytorze tekstu.

## Step 2: Insert the Rectangle Shape

Teraz faktycznie **how to add shape**. Metoda `insert_shape` wymaga typu kształtu oraz jego wymiarów (w punktach). Tutaj wybieramy prostokąt 200 × 100 pt i nadajemy mu wypełnienie jasnoniebieskim kolorem.

```python
# Step 2: Insert a rectangle shape and give it a light‑blue fill
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,  # shape type
    200,                            # width in points
    100)                            # height in points
rectangle_shape.fill_color = aw.Color.light_blue
```

*Pro tip:* Jeśli potrzebujesz, aby kształt był wyrównany do istniejącego tekstu, użyj `builder.move_to` przed wstawieniem lub dostosuj właściwości `left`/`top` po utworzeniu.

## Step 3: Turn the Shadow On

Kształt bez cienia wygląda płasko. Aby **set shadow distance** i uczynić efekt widocznym, pobierz format cienia i włącz go.

```python
# Step 3: Access the shape's shadow format and make the shadow visible
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
```

*Why this step:* Format cienia jest osobnym obiektem; przełączenie `visible` to pierwsza rzecz, którą musisz zrobić, w przeciwnym razie wszystkie pozostałe właściwości cienia są ignorowane.

## Step 4: Style the Shadow – Colour, Blur, Distance, Direction

Tutaj dzieje się magia. **change shadow color**, dostosujemy promień rozmycia, ustawimy, jak daleko cień znajduje się od prostokąta, i obrócimy go o 45°.

```python
# Step 4: Configure the appearance of the shadow
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER   # outer shadow
rectangle_shadow.blur_radius = 10.0                    # blur amount (pixels)
rectangle_shadow.distance = 5.0                        # distance from the shape
rectangle_shadow.direction = 45.0                     # angle in degrees
rectangle_shadow.color = aw.Color.gray                 # shadow colour
```

*Explanation of each property:*

| Property | What it does | Typical values |
|----------|--------------|----------------|
| `style` | Określa, czy cień jest *inner* (wewnętrzny) czy *outer* (zewnętrzny). | `OUTER` (najczęściej) |
| `blur_radius` | Kontroluje miękkość; wyższa wartość = bardziej rozmyte krawędzie. | 0–20 px to typowy zakres |
| `distance` | Jak daleko cień jest odsunięty od kształtu. | 0–10 pt dla subtelnego, >10 dla dramatycznego |
| `direction` | Kąt źródła światła, mierzony zgodnie z ruchem wskazówek zegara od osi x. | 0‑360° |
| `color` | Odcień cienia. | Dowolny `aw.Color` (np. `gray`, `dark_red`) |

*Edge case:* Jeśli ustawisz `distance` na `0`, cień znajdzie się bezpośrednio pod kształtem, skutecznie ukrywając wypełnienie kształtu. Utrzymaj wartość powyżej `0`, aby uzyskać widoczny offset.

## Step 5: Save the Document as a PDF

Na koniec **save document as pdf**. Aspose.Words automatycznie rasteryzuje cień, więc PDF wygląda dokładnie tak jak podgląd w Wordzie.

```python
# Step 5: Save the document as a PDF with the shadowed shape
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

*Why PDF?* PDF‑y zachowują układ na różnych platformach, co czyni je idealnymi do raportów, faktur czy innych drukowanych artefaktów.

---

![Create rectangle shape with shadow](https://example.com/images/rectangle-shadow.png){: .align-center alt="przykład prostokąta z cieniowaniem"}

*Powyższy obrazek przedstawia końcowy wynik w PDF — jasnoniebieski prostokąt z delikatnym szarym cieniem zewnętrznym, dokładnie tak skonfigurowany, jak opisano.*

## Common Questions & Variations

### What if I need a **transparent** shadow?

Ustaw kanał alfa w kolorze cienia:

```python
transparent_gray = aw.Color.from_argb(128, 0, 0, 0)  # 50% opacity black
rectangle_shadow.color = transparent_gray
```

### Can I apply the same shadow to multiple shapes?

Tak. Pobierz `ShadowFormat` z jednego kształtu i przypisz go do innego:

```python
another_shape = builder.insert_shape(aw.drawing.ShapeType.ELLIPSE, 150, 150)
another_shape.shadow_format = rectangle_shadow.clone()
```

### How do I change the shadow for a **different shape type**?

Wszystkie typy kształtów korzystają z tych samych właściwości `ShadowFormat`, więc możesz ponownie użyć tego samego bloku konfiguracji — po prostu zamień `ShapeType.RECTANGLE` na `ShapeType.OVAL`, `ShapeType.TRIANGLE` itp.

### What about **high‑resolution PDFs** for print?

Określ `PdfSaveOptions` z wyższym DPI:

```python
options = aw.saving.PdfSaveOptions()
options.image_resolution = 300  # 300 DPI for print quality
document.save(output_path, options)
```

## Recap

Omówiliśmy wszystko, co potrzebne, aby **create rectangle shape**, **how to add shape**, dostosować **shadow colour**, **set shadow distance**, a na końcu **save document as pdf**. Pełny, gotowy do uruchomienia skrypt wygląda tak:

```python
import aspose.words as aw

# Initialise document
document = aw.Document()
builder = aw.DocumentBuilder(document)

# Insert rectangle shape
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle_shape.fill_color = aw.Color.light_blue

# Enable and style shadow
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER
rectangle_shadow.blur_radius = 10.0
rectangle_shadow.distance = 5.0
rectangle_shadow.direction = 45.0
rectangle_shadow.color = aw.Color.gray

# Save as PDF
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Uruchom skrypt, otwórz wygenerowany plik `ShadowedShape.pdf` i zobaczysz wyraźny prostokąt z subtelnym szarym cieniem — dokładnie to, czego oczekujesz od profesjonalnie sformatowanego raportu.

## What Next?

- **Explore other shape types** (`ShapeType.OVAL`, `ShapeType.LINE`), aby wzbogacić swoje dokumenty.  
- **Combine multiple shadows** poprzez nakładanie kształtów; możesz nawet stworzyć efekt „glow”, używając wewnętrznego cienia w jasnym kolorze.  
- **Automate batch processing**: iteruj po kolekcji wierszy danych, generuj kształt dla każdego wiersza i scal wszystko w jeden PDF.  
- **Integrate with other Aspose libraries** (np. Aspose.Slides), jeśli potrzebujesz wyeksportować tę samą wizualizację do PowerPointa.

Śmiało eksperymentuj — zmieniaj `blur_radius`, baw się `direction` lub zamień `gray` na odcień charakterystyczny dla Twojej marki. API jest na tyle elastyczne, że kilka drobnych zmian może znacząco wpłynąć na efekt wizualny.

Masz pytania lub trudny scenariusz? zostaw komentarz poniżej lub napisz na forach społeczności Aspose. Szczęśliwego kodowania i ciesz się pięknie cieniowanymi prostokątami!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}