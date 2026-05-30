---
category: general
date: 2026-05-30
description: Jak wstawić prostokąt i dodać cień w Wordzie przy użyciu Aspose – krok
  po kroku przewodnik w Pythonie, jak stworzyć dokument Word z efektem cienia kształtu.
draft: false
keywords:
- how to insert rectangle
- add shadow to shape
- how to add shape shadow
- apply shadow effect word
- create word document aspose
language: pl
og_description: Jak wstawić prostokąt i dodać cień w Wordzie przy użyciu Aspose –
  dowiedz się, jak stworzyć dokument Word z efektem cienia kształtu w Pythonie.
og_title: Jak wstawić prostokąt i dodać cień w Wordzie przy użyciu Aspose
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: How to insert rectangle and add shadow in Word using Aspose – a step‑by‑step
    Python guide to create a Word document with shape shadow effect.
  headline: How to insert rectangle and add shadow in Word using Aspose
  type: TechArticle
- description: How to insert rectangle and add shadow in Word using Aspose – a step‑by‑step
    Python guide to create a Word document with shape shadow effect.
  name: How to insert rectangle and add shadow in Word using Aspose
  steps:
  - name: What each property does
    text: '| Property | Effect | Typical Range | |----------|--------|---------------|
      | `visible` | Turns the shadow on/off | `True` / `False` | | `distance` | How
      far the shadow sits from the shape | 2 – 10 pts | | `blur` | Softness of the
      shadow edges | 4 – 12 pts | | `color` | Shadow hue; dark gray is a sa'
  - name: Adding Multiple Shapes
    text: If you need more than one rectangle, simply repeat the `insert_shape` call.
      Remember to move the builder’s cursor (`builder.move_to(shape)`) or adjust `shape.left`/`shape.top`
      to avoid overlap.
  - name: Changing the Shape Type
    text: While this guide focuses on rectangles, the same pattern works for ovals,
      stars, or custom free‑form shapes. Replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`,
      `ShapeType.CLOUD`, etc., and the shadow settings remain identical.
  - name: Saving to Other Formats
    text: 'Aspose.Words can export to PDF, PNG, or even XPS with a single line:'
  - name: Handling Large Documents
    text: When generating massive reports, consider calling `doc.update_page_layout()`
      after inserting all shapes. This forces a layout pass and can improve performance
      when you later convert to PDF.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word Automation
title: Jak wstawić prostokąt i dodać cień w Wordzie przy użyciu Aspose
url: /pl/python/images-shapes/how-to-insert-rectangle-and-add-shadow-in-word-using-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak wstawić prostokąt i dodać cień w Wordzie przy użyciu Aspose

Zastanawiałeś się kiedyś **jak wstawić prostokąt** do pliku Word bez otwierania interfejsu? Nie jesteś sam. Wielu programistów musi generować raporty, faktury lub certyfikaty w locie, a narysowanie prostego prostokąta z ładnym cieniem może sprawić, że wynik będzie wyglądał profesjonalnie. W tym samouczku przeprowadzimy Cię przez dokładne kroki tworzenia dokumentu Word, wstawienia kształtu prostokąta i zastosowania realistycznego cienia przy użyciu Aspose.Words dla Pythona.

Omówimy wszystko, od konfiguracji pakietu Aspose po dostosowanie odległości, rozmycia i nieprzezroczystości cienia. Po zakończeniu będziesz mieć wielokrotnego użytku fragment kodu, który możesz wkleić do dowolnego potoku automatyzacji. Bez magii, tylko przejrzysty kod i kilka praktycznych wskazówek.

## Wymagania wstępne

- Python 3.8+ zainstalowany (kod działa na 3.9, 3.10 i nowszych)
- Aktywna licencja Aspose.Words for Python lub darmowy klucz ewaluacyjny
- pakiet `aspose-words` zainstalowany za pomocą `pip install aspose-words`
- Zapisywalny folder, w którym zostanie zapisany wygenerowany **create word document aspose**

To wszystko — bez dodatkowych DLL‑ów, bez interfejsu COM, tylko czysty Python.

## Krok 1: Inicjalizacja dokumentu (How to create word document aspose)

Na początek potrzebujesz nowego obiektu `Document`. Traktuj go jak czyste płótno. Poniższy kod tworzy dokument oraz `DocumentBuilder`, który pozwoli nam wstawiać kształty.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

*Dlaczego to ważne:* `DocumentBuilder` zapewnia wysokopoziomowe API do dodawania akapitów, tabel i — tak — kształtów bez konieczności pracy z niskopoziomowymi drzewami węzłów. Jeśli ominiesz builder i będziesz manipulować węzłami bezpośrednio, skończysz z rozbudowanym kodem, który jest trudniejszy w utrzymaniu.

## Krok 2: Wstawienie prostokąta (how to insert rectangle)

Teraz faktycznie **how to insert rectangle**. Aspose.Words traktuje prostokąt jako ogólny typ kształtu. Określasz szerokość i wysokość w punktach (1 punkt ≈ 1/72 cala). Śmiało dostosuj liczby do swojego układu.

```python
# Step 2: Insert a rectangle shape of the desired size
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

> **Pro tip:** Jeśli potrzebujesz, aby prostokąt był umieszczony w określonym miejscu na stronie, ustaw `shape.left` i `shape.top` po wstawieniu. Daje to kontrolę z dokładnością do piksela.

## Krok 3: Dostęp do formatu cienia kształtu (add shadow to shape)

Wygląd kształtu znajduje się w jego `ShadowFormat`. Pobierając go, uzyskujemy dostęp do każdej właściwości definiującej wygląd cienia.

```python
# Step 3: Access the shape's shadow format
shadow = shape.shadow_format
```

Na tym etapie cień jest niewidoczny — traktuj go jak ukrytą warstwę czekającą na Twoje instrukcje.

## Krok 4: Konfiguracja cienia (how to add shape shadow, apply shadow effect word)

Tutaj dzieje się magia. Włączymy cień i dostosujemy jego wygląd. Poniższe wartości generują miękki, diagonalny cień, który dobrze sprawdza się w większości dokumentów, ale możesz eksperymentować.

```python
# Step 4: Make the shadow visible and configure its appearance
shadow.visible = True                # Show the shadow
shadow.distance = 5.0                # Distance from the shape (points)
shadow.blur = 8.0                    # Blur radius (points)
shadow.color = aw.Color.dark_grey   # Shadow color
shadow.opacity = 0.6                 # Opacity (0‑1)
shadow.angle = 45.0                  # Direction in degrees
```

### Co robi każda właściwość

| Właściwość | Efekt | Typowy zakres |
|------------|-------|----------------|
| `visible` | Włącza/wyłącza cień | `True` / `False` |
| `distance` | Jak daleko cień znajduje się od kształtu | 2 – 10 pts |
| `blur` | Miękkość krawędzi cienia | 4 – 12 pts |
| `color` | Odcień cienia; ciemny szary to bezpieczna domyślna wartość | Any `aw.Color` |
| `opacity` | Przezroczystość; 0 = niewidoczny, 1 = pełny | 0.3 – 0.8 dla subtelnego wyglądu |
| `angle` | Kierunek, z którego pada światło | 0 – 360° |

**Dlaczego je dostosowywać?** Dobrze dobrany cień może sprawić, że płaski prostokąt będzie wyglądał, jakby unosił się nad stroną, dodając głębi bez użycia obrazów. Jeśli ustawisz `opacity` zbyt wysoko, cień będzie ostry; zbyt nisko i zniknie.

## Krok 5: Zapis dokumentu (create word document aspose)

Na koniec zapisz plik na dysku. Możesz użyć dowolnego rozszerzenia obsługiwanego przez Aspose.Words (`.docx`, `.pdf`, `.html`). W tym samouczku pozostaniemy przy `.docx`.

```python
# Step 5: Save the document with the shaped shadow
output_path = "output/ShapeWithShadow.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Otwórz powstały plik w Microsoft Word i zobaczysz wyraźny prostokąt z subtelnym cieniem — dokładnie to, czego oczekujesz od profesjonalnie zaprojektowanego szablonu.

![jak wstawić prostokątny kształt z cieniem przy użyciu Aspose.Words](/images/rectangle-shadow.png){alt="jak wstawić prostokątny kształt z cieniem przy użyciu Aspose.Words"}

*Zrzut ekranu (powyżej) pokazuje prostokąt z zastosowanym cieniem. Zauważ delikatne rozmycie i kąt 45°, który nadaje naturalny wygląd.*

## Typowe warianty i przypadki brzegowe

### Dodawanie wielu kształtów

Jeśli potrzebujesz więcej niż jednego prostokąta, po prostu powtórz wywołanie `insert_shape`. Pamiętaj, aby przesunąć kursor buildera (`builder.move_to(shape)`) lub dostosować `shape.left`/`shape.top`, aby uniknąć nakładania się.

```python
# Example: Insert a second rectangle 200 points to the right
second_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
second_shape.left = shape.left + 200
second_shape.top = shape.top
```

### Zmiana typu kształtu

Choć ten przewodnik koncentruje się na prostokątach, ten sam schemat działa dla owalów, gwiazd lub niestandardowych kształtów wolnej formy. Zamień `ShapeType.RECTANGLE` na `ShapeType.OVAL`, `ShapeType.CLOUD` itp., a ustawienia cienia pozostaną identyczne.

### Zapisywanie w innych formatach

Aspose.Words może eksportować do PDF, PNG lub nawet XPS jedną linią:

```python
doc.save("output/ShapeWithShadow.pdf")
```

Renderowanie cienia jest zachowane we wszystkich formatach, więc Twój PDF będzie wyglądał tak samo jak plik Word.

### Obsługa dużych dokumentów

Podczas generowania ogromnych raportów rozważ wywołanie `doc.update_page_layout()` po wstawieniu wszystkich kształtów. To wymusza przebieg układu i może poprawić wydajność przy późniejszej konwersji do PDF.

## Pełny działający przykład (wszystkie kroki połączone)

Poniżej znajduje się kompletny skrypt, który możesz skopiować i wkleić do pliku o nazwie `rectangle_shadow.py`. Uruchom go poleceniem `python rectangle_shadow.py` i sprawdź folder `output`.

```python
import aspose.words as aw
import os

# Ensure the output directory exists
os.makedirs("output", exist_ok=True)

# Initialize the document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

# Configure the shadow
shadow = shape.shadow_format
shadow.visible = True
shadow.distance = 5.0
shadow.blur = 8.0
shadow.color = aw.Color.dark_grey
shadow.opacity = 0.6
shadow.angle = 45.0

# Save the document
output_path = "output/ShapeWithShadow.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Uruchomienie tego skryptu generuje dokładnie ten sam dokument, o którym rozmawialiśmy wcześniej. Śmiało modyfikuj liczby; kod jest celowo prosty, abyś mógł eksperymentować bez obaw.

## Najczęściej zadawane pytania

**Q: Czy działa to na Linuxie?**


## Co powinieneś nauczyć się dalej?

- [Utwórz dokument Word w Java – Dodaj prostokątny kształt z efektem cienia](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Utwórz pusty dokument Word z prostokątnym kształtem z cieniem – przewodnik krok po kroku](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Samouczek cienia kształtu Aspose.Words – Dodaj cień do kształtu Word w C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}