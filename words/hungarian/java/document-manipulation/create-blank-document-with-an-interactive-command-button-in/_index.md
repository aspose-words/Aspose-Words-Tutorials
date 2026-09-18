---
category: general
date: 2026-09-18
description: Hozzon létre üres dokumentumot Java-ban, és adjon hozzá egy ActiveX gombot.
  Tanulja meg, hogyan szúrjon be parancsgombot, építsen interaktív űrlapot, és mentse
  el a Word dokumentumot.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- create interactive form
- add activex button
- how to insert command button
- create word document
language: hu
lastmod: 2026-09-18
og_description: Hozzon létre üres dokumentumot Java-ban, és ágyazzon be egy ActiveX
  parancsgombot. Kövesse ezt a lépésről‑lépésre útmutatót, hogy interaktív űrlapot
  készítsen, és elmentse a Word-fájlt.
og_image_alt: Screenshot of a Word document showing a clickable ActiveX command button
og_title: Üres dokumentum létrehozása interaktív parancsgombbal a Wordben
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  headline: Create blank document with an interactive command button in Word using
    Java
  type: TechArticle
- description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  name: Create blank document with an interactive command button in Word using Java
  steps:
  - name: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
    text: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
  - name: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
    text: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
  - name: Insert the button as shown in Step 3.
    text: Insert the button as shown in Step 3.
  - name: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
    text: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Üres dokumentum létrehozása interaktív parancsgombbal a Wordben Java‑val
url: /hu/java/document-manipulation/create-blank-document-with-an-interactive-command-button-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Üres dokumentum létrehozása interaktív parancsgombbal a Wordben Java használatával

Ha **üres dokumentumot** kell létrehoznod, amely egy kattintható gombot tartalmaz, ez az útmutató pontosan megmutatja, hogyan teheted meg az Aspose.Words for Java segítségével. Megtanulod, hogyan építs interaktív űrlapot, hogyan adj hozzá egy ActiveX gombot, és végül hogyan mentsd el a Word fájlt – mindezt néhány tömör lépésben.

Egy parancsgomb beágyazása egy statikus .docx fájlt funkcionális űrlappá alakít, amelyet a végfelhasználók közvetlenül a Microsoft Wordben használhatnak. Ez az oktatóanyag emellett bemutatja, **hogyan szúrj be parancsgombot**, a gyakori buktatók kezelését, és a megoldás kiterjesztését összetettebb űrlapokhoz.

## Előfeltételek

* Java 17 vagy újabb (a kód JDK 17+ verzióval fordítható)
* Aspose.Words for Java 23.9 vagy újabb – a könyvtár biztosítja a `Document`, `DocumentBuilder` és `Forms2OleControl` osztályokat.
* Egy IDE vagy build eszköz (Maven/Gradle), amely hozzá tudja adni az Aspose.Words függőséget.
* Alapvető ismeretek a Java szintaxisról és a Word dokumentum koncepciókról.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## 1. lépés: Üres dokumentum létrehozása

Az első művelet egy új `Document` objektum példányosítása. Ez az objektum egy üres Word fájlt képvisel, amely készen áll a tartalomra.

```java
// Step 1: Create a new blank document
Document doc = new Document();
```

Üres dokumentum létrehozása tiszta vásznat biztosít, ami elengedhetetlen, ha **Word dokumentumot** szeretnél programozottan létrehozni bármilyen előre létező sablon nélkül.

## 2. lépés: DocumentBuilder inicializálása

`DocumentBuilder` az elsődleges osztály szöveg, táblázatok és űrlapvezérlők hozzáadásához. Az általad most létrehozott `Document`-on működik.

```java
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);
```

A builder fenntartja az aktuális beszúrási pontot, így a későbbi parancsok a fájl megfelelő helyére hatnak.

## 3. lépés: Forms2Ole parancsgomb vezérlő beszúrása

Az Aspose.Words a `Forms2OleControl` osztályt biztosítja az ActiveX vezérlőkhöz. **ActiveX gomb hozzáadásához** egy `COMMANDBUTTON` típust kérsz le a builderből.

```java
// Step 3: Insert a Forms2Ole command button control
Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);
```

Az `insertForms2OleControl` metódus a vezérlőt a builder aktuális kurzorpozíciójába szúrja be. Mivel a vezérlő egy ActiveX objektum, csak a Microsoft Word asztali verziójában működik, nem a Word Online-ban.

## 4. lépés: A gomb megjelenésének és pozíciójának beállítása

A gomb feliratát, méretét és helyét a vezérlő setter metódusaival állíthatod be. A pozíció értékeket pontban mérik (1 pont = 1/72 hüvelyk).

```java
// Step 4: Configure the button's appearance and position
commandButton.setCaption("Click Me");   // Text shown on the button
commandButton.setTop(100);              // Distance from the top edge of the page (points)
commandButton.setLeft(100);             // Distance from the left edge of the page (points)
commandButton.setWidth(120);            // Optional: set button width
commandButton.setHeight(30);            // Optional: set button height
```

*Miért kell ezeket a tulajdonságokat beállítani?* A `Top` és `Left` beállítása biztosítja, hogy a gomb a kívánt helyen jelenjen meg az oldalon, míg a `Caption` a felhasználó számára látható feliratot határozza meg. Ha kihagyod a szélességet/magasságot, a Word alapértelmezett méreteket ad, amelyek nem feltétlenül egyeznek a tervezéseddel.

### Profi tipp
Ha több vezérlőt szeretnél hozzáadni, hívd meg a `builder.moveToDocumentEnd()` metódust minden beszúrás előtt, hogy elkerüld az átfedő objektumokat.

## 5. lépés: Dokumentum mentése a beágyazott parancsgombbal

Végül írd a dokumentumot a lemezre. A fájlkiterjesztésnek `.docx`-nek kell lennie (vagy `.doc` a régebbi Word verziókhoz), hogy megőrizze az ActiveX vezérlőt.

```java
// Step 5: Save the document with the embedded command button
String outputPath = "C:/temp/CommandButton.docx";
doc.save(outputPath);
System.out.println("Document saved to: " + outputPath);
```

Amikor megnyitod a `CommandButton.docx` fájlt a Microsoft Wordben, egy **Click Me** feliratú gombot látsz. A gombra kattintás elindítja az alapértelmezett ActiveX műveletet (ami alapértelmezés szerint semmit sem csinál). Később makrót vagy VBA szkriptet csatolhatsz, hogy egyedi viselkedést definiálj.

## Parancsgomb beillesztése meglévő űrlapba (opcionális)

Ha már van egy űrlapod szövegmezőkkel, és **interaktív űrlapot** szeretnél létrehozni, amely tartalmaz egy gombot, kövesd ezeket a további lépéseket:

1. Töltsd be a meglévő dokumentumot: `Document doc = new Document("ExistingForm.docx");`
2. Mozgasd a buildert a kívánt helyre: `builder.moveToParagraph(5, 0); // 6. bekezdés, első csomópont`
3. Szúrd be a gombot a 3. lépésben bemutatott módon.
4. Állítsd be a gomb `Top`/`Left` értékeit a bekezdés elrendezése alapján.

Ez a megközelítés lehetővé teszi, hogy bármely előre elkészített Word sablont ActiveX gombbal gazdagíts anélkül, hogy újra kellene építeni az egész fájlt.

## Szélsőséges esetek és hibaelhárítás

| Situation | What to check | Recommended fix |
|-----------|---------------|-----------------|
| A gomb nem jelenik meg a Wordben | Győződj meg arról, hogy a fájlt a Word asztali verziójában nyitottad meg (a Word Online eltávolítja az ActiveX-et). | Nyisd meg a fájlt a Word 2016+ asztali verziójában. |
| A felirat le van vágva | Ellenőrizd, hogy a gomb szélessége elég nagy-e a szöveg befogadásához. | Növeld a `setWidth` értékét, amíg a felirat elfér. |
| A mentés `IOException`-t dob | Ellenőrizd, hogy a kimeneti könyvtár létezik-e, és van írási jogosultságod. | Hozd létre a könyvtárat, vagy futtasd a programot emelt jogosultságokkal. |
| Több gomb átfedése | Lehet, hogy a builder kurzora nem mozdult el az előző beszúrás után. | Hívd meg a `builder.moveToDocumentEnd()` metódust minden új vezérlő beszúrása előtt. |

## Teljes futtatható példa

Az alábbiakban egy teljes, önálló Java program található, amelyet másolhatsz, lefordíthatsz és futtathatsz. Bemutatja a **üres dokumentum létrehozását**, a **activex gomb hozzáadását**, és a **Word dokumentum mentését** egy folyamatban.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) {
        try {
            // 1. Create a new blank document
            Document doc = new Document();

            // 2. Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Insert an ActiveX command button
            Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);

            // 4. Configure button properties
            commandButton.setCaption("Click Me");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(100);  // points from left
            commandButton.setWidth(120);
            commandButton.setHeight(30);

            // 5. Save the document
            String outPath = "CommandButton.docx";
            doc.save(outPath);
            System.out.println("Document created: " + outPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Expected output**

```
Document created: CommandButton.docx
```

A `CommandButton.docx` megnyitása egy egyoldalas dokumentumot mutat, amelyen egy **Click Me** feliratú gomb található, 100 pt-re a felső és bal szegélytől.

## Következtetés

Most már tudod, hogyan **hozz létre üres dokumentumot**, hogyan ágyazz be egy **ActiveX gombot**, és hogyan alakíts egy egyszerű Word fájlt **interaktív űrlappá**. A **parancsgomb beillesztésének** elsajátításával ezt a mintát kiterjesztheted jelölőnégyzetek, kombinált listák vagy akár egyedi VBA‑alapú logika hozzáadására.

Ezután érdemes megvizsgálni a következő kapcsolódó témákat:

* **Interaktív űrlap létrehozása** szövegmezőkkel (`builder.insertField`)  
* **ActiveX gomb hozzáadása**, amely VBA makrót futtat (`builder.insertOleObject`)  
* **Word dokumentum létrehozása** sablonból a `Document(docTemplatePath)` használatával  
* Az eredményül kapott .docx PDF‑re konvertálása a gomb megőrzése mellett (megjegyzés: a PDF a gombot statikus képként jeleníti meg).

Nyugodtan kísérletezz a gomb méretével, pozíciójával és feliratával, hogy illeszkedjen a UI tervezésedhez. Boldog kódolást!

## Mit érdemes legközelebb megtanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create Vba Project in Word Document](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Create New Word Document](/words/english/net/add-content-using-documentbuilder/create-new-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}