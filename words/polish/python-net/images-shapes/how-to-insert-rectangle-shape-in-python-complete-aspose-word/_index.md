---
category: general
date: 2026-06-27
description: Dowiedz się, jak wstawić prostokątny kształt w Pythonie przy użyciu Aspose.Words,
  zmienić kolor cienia, dodać zewnętrzny cień i zastosować efekt cienia do kształtu
  — wszystko w jednym samouczku.
draft: false
keywords:
- how to insert rectangle shape
- how to change shadow color
- how to add outer shadow
- apply shadow effect to shape
language: pl
og_description: Opanuj, jak wstawić kształt prostokąta w Pythonie, zmienić jego kolor
  cienia, dodać zewnętrzny cień oraz zastosować efekt cienia do kształtu przy użyciu
  Aspose.Words.
og_title: Jak wstawić kształt prostokąta w Pythonie – Poradnik Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  headline: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  name: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: Pro tip
    text: If you need the rectangle positioned at a specific location, use `builder.move_to`
      before inserting, or adjust `rectangle.left` and `rectangle.top` after creation.
  - name: Edge case
    text: If you forget to set `shadow.opacity`, the default is fully opaque, which
      can make the shadow look like a solid shape. Always pair a color change with
      an appropriate opacity level.
  - name: Common pitfalls
    text: '- **Missing directory:** `doc.save` will raise an error if the folder doesn’t
      exist. Create it first or use `os.makedirs`. - **Version mismatch:** The shadow
      API requires Aspose.Words 22.9+; older versions silently ignore shadow settings.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
title: Jak wstawić kształt prostokąta w Pythonie – Kompletny przewodnik Aspose.Words
url: /pl/python/images-shapes/how-to-insert-rectangle-shape-in-python-complete-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak wstawić kształt prostokąta w Pythonie – Kompletny przewodnik Aspose.Words

Zastanawiałeś się kiedyś **jak wstawić kształt prostokąta** do dokumentu Word przy użyciu Pythona? Nie jesteś jedyny — wielu programistów napotyka ten problem przy automatyzacji raportów lub tworzeniu szablonów. Dobrą wiadomością jest to, że Aspose.Words robi to w mig, a w tym tutorialu przeprowadzimy Cię przez cały proces, od narysowania prostokąta po nadanie mu eleganckiego cienia zewnętrznego.

Omówimy także **jak zmienić kolor cienia**, **jak dodać cień zewnętrzny** oraz ostateczny krok **zastosowania efektu cienia do kształtu**. Po zakończeniu będziesz mieć w pełni wystylizowany prostokąt, który możesz programowo wkleić do dowolnego pliku .docx.

## Wymagania wstępne

- Python 3.8+ zainstalowany na Twoim komputerze  
- Aspose.Words for Python via `pip install aspose-words`  
- Podstawowa znajomość skryptów w Pythonie (nie wymagana dogłębna wiedza o Word‑API)  

Jeśli już to masz, świetnie — zanurzmy się. Jeśli nie, najpierw pobierz bibliotekę; dalsza część przewodnika zakłada, że import działa bez problemów.

## Jak wstawić kształt prostokąta przy użyciu Aspose.Words for Python

Pierwszy krok to dokładnie to, co obiecuje główne słowo kluczowe: **jak wstawić kształt prostokąta**. Utworzymy nowy dokument, stworzymy `DocumentBuilder` i umieścimy prostokąt na stronie.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a fresh document and a builder to add content
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle shape of 200x100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Optional: give the rectangle a light fill so the shadow is visible
rectangle.fill_color = aw.drawing.Color.light_blue
```

> **Dlaczego to ważne:** Wywołanie `insert_shape` jest sednem *jak wstawić kształt prostokąta*. Zwraca ono obiekt `Shape`, którym możesz później manipulować — rozmiarem, pozycją, wypełnieniem, obramowaniem, itp. Zauważ, że ustawiamy także `fill_color`; bez tego cień może zlewać się z białą stroną, co utrudni jego widoczność.

### Porada
Jeśli potrzebujesz, aby prostokąt znajdował się w określonym miejscu, użyj `builder.move_to` przed wstawieniem lub dostosuj `rectangle.left` i `rectangle.top` po utworzeniu.

## Zmiana koloru cienia kształtu

Teraz, gdy prostokąt znajduje się w dokumencie, odpowiedzmy na pytanie **jak zmienić kolor cienia**. Aspose.Words udostępnia obiekt `ShadowEffect`, w którym możesz ustawić właściwość `color` na dowolną wartość RGB.

```python
# Create a shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # we’ll also cover outer shadow later
shadow.blur_radius = 8.0                  # smooth edges
shadow.distance = 6.0                     # how far the shadow sits from the shape
shadow.direction = 45                     # angle in degrees
shadow.opacity = 0.6                      # semi‑transparent

# Change the shadow color to a deep gray instead of black
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)

# Apply the shadow to our rectangle
rectangle.shadow = shadow
```

> **Dlaczego warto to zrobić:** Ciemny, czarny cień może być zbyt ostry, szczególnie w dokumentach o jasnym tle. Dostosowanie koloru pozwala dopasować go do identyfikacji wizualnej firmy lub po prostu uzyskać łagodniejszy efekt wizualny.

### Przypadek brzegowy
Jeśli zapomnisz ustawić `shadow.opacity`, domyślnie będzie ono w pełni nieprzezroczyste, co może sprawić, że cień będzie wyglądał jak solidny kształt. Zawsze łącz zmianę koloru z odpowiednim poziomem przezroczystości.

## Dodawanie efektu cienia zewnętrznego

Kolejne pytanie, które wielu zadaje, to **jak dodać cień zewnętrzny**. Flaga `ShadowStyle.OUTER` informuje Aspose.Words, aby renderował cień poza obrysem kształtu, a nie wewnątrz niego.

Powyższy fragment kodu już używa `ShadowStyle.OUTER`, ale wyodrębnijmy to ustawienie dla przejrzystości:

```python
# Ensure the shadow style is outer
shadow.style = ShadowStyle.OUTER
```

Jeśli przełączysz się na `ShadowStyle.INNER`, cień pojawi się *wewnątrz* prostokąta, co jest przydatne przy efektach wytłoczenia. W większości scenariuszy projektowania dokumentów styl zewnętrzny daje naturalny wygląd cienia opadającego.

## Zastosowanie efektu cienia do kształtu

Już **zastosowaliśmy efekt cienia do kształtu** poprzez przypisanie `rectangle.shadow = shadow`. Połączmy wszystko razem i zapiszmy dokument, aby potwierdzić, że efekt pozostaje.

```python
# Save the document – choose a folder you have write access to
output_path = "output/RectangleWithShadow.docx"
doc.save(output_path)

print(f"Document saved to {output_path}. Open it to see the rectangle with its outer shadow.")
```

Gdy otworzysz `RectangleWithShadow.docx` w Microsoft Word, powinieneś zobaczyć jasno-niebieski prostokąt z subtelnym szarym cieniem zewnętrznym padającym pod kątem 45°. Cień będzie lekko rozmyty i przesunięty, dokładnie tak, jak skonfigurowaliśmy.

### Typowe pułapki
- **Brak katalogu:** `doc.save` zgłosi błąd, jeśli folder nie istnieje. Utwórz go wcześniej lub użyj `os.makedirs`.
- **Niezgodność wersji:** API cienia wymaga Aspose.Words 22.9+; starsze wersje po cichu ignorują ustawienia cienia.

## Pełny działający przykład

Poniżej znajduje się kompletny, gotowy do uruchomienia skrypt, który łączy wszystkie kroki. Skopiuj‑wklej go do pliku o nazwie `rectangle_shadow.py` i uruchom poleceniem `python rectangle_shadow.py`.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Create a new document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2️⃣ Insert the rectangle shape (how to insert rectangle shape)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle.fill_color = aw.drawing.Color.light_blue   # make the shape visible

# 3️⃣ Define the shadow (how to change shadow color, how to add outer shadow)
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # outer shadow
shadow.blur_radius = 8.0
shadow.distance = 6.0
shadow.direction = 45
shadow.opacity = 0.6
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)  # custom gray

# 4️⃣ Apply the shadow (apply shadow effect to shape)
rectangle.shadow = shadow

# 5️⃣ Save the file
output_path = os.path.join(output_dir, "RectangleWithShadow.docx")
doc.save(output_path)

print(f"✅ Document generated: {output_path}")
```

**Oczekiwany wynik:** Dokument Word (`RectangleWithShadow.docx`) zawierający pojedynczy prostokąt z szarym cieniem zewnętrznym. Otwórz go w Wordzie, aby zweryfikować efekt wizualny.

## Najczęściej zadawane pytania

| Pytanie | Odpowiedź |
|----------|-----------|
| *Czy mogę użyć innego typu kształtu?* | Oczywiście — zamień `ShapeType.RECTANGLE` na `ShapeType.OVAL`, `ShapeType.TRIANGLE` itp., a ta sama logika cienia będzie działać. |
| *Co zrobić, jeśli potrzebuję grubszej obwódki?* | Ustaw `rectangle.line_width = 2.0` (punkty) przed zastosowaniem cienia. |
| *Czy da się animować cień?* | Bezpośrednio w Aspose.Words nie — musiałbyś wyeksportować do HTML/CSS, aby uzyskać animację. |
| *Czy to działa na macOS?* | Tak — Aspose.Words jest niezależny od platformy, o ile Python działa. |

## Zakończenie

Przeszliśmy przez **jak wstawić kształt prostokąta**, pokazaliśmy **jak zmienić kolor cienia**, wyjaśniliśmy **jak dodać cień zewnętrzny**, a na koniec pokazaliśmy, jak **zastosować efekt cienia do kształtu** przy użyciu Aspose.Words for Python. Pełny skrypt jest gotowy do wstawienia w dowolny pipeline automatyzacji, dając Ci profesjonalnie wyglądający prostokąt z dopracowanym cieniem w kilka sekund.

Gotowy na kolejny krok? Spróbuj zmienić kolor wypełnienia, poeksperymentuj z różnymi kątami `direction` lub dodaj wiele kształtów na tej samej stronie. Możesz także zagłębić się w bogate API formatowania tekstu Aspose.Words, aby łączyć cienie ze stylizowanym tekstem — idealne do przyciągających uwagę raportów.

Jeśli ten tutorial był pomocny, daj łapkę w górę, udostępnij go współpracownikom lub zostaw komentarz z własnymi wariacjami. Szczęśliwego kodowania!

![Diagram pokazujący, jak wstawić kształt prostokąta z zastosowanym cieniem zewnętrznym w dokumencie Word](/images/rectangle-shadow.png)


## Co powinieneś nauczyć się dalej?


Poniższe tutoriale obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}