---
category: general
date: 2026-06-24
description: Utwórz prostokątny kształt w Pythonie przy użyciu Aspose.Words, dowiedz
  się, jak dodać cień do kształtu, ustawić kąt cienia i zapisać dokument jako PDF
  w kilka minut.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shape shadow
- set shadow angle
language: pl
og_description: Utwórz prostokątny kształt w Pythonie, dodaj cień do kształtu, ustaw
  kąt cienia i zapisz dokument jako PDF przy użyciu Aspose.Words. Postępuj zgodnie
  z tym przewodnikiem krok po kroku.
og_title: Utwórz prostokątny kształt w Pythonie – Pełny samouczek Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  headline: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  name: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: What if I need a different shape?
    text: Aspose.Words supports many `ShapeType` values (ellipse, star, callout, etc.).
      Simply replace `aw.drawing.ShapeType.RECTANGLE` with the desired enum, like
      `aw.drawing.ShapeType.ELLIPSE`.
  - name: Can I add multiple shadows?
    text: The API exposes only one `ShadowFormat` per shape, but you can simulate
      multiple shadows by duplicating the shape, offsetting each copy, and adjusting
      transparency.
  - name: How do I change the shadow color to match my brand?
    text: Just set `shadow.color` to any `aw.drawing.Color`. For a brand blue, use
      `aw.drawing.Color.from_argb(255, 0, 120, 215)`.
  - name: What about saving as DOCX instead of PDF?
    text: Replace `document.save(pdf_path)` with `document.save("output/shadowed_rectangle.docx")`.
      The shadow rendering is preserved across both formats.
  - name: Does the shadow work on older PDF viewers?
    text: Aspose.Words renders the shadow as a vector effect, which is widely supported.
      However, very old viewers might flatten the effect; testing on your target audience’s
      devices is always a good habit.
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Utwórz prostokątny kształt w Pythonie – Kompletny przewodnik Aspose.Words
url: /pl/python/images-shapes/create-rectangle-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz kształt prostokąta w Pythonie – Kompletny przewodnik Aspose.Words

Zastanawiałeś się kiedyś, jak **utworzyć kształt prostokąta** w dokumencie Word przy użyciu Pythona? Być może potrzebujesz wyraźnego pola wyróżnienia, wizualnej wskazówki dla diagramu lub po prostu eleganckiego prostokąta do raportu. Niezależnie od powodu, trafiłeś we właściwe miejsce. W tym samouczku przeprowadzimy Cię przez cały proces — od wstawienia prostokąta, przez dodanie subtelnego cienia, dostosowanie kąta cienia, aż po **zapisanie dokumentu jako PDF**, abyś mógł go udostępnić każdemu.

Będziemy korzystać z **Aspose.Words for Python via .NET**, potężnej biblioteki, która pozwala manipulować plikami Word bez konieczności uruchamiania samego Worda. Po zakończeniu tego przewodnika będziesz w stanie pewnie odpowiedzieć na pytanie *„jak dodać cień do kształtu”* i będziesz mieć gotowy skrypt, który możesz wkleić do dowolnego projektu.

---

## Co będzie potrzebne

Zanim zaczniemy, upewnij się, że masz następujące elementy:

- **Python 3.8+** zainstalowany na Twoim komputerze.  
- **Aspose.Words for Python via .NET** (pakiet `aspose-words`). Zainstaluj go poleceniem:

  ```bash
  pip install aspose-words
  ```

- Folder, do którego można zapisywać pliki, w którym zostanie zapisany wygenerowany PDF.  
- (Opcjonalnie) IDE lub edytor tekstu — VS Code sprawdzi się doskonale.

To wszystko. Bez dodatkowych DLL‑ów, bez instalacji Office, tylko jeden pakiet pip.

---

## Krok 1: Przygotowanie dokumentu i buildera

Pierwszą rzeczą, którą musisz zrobić, jest **utworzenie obiektów przyjaznych dla kształtu prostokąta**: `Document` i `DocumentBuilder`. Pomyśl o builderze jak o piórze; rysuje wszystko za Ciebie.

```python
import aspose.words as aw

# Initialize a new blank document
document = aw.Document()

# DocumentBuilder gives us a convenient way to add content
builder = aw.DocumentBuilder(document)
```

> **Dlaczego to ważne:** Obiekt `Document` reprezentuje cały plik .docx, natomiast `DocumentBuilder` udostępnia metody takie jak `insert_shape`, które ułatwiają rysowanie kształtów.

---

## Krok 2: Wstawienie kształtu prostokąta

Mając już builder, możemy w końcu **utworzyć kształt prostokąta**. Metoda `insert_shape` wymaga trzech argumentów: typu kształtu, szerokości i wysokości. Użyjemy szerokości 200 pt i wysokości 100 pt, aby uzyskać ładne proporcje.

```python
# Insert a rectangle with a width of 200 points and a height of 100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

W tym momencie udało Ci się **utworzyć kształt prostokąta** w dokumencie. Jeśli otworzysz wygenerowany DOCX (zrobimy to później), zobaczysz zwykły prostokąt znajdujący się tam, gdzie znajdował się kursor.

---

## Krok 3: Dostęp do obiektu formatowania cienia

Aby **dodać cień do kształtu**, najpierw musimy pobrać formatowanie cienia kształtu. Każdy kształt w Aspose.Words posiada właściwość `shadow_format`, która udostępnia wszystkie ustawienia związane z cieniem.

```python
# Grab the shadow formatting object for later tweaks
shadow = rectangle.shadow_format
```

Posiadanie referencji do `shadow` pozwala nam przełączać widoczność, rozmycie, odległość, kąt, kolor i przezroczystość — wszystko w kilku linijkach kodu.

---

## Krok 4: Włączenie cienia i skonfigurowanie jego wyglądu

Teraz następuje magia. **Dodamy cień do kształtu**, lekko go rozmyjemy, nieco przesuniemy, ustawimy kierunek (część **ustawiania kąta cienia**) i nadamy mu półprzezroczysty czarny odcień.

```python
# Turn the shadow on
shadow.visible = True

# Soften the edges – a blur radius of 8 points looks natural
shadow.blur_radius = 8.0

# Push the shadow away from the rectangle by 5 points
shadow.distance = 5.0

# Set the direction of the light source – 45 degrees creates a diagonal drop
shadow.angle = 45

# Choose a color; black works well for most documents
shadow.color = aw.drawing.Color.black

# Make the shadow 30 % transparent for a subtle effect
shadow.transparency = 0.3
```

> **Wskazówka:** Jeśli potrzebujesz bardziej dramatycznego efektu, zwiększ `blur_radius` lub zmniejsz `transparency`. Odwrotnie, ostry, w pełni nieprzezroczysty cień uzyskasz, ustawiając `blur_radius = 0` i `transparency = 0`.

---

## Krok 5: Zapisanie dokumentu jako PDF

Utworzyliśmy **kształt prostokąta**, **dodaliśmy cień do kształtu**, a teraz **zapiszemy dokument jako PDF**, aby rezultat wyglądał identycznie na każdym urządzeniu. Aspose.Words robi to w jednej linijce.

```python
# Define where you want the PDF to land
output_path = "output/shadowed_rectangle.pdf"

# Save the whole document (including the rectangle with its shadow) as PDF
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Uruchomienie skryptu wygeneruje plik `shadowed_rectangle.pdf` w folderze `output`. Otwórz go w dowolnym przeglądarce PDF i zobaczysz czysty prostokąt z miękkim, 45‑stopniowym cieniem — dokładnie takim, jaki skonfigurowaliśmy.

---

## Pełny działający przykład

Poniżej znajduje się kompletny, gotowy do uruchomienia skrypt, który łączy wszystkie powyższe kroki. Skopiuj go do pliku o nazwie `create_rectangle_with_shadow.py` i uruchom poleceniem `python create_rectangle_with_shadow.py`.

```python
import aspose.words as aw
import os

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Initialize document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert the rectangle shape (200 pt × 100 pt)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Access shadow formatting
shadow = rectangle.shadow_format

# 4️⃣ Configure shadow – visible, blurred, offset, angled, colored, semi‑transparent
shadow.visible = True
shadow.blur_radius = 8.0          # softer edges
shadow.distance = 5.0            # how far the shadow sits from the shape
shadow.angle = 45                # direction in degrees – this is the **set shadow angle** step
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.3        # 30 % transparent

# 5️⃣ Save the document as PDF
pdf_path = os.path.join(output_dir, "shadowed_rectangle.pdf")
document.save(pdf_path)

print(f"✅ PDF created at: {pdf_path}")
```

**Oczekiwany wynik:** Plik PDF pokazujący pojedynczy prostokąt z delikatnym, ukośnym cieniem. Bez dodatkowych stron, bez ukrytych artefaktów — po prostu kształt, który stworzyłeś.

---

## Często zadawane pytania i sytuacje brzegowe

### Co zrobić, jeśli potrzebuję innego kształtu?

Aspose.Words obsługuje wiele wartości `ShapeType` (elipsa, gwiazda, dymek itp.). Po prostu zamień `aw.drawing.ShapeType.RECTANGLE` na żądany enum, np. `aw.drawing.ShapeType.ELLIPSE`.

### Czy mogę dodać wiele cieni?

API udostępnia tylko jeden `ShadowFormat` na kształt, ale możesz zasymulować wiele cieni, duplikując kształt, przesuwając każdą kopię i dostosowując przezroczystość.

### Jak zmienić kolor cienia, aby pasował do mojej marki?

Wystarczy ustawić `shadow.color` na dowolny `aw.drawing.Color`. Dla niebieskiego marki użyj `aw.drawing.Color.from_argb(255, 0, 120, 215)`.

### A co z zapisem jako DOCX zamiast PDF?

Zamień `document.save(pdf_path)` na `document.save("output/shadowed_rectangle.docx")`. Renderowanie cienia jest zachowane w obu formatach.

### Czy cień działa w starszych przeglądarkach PDF?

Aspose.Words renderuje cień jako efekt wektorowy, który jest szeroko wspierany. Jednak bardzo stare przeglądarki mogą spłaszczyć efekt; zawsze warto przetestować na docelowych urządzeniach odbiorców.

---

## Wskazówki, jak dopracować swój PDF

- **Dodaj obramowanie:** `rectangle.line_format.width = 1.5` i ustaw kolor, aby uzyskać wyraźny kontur.  
- **Wyśrodkuj prostokąt:** Użyj `builder.move_to_document_start()` przed wstawieniem, a następnie `builder.paragraph_format.alignment = aw.ParagraphAlignment.CENTER`.  
- **Połącz z tekstem:** Wstaw `TextFragment` po prostokącie, aby go opisać, np. `"Important Section"`.

Te małe poprawki mogą zamienić zwykły prostokąt w elegancki dymek, który wygląda profesjonalnie w raportach, ofertach czy e‑bookach.

---

## Zakończenie

Masz już kompletny przepis od **utworzenia kształtu prostokąta** w Pythonie, **dodania cienia do kształtu**, **ustawienia kąta cienia**, po **zapisanie dokumentu jako PDF** przy użyciu Aspose.Words. Kroki są proste, kod jest w pełni samodzielny, a Ty widziałeś, dlaczego każda linijka ma znaczenie — od inicjalizacji dokumentu po wykończenie finalnego PDF‑a.

Następnie możesz zbadać **jak dodać cień do bardziej złożonych rysunków**, eksperymentować z wypełnieniami gradientowymi lub generować tabele wewnątrz kształtów. Biblioteka obsługuje także łączenie kształtów z zakładkami, co może być przydatne w interaktywnych PDF‑ach.

Masz własny pomysł, który wypróbowałeś? Podziel się nim w komentarzach lub zadaj pytania, które Ci pozostały. Miłego kodowania i ciesz się dodatkową głębią w swoich dokumentach! 

![Rectangle shape with shadow – example of create rectangle shape in Python](/images/rectangle-shadow.png)


## Co warto nauczyć się dalej?


Poniższe samouczki dotyczą ściśle powiązanych tematów, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne przykłady kodu oraz szczegółowe wyjaśnienia, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}