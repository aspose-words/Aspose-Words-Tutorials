---
category: general
date: 2026-07-26
description: Wstaw prostokątny kształt w Javie przy użyciu Aspose.Words. Dowiedz się,
  jak ustawić rozmiar kształtu, pozycję kształtu oraz jak grupować kształty w pliku
  DOCX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- set shape size
- position shape
- how to group shapes
- how to add rectangle
language: pl
lastmod: 2026-07-26
og_description: Wstaw prostokątny kształt w Javie, aby tworzyć bogate grafiki w formacie
  DOCX. Postępuj zgodnie z tym przewodnikiem krok po kroku, aby łatwo ustawiać rozmiar
  kształtu, pozycję kształtu oraz grupować kształty.
og_image_alt: Screenshot showing a rectangle shape inserted and grouped in a Java‑generated
  Word document
og_title: Wstaw kształt prostokąta w Javie – opanuj grupowanie i pozycjonowanie
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert rectangle shape in Java using Aspose.Words. Learn how to set
    shape size, position shape, and how to group shapes in a DOCX file.
  headline: Insert Rectangle Shape in Java – Group and Position Shapes
  type: TechArticle
tags:
- Aspose.Words
- Java
- Shapes
- DOCX
title: Wstaw kształt prostokąta w Javie – grupuj i pozycjonuj kształty
url: /pl/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wstawianie prostokątnego kształtu w Javie – grupowanie i pozycjonowanie kształtów

Czy kiedykolwiek potrzebowałeś **wstawić prostokątny kształt** do dokumentu Word podczas pisania kodu w Javie? Nie jesteś jedyny — programiści tworzący raporty, faktury lub własne szablony często napotykają ten problem. Dobrą wiadomością jest to, że za pomocą kilku linii Aspose.Words for Java możesz **wstawić prostokątny kształt**, **ustawić rozmiar kształtu**, **pozycjonować kształt**, a nawet **jak grupować kształty**, aby poruszały się jako jedna jednostka.

W tym przewodniku przeprowadzimy Cię przez cały proces, od utworzenia pustego dokumentu po zapisanie pliku `.docx` zawierającego dwa prostokąty starannie zgrupowane razem. Po zakończeniu będziesz wiedział **jak dodać prostokąt** do obiektów, kontrolować ich wymiary, umieszczać je dokładnie tam, gdzie chcesz, i łączyć w wielokrotnego użytku grupę. Nie są wymagane żadne zewnętrzne biblioteki poza Aspose.Words, a kod działa z Java 8 i nowszymi.

## Prerequisites

- Java 8 lub nowsza zainstalowana (używam JDK 17, ale wszystko co obsługuje Maven będzie działać)
- Aspose.Words for Java 23.9 lub nowszy – dodaj zależność do swojego `pom.xml` lub pobierz plik JAR
- Podstawowa znajomość składni Java (jeśli potrafisz napisać metodę `main`, jesteś gotowy)
- IDE lub edytor tekstu według własnego wyboru (IntelliJ IDEA, Eclipse, VS Code…)

> **Wskazówka:** Jeśli używasz Maven, zależność wygląda tak:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Teraz, gdy mamy przygotowane podstawy, zanurzmy się w kod.

## Insert Rectangle Shape and Set Its Size

## Wstawianie prostokątnego kształtu i ustawianie jego rozmiaru

Pierwszą rzeczą, którą zrobisz, jest utworzenie nowego `Document` i `DocumentBuilder`. Builder jest Twoim „piórem”, które rysuje kształty na stronie. Poniżej **wstawiamy prostokątny kształt** i od razu **ustawiamy rozmiar kształtu** na 100 × 80 punktów.

```java
import com.aspose.words.*;

public class GroupedRectanglesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder to add content
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape(400, 200);
        // The group itself is 400×200 points – adjust as needed

        // ---------- First rectangle ----------
        // Insert rectangle shape
        Shape rectangle1 = new Shape(document, ShapeType.RECTANGLE);
        // Set shape size
        rectangle1.setWidth(100);
        rectangle1.setHeight(80);
        // Position shape inside the group
        rectangle1.setLeft(20);   // 20 points from the left edge of the group
        rectangle1.setTop(30);    // 30 points from the top edge of the group
        // Add the rectangle to the group
        group.appendChild(rectangle1);
```

Zauważ, że wywołania `setWidth`/`setHeight` **ustawiają rozmiar kształtu** w punktach (1 pt ≈ 1/72 cala). Możesz także użyć `setSize`, jeśli wolisz jedną metodę, ale explicite wywołania jasno określają intencję.

## Position Shape on the Page

## Pozycjonowanie kształtu na stronie

Po utworzeniu pierwszego prostokąta musimy **pozycjonować kształt** drugiego, aby nie nachodził na pierwszy. Pozycjonowanie działa tak samo: ustawiasz właściwości `Left` i `Top` względem pochodzenia grupy.

```java
        // ---------- Second rectangle ----------
        Shape rectangle2 = new Shape(document, ShapeType.RECTANGLE);
        rectangle2.setWidth(120);
        rectangle2.setHeight(60);
        // Position this rectangle a bit farther to the right and lower down
        rectangle2.setLeft(150);
        rectangle2.setTop(50);
        group.appendChild(rectangle2);
```

Jeśli zastanawiasz się, dlaczego używamy `setLeft` zamiast `setX`, to dlatego, że Aspose.Words przyjmuje klasyczny system współrzędnych Windows GDI — `Left` to przesunięcie w poziomie, `Top` to przesunięcie w pionie. Zmiana tych wartości pozwala precyzyjnie dopasować układ bez manipulacji tabelami czy akapitami.

## How to Group Shapes

## Jak grupować kształty

Możesz się zapytać: „Po co w ogóle grupa?” Grupowanie ma sens, gdy chcesz, aby kształty poruszały się razem, obracały się jako jednostka lub dzieliły wspólny styl. W powyższym fragmencie już utworzyliśmy `GroupShape` za pomocą `builder.insertGroupShape`. Ten obiekt jest w zasadzie kontenerem — pomyśl o nim jak o folderze, który przechowuje inne pliki kształtów.

> **Dlaczego to ważne:** Jeśli później zdecydujesz się dodać podpis lub obrócić cały diagram, wystarczy zmodyfikować grupę, a nie każdy prostokąt osobno.

## How to Add Rectangle to a Group

## Jak dodać prostokąt do grupy

Dodanie **jak dodać prostokąt** do grupy polega po prostu na wywołaniu `group.appendChild(rectangle)`. W tle Aspose.Words aktualizuje wewnętrzną kolekcję grupy i automatycznie przelicza ramkę ograniczającą, tak aby grupa nadal mieściła się w zadeklarowanej szerokości i wysokości.

```java
        // At this point the group already contains both rectangles.
        // You can also set the group’s border or fill if you like.
        group.getShapeStyle().setLineColor(Color.BLACK);
        group.getShapeStyle().setFillColor(Color.LIGHTGRAY);
```

Możesz eksperymentować z innymi `ShapeType` — `ShapeType.ELLIPSE`, `ShapeType.TRIANGLE` itd. — i ten sam wzorzec `appendChild` działa.

## Save the Document

## Zapisz dokument

Na koniec zapisujemy dokument na dysku. Ścieżka może być bezwzględna lub względna; po prostu upewnij się, że folder istnieje.

```java
        // Step 5: Save the document containing the grouped shapes
        String outPath = "output/GroupShape.docx";
        document.save(outPath);
        System.out.println("Document saved to: " + outPath);
    }
}
```

Kiedy otworzysz `GroupShape.docx` w Microsoft Word, zobaczysz dwa prostokąty obok siebie, oba zamknięte w jasnoszarej ramce. Zaznaczenie szarej ramki podświetli oba prostokąty jednocześnie — dowód, że **jak grupować kształty** naprawdę działa.

![Grouped rectangles in a Word document](placeholder-image.png){: .center-image alt="Insert rectangle shape example showing two rectangles grouped in a Java‑generated DOCX file"}

*Tekst alternatywny obrazu (SEO):* **przykład wstawiania prostokątnego kształtu pokazujący dwa prostokąty zgrupowane w pliku DOCX wygenerowanym w Javie**.

## Expected Output

## Oczekiwany wynik

- Plik `GroupShape.docx` znajdujący się w folderze `output`.
- W dokumencie: grupa o wymiarach 400 × 200 pt zawierająca dwa prostokąty (100 × 80 pt i 120 × 60 pt) umieszczone odpowiednio w (20, 30) i (150, 50).
- Grupa ma cienką czarną ramkę i jasnoszare wypełnienie, co wizualnie uwidacznia grupowanie.

Otwórz plik i spróbuj przeciągnąć szarą ramkę — oba prostokąty powinny poruszać się razem. Jeśli tak się nie dzieje, sprawdź ponownie, czy wywołałeś `group.appendChild` dla każdego kształtu.

## Common Pitfalls & Edge Cases

## Częste problemy i przypadki brzegowe

| Problem | Dlaczego się pojawia | Rozwiązanie |
|---------|----------------------|-------------|
| **Prostokąty pojawiają się poza stroną** | Wartości `Left`/`Top` przekraczają wymiary grupy | Zwiększ rozmiar grupy (`insertGroupShape(width, height)`) lub zmniejsz przesunięcia |
| **Grupa znika po zapisaniu** | Właściwości `Width`/`Height` grupy są ustawione na 0 | Podaj nie‑zerowe wymiary przy wywoływaniu `insertGroupShape` |
| **Kolory kształtu wyglądają niepoprawnie** | Domyślne wypełnienie jest przezroczyste; Word może wyświetlać je jako białe | Jawnie ustaw `setFillColor` lub użyj `ShapeStyle` |
| **Wyjątek `ArgumentOutOfRangeException`** | Używanie ujemnych współrzędnych | Utrzymuj `Left` i `Top` nieujemne |

Rozwiązanie tych problemów na wczesnym etapie chroni Cię przed bólami głowy typu „dlaczego mój kształt znika?”, z którymi spotyka się wielu nowicjuszy.

## Recap & Next Steps

## Podsumowanie i kolejne kroki

Omówiliśmy pełny cykl życia **wstawiania prostokątnego kształtu** w Javie: tworzenie dokumentu, **ustawianie rozmiaru kształtu**, **pozycjonowanie kształtu**, **jak grupować kształty** oraz **jak dodać prostokąt** do tej grupy. Pełny, działający przykład znajduje się w powyższym bloku kodu i możesz go wkleić bezpośrednio do projektu Maven, aby zobaczyć rezultat.

Co dalej? Rozważ eksperymentowanie z:
- Dodawanie tekstu wewnątrz każdego prostokąta za pomocą

## What Should You Learn Next?

## Co powinieneś nauczyć się dalej?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}