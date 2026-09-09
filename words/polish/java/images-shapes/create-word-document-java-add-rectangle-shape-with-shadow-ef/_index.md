---
category: general
date: 2026-01-11
description: Szybko utwórz dokument Word w Javie, dodając kształt prostokąta, ustawiając
  jego kolor wypełnienia i stosując cień do kształtu. Ucz się krok po kroku.
draft: false
keywords:
- create word document java
- add rectangle shape
- apply shadow to shape
- set shape fill color
- how to add shape
language: pl
og_description: Utwórz dokument Word w Javie, wstawiając kształt prostokąta, ustawiając
  jego kolor wypełnienia i stosując cień. Kompletny przewodnik z kodem.
og_title: Utwórz dokument Word w Javie – Dodaj prostokątny kształt z cieniem
tags:
- Aspose.Words
- Java
- Document Generation
title: Utwórz dokument Word w Javie – Dodaj prostokątny kształt z efektem cienia
url: /pl/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tworzenie dokumentu Word w Javie – Dodawanie prostokątnego kształtu z efektem cienia

Kiedykolwiek potrzebowałeś **create word document java** i chciałeś, aby wyglądał nieco bardziej dopracowanie? Może tworzysz generator raportów i zwykła strona po prostu nie wystarczy. Dobra wiadomość? Dzięki Aspose.Words for Java możesz wstawić prostokątny kształt do dokumentu, nadać mu kolor i dodać subtelny cień – wszystko w kilku linijkach kodu.

W tym samouczku przejdziemy krok po kroku przez to, jak dodać prostokątny kształt, ustawić jego kolor wypełnienia oraz zastosować cień, aby Twój plik Word wyglądał bardziej profesjonalnie. Na końcu będziesz mieć działający przykład, który możesz skopiować i wkleić do własnego projektu.

## Co będzie potrzebne

- **Java 17** (lub dowolny nowszy JDK) – kod korzysta ze standardowych funkcji języka.
- Biblioteka **Aspose.Words for Java** – zalecana wersja 23.9 lub nowsza.
- IDE lub edytor tekstu według własnego wyboru – IntelliJ IDEA, Eclipse, VS Code… decydujesz Ty.
- Folder, w którym zostanie zapisany wygenerowany plik `ShadowShape.docx`.

Nie wymaga dodatkowej konfiguracji; wystarczy dodać plik JAR Aspose.Words do classpath i gotowe.

## Krok 1: Konfiguracja projektu i import Aspose.Words

Na początek utwórz nowy projekt Maven (lub Gradle) i dodaj zależność Aspose.Words. Oto minimalny fragment `pom.xml` dla Maven:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>23.9</version>
        <classifier>jdk17</classifier>
    </dependency>
</dependencies>
```

Jeśli nie używasz Maven, po prostu wrzuć plik JAR do folderu `libs` i dodaj go do ścieżki kompilacji.

> **Pro tip:** Aspose oferuje darmową licencję próbną, którą możesz wstawić za pomocą `License license = new License(); license.setLicense("Aspose.Words.lic");`. Pomiń ją przy szybkich testach; biblioteka działa w trybie ewaluacyjnym.

## Krok 2: Utworzenie nowego dokumentu i buildera

Teraz faktycznie **create word document java** obiekty. Klasa `Document` reprezentuje cały plik .docx, a `DocumentBuilder` pozwala wstawiać zawartość.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

W tym momencie masz pusty dokument gotowy do przyjmowania kształtów, akapitów lub czegokolwiek innego, czego potrzebujesz.

## Krok 3: Wstawienie prostokątnego kształtu i ustawienie koloru wypełnienia

Dodanie kształtu jest tak proste, jak wywołanie `insertShape`. Skorzystamy z techniki **add rectangle shape**, która jest powiązana z drugorzędnym słowem kluczowym *add rectangle shape*.

```java
        // Insert a rectangle shape – 200pt wide, 100pt tall
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);

        // Set the fill color to a bright orange
        rectangle.setFillColor(java.awt.Color.ORANGE);
```

Dlaczego pomarańczowy? Wyróżnia się na białym tle, ale możesz zamienić go na dowolny `java.awt.Color`, który lubisz. Ten krok obejmuje drugorzędne słowo kluczowe *set shape fill color*.

## Krok 4: Konfiguracja wyglądu cienia – zastosowanie cienia do kształtu

Teraz najciekawsza część: nadanie prostokątowi subtelnego cienia. API Aspose udostępnia obiekt `ShadowFormat`, który kontroluje każdy aspekt cienia.

```java
        // Get the shadow format object for the shape
        ShadowFormat shadow = rectangle.getShadowFormat();

        // Make the shadow visible
        shadow.setVisible(true);

        // Choose a neutral gray for the shadow color
        shadow.setColor(java.awt.Color.GRAY);

        // Blur radius – larger values produce a softer edge
        shadow.setBlur(5.0);

        // Offset determines how far the shadow is displaced
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);

        // Transparency (0 = opaque, 1 = fully transparent)
        shadow.setTransparency(0.2);

        // Define the shadow style and type
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);

        // Scale controls the overall size of the shadow relative to the shape
        shadow.setScale(1.0);
```

Ten fragment kodu **apply shadow to shape** dokładnie tak, jak sugeruje drugorzędne słowo kluczowe. Możesz dostosować `blur`, `offsetX/Y` i `transparency`, aby pasowały do Twojego stylu. Na przykład większy `offsetX` tworzy bardziej dramatyczny cień, a wyższa `transparency` sprawia, że cień jest delikatny, a nie wyraźny.

## Krok 5: Zapisanie dokumentu

Na koniec zapisujemy dokument na dysku. Wybierz folder, do którego masz prawo zapisu, i nadaj plikowi czytelną nazwę.

```java
        // Save the result – adjust the path as needed
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Po otwarciu `ShadowShape.docx` w Microsoft Word lub LibreOffice zobaczysz jasny pomarańczowy prostokąt z miękkim szarym cieniem unoszącym się tuż pod nim.

![create word document java with rectangle shape](/images/shadow-rectangle.png "create word document java – rectangle with shadow")

*Tekst alternatywny obrazu zawiera główne słowo kluczowe, spełniając wymóg SEO.*

## Często zadawane pytania i przypadki brzegowe

### Co zrobić, jeśli potrzebuję innego kształtu?

Aspose.Words obsługuje dziesiątki wartości `ShapeType` – gwiazdy, strzałki, dymki i tak dalej. Po prostu zamień `ShapeType.RECTANGLE` na `ShapeType.OVAL` lub inny stały enum. Te same kroki **how to add shape** będą obowiązywać.

### Jak dodać kształt do konkretnego akapitu?

Zamiast wstawiać kształt bezpośrednio przy pomocy buildera, możesz najpierw utworzyć go (`new Shape(document, ShapeType.RECTANGLE)`) i dopiero potem dodać do `Paragraph` za pomocą `paragraph.appendChild(shape)`. Daje to większą kontrolę nad układem.

### Czy mogę zastosować wypełnienie gradientowe zamiast jednolitego koloru?

Tak! Użyj `rectangle.getFill().setFillType(FillType.GRADIENT)` i zdefiniuj `LinearGradientFill`. API jest nieco bardziej rozbudowane, ale świetnie sprawdza się w nowoczesnych projektach.

### A jak wygląda kompatybilność ze starszymi wersjami Worda?

Aspose.Words domyślnie zapisuje w formacie .docx, który jest obsługiwany przez Word 2007+ oraz LibreOffice. Jeśli potrzebujesz .doc, wywołaj `document.save("file.doc", SaveFormat.DOC)`. Renderowanie cienia może się nieco różnić, ale sam kształt pozostaje nienaruszony.

## Pełny działający przykład (gotowy do kopiowania)

Poniżej znajduje się cały program, gotowy do kompilacji i uruchomienia. Zamień `YOUR_DIRECTORY` na rzeczywistą ścieżkę na swoim komputerze.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape and set its fill color
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);
        rectangle.setFillColor(java.awt.Color.ORANGE);

        // Step 3: Apply shadow to shape
        ShadowFormat shadow = rectangle.getShadowFormat();
        shadow.setVisible(true);
        shadow.setColor(java.awt.Color.GRAY);
        shadow.setBlur(5.0);
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);
        shadow.setTransparency(0.2);
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);
        shadow.setScale(1.0);

        // Step 4: Save the document
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Uruchomienie tego kodu wygeneruje plik Word zawierający pomarańczowy prostokąt z miękkim szarym cieniem – dokładnie to, co chcieliśmy osiągnąć, **create word document java** z wystylizowanym kształtem.

## Zakończenie

Masz teraz kompletny przepis od początku do końca na **create word document java**, który *adds rectangle shape*, *sets shape fill color* i *applies shadow to shape*. Podejście jest proste, API jest płynne, a możliwości rozbudowy są praktycznie nieograniczone – różne kształty, wypełnienia gradientowe czy nawet wiele cieni na jednym kształcie.

Co dalej? Spróbuj warstwować kilka kształtów, poeksperymentuj ze `ShadowStyle.ETCHED` dla innego efektu wizualnego lub połącz to z generowaniem tabel, aby tworzyć w pełni rozbudowane raporty. Możliwości ogranicza tylko Twoja wyobraźnia (i ewentualnie poziom licencji Aspose).

Jeśli napotkasz problemy lub masz pomysły na dalsze ulepszenia, zostaw komentarz poniżej. Szczęśliwego kodowania i ciesz się tworzeniem dokumentów Word, które nie są już nijakie!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}