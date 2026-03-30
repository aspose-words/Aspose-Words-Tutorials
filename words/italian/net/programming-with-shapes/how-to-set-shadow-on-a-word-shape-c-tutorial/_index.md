---
category: general
date: 2026-03-30
description: Scopri come impostare l'ombra su una forma di Word usando C#. Questa
  guida mostra anche come aggiungere l'ombra alla forma, regolare la trasparenza della
  forma e aggiungere l'ombra al rettangolo.
draft: false
keywords:
- how to set shadow
- adjust shape transparency
- add shape shadow
- how to add shadow
- add rectangle shadow
language: it
og_description: Come impostare l'ombra su una forma di Word in C#? Segui questa guida
  passo passo per aggiungere l'ombra alla forma, regolare la trasparenza della forma
  e aggiungere l'ombra al rettangolo.
og_title: Come impostare l'ombra su una forma di Word – Tutorial C#
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: Come impostare l'ombra su una forma di Word – Tutorial C#
url: /it/net/programming-with-shapes/how-to-set-shadow-on-a-word-shape-c-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come impostare l'ombra su una forma Word – Tutorial C#

Ti sei mai chiesto **come impostare l'ombra** su una forma all'interno di un documento Word senza impazzire con l'interfaccia? Non sei l'unico. In molti report o presentazioni di marketing un'ombra leggera fa risaltare un rettangolo, e farlo programmaticamente fa risparmiare ore.

In questa guida percorreremo un esempio completo, pronto all'uso, che non solo mostra **come impostare l'ombra**, ma copre anche **add shape shadow**, **adjust shape transparency** e persino **add rectangle shadow** per quelle classiche caselle di richiamo. Alla fine avrai un file Word (`output.docx`) dall'aspetto curato e comprenderai perché ogni proprietà è importante.

## Prerequisiti

- .NET 6+ (o .NET Framework 4.7.2) con compilatore C#  
- Pacchetto NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- Familiarità di base con C# e il modello a oggetti di Word  

Non sono necessarie librerie aggiuntive—tutto è contenuto in Aspose.Words.

---

## Come impostare l'ombra su una forma Word in C#

Di seguito il file sorgente completo. Salvalo come `Program.cs` ed eseguilo dal tuo IDE o con `dotnet run`. Il codice carica un `.docx` esistente, trova la prima forma (un rettangolo per impostazione predefinita), attiva la sua ombra, regola alcuni parametri visivi e salva il risultato.

```csharp
// Program.cs
using System;
using System.Drawing;               // For Color
using Aspose.Words;                // Core document API
using Aspose.Words.Drawing;        // Shape and shadow classes

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the shape.
        // Replace YOUR_DIRECTORY with the folder where your files live.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the first shape in the document.
        // If you have multiple shapes, you can loop or use GetChild with a different index.
        Shape rectangleShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (rectangleShape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx contains at least one shape.");
            return;
        }

        // 3️⃣ Enable the shape's shadow and choose a base color.
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Black;   // You can pick any System.Drawing.Color

        // 4️⃣ Fine‑tune the shadow appearance.
        rectangleShape.ShadowFormat.Transparency = 0.3;     // 30 % transparent (adjust shape transparency)
        rectangleShape.ShadowFormat.OffsetX = 5;           // Horizontal offset in points
        rectangleShape.ShadowFormat.OffsetY = 5;           // Vertical offset in points
        rectangleShape.ShadowFormat.BlurRadius = 4;       // Soft edge radius

        // 5️⃣ Save the updated document.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Shadow applied! Check {outputPath}");
    }
}
```

> **Ciò che vedrai** – Il rettangolo ora presenta un'ombra nera con il 30 % di trasparenza, spostata di 5 pt a destra e in basso, con una leggera sfocatura. Apri `output.docx` in Word per verificare.

## Regolare la trasparenza della forma – Perché è importante

La trasparenza non è solo una manopola estetica; influisce sulla leggibilità. Un valore 0.0 rende l'ombra completamente opaca, mentre 1.0 la nasconde del tutto. Nell'esempio sopra abbiamo usato `0.3` per ottenere un effetto sottile che funziona sia su sfondi chiari che scuri. Sentiti libero di sperimentare:

```csharp
rectangleShape.ShadowFormat.Transparency = 0.1; // Almost solid shadow
rectangleShape.ShadowFormat.Transparency = 0.6; // Very faint
```

Ricorda, **adjust shape transparency** può essere applicato anche al colore di riempimento della forma se ti serve un rettangolo semi‑trasparente.

## Aggiungere ombra alla forma su diversi oggetti

Il codice che abbiamo usato si rivolge a un oggetto `Shape`, ma le stesse proprietà di `ShadowFormat` esistono su **Image**, **Chart** e persino su **TextBox**. Ecco un modello rapido da copiare‑incollare:

```csharp
// Assuming 'image' is an Aspose.Words.Drawing.Image object
image.ShadowFormat.Visible = true;
image.ShadowFormat.Color = Color.Gray;
image.ShadowFormat.OffsetX = 3;
image.ShadowFormat.OffsetY = 3;
image.ShadowFormat.BlurRadius = 2;
```

Quindi, sia che tu voglia **add shape shadow** a un logo o a un'icona decorativa, l'approccio rimane identico.

## Come aggiungere l'ombra a qualsiasi forma – Casi particolari

1. **Forma senza riquadro di delimitazione** – Alcune forme Word (come scarabocchi liberi) non supportano le ombre. Tentare di impostare `ShadowFormat.Visible` fallirà silenziosamente. Controlla `shape.IsShadowSupported` se ti serve sicurezza.  
2. **Versioni Word più vecchie** – Le proprietà dell'ombra corrispondono a funzionalità Word 2007+. Se devi supportare Word 2003, l'ombra verrà ignorata all'apertura del file.  
3. **Ombre multiple** – Aspose.Words attualmente supporta una sola ombra per forma. Se ti serve un effetto a doppio strato, duplica la forma, spostala e applica impostazioni di ombra diverse.

## Aggiungere ombra al rettangolo – Caso d'uso reale

Immagina di generare un report trimestrale e che ogni intestazione di sezione sia un rettangolo colorato. Aggiungere un **add rectangle shadow** conferisce alla pagina un aspetto “a scheda”. I passaggi sono identici all'esempio base; assicurati solo che la forma target sia effettivamente un rettangolo (`shape.ShapeType == ShapeType.Rectangle`). Se devi creare il rettangolo da zero, vedi lo snippet qui sotto:

```csharp
// Create a new rectangle shape programmatically
Shape newRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,
    Height = 50,
    WrapType = WrapType.Inline
};
newRect.FillColor = Color.LightBlue;

// Apply shadow (same settings as before)
newRect.ShadowFormat.Visible = true;
newRect.ShadowFormat.Color = Color.Black;
newRect.ShadowFormat.Transparency = 0.25;
newRect.ShadowFormat.OffsetX = 4;
newRect.ShadowFormat.OffsetY = 4;
newRect.ShadowFormat.BlurRadius = 3;

// Insert into the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(newRect);
```

Eseguire il programma completo con questa aggiunta ti darà un nuovo rettangolo che già possiede l'effetto **add rectangle shadow** desiderato.

---

![Word shape with shadow](placeholder-image.png){alt="come impostare l'ombra su una forma in Word"}

*Figura: Il rettangolo dopo l'applicazione delle impostazioni dell'ombra.*

## Riepilogo rapido (Cheat sheet a punti)

- **Carica** il documento con `new Document(path)`.  
- **Individua** la forma tramite `doc.GetChild(NodeType.Shape, index, true)`.  
- **Abilita** l'ombra: `shape.ShadowFormat.Visible = true;`.  
- **Imposta** il colore con qualsiasi `System.Drawing.Color`.  
- **Regola** la trasparenza (`0.0–1.0`) per controllare l'opacità.  
- **OffsetX / OffsetY** spostano l'ombra orizzontalmente/verticalmente (punti).  
- **BlurRadius** ammorbidisce il bordo—valori più alti = ombra più sfocata.  
- **Salva** il file e aprilo in Word per vedere il risultato.

## Cosa provare dopo?

- **Colori dinamici** – Preleva il colore dell'ombra da un tema o da un input utente.  
- **Ombre condizionali** – Applica un'ombra solo quando la larghezza della forma supera una soglia.  
- **Elaborazione batch** – Scorri tutte le forme in un documento e **add shape shadow** automaticamente.  

Se hai seguito i passaggi, ora sai **come impostare l'ombra**, come **regolare la trasparenza della forma** e come **add rectangle shadow** per una finitura professionale. Sperimenta, rompi le cose e poi riparale—il coding è il miglior insegnante.

---

*Buon coding! Se questo tutorial ti è stato utile, lascia un commento o condividi i tuoi trucchi per le ombre. Più impariamo gli uni dagli altri, più belli saranno i nostri documenti Word.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}