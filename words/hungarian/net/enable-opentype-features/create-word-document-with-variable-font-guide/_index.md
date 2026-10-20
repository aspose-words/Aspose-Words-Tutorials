---
category: general
date: 2026-03-19
description: Word dokumentum létrehozása Aspose.Words és egy változó betűtípus használatával.
  Tanulja meg, hogyan változtassa meg a betűvastagságot, állítsa be a betűszélességet,
  és határozza meg a betűvariációt C#‑ban.
draft: false
keywords:
- create word document
- change font weight
- set font width
- load variable font
- define font variation
language: hu
og_description: Készítsen Word-dokumentumot változó betűtípussal az Aspose.Words segítségével.
  Ez az útmutató megmutatja, hogyan töltheti be a betűtípust, módosíthatja a betűvastagságot,
  beállíthatja a betűszélességet, és definiálhatja a betűvariációt.
og_title: Word-dokumentum létrehozása változó betűtípussal – Teljes útmutató
tags:
- Aspose.Words
- C#
- Variable Font
title: Word-dokumentum létrehozása változó betűtípussal – Útmutató
url: /hu/net/enable-opentype-features/create-word-document-with-variable-font-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word dokumentum létrehozása változó betűtípussal – Útmutató

Valaha szükséged volt már **word dokumentum** létrehozására, amely modern változó betűtípust használ, de nem tudtad, hol kezdj? Nem vagy egyedül. Sok projektben—gondolj a dinamikus jelentésekre vagy a márkahű brosúrákra—az, hogy **betűvastagságot** tudj valós időben változtatni, igazi áttörés.

Ebben az útmutatóban végigvezetünk a teljes folyamaton: a változó betűtípus betöltésétől az Aspose.Words-be, a súly és a szélesség beállításáig, majd a pontosan úgy kinéző DOCX mentéséig, ahogy megtervezted. Nincs homályos hivatkozás, csak konkrét kód, amelyet azonnal beilleszthetsz a C# projektedbe.

## Amit megtanulsz

- Hogyan **tölts be változó betűtípus** fájlokat az Aspose.Words `FontSettings` segítségével.
- A **betűtípus variáció** tengelyek, például a `wght` (súly) és a `wdth` (szélesség) szintaxisa.
- Hogyan **állítsd be a betűtípus szélességét** és **változtasd meg a betűvastagságot** egyetlen `Run`-on.
- Tippek a gyakori hibák (hiányzó glifek, helytelen mappák stb.) elhárításához.
- Egy teljes, futtatható példa, amelyet másolhatsz‑beilleszthetsz és azonnal tesztelhetsz.

> **Előfeltételek**: .NET 6+ (vagy .NET Framework 4.6+), Aspose.Words for .NET telepítve NuGet‑en keresztül, valamint egy változó‑betűtípus fájl, például *RobotoFlex.ttf* egy helyi *Fonts* mappában.

---

## 1. lépés – A változó betűtípus betöltése az Aspose.Words-be

Először meg kell mondanunk az Aspose.Words‑nek, hol keresse az egyedi betűtípusainkat. Erre a `FontSettings` osztály szolgál.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Configure Aspose.Words to use the folder that contains the variable font
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);

// Apply the settings globally (optional but convenient)
FontSettings.DefaultInstance = fontSettings;
```

**Miért fontos**: A mappa regisztrálása nélkül az Aspose.Words a rendszer betűtípusaira támaszkodik, és figyelmen kívül hagyja az OpenType variációs adatokat, amelyeket később alkalmazni szeretnél. Egy konkrét könyvtár megadása garantálja, hogy a *RobotoFlex* (vagy bármely más változó betűtípus) minden futtatáskor megtalálható legyen.

> **Pro tipp**: Állítsd a `SetFontsFolder` második paraméterét `true`‑ra, ha azt szeretnéd, hogy az Aspose az alkönyvtárakat is átvizsgálja. Ez akkor hasznos, ha a betűtípusokat stílus vagy súly szerint rendezve tárolod.

---

## 2. lépés – Új dokumentum létrehozása és minta szöveg hozzáadása

Miután a betűtípus‑motor tudja, hol keressen, létrehozunk egy üres `Document`‑et, és egy bekezdést szúrunk be egy `Run`‑nal.

```csharp
// Create a fresh, empty document
Document document = new Document();

// Add a new paragraph to the first section
Paragraph paragraph = new Paragraph(document);
Run variableRun = new Run(document, "Variable‑weight text");

// Attach the run to the paragraph, then the paragraph to the document body
paragraph.AppendChild(variableRun);
document.FirstSection.Body.AppendChild(paragraph);
```

**Mi történik**: A `Run` egy egységes formázású szövegrészt képvisel. Először létrehozva a formázási logikát elkülönítjük—tökéletes alap a későbbi különböző variációs tengelyek külön‑külön `Run`‑okra való alkalmazásához, ha szükséges.

---

## 3. lépés – A kívánt variációs tengelyek definiálása (Súly & Szélesség)

A változó betűtípusok *tengelyeket* (axes) kínálnak, amelyeket futásidőben állíthatsz. A két leggyakoribb a `wght` (betűvastagság) és a `wdth` (betűszélesség). Az Aspose.Words ezt az `OpenTypeFontVariation` gyűjteménnyel modellezi.

```csharp
// Build a collection of variation axes
OpenTypeFontVariation variationAxes = new OpenTypeFontVariation
{
    // Change the weight to 700 (roughly Bold) and width to 100 (normal width)
    { "wght", 700 },
    { "wdth", 100 }
};
```

**Miért ezek a számok**: Az OpenType specifikáció szerint a `wght` a betűtípus minimum és maximum súlyai között mozog (gyakran 100–900). A **700** érték félkövér megjelenést eredményez. A `wdth` hasonlóan működik; a **100** az alap (normál) szélesség, míg az 100 alatti értékek a glifeket összenyomják.

> **Szélsőséges eset**: Egyes változó betűtípusok nem támogatnak bizonyos tengelyeket. Ha egy nem támogatott címkét adsz meg, az Aspose csendben figyelmen kívül hagyja. Mindig ellenőrizd a betűtípus specifikációját (általában a `.ttf` vagy `.otf` fájl metaadataiban található).

---

## 4. lépés – A variáció alkalmazása a Run‑ra a betűtípus neve alapján

Most a variációs adatot a tényleges szöveghez kötjük. A `FontInfo` osztály tárolja a betűcsalád nevét és a tengelygyűjteményt.

```csharp
// Assign the variable font and its axes to the run's FontInfo
variableRun.Font.FontInfo = new FontInfo("RobotoFlex", variationAxes);
```

**Magyarázat**: A `FontInfo` beállításával megkerülöd a szokásos `Font.Name` tulajdonságot, és a motor számára egy teljesen meghatározott betűtípus‑konfigurációt adsz át. Ez az egyetlen módja annak, hogy az Aspose.Words egy változó betűtípust használjon egyedi tengelyekkel.

> **Gyakori hiba**: A betűtípusfájlban szereplő pontos családnevet (`RobotoFlex` ebben a példában) nem egyezik meg. Egy elütés miatt az Aspose alapértelmezett betűtípusra vált, és a variáció elveszik.

---

## 5. lépés – Dokumentum mentése és az eredmény ellenőrzése

Végül írjuk a dokumentumot a lemezre. A generált DOCX tartalmazni fogja a változó‑betűtípus utasításokat, amelyeket a Microsoft Word (2016+) helyesen megjelenít.

```csharp
// Save the document; Word will render the variable font with the specified weight and width
document.Save(@"C:\MyProject\Output\VariableFont.docx");
```

Nyisd meg a létrehozott fájlt Word‑ben, jelöld ki a szöveget, és nézd meg a **Betűtípus** párbeszédpanelt. Látnod kell a *Roboto Flex* betűtípust, és a szöveg vastagabb lesz a környező tartalomnál—pontosan úgy, ahogy a `wght = 700` beállításunk kérte.

> **Ellenőrzési tipp**: Ha a szöveg változatlanul marad, ellenőrizd, hogy a betűtípusfájl valóban támogatja‑e a `wght` tengelyt. Néhány “változó” betűtípus csak `ital` (dőlt) vagy `opsz` (optikai méret) tengelyt kínál.

---

## Opcionális: További variáció – Szélesség dinamikus változtatása

Ha egy másik bekezdésnél *a betűszélességet* szeretnéd másként beállítani, egyszerűen ismételd meg a 3‑4. lépéseket egy új `OpenTypeFontVariation` gyűjteménnyel.

```csharp
// Example: widen the text to 115% (condensed vs expanded)
OpenTypeFontVariation wideAxes = new OpenTypeFontVariation
{
    { "wght", 500 },   // regular weight
    { "wdth", 115 }    // slightly expanded width
};

Run wideRun = new Run(document, "Expanded width text");
wideRun.Font.FontInfo = new FontInfo("RobotoFlex", wideAxes);
Paragraph wideParagraph = new Paragraph(document);
wideParagraph.AppendChild(wideRun);
document.FirstSection.Body.AppendChild(wideParagraph);
```

Most két `Run`‑od van—az egyik félkövér, a másik valamivel szélesebb—bemutatva a **betűvastagság változtatását** és a **betűszélesség beállítását** ugyanabban a dokumentumban.

---

## Teljes működő példa

Másold az alábbi kódrészletet egy új konzolalkalmazásba (`Program.cs`) és futtasd. Győződj meg róla, hogy a `Fonts` mappa tartalmazza a `RobotoFlex.ttf`‑t (vagy bármely más általad preferált változó betűtípust).

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the variable font
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);
        FontSettings.DefaultInstance = fontSettings;

        // 2️⃣ Create a document and a run
        Document doc = new Document();
        Paragraph para = new Paragraph(doc);
        Run run = new Run(doc, "Variable‑weight text");
        para.AppendChild(run);
        doc.FirstSection.Body.AppendChild(para);

        // 3️⃣ Define variation axes (weight = 700, width = 100)
        OpenTypeFontVariation axes = new OpenTypeFontVariation
        {
            { "wght", 700 },
            { "wdth", 100 }
        };

        // 4️⃣ Apply the variation using the font name
        run.Font.FontInfo = new FontInfo("RobotoFlex", axes);

        // 5️⃣ Save the result
        doc.Save(@"C:\MyProject\Output\VariableFont.docx");
    }
}
```

**Várt eredmény**: Egy `VariableFont.docx` fájl, ahol a „Variable‑weight text” kifejezés félkövérként jelenik meg a `wght = 700` tengelynek köszönhetően, miközben az alap szélességet megtartja.

---

## Gyakran Ismételt Kérdések & Szélsőséges Esetek

| Kérdés | Válasz |
|----------|--------|
| *Mi van, ha a betűtípus nem található?* | Ellenőrizd a mappa útvonalát, győződj meg a fájlnév helyességéről, és arról, hogy a folyamatnak olvasási jogosultsága van. Hívhatod a `fontSettings.GetFonts()`‑t is a felismert betűtípusok listázásához. |
| *Kombinálhatok több `Run`‑t különböző variációkkal?* | Természetesen. Minden `Run` saját `FontInfo`‑val rendelkezhet. Csak ismételd meg a 3‑4. lépéseket minden egyes `Run`‑ra. |
| *Támogatják-e a régebbi Word‑verziók a változó betűtípusokat?* | A Word 2016 (Build 16.0.8001) vezette be az alapvető támogatást. Régebbi verziók esetén a dokumentum a legközelebbi statikus betűtípus‑példányra fog visszaesni. |
| *Van korlátozás a beállítható tengelyek számában?* | Bármennyi tengelyt beállíthatsz, amit a betűtípus definiál. Gyakori címkék: `wght`, `wdth`, `ital`, `opsz`, `GRAD`. Egy nem támogatott címke egyszerűen hatástalan. |
| *Hogyan debug-oljam a hiányzó glifeket?* | Használd a `FontSettings.GetFontSources()`‑t a betöltött betűtípusok ellenőrzéséhez, és a `FontInfo.HasGlyph(char)`‑t az egyes karakterek teszteléséhez. |

---

## Összegzés

Néhány lépésben bemutattuk, **hogyan hozhatsz létre Word dokumentumot**, amely a változó betűtípusok erejét használja, lehetővé téve a **betűvastagság változtatását**, a **betűszélesség beállítását**, a **változó betűtípus** fájlok betöltését és a **betűtípus variáció** tengelyek definiálását—mindezt az Aspose.Words for .NET segítségével.

A lényeg egyszerű: regisztráld a betűtípus‑mappát, írd le a kívánt tengelyeket, csatold őket egy `Run`‑hoz, és mentsd el. Innen már kiterjesztheted a technikát egész szakaszokra, táblázatokra, vagy akár programozottan generált, márkára szabott jelentésekre.

**Következő lépések**: próbáld ki a `RobotoFlex` helyett egy másik változó betűtípust, kísérletezz az `ital` (dőlt) tengellyel, vagy generálj PDF‑et ugyanabból a dokumentumból az Aspose.PDF‑vel. Ugyanaz a minta: betöltés, definiálás, alkalmazás, mentés.

Boldog kódolást, és élvezd a változó betűtípusok nyújtotta rugalmasságot a Word automatizálási projektjeidben!  

<img src="variable-font-demo.png" alt="Create word document with variable font example">

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}