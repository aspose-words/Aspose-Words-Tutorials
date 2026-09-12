---
category: general
date: 2026-09-11
description: Tanulja meg, hogyan hozhat létre forms2olecontrol‑t kódból az Aspose.Words
  DocumentBuilder segítségével. Ez a lépésről‑lépésre útmutató lefedi az ActiveX parancsgomb
  beszúrását, a setOleClassName használatát és a méretezést.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create forms2olecontrol in code
- ActiveX command button
- Aspose.Words DocumentBuilder
- setOleClassName method
- Forms2OleControl size
language: hu
lastmod: 2026-09-11
og_description: Hozzon létre forms2olecontrol-t kódból az Aspose.Words segítségével.
  Kövesse ezt az útmutatót az ActiveX parancsgomb beszúrásához, az osztálynevének
  beállításához és a méretének módosításához.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX command
  button inserted via code
og_title: Forms2OleControl létrehozása kódból – teljes Aspose.Words útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  headline: How to create forms2olecontrol in code with Aspose.Words
  type: TechArticle
- description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  name: How to create forms2olecontrol in code with Aspose.Words
  steps:
  - name: Initialise the DocumentBuilder
    text: The `DocumentBuilder` class is the entry point for most document‑generation
      tasks in Aspose.Words. It gives you methods to add text, images, tables, and,
      importantly for this tutorial, OLE controls.
  - name: Insert the Forms2OleControl
    text: The `insertForms2OleControl` method returns a `Forms2OleControl` object.
      This object represents the OLE control placeholder that Word will render as
      an ActiveX button.
  - name: Specify the ActiveX class with setOleClassName
    text: Word needs to know which type of ActiveX control to render. The class name
      for a standard command button is `"Forms.CommandButton.1"`.
  - name: Adjust the Forms2OleControl size
    text: A button that is too small or too large looks unprofessional. You can control
      its dimensions with `setWidth` and `setHeight`.
  - name: Save the document and test
    text: After configuring the control, save the document to a location of your choice.
  - name: When to use Forms2OleControl vs. Content Controls
    text: If you only need simple data entry (e.g., a plain text field), Word’s built‑in
      content controls are lighter weight. Use `Forms2OleControl` when you require
      full ActiveX functionality such as event handling or custom VBA interaction.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Hogyan hozhatunk létre forms2olecontrol-t kódban az Aspose.Words használatával
url: /hu/java/using-document-elements/how-to-create-forms2olecontrol-in-code-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozhatunk létre forms2olecontrol-t kódból az Aspose.Words segítségével

Ha **forms2olecontrol-t kell kódból létrehoznod**, ez az útmutató pontosan megmutatja, hogyan teheted meg az Aspose.Words .NET API használatával. Akár egy olyan sablont automatizálsz, amelyhez ActiveX parancsgomb szükséges, akár egyszerűen csak programozottan szeretnéd gazdagabbá tenni a Word dokumentumot, az alábbi lépések mindent lefednek a vezérlő beszúrásától a megjelenés beállításáig.

Ebben az útmutatóban megtanulod, hogyan használhatod a **Aspose.Words DocumentBuilder**-t egy **ActiveX parancsgomb** beszúrásához, hogyan állíthatod be az osztályát a **setOleClassName metódussal**, és hogyan módosíthatod a **Forms2OleControl méretét**. Külső eszközök nem szükségesek – csak egy .NET fejlesztői környezet és az Aspose.Words könyvtár.

## Előfeltételek

* .NET 6.0 vagy újabb telepítve (a kód .NET Framework 4.7+‑vel is működik)
* Az Aspose.Words for .NET NuGet csomag legújabb verziója
* Alapvető ismeretek C#‑ban és az ActiveX vezérlők Word dokumentumokban való használatáról

Ha bármelyik hiányzik, telepítsd a NuGet csomagot a következővel:

```bash
dotnet add package Aspose.Words
```

## Mit fed le ez az útmutató

* `DocumentBuilder` példány létrehozása
* `Forms2OleControl` beszúrása (az ActiveX parancsgomb alapjául szolgáló objektum)
* A megfelelő osztálynév hozzárendelése a `setOleClassName` segítségével
* A vizuális szélesség és magasság beállítása a **Forms2OleControl méret** tulajdonságokkal
* A dokumentum mentése és az eredmény ellenőrzése

A útmutató végére egy teljesen működő Word fájlt kapsz, amely egy kattintható gombot tartalmaz, amelyet tovább testre szabhatsz vagy VBA makrókhoz köthetsz.

---

## Hogyan hozhatunk létre forms2olecontrol-t kódból – lépésről‑lépésre

### 1. lépés: A DocumentBuilder inicializálása

A `DocumentBuilder` osztály az Aspose.Words legtöbb dokumentum‑generálási feladatának belépési pontja. Metódusokat biztosít szöveg, kép, táblázat hozzáadásához, és, ami ebben az útmutatóban fontos, OLE vezérlőkhöz.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Initialise the builder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Miért fontos:**  
`DocumentBuilder` a dokumentum aktuális kurzorpozícióját tartja nyilván. Ha korán létrehozod, biztosítod, hogy minden későbbi beszúrás – például az **ActiveX parancsgomb** – pontosan a kívánt helyen jelenjen meg.

### 2. lépés: A Forms2OleControl beszúrása

Az `insertForms2OleControl` metódus egy `Forms2OleControl` objektumot ad vissza. Ez az objektum az OLE vezérlő helyőrzőjét képviseli, amelyet a Word ActiveX gombként jelenít meg.

```csharp
// Insert the Forms2OleControl at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

**Miért fontos:**  
E hívás nélkül nem tudod módosítani a vezérlő tulajdonságait. A visszakapott `Forms2OleControl` teljes hozzáférést biztosít a **setOleClassName metódushoz**, méretattribútumokhoz és egyéb OLE‑specifikus beállításokhoz.

### 3. lépés: Az ActiveX osztály megadása a setOleClassName segítségével

A Wordnek tudnia kell, hogy milyen típusú ActiveX vezérlőt jelenítsen meg. Egy szabványos parancsgomb osztályneve a `"Forms.CommandButton.1"`.

```csharp
// Tell Word that this OLE control is a CommandButton
commandButton.SetOleClassName("Forms.CommandButton.1");
```

**Miért fontos:**  
A `setOleClassName` metódus a generikus OLE helyőrző és a konkrét **ActiveX parancsgomb** közötti híd. A helytelen osztálynév üres objektumot vagy futásidejű hibát eredményez a dokumentum megnyitásakor.

### 4. lépés: A Forms2OleControl méretének beállítása

Egy túl kicsi vagy túl nagy gomb amatőr hatást kelt. Méreteit a `setWidth` és `setHeight` segítségével szabályozhatod.

```csharp
// Set the visual dimensions (points) of the button
commandButton.SetWidth(80);   // width in points
commandButton.SetHeight(30);  // height in points
```

**Miért fontos:**  
Ezek a tulajdonságok alkotják a **Forms2OleControl méretet**. Befolyásolják, hogyan jelenik meg a gomb a Word felhasználói felületén, és biztosítják, hogy a csatolt makró elegendő kattintási területet kapjon.

### 5. lépés: A dokumentum mentése és tesztelése

A vezérlő beállítása után mentsd a dokumentumot a kívánt helyre.

```csharp
// Save the document as a .docx file
doc.Save("ActiveXButton.docx");
```

Nyisd meg a `ActiveXButton.docx` fájlt a Microsoft Wordben. Egy „CommandButton1” feliratú gombot kell látnod (az alapértelmezett felirat). A kattintás semmit sem csinál, hacsak nem adsz hozzá VBA makrót, de a vezérlő maga teljesen működőképes.

**Várható kimenet:**  

![Word dokumentum beillesztett ActiveX parancsgombbal](/images/activeX-button.png "Screenshot of a Word document showing a newly created ActiveX command button inserted via code")

*The image alt text contains the primary keyword for accessibility and SEO.*  
*A kép alt szövege tartalmazza az elsődleges kulcsszót a hozzáférhetőség és SEO érdekében.*

---

## Az ActiveX Forms2OleControl osztály megértése

A `Forms2OleControl` osztály a Word által az ActiveX elemekhez használt alacsony szintű OLE infrastruktúrát csomagolja. A `Shape`‑ből örököl, ami azt jelenti, hogy szükség esetén tipikus alakzatformázást (pl. szegélyek, forgatás) is alkalmazhatsz.

- **ActiveX command button** – A leggyakoribb felhasználási eset; a Word fejlesztői eszközeivel makróhoz kötheted.
- **setOleClassName method** – Meghatározza, melyik COM osztályt tölti be a Word; egyéb érvényes értékek például `"Forms.TextBox.1"` és `"Forms.ComboBox.1"`.
- **Forms2OleControl size** – A `SetWidth`/`SetHeight` segítségével szabályozható. Ezek a metódusok pontban (1 pt = 1/72 in) fogadják az értékeket.

### Mikor használjuk a Forms2OleControl‑t a tartalomvezérlőkkel szemben

Ha csak egyszerű adatbevitelre van szükséged (pl. egy egyszerű szövegmező), a Word beépített tartalomvezérlői könnyebb súlyúak. Használd a `Forms2OleControl`‑t, ha teljes ActiveX funkcionalitásra van szükséged, például eseménykezelésre vagy egyedi VBA interakcióra.

---

## További tulajdonságok beállítása (opcionális)

Miközben az alaplépések elegendőek a **forms2olecontrol kódból történő létrehozásához**, gyakran finomhangolni szeretnéd a gomb megjelenését vagy viselkedését.

```csharp
// Change the button caption (requires a VBA macro to read it)
commandButton.SetOleData("Caption", "Submit");

// Disable the button initially
commandButton.SetOleData("Enabled", false);

// Add a tooltip
commandButton.SetOleData("ToolTipText", "Click to submit the form");
```

**Miért fontos:**  
A `SetOleData` lehetővé teszi, hogy tetszőleges tulajdonságértékeket írj közvetlenül az OLE adatfolyamba. Ez a legflexibilisebb mód egy **ActiveX parancsgomb** testreszabására VBA használata nélkül.

---

## Gyakori hibák és hibaelhárítás

| Tünet | Valószínű ok | Megoldás |
|--------|--------------|-----|
| A gomb szürke dobozként jelenik meg | Helytelen osztálynév lett átadva a `setOleClassName`‑nek | Ellenőrizd, hogy a karakterlánc pontosan `"Forms.CommandButton.1"` (kis‑nagybetű érzékeny) |
| A méret nem változik | Szélesség/Magasság a vezérlő beszúrása előtt lett beállítva | Mindig hívd a `SetWidth`/`SetHeight`‑et **az** `InsertForms2OleControl` **után** |
| A dokumentum „OLE object not found” hibát dob megnyitáskor | Hiányzó Aspose.Words licenc (az értékelő verzió korlátozhatja az OLE‑t) | Alkalmazz érvényes licencet, vagy használd a teljes OLE támogatással rendelkező ingyenes próbaverziót |
| A gomb felirata „CommandButton1” marad | `SetOleData` nincs használva vagy a makró nem olvassa a tulajdonságot | Használj VBA makrót a `"Caption"` tulajdonság olvasásához, vagy állítsd be a feliratot a Word felhasználói felületén |

---

## Teljes, futtatható példa

Az alábbiakban egy teljes konzolalkalmazás található, amelyet másolhatsz, beilleszthetsz és futtathatsz. Bemutatja az útmutatóban tárgyalt összes lépést.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace Forms2OleControlDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1. Create a new document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2. Insert the Forms2OleControl (ActiveX placeholder)
            Forms2OleControl commandButton = builder.InsertForms2OleControl();

            // 3. Set the ActiveX class to CommandButton
            commandButton.SetOleClassName("Forms.CommandButton.1");

            // 4. Define the visual size of the button
            commandButton.SetWidth(80);   // 80 points = ~1.11 inches
            commandButton.SetHeight(30);  // 30 points = ~0.42 inches

            // Optional: set a custom caption via OLE data (requires VBA to read)
            commandButton.SetOleData("Caption", "Submit");

            // 5. Save the document
            string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Az egyes szakaszok magyarázata**

- **Using directives** – Betölti az Aspose.Words névteret, amely a `Document`, `DocumentBuilder` és `Forms2OleControl` használatához szükséges.
- **Document creation** – Létrehozza az üres Word fájlt.
- **InsertForms2OleControl** – Az OLE vezérlőt a builder aktuális kurzorpozíciójába helyezi.
- **SetOleClassName** – A Wordnek jelzi, hogy a vezérlő egy **ActiveX parancsgomb**.
- **SetWidth / SetHeight** – A **Forms2OleControl méretet** állítja be professzionális megjelenéshez.
- **SetOleData (optional)** – Bemutatja, hogyan írj extra tulajdonságokat, például feliratot.
- **Save** – Kiírja a végleges `.docx` fájlt a lemezre.

Futtasd a programot (`dotnet run`), majd nyisd meg a `ActiveXButton.docx` fájlt. Egy gombot kell látnod, amelyet később makróhoz köthetsz.

---

## Összegzés

Most már tudod, hogyan **hozz létre forms2olecontrol-t kódból** az Aspose.Words használatával, a `DocumentBuilder` inicializálásától a **ActiveX parancsgomb** `setOleClassName`‑el történő beállításáig, valamint a **Forms2OleControl méret** szabályozásáig. Ez a megközelítés lehetővé teszi összetett Word dokumentumok automatizálását, interaktív UI elemek beágyazását, és a logika teljesen a kódban tartását.

## Mit érdemes következőként tanulni?

Az alábbi útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljesen működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Hogyan hozhatunk létre űrlapmezőket és adhatunk hozzá tartalmat a DocumentBuilder segítségével az Aspose.Words for Java-ban](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Csoport alakzat létrehozása Word dokumentumban az Aspose.Words for .NET használatával](/words/english/net/working-with-shapes/add-group-shape/)
- [Téglalap alakzat létrehozása Wordben az Aspose.Words‑szal – lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}