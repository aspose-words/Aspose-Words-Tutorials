---
category: general
date: 2026-06-21
description: Utwórz prostokątny kształt w Pythonie przy użyciu Aspose.Words. Dowiedz
  się, jak dodać cień do kształtu, ustawić kolor wypełnienia kształtu i zapisać dokument
  jako PDF w kilka minut.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- set shape fill color
language: pl
og_description: Utwórz prostokątny kształt w Pythonie przy użyciu Aspose.Words. Ten
  przewodnik pokazuje, jak dodać cień do kształtu, ustawić kolor wypełnienia kształtu
  oraz zapisać dokument jako PDF.
og_title: Utwórz kształt prostokąta w Pythonie – samouczek Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-21'
  description: Create rectangle shape in Python using Aspose.Words. Learn how to add
    shadow to shape, set shape fill color, and save document as PDF in minutes.
  headline: Create rectangle shape in Python – Aspose.Words tutorial
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF generation
title: Utwórz prostokątny kształt w Pythonie – samouczek Aspose.Words
url: /pl/python/images-shapes/create-rectangle-shape-in-python-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tworzenie prostokątnego kształtu w Python – samouczek Aspose.Words

Zastanawiałeś się kiedyś **jak stworzyć prostokątny kształt** w dokumencie Word, pisząc w Pythonie? Nie jesteś jedyny. Wielu programistów napotyka problem, gdy potrzebują szybkiego elementu wizualnego — np. kolorowego pola z delikatnym cieniem — i chcą wyeksportować całość jako PDF.  

W tym przewodniku przejdziemy przez kompletny, gotowy do uruchomienia przykład, który **tworzy prostokątny kształt**, **ustawia kolor wypełnienia kształtu**, **dodaje cień do kształtu**, a na końcu **zapisuje dokument jako PDF**. Bez niejasnych odniesień, tylko konkretny kod, który możesz skopiować‑wkleić i uruchomić już dziś.

## Czego będziesz potrzebować

Zanim zaczniemy, upewnij się, że masz na swoim komputerze następujące elementy:

- Python 3.8 lub nowszy (używana składnia działa w każdej aktualnej wersji).
- Aktywną licencję Aspose.Words for Python lub darmowy trial (biblioteka jest czysto‑Pythonowa, nie wymaga COM).
- Edytor tekstu lub IDE, w którym czujesz się komfortowo — VS Code świetnie się sprawdzi, ale każdy będzie odpowiedni.

To wszystko. Bez ciężkich frameworków, bez dodatkowych zależności systemowych. Zaczynajmy.

## Krok 1: Zainstaluj Aspose.Words for Python

Na początek. Jeśli jeszcze tego nie zrobiłeś, pobierz pakiet z PyPI:

```bash
pip install aspose-words
```

Dlaczego ten krok jest ważny: Aspose.Words dostarcza klasy `Document` i `DocumentBuilder`, na których będziemy polegać. Bez biblioteki żadne późniejsze wywołania — takie jak `insert_shape` — nie istnieją, więc skrypt zakończy się błędem, zanim narysuje cokolwiek.

> **Pro tip:** Utrzymuj wirtualne środowisko w porządku. Uruchom `python -m venv .venv && source .venv/bin/activate` przed instalacją, aby biblioteka była odizolowana od pakietów systemowych.

## Krok 2: Utwórz nowy dokument i DocumentBuilder

Teraz faktycznie **tworzymy prostokątny kształt** — ale najpierw potrzebujemy pustego płótna.

```python
import aspose.words as aw

# Initialize a new, empty Word document
doc = aw.Document()
# DocumentBuilder lets us add content programmatically
builder = aw.DocumentBuilder(doc)
```

Obiekt `Document` reprezentuje cały plik, natomiast `DocumentBuilder` to wygodny pomocnik, który wie, gdzie znajduje się kursor i może wstawiać elementy w tym miejscu. Myśl o builderze jak o piórze, które pisze na stronie.

## Krok 3: Wstaw prostokątny kształt

Tutaj dzieje się główna akcja. **Utworzymy prostokątny kształt** o stałej szerokości i wysokości, a następnie umieścimy go na stronie.

```python
# Insert a rectangle 200 points wide and 100 points tall
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

Dlaczego prostokąt? To najprostszy kształt, który wciąż pozwala nam pokazać kolory wypełnienia i cienie. Jeśli później potrzebujesz koła lub gwiazdy, po prostu zamień `ShapeType.RECTANGLE` na inną wartość wyliczenia.

## Krok 4: Ustaw kolor wypełnienia kształtu

Białe pole nie jest zbyt ekscytujące, więc **ustawmy kolor wypełnienia kształtu** na coś łagodnego — jasny niebieski dobrze sprawdza się w raportach.

```python
# Apply a light‑blue background to the rectangle
rectangle.fill_color = aw.Color.light_blue
```

Możesz użyć dowolnego z predefiniowanych członków `aw.Color` (`red`, `green`, `dark_gray` itd.) lub przekazać krotkę RGB (`aw.Color.from_argb(255, 30, 144, 255)`). Kolor wypełnienia to to, co użytkownik widzi przed nałożeniem cienia lub obramowania.

## Krok 5: Dodaj cień do kształtu

Teraz do wizualnego wykończenia: **dodaj cień do kształtu**. Cienie nadają głębi i sprawiają, że prostokąt wyróżnia się na stronie.

```python
# Grab the shadow format object
shadow = rectangle.shadow_format

# Turn the shadow on
shadow.visible = True
# Choose a dark gray tone for realism
shadow.color = aw.Color.dark_gray
# Blur radius controls softness (5 points is a nice middle ground)
shadow.blur = 5
# Horizontal and vertical offsets shift the shadow relative to the shape
shadow.offset_x = 3
shadow.offset_y = 3
# Slight transparency makes the shadow feel natural
shadow.transparency = 0.2
# Use an outer shadow – you could also try INSET for a different effect
shadow.type = aw.drawing.ShadowType.OUTER
```

**Jak dodać cień**? Powyższy kod robi dokładnie to, ale rozłóżmy, dlaczego każda właściwość ma znaczenie:

- `visible` — włącza/wyłącza efekt.
- `color` — definiuje odcień; ciemny szary imituje naturalne oświetlenie.
- `blur` — wyższe wartości dają miększą krawędź.
- `offset_x` / `offset_y` — przesuwają cień względem kształtu; dostosuj je, aby symulować różne kąty światła.
- `transparency` — 0 to pełna nieprzezroczystość, 1 to niewidzialny; 0.2 daje subtelną impresję.
- `type` — `OUTER` rzuca cień na zewnątrz kształtu, natomiast `INNER` wstawiałby go do środka.

Jeśli potrzebujesz dramatycznego cienia, zwiększ `blur` do 10‑15 i podbij `offset_x`/`offset_y` do 6‑8.

## Krok 6: Zapisz dokument jako PDF

Cała ta praca jest bez sensu, jeśli nie możemy **zapisz dokument jako PDF** i udostępnić go. Aspose.Words robi to w jednej linii:

```python
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Dlaczego PDF? Pliki PDF zachowują układ na wszystkich platformach, co czyni je idealnymi do raportów, faktur czy wszelkich materiałów do druku. Metoda `save` automatycznie wykrywa rozszerzenie pliku i wybiera odpowiedni format — wystarczy, że ścieżka zakończy się `.pdf`.

### Oczekiwany rezultat

Otwórz wygenerowany `ShapeWithShadow.pdf` i powinieneś zobaczyć jasnoniebieski prostokąt wyśrodkowany w pobliżu górnej części pierwszej strony, z miękkim ciemnoszarym cieniem lekko przesuniętym w prawo i w dół. Krawędzie kształtu są ostre, cień subtelny, a rozmiar pliku zazwyczaj poniżej 100 KB.

## Bonus: Dostosowywanie cieni – Odpowiedzi na „jak dodać cień”

Możesz się zastanawiać, *„Czy mogę zmienić kierunek cienia bez przesuwania samego kształtu?”* Oczywiście. Pozycja cienia jest niezależna od współrzędnych kształtu; po prostu zmień `offset_x` i `offset_y`. Dodatnie wartości przesuwają cień w prawo/dół, ujemne w lewo/górę. Dla źródła światła z góry‑lewej, użyj `offset_x = -3` i `offset_y = -3`.

Kolejne częste pytanie: *„Co jeśli potrzebuję kilku cieni na tym samym kształcie?”* Aspose.Words obsługuje tylko jeden cień na kształt. Jeśli potrzebujesz warstwowych efektów, utwórz duplikat kształtu, lekko go przesuń i zastosuj inny cień do każdego. To trochę hack, ale działa.

## Pełny skrypt – Gotowy do uruchomienia

Poniżej znajduje się kompletny, samodzielny skrypt. Skopiuj go do pliku o nazwie `create_rectangle_with_shadow.py` i uruchom poleceniem `python create_rectangle_with_shadow.py`.

```python
import aspose.words as aw

# ---------- Initialize document ----------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ---------- Insert rectangle ----------
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# ---------- Set fill color ----------
rectangle.fill_color = aw.Color.light_blue

# ---------- Configure shadow ----------
shadow = rectangle.shadow_format
shadow.visible = True
shadow.color = aw.Color.dark_gray
shadow.blur = 5
shadow.offset_x = 3
shadow.offset_y = 3
shadow.transparency = 0.2
shadow.type = aw.drawing.ShadowType.OUTER

# ---------- Save as PDF ----------
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

> **Uwaga:** Zamień `YOUR_DIRECTORY` na ścieżkę absolutną lub względną, która istnieje na twoim komputerze. Jeśli folder nie istnieje, Python zgłosi `FileNotFoundError`.

## Typowe pułapki i jak ich unikać

| Problem | Dlaczego się pojawia | Rozwiązanie |
|-------|----------------|-----|
| Cień się nie pojawia | `shadow.visible` domyślnie ustawione na `False` | Upewnij się, że `shadow.visible = True` |
| Kształt jest niewidoczny | Kolor wypełnienia ustawiony na `aw.Color.transparent` lub `None` | Użyj stałego koloru, np. `aw.Color.light_blue` |
| PDF jest pusty | Zapomniano wywołać `doc.save` lub zapisano z niewłaściwym rozszerzeniem | Wywołaj `doc.save("output.pdf")` i sprawdź ścieżkę |
| Błąd wykonania `ImportError` | Aspose.Words nie zainstalowany lub używane niewłaściwe środowisko | Uruchom `pip install aspose-words` w aktywnym venv |

## Kolejne kroki – Eksploruj więcej kształtów i formatowanie

Teraz, gdy opanowałeś **tworzenie prostokątnego kształtu**, możesz:

- Zamienić `ShapeType.RECTANGLE` na `ShapeType.ELLIPSE` lub `ShapeType.PENTAGON`, aby poeksperymentować z innymi geometriami.
- Dodać tekst wewnątrz kształtu używając `builder.move_to(rectangle.absolute_position)` i potem `builder.writeln("Hello World")`.
- Połączyć wiele kształtów w grupę za pomocą `group = aw.drawing.GroupShape(doc)` w celu stworzenia złożonych diagramów.
- Eksportować do innych formatów, takich jak DOCX (`doc.save("output.docx")`) lub HTML (`doc.save("output.html")`), aby zobaczyć, jak cień jest przenoszony.

Każde z tych rozszerzeń opiera się na tych samych podstawowych koncepcjach: **dodaj cień do kształtu**, **ustaw kolor wypełnienia kształtu** i **zapisz dokument jako PDF** (lub inny format).

---

### Podgląd obrazu *(opcjonalnie)*

![Create rectangle shape with shadow in Python](https://example.com/rectangle-shadow.png "Create rectangle shape with shadow in Python")

*Zrzut ekranu pokazuje końcowy wynik PDF z jasnoniebieskim prostokątem i subtelnym zewnętrznym cieniem.*

---

## Podsumowanie

Przeszliśmy przez każdy krok potrzebny do **tworzenia prostokątnego kształtu** w Pythonie, zastosowania własnego wypełnienia, **dodania cienia do kształtu**, a na końcu **zapisania dokumentu jako PDF**. Kod jest w pełni gotowy do uruchomienia, wyjaśnienia obejmują *dlaczego* każda właściwość jest używana, a także omówiliśmy typowe przypadki brzegowe i dalsze możliwości.

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne, działające przykłady kodu oraz szczegółowe wyjaśnienia, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}