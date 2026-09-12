---
category: general
date: 2026-09-11
description: Grupuj kształty w programie Word i dodaj prostokątny kształt przy użyciu
  Aspose.Words dla Javy. Dowiedz się, jak ustawić rozmiar kształtu, grupować obiekty
  i zapisać dokument.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- how to group shapes
- how to add rectangle
language: pl
lastmod: 2026-09-11
og_description: Grupuj kształty w programie Word i dodaj prostokątny kształt przy
  użyciu Aspose.Words for Java. Ten samouczek pokazuje, jak ustawić rozmiar kształtu,
  grupować kształty i eksportować dokument.
og_image_alt: Screenshot showing grouped shapes in a Word document
og_title: Grupowanie kształtów w Word – dodaj prostokąt za pomocą Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  headline: Group shapes in Word and add a rectangle with Aspose.Words
  type: TechArticle
- description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  name: Group shapes in Word and add a rectangle with Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17 or later installed. * Maven or Gradle to manage dependencies.
      * A valid Aspose.Words for Java license (or a free evaluation key). * An image
      file (`sample.png`) placed in a known directory (replace `YOUR_DIRECTORY` with
      your actual path).'
  - name: Add a group shape
    text: A group shape is a container that can hold other shapes. Think of it as
      a folder for drawing objects.
  - name: How to add rectangle
    text: The code above demonstrates **how to add rectangle** by creating a `Shape`
      instance with `ShapeType.RECTANGLE` and then appending it to the `GroupShape`.
      This pattern works for any other shape type (e.g., `ELLIPSE`, `POLYLINE`).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Grupowanie kształtów w Wordzie i dodawanie prostokąta przy użyciu Aspose.Words
url: /pl/java/images-shapes/group-shapes-in-word-and-add-a-rectangle-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Grupowanie kształtów w Wordzie i dodawanie prostokąta za pomocą Aspose.Words

Jeśli potrzebujesz **grupować kształty w Wordzie** podczas programowego dodawania prostokąta, ten przewodnik zapewnia kompletną, gotową do uruchomienia rozwiązanie. Zobaczysz dokładnie, jak wstawić grupowy kształt, dodać kształt prostokąta, ustawić rozmiar kształtu i w końcu zapisać dokument, aby od razu móc zobaczyć wynik.

Praca z dokumentami Word często oznacza układanie wielu obiektów — obrazów, wykresów lub prostych kształtów geometrycznych — w jedną logiczną całość. Grupowanie tych obiektów ułatwia ich jednoczesne przesuwanie, obracanie lub stylizowanie. W tym samouczku omówimy także **jak dodać prostokąt** oraz **ustawić rozmiar kształtu** dla pełnej kontroli układu.

## Czego się nauczysz

* Jak utworzyć nowy dokument Word przy użyciu Aspose.Words for Java.  
* **Jak grupować kształty**, aby zachowywały się jako pojedynczy obiekt.  
* **Dodawanie prostokąta** do grupy oraz wstawianie obrazu w tej samej grupie.  
* **Ustawianie rozmiaru kształtu** zarówno dla prostokąta, jak i obrazu.  
* Zapisanie dokumentu i otwarcie go w Microsoft Word w celu weryfikacji wyniku.

### Wymagania wstępne

* Java 17 lub nowsza.  
* Maven lub Gradle do zarządzania zależnościami.  
* Ważna licencja Aspose.Words for Java (lub darmowy klucz ewaluacyjny).  
* Plik obrazu (`sample.png`) umieszczony w znanym katalogu (zastąp `YOUR_DIRECTORY` rzeczywistą ścieżką).

---

## Jak grupować kształty w Wordzie przy użyciu Aspose.Words

Pierwszym krokiem jest utworzenie obiektu `Document` oraz `DocumentBuilder`. Builder zapewnia wygodne API do wstawiania kształtów, tekstu i innych elementów.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Initialize the document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Dlaczego to ważne:** `DocumentBuilder` działa bezpośrednio na obiekcie `Document`, umożliwiając wstawianie kształtów bez ręcznego zarządzania niskopoziomowymi kolekcjami węzłów.

### Dodaj grupowy kształt

Grupowy kształt to kontener, który może przechowywać inne kształty. Można go traktować jak folder dla obiektów rysunkowych.

```java
        // Insert an empty group shape – this will hold the rectangle and the picture
        GroupShape group = builder.insertGroupShape();
```

Metoda `insertGroupShape()` tworzy węzeł `GroupShape` i zwraca go, aby później móc dołączyć do niego kształty podrzędne.  

---

## Dodaj prostokąt do grupy

Teraz **dodamy prostokąt** do wcześniej utworzonej grupy. Prostokąt będzie pełnił rolę tła lub obramowania dla obrazu.

```java
        // Create a rectangle shape with a specific size
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points
        rectangle.setHeight(50.0);   // height in points
        rectangle.setFillColor(java.awt.Color.LIGHT_GRAY);
        rectangle.setStrokeColor(java.awt.Color.DARK_GRAY);
        rectangle.setStrokeWeight(1.0);
        // Append the rectangle to the group
        group.appendChild(rectangle);
```

> **Wskazówka:** Ustawienie `FillColor` i `StrokeColor` sprawia, że prostokąt jest widoczny w końcowym dokumencie. Jeśli pominiesz te właściwości, kształt może być przezroczysty.

### Jak dodać prostokąt

Powyższy kod demonstruje **jak dodać prostokąt** poprzez utworzenie instancji `Shape` z `ShapeType.RECTANGLE` i dołączenie jej do `GroupShape`. Ten sam schemat działa dla każdego innego typu kształtu (np. `ELLIPSE`, `POLYLINE`).

---

## Ustaw rozmiar kształtu dla prostokąta i obrazu

Odpowiednie wymiarowanie zapewnia prawidłowe wyrównanie prostokąta i obrazu. Tutaj także **ustawiamy rozmiar kształtu** dla obrazu, który wstawimy później.

```java
        // Insert an image and set its size
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.png");
        picture.setWidth(100.0);   // match rectangle width
        picture.setHeight(50.0);   // match rectangle height
        // Append the picture to the same group
        group.appendChild(picture);
```

Zarówno prostokąt, jak i obraz mają teraz te same wymiary (100 × 50 punktów). Ponieważ należą do tej samej grupy, przesuwanie lub obracanie grupy wpłynie na oba kształty jednocześnie.

> **Dlaczego dopasować rozmiary?** Dopasowanie wymiarów gwarantuje, że obraz leży schludnie wewnątrz prostokąta, tworząc czysty efekt „obramowanego obrazu”.

---

## Zapisz dokument i zobacz wynik

Na koniec zapisujemy dokument na dysku. Otwierając plik w Microsoft Word, zobaczysz grupowane kształty jako jeden wybieralny obiekt.

```java
        // Save the document – the group will appear as one object in Word
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Po otwarciu `output.docx` zobaczysz prostokąt z wstawionym w nim obrazem. Kliknięcie kształtu zaznaczy zarówno prostokąt, jak i obraz, ponieważ są **zgrupowane**.

![group shapes in word example](https://example.com/images/group-shapes-word.png "group shapes in word example")

*Tekst alternatywny obrazu:* *przykład grupowania kształtów w Wordzie* – dokument Word pokazujący zgrupowany prostokąt i obraz.

---

## Często zadawane pytania i obsługa przypadków brzegowych

| Pytanie | Odpowiedź |
|----------|-----------|
| **Co zrobić, jeśli potrzebny jest inny rozmiar obrazu?** | Dostosuj `picture.setWidth()` i `picture.setHeight()` po wstawieniu. Prostokąt może zachować swój pierwotny rozmiar lub również zostać zmieniony, aby pasował. |
| **Czy mogę dodać więcej kształtów do tej samej grupy?** | Tak. Wywołaj `group.appendChild(newShape)` dla dowolnych dodatkowych obiektów `Shape`. |
| **Jak obrócić całą grupę?** | Użyj `group.setRotationAngle(double angleInRadians)`. Obrót zostanie zastosowany do każdego dziecka grupy. |
| **Co jeśli plik obrazu nie istnieje?** | `insertImage` rzuca `FileNotFoundException`. Owiń wywołanie w blok try‑catch i zapewnij zastępczy kształt placeholder. |
| **Czy można później rozgrupować?** | Wywołaj `group.removeAllChildren()`, aby odłączyć dzieci, a następnie wstaw je z powrotem do dokumentu indywidualnie. |

---

## Zakończenie

Masz teraz kompletny, gotowy do uruchomienia przykład, który pokazuje **jak grupować kształty w Wordzie**, **dodawać prostokąt**, **ustawiać rozmiar kształtu** i **zapisywać** dokument przy użyciu Aspose.Words for Java. Grupując prostokąt i obraz, możesz przesuwać, zmieniać rozmiar lub obracać je jako jedną całość — dokładnie to, czego wymaga wiele scenariuszy automatyzacji dokumentów.

Od tego momentu możesz rozważyć:

* Dodawanie pól tekstowych do tej samej grupy (styl w stylu `how to add rectangle`).  
* Stosowanie różnych wzorów wypełnienia lub gradientów (`set shape size` w połączeniu ze stylizacją).  
* Wykorzystanie tej techniki do grupowania wykresów, tabel lub SmartArt (`how to group shapes` w kontekście innych typów obiektów).  

Śmiało eksperymentuj z innymi typami kształtów, kolorami i opcjami układu. Powodzenia w kodowaniu!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne, działające przykłady kodu oraz szczegółowe wyjaśnienia krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}