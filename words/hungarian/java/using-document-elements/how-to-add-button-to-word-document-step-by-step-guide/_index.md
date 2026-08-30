---
category: general
date: 2026-07-20
description: Hogyan adhatunk gombot Word dokumentumhoz az Aspose.Words használatával.
  Tanulja meg percek alatt, hogyan szúrjon be egy Forms2OleControl gombot a DocumentBuilderrel.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add button to word document
- Forms2OleControl
- DocumentBuilder
- insertForms2OleControl
- Word automation
language: hu
lastmod: 2026-07-20
og_description: Hogyan adjon hozzá gombot a Word dokumentumhoz az Aspose.Words segítségével.
  Kövesse ezt a gyakorlati útmutatót, hogy Java-val beágyazzon egy Forms2OleControl
  CommandButton-ot.
og_image_alt: Screenshot of a Word document with a clickable button added via Aspose.Words
  (how to add button to word document)
og_title: Hogyan adjunk gombot a Word dokumentumhoz – Teljes Aspose.Words útmutató
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  headline: How to Add Button to Word Document – Step‑by‑Step Guide
  type: TechArticle
- description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  name: How to Add Button to Word Document – Step‑by‑Step Guide
  steps:
  - name: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
    text: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
  - name: '`100` – width in points (≈1.39 inches).'
    text: '`100` – width in points (≈1.39 inches).'
  - name: '`30` – height in points (≈0.42 inches).'
    text: '`30` – height in points (≈0.42 inches).'
  type: HowTo
tags:
- Aspose.Words
- Java
- Office Automation
title: Hogyan adjunk gombot a Word dokumentumhoz – Lépésről lépésre útmutató
url: /hu/java/using-document-elements/how-to-add-button-to-word-document-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan adjunk gombot Word dokumentumhoz – Teljes Aspose.Words bemutató

Gondolkodtál már azon, **hogyan adjunk gombot Word dokumentumhoz** anélkül, hogy megnyitnád a felhasználói felületet és kattintgatnál? Nem vagy egyedül. Számos fejlesztőnek kell programozottan beágyazni interaktív vezérlőket – gondolj egy „Submit” gombra egy sablonban, amelyet később egy végfelhasználó tölt ki. A jó hír? Az Aspose.Words for Java-val ezt néhány sorban megteheted.

Ebben a bemutatóban lépésről lépésre bemutatjuk, hogyan szúrjunk be egy `Forms2OleControl` típusú **CommandButton**-t a `DocumentBuilder` segítségével. A végére egy használatra kész `.docx` fájlt kapsz, amely egy „Click Me” feliratú kattintható gombot mutat. Nincs rejtély, csak tiszta kód és a sorok mögötti magyarázat.

## Amit megtanulsz

- Hogyan hozzunk létre egy új Word dokumentumot a semmiből.
- Hogyan használjuk a **DocumentBuilder**-t egy **Forms2OleControl** elhelyezéséhez.
- Miért kell beállítani a gomb feliratát és méretét úgy, ahogy mi tesszük.
- Hogyan mentsük el és ellenőrizzük az eredményt.
- Gyakori buktatók (pl. hiányzó könyvtárak, nem támogatott vezérlőtípusok) és hogyan kerüljük el őket.

**Prerequisites** – Szükséged van Java 8+ (vagy újabb) és az Aspose.Words for Java könyvtárra (23.12 vagy újabb verzió). Egy IDE, mint az IntelliJ IDEA vagy az Eclipse megkönnyíti a dolgokat, de bármilyen szövegszerkesztő is működik.

---

## 1. lépés: Projekt beállítása és függőségek importálása

Mielőtt bármilyen kód futna, a Mavennek (vagy Gradlenek) tudnia kell, honnan töltse le az Aspose.Words-ot. Add hozzá ezt a kódrészletet a `pom.xml`-hez:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

Ha a Gradlet részesíted előnyben, az ekvivalens a következő:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Pro tip:** Használd a legújabb kiadást; a régebbi verziók esetleg hiányozhatnak a `Forms2OleControl` API-tól.

Miután a függőség feloldódik, készen állsz Java kód írására.

## 2. lépés: Új dokumentum létrehozása és DocumentBuilder beszerzése

A `Document` osztály képviseli a teljes `.docx` csomagot, míg a `DocumentBuilder` az a „ecset”, amellyel tartalmat festhetsz rá. Tekintsd a `DocumentBuilder`-t a „kurzorra”, amely tudja, hová kerüljön a következő elem.

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder tied to the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Miért fontos:** Egy új `Document` inicializálása tiszta vásznat ad. A builder automatikusan az első bekezdésre mutat, így nem kell manuálisan kezelned a szekciókat vagy oldalakat.

## 3. lépés: Forms2OleControl beszúrása CommandButton típusban

Most jön a főszereplő: `insertForms2OleControl`. Ez a metódus egy OLE (Object Linking and Embedding) vezérlőt hoz létre, amelyet a Word űrlapelemként kezel. Három argumentumot adunk át:

1. `Forms2OleControlType.COMMANDBUTTON` – azt mondja a Wordnek, hogy egy gombot szeretnénk.
2. `100` – szélesség pontban (≈1,39 hüvelyk).
3. `30` – magasság pontban (≈0,42 hüvelyk).

```java
        // Step 3: Insert a CommandButton with specific dimensions
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

**Hogyan működik:** A háttérben az Aspose.Words a megfelelő XML-t hozza létre a `word/document.xml` részben, hivatkozva az OLE objektumra. A megadott méreteket a Word elrendező motorja figyelembe veszi, így a gomb pontosan ott jelenik meg, ahol a builder kurzora áll.

## 4. lépés: A gomb feliratának (szövegének) beállítása

Egy címke nélküli gomb zavaró – képzeld el egy néma liftgombot. A `setCaption` metódus állítja be a látható szöveget:

```java
        // Step 4: Define the button's label
        commandButton.setCaption("Click Me");
```

A feliratot bármire módosíthatod: „Submit”, „Approve”, vagy akár egy lokalizált karakterláncra. A felirat az OLE objektum tulajdonságaiban tárolódik, így a Word natívan jeleníti meg.

## 5. lépés: Dokumentum mentése és az eredmény ellenőrzése

Végül írd a fájlt a lemezre. Válassz egy mappát, amelyhez írási jogosultságod van; különben `IOException`-t kapsz.

```java
        // Step 5: Persist the document
        String outputPath = "output/button-demo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Nyisd meg a `button-demo.docx`-et a Microsoft Wordben. Látnod kell egy **Click Me** feliratú gombot a dokumentum tetején. A Wordben való kattintás az alapértelmezett OLE viselkedést indítja el (általában egy helyőrző üzenetet, hacsak nem kötöd makróhoz).

## Gyakori szélhelyzetek és megoldások

| Situation | Why It Happens | Fix |
|-----------|----------------|-----|
| **Hiányzó `Forms2OleControl` típus** | A régebbi Aspose.Words verziók nem tartalmazták ezt az enumot. | Frissíts 23.12+ vagy újabb verzióra. |
| **A gomb képként jelenik meg** | A Word biztonsági beállításai blokkolják az OLE vezérlőket. | Engedélyezd a “Trust access to the VBA project object model” opciót a Trust Centerben, vagy használj makró‑engedélyezett `.docm` fájlt. |
| **Helytelen méret** | Pont és pixel közti zavar. | Ne feledd, 1 pont = 1/72 hüvelyk. Ennek megfelelően állítsd a számokat. |
| **Mentés `FileNotFoundException`-t dob** | Az útvonal nem létezik. | Győződj meg róla, hogy a könyvtár (`output/`) létrejön a `doc.save` előtt. Használd a `new File("output").mkdirs();`-t. |

## Példa kibővítése: Több gomb vagy más vezérlők hozzáadása

Ha egynél több gombra van szükséged, egyszerűen mozdítsd a builder kurzorát a `builder.moveTo` vagy `builder.writeln()` segítségével, mielőtt újra meghívnád az `insertForms2OleControl`-t.

```java
        // Add a second button below the first
        builder.writeln(); // moves to a new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");
```

Beilleszthetsz **CheckBox**, **ComboBox**, vagy **ListBox** elemeket is, ha kicseréled a `Forms2OleControlType.COMMANDBUTTON`-t a megfelelő enum értékre (`CHECKBOX`, `COMBOBOX`, stb.). Ugyanazok a szélesség/magasság paraméterek érvényesek.

## Hogyan illeszkedik ez a nagyobb Word automatizálási munkafolyamatokba

- **Template Generation:** Készíts egy szerződés sablont, amely tartalmaz egy „Approve” gombot a további aláíráshoz.
- **Reporting:** Generálj napi jelentést egy „Refresh Data” gombbal, amely makrót indít.
- **Form Distribution:** Küldj ki egy kérdőívet interaktív, előre kitöltött vezérlőkkel.

Mindezek a forgatókönyvek profitálnak a bemutatott **Word automatizálás** megközelítésből. A vezérlők programozott beágyazásával megszünteted a kézi szerkesztést és csökkented az emberi hibákat.

## Teljes forráskód (másolásra kész)

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a CommandButton (width: 100pt, height: 30pt)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

        // Set the button caption
        commandButton.setCaption("Click Me");

        // Optionally add a second button
        builder.writeln(); // new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");

        // Save the document
        String outputPath = "output/button-demo.docx";
        new java.io.File("output").mkdirs(); // ensure directory exists
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

**Várt kimenet:** Amikor megnyitod a `output/button-demo.docx`-et a Microsoft Wordben, két gombot látsz – „Click Me” és „Submit” – függőlegesen egymás alatt a fájl tetején.

## Következtetés

Megválaszoltuk, **hogyan adjunk gombot Word dokumentumhoz** az Aspose.Words for Java segítségével, lépésről lépésre. Egy üres `Document`-ből kiindulva a **DocumentBuilder**-t használtuk egy **CommandButton** típusú `Forms2OleControl` beszúrásához, barátságos feliratot állítottunk be, és elmentettük az eredményt. A megközelítés skálázható több vezérlőre, és tisztán integrálható a szélesebb **Word automatizálás** folyamatokba.

Készen állsz a következő kihívásra? Próbáld meg a gombot **CheckBox**-ra cserélni, vagy köss egy makrót, amely reagál, amikor a felhasználó a gombra kattint egy `.docm` fájlban. Ugyanaz a minta érvényes – csak cseréld ki az enumot és állítsd be a feliratot.

Ha bármilyen problémába ütközöl, ellenőrizd a könyvtár verzióját és a kimeneti mappa jogosultságait. Nyugodtan hagyj megjegyzést alább kérdésekkel vagy oszd meg a saját felhasználási esetedet. Boldog kódolást!

## Mit érdemes legközelebb megtanulni?

A következő bemutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Hogyan hozzunk létre űrlapmezőket és adjunk tartalmat a DocumentBuilder segítségével az Aspose.Words for Java-ban](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Inline kép beszúrása Word dokumentumba az Aspose.Words használatával](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Csoport alakzat létrehozása Word dokumentumban az Aspose.Words for .NET segítségével](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}