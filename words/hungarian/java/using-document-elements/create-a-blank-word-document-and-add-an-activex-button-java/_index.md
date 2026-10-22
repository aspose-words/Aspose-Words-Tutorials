---
category: general
date: 2026-10-16
description: Hozzon létre egy üres Word‑dokumentumot Java‑val, és tanulja meg, hogyan
  adhat hozzá egy ActiveX‑gombot, állíthatja be a feliratát, valamint módosíthatja
  a méreteit az Aspose.Words segítségével.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add activex button
- set button caption
- set button dimensions
language: hu
lastmod: 2026-10-16
og_description: Hozzon létre egy üres Word dokumentumot Java-val, majd adjon hozzá
  egy ActiveX gombot, állítsa be a feliratát, és határozza meg a méreteit az Aspose.Words
  segítségével.
og_image_alt: Screenshot showing a blank Word document with an ActiveX button inserted
og_title: Üres Word-dokumentum létrehozása és ActiveX gomb beágyazása – Java útmutató
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document with Java and learn how to add an ActiveX
    button, set its caption, and adjust its dimensions using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button (Java)
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
title: Hozzon létre egy üres Word-dokumentumot, és adjon hozzá egy ActiveX gombot
  (Java)
url: /hu/java/using-document-elements/create-a-blank-word-document-and-add-an-activex-button-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Üres Word dokumentum létrehozása és ActiveX gomb hozzáadása (Java)

Ha **programozottan szeretne üres Word dokumentumot** létrehozni, ez az útmutató megmutatja, hogyan teheti meg Java és az Aspose.Words segítségével. Emellett megtanulja, hogyan **adjunk hozzá egy ActiveX gombot**, **állítsuk be a gomb feliratát**, és **állítsuk be a gomb méreteit**, hogy a vezérlő pontosan úgy nézzen ki, ahogy elvárja.

Ez a bemutató a következőket tárgyalja:

* Üres Word fájl inicializálása az Aspose.Words for Java segítségével.  
* ActiveX `CommandButton` vezérlő beszúrása.  
* A gomb feliratának és méretének konfigurálása.  
* A végleges `.docx` fájl mentése.

Alapvető Java ismeretekkel és az Aspose.Words for Java könyvtár egy friss verziójával (a kód a 23.9-es és újabb verziókkal működik) kell rendelkeznie. További függőségek nem szükségesek.

![Üres Word dokumentum ActiveX gombbal](/images/activex-button-example.png){: .align-center alt="Üres Word dokumentum ActiveX gombbal"}

## Üres Word dokumentum létrehozása Aspose.Words segítségével

Az első lépés egy üres `Document` objektum példányosítása. Ez az objektum a teljes Word fájlt reprezentálja a memóriában, és a `DocumentBuilder` osztályt biztosítja a szerkesztéshez.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(doc);
        
        // The rest of the steps follow here...
```

**Miért fontos ez:**  
Üres dokumentum létrehozása tiszta vásznat biztosít, elkerülve a rejtett stílusokat vagy szekciókat, amelyek későbbi elrendezés-számításokba beavatkozhatnak.

## ActiveX gomb hozzáadása a dokumentumhoz

Az Aspose.Words lehetővé teszi örökölt ActiveX vezérlők beágyazását a `Forms2OleControl` osztályon keresztül. Az alábbi kód egy `CommandButton` vezérlőt szúr be az aktuális kurzorpozícióba.

```java
        // Step 2: Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Define the exact ActiveX class name (CommandButton)
        commandButton.setOleClassName("Forms.CommandButton.1");
```

**Tipp:** A `setOleClassName` értéke `"Forms.CommandButton.1"` a szabványos Microsoft Forms gomb ProgID-je. Egy másik ProgID (pl. `"Forms.CheckBox.1"`) más típusú vezérlőt helyezne be.

## Gomb feliratának beállítása

A felirat a gomb felületén megjelenő szöveg. Bármikor megváltoztatható a dokumentum mentése előtt.

```java
        // Step 3: Set the button's caption
        commandButton.setCaption("Click Me");
```

**Miért van erre szükség:**  
A felhasználók csak akkor értik meg a vezérlőt, ha célja egyértelmű. Egy jelentős felirat beállítása javítja a használhatóságot, különösen, ha a dokumentumot Windows rendszeren a Wordben nyitják meg.

## Gomb méreteinek beállítása

A pozíciót és a méretet pontban (1 pont = 1/72 hüvelyk) adjuk meg. Igazítsa az értékeket a kívánt elrendezéshez.

```java
        // Step 4: Define button size and location
        commandButton.setLeft(100);    // distance from the left edge of the page
        commandButton.setTop(200);     // distance from the top edge of the page
        commandButton.setWidth(120);   // width of the button
        commandButton.setHeight(30);   // height of the button
```

**Gyakori variációk:**

| Forgatókönyv | Módosítás |
|--------------|-----------|
| Nagyobb gomb érintőképernyőkhöz | Növelje a `setWidth` és `setHeight` értékeket arányosan |
| Középre helyezett gomb az oldalon | Számolja ki a `left = (pageWidth - width) / 2` |
| Több gomb egy oszlopban | Növelje a `setTop` értéket minden új gombnál |

## A dokumentum mentése, amely tartalmazza az ActiveX gombot

Végül írja a dokumentumot a lemezre. A `.docx` formátum megőrzi az ActiveX vezérlőt a Microsoft Word Windows verziói számára.

```java
        // Step 5: Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

**Várható eredmény:**  
A `ActiveXCommandButton.docx` megnyitása Wordben (Windows) egy üres oldalt mutat, amelyen egy kattintható **Click Me** feliratú gomb található, 100 pt-re a bal margótól és 200 pt-re a felső margótól.

## Teljes, futtatható példa

Másolja az alábbi teljes osztályt a fejlesztőkörnyezetébe, adja hozzá az Aspose.Words for Java JAR‑t a projekt osztályútvonalához, és futtassa.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setOleClassName("Forms.CommandButton.1");

        // Set button caption
        commandButton.setCaption("Click Me");

        // Set button dimensions and position
        commandButton.setLeft(100);    // points from left edge
        commandButton.setTop(200);     // points from top edge
        commandButton.setWidth(120);   // width in points
        commandButton.setHeight(30);   // height in points

        // Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

A program futtatása `ActiveXCommandButton.docx` fájlt hoz létre a munkakönyvtárban. Nyissa meg a Microsoft Word (Windows) programmal, hogy ellenőrizze, a gomb pontosan úgy jelenik meg, ahogy beállította.

## Miért ajánlott ez a megközelítés

* **Egyszerűség:** Csak a core Aspose.Words API‑t használja; nincs szükség COM interopra vagy további könyvtárakra.  
* **Hordozhatóság:** A kód bármely Java‑t támogató platformon fut, bár maga az ActiveX vezérlő csak a Word Windows verzióiban működik.  
* **Karbantarthatóság:** Minden tulajdonság (felirat, méretek, pozíció) egyértelmű, önmagát dokumentáló metódusokkal van beállítva, így a jövőbeli módosítások egyszerűek.

## Gyakori buktatók és hogyan kerüljük el őket

| Buktató | Megoldás |
|---------|----------|
| A gomb nem jelenik meg a Wordben macOS vagy Linux rendszeren | Az ActiveX vezérlők csak Windows‑ra korlátozódnak. Használjon másik vezérlőt (pl. tartalomvezérlő) a platformközi dokumentumokhoz. |
| A felirat levágott | Győződjön meg róla, hogy a gomb szélessége elég a szöveghez; növelje a `setWidth` értéket vagy használjon rövidebb feliratot. |
| A gomb átfed más tartalmat | Állítsa be a `setTop` és `setLeft` értékeket, vagy szúrjon be egy új bekezdést a vezérlő előtt, hogy saját helyet kapjon. |

## Következő lépések

Most, hogy **üres Word dokumentumot tud létrehozni**, **ActiveX gombot hozzáadni**, **a gomb feliratát beállítani**, és **a gomb méreteit meghatározni**, érdemes továbbfejleszteni:

* VBA makrók segítségével eseménykezelő kód hozzáadása (makrómodul beágyazását igényli).  
* Több vezérlő beszúrása táblázatos elrendezésben űrlapszerű dokumentumokhoz.  
* Az Aspose.Words **FormField** API‑jainak használata platformközi űrlapmegoldásokhoz.

Kísérletezzen különböző méretekkel, pozíciókkal és feliratokkal, hogy a dokumentumtervnek megfelelően alakítsa ki. Boldog kódolást!

## Mi legyen a következő tanulnivaló?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API‑funkciókat és alternatív megvalósítási megközelítéseket saját projektjeiben.

- [Word dokumentum létrehozása Java – Téglalap alakzat hozzáadása árnyékhatással](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Űrlapmezők létrehozása és tartalom hozzáadása DocumentBuilder használatával az Aspose.Words for Java-ban](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Vízjel hozzáadása dokumentumhoz az Aspose.Words for Java használatával](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}