---
category: general
date: 2026-07-03
description: Utwórz kształt prostokąta w Javie i dowiedz się, jak dodać cień do kształtu,
  zastosować efekt cienia, ustawić przezroczystość kształtu oraz szybko utworzyć pusty
  dokument.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- set shape transparency
- create blank document
language: pl
og_description: Utwórz prostokątny kształt w Javie z cieniem, przezroczystością i
  pustym dokumentem. Skorzystaj z tego przewodnika, aby opanować obsługę kształtów.
og_title: Stwórz prostokątny kształt w Javie – Pełny samouczek programistyczny
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  headline: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  name: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  steps:
  - name: What if I want a different shadow color?
    text: 'Simply change the `setColor` call:'
  - name: Can I apply the same shadow to multiple shapes?
    text: 'Yes. Create one `ShadowEffect` instance, configure it, then reuse it:'
  - name: How do I change the shadow blur dynamically?
    text: Expose a UI slider that maps to `setBlurRadius`. Values between `2` and
      `12` are typical; larger numbers produce a “glow” rather than a crisp shadow.
  - name: What if I need the shape to float rather than be inline?
    text: 'Swap the wrap type:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Automation
title: Tworzenie prostokątnego kształtu w Javie – Kompletny przewodnik krok po kroku
url: /pl/java/images-shapes/create-rectangle-shape-in-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tworzenie prostokątnego kształtu w Javie – Kompletny przewodnik krok po kroku

Zastanawiałeś się kiedyś, jak **utworzyć prostokątny kształt** w dokumencie Word przy użyciu Javy? Nie jesteś jedyny — programiści często potrzebują szybkiego sposobu na dodanie grafiki geometrycznej, a następnie nadanie jej subtelnego cienia, aby układ wyglądał bardziej dopracowanie. W tym samouczku przejdziemy przez cały proces: od utworzenia **pustego dokumentu** po **dodanie cienia do kształtu**, **zastosowanie efektu cienia** i nawet **ustawienie przezroczystości kształtu** dla profesjonalnego wyglądu.

Fragment kodu poniżej jest w pełni funkcjonalnym przykładem, który możesz skopiować i wkleić do swojego projektu. Nie potrzebujesz dodatkowej dokumentacji — po prostu postępuj zgodnie z krokami, zrozum „dlaczego” i w kilka sekund będziesz generować prostokąty z cieniem.

## Czego się nauczysz

- Jak **programowo utworzyć prostokątny kształt** przy użyciu Aspose.Words for Java.  
- Dokładne wywołania potrzebne do **dodania cienia do kształtu** i skonfigurowania jego właściwości wizualnych.  
- Sposoby **zastosowania efektu cienia** oraz dostosowywania parametrów takich jak offset, promień rozmycia i kolor.  
- Techniki **ustawiania przezroczystości kształtu** dla subtelniejszego wyglądu.  
- Jak **utworzyć pusty dokument**, wstawić kształt i zapisać wynik.

> **Pro tip:** Wszystkie te operacje są wykonywane na jednej instancji `Document`, co oznacza, że możesz je łączyć ze sobą bez martwienia się o pośrednie operacje I/O.

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że masz:

- Java 17 (lub nowszy JDK) zainstalowany.  
- Bibliotekę Aspose.Words for Java dodaną do projektu (współrzędne Maven: `com.aspose:aspose-words:23.12`).  
- IDE Java lub prosty edytor tekstu — nic skomplikowanego, po prostu miejsce do kompilacji i uruchomienia.

Jeśli czegoś brakuje, pobierz JDK ze strony Oracle i dodaj zależność Aspose przez Maven lub Gradle. Gdy to będzie gotowe, możesz przystąpić do działania.

## Krok 1: **Utworzenie pustego dokumentu** – płótno dla wszystkiego

Pierwszą rzeczą, której potrzebujesz, jest pusty obiekt `Document`. Pomyśl o nim jak o czystej kartce papieru; bez niego nie ma gdzie umieścić prostokąt.

```java
// Step 1: Create a new blank document
Document document = new Document();
```

Dlaczego zaczynamy od pustego dokumentu? Ponieważ każdy kształt znajduje się wewnątrz `Section`, a nowo‑utworzony `Document` już zawiera domyślną sekcję z ciałem gotowym przyjąć węzły. Pominięcie tego kroku zmusiłoby Cię do ręcznego tworzenia sekcji później, co wprowadza niepotrzebną złożoność.

## Krok 2: **Utworzenie prostokątnego kształtu** i określenie jego rozmiaru

Mając już płótno, **utwórzmy prostokątny kształt**. Klasa `Shape` przyjmuje referencję do dokumentu oraz `ShapeType`. W tym przykładzie wybieramy `RECTANGLE` i ustawiamy szerokość/wysokość w punktach (1 pt ≈ 1/72 cala).

```java
// Step 2: Insert a rectangle shape and define its size and layout
Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
rectangleShape.setWidth(200);   // 200 pt ≈ 2.78 inches
rectangleShape.setHeight(100);  // 100 pt ≈ 1.39 inches
rectangleShape.setWrapType(WrapType.INLINE);
```

Dlaczego ustawiamy `WrapType.INLINE`? Zawijanie inline sprawia, że kształt zachowuje się jak znak w akapicie, co zapewnia, że porusza się razem z otaczającym tekstem. Jeśli potrzebujesz zachowania pływającego, przełącz na `WrapType.SQUARE` lub `WrapType.TOP_BOTTOM`.

## Krok 3: **Zastosowanie efektu cienia** – nadanie prostokątowi głębi

Płaski prostokąt wygląda… po prostu płasko. Dodanie cienia sprawia, że „wyskakuje”. **Zastosujemy efekt cienia** tworząc instancję `ShadowEffect`, a następnie dostosowując jej właściwości wizualne.

```java
// Step 3: Create a shadow effect and configure its visual properties
ShadowEffect shadowEffect = new ShadowEffect();
shadowEffect.setColor(Color.getGray(0.5));   // medium gray
shadowEffect.setOffsetX(5);                  // horizontal offset (points)
shadowEffect.setOffsetY(5);                  // vertical offset (points)
shadowEffect.setBlurRadius(8);               // softness of the shadow
shadowEffect.setTransparency(0.3);           // 30 % transparent
```

Rozłóżmy to na części:

- **Color** – `Color.getGray(0.5)` zwraca 50 % szarości, co jest neutralne i pasuje do większości tła.  
- **OffsetX/Y** – Dodatnie wartości przesuwają cień w prawo i w dół; wartości ujemne przeniosłyby go w lewo/górę.  
- **BlurRadius** – Większe wartości tworzą miększy, bardziej rozproszony cień.  
- **Transparency** – Zakres od `0` (nieprzezroczysty) do `1` (całkowicie przezroczysty). Tutaj wybraliśmy `0.3` dla subtelnego efektu.

## Krok 4: **Dodanie cienia do kształtu** – powiązanie efektu

Stworzenie efektu to dopiero początek; musimy **dodać cień do kształtu**, przypisując obiekt `ShadowEffect` do prostokąta.

```java
// Step 4: Apply the shadow effect to the rectangle shape
rectangleShape.setShadowEffect(shadowEffect);
```

Za kulisami to wywołanie aktualizuje podstawowy znacznik OpenXML (`<w:shdw>`), którego Word używa do renderowania cieni. Jeśli przejrzysz zapisany plik `.docx`, zobaczysz element `<w:effect>` wypełniony parametrami, które ustawiliśmy.

## Krok 5: **Ustawienie przezroczystości kształtu** – opcjonalne, ale często przydatne

Czasami chcesz, aby sam prostokąt był częściowo przezroczysty, pozwalając tekstowi w tle prześwitać. Klasa `Shape` udostępnia `setFillColor` i `setFillTransparency`. Oto szybki przykład, który sprawia, że prostokąt jest w 40 % przezroczysty:

```java
// Optional: make the rectangle partially transparent
rectangleShape.setFillColor(Color.getWhite());
rectangleShape.setFillTransparency(0.4); // 40 % transparent
```

Dlaczego warto to zrobić? Wyobraź sobie znak wodny lub wyróżniony komentarz, w którym zawartość pod spodem musi pozostać czytelna. Dostosuj wartość przezroczystości, aby pasowała do Twojego języka projektowego.

## Krok 6: Wstawienie kształtu do dokumentu

Zbudowaliśmy prostokąt, dodaliśmy cień i (opcjonalnie) ustawiliśmy jego przezroczystość. Ostatnim krokiem jest **dodanie kształtu do pierwszej sekcji dokumentu**.

```java
// Step 5: Add the shape to the first section of the document
document.getFirstSection().getBody().appendChild(rectangleShape);
```

Dołączenie kształtu do ciała dokumentu umieszcza go na końcu pierwszego akapitu. Jeśli potrzebujesz konkretnego miejsca wstawienia, pobierz docelowy `Paragraph` i użyj `insertBefore` lub `insertAfter`.

## Krok 7: Zapisz dokument – zobacz rezultat

Cała ta praca kończy się jednym wywołaniem `save`. Wybierz ścieżkę, która ma sens w Twoim środowisku.

```java
// Step 6: Save the document with the shadowed shape
document.save("YOUR_DIRECTORY/ShadowShape.docx");
```

Otwórz powstały plik `ShadowShape.docx` w Microsoft Word lub LibreOffice, a zobaczysz wyraźny prostokąt z delikatnym szarym cieniem, lekko przezroczysty, jeśli wykonałeś opcjonalny krok. Wizualizacja odpowiada parametrom, które zdefiniowaliśmy programowo.

---

![utwórz prostokątny kształt z cieniem w dokumencie Word](https://example.com/images/rectangle-shadow.png "utwórz prostokątny kształt z cieniem")

*Tekst alternatywny obrazu:* **utwórz prostokątny kształt z cieniem** – wizualna reprezentacja końcowego wyniku.

## Często zadawane pytania i sytuacje brzegowe

### Co zrobić, jeśli chcę inny kolor cienia?

Po prostu zmień wywołanie `setColor`:

```java
shadowEffect.setColor(Color.getRed()); // bright red shadow
```

Pamiętaj, że zbyt jaskrawe cienie mogą wyglądać nieprofesjonalnie; subtelne odcienie zazwyczaj sprawdzają się lepiej.

### Czy mogę zastosować ten sam cień do wielu kształtów?

Tak. Utwórz jedną instancję `ShadowEffect`, skonfiguruj ją, a następnie użyj ponownie:

```java
Shape circle = new Shape(document, ShapeType.OVAL);
circle.setShadowEffect(shadowEffect); // same effect as rectangle
```

Unikaj modyfikowania `ShadowEffect` po przypięciu go do innych kształtów, chyba że zamierzasz zaktualizować je wszystkie.

### Jak dynamicznie zmienić rozmycie cienia?

Udostępnij suwak UI, który mapuje na `setBlurRadius`. Typowe wartości mieszczą się w przedziale od `2` do `12`; większe liczby dają efekt „poświaty” zamiast wyraźnego cienia.

### Co zrobić, jeśli kształt ma być pływający, a nie inline?

Zamień typ zawijania:

```java
rectangleShape.setWrapType(WrapType.SQUARE);
rectangleShape.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangleShape.setHorizontalAlignment(HorizontalAlignment.CENTER);
```

Kształty pływające dają większą swobodę układu, ale wymagają dodatkowej logiki pozycjonowania.

## Pełny działający przykład

Poniżej znajduje się kompletny program gotowy do skopiowania i wklejenia, który zawiera wszystkie omówione kroki. Uruchom go jako zwykłą aplikację Java.

```java
import com.aspose.words.*;

public class ShadowRectangleDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank document
        Document document = new Document();

        // 2. Build the rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);

        // 3. Configure shadow effect
        ShadowEffect shadowEffect = new ShadowEffect();
        shadowEffect.setColor(Color.getGray(0.5));
        shadowEffect.setOffsetX(5);
        shadowEffect.setOffsetY(5);
        shadowEffect.setBlurRadius(8);
        shadowEffect.setTransparency(0.3);

        // 4. Apply shadow to the rectangle
        rectangleShape.setShadowEffect(shadowEffect);

        // 5. (Optional) Make rectangle semi‑transparent
        rectangleShape.setFillColor(Color.getWhite());
        rectangleShape.setFillTransparency(0.4);

        // 6. Insert shape into the document
        document.getFirstSection().getBody().appendChild(rectangleShape);

        // 7. Save the file
        document.save("ShadowShape.docx");
    }
}
```

**Oczekiwany wynik:** Po otwarciu `ShadowShape.docx` zobaczysz biały prostokąt o wymiarach 200 × 100 pt, wyśrodkowany w pierwszym akapicie, z średnio szarym cieniem przesuniętym o 5 pt, rozmytym promieniem 8 i 30 % przezroczystością. Sam prostokąt jest w 40 % przezroczysty, co pozwala na prześwitowanie dowolnego tekstu pod nim.

## Podsumowanie

Właśnie **utworzyliśmy prostokątny kształt** od podstaw, **dodaliśmy cień do kształtu**, **zastosowaliśmy efekt cienia**, a nawet **ustawiliśmy przezroczystość kształtu** — wszystko przy użyciu **utworzenia pustego dokumentu** jako fundamentu. Podejście jest proste, opiera się na płynnym API Aspose.Words i może być rozszerzone o koła, gwiazdy lub niestandardowe wielokąty.

Co dalej w Twojej roadmapie? Spróbuj zamienić `ShapeType.RECTANGLE` na `ShapeType.OVAL`, aby generować cieniowane koła, lub poeksperymentuj z wypełnieniami gradientowymi dla

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne przykłady kodu oraz wyjaśnienia krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}