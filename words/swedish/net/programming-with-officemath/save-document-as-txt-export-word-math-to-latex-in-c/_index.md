---
category: general
date: 2026-04-24
description: Spara dokumentet som txt och konvertera Word till LaTeX med Aspose.Words.
  Lär dig hur du snabbt exporterar Word‑matematikformler till LaTeX.
draft: false
keywords:
- save document as txt
- convert word to latex
- convert word equations to latex
- export word math latex
language: sv
og_description: Spara dokument som txt och konvertera Word‑ekvationer till LaTeX med
  C#. Komplett steg‑för‑steg‑guide med kod.
og_title: Spara dokument som TXT – Exportera Word-matematik till LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
title: Spara dokument som TXT – Exportera Word-matematik till LaTeX i C#
url: /sv/net/programming-with-officemath/save-document-as-txt-export-word-math-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Spara dokument som TXT – Exportera Word Math till LaTeX i C#

Har du någonsin behövt **spara dokument som txt** samtidigt som du behåller dina avancerade ekvationer? Du är inte ensam. Word:s inbyggda “Spara som vanlig text” kastar bort Office Math och lämnar dig med oläslig skräpkod. Tänk om du kunde behålla ekvationerna, men i ren LaTeX istället?  

I den här handledningen går vi igenom exakt hur du **konverterar Word till LaTeX**‑klar text med Aspose.Words för .NET. I slutet har du en `.txt`‑fil där varje ekvation representeras som korrekt LaTeX‑markup, redo att klistras in i en artikel eller en markdown‑fil. Inga externa konverterare, ingen manuell kopiering‑och‑klistring—bara några rader C#.

## Vad du kommer att lära dig

- Hur du laddar en `.docx`‑fil med Aspose.Words.  
- Hur du konfigurerar `TxtSaveOptions` så att Office Math exporteras som LaTeX.  
- Hur du sparar resultatet till en vanlig textfil som du kan öppna i vilken editor som helst.  
- Hantering av kantfall för inline‑ vs. display‑ekvationer, samt ett snabbt tips för batch‑bearbetning av flera dokument.

### Förutsättningar

- .NET 6.0 eller senare (koden fungerar även med .NET Framework 4.6+).  
- Aspose.Words för .NET NuGet‑paket (`Install-Package Aspose.Words`).  
- Ett Word‑dokument som innehåller minst en ekvation (Office Math‑objekt).

---

## Steg 1: Installera Aspose.Words och konfigurera projektet

Först lägger du till biblioteket i ditt projekt. Öppna en terminal i din lösningsmapp och kör:

```bash
dotnet add package Aspose.Words
```

> **Proffstips:** Om du använder Visual Studio fungerar NuGet Package Manager‑gränssnittet lika bra—sök efter “Aspose.Words” och klicka på Install.

Skapa nu en ny konsolapp (eller klistra in koden i en befintlig). `using`‑direktiven du behöver är:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Dessa importerar `Document`‑klassen och `TxtSaveOptions`‑typen.

## Steg 2: Ladda källdokumentet

Vi måste peka Aspose.Words på Word‑filen som innehåller ekvationerna. Ersätt `YOUR_DIRECTORY/input.docx` med den faktiska sökvägen på din maskin.

```csharp
// Load the source .docx file
Document doc = new Document(@"C:\MyDocs\input.docx");
```

> **Varför detta är viktigt:** När dokumentet laddas får Aspose.Words full åtkomst till de interna Office Math‑objekten, som annars är osynliga för en enkel text‑exportör.

## Steg 3: Konfigurera TxtSaveOptions för LaTeX‑export

Magin sker i `TxtSaveOptions`‑objektet. Genom att sätta `OfficeMathExportMode` till `LaTeX` omvandlas varje ekvation till sin LaTeX‑ekvivalent.

```csharp
// Configure save options to export Office Math as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // Export all Office Math objects as LaTeX code
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Optional: keep line breaks similar to the original layout
    PreserveTableLayout = true
};
```

> **Behöver du MathML istället?** Ändra `OfficeMathExportMode` till `MathML`. Samma API stödjer flera utdataformat.

## Steg 4: Spara dokumentet som vanlig text

Nu skriver vi ut filen. Den resulterande `Math.txt` kommer att innehålla vanlig text plus LaTeX‑fragment för varje ekvation.

```csharp
// Save the document as a .txt file with LaTeX equations
doc.Save(@"C:\MyDocs\Math.txt", txtOptions);
Console.WriteLine("Document saved as txt with LaTeX equations.");
```

När programmet körs får du en fil som ser ungefär ut så här:

```
This is a simple paragraph.

Here is an inline equation: $E = mc^2$

And a displayed equation:
\[
\int_{0}^{\infty} e^{-x} \, dx = 1
\]
```

Lägg märke till hur inline‑ekvationen använder `$…$` medan display‑ekvationen är omsluten av `\[` och `\]`. Det är standardkonventionen i LaTeX, och Aspose.Words gör detta automatiskt.

## Steg 5: Verifiera resultatet (valfritt)

Om du vill dubbelkolla att LaTeX‑koden är giltig kan du skicka `.txt`‑filen till en LaTeX‑kompilator som `pdflatex` eller en online‑renderare som Overleaf. Texten bör kompilera utan fel, och ekvationerna visas exakt som i Word.

```bash
pdflatex Math.txt
```

Om du får “Undefined control sequence” så se till att de LaTeX‑paket du behöver (t.ex. `amsmath`) är inkluderade i ditt preamble när du bäddar in texten i ett större LaTeX‑dokument.

## Hantera vanliga variationer

### Konvertera flera filer i en mapp

```csharp
string[] files = Directory.GetFiles(@"C:\MyDocs\", "*.docx");
foreach (var file in files)
{
    Document d = new Document(file);
    d.Save(Path.ChangeExtension(file, ".txt"), txtOptions);
}
Console.WriteLine("Batch conversion complete.");
```

### Hantera inline‑ vs. display‑ekvationer

Aspose.Words upptäcker automatiskt ekvationstypen baserat på dess layout i Word. Om du vill tvinga en viss stil kan du efterbearbeta utskriften:

```csharp
string txt = File.ReadAllText(@"C:\MyDocs\Math.txt");
txt = txt.Replace("$", "\\(").Replace("$", "\\)"); // forces inline math delimiters
File.WriteAllText(@"C:\MyDocs\Math_fixed.txt", txt);
```

### Exportera till andra format

Om LaTeX inte är ditt mål, byt bara exportläget:

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML; // for MathML
```

Eller använd `HtmlSaveOptions` om du föredrar MathML inbäddat i HTML.

---

## Fullt fungerande exempel

Nedan är det kompletta, körbara programmet. Kopiera‑och‑klistra in det i `Program.cs` i ett .NET‑konsolprojekt.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToLatexTxt
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the source document
            Document doc = new Document(@"C:\MyDocs\input.docx");

            // 2️⃣ Set up save options to export Office Math as LaTeX
            TxtSaveOptions saveOptions = new TxtSaveOptions
            {
                OfficeMathExportMode = OfficeMathExportMode.LaTeX,
                PreserveTableLayout = true
            };

            // 3️⃣ Save as plain‑text with LaTeX equations
            string outputPath = @"C:\MyDocs\Math.txt";
            doc.Save(outputPath, saveOptions);

            Console.WriteLine($"✅ Saved document as txt at: {outputPath}");
            Console.WriteLine("Open the file to see LaTeX‑formatted equations.");
        }
    }
}
```

Kör programmet (`dotnet run`), öppna `Math.txt`, och du kommer att se ditt Word‑innehåll med LaTeX‑ekvationer intakta.

---

## Vanliga frågor

**Q: Fungerar detta med äldre .doc‑filer?**  
A: Ja—Aspose.Words kan öppna äldre `.doc`‑filer, men komplexa ekvationer kan lagras som bilder. I så fall faller exportören tillbaka på en platshållarkommentar.

**Q: Vad händer om en ekvation innehåller egna symboler?**  
A: Aspose.Words mappar de flesta Office Math‑symboler till standard‑LaTeX‑kommandon. För riktigt egna symboler kan du behöva redigera den genererade LaTeX‑koden manuellt.

**Q: Är utdata UTF‑8‑kodade?**  
A: Som standard skriver `TxtSaveOptions` UTF‑8, vilket är säkert för de flesta språk och symboler.

---

## Slutsats

Du vet nu hur du **sparar dokument som txt** samtidigt som du bevarar varje ekvation som ren LaTeX‑markup. Detta tillvägagångssätt låter dig **konvertera Word till LaTeX** utan tredjepartsverktyg, och det skalar från en enskild fil till hela mappar. Nästa steg kan vara att utforska **convert word equations to LaTeX** för batch‑bearbetning, eller dyka djupare in i **export word math latex** för HTML‑ eller Markdown‑pipelines.

Känn dig fri att experimentera—byt `OfficeMathExportMode` till MathML, justera radbrytningshantering, eller integrera detta kodsnutt i ett större dokument‑genereringsflöde. Lycka till med kodningen, och må dina ekvationer alltid renderas perfekt!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}