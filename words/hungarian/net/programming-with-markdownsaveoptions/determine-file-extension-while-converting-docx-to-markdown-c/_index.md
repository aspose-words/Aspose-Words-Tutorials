---
category: general
date: 2026-02-15
description: Tanulja meg, hogyan határozza meg a fájlkiterjesztést a DOCX Markdown
  formátumba konvertálásakor, hogyan vonja ki a képeket, mentse a diagramokat SVG
  formátumban, és exportálja a képeket PNG formátumban az Aspose.Words használatával.
draft: false
keywords:
- determine file extension
- convert docx to markdown
- how to extract images
- save charts as svg
- export images as png
language: hu
og_description: Tudja meg, hogyan határozhatja meg a fájl kiterjesztését, nyerhet
  ki képeket, menthet diagramokat SVG formátumban, és exportálhatja a képeket PNG
  formátumba a DOCX Markdown formátumba konvertálásakor az Aspose.Words segítségével.
og_title: Fájlkiterjesztés meghatározása DOCX konvertálásakor Markdownra
tags:
- Aspose.Words
- C#
- Document Conversion
title: Fájl kiterjesztés meghatározása DOCX konvertálásakor Markdownra – Teljes útmutató
url: /hu/net/programming-with-markdownsaveoptions/determine-file-extension-while-converting-docx-to-markdown-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# fájl kiterjesztés meghatározása DOCX konvertálásakor Markdown‑ba – Teljes útmutató

Valaha is elgondolkodtál, hogyan **meghatározzuk a fájl kiterjesztését** minden olyan erőforrásra, amely egy DOCX‑ből előjön, amikor Markdown‑ba konvertálod? Nem vagy egyedül. Sok valós projektben **convert docx to markdown**‑ra van szükségünk, minden képet ki kell nyernünk, és a diagramokat éles SVG fájlokként kell megtartani – anélkül, hogy egy titokzatos „resource_3.bin” fájlba torkollna.

Ebben az útmutatóban egy gyakorlati megoldáson keresztül vezetünk végig, amely nem csak automatikusan **meghatározza a fájl kiterjesztését**, hanem megmutatja, **hogyan vonjuk ki a képeket**, **hogyan mentjük a diagramokat SVG‑ként**, és **hogyan exportáljuk a képeket PNG‑ként** az Aspose.Words for .NET használatával. A végére egy kész‑kód snippetet kapsz, amely egy tiszta *.md* fájlt és egy rendezett erőforrás‑mappát hoz létre.

## Amire szükséged lesz

- .NET 6+ (vagy .NET Framework 4.7.2+) – az API mindkét esetben ugyanúgy működik.
- Aspose.Words for .NET (legújabb verzió, pl. 23.9).  
- Egy DOCX fájl, amely képeket, diagramokat vagy bármilyen más beágyazott erőforrást tartalmaz.
- Kedvenc IDE (Visual Studio, Rider vagy VS Code).  
- Az Aspose.Words‑on kívül nincs szükség további NuGet csomagokra.

## 1. lépés: A forrás DOCX dokumentum betöltése

Először is—szerezd be a Word fájlt, amelyet átalakítani szeretnél. Ez az a pont, ahol a konverziós folyamat elindul.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Load the source DOCX. Adjust the path to where your file lives.
Document doc = new Document(@"C:\Docs\Complex.docx");
```

*Miért fontos:* A `Document` objektum minden Aspose.Words művelet belépési pontja. Ha a fájlt nem lehet betölteni, semmi más nem fog működni, ezért mindig ellenőrizd az elérési utat és a fájl jogosultságait.

## 2. lépés: Mappa előkészítése a kinyert erőforrások számára

Amikor **meghatározzuk a fájl kiterjesztését**, szükségünk van egy helyre, ahová a létrejövő PNG‑eket, SVG‑ket vagy bármilyen más binárist elhelyezhetjük. A mappa előzetes létrehozása elkerüli a későbbi „könyvtár nem található” kivételeket.

```csharp
// Define where the extracted assets will live.
string resourcesFolder = @"C:\Docs\MarkdownResources";

// Ensure the folder exists – CreateDirectory is idempotent.
Directory.CreateDirectory(resourcesFolder);
```

*Pro tipp:* Tartsd a resources mappát a végső Markdown fájl **mellett**, így a relatív hivatkozások sokkal tisztábbak lesznek.

## 3. lépés: MarkdownSaveOptions konfigurálása – A folyamat szíve

Itt történik a tényleges **fájl kiterjesztés meghatározása** minden egyes erőforrásra. A `MarkdownSaveOptions` osztály lehetővé teszi a Base‑64 beágyazás kikapcsolását és egy `ResourceSavingCallback` csatlakoztatását. Ennek a visszahívásnak a belsejében ellenőrizzük a `args.ResourceType`‑t, és eldöntjük, hogy a fájlnak `.png`, `.svg` vagy valami más legyen.

```csharp
var mdOptions = new MarkdownSaveOptions
{
    // ExportImagesAsBase64 = false forces Aspose to write each image as a separate file.
    ExportImagesAsBase64 = false,

    // This callback runs for every external resource (image, chart, etc.).
    ResourceSavingCallback = (sender, args) =>
    {
        // ---- Step 3‑a: Determine a file extension based on the resource type ----
        string extension = args.ResourceType switch
        {
            // Images become PNG – this satisfies the “export images as png” requirement.
            ResourceType.Image => ".png",

            // Charts are saved as SVG – perfect for web‑friendly scaling.
            ResourceType.Chart => ".svg",

            // Anything else falls back to a generic binary.
            _ => ".bin"
        };

        // ---- Step 3‑b: Build a unique filename to avoid collisions ----
        string fileName = $"resource_{args.Index}{extension}";
        string fullPath = Path.Combine(resourcesFolder, fileName);

        // ---- Step 3‑c: Write the raw bytes to disk ----
        File.WriteAllBytes(fullPath, args.ResourceData);

        // ---- Step 3‑d: Tell the Markdown file where to find this asset ----
        // Use a relative path so the .md file stays portable.
        args.ResourceFileName = $"./MarkdownResources/{fileName}";
    }
};
```

### Miért határozzuk meg kifejezetten a **fájl kiterjesztését** itt

- **Átláthatóság:** A `.png` kép azonnal felismerhető, míg egy eltévedt `.bin` fájl összezavarja az olvasókat.
- **Kompatibilitás:** Sok statikus weboldalkészítő (Hugo, Jekyll) elvárja, hogy a képfájlok szabványos kiterjesztéssel rendelkezzenek.
- **Kontroll:** A `switch` kifejezést kibővítheted PDF‑ek, OLE‑objektumok stb. kezelésére anélkül, hogy a többi kódot módosítanád.

## 4. lépés: Dokumentum mentése Markdown‑ként

Miután a beállítások készen vannak, az utolsó hívás egy egyetlen soros kód. Az Aspose minden erőforrásra meghívja a visszahívást, kiírja a fájlokat, és egy tiszta Markdown dokumentumot hoz létre, amely hivatkozik rájuk.

```csharp
// Save the Markdown file alongside the resources folder.
string markdownPath = @"C:\Docs\Complex.md";
doc.Save(markdownPath, mdOptions);
```

### Várható kimenet

- `Complex.md` – egy Markdown fájl, amely olyan képhivatkozásokat tartalmaz, mint `![](./MarkdownResources/resource_0.png)`.
- `C:\Docs\MarkdownResources\` – egy mappa, amely a következőkkel van feltöltve:
  - `resource_0.png` (első kép)
  - `resource_1.svg` (első diagram)
  - …és így tovább minden beágyazott objektumnál.

Nyisd meg a Markdown fájlt VS Code‑ban vagy egy előnézőben; a képeknek helyesen kell megjelenniük. Ha egy diagram elmosódott raszterként jelenik meg, ellenőrizd, hogy a `ResourceType.Chart` eset `.svg`‑re mutat‑e – ez a kulcs a **diagramok SVG‑ként mentéséhez**.

## 5. lépés: Ellenőrzés és finomhangolás – Gyakori hibák és széljegyek

### 5.1 Hiányzó képek

Ha törött hivatkozásokat látsz, győződj meg arról, hogy a relatív útvonal (`./MarkdownResources/`) pontosan megegyezik a mappa nevével. A Windows nem érzékeny a kis‑ és nagybetűkre, de sok statikus weboldalkészítő igen.

### 5.2 Nem‑kép erőforrások

Az Aspose képes beágyazott objektumokat is kiadni, például PDF‑eket vagy OLE‑csomagokat. Bővítsd a `switch`‑et:

```csharp
ResourceType.OleObject => ".pdf",
ResourceType.Unknown   => ".bin"
```

### 5.3 Nagy dokumentumok

Több tucat nagy felbontású képet tartalmazó DOCX fájlok esetén érdemes lehet **lecsökkenteni** a méretet a lemezre írás előtt. Helyezz be egy elő‑mentés lépést:

```csharp
if (args.ResourceType == ResourceType.Image)
{
    using var img = Image.Load(args.ResourceData);
    img.Resize(800, 0, ResizeMode.Max); // keep aspect ratio
    args.ResourceData = img.SaveToBytes(ImageSaveFormat.Png);
}
```

### 5.4 Képek exportálása PNG‑ként vs. eredeti formátum

A példa minden képre PNG‑t kényszerít (`export images as png`). Ha inkább az eredeti formátumot szeretnéd megtartani (pl. JPEG), cseréld le a `.png` kiterjesztést a `Path.GetExtension(args.ResourceFileName)`‑re. Csak ne felejtsd el a MIME‑típust a Markdown‑ban szükség esetén módosítani.

## Teljes működő példa

Az alábbiakban a teljes, másolás‑beillesztésre kész program látható. .NET 6‑ra célzó konzolalkalmazásként fordul le, de a kódot bármilyen projekt típusba beillesztheted.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

namespace DocxToMarkdownDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source DOCX.
            Document doc = new Document(@"C:\Docs\Complex.docx");

            // 2️⃣ Create a folder for external resources.
            string resourcesFolder = @"C:\Docs\MarkdownResources";
            Directory.CreateDirectory(resourcesFolder);

            // 3️⃣ Set up Markdown save options with a callback that determines file extensions.
            var mdOptions = new MarkdownSaveOptions
            {
                ExportImagesAsBase64 = false,
                ResourceSavingCallback = (sender, args) =>
                {
                    // Determine proper extension.
                    string extension = args.ResourceType switch
                    {
                        ResourceType.Image => ".png",   // export images as png
                        ResourceType.Chart => ".svg",   // save charts as svg
                        _ => ".bin"
                    };

                    // Unique name and full disk path.
                    string fileName = $"resource_{args.Index}{extension}";
                    string fullPath = Path.Combine(resourcesFolder, fileName);

                    // Write the bytes to disk.
                    File.WriteAllBytes(fullPath, args.ResourceData);

                    // Point the Markdown file to the saved resource.
                    args.ResourceFileName = $"./MarkdownResources/{fileName}";
                }
            };

            // 4️⃣ Save as Markdown.
            string markdownPath = @"C:\Docs\Complex.md";
            doc.Save(markdownPath, mdOptions);

            // 5️⃣ Inform the user.
            System.Console.WriteLine("Conversion complete!");
            System.Console.WriteLine($"Markdown file: {markdownPath}");
            System.Console.WriteLine($"Resources folder: {resourcesFolder}");
        }
    }
}
```

Futtasd a programot, nyisd meg a `Complex.md`‑t, és láthatod a **fájl kiterjesztés meghatározása** logikát működés közben – minden kép PNG, minden diagram SVG, és minden hivatkozás a megfelelő fájlokra mutat.

## Összegzés

Most már tudod, **hogyan határozzuk meg a fájl kiterjesztését** minden egyes erőforrásra, amikor **docx‑t konvertálunk markdown‑ba**, hogyan **vonjuk ki a képeket**, **mentjük a diagramokat SVG‑ként**, és **exportáljuk a képeket PNG‑ként** az Aspose.Words segítségével. A kulcs a `ResourceSavingCallback`, ahol meghatározod a kiterjesztést, kiírod a bájtokat, és beállítod a relatív hivatkozást.

- Illeszd be a Markdown kimenetet egy statikus weboldalkészítőbe.
- Bővítsd a visszahívást PDF‑ek, audio vagy egyedi formátumok kezelésére.
- Adj hozzá képtömörítést vagy vízjelet a lemezre írás előtt.

Nyugodtan kísérletezz – cseréld le a `.png`‑t `.jpg`‑ra, ha a fájlméret számít, vagy finomítsd a diagramkezelést, hogy PNG‑ket állítson elő SVG‑k helyett. A minta változatlan marad: **meghatározzuk a fájl kiterjesztését**, kiírjuk a fájlt, és frissítjük a hivatkozást.

Van kérdésed a széljegyekkel kapcsolatban, vagy szeretnéd megosztani saját módosításaidat? Hagyj egy megjegyzést alább, és jó kódolást!  

![fájl kiterjesztés meghatározása diagram](determine_file_extension.png){: .align-center alt="fájl kiterjesztés meghatározása példa"}

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}