---
category: general
date: 2026-10-26
description: Tudja meg, hogyan hozhat létre Word-dokumentumot C#‑ban, és adhat hozzá
  programozottan ActiveX gombot. Ez a lépésről‑lépésre útmutató bemutatja a parancsgomb
  beszúrását, a tervezési időben való elrejtését és a fájl mentését.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to add activex button
- create command button word
- programmatically add command button
language: hu
lastmod: 2026-10-26
og_description: Hozzon létre Word-dokumentumot C#‑ban, és programozottan adjon hozzá
  egy ActiveX gombot. Kövesse ezt a teljes útmutatót, hogy beágyazzon egy parancsgombot,
  amely csak futásidőben jelenik meg.
og_image_alt: Screenshot of a Word document created with C# that contains an ActiveX
  command button
og_title: Word dokumentum létrehozása C#‑ban ActiveX parancsgombbal – teljes útmutató
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document C# and add an ActiveX button programmatically.
    This step‑by‑step guide covers inserting a command button, hiding it at design
    time, and saving the file.
  headline: How to create Word document C# with an ActiveX command button
  type: TechArticle
tags:
- C#
- Aspose.Words
- ActiveX
- Word automation
title: Hogyan készítsünk Word-dokumentumot C#-ban egy ActiveX parancsgombbal
url: /hu/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre Word dokumentumot C#‑ban egy ActiveX parancsgombbal

Ha **Word dokumentumot C#‑ban** kell létrehoznod, amely interaktív gombot tartalmaz, ez az útmutató pontosan megmutatja, hogyan. Az első két mondat végére már ismerni fogod az általános megközelítést, és a következő lépések végigvezetik a szükséges kódsorokon.

Megtanulod, hogyan adj hozzá egy ActiveX gombot, hogyan rejted el a tervezés során, és hogyan teszed láthatóvá csak akkor, amikor a felhasználó megnyitja a fájlt. Az útmutató kitér a gyakori buktatókra is, mint a biztonsági figyelmeztetések és a verziókompatibilitás, így megbízható dokumentumokat szállíthatsz.

## Prerequisites

Mielőtt elkezdenéd, győződj meg róla, hogy rendelkezel:

* .NET 6.0 vagy újabb telepítve  
* Egy licencelt példánnyal a **Aspose.Words for .NET**‑ből (az ingyenes próbaverzió kísérletezéshez is megfelelő)  
* Alapvető ismeretekkel a C#‑ról és a Visual Studio‑ról (bármely .NET‑et támogató IDE megfelel)  

További NuGet csomagok nem szükségesek a `Aspose.Words`‑en kívül.

## Step 1: Create a Word document C# and initialize the DocumentBuilder

Az első lépés egy `Document` objektum és egy `DocumentBuilder` példányosítása. A `Document` a teljes .docx fájlt képviseli, míg a `DocumentBuilder` folyékony módszereket biztosít a tartalom hozzáadásához.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document document = new Document();

        // Attach a builder to the document so we can insert nodes.
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Why this matters:** `DocumentBuilder` nélkül manuálisan kellene az OpenXML DOM‑ot manipulálnod, ami hibára hajlamos és nehezebben olvasható. A builder elrejti ezeket a részleteket, és garantálja a jól felépített Word fájlt.

## Step 2: How to add ActiveX button – insert a CommandButton control

Most egy **CommandButton ActiveX vezérlőt** szúrunk be egy meghatározott helyen. A téglalap határozza meg a gomb pozícióját (X, Y) és méretét (szélesség, magasság) pontban.

```csharp
        // Define the button's position and size.
        RectangleF buttonRect = new RectangleF(100, 100, 120, 30);

        // Insert the ActiveX CommandButton control.
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,   // Type of ActiveX control
            buttonRect,                          // Geometry
            "ClickMe");                          // Caption shown at design time
```

**Why this matters:** Az `InsertForms2OleControl` az egyetlen Aspose.Words metódus, amely valódi ActiveX OLE objektumot hoz létre. A `Forms2OleControlType.CommandButton` enum érték azt mondja a Wordnek, hogy egy kattintható gombot ágyazzon be, nem pedig egy általános OLE tárolót.

## Step 3: Programmatically add command button – hide it until runtime

A Word alapértelmezés szerint minden beillesztett alakzatot láthatóként kezel. Ahhoz, hogy a gombot láthatatlanul tartsd a sablon tervezése közben, állítsd be a `Hidden` tulajdonságot azon alakzaton, amelyet a builder most hozott létre.

```csharp
        // Retrieve the shape that represents the newly added control.
        Shape oleShape = (Shape)builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)[0];

        // Hide the shape; it will become visible when the document is opened.
        oleShape.Hidden = true;
```

**Why this matters:** A `Hidden = true` beállítás megakadályozza, hogy a gomb elzárja a tervező nézetet. Amikor a dokumentumot Wordben megnyitják, a futásidejű környezet automatikusan megjeleníti a vezérlőt, megőrizve a kívánt felhasználói élményt.

## Step 4: Save the file – create command button word document

Végül írjuk a dokumentumot lemezre. Válassz egy olyan útvonalat, ahová az alkalmazásod írni tud, és használd a `.docx` kiterjesztést a modern kompatibilitás biztosításához.

```csharp
        // Save the document containing the ActiveX button.
        document.Save(@"C:\Temp\ActiveXButton.docx");
    }
}
```

**Why this matters:** `.docx`‑ként mentve garantálja, hogy a beágyazott ActiveX vezérlő megfelel az Office Open XML szabványnak, amelyet a Word 2007 és újabb verziók támogatnak. Ha régi `.doc` támogatásra van szükséged, cseréld le a kiterjesztést, és használd a `SaveFormat.Doc`‑ot.

## Full working example

Mindent összegezve, itt a teljes program, amelyet másolhatsz, beilleszthetsz és futtathatsz:

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Step 1: Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control.
        RectangleF commandButtonRect = new RectangleF(100, 100, 120, 30);
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            commandButtonRect,
            "ClickMe");

        // Step 3: Hide the control so it appears only at runtime.
        Shape oleShape = (Shape)builder.CurrentParagraph
                                         .GetChildNodes(NodeType.Shape, true)[0];
        oleShape.Hidden = true;

        // Step 4: Save the document containing the ActiveX control.
        document.Save(@"C:\Temp\ActiveX.docx");
    }
}
```

**Expected output:** A program futtatása után nyisd meg a `C:\Temp\ActiveX.docx` fájlt a Microsoft Wordben. Egy üres dokumentumot látsz; a gomb nem látható a tervező módban. Nyomd meg az **Alt + F9**‑et a mezőkódok váltásához, majd kattints a gomb területére – a Word megjeleníti az ActiveX vezérlőt, és interakcióba léphetsz vele (pl. duplán kattintva megtekintheted a tulajdonságait).

## Edge cases and best‑practice tips

| Helyzet | Mit kell figyelni | Ajánlott megoldás |
|-----------|-------------------|-----------------|
| **User disables ActiveX** | A Word biztonsági figyelmeztetést jeleníthet meg, vagy blokkolhatja a vezérlőt. | Tájékoztasd a végfelhasználókat, hogy engedélyezzék az “ActiveX controls” opciót a Trust Center‑ben, vagy kínálj makró‑aláírt alternatívát. |
| **Document opened in Word Online** | A Word Online nem támogatja az ActiveX‑et; a gomb elmarad. | Használj tartalék hiperhivatkozást vagy egy tartalomvezérlőt, ha felhőkompatibilitásra van szükség. |
| **Different DPI settings** | A téglalap mérete nagyobbnak vagy kisebbnek tűnhet a magas DPI‑s kijelzőkön. | Használd a `GraphicsUnit.Point`‑ot (az alapértelmezettet) és teszteld a gyakori DPI beállításokon (96 dpi, 120 dpi). |
| **Multiple buttons** | A `GetChildNodes(NodeType.Shape, true)[0]` hívás csak az első alakzatot adja vissza. | Iterálj a `builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)` elemein, és állítsd be a `Hidden` tulajdonságot minden hozzáadott alakzatra. |
| **Legacy .doc format** | Néhány ActiveX tulajdonság elveszik a `.doc` mentésekor. | Előnyben részesítsd a `.docx`‑et, hacsak nincs szigorú régi formátum követelmény. |

**Pro tip:** A gomb beillesztése után hozzárendelhetsz egy makrót a `OnAction` tulajdonságához a Word felhasználói felületén keresztül. Így egyedi kattintási viselkedést definiálhatsz anélkül, hogy további C# kódot írnál.

## Frequently asked questions

* **Does this work with .NET Core?**  
  Igen. Az Aspose.Words for .NET teljes mértékben kompatibilis a .NET 5, .NET 6 és újabb verziókkal. Csak hivatkozz ugyanarra a NuGet csomagra.

* **Can I change the button caption after the document is generated?**  
  Az `InsertForms2OleControl`‑ben beállított felirat lesz az alapértelmezett tervezési szöveg. A felhasználók szerkeszthetik Wordben, de programozottan is frissítheted a feliratot az OLE objektum `Shape.OleFormat` API‑ján keresztül.

* **What if I need a different size for the button?**  
  Módosítsd a `RectangleF` értékeket. Az első két paraméter az X‑ és Y‑koordinátákat, az utolsó kettő pedig a szélességet és magasságot adja pontban (1 pt = 1/72 inch).

## Conclusion

Most már tudod, hogyan **hozz létre Word dokumentumot C#‑ban** és **programozottan adj hozzá parancsgombot** az Aspose.Words segítségével. Az útmutató bemutatta a dokumentum inicializálását, egy ActiveX gomb beszúrását, annak futásidőig tartó elrejtését, valamint a végleges fájl mentését. Ezekkel az építőelemekkel bármely Word sablonba beágyazhatsz interaktív vezérlőket.

Ezután fedezd fel a kapcsolódó témákat, például a **how to add ActiveX button** eseménykezelést, a **create command button word** stílus kialakítását VBA‑val, és a **programmatically add command button** meglévő dokumentumokhoz. A mintát könnyen kiterjesztheted jelölőnégyzetekre, kombinált listákra vagy egyedi OLE objektumokra – csak a `Forms2OleControlType` enum értékét kell módosítanod.

Kezdj el kísérletezni: cseréld le a feliratot, állítsd be a pozíciót, vagy láncolj több vezérlőt egymás után. Minél többet gyakorlod, annál magabiztosabban tudsz gazdag, interaktív Word dokumentumokat generálni C#‑ból. Boldog kódolást!

## What Should You Learn Next?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás komplett működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API‑funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Hogyan adjunk hozzá egy parancsgombot programozottan egy Word dokumentumban](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [Hogyan adjunk hozzá ActiveX gombot egy Word dokumentumban az Aspose.Words segítségével](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Word dokumentum létrehozása ActiveX gombbal – C# útmutató](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}