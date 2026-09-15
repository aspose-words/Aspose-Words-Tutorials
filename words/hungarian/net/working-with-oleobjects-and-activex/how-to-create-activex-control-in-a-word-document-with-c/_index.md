---
category: general
date: 2026-09-14
description: Hozzon létre ActiveX‑vezérlőt egy Word‑dokumentumban C#‑val. Tanulja
  meg, hogyan illessze be az ActiveX‑ot, adjon hozzá interaktív gombot, és generálja
  programozottan a .docx fájlt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- how to insert activex
- add interactive button
- create word document
- create button with code
language: hu
lastmod: 2026-09-14
og_description: Hozzon létre ActiveX‑vezérlőt egy Word-dokumentumban C#‑val. Kövesse
  ezt a teljes példát az ActiveX beszúrásához, interaktív gomb hozzáadásához és a
  fájl mentéséhez.
og_image_alt: Screenshot of a Word document containing a newly created ActiveX CommandButton
og_title: ActiveX-vezérlő létrehozása Wordben C#-val – lépésről lépésre útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Create ActiveX control in a Word document with C#. Learn how to insert
    ActiveX, add interactive button, and generate the .docx file programmatically.
  headline: How to create ActiveX control in a Word document with C#
  type: TechArticle
tags:
- ActiveX
- C#
- Word automation
title: Hogyan hozhatunk létre ActiveX vezérlőt egy Word-dokumentumban C#‑val
url: /hu/net/working-with-oleobjects-and-activex/how-to-create-activex-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre ActiveX vezérlőt egy Word dokumentumban C#-vel

Ha **ActiveX vezérlőt** kell létrehoznia egy Microsoft Word fájlban, ez az útmutató egy teljes, azonnal futtatható megoldást mutat be. Megmutatja pontosan, hogyan szúrjon be egy ActiveX CommandButton elemet, állítsa be a tulajdonságait, és mentse el a kapott `.docx` fájlt kizárólag C# kóddal.

Interaktív gomb hozzáadása egy Word dokumentumhoz gyakori követelmény, ha a végfelhasználók a dokumentum felhasználói felületéről szeretnének makrókat vagy egyedi logikát indítani. Az alábbi példa bemutatja, **hogyan szúrjunk be ActiveX** elemet harmadik fél eszközei nélkül, és azt is lefedi, **hogyan hozzunk létre Word dokumentumot** programozott módon.

A tutorial végére képes lesz **gombot létrehozni kóddal**, testreszabni a feliratát, és egy hordozható Word fájlt előállítani, amely megőrzi az ActiveX vezérlőt.

## Előfeltételek

- .NET 6.0 vagy újabb (az Aspose.Words for .NET könyvtár működik .NET Core és .NET Framework alatt)
- Hivatkozás a `Aspose.Words` NuGet csomagra  
  ```bash
  dotnet add package Aspose.Words
  ```
- Alapvető C# és objektum‑orientált programozási ismeretek

## 1. lépés: A projekt beállítása és a névterek importálása

Hozzon létre egy új konzolos projektet (vagy integrálja a kódot bármely meglévő C# alkalmazásba). Importálja a szükséges névtereket, hogy a fordító megtalálja a Word‑feldolgozó osztályokat.

```csharp
using System;
using System.Drawing;               // Provides RectangleF
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
```

> **Miért fontos ez a lépés** – Az `Aspose.Words` API biztosítja a `Document`, `DocumentBuilder` és `Forms2OleControl` osztályokat, amelyekkel objektumszinten manipulálhatja a Word fájlokat. Ezek a hivatkozások nélkül a többi kód nem fordulna le.

## 2. lépés: Új Word dokumentum és DocumentBuilder létrehozása

A `Document` objektum a teljes `.docx` csomagot képviseli, míg a `DocumentBuilder` egy folyékony API-t biztosít a tartalom beszúrásához.

```csharp
// Step 2: Initialize a fresh Word document
Document document = new Document();

// Attach a builder to the document – the builder knows where to write next
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Magyarázat** – Egy új `Document` példányosítása tiszta vásznat ad. A builder kurzora az első szakasz elején kezd, készen áll a következő beszúrásra.

## 3. lépés: Az ActiveX CommandButton beszúrása

Használja az `InsertForms2OleControl` metódust egy ActiveX vezérlő adott helyre való elhelyezéséhez. A metódus megköveteli a vezérlő típusát, valamint egy `RectangleF` objektumot, amely meghatározza az X/Y koordinátákat és a méretet (pontban).

```csharp
// Step 3: Add an ActiveX CommandButton at (100,100) with width 120 and height 30
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Miért működik** – Az `OleControlType.CommandButton` azt mondja az API-nak, hogy hozzon létre egy szabványos Windows CommandButton elemet. A téglalap a gombot az oldal bal‑felső sarkához viszonyítva helyezi el, lehetővé téve, hogy **interaktív gombot adj hozzá** pontosan oda, ahol szükség van rá.

## 4. lépés: A gomb tulajdonságainak beállítása

Most állítsa be a gomb látható szövegét (`Caption`) és a belső nevét (`Name`). Ezek a tulajdonságok azok, amelyeket a felhasználók látnak, és amelyeket a VBA kód később hivatkozhat.

```csharp
// Step 4: Define the button’s caption and programmatic name
commandButton.Caption = "Click Me";
commandButton.Name = "btnClick";
```

> **Gyakorlati tipp** – A `Name`-nek egyedinek kell lennie a dokumentumban; különben a VBA makrók a rossz vezérlőre hivatkozhatnak.

## 5. lépés: A dokumentum mentése

Végül írja a fájlt a lemezre. Az ActiveX vezérlő a Word csomagban tárolódik, így a mentett fájl teljes funkcionalitását megőrzi, amikor Microsoft Wordben megnyitják.

```csharp
// Step 5: Persist the document – the ActiveX control stays embedded
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Eredmény** – A `CommandButton.docx` megnyitása Wordben egy kattintható CommandButton-t mutat, amelynek felirata „Click Me”. A vezérlő a Word felhasználói felületén keresztül („Developer → Design Mode → Properties”) makróhoz kapcsolható.

## Teljes forráskód listázása

Az összes lépés egyesítése egyetlen, önálló programot eredményez, amelyet másolhat, beilleszthet és futtathat.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an ActiveX CommandButton at the desired location
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new RectangleF(100, 100, 120, 30));

        // Set the button's caption and internal name
        commandButton.Caption = "Click Me";
        commandButton.Name = "btnClick";

        // Save the document – the control is preserved
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Várható kimenet

A program futtatása egy megerősítő sort ír ki:

```
Document saved to C:\Temp\CommandButton.docx
```

Amikor megnyitja a generált fájlt Microsoft Wordben, egy **CommandButton**-t fog látni a megadott koordinátákon. A gomb kattintása tervező módban kiemeli, futási módban pedig úgy viselkedik, mint bármely szabványos ActiveX gomb.

## Gyakori variációk és szélsőséges esetek

| Forgatókönyv | Módosítás |
|--------------|-----------|
| **Eltérő vezérlő típus** | Cserélje a `OleControlType.CommandButton`-t `OleControlType.CheckBox`, `OleControlType.OptionButton` stb. értékekre. |
| **Több gomb** | Hívja meg többször az `InsertForms2OleControl`-t, és frissítse a `RectangleF` koordinátákat minden új gombhoz. |
| **Dinamikus méretezés** | Számolja ki a téglalap méreteit az oldal mérete alapján (`builder.PageSetup.PageWidth`). |
| **Mentés stream-be** | Használja a `document.Save(stream, SaveFormat.Docx)`-t, ha a fájlt egy web API-ból kell visszaadni. |
| **Word 97‑2003 formátum** | Módosítsa a mentési formátumot `SaveFormat.Doc`-ra, hogy `.doc` fájlt hozzon létre, amely továbbra is beágyazza az ActiveX vezérlőt. |

> **Pro tipp:** Mindig tesztelje a generált dokumentumot a célzott Word verzión, mivel a régebbi verziók alapértelmezés szerint olyan biztonsági beállításokat alkalmazhatnak, amelyek letiltják az ActiveX vezérlőket.

## Gyakran ismételt kérdések

**Működik ez .NET Core‑dal?**  
Igen. Az Aspose.Words könyvtár keresztplatformos és teljes mértékben kompatibilis a .NET Core és a .NET 5/6+ verziókkal.

**Programozottan hozzárendelhetek makrót a gombhoz?**  
Az API nem ágyazza be közvetlenül a VBA kódot. A dokumentum generálása után nyissa meg Wordben, engedélyezze a Developer fület, és rögzítsen vagy írjon egy makrót, amely a `btnClick`-re hivatkozik.

**Mi van, ha a gomb nem jelenik meg?**  
Ellenőrizze, hogy a `Developer` fül engedélyezve van-e Wordben, és hogy a dokumentum nem **Protected View** módban nyílt-e meg. Továbbá győződjön meg arról, hogy a téglalap koordinátái az oldal margóin belül vannak.

## Összegzés

Most már tudja, hogyan **hozzon létre ActiveX vezérlőt** egy Word fájlban C# használatával. A tutorial lefedte, **hogyan szúrjunk be ActiveX** elemet, bemutatta a **interaktív gomb hozzáadását**, megmutatta a **Word dokumentum létrehozását** a nulláról, és illusztrálta a **gomb létrehozását kóddal**, amely a mentés után is megmarad.  

Innen tovább felfedezhet további ActiveX típusokat, összekapcsolhatja a gombot VBA makrókkal, vagy beágyazhatja a logikát egy nagyobb dokumentum‑generáló szolgáltatásba. Kísérletezzen különböző méretekkel, pozíciókkal és vezérlő tulajdonságokkal, hogy pontosan a kívánt felhasználói élményt érje el.

---

## Mit érdemes legközelebb megtanulni?

A következő tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeiben.

- [Új Word dokumentum létrehozása](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [VBA projekt létrehozása Word dokumentumban](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Word dokumentum létrehozása és formázása Aspose.Words for .NET-ben](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}