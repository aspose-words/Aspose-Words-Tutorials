---
category: general
date: 2025-12-08
description: Aggiungi rapidamente l'ombra a una forma con Aspose.Words. Scopri come
  creare un documento Word usando Aspose, come aggiungere l'ombra a una forma e come
  applicare la trasparenza dell'ombra in C#.
draft: false
keywords:
- add shadow to shape
- create word document using aspose
- how to add shape shadow
- apply shadow transparency
language: it
og_description: Aggiungi un'ombra alla forma in un file Word usando Aspose.Words.
  Questa guida passo‑passo mostra come creare un documento, aggiungere una forma e
  applicare la trasparenza dell'ombra.
og_title: Aggiungi ombra alla forma – Tutorial Aspose.Words C#
tags:
- Aspose.Words
- C#
- Word Automation
title: Aggiungi ombra alla forma in un documento Word – Guida completa ad Aspose.Words
url: /italian/net/images-and-shapes/add-shadow-to-shape-in-a-word-document-complete-aspose-words/
---

{{< layout-start >}}

{{< layout-start >}}

# Aggiungere Ombra alla Forma – Guida Completa a Aspose.Words

Hai mai avuto bisogno di **aggiungere ombra alla forma** in un file Word ma non eri sicuro di quali chiamate API utilizzare? Non sei solo. Molti sviluppatori si trovano in difficoltà quando provano per la prima volta a dare a un rettangolo o a qualsiasi elemento di disegno una corretta ombra portata, soprattutto quando lavorano con Aspose.Words per .NET.

In questo tutorial passeremo in rassegna tutto ciò che devi sapere: dalla **creazione di un documento Word usando Aspose** alla configurazione dell'ombra, alla regolazione del suo blur, distanza, angolo e persino **l'applicazione della trasparenza dell'ombra**. Alla fine avrai un programma C# pronto all'uso che produce un file `.docx` con un rettangolo elegantemente ombreggiato—senza dover intervenire manualmente in Word.

---

## Cosa Imparerai

- Come configurare un progetto Aspose.Words in Visual Studio.  
- I passaggi esatti per **creare un documento Word usando Aspose** e inserire una forma.  
- **Come aggiungere l'ombra alla forma** con pieno controllo su blur, distanza, angolo e trasparenza.  
- Suggerimenti per risolvere problemi comuni (ad esempio, licenza mancante, unità errate).  
- Un esempio di codice completo, pronto per il copia‑incolla, che puoi eseguire subito.

> **Prerequisiti:** .NET 6+ (o .NET Framework 4.7.2+), una licenza valida di Aspose.Words (o la versione di prova gratuita) e una conoscenza di base di C#.

---

## Passo 1 – Configura il tuo progetto e aggiungi Aspose.Words

Prima di tutto. Apri Visual Studio, crea una nuova **Console App (.NET Core)** e aggiungi il pacchetto NuGet Aspose.Words:

```bash
dotnet add package Aspose.Words
```

> **Consiglio professionale:** Se hai un file di licenza (`Aspose.Words.lic`), copialo nella radice del progetto e caricalo all'avvio. Questo evita la filigrana che appare nella modalità di valutazione gratuita.

```csharp
// Load the license (optional but recommended)
var license = new Aspose.Words.License();
license.SetLicense("Aspose.Words.lic");
```

---

## Passo 2 – Crea un nuovo documento vuoto

Ora creiamo effettivamente **un documento Word usando Aspose**. Questo oggetto servirà da tela per la nostra forma.

```csharp
// Step 2: Initialize a new blank document
Document doc = new Document();   // Represents an empty .docx file
```

La classe `Document` è il punto di ingresso per tutto il resto—paragrafi, sezioni e, naturalmente, oggetti di disegno.

---

## Passo 3 – Inserisci una forma rettangolare

Con il documento pronto, possiamo aggiungere una forma. Qui scegliamo un semplice rettangolo, ma la stessa logica funziona per cerchi, linee o poligoni personalizzati.

```csharp
// Step 3: Create a rectangular shape that will hold the shadow
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 150,   // Width in points (1 point = 1/72 inch)
    Height = 100    // Height in points
};
```

> **Perché una forma?** In Aspose.Words un oggetto `Shape` può contenere testo, immagini o fungere semplicemente da elemento decorativo. Aggiungere un'ombra a una forma è molto più semplice che cercare di manipolare una cornice immagine.

---

## Passo 4 – Configura l'ombra (Aggiungere ombra alla forma)

Questo è il cuore del tutorial—**come aggiungere l'ombra alla forma** e perfezionare il suo aspetto. La proprietà `ShadowFormat` ti offre pieno controllo.

```csharp
// Step 4: Enable the shadow and configure its appearance
rectangle.ShadowFormat.Visible       = true;   // Turn the shadow on
rectangle.ShadowFormat.Blur          = 5.0;    // Blur radius – higher = softer edges
rectangle.ShadowFormat.Distance      = 3.0;    // Offset distance from the shape
rectangle.ShadowFormat.Angle         = 45;     // Direction in degrees (0 = right, 90 = down)
rectangle.ShadowFormat.Transparency  = 0.3;    // 30 % transparent – this is how we **apply shadow transparency**
```

### Cosa fa ciascuna proprietà

| Proprietà | Effetto | Valori tipici |
|-----------|---------|----------------|
| **Visible** | Attiva/disattiva l'ombra. | `true` / `false` |
| **Blur** | Ammorbidisce i bordi dell'ombra. | `0` (duro) a `10` (molto morbido) |
| **Distance** | Sposta l'ombra lontano dalla forma. | `1`–`5` punti è comune |
| **Angle** | Controlla la direzione dello spostamento. | `0`–`360` gradi |
| **Transparency** | Rende l'ombra parzialmente trasparente. | `0` (opaco) a `1` (invisibile) |

> **Caso limite:** Se imposti `Transparency` a `1`, l'ombra scompare completamente—utile per attivarla/disattivarla programmaticamente.

---

## Passo 5 – Aggiungi la forma al documento

Ora colleghiamo la forma al primo paragrafo del corpo del documento. Aspose crea automaticamente un paragrafo se non ne esiste.

```csharp
// Step 5: Append the shape to the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);
```

Se il tuo documento contiene già del contenuto, puoi inserire la forma in qualsiasi nodo usando `InsertAfter` o `InsertBefore`.

---

## Passo 6 – Salva il documento

Infine, scrivi il file su disco. Puoi scegliere qualsiasi formato supportato (`.docx`, `.pdf`, `.odt`, ecc.), ma per questo tutorial rimarremo al formato Word nativo.

```csharp
// Step 6: Save the document with the shadowed shape
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Apri il file risultante `ShadowedShape.docx` in Microsoft Word e vedrai un rettangolo con un'ombra morbida a 45 gradi, trasparente al 30 %—esattamente come abbiamo configurato.

---

## Esempio completo funzionante

Di seguito trovi il programma **completo, pronto per il copia‑incolla** che incorpora tutti i passaggi sopra. Salvalo come `Program.cs` ed eseguilo con `dotnet run`.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // OPTIONAL: Load Aspose.Words license (remove if using trial)
        // -------------------------------------------------
        try
        {
            var license = new License();
            license.SetLicense("Aspose.Words.lic");
        }
        catch (Exception ex)
        {
            Console.WriteLine("License not found – running in evaluation mode: " + ex.Message);
        }

        // -------------------------------------------------
        // 1. Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // 2. Insert a rectangle shape
        // -------------------------------------------------
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 150,
            Height = 100
        };

        // -------------------------------------------------
        // 3. Configure the shadow – this is where we **add shadow to shape**
        // -------------------------------------------------
        rectangle.ShadowFormat.Visible      = true;   // Show the shadow
        rectangle.ShadowFormat.Blur         = 5.0;    // Soft edges
        rectangle.ShadowFormat.Distance     = 3.0;    // Offset distance
        rectangle.ShadowFormat.Angle        = 45;     // Direction in degrees
        rectangle.ShadowFormat.Transparency = 0.3;    // 30 % transparent (apply shadow transparency)

        // -------------------------------------------------
        // 4. Add the shape to the document
        // -------------------------------------------------
        doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);

        // -------------------------------------------------
        // 5. Save the file
        // -------------------------------------------------
        string outFile = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
        doc.Save(outFile);
        Console.WriteLine($"Document created successfully: {outFile}");
    }
}
```

**Output previsto:** Un file chiamato `ShadowedShape.docx` contenente un singolo rettangolo con una leggera ombra sfumata semi‑trasparente inclinata a 45°.

---

## Varianti e consigli avanzati

### Cambiare il colore dell'ombra

Per impostazione predefinita l'ombra eredita il colore di riempimento della forma, ma puoi impostare un colore personalizzato:

```csharp
rectangle.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### Più forme con ombre diverse

Se ti servono diverse forme, basta ripetere i passaggi di creazione e configurazione. Ricorda di assegnare a ogni forma un nome univoco se prevedi di farvi riferimento in seguito.

### Esportare in PDF con ombre preservate

Aspose.Words preserva gli effetti di ombra quando salva in PDF:

```csharp
doc.Save("ShadowedShape.pdf");
```

### Problemi comuni

| Sintomo | Probabile causa | Soluzione |
|---------|-----------------|-----------|
| Ombra non visibile | `ShadowFormat.Visible` lasciato a `false` | Impostare a `true`. |
| L'ombra appare troppo dura | `Blur` impostato a `0` | Aumentare `Blur` a 3–6. |
| L'ombra scompare in PDF | Uso di una vecchia versione di Aspose.Words (< 22.9) | Aggiornare alla libreria più recente. |

---

## Conclusione

Abbiamo coperto **come aggiungere l'ombra alla forma** usando Aspose.Words, dall'inizializzazione di un documento alla regolazione fine di blur, distanza, angolo e **l'applicazione della trasparenza dell'ombra**. L'esempio completo dimostra un approccio pulito, pronto per la produzione, che puoi adattare a qualsiasi forma o layout di documento.

Hai domande su **create word document using aspose** per scenari più complessi—come tabelle con ombre o forme guidate da dati dinamici? Lascia un commento qui sotto o consulta i tutorial correlati su gestione delle immagini e formattazione dei paragrafi in Aspose.Words.

Buon coding e divertiti a dare ai tuoi documenti Word quel tocco visivo in più! 

--- 

![esempio di aggiunta ombra alla forma](shadowed_shape.png "esempio di aggiunta ombra alla forma")

{{< layout-end >}}

{{< layout-end >}}