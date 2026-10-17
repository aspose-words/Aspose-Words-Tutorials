---
category: general
date: 2026-04-10
description: come impostare l'ombra su una forma in C# – impara come applicare l'ombra
  esterna, modificare la trasparenza, regolare la sfocatura e aggiungere l'ombra alla
  forma usando Aspose.Words.
draft: false
keywords:
- how to set shadow
- apply drop shadow
- how to change transparency
- how to adjust blur
- add shape shadow
language: it
og_description: come impostare l'ombra su una forma in C# – questo tutorial mostra
  come applicare l'ombra esterna, modificare la trasparenza, regolare la sfocatura
  e aggiungere l'ombra alla forma con esempi di codice chiari.
og_title: Come impostare l'ombra su una forma in C# – Guida completa
tags:
- Aspose.Words
- C#
- Document Automation
title: Come impostare l'ombra su una forma in C# – guida passo passo
url: /it/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# come impostare l'ombra su una forma in C# – Guida completa

Ti sei mai chiesto **come impostare l'ombra** su una forma quando crei programmaticamente un documento Word? Non sei solo. Molti sviluppatori si trovano in difficoltà quando hanno bisogno di una leggera ombra per una casella di testo, un logo o una call‑out box, e la documentazione dell'API sembra un po' scarsa.  

In questo tutorial percorreremo l'intero processo: dal caricamento di un `.docx`, al recupero della prima `Shape`, all'applicazione di un'ombra, alla regolazione della trasparenza, al settaggio del raggio di sfocatura e, infine, al posizionamento corretto. Alla fine avrai uno snippet riutilizzabile che funziona con Aspose.Words .NET 2023 o versioni successive, e comprenderai *perché* ogni proprietà è importante.

## Cosa ti servirà

- **Aspose.Words for .NET** (pacchetto NuGet `Aspose.Words`) – la libreria che fornisce le classi `Document`, `Shape` e `ShadowFormat`.  
- **.NET 6+** (o .NET Framework 4.7.2) – qualsiasi runtime recente va bene.  
- Un semplice file Word (`input.docx`) che contenga già almeno una forma, ad esempio una casella di testo.  
- Visual Studio, VS Code o il tuo IDE preferito.

Tutto qui. Nessun tool di terze parti, nessun interop COM, solo puro C#.

![how to set shadow example](image-placeholder.png){:alt="come impostare l'ombra su una forma in un documento Word"}

## Come impostare l'ombra – Panoramica

L'idea centrale dietro **come impostare l'ombra** è manipolare l'oggetto `ShadowFormat` che vive su una `Shape`. Pensa a `ShadowFormat` come a un piccolo “foglio di stile” per l'ombra stessa: indica al renderer se l'ombra è visibile, di che colore deve essere, quanto è trasparente, quanto è sfocata e dove si colloca rispetto alla forma.  

Di seguito trovi il programma *completo* eseguibile. Sentiti libero di copiarlo e incollarlo in un'app console, premere **F5** e osservare l'ombra apparire nel file `output.docx` salvato.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;                 // Core document classes
using Aspose.Words.Drawing;         // Shape & ShadowFormat

class ShadowDemo
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Load the Word document that contains the shape.
        // -------------------------------------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // -------------------------------------------------
        // Step 2: Retrieve the first shape (e.g., a textbox) from the document.
        // -------------------------------------------------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx has a textbox.");
            return;
        }

        // -------------------------------------------------
        // Step 3: Make the shadow visible.
        // -------------------------------------------------
        shape.ShadowFormat.Visible = true;

        // -------------------------------------------------
        // Step 4: Set the shadow colour to a dark gray.
        // -------------------------------------------------
        shape.ShadowFormat.Color = Color.DarkGray;

        // -------------------------------------------------
        // Step 5: Define the shadow's transparency (30 % transparent).
        // -------------------------------------------------
        shape.ShadowFormat.Transparency = 0.3;   // 0 = opaque, 1 = fully transparent

        // -------------------------------------------------
        // Step 6: Configure the blur radius (size) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Size = 6;            // Larger value = softer edges

        // -------------------------------------------------
        // Step 7: Set the offset distance and direction (angle) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Distance = 2;        // How far the shadow is from the shape
        shape.ShadowFormat.Angle = 45;          // Angle in degrees (0 = right, 90 = down)

        // -------------------------------------------------
        // Save the modified document.
        // -------------------------------------------------
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Shadow applied successfully! Check output.docx.");
    }
}
```

### Perché queste impostazioni sono importanti

- **Visible** – Senza attivare questo flag, tutte le altre proprietà vengono ignorate.  
- **Color** – Un grigio scuro imita un'ombra tipica dell'interfaccia; puoi sostituirlo con qualsiasi `Color`.  
- **Transparency** – 0.3 conferisce un aspetto *soft* mantenendo la forma leggibile.  
- **Size** – Controlla la sfocatura; un valore di 6 è solitamente sufficiente per un risultato professionale.  
- **Distance & Angle** – Insieme definiscono lo *spostamento*; 2 pt a 45° producono un'ombra diagonale sottile.

Questa è l'essenza di **come impostare l'ombra**. Successivamente, analizzeremo ogni elemento così potrai **applicare l'ombra**, **modificare la trasparenza**, **regolare la sfocatura** e **aggiungere l'ombra alla forma** in modo indipendente.

---

## Applicare l'ombra a una forma

Quando le persone chiedono “come **applico l'ombra** in C#?”, spesso hanno bisogno solo dell'attivazione della visibilità e di un colore. Il frammento seguente isola queste due righe:

```csharp
shape.ShadowFormat.Visible = true;          // Turns the shadow on
shape.ShadowFormat.Color   = Color.Black;   // Classic black drop shadow
```

> **Suggerimento:** Se punti a versioni più vecchie di Word (2003‑2007), usa colori standard. Alcuni valori ARGB esotici potrebbero essere ignorati dal renderer legacy.

---

## Come cambiare la trasparenza dell'ombra

La trasparenza è espressa come **float compreso tra 0 e 1**. Un valore di **0** indica un'ombra completamente opaca; **1** la rende invisibile. La maggior parte dei designer si aggira intorno a **0.2‑0.4** per un aspetto naturale.

```csharp
shape.ShadowFormat.Transparency = 0.35; // 35 % transparent
```

### Casi particolari

- **Valori negativi** – Aspose.Words li ridurrà a 0, ma è meglio validare l'input.  
- **Valori > 1** – Ridotti a 1, nascondendo effettivamente l'ombra.  

Se devi consentire agli utenti di scegliere una percentuale, convertila prima:

```csharp
float percent = 30;                     // User enters 30 %
shape.ShadowFormat.Transparency = percent / 100f;
```

---

## Come regolare la sfocatura (Size) dell'ombra

La proprietà **Size** controlla il raggio di sfocatura. Numeri più alti producono un'ombra più morbida e diffusa. È misurata in punti (pt), non in pixel.

```csharp
shape.ShadowFormat.Size = 10;  // A generous blur for a “soft” effect
```

#### Quando usare una sfocatura piccola vs. grande

- **Sfocatura piccola (2‑4 pt)** – Ideale per callout in stile UI dove vuoi un bordo nitido.  
- **Sfocatura grande (8‑12 pt)** – Funziona bene per report stampati o quando la forma è distante dallo sfondo.

---

## Aggiungere l'ombra alla forma – Posizionamento e direzione

L'ultimo elemento di **add shape shadow** è lo spostamento. Due proprietà lavorano insieme:

| Proprietà | Significato |
|----------|-------------|
| **Distance** | Quanto lontano l'ombra si trova dalla forma (in punti). |
| **Angle**    | Direzione dello spostamento (0° = destra, 90° = giù, 180° = sinistra, 270° = su). |

Esempio che crea un'ombra sottile in basso‑a‑destra:

```csharp
shape.ShadowFormat.Distance = 1.5; // Slight lift
shape.ShadowFormat.Angle    = 135; // Down‑left direction (135°)
```

Puoi sperimentare con gli angoli per simulare la luce proveniente da diverse direzioni. Un trucco comune è far scegliere all'utente una “fonte di luce” da un menu a tendina e mappare il valore a un angolo.

---

## Esempio completo (tutti i passaggi combinati)

Di seguito trovi lo stesso programma mostrato in precedenza, ma con **commenti aggiuntivi** che rendono la logica cristallina. Copialo in `Program.cs` ed eseguilo; il file di output conterrà una casella di testo con un'ombra perfettamente sintonizzata.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main()
        {
            // Load the source document (must contain at least one shape)
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Grab the first shape we encounter – usually a textbox or picture
            Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
            if (shape == null)
            {
                Console.WriteLine("No shape found in the document.");
                return;
            }

            // ---------- Apply Drop Shadow ----------
            shape.ShadowFormat.Visible = true;          // Turn it on
            shape.ShadowFormat.Color   = Color.DarkGray; // Soft dark colour

            // ---------- How to Change Transparency ----------
            shape.ShadowFormat.Transparency = 0.3; // 30 % transparent – looks natural

            // ---------- How to Adjust Blur ----------
            shape.ShadowFormat.Size = 6; // Moderate blur for a professional feel

            // ---------- Add Shape Shadow (position) ----------
            shape.ShadowFormat.Distance = 2; // Slight offset
            shape.ShadowFormat.Angle    = 45; // Diagonal down‑right

            // Save the result
            doc.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("Document saved with shadow. Open output.docx to verify.");
        }
    }
}
```

**Risultato atteso:** Apri `output.docx`. La prima casella di testo mostrerà un'ombra grigio scuro, 30 % trasparente, leggermente sfocata (size = 6) e spostata di 2 pt a un angolo di 45°. L'effetto è sottile ma evidente—esattamente ciò che la maggior parte dei designer UI cerca.

---

## Domande frequenti e problemi comuni

- **“Funziona anche con le immagini?”**  
  Sì. Qualsiasi `Shape`—sia una casella di testo, un'immagine o un'auto‑forma—esponi `ShadowFormat`. Basta sostituire la logica di recupero della forma con l'indice o il nome appropriato.

- **“E se il documento contiene più forme?”**  
  Scorri `doc.GetChildNodes(NodeType.Shape, true)` e applica le stesse impostazioni a ciascuna. Puoi anche filtrare per `shape.Name` o `shape

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}