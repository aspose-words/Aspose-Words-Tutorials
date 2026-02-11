---
category: general
date: 2026-02-10
description: Utwórz kształt prostokąta w dokumencie Word przy użyciu Aspose.Words
  for Java. Dowiedz się, jak ustawić kolor cienia, jak dodać cień oraz jak programowo
  tworzyć dokument Word.
draft: false
keywords:
- create rectangle shape
- set shadow color
- create word document
- how to add shadow
- how to create shape
language: pl
og_description: Utwórz kształt prostokąta w dokumencie Word przy użyciu Aspose.Words
  for Java. Postępuj zgodnie z tym samouczkiem krok po kroku, aby ustawić kolor cienia,
  dodać cień i utworzyć dokument Word.
og_title: Tworzenie prostokątnego kształtu w Wordzie przy użyciu Javy – pełny przewodnik
tags:
- Aspose.Words
- Java
- Document Automation
title: Utwórz prostokątny kształt w Wordzie za pomocą Javy – pełny przewodnik
url: /pl/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

.

Let's produce translation.

Will keep shortcodes at start and end.

Proceed.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tworzenie prostokątnego kształtu w Wordzie przy użyciu Java – Pełny przewodnik

Kiedykolwiek potrzebowałeś **utworzyć prostokątny kształt** w dokumencie Word, ale nie wiedziałeś od czego zacząć? Nie jesteś sam — wielu programistów napotyka ten problem, gdy po raz pierwszy próbują rysować grafikę w Wordzie programowo. Dobra wiadomość? Dzięki Aspose.Words for Java możesz w kilka sekund dodać prostokąt na stronę, nadać mu ładny cień i zapisać plik. W tym tutorialu przejdziemy krok po kroku, **jak dodać cień**, **ustawić kolor cienia** oraz **utworzyć dokument Word** od podstaw.  

Omówimy wszystko, co jest potrzebne: wymagane biblioteki, każdy wiersz kodu, dlaczego niektóre ustawienia mają znaczenie oraz kilka trików, których nie znajdziesz w oficjalnej dokumentacji. Po zakończeniu będziesz mieć gotowy przykład, który tworzy prostokątny kształt z delikatnym szarym cieniem, zapisywany jako *Shadow.docx*.

## Wymagania wstępne – Co potrzebujesz przed rozpoczęciem

Zanim przejdziemy do kodu, upewnij się, że masz następujące elementy:

| Wymaganie | Powód |
|-----------|-------|
| Java Development Kit (JDK) 8 lub nowszy | Aspose.Words działa na dowolnym nowoczesnym JDK. |
| Maven lub Gradle (opcjonalnie) | Ułatwia dodanie zależności Aspose.Words. |
| Licencja Aspose.Words for Java (lub darmowa wersja próbna) | Biblioteka jest komercyjna; wersja próbna wystarczy do testów. |
| IDE (IntelliJ IDEA, Eclipse, VS Code itp.) | Umożliwia szybkie uruchomienie i debugowanie przykładu. |

Jeśli już masz projekt Java, po prostu dodaj współrzędną Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

Nie potrzebujesz żadnej skomplikowanej konfiguracji — wystarczy zwykła metoda `public static void main`.

![przykład tworzenia prostokątnego kształtu](https://example.com/rectangle-shadow.png "tworzenie prostokątnego kształtu z cieniem w Wordzie")

*Tekst alternatywny obrazu: przykład tworzenia prostokątnego kształtu pokazujący cyjanowy prostokąt z szarym cieniem.*

## Krok 1 – Utworzenie nowego dokumentu Word

Pierwszą rzeczą, którą musimy zrobić, jest utworzenie pustego dokumentu. Pomyśl o tym jak o otwarciu nowego pliku Word, na którym później będziesz rysować.

```java
// Step 1: Initialize a blank Document object
Document document = new Document();
```

Dlaczego zaczynamy od pustego `Document`? Ponieważ Aspose.Words traktuje klasę `Document` jako płótno dla wszystkich kolejnych operacji — dodawania akapitów, tabel czy kształtów. Jeśli pominiesz ten krok, natychmiast po próbie wstawienia czegokolwiek otrzymasz `NullPointerException`.

## Krok 2 – Konfiguracja DocumentBuilder

`DocumentBuilder` to Twój przyjazny pióro, które zapisuje do `Document`. To zalecany sposób dodawania treści, ponieważ automatycznie zarządza pozycją kursora.

```java
// Step 2: Create a DocumentBuilder tied to our document
DocumentBuilder builder = new DocumentBuilder(document);
```

Możesz się zastanawiać: „Dlaczego nie manipulować dokumentem bezpośrednio?” Odpowiedź: builder ukrywa szczegóły niskiego poziomu, takie jak obsługa sekcji, co sprawia, że kod jest czystszy i mniej podatny na błędy.

## Krok 3 – Wstawienie prostokątnego kształtu

Teraz przychodzi najciekawsza część — **jak utworzyć kształt**. Wstawimy prostokąt o wymiarach 100 × 50 punktów i nadamy mu wypełnienie cyjanem, aby był widoczny.

```java
// Step 3: Insert a rectangle shape of size 100x50 points
Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

// Apply a solid fill color to make the shape visible
rectangle.setFillColor(java.awt.Color.CYAN);
```

Kilka uwag:

* `ShapeType.RECTANGLE` informuje Aspose, że chcemy prostokąt; możesz zamienić go na `OVAL`, `LINE` itp.
* Wymiary podawane są w punktach (1 pt ≈ 1/72 cala). Dostosuj je do swojego układu.
* Bez koloru wypełnienia kształt byłby niewidoczny na białej stronie — stąd cyjan.

## Krok 4 – Dodanie cienia i **ustawienie koloru cienia**

Tutaj odpowiadamy na pytanie **jak dodać cień**. Obiekt `ShadowFormat` kontroluje każdy wizualny aspekt cienia, od koloru po promień rozmycia.

```java
// Step 4: Enable the shape's shadow and configure its appearance
rectangle.getShadowFormat().setVisible(true);                     // Turn the shadow on
rectangle.getShadowFormat().setColor(java.awt.Color.GRAY);      // **set shadow color** to gray
rectangle.getShadowFormat().setBlurRadius(5.0);                  // Soft blur for realism
rectangle.getShadowFormat().setOffsetX(4.0);                     // Horizontal offset
rectangle.getShadowFormat().setOffsetY(4.0);                     // Vertical offset
rectangle.getShadowFormat().setTransparency(0.3);               // 30 % transparent
```

Dlaczego właśnie te wartości?

* **Widoczność** – Bez `setVisible(true)` pozostałe ustawienia są ignorowane.
* **Kolor** – Szary to neutralny wybór, który działa zarówno na jasnym, jak i ciemnym tle. Śmiało zamień `java.awt.Color.GRAY` na dowolny inny `java.awt.Color`.
* **Promień rozmycia** – Wartość `5.0` daje delikatne piórko; większe liczby sprawiają, że cień staje się bardziej rozproszony.
* **OffsetX/Y** – Przesunięcia przesuwają cień w prawo i w dół, imitując źródło światła z górnego‑lewego rogu.
* **Przezroczystość** – Cień półprzezroczysty lepiej komponuje się ze stroną, zwłaszcza przy drukowaniu.

Jeśli potrzebujesz ostrzejszego wyglądu, zmniejsz promień rozmycia do `0` i zwiększ offset. Eksperymentowanie jest zalecane — cienie są bardzo wizualne, a odpowiednie ustawienia zależą od projektu dokumentu.

## Krok 5 – Zapisanie dokumentu

Na koniec zapisujemy wszystko do pliku `.docx`. Możesz wybrać dowolną ścieżkę, pod warunkiem że katalog istnieje.

```java
// Step 5: Save the document with the shaped shadow to a file
document.save("YOUR_DIRECTORY/Shadow.docx");
```

Gdy otworzysz *Shadow.docx* w Microsoft Word, zobaczysz cyjanowy prostokąt z subtelnym szarym cieniem, przesuniętym o 4 pt w prawo i w dół. To kompletny **workflow tworzenia dokumentu Word**.

### Oczekiwany rezultat

| Element | Wygląd |
|---------|--------|
| Prostokąt | Wypełnienie cyjanem, rozmiar 100 × 50 pt |
| Cień | Szary, 30 % przezroczysty, rozmycie 5 pt, offset (4, 4) |
| Plik | `Shadow.docx` zapisany w podanej ścieżce |

Jeśli kształt się nie pojawi, sprawdź, czy kolor wypełnienia nie jest taki sam jak tło strony oraz czy cień jest ustawiony jako widoczny.

## Porady profesjonalne i typowe pułapki

* **Porada pro:** Użyj `rectangle.setStrokeColor(java.awt.Color.BLACK);`, jeśli chcesz obramowanie wokół kształtu. Dzięki temu prostokąt lepiej wyróżnia się na wydruku.
* **Uwaga:** Zapisywanie do folderu tylko do odczytu spowoduje `IOException`. Wybierz lokalizację z prawami zapisu lub zmień uprawnienia.
* **Przypadek brzegowy:** Jeśli potrzebujesz przezroczystego wypełnienia (brak koloru), wywołaj `rectangle.setFillColor(java.awt.Color.WHITE); rectangle.setFillOpacity(0.0);`. Kształt nadal rzuci cień, co może być przydatne przy grafikach w stylu znaku wodnego.
* **Uwaga o wydajności:** Dodawanie setek kształtów w pętli może zwiększyć zużycie pamięci. Wywołuj `document.save` tylko raz po dodaniu wszystkich kształtów.

## Pełny działający przykład

Poniżej znajduje się cały program, który możesz skopiować i wkleić do klasy Java o nazwie `ShadowDemo`. Kompiluje się i uruchamia bez zmian (oczywiście przy założeniu, że masz plik JAR Aspose.Words w classpath).

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to construct the document content
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Apply a solid fill color to make the shape visible
        rectangle.setFillColor(java.awt.Color.CYAN);

        // Step 4: Enable the shape's shadow and configure its appearance
        rectangle.getShadowFormat().setVisible(true);
        rectangle.getShadowFormat().setColor(java.awt.Color.GRAY); // set shadow color
        rectangle.getShadowFormat().setBlurRadius(5.0);
        rectangle.getShadowFormat().setOffsetX(4.0);
        rectangle.getShadowFormat().setOffsetY(4.0);
        rectangle.getShadowFormat().setTransparency(0.3);

        // Step 5: Save the document with the shaped shadow to a file
        document.save("YOUR_DIRECTORY/Shadow.docx");
    }
}
```

Uruchom program, otwórz powstały *Shadow.docx* i zobaczysz prostokąt z cieniem dokładnie takim, jak opisano.

## Co zrobić, jeśli potrzebujesz więcej kształtów?

Możesz się zastanawiać: „Czy mogę **tworzyć prostokątny kształt** wielokrotnie lub używać innych kształtów?” Oczywiście. Po prostu umieść kod wstawiania w pętli i dostosuj współrzędne przy pomocy `builder.moveTo` lub `builder.insertParagraph`. Te same ustawienia cienia możesz ponownie wykorzystać, wyodrębniając je do metody pomocniczej:

```java
private static void applyStandardShadow(Shape shape) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(java.awt.Color.GRAY);
    shape.getShadowFormat().setBlurRadius(5.0);
    shape.getShadowFormat().setOffsetX(4.0);
    shape.getShadowFormat().setOffsetY(4.0);
    shape.getShadowFormat().setTransparency(0.3);
}
```

Wywołaj `applyStandardShadow(rectangle);` po każdym wstawieniu kształtu, aby utrzymać kod DRY (Don’t Repeat Yourself).

## Kolejne kroki – Wyjście poza podstawy

Teraz, gdy wiesz **jak dodać cień**, rozważ zgłębienie następujących tematów:

* **Jak ustawić kolor cienia** dla fragmentów tekstu – nadaje tytułom subtelny podniesiony efekt.
* **Tworzenie dokumentu Word** z tabelami i obrazami – połącz kształty z inną zawartością.
* **Jak tworzyć animacje kształtów** przy użyciu wbudowanych funkcji Worda

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}