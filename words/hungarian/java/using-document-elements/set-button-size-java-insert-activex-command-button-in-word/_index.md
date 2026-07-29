---
category: general
date: 2026-07-29
description: 'Gombméret beállítása Java oktatóanyag: megtanulja, hogyan szúrjon be
  ActiveX parancsgombot egy Word dokumentumba Java és az Aspose.Words használatával,
  valamint a méretezésről és az üres dokumentum létrehozásáról.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size java
- how to insert activex
- how to set button
- java create blank word
- insert command button word
language: hu
lastmod: 2026-07-29
og_description: A „set button size java” útmutató bemutatja, hogyan lehet Java segítségével
  ActiveX parancsgombot beilleszteni egy Word-fájlba, annak méretét beállítani, és
  a dokumentumot programozottan menteni.
og_image_alt: set button size java example showing a Word document with an ActiveX
  command button
og_title: gomb méretének beállítása Java – ActiveX parancsgomb hozzáadása Word-hez
  Java-val
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  headline: set button size java – Insert ActiveX Command Button in Word
  type: TechArticle
- description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  name: set button size java – Insert ActiveX Command Button in Word
  steps:
  - name: 1. Set Up the Project and Import Aspose.Words
    text: 'First, create a new Maven (or Gradle) project and add the Aspose.Words
      dependency shown above. Then, import the required classes in your Java source
      file:'
  - name: 2. java create blank word Document
    text: Now we actually **java create blank word** document. This is the foundation
      on which we’ll later **insert command button word**.
  - name: 3. Initialize DocumentBuilder and Insert the ActiveX Control
    text: 'The `DocumentBuilder` is a helper that lets us add content, paragraphs,
      tables, and, yes, ActiveX controls. Here’s where we answer **how to insert activex**:'
  - name: 4. How to Set Button Size Java – Adjust Width and Height
    text: 'Now comes the heart of the tutorial: **how to set button size java**. The
      control exposes several layout properties—`Left`, `Top`, `Width`, and `Height`.
      Setting them directly controls the button’s appearance on the page.'
  - name: 5. Save the Document
    text: 'Finally, persist the document to disk:'
  - name: What if the button doesn’t appear in Word?
    text: '- **Check the Word version.** ActiveX controls require the desktop version
      of Word; Word Online strips them out. - **Make sure the Aspose.Words license
      is applied** (if you’re using a paid edition). An unlicensed evaluation version
      may embed a watermark but still shows the control.'
  - name: Can I change the button’s font or color?
    text: Yes. After inserting the control, you can access its underlying OLE object
      and manipulate the VBA properties. That’s a more advanced topic—look into `commandButton.getOleObject().setProperty("ForeColor",
      0xFF0000)` for a red caption, for example.
  - name: How do I handle the button’s click event?
    text: ActiveX command buttons fire a VBA `Click` event. To make the button functional,
      you’ll need to embed a macro in the same document. Aspose.Words can add a macro
      module via the `Document.getMacros()` API, but the macro code itself must be
      written in VBA.
  - name: What about different button types?
    text: 'Aspose.Words supports many `Forms2OleControlType` values: `CHECKBOX`, `OPTIONBUTTON`,
      `LISTBOX`, etc. Swap the enum constant in the `insertForms2OleControl` call
      to experiment.'
  type: HowTo
tags:
- Java
- Aspose.Words
- ActiveX
- Word Automation
title: Gomb méretének beállítása Java – ActiveX parancsgomb beszúrása Wordben
url: /hu/java/using-document-elements/set-button-size-java-insert-activex-command-button-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set button size java – ActiveX parancsgomb beszúrása Wordben

Valaha is elgondolkodtál azon, **how to set button size java**-ról, amikor Word dokumentumokat automatizálsz? Lehet, hogy egy jelentéskészítő eszközt építesz, amelynek egy kattintható „Submit” gombra van szüksége közvetlenül a .docx fájlban. Ebben az útmutatóban végigvezetünk a teljes folyamaton – egy üres Word dokumentum létrehozása, egy ActiveX parancsgomb beszúrása, és a szélességének és magasságának kifejezett beállítása – mindezt Java és Aspose.Words segítségével.

Megválaszoljuk azt a gyakran felmerülő “how to insert activex” kérdést is, amely sok fejlesztőnél felmerül. A végére egy futtatható programod lesz, amely egy olyan Word fájlt hoz létre, amely tökéletes méretű parancsgombot tartalmaz, készen áll a további testreszabásra.

---

## Amire szükséged lesz

- **Java Development Kit (JDK) 8 vagy újabb** – a kód bármely friss JDK-val lefordítható.
- **Aspose.Words for Java** (a legújabb verzió 2026 júliusától). Szerezd be a JAR-t az [Aspose website](https://products.aspose.com/words/java) vagy Maven-en keresztül:
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.10</version>
  </dependency>
  ```
- Egy IDE vagy egyszerű szövegszerkesztő – az IntelliJ IDEA, Eclipse vagy VS Code megfelel.
- Egy mappa, ahol a generált **CommandButton.docx** tárolódni fog.

Ennyi. Nincs szükség extra Office interop könyvtárakra, COM trükkökre, csak tiszta Java.

---

## Lépésről‑lépésre megvalósítás

A megoldást öt logikai lépésre bontjuk. Minden lépésnek saját H2 címe van; az egyik tartalmazza a **primary keyword**-et a SEO érdekében.

### 1. A projekt beállítása és az Aspose.Words importálása

Először hozz létre egy új Maven (vagy Gradle) projektet, és add hozzá a fent bemutatott Aspose.Words függőséget. Ezután importáld a szükséges osztályokat a Java forrásfájlodba:

```java
import com.aspose.words.*;
```

> **Pro tipp:** Ha IDE-t használsz, engedd, hogy automatikusan importálja az osztályokat. Sok gépelést takarít meg, és elkerüli a hibákat.

### 2. java create blank word Document

Most **java create blank word** dokumentumot hozunk létre. Ez lesz az alap, amelyre később **insert command button word**-t fogunk beszúrni.

```java
// Step 2: Create a new blank document
Document document = new Document();          // Starts with a clean, empty .docx
```

A `Document` objektum a teljes Word fájlt reprezentálja a memóriában. Ebben a pontban a fájl még nem tartalmaz oldalakat, szöveget – csak egy tiszta lap.

### 3. DocumentBuilder inicializálása és az ActiveX vezérlő beszúrása

A `DocumentBuilder` egy segédeszköz, amely lehetővé teszi tartalom, bekezdések, táblázatok és igen, ActiveX vezérlők hozzáadását. Itt válaszolunk a **how to insert activex** kérdésre:

```java
// Step 3: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX command button (COMMANDBUTTON is a built‑in type)
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMANDBUTTON);
```

`Forms2OleControl` az Aspose OLE objektum köré épített burkolója. A `COMMANDBUTTON` megadásával azt mondjuk a Wordnek, hogy ágyazzon be egy klasszikus ActiveX parancsgombot.

### 4. How to Set Button Size Java – Szélesség és magasság beállítása

Most jön a tutorial szíve: **how to set button size java**. A vezérlő több elrendezési tulajdonságot is elérhetővé tesz – `Left`, `Top`, `Width` és `Height`. Ezek közvetlen beállítása szabályozza a gomb megjelenését az oldalon.

```java
// Step 4: Set button properties, including size
commandButton.setCaption("Click Me"); // Text shown on the button
commandButton.setLeft(100);           // Distance from the left margin (points)
commandButton.setTop(200);            // Distance from the top margin (points)
commandButton.setWidth(120);          // Width in points (≈1.67 inches)
commandButton.setHeight(30);          // Height in points (≈0.42 inches)
```

Miért ezek a számok? A Wordben egy pont 1/72 hüvelyknek felel meg. Így a `120` pont szélesség körülbelül 1,67 hüvelyknek felel meg – elég nagy egy olvasható címke számára, de nem túl nagy. Állítsd a értékeket a saját elrendezésedhez; ugyanazok a tulajdonságok válaszolnak a **how to set button** kérdésre is.

> **Megjegyzés:** Ha más típusú gombra van szükséged (például jelölőnégyzet), cseréld le a `Forms2OleControlType.COMMANDBUTTON`-t a megfelelő enum értékre.

### 5. Dokumentum mentése

Végül mentsd el a dokumentumot a lemezre:

```java
// Step 5: Save the document with the embedded ActiveX control
document.save("YOUR_DIRECTORY/CommandButton.docx");
```

Cseréld le a `YOUR_DIRECTORY`-t a gépeden lévő abszolút vagy relatív útvonalra. A program futtatása után nyisd meg a generált fájlt a Microsoft Wordben. Egy „Click Me” feliratú gombot látsz, amely 100 pt-re van balról és 200 pt-re felülről, pontosan a megadott mérettel.

---

## Teljes működő példa

Az alábbiakban a teljes, azonnal futtatható Java osztály található. Másold be a `CommandButtonActiveX.java` fájlba, állítsd be a kimeneti útvonalat, és nyomd meg a **Run** gombot.

```java
import com.aspose.words.*;

public class CommandButtonActiveX {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document (java create blank word)
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert an ActiveX command button (how to insert activex)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 4: Set button properties – this is how to set button size java
        commandButton.setCaption("Click Me"); // Button text
        commandButton.setLeft(100);           // Left position (points)
        commandButton.setTop(200);            // Top position (points)
        commandButton.setWidth(120);          // Width (points)
        commandButton.setHeight(30);          // Height (points)

        // Step 5: Save the document (insert command button word)
        document.save("YOUR_DIRECTORY/CommandButton.docx");
    }
}
```

**Várható kimenet:** A `CommandButton.docx` megnyitása a Wordben egyetlen oldalt jelenít meg egy kattintható „Click Me” gombbal, amely nagyjából az oldal közepén helyezkedik el. A gomb méretei megegyeznek a beállított értékekkel, ami megerősíti, hogy a **set button size java** a várt módon működik.

---

## Gyakori kérdések és szélhelyzetek

### Mi van, ha a gomb nem jelenik meg a Wordben?

- **Ellenőrizd a Word verzióját.** Az ActiveX vezérlőkhez a Word asztali verziója szükséges; a Word Online eltávolítja őket.
- **Győződj meg arról, hogy az Aspose.Words licenc alkalmazva van** (ha fizetős kiadást használsz). Egy licenc nélküli értékelő verzió vízjelet ágyazhat be, de még mindig megjeleníti a vezérlőt.

### Megváltoztathatom a gomb betűtípusát vagy színét?

Igen. A vezérlő beszúrása után hozzáférhetsz az alatta lévő OLE objektumhoz, és módosíthatod a VBA tulajdonságokat. Ez egy haladóbb téma – például nézd meg a `commandButton.getOleObject().setProperty("ForeColor", 0xFF0000)` kódot egy piros felirat esetén.

### Hogyan kezelem a gomb **Click** eseményét?

Az ActiveX parancsgombok egy VBA `Click` eseményt váltanak ki. Ahhoz, hogy a gomb működjön, egy makrót kell beágyaznod ugyanabba a dokumentumba. Az Aspose.Words a `Document.getMacros()` API-n keresztül tud makrómodult hozzáadni, de magát a makrókódot VBA-ban kell megírni.

### Mi a helyzet a különböző gombtípusokkal?

Az Aspose.Words számos `Forms2OleControlType` értéket támogat: `CHECKBOX`, `OPTIONBUTTON`, `LISTBOX` stb. Cseréld ki az enum konstansot az `insertForms2OleControl` hívásban a kísérletezéshez.

---

## Pro tippek a production‑kész kódhoz

1. **Használj konstansokat az elrendezési értékekhez** – megkönnyíti a jövőbeli módosításokat.
2. **Tegyük a mentési útvonalat egy `Path` objektumba** a platform‑specifikus elválasztók elkerülése érdekében.
3. **Zárd le a Document objektumot** (vagy használj try‑with‑resources blokkot), ha egy ciklusban sok fájlt dolgozol fel.
4. **Ellenőrizd a kimeneti mappát** a `save` hívása előtt, hogy elkerüld a `FileNotFoundException`-t.

---

## Következtetés

Most megtanultad a **set button size java**-t egy üres Word fájl létrehozásával, egy ActiveX parancsgomb beszúrásával és a méretek pontos beállításával – mindezt néhány Java sorral. Ez lefedi a **how to insert activex**, **how to set button**, **java create blank word**, és **insert command button word** alapjait egyetlen, önálló példában.

Következő lépések? Próbáld meg testreszabni a gomb feliratát, makrót hozzáadni a kattintások kezeléséhez, vagy több vezérlőt beágyazni ugyanarra az oldalra. Emellett felfedezheted a .docx PDF‑re konvertálását az Aspose.Words segítségével, a gombot statikus képként megőrizve.

Nyugodtan kísérletezz, és ha elakadsz, írj egy megjegyzést alább. Boldog kódolást!

## Mit érdemes még megtanulni?

Az alábbi útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Load Word Documents with Aspose.Words Java: Comprehensive Guide](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}