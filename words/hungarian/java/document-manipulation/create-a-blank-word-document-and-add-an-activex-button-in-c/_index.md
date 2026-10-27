---
category: general
date: 2026-10-23
description: Üres Word-dokumentum létrehozása C#-vel, és megtanulni, hogyan szúrjunk
  be ActiveX vezérlőket, többek között egy gombot, az Aspose.Words segítségével.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- create activex control
- word document activex button
language: hu
lastmod: 2026-10-23
og_description: Készítsen üres Word-dokumentumot C#-vel, és tanulja meg, hogyan illesszen
  be ActiveX vezérlőket, többek között egy gombot, az Aspose.Words használatával.
og_image_alt: Result of creating a blank Word document with an ActiveX Submit button
og_title: Üres Word-dokumentum létrehozása és ActiveX gomb hozzáadása C#‑ban
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button in C#
  type: TechArticle
- description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  name: Create a blank Word document and add an ActiveX button in C#
  steps:
  - name: Instantiate a `Document`.
    text: Instantiate a `Document`.
  - name: Use `DocumentBuilder` to work with the file.
    text: Use `DocumentBuilder` to work with the file.
  - name: Call `InsertForms2OleControl` to **how to insert activex** controls.
    text: Call `InsertForms2OleControl` to **how to insert activex** controls.
  - name: Configure the control’s properties (**create activex control**).
    text: Configure the control’s properties (**create activex control**).
  - name: Save the file, yielding a **word document activex button** ready for VBA
      integration.
    text: Save the file, yielding a **word document activex button** ready for VBA
      integration.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Hozzon létre egy üres Word-dokumentumot, és adjon hozzá egy ActiveX gombot
  C#‑ban.
url: /hu/java/document-manipulation/create-a-blank-word-document-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Üres Word dokumentum létrehozása és ActiveX gomb hozzáadása C#-ban

Ha programozott módon **üres Word dokumentumot** kell létrehoznod, ez az útmutató pontosan megmutatja, hogyan. Látni fogsz egy teljes, futtatható példát, amely új dokumentumot hoz létre, egy ActiveX CommandButton-t szúr be, és elmenti a fájlt – mindezt az Aspose.Words for .NET segítségével.

A Word fájlok kezelése gyakran többet igényel, mint egyszerű szöveget. Egy **ActiveX gomb** hozzáadása lehetővé teszi interaktív funkciók beágyazását, amelyeket makró‑engedélyezett sablonokban vagy csak Windows‑ra szánt megoldásokban lehet használni. A tutorial végére képes leszel bármilyen ActiveX vezérlő beillesztésére, de a leggyakoribb esetre koncentrálunk: egy **Word dokumentum ActiveX gomb**, amely űrlapot küld el.

## Előkövetelmények

* .NET 6.0 vagy újabb (a kód .NET Framework 4.7+‑vel is működik)
* Visual Studio 2022 (vagy bármely C# IDE)
* **Aspose.Words for .NET** NuGet csomag  
  ```bash
  dotnet add package Aspose.Words
  ```
* Alapvető ismeretek a C# szintaxisban

> **Pro tipp:** Az Aspose.Words egy kereskedelmi könyvtár, de ingyenes ideiglenes licencet biztosít teszteléshez. Telepítsd a licencet korán, hogy elkerüld a kiértékelési vízjelet.

## 1. lépés: Üres Word dokumentum létrehozása Aspose.Words segítségével

Az első lépés egy `Document` objektum példányosítása. Ez egy üres `.docx` fájlt reprezentál a memóriában.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
```

`Document` kezdetben nincs szekciója, oldala vagy tartalma. Ez a tiszta kiindulási alap, amire a **üres Word dokumentum létrehozása** forgatókönyvekhez, például a jelentések nulláról történő generálásához szükséged van.

## 2. lépés: DocumentBuilder beszerzése a dokumentum szerkesztéséhez

`DocumentBuilder` kényelmes API-t biztosít szöveg, kép és vezérlők hozzáadásához. Ezt fogjuk használni az ActiveX vezérlő elhelyezéséhez.

```csharp
// Obtain a DocumentBuilder tied to the blank document
DocumentBuilder builder = new DocumentBuilder(document);
```

A builder automatikusan hozzáad egy alapértelmezett szekciót és az első oldalt, így azonnal elkezdhetsz objektumokat beszúrni.

## 3. lépés: ActiveX vezérlők beszúrása a dokumentumba

Az Aspose.Words a `InsertForms2OleControl` metódust biztosítja OLE/ActiveX objektumok beágyazásához. A metódus a vezérlő típusát, a szélességet és a magasságot (pontban) igényli. Az alábbiakban egy **CommandButton**-t szúrunk be – a klasszikus űrlapgombot, amelyet a régi Word sablonokban látsz.

```csharp
// Insert an ActiveX CommandButton control (100 × 30 points)
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

> **Miért működik:** A `Forms2OleControlType.COMMANDBUTTON` azt mondja a Wordnek, hogy hozzon létre egy gombot, amely kattintási eseményekre reagál, amikor a dokumentumot egy ActiveX‑t támogató Windows környezetben nyitják meg.

## 4. lépés: ActiveX vezérlő létrehozása – tulajdonságok beállítása

Most adunk a gombnak egy programozott nevet és egy látható feliratot. Ez a **ActiveX vezérlő létrehozása** része, amelyet a fejlesztők gyakran figyelmen kívül hagynak.

```csharp
// Set the button's name (used in VBA) and the text shown to users
commandButton.Name = "btnSubmit";
commandButton.Caption = "Submit";
```

* `Name` az azonosító, amelyet a VBA makrókból (`ActiveDocument.InlineShapes("btnSubmit")`) hivatkozol.
* `Caption` a gombon megjelenő felirat.

## 5. lépés: Word dokumentum mentése az ActiveX gombbal

Végül írjuk a dokumentumot a lemezre. A fájlkiterjesztésnek `.docx`-nek kell lennie (vagy `.docm`, ha később makrókat szeretnél hozzáadni). A példa egy helyőrző mappába ment – cseréld le a saját útvonaladra.

```csharp
// Save the document containing the ActiveX button
string outputPath = @"C:\Temp\ActiveXButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Amikor megnyitod a keletkezett fájlt a Microsoft Wordben (csak Windows), egy működő **Word dokumentum ActiveX gombot** látsz, amely VBA kóddal összekapcsolható.

## Teljes működő példa

Az alábbiakban a teljes program látható, amelyet beilleszthetsz egy új konzolprojektbe.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a blank Word document
            Document document = new Document();

            // 2. Get a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3. Insert an ActiveX CommandButton (100 × 30 points)
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

            // 4. Configure the button
            commandButton.Name = "btnSubmit";
            commandButton.Caption = "Submit";

            // 5. Save the file
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Várható kimenet a program futtatásakor**

```
Document saved to C:\Temp\ActiveXButton.docx
```

Nyisd meg a generált `ActiveXButton.docx` fájlt a Wordben, és egy **Submit** feliratú gombot látsz az első oldal tetején.

## Szélsőséges esetek és gyakori buktatók

| Situation | What to watch for | Recommendation |
|-----------|-------------------|----------------|
| macOS vagy Linux rendszeren futtatás | Az ActiveX Windows‑specifikus technológia, ezért a gomb helyőrzőként jelenik meg. | Használd a tutorialt csak Windows‑célú sablonokhoz. |
| Dokumentum megnyitása a Word Online‑ban | Az ActiveX vezérlők nem támogatottak a böngésző nézetben. | Biztosíts tartalék UI‑t vagy utasítsd a felhasználókat, hogy a fájlt a asztali kliensen nyissák meg. |
| Makró‑engedélyezett fájlra van szükség | A `.docx` fájlok nem tárolhatnak VBA kódot. | Mentsd `.docm`‑ként (`document.Save("MyFile.docm", SaveFormat.Docm)`) és add hozzá a makrót külön. |
| Vezérlő méreteltérés | A szélesség/magasság értékek pontban vannak (1 pt ≈ 1/72 in). | Állítsd a numerikus értékeket a kívánt vizuális méret eléréséhez. |

## Gyakran ismételt kérdések

**Hogyan szúrhatók be a gombon kívül más ActiveX vezérlők?**  
Használd ugyanazt a `InsertForms2OleControl` metódust, de adj meg egy másik `Forms2OleControlType` enum értéket, például `COMBOBOX` vagy `LISTBOX`.

**Módosíthatom a gomb betűtípusát vagy színét?**  
Az ActiveX gomb megjelenését a gazdaalkalmazás (Word) és az alatta lévő Windows téma szabályozza. A `ForeColor` és `BackColor` tulajdonságokat VBA‑val módosíthatod a dokumentum megnyitása után.

**Lehet-e közvetlenül C#‑ból hozzáadni egy kattintás‑kezelőt?**  
Nem. A kattintási eseményt VBA‑val vagy egy Word‑kiegészítővel kell kezelni, mivel a gomb a Word folyamatában fut, nem a .NET alkalmazásodban.

## Következtetés

Most már tudod, hogyan **hozz létre programozott módon üres Word dokumentumot** és ágyazz be egy **ActiveX gombot** az Aspose.Words for .NET segítségével. A lefedett lépések:

1. Példányosíts egy `Document`-ot.
2. `DocumentBuilder` használata a fájl kezeléséhez.
3. Hívd meg az `InsertForms2OleControl`-t a **ActiveX vezérlők beszúrásához**.
4. Állítsd be a vezérlő tulajdonságait (**ActiveX vezérlő létrehozása**).
5. Mentsd a fájlt, így egy **Word dokumentum ActiveX gomb** jön létre, amely készen áll a VBA integrációra.

Innen tovább felfedezheted más vezérlőtípusok hozzáadását, VBA makrók összekapcsolását, vagy a dokumentum PDF‑re konvertálását a gomb megtartásával (statikus képként). Kísérletezz különböző méretekkel, feliratokkal és nevekkel.

## Mit érdemes legközelebb megtanulni?

Az alábbi tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [How to add ActiveX button in a Word document with Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Create Word Document with ActiveX Button – C# Guide](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}