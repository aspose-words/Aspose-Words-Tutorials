---
category: general
date: 2026-08-23
description: Beküldés gomb létrehozása C# Word automatizálásban. Tanulja meg, hogyan
  adjon hozzá ActiveX gombot, és programozottan állítsa be a gomb nevét, feliratát
  és szövegét.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create submit button
- set button text
- set button name
- add activex button
- set button caption
language: hu
lastmod: 2026-08-23
og_description: Küldés gomb létrehozása C# Word automatizálásban. Ez az útmutató bemutatja,
  hogyan adhatunk hozzá ActiveX gombot, és állíthatjuk be a nevét, feliratát és szövegét
  az Aspose.Words használatával.
og_image_alt: Screenshot of a Word document showing a created submit button
og_title: Beküldés gomb létrehozása C# Word automatizálásban
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  headline: How to create submit button in C# Word automation
  type: TechArticle
- description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  name: How to create submit button in C# Word automation
  steps:
  - name: Expected output
    text: 'Running the program creates `SubmitButton.docx`. When you open the file
      in Microsoft Word:'
  - name: Handling naming collisions
    text: 'If you run the routine multiple times on the same document, Word may auto‑rename
      duplicate controls. To guarantee uniqueness, you can prepend a GUID:'
  - name: Localizing the button caption
    text: 'For multilingual documents, store captions in a resource file and assign
      them at runtime:'
  - name: Responding to the button click
    text: 'The button itself does not contain click logic in C#. You typically attach
      a VBA macro:'
  type: HowTo
tags:
- C#
- Word automation
- ActiveX
- Aspose.Words
title: Hogyan hozzunk létre beküldés gombot C# Word automatizálásban
url: /hu/net/working-with-oleobjects-and-activex/how-to-create-submit-button-in-c-word-automation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre elküldés gombot C# Word automatizálásban

Ha C#-ban Word dokumentumban **submit gombot** kell létrehozni, ez az útmutató végigvezet a teljes folyamaton. Megmutatjuk, hogyan adjon hozzá egy ActiveX gombot, rendeljön hozzá programozási nevet, és állítsa be a gomb feliratát, hogy úgy nézzen ki, mint egy szokásos *Submit* vezérlő.

A Word űrlapvezérlőinek automatizálása helyettesítheti a kézi elrendezési munkát, és biztosítja a konzisztenciát több száz dokumentumban. Az alábbi lépésekben megtanulja, hogyan **állítsa be a gomb szövegét**, **állítsa be a gomb nevét**, és **állítsa be a gomb feliratát** – mindez elengedhetetlen, ha a gomb makró‑vezérelt munkafolyamatban vesz részt.

## Prerequisites

Mielőtt elkezdené, győződjön meg róla, hogy rendelkezik:

* .NET 6.0 (vagy újabb) telepítve.
* **Aspose.Words for .NET** hivatkozással (az a könyvtár, amely biztosítja a `DocumentBuilder.InsertForms2OleControl` metódust).
* Alapvető C# és a Word ActiveX űrlapvezérlőinek ismeretével.

Az Aspose.Words telepíthető a NuGet-en keresztül:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Használja az Aspose.Words legújabb stabil verzióját, hogy részesüljön a hibajavításokból és az ActiveX vezérlőkkel kapcsolatos új funkciókból.

## Overview of the solution

Az útmutató három egyértelmű lépésre van bontva:

1. **Add ActiveX button** – használja az `InsertForms2OleControl` metódust egy parancsgomb elhelyezéséhez a dokumentumban.  
2. **Set button name** – egyedi programozási azonosítót adjon a `Name` tulajdonsággal.  
3. **Set button caption** – a gomb látható szövegét a `Caption` tulajdonsággal definiálja (ez irányítja a **set button text** megjelenítését is a felhasználói felületen).

A útmutató végére egy teljesen működő **create submit button** rutinja lesz, amelyet bármely Word automatizálási projektben újra felhasználhat.

## Step 1: Add an ActiveX button to the document

Az első feladat a **add activex button** hozzáadása a Word fájlhoz. Az Aspose.Words a `Forms2OleControlType.CommandButton` enumerációt biztosítja ehhez a célhoz.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load or create a new document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a CommandButton ActiveX control at the cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton);
```

**Why this step matters:**  
Az ActiveX vezérlők az egyetlen Word űrlapelem, amely VBA makrókat tud végrehajtani vagy külső kóddal kommunikálni. A vezérlő hozzáadása egy helyőrzőt hoz létre, amelyet a későbbi lépések konfigurálni fognak.

> **Edge case:** Ha a dokumentum már tartalmaz egy azonos nevű vezérlőt, a Word automatikusan átnevezi az újat (pl. `CommandButton1`). A név explicit beállítása a következő lépésben elkerüli az ilyen ütközéseket.

## Step 2: Set the button name

Egy megbízható **set button name** elengedhetetlen, amikor a vezérlőt VBA‑ból vagy a C# kódból kell hivatkozni. A `Name` tulajdonság programozási azonosítót ad a gombnak.

```csharp
// Assign a unique programmatic name
commandBtn.Name = "btnSubmit";
```

**Why you should set a name:**  
A dokumentum megnyitásakor a VBA a `ActiveDocument.InlineShapes("btnSubmit")` segítségével lekérheti a gombot. Egy értelmes név, például `btnSubmit`, egyértelművé teszi a szándékot, amikor a dokumentum XML‑ét vizsgálja.

> **Pro tip:** Tartsa a neveket röviden, alfanumerikusan, és kezdje betűvel, hogy kompatibilisek legyenek a VBA elnevezési szabályaival.

## Step 3: Set the button caption (visible text)

A felhasználók által a gombon látott szöveget a **set button caption** tulajdonság szabályozza. A Word felhasználói felületén ez a gomb címkéje, amely egyben a **set button text** is, amit meg szeretne jeleníteni.

```csharp
// Define the text shown on the button
commandBtn.Caption = "Submit";
```

**Why the caption matters:**  
A felirat a felhasználó számára látható címke. Későbbi módosítása nem érinti a gomb nevét, így a UI‑t lokalizálhatja anélkül, hogy a `btnSubmit`‑ra hivatkozó kód megsérülne.

> **Common question:** *Can I set both Caption and Value?*  
> A `CommandButton` esetén a `Caption` vezérli a címkét, míg a `Value` nincs használatban. Ha rejtett értékre van szükség, azt egy egyéni dokumentumtulajdonságban tárolja.

## Full working example

A három lépés összevonásával egy komplett rutin jön létre, amelyet bármely konzol‑ vagy Windows‑alkalmazásba beilleszthet:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert the ActiveX command button
        Forms2OleControl commandBtn = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton);

        // 3. Set a meaningful name for later reference
        commandBtn.Name = "btnSubmit";

        // 4. Set the visible caption (this is the button text)
        commandBtn.Caption = "Submit";

        // Optional: position the button (in points)
        commandBtn.Left = 100;   // distance from left margin
        commandBtn.Top = 200;    // distance from top margin
        commandBtn.Width = 80;
        commandBtn.Height = 30;

        // Save the document
        doc.Save("SubmitButton.docx");
        Console.WriteLine("Document with submit button created successfully.");
    }
}
```

### Expected output

A program futtatása létrehozza a `SubmitButton.docx` fájlt. Amikor megnyitja a fájlt a Microsoft Wordben:

* Egy **Submit** gomb jelenik meg a megadott helyen.
* A gomb neve `btnSubmit` (ellenőrizhető a *Developer → Design Mode → Properties* menüpontban).
* A tervezői módban a gomb kattintásakor a felirat *Submit* jelenik meg.

Most már van egy újrahasználható építőeleme bármely űrlap‑vezérelt Word megoldáshoz.

## Additional considerations

### Handling naming collisions

Ha a rutint többször futtatja ugyanazon a dokumentumon, a Word automatikusan átnevezi a duplikált vezérlőket. Az egyediség garantálásához előtagként használhat egy GUID‑ot:

```csharp
commandBtn.Name = $"btnSubmit_{Guid.NewGuid():N}";
```

### Localizing the button caption

Többnyelvű dokumentumok esetén tárolja a feliratokat egy erőforrásfájlban, és rendelje őket futásidőben:

```csharp
commandBtn.Caption = Resources.SubmitButtonLabel;
```

### Responding to the button click

A gomb önmagában nem tartalmaz kattintási logikát C#‑ban. Általában egy VBA makrót csatol:

```vba
Sub btnSubmit_Click()
    MsgBox "Form submitted!"
End Sub
```

Mivel **set button name**-t `btnSubmit`‑re állította, a makró neve automatikusan a `<Name>_Click` konvenciót követi.

## Troubleshooting FAQ

| Question | Answer |
|----------|--------|
| **Why does the button appear blank?** | Győződjön meg róla, hogy beállította a `Caption` tulajdonságot; enélkül a gomb nem jelenít meg szöveget. |
| **Can I use a different ActiveX control?** | Igen. Cserélje le a `Forms2OleControlType.CommandButton`-t `CheckBox`, `OptionButton` stb. típusra, de a tulajdonságok eltérnek. |
| **Is this compatible with .NET Core?** | Az Aspose.Words for .NET támogatja a .NET 6+ verziókat, így ugyanaz a kód működik .NET Core‑on és .NET Framework‑ön is. |
| **What if the document already has a button?** | Használjon egyedi `Name`‑t (például fűzzön hozzá egy GUID‑ot), hogy elkerülje az ütközéseket. |

## Conclusion

Most már tudja, hogyan kell **create submit button**-t programozottan létrehozni egy Word dokumentumban C#‑val. A három lépés – **add activex button**, **set button name**, és **set button caption** – követésével megbízhatóan **set button text**, **set button name**, és **set button caption** állítható be bármilyen automatizált űrlapmegoldáshoz.

Innen tovább:

* VBA makrók hozzáadása, amelyek reagálnak a **submit button** kattintására.
* A gomb stílusának testreszabása egyedi betűtípusokkal vagy színekkel az alapszintű XML‑en keresztül.
* Több gomb generálása ciklusban dinamikus űrlapokhoz.

Kísérletezzen különböző feliratokkal, nevekkel és pozíciókkal, hogy a saját munkafolyamatához leginkább illeszkedjen. Boldog automatizálást!

## What Should You Learn Next?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsenek további API‑funkciók elsajátításában és alternatív megvalósítási megközelítések felfedezésében saját projektjeiben.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create a Line Chart in Word using Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}