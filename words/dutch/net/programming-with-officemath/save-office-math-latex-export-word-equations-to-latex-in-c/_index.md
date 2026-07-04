---
category: general
date: 2026-04-21
description: sla Office-wiskunde LaTeX snel op met Aspose.Words – leer ook hoe je
  platte tekst van Word kunt opslaan en Word‑vergelijkingen in LaTeX kunt exporteren
  in één keer.
draft: false
keywords:
- save office math latex
- save word plain text
- export word equations latex
- convert word math latex
- convert word equations mathml
language: nl
og_description: sla Office‑wiskunde LaTeX direct op; leer Word‑vergelijkingen exporteren
  naar LaTeX en converteer Word‑wiskunde naar LaTeX met Aspose.Words in C#.
og_title: save office math latex – Exporteer Word‑vergelijkingen naar LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
title: save office math latex – Exporteer Word‑vergelijkingen naar LaTeX in C#
url: /nl/net/programming-with-officemath/save-office-math-latex-export-word-equations-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# save office math latex – Exporteer Word‑vergelijkingen naar LaTeX met Aspose.Words

Heb je ooit **save office math latex** nodig gehad uit een `.docx`‑bestand maar wist je niet waar te beginnen? Je bent niet de enige, en het goede nieuws is dat de oplossing vrij eenvoudig is. In deze gids lopen we de exacte stappen door om Word‑vergelijkingen latex (en zelfs MathML) te exporteren met Aspose.Words voor .NET, terwijl we je laten zien hoe je **save word plain text** naast de wiskunde kunt opslaan.

We behandelen alles waar je je over zou kunnen afvragen: waarom je LaTeX boven andere formaten zou kiezen, hoe je de `TxtSaveOptions` configureert, en wat te doen als je **convert word math latex** naar een andere weergave moet omzetten. Aan het einde heb je een uitvoerbaar fragment dat een Word‑document met Office‑Math‑objecten neemt en een schoon `.txt`‑bestand met LaTeX (of MathML)‑vergelijkingen genereert. Geen externe tools, geen handmatig kopiëren‑plakken — alleen nette C#‑code die je in elk project kunt plaatsen.

## Vereisten

- **Aspose.Words for .NET** (v23.10 of later). Het NuGet‑pakket is `Aspose.Words`.
- Een .NET‑ontwikkelomgeving (Visual Studio, Rider, of VS Code met de C#‑extensie).
- Een Word‑bestand (`.docx`) dat minstens één vergelijking bevat die is gemaakt met de Office‑Math‑editor.
- Basiskennis van C#‑syntaxis — niets ingewikkeld, gewoon de gebruikelijke `using`‑statements.

Als je die punten al hebt afgevinkt, geweldig — laten we erin duiken.

## Stap 1 – Stel **save office math latex**‑opties in

Het eerste wat je moet doen is Aspose.Words vertellen hoe je de wiskundige inhoud wilt renderen. De `TxtSaveOptions`‑klasse heeft een `OfficeMathExportMode`‑eigenschap die drie waarden accepteert: `LaTeX`, `MathML` of `Text`. Voor ons primaire doel kiezen we `LaTeX`.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Configure TXT save options to export equations as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // This line makes the library output LaTeX for every Office Math object
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
    // You could also use OfficeMathExportMode.MathML or .Text here
};
```

**Waarom dit belangrijk is:** Wanneer je `OfficeMathExportMode` instelt op `LaTeX`, wordt elke vergelijking omgezet naar de ruwe LaTeX‑bron. Die bron kan later met elke LaTeX‑engine worden gecompileerd, waardoor je pixel‑perfecte typesetting krijgt zonder de formules opnieuw te hoeven typen.

> **Pro tip:** Als je ooit **convert word equations mathml** moet doen, verwissel dan simpelweg de enum‑waarde naar `OfficeMathExportMode.MathML`. De rest van de code blijft ongewijzigd.

## Stap 2 – Laad het Word‑document (het **save word plain text**‑scenario)

Vervolgens laden we het bron‑`.docx`. Deze stap is identiek, of je nu alleen geïnteresseerd bent in platte‑tekst‑extractie of ook de vergelijkingen in LaTeX wilt hebben.

```csharp
// Load the document that contains Office Math objects
Document doc = new Document(@"C:\MyDocs\input.docx");

// Optional: verify that the document actually has equations
bool hasMath = doc.GetChildNodes(NodeType.OfficeMath, true).Count > 0;
if (!hasMath)
{
    Console.WriteLine("Warning: No Office Math objects found in the document.");
}
```

**Wat gebeurt er hier?** De `Document`‑constructor leest het bestand in het geheugen. De snelle controle met `GetChildNodes` helpt je een veelvoorkomend randgeval te vangen — proberen LaTeX te exporteren uit een bestand dat geen vergelijkingen bevat. Het is een kleine beveiliging die je later een raadselachtige lege output bespaart.

## Stap 3 – **save office math latex** naar een platte‑tekst‑bestand

Nu schrijven we eindelijk het bestand. De `Save`‑methode respecteert de `TxtSaveOptions` die we eerder hebben geconfigureerd, zodat het resulterende `.txt` zowel gewone tekst als LaTeX‑fragmenten voor elke vergelijking bevat.

```csharp
// Define the output path
string outputPath = @"C:\MyDocs\Equations.txt";

// Save the document as plain text, with LaTeX equations embedded
doc.Save(outputPath, txtOptions);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

Wanneer je `Equations.txt` opent, zie je iets als:

```
This is a sample paragraph.

\begin{equation}
E = mc^2
\end{equation}

Another paragraph follows.
```

De LaTeX‑blokken worden automatisch ingesloten in `\begin{equation}` … `\end{equation}`, waardoor ze klaar zijn voor opname in elk LaTeX‑document.

## Stap 4 – Alternatief: **convert word equations mathml** in plaats van LaTeX

Als je downstream‑toolchain MathML prefereert (bijvoorbeeld een webpagina die vergelijkingen rendert met MathJax), wijzig dan simpelweg de exportmodus:

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
doc.Save(@"C:\MyDocs\EquationsMathML.txt", txtOptions);
```

De output zal nu XML‑achtige MathML‑tags bevatten, zoals:

```xml
<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>E</mi>
  <mo>=</mo>
  <mi>m</mi>
  <msup><mi>c</mi><mn>2</mn></msup>
</math>
```

Dat is de snelle manier om **convert word equations mathml** uit te voeren zonder een eigen parser te schrijven.

## Stap 5 – Bonus: **save word plain text** terwijl je vergelijkingen gescheiden houdt

Soms wil je een schone tekstversie van het document *zonder* enige LaTeX‑ of MathML‑inbedding. Dat kun je bereiken door de exportmodus te schakelen naar `Text` en een tweede opslaan‑pass uit te voeren:

```csharp
// Export pure plain text (no math markup)
txtOptions.OfficeMathExportMode = OfficeMathExportMode.Text;
doc.Save(@"C:\MyDocs\PlainDocument.txt", txtOptions);
```

Nu heb je drie bestanden naast elkaar:

| Bestand                     | Inhoud                                 |
|------------------------------|----------------------------------------|
| `Equations.txt`              | Platte tekst **+** LaTeX‑vergelijkingen |
| `EquationsMathML.txt`        | Platte tekst **+** MathML‑vergelijkingen |
| `PlainDocument.txt`          | Zuivere tekst, vergelijkingen verwijderd      |

Dit patroon is handig wanneer je de platte tekst in een zoekindex moet voeren, terwijl je de oorspronkelijke wiskunde behoudt voor academische publicaties.

## Volledig werkend voorbeeld (Klaar om te kopiëren‑plakken)

Hieronder staat het volledige programma dat je kunt compileren en direct kunt uitvoeren. Het demonstreert **save office math latex**, **export word equations latex**, **convert word math latex**, en **save word plain text** — alles in één net script.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure TXT save options for LaTeX export
        TxtSaveOptions txtOptions = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };

        // 2️⃣ Load the source Word document
        string inputPath = @"C:\MyDocs\input.docx";
        Document doc = new Document(inputPath);

        // Quick sanity check for equations
        if (doc.GetChildNodes(NodeType.OfficeMath, true).Count == 0)
        {
            Console.WriteLine("No equations found – proceeding with plain‑text export only.");
        }

        // 3️⃣ Save with LaTeX equations embedded
        string latexPath = @"C:\MyDocs\Equations.txt";
        doc.Save(latexPath, txtOptions);
        Console.WriteLine($"LaTeX export saved to {latexPath}");

        // 4️⃣ Switch to MathML and save (optional)
        txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
        string mathmlPath = @"C:\MyDocs\EquationsMathML.txt";
        doc.Save(mathmlPath, txtOptions);
        Console.WriteLine($"MathML export saved to {mathmlPath}");

        // 5️⃣ Finally, pure plain‑text export (no math markup)
        txtOptions.OfficeMathExportMode = OfficeMathExportMode.Text;
        string plainPath = @"C:\MyDocs\PlainDocument.txt";
        doc.Save(plainPath, txtOptions);
        Console.WriteLine($"Plain‑text export saved to {plainPath}");
    }
}
```

**Verwacht resultaat:** Na het uitvoeren vind je drie tekstbestanden in `C:\MyDocs`. Open `Equations.txt` en je ziet LaTeX‑blokken; `EquationsMathML.txt` bevat MathML; `PlainDocument.txt` is vrij van enige vergelijking‑markup.

## Veelgestelde vragen & randgevallen

- **Wat als ik alleen LaTeX nodig heb voor een deel van de vergelijkingen?**  
  Gebruik de `OfficeMath`‑node‑API om over elke vergelijking te itereren, exporteer deze handmatig met `MathConverter`, en vervang de tijdelijke tekst waar je wilt. Deze aanpak geeft je fijnmazige controle, maar voegt een paar extra regels code toe.

- **Werkt dit met .NET Core / .NET 5+?**  
  Absoluut. Aspose.Words is cross‑platform, dus dezelfde code draait op Windows, Linux en macOS zolang de runtime‑versie overeenkomt met de vereisten van de bibliotheek.

- **Kan ik de LaTeX‑wrapper (`\begin{equation}`) naar iets anders wijzigen?**  
  Ja. Stel `txtOptions.OfficeMathExportMode = OfficeMathExportMode.LaTeX` in en wijzig vervolgens `txtOptions.MathExportSettings` (beschikbaar in nieuwere releases) om de delimiters aan te passen.

- **Prestatiezorgen voor enorme documenten?**  
  De bibliotheek streamt de output, zodat het geheugenverbruik bescheiden blijft. Echter

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}