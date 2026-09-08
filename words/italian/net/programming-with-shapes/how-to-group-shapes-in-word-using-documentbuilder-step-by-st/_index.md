---
category: general
date: 2026-09-08
description: Scopri come raggruppare le forme in Word con un DocumentBuilder, creare
  un documento Word vuoto e inserire una forma rettangolare in poche righe di codice
  C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create blank word doc
- insert rectangle shape word
- how to use documentbuilder
language: it
lastmod: 2026-09-08
og_description: Raggruppa le forme in Word usando DocumentBuilder. Questo tutorial
  mostra come creare un documento Word vuoto, inserire una forma rettangolare e combinare
  le forme in un GroupShape.
og_image_alt: Screenshot of a Word document showing grouped shapes – group shapes
  in Word example
og_title: Raggruppa le forme in Word con DocumentBuilder – esempio completo in C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to group shapes in Word with a DocumentBuilder, create a
    blank Word doc, and insert a rectangle shape in just a few lines of C# code.
  headline: How to group shapes in Word using DocumentBuilder – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Come raggruppare le forme in Word usando DocumentBuilder – guida passo passo
url: /it/net/programming-with-shapes/how-to-group-shapes-in-word-using-documentbuilder-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come raggruppare forme in Word usando DocumentBuilder – guida passo‑passo

Se hai bisogno di **raggruppare forme in Word** programmaticamente, questo tutorial mostra una soluzione completa in C#. Vedrai come **creare un documento Word vuoto**, usare **DocumentBuilder** e **inserire una forma rettangolare** prima di raggrupparla con un'ellisse. Il risultato è un unico `GroupShape` che puoi spostare, ridimensionare o stilizzare come un unico oggetto.

Questa guida copre tutto ciò che devi sapere per generare un documento Word con grafica raggruppata usando la libreria Aspose.Words per .NET. Alla fine dell’articolo avrai un progetto eseguibile che produce `GroupedShapes.docx` contenente un rettangolo e un’ellisse combinati in una singola forma.

## Prerequisiti

- .NET 6.0 o successivo (il codice funziona anche con .NET Framework 4.7.2+)
- Pacchetto NuGet Aspose.Words per .NET (`Aspose.Words`) – versione 23.12 o successiva
- Un IDE C# come Visual Studio 2022 o Visual Studio Code
- Familiarità di base con la sintassi C# e la programmazione orientata agli oggetti

> **Suggerimento professionale:** Installa il pacchetto NuGet dalla riga di comando per mantenere il progetto ordinato:  
> `dotnet add package Aspose.Words --version 23.12.0`

## Step 1: Create a blank Word document

La prima operazione è istanziare un oggetto `Document`, che rappresenta un file Word vuoto, e un `DocumentBuilder` che ti consente di aggiungere contenuti.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Step 1: Create a blank Word document and a DocumentBuilder
        Document document = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Why this matters:** `Document` fornisce il contenitore del file, mentre `DocumentBuilder` offre un’API fluida per inserire testo, immagini e forme. Senza un `DocumentBuilder` dovresti manipolare manualmente l’albero dei nodi del documento, operazione soggetta a errori.

## Step 2: Insert a rectangle shape

Un rettangolo è un blocco costruttivo comune per i diagrammi. Usa `InsertShape` con `ShapeType.Rectangle` e specifica larghezza e altezza in punti (1 pt ≈ 1/72 in).

```csharp
        // Step 2: Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;   // distance from the left margin (points)
        rectangleShape.Top = 50;    // distance from the top margin (points)
```

**Why this matters:** Impostare `Left` e `Top` posiziona il rettangolo con precisione sulla pagina, fondamentale quando lo raggrupperai successivamente con altre forme. Il metodo `InsertShape` aggiunge automaticamente la forma al paragrafo corrente.

## Step 3: Insert an ellipse shape

Successivamente, aggiungi un’ellisse che si posizionerà accanto al rettangolo.

```csharp
        // Step 3: Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;
```

**Why this matters:** L’uso di un `ShapeType` diverso dimostra come la stessa API `DocumentBuilder` possa creare grafiche variegate. Posizionare l’ellisse in modo che si sovrapponga al rettangolo rende evidente l’effetto di raggruppamento.

## Step 4: Group the two shapes

Un `GroupShape` funziona come un contenitore. Aggiungendo il rettangolo e l’ellisse come figli, si comportano come un unico oggetto.

```csharp
        // Step 4: Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        // Define the bounding rectangle that encloses all child shapes
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Insert the group into the document body
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);
```

**Why this matters:** La proprietà `Bounds` indica a Word dove il gruppo si trova sulla pagina. Aggiungendo le forme figlie, mantieni la loro formattazione individuale consentendo trasformazioni collettive (spostamento, rotazione, ridimensionamento).

## Step 5: Save the document

Infine, scrivi il documento su disco. Puoi modificare il percorso con qualsiasi cartella tu preferisca.

```csharp
        // Step 5: Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Quando apri `GroupedShapes.docx` in Microsoft Word, vedrai un rettangolo e un’ellisse raggruppati insieme. Selezionando il gruppo verranno evidenziate entrambe le forme, permettendoti di trascinarle o ridimensionarle come un’unica unità.

### Expected output

- Un file Word chiamato **GroupedShapes.docx**
- La prima pagina contiene un **rettangolo** (100 pt × 50 pt) nella posizione (50, 50)
- Un’**ellisse** (80 pt × 80 pt) nella posizione (200, 70)
- Entrambe le forme fanno parte di un **GroupShape** con una bounding box di 300 pt × 200 pt

## Common variations and edge cases

| Scenario | Adjustment |
|----------|------------|
| **Different page size** | Imposta `document.Sections[0].PageSetup.PageWidth` e `PageHeight` prima di inserire le forme. |
| **More than two shapes** | Crea oggetti `Shape` aggiuntivi e chiama `groupShape.AppendChild(newShape)` per ciascuno. |
| **Apply fill color** | `rectangleShape.FillColor = System.Drawing.Color.LightBlue;` |
| **Rotate the group** | `groupShape.Rotation = 45;` (gradi) |
| **Export to PDF** | Dopo aver salvato il DOCX, chiama `document.Save("GroupedShapes.pdf");` |

## Full source code (ready to run)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Create a blank Word document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;
        rectangleShape.Top = 50;

        // Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;

        // Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);

        // Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Copia il codice in un nuovo progetto console, ripristina il pacchetto NuGet Aspose.Words e avvia. La console confermerà la posizione del file e, aprendo il file, vedrai la grafica raggruppata.

## Conclusion

Ora sai **come raggruppare forme in Word** con `DocumentBuilder` di Aspose.Words. Il tutorial ha mostrato come creare un **documento Word vuoto**, **inserire una forma rettangolare**, aggiungere un’ellisse e combinarle in un `GroupShape`. Con queste basi potrai costruire diagrammi più complessi, flowchart o grafiche personalizzate direttamente da C#.

### What’s next?

- Esplora **come usare DocumentBuilder** per tabelle, intestazioni e piè di pagina.
- Combina le tecniche **insert rectangle shape Word** con caselle di testo per diagrammi annotati.
- Usa **create blank word doc** come modello per la generazione automatica di report.

Sentiti libero di sperimentare con colori, gradienti e forme aggiuntive. Buon coding!

## What Should You Learn Next?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell’API ed esplorare approcci alternativi nei tuoi progetti.

- [Crea forma di gruppo in un documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Inserisci forme in documenti Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Crea forma rettangolare in Word usando C# – Guida passo‑passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}