---
category: general
date: 2026-08-20
description: Tanulja meg, hogyan hozhat létre ActiveX‑vezérlőt, állíthatja be a gomb
  méretét, és adhat hozzá gombot a Wordhöz egy teljes C# példával.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- set button size
- add button to word
- how to insert button
- create clickable button
language: hu
lastmod: 2026-08-20
og_description: ActiveX vezérlő létrehozása Word-fájlban C#-val. Ez az útmutató bemutatja,
  hogyan állítsuk be a gomb méretét, adjuk hozzá a gombot a Wordhöz, és készítsünk
  kattintható gombot.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX control
  button
og_title: ActiveX-vezérlő létrehozása Wordben – lépésről lépésre C# útmutató
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  headline: How to create ActiveX control in a Word document using C#
  type: TechArticle
- description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  name: How to create ActiveX control in a Word document using C#
  steps:
  - name: Why this works
    text: '* `InsertForms2OleControl` tells Word to embed an OLE object of type **CommandButton**,
      which is the classic ActiveX button class. * The width and height arguments
      directly **set button size**; Word translates the values from points (1 pt ≈
      1/72 in). * Naming the control (`Name = "btnSubmit"`) makes'
  - name: Pro tip
    text: 'If you want a square button, set both dimensions to the same value:'
  - name: 1. What if the button does not appear after saving?
    text: '* Verify that the Aspose.Words version supports `InsertForms2OleControl`.
      Versions prior to 22.5 lack this feature. * Ensure the target file format is
      `.docx` or `.doc`. Older formats like `.rtf` cannot store ActiveX objects.'
  - name: 2. Can I insert the button at a specific bookmark?
    text: 'Yes. Move the builder to the bookmark before calling `InsertForms2OleControl`:'
  - name: 3. How to **set button size** dynamically based on text length?
    text: Calculate the required width using the `Graphics.MeasureString` method (from
      `System.Drawing`) and convert pixels to points (`points = pixels * 72 / DPI`).
      Then pass the computed width to `InsertForms2OleControl`.
  - name: 4. Is there a way to add multiple buttons in a loop?
    text: 'Absolutely. Wrap the insertion logic in a `for` loop and adjust the `Left`
      and `Top` properties for each iteration:'
  type: HowTo
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
title: Hogyan hozhatunk létre ActiveX-vezérlőt egy Word-dokumentumban C#-val
url: /hu/java/integration-interoperability/how-to-create-activex-control-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozhatunk létre ActiveX vezérlőt egy Word dokumentumban C#‑val

Ha **ActiveX vezérlőt** kell létrehoznod egy Microsoft Word fájlban, ez az útmutató pontosan megmutatja, hogyan teheted meg. Megtanulod, hogyan **adjunk gombot a Wordhöz**, állítsuk be a gomb méretét, és hogyan tegyük a vezérlőt kattinthatóvá – mindezt egy rövid, önálló C# programmal.

Ebben a tutorialban:

* Megérted, miért hasznos egy ActiveX vezérlő interaktív Word dokumentumokhoz.  
* Megtanulod a pontos kódot a **gombméret beállításához** és felirat hozzárendeléséhez.  
* Láthatod, hogyan **hozzunk létre kattintható gombot**, amely később makróhoz vagy külső logikához csatlakoztatható.  

A lépések az Aspose.Words .NET 23.12 vagy újabb verzióval működnek, és csak egy .NET fejlesztői környezetet igényelnek.

> **Előfeltétel** – Van érvényes Aspose.Words licenced (vagy az értékelő verziót használod) és Visual Studio 2022 vagy bármely C# IDE.

---

## Hogyan hozhatunk létre ActiveX vezérlőt egy Word dokumentumban

Az első lépés egy üres `Document` és egy `DocumentBuilder` példányosítása. A builder biztosítja a magas szintű API‑t objektumok, például ActiveX vezérlők beszúrásához.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document and obtain a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // The rest of the steps are explained in the following sections.
            InsertActiveXButton(builder);

            // Save the result so you can open it in Word.
            doc.Save("ActiveXButton.docx");
            Console.WriteLine("Document saved as ActiveXButton.docx");
        }
```

Az `InsertActiveXButton` metódus (lent definiálva) tartalmazza a **gomb beszúrásának** és konfigurálásának logikáját.

```csharp
        /// <summary>
        /// Inserts a CommandButton ActiveX control, sets its size, name, and caption.
        /// </summary>
        static void InsertActiveXButton(DocumentBuilder builder)
        {
            // Step 2: Insert a CommandButton ActiveX control with the desired size (width: 100, height: 30).
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                "CommandButton", 100, 30);

            // Step 3: Assign a name to the control for later reference.
            commandButton.Name = "btnSubmit";

            // Step 4: Set the caption that will be displayed on the button.
            commandButton.Caption = "Submit";

            // Optional: Position the button on the page (e.g., 100 points from the top left).
            commandButton.Left = 100;
            commandButton.Top = 150;
        }
    }
}
```

A program futtatása létrehozza a **ActiveXButton.docx** fájlt. A Wordben megnyitva egy **Submit** feliratú gomb jelenik meg. A vezérlő teljesen működőképes – a kattintás a szabványos `CommandButton_Click` eseményt váltja ki, amelyet később VBA makróhoz köthetsz.

### Miért működik ez

* `InsertForms2OleControl` azt mondja a Wordnek, hogy egy **CommandButton** típusú OLE objektumot ágyazzon be, ami a klasszikus ActiveX gomb osztály.  
* A szélesség és magasság argumentumok közvetlenül **beállítják a gomb méretét**; a Word a pontokból (1 pt ≈ 1/72 in) számítja át.  
* A vezérlő elnevezése (`Name = "btnSubmit"`) megkönnyíti a VBA‑beli elérést (`ActiveDocument.InlineShapes("btnSubmit")`).  

---

## Gombméret és felirat beállítása

Ha más megjelenést szeretnél, módosítsd a numerikus argumentumokat az `InsertForms2OleControl` hívásban. A metódus aláírása:

```csharp
Forms2OleControl InsertForms2OleControl(string progId, double width, double height);
```

* **progId** – Az ActiveX osztály programozási azonosítója (`"CommandButton"` egy szabványos gombhoz).  
* **width / height** – Méret pontban. Egy 2 cm széles gombhoz használd a `width = 56.7` értéket (2 cm ≈ 56.7 pt).  

A feliratot is módosíthatod a beszúrás után:

```csharp
commandButton.Caption = "Send Request";
```

A felirat megváltoztatása nem befolyásolja a méretet, de a felhasználó számára látható visszajelzést változtat.

### Profi tipp

Ha négyzet alakú gombot szeretnél, állítsd mindkét dimenziót ugyanarra az értékre:

```csharp
Forms2OleControl squareBtn = builder.InsertForms2OleControl("CommandButton", 50, 50);
squareBtn.Caption = "OK";
```

---

## Gomb hozzáadása a Wordhöz és kattinthatóvá tétele

A fenti kód már **gombot ad a Wordhöz**. Ahhoz, hogy a gomb műveletet hajtson végre, VBA makrót kell írnod, amely kezeli a `Click` eseményt. Íme egy minimális makró, amelyet a Word VBA szerkesztőjébe ( `Alt+F11` → Insert → Module) másolhatsz:

```vba
Sub btnSubmit_Click()
    MsgBox "You clicked the Submit button!", vbInformation
End Sub
```

Mivel a vezérlő neve `btnSubmit`, a Word automatikusan a `Click` eseményt a `btnSubmit_Click`-hez rendeli. Ez a szabványos módja a **kattintható gomb** funkció létrehozásának külső könyvtárak nélkül.

> **Megjegyzés:** A Word makróbiztonsági beállításai blokkolhatják az ActiveX vezérlőket. Győződj meg róla, hogy a dokumentumhoz a „Enable all macros” vagy „Enable VBA macros” opció van kiválasztva, vagy digitálisan írd alá a makrót éles használathoz.

---

## Gyakori kérdések: gomb beszúrása és hibakeresés

### 1. Mi van, ha a gomb nem jelenik meg a mentés után?

* Ellenőrizd, hogy az Aspose.Words verzió támogatja-e az `InsertForms2OleControl` metódust. A 22.5 előtti verziók nem tartalmazzák ezt a funkciót.  
* Győződj meg róla, hogy a célfájl formátuma `.docx` vagy `.doc`. Régebbi formátumok, például `.rtf`, nem tudnak ActiveX objektumot tárolni.

### 2. Beszúrhatom a gombot egy konkrét könyvjelzőhöz?

Igen. A builder-t mozdítsd a könyvjelzőhöz, mielőtt meghívod az `InsertForms2OleControl`-t:

```csharp
builder.MoveToBookmark("InsertHere");
builder.InsertForms2OleControl("CommandButton", 100, 30);
```

### 3. Hogyan **állítsuk be a gombméretet** dinamikusan a szöveg hossza alapján?

Számold ki a szükséges szélességet a `Graphics.MeasureString` metódussal (`System.Drawing`), majd konvertáld a pixeleket pontokra (`points = pixels * 72 / DPI`). Ezt a számított szélességet add át az `InsertForms2OleControl`-nek.

### 4. Van mód több gomb hozzáadására egy ciklusban?

Természetesen. Csomagold be a beszúrási logikát egy `for` ciklusba, és állítsd be a `Left` és `Top` tulajdonságokat minden iterációhoz:

```csharp
for (int i = 0; i < 3; i++)
{
    Forms2OleControl btn = builder.InsertForms2OleControl("CommandButton", 80, 25);
    btn.Name = $"btnOption{i + 1}";
    btn.Caption = $"Option {i + 1}";
    btn.Left = 50;
    btn.Top = 100 + i * 40; // stagger vertically
}
```

---

## Várható kimenet

Amikor futtatod a programot és megnyitod a **ActiveXButton.docx** fájlt:

* Egyetlen **Submit** gomb jelenik meg az első oldal bal‑felső sarkában.  
* A gomb mérete megegyezik a megadott dimenziókkal (`100 pt × 30 pt`).  
* Ha hozzáadtad a VBA makrót, a gomb kattintása egy üzenetdobozot jelenít meg: „You clicked the Submit button!”.

Sikeresen **létrehoztad az ActiveX vezérlőt**, **beállítottad a gombméretet**, és **gombot adtál a Wordhöz**, miközben megtanultad, hogyan **szúrj be gombot** és **hozz létre kattintható gombot** a jövőbeli automatizálási feladatokhoz.

---

## Összegzés

Ebben a tutorialban megtanultad, hogyan **hozz létre ActiveX vezérlőt** egy Word dokumentumban C#‑val. A lépések követésével **beállíthatod a gombméretet**, értelmes nevet adhatod a vezérlőnek, és **gombot adhatsz a Wordhöz**, így egy **kattintható gomb** lesz, amely VBA makróhoz kapcsolódik.  

Innen tovább:

* A gomb .NET COM add‑inhez kötése VBA helyett.  
* Más ActiveX osztályok használata, például `CheckBox` vagy `ComboBox`.  
* Teljes űrlapok automatizálása több vezérlővel.

Nyugodtan kísérletezz különböző méretekkel


## Mit érdemes még megtanulni?

A következő tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Create Word Document with Floating Image in .NET](/words/english/net/add-content-using-document-builder/insert-floating-image/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create Accessible PDF from Word – Complete Guide](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-from-word-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}