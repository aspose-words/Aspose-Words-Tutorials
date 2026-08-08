---
category: general
date: 2026-08-07
description: Ismerje meg, hogyan adhat hozzá ActiveX vezérlőt egy Word dokumentumba
  C#-vel. Tartalmazza a makró gombhoz való társítását és kattintható gombok hozzáadását
  Word példákkal.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex control
- associate macro with button
- add clickable button word
- add command button word
language: hu
lastmod: 2026-08-07
og_description: Hogyan adjon hozzá ActiveX vezérlőt egy Word dokumentumhoz az Aspose.Words
  segítségével. Kövesse ezt az útmutatót a gomb beszúrásához, a makró gombhoz való
  társításához, és egy kattintható gomb szó hozzáadásához.
og_image_alt: Screenshot showing a Word document with an ActiveX command button inserted
  via Aspose.Words
og_title: Hogyan adhatunk hozzá ActiveX vezérlőt a Wordben – teljes C# útmutató
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  headline: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  name: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  steps:
  - name: Why each line matters
    text: '| Line | Purpose | |------|---------| | `Document doc = new Document();`
      | Instantiates a fresh Word package in memory. | | `DocumentBuilder builder
      = new DocumentBuilder(doc);` | Provides a fluent API for inserting content,
      including ActiveX controls. | | `InsertForms2OleControl` | The only Aspose.'
  - name: Common pitfalls when associating a macro
    text: '* **Macro security settings** – If the document is opened on a machine
      with strict security policies, the macro may be blocked. Provide instructions
      to lower the security level or sign the macro. * **Naming conflicts** – The
      macro name must be unique within the document’s VBA project; otherwise Word'
  - name: 'Edge case: Long captions'
    text: Word truncates captions that exceed the button’s width. To avoid clipping,
      either increase the width argument in `InsertForms2OleControl` or shorten the
      text. Testing with different languages (e.g., German or Japanese) is advisable
      because character width varies.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Hogyan adjon hozzá ActiveX vezérlőt a Wordben az Aspose.Words segítségével
  – lépésről lépésre útmutató
url: /hu/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan adjunk hozzá ActiveX vezérlőt a Word-hez az Aspose.Words segítségével

Ha programozott módon szeretne **hogyan adjunk hozzá ActiveX vezérlőt** egy Microsoft Word fájlba, ez a tutorial pontos lépéseket mutat be az Aspose.Words for .NET használatával. Meg fogja látni, hogyan szúrjon be egy parancsgombot, állítsa be a feliratát, és **makrót társítson a gombhoz**, hogy a vezérlő reagáljon, amikor a felhasználó rákattint. A végére egy makró‑engedélyezett `.docm` fájlt kap, amely egy teljesen működő gombot tartalmaz.

Az ActiveX gomb hozzáadása gyakori igény interaktív sablonok, például hitelkérelmek, alkalmazotti beléptető űrlapok vagy automatizált jelentések készítésekor. Ez az útmutató minden kódsort részletesen bemutat, elmagyarázza, **miért** fontos minden lépés, és kitér a tipikus buktatókra, amelyekkel szembesülhet.

## Előfeltételek

Mielőtt elkezdené, győződjön meg róla, hogy rendelkezik:

* .NET 6 (vagy .NET Core 3.1 / .NET Framework 4.8) telepítve.
* Érvényes Aspose.Words for .NET licenccel vagy ideiglenes értékelő kulccsal.
* Visual Studio 2022‑vel (vagy bármely C#‑t támogató IDE‑vel).
* Alapvető ismeretekkel a Word makrókról (VBA), ha a gomb által indítandó makrót szeretné megírni.

> **Pro tipp:** A minta futtatásakor mentse a kimenetet egy olyan mappába, ahol írási jogosultsága van, különben a `doc.Save` kivételt dob.

## Hogyan adjunk hozzá ActiveX vezérlőt egy Word dokumentumhoz az Aspose.Words segítségével

A megoldás középpontjában egy rövid C# program áll, amely új dokumentumot hoz létre, egy ActiveX **CommandButton** vezérlőt szúr be, és a fájlt makró‑engedélyezett dokumentumként (`.docm`) menti. A kód teljes és készen áll a másolás‑beillesztésre.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert an ActiveX CommandButton control (Forms2OleControl)
        // Parameters: control type, left, top, width, height (in points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            0,   // left position (points)
            0,   // top position (points)
            150, // width (points)
            30   // height (points)
        );

        // Step 3: Set the button's visible caption – this is the add clickable button word
        commandButton.Caption = "Click Me";

        // Step 4 (optional): Associate a macro with the button's click action
        // This demonstrates how to associate macro with button
        commandButton.OnAction = "MyMacro";

        // Step 5: Save the document as a macro‑enabled file to preserve the button reference
        // The file extension .docm tells Word to keep ActiveX controls and macros
        doc.Save("CommandButton.docm");
    }
}
```

### Miért fontos minden sor

| Sor | Cél |
|------|---------|
| `Document doc = new Document();` | Új Word csomagot hoz létre a memóriában. |
| `DocumentBuilder builder = new DocumentBuilder(doc);` | Folyékony API-t biztosít a tartalom, köztük az ActiveX vezérlők beszúrásához. |
| `InsertForms2OleControl` | Az egyetlen Aspose.Words metódus, amely ActiveX vezérlőt hoz létre; meg kell adni a vezérlő típusát (`CommandButton`) és annak geometriáját. |
| `commandButton.Caption = "Click Me";` | Beállítja a **kattintható gomb feliratát**, amelyet a végfelhasználó lát. Felirat nélkül a gomb üres lesz. |
| `commandButton.OnAction = "MyMacro";` | **makrót társít a gombhoz** – megmondja a Wordnek, mely VBA makrót futtassa a vezérlő kattintásakor. |
| `doc.Save("CommandButton.docm");` | A dokumentumot makró‑engedélyezett fájlként menti; egy normál `.docx` eltávolítaná a vezérlőt és a makrót. |

> **Megjegyzés:** A koordináták (bal, felső) pontban vannak megadva (1 pt ≈ 1/72 in). Igazítsa őket, hogy a gomb a kívánt helyen jelenjen meg az oldalon.

## Hogyan társítsunk makrót a gombhoz

Az `OnAction` tulajdonság a gombot egy `MyMacro` nevű VBA makróhoz köti. A makrót még létre kell hozni a Word fájlban, akár manuálisan, akár programozottan VBA kódot injektálva (az Aspose.Words nem ír VBA kódot). Íme egy minimális makró, amelyet a Word **Fejlesztő → Visual Basic** szerkesztőjével adhat hozzá:

```vba
Sub MyMacro()
    MsgBox "Button clicked!", vbInformation, "ActiveX Demo"
End Sub
```

Amikor a felhasználó megnyitja a `CommandButton.docm` fájlt és rákattint a gombra, a Word végrehajtja a `MyMacro`-t és megjelenít egy üzenetablakot. Ha a makróbiztonság **Minden makró letiltása értesítés nélkül** állapotra van állítva, a gomb le lesz tiltva. Tanácsolja a felhasználóknak, hogy engedélyezzék a makrókat a dokumentumhoz, vagy írják alá a makrót egy megbízható tanúsítvánnyal.

### Gyakori buktatók a makró társításakor

* **Makróbiztonsági beállítások** – Ha a dokumentum szigorú biztonsági szabályokkal rendelkező gépen nyílik meg, a makró blokkolva lehet. Adjon útmutatót a biztonsági szint csökkentéséhez vagy a makró aláírásához.
* **Névütközések** – A makró neve egyedinek kell lennie a dokumentum VBA projektjében; ellenkező esetben a Word “duplicate procedure name” hibát jelez.
* **64‑bit vs 32‑bit Word** – Az ActiveX vezérlők ugyanúgy működnek, de a VBA szerkesztő különböző figyelmeztető üzeneteket jeleníthet meg az Office verziójától függően.

## Hogyan adjunk hozzá kattintható gomb feliratot egy Word űrlaphoz

A `Caption` tulajdonság határozza meg, mit látnak a felhasználók a gombon. További testreszabás lehetséges:

```csharp
commandButton.Caption = "Submit Form";
commandButton.Font.Size = 10;      // Adjust font size
commandButton.Font.Name = "Arial"; // Choose a readable font
```

Ha a feliratnak dinamikusan kell változnia a felhasználói bemenet alapján, később a Word objektummodelljén keresztül érheti el a vezérlőt:

```vba
Sub UpdateButtonCaption()
    Dim btn As InlineShape
    Set btn = ActiveDocument.InlineShapes(1).OLEFormat.Object
    btn.Caption = "Updated Text"
End Sub
```

### Szélsőséges eset: Hosszú feliratok

A Word levágja a gomb szélességét meghaladó feliratokat. A vágás elkerülése érdekében növelje a `InsertForms2OleControl` szélesség‑argumentumát, vagy rövidítse a szöveget. Érdemes különböző nyelvekkel (pl. német vagy japán) tesztelni, mivel a karakterek szélessége változik.

## Hogyan adjunk hozzá parancsgomb szót az űrlap‑automatizáláshoz

A vizuális feliraton túl a **add command button word** koncepció a vezérlő programozott nevét jelenti. Az Aspose.Words nem biztosít közvetlen `Name` tulajdonságot az ActiveX vezérlőknek, de beállíthatja az `AltText` mezőt, amelyet a Word a vezérlő azonosítójának tekint:

```csharp
commandButton.AltText = "SubmitButton";
```

Később VBA‑ban a gombot az `AltText` értékével hivatkozhatja:

```vba
Sub FindButton()
    Dim shp As Shape
    For Each shp In ActiveDocument.Shapes
        If shp.AlternativeText = "SubmitButton" Then
            MsgBox "Found the Submit button!"
        End If
    Next shp
End Sub
```

Ez a technika akkor hasznos, ha több gombja van, és programozottan kell megkülönböztetni őket.

## Teljes működő példa

Az alábbi program a teljes kód, amelyet lefordíthat és futtathat konzolos alkalmazásként. Tartalmaz opcionális stílusbeállításokat, makró‑társítást és egy megjegyzésblokkot, amely minden lépést leír.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class AddActiveXButton
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert an ActiveX CommandButton.
        //    left=50pt, top=100pt places the button away from the margin.
        Forms2OleControl btn = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            50,   // left
            100,  // top
            200,  // width
            40    // height
        );

        // 3️⃣ Add clickable button word (caption) and style it.
        btn.Caption = "Submit Form";
        btn.Font.Size = 11;
        btn.Font.Name = "Calibri";

        // 4️⃣ Associate macro with button – this is how to associate macro with button.
        btn.OnAction = "SubmitMacro";

        // 5️⃣ Give the control a friendly identifier (add command button word).
        btn.AltText = "SubmitButton";

        // 6️⃣ Save as macro‑enabled document.
        doc.Save("SubmitForm.docm");
    }
}
```

**Várható eredmény:** A `SubmitForm.docm` megnyitása a Microsoft Wordben egy kék‑keretű gombot jelenít meg, amelyen a *Submit Form* felirat látható. A gomb megnyomásakor a `SubmitMacro` VBA makró fut (ha hozzáadta a makrót a dokumentumhoz). A gomb tovább mozgatható, átméretezhető vagy stílusosan formázható ugyanazzal a `Forms2OleControl` objektummal.

## A megoldás tesztelése

1. Építse és futtassa a C# konzolos alkalmazást.
2. Nyissa meg a generált `SubmitForm.docm` fájlt a Wordben.
3. Ha a program kéri, engedélyezze a makrókat.
4. Kattintson a *Submit Form* gombra – meg kell jelennie a `SubmitMacro`‑ban definiált üzenetablaknak.

Ha a gomb megjelenik, de nem csinál semmit, ellenőrizze, hogy a makró neve pontosan egyezik‑e (`SubmitMacro`), és hogy a makróbiztonság nem blokkolja‑e a végrehajtást.

## Gyakran ismételt kérdések

| Kérdés | Válasz |
|----------|--------|
| *Hozzáadhatok több ActiveX gombot?* | Igen. Hívja meg többször az `InsertForms2OleControl`‑t különböző koordinátákkal. Használjon külön `OnAction` és `AltText` értékeket a megkülönböztetéshez. |
| *Látható az ActiveX vezérlő a Word Online‑ban?* | Nem. |

## Mit érdemes még tanulni?

Az alábbi tutorialok szorosan kapcsolódó témákat fednek le, amelyek tovább építik a jelen útmutatóban bemutatott technikákat. Minden forrás tartalmaz teljes, működő kódpéldákat lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API‑funkciókat és alternatív megvalósítási megközelítéseket saját projektjeiben.

- [Tartalom hozzáadása a Document Builder segítségével az Aspose.Words for .NET-ben](/words/english/net/add-content-using-document-builder/)
- [Aspose.Words alakzat árnyék tutorial – Árnyék hozzáadása Word alakzathoz C#-ban](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Új szakasz hozzáadása Word dokumentumhoz | Aspose.Words for .NET](/words/english/net/document-sections/add-section/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}