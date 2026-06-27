---
category: general
date: 2026-06-27
description: Dowiedz się, jak skonfigurować promień rozmycia kształtu przy użyciu
  Aspose.Words for Java. Ten krok po kroku poradnik obejmuje także ustawienia cienia,
  przezroczystość i zapisywanie dokumentu.
draft: false
keywords:
- configure shape blur radius
- Aspose.Words shape shadow
- Java shadow format
- Word document shape manipulation
- set blur radius
language: pl
og_description: Skonfiguruj promień rozmycia kształtu w dokumencie Word przy użyciu
  Javy. Przejdź ten szczegółowy samouczek, aby opanować ustawienia cieni kształtów
  w Aspose.Words.
og_title: Skonfiguruj promień rozmycia kształtu w Javie – kompletny przewodnik
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to configure shape blur radius using Aspose.Words for Java.
    This step‑by‑step tutorial also covers shadow settings, transparency, and saving
    the document.
  headline: Configure Shape Blur Radius in Java – Complete Guide
  type: TechArticle
- description: Learn how to configure shape blur radius using Aspose.Words for Java.
    This step‑by‑step tutorial also covers shadow settings, transparency, and saving
    the document.
  name: Configure Shape Blur Radius in Java – Complete Guide
  steps:
  - name: Understanding the Numbers
    text: '- **Blur radius** (`setBlurRadius`) controls how fuzzy the shadow looks.
      A value of `0` gives a crisp edge, while `10` or higher yields a dreamy glow.
      - **DistanceX / DistanceY** shift the shadow relative to the shape. Positive
      X moves it right; positive Y moves it down. - **Transparency** makes the'
  - name: Targeting a Specific Shape by Name
    text: 'If your document contains many shapes, rely on the shape’s **name** (set
      in Word’s layout options) instead of index:'
  - name: Applying Different Blur Radii
    text: 'You might want a stronger blur for background graphics and a subtle one
      for icons. Loop through all shapes:'
  - name: Compatibility Notes
    text: '- **Units:** Aspose.Words uses points (1 pt = 1/72 inch). If you work with
      millimeters, convert accordingly. - **Version:** The API shown works with Aspose.Words
      for Java 24.9 and later. Older versions may use `setBlurRadius(double)` but
      lack some newer shadow properties.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: Konfiguracja promienia rozmycia kształtu w Javie – Kompletny przewodnik
url: /pl/java/images-shapes/configure-shape-blur-radius-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skonfiguruj promień rozmycia kształtu w Javie – Kompletny przewodnik

Czy kiedykolwiek potrzebowałeś **skonfigurować promień rozmycia kształtu** w dokumencie Word podczas pracy w Javie? Nie jesteś jedynym, który się nad tym zastanawia. Niezależnie od tego, czy dopracowujesz raport korporacyjny, czy dodajesz subtelną wizualną nutę do ulotki, opanowanie tego ustawienia może sprawić, że Twoje dokumenty będą wyglądały znacznie bardziej profesjonalnie.

W tym tutorialu przeprowadzimy Cię przez cały proces — od wczytania pliku `.docx`, przez dostosowanie rozmycia cienia, aż po zapisanie wyniku. Po drodze poruszymy także powiązane tematy, takie jak **Aspose.Words shape shadow**, **Java shadow format** oraz ogólna **Word document shape manipulation**. Na końcu będziesz mieć gotowy do uruchomienia fragment kodu oraz jasne zrozumienie, dlaczego każda linijka ma znaczenie.

## Czego się nauczysz

- Jak wczytać dokument Word przy użyciu Aspose.Words for Java.  
- Jak zlokalizować pierwszy obiekt `Shape` w treści dokumentu.  
- Dokładne kroki, aby **skonfigurować promień rozmycia kształtu** oraz inne właściwości cienia, takie jak odległość i przezroczystość.  
- Jak zapisać zmiany do nowego pliku `.docx`.  

Nie są wymagane żadne zewnętrzne biblioteki poza Aspose.Words, a kod działa z Java 8‑plus oraz dowolną aktualną wersją Aspose.Words for Java (np. 24.9). Jeśli znasz podstawy składni Javy, poradzisz sobie bez problemu.

---

## Krok 1: Wczytaj dokument Word

Zanim będziesz mógł modyfikować jakikolwiek kształt, musisz mieć dokument w pamięci. Aspose.Words robi to w jednej linii.

```java
// Load the source .docx file
com.aspose.words.Document document = new com.aspose.words.Document("YOUR_DIRECTORY/input.docx");
```

**Dlaczego to ważne:**  
Utworzenie obiektu `Document` parsuje cały plik, dając dostęp do sekcji, akapitów, tabel, **i kształtów**. Pominięcie tego kroku pozostawi Cię bez kontekstu, w którym można zastosować promień rozmycia.

> **Porada:** Jeśli pracujesz z dużymi plikami, rozważ użycie `LoadOptions`, aby strumieniować tylko potrzebne części. Może to znacząco zmniejszyć zużycie pamięci.

---

## Krok 2: Pobierz docelowy kształt

Kształty mogą znajdować się wszędzie — w nagłówkach, stopkach, tabelach, gdzie tylko chcesz. Dla uproszczenia pobierzemy pierwszy kształt znaleziony w głównej treści pierwszej sekcji.

```java
// Navigate to the first shape in the document body
com.aspose.words.Shape shape = (com.aspose.words.Shape) document
        .getFirstSection()
        .getBody()
        .getChild(com.aspose.words.NodeType.SHAPE, 0, true);
```

**Dlaczego to ważne:**  
Wywołanie `getChild` przeszukuje drzewo węzłów metodą depth‑first, zwracając *pierwszy* kształt, który spełnia warunek `NodeType.SHAPE`. Jeśli dokument zawiera wiele kształtów, możesz zmienić indeks (`0`) lub iterować po `document.getChildNodes(NodeType.SHAPE, true)`.

> **Przypadek brzegowy:** Jeśli dokument nie zawiera kształtów, zmienna `shape` będzie równa `null` i kolejna linijka spowoduje `NullPointerException`. Zawsze zabezpiecz się przed tym w kodzie produkcyjnym.

---

## Krok 3: Skonfiguruj cień kształtu – ustaw promień rozmycia

Teraz najważniejsza część: regulacja promienia rozmycia. To ustawienie znajduje się w obiekcie `ShadowFormat` powiązanym z kształtem.

```java
// Access the shadow format of the shape
com.aspose.words.ShadowFormat shadow = shape.getShadowFormat();

// Set the blur radius (in points). Larger values produce a softer edge.
shadow.setBlurRadius(5.0);

// Optional: fine‑tune other shadow attributes
shadow.setDistanceX(3.0);          // Horizontal offset
shadow.setDistanceY(3.0);          // Vertical offset
shadow.setTransparency(0.3);      // 0 = fully opaque, 1 = fully transparent
```

### Zrozumienie liczb

- **Promień rozmycia** (`setBlurRadius`) określa, jak rozmyty będzie cień. Wartość `0` daje ostry brzeg, natomiast `10` lub wyższa tworzy miękki, rozmyty blask.  
- **DistanceX / DistanceY** przesuwają cień względem kształtu. Dodatni X przesuwa w prawo; dodatni Y przesuwa w dół.  
- **Transparency** sprawia, że cień jest przezroczysty. Przydatne, gdy chcesz subtelny efekt, a nie solidny czarny blok.

> **Dlaczego konfigurować promień rozmycia?**  
> W wielu szablonach korporacyjnych lekki rozmyty cień dodaje głębi bez rozpraszania czytelnika. To mała zmiana wizualna, która może znacząco podnieść postrzeganą jakość dokumentu.

---

## Krok 4: Zapisz zmodyfikowany dokument

Wszystkie ciężkie operacje zostały wykonane; teraz zapisz zmiany na dysk.

```java
// Persist the modified document
document.save("YOUR_DIRECTORY/output.docx");
```

**Dlaczego to ważne:**  
Wywołanie `save` zapisuje cały dokument, w tym zaktualizowany `ShadowFormat`. Jeśli potrzebujesz jedynie obrazu kształtu, możesz wyeksportować go za pomocą `shape.getImageData().save(...)`.

---

## Pełny działający przykład

Poniżej znajduje się kompletny, samodzielny program, który możesz skopiować i wkleić do dowolnego IDE Javy. Upewnij się, że plik JAR Aspose.Words for Java znajduje się w classpath.

```java
import com.aspose.words.*;

public class ConfigureShapeBlurRadius {
    public static void main(String[] args) throws Exception {
        // 1. Load the document
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Get the first shape (add null‑check for safety)
        Shape shape = (Shape) document.getFirstSection()
                .getBody()
                .getChild(NodeType.SHAPE, 0, true);
        if (shape == null) {
            System.out.println("No shape found in the document.");
            return;
        }

        // 3. Configure shadow – focus on blur radius
        ShadowFormat shadow = shape.getShadowFormat();
        shadow.setBlurRadius(5.0);          // Soft blur
        shadow.setDistanceX(3.0);           // Horizontal offset
        shadow.setDistanceY(3.0);           // Vertical offset
        shadow.setTransparency(0.3);        // Slightly transparent

        // 4. Save the result
        document.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved with configured shape blur radius.");
    }
}
```

**Oczekiwany wynik:**  
Uruchomienie programu tworzy nowy plik `output.docx`, w którym pierwszy kształt posiada delikatny, półprzezroczysty cień o promieniu rozmycia równym `5` punktów. Otwórz plik w Wordzie, zaznacz kształt i w sekcji **Shape Format → Shadow Effects → Shadow Options** zobaczysz ustawione wartości odzwierciedlone w interfejsie.

---

## Obsługa wielu kształtów i scenariusze zaawansowane

### Wybór konkretnego kształtu po nazwie

Jeśli dokument zawiera wiele kształtów, użyj **nazwy** kształtu (ustawionej w opcjach układu Worda) zamiast indeksu:

```java
Shape target = (Shape) document.getChildNodes(NodeType.SHAPE, true)
        .stream()
        .filter(node -> ((Shape) node).getName().equals("MyLogo"))
        .findFirst()
        .orElse(null);
```

### Stosowanie różnych promieni rozmycia

Możesz chcieć mocniejszego rozmycia dla grafik tła i subtelniejszego dla ikon. Pętla po wszystkich kształtach:

```java
for (Node node : document.getChildNodes(NodeType.SHAPE, true)) {
    Shape s = (Shape) node;
    ShadowFormat sf = s.getShadowFormat();
    sf.setBlurRadius(s.getName().contains("Background") ? 10.0 : 3.0);
}
```

### Uwagi dotyczące kompatybilności

- **Jednostki:** Aspose.Words używa punktów (1 pt = 1/72 cala). Jeśli pracujesz w milimetrach, przelicz odpowiednio.  
- **Wersja:** Pokazany API działa z Aspose.Words for Java 24.9 i nowszymi. Starsze wersje mogą używać `setBlurRadius(double)`, ale nie posiadają niektórych nowszych właściwości cienia.

---

## Typowe pułapki i jak ich unikać

| Pułapka | Dlaczego się pojawia | Rozwiązanie |
|---------|----------------------|-------------|
| `NullPointerException` przy `shape` | Dokument nie zawiera kształtów lub indeks jest poza zakresem | Dodaj sprawdzenie null przed dostępem do `ShadowFormat`. |
| Cień niewidoczny w Wordzie | Domyślny kolor cienia jest przezroczysty lub wartości odległości przesuwają go poza stronę | Ustaw widoczny `ShadowColor` (`shadow.setColor(Color.BLACK)`) i utrzymuj `DistanceX/Y` w umiarkowanych wartościach. |
| Promień rozmycia nie zmienia się | Używana jest przestarzała wersja Aspose.Words, która ignoruje tę właściwość | Zaktualizuj bibliotekę do najnowszej wersji; właściwość została wprowadzona w wersji 20.5. |
| Spowolnienie przy dużych dokumentach | Zapisywanie całego dokumentu po każdej modyfikacji kształtu | Zgrupuj wszystkie zmiany, a następnie wywołaj `save` raz. |

---

## Podsumowanie

Teraz wiesz, **jak skonfigurować promień rozmycia kształtu** w dokumencie Word przy użyciu Javy i Aspose.Words. Od wczytania pliku, przez pobranie właściwego `Shape`, modyfikację `ShadowFormat`, po zapisanie zmian — każdy krok został opisany wraz z praktycznymi wskazówkami.  

Technika nie ogranicza się do jednego kształtu; możesz ją skalować na cały dokument, stosować różne poziomy rozmycia lub łączyć z innymi atrybutami cienia, takimi jak **shadow transparency Java**. Kolejnymi logicznymi krokami są eksploracja **set blur radius** dla obrazów, eksperymenty z **Java shadow format** na wykresach lub głębsze zanurzenie się w **Word document shape manipulation** w celu dynamicznego generowania raportów.

Masz scenariusz, którego tutaj nie omówiono? Zostaw komentarz lub zajrzyj do dokumentacji Aspose.Words for Java, aby poznać bardziej zaawansowane efekty cieni. Szczęśliwego kodowania!

---

<img src="configure-shape-blur-radius.png" alt="Configure shape blur radius using Aspose.Words Java example" style="max-width:100%;">

---


## Co warto nauczyć się dalej?

Poniższe tutoriale obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne przykłady kodu oraz szczegółowe wyjaśnienia, pomagające opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}