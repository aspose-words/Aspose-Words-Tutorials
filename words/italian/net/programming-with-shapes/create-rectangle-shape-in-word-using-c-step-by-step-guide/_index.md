---
category: general
date: 2026-01-03
description: Crea una forma rettangolare in Word con C# e aggiungi l'ombra alla forma.
  Scopri come inserire una forma in Word, aggiungere l'ombra alla forma e generare
  documenti Word programmaticamente.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- insert shape in word
- how to add shape
- c# generate word document
language: it
og_description: Crea una forma rettangolare in Word con C# e aggiungi un'ombra alla
  forma. Segui questa guida per inserire la forma in Word, configurare le ombre e
  generare documenti programmaticamente.
og_title: Crea forma rettangolare in Word usando C# – Tutorial completo
tags:
- C#
- Word Automation
- Aspose.Words
title: Crea una forma rettangolare in Word usando C# – Guida passo passo
url: /it/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea una forma rettangolare in Word usando C# – Tutorial completo

Hai mai avuto bisogno di **create rectangle shape** in un documento Word ma non sapevi da dove cominciare? Non sei solo—molti sviluppatori incontrano lo stesso ostacolo quando vogliono **add shadow to shape** per un aspetto curato. In questo tutorial ti guideremo passo passo per **insert shape in Word**, applicare un'ombra sottile e infine **c# generate word document** file che puoi distribuire agli utenti.

Copriremo tutto, dall'impostazione del progetto alla regolazione delle proprietà dell'ombra, e concluderemo con un esempio di codice pronto‑da‑eseguire. Niente superfluo, solo le parti pratiche che portano al risultato.

## Cosa imparerai

- Come **create rectangle shape** con Aspose.Words (o Open XML) in C#
- Le proprietà esatte necessarie per **add shadow to shape** per dare profondità
- Dove posizionare la forma usando `DocumentBuilder`
- Come salvare il file in modo che si apra correttamente in Microsoft Word
- Suggerimenti, insidie e variazioni per scenari reali

### Prerequisiti

- .NET 6.0 o versioni successive (il codice funziona su .NET Core e .NET Framework)
- Un pacchetto NuGet che può manipolare file Word – useremo **Aspose.Words for .NET** perché la sua API è concisa. Se preferisci Open XML SDK, i concetti sono gli stessi, solo le classi cambiano.
- Visual Studio, VS Code, o qualsiasi IDE C# che preferisci

> **Consiglio:** Se hai un budget limitato, Aspose offre una prova gratuita perfetta per imparare. Basta sostituire la riga di licenza con un commento durante il test.

## Passo 1: Installa la libreria di elaborazione Word

Per prima cosa, aggiungi la libreria al tuo progetto. Apri un terminale nella cartella della soluzione ed esegui:

```bash
dotnet add package Aspose.Words
```

Se stai usando l'Open XML SDK, il comando sarebbe `dotnet add package DocumentFormat.OpenXml`. Il resto di questa guida presuppone Aspose.Words, ma sostituire le chiamate API è semplice.

## Passo 2: Crea un nuovo documento vuoto

Ora che la libreria è pronta, possiamo **create rectangle shape** iniziando con un oggetto `Document` pulito. Consideralo come una tela fresca.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 2: Initialize a blank Word document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

## Passo 3: Inserisci la forma rettangolare

Con il builder a disposizione, possiamo **insert shape in Word**. Il metodo `InsertShape` accetta il tipo di forma e le sue dimensioni (larghezza, altezza) in punti.

```csharp
// Step 3: Insert a rectangle shape – 150pt wide, 80pt high
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

## Passo 4: Aggiungi l'ombra alla forma

Le ombre conferiscono alla forma una sensazione di profondità. L'oggetto `Shadow` ci permette di regolare finemente sfocatura, distanza, angolo, colore e trasparenza. Di seguito una configurazione completa che funziona bene per la maggior parte dei report.

```csharp
// Step 4: Configure a subtle shadow
rectangle.Shadow = new Shadow
{
    BlurRadius = 5.0,          // Soft edges
    Distance = 4.0,            // How far the shadow is offset
    Angle = 45,                // Direction in degrees (45° = down‑right)
    Color = Color.Black,       // Shadow color
    Transparency = 0.3         // 30 % transparent for a gentle look
};
```

**Perché questi valori?**  
- **BlurRadius** di `5.0` mantiene il bordo liscio senza apparire sfocato.  
- **Distance** di `4.0` sposta l'ombra giusto quanto per essere notabile.  
- **Angle** `45` imita l'illuminazione naturale dall'alto‑sinistra, una convenzione UI comune.  
- **Transparency** `0.3` impedisce che l'ombra sovrasti il riempimento della forma.

Se desideri un effetto più drammatico, aumenta `BlurRadius` e diminuisci `Transparency`. Per un sollevamento sottile, quasi invisibile, inverti questi valori.

## Passo 5: Salva il documento

Infine, scrivi il file su disco. Il metodo `Save` rileva il formato dall'estensione del file, quindi `.docx` ti fornisce il formato Word moderno.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\ShadowRectangle.docx";
document.Save(outputPath);
```

Apri `ShadowRectangle.docx` in Microsoft Word e vedrai un rettangolo nitido con un'ombra morbida—esattamente ciò che volevi quando hai chiesto “**how to add shape**” con una finitura professionale.

![Crea forma rettangolare con ombra in Word](placeholder-image.png "Crea forma rettangolare con ombra in Word")

*Testo alternativo immagine: crea forma rettangolare con ombra in Word*

## Esempio completo funzionante

Mettendo tutto insieme, ecco il programma completo, pronto‑da‑eseguire. Copia‑incolla in un'app console e premi **F5**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a rectangle shape (150pt × 80pt)
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Add a subtle shadow
            rect.Shadow = new Shadow
            {
                BlurRadius = 5.0,
                Distance = 4.0,
                Angle = 45,
                Color = Color.Black,
                Transparency = 0.3
            };

            // 4️⃣ Save the file
            string filePath = @"C:\Temp\ShadowRectangle.docx";
            doc.Save(filePath);

            System.Console.WriteLine($"Document saved to {filePath}");
        }
    }
}
```

### Risultato atteso

- Il `ShadowRectangle.docx` generato contiene **una forma rettangolare** centrata dove il cursore era posizionato.  
- Il rettangolo mostra una **ombra nera morbida, al 30 % di trasparenza** spostata a un angolo di 45°.  
- Nessun altro contenuto è aggiunto, mantenendo il file leggero e facile da incorporare in report più grandi.

## Domande comuni e casi particolari

### E se avessi bisogno di una forma diversa?

Sostituisci `ShapeType.Rectangle` con qualsiasi altro valore enum `ShapeType` (ad esempio `Ellipse`, `Triangle`). L'API dell'ombra funziona allo stesso modo, quindi puoi riutilizzare la configurazione.

### Come cambio il colore di riempimento?

```csharp
rect.FillColor = Color.LightBlue;   // or any System.Drawing.Color
```

### Posso aggiungere la forma a un paragrafo specifico?

Sì. Sposta il `DocumentBuilder` al paragrafo di destinazione con `builder.MoveToParagraph(index)` prima di chiamare `InsertShape`. Questo garantisce che la forma appaia esattamente dove ti serve.

### E per i formati Word più vecchi (.doc)?

Basta cambiare l'estensione:

```csharp
doc.Save(@"C:\Temp\ShadowRectangle.doc", SaveFormat.Doc);
```

La funzionalità ombra è supportata da Word 2003 in poi, quindi vedrai comunque l'effetto.

### Usare Open XML SDK invece di Aspose?

I passaggi rimangono: crea un `WordprocessingDocument`, aggiungi un elemento `Drawing`, imposta le proprietà `<a:shadow>`. L'XML è più verboso, ma gli stessi concetti (dimensione, sfocatura, distanza, angolo) si applicano.

## Consigli per evitare problemi

- **Non dimenticare la licenza** se usi una versione a pagamento di Aspose; altrimenti otterrai una filigrana.  
- **Le unità sono punti**, non pixel. Un tipico pixel dello schermo ≈ 0.75 pt, quindi regola le dimensioni di conseguenza.  
- **Le proprietà dell'ombra sono ignorate** se il `WrapType` della forma è impostato a `Inline`. Usa `WrapType = WrapType.Square` per forme fluttuanti che rispettano il rendering dell'ombra.  
- **Salvare su una condivisione di rete** può richiedere permessi adeguati; testa sempre il percorso prima.

## Conclusione

Ora sai come **create rectangle shape** in un documento Word usando C#, **add shadow to shape**, e **c# generate word document** file che appaiono curati fin da subito. I passaggi fondamentali—installare la libreria, istanziare `Document`, inserire la forma, configurare l'ombra e salvare—sono facili da ricordare e adattabili ad altre forme, colori o anche dati dinamici.

Cosa fare dopo? Prova a sovrapporre più forme, incorporare immagini o generare un report completo con tabelle e grafici. Puoi anche esplorare la formattazione condizionale—cambiando l'intensità dell'ombra in base ai valori dei dati—per rendere i tuoi documenti non solo funzionali ma anche visivamente accattivanti.

Sentiti libero di sperimentare, e se incontri problemi, lascia un commento qui sotto. Buon coding, e che i tuoi documenti Word abbiano sempre quella perfetta ombra!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}