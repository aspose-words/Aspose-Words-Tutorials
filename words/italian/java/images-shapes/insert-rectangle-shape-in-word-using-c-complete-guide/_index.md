---
category: general
date: 2026-08-04
description: Inserisci una forma rettangolare in un documento Word con C#. Scopri
  come raggruppare le forme in Word, salvare il documento come docx e utilizzare DocumentBuilder
  per layout avanzati.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to group shapes
- group shapes in word
- save document as docx
- how to use builder
language: it
lastmod: 2026-08-04
og_description: Inserisci una forma rettangolare in un file Word usando C# e poi raggruppa
  le forme per layout avanzati. Questo tutorial copre anche il salvataggio del documento
  come docx e l'uso efficiente di DocumentBuilder.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with C# DocumentBuilder
og_title: Inserisci forma rettangolare in Word – Guida passo‑passo C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Insert rectangle shape in a Word document with C#. Learn how to group
    shapes in Word, save document as docx, and use DocumentBuilder for advanced layouts.
  headline: Insert rectangle shape in Word using C# – complete guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Inserire una forma rettangolare in Word usando C# – guida completa
url: /it/java/images-shapes/insert-rectangle-shape-in-word-using-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserire forma rettangolare in Word usando C# – guida completa

Se hai bisogno di **inserire una forma rettangolare** in un documento Word usando C#, questo tutorial ti mostra esattamente come fare. Imparerai anche **come raggruppare le forme** in Word, **salvare il documento come docx**, e **come usare Builder** per un codice pulito e manutenibile.

Lavorare con le forme è una necessità comune quando si generano report, certificati o layout personalizzati in modo programmatico. Alla fine di questa guida avrai un esempio completamente eseguibile che crea un rettangolo, aggiunge un'ellisse, le raggruppa e salva il risultato come file DOCX.

## Prerequisiti

* .NET 6.0 o versioni successive installate  
* Visual Studio 2022 (o qualsiasi IDE che supporti C#)  
* La libreria **Aspose.Words for .NET** (disponibile via NuGet)  

Puoi aggiungere la libreria con il seguente comando:

```bash
dotnet add package Aspose.Words
```

## Inserire forma rettangolare con DocumentBuilder

Il primo passo è creare un nuovo `Document` e un `DocumentBuilder`. Il builder ti fornisce un'API fluida per inserire contenuti, incluse le forme.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document.
        Document document = new Document();

        // Initialize the builder that will edit the document.
        DocumentBuilder builder = new DocumentBuilder(document);
```

L'istanza di `DocumentBuilder` è l'oggetto principale che utilizzerai per **inserire una forma rettangolare** e altri elementi. Tiene traccia della posizione corrente del cursore all'interno del documento, così ogni inserimento avviene esattamente dove ti serve.

## Come inserire una forma rettangolare

Con il builder pronto, chiama `InsertShape`. Specifica il `ShapeType`, la larghezza e l'altezza in punti (1 pt ≈ 1/72 in).

```csharp
        // Insert a rectangle of 100 pt width and 50 pt height.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
```

*Perché è importante*: impostare `FillColor` e `StrokeColor` rende il rettangolo visivamente distinto, il che aiuta quando lo raggruppi successivamente con altre forme.

## Come raggruppare le forme in Word

Raggruppare le forme ti consente di spostare, ruotare o formattare più oggetti come un'unica entità. Dopo aver inserito il rettangolo, aggiungi un'altra forma (un'ellisse in questo esempio) e poi crea un `GroupShape`.

```csharp
        // Insert an ellipse of 80 pt diameter.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // Insert an empty group container.
        GroupShape groupShape = builder.InsertGroupShape();

        // Add the rectangle and ellipse to the group.
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
```

La chiamata `InsertGroupShape` crea un segnaposto che può contenere un numero qualsiasi di forme figlie. Aggiungendo il rettangolo e l'ellisse, raggruppi effettivamente **le forme in Word**. Il gruppo si comporta come una singola forma—puoi riposizionarlo, applicare un bordo o ridimensionarlo senza influire sul layout interno di ciascun figlio.

### Consiglio professionale

Dopo aver raggruppato, puoi modificare la posizione del gruppo rispetto alla pagina:

```csharp
        // Move the whole group 150 pt right and 100 pt down.
        groupShape.Left = 150;
        groupShape.Top = 100;
```

## Salva il documento come docx

Una volta che le forme sono sistemate, devi persistere il file. Il metodo `Document.Save` determina automaticamente il formato dall'estensione del file. Per **salvare il documento come docx**, passa un percorso che termina con `.docx`.

```csharp
        // Save the document to the output folder.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

Eseguendo il programma viene creato `output.docx`. Apri il file in Microsoft Word e vedrai un rettangolo azzurro chiaro e un'ellisse corallo chiaro raggruppati insieme. Puoi fare clic sul gruppo e spostarlo come un unico oggetto.

## Come utilizzare DocumentBuilder in modo efficace

`DocumentBuilder` è più di un inseritore di forme; gestisce anche testo, tabelle, intestazioni e piè di pagina. Quando combini la creazione di forme con il testo, ricorda di resettare il cursore se devi inserire contenuti altrove:

```csharp
        // Move the cursor to a new paragraph after the group.
        builder.Writeln(); // Inserts a line break.
        builder.Font.Size = 12;
        builder.Writeln("Shapes have been added and grouped successfully.");
```

Mantenere esplicito lo stato del builder evita sovrascritture accidentali e rende il codice più facile da mantenere.

## Casi limite e variazioni

| Situazione | Approccio consigliato |
|-----------|----------------------|
| **Più di due forme** | Inserisci ogni forma, poi chiama `AppendChild` per ogni forma prima di salvare. |
| **Gruppi nidificati** | Crea un gruppo, aggiungi le forme, poi inserisci quel gruppo in un altro `GroupShape`. |
| **Unità di misura diverse** | Usa `builder.ConvertPixelsToPoints` se hai dimensioni in pixel. |
| **Compatibilità con versioni più vecchie di Word** | Salva come `.doc` cambiando l'estensione; la maggior parte delle funzionalità delle forme funziona ancora. |

## Esempio completo funzionante

Di seguito trovi il programma completo che puoi copiare‑incollare in un nuovo progetto console. Non sono necessari snippet aggiuntivi.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;

        // 3️⃣ Insert an ellipse shape.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // 4️⃣ Create a group shape and add both shapes.
        GroupShape groupShape = builder.InsertGroupShape();
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Optional: reposition the group.
        groupShape.Left = 150;
        groupShape.Top = 100;

        // 5️⃣ Add a caption below the group.
        builder.Writeln();
        builder.Font.Size = 12;
        builder.Writeln("Grouped rectangle and ellipse created with DocumentBuilder.");

        // 6️⃣ Save the document as DOCX.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

**Risultato atteso**: Aprendo `output.docx` vedrai un rettangolo azzurro chiaro e un'ellisse corallo chiaro raggruppati insieme, posizionati a 150 pt dal margine sinistro e 100 pt dall'alto. La didascalia appare sotto il gruppo.

## Conclusione

Ora sai come **inserire una forma rettangolare** in un file Word usando C#, **come raggruppare le forme in Word**, e **come salvare il documento come docx** con l'`DocumentBuilder` di Aspose.Words. Padroneggiando questi passaggi puoi creare layout complessi—certificati, report o moduli personalizzati—interamente tramite codice.

Successivamente, esplora argomenti correlati come **aggiungere caselle di testo**, **lavorare con le tabelle**, o **esportare in PDF**. Ognuno di questi si basa sugli stessi fondamenti di `DocumentBuilder` che hai appena praticato.

Pronto a automatizzare i tuoi documenti Word? Prova a estendere l'esempio con più forme, applicare gradienti o iterare sui dati per generare un report completo in un'unica esecuzione. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}