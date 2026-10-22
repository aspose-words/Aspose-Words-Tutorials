---
category: general
date: 2026-08-10
description: Formázza a lábjegyzet-elválasztót C#-ban az Aspose.Words segítségével,
  hogy testreszabja a lábjegyzet- és végjegyzetvonalakat. Tanulja meg a C# lábjegyzetformázást
  percek alatt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- format footnote separator
- Aspose.Words footnote separator
- C# footnote formatting
- modify footnote separator
- style footnote separator
- endnote separator formatting
language: hu
lastmod: 2026-08-10
og_description: Formázza a lábjegyzet-elválasztót C#-ban az Aspose.Words segítségével.
  Kövesse ezt az útmutatót a lábjegyzet- és végjegyzet-elválasztók gyors és megbízható
  formázásához.
og_image_alt: Code editor showing C# snippet that styles a footnote separator
og_title: Lábjegyzet elválasztó formázása C#‑ban – teljes Aspose.Words útmutató
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  headline: Format footnote separator in C# using Aspose.Words
  type: TechArticle
- description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  name: Format footnote separator in C# using Aspose.Words
  steps:
  - name: Styling the continuation separator (optional)
    text: 'The continuation separator appears when a footnote spans multiple pages.
      You can style it similarly:'
  - name: Formatting the endnote separator
    text: 'If your document also uses endnotes, you can apply the same logic to the
      `Endnotes` collection:'
  - name: Using a custom string for the separator
    text: 'Sometimes you want the separator to be a series of asterisks (`***`). Replace
      the existing runs with a new run:'
  - name: Handling documents without a separator node
    text: 'A rare edge case is a document that omits the separator node (e.g., when
      the author deleted it). In that scenario `document.Footnotes.Separator` returns
      `null`. Guard against it:'
  type: HowTo
tags:
- Aspose.Words
- C#
- footnotes
- document‑processing
title: Lábjegyzet-elválasztó formázása C#-ban az Aspose.Words segítségével
url: /hu/net/working-with-footnote-and-endnote/format-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formázza a lábjegyzet elválasztót C#-ban az Aspose.Words használatával

Ha **lábjegyzet elválasztót** kell formáznia egy Word dokumentumban, ez az útmutató megmutatja, hogyan teheti ezt meg az Aspose.Words for .NET segítségével. Egy teljes, futtatható példát fog látni, amely megváltoztatja az elválasztó bekezdés igazítását és színét, és megtanulja, hogyan alkalmazza ugyanazt a technikát a végjegyzet elválasztókra is.

Az oktatóanyag minden lépést lefed – a forrásfájl betöltésétől a módosított dokumentum mentéséig – így a kódot egyszerűen átmásolhatja a saját projektjébe további kutatás nélkül.

## Amire szüksége lesz

* .NET 6.0 vagy újabb (a kód .NET Framework 4.6+‑vel is működik)
* Érvényes Aspose.Words for .NET licenc (az ingyenes próba verzió értékelésre elegendő)
* Egy Word fájl, amely legalább egy lábjegyzetet vagy végjegyzetet tartalmaz (pl. `Footnotes.docx`)
* Visual Studio 2022 vagy bármely kedvelt C# IDE

Ezeknek az elemeknek a rendelkezésre állása lehetővé teszi, hogy a **C# lábjegyzet formázás** logikára koncentráljon a környezet beállítása helyett.

## 1. lépés: A lábjegyzeteket és végjegyzeteket tartalmazó dokumentum betöltése

Az első művelet egy `Document` objektum létrehozása, amely a forrásfájlra mutat. Az Aspose.Words beolvassa a teljes DOCX csomagot a memóriába, így teljes hozzáférést kap a lábjegyzet‑ és végjegyzet‑csomópontokhoz.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;

// Load the source DOCX file
Document document = new Document(@"C:\Docs\Footnotes.docx");
```

*Miért fontos*: A dokumentum betöltése előfeltétele minden további manipulációnak. Ha a fájl útvonala hibás, az Aspose.Words `FileNotFoundException`‑t dob, ezért ellenőrizze az útvonalat a folytatás előtt.

## 2. lépés: Az elválasztó és a folytatás‑elválasztó csomópontok lekérése

A lábjegyzet‑ és végjegyzet‑elválasztók speciális csomópontokként tárolódnak a `Footnotes` és `Endnotes` gyűjteményekben. Minden gyűjtemény `Separator` és `ContinuationSeparator` tulajdonságot biztosít, amely egy `Node` referenciát ad vissza.

```csharp
// Footnote separator nodes
Node footnoteSeparator          = document.Footnotes.Separator;
Node footnoteContinuationSep    = document.Footnotes.ContinuationSeparator;

// Endnote separator nodes
Node endnoteSeparator           = document.Endnotes.Separator;
Node endnoteContinuationSep     = document.Endnotes.ContinuationSeparator;
```

*Miért fontos*: A `Separator` csomópont a vizuális vonalat jelenti, amely elválasztja a fő szöveget a lábjegyzetblokkól. Ha megszerzi a referenciát, módosíthatja a bekezdés formátumát, betűtípusát, vagy akár teljesen kicserélheti a csomópontot.

## 3. lépés: A lábjegyzet elválasztó vizuális stílusának módosítása

A legtöbb Word dokumentumban az elválasztó egyetlen bekezdés, amely egy kötőjelet vagy csillagot tartalmaz. Az alábbi kód ellenőrzi, hogy az elválasztó `Paragraph`‑e, és ha igen, középre igazítja, valamint szürke színűre állítja a szöveget.

```csharp
// Ensure the separator is a Paragraph before casting
if (footnoteSeparator is Paragraph separatorParagraph)
{
    // Center the separator paragraph
    separatorParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;

    // Set the separator text color to gray
    if (separatorParagraph.Runs.Count > 0)
    {
        separatorParagraph.Runs[0].Font.Color = Color.Gray;
    }
}
```

### A folytatás elválasztó stílusának beállítása (opcionális)

A folytatás‑elválasztó akkor jelenik meg, amikor egy lábjegyzet több oldalon átível. Hasonlóan formázható:

```csharp
if (footnoteContinuationSep is Paragraph contParagraph)
{
    contParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (contParagraph.Runs.Count > 0)
        contParagraph.Runs[0].Font.Color = Color.DarkGray;
}
```

*Miért fontos*: Az elválasztó igazítása javítja az olvashatóságot, a szín módosítása pedig megkülönbözteti a normál bekezdésszövegtől. A `ParagraphAlignment.Center`‑t helyettesítheti `Left`‑nel vagy `Right`‑nal a dokumentum tervezési irányelveinek megfelelően.

## 4. lépés: A módosított dokumentum mentése

A kívánt stílus alkalmazása után írja vissza a dokumentumot a lemezre. Felülírhatja az eredeti fájlt, vagy létrehozhat egy új verziót.

```csharp
// Save the document with the modified separator
document.Save(@"C:\Docs\Footnotes_Styled.docx");
```

Amikor megnyitja a `Footnotes_Styled.docx` fájlt a Microsoft Wordben, a lábjegyzet elválasztó középre igazított és szürke lesz, pontosan úgy, ahogy a kód meghatározta.

## Haladó variációk

### A végjegyzet elválasztó formázása

Ha a dokumentuma végjegyzeteket is tartalmaz, ugyanazt a logikát alkalmazhatja az `Endnotes` gyűjteményre:

```csharp
if (endnoteSeparator is Paragraph endSepParagraph)
{
    endSepParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (endSepParagraph.Runs.Count > 0)
        endSepParagraph.Runs[0].Font.Color = Color.SlateGray;
}
```

### Egyedi karakterlánc használata az elválasztóhoz

Előfordulhat, hogy az elválasztó egy csillagokból álló sorozat (`***`) legyen. Cserélje le a meglévő futásokat egy új `Run`‑ra:

```csharp
if (footnoteSeparator is Paragraph sepPara)
{
    // Clear existing content
    sepPara.Runs.Clear();

    // Add a custom separator string
    Run newRun = new Run(document, "***");
    newRun.Font.Color = Color.Gray;
    sepPara.Runs.Add(newRun);
}
```

### Dokumentumok kezelése elválasztó csomópont nélkül

Ritka eset, amikor a dokumentum nem tartalmaz elválasztó csomópontot (pl. a szerző törölte). Ebben az esetben a `document.Footnotes.Separator` `null`‑t ad vissza. Védekezzen ellene:

```csharp
if (footnoteSeparator != null && footnoteSeparator is Paragraph sepPara)
{
    // Apply styling as shown earlier
}
else
{
    // Optionally create a new separator paragraph
    Paragraph newSep = new Paragraph(document);
    newSep.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    Run run = new Run(document, "-");
    run.Font.Color = Color.Gray;
    newSep.Runs.Add(run);
    document.Footnotes.InsertAfter(newSep, document.Footnotes.LastParagraph);
}
```

## Gyakori buktatók és elkerülésük módja

| Probléma | Miért fordul elő | Megoldás |
|----------|-------------------|----------|
| **Az elválasztó nem `Paragraph`** | Egyes Word sablonok `Table`‑t vagy `Shape`‑t használnak elválasztóként. | Ellenőrizze a csomópont típusát `is Paragraph`‑val, mielőtt átkonvertálná. |
| **A `Runs` gyűjtemény üres** | Az elválasztó lehet egy üres bekezdés. | Győződjön meg róla, hogy `Runs.Count > 0` legyen, mielőtt a `Runs[0]`‑hoz hozzáférne. |
| **Licenc nincs alkalmazva** | Licenc nélkül az Aspose.Words vízjelet helyez el, és korlátozhatja az API használatát. | Hívja meg a `License license = new License(); license.SetLicense("Aspose.Words.lic");` kódrészt a program elején. |
| **Mentés írásvédett mappába** | A `Save` metódus `UnauthorizedAccessException`‑t dob. | Biztosítsa, hogy a célkönyvtár rendelkezzen írási jogosultsággal. |

Ezeknek a kérdéseknek a korai kezelése megakadályozza a futásidejű kivételeket, és biztosítja a zökkenőmentes **lábjegyzet elválasztó módosítása** élményt.

## Teljes, futtatható példa

Az alábbi önálló konzolalkalmazás bemutatja a fent tárgyalt minden lépést. Másolja a kódot egy új .NET konzolprojektbe, cserélje ki a fájl útvonalakat, és futtassa.

```csharp
using Aspose.Words;
using System;
using System.Drawing;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // OPTIONAL: Apply your Aspose.Words license
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1. Load the source document
            string inputPath = @"C:\Docs\Footnotes.docx";
            Document doc = new Document(inputPath);

            // 2. Retrieve separator nodes
            Node footnoteSeparator = doc.Footnotes.Separator;
            Node footnoteContinuationSep = doc.Footnotes.ContinuationSeparator;
            Node endnoteSeparator = doc.Endnotes.Separator;
            Node endnoteContinuationSep = doc.Endnotes.ContinuationSeparator;

            // 3. Style footnote separator
            if (footnoteSeparator is Paragraph footSepPara)
            {
                footSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footSepPara.Runs.Count > 0)
                    footSepPara.Runs[0].Font.Color = Color.Gray;
            }

            // 3a. (Optional) Style footnote continuation separator
            if (footnoteContinuationSep is Paragraph footContPara)
            {
                footContPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footContPara.Runs.Count > 0)
                    footContPara.Runs[0].Font.Color = Color.DarkGray;
            }

            // 4. Style endnote separator (optional)
            if (endnoteSeparator is Paragraph endSepPara)
            {
                endSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (endSepPara.Runs.Count > 0)
                    endSepPara.Runs[0].Font.Color = Color.SlateGray;
            }

            // 5. Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Styled.docx";
            doc.Save(outputPath);

            Console.WriteLine("Footnote separator formatted successfully.");
            Console.WriteLine($"Saved to: {outputPath}");
        }
    }
}
```

**Várható eredmény**  

Amikor megnyitja a `Footnotes_Styled.docx` fájlt:

* A lábjegyzet elválasztó vonala a fő szöveg alatt középre igazított.
* Színe világosszürke, így vizuálisan megkülönböztethető.
* Ha a dokumentum végjegyzeteket is tartalmaz, azok elválasztói szintén középre igazítottak és szürke (vagy pala) színűek lesznek.

## Mit érdemes még megtanulni?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódpéldákat és lépésről‑lépésre magyarázatokat tartalmaz, hogy elsajátíthassa a további API‑funkciókat, és alternatív megvalósítási megközelítéseket fedezzen fel saját projektjeiben.

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Set Footnote And Endnote Position](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Working With Footnote And Endnote](/words/german/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}