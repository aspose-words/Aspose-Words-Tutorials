---
category: general
date: 2026-08-07
description: A lábjegyzet-elválasztó lekérése az Aspose.Words for .NET segítségével.
  Tanulja meg, hogyan lehet kinyerni a lábjegyzet- és végjegyzet-elválasztókat, ellenőrizni
  a csomóponttípusokat, és módosítani őket C#‑ban.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve footnote separator
- Aspose.Words footnote separator
- C# footnote extraction
- endnote separator retrieval
- document node type
language: hu
lastmod: 2026-08-07
og_description: Lábjegyzet elválasztó lekérése az Aspose.Words for .NET segítségével.
  Ez az útmutató bemutatja, hogyan lehet kinyerni a lábjegyzet- és végjegyzet-elválasztókat,
  ellenőrizni azok csomóponttípusait, és menteni a módosításokat.
og_image_alt: Console output demonstrating retrieve footnote separator results
og_title: Lábjegyzet elválasztó lekérése C#‑ban – lépésről lépésre Aspose.Words útmutató
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: retrieve footnote separator using Aspose.Words for .NET. Learn how
    to extract footnote and endnote separators, inspect node types, and modify them
    in C#.
  headline: retrieve footnote separator in C# – complete Aspose.Words guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
title: Lábjegyzet-elválasztó lekérése C#-ban – teljes Aspose.Words útmutató
url: /hu/net/working-with-footnote-and-endnote/retrieve-footnote-separator-in-c-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# lábjegyzet elválasztó lekérése C#-ban – teljes Aspose.Words útmutató

Ha szükséged van a **retrieve footnote separator** lekérésére egy Word dokumentumból, ez a tutorial pontosan megmutatja, hogyan teheted meg az Aspose.Words for .NET segítségével. Akár dokumentumfeldolgozó szolgáltatást építesz, akár a lábjegyzet formázását tisztítod, egy teljes, futtatható példát láthatsz, amely mind a lábjegyzet, mind az végjegyzet elválasztókat kinyeri.

Ebben az útmutatóban megtanulod, hogyan tölts be egy `.docx` fájlt, hogyan hívod meg a `FootnoteSeparator` és `EndnoteSeparator` tulajdonságokat, hogyan vizsgáld meg a visszakapott `Node` objektumokat, és opcionálisan hogyan cseréld le az elválasztó vonalat. Külső dokumentációra nincs szükség – minden, amire szükséged van, alább megtalálható.

## Előfeltételek

* .NET 6.0 vagy újabb (a kód .NET Framework 4.7.2‑n is működik)
* Aspose.Words for .NET NuGet csomag (24.9 vagy újabb verzió)
* Egy Word dokumentum, amely lábjegyzeteket és/vagy végjegyzeteket tartalmaz (pl. `Footnotes.docx`)

Az Aspose.Words csomagot a következő CLI parancs segítségével adhatod hozzá:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

## 1. lépés: A projekt beállítása és névterek importálása

Hozz létre egy új konzolos projektet, vagy add hozzá a kódot egy meglévőhöz. A szükséges `using` direktívák alább találhatók.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

Ezek a névterek hozzáférést biztosítanak a `Document` osztályhoz, a `Node` hierarchiához és a `NodeType` felsoroláshoz, amely a **retrieve footnote separator** műveletekhez szükséges.

## 2. lépés: A lábjegyzeteket és végjegyzeteket tartalmazó dokumentum betöltése

Az első művelet bármely Aspose.Words munkafolyamatban a forrásfájl betöltése. Cseréld le a helyőrző útvonalat a `.docx` tényleges helyére.

```csharp
// Load a document that contains footnotes and endnotes
Document doc = new Document(@"C:\Docs\Footnotes.docx");

// Verify that the document was loaded
Console.WriteLine($"Document loaded: {doc.OriginalFileName}");
```

A fájl betöltése előkészíti a belső node-fát, ami elengedhetetlen a **retrieve footnote separator** számára, mivel az elválasztó node-ok ebben a fában találhatók.

## 3. lépés: A lábjegyzet elválasztó node lekérése

Most a `Document` objektum `FootnoteSeparator` tulajdonságának elérésével **retrieve footnote separator** hajtható végre. Ez a node a lábjegyzeteket a fő szövegtől elválasztó vonalat képviseli.

```csharp
// Retrieve the footnote separator node (the line that separates footnotes from the main text)
Node footnoteSeparator = doc.FootnoteSeparator;

// Output its type for verification
Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");
```

A `NodeType` egy szabványos elválasztó vonal esetén `Paragraph` lesz. A node típus ismerete segít eldönteni, hogy módosítani kell-e az elválasztót, vagy teljesen cserélni.

## 4. lépés: A végjegyzet elválasztó node lekérése

Hasonlóan, a `EndnoteSeparator` tulajdonság használatával **retrieve endnote separator** hajtható végre. Ez a node a végjegyzeteket a fő tartalomtól választja el.

```csharp
// Retrieve the endnote separator node (the line that separates endnotes from the main text)
Node endnoteSeparator = doc.EndnoteSeparator;

// Output its type for verification
Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");
```

Mindkét elválasztó node a legtöbb dokumentumban ugyanazt a `NodeType`-ot (`Paragraph`) használja, de függetlenül testreszabhatók.

## 5. lépés: Az elválasztó tartalmának ellenőrzése vagy módosítása (opcionális)

Ha meg kell változtatnod az elválasztó vizuális megjelenését – például egy kötőjelekből álló vonalat vékony vonallá cserélni – közvetlenül szerkesztheted a `Paragraph` node-ot. Az alábbi példa a alapértelmezett elválasztó szöveget egy egyedi karakterláncra cseréli.

```csharp
// Cast to Paragraph to access its text
Paragraph footnotePara = (Paragraph)footnoteSeparator;
footnotePara.Clear(); // Remove existing runs
footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

// Do the same for the endnote separator
Paragraph endnotePara = (Paragraph)endnoteSeparator;
endnotePara.Clear();
endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));
```

A node-ok módosítása után mentheted a dokumentumot, hogy a változások megjelenjenek a Wordben.

```csharp
// Save the updated document
string outputPath = @"C:\Docs\Footnotes_Updated.docx";
doc.Save(outputPath);
Console.WriteLine($"Updated document saved to: {outputPath}");
```

## Várható konzolkimenet

A program futtatásakor az eredeti `Footnotes.docx`-el valami hasonlót kell látnod:

```
Document loaded: Footnotes.docx
Footnote separator node type: Paragraph
Endnote separator node type: Paragraph
Updated document saved to: C:\Docs\Footnotes_Updated.docx
```

Ha megnyitod a `Footnotes_Updated.docx`-et a Microsoft Wordben, a lábjegyzet és végjegyzet elválasztók a beillesztett egyedi szöveget fogják mutatni.

## Gyakori kérdések és szélsőséges esetek

**Mi van, ha a dokumentumnak nincsenek lábjegyzetei?**  
A `FootnoteSeparator` tulajdonság továbbra is egy `Paragraph` node-ot ad vissza, mivel a Word mindig tartalmaz egy elválasztó helyőrzőt. A node üres lesz, így nyugodtan hozzáadhatsz tartalmat, vagy hagyhatod változatlanul.

**Lekérhetem az elválasztót egy adott szekcióhoz?**  
A lábjegyzet és végjegyzet elválasztók dokumentumszintűek, nem szekcióspecifikusak. Ha szekciónkénti vezérlésre van szükséged, a `Section.FootnoteOptions` és `Section.EndnoteOptions` használatával kell dolgoznod a globális elválasztó node-ok helyett.

**Működik ez .NET Core‑dal?**  
Igen. Az Aspose.Words for .NET platformfüggetlen, és ugyanaz a kód fut Windows, Linux és macOS rendszereken .NET 6+ verzióval.

**Milyen node típust várhatok?**  
Mind a `FootnoteSeparator`, mind az `EndnoteSeparator` egy `Paragraph` node-ot ad vissza (`NodeType.Paragraph`). Ha más típust kapsz, a dokumentum sérült lehet, és újra kell töltened vagy ellenőrizned a forrásfájlt.

## Teljes forráskód gyors másoláshoz

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace RetrieveFootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // Load the document containing footnotes and endnotes
            Document doc = new Document(@"C:\Docs\Footnotes.docx");
            Console.WriteLine($"Document loaded: {doc.OriginalFileName}");

            // Retrieve footnote separator
            Node footnoteSeparator = doc.FootnoteSeparator;
            Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");

            // Retrieve endnote separator
            Node endnoteSeparator = doc.EndnoteSeparator;
            Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");

            // OPTIONAL: Customize separator text
            Paragraph footnotePara = (Paragraph)footnoteSeparator;
            footnotePara.Clear();
            footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

            Paragraph endnotePara = (Paragraph)endnoteSeparator;
            endnotePara.Clear();
            endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));

            // Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Updated.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Updated document saved to: {outputPath}");
        }
    }
}
```

Másold a kódot egy `Program.cs` fájlba, állítsd be a fájl útvonalakat, és futtasd a `dotnet run` parancsot. A program bemutatja a teljes **retrieve footnote separator** munkafolyamatot, a dokumentum betöltésétől a módosítások mentéséig.

## Összegzés

Most már tudod, hogyan kell **retrieve footnote separator** és **endnote separator retrieval** használni az Aspose.Words for .NET segítségével, hogyan vizsgáld meg a `document node type`-jukat, és opcionálisan hogyan cseréld le a tartalmukat. Ez a technika lehetővé teszi a lábjegyzet formázásának automatizálását, egyedi elválasztó vonalak generálását, vagy a dokumentum struktúrájának ellenőrzését bármely C# alkalmazásban.

Ezután érdemes lehet kapcsolódó témákat felfedezni, például a **C# footnote extraction** egyedi lábjegyzet szövegekhez, vagy megtanulni, hogyan **modify footnote reference marks** a `FootnoteOptions` használatával. Mindkét koncepció közvetlenül az itt bemutatott node‑fa alapokra épül.

Boldog kódolást, és nyugodtan kísérletezz különböző elválasztó stílusokkal, hogy illeszkedjenek a projekted arculatához!

## Mi legyen a következő tanulnivalód?

Az alábbi tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljesen működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Szövegfeldolgozás lábjegyzetekkel és végjegyzetekkel](/words/english/net/working-with-footnote-and-endnote/)
- [Tartalom hozzáadása Document Builderrel az Aspose.Words for .NET-ben](/words/english/net/add-content-using-document-builder/)
- [Munka lábjegyzetekkel és végjegyzetekkel](/words/hindi/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}