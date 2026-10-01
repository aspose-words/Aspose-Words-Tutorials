---
category: general
date: 2026-09-30
description: Dowiedz się, jak utworzyć prostokątny kształt, dodać cień do kształtu
  i zapisać dokument Word z kształtem przy użyciu Aspose.Words dla Pythona.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- how to add shape
- apply shadow to shape
- set shadow blur
- save word with shape
language: pl
lastmod: 2026-09-30
og_description: Szybko utwórz prostokątny kształt w dokumencie Word. Ten poradnik
  pokazuje, jak dodać kształt, zastosować cień, ustawić rozmycie cienia i zapisać
  dokument Word z kształtem.
og_image_alt: Screenshot of a Word document showing a rectangle shape with a soft
  shadow
og_title: Tworzenie prostokątnego kształtu w Wordzie przy użyciu Pythona – przewodnik
  krok po kroku
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Learn how to create rectangle shape, apply shadow to shape, and save
    Word with shape using Aspose.Words for Python.
  headline: How to create rectangle shape in a Word document using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- Shapes
title: Jak utworzyć prostokątny kształt w dokumencie Word przy użyciu Pythona
url: /pl/python/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć prostokątny kształt w dokumencie Word przy użyciu Pythona

Jeśli potrzebujesz **utworzyć prostokątny kształt** w pliku Word, ten przewodnik pokaże Ci kompletną, gotową do uruchomienia rozwiązanie. Zobaczysz, jak dodać kształt, zastosować efekt cienia, dostosować rozmycie i w końcu **zapisać Word z kształtem**, aby wynik mógł zostać otwarty w Microsoft Word lub dowolnym kompatybilnym podglądzie.

Przykład wykorzystuje **Aspose.Words for Python via .NET**, bibliotekę umożliwiającą manipulację dokumentami Word bez zainstalowanego Microsoft Office. Nie wymaga wcześniejszej znajomości API – wystarczy podstawowa wiedza o Pythonie.

## Co osiągniesz

- Wstawisz prostokąt do pierwszej sekcji nowego dokumentu.  
- Skonfigurujesz miękki cień, ustawiając jego rozmycie, offset i kolor.  
- Zapiszesz dokument na dysku i zweryfikujesz rezultat wizualny.

## Wymagania wstępne

- Python 3.8 lub nowszy.  
- Pakiet `aspose-words` zainstalowany (`pip install aspose-words`).  
- Uprawnienia do zapisu w katalogu wyjściowym.

## Utwórz prostokątny kształt i skonfiguruj jego wygląd

Pierwszym krokiem jest utworzenie pustego dokumentu i dodanie do niego prostokątnego kształtu. Kształt będzie służył jako płótno dla efektu cienia.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Step 1: Create a new blank document
doc = aw.Document()

# Step 2: Add a rectangle shape to the first section
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Optional: Define the shape’s size and position (in points)
shape.width = aw.ConvertUtil.inch_to_point(2)   # 2 inches wide
shape.height = aw.ConvertUtil.inch_to_point(1)  # 1 inch tall
shape.left = aw.ConvertUtil.inch_to_point(1)    # 1 inch from the left margin
shape.top = aw.ConvertUtil.inch_to_point(1)     # 1 inch from the top margin
```

**Dlaczego to ważne:**  
Utworzenie prostokąta daje Ci konkretny obiekt (`shape`), który później możesz stylizować. Ustawienie wyraźnych wymiarów zapewnia, że kształt będzie wyglądał tak samo na każdej platformie.

## Jak dodać kształt do dokumentu Word

Choć powyższy kod już dodaje prostokąt, później możesz potrzebować dodać dodatkowe kształty (np. koła, strzałki). Ten sam wzorzec ma zastosowanie: wywołaj `append_child` na ciele dokumentu i przekaż żądany `ShapeType`.

```python
# Example: Adding a second shape – an ellipse
ellipse = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.ELLIPSE)
)
ellipse.width = aw.ConvertUtil.inch_to_point(1.5)
ellipse.height = aw.ConvertUtil.inch_to_point(1)
ellipse.left = aw.ConvertUtil.inch_to_point(3.5)
ellipse.top = aw.ConvertUtil.inch_to_point(1)
```

**Wskazówka:** Używaj wyliczenia `ShapeType`, aby przeglądać wszystkie obsługiwane kształty. Dzięki temu kod pozostaje czytelny i unikasz „magicznych liczb”.

## Zastosuj cień do kształtu i ustaw rozmycie cienia

Cień dodaje głębi i atrakcyjności wizualnej. Klasa `ShadowEffect` pozwala kontrolować rozmycie, offset i kolor. Poniżej stosujemy miękki czarny cień do prostokąta.

```python
# Step 3: Configure a shadow effect for the rectangle
shadow = ShadowEffect()
shadow.blur = 5.0          # Sets the softness of the shadow edge
shadow.offset_x = 2.0      # Horizontal displacement from the shape
shadow.offset_y = 2.0      # Vertical displacement from the shape
shadow.color = aw.Color.black

# Step 4: Apply the shadow effect to the shape
shape.shadow = shadow
```

**Dlaczego ustawia się rozmycie?**  
`blur` określa, jak rozproszony jest cień. Niska wartość (np. 1.0) daje ostry brzeg, natomiast wyższa wartość (np. 5.0) tworzy łagodne przejście, które jest zazwyczaj bardziej estetyczne.

**Przypadek brzegowy:** Jeśli ustawisz `blur` na 0, cień stanie się pełną sylwetką. Niektóre przeglądarki mogą wyświetlać go z artefaktami aliasingu, więc wybierz wartość większą niż 0, aby uzyskać płynniejszy efekt.

## Zapisz Word z kształtem

Zapisanie dokumentu finalizuje wszystkie zmiany. Metoda `save` zapisuje plik `.docx`, który może otworzyć każdy nowoczesny edytor Word.

```python
# Step 5: Save the document to see the result
output_path = "output.docx"   # Adjust the path as needed
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Po otwarciu `output.docx` zobaczysz prostokąt umieszczony jedną calą od lewego górnego rogu, z miękkim czarnym cieniem przesuniętym o dwa punkty w prawo i w dół. Rozmycie cienia sprawia wrażenie, że kształt unosi się nad stroną.

**Profesjonalna wskazówka:** Jeśli musisz generować wiele dokumentów w pętli, ponownie używaj tej samej instancji `Document` i czyść jej ciało pomiędzy iteracjami, aby zmniejszyć zużycie pamięci.

## Typowe warianty i rozwiązywanie problemów

| Sytuacja | Co zmienić | Powód |
|----------|------------|-------|
| Inny kolor cienia | `shadow.color = aw.Color.red` | Użyj kolorów firmowych lub podkreśl ważne kształty. |
| Większy offset cienia | Zwiększ `shadow.offset_x`/`offset_y` | Podkreśl głębię w makietach UI. |
| Brak cienia | Pomiń linię `shape.shadow = shadow` | Przydatne w minimalistycznych raportach. |
| Eksport do PDF zamiast DOCX | `doc.save("output.pdf")` | PDF jest idealny do dystrybucji tylko do odczytu. |

Jeśli kształt się nie pojawia, sprawdź, czy dodajesz go do właściwej sekcji (`get_first_section()`) i czy dokument jest zapisywany po wprowadzeniu zmian.

## Pełny, gotowy do uruchomienia przykład

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Create a new blank document
doc = aw.Document()

# Add a rectangle shape
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
shape.width = aw.ConvertUtil.inch_to_point(2)
shape.height = aw.ConvertUtil.inch_to_point(1)
shape.left = aw.ConvertUtil.inch_to_point(1)
shape.top = aw.ConvertUtil.inch_to_point(1)

# Configure and apply a shadow
shadow = ShadowEffect()
shadow.blur = 5.0
shadow.offset_x = 2.0
shadow.offset_y = 2.0
shadow.color = aw.Color.black
shape.shadow = shadow

# Save the document
output_path = "output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Uruchomienie skryptu generuje `output.docx` zawierający prostokąt z miękkim cieniem. Otwórz plik w Microsoft Word, aby potwierdzić, że efekt wizualny odpowiada opisowi.

## Podsumowanie

Teraz wiesz, jak **utworzyć prostokątny kształt**, **dodać kształt** do dokumentu Word, **zastosować cień do kształtu**, **ustawić rozmycie cienia** oraz w końcu **zapisać Word z kształtem** przy użyciu Aspose.Words for Python. Ten sam wzorzec można rozszerzyć na inne typy kształtów, kolory i efekty, dając pełną kontrolę nad grafiką dokumentu bez potrzeby automatyzacji Office.

**Kolejne kroki**

- Eksperymentuj z `Shape.fill`, aby dodać gradienty lub tła obrazkowe.  
- Użyj obiektów `Paragraph`, aby umieścić tekst wewnątrz prostokąta.  
- Połącz wiele kształtów, aby tworzyć złożone diagramy, a następnie wyeksportuj do PDF w celu dystrybucji.  

Śmiało dostosowuj kod do własnych potrzeb raportowych lub szablonowych i podziel się wynikami w komentarzach!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne, działające przykłady kodu oraz wyjaśnienia krok po kroku, pomagające opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}