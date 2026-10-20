---
category: general
date: 2026-08-04
description: Lábjegyzet-elválasztó módosítása C#-ban az Aspose.Words használatával
  – tanulja meg, hogyan szerkessze a lábjegyzet-elválasztót és változtassa meg a végjegyzet-elválasztót
  Word dokumentumokban.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote separator
- edit footnote separator
- how to change footnote separator
- change endnote separator
language: hu
lastmod: 2026-08-04
og_description: Lábjegyzet-elválasztó módosítása C#-ban az Aspose.Words segítségével.
  Ez az útmutató megmutatja, hogyan szerkesztheti a lábjegyzet-elválasztót, testreszabhatja
  a végjegyzet-elválasztót, és mentheti a frissített dokumentumot.
og_image_alt: Screenshot showing the changed footnote separator in a Word document
og_title: Lábjegyzet elválasztó módosítása C#-ban – teljes Aspose.Words útmutató
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Change footnote separator in C# using Aspose.Words – learn how to edit
    footnote separator and change endnote separator in Word documents.
  headline: Change footnote separator in C# using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
- Document processing
title: A lábjegyzet elválasztó módosítása C#-ban az Aspose.Words használatával
url: /hu/net/working-with-footnote-and-endnote/change-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lábjegyzet elválasztó módosítása C#-ban az Aspose.Words használatával

Ha **change footnote separator**-t kell módosítania egy Word dokumentumban, ez az útmutató pontos lépéseken keresztül vezet el az Aspose.Words for .NET segítségével. Akár az alapértelmezett vonalat szeretné egy szimbólummal helyettesíteni, akár más stílust alkalmazna az végjegyzet elválasztókra, az alábbi kód lefedi a teljes munkafolyamatot.

Megtanulja, hogyan **edit footnote separator**-t és a kapcsolódó **change endnote separator** műveletet, így ugyanabban a dokumentumban konzisztens megjelenést érhet el a lábjegyzetek és végjegyzetek számára is. Nincs szükség külső eszközökre – csak néhány C# sorra.

## Mit fog elérni

* Töltsön be egy meglévő *.docx* fájlt, amely lábjegyzeteket és végjegyzeteket tartalmaz.  
* Érje el a lábjegyzetek, lábjegyzet folytatások és végjegyzetek elválasztó csomópontjait.  
* Cserélje le az elválasztó karaktert (például változtassa meg az alapértelmezett vonalat csillagra).  
* Mentse el a módosított dokumentumot anélkül, hogy bármilyen egyéb tartalmat elveszítene.  

Az útmutató feltételezi, hogy alapvető C# ismeretekkel rendelkezik, és telepítette a **Aspose.Words** NuGet csomagot (24.9 vagy újabb verzió).  

---

## Előkövetelmények

| Követelmény | Indoklás |
|-------------|----------|
| .NET 6.0+ vagy .NET Framework 4.7.2+ | Az Aspose.Words számára szükséges futtatókörnyezet |
| Aspose.Words for .NET library | Biztosítja a `Document` és `FootnoteOptions` API-kat |
| Bemeneti Word fájl (`input.docx`) legalább egy lábjegyzet vagy végjegyzet tartalmával | Bemutatja az elválasztó módosítását |

Az Aspose.Words hozzáadható a projekthez a következő CLI parancs segítségével:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

---

## 1. lépés: A lábjegyzeteket tartalmazó dokumentum betöltése

Az első művelet a forrásfájl beolvasása egy `Document` objektumba. Ez az objektum a teljes Word fájlt memóriában képviseli, és hozzáférést biztosít az összes csomópontjához.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Load the .docx file that contains footnotes and endnotes.
Document document = new Document(@"C:\Docs\input.docx");
```

**Miért fontos:** A dokumentum betöltése minden manipuláció kiindulópontja. Ha a fájl nem található, az Aspose.Words `FileNotFoundException`-t dob, ezért a folytatás előtt ellenőrizze, hogy az útvonal helyes-e.

---

## 2. lépés: A lábjegyzet és végjegyzet elválasztó csomópontjainak elérése

`Document.FootnoteOptions` három elválasztó csomópontot tesz elérhetővé:

* `Separator` – az a vonal, amely az első oldalon a lábjegyzet gyűjtemény után jelenik meg.  
* `ContinuationSeparator` – a vonal, amelyet akkor használnak, amikor a lábjegyzetek a következő oldalra folytatódnak.  
* `EndnoteSeparator` – a vonal, amely elválasztja a fő szöveget a végjegyzet listától.

Ezeket a csomópontokat általános `Node` objektumként kérheti le, majd `Run`-ra konvertálja a szöveg módosításához.

```csharp
// Retrieve the three separator nodes.
Node footnoteSeparator = document.FootnoteOptions.Separator;
Node footnoteContinuation = document.FootnoteOptions.ContinuationSeparator;
Node endnoteSeparator = document.FootnoteOptions.EndnoteSeparator;
```

**Miért fontos:** Ezek a csomópontok az egyetlen helyek, ahol a vizuális elválasztó karakter tárolódik. Bármely más csomópont (például egy normál bekezdés) módosítása nem befolyásolja a lábjegyzet formázását.

---

## 3. lépés: A lábjegyzet elválasztó karakterének módosítása

A leggyakoribb igény az alapértelmezett vonal cseréje egy szimbólumra, például egy csillagra (`*`). Mivel az elválasztó `Run`-ként van tárolva, biztonságosan módosíthatja a `Text` tulajdonságát.

```csharp
// Change the primary footnote separator to an asterisk.
if (footnoteSeparator is Run footnoteRun)
{
    footnoteRun.Text = "*";
}

// Optionally, change the continuation separator as well.
if (footnoteContinuation is Run continuationRun)
{
    continuationRun.Text = "*";
}
```

**Miért fontos:** A `Run.Text` közvetlen szerkesztése frissíti a vizuális megjelenést a végső dokumentumban anélkül, hogy a többi lábjegyzet tartalmát befolyásolná. Ugyanez a minta bármilyen karakterlánc alkalmazására használható, beleértve az Unicode szimbólumokat is.

---

## 4. lépés: A végjegyzet elválasztó módosítása (opcionális)

Ha Önnek is szüksége van a **change endnote separator**-re, a folyamat a lábjegyzet módosításához hasonló. Cserélje le az `endnoteSeparator` szövegét a kívánt karakterre.

```csharp
// Change the endnote separator to a dash.
if (endnoteSeparator is Run endnoteRun)
{
    endnoteRun.Text = "-";
}
```

**Miért fontos:** A végjegyzetek gyakran más stílusúak, mint a lábjegyzetek. Külön elválasztó biztosítása lehetővé teszi a vizuális konzisztencia fenntartását a dokumentum tervezési irányelveivel.

---

## 5. lépés: A módosított dokumentum mentése

A módosítások után mentse el a változásokat a `Document.Save` segítségével. Felülírhatja az eredeti fájlt, vagy egy új helyre írhatja.

```csharp
// Save the updated document.
document.Save(@"C:\Docs\ModifiedSeparators.docx");
```

**Miért fontos:** A `Save` a memóriában lévő reprezentációt lemezre írja, megőrizve minden egyéb elemet (stílusok, képek, táblázatok) változatlanul.

---

## Teljes, futtatható példa

Az összes elemet egyesítve, itt egy önálló konzolalkalmazás, amely bemutatja a teljes munkafolyamatot:

```csharp
using System;
using Aspose.Words;

namespace FootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document.
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Access separator nodes.
            Node footnoteSep = doc.FootnoteOptions.Separator;
            Node footnoteCont = doc.FootnoteOptions.ContinuationSeparator;
            Node endnoteSep = doc.FootnoteOptions.EndnoteSeparator;

            // 3️⃣ Change footnote separator to an asterisk.
            if (footnoteSep is Run footnoteRun)
                footnoteRun.Text = "*";

            // Optional: also change the continuation separator.
            if (footnoteCont is Run contRun)
                contRun.Text = "*";

            // 4️⃣ Change endnote separator to a dash.
            if (endnoteSep is Run endnoteRun)
                endnoteRun.Text = "-";

            // 5️⃣ Save the result.
            string outputPath = @"C:\Docs\ModifiedSeparators.docx";
            doc.Save(outputPath);

            Console.WriteLine("Document saved to " + outputPath);
        }
    }
}
```

**Expected result:** Nyissa meg a *ModifiedSeparators.docx* fájlt a Microsoft Wordben. A lábjegyzet elválasztó vonala az első lábjegyzet oldal alján most egyetlen csillag (`*`) lesz. Ha a dokumentum tartalmaz végjegyzeteket, a fő szöveget a végjegyzet listától elválasztó vonal egy kötőjel (`-`) lesz. Minden egyéb tartalom (szöveg, képek, táblázatok) érintetlen marad.

---

## Gyakori kérdések és szél‑eset kezelése

| Kérdés | Válasz |
|----------|--------|
| **Mi a teendő, ha a dokumentumnak nincs lábjegyzete?** | `FootnoteOptions.Separator` továbbra is egy `Run` csomópontot ad vissza, de a szövege üres lehet. A kód biztonságosan ellenőrzi a csomópont típusát a módosítás előtt. |
| **Használhatok többkarakteres karakterláncot (pl. "***")?** | Igen. A `Run.Text` tulajdonság bármilyen karakterláncot elfogad, beleértve az Unicode karaktereket is. |
| **A separator módosítása befolyásolja a meglévő lábjegyzet számozást?** | Nem. Az elválasztó független a számozási sémától. |
| **Szükséges-e felszabadítani a `Document` objektumot?** | `Document` implémentálja az `IDisposable`-t közvetve a `Node`-on keresztül. Egy rövid életű konzolalkalmazásban ez opcionális, de hosszú futású szolgáltatások esetén `using` blokkba tehető. |
| **Hogyan működik ez .NET Core és .NET Framework esetén?** | Az API minden futtatókörnyezetben azonos; csak a célkeretrendszer verziója számít (nek támogatnia kell az Aspose.Words csomagot). |

**Pro tipp:** Ha különböző elválasztókat kell alkalmaznia különböző szakaszokban, iterálhat a `doc.GetChildNodes(NodeType.Footnote, true)`-en, és egyenként módosíthatja minden lábjegyzet `Separator` tulajdonságát. Ez haladóbb, de hasznos összetett dokumentumok esetén.

---

## Összegzés

Most már tudja, hogyan **change footnote separator**-t és **change endnote separator**-t módosítson egy Word fájlban az Aspose.Words for C# használatával. Az útmutató lefedte a dokumentum betöltését, a megfelelő elválasztó csomópontok elérését, a szöveg módosítását és az eredmény mentését – mindezt egyetlen, önálló programban.

Innen tovább felfedezheti a kapcsolódó témákat, például a **edit footnote separator style** testreszabását, a lábjegyzet számozásának módosítását, vagy feltételes formázás alkalmazását az oldalelrendezés alapján. Ugyanez a minta (csomópont lekérése, `Run`-ra konvertálás, `Text` módosítása) sok más Word‑feldolgozási helyzetben is működik.

Boldog kódolást, és nyugodtan kísérletezzen különböző szimbólumokkal vagy akár képek beágyazásával elválasztóként egy igazán egyedi dokumentumelrendezéshez!

## Mit érdemes következőként megtanulni?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket saját projektjeiben.

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Get Paragraph Style Separator In Word Document](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Insert Document Style Separator in Word](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}