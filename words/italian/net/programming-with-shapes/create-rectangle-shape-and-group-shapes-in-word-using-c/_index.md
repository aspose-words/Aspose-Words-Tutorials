---
category: general
date: 2026-09-08
description: Crea una forma rettangolare in un documento Word con C#. Impara a impostare
  le dimensioni della forma, raggruppare più forme e creare un documento Word vuoto
  programmaticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- set shape size
- group multiple shapes
- create blank word document
language: it
lastmod: 2026-09-08
og_description: Crea una forma rettangolare in un documento Word con C#. Questa guida
  mostra come impostare le dimensioni della forma, raggruppare più forme e creare
  un documento Word vuoto programmaticamente.
og_image_alt: Screenshot showing how to create rectangle shape in a Word document
  using C#
og_title: Crea forma rettangolare e raggruppa forme in Word usando C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Create rectangle shape in a Word document with C#. Learn to set shape
    size, group multiple shapes, and create blank Word document programmatically.
  headline: Create rectangle shape and group shapes in Word using C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Crea una forma rettangolare e raggruppa le forme in Word usando C#
url: /it/net/programming-with-shapes/create-rectangle-shape-and-group-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea forma rettangolare e raggruppa forme in Word usando C#

Se hai bisogno di **creare una forma rettangolare** all'interno di un file Word, questo tutorial ti fornisce una soluzione completa, pronta all'uso. Vedrai come impostare le dimensioni della forma, raggruppare più forme e creare un documento Word vuoto da zero—tutto con la libreria Aspose.Words per .NET.

Lavorare programmaticamente con i documenti Word spesso sembra un esercizio di equilibrio tra molti piccoli dettagli. Alla fine di questa guida avrai un unico metodo che produce un file `.docx` contenente un rettangolo e un'ellisse raggruppati insieme, pronti per ulteriori modifiche o stampe.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* .NET 6.0 o successivo (il codice funziona anche con .NET Framework 4.6+)
* Una copia con licenza di **Aspose.Words per .NET** (puoi usare una chiave di valutazione gratuita)
* Un IDE come Visual Studio 2022 o Visual Studio Code
* Familiarità di base con la sintassi C#

Non sono richiesti pacchetti NuGet aggiuntivi oltre a `Aspose.Words`.

## Passo 1: Crea un documento Word vuoto

Il primo passo è creare un documento vuoto che ospiterà le forme. Questo soddisfa il requisito di *creare documento Word vuoto*.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty Word document
Document doc = new Document();

// The document already contains one section and one empty paragraph
// You can add additional sections later if needed
```

Creare un documento vuoto ti fornisce una tela pulita. L'oggetto `Document` rappresenta l'intero file `.docx`, e il suo `FirstSection.Body.FirstParagraph` è il punto di inserimento predefinito per i nuovi nodi.

## Passo 2: Crea una forma rettangolare

Ora puoi aggiungere il rettangolo. È qui che avviene l'operazione **creare forma rettangolare**.

```csharp
// Initialize a DocumentBuilder to simplify node insertion
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape instance
Shape rectangle = new Shape(doc, ShapeType.Rectangle);

// Set the rectangle's size (width and height) and position
rectangle.Width  = 100;   // points; 1 point = 1/72 inch
rectangle.Height = 50;
rectangle.Left   = 10;    // distance from the left edge of the container
rectangle.Top    = 20;    // distance from the top edge of the container

// Optional: give the rectangle a visible border
rectangle.StrokeColor = Color.Blue;
rectangle.FillColor   = Color.LightGray;
```

Impostare direttamente le dimensioni risponde alla parola chiave **set shape size**. Tutti i valori di dimensione sono espressi in punti, il che garantisce un controllo preciso su come la forma appare nel documento finale.

## Passo 3: Crea una forma aggiuntiva (ellisse)

Un caso d'uso tipico è combinare diverse forme. Qui aggiungiamo un'ellisse che in seguito condividerà lo stesso contenitore.

```csharp
// Create an ellipse shape instance
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width  = 80;
ellipse.Height = 80;
ellipse.Left   = 120;   // Position it to the right of the rectangle
ellipse.Top    = 30;

// Give the ellipse a distinct border and fill
ellipse.StrokeColor = Color.DarkGreen;
ellipse.FillColor   = Color.LightYellow;
```

Entrambe le forme sono ancora indipendenti a questo punto. Il passo successivo mostra come **raggruppare più forme** insieme.

## Passo 4: Raggruppa le forme in Word

Raggruppare le forme ti permette di spostarle, ridimensionarle o formattarle come un'unica unità. Questo soddisfa i requisiti **group shapes in word** e **group multiple shapes**.

```csharp
// Create a GroupShape container that will hold the rectangle and ellipse
GroupShape group = new GroupShape(doc);

// Define the container's bounding box – it must be large enough for all children
group.Bounds = new RectangleF(0, 0, 300, 200);

// Append the group to the document's first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(group);

// Add the rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

La proprietà `GroupShape.Bounds` determina il sistema di coordinate per le forme figlie. Posizionando rettangolo ed ellisse nello stesso `GroupShape`, potrai successivamente spostarli o ruotarli insieme con una singola chiamata.

## Passo 5: Salva il documento

Infine, scrivi il documento su disco. Il file conterrà le forme raggruppate che hai appena creato.

```csharp
// Choose an output path – ensure the directory exists and you have write permission
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");

// Save the document in DOCX format
doc.Save(outputPath);
```

Dopo aver eseguito il programma, apri `GroupedShapes.docx` in Microsoft Word. Dovresti vedere un rettangolo e un'ellisse raggruppati; selezionare una forma seleziona anche l'altra, confermando che il raggruppamento è riuscito.

## Codice sorgente completo

Copia il programma completo seguente in un nuovo progetto console‑app e avvialo. Non è necessario alcun codice aggiuntivo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
using System.Drawing;
using System.IO;

class Program
{
    static void Main()
    {
        // Step 1: create a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: create rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 100,
            Height = 50,
            Left   = 10,
            Top    = 20,
            StrokeColor = Color.Blue,
            FillColor   = Color.LightGray
        };

        // Step 3: create ellipse shape
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width  = 80,
            Height = 80,
            Left   = 120,
            Top    = 30,
            StrokeColor = Color.DarkGreen,
            FillColor   = Color.LightYellow
        };

        // Step 4: group the shapes
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new RectangleF(0, 0, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);
        group.AppendChild(rectangle);
        group.AppendChild(ellipse);

        // Step 5: save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Output previsto

L'esecuzione del programma produce `GroupedShapes.docx`. L'apertura del file in Word mostra:

* Un **rettangolo** (100 pt × 50 pt) con bordo blu e riempimento grigio chiaro.
* Un'**ellisse** (80 pt × 80 pt) con bordo verde scuro e riempimento giallo chiaro.
* Entrambe le forme sono all'interno di un unico gruppo, quindi spostare una sposta anche l'altra.

## Domande comuni e casi limite

| Domanda | Risposta |
|----------|--------|
| **Posso aggiungere più di due forme al gruppo?** | Sì. Crea ulteriori oggetti `Shape` e chiama `group.AppendChild(yourShape)` per ciascuna. |
| **E se devo ruotare il gruppo?** | Imposta `group.RotationAngle = 45;` (gradi). Tutte le forme figlie ruotano insieme. |
| **È possibile raggruppare le forme dopo aver salvato il documento?** | Devi modificare la struttura del documento prima del salvataggio; altrimenti dovresti caricare il file, individuare le forme e ricreare il gruppo. |
| **Devo rilasciare qualche oggetto?** | Aspose.Words gestisce le proprie risorse, ma dovresti chiudere gli oggetti `FileStream` se apri stream manualmente. |
| **Il codice funziona con il formato .doc (binario)?** | Sì, cambia `doc.Save("output.doc")`. Il comportamento di raggruppamento è identico. |

## Conclusione

Ora sai come **creare forma rettangolare**, **impostare le dimensioni della forma** e **raggruppare più forme** all'interno di un file Word usando C#. Questo approccio ti consente di costruire programmaticamente diagrammi complessi, filigrane o report basati su template senza dover intervenire manualmente.

### Passaggi successivi

* Approfondisci **group shapes in word** aggiungendo caselle di testo o immagini allo stesso gruppo.
* Usa il pattern `SetShapeSize` per calcolare dinamicamente le dimensioni in base al layout della pagina.
* Combina questa tecnica con i campi di stampa unione per generare documenti personalizzati su larga scala.

Sentiti libero di sperimentare con diversi tipi di forma, colori e trasformazioni di gruppo. Buona programmazione!

## Cosa dovresti imparare dopo?

I tutorial seguenti coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑a‑passo per aiutarti a padroneggiare ulteriori funzionalità dell'API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea forma di gruppo in documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Crea documento Word vuoto con forma rettangolare ombreggiata – Guida passo‑a‑passo](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Crea documento Word con un rettangolo ombreggiato – Guida passo‑a‑passo](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}