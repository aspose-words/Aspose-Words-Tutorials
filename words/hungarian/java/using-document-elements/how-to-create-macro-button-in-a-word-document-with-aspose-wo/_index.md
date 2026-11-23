---
category: general
date: 2026-11-22
description: Készíts makrógombot egy Word-dokumentumban Java használatával. Tanuld
  meg, hogyan illessz be parancsgombot, állítsd be a gomb szövegét, és kapcsolj makrót
  a gombhoz interaktív dokumentumokhoz.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create macro button
- insert command button
- set button text
- link macro to button
- add interactive button
language: hu
lastmod: 2026-11-22
og_description: Makrógomb létrehozása Word-dokumentumban Java-val. Ez az útmutató
  bemutatja, hogyan szúrj be parancsgombot, állítsd be a gomb szövegét, és köss makrót
  a gombhoz a teljes interaktivitás érdekében.
og_image_alt: Screenshot of a Word document showing a macro button created with Java
  code
og_title: Makrógomb létrehozása Word-dokumentumban Java-val – lépésről lépésre útmutató
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  headline: How to create macro button in a Word document with Aspose.Words for Java
  type: TechArticle
- description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  name: How to create macro button in a Word document with Aspose.Words for Java
  steps:
  - name: Insert command button into the document
    text: '`DocumentBuilder.insertForms2OleControl` creates an OLE control of the
      specified type. The `Forms2OleControlType.COMMAND_BUTTON` constant tells Aspose.Words
      to generate a command button that can host a macro.'
  - name: Set button text (caption)
    text: The caption is the visible label on the button. Use `setCaption` to define
      what the user sees.
  - name: Link macro to button
    text: A macro is identified by its name, for example `MyMacro`. The `setOnClick`
      method stores this name in the button’s `OnClick` event handler.
  - name: Add interactive button to a Word document
    text: After configuring the OLE control, you may want to position it, resize it,
      or add surrounding text. The `DocumentBuilder` continues to operate on the document,
      so you can insert paragraphs before or after the button.
  - name: Expected output
    text: 'Running the program generates `MacroButtonDemo.docm`. Opening the file
      in Microsoft Word shows:'
  type: HowTo
tags:
- Aspose.Words
- Java
- OLE controls
- Automation
title: Hogyan hozzunk létre makrógombot egy Word dokumentumban az Aspose.Words for
  Java segítségével
url: /hu/java/using-document-elements/how-to-create-macro-button-in-a-word-document-with-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre makrógombot egy Word dokumentumban az Aspose.Words for Java segítségével

Ha **makrógombot** kell **létrehoznod** egy Word fájlban, ez az útmutató végigvezet a szükséges lépéseken. Megtanulod, hogyan **parancsgombot illessz be**, **gomb szövegét állítsd be**, és **makrót a gombhoz kapcsolj**, hogy a dokumentum teljesen interaktív legyen.

A fejlesztők gyakran ágyaznak be OLE vezérlőket, hogy VBA makrókat indítsanak a dokumentumból. Ez az útmutató lefedi a teljes munkafolyamatot, a projekt beállításától egy futtatható Java példáig, amely **interaktív gombot** ad hozzá egy .docx fájlhoz. Nem szükséges külső szkript – minden a Java folyamaton belül fut.

## Előfeltételek

* JDK 17 vagy újabb telepítve.
* Maven 3.8+ (vagy Gradle) a függőségkezeléshez.
* Aspose.Words for Java 23.9 vagy újabb – a könyvtár biztosítja a `DocumentBuilder` és OLE vezérlő API-kat.
* Alapvető ismeretek a Java és VBA makrókról.

Ha bármelyik elem hiányzik, először telepítsd őket; a további útmutató feltételezi, hogy elérhetők.

## Hogyan hozzunk létre makrógombot az Aspose.Words for Java segítségével

A megoldás alapja négy lépésből áll:

1. **Parancsgomb beillesztése** OLE vezérlőként a dokumentumba.
2. **Gomb szövegének beállítása** (címke), amit a felhasználó lát.
3. **Makró összekapcsolása a gombbal**, hogy a kattintás elindítsa a kívánt VBA rutint.
4. **A dokumentum mentése** a beágyazott makróval.

Minden lépést a következő szakaszokban részletezünk.

### 1. lépés: Parancsgomb beillesztése a dokumentumba

`DocumentBuilder.insertForms2OleControl` létrehoz egy megadott típusú OLE vezérlőt. A `Forms2OleControlType.COMMAND_BUTTON` konstans azt mondja az Aspose.Words-nek, hogy generáljon egy parancsgombot, amely makrót tud tartalmazni.

```java
import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load a blank document or create a new one
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Miért fontos:** Az OLE vezérlő a makró tárolójaként működik. Ha nem illeszted be, nem lesz vizuális elem, amire a felhasználó kattinthat.

### 2. lépés: Gomb szövegének (címke) beállítása

A címke a gomb látható felirata. Használd a `setCaption` metódust a felhasználó által látott szöveg meghatározásához.

```java
        // Set the button's caption – this is the text displayed on the button
        commandButton.setCaption("Run Report");
```

**Miért fontos:** A világos gombszöveg javítja a használhatóságot. A `setCaption` metódus frissíti az OLE vezérlő `Caption` tulajdonságát, amelyet a Word gombcímkének jelenít meg.

### 3. lépés: Makró összekapcsolása a gombbal

A makró nevét használja az azonosításhoz, például `MyMacro`. A `setOnClick` metódus ezt a nevet tárolja a gomb `OnClick` eseménykezelőjében.

```java
        // Assign a macro to run when the button is clicked
        commandButton.setOnClick("MyMacro");
```

**Miért fontos:** A makró összekapcsolása interaktív viselkedést hoz létre. Amikor a felhasználó a Wordben a gombra kattint, a hozzákapcsolt VBA rutin lefut.

### 4. lépés: Interaktív gomb hozzáadása egy Word dokumentumhoz

Az OLE vezérlő beállítása után elhelyezheted, átméretezheted, vagy körülötte szöveget adhatsz hozzá. A `DocumentBuilder` továbbra is a dokumentummal dolgozik, így beilleszthetsz bekezdéseket a gomb előtt vagy után.

```java
        // Add a descriptive paragraph before the button
        builder.moveToDocumentStart();
        builder.writeln("Click the button below to generate the report:");

        // Move the cursor back to the button location (optional)
        builder.moveTo(commandButton.getNode());

        // Optionally, resize the button (width and height in points)
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // Save the document with the macro-enabled format
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

**Miért fontos:** A `.docm` formátumban mentés megőrzi a makrókódot. Ha `.docx`-ként mented, a makróhivatkozás elveszik.

## Teljes futtatható példa

Az alábbiakban a teljes Java program található, beleértve az importokat, a kivételkezelést és a lépéseket magyarázó megjegyzéseket. Másold a kódot egy Maven projektbe az Aspose.Words függőséggel, és futtasd.

```java
// Maven dependency (add to pom.xml):
// <dependency>
//   <groupId>com.aspose</groupId>
//   <artifactId>aspose-words</artifactId>
//   <version>23.9</version>
// </dependency>

import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new empty document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Write an introductory paragraph
        builder.writeln("Press the button to execute the macro:");

        // 4. Insert the command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 5. Set the visual caption of the button
        commandButton.setCaption("Run Report");

        // 6. Link the button to a VBA macro named MyMacro
        commandButton.setOnClick("MyMacro");

        // 7. Resize the button for better appearance
        commandButton.setWidth(120);   // points
        commandButton.setHeight(30);   // points

        // 8. Save the document as a macro‑enabled file
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

### Várt kimenet

A program futtatása létrehozza a `MacroButtonDemo.docm` fájlt. A fájl megnyitása a Microsoft Wordben a következőket mutatja:

* Egy bekezdés, amely a *„Nyomd meg a gombot a makró futtatásához:”* szöveget tartalmazza.
* Egy **Run Report** feliratú gomb közvetlenül a bekezdés alatt.
* Amikor rákattintasz a gombra, a Word megpróbálja futtatni a `MyMacro` makrót. (A tényleges VBA kódot manuálisan vagy egy másik automatizálási lépésen keresztül kell a dokumentumba hozzáadni.)

Ha a makró nem létezik, a Word biztonsági figyelmeztetést jelenít meg, ami a makró‑engedélyezett dokumentumoknál szokásos.

## Gyakori variációk és szélhelyzetek

| Szituáció | Hogyan módosítsuk a kódot |
|----------|---------------------------|
| **Eltérő gombcímke** | Módosítsd a `setCaption`-nek átadott karakterláncot. |
| **Több gomb** | Hívjuk többször a `insertForms2OleControl`-t, mindegyikhez saját `setCaption` és `setOnClick` beállítással. |
| **Egyéni makrónevek** | Cseréld le a `"MyMacro"`-t bármely érvényes VBA eljárásnévre, például `"ExportToExcel"`. |
| **Gombméret korlátozások** | Állítsd be a `setWidth` és `setHeight` értékeket; a Word a megadott pontokat veszi figyelembe. |
| **Makró beágyazása programozottan** | Használd a `Document.getBuiltInDocumentProperties().add("Macros", …)`-t vagy egy külön VBA injektálási lépést; az Aspose.Words önmagában nem ír VBA kódot. |

**Pro tipp:** Mindig teszteld a generált `.docm` fájlt egy olyan gépen, ahol a makróbiztonság *Enable all macros* (Minden makró engedélyezése) állásra van állítva fejlesztés közben. Éles környezetben írd alá a makrót egy megbízható tanúsítvánnyal a biztonsági figyelmeztetések elkerülése érdekében.

## Hibaelhárítási ellenőrzőlista

* **A gomb nem jelenik meg** – Ellenőrizd, hogy a dokumentum `.docm` formátumban van mentve, és olyan Word verzióban nyitod meg, amely támogatja az OLE vezérlőket.
* **A makró nem fut** – Győződj meg róla, hogy a makró neve pontosan egyezik (beleértve a kis- és nagybetűket), és hogy a makró létezik a dokumentum VBA projektjében.
* **A gombcímke levágott** – Növeld a gomb szélességét a `setWidth` használatával, hogy hosszabb szöveget is elférjen.
* **Váratlan elrendezési eltolódás** – Használd a `builder.moveTo`-t a kurzor pontos pozicionálásához a vezérlő beillesztése előtt.

## Összegzés

Most már tudod, hogyan **hozz létre makrógombot** egy Word dokumentumban Java segítségével, **parancsgombot illessz be**, **állítsd be a gomb szövegét**, és **kapcsold össze a makrót a gombbal** a teljes interaktivitás érdekében. A teljes példa bemutatja az összes szükséges API hívást, elmagyarázza, miért fontos minden lépés, és útmutatást ad a gyakori variációkhoz.

Most pedig érdemes lehet:

* **Interaktív gomb hozzáadása** meglévő sablonokhoz egy új dokumentum helyett.
* **VBA kód programozott injektálása** az Open XML SDK vagy egy másodlagos automatizálási eszköz segítségével.
* **Több OLE vezérlő kombinálása** (jelölőnégyzetek, listamezők) gazdag űrlapok építéséhez.

Kísérletezz különböző címkékkel, makrónevekkel és gombméretekkel, hogy a saját felhasználási esetedhez illeszkedjenek. Boldog kódolást!

## Mit érdemes még megtanulni?

Az alábbi útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Hogyan illessz be parancsgombot egy Word dokumentumba Java használatával](/words/english/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/)
- [Hogyan állítsd be a gomb pozícióját egy Word dokumentumban Java-val](/words/english/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/)
- [Hogyan illessz be ActiveX gombot Word-be – Gombcímke beállítása](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}