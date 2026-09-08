---
category: general
date: 2026-09-08
description: Hogyan mentse a docx-et ActiveX vezérlő beillesztése közben C#-ban. Kövesse
  ezt a lépésről‑lépésre útmutatót, hogy programozottan hozzáadjon egy parancsgombot.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save docx
- insert activex control
- add activex button
- create word document programmatically
- how to add command button
language: hu
lastmod: 2026-09-08
og_description: Hogyan menthetünk docx fájlt ActiveX vezérlő beszúrása közben C#-ban.
  Ez az útmutató lépésről lépésre végigvezet a programozott Word dokumentum létrehozásán,
  egy parancsgomb hozzáadásán és a fájl mentésén.
og_image_alt: How to save docx with an ActiveX command button displayed in the document
og_title: Hogyan mentse a docx fájlt és ágyazzon be egy ActiveX gombot C#-ban
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: How to save docx while inserting an ActiveX control in C#. Follow this
    step‑by‑step guide to add a command button programmatically.
  headline: How to save docx and insert an ActiveX button with C#
  type: TechArticle
tags:
- C#
- Word automation
- ActiveX
- Docx
title: Hogyan menthetünk docx-et és szúrhatunk be egy ActiveX gombot C#-ban
url: /hu/net/working-with-oleobjects-and-activex/how-to-save-docx-and-insert-an-activex-button-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan mentse el a docx-et és szúrjon be egy ActiveX gombot C#-ban

Ha programozott módon kell Word dokumentumot létrehoznia, majd docx-et menteni egy interaktív gombbal, ez az útmutató megmutatja, hogyan teheti meg. Megtanulja, hogyan szúrjon be egy ActiveX vezérlőt, adjon hozzá egy ActiveX gombot, és mentse el a kapott .docx fájlt C#-ban és az Aspose.Words könyvtárral.

Az útmutató minden szükséges lépést lefed a **word dokumentum programozott létrehozásához**, egy **parancsgomb** beágyazásához, és a fájl lemezen való tárolásához. Nem szükséges előzetes tapasztalat a COM objektumokkal, de alapvető C# ismeretekkel és telepített Visual Studio-val kell rendelkeznie.

## Előfeltételek

* .NET 6.0 SDK vagy újabb  
* Visual Studio 2022 (vagy bármely C# IDE)  
* Aspose.Words for .NET NuGet csomag (`Install-Package Aspose.Words`)  
* C# projektstruktúra megértése  

Ezek az elemek garantálják, hogy a kód fordítható és futtatható további konfiguráció nélkül.

## 1. lépés: Új C# konzolprojekt létrehozása

Hozzon létre egy konzolalkalmazást, amely a Word automatizálási logikát fogja tartalmazni.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

A fenti parancs létrehozza a **WordActiveXDemo** nevű mappát, hozzáadja az Aspose.Words hivatkozást, és előkészíti a projektet a fordításhoz.

## 2. lépés: Word dokumentum programozott létrehozása

Nyissa meg a generált `Program.cs` fájlt, és adja hozzá a szükséges `using` direktívákat.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;   // not used directly but required for some overloads
```

Most hozza létre egy üres `Document` objektum példányát. Ez az objektum a teljes Word fájlt reprezentálja a memóriában.

```csharp
// Step 2: Create a new blank document
Document document = new Document();
```

A `Document` osztály a belépési pont minden Word‑feldolgozási művelethez. Ebben a szakaszban a dokumentum nem tartalmaz oldalakat, de az Aspose.Words automatikusan létrehoz egy alapértelmezett szekciót, amikor tartalmat ad hozzá.

## 3. lépés: ActiveX vezérlő beszúrása – ActiveX gomb hozzáadása

A **Forms2OleControl** objektum lehetővé teszi, hogy egy ActiveX vezérlőt ágyazzon be egy Word bekezdésbe. A következő kód egy **CommandButton**-t szúr be 150 pt szélességgel és 30 pt magassággal.

```csharp
// Step 3: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX CommandButton control with the desired size
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

`InsertForms2OleControl` létrehozza a vezérlőt, és egy erősen típusos `Forms2OleControl` példányt ad vissza, amelyet tovább konfigurálhat. A metódus automatikusan hozzáad egy új bekezdést a vezérlő elhelyezéséhez, így nem kell manuálisan kezelnie a bekezdésobjektumokat.

## 4. lépés: A parancsgomb konfigurálása – hogyan adjon hozzá parancsgomb tulajdonságokat

Állítsa be a gomb **Name** és **Caption** tulajdonságait, hogy futásidőben azonosítható és felhasználóbarát legyen a felületen.

```csharp
// Step 4: Set the control's name and caption
commandButton.Name = "cmdSubmit";
commandButton.Caption = "Submit";
```

A `Name` attribútum hasznos, ha később a gomb kattintási eseményét VBA-val vagy Word makróval kezeli. A `Caption` a szöveg, amelyet a végfelhasználó a gomb felületén lát.

### Pro tipp
Ha a kattintás kezelését C#-ból szeretné automatizálni, ágyazzon be egy VBA makrót, amely a `cmdSubmit`-re hivatkozik. A Word felkéri a felhasználót, hogy engedélyezze a makrókat a dokumentum megnyitásakor, ami az ActiveX vezérlők standard biztonsági viselkedése.

## 5. lépés: Hogyan mentse el a docx-et

Miután a vezérlő a helyén van, mentse el a dokumentumot .docx fájlként. A `Save` metódus automatikusan a fájlkiterjesztés alapján választja ki a megfelelő formátumot.

```csharp
// Step 5: Save the document containing the CommandButton
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

A fájl mentése befejezi a **hogyan mentse el a docx-et** munkafolyamatot. A kapott fájl megnyitható a Microsoft Wordben, ahol az ActiveX gomb az első oldalon jelenik meg. Ha rákattint, a Word egy helyőrző üzenetet jelenít meg, hacsak nincs makró csatolva.

## 6. lépés: A program futtatása és az eredmény ellenőrzése

Fordítsa le és futtassa a konzolalkalmazást:

```bash
dotnet run
```

A program befejezése után nyissa meg a `C:\Temp\CommandButton.docx` fájlt a Microsoft Wordben:

* A dokumentum egyetlen oldalt tartalmaz, a teteje közelében egy **Submit** gombbal.  
* A gomb fölé húzva megjelenik a tooltip a `cmdSubmit` névvel.  
* Nem vesz el semmilyen tartalom, és a fájlméret hasonló egy standard üres .docx-hez.

Ha a gomb nem jelenik meg, ellenőrizze, hogy:

1. A Word **Trust Center** beállításai engedélyezik az ActiveX vezérlőket.  
2. A fájl `.docx` kiterjesztéssel lett mentve (nem `.doc`).  

## Szélsőséges esetek és gyakori variációk

| Helyzet | Javasolt módosítás |
|-----------|------------------------|
| Más gombméretre van szüksége | Módosítsa a szélesség és magasság argumentumokat az `InsertForms2OleControl`-ben. |
| A gombot egy adott oldalon szeretné | Használja a `builder.MoveToDocumentEnd();`-t az oldalak hozzáadása után, vagy szúrjon be egy oldaltörést a vezérlő előtt. |
| Támogatnia kell olyan környezeteket, ahol nincs Aspose.Words | Használja az Open XML SDK-t egy `w:object` elem beszúrásához, de a kód jelentősen összetettebbé válik. |
| Makró‑engedélyezett dokumentum szükséges | Mentse `.docm` kiterjesztéssel (`document.Save("MyDoc.docm");`) és ágyazzon be egy VBA modult, amely kezeli a `cmdSubmit_Click` eseményt. |

## Teljes forráskód

Az alábbiakban a teljes, önálló program található, amelyet átmásolhat a `Program.cs` fájlba, és módosítások nélkül (kivéve a kimeneti útvonalat) futtathat.

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
            // Create a new blank document
            Document document = new Document();

            // Initialize a DocumentBuilder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control with the desired size
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Set the control's name and caption
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // Save the document containing the CommandButton
            string outputPath = @"C:\Temp\CommandButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Várható kimenet a konzolon

```
Document saved to C:\Temp\CommandButton.docx
```

A fájl megnyitása Wordben egy **Submit** feliratú gombot jelenít meg. A gombra kattintva az alapértelmezett ActiveX viselkedés lép életbe (egy üzenetablak, amely jelzi, hogy nincs makró csatolva).

## Következtetés

Ez az útmutató bemutatta, hogyan **mentse el a docx-et** miközben **ActiveX vezérlőt** ágyaz be, konkrétan egy **add activex button**-t, amely parancsgombként működik. Most már tudja, hogyan **hozzon létre word dokumentumot programozott módon**, konfigurálja a gomb tulajdonságait, és tárolja a fájlt a végfelhasználói interakcióhoz.

Innen tovább felfedezheti:

* VBA makrók hozzáadása a `cmdSubmit_Click` kezeléséhez.  
* Egyéb ActiveX vezérlők, például jelölőnégyzetek vagy kombinált listák beszúrása.  
* Többoldalas dokumentumok generálása több interaktív elemmel.  

Kísérletezzen különböző vezérlőtípusokkal és elrendezési beállításokkal, hogy gazdag, interaktív Word sablonokat építsen, amelyek egyszerűsítik az üzleti folyamatait.

## Mit érdemes legközelebb megtanulni?

Az alábbi útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeiben.

- [Aspose.Words – Docx mentése txt-ként és Word egyenletek exportálása LaTeX‑ként – Teljes útmutató](/words/english/net/basic-conversions/save-docx-as-txt-complete-guide-to-export-word-equations-as/)
- [hogyan állítsuk helyre a docx-et – C# útmutató sérült Word fájlokhoz](/words/english/net/programming-with-loadoptions/how-to-recover-docx-c-guide-for-corrupted-word-files/)
- [Hogyan mentse a Word-öt Markdown‑ként – Teljes C# útmutató](/words/english/net/programming-with-markdownsaveoptions/how-to-save-word-as-markdown-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}