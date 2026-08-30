---
category: general
date: 2026-07-26
description: Hogyan szúrjunk be ActiveX gombot egy Word dokumentumba az Aspose.Words
  segítségével – tanulja meg beállítani a gomb feliratát, pozícióját és méretét néhány
  sorban.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert activex
- set button caption
language: hu
lastmod: 2026-07-26
og_description: Hogyan illesszünk be ActiveX gombot egy Word dokumentumba az Aspose.Words
  segítségével. Kövesd ezt a lépésről‑lépésre útmutatót a gomb feliratának, pozíciójának
  és méretének beállításához.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX CommandButton
  with a custom caption
og_title: Hogyan illessz be ActiveX gombot a Wordben – Gyors útmutató
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: How to insert ActiveX button in a Word document using Aspose.Words
    – learn to set button caption, position, and size in just a few lines.
  headline: How to Insert ActiveX Button in Word – Set Button Caption
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- Document generation
title: Hogyan illesszünk be ActiveX gombot a Wordben – Állítsuk be a gomb feliratát
url: /hu/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan szúrjunk be ActiveX gombot a Wordben – Gombfelirat beállítása

Gondoltad már, **hogyan szúrjunk be ActiveX** vezérlőket egy Word fájlba anélkül, hogy megnyitnánk a felhasználói felületet? Nem vagy egyedül. Sok vállalati alkalmazásban szükség van egy kattintható gombra, amely makrót futtat, és a programozott megoldás órákat takarít meg. Ez az útmutató pontosan megmutatja, **hogyan szúrjunk be ActiveX** CommandButton-t az Aspose.Words for Java segítségével, és – igen – hogyan **állítsuk be a gombfeliratot**, hogy a felhasználó tudja, mire kell kattintani.

Végigvezetünk a teljes folyamaton: a könyvtár beállításától, egy új dokumentum létrehozásán, a gomb elhelyezésén, a méret és pozíció finomhangolásán, egy barátságos felirat hozzáadásán, egészen a fájl mentéséig. A végére egy futtatható `.docx` fájlt kapsz, amely Wordben megnyílik egy teljesen működőképes ActiveX gombbal, készen állva a makró indítására.

---

## Mit fogsz megtanulni

- Telepítsd és hivatkozd az Aspose.Words-ot egy Java projektben.  
- Hozz létre egy új `Document` és `DocumentBuilder` objektumot.  
- **Insert ActiveX** CommandButton vezérlő egyetlen kódsorral.  
- **Set button caption**, állítsd be a pozícióját, és határozd meg a méreteit.  
- Mentsd a dokumentumot, és nyisd meg Wordben, hogy lásd az eredményt.

Az ActiveX előzetes ismerete nem szükséges; elegendő az alap Java tudás és egy Aspose.Words példány.

## Előfeltételek

- Java 8 vagy újabb telepítve a gépeden.  
- Maven vagy Gradle a függőségkezeléshez (a Maven példát mutatjuk).  
- Licencelt vagy értékelő példány a **Aspose.Words for Java**‑ból (az ingyenes próba megfelelő a bemutatóhoz).  
- Microsoft Word (bármely friss verzió) a generált fájl teszteléséhez.

## 1. lépés: Aspose.Words beállítása a projektben

Először is—add hozzá az Aspose.Words függőséget. Ha Maven-t használsz, helyezd ezt a `pom.xml`-be:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for the latest version -->
</dependency>
```

Gradle felhasználók hozzáadhatják:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

Egy gyors `mvn clean install` (vagy `gradle build`) után a könyvtár a classpath-odban lesz, és készen állsz a kódolásra.

## 2. lépés: Új dokumentum és builder létrehozása

A `Document` a teljes Word fájlt képviseli, míg a `DocumentBuilder` lehetővé teszi annak szerkesztését. Tekintsd a buildert egy tollnak, amely egy friss vászonra rajzol.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();                 // creates an empty .docx
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Miért kezdjünk egy üres dokumentummal? Biztosítja, hogy teljes kontrollod legyen minden hozzáadott elem felett, és nincs rejtett formázás, ami később meglephet.

## 3. lépés: ActiveX CommandButton vezérlő beszúrása

Most jön a főszereplő. Az Aspose.Words biztosítja az `insertForms2OleControl` metódust, amely bármely megadott ActiveX vezérlőt elhelyezhet. Itt egy **CommandButton**-t kérünk.

```java
        // Step 3: Insert a CommandButton ActiveX control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

A metódus egy `Forms2OleControl` objektumot ad vissza, amely programozott hozzáférést biztosít a gomb tulajdonságaihoz. Itt a **how to insert activex** egyetlen soros megoldássá válik – nincs szükség alacsony szintű COM API-kkal való bajlódásra.

## 4. lépés: Pozíció, méret és gombfelirat beállítása

Egy gomb, amely a lap közepén lebeg, nem túl hasznos. Szeretnéd azt a helyen elhelyezni, ahol a felhasználók számítanak rá, megfelelő méretet adni neki, és – ami a legfontosabb – **set button caption**, hogy tudják, mit csinál a kattintás.

```java
        // Step 4a: Position the button (coordinates are in points)
        commandBtn.setLeft(100);   // distance from the left margin
        commandBtn.setTop(150);    // distance from the top margin

        // Step 4b: Define width and height
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Step 4c: Set the button caption (the text that appears on the button)
        commandBtn.setCaption("Click Me");
```

**Miért ezek a számok?** A Word pontokat használ (1 pt ≈ 1/72 hüvelyk). `100 pt` ≈ 1,4 hüvelyk balról, `150 pt` ≈ 2,1 hüvelyk felülről – nagyjából egy standard A4 oldal középpontja. Igazítsd őket a saját elrendezésedhez.

A felirat beállítása kulcsfontosságú; nélküle a gomb egy üres téglalapként jelenik meg. A `setCaption` metódus bármilyen karakterláncot elfogad, így később lokalizálhatod, ha szükséges.

## 5. lépés: Dokumentum mentése

Végül írd a dokumentumot a lemezre. Bármilyen mappát választhatsz, csak győződj meg róla, hogy az útvonal létezik.

```java
        // Step 5: Save the document to a .docx file
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Amikor megnyitod a `ActiveXButton.docx` fájlt Wordben, egy szépen elhelyezett, **„Click Me.”** feliratú gombot látsz. Ha duplán rá kattintasz, a Word felszólít a makrók engedélyezésére (mivel az ActiveX vezérlőket makró‑engedélyezettnek tekintik). Innen már egy VBA rutinhoz kötheted a gomb `Click` eseményét.

## Szélhelyzetek és tippek, amiket esetleg kihagysz

- **Makró‑engedélyezett formátum**: A Word letiltja az ActiveX vezérlőket egyszerű `.docx` fájlokban, hacsak a felhasználó nem engedélyezi a makrókat. Ha azt szeretnéd, hogy a gomb azonnal működjön, fontold meg a mentést `.docm` (makró‑engedélyezett) formátumban a `doc.save(outputPath, SaveFormat.DOCM);` használatával.  
- **Kompatibilitás**: A régebbi Word verziók (2007 előtti) a bináris `.doc` formátumot használják. Az Aspose.Words képes ebbe a formátumba menteni, de a vezérlő tulajdonságai kissé eltérően jelenhetnek meg.  
- **Biztonsági beállítások**: Egyes vállalati környezetek letiltják az ActiveX-et. Ha a gomb nem jelenik meg, ellenőrizd a Word Trust Center → ActiveX Settings beállításait.  
- **Több gomb**: Több gombra van szükséged? Csak ismételd meg az `insertForms2OleControl` hívást, és állítsd be minden gomb `Left`/`Top` értékét. Kövesd nyomon a visszakapott objektumokat, hogy egyedi feliratokat állíthass be.  
- **A felirat stílusozása**: A felirat az alapértelmezett betűtípust örökli. A módosításhoz a mögöttes XML-t kell szerkeszteni, vagy a beszúrás után Word stílust alkalmazni – ez túlmutat a gyors útmutató keretein, de megvalósítható az Aspose.Words `ParagraphFormat` API-jával.

## Teljes működő példa

Az alábbiakban a teljes, futtatható Java osztály látható. Másold be a fejlesztői környezetedbe, állítsd be a kimeneti útvonalat, és nyomd meg a **Run** gombot.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Position the button (points from the left/top margins)
        commandBtn.setLeft(100);
        commandBtn.setTop(150);

        // Set size (width × height in points)
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Set the button caption – this is the visible text
        commandBtn.setCaption("Click Me");

        // Save the document; you may also use SaveFormat.DOCM for macro‑enabled files
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

**Várható kimenet**: A futtatás után a konzol kiírja a mentési helyet. A generált fájl Wordben való megnyitása egy körülbelül a lap közepén elhelyezett, „Click Me” feliratú gombot mutat. A kattintás elindítja a standard ActiveX click eseményt (ehhez VBA makrót kell csatolnod a válaszadáshoz).

## Következtetés

Most már tudod, **hogyan szúrjunk be ActiveX** CommandButton vezérlőket egy Word dokumentumba programozott módon az Aspose.Words segítségével, és pontosan láttad, hogyan **állítsuk be a gombfeliratot**, a pozíciót és a méretet. Ez a megközelítés megszünteti a manuális UI munkát, tisztán integrálódik az automatizált jelentésgenerátorokba, és teljes kontrollt ad a

## Mit érdemes következőként megtanulni?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Alakzatok beszúrása Word dokumentumokba az Aspose.Words for .NET használatával](/words/english/net/working-with-shapes/insert-shape/)
- [Beágyazott kép beszúrása Word dokumentumba az Aspose.Words segítségével](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Kép beszúrása Word dokumentum fejlécébe | Aspose.Words for .NET](/words/english/net/header-footer-formatting/insert-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}