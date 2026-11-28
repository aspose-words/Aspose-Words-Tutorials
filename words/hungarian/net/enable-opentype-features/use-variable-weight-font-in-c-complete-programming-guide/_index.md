---
category: general
date: 2026-06-02
description: Tanulja meg, hogyan használjon változó súlyú betűtípust C#-ban, és állítsa
  be programozottan a betűsúlyt, miközben módosítja a betűnyújtás kódját a dinamikus
  tipográfiához.
draft: false
keywords:
- use variable weight font
- set font weight programmatically
- change font stretch code
- variable font Aspose.Words
- dynamic typography C#
language: hu
og_description: Használjon változó súlyú betűtípust C#-ban a betűsúly programozott
  beállításához és a betűszélesség kódjának módosításához, lehetővé téve a dinamikus
  tipográfiát a dokumentumaiban.
og_title: Változó vastagságú betűkészlet használata C#-ban – Teljes útmutató
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  headline: Use Variable Weight Font in C# – Complete Programming Guide
  type: TechArticle
- description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  name: Use Variable Weight Font in C# – Complete Programming Guide
  steps:
  - name: What if the font doesn’t appear at all?
    text: '- **Missing FontSettings**: Double‑check that `doc.FontSettings = fontSettings;`
      is executed **before** any text is added. - **Incorrect family name**: Use `fontSettings.GetFonts()`
      to list all discovered families; copy the exact string. - **Unsupported weight/stretch**:
      Some variable fonts only sup'
  - name: Can I change the weight after the document is saved?
    text: Yes. The `Run` object is mutable, so you can adjust `FontWeight` or `FontStretch`
      at any point before the final `Save`. If you need to toggle weights dynamically
      (e.g., based on user interaction), consider generating separate runs for each
      state.
  - name: Does this work with DOCX output?
    text: Absolutely. The variable‑weight metadata is stored in the underlying OpenXML,
      and modern versions of Word can interpret it. However, older Word versions may
      ignore the stretch setting.
  type: HowTo
tags:
- C#
- Aspose.Words
- Variable Fonts
title: Változó súlyú betűtípus használata C#-ban – Teljes programozási útmutató
url: /hu/net/enable-opentype-features/use-variable-weight-font-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Változó súlyú betűkészlet használata C#‑ban – Teljes programozási útmutató

Valaha szükséged volt **változó súlyú betűkészlet** használatára egy .NET projektben, de nem tudtad, hogyan tegyed a súlyt és a nyújtást felhasználói bemenetre reagálóvá? Nem vagy egyedül. Sok UI vagy jelentéskészítési helyzetben azt szeretnéd, hogy a szöveg alkalmazkodjon – például egy könnyű címsor, amely hover‑nél félkövér lesz, vagy egy bekezdés, amely a hangsúlyozás érdekében szélesedik. A jó hír, hogy az Aspose.Words‑szal **programozottan beállíthatod a betűsúlyt** és akár **a betűnyújtás kódját** is módosíthatod menet közben.

Ebben az útmutatóban egy gyakorlati példán keresztül mutatjuk be, hogyan tölts be egy változó‑súlyú betűkészletet, alkalmazz egy egyéni súlyt, és állítsd be a nyújtási beállítást – mindezt tiszta C# kóddal, amelyet egyszerűen másolhatsz‑beilleszthetsz. A végére egy futtatható konzolalkalmazásod lesz, amely PDF‑ben mutatja be a hatást.

---

## Amire szükséged lesz

- **Aspose.Words for .NET** (v23.12 vagy újabb). A könyvtár teljes támogatást nyújt a változó‑súlyú betűkészletekhez.
- Egy mappa, amely legalább egy változó‑súlyú betűkészlet‑fájlt tartalmaz, pl. *RobotoFlex‑Variable.ttf*. Letöltheted a Google Fonts‑ról.
- .NET 6 SDK (vagy bármely friss .NET verzió) és a kedvenc IDE‑d.
- Alapvető C# ismeretek – semmi bonyolult, csak néhány sor kód.

Ennyi. Nem kell semmilyen extra NuGet csomag az Aspose.Words‑en kívül, és nincs rejtett konfigurációs fájl.

---

![Változó súlyú betűkészlet használata példa](https://example.com/variable-weight-sample.png "Változó súlyú betűkészlet bemutató")

*Alt text: képernyőkép, amely a változó súlyú betűkészlet használatát mutatja egy generált PDF dokumentumban.*

---

## 1. lépés: FontSettings beállítása és a betűkészlet‑mappa megadása  

Először is – az Aspose.Words‑nek tudnia kell, hol találhatók a változó‑súlyú betűkészletek. Ezt egy `FontSettings` objektum létrehozásával és egy `FolderFontSource` csatolásával éred el. A `true` jelző azt mondja a motornak, hogy a almappákat is keresse, ami hasznos, ha több betűcsaládot tárolsz együtt.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create FontSettings and point to the folder containing variable‑weight fonts
var fontSettings = new FontSettings();
fontSettings.SetFontSources(new FontSourceBase[]
{
    new FolderFontSource(@"C:\MyProject\Fonts\", true) // Adjust path to your own directory
});
```

**Miért fontos:** A mappa regisztrálása nélkül az Aspose.Words a rendszer betűkészleteire támaszkodik, és figyelmen kívül hagyja a saját betűfájlodban beágyazott változó‑súlyú adatokat. Ez a lépés az alapja mindennek, ami később következik.

---

## 2. lépés: FontSettings csatolása a Document‑hez  

Most létrehozunk egy új `Document`‑et (vagy betöltünk egy meglévőt), és megmondjuk neki, hogy használja a most előkészített `FontSettings`‑et. Ez a kötés teszi lehetővé, hogy a változó‑súlyú adatok minden később hozzáadott `Run`‑ban elérhetők legyenek.

```csharp
// Step 2: Attach the FontSettings to the document
var doc = new Document();          // Starts with a blank document
doc.FontSettings = fontSettings;   // Connects our custom fonts
```

Ha már van egy sablonod – mondjuk egy Word‑fájl helyőrzőkkel – akkor a `new Document()` helyett `new Document("Template.docx")`‑t használhatsz. Ugyanaz a `FontSettings` lesz alkalmazva.

---

## 3. lépés: Run hozzáadása, amely a változó‑súlyú betűkészletet fogja használni  

A **Run** a legkisebb szövegformázási egység az Aspose.Words‑ben. Létrehozunk egyet, beillesztjük egy új bekezdésbe, majd később módosítjuk a betűtulajdonságait.

```csharp
// Step 3: Add a run of text that will use the variable‑weight font
var paragraph = new Paragraph(doc);
doc.FirstSection.Body.AppendChild(paragraph);

var run = new Run(doc, "Variable‑weight text demo");
paragraph.AppendChild(run);
```

Ekkor a szöveg az alapértelmezett betűvel (általában Times New Roman) jelenik meg. A varázslat akkor kezdődik, amikor a változó‑súlyú családot hozzárendeljük.

---

## 4. lépés: Változó‑súlyú betűcsalád kiválasztása  

Itt jön a **változó súlyú betűkészlet** tényleges használata. Állítsd be a `Font.Name`‑t a változó betűfájlban definiált pontos családnévre. A Roboto Flex esetében ez `"Roboto Flex"`.

```csharp
// Step 4: Choose the variable‑weight font family
run.Font.Name = "Roboto Flex";
```

Ha nem vagy biztos a családnévben, nyisd meg a `.ttf` fájlt egy betűkészlet‑böngészőben, vagy használd a `fontSettings.GetFonts()` metódust a rendelkezésre álló családok felsorolásához.

---

## 5. lépés: Betűsúly és nyújtás programozott beállítása  

Most jön a tutorial középpontja: **programozottan beállítjuk a betűsúlyt** és **módosítjuk a betűnyújtás kódját**. Mindkét tulajdonság egész számot vár, amely az OpenType specifikációnak felel meg.

```csharp
// Step 5: Specify the desired weight and stretch for the run
run.Font.FontWeight = 300;   // Light weight (300)
run.Font.FontStretch = 125; // Expanded stretch (125% of normal width)
```

- **FontWeight**: 100 (Thin) → 900 (Black). Válassz bármilyen értéket, amelyet a változó betűkészlet támogat.
- **FontStretch**: 50 (Ultra‑Condensed) → 200 (Ultra‑Expanded). Az alapértelmezett 100 (Normal).

> **Pro tipp:** Nem minden változó betűkészlet teszi elérhetővé a teljes tartományt. Ha olyan értéket állítasz be, amely nincs támogatva, a motor a legközelebbi elérhető súlyra vagy nyújtásra korlátozza.

---

## 6. lépés: Dokumentum mentése és az eredmény ellenőrzése  

Végül írd ki a dokumentumot PDF‑be (vagy DOCX‑be), majd nyisd meg, hogy lásd a hatást. A PDF kiváló formátum a vizuális ellenőrzéshez, mert a megjelenítés minden platformon konzisztens.

```csharp
// Step 6: Save the document as PDF
doc.Save(@"C:\MyProject\Output\VariableWeightDemo.pdf", SaveFormat.Pdf);
```

Amikor megnyitod a *VariableWeightDemo.pdf*-t, a „Variable‑weight text demo” feliratot egy könnyű, enyhén kibővített Roboto Flex változatban kell látnod. Állítsd a `FontWeight`‑t `700`‑ra és a `FontStretch`‑t `80`‑ra, majd futtasd újra – figyeld, ahogy a szöveg félkövér és sűrűbb lesz.

---

## Gyakori kérdések és speciális esetek  

### Mi van, ha a betűkészlet egyáltalán nem jelenik meg?  

- **Hiányzó FontSettings**: Ellenőrizd, hogy a `doc.FontSettings = fontSettings;` **minden szöveg hozzáadása előtt** végrehajtásra került-e.
- **Helytelen családnév**: Használd a `fontSettings.GetFonts()`‑t az összes felfedezett család listázásához; másold ki a pontos karakterláncot.
- **Nem támogatott súly/nyújtás**: Néhány változó betűkészlet csak a 100‑900 tartomány egy részét támogatja. Használd a `run.Font.FontWeight = 400;`‑et biztonságos tartalékként.

### Módosítható a súly a dokumentum mentése után?  

Igen. A `Run` objektum módosítható, így a `FontWeight` vagy `FontStretch` értékét a végső `Save` előtt bármikor megváltoztathatod. Ha dinamikusan szeretnél súlyokat váltogatni (pl. felhasználói interakció alapján), érdemes külön `Run`‑okat létrehozni minden állapothoz.

### Működik ez DOCX kimenettel is?  

Természetesen. A változó‑súlyú metaadatok az alapszintű OpenXML‑ben tárolódnak, és a modern Word‑verziók képesek értelmezni őket. Azonban a régebbi Word‑verziók esetleg figyelmen kívül hagyják a nyújtási beállítást.

---

## Teljes működő példa  

Az alábbiakban egy komplett konzolprogramot találsz, amelyet azonnal lefordíthatsz és futtathatsz. Tartalmazza a szükséges `using` direktívákat, hibakezelést és megjegyzéseket.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace VariableWeightDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure FontSettings
            var fontSettings = new FontSettings();
            fontSettings.SetFontSources(new FontSourceBase[]
            {
                // 👉 Point to your local folder containing the variable‑weight font files
                new FolderFontSource(@"C:\MyProject\Fonts\", true)
            });

            // 2️⃣ Create the document and attach FontSettings
            var doc = new Document();
            doc.FontSettings = fontSettings;

            // 3️⃣ Build a paragraph with a run of text
            var paragraph = new Paragraph(doc);
            doc.FirstSection.Body.AppendChild(paragraph);
            var run = new Run(doc, "Variable‑weight text demo");
            paragraph.AppendChild(run);

            // 4️⃣ Apply the variable‑weight font family
            run.Font.Name = "Roboto Flex";

            // 5️⃣ Set weight (300 = Light) and stretch (125 = Expanded)
            run.Font.FontWeight = 300;   // set font weight programmatically
            run.Font.FontStretch = 125; // change font stretch code

            // 6️⃣ Save as PDF to verify the rendering
            string outputPath = @"C:\MyProject\Output\VariableWeightDemo.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}");
            Console.WriteLine("Open the PDF to see the light, expanded Roboto Flex text.");
        }
    }
}
```

**Várható kimenet:** A konzol kiírja a mentési útvonalat, a generált PDF pedig a szöveget egy könnyű, kibővített stílusban mutatja – pontosan úgy, ahogy konfiguráltuk.

---

## Összefoglalás  

Megmutattuk, hogyan **használj változó súlyú betűkészletet** C#‑ban az Aspose.Words‑szal, bemutattuk a **betűsúly programozott beállítását**, és megmutattuk a **betűnyújtás kódjának módosítását** a glifek szélesítéséhez vagy szűkítéséhez. A lépések egyszerűek: konfiguráld a `FontSettings`‑et, csatold a `Document`‑hez, hozz létre egy `Run`‑t, válaszd ki a változó‑súlyú családot, majd finomhangold a `FontWeight` és `FontStretch` értékeket.

---

## Mi következik?  

- **Dinamikus UI integráció**: Kapcsold ugyanazt a logikát egy WinForms vagy WPF alkalmazáshoz, hogy a felhasználók súlyt/nyújtást csúszkákkal választhassanak.
- **Több run**: Kombinálj több `Run`‑t különböző súlyokkal egy bekezdésen belül, hogy gazdag tipográfiai hierarchiát hozz létre.
- **Haladó tengelyek**: Néhány változó betűkészlet további tengelyeket (pl. dőlésszög, optikai méret) is kínál. Használd a `run.Font.FontStyle`‑t vagy fedezd fel a `FontVariationSettings`‑et a még finomabb vezérléshez.
- **Teljesítmény tippek**: Cache‑eld a `FontSettings` példányt sok dokumentum feldolgozása esetén, hogy elkerüld az ismételt mappakereséseket.

Kísérletezz bátran – cseréld le a *Roboto Flex*-et *Inter Variable*-ra vagy bármely más OpenType változó betűkészletre, és nézd meg, hogyan nyernek új vizuális rugalmasságot a dokumentumaid. Boldog kódolást!

## Mit érdemes legközelebb megtanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra építenek. Minden forrás komplett, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek az API további funkcióinak elsajátításában és alternatív megvalósítási megközelítések felfedezésében saját projektjeidben.

- [Use Font From Target Machine](/words/english/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Use Font From Target Machine](/words/german/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Use Font From Target Machine](/words/french/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}