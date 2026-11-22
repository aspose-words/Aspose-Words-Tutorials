---
category: general
date: 2026-11-22
description: Tanulja meg, hogyan töltsön be Markdown-t formázással Java-ban. Ez az
  útmutató megmutatja, hogyan olvassa be a Markdown-t formázással a LoadOptions és
  a Document használatával.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to load markdown
- read markdown with formatting
- Java markdown parsing
- LoadOptions import underline
- Document processing Java
language: hu
lastmod: 2026-11-22
og_description: Hogyan töltsünk be markdown-t formázással Java-ban. Kövesse ezt a
  teljes útmutatót a markdown formázott olvasásához, az aláhúzási stílusok megőrzéséhez
  és a Document objektumokkal való munkához.
og_image_alt: Java code snippet showing markdown loading with formatting enabled
og_title: Hogyan töltsünk be markdownot formázással Java-ban – lépésről lépésre útmutató
schemas:
- author: GroupDocs
  dateModified: '2026-11-22'
  description: Learn how to load markdown with formatting in Java. This guide shows
    you how to read markdown with formatting using LoadOptions and Document.
  headline: How to load markdown with formatting in Java
  type: TechArticle
tags:
- markdown
- java
- document-processing
title: Hogyan töltsük be a markdown-t formázással Java-ban
url: /hu/java/document-loading-and-saving/how-to-load-markdown-with-formatting-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan töltsünk be markdown-t formázással Java-ban

Ha **hogyan töltsünk be markdown-t** a vizuális stílusok megőrzése mellett, ez a bemutató egy azonnal futtatható megoldást nyújt. Megmutatja pontosan, hogyan **olvassuk be a markdown-t formázással**, például aláhúzott szöveggel, hogy a megjelenített dokumentum megegyezzen az eredeti forrással.

A útmutató minden lépést lefed a betöltő konfigurálásától a formázás importálásának ellenőrzéséig. Nem szükséges külső eszköz a standard GroupDocs.Viewer könyvtár (vagy bármely kompatibilis API, amely biztosítja a `LoadOptions` és `Document` osztályokat) mellett. A végére képes leszel a markdown betöltését integrálni bármely Java backend, webszolgáltatás vagy asztali alkalmazásba.

## Előfeltételek

Mielőtt elkezdenéd, győződj meg róla, hogy a következőkkel rendelkezel:

* Java 17 vagy újabb telepítve.  
* Maven vagy Gradle a függőségkezeléshez.  
* Hozzáférés a GroupDocs.Viewer (vagy ekvivalens) JAR-hoz, amely tartalmazza a `LoadOptions` és `Document` osztályokat.  
* Egy mintamarkdown fájl (`sample.md`), amely aláhúzási jelölést tartalmaz (pl. `<u>underlined text</u>` vagy `_underlined_` a parser függvényében).

## 1. lépés: A szükséges függőség hozzáadása

Ha Maven-t használsz, add hozzá a következőt a `pom.xml`-hez. Állítsd be a verziót a legújabb stabil kiadásra.

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>23.12</version>
</dependency>
```

Gradle felhasználók a következőt adhatják hozzá:

```groovy
implementation 'com.groupdocs:groupdocs-viewer:23.12'
```

A könyvtár beillesztése lehetővé teszi, hogy a `LoadOptions` és `Document` osztályok elérhetők legyenek fordítási időben.

## 2. lépés: LoadOptions konfigurálása az aláhúzott formázás importálásához

A `LoadOptions` objektum megmondja a parsernek, mely markdown funkciókat kell megőrizni. Az aláhúzott formázás engedélyezése biztosítja, hogy a vizuális stílus megjelenjen a létrejövő `Document`-ben.

```java
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Creates a LoadOptions instance with underline import enabled.
 *
 * @return configured LoadOptions
 */
private static LoadOptions createLoadOptions() {
    LoadOptions loadOptions = new LoadOptions();
    // Preserve underline markup when the markdown is parsed.
    loadOptions.setImportUnderlineFormatting(true);
    return loadOptions;
}
```

**Miért fontos:**  
`setImportUnderlineFormatting(true)` nélkül a parser eltávolítja az aláhúzott címkéket, és egyszerű szöveget hagy hátra. A flag engedélyezése megőrzi a stílust, ami elengedhetetlen, ha a downstream fogyasztó (pl. egy PDF generátor) a vizuális jelekre támaszkodik.

## 3. lépés: A markdown dokumentum betöltése a konfigurált beállításokkal

Most már beolvashatod a markdown fájlt. A `Document` konstruktor elfogadja a fájl elérési útját és a korábban előkészített `LoadOptions`-t.

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Loads a markdown file while preserving formatting.
 *
 * @param markdownPath absolute or relative path to the .md file
 * @param options      LoadOptions with formatting flags
 * @return Document representing the parsed markdown
 */
private static Document loadMarkdown(String markdownPath, LoadOptions options) {
    return new Document(markdownPath, options);
}
```

**Miért fontos:**  
A `LoadOptions` átadása a `Document` konstruktorának garantálja, hogy a parser a teljes importfolyamat során tiszteletben tartja az aláhúzott flag-et. A kapott `Document` objektum renderelhető, konvertálható vagy teljes formázással ellenőrizhető.

## 4. lépés: Az aláhúzott formázás ellenőrzése

Gyors módja annak, hogy megerősítsd az aláhúzás jelenlétét, ha a dokumentumot HTML-re rendereled és kiírod a kimenetet. A HTML `<u>` címkéket tartalmaz, ha az import sikeres volt.

```java
import com.groupdocs.viewer.options.HtmlViewOptions;
import com.groupdocs.viewer.Viewer;

/**
 * Renders the loaded Document to HTML and prints the first page.
 *
 * @param doc Document loaded from markdown
 */
private static void renderAndPrint(Document doc) {
    // Create a Viewer instance for rendering.
    Viewer viewer = new Viewer(doc);
    // Render the first page as HTML.
    HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources();
    viewer.view(viewOptions, 1);
    String html = viewOptions.getHtmlContent();

    System.out.println("Rendered HTML snippet:");
    System.out.println(html.substring(0, Math.min(html.length(), 500)));
}
```

A teljes program futtatása egy HTML részletet kell, hogy megjelenítsen, amely tartalmazza a `<u>underlined text</u>` elemet. Ha a címke hiányzik, ellenőrizd, hogy a `setImportUnderlineFormatting(true)` meghívásra került‑e a fájl betöltése előtt.

## Teljesen futtatható példa

Mindent egy helyre gyűjtve, itt egy önálló Java osztály, amelyet lefordíthatsz és futtathatsz:

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.Viewer;
import com.groupdocs.viewer.options.HtmlViewOptions;
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Demonstrates how to load markdown with formatting in Java.
 * The program reads a markdown file, preserves underline markup,
 * renders the first page to HTML, and prints a snippet.
 */
public class MarkdownLoader {

    public static void main(String[] args) {
        // Path to the markdown file – adjust as needed.
        String markdownPath = "sample.md";

        // Step 1: create LoadOptions with underline support.
        LoadOptions options = createLoadOptions();

        // Step 2: load the markdown document.
        Document doc = loadMarkdown(markdownPath, options);

        // Step 3: render the document to HTML and verify formatting.
        renderAndPrint(doc);
    }

    private static LoadOptions createLoadOptions() {
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setImportUnderlineFormatting(true);
        return loadOptions;
    }

    private static Document loadMarkdown(String path, LoadOptions options) {
        return new Document(path, options);
    }

    private static void renderAndPrint(Document doc) {
        Viewer viewer = new Viewer(doc);
        HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources();
        viewer.view(viewOptions, 1); // render first page
        String html = viewOptions.getHtmlContent();

        System.out.println("Rendered HTML snippet:");
        System.out.println(html.substring(0, Math.min(html.length(), 500)));
    }
}
```

**Várható kimenet (rövidítve):**

```
Rendered HTML snippet:
<div class="page">
  <p>This is a <u>underlined text</u> example from the markdown file.</p>
  …
```

Ha a `<u>` címke megjelenik, a markdown formázással betöltődött.

## Gyakori variációk és szélhelyzetek

| Helyzet                              | Mit kell módosítani                                                |
|--------------------------------------|--------------------------------------------------------------------|
| **Különböző markdown kiterjesztések**      | Használja a `loadOptions.setImportBoldFormatting(true)`‑t **félkövér** szöveghez. |
| **Nagy fájlok (> 10 MB)**              | Olvassa be a fájlt `FileInputStream`‑el, és adja át a streamet a `Document`‑nek. |
| **PDF kimenet szükséges**                    | Betöltés után használja a `PdfViewOptions`‑t a `Viewer`‑rel, hogy PDF‑et generáljon, amely megőrzi az aláhúzott stílusokat. |
| **Servlet konténerben futtatás**     | Tárolja a `Document`‑et a kérés hatókörében, és helyben renderelje HTML‑re. |

**Pro tipp:** Mindig hozz létre egy új `LoadOptions` példányt minden egyes betöltési művelethez. Ugyanazon objektum újrahasználata szálak között váratlan állapot‑szivárgáshoz vezethet.

## Összegzés

Most már tudod, **hogyan töltsünk be markdown‑t formázással Java‑ban**, és **hogyan olvassuk be a markdown‑t formázással** a `LoadOptions` használatával. A teljes példa bemutatja a konfigurációt, a betöltést és az ellenőrzést, így beágyazhatod ezt a mintát bármely Java projektbe, amely markdown fájlokat dolgoz fel.  

Ezután fedezd fel a kapcsolódó témákat, például **markdown olvasása képekkel**, **markdown konvertálása PDF‑re**, vagy **más stílusimportok testreszabása** (félkövér, dőlt, áthúzott). Ezek a kiterjesztések ugyanazt a mintát követik: állítsd be a `LoadOptions` flag‑eket, töltsd be a `Document`‑et, és rendereld a kívánt formátumban.

Jó kódolást!

## Mit tanulj meg legközelebb?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Hogyan töltsünk be markdown dokumentumot Java-ban egyedi importálási beállításokkal](/words/english/java/document-loading-and-saving/how-to-load-markdown-document-in-java-with-custom-import-opt/)
- [Hogyan olvassunk és töltsünk be egy Markdown fájlt Java-ban az Aspose.Words segítségével](/words/english/java/document-loading-and-saving/how-to-read-markdown-file-java-with-aspose-words/)
- [Hogyan töltsünk be Markdown-t Java-ban – Teljes útmutató](/words/english/java/document-loading-and-saving/how-to-load-markdown-in-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}