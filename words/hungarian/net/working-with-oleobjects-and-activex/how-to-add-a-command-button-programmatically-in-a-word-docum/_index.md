---
category: general
date: 2026-10-13
description: Ismerje meg, hogyan adhat hozzá parancsgombot programozottan az Aspose.Words
  segítségével. Ez az útmutató azt is bemutatja, hogyan hozhat létre Word-dokumentum
  gombot teljes C# kóddal.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button programmatically
- create word document button
language: hu
lastmod: 2026-10-13
og_description: Programozott módon adj hozzá egy parancsgombot egy Word dokumentumhoz
  az Aspose.Words használatával. Kövesd ezt a teljes útmutatót, hogy C#‑al Word dokumentum
  gombot hozz létre.
og_image_alt: Screenshot of a Word document with a command button inserted programmatically
og_title: Parancsgomb hozzáadása programozottan egy Word-dokumentumhoz – lépésről
  lépésre útmutató
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  headline: How to add a command button programmatically in a Word document
  type: TechArticle
- description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  name: How to add a command button programmatically in a Word document
  steps:
  - name: 'Create a new console project:'
    text: 'Create a new console project:'
  - name: 'Add the Aspose.Words NuGet package:'
    text: 'Add the Aspose.Words NuGet package:'
  - name: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
    text: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Hogyan lehet programozottan parancsgombot hozzáadni egy Word-dokumentumhoz
url: /hu/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan adhatunk hozzá egy parancsgombot programozottan egy Word dokumentumban  

Ha **programozottan szeretne parancsgombot hozzáadni**, az Aspose.Words egy tiszta API-t biztosít, amely lehetővé teszi OLE űrlapvezérlők közvetlen beágyazását egy .docx fájlba. Ez az útmutató végigvezeti Önt minden szükséges lépésen, hogy **Word dokumentumban gombot hozzon létre**, amely a Microsoft Word‑ben megnyitott dokumentumban egy szokásos űrlapgombként viselkedik.  

Megtanulja, hogyan állítsa be a fejlesztői környezetet, hogyan illessze be a gombot, hogyan konfigurálja a tulajdonságait, és hogyan ellenőrizze az eredményt. Nem szükséges külső segédprogram – csak egy .NET projekt és az Aspose.Words for .NET könyvtár.  

## Előfeltételek  

Mielőtt elkezdené, győződjön meg róla, hogy rendelkezik:  

* .NET 6.0 SDK vagy újabb telepítve.  
* Az Aspose.Words for .NET egy friss verziójával (a példák 23.12‑t használnak, de bármely 22.x+ kiadás működik).  
* IDE‑vel, például Visual Studio 2022 vagy Visual Studio Code‑dal.  

A kód Windows, macOS és Linux rendszereken fut, mivel az Aspose.Words platform‑független.  

## 1. lépés: A projekt beállítása és az Aspose.Words hivatkozás hozzáadása  

1. Hozzon létre egy új konzolos projektet:  

   ```bash
   dotnet new console -n WordButtonDemo
   cd WordButtonDemo
   ```  

2. Adja hozzá az Aspose.Words NuGet csomagot:  

   ```bash
   dotnet add package Aspose.Words
   ```  

3. Nyissa meg a **Program.cs** fájlt, és cserélje ki a tartalmát a következő lépésekben bemutatott vázra.  

A projekt ilyen módon történő beállítása biztosítja, hogy a fordító megtalálja a `Aspose.Words` és `Aspose.Words.Drawing.Forms` névtereket, amelyek a űrlapvezérlőkhöz szükségesek.  

## 2. lépés: Üres dokumentum és DocumentBuilder inicializálása  

A `Document` osztály képviseli a teljes Word fájlt, míg a `DocumentBuilder` egy folyékony API‑t biztosít a tartalom hozzáadásához.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;
using System.Drawing;   // required for RectangleF

// Create an empty document.
Document doc = new Document();

// Create a builder linked to the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```  

*Miért fontos ez a lépés* – `DocumentBuilder` nélkül nem tudja pontosan elhelyezni a gombot az oldalon. A builder tiszteletben tartja az aktuális kurzorpozíciót, így később könnyen beilleszthet több vezérlőt.  

## 3. lépés: A parancsgomb OLE vezérlő beillesztése  

Az Aspose.Words a parancsgombot `ControlType.CommandButton` típusú OLE vezérlőnek kezeli. A helyét és méretét egy `RectangleF`‑el adja meg, amely pontban van mérve (1 pont = 1/72 hüvelyk).  

```csharp
// Define the button rectangle: X=100, Y=150, Width=120, Height=30 (points)
RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

// Insert the command button at the current cursor position.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    buttonRect);
```  

**Fontos pontok**  

* A téglalap origója (X, Y) a lap bal‑felső sarkához képest relatív.  
* A `Width` vagy `Height` módosítása a gomb vizuális méretét változtatja.  
* Az `InsertForms2OleControl` egy `Forms2OleControl` objektumot ad vissza, amelyet tovább konfigurálhat.  

## 4. lépés: A gomb neve és felirata beállítása  

A **név** a Word makrómotorja használja a vezérlő azonosítására, míg a **felirat** az a szöveg, amelyet a felhasználó lát.  

```csharp
// Set a unique identifier for the button.
commandButton.Name = "cmdSubmit";

// Set the text displayed on the button.
commandButton.Caption = "Submit";
```  

Ha később VBA makrókat tervez hozzáadni, használjon leíró nevet, mivel a Word makrórögzítője erre a tulajdonságra hivatkozik.  

## 5. lépés: (Opcionális) A dokumentum mentése és az eredmény ellenőrzése  

A fájl mentése lehetővé teszi, hogy megnyissa a Microsoft Word‑ben, és megerősítse, hogy a gomb megjelenik és működik.  

```csharp
// Save the document to the output folder.
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButtonDemo.docx");
doc.Save(outputPath);

Console.WriteLine($"Document saved to: {outputPath}");
```  

Amikor megnyitja a *CommandButtonDemo.docx* fájlt a Word‑ben, egy **Submit** feliratú gombot kell látnia, amely körülbelül 1,4 hüvelykre van a bal margótól és 2,1 hüvelykre a lap tetejétől. Alapértelmezés szerint a gomb kattintása nem csinál semmit, mivel nincs makró csatolva, de a vizuális vezérlő teljesen funkcionális.  

## 6. lépés: Szélső esetek és gyakori buktatók  

| Helyzet | Mire kell figyelni | Javasolt megoldás |
|-----------|-------------------|-----------------|
| **A gomb átfed meglévő szöveget** | A téglalap átfedhet egy bekezdéssel, ami elrendezési problémákat okozhat. | Illessze be a gombot a `builder.Writeln()` hívása után, hogy a kurzor egy új sorra kerüljön, vagy állítsa be a `Y` koordinátát. |
| **A dokumentum figyelmeztetéssel nyílik meg** | Egyes Word‑verziók OLE vezérlőket jelölnek meg, ha nincs hozzákapcsolt program. | Győződjön meg róla, hogy a vezérlő típusa `CommandButton`; a Word ezt szabványos űrlapelemként kezeli, és nem igényel külső programot. |
| **Linuxon fej nélküli környezetben futtatás** | A Word nem indítható a UI teszteléséhez, de a fájl érvényes marad. | Használjon egységtesztet, amely kiolvassa a vezérlő tulajdonságait (`commandButton.Name`, `commandButton.Caption`) a helyes beállítás ellenőrzéséhez. |
| **Több gomb szükséges** | Ugyanazt a `DocumentBuilder`‑t újra‑használva, anélkül hogy a kurzort mozgatná, a gomb a korábbi fölé kerül. | Hívja a `builder.MoveToDocumentEnd()`‑et, vagy állítsa be a téglalap `Y` értékét minden egyes beillesztés előtt. |

Ezeknek a szélső eseteknek a korai kezelése időt takarít meg, amikor a megoldást több tucat vezérlővel ellátott teljes űrlapokra skálázzuk.  

## 7. lépés: Teljes, futtatható példa  

Az alábbi önálló programot egyszerűen másolja, illessze be és futtassa módosítás nélkül (kivéve a NuGet visszaállítást).  

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

namespace WordButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a new empty document.
            Document doc = new Document();

            // 2. Create a DocumentBuilder to work with the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Define the button rectangle (position + size).
            RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

            // 4. Insert the command button OLE control.
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                buttonRect);

            // 5. Set identifying properties.
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // 6. Save the document.
            string outputPath = Path.Combine(
                Environment.CurrentDirectory,
                "CommandButtonDemo.docx");
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

**Várt kimenet**  

A program futtatása egy hasonló útvonalat ír ki:  

```
Document saved to: C:\Path\To\WordButtonDemo\CommandButtonDemo.docx
```  

A generált *CommandButtonDemo.docx* megnyitása egyetlen **Submit** gombot mutat, amely a kódban definiált koordinátákon helyezkedik el. Nem jelennek meg további UI elemek, ami megerősíti, hogy a **parancsgomb programozott hozzáadása** munkafolyamat sikeres volt.  

## Összegzés  

Most már tudja, hogyan **programozottan adhat hozzá egy parancsgombot** egy Word dokumentumhoz az Aspose.Words segítségével, és azt is, hogyan **hozzon létre Word dokumentumban gombot**, amely később VBA makrókhoz vagy külső automatizációs eszközökhöz csatlakoztatható. A folyamat egy dokumentum inicializálásából, egy OLE `CommandButton` vezérlő beillesztéséből, a tulajdonságok konfigurálásából és a fájl mentéséből áll.  

Innen tovább:  

* További vezérlők (jelölőnégyzetek, szövegmezők) hozzáadása a 3. lépés ismétlésével különböző `ControlType` értékekkel.  
* VBA makrók csatolása a gombhoz, hogy például űrlap mentése vagy e‑mail küldése történjen.  
* Teljes űrlapok dinamikus generálása adat‑vezérelt meződefiníciók gyűjteményén való iterálással.  

Kísérletezzen a téglalap koordinátáival és a gomb feliratával, hogy illeszkedjen a UI‑tervhez. Boldog kódolást!  


## Mit érdemes még megtanulni?  


Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészletet tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API‑funkciókat és alternatív megvalósítási megközelítéseket saját projektjeiben.

- [Combo Box űrlapmező hozzáadása Word dokumentumhoz Aspose.Words for .NET‑el](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Check Box űrlapmező hozzáadása Word dokumentumhoz Aspose.Words for .NET‑el](/words/english/net/add-content-using-documentbuilder/insert-check-box/)
- [Üres Word dokumentum létrehozása Aspose.Words‑szel – Lépés‑ről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}