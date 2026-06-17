---
category: general
date: 2026-04-24
description: Sla het document op als txt en converteer Word naar LaTeX met Aspose.Words.
  Leer hoe je Word-wiskundige vergelijkingen snel naar LaTeX exporteert.
draft: false
keywords:
- save document as txt
- convert word to latex
- convert word equations to latex
- export word math latex
language: nl
og_description: Sla document op als txt en converteer Word‑vergelijkingen naar LaTeX
  met C#. Complete stapsgewijze handleiding met code.
og_title: Document opslaan als TXT – Exporteer Word‑wiskunde naar LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
title: Document opslaan als TXT – Exporteer Word‑wiskunde naar LaTeX in C#
url: /nl/net/programming-with-officemath/save-document-as-txt-export-word-math-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Document opslaan als TXT – Word-wiskunde exporteren naar LaTeX in C#

Heb je ooit moeten **document opslaan als txt** terwijl je je mooie vergelijkingen intact wilt houden? Je bent niet de enige. De ingebouwde “Save as plain text” van Word verwijdert Office Math, waardoor je onleesbare rommel overhoudt. Wat als je die vergelijkingen kunt behouden, maar in nette LaTeX?

In deze tutorial lopen we stap voor stap door hoe je **convert Word to LaTeX**‑klaar tekst kunt maken met Aspose.Words voor .NET. Aan het einde heb je een `.txt`‑bestand waarin elke vergelijking wordt weergegeven als juiste LaTeX‑opmaak, klaar om in een paper of een markdown‑bestand te plakken. Geen externe converters, geen handmatig kopiëren‑plakken—slechts een paar regels C#.

## Wat je zult leren

- Hoe je een `.docx`‑bestand laadt met Aspose.Words.  
- Het configureren van `TxtSaveOptions` zodat Office Math wordt geëxporteerd als LaTeX.  
- Het opslaan van het resultaat naar een platte‑tekst‑bestand dat je in elke editor kunt openen.  
- Afhandeling van randgevallen voor inline‑ versus display‑vergelijkingen, en een snelle tip voor batch‑verwerking van meerdere documenten.

### Vereisten

- .NET 6.0 of later (de code werkt ook met .NET Framework 4.6+).  
- Aspose.Words for .NET NuGet‑pakket (`Install-Package Aspose.Words`).  
- Een Word‑document dat minstens één vergelijking bevat (Office Math‑object).

---

## Stap 1: Installeer Aspose.Words en stel het project in

Eerst voeg je de bibliotheek toe aan je project. Open een terminal in je solution‑map en voer uit:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Als je Visual Studio gebruikt, werkt de NuGet Package Manager UI even goed—zoek naar “Aspose.Words” en klik op Installeren.

Maak nu een nieuwe console‑app (of plak de code in een bestaande). De `using`‑directives die je nodig hebt zijn:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Stap 2: Laad het bron‑document

We moeten Aspose.Words wijzen op het Word‑bestand dat de vergelijkingen bevat. Vervang `YOUR_DIRECTORY/input.docx` door het daadwerkelijke pad op jouw machine.

```csharp
// Load the source .docx file
Document doc = new Document(@"C:\MyDocs\input.docx");
```

> **Waarom dit belangrijk is:** Het laden van het document geeft Aspose.Words volledige toegang tot de interne Office Math‑objecten, die anders onzichtbaar zijn voor een eenvoudige tekst‑exporteur.

## Stap 3: Configureer TxtSaveOptions voor LaTeX‑export

De magie gebeurt in het `TxtSaveOptions`‑object. Door `OfficeMathExportMode` in te stellen op `LaTeX`, wordt elke vergelijking omgezet naar het overeenkomstige LaTeX‑equivalent.

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

> **Wat als je MathML nodig hebt?** Verander `OfficeMathExportMode` naar `MathML`. dezelfde API ondersteunt verschillende uitvoerformaten.

## Stap 4: Sla het document op als platte‑tekst

Nu schrijven we het bestand weg. Het resulterende `Math.txt` zal gewone tekst bevatten plus LaTeX‑fragmenten voor elke vergelijking.

```csharp
// Save the document as a .txt file with LaTeX equations
doc.Save(@"C:\MyDocs\Math.txt", txtOptions);
Console.WriteLine("Document saved as txt with LaTeX equations.");
```

Het uitvoeren van het programma produceert een bestand dat er ongeveer zo uitziet:

```
This is a simple paragraph.

Here is an inline equation: $E = mc^2$

And a displayed equation:
\[
\int_{0}^{\infty} e^{-x} \, dx = 1
\]
```

Let op hoe de inline‑vergelijking `$…$` gebruikt, terwijl de display‑vergelijking wordt omgeven door `\[` en `\]`. Dat is de standaard LaTeX‑conventie, en Aspose.Words doet dit automatisch.

## Stap 5: Verifieer de output (optioneel)

Als je wilt dubbel‑controleren of de LaTeX geldig is, kun je het `.txt`‑bestand voeren aan een LaTeX‑compiler zoals `pdflatex` of een online renderer zoals Overleaf. De tekst zou zonder fouten moeten compileren, en de vergelijkingen verschijnen precies zoals ze in Word stonden.

```bash
pdflatex Math.txt
```

Als je “Undefined control sequence” krijgt, zorg er dan voor dat de LaTeX‑pakketten die je nodig hebt (bijv. `amsmath`) zijn opgenomen in je preamble wanneer je de tekst in een groter LaTeX‑document embedde.

## Afhandeling van veelvoorkomende variaties

### Meerdere bestanden in een map converteren

```csharp
string[] files = Directory.GetFiles(@"C:\MyDocs\", "*.docx");
foreach (var file in files)
{
    Document d = new Document(file);
    d.Save(Path.ChangeExtension(file, ".txt"), txtOptions);
}
Console.WriteLine("Batch conversion complete.");
```

### Omgaan met inline‑ versus display‑vergelijkingen

Aspose.Words detecteert automatisch het type vergelijking op basis van de lay-out in Word. Als je een bepaalde stijl wilt forceren, kun je de output post‑processen:

```csharp
string txt = File.ReadAllText(@"C:\MyDocs\Math.txt");
txt = txt.Replace("$", "\\(").Replace("$", "\\)"); // forces inline math delimiters
File.WriteAllText(@"C:\MyDocs\Math_fixed.txt", txt);
```

### Exporteren naar andere formaten

Als LaTeX niet jouw doel is, schakel dan eenvoudig de exportmodus:

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML; // for MathML
```

Of gebruik `HtmlSaveOptions` als je MathML ingebed in HTML verkiest.

---

## Volledig werkend voorbeeld

Hieronder staat het complete, kant‑klaar programma. Kopieer‑plak het in `Program.cs` van een .NET console‑project.

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

Voer het programma uit (`dotnet run`), open `Math.txt`, en je ziet je Word‑inhoud met LaTeX‑vergelijkingen intact.

---

## Veelgestelde vragen

**Q: Werkt dit met oudere .doc‑bestanden?**  
A: Ja—Aspose.Words kan legacy `.doc`‑bestanden openen, maar complexe vergelijkingen kunnen als afbeeldingen worden opgeslagen. In dat geval valt de exporter terug op een placeholder‑commentaar.

**Q: Wat als een vergelijking aangepaste symbolen bevat?**  
A: Aspose.Words mappt de meeste Office Math‑symbolen naar standaard LaTeX‑commando's. Voor echt aangepaste symbolen moet je mogelijk handmatig de gegenereerde LaTeX bewerken.

**Q: Is de output UTF‑8 gecodeerd?**  
A: Standaard schrijft `TxtSaveOptions` UTF‑8, wat veilig is voor de meeste talen en symbolen.

## Conclusie

Je weet nu hoe je **save document as txt** kunt uitvoeren terwijl je elke vergelijking behoudt als nette LaTeX‑opmaak. Deze aanpak stelt je in staat **convert Word to LaTeX** uit te voeren zonder tools van derden, en schaalt van één bestand tot volledige mappen. Vervolgens kun je **convert word equations to LaTeX** verkennen voor batch‑verwerking, of duiken in **export word math latex** voor HTML‑ of Markdown‑pijplijnen.

Voel je vrij om te experimenteren—verwissel `OfficeMathExportMode` voor MathML, pas de regel‑afbrekingsafhandeling aan, of integreer dit fragment in een grotere document‑generatie‑workflow. Veel plezier met coderen, en moge je vergelijkingen altijd perfect renderen!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}